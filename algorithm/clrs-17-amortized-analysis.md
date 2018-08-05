# clrs-17-amortized-analysis

CLRS Lecture 17

## What is amortized analysis?

In **amortized analysis** we try to **analyze the time required by a sequence of operations**.

There are many situations in which, even though it is possible for an **individual operation to be very expensive**, **the average cost** of an operation (taken over all operations performed) **can be shown to be small**.

Another way of saying this is that amortized analysis guarantees the average case performance of each operation in the worst case.

Note that this is very different from what is normally meant by average-case analysis; there is no probability at work here.

## Examples

1. multipop
2. binary counter
3. vector dynamic allocation

## 3 different approaches to Amortized Analysis

### Aggregate Analysis

Let T(n) be the total cost of some sequence of n operations. In the worst case the average cost, or amortized cost per operation, is T (n)/n.

In this type of analysis, **every operation will have the same amortized cost**.

### The Accounting Method

Each operation is charged an amortized cost, which can be different than actual cost.

Difference between actual cost and amortized cost is expressed in **credits**. Extra credits are placed in specific parts of data structure. Lack of credits are made up by using credits previously placed in data structure.

Different operations can have different amortized costs. **Sum of the amortized costs of a sequence of operations is ≤ total cost of the sequence**

### The Potential Method

The data structure is assigned a **potential (energy) ≥ 0** based on its current configuration.

Potential of original configuration is usually 0.
The amortized cost of an operation will be the sum of its actual cost plus the difference between the potential before the operation and the potential after the operation.

Different operations can have different amortized costs. **Sum of the amortized costs of a sequence of operations is ≤ total cost of the sequence**
