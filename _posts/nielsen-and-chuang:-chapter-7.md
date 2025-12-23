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

I just finished reading Chapter 7 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. Section 7.4 bookkeeping can be challenging keeping track of the statespace of logical qubits and optical modes.  

<details><summary>Click to expand details</summary>

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



### Exercise 7.2 {#exercise-72}

$$\begin{aligned}
\lbrack a,a^\dagger \rbrack &= aa^\dagger - a^\dagger a \\
&= \left(\frac{H}{\hbar\omega} + \frac{1}{2}\right)  - \left( \frac{H}{\hbar\omega} - \frac{1}{2} \right) & \text{from exercise 7.1}\\
&= 1
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


### Exercise 7.3 {#exercise-73}

$$\begin{aligned}
\lbrack H,a \rbrack &= Ha - aH \\
&= \hbar\omega\left(\left(a^\dagger a + \frac{1}{2}\right)a - a\left(a^\dagger a + \frac{1}{2}\right)\right)\\
&= \hbar\omega\left(\left(a^\dagger a + \frac{1}{2}\right) - \left(aa^\dagger  + \frac{1}{2}\right)\right)a\\
&= \hbar\omega\left(a^\dagger a  - aa^\dagger \right)a\\
&= -\hbar\omega\lbrack a, a^\dagger\rbrack a\\
&= -\hbar\omega a\\
\end{aligned}$$

By the time independent Schrodinger equation 

$$\begin{aligned}
H\ket{\psi} = E\ket{\psi}
\end{aligned}$$

and so

$$\begin{aligned}
-\hbar\omega a\ket{\psi} &= \left(Ha - aH\right)\ket{\psi} \\
&= Ha\ket{\psi} - aH\ket{\psi}\\
&= Ha\ket{\psi} - Ea\ket{\psi}\\
Ha\ket{\psi} &= \left(E-\hbar\omega\right) a\ket{\psi}\\
\end{aligned}$$

This is the same form as the time independent Schrodinger equation, so we know that either $a\ket{\psi}$ is an eigenstate with energy $E-\hbar\omega$ or $a\ket{\psi}=0$. By applying the same identity repeatedly we get that $a^n\ket{\psi}$ is an eigenstate with energy $E-n\hbar\omega$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


### Exercise 7.4 {#exercise-74}

$$\begin{aligned}
\frac{\left(a^\dagger\right)^n}{\sqrt{n!}}\ket{0} &= \frac{\left(a^\dagger\right)^{n-1}}{\sqrt{n!}}\sqrt{1}\ket{1} &\text{equation 7.11}\\
&= \frac{\left(a^\dagger\right)^{n-2}}{\sqrt{n!}}\sqrt{2}\ket{2} \\
& \vdots \\
&= \frac{a^\dagger}{\sqrt{n!}}\sqrt{(n-1)!}\ket{n-1} \\
&= \frac{1}{\sqrt{n!}}\sqrt{(n-1)!}\sqrt{n}\ket{n} \\
&= \frac{1}{\sqrt{n!}}\sqrt{n!}\ket{n} \\
&= \ket{n} \\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


### Exercise 7.5 {#exercise-75}

$$\begin{aligned}
a^\dagger a \ket{n} &= a^\dagger \sqrt{n}\ket{n-1} & \text{equation 7.12}\\
&= \sqrt{n} a^\dagger\ket{n-1} \\
&= \sqrt{n} \sqrt{n-1+1}\ket{n-1+1} & \text{equation 7.11}\\
&= n\ket{n}
\end{aligned}$$

Therefore, equation 7.11 and 7.12 are consistent with 7.10. 

For the normalization condition

$$\begin{aligned}
\braket{n\vert n} &= \braket{0\vert \frac{(a)^n}{\sqrt{n!}} \frac{(a^\dagger )^n}{\sqrt{n!}} \vert 0} \\
&= \braket{0\vert \frac{(a)^n}{\sqrt{n!}} \vert n} \\
&= \braket{0 \vert 0} \\
&= 1
\end{aligned}$$

Therefore, if the ground state is normalized (which it should be) then all $\ket{n}$ are also normalized. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


## Optical photon quantum computer

### Exercise 7.6 {#exercise-76}

$$\begin{aligned}
a\ket{\alpha} &= a\left(e^{ -\vert\alpha\vert^2/2 }\sum_{n=0}^{\infty} \frac{\alpha^n}{\sqrt{n!}}\ket{n}\right) \\
&= e^{ -\vert\alpha\vert^2/2 }\sum_{n=0}^{\infty} \frac{\alpha^n}{\sqrt{n!}}a\ket{n} \\
&= e^{ -\vert\alpha\vert^2/2 }\sum_{n=1}^{\infty} \frac{\alpha^n}{\sqrt{n!}}\sqrt{n}\ket{n-1}  & \text{sum starts at $n=1$ since $a\ket{0}=0$}  \\
&= e^{ -\vert\alpha\vert^2/2 }\sum_{n=1}^{\infty} \frac{\alpha\alpha^{n-1}}{\sqrt{(n-1)!}}\ket{n-1} \\
&= \alpha e^{ -\vert\alpha\vert^2/2 }\sum_{m=0}^{\infty} \frac{\alpha^{m}}{\sqrt{m!}}\ket{m} & \text{where $m=n-1$}\\
&= \alpha\ket{\alpha}
\end{aligned}$$


| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

### Exercise 7.7 {#exercise-77}

Let's first represent this circuit in the full photon population basis $\lbrace \ket{00},\ket{01},\ket{10},\ket{11}\rbrace$,

$$\begin{aligned}
I \otimes \pi &= \begin{bmatrix} 1 & 0 \\\ 0 & 1 \end{bmatrix} \otimes \begin{bmatrix} 1 & 0 \\\ 0 & e^{i\pi} \end{bmatrix} \\
&= \begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & e^{i\pi} & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & e^{i\pi} \end{bmatrix} \\
\end{aligned}$$

The dual-rail subspace only spans these basis states $\ket{0}_L=\ket{01}$ and $\ket{1}_L=\ket{10}$ and so we can represent the circuit with a reduced matrix consisting of only the entries for those states

$$\begin{aligned}
\begin{bmatrix} 1 & 0 & 0 & 0 \\\ 0 & e^{i\pi} & 0 & 0 \\\ 0 & 0 & 1 & 0 \\\ 0 & 0 & 0 & e^{i\pi} \end{bmatrix} \rightarrow \begin{bmatrix} e^{i\pi} & 0 \\\ 0 & 1 \end{bmatrix}\\
\end{aligned}$$

This matches equation 7.23. 


| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


### Exercise 7.8 {#exercise-78}

So, we know that 

$$\begin{aligned}
P &= \exp(-iH\Delta/\hbar)\\
&= \exp(-i\Delta \omega a^\dagger a) & \text{equation 7.20}\\
\end{aligned}$$

and that

$$\begin{aligned}
P\ket{n} &= \exp(-i\Delta\omega a^\dagger a) \ket{n}\\
&= \sum_{m=0}^{\infty} \exp(-i\Delta\omega m)\ket{m}\braket{m \vert n} \\
&= \exp(-i\Delta\omega n)\ket{n}
\end{aligned}$$

The book states that $P\ket{1} = e^{i\Delta}\ket{1}$, so it looks like they are using the convention where the negative sign and $\omega$ is aborbed by the $\Delta$, so $-\Delta \omega \rightarrow \Delta$. Therefore,

$$\begin{aligned}
P\ket{\alpha} &=  P \left(e^{-\vert\alpha\vert^2/2}\sum_{n=0}^{\infty}\frac{\alpha^n}{\sqrt{n!}}\ket{n}\right)\\
&= e^{-\vert\alpha\vert^2/2}\sum_{n=0}^{\infty}\frac{\alpha^n}{\sqrt{n!}}P\ket{n} \\
&= e^{-\vert\alpha\vert^2/2}\sum_{n=0}^{\infty}\frac{\alpha^n}{\sqrt{n!}}e^{i\Delta n}\ket{n} \\
&= e^{-\vert\alpha\vert^2/2}\sum_{n=0}^{\infty}\frac{\left(\alpha e^{i\Delta}\right)^n}{\sqrt{n!}}\ket{n} \\
&= e^{-\vert\alpha e^{i\Delta}\vert^2/2}\sum_{n=0}^{\infty}\frac{\left(\alpha e^{i\Delta}\right)^n}{\sqrt{n!}}\ket{n} & \text{absolute value not changed by phase}\\
&= \ket{\alpha e^{i\Delta}}
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


### Exercise 7.9 {#exercise-79}

One thing to note: the beamsplitter shown is for $B^\dagger$ not $B$. Figure 7.3 shows you how to tell which is which, but also inverts the wires relative to what we are asked to use in exercise 7.7 and (I think) here. 

$$\begin{aligned}
PB^\dagger &= \begin{bmatrix} e^{i\pi} & 0 \\\ 0 & 1 \end{bmatrix}\begin{bmatrix} \cos\theta & \sin\theta \\\ -\sin\theta & \cos\theta \end{bmatrix} & \text{equation 7.35 and exercise 7.7} \\
&= \begin{bmatrix} e^{i\pi}\cos\theta & e^{i\pi}\sin\theta \\\ -\sin\theta & \cos\theta \end{bmatrix} \\ 
&= \frac{1}{\sqrt{2}}\begin{bmatrix} -1 & -1 \\\ -1 & 1 \end{bmatrix} \\ 
&= -\frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 1 \\\ 1 & -1 \end{bmatrix} \\ 
&= -H\\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


### Exercise 7.10 {#exercise-710}

(1)

$$\begin{aligned}
BB^\dagger &= \begin{bmatrix} \cos\theta & -\sin\theta \\\ \sin\theta & \cos\theta \end{bmatrix}\begin{bmatrix} \cos\theta & \sin\theta \\\ -\sin\theta & \cos\theta \end{bmatrix} \\
&= \begin{bmatrix} \cos^2\theta + \sin^2\theta & \cos\theta\sin\theta - \sin\theta\cos\theta  \\\ \sin\theta\cos\theta - \cos\theta\sin\theta & \sin^2\theta + \cos^2\theta \end{bmatrix}\\
&= \begin{bmatrix} 1 & 0  \\\ 0 & 1 \end{bmatrix}\\
&= I
\end{aligned}$$

(2)

$$\begin{aligned}
BP_bB^\dagger &= \begin{bmatrix} \cos\theta & -\sin\theta \\\ \sin\theta & \cos\theta \end{bmatrix}\begin{bmatrix} 1 & 0 \\\ 0 & e^{i\varphi} \end{bmatrix}\begin{bmatrix} \cos\theta & \sin\theta \\\ -\sin\theta & \cos\theta \end{bmatrix} \\
&= \begin{bmatrix} \cos\theta & -e^{i\varphi}\sin\theta \\\ \sin\theta & e^{i\varphi}\cos\theta \end{bmatrix}\begin{bmatrix} \cos\theta & \sin\theta \\\ -\sin\theta & \cos\theta \end{bmatrix} \\
&= \begin{bmatrix} \cos^2\theta + e^{i\varphi}\sin^2\theta & \cos\theta\sin\theta-e^{i\varphi}\sin\theta\cos\theta \\\ \sin\theta\cos\theta -e^{i\varphi}\cos\theta\sin\theta & \sin^2\theta + e^{i\varphi}\cos^2\theta \end{bmatrix} \\
&= \begin{bmatrix} \cos^2\theta + e^{i\varphi}\sin^2\theta & \left(1-e^{i\varphi}\right)\sin\theta\cos\theta \\\ \left(1-e^{i\varphi}\right) \cos\theta\sin\theta & \sin^2\theta + e^{i\varphi}\cos^2\theta \end{bmatrix} \\
&= \frac{1}{2}\begin{bmatrix} 1 + e^{i\varphi} & 1-e^{i\varphi} \\\ 1-e^{i\varphi} & 1 + e^{i\varphi} \end{bmatrix} & \text{assume 50:50 beamsplitters} \\
&= e^{i\varphi/2}\begin{bmatrix} \frac{e^{-i\varphi/2} + e^{i\varphi/2}}{2} & \frac{e^{-i\varphi/2} - e^{i\varphi/2}}{2} \\\  \frac{e^{-i\varphi/2} - e^{i\varphi/2}}{2} &  \frac{e^{-i\varphi/2} + e^{i\varphi/2}}{2} \end{bmatrix} \\
&= e^{i\varphi/2}\begin{bmatrix} \cos\frac{\varphi}{2} & -i\sin\frac{\varphi}{2} \\\  -i\sin\frac{\varphi}{2} &  \cos\frac{\varphi}{2} \end{bmatrix} \\
&= e^{i\varphi/2}R_x(\varphi)
\end{aligned}$$


| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


### Exercise 7.11 {#exercise-711}

I'm following a similar analysis to what is shown on page 292. Here they have the states written like $\ket{n_b,n_a}$, where $n_b$ is the number of photons on the $b$ rail and $n_a$ is the number of photons on the $a$ rail. 

$$\begin{aligned}
B\ket{2,0} &= \frac{1}{\sqrt{2}} Bb^\dagger \ket{1,0} \\
&= \frac{1}{\sqrt{2}} Bb^\dagger B^\dagger B\ket{1,0} \\
&= \frac{1}{\sqrt{2}} Bb^\dagger B^\dagger B b^\dagger\ket{0,0} \\
&= \frac{1}{\sqrt{2}} Bb^\dagger B^\dagger B b^\dagger B^\dagger B\ket{0,0} \\
&= \frac{1}{\sqrt{2}} \left(Bb^\dagger B^\dagger\right)\left( B b^\dagger B^\dagger \right) \ket{0,0} & \text{since $B\ket{0,0}=\ket{0,0}$}\\
&=  \frac{1}{\sqrt{2}} \left(-a^\dagger\sin\theta + b^\dagger\cos\theta\right)\left( -a^\dagger\sin\theta + b^\dagger\cos\theta \right) \ket{0,0} \\
&=  \frac{1}{\sqrt{2}} \left(a^\dagger a^\dagger\sin^2\theta - (b^\dagger a^\dagger + a^\dagger b^\dagger)\cos\theta\sin\theta + b^\dagger b^\dagger\cos^2\theta \right) \ket{0,0} \\
&=  \frac{1}{\sqrt{2}} \left(\sqrt{2}\sin^2\theta\ket{0,2} - 2\cos\theta\sin\theta\ket{1,1} + \sqrt{2}\cos^2\theta \ket{2,0}\right) \\
&=  \frac{1}{2}\ket{0,2} - \frac{1}{\sqrt{2}}\ket{1,1} + \frac{1}{2}\ket{2,0} & \text{since $\theta = \frac{\pi}{4}$}\\
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


### Exercise 7.12 {#exercise-712}

$$\begin{aligned}
B\ket{\alpha}\ket{\beta} &= B \left(e^{-\vert\alpha\vert^2/2}\sum_{n=0}^{\infty}\frac{\alpha^n}{\sqrt{n!}}\ket{n}\right)\left(e^{-\vert\beta\vert^2/2}\sum_{m=0}^{\infty}\frac{\beta^m}{\sqrt{m!}}\ket{m}\right) \\
&= e^{-\vert\alpha\vert^2/2}e^{-\vert\beta\vert^2/2}\sum_{n=0}^{\infty}\sum_{m=0}^{\infty}\frac{\alpha^n}{\sqrt{n!}}\frac{\beta^m}{\sqrt{m!}}B\ket{n}\ket{m} \\
&= e^{-\vert\alpha\vert^2/2}e^{-\vert\beta\vert^2/2}\sum_{n=0}^{\infty}\sum_{m=0}^{\infty}\frac{\alpha^n}{n!}\frac{\beta^m}{m!}(Ba^\dagger B^\dagger)^n(Bb^\dagger B^\dagger)^m\ket{0}\ket{0} \\
&= e^{-\vert\alpha\vert^2/2}e^{-\vert\beta\vert^2/2}\sum_{n=0}^{\infty}\sum_{m=0}^{\infty}\frac{(\alpha Ba^\dagger B^\dagger)^n}{n!}\frac{(\beta Bb^\dagger B^\dagger)^m}{m!}\ket{0}\ket{0} \\
&= e^{-\vert\alpha\vert^2/2}e^{-\vert\beta\vert^2/2}\sum_{n=0}^{\infty}\sum_{m=0}^{\infty}\frac{(\alpha\cos\theta a^\dagger + \alpha\sin\theta b^\dagger)^n}{n!}\frac{(\beta\cos\theta b^\dagger - \beta\sin\theta a^\dagger)^m}{m!}\ket{0}\ket{0} \\
&= \ket{\alpha\cos\theta - \beta\sin\theta}\ket{\alpha\sin\theta + \beta\cos\theta}
\end{aligned}$$

I feel like there have been some inconsistencies with wire labeling in this section of the book, so for the purpose of clarity for this exercise I am defining the behavior of the beamsplitter like this

$$\begin{aligned}
Ba^\dagger B^\dagger &= a^\dagger\cos\theta + b^\dagger\sin\theta \\
Bb^\dagger B^\dagger &= b^\dagger\cos\theta - a^\dagger\sin\theta \\
\end{aligned}$$


| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


### Exercise 7.13 {#exercise-713}

First let's do some bookkeeping. The beamsplitters (following the convention in Figure 7.3) perform the following transformation on the mode operators $a$ and $b$

$$\begin{aligned}
b^\dagger \overset{B}{\longrightarrow} \frac{b^\dagger-a^\dagger}{\sqrt{2}}\\
a^\dagger \overset{B}{\longrightarrow} \frac{a^\dagger+b^\dagger}{\sqrt{2}}\\
b^\dagger \overset{B^\dagger}{\longrightarrow} \frac{a^\dagger+b^\dagger}{\sqrt{2}}\\
a^\dagger \overset{B^\dagger}{\longrightarrow} \frac{a^\dagger-b^\dagger}{\sqrt{2}}\\
\end{aligned}$$

Therefore, they have the following impact on the logic states $\ket{0}_L = \ket{0}_b\ket{1}_a=\ket{01}$ and $\ket{1}_L=\ket{1}_b\ket{0}_a=\ket{10}$

$$\begin{aligned}
B\ket{0}_L &= B\ket{01}\\
&= Ba^\dagger \ket{00} \\
&= \frac{a^\dagger + b^\dagger}{\sqrt{2}}\ket{00}\\
&= \frac{\ket{01} + \ket{10}}{\sqrt{2}}\\
&= \frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}}\\
B\ket{1}_L &= B\ket{10} \\
&= Bb^\dagger \ket{00} \\
&= \frac{b^\dagger-a^\dagger}{\sqrt{2}}\ket{00}\\
&= \frac{\ket{10} - \ket{01}}{\sqrt{2}}\\
&= \frac{\ket{1}_L - \ket{0}_L}{\sqrt{2}}\\
\end{aligned}$$

Then for the inverted beamsplitter

$$\begin{aligned}
B^\dagger \ket{0}_L &= B^\dagger \ket{01}\\
&= B^\dagger a^\dagger \ket{00} \\
&= \frac{a^\dagger - b^\dagger}{\sqrt{2}}\ket{00}\\
&= \frac{\ket{01} - \ket{10}}{\sqrt{2}}\\
&= \frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}}\\
B^\dagger \ket{1}_L &= B^\dagger \ket{10} \\
&= B^\dagger b^\dagger \ket{00} \\
&= \frac{a^\dagger+b^\dagger}{\sqrt{2}}\ket{00}\\
&= \frac{\ket{01} + \ket{10}}{\sqrt{2}}\\
&= \frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}}\\
\end{aligned}$$

(1) Let's define the two dual-rail states as follows. 

$$\begin{aligned}
\ket{0}_L\ket{0}_L &= \ket{1001}\\
\ket{0}_L\ket{1}_L &= \ket{1010}\\
\ket{1}_L\ket{0}_L &= \ket{0101}\\
\ket{1}_L\ket{1}_L &= \ket{0110}\\
\end{aligned}$$ 

where $\ket{dcba}$ represents the states of the four modes of light. Note: for the $dc$ pair we flip the logical labeling, as was done in the book. The system initially starts out in the state

$$\begin{aligned}
\ket{10}\ket{01} &= \ket{0}_L\ket{0}_L
\end{aligned}$$

Then after the two beamsplitters before $U_f$, it becomes

$$\begin{aligned}
\left(\frac{\ket{10} - \ket{01}}{\sqrt{2}}\right)\left(\frac{\ket{01} + \ket{10}}{\sqrt{2}}\right) &= \frac{1}{2}\left(\ket{1001} + \ket{1010} - \ket{0101} - \ket{0110}\right) \\
&= \frac{1}{2}\left(\ket{0}_L\ket{0}_L + \ket{0}_L\ket{1}_L - \ket{1}_L\ket{0}_L - \ket{1}_L\ket{1}_L\right) \\
\end{aligned}$$

Which is then the input to $U_f$. The possible outputs for four different functions are

$$\begin{aligned}
\frac{1}{2}\left(\ket{0}_L\ket{0}_L + \ket{0}_L\ket{1}_L - \ket{1}_L\ket{0}_L - \ket{1}_L\ket{1}_L\right)  & \text{when $f(x)=0$}\\
\frac{1}{2}\left(\ket{0}_L\ket{1}_L + \ket{0}_L\ket{0}_L - \ket{1}_L\ket{1}_L - \ket{1}_L\ket{0}_L\right)  & \text{when $f(x)=1$}\\
\frac{1}{2}\left(\ket{0}_L\ket{0}_L + \ket{0}_L\ket{1}_L - \ket{1}_L\ket{1}_L - \ket{1}_L\ket{0}_L\right)  & \text{when $f(x)=x$}\\
\frac{1}{2}\left(\ket{0}_L\ket{1}_L + \ket{0}_L\ket{0}_L - \ket{1}_L\ket{1}_L - \ket{1}_L\ket{0}_L\right)  & \text{when $f(x)=\lnot x$}\\
\end{aligned}$$

So, for the first case, we just need the wires running through the circuit with no additional gates since the output is the same as the input. 

<img width="612" height="282" alt="image" src="https://github.com/user-attachments/assets/06ae63eb-dee1-43ae-acb8-751d9e76287f" />

The evolution of the state through the circuit is as follows

$$\begin{aligned}
 \ket{1}\ket{0}\ket{0}\ket{1} &= \ket{0}_L\ket{0}_L & \text{initial input}\\
 \left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= \left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after beamsplitters} \\
 \left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= \left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after $U_f$} \\
 \ket{1}\ket{0}\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= \ket{0}_L\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after beamsplitter} \\
\end{aligned}$$

For the second case, we need to apply the NOT operation on the second register. This can be done using a Fredkin gate (described in Box 7.4) on the two inputs for the second register with a control input set to $\ket{1}$ 

<img width="612" height="282" alt="image" src="https://github.com/user-attachments/assets/d4fabebd-679b-42b4-9282-b0edd5e66994" />

The evolution of the state through the circuit is as follows

$$\begin{aligned}
\ket{1}\ket{0}\ket{0}\ket{1} &= \ket{0}_L\ket{0}_L & \text{initial input}\\
\left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= \left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after beamsplitters} \\
\left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\ket{1}\ket{0} &= \left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\ket{1}_L & \text{after 1st $U_f$ beamsplitter} \\
-\left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\ket{1}\ket{0} &= -\left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\ket{1}_L  & \text{after Kerr medium} \\
-\left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= -\left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after 2nd $U_f$ beamsplitter} \\
-\ket{10}\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= -\ket{0}_L\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after last beamsplitter} \\
\end{aligned}$$

One thing to note: when looking at the state after $U_f$ there is a $-1$ global phase shift relative to the desired output that we defined earlier. This phase shift won't change detection probabilities. 

For the third case, we need a CNOT with the first register being the control and the second being the target. This can be done using the circuit described in equation 7.46. 

<img width="612" height="282" alt="image" src="https://github.com/user-attachments/assets/74f31c06-9a78-49b4-a428-177e216e5a4a" />

The evolution of the state through the circuit is as follows

$$\begin{aligned}
\ket{1}\ket{0}\ket{0}\ket{1} &= \ket{0}_L\ket{0}_L & \text{initial input}\\
\left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= \left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after beamsplitters} \\
\left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\ket{1}\ket{0} &= \left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\ket{1}_L & \text{after 1st $U_f$ beamsplitter} \\
\left(\frac{\ket{1}\ket{0}+\ket{0}\ket{1}}{\sqrt{2}}\right)\ket{1}\ket{0} &= \left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right)\ket{1}_L  & \text{after Kerr medium} \\
\left(\frac{\ket{1}\ket{0}+\ket{0}\ket{1}}{\sqrt{2}}\right)\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= \left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right)\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after 2nd $U_f$ beamsplitter} \\
\ket{01}\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= \ket{1}_L\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after last beamsplitter} \\
\end{aligned}$$


For the fourth case, we need to implement both the NOT on the second register and a CNOT with the first register being the control and the second being the target. Two middle beamsplitters were removed from the center of the circuit since $BB^\dagger=I$.  

<img width="715" height="283" alt="image" src="https://github.com/user-attachments/assets/c4122ddf-0ede-4f92-9020-c83685e6af46" />

The evolution of the state through the circuit is as follows

$$\begin{aligned}
\ket{1}\ket{0}\ket{0}\ket{1} &= \ket{0}_L\ket{0}_L & \text{initial input}\\
\left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= \left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after beamsplitters} \\
\left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\ket{1}\ket{0} &= \left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\ket{1}_L & \text{after 1st $U_f$ beamsplitter} \\
-\left(\frac{\ket{1}\ket{0}-\ket{0}\ket{1}}{\sqrt{2}}\right)\ket{1}\ket{0} &= -\left(\frac{\ket{0}_L - \ket{1}_L}{\sqrt{2}} \right)\ket{1}_L  & \text{after 1st Kerr medium} \\
-\left(\frac{\ket{1}\ket{0}+\ket{0}\ket{1}}{\sqrt{2}}\right)\ket{1}\ket{0} &= -\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right)\ket{1}_L  & \text{after 2nd Kerr medium} \\
-\left(\frac{\ket{1}\ket{0}+\ket{0}\ket{1}}{\sqrt{2}}\right)\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= -\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right)\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after 2nd $U_f$ beamsplitter} \\
-\ket{01}\left(\frac{\ket{0}\ket{1}+\ket{1}\ket{0}}{\sqrt{2}}\right) &= -\ket{1}_L\left(\frac{\ket{0}_L + \ket{1}_L}{\sqrt{2}} \right) & \text{after last beamsplitter} \\
\end{aligned}$$

One thing to note: when looking at the state after $U_f$ there is a $-1$ global phase shift relative to the desired output that we defined earlier. This phase shift won't change detection probabilities. 

(2) We saw in [exercise 7.9](#exercise-79) that an optical Hadamard gate can be created using a beamsplitter and a phase shifter. The quantum circuit outlined on page 35 starts with Hadamard gates on all wires. So, I believe that this question is asking, why don't we need phase shifters to create the Hadamard gates in these optical circuits. In the optical construction, the beamsplitters already implement the needed Hadamard gate up to a fixed phase that is either global or absorbed into the dual rail labeling, so no separate phase shifters are required. 

(3) Interference at the final beamsplitter for the first logical register explains how the quantum algorithm distinguishes the different $U_f$.

For circuits where $f(x)$ is constant, the oracle does not introduce a relative phase between the two components of the superposition in the first logical register. As a result, the two optical paths arrive at the final beamsplitter in phase and interfere constructively in the same output mode, so the photon exits the same logical output port as it entered.

For circuits where $f(x)$ is balanced, the oracle introduces a relative $\pi$ phase shift between the two components of the superposition in the first logical register. When the paths recombine at the final beamsplitter, this phase difference causes destructive interference in the original output port and constructive interference in the opposite port, causing the photon to exit a different logical output mode.

In this way, the algorithm’s result is determined by interference at the final beamsplitter, allowing the nature of $f(x)$ to be identified with a single measurement.

(4) No. This implementation relies on dual-rail qubits encoded in the single-photon subspace, where exactly one photon occupies one of the two rails. Coherent states populate both rails and involve superpositions of many photon-number states, so the system no longer remains in the logical qubit subspace. As a result, the Fredkin/Kerr elements and the final interference do not implement the required oracle action or phase kickback, and the quantum algorithm fails.



| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 7.14 {#exercise-714}

The definition of $K$ is given by 

$$\begin{aligned}
K &= e^{i \chi L a^\dagger ab^\dagger b}
\end{aligned}$$

and so

$$\begin{aligned}
K\ket{\alpha}\ket{n} &= e^{i \chi L a^\dagger ab^\dagger b}e^{-\vert\alpha\vert^2/2}\sum_{m=0}^{\infty}\frac{\alpha^m}{\sqrt{m!}}\ket{m}\ket{n}\\
&= e^{-\vert\alpha\vert^2/2}\sum_{m=0}^{\infty}\frac{\alpha^m}{\sqrt{m!}}e^{i \chi L a^\dagger ab^\dagger b}\ket{m}\ket{n}\\
&= e^{-\vert\alpha\vert^2/2}\sum_{m=0}^{\infty}\frac{\alpha^m}{\sqrt{m!}}e^{i \chi L m n}\ket{m}\ket{n}\\
&= e^{-\vert\alpha  e^{i \chi L n}\vert^2/2}\sum_{m=0}^{\infty}\frac{\left(\alpha e^{i \chi L n}\right)^m}{\sqrt{m!}}\ket{m}\ket{n}\\
&= \ket{\alpha  e^{i \chi L n}}\ket{n}
\end{aligned}$$

then

$$\begin{aligned}
\rho_a &= Tr_b\lbrack K\ket{\alpha}\ket{\beta}\bra{\beta}\bra{\alpha}K^\dagger\rbrack \\
&= Tr_b\left\lbrack \left(e^{-\vert\beta\vert^2/2}\sum_{m=0}^{\infty}\frac{\beta^m}{\sqrt{m!}}\ket{\alpha  e^{i \chi L m}}\ket{m}\right)\left(e^{-\vert\beta\vert^2/2}\sum_{n=0}^{\infty}\frac{\left(\beta^\ast \right)^n}{\sqrt{n!}}\bra{n}\bra{\alpha  e^{i \chi L n}}\right) \right\rbrack \\
&= e^{-\vert\beta\vert^2}\sum_{m=0}^{\infty}\frac{\vert\beta\vert^{2m}}{m!}\ket{\alpha  e^{i \chi L m}}\bra{\alpha  e^{i \chi L m}} 
\end{aligned}$$

The weights $e^{-\vert\beta\vert^2}\frac{\vert\beta\vert^{2m}}{m!}$ form a Poisson distribution with mode $\lfloor \vert\beta\vert^{2} \rfloor$. Therefore, the main contribution to the sum is for $m=\lfloor \vert\beta\vert^{2} \rfloor$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/QCQI) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

</details>























