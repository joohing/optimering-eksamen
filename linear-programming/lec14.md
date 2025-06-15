# Holy shizzle guys now it's the last lecture for this subject!!

He starts out with an outline of the three ways that we, in the run of the
course, have formalized optimization problems. First up is linear programs
(LPs), from which algorithms include the Simplex algorithm. Then there are
Integer Linear Programs (ILPs), from which we have branch-and-bound, cutting
planes. And then there's Network Flow, which is the weird one with network
simplex, Ford-Fulkerson and its variants, and Klein's algorithm.

What they share (except for the flow algorithms, which are more efficient in the
worst case) is that they spend EXPONENTIAL time in some instances, which is
objectively ****ing ****.

So an obvious question is: can we get something better than exponential, e.g.
something that runs in polynomial time? Good question. (He explains that he
means an algorithm that is upper bounded by a polynomial in the size of its
input: thank you captain obvious.)

What even is the size of the input in this case? There are two models with which
to analyze this.

# Model 1: The Abstract, Perfect Computer

There has been much debate whether Model 1 gives computers unrealistic beauty
standards for themselves, since they will never be able to attain such perfect
number operations.

In this model, we assume that each operation on some numbers takes one "unit" of
time (just like I'm an absolute UNIT). In other words, it's constant no matter
which two numbers we are talking about. The input is thus just the
vectors/matrices that are given as input to the algorithm(s). The output is the
exact result as an element of the real numbers (which computers can't represent!).

# Model 2: The Real, "Erroneous" Computer

In this model, which is more close to the real world, the input size is not just
described as the size of the matrices/vectors in terms of the number of
elements, but rather the number of bits to describe the whole thing. We charge
money (nah JK but actually time which is, in some sense, money) for each bit
operation. The output is not an element of the real numbers, but instead the
exact rational result (i.e. a fraction).

# Model 1 vs. Model 2

Model 1 more closely resembles the way we usually talk about algorithms, but is
an abstraction and is actually impossible to implement 100%. You can actually go
from Model 1 to Model 2, as long as the input is restricted to rational numbers
(you cannot give real numbers to a computer - only a few of them anyway) and
doesn't rely on very large numbers that take up a billion yottabytes.

Side note: only numbers which can be represented as a fraction with the
denominator being a power of two (i.e. the prime factorization of the
denominator contains only 2's) can be represented using floating point
arithmetic.

# State-of-the-Art inside algorithms

Strongly polynomial time means model 1, polynomial time means model 2.

Network flow has some strongly polynomial-time algorithms (flow fixing, minimum
mean cost cycle cancellation algorithm). Linear programming does NOT have one,
but does have a few polynomial time algorithms (interior point, ellipsoid
algoritihm). ILP does not even have a polynomial time algorithm. The question of
finding one is actually just "P=NP" in disguise.

Interior point algorithms are more efficient in practice than the Ellipsoid
algorithm.

# So what on Earth is an ellipsoid algorithm?

Pretty simple. Enclose all feasible points within a large ball (which is just a
special case of an ellipsoid). See if the center is feasible. If not then offset
the plane representing the violated constraint by $\text{dist}(c_i, p)$ i.e. the
distance between the center point of the ellipsoid and the plane. Then, use this
offset plane to separate the ellipsoid into two. The side to which the plane of
the constraint lies is the half of the ellipsoid within which there are feasible
points. We now redraw the ellipsoid around the feasible half. Then repeat.

If you find a solution and want to improve it further, you can keep iterating by
using the objective function as a splitter plane.

## Why does taht work tho (I ain't fixing that spelling error)

He does some math, idk. At most $K = 16n(n + 1)L$ iterations are needed.

## What to do if the feasible region has 0 in some dimension

Then set $b_i' = b_i + 1/(2^{2L})$. This will affect the feasible region's
extent in all dimensions such that none of them will be zero. The original
program is feasible if and only if the new one is.

## Implementation & issues

See the slides for the implementation (he gives some formulas, don't wanna write
them all down here).

In the formulas, there is a square root. Which is a massive issue! So compute
with bad precision, make each new ellipsoid slightly bigger to account for
errors, double number of iterations. See why the ellipsoid method is not really
used in practice yet?

A unique feature of it, though, is that we don't per se need the inequalities,
just an "oracle" meaning we don't need to think about the number of inequalities
when solving the problem! Hell yeah.

# Okay moight, so what is an interior point algorithm?

Well moight, an interior point algorithm is one in which we start on the
interior rather than goin' round to all the corners of the polyhedron. NO
THANKS!!!!!!

This one is kinda funky. First, get the dual problem of the one you are working
with. This is relatively easy. Then convert it to a barrier problem, where you
use the primal slack variables for some of the stuff.

Now you have some terms with log and then some more stuff in them. The intuition
is that as soon as the numbers that the logs are taken of get small, then the
whole thing goes very negative (oh no!) and thus it doesn't matter how much you
try to optimize your objective function. The numbers that the logs are taken of
are the $x_j$'s, which means that you should get somewhere near 1 at least with
those, and the $w_i$'s, which means you want an even distance (it's a decreasing
function, so larger distances have diminishing returns) between the left-hand
sides and the right-hand sides of the constraints. So you end up with very
"safe" bets. Decreasing $\mu$ thus decreases this effect, letting the actual
objective function take over more and more. Thus letting the algorithm get
closer and closer to the optimal value.

The path traced by the interior point algorithm is the solutions along the way
when adjusting the $\mu$ value. Solutions you say? Yes, because actually the
solution is now a plane bound by a strict equality sign by each constraint,
rather than the inequality stuff we're used to.

## Sounds good moight, but please provide me some theoretical guarantees for the existence of a solution moight

Ok moight, if primal feasible set has a non-empty interior, and is bounded (lmao
unbounded fans be fuming rn) then for each $\mu \geq 0$ there is a unique
solution to the crazy system of equations that he derived on the slides that I
am not going to rewrite here.

I am not going to go through the rest of this lecture because my guy Kristoffer
was so savage that he decided not to talk about the hardest parts.
