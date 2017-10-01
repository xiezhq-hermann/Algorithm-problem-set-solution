# **PROBLEM SET 1**
#### *Zhiqiang Xie*  77892769

##Problem 1

`a.` By Master Theorem, $log_3 9 = 2$,

​	$T(n) \in \Theta(n^2lg(n))​$

`b.` By Master Theorem, $log_3 5 > 1$, and $n^{log_3 5}$ is polynomially large than $n$,

​	$T(n) \in \Theta(n^{log_3{5}})$

`c.` Let $n = 2^{8m}$, we can get:

​	$T(2^{8m}) = 7T(2^m) + 64m^2$, rename $S(m) = T(2^{8m})$ to prodece:

​	$S(m) = 7S(m/8) + 64m^2$, we can get $S(m) \in \Theta(m^2)$ by Master Theorem,

​	Therefore, $T(n) \in \Theta(lg^2(n))$

`d.` Assume that $T(n) \in O(n)$ and try $T(n) \leq cn$ and $\Theta(n) = dn$, we abtain:

​	$T(n) \leq \frac{c}{2}n + \frac{c}{4}n + dn$

​		$= (\frac{3c}{4}+d)n \leq cn$, 		as long as $c \geq 4d$, which is satisfiable.

​	Futher more, since $T(n) \geq dn$, $T(n) \in \Theta(n)$

`e.`

 - $log(log(n)) = o(log(n)) = o((log(n))^2) = o(\sqrt{n})$
 - $log(n!) = \Theta(nlog(n)) = o(n^{4/3}) = o(n^2)$
 - $2^{log(n^{log(log(n))})} = o(e^n) = o(n!) = o(n^n)$



##Problem 2 & 3

#### Algorithm 1

$T(n) = \Theta(1) + \sum\limits_{i=3}^n (\Theta(1) + (\lfloor{\sqrt i}\rfloor - 1)*\Theta(1)) \in O(n^{3/2})$

####Algorithm 2

$T(V,E) = \Theta(1) + \sum\limits_{i = 1}^V (\Theta(1) + n)$, where n is the number of nodes which is adjacent to vertex $V_i$.

ThereFore, $T(V, E) = \Theta(1) + V + \sum\limits_{i = 1}^{V}n = \Theta(1) + V + E \in \Theta(V + E)$, where $V, E$ are the number of vertex and edge.

#### Algorithm 3

$T(n) = T(n-1) + 2T(n-2) + \Theta(1)$

For simplification, we set $T(1) = T(2) = \Theta(1) = 1$, here we attain:

$\begin{bmatrix} T_n \\\ T_{n+1} \\\ 1\end{bmatrix}$ $= M*$$\begin{bmatrix}T_{n-1} \\\ T_n\\\ 1\end{bmatrix}$ Where $M = $$\begin{pmatrix}0 & 1 & 0\\\ 2 & 1 & 1 \\\ 0 &  0 & 1\end{pmatrix}$

Then we can get the Eigenvector matrix and Eigenvalue matrix:

$\Lambda = \begin{pmatrix}1 & 0 & 0\\\ 0 & 2 & 0 \\\ 0 & 0 & -1\end{pmatrix}$ $S = \begin{pmatrix}1 & 1 & 1\\\ 1 & 2 & -1 \\\ -2 & 0 & 0\end{pmatrix}$

$\begin{bmatrix}T_{1} \\\ T_2\\\ 1\end{bmatrix} = \begin{bmatrix}1 \\\ 1 \\\ 1\end{bmatrix} = -\frac{1}{2}\begin{bmatrix}1 \\\ 1\\\ -2\end{bmatrix} + \begin{bmatrix}1 \\\ 2\\\ 0\end{bmatrix} + \frac{1}{2} \begin{bmatrix}1 \\\ -1\\\ 0\end{bmatrix}$

Therefore, $T_n = -\frac{1}{2}*1^{n-1} + 2^{n-1} + \frac{1}{2}(-1)^{n-1} \in \Theta(2^n)$

#### Algorithm 4

$T(n) = \Theta(n) + T(n/3) + 2T(2n/3)$ (For wrost case)

Assume that $T(n) \in O(n^2)$ and try $T(n) <= cn^2 - dn$ and $\Theta(n) = en$, we attain:

$T(n) \leq en + \frac{c}{9}n^2 - \frac{d}{3}n + \frac{8}{9}n^2 - \frac{4d}{3}n$

​	$= cn^2 + (e-\frac{5d}{3})n$

​	$\leq cn^2 - dn$,		as long as $d \geq \frac{3}{2}e$, which is satisfiable

Therefore, $T(n) \in O(n^2)$



## Problem 4

`a.` $\sum\limits_{i=1}^{n}\frac{1}{i^2} < 2 - \frac{1}{n} < 2 $, $(n > 1)$

​	As for $n = 1,2$, the base cases ($ 1< 2$,  $1+1/4 < 2$) are true.

​	Suppose the inequation to be true for $n = k, k \in Z^+$, we have

​	$\sum\limits_{i=1}^{k+1}\frac{1}{i^2} < 2 - \frac{1}{k} + \frac{1}{(k+1)^2} = 2 - \frac{k^2+k+1}{k(k+1)^2} < 2 - \frac{k^2 + k}{k(k+1)^2} = 2 - \frac{1}{k+1}$

​	Therefore, by the principle of induction, the inequation is true for all $n \in Z^+$

`b.` Since $n$ is a interger and $n > 2$, we can simplify this inequation to be:

​	$n > (1 + 1/n)^n$

​	As for $n = 3$, the base case ( $ 4^3 = 64 < 81 = 3^4$) is true.

​	Suppose the inequation to be true for $n = k, k >= 3$, we have

​	$(1 + \frac{1}{n+1})^{n+1} < (1 + 1/n)^{n+1} = (1 + 1/n)^n * (1 + 1/n) < n*(1 + 1/n) = n + 1$

​	Therefore, by the principle of induction, the inequation is true for all integer $n > 2$



## Problem 5

`a.` Based on the formula, we can attain:

​	$x_{n+1} - x_n = \frac{1}{2}(\frac{\alpha}{x_n} - x_n) < 0$	 if $x_n > \sqrt{\alpha}$

​	$x_{n+1}^2 - \alpha = \frac{1}{4}(x_n^2 - 2\alpha + \frac{\alpha^2}{x_n^2}) > 0$	if $x_n > \sqrt{\alpha}$

​	Therefore, since $x_1 > \sqrt{\alpha}$, $x_{n+1} < x_n$, and $ x_{n} > \sqrt{\alpha}$ will be true for all $n \in Z^+$ and $x_n$ will converge to $\sqrt{\alpha}$

​	Therefore, $lim_{n\rightarrow \infty} x_n = \sqrt{\alpha}$

`b.` $\epsilon_{n+1} = x_{n+1} - \sqrt{\alpha} = \frac{1}{2}(x_n - 2\sqrt{\alpha} + \frac{\alpha}{x_n}) = \frac{(x_n - \sqrt{\alpha})^2}{2x_n} = \frac{\epsilon_n^2}{2x_n} < \frac{\epsilon_n^2}{2\sqrt{\alpha}}$, since $x_n > \sqrt{\alpha}$ for all n

​	From $\beta = 2\sqrt{\alpha}$, the formula becomes $\frac{\epsilon_{n+1}}{\beta} < (\frac{\epsilon_n}{\beta})^2$ for all $n > 0$

​	Therefore, $\epsilon_{n+1} < \beta(\frac{\epsilon_1}{\beta})^{2n}$

`c.` $\frac{\epsilon_1}{\beta} = (2- \sqrt{3})/(2*\sqrt{3}) = 0.077 < 1/10$ and certainly $\frac{\epsilon_n}{\beta} < 1/10$ for all $n > 0$

Based on the formula above: $\epsilon_{n+1} < \beta(\frac{\epsilon_1}{\beta})^{2n}$, we attain:

$\epsilon_5 < 2 * \sqrt{3}*(0.077)^{(2^4)} = 5.29*10^{-18} < 4*10^{-16}$

$\epsilon_6 < 2 * \sqrt{3}*(0.077)^{(2^5)} = 8.08*10^{-36} < 4*10^{-32}$
