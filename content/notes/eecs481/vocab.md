---
title: Vocab Cheat Sheet
linktitle: Vocab Cheat Sheet
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

## Software Process Narrative

### A/B Testing

Testing which is done with control groups where they are given two different versions of software which only differ by one change.

### Alpha Testing

Type of testing that is done usually by developers on-site.

### Beta Testing

Type of testing that is done by a small group of people done for the 

### Call-Graph Profile

Type of profiler / A report that explains time taken by each procedure (or function) and its children. This is what I used in Visual Studio in 281 to see what functions were taking the most amount of time.

### Comparator

The part of a test which compares the output to the desired output and determines if it is correct. For the most part, 281 uses **diff** to make sure that the output is exactly the same as their expected output.

### Conditional Breakpoint



### Dataflow Analysis

Type of static analysis. See dataflow analysis page for examples.

### Development Process

Divides software development into distinct phases to improve design, product, and project management.

### Dynamic Analysis

Runs an **instrumented** program in a controlled manner to collect information which can be analyzed to learn about a property of interest.

### Effort Estimation

Process of predicting the most realistic amount of effort (expressed in terms of person-hours or money) required to develop or maintain software based on incomplete, uncertain and noisy input. 

### Flat Profile

Compute the average call times, from the calls, and do not break down the call times based on the callee or the context.

### Formal Code Inspection

Team of developers meet to examine existing code, following a process to understand it and spot issues.

### Integration Testing

Tests multiple components together.

### Measurement

### Mocking

Hard coded representation of an external object used for testing. For example, if you were writing software that works with an API, but that API call was expensive, you could create a mocked object that has the same format as a response from that API would and use that for testing.

### Oracle

What is used to determine correctness of a test, the correct output.

### Passaround Code Review

Modern code reviewing - basically having someone review your github pull request.

### Perverse Incentive

Something that happens as the result of a bad software metric - for example, your code is considered better if it is longer, so you just write long garbage functions.

### Priority

It is decided that this defect much be fixed immediately.

### Quality Property

Developers are concerned about the software's performance on mobile devices.

### Readability Metric

### Risk

### Severity

The degree of impact that a defect has on the development or operation of a component application being tested.

### Software Metric

Standard of measure of a degree to which a software system or process possesses some property.

- bugs per line of code
- code coverage
- cyclomatic complexity
- halstead complexity
- lines of code
- defect removal rate
- etc

### Spiral Development

Focuses on the construction of an increasingly-complete series of prototypes while accounting for risk.

![image](/notes/eecs481/images/spiral.png)

### Threat to Validity

### Triage

Process in which each bug is prioritized based on its severity, frequency, risk, etc.

### Uncertainty

### Unit Test

### Watchpoint

A breakpoint for data rather than code. Allows the programmer to stop the code when a specified data area is being accessed for reading or writing. 

### Waterfall Model

Software development model for which the following phases are carried out **in order**

**Systems and software requirements**

- Elicited from customer, captured in a document

**Analysis**

- Derive models, schema, and business rules

**Design**

- Software architecture

**Coding**

- Development, proving, and integration of software

**Testing**

- Systematic discovery and debugging of defects

**Operations**

- Installation, migration, support and maintenance of complete systems

