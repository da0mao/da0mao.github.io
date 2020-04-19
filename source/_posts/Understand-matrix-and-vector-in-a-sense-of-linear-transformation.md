---
title: Understand Matrix and Vector in a sense of linear transformation
author: Jun Hu
date: 2019-08-04 19:38:00
tags:
 - Matrix
 - Vector
 - Linear Algebra
---

There is hardly any theory which is more elementary than linear algebra, in spite of the fact that generations of professors and textbook writers have obscured its simplicity by preposterous calculations with matrices.
-Jean Dieudonné

<!-- more -->

Matrix is a way of transforming a vector to another in a certain way. (AKA. "Linear transformation")

> "Transformation" is essentially a fancy word for "function". It's something that takes in inputs and spits out an output for each one. It's to be suggestive of a certain way to visualize this input-out relation.

Say there is a vector $[1,0,0,0]$ and you'd like to move the "1" from the 1st position to the 2nd so that you get $[0,1,0,0]$.

To archive that, one can simply multiply a matrix with this vector:

$\begin{bmatrix}1&0&0&0\end{bmatrix}\begin{bmatrix}0&1&0&0\\\0&0&1&0\\\0&0&0&1\\\1&0&0&0\end{bmatrix}=\begin{bmatrix}0&1&0&0\end{bmatrix}\dots\dots\dots(1)$

What's more interesting is if you continue to multiply this matrix with the new vector, the "1" keeps moving to the 3rd place:

$\begin{bmatrix}0&1&0&0\end{bmatrix}\begin{bmatrix}0&1&0&0\\\0&0&1&0\\\0&0&0&1\\\1&0&0&0\end{bmatrix}=\begin{bmatrix}0&0&1&0\end{bmatrix}$

In fact this matrix can keep moving this "1" from one place to the right next and then, if it's the last, back to the top.

$\begin{bmatrix}0&0&0&1\end{bmatrix}\begin{bmatrix}0&1&0&0\\\0&0&1&0\\\0&0&0&1\\\1&0&0&0\end{bmatrix}=\begin{bmatrix}1&0&0&0\end{bmatrix}$

Then, instead of thinking the vector changes, think of the changes of the coordinate system while the vector itself remains unchanged. In which way, what the matrix did in (1) is changing the coordinator system from where the vector points along with x axis with one unit of length to where it points along with y axis. (If the vector and the matrix is only 2D then the coordinator system is simply rotating $90^o$ clockwise).

---
