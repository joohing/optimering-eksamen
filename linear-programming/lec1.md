### ------------------------------------------------------------------
###                    Linear Programming (poggers) 		
### ------------------------------------------------------------------

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
		&a_{m1}x_1 + a_{m2}x_2 + ... + a_{mn}x_n \leq b_m
\end{align}

Hello.
