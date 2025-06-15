# ------------------------------------------------------------------
#                    Linear Programming (poggers)         
# ------------------------------------------------------------------

Very shortly put, it is simply optimizing a linear function w.r.t. linear constraints.

The matrix form of a maximization problem would be:

\begin{align}
    \text{Maximize}&\ c^Tx\\
    \text{Subject to}&\ Ax \leq b
\end{align}

Or, they could be split into many constraints instead, with both $\leq$, $\geq$, and $=$ between
them.

The decision variables are $x$. An assignment to them is a solution. A solution satisfying the
constraints is feasible. A feasible solution that actually minimizes/maximizes is optimal (sometimes
denoted by an asterisk, i.e. $P*$).

The set of feasible solutions, called $F$, is a convex polyhedron. That means it has $n$ sides and
has no two points such that a line may be drawn between them that crosses outside of the polyhedron.
Usually, you need to traverse to a corner of the polyhedron to attain an optimal solution.

Two stinky cases: unbounded solutions, where an arbitrarily good solution may be found, and
infeasible LP's, where the set of feasible solutions is empty.

I know what you're thinking at this point: "That's really cool, Jonathan, but what is the standard
form of a linear program?" Well, here it is!

\begin{align}
    \text{Maximize}& \ c_1x_1 + c_2x_2 + ... + c_nx_n \\
    \text{Subject to}& \\
        &a_{11}x_1 + a_{12}x_2 + ... + a_{1n}x_n \leq b_1\\
        &a_{21}x_1 + a_{22}x_2 + ... + a_{2n}x_n \leq b_2\\
        &...\\
        &a_{m1}x_1 + a_{m2}x_2 + ... + a_{mn}x_n \leq b_m\\
        &x_1, x_2, ..., x_n \geq 0
\end{align}

Standard form is practical because then you can perform algorithms which assume that your program is
of some standard form. Any other linear program can be transformed to standard form with very simple
steps. E.g. if we want to minimize, replace with maximizing the negative. If we have some constraint
with the inequality flipped the wrong, way, multiply each side with $-1$, and so on.

The most important one is that you can have an equality and make it into standard form by rewriting
it with a $\leq$, and then multiplying each side by -1 WHILST keeping the inequality the same. This
way you have two inequalities that, when they are both satisfied, the solution must satisfy the
original equality.

A few more conversion tricks:
\begin{itemize}

    \item If you want an unconstrainted $y$, replace $y \geq 0$, with $y_+, y_- \geq 0$ and replace
    $y$ with $y_+ - y_-$ everywhere.

    \item If you want to adjust a constraint, e.g. to say that $y \geq -17$, replace $y \geq 0$ with
    $y' = y + 17$. Replace $y$ with $y' - 17$ everywhere.
\end{itemize}

After you made those substitutions, you can convert a solution found back into a solution for the
normal LP. This is done by subbing back $y = y_+ - y_-$. Subbing the other way can be done by
subbing $y_+ = \text{max}(y, 0)$ and $y_- = -\text{min}(y, 0)$.

Unfortunately this causes a 2x blowup in size in terms of variables and constraints, but in one of
the exercises it's shown that you can do it with just 1 extra constraint & variable.

# So what's the simplex algorithm?

The simplex algorithm is basically starting in some corner of $F$ (the polyhedron of feasible points),
and then while some better corner exists, go to that. What about interior solutions? Nah moight
don't worry about it. I guess that's treated later in the course?

Before going in depth with the simplex algorithm, let's have a lookie at dictionaries.

## Dictionaries moight

Aw yiss moight. Dictionaries are a system of equations like

| | | | | | |
|-|-|-|-|-|-|
| $z =$ 	|   	|   	| $3x_1$ 	| $+$ 	| $2x_2$ 	|
| $x_3 =$ 	| $10$ 	| $-$ 	| $3x_1$ 	| $-$ 	| $x_2$ 	|
| $x_4 =$ 	| $6$ 	| $-$ 	| $2x_1$ 	| $-$ 	| $5x_2$ 	|
| $x_5 =$ 	| $2$ 	| $+$ 	| $x_1$ 	| $-$ 	| $2x_2$ 	|

The above is constructed from an LP. The LP:

\begin{align}
	\text{Maximize}&\ 3x_1+2x_2\\
	\text{Subject to}&\ \\
	&\ 3x_1 + x_2 \leq 6\\
	&\ 2x_1 + 5x_2 \leq 10\\
	&\ -x_1 + 2x_2 \leq 2\\
	&\ x_1, x_2 \geq 0
\end{align}

In the dictionary, there are more variabes than in the original LP. This is because your mom ate
them in the original LP (she so fat she has her own gravitational field). The new variables are
called slack variables.

Constructing a dictionary with $m$ constraints and $n$ variables requires a feasible origin.
Notice that the slack variables are instantiated as the constraints, minus the left-hand side
of the equation. The dictionary becomes a system of equations with $m + n + 1$ variables, where
the 1 is the $z$ (objective function). There are $m+1$ equations expressing $m+1$ variables as
linear combinations of the rest.

The left-hand variables, except for $z$, are called the basic, variables, and the right-hand ones
are called the non-basic ones. The set of basic variables is called the basis. The basic solution
for a dictionary is the solution by assigning 0 to all non-basic variables. A basic solution is
feasible if the values of the basic variables, after assigning 0 to all non-basic variables, are at
least zero (i.e. their non-negativity constraint is obeyed). A dictionary is feasible if its basic
solution is feasible.

The current solution while iterating over a dictionary with the simplex method is the basic feasible
solution. Geometrically, basic feasible solutions are corner points of the polyhedron $F$. This
means our corner traversal is represented by the basic solution changing.

Initializing a dictionary is a mapping from constraints to equations. Each constraint is mapped, as
mentioned, to the right-hand side of the constraint minus the left-hand side. This is then assigned
to the basic variables that are slack variables we create.

## Pivoting

We must find entering and leaving variables. Entering variables enter the basis, leaving ones leave.
There are heuristics for how exactly to find these, but entering variables must have positive
coefficients in the objective function, and leaving variables must preserve the non-negativity of
the basic variables. Importantly, if an entering variable can be found which has non-negative ($\geq
0$ coefficients in all equations, you can find arbitrarily good solutions.

## Simplex, finally

One phase Simplex: what was described above.

Input: an LP $P$ in standard form with feasible origo. Construct the dictionary. While there are
positive coefficients in $z$, find basic variable with the strictest bound on increasing $x_i$ i.e.
if you go past this it will be negative. Perform the substitution (by rewriting the $x_j$ equation
and substituting $x_i$ in terms of $x_j$ into all the places where $x_i$ was used). When no more
positive coefficients in $z$, return the basic solution of the resulting $D$.

# Analysis

In the slides, we are given a short analysis of why the solution is optimal:

- We terminate when all coefficents have reached 0 in the objective function.
- All the variables are assigned zero at this point. So the solution gets a value equal
    to the constant part of the objective function.
- Since the variables are constrained to be non-negative, we must have an optimal solution.
    (Any change in variables would yield a smaller value than the one we have now.)
