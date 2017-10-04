# **CS240 Homework #1**

## _Zhiqiang Xie_ 77892769



### Problem 1

I represent the ascending order in Asymptotic notations:

$2^{\sqrt{\log n}} = o(n(\log n)^3) = o(n^{4/3}) = o(n^{\log n}) = o(2^n) = o(2^{n^2}) = o(2^{2^n})$



### Problem 2

 1.  $f(n) = p + q*n$, where $p, q$ are constants. Therefore,  $f(n) = O(n)$

 2.  Treat $n$ as a binary number, so that we only need to calculate the 1th, 2th, 4th... power of x. I'll illustrate a faster algorithm in Python code:

     **Python**

     ```python
     def fastPower(x, n):
         """
         :type x: int != 0
         :type n: int >= 0
         :rtype: int
         """
         res = 1
         while n:
             if n&1:
                res *= x
             n >> 1
             x *= x
         return res
     ```

     Thus, $g(n) = p_1 + q_1*\lceil\log_2 n\rceil$, where $p_1, q_1$ are constants.

     Therefore, $g(n) = O(\log n), lim_{n\rightarrow \infty} \frac{g(n)}{f(n)} = 0$



### Problem 3

I summarize and abstract the information of this problem below:

 - $n$ scenic spots and $m$ roads mean a graph contains $n$ vertices and $m$ edges.
 - Roads in one direction and no cycle mean the graph is a directed acyclic graph(DAG).
 - Our task is to determine whether here exists a path which can traverse all vertices(since it's a DAG, no path could visit the same city twice or more)

We need two lemmas to start our procedures:

 - Here are always one or more vertices with in-degree zero.
    - At least one city in our map cannot be reached from any other cities.
- Any sub-graph of a DAG is a DAG
  - Every time we have visited a city, the subsequent task is just the same.

We need to prepare an in-degree table first:

 - To do this, we'll iterate all vertices once. Now we know  the vertices with 0 in-degree.
 - This preparation cost $\Theta(n)$ time and $\Theta(n)$ space.

Now we start our algorithm at the cities with 0 in-degree:

 - Once we have more than one 0 in-degree city, we know it's impossible to find such a path to visit all cities. The program terminates.
 - We remove the selected city from our map and deduct the in-degree of the cities being directed by one.
 - Then we choose the cities with 0 in-degree from them. Based on the lemma 2, here must be at least one city to be choosen.
 - Repeat the procedures until we traverse all cities or terminated in procedure 1.
 - These procedures cost $O(m + n)$ time.

Finally, the time complexity is $O(m + n) + \Theta(n) \in O(m + n)$



### Problem 4

I summarize and abstract the information of this problem below:

 - $n$ scenic spots and $m$ roads mean a graph contains $n$ vertices and $m$ edges.
 - The graph is undirected and connected.
 - Our task is to remove a vertex from the graph and make it remain connected.

Now we start our algorithm at a random city:

-   Set the vertex to be part of the spanning tree of the graph.


-   Do BFS or DFS from the vertex we selected.
-   Every time we find a vertex that is not in the spanning tree, add to the spanning tree both the new
    node and the edge.

Since the graph is connected, we'll get a spanning tree after the precedure above.

-   The procedure costs $O(m + n)$ time.
-   Then we choose a leaf from the spanning tree and the vertex is our answer.
-   Choose a leaf cost $O(n)$ time (worst case, $O(\log n)$ is more general)

Finally, the time complexity is $O(m + n) + O(n) \in O(m + n)$



### Problem 5

Proof part:

-   Firstly, we can assume that no such node $v$ existes.
-   At this case, there must be two totally different path from node $s$ to node $t$ with the length strictly greater than $n/2$.
-   However, it requires number of nodes $n > (n/2 + 1)*2 - 2 = n$, which is impossible.
-   Therefore, there must exist some node $v$, not equal to either $s$ or $t$, such that deleting $v$ from $G$ destroys all $s-t$ paths.

Algorithm part (some details in implementation is ommited):

-   Start two BFS from $s$ and $t$ respectively.
-   When the two BFS meet at just one node, we get the node $v$.
-   The procedure costs $O(m + n)$ time.
