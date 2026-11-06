# GLOBAL_MULTIPLICITY - box-wide multiplicity accounting (S4a, 2026-11-06; new file; research only, Shadow only, no PASS claim, no purchase, no new data)
Everything below is computed from saved artefacts (M.npy null vectors, cell tables, frames, ledger) and from pages cited as file:line. Code l2vast/ds3/code/t2s4a/global_mult.py, global_mult2.py, global_mult_write.py. **Scales:** the T-INSTR-2 and learned-rule (LRS) rows use the ALLINST scale, z of min(z_L6M, z_HOLD) of the cell against 200 random-side hash worlds of the SAME cell; the daily rows use the z of the 13-year net against the cell's own 1,000 random-side worlds; the tick-scale rows use the gross-structure z against a shuffled-day null. Scales differ, but each is standardised against its own null, which is what the extreme-value reading needs.

## 1. What was counted
* Registry /mnt/l2/l2vast/instr2/n_tested.jsonl: 65 lines, total **2,044,903** cells (lines 5, 2, 3 = ES / RTY / YM own grids at 502,740 each; 7 = GC 141,120; 4, 6, 8 = CL 66,024, 6E 65,835, 6J 82,152; 63 = GC discretionary 105,000; 47 = ES+RTY+NQ 1b-c 30,542; 21-35, 41-49 = LRS ~9,700; 50-52 = 1b-a 3 x 2,784; 36-40 map books 1,812; 57-59, 62 RV books 1,572; 61 = FIND_DAILY 408; 65 = DAILY-R6 612; withdrawn block-B lines 13-15 net out -12,888). It does NOT contain the S4b grids (BTCM / MBT / BTC / NKD, 144,648 cells each, T2BTC_NTESTED.md / DS3_INSTR2_NKD.md:4) nor ZN / ZB stage A (5,426 each) nor the earlier programs.
* Earlier programs: l2vast/ds3/out/uf/DEAD_CELLS.csv holds 2,088,352 ledger rows in 448 programs; excluding the T-INSTR-2 / T-FIND program names, 1,570,557 rows in 324 earlier programs (largest: RISKOFF_NTE2 483,488; NTZ1 131,026; BARSCAND2 96,131; RISKOFF_RO2 75,264; RC1_RA2 52,957; CFSUBMIN2 52,690).
* Box-wide cells (not de-duplicated, ledger and registry overlap in places): about 2.04M (registry) + 0.58M (S4b grids) + 1.57M (earlier programs) = **about 4.2 million**.

## 2. Program families on the same scale: best observed z against the program's own family null
T-INSTR-2 own grids (ALLINST scale; n = eligible cells; best z over ALL eligible cells; own p = share of 200 worlds whose per-world maximum is at least the best z; N_eff = effective number of independent tests implied by the null: the N for which the median / 95th-percentile maximum of N iid normals equals the null's own median / 95th percentile):
| instrument | eligible cells | tolerant | best z | best tolerant z | null max median / p95 | own p of best | N_eff (median method / p95 method) | source |
|--|--|--|--|--|--|--|--|--|
| ES | 456,498 | 8,149 | 4.26 | 3.47 | 3.57 / 4.01 | 0.020 | 3,818 / 1,721 | DS3_INSTR2_ES.md:5 |
| RTY | 457,338 | 8,490 | 3.62 | 3.40 | 3.60 / 4.08 | 0.478 | 4,331 / 2,314 | DS3_INSTR2_RTY.md:6 |
| YM | 457,674 | 11,605 | 3.92 | 3.36 | 3.57 / 4.07 | 0.124 | 3,873 / 2,145 | DS3_INSTR2_YM.md:6 |
| CL | 64,230 | 7,883 | 3.49 | 3.24 | 3.28 / 3.81 | 0.229 | 1,343 / 724 | DS3_INSTR2_ALLINST.md:38,95 |
| 6E | 63,888 | 2,676 | 3.04 | 2.63 | 3.20 / 3.68 | 0.741 | 1,007 / 445 | DS3_INSTR2_ALLINST.md:39,96 |
| 6J | 64,323 | 310 | 2.53 | 1.12 | 3.13 / 3.66 | 1.000 | 786 / 405 | DS3_INSTR2_ALLINST.md:40,97 |
| GC | 132,304 | 2,111 | 3.76 | 3.09 | 3.49 / 3.99 | 0.194 | 2,830 / 1,540 | DS3_INSTR2_ALLINST.md:98 |
| BTC | 142,121 | 1,723 | 3.92 | 3.15 | 3.48 / 3.94 | 0.060 | 2,736 / 1,272 | DS3_INSTR2_ALLINST.md:107 |
| MBT | 141,449 | 2,120 | 3.86 | 3.50 | 3.51 / 4.00 | 0.119 | 3,127 / 1,596 | DS3_INSTR2_ALLINST.md:108 |
| NKD | 140,961 | 102 | 3.71 | 2.39 | 3.41 / 4.03 | 0.229 | 2,147 / 1,836 | DS3_INSTR2_ALLINST.md:109 |
| ZN | 4,536 | 13 | 1.83 | 1.07 | 2.08 / 2.89 | 0.791 | 36 / 26 | DS3_INSTR2_ALLINST.md:110 |
| ZB | 3,696 | 0 | 1.59 | - | 2.08 / 2.86 | 0.876 | 37 / 24 | DS3_INSTR2_ALLINST.md:111 |
| **12-instrument joint** | 2,129,018 | 45,182 | 4.26 | 3.50 | 3.94 / 4.37 | **0.100** | 16,805 / 8,151 | DS3_INSTR2_ALLINST.md:104 (median 3.94, p95 4.37) |
So the 2.13 million cells of the 1-minute grids behave like about 8,000-17,000 independent tests (compression 125-260x), and the best cell of all 12 instruments (ES, z 4.26) is at the edge of what the joint null produces at random (p 0.10).
Learned-rule search (ZL-1 lrs_lib, same scale, 648 candidates per instrument, /mnt/l2/l2vast/find_lrs/<SYM>/cells.pkl and M.npy; MORNING.md:2607, DS3_FIND.md:6,53):
| instrument | candidates | best z | null max median / p95 | own p | N_eff (median) |
|--|--|--|--|--|--|
| 6E | 648 | 2.38 | 2.40 / 3.01 | 0.522 | 84 |
| 6J | 648 | 2.52 | 2.37 / 3.17 | 0.348 | 78 |
| BTC_CAPBREACH | 486 | 2.37 | 2.19 / 2.91 | 0.318 | 48 |
| CL | 648 | 2.51 | 2.41 / 3.10 | 0.383 | 88 |
| ES | 648 | 2.48 | 2.42 / 3.03 | 0.463 | 90 |
| GC | 648 | 2.59 | 2.33 / 3.01 | 0.264 | 69 |
| MBT | 648 | 1.97 | 2.29 / 2.87 | 0.836 | 63 |
| NKD_CAPBREACH | 484 | 2.14 | 2.18 / 2.98 | 0.542 | 47 |
| NQ | 648 | 2.48 | 2.47 / 3.20 | 0.502 | 101 |
| RTY | 648 | 2.90 | 2.42 / 3.09 | 0.114 | 90 |
| YM | 648 | 2.75 | 2.46 / 3.17 | 0.224 | 100 |
| ZB | 648 | 2.65 | 2.42 / 3.07 | 0.274 | 90 |
| ZN | 648 | 2.58 | 2.36 / 3.11 | 0.279 | 76 |
The best learned rule is RTY at z 2.90 (own p 0.114; the cross-instrument joint p is 0.72, MORNING.md:2607); BTC and NKD standard are degenerate (max lots 0). CHAR-B / CHAR-C restricted learned-rule searches (2,268 + 1,164 candidates, best family p .18-.38; DECISION_PACK_20261106.md:163) add no new maximum.
Tick-scale 1b-a (ES, RTY, NQ; 2,784 scored cells each; gross-structure z against shuffled days; DS3_FIND_CHARACTER.md:2783, 2817, 2851): null maximum median / p95 = 3.28 / 4.01 (ES), 3.19 / 3.96 (RTY), 3.25 / 3.89 (NQ); cells with family p <= .10: 370 / 265 / 29 of 2,784 (10% would be 278 per instrument), cells with net > 0: **0 / 0 / 0** (the structure is real in gross terms and smaller than the 1.4 / 3.0 / 4.0-tick taker cost).
Daily programs: FIND_DAILY 408 cells: best z 2.84 (200 worlds), null maximum 2.69 / 3.41; at 1,000 fresh worlds 2.73 / 3.46 and the best tolerant cell has family p .593 (DS3_REPLICATION.md:32; DS3_FIND_DAILY.md:27-36). DAILY-R6 578 cells: tolerant best z 2.66, null maximum 2.90 / 3.53, family p .78; joint 1,020-cell family null 3.03 / 3.68, p .92 (DS3_FIND_DAILY.md:514). The unconditional overnight legs reach z 5.0 (LE) and 4.3 (ZS) with family p < .001 (DS3_FIND_DAILY.md:548).
Programs with no z-scale null (their own family tests are cited): map books (CHAR-B 2,142 cells: best family p GC .59, CL .38, ZB .61, ZN 1.00; CHAR-C 1,812 cells: min .50; DECISION_PACK_20261106.md:163, MORNING.md:2610), relative-value spreads (1,554-1,572 cells: 0 clear, median cell loses $730-$1,508 a week in HOLD; DECISION_PACK_20261106.md:163), event windows (25 tests, Bonferroni 1.00; same line), block B (CL, YM, 6E, 6J run; 0 family-surviving: DS3_INSTR2_6E_B.md:6), native books (ZN/ZB, GC, BTC/MBT/NKD: no cell clears; DS3_INSTR2_NATIVE.md).

## 3. Effective N from cell-cluster correlation (three or more programs)
Participation ratio PR = (sum of eigenvalues)^2 / sum of squared eigenvalues of the correlation matrix of weekly P&L of the TOLERANT cells (an effective number of independent bets among those cells; k90 = eigenvalues needed for 90% of the variance; 2023-04..2026-10 weekly P&L for frames, 2013-2026 for the daily cells):
| set | cells | PR | k90 | mean pairwise corr |
|--|--|--|--|--|
| T-INSTR-2 GC tolerant frames | 77 | 18.2 | 25 | 0.07 |
| T-INSTR-2 YM tolerant frames | 29 | 8.0 | 9 | 0.12 |
| T-INSTR-2 RTY tolerant frames | 44 | 9.0 | 15 | 0.16 |
| T-INSTR-2 ES tolerant frames | 17 | 8.6 | 9 | 0.10 |
| T-INSTR-2 CL tolerant frames | 5 | 4.7 | 5 | 0.06 |
| FIND_DAILY tolerant cells | 30 | 12.3 | 15 | 0.08 |
| DAILY-R6 tolerant cells | 13 | 9.6 | 10 | 0.03 |
| R6 night legs ZS LE HE 6C | 4 | 3.7 | 4 | 0.01 |
| Monday excess ES NQ RTY YM | 4 | 1.3 | 2 | 0.83 |
Reading: the tolerant finalists of the 1-minute grids are not highly redundant with each other (PR 8-18 for 17-77 cells, mean correlation 0.07-0.16) because they come from different sessions and signal families; the real redundancy is in the FULL cell set, where the null-calibrated compression is 125-260x (section 2). The cluster that is strongly collinear is the equity Monday (4 indices = PR 1.3) and the rates complex (ZF ZT ZN ZB = 1.6-1.7, DS3_FIND_DAILY.md RATES-MOM block). Two estimators, therefore: the null-calibrated N_eff for the whole cell set (used for N below) and the correlation-based PR for the finalists (used for the number of independent bets per item).

## 4. Box-wide extreme-value reading
N = effective number of independent tests in the whole box, summed over the blocks (programs treated as independent, which overstates N where instruments are correlated and so is conservative against calling anything real):
| block | N_eff low | N_eff central | N_eff high |
|--|--|--|--|
| T-INSTR-2 joint (12 instruments) | 8,151 | 16,805 | 26,069 |
| LRS ZL-1 (13 instruments) | 624 | 1,023 | 1,023 |
| tick-scale 1b-a (ES, RTY, NQ) | 3,510 | 3,510 | 4,082 |
| daily FIND_DAILY + R6 (joint family 1,020 cells) | 440 | 567 | 567 |
| other T-FIND / T-INSTR-2 programs without a z-null (169,594 cells, compression 100-250x ASSUMED) | 678 | 969 | 1,696 |
| earlier programs (DEAD_CELLS ledger, 1,570,557 rows in 324 programs; compression 100-250x ASSUMED) | 6,282 | 8,975 | 15,706 |
| **TOTAL (sum, programs treated as independent: an upper bound on N)** | **19,685** | **31,848** | **49,141** |
Under the global null that NO cell anywhere has an edge, the maximum of N independent standard-normal z is at the median 3.97 / 4.09 / 4.19 (N = low / central / high) and its 95th percentile 4.56 / 4.66 / 4.74. The chance that chance alone gives at least the best z found:
| N scenario | N | median best z | 95th pct best z | P(max >= 4.26, the best T-INSTR-2 cell) | P(max >= 3.92, the best BTC cell) | P(max >= 5.0, LE night long, on the daily block's own N only below) |
|--|--|--|--|--|--|--|
| low | 19,685 | 3.97 | 4.56 | 18% | 58% | 1% |
| central | 31,848 | 4.09 | 4.66 | 28% | 76% | 1% |
| high | 49,141 | 4.19 | 4.74 | 39% | 89% | 1% |
(the last column uses the whole-box N for illustration; on the daily blocks' own N of about 1,000 the chance of a z of 5.0 is about 0.03%, of 4.3 about 0.9%.) **The best-found cell of all the 1-minute programs (z 4.26) is within what the box would produce at random with probability about 28% (range 18-39%).**

## 5. The best surviving items (ten smallest program-family p), with box-wide adjustment
K = 27 independent program-level families (T-INSTR-2 joint 1; LRS 1; tick-scale 1b-a 3; 1b-c 1; 1b-d 1; map books 3; events 1; RV 1; native books 3; block B 1; GC discretionary 1; FIND_DAILY 1; DAILY-R6 1; WF groups 2; rates 1; CL stress 1; Monday 1; 6E post-hoc 1; 1-s LRS 1; S4b crypto cluster 1; ES IB-edge 1; BTC/MBT fee audit 0 = about 27, range 15-50). Box Bonferroni = min(1, K x p); Holm = ordered (K - rank + 1) x p, made monotone. p floors are the resolution of the number of worlds (1/1,001 for 1,000 worlds, 1/201 for 200) and are used as is, which is conservative.
| rank | item | program family | statistic | family p (raw) | box Bonferroni / Holm (K = 27) | independent bets | nature | source |
|--|--|--|--|--|--|--|--|--|
| 1 | LE night long (overnight drift; DAILY-R6 unconditional leg, 13-year net -$68k at 1 tick/leg: cost-eaten) | daily R6 families A (578) / B (1,020) | z 5.0 vs random-sign null (gross drift) | 0.001 | 0.027 / 0.027 | 1 (night legs ZS/LE/HE/6C: PR 3.75 of 4) | GROSS STRUCTURE, net negative | DS3_FIND_DAILY.md:514,548 |
| 2 | ZS night long (same family, net -$20k; +$72k at half-tick) | same | z 4.3 | 0.001 | 0.027 / 0.027 | same cluster | GROSS STRUCTURE, net ~0 | DS3_FIND_DAILY.md:548 |
| 3 | GC trend count excess (493 of 4,200 tolerant; 0 of 2,000 fresh worlds reach it) | S4a canonical-bracket family null | count 493 vs null max 323 / 453 | 0.001 | 0.027 / 0.027 | 1 regime (PR 18 of 77 by weekly correlation, but one 2026 explanation; all 40 finalists negative 2013-2023) | REGIME, no single cell (max HOLD p .85/.62) | DS3_REPLICATION.md:86 |
| 4 | ZF / ZT momentum (annual-refit walk-forward OOS +$94k / +$86k) | daily R6 WF, 90 groups | OOS Calmar 0.5; p vs random parameter 0.004 (Bonferroni over 90 groups 0.36) | 0.004 | 0.108 / 0.096 | 1.6-1.7 (rates complex) | one-regime (2022), plateau rule failed | DS3_FIND_DAILY.md (RATES-MOM block), DS3_FIND_DAILY.md:514 |
| 5 | ES IB-edge passive continuation NY-PM 300 s | ZL-1 1b-d, WY over 149 ES cells (200 worlds) | per-order t 0.9-1.9; fails dollar gate (L3M/L6M) | 0.005 | 0.135 / 0.115 | 1 | REGIME/WATCH (p at the 200-world floor) | DS3_FIND.md:1088; MORNING.md:2705 |
| 6 | RTY prior-day-level continuation 08:30 pre-market 30/60 s (passive) | ZL-1 1b-d, joint over 3 instruments (200 worlds) | per-order t 0.9-1.9; fails X' in dollars | 0.005 | 0.135 / 0.115 | 1 (joint over ES/RTY/NQ also .005) | REGIME/WATCH (floor) | MORNING.md:2705 |
| 7 | BTC/MBT Asia Keltner-10m cluster | S4b fresh-world count test on the selected region (200 worlds); unconditional full-grid max-stat p .13 | fee-adjusted counts 62 / 540 (was 119 / 1,359); best t 2.0-2.1 | 0.005 | 0.135 / 0.115 | 1 (BTCM = MBT series; BTC standard CAP-BREACH twin) | WATCH, CAP-bound (MBT 1.4 lots) | DS3_INSTR2_BTC.md:143; FEE_AUDIT_INSTR2.md:27 |
| 8 | Best single cell of the T-INSTR-2 grids (ES, z 4.26, NOW-ONLY London regime cell) | T-INSTR-2 own ES null (own p .020), 12-instrument joint | z of min(L6M,HOLD) 4.26 | 0.100 | 1.000 / 1.000 | 1 | best-of-F; PRE and X' negative | DS3_INSTR2_ES.md:5; DS3_INSTR2_ALLINST.md:104 |
| 9 | Learned-rule search best (RTY, joint z 2.90) | ZL-1 LRS RTY 648 cells; cross-instrument joint .72 | z 2.90 vs null p95 3.09 | 0.114 | 1.000 / 1.000 | 1 | NULL | MORNING.md:2607; DS3_FIND.md:6 |
| 10 | Equity Monday long (ES NQ RTY YM) | CHAR-A joint equity family (20 cells), 20,000 draws | excess +8 to +19 bps; z 1.8-2.5 | 0.141 | 1.000 / 1.000 | 1.3 (4 indices, mean corr .83) | WATCH/REGIME, best-of-F | DS3_REPLICATION.md:13 |
Also surviving as WATCH but with a large family p (no statistical support at program level):
| item | family | evidence | independent bets | source |
|--|--|--|--|--|
| CL daily Donchian-20 SAR (watch cell) | FIND_DAILY 408 cells | family p 1.000 (random-side) / .998 (shift) at 1,000 worlds; annual-refit WF p .06; 89% of net from 3 trades | 1 | DS3_REPLICATION.md:32-70 (R4 table); DS3_FIND_FINAL.md:24 |
| NQ NY-AM prior-day-level passive | CHAR-A level-touch family (ES 149, RTY 147, NQ 152 cells) | ES h60 family p .43, NQ h30 .78 | 1 | MORNING.md:2705 |
| RTY pre-market PD-touch + burst continuation (CHAR-A book version) | 1b-DEEP | family p 1.00; placebo p_book .12-.87 | 1 | DS3_FIND_FINAL.md:22 |
| CMD4 cross-sectional momentum (GC CL ZN ZB) | DAILY4 87 cells | family p .88 | ~1.3 (4 commodities) | DS3_FIND_FINAL.md:27 |

## 6. Plain conclusion
**Is anything the box found distinguishable from the best result chance would produce? For anything that could be traded after costs: no. For three kinds of gross structure: yes, but none of them is an edge after costs or across time.**
The box tried about 4.2 million cells. Many of them are the same idea with different settings, so the number of genuinely different tests is far smaller: about 8,000-17,000 for the 1-minute strategy grids and about 19,685-49,141 for everything together. With that many independent tries, pure luck is expected to produce a best result around z 4.1 (95% of the time somewhere between 3.7 and 4.7). The best single result in the 1-minute grids, the ES cell at z 4.26, is exactly the size of best result luck produces about 28% of the time, and it is a cell that lost money in earlier years. The learned-rule search (best z 2.90, joint p 0.72), the daily books (best family p .59-.78), the map and relative-value books (best p .38-1.00) and every walk-forward row are inside the luck band; the highest-looking walk-forward rows (ZF / ZT momentum, p .004) carry a Bonferroni .36 and half of their profit is one year.
What does stand out statistically is three gross structures: (1) overnight drift in live cattle and soybeans (z 5.0 and 4.3, p below .001; roughly 1% chance anywhere in the box for the cattle number), but their cost per trade is as large as the gross edge, so the net result is negative at one tick per side and about break-even at half a tick, which we cannot measure without order-book data we do not own; (2) the excess number of tolerant gold-trend cells in 2026 (0 of 2,000 fresh random worlds reach it), which is one 2026 regime (negative in 2013-2023 for all 40 finalists); (3) tick-scale passive continuation at the ES initial-balance edge and the RTY pre-market prior-day level (p .005, at the floor of 200 worlds, per-order t below 2, 87% of modelled ES fills rely on unconfirmed cancels). After the box-wide correction (K = 27) these three still have adjusted p around .03-.12; none has a net-of-cost, out-of-sample or pre-2023 confirmation, and none can be reached with data we own except by waiting.
Everything else on the WATCH list (Monday long, CL Donchian, BTC/MBT Asia Keltner, NQ prior-day-level, RTY pre-market book version) has a program-level p of 0.06-1.00, which after the box-wide correction is indistinguishable from the best chance would produce; they are worth following forward only because they are cheap, not because the past data say they are real.

## 7. Limits of this accounting
N_eff by the null-calibrated method assumes the program's null maximum behaves like the maximum of N iid normals (its median fixes N; the 95th-percentile method gives about half as many, which is the 'low' column); blocks without a saved null are assigned a 100-250x compression taken from the T-INSTR-2 grids (ASSUMED); programs are summed as if independent; K is a count of families, not an exact quantity; p values at a world-count floor are upper bounds on the true small p; scales differ between families (stated in the header); the earlier-programs ledger counts rows, not independent tests, and their own results are not on a z scale (their headline results are in WHAT_IS_DEAD_20261105.md and the pages they cite).

## 8. Notes on the table in section 3 (appended)
The FIND_DAILY row has 30 cells because the 6 portfolio cells of the 36 tolerant are excluded, and the DAILY-R6 row 13 because the one tolerant portfolio cell (PORT16) is excluded; the Monday row uses the weekly Monday-excess series of ES, NQ, RTY, YM from /mnt/l2/l2vast/ds3/out/find/monday_weeks.pkl; the frame rows use the S0-tolerant frames of costcal_A.pkl (gate_v2a not required). The 'central' N_eff of the tick-scale block equals its median-method value and its 'low' is the smaller of the two methods; for the T-INSTR-2 joint block the 'high' value is the sum of the per-instrument values (no cross-instrument compression).
