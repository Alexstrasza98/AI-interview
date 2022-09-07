# Principle Component Analysis (PCA)
## Introduction
PCA是一种**线性**的降维方法。其通过一个正交矩阵，把原有变量通过线性组合的方式构成一组新变量（称为主成分）。
主成分往往有低于原变量的维度，并且能够降低变量之间可能的相关性。同时我们希望新变量能够最大程度地保留原变量中的信息。

用数学语言来说：我们有一组数据点 $X \in R^{n \times d}$，我们希望得到一个正交矩阵 $A \in R^{d \times k}, A^TA=I$，使得变换后的数据点 $\hat{X} = XA \in R^{n \times k}$ ( $k \ll d$ ）。
问题在于如何求解这个矩阵 $A$，可以从两种思路推导：
1. 最大化数据间方差
2. 最小化数据点和投影点之间的距离

## Theory
1. 最大化数据间方差

考虑一个样本点 $x_i \in R^d$，和一个单位向量 $w \in R^d, w^Tw=1$, $x$ 在 $w$方向的投影点是 $w^Tx$，那么 $n$个样本点投影后的方差可以表达为
$$\operatorname{Var}\left(w^T x_i\right)=\frac{1}{n} \sum_{i=1}^n\left(w^T x_i-\operatorname{mean}\left(w^T x_i\right)\right)^2$$

假设输入样本是零均值，那么上式可化为

$$w = \arg \max_w \sum_{i=1}^{n} \left(w^T x_i\right)^2=\|X w\|_2^2=w^T X^T X w$$

2. 最小化数据点和投影点间的距离

投影点的表示为 $(w^Tx_iw)$, 则距离可以定义为Squared Approximation Error

$$
\begin{aligned}
w &=\arg \min_w \sum_{i=1}^n\left\|x_i-w w^T x_i\right\|^2 \quad \text { s.t. } \quad w^T w=1 \\
&=\arg \min_w \sum_{i=1}^n x_i^T x_i-w^T \underbrace{\left(\sum_{i=1}^n x_i x_i^T\right)}_{=X X^T} w
\end{aligned}
$$

由于第一项是常数，因此可以转化为新的优化问题：

$$w = \arg \max_w \sum_{i=1}^{n} \left(w^T x_i\right)^2=\|X w\|_2^2=w^T X^T X w$$

两者是殊途同归的。
