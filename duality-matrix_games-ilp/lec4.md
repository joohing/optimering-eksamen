# Weewoo let's go it's the lecture 4 police in da house and I want ferie lige nu eller jeg bliver angery

The first actually new thing he goes over is how to find the optimal dual
solution from the primal solution. He has a dictionary over the final primal
dictionary, and that allows basically directly reading off the values for the
entries of the vector $y$.

# Reading off some shizzle

A particular dictionary can have its dual solution values read off it by simply
taking the negative of the coefficients of the slack variables in the primal
dictionary's objective function.

I.e. if you have a final dictionary with objective function $z = 13 - 3x_2 -
x_4 - x_6$, and the slack variables are $x_4$, $x_5$, and $x_6$, then you know
that since $x_4$ and $x_6$ have coefficients $-1$ in the objective function,
then $y_1$ and $y_3$ both have value 1. What about $y_2$? Since $x_5$ is in the
basis, we say that that has coefficient zero in the objective function, so the
value of $y_2$ is $y_2 = -0 = 0$.

# Direct translation from one dict to another

Since the dual problem defines a minimization problem and has greater-than
constraints rather than less-than constraints, the dictionary of the dual ends
up being the negative transpose (transpose the matrix, then negate each element)
of the primal dictionary. (This works a bit weirdly, because the objective
value $w$ is negated, but not any of the other "variables".)

In fact, the two (primal and dual dict) remain exactly the negative transposes
of eachother across pivots. This doesn't necessarily mean they are both always
feasible though!!!!

# Using this as a proof of the Strong Duality Theorem

Don't really understand this, might look at it later

# Duality theorems

These are also in lec3-second-part.md

A consequence of them is that software using LP can easily be checked - it is
completely certain that if the dual and primal solutions yield the same value
the primal program is optimal.

Another consequence is that you can now use a linear inequality solver to solve
the system of equations and find the optimum. Simply check first if the linear
program $P$ is feasible, if so, construct the dual $D$ of $P$ and find vectors
$x, y$ such that $Ax \leq b,\ x\geq 0, A^Ty \geq c, y\geq 0$, and finally $c^Tx
= b^Ty$. In words: solve the problem so that the constraints for both are obeyed
and the solutions are equal.

# Complementary slackness theorem

The complementary slackness theorem states that solutions $x$ and $y$ are
optimal if and only if they satisfy complementary slackness.

Note that this doesn't mean that any solutions satisfying complementary
slackness are optimal or even feasible.

## Complementary slackness property

Complementary slackness is that, for both the primal and the dual: either the
slack of a constraint is zero, or the corresponding primal/dual variable is
zero. Expressed elegantly in the book:

\begin{align}
    \item For all $j = 1, ..., n$: $x_jz_j = 0$
    \item For all $i = 1, ..., m$: $w_iy_i = 0$
\end{align}

Where $x$ and $y$ are the basic variables for the primal and the dual problems
respectively, and $w$ and $z$ are slack variables for the primal and dual
problems respectively.

## Ayo when is my LP origo feasible?

In practice, we often want to minimize cost. This means each coefficient in the
objective function is probably positive (since it is cost - otherwise you'd just
make infinite product). For situations where all of those are positive, the dual
is origo feasible.

## Some rules for taking the dual of a general LP

| Primal (maximization)           | Dual (minimization)           |
|---------------------------------|-------------------------------|
| $\leq$ for constraint           |     $\geq0$ for variable      |
| $\geq$ for constraint           |     $\leq0$ for variable      |
| $=$ for constraint              |     free for variable         |
| $\geq$ for variable             |     $\geq$ for variable       |
| $\leq$ for variable             |     $\leq0$ for variable      |
| free for variable               |     $=$ for variable          |


# Can we prove infeasibility or unboundedness?

So as we saw we can easily see if a problem was solved optimally if, by reading
off the solution to the dual from the final dictionary and plugging it into the
objective function, we get the same value as the primal's objective function.

Can we do similarly for the other two outcomes of an LP?

YES!!!! Of course we can you nerd.

## Farkas Lemma

The $Ax \leq b$ has no solutions if and only if there is a $y$ such that $A^Ty =
0$, $y\geq 0$, $b^Ty < 0$.

What this means is that, if you can find such a $y$, then the primal is
infeasible. Thus the primal is infeasible if and only if the dual is unbounded.

## Strict Complementary Slackness

Instead of either the slacks being 0 or the dual variables being 0 for both the
primal and the dual problem, exactly one of the two must hold for all of the
indeces of one, and exactly one of the two must hold for all indeces of the
other. So, e.g. for the dual problem, either ALL of the primal constraints have
zero slack, or all of
