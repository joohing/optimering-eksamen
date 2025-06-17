# Lecture 27 - Local-search heuristics for Teaspoons

Since we can get caught in a local minimum, how do we escape it? In this lecture
we get some different techniques.

## Tabu search

We start out with this banger which is apparently pretty bad for TSP. The idea
is to just keep searching when reaching a local minimum - we start going to the
best neighbours and keep a list of already seen solutions, making it tabu to
enter any of them. Problem is that we tend to circle around the local optimum
(in however many dimensional-space). So we can instead make individual moves
illegal.

## Lin-Kernighan

A heuristic for TSP that is "very successful" and has tabu-like elements.
Description from slides: "boosting 3-OPT by a sequence of possibly uphill 2-OPT
moves".

The procedure:

- Whenever a 3-OPT move is made we do additional LK-moves (which seem to be 2-OPT
  moves?).
- While doing this we don't delete ones that have been modified already by an
  LK-move.
- Keep track and take the best one.

Moves under the search could be uphill (since you can't remove the ones you
added in the search, you may end up in such a situation).

(TODO see what "1-trees lighter than the current tour" means???)

(TODO read up on "Speeding up k-OPT" list, incl neighbour lists)

### Iterated LK

Do new search after you are done from a starting point one 4-OPT move away.
(What is a double bridge move?)

## Metropolis algorithm and Simulated Annealing

Allow bad move with probability. "Temperature" as in LLMs.

The $y$ value (current best) is then assigned $z$ with some probability. In the
slides he writes $min(e^{(v(y)-v(z))/T}, 1)$, where $T$ is some input (and the
other two are $y$, the current best, and $z$ the current neighbour in
consideration). That will, if the numerator is positive, always set $y:=z$. Of
course if the solution sucks, then the probability is less than 1, but still
present - this is where the magic happens. Also notice - for a negative exponent
(solution worse than before) then an increase in $T$ increases the probability
that the solution is picked anyways.

The convergence picked here (using $e$) is "slow", so other expressions could be
picked if you wanna.

### Simulated Annealing

Like the metropolis algo, but we change T while we run. Lowered over the course.

## Evolutionary algorithms for TSP

Seems cursory, don't care
