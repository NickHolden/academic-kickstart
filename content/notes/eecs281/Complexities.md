---
title: Various Complexities
linktitle: Time / Space Complexities
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

## <span style="color:orange">Binary Search Tree \<map></span>

### <span style="color:gold">Search / Insert / Deletion</span>

- Average Case: $O(\log n)$
  - A semi-balanced tree because we halve the search space each time
- Worst Case: $O(n)$
  - Stick-like tree, could have to traverse through every node

## <span style="color:orange">Hash Table <unordered_map></span>

### <span style="color:gold">Search / Insertion / Deletion</span>

- Average Case: $O(1)$
  - Good hashing function to prevent collisions.
- Worst Case: $O(n)$
  - All keys mapping to the same index, lots of rehash

## <span style="color:orange">Binary Tree</span>

### <span style="color:gold">Array Implementation</span>

#### Insert / Delete

- Average Case (insert): $O(1)$
- Worst Case: $O(n)$

#### Space

- Best Case: $O(n)$
- Worst Case: $O(2^n)$

### <span style="color:gold">Pointer implementation</span>

#### Insert / Delete

- Best Case: $O(1)$
- Worst Case $O(n)$

### <span style="color:gold">Parent / Child</span>

- $O(n)$

#### Space

- Best and Worst Case: $O(n)$

## <span style="color:orange">Binary Search Tree</span>

In general operations on BSTs are:

- Average: $O(\log n)$
- Worst: $O(n)$

### <span style="color:gold">Search</span>

- Complexity of search is $O(h)$ where $h$ is the maximum height of the tree
- Average Case (Balanced): $O(\log n)$ 
- Worst Case (Stick-like): $O(n)$

### <span style="color:gold">Insert</span>

- Complexity of insert depends on the height of the tree
- Average Case (Balanced): $O(\log n)
- Worst Case (Stick-like): $O(n)$

## <span style="color:orange">AVL Tree</span>

### <span style="color:gold">Search / Insert / Remove</span>

- Average Case: $O(\log n)$
- Worst Case: $O(\log n)$
  - This is because the tree is self balancing, so we can never have a stick-like tree

### <span style="color:gold">Sort</span>

- $O(n \log n)$ to build the tree
- $O(n)$ to do in-order traversal

### <span style="color:gold">Rotation</span>

- $O(1)$ for a single rotation, $O(1)$ for a double rotation

## <span style="color:orange">Graphs</span>

### <span style="color:gold">Adjacency List</span>

- Access Vertex: $O(1)$
- Find edge on vertex list: $O(E/V)$
- Average cost for individual vertex $O(1 + E/V)$
- Cost for **all** vertices $O(V) \cdot O(1 + E/V) = O(V+E)$





## <span style="color:orange">DFS / BFS</span>

### <span style="color:gold">Adjacency List</span>

Called for each vertex at most once $O(V)$

Adjacency List for each vertex is visited at most once and set of edges is distributed over set of vertices $O(1+E/V)$ 

Therefore, $O(V+E)$: linear with number of vertices and edges.

### <span style="color:gold">Adjacency Matrix</span>

Called for each vertex at most once $O(V)$

Adjacency Matrix row for each vertex is visited at most once $O(V)$

Therefore, $O(V^2)$: quadratic with number of vertices

## <span style="color:orange">Prim's Algorithm</span>

### <span style="color:gold">Linear Search Implementation (double nested for loop)</span>

$O(V^2)$ 

Repeat until every $k_v$ is true: $|V|$ times

Find smallest false $k_v$: $O(|V|)$

Set $k_v$ to true: $O(1)$

Each vertex $w$ adjacent to $v$ where $k_w$ is false, test distance. $O(|V|)$

### <span style="color:gold">Heap Implementation</span>

$O(E \log E)$

## <span style="color:orange">Kruskal's Algorithm</span>

$O(E \log V)$. Better for sparse graphs
