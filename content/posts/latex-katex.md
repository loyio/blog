---
title: "KaTeX(Latex)支持的TeX函数"
date: 2021-07-08T08:49:53+08:00
#description: <descriptive text here>
# weight: 1
aliases: ["/latex"]
tags: ["KaTex", "latex", "数学公式", "Tex", "字符排版"]
categories: ["Tex"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
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

## 字符与Unicode

### 希腊字母（Greek Letters）

#### 小写形式

| 渲染字符 | Katex | 渲染字符 | Katex | 渲染字符 | Katex | 渲染字符 | Katex |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| $\alpha$ | `\alpha` | $\beta$ | `\beta` | $\gamma$ | `\gamma` | $\delta$ | `\delta` |
|  $\epsilon$   |  `\epsilon`   |   $\zeta$   |   `\zeta`   | $\eta$ | `\eta` | $\theta$ | `\theta` |
|    $\iota$    |    `\iota`    |  $\kappa$   |  `\kappa`   | $\lambda$ | `\lambda` | $\mu$ | `\mu` |
|     $\nu$     |     `\nu`     |    $\xi$    |    `\xi`    | $\omicron$ | `\omicron` | $\pi$ | `\pi` |
|    $\rho$     |    `\rho`     |  $\sigma$   |  `\sigma`   | $\tau$ | `\tau` | $\upsilon$ | `\upsilon` |
|    $\phi$     |    `\phi`     |   $\chi$    |   `\chi`    |   $\psi$    |   `\psi`    |  $\omega$   |  `\omega`   |
| $\varepsilon$ | `\varepsilon` | $\varkappa$ | `\varkappa` | $\vartheta$ | `\vartheta` | $\thetasym$ | `\thetasym` |
|   $\varpi$    |   `\varpi`    |  $\varrho$  |  `\varrho`  | $\varsigma$ | `\varsigma` |  $\varphi$  |  `\varphi`  |
|  $\digamma$   |  `\digamma`   | $\varGamma$ | `\varGamma` | $\varDelta$ | `\varDelta` | $\varTheta$ | `\varTheta` |
| $\varLambda$  | `\varLambda`  |  $\varXi$   |  `\varXi`   |  $\varPi$   |  `\varPi`   | $\varSigma$ | `\varSigma` |
| $\varUpsilon$ | `\varUpsilon` |  $\varPhi$  |  `\varPhi`  |  $\varPsi$  |  `\varPsi`  | $\varOmega$ | `\varOmega` |

#### 大写形式

|  渲染字符  |   Katex    | 渲染字符 |  Katex   |  渲染字符  |   Katex    |  渲染字符  |   Katex    |
| :--------: | :--------: | :------: | :------: | :--------: | :--------: | :--------: | :--------: |
|  $\Alpha$  |  `\Alpha`  | $\Beta$  | `\Beta`  |  $\Gamma$  |  `\Gamma`  |  $\Delta$  |  `\Delta`  |
| $\Epsilon$ | `\Epsilon` | $\Zeta$  | `\Zeta`  |   $\Eta$   |   `\Eta`   |  $\Theta$  |  `\Theta`  |
|  $\Iota$   |  `\Iota`   | $\Kappa$ | `\Kappa` | $\Lambda$  | `\Lambda`  |   $\Mu$    |   `\Mu`    |
|   $\Nu$    |   `\Nu`    |  $\Xi$   |  `\Xi`   | $\Omicron$ | `\Omicron` |   $\Pi$    |   `\Pi`    |
|   $\Rho$   |   `\Rho`   | $\Sigma$ | `\Sigma` |   $\Tau$   |   `\Tau`   | $\Upsilon$ | `\Upsilon` |
|   $\Phi$   |   `\Phi`   |  $\Chi$  |  `\Chi`  |   $\Psi$   |   `\Psi`   |  $\Omega$  |  `\Omega`  |



## 操作符

### 大操作符

|  渲染操作符  |    Katex     |      说明      |                          举例                           |                       Katex函数                        |
| :----------: | :----------: | :------------: | :-----------------------------------------------------: | :----------------------------------------------------: |
|    $\sum$    |    `\sum`    |    求和符号    |            $\displaystyle\sum_{n=1}^{6}{4n}$            |           `\displaystyle\sum_{n=1}^{6}{4n}`            |
|   $\prod$    |   `\prod`    | 连乘、求积符号 | $\displaystyle\prod_{n=1}^{\infty}{(1-\frac{1}{4n^2})}$ | `\displaystyle\prod_{n=1}^{\infty}{(1-\frac{1}{4n^2})` |
| $\bigotimes$ | `\bigotimes` |                |                                                         |                                                        |
|  $\bigvee$   |  `\bigvee`   |                |                                                         |                                                        |
|    $\int$    |    `\int`    |    积分符号    |                 $\int_{0}^{t}{f(t)dt}$                  |                 `\int_{0}^{t}{f(t)dt}`                 |

