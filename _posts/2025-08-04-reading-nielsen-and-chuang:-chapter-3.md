# Reading Nielsen and Chuang: Chapter 3

I just finished reading Chapter 3 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. 

I went to the History and further reading section of this chapter after reading the first couple of questions, since it was apparent that I was missing important background knowledge. Here are some of the resources that I found useful. 

*Computation: Finite and Infinite Machines* by Minsky: https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf <br>
*Computational Complexity* by Papadimitriou: http://103.203.175.90:81/fdScript/RootOfEBooks/E%20Book%20collection%20-%202023%20-%20E/CSE%20ITAIDSML/Computational%20Complexity%20-%20Papadimitriou.pdf


The Conway articles are here: <br>
Unpredictable Iterations: https://gwern.net/doc/cs/computable/1972-conway.pdf <br>
Fractran: https://www.cs.unc.edu/~stotts/COMP210-s23/madMath/Conway87.pdf

I used visual paradigm to make the logic diagrams: <br>
https://online.visual-paradigm.com/diagrams/features/logic-diagram-software/

Big O notation in this book different than what I remember learning previously. Complexity classes very important in demonstrating whether quantum computers have an advantage over classical computers -- as of the writing of this book, this has not been demonstrated. 

## Navigation

* [Models for computation](#models-for-computation)
* [The analysis of computational problems](#the-analysis-of-computational-problems)
* [Chapter Problems](#chapter-problems)




## Models for computation

### Models for computation - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Elements of a Turing machine         | section 3.1.1             | (1) a program <br> (2) a finite state control (acts like a stripped-down microprocessor) <br> (3) a tape (acts like memeory) <br> (4) a read-write tape-head (points to the position on the tape which is currently readable or writable) |
| Internal states of a Turing machine  | section 3.1.1             | The finite state control consists of a finite set of internal states, $q_1, \cdots, q_m$, the starting state $q_s$, and the halting state $q_h$. At the beginning of computation, the state is $q_s$. As computation executes the internal states change. If computation finishes the machine ends up in $q_h$. |
| Properties of the tape               | section 3.1.1             | The tape is a on-dimensional object of infinite length which consists of tape squares numbered $0, 1, 2, \cdots$ that each contain a symbol from some alphabet $\Gamma$. |
| Alphabet used in the book            | section 3.1.1             | $0, 1, b \text{ (blank)}, \triangleright \text{ (left edge of tape)}$       |
| Program for a Turing machine         | section 3.1.1             | Finite list of program lines in the form $\braket{q, x, q', x', s}$, where $q$ and $q'$ are internal states, $x$ and $x'$ are symbols from $\Gamma$, and $s$ is $-1$, $1$, or $0$ representing movement of the tape-head left, right, or stand still, respectively. On each machine cycle the Turing machine seaches the program lines in order for $\braket{q,x,\cdot,\cdot, \cdot}$ where $q$ is the current internal state and $x$ is the current symbol being read on the tape. If a program line is found, then that line is executed. If not, the internal state is set to $q_h$ and the machine halts. When executing a program line, the internal state is set to $q'$, the symbol $x$ on the tape is changed to $x'$, and the tape head moves based on $s$, unless asked to move farther left than the leftmost square, in which case it doesn't move. |
| Church-Turing thesis                 | section 3.1.1             | Any function that can be effectively computed by an algorithm can be computed by a Turing machine. This thesis is important because it provided a good definition for computability. | 
| The halting problem                  | section 3.1.1             | A famous problem in computer science that asks whether it's possible to create a universal algorithm that can determine if any given program will halt or run forever. Alan Turing proved that such an algorithm cannot exist. |
| Circuit model                        | section 3.1.2             | Models computation in terms of wires and gates.                                                        |
| Logic gates                          | section 3.1.2             | <img width="458" height="250" alt="image" src="https://github.com/user-attachments/assets/b87e0e7c-cae9-4370-8459-2f8824bb1952" /> |
| Boolean function                     | section 3.1.2             | Takes $n$ input bits and outputs a single bit. <br> $f:\\{0,1\\}^n \rightarrow \\{0,1\\}$  |
| Universal circuit components         | section 3.1.2             | (1) wires, preserve the states of the bits <br> (2) ancilla bits prepared in standard states <br> (3) the FANOUT operation, which takes a single bit as input and ouputs two copies <br> (4) the CROSSOVER operation, which interchanges the values of two bits <br> (5) logic gates (AND, XOR, and NOT) |
| Circuit family                       | section 3.1.2             | A collection of circuits, $\\{C_n\\}$, indexed by a positive integer $n$.
| Uniform circuit family               | section 3.1.2             | Circuit families for which there exists a Turing machine that, upon input of $n$, can generate a description of $C_n$ (the information needed to build the circuit). | 



### Models for computation - Exercises
  
**Exercise 3.1** 

This question is about non-computable processes in Nature. The authors previously went into a more detailed discussion of the Church-Turing thesis in section 1.1.1. Interestingly, section 3.1.1 dropped the word "efficently" from the thesis and just focused on computability. Minsky chapter 5 discusses the idea of computability. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

To recognize that a process in Nature computes a function not computable by a Turing machine, one would need to demonstrate that no Turing machine can reproduce the same input-output behavior. This typically involves proving that the function the process computes is non-computable. According to Minsky (Chapter 5), *“any procedure which can be precisely described can be programmed to be performed by a computer"*. Therefore, if a physical process yields results that cannot be captured by any precisely describable algorithm, it would suggest that the process computes a non-Turing-computable function. 

</details>

**Exercise 3.2**

I found reading Minsky section 7.2 to be helpful in understanding what this question is asking us to do (and why it may be useful), which is to find a way of representing a given Turing machine's "state diagram" (the set of quintuples that represent its states, inputs, and outputs, i.e. what QCQI authors call the "program") as a unique number that can be used by a universal Turing machine to simulate that specific Turing machine. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

Let's say we have a program described by a finite list of program lines of the form $\braket{q, x, q', x', s}$ with a library consiting of $0, 1, b, \triangleright$, $-1$ for tape-head movement, internal states $q_1, \cdots, q_m$, the starting state $q_s$, and the halting state $q_h$, we can represent each symbol in the library and the different states as a non-negative integer as shown below

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

</details>


**Exercise 3.3**

Here we are to describe a Turing machine which takes a binary number as input and outputs the bits in reverse order. I found it useful to look at examples in Minsky (section 6.1) and use a multi-tape turing machine to create this solution, as recommended in the hint. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

We will setup the machine with two tapes, one that has the input binary number followed by blank squares and the other is all blank. The program is setup to read the binary input from the first tape and print the bits in reverse order on the second. 

The program is given as follows

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

</details>


**Exercise 3.4**

For this exercise we are asked to describe a Turing machine which adds two binary numbers modulo 2. I also used two tapes for this machine. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

We will use two tapes for this machine. The first will contain the binary values and the second will start out blank. The program will first transfer the values for the first number to the second tape, then do a bit-wise XOR on the last digit of the two numbers, replacing the last value on the second tape with the results, then it will zero out the rest of the values on the second tape, so that the value on the second tape is the answer. 

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

</details>


**Exercise 3.5**

In Box 3.2 the authors introduce the halting problem for a Turing machine with an input equal to its Turing number. For this exercise, we are asked to think about the halting problem for a Turing machine with no inputs. The blank tape halting problem is discussed by Minsky in section 8.3.3 of his book, if you'd like another resource for this exercise. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

Let's say that we can create an algorithm to determine whether a Turing machine halts when the input to the machine is a blank tape. With this algorithm, we could take a machine $T$ with tape $t$ and make a new machine $M_T$ which is constructed from the description of $T$ with additional program lines. These additional lines will generate the output of $t$ on a blank tape at the start of the computation, such that $M_T$ starting with a blank tape is the equivalent of $T$ starting with tape $t$. Using the algorithm mentioned above, we can determine whether $M_T$ halts when the input to the machine is a blank tape, this means that using the algorithm we can determine if $T$ halts starting with tape $t$. 

From Box 3.2, we know that there is no algorithm that can be used to determine if a Turing machine with Turing number $x$ halts upon input of $x$. But with our algorithm we can determine if $T$ halts when $t=x$. We have a contradiction; therefore it is not possible to create an algorithm to determine whether a Turing machine halts when the input to the machine is a blank tape.

</details>


**Exercise 3.6**

In this exercise we are asked to revisit the halting problem again, but this time the Turing machine is probabilistic. On page 127, the autors talk about creating a probabilistic Turing machine by adding a random component to the change in internal states with the execution of each program line. I am not confident in my solution to this exercise, as I don't have much experience with this area of theoretical computer science, but I'll put what I have below. Let me know if you have a better solution. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

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

Each time this algorithm is run, there is a probability $P_h$ of getting $0$ and a probability of $1-P_h$ of it looping forever. This contradicts our expectations of it halting with probability $P_h$. If $P_h$ was not strictly greater than $1/2$, but instead allowed to be equal to $1/2$ then we could have the situation where $P_h = 1-P_h$, and there would be no contradiction, but we're wanting to find a case where the probability of correctness is strictly greater than $1/2$. Putting this in terms of our halting function, we find that $h_p = 0$, but we know that $h_p = 1$. Therefore, there is a contradiction and so there is no probabilistic Turing machine which can output $h_p(x)$ with probability of correctness strictly greater than $1/2$ for all $x$. 

</details>


**Exercise 3.7**

This exercise asks if adding an oracle to a Turing machine resolves the halting problem. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

An oracle machine with access to a halting problem oracle for standard Turing machines can decide whether any given Turing machine halts. However, no oracle machine can solve its own halting problem, by a similar argument to the one that shows no Turing machine can decide its own halting behavior. 

</details>


**Exercise 3.8**

For this exercise we are to create an AND, NOT, and XOR gate using NAND gates. I find it useful to make logic tables that show the outputs for the different inputs to teh NAND gates. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

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

</details>



## The analysis of computational problems

### The analysis of computational problems - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Big O notation                       | section 3.2.1             | Describes the upper bounds behavior of a function. <br> $f(n)$ is $O(g(n))$ if $f(n) \leq cg(n)$ for some real positive constant $c$ and for all $n \geq n_0$ |
| Big Omega notation                   | section 3.2.1             | Describes the lower bounds on resources required. <br> $f(n)$ is $\Omega (g(n))$ if $f(n) \geq cg(n)$ for some real positive constant $c$ and for all $n \geq n_0$|
| Big Theta notation                   | section 3.2.1             | Can be used to describe a functions behavior when $f(n)$ behaves the same as $g(n)$ asymptotically, up to unimportant constat factors. <br> $f(n)$ is $\Theta (g(n))$ if it is both $O(g(n))$ and $\Omega (g(n))$ |
| Strong Church-Turing thesis          | section 3.2.2             | Any model of computation can be simulated on a probabilistic Turing machine with at most a polynomial increase in the number of elementary operations required |
| Easy vs hard to compute algorithms   | section 3.2.2             | A problem is regarded as easy, tractable, or feasible if an algorithm exists for solving the problem using polynomial resources. It is considered hart, intractable, or infeasible if it requires exponential (i.e. grows faster than polynomial) resources. |
| Decision problems                    | section 3.2.3             | Problems with yes or no answers.  |
| Language membership problem          | section 3.2.3             | Decision problems can be represented as language membership problems where the goal is to determine if a given input belongs to a specific language. |
| $\text{TIME}(f(n))$                  | section 3.2.3             | The set of all decision problems (languages) that can be decided by a Turing machine in time $O(f(n))$. |
| Complexity class **P**               | section 3.2.3             | The collection of all languages which are in TIME($n^k$) for some $k$, i.e. can be solved in polynomial time |
| Complexity class **NP**              | section 3.2.3             | The collection of all languages $L$ for which there is a Turing machine $M$ with the following properties: <br> (1) If $x \in L$ then there exists a witness string $w$ such that $M$ halts in the state $q_Y$ after a time polynomial in $\vert x \vert$ when the machine is stated in the state $x\text{-blank-}w$. <br> (2) If $x \not\in L$ then for all strings $w$ which attempt to play the role of a witness, the machine halts in state $q_N$ after a time polynomial in $\vert x \vert$ when $M$ is started in the state $x\text{-blank-}w$. |
| Complexity class **coNP**            | section 3.2.3             | The class of languages which have witnesses to 'no' instances. These languages are complements of the languages in **NP**. |
| Reduction                            | section 3.2.3             | A technique used to relate the difficulty of solving two different problems. It involves transforming one problem into another, such that a solution to the second problem can be used to solve the first. Language B is said to be reducible to language A if there exists a Turing machine operating in polynomial time such that given as input $x$ it outputs $R(x)$ where $x \in B$ if and only if $R(x) \in A$.|
| Complete                             | section 3.2.3             | A problem in a complexity class is complete if its language $L$ is the most difficult to decide in the sense that every other language in the complexity class can be reduced to $L$. |
| Circuit Satisfiability problem (CSAT)| section 3.2.3             | A **NP**-complete problem that is often used as a benchmark for testing the complexity of other problems. |
| Complexity class **NPI**             | section 3.2.3             | **NP** intermediate, which are problems neither solvable with polynomial resources nor are **NP**-complete. There are no problems known to be in **NPI**, but there are several problems that are considered likely candidates. This is the class of problems for which quantum computation is expected to be useful. | 
| Complexity class **PSPACE**          | section 3.2.4             | A space-bound complexity class of decision problems that can be solved on a Turing machine using a polynomial number of working bits. Both **P** and **NP** are subsets of **PSPACE**. It is not known whether **P** = **PSPACE**, but if it does then quantum computers offer no advantage over classical computers.|
| Landauer's principle                 | section 3.2.5             | In order to erase information, it is necessary to dissipate energy. <br> The amount of energy dissipated into the environment is at least $k_BT \ln2$ for each bit of information erased. The entropy of the environment increases by at least $k_B \ln2$ for each bit of information erased. Where $k_B$ is the Botzmann constant and $T$ is the temperature of the environment of the computer. Modern computers dissipate significantly more energy than this lower limit. If all computation was done reversibly, then Landauer's principle would imply no lower bound on the amount of energy dissipated. |
| Toffoli gate                         | section 3.2.5             | A reversible gate with three inputs $(a, b, c)$ and three outputs $(a, b, c \oplus ab)$ |
| Fredkin gate                         | section 3.2.5             | <img width="670" height="328" alt="image" src="https://github.com/user-attachments/assets/6d9e75ad-a594-4eb8-b779-05f190ef1b1b" /> | 



### The analysis of computational problems - Exercises

**Exercise 3.9**

For this exercise we are to prove that $f(n)$ is $O(g(n))$ if and only if $g(n)$ is $\Omega (f(n))$ and that $f(n)$ is $\Theta (g(n))$ if and only if $g(n)$ is $\Theta (f(n))$. We can do this using the details I listed in the notes above for these different notations.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

We know that $f(n)$ is $O(g(n))$ if $f(n) \leq cg(n)$ for some constant $c$ and for all $n \geq n_0$. We also know that $g(n)$ is $\Omega (f(n))$ if $g(n) \geq c'f(n)$ for some constant $c'$ and for all $n \geq n_0'$. If we set $c = \frac{1}{c'}$ and $n_0 = n_0'$, then we can see that the two inequalities are identical. Therefore, $f(n)$ is $O(g(n))$ if and only if $g(n)$ is $\Omega (f(n))$.

We know that $f(n)$ is $\Theta (g(n))$ when $f(n)$ behaves the same as $g(n)$ asymptotically. When this is the case, we can also say that $g(n)$ behaves the same as $f(n)$ asymptotically and so $g(n)$ is $\Theta (f(n))$. 

</details>


**Exercise 3.10**

For this exercise we are to show that a polynomial of degree $k$ is $O(n^l)$ for any $l \geq k$.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

To show that $g(n)$ is $O(n^l)$ we need to show that $g(n) \leq cn^l$ for some real positive constant $c$ and for all $n \geq n_0$ for some $n_0$. We know that $g(n) = \sum_{i=0}^k c_i n^i$. If we set $c=c_k$, then $c_k n^k + \sum_{i=0}^{k-1} c_i n^i \leq c_k n^l$. For sufficiently large $n$ the lower order terms on the left hand side become small compared to the $k\text{th}$ term and can be ignored, so we have $c_k n^k \leq c_k n^l$, which is always true. Therefore a polynomial of degree $k$ is $O(n^l)$ for any $l \geq k$.

</details>


**Exercise 3.11**

Show that log $n$ is $O(n^k)$ for any $k > 0$.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

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

</details>


**Exercise 3.12**

Show that $n^{\log n}$ is super-polynomial.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

We need to show that $n^k \leq c n^{\log n}$ for some real positive constant $c$, some $n_0$, and any $k$ for $n \geq n_0$.

$$\begin{aligned}
n^k & \leq cn^{\log n} \\
k & \leq \log_n (cn^{\log n}) & \text{take $log_n$ of both sides}\\
k & \leq \log_n (c) + \log_n(\log n) \\
k & \leq k + \log_n(\log n) & \text{set $\log_n (c) = k$ }
\end{aligned}$$ 

It can be seen that this inequality is true when $\log_n(\log n) \geq 0$, which will happen for all $n \geq 2$, since $\log$ is base $2$ when not specified as something else in this book. This shows that $n^k$ is $O(n^{\log n})$ for any $k$ and $n^{\log n}$ is never $O(n^k)$. 

</details>


**Exercise 3.13**

Show that $n^{\log n}$ is sub-exponential.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

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

</details>


**Exercise 3.14**

Suppose $e(n)$ is $O(f(n))$ and $g(n)$ is $O(h(n))$. Show that $e(n)g(n)$ is $O(f(n)h(n))$. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

Since $e(n)$ is $O(f(n))$ we know that $e(n) \leq cf(n)$ for some real positive constant $c$ and for all $n \geq n_0$. Also since $g(n)$ is $O(h(n))$ we know that $g(n) \leq dh(n)$ for some real positive constant $d$ and for all $n \geq n_1$. To show that $e(n)g(n)$ is $O(f(n)h(n))$, we need to show that $e(n)g(n) \leq b f(n)h(n)$ for some real positive constant $b$ and for all $n \geq n_2$. 

$$\begin{aligned}
e(n)g(n) \leq b f(n)h(n) \\
e(n)g(n) \leq cd f(n)h(n) & \text{let $b = cd$} \\
e(n)g(n) \leq (c f(n))(d h(n))
\end{aligned}$$ 

Since we know that $e(n) \leq cf(n)$ for $n \geq n_0$ and $g(n) \leq dh(n)$ for $n \geq n_1$ we know that the above inequality is true for $n \geq n_2$ where $n_2 = \max(n_0, n_1)$. 

</details>


**Exercise 3.15**

In this exercise we are to show that the lower bounds of a compare-and-swap sorting algorithm is $O(n \log n)$. You will need to use Stirling's approximation to do this. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

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

For sufficiently large $n$ the left-hand side is dominated by the $n\log(n)$ term and so if $c<1$ the above inequalitiy will be true for $n > n_0$ for some value of $n_0$. Therefore $\Omega (n\log(n))$ compare-and-swap operations are required to sort all possible initial orderings into the correct order.

</details>


**Exercise 3.16**

This exercise asks us to find an example of a hard to compute function. For this you first need to find the number of possible Boolean functions that can be created with $n$ inputs. Then find the number of circuit configurations that can be created with $m$ logic gates. Finally find the minimum number of gates needed to create all possible Boolean functions with $n$ inputs. Note: the online errata page (https://michaelnielsen.org/qcqi/errata/errata/errata.html) says that $2^n/\log(n)$ should be $2^n/n$. 

This problem is challenging, and I ended up referencing the following resources to find and understand the solution. I did change some steps in my solution compared to what is in these resources. These changes did not impact the final result - it just made more sense to me to do it that way.  <br>
https://math.stackexchange.com/questions/505393/how-many-semantically-different-boolean-functions-are-there-for-n-boolean-variab <br>
https://www.cs.umd.edu/~jkatz/complexity/f05/lecture4.pdf <br>
https://deeplearning.cs.cmu.edu/S25/document/readings/booleancircuits_shannonproof.pdf <br>
https://cs.stackexchange.com/questions/82271/how-to-show-that-hard-to-compute-boolean-functions-exist 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

We know a Boolean function takes $n$ input bits and outputs a single bit, $f:\\{0,1\\}^n \rightarrow \\{0,1\\}$. With $n$ bits there are $2^n$ possible distinct input combinations. With each input combination there are two possible outcomes, meaning that there are $2^{2^n}$ possible functions. Below is an example of all 16 possible functions for the case of $n=2$.

|$n_1$|$n_2$|$f_1$|$f_2$|$f_3$|$f_4$|$f_5$|$f_6$|$f_7$|$f_8$|$f_9$|$f_{10}$|$f_{11}$|$f_{12}$|$f_{13}$|$f_{14}$|$f_{15}$|$f_{16}$|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|--------|--------|--------|--------|--------|--------|--------|
|**0**|**0**| 0   | 1   | 0   | 0   | 0   | 1   | 1   | 1   | 0   | 0      | 0      | 1      | 1      | 1      | 0      | 1      |
|**1**|**0**| 0   | 0   | 1   | 0   | 0   | 1   | 0   | 0   | 1   | 1      | 0      | 1      | 1      | 0      | 1      | 1      |
|**0**|**1**| 0   | 0   | 0   | 1   | 0   | 0   | 1   | 0   | 1   | 0      | 1      | 1      | 0      | 1      | 1      | 1      |
|**1**|**1**| 0   | 0   | 0   | 0   | 1   | 0   | 0   | 1   | 0   | 1      | 1      | 0      | 1      | 1      | 1      | 1      |


Let's say that we have a collection of circuits, each created with $m$ logic gates. We'd like to know what the maximum number of distinct circuits we can create with the $n$ inputs and $m \geq n-1$ logic gates with two-inputs (you need at least $n-1$ two-input gates to take $n$ inputs and reduce it to one output). For each of the gates there are $16$ possible logic functions, as we showed in the table above. Each of the two gate inputs can come from either the inputs $n$ or the output from one of the other $m-1$ gates, resulting in $(n + m - 1)^2$ possible combination of inputs, and so there are $16(n+m-1)^2$ ways to create each gate, except for the output gate which is specifically defined. This results in $m(16(n+m-1)^2)^{m-1}$ possible circuit configurations. However, this calculation is overcounting due to their being multiple permutations of the gates. This estimation can be tightened by dividing by $m!$ which gives us $\frac{m\left( 16(n+m-1)^2 \right)^{m-1}}{m!}$ possible circuit configurations. 

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

</details>


**Exercise 3.17**

For this exercise we are to prove that a polynomial-time algorithm for finding the factors of a number $m$ exist if and only if the factoring decision problem is **P**. The factoring decision problem is as follows: given a composite interger $m$ and $l<m$, does $m$ have a non-trival factor less than $l$? 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

Suppose we have a polynomial-time algorithm that can find a non-trivial factor of a composite number $m$. Then we could solve the factoring decision problem in polynomial time as follows:

1.	Use the factor-finding algorithm to obtain all factors $n_i$ of $m$. 
2.	For each $n_i$ check whether $n_i<l$, which is a simple comparison and can be done in polynomial time.
3.	Report yes if at least one $n_i$ is less than $l$ and no otherwise

Thus, if finding non-trivial factors is in **P**, then the factoring decision problem is also in **P**.

Conversely, suppose we can solve the factoring decision problem in polynomial time for any input $(m, l)$. Then we can find the smallest non-trivial factor $s$ of $m$ by performing a binary search over the range $2$ to $m-1$ using the decision problem as an oracle. Each step of the binary search involves asking whether a factor exists below a certain bound $l$, which takes polynomial time. 

Once we find $s$ we can calculate $r=\frac{m}{s}$ and recursively apply the same method to $r$. We repeat this process until all factors are found. Since binary search requires only $O(\log m)$ calls, the entire procedure runs in polynomial time. Therefore, if the factoring decision problem is in **P**, then finding the factors is also in **P**.

</details>

**Exercise 3.18**

For this exercise we are to prove that if **coNP** $\neq$ **NP** then **P** $\neq$ **NP**. I found it useful to read more about complement complexity classes in Papadimitriou section 7.1 before solving this exercise. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

**NP** and **coNP** are complements of each other. In Papadimitriou (section 7.1) a complement complexity class $C$ is defined as the class $\\{ \bar{L} : L \in C \\}$, where $\bar{L}$ is the complement of language $L$. If C is a deterministic complexity class, then $C=coC$. This is because any deterministic Turing machine deciding $L$ can be converted to decide $\bar{L}$ within the same time or space bound by reversing the roles of "yes" and "no". Since **P** is a deterministic complexity class, **P** $=$ **coP**. If **P** = **NP**, that would mean that **NP** = **P** = **co(P)** = **co(NP)**. Therefore if **coNP** $\neq$ **NP**, it must mean that **P** $\neq$ **NP**.

</details>


**Exercise 3.19**

For this exercise we are asked to show that we can determine whether there is a path between two specified vertices in a graph using $O(n)$ operations where $n$ is the number of vertices. Then we are asked to show that it is possible to decide whether a graph is connected in $O(n^2)$ operations. 

Papadimitriou section 1.1 discuses graph reachability and answers this question. I was not sure how to approach this exercise before reading this section, since I had not worked with these kind of graph problems before, but the general approach is that at each step of an algorithm you can access a vertex, see what edges and other vertices are connected to that vertex, update variables or perform other actions as desired, and then proceed on to the next step. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

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
Here the agorithm starts by initializing two lists, S and M, and adding the starting vertex s to both lists. The following steps are repeated until list S is empty: (1) finds all the vertices connected to the first element in list S that are not in list M, (2) adds these vertices to S and M, (3) remove the first element in list S. The algorithm then checks if f is in M and returns yes if it is and no if it isn't. It can be seen that this function is $O(n)$ since v is only able to represent each vertex one time and so the while loop only loops, at most, $n$ times.

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

</details>


**Exercise 3.20**

In this exercise we are asked to prove Euler's theorem, which is: a connected graph contains an Euler cycle if and only if every vertex has an even number of edges incident upon it. An Euler cycle is an ordering of the edges of a graph $G$ so that every edge in the graph is visited exactly once. Then we are also asked to give a constructive procedure for finding an Euler cycle. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

For a Euler cycle to exist, each vertex needs at least two incident edges, one to go away from the vertex and one to return to the vertex. A simple example is shown in Example 1 where there are three vertices, all connected. An Euler cycle can be identified as $1,2,3,1$.


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

</details>


**Exercise 3.21**

Here we are to demonstrate the transitive property of reduction using the defition of reducible given on page 145.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

If $L_1$ is reducible to $L_2$ that means that there is a Turing machine $M_1$ operating in polynomial time such that given as input $x$ it outputs $R(x)$, and $x \in L_1$ if and only if $R(x) \in L_2$. If $L_2$ is reducible to $L_3$ that means that there is a Turing machine $M_2$ operating in polynomial time such that given as input $y$ it outputs $S(y)$, and $y \in L_2$ if and only if $S(y) \in L_3$. 

If we constructed a Turing machine $M_3$ by combining $M_1$ and $M_2$ we would have a Turing machine that given as input $x$ it outputs $S(R(x))$, and $x \in L_1$ if and only if $S(R(x)) \in L_3$. We know $M_3$ operates in polynomial time because it first runs $M_1$ (in polynomial time) to produce $R(x)$ (whose length is polynomial in $\vert x \vert$), and then runs $M_2$ on $R(x)$ (also in polynomial time).

Therefore, if $L_1$ is reducible to $L_2$ and $L_2$ is reducible to $L_3$ then $L_1$ is reducible to $L_3$. 

</details>

**Exercise 3.22**

For this exercise we are to show that if $L$ is complete for a complexity class, and $L'$ is another language in the complexity class such that $L$ reduces to $L'$, then $L'$ is also complete for the complexity class. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

Let $L_i$ be all the languages in the complexity class other than $L$ and $L'$. Since $L$ is complete, we know that all other languages in the complexity class (which are the set of all $L_i$ and $L'$) reduce to $L$. We are given that $L$ reduces to $L'$ and so by the transitive property shown in exercise 3.21 we know that all $L_i$ reduce to $L'$. Since we've shown that $L_i$ and $L$ (which are all the other languages in the complexity class) reduce to $L'$ we know that $L'$ is complete.

</details>

**Exercise 3.23**

For this exercise we are asked to show that SAT is **NP**-complete. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

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

</details>

**Exercise 3.24**

In this exercise we are asked to show that 2SAT can be solved in polynomial time. Papadimitriou discusses kSAT, where $k \geq 1$, in section 9.2. I found it useful to look at figure 9-1 before starting the exercise, to confirm that I understood what these graphs look like, but not to read the section until after I had spent some time working on the exercise independently, since it contains the answer. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

(1) We are first asked to construct graphs $G(\phi)$ with directed edges in the following way: the vertices of $G$ correspond to variables $x_j$ and their negations $¬x_j$ in $\phi$. There is a directed edge $(\alpha, \beta)$ in $G$ if and only if the clause $(¬\alpha ∨ \beta)$ or the clause $(\beta ∨ ¬\alpha)$ is present in $\phi$. I constructed a few examples below.

<img width="2044" height="1572" alt="image" src="https://github.com/user-attachments/assets/34c33afe-6948-464e-9c95-266778ec0a4a" />

For $\phi$ to be true, each clause (the OR of two literals) needs to be true. Therefore at least one of the literals in each clause must be true. Looking at how the graphs are constructed, we see that up to two edges are created from each clause. The edges start at the negation of one of the literals and end at the other literal from the clause. Let's say that $\phi$ is true, if the negation of one of the literals is true (which means the literal itself is false) then that implies that the other literal must be true. 

Reading the graphs, if there is a path $v_1, v_2, v_3, \cdots, v_{n-1}, v_n$, by following the directed edges one can say that for $\phi =$ true, if $v_1$ is true, then $v_2$ is also true; if $v_2$ is true, then $v_3$ is also true;...if $v_{n-1}$ is true, then $v_n$ is also true. Therefore, if there is a path going from $x$ to $¬x$ and $¬x$ to $x$ we would end up saying if $x$ is true, then $¬x$ is true and if $¬x$ is true then $x$ is true. This forms a contradiction and therefore the function is not satisfiable. This is enough to complete part 1 of the exercise, but I am going to walk through the example graphs in more detail because I found it useful for understanding how these graphs work. 

For example a, we can read the graph as saying for $\phi =$ true, if $x_1$ is true, then $x_1$ is also true and for $\phi =$ true, if $¬x_1$ is true, then $¬x_1$ is also true. These statements are always true. Looking at the graph, you can see that the edges point back to the vertex from which they originated and therefore cannot contribute to paths from $x$ to $¬x$ or from $¬x$ to $x$. 

We can read the graph in example b as saying for $\phi=$ true, if $¬x_1$  is true, then $x_1$ is also true.  However, if $¬x_1$ is true, then $x_1$ must be false, since $¬x_1$ is the negation of $x_1$. The graph implication therefore conflicts with this assumption, meaning the assumption $¬x_1$ is true cannot hold. As a result, we conclude that $¬x_1$ must be false and $x_1$ must be true. In other words, this case does not make the formula unsatisfiable, it simply forces $x_1$ to take the value “true.” Example c works similarly to example b, but the roles are reversed. If $x_1$ is true, then $¬x_1$ must also be true according to the graph. But $¬x_1$  being true means $x_1$ is false, which conflicts with our starting assumption. Therefore $x_1$ must be false, and $¬x_1$ must be true. Again, this is not an unsatisfiable case; the graph simply forces $x_1$ to be false. For both of these examples there is only one path going between the literal and its negation. 

Example d differs from b and c in that here, both $x_1$ and $¬x_1$ are simultaneously forced to be true due to implications in both directions. This is a genuine contradiction, meaning the formula is unsatisfiable. This example has paths going from $x_1$ to $¬x_1$ and $¬x_1$ to $x_1$. 

Examples e-h show graphs with more than one literal/negation pairs. The way of reading the graphs is the same as the one literal/negation case, e.g. for example e the graph can be read for $\phi =$ true, if $¬x_1$ is true, then $x_2$ is also true and for $\phi =$ true, if $¬x_2$ is true, then $x_1$ is also true. All these examples are satisfiable and none of them have paths going from $x$ to $¬x$ and $¬x$ to $x$.

Examples i and j are graphs of not satisfiable functions. Here we run into the same contradiction as we saw in example d where we find that $x_1$ must be true and $¬x_1$ must be true. There are paths going from $x_1$ to $¬x_1$ and $¬x_1$ to $x_1$. This trend holds for all 2SAT functions. Due to the structure of the implication graph, if there are paths from $x$ to $¬x$ and from $¬x$ to $x$ for some $x$, the function is not satisfiable. 

(2) For this part we are asked to show that, given a directed graph $G$ containing $n$ vertices, it is possible to determine whether two vertices $v_1$ and $v_2$ are connected in polynomial time. We can use the path function from in exercise 3.19 with a few minor modifications to do this check. We have already demonstrated that this function is $O(n)$, the modifications will not change this and so the function can be used to determine whether the two vertices are connected in polynomial time.

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

</details>


**Exercise 2.25**

For this exercise we are to prove that **PSPACE** $\subseteq$ **EXP**. The authors give a very generous hint for this exercise. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

**PSPACE** is the set of all decision problems that can be solved by a Turing machine using a polynomial amount of space. A Turing machine has $l$ internal states, an $m$ letter alphabet, and uses space $p(n)$, so the machine can exist in at most $lm^{p(n)}$ different states. If a Turing machine is to avoid infinite loops then it must halt before revisiting a state, therefore it will halt after at most $lm^{p(n)}$ operation steps. Decision problems are in **EXP** if they are in TIME($2^{n^k}$), per Papadimitriou chapter 20. Therefore, if $lm^{p(n)}$ is in $O(2^{n^k})$ for some $k$ then **PSPACE** $\subseteq$ **EXP**. 

In order for $lm^{p(n)}$ to be in $O(2^{n^k})$ the following must be true for some $k$ and all $n>n_0$ for some $n_0$.

$$\begin{aligned}
lm^{p(n)} & \leq 2^{n^k} \\
\log_m(lm^{p(n)}) & \leq \log_m(2^{n^k}) & \text{take $log_m$ of both sides}\\
\log_m(l) + p(n) & \leq \frac{\log_2(2^{n^k})}{\log_2(m)} & \text{change of base} \\
\log_m(l) + p(n) & \leq \frac{n^k}{\log_2(m)} \\
p(n) & \leq \frac{n^k}{\log_2(m)} - \log_m(l)
\end{aligned}$$

For $k$ larger than the degree of $p(n)$, there will be a sufficiently large $n_0$ such that $p(n) \leq \frac{n^k}{\log_2(m)} - \log_m(l)$ for all $n>n_0$, therefore $lm^{p(n)}$ is in $O(2^{n^k})$ and so **PSPACE** $\subseteq$ **EXP**.

</details>


**Exercise 3.26**

For this exercise we are to show that **L** $\subseteq$ **P**.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

A Turing machine has $l$ internal states, an $m$ letter alphabet, and uses space $q(n)$ (which, in this case, is a logarithmic function), so the machine can exist in at most $lm^{q(n)}$ different states. If a Turing machine is to avoid infinite loops, then it must halt before revisiting a state, therefore it will halt after at most $lm^{q(n)}$ operation steps. **P** decision problems halt after a polynomial number of operation steps. So, if $lm^{q(n)}$ is a polynomial function, then **L** $\subseteq$ **P**. 

Let's let $q(n) = \log_k(n)$ for some $k$. Then

$$\begin{aligned}
lm^{q(n)} &= lm^{\log_k(n)} \\
&= lm^{\frac{\log_m(n)}{\log_m(k)}} & \text{change of base} \\
&= l\left(m^{\log_m(n)}\right)^{\frac{1}{\log_m(k)}} \\
&= ln^{\frac{1}{\log_m(k)}}
\end{aligned}$$

This function is a polynomial with degree $\frac{1}{\log_m(k)}$. Therefore, **L** $\subseteq$ **P**. 

</details>

**Exercise 3.27**

In this exercise we are to prove that the given algorithm approximates the vertex cover for a graph $G$ within a factor of two of being a minimal vertex cover. Per Wikipedia, in graph theory, a vertex cover of a graph is a set of vertices that includes at least one endpoint of every edge of the graph.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

Let's first look at two extreme examples of possible graphs and the minimum vertex cover for those graphs. 
<img width="1298" height="430" alt="image" src="https://github.com/user-attachments/assets/b455fc97-4a2c-4cd7-b410-05d1457e6e23" />

Then let's look at the worst-case scenario when executing the given algorithm for those graphs. Here for each step an edge is chosen (and marked green) then every incident edge on the two vertices that define the selected edge are removed - you can consider both the green edges and the dashed edges as removed. The green vertices comprise the returned vertex cover. 
<img width="1298" height="424" alt="image" src="https://github.com/user-attachments/assets/d135b402-1a1c-49f5-be37-c664fc86fde6" />

In both cases, the algorithm is off by a factor of two for the number of vertices selected for the vertex cover compared to the minimum vertex cover. 

Let's think a little bit more about what is happening. For each step, the algorithm chooses an edge. Let's let $E_C$ be a list of the edges chosen. By construction, the algorithm removes all edges incident to the endpoints of a chosen edge before selecting the next one. Therefore, no two edges of $E_C$ share a vertex and so the length of $VC$ will be equal to the length of $2E_C$. Since no two edges in $E_C$ share a vertex, we also know that the minimum vertex cover, $VC_{min}$, must include at least one vertex from each edge in $E_C$. Therefore, the length of $VC_{min}$ is at least as large as the length of $E_C$. Thus,

$$\begin{aligned}
\vert VC \vert = 2 \vert E_C \vert \leq 2 \vert VC_{min} \vert 
\end{aligned}$$

</details>

**Exercise 3.28**

For this exercise we are asked to show the arbitrariness of the constant in the definition of BPP. Papadimitriou discusses Randomized Complexity classes, of which BPP is one, in section 11.2. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

Per Papadimitriou page 254,

>If we have a randomized algorithm with probability of false negatives at most $1 - \epsilon$, for some $\epsilon < \frac{1}{2}$, then we could transform it into one with probability at most $\frac{1}{2}$ by repeating the algorithm k times. "Repeating" in the Turing machine domain means that from each leaf of the nondeterministic computation tree we "hang" another tree identical to the original one. And so on for k repetitions. At the final leaves we report "yes" if and only if at least one computation leading to this leaf has reported "yes". The probability of a false negative answer is now at most $(1 - \epsilon)^k$. By taking $k = \lceil -\frac{1}{\log(1-\epsilon)}\rceil$ we make sure that this probability is at least $\frac{1}{2}$.

We can do something similar for our Turing machine $M$, where we build a new Turing machine $M'$ by repeating the algorithm of $M$ $m$ times such that $\frac{1}{4} \geq (1 - k)^m$. Solving for $m$ we get $m=\lceil\frac{-2}{\log(1-k)}\rceil$. Therefore, since we can build a probabilistic Turing machine $M'$ such that $x \in L$ then $M'$ accepts $x$ with probability at least $3/4$, and if $x \notin L$, then $M'$ rejects $x$ with probability at least $3/4$, then $L \in$ **BPP**.

</details>


**Exercise 3.29**

Show that applying two consecutive Fredkin gates gives the same outputs as inputs.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

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

</details>

**Exercise 3.30**

Verify that the billiard ball computer in Figure 3.14 computes the Fredkin gate.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

Below are the billiard ball trajectories for all inputs listed in Figure 3.15. The trajectories match the table outputs. Therefore, the billiard ball computer computes the Fredkin gate.

<img width="854" height="916" alt="image" src="https://github.com/user-attachments/assets/2b5f9c9b-0ce5-47ba-82e5-b0b2dac11918" />

</details>


**Exercise 3.31**

In this exercise we are asked to construct a reversible half-adder circuit where the input is two bits $x$ and $y$, and the outputs are $(x,y,c,x\oplus y)$. Right before this exercise, the authors discuss how to do uncomputation; I followed these instructions for constructing this circuit. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

This is the circuit that I came up with. It uses Fredkin gates to compute $x\oplus y$ and $c=a∧b$, then uses CNOT gates to add the results to another register, and lastely uses Fredkin gates for uncomputation to get rid of garbage bits. The outputs are highlighted yellow.

<img width="1798" height="960" alt="image" src="https://github.com/user-attachments/assets/ff004586-6df6-4e80-869d-994b6002727d" />

Here is the same circuit drawn as a quantum circuit diagram. 

<img width="1198" height="792" alt="image" src="https://github.com/user-attachments/assets/71ffad18-f885-4e51-8fa8-2b86dcb52814" />




</details>

**Exercise 3.32**

In this exercise we are asked to find the smallest number of Fredkin gates needed to simulate a Toffoli gate and vice versa. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

To simulate a Toffoli gate, what we ultimately want to do is flip c when a ∧ b = 1, a Boolean formula to represent this is $𝑐′=(¬𝑐∧(𝑎∧𝑏)) ∨ (𝑐∧¬(𝑎∧𝑏))=c \oplus (𝑎∧𝑏)$. Here is a reversible circuit that I came up with that uses Fredkin gates to simulate a Toffoli gate. 

<img width="1922" height="986" alt="image" src="https://github.com/user-attachments/assets/f46f2925-3617-4c0e-915f-6559a5b6d954" />

Here is the same circuit drawn as a quantum circuit diagram.

<img width="1330" height="790" alt="image" src="https://github.com/user-attachments/assets/3338627a-133a-4dde-834f-b901e096b801" />


So, we see that we can successfully simulate a Toffoli gate using Fredkin gates. However, it is unclear if this circuit represents the least number of Fredkin gates needed to simulate a Toffoli gate.  

If I didn't worry about getting rid of garbage bits, I was able to create circuits with four Fredkin gates that simulated a Toffoli gate; here is an example of one of them below. I used three gates to get $𝑐′=c \oplus (𝑎∧𝑏)$ and then another gate to restore $b$. 

<img width="1760" height="704" alt="image" src="https://github.com/user-attachments/assets/c7be8c77-4da5-45e4-a80e-b406c7380a3a" />

Here is the same circuit drawn as a quantum circuit diagram.

<img width="1326" height="670" alt="image" src="https://github.com/user-attachments/assets/cc4ba2da-5d91-40ea-8212-633377a72752" />


It is somewhat unclear to me what the authors mean when they ask us to simulate a Toffoli gate. Do they want the outputs $(a', b', c')$ to be on the same wires as the inputs $(a,b,c)$? Do they want all the garbage bits to be uncomputed? I couldn't find a way to do both of these things simultaneously. 

I'm tempted to make some argument related to the Boolean formula $𝑐′=c \oplus (𝑎∧𝑏)$, but am not confident that it is accurate. If I were to make such an argument it would go something like this: we know that $\oplus$ requires two gates and AND reqires one gate, which means to compute $c'=c \oplus (𝑎∧𝑏)$ we need at least 3 Fredkin gates. If ancilla bits are used, uncomputation will need to be done (if we don't want any garbage bits left over) which will require up to 3 more Fredkin gates. Therefore, the minimum number of Fredkin gates needed to simulate a Toffoli gate is 3-6, depending on uncomputation requirements.

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

</details>


## Chapter Problems

**Problem 3.1**

For this problem we are asked to show that a Minsky machine is capable of computing all Turing computable functions and sketch a proof that any function which can be computed on a Minsky machine can also be computed on a Turing machine. 

(1) We need to demonstrate that for any Turning machine $T$ we can construct a Minsky machine $M_T$ which is equivlent to $T$. 

To do this, we need to represent the state of $T$ as numbers in the register of $M_T$. The content of the tape of $T$ can be stored as a set of three integers in register $r_1$, $r_2$, and $r_3$. Since the tape contains symbols, these symbols will need to be converted to integers using a table like the one below:

| Symbol           | Integer |
|------------------|---------|
| $0$              | $2$     |
| $1$              | $3$     |
| $b$              | $4$     |
| $\triangleright$ | $5$     |

The value currently under the tape head will be stored in $r_1$. The other values in the tape will be stored as two separate values; $r_2$ will contain an integer representing the entries to the left of the tape head and $r_3$ will contain an integer representing entries to the right of the tape head. We will use a similar methodology to the one used in exercise 3.2 to generate the intgers that will be stored in $r_2$ and $r_3$. If we let $t$ be a list of the interger representation of the tape, $r_1$, $r_2$, and $r_3$ are given as follows when the tape head is on $t_j$

$$\begin{aligned}
r_1 = t_j \\
r_2 = p_1^{t_{j-1}}p_2^{t_{j-2}}p_3^{t_{j-3}}\cdots p_{j-1}^{t_1} \\
r_3 = p_1^{t_{j+1}}p_2^{t_{j+2}}p_3^{t_{j+3}}\cdots p_{k}^{t_{j+k}}
\end{aligned}$$

Where $p_1, \cdots, p_{k}$ are unique prime numbers. Whever the tape head moves the following calculation is done. Since all of these functions can be calculated by incrementing or decrementing a value (as shown below), they can be done on a Minsky machine by storing the needed variables in other entries of the register and constructing the appropriate orders. 

```
\\for all these functions we will assume that all the inputs are positive integers

addition(x, y):
  sum = x
  term = y
  while term > 0:
    sum += 1
    term -= 1
  return sum

subtraction(x, y):
  difference = x
  term = y
  while term > 0:
    difference -= 1
    term -= 1
  return difference

division(x, y):
  quotient = 0
  remainder = x
  while remainder >= y:
    remainder = subtraction(remainder, y)
    quotient += 1
  return remainder, quotient

multiplication(x, y):
  product = 0
  multiplier = x
  while multiplier > 0
    product = addition(product, y)
    multiplier -= 1
  return product

power(x, y): 
  exponent = y
  result = x
  while exponent > 0:
    result = multiplication(result, x)
    exponent =- 1
  return result

findpower(r, p):
  t = 0
  remainder, quotient = division(r, p)
  while remainder == 0:
    t += 1
    remainder, quotient = division(quotient, p)
  return t

nextprime(x):
  test = x+1
  while

updateleft(r1, r2, movement):
  new_r2 = 1
  old_r2 = r2
  j = 2
  while old_r2 >= j:
    p = findpower(old_r2, j)
    old_r2 = division(old_r2, power(j,p))
    new_r2 = multiplication(new_r2, power(nextprime(j), p))
  

```



