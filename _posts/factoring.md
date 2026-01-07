---
title: "Factoring Using a Quantum Computer"
description: "Notes on implementing Shor's algorithm."
categories:
  - Qiskit
permalink: /qiskit/factoring
toc: true
tags:
  - quantum computing
  - Qiskit
  - factoring
  - order finding
  - quantum Fourier transform
last_modified_at: 2025-12-26 12:00:00 -08:00
---

This post documents my use of Shor's algorithm for factoring. 

## Algorithm Overview

This section gives an overview of the algorithm used for factoring using a quantum computer. 

### Classical Pre-Processing

1. If $N$ is even, return the factor $2$.
2. Determine whether $N=a^b$ for integers $a\geq 1$ and $b\geq 2$, and if so return the factor $a$
3. Randomly choose $x$ in the range $1$ to $N-1$. If $\text{gcd}(x,N)>1$ then return the factor $\text{gcd}(x,N)$.

### Quantum Order Finding

The phase estimation algorithm applied to the unitary operator $U_{x,N}\ket{y} \equiv \ket{xy \mod N}$ with $y\in \lbrace 0,1\rbrace^L$  

4. initial state $\ket{0}\ket{1}$ 
5. create superposition $\rightarrow \frac{1}{\sqrt{2^t}} \sum_{j=0}^{2^t-1}\ket{j}\ket{1}$
6. apply $U_{x,N}$, $\rightarrow \frac{1}{\sqrt{2^t}} \sum_{j=0}^{2^t-1}\ket{j}\ket{x^{j}\mod N}\approx \frac{1}{\sqrt{r2^t}}\sum_{x=0}^{r-1}\sum_{j=0}^{2^t-1} e^{2\pi isj/r}\ket{j}\ket{u_s}$
7. apply inverse Fourier transform to the first register $\rightarrow \frac{1}{\sqrt{r}}\sum_{s=0}^{r-1}\ket{\widetilde{s/r}}\ket{u_x}$
8. measure first register $\rightarrow \widetilde{s/r}$

### Classical Post-Processing

9. apply continued fractions algorithm $\rightarrow r$
10. If $r$ is even and $x^{r/2}\neq -1 \mod N$ then compute $\text{gcd}(x^{r/2}-1, N)$ and $\text{gcd}(x^{r/2}+1, N)$, and test to see if one of these is a non-trival factor, returning that factor if so. 

## Required Resources

Before constructing the circuit we need to determin how many qubits and classical bits will be needed to implement the quantum order finding portion of the calculation. From section 5.3.1 in N&C's QCQI we know that we need

$$\begin{aligned}
t=2L + 1 +\left\lceil \log\left(2+\frac{1}{2\epsilon}\right)\right\rceil
\end{aligned}$$

qubits for register 1 and $L$ qubits in register 2 where $L=\lceil\log N\rceil$. [Experimental realization of Shor’s quantum factoring algorithm
using nuclear magnetic resonance](https://arxiv.org/pdf/quant-ph/0112176) was able to reduce the number of qubits needed to 7 when factoring 15, but they did so with prior knowledge of the solution. For now, let's not use any prior knowledge and say we want to factor up to the value 32 and so the register 1 needs 15 qubits and register 2 needs 5 qubits.  

## Constructing Circuit with Qiskit



## Implementing Circuit on IBM Quantum Computer


