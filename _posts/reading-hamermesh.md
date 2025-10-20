# Reading Hamermesh

I just finished reading *Group Theory And Its Application To Physical Problems* by Morton Hamermesh. I read this in parallel with the book *Quantum Computation and Quantum Information* by Nielsen and Chuang. 


## Navigation

* [Chapter 1 Elements of Group Theory](#chapter-1-elements-of-group-theory)
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




## Chapter 1 Elements of Group Theory



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

The order of two 3-cycles can be found by taking powers of an example permutation, say $(123)(456)$, which are $(132)(465)$, and $e$. Therefore, two 3-cycles are of order 3. 

The order of three 2-cycles can also be found by taking powers of an example permutation, say $(15)(24)(36)$, when you square this permutation, you get $e$, so three 2-cycles are of order 2. 

Therefore, every non-identity element must be one of: <br>
* a single 6-cycle (order 6) <br>
* a product of two disjoint 3-cycles (order 3) <br>
* a product of three disjoint 2-cycles (order 2) <br>

Looking at the different permutations of the two 3-cycle and three 2-cycles elements, we get $\lbrace e, (123)(456), (132)(465), (15)(24)(36), (14)(26)(35), (16)(25)(34) \rbrace$ which is of order 6. If we set $(123)(456)=a$ and $(15)(24)(36)=b$, we see that this group is equivalent to $\lbrace e, a, a^2, b, ba, ba^2 \rbrace$ with $bab=a^{-1}$ and so this group is isomorphic to $S_3$

Therefore, for groups that are order 6, if the group has an element of order 6 it is $C_6$; otherwise, it is $S_3$.

</details>


**Page 22**

The cyclic permutations on four symbols form a subgroup $H$ of $S_4$. Resolve $S_4$ into left cosets with respect to $H$. Compare this resolution with one into right cosets. 

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

By taking successive powers of $(1234)$ we get the cyclic subgroup of $S_4$, $H=\lbrace (1234), (13)(24), (1432), e \rbrace$. Let's calculate some left cosets. 

$$\begin{aligned}
eH &= \lbrace (1234), (13)(24), (1432), e \rbrace = H \\
(12)H &= \lbrace (234), (1324), (143), (12) \rbrace \\
(13)H &= \lbrace (12)(34), (24), (14)(23), (13) \rbrace \\
(14)H &= \lbrace (123), (1342), (243), (14) \rbrace \\
(23)H &= \lbrace (134), (1243), (142), (23) \rbrace \\
(24)H &= \lbrace (14)(23), (13), (12)(34), (24) \rbrace = (13)H \\
(34)H &= \lbrace (124), (1423), (132), (34) \rbrace \\
\end{aligned}$$


The number of elements in $S_4 = 4! = 24$. Therefore, we can define $S_4 = H + (12)H + (13)H + (14)H + (23)H + (34)H$, which has 24 unique elements. 

Now let's do the same for right cosets.

$$\begin{aligned}
He &= \lbrace (1234), (13)(24), (1432), e \rbrace = H \\
H(12) &= \lbrace (134), (1423), (243), (12) \rbrace \\
H(13) &= \lbrace (14)(23), (24), (12)(34), (13) \rbrace \\
H(14) &= \lbrace (234), (1243), (132), (14) \rbrace \\
H(23) &= \lbrace (124), (1342), (143), (23) \rbrace \\
H(24) &= \lbrace (12)(34), (13), (14)(23), (24) \rbrace = H(13)\\
H(34) &= \lbrace (123), (1324), (142), (34) \rbrace \\
\end{aligned}$$


Therefore, we can define $S_4 = H + H(12) + H(13) + H(14) + H(23) + H(34)$. This is a similar resolution as in the same permutations are multiplied to $H$, however the left and right cosets are not equal.

</details>


**Page 23**

Find the possible structures of groups of order 8.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

If the group contains an element $a$ of order 8, then the group is a cyclic group $\lbrace a, a^2, a^3, a^4, a^5, a^6, a^7, a^8=e \rbrace$. 

To find other possible structure, suppose that the group contains no elements of order 8, but instead has element $a$ of order 4. Thus, the group contains the subgroup $\lbrace a, a^2, a^3, a^4=e \rbrace$. If the group contains another distinct element, b, then it contains 8 distinct elements $\lbrace e, a, a^2, a^3, b, ba, ba^2, ba^3 \rbrace$. 

The element $b$ has order 2 or 4. If $b$ is order 4, then the element $b^3$ and $b^2$ must each be equal to one of the 8 distinct elements. Let's consider the options:
* $b^2=e$ or $b^3=e$: neither of these work because we assumed that $b$ has order 4
* $b^3=a$ or $b^2=a$: if $b^3=a$ that implies $ba=e$ and if $b^2=a$ that impiles $a^2=e$, these contradict the assumtion that $ba$ and $a^2$ are distinct elements.
* $b^3=a^2$: if $b^3=a^2$ it implies $ba^2=e$ which contradicts the assumption that $ba$ is a distinct element.
* $b^3=a^3$ or $b^2=a^3$: if $b^3=a^3$ it implies $ba^3=e$ and if $b^2=a^3$ it implies $e = a^2$ these contradict the assumption that $ba^3$ and $a^2$ are distinct elements.
* $b^3=b$ or $b^2=b$: if $b^3=b$ that implies $b^2=e$ which we already domonstrated is not possible and if $b^2=b$ it implies that $b=e$ which contradicts the assumption that $b$ is a distinct element.
* $b^3=ba$ or $b^2=ba$: if $b^3=ba$ it implies that $a=b^2$ which we already demonstrated is not possible and if $b^2=ba$ it implies that $b=a$ which contradicts the assumption that $b$ is a distinct element.
* $b^2=ba^2$: if $b^2=ba^2$ it implies that $b=a^2$ which contradicts the assumption that $b$ is a distinct element.
* $b^3=ba^3$ or $b^2=ba^3$: if $b^3=ba^3$ it implies that $b^2=a^3$ which we already demonstrated is not possible and if $b^2=ba^3$ that implies $b=a^3$ which contradicts the assumption that $b$ is a distinct element. 

Looking at what is left we see
* $b^2=a^2$
* $b^3=ba^2$

Therefore, $b$ can have order 4 if and only if $b^2=a^2$. Otherwise, $b$ has order 2 and $b^2=e$. 

Now let's check to see if the elements $a$ and $b$ can commute. In the book, the authors check the order of $ab$ when determining the possible structure of groups of order 6 to see if it contradicts any assumptions made thus far and so we'll perform a similar check for groups of order 8. If $a$ and $b$ commute $ab = ba$ and so $(ab)^2 = (ab)(ab) = (ab)(ba) = ab^2a$. When $b$ is order 4, $ab^2a = a^4=e$, which does not contradict any assumptions. When $b$ is order 2, $ab^2a = a^2 \neq e$. Checking larger powers, we see $(ab)^3 = ba^3$, $(ab)^4 = e$ and so $(ab)$ is order 4, which also does not contradict any assumptions. So unlike groups of order 6, non-cyclic groups of order 8 can have the elements commute.

Let's now suppose the group contains no order 4 or order 8 elements. Now we have $a$, $b$, and $c$ all of order 2. Then the elements are $\lbrace e, a, b, c, ab, ac, bc, abc \rbrace$. Since all the elements are order 2, $(ab)^2=(bc)^2=(ca)^2=e$ and so, using $ab$ as an example, $(ab)^2=abab = e \Rightarrow ab=ba$. Therefore, all terms must commute. 

Therefore, the following groups are possible for groups of order 8:
* $\braket{a \vert a^8=e}$
* $\braket{a,b \vert a^4=b^4=e, a^2=b^2, bab^{-1} = a}$
* $\braket{a,b \vert a^4=b^2=e, bab^{-1} = a}$
* $\braket{a,b \vert a^4=b^4=e, a^2=b^2, bab^{-1} = a^{-1}}$
* $\braket{a,b \vert a^4=b^2=e, bab^{-1} = a^{-1}}$
* $\braket{a,b,c \vert a^2=b^2=c^2=e, \text{all commute}}$

The group table for $\braket{a \vert a^8=e}$ is

| $e$    | $a$    | $a^2$  | $a^3$  | $a^4$  | $a^5$  | $a^6$  | $a^7$  |
|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|
| $a$    | $a^2$  | $a^3$  | $a^4$  | $a^5$  | $a^6$  | $a^7$  | $e$    |
| $a^2$  | $a^3$  | $a^4$  | $a^5$  | $a^6$  | $a^7$  | $e$    | $a$    |
| $a^3$  | $a^4$  | $a^5$  | $a^6$  | $a^7$  | $e$    | $a$    | $a^2$  | 
| $a^4$  | $a^5$  | $a^6$  | $a^7$  | $e$    | $a$    | $a^2$  | $a^3$  |
| $a^5$  | $a^6$  | $a^7$  | $e$    | $a$    | $a^2$  | $a^3$  | $a^4$  |
| $a^6$  | $a^7$  | $e$    | $a$    | $a^2$  | $a^3$  | $a^4$  | $a^5$  |
| $a^7$  | $e$    | $a$    | $a^2$  | $a^3$  | $a^4$  | $a^5$  | $a^6$  |


The group table for $\braket{a,b \vert a^4=b^4=e, a^2=b^2, bab^{-1} = a}$ is

| $e$    | $a$    | $a^2$  | $a^3$  | $b$    | $ba$   | $ba^2$ | $ba^3$ |
|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|
| $a$    | $a^2$  | $a^3$  | $e$    | $ba$   | $ba^2$ | $ba^3$ | $b$    |
| $a^2$  | $a^3$  | $e$    | $a$    | $ba^2$ | $ba^3$ | $b$    | $ba$   |
| $a^3$  | $e$    | $a$    | $a^2$  | $ba^3$ | $b$    | $ba$   | $ba^2$ | 
| $b$    | $ba$   | $ba^2$ | $ba^3$ | $a^2$  | $a^3$  | $e$    | $a$    |
| $ba$   | $ba^2$ | $ba^3$ | $b$    | $a^3$  | $e$    | $a$    | $a^2$  |
| $ba^2$ | $ba^3$ | $b$    | $ba$   | $e$    | $a$    | $a^2$  | $a^3$  |
| $ba^3$ | $b$    | $ba$   | $ba^2$ | $a$    | $a^2$  | $a^3$  | $e$    |

The group table for $\braket{a,b \vert a^4=b^2=e, bab^{-1} = a}$ is

| $e$    | $a$    | $a^2$  | $a^3$  | $b$    | $ba$   | $ba^2$ | $ba^3$ |
|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|
| $a$    | $a^2$  | $a^3$  | $e$    | $ba$   | $ba^2$ | $ba^3$ | $b$    |
| $a^2$  | $a^3$  | $e$    | $a$    | $ba^2$ | $ba^3$ | $b$    | $ba$   |
| $a^3$  | $e$    | $a$    | $a^2$  | $ba^3$ | $b$    | $ba$   | $ba^2$ | 
| $b$    | $ba$   | $ba^2$ | $ba^3$ | $e$    | $a$    | $a^2$  | $a^3$  |
| $ba$   | $ba^2$ | $ba^3$ | $b$    | $a$    | $a^2$  | $a^3$  | $e$    |
| $ba^2$ | $ba^3$ | $b$    | $ba$   | $a^2$  | $a^3$  | $e$    | $a$    |
| $ba^3$ | $b$    | $ba$   | $ba^2$ | $a^3$  | $e$    | $a$    | $a^2$  |

The group table for $\braket{a,b \vert a^4=b^4=e, a^2=b^2, bab^{-1} = a^{-1}}$ is

| $e$    | $a$    | $a^2$  | $a^3$  | $b$    | $ba$   | $ba^2$ | $ba^3$ |
|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|
| $a$    | $a^2$  | $a^3$  | $e$    | $ba^3$ | $b$    | $ba$   | $ba^2$ |
| $a^2$  | $a^3$  | $e$    | $a$    | $ba^2$ | $ba^3$ | $b$    | $ba$   |
| $a^3$  | $e$    | $a$    | $a^2$  | $ba$   | $ba^2$ | $ba^3$ | $b$    | 
| $b$    | $ba$   | $ba^2$ | $ba^3$ | $a^2$  | $a^3$  | $e$    | $a$    |
| $ba$   | $ba^2$ | $ba^3$ | $b$    | $a$    | $a^2$  | $a^3$  | $e$    |
| $ba^2$ | $ba^3$ | $b$    | $ba$   | $e$    | $a$    | $a^2$  | $a^3$  |
| $ba^3$ | $b$    | $ba$   | $ba^2$ | $a^3$  | $e$    | $a$    | $a^2$  |

The group table for $\braket{a,b \vert a^4=b^2=e, bab^{-1} = a^{-1}}$ is

| $e$    | $a$    | $a^2$  | $a^3$  | $b$    | $ba$   | $ba^2$ | $ba^3$ |
|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|
| $a$    | $a^2$  | $a^3$  | $e$    | $ba^3$ | $b$    | $ba$   | $ba^2$ |
| $a^2$  | $a^3$  | $e$    | $a$    | $ba^2$ | $ba^3$ | $b$    | $ba$   |
| $a^3$  | $e$    | $a$    | $a^2$  | $ba$   | $ba^2$ | $ba^3$ | $b$    | 
| $b$    | $ba$   | $ba^2$ | $ba^3$ | $e$    | $a$    | $a^2$  | $a^3$  |
| $ba$   | $ba^2$ | $ba^3$ | $b$    | $a^3$  | $e$    | $a$    | $a^2$  |
| $ba^2$ | $ba^3$ | $b$    | $ba$   | $a^2$  | $a^3$  | $e$    | $a$    |
| $ba^3$ | $b$    | $ba$   | $ba^2$ | $a$    | $a^2$  | $a^3$  | $e$    |

The group table for $\braket{a,b,c \vert a^2=b^2=c^2=e, \text{all commute}}$ is

| $e$    | $a$    | $b$    | $c$    | $ab$   | $bc$   | $ca$   | $abc$  |
|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|
| $a$    | $e$    | $ab$   | $ca$   | $b$    | $abc$  | $c$    | $bc$   |
| $b$    | $ab$   | $e$    | $bc$   | $a$    | $c$    | $abc$  | $ca$   |
| $c$    | $ca$   | $bc$   | $e$    | $abc$  | $b$    | $a$    | $ab$   | 
| $ab$   | $b$    | $a$    | $abc$  | $e$    | $ca$   | $bc$   | $c$    |
| $bc$   | $abc$  | $c$    | $b$    | $ca$   | $e$    | $ab$   | $a$    |
| $ca$   | $c$    | $abc$  | $a$    | $bc$   | $ab$   | $e$    | $b$    |
| $abc$  | $bc$   | $ca$   | $ab$   | $c$    | $a$    | $b$    | $e$    |

</details>


**Page 25**

Separate the elements of $S_5$ into conjugate classes.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

In $S_5$ the distinct classes are:
1. $e$
2. $(12),(13),(14),(15),(23),(24),(25),(34),(35),(45)$
3. $(12)(34),(13)(24),(14)(23),(12)(35),(13)(25),(15)(23),(12)(45),(14)(25),(15)(24),(13)(45),(14)(35),(15)(34),(23)(45),(24)(35),(25)(34)$
4. $(123),(124),(125),(132),(142),(152),(134),(135),(143),(153),(145),(154),(234),(235),(243),(253),(245),(254),(345),(354)$
5. $(123)(45),(132)(45),(124)(35),(142)(35),(125)(34),(152)(34),(134)(25),(143)(25),(135)(24),(153)(24),(145)(23),(154)(23),(234)(15),(243)(15),(235)(14),(253)(14),(245)(13),(254)(13),(345)(12),(354)(12)$
6. $(1234),(1235),(1243),(1253),(1245),(1254),(1324),(1325),(1342),(1352),(1423),(1523),(1432),(1532),(1425),(1452),(1524),(1542),(2345),(2354),(2435),(2453),(2534),(2543),(1345),(1354),(1435),(1453),(1534),(1543)$
7. $(12345),(12354),(12435),(12453),(12534),(12543),(13245),(13254),(13425),(13452),(13524),(13542),(14235),(14253),(14325),(14352),(14523),(14532),(15234),(15243),(15324),(15342),(15423),(15432)$

</details>


**Page 27**

Continue the table to $n=5,6,7$. For $n=5$, give the cycle structure corresponding to each partition.

<details style="margin-bottom: 20px;" markdown="1">
<summary>Solution</summary>

The table through $n=7$ is 

$$\begin{aligned}
S_1: & (1); & r=1, \\
S_2: & (2), (1^2); & r=2 \\
S_3: & (3), (21), (1^3); & r=3 \\
S_4: & (4), (31), (2^2), (21^2), (1^4); & r=5 \\
S_5: & (5), (41), (32), (31^2), (2^21), (21^3), (1^5); & r= 7 \\
S_6: & (6), (51), (42), (41^2), (3^2), (321), (31^3), (2^3), (2^21^2), (21^4), (1^6); & r= 11\\
S_7: & (7), (61), (52), (51^2), (43), (421), (41^3), (3^21), (32^2), (321^2), (31^4), (2^31), (2^21^3), (21^5), (1^7); & r= 15
\end{aligned}$$

The structure for each partition for $S_5$ is

$$\begin{aligned}
(5): & (12345)\\
(41): & (1234) \\
(32): & (123)(45) \\
(31^2): & (123) \\
(2^21): & (12)(34)\\
(21^3): & (12) \\
(1^5): & e
\end{aligned}$$

</details>




