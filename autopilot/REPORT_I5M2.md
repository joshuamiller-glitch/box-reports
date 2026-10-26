# REPORT_I5M2 - IDEAS-5000 A-D as METHOD-2 families (scored with ap_m2; POWER2 configuration)
2026-10-17. Config: fit 12 / read 3 / step 3, tilt, first OOS week 2024-02 (142 OOS weeks), gates a-d (OOS Sharpe and net > 0; null rank >= 0.95; 4-week block bootstrap lower bound > 0; both OOS halves net > 0), halves 2024-02..2025-04 / 2025-05..2026-10. Engine exec_engine v2 ECON, every cell kept (losers included), order-handling rule in the family id. Null: custom drift-matched random-entry copy from this engine (ap_m2_i5score.py): each cell's setups re-placed on random eligible decision rows of the same clock / conditioner mask / year with the same number of setups and side counts per year, depth/stop/target/life/hold re-assigned within the year, re-run under the cell's own rule; 200 replicates; cells with similar trade counts share timing (cell correlations survive). Per-family rows are in outputs/methods2/FAMILY_RESULTS.csv (plateau breadth and power class included); full table outputs/methods2/I5_FAMILY_SCORES.csv; OOS series and nulls outputs/methods2/oos/.
## Counts (252 families: A 72, B 54, C 72, D 54; 20,348 cells)
| kind | families | OOS Sharpe > 0 | null rank >= 0.95 | gates a-d pass | median OOS Sharpe | best |
|---|---|---|---|---|---|---|
| A (impulse x rule x clock T3/V1) | 72 | 12 | 28 | 1 | -0.57 | 0.96 |
| B (clock groups) | 54 | 17 | 25 | 3 | -0.42 | 1.31 |
| C (conditioner sets) | 72 | 9 | 8 | 0 | -0.49 | 0.98 |
| D (other instruments) | 54 | 7 | 3 | 0 | -0.86 | 0.60 |
The executable basis (v2, 1 tick/side + commission, 1-minute rows) makes most of these books negative; the null (random entries at the same structure) is also negative (cost-laden), so a family can have OOS Sharpe < 0 and still rank high against its own null; gate a removes those.
## Families that pass gates a-d
| family | OOS Sharpe | null rank | boot lo | halves | pair corr | plateau breadth / class | best-of-F rank: nominal F=252 | F = registry (1,582) | F_eff = 156 (clusters of the A-D OOS series) |
|---|---|---|---|---|---|---|---|---|---|
| M2-B-A9-ffw-Renko | 1.307 | 1.000 | +0.079 | 2.26 / 0.68 | -0.01 | 0.36 peaked | 0.188 | 0.000 | 0.356 |
| M2-B-A9-ffw-Range | 1.167 | 1.000 | +0.034 | 2.51 / 0.55 | +0.01 | 0.00 peaked | 0.174 | 0.000 | 0.339 |
| M2-B-A4-ffw-Tother | 0.968 | 1.000 | +0.007 | 0.08 / 1.90 | +0.04 | -0.37 peaked | 0.123 | 0.000 | 0.274 |
| M2-A-A9-nro-V1 | 0.964 | 1.000 | +0.003 | 1.13 / 0.88 | +0.06 | 0.44 peaked | 0.123 | 0.000 | 0.273 |
Effective F: nominal 252 (A-D), registry 1,582 ready families; the A-D OOS series cluster into 156 groups at correlation >= 0.5 (greedy leader) with a participation-ratio effective number of 30.4; the global clustering of the registry (F_CLUSTERS.csv, 1,553 families) gives 594 clusters / 55.6 participation ratio. Best-of-F ranks use G(s)^F with the pooled null sample of the 252 families. The gate (a778's REPORT_FAMILIES) is F_eff = 447; none of the four reaches 0.95 under any of these F values.
Plateau classes of the 252: flat 0, peaked 233, no fit edge 19 (breadth = mean fit-window Sharpe of the cells within Hamming distance 2 of the best fit cell, relative to it, on the first 12-month fit window; flat >= 0.885). Every family is peaked, i.e. the lower power class of POWER2 applies (about 38% power at Sharpe 1.5): a real A-D effect of Sharpe 1.0 would usually be missed.
## Verdicts
No A-D family passes METHOD-2 (gates a-d plus best-of-F rank >= 0.95): 0 PASS. Four pass the single-family gates (all peaked plateau, all failing multiplicity). Renko ES replication (M2-REPL3) passed the pre-registered rule (OOS 0.784 >= 0.654), Range ES failed; per REPORT_RENKO_RANGE_VERIFY the Renko/Range results depend on the engine's 1-minute-row bar rule (tick-built bars give negative expectancy), so neither is a candidate for an NT8-native implementation. LIVEPACK: packs emitted PROVISIONAL for the M2-REPL list only (M2-B-A9-ffw-Renko, M2-B-A9-ffw-Range, I9_IBS_dipbuy, K4_longonly_RW); no other A-D family qualifies for a pack. Factor section: the four passing families have pair correlation |r| <= 0.06 and are one bet only if their OOS series correlate >= 0.5 (Renko and Range both rest on A9; computed in I5_effective_F.json clusters).
DONE I5M2
