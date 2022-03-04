---
title: '有标号树计数杂谈'
date: 2021-11-14 12:30:00
tags: []
mathjax: true
description: 有标号树计数的一种较通用的EGF处理方法

---

<!--more-->

## 有标号树计数杂谈

### 通过 Purfer 序列得到的性质

$T_n$ 表示 $n$ 个节点的有标号有根树数量，$T(z)$ 为其 EGF
$$
\begin{aligned}
T_n &= \begin{cases}n^{n-1} & n \ge 1\\ 0 & n=0\end{cases}\\
T(z) &= \sum_{k\ge 0} T_k\ \frac{z^k}{k!}\\
&= \sum_{k\ge 1} k^{k-1}\ \frac{z^k}{k!}\\
\end{aligned}
$$

### 组合意义及其EGF表达式

#### 1 ：删去根节点得到森林

$$
\begin{aligned}
\frac{T_n}{n} &= (n-1)! \left[z^{n-1}\right] \sum_{d=1}^n \frac{1}{d!} T^d\\
T &= z\cdot \exp(T)
\end{aligned}
$$

##### 自洽性证明 - 拉格朗日反演

$$
\begin{aligned}
T &= z \cdot \exp(T)\\
T^{-1} &= z e^{-z}\\
\left[z^n\right] T &= \frac{1}{n} \left[z^{n-1}\right] (\frac{z}{T^{-1}})^n\\
&= \frac{1}{n} \left[z^{n-1}\right] e^{nz}\\
&= \frac{n^{n-1}}{n!}
\end{aligned}
$$

##### 自洽性证明 - 求导化简


$$
\begin{aligned}
T &= z \cdot \exp(T)\\
T &= \ln T - \ln z\\
T' &= \frac{T'}{T} - \frac{1}{z}\\
zT' &= \frac{zT'}{T} - 1\\
zTT' &= zT' - T\\
\end{aligned}
$$

#### 2：删去任意一条边得到两棵树

$$
\begin{aligned}
2(n-1)\cdot \frac{T_n}{n} &= n! \left[z^n\right] T^2\\
\end{aligned}
$$

> 前置知识：EGF 的基本性质
>
> $T(z) = \sum_{k\ge 0} T_k\ \frac{z^k}{k!}$
>
> $T'(z) = \sum_{k\ge 1} T_{k}\ \frac{z^{k-1}}{(k-1)!}$
>
> $\int T(z) = \sum_{k\ge 0} T_{k}\ \frac{z^{k+1}}{(k+1)!}$
>
> $\frac{1}{z} T(z) = \sum_{k\ge 1} \frac{T_k}{k}\ \frac{z^{k-1}}{(k-1)!}$
>
> $z T(z) = \sum_{k\ge 0} (k+1)T_k\ \frac{z^{k+1}}{(k+1)!}$

##### 自洽性证明 - 求导化简

$$
\begin{aligned}
2(n-1)\cdot \frac{T_n}{n} &= n! \left[z^n\right] T^2\\
T - \int\frac{T}{z}\mathrm{d}z &= \frac{1}{2} T^2\\
T' - \frac{T}{z} &= TT'\\
zT'-T &= zTT'\\
\end{aligned}
$$

#### 3：删去任意两个点连成的链得到森林

$$
\begin{aligned}
n(n-1)\frac{T_n}{n}& = n! \left[z^n\right]\sum_{k\ge 2} T^k\\
\end{aligned}
$$

##### 自洽性证明 - 求导化简

$$
\begin{aligned}
n(n-1)\frac{T_n}{n}& = n! \left[z^n\right]\sum_{k\ge 2} T^k\\
\sum_{k\ge1} (k-1)T_k\ \frac{z^k}{k!} &= \sum_{k\ge 2} T^k\\
(zT)' - 2T &= \frac{T^2}{1-T}\\
zT' - T &= \frac{T^2}{1-T}\\
(1-T)(zT' - T) &= T^2\\
zT'-T-zTT' &= 0\\
\end{aligned}
$$

### 应用

求 $\sum_{T \in \text{tree}(n)} \sum_{i=1}^n \sum_{j=1}^n \text{dis}^2(i,j) $ ：

$$
\begin{aligned}
n(n-1)\frac{T_n}{n} &= n! \left[z^n\right]\sum_{k\ge 1} T^k\\
\\
\sum_{T \in \text{tree}(n)} \sum_{i=1}^n \sum_{j=1}^n \text{dis}^2(i,j) &= \sum_{k\ge 1} \left[z^n\right] T^k (k-1)^2\\
F_n &= n!\left[z^n\right]\big(\sum_{k\ge 0} T^k (k^2-2k+1) \big)- 1\\
F &= \frac{2}{(1-T)^3} - \frac{5}{(1-T)^2} + \frac{4}{1-T} - 1\\
&= \frac{1-3T+4T^2}{(1-T)^3} - 1\\
\end{aligned}
$$

