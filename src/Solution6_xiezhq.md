# PROBLEM SET 6

## _Zhiqiang Xie_ 77892769

### Problem 1: Knapsack Variants

- If $i=0$, $OPT(i,w) = 0$
- If $w < w_i,$ $OPT(i,w) = OPT(i-1,w)$
- If $w_i < w < 2w_i$, $OPT(i,w) = max\{OPT(i-1,w), v_i+OPT(i-1,w-w_i)\}$
- If $2w_i\leq w $, $OPT(i,w) = max\{OPT(i-1,w), v_i+ max\{OPT(i,w-w_i),OPT(i-1,w-w_i)\}\}$

1. **Python**

   ```python

   ```
   ​


### Problem 2: Multiplication Card

$OPT(1,n) = min_{2\leq j\leq n-1}\{OPT(1,j) + OPT(j,n) + c_1*c_j*c_n\}$



### Problem 3:



### Problem 4: 

- Assumptions:

  - Every node in $T$ has a parent-child relation with the nodes they connected.
  - Precompute the $2^j th$ ancestor for all valid $j$ for each node in $T$.
  - Put the result above into a sparse 2D table $P$ such that $P[i][j]$ stores the $2^j th$ ancestor for node $i$.

  This preprocess costs $O(V\log V)$ time and space.

- Every number can be expressed as a *sum* of distinct *powers* of $2$.

- Hence, we may use our table $P$ to keep raising our nodes by distinct powers of $2$ to find their LCA.

- Some details about the procedures above is omitted.

- In this way, we can find the LCA in $O(\log V)$ time.