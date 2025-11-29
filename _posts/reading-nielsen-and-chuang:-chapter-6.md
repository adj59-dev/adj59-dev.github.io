---
title: "Reading Nielsen and Chuang: Chapter 6"
description: "Notes and exercise solutions for QCQI Chapter 6: quantum search algorithms, quantum counting, speeding up the solution of NP-complete problems."
categories:
  - Quantum Computation and Quantum Information
tags:
  - QCQI
  - quantum computing
  - Quantum Computation and Quantum Information
  - Nielsen & Chuang
  - chapter 6
  - exercise
  - problem
  - solutions
---


# Reading Nielsen and Chuang: Chapter 6

I just finished reading Chapter 6 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. 

## Navigation

* [The quantum search algorithm](#the-quantum-search-algorithm)
* [Quantum search as a quantum simulation](#quantum-search-as-a-quantum-simulation)
* [Quantum counting](#quantum-counting)
* [Speeding up the solution of NP-complete problems](#speeding-up-the-solution-of-np-complete-problems)
* [Quantum search of an unstructured database](#quantum-search-of-an-unstructured-database)
* [Optimality of the search algorithm](#optimality-of-the-search-algorithm)
* [Black box algorithm limits](#black-box-algorithm-limits)
* [Chapter problems](#chapter-problems)



## The quantum search algorithm

### The quantum search algorithm - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Grover iteration                     | 6.1.2                     | (1) Apply the oracle $O$. <br> (2) Apply the Hadamard transform $H^{\otimes n}$. <br> (3) Perform a conditional phase shift on the computer, with every computation basis state except $\ket{0}$ recieving a phase shift of -1, $\ket{x}\rightarrow -(-1)^{\delta_{x0}}\ket{x}$. <br> (4) Apply the Hadamard transform $H^{\otimes n}$. <br> $G=(2\ket{\psi}\bra{\psi}-I)O$, where $\ket{\psi}$ is the equally weighted superposition of states. |
| Quantum search algorithm for $M=1$   | 6.1.4                     | **Inputs:** (1) a black box oracle $O$ which performs the transformation $O\ket{x}\ket{q} = \ket{x}\ket{q\oplus f(x)}$ where $f(x)=0 for all $0\leq x< 2^n$ except $x_0$, for which $f(x_0)=1$; (2) $n+1$ qubits in the state $\ket{0}$ <br> **Outputs:** $x_0$ <br> **Runtime:** $O(\sqrt{2^n})$ operations. Succeeds with probability $O(1)$. <br> **Procedure:** <br> 1. initial state: $\ket{0}^{\otimes n}\ket{0}$ <br> 2. apply $H^{\otimes n}$ to the first $n$ qubits, and $HX$ to the last qubit. <br> 3. apply the Grover iteration $R\approx \lceil\pi\sqrt{2^n}/4\rceil$ times. <br> 4. measure the first $n$ qubits. |



### The quantum search algorithm - Exercises

**Exercise 6.1**

Show that the unitary operator corresponding to the phase shift in the Grover iteration is $2\ket{0}\bra{0} - I$.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

Let's calculate $U\ket{x}$ and compare results to desired behavior, where $U=2\ket{0}\bra{0}-I$.

$$\begin{aligned}
U\ket{x} &= \left(2\ket{0}\bra{0} - I\right)\ket{x} \\
&= 2\ket{0}\braket{0\vert x} - \ket{x} \\
&= 2\delta_{x0}\ket{0} - \ket{x} \\
&= -(-1)^{\delta_{x0}}\ket{x}
\end{aligned}$$

This matches the desired behavior and so the unitary operator corresponding to the phase shift in the Grover iteration is $2\ket{0}\bra{0} - I$.

</details>


**Exercise 6.2**

Show that the operation $(2\ket{\psi}\bra{\psi}-I)$ applied to a general state $\sum_{k}\alpha_k\ket{k}$ produces

$$\begin{aligned}
\sum_{k}\lbrack -\alpha_k+2\braket{\alpha}\rbrack\ket{k},
\end{aligned}$$

where $\braket{\alpha}\equiv \sum_k\alpha_k/N$ is the mean value of the $\alpha_k$. For this reason, $(2\ket{\psi}\bra{\psi}-I)$ is sometimes referred to as the inversion about mean operation.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 6.3**

Show that in the $\ket{\alpha}$, $\ket{\beta}$ basis, we may write the Grover iteration as

$$\begin{aligned}
G = \begin{bmatrix} \cos\theta & -\sin\theta \\\ \sin\theta & \cos\theta \end{bmatrix},
\end{aligned}$$

where $\theta$ is a real number in the range $0$ to $\pi/2$ (assuming for simplicity that $M\leq N/2$; this limitation will be lifted shortly, chosen so that 

$$\begin{aligned}
\sin\theta = \frac{2\sqrt{M(N-M)}}{N}
\end{aligned}$$

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

We start with $\ket{\psi} = \cos\frac{\theta}{2}\ket{\alpha} + \sin\frac{\theta}{2}\ket{\beta}$ then

$$\begin{aligned}
G\ket{\psi} &= \begin{bmatrix} \cos\theta & -\sin\theta \\\ \sin\theta & \cos\theta \end{bmatrix}\begin{bmatrix} \cos\frac{\theta}{2} \\\ \sin\frac{\theta}{2} \end{bmatrix}\\
&= \begin{bmatrix} \cos\theta\cos\frac{\theta}{2} - \sin\theta\sin\frac{\theta}{2} \\\ \sin\theta\cos\frac{\theta}{2} + \cos\theta\sin\frac{\theta}{2} \end{bmatrix}\\
&= \begin{bmatrix} \cos\frac{3\theta}{2} \\\ \sin\frac{3\theta}{2} \end{bmatrix}\\
&= \cos\frac{3\theta}{2}\ket{\alpha} + \sin\frac{3\theta}{2}\ket{\beta}
\end{aligned}$$

This agrees with equation 6.11. Therefore, the Grover iteration may be written as matrix $G$ in the $\ket{\alpha}$, $\ket{\beta}$ basis. 

</details>


**Exercise 6.4**

Give explicit steps for the quantum search algorithm, as above, but for the case of multiple solutions $(1<M<N/2)$.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 6.5**

Show that the augmented oracle $O'$ may be constructed using one application of $O$, and elementary quantum gates, using the extra qubit $\ket{q}$.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 6.6**

Verify that the gates in the dotted box in the second figure of Box 6.1 perform the conditional phase shift operation $2\ket{00}\bra{00}-I$, up to an unimportant global phase factor. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>



## Quantum search as a quantum simulation

### Quantum search as a quantum simulation - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|




### Quantum search as a quantum simulation - Exercises


**Exercise 6.7**

Verify that the circuits shown in Figures 6.4 and 6.5 implement the operations $\exp(-i\ket{x}\bra{x}\Delta t)$ and $\exp(-i\ket{\psi}\bra{\psi}\Delta t)$, respectively, with $\ket{\psi}$ as in (6.24).

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 6.8**

Suppose the simulation step is performed to an accuracy $O(\Delta t^r)$. Show that the number of oracle calls required to simulate $H$ to reasonable accuracy is $O\left(N^{r/2(r-1)}\right)$.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

Since the step length is $\Delta t$ the total number of steps required is $t/\Delta t=\Theta(\sqrt{N}/\Delta t)$, and thus the cumulative error is $O(\Delta t^r\times \sqrt{N}/\Delta t) = O(\Delta t^{r-1}\sqrt{N})$. We need the error to be $O(1)$, which means we must choose $\Delta t = \Theta\left(N^{-\frac{1}{2(r-1)}}\right)$ and so the number of oracle calls scales like $O\left(\sqrt{N}/N^{-\frac{1}{2(r-1)}}\right) = O\left(N^{\frac{1}{2} + \frac{1}{2(r-1)}}\right) = O\left(N^{r/2(r-1)}\right)$.

</details>


**Exercise 6.9**

Verify Equation (6.25).

I couldn't initially find a "simple calculation" to verify this equation because I wasn't sure how to convert the equation into a composition of two rotation operations and so I instead brute forced it using some identities that I derived in [Exercise 4.6](https://adj59-dev.github.io/2025/09/27/reading-nielsen-and-chuang-chapter-4.html#exercise-46). Later, I did figure it out (I think) and re-did the exercise using the results from [Exercise 4.15](https://adj59-dev.github.io/2025/09/27/reading-nielsen-and-chuang-chapter-4.html#exercise-415), which was significantly easier. I've left both solutions below.  

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 6.10**

Show that by choosing $\Delta t$ appropriately we can obtain a quantum search algorithm which uses $O(\sqrt{N})$ queries, and for which the final state is $\ket{x}$ exactly, that is, the algorithm works with probability 1, rather than with some smaller probability. 

If we chose $\Delta t=\pi$ then each oracle call rotates the state by $\theta\approx 4/\sqrt{N}$ and so the number of oracal calls required will be 

$$\begin{aligned}
\frac{\pi}{\theta} &= \frac{\pi}{4/\sqrt{N}}\\
&= \frac{\pi\sqrt{N}}{4}\\
&= O(\sqrt{N})
\end{aligned}$$

One oracal call results in the rotation about $\vec{r}$ defined by

$$\begin{aligned}
U(\pi) &= \left(\cos^2\left(\frac{\pi}{2}\right) - \sin^2\left(\frac{\pi}{2}\right)\vec{\psi}\cdot\hat{z}\right)I - 2i\sin\left(\frac{\pi}{2}\right)\left(\cos\left(\frac{\pi}{2}\right)\frac{\vec{\psi}+\hat{z}}{2} + \sin\left(\frac{\pi}{2}\right)\frac{\vec{\psi}\times\hat{z}}{2}\right)\cdot \vec{\sigma}\\
&= \left( - \vec{\psi}\cdot\hat{z}\right)I - 2i\left(\frac{\vec{\psi}\times\hat{z}}{2}\right)\cdot \vec{\sigma}\\
&= -\left(\alpha^2-\beta^2 \right)I - 2i\left(\frac{-2\alpha\beta\hat{y}}{2}\right)\cdot \vec{\sigma} & \text{since $\hat{z}=(0,0,1)$ and $\vec{\psi}=(2\alpha\beta,0,(\alpha^2-\beta^2))$}\\
&= -\left(\alpha^2-\beta^2 \right)I + i\alpha\beta Y\\
&= -\left(\frac{2}{N}-1 \right)I + i\alpha\beta Y
\end{aligned}$$

Applying $U(\pi)$ to $\ket{\psi}$ we get

$$\begin{aligned}
U(\pi)\ket{\psi} &= \left(-\left(\frac{2}{N}-1 \right)I + i\alpha\beta Y\right)\left(\alpha\ket{x} + \beta\ket{y}\right)\\
&= -\left(\frac{2}{N}-1 \right)\left(\alpha\ket{x} + \beta\ket{y}\right) + i\alpha\beta Y\left(\alpha\ket{x} + \beta\ket{y}\right)\\
\end{aligned}$$















