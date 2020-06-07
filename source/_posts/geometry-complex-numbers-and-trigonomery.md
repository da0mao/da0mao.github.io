---
title: Geometry complex numbers and trigonometry
author: Jun Hu
tags:
  - trigonometry
  - complex number
date: 2020-05-13 22:21:30
---

Being tired of memorizing these formulas? See how a unit circle and the complex numbers can help.
$\begin{array}{1}\sin(\alpha+\beta)=\sin\alpha\cos\beta+\cos\alpha\sin\beta\\\cos(\alpha+\beta)=\cos\alpha\cos\beta-\sin\alpha\sin\beta\end{array}$

<!-- more -->

{%cq%}Trigonometry - you think it is about triangles, but really it is about circles.{%endcq%}

Consider a unit circle (whose radius is 1), the coordinator of a point (z) on the circle can be written as $(\cos\theta,\sin\theta)$, where $\theta$ is the angle the line of oz rotates from x axis clockwise, so to rotate another angle $\phi$, we will have $(\cos(\theta+\phi),\sin(\theta+\phi)$.

![Trigonometry](/images/Trigonometry1.jpg)

Now, instead of y axis, think of it as an axis with unit of $i$, where $i=\sqrt{-1}$.

Then the coordinator can be written as $(\cos(\theta+\phi),i\sin(\theta+\phi)$, which is actually the result two rotation.

Thus we have:

$(\cos(\theta+\phi),i\sin(\theta+\phi)=(\cos\theta,i\sin\theta)(\cos\phi,i\sin\phi)$

then it is not hard to derive that:

$\cos(\theta+\phi)=(\cos\theta\cos\phi+i^2\sin\theta\sin\phi)$

and

$i\sin(\theta+\phi)=i(\cos\theta\sin\phi-\sin\theta\cos\phi)$

For example, $\cos75^o=\cos(45^o+30^o)$:

Consider it geometrically, is the x axis rotates from $0^o$ first $45^o$ then another $30^o$.

Thus we can easily write

$\cos75^o+i\sin75^o=(\cos45^o+i\sin45^o)(\cos30^o+i\sin30^o)$,

where the real part

$\cos45^o\cos30^o-\sin45^o\sin30^o$ is $cos75^o$,

and the imaginary part (without i)

$cos45^o\sin30^o+\sin45^o\cos30^o$ is $\sin75^o$.

> These are just notes I took from the amazing videos from 3Blue1Brown. I highly suggest everyone who's interested in details watch it. The link is down below.

---


Reference:

*- [YouTube: Complex number fundamentals | Lockdown math ep. 3](https://youtu.be/5PcpBw5Hbwo)*

