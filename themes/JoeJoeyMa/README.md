# JoeJoeyMa Themes

[![Build Status](https://travis-ci.org/JoeJoeyMa/hexo-theme-JoeJoeyMa.svg?branch=master)](https://travis-ci.org/JoeJoeyMa/hexo-theme-JoeJoeyMa)


An attractive, exquisite theme for [Hexo]. named "JoeJoeMa" 

[**☞ Live Preview**](http://joejoey.tk/)  |  [**✎ JoeJoeyMa 中文版使用文档**](https://github.com/JoeJoeyMa/hexo-theme-JoeJoeyMa/blob/master/README.cn.md)


![Desktop Preview](https://raw.githubusercontent.com/JoeJoeyMa/JoeJoeyMa.github.io/master/gallery/1.JPG)
![Post Preview](https://raw.githubusercontent.com/JoeJoeyMa/JoeJoeyMa.github.io/master/gallery/2.JPG)
![Mobile Preview](https://raw.githubusercontent.com/JoeJoeyMa/JoeJoeyMa.github.io/master/gallery/3.JPG)
![Mobile Preview](https://raw.githubusercontent.com/JoeJoeyMa/JoeJoeyMa.github.io/master/gallery/4.JPG)
![Mobile Preview](https://raw.githubusercontent.com/JoeJoeyMa/JoeJoeyMa.github.io/master/gallery/5.JPG)



> This is DEMO source which you can refer to: http://joejoey.tk/categories/
<!--more-->

## Installation

 1. Get it from GitHub

```shell
 $ git clone https://github.com/JoeJoeyMa/hexo-theme-JoeJoeyMa.git themes/JoeJoeyMa
```
 2. Enable

 Modify `theme` setting in `_config.yml` to `JoeJoeyMa`.
 ```
 # Extensions
 ## Plugins: http://hexo.io/plugins/
 ## Themes: http://hexo.io/themes/
 theme: hiker
 ```
 3. Update

```shell
 $ cd themes/JoeJoeyMa
 $ git pull
```


## Features

### Homepage background

You could place the image file in `YOUR_HEXO_SITE\themes\JoeJoeyMa\source\css\images` directory. and modify `home_background_image` in JoeJoeyMa/_config.yml. 

```yml
# Homepage
# eg. home_background_image: [css/images/home-bg.jpg, http://t.cn/RMbvEza]
# eg. mode: image | polyline | trianglify
home_background_image:
  enable: true
  mode: image
  rolling: true
  url: [css/images/home-bg.jpg, css/images/sample.jpg, https://source.unsplash.com/collection/954550/1920x1080]
```

There are 3 modes to select: 

- `image`
- `polyline`
- `trianglify`

`image` mode is default, `trianglify` mode is from [Trianglify](https://github.com/qrohlf/trianglify), looks like below.

![](https://cloud.githubusercontent.com/assets/347189/6771063/f8b0af46-d090-11e4-8d4c-6c7ef5bd9d37.png)

`polyline` mode: if you DON'T want any image as your homepage background, you can use this mode. Or you can keep `enable` true, then set `url` of `home_background_image` empty in JoeJoeyMa/_config.yml, you will have an default homepage with **random decorative pattern**.

![](https://itimetraveler.github.io/hexo-theme-hiker/2016/10/24/Hiker%E4%B8%BB%E9%A2%98%E9%A2%84%E8%A7%88/home-no-background1.png)




### Code Highlight Theme

JoeJoeyMa use [Tomorrow Theme](https://github.com/chriskempson/tomorrow-theme) for your code block. We have six options in total: `default`, `normal`, `night`, `night blue`, `night bright`, `night eighties`

![code `default` theme Preview](https://itimetraveler.github.io/hexo-theme-hiker/2016/10/24/Hiker%E4%B8%BB%E9%A2%98%E9%A2%84%E8%A7%88/code-theme-default.png)

Above preview picture is default theme. the image below show other five Highlight themes.

![code themes](https://github.com/iTimeTraveler/hexo-theme-hiker/blob/master/source/preview/code-theme.jpg?raw=true)

Modify `highlight_theme` in JoeJoeyMa/_config.yml.

```yml
# Code Highlight theme
# Available value:
#    default | normal | night | night eighties | night blue | night bright
# https://github.com/chriskempson/tomorrow-theme
highlight_theme: default
```

### Blog Theme Color

JoeJoeyMa provide five color themes for your blog.

![theme colors](https://github.com/iTimeTraveler/hexo-theme-hiker/blob/master/source/preview/theme-color.png?raw=true)

- <span style="display: inline-block; width: 18px; height: 18px; margin: 0 4px; background-color: #fb6d19; border-radius: 3px; vertical-align: middle;"></span> orange
- <span style="display: inline-block; width: 18px; height: 18px; margin: 0 4px; background-color: #00aced; border-radius: 3px; vertical-align: middle;"></span> blue
- <span style="display: inline-block; width: 18px; height: 18px; margin: 0 4px; background-color: #f03838; border-radius: 3px; vertical-align: middle;"></span> red
- <span style="display: inline-block; width: 18px; height: 18px; margin: 0 4px; background-color: #39aa56; border-radius: 3px; vertical-align: middle;"></span> green
- <span style="display: inline-block; width: 18px; height: 18px; margin: 0 4px; background-color: #404040; border-radius: 3px; vertical-align: middle;"></span> black

You can modify `theme_color` in JoeJoeyMa/_config.yml.

```yml
# Article theme color
# Available value:
#    random | orange | blue | red | green | black
theme_color: random
```

### Night mode

Just for article reading. In article page, you can click the **logo image of header** to switch to Night mode.

![](https://itimetraveler.github.io/hexo-theme-hiker/2016/10/24/Hiker%E4%B8%BB%E9%A2%98%E9%A2%84%E8%A7%88/night-mode.gif)


### Search

JoeJoeyMa use `Insight Search` to help you search anything inside your site without any third-party plugin.

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

JoeJoeyMa uses [Fancybox] to showcase your photos. You can use Markdown syntax or fancybox tag plugin to add your photos.

```
![img caption](img url)

{% fancybox img_url [img_thumbnail] [img_caption] %}
```

### Sidebar

You can put your sidebar in left side, right side or bottom of your site by editing `sidebar` setting.
JoeJoeyMa provides 5 built-in widgets:

- category
- tag
- tagcloud
- archives
- recent_posts

All of them are enabled by default. You can edit them in `widget` setting.

### Comment support (add new Gitment)

JoeJoeyMa has native support for DuoShuo & Disqus comment systems. Modify the following snippets to JoeJoeyMa `JoeJoeyMa/_config.yml`:

```yml
# comment ShortName, you can choose only ONE to display.
gentie_productKey: #your-gentie-product-key
duoshuo_shortname: 
disqus_shortname: 
livere_shortname: MTAyMC8yOTQ4MS82MDQ5
uyan_uid: 
wumii: 
```
https://github.com/settings/applications/new



## Browser support

![](https://github.com/iTimeTraveler/hexo-theme-hiker/blob/master/source/preview/browser-support.png?raw=true)


## Contributing

All kinds of contributions (enhancements, new features, documentation & code improvements, issues & bugs reporting) are welcome.

Looking forward to your pull request.

[Hexo]: https://hexo.io/
[Fancybox]: http://fancyapps.com/fancybox/
[Font Awesome]: http://fontawesome.io/
