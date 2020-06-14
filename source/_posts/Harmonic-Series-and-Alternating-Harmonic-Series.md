title: Harmonic Series and Alternating Harmonic Series

author: Jun Hu

tags:

  - Nature Logarithm
  - Infinite Series

date: 2020-06-14 10:18:00

---

The harmonic series,
$$
1+\frac1{2}+\frac1{3}+\frac1{4}+\frac1{5}+\dots =\sum_{n=1}^\infty\frac1{n}=?
$$
<!-- more -->

Let’s assume that we know $ln’(x)=\frac{d}{dx}ln(x)=\frac1{x}$

![Infinite Series 1](/images/infiniteseries1.jpg)

Then from above we can see that

$$
\sum_{n=0}^\infty >\int_{n=0}^{n=\infty}\frac1{x}dx=ln(n)=\infty
$$

So the harmonic series is a divergent series.
In fact, the difference between these two infinite number is a constant (called Euler–Mascheroni constant $\gamma$)

$$
\sum_{n=0}^\infty =ln(n)+\gamma
$$

But the alternating harmonic series is different,

$$
1-\frac1{2}+\frac1{3}-\frac1{4}+\frac1{5}-\dots =-\sum_{n=1}^\infty\frac{(-1)^n}{n}=?
$$

There’s a rather counterintuitive way of calculating it.

$$
1-\frac1{2}+\frac1{3}-\frac1{4}+\frac1{5}-\dots
$$

To generalize the series,

$$
\hookrightarrow x-\frac{x^2}{2}+\frac{x^3}{3}-\frac{x^4}{4}+\frac{x^5}{5}-\dots
$$

And then take the derivates of it,

$$
\begin{align}
\hookrightarrow &\frac{d}{dx}(x-\frac{x^2}{2}+\frac{x^3}{3}-\frac{x^4}{4}+\frac{x^5}{5}-\dots)\nonumber\\\\
&=1-x+x^2-x^3+x^4-\dots\nonumber\\\\
&=\frac1{1+x}\nonumber
\end{align}
$$

And then, to integrate it back, and to specialize it to the series we are interested in,

$$
\begin{align}
&1-\frac1{2}+\frac1{3}-\frac1{4}+\frac1{5}-\dots\nonumber\\\\
&=[x-\frac{x^2}{2}+\frac{x^3}{3}-\frac{x^4}{4}+\frac{x^5}{5}-\dots]_0^1\nonumber\\\\
&=\int_0^1\frac1{1+x}dx\nonumber\\\\
&=ln(1+x)|_0^1\nonumber\nonumber\\\\
&=ln(2)\nonumber
\end{align}
$$

---


Reference:


*- [YouTube: What makes the natural log "natural"? | Lockdown math ep. 7](https://youtu.be/4PDoT7jtxmw)*
