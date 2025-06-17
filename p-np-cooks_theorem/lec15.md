# Lecture 15

In this lecture we get an introduction to the concept of P vs NP.

## Reductions of the things we've learned so far

Max flow can be reduced to min cost flow, which can be reduced to linear
programming, which can be reduced to Mixed ILP (which I guess is just ILP with
the relaxed-LP solutions, Branch-and-Cut stuff etc.).

MILP was exponential, but we actually found efficient, polynomial time
algorithms for the others. TSP was reducible to MILP.

Now the question is: Can TSP be reduced to ILP instead, since that is more
efficiently solvable? The answer is: not unless P=NP.

## What is NP-completeness?

A mathematical tool that allows us to make statements about whether somthing can
be solved efficiently, i.e. by algorithms that, in the worst case, run in
polynomial time.

Analogous to berlog, where we had to reason about the decidability of problems.
However here, we rely on an unproven assumption of $P\neq NP$ to draw
conclusions about whether efficient algorithms exist.

Like in undecidability, the main utility arises from the fact that we can reduce
between instances of problems (reductions). So we can reduce something to
something else, then see that it is/isn't solvable efficiently.

Examples of undecidability are HALT and PCP (post correspondance problem: can a
given set of string pairs be concatenated to form identical strings). These can
be reduced to one another.

## K-coloring

You know what K-coloring is. It's a yes/no problem, where answers are easy to
verify - just try them out. But you can only say "yes" for certain when the
answer is yes, you can't say no for certain - since there may be another way
that you just haven't found.

Instead, in order to fully say "No" to some K-colorability problem, we would
have to check all combinations - an exhaustive search. This characteristic is
shared across the problems in NP.

An important distinction is exhaustive vs combinatorial exhaustive - think
Branch-and-Cut, where we were able to prune many useless branches of
computation. Combinatorial exhaustive search is when you have a way to limit the
exhaustive search to a smaller space using heuristics (home cooked explanation).

## How to use P vs. NP

Good application: If P is different from NP, then some guy's algorithm for the
Travelling Rizzler's Problem is incorrect.

Bad application: All electron apps are bad applications. Also "The TSP problem
is NP-hard so it can't be solved" - WRONG! Solvable in exponential time $\neq$
not solvable.

## What's a language?

Here is the weird, out-of-touch, computer science way to define languages:

A language is any bitstring (subset of ${0, 1}*$). A language implies a decision
(yes/no) problem among instances of bitstrings - if an instance is in the
language, answer yes, else no.

This means real numbers are not representable by any language - which is
intentional. The NP-completeness model is not intended to capture model 1,
rather model 2 (with the bits and the bytes).

One thing to notice is that all inputs are legal in this representation - If
they are malformed i.e. not a bitstring, they are simply lumped in with the
"No" answers.

## Language stand-in

$L_f$ is the stand-in for $f$. It has an efficient algorithm if, and only if,
$f$ has an efficient algorithm. Since that is the case, we can use the stand-in
(even though it may be easier to solve than the original problem) to reason
about the existence of certain types of algorithms for $f$.

## What is P and NP?

Sets of languages (sets of sets of bit strings). Each language represents a
decision problem of "does this input belong to the language".

P is then the class of languages that are decided by a Turing machine that runs
at most polynomial steps in the input length (i.e. the length of the bitstring
is the $n$ here).

Why use Turing machines? We can model any decision problem that can be solved by
some mechanical procedure with a Turing machine. Additionally, a decision
problem can only be solved in polynomial time by some sequential model of
computation IF AND ONLY IF it can be solved in polynomial time by a Turing
machine.

## Polynomial time computable maps

A map from one bitstring to another is polynomial time computable if the length
of the output is bounded (for all inputs $x$) by some polynomial on the input size.

## Maps and polynomially equivalent representations

As we know from this course and others, we can map between representations. E.g.
for a graph, you can, instead of a list of edges between the nodes, have an
adjacency matrix. We call these two representations polynomially equivalent if
there is a polynomial-time computable map between them.

## Robust representations

This result is useful to transitively claim things about polynomially equivalent
representations: if two representations are polynomially equivalent and one is
in $P$, then the other is also in $P$.
