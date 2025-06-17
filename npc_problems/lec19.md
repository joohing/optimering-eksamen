# Lecture 19 - SAT variants

Starting out with a few tools for NP-hardness

## NP-hardness establishing

Lemma: if $L_1$ is NP-hard and $L_1$ reduces to $L_2$, then $L_2$ is also
NP-hard because then all NP problems can be reduced to $L_2$ through $L_1$,
which is the definition of NP-hardness.

To reduce we usually construct a polynomial time computable map such that $x$
belonging to the one language implies that $r(x)$ belongs to the other.

We can then prove correctness using "solution mappings" such that we can use
$r(x)$, $g_1(x, y)$, $g_2(x, y)$ to "go both ways" with the mapping. Kind of
like property based testing of a list reverse function (rev(rev(list)) == list).

TODO some weird slides here, not sure to do with the information, closer
research needed.

## Davis-Putnam procedure

Input CNF formula, output whether it's satisfiable.

Pick a variable, suppose it's true. Simplify (removes $x_i$ from $F$). Do it
again. If true was returned, when we good. Else assign false to the variable
instead, and try again.

## Implication graphs

As an example, a 2CNF (CNF with two in each term). There's a nice example in the
visualizer PDF. E.g. $\not x_1 \lor x_2$ results in nodes $x_1$ and $x_2$ (and
their not variants as well), where $x_1$ has an arrow to $x_2$ - this is because
if $x_1$ is true then the negation causes it to be false, implying that $x_2$
must be true. Do that for all the terms and you've got a $G(F)$. LMAO

Ending with a useful (although obvious) theorem: $F$ is satisfiable IFF there is
no variable such that its negation implies itself, and itself implies its
negation.

One of these would work. E.g. if its negation implies itself, then just assign
true to the variable (false won't work for obvious reasons). If a variable
implies its own negation, assign false to it (assigning true would mean it
should imply its negation, which would evaluate to false - a contradiction).

Both doesn't work because if the negation implies the variable and the variable
implies the negation, then that formula isn't satisfiable. You can't assign true
- that would imply the negation, i.e. that the variable is false, and you can't
  assign false since that would imply that the variable is true. So you are
screwed in that case.

TODO: Weird "gadget" thing on last slide, figure that out.
