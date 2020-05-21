---
title: LECTURE - Test Suite Quality Metrics
linktitle: Test Suite Quality Metrics
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

https://dijkstra.eecs.umich.edu/kleach/eecs481/lectures/se-05-testquality.pdf

Test suite quality metrics allow test suites to be compared.

## Metrics

### Line (statement) coverage

Line / statement coverage is a test suite quality metric that is the number of unique lines visited when running the test suite.

### Branch Coverage

Branch coverages counts the number of conditional branches that are reached by the test suite. 

So if true and if false branches are counted separately.

For every branch in the program we would want to write a test that hits both branches. 

Note - if you have 100% branch coverage then you will have 100% line coverage, but the converse is not necessarily true.

### Function Coverage

Function coverage counts what fraction of functions have been called.

### Conditional Coverage

Conditional coverage is a metric that counts what fraction of boolean subexpressions have been evaluated. 

So if we were to have

```python
if (a > b and b < c or a == b)
```

each condition in the expression is considered. 

Conditional coverage differs from branch coverage in that branch coverage considers the boolean result as a whole whereas conditional coverage considers each individual boolean.

### Modified Condition / Decision Coverage

Basically just function coverage + branch coverage.

## Alpha Testing

Alpha testing is done by developers.

## Beta Testing

Beta Testing is done by users. Can be considered a sampling of the space of users.

## A/B Testing

Testing which differs by one feature. Not really used for finding bugs but rather testing user experience changes.

## Mutation Testing

The quality of the test suite is related to the number of intentionally added defects it finds. 

### Defect seeding

Defect seeding is the act of intentionally introducing bugs. The defects introduce should be the same as the types of bugs that a real developer might introduce (such as typos, using != instead of ==, etc). Typically done in source code

**Mutation Testing** is basically automatic defect seeding.

## Mutation Operator

Systematically changes a program point.

For example 

if a < b becomes if a <= b or if a == b becomes if a != b.

### Mutant

A mutant is a version of the original program which is produced by applying one or more mutations. A **n-th order** mutant is the number of mutations applied to the original program.

A test suite is said to **kill** a mutant if the mutant fails a test that the original passes.