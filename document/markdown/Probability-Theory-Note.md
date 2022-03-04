---
title: '概率论学习笔记'
date: 2022-01-29 12:30:00
tags: []
mathjax: true
description: 大学文化课
---

## 概率公理化

定义全集为 $\Omega$ ，事件 $A$ 为 $\Omega$ 的子集 ，$\Omega$ 是事件，可数个事件的并也是事件，有限个事件的交、并也是事件

概率公理化：

1. $\forall A, P(A) \ge 0$

2. $P(\Omega) = 1$

3. 对于互不相容的 $A_1, A_2, \dots$ ，$P(\bigcup_{j=1}^\infty A_j) = \sum_{j=1}^\infty P(A_j)$

可以推出：$P(\varnothing) = 0$ ，$P(\overline A) = 1-P(A)$ 等性质



## 概率公式

### 加法公式

$P(A+B) = P(A) + P(B) - P(AB)$​

$P(\sum_{j=1}^n A_j) = \sum_{1\le j_1 < j_2 < \dots < j_m \le n} (-1)^{m+1} P(A_{j_1} A_{j_2} \dots A_{j_m})$ 

### 事件独立

称事件 $A,B$ 独立当且仅当 $P(AB) = P(A)P(B)$

### 条件概率

当事件 $A$ 发生时事件 $B$ 发生的概率： $P(B|A) = \frac{P(AB)}{P(A)}$

全概率公式：$P(B) = P(A)P(B|A) + P(\overline A)P(B|\overline A)$

贝叶斯公式：$P(A|B) = \frac{P(AB)}{P(B)} = \frac{P(A)P(B|A)}{P(B)}$

## 随机变量 / 向量

### 随机变量

考虑有概率得到不同实数值的变量 $X$ 

定义（概率）分布函数 $F(x) = P(X \le x)\ (-\infty < x < +\infty)$

如果 $F(x)$ 连续，$X$ 有（概率）密度 $F(x) = \int_{-\infty}^x f(s) \mathrm d s$

当 $F'(x)$ 存在时，$f(x) = F'(x)$ ，否则 $f(x)=0$


### 随机向量

联合分布函数：$F(x,y) = P(X\le x, Y\le y)$

边缘分布函数：$F_X(x) = P(X\le x),\ F_Y(y) = P(Y\le y)$

联合密度函数：$P((X,Y)\in D) = \iint_{D} f(x,y) \mathrm dx\mathrm dy$

独立性：$X,Y$ 独立 $\iff f(x,y) = f_X(x) f_Y(y) \iff P(X\le x, Y\le y) = P(X\le x)P(Y\le y)$



### 函数变换

#### 1D-1D

（要求 $h$ 单调）

$P(X=x) = \lim_{\Delta x \to 0} F(x) - F(x-\Delta x) = F'(x) \mathrm dx$

若 $P(X=x) = f(x) \mathrm dx$，$P(X=h(y)) = |f(h(y)) \mathrm d h(y)| = |h'(y)| f(h(y)) \mathrm dy$



$Y = h(X)$ ，已知 $X$ 概率密度函数 $f(x)$ ，求 $Y$ 概率密度函数 $g(y)$

微分法：
$$
\begin{aligned}
g(y) \mathrm dy &= P(Y=y)\\
&= P(X = h^{-1}(y)) = f(h^{-1}(y)) \mathrm dx\\
\\
x &= h^{-1}(y)\\
\mathrm dx &= (h^{-1}(y))' \cdot \mathrm dy
\end{aligned}
$$
积分法：
$$
\begin{aligned}
\int_{-\infty}^y g(t) \mathrm dt &= P(Y\le y)\\
&= P(h(X) \le y) = \int_{-\infty}^{h^{-1}(y)} f(x) \mathrm dx\\
\\
g(y) &= h^{-1}(y)'\cdot f(h^{-1}(y))
\end{aligned}
$$


#### 2D-1D

$U = u(X,Y), P(U\le u) = \iint \left[u(x,y) \le u\right] f(x,y) \mathrm dx\mathrm dy$

#### 2D-2D

$$
\begin{aligned}
P(X=x,Y=y) &= f(x,y) \mathrm dx\mathrm dy\\
P(U=u,V=v) &= P(X=x(u,v), Y=y(u,v))\\
&= f(x(u,v), y(u,v)) \mathrm dx\mathrm dy\\
&= f(x(u,v), y(u,v)) \left|\frac{\partial(x,y)}{\partial(u,v)}\right| \mathrm du\mathrm dv\\
\\
g(u,v) \mathrm du\mathrm dv &= f(x(u,v), y(u,v)) \mathrm dx\mathrm dy = f(x(u,v), y(u,v)) \left|\frac{\partial(x,y)}{\partial(u,v)}\right| \mathrm du\mathrm dv\\
\end{aligned}
$$



### 离散型随机变量

#### 二项分布

$X \sim \mathcal B(n,p),\ n\in \mathbb N^+, 0<p<1$

$P(X=k) = {n\choose k} p^k (1-p)^{n-k}, \ k=0,1,\dots,n$

$(px+(1-p))^{n} = \sum_{k=0}^n {n\choose k} (px)^k (1-p)^{n-k},\ \sum_{k=0}^n P(X=k) =1$

$n=1$​ 时也被称作伯努利分布（两点分布）

考虑 $\frac{P(X=k)}{P(X=k-1)}$ ，$P(X = \lfloor (n+1) p\rfloor)$​ 最大

$E(X) = np$

$Var(X) = npq$

#### 泊松分布

$X \sim \mathcal P(\lambda),\ \lambda > 0$

$P(X=k) = \frac{\lambda^k}{k!} e^{-\lambda},\ k=0,1,\dots$

$e^{\lambda x}e^{-\lambda} = \sum_{k=0}^\infty \frac{(\lambda x)^k}{k!}e^{-\lambda},\ \sum_{k=0}^\infty P(X=k) =1$

考虑 $\frac{P(X=k)}{P(X=k-1)}$ ，$P(X = \lfloor \lambda\rfloor)$ 最大



可加性：$X_1 \sim \mathcal P(\lambda_1), X_2 \sim \mathcal P(\lambda_2) \Longrightarrow X_1+X_2 \sim \mathcal P(\lambda_1+\lambda_2)$



和二项分布的关系：设 $X \sim \mathcal P(\lambda)$ ，$Y \sim \mathcal B(n,\frac{\lambda}{n})$

$$
\begin{aligned}
\lim_{n\to \infty} P(Y=k) &= \lim_{n\to \infty}{n\choose k} (\frac{\lambda}{n})^k (1-\frac{\lambda}{n})^{n-k}\\
&= \lim_{n\to \infty} \frac{n^{\underline k}}{k!}(\frac{\lambda}{n})^k (1-\frac{\lambda}{n})^{n-k}\\
&= \lim_{n\to \infty} \frac{\lambda^k}{k!}\ \frac{n^{\underline k}}{n^k} (1-\frac{\lambda}{n})^{n-k}\\
&= \frac{\lambda^k}{k!}\lim_{n\to \infty} (1-\frac{\lambda}{n})^{n}\\
&= \frac{\lambda^k}{k!} e^{-\lambda} = P(X = k)\\
\end{aligned}
$$

$E(X) = \lambda$

$Var(X) = \lambda$

#### 超几何分布

$X \sim H(N,M,n),\ N\ge M, N\ge n$

$P(X=m) = \frac{ {M \choose m} \cdot {N-M \choose n-m} }{N \choose n},\ m = 0,1,\dots,M$

这里不合法的组合数都为0

组合意义：$N$ 件产品中有 $M$ 件次品，从 $N$ 件产品中选出 $n$ 件，次品数为随机变量 $X \sim H(N,M,n)$

$P(X = \lfloor (n+1)\frac{M+1}{N+2}\rfloor)$ 最大



#### 几何分布

$0<p<1$

$P(X=k) = (1-p)^{k-1} p,\ k=1,2,\dots$  表示单次成功率为 $p$ 的试验第 $k$ 次终于成功的概率



$E(X) = \frac{1}{p}$

$Var(X) = \frac{1-p}{p^2}$



### 连续性随机变量

#### 均匀分布

$X \sim U(a,b),\ a<b$

$f(x) = \frac{1}{b-a}\ (x\in(a,b))$



$E(X) = \frac{a+b}{2}$

$Var(X) = \frac{(b-a)^2}{12}$

#### 指数分布

$X \sim Exp(\lambda),\ \lambda>0$

$f(x) = \lambda e^{-\lambda x}\ (x\ge 0)$

$\int_{0}^{+\infty} \lambda e^{-\lambda x} \mathrm dx = \left[-e^{-\lambda x}\right]_0^{+\infty} = 1$

无记忆性：$P(X>s+t \mid X>s) = P(x>t)$

$E(X) = \frac{1}{\lambda}$

$Var(X) = \frac{1}{\lambda^2}$

#### 正态分布

##### 标准正态分布

$\varphi(x) = \frac{1}{\sqrt{2\pi}} \exp(-\frac{x^2}{2})$ ，$\Phi(x) = \int_{-\infty}^x \varphi(s) \mathrm ds$ ，通过查表得到

证明：$\int_{-\infty}^{+\infty} \exp(-\frac{x^2}2) \mathrm dx = \sqrt{2\pi}$
$$
\begin{aligned}
(\int_{-\infty}^{+\infty} \exp(-\frac{x^2}2) \mathrm dx)^2 &= \iint_{R^2} \exp(-\frac{x^2+y^2}{2})\mathrm dx \mathrm dy\\
&= \int_{0}^{2\pi} \mathrm d\theta \int_{0}^{\infty} \exp(-\frac{r^2}{2}) r\mathrm dr\\
&= 2\pi \int_{0}^{\infty} e^{-\frac{r^2}{2}} r\mathrm dr\\
&= 2\pi \int_{0}^{\infty} e^{-\frac{r^2}{2}} \mathrm d\frac{r^2}{2}\\
&= 2\pi \int_{0}^{\infty} e^{-x} \mathrm dx = 2\pi\\
\end{aligned}
$$

##### 普通正态分布

$Z \sim N(0,1), \frac{X-\mu}{\sigma} = Z,\ X\sim N(\mu,\sigma^2),\ \sigma>0$

$f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} \exp \left[-\frac{(x-\mu)^2}{2\sigma^2}\right],\ (x\in \mathbb R)$

对于 $X\sim N(\mu,\sigma^2)$ ，$P(x \le a) = \int_{-\infty}^a \frac{1}{\sqrt{2\pi\sigma^2}} \exp \left[-\frac{(x-\mu)^2}{2\sigma^2}\right] \mathrm dx = \int_{-\infty}^{\frac{a-\mu}{\sigma}} \frac{1}{\sqrt{2\pi}} \exp(-\frac{x^2}{2})\mathrm dx = \Phi(\frac{a-\mu}{\sigma})$

$E(X) = \mu, Var(X) = \sigma^2$

期望为 $\mu$ ，方差为 $\sigma^2$ 的正态分布只有 $N(\mu,\sigma^2)$

##### 正态分布“脱靶量”

$X \sim N(0,1),\ Y \sim N(0,1),\ f(x,y) = \frac{1}{2\pi} \exp(-\frac{x^2+y^2}{2})$

$P(\sqrt{x^2+y^2} \le r) = \iint_D \frac{1}{2\pi} \exp(-\frac{x^2+y^2}{2}) \mathrm dx\mathrm dy = \frac{1}{2\pi} \int_{0}^{2\pi} \mathrm d\theta\int_0^r e^{-\frac{z^2}{2}} z\mathrm dz = \int_0^r e^{-\frac{z^2}{2}} z\mathrm dz$

$f(r) = re^{-\frac{r^2}2}$

##### 正态分布高阶矩

对于 $X\sim N(0,\sigma^2)$ ，求 $E(X^n) = \int_{-\infty}^{+\infty} x^n \frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{x^2}{2\sigma^2}} \mathrm dx$ ，当 $n$ 为奇数时显然为 $0$ ，下面只讨论 $n=2k$
$$
\begin{aligned}
\int_{-\infty}^{+\infty} u^n e^{-\frac{u^2}2} \mathrm du
&= 2\int_{0}^{+\infty} u^n e^{-\frac{u^2}2} \mathrm du\\
&= 2\int_{0}^{+\infty} (\sqrt{2t})^n e^{-t} \mathrm d(\sqrt{2t})\\
&= 2^{k+\frac12} \int_{0}^{+\infty} t^{k-\frac12} e^{-t}\mathrm dt\\
&= 2^{\frac{n+1}2} \Gamma(\frac{n+1}2)\\
&= (n-1)\cdot 2^{\frac{(n-2)+1}{2}} \Gamma(\frac{(n-2)+1}{2})\\
&= \dots\\
&= (n-1)\times(n-3)\times(n-5)\times\dots\times1\times \sqrt{2\pi}\\
&= (n-1)!!\times\sqrt{2\pi}\\
\\
E(X^n) &= \frac{1}{\sqrt{2\pi\sigma^2}}\int_{-\infty}^{+\infty} x^n e^{-\frac{x^2}{2\sigma^2}} \mathrm dx\\
&= \frac{\sigma^n}{\sqrt{2\pi}}\cdot \int_{-\infty}^{+\infty} u^n e^{-\frac{u^2}2} \mathrm du\\
&= \sigma^n \times (n-1)!!
\end{aligned}
$$

#### 二维正态分布

##### 标准二维正态分布

$\varphi(z_1,z_2) = \varphi(z_1) \varphi(z_2) = \frac{1}{2\pi} \exp(-\frac{z_1^2+z_2^2}{2})$

##### 二维正态分布

$(Z_1, Z_2)$ 服从标准二维正态分布，$\begin{cases}X_1 = aZ_1 + bZ_2 + \mu_1\\X_2 = cZ_1+dZ_2 + \mu_2\end{cases}, ad-bc \not=0$ ，$(X_1, X_2)$ 服从二维正态分布

$$
f(x_1,x_2) \mathrm dx_1\mathrm dx_2 = \varphi(z_1,z_2) \mathrm dz_1\mathrm dz_2 = \varphi(z_1,z_2) \left|\frac{\partial(x,y)}{\partial(u,v)}\right| \mathrm dx_1\mathrm dx_2\\

J = ad-bc,\ X_1' = X_1-\mu_1,\ X_2' = X_2-\mu_2\\

\begin{cases}
aZ_1+bZ_2 = X_1'\\
cZ_1+dZ_2 = X_2'
\end{cases}
\Longrightarrow
\begin{cases}
Z_1 = \frac1J (dX_1' - bX_2')\\
Z_2 = \frac1J (-cX_1' + aX_2')\\
\end{cases}\\
\left|\frac{\partial(x,y)}{\partial(u,v)}\right| = \frac1J\\
\\
\begin{aligned}
f(x_1,x_2) &= \frac{1}{2\pi J} \exp(-\frac{1}{2J^2} \left[(dX_1' - bX_2')^2 + (-cX_1' + aX_2')^2\right])\\
&= \frac{1}{2\pi J} \exp(-\frac{1}{2J^2} \left[(c^2+d^2) X_1'^2 - 2(ac+bd)X_1'X_2' + (a^2+b^2)X_2'^2\right])\\
\end{aligned}
\\
\\
\sigma_1 = \sqrt{a^2+b^2}, \sigma_2 = \sqrt{c^2+d^2},\ \rho = \frac{ac+bd}{\sigma_1\sigma_2}\\
\begin{aligned}
J^2 + (\rho\sigma_1\sigma_2)^2 &= (ad-bc)^2 + (ac+bd)^2\\
&= a^2d^2 + b^2c^2 + a^2c^2 + b^2d^2\\
&= (a^2 + b^2) (c^2 + d^2) = \sigma_1^2 \sigma_2^2\\
J^2 &= \sigma_1^2 \sigma_2^2 (1 - \rho^2)
\end{aligned}\\
\\
\begin{aligned}
f(x_1,x_2) &= \frac{1}{2\pi J} \exp(-\frac{1}{2J^2} \left[\sigma_2^2 X_1'^2 - 2(ac+bd)X_1'X_2' + \sigma_1^2X_2'^2\right])\\
&= \frac{1}{2\pi J} \exp(-\frac{\sigma_1^2\sigma_2^2}{2J^2} \left[\frac{X_1'^2}{\sigma_1^2} - \frac{2\rho X_1'X_2'}{\sigma_1\sigma_2} + \frac{X_2'^2}{\sigma_2^2}\right])
\end{aligned}\\
\\
f(x_1,x_2) = \small{\frac{1}{2\pi \sigma_1\sigma_2\sqrt{1-\rho^2}} \exp\left(-\frac{1}{2(1-\rho^2)}\left[\frac{(x_1-\mu_1)^2}{\sigma_1^2}-\frac{2\rho (x_1-\mu_1)(x_2-\mu_2)}{\sigma_1\sigma_2}+\frac{(x_2-\mu_2)^2}{\sigma_2^2}\right]\right)}
$$
称 $(X_1,X_2) \sim N(\mu_1,\mu_2;\sigma_1^2,\sigma_2^2;\rho)$

$X_1$ 的边缘概率密度：
$$
\begin{aligned}
f_{X_1}(x) &= \small{\int_{-\infty}^{+\infty}\frac{1}{2\pi \sigma_1\sigma_2\sqrt{1-\rho^2}} \exp\left(-\frac{1}{2(1-\rho^2)}\left[\frac{X_1'^2}{\sigma_1^2}-\frac{2\rho X_1'X_2'}{\sigma_1\sigma_2}+\frac{X_2'^2}{\sigma_2^2}\right]\right)\mathrm dX_2'}\\
&= \small{\int_{-\infty}^{+\infty}\frac{1}{2\pi \sigma_1\sigma_2\sqrt{1-\rho^2}} \exp\left(-\frac{1}{2(1-\rho^2)}\left[\frac{(1-\rho^2)X_1'^2}{\sigma_1^2}+\frac{\rho^2X_1'^2}{\sigma_1^2}-\frac{2\rho X_1'X_2'}{\sigma_1\sigma_2}+\frac{X_2'^2}{\sigma_2^2}\right]\right)\mathrm dX'_2}\\
&= \small{\frac{1}{2\pi \sigma_1\sigma_2\sqrt{1-\rho^2}} \exp(-\frac{X_1'^2}{2\sigma_1^2})\ \int_{-\infty}^{+\infty}\exp\left(-\frac{1}{2(1-\rho^2)}\left[\frac{\rho X_1'}{\sigma_1}-\frac{X_2'}{\sigma_2}\right]^2\right)\mathrm dX'_2}\\
\end{aligned}
$$

$$
\begin{aligned}
\small{\int_{-\infty}^{+\infty}\exp\left(-\frac{1}{2(1-\rho^2)}\left[\frac{\rho X_1'}{\sigma_1}-\frac{X_2'}{\sigma_2}\right]^2\right)\mathrm dX'_2} &= \small{\sigma_2\sqrt{1-\rho^2} \int_{-\infty}^{+\infty}\exp\left(-\frac{1}{2}(\frac{\frac{\rho X_1'}{\sigma_1}-\frac{X_2'}{\sigma_2}}{\sqrt{1-\rho^2}})^2\right)\mathrm d \frac{\frac{X_2'}{\sigma_2}-\frac{\rho X_1'}{\sigma_1}}{\sqrt{1-\rho^2}}}\\
&= \sigma_2\sqrt{1-\rho^2} \int_{-\infty}^{+\infty} \exp(-\frac12 t^2) \mathrm dt\\
&= \sigma_2\sqrt{1-\rho^2} \sqrt{2\pi}
\end{aligned}
$$

$$
\begin{aligned}
f_{X_1}(x) &= \frac{1}{2\pi \sigma_1\sigma_2\sqrt{1-\rho^2}} \exp(-\frac{X_1'^2}{2\sigma_1^2})\sigma_2\sqrt{1-\rho^2} \sqrt{2\pi}\\
&= \frac{1}{\sqrt{2\pi} \sigma_1} \exp(-\frac{X_1'^2}{2\sigma_1^2}) = \frac{1}{\sqrt{2\pi} \sigma_1} \exp(-\frac{(x-\mu_1)^2}{2\sigma_1^2})
\end{aligned}
$$

$(X_1,X_2) \sim N(\mu_1,\mu_2;\sigma_1^2,\sigma_2^2;\rho) \Longrightarrow X_1 \sim N(\mu_1,\sigma_1^2)$

$X_1,X_2$ 独立 $\iff \rho=0$

正态分布的非零线性组合也是正态分布



$Cov(X_1,X_2) = ac+bd,\ \rho(X_1,X_2) = \rho$

#### 伽马分布

引入伽马函数 $\Gamma(\alpha) = \int_0^\infty x^{\alpha-1} e^{-x} \mathrm dx$ ，$\forall \alpha>0, n\in \mathbb N^+,\ \Gamma(1+\alpha) = \alpha \Gamma(\alpha), \ \Gamma(n) = (n-1)!,\ \Gamma(\frac{1}{2}) = \sqrt{\pi}$

$X \sim \Gamma(\alpha,\beta),\ \alpha,\beta > 0$

$f(x) = \frac{\beta^\alpha}{\Gamma(\alpha)} x^{\alpha-1} e^{-\beta x}$



### 期望和方差

#### 期望

期望 $E(X) = \sum p_i x_i$ （离散型）  $E(X) = \int_{-\infty}^{+\infty} xf(x) \mathrm dx$ （连续性）

$\forall X,Y,\ E(X+Y) = E(X) + E(Y), E(\lambda X) = \lambda E(X)$

$X,Y$ 独立时，$E(XY) = E(X)E(Y)$

内积不等式：$EX^2,EY^2<+\infty,\ |E(XY)| \le \sqrt{EX^2EY^2}$ 当前仅当存在不全为0的 $a,b$ 满足 $P(aX+bY=0)=1$ 时等号成立（类似柯西不等式，用二次型证明）

#### 方差

方差 $Var(X) = \sigma_{XX} = E(X-\mu_X)^2 = EX^2 - (EX)^2,\ \mu_X = \overline{X}$

标准差 $\sigma_X = \sqrt{Var(X)}$

$\forall X,\ Var(a+bX) = b^2 Var(X)$

当 $X_1,X_2,\dots X_n$ 独立时，$Var(\sum X_i) = E\left(\sum (X_i - \mu_{i})\right)^2 = \left[\sum E (X_i - \mu_{i})^2\right] + \sum E(X_i - \mu_{i})E(X_j - \mu_{j}) = \sum Var(X_i)$

#### 协方差

协方差 $\sigma_{XY} = Cov(X,Y) = E\left[(X-\mu_X)(Y-\mu_Y)\right]$

相关系数 $\rho_{XY} = \frac{\sigma_{XY}}{\sigma_X\sigma_Y} = Cov(\frac{X-\mu_X}{\sigma_X},\frac{Y-\mu_Y}{\sigma_Y})$ ，$|\rho| \le 1$，$\rho=0$ 时 $X,Y$ 不相关（不相关不一定独立，只是无明显线性关系，独立一定不相关），$\rho=\pm 1$ 时 $X,Y$ 有线性关系

$Cov(X,Y) = E(XY) - (EX)(EY)$

$Cov(aX+bY,Z) = aCov(X,Z) + bCov(Y,Z)$

$Var(X\pm Y) = Var(X) + Var(Y) \pm 2Cov(X,Y)$ （证明：$Var(X) = Cov(X,X)$）

#### 协方差矩阵

随机向量 $(X_1,X_2)$ 的协方差矩阵 $\Sigma = \left(\begin{array}\\ \sigma_{11} & \sigma_{12} \\ \sigma_{21} & \sigma_{22}\end{array}\right)$

协方差矩阵是对称矩阵、半正定矩阵

> 实对称矩阵$A$称为半正定的，当且仅当对于任意不为$0$的实列向量$x$，都有$x^TAx\ge 0$.
>
> 半正定矩阵的行列式是非负的

$\forall a,\ a^T\Sigma a = \sum_{i,j} a_i E(X_i-\mu_{i})(X_j-\mu_{j})a_j = E(\sum_{i,j} a_i(X_i-\mu_{i}))^2 \ge 0$



## 大数律

> $(X_n)_{n\ge 1}$ 是随机事件列，分布函数为 $(F_n(x))_{n\ge 1}$，$X$ 是随机事件，分布函数为 $F(x)$
>
> 依分布收敛：$\lim_{n\to\infty} F_n(x) = F(x)$
>
> 依概率收敛：$\forall \varepsilon>0,\ \lim_{n\to\infty} P(|X_n-X| > \varepsilon) = 0$
>
> 以概率1收敛：$P(\lim_{n\to\infty} X_n = X) = 1$
>
> 依概率1收敛(a.s.)（几乎处处收敛(w.p.1)）> 依概率收敛(p) > 依分布收敛(d)

### 强大数律

随机变量 $X_1,X_2,\dots$ 独立同分布，$E X_1 = \mu$，$\lim_{n\to\infty} \overline{X}_n = \mu$ 以概率$1$成立

也称Kolmogorov's law，证明比弱大数律复杂

（几乎处处收敛）

### 切比雪夫不等式

$X$ 为一随机变量，$\forall \varepsilon>0,\ P(|X-\mu| \ge \varepsilon) \le \frac{1}{\varepsilon^2} Var(X)$

证明：
$$
\begin{aligned}
P(|X-\mu| \ge \varepsilon) &= \int_{|X-\mu| \ge \varepsilon} f(x) \mathrm dx\\
&\le \int_{|X-\mu| \ge \varepsilon} \left(\frac{x-\mu}{\varepsilon}\right)^2f(x) \mathrm dx\\
&\le \int_{R} \left(\frac{x-\mu}{\varepsilon}\right)^2f(x) \mathrm dx = \frac{1}{\varepsilon^2} Var(X)\\
\end{aligned}
$$

### 切比雪夫大数律

随机变量 $X_1,X_2,\dots$ 独立（不需要同分布），期望存在，方差有相同上界 $M$ 

$\lim_{n\to \infty} P(|\overline{X}_n - \overline{\mu}_n| \ge \varepsilon)\ \le\  \lim_{n\to \infty} \frac{1}{\varepsilon^2} Var(\overline{X}_i)\ \le\ \lim_{n\to \infty} \frac{M}{n\varepsilon^2} = 0$

### 辛钦大数律

随机变量 $X_1,X_2,\dots$ 独立同分布，期望存在

$\lim_{n\to \infty} P(|\overline{X}_n - \overline{\mu}_n| \ge \varepsilon)\ \le\ \lim_{n\to \infty} \frac{M}{n\varepsilon^2} = 0$

未找到证明

（依概率收敛）

### 中心极限定律

随机变量 $X_1,X_2,\dots$ 独立同分布，$E X_1 = \mu,\ Var(X_1) = \sigma^2 > 0$

对于较大的 $n$，$Z_n = \frac{\overline{X}_n - \mu}{\sqrt{\sigma^2/n}} \sim N(0,1)$，$\overline{X}_n \sim N(\mu, \frac{\sigma^2}{n})$ ，部分和 $S_n \sim N(n\mu, n\sigma^2)$ 近似成立

（依分布收敛）

对于离散型随机变量，$P(X=k)$ 需要变换为 $P(k-0.5\le X \le k+0.5)$

如果 $\sigma$ 未知，可以用 $\begin{cases}\hat{\sigma}^2 = \frac{1}{n-1} \sum_{j=1}^n (X_i - \overline X_i)^2\\\hat{\sigma}^2 = \frac{1}{n} \sum_{j=1}^n (X_i - \overline X_i)^2\end{cases}$ 代替



$\overline X_n \sim N(\mu_1, \frac{\sigma_1^2}{n}), \overline Y_m \sim N(\mu_2, \frac{\sigma_2^2}{m}),\ (\overline X_n - \overline Y_m) \sim N(\mu_1-\mu_2, \frac{\sigma_1^2}{n}+\frac{\sigma_2^2}{m})$

$\frac{(\overline X_n - \overline Y_m) - (\mu_1-\mu_2)}{\sqrt{\sigma_1^2/n+\sigma_2^2/m}} \sim N(0,1)$



## 参数估计

$X_1,X_2,\dots X_n$ 独立且与 $X$ 同分布，称 $X$ 是总体，$X_1,X_2,\dots X_n$ 是总体的样本，$x_1,x_2,\dots x_n$ 是样本的观测值

$\theta$ 是 $X$ 的未知参数，函数 $g(x_1,x_2,\dots x_n)$ 的值 $\hat \theta$ 称作估计量/统计量，估计量由函数 $g$ 和输入 $x_1,x_2,\dots, x_n$ 决定，当 $X_1,X_2,\dots,X_n$ 未确定时（为随机变量），$\hat \theta$ 同样为随机变量



无偏估计：$E \hat \theta = \theta$

如果 $\hat \theta_1 = \hat \theta_2$ 都是无偏估计，$Var(\hat \theta_1) < Var(\hat \theta_2)$ ，则称 $\hat \theta_1$ 比 $\hat \theta_2$ 更有效



相合估计：$n\to \infty$ ，$\hat \theta$ 依概率收敛到 $\theta$

强相合估计：$n\to \infty$ ，$\hat \theta$ 以概率$1$收敛到 $\theta$，（强相合估计一定是相合估计）



### 样本均值

样本均值 $\hat \mu = \overline X_n$ 是对期望的无偏估计、强相合估计（强大数律），且 $\overline X_n$ 比 $\overline X_{n-1}$ 更有效

### 样本方差

定义 $\hat \mu = \overline X_n,\ \mu = EX$ ，总方差 $\sigma^2 = Var(X)$ 的估计由样本方差 $S^2 = \frac{1}{n-1} \sum_{j=1}^{n} (X_j - \hat \mu)^2$ 表示

$S^2$ 是对 $\sigma^2$ 的无偏估计



证明 $E(S^2) = \sigma^2$
$$
\begin{aligned}
E(S^2) &= E\left( \frac{1}{n-1} \sum_{j=1}^{n} (X_j - \hat \mu)^2 \right)\\
&= \frac{1}{n-1} E\left((\sum_{j=1}^{n} X_j^2) - n\hat\mu^2\right)\\
&= \frac{n}{n-1} E(X^2) - \frac{1}{n(n-1)} E\left((\sum_{j=1}^{n} X_j)^2\right)\\
&= \frac{n}{n-1} E(X^2) - \frac{1}{n(n-1)} E\left(\sum_{j=1}^{n} X_j^2 + \sum_{i\not=j} X_i X_j\right)\\
&= \frac{n}{n-1} E(X^2) - \frac{1}{n(n-1)} \left(nE(X^2) + n(n-1) (EX)^2\right)\\
&= E(X^2) - (EX)^2 = \sigma^2
\end{aligned}
$$
$S^2\to \sigma^2$ 以概率$1$成立，$S^2$ 是 $\sigma^2$ 的强相合估计

### 样本标准差

$S = \sqrt{\frac{1}{n-1} \sum_{j=1}^{n} (X_j - \hat \mu)^2}$

因为$S^2$ 是 $\sigma^2$ 的强相合估计，所以$S$ 是 $\sigma$ 的强相合估计

但不是无偏估计（$ES = E(S\cdot 1) < \sqrt{ES^2 \cdot E1^2} = \sigma$）



### 样本矩

定义 $\mu_k = EX^k, \ (k\ge 1)$

定义 $k$ 阶样本矩 $\hat\mu_k = \frac{1}{n} \sum_{j=1}^n X_i^k$ ，$\hat\mu_k$ 是 $\mu_k$ 的强相合无偏估计（证明与样本均值相同）



### 矩估计

使用样本矩取代（未知的）总体矩，解出感兴趣的参数，只使用了部分信息，有偏差



举例：

$X \sim P(\lambda)\ \Longrightarrow\  \lambda=\mu\ \Longrightarrow\ \hat \lambda = \hat \mu_1$

$X \sim Exp(\lambda)\ \Longrightarrow\ \lambda=\frac{1}{\mu}\ \Longrightarrow\ \hat \lambda = \frac{1}{\hat\mu_1}$

$X \sim N(\mu,\sigma^2)\ \Longrightarrow\ \sigma^2=\mu_2-\mu_1^2\ \Longrightarrow\ \hat \sigma^2 = \hat \mu_2 - \hat \mu_1^2$

例如在正态分布中，矩估计有一定偏差



### 最大似然估计（MLE）

#### 离散型

定义似然函数 $L(\theta) = P(X_1=x_1,X_2=x_2,\dots, X_n=x_n)$，$\hat \theta$ 为 $L(\theta)$ 的最大值点

对数似然函数 $l(\theta) = \ln L(\theta)$ 和 $L(\theta)$ 有相同最大值点，一般用 $l'(\theta)=0$ 解出 $\hat \theta$



#### 连续性

$L(\vec \theta) = f(x_1,x_2,\dots,x_n;\vec \theta) = \prod f(x_j; \vec \theta),\quad l(\vec \theta) = \sum \ln f(x_j; \vec \theta)$

解似然方程组 $\frac{\partial l(\vec \theta)}{\partial \theta_j} = 0,\ j=1,2,\dots,n$



## 抽样分布

### $\chi^2$ 分布

独立随机变量 $X_1,X_2,\dots,X_n$ 都服从 $N(0,1)$ ，$\xi^2 = \sum_{i=1}^n X_i^2\sim \chi^2(n)$

$n$ 为自由度

$E(\chi^2(n)) = n$

$Var(\chi^2(n)) = 2n$

### t 分布

设 $Z, \xi_n^2$ 独立，$Z \sim N(0, 1),\ ξ_n^2 ∼ \chi^2 (n)$，则称 $T_n = \frac{Z}{\sqrt{\xi_n^2/n}} \sim t(n)$

$E(t(n)) = 0$

$Var(t(n)) = \frac{n}{n-2}$

### F 分布

$\xi,\eta$ 独立，$\xi^2 \sim \chi^2(n),\ \eta^2 \sim\chi^2(m)$ ，则称 $F = \frac{\xi^2/n}{\eta^2/m} \sim F(n,m)$



### 结论

定义 $X_i \sim N(\mu,\sigma^2),\ Z_i \sim N(0,1),\ \xi_n^2 \sim \chi^2(n)$ ，两两独立，$S^2$ 为样本方差

有以下结论：

1 :  $\overline X$ 与 $S^2$ 独立

2 : $\frac{(n-1)S^2}{\sigma^2} \sim \chi^2(n-1)$

> 只需证明：$\sum_{i=1}^n(Z_i-\overline Z)^2 \sim \chi^2(n)$
> $$
> \begin{aligned}
> \sum_{i=1}^n (Z_i - \overline Z)^2
> &= \sum_{i=1}^n Z_i^2 - 2Z_i\overline Z + \overline Z^2\\
> &= \left(\sum_{i=1}^n Z_i^2\right) - n\overline Z^2\\
> &= \left(\sum_{i=1}^n Z_i^2\right) - \frac1n(\sum_{i=1}^n Z_i)^2\\
> &= \frac{n-1}{n}\left(\sum_{i=1}^n Z_i^2\right) - \frac2n\sum_{i=1}^n\sum_{j=i+1}^n Z_iZ_j\\
> &= \mathbf Z^T \mathbf A \mathbf Z\\
> \mathbf A &= \left(\begin{matrix}
> \frac{n-1}{n} & -\frac{1}{n} & -\frac{1}{n} & \cdots & -\frac{1}{n}\\
> -\frac{1}{n} & \frac{n-1}{n} & -\frac{1}{n} & \cdots & -\frac{1}{n}\\
> -\frac{1}{n} & -\frac{1}{n} & \frac{n-1}{n} & \cdots & -\frac{1}{n}\\
> \vdots & \vdots & \vdots & \ddots & \vdots\\
> -\frac{1}{n} & -\frac{1}{n} & -\frac{1}{n} & \cdots & \frac{n-1}{n}\\
> \end{matrix}\right)\\
> |\lambda \mathbf I-\mathbf A| = 0 &\Longrightarrow (\lambda-1)^{n-1} \lambda\\
> \exists \mathbf Q^T\mathbf A\mathbf Q &= \left(\begin{matrix}
> 1 & 0 & \cdots & 0 & 0\\
> 0 & 1 & \cdots & 0 & 0\\
> \vdots & \vdots & \ddots & \vdots & \vdots\\
> 0 & 0 & \cdots & 1 & 0\\
> 0 & 0 & \cdots & 0 & 0\\
> \end{matrix}\right)\\
> \end{aligned}
> $$

$$
\begin{aligned}
\\
&\frac{\overline X-\mu}{\sigma/\sqrt{n}} \sim N(0,1)\\
\\
&\frac{\overline X_n - \mu}{S / \sqrt{n}} \sim t(n-1)\\
\\
&\frac{S_1^2/S_2^2}{\sigma_1^2/\sigma_2^2} \sim F(n-1,m-1)\\
\end{aligned}
$$


$$
E\left(\frac{(n-1)S^2}{\sigma^2}\right) = n-1 \Longrightarrow E(S^2) = \sigma^2\\
Var\left(\frac{(n-1)S^2}{\sigma^2}\right) = 2(n-1) \Longrightarrow Var(S^2) = \frac{2\sigma^4}{n-1}\\
$$
