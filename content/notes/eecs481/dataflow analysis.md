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

## Backwards Analysis

- Live Variable Analysis
- Secure Information Flow

Backwards analysis transfers data from right after a statement to right before a statement