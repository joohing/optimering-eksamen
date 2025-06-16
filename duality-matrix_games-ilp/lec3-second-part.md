# Alright guys here we go, duality time!

Duality starts off as a discussion about which theoretical bounds we can set for
the Simplex algorithm.

So which ones can we give? We can give a theoretical upper bound with a new
linear program called the dual.

# What is the dual and how do I make one?

The dual provides an upper bound on the primal problem's solution. Thus you can
actually (by the strong duality theorem) deduce that if you find the optimal
value of the dual problem, then it is equal to that of the primal problem.

To make the dual, you create $m$ new variables $y_1, ..., y_m$ (where $m$ is the
number of constraints). The objective function, which must be minimized, is the
sum of all constraints times the corresponding bound, $b_i$. Each constraint is
now bounded by being greater-than-or-equal-to each coefficient in the objective
function of the primal. The coefficient in the columns of a row $i$ are the
coefficients in the rows of column $i=j$. So basically, the whole matrix
representing the left-hand sides of the constraints is just transposed.

In short, for the primal problem

\begin{align}
    \text{Max}&\ c^Tx\\
    \text{Subject to}&\ Ax \leq b\\
    &\ x \geq 0
\end{align}

We get the dual problem

\begin{align}
    \text{Minimize}&\ b^Ty\\
    \text{Subject to}&\ A^Ty \geq c\\
    &\ y \geq 0
\end{align}

Which is kinda crazy ngl.

# Weak (cringe) duality theorem

If $x$ is feasible for $P$ and $y$ is feasible for $D$, then:

$$ c^Tx \leq b^Ty $$

So all feasible points for the primal yield a smaller result in the objective
function than for all feasible points for the dual.

# Strong (based) duality theorem

If some $x\*$ is optimal for the primal, and some $y\*$ is optimal for the dual,
then the objective functions for the primal and the dual are equal when
evaluated at those points, i.e.

$$ c^Tx\* = b^Ty\* $$

What this also implies is that an LP max problem can be expressed as an
equivalent minimization problem, yielding the exact same optimal value!!
