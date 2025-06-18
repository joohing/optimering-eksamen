# NP complete problems

Based on lectures 19, 20, 21, 22, 23

- 19: Results: 3SAT is in NPC (2 reductions), 2SAT is in P (Resolve and
  graph-based algo), MAX2SAT is in NPC.
- 20: NPC results: Indep. Set, Clique, Vertexcover (those three are alike), NAESAT.
- 21: NAESAT use to show MAXCUT and 3-color in NPC. HAMIL. PATH and TSP in NPC.
- 22: TRIPARTITE MATCHING, XC3, SET COVER, SET PACKING are in NPC.
- 23: KNAPSACK, SUBSET SUM, BIN PACKING are in NPC. Strong NP-hardness.
  Pseudopoly time algos.

## Overview of the presentation

What does NP mean? What does NPC mean? Implications of something being in NPC.
Show SAT is in NPC. Show the three graph problems in lec 20 are in NPC.
NP-hardness and pseudopoly time algos if time allows.

## Details

NP: x such that exists y polynomial time verifiable solution (also bounded in
length). NPC: in NP, and NP-hard. NP-hard: all NP problems reducible to it.

What is a reduction? Reduce CSAT to SAT (shows SAT in NPC).

Show equivalence of indep set (over G with K nodes), clique (over compl of G),
vertex cover (V \ indep set is vertex cover).

Show Indep set in NPC.

- P/NP/NPC
- Reductions
- CSAT <= SAT
- Ind. set <=> VC <=> Clique
