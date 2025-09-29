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
| Product representation of quantum Fourier transform | 5.1        | Write state $\ket{j}$ using the binary representation $j = j_12^{n-1} + j_22^{n-2} + \cdots + j_n2^0$. With the binary fraction represented as $0.j_lj_{l+1}\cdots j_m = j_l/2+j_{l+1}/4 + \cdots + j_m/2^{m-l+1}$. Then the Fourier transform can be written as <br> $\ket{j_1,\cdots,j_n} \to \frac{\left(\ket{0} + e^{2\pi i  0.j_n }\right)\left(\ket{0} + e^{2\pi i  0.j_{n-1}j_n }\right)\cdots \left(\ket{0} + e^{2\pi i  0.j_1j_2\cdots j_n }\right)}{2^{n/2}}$ |

  
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











