---
title: "Nielsen and Chuang: Chapter 5"
description: "Notes and exercise solutions for QCQI Chapter 5: QFT, phase estimation, factoring, order finding, and other applications."
categories:
  - Quantum Computation and Quantum Information
permalink: /qcqi/chapter-5/
toc: true
tags:
  - QCQI
  - quantum computing
  - Quantum Computation and Quantum Information
  - Nielsen & Chuang
  - chapter 5
  - exercise
  - problem
  - solutions
last_modified_at: 2025-12-07 12:00:00 -08:00
exercises:
  - anchor: exercise-51
    label: Exercise 5.1
  - anchor: exercise-52
    label: Exercise 5.2
  - anchor: exercise-53
    label: Exercise 5.3
  - anchor: exercise-54
    label: Exercise 5.4
  - anchor: exercise-55
    label: Exercise 5.5
  - anchor: exercise-56
    label: Exercise 5.6
  - anchor: exercise-57
    label: Exercise 5.7
  - anchor: exercise-58
    label: Exercise 5.8
  - anchor: exercise-59
    label: Exercise 5.9
  - anchor: exercise-510
    label: Exercise 5.10
  - anchor: exercise-511
    label: Exercise 5.11
  - anchor: exercise-512
    label: Exercise 5.12
  - anchor: exercise-513
    label: Exercise 5.13
  - anchor: exercise-514
    label: Exercise 5.14
  - anchor: exercise-515
    label: Exercise 5.15
  - anchor: exercise-516
    label: Exercise 5.16
  - anchor: exercise-517
    label: Exercise 5.17
  - anchor: exercise-518
    label: Exercise 5.18
  - anchor: exercise-519
    label: Exercise 5.19
  - anchor: exercise-520
    label: Exercise 5.20
  - anchor: exercise-521
    label: Exercise 5.21
  - anchor: exercise-522
    label: Exercise 5.22
  - anchor: exercise-523
    label: Exercise 5.23
  - anchor: exercise-524
    label: Exercise 5.24
  - anchor: exercise-525
    label: Exercise 5.25
  - anchor: exercise-526
    label: Exercise 5.26
  - anchor: exercise-527
    label: Exercise 5.27
  - anchor: exercise-528
    label: Exercise 5.28
  - anchor: exercise-529
    label: Exercise 5.29
  - anchor: problem-51
    label: Problem 5.1
  - anchor: problem-52
    label: Problem 5.2
  - anchor: problem-53
    label: Problem 5.3
  - anchor: problem-54
    label: Problem 5.4
  - anchor: problem-55
    label: Problem 5.5
  - anchor: problem-56
    label: Problem 5.6
chapter: 5
---

<a id="top"></a>



I just finished reading Chapter 5 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. I also worked through section A2.1 of Appendix 2 and all of Appendix 4. The authors reference Appendix 4 at the beginning of Section 5.3 to ensure the reader has sufficient background in number theory before starting the section. Since I’ve never formally studied this subject, I decided to read that appendix and do the exercises.

While working through Appendix 4, I realized that I needed to learn some group theory before continuing, so I jumped over to Appendix 2. That was very helpful until I reached A2.2 on representations, where I began to struggle. Fortunately, section A2.1 contained everything I needed to complete Appendix 4 and return to Chapter 5.

To strengthen my understanding going forward, I’ve purchased *Group Theory and Its Application to Physical Problems* by Morton Hamermesh and plan to work through it alongside QCQI. It seems to offer a gentler introduction to group theory than QCQI, although some of the terminology is a bit dated.

As with the earlier chapters, I’ve included my notes and exercise solutions below. 



<!-- toc -->





## The quantum Fourier transform

### Exercise 5.1 {#exercise-51}

 




The transformation from equation 5.2 can be written $T=\frac{1}{\sqrt{N}}\sum_{k=0}^{N-1}\sum_{j=0}^{N-1}e^{2\pi i j k/N}\ket{k}\bra{j}$. In order for $T$ to be unitary $TT^\dagger = T^\dagger T = I$. So let's check this

$$\begin{aligned}
TT^\dagger &= \left(\frac{1}{\sqrt{N}}\sum_{k=0}^{N-1}\sum_{j=0}^{N-1}e^{2\pi i j k/N}\ket{k}\bra{j} \right)\left(\frac{1}{\sqrt{N}}\sum_{k'=0}^{N-1}\sum_{j'=0}^{N-1}e^{2\pi i j' k'/N}\ket{k'}\bra{j'} \right)^\dagger \\
&= \frac{1}{N}\sum_{k=0}^{N-1}\sum_{k'=0}^{N-1}\sum_{j=0}^{N-1}\sum_{j'=0}^{N-1}e^{2\pi i j k/N}e^{-2\pi i j' k'/N}\ket{k}\braket{j \vert j'}\bra{k'} \\
&= \frac{1}{N}\sum_{k=0}^{N-1}\sum_{k'=0}^{N-1}\sum_{j=0}^{N-1}\sum_{j'=0}^{N-1}e^{2\pi i j k/N}e^{-2\pi i j' k'/N}\delta_{jj'}\ket{k}\bra{k'} \\
&= \frac{1}{N}\sum_{k=0}^{N-1}\sum_{k'=0}^{N-1}\sum_{j=0}^{N-1}e^{2\pi i j (k-k')/N}\ket{k}\bra{k'} \\
&= \frac{1}{N}\sum_{k=0}^{N-1}\sum_{k'=0}^{N-1}N\delta_{kk'}\ket{k}\bra{k'} \\
&=\sum_{k'=0}^{N-1}\ket{k}\bra{k} \\
&= I
\end{aligned}$$

Therefore $T$ is unitary. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.2 {#exercise-52}






For the equations below, $N=2^n$.

$$\begin{aligned}
T\ket{00\cdots 0} &= \frac{1}{\sqrt{N}}\sum_{k=0}^{N-1}\sum_{j=0}^{N-1}e^{2\pi i j k/N}\ket{k}\braket{j \vert 00\cdots 0} \\
&= \frac{1}{\sqrt{N}}\sum_{k=0}^{N-1}\sum_{j=0}^{N-1}e^{2\pi i j k/N} \delta_{j,0}\ket{k} \\
&= \frac{1}{\sqrt{N}}\sum_{k=0}^{N-1}\ket{k}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.3 {#exercise-53}






Equation 5.1 is 

$$\begin{aligned}
y_k = \frac{1}{\sqrt{N}}\sum_{j=0}^{N-1}x_je^{2\pi ijk/N}
\end{aligned}$$

where $x_0,\cdots,x_{N-1}$ is the input vector of complex numbers and $y_0,\cdots,y_{N-1}$ is the output vector of complex numbers. We can see that each $y_k$ value requires $\Theta(2^n)$ elementary arithmetic operations since $N=2^n$ and the calculation inside the summation is done $N$ times. The calculation in equation 5.1 is then done $N$ times, once for each $y_k$, so the entire transform is $\Theta(2^n \times 2^n)=\Theta(2^{2n})$.

Equation 5.4 is 

$$\begin{aligned}
\ket{j_1,\cdots,j_n} \to \frac{\left(\ket{0} + e^{2\pi i  0.j_n }\ket{1}\right)\left(\ket{0} + e^{2\pi i  0.j_{n-1}j_n }\ket{1}\right)\cdots \left(\ket{0} + e^{2\pi i  0.j_1j_2\cdots j_n }\ket{1}\right)}{2^{n/2}}
\end{aligned}$$

This is a quantum decomposition, not a classical one so it cannot be used directly, but perhaps we can factor equation 5.1 in a similar fashion. Let $W=e^{2\pi i/N}$, then

$$\begin{aligned}
\begin{bmatrix} y_0 \\\ y_1 \\\ y_2 \\\ \vdots \\\ y_{N-1} \end{bmatrix} &= \frac{1}{\sqrt{N}}\begin{bmatrix} 1 & 1 & 1 & \cdots & 1 \\\ 1 & W & W^2 & \cdots & W^{N-1} \\\ 1 & W^2 & W^4 & \cdots & W^{2(N-1)} \\\ \vdots & \vdots & \vdots & \ddots & \vdots \\\ 1 & W^{N-1} & W^{2(N-1)} & \cdots & W^{(N-1)^2} \end{bmatrix} \begin{bmatrix} x_0 \\\ x_1 \\\ x_2 \\\ \vdots \\\ x_{N-1} \end{bmatrix}
\end{aligned}$$

Let's first look at the $N=2$ case. 

$$\begin{aligned}
\begin{bmatrix} y_0 \\\ y_1 \end{bmatrix} &=  \frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 1  \\\ 1 & W \end{bmatrix} \begin{bmatrix} x_0 \\\ x_1 \end{bmatrix} \\
&=  \frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 1  \\\ 1 & -1 \end{bmatrix} \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= H \begin{bmatrix} x_0 \\\ x_1 \end{bmatrix}
\end{aligned}$$

Now let's look at $N=4$

$$\begin{aligned}
\begin{bmatrix} y_0 \\\ y_1 \\\ y_2 \\\ y_3 \end{bmatrix} &=  \frac{1}{2}\begin{bmatrix} 1 & 1 & 1 & 1  \\\ 1 & W & W^2 & W^3 \\\ 1 & W^2 & W^4 & W^6 \\\ 1 & W^3 & W^6 & W^9 \end{bmatrix} \begin{bmatrix} x_0 \\\ x_1 \\\ x_2 \\\ x_3 \end{bmatrix} \\
&=  \frac{1}{2}\begin{bmatrix} 1 & 1 & 1 & 1  \\\ 1 & i & -1 & -i \\\ 1 & -1 & 1 & -1 \\\ 1 & -i & -1 & i \end{bmatrix} \begin{bmatrix} x_1 \\\ x_2 \\\ x_3 \\\ x_4 \end{bmatrix} \\
&= \left(\frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 0 & 1 & 0 \\\ 0 & 1 & 0 & 1 \\\ 1 & 0 & -1 & 0 \\\ 0 & 1 & 0 & -1 \end{bmatrix}\right)\left(\begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & i \end{bmatrix}\right)\left(\frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 1 & 0 & 0 \\\ 1 & -1 & 0 & 0 \\\ 0 & 0 & 1 & 1 \\\ 0 & 0 & 1 & -1 \end{bmatrix}\right)\left(\begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \end{bmatrix}\right)\\
&= (H \otimes I_2)R_2(I_2 \otimes H)SWAP \\
\end{aligned}$$

This is the same form as the circuit in figure 5.1. Looking at this circuit, we see that there will be $n$ single qubit Hadamard gates applied. Each of those Hadamard gates will involve $2 (2^n)$ arithmetic operations. Then there will also be up to $n-1$ controlled $R$ gates for each qubit. Since these operations are diagonal, they can be combined with the matrix for a neighboring Hadamard gate without increasing the number of non-zero entries in the matrix. The SWAP gate will also have $2^n$ arithmetic operations. Therefore, the circuit as a whole has $2n2^n + 2^n$ arithmetic operations, which is $\Theta(n2^n)$. 

Since the circuit in figure 5.1 has the same matrix representation as the classical Fourier transform in equation 5.1, the equation can be factored in the same way. When performing the calculation in this factored form, the classical Fourier transform can be done in $\Theta(n2^n)$ arithmetic operations.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 5.4 {#exercise-54}






I came up with this gate

<img width="497" height="198" alt="image" src="https://github.com/user-attachments/assets/6daa4352-e9c1-4be3-8dc2-54c7cfd0e275" />

Using single qubit phase gates

$$\begin{aligned}
P(\theta) = \begin{bmatrix} 1 & 0 \\\ 0 & e^{i\theta} \end{bmatrix}
\end{aligned}$$

Which has this effect on the qubits

$$\begin{aligned}
CNOT_{12} P_2(-2\pi/2^{k+1}) CNOT_{12} P_2(2\pi/2^{k+1}) P_1(2\pi/2^{k+1}) 
= \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & e^{2\pi/2^k} \end{bmatrix}
\end{aligned}$$

I confirmed this result with this python script

```
from sympy import simplify, Matrix, symbols, exp, I, pi
from sympy.physics.quantum import TensorProduct

k = symbols('k', real=True)

Identity = Matrix([[1, 0], [0, 1]])

CNOT = Matrix([
    [1,0,0,0],
    [0,1,0,0],
    [0,0,0,1],
    [0,0,1,0]
    ])


Pp = Matrix([
    [1,0],
    [0,exp(I*2*pi/2**(k+1))],
    ])

Pn = Matrix([
    [1,0],
    [0,exp(-I*2*pi/2**(k+1))],
    ])


Ppa = TensorProduct(Pp, Identity)
Ppb = TensorProduct(Identity, Pp)
Pnb = TensorProduct(Identity, Pn)

circuit =simplify(CNOT @ Pnb @ CNOT @ Ppb @ Ppa)

print(circuit)
```

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.5 {#exercise-55}






Since the quantum Fourier transform is a unitary operation, the adjoint of the operation will give us the inverse quantum Fourier transform. So, to construct a circuit for the inverse quantum Fourier transform, we can take the circuit in Figure 5.1 (or Box 5.1) and apply the adjoints of each of the gates in reverse order. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.6 {#exercise-56}






From equation 4.69 we know that

$$\begin{aligned}
E(U,V) &= E(U_m U_{m-1}\cdots U_1, V_mV_{m-1}\cdots V_1) \\
&\leq \sum_{j=1}^m E(U_j,V_j) \\
&= \frac{n(n-1)}{2}\frac{1}{p(n)} & \text{since there are $\frac{n(n-1)}{2}$ controlled-$R_k$ gates}\\
&= \Theta(n^2/p(n))
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## Phase estimation


### Exercise 5.7 {#exercise-57}






The Hadamard gates transforms 

$$\begin{aligned}
\ket{0}\ket{0}\cdots\ket{0}\ket{u} \to \frac{1}{2^{t/2}}(\ket{0} + \ket{1})(\ket{0} + \ket{1})\cdots(\ket{0} + \ket{1})\ket{u}.
\end{aligned}$$

Then the controlled- $U$ gates transform the following

$$\begin{aligned}
\frac{1}{2^{t/2}}(\ket{0} + \ket{1})(\ket{0} + \ket{1})\cdots(\ket{0} + \ket{1})\ket{u} \\
\to \frac{1}{2^{t/2}}\left(\ket{0} \otimes I + \ket{1} \otimes U^{2^{t-1}}\right)\left(\ket{0} \otimes I + \ket{1} \otimes U^{2^{t-2}}\right)\cdots\left(\ket{0}\otimes I + \ket{1}\otimes U^{2^0}\right)\ket{u} \\
= \frac{1}{2^{t/2}}\sum_{j_0,j_1,\cdots,j_{t-1}=0}^{1} \ket{j_{t-1}\cdots j_1 j_0} U^{j_{t-1}2^{t-1}}U^{j_{t-2}2^{t-2}}\cdots U^{j_0 2^0} \ket{u} \\
= \frac{1}{2^{t/2}}\sum_{j_0,j_1,\cdots,j_{t-1}=0}^{1} \ket{j_{t-1}\cdots j_1 j_0} U^{j_{t-1}2^{t-1}+j_{t-2}2^{t-2}+\cdots + j_0 2^0} \ket{u} \\
= \frac{1}{2^{t/2}}\sum_{j=0}^{2^t-1} \ket{j} U^j \ket{u} & \text{for $j=j_{t-1}2^{t-1}+j_{t-2}2^{t-2}+\cdots + j_0 2^0$}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.8 {#exercise-58}






Equation 5.35 is

$$\begin{aligned}
t = n + \left\lceil \log\left(2+\frac{1}{2\epsilon}\right) \right\rceil
\end{aligned}$$

Earlier in section 5.2.1 the authors showed that when selecting $t$ given by equation 5.35, the probability of obtaining a measurement of $\phi$ accurate to $n$ bits is given by $p_{accurate} \geq 1-\epsilon$.

The output from the algorithm is now given by

$$\begin{aligned}
\sum_u c_u \ket{\tilde{\phi_u}}\ket{u}
\end{aligned}$$

where $\ket{u}$ has a probability $p_u = \vert c_u \vert^2$ of being measured. Therefore, the probability of accurately measuring $\phi_u$ is given by multiplying the probability of measuring $\ket{u}$ with the probability of obtaining an accurate measurement. Therefore, the probability of measuring $\phi_u$ accurate to $n$ bits is $p \geq p_u p_{accurate} = \vert c_u\vert^2(1-\epsilon)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.9 {#exercise-59}






Since the eigenvalues are $\pm 1$ we know that $\phi = 0$ or $\phi = \frac{1}{2}$. To express these values exactly we need $t=1$ bit. Therefore, the circuit will be as follows

<img width="375" height="195" alt="image" src="https://github.com/user-attachments/assets/56ff5cb0-3241-4d54-8689-0b20dda0901f" />

The Fourier transform for a one-bit gate is just one Hadamard gate. So $FT^\dagger = H^\dagger = H$. Looking at exercise 4.34, we see that this circuit is the same as the one in that exercise.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## Appendix 2

### Exercise A2.1 {#exercise-a21}





Let $G$ be a finite multiplicative group with $\vert G \vert=n$ and let $g\in G$. Since $G$ is a multiplicative group, $g^r \in G$ for all positive integer $r$. Let's consider the $n+1$ elements $e,g,g^2,\cdots,g^n$. Since there are only $n$ elements in $G$, by the pigeonhole principle two of these must be equal, therefore for some integers $0\leq i < j \leq n$ 

$$\begin{aligned}
g^i &= g^j \\
e &= g^{j-i} & \text{multiply both sides by $(g^i)^{-1}$} \\
e &= g^r & \text{let $r=j-i$}
\end{aligned}$$

Thus for any element $g$ of a finite group, there always exists a positive integer $r$ such that $g^r=e$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A2.2 {#exercise-a22}





Let $G$ be a finite multiplicative group with $\vert G \vert=n$ and $H$ be a subgroup of $G$. Additionally, let $h$ be the elements of $H$ and $g$ be the elements of $G$. Since $H$ is a subgroup of $G$ we know that $h\in G$ for all $h$. Therefore, $gh \in G$ for any $h \in H$ and $g \in G$. The map $H \to gH$ is a bijection and so $\vert gH \vert = \vert H \vert$. 

Let's consider elements $x$. If $x \in gH$ then there must exist an $h \in H$ such that $gh=x$ and so $xH=(gh)H=g(hH)=gH$. Therefore, if $x$ belongs to $gH$ then $gH=xH$ and thus the cosets $gH$ are disjoint. 

Every element of $G$ lies in some $gH$ since $e \in H$, therefore $\lbrace gH : g\in G\rbrace$ covers $G$. 

Since the cosets $gH$ are disjoint and cover $G$, they partition $G$. 

Let $k$ be the number of cosets. Each coset has $\vert H \vert$ elements so $\vert G \vert = k \vert H \vert$. Therefore $\vert H \vert$ divides $\vert G \vert$. This proves Lagrange's theorem. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A2.3 {#exercise-a23}






Let $r$ be the order of an element $g\in G$. Then $\braket{g} = \lbrace e, g, g^2, \cdots, g^{r-1} \rbrace$ is a subgroup of $G$ and $\vert \braket{g} \vert = r$. Using Lagrange's theorem, we know that $\vert \braket{g} \vert$ divides $\vert G \vert$. Therefore the order of an element $g\in G$ divides $\vert G \vert$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A2.4 {#exercise-a24}






Let $G_x = \lbrace g^{-1}xg \vert g\in G \rbrace$ and $G_y = \lbrace h^{-1}yh \vert h\in G \rbrace$ for elements $x$ and $y$ in a group $G$. If $y\in G_x$ that means for some $g\in G$, $y=g^{-1}x g$ therefore for any $h \in G$

$$\begin{aligned}
h^{-1}yh &= h^{-1}(g^{-1} x g) h \\
&= (gh)^{-1} x (gh) \\
&\in G_x & \text{since $gh \in G$}
\end{aligned}$$

Therefore, if $y\in G_x$ then $G_y \subseteq G_x$. The same argument can be made with $x$ and $y$ swapped giving $G_x \subseteq G_y$. Thus, $G_x=G_y$ if $y \in G_x$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A2.5 {#exercise-a25}






A group is said to be Abelian if $g_1 g_2 = g_2 g_1$ for all $g_1,g_2 \in G$. Therefore, for any $g$

$$\begin{aligned}
g^{-1} x g &= g^{-1}g x & \text{since the group is Abelian} \\
&= ex \\
&= x
\end{aligned}$$

Thus every conjugate of $x$ equals $x$. Therefore if $x$ is an element of an Abelian group $G$ then $G_x = \lbrace x \rbrace$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A2.6 {#exercise-a26}






Let $G$ be a finite group with $\vert G \vert = p$ where $p$ is a prime number. Consider the subgroup $\braket{g}$ for any $g\in G$ with $g\neq e$. From Lagrange's theorem we know that $\vert \braket{g}\vert \vert \vert G \vert$. Since $p$ is prime and $\vert \braket{g} \vert \neq 1$ (since $g \neq e$), then $\vert \braket{g} \vert = p$ and so $\braket{g}=G$. Therefore any group of prime order is cyclic. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A2.7 {#exercise-a27}






Let $G$ be a cyclic group of order $r$ such that any element $g\in G$ can be expressed as $a^n$ for $n \in \lbrace 0, 1, \cdots, r-1 \rbrace = \mathbb{Z_r}$. Let $H$ be a subgroup of $G$, where the elements of $H$ are $a^k$ for some set of integers $k \in K$, where $K$ is a subgroup of the additive group $\mathbb{Z_r}$.

Since $K$ is a subgroup of $\mathbb{Z_{r}}$, its elements must form an arithmetic progression modulo $r$ with a common difference $d$ where $d \vert r$. This can be seen by taking any element $k\in K$ and writing it in terms of $d$ which we'll say is the least positive element in $K$, an integer multiplier $m$, and some other integer $t$ where $0\leq t\leq d$, so $k=md+t$. Since $k$ and $md$ are in $K$, their difference is also in $K$, therefore $k-md=(md+t)-md=t$ and so $t\in K$. However, we said $t<d$ and $d$ is the least positive element in $K$, therefore $t=0$ and so $k=md$.  Since $a^{r}=e\in H$, we know $r = md$ for some integer $m$, thus $d \vert r$. Since $r \mod r = 0$, the maximum value of $m$ is $\frac{r-d}{d}$.

We can now say that $K=\lbrace 0,d,2d,\cdots,r-d\rbrace$, and so $H=\braket{a^d}$. Therefore $H$ is cyclic. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A2.8 {#exercise-a28}






If $g\in G$ has finite order $r$ then $g^{m}=g^{m \mod r}$ because $g^r=e$ and $m$ can be written as $m=qr+s$ for some $q$ and $s$ (per equation A4.2), so $g^m=(g^r)^q g^s=e^qg^s=g^s=g^{m \mod r}$. By the same argument $g^{n}=g^{n \mod r}$. 

If $0\leq m,n < r$ and $g^m=g^n$, then $g^{m-n}=e$. Since $r$ is the least positive integer with $g^r=e$, we must have $r \vert (m-n)$ or $m-n=0$. We know $\vert m - n \vert < r$, so $m-n=0$, hence $m=n$. 

For general $m,n$ from above we know $g^{m}=g^{m \mod r}$ and $g^{n}=g^{n \mod r}$, so if $g^m=g^n$, then $g^{m \mod r}=g^{n \mod r}$ and therefore $m \mod r = n \mod r$ or $m \equiv n \mod r$. 

If $m \equiv n \mod r$, then $g^m=g^{n+kr}=g^n(g^r)^k=g^ne^k=g^n$.

Therefore, if $g\in G$ has finite order $r$, then $g^m=g^n$ if and only if $m \equiv n \mod r$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A2.9 {#exercise-a29}






If there exists an $h \in H$ such that $g_2=g_1h$, then $g_2H=(g_1h)H=g_1(hH)=g_1H$ and so $g_1$ and $g_2$ must be in the same coset.  

If $g_1$ and $g_2$ are in the same coset, then $g_1H=g_2H$. Multiply both sides by $g_1^{-1}$, then $H=g_1^{-1}g_2 H$, so $g_1^{-1}g_2 \in H$. Let $h=g_1^{-1}g_2 \in H$. Then $g_2=g_1 h$. 

Thus, $g_1,g_2 \in G$ are in the same coset of $H$ in $G$ if and only if there exists some $h\in H$ such that $g_2=g_1h$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A2.10 {#exercise-a210}






The map $H \to gH$ is a bijection and so $\vert gH \vert = \vert H \vert$. So all the cosets have the same size as $H$. 

Let's consider elements $x \in G$. If $x \in gH$ then there must exist an $h \in H$ such that $gh=x$ and so $xH=(gh)H=g(hH)=gH$. Therefore, if $x$ belongs to $gH$ then $gH=xH$ and thus the cosets $gH$ are disjoint. 

Every element of $G$ lies in some $gH$ since $e \in H$, therefore $\lbrace gH : g\in G\rbrace$ covers $G$. 

Therefore, the number of cosets of $H$ is given by $N=\frac{\vert G \vert}{\vert H \vert}$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A2.11 {#exercise-a211}





For this section of the book $G$ is assumed to be finite. The character of a matrix group $G \subset M_n$ is a function on the group defined by $\chi(g)=\text{tr}(g)$, for $g\in G$, where $\text{tr}(\cdot)$ is the usual trace function on matrices. For this exercise I'll prove these properties for unitary matrix groups. The next exercise we show that every matrix group is equivalent to a unitary matrix group. 

For (1)

$$\begin{aligned}
\chi(I)&=\text{tr}(I)\\
&= \sum_i^n I_{ii} \\
&= n 
\end{aligned}$$

For (2)

$$\begin{aligned}
\vert \chi(g) \vert &=\vert \text{tr}(g)\vert\\
&=\left\vert \sum_i^n g_{ii}\right\vert \\
&= \left\vert \sum_i^n \lambda_i \right\vert & \text{where $\lambda_i$ are the eigenvalues of $g$} \\
&\leq \sum_i^n \vert \lambda_i \vert = n  & \text{if $g$ is unitary}\\
\end{aligned}$$

For (3)

If $g$ is unitary then all the eigenvalues can be written of the form $e^{i\theta}$. Then,

$$\begin{aligned}
\vert \chi(g) \vert &= \left\vert \sum_i^n e^{i\theta} \right\vert \\
&\leq n
\end{aligned}$$

and equality occurs if and only if all terms point in exactly the same direction in the complex plane. That is, $e^{i\theta_1}=e^{i\theta_2}=\cdots = e^{i\theta_n}e^{i\theta}$. If all eigenvalues are equal to $e^{i\theta}$ then $g=e^{i\theta}I$. Therefore, $\vert \chi(g)\vert=n$ implies $g=e^{i\theta}I$.

For (4)

Conjugation class $G_x=\lbrace g^{-1}xg \vert g\in G \rbrace$ for $x\in G$. So

$$\begin{aligned}
\chi(g^{-1}xg) &=\text{tr}(g^{-1}xg)\\
&= \text{tr}(xgg^{-1}) & \text{per exercise 2.37}\\
&= \text{tr}(xI) \\
&= \text{tr}(x) \\
&= \chi(x)
\end{aligned}$$

So $\chi$ for all elements of $G_x$ will be the same. 

For (5)

$$\begin{aligned}
\chi(g^{-1}) &= \text{tr}(g^{-1}) \\
&= \text{tr}(g^\dagger g g^{-1}) & \text{since $g^\dagger g = I$ if $g$ is unitary}\\
&= \text{tr}(g^\dagger) \\
&= \text{tr}(g^T)^\ast \\
&= \text{tr}(g)^\ast \\
&= \chi(g)^\ast
\end{aligned}$$

For (6)

An algebraic number is a number that is a root of a non-zero polynomial in one variable with integer (or rational) coefficients. 

For a finite group, each $g\in G$ has a finite order $m$. Then $g^m=I$, so the minimal polynomial of $g$ divides $x^m-1 \in \mathbb{Z}\lbrack x \rbrack$. Hence the eigenvalues of $g$ are $m$-th roots of unity, which are algebraic integers. The sum $\chi(g)$ is therefore an algebraic number. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A2.13 {#exercise-a213}





For a matrix group $G$ to be irreducible, it must not be equivalent to another matrix group $H$ which is of block diagonal form. For a matrix group $G$ to be Abelian, $g_1 g_2=g_2 g_1$ for all $g \in G$. We can rewrite this requirement in the form of Lemma A2.2, where $H=G$, $S=g_1$, $g_i=g_2$, and $h_i = g_2$. This tells us that either $g_1$ is the zero matrix or $g_1$ is a square nonsingular matrix. A nonsingular matrix is a square matrix that is invertible, i.e. $g_1 g_1^{-1}=g_1^{-1}g_1=I_n$.  

Let's now consider the eigenvalue $\lambda_1$ of $g_1$ for eigenvector $v$, so $g_1 v = \lambda_1 v$. Since $g_1$ commutes with $g_2$, $g_2(g_1 v) = g_2 \lambda_1 v = \lambda_1 (g_2 v)$ and so $g_2 v$ is also an eigenvector of $g_1$ with the same eigenvalue $\lambda_1$. Using this, one can extrapolate that all eigenvectors of $g_1$ have the eigenvalue $\lambda_1$ and so $g_1=\lambda_1 I_n$. Since $g_1$ was an arbitrary element of $G$, this means all $g\in G$ are the form $g=\lambda I_n$.

When $g=\lambda I_n$ all matrix groups for $n>1$ are automatically completely reducible because you can trivially write each matrix as $\lambda I_n = diag(\lambda, \lambda, \cdots, \lambda)$ which is in block-diagonal form. Therefore, every irreducible Abelian matrix group must be one-dimensional. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |









## Appendix 4


### Exercise A4.1 {#exercise-a41}






We know that there exists an integer $k$ such that $b=ka$. We also know that there exists an integer $l$ such that $c=lb$. Knowing this, we can say that $c = lb = lka$. Since $l$ and $k$ are integers, $lk$ is an integer. Therefore, $a \vert c$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A4.2 {#exercise-a42}





We know that there exists an integer $k$ such that $a=kd$. We also know that there exists an integer $l$ such that $b=ld$. Knowing this, we can say that $ax+by = (kd)x + (ld)y = d(kx+ly)$. Therefore, since $kx+ly \in \mathbb{Z}$ we can say $d \vert (ax+by)$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A4.3 {#exercise-a43}





If $a\vert b$ then there exists some integer $k$ such that $b=ka$. Since $a$ and $b$ are both positive integers, then $k\geq 1$ and so $a\leq b$. If $b\vert a$ is also true, then $a=lb$ for some integer $l$. Therefore, $a=lb=lka$ and so $lk=1$. Since $l\geq 1$ and $k\geq 1$ and $lk = 1$ then $l=k=1$ and thus $a=b$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A4.4 {#exercise-a44}





$$\begin{aligned}
697 &= 17 \times 41 \\
36300 &= 2^2 \times 3 \times 5^2 \times 11^2
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.5 {#exercise-a45}





Let's assume $a$ is an integer with value $1\leq a\leq p-1$. Since $p$ is a prime number and $1\leq a\leq p-1$ we know that $\text{gcd}(a,p)=1$, therefore by Theorem A4.2 we know that $ax+py=1$ where $x$ and $y$ are integers. Rearranging the equation, we get $ax = 1 + (-y)p$. Here we can see that $x$ is the multiplicative inverse modulo $p$ of $a$. 

Now Let's assume $a$ is an integer with value $1\leq a \leq p^2-1$. Since $p$ is a prime number, we know that $\text{gcd}(a,p^2)=p$ when $a=p,2p,3p,\cdots,(p-1)p$ and $\text{gcd}(a,p^2)=1$ for all other $a$. By the same reasoning as the previous proof, if $a$ is not a multiple of $p$ then $a$ has a multiplicative inverse modulo $p^2$ and if $a$ is a multiple of $p$ then it does not. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.6 {#exercise-a46}





We need to find $b$ such that $17b = 1 + k24$ for some integer $k$. This relation is true for $k=12$ and $b=17$. Therefore, 17 is a multiplicative inverse of 17 modulo 24. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.7 {#exercise-a47}





We need to find $b$ such that $(n+1)b = 1 + kn^2$ for some integer $k$. This relation is true for $k=n$ and $b=n^2-n+1$

$$\begin{aligned}
1+n^3 &= (n+1)b \\
&= (n+1)(n^2-n+1) \\
&=n^3+1 
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.8 {#exercise-a48}





Since $b$ and $b'$ are multiplicative inverses of $a$ modulo n, we know $ab = 1+kn$ and $ab'=1+ln$ for some integers $k$ and $l$. Therefore, $a(b-b') = (k-l)n = 0 \mod n$ and so $n \vert a(b-b')$. Because an inverse exists, we know $\text{gcd}(a,n) = 1$, and so $n \vert (b-b')$ which means $b=b' \mod n$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.9 {#exercise-a49}





Here is a procedure
1) Look at prime factorization and identify factors shared by both $a$ and $b$
2) multiply those shared factors together to get gcd

Here are the prime factorizations

$$\begin{aligned}
6825 &= 3 \times 5^2 \times 7 \times 13\\
1430 &= 2 \times 5 \times 11 \times 13\\
\text{gcd}(6825, 1430) &= 5 \times 13 = 65
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.10 {#exercise-a410}





First we need to find the prime factorization of 187

$$\begin{aligned}
187 = 11 \times 17
\end{aligned}$$

Then we use equation A4.23 

$$\begin{aligned}
\varphi(187) &= \prod_{j=1}^k p_j^{\alpha_{j}-1}(p_j-1) \\
&= 11^{1-1}(11-1) \times 17^{1-1}(17-1) \\
&= 160
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.11 {#exercise-a411}





Let's first look at the case where $n=p^\alpha$. Here the only divisors are $d=1,p, p^2, \cdots, p^\alpha$.

$$\begin{aligned}
n &= \sum_{d\vert n}\varphi(d)\\
&= \varphi(1) + \varphi(p) + \cdots + \varphi(p^\alpha) \\
&= 1 + p^{1-1}(p-1) + p^{2-1}(p-1) + \cdots + p^{\alpha-1}(p-1) & \text{equation A4.23}\\
&= 1 + \sum_{j=0}^{\alpha-1}p^{j+1} - p^j \\
&= \sum_{j=0}^{\alpha}p^{j} - \sum_{i=0}^{\alpha-1} p^i \\
&= p^\alpha \\
&= n
\end{aligned}$$

Then for $n=p_1^{\alpha_1}p_2^{\alpha_2}\cdots p_k^{\alpha_k}$. Now $d$ can equal 1, all powers of $p_j$ up to $\alpha_j$, and any multiples of those. 

$$\begin{aligned}
n &= \sum_{d\vert n}\varphi(d)\\
&= \varphi(p_1^{\alpha_1}p_2^{\alpha_2}\cdots p_k^{\alpha_k}) + \varphi(p_2^{\alpha_2}\cdots p_k^{\alpha_k}) +\varphi(p_1^{\alpha_1}\cdots p_k^{\alpha_k}) + \varphi(p_1^{\alpha_1}p_2^{\alpha_2}\cdots p_{k-1}^{\alpha_{k-1}}) + \cdots + \varphi(1) \\
&= \varphi(p_1^{\alpha_1})\varphi(p_2^{\alpha_2})\cdots\varphi(p_k^{\alpha_k}) + \varphi(p_2^{\alpha_2})\cdots\varphi(p_k^{\alpha_k}) + \varphi(p_1^{\alpha_1})\cdots\varphi(p_k^{\alpha_k}) + \cdots + \varphi(p_1^{\alpha_1})\varphi(p_2^{\alpha_2})\cdots\varphi(p_{k-1}^{\alpha_{k-1}}) + \cdots + \varphi(1) & \text{per A4.22}\\
&= \sum_{j_1,j_2,\cdots,j_k=0}^{\alpha_1,\alpha_2,\cdots\alpha_k} \varphi(p_1^{j_1})\varphi(p_2^{j_2})\cdots\varphi(p_k^{j_k}) \\
&= \left(\sum_{j_1=0}^{\alpha_1} \varphi(p_1^{j_1})\right)\left(\sum_{j_2=0}^{\alpha_2} \varphi(p_2^{j_2})\right)\cdots\left(\sum_{j_k=0}^{\alpha_k} \varphi(p_k^{j_k})\right) \\
&= p_1^{\alpha_1}p_2^{\alpha_2}\cdots p_k^{\alpha_k} & \text{per the first part of this exercise} \\
&= n
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A4.12 {#exercise-a412}





$\mathbb{Z}_n^\ast$ is the set of all elements in $\mathbb{Z}_n$ which have inverses modulo $n$, which is the set of all elements in $\mathbb{Z}_n$ which are co-primes to $n$. Therefore, we know $a \in \mathbb{Z}_n^\ast$ if and only if there is a $b \in \mathbb{Z}_n^\ast$ such that $ab=1\mod n$. 

Now we need to verify that $\mathbb{Z}_n^\ast$ forms a group under the operation of multiplication modulo $n$, by confiming the closure, associativity, identity, and inverses properties of a group. 

For closure, if $a_1 \in \mathbb{Z}_n^\ast$ then there exists a $b_1 \in \mathbb{Z}_n^\ast$ such that $a_1b_1=1\mod n$. Similarly, if $a_2 \in \mathbb{Z}_n^\ast$ then there exists a $b_2 \in \mathbb{Z}_n^\ast$ such that $a_2b_2=1\mod n$. Therefore, for $a_1 \cdot a_2$ we have a $b_1 \cdot b_2$ such that

$$\begin{aligned}
(a_1a_2)(b_1b_2) &= (a_1b_1)(a_2b_2) \\
&= (1 \mod n)(1 \mod n) \\
&= 1 \mod n
\end{aligned}$$

and so $a_1 \cdot a_2 \in \mathbb{Z}_n^\ast$ for all $a_1,a_2 \in \mathbb{Z}_n^\ast$. 

For associativity, $(a_1\cdot a_2) \cdot a_3 = a_1 \cdot (a_2 \cdot a_3)$ becuase multiplication in $\mathbb{Z}$ is associative and reduction mod $n$ respects products, so multiplication mod $n$ is associative. 

For identity, $1$ satisfies $1\cdot a = a\cdot 1 = a$ for all $a\in \mathbb{Z}_n^\ast$. Also $\text{gcd}(1,n)=1$ so $1\in \mathbb{Z}_n^\ast$ and is the identity element.

For inverses, all $a \in \mathbb{Z}_n^\ast$ have an inverse $b \in \mathbb{Z}_n^\ast$ such that $ab=1\mod n$.

The size of $\mathbb{Z}_n^\ast$ is $\varphi(n)$ since by definition $\varphi(n)$ is the number of positive integers less than $n$ which are co-prime to $n$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.13 {#exercise-a413}





From Theorem A4.9, we know that if $a$ is co-prime to $n$, then $a^{\varphi(n)} = 1 \mod n$. Though, it is possible that the powers of $a$ may cycle earlier, so we'll say there is a $r\leq \varphi(n)$ such that $a^r=1\mod n$. This can be written as $a^{m}a^{r-m}=1\mod n$ for integer $m$ with values $1\leq m < r$ and so $S=\lbrace 1, a, a^2, \cdots, a^{r-1}\rbrace$ and is size $r$.

For $S$ to be a subgroup of $\mathbb{Z}_n^\ast$ it needs to satisfy the group axioms under the same operation as $\mathbb{Z}_n^\ast$.

For closure, if $a^i \in S$ and $a^j \in S$ then $a^ia^j=a^{i+j} \in S$

For associativity, $(a^ia^j)a^k=a^i(a^ja^k)$

For identity, $1 \in S$

For inverses, for each $a^m$ there is a $a^{r-m}$ which is its inverse mod $n$, as shown above.

Therefore, $S$ is a subgroup of $\mathbb{Z}_n^\ast$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.14 {#exercise-a414}





We know from [exercise A4.12](#exercise-a412) that $\mathbb{Z}_n^\ast$ forms a group of size $\varphi(n)$. If $g$ is a generator for $\mathbb{Z}_n^\ast$ then $\braket{g} = \lbrace 1, g, g^2, \cdots \rbrace = \mathbb{Z}_n^\ast$ and so $g$ must have order $\varphi(n)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.15 {#exercise-a415}





Lagrange's theorem says that if $H$ is a subgroup of a finite group $G$ then $\vert H \vert$ divides $\vert G \vert$. 

From [exercise A4.12](#exercise-a412) we know that $\mathbb{Z}_n^\ast$ is a group of size $\varphi(n)$. From exercise A4.12 we know that $S=\lbrace 1, a, a^2, \cdots, a^{r-1}\rbrace$ is a subgroup of $\mathbb{Z}_n^\ast$ where $r$ is the least value such that $a^r=1\mod n$ and that $\vert S\vert = r$. From Lagrange's theorem, we know that $r$ must divide $\varphi(n)$ and so $\varphi(n) = mr$ for some integer $m$. Therefore,

$$\begin{aligned}
a^{\varphi(n)} &= a^{mr} \\
&= (a^r)^m \\
&\equiv 1^m \mod n \\
&\equiv 1 \mod n
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.16 {#exercise-a416}





From theorem A4.9, $x^{\varphi(N)}=1 \mod N$. From [exercise A4.15](#exercise-a415), we know that this means there is a subgroup $S=\lbrace 1, x, x^2, \cdots, x^{r-1}\rbrace$ of size $r$ where $r$ divides $\varphi(N)$. This $r$ is equal to the order of $x \mod N$. Therefore, the order of $x$ modulo $N$ must divide $\varphi(N)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A4.17 {#exercise-a417}
 




If we had an algorithm that efficiently identified all the factors of a number, we could use the following algorithm to efficiently find the order modulo $N$ of any $x$ co-prime to $N$: <br>
(1) Factor $N=\prod_i p_i^{\alpha_i}$ <br>
(2) Calculate $\varphi(N) = \prod_i p_i^{\alpha_{i}-1}(p_i-1)$  and set $r=\varphi(N)$ <br>
(3) Factor $\varphi(N) = \prod_j q_j^{\beta_j}$ and find its distinct primes $\lbrace q_1, \cdots, q_t\rbrace$<br>
(4) For each $q\in \lbrace q_1, \cdots, q_t \rbrace$: while $q \vert r$ and $x^{r/q} = 1 \mod N$ set $r = r/q$. <br>
(5) return $r$

We know step (1) and step (3) are efficient because they are the efficient factoring algorithm. Step (2) is efficient because it is $O(\log N)$ integer multiplications. Step (4) is efficient because it is $O(\log \varphi(N)) \leq O(\log N)$ arithmetic checks. Therefore, this order modulo $N$ algorithm is efficient.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise A4.18 {#exercise-a418}





$$\begin{aligned}
x &= \frac{19}{17} \\
&= 1 + \frac{2}{17} \\
&= 1 + \frac{1}{\frac{17}{2}} \\
&= 1 + \frac{1}{8 + \frac{1}{2}} \\
\end{aligned}$$

So, $x=\lbrack 1, 8, 2 \rbrack$

$$\begin{aligned}
x &= \frac{77}{65} \\
&= 1 + \frac{12}{65} \\
&= 1 + \frac{1}{\frac{65}{12}} \\
&= 1 + \frac{1}{5 + \frac{5}{12}} \\
&= 1 + \frac{1}{5 + \frac{1}{\frac{12}{5}}} \\
&= 1 + \frac{1}{5 + \frac{1}{2 + \frac{2}{5}}} \\
&= 1 + \frac{1}{5 + \frac{1}{2 + \frac{1}{\frac{5}{2}}}} \\
&= 1 + \frac{1}{5 + \frac{1}{2 + \frac{1}{2 + \frac{1}{2}}}} \\
\end{aligned}$$

So, $x = \lbrack 1, 5, 2, 2, 2, \rbrack$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise A4.19 {#exercise-a419}





From Theorem A4.15 we know that for $2\leq n \leq N$

$$\begin{aligned}
p_n \equiv a_np_{n-1} + p_{n-2} \\
q_n \equiv a_nq_{n-1} + q_{n-2}
\end{aligned}$$

For $n=0$ we are given

$$\begin{aligned}
p_0 = a_0 \\
q_0 = 1
\end{aligned}$$

For $n=1$ we are given

$$\begin{aligned}
p_1 = 1 + a_0a_1 \\
q_1 = a_1
\end{aligned}$$

Therefore,

$$\begin{aligned}
q_np_{n-1} - p_nq_{n-1} \\
= (a_nq_{n-1} + q_{n-2})p_{n-1}-(a_np_{n-1} + p_{n-2})q_{n-1} \\
= a_nq_{n-1}p_{n-1} + q_{n-2}p_{n-1} - a_np_{n-1}q_{n-1} - p_{n-2}q_{n-1}\\
= q_{n-2}p_{n-1} - p_{n-2}q_{n-1}\\
= -(q_{n-1}p_{n-2} - p_{n-1}q_{n-2}) & \text{this is $-1$ times the same expression at $n-1$}\\
= \vdots & \text{repeat until we reach the base case of $n=1$}\\
= (-1)^{n-1}(q_1p_0 - p_1q_0) \\
= (-1)^{n-1}(a_1a_0 - (1+a_0a_1)) \\
= (-1)^{n-1}(-1)\\
= (-1)^n
\end{aligned}$$

Therefore, $q_np_{n-1}-p_nq_{n-1}=(-1)^n$ for $n\geq 1$. 

If $d$ divides $p_n$ and $q_n$ then $d$ divides $q_np_{n-1}-p_nq_{n-1} = (-1)^n$. So $d \vert 1$ and so $d=1$ which means $\text{gcd}(p_n,q_n)=1$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## Order-finding and factoring applications


### Exercise 5.10 {#exercise-510}





So we want to find the least positive $r$ such that $x^r=1\mod 21$, when $x=5\mod 21$. 

Check $r=1$, $x = 5 \mod 21 \neq 1 \mod 21$ <br>
Check $r=2$, $x^2 = 4 \mod 21 \neq 1 \mod 21$ <br>
Check $r=3$, $x^3 = 20 \mod 21 \neq 1 \mod 21$ <br>
Check $r=4$, $x^4 = 16 \mod 21 \neq 1 \mod 21$ <br>
Check $r=5$, $x^5 = 17 \mod 21 \neq 1 \mod 21$ <br>
Check $r=6$, $x^6 = 1 \mod 21$

The least positive $r$ such that $x^r=1\mod 21$ is 6. Therefore, the order of $x$ is 6.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.11 {#exercise-511}





From Theorem A4.9 we know that $x^{\varphi(N)} = 1 \mod N$ and so $r \leq \varphi(N)$. By definition, $\varphi(N)$ is the number of positive integers less than $N$ which are co-prime to $N$, which means $\varphi(N) \leq N$. Therefore, $r \leq \varphi(N) \leq N$. Thus, the order of $x$ satisfies $r \leq N$.   

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.12 {#exercise-512}





From equation 5.36, $U\ket{y} \equiv \ket{xy \mod N}$ with $y\in\lbrace 0,1 \rbrace^L$ and so,

$$\begin{aligned}
\braket{ Uy \vert Uy'} &= \braket{xy \mod N \vert xy' \mod N} \\
&= \delta_{xy \mod N, xy' \mod N} \\
&= \delta_{y,y'} & \text{see below for justification}\\
\end{aligned}$$

For the delta function above, we wanted to find when $xy \equiv xy' \mod N$. Using the fact that $x$ is co-prime to $N$ and therefore has an inverse modulo $N$ we can write,

$$\begin{aligned}
xy &\equiv xy' \mod N \\
x^{-1}xy &\equiv x^{-1}xy' \mod N \\
y &\equiv y' \mod N \\
y &= y' & \text{$U$ only acts nontrivially when $0\leq y\leq N-1$}
\end{aligned}$$

Therefore, $U$ is unitary since it preserves the inner product. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.13 {#exercise-513}





From equation (5.37) we know that

$$\begin{aligned}
\ket{u_s} \equiv \frac{1}{\sqrt{r}}\sum_{n=0}^{r-1}e^{-2\pi isn/r}\ket{x^n\mod N}
\end{aligned}$$

and so

$$\begin{aligned}
\frac{1}{\sqrt{r}}\sum_{s=0}^{r-1}e^{2\pi isk/r}\ket{u_s} \\
= \frac{1}{\sqrt{r}}\sum_{s=0}^{r-1}e^{2\pi isk/r}\left(\frac{1}{\sqrt{r}}\sum_{n=0}^{r-1}e^{-2\pi isn/r}\ket{x^n \mod N}\right)\\
= \frac{1}{r}\sum_{s=0}^{r-1}\sum_{n=0}^{r-1}e^{2\pi is(k-n)/r}\ket{x^n\mod N} \\
= \frac{1}{r}\sum_{n=0}^{r-1}\left(\sum_{s=0}^{r-1}e^{2\pi is(k-n)/r}\right)\ket{x^n\mod N} \\
= \frac{1}{r}\sum_{n=0}^{r-1}\left(r \delta_{kn}\right)\ket{x^n\mod N} & \text{from the hint}\\
=\ket{x^k\mod N}
\end{aligned}$$

then for $k=0$

$$\begin{aligned}
\frac{1}{\sqrt{r}}\sum_{s=0}^{r-1}\ket{u_s} &=\ket{x^0\mod N}\\
&= \ket{1}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.14 {#exercise-514}





If we applied a different unitary transform $V$ and started the second register in state $\ket{0}$ then

$$\begin{aligned}
\ket{\psi} &= \sum_{j=0}^{2^t-1}V\ket{j}\ket{0} \\
&=  \sum_{j=0}^{2^t-1}\ket{j}\ket{0 + x^j \mod N} & \text{since $k=0$} \\
&= \sum_{j=0}^{2^t-1}\ket{j}\ket{x^j\mod N} \\
&= \sum_{j=0}^{2^t-1}\ket{j}U^j\ket{1} \\
\end{aligned}$$

The transformation that we want to compute is

$$\begin{aligned}
\ket{j}\ket{k} &\rightarrow \ket{j}\ket{k+x^j\mod N}
\end{aligned}$$

Thus $V$ is the equivalent to adding the modular exponential $x^j\mod N$ modulo $N$ to the contents of the second register. This can be done by reversibly computing the function $x^j\mod N$ of $j$ in a third register and then reversibly adding it modulo $N$ to the contents of the second register, using the trick of uncomputation to erase the contents of the third register upon completion. The algorithm for computing the modular exponential is the same as the one described in Box 5.2 and uses $O(L^3)$ gates. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.15 {#exercise-515}





If $z$ is the least common multiple of $x$ and $y$ that means it is the smallest integer where $z=mx=ny$ for some integers $m$ and $n$. Let $g=\text{gcd}(x,y)$ we know that $x=ga$ and $y=gb$ with $\text{gcd}(a,b)=1$ and so $ma=nb$. Since $a$ and $b$ are coprime, we know that $b \vert ma$ implies $b \vert m$ and that $a \vert nb$ implies $a \vert n$, therefore $m=bt$ and $n=at$ for some integer $t$. Thus 

$$\begin{aligned}
z &= mx = ny \\
&= btga = atgb & \text{always true}\\
&= bga & \text{let $t=1$ since $z$ is the least common multiple} \\
&= \frac{(ga)(gb)}{g} \\
&= \frac{xy}{g}
\end{aligned}$$

Therefore, the least common multiple of positive integers $x$ and $y$ is $xy/\text{gcd}(x,y)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.16 {#exercise-516}





First,

$$\begin{aligned}
\int_x^{x+1} \frac{1}{y^2} \ dy &= \left. -\frac{1}{y}\right\vert_x^{x+1} & \text{for $x\neq 0 \text{ or } -1$}\\
&= \frac{1}{x} - \frac{1}{x+1} \\
&=\frac{x+1}{x(x+1)} - \frac{x}{x(x+1)} \\
&= \frac{1}{x^2+x} \\
&\geq \frac{2}{3x^2} & \text{for all $x\geq 2$} \\
\end{aligned}$$

Therefore,

$$\begin{aligned}
\frac{3}{2} \int_x^{x+1} \frac{1}{y^2} \ dy  &\geq \frac{1}{x^2} 
\end{aligned}$$

Then for $\sum_q$ being the sum over all prime numbers $q$,

$$\begin{aligned}
\sum_q \frac{1}{q^2} &\leq \sum_{n=2}^{\infty} \frac{1}{n^2} \\
&\leq \frac{3}{2}\int_2^\infty \frac{1}{y^2} \ dy \\
&= \frac{3}{4}
\end{aligned}$$

and thus (5.58) holds. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.17 {#exercise-517}

This problem took me a while to work through, and I ended up relying heavily on [Wikipedia](https://en.wikipedia.org/wiki/Computational_complexity_of_mathematical_operations) to find the complexity of different mathematical operations. I also read several forums discussing different methods of calculating $\log(N)$ to the necessary precision, with this [StackExchange](https://math.stackexchange.com/questions/3381629/what-is-the-fastest-algorithm-for-finding-the-natural-logarithm-of-a-big-number) discussion being the most useful. I also read a little of [Modern Computer Arithmetic](https://maths-people.anu.edu.au/~brent/pd/mca-cup-0.5.9.pdf). 

I feel like this exercise wanted us to actually come up with algorithms for these different mathematical operations, which I did and found to be an enlightening exercise, but to increase the likeliness of sharing a correct solution, I'm going to refer to names of known algorithms with known complexity in the solution below. 




For (1), if $b$ exists,

$$\begin{aligned}
L &= \lfloor \log(N)\rfloor+1 \\
&= \lfloor \log(a^b) \rfloor +1 \\
&= \lfloor b\log(a) \rfloor +1 \\
&\geq b + 1 & \text{if $a\geq 2$} \\
&\geq b
\end{aligned}$$

For (2), To compute $y=\log(N)$, the number of operations depends on how many fractional bits will be needed. For this algorithm, we need enough bits to calculate $2^x$ with an error less than $0.5$ and so

$$\begin{aligned}
\frac{1}{2} &> \vert 2^{\tilde{x}} - 2^x \vert \\
&= \vert 2^x(2^{\tilde{x}-x} - 1) \vert \\
&\approx \vert 2^x(1 + \ln(2)(\tilde{x}-x) - 1)\vert & \text{for small $\tilde{x}-x$ from the Taylor series}\\
&= \vert \ln(2)2^x (\tilde{x}-x) \vert \\
\end{aligned}$$

thus,

$$\begin{aligned}
\frac{1}{2\ln(2)2^x} &> \vert \tilde{x}-x \vert \\
\end{aligned}$$

Therefore, we'll need $p$ fractional bits such that $2^{-p} < \frac{1}{2\ln(2)2^x}$ and so $p>\log(2\ln(2)2^x)\approx x \approx \frac{L}{b}$. Looking at the elementary functions section of Wikipedia, we see that using the arithmetic-geometric mean iteration algorithm we can compute $\log(N)$ in $O(M(p)\log(p))$ operations, where $M(p)$ is dependent on the multiplication algorithm used. If we use the Harvey-Hoeven algorithm $M(p)=O(p\log(p))$ and so $\log(N)$ can be computed in $O(p(\log(p))^2)$. Since $p\approx \frac{L}{b}$, this means it can be computed in $O(L(\log(L))^2)$.

To compute $x=y/b=\log(N)/b$ for $b\leq L$, we can use the Newton-Raphson algorithm which can be done in $O(p\log(p))$. So the number of operations will be $O((L)\log(L))$

To compute the two integers $u_1$ and $u_2$ nearest to $2^x$, we would first need to calculate $2^x$ and then round up or down. The precision needed to compute $2^x$ is $\approx L/b$ bits and so using the arithmetic-geometric mean iteration algorithm this calculation can be done in $O(L(\log(L))^2)$ operations and then $O(1)$ operations would be needed to round the number up and down. 

For (3), both $u_1$ and $u_2$ are $\approx L/b$ bit numbers. Exponentiation by repeated squaring is an efficient algorithm to compute large exponents by repeatedly squaring the base and would involve $O(\log (b))$ multiplications. Then each multiplication would be $O(L\log (L))$ operations, using the Harvey-Hoeven algorithm. The check for equality is $O(L)$. Therefore, the entire calculation would be $O(L(\log L)(\log b))$, which is in $O(L(\log(L))^2)$, since $b\leq L$.  


For (4), 

```
for b = 2 to L:
  x=log(N)/b        #O(L(\log(L))^2)
  d = 2^x           #O(L(\log(L))^2)
  u1 = floor(d)     #O(1)
  u2 = ceil(d)      #O(1)
  a1 = u1^b         #O(L(\log(L))^2)
  if a1 = N:        #O(L)
    return u1       
  a2 = u2^b         #O(L(\log(L))^2)
  if a2 = N:        #O(L)
    return u2
return nothing      
```

Looking at the algorithm, we can see that the calculations in the for loop are $O(L(\log(L))^2)$ and these calculations are done up to $L-1$ times and so the entire algorithm is done in $O(L^2(\log(L))^2)$ operations which is in $O(L^3)$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.18 {#exercise-518}

Note: I fixed the error reported on the [errata page](https://michaelnielsen.org/qcqi/errata/errata/errata.html).




Step 1. check if $91$ is even. $91/2 = 45.5$ therefore, $91$ is not even.

Step 2. Determine whether $91=a^b$. Using the algorithm from [exercise 5.17](#exercise-517), I generated the table below. Since none of the $a_1$ or $a_2$ equal $91$ there is no $a$ such that $91=a^b$.


| $b$ |	$x=\log(91)/b$ |	$d=2^x$	| $u_1=\lfloor d \rfloor$ |	$u_2= \lceil d \rceil$ |	$a_1 = u_1^b$ |	$a_2=u_2^b$ |
|:---:|:--------------:|:--------:|:-----------------------:|:----------------------:|:--------------:|:-----------:|
| 2   |	3.25           |	9.51    |	9	                      | 10                     |	81            |	100         |
| 3   |	2.17           |	4.5     |	4                       |	5                      |	64            |	125         |
| 4   |	1.63           |	3.1     |	3                       |	4                      |	81            |	256         |
| 5   |	1.30           |	2.46    |	2                       |	3                      |	32            |	243         |
| 6   |	1.08           |	2.11    |	2                       |	3                      |	64            |	729         |
| 7	  | 0.93           |	1.91    |	1                       |	2                      |	1             |	128         |

Step 3. $x=4$ was randomly chosen and it was determined that it is co-prime to $91$ since $\text{gcd}(4,91) = 1$.

Step 4. find the order $r$ of $x=4$ for $N=91$. Using a brute force calculation, shown below, we see that $r=6$ and 

$$\begin{aligned}
x^{r/2} \mod 91 = x^{3} \mod 91 = 64 \neq -1 \mod 91.
\end{aligned}$$

| $r$ | $x^r$ |	$x^r \mod N$ |
|:---:|:-----:|:------------:|
| 1	  | 4     |	4            |
| 2	  | 16    |	16           |
| 3   |	64    |	64           |
| 4   |	256   |	74           |
| 5   |	1024  |	23           |
| 6   |	4096  |	1            |

Step 5. compute $\text{gcd}(64-1, 91)$ and $\text{gcd}(64+1, 91)$ and test to see if one of these is a non-trivial factor. We'll use Euclid's algorithm from section A4.2.

$$\begin{aligned}
91 &= 1 \times 63 + 28 \\
63 &= 2 \times 28 + 7 \\
28 &= 4 \times 7 \\
\end{aligned}$$

Therefore $\text{gcd}(63, 91) = 7$.

$$\begin{aligned}
91 &= 1 \times 65 + 26 \\
65 &= 2 \times 26 + 13 \\
26 &= 2 \times 13 \\
\end{aligned}$$

Therefore $\text{gcd}(65, 91) = 13$.

From this, we know that both 7 and 13 are factors of 91.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.19 {#exercise-519}






Let's look at the requirements:
* Is a composite number. So, needs at least two non-trivial factors $a \geq 2$ and $b \geq 2$.
* Is not even. Therefore, neither $a$ nor $b$ can be even.
* Is not a power of some smaller integer. Therefore, $a \neq b$.
  
The smallest number for which the order-finding subroutine is required will be the number with the smallest possible factors $a$ and $b$. The smallest possible $a$ is $3$, since $a$ can't be even. Since $b \neq a$, the smallest possible $b$ is then 5. Therefore, the smallest number for which the order-finding subroutine is required is $3 \times 5 = 15$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |






## General applications of the quantum Fourier transform


### Exercise 5.20 {#exercise-520}





Let $N=qr$ where $q$ is some integer. Then every $x$ can be written as $x=a+kr$ where $a\in \lbrace 0, \cdots, r-1 \rbrace$ and $k\in \lbrace 0, \cdots, q-1 \rbrace$ and so

$$\begin{aligned}
\hat{f}(l) &\equiv \frac{1}{\sqrt{N}}\sum_{x=0}^{N-1} e^{-2\pi ilx/N}f(x) \\
&= \frac{1}{\sqrt{N}}\sum_{a=0}^{r-1} \sum_{k=0}^{q-1} e^{-2\pi il(a+kr)/N}f(a + kr) \\ 
&= \frac{1}{\sqrt{N}}\sum_{a=0}^{r-1} \sum_{k=0}^{q-1} e^{-2\pi il(a+kr)/N}f(a) & \text{since we know $f(x+r)=f(x)$} \\ 
&= \frac{1}{\sqrt{N}}\sum_{a=0}^{r-1}  e^{-2\pi ila/N}f(a) \sum_{k=0}^{q-1} e^{-2\pi ilkr/N} \\
&= \frac{1}{\sqrt{N}}\sum_{a=0}^{r-1}  e^{-2\pi ila/N}f(a) \sum_{j\in \lbrace 0,r,2r,\cdots,N-r \rbrace} e^{-2\pi ijl/N} & \text{where $j=kr$} \\
&= \begin{cases}
  \frac{\sqrt{N}}{r}\sum_{a=0}^{r-1}  e^{-2\pi ila/N}f(a) &  \text{if $l$ is an integer multiple of $N/r$} \\
  0 & \text{otherwise}  \\
\end{cases}
\end{aligned}$$

For $l$ that are integer multiples of $N/r$ we can write $l=mN/r=mq$, and so $e^{-2\pi ila/N}=e^{-2\pi i(mq)a/(qr)}=e^{-2\pi ima/r}$. Thus,

$$\begin{aligned}
\hat{f}(l) &= \begin{cases}
  \frac{\sqrt{N}}{r}\sum_{a=0}^{r-1}  e^{-2\pi ima/r}f(a) &  \text{if $l$ is an integer multiple of $N/r$} \\
  0 & \text{otherwise}  \\
\end{cases}
\end{aligned}$$

The case where $l$ is an integer multiplier of $N/r$ has a similar form to (5.63). 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.21 {#exercise-521}





For (1) we can write $U_y$ as

$$\begin{aligned}
U_y &= \sum_{k=0}^{r-1}\ket{f(k+y)}\bra{f(k)} \\
\end{aligned}$$

and so

$$\begin{aligned}
U_y\ket{\hat{f}(l)} &= \left(\sum_{k=0}^{r-1}\ket{f(k+y)}\bra{f(k)} \right)\left(\frac{1}{\sqrt{r}}\sum_{x=0}^{r-1}e^{-2\pi ilx/r}\ket{f(x)} \right) \\
&= \sum_{k=0}^{r-1}\sum_{x=0}^{r-1}\frac{1}{\sqrt{r}}e^{-2\pi ilx/r}\ket{f(k+y)}\braket{f(k) \vert f(x)}  \\
&= \frac{1}{\sqrt{r}}\sum_{x=0}^{r-1}e^{-2\pi ilx/r}\ket{f(x+y)}  \\
&= e^{2\pi ily/r}\frac{1}{\sqrt{r}}\sum_{x=0}^{r-1}e^{-2\pi il(x+y)/r}\ket{f(x+y)}  \\
&= e^{2\pi ily/r}\ket{\hat{f}(l)} \\
\end{aligned}$$

Therefore, $\ket{\hat{f}(l)}$ is an eigenvector with eigenvalue $e^{2\pi ily/r}$.

For (2) let's assume that we start with the state $\ket{0}\ket{f(x_0)}$. Then we create a superposition, like what is done in step 2 of the period-finding algorithm,

$$\begin{aligned}
\rightarrow & \frac{1}{\sqrt{2^t}}\sum_{x=0}^{2^t-1}\ket{x}\ket{f(x_0)} \\
\end{aligned}$$

Then you can apply controlled powers of $U_y$

$$\begin{aligned}
\rightarrow & \frac{1}{\sqrt{2^t}}\sum_{x=0}^{2^t-1}\ket{x}U_y^x\ket{f(x_0)}\\
&= \frac{1}{\sqrt{2^t}}\sum_{x=0}^{2^t-1}\ket{x}\ket{f(x_0 + xy)}\\
&= \frac{1}{\sqrt{r2^t}}\sum_{l=0}^{r-1}\sum_{x=0}^{2^t-1}e^{2\pi il(x_0+xy)/r}\ket{x}\ket{\hat{f}(l)}\\
&= \frac{1}{\sqrt{r2^t}}\sum_{l=0}^{r-1}e^{2\pi ilx_0/r}\sum_{x=0}^{2^t-1}e^{2\pi ilxy/r}\ket{x}\ket{\hat{f}(l)}\\
\end{aligned}$$

Then we can apply the inverse Fourier transform

$$\begin{aligned}
\rightarrow & \frac{1}{\sqrt{r}}\sum_{l=0}^{r-1}e^{2\pi ilx_0/r}\ket{\widetilde{ly/r}}\ket{\hat{f}(l)}\\
\end{aligned}$$

Then we measure the first register and get

$$\begin{aligned}
\rightarrow & \widetilde{ly/r}
\end{aligned}$$

Divide measurement by $y$ and then apply the continued fractions algorithm to get $r$. Therefore $U_y$ is as useful as $U$ in solving the period-finding problem. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.22 {#exercise-522}






We know that

$$\begin{aligned}
f(x_1,x_2) &= b^{x_1}a^{x_2} \\
&= \left(a^s\right)^{x_1}a^{x_2} \\
&= a^{sx_1+x_2} \\
&= f(0, sx_1+x_2)
\end{aligned}$$

Therefore, 

$$\begin{aligned}
\ket{\hat{f}(l_1,l_2)} &= \sum_{x_1=0}^{r-1}\sum_{x_2=0}^{r-1} e^{-2\pi i(l_1x_1+l_2x_2)/r}\ket{f(x_1,x_2)}\\
&= \sum_{x_1=0}^{r-1}\sum_{x_2=0}^{r-1} e^{-2\pi i(l_1x_1+l_2x_2)/r}\ket{f(0, sx_1+x_2)}\\
&= \sum_{x_1=0}^{r-1}\sum_{j=0}^{r-1}e^{-2\pi i(l_1x_1+l_2(j-sx_1))/r}\ket{f(0,j)} & \text{let $j=sx_1+x_2$} \\
&= \sum_{x_1=0}^{r-1}\sum_{j=0}^{r-1}e^{-2\pi i((l_1-sl_2)x_1+l_2j)/r}\ket{f(0,j)} \\
&= \sum_{j=0}^{r-1}e^{-2\pi il_2j/r}\sum_{x_1=0}^{r-1}e^{-2\pi i(l_1-sl_2)x_1/r}\ket{f(0,j)} \\
&= r\sum_{j=0}^{r-1}e^{-2\pi il_2j/r}\ket{f(0,j)} & \text{when $l_1-sl_2 = 0 \mod r$, otherwise $0$}\\
\end{aligned}$$

From above we see the constraint is 

$$\begin{aligned}
l_1-sl_2 &= 0 \mod r \\
l_1 &= sl_2 \mod r \\
l_1/s &= l_2 \mod r \\
l_1/s - l_2 &= 0 \mod r
\end{aligned}$$

Therefore $l_1/s-l_2$ must be an integer multiple of $r$ for this expression to be non-zero.

If we compare our solution to equation 5.72, we see that the prefactor is different. In our equation it is $r$ in 5.72 it is $\frac{1}{\sqrt{r}}$. I assume that this is due to the book normalizing the vector. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.23 {#exercise-523}






Using (5.70) we get

$$\begin{aligned}
\frac{1}{r} \sum_{l_1=0}^{r-1}\sum_{l_2=0}^{r-1} e^{-2\pi i(l_1x_1+l_2x_2)/r}\ket{\hat{f}(l_1,l_2)} \\
= \frac{1}{r} \sum_{l_1=0}^{r-1}\sum_{l_2=0}^{r-1} e^{-2\pi i(l_1x_1+l_2x_2)/r}\left(\frac{1}{\sqrt{r}}\sum_{j=0}^{r-1}e^{-2\pi il_2j/r}\ket{f(0,j)} \right)\\ 
= \frac{1}{r\sqrt{r}} \sum_{l_1=0}^{r-1}\sum_{l_2=0}^{r-1}\sum_{j=0}^{r-1}e^{-2\pi i(l_1x_1+l_2x_2+l_2j)/r}\ket{f(0,j)}\\ 
= \frac{1}{r\sqrt{r}} \sum_{l_2=0}^{r-1}\sum_{j=0}^{r-1}e^{-2\pi il_2(sx_1+x_2+j)/r}\ket{f(0,j)} & \text{since the terms are non-zero when $l_1=sl_2$}\\ 
= \frac{1}{\sqrt{r}} \sum_{j=0}^{r-1}\delta_{sx_1+x_2+j\equiv 0\mod r}\ket{f(0,j)} \\ 
= \frac{1}{\sqrt{r}}\ket{f(0,-(sx_1+x_2))} \\ 
= \frac{1}{\sqrt{r}}f(-x_1,-x_2)
\end{aligned}$$

This is a little different than $f(x_1,x_2)$, I wonder if we were supposed to use the non-normalized form of equation 5.70, that would give us a result without the $\frac{1}{\sqrt{r}}$. I also wonder if equation 5.73 was supposed to have a positive exponent.  

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.24 {#exercise-524}






Apply the continued fractions algorithm to both $sl_2/r$ and $l_2/r$ to generate their successive convergents, using equation (5.49) to compute each rational approximation $p_n/q_n$. For each pair of convergents, form approximations $x_1 \approx sl_2/r$ and $x_2\approx l_2/r$. Then compute

$$\begin{aligned}
s_{cand} = \text{round}\left(\frac{x_1}{x_2}  \right)
\end{aligned}$$

as a candidate value for $s$. Test this using the known $a$ and $b$ by checking whether $a^{s_{cand}}=b$. If so, stop. Otherwise, proceed to the next convergents, compute the new approximations using equation (5.49), recompute $s_{cand}$, and test again. Repeat until the correct value of $s$ is found.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.25 {#exercise-525}






We want a circuit implementing

$$\begin{aligned}
U\ket{x_1}\ket{x_2}\ket{y} = \ket{x_1}\ket{x_2}\ket{y\oplus b^{x_1} a^{x_2}}
\end{aligned}$$

This can be done by initializing a set of ancilla register to 1 and using modular exponentiation outlined in Box 5.2 to calculate

$$\begin{aligned}
\ket{x_1}\ket{x_2}\ket{y}\ket{1} \rightarrow \ket{x_1}\ket{x_2}\ket{y}\ket{b^{x_1} a^{x_2}}
\end{aligned}$$

This calculation uses $O(L^3)$ gates, where $L=\lceil \log(N)\rceil$.

Then $O(L)$ CNOT gates are used to calculate

$$\begin{aligned}
\ket{x_1}\ket{x_2}\ket{y}\ket{b^{x_1} a^{x_2}} \rightarrow \ket{x_1}\ket{x_2}\ket{y\oplus b^{x_1} a^{x_2}}\ket{b^{x_1} a^{x_2}}
\end{aligned}$$

Then another $O(L^3)$ gates are used to uncompute the ancilla register

$$\begin{aligned}
\ket{x_1}\ket{x_2}\ket{y\oplus b^{x_1} a^{x_2}}\ket{b^{x_1} a^{x_2}} \rightarrow \ket{x_1}\ket{x_2}\ket{y\oplus b^{x_1} a^{x_2}}\ket{1}
\end{aligned}$$

This gives a total complexity of $O(L^3)$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.26 {#exercise-526}






From equation 5.77 we know that equation 5.76 has near zero amplitudes for all values of $l$ except those which satisfy

$$\begin{aligned}
\vert K \vert &= \sum_{h\in K} e^{-2\pi ilh/\vert G\vert} \\
&= \sum_{h\in K} \prod_{i=1}^{M} e^{-2\pi il_i' h_i/p_i} & \text{equation 5.78}\\
&= \sum_{(h_p)_{p}\in \prod_{p}K_p} \prod_{i=1}^{M} e^{-2\pi il_i' h_i/p_i} \\
&=  \prod_{i=1}^{M} \left( \sum_{h_{p_i}\in K_{p_i}} e^{-2\pi il_i' h_{p_i}/p_i} \right)\\
\end{aligned}$$

From equation 5.69 we know that

$$\begin{aligned}
\sum_{h_{p_i}\in K_{p_i}} e^{-2\pi il_i' h_{p_i}/p_i} &=  \begin{cases}
  \vert K_{p_i} \vert &  \text{if $l_i'$ is an integer multiple of $\vert K_{p_i} \vert$} \\
  0 & \text{otherwise}  \\
  \end{cases}
\end{aligned}$$

Therefore, we know that all $l_i'$ need to be an integer multiple of $\vert K_{p_i} \vert$ in order for equation 5.76 to have a non-near zero amplitude. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.27 {#exercise-527}






Algorithm for decomposition: 
1. Randomly select $O(\log\vert G \vert)$ elements in $G$
2. Use the quantum order-finding algorithm to find their order
3. Use the hidden subgroup problem algorithm to identify the independent cyclic components
4. Use the quantum factoring algorithm on each cyclic component to split it into prime orders

The final result then looks like

$$\begin{aligned}
G = \mathbb{Z}_{p_1} \times \mathbb{Z}_{p_2} \times \cdots \times \mathbb{Z}_{p_M}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.28 {#exercise-528}

I had to reference several resources to understand the hidden subgroup problem. This paper from the History and further reading section for this chapter was helpful: [The Hidden Subgroup Problem and Eigenvalue Estimation on a Quantum Computer](https://arxiv.org/pdf/quant-ph/9903071). I also read [Wikipedia](https://en.wikipedia.org/wiki/Hidden_subgroup_problem). [THE HIDDEN SUBGROUP PROBLEM - REVIEW AND OPEN PROBLEMS](https://arxiv.org/pdf/quant-ph/0411037) was also a good resource. Unfortunately, none of these resources use the same notation as the book.




Algorithm: Hidden subgroup problem

Inputs: (1) a black box which performs the operation $U\ket{g}\ket{h} = \ket{g}\ket{h\oplus f(g)}$ for $g\in G$, $h\in X$, and $\oplus$ an appropriately chosen binary operation on $X$, (2) a state to store the function evaluation, initialized to $\ket{0}$, and (3) $M$ times $t=O(\lceil \log \vert G\vert\rceil + \log(1/\epsilon))$ qubit registers initialized to $\ket{0}$.

Outputs: A generating set for the hidden subgroup $K \leq G$.

Runtime: $n$ uses of $U$, and $O(n\lceil\log\vert G \vert\rceil^2)$ operations. Succeeds with probability of at least $1-2^{-\Omega(n)}$, where $n$ is the number of repetitions of steps 1-6 in the procedure. 

Procedure:

$$\begin{aligned}
1 & \ket{0}^{\otimes M}\ket{0} & \text{initial state}\\
2 & \rightarrow \frac{1}{\sqrt{\vert G \vert}}\sum_{g_1,\cdots,g_M}\ket{g_1}\cdots\ket{g_M}\ket{0} & \text{create superposition}\\
3 & \rightarrow \frac{1}{\sqrt{\vert G \vert}}\sum_{g_1,\cdots,g_M}\ket{g_1}\cdots\ket{g_M}\ket{f(g_1,\cdots,g_M)} & \text{apply $U$}\\
   & \approx \frac{1}{\sqrt{\vert G \vert}}\sum_{g_1,\cdots,g_M}\sum_{l_1'\cdots l_M'}\prod_{i=1}^{M}e^{2\pi i l_i' g_i/p_i}\ket{g_1}\cdots\ket{g_M}\ket{\hat{f}(l_1',\cdots,l_M')}\\
4 & \rightarrow \sum_{l_1'\cdots l_M'}\ket{\widetilde{l_1'}}\cdots\ket{\widetilde{l_M'}}\ket{\hat{f}(l_1',\cdots,l_M')} & \text{apply inverse FT to first $M$ registers} \\
5 & \rightarrow \left(\widetilde{l_1'},\cdots, \widetilde{l_M'}\right) & \text{measure first $M$ registers}\\
6 & \rightarrow \sum_{i=1}^M \frac{l_i'h_i}{p_i} \in \mathbb{Z} \text{ for all } h\in K & \text{calculate constraints from $\left(\widetilde{l_1'},\cdots, \widetilde{l_M'}\right)$}\\
7 & \text{ repeate steps 1-6} & \text{until hidden subgroup $K$ can be determined}\\
8 & \rightarrow K & \text{compute $K$}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 5.29 {#exercise-529}





Algorithm: Deutsch problem

Inputs: (1) a black box which performs the operation $U\ket{g}\ket{h} = \ket{g}\ket{h \oplus f(g)}$ for $g\in \lbrace 0,1\rbrace$ and $h\in \lbrace 0,1\rbrace$, (2) a state to store the function evaluation, initialized to $\ket{0}$, and (3) a one qubit registers initialized to $\ket{0}$.

Outputs: Decide whether the hidden subgroup is $K=\lbrace 0\rbrace$ or $K=\lbrace 0,1 \rbrace$. 

Runtime: $n$ uses of $U$, and $O(n)$ operations. Succeeds with probability of at least $1-2^{-\Omega(n)}$, where $n$ is the number of repetitions of steps 1-6 in the procedure.

Procedure:

$$\begin{aligned}
1 & \ket{0}\ket{0} & \text{initial state}\\
2 & \rightarrow \frac{1}{\sqrt{2}}\sum_{g \in \lbrace 0,1 \rbrace}\ket{g}\ket{0} & \text{create superposition}\\
3 & \rightarrow \frac{1}{\sqrt{2}}\sum_{g \in \lbrace 0,1 \rbrace}\ket{g}\ket{f(g)}& \text{apply $U$}\\
   & \approx \frac{1}{\sqrt{2}}\sum_{g \in \lbrace 0,1 \rbrace}\sum_{l'\in \lbrace 0,1 \rbrace}e^{2\pi i l' g/2}\ket{g}\ket{\hat{f}(l')}\\
4 & \rightarrow \sum_{l'\in \lbrace 0,1 \rbrace}\ket{\widetilde{l'}}\ket{\hat{f}(l')} & \text{apply inverse FT to first register} \\
5 & \rightarrow \widetilde{l'} & \text{measure first register}\\
6 & \rightarrow  \frac{l'h}{2} \in \mathbb{Z} \text{ for all } h\in K & \text{calculate constraints from $\widetilde{l'}$}\\
7  & \text{ repeate steps 1-6} & \text{until hidden subgroup $K$ can be determined}\\
8 & \rightarrow K & \text{compute $K$ to decide the Deutsch problem}
\end{aligned}$$

Looking at the procedure, we see that if in step 6 we measure $1$ this tells us that $K=\lbrace 0 \rbrace$. However, if we measure $0$ both $K=\lbrace 0\rbrace$ or $K=\lbrace 0,1 \rbrace$ could still be true. Therefore, we would need to repeate the measurement to increase the probability of correctly deciding $K$. This provides no significant advantage over the classical algorithm. We saw in earlier chapters that there is a quantum algorithm that can decide this problem in one measurement. Therefore, even though the HSP framework can be used to solve the Deutsch problem, it is not the most efficient algorithm to use. 

Algorithm: Simon problem

Inputs: (1) a black box which performs the operation $U\ket{g}\ket{h} = \ket{g}\ket{h\oplus f(g)}$ for $g\in \lbrace 0,1 \rbrace^M$ and $h\in \text{any finite set}$, (2) a state to store the function evaluation, initialized to $\ket{0}$, and (3) $M$ one qubit registers initialized to $\ket{0}^{\otimes M}$.

Outputs: A generating set for the hidden subgroup $K \leq G$.

Runtime: $n$ uses of $U$, and $O(nM^2)$ operations. Succeeds with probability of at least $1-2^{-\Omega(n)}$, where $n$ is the number of repetitions of steps 1-6 in the procedure. 

Procedure:

$$\begin{aligned}
1 & \ket{0}^{\otimes M}\ket{0} & \text{initial state}\\
2 & \rightarrow \frac{1}{\sqrt{2^M}}\sum_{g_1,\cdots,g_M \in \lbrace 0,1\rbrace}\ket{g_1}\cdots\ket{g_M}\ket{0} & \text{create superposition}\\
3 & \rightarrow \frac{1}{\sqrt{2^M}}\sum_{g_1,\cdots,g_M\in \lbrace 0,1\rbrace}\ket{g_1}\cdots\ket{g_M}\ket{f(g_1,\cdots,g_M)} & \text{apply $U$}\\
   & \approx \frac{1}{\sqrt{2^M}}\sum_{g_1,\cdots,g_M\in \lbrace 0,1\rbrace}\sum_{l_1'\cdots l_M'\in \lbrace 0,1\rbrace}\prod_{i=1}^{M}e^{2\pi i l_i' g_i/2}\ket{g_1}\cdots\ket{g_M}\ket{\hat{f}(l_1',\cdots,l_M')}\\
4 & \rightarrow \sum_{l_1'\cdots l_M'\in \lbrace 0,1\rbrace}\ket{\widetilde{l_1'}}\cdots\ket{\widetilde{l_M'}}\ket{\hat{f}(l_1',\cdots,l_M')} & \text{apply inverse FT to first $M$ registers} \\
5 & \rightarrow \left(\widetilde{l_1'},\cdots, \widetilde{l_M'}\right) & \text{measure first $M$ registers}\\
6 & \rightarrow \sum_{i=1}^M \frac{l_i'h_i}{2} \in \mathbb{Z} \text{ for all } h\in K & \text{calculate constraints from $\left(\widetilde{l_1'},\cdots, \widetilde{l_M'}\right)$}\\
7 & \text{ repeate steps 1-6} & \text{until hidden subgroup $K$ can be determined}\\
8 & \rightarrow K & \text{compute $K$}
\end{aligned}$$

The constraint calculated from step 6 can be written as 

$$\begin{aligned}
& \sum_{i=1}^M \frac{l_i's_i}{2} \in \mathbb{Z}  \\
& \Rightarrow \sum_{i=1}^M l_i's_i \equiv 0 \mod 2  \\
& \Rightarrow l'\cdot s = 0 \mod 2
\end{aligned}$$

It will take $n=\Theta(M)$ measurements to accurately calculate $s$, and therefore solve this problem, whereas the classical algorithm would need at least $\Omega(2^{M/2})$ measurements. Therefore, this algorithm, using the HSP framework, does show an advantage over the classical algorithm.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## Chapter problems

### Problem 5.1 {#problem-51}






This is the same as equation 5.2, where $N=p$. Reading further in section 5.1, we see that they set $N=2^n$ and constructed a circuit that performs the quantum Fourier transform, shown in Figure 5.1. Unfortunately for us, $N$ is now prime and so $N\neq 2^n$. We will still have $n=\lceil p \rceil$ qubits and registers containing states $\ket{0},\cdots,\ket{2^n-1}$, but we only want to apply the Fourier transform on the first $p$ of these basis states and so we need to construct a circuit that performs the operation

$$\begin{aligned}
U &= \begin{bmatrix} F_p & 0 \\\ 0 & I_{2^n-p} \end{bmatrix}
\end{aligned}$$

Since $U$ is unitary, we know that it can be approximated using Hadamard, phase, CNOT, and $\pi/8$ gates (as shown in section 4.5.3). However, since $F_p$ cannot be represented as the simple product decomposition of equation 5.10, the circuit shown in figure 5.1 does not apply. For prime $p$, the resulting circuit has no particularly simple structure, but it exists and can be systematically constructed by decomposing $U$ into elementary 1- and 2-qubit gates.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Problem 5.2 {#problem-52}

This paper was cited in the History and further reading section for this problem: [Semiclassical Fourier Transform for Quantum Computation](https://arxiv.org/pdf/quant-ph/9511007).




I'm going to use a 4 qubit example to show that the combination of quantum Fourier transform and measurement is equivalent to a circuit consisting entirely of one qubit gates and measurement, with classical control, and no two qubit gates, but the same reasoning can be applied to a circuit of any number of qubits. 

Using the design shown in Figure 5.1, we can write a Fourier transform for a 4 qubit circuit as the following,

<img width="851" height="296" alt="image" src="https://github.com/user-attachments/assets/88c18ce0-8ebf-45ed-bec0-f102ded18ad0" />

Since the controlled $R_k$ operation is a controlled-phase gate, we can swap the control and target qubits without changing the output of the circuit (as we showed in [Exercise 4.18](https://adj59-dev.github.io/qcqi/chapter-4/#exercise-418)) and so our circuit can be constructed like so

<img width="814" height="288" alt="image" src="https://github.com/user-attachments/assets/a98c3f37-e8f6-499d-9b27-d76c907cb495" />

In [Exercise 4.35](https://adj59-dev.github.io/qcqi/chapter-4/#exercise-435) we showed that measurement commutes with controls and so if we measured each qubit after the Hadamard gate, but prior to them serving as controls for the $R_k$ gates, then that would be equivalent to measuring the qubits after the Fourier transform has completed. Measuring earlier vs. measuring at the end gives the same outcome distribution. After commuting the measurement forward, the remaining $R_k$ operations are just single-qubit gates whose application pattern is chosen classically from the measured bits, so there is no 2-qubit gates in the circuit. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Problem 5.3 {#problem-53}






This circuit is similar to the one we investigated in [Exercise 4.34](https://adj59-dev.github.io/qcqi/chapter-4/#exercise-434), but since the eigenvalues can have imaginary components $\frac{I+U}{2}$ is not a projector and instead must be interpreted as a measurement operator $M$. We therefore know that the probability of measuring $0$ when replacing $U$ with $U^k$ can be calculated as

$$\begin{aligned}
p_k(0) &= \braket{u \vert M_{k}^\dagger M_{k} \vert u} \\
&= \frac{1}{4} \braket{u \vert (I + U^{k\dagger})(I+U^k) \vert u} \\
&= \frac{1}{4} \braket{u \vert (2I + U^k + U^{k\dagger}) \vert u} \\
&= \frac{1}{4} \left( \braket{u \vert 2I \vert u} +\braket{u \vert U^k \vert u}+\braket{u \vert  U^{k\dagger} \vert u}\right) \\
&= \frac{1}{4} \left( 2 + e^{i2\pi\varphi k} + e^{-i2\pi\varphi k}\right) \\
&= \frac{1}{4} \left( 2 + 2\cos(2\pi\varphi k)\right) \\
&= \cos^2(\pi\varphi k)
\end{aligned}$$

With a probability of $1-\cos^2(\pi\varphi k)=\sin^2(\pi\varphi k)$ of measuring $1$.

By tuning $k$ and collecting multiple measurements at different values we could find two values $k_m$ and $k_{m+1}$ for which the measured outcome is almost always $0$. Then we could calculate $\varphi \approx \frac{1}{k_{m+1} - k_m}$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Problem 5.4 {#problem-54}






Looking at the Algorithm on page 233-234, we see that when reducing factoring to order-finding there are two steps that the book labeled as having $O(L^3)$ operations: step 2 and step 4. 

In [Exercise 5.17](#exercise-517), we already showed that by using more efficient mathematical operation algorithms, step 2 can be completed in $O(L^2(\log(L))^2)$ operations. This comes from repeating a $O(L(\log(L))^2)$ operation algorithm $L$ times, once for each value of $b$ between 2 and $L$. However, we do not need to run the algorithm for all of those values. It is sufficient to just run them for prime values between 2 and $L$. This is because we can write $b=p_1^{k_1}p_2^{k_2}\cdots p_n^{k_n}$ and so for all $p\in \lbrace p_1,p_2,\cdots,p_n \rbrace$

$$\begin{aligned}
N &= a^{b} \\
&= a^{p(b/p)} \\
&= (a^{b/p})^p \\
&= c^p
\end{aligned}$$

and so if there is a solution for $N=a^b$ there is also a solution for $N=c^p$ and we can return factor $c$ in step 2. From the prime number theorem, we know that there is about $L/log(L)$ prime numbers less than $L$ and so by only sampling prime numbers between $2$ and $L$ only $O(L^2\log(L))$ operations are needed, which is better than $O(L^2\log L\log\log L)$.

For step 4, the book lists the quantum order finding algorithm as having $O(L^3)$ operations. From our HSP algorithm analysis, we know this comes from one use of $U$, and $O(L^2)$ other operations, so in order to look for improvements, we need to focus on $U$. Looking in Box 5.2 where the modular exponentiation calculation is outlined, it is noted that this calculation is computed using $O(L^3)$ gates, but more efficient algorithms are possible based on more efficient algorithms for multiplication. It looks like this calculation was done using shcoolbook long multiplication which is $O(L^2)$. However, if we use the Sch&ouml;nhage-Strassen algorithm it can be done in $O(L\log L\log\log L)$ (and can be done even more efficiently with Harvey-Hoeven). If we switched to this multiplication algorithm, the computation can be done in $O(L^2\log L\log\log L)$ and so the factoring algorithm would be in $O(L^2\log L\log\log L)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Problem 5.5 {#problem-55}


These articles are cited as being related to this problem in the History and further readings section:

* [On Quantum Algorithms for Noncommutative Hidden Subgroups](https://arxiv.org/pdf/quant-ph/9807029)
* [Fast Quantum Fourier Transforms for a Class of Non-abelian Groups](https://arxiv.org/pdf/quant-ph/9807064)
* [Quantum Lower Bounds by Polynomials](https://arxiv.org/pdf/quant-ph/9802049)
* [Hidden Subgroup States are Almost Orthogonal](https://arxiv.org/pdf/quant-ph/9901034) 
* [Polynomial-Time Solution to the Hidden Subgroup Problem for a Class of non-abelian Groups](https://arxiv.org/pdf/quant-ph/9812070)

I'm not going to reproduce the solution here, it is written out clearly in [Hidden Subgroup States are Almost Orthogonal](https://arxiv.org/pdf/quant-ph/9901034).

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


### Problem 5.6 {#problem-56}






Let's look at the first two steps

$$\begin{aligned}
& \ket{x} = \ket{x_1,\cdots,x_n} & \text{initial state}\\
& \rightarrow \frac{\left(\ket{0} + e^{2\pi i0.x_n}\ket{1}\right) \left(\ket{0} + e^{2\pi i0.x_{n-1}x_n}\ket{1}\right) \cdots \left(\ket{0} + e^{2\pi i0.x_1x_2\cdots x_n}\ket{1}\right)}{2^{n/2}} & \text{apply quantum Fourier transform}\\
& \rightarrow \frac{\left(\ket{0} + e^{2\pi i(0.x_n + \varphi_n)}\ket{1}\right) \left(\ket{0} + e^{2\pi i(0.x_{n-1}x_n + \varphi_{n-1})}\ket{1}\right) \cdots \left(\ket{0} + e^{2\pi i(0.x_1x_2\cdots x_n + \varphi_1)}\ket{1}\right)}{2^{n/2}}  & \text{apply single qubit phase shifts}\\
\end{aligned}$$

Just to get a feel for what's going on let's walk through a couple of examples. First let's think about the case where $x=11$ and $y=1$ and so $11 = (1)2^{3}+(0)2^{2} + (1)2^{1} + (1)2^{0}$, then $x+y = (1)2^{3}+(1)2^{2} + (0)2^{1} + (0)2^{0}$

$$\begin{aligned}
& \ket{1011} & \text{initial state}\\
& \rightarrow \frac{\left(\ket{0} + e^{2\pi i0.1_2}\ket{1}\right) \left(\ket{0} + e^{2\pi i0.11_2}\ket{1}\right) \left(\ket{0} + e^{2\pi i0.011_2}\ket{1}\right)\left(\ket{0} + e^{2\pi i0.1011_2}\ket{1}\right)}{2^{n/2}} & \text{apply quantum Fourier transform}\\
& \rightarrow \frac{\left(\ket{0} + e^{2\pi i(0.1_2 + \varphi_4)}\ket{1}\right) \left(\ket{0} + e^{2\pi i(0.11_2 + \varphi_3)}\ket{1}\right)  \left(\ket{0} + e^{2\pi i(0.011_2 + \varphi_2)}\ket{1}\right) \left(\ket{0} + e^{2\pi i(0.1011_2 + \varphi_1)}\ket{1}\right)}{4}  & \text{apply single qubit phase shifts}\\
& = \frac{\left(\ket{0} + e^{2\pi i0.0_2}\ket{1}\right) \left(\ket{0} + e^{2\pi i0.00_2}\ket{1}\right) \left(\ket{0} + e^{2\pi i0.100_2}\ket{1}\right)\left(\ket{0} + e^{2\pi i0.1100_2}\ket{1}\right)}{4} & \text{this is what we want}\\
& \rightarrow \ket{1100} & \text{inverse Fourier transform}
\end{aligned}$$

For this example, we need $\varphi_4 = 0.1_2 = y/2$, $\varphi_3 = 0.01_2=y/4$, $\varphi_2 = 0.001_2=y/8$, and $\varphi_1 = 0.0001_2=y/16$.


Now let's think about the case where $x=11$ and $y=2$ and so $11 = (1)2^{3}+(0)2^{2} + (1)2^{1} + (1)2^{0}$, then $x+y = (1)2^{3}+(1)2^{2} + (0)2^{1} + (1)2^{0}$

$$\begin{aligned}
& \ket{1011} & \text{initial state}\\
& \rightarrow \frac{\left(\ket{0} + e^{2\pi i0.1_2}\ket{1}\right) \left(\ket{0} + e^{2\pi i0.11_2}\ket{1}\right) \left(\ket{0} + e^{2\pi i0.011_2}\ket{1}\right)\left(\ket{0} + e^{2\pi i0.1011_2}\ket{1}\right)}{2^{n/2}} & \text{apply quantum Fourier transform}\\
& \rightarrow \frac{\left(\ket{0} + e^{2\pi i(0.1_2 + \varphi_4)}\ket{1}\right) \left(\ket{0} + e^{2\pi i(0.11_2 + \varphi_3)}\ket{1}\right)  \left(\ket{0} + e^{2\pi i(0.011_2 + \varphi_2)}\ket{1}\right) \left(\ket{0} + e^{2\pi i(0.1011_2 + \varphi_1)}\ket{1}\right)}{4}  & \text{apply single qubit phase shifts}\\
& = \frac{\left(\ket{0} + e^{2\pi i0.1_2}\ket{1}\right) \left(\ket{0} + e^{2\pi i0.01_2}\ket{1}\right) \left(\ket{0} + e^{2\pi i0.101_2}\ket{1}\right)\left(\ket{0} + e^{2\pi i0.1101_2}\ket{1}\right)}{4} & \text{this is what we want}\\
& \rightarrow \ket{1101} & \text{apply inverse Fourier transform}
\end{aligned}$$

For this example, we need $\varphi_4 = 1.0_2=y/2 \equiv 0.0_2 \mod 1$, $\varphi_3 = 0.10_2=y/4$, $\varphi_2 = 0.010_2=y/8$, and $\varphi_1 = 0.0010_2=y/16$. This follows the same trend as the first example. 


Going back to our procedure we can now add the last step.

$$\begin{aligned}
& \ket{x} = \ket{x_1,\cdots,x_n} & \text{initial state}\\
&\rightarrow \frac{\left(\ket{0} + e^{2\pi i0.x_n}\ket{1}\right) \left(\ket{0} + e^{2\pi i0.x_{n-1}x_n}\ket{1}\right) \cdots \left(\ket{0} + e^{2\pi i0.x_1x_2\cdots x_n}\ket{1}\right)}{2^{n/2}} &\text{apply quantum Fourier transform}\\
&\rightarrow \frac{\left(\ket{0} + e^{2\pi i(0.x_n + y/2)}\ket{1}\right) \left(\ket{0} + e^{2\pi i(0.x_{n-1}x_n + y/2^2)}\ket{1}\right) \cdots \left(\ket{0} + e^{2\pi i(0.x_1x_2\cdots x_n + y/2^n)}\ket{1}\right)}{2^{n/2}}  & \text{apply single qubit phase shifts}\\
&=\frac{1}{2^{n/2}} \otimes_{l=1}^{n}\lbrack \ket{0} + e^{2\pi i(x+y \mod 2^l)2^{-l}}\ket{1} \rbrack\\
&=\frac{1}{2^{n/2}}\sum_{k=0}^{2^n-1}e^{2\pi i (x+y \mod 2^n)k/2^{n}} & \text{following equations 5.5-5.9 in reverse} \\
&\rightarrow \ket{x+y \mod 2^n} & \text{apply inverse Fourier transform}
\end{aligned}$$

Any integer values of $y$ could be easily added this way. The Fourier transform and inverse Fourier transform can be done with $\Theta(n^2)$ gates. Then we'll need $O(n)$ single qubit phase shift gates. So, the whole circuit requires $O(n^2)$ operations.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


