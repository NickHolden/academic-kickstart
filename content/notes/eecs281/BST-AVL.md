---
title: BST / AVL
linktitle: Binary Search Trees / AVL Trees
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  example:
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1

---

## What is a BST

A binary search tree is a tree such that the key of any node is:

-  $>$ the keys of all nodes in its left subtree
- <= the keys of all nodes in its right subtree

We use BSTs because they are very efficient to search and insert.

### Inserting

Start at the root and traverse downwards (based on the node's value) until a spot to append the node is found.

### Deletion

Three cases: Node has $1$ child, $2$ children, $0$ children.

$0$ children: Trivial. We simply just delete the node.

$1$ child: replace the node with its child and delete the child

$2$ children: replace with its in-order successor (or predecessor) and remove the in-order node from its original spot in the tree and replace it with its child if it has one.

#### Example

![image](/notes/eecs281/images/del1.png)

Delete the following: $5, 4, 8, 11$

Deleting $5:$ There is only on child, so we can simply replace the node we are deleting with its child $(6)$.

![image](/notes/eecs281/images/del2.png)

Deleting $4:$ Lets choose the in-order successor here. This is $3$ in this case. Remember the in-order successor is the next node in in-order traversal.

![image](/notes/eecs281/images/del3.png)

Deleting $8:$  Our in-order successor in this case is $6.$

![image](/notes/eecs281/images/del4.png)

Deleting $11:$ No children, so we can just delete it.

![image](/notes/eecs281/images/del5.png)

## Balancing

A BST $T$ is balanced if for every node $k$ of $T$, the heights of the children of $k$ differ by at most $1.$

It is important to try to keep trees balanced because this would make our insert and search complexities $O(\log n)$ because we will never have a stick-like tree.

## AVL Tree (self balancing BST)

![image](/notes/eecs281/images/avlrotations.png)

An AVL Tree is a self-balancing BST with worst and average case search/insert/delete complexities of $O(\log n)$

The AVL tree maintains balance with each insertion and deletion.

### AVL Invariants

- Is a BST
- Balance factor must be in the range $[-1, 1]$
  - $Balance factor(node) = Height(left subtree) - Height(right subtree)$

### Cases for Balancing (rotation)

There are $4$ different common cases for rotations. 

#### Case 1  Left subtree causes imbalance and left side of that subtree has extra node

![image](/notes/eecs281/images/avlbal1.png)

We need to balance this by rotating right at the first location where the tree is imbalanced.

![image](/notes/eecs281/images/avlbal2.png)

#### Case 2 Right subtree causes imbalance and right side of that subtree has extra node

![image](/notes/eecs281/images/avlbal3.png)

We need to balance this by rotating left at the first location, $3,$ where the tree is imbalanced.

![image](/notes/eecs281/images/avlbal4.png)

#### Case 3 Left subtree causes imbalance and right side of that subtree has extra node

![image](/notes/eecs281/images/avlbal5.png)

We need to balance this by first rotating left, which will give us a stick. Then we can fix in a similar way as before.

![image](/notes/eecs281/images/avlbal6.png)

![image](/notes/eecs281/images/avlbal7.png)

#### Case 4 Right subtree causes imbalance and left side of that subtree has an extra node

![image](/notes/eecs281/images/avlbal8.png)

We need to balance this by first rotating right, which will give us a stick. Then we can fix in a similar way as before.

![image](/notes/eecs281/images/avlbal9.png)

![image](/notes/eecs281/images/avlbal10.png)

#### Special case (a node that moves up children)

![image](/notes/eecs281/images/avlbal11.png)

We want to detach the in-order successor to our first problem node. In this case, the problem node is $2$ and our in-order successor is $3.$

![image](/notes/eecs281/images/avlbal12.png)

Once we do that, we can can rotate left, putting $4$ in the root position.

![image](/notes/eecs281/images/avlbal13.png)

Finally, we need to make $4$'s previous left child, $3,$ the right child of it's new left child $2.$

![image](/notes/eecs281/images/avlbal14.png)



## Complexities for non-self balancing BST

### Insertion / Lookup

Best case: $O(1)$ (root node)

Worst case: $O(n)$ (stick-like)

Average case: $O(\log n)$ (binary search)

### Deletion

Worst case: $O(n)$

Average case: $O(\log n)$

