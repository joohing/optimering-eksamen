# Lecture 20

Apparently the three graph problems are going to be the same with regard to
NP-completeness, so much so that he counted them as 1.

## Optimization version of SAT

For a target K, can we find an input that satisfies at least that for some 2CNF
instance? Still TODO: need to understand the "gadget" thing.

## NAESAT

NP-complete. Given 3CNF, can we satisfy it with each clause having
non-all-the-same literal values?

He gives some more details/proof stuff, and then definitions for graphs:
independent sets (no edge between any pair), cliques (edges between all pairs),
and vertex covers (all edges have at least one endpoint in cover).

He then gives the observation that if $I$ is an independent set in G, then $I$
is a clique in the complement of G. Then, vertices' difference from $I$ is a
vertex cover of G.

Few problems:

- INDEPENDENT SET: can we find an IS of size at least K?
- CLIQUE: can we find a clique of size at least K?
- VERTEXCOVER: can we, given "budget" B, cover the graph?
