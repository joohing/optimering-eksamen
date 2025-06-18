# Approximation Algorithms and Local Search Heuristics

Based on lectures 24, 25, 26, 27

- 24: VERTEX COVER, TSP approx algos.
- 25: MAXE3SAT, WEIGHTED VERTEX COVER, SET COVER, KNAPSACK approx algos.
- 26: TSP tour construction heuristics, k-OPT neighborhood for TSP (obvious
  bridge to branch and cut?)
- 27: Metaheuristics for TSP

- Methods of solving
- NPC problems
- Approx algos
- Local search
- k-OPT neighbourhoods
- Boosting

## Overview of the presentation

Start out with the "hierarchy" of search solutions (exact solutions, local
search, approx): what is hard about solving an NP problem, why not just solve it
exactly? What is an approx algo? Approximation ratios. Local search generally,
neighbourhoods etc. k-OPT neighbourhoods for TSP. Lin-Kernighan stuff (more or
less just talk about lec 27).

## Details

Exact solutions good. Local search OK, but no guaranteed optimal solution
(neighbourhoods? for tsp k-OPT?). Lastly approx algos.

NPC problems typically hard due to no found poly time algo. Approx algo is an
inexact answer, approx ratio the percent mistake worst case.

Local search: find neighbours, while better neighbour, switch solution.
(selective expansion - branch and cut.)

How to improve local search? Boosting (tabu search example - we end up in
circles though).
