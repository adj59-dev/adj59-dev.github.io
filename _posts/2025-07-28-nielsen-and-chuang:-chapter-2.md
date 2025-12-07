---
title: "Nielsen and Chuang: Chapter 2"
description: "Notes and exercise solutions for QCQI Chapter 2: linear algebra and quantum mechanics."
categories:
  - Quantum Computation and Quantum Information
permalink: /qcqi/chapter-2/
tags:
  - QCQI
  - quantum computing
  - Quantum Computation and Quantum Information
  - Nielsen & Chuang
  - chapter 2
  - exercise
  - problem
  - solutions
last_modified_at: 2025-12-05 19:10:00 -08:00
exercises:
  - anchor: exercise-21
    label: Exercise 2.1
  - anchor: exercise-22
    label: Exercise 2.2
  - anchor: exercise-23
    label: Exercise 2.3
  - anchor: exercise-24
    label: Exercise 2.4
  - anchor: exercise-25
    label: Exercise 2.5
  - anchor: exercise-26
    label: Exercise 2.6
  - anchor: exercise-27
    label: Exercise 2.7
  - anchor: exercise-28
    label: Exercise 2.8
  - anchor: exercise-29
    label: Exercise 2.9
  - anchor: exercise-210
    label: Exercise 2.10
  - anchor: exercise-211
    label: Exercise 2.11
  - anchor: exercise-212
    label: Exercise 2.12
  - anchor: exercise-213
    label: Exercise 2.13
  - anchor: exercise-214
    label: Exercise 2.14
  - anchor: exercise-215
    label: Exercise 2.15
  - anchor: exercise-216
    label: Exercise 2.16
  - anchor: exercise-217
    label: Exercise 2.17
  - anchor: exercise-218
    label: Exercise 2.18
  - anchor: exercise-219
    label: Exercise 2.19
  - anchor: exercise-220
    label: Exercise 2.20
  - anchor: exercise-221
    label: Exercise 2.21
  - anchor: exercise-222
    label: Exercise 2.22
  - anchor: exercise-223
    label: Exercise 2.23
  - anchor: exercise-224
    label: Exercise 2.24
  - anchor: exercise-225
    label: Exercise 2.25
  - anchor: exercise-226
    label: Exercise 2.26
  - anchor: exercise-227
    label: Exercise 2.27
  - anchor: exercise-228
    label: Exercise 2.28
  - anchor: exercise-229
    label: Exercise 2.29
  - anchor: exercise-230
    label: Exercise 2.30
  - anchor: exercise-231
    label: Exercise 2.31
  - anchor: exercise-232
    label: Exercise 2.32
  - anchor: exercise-233
    label: Exercise 2.33
  - anchor: exercise-234
    label: Exercise 2.34
  - anchor: exercise-235
    label: Exercise 2.35
  - anchor: exercise-236
    label: Exercise 2.36
  - anchor: exercise-237
    label: Exercise 2.37
  - anchor: exercise-238
    label: Exercise 2.38
  - anchor: exercise-239
    label: Exercise 2.39
  - anchor: exercise-240
    label: Exercise 2.40
  - anchor: exercise-241
    label: Exercise 2.41
  - anchor: exercise-242
    label: Exercise 2.42
  - anchor: exercise-243
    label: Exercise 2.43
  - anchor: exercise-244
    label: Exercise 2.44
  - anchor: exercise-245
    label: Exercise 2.45
  - anchor: exercise-246
    label: Exercise 2.46
  - anchor: exercise-247
    label: Exercise 2.47
  - anchor: exercise-248
    label: Exercise 2.48
  - anchor: exercise-249
    label: Exercise 2.49
  - anchor: exercise-250
    label: Exercise 2.50
  - anchor: exercise-251
    label: Exercise 2.51
  - anchor: exercise-252
    label: Exercise 2.52
  - anchor: exercise-253
    label: Exercise 2.53
  - anchor: exercise-254
    label: Exercise 2.54
  - anchor: exercise-255
    label: Exercise 2.55
  - anchor: exercise-256
    label: Exercise 2.56
  - anchor: exercise-257
    label: Exercise 2.57
  - anchor: exercise-258
    label: Exercise 2.58
  - anchor: exercise-259
    label: Exercise 2.59
  - anchor: exercise-260
    label: Exercise 2.60
  - anchor: exercise-261
    label: Exercise 2.61
  - anchor: exercise-262
    label: Exercise 2.62
  - anchor: exercise-263
    label: Exercise 2.63
  - anchor: exercise-264
    label: Exercise 2.64
  - anchor: exercise-265
    label: Exercise 2.65
  - anchor: exercise-266
    label: Exercise 2.66
  - anchor: exercise-267
    label: Exercise 2.67
  - anchor: exercise-268
    label: Exercise 2.68
  - anchor: exercise-269
    label: Exercise 2.69
  - anchor: exercise-270
    label: Exercise 2.70
  - anchor: exercise-271
    label: Exercise 2.71
  - anchor: exercise-272
    label: Exercise 2.72
  - anchor: exercise-273
    label: Exercise 2.73
  - anchor: exercise-274
    label: Exercise 2.74
  - anchor: exercise-275
    label: Exercise 2.75
  - anchor: exercise-276
    label: Exercise 2.76
  - anchor: exercise-277
    label: Exercise 2.77
  - anchor: exercise-278
    label: Exercise 2.78
  - anchor: exercise-279
    label: Exercise 2.79
  - anchor: exercise-280
    label: Exercise 2.80
  - anchor: problem-21
    label: Problem 2.1
  - anchor: problem-22
    label: Problem 2.2
  - anchor: problem-23
    label: Problem 2.3
chapter: 2
---

<a id="top"></a>

# Nielsen and Chuang: Chapter 2

I just finished reading Chapter 2 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. While the chapter serves as a brief introduction to quantum mechanics, much of it is devoted to linear algebra — with 50 out of 82 exercises focused on that topic. 

For me, the most valuable part was Section 2.1.7 on tensor products. I don’t recall covering tensor products in my undergraduate linear algebra course, so it was helpful to finally work through the formalism. It clarified a lot, especially given how central tensor products are to quantum computing.

The quantum mechanics portion was a good refresher, though some of the formalism here was also new to me. I'm glad I took the time to work through all the exercises, even though it was time-consuming. It helped reinforce concepts I’ll need later.

Below are my notes and solutions to the exercises.


## Navigation

{% assign headers = content | split: "<h" %}
{% for h in headers %}
  {% if h contains "</h2>" or h contains "</h3>" %}
    {% assign level = h | slice: 0, 1 %}
    {% assign text = h | split: ">" | last | split: "<" | first | strip | strip_newlines %}
    {% assign id = text
        | downcase
        | strip
        | strip_newlines
        | replace: " ", "-"
        | replace: ".", "" %}
    {% if level == "2" %}
* [{{ text }}](#{{ id }})
    {% elsif level == "3" %}
  * [{{ text }}](#{{ id }})
    {% endif %}
  {% endif %}
{% endfor %}





## Linear Algebra
  
### Exercise 2.1 {#exercise-21}

In section 2.1.1 the authors introduce the concept of linear dependence and independence. In this exercise you use the definition of linear dependence to demonstrate that three vectors are linearly dependent.




To show that these vectors are linearly dependent, we need to find a set of $a_1$, $a_2$, and $a_3$ such that

$$a_1 \begin{bmatrix} 1 \\\ -1 \end{bmatrix} + a_2 \begin{bmatrix} 1 \\\ 2 \end{bmatrix} + a_3 \begin{bmatrix} 2  \\\ 1 \end{bmatrix} = 0$$

This is true when $a_1=1, a_2=1,$ and $a_3=-1$. Therefore these vectors are linearly dependent.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.2 {#exercise-22}

In section 2.1.2 the authors talk about how linear operators can be represented as matrices. In this exercise you get practice representing a linear operator as a matrix. The first part of this exercise is straight forward, you just need to use the definition of the matrix representation of an operator, equation 2.12. The second part may be a bit more challenging if you haven't worked with the Pauli matrices before. I suggest reviewing section 1.3.3 if you are struggling with this exercise.



 
From definition of the matrix representation of an operator we know that

$$A \ket{v_j}=\sum_{i} A_{ij} \ket{v_i}$$

Given that $\ket{v_0}=\ket{0}$ and $\ket{v_1}=\ket{1}$ and that $A \ket{0}= \ket{1}$ and $A \ket{1} = \ket{0}$, we can say that $A_{00}=0$, $A_{01}=1$, $A_{10}=1$, and $A_{11}=0$. Therefore,

$$A = \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix}$$

Instead of using $\lbrace \ket{0}, \ket{1} \rbrace$ as the basis, let's use $\lbrace \ket{+}, \ket{-} \rbrace$. First we will calculate what the outputs are when $A$ acts on these vectors.

$$\begin{aligned}
A \ket{+} = A \frac{1}{\sqrt{2}} (\ket{0} + \ket{1})=\frac{1}{\sqrt{2}} (\ket{1} + \ket{0}) = \ket{+} \\
A \ket{-} = A \frac{1}{\sqrt{2}} (\ket{0} - \ket{1})=\frac{1}{\sqrt{2}} (\ket{1} - \ket{0}) = -\ket{-} 
\end{aligned}$$

For these basis vectors, $A$ is then represented as

$$A = \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.3 {#exercise-23}

This exercise provides further practice in representing linear operators as matrices. It also allows you to confirm for yourself that the matrix representation of a linear transformation $BA$ is a matrix product of the matrix representations of $B$ and $A$. To do this you'll once again use equation 2.12. You’ll also need the definition of matrix multiplication, which isn’t provided in the book, but is readily available online. Additionally, if it has been a while since you’ve work with the summation operator, reviewing common summation identities may be helpful, as they play a role in the derivation. 




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.4 {#exercise-24}

This is the final exercise focused on practicing how to represent linear operators as matrices. Here you will use equation 2.12 along with the definition of the identity operator given in section 2.1.2 ($I_V \ket{v} \equiv \ket{v}$) to confirm the matrix representation of the identity operator.




The matrix representation for $I$ will have entries with values $I_{ij}$ such that $I \ket{v_j}  = \sum_{i} I_{ij} \ket{v_i}$. Since we know that $I \ket{v_i} = \ket{v_i}$ for all $i$, $I_{ij} = 1$ when $i=j$ and $I_{ij} = 0$ when $i \neq j$. For a 2-dimensional vector space, the matrix representation for $I$ is

$$\begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.5 {#exercise-25}

In section 2.1.4 the authors introduce the concept of an inner product and list three requirements that need to be satisfied for something to be considered an inner product. In this exercise you need to show that $(\cdot, \cdot)$, which is given in equation 2.14, meet these three requirements.




(1) $(\cdot , \cdot)$ is linear in the second argument,

$$\begin{aligned}
\left(\ket{y}, \sum_{j}\lambda_j\ket{z_j}\right) & = \sum_{j} \lambda_j (\ket{y}, \ket{z_j}) & \text{this is the identity we want to prove} \\
& = \sum_{j} \lambda_j \sum_{i} y^\ast_i z_{j} & \text{inner product definition} \\
& = \sum_{j} \sum_{i} y^\ast_i \lambda_j z_{j} & \text{scalar multiplication distributivity} \\
& = \sum_{i} \sum_{j} y^\ast_i \lambda_j z_{j} & \text{summation operator commutativity} \\
& = \sum_{i} y^\ast_i \sum_{j} \lambda_j z_{j} & \text{scalar multiplication distributivity} \\
& = \left(\ket{y}, \sum_{j}\lambda_j\ket{z_j}\right) & \text{inner product definition} 
\end{aligned}$$

(2) Conjugate symmetry,

$$\begin{aligned} 
(\ket{y}, \ket{z}) & = (\ket{z}, \ket{y})^\ast & \text{this is the identity we want to prove}\\
&=\left(\sum_{i} z^\ast_iy_i \right)^\ast & \text{inner product definition}\\
&=\sum_{i} (z^\ast_i)^\ast  y_i^\ast & \text{complex conjugate distributivity}\\
&=\sum_{i} z_i  y_i^\ast & \text{$(a^\ast)^\ast = a$}\\
&=\sum_{i} y_i^\ast z_i  & \text{scalar multiplication commutativity}\\
&=(\ket{y}, \ket{z}) & \text{inner product definition}
\end{aligned}$$

(3) Positive semi-definiteness, $(\ket{y}, \ket{y}) \geq 0$ with equality if and only if $\ket{y}=0$. 

$$\begin{aligned}
(\ket{y}, \ket{y}) & = \sum_{i} y^\ast_i y_i & \text{this is the identity we want to prove}\\
& = \sum_{i} \left\vert y_i\right \vert^2 & \text{modulus definition}\\
& \geq 0 \text{ and only $=0$ when $\ket{y}$=0}
\end{aligned}$$

Since all three requirements are met, $( \cdot , \cdot)$ is an inner product. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.6 {#exercise-26}

For this exercise you will demonstrate that the inner product is conjugate-linear in the first argument using the properties that you just verified in the previous exercise.




$$\begin{aligned}
\left(\sum_{i} \lambda_i \ket{w_i}, \ket{v}\right) & = \sum_{i} \lambda^\ast_i (\ket{w_i}, \ket{v}) & \text{this is the identity we want to prove} \\
& = \sum_{i} \lambda^\ast_i (\ket{v}, \ket{w_i}) ^\ast & \text{conjugate symmetry}\\ 
& = \left(\ket{v}, \sum_{i} \lambda_i \ket{w_i}\right)^\ast  & \text{linear in the second argument}\\
&= \left(\sum_{i} \lambda_i \ket{w_i}, \ket{v}\right) & \text{conjugate symmetry }
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.7 {#exercise-27}

In section 2.1.4 the authors discuss orthogonal vectors, stating that vectors are orthogonal if their inner product is zero. They also define unit vectors and discuss how to normalize a vector to make it a unit vector. Here you will use that information to demonstrate that two vectors are orthogonal and calculate their normalized forms.  




These vectors are orthogonal if their inner product equals zero.

$$\braket{w \vert v}= \begin{bmatrix} 1 & 1 \end{bmatrix} \begin{bmatrix} 1 \\\ -1 \end{bmatrix}= 1-1=0$$

The normalized form of these vectors are 

$$\begin{aligned}
\ket{v_{norm}}=\frac{\ket{v}}{\Vert\ket{v} \Vert}=\frac{\ket{v}}{\sqrt{\braket{v \vert v}}}=\frac{\ket{v}}{\sqrt{1^2 + (-1)^2}}=\frac{1}{\sqrt{2}} \ket{v} \\
\ket{w_{norm}}=\frac{\ket{w}}{\Vert \ket{w} \Vert}=\frac{\ket{w}}{\sqrt{\braket{w \vert w}}}=\frac{\ket{w}}{\sqrt{1^2 + 1^2}}=\frac{1}{\sqrt{2}} \ket{w}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.8 {#exercise-28}

In section 2.1.4 the authors introduce the Gram-Schmidt procedure. Here you are asked to prove that the Gram-Schmidt procedure produces an orthonormal basis for $V$. This means that you'll need to prove several things: the vectors that are produced are unit vectors, they are orthogonal, and they form a basis for $V$. For this exercise, you will need to use proof by induction for at least one of these. 




The Gram-Schmidt procedure works as follows: define $\ket{v_1} \equiv \ket{w_1}/\Vert{\ket{w_1}}\Vert$ and for $1 \leq k \leq d-1$ define

$$\begin{aligned}
\ket{v_{k+1}} \equiv \frac{\ket{w_{k+1}} - \sum_{i=1}^{k} \braket{v_i \vert w_{k+1}}\ket{v_i}}{\Vert\ket{w_{k+1}} - \sum_{i=1}^{k} \braket{v_i \vert w_{k+1}} \ket{v_i}\Vert}
\end{aligned}$$

where $\ket{w_1},\dots,\ket{w_d}$ is a basis set for some vector space $V$. 

In order to be an orthonormal basis for $V$, all vectors must be unit vectors, they must be orthogonal i.e. $\braket{i \vert j}=\delta_{ij}$, and they must form a basis set for $V$. One can tell by the procedure definition that all vectors are unit vectors since all the calculations follow the form  $\ket{x}/\Vert\ket{x}\Vert$. 

To determine whether all vectors are orthogonal, let's first take the inner product of the first two vectors

$$\begin{aligned}
\braket{v_1 \vert v_2} & = \frac{\braket{v_1 \vert w_2} -  \braket{v_1 \vert w_2}\braket{v_1\vert v_1}}{\Vert\ket{w_{2}} - \braket{v_1 \vert w_2}\ket{v_1}\Vert} \\ 
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
\braket{v_j \vert v_4} & = \frac{\braket{v_j \vert w_4} - \sum_{i=1}^{3} \braket{v_i \vert w_4}\braket{v_j \vert v_i}}{\Vert\ket{w_4} - \sum_{i=1}^{k} \braket{v_i \vert w_4}\ket{v_i}\Vert}\\
& = \frac{\braket{v_j \vert w_4} - \braket{v_j \vert w_4}\braket{v_j \vert v_j}}{\Vert\ket{w_4} - \sum_{i=1}^{k} \braket{v_i \vert w_4}\ket{v_i}\Vert} & \text{Since $\braket{v_j \vert v_i}=0$ when $i \neq j$} \\
& = \frac{\braket{v_j \vert w_4} - \braket{v_j \vert w_4}}{\Vert\ket{w_4} - \sum_{i=1}^{k} \braket{v_i \vert w_4}\ket{v_i}\Vert} & \text{Since $\braket{v_j \vert v_j}=1$} \\
& = 0
\end{aligned}$$

So now we know that that $\braket{v_j \vert v_i}=0$ when $i \neq j$ for $j,i \le 4$. This same calculation can be applied to $\braket{v_j \vert w_5}$ for $j<5$, then $\braket{v_j \vert w_6}$ for $j<6$, and so on up to $\braket{v_j \vert w_d}$ for $j<d$. We then get that that $\braket{v_j \vert v_i}=0$ when $i \neq j$ for $j,i \le d$, demonstrating that the vectors are orthogonal. 

The final thing that we need to do is show that this orthonormal set of vectors is a basis for $V$. In order for a set of vectors to be a basis set it needs to be linearly independent and span the vector space $V$. Orthogonality of a set of nonzero vectors intrinsically implies their linear independence, so since this set of vectors is orthogonal we know that it is linearly independent. However, if desired, we can demonstrate this by assuming that the vector set is linearly dependent which would mean that there exists a set of complex numbers $a_1, \dots, a_d$ with $a_i \neq 0$ for at least one value of i, such that $a_1 \ket{v_1} + a_2 \ket{v_2} + \dots + a_d \ket{v_d} = 0$. In other words, we would be able to represent at least one of the vectors in the set, let's call it $\ket{v_j}$, as a linear combination of the other vectors in the set, 

$$\begin{aligned}
\ket{v_j} = \sum_{i=1}^{j-1} a_i \ket{v_i} + \sum_{i=j+1}^{d} a_i \ket{v_i}
\end{aligned}$$

Taking the inner product of both sides with $\ket{v_j}$ we get

$$\begin{aligned}
\braket{v_j \vert v_j} = \sum_{i=1}^{j-1} a_i \braket{v_j \vert v_i} + \sum_{i=j+1}^{d} a_i \braket{v_j \vert v_i} 
\end{aligned}$$

Which simplifies to $1 = 0$ because $\braket{v_j \vert v_i} = 0$ for $j \neq i$ due to its orthogonality. Since this is not true, the set cannot be linearly dependent. 

We know that this set of vectors spans $V$ because it has the same number of elements as the original basis set $\ket{w_1}, \dots, \ket{w_d}$ and any two sets of linearly independent vectors which span a vector space contain the same number of elements, as stated in section 2.1.1. Therefore $\ket{v_1}, \dots, \ket{v_d}$ as generated by the Gram-Schmidt procedure is an orthonormal basis for $V$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.9 {#exercise-29}

In section 2.1.4 the authors introduce outer product representation for linear operators. For this exercise you are asked to express each Pauli matrix in outer product notation. This can be done by using equation 2.25. The Pauli matrices are given in section 2.1.3.




We can find their expression in outer product notation using equation 2.25, $A=\sum_{ij} \braket{w_j \vert A \vert v_i} \ket{w_j} \bra{v_i}$. As stated in the book, $\braket{w_j \vert A \vert v_i}$ equals the element in the $i \text{th}$ column and $j \text{th}$ row of the matrix representation of the operator, so it is possible to just read these values from the matrix or you can calculate them as shown below. 

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
Z &= \braket{0 \vert Z \vert 0} \ket{0} \bra{0} + \braket{0 \vert Z \vert 1} \ket{0} \bra{1} + \braket{1 \vert Z \vert 0} \ket{1} \bra{0} + \braket{1 \vert Z \vert 1} \ket{1} \bra{1} \\
&= \braket{0 \vert 0} \ket{0} \bra{0} - \braket{0 \vert 1} \ket{0} \bra{1} + \braket{1 \vert 0} \ket{1} \bra{0} - \braket{1 \vert 1} \ket{1} \bra{1} \\
&=  \ket{0} \bra{0} - \ket{1} \bra{1} 
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.10 {#exercise-210}

This exercise provides more practice with outer product notation. This time you will use equation 2.25 to find the matrix representation for an operator that is given in outer product notation. 




From equation 2.25 we can write $A=\sum_{mn} \braket{v_m \vert A \vert v_n} \ket{v_m} \bra{v_n} = \ket{v_j} \bra{v_k}$. Which means that we need $\braket{v_m \vert A \vert v_n} = 1$ when $m=j$ and $n=k$ and $\braket{v_m \vert A \vert v_n} = 0$ otherwise. This means the matrix representation has 1 for the $A_{jk}$ element and 0 for all other elements.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.11 {#exercise-211}

In this exercise you are asked to find the eigenvectors, eigenvalues, and diagonal representations of the Pauli matrices $X$, $Y$, and $Z$. The book explains how to calculate the eigenvalues by using the characteristic equation for operators that are in the matrix representation, but it assumes that you’re already familiar with how to find the corresponding eigenvectors. 

If you are unsure or need a refresher, here is a brief summary of the procedure: once you find an eigenvalue $\lambda$, you can solve the equation $0 = (A-\lambda I)\ket{e}$ to find eigenvector $\ket{e}$ where $A$ is the operator (in matrix form) and $I$ is the identity matrix. 

Once you have a full set of eigenvalues and eigenvectors, you can write the operator in diagonal representation using the form $A = \sum_{i} \ket{i} \bra{i}$, where vectors $\ket{i}$ form an orthonormal set of eigenvectors. 





Z is already in a diagonal representation, so the eigenvectors and eigenvalues can be easily seen,

$$\begin{aligned}
Z = \ket{0}\bra{0} - \ket{1}\bra{1}
\end{aligned}$$

With the eigenvectors $\ket{0}$, $\ket{1}$ and corresponding eigenvalues 1, -1. 

X can be diagonalized by converting to the basis set $\ket{+}$ and $\ket{-}$, like we did in [Exercise 2.2](#exercise-22)

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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.12 {#exercise-212}

For this exercise you need to prove that a specific matrix is not diagonalizable. In section 2.1.5 we are told that an operator is diagonalizable if it has diagonal representation. So to prove that it is not diagonalizable, you need to show that it does not have diagonal representation.




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.13 {#exercise-213}

In section 2.1.6 the authors introduce the adjoint of operators. For this exercise we are asked to show that $(\ket{w}\bra{v})^\dagger = \ket{v}\bra{w}$, this can be done using equation 2.32 and some of the properties of inner products that we've already identified.




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.14 {#exercise-214}

We are asked to show that the adjoint operation is anti-linear, this can be done using equation 2.32 and some of the properties of inner products that we've already identified. 




Plugging this operator into equation 2.32 we get

$$\begin{aligned}
\left(\left( \sum_{i} a_i A_i \right)^\dagger \ket{x}, \ket{y}\right) &= \left(\ket{x}, \left( \sum_{i} a_i A_i \right) \ket{y}\right) & \text{Adjoint definition}\\
&= \sum_{i} a_i \left(\ket{x}, A_i \ket{y}\right) & \text{linearity in the second argument}\\
&= \sum_{i} a_i \left(A_i^\dagger \ket{x}, \ket{y}\right) & \text{Adjoint definition}\\
&= \left(\left(\sum_{i} a_i^\ast A_i^\dagger \right) \ket{x}, \ket{y}\right) & \text{conjugate-linearity in the first argument}
\end{aligned}$$

From the first and last line it can be seen that $\left( \sum_{i} a_i A_i \right)^\dagger = \sum_{i} a_i^\ast A_i^\dagger$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.15 {#exercise-215}

We are asked to show that $(A^\dagger)^\dagger = A$, this can be done using equation 2.32 and some of the properties of inner products that we've already identified. 




Lets plug $A^\dagger$ in for $A$ in equation 2.32

$$\begin{aligned}
\left(\left( A^\dagger \right)^\dagger \ket{x}, \ket{y}\right) &= \left(\ket{x}, \left( A^\dagger \right) \ket{y}\right) & \text{Adjoint definition}\\
&= \left(\left( A^\dagger \right) \ket{y}, \ket{x}\right)^\ast & \text{conjugate symmetry}\\
&= \left(\ket{y}, A \ket{x}\right)^\ast & \text{Adjoint definition}\\
&= \left(A \ket{x}, \ket{y} \right) & \text{conjugate symmetry}
\end{aligned}$$

From the first and last line it can be seen that $(A^\dagger)^\dagger = A$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.16 {#exercise-216}

In section 2.1.6 the authors introduce the concept of projectors. For this exercise you use the definition of projector $P$ from equation 2.35 and basis vector orthogonality to demonstrate the $P^2=P$. 




From equation 2.35 we know that $P$ is defined as $P \equiv \sum_{i=1}^k \ket{i} \bra{i}$ and so $P^2$ is 

$$\begin{aligned}
P^2 &= PP \\
&= \sum_{i=1}^k \ket{i} \bra{i} \sum_{j=1}^k \ket{j} \bra{j} & \text{definition of $P$}\\
&= \sum_{i=1}^k \sum_{j=1}^k  \ket{i} \braket{i \vert j} \bra{j} & \text{summation operator distributivity}\\
&= \sum_{i=1}^k \sum_{j=1}^k  \ket{i} \bra{j} \delta_{ij} & \text{vector orthogonality}\\
&= \sum_{i=1}^k  \ket{i} \bra{i} & \text{delta function execution}\\
&= P & \text{definition of $P$}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.17 {#exercise-217}

In this exercise we are asked to explore the relationship between normal and Hermitian matrices. For this you will use spectral decomposition, anti-linearity of the adjoint, and the results from [exercise 2.13](#exercise-213). 




Operator $A$ is a normal matrix if it is diagonal with respect to some orthonormal basis (per spectral decomposition). Therefore $A$ can be written as $A=\sum_{i} \lambda_{i} \ket{i} \bra{i}$ where $\lambda_{i}$ are the eigenvalues of $A$ and $\ket{i}$ is an orthonormal basis. It then follows that

$$\begin{aligned}
A^\dagger &= \left(\sum_{i} \lambda_{i} \ket{i} \bra{i}\right)^\dagger & \text{spectral decomposition}\\
&= \sum_{i} \lambda_{i}^\ast \left(\ket{i} \bra{i}\right)^\dagger & \text{anti-linearity of the adjoint}\\
&= \sum_{i} \lambda_{i}^\ast \ket{i} \bra{i} & \text{like exercise 2.13} \\
\end{aligned}$$

Operator $A$ is Hermitian if $A^\dagger = A$. From the above equation, it can been seen that this is only the case when $\lambda_i^* = \lambda_i$, i.e. when the operator only has real eigenvalues.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.18 {#exercise-218}

Here we show that all eigenvalues of a unitary matrix has modulus 1 using the definition of a unitary matrix, the outer product representation for $U$ and $I$, and vector orthogonality.




Since $U$ is a unitary matrix we know that $U^\dagger U = I$. We also know that U has spectral decomposition and so can be written $U \equiv \sum_i \lambda_i \ket{i} \bra{i}$. $I$ is defined as $I = \sum_i \ket{i} \bra{i}$. Therefore, 

$$\begin{aligned}
I &= U^\dagger U & \text{unitary matrix definition}\\
\sum_i \ket{i} \bra{i} &= \left( \sum_i \lambda_i \ket{i} \bra{i} \right)^\dagger \left(\sum_j \lambda_j \ket{j} \bra{j} \right) & \text{outer product representation}\\
&= \left( \sum_i \lambda_i^\ast \ket{i} \bra{i} \right) \left(\sum_j \lambda_j \ket{j} \bra{j} \right) & \text{adjoint definition}\\
&= \sum_i \sum_j \lambda_i^\ast \lambda_j  \ket{i} \braket{i \vert j} \bra{j} & \text{summation distributivity}\\
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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.19 {#exercise-219}

This exercise has you demonstrate that the Pauli matrices are Hermitian and unitary. To do this you just use the definition of Hermitian and unitary matrices and plug in the Pauli matrices. 




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.20 {#exercise-220}

For this exercise you are asked to find the relationship between two different matrix representations of operator $A$. This can be done using the completeness relation as shown in equation 2.23.




Using the completeness relation we know that $A = I_W A I_W$ and so

$$\begin{aligned}
A_{ij}' &= \braket{v_i \vert A \vert v_j} & \text{definition of $A_{ij}'$} \\
&= \braket{v_i \vert I_W A I_W \vert v_j} & \text{completeness relation} \\
&= \braket{v_i \vert \left(\sum_m \ket{w_m} \bra{w_m} \right) A \left(\sum_n \ket{w_n} \bra{w_n} \right) \vert v_j} & \text{outer product representation of $I$}\\
&= \sum_m \sum_n \braket{v_i \vert w_m} \braket{w_m \vert A \vert w_n} \braket{w_n \vert v_j} & \text{summation distributivity}\\
&= \sum_m \sum_n \braket{v_i \vert w_m} A_{mn}'' \braket{w_n \vert v_j} & \text{definition of $A_{ij}''$}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.21 {#exercise-221}

For this exercise we are asked to repeat the spectral decomposition proof, but with a Hermitian operator instead of a normal operator. There are a couple of places where simplifications can be made. One is when demonstrating that $PMQ = 0$ and then another when showing that $QMQ$ is normal. 




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.22 {#exercise-222}

In this exercise we are to prove that two eigenvectors of a Hermitian operator with different eigenvalues are orthogonal. To do this you can use equation 2.32, the fact that for a Hermitian operator $H=H^\dagger$, and properties of the inner product.




Let's assume we have two eigenvectors $\ket{v}$ and $\ket{w}$ of Hermitian operator $M$ with eigenvalues $\lambda_v$ and $\lambda_w$. From equation 2.32 we know that $(\ket{v}, M \ket{w}) = (M^\dagger \ket{v}, \ket{w})$. Since M is Hermitian $M^\dagger=M$ so $(\ket{v}, M \ket{w}) = (M \ket{v}, \ket{w})$ and therefore $(\ket{v}, \lambda_w \ket{w}) = (\lambda_v \ket{v}, \ket{w})$. Using linearity in the second and conjugate-linearity in the first arguments we get $\lambda_w(\ket{v}, \ket{w}) = \lambda_v^\ast( \ket{v}, \ket{w})$. As shown in [Exercise 2.17](#exercise-217), we know that the eigenvalues of a Hermitian operator are real and therefore $\lambda_w(\ket{v}, \ket{w}) = \lambda_v( \ket{v}, \ket{w})$. This can only be true if $\lambda_w = \lambda_v$ or $(\ket{v}, \ket{w}) =0$, i.e. the vectors are orthogonal. Therefore if $\lambda_w \neq \lambda_v$ then the vectors must be orthogonal. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.23 {#exercise-223}

Here we show that the eigenvalues of a projector are all either $0$ or $1$ by comparing the definition of $P$ to the diagonal representation for an operator. 




By definition $P \equiv \sum_{i=1}^k \ket{i} \bra{i}$ for a k-dimensional vector subspace of a d-dimensional vector space. This is a diagonal matrix which has the form $\sum_i \lambda_i \ket{i} \bra{i}$. By looking at the definition of $P$ and comparing it to the form of a diagonal matrix, one can easily see that $\lambda_i=1$ for $1 \leq i \leq k$ and $\lambda_i=0$ for $k < i \leq d$. Therefore the eigenvalues are all either 0 or 1.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.24 {#exercise-224}

For this exercise follow the hint’s advice and find Hermitian operators $B$ and $C$ that satisfies $A=B+iC$ for an arbitrary operator $A$. Then use the definition of a positive operator to find what constraints there are on $B$ and $C$ if $A$ is a positive operator. You will find that $A$ must be Hermitian. 




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.25 {#exercise-225}

To show that $A^\dagger A$ is positive, use the definition of a positive operator, equation 2.32, and the positive semi-definiteness of the inner product.




In order for $A^\dagger A$ to be positive $\left(\ket{v}, A^\dagger A \ket{v}\right)$ must be a real, non-negative number. 

$$\begin{aligned}
\left(\ket{v}, A^\dagger A \ket{v}\right) &= \left((A^\dagger)^\dagger \ket{v}, A \ket{v}\right) & \text{equation 2.32} \\
&= \left(A \ket{v}, A \ket{v}\right) & \text{from exercise 2.15}
\end{aligned}$$

Due to the positive semi-definiteness of inner products, we know that $\left(A \ket{v}, A \ket{v}\right) \geq 0$ with equality if and only if $A \ket{v} = 0$. Therefore $A^\dagger A$ is positive.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.26 {#exercise-226}

In section 2.1.7 the authors introduce the concept of tensor products. In this exercise you will gain experience with tensor power notation and the Kronecker product. 




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.27 {#exercise-227}

This exercise is just further practice with the Kronecker product. To check if the tensor product is commutative compare your results from (b) and (c).




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.28 {#exercise-228}

For this exercise you will confirm the distributive property of several operators over the tensor product. There are probably several different ways you could do this, but one method for the complex conjugate and transpose is to use the Kronecker product along with the properties of block matrices. The adjoint is just a combination of complex conjugation and the transpose, so you can use the distributive properties from those operations to show that the adjoint is also distributive.




Complex Conjugation

$$\begin{aligned}
\left( A \otimes B\right)^\ast &= \left( \begin{bmatrix} A_{11}B & A_{12}B & \dots & A_{1n}B \\\ A_{21}B & A_{22}B & \dots & A_{2n}B \\\ \vdots & \vdots & \vdots & \vdots \\ A_{m1}B & A_{m2}B & \dots & A_{mn}B   \end{bmatrix} \right)^\ast \\
&= \begin{bmatrix} A_{11}^\ast B^\ast & A_{12}^\ast B^\ast & \dots & A_{1n}^\ast B^\ast \\\ A_{21}^\ast B^\ast & A_{22}^\ast B^\ast & \dots & A_{2n}^\ast B^\ast \\\ \vdots & \vdots & \vdots & \vdots \\\ A_{m1} B^\ast & A_{m2}^\ast B^\ast & \dots & A_{mn}^\ast B^\ast   \end{bmatrix} \\
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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.29 {#exercise-229}

Use the definition of a unitary operator to show that the tensor product of two unitary operators is unitary.




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.30 {#exercise-230}

Use the definition of a Hermitian operator to show that the tensor product of two Hermitian operators is Hermitian.




We need to show that $(A \otimes B)^\dagger = (A \otimes B)$ when $A$ and $B$ are both Hermitian. 

$(A \otimes B)^\dagger = A^\dagger \otimes B^\dagger = A \otimes B$

Therefore $A \otimes B$ is Hermitian.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.31 {#exercise-231}

Use the definition of a positive operator to show that the tensor product of two positive operators is positive.




We need to show that $\left( \ket{a} \otimes \ket{b}, (A \otimes B)(\ket{a} \otimes \ket{b})\right)$ is a real, non-negative number when $A$ and $B$ are positive. 

$$\begin{aligned}
\left( \ket{a} \otimes \ket{b}, (A \otimes B)(\ket{a} \otimes \ket{b})\right) &= \left( \ket{a} \otimes \ket{b}, A\ket{a} \otimes B\ket{b} \right) & \text{by equation 2.45}\\
&= \braket{a \vert A \vert a} \braket{b \vert B \vert b} & \text{by equation 2.49}
\end{aligned}$$

Since both $A$ and $B$ are positive operators, we know that $\braket{a \vert A \vert a}$ and $\braket{b \vert B \vert b}$ are real, non-negative numbers. Therefore $\braket{a \vert A \vert a} \braket{b \vert B \vert b}$ is a real non-negative number and so $A \otimes B$ is positive. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.32 {#exercise-232}

Use the definition of a projector to show that the tensor product of two projector is a projector.




From [exercise 2.16](#exercise-216) we know that any projector $P$ satisfies the equation $P^2 = P$. Lets say we have two projectors $P_1$ and $P_2$, then lets check the square of their tensor product 

$$\begin{aligned}
(P_1 \otimes P_2)^2 &= (P_1 \otimes P_2)(P_1 \otimes P_2) \\
&= P_1^2 \otimes P_2^2 & \text{tensor product distributes over matrix multiplication}\\
&= P_1 \otimes P_2 & \text{definition of $P$}
\end{aligned}$$

Therefore the tensor product of two projectors is a projector. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.33 {#exercise-233}

For this exercise you are asked to confirm that the Hadamard transform can be written as equation 2.55. One thing that can be confusing about this is that equation 2.55 is not well defined, i.e. it is not stated what the different variables represent. I found it useful to refer to section 1.4.4 where the Hadamard transform is discussed in more detail to better understand equation 2.55. From there you can confirm the $n=1$ case matches equation 2.55 and then use that to confirm the arbitrary $n$ case. 




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.34 {#exercise-234}

In section 2.1.8 the authors introduce the concept of operator functions and describe how to calculate them. In this exercise you get practice performing that calculation on a given matrix. Since this matrix is not in diagonal representation, you will first need to find its diagonal representation, then execute the operation on its eigen values, and then reconstruct the operator in matrix representation. 




We know that $f(A) \equiv \sum_{a} f(a) \ket{a} \bra{a}$ for $A = \sum_{a} a \ket{a}\bra{a}$. Since the given matrix is not diagonal, we'll need to diagonalize it. So first we'll find the eigenvalues

$$\begin{aligned}
0 &= \text{det} \left(\begin{bmatrix} 4 & 3 \\\ 3 & 4 \end{bmatrix} - \lambda \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) \\
&= \text{det} \left(\begin{bmatrix} 4 - \lambda & 3 \\\ 3 & 4 - \lambda \end{bmatrix} \right) \\
&= (4-\lambda)^2 - 9 \\
&= \lambda^2 - 8 \lambda + 7 \\
\lambda &= \frac{8 \pm \sqrt{64 - (4) (1) (7)}}{(2)(1)} \\
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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.35 {#exercise-235}

In this exercise you will confirm the exponential of the Pauli matrices. To do this, you'll need to find the diagonal representation of $\vec{v} \cdot \vec{\sigma}$, then use Euler's formula and the operator function calculation.




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

Which gives normalized eigenvectors $\ket{\lambda_+}= \frac{1}{\sqrt{2(1+v_3)}}(v_3 + 1, v_1 + i v_2)$ and $\ket{\lambda_-}= \frac{1}{\sqrt{2(1-v_3)}}(v_3 - 1, v_1 + i v_2)$ 

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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.36 {#exercise-236}

In section 2.1.8 the authors introduce the concept of the trace. Use the definition of the trace to calculate the trace of the Pauli matrices. 




The trace of a matrix is given by $\text{tr}(A) \equiv \sum_{i} A_{ii}$, therefore the trace of the Pauli matrices are

$$\begin{aligned}
\text{tr}(X) &= \text{tr} \left( \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \right) = 0 + 0 = 0 \\
\text{tr}(Y) &= \text{tr}\left( \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \right) = 0 + 0 = 0 \\
\text{tr}(Z) &= \text{tr} \left( \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \right) = 1 - 1 = 0 \\
\text{tr}(I) &= \text{tr} \left( \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) = 1 + 1 = 2 & \text{this will $=d$ where $d$ is the dimension}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.37 {#exercise-237}

For this exercise you use the definition of the trace and the definition of matrix multiplication to demonstrate that $\text{tr}(AB) = \text{tr}(BA)$.




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.38 {#exercise-238}

For this exercise you use the definition of the trace and the definition of matrix addition to demonstrate that $\text{tr}(A+B) = \text{tr}(A) + \text{tr}(B)$. You will also use the definition of the trace to demonstrate that $\text{tr}(zA) = z \text{tr}(A)$.




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.39 {#exercise-239}

This exercise has multiple parts. For the first part, you need to show that $(\cdot, \cdot)$ on $L_V \times L_V$ is an inner product using the requirements listed in section 2.1.4 and the Hilbert-Schmidt inner product defined in equation 2.65. Then you need to demonstrate that $L_V$ has dimensions $d^2$ by finding how many linear independent elements there are in the set of operators that span $L_V$. Finally, you need to find an orthonormal basis of Hermitian matrices for $L_V$. This can be done by taking the inner product of two arbitrary linear operators in $L_V$ and identifying what requirements are needed to make them orthonormal. 




(1) in order to show that $(A,B)$ is an inner product we need to go back to section 2.1.4 to get the requirements for an inner product, which are: linear in the second argument, conjugate symmetry, and positive semi-definiteness. To check for linearity in the second argument let's look at

$$\begin{aligned}
(A, zB) &= \text{tr}(A^\dagger zB) & \text{equation 2.65} \\
&= z \text{tr}(A^\dagger B) & \text{equation 2.64}\\
&= z (A, B) & \text{equation 2.65}
\end{aligned}$$

For conjugate symmetry 

$$\begin{aligned}
(A, B)^\ast &= \text{tr}(A^\dagger B)^\ast & \text{equation 2.65} \\
&= \text{tr}((A^T)^\ast B)^\ast & \text{because $M^\dagger = (M^\ast)^T$} \\
&= \text{tr}(A^T B^\ast) & \text{distributivity of complex conjugation}\\
&= \text{tr}((A^T B^\ast)^T) & \text{because $\text{tr}(M) = \text{tr}(M^T)$}\\
&= \text{tr}((A^T)^T (B^\ast)^T) & \text{distributivity of transpose}\\
&= \text{tr}(A B^\dagger) & \text{because $M^\dagger = (M^\ast)^T$ and $M = (M^T)^T$}\\
&= \text{tr}(B^\dagger A) & \text{equation 2.62}\\
&= (B, A) & \text{equation 2.65}
\end{aligned}$$

And finally positive semi-definiteness

$$\begin{aligned}
(A, A) &= \text{tr}(A^\dagger A) & \text{equation 2.65} \\
&= \sum_{i} \sum_{k} A_{ik}^\dagger A_{ki} & \text{definition of matrix multiplication}  \\
&= \sum_{i} \sum_{k} A^\ast_{ki}A_{ki} & \text{because $M^\dagger = (M^\ast)^T$} \\
&= \sum_{i} \sum_{k} \vert A_{ki} \vert^2 \geq 0 
\end{aligned}$$


(2) if $L_V$ is a set of linear operators then for each operator in the set $A: V \rightarrow V$ and, per equation 2.12, can be represented as

$$\begin{aligned}
A \ket{v_j} = \sum_{i} A_{ij} \ket{v_i}
\end{aligned}$$

with $\ket{v_1}, \dots, \ket{v_d}$ being an othernormal basis for $V$ which has $d$ elements. Therefore $A$ needs to be a $d \times d$ matrix. In order to form a basis set of linear operators that span $L_V$ there needs to be $d^2$ linearly independent elements in the set. Therefore $L_V$ has dimensions $d^2$. 

(3) In order for the operators $A$ and $B$ to be linearly independent their inner product needs to be $0$. We know that

$$\begin{aligned}
(A, B) &= \text{tr} (A^\dagger B) & \text{equation 2.65} \\
&= \text{tr} \left( \sum_{k} A^\dagger_{ik} B_{kj} \right) & \text{definition of matrix multiplication} \\
&= \sum_{ik} A^\dagger_{ik} B_{ki} & \text{definition of trace}\\
&= \sum_{ik} A^\ast_{ki} B_{ki} & \text{because $M^\dagger = (M^\ast)^T$}
\end{aligned}$$

Looking at the above results, it can easily be seen that one way to insure that $(A,B)=0$ is to set at least one of the elements $A_{ij}$ or $B_{ij}$ to $0$ for each $ij$. Expanding this to the entire basis set, the set is guaranteed to be linearly independent if only one of the basis matrices has a non-zero element for each $ij$. Therefore the following is a possible orthonormal basis set for $L_V$

$$\begin{aligned}
L_{Vij} = \sum_{i'j'} \delta_{ii'} \delta_{jj'} \ket{v_{j'}}\bra{v_{i'}} 
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

 

### Exercise 2.40 {#exercise-240}

In section 2.1.9 the authors introduce the concept of the commutator and anti-commutator. In this exercise you will use the definition of the commutator to verify commutation relations of the Pauli matrices.




$$\begin{aligned}
\lbrack X,Y \rbrack = XY - YX = \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} - \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} = \begin{bmatrix} i & 0 \\\ 0 & -i \end{bmatrix} - \begin{bmatrix} -i & 0 \\\ 0 & i \end{bmatrix} = 2i \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} = 2 i Z
\end{aligned}$$

$$\begin{aligned}
\lbrack Y,Z \rbrack = YZ - ZY = \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} - \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} = \begin{bmatrix} 0 & i \\\ i & 0 \end{bmatrix} - \begin{bmatrix} 0 & -i \\\ -i & 0 \end{bmatrix} = 2i \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} = 2 i X
\end{aligned}$$

$$\begin{aligned}
\lbrack Z,X \rbrack = ZX - XZ = \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} - \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} = \begin{bmatrix} 0 & 1 \\\ -1 & 0 \end{bmatrix} - \begin{bmatrix} 0 & -1 \\\ 1 & 0 \end{bmatrix} = 2 i \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} = 2 i Y
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.41 {#exercise-241}

In this exercise you will use the definition of the anti-commutator to verify anti-commutation relations of the Pauli matrices.




$$\begin{aligned}
\lbrace X,Y \rbrace = XY + YX = \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} + \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} = \begin{bmatrix} i & 0 \\\ 0 & -i \end{bmatrix} + \begin{bmatrix} -i & 0 \\\ 0 & i \end{bmatrix} = \begin{bmatrix} 0 & 0 \\\ 0 & 0 \end{bmatrix} = 0
\end{aligned}$$

$$\begin{aligned}
\lbrace Y,Z \rbrace = YZ + ZY = \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} + \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} 0 & -i \\\ i & 0 \end{bmatrix} = \begin{bmatrix} 0 & i \\\ i & 0 \end{bmatrix} + \begin{bmatrix} 0 & -i \\\ -i & 0 \end{bmatrix} = \begin{bmatrix} 0 & 0 \\\ 0 & 0 \end{bmatrix} = 0
\end{aligned}$$

$$\begin{aligned}
\lbrace Z,X \rbrace = ZX + XZ = \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} + \begin{bmatrix} 0 & 1 \\\ 1 & 0 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 0 & -1 \end{bmatrix} = \begin{bmatrix} 0 & 1 \\\ -1 & 0 \end{bmatrix} + \begin{bmatrix} 0 & -1 \\\ 1 & 0 \end{bmatrix} = \begin{bmatrix} 0 & 0 \\\ 0 & 0 \end{bmatrix} = 0
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.42 {#exercise-242}

In this exercise you will use the definition of the commutator and anti-commutator to verify equation 2.77.




$$\begin{aligned}
\lbrack A,B\rbrack &= AB - BA \\
\lbrace A,B \rbrace &= AB + BA \\
\lbrack A,B\rbrack + \lbrace A,B \rbrace &= AB - BA + AB + BA = 2AB \\
\Rightarrow AB &= \frac{\lbrack A,B\rbrack+ \lbrace A,B \rbrace }{2}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.43 {#exercise-243}

To verify equation 2.78 you will need to use the results from exercises [2.19](#exercise-219), [2.41](#exercise-241), and [2.42](#exercise-242).




Starting with equation 2.77 we know that

$$\begin{aligned}
\sigma_j \sigma_k &= \frac{\lbrack \sigma_j,\sigma_k \rbrack+ \lbrace\sigma_j,\sigma_k\rbrace }{2} & \text{equation 2.77}\\
&= \frac{\sum_{l=1}^{3} 2 i \epsilon_{jkl} \sigma_l+ 2\delta_{jk} I }{2} & \text{exercise 2.19 and 2.41}\\
&=\sum_{l=1}^{3}  i \epsilon_{jkl} \sigma_l + \delta_{jk} I & \text{simplify}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.44 {#exercise-244}

In section 2.1.9 the authors introduce the simultaneous diagonalization theorem. Here you will use that theorem along with the diagonal representation of $A$ and $B$ and the invertible matrix theorem (which is not in the book) to show that $B$ must be zero. 




If $\lbrack A,B \rbrack = 0$ that means there must be a common orthonormal set of eigenvectors $\ket{i}$ for $A$ and $B$ such that $A=\sum_{i} a_i \ket{i}\bra{i}$ and $B=\sum_{i} b_i \ket{i}\bra{i}$. This means that

$$\begin{aligned}
\lbrace A,B \rbrace &=AB+BA \\
&= \sum_{i} a_i \ket{i}\bra{i} \sum_{j} b_j \ket{j}\bra{j} +  \sum_{j} b_j \ket{j}\bra{j} \sum_{i} a_i \ket{i}\bra{i} & \text{diagonal representation}\\
&= \sum_{ij} a_i b_j \ket{i}\braket{i \vert j}\bra{j} + a_i b_j \ket{j}\braket{j \vert i}\bra{i} & \text{summation distributivity}\\
&= \sum_{ij} a_i b_j \delta_{ij} (\ket{i}\bra{j} + \ket{j}\bra{i} ) & \text{orthogonality of basis vectors}\\
&= \sum_{i} a_i b_i (\ket{i}\bra{i} + \ket{i}\bra{i} ) & \text{delta function}\\
&= \sum_{i} 2 a_i b_i \ket{i}\bra{i} 
\end{aligned}$$

Which is only $0$ if either $a_i$ or $b_i$ is $0$ for each $i$. In order for matrix $A$ to be invertible $0$ cannot be an eigenvalue of $A$ per the invertible matrix theorem. Therefore $b_i = 0$ for all $i$ and so $B=0$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.45 {#exercise-245}

For this exercise you will use the definition of commutation and the properties of the adjoint to demonstrate the relation shown in the question.




$$\begin{aligned}
\lbrack A,B \rbrack ^\dagger &= (AB - BA)^\dagger & \text{commutation definition}\\
&= (AB)^\dagger - (BA)^\dagger & \text{adjoint distributivity over matrix addition} \\
&= B^\dagger A^\dagger  -  A^\dagger B^\dagger & \text{adjoint anti-distributivity over matrix multiplication}\\
&= \lbrack B^\dagger, A^\dagger \rbrack & \text{commutation definition}\\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.46 {#exercise-246}

For this exercise you will use the definition of commutation to demonstrate the relation shown in the question.




$\lbrack A,B \rbrack = AB-BA = -(BA-AB)=-\lbrack B,A \rbrack$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.47 {#exercise-247}

Here you will use the definition of Hermitian, the definition of commutation, and properties of the adjoint to show that $i \lbrack A,B \rbrack$ is Hermitian. 




If $A$ and $B$ are Hermitian it means that $A^\dagger = A$ and $B^\dagger=B$. With this in mind, we can check if $i \lbrack A,B \rbrack$ is Hermitian by taking the adjoint.

$$\begin{aligned}
( i \lbrack A,B \rbrack )^\dagger &= ( i AB - i BA )^\dagger & \text{commutation definition}\\
&= -i (AB)^\dagger + i (BA)^\dagger & \text{adjoint distributivity over matrix addition}\\
&= -i B^\dagger A^\dagger + i A^\dagger B^\dagger & \text{adjoint anti-distributivity over matrix multiplication}\\
&= -i BA + i AB & \text{since $A$ and $B$ are Hermitian}\\
&= i (AB - BA) & \text{rearranging}\\
&= i \lbrack A,B \rbrack & \text{commutation definition}
\end{aligned}$$

Therefore $i \lbrack A,B \rbrack$ is Hermitian.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.48 {#exercise-248}

In section 2.1.10 the authors introduce the concept of polar decomposition which is a method used to break a general linear operator up into products of unitary operators and positive operators. In this exercise you are asked to perform polar decomposition on a positive matrix, a unitary matrix, and a Hermitian matrix. You can follow the calculation outlined in the book, but simplifications can also be made when taking into consideration the properties of the different matrices and the goal of polar decomposition.




Since $P$ is already a positive operator, polar decomposition is not needed, though $P$ can be written as $P=IP=PI$ where the identity operator $I$ is a unitary operator. 

Similar to the case of $P$, $U$ is already one of the simpler matrix elements that polar decomposition is used to break a general linear operator up into. However, if desired $U$ can be written as $U=UI = IU$

For Hermitian matrix $H$ we know that $H^\dagger = H$ and $H= \sum_{i} \lambda_i \ket{i}\bra{i}$ and therefore

$$\begin{aligned}
H^\dagger H &= HH & \text{definition of Hermitian}\\
&= \sum_{ii'} \lambda_i \lambda_{i'} \ket{i}\braket{i \vert i'}\bra{i'} & \text{spectral decomposition}\\
&= \sum_{i} \lambda_i^2 \ket{i}\bra{i} & \text{basis vector orthogonality}
\end{aligned}$$

For polar decomposition  $H=UJ=KU$ where 

$$\begin{aligned}
J &= \sqrt{H^\dagger H} & \text{definition of $J$}\\
&= \sqrt{\sum_{i} \lambda_i^2 \ket{i}\bra{i}} & \text{derived value of $H^\dagger H$}\\
&= \sum_{i} \vert\lambda_i\vert \ket{i}\bra{i} & \text{operator function calculation}
\end{aligned}$$

Since $H$ is Hermitian

$$\begin{aligned}
K &= \sqrt{H H^\dagger} & \text{definition of $K$}\\
&= \sqrt{H^\dagger H} & \text{definition of Hermitian}\\
&= J
\end{aligned}$$

To find $U$ we find need to define a set of orthonormal basis vectors 

$$\begin{aligned}
\ket{e_i} &\equiv \frac{H \ket{i}}{\vert\lambda_i\vert} & \text{from polar decomposition proof}\\
&= \frac{\lambda_i \ket{i}}{\vert\lambda_i\vert} & \text{evaluating $H \ket{i}$}
\end{aligned}$$

for $\lambda_i \neq 0$ and then define $U \equiv \sum_{i} \ket{e_i}\bra{i}$. If one or more of the $\lambda_i = 0$ use the Gram-Schmidt procedure to extend the orthonormal set $\ket{e_i}$ to form an orthonormal basis. 

Then $H = UJ = KU$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.49 {#exercise-249}

For this exercise you will perform a similar calculation as was done in the previous exercise, but this time for a normal matrix. 




Matrix $A$ is a normal matrix if $A^\dagger A = A A^\dagger$. It's spectral decomposition is $A=\sum_{i} \lambda_i \ket{i}\bra{i}$ therefore

$$\begin{aligned}
A^\dagger A &=  \sum_{ii'} \lambda_i^* \lambda_{i'} \ket{i}\braket{i \vert i'}\bra{i'} \\
&= \sum_{i} \vert\lambda_i\vert^2 \ket{i}\bra{i}
\end{aligned}$$

$$\begin{aligned}
J &= \sqrt{A^\dagger A} \\
&= \sqrt{\sum_{i} \vert\lambda_i\vert^2 \ket{i}\bra{i}} \\
&= \sum_{i} \vert\lambda_i\vert \ket{i}\bra{i} \\
&= K
\end{aligned}$$

To find $U$ we find need to define a set of orthonormal basis vectors 

$$\begin{aligned}
\ket{e_i} &\equiv \frac{A \ket{i}}{\vert\lambda_i\vert}\\
&= \frac{\lambda_i \ket{i}}{\vert\lambda_i\vert}
\end{aligned}$$

for $\lambda_i \neq 0$ and then define $U \equiv \sum_{i} \ket{e_i}\bra{i}$. If one or more of the $\lambda_i = 0$ use the Gram-Schmidt procedure to extend the orthonormal set $\ket{e_i}$ to form an orthonormal basis. 

Then $A = UJ = KU$. 

This may look the same as the results for the Hermitian matrix in [Exercise 2.48](#exercise-248), but now $\lambda_i$ can be complex and so $U$ not only represents the sign of $\lambda_i$ but also contains information about the complex component of the eigenvalues. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.50 {#exercise-250}

For this exercise you will perform polar decomposition on a given matrix. The procedure is like the previous two exercises but since the matrix is not currently in diagonal representation, you’ll first need to diagonalize it. Unfortunately, this calculation is complex and so I recommend using a calculator.  This matrix is invertible – which you can confirm for yourself – so you can use the inverse of the matrix to calculate $U$. 




Let 

$$\begin{aligned}
A = \begin{bmatrix} 1 & 0 \\\ 1 & 1 \end{bmatrix} 
\end{aligned}$$

therefore,

$$\begin{aligned}
A^\dagger = \begin{bmatrix} 1 & 1 \\\ 0 & 1 \end{bmatrix}
\end{aligned}$$

and 

$$\begin{aligned}
A A^\dagger &= \begin{bmatrix} 1 & 0 \\\ 1 & 1 \end{bmatrix} \begin{bmatrix} 1 & 1 \\\ 0 & 1 \end{bmatrix} \\
&= \begin{bmatrix} 1 & 1 \\\ 1 & 2 \end{bmatrix}. 
\end{aligned}$$

In order to find the square root of $A A^\dagger$, we'll first need to write the matrix in diagonal representation. 

Let's find the eigenvalues

$$\begin{aligned}
0 &= \left\vert \begin{bmatrix} 1 & 1 \\\ 1 & 2 \end{bmatrix} - \begin{bmatrix} \lambda & 0 \\\ 0 & \lambda \end{bmatrix} \right\vert \\
&= \left\vert \begin{bmatrix} 1- \lambda & 1 \\\ 1 & 2-\lambda \end{bmatrix} \right\vert \\
&= (1-\lambda)(2 - \lambda) - 1 \\
&= \lambda^2 - 3 \lambda + 2 - 1 \\
&= \lambda^2 - 3 \lambda +1 \\
\Rightarrow \lambda &= \frac{3 \pm \sqrt{9 - (4) (1) (1)}}{(2) (1)} = \frac{3 \pm \sqrt{5}}{2}
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


Next, let's find $A^\dagger A$ and do the same thing. 

$$\begin{aligned}
A ^\dagger A &= \begin{bmatrix} 1 & 1 \\\ 0 & 1 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\ 1 & 1 \end{bmatrix}  \\
&= \begin{bmatrix} 2 & 1 \\\ 1 & 1 \end{bmatrix}
\end{aligned}$$

Let's find the eigenvalues

$$\begin{aligned}
0 &= \left\vert \begin{bmatrix} 2 & 1 \\\ 1 & 1 \end{bmatrix} - \begin{bmatrix} \lambda & 0 \\\ 0 & \lambda \end{bmatrix} \right\vert \\
&= \left\vert \begin{bmatrix} 2- \lambda & 1 \\\ 1 & 1-\lambda \end{bmatrix} \right\vert \\
&= (1-\lambda)(2 - \lambda) - 1 \\
&= \lambda^2 - 3 \lambda + 2 - 1 \\
&= \lambda^2 - 3 \lambda +1 \\
\Rightarrow \lambda &= \frac{3 \pm \sqrt{9 - (4) (1) (1)}}{(2) (1)} = \frac{3 \pm \sqrt{5}}{2}
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
&= \frac{1}{\vert J \vert} \begin{bmatrix} \frac{2}{\sqrt{5}} & -\frac{1}{\sqrt{5}} \\\  -\frac{1}{\sqrt{5}} & \frac{3}{\sqrt{5}} \end{bmatrix} \\
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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## The Postulates of Quantum Mechanics

### Exercise 2.51 {#exercise-251}

In section 2.2.2 the authors discuss how any unitary operator can be used to evolve the state of a single qubit and then ask us to confirm that the Hadamard gate is unitary. This can be done using the definition of a unitary operator $U^\dagger U = U U^\dagger = I$.




From the linear algebra section that we just completed, we know that an operator is a unitary operator if $U^\dagger U = U U^\dagger = I$. From equation 2.85 we know that the Hadamar gate is 

$$\begin{aligned}
H = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix}
\end{aligned}$$

Finding the adjoint we see

$$\begin{aligned}
H^\dagger &= \left(\frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix}\right)^\dagger & \text{definition of $H$}\\
&= \left(\frac{1}{\sqrt{2}} \begin{bmatrix} 1^\ast & 1^\ast \\\ 1^\ast & -1^\ast \end{bmatrix}\right)^T & \text{because $A^\dagger = (A^\ast)^T$}\\
&=\frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \\
&= H
\end{aligned}$$

Note: since $H^\dagger = H$ the Hadamard gate is Hermitian. 

Calculating $H^\dagger H$ we get

$$\begin{aligned}
H^\dagger H &= \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix}  & \text{definition of $H$ and $H^\dagger$}\\
&= \frac{1}{2} \begin{bmatrix} 2 & 0 \\\ 0 & 2 \end{bmatrix} & \text{matrix multiplication} \\
&= \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} & \text{simplify} \\
&= I & \text{definition of $I$}
\end{aligned}$$

Since $H^\dagger H = I$ that means $H$ is unitary. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.52 {#exercise-252}

The authors now ask us to verify that $H^2=I$. This can easily be done by using an observation noted in the previous exercise. 




In the previous exercise we saw that the Hadamard gate is Hermitian and so $H^\dagger = H$. We also demonstrated that $H^\dagger H = I$. Therefore we know that $H^\dagger H = HH = H^2 = I$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.53 {#exercise-253}

We are now asked to find the eigenvalues and eigenvectors of H. We will do this using the same methods that we used in the previous secion. We'll first find the eigenvalues $\lambda$ using the characteristic equation and then solve $0 = (\lambda I - H)\ket{e}$ to find the eigenvectors. 




First let's find the eigenvalues

$$\begin{aligned}
0 &= \text{det} \left( H - \lambda I \right) & \text{characteristic equation}\\
&= \text{det} \left( \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} - \lambda \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) & \text{definitions of $H$ and $I$}\\
&= \text{det} \left( \begin{bmatrix} 1 - \lambda & 1 \\\ 1 & -1 - \lambda \end{bmatrix} \right) & \text{matrix subtraction}\\
&= (1-\lambda)(-1-\lambda) - 1 & \text{definition of the determinant}\\
\lambda &= \pm \sqrt{2} & \text{solving for $\lambda$}
\end{aligned}$$

Now we know that the eigenvalues are $\lambda = \pm \sqrt{2}$. Let's find the eigenvectors

$$\begin{aligned}
0 &= \left( H - \lambda I \right)\ket{e} \\
&= \left( \begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} - \lambda \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \right) \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} 1 - \lambda & 1 \\\ 1 & -1 - \lambda \end{bmatrix} \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} (1 - \lambda)x_1 + x_2 \\\ x_1 - (1 + \lambda)x_2 \end{bmatrix}
\end{aligned}$$

Solving for $x_1$ and $x_2$ we find that the unit eigenvectors are given by $\ket{e} = \frac{1}{\sqrt{\lambda^2 + 2\lambda + 2}}(1+\lambda, 1)$. 

For eigenvalue $\lambda_+ = \sqrt{2}$ the unit eigenvector is $\ket{e_+} = \frac{1}{\sqrt{4 + 2\sqrt{2}}}(1+\sqrt{2}, 1)$

For eigenvalue $\lambda_- = -\sqrt{2}$ the unit eigenvector is $\ket{e_-} = \frac{1}{\sqrt{4 - 2\sqrt{2}}}(1-\sqrt{2}, 1)$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.54 {#exercise-254}

We are asked to show that $\exp(A)\exp(B)=\exp(A+B)$ for commuting Hermitian operators $A$ and $B$. To do this, we need to use the simultaneous diagonalization theorem given in section 2.1.9 and knowledge of operator functions. 




From section 2.1.9 we know that if $A$ and $B$ are commuting operators they are simultaneously diagonalizable, meaning they can be written as

$$\begin{aligned}
A &= \sum_{i} a_i \ket{i} \bra{i} \\
B &= \sum_{i} b_i \ket{i} \bra{i} \\
A + B &= \sum_{i} a_i \ket{i} \bra{i} + \sum_{i} b_i \ket{i} \bra{i} \\
&= \sum_{i} (a_i + b_i) \ket{i} \bra{i}
\end{aligned}$$

where $\ket{i}$ is some common orthonormal set of eigenvectors.

Using our knowledge of operator functions we know that

$$\begin{aligned}
\exp(A) &=\sum_{i} \exp(a_i) \ket{i} \bra{i} \\
\exp(B) &=\sum_{i} \exp(b_i) \ket{i} \bra{i} \\
\exp(A + B) &= \sum_{i} \exp(a_i + b_i) \ket{i} \bra{i} 
\end{aligned}$$

Therefore,

$$\begin{aligned}
\exp(A)\exp(B) &= \sum_{i} \exp(a_i) \ket{i} \bra{i} \sum_{i'} \exp(b_{i'}) \ket{i'} \bra{i'} \\
&= \sum_{ii'} \exp(a_i)\exp(b_{i'}) \ket{i} \braket{i \vert i'} \bra{i'} \\
&= \sum_{i} \exp(a_i)\exp(b_{i}) \ket{i} \bra{i} \\
&= \sum_{i} \exp(a_i + b_{i}) \ket{i} \bra{i} \\
&= \exp(A+B)
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.55 {#exercise-255}

Here we are to prove that equation 2.91 is unitary, meaning $U^\dagger U = U U^\dagger = I$, using the knowledge that $H$ is a Hermitian operator and the results from the previous exercise. 




From equation 2.91 we know

$$\begin{aligned}
U(t_1, t_1) = \exp \left\lbrack \frac{-iH(t_2 - t_1)}{\hbar} \right\rbrack
\end{aligned}$$

From equation 2.87 we know

$$\begin{aligned}
H = \sum_{E} E \ket{E} \bra{E}
\end{aligned}$$

and therefore 

$$\begin{aligned}
\exp \left\lbrack \frac{-iH(t_2 - t_1)}{\hbar} \right\rbrack = \sum_{E} \exp \left\lbrack \frac{-iE(t_2 - t_1)}{\hbar} \right\rbrack \ket{E} \bra{E}
\end{aligned}$$

Now let's find $U^\dagger$

$$\begin{aligned}
U^\dagger(t_1, t_1) &= \left( \sum_{E} \exp \left\lbrack \frac{-iE(t_2 - t_1)}{\hbar} \right\rbrack \ket{E} \bra{E} \right)^\dagger \\
&= \sum_{E} \exp \left\lbrack \frac{iE(t_2 - t_1)}{\hbar} \right\rbrack \ket{E} \bra{E} \\
&= \exp \left\lbrack \frac{iH(t_2 - t_1)}{\hbar} \right\rbrack
\end{aligned}$$

Using the results from the previous exercise, keeping in mind that H is a Hermitian operator, we know

$$\begin{aligned}
U^\dagger(t_1, t_1) U(t_1, t_1) &= \exp \left\lbrack \frac{iH(t_2 - t_1)}{\hbar} \right\rbrack \exp \left\lbrack \frac{-iH(t_2 - t_1)}{\hbar} \right\rbrack \\
&= \exp \left\lbrack \frac{iH(t_2 - t_1) - iH(t_2 - t_1)}{\hbar} \right\rbrack \\
&= \exp \left\lbrack 0 \right\rbrack \\
&= \sum_{E} \exp \left\lbrack 0 \right\rbrack \ket{E} \bra{E} \\
&= \sum_{E} \ket{E} \bra{E} \\
&= I
\end{aligned}$$

Therefore $U$ is unitary.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.56 {#exercise-256}

In this exercise we use spectral decomposition to show that $K= -i \log(U)$ is Hermitian for any unitary operator $U$ and thus $U = \exp(iK)$ for some Hermitian operator $K$. To do this, you will represent the eigenvalues of $U$ as described in [exercise 2.18](#exercise-218). 




Since $U$ is unitary using spectral decomposition we know that it can be written

$$\begin{aligned}
U = \sum_{E} \lambda_E \ket{E} \bra{E}
\end{aligned}$$

where $\lambda_E$ are the eigenvalues and $\ket{E}$ form an orthonormal basis for $U$. 

From [exercise 2.18](#exercise-218), we know that the eigenvalues of a unitary matrix can be written in the form $\lambda_E = e^{i \theta_E}$ for some real $\theta_E$.

Looking at our definition of $K$ we see

$$\begin{aligned}
K &= - i \log (U) \\
&= -i \sum_{E} \log (\lambda_E) \ket{E} \bra{E} \\
&= -i \sum_{E} \log (e^{i \theta_E}) \ket{E} \bra{E} \\
&= -i \sum_{E} \frac{\ln (e^{i \theta_E})}{\ln(2)} \ket{E} \bra{E} & \text{change of base}\\
&= -i \sum_{E} i \frac{\theta_E}{\ln(2)} \ket{E} \bra{E} \\
&= \sum_{E} \frac{\theta_E}{\ln(2)} \ket{E} \bra{E}
\end{aligned}$$

Since $\theta_E$ are real, we know that $K = \sum_{E} \frac{\theta_E}{\ln(2)} \ket{E} \bra{E}$ is in the form of a Hermitian matrix. Therefore $K$ is Hermitian. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.57 {#exercise-257}

In section 2.2.3 the authors discuss measuring a quantum system and in equation 2.93 show what the state of the system is after measurement. Here you are asked to show that two sequential measurement operations are the equivalent of a single measurement operation that is the matrix multiplication of both individual measurement operators.




Using equation 2.93 to get the state of the system after measurement $L_l$ we find

$$\begin{aligned}
\ket{\psi} \rightarrow \ket{\psi'} = \frac{L_l \ket{\psi}}{\sqrt{\braket{\psi \vert L_l^\dagger L_l \vert \psi}}}
\end{aligned}$$

Then using equation 2.93 again to get the state of the system after measurement $M_m$ we find

$$\begin{aligned}
\ket{\psi'} \rightarrow \ket{\psi''} &= \frac{M_m \ket{\psi'}}{\sqrt{\braket{\psi' \vert M_m^\dagger M_m \vert \psi'}}} \\
&= \frac{M_m \frac{L_l \ket{\psi}}{\sqrt{\braket{\psi \vert L_l^\dagger L_l \vert \psi}}}}{\sqrt{\frac{\bra{\psi}L_l^\dagger}{\sqrt{\braket{\psi \vert L_l^\dagger L_l \vert \psi}}} M_m^\dagger M_m \frac{L_l \ket{\psi}}{\sqrt{\braket{\psi \vert L_l^\dagger L_l \vert \psi}}}}} \\
&= \frac{M_mL_l \ket{\psi}}{\sqrt{\braket{\psi \vert L_l^\dagger M_m^\dagger M_mL_l \vert \psi}}}
\end{aligned}$$

If we instead calculated the system after measurement $N_{lm} = M_m L_l$ we would get

$$\begin{aligned}
\ket{\psi} \rightarrow \ket{\psi'''} &= \frac{N_{lm} \ket{\psi}}{\sqrt{\braket{\psi \vert N_{lm}^\dagger N_{lm} \vert \psi}}} \\
&= \frac{M_m L_l \ket{\psi}}{\sqrt{\braket{\psi \vert (M_m L_l)^\dagger M_m L_l \vert \psi}}} \\
&= \frac{M_m L_l \ket{\psi}}{\sqrt{\braket{\psi \vert L_l^\dagger M_m^\dagger M_m L_l \vert \psi}}}
\end{aligned}$$

We can see that $\ket{\psi''}=\ket{\psi'''}$ therefore the sequential measurements are equivalent to $N_{lm}$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.58 {#exercise-258}

In section 2.2.5 the authors introduce the concept of projective measurements and show how to calculate the average observed value and standard deviation for an observable operator. For this exercise you will get practice with these calculations for eigenvector $\ket{\psi}$ of observable $M$ with eigenvalue $m$. 




We can calculate the average value of the measurement using equation 2.113,

$$\begin{aligned}
E(M) &= \braket{\psi \vert M \vert \psi} \\
&= \braket{\psi \vert m \psi} & \text{since $\ket{\psi}$ is an eigenvector of $M$ with eigenvalue $m$}\\
&= m \braket{\psi \vert \psi} \\
&= m
\end{aligned}$$

Then calculating the standard deviation we get

$$\begin{aligned}
\Delta (M) &= \sqrt{\braket{\psi \vert M^2 \vert \psi} - \braket{\psi \vert M \vert \psi}^2 } \\
&= \sqrt{\braket{\psi \vert MM\vert \psi} - m^2 } & \text{from the above calculation}\\
&= \sqrt{\braket{\psi \vert M^\dagger M\vert \psi} - m^2 } & \text{since M is Hermitian} \\
&= \sqrt{\braket{ m^\ast \psi \vert m \psi} - m^2 } & \text{since $\ket{\psi}$ is an eigenvector of $M$ with eigenvalue $m$} \\
&= \sqrt{m^2 \braket{\psi \vert \psi} - m^2 } & \text{eigenvalues of Hermitian operators are real} \\
&= \sqrt{m^2 - m^2} \\
&= 0
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.59 {#exercise-259}

In this exercise we are to calculate the average and standard deviation of the observed value of $X$ for state $\ket{0}$. For this, we will use the results from [exercise 2.9](#exercise-29), [exercise 2.19](#exercise-219), and the calculations outlined in section 2.2.5.




From exercise 2.9, we know that the outer product representation of $X$ can be written as

$$\begin{aligned}
X = \ket{0}\bra{1} + \ket{1}\bra{0}
\end{aligned}$$

First let's calculate $\braket{0 \vert X \vert 0}$

$$\begin{aligned}
\braket{0 \vert X \vert 0} &= \braket{0 \vert \left( \ket{0}\bra{1} + \ket{1}\bra{0} \right) \vert 0}\\
&= \braket{0 \vert 0}\braket{1 \vert 0} + \braket{0 \vert 1}\braket{0 \vert 0}\\
&= 0
\end{aligned}$$

From exercise 2.19, we know that $X^2=I$, using this let's calculate $\braket{0 \vert X^2 \vert 0}$

$$\begin{aligned}
\braket{0 \vert X^2 \vert 0} &= \braket{0 \vert I \vert 0}
&= \braket{0 \vert 0}
&= 1
\end{aligned}$$

From equation 2.113 we know that the average value of the measurement is $\braket{0 \vert X \vert 0} = 0$ and from equation  2.115 we know the standard deviation is $\sqrt{\braket{0 \vert X^2 \vert 0} - \braket{0 \vert X \vert 0}^2} = \sqrt{1-0^2} = 1$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.60 {#exercise-260}

For this exercise we are to show that equation 2.116 has eigenvalues $\pm 1$ and that the projectors onto the corresponding eigenspaces are given by $P_{\pm}=(I \pm \vec{v} \cdot \vec{\sigma})/2$. Some of the calculations needed for this were already done in [exercise 2.35](#exercise-235).




From exercise 2.35 we know that 

$$\begin{aligned}
\vec{v} \cdot \vec{\sigma} = \begin{bmatrix} v_3 & v_1 - i v_2 \\\ v_1 + i v_2 & -v_3 \end{bmatrix}
\end{aligned}$$

wich has eigenvalues $\lambda_{\pm} = \pm \sqrt{v_1^2 + v_2^2 + v_3^2} = \pm 1$ and eigenvectors $\ket{\lambda_{\pm}}= \frac{1}{\sqrt{2(1 \pm v_3)}}(v_3 \pm 1, v_1 + i v_2)$ .

Therefore $\vec{v} \cdot \vec{\sigma}$ can be written as

$$\begin{aligned}
\vec{v} \cdot \vec{\sigma} = \ket{\lambda_+}\bra{\lambda_+} - \ket{\lambda_-}\bra{\lambda_-} = \sum_{m} m P_m
\end{aligned}$$

Looking at the above equation, it can be seen that $m = \pm 1$ and $P_m = \ket{\lambda_{\pm}}\bra{\lambda_{\pm}}$ therefore

$$\begin{aligned}
\vec{v} \cdot \vec{\sigma} = P_+ - P_-
\end{aligned}$$

We know that $\sum_{m} P_m = I = P_+ + P_-$, So $P_- = I - P_+$ and $P_+ = I - P_-$ therefore

$$\begin{aligned}
\vec{v} \cdot \vec{\sigma} &= P_+ -(I - P_+)  = 2 P_+ - I \\
\Rightarrow P_+ &= (I + \vec{v} \cdot \vec{\sigma})/2 \\
\vec{v} \cdot \vec{\sigma} &= (I - P_-) - P_+  = I - 2P_- \\
\Rightarrow P_- &= (I - \vec{v} \cdot \vec{\sigma})/2
\end{aligned}$$

Which shows that $P_{\pm}=(I \pm \vec{v} \cdot \vec{\sigma})/2$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.61 {#exercise-261}

Use the results from the previous exercise as well as equations 2.103 and 2.104 to find the probability of obtaining the measurement result of $+1$ and the state of the system after the measurement if $+1$ is obtained when the state prior to measurement is $\ket{0}$.




Using equation 2.103 and the results from the previous exercise, the probability of obtaining result $+1$ is given by 

$$\begin{aligned}
\braket{0 \vert P_+ \vert 0} &= \braket{0 \vert \left(\ket{\lambda_+}\bra{\lambda_+}\right) \vert 0} \\
&= \begin{bmatrix} 1 & 0 \end{bmatrix} \left( \frac{1}{\sqrt{2(1+v_3)}} \begin{bmatrix}v_3 + 1 \\\ v_1 + i v_2 \end{bmatrix} \right) \left( \frac{1}{\sqrt{2(1+v_3)}} \begin{bmatrix}v_3 + 1 & v_1 - i v_2 \end{bmatrix} \right) \begin{bmatrix} 1 \\\ 0 \end{bmatrix} \\
&= \frac{(v_3 + 1)^2}{2(v_3 + 1)} \\
&= \frac{v_3 + 1}{2} 
\end{aligned}$$

Note: if you did not previously find the eigenvectors for $\vec{v} \cdot \vec{\sigma}$ there are ways of solving this exercise without them. I had just previously calculated them and chose to use them. 

The state after the measurement is given by equation 2.104

$$\begin{aligned}
\frac{P_+ \ket{0}}{\sqrt{\braket{0 \vert P_+ \vert 0}}} &= \frac{\ket{\lambda_+}}{\sqrt{\frac{v_3 + 1}{2}}} \braket{\lambda_+ \vert 0} \\
&= \frac{\ket{\lambda_+}}{\sqrt{\frac{v_3 + 1}{2}}} \left( \frac{1}{\sqrt{2(1+v_3)}} \begin{bmatrix}v_3 + 1 & v_1 - i v_2 \end{bmatrix} \right) \begin{bmatrix} 1 \\\ 0 \end{bmatrix} \\
&= \frac{\ket{\lambda_+}}{v_3 + 1} (v_3 + 1) \\
&= \ket{\lambda_+}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.62 {#exercise-262}

For this exercise, we are to show that any measurement where the measurement operators and the POVM elements coincide (i.e. where $E_m = M_m$) is a projective measurement.




For this case

$$\begin{aligned}
M_m &= E_m \\
&= M^\dagger M & \text{definition of $E_m$} \\
\end{aligned}$$

We know that any projector satisfies the equation $P=PP=P^\dagger P$ and so $M$ must be a projector. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.63 {#exercise-263}

In this exercise we are to show that there exists unitary operators $U_m$ such that $M_m=U_m \sqrt{E_m}$. For this, think back to the section 2.1.10 discussion on polar decomposition. 




In section 2.1.10 we learned that a linear operator can be broken up into a product of a unitary operator and positive operators such that $A=UJ=KU$ where the positive operators are given as $J=\sqrt{A^\dagger A}$ and $K=\sqrt{AA^\dagger}$. 

From equation 2.117 we know that $E_m = M_m^\dagger M_m$, therefore $\sqrt{E_m} = \sqrt{M_m^\dagger M_m}=J$. From polar decomposition we then know $M_m$ can be written as $M_m = U_m J = U_m \sqrt{E_m}$.  

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.64 {#exercise-264}

Create a set of $E_m$ such that if outcome $E_i$ occurs then you know with certainty that state $\ket{\psi_i}$ from the linearly independent set $\ket{\psi_1}, \dots, \ket{\psi_m}$ was measured. This set will include $E_{m+1}$ to satisfy the completeness relation. 




$E_i = \ket{\psi_i}\bra{\psi_i}$ for $1 \leq i \leq m$ and $E_{m+1}=I - \sum_{i=1}^m E_i$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.65 {#exercise-265}

In this exercise we change the basis of two states such that they are no longer the same up to a relative phase shift. You can use the results from [exercise 2.11](#exercise-211).




We know from exercise 2.11 that one of the basis for the Pauli $X$ matrix is 

$$\begin{aligned}
\ket{+} &= \frac{\ket{0} + \ket{1}}{\sqrt{2}} \\
\ket{-} &= \frac{\ket{0} - \ket{1}}{\sqrt{2}}
\end{aligned}$$

which are the states given in the exercise. When written like this, they are not the same up to a relative phase shift. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.66 {#exercise-266}

In this exercise we are to show that the average value of the observable $X_1Z_2$ is zero for a two-qubit system measured in the state $(\ket{00} + \ket{11})/\sqrt{2}$. For this, you can reference the outer product notation for the $X$ and $Z$ operators from [exercise 2.9](#exercise-29). and use equation 2.113 with $M=X_1Z_2$.




From exercise 2.9 we know that 

$$\begin{aligned}
X &= \ket{0}\bra{1} + \ket{1}\bra{0} \\
Z &= \ket{0}\bra{0} - \ket{1}\bra{1}
\end{aligned}$$

I don't plan to actually plug these equations into anything below (though you can if you find it helpful) but I like to have them handy as reference when doing the calculation in my head. 

The state of the qubits before measurement is

$$\begin{aligned}
\ket{\psi_1} = \frac{\ket{00} + \ket{11}}{\sqrt{2}}
\end{aligned}$$

First let's calculate $X_1Z_2 \ket{\psi_1}$

$$\begin{aligned}
\ket{\psi_2} &= X_1Z_2 \ket{\psi_1} \\
&= X_1Z_2\left(\frac{\ket{00} + \ket{11}}{\sqrt{2}}\right) \\
&= \frac{X_1Z_2\ket{00} + X_1Z_2\ket{11}}{\sqrt{2}} \\
&= \frac{\ket{10} - \ket{01}}{\sqrt{2}} 
\end{aligned}$$

Then we can use equation 2.113 to calculate the average value

$$\begin{aligned}
\braket{\psi_1 \vert X_1Z_2 \vert \psi_1} &= \braket{\psi_1 \vert \psi_2} \\
&= \frac{\braket{00 \vert 10} - \braket{00 \vert 01} - \braket{11 \vert 10} + \braket{11 \vert 01}}{2} \\
&= 0
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.67 {#exercise-267}

$U$ is linear operator that preserves the inner product in $W$, which is a subspace of $V$. In this exercise we prove that there exists a unitary operator $U': V \rightarrow V$ that extends $U$. To do this, think about what you would need to add to $U$ to have it span all of $V$. Build $U'$ by adding that to $U$ and then prove that this $U'$ is unitary and satisfies $U'\ket{w} = U\ket{w}$. 




We start by writing $U = \sum_{i=1}^k \lambda_i \ket{i}\bra{i}$, with $\vert \lambda_i \vert = 1$ . To extend this we need to add elements ranging from $k+1$ to $d$. Which will give us something like $U' = \sum_{i=1}^k \lambda_i \ket{i}\bra{i} + \sum_{j=k+1}^d \lambda_j \ket{j}\bra{j}$, where $\ket{i} \cup \ket{j}$ form an orthonormal basis for $V$. Now we need to prove that $U'$ is a unitary operator and $U'\ket{w} = U\ket{w}$ for all $\ket{w}$ in $W$. 

To prove that $U'$ is unitary we need to show that $U'^\dagger U' = I$

$$\begin{aligned}
U'^\dagger U' &= \left( \sum_{i=1}^k \lambda_i \ket{i}\bra{i} + \sum_{j=k+1}^d \lambda_j \ket{j}\bra{j} \right)^\dagger \left( \sum_{i'=1}^k \lambda_{i'} \ket{i'}\bra{i'} + \sum_{j'=k+1}^d \lambda_{j'} \ket{j'}\bra{j'} \right) \\
&= \left( \sum_{i=1}^k \lambda_i^\ast \ket{i}\bra{i} + \sum_{j=k+1}^d \lambda_j^\ast \ket{j}\bra{j} \right) \left( \sum_{i'=1}^k \lambda_{i'} \ket{i'}\bra{i'} + \sum_{j'=k+1}^d \lambda_{j'} \ket{j'}\bra{j'} \right) \\
&= \sum_{i=1}^k \sum_{j=k+1}^d \sum_{i'=1}^k \sum_{j'=k+1}^d \lambda_i^\ast \lambda_{i'} \ket{i}\braket{i \vert i'}\bra{i'} + \lambda_j^\ast \lambda_{i'} \ket{j}\braket{j \vert i'}\bra{i'} + \lambda_i^\ast \lambda_{j'}\ket{i}\braket{i \vert j'}\bra{j'} + \lambda_j^\ast \lambda_{j'}\ket{j}\braket{j \vert j'}\bra{j'} \\
&= \sum_{i=1}^k \sum_{j=k+1}^d \sum_{i'=1}^k \sum_{j'=k+1}^d \lambda_i^\ast \lambda_{i'} \delta_{i i'} \ket{i}\bra{i'} + \lambda_j^\ast \lambda_{i'} \delta_{j i'} \ket{j}\bra{i'} + \lambda_i^\ast \lambda_{j'} \delta_{i j'} \ket{i}\bra{j'} + \lambda_j^\ast \lambda_{j'} \delta_{j j'}\ket{j}\bra{j'} \\
&= \sum_{i=1}^k \sum_{j=k+1}^d \vert \lambda_i \vert^2 \ket{i}\bra{i} + \vert \lambda_j \vert^2 \ket{j}\bra{j} \\
&= I & \text{if $\vert \lambda_j \vert^2 = 1$ for all $j$}
\end{aligned}$$

Therefore $U'$ is unitary if $\vert \lambda_j \vert^2 = 1$ for all $j$.

Now let's look at $U'\ket{w}$. We know that since $\ket{w}$ is in $W$ it can be written as a combination of the orthonormal basis vectors for $W$, i.e. $\ket{w} = \sum_{i=1}^k a_i \ket{i}$ for a set of complex values $a_i$. Combining this with our equation for $U'$ we get

$$\begin{aligned}
U'\ket{w} &= \left(U + \sum_{j=k+1}^d \lambda_j \ket{j}\bra{j}\right) \ket{w} \\
&= U \ket{w} + \left( \sum_{j=k+1}^d \lambda_j \ket{j}\bra{j} \right)\left( \sum_{i=1}^k a_i \ket{i} \right) \\
&= U \ket{w} + \sum_{j=k+1}^d \sum_{i=1}^k\lambda_j \ket{j} \braket{j \vert i} \\
&= U \ket{w} + \sum_{j=k+1}^d \sum_{i=1}^k\lambda_j \ket{j} \delta_{ij} \\
&= U \ket{w} 
\end{aligned}$$

Therefore $U'\ket{w} = U \ket{w}$ for all $\ket{w}$ in $W$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.68 {#exercise-268}

Prove that $\ket{\psi} \neq \ket{a}\ket{b}$ for all single qubit states $\ket{a}$ and $\ket{b}$. You may find it helpful to refer back to section 1.2.1 when solving this problem. 




From equation 1.5 we know that the state vector describing the two qubits are

$$\begin{aligned}
\ket{\psi} = \alpha_{00} \ket{00} + \alpha_{01} \ket{01} + \alpha_{10} \ket{10} + \alpha_{11} \ket{11}
\end{aligned}$$

For single qubits the state vectors are

$$\begin{aligned}
\ket{a} &= a_0 \ket{0} + a_1 \ket{1} \\
\ket{b} &= b_0 \ket{0} + b_1 \ket{1} \\
 \Rightarrow \ket{a}\ket{b} &= \left(a_0 \ket{0} + a_1 \ket{1} \right) \left(b_0 \ket{0} + b_1 \ket{1}\right) \\
 &= a_0 b_0 \ket{0} \ket{0} + a_1 b_0 \ket{1} \ket{0} + a_0 b_1 \ket{0} \ket{1} + a_1 b_1 \ket{1} \ket{1}
\end{aligned}$$

If $\ket{\psi} = \ket{a}\ket{b}$ the following must be true

$$\begin{aligned}
\alpha_{00} &= a_0 b_0 \\
\alpha_{01} &= a_0 b_1 \\
\alpha_{10} &= a_1 b_0 \\
\alpha_{11} &= a_1 b_1
\end{aligned}$$

However, there are cases where this cannot be true, such as the Bell state $\ket{\psi}=\frac{\ket{00} + \ket{11}}{\sqrt{2}}$. Here $\alpha_{00} = \alpha_{11} = \frac{1}{\sqrt{2}}$ and $\alpha_{01} = \alpha_{10} = 0$ There are no combinations of $a_0, a_1, b_0, b_1$ which would be able to represent this state. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |





## Superdense Coding

### Exercise 2.69 {#exercise-269}

In section 2.3 the authors discuss how to used an entangled pair of qubits to transfer two bits of classical information. The possible resulting states are the Bell states. In this exercise we verify that these states form an orthonormal basis for the two qubit state space. In order for these states to form an orthonormal basis, they must be orthogonal, they must be unit vectors, and they must span the state space.



  
The Bell states are

$$\begin{aligned}
\ket{\psi_1} &= \frac{\ket{00} + \ket{11}}{\sqrt{2}} \\
\ket{\psi_2} &= \frac{\ket{00} - \ket{11}}{\sqrt{2}} \\
\ket{\psi_3} &= \frac{\ket{10} + \ket{01}}{\sqrt{2}} \\
\ket{\psi_4} &= \frac{\ket{01} - \ket{10}}{\sqrt{2}} 
\end{aligned}$$

To prove that they are orthogonal we can take the inner product of different states and confirm it to be zero

$$\begin{aligned}
\braket{\psi_1 \vert \psi_2} &= \left( \frac{\bra{00} + \bra{11}}{\sqrt{2}} \right) \left(\frac{\ket{00} - \ket{11}}{\sqrt{2}} \right) \\
&= \frac{1}{2} \left( \braket{00 \vert 00} - \braket{00 \vert 11} + \braket{11 \vert 00} - \braket{11 \vert 11}\right) \\
&= \frac{1}{2}(1 - 0 + 0 - 1) \\
&= 0 
\end{aligned}$$

$$\begin{aligned}
\braket{\psi_1 \vert \psi_3} &= \left( \frac{\bra{00} + \bra{11}}{\sqrt{2}} \right) \left(\frac{\ket{10} + \ket{01}}{\sqrt{2}} \right) \\
&= \frac{1}{2} \left( \braket{00 \vert 10} + \braket{00 \vert 01} + \braket{11 \vert 10} + \braket{11 \vert 01}\right) \\
&= \frac{1}{2}(0 + 0 + 0 + 0) \\
&= 0 
\end{aligned}$$

$$\begin{aligned}
\braket{\psi_1 \vert \psi_4} &= \left( \frac{\bra{00} + \bra{11}}{\sqrt{2}} \right) \left(\frac{\ket{01} - \ket{10}}{\sqrt{2}} \right) \\
&= \frac{1}{2} \left( \braket{00 \vert 01} - \braket{00 \vert 10} + \braket{11 \vert 01} - \braket{11 \vert 10}\right) \\
&= \frac{1}{2}(0 - 0 + 0 - 0) \\
&= 0 
\end{aligned}$$

$$\begin{aligned}
\braket{\psi_2 \vert \psi_3} &= \left( \frac{\bra{00} - \bra{11}}{\sqrt{2}} \right) \left(\frac{\ket{10} + \ket{01}}{\sqrt{2}} \right) \\
&= \frac{1}{2} \left( \braket{00 \vert 10} + \braket{00 \vert 01} - \braket{11 \vert 10} - \braket{11 \vert 01}\right) \\
&= \frac{1}{2}(0 + 0 - 0 - 0) \\
&= 0 
\end{aligned}$$

$$\begin{aligned}
\braket{\psi_2 \vert \psi_4} &= \left( \frac{\bra{00} - \bra{11}}{\sqrt{2}} \right) \left(\frac{\ket{01} - \ket{10}}{\sqrt{2}} \right) \\
&= \frac{1}{2} \left( \braket{00 \vert 01} + \braket{00 \vert 10} - \braket{11 \vert 01} + \braket{11 \vert 10}\right) \\
&= \frac{1}{2}(0 + 0 - 0 + 0) \\
&= 0 
\end{aligned}$$

$$\begin{aligned}
\braket{\psi_3 \vert \psi_4} &= \left( \frac{\bra{10} + \bra{01}}{\sqrt{2}} \right) \left(\frac{\ket{01} - \ket{10}}{\sqrt{2}} \right) \\
&= \frac{1}{2} \left( \braket{10 \vert 01} - \braket{10 \vert 10} + \braket{01 \vert 01} - \braket{01 \vert 10}\right) \\
&= \frac{1}{2}(0 - 1 + 1 - 0) \\
&= 0 
\end{aligned}$$

To confirm that they are unit vectors we can take their inner product with themselves and show it is 1

$$\begin{aligned}
\braket{\psi_1 \vert \psi_1} &= \left( \frac{\bra{00} + \bra{11}}{\sqrt{2}} \right) \left(\frac{\ket{00} + \ket{11}}{\sqrt{2}} \right) \\
&= \frac{1}{2} \left( \braket{00 \vert 00} + \braket{00 \vert 11} + \braket{11 \vert 00} + \braket{11 \vert 11}\right) \\
&= \frac{1}{2}(1 + 0 + 0 + 1) \\
&= 1
\end{aligned}$$

$$\begin{aligned}
\braket{\psi_2 \vert \psi_2} &= \left( \frac{\bra{00} - \bra{11}}{\sqrt{2}} \right) \left(\frac{\ket{00} - \ket{11}}{\sqrt{2}} \right) \\
&= \frac{1}{2} \left( \braket{00 \vert 00} - \braket{00 \vert 11} - \braket{11 \vert 00} + \braket{11 \vert 11}\right) \\
&= \frac{1}{2}(1 - 0 - 0 + 1) \\
&= 1
\end{aligned}$$

$$\begin{aligned}
\braket{\psi_3 \vert \psi_3} &= \left( \frac{\bra{10} + \bra{01}}{\sqrt{2}} \right) \left(\frac{\ket{10} + \ket{01}}{\sqrt{2}} \right) \\
&= \frac{1}{2} \left( \braket{10 \vert 10} + \braket{10 \vert 01} + \braket{01 \vert 10} + \braket{01 \vert 01}\right) \\
&= \frac{1}{2}(1 + 0 + 0 + 1) \\
&= 1
\end{aligned}$$

$$\begin{aligned}
\braket{\psi_4 \vert \psi_4} &= \left( \frac{\bra{01} - \bra{10}}{\sqrt{2}} \right) \left(\frac{\ket{01} - \ket{10}}{\sqrt{2}} \right) \\
&= \frac{1}{2} \left( \braket{01 \vert 01} - \braket{01 \vert 10} - \braket{10 \vert 01} + \braket{10 \vert 10}\right) \\
&= \frac{1}{2}(1 - 0 - 0 + 1) \\
&= 1
\end{aligned}$$

The state space is $2x2$ dimensions and therefore we need $4$ vectors to form a basis that spans the state space. There are $4$ Bell states which are orthonormal, therefore they form an orthonormal basis set. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.70 {#exercise-270}

Show that $\braket{\psi \vert E \otimes I \vert \psi}$ takes the same value when $\psi$ is any of the four Bell states for some positive operator $E$. Then use the results to answer the second half of the question: if Alice's qubit was intercepted on its way to Bob, would the person who intercepted it be able to determine anything?




For $\ket{\psi} = \frac{\ket{00} + \ket{11}}{\sqrt{2}}$, 

$$\begin{aligned}
\braket{\psi \vert E \otimes I \vert \psi} &= \left( \frac{\bra{00} + \bra{11}}{\sqrt{2}} \right) E \otimes I \left( \frac{\ket{00} + \ket{11}}{\sqrt{2}} \right) \\
&= \frac{1}{2}\left( \braket{00 \vert E \otimes I \vert 00} + \braket{00 \vert E \otimes I \vert 11} + \braket{11 \vert E \otimes I \vert 00} + \braket{11 \vert E \otimes I \vert 11}\right) \\
&= \frac{1}{2}\left( \braket{0 \vert E \vert 0} \braket{0 \vert 0} + \braket{0 \vert E \vert 1}  \braket{0 \vert 1} + \braket{1 \vert E \vert 0}  \braket{1 \vert 0} + \braket{1 \vert E \vert 1}  \braket{1 \vert 1} \right) \\
&= \frac{1}{2}\left( \braket{0 \vert E \vert 0} + \braket{1 \vert E \vert 1} \right)
\end{aligned}$$

For $\ket{\psi} = \frac{\ket{00} - \ket{11}}{\sqrt{2}}$, 

$$\begin{aligned}
\braket{\psi \vert E \otimes I \vert \psi} &= \left( \frac{\bra{00} - \bra{11}}{\sqrt{2}} \right) E \otimes I \left( \frac{\ket{00} - \ket{11}}{\sqrt{2}} \right) \\
&= \frac{1}{2}\left( \braket{00 \vert E \otimes I \vert 00} - \braket{00 \vert E \otimes I \vert 11} - \braket{11 \vert E \otimes I \vert 00} + \braket{11 \vert E \otimes I \vert 11}\right) \\
&= \frac{1}{2}\left( \braket{0 \vert E \vert 0} \braket{0 \vert 0} - \braket{0 \vert E \vert 1}  \braket{0 \vert 1} - \braket{1 \vert E \vert 0}  \braket{1 \vert 0} + \braket{1 \vert E \vert 1}  \braket{1 \vert 1} \right) \\
&= \frac{1}{2}\left( \braket{0 \vert E \vert 0} + \braket{1 \vert E \vert 1} \right)
\end{aligned}$$

For $\ket{\psi} = \frac{\ket{10} + \ket{01}}{\sqrt{2}}$, 

$$\begin{aligned}
\braket{\psi \vert E \otimes I \vert \psi} &= \left( \frac{\bra{01} + \bra{10}}{\sqrt{2}} \right) E \otimes I \left( \frac{\ket{01} + \ket{10}}{\sqrt{2}} \right) \\
&= \frac{1}{2}\left( \braket{01 \vert E \otimes I \vert 01} + \braket{01 \vert E \otimes I \vert 10} + \braket{10 \vert E \otimes I \vert 01} + \braket{10 \vert E \otimes I \vert 10}\right) \\
&= \frac{1}{2}\left( \braket{0 \vert E \vert 0} \braket{1 \vert 1} + \braket{0 \vert E \vert 1}  \braket{1 \vert 0} + \braket{1 \vert E \vert 0}  \braket{0 \vert 1} + \braket{1 \vert E \vert 1}  \braket{0 \vert 0} \right) \\
&= \frac{1}{2}\left( \braket{0 \vert E \vert 0} + \braket{1 \vert E \vert 1} \right)
\end{aligned}$$

For $\ket{\psi} = \frac{\ket{10} - \ket{01}}{\sqrt{2}}$, 

$$\begin{aligned}
\braket{\psi \vert E \otimes I \vert \psi} &= \left( \frac{\bra{01} - \bra{10}}{\sqrt{2}} \right) E \otimes I \left( \frac{\ket{01} - \ket{10}}{\sqrt{2}} \right) \\
&= \frac{1}{2}\left( \braket{01 \vert E \otimes I \vert 01} - \braket{01 \vert E \otimes I \vert 10} - \braket{10 \vert E \otimes I \vert 01} + \braket{10 \vert E \otimes I \vert 10}\right) \\
&= \frac{1}{2}\left( \braket{0 \vert E \vert 0} \braket{1 \vert 1} - \braket{0 \vert E \vert 1}  \braket{1 \vert 0} - \braket{1 \vert E \vert 0}  \braket{0 \vert 1} + \braket{1 \vert E \vert 1}  \braket{0 \vert 0} \right) \\
&= \frac{1}{2}\left( \braket{0 \vert E \vert 0} + \braket{1 \vert E \vert 1} \right)
\end{aligned}$$

Therefore $\braket{\psi \vert E \otimes I \vert \psi}$ is the same for all four Bell states.

If Alice's qubit was intercepted on its way to Bob, the person who intercepted it would not be able to infer anything from it since, as was just demonstrated, both qubits need to be measured in order to distinguish between the different states. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## The Density Operator

### Exercise 2.71 {#exercise-271}

In this exercise we show that $\text{tr} ( \rho^2 ) \leq 1$ with equality only if $\rho$ is a pure state using the definition of $\rho$ and the fact that $\sum_i p_i = 1$.




$$\begin{aligned}
\text{tr} ( \rho^2 ) &= \text{tr} \left( \left( \sum_{i} p_i \ket{\psi_i}\bra{\psi_i} \right) \left( \sum_{i'} p_{i'} \ket{\psi_{i'}}\bra{\psi_{i'}} \right) \right) \\
&= \text{tr} \left( \sum_{i} \sum_{i'} p_i p_{i'} \ket{\psi_i}\braket{\psi_i \vert \psi_{i'}}\bra{\psi_{i'}}  \right) \\
&= \text{tr} \left( \sum_{i} \sum_{i'} p_i p_{i'} \delta_{ii'} \ket{\psi_i}\bra{\psi_{i'}}  \right) \\
&= \text{tr} \left( \sum_{i} p_i^2 \ket{\psi_i}\bra{\psi_{i}}  \right) \\
&= \sum_{i} p_i^2
\end{aligned}$$

We know that $\sum_i p_i = 1$. If $\rho$ is a pure state, there is only one $p_i$ and it is equal to $1$. Therefore $\text{tr} ( \rho^2 ) = 1$.

When $\rho$ is a mixed state, there are multiple $p_i$ which add up to $1$. Since each $p_i$ is less than $1$, $p_i^2 < p_i$. Therefore $\sum_i p_i^2 < \sum_i p_i = 1$.

This proves that $\text{tr} ( \rho^2 ) \leq 1$ with equality only if $\rho$ is a pure state. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.72 {#exercise-272}

For this exercise we are asked to derive some of the properties of the Bloch sphere for mixed states. For the first part we are to show that an arbitrary density matrix for a mixed state can be written as equation 2.175. To do this we will use the results from [Exercise 2.60](#exercise-260) where we found the projectors for the pure states on the Bloch sphere. From the results of the first part, the second and third parts are straight forward. For the fourth part we need to derive the density matrix for a pure state starting with equation 1.4.




(1) In exercise 2.60 we showed that $\vec{v} \cdot \vec{\sigma}$ has eigenvalues $\pm 1$ and that the projectors onto the corresponding eigenspaces are given by $P_{\pm}=(I \pm \vec{v} \cdot \vec{\sigma})/2 = \ket{\lambda_{\pm}}\bra{\lambda_{\pm}}$. If $p_+$ is the probability of being in state $\lambda_+$ and $p_-$ is the probability of being in state $\lambda_-$ and $p_- + p_+ = 1$ then the density matrix is given by

$$\begin{aligned}
\rho &= p_+ \ket{\lambda_{+}}\bra{\lambda_{+}} + p_- \ket{\lambda_{-}}\bra{\lambda_{-}} \\
&= p_+ P_+ + p_- P_- \\
&= p_+ \frac{I + \vec{v} \cdot \vec{\sigma}}{2} + p_- \frac{I - \vec{v} \cdot \vec{\sigma}}{2} \\
&= \frac{(p_+ + p_-)I + (p_+ - p_-)\vec{v} \cdot \vec{\sigma}}{2} \\
&= \frac{I+ (p_+ - p_-)\vec{v} \cdot \vec{\sigma}}{2}
\end{aligned}$$

We can set $\vec{r} = (p_+ - p_-)\vec{v}$ and then we get $\rho = \frac{I+\vec{r} \cdot \vec{\sigma}}{2}$. Here, we know that $\Vert \vec{r} \Vert = \vert p_+ - p_- \vert \leq 1$ since both $p_-$ and $p_+$ are positive, $p_+ + p_- = 1$, and $\Vert \vec{v} \Vert = 1$.

(2) If $\rho = \frac{I}{2}$ then $r=0$.

(3) A state $\rho$ is pure when if it is constructed with only a pure state, i.e. when either $p_-$ or $p_+$ is $1$ and the other is $0$. Therefore $\Vert \vec{r} \Vert = \vert p_+ - p_- \vert = 1$. 

(4) In section 1.2 the description of the Bloch vector is given by $\ket{\psi} = \cos\frac{\theta}{2}\ket{0} + e^{i\phi} \sin\frac{\theta}{2}\ket{1}$. Therefore, for a pure state the density operator can be given by 

$$\begin{aligned}
\rho &= \ket{\psi}\bra{\psi} \\
&= \left(\cos\frac{\theta}{2}\ket{0} + e^{i\phi} \sin\frac{\theta}{2}\ket{1} \right)\left(\cos\frac{\theta}{2}\bra{0} + e^{-i\phi} \sin\frac{\theta}{2}\bra{1} \right) \\
&= \cos^2\frac{\theta}{2}\ket{0}\bra{0} + e^{-i\phi}\cos\frac{\theta}{2}\sin\frac{\theta}{2}\ket{0}\bra{1} + e^{i\phi} \sin\frac{\theta}{2}\cos\frac{\theta}{2}\ket{1}\bra{0} + \sin^2\frac{\theta}{2}\ket{1}\bra{1} \\
&= \frac{1 + \cos\theta }{2}\ket{0}\bra{0} + \frac{e^{-i\phi}\sin\theta}{2}\ket{0}\bra{1} + \frac{e^{i\phi}\sin\theta}{2}\ket{1}\bra{0} + \frac{1 - \cos\theta }{2}\ket{1}\bra{1} \\
&= \frac{1}{2}\left(\ket{0}\bra{0} + \ket{1}\bra{1} \right) + \left(\frac{\cos\theta }{2}\ket{0}\bra{0} - \frac{\cos\theta }{2}\ket{1}\bra{1} \right) + \left( \frac{e^{-i\phi}\sin\theta}{2}\ket{0}\bra{1} + \frac{e^{i\phi}\sin\theta}{2}\ket{1}\bra{0} \right) \\
&= \frac{I + \cos\theta Z + \left(\cos(-\phi) + i\sin(-\phi) \right)\sin\theta\ket{0}\bra{1} + \left(\cos(\phi) + i\sin(\phi) \right) \sin\theta\ket{1}\bra{0} }{2} \\
&= \frac{I + \cos\theta Z + \left(\cos(\phi) - i\sin(\phi) \right)\sin\theta\ket{0}\bra{1} + \left(\cos(\phi) + i\sin(\phi) \right) \sin\theta\ket{1}\bra{0} }{2} \\
&= \frac{I + \cos\theta Z + \cos(\phi)\sin\theta X +  \sin(\phi)\sin\theta Y}{2} \\
&= \frac{I + \vec{v} \cdot \vec{\sigma}}{2}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.73 {#exercise-273}

For this exercise we use theorem 2.6 to demonstrate that for any state $\ket{\psi}$ in support of $\rho$ there is a minimal ensemble for $\rho$ that contains $\ket{\psi}$ and also calculate the probability of $\ket{\psi}$.  




The density operator can be written as $\rho = \sum_{j} q_j \ket{\phi_j} \bra{\phi_j}$ with $\lbrace q_j \vert \ket{\phi_j} \rbrace$ as a minimal ensemble for $\rho$ that is made up of orthonormal states $\ket{\phi_j}$. Since $\ket{\psi}$ is in support of $\rho$, it can be written as a linear combination of the vectors $\ket{\phi_j}$, therefore $\ket{\psi} =\ket{\tilde{\psi_i}} = \sqrt{p_i} \ket{\psi_i} = \sqrt{p_i} \sum_j a_{ij} \ket{\phi_j}$ for some values of $a_{ij}$.

Using theorem 2.6, if there is a minimal ensemble for $\rho$ that contains $\ket{\psi}$ then the following is true for some unitary matrix given by $u_{ij}$

$$\begin{aligned}
\sum_{j} u_{ij} \sqrt{q_j}\ket{\phi_j} &= \sqrt{p_i}\ket{\psi_i} \\
&= \sum_j a_{ij} \sqrt{p_i}\ket{\phi_j}
\end{aligned}$$

Looking at the above equation, we can see that we need to show that $u_{ij} = a_{ij}\sqrt{\frac{p_i}{q_j}}$ are the elements of a unitary matrix. Therefore we need to show  

$$\begin{aligned}
I_{ij} &= \sum_{k} \left(a_{ik}\frac{\sqrt{p_i}}{\sqrt{q_k}}\right) \left( a_{kj} \frac{\sqrt{p_k}}{\sqrt{q_j}} \right)^\dagger \\
&= \sum_{k} \left(a_{ik}\frac{\sqrt{p_i}}{\sqrt{q_k}}\right) \left( a_{jk}^\ast \frac{\sqrt{p_j}}{\sqrt{q_k}} \right) \\
&= \sum_{k} a_{ik} a_{jk}^\ast \frac{\sqrt{p_i p_j}}{q_k}
\end{aligned}$$

Which means that the following conditions need to be true

$$\begin{aligned}
1 &= \sum_{k} \vert a_{ik} \vert^2 \frac{p_i}{q_k}& \text{for $j=i$} \\
0 &= \sum_{k} a_{ik}a_{jk}^\ast \frac{\sqrt{p_i p_j}}{q_k} & \text{for $j \neq i$}
\end{aligned}$$

Solving the first condition for $p_i^{-1}$ we get

$$\begin{aligned}
p_i^{-1} &= \sum_{k}\frac{q_k}{\vert a_{ik} \vert^2}
\end{aligned}$$

We know that the inverse of $\rho$ is given by $\rho^{-1} = \sum_j \frac{1}{q_j} \ket{\phi_j} \bra{\phi_j}$. Therefore

$$\begin{aligned}
\braket{\psi_i \vert \rho^{-1} \vert \psi_i } &= \sum_j \frac{1}{q_j} \braket{\psi_i \vert \phi_j} \braket{\phi_j \vert \psi_i} \\
&= \sum_j \frac{\vert a_{ij} \vert^2}{q_j} \\
&= p_i^{-1}
\end{aligned}$$

and so for this ensemble this must be true to satisfy the first condition

$$\begin{aligned}
p_i = \frac{1}{\braket{\psi_i \vert \rho_{-1} \vert \psi_i }}
\end{aligned}$$

If you take the inner product of $\ket{\psi}$ with other members of the ensemble, it should equal $0$ as long as the ensemble that you constructed $\lbrace p_i \vert \ket{\psi_i} \rbrace$ is orthogonal (which it should be since it is a minimal ensemble), therefore

$$\begin{aligned}
0 &= \braket{\tilde{\psi_j} \vert \tilde{\psi_i}} & \text{when $i \neq j$}\\
&= \sqrt{p_i p_j}\braket{\psi_j \vert \psi_i}\\
&= \sum_{kk'} a_{ik} a_{jk'}^\ast \sqrt{p_i p_j} \braket{\phi_k \vert \phi_{k'}} \\
&= \sum_{kk'} a_{ik} a_{jk'}^\ast\frac{\sqrt{p_i p_j}}{\sqrt{q_k q_{k'}}} \braket{\tilde{\phi_k} \vert \tilde{\phi_{k'}}} \\
&= \sum_{k} a_{ik} a_{jk}^\ast\frac{\sqrt{p_i p_j}}{q_k} 
\end{aligned}$$

Going back to the second condition, we can see that this is met. Therefore $u_{ij}=a_{ij}\sqrt{\frac{p_i}{q_j}}$ are elements of a unitary matrix and so we can use theorem 2.6 to show that there is a minimal ensemble for $\rho$ that contains $\ket{\psi}$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.74 {#exercise-274}

Suppose a composite state of systems $A$ and $B$ is in state $\ket{a}\ket{b}$, show that the reduced density operator of system $A$ is a pure state. This is done using equations 2.177 and 2.178.




First we need to construct the density matrix for the composite system

$$\begin{aligned}
\rho^{AB} = \ket{a}\bra{a} \otimes \ket{b}\bra{b}
\end{aligned}$$

Now we'll use equations 2.177 and 2.178 to find $\rho^A$

$$\begin{aligned}
\rho^A &= \text{tr}_B(\rho^{AB}) \\
&= \text{tr}_B(\ket{a}\bra{a} \otimes \ket{b}\bra{b}) \\
&= \ket{a}\bra{a} \text{tr}(\ket{b}\bra{b}) \\
&= \ket{a}\bra{a} \braket{b \vert b}\\
&= \ket{a}\bra{a}
\end{aligned}$$

This describes a pure state.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.75 {#exercise-275}

In this exercise we find the reduced density operator for each qubit for each of the four Bell states. The authors already did this for one of the qubits for one of the Bell states in equations 2.185 - 2.191. 




First let's look at the Bell state $\frac{\ket{00} + \ket{11}}{\sqrt{2}}$. The authors already found $\rho^1$, so let's find $\rho^2$ using the same methodology.

$$\begin{aligned}
\rho^2 &= \text{tr}_1(\rho) \\
&= \frac{\text{tr}_1(\ket{00}\bra{00}) + \text{tr}_1(\ket{11}\bra{00}) + \text{tr}_1(\ket{00}\bra{11}) + \text{tr}_1(\ket{11}\bra{11})}{2} \\
&= \frac{\ket{0}\bra{0} \braket{0 \vert 0} + \ket{1}\bra{0} \braket{0 \vert 1} + \ket{0}\bra{1} \braket{1 \vert 0} + \ket{1}\bra{1} \braket{1 \vert 1}}{2} \\
&= \frac{\ket{0}\bra{0}  + \ket{1}\bra{1} }{2} \\
&= \frac{I}{2}
\end{aligned}$$

Now let's look at the Bell state $\frac{\ket{00} - \ket{11}}{\sqrt{2}}$

The density operator is given by 

$$\begin{aligned}
\rho &= \left(\frac{\ket{00} - \ket{11}}{\sqrt{2}} \right)\left(\frac{\bra{00} - \bra{11}}{\sqrt{2}} \right)\\
&= \frac{\ket{00}\bra{00} - \ket{00}\bra{11} - \ket{11}\bra{00} +\ket{11}\bra{11}}{2}
\end{aligned}$$

and so the density operators of the individual qubits are

$$\begin{aligned}
\rho^1 &= \text{tr}_2(\rho) \\
&= \frac{\text{tr}_2(\ket{00}\bra{00}) - \text{tr}_2(\ket{11}\bra{00}) - \text{tr}_2(\ket{00}\bra{11}) + \text{tr}_2(\ket{11}\bra{11})}{2} \\
&= \frac{\ket{0}\bra{0} \braket{0 \vert 0} - \ket{1}\bra{0} \braket{0 \vert 1} - \ket{0}\bra{1} \braket{1 \vert 0} + \ket{1}\bra{1} \braket{1 \vert 1}}{2} \\
&= \frac{\ket{0}\bra{0}  + \ket{1}\bra{1} }{2} \\
&= \frac{I}{2}
\end{aligned}$$

$$\begin{aligned}
\rho^2 &= \text{tr}_1(\rho) \\
&= \frac{\text{tr}_1(\ket{00}\bra{00}) - \text{tr}_1(\ket{11}\bra{00}) - \text{tr}_1(\ket{00}\bra{11}) + \text{tr}_1(\ket{11}\bra{11})}{2} \\
&= \frac{\ket{0}\bra{0} \braket{0 \vert 0} - \ket{1}\bra{0} \braket{0 \vert 1} - \ket{0}\bra{1} \braket{1 \vert 0} + \ket{1}\bra{1} \braket{1 \vert 1}}{2} \\
&= \frac{\ket{0}\bra{0}  + \ket{1}\bra{1} }{2} \\
&= \frac{I}{2}
\end{aligned}$$


Then let's look at the Bell state $\frac{\ket{01} + \ket{10}}{\sqrt{2}}$

The density operator is given by 

$$\begin{aligned}
\rho &= \left(\frac{\ket{01} + \ket{10}}{\sqrt{2}} \right)\left(\frac{\bra{01} + \bra{10}}{\sqrt{2}} \right)\\
&= \frac{\ket{01}\bra{01} + \ket{01}\bra{10} + \ket{10}\bra{01} +\ket{10}\bra{10}}{2}
\end{aligned}$$

and so the density operators of the individual qubits are

$$\begin{aligned}
\rho^1 &= \text{tr}_2(\rho) \\
&= \frac{\text{tr}_2(\ket{01}\bra{01}) + \text{tr}_2(\ket{01}\bra{10}) + \text{tr}_2(\ket{10}\bra{01}) + \text{tr}_2(\ket{10}\bra{10})}{2} \\
&= \frac{\ket{0}\bra{0} \braket{1 \vert 1} + \ket{0}\bra{1} \braket{0 \vert 1} + \ket{1}\bra{0} \braket{1 \vert 0} + \ket{1}\bra{1} \braket{0 \vert 0}}{2} \\
&= \frac{\ket{0}\bra{0}  + \ket{1}\bra{1} }{2} \\
&= \frac{I}{2}
\end{aligned}$$

$$\begin{aligned}
\rho^2 &= \text{tr}_1(\rho) \\
&= \frac{\text{tr}_1(\ket{01}\bra{01}) + \text{tr}_1(\ket{01}\bra{10}) + \text{tr}_1(\ket{10}\bra{01}) + \text{tr}_1(\ket{10}\bra{10})}{2} \\
&= \frac{\ket{1}\bra{1} \braket{0 \vert 0} + \ket{1}\bra{0} \braket{0 \vert 0} + \ket{0}\bra{1} \braket{0 \vert 1} + \ket{0}\bra{0} \braket{1 \vert 1}}{2} \\
&= \frac{\ket{1}\bra{1} + \ket{0}\bra{0}}{2} \\
&= \frac{I}{2}
\end{aligned}$$

Finally let's look at the Bell state $\frac{\ket{01} - \ket{10}}{\sqrt{2}}$

The density operator is given by 

$$\begin{aligned}
\rho &= \left(\frac{\ket{01} - \ket{10}}{\sqrt{2}} \right)\left(\frac{\bra{01} - \bra{10}}{\sqrt{2}} \right)\\
&= \frac{\ket{01}\bra{01} - \ket{01}\bra{10} - \ket{10}\bra{01} +\ket{10}\bra{10}}{2}
\end{aligned}$$

and so the density operators of the individual qubits are

$$\begin{aligned}
\rho^1 &= \text{tr}_2(\rho) \\
&= \frac{\text{tr}_2(\ket{01}\bra{01}) - \text{tr}_2(\ket{01}\bra{10}) - \text{tr}_2(\ket{10}\bra{01}) + \text{tr}_2(\ket{10}\bra{10})}{2} \\
&= \frac{\ket{0}\bra{0} \braket{1 \vert 1} - \ket{0}\bra{1} \braket{0 \vert 1} - \ket{1}\bra{0} \braket{1 \vert 0} + \ket{1}\bra{1} \braket{0 \vert 0}}{2} \\
&= \frac{\ket{0}\bra{0}  + \ket{1}\bra{1} }{2} \\
&= \frac{I}{2}
\end{aligned}$$

$$\begin{aligned}
\rho^2 &= \text{tr}_1(\rho) \\
&= \frac{\text{tr}_1(\ket{01}\bra{01}) - \text{tr}_1(\ket{01}\bra{10}) - \text{tr}_1(\ket{10}\bra{01}) + \text{tr}_1(\ket{10}\bra{10})}{2} \\
&= \frac{\ket{1}\bra{1} \braket{0 \vert 0} - \ket{1}\bra{0} \braket{1 \vert 0} - \ket{0}\bra{1} \braket{0 \vert 1} + \ket{0}\bra{0} \braket{1 \vert 1}}{2} \\
&= \frac{\ket{1}\bra{1} + \ket{0}\bra{0}}{2} \\
&= \frac{I}{2}
\end{aligned}$$

So for all Bell states the density operator of a single qubit is given by $\frac{I}{2}$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## The Schmidt decomposition and purifications

### Exercise 2.76 {#exercise-276}

In this exercise we extend the Schmidt decomposition proof to include $A$ and $B$ with different dimensionality. It is useful to look up singular value decomposition for non-square matrices to complete this exercise. 




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
u = \begin{bmatrix} u' & u'' \end{bmatrix}
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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.77 {#exercise-277}

In this exercise we are to show that Schmidt decomposition would not always work for a three component quantum system. This is done by picking a state which it doesn't work for and then demonstrating that the different reduced density matrices for the different components have different Schmidt coefficients. 




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
&= \text{tr}_B\left(\text{tr}_C\left(\frac{\ket{0}\ket{0}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{0}\ket{0}\ket{0}\bra{1}\bra{1}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{1}\bra{1}\bra{0}}{2}\right)\right)\\
&= \text{tr}_B\left(\frac{\ket{0}\ket{0}\bra{0}\bra{0} \braket{0 \vert 0}+ \ket{0}\ket{0}\bra{1}\bra{1}\braket{0 \vert 0} + \ket{1}\ket{1}\bra{0}\bra{0}\braket{0 \vert 0} + \ket{1}\ket{1}\bra{1}\bra{1}\braket{0 \vert 0}}{2}\right) \\
&= \text{tr}_B\left(\frac{\ket{0}\ket{0}\bra{0}\bra{0}+ \ket{0}\ket{0}\bra{1}\bra{1} + \ket{1}\ket{1}\bra{0}\bra{0} + \ket{1}\ket{1}\bra{1}\bra{1}}{2}\right) \\
&= \frac{\ket{0}\bra{0}\braket{0 \vert 0} + \ket{0}\bra{1}\braket{1 \vert 0} + \ket{1}\bra{0}\braket{0 \vert 1} + \ket{1}\bra{1}\braket{1 \vert 1}}{2} \\
&= \frac{\ket{0}\bra{0} + \ket{1}\bra{1}}{2} \\
\end{aligned}$$

$$\begin{aligned}
\rho^B &= \text{tr}_A(\text{tr}_C(\rho^{ABC}))\\
&= \text{tr}_A\left(\text{tr}_C\left(\frac{\ket{0}\ket{0}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{0}\ket{0}\ket{0}\bra{1}\bra{1}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{1}\bra{1}\bra{0}}{2}\right)\right)\\
&= \text{tr}_A\left(\frac{\ket{0}\ket{0}\bra{0}\bra{0} \braket{0 \vert 0}+ \ket{0}\ket{0}\bra{1}\bra{1}\braket{0 \vert 0} + \ket{1}\ket{1}\bra{0}\bra{0}\braket{0 \vert 0} + \ket{1}\ket{1}\bra{1}\bra{1}\braket{0 \vert 0}}{2}\right) \\
&= \text{tr}_A\left(\frac{\ket{0}\ket{0}\bra{0}\bra{0}+ \ket{0}\ket{0}\bra{1}\bra{1} + \ket{1}\ket{1}\bra{0}\bra{0} + \ket{1}\ket{1}\bra{1}\bra{1}}{2}\right) \\
&= \frac{\ket{0}\bra{0}\braket{0 \vert 0} + \ket{0}\bra{1}\braket{1 \vert 0} + \ket{1}\bra{0}\braket{0 \vert 1} + \ket{1}\bra{1}\braket{1 \vert 1}}{2} \\
&= \frac{\ket{0}\bra{0} + \ket{1}\bra{1}}{2} \\
\end{aligned}$$

$$\begin{aligned}
\rho^C &= \text{tr}_B(\text{tr}_A(\rho^{ABC}))\\
&= \text{tr}_B\left(\text{tr}_A\left(\frac{\ket{0}\ket{0}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{0}\ket{0}\ket{0}\bra{1}\bra{1}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{0}\bra{0}\bra{0} + \ket{1}\ket{1}\ket{0}\bra{1}\bra{1}\bra{0}}{2}\right)\right)\\
&= \text{tr}_B\left(\frac{\ket{0}\ket{0}\bra{0}\bra{0}\braket{0 \vert 0} + \ket{0}\ket{0}\bra{1}\bra{0} \braket{1 \vert 0}  + \ket{1}\ket{0}\bra{0}\bra{0}\braket{0 \vert 1}  + \ket{1}\ket{0}\bra{1}\bra{0}\braket{1 \vert 1} }{2}\right)\\
&= \text{tr}_B\left(\frac{\ket{0}\ket{0}\bra{0}\bra{0} + \ket{1}\ket{0}\bra{1}\bra{0}}{2}\right)\\
&= \frac{\ket{0}\bra{0}\braket{0 \vert 0} + \ket{0}\bra{0}\braket{1 \vert 1}}{2}\\
&= \ket{0}\bra{0} \\
\end{aligned}$$

By Schmidt decomposition we should be able to write $\rho^A = \sum_i \lambda_i^2 \ket{i_A}\bra{i_A}$, $\rho^B = \sum_i \lambda_i^2 \ket{i_B}\bra{i_B}$, and $\rho^C = \sum_i \lambda_i^2 \ket{i_C}\bra{i_C}$ for some values of $\lambda_i^2$. For $\rho^A$ and $\rho^B$ there are two Schmidt coefficients that are both $\lambda_i^2 = \frac{1}{2}$. For $\rho^C$ the Schmidt coefficients are $\lambda_1^2 = 1$ and $\lambda_2^2 = 0$. Since these are not the same for all three components, we are unable to write the quantum states in the form given by equation 2.206.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.78 {#exercise-278}

Product states are multi-qubit states that can be represented as simple combinations of individual qubit states - i.e. the qubits are not entangled. In this exercise we are to prove that a state of a composite system is a product state only if it has a Schmidt number of 1 and its reduced density matrices are pure states. I was unsure what the authors wanted for this solution since, if you just compare equation 2.202 to state $\ket{\psi} = \ket{a}\ket{b}$ for pure states $\ket{a}$ and $\ket{b}$, the answer seems obvious. But just pointing that out didn't seem like enough, so I started with a composite of two arbitrary single qubit pure states and then followed similar steps shown in the proof for Schmidt decomposition. 




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

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 2.79 {#exercise-279}

In this exercise we are to find the Schmidt decomposition of three given states. For states that are not already written as a Schmidt decomposition, you can find their eigenvalues and eigenvectors using the reduced density matrices. 




Let's look at the first given state

$$\begin{aligned}
\ket{\psi} &= \frac{\ket{00} + \ket{11}}{\sqrt{2}} \\
\end{aligned}$$

This state is already written as a Schmidt decomposition with $\lambda_1 = \lambda_2 = \frac{1}{\sqrt{2}}$, $\ket{1_A} = \ket{0}$, $\ket{2_A} = \ket{1}$, $\ket{1_B} = \ket{0}$, and $\ket{2_B} = \ket{1}$.


Moving on to the second state

$$\begin{aligned}
\ket{\psi} &= \frac{\ket{00} + \ket{01} + \ket{10} + \ket{11}}{2} \\
\end{aligned}$$

First let's calculate the reduced density matrix for $A$

$$\begin{aligned}
\rho^A &= \text{tr}_B \left(\left( \frac{\ket{00} + \ket{01} + \ket{10} + \ket{11}}{2} \right) \left( \frac{\bra{00} + \bra{01} + \bra{10} + \bra{11}}{2} \right) \right) \\
&= \frac{\ket{0}\bra{0} + \ket{0}\bra{1} + \ket{1}\bra{0} + \ket{1}\bra{1}}{2} \\
&= \begin{bmatrix} \frac{1}{2} & \frac{1}{2} \\\ \frac{1}{2} & \frac{1}{2} \end{bmatrix}
\end{aligned}$$

Now let's find the eigenvalues for this matrix

$$\begin{aligned}
0 &= \text{det} \left(\begin{bmatrix} \frac{1}{2} & \frac{1}{2} \\\ \frac{1}{2} & \frac{1}{2} \end{bmatrix} - \begin{bmatrix} \lambda & 0 \\\ 0 & \lambda \end{bmatrix} \right) \\
&= \text{det} \left(\begin{bmatrix} \frac{1}{2} - \lambda & \frac{1}{2} \\\ \frac{1}{2} & \frac{1}{2} - \lambda \end{bmatrix} \right) \\
&= \left(\frac{1}{2} - \lambda \right)^2 - \frac{1}{4} \\
&= \lambda^2 - \lambda 
\end{aligned}$$

Therefore $\lambda_1 = 1$ and $\lambda_2=0$. 

The eigenvector for $\lambda_1 = 1$ can be found by solving for

$$\begin{aligned}
0 &= \begin{bmatrix} \frac{1}{2} - 1 & \frac{1}{2} \\\ \frac{1}{2} & \frac{1}{2} - 1 \end{bmatrix} \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} -\frac{1}{2} x_1 + \frac{1}{2} x_2 \\\ \frac{1}{2}x_1 + -\frac{1}{2} x_2 \end{bmatrix}
\end{aligned}$$

Which means $x_1 = x_2$ and so the normalized eigenvector is $\ket{1_A} = \frac{1}{\sqrt{2}}(\ket{0} + \ket{1})$. It can be seen that state $B$ has the same reduced density matrix and therefore the same eigenvectors and eigenvalues. Therefore the Schmidt decomposition can be written as

$$\begin{aligned}
\ket{\psi} = \left( \frac{1}{\sqrt{2}}(\ket{0} + \ket{1}) \right)\left( \frac{1}{\sqrt{2}}(\ket{0} + \ket{1}) \right)
\end{aligned}$$

Finally, we'll look at the third state

$$\begin{aligned}
\ket{\psi} &= \frac{\ket{00} + \ket{01} + \ket{10}}{\sqrt{3}} \\
\end{aligned}$$

We'll first caclulate the reduced density matrix for $A$

$$\begin{aligned}
\rho^A &= \text{tr} \left(\left(\frac{\ket{00} + \ket{01} + \ket{10}}{\sqrt{3}} \right)\left(\frac{\bra{00} + \bra{01} + \bra{10}}{\sqrt{3}} \right) \right)\\
&=\frac{2\ket{0}\bra{0} + \ket{0}\bra{1} + \ket{1}\bra{0} + \ket{1}\bra{1}}{3} \\
&= \begin{bmatrix} \frac{2}{3} & \frac{1}{3} \\\ \frac{1}{3} & \frac{1}{3} \end{bmatrix}
\end{aligned}$$

Now let's find the eigenvalues for this matrix

$$\begin{aligned}
0 &= \text{det} \left(\begin{bmatrix} \frac{2}{3} & \frac{1}{3} \\\ \frac{1}{3} & \frac{1}{3} \end{bmatrix} - \begin{bmatrix} \lambda & 0 \\\ 0 & \lambda \end{bmatrix} \right) \\
&= \text{det} \left(\begin{bmatrix} \frac{2}{3} - \lambda & \frac{1}{3} \\\ \frac{1}{3} & \frac{1}{3} - \lambda \end{bmatrix} \right) \\
&= \left(\frac{2}{3} - \lambda \right) \left(\frac{1}{3} - \lambda \right) - \frac{1}{9} \\
&= \frac{1}{9} - \lambda  + \lambda^2 
\end{aligned}$$

Therefore the eigenvalues are $\lambda_{\pm} = \frac{3 \pm \sqrt{5}}{6}$.

The eigenvectors then can be found by solving

$$\begin{aligned}
0 &=  \begin{bmatrix} \frac{2}{3} - \lambda_{\pm} & \frac{1}{3} \\\ \frac{1}{3} & \frac{1}{3} - \lambda_{\pm} \end{bmatrix} \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix} \\
&= \begin{bmatrix} x_1 \left(\frac{2}{3} - \lambda_{\pm}\right) + x_2 \frac{1}{3}  \\\ x_1 \frac{1}{3} + x_2 \left(\frac{1}{3} - \lambda_{\pm}\right) \end{bmatrix} \\
\end{aligned}$$

and so the eigenvectors are given by $\ket{\pm} = \frac{1}{\sqrt{10 \pm 2\sqrt{5}}}\left( 1 \pm \sqrt{5} \ket{0} + 2 \ket{1}\right)$. It can be seen that state $B$ has the same reduced density matrix and therefore the same eigenvectors and eigenvalues. Therefore the Schmidt decomposition can be written as

$$\begin{aligned}
\ket{\psi} &= \sqrt{\lambda_+}\ket{+}\ket{+} + \sqrt{\lambda_-}\ket{-}\ket{-} 
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.80 {#exercise-280}

In this exercise we show some properties of unitary transformations on pure composite system states using the definition of a unitary operator from section 2.1.6, $U=\sum_{i} \ket{w_i}\bra{v_i}$, and the fact that $U\ket{\phi} = \sum_i \lambda_i (U\ket{i_A})\ket{i_B}$ if $U$ is a unitary operator acting on $A$ alone. 




From section 2.1.6 we know that a unitary operator can be defined as $U=\sum_{i} \ket{w_i}\bra{v_i}$ for any two orthonormal bases $\ket{v_i}$ and $\ket{w_i}$ for $A$ and $V=\sum_{i} \ket{y_i}\bra{x_i}$ for any two orthonormal bases $\ket{x_i}$ and $\ket{y_i}$ for $B$. From section 2.5 we know that $(U \otimes V)\ket{\phi} = \sum_i \lambda_i (U\ket{v_i}) (V \ket{x_i}) = \sum_i \lambda_i \ket{w_i}\ket{y_i}$ when $U$ is a unitary operator acting on system $A$ alone and $V$ is a unitary operator acting on system $B$ alone. 

Therefore if $\ket{\psi} = \sum_i \lambda_i \ket{w_i}\ket{y_i}$ and $\ket{\phi} = \sum_i \lambda_i \ket{v_i}\ket{x_i}$ for the same values of $\lambda_i$, then $\ket{\psi} = (U \otimes V) \ket{\phi}$ for some unitary operators $U$ and $V$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.81 {#exercise-281}

In this exercise we prove that there exists a unitary transformation $U_R$ acting on reference system $R$ such that $\ket{AR_1} = (I_A \otimes U_R)\ket{AR_2}$ for purification states $\ket{AR_1}$ and $\ket{AR_2}$ of state $\rho^A$ by using equation 2.207 and the results from the previous exercise. 




From equation 2.207 we know that purification states can be written as 

$$\begin{aligned}
\ket{AR_1} &= \sum_i \sqrt{p_i}\ket{i^A}\ket{i_1^R} \\
\ket{AR_2} &= \sum_i \sqrt{p_i}\ket{i^A}\ket{i_2^R} 
\end{aligned}$$

For some orthonormal bases $\ket{i_1^R}$ and $\ket{i_2^R}$ of $R$. Let $U_R = \sum_i \ket{i_2^R}\bra{i_1^R}$ be some unitary operator acting on system $R$, therefore

$$\begin{aligned}
(I_A \otimes U_R)\ket{AR_1} &= \sum_i \sqrt{p_i} (I_A \ket{i^A}) (U_R \ket{i_1^R}) \\
&= \sum_i \sqrt{p_i} \ket{i^A} \ket{i_2^R} \\
&= \ket{AR_2}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 2.82 {#exercise-282}

In this exercise we are just looking at more properties of purification. The first part we reproduce the steps in equation 2.207 - 2.211, but just switch out the labels for the states. For the second part we use the relationship between the reduced density matrices and Schmidt decomposition and equation 2.131. For the third part we use theorem 2.6.  




(1) We are given $\ket{AR} = \sum_i \sqrt{p_i} \ket{\psi_i}\ket{i}$

Now we calculate the reduced density operator for system $A$ corresponding to the state $\ket{AR}$

$$\begin{aligned}
tr_R (\ket{AR}\bra{AR}) &= \sum_{ij} \sqrt{p_ip_j} \ket{\psi_i}{\psi_j} tr(\ket{i}\bra{i}) \\
&= \sum_{ij} \sqrt{p_ip_j} \ket{\psi_i}\bra{\psi_j} \delta_{ij} \\
&= \sum_{i} p_i \ket{\psi_i}\bra{\psi_i} \\
&= \rho^A
\end{aligned}$$

Thus $\sum_i \sqrt{p_i} \ket{\psi_i}\ket{i}$ is a purification of $\rho^A$. 

(2) Since $\ket{AR} = \sum_i \sqrt{p_i} \ket{\psi_i}\ket{i}$ is written in the form of a Schmidt decomposition we know that the reduced density matrix for $R$ can be written as 

$$\begin{aligned}
\rho^R = \sum_i p_i \ket{i}\bra{i}\\
\end{aligned}$$

We can read directly from the density matrix that the probability of obtaining outcome $i$ is $p_i$. 

The state after the measurement $M_i = I \otimes \ket{i}\bra{i}$ is

$$\begin{aligned}
\frac{M_i\ket{\psi}}{\sqrt{p_i}} &= \frac{(I_A \otimes \ket{i}\bra{i})(\sum_{i'} \sqrt{p_{i'}} \ket{\psi_{i'}}\ket{i'})}{\sqrt{p_{i}}} \\
&= \frac{\sum_{i'} \sqrt{p_{i'}} \ket{\psi_{i'}}\ket{i}\braket{i \vert i'}}{\sqrt{p_{i}}} \\
&= \frac{ \sqrt{p_{i}} \ket{\psi_{i}}\ket{i}}{\sqrt{p_{i}}} \\
&= \ket{\psi_{i}}\ket{i}
\end{aligned}$$

So the corresponding state of system $A$ is $\ket{\psi_i}$

(3) An arbitrary ensemble and purification of $\rho$ can be written as $\ket{AR} = \sum_j \sqrt{q_j}\ket{\phi_j}\ket{j}$. By theorem 2.6 we know that $\sqrt{q_j}\ket{\phi_j} = \sum_i u_{ji} \sqrt{p_i}\ket{\psi_i}$ for some unitary $u_{ji}$ if both $\sqrt{p_i}\ket{\psi_i}$ and $\sqrt{q_j}\ket{\phi_j}$ generate the same density matrix. Therefore any purification of $\rho$ can be written as

$$\begin{aligned}
\ket{AR} &= \sum_j\sqrt{q_j}\ket{\phi_j}\ket{j} \\
&= \sum_j\sqrt{q_j}\ket{\phi_j}\ket{j} \\
&= \sum_j \left(\sum_i u_{ji} \sqrt{p_i}\ket{\psi_i} \right) \ket{j} \\
&= \sum_i \sqrt{p_i}\ket{\psi_i} \left(\sum_j u_{ji} \ket{j} \right) \\
&= \sum_i \sqrt{p_i}\ket{\psi_i} \ket{i} 
\end{aligned}$$

Where we define $\ket{i} = \sum_j u_{ji} \ket{j}$. Since $u_{ji}$ is unitary, it preserves the orthonormality of the vectors, therefore $\ket{i}$ is an orthonormal basis in which $R$ can be measured such that the corresponding post-measurement state for system $A$ is $\ket{\psi_i}$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



## Chapter Problems

### Problem 2.1 {#problem-21}

This problem is similar to [exercise 2.35](#exercise-235) but has us derive the equation for an arbitrary function of $\vec{n} \cdot \vec{\sigma}$ rather than an exponential. 




From exercise 2.35 we know that $\vec{n} \cdot \vec{\sigma}$ has eigengvalues $\lambda_{\pm} = \pm 1$ and so can be written as

$$\begin{aligned}
\vec{n} \cdot \vec{\sigma} = \ket{\lambda_+}\bra{\lambda_+} - \ket{\lambda_-}\bra{\lambda_-}
\end{aligned}$$

Therefore 

$$\begin{aligned}
f (\theta \vec{n} \cdot \vec{\sigma}) &= f(\theta) \ket{\lambda_+}\bra{\lambda_+} + f(-\theta) \ket{\lambda_-}\bra{\lambda_-} \\
&= \frac{1}{2}f(\theta)\left(\ket{\lambda_+}\bra{\lambda_+} + \ket{\lambda_-}\bra{\lambda_-} + \ket{\lambda_+}\bra{\lambda_+} -  \ket{\lambda_-}\bra{\lambda_-} \right) + \frac{1}{2}f(-\theta)\left( \ket{\lambda_-}\bra{\lambda_-} + \ket{\lambda_+}\bra{\lambda_+} + \ket{\lambda_-}\bra{\lambda_-} - \ket{\lambda_+}\bra{\lambda_+} \right) \\
&= \frac{1}{2}f(\theta)\left(I + \vec{n} \cdot \vec{\sigma} \right) + \frac{1}{2}f(-\theta)\left( I - \vec{n} \cdot \vec{\sigma} \right) \\
&= \frac{f(\theta) + f(-\theta)}{2}I + \frac{f(\theta) - f(-\theta)}{2} \vec{n} \cdot \vec{\sigma}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Problem 2.2 {#problem-22}

In this problem we explore some of the properties of the Schmidt number using what we learned in section 2.5. 




(1) Since $\ket{\psi}$ is a pure state from equation 2.202 we know that $\ket{\psi} = \sum_i \ket{i_A}\ket{i_B}$ for some orthonormal states $\ket{i_A}$ for system $A$ and $\ket{i_B}$ for system $B$. The reduced density matrices is then

$$\begin{aligned}
\rho^A = \sum_i \lambda_i^2 \ket{i_A}\bra{i_A}
\rho^B = \sum_i \lambda_i^2 \ket{i_B}\bra{i_B}
\end{aligned}$$

The Schmidt number is the number of non-zero $\lambda_i$ values in equation 2.202. The rank of the reduced density matrices is also the number of non-zero $\lambda_i$ values. Therefore the Schmidt number and the rank of the reduced density matrices are the same. 

(2) Starting with $\ket{\psi} = \sum_j \ket{\alpha_j}\ket{\beta_j}$, we first find the reduced density matrix for system $A$.

$$\begin{aligned}
\rho^A &= tr_B \left( \sum_{jj'} \ket{\alpha_j}\ket{\beta_j} \bra{\alpha_j'}\ket{\beta_j'} \right) \\
&= \sum_{jj'} \ket{\alpha_j}\bra{\alpha_j'}\braket{\beta_j\vert \beta_j'} \\
&= \sum_{jj'} \ket{\alpha_j}\bra{\alpha_j'}\delta_{jj'} \\
&= \sum_{j} \ket{\alpha_j}\bra{\alpha_j}
\end{aligned}$$

from here, we need to put the reduced density matrix in the form $\rho^A = \sum_i \lambda_i^2 \ket{i_A}\bra{i_A}$ by finding its eigenvalues and eigenvectors. If the ensemble of vectors $\ket{\alpha_j}$ are linearly independent, then the number of eigenvectors for $\rho^A$  would equal the number of terms in the decomposition. If they are not linearly independent, then there will be less eigenvectors than the number of terms in the decomposition. As shown in part 1, the Schmidt number is equal to the rank of the reduced density matrix and so the Schmidt number would be less than or equal to the number of terms in the decomposition. 

(3) Suppose that $\ket{\psi} = \alpha\ket{\phi} + \beta \ket{\gamma}$. I'm going to assume that $\ket{\phi}$ and $\ket{\gamma}$ are also pure states of the composite system of $A$ and $B$, therefore

$$\begin{aligned}
\ket{\psi} &= \alpha\ket{\phi} + \beta \ket{\gamma} \\
&= \alpha \left( \sum_i \lambda_i \ket{i_A}\ket{i_B} \right) + \beta \left( \sum_i \kappa_{i} \ket{i_A}\ket{i_B} \right) \\
&= \sum_i \left( \alpha \lambda_i + \beta\kappa_i \right)\ket{i_A}\ket{i_B} 
\end{aligned}$$

The Schmidt coefficients are given by $\alpha \lambda_i + \beta\kappa_i$ which can now be zero when $\lambda_i = \kappa_i =0$ or when $\alpha \lambda_i = -\beta\kappa_i$. If $\alpha \lambda_i = -\beta\kappa_i$ for all states shared by $\ket{\phi}$ and $\ket{\gamma}$ then the Schmidt number is $\vert \text{Sch} (\phi) - \text{Sch} (\gamma) \vert$. Therefore $\text{Sch} (\psi) \geq \vert \text{Sch} (\phi) - \text{Sch} (\gamma) \vert$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Problem 2.3 {#problem-23}

For this problem we derive Tsirelson's inequality. To do this we'll use equation 2.78, equation 2.107, equation 2.115 and the definition of the commutator. 




Let's find what $Q^2$ equals

$$\begin{aligned}
Q^2 &= (\vec{q} \cdot \vec{\sigma})^2 \\
&= (q_1 \sigma_1 + q_2 \sigma_2 + q_3 \sigma_3)^2 \\
&= q_1^2 \sigma_1^2 + q_1q_2 \sigma_1\sigma_2 + q_1q_3 \sigma_1\sigma_3 + q_2q_1 \sigma_2\sigma_1 +  q_2^2 \sigma_2^2 + + q_2q_3 \sigma_2\sigma_3 + q_3q_1\sigma_3\sigma_1 + q_3q_2\sigma_3\sigma_2 + q_3^2 \sigma_3^2 \\
&= q_1^2 I + q_1q_2 i\sigma_3 - q_1q_3 i\sigma_2 - q_2q_1 i\sigma_3 +  q_2^2 I + + q_2q_3 i\sigma_1 + q_3q_1 i \sigma_2 - q_3q_2 i \sigma_1 + q_3^2 I & \text{per equation 2.78} \\
&= (q_1^2 + q_2^2 + q_3^2)I \\
&= I
\end{aligned}$$

Therefore $Q^2 = R^2 = S^2 = T^2 = I$. Now let's look at equation 2.233

$$\begin{aligned}
(Q \otimes S + R \otimes S + R \otimes T - Q \otimes T)^2 &= (Q \otimes (S - T) + R \otimes (S + T))^2 \\
&= Q^2 \otimes (S-T)^2 + QR\otimes (S - T)(S + T) + RQ \otimes (S + T)(S - T) + R^2 \otimes (S+T)^2 \\
&= I \otimes (S^2 - ST - TS + T^2) + QR\otimes (S - T)(S + T) + RQ \otimes (S + T)(S - T)+ I \otimes (S^2 + ST + TS + T^2) \\
&= I \otimes (I - ST - TS + I) + QR\otimes (S^2 + ST - TS - T^2) + RQ \otimes (S^2 - ST + TS - T^2)+ I \otimes (I + ST + TS + I) \\
&= I \otimes (4 I) + QR\otimes (I + ST - TS - I) + RQ \otimes (I - ST + TS - I)\\
&= I \otimes (4 I) + QR\otimes (ST - TS) - RQ \otimes (ST - TS)\\
&= 4I \otimes I + (QR - RQ) \otimes (ST - TS) \\
&= 4I \otimes I + \lbrack Q,R \rbrack \otimes \lbrack S,T \rbrack 
\end{aligned}$$

Then let's use those results to prove equation 2.234

$$\begin{aligned}
\braket{ (Q \otimes S + R \otimes S + R \otimes T - Q \otimes T)^2 } &= \braket{ 4I \otimes I + \lbrack Q,R \rbrack \otimes \lbrack S,T \rbrack } \\
&= \braket{4I \otimes I} + \braket{\lbrack Q,R \rbrack \otimes \lbrack S,T \rbrack} \\
&= \braket{4I \otimes I} + \braket{\lbrack Q,R \rbrack}_1 \braket{\lbrack S,T \rbrack}_2 \\
& \leq 4 + \sqrt{4\braket{Q^2}_1\braket{R^2}_1} \sqrt{4\braket{S^2}_2\braket{T^2}_2} & \text{per equation 2.107}\\
4 + \sqrt{4\braket{Q^2}_1\braket{R^2}_1} \sqrt{4\braket{S^2}_2\braket{T^2}_2} &= 4 + \sqrt{4\braket{I}_1\braket{I}_1} \sqrt{4\braket{I}_2\braket{I}_2} \\
& = 4 + \sqrt{4} \sqrt{4} \\
&= 8
\end{aligned}$$

So now we know that $\braket{ (Q \otimes S + R \otimes S + R \otimes T - Q \otimes T)^2 } \leq 8$ and from equation 2.115 we know that $\braket{M^2} = \braket{M}^2 + \lbrack \Delta (M) \rbrack^2$, therefore $\braket{M^2} \geq \braket{M}^2$. Putting it together we get

$$\begin{aligned}
8 \geq \braket{ (Q \otimes S + R \otimes S + R \otimes T - Q \otimes T)^2 } \geq \braket{ Q \otimes S + R \otimes S + R \otimes T - Q \otimes T }^2
\end{aligned}$$

Taking the square root we get

$$\begin{aligned}
2\sqrt{2} \geq \braket{ Q \otimes S + R \otimes S + R \otimes T - Q \otimes T } = \braket{ Q \otimes S } + \braket{ R \otimes S} + \braket{R \otimes T} - \braket{Q \otimes T }
\end{aligned}$$

which is equation 2.234.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


