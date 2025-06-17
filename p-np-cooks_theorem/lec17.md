# Lecture 17

Min gut laegger ud med at forklare boolske funktioner.

## DNF & CNF

Disjunctive and conjunctive normal form.

CNF is something like (this or that or NOT that) AND (thus or thas or NOT thoz)

DNF is the "reverse": (this and NOT that and that) OR (thus and thas and NOT
thoz)

So a CNF is a conjunction of clauses that are disjunctions of literals. A DNF is
a disjunction of terms, which are conjunctions of literals.

You can convert between these of course. Any function on $n$ variables can be
described by a DNF with $s$ terms of length $n$ and a CNF of $t$ clauses of
length $n$. For these $s$ and $t$, $s + t = 2^n$.

## The SAT problem

Is a boolean function in CNF representation satisfiable (outputs true)?

SAT is in NP (free fact) and we know from Cook's theorem that it's NP-hard as
well, so since it's in NP and it's NP-hard, we know that SAT is in NPC.

## (Boolean) Circuits

A circuit is a DAG, and nodes are called gates. Gates: inputs, constants, not,
copy, and, or. In-degrees obvious, if you don't know them too bad.

There are also $m$ output gates.

## Cooked Theorem

CIRCUIT SAT is NP-hard, and reduces to SAT. Therefore, since all NP-problems
reduce to CSAT which reduces to SAT, SAT is NP-hard.

## Circuit SAT (CSAT)

Given a circuit, is it satisfiabililty?

I ain't writing anymore for this one my guy
