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

## 一.可分离变量的一阶微分方程

如果能够把一阶微分方程中所有关于 $y$ 的部分 (包括 $\mathrm{d}y$) 放在一边, 所有关于 $x$ 的部分 (包括 $\mathrm{d}x$) 放在另一边, 则该微分方程被称为是可分离变量的. 例如, 方程 $\mathrm{dy}/\mathrm{dx} = ky$ 可重新整理为
$$
\frac{1}{ky}\mathrm{d}y = \mathrm{d}x,
$$
就是可分离变量的。



然后继续计算的方法就是两遍加积分号求积分。然后再整理求得 $y$。

最终求得的全解，可能会包含一些常数变量。



如果在题干中，涉及到初值时，还是使用以上的求解方法，最后将初值代入求得的全解中，就可以得到未知常数$C$了。



## 二.一阶线性方程的求解

### 1.前言

形如
$$
\frac{\mathrm{d}y}{\mathrm{d}x}+p(x)y = q(x)
$$
其中 $p$ 和 $q$ 是关于 $x$ 的函数，这样的方程就称为***一阶线性微分方程***， 它可能不是可分离变量的, 甚至连线性看起来也不很明显! 例如,
$$
\frac{\mathrm{d} y}{\mathrm{~d} x}+6 x^{2} y=\mathrm{e}^{-2 x^{3}} \sin (x)
$$
就不像是线性的, 然而这个方程确实是一阶线性的, 因为 $y$ 和 $\mathrm{d}y/\mathrm{d}x$ 的幂次都是 1. 而方程
$$
\frac{\mathrm{d} y}{\mathrm{~d} x}+6 x^{2} y^{3}=\mathrm{e}^{-2 x^{3}} \sin (x)
$$
不是一阶线性的, 因为 $y^3$ 不是 $y$ 的一次

同样，上述式子也不是可分离变量的，我们无法得到一个一边只关于$x$ ，另一边只关于$y$的表达式。

​    

我们对上式两遍都乘以$\mathrm{e}^{2x^3}$,对右边进行了化简。得到以下表达式：
$$
\mathrm{e}^{2 x^{3}} \frac{\mathrm{d} y}{\mathrm{~d} x}+6 x^{2} \mathrm{e}^{2 x^{3}} y=\sin (x)
$$
观察左边的式子，我们根据求导乘积法则的逆用（即$(uv)' = u'v+uv'$），可以将$\mathrm{e}^{2 x^{3}} \frac{\mathrm{d} y}{\mathrm{~d} x}+6 x^{2} \mathrm{e}^{2 x^{3}}$改写成$\frac{\mathrm{d}}{\mathrm{d}x}(\mathrm{e}^{2 x^{3}}y)$，即$\mathrm{e}^{2 x^{3}}$乘以 $y$ 的导数。

然后得到下面的表达式：
$$
\frac{\mathrm{d}}{\mathrm{d}x}(\mathrm{e}^{2 x^{3}}y) = \sin{x}
$$
现在要做的就是两遍关于 $x$ 积分，这样，就消掉了左边的导数，剩下
$$
\mathrm{e}^{2 x^{3}} y=\int \sin (x) \mathrm{d} x=-\cos (x)+C
$$
最后除以$\mathrm{e}^{2x^3}$，得到解
$$
y=(C-\cos (x)) \mathrm{e}^{-2 x^{3}}
$$
其中$C$为任意常数，可以求导验证是否满足原微分方程。



### 2.积分因子

上述求解的关键是乘以$\mathrm{e}^{2x^3}$ . 之后, 我们能将左边整体写成 $\frac{\mathrm{d}}{\mathrm{d}x}$ (某式) 的形式, 这样就很容易积分了. 出于这个原因, $\mathrm{e}^{2x^3}$被称为积分因子. 可知, 对于一般一阶线性微分方程
$$
\frac{\mathrm{d} y}{\mathrm{~d} x}+p(x) y=q(x)
$$
积分因子由等式
$$
\text{积分因子}=e^{\int{p(x)\mathrm{d}x}}
$$
给出，这里不必对积分结果 $+C$. 在将原微分方程乘了这个积分因子之后，左边就可被"因式分解"成
$$
\frac{\mathrm{d}}{\mathrm{d}x}{(\text{积分因子}\times y)}
$$
​    

​    

下面我们通过一个例子来学习应用一下
$$
\frac{\mathrm{d} y}{\mathrm{~d} x}=\mathrm{e}^{x} y+\mathrm{e}^{2 x}, \quad y(0)=2(\mathrm{e}-1) ?
$$
这是一个IVP（初始值问题），第一件事是将其变成标准形式, 意思是需将所有关于 $y$ 的部分放在左边, 所有关于 $x$ 的部分放在右边, 且 $\mathrm{d}y/\mathrm{d}x$ 的系数要为 1. 在本例中, 我们只需两边减去 $e^xy$, 得
$$
\frac{\mathrm{d} y}{\mathrm{~d} x}-\mathrm{e}^{x} y=\mathrm{e}^{2 x}, \quad y(0)=2(\mathrm{e}-1)
$$
$y$ 的系数为$-e^x$，可以可以求得积分因子
$$
\text { 积分因子 }=\mathrm{e}^{\int\left(-\mathrm{e}^{x}\right) \mathrm{d} x}=\mathrm{e}^{-\mathrm{e}^{x}} \text { . }
$$
我们用这个积分因子乘以上述微分方程的两边：
$$
\mathrm{e}^{-\mathrm{e}^{x}} \frac{\mathrm{d} y}{\mathrm{~d} x}-\mathrm{e}^{x} \mathrm{e}^{-\mathrm{e}^{x}} y=\mathrm{e}^{-\mathrm{e}^{x}} \mathrm{e}^{2 x}
$$
跟之前的步骤一样，左边是积分因子乘 $y$ 的导数，所以得到下式：
$$
\frac{\mathrm{d}}{\mathrm{d} x}\left(\mathrm{e}^{-\mathrm{e}^{x}} y\right)=\mathrm{e}^{-\mathrm{e}^{x}} \mathrm{e}^{2 x}
$$
 当然也可以通过左边求导验证这个步骤是否正确。

然后，对上述方程的两边积分可得：
$$
\mathrm{e}^{-\mathrm{e}^{x}} y=\int \mathrm{e}^{-\mathrm{e}^{x}} \mathrm{e}^{2 x} \mathrm{~d} x
$$
求右边的积分，令 $t= e^x$，则 $\mathrm{d}t = e^x\mathrm{d}x$，主要运用分布积分法完成，最终结果方程为
$$
\mathrm{e}^{-\mathrm{e}^{x}} y=-\mathrm{e}^{x} \mathrm{e}^{-\mathrm{e}^{x}}-\mathrm{e}^{-\mathrm{e}^{x}}+C \text { . }
$$
最后，两边除以积分因子$e^{-\mathrm{e}^x}$可得
$$
y=-\mathrm{e}^x-1+C\mathrm{e}^{\mathrm{e}^x}
$$
对某常数 $C$ 成立，现在剩下的就是解初值问题，当 $x=0$ 时，我们直到 $y=2(\mathrm{e}-1)$，所以将这个带入上述方程，有
$$
2(\mathrm{e}-1)=-\mathrm{e}^{0}-1+C \mathrm{e}^{\mathrm{e}^{0}}
$$
很容易解出 $C=2$，故最后的解是
$$
y=2 \mathrm{e}^{\mathrm{e}^{x}}-\mathrm{e}^{x}-1
$$
可对其求导来验证它满足原微分方程
