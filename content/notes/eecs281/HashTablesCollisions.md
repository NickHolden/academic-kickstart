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

A hash table is an ADT of key, value pairs. Think of a dictionary where the keys are words and the values associated with those keys are the definitions.

## <span style="color:orange">When are hash tables good</span>

- $O(1)$ amortized average case **insertion, removal, **and **lookup**
- Good when we have a lot of distinct keys

### <span style="color:gold"> Good use examples</span>

- Storing U of M students in a hash table with the key being their UMID.

## <span style="color:orange"> When are hash tables bad</span>

- Doing lots of $<, >$ queries on data
- When the load factor is high
  - Load factor: $\frac{N}{M}$ where $N$ is the number of keys and $M$ is the table size.

#### <span style="color:gold">Bad use examples</span>

- Anything where we need a relation between data, like $k_1$ < $k_2$. 
  - We would rather use a binary search tree for this.

## <span style="color:orange"> Hashing Functions</span>

We need to make sure that our hashing function is deterministic, i.e. if we hash a key "hello" we need it to map to the same index every single time.

We also need to make sure that the index is always within our array. This is done by taking $index \mod m$ where $m$ is our table size.

## <span style="color:orange">Collisions</span>

When two keys map to the same index, this is called a **collision.** There are a few different common ways to handle collisions. We will be concerned with **Separate Chaining** and **Open Addressing** methods.

## <span style="color:orange">Separate Chaining</span>

Each table address has a linked list (or some other data structure), to which we append a key/value pair to the end.

When we hash to a certain address in an array, we insert the value into another data structure. This allows us to support densities $>1$ without rehashing, but it is slow.

## <span style="color:orange">Open Addressing</span>

A method in which we solve collision problems by **probing,** or searching through alternative locations in the array until either the target record is found, or an unused array slot is found, which indicates there is no such key in the table.

Note that when resolving collisions with $i$, we need to increment $i$ every time our collision resolution fails.



### <span style="color:gold">Linear Probing</span>

- $T(k) = (T(k) + i)$ $\mod M$ for $i = 0, 1, 2, 3, 4, ...$

1. Use a hash function to find the index for a key.
2. If that spot already contains a value, use the next available spot (move right). If the end of the array is reached, loop back to the beginning.

#### <span style="color:yellow">Example - Insert the following numbers into a hash table of size $5$ using the hash function $H(key) = key \mod 5$</span>

$10,11,12,15$

| 0    | 1    | 2    | 3    | 4    |
| ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |

$H(10) = 10 \mod 5 = 0$ 

$H(11) = 10 \mod 5 = 1$

$H(12) = 12 \mod 5 = 2$

| 0    | 1    | 2    | 3    | 4    |
| ---- | ---- | ---- | ---- | ---- |
| $10$ | $11$ | $12$ |      |      |

$H(15) = 15 \mod 5 = 0$

We can see that the $0$ index is full, so we need to continue moving right until we have an available spot. After resolving the collision, our hash table looks like this

| 0    | 1    | 2    | 3    | 4    |
| ---- | ---- | ---- | ---- | ---- |
| $10$ | $11$ | $12$ | $15$ |      |

### <span style="color:gold">Quadratic Probing</span>

- $T(k) = (T(k) + i^2) \mod M$ for $i = 0, 1, 2, 3, 4, ...$

#### <span style="color:yellow">Example - Insert the following numbers into a hash table of size $7$ using the hash function $H(key)=key \mod 7$</span>

$76,40,48,5,20$

| 0    | 1    | 2    | 3    | 4    | 5    | 6    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |      |      |

We insert our first value $76$ 

$H(76) = 76 \mod 7 = 6$ which is empty, so we just place our key in slot 6.

| 0    | 1    | 2    | 3    | 4    | 5    | 6    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |      | $76$ |

Now $40$, $H(40) = 40 \mod 7 = 5$ which is empty, so we just place our key in slot 5.

| 0    | 1    | 2    | 3    | 4    | 5    | 6    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      | $40$ | $76$ |

$H(48) = 48 \mod 7 = 6$ we have a collision, so we need to use our quadratic probing function with $i=0$

$T(48) = 6 + 0^2 \mod 7 = 6$, which is still a collision, so we need to increment our $i$ value.

$T(48) = 6 + 1^2 \mod 7 = 49 \mod 7 = 0$ which is open, so we can place $48$ into slot 0.

| 0    | 1    | 2    | 3    | 4    | 5    | 6    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| $48$ |      |      |      |      | $40$ | $76$ |

Now, $H(5) = 5 \mod 7 = 5$ which is a collision, we will start $i$ at $1$ this time because we know the result will not differ by adding $0$. 

$T(5) = 5 + 1^2 \mod 7 = 6$ which is a collision, so we need to increment $1$ and try again.

$T(5) = 5 + 2^2 \mod 7 = 9 \mod 7 = 2$ which is open, so we can finally place $5$ in slot 2.

| 0    | 1    | 2    | 3    | 4    | 5    | 6    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| $48$ |      | $5$  |      |      | $40$ | $76$ |

Finally, we will need to quadratic probe our last value up until $i=2$ giving us a final table of

| 0    | 1    | 2    | 3    | 4    | 5    | 6    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| $48$ |      | $5$  | $20$ |      | $40$ | $76$ |

### <span style="color:gold">Double Hashing (less likely to show up on the exam)</span>

In double hashing we basically use the $T(k)$ hash function starting with $i=0$ and on our first collision we increase $i.$

- $T(k) = (T(k) + i \cdot T'(k)) \mod M$ for $i = 0, 1,2,3,4,...$
- $T'(k) = q - (T(k) \mod q)$ where $q$ is prime and $q < M$ where $M$ is the table size.

#### <span style="color:yellow">Example - Insert the following key, value pairs using double hashing where $q=5.$ Use the first character in the string for your hash value.</span>



1. banana, yellow
2. blueberry, blue
3. blackberry, black
4. cranberry, red
5. apricot, orange
6. lime, green

| **Index** | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    |
| --------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| **Key**   |      |      |      |      |      |      |      |      |      |      |
| **Value** |      |      |      |      |      |      |      |      |      |      |

First we insert pair banana. $H(1)$ = $1 \mod 10 = 1$

| **Index** | 0    | 1      | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    |
| --------- | ---- | ------ | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| **Key**   |      | banana |      |      |      |      |      |      |      |      |
| **Value** |      | yellow |      |      |      |      |      |      |      |      |

Next we insert blueberry, but we get a collision. Therefore, we resolve the collision using our secondary hashing function.

$T'(k) = 5 - (1 \mod 5) = 5 - 1 = 4$

Now, we find $T(k)$ with $1 + 1 \cdot 4 = 5$ 

| **Index** | 0    | 1      | 2    | 3    | 4    | 5         | 6    | 7    | 8    | 9          |
| --------- | ---- | ------ | ---- | ---- | ---- | --------- | ---- | ---- | ---- | ---------- |
| **Key**   |      | banana |      |      |      | blueberry |      |      |      | blackberry |
| **Value** |      | yellow |      |      |      | blue      |      |      |      | black      |

We get another collision with blackberry, but we know that $i=0$ and $i=1$ won't work, because we already used them for 'b'.

So, $T'(k) = 4$ and $T(k) = 1 + 2 \cdot 4 = 9$

We can fill in the rest of our table in the same way, giving us a final table of

| **Index** | 0       | 1      | 2         | 3     | 4    | 5         | 6    | 7    | 8    | 9          |
| --------- | ------- | ------ | --------- | ----- | ---- | --------- | ---- | ---- | ---- | ---------- |
| **Key**   | apricot | banana | cranberry | lime  |      | blueberry |      |      |      | blackberry |
| **Value** | orange  | yellow | red       | green |      | blue      |      |      |      | black      |

## <span style="color:orange">Hashing Complexities</span>

Time complexities for **insertion/search.**

### <span style="color:gold">Separate Chaining</span>

- Best: $O(1)$
- Worst: $O(n)$
  - All the keys hash to the same index
- Average: $O(n/m)$
- Amortized $O(1)$

### <span style="color:gold">Linear Probing</span>

- Best: $O(1)$
- Worst: $O(n)$
- Average not needed for exam

