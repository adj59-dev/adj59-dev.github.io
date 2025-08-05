# Reading Nielsen and Chuang: Chapter 3

I just finished reading Chapter 3 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. 

I went to the History and further reading section of this chapter after reading the first couple of questions, since it was apparent I was missing important background knowledge. Here are some of the resources that I found useful. 

*Computation: Finite and Infinite Machines* by Minsky: https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf

The Conway articles are here: <br>
Unpredictable Iterations: https://gwern.net/doc/cs/computable/1972-conway.pdf <br>
Fractran: https://www.cs.unc.edu/~stotts/COMP210-s23/madMath/Conway87.pdf

I used visual paradigm to make the logic diagrams: <br>
https://online.visual-paradigm.com/diagrams/features/logic-diagram-software/

Big O notation in this book different than what I remember learning previously.

## Navigation

* [Models for computation](#models-for-computation)
* [The analysis of computational problems](#the-analysis-of-computational-problems)
* [Perspectives on computer science](#perspectives-on-computer-science)




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
| Big O notation                       | section 3.2.1             | Describes the upper bounds behavior of a function. <br> $f(n)$ is $O(g(n))$ if $f(n) \leq cg(n)$ for some constant $c$ and for all $n \geq n_0$ |
| Big Omega notation                   | section 3.2.1             | Describes the lower bounds on resources required. <br> $f(n)$ is $\Omega (g(n))$ if $f(n) \geq cg(n)$ for some constant $c$ and for all $n \geq n_0$|
| Big Theta notation                   | section 3.2.1             | Can be used to describe a functions behavior when $f(n)$ behaves the same as $g(n)$ asymptotically, up to unimportant constat factors. <br> $f(n)$ is $\Theta (g(n))$ if it is both $O(g(n))$ and $\Omega (g(n))$ |


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

To show that $g(n)$ is $O(n^l)$ we need to show that $g(n) \leq cn^l$ for some constant $c$ and for all $n \geq n_0$ for some $n_0$. We know that $g(n) = \sum_{i=0}^k c_i n^i$. If we set $c=c_k$, then $c_k n^k + \sum_{i=0}^{k-1} c_i n^i \leq c_k n^l$. For sufficiently large $n$ the lower order terms on the left hand side become small compared to the $k\text{th}$ term and can be ignored, so we have $c_k n^k \leq c_k n^l$, which is always true. Therefore a polynomial of degree $k$ is $O(n^l)$ for any $l \geq k$.

</details>


**Exercise 3.11**

Show that log $n$ is $O(n^k)$ for any $k > 0$.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

To show that log $n$ is $O(n^k)$ for any $k > 0$ we need to show that the following is true for some $c$ and $n_0$ for all $n>n_0$

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

We need to show that $n^k \leq c n^{\log n}$ for some $c$, some $n_0$, and any $k$ for $n \geq n_0$.

$$\begin{aligned}
n^k & \leq cn^{\log n} \\
k & \leq \log_n (cn^{\log n}) & \text{take $log_n$ of both sides}\\
k & \leq \log_n (c) + \log_n(\log n) \\
k & \leq k + \log_n(\log n) & \text{set $\log_n (c) = k$ }
\end{aligned}$$ 

It can be seen that this inequality is true when $\log_n(\log n) \geq 0$, which will happen for all $n \geq 3$, assuming log is referring to the natural log. If it is referring to base $10$ than the inequality will be true for all $n \geq 10$. Regardless, this shows that $n^k$ is $O(n^{\log n})$ for any $k$ and $n^{\log n}$ is never $O(n^k)$. 

</details>


**Exercise 3.13**

Show that $n^{\log n}$ is sub-exponential.

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

We need to show that $c^n \geq a n^{\log n}$ for some $a$, some $n_0$, and any $c > 1$ for $n \geq n_0$.

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

Since $e(n)$ is $O(f(n))$ we know that $e(n) \leq cf(n)$ for some $c$ and for all $n \geq n_0$. Also since $g(n)$ is $O(h(n))$ we know that $g(n) \leq dh(n)$ for some $d$ and for all $n \geq n_1$. To show that $e(n)g(n)$ is $O(f(n)h(n))$, we need to show that $e(n)g(n) \leq b f(n)h(n)$ for some $b$ and for all $n \geq n_2$. 

$$\begin{aligned}
e(n)g(n) \leq b f(n)h(n) \\
e(n)g(n) \leq cd f(n)h(n) & \text{let $b = cd$} \\
e(n)g(n) \leq (c f(n))(d h(n))
\end{aligned}$$ 

Since we know that $e(n) \leq cf(n)$ for $n \geq n_0$ and $g(n) \leq dh(n)$ for $n \geq n_1$ we know that the above inequality is true for $n \geq n_2$ where $n_2 = \max(n_0, n_1)$. 

</details>



### The analysis of computational problems - Exercises




## Perspectives on computer science

### Perspectives on computer science - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|



### Perspectives on computer science - Exercises
