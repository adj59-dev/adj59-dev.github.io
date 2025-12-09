---
title: "Nielsen and Chuang: Chapter 4"
description: "Notes and exercise solutions for QCQI Chapter 4: quantum algorithms, single qubit operations, controlled operations, measurement, and simulation of quantum systems."
categories:
  - Quantum Computation and Quantum Information
permalink: /qcqi/chapter-4/
toc: true
tags:
  - QCQI
  - quantum computing
  - Quantum Computation and Quantum Information
  - Nielsen & Chuang
  - chapter 4
  - exercise
  - problem
  - solutions
last_modified_at: 2025-12-07 12:00:00 -08:00
exercises:
  - anchor: exercise-41
    label: Exercise 4.1
  - anchor: exercise-42
    label: Exercise 4.2
  - anchor: exercise-43
    label: Exercise 4.3
  - anchor: exercise-44
    label: Exercise 4.4
  - anchor: exercise-45
    label: Exercise 4.5
  - anchor: exercise-46
    label: Exercise 4.6
  - anchor: exercise-47
    label: Exercise 4.7
  - anchor: exercise-48
    label: Exercise 4.8
  - anchor: exercise-49
    label: Exercise 4.9
  - anchor: exercise-410
    label: Exercise 4.10
  - anchor: exercise-411
    label: Exercise 4.11
  - anchor: exercise-412
    label: Exercise 4.12
  - anchor: exercise-413
    label: Exercise 4.13
  - anchor: exercise-414
    label: Exercise 4.14
  - anchor: exercise-415
    label: Exercise 4.15
  - anchor: exercise-416
    label: Exercise 4.16
  - anchor: exercise-417
    label: Exercise 4.17
  - anchor: exercise-418
    label: Exercise 4.18
  - anchor: exercise-419
    label: Exercise 4.19
  - anchor: exercise-420
    label: Exercise 4.20
  - anchor: exercise-421
    label: Exercise 4.21
  - anchor: exercise-422
    label: Exercise 4.22
  - anchor: exercise-423
    label: Exercise 4.23
  - anchor: exercise-424
    label: Exercise 4.24
  - anchor: exercise-425
    label: Exercise 4.25
  - anchor: exercise-426
    label: Exercise 4.26
  - anchor: exercise-427
    label: Exercise 4.27
  - anchor: exercise-428
    label: Exercise 4.28
  - anchor: exercise-429
    label: Exercise 4.29 & 4.30
  - anchor: exercise-431
    label: Exercise 4.31
  - anchor: exercise-432
    label: Exercise 4.32
  - anchor: exercise-433
    label: Exercise 4.33
  - anchor: exercise-434
    label: Exercise 4.34
  - anchor: exercise-435
    label: Exercise 4.35
  - anchor: exercise-436
    label: Exercise 4.36
  - anchor: exercise-437
    label: Exercise 4.37
  - anchor: exercise-438
    label: Exercise 4.38
  - anchor: exercise-439
    label: Exercise 4.39
  - anchor: exercise-440
    label: Exercise 4.40
  - anchor: exercise-441
    label: Exercise 4.41
  - anchor: exercise-442
    label: Exercise 4.42
  - anchor: exercise-443
    label: Exercise 4.43
  - anchor: exercise-444
    label: Exercise 4.44
  - anchor: exercise-445
    label: Exercise 4.45
  - anchor: exercise-446
    label: Exercise 4.46
  - anchor: exercise-447
    label: Exercise 4.47
  - anchor: exercise-448
    label: Exercise 4.48
  - anchor: exercise-449
    label: Exercise 4.49
  - anchor: exercise-450
    label: Exercise 4.50
  - anchor: exercise-451
    label: Exercise 4.51
  - anchor: problem-41
    label: Problem 4.1
  - anchor: problem-42
    label: Problem 4.2
  - anchor: problem-43
    label: Problem 4.3
  - anchor: problem-44
    label: Problem 4.4
  - anchor: problem-45
    label: Problem 4.5
  - anchor: problem-46
    label: Problem 4.6
chapter: 4
---

<a id="top"></a>



I just finished reading Chapter 4 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. This is the first chapter in Part II, which focuses on quantum computation. Chapter 4 introduces quantum circuits as the fundamental model of quantum computation and shows that there exists a universal set of gates capable of approximating any quantum operation.

As with the earlier chapters, I’ve included my notes and exercise solutions below. 


<!-- toc -->





## Single qubit operations

### Rotation Operator Decomposition

For several exercises in this section, I perform decomposition on the rotation operators $R_x$, $R_y$ and $R_z$ where I write one of these operators in terms of the other ones. I wanted to take a moment here to prove that this is valid and to confirm the signs of the rotations and their ordering; since they do not commute it is important to get their order correct. 





We can write $R_x$ in terms of $R_y$ and $R_z$ as follows

$$\begin{aligned}
R_x(\theta) &= R_z(-\pi/2)R_y(\theta)R_z(\pi/2) \\
&= \left(\cos\frac{-\pi}{4}I - i\sin\frac{-\pi}{4}Z\right)\left(\cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Y\right)\left(\cos\frac{\pi}{4}I - i\sin\frac{\pi}{4}Z\right) \\
&= \left(\frac{1}{\sqrt{2}}I + i\frac{1}{\sqrt{2}}Z\right)\left(\cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Y\right)\left(\frac{1}{\sqrt{2}}I - i\frac{1}{\sqrt{2}}Z\right) \\
&= \frac{1}{2}\cos\frac{\theta}{2}I + i\frac{1}{2}\cos\frac{\theta}{2}Z - i\frac{1}{2}\sin\frac{\theta}{2}Y + \frac{1}{2}\sin\frac{\theta}{2}ZY - i\frac{1}{2}\cos\frac{\theta}{2}Z + \frac{1}{2}\cos\frac{\theta}{2}ZZ - \frac{1}{2}\sin\frac{\theta}{2}YZ - i\frac{1}{2}\sin\frac{\theta}{2}ZYZ \\
&= \frac{1}{2}\cos\frac{\theta}{2}(I + ZZ) + i\frac{1}{2}\cos\frac{\theta}{2}(Z-Z) - i\frac{1}{2}\sin\frac{\theta}{2}(Y + ZYZ) + \frac{1}{2}\sin\frac{\theta}{2}(ZY - YZ) \\
&= \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}X & \text{since $ZZ=I$, $ZYZ=-Y$, and $ZY-YZ = -2iX$}\\
\end{aligned}$$

We can write $R_y$ in terms of $R_x$ and $R_z$ as follows

$$\begin{aligned}
R_y(\theta) &= R_x(-\pi/2)R_z(\theta)R_x(\pi/2) \\
&= \left(\cos\frac{-\pi}{4}I - i\sin\frac{-\pi}{4}X\right)\left(\cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Z\right)\left(\cos\frac{\pi}{4}I - i\sin\frac{\pi}{4}X\right) \\
&= \left(\frac{1}{\sqrt{2}}I + i\frac{1}{\sqrt{2}}X\right)\left(\cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Z\right)\left(\frac{1}{\sqrt{2}}I - i\frac{1}{\sqrt{2}}X\right) \\
&= \frac{1}{2}\cos\frac{\theta}{2}I + i\frac{1}{2}\cos\frac{\theta}{2}X - i\frac{1}{2}\sin\frac{\theta}{2}Z + \frac{1}{2}\sin\frac{\theta}{2}XZ - i\frac{1}{2}\cos\frac{\theta}{2}X + \frac{1}{2}\cos\frac{\theta}{2}XX - \frac{1}{2}\sin\frac{\theta}{2}ZX - i\frac{1}{2}\sin\frac{\theta}{2}XZX \\
&= \frac{1}{2}\cos\frac{\theta}{2}(I + XX) + i\frac{1}{2}\cos\frac{\theta}{2}(X-X) - i\frac{1}{2}\sin\frac{\theta}{2}(Z + XZX) + \frac{1}{2}\sin\frac{\theta}{2}(XZ - ZX) \\
&= \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Y & \text{since $XX=I$, $XZX=-Z$, and $XZ-ZX = -2iY$}\\
\end{aligned}$$

We can write $R_z$ in terms of $R_y$ and $R_x$ as follows

$$\begin{aligned}
R_z(\theta) &= R_y(-\pi/2)R_x(\theta)R_y(\pi/2) \\
&= \left(\cos\frac{-\pi}{4}I - i\sin\frac{-\pi}{4}Y\right)\left(\cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}X\right)\left(\cos\frac{\pi}{4}I - i\sin\frac{\pi}{4}Y\right) \\
&= \left(\frac{1}{\sqrt{2}}I + i\frac{1}{\sqrt{2}}Y\right)\left(\cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}X\right)\left(\frac{1}{\sqrt{2}}I - i\frac{1}{\sqrt{2}}Y\right) \\
&= \frac{1}{2}\cos\frac{\theta}{2}I + i\frac{1}{2}\cos\frac{\theta}{2}Y - i\frac{1}{2}\sin\frac{\theta}{2}X + \frac{1}{2}\sin\frac{\theta}{2}YX - i\frac{1}{2}\cos\frac{\theta}{2}Y + \frac{1}{2}\cos\frac{\theta}{2}YY - \frac{1}{2}\sin\frac{\theta}{2}XY - i\frac{1}{2}\sin\frac{\theta}{2}YXY \\
&= \frac{1}{2}\cos\frac{\theta}{2}(I + YY) + i\frac{1}{2}\cos\frac{\theta}{2}(Y-Y) - i\frac{1}{2}\sin\frac{\theta}{2}(X + YXY) + \frac{1}{2}\sin\frac{\theta}{2}(YX - XY) \\
&= \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Z & \text{since $YY=I$, $YXY=-Z$, and $YX-XY = -2iZ$}\\
\end{aligned}$$

The following is also true,

$$\begin{aligned}
R_x(\theta) &= R_y(\pi/2)R_z(\theta)R_y(-\pi/2) \\
&= R_y(\pi/2)R_y(-\pi/2)R_x(\theta)R_y(\pi/2)R_y(-\pi/2) &\text{decomposition of $R_z$} \\
&= R_x(\theta)
\end{aligned}$$

The same can be shown for $R_y$ and $R_z$, 

$$\begin{aligned}
R_y(\theta) &= R_z(\pi/2)R_x(\theta)R_z(-\pi/2) \\
&= R_z(\pi/2)R_z(-\pi/2)R_y(\theta)R_z(\pi/2)R_z(-\pi/2) &\text{decomposition of $R_x$} \\
&= R_y(\theta) \\
R_z(\theta) &= R_x(\pi/2)R_y(\theta)R_x(-\pi/2) \\
&= R_z(\pi/2)R_x(-\pi/2)R_x(-\pi/2)R_z(\theta)R_x(\pi/2)R_x(\pi/2)R_z(-\pi/2) &\text{decomposition of $R_y$} \\
&= R_z(\theta)
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


  
### Exercise 4.1 {#exercise-41} 






The eigenvectors for $Z$ are $\ket{0}$ and $\ket{1}$. These correspond to Bloch vectors of $(0, 0, 1)$ and $(0, 0, -1)$.

The eigenvectors for $X$ are $\frac{1}{\sqrt{2}}(\ket{0} + \ket{1})$ and $\frac{1}{\sqrt{2}}(\ket{0} - \ket{1})$. These correspond to Bloch vectors of $(1, 0, 0)$ and $(-1, 0, 0)$.

The eigenvectors for $Y$ are $\frac{1}{\sqrt{2}}(\ket{0} + i\ket{1})$ and $\frac{1}{\sqrt{2}}(\ket{0} - i\ket{1})$. These correspond to Bloch vectors of $(0, 1, 0)$ and $(0, -1, 0)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 4.2 {#exercise-42}






First we show that $\exp(iAx)=\cos(x)I+i\sin(x)A$

$$\begin{align}
\exp(iAx) &= \cos(Ax) + i\sin(Ax) & \text{Euler's formula} \\
&= \sum_{i}\cos(x\lambda_i)\ket{i}\bra{i} + \sum_j i\sin(x\lambda_j)\ket{j}\bra{j} & \text{spectral decomposition and applying functions}\\
&= \cos(x)\ket{+1}\bra{+1} + \cos(-x)\ket{-1}\bra{-1} + i\sin(x)\ket{+1}\bra{+1} + i\sin(-x)\ket{-1}\bra{-1} & \text{since $A^2=I$ its eigenvalues must be $\pm 1$ with eigenvectors $\ket{\pm 1}$}\\
&= \cos(x)\ket{+1}\bra{+1} + \cos(x)\ket{-1}\bra{-1} + i\sin(x)\ket{+1}\bra{+1} - i\sin(x)\ket{-1}\bra{-1} \\
&= \cos(x)(\ket{+1}\bra{+1} + \ket{-1}\bra{-1}) + i\sin(x)(\ket{+1}\bra{+1} - \ket{-1}\bra{-1}) \\
&= \cos(x) I + i\sin(x) A
\end{align}$$

Now we use the result to verify equations 4.4 - 4.6. From [exercise 2.19](https://adj59-dev.github.io/qcqi/chapter-2/#exercise-219) we know that the Pauli matrices are Hermitian and unitary (i.e. $A^2=I$), therefore we can directly use the result above to generate equations 4.4-4.6 by replacing $A$ with $X$, $Y$, or $Z$. 

$$\begin{aligned}
R_x(\theta) & = e^{-i\theta X/2} = \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}X = \cos\frac{\theta}{2}\begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} - i\sin\frac{\theta}{2}\begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} = \begin{bmatrix} \cos\frac{\theta}{2} & -i\sin\frac{\theta}{2} \\\ -i\sin\frac{\theta}{2} & \cos\frac{\theta}{2} \end{bmatrix} \\
R_y(\theta) &= e^{-i\theta Y/2} = \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Y = \cos\frac{\theta}{2}\begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} - i\sin\frac{\theta}{2}\begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} = \begin{bmatrix} \cos\frac{\theta}{2} & -\sin\frac{\theta}{2} \\\ \sin\frac{\theta}{2} & \cos\frac{\theta}{2} \end{bmatrix} \\
R_z(\theta) &= e^{-i\theta Z/2} = \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Z = \cos\frac{\theta}{2}\begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} - i\sin\frac{\theta}{2}\begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} = \begin{bmatrix} e^{-i\theta/2} & 0 \\\ 0 & e^{i\theta/2} \end{bmatrix}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.3 {#exercise-43}






Let's first calculate $R_z(\pi/4)$

$$\begin{aligned}
R_z(\pi/4) &= \begin{bmatrix} e^{-i(\pi/4)/2} & 0 \\\ 0 & e^{i(\pi/4)/2} \end{bmatrix} \\
&= \begin{bmatrix} e^{-i\pi/8} & 0 \\\ 0 & e^{i\pi/8} \end{bmatrix} \\
&= e^{-i\pi/8}\left(e^{i\pi/8}\begin{bmatrix} e^{-i\pi/8} & 0 \\\ 0 & e^{i\pi/8} \end{bmatrix} \right) \\
&= e^{-i\pi/8} T & \text{per equation 4.3}
\end{aligned}$$

Therefore,  up to a global phase $e^{-i\pi/8}$, the $\pi/8$ gate satisfies $T=R_z(\pi/4)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.4 {#exercise-44}

I'm not sure how we are supposed to complete this exercise without either knowing the answer to begin with or using some of the techniques that will be covered later in this section. I was able to use the description of the Hadamard gate in section 1.3.1 (where we're told that $H$ is a rotation on the Bloch sphere about the y axis by $90^{\circ}$ and then a rotation about the x axis by $180^{\circ}$ ) and the rotation operators to express $H$ in terms of $R_x$ and $R_y$, but I needed to use decomposition techniques discussed later to write $R_y$ as a product of $R_x$ and $R_z$.




Let's first think about what $H$ does. In section 1.3.1 we're told that $H$ is a rotation on the Bloch sphere about the y axis by $90^{\circ}$ and then a rotation about the x axis by $180^{\circ}$. Therefore,

$$\begin{aligned}
H &= R_x(\pi)R_y(\pi/2)e^{i\phi} \\
&= (\cos\frac{\pi}{2}I - i\sin\frac{\pi}{2}X)(\cos\frac{\pi}{4}I - i\sin\frac{\pi}{4}Y)e^{i\phi} \\
&= \frac{-ie^{i\phi}}{\sqrt{2}}XI - \frac{e^{i\phi}}{\sqrt{2}}XY \\
&= \frac{-ie^{i\phi}}{\sqrt{2}}X - \frac{e^{i\phi}}{\sqrt{2}}(iZ) & \text{per equation 2.78}\\
&= \frac{-ie^{i\phi}}{\sqrt{2}}(X + Z) \\
&= -ie^{i\phi} H & \text{since $H=(X+Z)/\sqrt{2}$}
\end{aligned}$$

Therefore, $e^{i\phi} = i$, so $\phi=\pi/2$ and we get $H=R_x(\pi)R_y(\pi/2)e^{i\pi/2}$. Unfortunately, we were not asked to write $H$ in terms of $R_x$ and $R_y$, we were asked to write it in terms of $R_x$ and $R_z$, so now we need to see if we can write $R_y(\pi/2)$ in terms of $R_x$ and $R_z$. I did this by doing a decomposition of $R_y$ to express it in terms of $R_x$ and $R_z$ and then did some additional steps to put the results in a similar form as equation 4.13.

$$\begin{aligned}
R_x(\pi)R_y(\pi/2) &= R_x(\pi)R_z(\pi/2)R_x(\pi/2)R_z(-\pi/2) & \text{decomposition of $R_y$} \\
&= R_z(-\pi/2)R_x(\pi)R_x(\pi/2)R_z(-\pi/2) & \text{conjugation flips $Z$ under a $\pi$ rotation about $X$, shown below} \\
&= R_z(-\pi/2)R_x(3\pi/2)R_z(-\pi/2) & \text{combinding the rotations about $X$}\\
&= -R_z(-\pi/2)R_x(-\pi/2)R_z(-\pi/2) & \text{$3\pi/2$ rotation is the same as a $-\pi/2$ rotation with a -1 global phase change} \\
&= e^{-i\pi}R_z(-\pi/2)R_x(-\pi/2)R_z(-\pi/2)
\end{aligned}$$

Here I'll show why conjugation flips $Z$ under a $\pi$ rotation about $X$

$$\begin{aligned}
R_x(\pi)R_z(\theta)R_x(\pi)^\dagger &= R_x(\pi)e^{-i\theta Z/2}R_x(\pi)^\dagger \\
&= e^{-i\theta/2(R_x(\pi)ZR_x(\pi)^\dagger)} & \text{since $Ue^A U^\dagger = e^{UAU^\dagger}$} \\
&= e^{-i\theta/2((-iX)Z(iX))} \\
&= e^{-i\theta/2(XZX)} \\
&= e^{-i\theta/2(-Z)} \\
&= e^{i\theta/2Z} \\
&= R_z(-\theta) \\
R_x(\pi)R_z(\theta) &= R_z(-\theta)R_x(\pi) & \text{multiply both sides by $R_x(\pi)$ on the right}
\end{aligned}$$

Therefore, 

$$\begin{aligned}
H &= e^{-i\pi/2}R_z(-\pi/2)R_x(-\pi/2)R_z(-\pi/2)\\
&= e^{i\pi/2}R_z(\pi/2)R_x(\pi/2)R_z(\pi/2)
\end{aligned}$$

Which will be shown below

$$\begin{aligned}
e^{i\pi/2}R_z(\pi/2)R_x(\pi/2)R_z(\pi/2) &= e^{i\pi/2}\begin{bmatrix} e^{-i\pi/4} & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \begin{bmatrix} \cos\frac{\pi}{4} & -i\sin\frac{\pi}{4} \\\ -i\sin\frac{\pi}{4} & \cos\frac{\pi}{4} \end{bmatrix}  \begin{bmatrix} e^{-i\pi/4} & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \\
&= e^{i\pi/2}\begin{bmatrix} e^{-i\pi/4} & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \begin{bmatrix} \frac{1}{\sqrt{2}} & -i\frac{1}{\sqrt{2}} \\\ -i\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \end{bmatrix} \ \begin{bmatrix} e^{-i\pi/4} & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \\
&= e^{i\pi/2}\begin{bmatrix} e^{-i\pi/4}\frac{1}{\sqrt{2}} & -ie^{-i\pi/4}\frac{1}{\sqrt{2}} \\\ -ie^{i\pi/4}\frac{1}{\sqrt{2}} & e^{i\pi/4}\frac{1}{\sqrt{2}} \end{bmatrix} \begin{bmatrix} e^{-i\pi/4} & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \\
&= e^{i\pi/2}\begin{bmatrix} e^{-i\pi/2}\frac{1}{\sqrt{2}} & -i\frac{1}{\sqrt{2}} \\\ -i\frac{1}{\sqrt{2}} & e^{i\pi/2}\frac{1}{\sqrt{2}} \end{bmatrix} \\
&= \frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \\
&= H
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.5 {#exercise-45}

 




First let's calculate $\hat{n}\cdot \vec{\sigma}$, where $\vec{\sigma}$ are the Pauli matrices. 

$$\begin{aligned}
\hat{n}\cdot \vec{\sigma} & = n_x \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} + n_y \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} + n_z \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \\
&= \begin{bmatrix} n_z & n_x - i n_y \\\ n_x + i n_y & -n_z \end{bmatrix}
\end{aligned}$$

Now let's calculate $(\hat{n}\cdot \vec{\sigma})^2$

$$\begin{aligned}
(\hat{n}\cdot \vec{\sigma})^2 &= \begin{bmatrix} n_z & n_x - i n_y \\\ n_x + i n_y & -n_z \end{bmatrix} \begin{bmatrix} n_z & n_x - i n_y \\\ n_x + i n_y & -n_z \end{bmatrix} \\
&= \begin{bmatrix} n_z^2 +(n_x-in_y)(n_x+in_y) & (n_x - i n_y)n_z -n_z(n_x-in_y) \\\ (n_x+in_y)n_z -n_z(n_x+in_y) & (n_x+in_y)(n_x-in_y)+n_z^2 \end{bmatrix} \\
&= \begin{bmatrix} n_z^2 + n_y^2 + n_x^2 & 0 \\\ 0 & n_x^2 + n_y^2+n_z^2 \end{bmatrix} \\
&= \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \\
&= I
\end{aligned}$$

Since $(\hat{n}\cdot \vec{\sigma})^2 = I$, we can plug it into equation 4.7 to get

$$\begin{aligned}
\exp(i\hat{n}\cdot \vec{\sigma}x) &= \cos(x)I + i\sin(x)(\hat{n}\cdot \vec{\sigma}) \\
\exp(-i\theta\hat{n}\cdot \vec{\sigma}/2) &= \cos(-\theta/2)I + i\sin(-\theta/2)(\hat{n}\cdot \vec{\sigma}) &\text{let $x=-\theta/2$} \\
&=\cos(\theta/2)I - i\sin(\theta/2)(\hat{n}\cdot \vec{\sigma}) \\
&=\cos(\theta/2)I - i\sin(\theta/2)(n_xX + n_yY + n_zZ)
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |





### Exercise 4.6 {#exercise-46}






From [exercise 2.72](https://adj59-dev.github.io/qcqi/chapter-2/#exercise-272), we know that we can write the density matrix for a single qubit with Bloch vector $\vec{\lambda}$ as

$$\begin{aligned}
\rho = \frac{I+\vec{\lambda}\cdot\vec{\sigma}}{2}
\end{aligned}$$

The evolution of the density operator upon rotation $R_{\hat{n}}(\theta)$ is given by equation 2.139,

$$\begin{aligned}
\rho & \xrightarrow{R_{\hat{n}}} R_{\hat{n}}(\theta)\rho R_{\hat{n}}(\theta)^\dagger \\
&=(\cos(\theta/2)I -i\sin(\theta/2)\hat{n}\cdot\vec{\sigma})\frac{I+\vec{\lambda}\cdot\vec{\sigma}}{2} (\cos(\theta/2)I + i\sin(\theta/2)\hat{n}\cdot\vec{\sigma}) \\
&=\frac{1}{2}(\cos^2(\theta/2)I + \cos^2(\theta/2)\vec{\lambda}\cdot\vec{\sigma} -i\sin(\theta/2)\cos(\theta/2)\hat{n}\cdot\vec{\sigma} -i\sin(\theta/2)\cos(\theta/2)(\hat{n}\cdot\vec{\sigma})(\vec{\lambda}\cdot\vec{\sigma}) + i\cos(\theta/2)\sin(\theta/2)\hat{n}\cdot\vec{\sigma} + i\cos(\theta/2)\sin(\theta/2)(\vec{\lambda}\cdot\vec{\sigma})(\hat{n}\cdot\vec{\sigma}) + \sin^2(\theta/2)(\hat{n}\cdot\vec{\sigma})(\hat{n}\cdot\vec{\sigma}) + \sin^2(\theta/2)(\hat{n}\cdot\vec{\sigma})(\vec{\lambda}\cdot\vec{\sigma})(\hat{n}\cdot\vec{\sigma})) \\
&=\frac{1}{2}(I + \cos^2(\theta/2)\vec{\lambda}\cdot\vec{\sigma} -i\sin(\theta/2)\cos(\theta/2)((\hat{n} \cdot \vec{\lambda})I + i(\hat{n}  \times \vec{\lambda})\cdot\vec{\sigma})  + i\cos(\theta/2)\sin(\theta/2)((\vec{\lambda} \cdot \hat{n})I + i(\vec{\lambda}  \times \hat{n})\cdot\vec{\sigma}) + \sin^2(\theta/2)((\hat{n} \cdot \vec{\lambda})I + i(\hat{n}  \times \vec{\lambda})\cdot\vec{\sigma})(\hat{n}\cdot\vec{\sigma})) \\
&=\frac{1}{2}(I + \cos^2(\theta/2)\vec{\lambda}\cdot\vec{\sigma} + 2\sin(\theta/2)\cos(\theta/2)(\hat{n}  \times \vec{\lambda})\cdot\vec{\sigma} + \sin^2(\theta/2)(2(\hat{n} \cdot \vec{\lambda})(\hat{n}\cdot\vec{\sigma}) - \vec{\lambda}\cdot\vec{\sigma})) \\
&=\frac{1}{2}(I + (\cos^2(\theta/2)-\sin^2(\theta/2))\vec{\lambda}\cdot\vec{\sigma} + 2\sin(\theta/2)\cos(\theta/2)(\hat{n}  \times \vec{\lambda})\cdot\vec{\sigma} + 2\sin^2(\theta/2)(\hat{n} \cdot \vec{\lambda})(\hat{n}\cdot\vec{\sigma})) \\
&=\frac{1}{2}(I + \cos(\theta)\vec{\lambda}\cdot\vec{\sigma} + \sin(\theta)(\hat{n}  \times \vec{\lambda})\cdot\vec{\sigma} + (1-\cos(\theta))(\hat{n} \cdot \vec{\lambda})(\hat{n}\cdot\vec{\sigma})) \\
\end{aligned}$$

Here are a couple of calculations that I did on the side and used in the above calculation:

$$\begin{aligned}
(\vec{a}\cdot\vec{\sigma})(\vec{b}\cdot\vec{\sigma}) &= (a_xX+a_yY+a_zZ)(b_xX+b_yY+b_zZ)\\
&= a_xb_xXX+a_xb_yXY+b_za_xXZ + a_yb_xYX+a_yb_yYY+a_yb_zYZ + a_zb_xZX+a_zb_yZY+a_zb_zZZ \\
&= a_xb_xI+ia_xb_yZ-ib_za_xY - ia_yb_xZ+a_yb_yI+ia_yb_zX + ia_zb_xY-ia_zb_yX+a_zb_zI & \text{per equation 2.78} \\
&= (a_xb_x + a_yb_y + a_zb_z)I + i(a_xb_y- a_yb_x)Z  + i(a_zb_x - b_za_x)Y + i(a_yb_z - a_zb_y)X \\
&= (\vec{a} \cdot \vec{b})I + i(\vec{a} \times \vec{b})\cdot\vec{\sigma} \\
\end{aligned}$$

$$\begin{aligned}
(\vec{a}\cdot\vec{\sigma})(\vec{b}\cdot\vec{\sigma})(\vec{a}\cdot\vec{\sigma}) &= (\vec{a} \cdot \vec{b})(\vec{a}\cdot\vec{\sigma}) + i((\vec{a} \times \vec{b})\cdot\vec{\sigma})(\vec{a}\cdot\vec{\sigma}) \\
&= (\vec{a} \cdot \vec{b})(\vec{a}\cdot\vec{\sigma}) + i(((\vec{a} \times \vec{b}) \cdot \vec{a})I + i((\vec{a} \times \vec{b}) \times \vec{a})\cdot\vec{\sigma}) \\
&= (\vec{a} \cdot \vec{b})(\vec{a}\cdot\vec{\sigma}) - (\vec{b} - \vec{a}(\vec{b}\cdot\vec{a}))\cdot\vec{\sigma} \\
&= (\vec{a} \cdot \vec{b})(\vec{a}\cdot\vec{\sigma}) - \vec{b}\cdot\vec{\sigma} + (\vec{b}\cdot\vec{a})\vec{a}\cdot\vec{\sigma} \\
&= 2(\vec{a} \cdot \vec{b})(\vec{a}\cdot\vec{\sigma}) - \vec{b}\cdot\vec{\sigma}
\end{aligned}$$

Then in the end we get the new density operator,

$$\begin{aligned}
\rho' &=\frac{1}{2}(I + (\cos(\theta)\vec{\lambda} + \sin(\theta)(\hat{n}  \times \vec{\lambda}) + (1-\cos(\theta))(\hat{n} \cdot \vec{\lambda})\hat{n})\cdot\vec{\sigma}) \\
\end{aligned}$$

With Bloch vector,

$$\begin{aligned}
\lambda' &= \cos(\theta)\vec{\lambda} + \sin(\theta)(\hat{n}  \times \vec{\lambda}) + (1-\cos(\theta))(\hat{n} \cdot \vec{\lambda})\hat{n} \\
\end{aligned}$$

This vector is the same as Rodrigues’ rotation formula, proving that $R_{\hat{n}}(\theta)$ rotates a single qubit state by angle $\theta$ about the $\hat{n}$ axis of the Bloch sphere.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.7 {#exercise-47}






Let's first show that $XYX = -Y$ 

$$\begin{aligned}
XYX &= iZX & \text{per equation 2.78}\\
&= i(iY) & \text{per equation 2.78}\\
&= -Y
\end{aligned}$$

Now let's show that $XR_y(\theta)X=R_y(-\theta)$

$$\begin{aligned}
XR_y(\theta)X &= X(\cos(\frac{\theta}{2})I - i\sin(\frac{\theta}{2})Y)X \\
&= \cos(\frac{\theta}{2})XIX - i\sin(\frac{\theta}{2})XYX \\
&= \cos(\frac{\theta}{2})I + i\sin(\frac{\theta}{2})Y \\
&= \cos(\frac{-\theta}{2})I - i\sin(\frac{-\theta}{2})Y \\
&= R_y(-\theta)
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.8 {#exercise-48}

 




From [exercise 2.56](https://adj59-dev.github.io/qcqi/chapter-2/#exercise-256), we know that $U=\exp(iK)$ for some Hermitian operator $K$. We also know that any 2x2 Hermitian operator can be written as $K=\alpha I - \frac{\theta}{2}\hat{n}\cdot\vec{\sigma}$ for some real $\alpha$ and $\theta$, and a real three-dimensional unit vector $\hat{n}$, since $\lbrace I, \sigma_x, \sigma_y, \sigma_z\rbrace$ form a basis set. Therefore, 

$$\begin{aligned}
U&=\exp(iK)\\
&=\exp(i\alpha I - i\frac{\theta}{2}\hat{n}\cdot\vec{\sigma})\\
&=\exp(i\alpha)\exp(-i\frac{\theta}{2}\hat{n}\cdot\vec{\sigma}) & \text{since $I$ and $\hat{n}\cdot\vec{\sigma}$ commute}\\
&=\exp(i\alpha)R_{\hat{n}}(\theta)
\end{aligned}$$

For the Hadamard gate, we know that

$$\begin{aligned}
H &= \exp(i\alpha)(\cos\frac{\theta}{2}I -i \sin\frac{\theta}{2}(n_xX + n_yY + n_zZ)) & \text{from above}\\
&=\frac{1}{\sqrt{2}}(X + Z) & \text{given in section 4.2}
\end{aligned}$$

Looking at the equation we can see that $\hat{n} = (\frac{1}{\sqrt{2}}, 0, \frac{1}{\sqrt{2}})$. We also know $\cos\frac{\theta}{2} = 0$, therefore $\theta = \pi$ and $\sin\frac{\theta}{2} = 1$. This means, $\exp{i\alpha}=i$ and so $\alpha = \frac{\pi}{2}$.

For the phase gate, we know that

$$\begin{aligned}
S &= \begin{bmatrix} 1 & 0 \\\ 0 & i \end{bmatrix}\\
&= \frac{1}{2}(I + Z) + i\frac{1}{2}(I - Z)\\
&= \frac{1+i}{2}I + \frac{1-i}{2}Z \\
&= \exp(i\alpha)(\cos\frac{\theta}{2}I - i \sin\frac{\theta}{2}(n_xX + n_yY + n_zZ))
\end{aligned}$$

Looking above we can see that $\hat{n} = (0,0,1)$. We can also see that $\frac{1+i}{2} = \exp(i\alpha)\cos\frac{\theta}{2}$ and that $\frac{1-i}{2} = -i\exp(i\alpha)\sin\frac{\theta}{2}$, which means $\alpha = \frac{\pi}{4}$ and $\theta=\frac{\pi}{2}$, as shown below

$$\begin{aligned}
\frac{1+i}{2} &= \exp(i\alpha)\cos\frac{\theta}{2} \\
&= (\cos(\alpha) + i\sin(\alpha))\cos\frac{\theta}{2} \\
&= (\cos(\frac{\pi}{4}) + i\sin(\frac{\pi}{4}))\cos\frac{\pi}{4} \\
&= (\frac{1}{\sqrt{2}} + i\frac{1}{\sqrt{2}})\frac{1}{\sqrt{2}} \\
&= \frac{1+i}{2}
\end{aligned}$$

$$\begin{aligned}
\frac{1-i}{2} &= -i\exp(i\alpha)\sin\frac{\theta}{2} \\
&= -i(\cos(\alpha) + i\sin(\alpha))\sin\frac{\theta}{2} \\
&= -i(\cos(\frac{\pi}{4}) + i\sin(\frac{\pi}{4}))\sin\frac{\pi}{4} \\
&= -i(\frac{1}{\sqrt{2}} + i\frac{1}{\sqrt{2}})\frac{1}{\sqrt{2}} \\
&= -i\frac{1+i}{2} \\
&= \frac{1-i}{2} \\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 4.9 {#exercise-49}






We know from [exercise 4.8](#exercise-48), we know that $U=\exp(i\alpha)R_{\hat{n}}(\theta)$. We also know that for an operator to be a unitary operator $U^\dagger U = UU^\dagger = I$. Therefore,

$$\begin{aligned}
U &= \exp(i\alpha)\begin{bmatrix} a & b \\\ c & d \end{bmatrix} \\
&= \exp(i\alpha)\left(\cos\left(\frac{\theta}{2}\right)I - i\sin\left(\frac{\theta}{2}\right)\hat{n} \cdot \vec{\sigma}\right)\\
&=\exp(i\alpha)\left(\cos\left(\frac{\theta}{2}\right)\begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} - i\sin\left(\frac{\theta}{2}\right)\begin{bmatrix} n_z & n_x - i n_y \\\ n_x + i n_y & -n_z \end{bmatrix}\right)\\
&=\exp(i\alpha)\left(\begin{bmatrix} \cos\left(\frac{\theta}{2}\right) - in_z\sin\left(\frac{\theta}{2}\right) & - i(n_x - i n_y)\sin\left(\frac{\theta}{2}\right) \\\ - i(n_x + i n_y)\sin\left(\frac{\theta}{2}\right) &  \cos\left(\frac{\theta}{2}\right) + in_z\sin\left(\frac{\theta}{2}\right)\end{bmatrix}\right)
\end{aligned}$$

and so taking the determinant,

$$\begin{aligned}
\det \left( \begin{bmatrix} a & b \\\ c & d \end{bmatrix} \right) &= ad-bc \\
&= \left(\cos\left(\frac{\theta}{2}\right) - in_z\sin\left(\frac{\theta}{2}\right)\right)\left(\cos\left(\frac{\theta}{2}\right) + in_z\sin\left(\frac{\theta}{2}\right)\right) - \left(- i(n_x - i n_y)\sin\left(\frac{\theta}{2}\right)\right)\left(- i(n_x + i n_y)\sin\left(\frac{\theta}{2}\right)\right)\\
&= \cos^2\left(\frac{\theta}{2}\right) + n_z^2\sin^2\left(\frac{\theta}{2}\right) + (n_x^2 + n_y^2)\sin^2\left(\frac{\theta}{2}\right)\\
&= \cos^2\left(\frac{\theta}{2}\right) + \sin^2\left(\frac{\theta}{2}\right)\\
&= 1
\end{aligned}$$

Since $U$ is unitary the following conditions must be true,

$$\begin{aligned}
I &= UU^\dagger \\
&= \exp(i\alpha)\exp(-i\alpha)\begin{bmatrix} a & b \\\ c & d \end{bmatrix} \begin{bmatrix} a^\ast & c^\ast \\\ b^\ast & d^\ast \end{bmatrix} \\
&= \begin{bmatrix} aa^\ast + bb^\ast & ac^\ast + bd^\ast \\\ ca^\ast + db^\ast & cc^\ast + dd^\ast \end{bmatrix} \\
\end{aligned}$$

Putting it all together we get these sets of equations

$$\begin{aligned}
1 &= aa^\ast + bb^\ast = \vert a \vert^2 + \vert b \vert^2 \\
1 &= cc^\ast + dd^\ast = \vert c \vert^2 + \vert d \vert^2 \\
0 &= ac^\ast + bd^\ast  \\
1 &= ad - bc & \text{from the determinant} \\
\end{aligned}$$

Solving for these equations we get $c = -b^\ast$ and $d = a^\ast$, with the constraint $\vert a \vert^2 + \vert b \vert^2=1$. The following parameterization meets these conditions without loss of generality so can be used: $a = e^{-i(\beta/2 + \delta/2)}\cos\frac{\gamma}{2}$ and $b = -e^{-i(\beta/2 - \delta/2)}\sin\frac{\gamma}{2}$. Therefore,

$$\begin{aligned}
U &= \exp(i\alpha)\begin{bmatrix} e^{-i(\beta/2 + \delta/2)}\cos\frac{\gamma}{2} & -e^{-i(\beta/2 - \delta/2)}\sin\frac{\gamma}{2} \\\ e^{i(\beta/2 - \delta/2)}\sin\frac{\gamma}{2} & e^{i(\beta/2 + \delta/2)}\cos\frac{\gamma}{2} \end{bmatrix} \\
&= \begin{bmatrix} e^{i(\alpha - \beta/2 - \delta/2)}\cos\frac{\gamma}{2} & -e^{i(\alpha - \beta/2 + \delta/2)}\sin\frac{\gamma}{2} \\\ e^{i(\alpha + \beta/2 - \delta/2)}\sin\frac{\gamma}{2} & e^{i(\alpha + \beta/2 + \delta/2)}\cos\frac{\gamma}{2} \end{bmatrix} \\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.10 {#exercise-410}






Theorem 4.1 says 

$$\begin{aligned}
U=e^{i\alpha} R_z(\beta)R_y(\gamma)R_z(\delta)\\
\end{aligned}$$

and so an analogous decomposition would be 

$$\begin{aligned}
U &= e^{i\alpha} R_x(\beta)R_y(\gamma)R_x(\delta)\\
&= e^{i\alpha} \begin{bmatrix} \cos\left(\frac{\beta}{2} \right) & -i\sin\left(\frac{\beta}{2} \right) \\\ -i\sin\left(\frac{\beta}{2} \right)  & \cos\left(\frac{\beta}{2} \right) \end{bmatrix} \begin{bmatrix} \cos\left(\frac{\gamma}{2} \right) & -\sin\left(\frac{\gamma}{2} \right) \\\ \sin\left(\frac{\gamma}{2} \right)  & \cos\left(\frac{\gamma}{2} \right) \end{bmatrix} \begin{bmatrix} \cos\left(\frac{\delta}{2} \right) & -i\sin\left(\frac{\delta}{2} \right) \\\ -i\sin\left(\frac{\delta}{2} \right)  & \cos\left(\frac{\delta}{2} \right) \end{bmatrix} \\
&= e^{i\alpha} \begin{bmatrix} a & -ib  \\\ -ib  & a  \end{bmatrix} \begin{bmatrix} c & -d \\\ d  & c \end{bmatrix} \begin{bmatrix} e & -if \\\ -if  & e \end{bmatrix} &\text{introduce shorthand, where $a,b,c,d,e,f \in \mathbb{R}$} \\
&= e^{i\alpha} \begin{bmatrix} ac -ibd & -ad - ibc  \\\ -ibc + ad  & ibd + ac  \end{bmatrix}\begin{bmatrix} e & -if \\\ -if  & e \end{bmatrix}\\
&= e^{i\alpha} \begin{bmatrix} (ac -ibd)e - i(-ad - ibc)f & -i(ac -ibd)f + (-ad - ibc)e  \\\ (-ibc + ad )e - i(ibd + ac)f & -i(-ibc + ad )f + (ibd + ac)e \end{bmatrix}
\end{aligned}$$

From [exercise 4.9](#exercise-49), we know that these criteria must be met in order for this decomposition to work for any unitary operator: $(-ibc + ad )e - i(ibd + ac)f = -(-i(ac -ibd)f + (-ad - ibc)e)^\ast$ and $-i(-ibc + ad )f + (ibd + ac)e = ((ac -ibd)e - i(-ad - ibc)f)^\ast$, with the constraint $\vert (ac -ibd)e - i(-ad - ibc)f \vert^2 + \vert -i(ac -ibd)f + (-ad - ibc)e \vert^2=1$. So, let's check them

$$\begin{aligned}
(-ibc + ad )e - i(ibd + ac)f = -(-i(ac -ibd)f + (-ad - ibc)e)^\ast \\
-ibce + ade + bdf - iacf &= -(-iacf - bdf - ade - ibce)^\ast \\
-ibce + ade + bdf - iacf &= -iacf + bdf + ade - ibce & \text{the two sides are equal}
\end{aligned}$$

$$\begin{aligned}
-i(-ibc + ad )f + (ibd + ac)e = ((ac -ibd)e - i(-ad - ibc)f)^\ast \\
-bcf - iadf + ibde + ace &= (ace - ibde + iadf - bcf)^\ast \\
-bcf - iadf + ibde + ace &= ace + ibde - iadf - bcf & \text{the two sides are equal}
\end{aligned}$$

$$\begin{aligned}
1 &= \vert (ac -ibd)e - i(-ad - ibc)f \vert^2 + \vert -i(ac -ibd)f + (-ad - ibc)e \vert^2 \\
&= ((ac -ibd)e + i(ad + ibc)f)((ac -ibd)e + i(ad + ibc)f)^\ast + (-i(ac -ibd)f - (ad + ibc)e )(-i(ac -ibd)f - (ad + ibc)e )^\ast \\
&= (ace -ibde + iadf - bcf)(ace -ibde + iadf - bcf)^\ast + (-iacf -bdf - ade - ibce )(-iacf - bdf - ade - ibce )^\ast \\
&= (ace -ibde + iadf - bcf)(ace +ibde - iadf - bcf) + (-iacf -bdf - ade - ibce )(iacf - bdf - ade + ibce ) \\
&= (ace - bcf)^2 + (adf - bde)^2 + (ade + bdf)^2 + (acf + bce)^2 \\
&= a^2c^2e^2 + b^2c^2f^2 - 2abc^2ef + a^2d^2f^2 + b^2d^2e^2 -2abd^2ef + a^2d^2e^2 + b^2d^2f^2 + 2abd^2ef + a^2c^2f^2 + b^2c^2f^2 + 2abc^2ef \\
&= a^2c^2e^2 + b^2c^2f^2 + a^2d^2f^2 + b^2d^2e^2 + a^2d^2e^2 + b^2d^2f^2 + a^2c^2f^2 + b^2c^2f^2  \\
&= (a^2 + b^2)(c^2e^2 + c^2f^2 + d^2f^2 + d^2e^2) \\
&= (a^2 + b^2)(c^2 + d^2)(e^2 + f^2) \\
&= \left(\cos^2\left(\frac{\beta}{2}\right) + \sin^2\left(\frac{\beta}{2}\right)\right)\left(\cos^2\left(\frac{\gamma}{2}\right) + \sin^2\left(\frac{\gamma}{2}\right)\right)\left(\cos^2\left(\frac{\delta}{2}\right) + \sin^2\left(\frac{\delta}{2}\right)\right) \\
&= 1 
\end{aligned}$$

Since all required conditions are met, $U = e^{i\alpha} R_x(\beta)R_y(\gamma)R_x(\delta)$ is a valid decomposition for any unitary operator. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.11 {#exercise-411}

Note: per the [errata page](https://michaelnielsen.org/qcqi/errata/errata/errata.html) the correct equation is different than what is in the book. 




Let's start with Theorem 4.1 $U=e^{i\alpha}R_z(\beta)R_y(\gamma)R_z(\delta)$ and then think about how we can write it in terms of rotations about two arbitrary axes $\hat{n}$ and $\hat{m}$. We know that we can write $R_z$ and $R_y$ in terms of $R_{\hat{m}}$ and $R_{\hat{n}}$ as shown below since rotating about two fixed non-parallel axes is enough to generate all possible orientations,

$$\begin{aligned}
R_z(\theta_1) &= R_{\hat{n}}(\beta_1)R_{\hat{m}}(\gamma_1)R_{\hat{n}}(\delta_1) \\
R_y(\theta_2) &= R_{\hat{n}}(\beta_2)R_{\hat{m}}(\gamma_2)R_{\hat{n}}(\delta_2) \\
\end{aligned}$$

Then,

$$\begin{aligned}
U &= e^{i\alpha}R_z(\theta_1)R_y(\theta_2)R_z(\theta_3) \\
&= e^{i\alpha}R_{\hat{n}}(\beta_1)R_{\hat{m}}(\gamma_1)R_{\hat{n}}(\delta_1)R_{\hat{n}}(\beta_2)R_{\hat{m}}(\gamma_2)R_{\hat{n}}(\delta_2)R_{\hat{n}}(\beta_3)R_{\hat{m}}(\gamma_3)R_{\hat{n}}(\delta_3) \\
&= e^{i\alpha}R_{\hat{n}}(\beta_1)R_{\hat{m}}(\gamma_1)R_{\hat{n}}(\delta_1 + \beta_2)R_{\hat{m}}(\gamma_2)R_{\hat{n}}(\delta_2 + \beta_3)R_{\hat{m}}(\gamma_3)R_{\hat{n}}(\delta_3) \\
\end{aligned}$$

Therefore, an arbitrary single qubit unitary $U$ may be written $U=e^{i\alpha}R_{\hat{n}}(\beta_1)R_{\hat{m}}(\gamma_1)R_{\hat{n}}(\beta_2)R_{\hat{m}}(\gamma_2)\cdots$ for appropriate choices of $\alpha, \beta_k, \gamma_k$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.12 {#exercise-412}






From Corollary 4.2 we know that there exist operators $A,B,C$ such that $U=e^{i\alpha}AXBXC$ and $ABC=I$. In [exercise 4.4](#exercise-44) we showed that the Hadamard gate can be written as $H=e^{i\pi/2}R_z(\pi/2)R_x(\pi/2)R_z(\pi/2)$, but to write it in the requested form we'll need to have it written in terms of $R_z$ and $R_y$. We know,

$$\begin{aligned}
R_x(\theta) &= R_z(-\pi/2)R_y(\theta)R_z(\pi/2)
\end{aligned}$$

and so

$$\begin{aligned}
H &= e^{i\pi/2}R_z(\pi/2)R_x(\pi/2)R_z(\pi/2)\\
&= e^{i\pi/2}R_z(\pi/2)R_z(-\pi/2)R_y(\pi/2)R_z(\pi/2)R_z(\pi/2) & \text{decomposition of $R_x$}\\
&= e^{i\pi/2}R_z(0)R_y(\pi/2)R_z(\pi) \\
&= e^{i\pi/2}R_y(\pi/2)R_z(\pi) & \text{since $R_z(0)=I$}\\
&= e^{i\pi/2}R_y(\pi/4)R_y(\pi/4)R_z(\pi/2)R_z(\pi/2) \\
&= e^{i\pi/2}R_y(\pi/4)XR_y(-\pi/4)XXR_z(-\pi/2)XR_z(\pi/2) & \text{see corollary proof} \\
&= e^{i\pi/2}R_y(\pi/4)XR_y(-\pi/4)R_z(-\pi/2)XR_z(\pi/2) & \text{since $XX=I$}
\end{aligned}$$

Therefore, $A = R_y(\pi/4)$, $B = R_y(-\pi/4)R_z(-\pi/2)$, $C = R_z(\pi/2)$, and $\alpha = \pi/2$. This satisfies the requirement that $ABC=I$, as shown below.

$$\begin{aligned}
ABC &= R_y(\pi/4)R_y(-\pi/4)R_z(-\pi/2)R_z(\pi/2)\\
&= R_y(0)R_z(0) \\
&= I
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.13 {#exercise-413}






$$\begin{aligned}
HXH &= \frac{1}{2}(X + Z)X(X + Z) & \text{$H=\frac{X+Z}{\sqrt{2}}$ given on page 174}\\
&= \frac{1}{2}(XX + ZX)(X + Z) \\
&= \frac{1}{2}(XXX + ZXX + XXZ + ZXZ) \\
&= \frac{1}{2}(XI + ZI + IZ - X) \\
&= \frac{1}{2}(2Z) \\
&= Z
\end{aligned}$$

$$\begin{aligned}
HYH &= \frac{1}{2}(X + Z)Y(X + Z) & \text{$H=\frac{X+Z}{\sqrt{2}}$ given on page 174}\\
&= \frac{1}{2}(XY + ZY)(X + Z) \\
&= \frac{1}{2}(XYX + ZYX + XYZ + ZYZ)\\
&= \frac{1}{2}(-Y + Z(-iZ) + (iZ)Z - Y) & \text{equation 2.78}\\
&= \frac{1}{2}(-2Y) \\
&= -Y \\
\end{aligned}$$

$$\begin{aligned}
HZH &= \frac{1}{2}(X + Z)Z(X + Z) & \text{$H=\frac{X+Z}{\sqrt{2}}$ given on page 174}\\
&= \frac{1}{2}(XZ + ZZ)(X + Z) \\
&= \frac{1}{2}(XZX + ZZX + XZZ + ZZZ) \\
&= \frac{1}{2}(-Z + IX + XI + IZ) \\
&= \frac{1}{2}(2X) \\
&= X
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.14 {#exercise-414}






From [exercise 4.3](#exercise-43) we know that $T=R_z(\pi/4)$ up to a global phase. Therefore, the following is true up to a global phase

$$\begin{aligned}
HTH &= HR_z(\pi/4)H \\
&= R_z(\pi/2)R_x(\pi/2)R_z(\pi/2)R_z(\pi/4)R_z(\pi/2)R_x(\pi/2)R_z(\pi/2) & \text{true up to a global phase per exercise 4.4} \\
&=  R_z(\pi/2)R_x(\pi/2)R_z(-\pi/2)R_z(\pi/2)R_z(\pi/2)R_z(\pi/4)R_z(\pi/2)R_z(\pi/2)R_z(-\pi/2)R_x(\pi/2)R_z(\pi/2)  & \text{since $R_z(-\pi/2)R_z(\pi/2)=I$}\\
&=  R_y(\pi/2)R_z(2\pi + \pi/4)R_y(-\pi/2) & \text{decomposition} \\
&=  R_y(\pi/2)R_z(\pi/4)R_y(-\pi/2) \\
&= R_x(\pi/4) & \text{decomposition} 
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.15 {#exercise-415}

Note: The [errata page](https://michaelnielsen.org/qcqi/errata/errata/errata.html) says that in Equations (4.20) and (4.22) the minus sign on the right-hand side should be a plus.




So let's calculate this rotation with $c_i = \cos(\beta_i/2)$ and $s_i = \sin(\beta_i/2)$,

$$\begin{aligned}
R_{\hat{n_2}}(\beta_2)R_{\hat{n_1}}(\beta_1) &= \left(c_2I - is_2(\hat{n_2}\cdot \vec{\sigma})\right)\left(c_1I - is_1(\hat{n_1}\cdot \vec{\sigma})\right) \\
&= c_1c_2II - ic_1s_2(\hat{n_2}\cdot \vec{\sigma})I - is_1c_2I(\hat{n_1}\cdot \vec{\sigma}) - s_1s_2(\hat{n_2}\cdot \vec{\sigma})(\hat{n_1}\cdot \vec{\sigma}) \\
&= c_1c_2I - ic_1s_2(\hat{n_2}\cdot \vec{\sigma}) - is_1c_2(\hat{n_1}\cdot \vec{\sigma}) - s_1s_2((\hat{n_2} \cdot \hat{n_1})I + i(\hat{n_2} \times \hat{n_1})\cdot\vec{\sigma}) & \text{from exercise 4.6}\\
&= (c_1c_2 - s_1s_2(\hat{n_2} \cdot \hat{n_1}))I - i(c_1s_2\hat{n_2} + s_1c_2\hat{n_1}+ s_1s_2(\hat{n_2} \times \hat{n_1}))\cdot\vec{\sigma} \\
&= c_{12}I - is_{12}(\hat{n_{12}}\cdot\vec{\sigma}) \\
\end{aligned}$$

where $c_{12} = c_1c_2 - s_1s_2(\hat{n_2} \cdot \hat{n_1})$ and $s_{12}\hat{n_{12}} = c_1s_2\hat{n_2} + s_1c_2\hat{n_1}+ s_1s_2(\hat{n_2} \times \hat{n_1})$. 

If $\beta_1 = \beta_2$ and $\hat{n_1} = \hat{z}$, then $c_1=c_2=c$, $s_1=s_2=s$,

$$\begin{aligned}
c_{12} &= c_1c_2 - s_1s_2(\hat{n_2} \cdot \hat{n_1})\\
&= c^2 - s^2(\hat{n_2} \cdot \hat{z})\\
\end{aligned}$$

and

$$\begin{aligned}
s_{12}\hat{n_{12}} &= c_1s_2\hat{n_2} + s_1c_2\hat{n_1}+ s_1s_2(\hat{n_2} \times \hat{n_1}) \\
&= cs\hat{n_2} + sc\hat{z}+ s^2(\hat{n_2} \times \hat{z}) \\
&= sc(\hat{z} + \hat{n_2})+ s^2(\hat{n_2} \times \hat{z}) \\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |





## Controlled operations

### Exercise 4.16 {#exercise-416}

Find the matrix representation for a given circuit.




The first circuit applies the Hadamard operation to $\ket{x_2}$ and leaves $\ket{x_1}$ unchanged. Therefore for computation basis $\ket{x_1x_2}$,

$$\begin{aligned}
M &= I \otimes H \\
&= \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \otimes \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \\
&=\frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 1 & 0 & 0 \\\ 1 & -1 & 0 & 0 \\\ 0 & 0 & 1 & 1 \\\ 0 & 0 & 1 & -1 \end{bmatrix}
\end{aligned}$$

The second circuit applies the Hadamard operation to $\ket{x_1}$ and leaves $\ket{x_2}$ unchanged. Therefore for computation basis $\ket{x_1x_2}$,

$$\begin{aligned}
M &= H \otimes I \\
&= \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \otimes \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix}  \\
&=\frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 0 & 1 & 0 \\\ 0 & 1 & 0 & 1 \\\ 1 & 0 & -1 & 0 \\\ 0 & 1 & 0 & -1 \end{bmatrix}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.17 {#exercise-417}






The matrix representation for a CNOT gate is

$$\begin{aligned}
CNOT = \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix}
\end{aligned}$$

and the matrix representation for a controlled-Z gate is

$$\begin{aligned}
CZ = \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & -1 \end{bmatrix}
\end{aligned}$$

Let's try $(I \otimes H)CZ(I \otimes H)$ since we know $HZH = X$ from [exercise 4.13](#exercise-413) and it looks like CNOT is a controlled-X gate.

$$\begin{aligned}
(I \otimes H)CZ(I \otimes H) &= \frac{1}{2}\begin{bmatrix} 1 & 1 & 0 & 0 \\\ 1 & -1 & 0 & 0 \\\ 0 & 0 & 1 & 1 \\\ 0 & 0 & 1 & -1 \end{bmatrix} \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & -1 \end{bmatrix} \begin{bmatrix} 1 & 1 & 0 & 0 \\\ 1 & -1 & 0 & 0 \\\ 0 & 0 & 1 & 1 \\\ 0 & 0 & 1 & -1 \end{bmatrix} \\
 &= \frac{1}{2}\begin{bmatrix} 1 & 1 & 0 & 0 \\\ 1 & -1 & 0 & 0 \\\ 0 & 0 & 1 & -1 \\\ 0 & 0 & 1 & 1 \end{bmatrix} \begin{bmatrix} 1 & 1 & 0 & 0 \\\ 1 & -1 & 0 & 0 \\\ 0 & 0 & 1 & 1 \\\ 0 & 0 & 1 & -1 \end{bmatrix} \\
 &= \frac{1}{2}\begin{bmatrix} 2 & 0 & 0 & 0 \\\ 0 & 2 & 0 & 0 \\\ 0 & 0 & 0 & 2 \\\ 0 & 0 & 2 & 0 \end{bmatrix}  \\
 &= \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix} \\
 &= CNOT
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.18 {#exercise-418}






Let's compare the behavior of the two gates for a basis set of states.

| $\ket{a}\ket{b}$ | $Z^b\ket{a}\ket{b}$ | $\ket{a}Z^a\ket{b}$ |
|:----------------:|:-------------------:|:--------------------|
| $\ket{0}\ket{0}$ | $\ket{0}\ket{0}$    | $\ket{0}\ket{0}$    |
| $\ket{1}\ket{0}$ | $\ket{1}\ket{0}$    | $\ket{1}Z\ket{0}=\ket{1}\ket{0}$    |
| $\ket{0}\ket{1}$ | $Z\ket{0}\ket{1}=\ket{0}\ket{1}$    | $\ket{0}\ket{1}$    |
| $\ket{1}\ket{1}$ | $Z\ket{1}\ket{1} = -\ket{1}\ket{1}$   | $\ket{1}Z\ket{1}=-\ket{1}\ket{1}$   |

Since the behavior of the two gates are the same for all the states, the two gates are equivalent. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.19 {#exercise-419}






The density matrix can be written

$$\begin{aligned}
\rho = \begin{bmatrix} p_{11} & p_{12} & p_{13} & p_{14} \\\ p_{21} & p_{22} & p_{23} & p_{24} \\\ p_{31} & p_{32} & p_{33} & p_{34} \\\ p_{41} & p_{42} & p_{43} & p_{44} \end{bmatrix} 
\end{aligned}$$


Therefore the impact to the density matrix is $\rho \rightarrow CNOT \rho CNOT^\dagger$, as shown below

$$\begin{aligned}
CNOT \rho CNOT^\dagger &= \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix}\begin{bmatrix} p_{11} & p_{12} & p_{13} & p_{14} \\\ p_{21} & p_{22} & p_{23} & p_{24} \\\ p_{31} & p_{32} & p_{33} & p_{34} \\\ p_{41} & p_{42} & p_{43} & p_{44} \end{bmatrix}  \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix}^\dagger \\
&= \begin{bmatrix} p_{11} & p_{12} & p_{13} & p_{14} \\\ p_{21} & p_{22} & p_{23} & p_{24} \\\ p_{41} & p_{42} & p_{43} & p_{44} \\\ p_{31} & p_{32} & p_{33} & p_{34} \end{bmatrix}  \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix} \\
&= \begin{bmatrix} p_{11} & p_{12} & p_{14} & p_{13} \\\ p_{21} & p_{22} & p_{24} & p_{23} \\\ p_{41} & p_{42} & p_{44} & p_{43} \\\ p_{31} & p_{32} & p_{34} & p_{33} \end{bmatrix} 
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.20 {#exercise-420}






First let's calculate $H \otimes H$.

$$\begin{aligned}
\frac{1}{2}\begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \otimes \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix}  &= \frac{1}{2}\begin{bmatrix} 1 & 1 & 1 & 1 \\\ 1 & -1 & 1 & -1 \\\ 1 & 1 & -1 & -1 \\\ 1 & -1 & -1 & 1 \end{bmatrix} 
\end{aligned}$$

Now let's calculate $(H \otimes H)CNOT_{12}(H\otimes H)$

$$\begin{aligned}
(H \otimes H)CNOT_{12}(H\otimes H) &= \frac{1}{4}\begin{bmatrix} 1 & 1 & 1 & 1 \\\ 1 & -1 & 1 & -1 \\\ 1 & 1 & -1 & -1 \\\ 1 & -1 & -1 & 1 \end{bmatrix} \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix} \begin{bmatrix} 1 & 1 & 1 & 1 \\\ 1 & -1 & 1 & -1 \\\ 1 & 1 & -1 & -1 \\\ 1 & -1 & -1 & 1 \end{bmatrix} \\ 
&= \frac{1}{4}\begin{bmatrix} 1 & 1 & 1 & 1 \\\ 1 & -1 & -1 & 1 \\\ 1 & 1 & -1 & -1 \\\ 1 & -1 & 1 & -1 \end{bmatrix} \begin{bmatrix} 1 & 1 & 1 & 1 \\\ 1 & -1 & 1 & -1 \\\ 1 & 1 & -1 & -1 \\\ 1 & -1 & -1 & 1 \end{bmatrix} \\ 
&= \frac{1}{4}\begin{bmatrix} 4 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 4 \\\ 0 & 0 & 4 & 0 \\\ 0 & 4 & 0 & 0 \end{bmatrix} \\ 
&= \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \\\ 0 & 1 & 0 & 0 \end{bmatrix} \\
&= CNOT_{21}
\end{aligned}$$

Now that we've proven this circuit identity, let's use it to show that the effect of a CNOT with the first qubit as the control and the second qubit as the target is as follows:

$$\begin{aligned}
\ket{+}\ket{+} &\xrightarrow{CNOT_{12}} \ket{+}\ket{+} \\
\ket{-}\ket{+} &\xrightarrow{CNOT_{12}} \ket{-}\ket{+} \\
\ket{+}\ket{-} &\xrightarrow{CNOT_{12}} \ket{-}\ket{-} \\
\ket{-}\ket{-} &\xrightarrow{CNOT_{12}} \ket{+}\ket{-} \\
\end{aligned}$$

The $CNOT_{21}$ gate has the following effect:

$$\begin{aligned}
\ket{0}\ket{0} &\xrightarrow{CNOT_{21}} \ket{0}\ket{0} \\
\ket{1}\ket{0} &\xrightarrow{CNOT_{21}} \ket{1}\ket{0} \\
\ket{0}\ket{1} &\xrightarrow{CNOT_{21}} \ket{1}\ket{1} \\
\ket{1}\ket{1} &\xrightarrow{CNOT_{21}} \ket{0}\ket{1} \\
\end{aligned}$$

The Hadamard gates transform $\ket{0} \rightarrow \ket{+}$ and $\ket{1} \rightarrow \ket{-}$. They also transform $\ket{+} \rightarrow \ket{0}$ and $\ket{-} \rightarrow \ket{1}$. Therefore looking at the effect of the $CNOT_{21}$ gate and using the circuit identity, we can write:

$$\begin{aligned}
\ket{0}\ket{0} &\xrightarrow{H \otimes H} \ket{+}\ket{+} &\xrightarrow{CNOT_{12}} \ket{+}\ket{+} &\xrightarrow{H \otimes H} \ket{0}\ket{0} \\
\ket{1}\ket{0} &\xrightarrow{H \otimes H} \ket{-}\ket{+} &\xrightarrow{CNOT_{12}} \ket{-}\ket{+} &\xrightarrow{H \otimes H} \ket{1}\ket{0} \\
\ket{0}\ket{1} &\xrightarrow{H \otimes H} \ket{+}\ket{-} &\xrightarrow{CNOT_{12}} \ket{-}\ket{-} &\xrightarrow{H \otimes H} \ket{1}\ket{1} \\
\ket{1}\ket{1} &\xrightarrow{H \otimes H} \ket{-}\ket{-} &\xrightarrow{CNOT_{12}} \ket{+}\ket{-} &\xrightarrow{H \otimes H} \ket{0}\ket{1} \\
\end{aligned}$$

The effect of a CNOT gate on the $\ket{\pm}\ket{\pm}$ states is shown in the middle.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.21 {#exercise-421}

I approached this exercise by expressing all the gates in their matrix representation and multiplying together the ones on the right-hand side of the circuit inequality to get the effect of the combined circuit. Then I pointed out that this is equal to the matrix representation of the circuit on the left-hand side of the circuit inequality. 




<img width="762" height="198" alt="image" src="https://github.com/user-attachments/assets/95534f9b-e2e3-4d01-81c2-23d867c3a7d3" />

First I am going to make matrix representations for these different gates. The basis I am going to use is $\lbrace \ket{000}, \ket{001}, \ket{010}, \ket{011}, \ket{100}, \ket{101}, \ket{110}, \ket{111} \rbrace$ for $\ket{abc}$

Let's construct the matrix for $V_{bc}$

$$\begin{aligned}
\ket{000} &\xrightarrow{V_{bc}} \ket{000} \\
\ket{001} &\xrightarrow{V_{bc}} \ket{001} \\
\ket{010} &\xrightarrow{V_{bc}} V_{c}\ket{010} \\
\ket{011} &\xrightarrow{V_{bc}} V_{c}\ket{011} \\
\ket{100} &\xrightarrow{V_{bc}} \ket{100} \\
\ket{101} &\xrightarrow{V_{bc}} \ket{101} \\
\ket{110} &\xrightarrow{V_{bc}} V_{c}\ket{110} \\
\ket{111} &\xrightarrow{V_{bc}} V_{c}\ket{111} \\
\end{aligned}$$

$$\begin{aligned}
V_{bc} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & v_{11} & v_{12} & 0 & 0 & 0 & 0 \\\ 0 & 0 & v_{21} & v_{22} & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{11} & v_{12} \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{21} & v_{22}\end{bmatrix}
\end{aligned}$$

Let's construct the matrix for $V_{ac}$

$$\begin{aligned}
\ket{000} &\xrightarrow{V_{ac}} \ket{000} \\
\ket{001} &\xrightarrow{V_{ac}} \ket{001} \\
\ket{010} &\xrightarrow{V_{ac}} \ket{010} \\
\ket{011} &\xrightarrow{V_{ac}} \ket{011} \\
\ket{100} &\xrightarrow{V_{ac}} V_{c}\ket{100} \\
\ket{101} &\xrightarrow{V_{ac}} V_{c}\ket{101} \\
\ket{110} &\xrightarrow{V_{ac}} V_{c}\ket{110} \\
\ket{111} &\xrightarrow{V_{ac}} V_{c}\ket{111} \\
\end{aligned}$$

$$\begin{aligned}
V_{ac} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & v_{11} & v_{12} & 0 & 0 \\\ 0 & 0 & 0 & 0 & v_{21} & v_{22} & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{11} & v_{12} \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{21} & v_{22}\end{bmatrix}
\end{aligned}$$

Let's construct the matrix for $CNOT_{ab}$

$$\begin{aligned}
\ket{000} &\xrightarrow{CNOT_{ab}} \ket{000} \\
\ket{001} &\xrightarrow{CNOT_{ab}} \ket{001} \\
\ket{010} &\xrightarrow{CNOT_{ab}} \ket{010} \\
\ket{011} &\xrightarrow{CNOT_{ab}} \ket{011} \\
\ket{100} &\xrightarrow{CNOT_{ab}} \ket{110} \\
\ket{101} &\xrightarrow{CNOT_{ab}} \ket{111} \\
\ket{110} &\xrightarrow{CNOT_{ab}} \ket{100} \\
\ket{111} &\xrightarrow{CNOT_{ab}} \ket{101} \\
\end{aligned}$$

$$\begin{aligned}
CNOT_{ab} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0\end{bmatrix}
\end{aligned}$$

Then we expect $U_{abc}$ to be given by 

$$\begin{aligned}
\ket{000} &\xrightarrow{U} \ket{000} \\
\ket{001} &\xrightarrow{U} \ket{001} \\
\ket{010} &\xrightarrow{U} \ket{010} \\
\ket{011} &\xrightarrow{U} \ket{011} \\
\ket{100} &\xrightarrow{U} \ket{101} \\
\ket{101} &\xrightarrow{U} \ket{100} \\
\ket{110} &\xrightarrow{U} U_{c}\ket{111} \\
\ket{111} &\xrightarrow{U} U_{c}\ket{110} \\
\end{aligned}$$

$$\begin{aligned}
U_{abc}  = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & u_{11} & u_{12} \\\ 0 & 0 & 0 & 0 & 0 & 0 & u_{21} & u_{22} \end{bmatrix}
\end{aligned}$$

The left hand side of the circuit inequality is

$$\begin{aligned}
V_{ac} CNOT_{ab} V_{bc}^\dagger CNOT_{ab} V_{bc} &= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & v_{11} & v_{12} & 0 & 0 \\\ 0 & 0 & 0 & 0 & v_{21} & v_{22} & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{11} & v_{12} \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{21} & v_{22}\end{bmatrix} \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0\end{bmatrix} \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & v_{11}^\ast & v_{21}^\ast & 0 & 0 & 0 & 0 \\\ 0 & 0 & v_{12}^\ast & v_{22}^\ast & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{11}^\ast & v_{21}^\ast \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{12}^\ast & v_{22}^\ast \end{bmatrix}\begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0\end{bmatrix} \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & v_{11} & v_{12} & 0 & 0 & 0 & 0 \\\ 0 & 0 & v_{21} & v_{22} & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{11} & v_{12} \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{21} & v_{22}\end{bmatrix} \\
&= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & \vert v_{11} \vert^2 + \vert v_{21} \vert^2 & v_{12}v_{11}^\ast + v_{22}v_{21}^\ast & 0 & 0 & 0 & 0 \\\ 0 & 0 & v_{11}v_{12}^\ast + v_{21}v_{22}^\ast & \vert v_{12} \vert^2 + \vert v_{22} \vert^2 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & \vert v_{11} \vert^2 + \vert v_{12} \vert^2 & v_{11}v_{21}^\ast + v_{12}v_{22}^\ast & 0 & 0 \\\ 0 & 0 & 0 & 0 & v_{21}v_{11}^\ast + v_{22}v_{12}^\ast & \vert v_{21} \vert^2 + \vert v_{22} \vert^2 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{11}^2 + v_{12}v_{21} & v_{12}(v_{11}+v_{22}) \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{21}(v_{11} + v_{22}) & v_{12}v_{21} + v_{22}^2 \end{bmatrix} \\
\end{aligned}$$

We know that $V^2 = U$ so

$$\begin{aligned}
V^2 &= \begin{bmatrix} v_{11} & v_{12} \\\ v_{21} & v_{22} \end{bmatrix} \begin{bmatrix} v_{11} & v_{12} \\\ v_{21} & v_{22} \end{bmatrix} \\
&= \begin{bmatrix} v_{11}^2 + v_{12}v_{21} & v_{12}(v_{11} + v_{22}) \\\ v_{21}(v_{11} + v_{22}) & v_{22}^2 + v_{12}v_{21} \end{bmatrix} \\
&= \begin{bmatrix} u_{11} & u_{12} \\\ u_{21} & u_{22} \end{bmatrix}
\end{aligned}$$

We also know that $V$ is unitary so

$$\begin{aligned}
I &= VV^\dagger \\ 
&= \begin{bmatrix} v_{11} & v_{12} \\\ v_{21} & v_{22} \end{bmatrix} \begin{bmatrix} v_{11}^\ast & v_{21}^\ast \\\ v_{12}^\ast & v_{22}^\ast \end{bmatrix} \\
&= \begin{bmatrix} \vert v_{11} \vert^2 + \vert v_{12} \vert^2 & v_{11}v_{21}^\ast + v_{12}v_{22}^\ast \\\ v_{21}v_{11}^\ast +v_{22}v_{12}^\ast & \vert v_{22} \vert^2 + \vert v_{21} \vert^2 \end{bmatrix} \\
&= V^\dagger V \\
&= \begin{bmatrix} v_{11}^\ast & v_{21}^\ast \\\ v_{12}^\ast & v_{22}^\ast \end{bmatrix} \begin{bmatrix} v_{11} & v_{12} \\\ v_{21} & v_{22} \end{bmatrix} \\
&= \begin{bmatrix} \vert v_{11} \vert^2 + \vert v_{21} \vert^2 & v_{11}^\ast v_{12} + v_{21}^\ast v_{22} \\\ v_{12}^\ast v_{11} +v_{22}^\ast v_{21} & \vert v_{22} \vert^2 + \vert v_{12} \vert^2 \end{bmatrix} \\
&= \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix}
\end{aligned}$$

Putting it all together we get 

$$\begin{aligned}
V_{ac} CNOT_{ab} V_{bc}^\dagger CNOT_{ab} V_{bc} &= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & u_{11} & u_{12} \\\ 0 & 0 & 0 & 0 & 0 & 0 & u_{21} & u_{22} \end{bmatrix}
&= U_{abc}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.22 {#exercise-422}

I found comparing the circuit that I was creating to the Toffoli gate on Wikipedia and rereading section 4.3 with this exercise in mind helpful when working on this exercise. 




From Corollary 4.2 we know that any unitary can be expressed as $U=e^{i\alpha}AXBXC$, so we can create the $V$ gates using two CNOTs and three one-qubit gates as $V=e^{i\alpha}AXBXC$. Then $V^\dagger = e^{-i\alpha}(AXBXC)^\dagger = e^{-i\alpha}C^\dagger X^\dagger B^\dagger X^\dagger A^\dagger = e^{-i\alpha}C^\dagger X B^\dagger X A^\dagger$. We can then construct the gate as so

<img width="829" height="216" alt="image" src="https://github.com/user-attachments/assets/63880985-2e67-4b03-9100-9f097c3e5315" />

However, this circuit contains 9 one-qubit gates and 8 CNOTs. So, let's think about how we could make this with fewer gates. We can get rid of the $U$ and $U^\dagger$ pairs for operators on the same wire that do not have a gate between them since $UU^\dagger = U^\dagger U = I$

<img width="816" height="196" alt="image" src="https://github.com/user-attachments/assets/75e2f1a9-8f9c-4cea-ab67-a6c78c3ce7ff" />

Now, let's see if we can merge any of the CNOTs.

For the three CNOTs between $B$ and $B^\dagger$ their effect is

$$\begin{aligned}
\ket{000} &\xrightarrow{CNOT_{bc}} \ket{000} &\xrightarrow{CNOT_{ab}} \ket{000} &\xrightarrow{CNOT_{bc}} \ket{000} \\
\ket{001} &\xrightarrow{CNOT_{bc}} \ket{001} &\xrightarrow{CNOT_{ab}} \ket{001} &\xrightarrow{CNOT_{bc}} \ket{001} \\
\ket{010} &\xrightarrow{CNOT_{bc}} \ket{011} &\xrightarrow{CNOT_{ab}} \ket{011} &\xrightarrow{CNOT_{bc}} \ket{010} \\
\ket{011} &\xrightarrow{CNOT_{bc}} \ket{010} &\xrightarrow{CNOT_{ab}} \ket{010} &\xrightarrow{CNOT_{bc}} \ket{011} \\
\ket{100} &\xrightarrow{CNOT_{bc}} \ket{100} &\xrightarrow{CNOT_{ab}} \ket{110} &\xrightarrow{CNOT_{bc}} \ket{111} \\
\ket{101} &\xrightarrow{CNOT_{bc}} \ket{101} &\xrightarrow{CNOT_{ab}} \ket{111} &\xrightarrow{CNOT_{bc}} \ket{110} \\
\ket{110} &\xrightarrow{CNOT_{bc}} \ket{111} &\xrightarrow{CNOT_{ab}} \ket{101} &\xrightarrow{CNOT_{bc}} \ket{101} \\
\ket{111} &\xrightarrow{CNOT_{bc}} \ket{110} &\xrightarrow{CNOT_{ab}} \ket{100} &\xrightarrow{CNOT_{bc}} \ket{100} \\
\end{aligned}$$

It can be seen that $CNOT_{bc}CNOT_{ab}CNOT_{bc} = CNOT_{ab}CNOT_{ac}$, since when $a=1$ both $b$ and $c$ flip, but otherwise their values are left unchanged. So, we can reduce at least one of the CNOT gates there. 

Now let's look at the three CNOTs between $B^\dagger$ and $B$. 

$$\begin{aligned}
\ket{000} &\xrightarrow{CNOT_{bc}} \ket{000} &\xrightarrow{CNOT_{ab}} \ket{000} &\xrightarrow{CNOT_{ac}} \ket{000} \\
\ket{001} &\xrightarrow{CNOT_{bc}} \ket{001} &\xrightarrow{CNOT_{ab}} \ket{001} &\xrightarrow{CNOT_{ac}} \ket{001} \\
\ket{010} &\xrightarrow{CNOT_{bc}} \ket{011} &\xrightarrow{CNOT_{ab}} \ket{011} &\xrightarrow{CNOT_{ac}} \ket{011} \\
\ket{011} &\xrightarrow{CNOT_{bc}} \ket{010} &\xrightarrow{CNOT_{ab}} \ket{010} &\xrightarrow{CNOT_{ac}} \ket{010} \\
\ket{100} &\xrightarrow{CNOT_{bc}} \ket{100} &\xrightarrow{CNOT_{ab}} \ket{110} &\xrightarrow{CNOT_{ac}} \ket{111} \\
\ket{101} &\xrightarrow{CNOT_{bc}} \ket{101} &\xrightarrow{CNOT_{ab}} \ket{111} &\xrightarrow{CNOT_{ac}} \ket{110} \\
\ket{110} &\xrightarrow{CNOT_{bc}} \ket{111} &\xrightarrow{CNOT_{ab}} \ket{101} &\xrightarrow{CNOT_{ac}} \ket{100} \\
\ket{111} &\xrightarrow{CNOT_{bc}} \ket{110} &\xrightarrow{CNOT_{ab}} \ket{100} &\xrightarrow{CNOT_{ac}} \ket{101} \\
\end{aligned}$$

It can be seen that $CNOT_{ac}CNOT_{ab}CNOT_{bc} = CNOT_{bc}CNOT_{ab}$, as I'll show below, so we can reduce another gate there.

$$\begin{aligned}
\ket{000} &\xrightarrow{CNOT_{ab}} \ket{000} &\xrightarrow{CNOT_{bc}} \ket{000}  \\
\ket{001} &\xrightarrow{CNOT_{ab}} \ket{001} &\xrightarrow{CNOT_{bc}} \ket{001}  \\
\ket{010} &\xrightarrow{CNOT_{ab}} \ket{010} &\xrightarrow{CNOT_{bc}} \ket{011} \\
\ket{011} &\xrightarrow{CNOT_{ab}} \ket{011} &\xrightarrow{CNOT_{bc}} \ket{010}  \\
\ket{100} &\xrightarrow{CNOT_{ab}} \ket{110} &\xrightarrow{CNOT_{bc}} \ket{111} \\
\ket{101} &\xrightarrow{CNOT_{ab}} \ket{111} &\xrightarrow{CNOT_{bc}} \ket{110} \\
\ket{110} &\xrightarrow{CNOT_{ab}} \ket{100} &\xrightarrow{CNOT_{bc}} \ket{100} \\
\ket{111} &\xrightarrow{CNOT_{ab}} \ket{101} &\xrightarrow{CNOT_{bc}} \ket{101} \\
\end{aligned}$$

Therefore, the circuit can be reduced to 6 CNOTs and 5 single qubit gates. 

<img width="632" height="192" alt="image" src="https://github.com/user-attachments/assets/3177406f-b4b0-48ce-9176-2e8f47d32869" />

Ok, so now we have too few single qubit gates. What are we missing? Looking at figure 4.9, we see that the circuit is configured a little differently than ours. The $CNOT_{ab}$ gates are pulled out to the end of the circuit and then additional single qubit gates are added to the $a$ and $b$ wires. So first let's move the $CNOT_{ab}$ gates.

<img width="650" height="189" alt="image" src="https://github.com/user-attachments/assets/9ededfb9-2e97-46c3-95e4-dac47d241a1a" />

I wrote the following python script to confirm that the circuits have been equivalent so far. This check initially shows that the circuit after the first simplification (of removing $A, A^\dagger, C^\dagger, C$ )resulted in a different circuit, but upon further review, one can see that this is due to a simplification error and all the circuits created so far are equivalent. 

```
from sympy import simplify, Matrix, symbols, exp, sin, cos, I
from sympy.physics.quantum import TensorProduct

theta_a, alpha_a, beta_a, phi_a = symbols('theta_a alpha_a beta_a phi_a', real=True)
theta_b, alpha_b, beta_b, phi_b = symbols('theta_b alpha_b beta_b phi_b', real=True)
theta_c, alpha_c, beta_c, phi_c = symbols('theta_c alpha_c beta_c phi_c', real=True)

A = exp(I*phi_a/2)*Matrix([[exp(I*alpha_a)*cos(theta_a), exp(I*beta_a)*sin(theta_a)], [-exp(-I*beta_a)*sin(theta_a), exp(-I*alpha_a)*cos(theta_a)]])
B = exp(I*phi_b/2)*Matrix([[exp(I*alpha_b)*cos(theta_b), exp(I*beta_b)*sin(theta_b)], [-exp(-I*beta_b)*sin(theta_b), exp(-I*alpha_b)*cos(theta_b)]])
C = exp(I*phi_c/2)*Matrix([[exp(I*alpha_c)*cos(theta_c), exp(I*beta_c)*sin(theta_c)], [-exp(-I*beta_c)*sin(theta_c), exp(-I*alpha_c)*cos(theta_c)]])
Identity = Matrix([[1, 0], [0, 1]])

Ac = TensorProduct(TensorProduct(Identity, Identity), A)
Bc = TensorProduct(TensorProduct(Identity, Identity), B)
Cc = TensorProduct(TensorProduct(Identity, Identity), C)

CNOTab = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0]])
CNOTbc = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])
CNOTac = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])

circuit1 = simplify(Ac @ CNOTac @ Bc @ CNOTac @ Cc @ CNOTab @ Cc.adjoint() @ CNOTbc @ Bc.adjoint() @ CNOTbc @ Ac.adjoint() @ CNOTab @ Ac @ CNOTbc @ Bc @ CNOTbc @ Cc) 
circuit2 = simplify(Ac @ CNOTac @ Bc @ CNOTac @ CNOTab @ CNOTbc @ Bc.adjoint() @ CNOTbc @ CNOTab @ CNOTbc @ Bc @ CNOTbc @ Cc)
circuit3 = simplify(Ac @ CNOTac @ Bc @ CNOTbc @ CNOTab @ Bc.adjoint() @ CNOTac @ CNOTab @ Bc @ CNOTbc @ Cc)
circuit4 = simplify(CNOTab @ CNOTab @ Ac @ CNOTac @ Bc @ CNOTbc @ Bc.adjoint() @ CNOTac @ Bc @ CNOTbc @ Cc)

check = simplify(circuit1 @ circuit4.adjoint())

print("circuit1 = circuit2: ")
print(circuit1 == circuit2)
print("circuit2 = circuit3: ")
print(circuit2 == circuit3)
print("circuit3 = circuit4: ")
print(circuit3 == circuit4)

print("Circuit check:")
print(check)


```

We can further simplify the circuit by removing the two $CNOT_{ab}$ gates, as they combind to create an identity operation. However, we now have 5 single qubit gates and 4 CNOT gates. 

<img width="556" height="180" alt="image" src="https://github.com/user-attachments/assets/e1c1345a-0563-40eb-9b0c-fa5e8e416c5b" />

Looking back at figure 4.9, we can see that (if we combine the last two gates on the $c$ wire) there are 5 single qubit gates on the $c$ wire, like our current circuit. The additional single qubit gates are on the other wires. So now let's think about what we may have left out; it is the global phase component of our unitary operators. From figure 4.5 we see that we can create the equivalent of a controlled phase shift gate with a single qubit gate on the control wire for a two wire circuit. What we need is to create the three wire equivalent that we can add to our circuit.

So, what we'd like to have is some circuit $G$ which applies a global phase when $a=\ket{1}$ and $b=\ket{1}$ as shown below

$$\begin{aligned}
\ket{000} &\xrightarrow{G} \ket{000} \\
\ket{001} &\xrightarrow{G} \ket{001} \\
\ket{010} &\xrightarrow{G} \ket{010} \\
\ket{011} &\xrightarrow{G} \ket{011} \\
\ket{100} &\xrightarrow{G} \ket{100} \\
\ket{101} &\xrightarrow{G} \ket{101} \\
\ket{110} &\xrightarrow{G} e^{i\alpha}\ket{110} \\
\ket{111} &\xrightarrow{G} e^{i\alpha}\ket{111} \\
\end{aligned}$$

Therefore

$$\begin{aligned}
G = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & e^{i\alpha} & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & e^{i\alpha} \end{bmatrix}
\end{aligned}$$

Let's say there is a single qubit gate $D$ such that

$$\begin{aligned}
D = \begin{bmatrix} 1 & 0 \\\ 0 & e^{i\alpha/2} \end{bmatrix}
\end{aligned}$$

Looking at the Toffoli gate on Wikipedia (since the one in the book actually has too many gates) I'm going to try this

<img width="505" height="194" alt="image" src="https://github.com/user-attachments/assets/64283b1d-c736-4635-a22f-f6b9d9e06d67" />

and confirm that it is valid below 

$$\begin{aligned}
CNOT_{ab}D_{a}D_{b}^\dagger CNOT_{ab}D_{b} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0  \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & e^{i\alpha} & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & e^{i\alpha} \end{bmatrix} = G
\end{aligned}$$

which was calculated using this python script

```
from sympy import Matrix, symbols, exp, I
from sympy.physics.quantum import TensorProduct

alpha_d = symbols('alpha_d', real=True)

D = Matrix([[1, 0], [0, exp(I*alpha_d/2)]])

Identity = Matrix([[1, 0], [0, 1]])

Db = TensorProduct(TensorProduct(Identity, D), Identity)
Da = TensorProduct(TensorProduct(D, Identity), Identity)

CNOTab = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0]])

circuit5 = CNOTab @ Da @ Db.adjoint() @ CNOTab @ Db

print(circuit5)

```

Thus, this is our final circuit which can be used to create any unitary gate with the appropriate selection of $A$, $B$, $C$, and $D$ gates. It contains 8 single qubit gates and 6 CNOT gates. Therefore, a $C^2(U)$ gate for any single qubit unitary $U$ can be constructed using at most eight one-qubit gates, and six controlled-NOT. 

<img width="697" height="219" alt="image" src="https://github.com/user-attachments/assets/828089cd-2ca5-4545-8790-6c277ba226fe" />

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.23 {#exercise-423}





From figure 4.6 we know we can create a $C^1(U)$ gate like this

<img width="363" height="123" alt="image" src="https://github.com/user-attachments/assets/9ef2c443-8b0a-4bb0-af02-f359fa79860b" />

We know that we can write $R_x(\theta)$ as

$$\begin{aligned}
R_x(\theta) &= R_z(-\pi/2)R_y(\theta)R_z(\pi/2) \\
&= R_z(-\pi/2)R_y(\theta/2)R_y(\theta/2)R_z(\pi/2) \\
&= R_z(-\pi/2)R_y(\theta/2)XR_y(-\theta/2)XR_z(\pi/2)
\end{aligned}$$

And so a gate can be constructed with $A= R_z(-\pi/2)R_y(\theta/2)$, $B=R_y(-\theta/2)$, $C=R_z(\pi/2)$, and no $D$ gate. 

Now we are asked if we can reduce the number of single qubit gates needed from three to two. I don't think we can do that for $R_x$ since we need to use decomposition to write it as $R_y$ and $R_z$. 

For $R_y$ we have

$$\begin{aligned}
R_y(\theta) &= R_y(\theta/2)R_y(\theta/2) \\
&= R_y(\theta/2)XR_y(-\theta/2)X
\end{aligned}$$

And so a gate can be constructed with $A= R_y(\theta/2)$, $B=R_y(-\theta/2)$, no $C$ gate, and no $D$ gate. This uses two single qubit gates.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.24 {#exercise-424}





I wrote the following python code to calculate the matrix representation of the circuit in Figure 4.9.

```
from sympy import simplify, Matrix, exp, I, pi, sqrt
from sympy.physics.quantum import TensorProduct


T = Matrix([[1, 0], [0, exp(I*pi/4)]])
S = Matrix([[1, 0], [0, I]])
H = 1/sqrt(2)*Matrix([[1, 1], [1, -1]])

Identity = Matrix([[1, 0], [0, 1]])

Tc = TensorProduct(TensorProduct(Identity, Identity), T)
Tb = TensorProduct(TensorProduct(Identity, T), Identity)
Ta = TensorProduct(TensorProduct(T, Identity), Identity)

Sb = TensorProduct(TensorProduct(Identity, S), Identity)

Hc = TensorProduct(TensorProduct(Identity, Identity), H)


CNOTab = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0]])
CNOTbc = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])
CNOTac = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])


circuit = simplify(Hc @ CNOTbc @ Tc.adjoint() @ CNOTac @ Tc @ CNOTbc @ Tc.adjoint() @ CNOTac @ Tc @ Tb.adjoint() @ Hc @ CNOTab @ Tb.adjoint() @ CNOTab @ Sb @ Ta) 

print("Circuit:")
print(circuit)

```


The code produced the following 

$$\begin{aligned}
Toffoli = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \end{bmatrix}
\end{aligned}$$

Which is the same as the matrix representation of the Toffoli gate. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.25 {#exercise-425}






(1) This first part we are to construct a Fredkin gate with three Toffoli gates. This is something we already did in [exercise 3.32](https://adj59-dev.github.io/qcqi/chapter-3/#exercise-332). I changed the following one up a little so that the a wire is the control wire to match the matrix shown later in this exercise.

<img width="696" height="192" alt="image" src="https://github.com/user-attachments/assets/cacb8cf7-10df-4796-be53-080234918dac" />


(2) Now we are asked to show that the first and last gates can be replaced by CNOT gates. We already have the matrix representation for Toffoli gate with a and b as the control wires, now we need to find the matrix representation for a Toffoli gate with a and c as the control wires.

$$\begin{aligned}
\ket{000} &\xrightarrow{Toffoli_{acb}} \ket{000} \\
\ket{001} &\xrightarrow{Toffoli_{acb}} \ket{001} \\
\ket{010} &\xrightarrow{Toffoli_{acb}} \ket{010} \\
\ket{011} &\xrightarrow{Toffoli_{acb}} \ket{011} \\
\ket{100} &\xrightarrow{Toffoli_{acb}} \ket{100} \\
\ket{101} &\xrightarrow{Toffoli_{acb}} \ket{111} \\
\ket{110} &\xrightarrow{Toffoli_{acb}} \ket{110} \\
\ket{111} &\xrightarrow{Toffoli_{acb}} \ket{101} \\
\end{aligned}$$

$$\begin{aligned}
Toffoli_{acb} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \end{bmatrix}
\end{aligned}$$

If we replace the first and last Toffoli gates by $CNOT_{bc}$ gates, we get the same effect, i.e. $Toffoli_{abc} Toffoli_{acb} Toffoli_{abc} = CNOT_{bc} Toffoli_{acb} CNOT_{bc}$

<img width="712" height="196" alt="image" src="https://github.com/user-attachments/assets/d10d6a14-ab6a-4a59-bfbb-dfd1e06f7c87" />

I confirm this circuit has the same effect using this python script.

```

from sympy import simplify, Matrix


CNOTab = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0]])
CNOTbc = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])
CNOTac = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])

Toffoliabc =  Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])
Toffoliacb =  Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, 1, 0, 0]])

circuit1 = simplify(Toffoliabc @ Toffoliacb @ Toffoliabc) 
circuit2 = simplify(CNOTbc @ Toffoliacb @ CNOTbc) 

print("Circuit1:")
print(circuit1)
print("Circuit2:")
print(circuit2)
print("Circuit1 = Circuit2: ")
print(circuit1 == circuit2)

```

(3) Now we need to replace the middle Toffoli gate with the circuit in figure 4.8

<img width="721" height="183" alt="image" src="https://github.com/user-attachments/assets/6503d390-ebc5-4ab8-ab28-69dcb1d78ad9" />


Here, $V = \frac{(1-i)(I + iX)}{2}$ and $V^2 = X$. We could combine the first two gates (since they both only interact with the b and c wire) to form a single two qubit gate. This will give us a circuit with only 6 two qubit gates. 

(4) In order to reduce the number of gates further, let's think about different circuit identities that we might be able to use. Since we know that $VV^\dagger = V^\dagger V=I$ we can insert $VV^\dagger$ or $V^\dagger V$ wherever we'd like. We also know that $V^2=X$, therefore $V_{ab}=V_{ab}V_{ab}V_{ab}^\dagger =CNOT_{ab}V_{ab}^\dagger$, and so we can write the equivalent circuit

<img width="699" height="183" alt="image" src="https://github.com/user-attachments/assets/96adae4b-d974-470d-a960-79bb4d78ea9c" />

We can swap $CNOT_{ac}$ and $V_{ab}^\dagger$

<img width="699" height="196" alt="image" src="https://github.com/user-attachments/assets/b34497c1-3c6b-4fc9-81b3-f7279ccef4c4" />

Now let's see if we can rewrite $CNOT_{bc}CNOT_{ab}CNOT_{ac}$ as something that we will be able to combine to have fewer gates. Using the below python script, you can see that $CNOT_{bc}CNOT_{ab}CNOT_{ac} = CNOT_{ab}CNOT_{bc}$ 

```
from sympy import simplify, Matrix


CNOTab = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0]])
CNOTbc = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])
CNOTac = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])

circuit1 = simplify(CNOTbc @ CNOTab @ CNOTac) 
circuit2 = simplify(CNOTab @ CNOTbc) 

print("Circuit1:")
print(circuit1)
print("Circuit2:")
print(circuit2)
print("Circuit1 = Circuit2: ")
print(circuit1 == circuit2)

```

Therefore, our circuit can be constructed like so

<img width="702" height="183" alt="image" src="https://github.com/user-attachments/assets/8f5d8352-5587-4244-9637-da14af3e1552" />

We can swap $V_{cb}^\dagger$ and $V_{ab}^\dagger$. If you then combine the $V_{cb}CNOT_{bc}$ gates and $CNOT_{bc}V_{cb}^\dagger$ gates, as shown below, you have five gates. 

<img width="709" height="210" alt="image" src="https://github.com/user-attachments/assets/f068f0f4-82c9-4b9a-b75b-c1e49ba9c7eb" />


I wrote a python script to confirm that the above circuit is equivalent to a Fredkin gate.

```
from sympy import simplify, Matrix, I


CNOTab = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0]])
CNOTbc = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])
CNOTac = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])

Toffoliabc =  Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])
Toffoliacb =  Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, 1, 0, 0]])

V =simplify((1 - I)*( Matrix([[1, 0], [0, 1]]) + I*Matrix([[0, 1], [1, 0]]) )/2)

Vab = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, V[0,0], 0, V[0,1], 0], [0, 0, 0, 0, 0, V[0,0], 0, V[0,1]], [0, 0, 0, 0, V[1,0], 0, V[1,1], 0], [0, 0, 0, 0, 0, V[1,0], 0, V[1,1]]])
Vcb = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, V[0,0], 0, V[0,1], 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, V[1,0], 0, V[1,1], 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, V[0,0], 0, V[0,1]], [0, 0, 0, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, V[1,0], 0, V[1,1]]])

circuit1 = simplify(Toffoliabc @ Toffoliacb @ Toffoliabc) 
circuit3 = simplify(CNOTab @ CNOTbc @ Vcb.adjoint() @ Vab.adjoint() @ CNOTac @ Vcb @ CNOTbc)

print("Circuit1:")
print(circuit1)
print("Circuit3:")
print(circuit3)
print("Circuit1 = Circuit3: ")
print(circuit1 == circuit3)

```

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |





### Exercise 4.26 {#exercise-426}

In this exercise we are asked to show that a given circuit differs from a Toffoli gate only by a relative phase. The drawing of the circuit has several $R_y(\theta)$ single bit operations, but it is a little unclear (at least in my book) what $\theta$ is supposed to be, as it is written as $\pi/$. Through some trial and error, I think it is supposed to be $\frac{\pi}{4}$. 




I wrote the following python script to calculate the matrix representation of the given circuit.

```
from sympy import simplify, Matrix, pi, cos, sin
from sympy.physics.quantum import TensorProduct


Identity = Matrix([[1, 0], [0, 1]])

Ryp = Matrix([[cos(pi/8), -sin(pi/8)], [sin(pi/8), cos(pi/8)]])
Ryn = Matrix([[cos(-pi/8), -sin(-pi/8)], [sin(-pi/8), cos(-pi/8)]])

Rypc = TensorProduct(TensorProduct(Identity, Identity), Ryp)
Rync = TensorProduct(TensorProduct(Identity, Identity), Ryn)


CNOTab = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 1, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0]])
CNOTbc = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])
CNOTac = Matrix([[1, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 1, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 1], [0, 0, 0, 0, 0, 0, 1, 0]])


circuit = simplify(Rync @ CNOTbc @ Rync @ CNOTac @ Rypc @ CNOTbc @ Rypc) 

print("Circuit:")
print(circuit)

```

The resulting matrix is

$$\begin{aligned}
C = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & -1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \end{bmatrix}
\end{aligned}$$

This is the same as the Toffoli gate matrix except for a factor of -1 in the 6th row, which translates to a phase shift of $e^{i\pi}$ for $\ket{101}$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.27 {#exercise-427}






The matrix representation of the circuit given by equation 4.31 is

$$\begin{aligned}
C = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \end{bmatrix}
\end{aligned}$$

Let's look at what this circuit is doing

$$\begin{aligned}
\ket{000} &\xrightarrow{C} \ket{000} \\
\ket{001} &\xrightarrow{C} \ket{010} \\
\ket{010} &\xrightarrow{C} \ket{011} \\
\ket{011} &\xrightarrow{C} \ket{100} \\
\ket{100} &\xrightarrow{C} \ket{101} \\
\ket{101} &\xrightarrow{C} \ket{110} \\
\ket{110} &\xrightarrow{C} \ket{111} \\
\ket{111} &\xrightarrow{C} \ket{001} \\
\end{aligned}$$

and think about how we can write this out as a Boolean formula.  

$$\begin{aligned}
\ket{a,b,c} &\xrightarrow{C} \ket{(b \land c)\oplus a, c \oplus b, c \oplus (((b \land c)\oplus a) \lor (c \oplus b))} \\
&= \ket{(b \land c)\oplus a, c \oplus b, c \oplus ((b \land c)\oplus a) \oplus (c \oplus b) \oplus (((b \land c)\oplus a)\land (c \oplus b))}
\end{aligned}$$

Looking at the above formula, one can see that the a wire effect can be achived with a Toffoli gate with the b and c wires as the control wires. The b wire effect can be achieved with a $CNOT_{cb}$ gate. The c wire effect can be achieved with two CNOT and one additional Toffoli gates. The full circuit is shown below.

<img width="759" height="183" alt="image" src="https://github.com/user-attachments/assets/af69a9ec-58de-4612-afcb-3225c14dcbc5" />

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.28 {#exercise-428}

 




From [exercise 4.21](#exercise-421) we know that we can construct a $C^2(U)$ gate as shown below

<img width="749" height="181" alt="image" src="https://github.com/user-attachments/assets/33962739-1a7f-4c15-874f-a08f56c14250" />

Using a $C^1(V)$ gate, $C^1(V^\dagger)$ gate, $C^2(V)$ gate, and Toffoli gates we can construct a $C^3(U)$ gate as shown below

<img width="752" height="240" alt="image" src="https://github.com/user-attachments/assets/7bda8e0b-6120-4be3-a85b-767f794f2598" />

Similarly, we can create $C^4(U)$ gates 

<img width="777" height="290" alt="image" src="https://github.com/user-attachments/assets/0f73294e-93f3-4469-a4b1-916c278884be" />

and $C^5(U)$ gates

<img width="774" height="364" alt="image" src="https://github.com/user-attachments/assets/f8ea8ba9-671e-4c42-a029-43c0d15bea05" />

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.29 & 4.30 {#exercise-429}

Since exercises 4.29 and 4.30 are closely related, I've combined them here. 




From the previous exercise we know that

<img width="794" height="372" alt="image" src="https://github.com/user-attachments/assets/62b8103c-b167-4703-9ebd-fc715846d4a8" />

Following a similar calculation as was done in [exercise 4.22](#exercise-422), where $V=e^{i\alpha}AXBXC$ and $D$ is the phase gate. 

<img width="844" height="370" alt="image" src="https://github.com/user-attachments/assets/997e42f0-3973-4ce7-ad63-7e9755806543" />

$AA^\dagger = I$ and so can be removed from the circuit.

<img width="833" height="368" alt="image" src="https://github.com/user-attachments/assets/70cb8bc2-d95e-41f2-8ff7-9740c0823967" />


This circuit has $6$ single qubit gates, 4 $CNOT$ gates, and 3 $C^{n-1}$ gates. Therefore, the total number of gates for a $C^n$ gate is

$$\begin{aligned}
N(C^n) &= 10 + 3 N(C^{n-1}) \\
&= 10 + 3(10 + 3 N(C^{n-2})) \\
&= 3^{n-2}N(C^2) + 10\sum_{i=0}^{n-3} 3^i \\
&= 3^{n-2}N(C^2) + 10 \frac{1-3^{n-3+1}}{1 - 3} \\
&= 3^{n-2}N(C^2) + 5 (3^{n-2}-1) \\
&= 3^{n-2}(N(C^2) + 5) - 5
\end{aligned}$$

This would mean the circuit contains $O(3^n)$ gates, which is not in $O(n^2)$. However, this calculation is done with the assumption that the $C^{n-1}(X)$ gates cost the same as other $C^{n-1}(V)$ gate, if they are less costly, say $O(n)$, then the total number of gates for a $C^n$ gate is

$$\begin{aligned}
N(C^n) &= 10 + 2 O(n) + N(C^{n-1}) \\
&= 10 + 2 O(n) + (10 + 2 O(n-1) + N(C^{n-2})) \\
&= 2\sum_{k=2}^n O(k) + (n-2)10 + N(C^2)\\
&= O(n^2) + O(n) + O(1)
\end{aligned}$$

This would be $O(n^2)$. So we need to find a different way to make these $C^{n-1}(X)$ circuits with $O(n)$ gates and no work bits. If we can do this, we can make any $C^n(U)$ gate with $O(n^2)$ gates. 

Thinking back to [exercise 4.26](#exercise-426), we know that we can approximate a controlled X gate up to a relative phase by using the following circuit,

<img width="707" height="361" alt="image" src="https://github.com/user-attachments/assets/0a23672b-1d44-4b1d-83e7-a958ce4f9617" />

where $E=R_y(\pi/4)$. This circuit only has one $C^{n-1}$ gate and so will not grow exponentially with $n$. The number of gates is given by

$$\begin{aligned}
N(C^n) &= 6 + N(C^{n-1})\\
&= 6 + (6 + N(C^{n-2}) \\
&= 6(n-2) + N(C^2)
\end{aligned}$$

And so the circuit contains $O(n)$ gates. However, this circuit is different from a controlled-X gate by relative phases. Looking back at the non-approximated circuit one sees that there are two $C^{n-1} NOT$ gates. Is it possible to replace these $C^{n-1} NOT$ gates with this approximation and have the relative phase difference cancel out? 

Let's first look at the $C^3(X)$ case, where $V = \frac{(1-i)(I+iX)}{2}$

<img width="449" height="238" alt="image" src="https://github.com/user-attachments/assets/f58ae973-7333-4b95-b020-724ba7c1fa1a" />

Now let's see if we can substitute in the approximation for the Toffoli gates.

<img width="820" height="254" alt="image" src="https://github.com/user-attachments/assets/a5db94ad-68b4-4c9e-bc2e-dc963342396b" />

Let's find the matrix representation for the different gates so we can calculate their effect. 

For $V_{cd}$ 

$$\begin{aligned}
\ket{0000} &\xrightarrow{V_{cd}} \ket{0000} \\
\ket{0001} &\xrightarrow{V_{cd}} \ket{0001} \\
\ket{0010} &\xrightarrow{V_{cd}} V_d \ket{0010} \\
\ket{0011} &\xrightarrow{V_{cd}} V_d \ket{0011} \\
\ket{0100} &\xrightarrow{V_{cd}} \ket{0100} \\
\ket{0101} &\xrightarrow{V_{cd}} \ket{0101} \\
\ket{0110} &\xrightarrow{V_{cd}} V_d \ket{0110} \\
\ket{0111} &\xrightarrow{V_{cd}} V_d \ket{0111} \\
\ket{1000} &\xrightarrow{V_{cd}} \ket{1000} \\
\ket{1001} &\xrightarrow{V_{cd}} \ket{1001} \\
\ket{1010} &\xrightarrow{V_{cd}} V_d \ket{1010} \\
\ket{1011} &\xrightarrow{V_{cd}} V_d \ket{1011} \\
\ket{1100} &\xrightarrow{V_{cd}} \ket{1100} \\
\ket{1101} &\xrightarrow{V_{cd}} \ket{1101} \\
\ket{1110} &\xrightarrow{V_{cd}} V_d \ket{1110} \\
\ket{1111} &\xrightarrow{V_{cd}} V_d \ket{1111} \\
\end{aligned}$$

$$\begin{aligned}
V_{cd} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & v_{00} & v_{01} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & v_{10} & v_{11} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{00} & v_{01} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & v_{10} & v_{11} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & v_{00} & v_{01} & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & v_{10} & v_{11} & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & v_{00} & v_{01} \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & v_{10} & v_{11} \end{bmatrix}
\end{aligned}$$

For $V_{abd}$ 

$$\begin{aligned}
\ket{0000} &\xrightarrow{V_{abd}} \ket{0000} \\
\ket{0001} &\xrightarrow{V_{abd}} \ket{0001} \\
\ket{0010} &\xrightarrow{V_{abd}} \ket{0010} \\
\ket{0011} &\xrightarrow{V_{abd}} \ket{0011} \\
\ket{0100} &\xrightarrow{V_{abd}} \ket{0100} \\
\ket{0101} &\xrightarrow{V_{abd}} \ket{0101} \\
\ket{0110} &\xrightarrow{V_{abd}} \ket{0110} \\
\ket{0111} &\xrightarrow{V_{abd}} \ket{0111} \\
\ket{1000} &\xrightarrow{V_{abd}} \ket{1000} \\
\ket{1001} &\xrightarrow{V_{abd}} \ket{1001} \\
\ket{1010} &\xrightarrow{V_{abd}} \ket{1010} \\
\ket{1011} &\xrightarrow{V_{abd}} \ket{1011} \\
\ket{1100} &\xrightarrow{V_{abd}} V_d \ket{1100} \\
\ket{1101} &\xrightarrow{V_{abd}} V_d \ket{1101} \\
\ket{1110} &\xrightarrow{V_{abd}} V_d \ket{1110} \\
\ket{1111} &\xrightarrow{V_{abd}} V_d \ket{1111} \\
\end{aligned}$$

$$\begin{aligned}
V_{abd} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & v_{00} & v_{01} & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & v_{10} & v_{11} & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & v_{00} & v_{01} \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & v_{10} & v_{11} \end{bmatrix}
\end{aligned}$$

For $CNOT_{bc}$

$$\begin{aligned}
\ket{0000} &\xrightarrow{CNOT_{bc}} \ket{0000} \\
\ket{0001} &\xrightarrow{CNOT_{bc}} \ket{0001} \\
\ket{0010} &\xrightarrow{CNOT_{bc}} \ket{0010} \\
\ket{0011} &\xrightarrow{CNOT_{bc}} \ket{0011} \\
\ket{0100} &\xrightarrow{CNOT_{bc}} \ket{0110} \\
\ket{0101} &\xrightarrow{CNOT_{bc}} \ket{0111} \\
\ket{0110} &\xrightarrow{CNOT_{bc}} \ket{0100} \\
\ket{0111} &\xrightarrow{CNOT_{bc}} \ket{0101} \\
\ket{1000} &\xrightarrow{CNOT_{bc}} \ket{1000} \\
\ket{1001} &\xrightarrow{CNOT_{bc}} \ket{1001} \\
\ket{1010} &\xrightarrow{CNOT_{bc}} \ket{1010} \\
\ket{1011} &\xrightarrow{CNOT_{bc}} \ket{1011} \\
\ket{1100} &\xrightarrow{CNOT_{bc}} \ket{1110} \\
\ket{1101} &\xrightarrow{CNOT_{bc}} \ket{1111} \\
\ket{1110} &\xrightarrow{CNOT_{bc}} \ket{1100} \\
\ket{1111} &\xrightarrow{CNOT_{bc}} \ket{1101} \\
\end{aligned}$$

$$\begin{aligned}
CNOT_{bc} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \end{bmatrix}
\end{aligned}$$

For $CNOT_{ac}$

$$\begin{aligned}
\ket{0000} &\xrightarrow{CNOT_{ac}} \ket{0000} \\
\ket{0001} &\xrightarrow{CNOT_{ac}} \ket{0001} \\
\ket{0010} &\xrightarrow{CNOT_{ac}} \ket{0010} \\
\ket{0011} &\xrightarrow{CNOT_{ac}} \ket{0011} \\
\ket{0100} &\xrightarrow{CNOT_{ac}} \ket{0100} \\
\ket{0101} &\xrightarrow{CNOT_{ac}} \ket{0101} \\
\ket{0110} &\xrightarrow{CNOT_{ac}} \ket{0110} \\
\ket{0111} &\xrightarrow{CNOT_{ac}} \ket{0111} \\
\ket{1000} &\xrightarrow{CNOT_{ac}} \ket{1010} \\
\ket{1001} &\xrightarrow{CNOT_{ac}} \ket{1011} \\
\ket{1010} &\xrightarrow{CNOT_{ac}} \ket{1000} \\
\ket{1011} &\xrightarrow{CNOT_{ac}} \ket{1001} \\
\ket{1100} &\xrightarrow{CNOT_{ac}} \ket{1110} \\
\ket{1101} &\xrightarrow{CNOT_{ac}} \ket{1111} \\
\ket{1110} &\xrightarrow{CNOT_{ac}} \ket{1100} \\
\ket{1111} &\xrightarrow{CNOT_{ac}} \ket{1101} \\
\end{aligned}$$

$$\begin{aligned}
CNOT_{ac} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \end{bmatrix}
\end{aligned}$$


I used the following script to calculate the circuit and check if it matches a $C^3(X)$ gate, which it does.  So this looks like a viable solution. 

```

from sympy import simplify, Matrix, sin, cos, I, pi
from sympy.physics.quantum import TensorProduct



Identity = Matrix([[1, 0], [0, 1]])
X = Matrix([[0, 1], [1, 0]])

V = (1-I)*(Identity + I*X)/2

Ryp = Matrix([[cos(pi/8), -sin(pi/8)], [sin(pi/8), cos(pi/8)]])
Ryn = Matrix([[cos(-pi/8), -sin(-pi/8)], [sin(-pi/8), cos(-pi/8)]])
ID = TensorProduct(Identity, Identity, Identity, Identity)

Rypc = TensorProduct(Identity, Identity, Ryp, Identity)
Rync = TensorProduct(Identity, Identity, Ryn, Identity)


CNOTbc=Matrix([[1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0],[0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1],[0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0]])
CNOTac=Matrix([[1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0],[0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1],[0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0]])
CCNOTabc=Matrix([[1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1],[0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0]])

Vabd=Matrix([[1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,V[0,0],V[0,1],0,0],[0,0,0,0,0,0,0,0,0,0,0,0,V[1,0],V[1,1],0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,V[0,0],V[0,1]],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,V[1,0],V[1,1]]])
Vcd=Matrix([[1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,V[0,0],V[0,1],0,0,0,0,0,0,0,0,0,0,0,0],[0,0,V[1,0],V[1,1],0,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,V[0,0],V[0,1],0,0,0,0,0,0,0,0],[0,0,0,0,0,0,V[1,0],V[1,1],0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,V[0,0],V[0,1],0,0,0,0],[0,0,0,0,0,0,0,0,0,0,V[1,0],V[1,1],0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,V[0,0],V[0,1]],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,V[1,0],V[1,1]]])

approx = Rync @ CNOTbc @ Rync @ CNOTac @ Rypc @ CNOTbc @ Rypc 

circuit1 = simplify(Vabd @ approx @ Vcd.adjoint() @ approx @ Vcd)
circuit2 = simplify(Vabd @ CCNOTabc @ Vcd.adjoint() @ CCNOTabc @ Vcd)

print("Circuit:")
print(circuit1)
print("Equal to CCCNOT gate: ")
print(circuit1 == circuit2)

```

It makes sense that these phases cancel out, since our approximation is equal to $approx = D \cdot C^{n-1}(X)$, where $D$ is a diagonal relative-phase error. Then the circuit is

$$\begin{aligned}
C^{n}(U) &= V (D C^{n-1}(X)) V^\dagger (D C^{n-1}(X)) V \\
&= DD (VC^{n-1}(X) V^\dagger C^{n-1}(X) V) & \text{since $D$ is diagonal} \\
&= VC^{n-1}(X) V^\dagger C^{n-1}(X) V & \text{$D$s cancel} \\
&= C^{n}(U) 
\end{aligned}$$

This calculation will hold for all $n>3$.

So the $C^n(X)$ circuit will be as shown below, where the $C^{n-2}(X)$ gates between the $E$ and $E^\dagger$ gates can be recursively decomposed into Toffoli, CNOT and single bit gates using the approximation $C^{n-2}(X) = E^\dagger \cdot CNOT_{(c_{n-2})(c_{n})} \cdot E^\dagger \cdot C^{n-3}(X) \cdot E \cdot CNOT_{(c_{n-2})(c_{n})} \cdot E$. This will construct a circuit using $O(n^2)$ gates. 

<img width="824" height="347" alt="image" src="https://github.com/user-attachments/assets/f2303b42-6afd-4c94-bf2d-8c7d61990df3" />


This decomposition is valid for any $C^n(U)$ gate by selecting the appropriate $V$ gates. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.31 {#exercise-431}






I used the following script to confirm the identities. 

```
from sympy import simplify, Matrix, sin, cos, I, exp, symbols
from sympy.physics.quantum import TensorProduct

theta = symbols('theta', real=True)

Identity = Matrix([[1, 0], [0, 1]])
X = Matrix([[0, 1], [1, 0]])
Y = Matrix([[0, -I], [I, 0]])
Z = Matrix([[1, 0], [0, -1]])

Rz = Matrix([[exp(-I*theta/2), 0], [0, exp(I*theta/2)]])
Rx = Matrix([[cos(theta/2), -I*sin(theta/2)], [-I*sin(theta/2), cos(theta/2)]])

C = Matrix([[1,0,0,0],[0,1,0,0],[0,0,0,1],[0,0,1,0]])

print("CX1C = X1X2: ")
print(simplify(C @ TensorProduct(X, Identity) @ C) == simplify(TensorProduct(X, Identity) @ TensorProduct(Identity, X)))
print("CY1C = Y1X2: ")
print(simplify(C @ TensorProduct(Y, Identity) @ C) == simplify(TensorProduct(Y, Identity) @ TensorProduct(Identity, X)))
print("CZ1C = Z1: ")
print(simplify(C @ TensorProduct(Z, Identity) @ C) == simplify(TensorProduct(Z, Identity)))
print("CX2C = X2")
print(simplify(C @ TensorProduct(Identity, X) @ C) == simplify(TensorProduct(Identity, X)))
print("CY2C = Z1Y2: ")
print(simplify(C @ TensorProduct(Identity, Y) @ C) == simplify(TensorProduct(Z, Identity) @ TensorProduct(Identity, Y)))
print("CZ2C = Z1Z2: ")
print(simplify(C @ TensorProduct(Identity, Z) @ C) == TensorProduct(Z, Identity) @ TensorProduct(Identity, Z))
print("Rz1(theta)C = CRz1(theta): ")
print(simplify(TensorProduct(Rz, Identity) @ C) == simplify(C @ TensorProduct(Rz, Identity)))
print("Rx2(theta)C = C Rx2(theta): ")
print(simplify(TensorProduct(Identity, Rx) @ C) == simplify(C @ TensorProduct(Identity, Rx)))

```

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## Measurement

### Exercise 4.32 {#exercise-432}






The density matrix for a two qubit system after measurement is given by

$$\begin{aligned}
\rho' &= \sum_{k=0,1} P_k \rho P_k \\
&= P_0 \rho P_0 + P_1 \rho P_1 
\end{aligned}$$

The reduced density matrix for the first qubit is given by 

$$\begin{aligned}
tr_2(\rho') &= tr_2(P_0 \rho P_0 + P_1 \rho P_1) \\
&= tr_2(P_0 \rho P_0) + tr_2(P_1 \rho P_1) \\
&= tr_2(\rho P_0^2) + tr_2(\rho P_1^2) \\
&= tr_2(\rho P_0) + tr_2(\rho P_1) \\
&= tr_2(\rho( P_0 + P_1)) \\
&= tr_2(\rho I) \\
&= tr_2(\rho ) \\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.33 {#exercise-433}






The matrix representation of the circuit is given by

$$\begin{aligned}
C &=  H_{a} CNOT_{ab}\\
&= \frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 0 & 0 & 1 \\\ 0 & 1 & 1 & 0 \\\ 1 & 0 & 0 & -1 \\\ 0 & 1 & -1 & 0 \end{bmatrix} \\
\end{aligned}$$

Looking at the matrix we see that the circuit has this effect on the computational basis

$$\begin{aligned}
\ket{00} \xrightarrow{C} \frac{1}{\sqrt{2}}(\ket{00} + \ket{10}) \\
\ket{01} \xrightarrow{C} \frac{1}{\sqrt{2}}(\ket{01} + \ket{11}) \\
\ket{10} \xrightarrow{C} \frac{1}{\sqrt{2}}(\ket{01} - \ket{11}) \\
\ket{11} \xrightarrow{C} \frac{1}{\sqrt{2}}(\ket{00} - \ket{10}) \\
\end{aligned}$$

Therefore the effect on a Bell state basis is

$$\begin{aligned}
\ket{\beta_{00}} = \frac{1}{\sqrt{2}}(\ket{00} + \ket{11}) \xrightarrow{C} \frac{1}{2}(\ket{00} + \ket{10} + \ket{00} - \ket{10}) = \ket{00} \\
\ket{\beta_{01}} = \frac{1}{\sqrt{2}}(\ket{01} + \ket{10}) \xrightarrow{C} \frac{1}{2}(\ket{01} + \ket{11} + \ket{01} - \ket{11}) = \ket{01} \\
\ket{\beta_{10}} = \frac{1}{\sqrt{2}}(\ket{00} - \ket{11}) \xrightarrow{C} \frac{1}{2}(\ket{00} + \ket{10} - \ket{00} + \ket{10}) = \ket{10} \\
\ket{\beta_{11}} = \frac{1}{\sqrt{2}}(\ket{01} - \ket{10}) \xrightarrow{C} \frac{1}{2}(\ket{01} + \ket{11} - \ket{01} + \ket{11}) = \ket{11} \\
\end{aligned}$$

So the measurement operator can be written as

$$\begin{aligned}
M_{00} = \ket{00}\bra{\beta_{00}} \\
M_{01} = \ket{01}\bra{\beta_{01}} \\
M_{10} = \ket{10}\bra{\beta_{10}} \\
M_{11} = \ket{11}\bra{\beta_{11}}
\end{aligned}$$

and the POVM elements given by $E_m = M_m^\dagger M_m$ are

$$\begin{aligned}
E_{00} = \ket{\beta_{00}}\bra{\beta_{00}} \\
E_{01} = \ket{\beta_{01}}\bra{\beta_{01}} \\
E_{10} = \ket{\beta_{10}}\bra{\beta_{10}} \\
E_{11} = \ket{\beta_{11}}\bra{\beta_{11}}
\end{aligned}$$

These POVM elements are projectors onto the Bell states. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.34 {#exercise-434}






Let's write $U$ as

$$\begin{aligned}
U = \begin{bmatrix} u_{00} & u_{01} \\\ u_{10} & u_{11} \end{bmatrix}
\end{aligned}$$

Then the matrix representation of the circuit is given by 

$$\begin{aligned}
C = \frac{1}{2} \begin{bmatrix} u_{00} + 1 & u_{01} & 1 - u_{00} & -u_{01} \\\ u_{10} & u_{11} + 1 & -u_{10} & 1 - u_{11} \\\ 1 - u_{00} & -u_{01} & u_{00} + 1 & u_{01} \\\ -u_{10} & 1-u_{11} & u_{10} & u_{11} + 1 \end{bmatrix}
\end{aligned}$$

and so if the input into the circuit is 

$$\begin{aligned}
\ket{0} \otimes \ket{\psi_{in}} &= \begin{bmatrix} 1 \\\ 0 \end{bmatrix} \otimes \begin{bmatrix} \psi_{0} \\\ \psi_{1} \end{bmatrix} \\\
&= \begin{bmatrix} \psi_{0} \\\ \psi_{1} \\\ 0 \\\ 0 \end{bmatrix}
\end{aligned}$$

then the output is

$$\begin{aligned}
C (\ket{0} \otimes \ket{\psi_{in}}) &= \frac{1}{2} \begin{bmatrix} u_{00} + 1 & u_{01} & 1 - u_{00} & -u_{01} \\\ u_{10} & u_{11} + 1 & -u_{10} & 1 - u_{11} \\\ 1 - u_{00} & -u_{01} & u_{00} + 1 & u_{01} \\\ -u_{10} & 1-u_{11} & u_{10} & u_{11} + 1 \end{bmatrix}\begin{bmatrix} \psi_{0} \\\ \psi_{1} \\\ 0 \\\ 0 \end{bmatrix} \\
&=  \frac{1}{2}\begin{bmatrix}  \psi_{0} + (u_{00}\psi_{0} + u_{01}\psi_{1}) \\\ \psi_{1} + (u_{10} \psi_{0} + u_{11}\psi_{1}) \\\ \psi_{0} - (u_{00}\psi_{0} + u_{01}\psi_{1}) \\\ \psi_{1} - (u_{10}\psi_{0} + u_{11}\psi_{1}) \end{bmatrix} \\
&= \frac{1}{2}\begin{bmatrix}  (I + U)\begin{bmatrix} \psi_{0} \\\ \psi_{1} \end{bmatrix}  \\\ (I - U) \begin{bmatrix} \psi_{0} \\\ \psi_{1} \end{bmatrix} \end{bmatrix} \\
&= \begin{bmatrix}  P_{+}\begin{bmatrix} \psi_{0} \\\ \psi_{1} \end{bmatrix}  \\\ P_{-}\begin{bmatrix} \psi_{0} \\\ \psi_{1} \end{bmatrix} \end{bmatrix} & \text{exercise 2.60} \\
&= \ket{0} \otimes P_{+}\ket{\psi_{in}} + \ket{1} \otimes P_{-}\ket{\psi_{in}} \\
&= \sqrt{p(+)}\ket{0} \otimes \ket{\psi_{+}} + \sqrt{p(-)}\ket{1} \otimes \ket{\psi_{-}}
\end{aligned}$$

Where $p(\pm) = \braket{\psi_{in} \vert P_{\pm} \vert \psi_{in}}$ and $P_{\pm}$ are the projectors for $U$. This shows that the first wire gives a measurement result that indicates one of the two eigenvalues of $U$ where $\ket{0}$ represents an eigenvalue of 1 and $\ket{1}$ represents an eigenvalue of -1 and leaves $\ket{\psi_{out}}$ as the corresponding eigenvector.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.35 {#exercise-435}






In the exercise we are given three circuits that have a controlled $U$ gate such that $C_{U} = \ket{0}\bra{0} \otimes I + \ket{1}\bra{1} \otimes U$. Let's say that the state of the system before the circuit is $\ket{\psi} = \alpha \ket{0}\ket{\psi_{b}} + \beta\ket{1}\ket{\psi_{b}}$

First let's consider the case when the control qubit is measured after the quantum gate (the leftmost circuit). For this case $C_{U}$ is applied first which puts the system in the state

$$\begin{aligned}
C_{U}\ket{\psi} &= \left(\ket{0}\bra{0} \otimes I + \ket{1}\bra{1} \otimes U \right) \left(\alpha \ket{0}\ket{\psi_{b}} + \beta\ket{1}\ket{\psi_{b}}\right)\\
&= \alpha \ket{0} \otimes \ket{\psi_{b}} + \beta \ket{1} \otimes U\ket{\psi_{b}}
\end{aligned}$$

Then when the control wire is measured there is a $\vert \alpha \vert^2$ probability of obtaining the result $\ket{0}$ putting the system in the state $\ket{0} \otimes \ket{\psi_{b}}$ and a $\vert \beta \vert^2$ probability of obtaining the result $\ket{1}$ putting the system in the state $\ket{1} \otimes U\ket{\psi_{b}}$.

Now let's consider the case when the control qubit is measured before the quantum gate (the middle circuit). For this case first the control qubit is measured, where there is a $\vert \alpha \vert^2$ probability of measuring $\ket{0}$ and a $\vert \beta \vert^2$ probability of measuring $\ket{1}$, putting the control wires in the measured state. Then $C_U$ is applied, resulting in the system being in state $\ket{0} \otimes \ket{\psi_{b}}$ or $\ket{1} \otimes U\ket{\psi_{b}}$, depending on what the control qubit measurement was. 

Both circuits have the same probability of obtaining one of the two same outputs and therefore are equivalent.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |





## Universal quantum gates

### Exercise 4.36 {#exercise-436}






This circuit will perform the transformation $\ket{x,y} \rightarrow \ket{x, x+y \mod 4}$. Since $x$ and $y$ are two bit numbers each number will be written in the following convention $x=x_2 x_1$, where $x_1$ and $x_2$ are digits in the number $x$. Therefor the transformation can be written as

$$\begin{aligned}
\ket{x_1, x_2,y_1, y_2} &\rightarrow \ket{x_1, x_2, (x+y \mod 4)_1, (x+y \mod 4)_2} \\
&= \ket{x_1, x_2, x_1 \oplus y_1, x_2 \oplus y_2 \oplus (x_1 \land y_1)}
\end{aligned}$$

The following circuit performs this transformation

<img width="564" height="231" alt="image" src="https://github.com/user-attachments/assets/dc5a1bd0-af92-4e1a-a5a1-159cd8046896" />

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.37 {#exercise-437}






Since $U$ is a $4 \times 4$ matrix, we'll need to find $U_1, \cdots, U_k$ such that $U_k \cdots U_1 = I$ where $k \leq 6$ using a procedure similar to the one outlined in equations 4.44 - 4.50. 

From equation 4.54

$$\begin{aligned}
U = \frac{1}{2}\begin{bmatrix} 1 & 1 & 1 & 1 \\\ 1 & i & -1 & -i \\\ 1 & -1 & 1 & -1 \\\ 1 & -i & -1 & i \end{bmatrix}
\end{aligned}$$

Then let's set 

$$\begin{aligned}
U_1 = \begin{bmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} & 0 & 0 \\\ \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 1 \end{bmatrix}
\end{aligned}$$

Which gives

$$\begin{aligned}
U_1 U = \frac{1}{2}\begin{bmatrix} \sqrt{2} & \frac{\sqrt{2}(1+i)}{2} & 0 & \frac{\sqrt{2}(1-i)}{2} \\\ 0 & \frac{\sqrt{2}(1-i)}{2} & \sqrt{2} & \frac{\sqrt{2}(1+i)}{2} \\\ 1 & -1 & 1 & -1 \\\ 1 & -i & -1 & i \end{bmatrix} 
\end{aligned}$$

Now let's set 

$$\begin{aligned}
U_2 = \begin{bmatrix} \frac{\sqrt{2}}{\sqrt{3}} & 0 & \frac{1}{\sqrt{3}} & 0 \\\ 0 & 1 & 0 & 0 \\\ \frac{1}{\sqrt{3}} & 0 & -\frac{\sqrt{2}}{\sqrt{3}} & 0 \\\ 0 & 0 & 0 & 1 \end{bmatrix}
\end{aligned}$$

Which gives

$$\begin{aligned}
U_2 U_1 U = \frac{1}{2}\begin{bmatrix} \sqrt{3} & \frac{\sqrt{3}i}{3} & \frac{\sqrt{3}}{3} & -\frac{\sqrt{3}i}{3} \\\ 0 & \frac{\sqrt{2}(1-i)}{2} & \sqrt{2} & \frac{\sqrt{2}(1+i)}{2} \\\ 0 & \frac{\sqrt{6}(3 + i)}{6} & -\frac{\sqrt{6}}{3} & \frac{\sqrt{6}(3 - i)}{6} \\\ 1 & -i & -1 & i \end{bmatrix} 
\end{aligned}$$

Now let's set

$$\begin{aligned}
U_3 = \begin{bmatrix} \frac{\sqrt{3}}{2} & 0 & 0 & \frac{1}{2} \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ \frac{1}{2} & 0 & 0 & -\frac{\sqrt{3}}{2} \end{bmatrix}
\end{aligned}$$

Which gives

$$\begin{aligned}
U_3 U_2 U_1 U = \frac{1}{2}\begin{bmatrix} 2 & 0 & 0 & 0 \\\ 0 & \frac{\sqrt{2}(1-i)}{2} & \sqrt{2} & \frac{\sqrt{2}(1+i)}{2} \\\ 0 & \frac{\sqrt{6}(3 + i)}{6} & -\frac{\sqrt{6}}{3} & \frac{\sqrt{6}(3 - i)}{6} \\\ 0 & \frac{2\sqrt{3}i}{3} & \frac{2\sqrt{3}}{3} & -\frac{2\sqrt{3} i}{3} \end{bmatrix} 
\end{aligned}$$

Now let's set

$$\begin{aligned}
U_4 = \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & \frac{3\sqrt{2}(1+i)}{4\sqrt{6}} & \frac{3 - i}{4} & 0 \\\ 0 & \frac{3 + i}{4} & -\frac{3\sqrt{2}(1-i)}{4\sqrt{6}} & 0 \\\ 0 & 0 & 0 & 1 \end{bmatrix}
\end{aligned}$$

Which gives

$$\begin{aligned}
U_4 U_3 U_2 U_1 U = \frac{1}{2}\begin{bmatrix} 2 & 0 & 0 & 0 \\\ 0 & \frac{2 \sqrt{6}}{3} & \frac{\sqrt{6} i}{3} & \frac{\sqrt{6}}{3} \\\ 0 & 0 & \sqrt{2} & \sqrt{2} i \\\ 0 & \frac{2\sqrt{3}i}{3} & \frac{2\sqrt{3}}{3} & -\frac{2\sqrt{3} i}{3} \end{bmatrix} 
\end{aligned}$$

Now let's set

$$\begin{aligned}
U_5 = \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & \frac{\sqrt{6}}{3} & 0 & -\frac{\sqrt{3}i}{3} \\\ 0 & 0 & 1 & 0 \\\ 0 & \frac{\sqrt{3}i}{3} & 0 & -\frac{\sqrt{6}}{3} \end{bmatrix}
\end{aligned}$$

Which gives

$$\begin{aligned}
U_5 U_4 U_3 U_2 U_1 U = \frac{1}{2}\begin{bmatrix} 2 & 0 & 0 & 0 \\\ 0 & 2 & 0 & 0 \\\ 0 & 0 & \sqrt{2} & \sqrt{2} i \\\ 0 & 0 & -\sqrt{2} & \sqrt{2} i \end{bmatrix} 
\end{aligned}$$

Now let's set

$$\begin{aligned}
U_6 = \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & \frac{\sqrt{2}}{2} & -\frac{\sqrt{2}}{2} \\\ 0 & 0 & -\frac{\sqrt{2} i}{2} & -\frac{\sqrt{2} i}{2} \end{bmatrix}
\end{aligned}$$

Which gives

$$\begin{aligned}
U_6 U_5 U_4 U_3 U_2 U_1 U = \frac{1}{2}\begin{bmatrix} 2 & 0 & 0 & 0 \\\ 0 & 2 & 0 & 0 \\\ 0 & 0 & 2 & 0 \\\ 0 & 0 & 0 & 2 \end{bmatrix} = I
\end{aligned}$$


Then $U$ can be written as 

$$\begin{aligned}
U = U_1^\dagger U_2^\dagger U_3^\dagger U_4^\dagger U_5^\dagger U_6^\dagger
\end{aligned}$$

I used the following script to confirm these results

```
from sympy import simplify, Matrix, I, sqrt

U = Matrix([[1,1,1,1],[1,I,-1,-I],[1,-1,1,-1],[1,-I,-1,I]])/2
U1 = Matrix([[1/sqrt(2),1/sqrt(2),0,0],[1/sqrt(2),-1/sqrt(2),0,0],[0,0,1,0],[0,0,0,1]])
U2 = Matrix([[sqrt(2)/sqrt(3),0,1/sqrt(3),0],[0,1,0,0],[1/sqrt(3),0,-sqrt(2)/sqrt(3),0],[0,0,0,1]])
U3 = Matrix([[sqrt(3)/2,0,0,1/2],[0,1,0,0],[0,0,1,0],[1/2,0,0,-sqrt(3)/2]])
U4 = Matrix([[1,0,0,0],[0,3*sqrt(2)*(1+I)/(4*sqrt(6)),(3-I)/4,0],[0,(3+I)/4,-3*sqrt(2)*(1-I)/(4*sqrt(6)),0],[0,0,0,1]])
U5 = Matrix([[1,0,0,0],[0,sqrt(6)/3,0,-sqrt(3)*I/3],[0,0,1,0],[0,sqrt(3)*I/3,0,-sqrt(6)/3]])
U6 = Matrix([[1,0,0,0],[0,1,0,0],[0,0,sqrt(2)/2,-sqrt(2)/2],[0,0,-sqrt(2)/2*I,-sqrt(2)/2*I]])

print(simplify(U6 @ U5 @ U4 @ U3 @ U2 @ U1 @ U).evalf(3))
print(simplify(U1.adjoint() @ U2.adjoint() @ U3.adjoint() @ U4.adjoint() @ U5.adjoint() @ U6.adjoint() ).evalf(3))
```

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 4.38 {#exercise-438}

 




A complex $d \times d$ matrix can have up to $2d^2$ parameters ($d^2$ real parts and $d^2$ imaginary parts for the $d^2$ matrix entries). However, having the matrix be unitary places additional constraints on the entries, reducing the number of independent parameters to $d^2$. 

A two-level unitary matrix then has $2^2=4$ parameters. When multiplying $k$ two-level unitary matrices together, we'll then have $4k$ parameters. In order to decompose a $d \times d$ unitary matrix as the product of two-level unitary matrices, we'll need $4k \geq d^2$. For all $d \geq 2$ the following inequality holds $d^2 \geq 4(d-1)$.  Therefore, for all $d \geq 2$ there exists some $d \times d$ unitary matrix $U$ that requires $k \geq d-1$ two-level unitary matrices for the decomposition. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.39 {#exercise-439}






This transformation acts non-trivially only on the states $\ket{010}$ and $\ket{111}$. We write a Gray code connecting $010$ and $111$

$$\begin{aligned}
A & B & C \\\
0 & 1 & 0 \\\
0 & 1 & 1 \\\
1 & 1 & 1
\end{aligned}$$

Which can be implemented using this circuit

<img width="307" height="192" alt="image" src="https://github.com/user-attachments/assets/a6d6dca5-8cd7-4d2a-9d2a-018a9ce55190" />

As with the example given in section 4.5.2 of the book, each of the controlled operations in this circuit can be realized using $O(n)$ single qubit and CNOT gates.

 | [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.40 {#exercise-440}






$$\begin{aligned}
E(R_{\hat{n}}(\alpha), R_{\hat{n}}(\alpha + \beta)) &= max \Vert (R_{\hat{n}}(\alpha) - R_{\hat{n}}(\alpha + \beta))\ket{\psi} \Vert \\
&= max \Vert (R_{\hat{n}}(\alpha) - R_{\hat{n}}(\alpha + \beta))\ket{\psi} \Vert \\
&= max \Vert R_{\hat{n}}(\alpha)(I - R_{\hat{n}}(\beta))\ket{\psi} \Vert \\
&= max \Vert (I - R_{\hat{n}}(\beta))\ket{\psi} \Vert \\
&= max \lbrace \vert 1 - \exp(i\beta/2) \vert, \vert 1 - \exp(-i\beta/2) \vert \rbrace \\
&= \vert 1 - \exp(i\beta/2) \vert
\end{aligned}$$

Then as stated in section 4.5.3, $\theta$ is given by $\cos(\theta/2) = \cos^2(\pi/8)$, making $\theta$ a irrational multiple of $2\pi$, so we can write

$$\begin{aligned}
E(R_{\hat{n}}(\alpha), R_{\hat{n}}(\theta)^n) &= E(R_{\hat{n}}(\alpha), R_{\hat{n}}(n\theta)) \\
&= E(R_{\hat{n}}(\alpha), R_{\hat{n}}(\alpha + (n\theta - \alpha))) \\
&= \vert 1 - \exp(i(n\theta - \alpha)/2) \vert \\
&< \frac{\epsilon}{3} & \text{for $\epsilon>0$ }
\end{aligned}$$

That last statement above can be made because $\theta$ is an irrational multiple of $2\pi$ which means that with the appropriate selection of $n$ we can make $(n\theta - \alpha)/2 \mod 2\pi$ arbitrarily close to zero and therefore make $\vert 1 - \exp(i(n\theta - \alpha)/2) \vert$ arbitrarily small. Thus, there exists a $n$ for any $\epsilon>0$ where $E(R_{\hat{n}}(\alpha), R_{\hat{n}}(\theta)^n) < \frac{\epsilon}{3}$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.41 {#exercise-441}






The matrix representation for the circuit is given by 

$$\begin{aligned}
C &= H_1 H_2 CCNOT_{123} S_3 CCNOT_{123} H_2 H_1 \\
&= \frac{1}{4}\begin{bmatrix} 3 + i & 0 & 1-i & 0 & 1-i & 0 & -1 + i & 0 \\\ 0 & 1 + 3 i & 0 & -1 + i & 0 & -1 + i & 0 & 1-i \\\ 1-i & 0 & 3+i & 0 & -1+i & 0 & 1-i & 0 \\\ 0 & -1+i & 0 & 1+3i & 0 & 1-i & 0 & -1 + i \\\ 1 - i & 0 & -1 + i & 0 & 3 + i & 0 & 1 - i & 0 \\\ 0 & -1 + i & 0 & 1 - i & 0 & 1 + 3i & 0 & -1 + i \\\ -1 + i & 0 & 1 - i & 0 & 1 - i & 0 & 3 + i & 0 \\\ 0 & 1 - i & 0 & -1 + i & 0 & -1 + i & 0 & 1 + 3i \end{bmatrix}
\end{aligned}$$

Then the output of the circuit for an input $\ket{\psi} = \alpha \ket{0} + \beta \ket{1}$ is given by

$$\begin{aligned}
C (\ket{00} \otimes \ket{\psi}) &= \frac{1}{4}\begin{bmatrix} 3 + i & 0 & 1-i & 0 & 1-i & 0 & -1 + i & 0 \\\ 0 & 1 + 3 i & 0 & -1 + i & 0 & -1 + i & 0 & 1-i \\\ 1-i & 0 & 3+i & 0 & -1+i & 0 & 1-i & 0 \\\ 0 & -1+i & 0 & 1+3i & 0 & 1-i & 0 & -1 + i \\\ 1 - i & 0 & -1 + i & 0 & 3 + i & 0 & 1 - i & 0 \\\ 0 & -1 + i & 0 & 1 - i & 0 & 1 + 3i & 0 & -1 + i \\\ -1 + i & 0 & 1 - i & 0 & 1 - i & 0 & 3 + i & 0 \\\ 0 & 1 - i & 0 & -1 + i & 0 & -1 + i & 0 & 1 + 3i \end{bmatrix} \begin{bmatrix} \alpha \\\ \beta \\\ 0 \\\ 0 \\\ 0 \\\ 0 \\\ 0 \\\ 0 \end{bmatrix} \\
&= \frac{1}{4} \begin{bmatrix} \alpha (3 + i) \\\ \beta (1 + 3 i) \\\ \alpha(1 - i) \\\ -\beta(1 - i) \\\ \alpha(1 - i) \\\ \beta(-1 + i) \\\ -\alpha(1 - i) \\\ \beta(1 - i) \end{bmatrix} \\
&=  \frac{1}{4}\begin{bmatrix} (1+i)\sqrt{5}\begin{bmatrix} \frac{2-i}{\sqrt{5}} & 0 \\\ 0 & \frac{2+i}{\sqrt{5}} \end{bmatrix} \begin{bmatrix} \alpha \\\ \beta \end{bmatrix} \\\ (1-i) \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} \alpha \\\ \beta \end{bmatrix}  \\\ (1-i) \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} \alpha \\\ \beta \end{bmatrix} \\\ -(1-i) \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} \alpha \\\ \beta \end{bmatrix}  \end{bmatrix} \\
&=  \frac{\sqrt{2}}{4}\begin{bmatrix} e^{i\pi/4}\sqrt{5} R_z(\theta) \begin{bmatrix} \alpha \\\ \beta \end{bmatrix} \\\ e^{-i\pi/4} Z \begin{bmatrix} \alpha \\\ \beta \end{bmatrix}  \\\ e^{-i\pi/4} Z \begin{bmatrix} \alpha \\\ \beta \end{bmatrix} \\\ -e^{-i\pi/4} Z \begin{bmatrix} \alpha \\\ \beta \end{bmatrix}  \end{bmatrix} & \text{where $\cos\frac{\theta}{2}=\frac{2}{\sqrt{5}}$}\\
&= e^{i\pi/4}\frac{\sqrt{10}}{4}\ket{00} \otimes R_z(\theta) \ket{\psi} + e^{-i\pi/4}\frac{\sqrt{2}}{4}(\ket{01} + \ket{10} - \ket{11})\otimes Z \ket{\psi} \\
\end{aligned}$$

Above when both the first and second qubit measure as $0$, the third has the operation $R_z(\theta)$ applied, and otherwise $Z$ is applied. It can also be seen that the probability of the first and second qubit measuring as $0$ is $\left(\frac{\sqrt{10}}{4}\right)^2 = \frac{5}{8}$. Let's check to see what $\cos\theta$ is now that we know $\cos\frac{\theta}{2}=\frac{2}{\sqrt{5}}$.

$$\begin{aligned}
\cos\theta &= 2\cos^2(\theta/2) - 1 \\
&= 2\left(\frac{2}{\sqrt{5}}\right)^2 - 1 \\
&= \frac{3}{5}
\end{aligned}$$

This agrees with what is expected based on the exercise description. 

We can use a Repeat Until Success strategy using a measurement + classical feed-forward step to increase the probability of applying the operation $R_z(\theta)$ to the target qubit. This is done by measuring the ancilla qubits and if a measurement other than $\ket{00}$ is observed, the ancilla are reset to $\ket{0}$, the single-qubit operator $Z=S^2$ is applied to the target qubit to reset it to $\ket{\psi}$, and then $C$ is applied again. This process can be repeated until $\ket{00}$ is measured for the ancilla.   

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 4.42 {#exercise-442}






(1) Since $\cos\theta=3/5$,  we know that $e^{i\theta}=\frac{3+4i}{5}$. Assume for contradiction that $\theta$ is a rational multiple of $2\pi$ and so can be written as $\theta = \frac{2\pi n}{m}$ for integers $m,n>0$. Then,

$$\begin{aligned}
\left(e^{i\theta}\right)^m &=\left(\frac{3+4i}{5}\right)^m \\
e^{i m \theta} &= \frac{(3+4i)^m}{5^m} \\
1 &= \frac{(3+4i)^m}{5^m} & \text{since $\theta = \frac{2\pi n}{m}$} \\
5^m &= (3+4i)^m 
\end{aligned}$$

Therefore, if $\theta$ is rational then there exists positive integer $m$ such that $5^m = (3+4i)^m$.

(2) Given the above,

$$\begin{aligned}
(3+4i)^2 &= 9 - 16 + 24 i \\
&= -7 + 24i \\
&= (3 + 4i) + (-10 + 20i) \\
&= (3+4i) + 5(-2 + 4i) \\
&= 3 + 4i \mod 5
\end{aligned}$$

Then by induction,

$$\begin{aligned}
(3+4i)^m &= (3+i4)^2 (3+i4)^{m-2} \\
&= \left(3+i4 \mod 5 \right) (3+i4)^{m-2} \\
&= (3+i4) (3+i4)^{m-2} \mod 5 \\
&= (3+i4)^2 (3+i4)^{m-3} \mod 5 \\
& \vdots \\
&= 3+i4 \mod 5
\end{aligned}$$

Therefore,

$$\begin{aligned}
5^m &= (3+4i)^m \\
0 \mod 5 &= 3+i4 \mod 5
\end{aligned}$$

Since the above statement is false, there is no positive integer $m$ such that $5^m = (3+i4)^m$ and therefore $\theta$ is not a rational multiple of $2\pi$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.43 {#exercise-443}






From [exercise 4.41](#exercise-441), we know that we can apply $R_z(\theta)$ to a qubit with $\theta$ given by $\cos\theta=5/8$ using only Hadamard, phase, controlled-NOT, and Toffoli gates. From [exercise 4.42](#exercise-442), we know that this $\theta$ is an irrational multiple of $2\pi$. From [exercise 4.40](#exercise-440) and equation 4.76, we know that we can approximate a rotation $R_z(\alpha)$ from $R_z(\theta)^n$ for any $\alpha$ using an appropriately selected $n$ when $\theta$ is an irrational multiple of $2\pi$. Since we can approximate arbitrarily well rotation $R_z(\alpha)$ for arbitrary $\alpha$, we can then also approximate arbitrarily well rotation $R_x(\alpha)$ using Hadamard gates and $R_z(\alpha)$ since

$$\begin{aligned}
H R_z(\alpha) H &= H \left(\cos\frac{\alpha}{2} I - i\sin\frac{\alpha}{2} Z\right) H \\
&= \cos\frac{\alpha}{2} HIH - i\sin\frac{\alpha}{2} HZH \\
&= \cos\frac{\alpha}{2} I - i\sin\frac{\alpha}{2} X & \text{exercise 4.13} \\
&= R_x(\alpha)
\end{aligned}$$

Then using decomposition we can approximate arbitrarily well $R_y(\alpha)$ rotations

$$\begin{aligned}
R_y(\alpha) &=  R_x(-\pi/2)R_z(\alpha)R_x(\pi/2) \\
&= H R_z(-\pi/2) H R_z(\alpha) H R_z(\pi/2) H
\end{aligned}$$

Since we can create arbitrary $R_z$, $R_x$, and $R_y$ rotations, we can create any arbitrary unitary operation, as demonstrated in Theorem 4.1 and [exercise 4.10](#exercise-410), using only the Hadamard, phase, controlled-NOT, and Toffoli gates. Therefore these gates are universal for quantum computation. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.44 {#exercise-444}

This exercise is based on [Quantum computational networks](https://royalsocietypublishing.org/doi/10.1098/rspa.1989.0099) by Deutsch, which I ended up having to reference to find the solution. 




The matrix representation of $G$ is given by

$$\begin{aligned}
G_{123} &= iR_x(\pi\alpha) \\
&= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & i\cos\frac{\pi\alpha}{2} & \sin\frac{\pi\alpha}{2} \\\ 0 & 0 & 0 & 0 & 0 & 0 & \sin\frac{\pi\alpha}{2} & i\cos\frac{\pi\alpha}{2} \end{bmatrix}
\end{aligned}$$

Then the matrix representation of $G^n$ is given by

$$\begin{aligned}
G_{123}^n &= i^nR_x(\pi\alpha)^n \\
&= i^n R_x(n\pi\alpha) \\
&= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & i^n\cos\frac{n\pi\alpha}{2} & -i^{n+1}\sin\frac{n\pi\alpha}{2} \\\ 0 & 0 & 0 & 0 & 0 & 0 & -i^{n+1}\sin\frac{n\pi\alpha}{2} & i^n\cos\frac{n\pi\alpha}{2} \end{bmatrix} \\
&= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & e^{in\pi/2}\cos\frac{n\pi\alpha}{2} & -ie^{in\pi/2}\sin\frac{n\pi\alpha}{2} \\\ 0 & 0 & 0 & 0 & 0 & 0 & -ie^{in\pi/2}\sin\frac{n\pi\alpha}{2} & e^{in\pi/2}\cos\frac{n\pi\alpha}{2} \end{bmatrix} \\
\end{aligned}$$

Let's think about what kind of gates can be created with $G_{123}^n$. Let's first look at $G_{123}^{4n+1}$

$$\begin{aligned}
G_{123}^{4n+1} &= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & i\cos\left(\left(2n+\frac{1}{2}\right)\pi\alpha\right) & \sin\left(\left(2n+\frac{1}{2}\right)\pi\alpha\right) \\\ 0 & 0 & 0 & 0 & 0 & 0 & \sin\left(\left(2n+\frac{1}{2}\right)\pi\alpha\right) & i\cos\left(\left(2n+\frac{1}{2}\right)\pi\alpha\right) \end{bmatrix} \\
\end{aligned}$$

We know that given any $\epsilon > 0$ there exists positive integers $n$ and $m$ such that $\left(2n+\frac{1}{2}\right)\pi\alpha$ is within $\epsilon$ of $\left(2m+\frac{1}{2}\right)\pi$. Therefore, with the appropriate selection of $n$, we can approximate a Toffoli gate and thus can approximate all logic gates since the Toffoli gate is universal relative to the set of all logic gates.   

Now let's look at $G_{123}^{4n}$

$$\begin{aligned}
G_{123}^{4n} &= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & \cos\left(2n\pi\alpha\right) & -i\sin\left(2n\pi\alpha\right) \\\ 0 & 0 & 0 & 0 & 0 & 0 & -i\sin\left(2n\pi\alpha\right) & \cos\left(2n\pi\alpha\right) \end{bmatrix} \\
\end{aligned}$$

All $G_{123}^{4n}$ are of the form 

$$\begin{aligned}
U_\lambda &= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & \cos\left(\lambda \right) & -i\sin\left(\lambda\right) \\\ 0 & 0 & 0 & 0 & 0 & 0 & -i\sin\left(\lambda\right) & \cos\left(\lambda\right) \end{bmatrix} \\
\end{aligned}$$

and so $U_\lambda$ for any real $\lambda$ can be approximated by $G$. 

Let $P_{ij}$ be the permutation that interchanges $\ket{i}$ and $\ket{j}$. The $\lbrace P_{ij} \rbrace$ are made from logic gates and therefore able to be approximated by $G$ since $G$ can approximate Toffoli gates. Then for small $\lambda$

$$\begin{aligned}
P_{56}(U_\lambda P_{57})^2 (U_{-\lambda} P_{57})^2 P_{56} &= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & (2\sin^2(\lambda) + \cos^3(\lambda))\cos(\lambda) & i(\sin^2(\lambda) + \cos^3(\lambda) - \cos^2(\lambda))\sin(\lambda) & i(\cos(\lambda) - 1)\sin(\lambda)\cos(\lambda) \\\ 0 & 0 & 0 & 0 & 0 & i(1 - \cos(\lambda))\sin(\lambda)\cos(\lambda) & (\sin^2(\lambda) + \cos(\lambda))\cos(\lambda) & \sin^2(\lambda) \\\ 0 & 0 & 0 & 0 & 0 & i(-\sin^2(\lambda) - \cos^3(\lambda) + \cos^2(\lambda))\sin(\lambda) & (\cos(\lambda) - 2)\sin^2(\lambda)\cos(\lambda) & (\sin^2(\lambda) + \cos(\lambda))\cos(\lambda) \end{bmatrix} \\
&\approx \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & \lambda^2 \\\ 0 & 0 & 0 & 0 & 0 & 0 & -\lambda^2 & 1 \end{bmatrix} + O(\lambda^3)\\
&\approx \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & \cos\lambda^2 & \sin\lambda^2 \\\ 0 & 0 & 0 & 0 & 0 & 0 & -\sin\lambda^2 & \cos\lambda^2 \end{bmatrix} + O(\lambda^3)\\
\end{aligned}$$

The above calculation was done with the python script shown below. It can be seen that this matrix is approximating a gate that has the first and second bit as control bits controlling the application of a small $R_y(-2\lambda^2)$ rotation. 

```
from sympy import simplify, Matrix, I, symbols, cos, sin

L = symbols('L', real=True)

Up =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[0,0,0,0,0,0,cos(L),-I*sin(L)],[0,0,0,0,0,0,-I*sin(L),cos(L)]])
Un =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[0,0,0,0,0,0,cos(-L),-I*sin(-L)],[0,0,0,0,0,0,-I*sin(-L),cos(-L)]])

P56 =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,0,1,0],[0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,1]])
P57 =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,0,0,1],[0,0,0,0,0,0,1,0],[0,0,0,0,0,1,0,0]])

circuit = simplify(P56 @ (Up @ P57)**2  @ (Un @ P57)**2 @ P56)

print(circuit)
```

Therefore, matrices of the form shown below can be approximated by $G$ for any $\lambda$ 

$$\begin{aligned}
\lim_{n \to \infty} \lbrace P_{56}(U_{\sqrt{\lambda/n}} P_{57})^2 (U_{-\sqrt{\lambda/n}} P_{57})^2 P_{56} \rbrace^n &= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & \cos\lambda & \sin\lambda \\\ 0 & 0 & 0 & 0 & 0 & 0 & - \sin\lambda & \cos\lambda \end{bmatrix} &= V_{\lambda}
\end{aligned}$$

Going back to the case of small $\lambda$

$$\begin{aligned}
U_{\lambda}V_{\lambda}U_{-\lambda}V_{-\lambda}  &= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & (1 + i)(1 - \cos(4\lambda))/4 - \sin^4(\lambda) + \cos^4(\lambda) & (-2 - 2i)\sin^3(\lambda)\cos(\lambda) \\\ 0 & 0 & 0 & 0 & 0 & 0 & (2 - 2i)\sin^3(\lambda)\cos(\lambda) & (1 - i)(1 - \cos(4\lambda))/4 - \sin^4(\lambda) + \cos^4(\lambda) \end{bmatrix} \\
&\approx \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & (1 + i)(2\lambda^2) + 1 - 2\lambda^2 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & (1 - i)(2\lambda^2) + 1 - 2\lambda^2 \end{bmatrix} + O(\lambda^3)\\
&= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 + i2\lambda^2 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 - i2\lambda^2 \end{bmatrix} + O(\lambda^3)\\
&\approx \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & e^{i2\lambda^2} & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & e^{-i2\lambda^2} \end{bmatrix} + O(\lambda^3)\\
\end{aligned}$$

The above calculation was done with the python script shown below. It can be seen that this matrix is approximating a gate that has the first and second bit as control bits controlling the application of a small $R_z(-4\lambda^2)$ rotation.

```
from sympy import simplify, Matrix, I, symbols, cos, sin

L = symbols('L', real=True)

Up =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[0,0,0,0,0,0,cos(L),-I*sin(L)],[0,0,0,0,0,0,-I*sin(L),cos(L)]])
Un =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[0,0,0,0,0,0,cos(-L),-I*sin(-L)],[0,0,0,0,0,0,-I*sin(-L),cos(-L)]])

P56 =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,0,1,0],[0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,1]])
P57 =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,0,0,1],[0,0,0,0,0,0,1,0],[0,0,0,0,0,1,0,0]])

Vp = Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[0,0,0,0,0,0,cos(L),sin(L)],[0,0,0,0,0,0,-sin(L),cos(L)]])
Vn = Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[0,0,0,0,0,0,cos(-L),sin(-L)],[0,0,0,0,0,0,-sin(-L),cos(-L)]])


circuit = simplify(Up @ Vp @ Un @ Vn)

print(circuit)
```

Therefore, matrices of the form shown below can be approximated by $G$ for any $\lambda$ 

$$\begin{aligned}
\lim_{n \to \infty} \lbrace U_{\sqrt{\lambda/2n}}V_{\sqrt{\lambda/2n}}U_{-\sqrt{\lambda/2n}}V_{-\sqrt{\lambda/2n}} \rbrace^n &= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & e^{i\lambda} & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & e^{-i\lambda} \end{bmatrix} &= W_{\lambda}
\end{aligned}$$

Then using permutation operators and $W_{\lambda}$ the following can be approximated

$$\begin{aligned}
W_{-\lambda/8}P_{06}W_{-\lambda/8}P_{06}P_{16}W_{-\lambda/8}P_{16}P_{26}W_{-\lambda/8}P_{26}P_{36}W_{-\lambda/8}P_{36}P_{46}W_{-\lambda/8}P_{46}P_{56}W_{-\lambda/8}P_{56} &= \begin{bmatrix} e^{-i\lambda/8} & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & e^{-i\lambda/8} & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & e^{-i\lambda/8} & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & e^{-i\lambda/8} & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & e^{-i\lambda/8} & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & e^{-i\lambda/8} & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & e^{-i\lambda/8} & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & e^{i7\lambda/8} \end{bmatrix} \\
&= e^{-i\lambda/8}\begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & e^{i\lambda} \end{bmatrix} \\
&= e^{-i\lambda/8} X_{\lambda}
\end{aligned}$$

where the global phase $e^{-i\lambda/8}$ can be ignored. I used the following python script to confirm the above calculation. 

```
from sympy import simplify, Matrix, I, symbols, exp

L = symbols('L', real=True)

W =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[0,0,0,0,0,0,exp(-I*L/8),0],[0,0,0,0,0,0,0,exp(I*L/8)]])

P06 =  Matrix([[0,0,0,0,0,0,1,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[1,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,1]])
P16 =  Matrix([[1,0,0,0,0,0,0,0],[0,0,0,0,0,0,1,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[0,1,0,0,0,0,0,0],[0,0,0,0,0,0,0,1]])
P26 =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,0,0,0,0,1,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,1]])
P36 =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,0,0,0,1,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,1,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,0,0,0,1]])
P46 =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,0,0,1,0],[0,0,0,0,0,1,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,0,0,1]])
P56 =  Matrix([[1,0,0,0,0,0,0,0],[0,1,0,0,0,0,0,0],[0,0,1,0,0,0,0,0],[0,0,0,1,0,0,0,0],[0,0,0,0,1,0,0,0],[0,0,0,0,0,0,1,0],[0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,1]])

circuit = simplify((W @ P06 @ W @ P06 @ P16 @ W @ P16 @ P26 @ W @ P26 @ P36 @ W @ P36 @ P46 @ W @ P46 @ P56 @ W @ P56) )

print(circuit)
```

We can now approximate an arbitrary two-level unitary gate 

$$\begin{aligned}
U &= W_{\alpha}X_{2\alpha}W_{-\beta/2}V_{\gamma}W_{-\delta/2} \\
&= \begin{bmatrix} 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 0 & 0 & 0 & e^{i(\alpha-\beta/2-\delta/2)}\cos\gamma & e^{i(\alpha-\beta/2+\delta/2)}\sin\gamma \\\ 0 & 0 & 0 & 0 & 0 & 0 & - e^{i(\alpha+\beta/2-\delta/2)}\sin\gamma & e^{i(\alpha+\beta/2+\delta/2)}\cos\gamma \end{bmatrix}
\end{aligned}$$

and move its entries to different registries using permutation gates constructed with $G$ gates. In section 4.5.1 the authors demonstrated that two-level unitary gates are universal. Therefore, since we can approximate an arbitrary two-level unitary gate with $G$ gates, $G$ gates are universal.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 4.45 {#exercise-445}






$S$, $CNOT$, and Toffoli gates are of the form $M$. $H$ is of the form $2^{-1/2}M$. Therefore, any gate constructed from $H$, $S$, $CNOT$, and Toffoli gates will be of the form $2^{-k/2}M$ where $k$ is the number of $H$ gates used to construct the circuit. 

Repeating this exercise with the Toffoli gate replaced by the $\pi/8$ gate. The $\pi/8$ gate is of the form 

$$\begin{aligned}
T &= \begin{bmatrix} 1 & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \\
&= \begin{bmatrix} 1 & 0 \\\ 0 & (1+i)/\sqrt{2} \end{bmatrix} \\
\end{aligned}$$

This can't be written in the form of $2^{-1/2}M$. However, $T^2=S$ is in the form of $M$. So, if there is an even number of $\pi/8$ gates used it is possible (but not guaranteed) to construct $U$ in the form $2^{-k/2}M$ where $k$ is the number of $H$ gates used to construct $U$. If there is an odd number of $\pi/8$ gates then $U$ cannot be written in the form $2^{-k/2}M$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## Simulation of quantum systems

### Exercise 4.46 {#exercise-446}






With $n$ qubits there are $2^n$ different states that comprise a basis set, and so the density matrix $\rho$ will be a $2^n \times 2^n$ matrix. This matrix will, therefore, have $4^n$ elements. For a density matrix, the diagonal elements are real numbers that sum to one. Therefore, $2^n-1$ real numbers are needed to represent these elements. The reason it isn't $2^n$ is that once $2^n-1$ elements are defined, the last one is also defined due to the requirement that they sum to 1. The off-diagonal elements are complex conjugates of each other, i.e. $\rho_{ij} = \rho_{ji}^\ast$. So, even though each off-diagonal element is defined by two real numbers (the real and the imaginary component) there are only $4^n - 2^n$ independent real numbers needed. Therefore, the total number of independent real numbers needed to describe $\rho$ is $2^n-1 + 4^n - 2^n = 4^n-1$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.47 {#exercise-447}






Since $\lbrack H_j,H_k \rbrack = 0$, $H_j$ and $H_k$ are simultaneously diagonalizable, meaning they share a common basis and can be written as $H_j = \sum_{i} \lambda_{ji} \ket{i}\bra{i}$ and $H_k = \sum_{i} \lambda_{ki} \ket{i}\bra{i}$. Therefore $H_j + H_k = \sum_{i} \left(\lambda_{ji}+\lambda_{ki}\right)\ket{i}\bra{i}$ and so $H=\sum_k^L H_{k} = \sum_i \left(\sum_k^L \lambda_{ki}\right)\ket{i}\bra{i}$. Thus,

$$\begin{aligned}
e^{-iHt} &= \sum_i e^{-i\left(\sum_k^L \lambda_{ki}\right)t}\ket{i}\bra{i} \\
&= \sum_i \left(\prod_k^L e^{-i\lambda_{ki}t}\right)\ket{i}\bra{i} \\
&= \prod_k^L \left(\sum_i e^{-i\lambda_{ki}t}\ket{i}\bra{i}\right) \\
&= \prod_k^L e^{-iH_kt}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.48 {#exercise-448}






If $H_k$ is able to act on at most $c$ particles and there a $n$ particles that means that there are the following number of combination of particles that can be used for $H_k$

$$\begin{aligned}
\sum_{m=1}^{c} \binom{n}{m} \leq \sum_{m=1}^{c} \frac{n^m}{m!} = O(n^c) \\
\end{aligned}$$

Since the upper bound on the possible combinations of particles is $O(n^c)$ the upper bound on $L$ is polynomial in $n$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.49 {#exercise-449}






To prove equation 4.105 we use the Taylor expansion

$$\begin{aligned}
e^{(A+B)\Delta t} &= I + (A+B)\Delta t + \frac{(A+B)^2\Delta t^2}{2} + O(\Delta t^3) \\
&= I + (A+B)\Delta t + \frac{1}{2}(A^2 + AB + BA + B^2)\Delta t^2 + O(\Delta t^3) \\
&= I + (A+B)\Delta t + \frac{1}{2}(A^2 + 2AB - \lbrack A,B \rbrack + B^2)\Delta t^2 + O(\Delta t^3) \\
&= \left(I + A\Delta t + \frac{A^2 \Delta t^2}{2}\right)\left(I + B\Delta t + \frac{B^2 \Delta t^2}{2}\right)\left(I - \frac{1}{2}\lbrack A,B \rbrack \Delta t^2\right) + O(\Delta t^3) \\
&= e^{A\Delta t}e^{B\Delta t}e^{-\frac{1}{2}\lbrack A,B \rbrack \Delta t^2} + O(\Delta t^3)
\end{aligned}$$


For equation 4.103, if we let $t/n=\Delta t$ then equations 4.100 become

$$\begin{aligned}
e^{iA\Delta t}e^{iB\Delta t} &= I + i(A+B)\Delta t + O(\Delta t^2)
\end{aligned}$$

Substituting $A+B$ for $A$ in equation 4.99 we get

$$\begin{aligned}
e^{i(A+B)\Delta t} &= I + i(A+B)\Delta t + O(\Delta t^2)
\end{aligned}$$

Therefore,

$$\begin{aligned}
e^{i(A+B)\Delta t} = e^{iA\Delta t}e^{iB\Delta t} + O(\Delta t^2)
\end{aligned}$$

Now let's prove equation 4.104

$$\begin{aligned}
e^{(A+B)\Delta t} &= I + (A+B)\Delta t + \frac{(A+B)^2\Delta t^2}{2} + O(\Delta t^3) \\
&= I + (A+B)\Delta t + \frac{1}{2}(A^2 + AB + BA + B^2)\Delta t^2 + O(\Delta t^3) \\
&= I + (\frac{A}{2} + B + \frac{A}{2})\Delta t + (\frac{A^2}{4} + \frac{AB}{2} + \frac{B^2}{2} + \frac{BA}{2} + \frac{A^2}{4})\Delta t^2 + O(\Delta t^3) \\
&= \left(I + \frac{A\Delta t}{2} + \frac{A^2 \Delta t^2}{4}\right)\left(I + B\Delta t + \frac{B^2 \Delta t^2}{2}\right)\left(I + \frac{A\Delta t}{2} + \frac{A^2 \Delta t^2}{4}\right) + O(\Delta t^3) \\
&= e^{A\Delta t/2}e^{B\Delta t}e^{A\Delta t/2} + O(\Delta t^3)
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 4.50 {#exercise-450}






For (a)

$$\begin{aligned}
U_{\Delta t} &= \left\lbrack e^{-iH_1 \Delta t}e^{-iH_2 \Delta t}\cdots e^{-iH_L \Delta t} \right\rbrack \left\lbrack e^{-iH_L \Delta t}e^{-iH_{L-1} \Delta t}\cdots e^{-iH_1 \Delta t} \right\rbrack \\
&= \left\lbrack e^{-iH_1 \Delta t}e^{-iH_2 \Delta t}\cdots e^{-iH_{L-1} \Delta t} \right\rbrack\left(e^{-iH_{L} \Delta t}e^{-iH_{L} \Delta t} \right) \left\lbrack e^{-iH_{L-1} \Delta t}e^{-iH_{L-2} \Delta t}\cdots e^{-iH_1 \Delta t} \right\rbrack \\
&= \left\lbrack e^{-iH_1 \Delta t}e^{-iH_2 \Delta t}\cdots e^{-iH_{L-1} \Delta t} \right\rbrack\left(e^{-i2H_{L} \Delta t} \right) \left\lbrack e^{-iH_{L-1} \Delta t}e^{-iH_{L-2} \Delta t}\cdots e^{-iH_1 \Delta t} \right\rbrack + O(\Delta t^3) & \text{per equation 4.105}\\
&= \left\lbrack e^{-iH_1 \Delta t}e^{-iH_2 \Delta t}\cdots e^{-iH_{L-2} \Delta t} \right\rbrack\left(e^{-iH_{L-1} \Delta t}e^{-i2H_{L} \Delta t}e^{-iH_{L-1} \Delta t} \right) \left\lbrack e^{-iH_{L-2} \Delta t}e^{-iH_{L-3} \Delta t}\cdots e^{-iH_1 \Delta t} \right\rbrack + O(\Delta t^3) \\
&= \left\lbrack e^{-iH_1 \Delta t}e^{-iH_2 \Delta t}\cdots e^{-iH_{L-2} \Delta t} \right\rbrack\left(e^{-i2(H_{L-1} + H_{L}) \Delta t} \right) \left\lbrack e^{-iH_{L-2} \Delta t}e^{-iH_{L-3} \Delta t}\cdots e^{-iH_1 \Delta t} \right\rbrack + O(\Delta t^3) & \text{per equation 4.104}\\
&\vdots &\text{repeat the previous step} \\
&= e^{-i2(H_1 + \cdots + H_{L-1} + H_{L}) \Delta t} + O(\Delta t^3) \\
&= e^{-i2H \Delta t} + O(\Delta t^3)
\end{aligned}$$

For (b)

$$\begin{aligned}
E\left(U_{\Delta t}^m, e^{-2miH\Delta t}\right) &= E\left(U_{\Delta t}^m, \left(e^{-2iH\Delta t} + O(\Delta t^3)\right)^m \right) &\text{from (a)}\\
&\leq \sum_{j=1}^m E(U_{\Delta t}, e^{-2iH\Delta t} + O(\Delta t^3)) & \text{per equation 4.69} \\
&= m O(\Delta t^3) \\
&\leq m\alpha\Delta t^3 & \text{for some constant $\alpha$}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 4.51 {#exercise-451}

 




Figure 4.19 shows a circuit that simulates $H=Z_1 \otimes Z_2 \otimes Z_3$. We know that $X=HZH$ and that $Y = SXS^\dagger = SHZHS^\dagger$ and so we can construct the following circuit to simulate $H=X_1 \otimes Y_2 \otimes Z_3 = H_1Z_1H_1 \otimes S_2H_2Z_2H_2S_2^\dagger \otimes Z_3$. 

<img width="766" height="288" alt="image" src="https://github.com/user-attachments/assets/1dc3eeeb-e34f-4f30-a5aa-98fcb0cd6ae0" />

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## Chapter Problems

### Problem 4.1 {#problem-41}






$$\begin{aligned}
\ket{x} \to \exp\left(\frac{-2i\pi f(x)}{2^n}\right)\ket{x}
\end{aligned}$$

To create this circuit we can first apply the gate that is made of $T$ Toffoli gates that performs $f:\lbrace 0,\cdots,2^m-1\rbrace \to \lbrace 0,\cdots,2^n-1\rbrace$ from $m$ to $n$ bits. Then we can apply $n$ controlled Z rotations to $\ket{x}$, rotating it by $\frac{-2i\pi}{2^n}2^d$, where $d$ is the digit that the control qubit represents. Finally apply the inverse of the gate that performed $f(x)$. This will take $2T+n$ gates; $2T$ for the $f(x)$ and $f^{-1}(x)$ gates and $n$ for the rotation gates. 

<img width="1047" height="491" alt="image" src="https://github.com/user-attachments/assets/3cfdfa51-283d-45f4-a680-79333c904762" />

In the diagram I have $\Delta t = \frac{2\pi}{2^n}$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Problem 4.2 {#problem-42}






We can construct a gate similar to figure 4.10, but instead of having the target qubit of the Toffoli gate be a control qubit for the next one in the circuit, we can first split the $n$ control qubits into pairs for the first timestamp and target $n/2$ work qubits with the pairs as controls for $n/2$ Toffoli gates. Then split these $n/2$ work qubits into pairs and use them as controls for $n/4$ Toffoli gates targeting an addition $n/4$ work qubits. Then continue this trend until a timestamp only requires one Toffoli gate which targets the final qubit. This circuit will require $O(\log n)$ timestamps and so has a depth $O(\log n)$. The $n=8$ case is shown below. I've put a box around the different time stamps in the diagram.

<img width="624" height="457" alt="image" src="https://github.com/user-attachments/assets/cd77008c-3b01-42c8-9aa1-ce0b02a09713" />

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Problem 4.3 {#problem-43}






(1) Since $U$ is unitary using spectral decomposition, we know that it can be written

$$\begin{aligned}
U = \sum_{E} \lambda_E \ket{E} \bra{E}
\end{aligned}$$

where $\lambda_E$ are eigenvalues and $\ket{E}$ form an orthonormal basis for $U$. 

From [exercise 2.18](https://adj59-dev.github.io/qcqi/chapter-2/#exercise-218), we know that the eigenvalues of a unitary matrix can be written in the form $\lambda_E = e^{-i \theta_E}$ for some real $\theta_E$.

Looking at our definition of $H$ we see

$$\begin{aligned}
H &= i \ln (U) \\
&= i \sum_{E} \ln (\lambda_E) \ket{E} \bra{E} \\
&= i \sum_{E} \ln (e^{-i \theta_E}) \ket{E} \bra{E} \\
&= i \sum_{E} -i \theta_E \ket{E} \bra{E} \\
&= \sum_{E} \theta_E \ket{E} \bra{E}
\end{aligned}$$

Since $\theta_E$ are real, we know that $H = \sum_{E} \theta_E \ket{E} \bra{E}$ is in the form of a Hermitian matrix. Therefore $H$ is Hermitian. We can see the relationship between the eigenvalues of $U$ and $H$ is  $\lambda_E = e^{-i \theta_E}$, therefore only an interval of length $2\pi$ in $\theta_E$ will correspond to unique values for $\lambda_E$.

(2) $\lbrace I, X, Y, Z \rbrace$ form a basis for any single qubit operation. So, a $n$-fold tensor product of $\lbrace I, X, Y, Z \rbrace$ form a basis for any $n$ qubit operation. Therefore, $H$ can be written as

$$\begin{aligned}
H &=\sum_{g} h_{g} g
\end{aligned}$$

where $h_{g}$ are some constant values and the sum is over all $n$-fold tensor products $g$ of the Pauli matrices $\lbrace I, X, Y, Z \rbrace$. We can find $h_{g}$ by taking the inner product of $H$ with $g$

$$\begin{aligned}
(g, H) &= \text{tr}(g^\dagger H) & \text{equation 2.65} \\
&= \text{tr}(g H) & \text{g is Hermitian}\\
&= \sum_{g'} h_{g'} \text{tr}(g g') & \text{exercise 2.38}\\
&= 2^n h_{g} & \text{since $\text{tr}(g g') = 2^n \delta_{g, g'}$ per exercise 2.36 and equation 2.78} \\
& \Rightarrow h_{g} = \frac{1}{2^n} \text{tr}(g H)
\end{aligned}$$

To determine whether $h_{g}$ is real, we can also look at

$$\begin{aligned}
h_{g}^\ast &= \left(\frac{1}{2^n}\text{tr}(g H)\right)^\ast \\
 &= \frac{1}{2^n}\left(\text{tr}(g H)^T\right)^\ast \\
&= \frac{1}{2^n}\text{tr}((g H)^\dagger) \\
&= \frac{1}{2^n}\text{tr}(H^\dagger g^\dagger) \\
&= \frac{1}{2^n}\text{tr}(H g) \\
&= \frac{1}{2^n}\text{tr}(g H) & \text{per exercise 2.37}\\
&= h_{g}
\end{aligned}$$

Since $h_{g}^\ast = h_{g}$, $h_{g}$ must be real. 

(3) Letting $\Delta = 1/k$ for some postive integer $k$, we can construct a circuit like the one created in [exercise 4.51](#exercise-451) for each $h_{g} g$ because $g$ is of the form specified in equation 4.114 and so we are able to simulate $g$ with the outlined procedure. This circuit will have one $Z$ rotation gate, $2n$ CNOT gates, and up to $2n$ single qubit gates for an upper bounds of $4n+1$ gates which is $O(n)$.

(4) Looking at $\exp(-iH\Delta)$ we get

$$\begin{aligned}
\exp(-iH\Delta) &= \exp(-i\sum_{g = g_1}^{g_{4^n}} h_{g} g \Delta) \\
&= \exp(-ih_{g_1}g_1\Delta)\exp(-i\sum_{g=g_2}^{g_{4^n}} h_{g} g \Delta) + O(\Delta^2) & \text{equation 4.103} \\
&\vdots & \text{repeat the previous step $4^n-2$ times} \\
&= \prod_g \exp(-ih_g g\Delta) + O(4^n\Delta^2)
\end{aligned}$$

(5) Then 

$$\begin{aligned}
U &= \exp(-iH) \\
&= \exp(-ikH\Delta) \\
&= \left\lbrack \prod_g \exp(-ih_g g\Delta) \right\rbrack\exp(-i(k-1)H\Delta) + O(4^n\Delta^2) \\
&\vdots & \text{repeat $k-2$ times} \\
&= \left\lbrack \prod_g \exp(-ih_g g\Delta) \right\rbrack^k + O(4^nk\Delta^2) \\
&= \left\lbrack \prod_g \exp(-ih_g g\Delta) \right\rbrack^k + O(4^n\Delta) &\text{since $\Delta = 1/k$}
\end{aligned}$$


(6) To construct this circuit, use $k$ iterations of the circuit outlined in (3). We need to choose $\Delta = 1/k$ such that 

$$\begin{aligned}
O(4^n\Delta) \leq \epsilon \\
\Rightarrow \Delta \leq O\left(\frac{\epsilon}{4^n}\right)\\
\Rightarrow k \geq O\left(\frac{4^n}{\epsilon}\right)
\end{aligned}$$

Combinding this with our results from (3)

$$\begin{aligned}
N_{gates} &= k \times (\text{gates per $g$}) \times (\text{number of $g$ per $H$}) \\
&= O\left(\frac{4^n}{\epsilon}\right)O(n)O\left(4^n\right) \\
&= O\left(\frac{n16^n}{\epsilon}\right)
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Problem 4.4 {#problem-44}






(1) 5, the construction is shown in Figure 4.8

(2) 14, from [exercise 4.22](#exercise-422)

(3) 14, take the construction from [exercise 4.22](#exercise-422), but exchange the CNOTs with controlled-Z gates that have Hadamard gates on either side since $CNOT_{ab} = H_b CZ_{ab} H_b$. Those Hadamard gates can be combined with neighboring single qubit gates so they do not increase the total gate count. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Problem 4.5 {#problem-45}






In [exercise 4.48](#exercise-448) we showed that for Hamiltonian $H_n = \sum_{k=1}^L H_k$, restricting the maximum number of particles interacting via each operation $H_k$ to a constant value $c$ limited the upper bounds of $L$ (the number of operations) to $O(n^c)$. If there was no constant limit and instead the maximum number of particles interacting via $H_k$ grew with $n$, let's say by $f(n)$, then $L$ would be $O(n^{f(n)})$. Therefore, if the maximum number of particles interacting for each operation grows with $n$, then $H_n$ is super-polynomial in $n$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Problem 4.6 {#problem-46}

The authors reference a paper for this problem in the History and further reading section: [Quantum teleportation is a universal computational primitive](https://arxiv.org/pdf/quant-ph/9908010). The solution in the paper uses **classically controlled single qubit gates**, the ability to perform measurements of pairs of qubits in the Bell basis, and the ability to prepare arbitrary four qubit entangled states. I had been trying to solve this problem with just single qubit gates (as that is what I thought the question was asking for), but it turns out what was needed is to have classical feed-forward corrections. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

