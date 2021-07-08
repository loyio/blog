---
title: "常用的泰勒级数"
date: 2021-07-08T13:08:01+08:00
#description: <descriptive text here>
# weight: 1
# aliases: ["/first"]
tags: ["高等数学", "微积分", "泰勒公式", "泰勒级数"]
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

以下公式来源于[South Caolina](https://people.math.sc.edu/girardi/m142/handouts/10sTaylorPolySeries.pdf)

|                             级数                             |                             条件                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| $\begin{aligned}\frac{1}{1-x} \quad&=\quad1+x+x^{2}+x^{3}+x^{4}+\ldots \\&=\quad\sum_{n=0}^{\infty} x^{n}\end{aligned}$ |     当为几何级数时。只需将 x 视为 r<br />$x \in (-1,1)$      |
| $$\begin{aligned}e^{x}\quad &=\quad 1+x+\frac{x^{2}}{2 !}+\frac{x^{3}}{3 !}+\frac{x^{4}}{4 !}+\ldots \\&=\quad \sum_{n=0}^{\infty} \frac{x^{n}}{n !}\end{aligned}$$ | 举例<br/>$$\begin{array}{l}e=1+1+\frac{1}{2 !}+\frac{1}{3 !}+\frac{1}{4 !}+\ldots \\e^{(17 x)}=\sum_{n=0}^{\infty} \frac{(17 x)^{n}}{n !}=\sum_{n=0}^{\infty} \frac{17^{n} x^{n}}{n !}\end{array}$$<br />$x \in \Reals$ |
| $$\begin{aligned}\cos x \quad&=\quad1-\frac{x^{2}}{2 !}+\frac{x^{4}}{4 !}-\frac{x^{6}}{6 !}+\frac{x^{8}}{8 !}-\ldots \\&=\quad\sum_{n=0}^{\infty}(-1)^{n} \frac{x^{2 n}}{(2 n) !}\end{aligned}$$ | 注意 $y = \cos{x}$ 是一个偶函数（即 $\cos{(−x)} = +\cos{(x)}$）并且$y= \cos{x}$ 的泰勒级数只有偶数次幂。<br />$x \in \Reals$ |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |

