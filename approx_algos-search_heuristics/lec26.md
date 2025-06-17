# Lecture 26

Local search heuristics for Teaspoon. Just kidding, travelling salesman problem.
LOL!

The subtitle is "Tour construction heuristics" (oooh) "and k-OPT neighbourhoods"
(aaaah). So I'm guessing it has something to do with finding a solution that is
an aggregate of finding solutions to subsets of the problem each of size $k$
nodes.

## How to solve NP-hard problems

My guy starting out with a bombshell. "Often easier (than for P) to find the
best solution algo for NP-hard problems because you know what not to try".

He mentions branch-and-bound, branch-and-cut as "algorithmic patterns", so you
can probably apply these in a more general sense (with the rounding, finding
cutting planes etc.).

If you can't solve the problem using such an approach you may resort to
approximation algorithms. This sort of implies that approximation algorithms are
a last resort that suck harder than branch-and-so-on methods.

## Generalized local search

You can generally do a local search (locality to be defined) as such:

First, find some feasible solution to the problem instance $x$. Then, while
there is a $z$ in the neighbourhood for which the value is less than that of
$y$, assign $y := z$. So what is the neighbourhood? Here are some examples of
(exact) algorithms using local search.

- For the FF algo, a neighbourhood of a flow is any flow that can be obtained by
  adding an (s-t)-path flow (an augmenting path from source to sink I guess?) to
  the flow.
- For the Simplex algorithm, it is the adjacent vertices on the polyhedron.
  (Each time you pivot you go to a new one.)

So what do we do if we want to design a local search? We need some way to find
an initial solution, and then some way to obtain a neighbourhood structure (some
definition of "neighbourhood" for the problem).

## k-OPT

$k$-OPT swaps at most $k$ edges around such that the route is more optimal. So
the neighbourhood for a tour in TSP is all tours reachable by one $k$-OPT swap.

As such, the size of a neighbourhood of a tour in TSP is $O(N^k)$. (for $k=1$ we
have $N$ neighbours because only one possibility for swapping for each node, for
$k=2$ we have $N$ nodes to which we can route a new edge for each node, etc.)

We know that we can't get an exact solution this way (Held-Karp lower bound of
2/3), we know that if so then $P=NP$ (but it can be shown to be wrong anyways).

$k$-OPT is not super fast, each move is $O(N^3)$ because we have to compare all
of them. How to speed up? He lists some things in the slides, maybe look at them
later. Ok goodbye
