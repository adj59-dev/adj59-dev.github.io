# Reading Nielsen and Chuang: Chapter 3

I just finished reading Chapter 3 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. 


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


### Models for computation - Exercises
  
  **Exercise 3.1** 




## The analysis of computational problems

### The analysis of computational problems - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|



### The analysis of computational problems - Exercises




## Perspectives on computer science

### Perspectives on computer science - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|



### Perspectives on computer science - Exercises
