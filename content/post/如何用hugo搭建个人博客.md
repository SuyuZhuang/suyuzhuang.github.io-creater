---
title: "如何用hugo搭建个人博客"
date: 2019-08-21T21:41:27+08:00
draft: false
---
# 1 快速开始
## 1.1 开始前的准备
- 本地git工具
- github账号
- 本地安装好的hugo

安装步骤如下：

我使用的是Windows 10，所以直接去到[Hugo release页面](https://github.com/gohugoio/hugo/releases)下载 `hugo_0.57.2_Windows-64bit.zip`压缩包，在英文目录下解压。

然后把hugo目录加入到PATH中，比如`D:/tool/hugo`

执行`hugo version`，有版本结果出现则证明安装成功

## 1.2 搭建骨架
去到hugo官网，进入[quick-start教程](https://gohugo.io/getting-started/quick-start/),前期其实跟着教程一步步走就好了。

开辟一个新目录，如`D:/study/hugo`, 进入到该目录中，运行

```bash
hugo new site suyuzhuang.github.io-creater
```
再进入到刚刚创建的目录

```bash
cd suyuzhuang.github.io-creater
```
在该目录中初始化git，并加入主题。更多的主题可以在[themes.gohugo.io](https://themes.gohugo.io/)中找到

```bash
# Download the theme
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
```

将主题的设置放入到config.toml文件中

```bash
# Edit your config.toml configuration file
# and add the Ananke theme.
echo 'theme = "ananke"' >> config.toml
```

## 1.3 第一篇文章
添加第一篇文章，名叫自我介绍
```bash
hugo new posts/自我介绍.md
```
使用VS Code打开项目目录（在命令行中键入`code .`就能打开当前项目目录），修改md文件。

写完第一篇文章后，注意将上方`draft:true`修改为`draft:false`

## 1.4 启动本地服务，创建静态页面

```bash
hugo server -D
```

执行成功后，可以在本地http://localhost:1313/
链接中看到刚刚写的文章了。

修改一下配置文件,将博客名、语言等修改一下

```toml
baseURL = "https://suyuzhuang.github.io"
languageCode = "zh-Hans"
title = "苏苏的CodingLife"
theme = "ananke"
```

```bash
hugo
```

使用上面这个简单的`hufo`命令建立静态页面，此时，你会发现项目目录中会多了一个public文件夹


在项目目录中添加`.gitignore`文件，忽略`/public/`，因为我们的public目录将要自己成为一个新的repo

## 1.5 放入github仓库
在github中新建仓库`suyuzhuang.github.io`，注意不勾选自动添加README.md

进入到public文件夹，运行下面两个命令，使得public文件夹中的内容上传到github服务器。

```bash
git remote add origin git@github.com:SuyuZhuang/suyuzhuang.github.io.git

git push -u origin master
```

然后在github中进入该repo的settings，可以看到我们的博客目录就在https://suyuzhuang.github.io/
中了

# 2 精细装修
Hugo提供的主题其实不太尽人意，我们可以官网或其他网站搜索常用的主题，按照主题所在github文档中的提示一步步修改，再重新发布就好了。