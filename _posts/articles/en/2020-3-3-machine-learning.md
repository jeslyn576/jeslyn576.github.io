---
layout: post
title: "常用机器学习算法（一）"
image: /assets/img/head.png
header:
  image: /assets/img/head.png
tags: ["线性回归", "最小二乘法", "几何角度"]
ref: example-project-page
lang: en
---

# **线性回归**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;线性回归说白了它就是自变量和因变量之间的关系，我们的工作就是想找出一条最适合的直线（多元就成超平面了）去预测接下来的数值。细分的话还有一元线性回归/二元回归/多元线性回归，几元就是一个样本里包含几个维度的意思，万变不离其宗，都是一个公式：  $y=w^Tx+b$

那把这个简单的公式展开来看，可能看的更明白一点:

$$D=\{(x_1,y_1),(x_2,y_2),(x_3,y_3)...(x_n,y_n)\} $$
从下面这俩矩阵中能看到，这个数据集是有p个维度（p个特征），n个样本
$$x=\begin{pmatrix}
{x_{11}}&{x_{12}}&{\cdots}&{x_{1p}}\\
{x_{21}}&{x_{22}}&{\cdots}&{x_{2p}}\\
{\vdots}&{\vdots}&{\ddots}&{\vdots}\\
{x_{n1}}&{x_{n2}}&{\cdots}&{x_{np}}\\
\end{pmatrix}$$

$$y=\begin{pmatrix}
{y_{1}}\\
{y_{2}}\\
{\vdots}\\
{y_{n}}\\
\end{pmatrix}$$

 $$w=\begin{pmatrix}
{w_{1}}\\
{w_{2}}\\
{\vdots}\\
{w_{n}}\\
\end{pmatrix}$$

$$y=w_1x_1+w_2x_2+w_3x_3+...+w_nx_n+b$$

注意哦，这个式子的$x_1$其实长这样$(x_{11},x_{12},...x_{1p})$,一个样本有p个特征嘛。
## 最小二乘法

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;前情铺垫完毕了，可以说说怎么找这个合适的线，那首先得明确一下合适的标准，啥叫合适呢？就引出了我的下文，看！我多会写铺垫~

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;最小二乘法就是寻找这个合适的线的一个方法，优化方法当然还有其他，比如最为广知的梯度下降法。但就线性问题而言，理论上来说呢，首先我们要默认误差是符合正态分布（高斯分布）的，那么最小二乘法就是最优解。所以我这里要讲最小二乘法！多有理有据！

让我来郑重推出核心公式，最小二乘估计：
$$L(w)=\sum_{i=1}^N{||w^Tx_i+b-y_i||^2}$$
这公式的意思很显而易见吧，就是每个预测值和真实值的差的平方的和。因为这个b偏差嘛，后面一求导就没了，我推公式先去掉它，当做没有偏差的样子哦咱心里有数就行好吧。。。
$$\begin{aligned}
L(w)&=\sum_{i=1}^N{||w^Tx_i-y_i||^2}\\
&=\sum_{i=1}^N{(w^Tx_i-y_i)^2}\\
&=(w^Tx_1-y_1,w^Tx_2-y_2,...,w^Tx_n-y_n)\begin{pmatrix}
{w^Tx_1-y_1}\\
{w^Tx_2-y_2}\\
{\vdots}\\
{w^Tx_n-y_n}\\
\end{pmatrix}\\
&=(w^T(x_1,x_2,...,x_n)-(y_1,y_2,...,y_n))\begin{pmatrix}
{w^Tx_1-y_1}\\
{w^Tx_2-y_2}\\
{\vdots}\\
{w^Tx_n-y_n}\\
\end{pmatrix}\\
&=(w^Tx^T-y^T)(xw-y)\\
&=w^Tx^T*xw-w^Tx^Ty-y^Txw+y^Ty\\
&=w^Tx^T*xw-2w^Tx^Ty+y^Ty
\end{aligned}$$

推到这就相当于推到高地了，离胜利不远了！

$$w^T=argmin\,L(w)$$ 

那肯定要让它最小嘛，差值越小说明这线越合适对吧~

$$\frac{\partial L(w)}{\partial w}=2x^Txw-2x^Ty=0$$
$$w=(x^Tx)^{-1}x^Ty$$

合适的参数找着了，合适的线就有啦，这就算拆塔啦，victory！

其实还可以从几何角度去看，有$x$构成的一个p维空间，y不在这个空间里哦（除非x每个样本点都落在y上），我们也是要找y离$x$平面最近，就是投影啦。

投影垂直$x$平面上的每个$x$,即$x\perp y-yw$,由$x^Tx=0$,可得$x^T(y-xw)=0$,也能得出$w=(x^Tx)^{-1}x^Ty$。

其实线性回归看着简单，就一个公式，深挖会有很多知识，真是越学越感觉学海深不可测==硬顶
