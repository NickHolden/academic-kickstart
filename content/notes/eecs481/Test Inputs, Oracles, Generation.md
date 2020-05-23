---
title: LECTURE - Test Inputs, Orcales, and Generation 
linktitle: Test Inputs, Orcales, and Generation
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  481:
    parent: QA
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
# weight: 1


---

https://dijkstra.eecs.umich.edu/kleach/eecs481/lectures/se-06-inputsoracles.pdf

## Test Cases

A test case has 3 components

- Inputs (or data)
- Oracles (expected output)
- Comparator (diff, etc)

```bash
./prog < input > output; diff -b output oracle
```

In this case, **input** is the test input data, **diff** is the comparator, and **oracle** is the expected output that we are comparing our output with using the diff comparator.

### Comparator

Many test cases use a 'must match exactly' comparator (eecs 281 does this).

## Paths vs Branches

Paths are the number of ways to go through a program. This is similar to a path in a random walk, except the ending location is the end of the program. 

For example, given this program

```python
if a < b:
    this()
else: 
    that()
if c < d:
    foo()
else:
    bar()
if e < f:
    x()
else:
    y()
```

We have 8 paths in this program - 

```python
this()    this()  this()  this()  that()  that()  that()  that()
foo()     foo()	  bar()	  bar()	  bar()	  bar()   foo()	  foo()
x()		  y()     x()	  y()	  y()     x()     x()     y()
```

Notice that if we have $N$ sequential if statements, we have

- $2N$ branch edges (which we could cover in 2 tests, one always goes left and one always goes right)
- $2^N$ paths (meaning we need $2^N$ tests to cover all these branches).

## Path Testing

We can use a **path predicate** to generate a test. 

### Path Predicate

A path predicate is a boolean formula over the program variables that is true when the program executes the given path.

For the program above, one of our paths is that() bar() x(), or False, False, True.

The **path predicate** for that path is $$a\geq b \text{ and } c \geq d \text{ and } e < f$$. When this path predicate is true, the control flow follows the path we want.

In order to get this path predicate, we can solve a systems of equations to get a satisfying assignment.

### Satisfying Assignment

A satisfying assignment is a mapping from variables to values that makes a predicate true.

A path predicate may have multiple satisfying assignments. 

One satisfying assignment for the above path predicate is $a=5,b=4,c=3,d=2,e=1,f=2$

## Test Oracles

The **Oracle Problem** is the difficulty and cost of determining the correct test oracle for a given input.

An **implicit oracle** is one associated with the language or architecture (e.g. don't segfault or loop forever.)

### Invariants

An invariant is a predicate over a program expressions that are true on every run. 

A good invariant should **always **be able to be falsified by a mutation. 

- If its not falsifiable, the invariant was just a coincidence and isn't going to tell you anything.