---
title: "Mack: Chapter 1"
description: "Notes and exercise solutions for FPOL Chapter 1: basics of IC fabrication, Moore's Law, lithography processing."
categories:
  - Fundamental Principles of Optical Lithography
permalink: /fpol/chapter-1/
toc: true
tags:
  - lithography
  - Fundamental Principles of Optical Lithography
  - Mack
  - chapter 1
  - exercise
  - problem
  - solutions
last_modified_at: 2026-9-7 16:10:00 -08:00
exercises:
  - anchor: problem-11
    label: Problem 1.1
  - anchor: problem-12
    label: Problem 1.2
  - anchor: problem-13
    label: Problem 1.3
  - anchor: problem-14
    label: Problem 1.4
chapter: 1
---

<a id="top"></a>


I just finished reading Chapter 1 of *Fundamental Principles of Optical Lithography* by Chris Mack. I've had this book for years and have frequently referenced specific sections of it, but have never worked through all the problems. Since I am staying in the semiconductor industry, I wanted to switch gears with my studies back to lithography. I really enjoyed the work I did with my quantum computations studies of completing all the exercises and problems in each chapter, even the ones which took days, and so I wanted to apply the same rigor to the study of lithography. 

Chris Mack has been a very influential figure in semiconductor manufacturing in general and my career specifically. When I was interviewing for jobs in the industry I found that watching his online class [CHE 323 Micro and Nanofabrication](https://www.youtube.com/playlist?list=PLM2eE_hI4gSDjK4SiDbhpmpjw31Xyqfo_) to be very helpful as a form of interview prep. Then after entering the field I've rewatched the series at least two more time, just to hammer in the fundamentals. I ultimately purchased his book so that I could dive deeper into specific topics. 

I’ve included my notes and full problem solutions below.

<!-- toc -->


## Basics of IC Fabrication

The rate the resist CD changes during the resist is given by 

$$\begin{aligned}
\frac{dCD}{dt} &= 2\left(R_H + R_V \cot\theta \right) \\
\end{aligned}$$

where $R_H$ and $R_V$ are the horizontal and vertical etch rates and $\theta$ is the sidewall angle of the resist. 

During ion implantation the resist must have a thickness of at least 

$$\begin{aligned}
\text{resist thickness} \geq R_P + m\Delta R_P
\end{aligned}$$

where $R_P$ is the projected range and $\Delta R_R$ is the standard deviation of the depth profile called the stranggle. 

## Moore's Law and the Semiconductor Industry

Reading this section made me want to track down Moore's original papers. 

[Cramming more components into integrated circuits](https://www.cs.utexas.edu/~fussell/courses/cs352h/papers/moore.pdf)

[Progress in digital integrated electronics](https://www.lithoguru.com/scientist/CHE323/Moore1975.pdf)

## Lithography Processing

During substrate preparation the contact angle of a drop of water can be used to determine if the resist will adhere well to the wafer surface, with large contact angles indicating a hydrophobic surface and better resist adhesion. 

During the resist coating process the resist thickness (after a certian threshold) is independent on the amount of resist dispersed and is roughly given by

$$\begin{aligned}
\text{thickness} \propto \frac{v^0.4}{\omega^0.5}
\end{aligned}$$

where $v$ is the resist viscosity and $\omega$ is the spin speed. The final thickness varies over the square root of the spin speed. Though, too high of spin speeds will result in turbulent airflow which will limit uniformity. 

The resolution of the smallest feature that can be printed is given by the Rayleigh resolution criterion:

$$\begin{aligned}
\text{Resolution} \propto \frac{\lambda}{NA}
\end{aligned}$$

where $\lambda$ is the wavelength of the imaging light and $NA$ is the numerical aperture of the projection lens.

During the post-exposure bake, the presence of solvent enhances diffusion. Thus, a low-temperature post-apply bake can result in greater diffusion at PEB. 

## Problems

### Problem 1.1 {#problem-11}



| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/FPOL) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

### Problem 1.2 {#problem-12}


| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/FPOL) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

### Problem 1.3 {#problem-13}


| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/FPOL) | [Blog Archive](https://adj59-dev.github.io/archive.html) |

### Problem 1.4 {#problem-14}


| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/FPOL) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




