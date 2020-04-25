---
title: Dynamic Programming
linktitle: Dynamic Programming
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

Dynamic programming is a way to trade memory for speed by remembering the answers to every sub-problem. 

We can only use DP when we have **overlapping** sub-problems.

## Fibonacci

### Non-DP Approach

We can solve Fibonacci recursively with an $O(2^n)$ runtime

```c++
int fib(int n) {
	if (n <= 0) {
		return n;
	}
	else {
		return fib(n - 1) + fib(n - 2);
	}
}
```

This solution works. However, it takes a lot more time than is necessary because it redundantly computes values of previous sub-problems even after we have originally solved that sub-problem.

Say we were wanting to call fib(6). In order to solve fib(6) we need to call fib(5) and fib(4). Notice how on the left side of our call stack we are recalculating smaller fib values multiple times. 



We can cut out these needless calculations by using DP, storing previously calculated fib values.

### Top-down approach (Recursion)

When using a top-down approach for dynamic programming:

- When entering the function, check to see if the sub-problem has already been computed.
- Before leaving the function, make sure to store the calculation of the solved sub-problem.

This is how we would convert the Fibonacci solution in to a top down solution:

```c++
int fib(int n, vector<int>& v) {
	// Check to see if we have already calculated the nth fibonacci number
	// if it has, we simply return it
	if (v[n] != -1) {
		return v[n];
	}
	// Calculate the nth fibonacci number
	int fib_n = fib(n - 1, v) + fib(n - 2, v);
	// Store the nth fibonacci number in our memo
	v[n] = fib_n;
	// return the nth fibonacci number
	return fib_n;
}
```

Our top-down approach has reduced our solution from $O(2^n)$ to $O(n)$.



