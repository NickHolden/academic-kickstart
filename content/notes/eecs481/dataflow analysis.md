---
title: Dataflow Analysis
linktitle: Dataflow Analysis
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

Dataflow Analysis is a type of static analysis. 

Notation:

$\top$ - I have visited this location, but I don't know anything about it.

$\bot$ - I have not visited this location yet.

$c$ - I definitively know the value of this variable.

# Transfer Functions

We use transfer functions to transfer a property from one statement to the the next.

Formally,

For each statement $s$ we compute information about the value of $x$ (the value/property we are interested in) immediately before and after $s$.

$C_{in}(x, s)$ = the value of $x$ before $s$. 

$C_{out}(x,s)$ = the value of $x$ after $s$.

# Types of Dataflow Analysis

## Forward Analysis

- Constant Propagation
- Constant Folding

Transfers data from right before a statement to right after the statement

Input: the value of the property before a statement

Output: the value of the property after a statement

### Rules

#### Rule 1

![image](/notes/eecs481/images/dfa1.png)

If we don't know anything about $x$ prior to the statement and $x$ is assigned to a constant $c$ then $x=c$ immediately after the statement.

$C_{out}(x, x := c) = c$ if $c$ is a constant

#### Rule 2

![image](/notes/eecs481/images/dfa2.png)

If we haven't reached $x$ prior the the statement and the statement doesn't assign anything to $x$ then we still don't know anything about $x.$

$C_{out}(x,s) = \bot$ if $C_{in}(x,s) = \bot$

#### Rule 3

![image](/notes/eecs481/images/dfa3.png)

If we don't know anything about $x$ prior to the statement and $x$ is assigned to by a function, we conservatively approximate that we still don't know anything about $x$.

$C_{out}(x, x:=f(...)) = \top$

#### Rule 4

![image](/notes/eecs481/images/dfa4.png)

If $x$ was already assigned and the statement assigns to a different variable than $x$, then $x$ remains the same. 

$C_{out}(x, y:=...) = C_{in}(x,y:=...) \text{ if } x \neq y)$



Now we can move on to the rules for when there are multiple paths $p_i$ coming in to a single statement.

#### Rule 5

![image](/notes/eecs481/images/dfa5.png)

If at least one of the paths are visited but we still don't know anything about $x$ then we don't know anything about $x$. Remember data flow analysis is conservative so $\top$ dominates.

If $C_{out}(x,p_i)=\top$ for some $i$, then $C_{in}(x,s) = \top$

#### Rule 6

![image](/notes/eecs481/images/dfa6.png)

If we have multiple paths such that $x$ is a constant and two of those are different, then we don't know anything about $x$ coming into the new statement.

If $C_{out}(x,p_i)=c$ and $C_{out}(x,p_j)=d$ and $d \neq c$, then $C_{in}(x,s) = \top$

#### Rule 7

![image](/notes/eecs481/images/dfa7.png)

If $x=c$ for at least one path and the other paths are also all $c$ or unvisited, then we can conclude (unless things change) that $x=c$.

If $C_{out}(x, p_i)=c$ or $\bot$ for all $i$, then $C_{in}(x,s)=c$

#### Rule 8

![image](/notes/eecs481/images/dfa8.png)

If $x$ is unvisited for all paths leading into a statement, then $x$ is unvisited directly before that statement.

If $C_{out}(x,p_i)=\bot$ for all $i$, then $C_{in}(x,s) = \bot$

## Backwards Analysis

- Live Variable Analysis
- Secure Information Flow

Backwards analysis transfers data from right after a statement to right before a statement. On every path of execution we want to determine if a variable thats used is unsafe.