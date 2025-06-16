# Lecture 8 let's goooo

He starts out by roasting our Branch-and-Bound implementation. We don't want to
have our code use the recursion stack to represent the branch and bound tree,
since that just wastes time. Instead we should just expand the sub problem that
has the highest relaxed solution value.

## Updated B&B

Start out with an active set consisting only of the root problem (the relaxation
of the ILP). Initialize the current best to be minus infinity. Now, while the
active set is non-empty, pop a node from the set, generate its subproblems (and
the corresponding relaxed solutions). For each of the subproblems, if the
solution is worse than the current best, break the for loop (without adding it,
so we just kill it). Else, if it's integral, set the current best equal to that.
Else add it to the active set for expansion.

This way we only expand the subproblems (branches) with potential (relaxed
solutions equal to or greater than the current best).
