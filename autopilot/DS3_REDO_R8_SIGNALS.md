# DS3_REDO_R8_SIGNALS - live books' own signal parameters on the state base (REDO-R8, T-STACK-REDO addendum R8)
Version 2026-11-10 12:37Z (first-order SCREEN; exact pending). Label **PRE-PROOF** (entry match to the live week < .85 program-wide) and **FIRST-ORDER SCREEN ONLY**: nothing here is a PASS; every recommendation below needs the exact engine (SZ queue prefix `R8_`, tier 2) before it is a verdict. Post-hoc, Shadow only. Prereg: `autopilot/DS3_REDO_R8_PREREG.md` (sha line in DECISIONS.md; amendments listed in section 8). Instruments: NQ only (the live D7 books). Code `code/th_r8/`, stores `/mnt/l2/l2vast/_th_r8/`.

## 0. Method in six lines (read this before the tables)
1. Signals regenerated on the 1-min NQ store with the live arithmetic copied from DS7.cs (ports.py): Keltner, St10, HMA/VWAP flip, MomentumVote, PbEngine (Pb3 = P7, Pb7 = A7), OpenDrive; live parameters = the REFERENCE row of each grid (identity of the signal list vs the live trades: 'signal match' column).
2. Each signal is simulated NAKED on the 1-s tape (60/60; O7 40/90 to 16:00; live time blocks, one position per book, 16:55 flatten, session lot table x slot/B02 halves x ER Q1-A, entry at the signal-bar close, stop slip 1.5 pt), ROLL-EXCL weight 0 for trades spanning a >20-pt roll gap.
3. DRESSING (the point of R8): the naked series is mapped to a dressed series by a per-book surrogate `g[exit kind, MAE bin]` = mean S1b-COMB P&L per lot of the live-matched trades in the bin (it carries the state cut / locks / zones of the live stack: a trade that dips 30+ pts before the target is on average a cut loser, not a win). Fitted on the live cell and applied identically to every neighbour; an out-of-sample check (fit before 2025-01, evaluate after) gives the same correlation (see section 1).
4. DELTA METHOD: dressed book(cell) = S1b-COMB book + r_b x (surrogate(cell) - surrogate(live)), r_b = clipped weekly regression slope of the COMB book on the live surrogate; stack(cell) = S1b-COMB stack with the book swapped. The reference row is S1b-COMB to the dollar (delta 0).
5. Metrics: stack maxDD / worst-20 / Ulcer on ALL weeks, carrying week dropped from means only; equal-lots cut and EQUAL-MEAN cut (one global lot scale so the L6M mean equals live's); ranking key = mean of the equal-mean cut on L6M, L3M, L1M (standing rule 2, drawdown first, mean tie-break); PRE/X' tolerant label by rule 2a (`Z.prior_info`); bi-weekly walk-forward (trailing 26 w -> next 2 w, purge 7 d, lowest trailing stack maxDD among the book's cells, live default) on the STACK series; placebo = shared random circular week shift of all deltas (300 draws), own p and FAMILY max-stat p over the whole neighbourhood; held-out frozen live week 2026-11-02..05 = delta vs live.
6. Plateau rule: a cell is a plateau centre only when >= 75% of its +-1 grid neighbours beat live at equal mean in recents AND the neighbours' mean key is >= 80% of its own; otherwise it is a spike/edge and cannot be the proposal. A change is RECOMMENDED only when the best plateau centre passes ALL of: key > 0, OK-PRIOR, bi-weekly WF beat >= 50% with cut > 0, family p <= .10, live-week delta not worse than -1 weekly MDE. Everything else: the live setting stays.

## 1. Calibration of the dressing (does the first-order trade list resemble the live book?)
| book | live-cell sim trades | live trades (S1b-COMB) | signal match (+-1 s) | r_b (COMB weekly slope on surrogate) | weekly corr naked / surrogate | note |
|---|---|---|---|---|---|---|
| KB | 7509 | 7185 | 0.63 | 0.75 | 0.68 / 0.69 | OOS dressing (fit < 2025, weeks >= 2025): corr 0.64 vs naked 0.62 |
| SM | 1394 | 1373 | 0.79 | 0.72 | 0.75 / 0.77 | OOS dressing (fit < 2025, weeks >= 2025): corr 0.76 vs naked 0.74 |
| HM | 1079 | 1116 | 0.73 | 0.78 | 0.73 / 0.74 | OOS dressing (fit < 2025, weeks >= 2025): corr 0.73 vs naked 0.72 |
| MV | 3277 | 4525 | 0.63 | 0.73 | 0.54 / 0.58 | OOS dressing (fit < 2025, weeks >= 2025): corr 0.62 vs naked 0.54 |
| PE | 5697 | 5270 | 0.59 | 0.71 | 0.70 / 0.73 | OOS dressing (fit < 2025, weeks >= 2025): corr 0.73 vs naked 0.70 |
| PB | 1211 | 1160 | 0.67 | 0.96 | 0.89 / 0.90 | OOS dressing (fit < 2025, weeks >= 2025): corr 0.88 vs naked 0.87 |
| OD | 498 | 506 | 0.91 | 0.93 | 0.85 / 0.88 | OOS dressing (fit < 2025, weeks >= 2025): corr 0.90 vs naked 0.89 |

The surrogate is mean-calibrated per (kind, MAE bin) on the live-matched trades only; unmatched live trades (re-entries after state cuts, L2-gate/confirm timing) are not modelled, which is why signal match is 60-80% and the weekly correlation 0.6-0.9. This is the limit of a first-order screen; the exact engine runs below remove it for the finalists.

## 2. KB (K7) - 129 cells

| cell | stack maxDD cut % L6M/L3M/L1M (equal lots) | same at EQUAL MEAN | key (eq-mean avg) | d mean $/wk L6M / HOLD (equal lots) | cut % HOLD / PRE / X' | d mean PRE | PRIOR (2a) | bi-weekly WF: cut % / beat % | p own | p family | nb beating live | live-wk delta $ | signal match to live |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| KB_e14_m1.0_b3 **(LIVE)** | 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 | 0.0 | 0 / 0 | 0.0 / 0.0 / 0.0 | 0 | OK-PRIOR | 7.6 / 62 | 1.000 | 1.000 | 2/5 spike/edge | 0 | 0.63 |
| KB_e17_m1.5_b1 | 11.7 / 11.7 / 21.3 | 16.4 / 16.4 / 25.5 | 19.4 | 1409 / 167 | 9.5 / -16.6 / 1.1 | -214 | OK-PRIOR | 7.6 / 62 | 0.010 | 0.269 | 3/5 spike/edge | 3413 | 0.05 |
| KB_e10_m1.0_b1 | 18.6 / 18.6 / 18.5 | 15.4 / 15.4 / 15.3 | 15.3 | -884 / -1927 | -1.9 / -9.5 / 11.4 | -702 | OK-PRIOR | 7.6 / 62 | 0.020 | 0.365 | 2/3 spike/edge | 8844 | 0.04 |
| KB_e20_m1.0_b1 | 2.6 / 2.6 / 14.8 | 9.7 / 9.7 / 21.1 | 13.5 | 1778 / -234 | -8.6 / 11.3 / -4.6 | -917 | OK-PRIOR | 7.6 / 62 | 0.070 | 0.777 | 3/4 spike/edge | 7130 | 0.03 |
| KB_e20_m2.0_b1 | 5.1 / 5.1 / 12.5 | 9.7 / 9.7 / 16.7 | 12.0 | 1253 / 327 | 1.5 / 0.4 / 12.3 | -832 | OK-PRIOR | 7.6 / 62 | 0.010 | 0.385 | 5/5 spike/edge | 1140 | 0.07 |
| KB_e17_m1.0_b1 | 10.5 / 10.5 / 10.5 | 12.0 / 12.0 / 11.9 | 11.9 | 377 / 598 | -2.4 / 22.4 / 19.5 | -1138 | RECENT-ONLY | 7.6 / 62 | 0.043 | 0.279 | 2/4 spike/edge | 7060 | 0.03 |
| KB_e14_m1.5_b1 | -0.1 / 0.8 / 26.3 | 3.1 / 4.0 / 28.6 | 11.9 | 809 / -157 | 5.0 / -9.9 / -1.9 | -1116 | RECENT-ONLY | 7.6 / 62 | 0.196 | 0.967 | 4/5 spike/edge | 4646 | 0.06 |
| KB_e12_m1.5_b1 | 7.4 / 7.4 / 11.0 | 10.6 / 10.6 / 14.1 | 11.7 | 802 / -864 | 7.6 / -8.7 / 24.4 | -1196 | RECENT-ONLY | 7.6 / 62 | 0.056 | 0.698 | 4/5 spike/edge | 1038 | 0.06 |
| KB_e12_m1.25_b1 | 11.4 / 11.4 / 12.9 | 7.8 / 7.8 / 9.4 | 8.3 | -1085 / -596 | -4.8 / -10.6 / 0.5 | -1635 | RECENT-ONLY | 7.6 / 62 | 0.037 | 0.535 | 4/5 PLATEAU | 9516 | 0.05 |

Best cell by key: **KB_e17_m1.5_b1** (key 19.4; SPIKE/EDGE: not a plateau centre); best plateau centre: **KB_e12_m1.25_b1** (key 8.3). Family p of the best cell (max-stat over all 129 cells, shift null): 0.269. Procedure WF (bi-weekly re-pick over this neighbourhood, vs live): cut 7.6 %, beat 62 % of 74 refit periods (74 switches), d mean -296 $/wk.

Landscape (key = equal-mean stack cut %, L6M/L3M/L1M average; live = 0 by construction). Rows/cols = grid indices of the parameter order in the cell name; one matrix per (3rd, 4th) index:

`e10_m1.0_b1 ... e30_m3.0_b1` (slice 0,0)

|   a0 |    0 |     1 |    2 |    3 |    4 |     5 |
|-----:|-----:|------:|-----:|-----:|-----:|------:|
|    0 | 15.3 |  -1.5 |  3.4 | -2.4 | -8.4 | -19.6 |
|    1 |  9.3 |   8.3 | 11.7 |  5.7 | -9.1 | -12.9 |
|    2 | -1.1 |  10.8 | 11.9 | -1.1 |  6.7 |  -8.5 |
|    3 | 11.9 | -12.7 | 19.4 |  2.2 |  2.1 |  -2.9 |
|    4 | 13.5 |  -0.1 |  2.7 | 12   |  1.3 |  -4.4 |
|    5 |  8.8 |  11.3 |  6   |  7.1 |  9.8 | -19.5 |
|    6 | -3.9 |   0.7 | -6.1 |  9.8 | -3.3 |   5.5 |

`e10_m1.0_b3 ... e30_m3.0_b3` (slice 1,0)

|   a0 |    0 |     1 |    2 |     3 |     4 |     5 |
|-----:|-----:|------:|-----:|------:|------:|------:|
|    0 |  5.2 |   6.6 | -4.5 |   1.1 | -12.8 |  -7.7 |
|    1 | -1.2 |   4.3 | -1.8 | -16.5 |  -7.6 |  -8.7 |
|    2 |  0   | -10.2 |  2.8 |  -8.2 |  -2.9 | -10.8 |
|    3 |  2.5 |   4.5 | -2.5 |  -5.3 | -17.5 |  -8.1 |
|    4 |  3.7 |  -7.2 | -6.8 |   0.9 |  -3.8 |  -4.1 |
|    5 |  1.7 |  -6.3 |  4.1 |   8.2 | -16.2 | -11.3 |
|    6 |  1.9 | -11.6 |  2.3 |   3.1 |  -2.5 |  -8.9 |

`e10_m1.0_b5 ... e30_m3.0_b5` (slice 2,0)

|   a0 |    0 |    1 |    2 |     3 |     4 |     5 |
|-----:|-----:|-----:|-----:|------:|------:|------:|
|    0 | -1.3 |  3   |  2.3 |  -9.4 |  -8.8 | -11   |
|    1 | -1.1 | -1.8 | -4   | -13.6 | -11   | -13.5 |
|    2 |  6.8 |  2.4 | -7.1 |  -9.1 |   0.1 | -12.3 |
|    3 | -0.5 |  7.8 |  6.2 | -13.2 |   1   | -20.5 |
|    4 |  1.2 |  3.2 |  2   |  -7.2 |  -3.6 |  -0.8 |
|    5 | -3.8 | -5.7 |  4.1 |  -5.4 |  -1.9 |  -6.3 |
|    6 | -8.9 | -6.5 |  4.6 |   1.3 |   2.8 |  -8.8 |

Old-vs-new (old = judge naked, as discovered: key on the NAKED delta, no dressing; new = dressed surrogate): naked top-3 KB_e25_m2.5_b1 (naked rank 1..3 -> dressed rank 10), KB_e17_m1.5_b1 (naked rank 1..3 -> dressed rank 1), KB_e30_m3.0_b1 (naked rank 1..3 -> dressed rank 24); dressed top-3 KB_e17_m1.5_b1 (naked rank 2), KB_e10_m1.0_b1 (naked rank 24), KB_e20_m1.0_b1 (naked rank 33). The live reference row is identical to S1b-COMB to the dollar by construction (delta 0), so the base-change proof is the identity of the reference row; a changed ranking between old and new is the effect of dressing, not a testing defect.

**Verdict KB: KEEP LIVE** - RECENT-ONLY/prior RECENT-ONLY; family p 0.269.

Exact status: fd_hooks kb{ema,atr,mult} (3-min only); bar 1/5 via r8_hooks bar-swap. Panel field(s): KbEmaPeriod / KbAtrPeriod / KbMult / KbBarMinutes (K7 signal bar).

## 3. SM (U7) - 60 cells

| cell | stack maxDD cut % L6M/L3M/L1M (equal lots) | same at EQUAL MEAN | key (eq-mean avg) | d mean $/wk L6M / HOLD (equal lots) | cut % HOLD / PRE / X' | d mean PRE | PRIOR (2a) | bi-weekly WF: cut % / beat % | p own | p family | nb beating live | live-wk delta $ | signal match to live |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SM_a7_m3.0_b10 **(LIVE)** | 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 | 0.0 | 0 / 0 | 0.0 / 0.0 / 0.0 | 0 | OK-PRIOR | 14.0 / 51 | 1.000 | 1.000 | 4/5 spike/edge | 0 | 0.79 |
| SM_a7_m2.5_b5 | 20.7 / 21.2 / 21.1 | 29.2 / 29.6 / 29.5 | 29.5 | 3010 / 1810 | -0.2 / 19.9 / 2.3 | -690 | OK-PRIOR | 14.0 / 51 | 0.003 | 0.010 | 4/4 spike/edge | 5360 | 0.01 |
| SM_a21_m2.5_b5 | 18.4 / 18.4 / 36.0 | 23.3 / 23.3 / 39.8 | 28.8 | 1754 / 1225 | -1.9 / 19.6 / -6.2 | -911 | OK-PRIOR | 14.0 / 51 | 0.003 | 0.010 | 4/4 spike/edge | 7172 | 0.01 |
| SM_a10_m2.5_b5 | 22.5 / 23.5 / 23.4 | 27.6 / 28.6 / 28.5 | 28.3 | 1726 / 1330 | 3.9 / 21.7 / 0.4 | -1199 | RECENT-ONLY | 14.0 / 51 | 0.003 | 0.010 | 5/5 spike/edge | 5360 | 0.01 |
| SM_a7_m2.0_b10 | 13.5 / 13.5 / 25.8 | 22.6 / 22.6 / 33.6 | 26.3 | 2628 / 2214 | 7.8 / 14.0 / -15.5 | -1679 | RECENT-ONLY | 14.0 / 51 | 0.003 | 0.103 | 3/4 spike/edge | 10413 | 0.09 |
| SM_a21_m2.0_b5 | 16.9 / 16.9 / 16.8 | 24.7 / 24.7 / 24.6 | 24.7 | 2608 / 1572 | -1.8 / 24.8 / -31.3 | -1600 | RECENT-ONLY | 14.0 / 51 | 0.003 | 0.010 | 3/3 PLATEAU | 17921 | 0.00 |
| SM_a14_m2.5_b5 | 18.3 / 18.3 / 18.3 | 24.4 / 24.4 / 24.3 | 24.4 | 2212 / 1123 | 1.4 / 18.7 / -2.5 | -1508 | RECENT-ONLY | 14.0 / 51 | 0.003 | 0.010 | 5/5 PLATEAU | 5360 | 0.01 |
| SM_a21_m2.0_b10 | 22.6 / 22.6 / 22.9 | 22.5 / 22.5 / 22.7 | 22.6 | -41 / 1276 | 2.0 / 6.7 / 7.3 | -1052 | RECENT-ONLY | 14.0 / 51 | 0.010 | 0.043 | 3/4 spike/edge | 266 | 0.18 |

Best cell by key: **SM_a7_m2.5_b5** (key 29.5; SPIKE/EDGE: not a plateau centre); best plateau centre: **SM_a21_m2.0_b5** (key 24.7). Family p of the best cell (max-stat over all 60 cells, shift null): 0.010. Procedure WF (bi-weekly re-pick over this neighbourhood, vs live): cut 14.0 %, beat 51 % of 74 refit periods (74 switches), d mean -502 $/wk.

Landscape (key = equal-mean stack cut %, L6M/L3M/L1M average; live = 0 by construction). Rows/cols = grid indices of the parameter order in the cell name; one matrix per (3rd, 4th) index:

`a7_m2.0_b5 ... a21_m4.0_b5` (slice 0,0)

|   a0 |    0 |    1 |    2 |    3 |    4 |
|-----:|-----:|-----:|-----:|-----:|-----:|
|    0 | 15.3 | 29.5 | 19.4 | 14.9 | 12.3 |
|    1 | 11.8 | 28.3 |  6.1 | 11.8 | 11.8 |
|    2 | 19.3 | 24.4 | 15.1 | 16.2 | -7   |
|    3 | 24.7 | 28.8 | 16   | 13   |  6.3 |

`a7_m2.0_b10 ... a21_m4.0_b10` (slice 1,0)

|   a0 |    0 |    1 |     2 |    3 |     4 |
|-----:|-----:|-----:|------:|-----:|------:|
|    0 | 26.3 | 16.5 |   0   |  6.1 |  10.9 |
|    1 | 19.5 | 17.5 | -12.2 | 10.9 |  -5.2 |
|    2 | 13.9 | 11.9 | -10.4 |  8.3 | -17.2 |
|    3 | 22.6 |  7.9 |  -9.4 |  5.6 | -13.7 |

`a7_m2.0_b15 ... a21_m4.0_b15` (slice 2,0)

|   a0 |     0 |     1 |    2 |    3 |    4 |
|-----:|------:|------:|-----:|-----:|-----:|
|    0 |  -9.4 | -16.8 |  2.9 |  3.5 | 11.1 |
|    1 | -14.3 | -19.1 |  4.1 | -1.9 |  6   |
|    2 | -10.9 |  -0.4 | -5.8 | -4.9 | 11.8 |
|    3 |  -8.7 |   7.9 |  3.2 |  1.9 |  0.4 |

Old-vs-new (old = judge naked, as discovered: key on the NAKED delta, no dressing; new = dressed surrogate): naked top-3 SM_a21_m2.5_b5 (naked rank 1..3 -> dressed rank 2), SM_a7_m2.5_b5 (naked rank 1..3 -> dressed rank 1), SM_a10_m2.5_b5 (naked rank 1..3 -> dressed rank 3); dressed top-3 SM_a7_m2.5_b5 (naked rank 2), SM_a21_m2.5_b5 (naked rank 1), SM_a10_m2.5_b5 (naked rank 3). The live reference row is identical to S1b-COMB to the dollar by construction (delta 0), so the base-change proof is the identity of the reference row; a changed ranking between old and new is the effect of dressing, not a testing defect.

**Verdict SM: KEEP LIVE** - RECENT-ONLY/prior RECENT-ONLY.

Exact status: fd_hooks sm{atr,mult} (10-min only); bar 5/15 via r8_hooks bar-swap. Panel field(s): SmAtrPeriod / SmMult / EmBarMinutes (U7 signal bar).

## 4. HM (H7) - 59 cells

| cell | stack maxDD cut % L6M/L3M/L1M (equal lots) | same at EQUAL MEAN | key (eq-mean avg) | d mean $/wk L6M / HOLD (equal lots) | cut % HOLD / PRE / X' | d mean PRE | PRIOR (2a) | bi-weekly WF: cut % / beat % | p own | p family | nb beating live | live-wk delta $ | signal match to live |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM_f20_s55_b5_fixed **(LIVE)** | 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 | 0.0 | 0 / 0 | 0.0 / 0.0 / 0.0 | 0 | OK-PRIOR | -1.2 / 46 | 1.000 | 1.000 | 3/6 spike/edge | 0 | 0.73 |
| HM_f34_s55_b1_fixed | 10.8 / 10.8 / 10.7 | 25.1 / 25.1 / 25.0 | 25.0 | 4379 / 5554 | 0.6 / -0.0 / -20.5 | 432 | OK-PRIOR | -1.2 / 46 | 0.096 | 0.186 | 4/4 spike/edge | 13994 | 0.00 |
| HM_f20_s75_b1_fixed | 6.3 / 6.3 / 21.5 | 19.5 / 19.5 / 32.6 | 23.9 | 3784 / 4496 | 2.2 / 1.5 / -6.1 | 972 | OK-PRIOR | -1.2 / 46 | 0.113 | 0.239 | 5/5 spike/edge | 14102 | 0.00 |
| HM_f14_s75_b1_sess | 5.5 / 5.5 / 20.6 | 18.0 / 18.0 / 31.1 | 22.4 | 3489 / 3173 | -1.1 / -1.2 / -9.4 | -28 | OK-PRIOR | -1.2 / 46 | 0.066 | 0.286 | 5/5 spike/edge | 629 | 0.00 |
| HM_f27_s75_b1_fixed | 8.0 / 8.0 / 7.9 | 22.2 / 22.2 / 22.1 | 22.2 | 4620 / 5034 | -11.0 / -4.8 / -11.9 | 621 | OK-PRIOR | -1.2 / 46 | 0.100 | 0.209 | 4/5 spike/edge | 17549 | 0.00 |
| HM_f27_s34_b1_fixed | -1.0 / -1.0 / 10.3 | 18.4 / 18.4 / 27.5 | 21.5 | 6063 / 6452 | 10.1 / 7.6 / 14.9 | 816 | OK-PRIOR | -1.2 / 46 | 0.169 | 0.249 | 4/4 spike/edge | 30976 | 0.00 |
| HM_f14_s55_b1_sess | 5.1 / 5.1 / 5.0 | 18.6 / 18.6 / 18.5 | 18.6 | 4205 / 5008 | -3.5 / -0.2 / -16.6 | 870 | OK-PRIOR | -1.2 / 46 | 0.110 | 0.249 | 5/6 spike/edge | 27158 | 0.00 |
| HM_f34_s55_b1_sess | 1.4 / 1.4 / 17.7 | 13.2 / 13.2 / 27.5 | 18.0 | 3164 / 4763 | -7.4 / 1.2 / -15.9 | 1289 | OK-PRIOR | -1.2 / 46 | 0.179 | 0.379 | 2/4 spike/edge | 2971 | 0.00 |
| HM_f27_s55_b1_fixed | -2.2 / 3.1 / 6.8 | 10.7 / 15.3 / 18.5 | 14.8 | 3322 / 4486 | -8.3 / 6.4 / 10.3 | 510 | OK-PRIOR | -1.2 / 46 | 0.169 | 0.482 | 5/6 PLATEAU | 6115 | 0.00 |

Best cell by key: **HM_f34_s55_b1_fixed** (key 25.0; SPIKE/EDGE: not a plateau centre); best plateau centre: **HM_f27_s55_b1_fixed** (key 14.8). Family p of the best cell (max-stat over all 59 cells, shift null): 0.186. Procedure WF (bi-weekly re-pick over this neighbourhood, vs live): cut -1.2 %, beat 46 % of 74 refit periods (74 switches), d mean 2153 $/wk.

Landscape (key = equal-mean stack cut %, L6M/L3M/L1M average; live = 0 by construction). Rows/cols = grid indices of the parameter order in the cell name; one matrix per (3rd, 4th) index:

`f9_s34_b1_fixed ... f34_s75_b1_fixed` (slice 0,0)

|   a0 |     0 |    1 |    2 |
|-----:|------:|-----:|-----:|
|    0 |   9.6 |  7.9 |  4.5 |
|    1 |  11.4 | 17.8 | 11.1 |
|    2 |  14.6 | 16.4 | 23.9 |
|    3 |  21.5 | 14.8 | 22.2 |
|    4 | nan   | 25   |  5.6 |

`f9_s34_b1_sess ... f34_s75_b1_sess` (slice 0,1)

|   a0 |     0 |    1 |    2 |
|-----:|------:|-----:|-----:|
|    0 |  -1.2 | 13.9 | 11.4 |
|    1 |  17.7 | 18.6 | 22.4 |
|    2 |  12.9 |  5.8 | 15.9 |
|    3 |  14.6 | 14.2 |  1.6 |
|    4 | nan   | 18   | -4.8 |

`f9_s34_b5_fixed ... f34_s75_b5_fixed` (slice 1,0)

|   a0 |     0 |    1 |     2 |
|-----:|------:|-----:|------:|
|    0 |  -8.4 |  4.9 |  -5.7 |
|    1 |  -8.7 |  1   |   7.8 |
|    2 |  -5   |  0   |   5.8 |
|    3 |   9.6 | -3.9 |  -0.8 |
|    4 | nan   |  6.3 | -12   |

`f9_s34_b5_sess ... f34_s75_b5_sess` (slice 1,1)

|   a0 |     0 |    1 |     2 |
|-----:|------:|-----:|------:|
|    0 | -19.7 | -6.8 |   5.2 |
|    1 | -10.8 | -3.1 |   0.7 |
|    2 |   0.9 | -4.1 |   3.6 |
|    3 |   9.2 | -3.8 |  -4.7 |
|    4 | nan   | -3.3 | -10.2 |

Old-vs-new (old = judge naked, as discovered: key on the NAKED delta, no dressing; new = dressed surrogate): naked top-3 HM_f27_s75_b1_fixed (naked rank 1..3 -> dressed rank 4), HM_f20_s75_b1_fixed (naked rank 1..3 -> dressed rank 2), HM_f14_s75_b1_sess (naked rank 1..3 -> dressed rank 3); dressed top-3 HM_f34_s55_b1_fixed (naked rank 4), HM_f20_s75_b1_fixed (naked rank 2), HM_f14_s75_b1_sess (naked rank 3). The live reference row is identical to S1b-COMB to the dollar by construction (delta 0), so the base-change proof is the identity of the reference row; a changed ranking between old and new is the effect of dressing, not a testing defect.

**Verdict HM: KEEP LIVE** - WF beat 46% cut -1.2; family p 0.186.

Exact status: r8_hooks hm{nF,nS,ema,anchor,bar}. Panel field(s): H7FastPeriod / H7SlowPeriod / H7EmaPeriod / HmVwapAnchor (5-min bucket hard-coded by StackHm5Repl).

## 5. MV (M7) - 34 cells

| cell | stack maxDD cut % L6M/L3M/L1M (equal lots) | same at EQUAL MEAN | key (eq-mean avg) | d mean $/wk L6M / HOLD (equal lots) | cut % HOLD / PRE / X' | d mean PRE | PRIOR (2a) | bi-weekly WF: cut % / beat % | p own | p family | nb beating live | live-wk delta $ | signal match to live |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| MV_t0.5_v4_L5 **(LIVE)** | 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 | 0.0 | 0 / 0 | 0.0 / 0.0 / 0.0 | 0 | OK-PRIOR | -0.4 / 51 | 1.000 | 1.000 | 0/4 spike/edge | 0 | 0.63 |
| MV_t0.75_v3_L5 | -0.7 / -0.7 / 10.5 | -1.2 / -1.2 / 10.1 | 2.6 | -106 / 215 | -2.0 / -3.2 / -5.4 | -150 | OK-PRIOR | -0.4 / 51 | 0.153 | 1.000 | 0/4 spike/edge | 203 | 0.14 |
| MV_t0.5_v3_long | 0.4 / 0.4 / 4.7 | -0.4 / -0.4 / 3.9 | 1.0 | -200 / -175 | 14.4 / -0.2 / 8.6 | -23 | OK-PRIOR | -0.4 / 51 | 0.435 | 1.000 | 0/0 spike/edge | -2211 | 0.13 |
| MV_t0.5_v3_no240 | -3.2 / -3.2 / 5.8 | -2.1 / -2.1 / 6.9 | 0.9 | 256 / -19 | -0.2 / -2.8 / -9.1 | -443 | OK-PRIOR | -0.4 / 51 | 0.375 | 1.000 | 0/0 spike/edge | 2084 | 0.36 |
| MV_t0.5_v4_no240 | -1.4 / -1.4 / -1.5 | 0.1 / 0.1 / -0.0 | 0.1 | 357 / 137 | 7.8 / -3.9 / 5.2 | -162 | OK-PRIOR | -0.4 / 51 | 0.136 | 0.777 | 0/0 spike/edge | 362 | 0.22 |
| MV_t0.5_v2_long | -1.8 / -1.8 / -1.9 | -0.2 / -0.2 / -0.3 | -0.3 | 419 / 162 | 9.8 / -1.3 / 7.0 | -506 | OK-PRIOR | -0.4 / 51 | 0.279 | 1.000 | 0/0 spike/edge | -115 | 0.23 |
| MV_t0.5_v3_no15 | 0.1 / 0.1 / 5.3 | -2.4 / -2.4 / 3.0 | -0.6 | -640 / 3 | 5.3 / -3.0 / 5.6 | -341 | OK-PRIOR | -0.4 / 51 | 0.206 | 1.000 | 0/0 spike/edge | -4149 | 0.32 |
| MV_t0.5_v3_short | -4.1 / -4.1 / -4.3 | -0.6 / -0.6 / -0.7 | -0.6 | 806 / 556 | 6.3 / -6.4 / -0.5 | -361 | OK-PRIOR | -0.4 / 51 | 0.216 | 0.897 | 0/0 spike/edge | -973 | 0.14 |

Best cell by key: **MV_t0.75_v3_L5** (key 2.6; SPIKE/EDGE: not a plateau centre); best plateau centre: **none** (key ). Family p of the best cell (max-stat over all 34 cells, shift null): 0.777. Procedure WF (bi-weekly re-pick over this neighbourhood, vs live): cut -0.4 %, beat 51 % of 74 refit periods (73 switches), d mean -188 $/wk.

Landscape (key = equal-mean stack cut %, L6M/L3M/L1M average; live = 0 by construction). Rows/cols = grid indices of the parameter order in the cell name; one matrix per (3rd, 4th) index:

`t0.25_v2_L5 ... t1.0_v5_L5` (slice 0,0)

|   a0 |     0 |    1 |     2 |     3 |
|-----:|------:|-----:|------:|------:|
|    0 | -11.2 | -3.1 |  -6.3 | -11.9 |
|    1 |  -3.5 | -1.7 |  -5   | -12.3 |
|    2 |  -7.8 | -3.6 |   0   |  -5.7 |
|    3 |  -5.5 |  2.6 |  -7   |  -6.8 |
|    4 |  -4.5 | -3.9 | -20.3 |  -2.6 |

Old-vs-new (old = judge naked, as discovered: key on the NAKED delta, no dressing; new = dressed surrogate): naked top-3 MV_t0.5_v3_long (naked rank 1..3 -> dressed rank 2), MV_t1.0_v2_L5 (naked rank 1..3 -> dressed rank 17), MV_t0.5_v3_L5 (naked rank 1..3 -> dressed rank 14); dressed top-3 MV_t0.75_v3_L5 (naked rank 4), MV_t0.5_v3_long (naked rank 1), MV_t0.5_v3_no240 (naked rank 6). The live reference row is identical to S1b-COMB to the dollar by construction (delta 0), so the base-change proof is the identity of the reference row; a changed ranking between old and new is the effect of dressing, not a testing defect.

**Verdict MV: KEEP LIVE** - no plateau centre (best cell is a spike/edge).

Exact status: r8_hooks mv{thr,votes,look}. Panel field(s): MvThreshold / MvVotes (lookback set 15,30,60,120,240 is a constant, MomentumVote L2396).

## 6. PE (P7) - 107 cells

| cell | stack maxDD cut % L6M/L3M/L1M (equal lots) | same at EQUAL MEAN | key (eq-mean avg) | d mean $/wk L6M / HOLD (equal lots) | cut % HOLD / PRE / X' | d mean PRE | PRIOR (2a) | bi-weekly WF: cut % / beat % | p own | p family | nb beating live | live-wk delta $ | signal match to live |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PE_r5_a30_T2_e20 **(LIVE)** | 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 | 0.0 | 0 / 0 | 0.0 / 0.0 / 0.0 | 0 | OK-PRIOR | 26.5 / 45 | 1.000 | 1.000 | 5/6 spike/edge | 0 | 0.59 |
| PE_r10_a45_T2_e20 | 28.4 / 28.4 / 68.0 | 41.1 / 41.1 / 73.6 | 51.9 | 5259 / 2968 | 24.8 / 26.1 / 32.9 | -3738 | RECENT-ONLY | 26.5 / 45 | 0.003 | 0.130 | 6/7 spike/edge | 1784 | 0.40 |
| PE_r10_a60_T2_e20 | 35.4 / 42.9 / 42.9 | 44.7 / 51.2 / 51.1 | 49.0 | 4105 / -120 | 20.7 / 20.0 / 23.1 | -3313 | RECENT-ONLY | 26.5 / 45 | 0.003 | 0.090 | 3/6 spike/edge | -6318 | 0.39 |
| PE_r15_a45_T2_e20 | 8.0 / 43.3 / 61.6 | 22.5 / 52.3 / 67.7 | 47.5 | 4555 / 64 | 1.8 / 17.6 / 49.3 | -3065 | RECENT-ONLY | 26.5 / 45 | 0.040 | 0.472 | 6/6 spike/edge | -1607 | 0.36 |
| PE_r10_a15_T2_e20 | 18.7 / 20.4 / 74.0 | 19.7 / 21.4 / 74.3 | 38.5 | 286 / -193 | 9.1 / 2.3 / 35.6 | -3856 | RECENT-ONLY | 26.5 / 45 | 0.279 | 1.000 | 3/6 spike/edge | -1047 | 0.36 |
| PE_r5_a60_T2_e30 | 1.2 / 1.2 / 69.0 | 9.6 / 9.6 / 71.6 | 30.2 | 2157 / 4205 | 3.4 / 25.2 / 13.7 | -392 | OK-PRIOR | 26.5 / 45 | 0.306 | 1.000 | 2/5 spike/edge | 28071 | 0.16 |
| PE_r5_a45_T2_e30 | 2.4 / 2.4 / 74.1 | 7.0 / 7.0 / 75.3 | 29.8 | 1159 / 3386 | 3.7 / 29.8 / 5.7 | -2194 | RECENT-ONLY | 26.5 / 45 | 0.282 | 1.000 | 4/6 spike/edge | 21004 | 0.16 |
| PE_r5_a15_T2_e20 | 14.9 / 14.9 / 14.8 | 24.1 / 24.1 / 24.0 | 24.0 | 2685 / 3367 | 15.7 / -1.9 / 6.4 | -950 | OK-PRIOR | 26.5 / 45 | 0.060 | 0.439 | 3/5 spike/edge | -490 | 0.45 |
| PE_r15_a60_T2_e20 | 3.4 / 25.0 / 36.6 | -4.4 / 18.9 / 31.5 | 15.3 | -2071 / -2593 | -14.6 / 17.1 / 33.6 | -2182 | RECENT-ONLY | 26.5 / 45 | 0.060 | 0.864 | 4/5 PLATEAU | -15146 | 0.35 |

Best cell by key: **PE_r10_a45_T2_e20** (key 51.9; SPIKE/EDGE: not a plateau centre); best plateau centre: **PE_r15_a60_T2_e20** (key 15.3). Family p of the best cell (max-stat over all 107 cells, shift null): 0.090. Procedure WF (bi-weekly re-pick over this neighbourhood, vs live): cut 26.5 %, beat 45 % of 74 refit periods (74 switches), d mean -562 $/wk.

Landscape (key = equal-mean stack cut %, L6M/L3M/L1M average; live = 0 by construction). Rows/cols = grid indices of the parameter order in the cell name; one matrix per (3rd, 4th) index:

`r5_a15_T1_e10 ... r15_a60_T1_e10` (slice 0,0)

|   a0 |      0 |      1 |      2 |      3 |
|-----:|-------:|-------:|-------:|-------:|
|    0 |  -18.3 |  -31.5 |  -32.5 |  -32.5 |
|    1 | -111.8 | -155.7 | -177.6 | -177.6 |
|    2 |  -66.1 |  -92.3 |  -78.1 |  -78.1 |

`r5_a15_T1_e20 ... r15_a60_T1_e20` (slice 0,1)

|   a0 |    0 |     1 |     2 |     3 |
|-----:|-----:|------:|------:|------:|
|    0 |  9.9 |   0.9 |   0.2 |  -0.5 |
|    1 | -6.6 | -23.7 | -29.8 | -37.5 |
|    2 | 16.8 |   5.9 |  12.9 |   2.9 |

`r5_a15_T1_e30 ... r15_a60_T1_e30` (slice 0,2)

|   a0 |     0 |     1 |     2 |     3 |
|-----:|------:|------:|------:|------:|
|    0 | -24.5 |  -9.3 |  -3.1 |  -6.9 |
|    1 | -39   | -21.2 | -15   | -18.9 |
|    2 |   0.7 |   9.6 |   9.4 |  12.8 |

`r5_a15_T1_e40 ... r15_a60_T1_e40` (slice 0,3)

|   a0 |     0 |     1 |     2 |     3 |
|-----:|------:|------:|------:|------:|
|    0 | -68.2 | -77.6 | -73.1 | -71.6 |
|    1 | -85.2 | -96.5 | -93.7 | -93.9 |
|    2 | -63.3 | -63   | -40.2 | -14.5 |

`r5_a15_T2_e10 ... r15_a60_T2_e10` (slice 1,0)

|   a0 |     0 |     1 |     2 |     3 |
|-----:|------:|------:|------:|------:|
|    0 | -27.4 | -32.3 | -50.7 | -76.5 |
|    1 | -22.5 |  20.8 |   5   |  -3.3 |
|    2 | -18.7 |   0.2 |  21.1 |  -0.7 |

`r5_a15_T2_e20 ... r15_a60_T2_e20` (slice 1,1)

|   a0 |    0 |    1 |    2 |    3 |
|-----:|-----:|-----:|-----:|-----:|
|    0 | 24   |  0   | 18.7 | -6.1 |
|    1 | 38.5 | 18.1 | 51.9 | 49   |
|    2 |  8.7 |  3.9 | 47.5 | 15.3 |

`r5_a15_T2_e30 ... r15_a60_T2_e30` (slice 1,2)

|   a0 |     0 |     1 |    2 |    3 |
|-----:|------:|------:|-----:|-----:|
|    0 |   1.6 |   1.7 | 29.8 | 30.2 |
|    1 | -28.7 | -14.2 | 18.2 | 13.7 |
|    2 |   6.5 |  20.9 | 21.3 |  5.3 |

`r5_a15_T2_e40 ... r15_a60_T2_e40` (slice 1,3)

|   a0 |     0 |     1 |     2 |     3 |
|-----:|------:|------:|------:|------:|
|    0 | -27   | -43.9 | -13.9 | -16.4 |
|    1 | -79.2 | -69   | -51.3 | -53.1 |
|    2 | -62.3 | -61.5 | -29.5 | -48.9 |

Old-vs-new (old = judge naked, as discovered: key on the NAKED delta, no dressing; new = dressed surrogate): naked top-3 PE_r10_a45_T2_e20 (naked rank 1..3 -> dressed rank 1), PE_r15_a45_T2_e20 (naked rank 1..3 -> dressed rank 3), PE_r10_a60_T2_e20 (naked rank 1..3 -> dressed rank 2); dressed top-3 PE_r10_a45_T2_e20 (naked rank 1), PE_r10_a60_T2_e20 (naked rank 3), PE_r15_a45_T2_e20 (naked rank 2). The live reference row is identical to S1b-COMB to the dollar by construction (delta 0), so the base-change proof is the identity of the reference row; a changed ranking between old and new is the effect of dressing, not a testing defect.

**Verdict PE: KEEP LIVE** - RECENT-ONLY/prior RECENT-ONLY; WF beat 45% cut 26.5; live week delta -15146 < -MDE 13068.

Exact status: r8_hooks pb3{reg,arm,trig,ema,st}. Panel field(s): NONE (Pb3Rules constants in PbEngine L2225: regime bar 5, arm 30, trigger T2, EMA20 level): a new input would be needed.

## 7. PB (A7) - 96 cells

| cell | stack maxDD cut % L6M/L3M/L1M (equal lots) | same at EQUAL MEAN | key (eq-mean avg) | d mean $/wk L6M / HOLD (equal lots) | cut % HOLD / PRE / X' | d mean PRE | PRIOR (2a) | bi-weekly WF: cut % / beat % | p own | p family | nb beating live | live-wk delta $ | signal match to live |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB_r10_a15_d0.5_T1 **(LIVE)** | 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 | 0.0 | 0 / 0 | 0.0 / 0.0 / 0.0 | 0 | OK-PRIOR | -1.4 / 49 | 1.000 | 1.000 | 3/7 spike/edge | 0 | 0.67 |
| PB_r5_a10_d0.5_T1 | 2.3 / 2.3 / 12.8 | 5.0 / 5.0 / 15.2 | 8.4 | 781 / 744 | 1.4 / -5.0 / -9.2 | -277 | OK-PRIOR | -1.4 / 49 | 0.023 | 0.120 | 4/5 spike/edge | 5070 | 0.23 |
| PB_r5_a20_d0.5_T2 | -0.2 / -0.2 / 21.0 | 1.2 / 1.2 / 22.1 | 8.1 | 376 / 360 | 0.0 / -5.7 / -7.7 | -421 | OK-PRIOR | -1.4 / 49 | 0.116 | 0.478 | 5/6 spike/edge | 319 | 0.05 |
| PB_r5_a15_d0.5_T1 | 2.3 / 2.3 / 11.4 | 5.1 / 5.1 / 14.0 | 8.1 | 827 / 873 | 3.6 / -5.8 / -10.7 | -304 | OK-PRIOR | -1.4 / 49 | 0.023 | 0.120 | 4/6 spike/edge | 5070 | 0.24 |
| PB_r5_a20_d0.5_T1 | 2.3 / 2.3 / 10.1 | 5.2 / 5.2 / 12.8 | 7.7 | 850 / 919 | 3.6 / -5.8 / -10.7 | -279 | OK-PRIOR | -1.4 / 49 | 0.023 | 0.120 | 4/6 spike/edge | 5070 | 0.23 |
| PB_r5_a30_d0.5_T1 | 2.2 / 2.2 / 8.8 | 5.4 / 5.4 / 11.7 | 7.5 | 837 / 941 | 4.8 / -4.9 / -12.3 | -259 | OK-PRIOR | -1.4 / 49 | 0.023 | 0.120 | 3/5 spike/edge | 6840 | 0.23 |
| PB_r5_a15_d0.5_T2 | -0.2 / -0.2 / 18.7 | 0.5 / 0.5 / 19.3 | 6.8 | 196 / 110 | 0.0 / -8.2 / -5.9 | -517 | OK-PRIOR | -1.4 / 49 | 0.076 | 0.565 | 5/6 spike/edge | -1169 | 0.05 |
| PB_r5_a30_d0.5_T2 | -0.8 / -0.8 / 17.0 | 0.7 / 0.7 / 18.2 | 6.6 | 420 / 418 | 4.1 / -3.8 / -8.1 | -333 | OK-PRIOR | -1.4 / 49 | 0.120 | 0.548 | 4/5 spike/edge | 4032 | 0.05 |

Best cell by key: **PB_r5_a10_d0.5_T1** (key 8.4; SPIKE/EDGE: not a plateau centre); best plateau centre: **none** (key ). Family p of the best cell (max-stat over all 96 cells, shift null): 0.120. Procedure WF (bi-weekly re-pick over this neighbourhood, vs live): cut -1.4 %, beat 49 % of 74 refit periods (74 switches), d mean -159 $/wk.

Landscape (key = equal-mean stack cut %, L6M/L3M/L1M average; live = 0 by construction). Rows/cols = grid indices of the parameter order in the cell name; one matrix per (3rd, 4th) index:

`r5_a10_d0.25_T1 ... r15_a30_d0.25_T1` (slice 0,0)

|   a0 |    0 |    1 |    2 |    3 |
|-----:|-----:|-----:|-----:|-----:|
|    0 | -5.1 | -2.8 | -2.9 | -2.7 |
|    1 | -3.9 | -2.3 | -2.3 | -2.3 |
|    2 |  0.2 |  0.2 |  0.2 |  0.2 |

`r5_a10_d0.25_T2 ... r15_a30_d0.25_T2` (slice 0,1)

|   a0 |    0 |    1 |    2 |    3 |
|-----:|-----:|-----:|-----:|-----:|
|    0 | -7.5 | -4.4 | -5.5 | -6.5 |
|    1 | -5.9 | -4.6 | -6   | -6.3 |
|    2 | -6.9 | -5.7 | -7   | -5.6 |

`r5_a10_d0.5_T1 ... r15_a30_d0.5_T1` (slice 1,0)

|   a0 |    0 |    1 |    2 |    3 |
|-----:|-----:|-----:|-----:|-----:|
|    0 |  8.4 |  8.1 |  7.7 |  7.5 |
|    1 |  0.7 |  0   | -0.1 | -1   |
|    2 | -2.2 | -2.5 | -2.5 | -1.8 |

`r5_a10_d0.5_T2 ... r15_a30_d0.5_T2` (slice 1,1)

|   a0 |    0 |    1 |    2 |    3 |
|-----:|-----:|-----:|-----:|-----:|
|    0 |  4.5 |  6.8 |  8.1 |  6.6 |
|    1 | -0.1 |  2   |  2.2 |  1.2 |
|    2 | -0.9 | -1.4 | -1.1 | -1.2 |

`r5_a10_d0.75_T1 ... r15_a30_d0.75_T1` (slice 2,0)

|   a0 |    0 |    1 |    2 |    3 |
|-----:|-----:|-----:|-----:|-----:|
|    0 |  3.9 |  3.8 |  4   |  3   |
|    1 | -0.8 | -0.6 | -0.7 | -1.7 |
|    2 | -3.1 | -3.1 | -2.8 | -3.5 |

`r5_a10_d0.75_T2 ... r15_a30_d0.75_T2` (slice 2,1)

|   a0 |    0 |    1 |    2 |    3 |
|-----:|-----:|-----:|-----:|-----:|
|    0 |  6.5 |  4.8 |  4.3 |  5.8 |
|    1 | -0   | -1   | -1.3 | -1.5 |
|    2 | -1.7 | -3.2 | -3.8 | -1.8 |

`r5_a10_d1.0_T1 ... r15_a30_d1.0_T1` (slice 3,0)

|   a0 |    0 |    1 |     2 |    3 |
|-----:|-----:|-----:|------:|-----:|
|    0 | -9   | -9.9 | -10.3 | -8.9 |
|    1 | -9.6 | -9.1 |  -9   | -8   |
|    2 | -8.9 | -8.2 |  -8.1 | -6   |

`r5_a10_d1.0_T2 ... r15_a30_d1.0_T2` (slice 3,1)

|   a0 |    0 |    1 |    2 |    3 |
|-----:|-----:|-----:|-----:|-----:|
|    0 | -6.9 | -6   | -4.3 | -6.1 |
|    1 | -3.6 | -5.1 | -5.1 | -5.9 |
|    2 | -2   | -2.2 | -2.3 | -4.6 |

Old-vs-new (old = judge naked, as discovered: key on the NAKED delta, no dressing; new = dressed surrogate): naked top-3 PB_r5_a20_d0.5_T2 (naked rank 1..3 -> dressed rank 2), PB_r5_a10_d0.75_T2 (naked rank 1..3 -> dressed rank 8), PB_r5_a15_d0.5_T2 (naked rank 1..3 -> dressed rank 6); dressed top-3 PB_r5_a10_d0.5_T1 (naked rank 4), PB_r5_a20_d0.5_T2 (naked rank 1), PB_r5_a15_d0.5_T1 (naked rank 5). The live reference row is identical to S1b-COMB to the dollar by construction (delta 0), so the base-change proof is the identity of the reference row; a changed ranking between old and new is the effect of dressing, not a testing defect.

**Verdict PB: KEEP LIVE** - no plateau centre (best cell is a spike/edge).

Exact status: r8_hooks pb7{reg,arm,depth,trig}. Panel field(s): NONE (Pb7Rules constants: regime bar 10, arm 15, ATR5 depth 0.5, trigger T1): a new input would be needed.

## 8. OD (O7) - 20 cells

| cell | stack maxDD cut % L6M/L3M/L1M (equal lots) | same at EQUAL MEAN | key (eq-mean avg) | d mean $/wk L6M / HOLD (equal lots) | cut % HOLD / PRE / X' | d mean PRE | PRIOR (2a) | bi-weekly WF: cut % / beat % | p own | p family | nb beating live | live-wk delta $ | signal match to live |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| OD_arm0.5_w944 **(LIVE)** | 0.0 / 0.0 / 0.0 | 0.0 / 0.0 / 0.0 | 0.0 | 0 / 0 | 0.0 / 0.0 / 0.0 | 0 | OK-PRIOR | 0.0 / 14 | 1.000 | 1.000 | 2/4 spike/edge | 0 | 0.91 |
| OD_arm1.0_w944 | 0.9 / 0.9 / 0.8 | 1.6 / 1.6 / 1.5 | 1.5 | 165 / -7 | 0.0 / -0.9 / 0.5 | -211 | OK-PRIOR | 0.0 / 14 | 0.073 | 0.209 | 3/3 spike/edge | 611 | 0.92 |
| OD_arm1.0_w942 | 0.9 / 0.9 / 0.8 | 1.2 / 1.2 / 1.0 | 1.1 | 67 / -104 | 0.0 / -0.9 / 1.9 | -229 | OK-PRIOR | 0.0 / 14 | 0.060 | 0.296 | 1/2 spike/edge | 611 | 0.92 |
| OD_arm0.35_w949 | -0.8 / -0.8 / 1.2 | -0.3 / -0.3 / 1.7 | 0.4 | 117 / -39 | -0.6 / -0.4 / -0.2 | -31 | OK-PRIOR | 0.0 / 14 | 0.156 | 1.000 | 2/4 spike/edge | 1517 | 0.76 |
| OD_arm0.35_w959 | -0.8 / -0.8 / 1.2 | -0.3 / -0.3 / 1.7 | 0.4 | 117 / -39 | -0.6 / -0.4 / -0.2 | -31 | OK-PRIOR | 0.0 / 14 | 0.156 | 1.000 | 1/3 spike/edge | 1517 | 0.76 |
| OD_arm0.35_w944 | -0.8 / -0.8 / 2.0 | -0.6 / -0.6 / 2.1 | 0.3 | 41 / -80 | -0.6 / -0.4 / 0.3 | -12 | OK-PRIOR | 0.0 / 14 | 0.272 | 1.000 | 2/4 spike/edge | 0 | 0.78 |
| OD_arm0.75_w944 | 0.1 / 0.1 / 0.0 | 0.3 / 0.3 / 0.2 | 0.2 | 39 / -34 | 0.0 / 0.0 / -1.8 | 12 | OK-PRIOR | 0.0 / 14 | 0.312 | 1.000 | 1/4 spike/edge | 611 | 0.94 |
| OD_arm1.0_w949 | 0.1 / 0.1 / -0.0 | 0.2 / 0.2 / 0.1 | 0.1 | 17 / -6 | 0.0 / -0.9 / 0.5 | -219 | OK-PRIOR | 0.0 / 14 | 0.103 | 0.372 | 2/3 spike/edge | 2127 | 0.89 |

Best cell by key: **OD_arm1.0_w944** (key 1.5; SPIKE/EDGE: not a plateau centre); best plateau centre: **none** (key ). Family p of the best cell (max-stat over all 20 cells, shift null): 0.209. Procedure WF (bi-weekly re-pick over this neighbourhood, vs live): cut 0.0 %, beat 14 % of 74 refit periods (38 switches), d mean -8 $/wk.

Landscape (key = equal-mean stack cut %, L6M/L3M/L1M average; live = 0 by construction). Rows/cols = grid indices of the parameter order in the cell name; one matrix per (3rd, 4th) index:

`arm0.25_w942 ... arm1.0_w959` (slice 0,0)

|   a0 |    0 |    1 |    2 |    3 |
|-----:|-----:|-----:|-----:|-----:|
|    0 | -2.8 | -2.7 | -2.7 | -2.7 |
|    1 |  0.1 |  0.3 |  0.4 |  0.4 |
|    2 | -0.1 |  0   | -0.6 | -0.6 |
|    3 | -0.3 |  0.2 | -0.2 | -0.2 |
|    4 |  1.1 |  1.5 |  0.1 |  0.1 |

Old-vs-new (old = judge naked, as discovered: key on the NAKED delta, no dressing; new = dressed surrogate): naked top-3 OD_arm1.0_w944 (naked rank 1..3 -> dressed rank 1), OD_arm1.0_w942 (naked rank 1..3 -> dressed rank 2), OD_arm0.75_w944 (naked rank 1..3 -> dressed rank 6); dressed top-3 OD_arm1.0_w944 (naked rank 1), OD_arm1.0_w942 (naked rank 2), OD_arm0.35_w949 (naked rank 8). The live reference row is identical to S1b-COMB to the dollar by construction (delta 0), so the base-change proof is the identity of the reference row; a changed ranking between old and new is the effect of dressing, not a testing defect.

**Verdict OD: KEEP LIVE** - no plateau centre (best cell is a spike/edge).

Exact status: r8_hooks od{arm,win_end}. Panel field(s): NONE (arm 0.5 x median5 is a constant in OpenDriveEngine L1298; last-entry minute 09:44).

## 9. REFIT 2026-11-22 (what the bi-weekly procedure would pick today, trailing 26 weeks, drawdown first on the STACK; first-order, PRIOR label by rule 2a; the live setting is retained when nothing has a lower trailing maxDD)
| book | live cell | pick | | detail |
|---|---|---|---|---|
| KB | KB_e14_m1.0_b3 | KB_e10_m1.0_b1 | CHANGE | trailing 26 w ending 2026-11-05; top3 by trailing stack maxDD: KB_e10_m1.0_b1 (dd 65,082, OK-PRIOR); KB_e14_m2.5_b1 (dd 69,527, OK-PRIOR); KB_e17_m1.5_b1 (dd 70,577, OK-PRIOR) |
| SM | SM_a7_m3.0_b10 | SM_a21_m2.0_b10 | CHANGE | trailing 26 w ending 2026-11-05; top3 by trailing stack maxDD: SM_a21_m2.0_b10 (dd 61,813, RECENT-ONLY); SM_a10_m2.5_b5 (dd 61,928, RECENT-ONLY); SM_a7_m2.5_b5 (dd 63,377, OK-PRIOR) |
| HM | HM_f20_s55_b5_fixed | HM_f34_s55_b1_fixed | CHANGE | trailing 26 w ending 2026-11-05; top3 by trailing stack maxDD: HM_f34_s55_b1_fixed (dd 71,299, OK-PRIOR); HM_f27_s75_b1_fixed (dd 73,482, OK-PRIOR); HM_f20_s75_b1_fixed (dd 74,889, OK-PRIOR) |
| MV | MV_t0.5_v4_L5 | MV_t0.5_v3_long | CHANGE | trailing 26 w ending 2026-11-05; top3 by trailing stack maxDD: MV_t0.5_v3_long (dd 79,586, OK-PRIOR); MV_t0.5_v3_no15 (dd 79,830, OK-PRIOR); MV_t0.5_v4_L5 (dd 79,907, OK-PRIOR) |
| PE | PE_r5_a30_T2_e20 | PE_r10_a60_T2_e20 | CHANGE | trailing 26 w ending 2026-11-05; top3 by trailing stack maxDD: PE_r10_a60_T2_e20 (dd 51,601, RECENT-ONLY); PE_r10_a45_T2_e20 (dd 57,209, RECENT-ONLY); PE_r15_a45_T2_e30 (dd 66,869, RECENT-ONLY) |
| PB | PB_r10_a15_d0.5_T1 | PB_r5_a15_d0.5_T1 | CHANGE | trailing 26 w ending 2026-11-05; top3 by trailing stack maxDD: PB_r5_a15_d0.5_T1 (dd 78,073, OK-PRIOR); PB_r5_a10_d0.5_T1 (dd 78,073, OK-PRIOR); PB_r5_a20_d0.5_T1 (dd 78,073, OK-PRIOR) |
| OD | OD_arm0.5_w944 | OD_arm1.0_w944 | CHANGE | trailing 26 w ending 2026-11-05; top3 by trailing stack maxDD: OD_arm1.0_w944 (dd 79,212, OK-PRIOR); OD_arm1.0_w942 (dd 79,212, OK-PRIOR); OD_arm0.75_w944 (dd 79,821, OK-PRIOR) |

## SUMMARY BLOCK (T-STACK-REDO format)
| setting | live value | best on the state base | holds OOS? | change recommended | panel field |
|---|---|---|---|---|---|
| KB signal (ema 14 / atr 10 / mult 1.0 / 3-min) | ema 14 / atr 10 / mult 1.0 / 3-min | KB_e12_m1.25_b1 (key 8.3, L6M cut at equal mean 7.8 %, d mean -1085 $/wk) | no (WF/prior gate not met); RECENT-ONLY; WF 62 % | no | KbEmaPeriod / KbAtrPeriod / KbMult / KbBarMinutes (K7 signal bar) |
| SM signal (atr 7 / mult 3.0 / 10-min) | atr 7 / mult 3.0 / 10-min | SM_a21_m2.0_b5 (key 24.7, L6M cut at equal mean 24.7 %, d mean 2608 $/wk) | no (WF/prior gate not met); RECENT-ONLY; WF 51 % | no | SmAtrPeriod / SmMult / EmBarMinutes (U7 signal bar) |
| HM signal (fast 20 / slow 55 / EMA200 / 5-min / VWAP FixedMidnightUtc4) | fast 20 / slow 55 / EMA200 / 5-min / VWAP FixedMidnightUtc4 | HM_f27_s55_b1_fixed (key 14.8, L6M cut at equal mean 10.7 %, d mean 3322 $/wk) | no (WF/prior gate not met); OK-PRIOR; WF 46 % | no | H7FastPeriod / H7SlowPeriod / H7EmaPeriod / HmVwapAnchor (5-min bucket hard-coded by StackHm5Repl) |
| MV signal (thr 0.5 / votes 4 of 5 (15,30,60,120,240)) | thr 0.5 / votes 4 of 5 (15,30,60,120,240) | MV_t0.75_v3_L5 (spike, not a plateau) (key 2.6, L6M cut at equal mean -1.2 %, d mean -106 $/wk) | no (WF/prior gate not met); OK-PRIOR; WF 51 % | no | MvThreshold / MvVotes (lookback set 15,30,60,120,240 is a constant, MomentumVote L2396) |
| PE signal (regime 5-min / arm 30 / T2 / EMA20) | regime 5-min / arm 30 / T2 / EMA20 | PE_r15_a60_T2_e20 (key 15.3, L6M cut at equal mean -4.4 %, d mean -2071 $/wk) | no (WF/prior gate not met); RECENT-ONLY; WF 45 % | no | NONE (Pb3Rules constants in PbEngine L2225: regime bar 5, arm 30, trigger T2, EMA20 level): a new input would be needed |
| PB signal (regime 10-min / arm 15 / depth 0.5 ATR5 / T1) | regime 10-min / arm 15 / depth 0.5 ATR5 / T1 | PB_r5_a10_d0.5_T1 (spike, not a plateau) (key 8.4, L6M cut at equal mean 5.0 %, d mean 781 $/wk) | no (WF/prior gate not met); OK-PRIOR; WF 49 % | no | NONE (Pb7Rules constants: regime bar 10, arm 15, ATR5 depth 0.5, trigger T1): a new input would be needed |
| OD signal (arm 0.5 x median5 / last entry 09:44) | arm 0.5 x median5 / last entry 09:44 | OD_arm1.0_w944 (spike, not a plateau) (key 1.5, L6M cut at equal mean 1.6 %, d mean 165 $/wk) | no (WF/prior gate not met); OK-PRIOR; WF 14 % | no | NONE (arm 0.5 x median5 is a constant in OpenDriveEngine L1298; last-entry minute 09:44) |

## 10. Exact engine plan and hooks
Exact runs go through SZ-CORE's queue, prefix `R8_` (tier 2), plateau centre per book only. Hooks: `code/th_r8/r8_hooks.py` (composes fd_hooks; bar swap for KB 1/5 and SM 5/15, HM/MV/P7/A7/O7 parameters); identity with `par {}` is fd_hooks' FD_ID (identical to S1b-COMB). Not exact-capable without engine work: nothing in the list now except the HM VWAP 'sess' anchor (implemented, untested) and the PE confirm pattern/timeframe (R4's section). Exact status table: see section 11 when runs land.

## 11. Amendments to the prereg
(a) 21:40Z surrogate dressing (g[kind, MAE bin]) added after seeing that plain naked deltas ignore the state cut; (b) plateau rule made scale-aware (neighbours beating live in recents, neighbour mean key >= 80% of the centre) after the literal 20%-of-cut rule rejected every cell; both amendments were made after the first look at SM/KB/OD output. Plateau/verdict logic is otherwise as preregistered.
