# Network Flow Models and Flow Algorithms

Based on lectures 9, 10, 11, 12, 13

- 9: TUM LPs, min-cost flows.
- 10: Max (s, t)-flows.
- 11: Primal/dual network simplex.
- 12: FF, Edmond-Karps algos for max flow.
- 13: Cycle cancelling algo.

- Networks
- Flows
- Min cut/maxflow
- Residuals/FF algo

## Overview of the presentation

What is a network? D = (N, A) DAG.

What is a flow? Value of flow? Source, sink. Balance zero for all else. Arc
constraints: positive $l_j \leq u_j$.

Min cost: feasible flow minimizing sum of arc cost times flow at each arc.

Max (s, t)-flow: find feasible flow maximizing balance of source ($|x|$).

(s, t)-cut. Min-(s, t)-cut: find cut minimizing sum of capacities on edges
between them. Theorem: min cut solution is max cut solution.

Residual flows. Augmenting paths: add delta to forward edges, subtract it from
backward edges. Ford-Fulkerson: start with zero flow, add augmenting paths while
they exist.
