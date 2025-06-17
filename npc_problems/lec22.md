# Lecture 22 - SET COVER and friends (ew)

Introduces first some new problems.

## Exact cover by 3-sets

Given a finite set of size n and a set of subsets such that the union of all of
those is equal to the original, can we find a subset, C, of the set of subsets
such that the amount of sets in C is a third of n, and also the union of all
sets in C is equal to the original set? Best explanation, hell yeah

## Set cover

Can we cover the set U using less than B sets from the family of subsets F?

## Set packing

Can we find at least K disjoint subsets in F?

XC3 reduces to the two others.

## Tripartite matching

Given 3 sets of size n, and constructing triples through the cartesian product
of all of them, can we find a subset of the triples of size $n$ such that none
of the triples have the same element in them (i.e. b, g, h for each must be
completely unique)?

Also known as 3DM, 3-dimensional matching.

3DM reduces to XC3.

All of these are NP-complete (except for 3DM? probably not except).
