---
title: Algorithim Families
linktitle: Algorithm Families
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

| **Algorithm Family** | Notes                                                        |
| -------------------- | ------------------------------------------------------------ |
| Brute Force          | Guaranteed to be optimal. Very slow.                         |
| Greedy               | Picks the next best option - not guaranteed to be optimal.   |
| Divide and Conquer   | Combining solutions to subproblems (e.g. Mergesort)          |
| Backtracking         | Constraint satisfaction problems. Note that satisfying constraints is not necessarily the optimal way. |
| Branch and Bound     | Optimization problems.                                       |
| Dynamic Programming  | Save answers to overlapping subproblems to optimize time complexity. |

## <span style="color:orange">Brute Force</span>

Tries every possible combination and then uses the best one.

### <span style="color:gold">Example - Guessing an ATM Pin</span>

Assuming a $4$ digit pin, we would brute force the "solution" (i.e. get into their bank account) by trying every pin combination, so we would guess $0000, 0001, 0002, ... , 9998, 9999$ and pick the one that worked. In the worst case, it would take $10^4$ tries to crack.

**Complexity:** $O(n \cdot m)$, in the above example $n$ possible digits to guess, $m$ spots to put those digits.

## <span style="color:orange">Greedy</span>

Picks the next best choice, not guaranteed to be the optimal solution. 

### <span style="color:gold">Common greedy algorithms</span>

- Prim's Algorithm
- Kruskal's Algorithm
- Selection Sort

### <span style="color:gold">Example -  Fallout: New Vegas Knapsack Problem</span>

Suppose we are playing Fallout: New Vegas and found a treasure chest. Our bag has a weight capacity of $10$ and we want to try and maximize our total value in our bag. 

Assume each item $k_n$ has an unlimited quantity.

|            | $k_1$ | $k_2$ | $k_3$ | $k_4$ |
| ---------- | ----- | ----- | ----- | ----- |
| **Weight** | $.5$  | $2$   | $3$   | $6.2$ |
| **Value**  | $2$   | $10$  | $26$  | $50$  |

A greedy approach to this problem would be to select the highest value item we can at every point.

We first grab $k_4$, leaving us with $3.8$ capacity. Then we can pick up $k_3$ and $k_1$ leaving us with $.3$ capacity left and a total value of $78.$ 

We can see that this is a solution, but it is not an optimal solution because we could have picked $3$ of $k_3$ and $2$ of $k_1$ leaving us with $0$ capacity left and a total value of $80.$

## <span style="color:orange">Divide and Conquer</span>

1. Divide: Break a problem into subproblems of the same type
2. Conquer: Recursively solve these subproblems
3. Combine: Combine the answers

### <span style="color:gold">Common Divide and Conquer Algorithms</span>

- Binary Search
- Quicksort
- Merge Sort
- Closest Pair of Points

### <span style="color:gold">Example - </span>

## <span style="color:orange">Backtracking</span>

This is used to figure out if a certain constraint can be satisfied.

We used backtracking in Project 1 to see if we could reach the goal from a given starting location.

## <span style="color:orange">Branch and Bound</span>

We used this in Project 4 part C to quickly prune solutions that we knew wouldn't lead to an optimal solution.

### <span style="color:gold">Pseudocode</span>

```python
checknode (node v, best):
    if !is_promising(v):
        return
    if is_solution(v):
        update(best)
        return
    for each child u of v:
        checknode(u, best)
```

### <span style="color:gold">Bounding</span>

We use an **upper bound** which is the best solution that we've found so far along with a **lower bound** which is an optimistic estimate for remaining solutions in the current branch.

Lower bound + current is the best case scenario for continuing on the current branch, so **if we know that lower bound + current is less optimal than our current upper bound, we can just prune the branch off.**

### <span style="color:gold">Over-pruning</span>

Important invariants

- upper bound $\geq$ optimal solution
- lower bound $\leq$ optimal solution

If either of these are violated, the bounds are invalid. For the case of the upper bound, we will never find a solution and in the case of the lower bound we may accidentally prune the optimal solution and get a wrong answer.

## <span style="color:orange">Dynamic Programming </span>

Trades memory for speed by **remembering the answer to every subproblem** for overlapping subproblems.