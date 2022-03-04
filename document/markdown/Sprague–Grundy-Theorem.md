---
title: '简单无偏博弈'
date: 2021-11-01 22:48:51
tags: []
mathjax: true
description: 对无偏博弈、SG函数及其拓展的简单讨论和部分证明
---

<!--more-->

# 简单无偏博弈

**无偏博弈(Impartial Game)**，指**状态可行的移动**与当前**轮到的人**无关的双人游戏，而且有完全信息、无随机、有限步终止，状态间的转移形成一个 DAG（Graph Games）

在无偏博弈中，每个状态下先手还是后手胜利是确定的（如果双方足够聪明）

称**先手必胜**的状态为 P 状态，称**先手必负**的状态为 N 状态，称一个状态的结果（***outcome classes***）为 P 或 N

显然有：

1. P状态 **至少能转移到**一个 N 状态
2. N状态 **只能转移到** P 状态

通过以上结论，显然可以通过**递推**得知一个状态的结果

### 游戏

集合表示： $G = \{g_i\}$ 表示当前游戏可以转移到的游戏

$G\in P$ 表示 $G$ 先手必胜， $G\in N$ 表示 $G$ 先手必败

### 标准游戏

定义 $\ast 0 = \varnothing$ ，是一个无法移动的游戏

$\forall a\in \mathbb{N}^+$ 定义 $\ast a = \{\ast b \mid b\in \mathbb{N} ,b < a\}$ ，例如 $\ast 1 = \{\ast 0\} = \{\varnothing\},\ \ast2 = \{\ast 0, \ast 1\} = \{\{\varnothing\}, \varnothing\} \dots$ 

显然 $\ast 0 \in N,\ \ \forall a\in \mathbb{N}^+,\ \ast a \in P$  

## 不能移动者负（normal play）

### 游戏加法

表示每次移动选择两个游戏之一进行移动，形式化地：

$G_1+G_2 = \{g_1+G_2 \mid g_1 \in G_1\} \cup \{G_1+g_2 \mid g_2 \in G_2\}$

发现游戏加法有以下性质：

$G+G\in N$

$G_1 \in N \wedge G_2 \in N \Longrightarrow (G_1+G_2) \in N$

$(G_1+G_2) \in N \wedge G_1 \in N \Longrightarrow G_2 \in N$

交换律，结合律显然

### （加法）等价

定义 $G \sim \ast a \iff SG(G) = a\iff (G+\ast a) \in N$

SG值不超过一个：

$$
\begin{aligned}
&(G+\ast a)\in N \wedge (G+\ast b) \in N \\
\Longrightarrow& (G+G+\ast a+\ast b)\in N \\
\Longrightarrow& (\ast a+\ast b)\in N \\
\Longrightarrow & a=b
\end{aligned}
$$

（可通过制定策略证明）



### 一般游戏的转移

归纳证明：$SG(G) = \text{mex}\big(\{SG(g_i)\}\big)$

设 $G = \{g_i\}$ ，$\forall g_i \in G,\ \exists! a_i,\ SG(g_i) = a_i$

$\forall a\in \mathbb{N}$ ， $G+\ast a = \{G+\ast a'\mid a'\in \mathbb{N}, a'<a\} \cup \{g_i + \ast a \mid g_i \in G\}$

1.  $a < \text{mex}\big(\{SG(g_i)\}\big)$ ， $\exists g_i,\ SG(g_i) = a\ \Longrightarrow (g_i+\ast a) \in N \Longrightarrow (G+\ast a) \in P$

2.  $a = \text{mex}\big(\{SG(g_i)\}\big)$ ，因为 $(G+\ast a')\in P$ （在1.中证明） ，$(g_i+\ast a) \in P$ （SG值不超过一个），所以 $(G+\ast a) \in N$ 

因此，每个游戏有唯一 SG 值

### 标准游戏的加法

归纳证明：$(\ast a+\ast b+*c)\in N \Longrightarrow a\oplus b\oplus c=0$ :

$$
(\ast a+\ast b+*c)\in N \Longrightarrow 
\left\{
\begin{array}\\
\forall a'<a,\ a'\oplus b\oplus c \not= 0\\
\forall b'<b,\ a\oplus b'\oplus c \not= 0\\
\forall c'<c,\ a\oplus b\oplus c' \not= 0
\end{array}\right.

\Longrightarrow 

\left\{\begin{array}\\
a\le b\oplus c\\
b\le a\oplus c\\
c\le a\oplus b
\end{array}\right.
$$
从高到低考虑每一个二进制位，每位恰有偶数个1，三个不等式两边的值一直相等，得证

### 一般游戏的加法

$$
\begin{aligned}
&(G_1+\ast a_1)\in N \wedge (G_2+\ast a_2)\in N \wedge (\ast a_1+\ast a_2+*(a_1\oplus a_2)) \in N\\
\Longrightarrow& ((G_1+G_2)+*(a_1 \oplus a_2)) \in N\\
\Longrightarrow& SG(G_1+G_2) = SG(G_1) \oplus SG(G_2)
\end{aligned}
$$

## 不能移动者胜（SJ定理）

在DAG意义上考虑：$\overline G$ 表示新增一个点，将原DAG中的所有终点连向该点，这种游戏的性质不如 normal play



### anti-nim

$\overline{\ast a_1+\ast a_2+\dots+\ast a_n}\in P \iff \begin{cases}\oplus_{i=1}^n a_i=0 & \max(\{a_i\})\le 1\\ \oplus_{i=1}^n a_i\not=0 & \max(\{a_i\})>1\end{cases}$

1. $\max(\{a_i\})\le 1$ 时显然
2. $\{a_i\} = \{\underbrace{1,1,\dots,1}_{n个},x\} \ (x>1)$ ，能转移到 $\{\underbrace{1,1,\dots,1}_{n个}\}$ 和 $\{\underbrace{1,1,\dots,1}_{n+1个}\}$ ， 一定先手必胜，有 $\overline{\sum \ast a} \in P \iff \sum \ast a \in P$
3. $\{a_i\}$ 中至少两个元素大于1，只能转移到 2. 状态和 3. 状态。 由于 $\overline{\sum \ast a}$ 中该点的转移和 $\sum \ast a$ 中该点的转移相同，归纳证明 $\overline{\sum \ast a} \in P \iff \sum \ast a \in P$ 同样满足



**但是，将任意游戏映射到SG后再转为不能移动者胜会出现问题**：

$SG(\{\ast 1\}) = 0, \overline{\{\ast 1\}} \in P$

$SG(\{\ast 2\}) = 0, \overline{\{\ast 2\}} \in N$



### anti-SG

如果 $\{g_i\}$ 满足：” $(\forall g_i,\ SG(g_i) = 0) \wedge (\sum g_i \not= \ast 0) \longrightarrow \exists g_i$，$g_i$ 能转移到 $SG=1$ 的状态 “  

那么有：
$$
\overline{\ast g_1+\ast g_2+\dots+\ast g_n}\in P \iff \begin{cases}\oplus_{i=1}^n SG(g_i)=0 & \max(\{SG(g_i)\})\le 1\\ \oplus_{i=1}^n SG(g_i)\not=0 & \max(\{SG(g_i)\})>1\end{cases}
$$




## n阶Nim和

状态为 $(\ast a_1,\ast a_2,\dots,\ast a_m)_n$ ，表示每次可以选择至少一个，至多 $n$ 个子游戏进行移动，不能移动者输

$(\ast a_1,\ast a_2,\dots,\ast a_m)_n \in N \iff $ 对于每一个二进制位，$\{a_i\}$ 中该位为1的数的个数都是 $n+1$ 的倍数



但对于任意游戏，上述结论并不适用：

$G = (\ast 1, \ast 1, \ast 1, \{\ast 1\})_2$ ，$\{SG(g_i)\} = \{1,1,1,0\}$，但存在先手必胜策略：

先手从 $(\ast 1, \ast 1, \ast 1, \{\ast 1\})_2$ 移动到 $(\ast 1, \ast 1, \ast 1)_2$，无论后手移动到 $(\ast 1, \ast 1)_2$ 还是 $(\ast 1)_2$ ，都是必败态



## 游戏乘法（nim积）

### 标准游戏积

$\mathbb{N} \times \mathbb{N}$ 上有一个无穷表格 $A$，$A_{x,y} = \begin{cases}1 & x=n,y=m\\0 & \text{otherwise}\end{cases}$

每次可以选择 $0\le a< x,\ 0\le b< y$ ，$A_{x,y}=1$ ，翻转 $A_{a,b}, A_{a,y}, A_{x,b}, A_{x,y}$ ，不能移动者输



定义 $SG(A_{x,y}) = x \otimes y$，则 $x\otimes y = \text{mex}(\{(a\otimes b)\oplus(a\otimes y)\oplus(x\otimes b)\mid a<x,b<y\})$

可证明 $<[0,2^{2^n}-1], \oplus, \otimes>$ 构成有限域 $GF(2^{2^n})$ （乘法结合律、分配律、乘法逆元存在较难证明）



### 一般游戏积

The Tartan Theorem: $SG(G_1×G_2) = SG(G_1) \oplus SG(G_2)$

$G_1 \times G_2$ 不明



### 快速计算nim积

$O(\log x\log y)$ 计算 $x\otimes y$ 的代码：

```c++
#define Resolve(i, x) for (int u = (x), i = 0; (1ll << i) <= u; ++ i) if (u >> i & 1)

ll f(ll x, ll y);

ll g(int x, int y) {
	if (!x || !y) return 1ll << (x | y);
	if (~tab[x][y]) return tab[x][y];
	ll res = 1;
	Resolve(i, x ^ y) res <<= (1 << i);
	Resolve(i, x & y) res = f(res, 3ll << ((1 << i) - 1));
	return tab[x][y] = res;
}

ll f(ll x, ll y) {
	if (!x || !y) return x | y;
	if (x == 1 || y == 1) return max(x, y);
	ll res = 0;
	Resolve(i, x) Resolve(j, y) res ^= g(i, j);
	return res;
}
/*
f(x,y) = x \oplus y
g(x,y) = 2^x \oplus 2^y
init : forall x,y <= log, tab[x][y] = -1
*/
```



## 链接

[WC2009 从“k倍动态减法游戏”出发探究一类组合游戏问题](http://www.doc88.com/p-5098170314707.html)

2009集训队论文 组合游戏略述——浅谈SG游戏的若干拓展及变形

[Nim积解法小结 - zjp_shadow - 博客园 (cnblogs.com)](https://www.cnblogs.com/zjp-shadow/p/10507030.html)

[On nim multiplication and some related games · wcysai](https://wcysai.github.io/2019/09/17/On-nim-multiplication-and-related-games/)
