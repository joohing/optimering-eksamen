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

## Approximation schemes

... is what we've been talking about this entire time, LMAO.

### PTAS (Polynomial-time Approx Schemes) and FPTAS (fully)

Takes an instance of an optimization problem and a parameter $\epsilon$ and
outputs something with approx ratio $1 + \epsilon$ (or minus, if it's a max
problem).

If for every fixed $\epsilon$ the algo runs in poly time in the input length,
it's a PTAS. FPTAS if the time is also upper-bounded by a polynomial in $1 /
\epsilon$ (figure out what the intuition is here).

## An example FPTAS for Knapsack

You know what knapsack is (values, weights, max value with sum of weights less
than weight limit).

The example bases itself on some other algorithm that I don't know (todo, read
about it).

There's a table at the bottom of the slides with bounds on the approximation
ratios that cannot be surpassed at the exception of if $P=NP$.
