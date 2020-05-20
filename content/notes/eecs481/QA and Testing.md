---
title: Quality Assurance
linktitle: LECTURE - QA and Testing
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

https://dijkstra.eecs.umich.edu/kleach/eecs481/lectures/se-04-qatesting.pdf

## Quality Assurance

QA is a way of **preventing** mistakes and defects throughout the development and delivery process at every stage to maintain a desired level of quality. 

QA is focused on preventing issues while quality control (QC) is focused on detecting issues.

### External Quality (customer facing)

You want external quality so that customers actually want to buy your product.

Making sure the program

- Does the right thing - i.e. the program follows the spec
- Doesn't have security issues / crashes / makes sure errors are handled
- Bugs don't make their way back in

### Internal Quality (developer facing)

You want internal quality so that programs are readable and easy to maintain.

Ways to increase internal quality

- Code review
- Static analysis tools and linters
- Following programming idioms and design patterns
- Following local code standards

## Software Testing

Software testing is an investigation to provide stakeholders with information about the quality of the software or service. 

Testing does not prove the absence of bugs (unless your input space is finite) but gives confidence that the implementation sticks to the given specification.

### Fuzz Testing

Fuzz testing (testing with random inputs) helps find segfaults, memory errors, crashes, etc but does not help determine if the implementation is correct.

### Regression Testing

Regression testing confirms that a recent change has not affected existing features. This is just basically rerunning your current test suite when you have implemented a new feature and making sure the tests still pass. 

Good practice for regression testing - when you fix a bug, add a test case that exposes that bug. This is to ensure that new features don't reintroduce bugs.

### Unit Testing

Unit testing tests a specific function or individual unit. Used to validate that each function or feature is implemented correctly.

### xUnit

xUnit is the collective name of several unit testing frameworks.

### Integration Testing

Integration testing combines and tests individual components or modules as a group to verify they are working correctly together. 

### Mocking

Mocking simulates a real object to use in tests. This object is used to test behavior of other objects. This is sometimes used when API calls are expensive.

### Test Driven Development

TDD relies on repetition of short development cycles. Requirements are turned into test cases and then code is written so that those test cases pass.



