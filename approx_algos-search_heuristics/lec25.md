# Lecture 25 - approximation algorithms for various problems

## Min weight vertex cover

Is a problem that asks you to find the cover of the graph that weighs minimum.

Can be solved by solving the LP relaxation of the ILP formulation and rounding
up values for which $ x* \geq 1/2 $, which is then a cover for the original
because (proof).

Approx ratio is 2 because (proof).

## Relaxation and Rounding in general

They are very efficient tools for achieving nice approximations to NP-hard
problems in general. Especially randomized rounding for a number $ x \in [0, 1]
$, where you round to 1 with probability $x$ and $0$ with probability $1-x$.

## MAXE3SAT

For a giant ass CNF with each clause having 3 literals, what's the max clauses
that can be satisfied by an assignment?

An approximation algo: flip a coin for each var. Can be shown to have exp.
approx ratio of 8/7, proof/analysis on slides. (Can also be derandomized.)

Better approximation ratio is not possible unless $P=NP$.

## MINSETCOVER

Find min subset of sets that covers the nodes. Greedy algo: in each iter, pick S
with largest intersect with U. Set U = U \ S.

This problem does not have a constant approx ratio - instead, ln$(n)$. Don't
know what $n$ is though LMAO.
