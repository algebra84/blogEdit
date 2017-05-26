---
title: 最小二乘法
date: 2017-05-26 13:59:28
tags: 机器学习
categories: 技术
---

<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

机器学习依赖许多数学基础，其中一个入门级的优化就是最小二乘法。

## 最小二乘法
最小二乘法分为两类：线性最小二乘法和非线性最小二乘法。其主要区别是拟合函数是否线性，我们主要介绍线性最小二乘法。
线性最小二乘法：
给定函数\\(f(x)=w^T*x + b\\)，
给出m组数据\\(x^i\\),\\(y^i\\):i=1...m,其中\\({x,y,x^i,y^i,w}\in {\mathbb R}^n\\)。
求w,b，使得：
$$cost(w,b) = \min \sum_{i=1}^m (f(x^i)-y^i)^2$$
对于线性最小二乘法，利用一阶偏导数cost'(w,b) = 0可以求得解析解，这里我们就不深入讨论了。因为解析解涉及到求解逆矩阵，当矩阵很大时，逆矩阵的计算量非常大，所以我们想是不是可以求解数值解，这样虽然可能有一点点误差，但是计算量也会少很多；而且，对于非线性最小二乘法而言，本身就很难获取解析解。所以计算优化的主要目标还是求解最小二乘法的数值解。

## 梯度下降
梯度，直观的理解是cost函数变小的方向。
我们以一维来举例说明，高维情况可以类推。
函数\\(q(x) = (1-x)^2\\),当\\(x=x_0\\)时，其导数\\(f'(x_0)\\)的反方向即q(x)大小减小的方向。
也就是说:
$$x_1 = x_0 - \Delta * f'(x_0), f(x_1) <= f(x_0)$$

这样理论上，我们每步减去一个\\( \Delta \\)  时,就可以不断接近q(x)的最小值。
这样梯度下降逐渐收敛时，我们就得到了数值解
下图即为等高线图演示梯度下降。
![Alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/7/79/Gradient_descent.png/350px-Gradient_descent.png)


