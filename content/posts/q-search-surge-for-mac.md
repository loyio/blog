---
title: "Surge-For-Mac模块 Q-Search 自定义搜索"
date: 2020-05-06T19:55:11+08:00
#description: <descriptive text here>
# weight: 1
aliases: ["/2020/05/06/q-search-surge-for-mac"]
tags: ["Surge", "Surge模块", "自定义搜索", "Q-Search"]
categories: ["网络工具"]
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

昨天狠下心上了SurgeForMac的车，140永久，这是继Quantumult X后的又一次剁手，我也不知道自己怎么这么折腾，本来我Mac端用Clash用的好好的，没啥其它问题，可能是头脑一热吧，不过我今天就是想介绍一下，我重写的一款Surge模块，Q-Search



### 前言

在手机上用过Quantumult X和Surge的应该很熟悉这个插件，就是利用了重写的功能，实现自定义搜索命令，比如我想要在京东上搜索笔记本，我只需要在搜索栏输入 `jd 笔记本` 就可以了

![IMG_04FFB5FC9F1A-1](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlgy1geiofwsjamj30v90fxwi3.jpg)

然后回车，它会自动重定向至京东搜索页面，如下图所示

![IMG_FAE7C897F02B-1](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlgy1geioi201suj30u01im7ql.jpg)

像这样的搜索命令还有很多，比如`tb`(在淘宝网搜索)，`db`（在豆瓣搜索）， 我这就不一一列举了，可以在我的源码中查询，里面都有注释

我根据大佬们的源码，自己改进了一些，并成功适配Mac端的Surge，而且做了桌面页面的匹配，Quantumult X原代码链接[Github](https://github.com/nzw9314/QuantumultX/blob/master/Q-Search_All_in_one.conf)

### Surge配置

下面我说下如何在自己的SurgeForMac中配置Q-Search

#### 1.打开模块设置

首先打开Surge，在左面的菜单栏中选择设置，如下图所示，然后点击模块

![image-20200506135239668](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlgy1geiopw1qzjj30pp0gmgzs.jpg)

然后我们进入下面的页面

![image-20200506135435373](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlgy1geiorw05pwj30ku0fdtb1.jpg)

#### 2.安装模块

有两种方法安装模块，直接本地加载和从URL安装模块

第一种方法就是从github把模块下载下来，然后放到Surge默认配置路径中，注意后缀名称为`.sgmodule`

第二种方法，就是直接点击左下角的从URL安装模块，然后将 [Q-Search](https://raw.githubusercontent.com/loyelee/SurgeMacModule/master/Q-Search.sgmodule) 链接粘贴到文本框中，最后点击完成

![image-20200506140057465](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlgy1geioyiu7lbj30pm0b9n16.jpg)

#### 3.启用模块

安装模块后，记得启用模块，就是把左边的选项框勾选即可，如下图所示

![image-20200506140245784](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlgy1geip0e68jjj30m002paaa.jpg)

#### 4.注意事项

请确保你已经进行了Mitm配置，是否安装证书且信任证书，并进行了主机名配置

### 使用模块之前

请先将Safari的默认搜索改为DuckDuckGo

![image-20200506140711913](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlgy1geip50fzv3j30km06vjsr.jpg)

### 使用模块

一般无指令的搜索，默认是进行Google搜索

想要知道所有指令，直接点击下面链接即可，基本上都有注释说明

https://raw.githubusercontent.com/loyio/SurgeMacModule/master/Q-Search.sgmodule

下面我们在mac端试验一下京东搜索指令，指令还是`jd 笔记本`

![截屏2020-05-06 下午2.11.06](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlgy1geip9js2qhj30oa03g76u.jpg)

回车即可返回下面的搜索页面

![image-20200506141300725](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlgy1geipb32gjhj30yg0hlaiv.jpg)

如果有不明白的问题，可以邮件联系我
