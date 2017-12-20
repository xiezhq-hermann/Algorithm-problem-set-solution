# PROBLEM SET 6

## _Zhiqiang Xie_ 77892769

### Problem 1: Knapsack Variants

- If $i=0$, $OPT(i,w) = 0$
- If $w < w_i,$ $OPT(i,w) = OPT(i-1,w)$
- If $w_i < w < 2w_i$, $OPT(i,w) = max\{OPT(i-1,w), v_i+OPT(i-1,w-w_i)\}$
- If $2w_i\leq w $, $OPT(i,w) = max\{OPT(i-1,w), v_i+ max\{OPT(i,w-w_i),OPT(i-1,w-w_i)\}\}$

**Python**

```python

```


### Problem 2: Multiplication Card

$OPT(1,n) = min_{2\leq j\leq n-1}\{OPT(1,j) + OPT(j,n) + c_1*c_j*c_n\}$

$OPT(i,i+1) = 0$

**Python**

```python

```



### Problem 3:

Set the start node to be the root of the tree.

- For all each $u$ in tree, $OPT_0(u,0) = OPT_1(u,0) = w(u)$, $OPT(u,-1) = 0$ 
- If $u$ is leaf node, $OPT_0(u,i) = OPT_1(u,i) = w(u)$, $\forall i \in[1,k]$ 

$OPT_1(u,i) = max_{v\in children(u)}\{max_{-1\leq j\leq i-2}\{OPT_1(u,i-j-2) + OPT_1(v,j)\}\}$

$OPT_0(u,i) = \\max_{v\in children(u)}\{max_{0\leq j\leq i-1}\{OPT_0(u,i-j-2) + OPT_1(v,j), OPT_1(u,i-j-1)+OPT_0(v,j)\}\} $

Algorithm:

- ​

### Problem 4: 



Preprocessing:

- Precompute the level of every node (length of the path to the root).
  - This procedure costs $O(n)$ by BFS.
- Precompute the $2^j th$ ancestor for all valid $j$ for each node in the rooted tree.
- Put the result above into a sparse 2D table $P$ such that $P[i][j]$ stores the $2^j th$ ancestor for node $i$.
- This preprocess costs $O(n\log n)$ time and space.

If $level(v_i) = level(w_i)$:

- Every number can be expressed as a *sum* of distinct *powers* of $2$.
- Keep referencing the table by finding the "largest uncommon ancestor" and finally we'll get $LCA(v_i,w_i) = k^{th}$
- This procedure costs $O(\log H)$

Else:

- Replace the node with high level to be its ancestor with the same level to another node.
  - This procesdure could cost $O(\log H)$ 
- Repeat the procedure above.

Where $H$ is the height of the tree. 

Therefore, we can guarantee $T(n) = O(n\log n) + m*O(\log H) \in O((n+m)\log n)$



### Problem 5:

1. **Python**

   ```python

   ```

   $T(n) = O(\sum_{i=1}^{n-1} i(n-1)) \in O(n^3)$

   ​

2. $w(a,c) + w(b,d) = \sum_{k=a}^d a_k + \sum_{k=b}^c a_k = w(b,c) + w(a,d)$

   $w(b,c) = \sum_{k=b}^c a_k \leq \sum_{k=a}^b a_k + \sum_{k=b}^c a_k + \sum_{k=c}^d a_k = \sum_{k=a}^d a_k = w(a,d)$

   ​

3. As for $0<a<b<c<d$, we have:

   - $f(a,d) = f(a,t) + f(t+1,d) + w(a,d)$
   - $f(b,c) = f(b,k) + f(k+1,c) + w(b,c)$

   Without loss of generality, we can assume $a \leq t \leq k \leq c$

   $f(a,c) + f(b,d) \\ \leq f(a,t) + f(t+1,c) + w(a,c) + f(b,k) + f(k+1,d) + w(b,d)\\ \leq f(a,t) + f(t+1,d) + w(a,d) + f(b,k) + f(k+1,c) + w(b,c)\\ = f(a,d) + f(b,c)$

   Therefore, $f(a,c) + f(b,d)  \leq f(a,d) + f(b,c)$

   ​

4. By symmetry, we need only to prove that $K(i,j-1) \leq K(i,j)$

   Since $f(a,c) + f(b,d)  \leq f(a,d) + f(b,c)$:

   - TBD
   - ​

5. $f(i,j) = min_{K(i,j-1)\leq k \leq K(i+1,j)} \{f(i,k-1) + f(k,j) + w(i,j)\}$

   $T(n) \in O(n^2)$

