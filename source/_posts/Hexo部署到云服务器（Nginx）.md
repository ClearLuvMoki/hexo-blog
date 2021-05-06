---
title: 'Hexo部署云服务器(Nginx)'
date: 2020-02-23 23:24
updated: 2020-02-23 23:24
index_img: ./blog-img/hexo.png
categories: 
	- [Hexo]
	- [Nginx]
tags: Nginx
---

<h3>Hexo部署到阿里云服务器</h3>

> 在平时开发中需要个人的博客网站，不断的积累知识，于是找到了Hexo，最开始学习了怎么部署到github上，但是是通过https访问，并且访问速度很慢。
>
> 后面想着需要一个有域名的并且访问速度够快的个人博客网站，于是研究了怎么部署Hexo到服务器上。
>
> Hexo部署到github上访问请点击这里，[哔哩哔哩羊叔](https://www.bilibili.com/video/BV1Yb411a7ty?from=search&seid=7896361255674325515)。
>
> 服务器买的阿里云轻量级服务器1核2G，域名买的华为云。🧑🏻‍💻

<h5>一、安装Node.js</h5>

<p>由于第一次使用Linux，并且在多次安装出现问题情况下，首先安装路径要明确要记清楚。
我们在usr/local/下面新建一个文件夹 </p>

``` linux
mkdir node
```

<p>在<a href="https://nodejs.org/dist/">node.js</a>官网中选择Linux版本需要安装的node版本， 接着在node文件夹中解压这个压缩包</p>

```
wget https://nodejs.org/dist/v10.15.3/node-v10.15.3-linux-x64.tar.xz    // 下载node压缩包 
tar -xvf node-v10.15.3-linux-x64.tar.xz   // 解压node压缩包
./node -v  // 查看node版本
./npm -v // 查看npm
```

接着就是最重要的设置软链接，可以在服务器上任何文件夹中使用node:

``` 
ln -s /usr/local/node/bin/node /usr/bin/node  // 设置node的软链接
ln -s /usr/local/node/bin/npm /usr/bin/npm  //设置npm的软链接 
ln -s /usr/local/node/bin/npx /usr/bin/npx  //设置npx的软链接，以便后面需要
```

<h5>二、安装Git</h5>

<p>安装Git可以链接到仓库，并且可以在之后拉去Hexo的themes(在这只说明下载过程，具体Git配置请看GIt篇):</p>

```
yum install -y git
```

<h3>三、安装Hexo</h3>

<p>Hexo主要是博客的框架，在/usr/local中新建一个文件夹Blog，在文件夹中使用node下载Hexo脚手架：</p>

```
mkdir Blog  // 	新建文件夹
npm install hexo-cli -g   // 安装Hexo
hexo init //  本地新建Hexo
npm install // 下载依赖
git init  //  安装git本地仓库
```

<p>接着打开_config.yml文件，配置自己的代码仓库以及网页的icon和名称等信息：</p>

![设置代码仓库链接](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/hexoconfig.png)

![设置icon和网页标题](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/hexoconfig2.png)

<h5>四、安装Nginx</h5>

<p>在etc文件夹中使用命令安装Nginx:</p>

```
yum install -y nginx  // 安装nginx
vim /etc/nginx/nginx.conf  // 打开nginx.conf
```

<p>接着查看配置端口访问，在sercer_name中配置域名，在root中指向之前hexo的public目录，保证路径的正确，在location中设置访问index.html文件。</p>

![nginx配置](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/nginx.png)

```
接着启动Nginx服务:
systemctl start nginx
systemctl enable nginx  // 开机启动nginx服务
```

<h5>五、运行Hexo</h5>

<p>接着回到安装hexo的目录下，执行命令，启动hexo服务:</p>

```
hexo g
```

<h5>写在最后</h5>

<p>在不断的查找学习下，也算有了自己的网页，还有个像模像样的域名，中间也有朋友叫帮忙给他建一个网页，不断的练习，希望这个博客对自己的不断学习可以起到一个监督和积累的作用.</p>

<p>🌈Always</p>

