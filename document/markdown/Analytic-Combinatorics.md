---
title: '解析组合学习笔记'
date: 2021-08-01 00:00:00
tags: []
published: true
hideInList: false
feature: 
isTop: true
mathjax: true
description: 简单介绍了有标号计数、无标号计数及组合类的基本构造
---

<!--more-->

# 解析组合学习笔记

## 无标号计数（OGF）

#### 无标号组合类 $\mathcal{A}$ 

$$
\begin{aligned}
&\mathcal{R} = \{\langle a,b\rangle \mid a,b\in \mathcal{R}\}\cup \ \mathcal{R}_0\\
\\
&|a| : \mathcal{R} \to \mathbb{N}\\
&|a| = \begin{cases} \text{size}(a) & a\in \mathcal{R}_0 \\ |b|+|c| & a = \langle b,c\rangle\end{cases}\\
\\
&b\times c = \langle b,c\rangle
\end{aligned}
$$

$\mathcal{R_0}$ , $\text{size}$ 给定，$\mathcal{R_0}$ 中元素不可表示为二元组



一个集合，集合中每个元素 $a \in \mathcal{A}$ ，由一系列的基础元素和二元组构成，有一个可加的表示大小的函数 $|a|$

也可以看作是一种类型，每个元素 $a \in \mathcal{A}$ 的类型都是 $\mathcal{A}$

生成函数 $ A(z) = \sum_{i\ge0} A_n z^n$

#### 不交并（和）

$\mathcal{A} = \mathcal{B}+\mathcal{C} =\{\langle b,\square\rangle\mid b\in\mathcal{B}\}\cup\{\langle c,\triangle\rangle  \mid c\in\mathcal{C}\}$

其中 $|\square| = |\triangle| = 0$

#### 笛卡尔积

$\mathcal{A} = \mathcal{B}\times\mathcal{C} =\sum_{b\in\mathcal{B}, c\in\mathcal{C} } b\times c$

生成函数 $A = B * C$

#### SEQ 构造

$\text{SEQ}(\mathcal{A}) = \{\langle\langle\langle\langle\varepsilon,a_1\rangle,a_2\rangle,a_3\rangle,...a_n\rangle \mid n\in \mathbb{N}, a_i\in\mathcal{A} \}$

$\text{SEQ}(\mathcal{A}) = \text{SEQ}\mathcal(A)\times \mathcal{A} + \varepsilon$

生成函数 $\text{SEQ}(A) = 1 + A*\text{SEQ}(A) = \frac{1}{1-A}$

#### CYC 构造

$\text{CYC}(\mathcal{A}) = (\text{SEQ}(\mathcal{A}) - \varepsilon) / S$

其中 $S$ 是循环群，$|X/G|$ 表示等价类（轨道）数量

由 burnside 引理， $|X/G| = \frac{1}{|G|} \sum_{g\in G} |X^g|$
$$
\begin{aligned}
\text{CYC}(\mathcal{A}) &= \sum_{k>0} \frac{1}{k}\sum_{i=1}^{k} A(x^{k/gcd(k,i)})^{\gcd(k,i)}\\
&= \sum_{k>0} \frac{1}{k}\sum_{d=gcd(k,i)|k} \varphi(k/d) A(x^{k/d})^{d}\\
&= \sum_{k>0} \frac{1}{k}\sum_{d|k} \varphi(d) A(x^{d})^{k/d}\\
&= \sum_{d>0} \sum_{i=d/k>0} \frac{\varphi(d)}{d} \frac{1}{i} A(x^{d})^i\\
&= \sum_{d>0} \frac{\varphi(d)}{d} \sum_{i>0} \frac{1}{i} A(x^{d})^i = \sum_{d>0} \frac{\varphi(d)}{d} \ln	\frac{1}{1-A(x^d)}\\
\end{aligned}
$$
只需计算 $\ln\frac{1}{1-A(x)}$ ，复杂度 $O(n\log n)$

#### MSET 构造

$\text{MSET}(\mathcal{A}) = \text{SEQ}(\mathcal{A}) / R$

其中 $R$ 是对称群（全置换群）

根据组合意义，有
$$
\begin{aligned}
\text{MSET}(\mathcal{A}) &= \prod_{a\in \mathcal{A}} \frac{1}{1-x^{|a|}}= \prod_{i\ge0} (1-x^i)^{-a_i}\\
&= \exp(\sum_{i\ge0} -a_i \ln(1-x^i))\\
&= \exp(\sum_{i\ge0} a_i \sum_{j\ge1} \frac{x^{ij}}{j}) = \exp(\sum_{j\ge1} \frac{A(x^j)}{j})
\end{aligned}
$$

#### PSET 构造

$\text{PSET}(\mathcal{A}) = \sum_{\mathcal{B}\subset \mathcal{A}} \mathcal{B}$

根据组合意义，有
$$
\begin{aligned}
\text{PSET}(\mathcal{A}) &= \prod_{a\in \mathcal{A}} (1+x^{|a|})= \prod_{i\ge0} (1+x^i)^{a_i}\\
&= \exp(\sum_{i\ge0} a_i \ln(1+x^i))\\
&= \exp(\sum_{i\ge0} a_i \sum_{j\ge1} \frac{(-1)^{j-1}x^{ij}}{j}) = \sum_{j\ge1} \frac{(-1)^{j-1}A(x^j)}{j}
\end{aligned}
$$

### 举例

无标号有根树计数

$\mathcal{T} = z * \text{MSET}(\mathcal{T})$

## 有标号计数（EGF）

#### 有标号组合类 $\mathcal{A}$

$$
\begin{aligned}
&\mathcal{R}_0 = \{\langle a,p_a\rangle \dots \mid p_a \in \text{permutation}_{\text{size}(a)}\}\\
&\mathcal{R} = \mathcal{R}_0 + \sum_{\langle a,p_a\rangle,\langle b,p_b\rangle \in \mathcal{R}} \langle a,p_a\rangle \star \langle b,p_b\rangle\\
\\
&|a|: \mathcal{R} \to \mathbb{N}\\
&|a| = \begin{cases} \text{size}(a) & \exists \langle a,p_a\rangle\in \mathcal{R}_0 \\ |b|+|c| & a = \langle b,c\rangle\end{cases}\\
\\
&\langle a,p_a\rangle \star \langle b,p_b\rangle = \{\langle c, p_c\rangle \mid c=\langle a,b\rangle, p \in e(b,c)\}
\end{aligned}
$$

$e(b,c)$ 表示对 $b, c$ 重标号，即 $e(b,c) = \{p \mid p \in \text{permutation}_{p||+|c|}, \text{rank}(p[:|b|]) = b \wedge \text{rank}(p[|c|:]) = c\}$



$\forall a\in \mathcal{A}$ ,   由一系列的基础元素和二元组构成，每个基础元素 $b$, 对应着一个长度为 $|b|$ 的数列，将所有 $b_i$ 按顺序排列后，是一个长度为 $|a|$ 的排列

指数生成函数 $ A(z) = \sum_{i\ge0} A_n \frac{z^n}{n!}$

#### SEQ 构造

$\text{SEQ}(\mathcal{A}) = \text{SEQ}\mathcal(A)\times \mathcal{A} + \varepsilon$

生成函数 $\text{SEQ}(A) = 1 + A*\text{SEQ}(A) = \frac{1}{1-A}$

#### SET 构造

$\text{SET}(\mathcal{A}) = \text{SEQ}(\mathcal{A}) / R$

其中 $R$ 是对以 $\mathcal{A}$ 为基本元素的序列形成的 对称群（全置换群）

由于有标号的关系，$\forall b \in \text{SEQ}(\mathcal{A})$ , $b$ 中元素两两不等，因此

生成函数 $\text{SET}(A) = 1 + \frac{A}{1!} + \frac{A^2}{2!} + \frac{A^3}{3!} + \dots = \exp(A)$

（同样的，在子集卷积中，元素一定两两不同，所以也可以用exp）

#### CYC 构造

$\text{CYC}(\mathcal{A}) = (\text{SEQ}(\mathcal{A}) - \varepsilon) / S$

其中 $S$ 是循环群

同理，生成函数 $\text{CYC}(A) = \frac{A}{1} + \frac{A^2}{2} + \frac{A^3}{3} + \dots = \ln\frac{1}{1-A}$

#### Pointing 构造

$\Theta(\mathcal{A}) = \sum_{\langle a,p_a\rangle\in \mathcal{A}}\sum_{i=1}^{|a|} \langle a,p_a\rangle \star  \ \square_i$

生成函数 $\Theta(A) = z \frac{\mathrm{d}}{\mathrm{d}z} A(z)$

#### boxed product

$\mathcal{A}^{\square} \star \mathcal{B} = \{ \langle c,p_c\rangle \mid \langle c,p_c\rangle \in \mathcal{A}\star \mathcal{B}, 1\in p_c[:|a|]\}$

生成函数 $A^{\square} \star B = \frac{\mathrm{d}}{\mathrm{d}z} A(z) * B$
$$
\begin{aligned}
A(z) &= a_0 + \frac{a_1}{1!} z^1 + \frac{a_2}{2!} z^2 + \frac{a_3}{3!} z^3 + \dots\\
\frac{\mathrm{d}}{\mathrm{d}z} A(z) &= a_1 + \frac{a_2}{1!} z^1 + \frac{a_3}{2!} z^2 + \frac{a_4}{3!} z^3 + \dots\\
zA(z) &= \frac{1}{1!} a_0z + \frac{2a_1}{2!} z^2 + \frac{3a_2}{3!} z^3 + \frac{4a_3}{4!} z^4 + \dots\\
\end{aligned}
$$

##### 举例

$$
\begin{aligned}
A^{\square} \star B &= \int (\frac{\mathrm{d}}{\mathrm{d}z} A \times B)\\
\\
A^{\square} \star B + A \star B^{\square} &= \int (\frac{\mathrm{d}}{\mathrm{d}z}A \times B) + \int (\frac{\mathrm{d}}{\mathrm{d}z}B \times A)\\
&= \int \frac{\mathrm{d}}{\mathrm{d}z} AB\\
\\
\exp(A) \star A^{\square} &= \int (\frac{\mathrm{d}}{\mathrm{d}z} A\times \exp(A))\\
&= \int \frac{\mathrm{d}}{\mathrm{d}z} \exp(A)\\
&= \exp(A) - 1
\end{aligned}
$$

