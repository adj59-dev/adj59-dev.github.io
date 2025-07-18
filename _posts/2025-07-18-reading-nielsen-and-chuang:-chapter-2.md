# Reading Nielsen and Chuang: Chapter 2

I've completed reading chapter 2 of *Quantum Computation and Quantum Informaiton* by Nielsen and Chuang. This chapter provides an introduction to quantum mechanics.

## Linear Algebra

### Linear Algebra - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Qubit notation                       | Nomenclature and notation | $\ket{0} = (1,0)$, $\ket{1} = (0,1)$                                                                   |
| Linear dependence/independence       | section 2.1.1             | A set of non-zero vectors are linearly dependent if there exist $a_1, \dots, a_n$ with $a_ \neq 0$ for at least one $i$ such that $a1 \ket{v_1} + \dots + a_n \ket{v_n} = 0$. The set is linearly independent if it is not linearly dependent. |
| Basis set of vectors                 | section 2.1.1             | A set of linearly independent vectors which span a vector space                                        |
| Matrix representation of an operator | section 2.1.2             | $A \ket{v_j} = \sum_{i} A_{ij} \ket{w_j}$                                                              |
| Definition of a linear operator      | section 2.1.2             | $A \left(\sum_{i} a_i \ket{v_i} \right) = \sum_{i} a_i A \ket{v_i}$                                    |
| Pauli matrices and identity operator | section 2.13              | $I &= \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} & X &= \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix}$ <br> $Y &= \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} & Z &= \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix}$ |
| Inner product                        | section 2.1.4             | Definition: $\braket{v \vert w} = \left( \ket{v}, \ket{w} \right)$ <br> Representation in complex $n$-space: $\mathbb{C}^n$, $\braket{v \vert w} = \sum_i^n v_i^\ast w_i$ <br> Requirements: <br> - linear in the second argument: $\left(\ket{v}, \sum_{i} \lambda_i \ket{w_i}\right) = \sum_{i} \lambda_i (\ket{v}, \ket{w_i})$ <br> - conjugate symmetry: $\left(\ket{v}, \ket{w}\right) = \left(\ket{w}, \ket{v}\right)^\ast$ <br> - positive semi-definiteness: $\left(\ket{v}, \ket{v}\right) \geq 0$ with equality if and only if $\ket{v} = 0$ <br> Vector orthogonality: the inner product of two vectors is zero when they are orthogonal|
| Normalization                        | section 2.1.4             | Vector norm: $\Vert \ket{v} \Vert = \sqrt{\braket{v \vert v}}$ <br> Unit vector: $\ket{v}/\Vert \ket{v} \Vert$ |
| Outer product representation         | section 2.1.4             | $A = \sum_{ij} \braket{w_j \vert A \vert v_i} \ket{w_j} \bra{v_i}$                                     |
| Characteristic function              | section 2.1.5             | Definition: $c(\lambda)= \text{det} \vert A - \lambda I \vert$ <br> Solutions to $c(\lambda)=0$ are the eigenvalues |
| Diagonal representation              | section 2.1.5             | $A = \sum_{i} \lambda_i \ket{i} \bra{i}$, where $\ket{i}$ form an orthonormal set of eigenvectors for $A$ with eigenvalues $\lambda_i$ | 
| Hermitian operator                   | section 2.1.5             | Definition: $H^\dagger = H$                                                                            |
| Adjoint or Hermitian Conjugate       | section 2.1.6             | Definition: $\left(\ket{v}, A \ket{w} \right) = \left(A^\dagger \ket{v}, \ket{w} \right)$ <br> $A^\dagger = (A^\ast)^T$ |
| Projector                            | section 2.1.6             | Definition: $P = \sum_{i=1}^{k} \ket{i}\bra{i}$ <br> Orthogonal complement of P: $Q=I-P$               |
| Normal operator                      | section 2.1.6             | Definition: $A$ is normal if $A^\dagger A = A A^\dagger$ <br> Spectral decomposition: normal matrices can be written as $A = \sum_{i} \lambda_i \ket{i}\bra{i}$, where $\lambda_i$ are the eigenvalues and $\ket{i}$ is a orthonormal basis. |
| Unitary operator                     | section 2.1.6             | Definition: $U^\dagger U = UU^\dagger = I$ <br> Outer product representation: $U= \sum_{i} \ket{w_i}\bra{v_i}$ for orthonormal bases $\ket{v_i}$ and $\ket{w_i}$ |
| Positive operator                    | section 2.1.6             | Definition: for any vector $\ket{v}$, $(\ket{v}, A \ket{v})$ is a real, non-negative number <br> All positive operators are Hermitian |
| Tensor product properties            | section 2.1.7             | For a scalar $z$ and elements $\ket{v}$ of $V$ and $\ket{w}$ of $W$: <br> $z(\ket{v} \otimes \ket{w}) = (z \ket{v} ) \otimes \ket{w} = \ket{v} \otimes (z \ket{w})$ <br> $(\ket{v_1} + \ket{v_2})\otimes\ket{w} = \ket{v_1} \otimes \ket{w} + \ket{v_2} \otimes \ket{w}$ <br> $\ket{v} \otimes (\ket{w_1} + \ket{w_2}) = \ket{v} \otimes \ket{w_1} + \ket{v} \otimes \ket{w_2}$|
| Linear operator $A \otimes B$        | section 2.1.7             | Definition: $(A \otimes B)(\ket{v} \otimes \ket{w})\equiv A \ket{v} + B \ket{w}$                        |
| Inner product on $V \otimes W$       | section 2.1.7             | Definition: $\left( \sum_i a_i \ket{v_i} \otimes \ket{w_w}, \sum_j b_j \ket{v_j'} \otimes \ket{w_j'} \right) \equiv \sum_{ij} a_i^\ast b_j \braket{v_i \vert v_j'}{w_i \vert w_j'}$ | 
| Kronecker product                    | section 2.1.7             |                                                                                                          |
| Tensor power notation                | section 2.1.7             | $\ket{\psi}^{\otimes k}$ means $\ket{\psi}$ tensored with itself $k$ times <br> Example: $\ket{\psi}^{\otimes 3} = \ket{\psi} \otimes \ket{\psi} \otimes \ket{\psi}$ |
| Operator functions                   | section 2.1.8             | For $A=\sum_{a} a \ket{a} \bra{a}$, $f(A) = \sum_{a} f(a) \ket{a} \bra{a}$                               |
| Trace of a matrix                    | section 2.1.8             | Definition: $\text{tr}(A) = \sum_i A_{ii}$ <br> $\text{tr}(AB)=\text{tr}(BA)$ <br> $\text{tr}(A+B)=\text{tr}(A) + \text{tr}(B)$              |
| Hilbert-Schmidt inner productor      | section 2.1.8             | Definition: $(A,B) =\text{tr}(A^\dagger B)$                                                              |
| Commutator                           | section 2.1.9             | Definition: $\[A, B\]=AB-BA$                                                                             |
| Anti-commutator                      | section 2.1.9             | Definition: $\{ A, B \} = AB + BA$                                                                       |
| Polar decomposition                  | section 2.1.10            | $A=UJ=KU$ for a unitary operator $U$ and postitive operators $J=\sqrt{A^\dagger A}$ and $K=\sqrt{A A^\dagger}$ |


### Linear Algebra - Exercises
  
  **Exercise 2.1** 

In section 2.1.1 the authors introduce the concept of linear dependence and independence. In this exercise you use the definition of linear dependence to demonstrate that three vectors are linearly dependent.

<details>
<summary>Solution</summary> 

To show that these vectors are linearly dependent, we need to find a set of $a_1$, $a_2$, and $a_3$ such that

$$a_1 \begin{bmatrix} 1 \\\ -1 \end{bmatrix} + a_2 \begin{bmatrix} 1 \\\ 2 \end{bmatrix} + a_3 \begin{bmatrix} 2  \\\ 1 \end{bmatrix} = 0$$

This is true when $a_1=1, a_2=1,$ and $a_3=-1$. Therefore these vectors are linearly dependent.

</details>

**Exercise 2.2**

In section 2.1.2 the authors talk about how linear operators can be represented as matrices. In this exercise you get practice representing a linear operator as a matrix. The first part of this exercise is straight forward, you just need to use the definition of the matrix representation of an operator, equation 2.12. The second part may be a bit more challenging if you haven't worked with the Pauli matrices before. I suggest reviewing section 1.3.3 if you are struggling with this exercise.

<details>
<summary>Solution</summary>
 
From definition of the matrix representation of an operator we know that

$$A \ket{v_j}=\sum_{i} A_{ij} \ket{v_i}$$

Given that $\ket{v_0}=\ket{0}$ and $\ket{v_1}=\ket{1}$ and that $A \ket{0}= \ket{1}$ and $A \ket{1} = \ket{0}$, we can say that $A_{00}=0$, $A_{01}=1$, $A_{10}=1$, and $A_{11}=0$. Therefore,

$$A = \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix}$$

Instead of using $\\{ \ket{0}, \ket{1} \\}$ as the basis, let's use $\\{ \ket{+}, \ket{-} \\}$. First we will calculate what the outputs are when $A$ acts on these vectors.

$$\begin{aligned}
A \ket{+} = A \frac{1}{\sqrt{2}} (\ket{0} + \ket{1})=\frac{1}{\sqrt{2}} (\ket{1} + \ket{0}) = \ket{+} \\
A \ket{-} = A \frac{1}{\sqrt{2}} (\ket{0} - \ket{1})=\frac{1}{\sqrt{2}} (\ket{1} - \ket{0}) = -\ket{-} 
\end{aligned}$$

For these basis vectors, $A$ is then represented as

$$A = \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix}$$

</details>

**Exercise 2.3**

This exercise provides further practice in representing linear operators as matrices. It also allows you to confirm for yourself that the matrix representation of a linear transformation $BA$ is a matrix product of the matrix representations of $B$ and $A$. To do this you'll once again use equation 2.12. You’ll also need the definition of matrix multiplication, which isn’t provided in the book, but is readily available online. Additionally, if it has been a while since you’ve work with the summation operator, reviewing common summation identities may be helpful, as they play a role in the derivation. 

<details>
<summary>Solution</summary>

From the question, we know that

$$\begin{aligned}
A \ket{v_i}=\sum_{j} A_{ji} \ket{w_j} \\
B \ket{w_j}=\sum_{k} B_{kj} \ket{x_k}
\end{aligned}$$

Therefore

$$\begin{aligned}
BA \ket{v_i} & =B \sum_{j} A_{ji} \ket{w_j} & \text{definition of $A \ket{v_i}$} \\
& = \sum_{j} A_{ji} B \ket{w_j} & \text{linear operator definition}\\
& = \sum_{j} A_{ji} \sum_{k} B_{kj} \ket{x_k} & \text{definition of $B \ket{w_j}$}\\
& = \sum_{j} \sum_{k} A_{ji} B_{kj} \ket{x_k} & \text{scalar multiplication distributivity}\\
& = \sum_{j} \sum_{k} B_{kj}  A_{ji}  \ket{x_k} & \text{scalar multiplication commutativity}\\
& = \sum_{k} \sum_{j} B_{kj}  A_{ji}  \ket{x_k} & \text{summation operator commutativity}\\
& = \sum_{k} C_{ki}  \ket{x_k} & \text{matrix multiplication definition}
\end{aligned}$$

From this we can see that $BA \ket{v_i} = \sum_{k} C_{ki}  \ket{x_k}$ which means the matrix representation for the linear transformation $BA$ is the matrix product $C$ of the matrix representation for $B$ and $A$. 

</details>

**Exercise 2.4**

This is the final exercise focused on practicing how to represent linear operators as matrices. Here you will use equation 2.12 along with the definition of the identity operator given in section 2.1.2 ($I_V \ket{v} \equiv \ket{v}$) to confirm the matrix representation of the identity operator.

<details>
<summary>Solution</summary>

The matrix representation for $I$ will have entries with values $I_{ij}$ such that $I \ket{v_j}  = \sum_{i} I_{ij} \ket{v_i}$. Since we know that $I \ket{v_i} = \ket{v_i}$ for all $i$, $I_{ij} = 1$ when $i=j$ and $I_{ij} = 0$ when $i \neq j$. For a 2-dimensional vector space, the matrix representation for $I$ is

$$\begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix}$$

</details>

**Exercise 2.5**

In section 2.1.4 the authors introduce the concept of an inner product and list three requirements that need to be satisfied for something to be considered an inner product. In this exercise you need to show that $(\cdot, \cdot)$, which is given in equation 2.14, meet these three requirements.

<details>
<summary>Solution</summary>

(1) $(\cdot , \cdot)$ is linear in the second argument,

$$\begin{aligned}
\left(\ket{y}, \sum_{j}\lambda_j\ket{z_j}\right) & = \sum_{j} \lambda_j (\ket{y}, \ket{z_j}) & \text{linear in the second argument definition} \\
& = \sum_{j} \lambda_j \sum_{i} y^\ast_i z_{j} & \text{inner product definition} \\
& = \sum_{j} \sum_{i} y^\ast_i \lambda_j z_{j} & \text{scalar multiplication distributivity} \\
& = \sum_{i} \sum_{j} y^\ast_i \lambda_j z_{j} & \text{summation operator commutativity} \\
& = \sum_{i} y^\ast_i \sum_{j} \lambda_j z_{j} & \text{scalar multiplication distributivity} \\
& = \left(\ket{y}, \sum_{j}\lambda_j\ket{z_j}\right) & \text{inner product definition} 
\end{aligned}$$

(2) Conjugate symmetry,

$$\begin{aligned} 
(\ket{y}, \ket{z}) & = (\ket{z}, \ket{y})^\ast & \text{conjugate symmetry definition}\\
&=\left(\sum_{i} z^\ast_iy_i \right)^\ast & \text{inner product definition}\\
&=\sum_{i} (z^\ast_i)^\ast  y_i^\ast & \text{complex conjugate distributivity}\\
&=\sum_{i} z_i  y_i^\ast & \text{$(a^\ast)^\ast = a$}\\
&=\sum_{i} y_i^\ast z_i  & \text{scalar multiplication commutativity}\\
&=(\ket{y}, \ket{z}) & \text{inner product definition}
\end{aligned}$$

(3) Positive semi-definiteness, $(\ket{y}, \ket{y}) \geq 0$ with equality if and only if $\ket{y}=0$. 

$$\begin{aligned}
(\ket{y}, \ket{y}) & = \sum_{i} y^\ast_i y_i & \text{inner product definition}\\
& = \sum_{i} \left|y_i\right|^2 & \text{modulus definition}\\
& \geq 0 \text{ and only $=0$ when $\ket{y}$=0}
\end{aligned}$$

Since all three requirements are met, $( \cdot , \cdot)$ is an inner product. 

</details>

**Exercise 2.6**

For this exercise you will demonstrate that the inner product is conjugate-linear in the first argument using the properties that you just verified in the previous exercise.

<details>
<summary>Solution</summary>

$$\begin{aligned}
\left(\sum_{i} \lambda_i \ket{w_i}, \ket{v}\right) & = \sum_{i} \lambda^\ast_i (\ket{w_i}, \ket{v}) & \text{conjugate linear in the first argument definition} \\
& = \sum_{i} \lambda^\ast_i (\ket{v}, \ket{w_i}) ^\ast & \text{conjugate symmetry}\\ 
& = \left(\ket{v}, \sum_{i} \lambda_i \ket{w_i}\right)^\ast  & \text{linear in the second argument}\\
&= \left(\sum_{i} \lambda_i \ket{w_i}, \ket{v}\right) & \text{conjugate symmetry }
\end{aligned}$$

</details>

**Exercise 2.7**

In section 2.1.4 the authors discuss orthogonal vectors, stating that vectors are orthogonal if their inner product is zero. They also define unit vectors and discuss how to normalize a vector to make it a unit vector. Here you will use that information to demonstrate that two vectors are orthogonal and calculate their normalized forms.  

<details>
<summary>Solution</summary>

These vectors are orthogonal if their inner product equals zero.

$$\braket{w | v}= \begin{bmatrix} 1 & 1 \end{bmatrix} \begin{bmatrix} 1 \\\ -1 \end{bmatrix}= 1-1=0$$

The normalized form of these vectors are 

$$\begin{aligned}
\ket{v_{norm}}=\frac{\ket{v}}{\Vert\ket{v} \Vert}=\frac{\ket{v}}{\sqrt{\braket{v \vert v}}}=\frac{\ket{v}}{\sqrt{1^2 + (-1)^2}}=\frac{1}{\sqrt{2}} \ket{v} \\
\ket{w_{norm}}=\frac{\ket{w}}{\Vert \ket{w} \Vert}=\frac{\ket{w}}{\sqrt{\braket{w \vert w}}}=\frac{\ket{w}}{\sqrt{1^2 + 1^2}}=\frac{1}{\sqrt{2}} \ket{w}
\end{aligned}$$

</details>

**Exercise 2.8**

In section 2.1.4 the authors introduce the Gram-Schmidt procedure. Here you are asked to prove that the Gram-Schmidt procedure produces an orthonormal basis for $V$. This means that you'll need to prove several things: the vectors that are produced are unit vectors, they are orthogonal, and they form a basis for $V$. For this exercise, you will need to use proof by induction for at least one of these. 

<details>
<summary>Solution</summary>

The Gram-Schmidt procedure works as follows: define $\ket{v_1} \equiv \ket{w_1}/\Vert{\ket{w_1}}\Vert$ and for $1 \leq k \leq d-1$ define

$$\begin{aligned}
\ket{v_{k+1}} \equiv \frac{\ket{w_{k+1}} - \sum_{i=1}^{k} \braket{v_i \vert w_{k+1}}\ket{v_i}}{\Vert\ket{w_{k+1}} - \sum_{i=1}^{k} \braket{v_i \vert w_{k+1}} \ket{v_i}\Vert}
\end{aligned}$$

where $\ket{w_1},\dots,\ket{w_d}$ is a basis set for some vector space $V$. 

In order to be an orthonormal basis for $V$, all vectors must be unit vectors, they must be orthogonal i.e. $\braket{i|j}=\delta_{ij}$, and they must form a basis set for $V$. One can tell by the procedure definition that all vectors are unit vectors since all the calculations follow the form  $\ket{x}/\Vert\ket{x}\Vert$. 

To determine whether all vectors are orthogonal, let's first take the inner product of the first two vectors

$$\begin{aligned}
\braket{v_1 \vert v_2} & = \frac{\braket{v_1 \vert w_2} -  \braket{v_1 | w_2}\braket{v_1\vert v_1}}{\Vert\ket{w_{2}} - \braket{v_1 \vert w_2}\ket{v_1}\Vert} \\ 
& = \frac{\braket{v_1 \vert w_2} -  \braket{v_1 \vert w_2}}{\Vert\ket{w_{2}} - \braket{v_1 \vert w_2}\ket{v_1}\Vert} & \text{Since $\braket{v_1 \vert v_1}=1$} \\
& = 0
\end{aligned}$$

Now let's take the inner product of the first and third vectors

$$\begin{aligned}
\braket{v_1 \vert v_3} & = \frac{\braket{v_1 \vert w_3} -  \braket{v_1 \vert w_3}\braket{v_1 \vert v_1} - \braket{v_2 \vert w_3}\braket{v_1 \vert v_2}}{\Vert\ket{w_{3}} - \braket{v_1 \vert w_3}\ket{v_1}-\braket{v_2 \vert w_3}\ket{v_2}\Vert} \\
& = \frac{\braket{v_1 \vert w_3} -  \braket{v_1 \vert w_3} }{\Vert\ket{w_{3}} - \braket{v_1 \vert w_3}\ket{v_1}-\braket{v_2 \vert w_3}\ket{v_2}\Vert} & \text{Since $\braket{v_1 \vert v_1}=1$ and $\braket{v_1 \vert v_2}=0$} \\
& = 0
\end{aligned}$$

Then let's take the inner product of the second and third vectors

$$\begin{aligned}
\braket{v_2 \vert v_3} & = \frac{\braket{v_2 \vert w_3} -  \braket{v_1 \vert w_3}\braket{v_2 \vert v_1} - \braket{v_2 \vert w_3}\braket{v_2 \vert v_2}}{\Vert\ket{w_{3}} - \braket{v_1 \vert w_3}\ket{v_1}-\braket{v_2 \vert w_3}\ket{v_2}\Vert} \\
& = \frac{\braket{v_2 \vert w_3} -  \braket{v_2 \vert w_3} }{\Vert\ket{w_{3}} - \braket{v_1 \vert w_3}\ket{v_1}-\braket{v_2 \vert w_3}\ket{v_2}\Vert} & \text{Since $\braket{v_2 \vert v_2}=1$ and $\braket{v_1 \vert v_2}=0$} \\
& = 0
\end{aligned}$$

The above calculations show that $\braket{v_j \vert v_i}=0$ for $j < i \le 3$. Using conjugate symmetry this can be generalized to $\braket{v_j \vert v_i}=0$ when $i \neq j$ for $j,i \le 3$. We can then take the inner product of the fourth vector and an arbitrary vector $\ket{v_j}$ where $j<4$

$$\begin{aligned}
\braket{v_j | v_4} & = \frac{\braket{v_j | w_4} - \sum_{i=1}^{3} \braket{v_i | w_4}\braket{v_j | v_i}}{\Vert\ket{w_4} - \sum_{i=1}^{k} \braket{v_i | w_4}\ket{v_i}\Vert}\\
& = \frac{\braket{v_j | w_4} - \braket{v_j | w_4}\braket{v_j | v_j}}{\Vert\ket{w_4} - \sum_{i=1}^{k} \braket{v_i | w_4}\ket{v_i}\Vert} & \text{Since $\braket{v_j | v_i}=0$ when $i \neq j$} \\
& = \frac{\braket{v_j | w_4} - \braket{v_j | w_4}}{\Vert\ket{w_4} - \sum_{i=1}^{k} \braket{v_i | w_4}\ket{v_i}\Vert} & \text{Since $\braket{v_j | v_j}=1$} \\
& = 0
\end{aligned}$$

So now we know that that $\braket{v_j | v_i}=0$ when $i \neq j$ for $j,i \le 4$. This same calculation can be applied to $\braket{v_j | w_5}$ for $j<5$, then $\braket{v_j | w_6}$ for $j<6$, and so on up to $\braket{v_j | w_d}$ for $j<d$. We then get that that $\braket{v_j | v_i}=0$ when $i \neq j$ for $j,i \le d$, demonstrating that the vectors are orthogonal. 

The final thing that we need to do is show that this orthonormal set of vectors is a basis for $V$. In order for a set of vectors to be a basis set it needs to be linearly independent and span the vector space $V$. Orthogonality of a set of nonzero vectors intrinsically implies their linear independence, so since this set of vectors is orthogonal we know that it is linearity independent. However, if desired, we can demonstrate this by assuming that the vector set is linearly dependent which would mean that there exists a set of complex numbers $a_1, \dots, a_d$ with $a_i \neq 0$ for at least one value of i, such that $a_1 \ket{v_1} + a_2 \ket{v_2} + \dots + a_d \ket{v_d} = 0$. In other words, we would be able to represent at least one of the vectors in the set, let's call it $\ket{v_j}$, as a linear combination of the other vectors in the set, 

$$\begin{aligned}
\ket{v_j} = \sum_{i=1}^{j-1} a_i \ket{v_i} + \sum_{i=j+1}^{d} a_i \ket{v_i}
\end{aligned}$$

Taking the inner product of both sides with $\ket{v_j}$ we get

$$\begin{aligned}
\braket{v_j \vert v_j} = \sum_{i=1}^{j-1} a_i \braket{v_j \vert v_i} + \sum_{i=j+1}^{d} a_i \braket{v_j \vert v_i} 
\end{aligned}$$

Which simplifies to $1 = 0$ because $\braket{v_j \vert v_i} = 0$ for $j \neq i$ due to its orthogonality. Since this is not true, the set cannot be linearly dependent. 

We know that this set of vectors spans $V$ because it has the same number of elements as the original basis set $\ket{w_1}, \dots, \ket{w_d}$ and any two sets of linearly independent vectors which span a vector space contain the same number of elements, as stated in section 2.1.1. Therefore $\ket{v_1}, \dots, \ket{v_d}$ as generated by the Gram-Schmidt procedure is a orthonormal basis for $V$. 

</details>

**Exercise 2.9**

In section 2.1.4 the authors introduce outer product representation for linear operators. For this exercise you are asked to express each Pauli matrix in outer product notation. This can be done by using equation 2.25. The Pauli matrices are given in section 2.1.3.

<details>
<summary>Solution</summary>

We can find their expression in outer product notation using equation 2.25, $A=\sum_{ij} \braket{w_j | A | v_i} \ket{w_j} \bra{v_i}$. As stated in the book, $\braket{w_j | A | v_i}$ equals the element in the *i*th column and *j*th row of the matrix representation of the operator, so it is possible to just read these values from the matrix or you can calculate them as shown below. 

For $I$ we get

$$\begin{aligned}
I &= \braket{0 \vert I \vert 0} \ket{0} \bra{0} + \braket{0 \vert I \vert 1} \ket{0} \bra{1} + \braket{1 \vert I \vert 0} \ket{1} \bra{0} + \braket{1 \vert I \vert 1} \ket{1} \bra{1} \\
&= \braket{0 \vert 0} \ket{0} \bra{0} + \braket{0 \vert 1} \ket{0} \bra{1} + \braket{1 \vert 0} \ket{1} \bra{0} + \braket{1 \vert 1} \ket{1} \bra{1} \\
&=  \ket{0} \bra{0} + \ket{1} \bra{1} 
\end{aligned}$$

For $X$ we get

$$\begin{aligned}
X &= \braket{0 \vert X \vert 0} \ket{0} \bra{0} + \braket{0 \vert X \vert 1} \ket{0} \bra{1} + \braket{1 \vert X \vert 0} \ket{1} \bra{0} + \braket{1 \vert X \vert 1} \ket{1} \bra{1} \\
&= \braket{0 \vert 1} \ket{0} \bra{0} + \braket{0 \vert 0} \ket{0} \bra{1} + \braket{1 \vert 1} \ket{1} \bra{0} + \braket{1 \vert 0} \ket{1} \bra{1} \\
&=  \ket{0} \bra{1} + \ket{1} \bra{0} 
\end{aligned}$$

For $Y$ we get

$$\begin{aligned}
Y &= \braket{0 \vert Y \vert 0} \ket{0} \bra{0} + \braket{0 \vert Y \vert 1} \ket{0} \bra{1} + \braket{1 \vert Y \vert 0} \ket{1} \bra{0} + \braket{1 \vert Y \vert 1} \ket{1} \bra{1} \\
&= i \braket{0 \vert 1} \ket{0} \bra{0} - i \braket{0 \vert 0} \ket{0} \bra{1} + i \braket{1 \vert 1} \ket{1} \bra{0} - i \braket{1 \vert 0} \ket{1} \bra{1} \\
&=   i \ket{1} \bra{0} - i \ket{0} \bra{1}
\end{aligned}$$

For $Z$ we get

$$\begin{aligned}
X &= \braket{0 \vert Z \vert 0} \ket{0} \bra{0} + \braket{0 \vert Z \vert 1} \ket{0} \bra{1} + \braket{1 \vert Z \vert 0} \ket{1} \bra{0} + \braket{1 \vert Z \vert 1} \ket{1} \bra{1} \\
&= \braket{0 \vert 0} \ket{0} \bra{0} - \braket{0 \vert 1} \ket{0} \bra{1} + \braket{1 \vert 0} \ket{1} \bra{0} - \braket{1 \vert 1} \ket{1} \bra{1} \\
&=  \ket{0} \bra{0} - \ket{1} \bra{1} 
\end{aligned}$$

</details>

**Exercise 2.10**

This exercise provides more practice with outer product notation. This time you will use equation 2.25 to find the matrix representation for an operator that is given in outer product notation. 

<details>
<summary>Solution</summary>

From equation 2.25 we can write $A=\sum_{mn} \braket{v_m \vert A \vert v_n} \ket{v_m} \bra{v_n} = \ket{v_j} \bra{v_k}$. Which means that we need $\braket{v_m \vert A \vert v_n} = 1$ when $m=j$ and $n=k$ and $\braket{v_m \vert A \vert v_n} = 0$ otherwise. This means the matrix representation has 1 for the $A_{jk}$ element and 0 for all other elements.

</details>

**Exercise 2.11**

In this exercise you are asked to find the eigenvectors, eigenvalues, and diagonal representations of the Pauli matrices $X$, $Y$, and $Z$. The book explains how to calculate the eigenvalues by using the characteristic equation for operators that are in the matrix representation, but it assumes that you’re already familiar with how to find the corresponding eigenvectors. 

If you are unsure or need a refresher, here is a brief summary of the procedure: once you find an eigenvalue $\lambda$, you can solve the equation $0 = (A-\lambda I)\ket{e}$ to find eigenvector $\ket{e}$ where $A$ is the operator (in matrix form) and $I$ is the identity matrix. 

Once you have a full set of eigenvalues and eigenvectors, you can write the operator in diagonal representation using the form $A = \sum_{i} \ket{i} \bra{i}$, where vectors $\ket{i}$ form an orthonormal set of eigenvectors. 


<details>
<summary>Solution</summary>

Z is already in a diagonal representation, so the eigenvectors and eigenvalues can be easily seen,

$$\begin{aligned}
Z = \ket{0}\bra{0} - \ket{1}\bra{1}
\end{aligned}$$

With the eigenvectors $\ket{0}$, $\ket{1}$ and corresponding eigenvalues 1, -1. 

X can be diagonalized by converting to the basis set $\ket{+}$ and $\ket{-}$, like we did in Exercise 2.2

$$\begin{aligned}
X &= \ket{0}\bra{1} + \ket{1}\bra{0} \\
&= \ket{+}\bra{+} - \ket{-}\bra{-}
\end{aligned}$$

With the eigenvectors $\ket{+}$, $\ket{-}$ and corresponding eigenvalues 1, -1. 

For Y, we'll use the characteristic equation to identify the eigenvalues

$$\begin{aligned}
\text{det} \left(Y - \lambda I \right) &= \text{det} \left( \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} - \lambda  \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) \\
&= \text{det} \left( \begin{bmatrix} - \lambda & -i \\\ i & -\lambda \end{bmatrix} \right) \\ 
&= \lambda^2 - (-i)(i) \\
&= \lambda^2 - 1 = 0
\end{aligned}$$

Which means $\lambda = 1$ or $\lambda = -1$ . So now we need to solve

$$\begin{aligned}
0 &= (\lambda I - Y) \ket{e} \\ 
&= \left(\begin{bmatrix} \lambda & 0 \\\ 0 & \lambda \end{bmatrix}  - \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \right) \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} \lambda & i \\\ -i & \lambda \end{bmatrix} \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} \lambda x_1 + i x_2 \\\ \lambda x_2 - i x_1 \end{bmatrix}
\end{aligned}$$

Which gives us $\lambda x_1 + i x_2 = 0$ and $\lambda x_2 - i x_1 =0$. For $\lambda = 1$ this is true for the unit vector $\ket{e_1} = \frac{1}{\sqrt{2}} (1, i)$. For $\lambda = -1$ this is true for the unit vector $\ket{e_2} = \frac{1}{\sqrt{2}} (1, -i)$. Putting Y in diagonal outer product representation we get

$$\begin{aligned}
Y=\ket{e_1}\bra{e_1} - \ket{e_2}\bra{e_2}
\end{aligned}$$

With the eigenvectors $\ket{e_1}$, $\ket{e_2}$ and corresponding eigenvalues 1, -1.

</details>

**Exercise 2.12**

For this exercise you need to prove that a specific matrix is not diagonalizable. In section 2.1.5 we are told that an operator is diagonalizable if it has diagonal representation. So to prove that it is not diagonalizable, you need to show that it does not have diagonal representation.

<details>
<summary>Solution</summary>

First let's find the eigenvalues and eigenvectors for the matrix. 

$$\begin{aligned}
0 &= \text{det} \left( \begin{bmatrix} 1 & 0 \\\ 1 & 1 \end{bmatrix} - \lambda  \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) \\
&= \text{det} \left( \begin{bmatrix} 1-\lambda & 0 \\\ 1 & 1-\lambda \end{bmatrix}  \right) \\
&= (1-\lambda)^2
\end{aligned}$$

Which means the only eigenvalue is 1.

Now we'll find the eigenvectors. 

$$\begin{aligned}
0 &=  \left( \begin{bmatrix} 1 & 0 \\\ 1 & 1 \end{bmatrix} - \lambda  \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&=  \begin{bmatrix} 1-\lambda & 0 \\\ 1 & 1-\lambda \end{bmatrix} \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
& = \begin{bmatrix} (1-\lambda)x_1 \\\ x_1 + (1-\lambda)x_2 \end{bmatrix} \\
& = \begin{bmatrix} 0 \\\ x_1 \end{bmatrix}
\end{aligned}$$

This is true for the unit vector $(0,1)$, there are no other linearly independent eigenvectors. 

For a matrix to have a diagonal representation, it needs to have an orthonormal set of eigenvectors with corresponding eigenvalues that span the vector space; the set should have the same number of elements as the dimension of the vector space, which in this case is two. Since this matrix only has one linearly independent eigenvector, there is not an orthonormal set of eigenvectors that span the vector space and so the matrix does not have a diagonal representation. A matrix is only diagonalizable if it has a diagonal representation. Therefore this matrix is not diagonalizable. 

</details>

**Exercise 2.13**

In section 2.1.6 the authors introduce the adjoint of operators. For this exercise we are asked to show that $(\ket{w}\bra{v})^\dagger = \ket{v}\bra{w}$, this can be done using equation 2.32 and some of the properties of inner products that we've already identified.

<details>
<summary>Solution</summary>

Taking equation 2.32 and plugging in $\ket{w}\bra{v}$ for $A$ we get

$$\begin{aligned}
((\ket{w}\bra{v})^\dagger \ket{x}, \ket{y}) &= (\ket{x}, (\ket{w}\bra{v}) \ket{y}) & \text{Adjoint definition}\\
&= \braket{x \vert w} \braket{v \vert y} & \text{inner product definition}\\
&= \braket{w \vert x}^\ast \braket{y \vert v}^\ast & \text{conjugate symmetry} \\
& = \braket{y \vert v}^\ast \braket{w \vert x}^\ast & \text{scalar multiplication commutativity}\\
&= (\braket{y \vert v} \braket{w \vert x})^\ast & \text{complex conjugate distributivity}\\
&=(\ket{y}, (\ket{v}\bra{w}) \ket{x} )^\ast & \text{inner product definition}\\
&= ((\ket{v}\bra{w}) \ket{x}, \ket{y}) & \text{conjugate symmetry}
\end{aligned}$$

From the first and last line it can be seen that $(\ket{w}\bra{v})^\dagger = \ket{v}\bra{w}$.

</details>

**Exercise 2.14**

We are asked to show that the adjoint operation is anti-linear, this can be done using equation 2.32 and some of the properties of inner products that we've already identified. 

<details>
<summary>Solution</summary>

Plugging this operator into equation 2.32 we get

$$\begin{aligned}
\left(\left( \sum_{i} a_i A_i \right)^\dagger \ket{x}, \ket{y}\right) &= \left(\ket{x}, \left( \sum_{i} a_i A_i \right) \ket{y}\right) & \text{Adjoint definition}\\
&= \sum_{i} a_i \left(\ket{x}, A_i \ket{y}\right) & \text{linearity in the second argument}\\
&= \sum_{i} a_i \left(A_i^\dagger \ket{x}, \ket{y}\right) & \text{Adjoint definition}\\
&= \left(\left(\sum_{i} a_i^\ast A_i^\dagger \right) \ket{x}, \ket{y}\right) & \text{conjugate-linearity in the first argument}
\end{aligned}$$

From the first and last line it can be seen that $\left( \sum_{i} a_i A_i \right)^\dagger = \sum_{i} a_i^\ast A_i^\dagger$.

</details>

**Exercise 2.15**

We are asked to show that $(A^\dagger)^\dagger = A$, this can be done using equation 2.32 and some of the properties of inner products that we've already identified. 

<details>
<summary>Solution</summary>

Lets plug $A^\dagger$ in for $A$ in equation 2.32

$$\begin{aligned}
\left(\left( A^\dagger \right)^\dagger \ket{x}, \ket{y}\right) &= \left(\ket{x}, \left( A^\dagger \right) \ket{y}\right) & \text{Adjoint definition}\\
&= \left(\left( A^\dagger \right) \ket{y}, \ket{x}\right)^\ast & \text{conjugate symmetry}\\
&= \left(\ket{y}, A \ket{x}\right)^\ast & \text{Adjoint definition}\\
&= \left(A \ket{x}, \ket{y} \right) & \text{conjugate symmetry}
\end{aligned}$$

From the first and last line it can be seen that $(A^\dagger)^\dagger = A$.

</details>

**Exercise 2.16**

In section 2.1.6 the authors introduce the concept of projectors. For this exercise you use the definition of projector $P$ from equation 2.35 and basis vector orthogonality to demonstrate the $P^2=P$. 

<details>
<summary>Solution</summary>

From equation 2.35 we know that $P$ is defined as $P \equiv \sum_{i=1}^k \ket{i} \bra{i}$ and so $P^2$ is 

$$\begin{aligned}
P^2 &= PP \\
&= \sum_{i=1}^k \ket{i} \bra{i} \sum_{j=1}^k \ket{j} \bra{j} & \text{definition of $P$}\\
&= \sum_{i=1}^k \sum_{j=1}^k  \ket{i} \braket{i \vert j} \bra{j} & \text{summation operator distributivity}\\
&= \sum_{i=1}^k \sum_{j=1}^k  \ket{i} \bra{j} \delta_{ij} & \text{vector orthogonality}\\
&= \sum_{i=1}^k  \ket{i} \bra{i} & \text{delta function execution}\\
&= P & \text{definition of $P$}
\end{aligned}$$

</details>

**Exercise 2.17**

In this exercise we are asked to explore the relationship between normal and Hermitian matrices. For this you will use spectral decomposition, anti-linearity of the adjoint, and the results from exercise 2.13. 

<details>
<summary>Solution</summary>

Operator $A$ is a normal matrix if it is diagonal with respect to some orthonormal basis (per spectral decomposition). Therefore $A$ can be written as $A=\sum_{i} \lambda_{i} \ket{i} \bra{i}$ where $\lambda_{i}$ are the eigenvalues of $A$ and $\ket{i}$ is an orthonormal basis. It then follows that

$$\begin{aligned}
A^\dagger &= \left(\sum_{i} \lambda_{i} \ket{i} \bra{i}\right)^\dagger & \text{spectral decomposition}\\
&= \sum_{i} \lambda_{i}^\ast \left(\ket{i} \bra{i}\right)^\dagger & \text{anti-linearity of the adjoint}\\
&= \sum_{i} \lambda_{i}^\ast \ket{i} \bra{i} & \text{like exercise 2.13} \\
\end{aligned}$$

Operator $A$ is Hermitian if $A^\dagger = A$. From the above equation, it can been seen that this is only the case when $\lambda_i^* = \lambda_i$, i.e. when the operator only has real eigenvalues.

</details>

**Exercise 2.18**

Here we show that all eigenvalues of a unitary matrix has modulus 1 using the definition of a unitary matrix, the outer product representation for $U$ and $I$, and vector orthogonality.

<details>
<summary>Solution</summary>

Since $U$ is a unitary matrix we know that $U^\dagger U = I$. We also know that U has spectral decomposition and so can be written $U \equiv \sum_i \lambda_i \ket{i} \bra{i}$. $I$ is defined as $I = \sum_i \ket{i} \bra{i}$. Therefore, 

$$\begin{aligned}
I &= U^\dagger U & \text{unitary matrix definition}\\
\sum_i \ket{i} \bra{i} &= \left( \sum_i \lambda_i \ket{i} \bra{i} \right)^\dagger \left(\sum_j \lambda_j \ket{j} \bra{j} \right) & \text{outer product representation}\\
&= \left( \sum_i \lambda_i^\ast \ket{i} \bra{i} \right) \left(\sum_j \lambda_j \ket{j} \bra{j} \right) & \text{adjoint definition}\\
&= \sum_i \sum_j \lambda_i^\ast \lambda_j  \ket{i} \braket{i | j} \bra{j} & \text{summation distributivity}\\
&= \sum_i \sum_j \lambda_i^\ast \lambda_j  \delta_{ij} \ket{i} \bra{j} & \text{vector orthogonality}\\
&= \sum_i \lambda_i^\ast \lambda_i \ket{i} \bra{i} & \text{apply the delta function}\\
&= \sum_i \vert \lambda_i \vert^2 \ket{i} \bra{i} & \text{modulus definition}
\end{aligned}$$

Looking at the second and last line, it can be seen that $\sum_i \ket{i} \bra{i} = \sum_i \vert \lambda_i \vert^2 \ket{i} \bra{i}$ and therefore $\vert \lambda_i \vert^2= 1$, so the modulus is 1. 

I'm not sure if this part is necessary for the solution, but I'm going to write it out anyway. Let's set $\lambda_i = e^{i \theta}$ for some real $\theta$, then

$$\begin{aligned}
\vert \lambda_i \vert^2 &= \left(e^{i \theta} \right)^\ast \left(e^{i \theta} \right) \\
&= \left(e^{-i \theta} \right) \left(e^{i \theta} \right) \\
&= e^{i \theta -i \theta} \\
&= e^{0} \\
&= 1
\end{aligned}$$

Demonstrating that the eigenvalues can be written in the form $e^{i \theta}$.

</details>

**Exercise 2.19**

This exercise has you demonstrate that the Pauli matrices are Hermitian and unitary. To do this you just use the definition of Hermitian and unitary matrices and plug in the Pauli matrices. 

<details>
<summary>Solution</summary>

To show that the matrices are Hermitian, we need to demonstrate that $\sigma^\dagger = \sigma$ and to demonstrate that they are unitary we need to show that $\sigma^\dagger \sigma = I$. 

Calculating $X^\dagger$ we get

$$\begin{aligned}
X^\dagger &= \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} ^\dagger \\
&= \left(\begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix}^\ast \right)^T \\
&= \left(\begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \right)^T \\
&= \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix}  \\
&= X 
\end{aligned}$$

Then calculating $X^\dagger X$ we get

$$\begin{aligned}
X^\dagger X &= X X \\
&= \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \\
& = \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \\
& = I 
\end{aligned}$$

Calculating $Y^\dagger$ we get

$$\begin{aligned}
Y^\dagger &= \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} ^\dagger \\
&= \left(\begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix}^\ast \right)^T \\
&= \left(\begin{bmatrix} 0 & i \\\ -i & 0 \end{bmatrix} \right)^T \\
&= \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix}  \\
&= Y 
\end{aligned}$$

Then calculating $Y^\dagger Y$ we get

$$\begin{aligned}
Y^\dagger Y &= Y Y \\
&= \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \\
& = \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \\
& = I
\end{aligned}$$

Calculating $Z^\dagger$ we get

$$\begin{aligned}
Z^\dagger &= \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} ^\dagger \\
&= \left(\begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix}^\ast \right)^T \\
&= \left(\begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \right)^T \\
&= \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix}  \\
&= Z 
\end{aligned}$$

Then calculating $Z^\dagger Z$ we get

$$\begin{aligned}
Z^\dagger Z &= Z Z \\
&= \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \\
& = \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \\
& = I  
\end{aligned}$$

</details>

**Exercise 2.20**

For this exercise you are asked to find the relationship between two different matrix representations of operator $A$. This can be done using the completeness relation as shown in equation 2.23.

<details>
<summary>Solution</summary>

Using the completeness relation we know that $A = I_W A I_W$ and so

$$\begin{aligned}
A_{ij}' &= \braket{v_i \vert A \vert v_j} & \text{definition of $A_{ij}'$} \\
&= \braket{v_i \vert I_W A I_W \vert v_j} & \text{completeness relation} \\
&= \braket{v_i \vert \left(\sum_m \ket{w_m} \bra{w_m} \right) A \left(\sum_n \ket{w_n} \bra{w_n} \right) | v_j} & \text{outer product representation of $I$}\\
&= \sum_m \sum_n \braket{v_i \vert w_m} \braket{w_m \vert A \vert w_n} \braket{w_n \vert v_j} & \text{summation distributivity}\\
&= \sum_m \sum_n \braket{v_i \vert w_m} A_{mn}'' \braket{w_n \vert v_j} & \text{definition of $A_{ij}''$}
\end{aligned}$$

</details>

**Exercise 2.21**

For this exercise we are asked to repeat the spectral decomposition proof, but with a Hermitian operator instead of a normal operator. There are a couple of places where simplifications can be made. One is when demonstrating that $PMQ = 0$ and then another when showing that $QMQ$ is normal. 

<details>
<summary>Solution</summary>

Spectral decomposition theorem for the case when $M$ is Hermitian: Any Hermitian operator $M$ on a vector space $V$ is diagonal with respect to some orthonormal basis for $V$. Conversely, any diagonalizable operator is normal. 

The first part of the proof is identical to what is in the book. Proof by induction is used on the dimension $d$ of $V$. The case $d=1$ is trivial. Let $\lambda$ be an eigenvalue of $M$, $P$ the projector onto the $\lambda$ eigenspace, and $Q$ the projector onto the orthogonal complement. Then $M = (P+Q)M(P+Q) = PMP+QMP+PMQ+QMQ$. Obviously $PMP=\lambda P$. Furthermore, $QMP=0$, as $M$ takes the subspace $P$ into itself. Simplifications can be made when demonstrating that $PMQ = 0$ due to $M$ being Hermitian and so $M^\dagger = M$. This can now be shown by taking the adjoint of $QMP=0$ which gives 

$$\begin{aligned}
0 = (QMP)^\dagger = PM^\dagger Q = PMQ
\end{aligned}$$

Simplifications can also be made when proving that $QMQ$ is normal. That proof goes as follows

$$\begin{aligned}
QMQ (QMQ)^\dagger=QMQ QM^\dagger Q = QMQQMQ = QM^\dagger Q QMQ = (QMQ)^\dagger QMQ
\end{aligned}$$

Therefore $QMQ$ is normal. The rest of the proof is same as in the book where you use proof by induction to show that $QMQ$ is diagonal with respect to some orthonormal basis for subspace $Q$, and $PMP$ is already diagonal with respect to some orthonormal basis for $P$. It then follows that $M=PMP+QMQ$ is diagonal with respect to some orthonormal basis for the total vector space. 

</details>

**Exercise 2.22**

In this exercise we are to prove that two eigenvectors of a Hermitian operator with different eigenvalues are orthogonal. To do this you can use equation 2.32, the fact that for a Hermitian operator $H=H^\dagger$, and properties of the inner product.

<details>
<summary>Solution</summary>

Let's assume we have two eigenvectors $\ket{v}$ and $\ket{w}$ of Hermitian operator $M$ with eigenvalues $\lambda_v$ and $\lambda_w$. From equation 2.32 we know that $(\ket{v}, M \ket{w}) = (M^\dagger \ket{v}, \ket{w})$. Since M is Hermitian $M^\dagger=M$ so $(\ket{v}, M \ket{w}) = (M \ket{v}, \ket{w})$ and therefore $(\ket{v}, \lambda_w \ket{w}) = (\lambda_v \ket{v}, \ket{w})$. Using linearity in the second and conjugate-linearity in the first arguments we get $\lambda_w(\ket{v}, \ket{w}) = \lambda_v^\ast( \ket{v}, \ket{w})$. As shown in Exercise 2.17, we know that the eigenvalues of a Hermitian operator are real and therefore $\lambda_w(\ket{v}, \ket{w}) = \lambda_v( \ket{v}, \ket{w})$. This can only be true if $\lambda_w = \lambda_v$ or $(\ket{v}, \ket{w}) =0$, i.e. the vectors are orthogonal. Therefore if $\lambda_w \neq \lambda_v$ then the vectors must be orthogonal. 

</details>

**Exercise 2.23**

Here we show that the eigenvalues of a projector are all either $0$ or $1$ by comparing the definition of $P$ to the diagonal representation for an operator. 

<details>
<summary>Solution</summary>

By definition $P \equiv \sum_{i=1}^k \ket{i} \bra{i}$ for a k-dimensional vector subspace of a d-dimensional vector space. This is a diagonal matrix which has the form $\sum_i \lambda_i \ket{i} \bra{i}$. By looking at the definition of $P$ and comparing it to the form of a diagonal matrix, one can easily see that $\lambda_i=1$ for $1 \leq i \leq k$ and $\lambda_i=0$ for $k < i \leq d$. Therefore the eigenvalues are all either 0 or 1.

</details>

**Exercise 2.24**

For this exercise follow the hint’s advice and find Hermitian operators $B$ and $C$ that satisfies $A=B+iC$ for an arbitrary operator $A$. Then use the definition of a positive operator to find what constraints there are on $B$ and $C$ if $A$ is a positive operator. You will find that $A$ must be Hermitian. 

<details>
<summary>Solution</summary>

First we need to find a $B$ and $C$ that satisfy these requirements. Let's start by finding $A^\dagger$ in terms of $B$ and $C$, keeping in mind that $B^\dagger = B$ and $C^\dagger = C$, since they are Hermitian. 

$$\begin{aligned}
A^\dagger &= (B + i C)^\dagger \\
&= B^\dagger + (i C)^\dagger \\
&= B - iC
\end{aligned}$$

Therefore $A + A^\dagger = 2B$. Solving for $B$ we get $B=\frac{A+A^\dagger}{2}$. Then $A-A^\dagger = 2 i C$. Solving for $C$ we get $C=\frac{A-A^\dagger}{2i}$. 

We can then confirm that these definitions of $B$ and $C$ are Hermitian by taking the adjoint of them

$$\begin{aligned}
B^\dagger &= \left(\frac{A+A^\dagger}{2}\right)^\dagger \\
&= \frac{A^\dagger+(A^\dagger)^\dagger}{2} \\
&=\frac{A^\dagger + A}{2} \\
&=B \\
C^\dagger &= \left(\frac{A-A^\dagger}{2i}\right)^\dagger \\
&= \frac{A^\dagger-(A^\dagger)^\dagger}{-2i} \\
&= \frac{-A^\dagger+A}{2i} \\
&= C
\end{aligned}$$

Therefore $B$ and $C$ are Hermitian.

If $A$ is positive then $(\ket{v}, A \ket{v})$ is a real, non-negative number. Plugging in $A=B+iC$ we get $\braket{v \vert A \vert v} = \braket{v \vert B+iC \vert v} = \braket{v \vert B \vert v} + i \braket{v \vert C \vert v}$, which is only a real number when $C=0$. Therefore $A=B$ which is Hermitian.

</details>

**Exercise 2.25**

To show that $A^\dagger A$ is positive, use the definition of a positive operator, equation 2.32, and the positive semi-definiteness of the inner product.

<details>
<summary>Solution</summary>

In order for $A^\dagger A$ to be positive $\left(\ket{v}, A^\dagger A \ket{v}\right)$ must be a real, non-negative number. 

$$\begin{aligned}
\left(\ket{v}, A^\dagger A \ket{v}\right) &= \left((A^\dagger)^\dagger \ket{v}, A \ket{v}\right) & \text{equation 2.32} \\
&= \left(A \ket{v}, A \ket{v}\right) & \text{from exercise 2.15}
\end{aligned}$$

Due to the positive semi-definiteness of inner products, we know that $\left(A \ket{v}, A \ket{v}\right) \geq 0$ with equality if and only if $A \ket{v} = 0$. Therefore $A^\dagger A$ is positive.

</details>

**Exercise 2.26**

In section 2.1.7 the authors introduce the concept of tensor products. In this exercise you will gain experience with tensor power notation and the Kronecker product. 

<details>
<summary>Solution</summary>

Written as a tensor products, 

$$\begin{aligned}
\ket{\psi}^{\otimes 2}&=\ket{\psi} \otimes \ket{\psi} \\
&= \frac{\ket{0} + \ket{1} }{\sqrt{2}}\otimes \frac{\ket{0} + \ket{1}}{\sqrt{2}} \\
&= \frac{\ket{0}  \ket{0} + \ket{1}  \ket{0} + \ket{0}  \ket{1} + \ket{1}  \ket{1} }{2} \\
\ket{\psi}^{\otimes 3}&=\ket{\psi} \otimes \ket{\psi} \otimes \ket{\psi} \\
&= \frac{\ket{0} + \ket{1} }{\sqrt{2}}\otimes \frac{\ket{0} + \ket{1}}{\sqrt{2}} \otimes \frac{\ket{0} + \ket{1}}{\sqrt{2}} \\
&= \frac{\ket{0}  \ket{0} + \ket{1}  \ket{0} + \ket{0}  \ket{1} + \ket{1}  \ket{1} }{2} \otimes \frac{\ket{0} + \ket{1}}{\sqrt{2}} \\
&= \frac{\ket{0}  \ket{0} \ket{0} + \ket{1}  \ket{0}\ket{0} + \ket{0}  \ket{1}\ket{0} + \ket{1}  \ket{1}\ket{0} + \ket{0}  \ket{0}\ket{1} + \ket{1}  \ket{0}\ket{1} + \ket{0}  \ket{1}\ket{1} + \ket{1}  \ket{1} \ket{1}}{2 \sqrt{2}}
\end{aligned}$$


Let's write $\ket{\psi}$ in matrix form before representing the tensor products using the Kronecker product.

$$\begin{split}
\ket{\psi}&=\left(\ket{0} + \ket{1} \right)/ \sqrt{2} \\
&= \frac{1}{\sqrt{2}} \left( \begin{bmatrix} 1 \\\ 0  \end{bmatrix} + \begin{bmatrix} 0 \\\ 1  \end{bmatrix} \right) \\
&= \frac{1}{\sqrt{2}} \begin{bmatrix} 1 \\\ 1  \end{bmatrix}
\end{split}$$


Using the Kronecker product,

$$\begin{aligned}
\ket{\psi}^{\otimes 2}&=\frac{1}{\sqrt{2}} \begin{bmatrix} 1 \\\ 1  \end{bmatrix} \otimes \frac{1}{\sqrt{2}} \begin{bmatrix} 1 \\\ 1  \end{bmatrix} \\
&= \frac{1}{2} \begin{bmatrix} 1 \\\ 1 \\\ 1 \\\ 1 \end{bmatrix} \\
\ket{\psi}^{\otimes 3}&= \frac{1}{\sqrt{2}} \begin{bmatrix} 1 \\\ 1  \end{bmatrix} \otimes \frac{1}{\sqrt{2}} \begin{bmatrix} 1 \\\ 1  \end{bmatrix} \otimes \frac{1}{\sqrt{2}} \begin{bmatrix} 1 \\\ 1  \end{bmatrix} \\
&= \frac{1}{2} \begin{bmatrix} 1 \\\ 1 \\\ 1 \\\ 1 \end{bmatrix} \otimes \frac{1}{\sqrt{2}} \begin{bmatrix} 1 \\\ 1  \end{bmatrix} \\
&= \frac{1}{2 \sqrt{2}} \begin{bmatrix} 1 \\\ 1 \\\ 1 \\\ 1 \\\ 1 \\\ 1 \\\ 1 \\\ 1 \end{bmatrix} 
\end{aligned}$$

</details>

**Exercise 2.27**

This exercise is just further practice with the Kronecker product. To check if the tensor product is commutative compare your results from (b) and (c).

<details>
<summary>Solution</summary>

(a) tensor product of $X$ and $Z$

$$\begin{aligned}
X \otimes Z &= \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \otimes \begin{bmatrix} 1 & 0 \\\ 0 & -1  \end{bmatrix} \\
&= \begin{bmatrix} 0 * \begin{bmatrix} 1 & 0 \\\ 0 & -1  \end{bmatrix} & 1 * \begin{bmatrix} 1 & 0 \\\ 0 & -1  \end{bmatrix} \\\ 1 * \begin{bmatrix} 1 & 0 \\\ 0 & -1  \end{bmatrix} & 0 * \begin{bmatrix} 1 & 0 \\\ 0 & -1  \end{bmatrix} \end{bmatrix} \\
&= \begin{bmatrix} \begin{bmatrix} 0 & 0 \\\ 0 & 0  \end{bmatrix} & \begin{bmatrix} 1 & 0 \\\ 0 & -1  \end{bmatrix} \\\ \begin{bmatrix} 1 & 0 \\\ 0 & -1  \end{bmatrix} & \begin{bmatrix} 0 & 0 \\\ 0 & 0  \end{bmatrix} \end{bmatrix} \\
&= \begin{bmatrix} 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & -1 \\\ 1 & 0 & 0 & 0 \\\ 0 & -1 & 0 & 0 \end{bmatrix} 
\end{aligned}$$


(b) tensor product of $I$ and $X$

$$\begin{aligned}
I \otimes X &= \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \otimes \begin{bmatrix} 0 & 1 \\\ 1 & 0  \end{bmatrix} \\
&= \begin{bmatrix} 1 * \begin{bmatrix} 0 & 1 \\\ 1 & 0  \end{bmatrix}  & 0 * \begin{bmatrix} 0 & 1 \\\ 1 & 0  \end{bmatrix}  \\\ 0 * \begin{bmatrix} 0 & 1 \\\ 1 & 0  \end{bmatrix} & 1 * \begin{bmatrix} 0 & 1 \\\ 1 & 0  \end{bmatrix}   \end{bmatrix} \\
&= \begin{bmatrix} \begin{bmatrix} 0 & 1 \\\ 1 & 0  \end{bmatrix}  & \begin{bmatrix} 0 & 0 \\\ 0 & 0  \end{bmatrix}  \\\  \begin{bmatrix} 0 & 0 \\\ 0 & 0  \end{bmatrix} & \begin{bmatrix} 0 & 1 \\\ 1 & 0  \end{bmatrix}   \end{bmatrix} \\
&= \begin{bmatrix} 0 & 1 & 0 & 0 \\\ 1 & 0 & 0 & 0 \\\ 0 & 0 & 0 & 1 \\\ 0 & 0 & 1 & 0 \end{bmatrix} 
\end{aligned}$$


(c) tensor product of $X$ and $I$

$$\begin{aligned}
X \otimes I &= \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \otimes \begin{bmatrix} 1 & 0 \\\ 0 & 1  \end{bmatrix} \\
&= \begin{bmatrix} 0 * \begin{bmatrix} 1 & 0 \\\ 0 & 1  \end{bmatrix}   & 1 * \begin{bmatrix} 1 & 0 \\\ 0 & 1  \end{bmatrix}   \\\ 1 * \begin{bmatrix} 1 & 0 \\\ 0 & 1  \end{bmatrix} & 0 * \begin{bmatrix} 1 & 0 \\\ 0 & 1  \end{bmatrix} \end{bmatrix} \\
&= \begin{bmatrix} \begin{bmatrix} 0 & 0 \\\ 0 & 0  \end{bmatrix}   & \begin{bmatrix} 1 & 0 \\\ 0 & 1  \end{bmatrix}   \\\ \begin{bmatrix} 1 & 0 \\\ 0 & 1  \end{bmatrix} &  \begin{bmatrix} 0 & 0 \\\ 0 & 0  \end{bmatrix} \end{bmatrix} \\
&= \begin{bmatrix} 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & 1 \\\ 1 & 0 & 0 & 0 \\\ 0 & 1 & 0 & 0 \end{bmatrix} 
\end{aligned}$$


By comparing (b) and (c) we can see that the tensor product is not commutative.

</details>

**Exercise 2.28**

For this exercise you will confirm the distributive property of several operators over the tensor product. There are probably several different you could do this, but one method for the complex conjugate and transpose is to use the Kronecker product along with the properties of block matrices. The adjoint is just a combination of complex conjugation and the transpose, so you can use the distributive properties from those operations to show that the adjoint is also distributive.

<details>
<summary>Solution</summary>

Complex Conjugation

$$\begin{aligned}
\left( A \otimes B\right)^\ast &= \left( \begin{bmatrix} A_{11}B & A_{12}B & \dots & A_{1n}B \\\ A_{21}B & A_{22}B & \dots & A_{2n}B \\\ \vdots & \vdots & \vdots & \vdots \\ A_{m1}B & A_{m2}B & \dots & A_{mn}B   \end{bmatrix} \right)^\ast \\
&= \begin{bmatrix} A_{11}^\ast B^\ast & A_{12}^\ast B^\ast & \dots & A_{1n}^\ast B^\ast \\\ A_{21}^\ast B^\ast & A_{22}^\ast B^\ast & \dots & A_{2n}^\ast B^\ast \\\ \vdots & \vdots & \vdots & \vdots \\\ A_{m1}^\ast B^\ast & A_{m2}^\ast B^\ast & \dots & A_{mn}^\ast B^\ast   \end{bmatrix} \\
&= A^\ast \otimes B^\ast
\end{aligned}$$

therefore complex conjugation distributes over the tensor product.


Transpose

$$\begin{aligned}
\left( A \otimes B\right)^T &= \left( \begin{bmatrix} A_{11}B & A_{12}B & \dots & A_{1n}B \\\ A_{21}B & A_{22}B & \dots & A_{2n}B \\\ \vdots & \vdots & \vdots & \vdots \\\ A_{m1}B & A_{m2}B & \dots & A_{mn}B   \end{bmatrix} \right)^T \\
&= \begin{bmatrix} A_{11}B^T & A_{21}B^T & \dots & A_{n1}B^T \\\ A_{12}^\ast B^T & A_{22}B^T & \dots & A_{n2}B^T \\\ \vdots & \vdots & \vdots & \vdots \\\ A_{1m}B^T & A_{2m}B^T & \dots & A_{nm}B^T   \end{bmatrix} \\
&= A^T \otimes B^T
\end{aligned}$$

therefore transpose distributes over the tensor product.


Adjoint 

$\left( A \otimes B\right)^\dagger = \left( \left(A \otimes B\right)^\ast \right)^T=\left( A^\ast \otimes B^\ast \right)^T= (A^\ast)^T \otimes (B^\ast)^T =A^\dagger \otimes B^\dagger$ therefore adjoint distributes over the tensor product.

</details>

**Exercise 2.29**

Use the definition of a unitary operator to show that the tensor product of two unitary operators is unitary.

<details>
<summary>Solution</summary>

We need to show $(A \otimes B)^\dagger (A \otimes B) = I$ when $A$ and $B$ are both unitary. 

$$\begin{aligned}
(A \otimes B)^\dagger (A \otimes B) &= (A^\dagger \otimes B^\dagger) (A \otimes B) & \text{distributivity of the adjoint}\\
&= A^\dagger A \otimes B^\dagger B & \text{tensor product distributes over matrix multiplication}\\
&= I \otimes I  & \text{definition of unitary operator}
\end{aligned}$$

If $I \otimes I = I$ then $A \otimes B$ is unitary. Using the Kronecker product,

$$\begin{aligned}
I \otimes I &= \begin{bmatrix} I & 0 & 0 & \dots & 0 \\\ 0 & I & 0 & \dots & 0 \\\ 0 & 0 & I & \dots & 0 \\\ \vdots & \vdots & \vdots & \ddots & \vdots \\\ 0 & 0 & 0 & \dots & I \end{bmatrix} = I
\end{aligned}$$

Therefore $A \otimes B$ is unitary.

</details>

**Exercise 2.30**

Use the definition of a Hermitian operator to show that the tensor product of two Hermitian operators is Hermitian.

<details>
<summary>Solution</summary>

We need to show that $(A \otimes B)^\dagger = (A \otimes B)$ when $A$ and $B$ are both Hermitian. 

$(A \otimes B)^\dagger = A^\dagger \otimes B^\dagger = A \otimes B$

Therefore $A \otimes B$ is Hermitian.

</details>

**Exercise 2.31**

Use the definition of a positive operator to show that the tensor product of two positive operators is positive.

<details>
<summary>Solution</summary>

We need to show that $\left( \ket{a} \otimes \ket{b}, (A \otimes B)(\ket{a} \otimes \ket{b})\right)$ is a real, non-negative number when $A$ and $B$ are positive. 

$$\begin{aligned}
\left( \ket{a} \otimes \ket{b}, (A \otimes B)(\ket{a} \otimes \ket{b})\right) &= \left( \ket{a} \otimes \ket{b}, A\ket{a} \otimes B\ket{b} \right) & \text{by equation 2.45}\\
&= \braket{a \vert A \vert a} \braket{b \vert B \vert b} & \text{by equation 2.49}
\end{aligned}$$

Since both $A$ and $B$ are positive operators, we know that $\braket{a \vert A \vert a}$ and $\braket{b \vert B \vert b}$ are real, non-negative numbers. Therefore $\braket{a \vert A \vert a} \braket{b \vert B \vert b}$ is a real non-negative number and so $A \otimes B$ is positive. 

</details>

**Exercise 2.32**

Use the definition of a projector to show that the tensor product of two projector is a projector.

<details>
<summary>Solution</summary>

From exercise 2.16 we know that any projector $P$ satisfies the equation $P^2 = P$. Lets say we have two projectors $P_1$ and $P_2$, then lets check the square of their tensor product 

$$\begin{aligned}
(P_1 \otimes P_2)^2 &= (P_1 \otimes P_2)(P_1 \otimes P_2) \\
&= P_1^2 \otimes P_2^2 & \text{tensor product distributes over matrix multiplication}\\
&= P_1 \otimes P_2 & \text{definition of $P$}
\end{aligned}$$

Therefore the tensor product of two projectors is a projector. 

</details>

**Exercise 2.33**

For this exercise you are asked to confirm that the Hadamard transform can be written as equation 2.55. One thing that can be confusing about this is that equation 2.55 is now well defined, i.e. it is not stated what the different variables represent. I found it useful to refer to section 1.4.4 where the Hadamar transform is discussed in more detail to better understand equation 2.55. From there you can confirm the $n=1$ case matches equation 2.55 and then use that to confirm the arbitrary $n$ case. 

<details>
<summary>Solution</summary>

First let's look a little closer at the $n=1$ case

$$\begin{aligned}
H &= \frac{1}{\sqrt{2}} \lbrack(\ket{0} + \ket{1})\bra{0} + (\ket{0} - \ket{1})\bra{1}\rbrack \\
&= \frac{1}{\sqrt{2}} \lbrack \ket{0}\bra{0}  + \ket{1}\bra{0} + \ket{0}\bra{1} - \ket{1}\bra{1} \rbrack
\end{aligned}$$

This matches equation 2.55 with $x$ and $y$ spanning the values $\ket{0}$ and $\ket{1}$ and $x \cdot y$ representing the bitwise inner product of $x$ and $y$. 

Now let's show explicitly that the Hadamard transform on $n$ qubits can be written as equation 2.55. We've already shown how the $n=1$ case can be written as $H = \frac{1}{\sqrt{2} }\sum_{x,y} (-1)^{xy} \ket{x}\bra{y}$. The arbitrary $n$ case can then be written as

$$\begin{aligned}
H^{\otimes n} &= \frac{1}{\sqrt{2}} \sum_{x_1,y_1} (-1)^{x_1y_1} \ket{x_1}\bra{y_1} \otimes \frac{1}{\sqrt{2}} \sum_{x_2,y_2} (-1)^{x_2y_2} \ket{x_2}\bra{y_2} \otimes \cdots \otimes \frac{1}{\sqrt{2} }\sum_{x_n,y_n} (-1)^{x_ny_n} \ket{x_n}\bra{y_n} \\
&= \frac{1}{\sqrt{2^n}} \sum_{x_1,x_2,\cdots, x_n, y_1, y_2, \cdots, y_n} (-1)^{x_1 y_1 + x_2 y_2 + \cdots + x_n y_n}\ket{x_1 x_2 \cdots x_n}\bra{y_1 y_2 \cdots y_n} \\
&= \frac{1}{\sqrt{2^n}} \sum_{x,y} (-1)^{x \cdot y}\ket{x}\bra{y}
\end{aligned}$$

Now let's write out the matrix representation for $H^{\otimes 2}$.

$$\begin{aligned}
H^{\otimes 2} &= \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \otimes \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \\
&= \begin{bmatrix} \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} & \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \\\ \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} & \begin{bmatrix} -1 & -1 \\\ -1 & 1 \end{bmatrix} \end{bmatrix} \\
& = \begin{bmatrix} 1 & 1 & 1 & 1 \\\ 1 & -1 & 1 & -1 \\\ 1 & 1 & -1 & -1 \\\ 1 & -1 & -1 & 1 \end{bmatrix}
\end{aligned}$$

</details>

**Exercise 2.34**

In section 2.1.8 the authors introduce the concept of operator functions and describe how to calculate them. In this exercise you get practice performing that calculation on a given matrix. Since this matrix is not in diagonal representation, you will first need to find its diagonal representation, then execute the operation on its eigen values, and then reconstruct the operator in matrix representation. 

<details>
<summary>Solution</summary>

We know that $f(A) \equiv \sum_{a} f(a) \ket{a} \bra{a}$ for $A = \sum_{a} a \ket{a}\bra{a}$. Since the given matrix is not diagonal, we'll need to diagonalize it. So first we'll find the eigenvalues

$$\begin{aligned}
0 &= \text{det} \left(\begin{bmatrix} 4 & 3 \\\ 3 & 4 \end{bmatrix} - \lambda \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) \\
&= \text{det} \left(\begin{bmatrix} 4 - \lambda & 3 \\\ 3 & 4 - \lambda \end{bmatrix} \right) \\
&= (4-\lambda)^2 - 9 \\
&= \lambda^2 - 8 \lambda + 7 \\
\lambda &= \frac{8 \pm \sqrt{64 - 4 \* 1 \* 7}}{2 \* 1} \\
&= 4 \pm 3
\end{aligned}$$

Now we find the eigenvectors

$$\begin{aligned}
\begin{bmatrix} 0 \\\ 0 \end{bmatrix} &= \left(\begin{bmatrix} 4 & 3 \\\ 3 & 4 \end{bmatrix} - \lambda \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} 4 - \lambda & 3 \\\ 3 & 4 - \lambda \end{bmatrix}  \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} (4 - \lambda) x_1 + 3 x_2 \\\ 3 x_1 + (4-\lambda) x_2 \end{bmatrix} 
\end{aligned}$$

For $\lambda = 7$ we get

$$\begin{aligned}
\begin{bmatrix} 0 \\\ 0 \end{bmatrix} &= \begin{bmatrix} -3 x_1 + 3 x_2 \\\ 3 x_1 -3 x_2 \end{bmatrix} 
\end{aligned}$$

Which is true when $x_1 = x_2$ so $\ket{e_1} = (\frac{1}{\sqrt{2}}, \frac{1}{\sqrt{2}})$ is a normalized eigenvector with eigenvalue $7$.

For $\lambda = 1$ we get

$$\begin{aligned}
\begin{bmatrix} 0 \\\ 0 \end{bmatrix} &= \begin{bmatrix}  3 x_1 + 3 x_2 \\\ 3 x_1 + 3 x_2 \end{bmatrix} 
\end{aligned}$$

Which is true when $x_1 = -x_2$ so $\ket{e_2} = (\frac{1}{\sqrt{2}}, -\frac{1}{\sqrt{2}})$ is a normalized eigenvector with eigenvalue $1$.

Putting it all together, the spectral decomposition is

$$\begin{aligned}
A = 7 \ket{e_1}\bra{e_1} + \ket{e_2}\bra{e_2}
\end{aligned}$$

Therefore $f(A)$ is

$$\begin{aligned}
f(A) &= f(7) \ket{e_1}\bra{e_1} + f(1) \ket{e_2}\bra{e_2} \\
&= f(7) \begin{bmatrix} \frac{1}{\sqrt{2}} \\\ \frac{1}{\sqrt{2}} \end{bmatrix} \begin{bmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \end{bmatrix} + f(1)\begin{bmatrix} \frac{1}{\sqrt{2}} \\\ -\frac{1}{\sqrt{2}} \end{bmatrix} \begin{bmatrix} \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} \end{bmatrix} \\
&= \frac{f(7)}{2} \begin{bmatrix} 1 & 1 \\\ 1 & 1 \end{bmatrix} + \frac{f(1)}{2} \begin{bmatrix} 1 & -1 \\\ -1 & 1 \end{bmatrix} \\
&= \frac{1}{2} \begin{bmatrix} f(7) + f(1) & f(7) - f(1) \\\ f(7) - f(1) & f(7) + f(1) \end{bmatrix}
\end{aligned}$$

To find the square root

$$\begin{aligned}
\sqrt{A} = \frac{1}{2} \begin{bmatrix} \sqrt{7} + \sqrt{1} & \sqrt{7} - \sqrt{1} \\\ \sqrt{7} - \sqrt{1} & \sqrt{7} + \sqrt{1} \end{bmatrix} = \frac{1}{2} \begin{bmatrix} \sqrt{7} + 1 & \sqrt{7} - 1 \\\ \sqrt{7} - 1 & \sqrt{7} + 1 \end{bmatrix} 
\end{aligned}$$

To find the log

$$\begin{aligned}
\ln{A} = \frac{1}{2} \begin{bmatrix} \ln{7} + \ln{1} & \ln{7} - \ln{1} \\\ \ln{7} - \ln{1} & \ln{7} + \ln{1} \end{bmatrix} =\frac{\ln{7} }{2} \begin{bmatrix} 1 & 1  \\\ 1  & 1 \end{bmatrix}
\end{aligned}$$

</details>

**Exercise 2.35**

In this exercise you will confirm the exponential of the Pauli matrices. To do this, you'll need to find the diagonal representation of $\vec{v} \cdot \vec{\sigma}$, then use Euler's formula and the operator function calculation.

<details>
<summary>Solution</summary>

First let's calculate $\vec{v} \cdot \vec{\sigma}$, where $\vec{\sigma}$ are the Pauli matrices. 

$$\begin{aligned}
\vec{v} \cdot \vec{\sigma} &\equiv \sum_{i=1}^{3} v_i \sigma_i \\
& = v_1 \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} + v_2 \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} + v_3 \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \\
&= \begin{bmatrix} v_3 & v_1 - i v_2 \\\ v_1 + i v_2 & -v_3 \end{bmatrix}
\end{aligned}$$

Now let's find the diagonal representation by first finding the eigenvalues.

$$\begin{aligned}
0 &= det \left( \begin{bmatrix} v_3 & v_1 - i v_2 \\\ v_1 + i v_2 & -v_3 \end{bmatrix} - \lambda \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) \\
&= det \left(\begin{bmatrix} v_3 - \lambda & v_1 - i v_2 \\\ v_1 + i v_2 & -v_3 - \lambda \end{bmatrix} \right) \\
&= (v_3 - \lambda)(-v_3 - \lambda) - (v_1 - i v_2)(v_1 + i v_2) \\
&= \lambda^2 - v_3^2 - v_1^2 - v_2^2 \\
\lambda &= \pm \sqrt{v_1^2 + v_2^2 + v_3^2} = \pm 1
\end{aligned}$$

Then we'll find the eigenvectors.

$$\begin{aligned}
\begin{bmatrix} 0 \\\ 0 \end{bmatrix} &=  \begin{bmatrix} v_3 - \lambda & v_1 - i v_2 \\\ v_1 + i v_2 & -v_3 - \lambda \end{bmatrix}  \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} (v_3 - \lambda) x_1 + (v_1 - i v_2) x_2 \\\ (v_1 + i v_2) x_1 + (-v_3 - \lambda) x_2 \end{bmatrix} 
\end{aligned}$$

Solving for $x_1$ and $x_2$ we get

$$\begin{aligned}
\begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} = \begin{bmatrix} v_3 + \lambda  \\\ v_1 + i v_2 \end{bmatrix} 
\end{aligned}$$

Which gives eigenvectors $\ket{\lambda_+}= (v_3 + 1, v_1 + i v_2)$ and $\ket{\lambda_-}= (v_3 - 1, v_1 + i v_2)$ 

Now we can write 

$$\begin{aligned}
\vec{v} \cdot \vec{\sigma} = \ket{\lambda_+}\bra{\lambda_+} - \ket{\lambda_-}\bra{\lambda_-}
\end{aligned}$$

Using the above along with Euler's formula we get

$$\begin{aligned}
\exp(i \theta \vec{v} \cdot \vec{\sigma}) &= \cos(\theta \vec{v} \cdot \vec{\sigma}) + i \sin(\theta \vec{v} \cdot \vec{\sigma}) \\
&= \cos(\theta)\ket{\lambda_+}\bra{\lambda_+} + \cos(-\theta)\ket{\lambda_-}\bra{\lambda_-} + i \sin(\theta)\ket{\lambda_+}\bra{\lambda_+}+ i \sin(-\theta)\ket{\lambda_-}\bra{\lambda_-} \\
&= \cos(\theta) \ket{\lambda_+}\bra{\lambda_+} + \cos(\theta) \ket{\lambda_-}\bra{\lambda_-} + i \sin(\theta) \ket{\lambda_+}\bra{\lambda_+}- i \sin(\theta) \ket{\lambda_-}\bra{\lambda_-} \\
&= \cos(\theta) (\ket{\lambda_+}\bra{\lambda_+} +\ket{\lambda_-}\bra{\lambda_-} )+ i \sin(\theta) (\ket{\lambda_+}\bra{\lambda_+}- \ket{\lambda_-}\bra{\lambda_-}) \\
&= \cos(\theta) I + i \sin(\theta)  \vec{v} \cdot \vec{\sigma}
\end{aligned}$$


Well, it looks like we didn't need to calculate the eigenvectors for this proof, but I'm going to leave them in here in case we need them later. 

</details>

**Exercise 2.36**

In section 2.1.8 the authors introduce the concept of the trace. Use the definition of the trace to calculate the trace of the Pauli matrices. 

<details>
<summary>Solution</summary>

The trace of a matrix is given by $\text{tr}(A) \equiv \sum_{i} A_{ii}$, therefore the trace of the Pauli matrices are

$$\begin{aligned}
\text{tr}(X) &= \text{tr} \left( \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \right) = 0 + 0 = 0 \\
\text{tr}(Y) &= \text{tr}\left( \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \right) = 0 + 0 = 0 \\
\text{tr}(Z) &= \text{tr} \left( \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \right) = 1 - 1 = 0 \\
\text{tr}(I) &= \text{tr} \left( \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) = 1 + 1 = 2 & \text{this will $=d$ where $d$ is the dimension}
\end{aligned}$$

</details>

**Exercise 2.37**

For this exercise you use the definition of the trace and the definition of matrix multiplication to demonstrate that $\text{tr}(AB) = \text{tr}(BA)$.

<details>
<summary>Solution</summary>

From the definition of matrix multiplication we know that the matrix product $C=AB$ has entries defined by 

$$\begin{aligned}
C_{ij} = \sum_{k} A_{ik} B_{kj}
\end{aligned}$$

and the matrix product $D=BA$ has entries defined by

$$\begin{aligned}
D_{ij} = \sum_{k} B_{ik} A_{kj}
\end{aligned}$$

The trace of $AB$ is given by 

$$\begin{aligned}
\text{tr}(AB) &= \sum_{i} C_{ii}  & \text{definition of trace}\\
&= \sum_{i} \sum_{k} A_{ik} B_{ki} & \text{definition of matrix multiplication} \\
&= \sum_{i} \sum_{k} B_{ki} A_{ik} & \text{scalar multiplication commutativity}\\
&= \sum_{k} D_{kk} & \text{definition of matrix multiplication} \\
&= \text{tr}(BA) & \text{definition of trace}
\end{aligned}$$

</details>

**Exercise 2.38**

For this exercise you use the definition of the trace and the definition of matrix addition to demonstrate that $\text{tr}(A+B) = \text{tr}(A) + \text{tr}(B)$. You will also use the definition of the trace to demonstrate that $\text{tr}(zA) = z \text{tr}(A)$.

<details>
<summary>Solution</summary>

From the definition of matrix addition we know that the matrix $C=A+B$ has entries defined by

$$\begin{aligned}
C_{ij} = A_{ij} + B_{ij}
\end{aligned}$$

The trace of $A+B$ is

$$\begin{aligned}
\text{tr}(A+B) &= \text{tr}(C) \\
&= \sum_{i} C_{ii} & \text{definition of trace}\\
&= \sum_{i} A_{ii} + B_{ii} & \text{definition of matrix addition} \\
&= \sum_{i} A_{ii} + \sum_{i} B_{ii} & \text{summation associativity}\\
&=\text{tr}(A) + \text{tr}(B) & \text{definition of trace}
\end{aligned}$$


For arbitrary complex number $z$

$$\begin{aligned}
\text{tr}(zA) &= \sum_{i} zA_{ii} & \text{definition of trace}\\
&= z \sum_{i} A_{ii} & \text{summation distributivity}\\
&= z \text{tr}(A) & \text{definition of trace}
\end{aligned}$$

</details>

**Exercise 2.39**

(1) in order to show that $(A,B)$ is an inner product we need to go back to section 2.1.4 to get the requirements for an inner product, which are: linear in the second argument, conjugate symmetry, and positive semi-definiteness. To check for linearity in the second argument let's look at

$$\begin{aligned}
(A, zB) &= \text{tr}(A^\dagger zB) \\
&= z \text{tr}(A^\dagger B) \\
&= z (A, B)
\end{aligned}$$

For conjugate symmetry 

$$\begin{aligned}
(A, B)^\ast &= \text{tr}(A^\dagger B)^\ast \\
&= \text{tr}((A^T)^\ast B)^\ast \\
&= \text{tr}(A^T B^\ast) \\
&= \text{tr}((A^T B^\ast)^T) \\
&= \text{tr}(A B^\dagger) \\
&= \text{tr}(B^\dagger A) \\
&= (B, A)
\end{aligned}$$

And finally positive semi-definiteness

$$\begin{aligned}
(A, A) &= \text{tr}(A^\dagger A) \\
&= \sum_{i} \sum_{k} A_{ik}^\dagger A_{ki} \\
&= \sum_{i} \sum_{k} A^\ast_{ki}A_{ki} \\
&= \sum_{i} \sum_{k} \vert A_{ki} \vert^2 \geq 0
\end{aligned}$$


(2) if $L_V$ is a set of linear operators then for each operator in the set $A: V \rightarrow V$ and, per equation 2.12, can be represented as

$$\begin{aligned}
A \ket{v_j} = \sum_{i} A_{ij} \ket{v_i}
\end{aligned}$$

with $\ket{v_1}, \dots, \ket{v_d}$ being an othernormal basis for $V$ which has $d$ elements. Therefore $A$ needs to be a $d \times d$ matrix. In order to form a basis set of linear operators that span $L_V$ there needs to be $d^2$ linearly independent elements in the set. Therefore $L_V$ has dimensions $d^2$. 

(3) In order for the operators $A$ and $B$ to be linearly independent their inner product needs to be $0$. We know that

$$\begin{aligned}
(A, B) &= \text{tr} (A^\dagger B) \\
&= \text{tr} \left( \sum_{k} A^\dagger_{ik} B_{kj} \right) \\
&= \sum_{ik} A^\dagger_{ik} B_{ki} \\
&= \sum_{ik} A^\ast_{ki} B_{ki} 
\end{aligned}$$

Looking at the above results, it can easily be seen that one way to insure that $(A,B)=0$ is to set at least one of the elements $A_{ij}$ or $B_{ij}$ to $0$ for each $ij$. Expanding this to the entire basis set, the set is guaranteed to be linearly independent if only one of the basis matrices has a non-zero element for each $ij$. Therefore the following is a possible orthonormal basis set for $L_V$

$$\begin{aligned}
L_{Vij} = \sum_{i'j'} \delta_{ii'} \delta_{jj'} \ket{v_{j'}}\bra{v_{i'}} = \ket{v_{j}}\bra{v_{i}}
\end{aligned}$$
 

**Exercise 2.40**

$$\begin{aligned}
\lbrack X,Y \rbrack = XY - YX = \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} - \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} = \begin{bmatrix} i & 0 \\\ 0 & -i \end{bmatrix} - \begin{bmatrix} -i & 0 \\\ 0 & i \end{bmatrix} = 2i \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} = 2 i Z
\end{aligned}$$

$$\begin{aligned}
\lbrack Y,Z \rbrack = YZ - ZY = \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} - \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} = \begin{bmatrix} 0 & i \\\ i & 0 \end{bmatrix} - \begin{bmatrix} 0 & -i \\\ -i & 0 \end{bmatrix} = 2i \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} = 2 i X
\end{aligned}$$

$$\begin{aligned}
\lbrack Z,X \rbrack = ZX - XZ = \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} - \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} = \begin{bmatrix} 0 & 1 \\\ -1 & 0 \end{bmatrix} - \begin{bmatrix} 0 & -1 \\\ 1 & 0 \end{bmatrix} = 2 i \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} = 2 i Y
\end{aligned}$$


**Exercise 2.41**

$$\begin{aligned}
\{ X,Y \} = XY + YX = \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} + \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} = \begin{bmatrix} i & 0 \\\ 0 & -i \end{bmatrix} + \begin{bmatrix} -i & 0 \\\ 0 & i \end{bmatrix} = \begin{bmatrix} 0 & 0 \\\ 0 & 0 \end{bmatrix} = 0
\end{aligned}$$

$$\begin{aligned}
\{ Y,Z \} = YZ + ZY = \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} + \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} = \begin{bmatrix} 0 & i \\\ i & 0 \end{bmatrix} + \begin{bmatrix} 0 & -i \\\ -i & 0 \end{bmatrix} = \begin{bmatrix} 0 & 0 \\\ 0 & 0 \end{bmatrix} = 0
\end{aligned}$$

$$\begin{aligned}
\{ Z,X \} = ZX + XZ = \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} + \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} = \begin{bmatrix} 0 & 1 \\\ -1 & 0 \end{bmatrix} + \begin{bmatrix} 0 & -1 \\\ 1 & 0 \end{bmatrix} = \begin{bmatrix} 0 & 0 \\\ 0 & 0 \end{bmatrix} = 0
\end{aligned}$$


**Exercise 2.42**


$$\begin{aligned}
\lbrack A,B\rbrack &= AB - BA \\
\\{A,B\\} &= AB + BA \\
\lbrack A,B\rbrack + \\{A,B\\} &= AB - BA + AB + BA = 2AB \\
\Rightarrow AB &= \frac{\lbrack A,B\rbrack+ \\{A,B\\} }{2}
\end{aligned}$$


**Exercise 2.43**

Using the results from Exercises 2.19 and 2.40 - 2.42 we know that

$$\begin{aligned}
\sigma_j \sigma_k &= \frac{\lbrack \sigma_j,\sigma_k \rbrack+ \{\sigma_j,\sigma_k\} }{2} \\
&= \frac{\sum_{l=1}^{3} 2 i \epsilon_{jkl} \sigma_l+ 2\delta_{jk} I }{2} \\
&=\sum_{l=1}^{3}  i \epsilon_{jkl} \sigma_l + \delta_{jk} I
\end{aligned}$$



**Exercise 2.44**

If $\lbrack A,B \rbrack = 0$ that means there must be a common orthonormal set of eigenvectors $\ket{i}$ for $A$ and $B$ such that $A=\sum_{i} a_i \ket{i}\bra{i}$ and $B=\sum_{i} b_i \ket{i}\bra{i}$. This means that

$$\begin{aligned}
\{A,B\}&=AB+BA \\
&= \sum_{i} a_i \ket{i}\bra{i} \sum_{j} b_j \ket{j}\bra{j} +  \sum_{j} b_j \ket{j}\bra{j} a_i \ket{i}\bra{i}\\
&= \sum_{ij} a_i b_j \ket{i}\braket{i \vert j}\bra{j} + a_i b_j \ket{j}\braket{j \vert i}\bra{i} \\
&= \sum_{ij} a_i b_j \delta_{ij} (\ket{i}\bra{j} + \ket{j}\bra{i} ) \\
&= \sum_{i} 2 a_i b_i \ket{i}\bra{i}
\end{aligned}$$

Which is only $0$ if either $a_i$ or $b_i$ is $0$ for each $i$. In order for matrix $A$ to be invertible $0$ cannot be an eigenvalue of $A$ per the Invertible Matrix Theorem. Therefore $b_i = 0$ for all $i$ and so $B=0$. 


**Exercise 2.45**

$\lbrack A,B \rbrack ^\dagger = (AB - BA)^\dagger = (AB)^\dagger - (BA)^\dagger = B^\dagger A^\dagger  -  A^\dagger B^\dagger = \lbrack B^\dagger, A^\dagger \rbrack$


**Exercise 2.46**

$\lbrack A,B \rbrack = AB-BA = -(BA-AB)=-\lbrack B,A \rbrack$


**Exercise 2.47**

If $A$ and $B$ are Hermitian it means that $A^\dagger = A$ and $B^\dagger=B$. With this in mind, we can check if $i \lbrack A,B \rbrack$ is Hermitian by taking the adjoint.

$$\begin{aligned}
\left(i \lbrack A,B \rbrack \right)^\dagger &= \left(i AB - i BA \right)^\dagger \\
&= -i (AB)^\dagger + i (BA)^\dagger \\
&= -i B^\dagger A^\dagger + i A^\dagger B^\dagger \\
&= -i BA + i AB \\
&= i (AB - BA) \\
&= i \lbrack A,B \rbrack
\end{aligned}

Therefore $i \lbrack A,B \rbrack$ is Hermitian.


**Exercise 2.48**

Polar decomposition is a method used to break a general linear operator up into products of unitary operators and positive operators. Since $P$ is already a positive operator, polar decomposition is not needed, though $P$ can be written as $P=IP=PI$ where the identity operator $I$ is a unitary operator. 

Similar to the case of $P$, $U$ is already one of the simpler matrix elements that polar decomposition is used to break a general linear operator up into. However, if desired $U$ can be written as $U=UI = IU$

For Hermitian matrix $H$ we know that $H^\dagger = H$ and $H= \sum_{i} \lambda_i \ket{i}\bra{i}$ and therefore

$$\begin{aligned}
H^\dagger H &= HH \\
&= \sum_{ii'} \lambda_i \lambda_{i'} \ket{i}\braket{i \vert i'}\bra{i'} \\
&= \sum_{i} \lambda_i^2 \ket{i}\bra{i}
\end{aligned}$$

For polar decomposition  $H=UJ=KU$ where \\
$J = \sqrt{H^\dagger H} = \sqrt{\sum_{i} \lambda_i^2 \ket{i}\bra{i}} = \sum_{i} \vert\lambda_i}\vert \ket{i}\bra{i} = K$\\
To find $U$ we find need to define a set of orthonormal basis vectors $\ket{e_i} \equiv H \ket{i}  / \vert\lambda_i\vert = \lambda_i \ket{i}/ \vert\lambda_i\vert$  for $\lambda_i \neq 0$ and then define $U \equiv \sum_{i} \ket{e_i}\bra{i}$. If one or more of the $\lambda_i = 0$ use the Gram-Schmidt procedure to extend the orthonormal set $\ket{e_i}$ to form an orthonormal basis. 


**Exercise 2.49**

Matrix $A$ is a normal matrix if $A^\dagger A = A A^\dagger$. It's spectral decomposition is $A=\sum_{i} \lambda_i \ket{i}\bra{i}$ therefore

$$\begin{algined}
A^\dagger A &=  \sum_{ii'} \lambda_i^* \lambda_{i'} \ket{i}\braket{i \vert i'}\bra{i'} \\
&= \sum_{i} \vert\lambda_i\vert^2 \ket{i}\bra{i}
\end{aligned}$$


$J = \sqrt{A^\dagger A} = \sqrt{\sum_{i} \vert\lambda_i\vert^2 \ket{i}\bra{i}} = \sum_{i} \vert\lambda_i\vert \ket{i}\bra{i} = K$\\
To find $U$ we find need to define a set of orthonormal basis vectors $\ket{e_i} \equiv A \ket{i}  / \vert\lambda_i\vert = \lambda_i \ket{i}/ \vert\lambda_i\vert$  for $\lambda_i \neq 0$ and then define $U \equiv \sum_{i} \ket{e_i}\bra{i}$. If one or more of the $\lambda_i = 0$ use the Gram-Schmidt procedure to extend the orthonormal set $\ket{e_i}$ to form an orthonormal basis. This differs from the results from the Hermitian matrix in Exercise 2.48 because $\lambda_i$ now can be complex and so $U$ not only represents the sign of $\lambda$ but also contains the direction in the complex plane. 


**Exercise 2.50**

Let $A = \begin{bmatrix} 1 & 0 \\\ 1 & 1 \end{bmatrix}$, therefore $A^\dagger = \begin{bmatrix} 1 & 1 \\\ 0 & 1 \end{bmatrix}$ and $A A^\dagger = \begin{bmatrix} 1 & 0 \\\ 1 & 1 \end{bmatrix} \begin{bmatrix} 1 & 1 \\\ 0 & 1 \end{bmatrix} = \begin{bmatrix} 1 & 1 \\\ 1 & 2 \end{bmatrix}$. In order to find the square root of $A A^\dagger$, we'll first need to write the matrix in diagonal representation. 

Let's find the eigenvalues

$$\begin{aligned}
0 &= \vert \begin{bmatrix} 1 & 1 \\\ 1 & 2 \end{bmatrix} - \begin{bmatrix} \lambda & 0 \\\ 0 & \lambda \end{bmatrix} \vert\\
&= \vert \begin{bmatrix} 1- \lambda & 1 \\\ 1 & 2-\lambda \end{bmatrix}\vert \\
&= (1-\lambda)(2 - \lambda) - 1 \\
&= \lambda^2 - 3 \lambda + 2 - 1 \\
&= \lambda^2 - 3 \lambda +1 \\
\Rightarrow \lambda &= \frac{3 \pm \sqrt{9 - 4 \* 1 \* 1}}{2 \* 1} = \frac{3 \pm \sqrt{5}}{2}
\end{aligned}$$


Then let's find the eigenvectors

$$\begin{aligned}
\begin{bmatrix} 0 \\\ 0 \end{bmatrix} &=  \left(\begin{bmatrix} 1 & 1 \\\ 1 & 2 \end{bmatrix} - \begin{bmatrix} \lambda & 0 \\\ 0 & \lambda \end{bmatrix} \right) \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix}\\
&=  \begin{bmatrix} 1- \lambda & 1 \\\ 1 & 2-\lambda \end{bmatrix} \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} (1- \lambda) x_1 +  x_2 \\\ x_1 + (2-\lambda) x_2 \end{bmatrix} \\
\Rightarrow \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} = \ket{e_i} &=  \frac{1}{\sqrt{1 + (1-\lambda_i)^2}}\begin{bmatrix} -1 \\\ 1-\lambda_i \end{bmatrix}
\end{aligned}$$


Then we can write 

$$\begin{aligned}
K = \sqrt{A A^\dagger} &= \sum_{i} \sqrt{\lambda_i} \ket{e_i}\bra{e_i} \\
&= \sum_{i}  \frac{\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2}\begin{bmatrix} -1 \\\ 1-\lambda_i \end{bmatrix} \begin{bmatrix} -1 & 1-\lambda_i \end{bmatrix} \\
&= \sum_{i}  \frac{\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2}\begin{bmatrix} 1 & -(1-\lambda_i) \\\ -(1-\lambda_i) & (1-\lambda_i)^2 \end{bmatrix} \\
&= \sum_{i}  \begin{bmatrix} \frac{\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2} & \frac{-(1-\lambda_i)\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2} \\\ \frac{-(1-\lambda_i)\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2} & \frac{(1-\lambda_i)^2\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2} \end{bmatrix} \\
&= \frac{1}{\sqrt{5}} \begin{bmatrix} 2 & 1 \\\  1 & 3 \end{bmatrix} 
\end{aligned}$$


Next, let's find $A^\dagger A$ and do the same thing. $A ^\dagger A = \begin{bmatrix} 1 & 1 \\\ 0 & 1 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 1 & 1 \end{bmatrix}  = \begin{bmatrix} 2 & 1 \\\ 1 & 1 \end{bmatrix}$

Let's find the eigenvalues

$$\begin{aligned}
0 &= \vert \begin{bmatrix} 2 & 1 \\\ 1 & 1 \end{bmatrix} - \begin{bmatrix} \lambda & 0 \\\ 0 & \lambda \end{bmatrix} \vert\\
&= \vert \begin{bmatrix} 2- \lambda & 1 \\\ 1 & 1-\lambda \end{bmatrix} \vert \\
&= (1-\lambda)(2 - \lambda) - 1 \\
&= \lambda^2 - 3 \lambda + 2 - 1 \\
&= \lambda^2 - 3 \lambda +1 \\
\Rightarrow \lambda &= \frac{3 \pm \sqrt{9 - 4*1*1}}{2*1} = \frac{3 \pm \sqrt{5}}{2}
\end{aligned}$$


Then let's find the eigenvectors

$$\begin{aligned}
\begin{bmatrix} 0 \\\ 0 \end{bmatrix} &=  \left(\begin{bmatrix} 2 & 1 \\\ 1 & 1 \end{bmatrix} - \begin{bmatrix} \lambda & 0 \\\ 0 & \lambda \end{bmatrix} \right) \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix}\\
&=  \begin{bmatrix} 2- \lambda & 1 \\\ 1 & 1-\lambda \end{bmatrix} \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} (2- \lambda) x_1 +  x_2 \\\ x_1 + (1-\lambda) x_2 \end{bmatrix} \\
\Rightarrow \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} = \ket{e_i} &=  \frac{1}{\sqrt{1 + (1-\lambda_i)^2}}\begin{bmatrix} 1-\lambda_i \\\ -1 \end{bmatrix}
\end{aligned}$$


Then we can write 

$$\begin{aligned}
J = \sqrt{A^\dagger A} &= \sum_{i} \sqrt{\lambda_i} \ket{e_i}\bra{e_i} \\
&= \sum_{i}  \frac{\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2}\begin{bmatrix} 1-\lambda_i \\\ -1 \end{bmatrix} \begin{bmatrix} 1-\lambda_i & -1 \end{bmatrix} \\
&= \sum_{i}  \frac{\sqrt{\lambda_i}}{(1-\lambda_i)^2 + (1-\lambda_i)^2}\begin{bmatrix} 1 & -(1-\lambda_i) \\\ -(1-\lambda_i) & 1 \end{bmatrix} \\
&= \sum_{i}  \begin{bmatrix} \frac{(1-\lambda_i)^2\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2} & \frac{-(1-\lambda_i)\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2} \\\ \frac{-(1-\lambda_i)\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2} & \frac{\sqrt{\lambda_i}}{1 + (1-\lambda_i)^2} \end{bmatrix} \\
&= \frac{1}{\sqrt{5}} \begin{bmatrix} 3 & 1 \\\  1 & 2 \end{bmatrix} 
\end{aligned}$$


If $J$ is invertible, then $U=AJ^{-1}$. Let's check if it is invertible

$$\begin{aligned}
J^{-1} &= \begin{bmatrix} \frac{3}{\sqrt{5}} & \frac{1}{\sqrt{5}} \\\  \frac{1}{\sqrt{5}} & \frac{2}{\sqrt{5}} \end{bmatrix}^{-1} \\
&= \frac{1}{\abs{J}} \begin{bmatrix} \frac{2}{\sqrt{5}} & -\frac{1}{\sqrt{5}} \\\  -\frac{1}{\sqrt{5}} & \frac{3}{\sqrt{5}} \end{bmatrix} \\
&= \frac{1}{\frac{2}{\sqrt{5}}\frac{3}{\sqrt{5}} -\frac{1}{\sqrt{5}} \frac{1}{\sqrt{5}} } \begin{bmatrix} \frac{2}{\sqrt{5}} & -\frac{1}{\sqrt{5}} \\\  -\frac{1}{\sqrt{5}} & \frac{3}{\sqrt{5}} \end{bmatrix} \\
&=\frac{1}{\frac{6-1}{5}\sqrt{5}} \begin{bmatrix} 2 & -1 \\\  -1 & 3 \end{bmatrix} \\
&=\frac{1}{\sqrt{5}} \begin{bmatrix} 2 & -1 \\\  -1 & 3 \end{bmatrix}
\end{aligned}$$

To confirm $J$ is invertible check that $J^{-1}J = I$

$$\begin{aligned}
J^{-1}J &= \frac{1}{5} \begin{bmatrix} 2 & -1 \\\  -1 & 3 \end{bmatrix} \begin{bmatrix} 3 & 1 \\\  1 & 2 \end{bmatrix} \\
&= \frac{1}{5} \begin{bmatrix} 5 & 0 \\\  0 & 5 \end{bmatrix} \\
&= \begin{bmatrix} 1 & 0 \\\  0 & 1 \end{bmatrix} \\
&= I
\end{aligned}$$

So $J$ is invertible and therefore 

$$\begin{aligned}
U &= A J^{-1} \\
&= \frac{1}{\sqrt{5}} \begin{bmatrix} 1 & 0 \\\ 1 & 1 \end{bmatrix} \begin{bmatrix} 2 & -1 \\\  -1 & 3 \end{bmatrix}  \\
&= \frac{1}{\sqrt{5}}  \begin{bmatrix} 2 & -1 \\\  1 & 2 \end{bmatrix}
\end{aligned}$$


Therefore

$$\begin{aligned}
A  &= UJ = \left(\frac{1}{\sqrt{5}}  \begin{bmatrix} 2 & -1 \\\  1 & 2 \end{bmatrix}\right) \left(\frac{1}{\sqrt{5}} \begin{bmatrix} 3 & 1 \\\  1 & 2 \end{bmatrix} \right) \\
&= KU = \left( \frac{1}{\sqrt{5}} \begin{bmatrix} 2 & 1 \\\  1 & 3 \end{bmatrix} \right)\left(\frac{1}{\sqrt{5}}  \begin{bmatrix} 2 & -1 \\\  1 & 2 \end{bmatrix}\right)
\end{aligned}$$


