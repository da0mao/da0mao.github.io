---
title: Understand and derive Einstein field equations
author: Jun Hu
date: 2019-08-10 21:58:00
tags:
 - special relativity
 - general relativity
 - tensor

---

In this post I am to follow DrPhysicsA's excellent explanation (video provided at the end) and to provide some ideas myself.
I am also planning to re-write it afterwards - based on my own understanding. 

<!-- more -->

# Introduction

> The Einstein field equations (EFE; also known as Einstein's equations) comprise the set of 10 equations in Albert Einstein's general theory of relativity that describe the fundamental interaction of gravitation as a result of spacetime being curved by mass and energy. First published by Einstein in 1915 as a tensor equation, the EFE relate local spacetime curvature (expressed by the Einstein tensor) with the local energy and momentum within that spacetime (expressed by the stress–energy tensor).

First let's take a look at these equations (why "these" ? see below):
$$
R_{\mu\nu}-{\textstyle\frac12}Rg_{\mu\nu}-\Lambda g_{\mu\nu}=-\frac{8\pi G}{c^4}T_{\mu\nu}
$$
where $R_{\mu \nu}$ is the Ricci curvature tensor, R is the scalar curvature, $g_{\mu nu}$ is the metric tensor, Λ is the cosmological constant, G is Newton's gravitational constant, c is the speed of light in vacuum, and $T_{\mu \nu}$ is the stress–energy momentum tensor. 

$\mu$ and $\nu$ have numbers from 0 to 3, so these tensors with indices have 4x4=16 "versions" while 6 of them are duplicates, so there are in total 10 equations. 

The equations balance two things: Curvature of the spacetime on the left and mass/energy on the right. Thus some may say:

**_Mass tells spacetime how to curve and curved spacetime tells mass how to move._**

---

# Metric Tensor

Say there is a field and the height of the field is $\Phi$, then the change of the height $d\Phi$ in the $x^n$ coordinator system (for e.g. if n=3 then it is a 3-D space with coordinators of $x^1, x^2 \ and \ x^3$) can be descripted as:

$$
\begin{align}
d\Phi&=\frac{\partial\Phi}{\partial x^1}dx^1+\frac{\partial\Phi}{\partial x^2}dx^2\cdots\nonumber\\\\
&=\sum_n{\frac{\partial\Phi}{\partial x^n}dx^n}
  \label{eq:1}
\end{align}
$$

_Consider a $y^1$ in $y$ coordinator system, and again $x^1, x^2...etc.$ in $x$ coordinator system, then use chain rule we have_
$$
\begin{align}
\frac{d\Phi}{dy^1}&=\frac{\partial\Phi}{\partial x^1}\frac{\partial x^1}{\partial y^1}+\frac{\partial\Phi}{\partial x^2}\frac{\partial x^2}{\partial y^1}\cdots\nonumber\\\\
&=\sum_m\frac{\partial\Phi}{\partial x^m}\frac{\partial x^m}{\partial y^1}\nonumber
\end{align}
$$
$$
\begin{equation}
\frac{\partial \Phi}{\partial y^n}=\sum_m{\frac{\partial\Phi}{\partial x^m}\frac{\partial x^m}{\partial y^n}}
  \label{eq:2}
\end{equation}
$$


> Note: Equation \eqref{eq:2} is a collection of $n$ equations

Now we transform equation \eqref{eq:1} in a vector (rank 1 tensor) form by letting $d\Phi=V_y^n$ the change of height to be a vector in y coordinator system, and $dx^n=V_x^m$ the change of space to be a vector in x coordinator system:
$$
\begin{equation}
V_y^n=\sum_m{\frac{\partial y^n}{\partial x^m}V_x^m}
  \label{eq:3}
\end{equation}
$$

Now consider a rank 2 tensor, which is a combination of two vectors $T^{mn}=A^nB^n$

Substitute it into \eqref{eq:3}
$$
\begin{align}
T_y^{mn}&=A^mB^n\nonumber\\\\
&=\sum_{r,s}{\frac{\partial y^m}{\partial x^r}A_x^r\frac{\partial y^n}{\partial x^s}B_x^s}\nonumber\\\\
&=\sum_{r,s}{\frac{\partial y^m}{\partial x^r}\frac{\partial y^n}{\partial x^s}}T_x^{rs}
\label{eq:4}
\end{align}
$$

> Equation \eqref{eq:4} is a contravariant transformation
>
> Note: Equation \eqref{eq:4} is now a collection of $m\times n$ functions

Similarly,
$$
\begin{equation}
T_{mn}(y)=\sum_{r,s}{\frac{\partial x^r}{\partial y^m}\frac{\partial x^s}{\partial y^n}T_{rs}(x)}
\label{eq:5}
\end{equation}
$$
> Equation \eqref{eq:5} is a covariant transformation
>
> or we can use prime coordinators to avoid confusions caused by $T_y \ and \  T(y)$
>
> Such as $$T_{mn}=\sum_{r,s}{\frac{\partial x^r}{\partial y^m}\frac{\partial x^s}{\partial y^n}T_{mn}’}$$

Now we need to discuss some Pythagoras theorem:

Usually we write it as $ds^2=\sum_n{dx^ndx^n}$ but here by introducing Kronecker delta $\delta_{mn}$ we can write it as $ds^2=\delta_{mn}\sum_{m,n}{dx^m dx^n}$, where 
$$
\begin{equation}
\delta_{mn}=\\\{
\begin{array}{l}
1\cdots m=n\\\\
0\cdots m\neq n
\end{array}\nonumber
\end{equation}
$$


> This can also be written in the matrix form, for e.g. in 3-D:
> $$
> \left\langle\begin{bmatrix}
> 1&0&0\\\\
> 0&1&0\\\\
> 0&0&1\\\\
> \end{bmatrix},(\begin{bmatrix}
> dx^1\\\\
> dx^2\\\\
> dx^3
> \end{bmatrix}\otimes\begin{bmatrix}
> dx^1&dx^2&dx^3
> \end{bmatrix})\right\rangle_F={dx^1}^2+{dx^2}^2+{dx^3}^2
> $$
> the main point is $\delta_{mn}$ is a diagonal matrix.

Rewrite \eqref{eq:1} as $dx^m=\frac{\partial x^m}{\partial y^r}dy^r$(getting rid of the summation terms i.e. $\sum$ mark from now on) and substituting it into new Pythagoras we get:
$$
\begin{align}
ds^2&=\delta_{mn}\frac{\partial x^m}{\partial y^r}dy^r\frac{\partial x^n}{\partial y^s}dy^s\nonumber\\\\
&=\boxed{\delta_{mn}\frac{\partial x^m}{\partial y^r}\frac{\partial x^n}{\partial y^s}}dy^rdy^s\nonumber\\\\
&=g_{mn}dy^rdy^s
\label{eq:6}
\end{align}
$$
Here comes metric tensor $g_{mn}$ (the boxed part in above equation)!

# Christoffel Symbol $\Gamma$

Now to discuss the relations between derivatives for two tensors ($W_{mn}(x)=V_{mn}(x)$)
$$
\begin{align}
T_{mn}(y)&=\frac{\partial x^r}{\partial y^m}\frac{\partial x^s}{\partial y^n}T_{rs}(x)\nonumber\\\\
&=\frac{\partial x^r}{\partial y^m}\frac{\partial x^s}{\partial y^n}\frac{\partial V_r(x)}{\partial x^s}\nonumber\\\\
&=\frac{\partial x^r}{\partial y^m}\frac{\partial V_r{x}}{\partial y^n}\nonumber
\end{align}
$$

$$
\begin{align}
\frac{\partial V_m(y)}{\partial y^n}&=\frac{\partial }{\partial y^n}(\frac{\partial x^r}{y^m}V_r(x))\nonumber\\\\
&=\frac{\partial x^r}{\partial y^m}\frac{\partial V_r(x)}{\partial y^n}+\boxed{\frac {\partial }{\partial y^n}\frac{\partial x^r}{\partial y^m}}V_r(x)\nonumber\\\\
&=\frac{\partial x^r}{\partial y^m}\frac{\partial V_r(x)}{\partial y^n}+\Gamma_{mn}^rV_r(x)=\nabla_nV_m
\end{align}
$$


# Curvature

........................................................

........................................................

## Ricci Tensor

........................................................

........................................................

## Curvature Scalar

........................................................

........................................................

# Stress Energy Momentum Tensor

........................................................

........................................................

# Cosmological Constant

........................................................

........................................................

# Summary

........................................................

........................................................

