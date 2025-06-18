# P, NP, and Cook's theorem

Based on lectures 15, 16, 17, 18.

- 15: Turing machines, efficiency, P.
- 16: NP, reductions, NPC.
- 17: (circuit) SAT, Bool func representations, truth tables formulas and circuits.
- 18: Cook's theorem

- Turing machines
- Efficiency/P vs NP
- Reductions
- CSAT to SAT

## Overview of the presentation

What's a turing machine. What is efficiency. The class of P. NP and reductions.
What is a language, decision problems. Polynomial-time computable maps. How to
reduce some sample thing to SAT.

## Details

A turing machine has a tape head and infinite tape. Finite control which reads
and updates cells, controls tape head.

Efficiency: worst case poly time. P: efficiently computable. NP: solvable by
local search (comb exhaust search).

NP reductions: polynomial time computable maps. Verify a poly time map by going
"both ways" (need maps $g_1$ and $g_2$ as well). NP-hard: all NP problems
reducable to $l$, NPC: it's in NP as well.

Language: caters to model 2, zeros and ones. Decision problem: does it belong to
the language. NP-hard decision problem: HALT.

Reduction CSAT -> SAT (CNF): Handin. Tseitin trans: var for each gate, clause
for the computation of each gate. Example: draw (x1 AND x2) OR x3. Remember OR
is neg of AND. AND: z => x1 AND x2 becomes (x1 OR -z) AND (x2 OR -z) AND (-x1 OR
-x2 OR z). (Think "if the others hold, then either x1 is true or z is false".)
