---
title: Exam Review Notes
linktitle: Exam Review Notes
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

## ./configure, CC, CLAGS, how these tie together

- Build automation system, configure the project to use some compilation settings.

### ./configure

### CC

### CFLAGS

### How these tie together

### What is GDB

## Software Engineering Narrative

### Process reduces risk, increases efficiency

#### Agile Development

Frequent stand up meetings, sprints.

#### Spiral 

"less frequent" delivery of prototypes, continuous re-evaluation of things like requirements, design, and implementation.

#### Waterfall

Distinct phases

- Requirements, Design, Implementation, Testing, Maintenance

### Measurements help reduce risk, but are subject to validity limitations

Measurements can give you a first order approximation, but measurements used alone are not effective and can create perverse incentives.

We try to approximate things like maintainability, readability, etc using measurements.

Halstead Volume, Cyclomatic Complexity, Lines of Code

- Construct Validity / Predictive Validity issues

#### Perverse incentives

If a manager was to give bonuses for every commit made, developers are incentivised to make a bunch of commits rather than quality commits.

### Maintenance is expensive

Maintenance takes the majority of budget.

Maintenance gets more expensive the further along you are in a project. It is much more expensive to catch bugs later on rather than in early phases of software development cycle. 

### Testing is critical

Testing is an imperfect sampling, you approximate the input space or you approximate end user behavior, but we cannot guarantee the absence of bugs - just give confidence that your program adheres to the specification.

## Testing and coverage

### What is a test

- Set of inputs and an oracle, and then a comparator. The comparator verifies that your programs output matches the oracle.

### What is Statement / Branch / Path Coverage

Statement coverage is how many statements in the program are reached by test cases.

Branch coverage counts the number of conditional branches that are reached by a test suite. True and false branches are counted separately.

Path coverage counts the number of linearly independent paths taken by the test suite.

- A path is the single set of branches taken or not taken during a program execution.

### What is a path predicate

Assignments to variables that force a path to be executed.

## Mutation Testing and Invariant Detection

### What are useful program invariants

An invariant is a predicate that is always true on every program run.

A true program invariant is one that can be falsified by a mutant. 

### What are n-order mutants



### Why will changing a program result in falsifying or keeping a candidate invariant



