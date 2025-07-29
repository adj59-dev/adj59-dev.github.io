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

This question is about non-computable processes in Nature. I am not really sure what the authors are looking for from this question. 

<details style="margin-bottom: 20px;">
<summary>Solution</summary>

You would need to show that that no Turing machine could reproduce the same input-output mapping. 

</details>

**Exercise 3.2**

I went to the History and further reading section of this chapter after reading this question, since I was somewhat lost on what to do, and saw that the authors reference *Computation: Finite and Infinite Machines* by Minsky and a couple of articles by J.H. Conway as inspiration for the first four exercises in this chapter. 

A copy of Minsky's book can be found here: https://www.scss.tcd.ie/Martin.Emms/2062/PossReading/finite_and_infinite_machines_minsky.pdf

The Conway articles are here:
Unpredictable Iterations: https://gwern.net/doc/cs/computable/1972-conway.pdf <br>
Fractran: https://www.cs.unc.edu/~stotts/COMP210-s23/madMath/Conway87.pdf

I found reading Minsky section 7.2 to be helpful in understanding what this question is asking us to do (and why it may be useful), which is to find a way of representing a given Turing machine's "state diagram" (the set of quintuples that represent its states, inputs, and outputs, i.e. what QCQI authors call the "program") as a unique number that can be used by a universal Turing machine to simulate that specific Turing machine. The Fractran article discusses encoding data in the exponent of a prime number in the prime factorization of the integer, which is referenced in the hint for this exercise, but this doesn't appear to be the only way one might generate a "Turing number".


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
