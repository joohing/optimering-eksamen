# Lecture 23

Contains a bunch of random stuff, here I just note some of the terms used.

Pseudo-polynomial time algorithm: algorithm that is polynomial in input value,
not input size like polynomial-time algorithms.

Weakly polynomial time algorithm: polynomial in the number of ints and number of
bits in the largest integer.

The two following are true if P is not NP:
- Strongly NP-hard: no pseudo-poly time algo, no FPTAS (poly in both problem
  size and inverse of $\epsilon$). 3-Partition problem.
- Weakly NP-hard: no weakly poly time algo, but may have pseudo poly time algo.

Co-NP: x is a member if its complement is in NP. You can have problems in both.

IF a strongly NP-hard problem turns out to have a pseudo poly time algorithm,
then P=NP. Oh no!

Decision problems for optimization problems: an example is OPT, "find x
maximizing f(x)". Then we can have decision problem $L_{OPT}$ as a stand-in,
asking "decide if there is x s.t. f(x) $\geq$ v for some v".

Decision problems used as stand-ins are useful, since any efficient algorithm
for the original optimization problem yields an efficient algorithm for the
decision problem. Thus, the decision problem stand-in can also be used to reason
about the optimization problem.

For some problem Q involving integers(?)
- If the decision problem stand-in is in $P$, we know Q has a pseudopoly
  algorithm.
- If it's NP-hard, Q is strongly NP-hard. Doesn't have anything.

Slides finish off with a bunch of great memes that explain good and bad uses of
reasoning about complexity classes.
