---
title: Django2.0
date: 2017-010-27 12:15:18
tags:
- Django
- VPS
- 后端
- Python
- Rail
- MVC
- 语法堂
---
9月23，Django 发布了2.0a1版本，这是一个 feature freeze 版本，如果没有什么意外的话，2.0正式版不会再增加新的功能了。按照以往的规律，预计正式版将在12月发布。

备注：Django 2.0 于12月2日已经正式发布。

2.0无疑是一个里程碑版本，移除了对 Python2.7 的支持，最少需要 3.4 以上，建议使用3.5以上的版本。

What’s new in Django2.0 文档中一共列出了三个新的特性：

更简单的URL路由语法 (Simplified URL routing syntax)
admin应用的针对移动设备的优化改进(Mobile-friendly contrib.admin)
支持SQL开窗表达式(Window expressions)
第一个特性，主要用于动态路由定义上。在Django2.0代码实现中，主要的变化是新增了 django.urls.path 函数，它允许使用一种更加简洁、可读的路由语法。比如之前的版本的代码：

    url(r'^articles/(?P<year>[0-9]{4})/$', views.year_archive),
在新版本中也可以写为：
    path('articles/<int:year>/', views.year_archive),

问题引入
下面是Django1.X的一段代码：

'''python
from django.conf.urls import url
def year_archive(request, year):
    year = int(year) # convert str to int
    # Get articles from database
def detail_view(request, article_id):
    pass
def edit_view(request, article_id):
    pass
def delete_view(request, article_id):
    pass
urlpatterns = [
    url('articles/(?P<year>[0-9]{4})/', year_archive),
    url('article/(?P<article_id>[a-zA-Z0-9]+)/detail/', detail_view),
    url('articles/(?P<article_id>[a-zA-Z0-9]+)/edit/', edit_view),
    url('articles/(?P<article_id>[a-zA-Z0-9]+)/delete/', delete_view),
]
'''