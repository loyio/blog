---
title: "一阶微分方程与一阶线性方程的求解"
date: 2021-07-08T15:07:55+08:00
#description: <descriptive text here>
# weight: 1
# aliases: ["/first"]
tags: ["高等数学", "微积分", "微分方程","线性方程","一阶线性方程"]
categories: ["数学"]
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

## 1.可分离变量的一阶微分方程

如果能够把一阶微分方程中所有关于 $y$ 的部分 (包括 $\mathrm{d}y$) 放在一边, 所有关于 $x$ 的部分 (包括 $\mathrm{d}x$) 放在另一边, 则该微分方程被称为是可分离变量的. 例如, 方程 $\mathrm{dy}/\mathrm{dx} = ky$ 可重新整理为
$$
\frac{1}{ky}\mathrm{d}y = \mathrm{d}x,
$$
就是可分离变量的。



然后继续计算的方法就是两遍加积分号求积分。然后再整理求得 $y$。

