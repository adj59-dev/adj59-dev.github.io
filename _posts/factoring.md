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

Before constructing the circuit we need to determin how many qubits and classical bits will be needed to implement the calculation. 

## Constructing Circuit with Qiskit



## Implementing Circuit on IBM Quantum Computer


