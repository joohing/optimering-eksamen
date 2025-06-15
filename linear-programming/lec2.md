# Whoa, lecture 2! (Poggers)

Lecture 2 starts out with some sample simplex stuff. It performs some pivoting steps - nothing new.

The way to do pivots is pretty simple: You just express the entering variable in terms of the
leaving variable using basic algebra, and then sub in the newly gotten expression for the entering
variable all the places it's used. You then get (from subbing in the new equation into the other
basic variables' equations) new equations for all the other basic variables that now contain no
references to the entering variable, but instead ref- erences the leaving one.

# Muy importante special case for dictionaries

If an entering variable (a variable that is currently non-basic) has a non-negative coefficient in
all rows of the dictionary, then report unbounded, since you can keep increasing the variable's
value without violating any constraints. Thus arbitrarily good solutions exist.

# Problem for our correctness analysis

In this forelaesning he also shows an incorrect analysis where he shows that the algorithm does not
necessarily terminate - it should be an optimal solution that is reached when it does though. The
termination property is first reasoned about using the finite amount of combinations of non-basic
and basic variables. He shows that a cycle breaks this proof because the finite amount of steps
turns infinite if there is a cycle.

# Degenerate dictionaries and cycles

This leads to an intro to degenerate dictionaries. He defines a degenerate dictionary as a
dictionary in which some of the coefficients in the "constants column" are zero - i.e. some of the
constants that originated from the constraints $b_i$ are cancelled out at some point.

Usually the simplex algorithm fixes it after a few degenerate pivots, but it IS possible.

A cycle is one in which all the intermediate dictionaries are degenerate.

# Anti-cycling strategies

There is the lexicographic method, and there is Bland's rule.

An important theorem is stated about them: When using Bland's rule or the lexicographic rule for the
simplex method, it ALWAYS terminates.

# The lexicographic rule

I don't really care about this one. Maybe I'll understand it later.

# Bland's rule

This dingus figured something out about selecting the entering variables in some smart way.

- First choose the entering variable to be the one with the smallest index (and a positive
  coefficient in the objective function of course).
- Then choose the leaving variable to be the one with the most restrictive ratio (i.e. minimize the
  expression $b_i / a_{ij}$ where $b_i$ is the constant term in the row and $a_{ij}$ is the
  coefficient of the entering variable in that row). If there is a tie, break it by selecting the
  variable with the smallest index, you absolute dunce. 

In practice, switch to an anti-cycling rule (one that is cycling-proof like Bland's rule) when you
run into a cycle.

# Ayo what do I do if my origo is non-feasible?

Then you are fricked. Jk then you can use the auxiliary problem, which is phase 1 in the 2-phase
simplex method.

Phase 1: you construct a feasible dict for the auxiliary problem (more on that in a second) and then
you run then one phase Simplex method on it. If the optimal solution here has value $w<0$, i.e. the
objective function is negative, then the whole problem is infeasible. Otherwise, $w$ must be $0$,
and thus the solution is feasible for P (i.e the original LP). Now, if $x_0$ is a basic variable,
make a pivot in which you take it out of the basis, and remove all terms involving $x_0$ in the
dictionary. You may do this since $x_0$ is necessarily 0 (since $w=0=-x$). Lastly, express all the
non-basic variables in the objective function in terms of the non-basic variables - this is a simple
substitution and then some algebra. Finally, you can run the one-phase Simplex method on the
resulting dictionary, which will give you the optimal solution to the original problem.

# THE fundamental theorem of linear programming (holy shit!!!)

The slides state the following:

For an arbitrary linear program in standard form,
1. If there is no optimal solution, then the problem is either infeasible or unbounded.
2. If a feasible solution exists, then a basic feasible solution exists.
3. If an optimal solution exists, then an optimal feasible solution exists.

The proof for these: the two-phase simplex algorithm! Wowies!

# Geometry

In a linear program, we have $m$ constraints and $n$ variables, each with a
non-negativity constraint. Therefore we have $m+n$ half spaces in
$\mathbf{R}^n$, and the set of feasible solutions is the intersection between
all of them.

This sounds super crazy but looking at just one scribble of a triangle will make
you go "aaahhhhhhh".
