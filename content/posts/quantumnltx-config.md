---
title: "Quantumult X 相关配置问题"
date: 2020-05-03T18:43:06+08:00
#description: <descriptive text here>
# weight: 1
aliases: ["/2020/05/03/quantumnltx-config"]
tags: ["Quantumult X", "trojan"]
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

之前一直用的是Shadowrocket（俗称小火箭，用了快一年多了吧，感情还是挺深的），配置起来的确要简单很多，但功能也自然谈不上丰富，今天看自己的印度Apple ID里面还有800卢比，想着放里面也是无用，不如花了痛快，于是就果断买了Quantumult x（好像大家常把它叫做圈X）。

#### 1.购买之前

刚开始搜的时候出现了两个软件，Quantumult 和 Quantumult x，订阅价格差了20人民币左右，于是又在网上了解这两者的区别，总结来说，就是UI不一样，然后Quantumult x支持强大的JS脚本功能，对于喜欢瞎折腾的我当然是选择第二个完整版

![image-20200503202419197](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1gefj8wvh1kj309m05rmxt.jpg)



#### 2.寻找教程

在网上搜索了一下，进了非官方Tg群，这里有两个配置教程

Quantumult 完整教程: https://github.com/shigalin/Quantumult/blob/master/README.md

QuantumultX 用户教程: https://www.notion.so/kopshawn/Quantumult-X-1d32ddc6e61c4892ad2ec5ea47f00917

第一个相对比较简单，第二个就是进阶的操作了，不过这两个我都没怎么看

我打开了 https://merlinblog.xyz/wiki/quanx.html 这个网站，这个写的还是挺不错的，配置起来基本没啥难度

![image-20200503203413098](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1gefjgt1tk1j30j40cvabq.jpg)

最关键的网站出来了https://github.com/nzw9314/QuantumultX/tree/master 这个基本上包含了圈X的所有配置和脚本，而且还附有视频讲解，目前也一直在维护

#### 3.开始配置

具体过程我就不写了，上面的教程写的很清楚，我在这里只说几点我遇到的问题

自从去年GFW开始加大对ssr的封锁，我当时立即就决定用上给自己的服务器配置上trojan，用到现在也快有五六个月了吧，很久没用过ssr了，也很久没买过机场了，之前一直白嫖谷歌云，后面才开始买阿里云国际的3.5美元套餐，虽然各种服务比不上机场，但感觉用自己搭建的总是安全私密一点（可能是自己的心理作用吧）

好吧，回到正题，刚开始用圈X的时候我是懵逼的，这东西为什么不像小火煎那样，直接选择要连接的类型，然后在文本框中输入配置就算成功了，

![IMG_0070](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1gefjv6b5uxj30u01szjx5.jpg)

当然圈X也可以直接输入配置信息进行配置，不过只支持ss，先要用其它的协议，只能去编辑配置源文件，按照Quantumult X的示例文件中添加即可，就改几个参数而已

下面是trojan的配置，将example.com改成你自己的trojan域名，pwd改成自己的密码就可以了

```bash
trojan=example.com:443, password=pwd, over-tls=true, tls-verification=true, fast-open=false, udp-relay=false, tag=trojan-tls-01
```

![IMG_0071](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1gefk2jzrj9j30u01medmn.jpg)

界面其实还挺好看的

其实到这一步，基本上代理的功能就完成了，也就是小火箭的功能

#### 4.高级配置

在Quantumult X中有一个功能叫做重写，其实有点像我们在浏览器用到的js插件，也就是在页面中注入一些其它信息，比如逛京东时，可以看历史最低价

![IMG_0072](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1gefk7jqeqxj30u01meanl.jpg)

看netflix时，可以看这个节目在IMDB和豆瓣的评分

![IMG_0517](https://cdn.jsdelivr.net/gh/loyio/oss@main/blogs/2021/07/007S8ZIlly1gefk9uplh9j316d0u0k6p.jpg)

个人感觉是要方便很多

另一个高级一点的功能就是定时任务，执行js脚本，这个我觉得也挺有用的，比如各种签到任务啊，用Quantumult X的一个比较突出的一个特点就是获取cookie方便多了，不像我搞个签到网站，还要各种抓包，最后还不一定能成功，这里我不过多赘述了，再次贴上项目合集的网址

https://github.com/nzw9314/QuantumultX/tree/master