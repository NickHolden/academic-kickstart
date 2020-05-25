---
title: Static Analysis
linktitle: LECTURE - Static Analysis
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

https://dijkstra.eecs.umich.edu/kleach/eecs481/lectures/se-09-static.pdf

In static analyses we don't run the program. 

Static analyses usually focuses on defects that result from inconsistentcy following simple, mechanical design rules:

- Security: buffer overruns, input validation
- Memory safety: null pointers, initialized data
- Resource leaks: memory, OS resources
- API protocols: device drivers, GUI frameworks
- Exceptions: arithmetic, library, user-defined
- Encapsulation: internal data, private functions
- Data races: two threads, one variable

## Abstract Syntax Tree

An AST is a tree representation of the syntactic structure of the source code. Records only semantically relevant information.

![image-20200523171803211](/home/nick/.config/Typora/typora-user-images/image-20200523171803211.png)

## Dataflow Analysis

Dataflow analysis is a technique for gathering information about the possible set of values calculated at various points in a program.

Dataflow analysis algorithm must terminate even if the input program loops.

- this is one source of imprecision.

Static analysis are conservative. If the analysis depends on whether or not a property P is true, then we want to know either P is definitely true or we don't know if P is true. 

It is **always** correct to say "don't know."

We must think about the software engineering process. For example

Bug finding analysis for developers vs bug finding analysis for airplane autopilot.

**Developers**: Devs hate 'false positives' so our conservative approach here would be to only report when we know definitively if there is a bug or not.

**Airplane autopilot**: Safety is critical, so if we don't know for sure, we would give a warning, erring on the side of caution.



$\top$ - can't be certain about the statement

$\bot$ - haven't yet visited the statement (unreachable code)

$c$ - specific integer value (constant)

