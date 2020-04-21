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

- Visit the left subtree, parent, right subtree

In-order Traversal for the above tree: 4, 2, 5, 1, 3

## Post-order

- Visit the left subtree, right subtree, parent

Post-order Traversal for the above tree: 4, 5, 2, 3, 1

## Level Order

Breadth-first search, uses a queue normally.

Level Order Traversal for the above tree: 1, 2, 3, 4, 5





