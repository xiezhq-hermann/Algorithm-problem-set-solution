# **CS240 Homework #4**

## _Zhiqiang Xie_ 77892769



### Problem 1: Stingy SAT

We call the problem described here "Stingy SAT", in formal-language terms:

STINGY-SAT = $\{<\phi, k>: \phi$ is a satisfiable boolean formula with at most $k$ variables are true$\}$

1. STINGY-SAT $\in$ NP.

   - Given an arbitary solution to Stingy SAT, we can evaluate the CNF formula in polynomial time by basic logical operations. And it just takes $O(1)$ time more to check whether the number of variables which are assigned to be true is less or equal to $k$.

2. SAT $\leq_p$ STINGY-SAT

   - Transformation:
     - Given a SAT formula $f$ with $n$ variables, we choose $(f,n)$ as an instance of Stingy SAT.

   - Proof:

     We now need to prove that $f$ is a yes-instance of SAT if and only if that $(f,n)$ is a yes-instance of Stingy SAT.

     - $(\Rightarrow)$ Suppose that $f$ is a yes-instance, and we can see that no more than $n$ variables in the formula can be true since $n$ is the amount of variables. So any satisfying assignment of instance $f$ will be a satisfying assignment of instance $(f,n)$. Therefore, $(f,n)$ is a yes-instance of Stingy SAT.
     - $(\Leftarrow)$ Suppose that $(f,n)$ is a yes-instance, any satisfying assignment of it's certainly a satisfying assignment of instance $f$.  Therefore, $f$ is a yes-instance of SAT.

Stingy SAT problem is NP-complete.

### Problem 2: Zero Weight Cycle

We call a simple cycle with the sum of its edge weights to be exactly $0$ "zero weight cycle", in formal-language terms:

Zero-Weight-Cycle = $\{<G>: G$ is a directed graph containing a zero weight cycle$\}$

1. Zero-Weight-Cycle $\in$ NP.

   - Given an arbitary solution to it $G_s \subseteq G$, we can check whether $G_s$ is a zero weight cycle in polynomial time by checking whether the sum of its edge weights is exactly $0$.

2. Directed-Hamiltonian-Cycle $\leq_p$ Zero-Weight-Cycle

   - Transformation:

     - Given an instance of Directed-Hamiltonian-Cycle, a directed graph $G = (V,E)$, where $n = |E|, E = \{e_1,e_2, ..., e_n\}$, we construct a new directed graph $G^\prime = (V^\prime, E^\prime)$. $G^\prime$ contains $n$ components $\{G_1, G_2, ..., G_n\}$.

       - Where $G_n = (V, E_n)$, $E_n$ means $weight(e_n) = -(|V|-1)$ and weights of other edges are $1$.

       This transformation cost polynomial time $O(n^2)$.

     - Now we set the directed graph $G^\prime$ to be an instance of Zero-Weight-Cycle.

   - Proof:

     We now need to prove that $G$ is a yes-instance of Directed-Hamiltonian-Cycle if and only if that $G^\prime$ is a yes-instance of Zero-Weight-Cycle.

     - $(\Rightarrow)$ Suppose that $G$ is a yes-instance, we'll see that at least one component $G_i \in \{G_1, G_2, ..., G_n\}$ contains a zero weight cycle (the hamiltonian cycle). Thus, $G^\prime$ contains at least one zero weight cycle. Therefore $G^\prime$ is a yes-instance of Zero-Weight-Cycle.

     - $(\Leftarrow)$ Suppose that $G^\prime$ is a yes-instance, and we know the only way to produce a zero weight cycle in any component $G_i \in \{G_1, G_2, ..., G_n\}$ is a hamiltonian cycle: $0 = (|V|-1)*1 + (-(|V|-1))$. Thus, $G$ is a hamiltonian graph.

       Therefore $G$ is a yes-instance of Directed-Hamiltonian-Cycle.

Zero Weight Cycle problem is NP-complete.

### Problem 3: Vertex Cover Neighbor 

We call the problem described here "Vertex Cover Neighbor", a *vertex cover neighbor* of an graph $G = (V, E)$ is a subset $V^\prime \in V$ such that for every $v \in V$, we have $v \in V^\prime$ or at least one of its neighbors $\in V^\prime$, in formal-language terms:

Vertex-Cover-Neighbor = $\{<G,K>:$ graph $G$ has a vertex cover neighbor of size $K\}$.

1. Vertex-Cover-Neighbor $\in$ NP.

   - Given an arbitary solution to it $V^\prime \in V$, we can check whether $V^\prime$ is a vertex cover neighbor in polynomial time by checking whether for each $v \in V$, $v \in V^\prime$ or at least one of its neighbors $\in V^\prime$. And it just takes $O(1)$ time more to check whether the number of nodes in $V^\prime$ is less or equal to $K$.

2. SET-COVER $\leq_p$ Vertex-Cover-Neighbor

   - Transformation:

     - Given an instance of 

   - Proof:

     We now need to prove that $G$ is a yes-instance of Directed-Hamiltonian-Cycle if and only if that $G^\prime$ is a yes-instance of Zero-Weight-Cycle.

     - $(\Rightarrow)$ Suppose that $$ is a yes-instance . Therefore $ $ is a yes-instance of 
     - $(\Leftarrow)$ Suppose that $$ is a yes-instance . Therefore $ $ is a yes-instance of 

 problem is NP-complete.



### Problem : 

We call the problem described here "", in formal-language terms:

 = $\{<G>: G$ $\}$

1. $\in$ NP.

   - Given an arbitary solution to it

2. $\leq_p$

   - Transformation:

     - Given an instance of 

   - Proof:

     We now need to prove that $G$ is a yes-instance of  if and only if that $G^\prime$ is a yes-instance of .

     - $(\Rightarrow)$ Suppose that $$ is a yes-instance . Therefore $ $ is a yes-instance of 
     - $(\Leftarrow)$ Suppose that $$ is a yes-instance . Therefore $ $ is a yes-instance of 

 problem is NP-complete.