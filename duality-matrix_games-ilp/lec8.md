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

## Branch-and-Cut

Branch and cut was used to solve crazy problems (TSP for all pubs in the UK, for
example (of which there are very many (god I'd love some beer right now))).

Adding an inequality to an ILP, it's important that it doesn't change the
solution space. A new inequality is thus called valid if it doesn't change the
set of integer solutions to the ILP - so it is allowed to remove non-integer
solutions (we don't care about those).

A cutting plane is one that removes the non-integer optimum solution to the
relaxed LP. As such we "cut corners" to get to the good stuff.

## A cutting plane algorithm for ILPs

If we have an efficient way to find valid cutting planes, we can simply set up a
while loop. This while loop should construct an LP-relaxation of the ILP
instance input. Then, if the optimal solution is non-integer, introduce a valid
cutting plane to the input ILP and try again. Then return the optimal solution
(that is now an integer, after the while loop).

So how do we find a cutting plane?

## Finding valid cutting planes

There's something called the Gomory cutting plane algorithm. It requires
assuming all initial coefficients in the ILP instance (in standard form) are
integers.

The algorithm is basically this: say you found the optimal solution to the
LP-relaxation, and some line reads $x_i = b_i + \sum_j a_jx_j$ where $b_i$ is
not an integer. Then you can reconstruct the line as follows:

\begin{itemize}
    \item $x_i$ is, of course, equal to the left-hand side.

    \item $b_i' = b_i - \lfloor b_i\rfloor$ is the non-integer part of $b_i$,
        and $a_j'$ the same.

    \item Taking $x_i - \lfloor b_i \rfloor - \sum_j \lfloor a_j \rfloor x_j$
        is the same as calculating the non-integer part of the whole expression.

    \item Calculating $b_i' + \sum_j a_j' x_j$ is also that.

    \item Thus $x_i - \lfloor b_i \rfloor - \sum_j \lfloor a_j \rfloor x_j =
        b_i' + \sum_j a_j' x_j$.
\end{itemize}

So both of those expressions just compute the non-integral part of the line in
the dictionary. Now, for all integer solutions, the left-hand side of the last
equation must be an integer. This is because there would be no decimal part in
the $x_i$ (we know there is in the $b_i$ though). So we know that, if it's a
valid integer solution, the $x_i$ is integer.

Additionally, since we've already assumed that $b_i$ is not an integer, we may
assume that $b_i'$ is positive, and therefore the right-hand side is strictly
positive.

Therefore, we shall be cutting only non-integer solutions, and we will actually
be cutting them away since the right-hand side is strictly greater than 0.

Therefore this procedure generates valid cutting planes.

### Is it correct? Does it terminate?

Partial correctness is "easy" (sure, for the professor it is). Partial
correctness is that the algorithm never terminates with an incorrect result
(termination not guaranteed), total correctness is that the algorithm always
terminates with the correct result.

So termination is not guaranteed. But it can be, if the simplex algorithm uses
special pivot rule and the line of the final dictionary from which to select the
cutting plane is chosen carefully!

Rest will be written soon TM
