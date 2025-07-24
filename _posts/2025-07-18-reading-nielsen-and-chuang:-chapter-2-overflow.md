# Reading Nielsen and Chuang: Chapter 2 Overflow

## The Schmidt decomposition and purifications

### The Schmidt decomposition and purifications - Key Concepts

| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Schmidt decomposition                | section 2.5               | If $\ket{\psi}$ is a pure state of a composite system $AB$ then there exists orthonormal states $\ket{i_A}$ and $\ket{i_B}$ such that $\ket{\psi} = \sum_i \lambda_i \ket{i_A}\ket{i_B}$ where $\lambda_i$ are non-negative real numbers satisfying $\sum_i \lambda_i^2 = 1$ |
| Reduced density matrix of a Schmidt decomposition | section 2.5  | $\rho^A = \sum_i \lambda_i^2 \ket{i_A}\bra{i_A}$ and $\rho^B = \sum_i \lambda_i^2 \ket{i_B}\bra{i_B}$, where $\lambda_i$ are identical for both reduced density operators. |

### The Schmidt decomposition and purifications - Exercises

**Exercise 2.76**

In this exercise we extend the Schmidt decomposition proof to include $A$ and $B$ with different dimensionality. It is useful to look up singular value decomposition for non-square matrices to complete this exercise. 

<details>
<summary>Solution</summary>

For the case where systems $A$ has dimensions $m$ and $B$ has dimensions $n$ and $m \geq n$, let $\ket{j}$ and $\ket{k}$ be any fixed orthonormal bases for systems $A$ and $B$, respectively. Then $\ket{\psi}$ can be written as

$$\begin{aligned}
\ket{\psi} = \sum_{jk} a_{jk}\ket{j}\ket{k}
\end{aligned}$$

for some matrix $a$ of complex number $a_{jk}$. By the singular value decomposition, $a = u c v$, where $c$ is a $m \times n$ matrix defined by

$$\begin{aligned}
c = \begin{bmatrix} d \\\ 0 \end{bmatrix}
\end{aligned}$$

with $d$ as a $n \times n$ diagonal matrix with non-negative elements, $u$ is a unitary $m \times m$ matrix given by

$$\begin{aligned}
u = \begin{bmatrix} u' \\\ u'' \end{bmatrix}
\end{aligned}$$

 $u'$ is a $m \times n$ matrix, and $v$ is a unitary $n \times n$ matrix. Thus

$$\begin{aligned}
\ket{\psi} = \sum_{ijk} u_{ji}' d_{ii} v_{ik} \ket{j}\ket{k} 
\end{aligned}$$

Defining $\ket{i_A} = \sum_j u_{ji}'\ket{j}$, $\ket{i_B}=\sum_k v_{ik} \ket{k}$, and $\lambda_i = d_{ii}$ we get

$$\begin{aligned}
\ket{\psi} = \sum_{i=1}^n \lambda_i \ket{i_A}\ket{i_B}
\end{aligned}$$

A similar calculation can be done for $m \leq n$ with the results

$$\begin{aligned}
\ket{\psi} = \sum_{i=1}^m \lambda_i \ket{i_A}\ket{i_B}
\end{aligned}$$

Therefore,

$$\begin{aligned}
\ket{\psi} = \sum_{i=1}^{\min(m,n)} \lambda_i \ket{i_A}\ket{i_B}
\end{aligned}$$

</details>


**Exercise 2.77**

In this exercise we are to show that Schmidt decomposition would not always work for a three component quantum system. 

Let $\ket{j}$, $\ket{k}$, and $\ket{l}$ be fixed orthonormal basis for systems $A$, $B$, and $C$ with an arbitrary three component quantum state given by $\ket{\psi} = \sum_{jkl} a_{jkl} \ket{j}\ket{k}\ket{l}$. 

I'm going to add $\ket{0}$ to a Bell state to see if this example is one that can't be written as 2.206. This is mostly just an educated guess after reading section 2.5 and thinking about what the respective decompositions may be for the different systems. Therefore, 

$$\begin{aligned}
\ket{\psi} = \frac{\ket{0}\ket{0}\ket{0} + \ket{1}\ket{1}\ket{0}}{\sqrt{2}}
\end{aligned}$$

We can write the density operator for this system as 

$$\begin{aligned}
\rho &= \ket{\psi}\bra{\psi} \\
&= \left( \frac{\ket{0}\ket{0}\ket{0} + \ket{1}\ket{1}\ket{0}}{\sqrt{2}} \right) \left( \frac{\bra{0}\bra{0}\bra{0} + \bra{1}\bra{1}\bra{0}}{\sqrt{2}} \right) \\
&= \frac{\ket{0}\ket{0}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{0}\ket{0}\ket{0}\bra{1}\bra{1}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{1}\bra{1}\bra{0}}{2}
\end{aligned}$$

We know we that we can extract the reduced density operator for a system from a composite system density operator using equation 2.177 and so

$$\begin{aligned}
\rho^A &= \text{tr}_B(\text{tr}_C(\rho^{ABC}))\\
&= \text{tr}_B(\text{tr}_C(\frac{\ket{0}\ket{0}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{0}\ket{0}\ket{0}\bra{1}\bra{1}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{1}\bra{1}\bra{0}}{2}))\\
&= \text{tr}_B(\frac{\ket{0}\ket{0}\bra{0}\bra{0} \braket{0 \vert 0}+ \ket{0}\ket{0}\bra{1}\bra{1}\braket{0 \vert 0} + \ket{1}\ket{1}\bra{0}\bra{0}\braket{0 \vert 0} + \ket{1}\ket{1}\bra{1}\bra{1}\braket{0 \vert 0}}{2}) \\
&= \text{tr}_B(\frac{\ket{0}\ket{0}\bra{0}\bra{0}+ \ket{0}\ket{0}\bra{1}\bra{1} + \ket{1}\ket{1}\bra{0}\bra{0} + \ket{1}\ket{1}\bra{1}\bra{1}}{2}) \\
&= \frac{\ket{0}\bra{0}\braket{0 \vert 0} + \ket{0}\bra{1}\braket{1 \vert 0} + \ket{1}\bra{0}\braket{0 \vert 1} + \ket{1}\bra{1}\braket{1 \vert 1}}{2} \\
&= \frac{\ket{0}\bra{0} + \ket{1}\bra{1}}{2} \\
\end{aligned}$$

$$\begin{aligned}
\rho^B &= \text{tr}_A(\text{tr}_C(\rho^{ABC}))\\
&= \text{tr}_A(\text{tr}_C(\frac{\ket{0}\ket{0}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{0}\ket{0}\ket{0}\bra{1}\bra{1}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{1}\bra{1}\bra{0}}{2}))\\
&= \text{tr}_A(\frac{\ket{0}\ket{0}\bra{0}\bra{0} \braket{0 \vert 0}+ \ket{0}\ket{0}\bra{1}\bra{1}\braket{0 \vert 0} + \ket{1}\ket{1}\bra{0}\bra{0}\braket{0 \vert 0} + \ket{1}\ket{1}\bra{1}\bra{1}\braket{0 \vert 0}}{2}) \\
&= \text{tr}_A(\frac{\ket{0}\ket{0}\bra{0}\bra{0}+ \ket{0}\ket{0}\bra{1}\bra{1} + \ket{1}\ket{1}\bra{0}\bra{0} + \ket{1}\ket{1}\bra{1}\bra{1}}{2}) \\
&= \frac{\ket{0}\bra{0}\braket{0 \vert 0} + \ket{0}\bra{1}\braket{1 \vert 0} + \ket{1}\bra{0}\braket{0 \vert 1} + \ket{1}\bra{1}\braket{1 \vert 1}}{2} \\
&= \frac{\ket{0}\bra{0} + \ket{1}\bra{1}}{2} \\
\end{aligned}$$

$$\begin{aligned}
\rho^C &= \text{tr}_B(\text{tr}_A(\rho^{ABC}))\\
&= \text{tr}_B(\text{tr}_A(\frac{\ket{0}\ket{0}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{0}\ket{0}\ket{0}\bra{1}\bra{1}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{1}\bra{1}\bra{0}}{2}))\\
&= \text{tr}_B(\frac{\ket{0}\ket{0}\bra{0}\bra{0}\braket{0 \vert 0} + \ket{0}\ket{0}\bra{1}\bra{0} \braket{1 \vert 0}  + \ket{1}\ket{0}\bra{0}\bra{0}\braket{0 \vert 1}  + \ket{1}\ket{0}\bra{1}\bra{0}\braket{1 \vert 1} }{2})\\
&= \text{tr}_B(\frac{\ket{0}\ket{0}\bra{0}\bra{0} + \ket{1}\ket{0}\bra{1}\bra{0}}{2})\\
&= \frac{\ket{0}\bra{0}\braket{0 \vert 0} + \ket{0}\bra{0}\braket{1 \vert 1}}{2}\\
&= \ket{0}\bra{0} \\
\end{aligned}$$

By Schmidt decomposition we should be able to write $\rho^A = \sum_i \lambda_i^2 \ket{i_A}\bra{i_A}$, $\rho^B = \sum_i \lambda_i^2 \ket{i_B}\bra{i_B}$, and $\rho^C = \sum_i \lambda_i^2 \ket{i_C}\bra{i_C}$ for some values of $\lambda_i^2$. 



## EPR and the Bell Inequality

### EPR and the Bell Inequality - Key Concepts

| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|


## Chapter Problems
