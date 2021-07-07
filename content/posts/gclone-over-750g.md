---
title: "rclone突破750G转存限制（使用gclone和Autoclone）"
date: 2020-05-07T19:59:48+08:00
#description: <descriptive text here>
# weight: 1
# aliases: ["/2020/05/07/gclone-over-750g"]
tags: ["GoogleDrive", "gclone", "autoclone", "谷歌云"]
categories: ["GoogleDrive"]
showToc: false
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

最近一直都在折腾GoogleDrive，有时候看到Tg群里面大佬分享的资源，都特别的大，本来一开始我是使用插件copy url to googledrive，应该是这个名称吧，不过比较鸡肋的是，这个只能转存到个人盘中，在没购买容量套餐前所有的人都默认是15G，远远不够用，虽然我买了一年的100G，但是依然不够用，随便转存点什么，就超过100G了，而且还要自己手动移动到团队盘



在之前我就讲过了用rclone挂载GoogleDrive到linux服务器上的教程，大家可以点击下面的链接查看

[使用谷歌云搭建google drive离线下载服务器](https://blog.loyio.me/2020/04/28/gcp-create-gdrive-download-server/)

在用rclone转存文件时，我们可能会遇到超过日转存限制的情况，Google每天的限制750G，这对于我们这些特别喜欢搬运的人来说是远远不够的

首先说一些解决方法原理：

谷歌开发者平台可以多个项目，每个项目下还可以创建多个服务账号（SA：Service Account），每个SA又可以创建自己单独的Api，每个Api都可以和单个用户一样拥有750GB的权限。

这里我们要用到autoclone，批量生成SA账号，还要用到gclone，自动切换SA，以突破750G的限制

我在这里不说具体的操作过程了，大佬们都有写，做重复的事情没有什么意义

[gclone 搬山之术](https://tech.he-sb.top/posts/usage-of-gclone/) by [HE-SB-技术栈](https://tech.he-sb.top/)

[AutoRclone配合gclone突破GoogleTeamDrive750G流量限制](https://www.uud.me/qiwenzalun/autorclone-gclone.html) by [余十一 ](https://www.uud.me/cross.html)

[可能是最简单的AutoRclone教程：如何突破Google Drive每日750G限制？](https://panoan.top/index.php/archives/3/) by [Great Panoan](https://panoan.top/index.php/)

我在这里只记录一下重要的网址和一些代码

首先要安装python3,可以源码安装，也可以直接通过yum或者apt-get安装

然后安装autoclone

```
git clone https://github.com/xyou365/AutoRclone && cd AutoRclone && pip3 install -r requirements.txt
```

获取Python DriveApi 凭证

https://developers.google.com/drive/api/v3/quickstart/python

管理Google Group

https://groups.google.com/

查看ServiceAccount

https://console.cloud.google.com/projectselector2/iam-admin/serviceaccounts?pli=1&supportedpurview=project

基本上就上面这些东西，如果有不明白的可以到上面的那些链接里去问大佬，当然也可以发邮件给我，我尽力解答
