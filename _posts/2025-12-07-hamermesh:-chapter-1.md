---
title: "Hamermesh: Chapter 1"
description: "Notes and exercise solutions for Group Theory and Its Application to Physical Problems Chapter 1: elements of group theory."
categories:
  - Group Theory and Its Application to Physical Problems
permalink: /GTAPP/chapter-1/
toc: true
tags:
  - Group Theory and Its Application to Physical Problems
  - Morton Hamermesh
  - Hamermesh
  - chapter 1
  - exercise
  - problem
  - solutions
last_modified_at: 2025-12-07 12:00:00 -08:00
exercises:
  - anchor: page-4-problem-1
    label: Page 4, Problem 1
  - anchor: page-11-problem-1
    label: Page 11, Problem 1
  - anchor: page-11-problem-2
    label: Page 11, Problem 2
  - anchor: page-11-problem-3
    label: Page 11, Problem 3
  - anchor: page-20-problem-1
    label: Page 20, Problem 1
  - anchor: page-20-problem-2
    label: Page 20, Problem 2
  - anchor: page-22-problem-1
    label: Page 22, Problem 1
  - anchor: page-23-problem-1
    label: Page 23, Problem 1
  - anchor: page-25-problem-1
    label: Page 25, Problem 1
  - anchor: page-27-problem-1
    label: Page 27, Problem 1
  - anchor: page-28-problem-1
    label: Page 28, Problem 1
  - anchor: page-29-problem-1
    label: Page 29, Problem 1
  - anchor: page-29-problem-2
    label: Page 29, Problem 2
  - anchor: page-29-problem-3
    label: Page 29, Problem 3
chapter: 1
---

I recently finished Chapter 1 of *Group Theory and Its Application to Physical Problems* by Morton Hamermesh. I picked up this book to complement *Quantum Computation and Quantum Information* by Nielsen and Chuang, which I’m working through in parallel. QCQI introduces several group theory ideas but doesn’t explore them in depth, so I wanted a resource that develops the concepts more systematically. Hamermesh does exactly that; his exposition is slower, richer in examples, and builds intuition before asking the reader to tackle problems.

One small note: the book uses the term invariant subgroup, which is largely outdated; modern texts refer to these as normal subgroups. Otherwise, the treatment has held up surprisingly well. I've included the solutions to the problems in chapter 1 below. 


<!-- toc -->


## Page 4

### Problem 1 {#page-4-problem-1}

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


## Page 11

### Problem 1 {#page-11-problem-1}

For the two groups given $a^2 = b$ and $a^2 = b^2 = c^2 = e$. We know $a^2 \neq a$ because then $a=e$. If we said $a^2 = c$ then we would get a group of the same form as (A), just with $b$ and $c$ swapped so this would not be a distinct structure. There are no other elements of the group that we could say $a^2$ is equal to, therefore there are no other distinct structures for a group of order 4. 

### Problem 2 {#page-11-problem-2}

Group (A) is $\lbrace e, a, a^2, a^3 \rbrace$ and group (B) is $\lbrace e, a, b, c \rbrace$. To show that a group is abelian, we need to show that $ab = ba$ for all $a,b$ in the group. 

For group (A),  since it is cyclic it is abelian. 

For group (B), for any $a,b$ in the group, since $a^2=e$ and $b^2=e$, then $a=a^{-1}$ and $b=b^{-1}$. Therefore, $(ab)^{-1} = b^{-1}a^{-1} = ba$. But since $(ab)^2 = c^2 = e$, then also $(ab)^{-1} = ab$ and so $ab=(ab)^{-1} = ba$. Therefore, group (B) is abelian.

### Problem 3 {#page-11-problem-3}


For group (A), a realization could be $0^\circ$, $90^\circ$, $180^\circ$, and $270^\circ$ rotation about a fixed axis in three dimensions. 

For group (B), a realization could be no rotation, $180^\circ$ rotation about the x-axis, $180^\circ$ rotation about the y-axis, and $180^\circ$ rotation about the z-axis in three dimensions.




## Page 20

### Problem 1 {#page-20-problem-1}

The elements are $e$, $(123456)$, and the powers of $(123456)$ which are $(135)(246)$, $(14)(25)(36)$, $(153)(264)$, and $(165432)$.

### Problem 2 {#page-20-problem-2}

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


## Page 22

### Problem 1 {#page-22-problem-1}

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


## Page 23

### Problem 1 {#page-23-problem-1}

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



## Page 25

### Problem 1 {#page-25-problem-1}

In $S_5$ the distinct classes are:
1. $e$
2. $(12),(13),(14),(15),(23),(24),(25),(34),(35),(45)$
3. $(12)(34),(13)(24),(14)(23),(12)(35),(13)(25),(15)(23),(12)(45),(14)(25),(15)(24),(13)(45),(14)(35),(15)(34),(23)(45),(24)(35),(25)(34)$
4. $(123),(124),(125),(132),(142),(152),(134),(135),(143),(153),(145),(154),(234),(235),(243),(253),(245),(254),(345),(354)$
5. $(123)(45),(132)(45),(124)(35),(142)(35),(125)(34),(152)(34),(134)(25),(143)(25),(135)(24),(153)(24),(145)(23),(154)(23),(234)(15),(243)(15),(235)(14),(253)(14),(245)(13),(254)(13),(345)(12),(354)(12)$
6. $(1234),(1235),(1243),(1253),(1245),(1254),(1324),(1325),(1342),(1352),(1423),(1523),(1432),(1532),(1425),(1452),(1524),(1542),(2345),(2354),(2435),(2453),(2534),(2543),(1345),(1354),(1435),(1453),(1534),(1543)$
7. $(12345),(12354),(12435),(12453),(12534),(12543),(13245),(13254),(13425),(13452),(13524),(13542),(14235),(14253),(14325),(14352),(14523),(14532),(15234),(15243),(15324),(15342),(15423),(15432)$


## Page 27

### Problem 1 {#page-27-problem-1}

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

In the book, these partitions for $S_5$ are of the form $(\lambda_1 \lambda_2 \lambda_3 \lambda_4 \lambda_5)$, where the number of $j-\text{cycles}$ is given by $v_j = \lambda_j-\lambda_{j+1}$ for $j<5$ and $v_5=\lambda_5$. Therefore, the structure for each partition for $S_5$ is

$$\begin{aligned}
\text{partition (book notation)} & (\lambda_1 \lambda_2 \lambda_3 \lambda_4 \lambda_5) & (v_1 v_2 v_3 v_4 v_5) & \text{example} & \text{number of permutations} \\
(5) & (50000) & (50000) & e & 1\\ 
(41) & (41000) & (31000) & (12) & 10 \\
(32) & (32000) & (12000) & (12)(34) & 15\\
(31^2) & (31100) & (20100) & (123) & 20 \\
(2^21) & (22100) & (01100) & (123)(45) & 20\\
(21^3) & (21110) & (10010) & (1234) & 30\\
(1^5) & (11111) & (00001) & (12345) & 24\\
\end{aligned}$$



## Page 28

### Problem 1 {#page-28-problem-1}

$$\begin{aligned}
(1234)(5678) & \text{and} & (1537)(2846)
\end{aligned}$$

show that one generates a group of order 8. Separate the elements of the group into conjugate classes. Show that this group (the quaternion group) is isomorphic to the group with elements

$$\begin{aligned}
1, -1, i, -i, j, -j, k, -k;\\
\end{aligned}$$

$$\begin{aligned}
i^2=j^2=k^2=-1, & ij=k, & jk=i, & ki=j
\end{aligned}$$

Let $a=(1234)(5678)$ and $b=(1537)(2846)$ then 

$$\begin{aligned}
a^2 &= (13)(24)(57)(68) & &\Leftrightarrow i^2 = -1\\
b^2 &= (13)(24)(57)(68) &= a^2 &\Leftrightarrow j^2 = -1\\
ab &= (1638)(2547) &= c &\Leftrightarrow ij=k\\
c^2 &= (13)(24)(57)(68) &= a^2 = b^2 &\Leftrightarrow k^2 = -1\\
bc &= (1234)(5678) &= a &\Leftrightarrow jk = i\\
ca &= (1537)(2846) &= b &\Leftrightarrow ki = j\\
a^4 &= e & = b^4 = c^4 &\Leftrightarrow 1 = i^4=j^4=k^4\\
\end{aligned}$$

Therefore, the group $\lbrace e, a^2, a, a^3, b, b^3, ab, (ab)^3\rbrace$ is isomorphic to $\lbrace  1, -1, i, -i, j, -j, k, -k \rbrace$. 


## Page 29

### Problem 1 {#page-29-problem-1}

The subgroups are invariant if they contain either all or none of the elements in a given class of $S_4$. None of these subgroups are invariant. 

The conjugate subgroups are calculated from $aHa^{-1}$ where $a$ is any element in $S_4$ and $H$ are the subgroups of $S_4$. When we form $aHa^{-1}$ with elements $a$ from $S_4$, we must get cycle structures that are the same as those of elements of $H$ and a subgroup that is the same size as $H$. 

For $S_3$ each conjugate subgroup will be of the structure $\lbrace e, (12), (13), (23), (123), (132) \rbrace$, with just permutations of the numbers $\lbrace 1,2,3,4 \rbrace$. There will be four such conjugates. 

For $S_2$ each conjugate subgroup with be of the structure $\lbrace e, (12) \rbrace$, with just permutations of the numbers $\lbrace 1,2,3,4 \rbrace$. There will be six such conjugates.

Similarly, for the cyclic group each conjugate subgroup with be of the structure $\lbrack e, (123), (132) \rbrack$, with just permutations of the numbers $\lbrace 1,2,3,4 \rbrace$. There will be four such conjugates. 

### Problem 2 {#page-29-problem-2}

The index of a subgroup is the number of distinct cosets of $H$ there are in $G$. If the index is 2, there are only two distinct left cosets in $G$: $H$ and $aH$ for $a\notin H$. There are also only two distinct right cosets: $H$ and $Ha$ for $a\notin H$. We see that $aH$ is all elements of $G$ that are not in $H$ and $Ha$ is also all elements of $G$ that are not in $H$. Therefore, $aH=Ha$. So, for any $g\in G$ it is either in $H$ and so $gH=H=Hg$ or it is not in $H$ and so $gH=aH=Ha=Hg$. Thus $gH=Hg$ for all $g$. Therefore $H$ is invariant. 

### Problem 3 {#page-29-problem-3}

A quaternion group is defined by $G=\lbrace 1,-1,i,-i,j,-j,k,-k\rbrace$ where $i^2=j^2=k^2=-1$, $ij=k$, $jk=i$, $ki=j$. Since any group with two of the components in $\lbrace i,j,k \rbrace$ will be able to generate the third component, the only nontrivial subgroups only contain one (or none) of them and is therefore of the structure $\lbrace 1, -1, a, -a \rbrace$ where $a=i,j,\text{ or }k$, $\lbrace 1, -1 \rbrace$, or is $\lbrace 1 \rbrace$.

For subgroups $\lbrace 1, -1, a, -a \rbrace$ where $a=i,j,\text{ or }k$, their index is 2 and so by problem (2) are necessarily invariant. For $H=\lbrace 1, -1 \rbrace$ for every $g\in G$, $gHg^{-1}=H$ since all elements in $H$ commute with all $g\in G$ and so $H$ is invariant. The same can be said for $\lbrace 1 \rbrace$. Therefore, all subgroups in the quaternion group are invariant. 




