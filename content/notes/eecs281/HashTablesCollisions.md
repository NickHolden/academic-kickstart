---
title: Hash Tables and Hash Collisions
linktitle: Hash Tables and Hash Collisions
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

## When is hashing good and when is it bad

## Why would we want a hash table for something

## good at inserting, removing, finding elements in a dataset with lots of distinct keys

## bad for >, < queries on numbers

## bad when load factor is high (N / M)

- N are number of keys
- M is table size

# some good uses for hash tables

# some bad uses for hash tables

anything where you need a relation between the data

we don't want to be using these things where we are thinking of relations between objects (we would rather use binary search trees for this)

## Hash Functions

Our hash functions need to be deterministic and always fit inside of our array (this is done by mod m)

# Handling Collisions

## Separate Chaining

Store a linked list in each bucket, append key value pair to end

When we hash at a certain address in an array, we insert the value into another data structure.

## Open Addressing

When resolving the collisions with $i$ we increment $i$ every time our collision resolution fails.

### Linear Probing

- $T(k) = (T(k) + i)$ $\mod M$ for $i = 0, 1, 2, 3, 4, ...$

1. Use a hash function to find the index for a key.
2. If that spot already contains a value, use the next available spot (move right). If the end of the array is reached, loop back to the beginning.

Example: Insert the following numbers into a hash table of size $5$ using the hash function $H(key) = key \mod 5$



| 0    | 1    | 2    | 3    | 4    |
| ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |

$H(10) = 10 \mod 5 = 0$ 

$H(11) = 10 \mod 5 = 1$

$H(12) = 12 \mod 5 = 2$

| 0    | 1    | 2    | 3    | 4    |
| ---- | ---- | ---- | ---- | ---- |
| 10   | 11   | 12   |      |      |

$H(15) = 15 \mod 5 = 0$

We can see that the $0$ index is full, so we need to continue moving right until we have an available spot. After resolving the collision, our hash table looks like this

| 0    | 1    | 2    | 3    | 4    |
| ---- | ---- | ---- | ---- | ---- |
| 10   | 11   | 12   | 15   |      |



### Quadratic Probing

- $T(k) = (T(k) + i^2) \mod M$ for $i = 0, 1, 2, 3, 4, ...$
  - We can start $i$ at $1$ because we know that $0$ will fail.

### Double Hashing (less likely to show up on the exam)

- $T(k) = (T(k) + i \cdot T'(k)) \mod M$ for $i = 0, 1,2,3,4,...$
- $T'(k) = q - (T(k) \mod q)$ where $q$ is prime and $q < M.$

