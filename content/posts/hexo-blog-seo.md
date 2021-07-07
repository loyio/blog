---
title: "Hexo博客SEO优化，将你的网站提交到搜索引擎"
date: 2020-05-04T19:10:17+08:00
#description: <descriptive text here>
# weight: 1
aliases: ["/2020/05/04/hexo-blog-seo"]
tags: ["Hexo" "SEO" "搜索引擎" "搜索优化" "Baidu" "Google"]
categories: ["网站搭建"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: true
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
---

### 1.什么是SEO

SEO（Search Engine Optimization）顾名思义就是搜索引擎优化，比如你想让别人在百度、google搜索某些内容时，刚好可以出现自己网站的链接，简单来说，就是提高你个人网站的流量。虽然我这人本来就没想过要什么流量，主要目的是想记录一些东西，给自己看的，但是，如果自己的博客能够帮助到别人解决问题，我感觉还是挺值得的。我下面介绍的都是Hexo静态网站博客相关的

### 2.站点地图

也就是sitemap，站点地图可以告诉搜索引擎自己的网站有哪些可以抓取的内容，可以帮助搜索引擎更智能地抓取网站各个分支内容



#### 1⃣️ 生成站点地图

首先要安装百度和谷歌（Google）的站点地图生成插件

```bash
npm install hexo-generator-baidu-sitemap --save
npm install hexo-generator-sitemap --save
```

#### 2⃣️ 修改配置文件

打开博客主目录的`config.yml`文件，添加下面的sitemap配置内容

```yaml
# 生成博客sitemap
sitemap:
  path: sitemap.xml
baidusitemap:
  path: baidusitemap.xml
```

#### 3⃣️ 生成页面并部署到服务器

这个直接使用一键命令就可以了

```bash
hexo g -d
```

可以看到自己的public目录已经有下面两个文件了

![image-20200504090833044](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg59oqm75j308x03fweg.jpg)

### 3.百度站长平台

#### 1⃣️ 添加网站

首先你要打开下面的网站

https://ziyuan.baidu.com/

然后登录你的账号，好像直接用百度账号就可以了，进入控制台，页面如下

![image-20200504091627191](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg5hvi9ntj30s40gnq56.jpg)

点击下面的添加网站

![image-20200504093020147](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg5wclpwpj30rn038aaf.jpg)

根据步骤，选择站点属性，然后开始验证网站

我在这里选择的是文件验证，下载验证文件，然后把它放到你的网站根目录的source文件夹下，然后执行生成部署命令

```bash
hexo clean
hexo g -d
```

然后点击完成验证就可以了 (:exclamation:如果验证失败，建议先生成页面，然后将文件放到public文件夹中，然后再部署到服务器)

#### 2⃣️ 链接提交

我们在这里讲一下自动提交方法，手动提交按照要求在括号内填入链接即可

![image-20200504094615711](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg6cw5i6tj30rz0dlmyf.jpg)

自动提交也有三种选项，主动推送、自动推送以及sitemap

##### 1.主动推送

我们要用到hexo的插件，输入命令安装即可

```bash
npm install hexo-baidu-url-submit --save
```

然后在_config.yml文件添加以下内容

```yaml
baidu_url_submit:
  count: 5 ## 提交最新的五个链接
  host: blog.loyio.me ## 百度站长平台中注册的域名
  token: token ## 准入秘钥
  path: baidu_urls.txt ## 文本文档的地址， 新链接会保存在此文本文档里
```

host后面就是你在百度提交的网站域名

token你点击右边的修改准入密钥，就可以获取了，也可以实时更新自己的密钥

![image-20200504095712171](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg6o9vibqj30s10c9dgw.jpg)

然后，增加deployer选项

```yaml
deploy:
- type: git
  repo: git@github.com.....
  branch: master 
- type: baidu_url_submitter #百度链接主动提交
```

最后生成提交就可以了

```bash
hexo g -d
```

可以看到最后成功提交的输出

![image-20200504100400535](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg6vdi3sjj30b1039wer.jpg)

##### 2.自动推送

复制百度提供的自动推送代码

```html
<script>
(function(){
    var bp = document.createElement('script');
    var curProtocol = window.location.protocol.split(':')[0];
    if (curProtocol === 'https') {
        bp.src = 'https://zz.bdstatic.com/linksubmit/push.js';
    }
    else {
        bp.src = 'http://push.zhanzhang.baidu.com/push.js';
    }
    var s = document.getElementsByTagName("script")[0];
    s.parentNode.insertBefore(bp, s);
})();
</script>
```

打开主题目录，再打开布局目录下的 `post.swig` ,比如我的目录链接是这样的 `themes/next/layout/post.swig`

将上面的代码粘贴到最后就可以了

##### 3.sitemap

之前已经生成过sitemap文件了，这里只需要复制链接过去就可以了，比如我的百度sitemap文件链接如下

```text
https://blog.loyio.me/baidusitemap.xml
```

点击提交就可以了

### 4.Google网站站长

打开网站 https://www.google.com/webmasters/ ，然后登录自己的Google账号，点击SEARCH CONSOLE

![image-20200504101547402](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg77m6klgj30zx0gmade.jpg)

选择网址前缀资源类型，也就是第二个

![image-20200504101718180](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg796snxij30ou0fewgd.jpg)

输入自己网站的域名，点击继续，然后验证所有权，操作方法和百度基本相似，下载文件，然后将它放入文件夹中，生成部署就可以了

![截屏2020-05-04 上午10.18.05](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg7b7s7haj30mf0gkdh7.jpg)

部署完成后，点击验证就可以了，进入Google Search Console，点击右边栏的Sitemaps

![image-20200504102356189](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg7g5whhoj30yw0gjabs.jpg)

输入之前生成的sitemap.xml，然后点击SUBMIT（提交），就大功告成了

![image-20200504102518790](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1geg7hjd87fj30pa04u0sz.jpg)
