# Reading Nielsen and Chuang: Chapter 2 Overflow

## The Schmidt decomposition and purifications

### The Schmidt decomposition and purifications - Key Concepts

| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Schmidt decomposition                | section 2.5               | If $\ket{\psi}$ is a pure state of a composite system $AB$ then there exists orthonormal states $\ket{i_A}$ and $\ket{i_B}$ such that $\ket{\psi} = \sum_i \lambda_i \ket{i_A}\ket{i_B}$ where $\lambda_i$ are non-negative real numbers satisfying $\sum_i \lambda_i^2 = 1$ |
| Reduced density matrix of a Schmidt decomposition | section 2.5  | $\rho^A = \sum_i \lambda_i^2 \ket{i_A}\bra{i_A}$ and $\rho^B = \sum_i \lambda_i^2 \ket{i_B}\bra{i_B}$, where $\lambda_i$ are identical for both reduced density operators. |
| Purification                         | section 2.5               | Given a state $\rho^A$ of a quantum system $A$, it is possible to introduce a reference system $R$ (that does not have physical significance) to define a pure state $\ket{AR}$ for the joint system $AR$ such that $\rho^A = \text{tr}_R (\ket{AR}\bra{AR})$ where $\ket{AR} = \sum_i \sqrt{p_i}\ket{i^A}{i^R}$ for orthonormal basis states $\ket{i^A}$ and $\ket{i^R}$ |

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

In this exercise we are to show that Schmidt decomposition would not always work for a three component quantum system. This is done by picking a state which it doesn't work for and then demonstrating that the different reduced density matrices for the different components have different Schmidt coefficients. 

<details>
<summary>Solution</summary>

Let $\ket{j}$, $\ket{k}$, and $\ket{l}$ be fixed orthonormal basis for systems $A$, $B$, and $C$ with an arbitrary three component quantum state given by $\ket{\psi} = \sum_{jkl} a_{jkl} \ket{j}\ket{k}\ket{l}$. 

I'm going to add $\ket{0}$ to a Bell state to see if this example is one that can't be written as 2.206. This is mostly just an educated guess after reading section 2.4.3 and section 2.5 and thinking about what the reduced density matrices will likely be for the different systems. Therefore, 

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

By Schmidt decomposition we should be able to write $\rho^A = \sum_i \lambda_i^2 \ket{i_A}\bra{i_A}$, $\rho^B = \sum_i \lambda_i^2 \ket{i_B}\bra{i_B}$, and $\rho^C = \sum_i \lambda_i^2 \ket{i_C}\bra{i_C}$ for some values of $\lambda_i^2$. For $\rho^A$ and $\rho^B$ there are two Schmidt coefficients that are both $\lambda_i^2 = \frac{1}{2}$. For $\rho^C$ the Schmidt coefficients are $\lambda_1^2 = 1$ and $\lambda_2^2 = 0$. Since these are not the same for all three components, we are unable to write the quantum states in the form given by equation 2.206.

</details>


**Exercise 2.78**

Product states are multi-qubit states that can be represented as simple combinations of individual qubit states - i.e. the qubits are not entangled. In this exercise we are to prove that a state of a composite system is a product state only if it has a Schmidt number of 1 and its reduced density matrices are pure states. I was unsure how much detail the authors wanted for this solution, so I erred on the side of more rather than less. I started with a composite of two arbitrary single qubit pure states and then followed similar steps shown in the proof for Schmidt decomposition. That may have been more work than what was needed since, if you just compare equation 2.202 to state $\ket{\psi} = \ket{a}\ket{b}$ for pure states $\ket{a}$ and $\ket{b}$, the answer seems obvious. 

<details>
<summary>Solution</summary>

For a composite system made from two single qubits with pure state unit vectors given by $\ket{a}$ and $\ket{b}$, $\ket{\psi}$ can be written as

$$\begin{aligned}
& \ket{a} &= a_0 \ket{0} + a_1 \ket{1} \\
& \ket{b} &= b_0 \ket{0} + b_1 \ket{1} \\
 \Rightarrow & \ket{\psi} &= \ket{a}\ket{b} \\
& &= \left(a_0 \ket{0} + a_1 \ket{1} \right) \left(b_0 \ket{0} + b_1 \ket{1}\right) \\
& &= a_0 b_0 \ket{0} \ket{0} + a_1 b_0 \ket{1} \ket{0} + a_0 b_1 \ket{0} \ket{1} + a_1 b_1 \ket{1} \ket{1} \\
& &= \sum_{jk} a_{jk}\ket{j}\ket{k}
\end{aligned}$$

Then matrix $a$ is 

$$\begin{aligned}
a = \begin{bmatrix} a_0b_0 & a_0b_1 \\\ a_1b_0 & a_1b_1 \end{bmatrix}
\end{aligned}$$


Performing singular value decomposition, we get

$$\begin{aligned}
\begin{bmatrix} a_0b_0 & a_0b_1 \\\ a_1b_0 & a_1b_1 \end{bmatrix} &= \begin{bmatrix} u_{11} & u_{12} \\\ u_{21} & u_{22} \end{bmatrix} \begin{bmatrix} \lambda_1 & 0 \\\ 0 & \lambda_2 \end{bmatrix} \begin{bmatrix} v_{11} & v_{12} \\\ v_{21} & v_{22} \end{bmatrix} \\
&= \begin{bmatrix} a_0 & a_1 \\\ a_1 & -a_0 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 0 & 0 \end{bmatrix} \begin{bmatrix} b_0 & b_1 \\\ b_1 & -b_0 \end{bmatrix} \\
\end{aligned}$$

Therefore the Schmidt number is $1$, since there is only one non-zero $\lambda$ and the orthonormal states are 

$$\begin{aligned}
\ket{1_A} = \sum_j u_{j1}\ket{j} = a_0\ket{0} + a_1\ket{1} = \ket{a}\\
\ket{1_B} = \sum_k v_{1k}\ket{k} = b_0\ket{0} + b_1\ket{1} = \ket{b}
\end{aligned}$$

These are just the individual pure states that we started with. 

The the reduced density matrices are 

$$\begin{aligned}
\rho^A = \ket{a}\bra{a}\\
\rho^B = \ket{b}\bra{b}
\end{aligned}$$

You can further confirm that these are pure states by checking that $\text{tr}((\rho^A)^2) = \text{tr}((\rho^B)^2) = 1$, which I'll show below for $\rho^A$

$$\begin{aligned}
\text{tr}((\rho^A)^2) &= \text{tr}(\ket{a}\braket{a \vert a}\bra{a})\\
&= \text{tr}(\ket{a}\bra{a}) \\
&= \braket{a \vert a} \\
&= 1
\end{aligned}$$

Looking back at the singular value decomposition we can think about what things would look like if $\lambda_2$ was not $0$. The Schmidt number would then be $2$ and the Schmidt bases would be

$$\begin{aligned}
\ket{1_A} = \sum_j u_{j1}\ket{j} = a_0\ket{0} + a_1\ket{1}  \\
\ket{2_A} = \sum_j u_{j2}\ket{j} = a_1\ket{0} - a_0\ket{1} \\
\ket{1_B} = \sum_k v_{1k}\ket{k} = b_0\ket{0} + b_1\ket{1} \\
\ket{2_B} = \sum_k v_{2k}\ket{k} = b_1\ket{0} - b_0\ket{1}
\end{aligned}$$

The reduced density matrices now look like

$$\begin{aligned}
\rho^A = \lambda_1^2\ket{1_A}\bra{1_A} + \lambda_2^2\ket{2_A}\bra{2_A}\\
\rho^B = \lambda_1^2\ket{1_B}\bra{1_B} + \lambda_2^2\ket{2_B}\bra{2_B}\\
\end{aligned}$$

These are not pure states, which we can confirm this by showing $\text{tr}((\rho^A)^2) = \text{tr}((\rho^B)^2) < 1$

$$\begin{aligned}
\text{tr}((\rho^A)^2) &= \text{tr}(\lambda_1^4\ket{1_A}\braket{1_A \vert 1_A}\bra{1_A} + \lambda_1^2\lambda_2^2\ket{1_A}\braket{1_A \vert 2_A}\bra{2_A} + \lambda_1^2\lambda_2^2\ket{2_A}\braket{2_A \vert 1_A}\bra{1_A} + \lambda_2^4\ket{2_A}\braket{2_A \vert 2_A}\bra{2_A})\\
&= \text{tr}(\lambda_1^4\ket{1_A}\bra{1_A} + \lambda_2^4\ket{2_A}\bra{2_A}) \\
&= \lambda_1^4\braket{1_A \vert 1_A} + \lambda_2^4\braket{2_A \vert 2_A} \\
&= \lambda_1^4 + \lambda_2^4 < 1
\end{aligned}$$

The composite state made by these orthonormal states look like this

$$\begin{aligned}
\ket{\psi} &= \sum_i \lambda_i \ket{i_A}\ket{i_B} \\
&= \lambda_1\ket{1_A}\ket{1_B} + \lambda_2\ket{2_A}\ket{2_B} 
\end{aligned}$$

which is not a product state. 

</details>

**Exercise 2.79**

In this exercise we are to find the Schmidt decomposition of three given states.

Let's look at the first given state

$$\begin{aligned}
\ket{\psi} &= \frac{\ket{00} + \ket{11}}{\sqrt{2}} \\
\end{aligned}$$

This state is already written as a Schmidt decomposition with $\lambda_1 = \lambda_2 = \frac{1}{\sqrt{2}}$, $\ket{1_A} = \ket{0}$, $\ket{2_A} = \ket{1}$, $\ket{1_B} = \ket{0}$, and $\ket{2_B} = \ket{1}$.


Moving on to the second state

$$\begin{aligned}
\ket{\psi} &= \frac{\ket{00} + \ket{01} + \ket{10} + \ket{11}}{2} \\
\end{aligned}$$

Now let's calculate the density matrix

$$\begin{aligned}
\rho &= \left( \frac{\ket{00} + \ket{01} + \ket{10} + \ket{11}}{2} \right) \left( \frac{\bra{00} + \bra{01} + \bra{10} + \bra{11}}{2} \right) \\
&= \frac{\ket{00} + \ket{01} + \ket{10} + \ket{11}}{4} \right) \left( \frac{\bra{00} + \bra{01} + \bra{10} + \bra{11}}{2} \right)
\end{aligned}$$


Finally, we'll look at the third state

$$\begin{aligned}
\ket{\psi} &= \frac{\ket{00} + \ket{01} + \ket{10}}{\sqrt{3}} \\
\end{aligned}$$





## EPR and the Bell Inequality

### EPR and the Bell Inequality - Key Concepts

| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|


## Chapter Problems
