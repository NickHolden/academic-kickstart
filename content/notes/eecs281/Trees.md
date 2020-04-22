---
title: Trees and Tree Algorithims
linktitle: Trees and Tree Algorithims
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

# Tree Definitions

## Balanced



## Complete

![](C:\Users\NickolasHolden\Desktop\CompleteBinary.jpg)

- All levels are filled, except maybe the last, and all nodes in the last level are as far left as possible
- A complete tree is not binary, but the binary heap is a complete tree

## Full / Proper

![](C:\Users\NickolasHolden\Desktop\FullBinary.jpg)

- Every node has either 2 or 0 children

# Traversals

![](C:\Users\NickolasHolden\Desktop\tree12.gif)

## Preorder

- Visit the parent, left subtree, right subtree

Preorder Traversal for above tree: 1, 2, 4, 5, 3

## In-order

If the In-order is the sorted data, we know that our tree is a BST.

- Visit the left subtree, parent, right subtree

In-order Traversal for the above tree: 4, 2, 5, 1, 3

We know that everything to the left of the root is in the left subtree and everything to the right of the node is in the right subtree.

## Post-order

- Visit the left subtree, right subtree, parent

Post-order Traversal for the above tree: 4, 5, 2, 3, 1

## Level Order

Breadth-first search, uses a queue normally.

Level Order Traversal for the above tree: 1, 2, 3, 4, 5

### When given two of the three traversals, how do we make the tree?

We will usually be given the In-order (or else it wouldn't be a unique tree)





