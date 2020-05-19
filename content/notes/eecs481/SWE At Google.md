---
title: Software Engineering At Google
linktitle: Software Engineering at Google (Fergus Henderson)
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

https://dijkstra.eecs.umich.edu/kleach/eecs481/readings/henderson-google.pdf

## 2.1 Source Repository

All development at Google happens at the head of the repository instead of branches. This is done to more quickly identify integration problems.

## 2.2 The Build System

Individual build steps must depend only on their declared inputs. 

When initiating a code review, Google has tools for automatically running a test suite. **What type of testing is this?**

## 2.3 Code Review

All changes to the main repository must be reviewed by at least one other engineer (and at least one owner of the file being modified.)


Code review is most effective as the code is being developed rather than after the fact. 

Engineers are encouraged to keep changes small.

## 2.4 Unit Testing

All code in production is expected to have unit tests. Load testing (a type of **non-functional** testing) is done prior to deployment, where teams are expected to produce a table or graph showing key metrics.

## 2.5 Bug Tracking

When sending in code reviews, engineers are prompted to associate the change with a specific issue number.

Many teams label bugs to indicate whether they have been **triaged** and what release targets the bug.