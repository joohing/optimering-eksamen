# LP Duality, Matrix Games, and Integer linear programming

Based on lectures 3 (second part), 4, 5 (part about duality), 6, 7, 8.

- 3: Duality.
- 4: Duality, complementary slackness, Farkas' lemma and strict complementarity.
- 5: Lil' bit about duality.
- 6: Game theory.
- 7: ILP, Branch-and-Bound.
- 8: Branch-and-Bound, Branch-and-Cut.

## Overview of the presentation

First, what is LP? Simplex? (Those should be quick.) Then explain how to get the
dual. Give properties about the dual problem (not necessarily Farkas', don't
really wanna go in that direction). Then start on ILP. LP relaxations.
Branch-and-Cut. Cutting planes.

- LP & Duality
- Compl slackness
- Weak/strong dual
- ILP
- Branch & Cut

## Details

Motivation for duality: can we establish nice upper bounds for the primal?

Weak/strong duality: if x, y feasible for P, D, then $c^Tx \leq b^Ty$. Strong:
they are equal if x, y optimal.

Proof of weak duality: $c^Tx \leq (y^TA)x \leq y^T(Ax) \leq y^Tb$. Values of
$A^Ty$ are same but transposed. Look at constraints, inequality follows from
those.

For solution optimality: primal and dual feasible, complementary slackness
satisfied.

Comp slack: pairs of (primal var, dual slack) and (dual var, primal slack) equal
zero. For strict, only one may be zero.

If dual infeasible, primal unbounded. Vice versa.

ILP not convex. Branch and Cut: Branch and bound combined with cutting planes.
Branch and bound: have neighbourhood, "value" for each neighbourhood. Expand
neighbourhoods with potential. Cut: find cutting planes that don't remove
integer solutions.

Gomory algorithm: find $b_i$ non-integer in the final dict. Put lhs - rhs
$\geq$ 1 as cutting plane. Proof: $x_i - \lfloor b_i \rfloor - \sum_j \lfloor
a_j \rfloor x_j = b_i' + \sum_j a_j' x_j$
