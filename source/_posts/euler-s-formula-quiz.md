---
title: Euler's formula quiz
author: Jun Hu
tags:
  - Euler
date: 2020-05-16 20:36:12
---

The goal is to prove that

$\exp(x+y)\exp(x)\exp(y)$,

or in another form

$e^{(x+y)}=e^x+e^y$.

<!-- more -->

1. Show that when you fully expand $\exp(x)\cdot\exp(y)$, each term has the form $\frac{x^k\cdot y^m}{k!\cdot m!}$.

   From Cauchy product,
   $$
   \left(\sum_{i=0}^\infty a_i\right) \cdot \left(\sum_{j=0}^\infty b_j\right) = \sum_{k=0}^\infty c_k
   $$
   where, $c_k=\sum_{l=0}^k a_l b_{k-l}$

$$
\begin{align}
\nonumber\exp(x)\cdot\exp(y)&=\sum_{n=k+m}^{\infty}\frac{x^{n}}{n!}\sum_{m}^{\infty}\frac{y^{m}}{m!}\\\\
&=\sum_{k}^{\infty}\sum_{m}^{k}\frac{x^{k}}{k!}\frac{y^{m}}{m!}
\end{align}
$$

2. Show that when you expand $\exp(x+y)$, each term has the form $\frac{1}{n!}{n\choose k}x^ky^{n-k}$.

	From Binomial theorem, 
$$
(x+y)^{n}=\sum _{k=0}^{n}{n \choose k}x^{n-k}y^{k}=\sum _{k=0}^{n}{n \choose k}x^{k}y^{n-k}
$$

$$
\begin{align}
\nonumber\exp(x+y)&=\sum_n\frac{(x+y)^n}{n!}\\\\
\nonumber&=\sum_{n}\frac{1}{n!}\sum_{n=k+m} {n \choose k} x^ky^m \\\\
&= \sum_{n=k+m} \frac{1}{n!}{n\choose k}x^ky^{n-k}
\end{align}
$$


3. Compare the two results above to explain why $\exp(x+y)=\exp(x)\cdot\exp(y)$.

	Compare (1) and (2), as ${n\choose k}=\frac{n!}{k!m!}$,
	$$
	\begin{align}
	\nonumber\exp(x+y)&=\sum_{n=k+m} \frac{1}{n!}\frac{n!}{k!m!}x^ky^m\\\\
	&=\exp(x)\cdot\exp(y)
	\end{align}
	$$
	
4. Would this result still hold if x and y are complex numbers? What about matrices?
	Note that in Binomial theorem, 
	$$
	\sum _{k=0}^{n}{n \choose k}x^{n-k}y^{k}=\sum _{k=0}^{n}{n \choose k}x^{k}y^{n-k}
	$$
	does NOT work for matrices, so it does NOT hold for matrices.

---


Reference:

*- [YouTube: What is Euler's formula actually saying? | Lockdown math ep. 4](https://youtu.be/ZxYOEwM6Wbk)*

*- [Proving the Exponential Functional Equation exp(x+y)=exp(x)exp(y)](https://youtu.be/owdvXpe_-Zc)*

