---
title: Trees
linktitle: Trees
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

## <span style="color:orange"> Definitions and Terminology</span>

### <span style="color:gold">Root</span>

Node with no parents.

### <span style="color:gold">Leaf</span>

Node with no children

### <span style="color:gold">Internal Node</span>

Node with children (including the root).

### <span style="color:gold">Depth</span>

Distance from a node to the root.

### <span style="color:gold">Height</span>

Distance from a node to the lowest leaf node

### <span style="color:gold">Siblings</span>

Nodes with the same parent node

### <span style="color:gold">Balanced</span>

The difference between heights of the left subtree and right subtree is not more than $1.$

### <span style="color:gold">Complete</span>

![image](/notes/eecs281/images/CompleteBinary.jpg)

All levels are filled (except possibly the last) and all nodes in the last level are as far left as possible.

A complete tree is not binary, but the binary heap is a complete tree.

### <span style="color:gold">Full / Proper</span>

![image](/notes/eecs281/images/FullBinary.jpg)

Every node either exactly $2$ or $0$ children.

## <span style="color:orange">Traversals</span>

![image](/notes/eecs281/images/tree12.gif)

Let P = Parent, L = Left Child, R = Right Child.

### <span style="color:gold">Pre-order</span>

Explore all nodes first - top-down recursion.

Traversal Order: PLR

Pre-order traversal for the above tree: $1,2,4,5,3$

### <span style="color:gold">In-order</span>

Flattens back to original insertion sequence.

Traversal Order: LPR

If the In-order traversal is the sorted data, then we know the tree is a BST.

**We know that everything to the left of the root is in the left subtree and everything to the right of the root is in the right subtree.**

In-order traversal for the above tree: $4,2,5,1,3$

### <span style="color:gold">Post-order</span>

Explore all leaves first - bottom-up recursion.

Traversal Order: LRP

Post-order traversal for the above tree: $4,5,2,3,1$

### <span style="color:gold">Level-order</span>

This is a Breadth-first search. Traverse all nodes of a level starting at the root and traverse left to right.

Level-order traversal for the above tree: $1,2,3,4,5$

## <span style="color:orange">Tree Reconstruction</span>

### <span style="color:gold">Solving</span>

We need to take a look at the post-order or the pre-order traversal. Our root note is going to be the first element of the pre-order and last element in the post order.

From here, we can use the In-order traversal to recreate our tree because we know that everything to the left of the root in the in-order is going to be in the left subtree and everything to the right of the root will be in the right subtree.

Now, we take the left subtree's elements from the in-order/pre-order traversal and look at the post order to determine the root of that subtree. We keep doing this recursively until we have reconstructed the tree.

### <span style="color:gold">Example</span>

Given the following traversals, draw a tree that would match the traversal results.

In-order: $4,8,2,5,1,6,3,7$

Post-order: $8,4,5,2,6,7,3,1$

We know that with post order our root is going to be the last node visited. Therefore, we know our root is $1.$ Now we also know that when given the In-order traversal, everything to the left of the root is going to be in the left subtree. 

So we know that $4,8,2,5$ are going to be to the left of $1.$

![image](/notes/eecs281/images/recon1.png)

In our subtree of $4,8,2,5$ we know that $2$ is going to be our root and $5$ goes to the right.

![image](/notes/eecs281/images/recon2.png)

![image](/notes/eecs281/images/recon3.png)

We now look at the subtree $4,8$ and see that $4$ is the root of that tree.

![image](/notes/eecs281/images/recon4.png)

![image](/notes/eecs281/images/recon5.png)

Now we can go to the right side and look at the subtree $6,3,7.$ From our post-order traversal we know that $3$ is the root.

![image](/notes/eecs281/images/recon6.png)

Now we look to the in-order, and see that $6$ is left and $7$ is right, so we can finish our reconstruction.

![image](/notes/eecs281/images/recon7.png)