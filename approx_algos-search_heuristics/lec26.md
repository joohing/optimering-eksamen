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
there 
