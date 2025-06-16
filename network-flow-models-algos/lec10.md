# Lecture 10 - The most 10 out of 10 lecture

## Max (s, t)-flow problem

Find the maximum feasible flow $x$. Need to maximize $|x| = b_s(x)$, which is
just the balance of the sink node.

Can be seen as a special case of the minimum cost flow problem.

## (s, t) cuts

Given a network, an (s, t)-cut is a partition $(S, T)$ of the nodes where $s\in
S$ and $t\in T$, i.e. the sink and the source are separated in the two
partitions.

## Min (s, t)-cut problem 

Find the (s, t)-cut minimizing the sum of the upper bounds of the edges between
the nodes in $S$ and the nodes in $T$. This quantity is:

$$ u(S, T) = \sum_{i\in S, j\in T} u_{ij} $$

## Max-flow Min-cut theorem

Let $x$ be a feasible (s, t)-flow. Let $(S, T)$ be an (s, t)-cut. Then the flow
must have capacity equal to or less than the capacity of the cut.

Theorem: the maximal feasible flow for a network is equal to the capacity of the
minimum (s, t)-cut.

## Solving the min-cost flow problem

It's a special case of LP. Here: the network simplex algorithm.

Whoops, super important side note: THE FEASIBILITY OF THE DUAL SOLUTION DURING
THE PRIMAL SIMPLEX RUN IS THE TERMINATION CRITERION. I.e. the dual solution is
infeasible all the way until that point.

I ain't reading all that (may write about and understand the simplex algorithm
for networks later).
