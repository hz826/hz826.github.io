---
title: 'SAM 结构及证明'
date: 2020-08-19 15:44:56
tags: []
published: true
hideInList: false
feature: 
isTop: true
mathjax: true
---
<center>2012年noi冬令营陈立杰SAM讲稿阅读笔记</center>

![](Suffix-Automaton/SAM_abbab.png)

<center><font color=grey size=2>SAM("abbab")</center>

<!--more-->

## 本文的一些定义

### 确定有限自动机 (DFA) 

以下内容摘自wiki，有省略

DFA 可用一个五元组 $\langle Q,\Sigma,\delta,q_0,F \rangle$ 表示：

>$Q$ ：状态集合
>
>$\Sigma$ : 符号的有限集合，自动机接受的“字母表”
>
>$\delta$ : **转移**函数，在某一状态下，接受字母，转移到唯一新状态 （$\delta : (Q,\Sigma) \rightarrow Q$）（下文记作 $\text{nxt}(q,x)$）
>
>$q_0$ : 开始状态（$q_0 \in Q$）
>
>$F$ : 终止状态集合（$F \subset Q$，对于可识别字符串，自动机一定停止于 $F$ 中的某个状态）

<img src="Suffix-Automaton/wiki_DFA.png" style="zoom:50%;" />

<center><font color=grey size=2>自动机可用有向图表示，其中每条边上都写着一个字符表示接受的符号，每个状态对应图中一个节点，F集中的状态用双圆圈表示</center>

### 字符串

$s = s_0s_1 \dots s_{n-1}$ ，$|s|$ 表示字符串长度

$\text{substring}(s)$ 表示 $s$ 的所有子串，每个非空子串可以用左闭右开区间 $s\small{\left[ l,r \right)},\ (0\le l<r\le n)$ 表示

$\text{perfix}(s)$ 表示 $s$ 的所有前缀 $s\small{\left[ 0,r \right)}$， $\text{suffix}(s)$ 表示 $s$ 的所有后缀 $s\small{\left[ l,n \right)}$



$\text{nxt}(q,x)$ 表示状态 $q$ 接受字符 $x$ 后转移到的节点（可能为 $\text{null}$，$\text{null}$ 永远转移到 $\text{null}$）

$\text{trans}(q,s)$ 表示状态 $q$ 接受字符串 $s$ 后转移到的节点，即 $\text{trans}(q,s) = \text{nxt}(\text{trans}(q,s\small{\left[0,|s|-1\right)}\ ), s_{|s|-1})$（可能为 $\text{null}$）



定义状态 $q$ 可以**识别**的字符串为 $L(q) = \{s \mid \text{trans}(q, s) \in F\}$ 

### 最小 DFA

对于最小DFA，有以下结论：

1. 最小DFA唯一

2. 一个DFA为最小DFA当且仅当该DFA中不存在：

   2.1 **不可达状态**（指对DFA输入任意字符串，都无法到达的状态）

   2.2 **等价状态**（指可识别字符串集合 $L$ 相同的状态）



证明：

因为不存在等价状态，所以可以通过有限集 $L$ 唯一确定对应的 $q$，通过有限集 $L(q_0)$ 能唯一确定一个最简 DFA，可以符号化地构造：

状态：$\forall L_0,\ (\exists q,\ L(q) = L_0) \iff (\exists t, L_0 = \{s\mid s\in L(q_0),\ t\in \text{perfix}(s)\})$

转移：$\text{nxt}(p,x)=q \iff L(q) = \{s\mid s\in L(p),\ s_0=x\}$



### 后缀自动机 (SAM)

定义：对于字符串 $S$，SAM 是 **恰能识别** $S$ **所有后缀**的**最小DFA**

下面讨论字符串 $S$ 构建的 SAM，其中 $S$ 长度为 $n$ 



**由最小 DFA 性质，SAM 唯一。利用字符串后缀的特殊性质，可以 $O(n)$ 构造出SAM，并且 SAM 满足以下一些性质：**

## 后缀与子串

根据 SAM 定义，$\text{trans}(q_0,s) \in F \iff s \in \text{suffix}(S)$ 

此外，由于最小 DFA 中不存在不能转移到 $F$ 集的状态，若 $\text{trans}(q_0,s) \not = \text{null}$，说明 $s$ 是某个<u>后缀的前缀</u>，也就是说：$\text{trans}(q_0,s) \not = \text{null} \iff s \in \text{substring}(S)$

## right集合、len区间，与parent树

### right集合

考虑状态 $q$ 能识别哪些字符串：若 $q$ 能转移到 $F$ 集，则存在 从 $q_0$ 出发，经过 $q$ 的转移路径 到 $F$ 集，因此 $q$ 能识别的字符串都是 <u>后缀的后缀</u>，$q$ **只能识别后缀**

**定义：$\text{right}(q)$ 是 $q$ 能识别的后缀的左端点集合**，假设 $q$ 能识别 $S\left[r_1,n\right),S\left[r_2,n\right)......S\left[r_m,n\right)$，则$\text{right}(q) = \{ r_1,r_2,\dots,r_m \}$



若 $\text{trans}( q_0,S\left[l,r\right) ) = q$，因为 $\text{trans}( q_0,S\left[l,n\right) ) \in F$，所以 $\text{trans}( q,S\left[r,n\right) ) \in F$

也就是说：$\text{trans}( q_0,S\left[l,r\right) )=q \Longrightarrow r \in \text{right}(q)$（可以发现：$q \in F   \Longleftrightarrow n\in \text{right}(q)$ ）

另外，由最小 DFA 性质，不可能存在两个状态的 $\text{right}$ 集合相等

### len区间

上文中已得出 $\text{trans}( q_0,S\left[l,r\right) )=q \Longrightarrow r \in \text{right}(q)$，现在考虑对 $l$ 的要求：

设 $l_1 < l_2$ ，则 $S\left[l_1,r\right)$ 包含 $S\left[l_2,r\right)$ ，若 $S\left[l_1,r\right)$ 出现在字符串某位置，$S\left[l_2,r\right)$ 一定也出现

![](Suffix-Automaton/seg_01.png)

因此：$ \text{right}( \text{trans}( q_0,S\left[l_1,r\right) ) ) \subseteq \text{right}( \text{trans}( q_0,S\left[l_2,r\right) ) )$

注意到：$\text{right}$ 集合相同则状态相同，所以，对于确定的 $r,q$，$\text{trans}( q_0,S\left[l,r\right) ) = q \iff \text{right}(\text{trans}( q_0,S\left[l,r\right))) = \text{right}(q)$ 

结合 $\text{right}$ 的包含性质可得出，满足 $\text{trans}( q_0,S\left[l,r\right) ) = q$ 的 $l$ 一定在某个区间内，

定义 $l \in \text{len}(q) = \left[\min(q),\max(q)\right]$ 



$\text{trans}( q_0,S\left[l,r\right) )=q \Longleftrightarrow r \in \text{right}(q) \land r-l \in \left[\min(q),\max(q)\right]$

$L(q)$ 包含长度从 $\min(q)$ 到 $\max(q)$ 的字符串各一个

定义 $L_m(q)$ 表示 $L(q)$ 中最长的字符串（长度为 $\max(q)$）

那么 $L(q) = \{s \mid s \in \text{suffix}(L_m(q) )\land |s| \in \left[\min(q),\max(q)\right]\}$ 



**$s$ 在 $S$ 中的出现次数等于 $| \text{right}( \text{trans}(q_0,s) ) |$**



综上，SAM 中状态的内容可分为两部分
$$
q_0 \xrightarrow{\quad[min(q),max(q)]\quad} q \xrightarrow{\quad \text{right}(q)\quad } F
$$

一个没什么用但有助于理解的结论：$\sum_{q\not = q_0} [\max(q)-\min(q)+1] \times | \text{right}(q) | = \frac{n(n-1)}{2}$

### parent树

考虑两个状态 $q_1, q_2$ 的 $\text{right}$ 集合的交：

若 $\text{right}(q_1), \text{right}(q_2)$ 有交，设 $r \in \text{right}(q_1) \cap \text{right}(q_2)$，

则 $\forall x_1\in \text{len}(q_1),\ S\left[r-x_1,r\right) \in L(q_1)$ ，$\forall x_2\in \text{len}(q_2),\ S\left[r-x_2,r\right) \in L(q_2)$

![](Suffix-Automaton/seg_01.png)

有和上文相同的包含关系，又因为 $q_1,q_2$ 的 $\text{right}$ 集不等，可推出 $\text{right}(q_1) \subset \text{right}(q_2)$ 或 $\text{right}(q_2) \subset \text{right}(q_1)$

因此，**所有状态的 $\text{right}$ 集合由形成一颗有根树（parent树）**，父集合包含子集合中的全部元素和一些其他元素

<img src="Suffix-Automaton/beamer_01.png" style="zoom:67%;" />

定义状态 $q$ 在 **parent 树中的父节点为 $\text{pre}(q)$**，则 $\text{right}(q) \subset \text{right}(\text{pre}(q))$

显然，对于任一 $\text{right}$ 集合中元素 $r$，$r$ 只出现在由根到某一结点 $q$ 的路径中，

也就是说 ：$\text{trans}(s+t)=p, \text{trans}(t)=q \Longrightarrow \exists t\ge 0, \text{pre}^t(p) = q$ 



深度减小，$\text{right}$ 集大小增大，$\text{len}$ 区间减小，由区间的连续性，$\max(\text{pre}(q)) + 1 = \min(q)$

![](Suffix-Automaton/seg_02.png)
<center> <font color=grey size=2>在下文中，用所有最长的满足 \text{trans}(q_0,str) = q 的 字符串str表示状态q</font> </center>

### right底层节点

$r \in \text{right}(q) \iff \exists l,\ \text{trans}(q_0, S\left[l,r\right))=q$​ ，因为深度减小，$\text{len}$​ 区间减小，所以满足 $r \in \text{right}(q)$​ 的最深的 $q$​ 一定满足 $q = \text{trans}(q_0, S\left[0,r\right))$​

**在计算 $\text{right}$ 时有重要作用**

### 失配指针

设 $\text{trans}(q_0, S\left[l,r\right)) = q$，考虑 $S\left[l,r\right)$ 的最长后缀 $S\left[l',r\right)$ 满足 $\text{trans}( q_0,S\left[l',r\right) ) \not = q$，

（易证 $\text{trans}( q_0,S\left[l',r\right) ) = \text{pre}(q)$ ），因此 $\text{pre}$ 在 SAM 中也是该状态的失配指针（与AC自动机中的 fail 相同）

## 线性证明

由于 parent 树的划分性质，最大状态数 $f(n) = \max_{\sum a_i \le n} \{ \sum f(a_i) + 1\}, f(1) = 1$，解得 $f(n)=2n-1$



关于SAM中有效转移（状态到非 $\text{null}$ 状态） 的边数，有以下证明：

>  将自动机的转移看作一个DAG，对 DAG 求出任意一颗以 q_0 为根的生成树，下证明非树边数量不大于后缀数量：
>
> 构造映射（满射） f : 所有非树边 $\rightarrow$ 部分后缀，返回 先走树边，再走非树边，然后到达F集的路径所对于的后缀（由于该非树边为第一条非树边，所以不会重复）

## 构造方法

设原字符串为 $S$，长度为 $n$，现在添加字符 $x$，设新的 $F$ 集为 $F'$

新建 $np = \text{trans}(q_0,S+x)$，$np$ 没有后继，只能识别 $S+x$ ，即 $\text{right}(np) = \{n+1\}$

由 parent 树性质，原 $F$ 集中所有状态可表示为 $\text{pre}^t(\text{trans}(q_0, S\left[0,n\right)\ ))$ ，在 parent 树的一条链上

对于原 $F$ 集的**所有节点 $p$** ，都要保证 $\text{trans}(p,x)$ $\in F'$ ，同时也要保证不能误识别非后缀字符串

下面分3种情况讨论：

### case 1

$\text{nxt}(p,x) = \text{null}$，将 $\text{nxt}(p,x)$ 直接修改为 $np$ 即可

注意到：$\text{nxt}(q,x) \not = \text{null} \iff \exists r \in \text{right}(q) ,\ S_{r} = x$

而 $\text{right}$ 集合随 parent 树深度减小而扩大，因此可以将从底层节点到根的路径分为上下两部分：

下部的所有状态 p 满足 $\text{nxt}(p,x) = \text{null}$，可直接处理

而上部 $\text{nxt}(p,x) \not = \text{null}$，继续讨论 

![](Suffix-Automaton/seg_03.png)
<center> <font color=grey size=2>图中，p属于下部，而 q=pre(p) 属于上部</font> </center>

### case 2

设上部所有节点集合为 $P$，设 $Q' = \{\text{nxt}(p_i,x) \mid p_i \in P\}$，$P$ 中最深节点为 $p$，$\text{nxt}(p,x) = q$ （由于 parent 树的后缀性质，显然 $Q'$ 中所有不同的元素也在一条链上，且 $q$ 为其中最深的节点）

考虑直接将所有 $Q'$ 集元素和 $np$ 设为 $F'$ 的可能性：

对于任意一个新后缀，可表示为 $suf + x$，其中 $suf$ 为原后缀。若 $suf$ 满足 $\text{trans}(q_0,suf) \in P$（原 F），一定满足 $\text{trans}(q_0,suf+x) \in F'$

现在考虑**是否存在不是新后缀的 str**，满足 $\text{trans}(q_0,str) \in Q'$ ：

![](Suffix-Automaton/seg_04.png)
<center> <font color=grey size=2>如果 max(p)+1 = max(q)， 可以直接设新F集</font> </center>

1. 由 $\max( \text{nxt}(\text{pre}(p),x) ) \le \max( \text{nxt}(p,x) )$ （当且仅当 $\text{nxt}(\text{pre}(p),x) = \text{nxt}(p,x)$ 时取等），可得： $\text{trans}(q_0,str) \in Q' \Longrightarrow |str| \le \max(q)$
2. 若 $|str| \le \max(p)+1$ ，一定存在原后缀 $suf$ 满足 $|suf|=|str|-1$，$\text{trans}(q_0,suf) \in P，\text{trans}(q_0,suf+x) \in Q'$，由于 $str$ 与 $suf+x$ 等长，可证明 $str = suf+x$，$str$ 一定为新后缀

因此不用考虑其他情况，一定不会误识别

此外，还要将 np 的父节点设为 q 

### case 3

由 max 定义，显然有 $\max(p) + 1 \le \max(q)$，上一节已经讨论了 $max(p) + 1 = max(q)$ 的情况

而如果 $\max(p) + 1 < \max(q)$ ，在直接将 $q$ 加入 新 $F$ 集时，**一定会出现不是新后缀的 $str$，满足$\text{trans}(q_0,str) = q$**

![](Suffix-Automaton/seg_05.png)

<center> <font color=grey size=2>注意：图中黄色字符一定不等于绿色字符 y
</font> </center>

反证：若黄色字符也是 y，考虑 “原后缀” suf' = y + S[n-max(p),n) （字符 y 加上蓝色部分），

suf' 满足 \text{trans}( q_0, suf' ) 属于原 F 集，又有 |suf'| > max(p) ，\text{trans}(q_0, suf') 属于下部分，

所以 \text{nxt}( \text{trans}( suf' ) , x) 应该为 \text{null}，但字符串 suf' + x 一定出现过（q存在），矛盾。

---

为避免误识别，尝试设置一新状态 nq，max(nq) = max(p)+1

![](Suffix-Automaton/seg_06.png)

显然有 max(nq) < max(q)，而由于 \text{nxt}(p,x) = q，有

$$
min(q) \le max(p)+1\\
$$
$$
max(pre(q))+1 \le max(p)+1 = max(nq) \\
$$
$$
max(pre(q)) < max(nq)
$$

对于 parent树：在 q 和 \text{pre}(q) 之间插入 nq ，并将 np 的父节点设为 nq 即可

$$
pre(q) \xleftarrow{} nq \xleftarrow{} q
$$

对于 \text{nxt}函数：

1. 考虑哪些节点应该转移到 nq：因为 \text{nxt}(p,x) = nq，所以若 \text{nxt}(p',x) = nq，p' 是 p 一定范围内的祖先（直到 \text{nxt}(p',x) = \text{pre}(q) ）（parent树的后缀性质）
2. 考虑 nq 应该转移到哪些节点：\text{nxt}(nq) 由 \text{right}(nq) 决定，又因为 \text{right}(nq) = \text{right}(q) $\cup$ {n+1}，所以 \text{nxt}(nq) = \text{nxt}(q)

### 构造复杂度

构造 S[0,n) 的 SAM 时，新增 O(n) 边

不会删除边

对于边的修改：可以证明**被修改过的边不会再被修改**

证明如下：

只需考虑 parent 树上的两条链（称为p链和q链），其中每个p链上部点都有一条边连向q链上部点（对于每一个q链上的点，有**一到多个**p链上的点连向它）

<img src="Suffix-Automaton/graph_01.png" style="zoom:38%;" />

<center><font size=2 color="grey"> 左侧为p链，右侧为q链</center>

若一条边 p->q 满足 max(p)+1 = max(q)，在接下来的操作中，p->q 边上方的边均不会被修改（只考虑两条链的话，边之间显然不会交叉）

### 证明新SAM是最小DFA

$\text{right}$ 集合不重复，而且新 SAM 恰好只可以所有后缀，新 SAM 一定是最小 DFA

## SAM建后缀树

$L_m(\text{pre}(p)) \in \text{suffix}(L_m(p))$，反转后，$\text{pre}(p)$ 对应的最长字符串是 $p$ 对应的最长字符串的前缀

定义 $a^R = \{x \mid |a|+1-x \in a\}$

那么，反SAM中，节点p对应起点在 $\text{right}(p)^R, \text{len}(p.\text{pre}) < \text{len}\le \text{len}(p)$​ 的子串，他们有相同的前缀

在父节点中的排名权值为 $S_{r+\text{len}(p.pre)}$

## 广义SAM

T : trie
F(T) : T 中的子串 s = Tx...Ty，where Ty \in subtree( Tx )
S(T) : T 中的后缀
\text{right}(s) : Ty, where s=Tx...Ty 
