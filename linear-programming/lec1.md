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
form of a linear program?" Fuck you you piece of shit. Here it is:

\begin{align}
	\text{Maximize}&\ c_1x_1 + c_2x_2 + \ellipsis + c_nx_n\\
	\text{Subject to}&\ Ax \leq b
\end{align}
