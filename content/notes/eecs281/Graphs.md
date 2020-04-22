---
title: Graphs
linktitle: Graphs
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  example:
    parent: Example Topic
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1


---



## Definitions

### What is a graph

A graph $G = (V, E)$ is a set of vertices and edges.

Each edge can be thought of as a tuple $e_m = (v_1, v_6)$  means that there is an edge from vertex 1 to vertex 6.

### Simple Graph

Graph without parallel edges or self loops. These are the types of graphs we will be focusing on.

### Simple Path

Set of edges leading from 1 vertex to another vertex. No vertex appears twice.

### Connected

There exists a path between every pair of vertices.

![image](/notes/eecs281/images/connected.png)

### Disconnected

There exists a pair of vertices such that no edge connects them.

<img src="images/unconnected.png">

### Cycle

A special case of a simple path, except the first and last node are the same. An example of this would be my route from home to class then back home.

<img src="cycle.png">

### Directed

Vertex order of edges matter in this case. For example, if we were only able to go from home to 281 but not 281 to home, meaning that we could never skip 176 and just go home.

<img src="directed.png">

### Weighted

Edges could have weights, could be the cost to travel to a node, or distance between nodes, whatever metric you want really.

### Dense

- Adjacency matrix representation usually.

A dense graph has many edges, roughly $|E| \approx |V|^2$

### Sparse

- Adjacency list representation usually.

Fewer edges, generally $|E|$ is much less than $|V|^2$, or $|E| \approx |V|$

## Adjacency Matrix

We can represent this <img src="flights.png">

 graph as an adjacency matrix where an entry $1$ means there is an edge between the vertices and $0$ means there is not.

|         | **SFO** | **DFW** | **ORD** | **JFK** | **BOS** |
| ------- | ------- | ------- | ------- | ------- | ------- |
| **SFO** | 0       | 1       | 1       | 0       | 1       |
| **DFW** | 1       | 0       | 1       | 0       | 0       |
| **ORD** | 1       | 1       | 0       | 1       | 1       |
| **JFK** | 0       | 0       | 1       | 0       | 1       |
| **BOS** | 1       | 0       | 1       | 1       | 0       |

We could also similarly make a distance matrix where we just include the distances between the vertices. So for example, in the [SFO][DFW\] entry we would have $1846$. 

### Adjacency List

We could have an adjacency list of the flight graph above which basically just shows us what we can reach from a given node.

<img src="adjlist.png">

We would have a list like this for every possible starting node.

Note that we could also include the distance within our node structure.

## Graph Algorithms

### Unweighted vs Weighted

#### Unweighted

Generally looking if a path in general is possible from start node to end node.

#### Weighted

Generally looking for the least cost path from start node to end node.

### Depth-first search

Uses a stack

Given a graph $G=(V,E)$, we systematically explore the edges of $G$ to discover if a path exists from our source $s$ to the goal $g$. 

#### Pseudocode Algorithm

1. Mark source as visited
2. Push source to the stack
3. While stack is not empty
   1. get/pop candidate from top of the stack
   2. For each child of candidate
      1. If child is unvisited
         1. Mark child visited
         2. push child to top of the stack
         3. if child is the goal, return success
4. return failure

Use of an adjacency list or adjacency matrix depends on our underlying graph and whether it is sparse or dense.

### Breadth-first search (optimal for unweighted)

Uses a queue

Always discovers a shortest path if unweighted 

The algorithm for BFS is exactly the same as DFS except we push to the queue and grab our node from the front of the queue. 

Same complexity as DFS.

## Complexities

### Adjacency List/Matrix

Access vertex: $O(1)$

Find edge: $O(E/V)$

Average cost for individual vertex: $O(1+E/V)$

Cost for all vertices is $O(V) \cdot O(1+E/V) = O(V+E)$

### Depth-first search

#### Adjacency List

Each vertex is pushed at most once - $O(V)$

Each vertex is popped at most once, then next node is visited - $O(1 + E/V)$

Therefore, $O(V+E)$

#### Adjacency Matrix

Each vertex is pushed at most once - $O(V)$

For each vertex, vertex is visited at most once - $O(V)$

Therefore, $O(V^2)$

##### When to choose list vs matrix

We make this decision based on what our underlying graph looks like.

Recall that for **sparse** $E \approx V$ and for **dense** $E \approx V^2$

Therefore,

**Adjacency Matrix: Dense**

**Adjacency List: Sparse**











