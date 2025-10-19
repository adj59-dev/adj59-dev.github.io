# Reading Hamermesh

I just finished reading *Group Theory And Its Application To Physical Problems* by Morton Hamermesh. I read this in parallel with the book *Quantum Computation and Quantum Information* by Nielsen and Chuang. 


## Navigation

* [Chapter 1. Elements of Group Theory](#chapter-1.-elements-of-group-theory)
* [Chapter 2](#chapter-2)
* [Chapter 3](#chapter-3)
* [Chapter 4](#chapter-4)
* [Chapter 5](#chapter-5)
* [Chapter 6](#chapter-6)
* [Chapter 7](#chapter-7)
* [Chapter 8](#chapter-8)
* [Chapter 9](#chapter-9)
* [Chapter 10](#chapter-10)
* [Chapter 11](#chapter-11)
* [Chapter 12](#chapter-12)




## Chapter 1. Elements of Group Theory



### Elements of Group Theory - Problems

**Page 4**

The cross ratio of four points on a line is defined as 

$$\begin{aligned}
\frac{(x_1-x_2)/(x_3-x_2)}{(x_1-x_4)/(x_3-x_4)}
\end{aligned}$$

where $x_1,x_2,x_3,x_4$ are the coordinates of the four points. Show that the cross ratio is invariant under projective transformation.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

Projective transformation of a line is defined by

$$\begin{aligned}
x\rightarrow x'; & x'=\frac{ax+b}{cx+d}, & \text{where $ad-bc\neq 0$}
\end{aligned}$$

and so

$$\begin{aligned}
\frac{(x_1-x_2)/(x_3-x_2)}{(x_1-x_4)/(x_3-x_4)} &\rightarrow \frac{\left(\frac{ax_1+b}{cx_1+d}-\frac{ax_2+b}{cx_2+d}\right)/\left(\frac{ax_3+b}{cx_3+d}-\frac{ax_2+b}{cx_2+d}\right)}{\left(\frac{ax_1+b}{cx_1+d}-\frac{ax_4+b}{cx_4+d}\right)/\left(\frac{ax_3+b}{cx_3+d}-\frac{ax_4+b}{cx_4+d}\right)} \\
&= \frac{\left(\frac{ax_1+b}{cx_1+d}-\frac{ax_2+b}{cx_2+d}\right)\left(\frac{ax_3+b}{cx_3+d}-\frac{ax_4+b}{cx_4+d}\right)}{\left(\frac{ax_3+b}{cx_3+d}-\frac{ax_2+b}{cx_2+d}\right)\left(\frac{ax_1+b}{cx_1+d}-\frac{ax_4+b}{cx_4+d}\right)} \\
&= \frac{\left(\frac{(ax_1+b)(cx_2+d)-(ax_2+b)(cx_1+d)}{(cx_1+d)(cx_2+d)}\right)\left(\frac{(ax_3+b)(cx_4+d)-(ax_4+b)(cx_3+d)}{(cx_3+d)(cx_4+d)}\right)}{\left(\frac{(ax_3+b)(cx_2+d)-(ax_2+b)(cx_3+d)}{(cx_3+d)(cx_2+d)}\right)\left(\frac{(ax_1+b)(cx_4+d)-(ax_4+b)(cx_1+d)}{(cx_1+d)(cx_4+d)}\right)}\\
&= \frac{\left((ax_1+b)(cx_2+d)-(ax_2+b)(cx_1+d)\right)\left((ax_3+b)(cx_4+d)-(ax_4+b)(cx_3+d)\right)}{\left((ax_3+b)(cx_2+d)-(ax_2+b)(cx_3+d)\right)\left((ax_1+b)(cx_4+d)-(ax_4+b)(cx_1+d)\right)}\\
&= \frac{\left((ad-bc)(x_1-x_2)\right)\left((ad-bc)(x_3-x_4)\right)}{\left((ad-bc)(x_3-x_2)\right)\left((ad-bc)(x_1-x_4)\right)}\\
&= \frac{(x_1-x_2)(x_3-x_4)}{(x_3-x_2)(x_1-x_4)}\\
&= \frac{(x_1-x_2)/(x_3-x_2)}{(x_1-x_4)/(x_3-x_4)}
\end{aligned}$$

Therefore, the cross ratio is invariant under projective transformation.

</details>

**Page 11**

(1) Show that (A) and (B) are the only possible structures for the group of order 4.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

For the two groups given $a^2 = b$ and $a^2 = b^2 = c^2 = e$. We know $a^2 \neq a$ because then $a=e$. If we said $a^2 = c$ then we would get a group of the same form as (A), just with $b$ and $c$ swapped so this would not be a distinct structure. There are no other elements of the group that we could say $a^2$ is equal to, therefore there are no other distinct structures for a group of order 4. 

</details>

(2) Show directly that the group of order 4 must be abelian.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

Group (A) is $\lbrace e, a, a^2, a^3 \rbrace$ and group (B) is $\lbrace e, a, b, c \rbrace$. To show that a group is abelian, we need to show that $ab = ba$ for all $a,b$ in the group. 

For group (A),  since it is cyclic it is abelian. 

For group (B), for any $a,b$ in the group, since $a^2=e$ and $b^2=e$, then $a=a^{-1}$ and $b=b^{-1}$. Therefore, $(ab)^{-1} = b^{-1}a^{-1} = ba$. But since $(ab)^2 = c^2 = e$, then also $(ab)^{-1} = ab$ and so $ab=(ab)^{-1} = ba$. Therefore, group (B) is abelian.

</details>

(3) Give a realization of each of the groups of order 4.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

For group (A), a realization could be $0^\circ$, $90^\circ$, $180^\circ$, and $270^\circ$ rotation about a fixed axis in three dimensions. 

For group (B), a realization could be no rotation, $180^\circ$ rotation about the x-axis, $180^\circ$ rotation about the y-axis, and $180^\circ$ rotation about the z-axis in three dimensions.

</details>


**Page 20**

(1) Give the elements of the regular subgroup of $S_6$ which is isomorphic with the cyclic group of order $6$. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

The elements are $e$, $(123456)$, and the powers of $(123456)$ which are $(135)(246)$, $(14)(25)(36)$, $(153)(264)$, and $(165432)$.

</details>

(2) Use Cayley's theorem to find the possible structures of groups of order 6.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

This problem is equivalent to finding the structure of the regular subgroups of $S_6$. For regular permutation subgroups, we know that all the cycles in a permutation must have the same length. Therefore, we know that the elements in a subgroup must have either one 6-cycle, two 3-cycles, or three 2-cycles. 

The elements of a subgroup containing a 6-cycle are given in problem (1) which is a cyclic group of order 6, $C_6$. 

The order of two 3-cycles can be found by taking powers of an example permutation, say $(135)(246)$, which are $(153)(264)$, and $e$. Therefore, two 3-cycles are of order 3. 

The order of three 2-cycles can also be found by taking powers of an example permutation, say $(14)(25)(36)$, when you square this permutation, you get $e$, so three 2-cycles are of order 2. 

Therefore, every non-identity element must be one of: <br>
* a single 6-cycle (order 6) <br>
* a product of two disjoint 3-cycles (order 3) <br>
* a product of three disjoint 2-cycles (order 2) <br>

Looking at the different permutations of the two 3-cycle and three 2-cycles elements, we get $\lbrace e, (123)(456), (132)(465), (14)(25)(36), (15)(26)(34), (16)(24)(35) \rbrace$ which is of order 6. If we set $(123)(456)=a$ and $(14)(25)(36)=b$, we see that this group is equivalent to $\lbrace e, a, a^2, b, ba, ba^2 \rbrace$ with $bab=a^{-1}$ and so this group is isomorphic to $S_3$

Therefore, for groups that are order 6, if the group has an element of order 6 it is $C_6$; otherwise, it is $S_3$.

</details>




