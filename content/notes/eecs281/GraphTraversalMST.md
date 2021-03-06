---


title: Graph Traversal Algorithms (and MSTS)
linktitle: Graph Traversal Algorithms (and MSTS)
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  example:
    parent: Final Topics
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1

---

## <span style="color:orange">Depth-first search</span>

Uses a stack

Visit the child nodes before visiting the sibling nodes. This allows us to traverse the depth of any particular path before exploring its breadth.

## <span style="color:orange">Breadth-first search</span>

Uses a queue

Visits the sibling nodes before visiting the child nodes

When all edges have the same cost (e.g. unweighted graph), BFS finds the shortest path between nodes.

More generally, if the cost of the path is non-decreasing function of the depth of the node, then BFS finds the shortest path between nodes.

## <span style="color:orange">Spanning Trees</span>

A spanning tree is a subset of a graph $G$ that contains all vertices in $V$, is connected and is acyclic.

Given this graph

![image](/notes/eecs281/images/mst1.png)

This would be an example of a spanning tree

![image](/notes/eecs281/images/mst2.png)

### <span style="color:gold">Minimum Spanning Tree (MST)</span>

An MST is the spanning tree which has the lowest total cost.

Important distinction between MST and regular spanning tree: the sum of the edge weights is less than any other spanning tree.

### <span style="color:gold">Example</span>

Our initial graph

![image](/notes/eecs281/images/mst3.png)

A valid spanning tree, but not an MST

![image](/notes/eecs281/images/mst4.png)

An MST

![image](/notes/eecs281/images/mst5.png)

## <span style="color:orange">Algorithms for finding spanning trees</span>

### <span style="color:gold">Prim's Algorithm (greedy)</span>

Best for **dense** graphs

We separate vertices into two groups:

- "innies" are vertices that are present in your partial MST at any point in time
- "outies" are other vertices

Iteratively add the nearest outie, converting it to an innie.

#### <span style="color:yellow">Algorithm</span>

1. Find the closest (meaning smallest weight) out-vertex $X$
2. Mark $X$ as "in"
3. Update nearest for each out-vertex $Y$ that is closer to $X$ than $Y$'s old nearest.

#### <span style="color:gold">Complexity</span>

| Data Structure Implementation                                | Time Complexity                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Adjacency matrix as graph; **linear search** to find next vertex to add. | $O(V^2)$                                                     |
| Adjacency list as graph; use **binary heap** to determine next vertex to add. | $O((V+E \log V))$, since $\log E < 2 \log V$ this is the same as $O(E \log V)$ |
| Adjacency list as graph; use **Fibonacci heap** to determine the next vertex to add (Fib heap has $O(1)$ amortized update element) | $O(E + V \log V)$                                            |



#### <span style="color:color:gold">Example</span>

Starting with this graph

![image](/notes/eecs281/images/prim1.png)

We can use a Prim Table

$v$ = a vertex

$k_v$ = a bool basically asking, is this vertex inside the MST?

$d_v$ = how far from the nearest vertex inside the MST?

$p_v$ = what is the nearest vertex inside the MST?

| $v$   | $k_v$ | $d_v$    | $p_v$ |
| ----- | ----- | -------- | ----- |
| $v_1$ | $F$   | $0$      |       |
| $v_2$ | $F$   | $\infty$ |       |
| $v_3$ | $F$   | $\infty$ |       |
| $v_4$ | $F$   | $\infty$ |       |
| $v_5$ | $F$   | $\infty$ |       |
| $v_6$ | $F$   | $\infty$ |       |

We start by picking a random node, we will just pick $v_1$ and mark that as true. We look at all the neighbors of $v_1$ and update their distance if necessary.

| $v$   | $k_v$ | $d_v$    | $p_v$ |
| ----- | ----- | -------- | ----- |
| $v_1$ | $T$   | $0$      |       |
| $v_2$ | $F$   | $13$     | $v_1$ |
| $v_3$ | $F$   | $\infty$ |       |
| $v_4$ | $F$   | $7$      | $v_1$ |
| $v_5$ | $F$   | $\infty$ |       |
| $v_6$ | $F$   | $\infty$ |       |

Now to find our next node, we look through the $d_v$ column and find the lowest distance such that $k_v$ is false. So we would pick $v_4$.

We mark $v_4$ as true, and then repeat the process. 

| $v$   | $k_v$ | $d_v$ | $p_v$ |
| ----- | ----- | ----- | ----- |
| $v_1$ | $T$   | $0$   |       |
| $v_2$ | $F$   | $13$  | $v_1$ |
| $v_3$ | $F$   | $6$   | $v_4$ |
| $v_4$ | $T$   | $7$   | $v_1$ |
| $v_5$ | $F$   | $4$   | $v_4$ |
| $v_6$ | $F$   | $2$   | $v_4$ |

We continue this process until every vertex has been included in the MST, i.e. $k_v = T$.

| $v$   | $k_v$ | $d_v$ | $p_v$ |
| ----- | ----- | ----- | ----- |
| $v_1$ | $T$   | 0     |       |
| $v_2$ | $T$   | 5     | $v_5$ |
| $v_3$ | $T$   | 6     | $v_4$ |
| $v_4$ | $T$   | 7     | $v_1$ |
| $v_5$ | $T$   | 4     | $v_4$ |
| $v_6$ | $T$   | 2     | $v_4$ |

![image](/notes/eecs281/images/prim2.png)

### <span style="color:gold">Kruskal's Algorithm (greedy)</span>

Best for **sparse** graphs.

Maintain a "forest" or group of trees / disjoint sets.

Iteratively select the cheapest edge in a graph, if the edge forms a cycle, don't add it. Otherwise, add it to the forest.

Continue until all vertices are part of the same set.

#### <span style="color:gold">Complexity</span>

1. We sort the edges by weight in $O(E \log E)$ time.
2. We use a disjoint-set data structure (such as union-find) to keep track of the vertices in each component.
   1. 2 find operations per edge, up to 1 union
   2. each operation takes $\alpha(V)$ time, which is almost $O(1)$.

Total time complexity is $O(E \log E)$ or $O(E \log V)$

Faster in practice than Prim's with binary heap for very sparse graphs.

### <span style="color:gold"> Dijkstra's Algorithm </span>

![image](/notes/eecs281/images/da1.png)

Dijkstra's Algorithm is very similar to Prim's except we keep track of the cumulative distance to each node. 

| Vertex | Visited | Distance from Start | Previous Vertex |
| ------ | ------- | ------------------- | --------------- |
| A      | F       | 0                   |                 |
| B      | F       | $\infty$            |                 |
| C      | F       | $\infty$            |                 |
| D      | F       | $\infty$            |                 |
| E      | F       | $\infty$            |                 |

We find the smallest unvisited vertex, which is going to be in this case. We then update the distance of the neighbors of A, then mark A true.

| Vertex | Visited | Distance from Start | Previous Vertex |
| ------ | ------- | ------------------- | --------------- |
| A      | T       | $0$                 |                 |
| B      | F       | 6                   | A               |
| C      | F       | $\infty$            |                 |
| D      | F       | 1                   | A               |
| E      | F       | $\infty$            |                 |

Now we find the smallest unvisited vertex, which is D. Now we need to look at the unvisited neighbors of D and add their edges, along with the distance from the start. If this distance is smaller than what is already known, we update the distance and previous vertex.

| Vertex | Visited | Distance from Start | Previous Vertex |
| ------ | ------- | ------------------- | --------------- |
| A      | T       | $0$                 |                 |
| B      | F       | $3$                 | D               |
| C      | F       | $\infty$            |                 |
| D      | T       | $1$                 | A               |
| E      | F       | $2$                 | D               |

We continue this process until we finish the table.

| Vertex | Visited | Distance from Start | Previous Vertex |
| ------ | ------- | ------------------- | --------------- |
| A      | T       | $0$                 |                 |
| B      | T       | $3$                 | D               |
| C      | T       | $7$                 | E               |
| D      | T       | $1$                 | A               |
| E      | T       | $2$                 | D               |

This is what our shortest path looks like:

![image](/notes/eecs281/images/da2.png)

## <span style="color:orange">Updating MSTs</span>

#### Case 1: Edge is in the MST and we are decreasing its weight

This won't change the correctness of our MST

#### Case 2: Edge is not in the MST and we are decreasing its weight

We add the new edge to the MST. This would give us $1$ cycle in our graph. 

We need to check this cycle for the edge that has the **highest** weight and remove that edge. This can be done with DFS or BFS with complexity $O(|V|)$

#### Case 3: Edge is not in MST and we are increasing its weight

This won't change the correctness of our MST, it was already excluded from our MST in the first place, so why would increasing its weight change anything?

#### Case 4: Edge is not in MST and we are decreasing its weight

We would need to detach that edge and then find which node can connect the two trees the cheapest. A new edge can be found in $O(E)$ time. 

- Traverse through the components (components meaning the disconnected subtrees) using DFS or BFS and build two hash tables for quick look-ups.
- Find the shortest edge whose ends are in the opposite components.



