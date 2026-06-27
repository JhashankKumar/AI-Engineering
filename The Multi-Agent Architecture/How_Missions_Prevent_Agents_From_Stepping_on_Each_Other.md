# How Do Missions Prevent Agents from Stepping on Each Other?

## Overview

One of the biggest challenges in multi-agent software engineering is
preventing agents from interfering with one another while working on the
same codebase.

If multiple agents modify the code simultaneously, they can overwrite
each other's changes, duplicate work, and make conflicting architectural
decisions.

To solve this problem, Missions use **serial execution** for feature
implementation while applying **parallelization only to read-only
tasks**.

------------------------------------------------------------------------

# The Problem with Multiple Writers

When several agents write code at the same time, they commonly create:

-   Merge conflicts
-   Overwritten changes
-   Duplicate implementations
-   Inconsistent architectural decisions
-   Increased coordination overhead
-   Wasted computational resources (tokens)

Instead of accelerating development, these conflicts often slow the
overall workflow.

------------------------------------------------------------------------

# The Mission Solution: Serial Execution

Missions enforce a simple but effective rule:

> **Only one Worker or Validator is allowed to modify the codebase at
> any given time.**

This ensures that:

-   One feature is completed before the next begins.
-   Every implementation builds upon the latest project state.
-   Architectural consistency is maintained throughout development.

By allowing only a single agent to write code, Missions eliminate most
codebase conflicts before they occur.

------------------------------------------------------------------------

# Safe Parallelization

Although writing tasks are serialized, Missions still use parallelism
where it cannot create conflicts.

## Read-Only Operations

The following tasks are executed in parallel because they do not modify
shared project state:

-   Searching the codebase
-   Researching APIs
-   Reading documentation
-   Conducting code reviews
-   Gathering project information

Since these operations only read data, multiple agents can perform them
simultaneously without interfering with one another.

------------------------------------------------------------------------

# Benefits of This Approach

Using serial execution for implementation and parallel execution for
read-only work provides several advantages.

## Prevents Code Conflicts

Only one agent modifies the codebase at a time, eliminating overlapping
changes.

## Maintains Architectural Consistency

Each feature is implemented using the latest project state.

## Reduces Duplicate Work

Agents are less likely to solve the same problem multiple times.

## Improves Resource Efficiency

Fewer conflicts mean less wasted computation and fewer unnecessary
retries.

## Enables Long-Running Autonomy

Projects that run for several days remain stable because every
implementation follows a controlled workflow.

------------------------------------------------------------------------

# Serial vs. Parallel Responsibilities

  Serial Tasks                                Parallel Tasks
  ------------------------------------------- ------------------------
  Writing code                                Searching the codebase
  Implementing features                       API research
  Modifying project files                     Documentation lookup
  Feature validation involving code changes   Code reviews
  Git commits                                 Information gathering

------------------------------------------------------------------------

# Key Takeaways

-   Missions prevent agents from interfering by allowing only one agent
    to modify the codebase at a time.
-   Serial execution eliminates merge conflicts and inconsistent
    architectural decisions.
-   Read-only tasks are safely parallelized to improve efficiency.
-   This balance between serial writing and parallel reading enables
    stable, scalable, long-running autonomous software development.
