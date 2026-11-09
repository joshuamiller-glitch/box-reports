# SZ_AB - T-SIZER-EXHAUST families A (ER) and B (volatility-target) + K (P7) slice  (refreshed 2026-11-09 18:28Z)
**ROLL-EXCL: the 33 engine roll-artifact base trades (31 of 21,135 on S1b-COMB; key book + signal second, list /mnt/l2/l2vast/_th_exh/hi/roll_bracket_trades.csv) are excluded from every number on this page (their P&L set to 0 in cell and reference); flag per trade in /mnt/l2/l2vast/_th_sz/ab/roll_excl_S1B-COMB.npy (M_AB.npz keeps the row order and the multipliers of these trades). FIRST-ORDER SCREEN ONLY unless a row says EXACT (exact-engine rows are in the exact section, top-5 + mild twin only). Label: base S1b-COMB (live D7 v1.5 state cut), FIRST-ORDER trade-level scoring (pnl per planned lot x new lots; first-order mean is not reliable, drawdown ranking is usable), in-sample, PRE-PROOF, post-hoc, Shadow only, no PASS claims. Windows as of 2026-11-09; carrying week (largest |cell - Q1-A| weekly delta) dropped from means; maxDD/worst-20/Ulcer on all weeks.**
Prereg: autopilot/SZ_AB_PREREG.md (sha in DECISIONS.md). Ledger /mnt/l2/l2vast/_th_sz/ledger_AB.parquet (copy at _th_sz/ab/ledger_AB.parquet; 63914 cells, 34622 down-only equal-mean valid). J-pair multipliers /mnt/l2/l2vast/_th_sz/M_AB.npz (new lots / base lots, 21135 trades in C.prepare(load_trades(S1B-COMB)) order).

Objectives: (a) equal lots - maxDD cut vs Q1-A (+ = shallower); (b) equal mean - lots of the cell scaled by one global factor s (column eq scale) so L6M mean = Q1-A, then maxDD cut (valid only for 0 < s <= 2; cells needing s > 2 are excluded from ranking). Tolerant eq score = second-smallest of the equal-mean cuts over L6M/PRE/X' (tolerant on one window). worst-20 ok = equal-mean worst-20 not worse than -5%.

**STANDING RULE: every D7 layer stays ON. The rows below (sizer off, old ladder) are REFERENCE ROWS only, never candidates. The deliverable is the best SETTING of the sizer layer; the live setting (Q1-A) is always one of the top-5 (see _th_joint/layers/sizer/topK_AB.json); if no cell beats Q1-A out of sample and in the exact engine, keep Q1-A.**

## Reference rows (weekly mean / maxDD, USD, first-order, S1b-COMB)
| ref | L6M mean / maxDD | HOLD | PRE | X' |
|--|--|--|--|--|
| Q1-A (ER<.30 x0.5) | +23046 / 79907 | +16047 / 99496 | +14626 / 140288 | +1800 / 128944 |
| sizer off (x1) | +30271 / 108038 | +21237 / 134892 | +16414 / 151592 | +255 / 215194 |
| old ladder (x.5/x1.5) | +26750 / 116699 | +20624 / 130207 | +19141 / 207515 | +147 / 138935 |

## ROLL FIX (17:35Z): features re-derived on roll-adjusted NQ bars
Features now use /mnt/l2/l2vast/_th_sz/ab/nq1m_adj.npz: the 12 quarterly roll jumps in nq1m_state.npz (> 120 pts, 00:00 UTC, gap <= 2 min: 2023-06-14 ... 2026-09-16) are back-adjusted (the earlier note that the file flags only 2 rolls and that the 2 percent return zeroing handles them was wrong: 120-300 pt jumps are 0.5-1.5 %). No jump was found for the 2024-12 and 2025-06 quarters in that file (data continuous there or the roll sits in a maintenance gap; cannot be detected). ES/RTY 1-s closes show no roll-sized jumps and are used unchanged. Trades affected by a roll inside a feature window: 239 (1.1 %) within 1 calendar day after a roll (intraday ER/ATR/GK/range windows), 1,268 (6.0 %) within 7 days (5-day windows), 5,482 (25.9 %) within 28 days (20-60 day norm medians). All 63,914 cells were re-scored: score correlation old vs new 0.991; top-200 overlap 177 of 200; the 12 finalists keep their cell definitions and their tolerant scores move by at most 7.5 points (ranks see ranked tables); no finalist changes label. The exact sets use the pre-fix M tables: at most 78 of 21,135 trades (0.4 %) differ for the vol finalists (280 for the range cell, not in the exact set).

**VOID NOTICE (17:00Z): the first exact rows for AB_F00/F01/F02/F12 (L6M cut +10.4 / +4.4 / +19.1 / +2.0 %) are VOID: sz_exact.py keyed the multiplier table on the arm second, not the signal second (SZ-CORE defect). The reading that first-order cuts are overstated 2-5x is WITHDRAWN. All six exact sets were re-queued from scratch with the fixed driver; there is no exact verdict yet and every number here is FIRST-ORDER SCREEN ONLY.**

## ADDENDUM 1 - results move with the base (FIRST-ORDER SCREEN ONLY)
**Testing-defect check: 0 of 400 cells have an L6M maxDD identical to the dollar on OLD-BASE and S1b-COMB: none, so no cached-list defect. Score correlation new vs old (Pearson 0.37, Spearman 0.29) shows the sizing answer moves with the base.** First-order pnl-per-lot scaling cannot see exits by construction; the base dependence seen here comes only from which trades the base produces. The exact runs below are the verdict.

Base proof (same Q1-A reference row on each base; OLD-BASE = replica ITER14 per-print/ThL2 cut, S1b-COMB = state cut):

| base | trades | cut-exit share | stop share | target share | mean trade $ | zero-rule (Q1-A) L6M mean/wk | L6M maxDD | HOLD maxDD | PRE maxDD |
|--|--|--|--|--|--|--|--|--|--|
| OLD-BASE | 23776 | 0.57 | 0.007 | 0.385 | 76 | 19583 | 141835 | 141835 | 165018 |
| S1B-COMB | 21135 | 0.34 | 0.042 | 0.453 | 117 | 24476 | 79907 | 99496 | 140288 |
| S1B-NOCUT | 18960 | 0.04 | 0.065 | 0.501 | 114 | 16663 | 182380 | 182380 | 127656 |
| S1B-UNIF | 19797 | 0.19 | 0.052 | 0.480 | 115 | 14701 | 174856 | 174856 | 134464 |

Finalists old base vs new base (first-order; tolerant equal-mean score, maxDD cut L6M/PRE; rank among the 400 M_AB cells):

| cell | tol new | tol old | delta | L6M cut new/old | PRE cut new/old | rank new -> old |
|--|--|--|--|--|--|--|
| VOL-pool vr_gk_w30_g20 [1.25, 0.0] onQ1A | 61.2 | 56.1 | +5.2 | +34/+69 | +52/+48 | 2 -> 17 |
| VOL-pool vr_park_w10_g20 [1.25, 0.0] onQ1A | 58.8 | 43.0 | +15.8 | +53/+51 | +45/+56 | 6 -> 85 |
| VOL-pool vr_gk_w10_g20 [1.25, 0.0] onQ1A | 59.4 | 65.8 | -6.5 | +54/+62 | +57/+56 | 4 -> 1 |
| VOL-pool vr_gk_w10_bk [1.25, 0.0] onQ1A | 60.6 | 63.4 | -2.8 | +17/+58 | +55/+57 | 3 -> 3 |
| VOL-P7 vr_rv1_w240_bk [1.25, 0.0] onQ1A | 55.6 | 53.0 | +2.6 | +43/+41 | +43/+56 | 14 -> 29 |
| VOL-P7 vr_park_w60_bk [1.1, 0.0] onQ1A | 50.8 | 40.9 | +9.9 | -3/+39 | +43/+32 | 25 -> 105 |
| ER-NQ er_nq_b3_n10 [0.2, 0.4, 0.25, 0.5, 1.0] min | 40.8 | 10.5 | +30.3 | +35/+49 | +20/+8 | 92 -> 377 |
| ER-NQ-P7 er_nq_b15_n20 [0.3, 0.0, 1.0] min | 44.5 | 43.0 | +1.5 | +37/+32 | +47/+49 | 66 -> 86 |
| ER-hyst-P7 hy_b15_n20_30_40 [0.5, 0.0] min | 35.0 | 44.4 | -9.4 | +30/+37 | +46/+50 | 168 -> 76 |
| RANGE rr_sofar_n20 [1.5, 0.0] onQ1A | 39.1 | 55.3 | -16.2 | +8/+48 | +35/+46 | 104 -> 20 |
| RANGE-P7 rr_sofar_n20 [1.5, 0.0] onQ1A | 45.9 | 51.3 | -5.4 | +8/+40 | +48/+55 | 55 -> 38 |
| ER-xinst-P7 er_min3_b15_n20 [0.35, 0.0, 1.0] min | 36.7 | 40.8 | -4.1 | +47/+66 | +57/+58 | 131 -> 106 |

## Plain sentences

- **Vol-target (pooled, B), stacked on Q1-A:** the best DD-first cell is "skip the signal when short-horizon range vol is more than 1.25x its 20-day norm" (vr_atr_b1_n50_g20 onQ1A [1.25, 0.0]): equal-mean maxDD cut +31/+65/+62 % on L6M/PRE/X' (equal lots +19/+59/+55 %), with L6M d mean +4391 $/wk at equal lots and skipping 52 % of signals; own placebo p 0.02, family p 0.23 (whole-set max-stat: only 0 of 34622 down-only cells reach family p <= .10); for context the "alone" variants (ER sizer also dropped) reach tolerant scores near 67 but skip 76 % of signals; the held-out live week would have changed by -66935 of the week's $104.8k. Graded step cells beat the continuous (ref/now)^p ones. It fails OOS as a picked procedure: walk-forward over the vol-target family cuts maxDD 36 % at equal lots but -9 % at equal mean (mean -6890 $/wk).
- **ER family (pooled NQ ER, A):** the best cell (er_nq_b3_n10 t3 [0.2, 0.4, 0.25, 0.5, 1.0] min) cuts equal-mean maxDD +41/+27/+51 % (L6M/PRE/X'), own p 0.02 but family p 1.00; the walk-forward of the ER picking procedure gives OOS maxDD 27 % at equal lots and -22 % at equal mean: the ER grid is selection noise around Q1-A once the pick has to be made in advance. Cells beating Q1-A on both mean and maxDD (L6M and HOLD d mean >= 0, tolerant cut > 0) exist (107 down-only), but none holds the family null.
- **ER of ES/RTY/max/min and ER at session open:** best er_max2_b15_n20 t3 [0.35, 0.45, 0.25, 0.5, 1.0] (min): equal-mean cut +35/+40/+5 % L6M/PRE/X', own p 0.02 / family p 1.00, live d$ -38084. Cross-instrument and session-open ER do not beat the NQ-only ER on the tolerant score (best 37 vs 41).
- **Range ratios (B02 generalised, so-far / premarket / first-30):** best rr_sofar_n20 stepv [1.5, 0.5] (onQ1A): equal-mean cut +16/+33/+35 % L6M/PRE/X', own p 0.02 / family p 1.00, live d$ -24468. 
- **VIX level / change (owned to 2026-10-16 only):** best vix_chg1 stepv [0.1, 0.0] (onQ1A): equal-mean cut +5/+36/+34 % L6M/PRE/X', own p 0.02 / family p 1.00, live d$ +0. 
- **Per-book / per-session thresholds:** the best (er_nq_b15_n10 t2 [0.5, 0.0, 1.0], scope ["sess", 1]) cuts equal-mean maxDD +40/+56/-16 %; the per-book and per-session cells that win do it by skipping (lot 0) in one window and are negative in another (X' or PRE), i.e. weaker than pooled cells; own-draw p of the group is mostly > .10 (see ledger).
- **P7 (K slice):** P7 alone the best volatility cell (vr_rv1_w240_bk stepv [1.25, 0.0] onQ1A) skips only 8 % of all signals (P7 trades) and cuts stack equal-mean maxDD +56/+56/+38 % with P7-alone tolerant score +50; ER cells on P7 alone give up to 45 % tolerant. WF over the P7 slice: OOS cut 32 % equal lots / 16 % equal mean. Live week (a P7-heavy week) would have lost -54480.

## Walk-forward of the picking procedure (monthly 2024-01..2026-10, 26 trailing weeks, 8-day purge; pick = largest trailing equal-mean maxDD cut among the set; OOS in 5-business-day blocks, approximate weeks)
| set | OOS cut equal lots % | OOS cut equal mean % | OOS d mean $/wk | ref OOS maxDD |
|--|--|--|--|--|
| ALL | -1.9 | -85.6 | -7488 | 140288 |
| A | -1.9 | -122.5 | -8999 | 140288 |
| B | +36.0 | -9.5 | -6890 | 140288 |
| ER-NQ pooled | +26.8 | -22.0 | -6635 | 140288 |
| VOL-pool | +45.1 | +21.2 | -5033 | 140288 |
| P7 (K slice) | +31.6 | +15.9 | -3088 | 140288 |

## Finalists (FIRST-ORDER SCREEN ONLY; <= 12; ids in /mnt/l2/l2vast/_th_sz/ab/finalists.json; down-only, worst-20 ok, own p <= .10; placebo B=400 within book x session lot-ratio permutations)

| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool | vr_gk_w30_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +34 / +47 / +52 / +57 | +60 / +35 | +53 | +5737 | - | +47 / +61 / +65 | 0.54 | 0.02/0.26 | 0.80 | plc400 0.005 | live d$ -51940 dd -1940 | 61.2 |
| VOL-pool | vr_park_w10_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +53 / +58 / +45 / +70 | +29 / +44 | +64 | +3219 | - | +59 / +52 / +74 | 0.56 | 0.02/0.34 | 0.87 | plc400 0.007 | live d$ -48050 dd +0 | 58.8 |
| VOL-pool | vr_gk_w10_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +54 / +59 / +57 / +55 | +7 / +42 | +66 | +2507 | - | +59 / +61 / +59 | 0.56 | 0.02/0.31 | 0.90 | plc400 0.002 | live d$ -63235 dd +0 | 59.4 |
| VOL-pool | vr_gk_w10_bk stepv[1.25,0.0] | onQ1A/down | ["pool"] | +17 / +34 / +55 / +59 | +43 / +32 | +54 | +3328 | - | +28 / +61 / +64 | 0.38 | 0.02/0.26 | 0.88 | plc400 0.002 | live d$ -42505 dd +0 | 60.6 |
| VOL-P7 | vr_rv1_w240_bk stepv[1.25,0.0] | onQ1A/down | ["book","P7"] | +43 / +34 / +43 / +20 | +85 / +20 | +52 | +6518 | - | +56 / +56 / +38 | 0.08 | 0.02/0.55 | 0.78 | plc400 0.002 | live d$ -54480 dd +0 | 55.6 |
| VOL-P7 | vr_park_w60_bk stepv[1.1,0.0] | onQ1A/down | ["book","P7"] | -3 / +17 / +43 / +44 | +39 / +26 | +27 | +3939 | - | +12 / +51 / +52 | 0.11 | 0.02/0.80 | 0.86 | plc400 0.012 | live d$ -57215 dd +0 | 50.8 |
| ER-NQ | er_nq_b3_n10 t3[0.2,0.4,0.25,0.5,1.0] | min/down | ["pool"] | +35 / +11 / +20 / +46 | +57 / +18 | +42 | +1987 | - | +41 / +27 / +51 | 0.17 | 0.02/1.00 | 0.91 | plc400 0.002 | live d$ -29212 dd +0 | 40.8 |
| ER-NQ-P7 | er_nq_b15_n20 t2[0.3,0.0,1.0] | min/down | ["book","P7"] | +37 / -18 / +47 / +49 | +4 / +25 | +45 | -1129 | 38 | +34 / +45 / +47 | 0.15 | 0.02/0.98 | 1.05 | plc400 0.007 | live d$ -36915 dd -6905 | 44.5 |
| ER-hyst-P7 | hy_b15_n20_30_40 stepv[0.5,0.0] | min/down | ["book","P7"] | +30 / -41 / +46 / +54 | -12 / +37 | +50 | -3889 | 162 | +15 / +35 / +44 | 0.17 | 0.05/1.00 | 1.21 | plc400 0.040 | live d$ -50125 dd -6905 | 35.0 |
| RANGE | rr_sofar_n20 stepv[1.5,0.0] | onQ1A/down | ["pool"] | +8 / -6 / +35 / +49 | -8 / +30 | +22 | +1623 | - | +14 / +39 / +52 | 0.30 | 0.02/1.00 | 0.94 | plc400 0.002 | live d$ -69300 dd -8855 | 39.1 |
| RANGE-P7 | rr_sofar_n20 stepv[1.5,0.0] | onQ1A/down | ["book","P7"] | +8 / +15 / +48 / +41 | -2 / +25 | +18 | +2133 | - | +16 / +52 / +46 | 0.08 | 0.02/0.98 | 0.92 | plc400 0.002 | live d$ -47815 dd +0 | 45.9 |
| ER-xinst-P7 | er_min3_b15_n20 t2[0.35,0.0,1.0] | min/down | ["book","P7"] | +47 / -7 / +57 / +62 | -28 / +44 | +58 | -7215 | 190 | +23 / +37 / +43 | 0.21 | 0.03/1.00 | 1.47 | plc400 0.040 | live d$ -63305 dd -6905 | 36.7 |

## Ranked family tables (FIRST-ORDER SCREEN ONLY; top 6 per sub-family by tolerant equal-mean score; down-only; worst-20 ok; family p = max-stat over all 63914 cells, B=64 common permutations, own p B=64)

### ER-NQ (1912 valid cells; 1053 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ | er_nq_b3_n10 t3[0.2,0.4,0.25,0.5,1.0] | min/down | ["pool"] | +35 / +11 / +20 / +46 | +57 / +18 | +42 | +1987 | - | +41 / +27 / +51 | 0.17 | 0.02/1.00 | 0.91 | plc400 0.002 | live d$ -29212 dd +0 | 40.8 |
| ER-NQ | er_nq_b15_n14 t2[0.35,0.0,1.0] | min/down | ["pool"] | +54 / +38 / +58 / +48 | -7 / +37 | +58 | -6284 | 146 | +40 / +45 / +32 | 0.61 | 0.02/1.00 | 1.31 | - | live d$ -46430 dd +0 | 39.6 |
| ER-NQ | er_nq_b3_n30 t3[0.35,0.55,0.25,0.5,1.0] | min/down | ["pool"] | +40 / +43 / +62 / +61 | -27 / +44 | +50 | -7844 | 246 | +5 / +40 / +38 | 0.37 | 0.02/1.00 | 1.58 | - | live d$ -46816 dd +0 | 38.1 |
| ER-NQ | er_nq_b3_n20 t3[0.35,0.55,0.25,0.5,1.0] | min/down | ["pool"] | +46 / +39 / +50 / +50 | +13 / +33 | +52 | -4301 | 117 | +33 / +38 / +38 | 0.32 | 0.03/1.00 | 1.24 | - | live d$ -52048 dd +0 | 38.0 |
| ER-NQ | er_nq_b3_n14 t3[0.35,0.55,0.25,0.5,1.0] | min/down | ["pool"] | +43 / +26 / +37 / +50 | +34 / +27 | +53 | -2198 | 64 | +37 / +30 / +44 | 0.28 | 0.02/1.00 | 1.11 | - | live d$ -50536 dd +0 | 36.5 |
| ER-NQ | er_nq_b3_n10 t3[0.25,0.45,0.25,0.5,1.0] | min/down | ["pool"] | +30 / +15 / +24 / +29 | +61 / +22 | +38 | +2047 | - | +36 / +30 / +36 | 0.20 | 0.02/1.00 | 0.91 | - | live d$ -32875 dd +0 | 35.5 |

### ER-NQ-P7 (2367 valid cells; 1419 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ-P7 | er_nq_b15_n20 t2[0.3,0.0,1.0] | min/down | ["book","P7"] | +37 / -18 / +47 / +49 | +4 / +25 | +45 | -1129 | 38 | +34 / +45 / +47 | 0.15 | 0.02/0.98 | 1.05 | plc400 0.007 | live d$ -36915 dd -6905 | 44.5 |
| ER-NQ-P7 | er_nq_b15_n14 t2[0.35,0.0,1.0] | min/down | ["book","P7"] | +36 / +20 / +45 / +31 | +19 / +26 | +48 | +2222 | - | +42 / +50 / +37 | 0.15 | 0.03/1.00 | 0.91 | - | live d$ -30145 dd +0 | 41.6 |
| ER-NQ-P7 | er_nq_b15_n20 t2[0.35,0.0,1.0] | min/down | ["book","P7"] | +50 / -10 / +43 / +45 | -2 / +31 | +59 | -2303 | 58 | +44 / +36 / +39 | 0.17 | 0.02/1.00 | 1.11 | - | live d$ -63305 dd -6905 | 38.5 |
| ER-NQ-P7 | er_nq_b30_n10 t2[0.5,0.0,1.0] | min/down | ["book","P7"] | +44 / +3 / +35 / +55 | +4 / +27 | +50 | -2007 | 57 | +38 / +28 / +50 | 0.17 | 0.05/1.00 | 1.10 | - | live d$ -63395 dd -6905 | 38.3 |
| ER-NQ-P7 | er_nq_b1_n14 t2[0.55,0.0,1.0] | min/down | ["book","P7"] | +48 / +35 / +66 / +70 | -40 / +57 | +54 | -10056 | 265 | +1 / +36 / +43 | 0.24 | 0.05/1.00 | 1.89 | - | live d$ -90220 dd -4500 | 36.4 |
| ER-NQ-P7 | er_nq_b3_n10 t3[0.2,0.4,0.25,0.5,1.0] | min/down | ["book","P7"] | +31 / +10 / +13 / +35 | +39 / +15 | +35 | +1318 | - | +35 / +18 / +39 | 0.11 | 0.02/1.00 | 0.94 | - | live d$ -26300 dd +0 | 35.2 |

### ER-NQ-book (4090 valid cells; 544 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ-book | er_nq_b15_n45 t2[0.1,0.0,1.0] | min/down | ["book","K7"] | +20 / +9 / -4 / +23 | +16 / -0 | +21 | +1244 | - | +24 / +2 / +27 | 0.11 | 0.02/1.00 | 0.95 | - | live d$ -490 dd +0 | 24.1 |
| ER-NQ-book | er_nq_b15_n45 t2[0.15,0.0,1.0] | min/down | ["book","K7"] | +16 / +7 / -8 / +20 | +11 / +1 | +16 | +751 | - | +19 / -4 / +23 | 0.17 | 0.02/1.00 | 0.97 | - | live d$ -330 dd +0 | 18.8 |
| ER-NQ-book | er_nq_b60_n10 t2[0.5,0.0,1.0] | min/down | ["book","M7"] | +14 / +13 / +13 / -19 | +18 / +10 | +17 | +1119 | - | +18 / +17 / -13 | 0.15 | 0.05/1.00 | 0.95 | - | live d$ -2415 dd +0 | 17.0 |
| ER-NQ-book | er_nq_b60_n45 t2[0.25,0.0,1.0] | min/down | ["book","M7"] | +18 / +6 / +11 / -28 | +51 / +7 | +24 | +1863 | - | +23 / +17 / -20 | 0.15 | 0.06/1.00 | 0.94 | - | live d$ -12275 dd +0 | 16.7 |
| ER-NQ-book | er_nq_b15_n45 t2[0.5,0.0,1.0] | min/down | ["book","M7"] | +14 / +16 / +15 / -24 | +31 / +11 | +21 | +367 | - | +15 / +16 / -23 | 0.21 | 0.25/1.00 | 0.99 | - | live d$ -8435 dd +0 | 15.4 |
| ER-NQ-book | er_nq_b60_n20 t2[0.6,0.0,1.0] | min/down | ["book","M7"] | +13 / +15 / +15 / -26 | +31 / +10 | +19 | +781 | - | +15 / +18 / -22 | 0.20 | 0.22/1.00 | 0.97 | - | live d$ -6015 dd +0 | 15.0 |

### ER-NQ-bxs (4395 valid cells; 84 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ-bxs | er_nq_b15_n20 t2[0.5,0.0,1.0] | min/down | ["bxs","P7",1] | +34 / -41 / +51 / -22 | +22 / +29 | +38 | +2148 | - | +39 / +55 / -12 | 0.07 | 0.03/1.00 | 0.92 | - | live d$ -1690 dd +0 | 39.0 |
| ER-NQ-bxs | er_nq_b15_n20 t2[0.45,0.0,1.0] | min/down | ["bxs","P7",1] | +31 / -48 / +47 / -32 | +21 / +29 | +33 | +2472 | - | +37 / +52 / -20 | 0.06 | 0.03/1.00 | 0.91 | - | live d$ -1690 dd +0 | 37.4 |
| ER-NQ-bxs | er_nq_b5_n20 t2[0.45,0.0,1.0] | replace/down | ["bxs","P7",1] | +27 / -43 / +38 / -8 | +6 / +23 | +29 | +1648 | - | +32 / +42 / -1 | 0.07 | 0.14/1.00 | 0.94 | - | live d$ -385 dd +0 | 31.8 |
| ER-NQ-bxs | er_nq_b5_n20 t2[0.45,0.0,1.0] | min/down | ["bxs","P7",1] | +27 / -43 / +38 / -8 | +6 / +23 | +29 | +1648 | - | +32 / +42 / -1 | 0.07 | 0.14/1.00 | 0.94 | - | live d$ -385 dd +0 | 31.8 |
| ER-NQ-bxs | er_nq_b15_n20 t2[0.4,0.0,1.0] | min/down | ["bxs","P7",1] | +29 / -42 / +44 / -23 | +21 / +25 | +32 | +258 | - | +30 / +45 / -22 | 0.06 | 0.15/1.00 | 0.99 | - | live d$ -1690 dd +0 | 29.7 |
| ER-NQ-bxs | er_nq_b15_n20 t2[0.35,0.0,1.0] | min/down | ["bxs","P7",1] | +18 / -58 / +41 / -38 | +19 / +22 | +31 | +3441 | - | +28 / +49 / -20 | 0.05 | 0.11/1.00 | 0.87 | - | live d$ -1690 dd +0 | 28.0 |

### ER-NQ-sess (5286 valid cells; 529 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ-sess | er_nq_b15_n10 t2[0.5,0.0,1.0] | min/down | ["sess",1] | +36 / -36 / +53 / -22 | +7 / +26 | +46 | +1233 | - | +40 / +56 / -16 | 0.23 | 0.02/1.00 | 0.95 | - | live d$ -1120 dd +0 | 39.9 |
| ER-NQ-sess | er_nq_b15_n20 t3[0.3,0.5,0.25,0.5,1.0] | min/down | ["sess",1] | +31 / -35 / +42 / -17 | +29 / +19 | +37 | +2471 | - | +37 / +47 / -6 | 0.12 | 0.02/1.00 | 0.91 | - | live d$ +2366 dd +0 | 37.3 |
| ER-NQ-sess | er_nq_b15_n10 t2[0.55,0.0,1.0] | min/down | ["sess",1] | +38 / -34 / +49 / -7 | +26 / +26 | +49 | -598 | 19 | +37 / +48 / -9 | 0.25 | 0.15/1.00 | 1.03 | - | live d$ -1585 dd +0 | 36.9 |
| ER-NQ-sess | er_nq_b15_n45 t2[0.15,0.0,1.0] | min/down | ["sess",1] | +19 / +14 / +47 / +29 | +49 / +30 | +32 | +2627 | - | +27 / +52 / +37 | 0.16 | 0.08/1.00 | 0.90 | - | live d$ +3000 dd +0 | 36.5 |
| ER-NQ-sess | er_nq_b15_n10 t2[0.45,0.0,1.0] | min/down | ["sess",1] | +31 / -25 / +39 / -32 | +10 / +24 | +41 | +1631 | - | +36 / +44 / -23 | 0.22 | 0.08/1.00 | 0.93 | - | live d$ +3680 dd +0 | 36.2 |
| ER-NQ-sess | er_nq_b15_n20 t3[0.35,0.45,0.25,0.5,1.0] | min/down | ["sess",1] | +31 / -32 / +40 / -19 | +15 / +20 | +34 | +1833 | - | +36 / +44 / -10 | 0.11 | 0.02/1.00 | 0.93 | - | live d$ +3566 dd +0 | 35.8 |

### ER-hyst (49 valid cells; 26 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-hyst | hy_b5_n30_35_50 stepv[0.5,0.5] | min/down | ["pool"] | +13 / +26 / +31 / +28 | +9 / +21 | +30 | -1375 | 129 | +8 / +27 / +24 | 0.18 | 0.03/1.00 | 1.06 | - | live d$ -4748 dd +0 | 23.5 |
| ER-hyst | hy_b15_n30_30_45 stepv[0.5,0.5] | min/down | ["pool"] | +28 / +18 / +33 / +16 | +7 / +25 | +34 | -1969 | 87 | +21 / +26 / +7 | 0.19 | 0.02/1.00 | 1.10 | - | live d$ -18544 dd +0 | 21.0 |
| ER-hyst | hy_b15_n30_35_50 stepv[0.5,0.5] | min/down | ["pool"] | +28 / +18 / +37 / +17 | -2 / +25 | +33 | -2530 | 112 | +19 / +29 / +6 | 0.20 | 0.02/1.00 | 1.13 | - | live d$ -23348 dd +0 | 18.6 |
| ER-hyst | hy_b15_n30_30_40 stepv[0.5,0.5] | min/down | ["pool"] | +26 / +18 / +31 / +11 | +3 / +21 | +35 | -2071 | 98 | +18 / +24 / +2 | 0.18 | 0.03/1.00 | 1.11 | - | live d$ -17183 dd +0 | 18.5 |
| ER-hyst | hy_b15_n20_20_30 stepv[0.5,0.5] | min/down | ["pool"] | +20 / +5 / +25 / +5 | +9 / +16 | +22 | -488 | 31 | +18 / +24 / +3 | 0.10 | 0.02/1.00 | 1.02 | - | live d$ -12596 dd +0 | 17.7 |
| ER-hyst | hy_b15_n10_30_45 stepv[0.5,0.5] | min/down | ["pool"] | +11 / +13 / +19 / +18 | +9 / +13 | +15 | -477 | 56 | +9 / +18 / +16 | 0.08 | 0.02/1.00 | 1.02 | - | live d$ -567 dd +0 | 16.0 |

### ER-hyst-P7 (55 valid cells; 42 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-hyst-P7 | hy_b15_n20_25_35 stepv[0.5,0.0] | min/down | ["book","P7"] | +42 / -18 / +34 / +47 | -13 / +24 | +55 | -2166 | 64 | +36 / +28 / +41 | 0.15 | 0.03/1.00 | 1.10 | - | live d$ -54335 dd -6905 | 36.4 |
| ER-hyst-P7 | hy_b15_n20_30_40 stepv[0.5,0.0] | min/down | ["book","P7"] | +30 / -41 / +46 / +54 | -12 / +37 | +50 | -3889 | 162 | +15 / +35 / +44 | 0.17 | 0.05/1.00 | 1.21 | plc400 0.040 | live d$ -50125 dd -6905 | 35.0 |
| ER-hyst-P7 | hy_b5_n30_35_50 stepv[0.5,0.5] | min/down | ["book","P7"] | +21 / +20 / +20 / +15 | +24 / +15 | +28 | +684 | - | +24 / +23 / +17 | 0.08 | 0.02/1.00 | 0.97 | - | live d$ -8075 dd +0 | 22.7 |
| ER-hyst-P7 | hy_b15_n30_35_50 stepv[0.5,0.5] | min/down | ["book","P7"] | +26 / +12 / +22 / +4 | +21 / +18 | +29 | -365 | 18 | +24 / +21 / +2 | 0.09 | 0.02/1.00 | 1.02 | - | live d$ -23641 dd +0 | 21.0 |
| ER-hyst-P7 | hy_b15_n30_30_45 stepv[0.5,0.5] | min/down | ["book","P7"] | +26 / +12 / +21 / +0 | +24 / +18 | +29 | -128 | 6 | +25 / +20 / -0 | 0.08 | 0.02/1.00 | 1.01 | - | live d$ -20035 dd +0 | 20.1 |
| ER-hyst-P7 | hy_b15_n30_25_40 stepv[0.5,0.5] | min/down | ["book","P7"] | +24 / +12 / +20 / +3 | +25 / +14 | +27 | -13 | 1 | +24 / +20 / +3 | 0.07 | 0.02/1.00 | 1.00 | - | live d$ -18674 dd +0 | 19.5 |

### ER-open (209 valid cells; 149 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-open | er_nq_b5_n20_open t2[0.5,0.5,1.0] | min/down | ["pool"] | +23 / +22 / +33 / +33 | +12 / +22 | +33 | -1779 | 98 | +16 / +27 / +27 | 0.20 | 0.02/1.00 | 1.09 | - | live d$ -25321 dd +0 | 26.5 |
| ER-open | er_nq_b5_n20_open t3[0.25,0.45,0.5,0.75,1.0] | min/down | ["pool"] | +13 / +19 / +32 / +30 | +14 / +17 | +21 | -1503 | 144 | +6 / +27 / +25 | 0.16 | 0.02/1.00 | 1.08 | - | live d$ -17058 dd +0 | 25.0 |
| ER-open | er_nq_b5_n20_open cont[0.6,0.5,1.0] | min/down | ["pool"] | +20 / +21 / +35 / +33 | +5 / +22 | +28 | -2305 | 142 | +11 / +27 / +25 | 0.20 | 0.02/1.00 | 1.12 | - | live d$ -21718 dd +0 | 24.8 |
| ER-open | er_nq_b5_n10_open t2[0.25,0.5,1.0] | min/down | ["pool"] | +25 / +14 / +25 / +14 | +23 / +15 | +27 | -257 | 13 | +24 / +24 / +13 | 0.10 | 0.02/1.00 | 1.01 | - | live d$ -19664 dd +0 | 23.9 |
| ER-open | er_nq_b5_n20_open t3[0.3,0.5,0.5,0.75,1.0] | min/down | ["pool"] | +16 / +23 / +30 / +30 | +10 / +17 | +23 | -1689 | 129 | +9 / +24 / +24 | 0.17 | 0.02/1.00 | 1.09 | - | live d$ -17608 dd +0 | 23.9 |
| ER-open | er_nq_b5_n10_open t2[0.45,0.5,1.0] | min/down | ["pool"] | +25 / +22 / +28 / +28 | +29 / +19 | +33 | -1140 | 57 | +21 / +24 / +24 | 0.16 | 0.02/1.00 | 1.06 | - | live d$ -16871 dd +0 | 23.6 |

### ER-xinst (1645 valid cells; 606 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-xinst | er_max2_b15_n20 t3[0.35,0.45,0.25,0.5,1.0] | min/down | ["pool"] | +42 / -2 / +47 / +15 | +7 / +30 | +56 | -2593 | 77 | +35 / +40 / +5 | 0.28 | 0.02/1.00 | 1.12 | - | live d$ -38084 dd +0 | 35.0 |
| ER-xinst | er_mean3_b15_n20 t3[0.3,0.5,0.25,0.5,1.0] | min/down | ["pool"] | +52 / -9 / +50 / +11 | -4 / +36 | +55 | -5224 | 125 | +37 / +34 / -18 | 0.32 | 0.02/1.00 | 1.32 | - | live d$ -34051 dd +0 | 33.8 |
| ER-xinst | er_max3_b15_n20 t3[0.35,0.55,0.25,0.5,1.0] | min/down | ["pool"] | +52 / -4 / +46 / +18 | -5 / +32 | +58 | -4109 | 99 | +40 / +33 / -1 | 0.29 | 0.02/1.00 | 1.24 | - | live d$ -45448 dd +0 | 33.4 |
| ER-xinst | er_max2_b15_n20 t3[0.3,0.4,0.25,0.5,1.0] | min/down | ["pool"] | +38 / -5 / +46 / +15 | +6 / +28 | +49 | -1699 | 56 | +33 / +42 / +9 | 0.25 | 0.02/1.00 | 1.08 | - | live d$ -27434 dd +0 | 33.2 |
| ER-xinst | er_max3_b15_n20 t3[0.35,0.45,0.25,0.5,1.0] | min/down | ["pool"] | +42 / -3 / +43 / +12 | -4 / +28 | +52 | -3189 | 95 | +33 / +34 / -1 | 0.26 | 0.02/1.00 | 1.15 | - | live d$ -38084 dd +0 | 33.1 |
| ER-xinst | er_max3_b5_n30 t3[0.2,0.4,0.25,0.5,1.0] | min/down | ["pool"] | +44 / +16 / +40 / +35 | +7 / +28 | +47 | -2475 | 71 | +37 / +32 / +27 | 0.22 | 0.02/1.00 | 1.12 | - | live d$ -17334 dd +0 | 32.4 |

### ER-xinst-P7 (715 valid cells; 290 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-xinst-P7 | er_max2_b15_n20 t2[0.4,0.0,1.0] | min/down | ["book","P7"] | +24 / -13 / +49 / +44 | +7 / +33 | +45 | -2308 | 121 | +15 / +43 / +37 | 0.18 | 0.05/1.00 | 1.11 | - | live d$ -63305 dd -6905 | 37.1 |
| ER-xinst-P7 | er_min3_b15_n20 t2[0.35,0.0,1.0] | min/down | ["book","P7"] | +47 / -7 / +57 / +62 | -28 / +44 | +58 | -7215 | 190 | +23 / +37 / +43 | 0.21 | 0.03/1.00 | 1.47 | plc400 0.040 | live d$ -63305 dd -6905 | 36.7 |
| ER-xinst-P7 | er_mean3_b15_n20 t2[0.5,0.0,1.0] | min/down | ["book","P7"] | +57 / -3 / +64 / +51 | -34 / +52 | +61 | -7392 | 161 | +36 / +46 / +27 | 0.22 | 0.02/1.00 | 1.49 | - | live d$ -77290 dd -4500 | 36.4 |
| ER-xinst-P7 | er_max3_b15_n20 t2[0.4,0.0,1.0] | min/down | ["book","P7"] | +14 / -36 / +41 / +47 | -2 / +31 | +35 | -2231 | 200 | +4 / +35 / +41 | 0.16 | 0.06/1.00 | 1.11 | - | live d$ -63305 dd -6905 | 34.9 |
| ER-xinst-P7 | er_max3_b15_n20 t2[0.35,0.0,1.0] | min/down | ["book","P7"] | +34 / -30 / +42 / +32 | -2 / +25 | +47 | -81 | 3 | +34 / +42 / +32 | 0.14 | 0.06/1.00 | 1.00 | - | live d$ -63305 dd -6905 | 34.0 |
| ER-xinst-P7 | er_min3_b15_n20 t3[0.3,0.4,0.25,0.5,1.0] | min/down | ["book","P7"] | +40 / +13 / +35 / +41 | +20 / +29 | +46 | -2066 | 64 | +34 / +28 / +35 | 0.19 | 0.02/1.00 | 1.11 | - | live d$ -29991 dd +0 | 33.7 |

### RANGE (314 valid cells; 89 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RANGE | rr_sofar_n20 stepv[1.5,0.5] | onQ1A/down | ["pool"] | +10 / +22 / +29 / +32 | +3 / +16 | +19 | +1423 | - | +16 / +33 / +35 | 0.13 | 0.02/1.00 | 0.94 | - | live d$ -24468 dd +0 | 33.3 |
| RANGE | rr_pre_n20 stepv[1.5,0.0] | onQ1A/down | ["pool"] | -16 / +6 / +20 / +21 | +27 / +5 | +1 | +2163 | - | -6 / +27 / +28 | 0.08 | 0.02/1.00 | 0.91 | - | live d$ -7975 dd +0 | 26.6 |
| RANGE | rr_pre_n40 stepv[1.5,0.0] | onQ1A/down | ["pool"] | -16 / +4 / +19 / +21 | +28 / +5 | -2 | +1810 | - | -8 / +25 / +27 | 0.08 | 0.02/1.00 | 0.93 | - | live d$ -7975 dd +0 | 25.2 |
| RANGE | rr_pre_n20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | -15 / +4 / +19 / +21 | +30 / +2 | -3 | +1765 | - | -6 / +25 / +27 | 0.12 | 0.02/1.00 | 0.93 | - | live d$ -19280 dd +0 | 25.0 |
| RANGE | rr_pre_n10 stepv[1.0,0.0] | onQ1A/down | ["pool"] | +14 / +17 / +16 / +33 | +34 / +8 | +12 | +2395 | - | +22 / +24 / +39 | 0.18 | 0.05/1.00 | 0.90 | - | live d$ -19280 dd +0 | 23.7 |
| RANGE | rr_pre_n5 stepv[1.0,0.0] | onQ1A/down | ["pool"] | +14 / +17 / +14 / +11 | +28 / +0 | +11 | +2472 | - | +22 / +23 / +20 | 0.18 | 0.06/1.00 | 0.90 | - | live d$ -19280 dd +0 | 22.3 |

### RANGE-P7 (338 valid cells; 100 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RANGE-P7 | rr_sofar_n10 stepv[1.0,0.0] | onQ1A/down | ["book","P7"] | +11 / -6 / +41 / +52 | -19 / +39 | +25 | -3678 | 423 | -6 / +30 / +43 | 0.15 | 0.05/1.00 | 1.19 | - | live d$ -53465 dd +0 | 29.8 |
| RANGE-P7 | rr_sofar_n20 stepv[1.5,0.5] | onQ1A/down | ["book","P7"] | +6 / +24 / +22 / +23 | +8 / +15 | +14 | +1468 | - | +12 / +27 / +27 | 0.08 | 0.02/1.00 | 0.94 | - | live d$ -20330 dd +0 | 26.9 |
| RANGE-P7 | rr_pre_n10 stepv[1.15,0.0] | onQ1A/down | ["book","P7"] | +5 / +19 / +19 / +26 | +41 / +5 | +13 | +1470 | - | +10 / +23 / +30 | 0.03 | 0.03/1.00 | 0.95 | - | live d$ -4460 dd +0 | 23.4 |
| RANGE-P7 | rr_pre_n5 stepv[1.0,0.0] | onQ1A/down | ["book","P7"] | +14 / +19 / +12 / +1 | +42 / +2 | +12 | +3305 | - | +24 / +22 / +13 | 0.03 | 0.09/1.00 | 0.88 | - | live d$ -16460 dd +0 | 22.5 |
| RANGE-P7 | rr_pre_n20 stepv[1.15,0.0] | onQ1A/down | ["book","P7"] | -4 / +17 / +17 / +26 | +45 / +2 | +12 | +1753 | - | +3 / +22 / +31 | 0.03 | 0.06/1.00 | 0.94 | - | live d$ -16460 dd +0 | 22.1 |
| RANGE-P7 | rr_sofar_n20 stepv[1.25,0.5] | onQ1A/down | ["book","P7"] | +5 / +23 / +32 / +22 | +3 / +20 | +18 | -47 | 13 | +4 / +32 / +22 | 0.11 | 0.05/1.00 | 1.00 | - | live d$ -25626 dd +0 | 22.0 |

### RANGE-book (2251 valid cells; 120 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RANGE-book | rr_sofar_n20 stepv[1.15,0.0] | onQ1A/down | ["book","M7"] | +7 / +12 / +14 / -8 | +12 / +8 | +11 | +1230 | - | +12 / +18 / -2 | 0.10 | 0.11/1.00 | 0.95 | - | live d$ -9320 dd +0 | 11.9 |
| RANGE-book | rr_sofar_n40 stepv[1.0,0.0] | onQ1A/down | ["book","M7"] | +9 / +15 / +16 / -11 | +25 / +10 | +14 | +573 | - | +11 / +18 / -8 | 0.13 | 0.26/1.00 | 0.98 | - | live d$ -5840 dd +0 | 11.5 |
| RANGE-book | rr_sofar_n10 stepv[1.0,0.0] | onQ1A/down | ["book","M7"] | +12 / +12 / +7 / -6 | +31 / +10 | +17 | +903 | - | +15 / +10 / -2 | 0.12 | 0.26/1.00 | 0.97 | - | live d$ -8675 dd +0 | 10.0 |
| RANGE-book | rr_sofar_n10 stepv[1.15,0.0] | onQ1A/down | ["book","M7"] | +8 / +8 / +8 / -13 | +20 / +6 | +12 | +588 | - | +9 / +10 / -11 | 0.10 | 0.35/1.00 | 0.98 | - | live d$ -9320 dd +0 | 9.5 |
| RANGE-book | rr_sofar_n20 stepv[1.0,0.0] | onQ1A/down | ["book","M7"] | +6 / +12 / +16 / -12 | +35 / +10 | +17 | +1139 | - | +9 / +19 / -7 | 0.12 | 0.43/1.00 | 0.96 | - | live d$ -6255 dd +0 | 9.5 |
| RANGE-book | rr_sofar_n10 stepv[1.25,0.0] | onQ1A/down | ["book","M7"] | +9 / +6 / +7 / -10 | +4 / +7 | +8 | +632 | - | +11 / +9 / -7 | 0.08 | 0.17/1.00 | 0.97 | - | live d$ -9320 dd +0 | 9.3 |

### VIX (23 valid cells; 2 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VIX | vix_chg1 stepv[0.1,0.0] | onQ1A/down | ["pool"] | +0 / -16 / +33 / +30 | +38 / +23 | +4 | +1305 | - | +5 / +36 / +34 | 0.11 | 0.02/1.00 | 0.95 | - | live d$ +0 dd +0 | 33.7 |
| VIX | vix_chg1 stepv[0.1,0.5] | onQ1A/down | ["pool"] | +0 / +16 / +15 / +9 | +22 / +12 | +4 | +410 | - | +1 / +17 / +11 | 0.05 | 0.05/1.00 | 0.99 | - | live d$ +0 dd +0 | 10.7 |
| VIX | vix_rel20 stepv[1.15,0.5] | onQ1A/down | ["pool"] | +0 / +5 / +38 / +8 | +5 / +15 | -0 | +335 | - | +1 / +39 / +9 | 0.07 | 0.12/1.00 | 0.99 | - | live d$ +0 dd +0 | 9.5 |
| VIX | vix_lvl stepv[17,0.5] | onQ1A/down | ["pool"] | +0 / +20 / +43 / +20 | +2 / +18 | +6 | -3300 | - | -14 / +35 / +9 | 0.19 | 0.20/1.00 | 1.14 | - | live d$ +0 dd +0 | 8.9 |
| VIX | vix_chg1 stepv[0.03,0.5] | onQ1A/down | ["pool"] | +0 / +20 / +19 / +18 | -12 / +14 | +7 | -3011 | 34682 | -12 / +8 / +8 | 0.12 | 0.15/1.00 | 1.13 | - | live d$ +0 dd +0 | 7.7 |
| VIX | vix_lvl stepv[19,0.5] | onQ1A/down | ["pool"] | +0 / +5 / +43 / -8 | +9 / +17 | +1 | +634 | - | +3 / +45 / -5 | 0.11 | 0.34/1.00 | 0.97 | - | live d$ +0 dd +0 | 2.7 |

### VIX-P7 (31 valid cells; 0 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VIX-P7 | vix_chg1 stepv[0.1,0.0] | onQ1A/down | ["book","P7"] | +0 / -9 / +34 / +9 | +34 / +20 | +4 | +652 | - | +2 / +35 / +11 | 0.03 | 0.17/1.00 | 0.98 | - | live d$ +0 dd +0 | 11.3 |
| VIX-P7 | vix_chg1 stepv[0.03,0.5] | onQ1A/down | ["book","P7"] | -3 / +17 / +17 / +13 | -5 / +14 | +2 | -920 | - | -7 / +14 / +9 | 0.07 | 0.14/1.00 | 1.04 | - | live d$ +0 dd +0 | 9.2 |
| VIX-P7 | vix_rel20 stepv[1.15,0.5] | onQ1A/down | ["book","P7"] | +0 / +10 / +30 / +6 | +4 / +11 | -0 | +380 | - | +2 / +31 / +8 | 0.05 | 0.18/1.00 | 0.98 | - | live d$ +0 dd +0 | 7.9 |
| VIX-P7 | vix_lvl stepv[17,0.5] | onQ1A/down | ["book","P7"] | +0 / +20 / +30 / +15 | +11 / +13 | +5 | -2498 | - | -10 / +23 / +6 | 0.12 | 0.31/1.00 | 1.10 | - | live d$ +0 dd +0 | 6.2 |
| VIX-P7 | vix_lvl stepv[19,0.0] | onQ1A/down | ["book","P7"] | +0 / +18 / +51 / -9 | +2 / +21 | +2 | +1465 | - | +6 / +54 / -2 | 0.07 | 0.32/1.00 | 0.94 | - | live d$ +0 dd +0 | 6.1 |
| VIX-P7 | vix_lvl stepv[15,0.5] | onQ1A/down | ["book","P7"] | +0 / +20 / +30 / +23 | -14 / +23 | +23 | -3821 | 44010 | -22 / +15 / +6 | 0.18 | 0.34/1.00 | 1.22 | - | live d$ +0 dd +0 | 6.0 |

### VOL-P7 (569 valid cells; 406 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-P7 | vr_rv1_w240_bk stepv[1.25,0.0] | onQ1A/down | ["book","P7"] | +43 / +34 / +43 / +20 | +85 / +20 | +52 | +6518 | - | +56 / +56 / +38 | 0.08 | 0.02/0.55 | 0.78 | plc400 0.002 | live d$ -54480 dd +0 | 55.6 |
| VOL-P7 | vr_ewma5_l94_g20 stepv[1.1,0.0] | onQ1A/down | ["book","P7"] | +42 / +36 / +42 / +64 | +67 / +33 | +55 | +4246 | - | +51 / +51 / +69 | 0.15 | 0.02/0.80 | 0.85 | - | live d$ -67170 dd -5840 | 51.0 |
| VOL-P7 | vr_park_w60_bk stepv[1.1,0.0] | onQ1A/down | ["book","P7"] | -3 / +17 / +43 / +44 | +39 / +26 | +27 | +3939 | - | +12 / +51 / +52 | 0.11 | 0.02/0.80 | 0.86 | plc400 0.012 | live d$ -57215 dd +0 | 50.8 |
| VOL-P7 | vr_ewma5_l94_g20 stepv[1.25,0.0] | onQ1A/down | ["book","P7"] | +41 / +48 / +30 / +62 | +64 / +26 | +51 | +4031 | - | +50 / +40 / +68 | 0.13 | 0.03/0.83 | 0.85 | - | live d$ -54370 dd +0 | 49.6 |
| VOL-P7 | vr_rv1_w240_g20 stepv[1.1,0.0] | onQ1A/down | ["book","P7"] | +20 / +34 / +43 / +72 | +37 / +29 | +41 | +2760 | - | +29 / +49 / +75 | 0.14 | 0.02/0.86 | 0.89 | - | live d$ -58775 dd +0 | 49.1 |
| VOL-P7 | vr_park_w60_g20 stepv[1.5,0.0] | onQ1A/down | ["book","P7"] | +2 / +22 / +41 / +46 | +44 / +24 | +35 | +3339 | - | +14 / +48 / +53 | 0.10 | 0.02/0.88 | 0.88 | - | live d$ -45090 dd +0 | 48.3 |

### VOL-book (2658 valid cells; 293 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-book | vr_gk_w10_g20 stepv[1.25,0.5] | onQ1A/down | ["book","U7"] | +9 / +1 / +4 / +12 | -3 / +1 | +6 | +86 | - | +9 / +4 / +13 | 0.02 | 0.02/1.00 | 1.00 | - | live d$ -542 dd +0 | 9.0 |
| VOL-book | vr_atr_b5_n5_bk stepv[1.25,0.5] | onQ1A/down | ["book","U7"] | +1 / +2 / +8 / +12 | -1 / +3 | +2 | +168 | - | +2 / +8 / +13 | 0.02 | 0.03/1.00 | 0.99 | - | live d$ -542 dd +0 | 8.3 |
| VOL-book | vr_ewma5_l90_bk stepv[1.5,0.5] | onQ1A/down | ["book","U7"] | +1 / +1 / +7 / +7 | -0 / +3 | +2 | +324 | - | +3 / +8 / +9 | 0.01 | 0.02/1.00 | 0.99 | - | live d$ -1202 dd +0 | 8.2 |
| VOL-book | vr_atr_b5_n5_bk stepv[1.5,0.5] | onQ1A/down | ["book","U7"] | +0 / -2 / +8 / +8 | -4 / +3 | +0 | +0 | - | +0 / +8 / +8 | 0.02 | 0.02/1.00 | 1.00 | - | live d$ -1202 dd +0 | 7.8 |
| VOL-book | vr_rv5_w6_bk stepv[1.5,0.5] | onQ1A/down | ["book","U7"] | +1 / -2 / +7 / +8 | -1 / +3 | +3 | +195 | - | +2 / +8 / +8 | 0.01 | 0.02/1.00 | 0.99 | - | live d$ -542 dd +0 | 7.7 |
| VOL-book | vr_park_w10_bk stepv[1.25,0.5] | onQ1A/down | ["book","U7"] | +3 / +1 / +8 / +10 | -2 / +3 | +4 | -90 | 35 | +3 / +7 / +10 | 0.02 | 0.02/1.00 | 1.00 | - | live d$ -542 dd +0 | 7.4 |

### VOL-pool (1056 valid cells; 649 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool | vr_atr_b1_n50_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +19 / +35 / +59 / +55 | +36 / +46 | +44 | +4391 | - | +31 / +65 / +62 | 0.52 | 0.02/0.23 | 0.84 | - | live d$ -66935 dd -6055 | 61.8 |
| VOL-pool | vr_gk_w30_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +34 / +47 / +52 / +57 | +60 / +35 | +53 | +5737 | - | +47 / +61 / +65 | 0.54 | 0.02/0.26 | 0.80 | plc400 0.005 | live d$ -51940 dd -1940 | 61.2 |
| VOL-pool | vr_gk_w10_bk stepv[1.25,0.0] | onQ1A/down | ["pool"] | +17 / +34 / +55 / +59 | +43 / +32 | +54 | +3328 | - | +28 / +61 / +64 | 0.38 | 0.02/0.26 | 0.88 | plc400 0.002 | live d$ -42505 dd +0 | 60.6 |
| VOL-pool | vr_gk_w10_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +54 / +59 / +57 / +55 | +7 / +42 | +66 | +2507 | - | +59 / +61 / +59 | 0.56 | 0.02/0.31 | 0.90 | plc400 0.002 | live d$ -63235 dd +0 | 59.4 |
| VOL-pool | vr_atr_b1_n14_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +38 / +50 / +51 / +69 | +55 / +40 | +62 | +4073 | - | +47 / +59 / +74 | 0.55 | 0.02/0.34 | 0.85 | - | live d$ -55860 dd +0 | 58.9 |
| VOL-pool | vr_park_w10_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +53 / +58 / +45 / +70 | +29 / +44 | +64 | +3219 | - | +59 / +52 / +74 | 0.56 | 0.02/0.34 | 0.87 | plc400 0.007 | live d$ -48050 dd +0 | 58.8 |

### VOL-sess (1569 valid cells; 295 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-sess | vr_gk_w10_g20 stepv[1.25,0.5] | onQ1A/down | ["sess",1] | +9 / +7 / +21 / +26 | +1 / +13 | +11 | +537 | - | +11 / +22 / +27 | 0.06 | 0.03/1.00 | 0.98 | - | live d$ -1122 dd +0 | 22.4 |
| VOL-sess | vr_park_w10_g20 stepv[1.25,0.5] | onQ1A/down | ["sess",1] | +7 / +7 / +19 / +23 | +6 / +12 | +10 | +971 | - | +10 / +22 / +26 | 0.06 | 0.02/1.00 | 0.96 | - | live d$ +5105 dd +0 | 22.2 |
| VOL-sess | vr_atr_b1_n5_g20 stepv[1.25,0.5] | onQ1A/down | ["sess",1] | +10 / +3 / +19 / +19 | +13 / +11 | +16 | +335 | - | +11 / +20 / +20 | 0.07 | 0.02/1.00 | 0.99 | - | live d$ +4960 dd +0 | 20.0 |
| VOL-sess | vr_atr_b1_n20_bk stepv[1.25,0.5] | onQ1A/down | ["sess",1] | -5 / -1 / +17 / +19 | +2 / +8 | +4 | +529 | - | -3 / +19 / +21 | 0.04 | 0.02/1.00 | 0.98 | - | live d$ -1129 dd +0 | 18.7 |
| VOL-sess | vr_park_w240_g20 stepv[1.5,0.5] | onQ1A/down | ["sess",3] | +15 / +11 / +6 / +14 | +26 / +3 | +12 | +1103 | - | +18 / +10 / +18 | 0.04 | 0.02/1.00 | 0.96 | - | live d$ -7629 dd +0 | 17.8 |
| VOL-sess | vr_atr_b1_n30_bk stepv[1.25,0.5] | onQ1A/down | ["sess",1] | -8 / -1 / +17 / +15 | -1 / +7 | +5 | +731 | - | -4 / +19 / +17 | 0.04 | 0.02/1.00 | 0.97 | - | live d$ +146 dd +0 | 17.3 |

## UP vs Q1-A variants (alone / replace / up-allowed: raise lots for some trades vs Q1-A; labelled, never promoted)

| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-P7 | vr_ewma5_l94_g20 stepv[1.1,0.0] | alone/down | ["book","P7"] | +47 / +18 / +32 / +58 | +139 / +17 | +55 | +11528 | - | +64 / +54 / +72 | 0.21 | 0.02/0.17 | 0.67 | - | live d$ -62580 dd -7246 | 64.2 |
| VOL-pool | vr_gk_w60_g20 stepv[1.25,0.0] | alone/down | ["pool"] | -36 / -10 / +48 / +42 | +77 / +19 | +18 | +13759 | - | +14 / +67 / +64 | 0.76 | 0.02/0.18 | 0.63 | - | live d$ -37078 dd -3200 | 63.6 |
| VOL-pool | vr_atr_b1_n50_g20 stepv[1.25,0.0] | alone/down | ["pool"] | -19 / +5 / +55 / +36 | +106 / +27 | +29 | +16137 | - | +30 / +73 / +62 | 0.76 | 0.02/0.23 | 0.59 | - | live d$ -44050 dd -7255 | 62.1 |
| VOL-pool | vr_park_w60_g20 stepv[1.25,0.0] | alone/down | ["pool"] | -39 / -11 / +48 / +40 | +68 / +20 | +16 | +13334 | - | +12 / +67 / +62 | 0.76 | 0.02/0.23 | 0.64 | - | live d$ -29321 dd -3200 | 62.0 |
| VOL-P7 | vr_ewma5_l94_g20 stepv[1.25,0.0] | alone/down | ["book","P7"] | +47 / +36 / +13 / +53 | +129 / +9 | +51 | +8196 | - | +61 / +36 / +65 | 0.20 | 0.02/0.26 | 0.74 | - | live d$ -44971 dd +0 | 60.9 |
| VOL-pool | vr_atr_b5_n14_g20 stepv[1.25,0.0] | alone/down | ["pool"] | -8 / +13 / +37 / +58 | +83 / +14 | +33 | +13090 | - | +31 / +60 / +73 | 0.75 | 0.02/0.28 | 0.64 | - | live d$ -58996 dd -2000 | 59.8 |
| VOL-P7 | vr_rv1_w240_g20 stepv[1.25,0.0] | alone/down | ["book","P7"] | +44 / +23 / +20 / +56 | +140 / +4 | +53 | +9160 | - | +59 / +43 / +69 | 0.19 | 0.02/0.31 | 0.72 | - | live d$ -42790 dd +0 | 59.4 |
| VOL-pool | vr_gk_w10_g20 stepv[1.25,0.0] | alone/down | ["pool"] | +33 / +46 / +38 / +47 | +49 / +23 | +54 | +11659 | - | +56 / +59 / +65 | 0.77 | 0.02/0.32 | 0.66 | - | live d$ -36404 dd +0 | 59.0 |

## Skip-share diagnostics for the finalists: is it vol timing or just trading less?
Placebos (B=200, stat = tolerant equal-mean cut): R = same lot ratios assigned to random trades anywhere (same count); G = permuted within book x session; M = the vol/ER feature shuffled within book x session x month (rule unchanged, timing broken, regime level kept). Mild twin = the same cell with multiplier 0.5 instead of 0 (n/a for ER t3 and hysteresis).

| cell | share lots cut | eq scale s | tol score | random-R mean/sd | feature-shuffle mean / p90 | p R / G / M | mild 0.5: tol, share cut, L6M d mean, cut L6M/PRE/X' |
|--|--|--|--|--|--|--|--|
| VOL-pool vr_gk_w30_g20 [1.25, 0.0] onQ1A | 0.54 | 0.80 | 61.2 | -16.1 / 33.2 | 6.1 / 35.4 | 0.005 / 0.005 / 0.005 | 32.8, 0.17, +3234, +23/+23/+40 |
| VOL-pool vr_gk_w10_bk [1.25, 0.0] onQ1A | 0.38 | 0.88 | 60.6 | -22.3 / 34.3 | -0.2 / 27.0 | 0.005 / 0.010 / 0.005 | 28.7, 0.12, +342, +14/+28/+40 |
| VOL-pool vr_gk_w10_g20 [1.25, 0.0] onQ1A | 0.56 | 0.90 | 59.4 | -12.2 / 33.3 | 4.0 / 34.8 | 0.005 / 0.010 / 0.005 | 35.7, 0.18, +2177, +29/+30/+57 |
| VOL-pool vr_park_w10_g20 [1.25, 0.0] onQ1A | 0.56 | 0.87 | 58.8 | -17.4 / 34.6 | 0.3 / 32.5 | 0.005 / 0.005 / 0.005 | 34.5, 0.18, +2500, +24/+28/+55 |
| VOL-P7 vr_rv1_w240_bk [1.25, 0.0] onQ1A | 0.08 | 0.78 | 55.6 | -4.6 / 17.3 | 4.6 / 24.6 | 0.005 / 0.005 / 0.005 | 29.5, 0.07, +3924, +20/+17/+12 |
| VOL-P7 vr_park_w60_bk [1.1, 0.0] onQ1A | 0.11 | 0.86 | 50.8 | -7.6 / 18.0 | 17.6 / 37.7 | 0.005 / 0.015 / 0.010 | 25.3, 0.10, +2721, +1/+17/+24 |
| ER-NQ-P7 er_nq_b15_n20 [0.3, 0.0, 1.0] min | 0.15 | 1.05 | 44.5 | -10.9 / 23.7 | -13.3 / 24.4 | 0.010 / 0.010 / 0.020 | 18.2, 0.05, +765, +17/+15/-4 |
| ER-NQ er_nq_b3_n10 [0.2, 0.4, 0.25, 0.5, 1.0] min | 0.17 | 0.91 | 40.8 | -3.6 / 11.8 | 10.1 / 27.4 | 0.005 / 0.005 / 0.010 | n/a |
| ER-hyst-P7 hy_b15_n20_30_40 [0.5, 0.0] min | 0.17 | 1.21 | 35.0 | -16.2 / 27.0 | -10.5 / 24.5 | 0.005 / 0.040 / 0.025 | n/a |
| RANGE rr_sofar_n20 [1.5, 0.0] onQ1A | 0.30 | 0.94 | 39.1 | -27.5 / 38.1 | -26.8 / 13.4 | 0.015 / 0.005 / 0.010 | 33.3, 0.13, +1423, +10/+29/+32 |
| RANGE-P7 rr_sofar_n20 [1.5, 0.0] onQ1A | 0.08 | 0.92 | 45.9 | -6.6 / 14.7 | -15.2 / 17.9 | 0.005 / 0.005 / 0.005 | 26.9, 0.08, +1468, +6/+22/+23 |
| ER-xinst-P7 er_min3_b15_n20 [0.35, 0.0, 1.0] min | 0.21 | 1.47 | 36.7 | -8.0 / 26.0 | -7.2 / 17.5 | 0.020 / 0.045 / 0.005 | 22.3, 0.08, +412, +21/+21/+14 |

Skip share vs equal-mean scale (VOL-pool onQ1A step cells, all multipliers): 
| share of lots cut | n cells | median s | median tolerant eq score | median L6M d mean |
|--|--|--|--|--|
| (0.0, 0.1] | 355 | 1.00 | 3.7 | +0 |
| (0.1, 0.2] | 190 | 0.98 | 23.9 | +566 |
| (0.2, 0.3] | 60 | 1.00 | 26.1 | -67 |
| (0.3, 0.4] | 71 | 0.97 | 32.3 | +909 |
| (0.4, 0.5] | 34 | 1.01 | 38.0 | -175 |
| (0.5, 0.6] | 26 | 0.91 | 53.9 | +2397 |

## Controls (same cells, tolerant equal-mean score and L6M/PRE cuts on the NOCUT and UNIF bases; first-order)
| cell | tol COMB | tol NOCUT | tol UNIF | L6M cut C/N/U | PRE cut C/N/U |
|--|--|--|--|--|--|
| RANGE rr_sofar_n20 [1.5, 0.0] onQ1A | 39.1 | 60.2 | 53.1 | +8/+41/+34 | +35/+16/+28 |
| VOL-P7 vr_rv1_w240_bk [1.25, 0.0] onQ1A | 55.6 | 56.9 | 60.1 | +43/+48/+41 | +43/+42/+44 |
| VOL-P7 vr_park_w60_bk [1.1, 0.0] onQ1A | 50.8 | 63.4 | 55.8 | -3/+37/+30 | +43/+37/+48 |
| ER-NQ-P7 er_nq_b15_n20 [0.3, 0.0, 1.0] min | 44.5 | 34.0 | 43.9 | +37/+43/+36 | +47/+29/+25 |
| VOL-pool vr_park_w10_g20 [1.25, 0.0] onQ1A | 58.8 | 64.8 | 52.4 | +53/+59/+42 | +45/+29/+47 |
| VOL-pool vr_gk_w30_g20 [1.25, 0.0] onQ1A | 61.2 | 67.8 | 72.8 | +34/+59/+47 | +52/+27/+6 |
| ER-xinst-P7 er_min3_b15_n20 [0.35, 0.0, 1.0] min | 36.7 | 48.3 | 56.3 | +47/+70/+58 | +57/+50/+44 |
| VOL-pool vr_gk_w10_g20 [1.25, 0.0] onQ1A | 59.4 | 59.5 | 52.8 | +54/+63/+47 | +57/+35/+50 |
| ER-NQ er_nq_b3_n10 [0.2, 0.4, 0.25, 0.5, 1.0] min | 40.8 | 52.5 | 56.4 | +35/+42/+46 | +20/+15/+11 |
| ER-hyst-P7 hy_b15_n20_30_40 [0.5, 0.0] min | 35.0 | 19.8 | 40.4 | +30/+55/+42 | +46/+31/+25 |
| VOL-pool vr_gk_w10_bk [1.25, 0.0] onQ1A | 60.6 | 50.1 | 62.2 | +17/+47/+26 | +55/+30/+47 |
| RANGE-P7 rr_sofar_n20 [1.5, 0.0] onQ1A | 45.9 | 58.9 | 52.3 | +8/+40/+27 | +48/+37/+35 |

Across the 400 top cells (M_AB set) the tolerant score is > 0 on NOCUT for 98 % and on UNIF for 100 %; correlation of the score COMB vs NOCUT 0.54, vs UNIF 0.43.

## Hysteresis ER (enter/exit) - 183 strictly-down cells (bars 5/15, n 10/20/30, 8 enter/exit pairs, lo 0 or 0.5, pooled and P7)
Best: ER-hyst-P7 hy_b5_n30_35_50 [0.5, 0.0] (min): equal-mean cut +22/+44/+52 % L6M/PRE/X', own p 0.03, family p 0.98. Pooled hysteresis median tolerant score 3.4 vs plain ER-NQ min-mode median 9.5: hysteresis adds no robust edge beyond P7.

## Exact-engine re-runs (VOID: the first batch used the sz_exact keying bug and was withdrawn at 17:00Z; all six sets re-queued with the fixed driver, no exact verdict yet; sz_exact.py; lead cut 2026-11-09: only the top 3 finalists = AB_F00..AB_F04 (top-5: first three finalists, best ER cell, best P7-slice cell) plus AB_F12 = mild 0.5 twin of AB_F00; months L6M, then PRE, then X-prime; <=2 workers, MemAvailable >= 55 GB; the other 9 finalists stay first-order)
no scored window yet (EmptyDataError)

Cross-check: ab_score.py vs sz_core.Z.score on 27 cells (12 finalists + top 20): max abs difference in maxDD 0.001 $, worst-20 0.002 $, cut 0.0 pp, equal-mean cut 0.0 pp, mean/d mean 0.0 after aligning the carrying-week rule (weeks > 3 -> drop the largest |cell-ref| week from MEANS only; maxDD/worst-20/Ulcer always on ALL weeks; partial edge weeks count as weeks in both).

## Live week diagnosis (frozen file, 180 trade rows, first-order): what the vol-ratio skip removes
Total week P&L of these rows $104810. Winners/losers of the week by skipped status for the first 4 finalists (vol cells):

- VOL-pool vr_gk_w30_g20 [1.25, 0.0]: skips 124 of 180 trades (69%), their P&L $51940 (wins 58 / losses 66), kept P&L $52870; skipped by book {'A7': 1500.0, 'H7': 600.0, 'K7': 13900.0, 'M7': 5800.0, 'O7': 700.0, 'P7': 28400.0, 'U7': 1100.0}; by session {'asia': 31700.0, 'london': -6800.0, 'nyam': 22900.0, 'nypm': 4100.0}; by day {'Mon 11-02': 800.0, 'Sun 11-01': 22700.0, 'Thu 11-05': 1500.0, 'Tue 11-03': 5800.0, 'Wed 11-04': 21200.0}; median ratio of skipped 1.91 vs kept 1.10.
- VOL-pool vr_park_w10_g20 [1.25, 0.0]: skips 131 of 180 trades (73%), their P&L $48050 (wins 60 / losses 71), kept P&L $56760; skipped by book {'A7': 1400.0, 'H7': 600.0, 'K7': 11500.0, 'M7': 4700.0, 'O7': 700.0, 'P7': 30800.0, 'U7': -1600.0}; by session {'asia': 31100.0, 'london': -10000.0, 'nyam': 22900.0, 'nypm': 4100.0}; by day {'Mon 11-02': -5100.0, 'Sun 11-01': 22200.0, 'Thu 11-05': 1200.0, 'Tue 11-03': 2300.0, 'Wed 11-04': 27600.0}; median ratio of skipped 1.96 vs kept 1.06.
- VOL-pool vr_gk_w10_g20 [1.25, 0.0]: skips 134 of 180 trades (74%), their P&L $63235 (wins 64 / losses 70), kept P&L $41575; skipped by book {'A7': 1900.0, 'H7': 600.0, 'K7': 11500.0, 'M7': 8300.0, 'O7': 700.0, 'P7': 38000.0, 'U7': 2300.0}; by session {'asia': 31600.0, 'london': 4700.0, 'nyam': 22900.0, 'nypm': 4100.0}; by day {'Mon 11-02': -1200.0, 'Sun 11-01': 22700.0, 'Thu 11-05': 11900.0, 'Tue 11-03': 2300.0, 'Wed 11-04': 27600.0}; median ratio of skipped 1.93 vs kept 1.06.
- VOL-pool vr_gk_w10_bk [1.25, 0.0]: skips 114 of 180 trades (63%), their P&L $45055 (wins 52 / losses 62), kept P&L $59755; skipped by book {'A7': 700.0, 'H7': 600.0, 'K7': 6500.0, 'M7': 3100.0, 'O7': 1100.0, 'P7': 30800.0, 'U7': 2300.0}; by session {'asia': 28200.0, 'london': -7600.0, 'nyam': 23400.0, 'nypm': 1100.0}; by day {'Mon 11-02': -3000.0, 'Sun 11-01': 17300.0, 'Thu 11-05': 1400.0, 'Tue 11-03': 2800.0, 'Wed 11-04': 26600.0}; median ratio of skipped 1.71 vs kept 1.02.
- VOL-P7 vr_rv1_w240_bk [1.25, 0.0]: skips 36 of 180 trades (20%), their P&L $54480 (wins 19 / losses 17), kept P&L $50330; skipped by book {'P7': 54500.0}; by session {'asia': 39900.0, 'london': -1400.0, 'nyam': 16000.0}; by day {'Mon 11-02': -600.0, 'Sun 11-01': 21600.0, 'Thu 11-05': 20400.0, 'Tue 11-03': 3300.0, 'Wed 11-04': 9700.0}; median ratio of skipped 2.02 vs kept 1.32.
- VOL-P7 vr_park_w60_bk [1.1, 0.0]: skips 45 of 180 trades (25%), their P&L $57215 (wins 23 / losses 22), kept P&L $47595; skipped by book {'P7': 57200.0}; by session {'asia': 41000.0, 'london': 200.0, 'nyam': 16000.0}; by day {'Mon 11-02': -600.0, 'Sun 11-01': 21600.0, 'Thu 11-05': 18300.0, 'Tue 11-03': 3300.0, 'Wed 11-04': 14500.0}; median ratio of skipped 1.71 vs kept 1.38.

Week-level context: median vol ratio of all live signals 1.63 (20-day norm = 1.0); 69 % of live signals sit above 1.25.
Plain reading: this was a high-vol expansion week. Most live signals were above the 1.25x threshold, so the pooled vol-skip cells skip 63-74 %% of the week and remove about half of its P&L ($45-63k of $104.8k); the skipped set is not only winners (about 58 wins / 66 losses for the first cell) but it carries the large P7 Asia/NY-AM winners of Sunday 11-01 and Wednesday 11-04. A vol-ratio skip would therefore have skipped the winners of a high-vol week: the rule is a drawdown filter that gives up upside in expansion tape, which is exactly the mean cost shown in the equal-mean and live-week columns. The week has no losing day, so it cannot show the drawdown benefit. P7-only cells (20-25 %% of signals) lose $54-57k because P7 is the week driver.

## Dominance and frontier
- Cells dominating Q1-A on both mean and maxDD (down-only, L6M and HOLD d mean >= 0, tolerant equal-lots cut > 0): 3471 of 34622 (first-order means overstate; most are skip filters).
- Cells trading mean for DD: median $ weekly mean lost per $1k of maxDD cut (L6M, cells with d mean < 0 and cut > 0): 187.
- Caveats: skip cells change which trades exist, so exact re-runs (locks, re-entries, state-cut arm sizes via sqrt(lots)) will move numbers; ES/RTY ER and VIX exist only to 2026-10-16 (later signals fall back to Q1-A); the 10 v1.5 bug exits of the 11-08/09 night are not in the S1b base; live week = frozen file (180 rows), first-order.