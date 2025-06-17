# Lecture 13, last one for today

First new thing is the Klein algorithm. Din fucking kleine LMAO

## Klejner er dejlige

Klein's cycle-cancelling algorithm is for solving the min-cost flow problem.

## Simplifying assumptions

These are made in many of these algorithms.

- Network is connected (undirected)
- Uncapacitated (any capacitated network can be equivalently converted)
- No 2-cycles (just to make things simpler). A 2-cycler is a cycle with only 2
  nodes in it.

## How to do the cancellation of the cycles

The algorithm is: with $x$ a feasible flow, then while there exists an
augmenting cycle $C$, augment $x$ with it.

So basically the idea is to find cycles such that you can remove the flow in
them and save cost.

## Augmenting cycles

... are when the cost of the cycle is negative and there exists $\delta$ such
that $x + \gamma_C^\delta$ is feasible.

The maximum delta calc is a bit different from the one for the maximum for
augmenting paths - just substitute the second one ($\text{min} (x_{ij}$) for
$\text{min}_{ij\in B}(x_{ij} - l_{ij})$. So you just subtract the lower bound,
that's the only difference.

## Setting up the residual network

In this case we set the residual network $D_x$ for a feasible flow $x$ to be:

- Forward arc $ij$ with capacity $u_{ij} - x_{ij}$ when $x_{ij} < u_{ij}$. Cost
  is just $c_{ij}$.
- Backward arc $ij$ with capacity $x_{ij} - l_{ij}$ when $l_{ij} < x_{ij}$. Cost
  is $-c_{ij}$ (you can save money).

## Finding a negative cycle

Using the costs as weights, find a negative-weight directed cycle in $D_x$. Can
be solved using Bellman-Ford or Floyd-Warshall shortest path algos.

## Circulation decomp lemma

Yep, same exists for this one

## Partial Correctness

Claim: with $x$ feasible in $D$ and $x$ not min-cost flow, then an augmenting
cycle exists.

Proof: $y$ any min-cost flow, we then have mexican z in $D_x$ corresponding to
$z = y - x$ with the cost of mexican z (as defined in "Adding feasible residual
flow" - this time wrap each in the lemma with a $c(...)$ though) equal to $c(y)
- c(x)$ which is obviously negative, since $y$ is optimal and $x$ isn't. Then by
  the circulation decomposition lemma, mexican z decomposes into cycle flows and
one of these must have negative cost.

## Termination

Same as for FF.
