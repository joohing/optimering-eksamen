# Lecture 16: NP and so on

A refresher on the class of P: the class of decision problems such that for some
polynomial $p$ and all $x$, the Turing machine running on the input terminates
after at most $p(|x|)$ steps. So the worst case run time as a function of the
input length must be a polynomial.

## Definition of something being in NP

A language $L$ is in $NP$ if and only if there is a language $L'$ in $P$ as well
as a polynomial $p$, for which for all $x$ we have: If $x$ is in $L$, then there
is a bitstring with length bounded by $p(|x|)$ that is a solution to the problem
instance/input $x$. Here $\langle x, y \rangle$ means that $y$ is a solution to
the problem instance $x$.

Intuitively, the above explanation requires that for all instances of the
problem class $L$, we can verify solutions in polynomial time (by requiring $L'$
to be in $P$). Also that the length of the solution is bounded by a polynomial
on the length of the problem instance. So, we are not saying that $NP$ is hard
to solve, only that it's polynomial-time verifiable. This is of course because
we haven't been able to prove that $NP$ problems are not polynomial-time
solvable.

## Exhaustive search in $NP$

As mentioned we require that the solution is bounded in length by a polynomial
on the length of the input. This is our search space, i.e. for exhaustive search
we search through all bitstrings of length less-than-or-equal-to a polynomial in
the length of $x$.

## Is $P=NP$?

Then you can find better algorithms than exhaustive combinatorial search - these
algorithms will be polynomial time upper bounded and thus all of cryptography
breaks (oh no!).

## What is a mathematician? Good question.

Can we make an artificial mathematician that can solve all problems?

The Hilbert program tried, Godel said yeet and proved that you can't through his
Incompleteness Theorem which states that there is no mechanical procedure
(algorithm) that can verify every mathematical statement. There is also no
algorithm that says, for every statement, whether it is provable. So provability
and verifiability is not universally solvable through one single procedure each.
This means we are restricted to algorithms which decide only specific languages
(not all languages) and decidability of specific languages. So if you find a new
language you won't be able to apply the same old procedure to it, you will have
to do work.

## Can you, given provability, find proofs?

Yes, you can brute-force ZFC maths with a computer until you find proof of the
theorem. A computer can check whether each proof is correct. So we can find
proofs given (assumed) provability, and we can verify those proofs.

This takes billions of years though, so don't try at home.

Can we do better? That's exactly the $P$ vs. $NP$ problem.

## Reductions

A reduction is a polynomial time map from $L_1$ to $L_2$ such that, if and only
if input $x$ is in $L_1$, then $r(x)$ is in $L_2$.

This implies that if you have some hard problem $L_1$, then you can just reduce
any instance of it to an instance of $L_2$ using $r(x)$ and then solve that -
all in polynomial time.

## Reduction properties

Transitivity, downward closure (If $L_1$ reduces to $L_2$ and $L_2$ is in
$P$, then $L_1$ is in $P$).

## Types of NP stuff

NP-hardness: a language is NP-hard if and only if all NP problems reduce to it.

NP-completeness: a language that is in $NP$ and also $NP$-hard. So a problem in
$NP$ that all other $NP$ problems reduce to.

It follows that, if we can prove that some language $L$ is $NP$-complete and it
is in $P$, then $P=NP$.


