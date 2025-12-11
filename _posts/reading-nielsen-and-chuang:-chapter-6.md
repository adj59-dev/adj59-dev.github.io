---
title: "Reading Nielsen and Chuang: Chapter 6"
description: "Notes and exercise solutions for QCQI Chapter 6: quantum search algorithms, quantum counting, speeding up the solution of NP-complete problems."
categories:
  - Quantum Computation and Quantum Information
permalink: /qcqi/chapter-6/
toc: true
tags:
  - QCQI
  - quantum computing
  - Quantum Computation and Quantum Information
  - Nielsen & Chuang
  - chapter 6
  - exercise
  - problem
  - solutions
last_modified_at: 2025-11-29 19:10:00 -08:00
exercises:
  - anchor: exercise-61
    label: Exercise 6.1
  - anchor: exercise-62
    label: Exercise 6.2
  - anchor: exercise-63
    label: Exercise 6.3
  - anchor: exercise-64
    label: Exercise 6.4
  - anchor: exercise-65
    label: Exercise 6.5
  - anchor: exercise-66
    label: Exercise 6.6
  - anchor: exercise-67
    label: Exercise 6.7
  - anchor: exercise-68
    label: Exercise 6.8
  - anchor: exercise-69
    label: Exercise 6.9
  - anchor: exercise-610
    label: Exercise 6.10
  - anchor: exercise-611
    label: Exercise 6.11
  - anchor: exercise-612
    label: Exercise 6.12
  - anchor: exercise-613
    label: Exercise 6.13
  - anchor: exercise-614
    label: Exercise 6.14
  - anchor: exercise-615
    label: Exercise 6.15
  - anchor: exercise-616
    label: Exercise 6.16
  - anchor: exercise-617
    label: Exercise 6.17
  - anchor: exercise-618
    label: Exercise 6.18
  - anchor: exercise-619
    label: Exercise 6.19
  - anchor: exercise-620
    label: Exercise 6.20
  - anchor: problem-61
    label: Problem 6.1
  - anchor: problem-62
    label: Problem 6.2
  - anchor: problem-63
    label: Problem 6.3
  - anchor: problem-64
    label: Problem 6.4
chapter: 6
---

<a id="top"></a>


I just finished reading Chapter 6 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. 


<!-- toc -->


## The quantum search algorithm

### Exercise 6.1 {#exercise-61}

Show that the unitary operator corresponding to the phase shift in the Grover iteration is $2\ket{0}\bra{0} - I$.

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

Let's calculate $U\ket{x}$ and compare results to desired behavior, where $U=2\ket{0}\bra{0}-I$.

$$\begin{aligned}
U\ket{x} &= \left(2\ket{0}\bra{0} - I\right)\ket{x} \\
&= 2\ket{0}\braket{0\vert x} - \ket{x} \\
&= 2\delta_{x0}\ket{0} - \ket{x} \\
&= -(-1)^{\delta_{x0}}\ket{x}
\end{aligned}$$

This matches the desired behavior and so the unitary operator corresponding to the phase shift in the Grover iteration is $2\ket{0}\bra{0} - I$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.2 {#exercise-62}

Show that the operation $(2\ket{\psi}\bra{\psi}-I)$ applied to a general state $\sum_{k}\alpha_k\ket{k}$ produces

$$\begin{aligned}
\sum_{k}\lbrack -\alpha_k+2\braket{\alpha}\rbrack\ket{k},
\end{aligned}$$

where $\braket{\alpha}\equiv \sum_k\alpha_k/N$ is the mean value of the $\alpha_k$. For this reason, $(2\ket{\psi}\bra{\psi}-I)$ is sometimes referred to as the inversion about mean operation.

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

First let's rewrite $\ket{\psi}\bra{\psi}$ using equation 6.4

$$\begin{aligned}
\ket{\psi}\bra{\psi} &= \frac{1}{N}\sum_{x=0}^{N-1}\sum_{x'=0}^{N-1} \ket{x}\bra{x'}
\end{aligned}$$

Now let's use this in the exercise

$$\begin{aligned}
(2\ket{\psi}\bra{\psi}-I)\sum_{k}\alpha_k\ket{k} &= \sum_{k}2\alpha_k\ket{\psi}\braket{\psi\vert k}-\alpha_k\ket{k}\\
&= \sum_{k}\left(\sum_{x=0}^{N-1}\sum_{x'=0}^{N-1} \frac{2\alpha_k}{N}\ket{x}\braket{x'\vert k}\right)-\alpha_k\ket{k}\\
&= \sum_{k}\left(\sum_{x=0}^{N-1}\sum_{x'=0}^{N-1} \frac{2\alpha_k}{N}\ket{x} \delta_{kx'}\right)-\alpha_k\ket{k}\\
&= \sum_{k}\left(\sum_{x=0}^{N-1} \frac{2\alpha_k}{N}\ket{x}\right) -\alpha_k\ket{k}\\
&= \left(\sum_{x=0}^{N-1} \left(\sum_{k}\frac{2\alpha_k}{N}\right)\ket{x}\right) - \left(\sum_{k}\alpha_k\ket{k}\right)\\
&= \left(\sum_{x=0}^{N-1}2\braket{\alpha}\ket{x}\right) - \left(\sum_{k}\alpha_k\ket{k}\right)\\
&= \sum_{k}2\braket{\alpha}\ket{k} - \alpha_k\ket{k} & \text{relable $x$ as $k$}\\
&= \sum_{k}\lbrack 2\braket{\alpha} - \alpha_k\rbrack\ket{k} \\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.3 {#exercise-63}

Show that in the $\ket{\alpha}$, $\ket{\beta}$ basis, we may write the Grover iteration as

$$\begin{aligned}
G = \begin{bmatrix} \cos\theta & -\sin\theta \\\ \sin\theta & \cos\theta \end{bmatrix},
\end{aligned}$$

where $\theta$ is a real number in the range $0$ to $\pi/2$ (assuming for simplicity that $M\leq N/2$; this limitation will be lifted shortly, chosen so that 

$$\begin{aligned}
\sin\theta = \frac{2\sqrt{M(N-M)}}{N}
\end{aligned}$$

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

We start with $\ket{\psi} = \cos\frac{\theta}{2}\ket{\alpha} + \sin\frac{\theta}{2}\ket{\beta}$ then

$$\begin{aligned}
G\ket{\psi} &= \begin{bmatrix} \cos\theta & -\sin\theta \\\ \sin\theta & \cos\theta \end{bmatrix}\begin{bmatrix} \cos\frac{\theta}{2} \\\ \sin\frac{\theta}{2} \end{bmatrix}\\
&= \begin{bmatrix} \cos\theta\cos\frac{\theta}{2} - \sin\theta\sin\frac{\theta}{2} \\\ \sin\theta\cos\frac{\theta}{2} + \cos\theta\sin\frac{\theta}{2} \end{bmatrix}\\
&= \begin{bmatrix} \cos\frac{3\theta}{2} \\\ \sin\frac{3\theta}{2} \end{bmatrix}\\
&= \cos\frac{3\theta}{2}\ket{\alpha} + \sin\frac{3\theta}{2}\ket{\beta}
\end{aligned}$$

This agrees with equation 6.11. Therefore, the Grover iteration may be written as matrix $G$ in the $\ket{\alpha}$, $\ket{\beta}$ basis. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.4 {#exercise-64}

Give explicit steps for the quantum search algorithm, as above, but for the case of multiple solutions $(1<M<N/2)$.

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

Let $N=2^n$ and the subset $S$ represent a set of all solutions to the search problem, where $\vert S\vert = M$.

Algorithm: Quantum search

Inputs: (1) a black box oracle $O$ which performs the transformation $O\ket{x}\ket{q} = \ket{x}\ket{q\oplus f(x)}$ where $f(x)=0$ for all $0\leq x<2^n$ except $x\in S$, for which $f(x)=1$; (2) $n+1$ qubits in the state $\ket{0}$  

Outputs: an element of $S$

Runtime: $O(\sqrt{2^n/M})$ operations. Succeeds with probability $O(1)$. 

Procedure:

$$\begin{aligned}
1 & \ket{0}^{\otimes n}\ket{0} & \text{initial state}\\
2 & \rightarrow \frac{1}{\sqrt{2^n}}\sum_{x=0}^{2^n-1}\ket{x}\left\lbrack\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right\rbrack & \text{apply $H^{\otimes n}$ to the first $n$ qubits, and $HX$ to the last qubit}\\
3 & \rightarrow  \left\lbrack(2\ket{\psi}\bra{\psi}-I)O\right\rbrack^R\frac{1}{\sqrt{2^n}}\sum_{x=0}^{2^n-1}\ket{x}\left\lbrack\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right\rbrack & \text{apply the Grover iteration $R\approx \frac{\pi}{4}\sqrt{\frac{2^n}{M}}$ times}\\
   & \approx \ket{\beta}\left\lbrack\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right\rbrack & \text{where $\ket{\beta}$ is given by equation 6.9}\\
4 & \rightarrow x\in S & \text{measure the first $n$ qubits} \\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.5 {#exercise-65}

Show that the augmented oracle $O'$ may be constructed using one application of $O$, and elementary quantum gates, using the extra qubit $\ket{q}$.

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

We can build a circuit like the one below to make $O'$ by using one application of $O$ and two controlled-Z gates.

<img width="634" height="428" alt="image" src="https://github.com/user-attachments/assets/d804265b-e1bb-4b8e-af21-d941790f8874" />

We'll have one oracle bit $y$ initialized to $(\ket{0}-\ket{1})/\sqrt{2}$ and so before applying $O'$ we'll have

$$\begin{aligned}
\ket{x}\ket{q}\left(\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right)
\end{aligned}$$

If $q=0$ then the controlled-Z gates won't do anything and only $O$ will be applied. If $q=1$ then after the first controlled-Z gate the state will be

$$\begin{aligned}
\ket{x}\ket{q}\left(\frac{\ket{0}+\ket{1}}{\sqrt{2}}\right)
\end{aligned}$$

Then when $O$ is applied the state will not change, regardless of what $f(x)$ equals

$$\begin{aligned}
O\ket{x}\ket{q}\left(\frac{\ket{0}+\ket{1}}{\sqrt{2}}\right) &= \ket{x}\ket{q}\left(\frac{\ket{0 \oplus f(x)}+\ket{1 \oplus f(x)}}{\sqrt{2}}\right) \\
&= \begin{cases}
\ket{x}\ket{q}\left(\frac{\ket{1}+\ket{0}}{\sqrt{2}}\right) & \text{when $f(x)=1$} \\
\ket{x}\ket{q}\left(\frac{\ket{0}+\ket{1}}{\sqrt{2}}\right) & \text{when $f(x)=0$} \\
\end{cases}
\end{aligned}$$

Then the second controlled-Z gate will be applied restoring the state to

$$\begin{aligned}
\ket{x}\ket{q}\left(\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right)
\end{aligned}$$

Therefore, the circuit performs the desired calculation

$$\begin{aligned}
O'\ket{x}\ket{q}\left(\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right) = \begin{cases}
(-1)^{f(x)}\ket{x}\ket{q}\left(\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right), & \text{when $q=0$}\\
\ket{x}\ket{q}\left(\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right), & \text{when $q=1$}\\
\end{cases}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.6 {#exercise-66}

Verify that the gates in the dotted box in the second figure of Box 6.1 perform the conditional phase shift operation $2\ket{00}\bra{00}-I$, up to an unimportant global phase factor. 

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

These are the gates that we need to verify:

<img width="369" height="179" alt="image" src="https://github.com/user-attachments/assets/a362d05c-22ca-473b-945e-eeeb9d8f3229" />

If we start with a generic two qubit state $\ket{\psi_0} = \alpha_{00}\ket{00} + \alpha_{10}\ket{10} + \alpha_{01}\ket{01} + \alpha_{11}\ket{11}$ and apply an X gate to each of the qubits we get

$$\begin{aligned}
\ket{\psi_1} = \alpha_{00}\ket{11} + \alpha_{10}\ket{01} + \alpha_{01}\ket{10} + \alpha_{11}\ket{00}
\end{aligned}$$

Then applying the Hadamard gate to the second qubit we get

$$\begin{aligned}
\ket{\psi_2} = \alpha_{00}\left(\frac{\ket{10}-\ket{11}}{\sqrt{2}}\right) + \alpha_{10}\left(\frac{\ket{00}-\ket{01}}{\sqrt{2}}\right) + \alpha_{01}\left(\frac{\ket{10}+\ket{11}}{\sqrt{2}}\right) + \alpha_{11}\left(\frac{\ket{00}+\ket{01}}{\sqrt{2}}\right)
\end{aligned}$$

Then we apply the CNOT gate to get

$$\begin{aligned}
\ket{\psi_3} = \alpha_{00}\left(\frac{\ket{11}-\ket{10}}{\sqrt{2}}\right) + \alpha_{10}\left(\frac{\ket{00}-\ket{01}}{\sqrt{2}}\right) + \alpha_{01}\left(\frac{\ket{11}+\ket{10}}{\sqrt{2}}\right) + \alpha_{11}\left(\frac{\ket{00}+\ket{01}}{\sqrt{2}}\right)
\end{aligned}$$


Then the Hadamard gate on the second qubit

$$\begin{aligned}
\ket{\psi_4} = -\alpha_{00}\ket{11} + \alpha_{10}\ket{01} + \alpha_{01}\ket{10} + \alpha_{11}\ket{00}
\end{aligned}$$


Then the final two X gates

$$\begin{aligned}
\ket{\psi_5} &= -\alpha_{00}\ket{00} + \alpha_{10}\ket{10} + \alpha_{01}\ket{01} + \alpha_{11}\ket{11} \\
&=-\left(\alpha_{00}\ket{00} - \alpha_{10}\ket{10} - \alpha_{01}\ket{01} - \alpha_{11}\ket{11}\right) \\
&=e^{i\pi}\left(2\alpha_{00}\ket{00}-\left(\alpha_{00}\ket{00} + \alpha_{10}\ket{10} + \alpha_{01}\ket{01} + \alpha_{11}\ket{11}\right)\right) \\
&= e^{i\pi}\left(2\ket{00}\bra{00}-I\right)\ket{\psi_0} \\
\end{aligned}$$

Therefore, the dotted box in the second figure of Box 6.1 performs the conditional phase shift operation $2\ket{00}\bra{00}-I$, up to an unimportant global phase factor. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>



## Quantum search as a quantum simulation


### Exercise 6.7 {#exercise-67}

Verify that the circuits shown in Figures 6.4 and 6.5 implement the operations $\exp(-i\ket{x}\bra{x}\Delta t)$ and $\exp(-i\ket{\psi}\bra{\psi}\Delta t)$, respectively, with $\ket{\psi}$ as in (6.24).

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

Figure 6.4 performs the operation

$$\begin{aligned}
O\left(I_n\otimes P(\Delta t)\right)O\ket{y}\ket{0} &= O\left(I_n\otimes P(\Delta t)\right)\ket{y}\ket{f(y)}\\
&= O\left(1 + \left(e^{i\Delta t}-1\right)\delta_{1f(y)}\right)\ket{y}\ket{f(y)}\\
&= \left(1 + \left(e^{i\Delta t}-1\right)\delta_{1f(y)}\right)O\ket{y}\ket{f(y)}\\
&= \left(1 + \left(e^{i\Delta t}-1\right)\delta_{1f(y)}\right)\ket{y}\ket{0}\\
&= \left(I + \left(e^{i\Delta t}-1\right)\ket{x}\bra{x}\right)\ket{y}\ket{0}\\
&= \exp(i\ket{x}\bra{x}\Delta t)\ket{y}\ket{0}
\end{aligned}$$

That last step can be justified because operator $\ket{x}\bra{x}$ has two eigenvalues, 1 for the subspace spanned by $\ket{x}$ and 0 for the orthogonal subspace. Therefore, for any scalar $a$

$$\begin{aligned}
e^{a\ket{x}\bra{x}} &= e^{a(0)}(I-\ket{x}\bra{x}) + e^{a(1)}\ket{x}\bra{x} \\
&= I + (e^a-1)\ket{x}\bra{x}
\end{aligned}$$

One can see that the circuit in Figure 6.4 implements the operation $\exp(i\ket{x}\bra{x}\Delta t)\neq \exp(-i\ket{x}\bra{x}\Delta t)$. This can be fixed by using the gate 

$$\begin{aligned}
\begin{bmatrix} 1 & 0 \\\ 0 & e^{-i\Delta t}\end{bmatrix} 
\end{aligned}$$

instead of the one drawn in the figure.  

Figure 6.5 performs the operation

$$\begin{aligned}
\left(H^{\otimes n}\otimes I\right)\bar{C}^nNOT\left(I_n\otimes P(\Delta t)\right)\bar{C}^nNOT\left(H^{\otimes n}\otimes I\right)\ket{y}\ket{0} &= \left(H^{\otimes n}\otimes I\right)\bar{C}^nNOT\left(I_n\otimes P(\Delta t)\right)\bar{C}^nNOT \left(\frac{1}{2^{n/2}}\otimes_{i=0}^{n-1}\left(\ket{0} + (-1)^{y_i}\ket{1}\right)\right)\ket{0}\\
&= \left(H^{\otimes n}\otimes I\right)\bar{C}^nNOT\left(I_n\otimes P(\Delta t)\right)\frac{1}{2^{n/2}}\left(\ket{0\cdots 0}\ket{1} + \otimes_{i=0}^{n-1}\left(\ket{0} + (-1)^{y_i}\ket{1}\right)\ket{0}-\ket{0\cdots 0}\ket{0}\right)\\
&= \left(H^{\otimes n}\otimes I\right)\bar{C}^nNOT\frac{1}{2^{n/2}}\left(e^{i\Delta t}\ket{0\cdots 0}\ket{1} + \otimes_{i=0}^{n-1}\left(\ket{0} + (-1)^{y_i}\ket{1}\right)\ket{0}-\ket{0\cdots 0}\ket{0}\right)\\
&= \left(H^{\otimes n}\otimes I\right)\frac{1}{2^{n/2}}\left(e^{i\Delta t}\ket{0\cdots 0}\ket{0} + \otimes_{i=0}^{n-1}\left(\ket{0} + (-1)^{y_i}\ket{1}\right)\ket{0}-\ket{0\cdots 0}\ket{0}\right)\\
&= \ket{y}\ket{0} + \left(H^{\otimes n}\otimes I\right)\frac{1}{2^{n/2}}\left(e^{i\Delta t} - 1\right)\ket{0\cdots 0}\ket{0}\\
&= \ket{y}\ket{0} + \frac{1}{2^{n/2}}\left(e^{i\Delta t} - 1\right)\frac{\sum_{x}\ket{x}}{\sqrt{N}}\ket{0}\\
&= \ket{y}\ket{0} + \frac{1}{2^{n/2}}\left(e^{i\Delta t} - 1\right)\ket{\psi}\ket{0}\\
&= \left(I + \left(e^{i\Delta t} - 1\right)\ket{\psi}\bra{\psi}\right)\ket{y}\ket{0} & \text{since $\braket{\psi\vert y}= \frac{1}{2^{n/2}}$}\\
&= \exp(i\ket{\psi}\bra{\psi}\Delta t)
\end{aligned}$$

Like with Figure 6.4, there is a sign difference that can be fixed by using the gate 

$$\begin{aligned}
\begin{bmatrix} 1 & 0 \\\ 0 & e^{-i\Delta t}\end{bmatrix} 
\end{aligned}$$

instead of the one drawn in the figure.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.8 {#exercise-68}

Suppose the simulation step is performed to an accuracy $O(\Delta t^r)$. Show that the number of oracle calls required to simulate $H$ to reasonable accuracy is $O\left(N^{r/2(r-1)}\right)$.

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

Since the step length is $\Delta t$ the total number of steps required is $t/\Delta t=\Theta(\sqrt{N}/\Delta t)$, and thus the cumulative error is $O(\Delta t^r\times \sqrt{N}/\Delta t) = O(\Delta t^{r-1}\sqrt{N})$. We need the error to be $O(1)$, which means we must choose $\Delta t = \Theta\left(N^{-\frac{1}{2(r-1)}}\right)$ and so the number of oracle calls scales like $O\left(\sqrt{N}/N^{-\frac{1}{2(r-1)}}\right) = O\left(N^{\frac{1}{2} + \frac{1}{2(r-1)}}\right) = O\left(N^{r/2(r-1)}\right)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.9 {#exercise-69}

Verify Equation (6.25).

I couldn't initially find a "simple calculation" to verify this equation because I wasn't sure how to convert the equation into a composition of two rotation operations and so I instead brute forced it using some identities that I derived in [Exercise 4.6](https://adj59-dev.github.io/2025/09/27/reading-nielsen-and-chuang-chapter-4.html#exercise-46). Later, I did figure it out (I think) and re-did the exercise using the results from [Exercise 4.15](https://adj59-dev.github.io/2025/09/27/reading-nielsen-and-chuang-chapter-4.html#exercise-415), which was significantly easier. I've left both solutions below.  

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

$$\begin{aligned}
U(\Delta t) &= e^{-i\ket{\psi}\bra{\psi}\Delta t}e^{-i\ket{x}\bra{x}\Delta t}\\
&= \left(I + \left(e^{-i\Delta t}-1\right)\ket{\psi}\bra{\psi}\right)\left(I + \left(e^{-i\Delta t}-1\right)\ket{x}\bra{x}\right)\\
&= I + \left(e^{-i\Delta t}-1\right)\left(\ket{\psi}\bra{\psi} + \ket{x}\bra{x}\right) + \left(e^{-i\Delta t}-1\right)^2\left(\ket{\psi}\bra{\psi}\ket{x}\bra{x}\right)\\
&= I + \frac{e^{-i\Delta t}-1}{2}\left(\left(I + \vec{\psi}\cdot\vec{\sigma}\right) + \left(I+\hat{z}\cdot\vec{\sigma}\right)\right) + \frac{\left(e^{-i\Delta t}-1\right)^2}{4}\left(\left(I + \vec{\psi}\cdot\vec{\sigma}\right)\left(I+\hat{z}\cdot\vec{\sigma}\right) \right)\\
&= I + \frac{e^{-i\Delta t}-1}{2}\left(2I + \vec{\psi}\cdot\vec{\sigma}+ \hat{z}\cdot\vec{\sigma}\right) + \frac{\left(e^{-i\Delta t}-1\right)^2}{4}\left(I+\hat{z}\cdot\vec{\sigma} + \vec{\psi}\cdot\vec{\sigma} + (\vec{\psi}\cdot\vec{\sigma})(\hat{z}\cdot\vec{\sigma})\right)\\
&= I + \frac{e^{-i\Delta t}-1}{2}\left(2I + \vec{\psi}\cdot\vec{\sigma}+ \hat{z}\cdot\vec{\sigma}\right) + \frac{\left(e^{-i\Delta t}-1\right)^2}{4}\left(I+\hat{z}\cdot\vec{\sigma} + \vec{\psi}\cdot\vec{\sigma} + (\vec{\psi}\cdot\hat{z})I+i(\vec{\psi}\times\hat{z})\cdot\vec{\sigma}\right) & \text{Exercise 4.6}\\
&=\left(e^{-i\Delta t} + \frac{\left(e^{-i\Delta t}-1\right)^2}{4}+ \frac{\left(e^{-i\Delta t}-1\right)^2}{4}\vec{\psi}\cdot\hat{z}\right)I + \left(\frac{e^{-i\Delta t}-1}{2} + \frac{\left(e^{-i\Delta t}-1\right)^2}{4} \right)\left(\vec{\psi}\cdot\vec{\sigma}+ \hat{z}\cdot\vec{\sigma} \right) + \frac{\left(e^{-i\Delta t}-1\right)^2}{4}i(\vec{\psi}\times\hat{z})\cdot\vec{\sigma}\\
&=e^{-i\Delta t}\left(\cos^2\left(\frac{\Delta t}{2}\right) - \sin^2\left(\frac{\Delta t}{2}\right)\vec{\psi}\cdot\hat{z}\right)I - ie^{-i\Delta t}\left(\sin\left(\frac{\Delta t}{2}\right)\cos\left(\frac{\Delta t}{2}\right) \right)\left(\vec{\psi}\cdot\vec{\sigma}+ \hat{z}\cdot\vec{\sigma} \right) - ie^{-i\Delta t}\sin^2\left(\frac{\Delta t}{2}\right)(\vec{\psi}\times\hat{z})\cdot\vec{\sigma} & \text{shown below}\\
&= e^{-i\Delta t} \left\lbrack\left(\cos^2\left(\frac{\Delta t}{2}\right) - \sin^2\left(\frac{\Delta t}{2}\right)\vec{\psi}\cdot\hat{z}\right)I - 2i\sin\left(\frac{\Delta t}{2}\right)\left(\cos\left(\frac{\Delta t}{2}\right)\frac{\vec{\psi}+\hat{z}}{2} + \sin\left(\frac{\Delta t}{2}\right)\frac{\vec{\psi}\times\hat{z}}{2}\right)\cdot \vec{\sigma}\right\rbrack\\
\end{aligned}$$


Here are some calculations that I used above:

$$\begin{aligned}
\sin^2\left(\frac{\Delta t}{2}\right) &=\left(\frac{e^{-i\Delta t/2} - e^{i\Delta t/2}}{2i}\right)^2\\
&= -\frac{\left(e^{-i\Delta t/2} - e^{i\Delta t/2}\right)^2}{4}\\
&= -e^{i\Delta t}\frac{\left(e^{-i\Delta t} - 1\right)^2}{4}\\
\end{aligned}$$

$$\begin{aligned}
\cos^2\left(\frac{\Delta t}{2}\right) &=\left(\frac{e^{i\Delta t/2} + e^{-i\Delta t/2}}{2}\right)^2\\
&= \frac{\left(e^{i\Delta t/2} + e^{-i\Delta t/2}\right)^2}{4}\\
&= \frac{e^{i\Delta t} + e^{-i\Delta t} + 2}{4}\\
&= e^{i\Delta t}\left(e^{-i\Delta t} + \frac{1 + e^{-2i\Delta t} - 2e^{-i\Delta t}}{4}\right)\\
&= e^{i\Delta t}\left(e^{-i\Delta t} + \frac{\left(e^{-i\Delta t}-1\right)^2}{4}\right)\\
\end{aligned}$$

$$\begin{aligned}
\sin\left(\frac{\Delta t}{2}\right)\cos\left(\frac{\Delta t}{2}\right) &= -\left(\frac{e^{-i\Delta t/2} - e^{i\Delta t/2}}{2i}\right)\left(\frac{e^{i\Delta t/2} + e^{-i\Delta t/2}}{2}\right)\\
&= -\frac{e^{-i\Delta t}-e^{i\Delta t}}{4i}\\
&= -e^{i\Delta t}\frac{e^{-i2\Delta t}-1}{4i}\\
&= -e^{i\Delta t}\frac{2e^{-i\Delta t}-2 + e^{-i2\Delta t}+1-2e^{-i\Delta t}}{4i}\\
&= -e^{i\Delta t}\left(\frac{e^{-i\Delta t}-1}{2i} + \frac{\left(e^{-i\Delta t}-1\right)^2}{4i}\right)\\
\end{aligned}$$

Now let's try to verify this equation the way the authors intended. So, we now know that the unimportant global phase factor is $e^{-i\Delta t}$ and so we can write

$$\begin{aligned}
U(\Delta t) &= e^{-i\ket{\psi}\bra{\psi}\Delta t}e^{-i\ket{x}\bra{x}\Delta t}\\
&= e^{-i\Delta t}\left(e^{i\Delta t/2}e^{-i\ket{\psi}\bra{\psi}\Delta t}\right)\left(e^{i\Delta t/2}e^{-i\ket{x}\bra{x}\Delta t}\right)\\
&= e^{-i\Delta t}e^{-i(\ket{\psi}\bra{\psi}-I/2)\Delta t}e^{-i(\ket{x}\bra{x}-I/2)\Delta t}\\
&= e^{-i\Delta t}e^{-i\frac{\Delta t}{2}\vec{\psi}\cdot\vec{\sigma}}e^{-i\frac{\Delta t}{2}\hat{z}\cdot\vec{\sigma}}\\
\end{aligned}$$

Which is the composition of two rotation operations. From exercise 4.15 we know that we can calculate the composition of two rotation operations using

$$\begin{aligned}
R_{\hat{n_2}}(\beta_2)R_{\hat{n_1}}(\beta_1) &= c_{12}I - is_{12}(\hat{n_{12}}\cdot\vec{\sigma}) \\
\end{aligned}$$

In our case, since  $\beta_1 = \beta_2$ and $\hat{n_1} = \hat{z}$, 

$$\begin{aligned}
c_{12} &= c^2 - s^2(\hat{n_2} \cdot \hat{z})\\
&= \cos^2\left(\frac{\Delta t}{2}\right) - \sin^2\left(\frac{\Delta t}{2}\right)(\vec{\psi} \cdot \hat{z})
\end{aligned}$$

and

$$\begin{aligned}
s_{12}\hat{n_{12}} &= sc(\hat{z} + \hat{n_2})+ s^2(\hat{n_2} \times \hat{z}) \\
&= \sin\left(\frac{\Delta t}{2}\right)\cos\left(\frac{\Delta t}{2}\right)(\hat{z} + \vec{\psi})+ \sin^2\left(\frac{\Delta t}{2}\right)(\vec{\psi} \times \hat{z}) 
\end{aligned}$$

Therefore,

$$\begin{aligned}
U(\Delta t) &= e^{-i\Delta t}\left\lbrack\left(\cos^2\left(\frac{\Delta t}{2}\right) - \sin^2\left(\frac{\Delta t}{2}\right)(\vec{\psi} \cdot \hat{z})\right)I - i\left(\sin\left(\frac{\Delta t}{2}\right)\cos\left(\frac{\Delta t}{2}\right)(\hat{z} + \vec{\psi})+ \sin^2\left(\frac{\Delta t}{2}\right)(\vec{\psi} \times \hat{z}) \right)\cdot\vec{\sigma}\right\rbrack \\
&= e^{-i\Delta t} \left\lbrack\left(\cos^2\left(\frac{\Delta t}{2}\right) - \sin^2\left(\frac{\Delta t}{2}\right)\vec{\psi}\cdot\hat{z}\right)I - 2i\sin\left(\frac{\Delta t}{2}\right)\left(\cos\left(\frac{\Delta t}{2}\right)\frac{\vec{\psi}+\hat{z}}{2} + \sin\left(\frac{\Delta t}{2}\right)\frac{\vec{\psi}\times\hat{z}}{2}\right)\cdot \vec{\sigma}\right\rbrack\\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.10 {#exercise-610}

Show that by choosing $\Delta t$ appropriately we can obtain a quantum search algorithm which uses $O(\sqrt{N})$ queries, and for which the final state is $\ket{x}$ exactly, that is, the algorithm works with probability 1, rather than with some smaller probability. 

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

If we chose $\Delta t=\pi$ then each oracle call rotates the state by $\theta\approx 4/\sqrt{N}$ and so the number of oracle calls required will be 

$$\begin{aligned}
\frac{\pi}{\theta} &= \frac{\pi}{4/\sqrt{N}}\\
&= \frac{\pi\sqrt{N}}{4}\\
&= O(\sqrt{N})
\end{aligned}$$

The Grover iteration can be written as $G=(2\ket{\psi}\bra{\psi}-I)O=(2\ket{\psi}\bra{\psi}-I)(I-2\ket{x}\bra{x})$. Calculating $U(\pi)$ we get

$$\begin{aligned}
U(\pi) &= e^{-i\ket{\psi}\bra{\psi}\pi}e^{-i\ket{x}\bra{x}\pi}\\
&= (I-2\ket{\psi}\bra{\psi})(I-2\ket{x}\bra{x}) \\
&= e^{i\pi}(2\ket{\psi}\bra{\psi}-I)(I-2\ket{x}\bra{x})\\
&= e^{i\pi}G
\end{aligned}$$

Since $𝑈(\pi)$ is (up to a global phase) the standard Grover iteration, and Grover’s algorithm can be tuned to reach $\ket{x}$ exactly with an appropriate number of iterations, the algorithm using $U(\pi)$ also succeeds with probability 1.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.11 {#exercise-611}

Guess a Hamiltonian with which one may solve the continuous time search problem in the case where the search problem has $M$ solutions. 

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

I'm going to guess the following Hamiltonian

$$\begin{aligned}
H = \ket{\beta}\bra{\beta} + \ket{\psi}\bra{\psi}
\end{aligned}$$

where $\ket{\beta}=\frac{1}{\sqrt{M}}\sum_{x}'\ket{x}$ and $\sum_{x}'$ indicates a sum over all $x$ which are solutions to the search problem. 

Like with the case of one solution, we can restrict the analysis to the two-dimensional space spanned by $\ket{\beta}$ and $\ket{\psi}$. Performing the Gram-Schmidt procedure, we can find $\ket{y}$ such that $\ket{\beta}$, $\ket{y}$ form an orthonormal basis for this space and that $\ket{\psi} = a\ket{\beta} + b\ket{y}$ where $a^2+b^2=1$. For convenience we have chosen the phases of $\ket{\beta}$ and $\ket{y}$ so that $a$ and $b$ are real and non-negative. In this basis we have

$$\begin{aligned}
H = \begin{bmatrix} 1 & 0 \\\ 0 & 0 \end{bmatrix} + \begin{bmatrix} a^2 & ab \\\ ab & b^2 \end{bmatrix} = I + a(bX+aZ)
\end{aligned}$$

Thus

$$\begin{aligned}
\exp(-iHt)\ket{\psi} = \exp(-it)\lbrack\cos(at)\ket{\psi}-i\sin(at)\ket{\beta}\rbrack.
\end{aligned}$$

Thus at time $t=\frac{\pi}{2a}$ yields the result $\ket{\beta}$ with probability one. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.12 {#exercise-612}

Suppose 

$$\begin{aligned}
H=\ket{x}\bra{\psi} + \ket{\psi}\bra{x}
\end{aligned}$$

(1) Show that it takes $O(1)$ to rotate from the state $\ket{\psi}$ to the state $\ket{x}$, given an evolution according to the Hamiltonian $H$.

(2) Explain how a quantum simulation of the Hamiltonian $H$ may be performed and determine the number of oracle calls your simulation technique requrires to obtain the solution with high probability. 

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

(1) Following the same steps that are on page 257, we can restrict the analysis to the two-dimensional space spanned by $\ket{x}$ and $\ket{\psi}$. Performing the Gram-Schmidt procedure, we can find $\ket{y}$ such that $\ket{x}$, $\ket{y}$ form an orthonormal basis for this space and that $\ket{\psi} = a\ket{x} + b\ket{y}$ where $a^2+b^2=1$. For convenience we have chosen the phases of $\ket{x}$ and $\ket{y}$ so that $a$ and $b$ are real and non-negative. In this basis we have

$$\begin{aligned}
H &= \begin{bmatrix} 1 \\\ 0 \end{bmatrix}\begin{bmatrix} a & b \end{bmatrix} + \begin{bmatrix} a \\\ b \end{bmatrix}\begin{bmatrix} 1 & 0 \end{bmatrix} \\
&= \begin{bmatrix} a & b \\\ 0 & 0 \end{bmatrix} + \begin{bmatrix} a & 0 \\\ b & 0 \end{bmatrix}\\
&= \begin{bmatrix} 2a & b \\\ b & 0 \end{bmatrix} \\
&= a(I + Z) + bX\\
\end{aligned}$$

Thus

$$\begin{aligned}
\exp(-iHt)\ket{\psi} &= \exp\left(-it\left(aI + aZ + bX\right)\right)\ket{\psi}\\
&= \exp\left(-iat\right)\exp\left(-it\left(aZ + bX\right)\right)\ket{\psi}\\
&= \exp\left(-iat\right)\left\lbrack \cos(t) - i\sin(t)\left(aZ + bX\right)\right\rbrack\ket{\psi} & \text{equation 4.7}\\
&= \exp\left(-iat\right)\left\lbrack \cos(t)\ket{\psi} - i\sin(t)\ket{x}\right\rbrack \\
\end{aligned}$$

You can see that at time $t=\frac{\pi}{2}$ this yields the result $\ket{x}$ with probability one. Notice, this does not depend on $a$ or $b$ and so the evolution time under $H$ is constant - it is $O(1)$. 


(2) Let's label the Hamiltonians from equation 6.18 and 6.19 as $H_{6.18} = \ket{x}\bra{x} + \ket{\psi}\bra{\psi}$ and $H_{6.19}=\ket{x}\bra{\psi}+\ket{\psi}\bra{x}$, respectively, and set $\ket{\psi}=\frac{\sum_x\ket{x}}{\sqrt{N}}$ as in equation 6.24. Comparing part 1 of this exercise to equations 6.22 and 6.23, we see that  

$$\begin{aligned}
\exp\left(-iH_{6.19} \Delta t\right)\ket{\psi} &= \exp\left(-iH_{6.18} \Delta t/a\right)\ket{\psi}  \\
&= \exp\left(-iH_{6.18} \Delta t\sqrt{N}\right)\ket{\psi}  & \text{from equation 6.24}\\
&= \left(\exp\left(-iH_{6.18} \Delta t\right)\right)^{\sqrt{N}}\ket{\psi} \\
\end{aligned}$$

up to an unimportant global phase. Therefore, it is possible to simulate $\exp\left(-iH_{6.19} \Delta t\right)$ by $\sqrt{N}$ number of implementations of the simulation for $\exp\left(-iH_{6.18} \Delta t\right)$. We confirmed in [exercise 6.7](#exercise-67) that it takes 2 oracle calls to simulate $\exp\left(-iH_{6.18} \Delta t\right)$ and so it will take $2\sqrt{N}$ oracle calls to simulate $\exp\left(-iH_{6.19} \Delta t\right)$. 

The total number of oracle calls will be dependent on the number of steps taken which will equal $s=t/\Delta t$. The accuracy of the simulation will be dependent on the accuracy of each $\exp\left(-iH_{6.18} \Delta t\right)$ simulation, if we say that accuracy is $O(\Delta t^r)$ then the total error behaves like $\Delta t^r \frac{t}{\Delta t}\sqrt{N} = t\sqrt{N}\Delta t^{r-1}$. Therefore, to get $O(1)$ total error, we need $\Delta t = O\left(\left(t\sqrt{N}\right)^{-\frac{1}{r-1}}\right)$. Therefore $s=O\left(t\left(t\sqrt{N}\right)^{\frac{1}{r-1}}\right)=O\left(\left(\sqrt{N}\right)^{\frac{1}{r-1}}\right)$, since $t=O(1)$. Then the total number of oracle calls will be $O\left(N^{r/2(r-1)}\right)$. This is the same as what we got for $H_{6.18}$ in [exercise 6.8](#exercise-68).

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


## Quantum counting

### Exercise 6.13 {#exercise-613}

Consider a classical algorithm for the counting problem which samples uniformly and independently $k$ times from the search space, and let $X_1,\cdots,X_k$ be the results of the oracle calls, that is, $X_j=1$ if the *j*th oracle call revealed a solution to the problem, and $X_j=0$ if the *j*th oracle call did not reveal a solution to the problem. This algorithm returns the estimate $S\equiv N\times \sum_j X_j/k$ for the number of solutions to the search problem. Show that the standard deviation in $S$ is $\Delta S=\sqrt{M(N-M)/k}$. Prove that to obtain a probability at least $3/4$ of estimating $M$ correctly to within an accuracy of $\sqrt{M}$ for all values of $M$ we must have $k=\Omega(N)$.

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

Since the samples are uniform and independent, this oracle is sampling a Bernoulli distribution where there is a $p=\frac{M}{N}$ probability of the oracle call returning $X_j=1$ and a $1-p=\frac{N-M}{N}$ probability of returning $X_j=0$. The variance of a Bernoulli distribution for each $X_j$ is given by 

$$\begin{aligned}
\text{Var}\lbrack X_j \rbrack &= p(1-p)\\
&= \frac{M(N-M)}{N^2}
\end{aligned}$$

The variance of the sample mean $\bar{X}=\frac{1}{k}\sum_{j=1}^k X_j$ for $k$ oracle calls is then

$$\begin{aligned}
\text{Var}\lbrack\bar{X}\rbrack &= \frac{\text{Var}\lbrack X_j\rbrack}{k} \\
&= \frac{M(N-M)}{kN^2}
\end{aligned}$$

Since $S=N \bar{X}$

$$\begin{aligned}
\text{Var}\lbrack S \rbrack &= \text{Var}\lbrack\bar{X}\rbrack N^2 \\
&= \frac{M(N-M)}{k}
\end{aligned}$$

and so the standard deviation is

$$\begin{aligned}
\Delta S &= \sqrt{\text{Var}\lbrack S \rbrack} \\
&= \sqrt{\frac{M(N-M)}{k}}
\end{aligned}$$

Using the Chebyshev's inequality, we know

$$\begin{aligned}
Pr\left(\vert S - M \vert \geq \sqrt{M}\right) \leq \frac{\Delta S^2}{M} \\
\end{aligned}$$

We want $Pr\left(\vert S - M \vert \geq \sqrt{M}\right)\leq \frac{1}{4}$ and so we need

$$\begin{aligned}
\frac{1}{4} &\geq \frac{\Delta S^2}{M} \\
&= \frac{M(N-M)}{kM} \\
&= \frac{N-M}{k} \\
\end{aligned}$$

which requires $k \geq 4(N-M)$. To select a $k$ that works for all $M$ we then need $k \geq 4(N-1)$ and so $k=\Omega(N)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>


### Exercise 6.14 {#exercise-614}

Prove that any classical counting algorithm with a probability of at least $3/4$ for estimating $M$ correctly to within an accuracy $c\sqrt{M}$ for some constant $c$ and for all values of $M$ must make $\Omega(N)$ oracle calls. 

I found this to be a really challenging exercise since I don't have much experience finding the lower bounds for a class of algorithms. Looking online, there seems to be a few common concepts used for doing this kind of analysis:
* Comparison-based lower bounds (decision trees)
* Adversary arguments
* Information theory
* Reduction
* Yao's minimax principle

I reviewed some lecture notes to get an idea of what these things are. [Lecture 12: Lower Bounds](https://jeffe.cs.illinois.edu/teaching/algorithms/notes/12-lowerbounds.pdf) discusses decision trees, adversary arguments, and touches on information theory. [Adversary Lower Bound Technique](https://goldman.cse.wustl.edu/crc2007/handouts/adv-lb.pdf) goes into more detail about the adversary arguments. [Chapter G1: Lower Bounds](https://people.computing.clemson.edu/~goddard/texts/algor/G1.pdf) provides more details about information theory and adversary arguments.  

Based on what I read in those notes, I tracked down these YouTube videos to have someone walk me through it:
* [Introduction to Information Theory Lower Bounds](https://www.youtube.com/watch?v=xIryno2jMjY&t=1068s)
* [Second Lecture on Information Theory Lower Bounds](https://www.youtube.com/watch?v=Ws7EYLT43u4)
* [Adversary Lower Bound Arguments](https://www.youtube.com/watch?v=GjimDZlQeJM&list=PL_w_qWAQZtAaNemYPcciRtoJLEJz5MwYW&index=14)
* [Second Lecture on Adversary Lower Bounds](https://www.youtube.com/watch?v=4y6xstHvpz0&list=PL_w_qWAQZtAaNemYPcciRtoJLEJz5MwYW&index=14) - not as helpful

I ended up using a decision tree/information theory argument for this exercise. But it was good to learn more about adversary arguments, even if they were not used.

<details style="margin-bottom: 20px;" markdown="1">
<summary><strong>Click to view the solution</strong></summary>

First, we need to create a framework that defines the class of algorithms the authors call "*any* classical counting algorithm". 

What we know:<br>
(1) Any classical counting algorithm makes oracle calls. <br>
(2) $M$ is estimated based on the results of those oracle calls. <br>
(3) enough oracle calls are made such that the algorithm has a probability of at least $3/4$ for estimating $M$ correctly to within an accuracy $c\sqrt{M}$ for some constant $c$ and for all values of $M$ <br>

What we don't know: <br>
(1) How the samples are chosen for the oracle calls, i.e. random or deterministic and independent or not independent. <br>
(2) How the estimation is calculated from the results of the oracle calls. <br>

If we were to use the decision tree framework, the graph below shows any $k=3$ classical counting algorithm.  

<img width="871" height="489" alt="image" src="https://github.com/user-attachments/assets/b487326e-9549-49bd-920f-3f0bc557ed63" />

All deterministic algorithms in this class of algorithms can be represented as decision trees with the same overall shape: each of the $k$ levels correspond to an oracle query, and each branching corresponds to the oracle's answer of $0$ or $1$. A randomized algorithm is simply a probability distribution over such deterministic trees. Because every deterministic tree has the same structure, we may analyze only deterministic trees when proving the lower bound. This is because if every deterministic tree requires $k=\Omega(N)$, they any randomized algorithm (a distribution over such trees) must also require $k=\Omega(N)$.

We can see that there is one leaf per possible sequence of oracle answers. Thinking back to the YouTube videos that I watched, I know that each leaf is mapped to a single output for the algorithm, which we'll label $\hat{M}$, and we need at least one leaf that maps to each possible output (though several leaves may share the same output value). Regardless of its internal computation, the algorithm will only have the following information from the oracle calls: the result of the oracle call $X_j$ from the $k$ indices $j\in \lbrace 1,\cdots N\rbrace$. Calling the oracle for the same index more than once never reveals new information, so we may assume without loss of generality that the algorithm samples $k$ distinct indices without replacement. This is because if we can show that any algorithm that samples without replacement must make $\Omega(N)$ oracle calls to achieve the desired accuracy, then we can also say that algorithms that sample with replacement can't do any better since they will have less information. 

We know that the good outputs for the algorithm for a specific $M$ lie in $\lbrack M-c\sqrt{M}, M+c\sqrt{M}\rbrack$ for some constant $c$ and all $M$. This means that we need at least one leaf that maps to $\hat{M_0}=0$ for when $M=0$. Let $t$ be the smallest value such that $t-c\sqrt{t}>0$. Then, there needs to be a different leaf that maps to $\hat{M_t}\in \lbrack t-c\sqrt{t}, t+c\sqrt{t}\rbrack$ for when $M=t$. We know the $\hat{M_0}$ output will map to a leaf that consist of all $0$ values for the oracle answers and so the leaf that maps to the $\hat{M_t}$ output will need at least one $1$ value so it is a different leaf than the one that maps to $\hat{M_0}$. 

If we assume that the probability of a single oracle call of returning the value $1$ is $P(X_j)=\frac{t}{N}$ (i.e. random distribution of the marked solutions), then the probability of the oracle returning at least one $1$ value when sampling $k$ indices without repeat for $M=t$ is  

$$\begin{aligned}
p &= P\left(\cup_{j=1}^{k} X_j\right)\\
&\leq \sum_{j=1}^{k}P(X_j) & \text{Boole's inequality}\\
&= k\frac{t}{N}
\end{aligned}$$

We need $p \geq \frac{3}{4}$ so there is a probability of at least $3/4$ for estimating $M=t$ correctly. So we need to find a $k$ such that $k\frac{t}{N}\geq p \geq \frac{3}{4}$. Therefore,

$$\begin{aligned}
&\frac{3}{4} \leq k\frac{t}{N} \\
\Rightarrow & k\geq N\frac{3}{4t}
\end{aligned}$$

Therefore, this lower bounds argument give us $k=\Omega(N)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>



## Optimality of the search algorithm


### Exercise 6.15 {#exercise-615}

Note: the authors use the notation $\psi$ for $\ket{\psi}$ and $x$ for $\ket{x}$. 

The Cauchy-Schwarz inequality can be written in many forms, but the one relevant to this exercise states that $\left(\sum_{i=1}^n u_iv_i\right)^2 \leq \left(\sum_{i=1}^n u_i^2 \right)\left(\sum_{i=1}^n v_i^2\right)$ and so using that,

$$\begin{aligned}
\sum_{x} \Vert \psi-x\Vert^2 &= \sum_{x} \braket{\psi-x \vert \psi-x}  \\
&= \sum_{x} \braket{\psi\vert \psi} + \braket{x\vert x} - \braket{\psi \vert x} - \braket{x \vert \psi}  \\
&= \sum_{x} 2 - \braket{\psi \vert x} - \braket{x \vert \psi}  \\
&= \sum_{x} 2 - 2\text{Re}\left(\braket{\psi \vert x}\right) & \text{since $\braket{\psi \vert x}=\braket{x \vert \psi}^\ast$} \\
&= 2N - 2\sum_{x} \text{Re}\left(\braket{\psi \vert x}\right) \\
&\geq 2N - 2\sum_{x} \vert\braket{\psi \vert x}\vert \\
&= 2N - 2\sqrt{\left(\sum_{x} \vert\braket{\psi \vert x}\vert \right)^2} \\
&\geq 2N - 2\sqrt{\left(\sum_{x} \vert\braket{\psi \vert x}\vert^2 \right)\left(\sum_{x} 1^2\right)}  & \text{Cauchy-Schwarz}\\
&= 2N - 2\sqrt{\left( 1 \right)\left(\sum_{x} 1 \right)}  & \text{Since $\psi$ is normalized and $\lbrace x\rbrace$ is an orthonormal basis}\\
&= 2N - 2\sqrt{N}\\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 6.16 {#exercise-616}

Based on what section this question is in and the wording of the question, I'm going to assume we need to prove that $\Omega(\sqrt{N})$ oracle calls are still required. 

We can start with the same proof as is outlined in section 6.6 up until the first full paragraph on page 270. Here instead of $\vert \braket{x\vert\psi_k^x}\vert^2\geq 1/2$ for all $x$, now, 

$$\begin{aligned}
\frac{1}{2} &\leq \frac{1}{N}\sum_x \vert \braket{x\vert\psi_k^x}\vert^2 \\ 
\end{aligned}$$

and so

$$\begin{aligned}
E_k &\equiv \sum_x \Vert \psi_k^x - x \Vert^2 \\
&= \sum_x 2 - 2\vert \braket{x \vert \psi_k^x} \vert & \text{equation 6.47}\\
&= 2N - 2\sum_x \vert \braket{x \vert \psi_k^x} \vert \\
&\leq 2N - 2\sum_x \vert \braket{x \vert \psi_k^x} \vert^2 & \text{since $\vert \braket{x \vert \psi_k^x} \vert \in \lbrack 0, 1\rbrack$}\\
&\leq 2N -2\frac{N}{2} & \text{from probability of error}\\
&= N
\end{aligned}$$

So, $E_k \leq N$ and $F_k \geq 2N - 2 \sqrt{N}$ remains unchanged. Therefore,

$$\begin{aligned}
D_k &\geq E_k + F_k - 2\sqrt{E_kF_k}\\
&\geq N + 2N-2\sqrt{N} - 2\sqrt{N(2N-2\sqrt{N})}\\
&= N\left(3 - 2\sqrt{2 - 2\frac{1}{\sqrt{N}}}\right) - 2\sqrt{N} \\
&= cN & \text{where $c\approx 0.17$ for large $N$}
\end{aligned}$$

Since $cN \leq D_k\leq 4k^2$ this implies $k\geq\sqrt{cN/4}$.  Therefore, $\Omega(\sqrt{N})$ oracle calls are still required. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 6.17 {#exercise-617}

For this one, I am also going to assume that we need to prove $\Omega(\sqrt{N/M})$ oracle calls are requried to find a solution to the search problem that has $M$ solutions.

Now that there are multiple sultions, the oracle is $O_S=I-\sum_x' \ket{x}\bra{x}$  where $\sum_x'$ represents the sum over all $M$ solutions to the search problem. 

$$\begin{aligned}
D_k = \sum_S \Vert\psi_k^S - \psi_k\Vert^2
\end{aligned}$$

where the sum is over all possible sets $S$ of size $M$. 

Now let's find a bound for $D_k$ in relation to $k$. Like the one solution case, $D_k=0$ when $k=0$. Then,

$$\begin{aligned}
D_{k+1} &= \sum_S \Vert O_S \psi_k^S - \psi_k\Vert^2 \\
&= \sum_S \Vert O_S (\psi_k^S - \psi_k) + (O_S-I)\psi_k \Vert^2 \\
&\leq \sum_S \left(\Vert O_S(\psi_k^S-\psi_k)\Vert^2 + 2\Vert O_S(\psi_k^S-\psi_k)\Vert\Vert(O_S-I)\psi_k \Vert + \Vert(O_S-I)\psi_k \Vert^2\right)\\
&= \sum_S \left(\Vert \psi_k^S-\psi_k\Vert^2 + 2\Vert \psi_k^S-\psi_k \Vert\Vert\sum_x' \ket{x}\braket{x\vert\psi_k} \Vert + \Vert\sum_x' \ket{x}\braket{x\vert\psi_k} \Vert^2\right)\\
\end{aligned}$$

If we maintain the constraint that the algorithm must yield a solution to the search problem with probability at least one-half then we can say $\vert\braket{x\vert\psi_k^x}\vert^2\geq \frac{1}{2M}$. Now,

$$\begin{aligned}
\Vert\psi_k^x-x\Vert^2 &= 2 - \vert\braket{x\vert\psi_k^x}\vert \\
&\leq 2 - \sqrt{\frac{2}{M}}
\end{aligned}$$

and so 

$$\begin{aligned}
E_k\leq \left(2-\sqrt{\frac{2}{M}}\right)N.
\end{aligned}$$

$F_k$ remains unchanged from the one soltuion case and so

$$\begin{aligned}
D_k &= E_k + F_k - 2\sqrt{E_kF_k}\\
&\geq \left(2-\sqrt{\frac{2}{M}}\right)N + 2N - 2\sqrt{N} - 2\sqrt{\left(2-\sqrt{\frac{2}{M}}\right)N\left(2N-2\sqrt{N}\right)}\\
\end{aligned}$$





##  Black box algorithm limits












