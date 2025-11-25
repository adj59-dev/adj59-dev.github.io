# Reading Nielsen and Chuang: Chapter 6

I just finished reading Chapter 6 of *Quantum Computation and Quantum Information* by Nielsen and Chuang. 

## Navigation

* [The quantum search algorithm](#the-quantum-search-algorithm)
* [Quantum search as a quantum simulation](#quantum-search-as-a-quantum-simulation)
* [Quantum counting](#quantum-counting)
* [Speeding up the solution of NP-complete problems](#speeding-up-the-solution-of-np-complete-problems)
* [Quantum search of an unstructured database](#quantum-search-of-an-unstructured-database)
* [Optimality of the search algorithm](#optimality-of-the-search-algorithm)
* [Black box algorithm limits](#black-box-algorithm-limits)
* [Chapter problems](#chapter-problems)



## The quantum search algorithm

### The quantum search algorithm - Key Concepts


| Concept                              | Book Section              | Notes                                                                                                  |
|--------------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------|
| Grover iteration                     | 6.1.2                     | (1) Apply the oracle $O$. <br> (2) Apply the Hadamard transform $H^{\otimes n}$. <br> (3) Perform a conditional phase shift on the computer, with every computation basis state except $\ket{0}$ recieving a phase shift of -1, $\ket{x}\rightarrow -(-1)^{\delta_{x0}}\ket{x}$. <br> (4) Apply the Hadamard transform $H^{\otimes n}$.|



### The quantum search algorithm - Exercises

**Exercise 6.1**

Show that the unitary operator corresponding to the phase shift in the Grover iteration is $2\ket{0}\bra{0} - I$.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

Let's calculate $U\ket{x}$ and compare results to desired behavior, where $U=2\ket{0}\bra{0}-I$.

$$\begin{aligned}
U\ket{x} &= \left(2\ket{0}\bra{0} - I\right)\ket{x} \\
&= 2\ket{0}\braket{0\vert x} - \ket{x} \\
&= 2\delta_{x0}\ket{0} - \ket{x} \\
&= -(-1)^{\delta_{x0}}\ket{x}
\end{aligned}$$

This matches the desired behavior and so the unitary operator corresponding to the phase shift in the Grover iteration is $2\ket{0}\bra{0} - I$.

</details>















