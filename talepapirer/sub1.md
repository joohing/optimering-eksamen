# The linear programming model and LP algorithms

Based on lectures 1, 2, 3 (first part), 5 (simplex impl part), 14

- 1: The linear programming problem.
- 2: Analysis of the Simplex algorithm, two-phase simplex.
- 3: Two-phase simplex, analysis.
- 5: Implementation issues for the simplex method.
- 14: Ellipsoid and interior point algorithms. General convex quad programming,
  general convex programming.

## Overview of the presentation

First, talk about what linear programming is. Introduce general, standard form.
Then introduce dictionaries. Then explain the simplex algorithm.
Origo-infeasible? Oh no! Bam: Auxiliary problem. Two-phase simplex. Lastly, an
overview of the ellipsoid and interior point algorithms.

## Niddy griddy LMAO

- What is linear programming?

Linear programming is optimizing a linear objective function w.r.t. linear
constraints. Generally, a linear constraint is a linear function restricted with
an inequality/equality. LP is super useful for modelling problems, and we have
efficient (what is efficiency?) methods for computing them (slightly random
perturbations in input yield exp. poly time, due to Spielman and Teng).
Otherwise, using deterministic pivot rules, you'd usually have exponential time.
LP is a problem in P.

- General/Standard form

In terms of LP, there's both general form, which basically allows all sorts of
shenanigans. There's also standard form, which for all constraints requires
$\leq$, for all variables requires non-negativity. You may run into troubles
with this. Conversion rules: Constraint facing wrong way? Negate. Minimizing obj
function? negate and maximize. Equality constraint? replace with $u \leq v$ and
$-u\leq -v$. Var with no non-negativity constraint? replace everywhere with $x =
x' - x''$ and add constraints for those. Need some other constant to be the
lower bound than 0? Put $y' = y + c$ and replace $y$ with $y' - c$ everywhere.

- Geometric interpretation of feasibility

Introduce solution, feasible, optimal. Introduce feasibility in the geometric
sense, show how the algorithm moves through corners of a polyhedron. Notice how
the feasible set is convex - this makes it easier to solve, contra how an ILP
feasible set looks.

- Dictionaries & Simplex

You know what dictionaries are. Slack variables = rhs of constraints - lhs of
constraints. Non-negativity constraint for all vars.

Simplex: Start with a corner of F. While there's a better neighbouring corner,
pick that instead. Return the found corner. Pivots happen according to rules
(largest coefficient, Bland's rule) - Bland's is a nice anti-cycling strat.
(Talk about degenerate pivots and degenerate dicts?)

Termination of Simplex: when the dual problem becomes feasible (and thus dual
solution equals primal solution), but also when non-positive in all coefficients
of the objective function.

- What to do when no feasible origo?

An infeasible origo is when the initial dictionary is infeasible. Luckily you
can just adjust the constraints a bit with a constant, which is where the
auxiliary problem comes in.

The auxiliary problem replaces the objective function with $-x_0$, and adds
$-x_0$ to all constraints (in standard form). Solve this - if the solution
results in 0 then the solution is feasible for P. For this solution, if the
$x_0$ is in the basis, do a pivot removing it (won't change the solution since
$x_0 = 0$ anyways) and remove all terms involving $x_0$. Then run the simplex
algorithm on the dict. This is the two-phase simplex algo.

Example from slides:

\begin{align}
    \text{Maximize}&\ x_1 - x_2 + x_3\\
    \text{Subject to}&\ 2x_1 - 3x_2 + x_3 \leq 5\\
    &\ 2x_1 - x_2 + 2x_3\\
    &\ -x_1 + x_2 - 2x_3\\
    &\ x_1, x_2, x_3 \geq 0
\end{align}

This algorithm is proof of the fundamental theorem of LP, which is that if an
optimal solution exists, a feasible optimal solution exists. If a feasible
solution exists, then a basic feasible solution exists. If an optimal solution
doesn't exist, then the problem is either unbounded or infeasible.

- Polynomial-time worst-case alternatives to Simplex

Ellipsoid algorithm, which has less issues pertaining to termination, since it
is easily provable that the volume is finite and integral, and reduces each
iteration (thus at some point reaching zero). (Sketch the ellipsoid algorithm.)

The interior point method, which is basically
