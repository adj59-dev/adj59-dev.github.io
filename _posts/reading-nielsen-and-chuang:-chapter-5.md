# Reading Nielsen and Chuang: Chapter 5

I just finished reading Chapter 5 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. 


## Navigation

* [The quantum Fourier transform](#the-quantum-fourier-transform)
* [Phase estimation](#phase-estimation)
* [Order-finding and factoring applications](#order-finding-and-factoring-applications)
* [General applications of the quantum Fourier transform](#general-applications-of-the-quantum-fourier-transform)




## The quantum Fourier transform

### The quantum Fourier transform - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Quantum Fourier transform            | 5.1                       | Fourier transform on an orthonormal basis $\ket{0},\cdots,\ket{N-1}$ is <br> $\ket{j} \to \frac{1}{\sqrt{N}}\sum_{k=0}^{N-1}e^{2\pi i j k/N}\ket{k}$. <br> The action on an arbitrary state is <br> $\sum_{j=0}^{N-1} x_j \ket{j} \to \sum_{k=0}^{N-1} y_k \ket{k}$ |
| Product representation of quantum Fourier transform | 5.1        | Write state $\ket{j}$ using the binary representation $j = j_12^{n-1} + j_22^{n-2} + \cdots + j_n2^0$. With the binary fraction represented as $0.j_lj_{l+1}\cdots j_m = j_l/2+j_{l+1}/4 + \cdots + j_m/2^{m-l+1}$. Then the Fourier transform can be written as <br> $\ket{j_1,\cdots,j_n} \to \frac{\left(\ket{0} + e^{2\pi i  0.j_n }\ket{1}\right)\left(\ket{0} + e^{2\pi i  0.j_{n-1}j_n }\ket{1}\right)\cdots \left(\ket{0} + e^{2\pi i  0.j_1j_2\cdots j_n }\ket{1}\right)}{2^{n/2}}$ |
| Quantum Fourier transform limitations | 5.1                      | We cannot directly access the amplitudes in a quantum computer, therefore there is no way of determining the Fourier transformed amplitudes of the original state. There is also no way to efficiently prepare the original state to be Fourier transformed. |

  
### The quantum Fourier transform - Exercises

**Exercise 5.1**

Give a direct proof that the linear transformation defined by equation 5.2 is unitary. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


**Exercise 5.2**

Explicitly compute the Fourier transform of the $n$ qubit state $\ket{00\cdots 0}$. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

For the equations below, $N=2^n$.

$$\begin{aligned}
T\ket{00\cdots 0} &= \frac{1}{\sqrt{N}}\sum_{k=0}^{N-1}\sum_{j=0}^{N-1}e^{2\pi i j k/N}\ket{k}\braket{j \vert 00\cdots 0} \\
&= \frac{1}{\sqrt{N}}\sum_{k=0}^{N-1}\sum_{j=0}^{N-1}e^{2\pi i j k/N} \delta_{j,0}\ket{k} \\
&= \frac{1}{\sqrt{N}}\sum_{k=0}^{N-1}\ket{k}
\end{aligned}$$

</details>


**Exercise 5.3**

Suppose we wish to perform a Fourier transform of a vector containing $2^n$ complex numbers on a classical computer. Verify that the straightforward method for performing the Fourier transform, based upon direct evaluation of Equation (5.1) requires $\Theta(2^{2n})$ elementary arithmetic operations. Find a method for reducing this to $\Theta(n2^n)$ based upon Equation (5.4).

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

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

</details>


