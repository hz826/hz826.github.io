---
title: '大学物理学习笔记'
date: 2022-01-29 12:30:00
tags: []
mathjax: true
description: 大学文化课
---

## 质点运动学

$$
a = \frac{\mathrm{d}v}{\mathrm{d}t} = v \frac{\mathrm{d}v}{\mathrm{d}x}
$$

### 圆周运动分解

t : 切向， n : 法向
$$
\vec a = \vec a_t + \vec a_n\\
a_t = \frac{\mathrm{d}|\vec v|}{\mathrm{d}t} \cdot \vec e_t\\
a_n = \frac{\vec v^2}{R} \cdot \vec e_n
$$

### 科里奥利力

物体在现实空间中直线运动，对于位于匀速圆盘上的观测者而言，物体受到了科里奥利力，$\vec F_c = 2m \vec v \times \vec w$

### 直线运动和圆周运动

| 物理量            | 直线运动                                        | 圆周运动                                                     |
| ----------------- | ----------------------------------------------- | ------------------------------------------------------------ |
| 位移 / 角位移     | $\vec s$                                        | $\theta$                                                     |
| 速度 / 角速度     | $\vec v = \frac{\mathrm{d}\vec s}{\mathrm{d}t}$ | $\vec\omega = \frac{\mathrm{d} \theta}{\mathrm{d}t},\ \vec \omega \times \vec r = \vec v$ |
| 加速度 / 角加速度 | $\vec a = \frac{\mathrm{d}\vec v}{\mathrm{d}t}$ | $\vec\alpha= \frac{\mathrm{d} \vec \omega}{\mathrm{d}t},\ \vec \alpha \times \vec r = \vec a$ |
| 质量 / 转动惯量   | $m$                                             | $I = \sum \vec r^2 m$                                        |
| 力 / 力矩         | $\vec F$                                        | $\vec M = \vec r\times \vec F$                               |
| 牛顿第二定律      | $\vec F = m\vec a$                              | $\vec M = I \vec \alpha$                                     |
| 动量 / 角动量     | $\vec p = m\vec v$                              | $\vec L = \vec r \times \vec p$                              |
| 动量定理          | $\int \vec F \mathrm{d}t = \Delta \vec p$       | $\int \vec M \mathrm{d}t = \Delta \vec L$                    |
| 功                | $A = \int \vec F \mathrm{d} \vec r$             | $A = \int \vec M \mathrm{d} \theta$                          |

$\theta$ 是标量，$\mathrm{d} \theta$ 是矢量，方向垂直于转动平面，由右手螺旋确定

质心系内力做功不一定为0，动量/角动量一定为0

一般点在质心系的运动分解为质心的运动和点绕质心的旋转 $\vec v_A = \vec v_C + \vec \omega \times \vec r_{CA}$

## 简谐运动

### 基本方程

$$
\frac{\mathrm{d}^2x}{\mathrm{d}t} + \omega^2 = 0 \iff x = A \cos(\omega t + \varphi) = \text{Re}(\pmb{A} \cdot e^{\omega ti})\\
x = A \cos(\omega t + \varphi)\\
v = -A\omega \sin(\omega t + \varphi)\\
a = -A\omega^2 \cos(\omega t + \varphi)\\
$$

基本变量

| 名称   | 定义                                                    |
| ------ | ------------------------------------------------------- |
| 振幅   | $A$                                                     |
| 角频率 | $\omega$                                                |
| 周期   | $T = \frac{2\pi}{\omega}$                               |
| 频率   | $\nu = \frac{1}{T} = \frac{\omega}{2\pi}$, 有时记作 $f$ |
| 相位   | $\varphi$                                               |

### 单/复摆

$$
M = I \frac{\mathrm{d}^2 \theta}{\mathrm{d}t^2} = -mgl\sin \theta \approx -mgl\theta\\
\omega = \sqrt{\frac{mgl}{I}}
$$

单摆另外有$I=l^2m, \omega = \sqrt{\frac{g}{l}}$

### 能量

弹簧振子模型
$$
E_k = \frac 12 mv^2  + \frac 12 kx^2 = \frac 12 m (A\omega)^2 \sin^2(\omega t + \varphi) + \frac 12 kA^2 \cos^2(\omega t + \varphi) = \frac 12 kA^2
$$

### 频率简谐运动合成

1. 同频率

$$
A_1 \cos(\omega t + \varphi_1) + A_2 \cos(\omega t + \varphi_2)= \text{Re}((\pmb{A}_1+\pmb{A}_2) \cdot e^{\omega ti})
$$

2.  $|\omega_2-\omega_1|$ 较小

$$
A \cos(\omega_1 t + \varphi) + A \cos(\omega_2 t + \varphi) = 2A \cos(\frac{\omega_2-\omega_1}{2} t) \cos(\frac{\omega_2+\omega_1}{2}t+\varphi)
$$

​								拍频 $\nu = |\nu_2 - \nu_1|$

3. 同频率垂直
   $$
   x = A_1 \cos(\omega t + \varphi_1)\\
   y = A_2 \cos(\omega t + \varphi_2)\\
   \frac{x^2}{A_1^2} + \frac{y^2}{A_2^2} - 2\frac{xy}{A_1A_2} \cos(\varphi_2 - \varphi_1) = \sin^2(\varphi_2 - \varphi_1)\\
   $$

### 阻尼振动

解二阶常系数微分方程，

欠阻尼：若微分方程有两复数解，则可化为 $x = C e^{\lambda t} \cos(\omega t + \varphi)$

过阻尼：若微分方程有两实数解，$x = C_1 e^{\lambda_1t} + C_2 e^{\lambda_2t}$

临界阻尼：若微分方程有一实数解， $x = (C_1+C_2t) e^{\lambda t}$

## 机械波

### 基本方程

沿x轴正方向传播的平面简谐波的波动表达式
$$
\begin{aligned}
y_0(t) &= A \cos\big(\ \omega t + \varphi_0\ \big)\\
y(x,t) &= A \cos \big( \omega (t-\frac{x}{u}) + \varphi_0\ \big)\\ &= A \cos \big(\ \omega t - \frac{2\pi x}{\lambda} + \varphi_0\ \big)\\
v(x,t) &= \frac{\partial y(x,t)}{\partial t}
\end{aligned}
$$
 图像为：随 $t$ 增大向右移动的三角函数，右边相位超前于左边

基本变量（波速、波长、频率/周期 ： 知二推一）

| 名称 | 定义                                      |
| ---- | ----------------------------------------- |
| 波速 | $u = \frac{\lambda}{T}$                   |
| 波长 | $\lambda = uT$                            |
| 频率 | $\nu = \frac{\omega}{2\pi} = \frac{1}{T}$ |

### 能量

$\rho$ : 棒密度， $S$ : 横截面积

能量密度 $w$
$$
w = \frac{\mathrm{d}E}{\mathrm{d}V} = \rho A^2 \omega^2 \sin^2 [\ \omega(t-\frac{x}{u})\ ]\\
\overline{w} = \frac 12 \rho A^2 \omega^2
$$

能流 $P = wuS$，$\overline{P} = \overline{w}uS$

波的强度 $I = I = \frac{\overline P}{S} = \overline wu$

### 惠更斯原理

任一点可以看作新的波源

### 折射

折射角：射线与法线的夹角

折射率：sin(入射角) / sin(反射角)

### 干涉

$\Delta \varphi = (\varphi_2 - \frac{2\pi r_2}{\lambda}) - (\varphi_1 - \frac{2\pi r_1}{\lambda})$

相长干涉：$\Delta \varphi = 2k\pi, k\in \mathbb Z$

相消干涉：$\Delta \varphi = (2k-1)\pi, k\in \mathbb Z$

### 驻波

$$
A \cos[\ \omega t - \frac{2\pi x}{\lambda} + \varphi_1\ ] + A \cos[\ \omega t + \frac{2\pi x}{\lambda} + \varphi_2\ ] = 2A \cos(\frac{2\pi x}{\lambda}+\frac{\varphi_2-\varphi_2}{1}) \cos(wt+\frac{\varphi_1+\varphi_2}{2})
$$

两列频率、振幅相同，传播方向相反的波合成，会形成驻波，两个cos分别只跟$x,t$ 有关，图像表现为随时间对三角函数 $ 2A \cos(\frac{2\pi x}{\lambda}+\frac{\varphi_2-\varphi_2}{1})$ 的周期性放缩

总平均能流密度为0

### 半波损失

波疏介质：$\rho u$ 较小；波密介质：$\rho u$ 较大

入射波：$A \cos[\ \omega t - \frac{2\pi x}{\lambda} + \varphi_1\ ]$，在 $x_1$ 反射

波密 -> 波疏 -> 波密，无半波损失，反射波 $A \cos[\ \omega t - \frac{2\pi (x_1+(x_1-x))}{\lambda} + \varphi_1\ ] $

波疏 -> 波密 -> 波疏，有半波损失，反射波 $A \cos[\ \omega t - \frac{2\pi (x_1+(x_1-x))}{\lambda} + \varphi_1\ +\pi] $

### 简正模式

$L$ : 弦长

两端固定的弦：$L = n \cdot \frac{\lambda_n}{2}, n\in \mathbb N^+$

一端固定，一端自由的棒：$L = (2n-1) \cdot \frac{\lambda_n}{4}, n\in \mathbb N^+$

### 多普勒效应

$S$ : 波源，$R$ : 接收者

只考虑速度在 有向直线 : "波源 -> 接收者" 上的投影

$$
\nu_R = \frac{u-u_R}{u-u_S} \nu_S
$$

## 气体动理论

### 理想气体

$$
pV = \frac{m}{M} RT\\
p = \frac{N}{V} \frac{R}{N_A} T = nkT\\
$$

$M$ : 摩尔质量

$\frac mM$ : 物质的量

$n = \frac NV$ : 单位体积分子数

$k = \frac R{N_A}$ : 玻尔兹曼常量



理想气体压强 $p = \frac 23 n \overline {\varepsilon_t}$

理想气体平均平动动能 $\overline {\varepsilon_t} = \frac 32 kT$

平均分子动能 $\overline {\varepsilon_t} = \frac12 m_0 \overline {v^2}$

### 麦克斯韦分布律

$R$ : 摩尔气体常量

最概然速率 $v_p = \sqrt{\frac{2RT}{M}}$

平均速率 $\overline{v} = \sqrt{\frac{8RT}{\pi M}}$

方根均速率 $\sqrt{\overline{v^2}} = \sqrt{\frac{3RT}{M}}$

### 玻尔兹曼能量分布律

在 $(x,y,z)$ 处单位体积内，具有势能 $\varepsilon_P$ 的分子数：
$$
n = n_0 e^{-\frac{\varepsilon_P}{kT}}
$$

### 能量均分定理

自由度 $i = t+r+v$

平动自由度 $t=3$

转动自由度 $r=0$（单原子）, $r=2$（双原子）, $r=3$（多原子）

振动自由度 $v=0$ （刚性分子）



分子平均动能 $\overline {\varepsilon_t} = \frac i2 kT$

1mol理想气体内能 $E_m = \frac i2 RT$

### 平均碰撞频率、平均自由程

平均碰撞频率：$\overline{Z} = \sqrt 2 \pi d^2 n \overline v$

平均自由程：$\overline{\lambda} = \frac{\overline{v}}{\overline{Z}}$

$d$ : 分子有效直径

## 热力学

$$
A = \int p \ \mathrm{d}V\\
E = \frac i2 \frac{m}{M} RT\\
Q = A+E_2 - E_1
$$
$A$ : 对外做功

$Q$ : 从外界吸收的热量

$E$ : 内能

上述公式能描述封闭理想气体的状态
$$
\Delta E = \frac mM C_{V,m} \Delta T\\
C_{V,m} = \frac i2 R
$$
等容过程，摩尔定容热容：$\frac{\mathrm{d}Q}{\mathrm{d}T} = \frac{m}{M} C_{V,m} = \frac i2 R$

等压过程，摩尔定压热容：$\frac{\mathrm{d}Q}{\mathrm{d}T} = \frac{m}{M} C_{p,m} = \frac{i+2}{2} R$

摩尔热容比 $\gamma = \frac{C_{p,m}}{C_{V,m}} = \frac{i+2}{i}$

### 热机

循环一周期，吸热 $Q_1$ , 放热 $Q_2$,  对外做功 $A$ ，内能不变，热机效率 $\eta$
$$
A= Q_1 - Q_2\\
\eta = \frac A {Q_1} = 1 - \frac{Q_2}{Q_1}
$$
循环一周期，放热 $Q_1$ , 吸热 $Q_2$,  受外界做功 $A$ ，内能不变，制冷系数 $w$
$$
A= Q_1 - Q_2\\
w = \frac {Q_2} A = \frac{Q_2}{Q_1-Q_2}
$$
卡诺循环：

**两个等温**过程和**两个绝热**过程， $\eta = 1 - \frac{Q_2}{Q_1} = 1 - \frac{T_2}{T_1}$,  $w = \frac{Q_2}{Q_1-Q_2} = \frac{T_2}{T_1-T_2}$

卡诺定理：
$$
\eta_{不可逆} < \eta_{可逆} = 1 - \frac{T_2}{T_1}
$$
熵

不可逆过程 ：$\oint \frac{\mathrm{d} Q}{T} < 0$

可逆过程：$\oint \frac{\mathrm{d} Q}{T} = 0$

在 p-V 图上的过程一定可逆，$\Delta S = \int \frac{\mathrm{d} Q}{T}$ 与路径无关
$$
\mathrm{d}Q = \mathrm{d}E + \mathrm{d}A = \frac mM \frac i2R \ \mathrm{d}T + p \mathrm{d}V = \frac mM \frac i2R \ \mathrm{d}T + \frac mM \frac {RT}V \mathrm{d}V
$$
即可积分 $\frac{\mathrm{d} Q}{T}$

## 电磁学

### 电场

电场的大小用电场强度 $\vec E$ 表示，电场中电荷受力：$\vec F =  q\vec E$

点电荷产生的电场强度 $\vec E = \frac {kq}{r^2} \vec e_r$ ，其中 $k = \frac{1}{4\pi \varepsilon_0}$

**真空中的高斯定理**：$\oint _S \vec {E} \cdot \mathrm{d}\vec{S} = \frac{1}{\varepsilon_0} \sum q_i$ ，其中 $\sum q_i$ 为所有在闭合曲面内的电荷量之和

$\vec E$ 是保守/无旋场，即 $\oint_L \vec E \cdot \mathrm d\vec l = 0$



电场做功：将电荷从A移动到B电场所做的功：$W = \int_A^B q\vec E \cdot \mathrm d\vec l$  ，电势差 $U = \int_A^B \vec E \cdot \mathrm d\vec l$

电势能：将单位电荷从无穷远点移到一点所需的能量：$V_\infty = 0$ ，$V_A = -\int_{\infty}^A \vec E \cdot \mathrm d\vec l$

或是将单位电荷从A点移到B点所需的能量： $V_{AB} = V_{B} - V_{A} = -\int_A^B \vec E \cdot \mathrm d\vec l, \ $

$\vec E = -\Delta V$



### 导体

导电平衡时，**导体内部场强为0**，电荷只分布在表面，导体等势

设表面电荷 <u>面密度</u> 为 $\sigma$，有 $E = \frac{\sigma}{\varepsilon_0}$ （取垂直穿过这一小段面积的圆柱，应用高斯定理）

由高斯定理可推导出静电屏蔽现象



### 电容

给定电压，有储存电荷能力的的器件称为电容

当两极板之间的电势差为$U$，电荷量分别为 $\pm q$ ，定义电容 $C = \frac{q}{U}$



对于平行板电容器，极板间场强 $E = \frac{\sigma}{\varepsilon_0} = \frac{q}{\varepsilon_0 S}$ ，电势差 $U = \int_A^B \vec E \cdot \mathrm d\vec l = Ed = \frac{q d}{\varepsilon_0 S}$ ，电容 $C = \frac QU = \frac{\varepsilon_0 S}{d}$

可证明对于圆柱形/球形电容器，均有 $C \approx \frac{\varepsilon_0 S}{d}$



电容器串联 $\frac1C = \sum \frac 1{C_i}$， 电容器并联 $C = \sum C$



### 电介质

绝缘体，有外电场时极化

电极化率 $\chi_e$ ，电极化强度矢量 $\vec{P} = \chi_e \varepsilon_0 \vec{E}$ （对于外电场不大的各向同性电介质）

电位移矢量 $\vec{D} = \varepsilon_0 \vec{E} + \vec{P} = \varepsilon \vec E$

有电介质存在时的高斯定理：$\oint_{S} \vec {D} \cdot \mathrm{d}\vec{S} = \sum_{S} q_i$



相对电容率 $\varepsilon_r = 1 + \chi_e$ ，电容率 $\varepsilon = \varepsilon_0 \varepsilon_r$ ，对电容影响：$C = \varepsilon_r C_0 = \frac{\varepsilon_0 \varepsilon_r S}{d}$



电容器能量（静电能）$W_e = \frac 12 \frac{Q^2}{C} = \frac 12 CU^2 = \int \frac 12 DE \mathrm{d} V$

能量密度 $w_e = \frac 12 \varepsilon E^2$

### 磁场

#### 电流

电流：单位时间内通过导体横截面的电荷量  $I$

微观表达式：$I = nqSv$，$n$：单位体积电荷数，$q$：单个电荷电量，$S$：截面积，$v$：移动速度

定义电流密度矢量 $\vec j$ ：$\int_S \vec j \cdot \mathrm d \vec S = I$

**电流连续性方程**：$\int_S \vec j \cdot \mathrm d \vec S = -\frac{\mathrm d Q}{\mathrm d t}$ （恒定电流：$\int_S \vec j \cdot \mathrm d \vec S = 0$）

欧姆定律微分形式：$\vec j = \sigma \vec E$ ，电导率 $\sigma = \frac{1}{\rho}$ ，$\rho$ 为电阻率，有 $R = \int \rho \frac{\mathrm d l}{S}$

电动势：将单位正电荷沿回路运动一周，**非静电力**所做的功（非静电力向体系中输入能量）

 $\mathcal{E} = \oint \vec E_k \mathrm d\vec l$



#### 磁场

磁场的大小用磁感应强度 $\vec B$ 表示，运动电荷受洛伦兹力 $\vec F = q \vec v \times \vec B$

毕奥-萨伐尔定律（电流元对一点产生的磁场，**只适用于恒定电流**）：$\mathrm d\vec B = \frac{\mu_0}{4\pi} \cdot \frac{I \mathrm d \vec l \times \vec e_r}{r^2}$ （$\vec e_r$ : 电流元指向该点的单位矢量）

> 常用积分：（可用右手螺旋定理判断方向）
>
> 载流直导线，点$(R,0)$，直导线$(0,x_1) \to (0,x_2)$
>
> $B = \int_{x_1}^{x_2} \frac{\mu_0}{4\pi} \cdot \frac{ I\mathrm d \vec x \times \vec r}{(\sqrt{R^2+x^2})^3}= \frac{\mu_0I}{4\pi R}\int_{x_1}^{x_2} \frac{R^2 \mathrm dx}{(R^2+x^2)^{3/2}} = \frac{\mu_0 I}{4\pi R} [\frac{x}{\sqrt{R^2+x^2}}]_{x_1}^{x_2}$
>
> 无限长载流直导线，点$(R,0)$
>
> $B = \frac{\mu_0 I}{2\pi R} $
>
> 圆电流轴线上一点的磁场，圆位于平面$yOz$，半径$R$，点距离圆心$x$
>
> $B = \int_L \frac{\mu_0}{4\pi} \cdot \frac{ I\mathrm d \vec l \times (\vec r_{yOz}+ \vec r_x)}{(\sqrt{R^2+x^2})^3} = \frac{\mu_0I}{4\pi}\int_L \cdot \frac{\mathrm d \vec l \times \vec r_{yOz}}{(\sqrt{R^2+x^2})^3} = \frac{\mu_0I}{4\pi} \cdot \frac{2\pi R^2}{(\sqrt{R^2+x^2})^3} = \frac{\mu_0 IR^2}{2 (R^2+x^2)^{3/2}}$
>
> 螺旋线圈 $(0,x_1) \to (0,x_2)$，单位长度匝数为 $n$
>
> $B = \int_{x_1}^{x_2} \frac{\mu_0 nIR^2 \mathrm dx}{2 (R^2+x^2)^{3/2}} = \frac{\mu_0 nI}{2} \int_{x_1}^{x_2} \frac{R^2 \mathrm dx}{(R^2+x^2)^{3/2}} = \frac{\mu_0 nI}{2} [\frac{x}{\sqrt{R^2+x^2}}]_{x_1}^{x_2}$
>
> 无限长螺旋线圈，单位长度匝数为 $n$
>
> $B = \mu_0 nI$



#### 磁通量

$\Phi = \int_S \vec B \cdot \mathrm d \vec S$

**磁场的高斯定理**：$\oint_S \vec B \cdot \mathrm d \vec S = 0$ ，说明磁场是无源场（磁感线一定闭合）

真空中磁场的安培环路定理：$\oint_L \vec B \cdot \mathrm d \vec l = \mu_0 \sum I_0 = \mu_0 \int_S \vec j \cdot \mathrm d \vec S$ （可用右手螺旋定理判断方向）



安培力：$\mathrm d \vec F = I \mathrm d \vec l \times \vec B$ （**匀强磁场中，安培力保守**，闭合载流导线受合力为0）

载流线圈在匀强磁场中的受到的磁力矩：$\vec M = \int \vec r \times \mathrm d\vec F = NISB$ （合力为0，与中心点无关，一般模型中心点为转轴）（推导较复杂）

磁矩 $\vec m = NSIe_n$ ，$\vec M = \vec m \times \vec B$ （可用右手螺旋定理判断方向）



#### 磁介质

被磁化的磁介质会激发附加磁场 $B'$ ，磁介质内磁感应强度变为 $B = B_0 + B'$，定义相对磁导率 $\mu_r = \frac{B}{B_0}$

顺磁质：$\mu_r \approx 1+10^{-4}$    抗磁质：$\mu_r \approx 1-10^{-5}$    铁磁质：$\mu_r >> 1$ 



$I_0$ ：传导电流，$I_s$：磁化电流，磁化电流性质与传导电流类似，为了计算方便引入磁介质

磁化强度与磁化电流的关系： $\oint \vec M \cdot \mathrm d \vec L = \sum I_s$

定义磁场强度 $\vec H = \frac{\vec B}{\mu_0} - \vec M$ ，有磁介质存在时磁场的安培环路定律：$\oint \vec H \cdot \mathrm d \vec L = \sum I_0$ 

有磁介质存在时磁场的高斯定律：$\oint_S \vec B \cdot \mathrm d \vec S = 0$ 



磁化特性：$\vec M = \chi_m \vec H$ , $\vec B = \mu_0 (\vec H+\vec M) = \mu_0 (1+\chi_m) \vec H= \mu_0 \mu_r \vec H = \mu \vec H$

其中 $\mu_r = 1+\chi_m$ ，$\mu = \mu_0 \mu_r$


### 电磁感应

#### 法拉第电磁感应定律

穿过导体回路中的磁通量发生变化时，会有感应电动势产生： $\mathcal{E} = -\frac{\mathrm d \Phi}{\mathrm d t}$

对于$N$匝线圈，$\mathcal{E}_i = -N\frac{\mathrm d \Phi}{\mathrm d t} = -\frac{\mathrm d \Psi}{\mathrm d t}$ ，$\Psi$ : 磁链



#### 动生电动势

洛伦兹力：$\vec F = q \vec v \times \vec B$ 

AB上的动生电动势等于把单位正电荷沿着导线从A移动到B非静电力做的功 $\mathcal{E} = \int_A^B (\vec v \times \vec B) \cdot \mathrm d \vec l$



#### 感生电场

**变化的磁场会产生感生电场** $\vec E_i$ （发现可以统一用电场解释）

那么有 $\mathcal{E} = \oint_L \vec E_i \cdot \mathrm d \vec l $ 和 $\mathcal{E} = -\frac{\mathrm d \Phi}{\mathrm d t}$ , 可得 $\oint_L \vec E_i \cdot \mathrm d \vec l = - \int_S \frac{\partial \vec B}{\partial t} \cdot \mathrm d \vec S$ 

又有 $\oint_S \vec E_i \cdot \mathrm d \vec S = 0$ （不清楚证明）

感生电场是无源有旋场



#### 自感与互感

由毕奥-萨伐尔定律，穿过线圈的磁感应强度和电流大小的比值是定值，因此定义自感系数 $L = \frac{\Psi}{I}$, 符号为 $\mathrm H$

自感电动势 $\mathcal{E}_L = -\frac{\mathrm d \Psi}{\mathrm d t} = - L\frac{\mathrm d I}{\mathrm d t} - I\frac{\mathrm d L}{\mathrm d t}$

如果线圈形状、性质不随时间改变，$\frac{\mathrm d L}{\mathrm d t} = 0$ ，$\mathcal{E}_L = - L\frac{\mathrm d I}{\mathrm d t}$



互感系数 $M = \frac{\Psi_{12}}{I_2} = \frac{\Psi_{21}}{I_1}$ ，$\Psi_{21}$ : 电流 $I_1$ 产生的磁场通过线圈2产生的磁链

互感电动势 $\begin{array} \\\mathcal{E}_{21} = -\frac{\mathrm d \Psi_{21}}{\mathrm d t} = -M \frac{\mathrm d I_1}{\mathrm d t}\\ \mathcal{E}_{12} = -\frac{\mathrm d \Psi_{12}}{\mathrm d t} = -M \frac{\mathrm d I_2}{\mathrm d t}\end{array}$



#### 磁场能量

电感的自感电动势 $\mathcal{E}_L = -L \frac{\mathrm di}{\mathrm dt}$

自感系数为 $L$ 的线圈，通有电流 $I$ 时，线圈内部储存能量 $W_m = \frac{1}{2} LI^2$

（与电容器储能公式 $\frac 12 CU^2$ 类似）



也可以定义空间中一点的磁场能量 $w_m = \frac{1}{2\mu} B^2$ ，有 $W_m = \int_{R^3} w_m$



### 麦克斯韦方程组

空间中的总电场强度 $\vec E = \vec E_{静} + \vec E_{感}$ ，总电位移矢量 $\vec D = \vec D_{静} + \vec D_{感}$ （$\vec D = \varepsilon \vec E$）

|          | 是否无旋 ($\oint_L = 0$)                                     | 是否无源（$\oint_S = 0$）                             |
| -------- | ------------------------------------------------------------ | ----------------------------------------------------- |
| 静电场   | 无旋                                                         | $\oint_S \vec D_{静} \cdot \mathrm d \vec S = \sum q$ |
| 感生电场 | $\oint_L \vec E_{感} \cdot \mathrm d \vec l = -\frac{\mathrm d \Phi}{\mathrm dt} = -\int_S \frac{\partial \vec B}{\partial t} \cdot \mathrm d \vec S$ | 无源                                                  |

$\oint_S \vec D \cdot \mathrm d \vec S = \int_V \rho \ \mathrm d V$

$\oint_L \vec E \cdot \mathrm d \vec l =- \int_S \frac{\partial \vec B}{\partial t} \cdot \mathrm d \vec S$



电流分为传导电流 $I_C$ 和位移电流 $I_D$ ，其总和称为全电流 $I_S$

位移电流 $I_D$ 能产生磁场（安培环路），**其他与传导电流 $I_C$ 没有共同之处**

$\vec j_D = \frac{\partial \vec D}{\partial t}$

$I_S = I_C + I_D = \int_S \vec j_C \cdot \mathrm d \vec S + \int_S \frac{\partial \vec D}{\partial t} \cdot \mathrm d \vec S$



空间中的磁场由传导电流和位移电流共同产生（传导电流只能在导体中传播，变化的电场一定产生位移电流，位移电流可以在真空中传播）

$\oint_L \vec H \cdot \mathrm d \vec l =  \oint_S (\vec j_C+\vec j_D) \cdot \mathrm d \vec S = \oint_S \vec j_C \cdot \mathrm d \vec S + \oint_S \frac{\partial \vec D}{\partial t} \cdot \mathrm d \vec S$

恒定电流和位移电流产生的磁场都是无源的涡旋场，

$\oint_S \vec B \cdot \mathrm d \vec S = 0$

## 电磁波

LC 震荡电路： $\nu = \frac1{2\pi \sqrt{LC}}$



电磁波传播速度 $u = \frac 1{\sqrt{\mu \varepsilon}}$

波动表达式： $\begin{array}\\E(r,t) = \frac{p_0 \omega^2 \sin \theta}{4\pi \varepsilon u^2 r} \cos \omega (t-\frac ru) = E_0 \cos \omega (t-\frac ru)=E_0 \cos (\omega t - \frac{2\pi}{\lambda} r)\\H(r,t) =\frac{p_0 \omega^2 \sin \theta}{4\pi u r} \cos \omega (t-\frac ru) = H_0 \cos \omega (t-\frac ru)=H_0 \cos (\omega t - \frac{2\pi}{\lambda} r)\end{array}$

$\vec E,\vec H$ 同相位，方向垂直，$\vec E \times \vec H$ 方向为传播方向，称 $\vec E$ 为光矢量



$\frac{H}{E} = u\varepsilon = \frac{\sqrt \varepsilon}{\sqrt \mu}$ ，$\sqrt \varepsilon E = \sqrt \mu H$



能量密度：

电场和磁场的能量密度分别为 $w_e = \frac12 \varepsilon E^2, \ w_m = \frac 12 \mu H^2$

$w = w_e + w_m = \varepsilon E^2 = \mu H^2 = \frac{EH}{u}$

$\overline w = \frac 1T \int_{t}^{t+T} w \mathrm dt = \frac 12 \varepsilon E_0^2 = \frac 12 \mu H_0^2 = \frac 12 \frac{E_0H_0}{u}$



能流密度：

单位时间通过单位垂直截面的电磁波的能量密度 $S = wu = EH$ 

光强 $I = \overline S = \frac 12 u\varepsilon E_0^2 = \frac 12 u\mu H_0^2 = \frac 12 E_0H_0$

动量：$\vec p = \frac{\vec E \times \vec H}{c^2} = \frac{\vec S}{c^2}$



### 光的干涉

$I = \frac 1\tau \int_0^{\tau} (E_{10}^2 + E_{20}^2 + 2E_{10}E_{20} \cos \Delta\varphi_P ) \mathrm dt = I_1 + I_2 + \frac 1\tau \int_0^{\tau} 2\sqrt{I_1I_2} \cos \Delta\varphi_P \mathrm dt$

非相干叠加：$\Delta \varphi_P$ 随时间变化，积分为0，$I = I_1 + I_2$

相干叠加：$\Delta \varphi_P$ 为定值，$I = I_1 + I_2 +  2\sqrt{I_1I_2} \cos \Delta\varphi_P$

特殊情况：

$\Delta \varphi_P = \pm 2k\pi$ ，           $I = I_{max} = (E_{10} + E_{20})^2$ 

$\Delta \varphi_P = \pm (2k-1)\pi$ ，$I = I_{min} = (E_{10} - E_{20})^2$

定义干涉条纹的对比度 $\eta = \frac{I_{max}-I_{min}}{I_{max}+I_{min}}$



#### 分波阵面法产生光的干涉

杨氏双缝干涉实验：

波程差 $\delta = r_2 - r_1$ ，$r_1 = \sqrt{(x-\frac d2)^2+D^2}, \ r_2 = \sqrt{(x+\frac d2)^2+D^2}$ ，$(r_2-r_1)(r_2+r_1) = r_2^2 - r_1^2 = 2dx$

$D\gg d$ , $r_2+r_1 \approx 2D$ ,  $\delta = r_1-r_2 \approx \frac{d}{D}x$



明条纹中心位置：$\delta = k \lambda$

暗条纹中心位置：$\delta = (k+\frac{1}{2})\lambda$



#### 光程

真空中波长为 $\lambda$ 的单色光，在折射率为 $n$ 的透明介质中的波长 $\lambda' = \frac{\lambda}{n}$

定义光程 $L = n l$ ，则光程差 $\delta = \Delta L$ 与介质折射率无关



理想透镜不产生光程差，从物点发出，经过透镜任一点折射到像点的光的光程相同

#### 分振幅法

半波损失：若反射时 $n_1<n_2$，附加光程差 $\delta = \frac{\lambda}{2}$ （n小 -> n大 -> n小 / 光疏 -> 光密 -> 光疏）

薄膜干涉：光从 $n_1$ 介质以折射角 $i$ 进入厚度为 $e$ 的 $n_2$ 再反射返回 $n_1$ ，光程差 $\delta = 2e\sqrt{n_2^2 - n_1^2 \sin^2 i}$ （未考虑半波损失）



#### 光学常识

<img src="C:\Users\29459\AppData\Roaming\Typora\typora-user-images\image-20211220142821916.png" alt="image-20211220142821916" style="zoom: 33%;" />

<img src="C:\Users\29459\AppData\Roaming\Typora\typora-user-images\image-20211220143016847.png" alt="image-20211220143016847" style="zoom:33%;" />

<img src="C:\Users\29459\AppData\Roaming\Typora\typora-user-images\image-20211220143840793.png" alt="image-20211220143840793" style="zoom:33%;" />

<img src="C:\Users\29459\AppData\Roaming\Typora\typora-user-images\image-20211220143927657.png" alt="image-20211220143927657" style="zoom:50%;" />

![img](https://img2020.cnblogs.com/blog/1916612/202106/1916612-20210621132610559-938046939.png)

全反射：$\sin i_B = \frac{n_2}{n_1}$

可见光：波长 780nm(红)～400nm(紫)

### 光的衍射

#### 单缝夫琅禾费衍射

单色平行光经过狭缝出现各个角度的衍射光，狭缝宽度为 $a$ ，单色光波长为 $\lambda$，经过焦距为 $f$ 的凸透镜在光屏上投影出明暗纹

观察屏上光强 $I = I_0 (\frac{\sin\beta}{\beta})^2$ ，其中 $\beta = \frac \pi\lambda a\sin \theta$ ，$\theta$ 为衍射角

暗纹（光强为0）满足 $a\sin \theta = \pm k\lambda,\ (k \not=0, k=1,2, \dots)$

明纹满足 $a\sin \theta = \pm \frac{2k+1}{2} \lambda,\ (k \not=0, k=1,2, \dots)$



$\theta_k = \arcsin \frac{k\lambda}{a} \approx \frac{k\lambda}{a}$

中央明纹 $\Delta \theta_0 = 2\frac{\lambda}{a}$ ，其余明纹 $\Delta\theta_k = \theta_{k+1} - \theta_k = \frac\lambda a$

线宽度 $\Delta x = f \Delta \theta$



#### 圆孔衍射

中心明圆环（艾里斑）角半径  $\theta_0 = \arcsin(0.61\frac\lambda R) \approx 0.61\frac\lambda R = 1.22 \frac\lambda D$

半径 $r_0 = f\tan\theta_0 \approx 0.61\frac{\lambda f} R = 1.22 \frac{\lambda f} D$



光学仪器最小分辨角 $\delta\varphi = \theta_0$ ，分辨本领 $R = \frac{1}{\delta\varphi}$



#### 光栅衍射

光栅上有很多等宽平行狭缝，狭缝间宽度为 $d$，狭缝宽度为 $a$，不透明部分宽度为 $b$，$d=a+b$，光程差 $\delta = d\sin \theta$

$\delta = d\sin \theta = \pm k\lambda$ ，则出现干涉条纹，记作第 $k$ 级明条纹



缺级现象：$\begin{cases}d\sin \theta = \pm k\lambda\\a\sin \theta = \pm k'\lambda\end{cases}$ 同时满足则缺级

光强分布公式：$I = I_0 (\frac{\sin\beta}{\beta})^2(\frac{\sin Nu}{\sin u})^2$ ，$u=\frac{\pi}{\lambda} d\sin\theta$ ，当 $u=\pm k\pi$ 时得到主极大，光强是单缝衍射的 $N^2$ 倍



X射线衍射：相邻两层晶面距离 $d$ ，衍射条件 $2d\sin\theta = k\lambda\ (k=1,2,\dots)$

### 光的偏振

#### 偏振片

强度为 $I_0$ 的**自然光**垂直入射到偏振片上，透出来的光 $I = \frac12 I_0$

马吕斯定律：强度为 $I_0$ 的**线偏振光**垂直入射到偏振片上，透出来的光 $I = I_0 \cos^2\alpha,\ E=E_0 \cos \alpha$

其中 $\alpha$ 是 偏振光光振动方向 与 偏振片偏振化方向 的夹角

偏振光可以矢量相加、分解，自然光不能



#### 布儒斯特定律

一束自然光投射到介质分界面时，反射光和折射光很可能为部分偏振光

布儒斯特定律：如果入射角满足 $\tan i_B = \frac{n_2}{n_1}$ （或者说反射线与折射线垂直），反射光为完全偏振光，光振动方向垂直于反射面（折射光不一定是）



#### 波片和椭圆偏振光

线偏振光与主光轴夹角$\alpha$进入波片后，分解为**沿光轴的e光**和垂直于光轴的o光，$E_e = E_0 \sin \alpha,\ E_o = E_0 \cos\alpha$

经过距离$d$产生光程差 $\delta_0 = (n_o-n_e)d$，相位差 $\Delta\varphi_0 = \frac{2\pi}{\lambda} \sigma_0$

1/4波片：$\delta = \pm \lambda/4,\ \Delta\varphi_0 = \pm \pi/2$，椭圆偏振光，长短轴为e,o，长度为 $E_0\sin\alpha, E_0\cos\alpha$

1/2波片：$\delta = \pm \lambda/2,\ \Delta\varphi_0 = \pm \pi$，仍是线偏振光，偏振化方向转动$2\alpha$，光强不变

全波片：$\delta = \pm \lambda,\ \Delta\varphi_0 = \pm 2\pi$，仍是线偏振光，偏振化方向不变



椭圆计算：
$$
x=A_1\cos(\omega t+\varphi_1)\\
y=A_2\cos(\omega t+\varphi_2)\\
\\
\frac{x^2}{A_1^2} + \frac{y^2}{A_2^2} - 2\frac{xy}{A_1A_2}\cos(\varphi_1-\varphi_2) = \sin^2 (\varphi_1-\varphi_2)
$$


长/短轴与波片对齐的椭圆偏振光经过波片变成线偏振光



#### 偏振光的干涉

椭圆偏振光经过偏振片后得到两束振动方向相同，有相位差的光

## 狭义相对论

### 洛伦兹变换

有两个惯性系 $S,S'$，在 $S$ 系中， $S'$ 以速度 $v$ 沿坐标轴 $xx'$ 移动

在 $S$ 系中，事件发生于$(x,t)$，在 $S'$ 系中，事件发生于$(x',t')$

#### 坐标变换

正变换：
$$
\begin{cases}
x' = \frac{x-vt}{\sqrt{1-v^2/c^2}} = \gamma(x-vt)\\
y'=y\\
z'=z\\
t' = \frac{t-\frac{v}{c^2}x}{\sqrt{1-v^2/c^2}} = \gamma(t-\frac{v}{c^2}x)
\end{cases}
$$
逆变换：令 $v = -v$

#### 速度变换

定义两个系中的速度：$u_x = \frac{\mathrm dx}{\mathrm dt}, u_y = \frac{\mathrm dy}{\mathrm dt}, u_z = \frac{\mathrm dz}{\mathrm dt}$，$u_x' = \frac{\mathrm dx'}{\mathrm dt'}, u_y' = \frac{\mathrm dy'}{\mathrm dt'}, u_z' = \frac{\mathrm dz'}{\mathrm dt'}$

正变换：
$$
\begin{cases}
\mathrm dx' = \gamma(\mathrm dx-v\mathrm dt)\\
\mathrm dy' = \mathrm dy\\
\mathrm dz' = \mathrm dz\\
\mathrm dt' = \gamma(\mathrm dt - \frac{v}{c^2} \mathrm dx)
\end{cases}
$$

$$
\begin{cases}
u_x' = \frac{\mathrm dx'}{\mathrm dt'}\\
u_y' = \frac{\mathrm dy'}{\mathrm dt'}\\
u_z' = \frac{\mathrm dz'}{\mathrm dt'}\\
\end{cases}
$$

逆变换：令 $v = -v$



### 时空观

#### 因果关系

某两个事件在参考系$S$中的发生顺序和在$S'$中的发生顺序可能不同，但不影响因果

在不同坐标系中定义两个事件的时空间隔：
$$
\begin{cases}
d^2 = c^2(t_1-t_2)^2 - [(x_1-x_2)^2 + (y_1-y_2)^2 + (z_1-z_2)^2]\\
d'^2 = c^2(t'_1-t'_2)^2 - [(x'_1-x'_2)^2 + (y'_1-y'_2)^2 + (z'_1-z'_2)^2]\\
\end{cases}
$$
可以证明，对于任意参考系 $S,S'$ 有 $d^2 = d'^2$

类时间隔：$d^2 > 0$ ，存在坐标系 $S'$，两事件发生于同一地点不同时间，发生先后顺序不可颠倒，可以有因果

类光间隔：$d^2 = 0$ ，发生先后顺序不可颠倒，可以有因果，如果有因果，必以光速联系

类空间隔：$d^2 < 0$ ，发生先后顺序可以颠倒，不可能有因果



#### 长度收缩效应

对于静止的观测者，静止时长度为 $L_0$ 的物体在以相对速度 $v$ 运动时长度变为 $L = \sqrt{1-v^2/c^2} \cdot L_0$



移动坐标系：$(x'_1=0,t'_1=t'_1) \leftrightarrow (x'_2=L,t'_2=t'_2)$

静止坐标系：$(x_1=\gamma(vt'_1),t_1=\gamma t'_1) \leftrightarrow (x_2=\gamma(L+vt'_2),t_2=\gamma(t'_2+v/c^2 \cdot L))$



$\gamma t'_1=\gamma(t'_2-v/c^2 \cdot L),\ t_1'=t'_2+v/c^2 \cdot L$

$x_2-x_1 = \gamma(L + vt'_2) - \gamma(vt'_1) = \gamma(L - v^2/c^2 \cdot L) = \sqrt{1-v^2/c^2} \cdot L$

#### 时间延缓效应

对于静止的观测者，两事件时间间隔为 $\tau_0$，对于以相对速度 $v$ 移动的观测者，两事件时间间隔为 $\tau = \sqrt{1-v^2/c^2} \cdot \tau_0$



静止坐标系：$(x_1=0,t_1=0) \to (x_2=vt,t_2=t)$

移动坐标系：$(x'_1=0,t'_1=0)\to(x'_2=0,t'_2=\frac{t-v/c^2\cdot vt}{\sqrt{1-v^2/c^2}}=\sqrt{1-v^2/c^2} \cdot t)$



### 相对论动力学

静止质量为 $m_0$ 的物体，运动质量 $m=\frac{m_0}{\sqrt{1-v^2/c^2}} = \gamma m_0$

动量 $\vec p = m\vec v$

力 $\vec F = \frac{\mathrm d \vec p}{\mathrm d t} = m\frac{\mathrm d \vec v}{\mathrm d t} + \vec v\frac{\mathrm d m}{\mathrm d t}$



动能 $E_k = mc^2 - m_0 c^2$，（注意 $E_k=\frac12 mv^2$ 只是在 $v\ll c$ 时的近似表达式）

总能量 $E = mc^2$

静止能量 $E=m_0c^2$



能量-动量关系式：$E^2 = E_0^2 + p^2c^2$

光子没有静止质量，但有能量



## 量子论

### 黑体辐射

物体在任何温度下都会向外辐射电磁波，也会吸收电磁波



单色辐出度：$e(\lambda,T)$ 指温度为 $T$ 的物体，在单位时间、单位表面积上辐射出的波长在 $\lambda$ 附近的电磁能量

辐出度 $E(T)$ 指温度为 $T$ 的物体，在单位时间、单位表面积上辐射出的总电磁能量

$E(T) = \int_{0}^{\infty} e(\lambda,T) \mathrm d\lambda$



在任何温度下都能完全吸收照射到它表面的所有波长电磁辐射的物体称为**黑体**

温度相同时黑体热辐射规律相同



斯特藩-玻尔兹曼定律：$E_B(T) = \int_{0}^{\infty} e_B(\lambda,T) \mathrm d\lambda = \sigma T^4$

$\sigma$ 为斯特藩-玻尔兹曼常量

> CASIO : 物理化学常量 - 9



维恩位移定律：对于确定的$T$，使 $e_B(\lambda,T)$ 最大的 $\lambda_m$ 称为峰值波长，存在关系 $\lambda_m T = b$

$b$ 为维恩位移常量



普朗克公式：$e_B(\lambda,T) = \frac{2\pi hc^2}{\lambda^5} \frac{1}{e^{\frac{hc}{k\lambda T}}-1}$



### 光电效应

现象：

光照射到阴极表面时，有光电子溢出

饱和光电流大小 $i_m$ 与入射光强度 $I$ 成正比

光电子最大初动能 $E_{k,\max}$ 与入射光频率成线性关系 $E_{k,\max} = \frac 12 mv_\max^2 = eU_a = eK\nu - eU_0$



频率为 $\nu$ 的光子的能量 $\varepsilon = h\nu$ ，$h$ 为普朗克常量

光强 $I = \overline S = nh\nu$



光电效应方程：$\frac 12 mv_\max^2 = h\nu - A$

$A$ 是金属逸出功，金属红限频率：$\nu_0 = \frac Ah$ ，频率低于红限频率不能溢出

一个电子吸收了一个光子的能量



波粒二象性：频率为 $\nu$ （$\lambda\nu=c$）的光子具有能量、质量、动量：$\begin{cases}\varepsilon=h\nu\\m=\frac{\varepsilon}{c^2}\\p=mc=\frac{h\nu}{c}=\frac h\lambda\end{cases}$

### 康普顿效应

频率为$\nu$的光子与静止质量为$m_0$的静止电子碰撞后，设光子偏移角为 $\theta$ ，电子偏移角为 $\varphi$，由能量、动量守恒有：
$$
\begin{cases}
h\nu_0 + m_0c^2 = h\nu+mc^2\\
\frac{h\nu_0}{c} = \frac{h\nu}{c} \cos \theta + m v\cos \varphi\\
\frac{h\nu}{c} \sin \theta + m v\sin \varphi
\end{cases}
$$
联立得到波长偏移公式：在偏移 $\theta$ 的方向上测得的波长与原波长的**偏移值**
$$
\Delta\lambda = \lambda_C (1-\cos\theta) = \frac{h}{m_0c} (1-\cos\theta)
$$
$\lambda_C = 2.43\times 10^{-12}$ 为康普顿波长

> CASIO 原子与核常数 8

### 氢原子光谱

里德伯公式：$\sigma = \frac1\lambda = R_H (\frac 1{m^2} - \frac1{n^2})$，$R_H$ 为里德伯常量

玻尔的氢原子理论：$E_n = -\frac1{n^2}(\frac{me^4}{8\varepsilon_0^2h^2}) = \frac{E_1}{n^2}$ ，$E_1 = -13.6\ \text{eV}$，$h\nu = E_n - E_m$



轨道半径 $r_n = n^2 r_1$，$r_1$ 为第一玻尔轨道半径

稳定轨道的角动量：$L = mvr = n\frac{h}{2\pi}$ 

（在量子力学下，这两个公式是错误的）

![查看源图像](https://lifeng.lamost.org/courses/wlsy/FH/images/H_atom_spectrum_2.jpg)

## 量子力学

### 德布罗意波

具有能量 $E$ 和动量 $p$ 的粒子，对应平面单色波的频率和波长为（不是电磁波，注意相对论效应）：
$$
E = h\nu\\
p = \frac h\lambda\\
$$

### 不确定关系

位置和动量的不确定关系：$\Delta x \cdot \Delta p_x \ge \frac\hbar2$ ，$\hbar = \frac{h}{2\pi}$

表面微观粒子的坐标和相应方向的动量不可能同时准确确定

谱线宽度为 $\Delta \lambda$



能量和时间的不确定关系：$\Delta E \cdot \Delta t \ge \frac\hbar2$

$\Delta E$ : 激发态对应能量的不确定度，$\Delta t$ : 平均寿命



### 一维薛定谔方程的应用

#### 波函数

$\Psi(x,t) = \Psi_0 \exp(-i2\pi(\nu t-\frac x\lambda))$

$\Psi(\vec r,t) = \Psi_0 \exp(-\frac{i}{\hbar} (Et-\vec p\cdot\vec r))$

$P(\vec r,t) = |\Psi(\vec r,t)|^2$ ，$\int P(\vec r,t) \mathrm dV = 1$



#### 定态薛定谔方程

如果粒子在恒定势场 $U(\vec r,t) = U(\vec r)$ 中运动，那么 $\Psi(\vec r,t) = \Psi(\vec r) f(t)$

一维定态薛定谔方程：$\left[-\frac{\hbar}{2m} \frac{\mathrm d^2}{\mathrm dx^2} + U(x)\right] \Psi(x) = E\Psi(x)$



##### 一维无限深势阱

$U(x) = \begin{cases}0 & 0\le x\le a\\\infty & x<0,x>a\end{cases}$

波函数：$\Psi(x) = \begin{cases}\sqrt{\frac 2a} \sin \frac{n\pi}{a}x & 0\le x\le a\\0 & x<0,x>a\end{cases}$

概率密度：$P(x) = |\Psi_n(x)|^2 = \frac 2a \sin^2 \frac{n\pi}{a}x\quad (0\le x\le a)$

利用 $\Psi(0)=\Psi(a)=0$ 得到能量：$E_n = \frac{n^2h^2}{8ma^2}\quad (n=1,2,3,\dots)$



##### 一维谐振子

$U(x) = \frac 12m\omega x^2$

$E_n = (n+\frac 12) \hbar \omega = (n+\frac12) h\nu$



### 原子和固体的量子理论

#### 径向波函数

概率密度 $P(r) = |R(r)|^2r^2$



#### 四量子数

主量子数 $n=1,2,3,\dots$

角量子数 $l=0,1,2,\dots,(n-1)$

磁量子数 $m_l=0,\pm1,\pm2,\dots,\pm l$

自旋磁量子数 $m_s = \pm \frac 12$



角动量 $L = \sqrt{l(l+1)}\ \hbar$  ，$L_z = m_l \hbar$ 

自旋角动量 $S = \frac{\sqrt 3}{2} \hbar$ ，$S_z = m_s \hbar$

自旋磁矩 $\mu_S = -\frac em S$ ，$\mu_z = \pm \frac e{2m} \hbar$



#### 泡利不相容原理

在 $n$ 相同，$l=l_0$ 的次壳层上最多容纳电子数为 $2(2l+1)$ （$2$种$m_s$，$(2l+1)$种$m_l$）

$Z_n = \sum_{l=0}^{n-1} 2(2l+1) = 2n^2$



#### 能量最小原则

能级高低按 $(n+0.7l)$ 的值确定



#### 激光

粒子数正常分布：大多数粒子处于 $E_1$

粒子数反转分布：大多数粒子处于 $E_2$



光学谐振腔：形成驻波 $L = k\lambda_k / 2n$



