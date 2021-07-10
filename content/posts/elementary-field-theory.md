---
title: "场论初步"
date: 2021-07-10T10:27:37+08:00
#description: <descriptive text here>
# weight: 1
# aliases: ["/first"]
tags: ["场论初步", "方向导数", "梯度", "散度", "旋度"]
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

## 1.方向导数



### 方向导数的计算公式

设三元函数 $u=u(x,y,z)$ 在点 $P_0(x_0, y_0, z_0)$ 处可微分，则 $u=u(x,y,z)$ 在点 $P_0$ 处沿任意方向 $l$ 的方向导数都存在，且

{{<rawhtml>}}
$$
\frac{\partial u}{\partial l}\Bigl|_{P_{0}} =u'_{x}( P_{0})\cos \alpha +u'_{y}( P_{0})\cos \beta +u'_{z}( P_{0})\cos \gamma
$$
{{</rawhtml>}}



> 二元函数的情况与三元函数类似



## 2.梯度

在一个数量场中，函数在所给定点处沿不同的方向，其方向导数一般是不相同的。为研究沿哪一个方向其方向导数最大、或增加的速度最快，于是引入了一个重要的概念---梯度



设三元函数 $u=u(x,y,z)$ 在点 $P_0(x_0,y_0,z_0)$ 处具有一阶偏导数，则定义

{{<rawhtml>}}
$$
\operatorname{grad}\ u\Bigl|_{P_{0}} =( u'_{x}( P_{0}) ,\ u'_{y}( P_{0}) ,\ u'_{z}( P_{0}))
$$


{{</rawhtml>}}

为函数$u=u(x,y,z)$ 在点$P_0$处的梯度





## 3.方向导数与梯度的关系

由方向导数的计算公式 $\frac{\partial{u}}{\partial{l}}\bigl|_{P_0} = (u_x'(P_0),u_y'(P_0),u_z'(P_0))$与梯度的定义

{{<rawhtml>}}
$$
\operatorname{grad}\ u\Bigl|_{P_{0}} =( u'_{x}( P_{0}) ,\ u'_{y}( P_{0}) ,\ u'_{z}( P_{0}))
$$
{{</rawhtml>}}

可以得到

{{<rawhtml>}}
$$
\begin{aligned}
\left.\frac{\partial u}{\partial l}\right|_{P_{0}} &=\left(u_{x}^{\prime}\left(P_{0}\right), u_{y}^{\prime}\left(P_{0}\right), u_{z}^{\prime}\left(P_{0}\right)\right) \cdot(\cos \alpha, \cos \beta, \cos \gamma)=\left.\operatorname{grad} u\right|_{P_{0}} \cdot l^{\circ} \\
&=\left|\operatorname{grad} u\bigl|_{P_{0}}\right| | l^{\circ}|\cos \theta=\left| \operatorname{grad} u\bigl|_{P_{0}} \right| \cos \theta,
\end{aligned}
$$
{{</rawhtml>}}

其中 $\theta$ 为 $\operatorname{grad}u\bigl|_{P_0}$与 $l^\circ$的夹角，当$\cos{\theta}=1$时

$\displaystyle\frac{\partial{u}}{\partial{l}}\bigl|_{P_0}$有最大值

## 4.散度

设向量场 $A(x,y,z)=P(x,y,z)i+Q(x,y,z)j+R(x,y,z)k$,则
$$
\operatorname{div} A = \frac{\partial{P}}{\partial{x}}+\frac{\partial{Q}}{\partial{y}}+\frac{\partial{R}}{\partial{z}}
$$
叫**散度**。



## 5.旋度

设向量场$A(x,y,z)=P(x,y,z)i+Q(x,y,z)j+R(x,y,z)k$ ，则

{{<rawhtml>}}
$$
\operatorname{rot} \boldsymbol{A}=\left|\begin{array}{ccc}
\boldsymbol{i} & \boldsymbol{j} & \boldsymbol{k} \\
\frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\
P & Q & R
\end{array}\right|
$$


{{</rawhtml>}}

叫旋度



> $\operatorname{rot}A$表示场在$(x,y,z)$处最大旋转趋势的度量，若$\operatorname{rot}A=0$在场内处处成立，称 $A$为无旋场。
