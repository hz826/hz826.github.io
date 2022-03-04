---
title: '2021 icpc网络赛 I. Discrete Mathmatics MSET反演'
date: 2021-09-25 00:00:00
tags: []
mathjax: true
description: 解析组合MSET构造的应用
---

<!--more-->

### 题目

给出质数 $p$ ，正整数 $n,k$ ，求多项式环 $\mathbb{F}_p[x]$ 中最高项为 $x^n$，$x^n$ 项系数为 $1$ ，$x^{n-1}$ 项系数为 $k$ 的不可约多项式数量，答案模 $998244353$



$5\le p\le n\le 2500,\ 0\le k < p$



<details>
    <summary>完整题面</summary>
	<img src="MSET-Inversion/2021-ICPC-online-I.jpg" style="zoom: 30%;" />
</details>

### 题解

（首先，$\mathbb{F}_p[x]$ 是 UFD ，可以唯一分解）



$F_n$ 表示 $n$ 阶首一不可约多项式数量

不考虑 $k$ 的限制，有方程 $\text{MSET}(F) = \frac1{1-px}$ ，其中 $\text{MSET}(F) = \prod (\frac1{1-x^i})^{F_i}$


取 ln，
$$
\sum F_i (x^i + \frac 12 x^{2i} + \frac 13 x^{3i} + \dots) = px+\frac 12 p^2x^2 + \frac 13 p^3x^3 + \dots
$$

考虑等式两边 $x^n$ 项系数，$\frac{1}{n} p^n = \sum_{d\mid n} F_d\cdot \frac{d}{n}$

用狄利克雷卷积的形式表示：$(nF_n)\ \ast \ I = (p^n)$ ，可解出 $F_n = \frac 1n \sum_{d\mid n} \mu(d) p^{n/d}$



---



现在加入 $k$ 的限制，设 $\omega^p = \omega^0$ ，$F_{n,k}$ 表示 $n$ 阶，次高项为 $k$ 的首一不可约多项式数量

方程变为
$$
\prod (\frac 1{1-x^i\omega^j})^{F_{i,j}} = 1 + \frac{x(\omega^0 + \dots+\omega^{p-1})}{1-px}
$$

同样取 ln，
$$
\small\sum F_{i,j} (x^i\omega^j + \frac 12 (x^i\omega^j)^2 + \frac 13 (x^i\omega^j)^3 + \dots) = (\omega^0 + \dots+\omega^{p-1})(x+\frac 12 px^2 + \frac 13 p^2x^3 + \dots)
$$
可同理解出 $F_{i,j}$ ，复杂度 $O(np\log n)$

