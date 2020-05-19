---
title: Software Testing
linktitle: Wikipedia's Software Testing
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  example:
    parent: QA
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
# weight: 1
---

https://en.wikipedia.org/wiki/Software_testing

## Testing

Testing cannot guarantee that a program works in all cases, just that it works in specific cases. It is impossible to test every possible case in a non-trivial program.

## Test Oracles

Ways to determine whether a test passed or failed. Not always necessarily an assertion on solely the expected outcome.

## Combinatorial Test Design

Can be used to determine the number of test cases that need to be created for a desired amount of coverage.

## Static Testing

Code review and code walk-through. Does not involve running the actual software.

## Dynamic Testing

Involves running the software. Running test cases is an example of dynamic testing

## Passive Testing

Testing without interacting with the software itself. Log file analysis, etc.

## White Box Testing

This involves looking through the source code and testing specific portions of the code explicitly. 

## Black Box Testing

This involves testing a program with no knowledge of the internal implementation. 

## Grey Box Testing

A mix of both white and black box testing. An example would be similar to a strategy I used in EECS 281 for the projects - generate random test files and then looking at source code for edge cases that I want to test to get more coverage.

## Unit Testing

Testing specific sections of code. Testing a specific function would be an example of unit testing.

## Integration Testing

Testing that multiple pieces of the software work together, so basically testing multiple functions that rely on other functions to work.

## Systems Testing

Testing an entire process to make sure that it meets the requirements.

## Regression Testing

This is basically testing to ensure that when new features are added, no old bugs are introduced. A regression test suite would have tests that expose previously fixed bugs to make sure that they aren't re-introduced in the future. Type of maintenance testing

## Alpha Testing

This type of testing is usually done internally by the development team on site.

## Beta Testing

This type of testing is when a software is released to users outside of the development team and the main purpose is to expose bugs and get feedback.

## Functional Testing

Testing related to very specific portions of the code. Unit testing, integration testing, and smoke / sanity testing are all examples of functional testing.

## Non-functional Testing

This test things such as the scalability, usability, and performance of the software.

## Continuous Testing

Includes validation of both functional and non-functional tests

## Destructive Testing

Tries to get the software systems to fail. Ensures that the software will work even when given invalid or unexpected input.

## A/B Testing

Used when trying to consider what version or feature of a product is better. Uses control groups by giving one group version A and another group version B and analyzing what works better. So an example of this would be if you wanted to know what version of your shop interface caused the most people to click purchase - green button vs red button?