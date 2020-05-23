---
title: LECTURE - Dynamic Analysis Tools
linktitle: Dynamic Analysis
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

https://dijkstra.eecs.umich.edu/kleach/eecs481/lectures/se-08-dynamic.pdf

## Race Condition

A race condition occurs when two or more concurrent processes (or threads) access the same shared state without mutual exclusion (such as locking, etc) and at least one of them writes to that state. 

Race conditions are **only** a problem if one of them wants to write to a shared variable or resource. 

## Dynamic Analysis

1. Run a program 
2. In a systematic manner
   1. On controlled inputs
   2. On randomly-generated inputs
   3. In a specialized VM or environment
3. Monitor internal state of the program at runtime
   1. Instrument the program: i.e. capture data to learn more than just pass/fail.
4. Analyze the results

### Types of instrumentation

print statements in source code (reached line x)

tools like gcov, cobertura, gdb, etc that automatically change the source code

### Types of Dynamic Analysis

#### Edge Coverage

#### Path Coverage

#### Information Flow Tracking

#### Execution Time Profiling

Timing at the start and end of the function. An example of this is when we run the timing tool in visual studio like in 281.

## Components of Dynamic Analysis

**Property** of interest

- What are we trying to learn about? Why are we trying to learn about it? Example property of interest could be execution speed

**Information** related to property

- How are we learning about that property?

Mechanism for **collecting** that information

- How are we instrumenting (collecting) it?

Test **input** data

- What are we running the program on? What inputs?

Mechanism for **learning** about problem from the information

- How do we get from the logs to a meaningful answer?

## An example using branch coverage:

**Property**: Branch coverage of the test suite.

**Information**: What branch was executed when?

**Collecting**: Logging statement at each branch

**Input**: Test input data that was generated.

**Learning**: Postprocess, discard duplicates and divide the observed number by the total number.