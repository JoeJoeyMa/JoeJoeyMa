---
title: HexoForGit
date: 2020-1-2 12:27:27
tags:
- Django
- VPS
- 前端 
- Hexo
- Git
- 博客
- 笔记

---
## 使用hexo，如果换了电脑怎么更新博客？



------

其实，Hexo生成的文件里面是有一个.gitignore的，所以它的本意应该也是想我们把这些文件放到GitHub上存放的。但是考虑到如果每个GitHub Pages都需要额外的一个仓库存放这些文件，就显得特别冗余了。这个时候就可以用分支的思路！一个分支用来存放Hexo生成的网站原始的文件，另一个分支用来存放生成的静态网页。最近我也用GitHub Pages搭建了一个独立博客，想到了这个方法，使用之后真的特别简洁。为了更直观地说明，奉上使用这种方法不同时候的流程：



## 一、关于搭建的流程

1. 创建仓库，http://xxxx.github.io；
2. 创建两个分支：master 与 hexo；
3. 设置hexo为默认分支（因为我们只需要手动管理这个分支上的Hexo网站文件）；
4. 使用git clone git@github.com:xxxx/xxxx.github.io.git拷贝仓库；
5. 在本地http://xxxx.github.io文件夹下通过Git bash依次执行npm install hexo、hexo init、npm install 和 npm install hexo-deployer-git（此时当前分支应显示为hexo）;
6. 修改_config.yml中的deploy参数，分支应为master；
7. 依次执行git add .、git commit -m "..."、git push origin hexo提交网站相关的文件；
8. 执行hexo g -d生成网站并部署到GitHub上。


------

## 二、关于日常的改动流程

在本地对博客进行修改（添加新博文、修改样式等等）后，通过下面的流程进行管理。

1. 依次执行git add .、git commit -m "..."、git push origin hexo指令将改动推送到GitHub（此时当前分支应为hexo）；
2. 然后才执行hexo g -d发布网站到master分支上。

3. 虽然两个过程顺序调转一般不会有问题，不过逻辑上这样的顺序是绝对没问题的（例如突然死机要重装了，悲催....的情况，调转顺序就有问题了）。
------

## 三、本地资料丢失后的流程

当重装电脑之后，或者想在其他电脑上修改博客，可以使用下列步骤：

1. 使用git clone git@github.com:xxxx/CrazyMilk.github.io.git拷贝仓库（默认分支为hexo）；
2. 在本地新拷贝的http://xxxx.github.io文件夹下通过Git bash依次执行下列指令：npm install hexo、npm install、npm install hexo-deployer-git（记得，不需要hexo init这条指令）。
------