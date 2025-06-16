# Lecture 9 - How to Flow the Network and Stuff

## Total Unimodularity

If we have a totally unimodular linear program, then all basic solutions of it
are integer.

There are a ton of different ways to construct TUM matrices, won't rewrite them
here.

## Networks

A network is a directed graph. Each arc has a non-negative flow assigned to it.
A balance is the outgoing flow (sum of all flows of outgoing arcs) minus the
ingoing flow. If balance positive, then the node is a source, and a sink if
negative. If a flow has no sources or sinks, we call it a circulation.

We require that the total balance (all balances summed up) is zero.

Arcs can have flow constraints, i.e. we can only assign $x_{ij}$ to them between
$l_{ij}$ and $u_{ij}$, where $0\leq l_{ij} \leq u_{ij}$.

## Min cost problem

Assign a cost to each arc. Minimize $\sum_{ij\in A} c_{ij}x_{ij}$

### Integrality theorem

If all balance constraints, lower and upper bounds are integer, then there is a
min-cost feasible flow that is integer.
