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

### 1.$\frac{1}{1-x}$   
$$
\begin{aligned}\frac{1}{1-x} &=\quad1+x+x^{2}+x^{3}+x^{4}+\ldots \\\\&=\quad\sum_{n=0}^{\infty} x^{n}\end{aligned}
$$





当为几何级数时。只需将$x$视为$r$  
$x\in (-1,1)$
    
    

### 2. $e^x$   
$$
\begin{aligned}e^{x}\quad &=\quad 1+x+\frac{x^{2}}{2 !}+\frac{x^{3}}{3 !}+\frac{x^{4}}{4 !}+\ldots \\\\&=\quad\sum_{n=0}^{\infty} \frac{x^{n}}{n !}\end{aligned}
$$



### 3.$\cos{x}$

$$
\begin{aligned}\cos x\quad &=\quad1-\frac{x^{2}}{2 !}+\frac{x^{4}}{4 !}-\frac{x^{6}}{6 !}+\frac{x^{8}}{8 !}-\ldots \\\\&=\quad\sum_{n=0}^{\infty}(-1)^{n} \frac{x^{2 n}}{(2 n) !}\end{aligned}
$$



### 4.$\sin{x}$

$$
\begin{aligned}\sin x \quad &=\quad x-\frac{x^{3}}{3 !}+\frac{x^{5}}{5 !}-\frac{x^{7}}{7 !}+\frac{x^{9}}{9 !}-\ldots \\\\&=\quad \sum_{n=1}^{\infty}(-1)^{(n-1)} \frac{x^{2 n-1}}{(2 n-1) !} \stackrel{\text { or }}{=} \sum_{n=0}^{\infty}(-1)^{n} \frac{x^{2 n+1}}{(2 n+1) !}\end{aligned}
$$



### 5.$\ln{(1+x)}$

$$
\begin{aligned}\ln (1+x)\quad &=\quad x-\frac{x^{2}}{2}+\frac{x^{3}}{3}-\frac{x^{4}}{4}+\frac{x^{5}}{5}-\ldots \\\\&=\quad\sum_{n=1}^{\infty}(-1)^{(n-1)} \frac{x^{n}}{n} \stackrel{\text { or }}{=} \sum_{n=1}^{\infty}(-1)^{n+1} \frac{x^{n}}{n}\end{aligned}
$$



### 6.$\tan ^{-1} x$

$$
\begin{aligned}\tan ^{-1} x \quad &= \quad x-\frac{x^{3}}{3}+\frac{x^{5}}{5}-\frac{x^{7}}{7}+\frac{x^{9}}{9}-\ldots \\\\&= \quad\sum_{n=1}^{\infty}(-1)^{(n-1)} \frac{x^{2 n-1}}{2 n-1} \stackrel{\text { or }}{=} \sum_{n=0}^{\infty}(-1)^{n} \frac{x^{2 n+1}}{2 n+1}\end{aligned}
$$

