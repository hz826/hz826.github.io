---
title: 'dp优化小结'
date: 2020-09-01 00:00:00
tags: []
published: true
hideInList: false
feature: 
isTop: true
mathjax: true
description: 四边形不等式的应用
---

<!--more-->

# dp优化小结

## 四边形不等式

注意：由于大于/小于的对称性，下文中数值的 $\ge$ 和 $\max$ 不一定是大于，可理解为 “优于”，而不考虑其实际意义

### 四边形不等式

如果二元函数 $f(l,r) \ (l<r)$ 满足 $\forall a\le b\le c\le d \quad f(a,c)+f(b,d) \ge f(a,d)+f(b,c)$ ，则称 $f$ 满足四边形不等式

<img src="DP-Optimizing/image-20210122225933198.png" alt="image-20210122225933198" style="zoom: 40%;" />

#### 基本性质：

1. 若 $f_1, f_2$ 都满足四边形不等式，那么 $f_1+f_2$ 也满足四边形不等式
2. $\forall g,h, \ f(l,r) = g(l)+h(r)$  满足四边形不等式

### 四边形不等式优化区间合并DP

对于形如 $f(l,r) = \max_{k\in[l,r)} \{f(l,k) + f(k+1,r)\} + w(l,r)$ 的dp方程，如果 $w$ 满足四边形不等式，这一类dp可以从 $O(n^3)$ 优化到 $O(n^2)$

证明：

设 $g(l,r)$ 表示在dp到区间 $[l,r]$ 时的某一个最优决策点（比较正式的写法是 $g(l,r)\in\text{argmax}_{k\in[l,r)} \{f(l,k) + f(k+1,r)\} $ ）

**证明一：$f$ 也满足四边形不等式**，下证 $\forall a<b<c<d \quad f(a,c)+f(b,d) \ge f(a,d)+f(b,c)$

设为 $p=g(b,c),\ q=g(a,d)$，由于对称性，不妨令 $p\le q$

<img src="DP-Optimizing/image-20210122230956751.png" alt="image-20210122230956751" style="zoom:40%;" />

因为 $p\le q$，显然有 $q\in[b,d)$ 

可以发现，对于区间$[a,c],[b,d]$ （红色区间），只要 $[a,c]$ 区间以 $p$ 为决策点，$[b,d]$ 区间以 $q$ 为决策点，
$$
\begin{aligned}
LHS-RHS &=\big(f(a,c)+f(b,d)\big) - \big(f(a,d)+f(b,c)\big)\\
&\ge\big(f(a,p)+f(p+1,c)+f(b,q)+f(q+1,d)\big)\\
&\qquad- \big(f(b,p)+f(p+1,c)+f(a,q)+f(q+1,d)\big)\\
&\qquad+ \big(w(a,c)+w(b,d)\big) - \big(w(a,d)+w(b,c)\big)\\
&=\big(f(a,p)+f(b,q)\big)-\big(f(b,p)+f(a,q)\big)\\
&\qquad+ \big(w(a,c)+w(b,d)\big) - \big(w(a,d)+w(b,c)\big)\\
&\ge\big(f(a,p)+f(b,q)\big)-\big(f(b,p)+f(a,q)\big)\\
\end{aligned}
$$
（最后一个式子得到了一个更小区间上的四边形不等式，可用归纳法证明，结合下图更明显）

<img src="DP-Optimizing/image-20210122231424937.png" alt="image-20210122231424937" style="zoom:40%;" />

**证明二：如果 $f$ 满足四边形不等式，可以证明** $\forall g(a,b),\exists g(a,c)$ 使得 $ g(a,b) \le g(a,c)$

反证法：设 $p=g(a,c),\ q=g(a,b),\ p<q$

<img src="DP-Optimizing/image-20210122233920387.png" alt="image-20210122233920387" style="zoom:50%;" />

那么对于区间 $[a,c]$ ,$p$ 优于 $q$；对于区间 $[a,b]$, $q$ 优于 $p$
$$
\begin{aligned}
&\begin{cases}
f(a,p)+f(p+1,c) \ge f(a,q)+f(q+1,c)\\
f(a,q)+f(q+1,b) \ge f(a,p)+f(p+1,b)\\
\end{cases}\\
\\
\Longrightarrow&
\begin{cases}
f(p+1,c)-f(q+1,c) \ge f(a,q)-f(a,p)\\
f(a,q)-f(a,p) \ge f(p+1,b)-f(q+1,b)\\
\end{cases}\\
\\
\Longrightarrow& f(p+1,c)-f(q+1,c) \ge f(p+1,b)-f(q+1,b)\\
\\
\Longrightarrow& f(q+1,b)+f(p+1,c) \ge f(p+1,b)+f(q+1,c)
\end{aligned}
$$
又因为四边形不等式，

所以 $\begin{cases}f(a,p)+f(p+1,c) = f(a,q)+f(q+1,c)\\f(a,q)+f(q+1,b) = f(a,p)+f(p+1,b)\end{cases}$ 同时成立

此时不只是 $p$，$q$ 也是区间 $[a,c]$ 的最优决策点



**由对称性，** $\forall g(l,r-1), g(l+1,r),\ \exists g(l,r) \in [g(l,r-1), g(l+1,r)]$

记录最优决策点，只在 $[g(l,r-1), g(l+1,r)]$ 枚举区间 $[l,r]$ 的决策点，通过势能分析，复杂度 $O(n^2)$

### 四边形不等式优化区间指定数量拆分dp（决策单调性）

对于形如 $f(i,r) = \max_{l\in[1,r)} \{f(i-1,l) + w(l,r)\}$ 的dp方程，如果 $w$ 满足四边形不等式，这一类dp可以通过**决策单调性**从 $O(mn^2)$ 优化到 $O(mn\log n)$ （$n$ 是区间长度，$m$ 是 $i$ 枚举的范围，也就是区间划分个数）

证明：

由四边形不等式基本性质， 设 $w'(l,r) = f(i-1,l) + w(l,r)$ ，$w'$ 满足四边形不等式

类似**证明二**，$\forall a<b$ ，假如 $a$的某个最优决策点为$q$，$b$的某个最优决策点为$p$， $p<q$ ，$\begin{cases}w'(p,b) \ge w'(q,b)\\w'(q,a) \ge w'(p,a)\end{cases}$，两式相加，再结合四边形不等式，可得 $p,q$ 都是 $a,b$ 的最优决策点

也就是说这一类dp的最优决策点单调



有两种实现方法：

1. **二分法**，一开始假设每个点的最优决策点为 $1$ ，依次枚举 $2-n$，假设枚举到 $i$ ，二分找到 $i$ 能成为最优决策点（比 $i-1$ 优）的最小位置

<center><font color=blue size=2>11111111111111111111111111111111111111111111111111111</center>
<center><font color=blue size=2>111111111111111111<font color=red size=2>22222222222222222222222222222222222</center>
<center><font color=blue size=2>111111111111111111<font color=red size=2>22222222222222<font color=green size=2>333333333333333333333</center>

2. **分治法**，要求出 $1-n$ 的最优决策点，先暴力枚举 $1-n$ 找到 $\frac n2$ 的最优决策点，然后分治处理

### 四边形不等式优化区间任意拆分dp（决策单调性）

对于形如 $f(r) = \max_{l\in[1,r)} \{f(l) + w(l,r)\}$ 的dp方程，如果 $w$ 满足四边形不等式，这一类dp可以通过**决策单调性**从 $O(n^2)$ 优化到 $O(n\log n)$

决策单调性证明和上一章相同

算法实现：

似乎只能用二分法实现，算法内容于上一章相同

## 其他

### 斜率优化

对于形如 $f_i=\max_{j< i}\{a_jb_i+c_j+d_i\}$，其中 $a$ 严格单调递增（如果 $\min$ 就递减），$b\ge 0$ 的dp方程可以用**斜率优化**从 $O(n^2)$ 优化到 $O(n)$

满足斜率优化条件的dp方程都满足四边形不等式：

只需要考虑 $a,b$，即 $\forall x\le y\le z\le w,\ a_xb_z + a_yb_w \ge a_xb_w + a_yb_z$
