# Lecture 12 - Ford-Fulkerson and stuff

## Flows

First, a path flow is the following:

For $F$ being the forward arcs and $B$ being the backward arcs along a path,
then a path flow is where for the path, the arcs in $F$ have flow $\delta$, the
arcs in $B$ have negative that, and all other arcs have 0 flow. So if $P$ is a
path from $s$ to $t$ it's an (s, t)-path.

A cycle flow is the same but runs in a cycle.

For a flow $x$ satisfying flow conservation, then the flow with a path or a
cycle flow added also satisfies it. (I guess under the assumption that there are
no capacities.)

## Augmenting paths

An augmenting path is one such that $x + \gamma_P^\delta$ is feasible where $x$
feasible, $P$ an (s, t)-path, and $\delta > 0$. I.e. you can add some flow along
the arcs covered by the path and still be feasible.

You can max the $\delta$ by the following:

$$ \delta(P) = \text{min}\Big{\text{min}_{ij\in F} (u_{ij} - x_{ij}), min_{ij\in
B}(x_{ij}) $$

I.e. the max we can increase the flow along a path is the smallest of the
bottlenecks along the forward edges (first part with the capacity minus the
flow) and the flow along the back edges (second part).

This makes sense since you can't send more than the arc capacities, but also not
more than will make the back edges have negative flow. (Arc flows are restricted
to be non-negative.)

## Ford-Fulkerson algorithm

So the ford fulkerson algorithm is basically this.

Initialize $x$ to be all-zero. While you can find an augmenting path as
described above, augment the flow $x$ by it. Then return it.

## Residual networks

Useful intermediate representation of the network after assigning a flow to it
to find augmenting paths. The residual network is:

- For forward arcs, the capacity minus the flow.
- For backward arcs, the flow. (So the backward arc kind of represents how much
  the flow can be reduced by.)

## Taking the difference between feasible flows

Define flow (mexican z) to be $y-x$ with each entry being the absolute value of
the result. Then, for $y$ and $x$ feasible, mexican z is feasible in $D_x$
(residual network of $x$) and the flow of mexican z is that of y minus that of
x.

## Adding residual feasible flow

If $x$ feasible in $D$ and mexican z feasible in $D_x$, then define flow $z$ as
the following.

- If $ij \in A$ and $ji \in A_x$, the result is mexican z difference of the two.
- If $ij \in A$ but $ji \notin A_x$, then $z_{ij} = $ the mexican z entry.
- If In the left one then it's the negative of the right one.

So you can add them together basically. So you can take a residual flow, define
$z$ from it, and then calculate $x + z$. Then it is feasible in $D$ and the flow
is the sum of the flows of $x$ and mexican z.

## Flow decomposition lemma

For all flows, there rae paths (circular and flow paths) that, when added,
result in the flow.

## Proof of partial correctness of FF algo

The claim is that if $x$ is a feasible flow in D and $x$ is not the maximum
flow, then there exists an augmenting path.

Let $y$ be any maximum flow. We can then find mexican z corresponding to $z = y
- x$ i.e. we can find a flow in the residual network. Using the flow
decomposition lemma we know that mexican z decomposes into path and cycle flows,
and there's at least one path.

## Termination of FF algo

Not guaranteed, only if all upper bounds are integers.

Why? Value of flow is integer and increasing with every iteration. It is bounded
from above. Therefore you can only do finitely many iterations before being
bounded.

The algorithm MAY TAKE EXPONENTIAL TIME, which is not good. Next up: polynomial
runtime.

## Edmonds Karp Algorithm

Simply modified FF where you always select the shortest augmenting path instead.

Don't really understand the "crucial insight" so might get back to it.
