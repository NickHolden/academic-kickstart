---
title: AVL Trees
linktitle: AVL Trees
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

# AVL Trees

## AVL Tree Rules

Ensure that a tree stays **balanced**

- Balanced means that $|Height(left subtree) - Height(right subtree)| <= 1$ for all nodes

There are four cases

- rotate right, left, right then left, left then right

Insertion and deletions are the same as BST but they require checking all parents of a new node up to the root for balance and rotating if necessary

