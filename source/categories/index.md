---
type: About themes
comments: true
---
# JoejoeyMA blog

**A fashional newspaper, blog theme for Hexo**. 

- [**☞ Preview Demo**](http://joejoey.tk/) | [**查看中文使用文档**](https://github.com/iTimeTraveler/hexo-theme-joejoeyma/blob/master/README.cn.md)


![](https://raw.githubusercontent.com/JoeJoeyMa/JoeJoeyMa.github.io/master/gallery/1.JPG)

![](https://raw.githubusercontent.com/JoeJoeyMa/JoeJoeyMa.github.io/master/gallery/2.JPG)

![](https://raw.githubusercontent.com/JoeJoeyMa/JoeJoeyMa.github.io/master/gallery/3.JPG)

![](https://raw.githubusercontent.com/JoeJoeyMa/JoeJoeyMa.github.io/master/gallery/4.JPG)

![](https://raw.githubusercontent.com/JoeJoeyMa/JoeJoeyMa.github.io/master/gallery/5.JPG)


<!--more-->

## Installation

 1. Get it from GitHub

 ```shell
 $ git clone https://github.com/JoeJoeyMa/JoeJoeyMa.github.io themes/JoeJoeyMa
 ```
 2. Enable

 Modify `theme` setting in `_config.yml` to `JoeJoeyMa`.
 ```
 # Extensions
 ## Plugins: http://hexo.io/plugins/
 ## Themes: http://hexo.io/themes/
 theme: hipaper
 ```
 3. Update

 ```shell
 $ cd themes/JoeJoeyMa
 $ git pull
 ```



## Features


### Logo: Image or Text

You can set a image as your logo instead of original text title. Like this:

![](.jpg)

just enable `avatar` field in hipaper/_config.yml.

```yml
# Put your avatar.jpg into `hexo-site/themes/hipaper/source/` directory.
# url is target link (E.g. `url: https://hexo.io/logo.svg` or `url: css/images/mylogo.jpg`)
avatar: 
  enable: true
  width: 124
  height: 124
  bottom: 10
  url: https://hexo.io/logo.svg
```


### Code Highlight

Hipaper use [Tomorrow Theme](https://github.com/chriskempson/tomorrow-theme) for your code block. We have six options in total: `default`, `normal`, `night`, `night blue`, `night bright`, `night eighties`

![code `default` theme Preview](https://raw.githubusercontent.com/ChrisKempson/Tomorrow-Theme/master/Images/Tomorrow-Night-Eighties.png)

Above preview picture is default theme. the image below show other five Highlight themes.

![code themes](https://raw.githubusercontent.com/ChrisKempson/Tomorrow-Theme/master/Images/Tomorrow.png)

Modify `highlight_theme` in JoeJoeyMa/_config.yml.

```yml
# Code Highlight theme
# Available value:
#    default | normal | night | night eighties | night blue | night bright
# https://github.com/chriskempson/tomorrow-theme
highlight_theme: default
```



### Sidebar

You can put your sidebar in left side, right side or bottom of your site by editing `sidebar` setting.
Hipaper provides 7 built-in widgets:

- search
- social
- recent_posts
- category
- tag
- tagcloud
- archive

All of them are enabled by default. You can edit them in `widget` setting.


### Search

Hipaper use `Insight Search` to help you search anything inside your site without any third-party plugin.

![](4.png)

```yml
# Search
search:
    insight: true # you need to install `hexo-generator-json-content` before using Insight Search
    swiftype: # enter swiftype install key here
    baidu: false # you need to disable other search engines to use Baidu search, options: true, false
```

> Attention: You need to install `hexo-generator-json-content` before using Insight Search.

```bash
$ npm install -S hexo-generator-json-content
```


### Fancybox

Hipaper uses [Fancybox] to showcase your photos. You can use Markdown syntax or fancybox tag plugin to add your photos.

```
![img caption](img url)

{% fancybox img_url [img_thumbnail] [img_caption] %}
```

### Comment support

Hipaper has native support for DuoShuo & Disqus comment systems. Modify the following snippets to Hipaper `JoeJoeyMa/_config.yml`:

```yml
# comment ShortName, you can choose only ONE to display.
duoshuo_shortname: iTimeTraveler
disqus_shortname: 
```



## Browser support

![](https://raw.githubusercontent.com/iTimeTraveler/hexo-theme-hipaper/master/source/preview/browser-support.png?raw=true)



## Contributing

All kinds of contributions (enhancements, new features, documentation & code improvements, issues & bugs reporting) are welcome.

Looking forward to your pull request.



## License

Hipaper is under the MIT license. See the [LICENSE]() file for details.


[Hexo]: https://hexo.io/
[Font Awesome]: http://fontawesome.io/