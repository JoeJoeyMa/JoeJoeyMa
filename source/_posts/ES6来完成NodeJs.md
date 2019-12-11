---
title: ES6来完成NodeJs
date: 2018-03-09 14:28:01
tags:
- CSS
- 前端
- JavaScript
- ES6
- React
- Vue
- Dom
- Angular
- NodeJs

---

ES2015或ES6是指JavaScript最新的稳定的迭代版本。

ES6是JavaScript的重大更新，也是自2009年ES5标准化之后的第一次更新。这次更新包括了一些新的语言语法，其中有一部分被看做是语法糖。

目前主流JavaScript引擎还没有完全实现这些新功能，需要进行一些转换才能在旧的JavaScript中使用这些新功能。

在本教程中，我们将使用ES6创建一个[Express](https://expressjs.com/)应用。我们将会使用Babel编译器将ES6代码编译为ES5。

用Babel编译器我们可以在Express应用中使用JavaScript的新特性。当然你也需要治疗JavaScript的基础知识才能够成功完成本教程中的内容。

根据Babel的官网来看，我们可以用它来使用下一代JavaScript、

本教程假设你已经安装了 Node Package Manager([NPM](http://blog.npmjs.org/post/85484771375/how-to-install-npm))和 [NodeJS 引擎](https://docs.npmjs.com/getting-started/installing-node)。

学习本教程的时候最好使用 linux 或者 mac Os 系统。当然，使用 windows 系统也可以正常进行。

## 第一步：安装项目文件夹
 - 创建一个新的文件夹
 - [用terminal进入这个文件夹](https://askubuntu.com/questions/375867/how-to-access-a-folder-through-the-terminal)
 - 运行以下命令来初始化你的项目
```
npm init -y
```
这将会帮你在你的项目中创建一个 package.json 文件。在这一步中，你的 package.json 文件应该与下面这个例子非常相似：

```
{
  "name": "es6express",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```
## 第二步：创建程序入口
 - 在你项目的根目录下，创建 index.js 文件

## 第三步：安装需要的模块（dependencies/devDependencies ）
在这一步中，我们将会安装 express 应用需要的模块。

### Dependencies
注意这些依赖是可选的，只是因为我们创建 express 应用才需要。

 - [express](https://expressjs.com/)：一个快速的、无限制的、简约的 NodeJS web 框架
 - [margan](https://github.com/expressjs/morgan)：NodeJS 的 http 请求记录中间件

要安装这些依赖，在你项目中间夹中打开 terminal，运行以下命令：

```
npm install --save express morgan
```
在这一步，你的项目目录中应该会有一个 node_modules 文件夹，你的 package.json 文件应该与下面的这个例子类似：

```
{
  "name": "es6express",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.15.2",
    "morgan": "^1.8.1"
  }
}
```
### Development Dependencies
这些依赖是用于在我们项目中使用 babel 编译器的：
 - [babel-cli](https://babeljs.io/docs/usage/cli/)：使用 babel 命令行编译文件
 - [babel-preset-es2015 ](https://www.npmjs.com/package/babel-preset-es2015)：Babel 为ES2015预设的插件
 - [rimraf](https://github.com/isaacs/rimraf)：在 NodeJS 中使用 unix 命令 rm -rf

在这一步，你的 package.json 文件应该与下面这个例子类似：

```
{
  "name": "es6express",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.15.2",
    "morgan": "^1.8.1"
  },
  "devDependencies": {
    "babel-cli": "^6.24.0",
    "babel-preset-es2015": "^6.24.0",
    "rimraf": "^2.6.1"
  }
}
```

## 第四步：在你项目的根目录下创建一个 Babel 配置文件
 - 运行以下命令来创建一个 babel 配置文件

```
touch .babelrc
```
这个文件是用来告诉 babel 如何转换你的 JavaScript 文件。我们将会把我们的ES6代码转换为ES5代码。
 - 打开你的 .babelrc文件，把以下代码段复制到你的文件中，并保存。

```
{
  "presets": ["es2015"]
}
```

## 第五步：使用 Babel 来编译我们的 JavaScript 文件

我们要做的下一步就是使用 babel 把我们的 JavaScript 代码从ES6编译为ES5（我们现在还没有写什么 JavaScript 代码）。

 - 在你的 package.json 文件中，添加一个 start 和 build 命令。你的 package.json 文件应该与下面例子类似：
 
```
{
  "name": "es6express",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "rimraf dist/ && babel ./ --out-dir dist/ --ignore ./node_modules,./.babelrc,./package.json,./npm-debug.log --copy-files",
    "start": "npm run build && node dist/index.js"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.15.2",
    "morgan": "^1.8.1",
    "rimraf": "^2.6.1"
  },
  "devDependencies": {
    "babel-cli": "^6.24.0",
    "babel-preset-es2015": "^6.24.0"
  }
}

```

恭喜你！你现在已经可以在你的 express 中使用 JavaScript 的新特性了。





