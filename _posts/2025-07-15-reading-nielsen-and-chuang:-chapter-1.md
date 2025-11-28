---
title: "Reading Nielsen and Chuang: Chapter 1"
description: "Notes and exercise solutions for QCQI Chapter 1: introduction and overview."
categories:
  - Quantum Computation and Quantum Information
tags:
  - QCQI
  - quantum computing
  - Quantum Computation and Quantum Information
  - Nielsen & Chuang
  - chapter 1
  - exercise
  - problem
  - solutions
---

## Reading Nielsen and Chuang: Chapter 1

I recently started reading *Quantum Computation and Quantum Information* by Nielsen and Chuang. I don’t always read the introductory chapters of textbooks—often it is mostly material that is covered later in more detail—but with some unexpected free time, I decided to give this one a read.

The authors aim to provide a broad overview of the field for readers with little prior experience. One important caveat: the book was originally published in 2000, and quantum computing has evolved significantly since then. Still, this chapter does a good job previewing concepts that appear in more depth later in the book, which helps show how information from different parts of the book connects.

That said, if you’re not comfortable with Dirac notation, it might be a good idea to read section 2.1 (on linear algebra) first and then circle back.

There are two exercises and two problems in this chapter. It is suggested to wait until finishing the book before completing problems, and so I plan to take that advice. The exercises, however, I’ve worked through – and I’ll share my solutions below. 

When working through textbook problems on my own, outside of a class setting, I like to check my work against other people's solutions that I find online. I didn't see anyone solve these exercises exactly in the same way that I did, though similar reasoning was used. So, after attempting them on your own, I encourage anyone reading this to reference multiple sources to see how different people approached these exercises. 

### Exercise 1.1

In section 1.4.4 the authors describe the Deutsch-Jozsa algorithm and demonstrate how it can be used to solve Deutsch's problem in a single evaluation. In contrast a classical algorithm would require $2^n/2+1$ evaluations to solve the problem *with certainty*.  For this exercise the authors ask the reader instead to determine how many evaluations would be needed to solve the problem with some probability of error $\epsilon<1/2$.

For Deutsch's problem we are given some function $f(x)$ for $x$ ranging from $0$ to $2^n-1$. The output of $f(x)$ is always $0$ or $1$ and the function itself is either constant or produces an even balance of $0$ and $1$. The goal is to determine whether the function is constant or balanced with as few evaluations as possible. 

Several pieces of information are unknown in this problem (at least for how it is presented in the book) that could impact the results. Specifically, we do not know if there is an equal probability of $f(x)$ being constant or balanced, so for this solution I will define $P(C)$ to be the probability that $f(x)$ is constant and $P(B)$ to be the probability that $f(x)$ is balanced, with $P(C)+P(B)=1$. It is also not specified if the guesser knows what these probabilities are; though, I will assume that the person guessing does not have any prior knowledge of $P(C)$ and $P(B)$. 

The best classical algorithm for this problem could be dependent on this unknown information, but with the considerations above, a guessing algorithm will be executed as follows:
if all results are the same value guess that $f(x)$ is constant, 
else guess that $f(x)$ is balanced.

After one evaluation, regardless of the result, the guesser will guess that $f(x)$ is constant. The probability of error can then be calculated as $\epsilon=P(B)$. It is not guaranteed that $P(B)<1/2$ and so more than one evaluation is needed. 

After two evaluations the probability of error is given by the probability of both results being equal and $f(x)$ being balanced. This is because if both results are equal, the guesser will guess that $f(x)$ is constant, which is incorrect. For all other scenarios the guesser will guess correctly. The probability of error is now

$$\begin{aligned} \epsilon &= P(f(x_1)=f(x_2) \cap B) \\
&= P(f(x_1) = f(x_2)|B)P(B) \\
&= \frac{2^n/2-1}{2^n-1} P(B) \end{aligned}$$

We know that $P(B) \leq 1$. It can be shown that $(2^n/2-1)/(2^n-1) < 1/2$ for all n. Therefore $\epsilon < 1/2$ for all n with only two evaluations. 

### Exercise 1.2
In section 1.6.1 the authors introduce the idea of quantum distinguishability and say that it is not possible to reliably distinguish between non-orthogonal quantum states. In this exercise they ask the reader to explain how a device which, upon input of one of two non-orthogonal states correctly identifies the state, could be used to build a device which cloned the state, in violation of the no-cloning theorem. They then ask how a cloning device could be used to distinguish non-orthogonal quantum states. 

Let's say there is a device that is able to act upon two non-orthogonal quantum states $\ket{\psi}$ and $\ket{\phi}$ using some operator A and produce one of two states $\ket{\Psi}$ and $\ket{\Phi}$ which are easily distinguishable upon measurement (i.e. orthogonal) such that 

$$\begin{aligned}
A\ket{\psi} &= \ket{\Psi} \\
A\ket{\phi} &= \ket{\Phi}
\end{aligned}$$

Taking the inner product of these two equations we get $\bra{\phi}A^\dagger A\ket{\psi} = \braket{\Phi\vert\Psi}$.

Since $\ket{\Phi}$ and $\ket{\Psi}$ are orthogonal $\braket{\Phi\vert\Psi} = 0$, which means $\bra{\phi}A^\dagger A\ket{\psi} = 0$. If A is unitary $A^\dagger A = I$ and so $\braket{\phi\vert\psi} = 0$, which can only be true if $\ket{\phi}$ and $\ket{\psi}$ are orthogonal. Since $\ket{\phi}$ and $\ket{\psi}$ are not orthogonal, this means that we have created a device that acts upon our quantum states with a non-unitary operator. 

We can recall that in the no-cloning theorem (which we were told to skip ahead and read in section 1.3.5) the proof depended on the operator being unitary which caused the inner product of 12.3 and 12.4 to be reduced to 12.5. If we were allowed to use a non-unitary operator, such as A, this proof would no longer hold. 

If a cloning device was created, it could produce enough clones of a quantum state such that, by measuring the clones, one could build up a statistical representation of the state thus allowing them to distinguish the state from other non-orthogonal quantum states. 
