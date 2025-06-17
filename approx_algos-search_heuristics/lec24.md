# Lecture 24

What do we do about exponential time solvable problems?

We can use approximations that are nearly correct.

## Approximations

If we have some minimization problem and an efficient algorithm that always
returns feasible solutions, the algo has approximation ratio $\rho$ if for all
instances of problems, the cost(solution found) / cost(optimal solution) is less
than or equal to $\rho$.

So basically the approximation ratio is an upper bound on how costly the
solution found is. We can thus say we have found that the approximation algo at
most "costs" 50% more than the optimal solution.

## E.g. APPROX-VERTEX-COVER

... has approximation ratio 2, since (proof)

## General trick

Since we don't know about the optimal solution, we need to reason about a lower
bound for the optimal solution usually (for minimization problems).

## Traveling Salesman Problem stuff

Here we will be looking at a special case called Metric TSP, where the triangle
inequality holds for $d(i, j) \leq d(i, k) + d(k, j)$. The triangle inequality
is basically that one, for any two sides.

### Finding an approx algo for TSP

We use minimum spanning trees. We can basically turn a minimum spanning tree
into a TSP tour. The algorithm: select some vertex. Compute a minimum spanning
tree for the graph. Then preorder walk the tree, adding to a list of vertices H
in the order in which they are encountered. The result is a hamiltonian cycle
which we return.

A hamiltonian cycle is one in which each node in the tree is visited exactly
once.

This will have approximation ratio 2. Proof:

Let W be the full walk on T, T the spanning tree, H the result of the algo, H*
the optimal tour.

The full walk will go out each branch, then in, then out the next etc. So it
will be visiting each node twice and incurring twice the cost of T (at least),
so we have

$$ c(W) = 2c(T) $$

We also know that the result of the algo must be equal to or less than the full
walk.

$$ c(H) \leq c(W) $$

We also know that the cost of the spanning tree is going to be $\leq$ the
optimum (there is no way to walk the tour spanned by the spanning tree in less
cost because the tree needs to only go one way). So we have the following chain
of inequalities:

$$ c(H) \leq c(W) \leq 2c(T) \leq 2c(H*) $$

Thus $ c(H) \leq 2c(H*) $, i.e. we have our approximation ratio of 2.

Best approx algo actually has $3/2$ approx ratio (nearly, minus a small number).

## Why only metric TSP?

Because actually approximating general TSP is NP-hard, which is kinda crazy
(even for large $\rho$, it would imply P=NP).

Can be shown by modified reduction to Hamiltonian path problem (research later).
