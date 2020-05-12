---
title: Another View on the Quadratic Formula
author: Jun Hu
tags:
  - Quadratic Formula
date: 2020-05-12 20:32:42
---

Being tired of ${\displaystyle x={\frac {-b\pm {\sqrt {b^{2}-4ac}}}{2a}}\ \ }$?



<!-- more -->

Consider $ax^2+bx+c=0$, and to normalize the equation, provided that $b'=b/a$ and $c'=c/a$, then we have $x^2+b'x+c'=0$.

Suppose we have r and s, such that  $x^2+b'x+c'=(x-r)(x-s)=0$, then it is easy to see that: $b'=-(r+s)$ and $c'=rs$.

Now, think of the middle point m and the deviation d, where $r=m-d$ and $s=m+d$, as show in below snapshot:

![Quadratic](/images/Quadratic2.jpg)

Then we can re-write $b'$ and $c'$ as $b'=-2m$ and $c'=(m+d)(m-d)=m^2-d^2$, thus, $m=-b'/2$ and $d^2=m^2-c'$.

Meanwhile, the roots can be re-written as $x=m \pm d$, where $m=-b'/2$ and $d=\sqrt{m^2-c'}$.

For example, if $x^2-21x+110=0$, from above we have $m=10.5$ and $d=\sqrt{10.5^2-110}=0.5$, so the roots are $x=10.5\pm 0.5$, i.e. 10 and 11.

---


Reference:

*- [YouTube: The simpler quadratic formula | Lockdown math ep. 1](https://youtu.be/MHXO86wKeDY)*

