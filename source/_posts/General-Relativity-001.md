---
title: General Relativity Problem Set 1 Special Relativity
author: Jun Hu
date: 2019-08-27 11:58:00
tags:
 - special relativity
 - general relativity

---

Problem Set 1: Special Relativity
Reading: Chapter 1 of Carroll

<!-- more -->

---



# Problem 1


Particle physicists are so used to setting c = 1 that they measure mass in units of energy. In particular, they tend to use electron volts ( 1eV = $1.6\times10^{-12}$  erg = $1.8\times10^{-33}$ g), or, more commonly, keV, MeV, and GeV ($10^3$ eV, $10^6$ eV, and $10^9$ eV, respectively). The muon has been measured to have a mass of 0.106 GeV and a rest frame lifetime of $2.19\times10^{-6}$ seconds. Imagine that such a muon is moving in the circular storage ring of a particle accelerator, 1 kilometer in diameter, such that the muon's total energy is 1000 GeV. How long would it appear to live from the experimenter's point of view? How many radians would it travel around the ring? (from - Chapter 1, Problem 5 of Carroll-)

---
# Answer 1

Lorentz factor: $\gamma=1/\sqrt{1-v^2/c^2}$ and $m=m_0\gamma$, $\Delta t'=\Delta t\gamma$
thus $\gamma=m/m_0=9433$
the muon's life from the experimenter's point of view:
$\Delta t=\Delta t'/\gamma=0.02066s$
also the muon's velocity is:
$v=\sqrt{(c^2(1-1/\gamma^2)}=299999998m/s$
$R=(\Delta t \times v)/r=986.44\pi‬\approx 493  circles$

---

# Problem 2


Consider Minkowski space in the usual Cartesian coordinates
$$ds^2= \eta_{\mu\nu}dx^\mu dx^\nu =-dt^2+dx^2+dy^2+dz^2$$
in these coordinates, where $dx^\mu$ is an infinitesimal displacement of the coordinate $x^{\mu'}$. Consider a new coordinate system $x^\mu$ which differs from these Cartesian coordinates; here $\mu'$ is an index which runs from 0 to 3. The Cartesian coordinates $x^\mu$ can be written as a function of these new coordinates $x^\mu=x^\mu(x^{\mu'})$.

(a) Take a point $x^{\mu'}$ in this new coordinate system, and imagine displacing it by an infinitesimal amount to $x^{\mu'}+dx^{\mu'}$. We want to understand how the $x^{\mu'}$ coordinates change to first order in this displacement $x^{\mu'}$. Argue that $$dx^\mu =\frac{\partial x^\mu}{\partial x^{\mu'}}dx^{\mu'}$$
*(Hint: Taylor expand $x^\mu (x^{\mu'}+dx^{\mu'})$)*

(b) The sixteen quantities $\frac{\partial x^\mu}{\partial x^{\mu'}}$are referred to as the Jacobian matrix; we will require this matrix to be invertible. Show that the inverse of this matrix is $\frac{\partial x^{\mu'}}{\partial x^\mu}$.
*(Hint: Use the chain rule)*

(c) Consider spherical coordinates, $x^{\mu'}=(t,r,\theta ,\varphi )$ which are related to the Cartesian coordinates by $$(t,x,y,z)=(t,rsin\theta  cos\varphi , rsin\theta  sin\varphi , rcos\theta )$$Compute the matrix $\frac{\partial x^\mu}{\partial x^{\mu'}}$. Is this matrix invertible everywhere? Compute the displacements $dx^\mu$ in this coordinates system (i.e. write them as functions of $x^{\mu'}$ and the infinitesimal displacements $dx^{\mu'}$).

(d) Compute the line element $ds^2$ in this coordinate system.

---
# Answer 2

(a') $dx^\mu=x^\mu(x^{\mu'}+dx^{\mu'})-x^\mu(x^{\mu'})$
By Taylor expansion $f(x+dx)\approx f(x)+f'(x)dx$
we get $x^\mu(x^{\mu'}+dx^{\mu'})-x^\mu(x^{\mu'})=\frac{\partial x^\mu(x^{\mu'})}{\partial x^{\mu'}}dx^{\mu'}$, when $dx\rightarrow0$
Thus we have $dx^\mu=\frac{\partial x^\mu}{\partial x^{\mu'}}dx^{\mu'}$


(b') Using chain rule $\frac{\partial x^{\mu'}}{\partial x^\mu}\frac{\partial x^\mu}{\partial x^{\mu'}}=1$

(C') In Matlab
```matlab
syms t r th ph;
t=t;
x=r*sin(th)*cos(ph);
y=r*sin(th)*sin(ph);
z=r*cos(th);
J=jacobian([t;x;y;z],[t r th ph])
```
$\frac{\partial x^\mu}{\partial x^{\mu'}}=\begin{bmatrix}1&0&0&0\\\0&\cos\mathrm\varphi \\sin\mathrm\theta &r\\cos\mathrm\varphi \\cos\mathrm\theta &-r\\sin\mathrm\varphi \\sin\mathrm\theta \\\0&\sin\mathrm\varphi \\sin\mathrm\theta &r\\cos\mathrm\theta \\sin\mathrm\varphi &r\\cos\mathrm\varphi \\sin\mathrm\theta \\\0&\cos\mathrm\theta &-r\\sin\mathrm\theta &0\end{bmatrix}$
When r=0, the Jacobian matrix $\frac{\partial x^\mu}{\partial x^{\mu'}}=0$, thus this matrix is non-invertible or singular at r=0.
From $dx^\mu =\frac{\partial x^\mu}{\partial x^{\mu'}}dx^{\mu'}$ and above, we have
$\begin{array}{l}dt^2=dt'^2\\\dx^2=\lbrack cos\varphi sin\theta +sin\varphi sin\theta +cos\theta \rbrack dx'^2=dx'^2\\\dy^2=\lbrack rcos\varphi cos\theta +rcos\theta sin\varphi -rsin\theta \rbrack dy'^2=r(cos\theta -sin\theta )dy'^2\\\dz^2=\lbrack-rsin\varphi sin\theta +rcos\varphi sin\theta \rbrack dz'^2=rsin\theta (cos\varphi -sin\varphi )dz'^2\end{array}$

From above 
$ds^2=dt'^2+dx'^2+r(cos\theta -sin\theta )dy'^2+rsin\theta (cos\varphi -sin\varphi )dz'^2$

---

# Problem 3


Consider a particle moving through Minkowski space with worldline $x^\mu(\lambda)$. Here $\lambda$ is a continuous parameter which labels different points on the worldline and $x^\mu=(t,x,y,z)$ denotes the usual Cartesian coordinates. We will denote $\frac{\partial}{\partial\lambda}$ by a dot. In this problem we will assume that the trajectory of the particle obeys the equation of motion $\ddot x ^\mu=0$.

(a) Show that this trajectory describes a particle moving at constant velocity.

(b) Show that this trajectory is a local extremum of the action
$$S=\int ds=\int d\lambda \sqrt{\eta_{\mu \nu}\dot x^\mu \dot x^\nu}$$
which measures the invariant interval of a wordline.

(c) Consider a new coordinate system $x^{\mu'}$ which differs from the original Cartesian coordinate system; as before, the Cartesian coordinates $x^\mu$ can be written as a function of these new coordinates $x^\mu=x^\mu(x^{\mu'})$. Show that the equation of motion can be written in these new $x^{\mu'}$ coordinate as

$$
\begin{equation}
\ddot x^{\mu'}+\Gamma^{\mu'}_{\nu'\lambda'}\dot x^{\mu'}\dot x^{\lambda'}=0
\end{equation}
$$

for some $\Gamma_{\nu'\lambda'}^{\mu'}$ which you must compute; $\Gamma^{\mu'}_{\nu'\lambda'}$ is known as the Christoffel symbol. These extra Christoffel terms in the equation of motion can be thought of as "fictitious forces" that arise in an accelerated reference frame.

(d) Consider the case where the $x^{\mu'}=(t',x',y',z')$ describe a coordinates system which is rotating around the z axis with constant angular velocity $\omega$.This is related to the original cartesian coordinates by $$(t,x,y,z)=(t',x'cos\omega t'+y'sin\omega t',-x'sin\omega t'+y'cos\omega t',z')$$Compute the line element $ds^2$ in this new coordinate system.

(e) Compute $\Gamma^{\mu'}_{\nu'\lambda'}$ in this coordinate system. These terms describe the usual Centrifugal and Coriolis forces that arise in a rotating coordinate system. *(Himt: Rather than using the explicit formula you derived in part (c), you may find it easier to just compute $\ddot x^{\mu'}$ for a particle moving at constant velocity. The Christoffel symbols can then be determined using formula (1))*

---
# Answer 3

(a') Let $u^\mu, a^\mu$ be the particle's velocity and acceleration, respectively, thus we have
$$
\begin{equation}
a^\mu=\frac{\partial u^\mu}{\partial t}
\end{equation}
$$
Also according to Chain Rule we have
$$
\begin{align}
u^\mu&=\frac{\partial x^\mu}{\partial t}\\\\\nonumber
&=\frac{\partial x^\mu}{\partial \lambda}\frac{\partial \lambda}{\partial t}\\\\\nonumber
&=\dot x^\mu\frac{\partial t}{\partial\lambda}
\end{align}
$$
Substitute 3 into 2,
$$
\begin{align}
a^\mu&=\frac{\partial (\dot x^\mu\frac{\partial t}{\partial\lambda})}{\partial t}\\\\\nonumber
&=\frac{\partial \dot x^\mu\}{\partial t}\frac{\partial t}{\partial \lambda}+\frac{\partial(\frac{\partial t}{\partial \lambda})}{\partial t}\dot x^\mu\\\\\nonumber
&=\ddot x^\mu=0\nonumber
\end{align}
$$
Particle is moving with the acceleration of 0 thus at constant velocity.

(b') $\dot s=\sqrt{\eta_{\mu \nu}\dot x^\mu \dot x^\nu}$
thus $\ddot s=\sqrt{\eta_{\mu \nu}\ddot x^\mu \ddot x^\nu}=0$, when $\ddot x^\mu=0$ 

## TBC
---


Reference:

*- Chapter 1, Problem 5 of Carroll*

*-[Lecture Notes, recordings and problem sets](http://www.physics.mcgill.ca/~maloney/514/)*

---
