# What Is Targeted Internal Parallelization for Read-Only Operations?

## Overview

**Targeted Internal Parallelization** is a strategy used in Missions to
maximize efficiency while avoiding the codebase conflicts that arise
when multiple agents write code simultaneously.

Instead of allowing every task to run in parallel, Missions carefully
distinguish between **write operations**, which modify the codebase, and
**read-only operations**, which only gather or analyze information.

This selective use of parallelism enables high performance without
sacrificing software quality.

------------------------------------------------------------------------

# Why It Is Needed

When multiple agents write code at the same time, they can:

-   Overwrite each other's changes
-   Create merge conflicts
-   Duplicate implementations
-   Make inconsistent architectural decisions
-   Increase coordination overhead

These problems often outweigh the speed gains of full parallel
execution.

To avoid them, Missions execute **all write operations serially**.

------------------------------------------------------------------------

# How Targeted Internal Parallelization Works

The Mission architecture divides work into two categories.

## Write Operations (Serial Execution)

Tasks that modify the shared codebase are executed **one at a time**.

Examples include:

-   Writing production code
-   Implementing new features
-   Editing project files
-   Creating Git commits
-   Applying code changes

Only one Worker or Validator is allowed to perform these operations at
any given time.

------------------------------------------------------------------------

## Read-Only Operations (Parallel Execution)

Tasks that only read information can safely run simultaneously because
they do not alter the project's shared state.

Common examples include:

-   Searching the codebase to understand existing logic
-   Researching APIs and documentation
-   Conducting code reviews
-   Gathering project information
-   Analyzing existing source code

Since these activities do not modify files, multiple agents can perform
them concurrently without interfering with one another.

------------------------------------------------------------------------

# Why This Approach Works

Combining serial writes with parallel reads provides the best balance
between speed and reliability.

## Faster Information Gathering

Multiple agents can simultaneously explore different parts of the
project, reducing research time.

## No Codebase Conflicts

Only one agent modifies the codebase, preventing merge conflicts and
overwritten work.

## Lower Coordination Overhead

Less effort is spent resolving inconsistencies between concurrent
implementations.

## Higher Long-Term Accuracy

Although serial implementation may seem slower initially, it
significantly reduces the overall error rate during long-running
autonomous projects.

------------------------------------------------------------------------

# Read vs. Write Operations

  Serial Write Operations   Parallel Read-Only Operations
  ------------------------- -------------------------------
  Writing code              Searching the codebase
  Editing files             Researching APIs
  Implementing features     Reading documentation
  Creating Git commits      Conducting code reviews
  Modifying project state   Gathering project information

------------------------------------------------------------------------

# Long-Running Autonomous Missions

For software engineering tasks that may continue for several days,
avoiding code conflicts becomes more valuable than maximizing raw
execution speed.

Targeted Internal Parallelization enables:

-   Stable autonomous workflows
-   Consistent architectural decisions
-   Reduced error rates
-   Compounding correctness over time
-   Reliable long-term project execution

------------------------------------------------------------------------

# Key Takeaways

-   Targeted Internal Parallelization applies parallelism only where it
    is safe.
-   Code-writing tasks are executed serially to prevent conflicts.
-   Read-only tasks are heavily parallelized to maximize efficiency.
-   This balance minimizes coordination overhead while maintaining a
    consistent codebase.
-   Over long-running software projects, the strategy produces more
    reliable and maintainable results than full parallel execution.
