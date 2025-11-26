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



