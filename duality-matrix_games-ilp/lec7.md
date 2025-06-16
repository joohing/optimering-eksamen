# Lecture 7 babyyy

This introduces integer programming and Yao's principle.

## Yao's principle

The expected complexity of the best randomized algorithm on a worst-case input
equals the weighted average complexity for a worst-case distribution of inputs
using the best deterministic algorithm.

This is more or less the same as the von Neumann min-max principle. The proof of
the above is that both are the value of the game we defined (one guy chooses
input, another chooses algorithm, pay for each unit of execution time).

This means we can obtain the best lower bound possible for the complexity of a
randomized algorithm by 1. constructing a hard input distribution, and 2.
analyzing the average case complexity of the best deterministic algorithm on
this.

For example, we may ask "How long does it take to sort $n$ elements?" for a
randomized algorithm. By Yao's principle, we know that a deterministic one takes
worst case $\omega(n \text{log} n)$, thus ours will as well.

## Integer Linear Programming

An ILP is the same as an LP, but thevalues of the feasible solution must be
integral. So additionally we have $x \in \mathbb{Z}^n$. This means we can model
bools. ILPs are much more powerful but harder to solve.

Bools can be modelled by constraining each $x$ to be less than or equal to one.

## Propositional formula flex

He demonstrates that you can express propositional logic as integer linear
programs. I ain't writing all that. Nice flex though.

A bunch more examples are shown, don't care enough to write them here though LOL

## Travelling Salesman Problem

This Travelling Salesman is a real dang Problem.

The input to some algorithm solving it is a cost (distance) matrix of dimensions
$n-1\times n-1$. The output will be some permutation on the set of possible
values (up to and excluding $n$) that models the path. The permutation can be
interpreted as follows: $x_{ij} = 1$ if and only if for some $k$ it holds that
the path has $i$ at spot $k$, and $j$ at spot $(k+1) \text{mod} n$. I.e.:
Decision variable $x_{ij}$ is one if the salesman is at spot $i$ at time $k$,
and at $j$ right after. So it kind of models an edge between two vertices.

As mentioned we have decision variables $x_{ij}$. We also have decision
variables $t_j$. For these, $t_j = k$ if and only if the traveller is at $j$ at
step $k$.

The final formulation is then:

\begin{align}
    \text{min}&\ \sum_{i,j=0}^{n-1} c_{ij}x_{ij}\\
    \text{s.t.}&\ \forall i\ :\ \sum_{j=0}^{n-1} x_{ij}\\
    &\forall j\ :\ \sum_{i}^{n-1} x_{ij}\\
    & t_j\geq t_i + 1 - n(1 - x_{ij}), \text{for}\ i\geq 0, j\geq 1
\end{align}

Explanations:

\begin{itemize}
    \item The first constraint means each city has only one outgoing edge.

    \item The second means that each city has exactly one incoming edge.

    \item The last one enforces that, if city $j$ was travelled to from city
    $i$, then city $j$ was visited later than city $i$. This means you won't be
    able to visit cities twice.
\end{itemize}

Notice that the first two constraints enforce that each city is visited.

## Knapsack problem

Input: weights $w_1, ..., w_n$, values $v_1, ..., v_n$, and weight limit $W$.

Output: subset $J \subseteq {1, ..., n}$ maximizing $\sum_{i\in j} v_i$ such
that the sum of the weights is equal to or less than the weight limit $W$.

The ILP formulation is kinda obvious, you max the sum of the choices $x_i$ of
the things to put in, so the objective function is the sum of all the
$x_iv_i$'s. Then the constraint is that the sum of the $w_ix_i$'s are less than
or equal to the weight limit.

Standard form is the same as for a regular LP, but with the integer constraint
thing as well.

# Woah! New algorithms!

First we get Divide-and-Conquer.

The LP relaxation is defined simply as the same problem as the ILP but where you
drop the integrality constraint.

Here we see how we can use rounding for making the optimal solution for the LP
relaxation useful for the ILP as well.

## Divide-and-Conquer

Gives a way to partition the search space, might not be better than exhaustive
search in practice.

\begin{itemize}
    \item Compute the optimal solution to the LP relaxation.

    \item Find some $i$ where $x_i*$ is not an integer.

    \item Partition the search space: the optimal solution must satisfy either
    $x_i \geq \lceil x_i* \rceil$ or $x_i\leq \lfloor x_i* \rfloor$
\end{itemize}

Then we have new partitions of the search space.

## Branch and Bound

First, a bounded ILP is an ILP with an additional constraint of $l_i \leq x_i
\leq u_i$, where $l_i < u_i$, both integers. $x$ doesn't have to be positive.

Basically we can use the LP relaxation to find upper bounds on how good our
solutions are going to be. If we then can branch out into more subproblems, then
we can solve the LP relaxation of those and provide an upper bound on what we
can hope to find in further subproblems of those. If some upper bound is worse
than the current best found bound, we just return from the current branch with
no solution.

The branch and bound algorithm is as follows:

\begin{itemize}
    \item Solve LP relaxation. If the problem is not feasible, then neither is
        the ILP. If the solution is integer, return it.

    \item Otherwise, if the objective function turns out to be worse than the
        current best bound, then return from the branch with no solution

    \item Otherwise, pick an entry in the $x$ vector that isn't an integer.
        Branch and recursively solve the bounded ILP, setting the upper bound
        $u_i = \lfloor x_i* \rfloor$. Branch and recursively solve the bounded
        ILP with $l_i = \lceil x_i* \rceil$. Output the best solution of the
        two.

\end{itemize}

Termination is easy: the base case is that if for all $i$, $l_i = u_i$, then we
terminate. Since the two are integers and we either decrease one $l_i$ or a
$u_i$, we eventually terminate (they are integers and will at some point
coincide).


