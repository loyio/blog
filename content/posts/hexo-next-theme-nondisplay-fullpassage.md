---
title: "Hexo Next Theme Nondisplay Fullpassage"
date: 2020-05-04T19:17:40+08:00
#description: <descriptive text here>
# weight: 1
aliases: ["/2020/05/04/hexo-next-theme-nondisplay-fullpassage"]
tags: ["Hexo", "Next Theme", "网站配置"]
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

使用Hexo配置自己的博客后，感觉很多方面都要轻松很多，一开始我是在Hexo Theme Page里面找到了一个比较好看的主题，奈何配置上之后，很多功能无法实现，且开发者好像也不再维护更新了，最终我还是决定使用Next博客，配置项的确是挺多的，所以功能也比较齐全，目前也有社区在维护更新

Next博客的主页总是会将你的文章全文显示出来，这样可读性是比较差的，如果你文章特别长的话，对于加载也有一定的影响，另一方面，没有目录，访问者无法清楚的找出自己要得到的内容

所以我觉得还是要设置一些，让主页不显示全文，



Google了一下，发现解决方法就是打开主题下的配置文件，将下面的enable改为true就可以了

```yaml
auto_excerpt:
  enable: false
```

奈何我在配置文件中根本就没找到这个关键词，可能是主题配置重写了吧，下面说说我的解决步骤

打开`themes/next` 目录下的 `config.yml` ，查看摘要描述是否为true，默认是开启的

```yaml
# Automatically excerpt description in homepage as preamble text.
excerpt_description: true
```

然后你有两种方法，让你文章在首页只显示部分

#### 1.写概述

在文章的最上面 `front-matter` 中添加 `description`,

然后在冒号后面写你这篇文章的概述，配置完成后，你的主页就只会显示这篇文章的`description`

```markdown
title: 文章标题
date: 2020-05-04 13:07:04
description: 首页的概述，正文内容不会显示
```

#### 2.截断文章

在需要截断的地方加入

```markdown
<!--more-->
```

这时候首页就只会显示这条语句以上的内容，隐藏语句后面的所有内容

两种方法，各有长处，大家可以自己斟酌使用
