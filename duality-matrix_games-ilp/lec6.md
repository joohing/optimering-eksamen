# Matrix Games (hell yeah I love gaming)

The slides kick off with a bunch of motivation for the subject. My motivation is
just to pass the exam though LMAO.

A matrix game is given by a payoff matrix $A$.

Row player chooses a row without seeing the column-player's move, and vice
versa. They are zero sum games. The row player loses, the column player gains.
(In most other cases, the two are reversed such that the row player gains.)

## Optimal column player strat

Max wants to optimize the choice of coins such that the amount gained is
maximized. As such, we have some probabilities that Max needs to assign to each
choice (the probability that he will choose that particular coin). This can be
formulated as an LP.

## Optimal row player strat

Minnie wants to minimize (I guess the name makes sense now), so has to choose
the same but such that $l$ is minimized where $l$ is the bound on each
constraint.

The point here is that their programs are each other's duals!

Since they are each other's duals, the value of the expected outcome is called
the value of the game.

## Fair and symmetric games

A matrix game is symmetric if its matrix is antisymmetric. A matrix is
antisymmetric if its transpose is equal to its negation.

A symmetric game is always fair. A game is fair if its expected value is 0. The
opposite is not necessarily true (of course).

## Matrix algebra to find the expected outcome

Given that Max and Minnie play by randomized strats with likelihoods for the
outcomes given by vectors $p$ and $q$, the expected gain of Max is $q^TAp$. This
is pretty intuitive: the result of $Ap$ is just the expected (average) amount of
money left at each spot in the matrix (remember that a matrix applied to a
vector is a vector). Thus $q^TAp$ is just the probability that Max takes the
expected sum at each spot.

As such we can formulate the value of the game as

$$ v = \text{max}\_p \text{min}\_q q^TAp $$

This leads us to:

## Von Neumann Min-Max theorem

For any real matrix:

$$ \text{max}\_p \text{min}\_q q^TAp = \text{min}\_q \text{max}\_p q^TAp $$

When $p$ and $q$ are probability distributions on the columns and rows of $A$.

## Exploiting and Principle of Indiff

Exploit: achieve something better than the value of the game.

Principle of Indifference: Suppose Max plays the optimal strategy $p\*$, and
Minnie plays her own, not necessarily optimal, strategy. Then Max' payoff is the
same no matter which actual row Minnie selects. His payoff is then equal to the
value of the game. The important thing here is that, as long as Minnie's
plays are something that could have been played by an optimal strategy, Max
doesn't gain more than the value of the game.

The proof of this is the complementary slackness theorem! Since the problems are
each other's dual, and both strategies are optimal, we know that either the
probability of a certain outcome is assigned 0 by Max or Minnie satisfied the
constraint with equality i.e. the probability is equal to the minimized
objective $l$, and thus the optimal choice was made by Minnie in this situation,
yielding nothing more than the value of the game in the end.

The opposite also holds: Due to strict complementary slackness, then if some
optimal strategy would never select some row, and the row player places some
non-zero probability on it, then it's possible for the column player to
capitalize on this. The reason is that if some non-zero probability is placed on
the row, then necessarily (by strict complementary slackness) there must be an
inequality in the constraint for the maxxer. This means he gains more than the
value of the game.

## Nash equilibriums

Theorem: a pair of randomized strategies are a Nash equilibrium if and only if
they are both optimal.

## Three-card Poker, a sequential move game

Model this by doing a tree of probabilities.
