# DS3_REDO_R7_BRACKETS - stop / target / ATR / time exit per book x entry session on the state base (REDO-R7)

Version 2026-11-09 21:28Z. **PRE-PROOF** (entry match < .85). **FIRST-ORDER SCREEN ONLY** for every row below; exact engine runs for the top-5 policies are queued (tier 2, sets R7_P1..R7_P5, L6M then PRE; hooks module code/th_r7/r7_hooks.py; hook regression R7_HOOKREF/R7_TEST pending). No PASS claims. Shadow only.

## 0. Plain verdict
No bracket cell survives the whole bar (family-max p <= .10 + bi-weekly WF >= 50 % beat + tolerant PRE + placebo). Every per-group lead has a family p of .33-.86 over the 1,440-cell grid and a per-cell bi-weekly WF that beats live in only 3-34 % of refit periods (the procedure that picks the lowest trailing-26-week maxDD cell across the whole grid beats live in 40-60 % of periods and its OOS cut is negative or ~0 in 14 of 15 groups). **Live brackets stay (K7/M7/U7/P7/H7/A7 60/60, O7 40/90)**; the leads below are candidates for the joint stage and exact runs, nothing more.

## 1. Method and fidelity
- Base S1B-COMB, 21,135 trades (X3-X5 have no trades in the base list; sessions with lots 0 (pre, close) have no trades: 15 book x session groups). Each trade is re-walked on the 1-s state arrays (th_exh build_universe conventions: stop from the SIGNAL price (A7/O7 from the fill), target from the fill average, target first on a touching second, state cut S1-COMB per (book, entry session) incl. V1/V2 lot-scaled arms, time exit, flat 16:55 / O7 16:00). Stop-exit slippage is calibrated per book to the engine stop exits ({"A7": -0.99, "H7": -1.74, "K7": 0.15, "M7": 0.25, "O7": -1.7, "P7": -0.04, "U7": -0.72}).
- Fidelity of the kernel at the live bracket vs the engine base: exit class (target/stop/cut) matches on 99.5 % of trades whose engine exit is not StackCut/BookLock/TimeBlock (20127 trades, all-trade class match 94.7 %); remaining engine exits (1008) are stack/lock/time exits the screen cannot reproduce, so changed trades REPLACE their reference-kernel P&L inside the engine daily series (stack = engine daily + candidate - reference kernel).
- Grid per group: stop 30..90 step 10 (7) x target R 0.5..2.25 step .25 (8; 2.25 = O7 live R) plus ATR variants k 1..4 x ATR14 on 1-min / 5-min bars x R (64), x time exit (none / 60 / 120 / 180 / 240 min / session end) x state-cut arm held in POINTS vs as a PERCENT of the stop (arm x stop/60) = 1,440 cells; each in two lot variants: FIXED lots and EQUAL-$-RISK lots (lots x ref stop / stop, rounded, min 1). 15 groups x 2,880 = 43,200 cells scored (r7_cells.parquet).
- Metrics on the STACK daily series: maxDD / worst-20 / Ulcer on all weeks, carrying week dropped from means only. Ranking key = mean of the equal-mean maxDD cut (global lot scale so the L6M mean equals live) over L6M, L3M, L1M; eligibility: L6M eq cut > 0, L3M > -3, worst-20 not worse. Placebo = permutation of the group's per-trade P&L changes among its trades (same distribution, random timing; B=50); family p = max over the whole 1,440-cell grid of the permuted key. Bi-weekly WF (Z.wf_biweekly, trailing 26 wk -> next 2 wk, 7-d purge, first refit 2024-01-01) is its own column. Prior label = Z.prior_info (rule 2a). First-order has no re-entries/locks/stack-cut interaction, so cell MEANS and drawdown are screens (SZ_BASE_PROOF: first-order is blind to exits).
- Held-out frozen live week: NOT computed in v1 (needs live-week state paths through the kernel; R7 v2).

## 2. Per book x session: top-5 candidates (live reference first)
Columns: eq cuts = equal-mean maxDD cut % of the STACK; dM = delta mean $/wk (L6M / PRE) vs live; WF = bi-weekly re-pick beat % / OOS cut %; p = own / family permutation p.

### A7 asia (n=1160 trades; WF of the whole-grid pick procedure: beat 59 %, OOS cut -4.1 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| stop40|R1.75|tx_180m|arm_pct | fixed | 6.2 / 6.2 / 6.5 | 102.6 | -2.6 / -383.5 | 27.0 / -2.6 | 0.04 / 0.78 | OK-PRIOR | LEAD+ |
| stop40|R1.75|tx_sess|arm_pct | eqrisk | 9.0 / 9.0 / 8.9 | -124.7 | -2.4 / 171.1 | 24.3 / -2.4 | - / - | OK-PRIOR | LEAD |
| atr1_k2|R1.50|tx_180m|arm_pts | eqrisk | 7.8 / 7.8 / 7.7 | 147.7 | -2.3 / -251.4 | 6.8 / -2.3 | - / - | OK-PRIOR | LEAD |

Median key over the grid: arm in POINTS -2.8, arm as PERCENT of stop -4.0.

### H7 asia (n=701 trades; WF of the whole-grid pick procedure: beat 54 %, OOS cut 1.0 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| stop50|R2.25|tx_none|arm_pts | fixed | 6.1 / 6.1 / 14.7 | 720.4 | 3.7 / 39.0 | 44.6 / 0.0 | 0.16 / 0.61 | OK-PRIOR | LEAD |
| atr5_k4|R2.25|tx_180m|arm_pts | fixed | 8.9 / 8.9 / 8.8 | 219.0 | 3.9 / -1030.2 | 25.7 / 0.0 | 0.06 / 0.61 | RECENT-ONLY | LEAD+ RECENT-ONLY |
| stop50|R2.25|tx_none|arm_pct | fixed | 5.0 / 5.0 / 14.0 | 255.7 | 3.8 / -14.1 | 41.9 / 0.0 | 0.12 / 0.65 | OK-PRIOR | LEAD |
| stop50|R2.25|tx_none|arm_pts | eqrisk | 9.5 / 9.5 / 18.0 | 902.2 | 3.7 / 278.4 | 23.0 / 0.0 | - / - | OK-PRIOR | LEAD |
| stop50|R2.25|tx_none|arm_pct | eqrisk | 8.2 / 8.2 / 17.2 | 352.2 | 3.8 / 229.7 | 23.0 / 0.0 | - / - | OK-PRIOR | LEAD |

Median key over the grid: arm in POINTS -4.3, arm as PERCENT of stop -6.8.

### H7 nyam (n=415 trades; WF of the whole-grid pick procedure: beat 45 %, OOS cut 0.0 %)
(no cell passes the eligibility screen: L6M eq cut > 0, L3M > -3, key > 0, worst-20 not worse)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |

Median key over the grid: arm in POINTS 2.3, arm as PERCENT of stop 2.0.

### K7 asia (n=2383 trades; WF of the whole-grid pick procedure: beat 59 %, OOS cut -4.4 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| atr1_k3|R2.00|tx_none|arm_pct | eqrisk | 12.6 / 12.6 / 15.8 | -251.5 | -0.7 / -1017.4 | 13.5 / 0.0 | - / - | RECENT-ONLY | LEAD RECENT-ONLY |
| atr1_k4|R1.75|tx_sess|arm_pct | eqrisk | 11.2 / 11.2 / 17.4 | 888.2 | -0.7 / -672.9 | 5.4 / 0.0 | - / - | OK-PRIOR | LEAD |

Median key over the grid: arm in POINTS -10.8, arm as PERCENT of stop -15.8.

### K7 london (n=1760 trades; WF of the whole-grid pick procedure: beat 54 %, OOS cut 0.1 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| stop80|R1.25|tx_120m|arm_pct | fixed | 10.3 / 10.3 / 11.0 | -377.2 | -2.4 / 67.6 | 24.3 / 0.0 | 0.04 / 0.67 | OK-PRIOR | LEAD+ |
| stop80|R0.50|tx_120m|arm_pct | fixed | 6.6 / 6.6 / 6.5 | 196.8 | -3.1 / -123.0 | 36.5 / -3.1 | 0.02 / 0.86 | OK-PRIOR | LEAD+ |
| atr5_k4|R0.75|tx_120m|arm_pct | fixed | 6.0 / 6.0 / 6.4 | -127.9 | 5.2 / 81.4 | 45.9 / 5.2 | 0.14 / 0.90 | OK-PRIOR | LEAD |
| stop80|R1.25|tx_120m|arm_pct | eqrisk | 10.3 / 10.3 / 11.0 | -377.2 | -2.4 / 67.6 | 24.3 / 0.0 | - / - | OK-PRIOR | LEAD |
| stop90|R0.75|tx_120m|arm_pct | eqrisk | 7.1 / 7.1 / 7.1 | -254.4 | 1.0 / -387.5 | 33.8 / 1.0 | - / - | OK-PRIOR | LEAD |

Median key over the grid: arm in POINTS -4.2, arm as PERCENT of stop -5.7.

### K7 nyam (n=1686 trades; WF of the whole-grid pick procedure: beat 47 %, OOS cut -0.8 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| atr5_k4|R0.50|tx_none|arm_pct | fixed | 5.1 / 5.1 / 5.9 | 501.7 | -3.6 / -327.4 | 10.8 / 0.0 | 0.04 / 0.76 | OK-PRIOR | LEAD+ |
| atr5_k4|R2.25|tx_240m|arm_pts | fixed | 1.1 / 1.1 / 11.5 | 1177.1 | 10.3 / 575.6 | 10.8 / 0.0 | 0.14 / 0.84 | OK-PRIOR | LEAD |
| atr5_k1|R1.50|tx_240m|arm_pts | fixed | 3.5 / 3.5 / 5.8 | 655.1 | 0.5 / -238.0 | 36.5 / 0.0 | 0.04 / 0.84 | OK-PRIOR | LEAD+ |
| atr5_k4|R0.50|tx_none|arm_pct | eqrisk | 5.1 / 5.1 / 5.9 | 501.7 | -3.6 / -330.4 | 10.8 / 0.0 | - / - | OK-PRIOR | LEAD |
| atr5_k4|R2.25|tx_240m|arm_pts | eqrisk | 1.1 / 1.1 / 11.5 | 1177.1 | 10.3 / 572.8 | 10.8 / 0.0 | - / - | OK-PRIOR | LEAD |

Median key over the grid: arm in POINTS -0.7, arm as PERCENT of stop -3.1.

### K7 nypm (n=1356 trades; WF of the whole-grid pick procedure: beat 53 %, OOS cut -1.4 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| stop30|R1.25|tx_sess|arm_pts | eqrisk | 16.1 / 16.1 / 16.0 | 107.2 | -0.3 / 2.6 | 5.4 / -0.3 | - / - | OK-PRIOR | LEAD |
| stop30|R1.50|tx_60m|arm_pct | eqrisk | 11.7 / 11.7 / 16.8 | 209.5 | 1.8 / -121.4 | 21.6 / 0.0 | - / - | OK-PRIOR | LEAD |

Median key over the grid: arm in POINTS 2.6, arm as PERCENT of stop 2.7.

### M7 london (n=2722 trades; WF of the whole-grid pick procedure: beat 59 %, OOS cut -2.1 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| atr1_k4|R1.25|tx_180m|arm_pct | fixed | 6.4 / 6.4 / 14.1 | 2.7 | -39.4 / -913.9 | 45.9 / 0.0 | 0.06 / 0.75 | RECENT-ONLY | LEAD+ RECENT-ONLY |
| atr1_k4|R1.25|tx_none|arm_pct | fixed | 6.3 / 6.3 / 14.0 | -18.4 | -39.4 / -906.9 | 45.9 / 0.0 | 0.06 / 0.75 | RECENT-ONLY | LEAD+ RECENT-ONLY |
| atr1_k4|R1.25|tx_240m|arm_pct | fixed | 6.3 / 6.3 / 14.0 | -18.4 | -39.4 / -930.7 | 45.9 / 0.0 | 0.06 / 0.75 | RECENT-ONLY | LEAD+ RECENT-ONLY |

Median key over the grid: arm in POINTS -1.2, arm as PERCENT of stop -5.0.

### M7 nyam (n=1803 trades; WF of the whole-grid pick procedure: beat 47 %, OOS cut -2.2 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| stop40|R2.00|tx_240m|arm_pts | eqrisk | 6.4 / 6.4 / 14.4 | 1375.1 | 1.1 / 740.8 | 9.5 / 0.0 | - / - | OK-PRIOR | LEAD |
| atr1_k1|R2.25|tx_sess|arm_pts | eqrisk | 6.2 / 6.2 / 14.6 | 782.9 | -1.0 / -643.4 | 18.9 / 0.0 | - / - | OK-PRIOR | LEAD |

Median key over the grid: arm in POINTS 0.3, arm as PERCENT of stop -1.2.

### O7 nyam (n=506 trades; WF of the whole-grid pick procedure: beat 58 %, OOS cut -3.3 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop40/R2.25 (live 40/90)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| stop30|R1.25|tx_none|arm_pts | fixed | 2.3 / 2.3 / 2.6 | 40.9 | 0.0 / -446.4 | 18.9 / 0.0 | 0.04 / 0.65 | OK-PRIOR | LEAD+ |
| stop30|R1.25|tx_120m|arm_pts | fixed | 2.3 / 2.3 / 2.6 | 40.9 | 0.0 / -437.7 | 18.9 / 0.0 | 0.04 / 0.65 | OK-PRIOR | LEAD+ |
| stop30|R1.25|tx_180m|arm_pts | fixed | 2.3 / 2.3 / 2.6 | 40.9 | 0.0 / -439.4 | 18.9 / 0.0 | 0.04 / 0.65 | OK-PRIOR | LEAD+ |
| stop30|R1.25|tx_sess|arm_pts | eqrisk | 2.3 / 2.3 / 2.6 | 40.9 | 0.0 / -438.2 | 18.9 / 0.0 | - / - | OK-PRIOR | LEAD |
| stop30|R1.25|tx_240m|arm_pts | eqrisk | 2.3 / 2.3 / 2.6 | 40.9 | 0.0 / -431.3 | 18.9 / 0.0 | - / - | OK-PRIOR | LEAD |

Median key over the grid: arm in POINTS -0.7, arm as PERCENT of stop -1.4.

### P7 asia (n=2288 trades; WF of the whole-grid pick procedure: beat 47 %, OOS cut -56.8 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| stop40|R1.25|tx_180m|arm_pts | fixed | 9.3 / 9.3 / 18.5 | -1233.4 | 6.8 / -2550.0 | 35.1 / 6.8 | 0.08 / 0.90 | RECENT-ONLY | LEAD+ RECENT-ONLY |
| atr5_k3|R1.25|tx_180m|arm_pts | eqrisk | 19.1 / 30.4 / 30.3 | -1433.2 | -14.1 / -3146.4 | 12.2 / -2.9 | - / - | RECENT-ONLY | LEAD RECENT-ONLY |
| atr5_k3|R1.25|tx_none|arm_pts | eqrisk | 14.0 / 28.5 / 32.7 | 247.7 | -0.1 / -1933.9 | 2.7 / 0.0 | - / - | RECENT-ONLY | LEAD RECENT-ONLY |

Median key over the grid: arm in POINTS -88.6, arm as PERCENT of stop -125.9.

### P7 london (n=1679 trades; WF of the whole-grid pick procedure: beat 53 %, OOS cut 26.1 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| atr1_k2|R2.25|tx_180m|arm_pts | fixed | 41.2 / 41.2 / 41.1 | 130.9 | -25.5 / -253.4 | 24.3 / -25.5 | 0.02 / 0.35 | RECENT-ONLY | LEAD+ RECENT-ONLY |
| atr1_k2|R2.00|tx_240m|arm_pts | fixed | 41.1 / 41.1 / 41.0 | -105.3 | -28.4 / -164.0 | 14.9 / -28.4 | 0.02 / 0.37 | RECENT-ONLY | LEAD+ RECENT-ONLY |
| atr1_k2|R2.00|tx_none|arm_pts | fixed | 41.1 / 41.1 / 41.0 | -105.3 | -28.4 / -164.0 | 14.9 / -28.4 | 0.02 / 0.37 | RECENT-ONLY | LEAD+ RECENT-ONLY |
| atr1_k2|R1.50|tx_60m|arm_pct | eqrisk | 40.3 / 40.3 / 41.3 | 2246.5 | -24.4 / -2659.2 | 6.8 / -3.0 | - / - | RECENT-ONLY | LEAD RECENT-ONLY |

Median key over the grid: arm in POINTS 3.3, arm as PERCENT of stop 2.3.

### P7 nyam (n=1303 trades; WF of the whole-grid pick procedure: beat 54 %, OOS cut -7.1 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| atr5_k3|R0.50|tx_180m|arm_pct | fixed | 17.0 / 17.0 / 21.8 | 2425.2 | -15.1 / -1029.4 | 12.2 / 0.0 | 0.10 / 0.84 | RECENT-ONLY | LEAD+ RECENT-ONLY |
| atr5_k3|R0.50|tx_240m|arm_pct | fixed | 16.4 / 16.4 / 16.3 | 2084.4 | -15.1 / -1418.9 | 9.5 / 0.0 | 0.08 / 0.86 | RECENT-ONLY | LEAD+ RECENT-ONLY |
| atr5_k4|R0.50|tx_120m|arm_pct | fixed | 5.0 / 5.0 / 33.2 | 3824.7 | -5.1 / 522.4 | 9.5 / 0.0 | 0.16 / 0.92 | OK-PRIOR | LEAD |
| atr5_k4|R0.50|tx_240m|arm_pct | eqrisk | 13.0 / 13.0 / 27.6 | 1325.8 | 6.5 / -1651.7 | 33.8 / 0.0 | - / - | RECENT-ONLY | LEAD RECENT-ONLY |
| atr5_k4|R0.50|tx_none|arm_pct | eqrisk | 7.8 / 7.8 / 27.0 | 1108.2 | 6.5 / -1538.7 | 32.4 / 0.0 | - / - | RECENT-ONLY | LEAD RECENT-ONLY |

Median key over the grid: arm in POINTS -2.4, arm as PERCENT of stop -2.3.

### U7 asia (n=687 trades; WF of the whole-grid pick procedure: beat 47 %, OOS cut -6.1 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| stop40|R1.50|tx_sess|arm_pts | fixed | 6.2 / 6.2 / 6.1 | 514.2 | -2.8 / -678.9 | 17.6 / 0.0 | 0.04 / 0.80 | OK-PRIOR | LEAD+ |
| stop40|R1.50|tx_240m|arm_pts | fixed | 6.2 / 6.2 / 6.1 | 595.7 | -2.8 / -286.7 | 25.7 / 0.0 | 0.08 / 0.80 | OK-PRIOR | LEAD+ |
| stop40|R1.50|tx_180m|arm_pts | fixed | 6.1 / 6.1 / 6.0 | 577.8 | -2.8 / -437.9 | 25.7 / 0.0 | 0.06 / 0.80 | OK-PRIOR | LEAD+ |
| stop40|R2.00|tx_sess|arm_pts | eqrisk | 7.6 / 7.6 / 7.5 | 2591.8 | -7.8 / -634.9 | 16.2 / -7.8 | - / - | OK-PRIOR | LEAD |
| stop40|R0.50|tx_60m|arm_pts | eqrisk | 2.8 / 7.7 / 7.6 | 151.7 | -6.0 / -1571.3 | 10.8 / 0.0 | - / - | RECENT-ONLY | LEAD RECENT-ONLY |

Median key over the grid: arm in POINTS -12.5, arm as PERCENT of stop -13.6.

### U7 london (n=686 trades; WF of the whole-grid pick procedure: beat 41 %, OOS cut -0.9 %)
| cell | lots | eqcut L6M/L3M/L1M | dM L6M | PRE cut / dM | WF beat / cut | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|
| **LIVE stop60/R1.00 (live 60/60)** | fixed | 0 / 0 / 0 | 0 | 0 / 0 | - | - | - | reference |
| atr1_k1|R1.00|tx_none|arm_pct | fixed | 13.7 / 13.7 / 28.0 | 402.5 | 18.8 / -467.3 | 18.9 / 18.8 | 0.02 / 0.33 | OK-PRIOR | LEAD+ |
| atr1_k1|R1.00|tx_60m|arm_pct | fixed | 13.7 / 13.7 / 28.0 | 402.5 | 18.8 / -479.7 | 18.9 / 18.8 | 0.02 / 0.33 | OK-PRIOR | LEAD+ |
| atr1_k1|R1.00|tx_180m|arm_pct | fixed | 13.7 / 13.7 / 28.0 | 402.5 | 18.8 / -467.3 | 18.9 / 18.8 | 0.02 / 0.33 | OK-PRIOR | LEAD+ |

Median key over the grid: arm in POINTS 3.7, arm as PERCENT of stop 4.5.

## 3. Percent arm or point arm?
Grid-median key is higher with the arm held in POINTS in 12 of 15 groups; best-cell comparison: BEST_ARM_PTS 17.5 eq cut L6M vs BEST_ARM_PCT -2.4 (joint policies, section 4). **Recommendation: hold the POINT arm fixed** (the live state-cut arm is in points: unchanged when the stop moves); a percent arm shrinks the cut with tighter stops and widens it with wider ones and does not help in the screen. Exact: R7_P2 (points) vs R7_P3 (percent) are queued to confirm.

## 4. Joint bracket policies (one cell per group, composed on the stack)
All windows are first-order stack numbers vs the live stack; every policy FAILS the recents/WF bar in the screen (see label).

| policy | groups | cut L6M | eq L6M | eq L3M | eq L1M | dM L6M | PRE cut | PRE dM | X' cut | WF beat % | WF cut % | prior label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BEST_KEY | 11 | -0.5 | -39.0 | 63.0 | 87.9 | -7318.4 | -62.1 | -7626.7 | -2.2 | 18.9 | -18.0 | RECENT-ONLY |
| BEST_ARM_PTS | 10 | 28.8 | 17.5 | 67.2 | 92.9 | -3626.5 | 16.8 | -10089.0 | 28.0 | 16.2 | -1.7 | RECENT-ONLY |
| BEST_ARM_PCT | 8 | -5.1 | -2.4 | 59.4 | 80.5 | 612.3 | -66.6 | -3139.3 | 19.2 | 23.0 | -32.9 | RECENT-ONLY |
| BEST_EQRISK | 12 | -125.3 | -157.3 | 13.7 | 59.9 | -3292.6 | -75.4 | -9788.7 | -98.9 | 0.0 | 0.0 | RECENT-ONLY |
| BEST_OKPRIOR | 10 | -1.6 | -27.9 | 68.6 | 68.6 | -5438.0 | -5.8 | -3576.4 | 0.3 | 10.8 | -46.6 | RECENT-ONLY |

BEST_KEY mixes arm modes per group (hook pctfix is a policy-wide switch; set R7_P1 uses the majority). Equal-$-risk policy: the lot rule is `eqrisk` (lots x 60/stop; O7 40/stop) applied after the live chain.

### Policy lines for the best fixed-lot joint policy (BEST_ARM_PTS) - SHADOW, not recommended live
```
bracket H7 asia stop=50 target=2.25R lotmult=1.0  # fixed lots eqcut L6M 6.1 label LEAD
bracket K7 london stop=80 target=1.25R time=120m lotmult=1.0  # fixed lots eqcut L6M 5.8 label LEAD+
bracket K7 nyam stop=4xATR5 target=2.25R time=240m lotmult=1.0  # fixed lots eqcut L6M 1.1 label LEAD
bracket M7 london stop=1xATR5 target=1.5R time=60m lotmult=1.0  # fixed lots eqcut L6M 6.1 label LEAD+
bracket O7 nyam stop=30 target=1.25R lotmult=1.0  # fixed lots eqcut L6M 2.3 label LEAD+
bracket P7 asia stop=40 target=1.25R time=180m lotmult=1.0  # fixed lots eqcut L6M 9.3 label LEAD+ RECENT-ONLY
bracket P7 london stop=2xATR1 target=2.25R time=180m lotmult=1.0  # fixed lots eqcut L6M 41.2 label LEAD+ RECENT-ONLY
bracket P7 nyam stop=70 target=2.25R time=sess lotmult=1.0  # fixed lots eqcut L6M 12.9 label LEAD+ RECENT-ONLY
bracket U7 asia stop=40 target=1.5R time=sess lotmult=1.0  # fixed lots eqcut L6M 6.2 label LEAD+
bracket U7 london stop=1xATR1 target=1R time=180m lotmult=1.0  # fixed lots eqcut L6M 13.6 label LEAD+
```

## 5. Old vs new (previously published bracket cells, first-order, same kernel)
| cell | cut_L6M | dmean_L6M | cut_L3M | cut_PRE | dmean_PRE | dmean_HOLD |
|---|---|---|---|---|---|---|
| K7 asia 75/60 (D6 per-session override, measured -1.0 in ba2) | -1.3 | 104.2 | -1.3 | 5.0 | 343.0 | 195.4 |
| H7 nyam 90/75 (D6 override, measured +5.45, inside MDE) | 2.6 | 270.3 | 2.6 | 0.4 | 171.9 | 35.2 |

The old published values were on the old engine (per-print cut, library thinning); no identical-to-the-dollar test is possible because the base changed.  Both D6 overrides are positive on L6M mean in the screen (inside MDE) and ~0 on the stack maxDD: consistent with keep (inside noise).

## 6. REFIT 2026-11-22 (what the bi-weekly procedure would pick today)
Trailing 26 weeks to the data end, drawdown first on the STACK (maxDD, worst-20, Ulcer, then mean) over the full 1,440-cell grid per group (fixed lots), live retained unless a cell has a lower trailing maxDD; prior label attached from the screen.

| group | pick | trailing maxDD live -> pick | trailing mean live -> pick | prior (PRE cut / dM) |
|---|---|---|---|---|
| A7 asia | stop40|R1.75|tx_180m|arm_pct | 79907.3 -> 75245.3 | 24124.4 -> 23834.1 | OK-PRIOR (-2.6 / -383.5) |
| H7 asia | stop70|R2.00|tx_180m|arm_pct | 79907.3 -> 72093.6 | 24124.4 -> 25478.6 | RECENT-ONLY (4.2 / -1123.4) |
| H7 nyam | stop90|R1.25|tx_240m|arm_pts | 79907.3 -> 74093.8 | 24124.4 -> 24971.1 | OK-PRIOR (-2.6 / 110.8) |
| K7 asia | stop50|R0.75|tx_sess|arm_pts | 79907.3 -> 74985.3 | 24124.4 -> 23830.5 | OK-PRIOR (0.1 / -712.6) |
| K7 london | stop80|R1.25|tx_120m|arm_pct | 79907.3 -> 70495.8 | 24124.4 -> 23171.4 | OK-PRIOR (-2.4 / 67.6) |
| K7 nyam | atr5_k4|R0.50|tx_none|arm_pct | 79907.3 -> 77447.2 | 24124.4 -> 24232.8 | OK-PRIOR (-3.6 / -327.4) |
| K7 nypm | stop40|R1.00|tx_180m|arm_pct | 79907.3 -> 71812.0 | 24124.4 -> 23558.2 | OK-PRIOR (1.4 / -165.3) |
| M7 london | atr1_k1|R0.50|tx_none|arm_pts | 79907.3 -> 67468.2 | 24124.4 -> 24576.5 | OK-PRIOR (10.9 / -7.3) |
| M7 nyam | atr1_k2|R1.50|tx_60m|arm_pts | 79907.3 -> 76279.1 | 24124.4 -> 24091.0 | OK-PRIOR (-3.1 / -568.6) |
| O7 nyam | stop30|R1.25|tx_none|arm_pts | 79907.3 -> 78207.8 | 24124.4 -> 24051.9 | OK-PRIOR (0.0 / -446.4) |
| P7 asia | stop40|R1.50|tx_180m|arm_pts | 79907.3 -> 68325.8 | 24124.4 -> 22706.2 | RECENT-ONLY (4.6 / -2846.8) |
| P7 london | atr1_k2|R2.00|tx_none|arm_pts | 79907.3 -> 46870.3 | 24124.4 -> 22895.0 | RECENT-ONLY (-28.4 / -164.0) |
| P7 nyam | atr1_k1|R0.75|tx_none|arm_pct | 79907.3 -> 60549.3 | 24124.4 -> 25678.4 | RECENT-ONLY (-5.7 / -2291.0) |
| U7 asia | atr5_k4|R0.50|tx_60m|arm_pts | 79907.3 -> 73810.9 | 24124.4 -> 23681.7 | OK-PRIOR (7.3 / -518.3) |
| U7 london | stop30|R2.25|tx_60m|arm_pts | 79907.3 -> 67992.9 | 24124.4 -> 23277.7 | OK-PRIOR (9.0 / -719.8) |

These are what a pure trailing-DD refit would pick; the walk-forward says this procedure does not beat live out of sample (section 2 headers), so the recommendation for 2026-11-22 is: keep the live brackets unless the exact runs of R7_P2 confirm.

## 7. Exact-engine status
Sets R7_P1 (BEST_KEY) R7_P2 (BEST_ARM_PTS) R7_P3 (BEST_ARM_PCT) R7_P4 (BEST_EQRISK) R7_P5 (BEST_OKPRIOR) queued in /mnt/l2/l2vast/_th_sz/exact_queue_8_r7.txt (L6M 202605-202610, PRE 202402-202506); the live reference is the S1b-COMB base itself (hook regression R7_HOOKREF must equal it). Results are appended here in the next refresh; until then every row is [FIRST-ORDER SCREEN ONLY].

## 8. Summary block (setting | live value | best on the state base | holds OOS? | change recommended | panel field)

| setting | live value | best on the state base (screen) | holds OOS? | change recommended | panel field |
|---|---|---|---|---|---|
| bracket A7 asia | 60/60 | stop40|R1.75|tx_180m|arm_pct | no (WF beat 27.0 %) | no | policy line `bracket A7 asia ...` |
| bracket H7 asia | 60/60 | stop50|R2.25|tx_none|arm_pts | no (WF beat 44.6 %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket H7 nyam | 60/60 | none eligible | no (WF beat - %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket K7 asia | 60/60 | none eligible | no (WF beat - %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket K7 london | 60/60 | stop80|R1.25|tx_120m|arm_pct | no (WF beat 24.3 %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket K7 nyam | 60/60 | atr5_k4|R0.50|tx_none|arm_pct | no (WF beat 10.8 %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket K7 nypm | 60/60 | none eligible | no (WF beat - %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket M7 london | 60/60 | atr1_k4|R1.25|tx_180m|arm_pct | no (WF beat 45.9 %) | no | policy line `bracket M7 london ...` |
| bracket M7 nyam | 60/60 | none eligible | no (WF beat - %) | no | policy line `bracket M7 nyam ...` |
| bracket O7 nyam | 40/90 | stop30|R1.25|tx_none|arm_pts | no (WF beat 18.9 %) | no | O7BracketSessions |
| bracket P7 asia | 60/60 | stop40|R1.25|tx_180m|arm_pts | no (WF beat 35.1 %) | no | policy line `bracket P7 asia ...` |
| bracket P7 london | 60/60 | atr1_k2|R2.25|tx_180m|arm_pts | no (WF beat 24.3 %) | no | policy line `bracket P7 london ...` |
| bracket P7 nyam | 60/60 | atr5_k3|R0.50|tx_180m|arm_pct | no (WF beat 12.2 %) | no | policy line `bracket P7 nyam ...` |
| bracket U7 asia | 60/60 | stop40|R1.50|tx_sess|arm_pts | no (WF beat 17.6 %) | no | policy line `bracket U7 asia ...` |
| bracket U7 london | 60/60 | atr1_k1|R1.00|tx_none|arm_pct | no (WF beat 18.9 %) | no | policy line `bracket U7 london ...` |
| state-cut arm vs stop | points held fixed | points | yes (screen) | no | state-cut arm lines (points) |
