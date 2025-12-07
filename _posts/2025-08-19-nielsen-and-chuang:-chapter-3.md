---
title: "Nielsen and Chuang: Chapter 3"
description: "Notes and exercise solutions for QCQI Chapter 3: models for computation, the analysis of computational problems, and perspectives on computer science."
categories:
  - Quantum Computation and Quantum Information
permalink: /qcqi/chapter-3/
toc: true
tags:
  - QCQI
  - quantum computing
  - Quantum Computation and Quantum Information
  - Nielsen & Chuang
  - chapter 3
  - exercise
  - problem
  - solutions
last_modified_at: 2025-12-07 12:00:00 -08:00
exercises:
  - anchor: exercise-31
    label: Exercise 3.1
  - anchor: exercise-32
    label: Exercise 3.2
  - anchor: exercise-33
    label: Exercise 3.3
  - anchor: exercise-34
    label: Exercise 3.4
  - anchor: exercise-35
    label: Exercise 3.5
  - anchor: exercise-36
    label: Exercise 3.6
  - anchor: exercise-37
    label: Exercise 3.7
  - anchor: exercise-38
    label: Exercise 3.8
  - anchor: exercise-39
    label: Exercise 3.9
  - anchor: exercise-310
    label: Exercise 3.10
  - anchor: exercise-311
    label: Exercise 3.11
  - anchor: exercise-312
    label: Exercise 3.12
  - anchor: exercise-313
    label: Exercise 3.13
  - anchor: exercise-314
    label: Exercise 3.14
  - anchor: exercise-315
    label: Exercise 3.15
  - anchor: exercise-316
    label: Exercise 3.16
  - anchor: exercise-317
    label: Exercise 3.17
  - anchor: exercise-318
    label: Exercise 3.18
  - anchor: exercise-319
    label: Exercise 3.19
  - anchor: exercise-320
    label: Exercise 3.20
  - anchor: exercise-321
    label: Exercise 3.21
  - anchor: exercise-322
    label: Exercise 3.22
  - anchor: exercise-323
    label: Exercise 3.23
  - anchor: exercise-324
    label: Exercise 3.24
  - anchor: exercise-325
    label: Exercise 3.25
  - anchor: exercise-326
    label: Exercise 3.26
  - anchor: exercise-327
    label: Exercise 3.27
  - anchor: exercise-328
    label: Exercise 3.28
  - anchor: exercise-329
    label: Exercise 3.29
  - anchor: exercise-330
    label: Exercise 3.30
  - anchor: exercise-331
    label: Exercise 3.31
  - anchor: exercise-332
    label: Exercise 3.32
  - anchor: problem-31
    label: Problem 3.1
  - anchor: problem-32
    label: Problem 3.2
  - anchor: problem-33
    label: Problem 3.3
  - anchor: problem-34
    label: Problem 3.4
  - anchor: problem-35
    label: Problem 3.5
  - anchor: problem-36
    label: Problem 3.6
  - anchor: problem-37
    label: Problem 3.7
  - anchor: problem-38
    label: Problem 3.8
  - anchor: problem-39
    label: Problem 3.9
  - anchor: problem-310
    label: Problem 3.10
chapter: 3
---

<a id="top"></a>

# Nielsen and Chuang: Chapter 3

I just finished reading Chapter 3 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. 

Unlike the previous chapter, which felt more like review, this one was packed with new material for me. Because of this, I found myself searching for additional resources from the *History and further reading* section frequently, which help deepen my understanding of the topics. 

Two of the resources that I found most useful are
[*Computation: Finite and Infinite Machines*](https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf) by Minsky and [*Computational Complexity*](http://103.203.175.90:81/fdScript/RootOfEBooks/E%20Book%20collection%20-%202023%20-%20E/CSE%20ITAIDSML/Computational%20Complexity%20-%20Papadimitriou.pdf) by Papadimitriou. I also pulled in some additional references while working through specific problems, and I’ve linked those alongside my solutions below. 

This chapter covers a lot of foundational theoretical computer science topics: Turing machines, complexity classes, and graph theory. Before now, I only had a hazy awareness of these ideas. I knew that they existed, but I’d never studied them formally. It took me a few weeks to get through the material, but I feel like I’ve built a solid introductory understanding. That said, I think I’ll need to practice more problems (maybe from the books above) to really get comfortable solving them quickly. The chapter also covered circuits. While I’d learned about classical circuits before, the discussion of reversible circuits was new for me. 

I appreciated that the authors explained why these topics matter for quantum computing; it kept me motivated to work through the exercises instead of skipping ahead. I’m curious to see how much of this material will resurface in later chapters.

As with Chapter 2, I’ve included my notes and exercise solutions below. 


<!-- toc -->





## Models for computation
  
### Exercise 3.1 {#exercise-31}

This question is about non-computable processes in Nature. The authors previously went into a more detailed discussion of the Church-Turing thesis in section 1.1.1. Interestingly, section 3.1.1 dropped the word "efficently" from the thesis and just focused on computability. [Minsky](https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf) chapter 5 discusses the idea of computability. 




To recognize that a process in Nature computes a function not computable by a Turing machine, one would need to demonstrate that no Turing machine can reproduce the same input-output behavior. This typically involves proving that the function the process computes is non-computable. According to [Minsky](https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf) (Chapter 5), _“any procedure which can be precisely described can be programmed to be performed by a computer"_. Therefore, if a physical process yields results that cannot be captured by any precisely describable algorithm, it would suggest that the process computes a non-Turing-computable function. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 3.2 {#exercise-32}

I found reading [Minsky](https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf) section 7.2 to be helpful in understanding what this question is asking us to do (and why it may be useful), which is to find a way of representing a given Turing machine's "state diagram" (the set of quintuples that represent its states, inputs, and outputs, i.e. what QCQI authors call the "program") as a unique number that can be used by a universal Turing machine to simulate that specific Turing machine. 




Let's say we have a program described by a finite list of program lines of the form $\braket{q, x, q', x', s}$ with a library consisting of $0, 1, b, \triangleright$, $-1$ for tape-head movement, internal states $q_1, \cdots, q_m$, the starting state $q_s$, and the halting state $q_h$, we can represent each symbol in the library and the different states as a non-negative integer as shown below


| Symbol           | Integer |
|------------------|---------|
| $-1$             | $1$     |
| $0$              | $2$     |
| $1$              | $3$     |
| $b$              | $4$     |
| $\triangleright$ | $5$     |
| $q_s$            | $6$     |
| $q_h$            | $7$     |
| $q_1$            | $8$     |
| $\vdots$         | $\vdots$ |
| $q_m$            | $7+m$   |


If we list out all the symbols and states in the program lines sequentially, like this

$$\begin{aligned}
q_1, x_1, q_1', x_1', s_1, q_2, x_2, q_2', x_2', s_2, \cdots q_k, x_k, q_k', x_k', s_k
\end{aligned}$$

Then you can generate a unique number to represent a Turing machine using the following equation

$$\begin{aligned}
N = p_1^{a_1}p_2^{a_2}p_3^{a_3}\cdots p_{5k}^{a_{5k}}
\end{aligned}$$

Where $p_1, \cdots, p_{5k}$ are unique prime numbers and $a_1, \cdots, a_{5k}$ are integers representing the symbols and states in the program lines. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.3 {#exercise-33}

I found it useful to look at examples in [Minsky](https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf) (section 6.1) and use a multi-tape Turing machine to create this solution, as recommended in the hint. 




We will setup the machine with two tapes, one that has the input binary number followed by blank squares and the other starts all blank. The program is set up to read the binary input from the first tape and print the bits in reverse order on the second. 

The program is given as follows <br>


| $q$              | $x_1$            | $x_2$            | $q'$             | $x_1'$           | $x_2'$           | $s_1$            | $s_2$            |
|------------------|------------------|------------------|------------------|------------------|------------------|------------------|------------------|
| $q_s$            | $\triangleright$ | $\triangleright$ | $q_1$            | $\triangleright$ | $\triangleright$ | $1$              | $1$              |
| $q_1$            | 1                | b                | $q_1$            | 1                | b                | $1$              | $0$              |
| $q_1$            | 0                | b                | $q_1$            | 0                | b                | $1$              | $0$              |
| $q_1$            | b                | b                | $q_2$            | b                | b                | $-1$             | $0$              |
| $q_2$            | 1                | b                | $q_2$            | 1                | 1                | $-1$             | $1$              |
| $q_2$            | 0                | b                | $q_2$            | 0                | 0                | $-1$             | $1$              |
| $q_2$            | $\triangleright$ | b                | $q_h$            | $\triangleright$ | b                | $0$              | $0$              |


Here is an example of how it would run

| $\Downarrow$     |              |              |              |              |              |              |              |              | $q=q_s$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
| $\Uparrow$       |              |              |              |              |              |              |              |              |              |

|                  | $\Downarrow$ |              |              |              |              |              |              |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  | $\Uparrow$   |              |              |              |              |              |              |              |              |

|                  |              | $\Downarrow$ |              |              |              |              |              |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  | $\Uparrow$   |              |              |              |              |              |              |              |              |

|                  |              |              | $\Downarrow$ |              |              |              |              |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  | $\Uparrow$   |              |              |              |              |              |              |              |              |

|                  |              |              |              | $\Downarrow$ |              |              |              |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  | $\Uparrow$   |              |              |              |              |              |              |              |              |

|                  |              |              |              |              | $\Downarrow$ |              |              |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  | $\Uparrow$   |              |              |              |              |              |              |              |              |

|                  |              |              |              |              |              | $\Downarrow$ |              |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  | $\Uparrow$   |              |              |              |              |              |              |              |              |

|                  |              |              |              |              |              |              | $\Downarrow$ |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  | $\Uparrow$   |              |              |              |              |              |              |              |              |

|                  |              |              |              |              |              | $\Downarrow$ |              |              | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  | $\Uparrow$   |              |              |              |              |              |              |              |              |

|                  |              |              |              |              | $\Downarrow$ |              |              |              | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | 1            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              | $\Uparrow$   |              |              |              |              |              |              |              |

|                  |              |              |              | $\Downarrow$ |              |              |              |              | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | 1            | 1            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              |              | $\Uparrow$   |              |              |              |              |              |              |

|                  |              |              | $\Downarrow$ |              |              |              |              |              | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | 1            | 1            | 0            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              |              |              | $\Uparrow$   |              |              |              |              |              |

|                  |              | $\Downarrow$ |              |              |              |              |              |              | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | 1            | 1            | 0            | 1            | b            | b            | b            | b            | $\cdots$     |
|                  |              |              |              |              | $\Uparrow$   |              |              |              |              |

|                  | $\Downarrow$ |              |              |              |              |              |              |              | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | 1            | 1            | 0            | 1            | 0            | b            | b            | b            | $\cdots$     |
|                  |              |              |              |              |              | $\Uparrow$   |              |              |              |

| $\Downarrow$     |              |              |              |              |              |              |              |              | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | 1            | 1            | 0            | 1            | 0            | 1            | b            | b            | $\cdots$     |
|                  |              |              |              |              |              |              | $\Uparrow$   |              |              |

| $\Downarrow$     |              |              |              |              |              |              |              |              | $q=q_h$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 1            | 0            | 1            | 1            | b            | b            | $\cdots$     |
| $\triangleright$ | 1            | 1            | 0            | 1            | 0            | 1            | b            | b            | $\cdots$     |
|                  |              |              |              |              |              |              | $\Uparrow$   |              |              |

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.4 {#exercise-34}






We will use two tapes for this machine. The first will contain the binary values and the second will start out blank. The program will first transfer the values for the first number to the second tape, then do a bit-wise XOR on the last digit of the two numbers, replacing the last value on the second tape with the result, then it will zero out the rest of the values on the second tape, so that the value on the second tape is the answer. 

The program is given as follows

| $q$              | $x_1$            | $x_2$            | $q'$             | $x_1'$           | $x_2'$           | $s_1$            | $s_2$            |
|------------------|------------------|------------------|------------------|------------------|------------------|------------------|------------------|
| $q_s$            | $\triangleright$ | $\triangleright$ | $q_1$            | $\triangleright$ | $\triangleright$ | $1$              | $1$              |
| $q_1$            | $1$              | $b$              | $q_1$            | $1$              | $1$              | $1$              | $1$              |
| $q_1$            | $0$              | $b$              | $q_1$            | $0$              | $0$              | $1$              | $1$              |
| $q_1$            | $b$              | $b$              | $q_2$            | $b$              | $b$              | $1$              | $0$              |
| $q_2$            | $1$              | $b$              | $q_2$            | $1$              | $b$              | $1$              | $0$              |
| $q_2$            | $0$              | $b$              | $q_2$            | $0$              | $b$              | $1$              | $0$              |
| $q_2$            | $b$              | $b$              | $q_3$            | $b$              | $b$              | $-1$             | $-1$             |
| $q_3$            | $1$              | $1$              | $q_4$            | $1$              | $0$              | $-1$             | $-1$             |
| $q_3$            | $0$              | $0$              | $q_4$            | $0$              | $0$              | $-1$             | $-1$             |
| $q_3$            | $1$              | $0$              | $q_4$            | $1$              | $1$              | $-1$             | $-1$             |
| $q_3$            | $0$              | $1$              | $q_4$            | $0$              | $1$              | $-1$             | $-1$             |
| $q_4$            | $1$              | $1$              | $q_4$            | $1$              | $0$              | $-1$             | $-1$             |
| $q_4$            | $0$              | $0$              | $q_4$            | $0$              | $0$              | $-1$             | $-1$             |
| $q_4$            | $1$              | $0$              | $q_4$            | $1$              | $0$              | $-1$             | $-1$             |
| $q_4$            | $0$              | $1$              | $q_4$            | $0$              | $0$              | $-1$             | $-1$             |
| $q_4$            | $b$              | $\triangleright$ | $q_h$            | $b$              | $\triangleright$ | $0$              | $0$              |

Here is an example of how it would run for $x = 100$ and $y=111$

| $\Downarrow$     |              |              |              |              |              |              |              |              | $q=q_s$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
| $\Uparrow$       |              |              |              |              |              |              |              |              |              |

|                  | $\Downarrow$ |              |              |              |              |              |              |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | b            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  | $\Uparrow$   |              |              |              |              |              |              |              |              |

|                  |              | $\Downarrow$ |              |              |              |              |              |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 1            | b            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              | $\Uparrow$   |              |              |              |              |              |              |              |

|                  |              |              | $\Downarrow$ |              |              |              |              |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 1            | 0            | b            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              |              | $\Uparrow$   |              |              |              |              |              |              |

|                  |              |              |              | $\Downarrow$ |              |              |              |              | $q=q_1$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 1            | 0            | 0            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              |              |              | $\Uparrow$   |              |              |              |              |              |

|                  |              |              |              |              | $\Downarrow$ |              |              |              | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 1            | 0            | 0            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              |              |              | $\Uparrow$   |              |              |              |              |              |

|                  |              |              |              |              |              | $\Downarrow$ |              |              | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 1            | 0            | 0            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              |              |              | $\Uparrow$   |              |              |              |              |              |

|                  |              |              |              |              |              |              | $\Downarrow$ |              | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 1            | 0            | 0            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              |              |              | $\Uparrow$   |              |              |              |              |              |

|                  |              |              |              |              |              |              |              | $\Downarrow$ | $q=q_2$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 1            | 0            | 0            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              |              |              | $\Uparrow$   |              |              |              |              |              |

|                  |              |              |              |              |              |              | $\Downarrow$ |              | $q=q_3$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 1            | 0            | 0            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              |              | $\Uparrow$   |              |              |              |              |              |              |

|                  |              |              |              |              |              | $\Downarrow$ |              |              | $q=q_4$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 1            | 0            | 1            | b            | b            | b            | b            | b            | $\cdots$     |
|                  |              | $\Uparrow$   |              |              |              |              |              |              |              |

|                  |              |              |              |              | $\Downarrow$ |              |              |              | $q=q_4$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 1            | 0            | 1            | b            | b            | b            | b            | b            | $\cdots$     |
|                  | $\Uparrow$   |              |              |              |              |              |              |              |              |

|                  |              |              |              | $\Downarrow$ |              |              |              |              | $q=q_4$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 0            | 0            | 1            | b            | b            | b            | b            | b            | $\cdots$     |
| $\Uparrow$       |              |              |              |              |              |              |              |              |              |

|                  |              |              |              | $\Downarrow$ |              |              |              |              | $q=q_h$      | 
|------------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|
| $\triangleright$ | 1            | 0            | 0            | b            | 1            | 1            | 1            | b            | $\cdots$     |
| $\triangleright$ | 0            | 0            | 1            | b            | b            | b            | b            | b            | $\cdots$     |
| $\Uparrow$       |              |              |              |              |              |              |              |              |              |

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.5 {#exercise-35}

In Box 3.2 the authors introduce the halting problem for a Turing machine with an input equal to its Turing number. For this exercise, we are asked to think about the halting problem for a Turing machine with no inputs. The blank tape halting problem is discussed by [Minsky](https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf) in section 8.3.3 of his book, if you'd like another resource for this exercise. 




Let's say that we can create an algorithm to determine whether a Turing machine halts when the input to the machine is a blank tape. With this algorithm, we could take a machine $T$ with tape $t$ and make a new machine $M_T$ which is constructed from the description of $T$ with additional program lines. These additional lines will generate the output of $t$ on a blank tape at the start of the computation, such that $M_T$ starting with a blank tape is the equivalent of $T$ starting with tape $t$. Using the algorithm mentioned above, we can determine whether $M_T$ halts when the input to the machine is a blank tape, this means that using the algorithm we can determine if $T$ halts starting with tape $t$. 

From Box 3.2, we know that there is no algorithm that can be used to determine if a Turing machine with Turing number $x$ halts upon input of $x$. But with our algorithm we can determine if $T$ halts when $t=x$. We have a contradiction; therefore it is not possible to create an algorithm to determine whether a Turing machine halts when the input to the machine is a blank tape.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.6 {#exercise-36}

In this exercise we are asked to revisit the halting problem again, but this time the Turing machine is probabilistic. On page 127, the authors talk about creating a probabilistic Turing machine by adding a random component to the change in internal states with the execution of each program line. I am not confident in my solution to this exercise, as I don't have much experience with this area of theoretical computer science, but I'll put what I have below. Let me know if you have a better solution. 




The halting function is now

$$\begin{equation}
  h_p(x)=\begin{cases}
    1, & \text{if machine $x$ halts on input of $x$ with probability of at least $1/2$}.\\
    0, & \text{if machine $x$ halts on input of $x$ with a probability of less than $1/2$}.
  \end{cases}
\end{equation}$$

Let's say that the Turing machine halts with probability $P_h > 1/2$, which means that we expect $h_p = 1$. As with the example in Box 3.2 we'll consider an algorithm computing the function TURING($x$) with pseudocode. Here HALT($x$) is calculated for each execution of the algorithm, such that 

$$\begin{equation}
  \text{HALT}(x)=\begin{cases}
    1, & \text{if machine $x$ halts on input of $x$}.\\
    0, & \text{if machine $x$ does not halt on input of $x$}.
  \end{cases}
\end{equation}$$

Here we expect HALT($x$) to be 1 with a probability $P_h$ and 0 with the probability $1-P_h$. The pseudocode is then

```
TURING(x)

y = HALT(x)
if y = 0 then
  halt
else
  loop forever
end if
```

Each time this algorithm is run, there is a probability $P_h$ of getting $0$ and a probability of $1-P_h$ of it looping forever. This contradicts our expectations of it halting with probability $P_h$. If $P_h$ was not strictly greater than $1/2$, but instead allowed to be equal to $1/2$ then we could have the situation where $P_h = 1-P_h$, and there would be no contradiction, but we want to find a case where the probability of correctness is strictly greater than $1/2$. Putting this in terms of our halting function, we find that $h_p = 0$, but we know that $h_p = 1$. Therefore, there is a contradiction and so there is no probabilistic Turing machine which can output $h_p(x)$ with probability of correctness strictly greater than $1/2$ for all $x$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.7 {#exercise-37}






An oracle machine with access to a halting problem oracle for standard Turing machines can decide whether any given Turing machine halts. However, no oracle machine can solve its own halting problem, by a similar argument to the one that shows no Turing machine can decide its own halting behavior. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.8 {#exercise-38}






This is how you can make an AND gate with NAND gates

<img width="444" height="122" alt="image" src="https://github.com/user-attachments/assets/13a1479b-773c-4380-8d03-d0aeb547a979" />

| a | b | a NAND b | (a NAND b) NAND (a NAND b) | a AND b|
|---|---|----------|----------------------------|--------|
| 0 | 0 | 1        | 0                          | 0      |
| 1 | 0 | 1        | 0                          | 0      |
| 0 | 1 | 1        | 0                          | 0      |
| 1 | 1 | 0        | 1                          | 1      |


This is how you can make a NOT gate with a NAND gate

<img width="268" height="102" alt="image" src="https://github.com/user-attachments/assets/ac0668bd-53b1-4d25-b471-3bd2e7452590" />

| a | a NAND a | NOT a |
|---|----------|-------|
| 0 | 1        | 1     |
| 1 | 0        | 0     |


This is how you can make a XOR gate with NAND gates

<img width="769" height="209" alt="image" src="https://github.com/user-attachments/assets/b16673b8-6b78-4a6e-a5c1-c644c3e7e1d9" />


| a | b | a NAND b | a NAND (a NAND b) | b NAND (a NAND b)| (a NAND (a NAND b)) NAND (b NAND (a NAND b)) | XOR |
|---|---|----------|-------------------|------------------|----------------------------------------------|-----|
| 0 | 0 | 1        | 1                 | 1                | 0                                            | 0   |
| 1 | 0 | 1        | 0                 | 1                | 1                                            | 1   |
| 0 | 1 | 1        | 1                 | 0                | 1                                            | 1   |
| 1 | 1 | 0        | 1                 | 1                | 0                                            | 0   |

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |





## The analysis of computational problems

### Exercise 3.9 {#exercise-39}






We know that $f(n)$ is $O(g(n))$ if $f(n) \leq cg(n)$ for some constant $c$ and for all $n \geq n_0$. We also know that $g(n)$ is $\Omega (f(n))$ if $g(n) \geq c'f(n)$ for some constant $c'$ and for all $n \geq n_0'$. If we set $c = \frac{1}{c'}$ and $n_0 = n_0'$, then we can see that the two inequalities are identical. Therefore, $f(n)$ is $O(g(n))$ if and only if $g(n)$ is $\Omega (f(n))$.

We know that $f(n)$ is $\Theta (g(n))$ when $f(n)$ behaves the same as $g(n)$ asymptotically. When this is the case, we can also say that $g(n)$ behaves the same as $f(n)$ asymptotically and so $g(n)$ is $\Theta (f(n))$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.10 {#exercise-310}






To show that $g(n)$ is $O(n^l)$ we need to show that $g(n) \leq cn^l$ for some real positive constant $c$ and for all $n \geq n_0$ for some $n_0$. We know that $g(n) = \sum_{i=0}^k c_i n^i$. If we set $c=c_k$, then $c_k n^k + \sum_{i=0}^{k-1} c_i n^i \leq c_k n^l$. For sufficiently large $n$ the lower order terms on the left hand side become small compared to the $k\text{th}$ term and can be ignored, so we have $c_k n^k \leq c_k n^l$, which is always true. Therefore a polynomial of degree $k$ is $O(n^l)$ for any $l \geq k$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.11 {#exercise-311}






To show that log $n$ is $O(n^k)$ for any $k > 0$ we need to show that the following is true for some real positive constant $c$ and $n_0$ for all $n>n_0$

$$\begin{aligned}
\log n & \leq cn^k \\
n & \leq e^{cn^k} & \text{take the exponential of both sides} \\
n & \leq \sum_{i=0}^\infty \frac{(cn^k)^i}{i!} & \text{power series for an exponential function} \\
n & \leq \sum_{i=0}^\infty \frac{c^i n^{ik}}{i!} \\
n & \leq \sum_{i=0}^\infty \frac{\left(\log_{i'}(i'!) \right)^i n^{ik}}{i!} & \text{let $c=\log_{i'}(i'!)$ where $i'$ is the first $i$ such that $i'k \geq 1$} \\
n & \leq \frac{\left(\log_{i'}(i'!) \right)^{i'} n^{i'k}}{i'!} + \sum_{i=0}^{i'-1} \frac{\left(\log_{i'}(i'!) \right)^i n^{ik}}{i!} + \sum_{i=i'+1}^\infty \frac{\left(\log_{i'}(i'!) \right)^i n^{ik}}{i!} & \text{split out the $i'$th term}\\
n & \leq n^{i'k} + \sum_{i=0}^{i'-1} \frac{\left(\log_{i'}(i'!) \right)^i n^{ik}}{i!} + \sum_{i=i'+1}^\infty \frac{\left(\log_{i'}(i'!) \right)^i n^{ik}}{i!}
\end{aligned}$$ 

Since we know $i'k \geq 1$ and all the terms in the summations are positive, we know the inequality is true and therefore log $n$ is $O(n^k)$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.12 {#exercise-312}






We need to show that $n^k \leq c n^{\log n}$ for some real positive constant $c$, some $n_0$, and any $k$ for $n \geq n_0$.

$$\begin{aligned}
n^k & \leq cn^{\log n} \\
k & \leq \log_n (cn^{\log n}) & \text{take $log_n$ of both sides}\\
k & \leq \log_n (c) + \log_n(\log n) \\
k & \leq k + \log_n(\log n) & \text{set $\log_n (c) = k$ }
\end{aligned}$$ 

It can be seen that this inequality is true when $\log_n(\log n) \geq 0$, which will happen for all $n \geq 2$, since $\log$ is base $2$ when not specified as something else in this book. This shows that $n^k$ is $O(n^{\log n})$ for any $k$ and $n^{\log n}$ is never $O(n^k)$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.13 {#exercise-313}






We need to show that $c^n \geq a n^{\log n}$ for some real positive constant $a$, some $n_0$, and any $c > 1$ for $n \geq n_0$.

$$\begin{aligned}
c^n & \geq a n^{\log n} \\
n & \geq \log_c(a n^{\log n}) & \text{take $log_c$ of both sides} \\
n & \geq \log_c (a) + \log_c(n^{\log n}) \\
n & \geq \log_c (a) + \log(n)\log_c(n) \\
n & \geq \log(n)\log_c(n) & \text{set $a=1$} \\
n & \geq \frac{(\log(n))^2}{\log (c)} & \text{changing the base}
\end{aligned}$$ 

We know that $n$ grows faster than $(\log(n))^2$ (this can easily be seen by taking the derivative of both functions) and so the above inequality will be true for sufficiently large $n$ and $c>1$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.14 {#exercise-314}






Since $e(n)$ is $O(f(n))$ we know that $e(n) \leq cf(n)$ for some real positive constant $c$ and for all $n \geq n_0$. Also since $g(n)$ is $O(h(n))$ we know that $g(n) \leq dh(n)$ for some real positive constant $d$ and for all $n \geq n_1$. To show that $e(n)g(n)$ is $O(f(n)h(n))$, we need to show that $e(n)g(n) \leq b f(n)h(n)$ for some real positive constant $b$ and for all $n \geq n_2$. 

$$\begin{aligned}
e(n)g(n) \leq b f(n)h(n) \\
e(n)g(n) \leq cd f(n)h(n) & \text{let $b = cd$} \\
e(n)g(n) \leq (c f(n))(d h(n))
\end{aligned}$$ 

Since we know that $e(n) \leq cf(n)$ for $n \geq n_0$ and $g(n) \leq dh(n)$ for $n \geq n_1$ we know that the above inequality is true for $n \geq n_2$ where $n_2 = \max(n_0, n_1)$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.15 {#exercise-315}

 




There are $n!$ possible initial orderings of the list. Below is a table that shows how many of those orderings $n_k$ are in the correct order after $k$ compare-and-swaps. 

| $k$ | $n_k$ | Note                                                                      |
|-----|-------|---------------------------------------------------------------------------|
| 0   | 1     | With zero swaps only the ordering that started in order is in the correct order |
| 1   | 2     | With one compare-and-swap, two entries are compared and only the ordering that had those two entries out of order is put in order with the swap. The ordering that was already in order stays in order since the two values which were compared are not swapped. |
| 2   | 4     | The two scenarios from above still occur in this case. But now another pair is compared, so we have the added possibility of the first pair not swapping and second pair swapping and also the possibility of both pairs swapping. |
| 3   | 8     | Possibilities: zero pairs swapping, only the first pair swapping, only the second pair swapping, only the third pair swapping, first and second pair swapping, second and third pair swapping, first and third pair swapping, all pairs swapping | 
| k   | 2^k   | Continuing the trend we find that there are $2^k$ possible combinations    |

In order to find how many compare-and-swap operations are required to sort all possible combinations we need to find $k$ when $n! = 2^k$. 

$$\begin{aligned}
2^k &= n! \\
k &= \log(n!) & \text{take the log of both sides} \\
k & \approx n\log(n) - n\log(e) + O(\log (n)) & \text{Stirling's approximation} 
\end{aligned}$$ 

Now to confirm that this $k$ is $\Omega (n\log(n))$ we need to show that $k \geq c n\log(n)$ for some real positive constant $c$ and for all $n \geq n_0$. 

$$\begin{aligned}
 k \geq c n\log(n) \\
 n\log(n) - n\log(e) + O(\log (n)) \geq c n\log(n) \\
\end{aligned}$$ 

For sufficiently large $n$ the left-hand side is dominated by the $n\log(n)$ term and so if $c<1$ the above inequality will be true for $n > n_0$ for some value of $n_0$. Therefore $\Omega (n\log(n))$ compare-and-swap operations are required to sort all possible initial orderings into the correct order.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.16 {#exercise-316}

Note: the online [errata page](https://michaelnielsen.org/qcqi/errata/errata/errata.html) says that $2^n/\log(n)$ should be $2^n/n$. 

This problem is challenging, and I ended up referencing the following resources to find and understand the solution. I did change some steps in my solution compared to what is in these resources. These changes did not impact the final result - it just made more sense to me to do it that way.  <br>
-[how many semantically different boolean functions are there for n boolean variables?](https://math.stackexchange.com/questions/505393/how-many-semantically-different-boolean-functions-are-there-for-n-boolean-variab) <br>
-[Circuit Complexity](https://www.cs.umd.edu/~jkatz/complexity/f05/lecture4.pdf) <br>
-[Size and Depth complexity of Boolean Circuits](https://deeplearning.cs.cmu.edu/S25/document/readings/booleancircuits_shannonproof.pdf) <br>
-[How to show that hard-to-compute Boolean functions exist?](https://cs.stackexchange.com/questions/82271/how-to-show-that-hard-to-compute-boolean-functions-exist)




We know a Boolean function takes $n$ input bits and outputs a single bit, $f: \lbrace 0,1 \rbrace ^n \rightarrow \lbrace 0,1 \rbrace$. With $n$ bits there are $2^n$ possible distinct input combinations. With each input combination there are two possible outcomes, meaning that there are $2^{2^n}$ possible functions. Below is an example of all 16 possible functions for the case of $n=2$.

|$n_1$|$n_2$|$f_1$|$f_2$|$f_3$|$f_4$|$f_5$|$f_6$|$f_7$|$f_8$|$f_9$|$f_{10}$|$f_{11}$|$f_{12}$|$f_{13}$|$f_{14}$|$f_{15}$|$f_{16}$|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|--------|--------|--------|--------|--------|--------|--------|
|**0**|**0**| 0   | 1   | 0   | 0   | 0   | 1   | 1   | 1   | 0   | 0      | 0      | 1      | 1      | 1      | 0      | 1      |
|**1**|**0**| 0   | 0   | 1   | 0   | 0   | 1   | 0   | 0   | 1   | 1      | 0      | 1      | 1      | 0      | 1      | 1      |
|**0**|**1**| 0   | 0   | 0   | 1   | 0   | 0   | 1   | 0   | 1   | 0      | 1      | 1      | 0      | 1      | 1      | 1      |
|**1**|**1**| 0   | 0   | 0   | 0   | 1   | 0   | 0   | 1   | 0   | 1      | 1      | 0      | 1      | 1      | 1      | 1      |


Let's say that we have a collection of circuits, each created with $m$ logic gates. We'd like to know what the maximum number of distinct circuits we can create with the $n$ inputs and $m \geq n-1$ logic gates with two inputs (you need at least $n-1$ two-input gates to take $n$ inputs and reduce it to one output). For each of the gates there are $16$ possible logic functions, as we showed in the table above. Each of the two gate inputs can come from either the inputs $n$ or the output from one of the other $m-1$ gates, resulting in $(n + m - 1)^2$ possible combinations of inputs, and so there are $16(n+m-1)^2$ ways to create each gate, except for the output gate which is specifically defined. This results in $m(16(n+m-1)^2)^{m-1}$ possible circuit configurations. However, this calculation is overcounting due to there being multiple permutations of the gates. This estimate can be tightened by dividing by $m!$ which gives us $\frac{m\left( 16(n+m-1)^2 \right)^{m-1}}{m!}$ possible circuit configurations. 

Now we have an equation that bounds the number of circuits configurations that one can create with $m$ gates and $n$ inputs. We also know the number of Boolean functions possible with $n$ inputs. So now what we want to find is the minimum number of gates needed to create a circuit for each possible Boolean function, i.e. we need to find an $m$ such that the number of possible circuit configurations is greater than or equal to the number of Boolean functions we can create with $n$ inputs. 

First let's write out and simplify the inequality

$$\begin{aligned}
2^{2^n} &\leq \frac{m\left( 16(m+n-1)^2 \right)^{m-1}}{m!} \\
&\leq \frac{m\left( 16(m+m)^2 \right)^{m-1}}{m!} & \text{since $m \geq n-1$} \\
&= \frac{m\left( 64(m)^2 \right)^{m-1}}{\sqrt{2\pi m}\left(\frac{m}{e} \right)^m \left(1 + O\left(\frac{1}{m} \right) \right)} & \text{Stirling's formula} \\
&= \frac{(m)^{m - 3/2} (64e)^{m-1}}{\sqrt{2\pi} \left(1 + O\left(\frac{1}{m} \right) \right)}\\
2^n &\leq \log\left( \frac{(m)^{m - 3/2} (64e)^{m-1}}{\sqrt{2\pi} \left(1 + O\left(\frac{1}{m} \right) \right)} \right) & \text{take the log of both sides} \\
&= \log\left((m)^{m - 3/2}\right) + \log\left((64e)^{m-1} \right)- \log\left( \sqrt{2\pi} \left(1 + O\left(\frac{1}{m} \right) \right) \right) \\
&= (m - \frac{3}{2})\log\left(m\right) + (m-1)\log\left(64e \right)- \log\left( \sqrt{2\pi} \left(1 + O\left(\frac{1}{m} \right) \right) \right) \\
&= m\log\left(m\right) - \frac{3}{2}\log\left(m\right) + m\log\left(64e \right) - \log\left(64e \right)- \log\left( \sqrt{2\pi} \left(1 + O\left(\frac{1}{m} \right) \right) \right) \\
&= m\log\left(m\right) + O(m)
\end{aligned}$$

Now let's write both sides of the inequality $2^n \leq m\log\left(m\right) + O(m)$ in more easily comparable forms. 

$$\begin{aligned}
m\log\left(m\right) + O(m) &\geq 2^n \\
&= 2^n - \frac{2^n}{n}\log\left(n\right) + \frac{2^n}{n}\log\left(n\right) \\
&= \frac{2^n}{n}\left(n - \log\left(n\right)\right) + \frac{2^n}{n}\log\left(n\right)\\
&= \frac{2^n}{n}\left(n\log\left(2\right) - \log\left(n\right)\right) + \frac{2^n}{n}\log\left(n\right)\\
&= \frac{2^n}{n}\left(\log\left(2^n\right) - \log\left(n\right)\right) + \frac{2^n}{n}\log\left(n\right)\\
&= \frac{2^n}{n}\log\left(\frac{2^n}{n}\right) + \frac{2^n}{n}\log\left(n\right)
\end{aligned}$$

If we set $m = \frac{2^n}{n}$ then we would have $\frac{2^n}{n}\log(\frac{2^n}{n}) + O\left( \frac{2^n}{n}\right) \geq \frac{2^n}{n}\log\left(\frac{2^n}{n}\right) + \frac{2^n}{n}\log\left(n\right)$, which is not true for sufficiently large $n$, this means that $m$ must be greater than $\frac{2^n}{n}$ for at least some Boolean functions. Therefore there exists Boolean functions with $n$ inputs that require at least $\frac{2^n}{n}$ logic gates to compute. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.17 {#exercise-317}






Suppose we have a polynomial-time algorithm that can find a non-trivial factor of a composite number $m$. Then we could solve the factoring decision problem in polynomial time as follows:

1.	Use the factor-finding algorithm to obtain all factors $n_i$ of $m$. 
2.	For each $n_i$ check whether $n_i<l$, which is a simple comparison and can be done in polynomial time.
3.	Report yes if at least one $n_i$ is less than $l$ and no otherwise

Thus, if finding non-trivial factors is in **P**, then the factoring decision problem is also in **P**.

Conversely, suppose we can solve the factoring decision problem in polynomial time for any input $(m, l)$. Then we can find the smallest non-trivial factor $s$ of $m$ by performing a binary search over the range $2$ to $m-1$ using the decision problem as an oracle. Each step of the binary search involves asking whether a factor exists below a certain bound $l$, which takes polynomial time. 

Once we find $s$ we can calculate $r=\frac{m}{s}$ and recursively apply the same method to $r$. We repeat this process until all factors are found. Since binary search requires only $O(\log m)$ calls, the entire procedure runs in polynomial time. Therefore, if the factoring decision problem is in **P**, then finding the factors is also in **P**.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 3.18 {#exercise-318}

I found it useful to read more about complement complexity classes in [Papadimitriou](http://103.203.175.90:81/fdScript/RootOfEBooks/E%20Book%20collection%20-%202023%20-%20E/CSE%20ITAIDSML/Computational%20Complexity%20-%20Papadimitriou.pdf) section 7.1 before solving this exercise. 




**NP** and **coNP** are complements of each other. In [Papadimitriou](http://103.203.175.90:81/fdScript/RootOfEBooks/E%20Book%20collection%20-%202023%20-%20E/CSE%20ITAIDSML/Computational%20Complexity%20-%20Papadimitriou.pdf) (section 7.1) a complement complexity class $C$ is defined as the class $\lbrace \bar{L} : L \in C \rbrace$, where $\bar{L}$ is the complement of language $L$. If C is a deterministic complexity class, then $C=coC$. This is because any deterministic Turing machine deciding $L$ can be converted to decide $\bar{L}$ within the same time or space bound by reversing the roles of "yes" and "no". Since **P** is a deterministic complexity class, **P** $=$ **coP**. If **P** = **NP**, that would mean that **NP** = **P** = **co(P)** = **co(NP)**. Therefore if **coNP** $\neq$ **NP**, it must mean that **P** $\neq$ **NP**.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.19 {#exercise-319}

[Papadimitriou](http://103.203.175.90:81/fdScript/RootOfEBooks/E%20Book%20collection%20-%202023%20-%20E/CSE%20ITAIDSML/Computational%20Complexity%20-%20Papadimitriou.pdf) section 1.1 discuses graph reachability and answers this question. I was not sure how to approach this exercise before reading this section, since I had not worked with these kind of graph problems before, but the general approach is that at each step of an algorithm you can access a vertex, see what edges and other vertices are connected to that vertex, update variables or perform other actions as desired, and then proceed on to the next step. 




The following function written in pseudocode determines whether there is a path between vertex s and vertex f. 

```
path(s, f, graph):
  S = [s]
  M = [s]
  while S is not empty
    let v = the first element of S
    add all vertices connected to v and not in M to S
    add all vertices connected to v and not in M to M
    remove v from S
  if f is in M
    return yes
  else
    return no

```
Here the algorithm starts by initializing two lists, S and M, and adding the starting vertex s to both lists. The following steps are repeated until list S is empty: (1) finds all the vertices connected to the first element in list S that are not in list M, (2) adds these vertices to S and M, (3) remove the first element of list S. The algorithm then checks if f is in M and returns yes if it is and no if it isn't. It can be seen that this function is $O(n)$ since v is only able to represent each vertex one time and so the while loop only loops, at most, $n$ times.

A graph is considered connected if there is a path between every pair of vertices. We could modify our path function to determine if the graph is connected.

```
connected(graph):
  for s in graph
    S = [s]
    M = [s]
    while S is not empty
      let v = the first element of S
      add all vertices connected to v and not in M to S
      add all vertices connected to v and not in M to M
      remove v from S
    if the length of M < n
      return no
  return yes

```

Here an algorithm like the path function runs for each vertex in V, but instead of checking if a single vertex is in list M, it checks to see if all vertices are in M by comparing the length of M to n. If all the vertices are in M, the algorithm keeps going and checks the next vertex in V until all vertices are checked and then yes is returned. If it finds that the length of M < n for a vertex, it returns no and the algorithm stops before checking all the vertices. Since running the path function once is $O(n)$, this algorithm is $O(n^2)$ since it is like running the path algorithm up to $n$ times. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.20 {#exercise-320}
 




For an Euler cycle to exist, each vertex needs at least two incident edges, one to go away from the vertex and one to return to the vertex. A simple example is shown in Example 1 where there are three vertices, all connected. An Euler cycle can be identified as $1,2,3,1$.


<p align="center" width="100%">
  <img width="170" height="226" alt="image" src="https://github.com/user-attachments/assets/f800a841-67f3-4f54-8ed9-a012d5237d43" /> <br>
  Example 1
</p>

Additional edges can be added to a vertex beyond 2, but to have an Euler cycle they must be added in pairs, one going away from the vertex and one returning to the vertex. An Euler cycle in Example 2 is $1,2,3,1,4,5,1,6,7,1$.

<p align="center" width="100%">
  <img width="462" height="434" alt="image" src="https://github.com/user-attachments/assets/8c10f000-1110-4ab1-9cb1-6c22068c1198" /> <br>
  Example 2
</p>

This requirement isn't just for the vertex you start your Euler cycle on. Other vertices also need to have edges added in pairs, one going away from the vertex and one returning. An Euler cycle in Example 3 is $1,2,3,8,9,3,1,4,5,1,6,7,1$. Here a new sub-cycle $3,8,9,3$ was inserted in place of the $3$ in Example 2.

<p align="center" width="100%">
  <img width="566" height="442" alt="image" src="https://github.com/user-attachments/assets/ebca79e8-6469-44f1-9486-045af91f9f77" /> <br>
  Example 3 
</p>

If you don't have an even number of vertices, you won't be able to return to a vertex after going off on a sub-cycle and so you won't be able to continue the rest of the Euler cycle, as shown in Example 4. 

<p align="center" width="100%">
  <img width="558" height="412" alt="image" src="https://github.com/user-attachments/assets/6e6bd53a-612e-43a8-b139-b015617d6310" /> <br>
  Example 4
</p>

Therefore, if a graph has a Euler cycle, every vertex must have an even number of edges connected to it. Conversely, if all vertices have an even number of edges, the graph will have a Euler cycle. This is because as you traverse a path on the graph, whenever you arrive at a vertex you use up one incident unused edge and, since the vertex has an even number of edges, there is at least one other unused edge to take for the next step until you arrive back at your starting vertex. If there are additional unused edges left after arriving back at the starting vertex, you can create sub-cycles with those unused edges and then insert them into the main cycle, like what was done going from Example 2 to Example 3. 

Below is a procedure for finding a Euler cycle: <br>
(1) create an empty list where you'll track all the edges visited and an empty list where you'll track the cycle <br>
(2) pick a starting vertex and add it to your cycle list <br> 
(3) go to a vertex connected to your current vertex by an edge that is not in your visited edges list <br>
(4) add the edge traversed to the visited edges list and the vertex to the cycle list <br>
(5) repeat steps 3 and 4 until you are back at your starting vertex without any more edges available to traverse. If you end up somewhere other than your starting vertex, it means that the graph does not contain a Euler cycle. <br>
(6) If there are edges in the graph not on your list, find a vertex in the list that still has available edges and go there <br>
(7) go through steps 3-5 and add the path you just traversed to your cycle by inserting it in to the cycle in the location of the vertex identified in step 6 <br>
(8) repeat steps 6-7 until all edges are traversed in the cycle <br>

Here is that procedure written out in pseudocode

```
EulerCycle(starting_vertex, graph):

    // Step 0: first confirm that a Euler cycle exists
    if not all vertices in the graph have an even number of connected edges
        return []

    // Step 1–2: create lists, set starting vertex, add starting vertex to cycle
    cycle = []                         
    visited_edges = []                 
    current_vertex = starting_vertex
    append current_vertex to cycle

    // Step 3–5: build initial closed cycle
    while exists unused edge from current_vertex:
        next_vertex = neighbor of current_vertex connected by unused edge
        add edge (current_vertex, next_vertex) to visited_edges
        append next_vertex to cycle
        current_vertex = next_vertex

    // Step 6–8: expand cycle until all edges are used
    while there exists a vertex u in cycle with unused edges:
        current_vertex = u
        new_path = [u]
        while exists unused edge from current_vertex:
            next_vertex = neighbor of current_vertex connected by unused edge
            add edge (current_vertex, next_vertex) to visited_edges
            append next_vertex to new_path
            current_vertex = next_vertex
        insert new_path into cycle at the position of u

    return cycle
```

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.21 {#exercise-321}






If $L_1$ is reducible to $L_2$ that means that there is a Turing machine $M_1$ operating in polynomial time such that given as input $x$ it outputs $R(x)$, and $x \in L_1$ if and only if $R(x) \in L_2$. If $L_2$ is reducible to $L_3$ that means that there is a Turing machine $M_2$ operating in polynomial time such that given as input $y$ it outputs $S(y)$, and $y \in L_2$ if and only if $S(y) \in L_3$. 

If we constructed a Turing machine $M_3$ by combining $M_1$ and $M_2$ we would have a Turing machine that given as input $x$ it outputs $S(R(x))$, and $x \in L_1$ if and only if $S(R(x)) \in L_3$. We know $M_3$ operates in polynomial time because it first runs $M_1$ (in polynomial time) to produce $R(x)$ (whose length is polynomial in $\vert x \vert$), and then runs $M_2$ on $R(x)$ (also in polynomial time).

Therefore, if $L_1$ is reducible to $L_2$ and $L_2$ is reducible to $L_3$ then $L_1$ is reducible to $L_3$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 3.22 {#exercise-322}






Let $L_i$ be all the languages in the complexity class other than $L$ and $L'$. Since $L$ is complete, we know that all other languages in the complexity class (which are the set of all $L_i$ and $L'$) reduce to $L$. We are given that $L$ reduces to $L'$ and so by the transitive property shown in [exercise 3.21](#exercise-321) we know that all $L_i$ reduce to $L'$. Since we've shown that $L_i$ and $L$ (which are all the other languages in the complexity class) reduce to $L'$ we know that $L'$ is complete.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 3.23 {#exercise-323}






In section 3.2.3 the authors introduce SAT in terms of a Boolean formula. There the satisfiability problem is to determine, given Boolean formula $\phi$, whether it is satisfiable by any set of possible inputs, i.e. whether the output is ever 1. 

The problem is **NP** since evaluation of a Boolean formula is done in polynomial time which linearly scales with the number of operations in the Boolean formula. Therefore, if we had an input that resulted in an output of 1, it could be confirmed that the formula is satisfiable in polynomial time. 

So now we need to show that CSAT reduces to SAT. If CSAT is reducible to SAT that means that there is a Turing machine $M$ operating in polynomial time such that given as input a circuit $c$ it outputs $\phi(c)$, and $c \in$ CSAT if and only if $\phi(c) \in$ SAT, i.e. we need to show that we can represent a circuit as a Boolean formula that is satisfiable if and only if the circuit is satisfiable. 

For individual logic gates, we can represent their output in terms of their input using the Boolean formula shown below. 

<img width="1206" height="698" alt="image" src="https://github.com/user-attachments/assets/d91db449-90dc-4c7a-9f54-23eb915cf8ab" />

For each of these gates, the output equals 1 if and only if the Boolean formula equals 1. For example the AND gate only outputs 1 if and only if $a ∧ b = 1$. 

We can make a circuit with more than one logic gate and similarly write a Boolean formula that is satisfiable if and only if the circuit is satisfiable. 

<img width="1106" height="502" alt="image" src="https://github.com/user-attachments/assets/ded6f2c0-1d2a-4cdc-bc59-3c6164a582ce" />

Here the output of the circuit is 1 if and only if $(a ∧ b) ∧ (c ∧ d)  = 1$. 

It is possible to create an algorithm that constructs $\phi(c)$ (the Boolean formula) in polynomial time which scales linearly with the number of logic gates (the Tseytin transformation is an example). Therefore, there exists a Turing machine operating in polynomial time such that given as input a circuit $c$ it outputs $\phi(c)$, and $c \in$ CSAT if and only if $\phi(c) \in$ SAT. Thus, CSAT reduces to SAT. Since CSAT is **NP**-complete, SAT must also be **NP**-complete. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 3.24 {#exercise-324}

In this exercise we are asked to show that 2SAT can be solved in polynomial time. [Papadimitriou](http://103.203.175.90:81/fdScript/RootOfEBooks/E%20Book%20collection%20-%202023%20-%20E/CSE%20ITAIDSML/Computational%20Complexity%20-%20Papadimitriou.pdf) discusses kSAT, where $k \geq 1$, in section 9.2. I found it useful to look at figure 9-1 before starting the exercise, to confirm that I understood what these graphs look like, but not to read the section until after I had spent some time working on the exercise independently, since it contains the answer. 




(1) We are first asked to construct graphs $G(\phi)$ with directed edges in the following way: the vertices of $G$ correspond to variables $x_j$ and their negations $¬x_j$ in $\phi$. There is a directed edge $(\alpha, \beta)$ in $G$ if and only if the clause $(¬\alpha ∨ \beta)$ or the clause $(\beta ∨ ¬\alpha)$ is present in $\phi$. I constructed a few examples below.

<img width="2044" height="1572" alt="image" src="https://github.com/user-attachments/assets/34c33afe-6948-464e-9c95-266778ec0a4a" />

For $\phi$ to be true, each clause (the OR of two literals) needs to be true. Therefore at least one of the literals in each clause must be true. Looking at how the graphs are constructed, we see that up to two edges are created from each clause. The edges start at the negation of one of the literals and end at the other literal from the clause. Let's say that $\phi$ is true, if the negation of one of the literals is true (which means the literal itself is false) then that implies that the other literal must be true. 

Reading the graphs, if there is a path $v_1, v_2, v_3, \cdots, v_{n-1}, v_n$, by following the directed edges one can say that for $\phi =$ true, if $v_1$ is true, then $v_2$ is also true; if $v_2$ is true, then $v_3$ is also true;...if $v_{n-1}$ is true, then $v_n$ is also true. Therefore, if there is a path going from $x$ to $¬x$ and $¬x$ to $x$ we would end up saying if $x$ is true, then $¬x$ is true and if $¬x$ is true then $x$ is true. This forms a contradiction and therefore the function is not satisfiable. This is enough to complete part 1 of the exercise, but I am going to walk through the example graphs in more detail because I found it useful for understanding how these graphs work. 

For example a, we can read the graph as saying for $\phi =$ true, if $x_1$ is true, then $x_1$ is also true and for $\phi =$ true, if $¬x_1$ is true, then $¬x_1$ is also true. These statements are always true. Looking at the graph, you can see that the edges point back to the vertex from which they originated and therefore cannot contribute to paths from $x$ to $¬x$ or from $¬x$ to $x$. 

We can read the graph in example b as saying for $\phi=$ true, if $¬x_1$  is true, then $x_1$ is also true.  However, if $¬x_1$ is true, then $x_1$ must be false, since $¬x_1$ is the negation of $x_1$. The graph implication therefore conflicts with this assumption, meaning the assumption $¬x_1$ is true cannot hold. As a result, we conclude that $¬x_1$ must be false and $x_1$ must be true. In other words, this case does not make the formula unsatisfiable, it simply forces $x_1$ to take the value “true.” Example c works similarly to example b, but the roles are reversed. If $x_1$ is true, then $¬x_1$ must also be true according to the graph. But $¬x_1$  being true means $x_1$ is false, which conflicts with our starting assumption. Therefore $x_1$ must be false, and $¬x_1$ must be true. Again, this is not an unsatisfiable case; the graph simply forces $x_1$ to be false. For both of these examples there is only one path going between the literal and its negation. 

Example d differs from b and c in that here, both $x_1$ and $¬x_1$ are simultaneously forced to be true due to implications in both directions. This is a genuine contradiction, meaning the formula is unsatisfiable. This example has paths going from $x_1$ to $¬x_1$ and $¬x_1$ to $x_1$. 

Examples e-h show graphs with more than one literal/negation pairs. The way of reading the graphs is the same as the one literal/negation case, e.g. for example e the graph can be read for $\phi =$ true, if $¬x_1$ is true, then $x_2$ is also true and for $\phi =$ true, if $¬x_2$ is true, then $x_1$ is also true. All these examples are satisfiable and none of them have paths going from $x$ to $¬x$ and $¬x$ to $x$.

Examples i and j are graphs of not satisfiable functions. Here we run into the same contradiction as we saw in example d where we find that $x_1$ must be true and $¬x_1$ must be true. There are paths going from $x_1$ to $¬x_1$ and $¬x_1$ to $x_1$. This trend holds for all 2SAT functions. Due to the structure of the implication graph, if there are paths from $x$ to $¬x$ and from $¬x$ to $x$ for some $x$, the function is not satisfiable. 

(2) For this part we are asked to show that, given a directed graph $G$ containing $n$ vertices, it is possible to determine whether two vertices $v_1$ and $v_2$ are connected in polynomial time. We can use the path function from in [exercise 3.19](#exercise-319) with a few minor modifications to do this check. We have already demonstrated that this function is $O(n)$, the modifications will not change this and so the function can be used to determine whether the two vertices are connected in polynomial time.

The following function written in pseudocode determines whether there is a path between vertex v1 and vertex v2. 

```
path(v1, v2, G):
  S = [v1]
  M = [v1]
  while S is not empty:
    let v = the first element of S
    add all vertices that v is directed to and are not in M to S
    add all vertices that v is directed to and are not in M to M
    remove v from S
  if v2 is in M:
    return yes
  else:
    return no

```

(3) Now we are asked to find an efficient algorithm to solve 2SAT. For this, per part 1 of this exercise, we just need to determine that for all (i,j) combinations there is not both a path from vi to vj and from vj to vi. If this is the case, $G$ is satisfiable, otherwise it is not satisfiable. From part 2 of this exercise, we know we can do a single vi to vj path check in $O(n)$; therefore, we can do this check for every (i,j) combinations in $O(n^3)$, which means the algorithm operates in polynomial time. Therefore, there is an efficient algorithm to solve 2SAT.

Here is pseudocode to solve 2SAT.

```
2SAT(G):
  V = a list of all vertices in G
  for vi in V:
    for vj in V:
      if path(vi, vj, G) and path(vj, vi, G):
        return no
  return yes

```

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.25 {#exercise-325}






**PSPACE** is the set of all decision problems that can be solved by a Turing machine using a polynomial amount of space. A Turing machine has $l$ internal states, an $m$ letter alphabet, and uses space $p(n)$, so the machine can exist in at most $lm^{p(n)}$ different states. If a Turing machine is to avoid infinite loops then it must halt before revisiting a state, therefore it will halt after at most $lm^{p(n)}$ operation steps. Decision problems are in **EXP** if they are in TIME($2^{n^k}$), per [Papadimitriou](http://103.203.175.90:81/fdScript/RootOfEBooks/E%20Book%20collection%20-%202023%20-%20E/CSE%20ITAIDSML/Computational%20Complexity%20-%20Papadimitriou.pdf) chapter 20. Therefore, if $lm^{p(n)}$ is in $O(2^{n^k})$ for some $k$ then **PSPACE** $\subseteq$ **EXP**. 

In order for $lm^{p(n)}$ to be in $O(2^{n^k})$ the following must be true for some $k$ and all $n>n_0$ for some $n_0$.

$$\begin{aligned}
lm^{p(n)} & \leq 2^{n^k} \\
\log_m(lm^{p(n)}) & \leq \log_m(2^{n^k}) & \text{take $log_m$ of both sides}\\
\log_m(l) + p(n) & \leq \frac{\log_2(2^{n^k})}{\log_2(m)} & \text{change of base} \\
\log_m(l) + p(n) & \leq \frac{n^k}{\log_2(m)} \\
p(n) & \leq \frac{n^k}{\log_2(m)} - \log_m(l)
\end{aligned}$$

For $k$ larger than the degree of $p(n)$, there will be a sufficiently large $n_0$ such that $p(n) \leq \frac{n^k}{\log_2(m)} - \log_m(l)$ for all $n>n_0$, therefore $lm^{p(n)}$ is in $O(2^{n^k})$ and so **PSPACE** $\subseteq$ **EXP**.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.26 {#exercise-326}






A Turing machine has $l$ internal states, an $m$ letter alphabet, and uses space $q(n)$ (which, in this case, is a logarithmic function), so the machine can exist in at most $lm^{q(n)}$ different states. If a Turing machine is to avoid infinite loops, then it must halt before revisiting a state, therefore it will halt after at most $lm^{q(n)}$ operation steps. **P** decision problems halt after a polynomial number of operation steps. So, if $lm^{q(n)}$ is a polynomial function, then **L** $\subseteq$ **P**. 

Let's let $q(n) = \log_k(n)$ for some $k$. Then

$$\begin{aligned}
lm^{q(n)} &= lm^{\log_k(n)} \\
&= lm^{\frac{\log_m(n)}{\log_m(k)}} & \text{change of base} \\
&= l\left(m^{\log_m(n)}\right)^{\frac{1}{\log_m(k)}} \\
&= ln^{\frac{1}{\log_m(k)}}
\end{aligned}$$

This function is a polynomial with degree $\frac{1}{\log_m(k)}$. Therefore, **L** $\subseteq$ **P**. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 3.27 {#exercise-327}

In this exercise we are to prove that the given algorithm approximates the vertex cover for a graph $G$ within a factor of two of being a minimal vertex cover. Per [Wikipedia](https://en.wikipedia.org/wiki/Vertex_cover), in graph theory, a vertex cover of a graph is a set of vertices that includes at least one endpoint of every edge of the graph.




Let's first look at two extreme examples of possible graphs and the minimum vertex cover for those graphs. 
<img width="1298" height="430" alt="image" src="https://github.com/user-attachments/assets/b455fc97-4a2c-4cd7-b410-05d1457e6e23" />

Then let's look at the worst-case scenario when executing the given algorithm for those graphs. Here for each step an edge is chosen (and marked green) then every incident edge on the two vertices that define the selected edge are removed - you can consider both the green edges and the dashed edges as removed. The green vertices comprise the returned vertex cover. 
<img width="1298" height="424" alt="image" src="https://github.com/user-attachments/assets/d135b402-1a1c-49f5-be37-c664fc86fde6" />

In both cases, the algorithm is off by a factor of two for the number of vertices selected for the vertex cover compared to the minimum vertex cover. 

Let's think a little bit more about what is happening. For each step, the algorithm chooses an edge. Let's let $E_C$ be a list of the edges chosen. By construction, the algorithm removes all edges incident to the endpoints of a chosen edge before selecting the next one. Therefore, no two edges of $E_C$ share a vertex and so the length of $VC$ will be equal to the length of $2E_C$. Since no two edges in $E_C$ share a vertex, we also know that the minimum vertex cover, $VC_{min}$, must include at least one vertex from each edge in $E_C$. Therefore, the length of $VC_{min}$ is at least as large as the length of $E_C$. Thus,

$$\begin{aligned}
\vert VC \vert = 2 \vert E_C \vert \leq 2 \vert VC_{min} \vert 
\end{aligned}$$

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 3.28 {#exercise-328}

For this exercise we are asked to show the arbitrariness of the constant in the definition of BPP. [Papadimitriou](http://103.203.175.90:81/fdScript/RootOfEBooks/E%20Book%20collection%20-%202023%20-%20E/CSE%20ITAIDSML/Computational%20Complexity%20-%20Papadimitriou.pdf) discusses Randomized Complexity classes, of which BPP is one, in section 11.2. 




Per [Papadimitriou](http://103.203.175.90:81/fdScript/RootOfEBooks/E%20Book%20collection%20-%202023%20-%20E/CSE%20ITAIDSML/Computational%20Complexity%20-%20Papadimitriou.pdf) page 254,

>If we have a randomized algorithm with probability of false negatives at most $1 - \epsilon$, for some $\epsilon < \frac{1}{2}$, then we could transform it into one with probability at most $\frac{1}{2}$ by repeating the algorithm k times. "Repeating" in the Turing machine domain means that from each leaf of the nondeterministic computation tree we "hang" another tree identical to the original one. And so on for k repetitions. At the final leaves we report "yes" if and only if at least one computation leading to this leaf has reported "yes". The probability of a false negative answer is now at most $(1 - \epsilon)^k$. By taking $k = \lceil -\frac{1}{\log(1-\epsilon)}\rceil$ we make sure that this probability is at least $\frac{1}{2}$.

We can do something similar for our Turing machine $M$, where we build a new Turing machine $M'$ by repeating the algorithm of $M$ $m$ times such that $\frac{1}{4} \geq (1 - k)^m$. Solving for $m$ we get $m=\lceil\frac{-2}{\log(1-k)}\rceil$. Therefore, since we can build a probabilistic Turing machine $M'$ such that $x \in L$ then $M'$ accepts $x$ with probability at least $3/4$, and if $x \notin L$, then $M'$ rejects $x$ with probability at least $3/4$, then $L \in$ **BPP**.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.29 {#exercise-329}






In the table below, the first two columns are the same as Figure 3.15 in the textbook. The third column is the output of a Fredkin gate when the input is the one listed in the second column. As can be seen, the first and third column are the same. Therefore, applying two consecutive Fredkin gates gives the same output as the inputs.

| Gate 1 Inputs <br> a &nbsp;&nbsp;&nbsp;&nbsp; b &nbsp;&nbsp;&nbsp;&nbsp; c | Gate 1 Outputs/<br>Gate 2 Inputs <br> a' &nbsp;&nbsp;&nbsp;&nbsp; b' &nbsp;&nbsp;&nbsp;&nbsp; c'| Gate 2 Outputs <br> a'' &nbsp;&nbsp;&nbsp;&nbsp; b'' &nbsp;&nbsp;&nbsp;&nbsp; c''|
|:-------------------------------------------------------:|:-------------------------------------------------------:|:-------------------------------------------------------:|
| 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 | 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 | 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 |
| 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 | 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 | 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 |
| 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 | 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 | 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 |
| 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 | 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 | 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 |
| 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 | 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 | 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 0 |
| 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 | 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 | 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 &nbsp;&nbsp;&nbsp;&nbsp; 1 |
| 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 | 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 | 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 0 |
| 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 | 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 | 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 &nbsp;&nbsp;&nbsp;&nbsp; 1 |

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Exercise 3.30 {#exercise-330}






Below are the billiard ball trajectories for all inputs listed in Figure 3.15. The trajectories match the table outputs. Therefore, the billiard ball computer computes the Fredkin gate.

<img width="854" height="916" alt="image" src="https://github.com/user-attachments/assets/2b5f9c9b-0ce5-47ba-82e5-b0b2dac11918" />

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.31 {#exercise-331}






This is the circuit that I came up with. It uses Fredkin gates to compute $x\oplus y$ and $c=a∧b$, then uses CNOT gates to add the results to another register, and lastely uses Fredkin gates for uncomputation to get rid of garbage bits. The outputs are highlighted yellow.

<img width="1798" height="960" alt="image" src="https://github.com/user-attachments/assets/ff004586-6df6-4e80-869d-994b6002727d" />

Here is the same circuit drawn as a quantum circuit diagram. 

<img width="1198" height="792" alt="image" src="https://github.com/user-attachments/assets/71ffad18-f885-4e51-8fa8-2b86dcb52814" />


| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Exercise 3.32 {#exercise-332}






To simulate a Toffoli gate, what we ultimately want to do is flip c when a ∧ b = 1, a Boolean formula to represent this is $𝑐′=(¬𝑐∧(𝑎∧𝑏)) ∨ (𝑐∧¬(𝑎∧𝑏))=c \oplus (𝑎∧𝑏)$. Here is a reversible circuit that I came up with that uses Fredkin gates to simulate a Toffoli gate. 

<img width="1922" height="986" alt="image" src="https://github.com/user-attachments/assets/f46f2925-3617-4c0e-915f-6559a5b6d954" />

Here is the same circuit drawn as a quantum circuit diagram.

<img width="1330" height="790" alt="image" src="https://github.com/user-attachments/assets/3338627a-133a-4dde-834f-b901e096b801" />


So, we see that we can successfully simulate a Toffoli gate using Fredkin gates. However, it is unclear if this circuit represents the least number of Fredkin gates needed to simulate a Toffoli gate.  

If I didn't worry about getting rid of garbage bits, I was able to create circuits with four Fredkin gates that simulated a Toffoli gate; here is an example of one of them below. I used three gates to get $𝑐′=c \oplus (𝑎∧𝑏)$ and then another gate to restore $b$. 

<img width="1760" height="704" alt="image" src="https://github.com/user-attachments/assets/c7be8c77-4da5-45e4-a80e-b406c7380a3a" />

Here is the same circuit drawn as a quantum circuit diagram.

<img width="1326" height="670" alt="image" src="https://github.com/user-attachments/assets/cc4ba2da-5d91-40ea-8212-633377a72752" />


It is somewhat unclear to me what the authors mean when they ask us to simulate a Toffoli gate. Do they want the outputs $(a', b', c')$ to be on the same wires as the inputs $(a,b,c)$? Do they want all the garbage bits to be uncomputed? I couldn't find a way to do both of these things simultaneously. Did they want us to only use Fredkin gates and make the circuit reversible? I was also unable to find a way to do this. 

I'm tempted to make some argument related to the Boolean formula $𝑐′=c \oplus (𝑎∧𝑏)$, but am not confident that it is accurate. If I were to make such an argument it would go something like this: we know that $\oplus$ requires two gates and AND reqires one gate, which means to compute $c'=c \oplus (𝑎∧𝑏)$ we need at least 3 Fredkin gates. If ancilla bits are used, uncomputation will need to be done (if we don't want any garbage bits left over) which will require up to 3 more Fredkin gates. Therefore, the minimum number of Fredkin gates needed to simulate a Toffoli gate is 3-6, depending on uncomputation requirements. Also, this task may be impossible to do if the request is to make a reversible gate with only Fredkin gates that simulate a Toffoli gate. 

Now we are asked to simulate a Fredkin gate with Toffoli gates. For the Fredkin gate, we want to swap a and b when c = 1. So, we want $a' = (¬c ∧ a) \oplus (c ∧ b)$ and $b' = (¬c ∧ b) \oplus (c ∧ a)$. The following circuit generate those outputs using three gates.

<img width="1362" height="342" alt="image" src="https://github.com/user-attachments/assets/8943a33e-1a51-4e1f-9d68-362bd1237b85" />

After the first gate, the top wire becomes $a \oplus (b ∧ c)$. 

After the second gate the second wire becomes:

$$\begin{aligned}
b \oplus ((a \oplus (b ∧ c)) ∧ c) & = b \oplus (a ∧ c) \oplus (b ∧ c) \\
& = (a ∧ c) \oplus (b ∧ ¬c)
\end{aligned}$$

After the third gate, the top wire becomes:

$$\begin{aligned}
(a \oplus b ∧ c) \oplus (((a ∧ c) \oplus (b ∧ ¬c)) ∧ c) &= (a \oplus b ∧ c) \oplus ((a ∧ c) ∧ c) \oplus ((b ∧ ¬c) ∧ c)) \\
&= a \oplus (b ∧ c) \oplus (a ∧ c) \\
&= (b ∧ c) \oplus (a ∧ ¬c)
\end{aligned}$$

As with the first half of the exercise, creating a circuit made of Toffoli gates that simulates a Fredkin gate doesn't necessarily prove that three is the smallest number of gates needed. However, by looking at the results of adding the first and second gate to the circuit, it is obvious that a third gate is needed. To prove this more rigorously, one could create all the possible 1 and 2 gate circuits with these three inputs to demonstrate that none of them simulate a Fredkin gate. For the sake of moving on with this book, I will not do that here. Therefore, three is the smallest number of Toffoli gates that can be used to simulate a Fredkin gate.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




## Chapter Problems

### Problem 3.1 {#problem-31}

For this problem we are asked to show that a Minsky machine can compute all Turing computable functions and sketch a proof that any function which can be computed on a Minsky machine can also be computed on a Turing machine. [Minsky](https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf)'s book has a detailed discussion on this topic in chapter 10 and 11. What I put for my answer for part 1 is only a summary. For part 2, I'm not entirely sure what the authors are looking for.




(1) In order to show that a Minsky machine can compute all Turing computable functions, we need to demonstrate that for any Turing machine $T$ we can construct a Minsky machine $M_T$ which is equivalent to $T$. [Minsky](https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf) section 10.1 goes over the arithmetization of Turing machines, which shows how to represent the state of a Turing machine as a set of four integers. Then section 11.2 discusses how to store those four integers in the register of a Minsky machine and simulate the Turing machine by constructing the appropriate block of program for each state of the Turing machine. This demonstrates that a Minsky machine can be constructed for any Turning machine and so Minsky machines can compute all Turing computable functions. 

(2) To show that anything computed on a Minsky machine can also be computed on a Turing machine, one would need to demonstrate that you can store the Minsky register data on the Turing tape, that you can do the two main operations of a Minsky machine on a Turing machine (namely incrementing and decrementing register values), and that you can create Turing program lines that mimic the operation of the Minsky program. We know that this is all possible because the procedure for the Minsky machine operation is precisely described and any procedure which can be precisely described can be programmed to be performed by a Turing machine.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Problem 3.2 {#problem-32}

For this problem we are asked to prove that for any computable function $f(\cdot)$ there is a vector game which when started with the vector $(n, 0, \cdots, 0)$ reaches $(f(n), 0, \cdots, 0)$. As a hint, we are asked to show that a vector game in $k+2$ dimensions can simulate a Minsky machine containing $k$ registers. This vector game is discussed by Conway in [Unpredictable Iterations](https://gwern.net/doc/cs/computable/1972-conway.pdf), which also contains the solution to this problem.




Let's first try to simulate the following Minsky machine with the vector game:

<img width="786" height="450" alt="image" src="https://github.com/user-attachments/assets/c054e186-7f92-427d-9741-ff300f8066d2" />

For this machine, lets start with $r_1 = x$ and $r_2 = y$. As the program runs, it increments $r_2$ while decrementing $r_1$ until $r_1=0$ and $r_2 = x+y$, at which point it halts. 

We could create a vector game to simulate this Minsky machine with the following vectors: $(x, y)$ as our starting vector and $(-1, +1)$ as the only vector in our list of vectors. After the vector game completes, we would have $(0, x+y)$. 

Now let's think about what would happen if we added more orders to the Minsky machine. 

<img width="814" height="944" alt="image" src="https://github.com/user-attachments/assets/65487c1a-b6ec-4b77-863d-5a682efa649a" />

This new set of orders includes operations on a new register $r_3$, which is decremented while $r_1$ is incremented. Let say that the starting value of $r_3 = z$. So now, when the program starts the register values are $(x, y, z)$ and when it completes the values are $(z, x+y, 0)$. If we tried to use the same methodology as we used for the previous Minsky machine to create a vector game, our starting vector would be $(x, y, z)$ and our vector list would be:

$$\begin{aligned}
(-1, 1, 0) \\
(1, 0, -1) \\
\end{aligned}$$

With these vectors, the first part of the program runs as expected $(x, y, z) \rightarrow (0, x+y, z)$, then the next step is calculated as desired $(0, x+y, z) \rightarrow (1, x+y, z-1)$. But after that we start running into problems, since the first vector in the vector list starts being used again. Therefore, we need to find a way to track which which order needs to be preformed next. 

In order to track orders, two additional dimensions need to be added to our vectors. Now, our starting vector is $(x, y, z, 0, 3)$ and our vector list is as follows. 

$$\begin{aligned}
(0, 0, 0, 1, -1) \\
(-1, 0, 0, -4, 3) \\
(0, 0, 0, -4, 2) \\
(0, 1, 0, -3, 4) \\
(0, 0, -1, -2, 1) \\
(0, 0, 0, -2, 0) \\
(1, 0, 0, -1, 2) \\
\end{aligned}$$

The vector list starts with $(0, 0, 0, 1, -1)$, which transfers positive numbers from $r_5$ to $r_4$, and the rest of the vectors are generated from each order in the Minsky machine $(\text{operation on }r_1, \text{operation on }r_2, \text{operation on }r_3, -m, n\text{ or }p)$, which are listed from largest to smallest $m$. 

Using this methodology any Minsky machine can be simulated using a vector game. Therefore, for any computable function $f(\cdot)$ there is a vector game which when started with the vector $(n, 0, \cdots, 0)$ reaches $(f(n), 0, \cdots, 0)$. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Problem 3.3 {#problem-33}

For this problem we are asked to prove that for any computable function $f(.)$ there is a Fractran program which when started with $2^n$ reaches $2^{f(n)}$ without going through any intermediate powers of 2. There is an example in the book on page 169 of using Fractran, it is also discussed by Conway in [FRACTRAN: A SIMPLE UNIVERSAL PROGRAMMING LANGUAGE FOR ARITHMETIC](https://www.cs.unc.edu/~stotts/COMP210-s23/madMath/Conway87.pdf).




A Fractran program is defined by a list of positive rational numbers $q_1, \cdots, q_n$. It acts on a positive integer $m$ by replacing it by $q_i m$, where $i$ is the least number such that $q_i m$ is an integer. If there is ever a time when there is no $i$ such that $q_i m$ is an integer, then execution stops. 

So, thinking about this, we start with $2^n$. After the first step, we have $q_i 2^n$. We know that this is an integer. Let's say $q_i = \frac{a_i}{b_i}$, in its reduced form, therefore our new integer is $q_1 2^n = \frac{a_1 2^n}{b_1}$. Since it is an integer, we know that $b_2 = 2^{x_1}$ for some $x_1$. Therefore, our new number can be written as $q_1 2^n = \frac{a_1 2^n}{2^x_1} = a_1 2^{n-x}$. Now, for our next step we have $q_2 a_1 2^{n-x_1} = \frac{a_1 a_2 2^{n-x_1}}{b_2}$, which means that $b_2 = a_1 2^{x_2}$. Following this trend we see that $b_i = a_{i-1} 2^{x_i}$ for each step and so we can use the $a_i$ values and the ordering of the fractions in the list to create an algorithm. 

The authors give us a hint for this problem to use the previous problem. So, let's think about whether we can represent the two Minsky orders as lists of fractions. 

<img width="1526" height="434" alt="image" src="https://github.com/user-attachments/assets/dcb5b50f-388d-4791-9134-7328fbcb2046" />

Here, $n$ can be considered a registry in the Minsky machine. To increment $n$ by $x$ you can use a list that consists of one term: $2^x$. To decrement $n$ by $x$, when $n>=x$, you can also use a list that consists of one term: $\frac{1}{2^x}$. 

However, as we saw with the previous problem, just being able to increment and decrement a register is not enough, we also need a way to identify what Minsky order to use. For this, we will need two more registries. To create these registries, we can use two additional prime numbers, for now let's use 3 and 5. Now we can start with our starting value $2^n 3^0 5^0$ and increment or decrement the registries each step by using the fraction $\frac{2^{x_+}3^{y_+}5^{z_+}}{2^{x_-}3^{y_-}5^{z_-}}$. Where $x_+$ gives the amount incremented and $x_-$ is the amount decremented for register $r_1$, the same can be said for registers $r_2$ for $y_{\pm}$ and $r_3$ for $z_{\pm}$.

Going back to the example I made in the previous problem, 

<img width="814" height="944" alt="image" src="https://github.com/user-attachments/assets/65487c1a-b6ec-4b77-863d-5a682efa649a" />

We can now represent our starting vector and our vector list as fractions, as shown below

$$\begin{aligned}
\text{starting vector and fraction:} & (x, y, z, 0, 3) &\Rightarrow  \frac{2^x 3^y 5^z 11^3}{1} \\
\text{list of vectors and fractions:} & (0, 0, 0, 1, -1) &\Rightarrow \frac{7}{11}\\
& (-1, 0, 0, -4, 3) &\Rightarrow \frac{11^3}{2 \times 7^{4}}\\
& (0, 0, 0, -4, 2) &\Rightarrow \frac{11^2}{7^4}\\
& (0, 1, 0, -3, 4) &\Rightarrow \frac{3 \times 11^4}{7^3}\\
& (0, 0, -1, -2, 1) &\Rightarrow \frac{11}{5 \times 7^2}\\
& (0, 0, 0, -2, 0) &\Rightarrow \frac{1}{7^2}\\
& (1, 0, 0, -1, 2) &\Rightarrow \frac{11^2}{7}\\
\end{aligned}$$

And so our list of fractions that reproduces the Mindsky machine is $\frac{7}{11}, \frac{11^3}{2 \times 7^{4}}, \frac{11^2}{7^4}, \frac{3 \times 11^4}{7^3}, \frac{11}{5 \times 7^2}, \frac{1}{7^2}, \frac{11^2}{7}$, with a starting value of $\frac{2^x 3^y 5^z 11^3}{1}$. Using this methodology any Minsky machine can be simulated using a Fractran program. Therefore, for any computable function $f(\cdot)$ there is a Fractran program which when started with the vector $2^n$ reaches $2^{f(n)}$. This, unfortunatly, is not what we are asked to prove, which is that for any computable function $f(.)$ there is a Fractran program which when started with $2^n$ reaches $2^{f(n)}$ without going through any intermediate powers of 2.

Let's say that the program did go through an intermediate power of 2. What would that mean? It would mean that all the other "registries" were set to zero at some point in the program. Looking at our fractions and thinking about how they are generated from a Minsky machine, one notes that each order of the Minsky machine corresponds with decrementing the second to last register and incrementing the last register. If the last two registers are zero, the program will halt. 

However, this brings up an interesting question: how did the program start with only a power of 2 and all the other registries are empty? In the example that I gave, the program started with a non-zero value for the last registry to get it to run. The explanations that I've come up with to answer this question is that either the last two registries are factored out when discussing the input and output, or the vector game and Fractran programs are allowed to loop when given an input with only one non-zero entry. 

If the last two registries are factored out, then the proof is easy. There is no intermediate power of 2 because the program halts when it reaches a power of 2.

If the last two registries are not factored out, then an additional fraction will need to be added to the end of our program list to set the starting values for those last two registries. When the program completes calculating $f(n)$, the last two registries will be zero again (which will be when the program first reaches a power of 2). The program will then loop with $f(n)$ as the input; but regardless there will not be an intermediate power of 2 between the input of $2^n$ and the output of $2^f(n)$. 

Therefore, for any computable function $f(.)$ there is a Fractran program which when started with $2^n$ reaches $2^{f(n)}$ without going through any intermediate powers of 2.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Problem 3.4 {#problem-34}

For this problem, we are asked to prove that there is no algorithm to decide whether a Fractran program ever reaches 1. This is just another form of the halting problem.




Suppose, for contradiction, that there is a Fractran program $M_F$ that, given the code of another Fractran program $F$, tells us whether the run of $F$ from a fixed starting number ever reaches 1. Using $M_F$, we can design a new program $T_F$ with the following behavior: if $F$ ever reaches 1, then $T_F$ will reach 0 (and never 1); if $F$ never reaches 1, then $T_F$ will reach 1.

Now consider running $T_F$ with its own program as input. <br>
•	If $T_F$ never reaches 1, then by definition it should reach 1 — a contradiction. <br>
•	If $T_F$ does reach 1, then by definition it should not reach 1 — also a contradiction. <br>

Therefore such an $M_F$ cannot exist.

For an alternative (and likely better) proof, you can see [Minsky](https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf) section 8.3.2. I went there to check my answer and saw that he took a different approach. Though, I decided to leave my answer here as well. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Problem 3.5 {#problem-35}
 




In section 3.2.5, the authors talk about reversible and irreversible gates and comment on how a gate is irreversible if given the output of the gate, the input is not uniquely determined. From the book, we know that the NOT gate and identity gate are reversible and all the gates with fewer outputs than inputs are irreversible (AND, OR, XOR). 

So, let's think about how we could change these irreversible two-bit gates to make them reversible. One way would be to add an output that give us the value of one of the inputs, as shown below. 

<img width="658" height="250" alt="image" src="https://github.com/user-attachments/assets/e2f23aea-6752-4ee7-b88c-24f4a1055f7c" />

Let's think about what the truth tables would look for this gate for different logic operations.

| a | b | a AND b | b |
|:-:|:-:|:-------:|:-:|
| 0 | 0 | 0       | 0 |
| 0 | 1 | 0       | 1 |
| 1 | 0 | 0       | 0 |
| 1 | 1 | 1       | 1 |

Looking at the table we see that adding the addition output b to the AND gate, does not make the gate reversible since there are several inputs that correspond to the same output. 

| a | b | a OR b  | b |
|:-:|:-:|:-------:|:-:|
| 0 | 0 | 0       | 0 |
| 0 | 1 | 1       | 1 |
| 1 | 0 | 1       | 0 |
| 1 | 1 | 1       | 1 |

Looking at the table we see that adding the addition output b to the OR gate, does not make the gate reversible since there are several inputs that correspond to the same output. 

| a | b | a XOR b | b |
|:-:|:-:|:-------:|:-:|
| 0 | 0 | 0       | 0 |
| 0 | 1 | 1       | 1 |
| 1 | 0 | 1       | 0 |
| 1 | 1 | 0       | 1 |

Looking at the table we see that adding the addition output b to the XOR gate, makes the gate reversible since there is only one input that correspond to a given output. 

Therefore, with this modification to the standard 2-bit logic gates, only the XOR gate becomes reversible. So now the question is, what can we make with XOR, NOT, and ancilla bits?

First let's look at these gates and fixed value ancilla bits in algebraic normal form: <br>
Ancilla bit: 1 or 0 <br>
NOT: $1 \oplus a$ <br>
XOR: $a \oplus b$ <br>
AND: $ab$ <br>
OR: $a \oplus b \oplus ab$ <br>
Tofolli (on target c): $c \oplus ab$ <br>

Looking at these forms, we see that the ancilla bits have an algebraic degree of 0, the NOT and XOR gates have an algebraic degree of 1, and the AND, OR, and Toffolli gates has algebraic degree of 2. Using NOT gates, XOR gates, and ancilla bits, we are unable to create a gate with the algebraic degree of 2, the highest algebraic degree possible is 1. 

Therefore, there exist Boolean functions (e.g., AND, OR) that cannot be computed with only 1- and 2-bit reversible gates and ancillas. In particular, the Toffoli gate cannot be simulated from such gates (even with ancillas).

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |





### Problem 3.6 {#problem-36}





If a Hamiltonian cycle for $G$ is returned and there are $n$ vertices, that means there are $n$ edges, each with a length of 1, and so the length of the path is $n$. If there is not a Hamiltonian cycle, that means that there will be edges selected for the path that are not in $G$, let's say that the number is $m \geq 1$. Therefore, the path length is 

$$\begin{aligned}
(n-m)(1) + (m)(\lceil r \rceil \vert V \vert + 1) &= n + m(\lceil r \rceil \vert V \vert + 1 - 1) \\
&= n + m\lceil r \rceil \vert V \vert \\
\end{aligned}$$

So, now what we want to show is $\lceil r \rceil \vert V \vert < n + m\lceil r \rceil \vert V \vert$. We know that $n \geq 3$ because there need to be at least 3 cities in the TSP. We also know that, by definition, $m \geq 1$ when the Hamiltonian cycle is not returned. Therefore, we know $3 + \lceil r \rceil \vert V \vert \leq n + m\lceil r \rceil \vert V \vert$. Since $\lceil r \rceil \vert V \vert < 3 + \lceil r \rceil \vert V \vert$, then $\lceil r \rceil \vert V \vert < n + m\lceil r \rceil \vert V \vert$. 

Thus, when the approximation algorithm is applied to this instance of TSP then it returns a Hamiltonian cycle for $G$ if one exists and otherwise returns a tour of length more than $\lceil r \rceil \vert V \vert$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Problem 3.7 {#problem-37}






(1) In order for a Turing machine to be reversible we would need to be able to map any given configuration to at most one possible predecessor configuration. One way to do this is to take a normal single tape Turing machine and add a second log tape, which records the configuration at each step of the computation. 

(2) This would require space $s'(x) = O(s(x)t(x))$ and time $t'(x) = O(s(x)t(x))$.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |




### Problem 3.8 {#problem-38}






Monotone circuits (with only AND/OR gates, no negation) are discussed in section 14.4 of [Papadimitriou](http://103.203.175.90:81/fdScript/RootOfEBooks/E%20Book%20collection%20-%202023%20-%20E/CSE%20ITAIDSML/Computational%20Complexity%20-%20Papadimitriou.pdf). There, Razborov’s theorem is introduced: There is a constant $c$ such that for large enough $n$ all monotone circuits for $CLIQUE_{n,k}$ with $k = \sqrt[4]{n}$ have size at least $2^{c\sqrt[8]{n}}$. Therefore, monotone circuits for $CLIQUE_{n,k}$ with $k = \sqrt[4]{n}$ require a super-polynomial number of Boolean gates to compute. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |





### Problem 3.9 {#problem-39}

The further reading section cites three papers related to this problem: <br>
-Bennett: [TIME/SPACE TRADE-OFFS FOR REVERSIBLE COMPUTATION](https://mathweb.ucsd.edu/~sbuss/CourseWeb/Math268_2013W/Bennett_Tradeoffs.pdf) <br>
-Li and Vitany: [Reversibility and Adiabatic Computation: Trading Time and Space for Energy](https://homepages.cwi.nl/~paulv/papers/thermo.pdf) <br>
-Li, Tromp, and Vitany: [Reversible Simulation of Irreversible Computation ](https://homepages.cwi.nl/~paulv/papers/pebbles.pdf) <br>




It is known that QSAT is PSPACE-complete for a normal Turing machine. PSPACE is the set of all decision problems that can be solved by a Turing machine using a polynomial amount of space. So, what we need to show is that a decision problem that can be solved by a Turing machine using a polynomial amount of space can also be solved on a reversible Turing machine using a polynomial amount of space. 

Bennett's paper shows that Turing machines using time $T$ and space $S$ can be simulated by reversible ones using time $O(T^{1+\epsilon})$ for any $\epsilon > 0$ and space $O(S \log T)$. For a machine that is space-bounded by a polynomial $S$, its time $T$ can be at most $2^{O(S)}$ since there are only that many distinct configurations, so

$$\begin{aligned}
\log T &\leq \log 2^{O(S)} \\
&= O(S)
\end{aligned}$$

Therefore an upper bound on the space used for the reversible Turing machine is given by

$$\begin{aligned}
S\log T &=S O(S) \\
&=O(S^2) 
\end{aligned}$$

which is still a polynomial amount of space. So, the reversible Turing machine simulation uses polynomial space. Conversely, any reversible Turing machine using polynomial space can trivially be simulated by an ordinary Turing machine using polynomial space. Thus, the class of languages decidable by reversible Turing machines in polynomial space equals PSPACE.

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |



### Problem 3.10 {#problem-310}





Suppose there exists a reversible circuit $C$ of size polynomial in the input length $l$ that on input of $(m,n,0^k)$ outputs $(p_mp_n,  g(m,n))$, where $l$ (the bit-length of the inputs $m,n$) is $O(\log n)$ and $k$ (the number of ancilla bits) is $O(\log\log n)$. Then we need to show that this implies factoring (of the number $p_mp_n$) can be done in polynomial time in $l$ (hence in **P**).

Since $C$ is reversible, we know that given $(p_mp_n, g(m,n))$ we would be able to run $C$ in reverse ($C^{-1}$) to extract $(m,n)$ in polynomial time. Then $m$ and $n$ could be used to find $p_m$ and $p_n$ in polynomial time. This would allow factoring in polynomial time. 

We know that it is possible to find $p_m$ and $p_n$ given $m$ and $n$ in polynomial time because $C$ already maps $(m,n) \rightarrow (p_mp_n, g(m,n))$  in polynomial time and so $C$ can be used to find $p_m$ by inputting $n=1$ and then dividing the output $p_mp_n$ by two (and something similar can be done for $n$). 

The problem is, we don’t necessarily know $g(m,n)$ when using $C^{-1}$ for factoring. However, fortunately, we know that $g(m,n)$ is short, with $k$ in $O(\log\log n)$, and so the number of possible combinations is small $2^k = 2^{O(\log\log n)} = (\log n)^{O(1)} = (l)^{O(1)}$. Therefore, it is possible to try all candidate $g(m,n)$ values in time polynomial in $l$, since each run of $C^{-1}$ is $poly(l)$ and it will be run up to $(l)^{O(1)}$ times. Then we can check whether the candidate $g(m,n)$ value was correct by computing $C$ with the $(m,n)$ output from $C^{-1}$ and confirming it matches $p_m p_n$.

Therefore, if circuit $C$ exists, factoring can be done in polynomial time and hence is in **P**. 

| [Back to top](#top) | [Solutions Index](https://adj59-dev.github.io/solutions-index/) | [Blog Archive](https://adj59-dev.github.io/archive.html) |


