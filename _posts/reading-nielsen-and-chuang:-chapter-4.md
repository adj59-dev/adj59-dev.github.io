# Reading Nielsen and Chuang: Chapter 3

I just finished reading Chapter 4 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. 




## Navigation

* [Quantum algorithms](#quantum-algorithms)
* [Single qubit operations](#single-qubit-operations)
* [Controlled operations](#controlled-operations)
* [Measurement](#measurement)
* [Universal quantum gates](#universal-quantum-gates)
* [Summary of the quantum circuit model of computation](#summary-of-the-quantum-circuit-model-of-computation)
* [Simulation of quantum systems](#simulation-of-quantum-systems)
* [Chapter Problems](#chapter-problems)




## Quantum algorithms

### Quantum algorithms - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Quantum Fourier transform            | 4.1                       | Exponential speedup over classical algorithms. Created by Shor.  |
| Quantum searching                    | 4.1                       | Quadratic speedup over classical algorithms. Based on Grover's algorithm. |


## Single qubit operations

### Single qubit operations - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Important single qubit gates         | 4.2                       | Pauli matrices $X$, $Y$, and $Z$, Hadamard gate $H$, phase gate $S$, and $\pi/8$ gate $T$. <br> $X = \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \qquad Y = \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \qquad Z = \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix}$ $H = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \qquad S = \begin{bmatrix} 1 & 0 \\\ 0 & i \end{bmatrix} \qquad T = \begin{bmatrix} 1 & 0 \\\ 0 & \exp(i\pi/4) \end{bmatrix}$ <br> Useful algebraic facts: $H=(X+Z)/\sqrt{2}$ and $S=T^2$ |
|Bloch sphere representation           | 4.2                       | Single qubit state $\ket{\psi}=\cos(\theta/2)\ket{0} + e^{i\phi}\sin(\theta/2)\ket{1}$ can be visualized as a point on a unit sphere with vector $(\cos\phi \sin\theta, \sin\phi\sin\theta, \cos\theta)$ |
| Rotation operators                   | 4.2                       | $R_x(\theta) = e^{-i\theta X/2} = \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}X = \begin{bmatrix} \cos\frac{\theta}{2} & -i\sin\frac{\theta}{2} \\\ -i\sin\frac{\theta}{2} & \cos\frac{\theta}{2} \end{bmatrix}$ <br> $R_y(\theta) = e^{-i\theta Y/2} = \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Y = \begin{bmatrix} \cos\frac{\theta}{2} & -\sin\frac{\theta}{2} \\\ \sin\frac{\theta}{2} & \cos\frac{\theta}{2} \end{bmatrix}$ <br> $R_z(\theta) = e^{-i\theta Z/2} = \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Z = \begin{bmatrix} e^{i\theta/2} & 0 \\\ 0 & e^{-i\theta/2}\end{bmatrix}$ |


### Single qubit operations - Exercises
  
**Exercise 4.1** 

For this exercise we are asked to find the points on the Bloch sphere which correspond to the normalized eigenvectors of the different Pauli matrices.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

The eigenvectors for $Z$ are $\ket{0}$ and $\ket{1}$. These correspond to Bloch vectors of $(0, 0, 1)$ and $(0, 0, -1)$.

The eigenvectors for $X$ are $\frac{1}{\sqrt{2}}(\ket{0} + \ket{1})$ and $\frac{1}{\sqrt{2}}(\ket{0} - \ket{1})$. These correspond to Bloch vectors of $(1, 0, 0)$ and $(-1, 0, 0)$.

The eigenvectors for $Y$ are $\frac{1}{\sqrt{2}}(\ket{0} + i\ket{1})$ and $\frac{1}{\sqrt{2}}(\ket{0} - i\ket{1})$. These correspond to Bloch vectors of $(0, 1, 0)$ and $(0, -1, 0)$.

</details>

**Exercise 4.2**

Show that $\exp(iAx)=\cos(x)I+i\sin(x)A$ when $x$ is a real number and $A$ is a matrix such that $A^2=I$. Then use that result to verify equations 4.4-4.6.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

First we show that $\exp(iAx)=\cos(x)I+i\sin(x)A$

$$\begin{align}
\exp(iAx) &= \cos(Ax) + i\sin(Ax) & \text{Euler's formula} \\
&= \sum_{i}\cos(x\lambda_i)\ket{i}\bra{i} + \sum_j i\sin(x\lambda_j)\ket{j}\bra{j} & \text{spectral decomposition and applying functions}\\
&= \cos(x)\ket{+1}\bra{+1} + \cos(-x)\ket{-1}\bra{-1} + i\sin(x)\ket{+1}\bra{+1} + i\sin(-x)\ket{-1}\bra{-1} & \text{since $A^2=I$ its eigenvalues must be $\pm 1$ with eigenvectors $\ket{\pm 1}$}\\
&= \cos(x)\ket{+1}\bra{+1} + \cos(x)\ket{-1}\bra{-1} + i\sin(x)\ket{+1}\bra{+1} - i\sin(x)\ket{-1}\bra{-1} \\
&= \cos(x)(\ket{+1}\bra{+1} + \ket{-1}\bra{-1}) + i\sin(x)(\ket{+1}\bra{+1} - \ket{-1}\bra{-1}) \\
&= \cos(x) I + i\sin(x) A
\end{align}$$

Now we use the result to verify equations 4.4 - 4.6. From exercise 2.19 we know that the Pauli matrices are Hermitian and unitary (i.e. $A^2=I$), therefore we can directly use the result above to generate equations 4.4-4.6 by replacing $A$ with $X$, $Y$, or $Z$. 

$$\begin{aligned}
R_x(\theta) = e^{-i\theta X/2} = \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}X = \cos\frac{\theta}{2}\begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} - i\sin\frac{\theta}{2}\begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} = \begin{bmatrix} \cos\frac{\theta}{2} & -i\sin\frac{\theta}{2} \\\ -i\sin\frac{\theta}{2} & \cos\frac{\theta}{2} \end{bmatrix} \\
R_y(\theta) = e^{-i\theta Y/2} = \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Y = \cos\frac{\theta}{2}\begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} - i\sin\frac{\theta}{2}\begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} = \begin{bmatrix} \cos\frac{\theta}{2} & -\sin\frac{\theta}{2} \\\ \sin\frac{\theta}{2} & \cos\frac{\theta}{2} \end{bmatrix} \\
R_z(\theta) = e^{-i\theta Z/2} = \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}Z = \cos\frac{\theta}{2}\begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} - i\sin\frac{\theta}{2}\begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} = \begin{bmatrix} e^{-i\theta/2} & 0 \\\ 0 & e^{i\theta/2} \end{bmatrix}
\end{aligned}$$

</details>


**Exercise 4.3**

Show that, up to a global phase, the $\pi/8$ gate satisfies $T=R_z(\pi/4)$.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

Let's first calculate $R_z(\pi/4)$

$$\begin{aligned}
R_z(\pi/4) &= \begin{bmatrix} e^{-i(\pi/4)/2} & 0 \\\ 0 & e^{i(\pi/4)/2} \end{bmatrix} \\
&= \begin{bmatrix} e^{-i\pi/8} & 0 \\\ 0 & e^{i\pi/8} \end{bmatrix} \\
&= e^{-i\pi/8}\left(e^{i\pi/8}\begin{bmatrix} e^{-i\pi/8} & 0 \\\ 0 & e^{i\pi/8} \end{bmatrix} \right) \\
&= e^{-i\pi/8} T & \text{per equation 4.3}
\end{aligned}$$

Therefore,  up to a global phase $e^{-i\pi/8}$, the $\pi/8$ gate satisfies $T=R_z(\pi/4)$.

</details>


**Exercise 4.4**

Express the Hadamard gate $H$ as a product of $R_x$ and $R_z$ rotations and $e^{i\phi}$ for some $\phi$.

Let's first think about what $H$ does. In section 1.3.1 we're told that $H$ is a rotation on the Bloch sphere about the y axis by $90\degree$ and then a rotation about the x axis by $180\degree$. Therefore,

$$\begin{aligned}
H &= R_x(\pi)R_y(\pi/2)e^{i\phi} \\
&= (\cos\frac{\pi}{2}I - i\sin\frac{\pi}{2}X)(\cos\frac{\pi}{4}I - i\sin\frac{\pi}{4}Y)e^{i\phi} \\
&= \frac{-ie^{i\phi}}{\sqrt{2}}XI - \frac{e^{i\phi}}{\sqrt{2}}XY \\
&= \frac{-ie^{i\phi}}{\sqrt{2}}X - \frac{e^{i\phi}}{\sqrt{2}}(iZ) & \text{per equation 2.78}\\
&= \frac{-ie^{i\phi}}{\sqrt{2}}(X + Z) \\
&= -ie^{i\phi} H & \text{since $H=(X+Z)/\sqrt{2}$}
\end{aligned}$$

Therefore, $e^{i\phi} = i$, so $\phi=\pi/2$ and we get $H=R_x(\pi)R_y(\pi/2)e^{i\pi/2}$. Unfortunatly, we were not asked to write $H$ in terms fo $R_x$ and $R_y$, we were asked to write it in terms of $R_x$ and $R_z$, so now we need to see if we can write $R_y(\pi/2)$ in terms of $R_x$ and $R_z$. 

$$\begin{aligned}
R_x(\pi)R_y(\pi/2) &= R_x(\pi)R_z(\pi/2)R_x(\pi/2)R_z(-\pi/2) & \text{decomposition} \\
&= R_z(-\pi/2)R_x(\pi)R_x(\pi/2)R_z(-\pi/2) & \text{conjugation flips $Z$ under a $\pi$ rotation about $X$} \\
&= R_z(-\pi/2)R_x(3\pi/2)R_z(-\pi/2) & \text{combinding the rotations about $X$}\\
&= -R_z(-\pi/2)R_x(-\pi/2)R_z(-\pi/2) & \text{$3\pi/2$ rotation is the same as a $-\pi/2$ rotation with a -1 global phase change} \\
&= e^{-i\pi}R_z(-\pi/2)R_x(-\pi/2)R_z(-\pi/2)
\end{aligned}$$

Therefore, $H=e^{-i\pi/2}R_z(-\pi/2)R_x(-\pi/2)R_z(-\pi/2)=e^{i\pi/2}R_z(\pi/2)R_x(\pi/2)R_z(\pi/2)$. Which will be shown below

$$\begin{aligned}
e^{i\pi/2}R_z(\pi/2)R_x(\pi/2)R_z(\pi/2) &= e^{i\pi/2}(\cos\frac{\pi}{4}I - i\sin\frac{\pi}{4}Z)(\cos\frac{\pi}{4}I - i\sin\frac{\pi}{4}X)(\cos\frac{\pi}{4}I - i\sin\frac{\pi}{4}Z) \\
&= e^{i\pi/2}(\frac{1}{\sqrt{2}}I - i\frac{1}{\sqrt{2}}Z)(\frac{1}{\sqrt{2}}I - i\frac{1}{\sqrt{2}}X)(\frac{1}{\sqrt{2}}I - i\frac{1}{\sqrt{2}}Z) \\
&= 
\end{aligned}$$

