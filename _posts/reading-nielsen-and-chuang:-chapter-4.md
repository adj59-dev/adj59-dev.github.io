# Reading Nielsen and Chuang: Chapter 4

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
| Decomposition for a single qubit     | 4.2                       | There exists real numbers $\alpha$, $\beta$, $\gamma$, and $\delta$ such that a single qubit unitary operator $U$ may be written as $U=e^{i\alpha}R_z(\beta)R_y(\gamma)R_z(\delta)$ |


### Single qubit operations - Exercises

**Rotation Operator Decomposition**

For several exercises in this section, I perform decomposition on the rotation operators $R_x$, $R_y$ and $R_z$ where I write one of these operators in terms of the other ones. I wanted to take a moment here to prove that this is valid and to confirm the signs of the rotations and their ordering; since they do not commute it is important to get their order correct. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Proof</summary>

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

</details>
  
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

I'm not sure how we are supposed to complete this exercise without either knowing the answer to begin with or using some of the techniques that will be covered later in this section. I was able to use the description of the Hadamard gate in section 1.3.1 (where we're told that $H$ is a rotation on the Bloch sphere about the y axis by $90\degree$ and then a rotation about the x axis by $180\degree$ ) and the rotation operators to express $H$ in terms of $R_x$ and $R_y$, but I needed to use decomposition techniques discussed later to write $R_y$ as a product of $R_x$ and $R_z$.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

Let's first think about what $H$ does. In section 1.3.1 we're told that $H$ is a rotation on the Bloch sphere about the y axis by $90\degree$ and then a rotation about the x axis by $180\degree$. Therefore,

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

Therefore, $H=e^{-i\pi/2}R_z(-\pi/2)R_x(-\pi/2)R_z(-\pi/2)=e^{i\pi/2}R_z(\pi/2)R_x(\pi/2)R_z(\pi/2)$. Which will be shown below

$$\begin{aligned}
e^{i\pi/2}R_z(\pi/2)R_x(\pi/2)R_z(\pi/2) &= e^{i\pi/2}\begin{bmatrix} e^{-i\pi/4} & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \begin{bmatrix} \cos\frac{\pi}{4} & -i\sin\frac{\pi}{4} \\\ -i\sin\frac{\pi}{4} & \cos\frac{\pi}{4} \end{bmatrix}  \begin{bmatrix} e^{-i\pi/4} & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \\
&= e^{i\pi/2}\begin{bmatrix} e^{-i\pi/4} & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \begin{bmatrix} \frac{1}{\sqrt{2}} & -i\frac{1}{\sqrt{2}} \\\ -i\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \end{bmatrix} \ \begin{bmatrix} e^{-i\pi/4} & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \\
&= e^{i\pi/2}\begin{bmatrix} e^{-i\pi/4}\frac{1}{\sqrt{2}} & -ie^{-i\pi/4}\frac{1}{\sqrt{2}} \\\ -ie^{i\pi/4}\frac{1}{\sqrt{2}} & e^{i\pi/4}\frac{1}{\sqrt{2}} \end{bmatrix} \begin{bmatrix} e^{-i\pi/4} & 0 \\\ 0 & e^{i\pi/4} \end{bmatrix} \\
&= e^{i\pi/2}\begin{bmatrix} e^{-i\pi/2}\frac{1}{\sqrt{2}} & -i\frac{1}{\sqrt{2}} \\\ -i\frac{1}{\sqrt{2}} & e^{i\pi/2}\frac{1}{\sqrt{2}} \end{bmatrix} \\
&= \frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \\
&= H
\end{aligned}$$

</details>


**Exercise 4.5**

Prove that $(\hat{n}\cdot \vec{\sigma})^2 = I$ and use it to verify equation 4.8.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>



**Exercise 4.6**

Prove that $R_{\hat{n}}(\theta)$ rotates a single qubit state by angle $\theta$ about the $\hat{n}$ axis of the Bloch sphere. Use the evolution of the density operator upon rotation to demonstrate that the Bloch vector after rotation looks like Rodrigues’ rotation formula. Good luck! It is a lot of math. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

From exercise 2.72, we know that we can write the density matrix for a single qubit with Bloch vector $\vec{\lambda}$ as

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

</details>


**Exercise 4.7**

Show that $XYX = -Y$ and use this to prove that $XR_y(\theta)X=R_y(-\theta)$

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.8**

Prove that an arbitrary single qubit unitary operator can be written in the form $U=\exp(i\alpha)R_{\hat{n}}(\theta)$ for some real $\alpha$ and $\theta$, and a real three-dimensional unit vector $\hat{n}$. Then find the values for $\alpha$, $\theta$, and $\hat{n}$ for the Hadamard gate and the phase gate. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

From exercise 2.56, we know that $U=\exp(iK)$ for some Hermitian operator $K$. We also know that any 2x2 Hermitian operator can be written as $K=\alpha I - \frac{\theta}{2}\hat{n}\cdot\vec{\sigma}$ for some real $\alpha$ and $\theta$, and a real three-dimensional unit vector $\hat{n}$, since $\lbrace I, \sigma_x, \sigma_y, \sigma_z\rbrace$ form a basis set. Therefore, 

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

</details>

**Exercise 4.9**

Explain why any single qubit unitary operator can be written in the form 4.12.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

We know from exercise 4.8, we know that $U=\exp(i\alpha)R_{\hat{n}}(\theta)$. We also know that for an operator to be a unitary operator $U^\dagger U = UU^\dagger = I$. Therefore,

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

</details>


**Exercise 4.10**

Give a decomposition analogous to Theorem 4.1 but using $R_x$ instead of $R_z$.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

From exercise 4.9, we know that these criteria must be met in order for this decomposition to work for any unitary operator: $(-ibc + ad )e - i(ibd + ac)f = -(-i(ac -ibd)f + (-ad - ibc)e)^\ast$ and $-i(-ibc + ad )f + (ibd + ac)e = ((ac -ibd)e - i(-ad - ibc)f)^\ast$, with the constraint $\vert (ac -ibd)e - i(-ad - ibc)f \vert^2 + \vert -i(ac -ibd)f + (-ad - ibc)e \vert^2=1$. So, let's check them

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

</details>


**Exercise 4.11**

Suppose $\hat{m}$ and $\hat{n}$ are non-parallel real unit vectors in three dimensions. Use Theorem 4.1 to show that an arbitrary single qubit unitary $U$ may be written $U=e^{i\alpha}R_{\hat{n}}(\beta_1)R_{\hat{m}}(\gamma_1)R_{\hat{n}}(\beta_2)R_{\hat{m}}(\gamma_2)\cdots$ for appropriate choices of $\alpha, \beta_k, \gamma_k$. Note: per the [errata page](https://michaelnielsen.org/qcqi/errata/errata/errata.html) the correct equation is different than what is in the book. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.12**

Give $A$, $B$, $C$, and $\alpha$ for the Hadamard gate.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

From Corollary 4.2 we know that there exist operators $A,B,C$ such that $U=e^{i\alpha}AXBXC$ and $ABC=I$. In exercise 4.4 we showed that the Hadamard gate can be written as $H=e^{i\pi/2}R_z(\pi/2)R_x(\pi/2)R_z(\pi/2)$, but to write it in the requested form we'll need to have it written in terms of $R_z$ and $R_y$. We know,

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

</details>


**Exercise 4.13**

We are asked to prove several identites involving the Pauli matrices and the Hadamard gate.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.14**

Use the previous exercise to show that $HTH = R_x(\pi/4)$ up to a global phase.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

From exercise 4.3 we know that $T=R_z(\pi/4)$ up to a global phase. Therefore, the following is true up to a global phase

$$\begin{aligned}
HTH &= HR_z(\pi/4)H \\
&= R_z(\pi/2)R_x(\pi/2)R_z(\pi/2)R_z(\pi/4)R_z(\pi/2)R_x(\pi/2)R_z(\pi/2) & \text{true up to a global phase per exercise 4.4} \\
&=  R_z(\pi/2)R_x(\pi/2)R_z(-\pi/2)R_z(\pi/2)R_z(\pi/2)R_z(\pi/4)R_z(\pi/2)R_z(\pi/2)R_z(-\pi/2)R_x(\pi/2)R_z(\pi/2)  & \text{since $R_z(-\pi/2)R_z(\pi/2)=I$}\\
&=  R_y(\pi/2)R_z(2\pi + \pi/4)R_y(-\pi/2) & \text{decomposition} \\
&=  R_y(\pi/2)R_z(\pi/4)R_y(-\pi/2) \\
&= R_x(\pi/4) & \text{decomposition} 
\end{aligned}$$

</details>


**Exercise 4.15**

This exercise has us calculate the composition of two rotation operations on a single qubit. Note: The [errata page](https://michaelnielsen.org/qcqi/errata/errata/errata.html) says that in Equations (4.20) and (4.22) the minus sign on the right-hand side should be a plus.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>



## Controlled operations

### Controlled operations - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| CNOT                                 | 4.3                       | Controlled-NOT gate. $\ket{c}\ket{t} \rightarrow \ket{c}\ket{t\oplus c}$ |
| Controlled-U                         | 4.3                       | If the control qubit is set to $\ket{1}$ then $U$ is applied to the target qubit. $\ket{c}\ket{t} \rightarrow \ket{c}U^C\ket{t}$ |





### Controlled operations - Exercises


**Exercise 4.16**

Find the matrix representation for a given circuit.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.17**

For this exercise we are to construct a CNOT gate from a controlled-Z gate and two Hadamard gates.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

The matrix representation for a CNOT gate is

$$\begin{aligned}
CNOT = \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix}
\end{aligned}$$

and the matrix representation for a controlled-Z gate is

$$\begin{aligned}
CZ = \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & -1 \end{bmatrix}
\end{aligned}$$

Let's try $(I \otimes H)CZ(I \otimes H)$ since we know $HZH = X$ from exercise 4.13 and it looks like CNOT is a controlled-X gate.

$$\begin{aligned}
(I \otimes H)CZ(I \otimes H) &= \frac{1}{2}\begin{bmatrix} 1 & 1 & 0 & 0 \\\ 1 & -1 & 0 & 0 \\\ 0 & 0 & 1 & 1 \\\ 0 & 0 & 1 & -1 \end{bmatrix} \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & -1 \end{bmatrix} \begin{bmatrix} 1 & 1 & 0 & 0 \\\ 1 & -1 & 0 & 0 \\\ 0 & 0 & 1 & 1 \\\ 0 & 0 & 1 & -1 \end{bmatrix} \\
 &= \frac{1}{2}\begin{bmatrix} 1 & 1 & 0 & 0 \\\ 1 & -1 & 0 & 0 \\\ 0 & 0 & 1 & -1 \\\ 0 & 0 & 1 & 1 \end{bmatrix} \begin{bmatrix} 1 & 1 & 0 & 0 \\\ 1 & -1 & 0 & 0 \\\ 0 & 0 & 1 & 1 \\\ 0 & 0 & 1 & -1 \end{bmatrix} \\
 &= \frac{1}{2}\begin{bmatrix} 2 & 0 & 0 & 0 \\\ 0 & 2 & 0 & 0 \\\ 0 & 0 & 0 & 2 \\\ 0 & 0 & 2 & 0 \end{bmatrix}  \\
 &= \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix} \\
 &= CNOT
\end{aligned}$$

</details>


**Exercise 4.18**

Here we are to show that Gate 1 = Gate 2

<img width="559" height="207" alt="image" src="https://github.com/user-attachments/assets/bac7a835-2a0b-4d93-9233-ebdb74b0d191" />

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

Let's compare the behavior of the two gates for a basis set of states.

| $\ket{a}\ket{b}$ | $Z^b\ket{a}\ket{b}$ | $\ket{a}Z^a\ket{b}$ |
|:----------------:|:-------------------:|:--------------------|
| $\ket{0}\ket{0}$ | $\ket{0}\ket{0}$    | $\ket{0}\ket{0}$    |
| $\ket{1}\ket{0}$ | $\ket{1}\ket{0}$    | $\ket{1}Z\ket{0}=\ket{1}\ket{0}$    |
| $\ket{0}\ket{1}$ | $Z\ket{0}\ket{1}=\ket{0}\ket{1}$    | $\ket{0}\ket{1}$    |
| $\ket{1}\ket{1}$ | $Z\ket{1}\ket{1} = -\ket{1}\ket{1}$   | $\ket{1}Z\ket{1}=-\ket{1}\ket{1}$   |

Since the behavior of the two gates are the same for all the states, the two gates are equivalent. 

</details>


**Exercise 4.19**

Explicitly write out the action of the CNOT gate on the density matrix in the computational basis.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

The density matrix can be written

$$\begin{aligned}
\rho = \begin{bmatrix} p_{11} & p_{12} & p_{13} & p_{14} \\\ p_{21} & p_{22} & p_{23} & p_{24} \\\ p_{31} & p_{32} & p_{33} & p_{34} \\\p_{41} & p_{42} & p_{43} & p_{44} \end{bmatrix} 
\end{aligned}$$


Therefore the impact to the density matrix is $\rho \rightarrow CNOT \rho CNOT^\dagger$, as shown below

$$\begin{aligned}
CNOT \rho CNOT^\dagger &= \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix}\begin{bmatrix} p_{11} & p_{12} & p_{13} & p_{14} \\\ p_{21} & p_{22} & p_{23} & p_{24} \\\ p_{31} & p_{32} & p_{33} & p_{34} \\\p_{41} & p_{42} & p_{43} & p_{44} \end{bmatrix}  \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix}^\dagger \\
&= \begin{bmatrix} p_{11} & p_{12} & p_{13} & p_{14} \\\ p_{21} & p_{22} & p_{23} & p_{24} \\\ p_{41} & p_{42} & p_{43} & p_{44} \\\p_{31} & p_{32} & p_{33} & p_{34} \end{bmatrix}  \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix} \\
&= \begin{bmatrix} p_{11} & p_{12} & p_{14} & p_{13} \\\ p_{21} & p_{22} & p_{24} & p_{23} \\\ p_{41} & p_{42} & p_{44} & p_{43} \\\p_{31} & p_{32} & p_{34} & p_{33} \end{bmatrix} 
\end{aligned}$$

</details>


**Exercise 4.20**

We are asked to show that $(H \otimes H)CNOT_{12}(H\otimes H)$ is equivalent to $CNOT_{21}$ and then use that identity to show that the effect of a CNOT with the first qubit as the control and the second qubit as the target is as shown in the book.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.21**

We are asked to verify that figure 4.8 implements the $C^2(U)$ operation. I did this by expressing all the gates in their matrix representation and multiplying together the ones on the right-hand side of the circuit inequality to get the effect of the combined circuit. Then I pointed out that this is equal to the matrix representation of the circuit on the left-hand side of the circuit inequality. Since each gate requires an 8x8 matrix, this was a lot of matrix multiplication.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.22**

For this exercise we are asked to prove that a $C^2(U)$ gate for any single qubit unitary $U$ can be constructed using at most eight one-qubit gates and six controlled-NOTs. I found comparing the circuit that I was creating to the Toffoli gate on Wikipedia and rereading section 4.3 with this exercise in mind helpful when working on this exercise. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.23**

Construct a $C^1(U)$ gate for $U=R_x(\theta)$ and $U=R_y(\theta)$ using only CNOT and single qubit gates. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.24**

Verify that figure 4.9 implements the Toffoli gate.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.25**

For this exercise we are to construct a Fredkin gate.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

(1) This first part we are to construct a Fredkin gate with three Toffoli gates. This is something we already did in exercise 3.32. I changed the following one up a little so that the a wire is the control wire to match the matrix shown later in this exercise.

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

</details>



**Exercise 4.26**

In this exercise we are asked to show that a given circuit differs from a Toffoli gate only by a relative phase. The drawing of the circuit has several $R_y(\theta)$ single bit operations, but it is a little unclear (at least in my book) what $\theta$ is supposed to be, as it is written as $\pi/$. Through some trial and error, I think it is supposed to be $\frac{\pi}{4}$. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.27**

Using just CNOTs and Toffoli gates, construct a quantum circuit to perform the transformation in equation 4.31. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.28**

For this exercise we are to construct a $C^5(U)$ gate analogous to that in Figure 4.10 but using no work qubits. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

From exercise 4.21 we know that we can construct a $C^2(U)$ gate as shown below

<img width="749" height="181" alt="image" src="https://github.com/user-attachments/assets/33962739-1a7f-4c15-874f-a08f56c14250" />

Using a $C^1(V)$ gate, $C^1(V^\dagger)$ gate, $C^2(V)$ gate, and Toffoli gates we can construct a $C^3(U)$ gate as shown below

<img width="752" height="240" alt="image" src="https://github.com/user-attachments/assets/7bda8e0b-6120-4be3-a85b-767f794f2598" />

Similarly, we can create $C^4(U)$ gates 

<img width="777" height="290" alt="image" src="https://github.com/user-attachments/assets/0f73294e-93f3-4469-a4b1-916c278884be" />

and $C^5(U)$ gates

<img width="774" height="364" alt="image" src="https://github.com/user-attachments/assets/f8ea8ba9-671e-4c42-a029-43c0d15bea05" />

</details>


**Exercise 4.29 & 4.30**

Find a circuit containing $O(n^2)$ Toffoli, CNOT and single qubit gates which implements a $C^n(X)$ gate for $n>3$ using no work qubits. Then the next exercise asks us to find a circuit containing $O(n^2)$ gates which implements a $C^n(U)$ gate for $n>3$ using no work qubits. Since these exercises are closely related, I've combined them here. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

From the previous exercise we know that

<img width="794" height="372" alt="image" src="https://github.com/user-attachments/assets/62b8103c-b167-4703-9ebd-fc715846d4a8" />

Following a similar calculation as was done in exercise 4.22, where $V=e^{i\alpha}AXBXC$ and $D$ is the phase gate. 

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

Thinking back to exercise 4.26, we know that we can approximate a controlled X gate up to a relative phase by using the following circuit,

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

</details>


**Exercise 4.31**

In this exercise we are asked to prove sever circuit identities.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


## Measurement

### Measurement - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Principle of deferred measurement    | 4.4                       | Measurements can always be moved from an intermediate stage of a quantum circuit to the end of the circuit; if the measurement results are used at any stage of the circuit then the classically controlled operation can be replaced by conditional quantum operations. |
| Principle of implicit measurement    | 4.4                       | Without loss of generality, any unterminated quantum wires (qubits which are not measured) and the end of a quantum circuit may be assumed to be measured. |
| Reversible measurement               | 4.4                       | In order for a measurement to be reversible, it must reveal no information about the quantum state being measured. |





### Measurement - Exercises

**Exercise 4.32**

For this exercise we are to perform a projective measurement on the second qubit of a two qubit system, find the density matrix after the measurement, and show that the reduced density matrix for the first qubit is not affected by the measurement.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.33**

For this exercise we are asked to show that a given circuit performs a measurement in the basis of the Bell states.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.34**

We are asked to show that the given circuit implements a measurement of $U$.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 4.35**

For this exercise we are asked to show that measurements commute with quantum gates when the qubit being measured is a control qubit.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

In the exercise we are given three circuits that have a controlled $U$ gate such that $C_{U} = \ket{0}\bra{0} \otimes I + \ket{1}\bra{1} \otimes U$. Let's say that the state of the system before the circuit is $\ket{\psi} = \alpha \ket{0}\ket{\psi_{b}} + \beta\ket{1}\ket{\psi_{b}}$

First let's consider the case when the control qubit is measured after the quantum gate (the leftmost circuit). For this case $C_{U}$ is applied first which puts the system in the state

$$\begin{aligned}
C_{U}\ket{\psi} &= \left(\ket{0}\bra{0} \otimes I + \ket{1}\bra{1} \otimes U \right) \left(\alpha \ket{0}\ket{\psi_{b}} + \beta\ket{1}\ket{\psi_{b}}\right)\\
&= \alpha \ket{0} \otimes \ket{\psi_{b}} + \beta \ket{1} \otimes U\ket{\psi_{b}}
\end{aligned}$$

Then when the control wire is measured there is a $\vert \alpha \vert^2$ probability of obtaining the result $\ket{0}$ putting the system in the state $\ket{0} \otimes \ket{\psi_{b}}$ and a $\vert \beta \vert^2$ probability of obtaining the result $\ket{1}$ putting the system in the state $\ket{1} \otimes U\ket{\psi_{b}}$.

Now let's consider the case when the control qubit is measured before the quantum gate (the middle circuit). For this case first the control qubit is measured, where there is a $\vert \alpha \vert^2$ probability of measuring $\ket{0}$ and a $\vert \beta \vert^2$ probability of measuring $\ket{1}$, putting the control wires in the measured state. Then $C_U$ is applied, resulting in the system being in state $\ket{0} \otimes \ket{\psi_{b}}$ or $\ket{1} \otimes U\ket{\psi_{b}}$, depending on what the control qubit measurement was. 

Both circuits have the same probability of obtaining one of the two same outputs and therefore are equivalent.

</details>



## Universal quantum gates

### Universal quantum gates - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Universal quantum gate requirements  | 4.5                       | A set of gates is said to be universal for quantum computation if any unitary operation may be approximated to arbitrary accuracy by a quantum circuit involving only those gates. |
| Universal quantum computation gate set | 4.5                     | Hadamard, phase, CNOT, and $\pi/8$ gates. Though, the phase gate can be constructed with two $\pi/8$ gates. |
| Two-level unitary gates are universal | 4.5.1                    | If we find two-level unitary matrices $U_1, \cdots, U_{k}$ such that $U_{k} \cdots U_1 U = I$ then $U = U_1^\dagger \cdots U_{k}^\dagger$, where $U$ is a $d \times d$ matrix and $k\leq (d-1) + (d-2) + \cdots + 1 = \frac{d(d-1)}{2}$.  |





### Universal quantum gates - Exercises


**Exercise 4.36**

Construct a quantum circuit to add two two-bit numbers $x$ and $y$ modulo 4. 

<details style="margin-bottom: 20px;" markdown="1">

This circuit will perform the transformation $\ket{x,y} \rightarrow \ket{x, x+y \mod 4}$. Since $x$ and $y$ are two bit numbers each number will be written in the following convention $x=x_2 x_1$, where $x_1$ and $x_2$ are digits in the number $x$. Therefor the transformation can be written as

$$\begin{aligned}
\ket{x_1, x_2,y_1, y_2} &\rightarrow \ket{x_1, x_2, (x+y \mod 4)_1, (x+y \mod 4)_2} \\
&= \ket{x_1, x_2, x_1 \oplus y_1, x_2 \oplus y_2 \oplus (x_1 \land y_1)}
\end{aligned}$$

The following circuit performs this transformation

<img width="564" height="231" alt="image" src="https://github.com/user-attachments/assets/dc5a1bd0-af92-4e1a-a5a1-159cd8046896" />

</details>


**Exercise 4.37**

Provide a decomposition of the transform given in equation 4.52. 

Since $U$ is a $4 \times 4$ matrix, we'll need to find $U_1, U_2, U_3, U_4$ such that $U_4 U_3 U_2 U_1 = I$ using the a procedure similar to the one outlined in equations 4.44 - 4.50. 

From equation 4.54

$$\begin{aligned}
U = \begin{bmatrix} 1 & 1 & 1 & 1 \\\ 1 & i & -1 & -i \\\ 1 & -1 & 1 & -1 \\\ 1 & -i & -1 & i \end{bmatrix}
\end{aligned}$$

Then let's set 

$$\begin{aligned}
U_1 = \begin{bmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} & 0 & 0 \\\ \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 1 \end{bmatrix}
\end{aligned}$$

Which gives

$$\begin{aligned}
U_1 U &= \begin{bmatrix} \sqrt{2} & \frac{\sqrt{2}(1+i)}{2} & 0 & \frac{\sqrt{2}(1-i)}{2} \\\ 0 & \frac{\sqrt{2}(1-i)}{2} & \sqrt{2} & \frac{\sqrt{2}(1+i)}{2} \\\ 1 & -1 & 1 & -1 \\\ 1 & -i & -1 & i \end{bmatrix} 
\end{aligned}$$

Now let's set 

$$\begin{aligned}
U_2 = U_1 = \begin{bmatrix} \frac{\sqrt{2}}{\sqrt{3}} & 0 & \frac{1}{\sqrt{3}} & 0 \\\ 0 & 1 & 0 & 0 \\\ \frac{1}{\sqrt{3}} & 0 & -\frac{\sqrt{2}}{\sqrt{3}} & 0 \\\ 0 & 0 & 0 & 1 \end{bmatrix}
\end{aligned}$$

Which gives

$$\begin{aligned}
U_2 U_1 U &= \begin{bmatrix} \sqrt{3} & \frac{\sqrt{3}i}{3} & \frac{\sqrt{3}}{3} & -\frac{\sqrt{3}i}{3} \\\ 0 & \frac{\sqrt{2}(1-i)}{2} & \sqrt{2} & \frac{\sqrt{2}(1+i)}{2} \\\ 0 & \frac{\sqrt{6}(3 + i)}{6} & -\frac{\sqrt{6}}{3} & \frac{\sqrt{6}(3 - i)}{6} \\\ 1 & -i & -1 & i \end{bmatrix} 
\end{aligned}$$

Now let's set

$$\begin{aligned}
U_3 = \begin{bmatrix} \frac{\sqrt{3}}{2} & 0 & 0 & \frac{1}{2} \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ \frac{1}{2} & 0 & 0 & -\frac{\sqrt{3}}{2} \end{bmatrix}
\end{aligned}$$

Which gives

$$\begin{aligned}
U_3 U_2 U_1 U &= \begin{bmatrix} 2 & 0 & 0 & 0 \\\ 0 & \frac{\sqrt{2}(1-i)}{2} & \sqrt{2} & \frac{\sqrt{2}(1+i)}{2} \\\ 0 & \frac{\sqrt{6}(3 + i)}{6} & -\frac{\sqrt{6}}{3} & \frac{\sqrt{6}(3 - i)}{6} \\\ 0 & \frac{2\sqrt{3}i}{3} & \frac{2\sqrt{3}}{3} & -\frac{2\sqrt{3} i}{3} \end{bmatrix} 
\end{aligned}$$

Now let's set

$$\begin{aligned}
U_4 = \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & \frac{3\sqrt{2}(1+i)}{4\sqrt{6}} & \frac{3 - i}{4} & 0 \\\ 0 & \frac{3 + i}{4} & -\frac{3\sqrt{2}(1-i)}{4\sqrt{6}} & 0 \\\ 0 & 0 & 0 & 1 \end{bmatrix}
\end{aligned}$$

Which gives

$$\begin{aligned}
U_4 U_3 U_2 U_1 U &= \begin{bmatrix} 2 & 0 & 0 & 0 \\\ 0 & \frac{2 \sqrt{6}}{3} & \frac{\sqrt{6} i}{3} & \frac{\sqrt{6}}{3} \\\ 0 & 0 & \sqrt{2} & \sqrt{2} i \\\ 0 & \frac{2\sqrt{3}i}{3} & \frac{2\sqrt{3}}{3} & -\frac{2\sqrt{3} i}{3} \end{bmatrix} 
\end{aligned}$$

Now let's set

$$\begin{aligned}
U_5 = \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 1 \end{bmatrix}
\end{aligned}$$






