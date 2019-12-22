---
title: Python小爬虫的那些事
date: 2013/9/10 15:41:44
tags:
- Life
- work
- python
- 爬虫

---


## Python


从接触计算机以来，一直都有着想深入了解一门语言。也是因为有做着网络电商的原因吧，店家每天都一直维护干着同样或者是类似流水线式的工作,每天得上传自己的产品修改着宝贝详细里的描述，有时也得观察着同行的一举一动。让我拥有了想做一个真正脚本的想法念头，解放自己的劳动力！
俗话说的好解放劳动力才能增大自己的生产里，从琐碎事里摆脱，做着认为对自己有用的事情才能增长。

Python抓取网页方法，任务是批量下载网站上的文件。对于一个刚刚入门python的人来说，在很多细节上都有需要注意的地方，以下就分享一下在初学python过程中遇到的问题及解决方法。
学习Python，当然少不了环境的配置，最初我用的是Notepad++，不过发现它的提示功能实在是太弱了，于是，在Windows下我用了PyCharm，在Linux下我用了Eclipse for Python，另外还有几款比较优秀的IDE

## urllib库
 Python万能的胶水语言使得让它有更大的活力，以至于在爬虫这个领域中也诞生的很多库。

    response = urllib2.urlopen("http://www.baidu.com")
    urlopen(url, data, timeout)
    print response.read()

    import urllib2

    request = urllib2.Request("http://www.baidu.com")
    response = urllib2.urlopen(request)
    print response.read()
    

    
那么就开始吧


    import urllib
    import urllib2
    import re
    import tool
    import os

#抓取买家主页个人介绍
```python
class Spider:

    #页面初始化
    def __init__(self):
        self.siteURL = 'http://mm.taobao.com/json/request_top_list.htm'
        self.tool = tool.Tool()

    #获取索引页面的内容
    def getPage(self,pageIndex):
        url = self.siteURL + "?page=" + str(pageIndex)
        request = urllib2.Request(url)
        response = urllib2.urlopen(request)
        return response.read().decode('gbk')

    #获取索引界面所有的信息，list格式
    def getContents(self,pageIndex):
        page = self.getPage(pageIndex)
        pattern = re.compile('<div class="list-item".*?pic-word.*?<a href="(.*?)".*?<img src="(.*?)".*?<a class="lady-name.*?>(.*?)</a>.*?<strong>(.*?)</strong>.*?<span>(.*?)</span>',re.S)
        items = re.findall(pattern,page)
        contents = []
        for item in items:
            contents.append([item[0],item[1],item[2],item[3],item[4]])
        return contents

    #获取MM个人详情页面
    def getDetailPage(self,infoURL):
        response = urllib2.urlopen(infoURL)
        return response.read().decode('gbk')

    #获取个人文字简介
    def getBrief(self,page):
        pattern = re.compile('<div class="mm-aixiu-content".*?>(.*?)<!--',re.S)
        result = re.search(pattern,page)
        return self.tool.replace(result.group(1))

    #获取页面所有图片
    def getAllImg(self,page):
        pattern = re.compile('<div class="mm-aixiu-content".*?>(.*?)<!--',re.S)
        #个人信息页面所有代码
        content = re.search(pattern,page)
        #从代码中提取图片
        patternImg = re.compile('<img.*?src="(.*?)"',re.S)
        images = re.findall(patternImg,content.group(1))
        return images


    #保存多张图片
    def saveImgs(self,images,name):
        number = 1
        print u"发现",name,u"共有",len(images),u"张照片"
        for imageURL in images:
            splitPath = imageURL.split('.')
            fTail = splitPath.pop()
            if len(fTail) > 3:
                fTail = "jpg"
            fileName = name + "/" + str(number) + "." + fTail
            self.saveImg(imageURL,fileName)
            number += 1

    # 保存头像
    def saveIcon(self,iconURL,name):
        splitPath = iconURL.split('.')
        fTail = splitPath.pop()
        fileName = name + "/icon." + fTail
        self.saveImg(iconURL,fileName)

    #保存个人简介
    def saveBrief(self,content,name):
        fileName = name + "/" + name + ".txt"
        f = open(fileName,"w+")
        print u"正在偷偷保存她的个人信息为",fileName
        f.write(content.encode('utf-8'))


    #传入图片地址，文件名，保存单张图片
    def saveImg(self,imageURL,fileName):
         u = urllib.urlopen(imageURL)
         data = u.read()
         f = open(fileName, 'wb')
         f.write(data)
         print u"正在悄悄保存她的一张图片为",fileName
         f.close()

    #创建新目录
    def mkdir(self,path):
        path = path.strip()
        # 判断路径是否存在
        # 存在     True
        # 不存在   False
        isExists=os.path.exists(path)
        # 判断结果
        if not isExists:
            # 如果不存在则创建目录
            print u"偷偷新建了名字叫做",path,u'的文件夹'
            # 创建目录操作函数
            os.makedirs(path)
            return True
        else:
            # 如果目录存在则不创建，并提示目录已存在
            print u"名为",path,'的文件夹已经创建成功'
            return False

    #将一页淘宝MM的信息保存起来
    def savePageInfo(self,pageIndex):
        #获取第一页淘宝列表
        contents = self.getContents(pageIndex)
        for item in contents:
            #item[0]个人详情URL,item[1]头像URL,item[2]姓名,item[3]年龄,item[4]居住地
            print u"发现一位,名字叫",item[2],u"age",item[3],u",在",item[4]
            print u"正在保存",item[2],"的信息"
            print u"个人地址是",item[0]
            #个人详情页面的URL
            detailURL = item[0]
            #得到个人详情页面代码
            detailPage = self.getDetailPage(detailURL)
            #获取个人简介
            brief = self.getBrief(detailPage)
            #获取所有图片列表
            images = self.getAllImg(detailPage)
            self.mkdir(item[2])
            #保存个人简介
            self.saveBrief(brief,item[2])
            #保存头像
            self.saveIcon(item[1],item[2])
            #保存图片
            self.saveImgs(images,item[2])

    #传入起止页码，获取图片
    def savePagesInfo(self,start,end):
        for i in range(start,end+1):
            print u"正在找第",i,u"个地方，看看在不在"
            self.savePageInfo(i)
```

#传入起止页码即可，在此传入了2,10,表示抓取第2到10页
```spider = Spider()```
```spider.savePagesInfo(2,10)```

## Request库

```
使用 Requests 发送网络请求非常简单。


    import requests


requests库提供了http所有的基本请求方式

    r = requests.post("http://httpbin.org/post")
    r = requests.put("http://httpbin.org/put")
    r = requests.delete("http://httpbin.org/delete")
    r = requests.head("http://httpbin.org/get")
    r = requests.options("http://httpbin.org/get")

一次完整的请求

    import requests
    r = requests.get('https://taobao.com')
    r.text



## Scripts

```
