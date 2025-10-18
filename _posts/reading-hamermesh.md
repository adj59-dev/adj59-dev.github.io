# Reading Hamermesh

I just finished reading *Group Theory And Its Application To Physical Problems* by Morton Hamermesh. 


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
<summary>Proof</summary>

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


