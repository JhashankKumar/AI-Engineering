# Why Do Missions Run Features Serially Instead of in Parallel?

## Overview

At first glance, running multiple AI agents in parallel appears to be
the fastest way to build software. For example, running **10 agents
simultaneously** might seem like it should deliver **10× the
productivity**.

However, for complex software engineering, **full parallelization often
reduces overall efficiency and software quality**.

Missions therefore execute **feature implementation serially** while
reserving **parallelism for read-only operations**.

------------------------------------------------------------------------

# The Problem with Full Parallelization

When multiple agents modify the same codebase simultaneously, several
issues arise:

-   Merge conflicts
-   Duplicate work
-   Inconsistent architectural decisions
-   Conflicting implementations
-   Increased coordination overhead
-   Excessive token consumption

Instead of accelerating development, these conflicts consume time and
computational resources, reducing the benefits of parallel execution.

------------------------------------------------------------------------

# Why Missions Choose Serial Execution

To avoid these problems, Missions enforce **serial execution** for
implementation tasks.

At any given time:

-   Only one Worker writes production code.
-   Only one Validator performs implementation-related verification.

This ensures that each feature is completed before the next one begins,
preserving architectural consistency throughout the project.

------------------------------------------------------------------------

# Targeted Internal Parallelization

Although feature implementation is serial, Missions still leverage
parallelism where it is safe and beneficial.

## Parallel Read-Only Tasks

Operations that **do not modify the codebase** can be executed
simultaneously, including:

-   Searching the codebase
-   Researching APIs
-   Reading documentation
-   Running code reviews
-   Gathering project information

Because these tasks are read-only, they introduce no conflicts while
significantly improving efficiency.

------------------------------------------------------------------------

# Benefits of Serial Feature Development

Serial execution provides several important advantages.

## Consistent Architecture

Only one implementation is introduced at a time, reducing conflicting
design decisions.

## Fewer Merge Conflicts

Since only one agent modifies the codebase, overlapping changes are
minimized.

## Lower Coordination Overhead

Less time is spent resolving conflicts between agents.

## Reduced Token Waste

Avoiding duplicate work and unnecessary retries leads to more efficient
use of computational resources.

## Higher Accuracy

Although serial execution may appear slower, it significantly lowers the
overall error rate.

------------------------------------------------------------------------

# Long-Running Autonomous Development

For Missions that execute over several days, correctness becomes more
important than raw implementation speed.

By minimizing conflicts and maintaining a stable codebase, serial
execution enables:

-   Compounding correctness over time
-   Stable long-running workflows
-   Reliable autonomous software development
-   Better overall project outcomes

------------------------------------------------------------------------

# Serial vs. Parallel Execution

  -----------------------------------------------------------------------
  Serial Feature Execution        Full Parallel Feature Execution
  ------------------------------- ---------------------------------------
  One implementation at a time    Multiple concurrent implementations

  Consistent architecture         Conflicting architectural decisions

  Minimal merge conflicts         Frequent merge conflicts

  Lower coordination overhead     High coordination overhead

  Higher long-term accuracy       Higher short-term throughput but
                                  greater error rates
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Key Takeaways

-   Missions prioritize correctness over maximum parallelism.
-   Simultaneous code writing often leads to conflicts and wasted
    effort.
-   Feature implementation is performed serially to preserve
    consistency.
-   Read-only tasks are heavily parallelized to maximize efficiency.
-   Over long-running autonomous projects, serial execution produces
    more reliable, maintainable, and accurate software.
