# DS3 T-K: first-30 -> last-30 / last-30 -> next first-hour intraday momentum (D3K, from D3CT rows)
Prereg l2vast/ds3/prereg/T-K_prereg.md, sha256 62f348f527def5e187aed7c0b151400495aa5dcc5339779846c0edf71c0b9c9e (verified against T-K_prereg.sha256 and DECISIONS.md 2026-10-26T12:59:42Z, 19 cells, ledger cumulative 30904). Scored once by the T-C agent (code l2vast/ds3/code/tk_run.py, series l2vast/ds3/out/TK/, rows l2vast/ds3/rows/DS3_TK.json); the holdout look is logged under track TK (holdout_looks.jsonl, 13:15:34Z). D3K did NOT re-score anything and did not touch the holdout; this report is read from the rows file.

## Verdict
19 cells: 0 PASS, 0 CANDIDATE, 19 DEAD (all three tiers evaluated: PASS 0, CANDIDATE 0, DEAD 19). The best WF mean of any cell is +$6/wk (TK_GC_D2), 0.03 of its MDE, with negative holdout, SPAN23 and PRE23. No 3x3 widening is owed (no PASS). Nothing registered to PAPER-ALL. Pool contribution 0 (want 6, min 1: not met by this track).

The dominant result: 18 of 19 cells have WF mean below zero with CIs excluding zero for the bond cells and the baskets; ALL8_D1 loses $2,499/wk WF, $2,827/wk holdout, $4,892/wk WF at 2x cost ($5,404/wk holdout at 2x), and the 2014-22 PRE23 t is -25.1. The loss scales with cost (1x -> 1.5x -> 2x roughly linear), i.e. it is transaction cost (3 ticks + commission per round trip, one trade a day per market and leg) against a near-zero gross edge; there is no sign-reversed signal either (a negative edge of this size is the cost, not an anti-momentum effect, so reversal is not a free lead: it would pay the same cost). Bond ZB/ZF/ZN are the worst because 1 tick = $15.6-31.3 per side against a 30-minute move of a few ticks.

## Table (scoring windows: WF = 2024-02..2026-10, 142 wk; HOLD >= 2025-07; SPAN23 = 2023-04..2024-01; PRE23 = 2014..2023-02 independent history). $/wk at 1x cost unless stated.
| cell | WF/wk | MDE | WF CI | HOLD/wk | L8W/wk | SPAN23/wk | tr/wk | PRE23 mean (t) | WF 1.5x / 2x | HOLD 2x | plc lib / time | msh up | corrDS2 | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TK_ZB_D1 | -659 | 81 | [-716,-600] | -740 | -892 | -407 | 4.3 | -551 (-26.3) | -981 / -1303 | -1474 | 0.03 / 0.54 | False | -0.01 | DEAD |
| TK_ZB_D2 | -670 | 264 | [-855,-485] | -637 | -757 | -295 | 3.9 | -518 (-12.1) | -962 / -1253 | -1295 | 0.07 / 0.29 | False | -0.00 | DEAD |
| TK_ZF_D1 | -550 | 105 | [-623,-477] | -660 | -911 | -269 | 4.5 | -640 (-26.2) | -833 / -1117 | -1304 | 0.05 / 0.71 | False | -0.04 | DEAD |
| TK_ZF_D2 | -436 | 278 | [-623,-240] | -549 | -627 | -370 | 4.1 | -575 (-12.1) | -699 / -961 | -1140 | 0.08 / 0.80 | False | -0.07 | DEAD |
| TK_ZN_D1 | -649 | 105 | [-721,-576] | -736 | -1041 | -361 | 4.4 | -678 (-31.5) | -985 / -1321 | -1483 | 0.04 / 0.85 | False | -0.04 | DEAD |
| TK_ZN_D2 | -613 | 260 | [-785,-436] | -715 | -893 | -455 | 4.0 | -585 (-13.8) | -917 / -1221 | -1400 | 0.07 / 0.57 | False | -0.07 | DEAD |
| TK_6E_D1 | -211 | 45 | [-240,-180] | -237 | -302 | -181 | 4.5 | -198 (-11.8) | -310 / -410 | -433 | 0.05 / 0.15 | False | 0.03 | DEAD |
| TK_6E_D2 | -57 | 196 | [-202,82] | -57 | -253 | -436 | 4.3 | -151 (-4.0) | -152 / -246 | -241 | 0.16 / 0.97 | False | 0.12 | DEAD |
| TK_CL_D1 | -127 | 106 | [-206,-54] | -135 | 101 | -121 | 4.8 | -141 (-5.2) | -187 / -247 | -237 | 0.09 / 0.46 | False | 0.03 | DEAD |
| TK_CL_D2 | -236 | 223 | [-387,-78] | -181 | -96 | -78 | 4.8 | -232 (-6.1) | -296 / -356 | -283 | 0.10 / 0.07 | False | 0.12 | DEAD |
| TK_GC_D1 | -32 | 92 | [-96,33] | -25 | -69 | -111 | 4.8 | -151 (-9.3) | -58 / -84 | -54 | 0.15 / 0.73 | False | 0.01 | DEAD |
| TK_GC_D2 | 6 | 184 | [-120,129] | -49 | -100 | -162 | 4.8 | -156 (-3.9) | -20 / -46 | -78 | 0.25 / 0.80 | False | 0.00 | DEAD |
| TK_ES_D1 | -147 | 137 | [-241,-60] | -143 | -218 | -147 | 4.7 | -250 (-7.4) | -189 / -231 | -216 | 0.10 / 0.10 | False | -0.00 | DEAD |
| TK_ES_D2 | -39 | 252 | [-213,143] | -13 | 548 | -144 | 4.7 | -157 (-3.5) | -80 / -121 | -86 | 0.19 / 0.72 | False | 0.14 | DEAD |
| TK_YM_D1 | -124 | 131 | [-217,-34] | -151 | 88 | -53 | 4.7 | -151 (-5.0) | -152 / -180 | -201 | 0.11 / 0.06 | False | 0.06 | DEAD |
| TK_YM_D2 | -174 | 244 | [-350,6] | -48 | 122 | -272 | 4.7 | -78 (-1.8) | -202 / -231 | -97 | 0.12 / 0.09 | False | 0.20 | DEAD |
| TK_ALL8_D1 | -2499 | 401 | [-2781,-2212] | -2827 | -3243 | -1650 | 36.7 | -2760 (-25.1) | -3695 / -4892 | -5404 | 0.06 / 0.22 | False | 0.01 | DEAD |
| TK_ALL8_D2 | -2219 | 862 | [-2794,-1634] | -2249 | -2057 | -2213 | 35.3 | -2450 (-15.5) | -3327 / -4435 | -4621 | 0.13 / 0.55 | False | 0.11 | DEAD |
| TK_ALL8_BOTH | -4719 | 985 | [-5402,-4015] | -5076 | -5300 | -3863 | 72.1 | -5210 (-26.0) | -7023 / -9327 | -10024 | 0.01 / 0.44 | False | 0.10 | DEAD |

MDE = 2.8016 x weekly SD / sqrt(142) on WF (column 3); every cell's WF mean is either below -MDE (a real, significant negative: bond, 6E_D1, ES_D1, YM, CL_D2, ALL8) or inside +-MDE (6E_D2, GC, ES_D2, CL_D1: inconclusive nulls, an edge smaller than the MDE cannot be excluded, but none is positive and none passes the holdout/SPAN23 sign checks). Placebos: lib = equal-count random library books (rank of the cell; all well below 0.95), time = timing-destroyed (permuted signals; ranks 0.3-0.7 are not informative when the cell is negative by cost). Marginal Sharpe vs DS2 10/10/7: not up for any cell. Corr to DS2 about 0 (|r| < 0.1 for all baskets), so the failure is the standalone sign, not diversification. Failed criteria on the representative cells: holdout mean > 0, marginal Sharpe up, placebo >= 0.95, SPAN23 agrees, WF mean > 0. Trades/wk meets the 3/wk bar (3.9-4.8 per market-leg; 35-72 for baskets) so the cells were measurable.

## Executability
Deliverable in principle: 1-min bars of ES/YM/ZN/ZB/ZF/6E/CL/GC in NT8 on a 1-minute chart, ET sessions as in the prereg, signals known at the first-30 close (D1) or the prior close (D2), entries and exits as market orders at the open of a named 1-min bar (D1: entry at open of the first last-30 bar, exit near the final bar with 1 tick extra slip; D2: next session open, exit 60 minutes later), one trade per market per day. Exec status in the rows is PENDING because no cell reached PASS, so no SPEC and no identity test were written. Not recommended: a replay would be moot.

## Widening / own hypotheses
No 3x3 widening owed. No further genuine hypothesis found beyond the 19 cells; a sign-flipped (reversal) variant or a threshold filter (trade only when |r1| exceeds the k-th percentile) would be a new family needing its own prereg and, given costs here, would need an edge several times the cost of 3 ticks per trade; not scored.
