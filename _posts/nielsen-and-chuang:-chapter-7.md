---
title: "Nielsen and Chuang: Chapter 7"
description: "Notes and exercise solutions for QCQI Chapter 7: the physical realization of quantum computers, conditions for quantum computation, harmonic oscillator QCs, optical photon QCs, optical cavity QED, ion traps, NMR, other implementation schemes."
categories:
  - Quantum Computation and Quantum Information
permalink: /qcqi/chapter-7/
toc: true
tags:
  - QCQI
  - quantum computing
  - Quantum Computation and Quantum Information
  - Nielsen & Chuang
  - chapter 7
  - exercise
  - problem
  - solutions
last_modified_at: 2025-12-17 16:10:00 -08:00
exercises:
  - anchor: exercise-71
    label: Exercise 7.1
  - anchor: exercise-72
    label: Exercise 7.2
  - anchor: exercise-73
    label: Exercise 7.3
  - anchor: exercise-74
    label: Exercise 7.4
  - anchor: exercise-75
    label: Exercise 7.5
  - anchor: exercise-76
    label: Exercise 7.6
  - anchor: exercise-77
    label: Exercise 7.7
  - anchor: exercise-78
    label: Exercise 7.8
  - anchor: exercise-79
    label: Exercise 7.9
  - anchor: exercise-710
    label: Exercise 7.10
  - anchor: exercise-711
    label: Exercise 7.11
  - anchor: exercise-712
    label: Exercise 7.12
  - anchor: exercise-713
    label: Exercise 7.13
  - anchor: exercise-714
    label: Exercise 7.14
  - anchor: exercise-715
    label: Exercise 7.15
  - anchor: exercise-716
    label: Exercise 7.16
  - anchor: exercise-717
    label: Exercise 7.17
  - anchor: exercise-718
    label: Exercise 7.18
  - anchor: exercise-719
    label: Exercise 7.19
  - anchor: exercise-720
    label: Exercise 7.20
  - anchor: exercise-721
    label: Exercise 7.21
  - anchor: exercise-722
    label: Exercise 7.22
  - anchor: exercise-723
    label: Exercise 7.23
  - anchor: exercise-724
    label: Exercise 7.24
  - anchor: exercise-725
    label: Exercise 7.25
  - anchor: exercise-726
    label: Exercise 7.26
  - anchor: exercise-727
    label: Exercise 7.27
  - anchor: exercise-728
    label: Exercise 7.28
  - anchor: exercise-729
    label: Exercise 7.29
  - anchor: exercise-730
    label: Exercise 7.30
  - anchor: exercise-731
    label: Exercise 7.31
  - anchor: exercise-732
    label: Exercise 7.32
  - anchor: exercise-733
    label: Exercise 7.33
  - anchor: exercise-734
    label: Exercise 7.34
  - anchor: exercise-735
    label: Exercise 7.35
  - anchor: exercise-736
    label: Exercise 7.36
  - anchor: exercise-737
    label: Exercise 7.37
  - anchor: exercise-738
    label: Exercise 7.38
  - anchor: exercise-739
    label: Exercise 7.39
  - anchor: exercise-740
    label: Exercise 7.40
  - anchor: exercise-741
    label: Exercise 7.41
  - anchor: exercise-742
    label: Exercise 7.42
  - anchor: exercise-743
    label: Exercise 7.43
  - anchor: exercise-744
    label: Exercise 7.44
  - anchor: exercise-745
    label: Exercise 7.45
  - anchor: exercise-746
    label: Exercise 7.46
  - anchor: exercise-747
    label: Exercise 7.47
  - anchor: exercise-748
    label: Exercise 7.48
  - anchor: exercise-749
    label: Exercise 7.49
  - anchor: exercise-750
    label: Exercise 7.50
  - anchor: exercise-751
    label: Exercise 7.51
  - anchor: exercise-752
    label: Exercise 7.52
  - anchor: problem-71
    label: Problem 7.1
  - anchor: problem-72
    label: Problem 7.2
  - anchor: problem-73
    label: Problem 7.3
  - anchor: problem-74
    label: Problem 7.4
chapter: 7
---

<a id="top"></a>

I just finished reading Chapter 7 of *Quantum Computation and Quantum Information* by Nielsen and Chuang.



## Harmonic oscillator quantum computer

### Exercise 7.1 {#exercise-71}

Using equation 7.6 and 7.7

$$\begin{aligned}
a^\dagger a &= \frac{1}{2m\hbar\omega}\left(m\omega x - ip\right)\left(m\omega x+ip\right)\\
&= \frac{1}{2m\hbar\omega}\left(m^2\omega^2x^2 + im\omega xp - im\omega px + p^2\right)\\
&= \frac{1}{2m\hbar\omega}\left(m^2\omega^2x^2 + im\omega( xp - px) + p^2\right)\\
&= \frac{1}{2m\hbar\omega}\left(m^2\omega ^2x^2 + im\omega\lbrack x,p \rbrack + p^2\right)\\
&= \frac{1}{2m\hbar\omega}\left(m^2\omega^2x^2 - m\omega\hbar + p^2\right)\\
&= \frac{m\omega^2 x^2}{2\hbar\omega} - \frac{1}{2} + \frac{p^2}{2m\hbar\omega}\\
&= \left(\frac{m\omega^2 x^2}{2} + \frac{p^2}{2m}\right)\frac{1}{\hbar\omega} - \frac{1}{2} \\
&= \frac{H}{\hbar\omega} - \frac{1}{2} & \text{equation 7.4}\\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



I just finished reading Chapter 6 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. 
