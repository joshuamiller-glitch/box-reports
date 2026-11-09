# SZ_AB - T-SIZER-EXHAUST families A (ER) and B (volatility-target) + K (P7) slice  (refreshed 2026-11-09 16:58Z)
**FIRST-ORDER SCREEN ONLY unless a row says EXACT (exact-engine rows are in the exact section, top-5 + mild twin only). Label: base S1b-COMB (live D7 v1.5 state cut), FIRST-ORDER trade-level scoring (pnl per planned lot x new lots; first-order mean is not reliable, drawdown ranking is usable), in-sample, PRE-PROOF, post-hoc, Shadow only, no PASS claims. Windows as of 2026-11-09; carrying week (largest |cell - Q1-A| weekly delta) dropped from means; maxDD/worst-20/Ulcer on all weeks.**
Prereg: autopilot/SZ_AB_PREREG.md (sha in DECISIONS.md). Ledger /mnt/l2/l2vast/_th_sz/ledger_AB.parquet (copy at _th_sz/ab/ledger_AB.parquet; 63914 cells, 34625 down-only equal-mean valid). J-pair multipliers /mnt/l2/l2vast/_th_sz/M_AB.npz (new lots / base lots, 21135 trades in C.prepare(load_trades(S1B-COMB)) order).

Objectives: (a) equal lots - maxDD cut vs Q1-A (+ = shallower); (b) equal mean - lots of the cell scaled by one global factor s (column eq scale) so L6M mean = Q1-A, then maxDD cut (valid only for 0 < s <= 2; cells needing s > 2 are excluded from ranking). Tolerant eq score = second-smallest of the equal-mean cuts over L6M/PRE/X' (tolerant on one window). worst-20 ok = equal-mean worst-20 not worse than -5%.

## Reference rows (weekly mean / maxDD, USD, first-order, S1b-COMB)
| ref | L6M mean / maxDD | HOLD | PRE | X' |
|--|--|--|--|--|
| Q1-A (ER<.30 x0.5) | +22996 / 79907 | +15522 / 99496 | +14777 / 140288 | +2181 / 116941 |
| sizer off (x1) | +30122 / 108038 | +20265 / 134892 | +16662 / 151592 | +656 / 203191 |
| old ladder (x.5/x1.5) | +27181 / 116699 | +20273 / 130207 | +19241 / 207515 | +742 / 120096 |

**VOID NOTICE (17:00Z): the first exact rows for AB_F00/F01/F02/F12 (L6M cut +10.4 / +4.4 / +19.1 / +2.0 %) are VOID: sz_exact.py keyed the multiplier table on the arm second, not the signal second (SZ-CORE defect). The reading that first-order cuts are overstated 2-5x is WITHDRAWN. All six exact sets were re-queued from scratch with the fixed driver; there is no exact verdict yet and every number here is FIRST-ORDER SCREEN ONLY.**

## ADDENDUM 1 - results move with the base (FIRST-ORDER SCREEN ONLY)
**Testing-defect check: 0 of 400 cells have an L6M maxDD identical to the dollar on OLD-BASE and S1b-COMB: none, so no cached-list defect. Score correlation new vs old (Pearson 0.32, Spearman 0.24) shows the sizing answer moves with the base.** First-order pnl-per-lot scaling cannot see exits by construction; the base dependence seen here comes only from which trades the base produces. The exact runs below are the verdict.

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
| VOL-pool vr_gk_w30_g20 [1.25, 0.0] onQ1A | 62.0 | 56.7 | +5.3 | +34/+69 | +52/+48 | 1 -> 12 |
| VOL-pool vr_park_w10_g20 [1.25, 0.0] onQ1A | 59.3 | 43.6 | +15.7 | +53/+51 | +49/+57 | 2 -> 77 |
| VOL-pool vr_gk_w10_g20 [1.25, 0.0] onQ1A | 59.0 | 65.1 | -6.1 | +54/+62 | +58/+56 | 3 -> 1 |
| VOL-pool vr_gk_w10_bk [1.25, 0.0] onQ1A | 59.0 | 63.1 | -4.1 | +17/+58 | +53/+57 | 4 -> 3 |
| VOL-P7 vr_rv1_w240_bk [1.25, 0.0] onQ1A | 54.7 | 52.6 | +2.1 | +43/+41 | +43/+54 | 16 -> 26 |
| VOL-P7 vr_park_w60_bk [1.1, 0.0] onQ1A | 50.1 | 42.3 | +7.8 | -3/+39 | +43/+32 | 27 -> 88 |
| ER-NQ er_nq_b3_n10 [0.2, 0.4, 0.25, 0.5, 1.0] min | 41.3 | 10.3 | +31.0 | +35/+49 | +20/+7 | 82 -> 377 |
| ER-NQ-P7 er_nq_b15_n20 [0.3, 0.0, 1.0] min | 41.2 | 43.3 | -2.0 | +37/+32 | +47/+47 | 83 -> 82 |
| ER-hyst-P7 hy_b15_n20_30_40 [0.5, 0.0] min | 35.2 | 44.8 | -9.6 | +30/+37 | +46/+49 | 168 -> 71 |
| RANGE rr_sofar_n20 [1.5, 0.0] onQ1A | 31.5 | 35.1 | -3.5 | +8/+48 | +50/+45 | 299 -> 173 |
| RANGE-P7 rr_sofar_n20 [1.5, 0.0] onQ1A | 39.0 | 48.6 | -9.6 | +8/+40 | +48/+54 | 105 -> 47 |
| ER-xinst-P7 er_min3_b15_n20 [0.35, 0.0, 1.0] min | 35.9 | 39.0 | -3.1 | +47/+66 | +57/+57 | 149 -> 121 |

## Plain sentences

- **Vol-target (pooled, B), stacked on Q1-A:** the best DD-first cell is "skip the signal when short-horizon range vol is more than 1.25x its 20-day norm" (vr_gk_w30_g20 onQ1A [1.25, 0.0]): equal-mean maxDD cut +48/+62/+64 % on L6M/PRE/X' (equal lots +34/+52/+54 %), with L6M d mean +6308 $/wk at equal lots and skipping 54 % of signals; own placebo p 0.02, family p 0.15 (whole-set max-stat: only 0 of 34625 down-only cells reach family p <= .10); for context the "alone" variants (ER sizer also dropped) reach tolerant scores near 67 but skip 76 % of signals; the held-out live week would have changed by -51940 of the week's $104.8k. Graded step cells beat the continuous (ref/now)^p ones. It fails OOS as a picked procedure: walk-forward over the vol-target family cuts maxDD 29 % at equal lots but -10 % at equal mean (mean -5832 $/wk).
- **ER family (pooled NQ ER, A):** the best cell (er_nq_b3_n10 t3 [0.2, 0.4, 0.25, 0.5, 1.0] min) cuts equal-mean maxDD +41/+27/+50 % (L6M/PRE/X'), own p 0.02 but family p 1.00; the walk-forward of the ER picking procedure gives OOS maxDD 13 % at equal lots and -63 % at equal mean: the ER grid is selection noise around Q1-A once the pick has to be made in advance. Cells beating Q1-A on both mean and maxDD (L6M and HOLD d mean >= 0, tolerant cut > 0) exist (115 down-only), but none holds the family null.
- **ER of ES/RTY/max/min and ER at session open:** best er_max2_b15_n20 t3 [0.35, 0.55, 0.25, 0.5, 1.0] (min): equal-mean cut +40/+36/-8 % L6M/PRE/X', own p 0.02 / family p 1.00, live d$ -45448. Cross-instrument and session-open ER do not beat the NQ-only ER on the tolerant score (best 37 vs 41).
- **Range ratios (B02 generalised, so-far / premarket / first-30):** best rr_sofar_n20 stepv [1.5, 0.0] (onQ1A): equal-mean cut -14/+39/+32 % L6M/PRE/X', own p 0.02 / family p 1.00, live d$ -69300. 
- **VIX level / change (owned to 2026-10-16 only):** best vix_chg1 stepv [0.1, 0.0] (onQ1A): equal-mean cut +5/+36/+37 % L6M/PRE/X', own p 0.02 / family p 1.00, live d$ +0. 
- **Per-book / per-session thresholds:** the best (er_nq_b60_n20 t2 [0.45, 0.0, 1.0], scope ["sess", 1]) cuts equal-mean maxDD +41/+53/-6 %; the per-book and per-session cells that win do it by skipping (lot 0) in one window and are negative in another (X' or PRE), i.e. weaker than pooled cells; own-draw p of the group is mostly > .10 (see ledger).
- **P7 (K slice):** P7 alone the best volatility cell (vr_rv1_w240_bk stepv [1.25, 0.0] onQ1A) skips only 8 % of all signals (P7 trades) and cuts stack equal-mean maxDD +55/+55/+47 % with P7-alone tolerant score +52; ER cells on P7 alone give up to 41 % tolerant. WF over the P7 slice: OOS cut 28 % equal lots / 9 % equal mean. Live week (a P7-heavy week) would have lost -54480.

## Walk-forward of the picking procedure (monthly 2024-01..2026-10, 26 trailing weeks, 8-day purge; pick = largest trailing equal-mean maxDD cut among the set; OOS in 5-business-day blocks, approximate weeks)
| set | OOS cut equal lots % | OOS cut equal mean % | OOS d mean $/wk | ref OOS maxDD |
|--|--|--|--|--|
| ALL | -1.9 | -80.5 | -7220 | 140288 |
| A | -1.9 | -112.9 | -8645 | 140288 |
| B | +29.0 | -9.5 | -5832 | 140288 |
| ER-NQ pooled | +13.2 | -62.6 | -7721 | 140288 |
| VOL-pool | +40.9 | +17.9 | -4642 | 140288 |
| P7 (K slice) | +28.3 | +9.2 | -3482 | 140288 |

## Finalists (FIRST-ORDER SCREEN ONLY; <= 12; ids in /mnt/l2/l2vast/_th_sz/ab/finalists.json; down-only, worst-20 ok, own p <= .10; placebo B=400 within book x session lot-ratio permutations)

| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool | vr_gk_w30_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +34 / +47 / +52 / +54 | +62 / +35 | +52 | +6308 | - | +48 / +62 / +64 | 0.54 | 0.02/0.15 | 0.79 | plc400 0.005 | live d$ -51940 dd -1940 | 62.0 |
| VOL-pool | vr_park_w10_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +53 / +58 / +49 / +67 | +35 / +44 | +64 | +3560 | - | +59 / +56 / +71 | 0.56 | 0.02/0.28 | 0.86 | plc400 0.005 | live d$ -48050 dd +0 | 59.3 |
| VOL-pool | vr_gk_w10_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +54 / +59 / +58 / +55 | +7 / +43 | +66 | +2243 | - | +58 / +62 / +59 | 0.56 | 0.02/0.28 | 0.91 | plc400 0.002 | live d$ -63235 dd +0 | 59.0 |
| VOL-pool | vr_gk_w10_bk stepv[1.25,0.0] | onQ1A/down | ["pool"] | +17 / +34 / +53 / +55 | +42 / +32 | +53 | +3305 | - | +28 / +59 / +61 | 0.38 | 0.02/0.28 | 0.88 | plc400 0.002 | live d$ -45055 dd +0 | 59.0 |
| VOL-P7 | vr_rv1_w240_bk stepv[1.25,0.0] | onQ1A/down | ["book","P7"] | +43 / +31 / +43 / +33 | +83 / +20 | +52 | +5929 | - | +55 / +55 / +47 | 0.08 | 0.02/0.49 | 0.79 | plc400 0.002 | live d$ -54480 dd +0 | 54.7 |
| VOL-P7 | vr_park_w60_bk stepv[1.1,0.0] | onQ1A/down | ["book","P7"] | -3 / +17 / +43 / +42 | +39 / +26 | +27 | +3939 | - | +12 / +51 / +50 | 0.11 | 0.02/0.83 | 0.86 | plc400 0.010 | live d$ -57215 dd +0 | 50.1 |
| ER-NQ | er_nq_b3_n10 t3[0.2,0.4,0.25,0.5,1.0] | min/down | ["pool"] | +35 / +11 / +20 / +45 | +57 / +18 | +42 | +2179 | - | +41 / +27 / +50 | 0.17 | 0.02/1.00 | 0.91 | plc400 0.002 | live d$ -29212 dd +0 | 41.3 |
| ER-NQ-P7 | er_nq_b15_n20 t2[0.3,0.0,1.0] | min/down | ["book","P7"] | +37 / -23 / +47 / +44 | +4 / +25 | +45 | -1081 | 37 | +34 / +45 / +41 | 0.15 | 0.02/1.00 | 1.05 | plc400 0.010 | live d$ -36915 dd -6905 | 41.2 |
| ER-hyst-P7 | hy_b15_n20_30_40 stepv[0.5,0.0] | min/down | ["book","P7"] | +30 / -52 / +46 / +49 | -12 / +37 | +50 | -3842 | 160 | +16 / +35 / +39 | 0.17 | 0.05/1.00 | 1.21 | plc400 0.030 | live d$ -50125 dd -6905 | 35.2 |
| RANGE | rr_sofar_n20 stepv[1.5,0.0] | onQ1A/down | ["pool"] | +8 / -15 / +50 / +45 | +12 / +34 | +23 | -5255 | 809 | -14 / +39 / +32 | 0.29 | 0.02/1.00 | 1.24 | plc400 0.010 | live d$ -69300 dd -8855 | 31.5 |
| RANGE-P7 | rr_sofar_n20 stepv[1.5,0.0] | onQ1A/down | ["book","P7"] | +8 / -1 / +48 / +35 | +14 / +27 | +19 | +1562 | - | +14 / +51 / +39 | 0.08 | 0.02/1.00 | 0.94 | plc400 0.010 | live d$ -47815 dd +0 | 39.0 |
| ER-xinst-P7 | er_min3_b15_n20 t2[0.35,0.0,1.0] | min/down | ["book","P7"] | +47 / -11 / +57 / +58 | -29 / +43 | +58 | -7407 | 195 | +22 / +36 / +37 | 0.21 | 0.03/1.00 | 1.49 | plc400 0.040 | live d$ -63305 dd -6905 | 35.9 |

## Ranked family tables (FIRST-ORDER SCREEN ONLY; top 6 per sub-family by tolerant equal-mean score; down-only; worst-20 ok; family p = max-stat over all 63914 cells, B=64 common permutations, own p B=64)

### ER-NQ (1917 valid cells; 1045 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ | er_nq_b3_n10 t3[0.2,0.4,0.25,0.5,1.0] | min/down | ["pool"] | +35 / +11 / +20 / +45 | +57 / +18 | +42 | +2179 | - | +41 / +27 / +50 | 0.17 | 0.02/1.00 | 0.91 | plc400 0.002 | live d$ -29212 dd +0 | 41.3 |
| ER-NQ | er_nq_b15_n14 t2[0.35,0.0,1.0] | min/down | ["pool"] | +54 / +38 / +58 / +43 | -7 / +37 | +58 | -6053 | 141 | +40 / +45 / +26 | 0.61 | 0.02/1.00 | 1.30 | - | live d$ -46430 dd +0 | 40.2 |
| ER-NQ | er_nq_b3_n30 t3[0.35,0.55,0.25,0.5,1.0] | min/down | ["pool"] | +40 / +43 / +64 / +60 | -27 / +44 | +50 | -7461 | 234 | +8 / +45 / +39 | 0.37 | 0.02/1.00 | 1.54 | - | live d$ -46816 dd +0 | 38.9 |
| ER-NQ | er_nq_b3_n14 t3[0.35,0.55,0.25,0.5,1.0] | min/down | ["pool"] | +43 / +26 / +37 / +47 | +34 / +27 | +53 | -1910 | 56 | +37 / +31 / +42 | 0.28 | 0.02/1.00 | 1.10 | - | live d$ -50536 dd +0 | 37.5 |
| ER-NQ | er_nq_b5_n30 t3[0.2,0.4,0.25,0.5,1.0] | min/down | ["pool"] | +45 / +13 / +35 / +53 | -4 / +25 | +50 | -3288 | 92 | +36 / +24 / +45 | 0.27 | 0.02/1.00 | 1.17 | - | live d$ -17334 dd +0 | 35.5 |
| ER-NQ | er_nq_b3_n20 t3[0.35,0.55,0.25,0.5,1.0] | min/down | ["pool"] | +46 / +39 / +50 / +47 | +13 / +33 | +52 | -4023 | 109 | +34 / +39 / +35 | 0.32 | 0.03/1.00 | 1.22 | - | live d$ -52048 dd +0 | 35.5 |

### ER-NQ-P7 (2365 valid cells; 1397 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ-P7 | er_nq_b15_n20 t2[0.3,0.0,1.0] | min/down | ["book","P7"] | +37 / -23 / +47 / +44 | +4 / +25 | +45 | -1081 | 37 | +34 / +45 / +41 | 0.15 | 0.02/1.00 | 1.05 | plc400 0.010 | live d$ -36915 dd -6905 | 41.2 |
| ER-NQ-P7 | er_nq_b15_n14 t2[0.35,0.0,1.0] | min/down | ["book","P7"] | +36 / +20 / +45 / +27 | +19 / +26 | +48 | +2030 | - | +41 / +50 / +33 | 0.15 | 0.02/1.00 | 0.92 | - | live d$ -30145 dd +0 | 41.1 |
| ER-NQ-P7 | er_nq_b30_n10 t2[0.5,0.0,1.0] | min/down | ["book","P7"] | +44 / -3 / +35 / +50 | +1 / +27 | +50 | -2007 | 57 | +38 / +28 / +45 | 0.17 | 0.05/1.00 | 1.10 | - | live d$ -63395 dd -6905 | 38.3 |
| ER-NQ-P7 | er_nq_b1_n14 t2[0.55,0.0,1.0] | min/down | ["book","P7"] | +48 / +30 / +66 / +67 | -42 / +58 | +53 | -9912 | 261 | +2 / +37 / +38 | 0.24 | 0.06/1.00 | 1.87 | - | live d$ -90220 dd -4500 | 37.2 |
| ER-NQ-P7 | er_nq_b15_n20 t2[0.35,0.0,1.0] | min/down | ["book","P7"] | +50 / -20 / +43 / +42 | -2 / +32 | +59 | -2256 | 56 | +45 / +36 / +36 | 0.17 | 0.02/1.00 | 1.11 | - | live d$ -63305 dd -6905 | 36.4 |
| ER-NQ-P7 | er_nq_b3_n10 t3[0.2,0.4,0.25,0.5,1.0] | min/down | ["book","P7"] | +31 / +10 / +13 / +33 | +39 / +15 | +35 | +1318 | - | +35 / +18 / +37 | 0.11 | 0.02/1.00 | 0.94 | - | live d$ -26300 dd +0 | 35.2 |

### ER-NQ-book (4084 valid cells; 533 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ-book | er_nq_b15_n45 t2[0.1,0.0,1.0] | min/down | ["book","K7"] | +20 / +9 / -4 / +24 | +16 / -0 | +21 | +1487 | - | +25 / +3 / +29 | 0.11 | 0.02/1.00 | 0.94 | - | live d$ -490 dd +0 | 24.8 |
| ER-NQ-book | er_nq_b15_n45 t2[0.15,0.0,1.0] | min/down | ["book","K7"] | +16 / +7 / -8 / +21 | +11 / +1 | +16 | +993 | - | +20 / -3 / +25 | 0.16 | 0.02/1.00 | 0.96 | - | live d$ -330 dd +0 | 19.6 |
| ER-NQ-book | er_nq_b60_n10 t2[0.5,0.0,1.0] | min/down | ["book","M7"] | +14 / +13 / +13 / -22 | +18 / +9 | +17 | +1262 | - | +19 / +18 / -16 | 0.15 | 0.05/1.00 | 0.95 | - | live d$ -2415 dd +0 | 17.5 |
| ER-NQ-book | er_nq_b60_n45 t2[0.25,0.0,1.0] | min/down | ["book","M7"] | +18 / +6 / +11 / -28 | +51 / +7 | +24 | +1782 | - | +23 / +16 / -20 | 0.15 | 0.06/1.00 | 0.94 | - | live d$ -12275 dd +0 | 16.5 |
| ER-NQ-book | er_nq_b15_n45 t2[0.5,0.0,1.0] | min/down | ["book","M7"] | +14 / +16 / +15 / -27 | +31 / +10 | +21 | +339 | - | +15 / +16 / -26 | 0.21 | 0.26/1.00 | 0.99 | - | live d$ -8435 dd +0 | 15.3 |
| ER-NQ-book | er_nq_b60_n45 t2[0.15,0.0,1.0] | min/down | ["book","M7"] | +19 / +6 / +11 / -12 | +33 / +5 | +16 | +1398 | - | +23 / +15 / -6 | 0.10 | 0.02/1.00 | 0.95 | - | live d$ -6275 dd +0 | 15.0 |

### ER-NQ-bxs (4391 valid cells; 79 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ-bxs | er_nq_b15_n20 t2[0.5,0.0,1.0] | min/down | ["bxs","P7",1] | +34 / -62 / +51 / -24 | +22 / +29 | +38 | +2148 | - | +39 / +55 / -14 | 0.07 | 0.03/1.00 | 0.92 | - | live d$ -1690 dd +0 | 39.0 |
| ER-NQ-bxs | er_nq_b15_n20 t2[0.45,0.0,1.0] | min/down | ["bxs","P7",1] | +31 / -70 / +47 / -35 | +21 / +29 | +33 | +2472 | - | +37 / +52 / -22 | 0.06 | 0.03/1.00 | 0.91 | - | live d$ -1690 dd +0 | 37.5 |
| ER-NQ-bxs | er_nq_b5_n20 t2[0.45,0.0,1.0] | replace/down | ["bxs","P7",1] | +27 / -64 / +38 / -8 | +6 / +23 | +29 | +1648 | - | +32 / +42 / -1 | 0.07 | 0.14/1.00 | 0.94 | - | live d$ -385 dd +0 | 31.8 |
| ER-NQ-bxs | er_nq_b5_n20 t2[0.45,0.0,1.0] | min/down | ["bxs","P7",1] | +27 / -64 / +38 / -8 | +6 / +23 | +29 | +1648 | - | +32 / +42 / -1 | 0.07 | 0.14/1.00 | 0.94 | - | live d$ -385 dd +0 | 31.8 |
| ER-NQ-bxs | er_nq_b15_n20 t2[0.4,0.0,1.0] | min/down | ["bxs","P7",1] | +29 / -63 / +44 / -26 | +21 / +26 | +32 | +258 | - | +30 / +45 / -24 | 0.06 | 0.17/1.00 | 0.99 | - | live d$ -1690 dd +0 | 29.7 |
| ER-NQ-bxs | er_nq_b15_n20 t2[0.35,0.0,1.0] | min/down | ["bxs","P7",1] | +18 / -79 / +41 / -42 | +19 / +22 | +31 | +3441 | - | +28 / +49 / -24 | 0.05 | 0.14/1.00 | 0.87 | - | live d$ -1690 dd +0 | 28.0 |

### ER-NQ-sess (5285 valid cells; 565 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ-sess | er_nq_b60_n20 t2[0.45,0.0,1.0] | min/down | ["sess",1] | +35 / -53 / +48 / -17 | +6 / +30 | +39 | +2270 | - | +41 / +53 / -6 | 0.26 | 0.05/1.00 | 0.90 | - | live d$ -3845 dd +0 | 41.3 |
| ER-NQ-sess | er_nq_b15_n10 t2[0.5,0.0,1.0] | min/down | ["sess",1] | +36 / -57 / +53 / -24 | +6 / +27 | +46 | +1233 | - | +40 / +56 / -17 | 0.23 | 0.02/1.00 | 0.95 | - | live d$ -1120 dd +0 | 39.9 |
| ER-NQ-sess | er_nq_b15_n20 t3[0.3,0.5,0.25,0.5,1.0] | min/down | ["sess",1] | +31 / -56 / +42 / -18 | +29 / +19 | +37 | +2471 | - | +37 / +47 / -7 | 0.12 | 0.02/1.00 | 0.91 | - | live d$ +2366 dd +0 | 37.3 |
| ER-NQ-sess | er_nq_b15_n45 t2[0.15,0.0,1.0] | min/down | ["sess",1] | +19 / -7 / +47 / +30 | +49 / +28 | +32 | +2790 | - | +28 / +53 / +37 | 0.16 | 0.05/1.00 | 0.89 | - | live d$ +3000 dd +0 | 37.2 |
| ER-NQ-sess | er_nq_b15_n10 t2[0.55,0.0,1.0] | min/down | ["sess",1] | +38 / -55 / +54 / -7 | +26 / +27 | +49 | -598 | 19 | +37 / +52 / -10 | 0.25 | 0.15/1.00 | 1.03 | - | live d$ -1585 dd +0 | 36.9 |
| ER-NQ-sess | er_nq_b15_n45 t2[0.35,0.0,1.0] | min/down | ["sess",1] | +35 / -73 / +60 / -25 | +29 / +30 | +44 | +533 | - | +36 / +61 / -22 | 0.29 | 0.15/1.00 | 0.98 | - | live d$ -10590 dd +0 | 36.3 |

### ER-hyst (49 valid cells; 27 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-hyst | hy_b5_n30_35_50 stepv[0.5,0.5] | min/down | ["pool"] | +13 / +9 / +31 / +29 | +9 / +22 | +30 | -1030 | 96 | +9 / +28 / +26 | 0.18 | 0.02/1.00 | 1.05 | - | live d$ -4748 dd +0 | 26.0 |
| ER-hyst | hy_b15_n30_30_45 stepv[0.5,0.5] | min/down | ["pool"] | +28 / +18 / +33 / +13 | +7 / +25 | +34 | -1969 | 87 | +21 / +26 / +4 | 0.19 | 0.02/1.00 | 1.10 | - | live d$ -18544 dd +0 | 21.0 |
| ER-hyst | hy_b15_n30_35_50 stepv[0.5,0.5] | min/down | ["pool"] | +28 / +18 / +37 / +15 | -2 / +25 | +33 | -2482 | 110 | +19 / +29 / +4 | 0.20 | 0.02/1.00 | 1.13 | - | live d$ -23348 dd +0 | 18.8 |
| ER-hyst | hy_b15_n30_30_40 stepv[0.5,0.5] | min/down | ["pool"] | +26 / +18 / +31 / +8 | +3 / +21 | +35 | -2071 | 98 | +18 / +24 / -2 | 0.18 | 0.03/1.00 | 1.11 | - | live d$ -17183 dd +0 | 18.5 |
| ER-hyst | hy_b15_n20_20_30 stepv[0.5,0.5] | min/down | ["pool"] | +20 / -16 / +25 / +2 | +9 / +17 | +22 | -392 | 25 | +18 / +24 / -0 | 0.10 | 0.02/1.00 | 1.02 | - | live d$ -12596 dd +0 | 18.0 |
| ER-hyst | hy_b15_n10_30_45 stepv[0.5,0.5] | min/down | ["pool"] | +11 / +13 / +19 / +20 | +9 / +14 | +15 | -381 | 45 | +9 / +18 / +18 | 0.08 | 0.02/1.00 | 1.02 | - | live d$ -567 dd +0 | 17.9 |

### ER-hyst-P7 (54 valid cells; 41 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-hyst-P7 | hy_b15_n20_30_40 stepv[0.5,0.0] | min/down | ["book","P7"] | +30 / -52 / +46 / +49 | -12 / +37 | +50 | -3842 | 160 | +16 / +35 / +39 | 0.17 | 0.05/1.00 | 1.21 | plc400 0.030 | live d$ -50125 dd -6905 | 35.2 |
| ER-hyst-P7 | hy_b5_n30_35_50 stepv[0.5,0.5] | min/down | ["book","P7"] | +21 / +10 / +20 / +16 | +24 / +15 | +28 | +780 | - | +24 / +23 / +19 | 0.08 | 0.03/1.00 | 0.97 | - | live d$ -8075 dd +0 | 23.0 |
| ER-hyst-P7 | hy_b15_n30_35_50 stepv[0.5,0.5] | min/down | ["book","P7"] | +26 / +12 / +22 / +1 | +21 / +18 | +29 | -365 | 18 | +24 / +21 / -1 | 0.09 | 0.02/1.00 | 1.02 | - | live d$ -23641 dd +0 | 21.0 |
| ER-hyst-P7 | hy_b15_n30_30_45 stepv[0.5,0.5] | min/down | ["book","P7"] | +26 / +12 / +21 / -3 | +24 / +18 | +29 | -128 | 6 | +25 / +20 / -4 | 0.08 | 0.02/1.00 | 1.01 | - | live d$ -20035 dd +0 | 20.1 |
| ER-hyst-P7 | hy_b5_n30_30_45 stepv[0.5,0.5] | min/down | ["book","P7"] | +23 / +3 / +16 / +2 | +25 / +10 | +30 | +976 | - | +26 / +20 / +6 | 0.06 | 0.03/1.00 | 0.96 | - | live d$ -6196 dd +0 | 19.6 |
| ER-hyst-P7 | hy_b15_n30_25_40 stepv[0.5,0.5] | min/down | ["book","P7"] | +24 / +12 / +20 / +0 | +25 / +14 | +27 | -13 | 1 | +24 / +20 / +0 | 0.07 | 0.02/1.00 | 1.00 | - | live d$ -18674 dd +0 | 19.5 |

### ER-open (210 valid cells; 151 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-open | er_nq_b5_n20_open t3[0.25,0.45,0.5,0.75,1.0] | min/down | ["pool"] | +13 / +19 / +32 / +31 | +14 / +18 | +21 | -1503 | 144 | +6 / +27 / +26 | 0.16 | 0.02/1.00 | 1.08 | - | live d$ -17058 dd +0 | 26.1 |
| ER-open | er_nq_b5_n20_open t2[0.5,0.5,1.0] | min/down | ["pool"] | +23 / +22 / +33 / +32 | +12 / +22 | +33 | -1779 | 98 | +16 / +27 / +26 | 0.20 | 0.02/1.00 | 1.09 | - | live d$ -25321 dd +0 | 25.7 |
| ER-open | er_nq_b5_n10_open t2[0.3,0.5,1.0] | min/down | ["pool"] | +29 / +9 / +22 / +27 | +19 / +17 | +32 | -705 | 31 | +26 / +19 / +25 | 0.12 | 0.02/1.00 | 1.03 | - | live d$ -19664 dd +0 | 24.7 |
| ER-open | er_nq_b5_n30_open t2[0.35,0.5,1.0] | min/down | ["pool"] | +21 / +22 / +32 / +29 | +16 / +20 | +26 | -1384 | 84 | +15 / +27 / +25 | 0.19 | 0.02/1.00 | 1.07 | - | live d$ -10905 dd +0 | 24.6 |
| ER-open | er_nq_b5_n20_open cont[0.6,0.5,1.0] | min/down | ["pool"] | +20 / +21 / +35 / +32 | +5 / +22 | +28 | -2305 | 142 | +11 / +27 / +24 | 0.20 | 0.02/1.00 | 1.12 | - | live d$ -21718 dd +0 | 24.0 |
| ER-open | er_nq_b5_n10_open t2[0.25,0.5,1.0] | min/down | ["pool"] | +25 / -2 / +25 / +15 | +23 / +15 | +27 | -257 | 13 | +24 / +24 / +14 | 0.10 | 0.02/1.00 | 1.01 | - | live d$ -19664 dd +0 | 23.9 |

### ER-xinst (1640 valid cells; 606 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-xinst | er_max2_b15_n20 t3[0.35,0.55,0.25,0.5,1.0] | min/down | ["pool"] | +52 / +2 / +49 / +14 | -4 / +33 | +58 | -4294 | 104 | +40 / +36 / -8 | 0.31 | 0.02/1.00 | 1.25 | - | live d$ -45448 dd +0 | 35.9 |
| ER-xinst | er_max2_b15_n20 t3[0.35,0.45,0.25,0.5,1.0] | min/down | ["pool"] | +42 / -11 / +47 / +11 | +7 / +30 | +56 | -2566 | 76 | +35 / +40 / -0 | 0.28 | 0.02/1.00 | 1.12 | - | live d$ -38084 dd +0 | 35.0 |
| ER-xinst | er_max3_b15_n20 t3[0.35,0.55,0.25,0.5,1.0] | min/down | ["pool"] | +52 / -13 / +46 / +14 | -5 / +32 | +58 | -3965 | 96 | +41 / +34 / -6 | 0.29 | 0.02/1.00 | 1.23 | - | live d$ -45448 dd +0 | 33.9 |
| ER-xinst | er_mean3_b15_n20 t3[0.3,0.5,0.25,0.5,1.0] | min/down | ["pool"] | +52 / -19 / +50 / +6 | -4 / +37 | +55 | -5224 | 125 | +37 / +34 / -25 | 0.32 | 0.02/1.00 | 1.32 | - | live d$ -34051 dd +0 | 33.8 |
| ER-xinst | er_max3_b5_n30 t3[0.2,0.4,0.25,0.5,1.0] | min/down | ["pool"] | +44 / +3 / +40 / +36 | +7 / +28 | +47 | -2101 | 60 | +38 / +34 / +30 | 0.22 | 0.02/1.00 | 1.10 | - | live d$ -17334 dd +0 | 33.6 |
| ER-xinst | er_max2_b15_n20 t3[0.3,0.4,0.25,0.5,1.0] | min/down | ["pool"] | +38 / -18 / +46 / +11 | +6 / +28 | +49 | -1577 | 52 | +34 / +43 / +4 | 0.25 | 0.02/1.00 | 1.07 | - | live d$ -27434 dd +0 | 33.6 |

### ER-xinst-P7 (714 valid cells; 285 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-xinst-P7 | er_min3_b15_n20 t2[0.35,0.0,1.0] | min/down | ["book","P7"] | +47 / -11 / +57 / +58 | -29 / +43 | +58 | -7407 | 195 | +22 / +36 / +37 | 0.21 | 0.03/1.00 | 1.49 | plc400 0.040 | live d$ -63305 dd -6905 | 35.9 |
| ER-xinst-P7 | er_mean3_b15_n20 t2[0.5,0.0,1.0] | min/down | ["book","P7"] | +57 / -8 / +64 / +49 | -34 / +52 | +61 | -7584 | 166 | +35 / +45 / +23 | 0.22 | 0.02/1.00 | 1.51 | - | live d$ -77290 dd -4500 | 35.5 |
| ER-xinst-P7 | er_max3_b15_n20 t2[0.4,0.0,1.0] | min/down | ["book","P7"] | +14 / -46 / +41 / +45 | -0 / +31 | +34 | -2184 | 196 | +5 / +35 / +39 | 0.16 | 0.06/1.00 | 1.11 | - | live d$ -63305 dd -6905 | 35.0 |
| ER-xinst-P7 | er_max2_b15_n20 t2[0.4,0.0,1.0] | min/down | ["book","P7"] | +24 / -23 / +49 / +41 | +7 / +34 | +45 | -2261 | 119 | +15 / +43 / +34 | 0.17 | 0.08/1.00 | 1.11 | - | live d$ -63305 dd -6905 | 34.2 |
| ER-xinst-P7 | er_max3_b15_n20 t2[0.35,0.0,1.0] | min/down | ["book","P7"] | +34 / -41 / +42 / +29 | -2 / +25 | +47 | -33 | 1 | +34 / +42 / +28 | 0.14 | 0.06/1.00 | 1.00 | - | live d$ -63305 dd -6905 | 34.1 |
| ER-xinst-P7 | er_max2_b15_n20 t3[0.25,0.35,0.25,0.5,1.0] | min/down | ["book","P7"] | +30 / -24 / +30 / +16 | +29 / +14 | +34 | +1386 | - | +34 / +34 / +20 | 0.12 | 0.02/1.00 | 0.94 | - | live d$ -28792 dd +0 | 33.7 |

### RANGE (319 valid cells; 88 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RANGE | rr_sofar_n20 stepv[1.5,0.0] | onQ1A/down | ["pool"] | +8 / -15 / +50 / +45 | +12 / +34 | +23 | -5255 | 809 | -14 / +39 / +32 | 0.29 | 0.02/1.00 | 1.24 | plc400 0.010 | live d$ -69300 dd -8855 | 31.5 |
| RANGE | rr_pre_n20 stepv[1.5,0.0] | onQ1A/down | ["pool"] | -16 / +6 / +20 / +23 | +27 / +5 | +1 | +2163 | - | -6 / +27 / +29 | 0.08 | 0.02/1.00 | 0.91 | - | live d$ -7975 dd +0 | 26.6 |
| RANGE | rr_pre_n40 stepv[1.5,0.0] | onQ1A/down | ["pool"] | -16 / +4 / +19 / +23 | +28 / +5 | -2 | +1810 | - | -7 / +25 / +29 | 0.08 | 0.02/1.00 | 0.93 | - | live d$ -7975 dd +0 | 25.2 |
| RANGE | rr_pre_n20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | -15 / +3 / +19 / +23 | +30 / +2 | -3 | +1765 | - | -6 / +25 / +29 | 0.12 | 0.02/1.00 | 0.93 | - | live d$ -19280 dd +0 | 25.0 |
| RANGE | rr_sofar_n20 stepv[1.5,0.5] | onQ1A/down | ["pool"] | +10 / +5 / +29 / +35 | +9 / +16 | +19 | -1731 | 207 | +4 / +24 / +31 | 0.13 | 0.02/1.00 | 1.07 | - | live d$ -24468 dd +0 | 24.4 |
| RANGE | rr_pre_n10 stepv[1.0,0.0] | onQ1A/down | ["pool"] | +14 / +17 / +16 / +32 | +34 / +8 | +12 | +2395 | - | +22 / +24 / +39 | 0.18 | 0.05/1.00 | 0.90 | - | live d$ -19280 dd +0 | 23.7 |

### RANGE-P7 (343 valid cells; 106 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RANGE-P7 | rr_sofar_n20 stepv[1.5,0.0] | onQ1A/down | ["book","P7"] | +8 / -1 / +48 / +35 | +14 / +27 | +19 | +1562 | - | +14 / +51 / +39 | 0.08 | 0.02/1.00 | 0.94 | plc400 0.010 | live d$ -47815 dd +0 | 39.0 |
| RANGE-P7 | rr_sofar_n20 stepv[1.25,0.0] | onQ1A/down | ["book","P7"] | +3 / -11 / +39 / +45 | -12 / +38 | +24 | -2360 | 1017 | -8 / +32 / +38 | 0.11 | 0.02/1.00 | 1.11 | - | live d$ -59605 dd +0 | 32.3 |
| RANGE-P7 | rr_sofar_n20 stepv[1.25,0.5] | onQ1A/down | ["book","P7"] | +5 / +12 / +29 / +29 | +2 / +20 | +18 | -496 | 136 | +2 / +27 / +28 | 0.11 | 0.02/1.00 | 1.02 | - | live d$ -25626 dd +0 | 27.4 |
| RANGE-P7 | rr_sofar_n20 stepv[1.5,0.5] | onQ1A/down | ["book","P7"] | +6 / +8 / +22 / +25 | +14 / +15 | +14 | +1110 | - | +10 / +26 / +28 | 0.08 | 0.02/1.00 | 0.95 | - | live d$ -20330 dd +0 | 25.9 |
| RANGE-P7 | rr_sofar_n10 stepv[1.0,0.0] | onQ1A/down | ["book","P7"] | +11 / -49 / +41 / +54 | -19 / +39 | +26 | -4726 | 543 | -12 / +26 / +42 | 0.15 | 0.05/1.00 | 1.25 | - | live d$ -53465 dd +0 | 25.8 |
| RANGE-P7 | rr_pre_n10 stepv[1.15,0.0] | onQ1A/down | ["book","P7"] | +5 / -1 / +19 / +29 | +41 / +5 | +13 | +1470 | - | +10 / +23 / +33 | 0.03 | 0.03/1.00 | 0.95 | - | live d$ -4460 dd +0 | 23.4 |

### RANGE-book (2254 valid cells; 128 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RANGE-book | rr_sofar_n40 stepv[1.0,0.0] | onQ1A/down | ["book","M7"] | +9 / +13 / +16 / -10 | +27 / +10 | +14 | +788 | - | +12 / +18 / -7 | 0.13 | 0.23/1.00 | 0.97 | - | live d$ -4640 dd +0 | 11.5 |
| RANGE-book | rr_sofar_n10 stepv[1.0,0.0] | onQ1A/down | ["book","M7"] | +12 / +12 / +7 / -6 | +32 / +10 | +17 | +1051 | - | +16 / +10 / -2 | 0.12 | 0.25/1.00 | 0.96 | - | live d$ -8675 dd +0 | 10.4 |
| RANGE-book | rr_sofar_n20 stepv[1.0,0.0] | onQ1A/down | ["book","M7"] | +6 / +12 / +16 / -9 | +34 / +10 | +17 | +1240 | - | +10 / +19 / -5 | 0.12 | 0.31/1.00 | 0.96 | - | live d$ -6255 dd +0 | 9.8 |
| RANGE-book | rr_sofar_n10 stepv[1.15,0.0] | onQ1A/down | ["book","M7"] | +8 / +8 / +8 / -11 | +23 / +7 | +12 | +655 | - | +10 / +10 / -9 | 0.10 | 0.25/1.00 | 0.98 | - | live d$ -9320 dd +0 | 9.7 |
| RANGE-book | rr_sofar_n10 stepv[1.5,0.0] | onQ1A/down | ["book","M7"] | +11 / +4 / +7 / -7 | +10 / +4 | +10 | +692 | - | +13 / +9 / -4 | 0.05 | 0.06/1.00 | 0.97 | - | live d$ -9320 dd +0 | 9.2 |
| RANGE-book | rr_sofar_n20 stepv[1.15,0.0] | onQ1A/down | ["book","M7"] | +7 / +12 / +15 / -10 | +14 / +8 | +11 | +516 | - | +9 / +17 / -7 | 0.10 | 0.17/1.00 | 0.98 | - | live d$ -9320 dd +0 | 9.2 |

### VIX (23 valid cells; 3 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VIX | vix_chg1 stepv[0.1,0.0] | onQ1A/down | ["pool"] | +0 / -37 / +33 / +34 | +38 / +23 | +4 | +1305 | - | +5 / +36 / +37 | 0.11 | 0.02/1.00 | 0.95 | - | live d$ +0 dd +0 | 36.1 |
| VIX | vix_chg1 stepv[0.1,0.5] | onQ1A/down | ["pool"] | +0 / +6 / +15 / +10 | +22 / +12 | +4 | +410 | - | +2 / +17 / +12 | 0.05 | 0.05/1.00 | 0.98 | - | live d$ +0 dd +0 | 11.6 |
| VIX | vix_lvl stepv[17,0.5] | onQ1A/down | ["pool"] | +0 / +20 / +43 / +22 | +2 / +18 | +6 | -3396 | - | -14 / +35 / +11 | 0.19 | 0.18/1.00 | 1.14 | - | live d$ +0 dd +0 | 10.9 |
| VIX | vix_rel20 stepv[1.15,0.5] | onQ1A/down | ["pool"] | +0 / +5 / +38 / +9 | +5 / +15 | -0 | +335 | - | +1 / +39 / +10 | 0.07 | 0.09/1.00 | 0.99 | - | live d$ +0 dd +0 | 10.3 |
| VIX | vix_chg1 stepv[0.03,0.5] | onQ1A/down | ["pool"] | +0 / +9 / +19 / +20 | -12 / +13 | +7 | -3011 | 34682 | -12 / +8 / +10 | 0.12 | 0.15/1.00 | 1.13 | - | live d$ +0 dd +0 | 8.5 |
| VIX | vix_lvl stepv[19,0.5] | onQ1A/down | ["pool"] | +0 / +5 / +43 / -8 | +9 / +17 | +1 | +634 | - | +3 / +45 / -6 | 0.11 | 0.34/1.00 | 0.97 | - | live d$ +0 dd +0 | 2.7 |

### VIX-P7 (31 valid cells; 0 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VIX-P7 | vix_chg1 stepv[0.1,0.0] | onQ1A/down | ["book","P7"] | +0 / -30 / +33 / +10 | +34 / +20 | +4 | +652 | - | +2 / +35 / +12 | 0.03 | 0.17/1.00 | 0.98 | - | live d$ +0 dd +0 | 12.2 |
| VIX-P7 | vix_chg1 stepv[0.03,0.5] | onQ1A/down | ["book","P7"] | -3 / +0 / +17 / +14 | -5 / +14 | +2 | -920 | - | -7 / +14 / +11 | 0.07 | 0.12/1.00 | 1.04 | - | live d$ +0 dd +0 | 10.6 |
| VIX-P7 | vix_lvl stepv[15,0.5] | onQ1A/down | ["book","P7"] | +0 / +20 / +30 / +26 | -14 / +24 | +23 | -3821 | 44010 | -22 / +15 / +10 | 0.18 | 0.17/1.00 | 1.22 | - | live d$ +0 dd +0 | 9.7 |
| VIX-P7 | vix_rel20 stepv[1.15,0.5] | onQ1A/down | ["book","P7"] | +0 / +8 / +30 / +7 | +4 / +11 | -0 | +380 | - | +2 / +31 / +9 | 0.05 | 0.17/1.00 | 0.98 | - | live d$ +0 dd +0 | 8.5 |
| VIX-P7 | vix_lvl stepv[17,0.5] | onQ1A/down | ["book","P7"] | +0 / +20 / +30 / +16 | +11 / +13 | +5 | -2594 | - | -11 / +23 / +8 | 0.12 | 0.25/1.00 | 1.11 | - | live d$ +0 dd +0 | 7.5 |
| VIX-P7 | vix_lvl stepv[19,0.0] | onQ1A/down | ["book","P7"] | +0 / +18 / +51 / -10 | +2 / +21 | +2 | +1465 | - | +6 / +54 / -3 | 0.07 | 0.31/1.00 | 0.94 | - | live d$ +0 dd +0 | 6.1 |

### VOL-P7 (569 valid cells; 407 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-P7 | vr_rv1_w240_bk stepv[1.25,0.0] | onQ1A/down | ["book","P7"] | +43 / +31 / +43 / +33 | +83 / +20 | +52 | +5929 | - | +55 / +55 / +47 | 0.08 | 0.02/0.49 | 0.79 | plc400 0.002 | live d$ -54480 dd +0 | 54.7 |
| VOL-P7 | vr_park_w60_bk stepv[1.1,0.0] | onQ1A/down | ["book","P7"] | -3 / +17 / +43 / +42 | +39 / +26 | +27 | +3939 | - | +12 / +51 / +50 | 0.11 | 0.02/0.83 | 0.86 | plc400 0.010 | live d$ -57215 dd +0 | 50.1 |
| VOL-P7 | vr_ewma5_l94_g20 stepv[1.1,0.0] | onQ1A/down | ["book","P7"] | +42 / +32 / +42 / +60 | +64 / +34 | +55 | +3507 | - | +50 / +50 / +65 | 0.15 | 0.02/0.83 | 0.87 | - | live d$ -67170 dd -5840 | 49.7 |
| VOL-P7 | vr_park_w60_g20 stepv[1.5,0.0] | onQ1A/down | ["book","P7"] | +2 / +18 / +41 / +49 | +44 / +24 | +35 | +3771 | - | +16 / +49 / +56 | 0.10 | 0.02/0.86 | 0.86 | - | live d$ -45090 dd +0 | 49.2 |
| VOL-P7 | vr_ewma5_l94_g20 stepv[1.25,0.0] | onQ1A/down | ["book","P7"] | +41 / +36 / +30 / +58 | +65 / +25 | +51 | +3700 | - | +49 / +40 / +64 | 0.13 | 0.03/0.88 | 0.86 | - | live d$ -54370 dd +0 | 49.0 |
| VOL-P7 | vr_atr_b5_n14_bk stepv[1.1,0.0] | onQ1A/down | ["book","P7"] | +6 / +25 / +40 / +43 | +51 / +25 | +39 | +3023 | - | +17 / +47 / +50 | 0.11 | 0.02/0.95 | 0.89 | - | live d$ -37700 dd +0 | 46.9 |

### VOL-book (2681 valid cells; 274 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-book | vr_gk_w10_g20 stepv[1.25,0.5] | onQ1A/down | ["book","U7"] | +9 / +1 / +4 / +15 | -3 / +1 | +6 | +86 | - | +9 / +4 / +15 | 0.02 | 0.02/1.00 | 1.00 | - | live d$ -542 dd +0 | 9.0 |
| VOL-book | vr_atr_b5_n5_bk stepv[1.25,0.5] | onQ1A/down | ["book","U7"] | +1 / +1 / +8 / +15 | -1 / +3 | +2 | +72 | - | +2 / +8 / +15 | 0.02 | 0.03/1.00 | 1.00 | - | live d$ -542 dd +0 | 8.0 |
| VOL-book | vr_atr_b1_n5_bk stepv[1.25,0.5] | onQ1A/down | ["book","U7"] | +3 / +1 / +8 / +8 | -4 / +0 | +1 | -14 | 6 | +3 / +8 / +8 | 0.02 | 0.03/1.00 | 1.00 | - | live d$ +732 dd +0 | 7.7 |
| VOL-book | vr_gk_w10_g20 stepv[1.5,0.5] | onQ1A/down | ["book","U7"] | +9 / -2 / +1 / +8 | -1 / +1 | +6 | -322 | 47 | +8 / -0 / +7 | 0.01 | 0.02/1.00 | 1.01 | - | live d$ -1202 dd +0 | 7.1 |
| VOL-book | vr_atr_b5_n20_bk stepv[1.25,0.5] | onQ1A/down | ["book","U7"] | +0 / +2 / +8 / +8 | -3 / +1 | +0 | -159 | - | -1 / +7 / +7 | 0.02 | 0.03/1.00 | 1.01 | - | live d$ -1742 dd +0 | 7.1 |
| VOL-book | vr_atr_b5_n5_bk stepv[1.5,0.5] | onQ1A/down | ["book","U7"] | +0 / -2 / +8 / +11 | -4 / +3 | +0 | -192 | - | -1 / +7 / +10 | 0.02 | 0.02/1.00 | 1.01 | - | live d$ -1202 dd +0 | 7.0 |

### VOL-pool (1076 valid cells; 635 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool | vr_gk_w30_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +34 / +47 / +52 / +54 | +62 / +35 | +52 | +6308 | - | +48 / +62 / +64 | 0.54 | 0.02/0.15 | 0.79 | plc400 0.005 | live d$ -51940 dd -1940 | 62.0 |
| VOL-pool | vr_park_w10_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +53 / +58 / +49 / +67 | +35 / +44 | +64 | +3560 | - | +59 / +56 / +71 | 0.56 | 0.02/0.28 | 0.86 | plc400 0.005 | live d$ -48050 dd +0 | 59.3 |
| VOL-pool | vr_gk_w10_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +54 / +59 / +58 / +55 | +7 / +43 | +66 | +2243 | - | +58 / +62 / +59 | 0.56 | 0.02/0.28 | 0.91 | plc400 0.002 | live d$ -63235 dd +0 | 59.0 |
| VOL-pool | vr_gk_w10_bk stepv[1.25,0.0] | onQ1A/down | ["pool"] | +17 / +34 / +53 / +55 | +42 / +32 | +53 | +3305 | - | +28 / +59 / +61 | 0.38 | 0.02/0.28 | 0.88 | plc400 0.002 | live d$ -45055 dd +0 | 59.0 |
| VOL-pool | vr_atr_b1_n50_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +19 / +35 / +59 / +52 | +34 / +46 | +45 | +3634 | - | +29 / +64 / +59 | 0.52 | 0.02/0.28 | 0.87 | - | live d$ -66935 dd -6055 | 58.7 |
| VOL-pool | vr_park_w30_g20 stepv[1.25,0.0] | onQ1A/down | ["pool"] | +24 / +39 / +48 / +58 | +72 / +36 | +52 | +5716 | - | +39 / +59 / +66 | 0.54 | 0.02/0.28 | 0.80 | - | live d$ -60495 dd -1940 | 58.5 |

### VOL-sess (1572 valid cells; 300 with own p <= .10)
| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-sess | vr_gk_w10_g20 stepv[1.25,0.5] | onQ1A/down | ["sess",1] | +9 / -5 / +21 / +31 | +1 / +13 | +11 | +537 | - | +11 / +22 / +33 | 0.06 | 0.03/1.00 | 0.98 | - | live d$ -1122 dd +0 | 22.4 |
| VOL-sess | vr_park_w10_g20 stepv[1.25,0.5] | onQ1A/down | ["sess",1] | +7 / -4 / +19 / +26 | +5 / +12 | +10 | +930 | - | +10 / +22 / +28 | 0.06 | 0.02/1.00 | 0.96 | - | live d$ +5105 dd +0 | 22.1 |
| VOL-sess | vr_ewma1_l90_g20 stepv[1.25,0.5] | onQ1A/down | ["sess",1] | +8 / -2 / +19 / +20 | +7 / +9 | +8 | +544 | - | +10 / +21 / +22 | 0.06 | 0.03/1.00 | 0.98 | - | live d$ +755 dd +0 | 21.1 |
| VOL-sess | vr_atr_b1_n5_g20 stepv[1.25,0.5] | onQ1A/down | ["sess",1] | +10 / +2 / +19 / +21 | +13 / +11 | +16 | +335 | - | +11 / +20 / +22 | 0.07 | 0.02/1.00 | 0.99 | - | live d$ +4960 dd +0 | 20.0 |
| VOL-sess | vr_atr_b1_n20_bk stepv[1.25,0.5] | onQ1A/down | ["sess",1] | -5 / -1 / +17 / +21 | +4 / +8 | +4 | +632 | - | -2 / +19 / +23 | 0.04 | 0.02/1.00 | 0.97 | - | live d$ -1129 dd +0 | 19.1 |
| VOL-sess | vr_atr_b1_n30_bk stepv[1.25,0.5] | onQ1A/down | ["sess",1] | -8 / -3 / +17 / +16 | -1 / +7 | +5 | +731 | - | -4 / +19 / +19 | 0.04 | 0.02/1.00 | 0.97 | - | live d$ -1129 dd +0 | 18.8 |

## UP vs Q1-A variants (alone / replace / up-allowed: raise lots for some trades vs Q1-A; labelled, never promoted)

| sub | cell | mode/dir | scope | maxDD cut % L/H/P/X' (equal lots) | worst-20 d% L6M/PRE | Ulcer cut % L6M | d mean $/wk L6M | $ mean lost per $1k DD cut | equal-mean maxDD cut % L6M/PRE/X' | share lots changed | p own/family | eq scale s | placebo | live week | tolerant eq score |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool | vr_gk_w60_g20 stepv[1.25,0.0] | alone/down | ["pool"] | -36 / -10 / +48 / +47 | +86 / +18 | +20 | +14309 | - | +15 / +68 / +67 | 0.76 | 0.02/0.08 | 0.62 | - | live d$ -37078 dd -3200 | 66.8 |
| VOL-pool | vr_gk_w10_g20 stepv[1.25,0.0] | alone/down | ["pool"] | +33 / +46 / +48 / +47 | +47 / +25 | +54 | +11037 | - | +54 / +65 / +64 | 0.77 | 0.02/0.14 | 0.68 | - | live d$ -36404 dd +0 | 64.1 |
| VOL-pool | vr_park_w60_g20 stepv[1.25,0.0] | alone/down | ["pool"] | -39 / -11 / +46 / +43 | +69 / +20 | +16 | +13089 | - | +11 / +65 / +64 | 0.76 | 0.02/0.14 | 0.64 | - | live d$ -29321 dd -3200 | 63.6 |
| VOL-P7 | vr_ewma5_l94_g20 stepv[1.1,0.0] | alone/down | ["book","P7"] | +47 / +20 / +32 / +54 | +131 / +18 | +55 | +10454 | - | +63 / +53 / +68 | 0.21 | 0.02/0.14 | 0.69 | - | live d$ -62580 dd -7246 | 63.1 |
| VOL-pool | vr_atr_b1_n50_g20 stepv[1.25,0.0] | alone/down | ["pool"] | -19 / +5 / +54 / +38 | +105 / +26 | +31 | +15111 | - | +28 / +72 / +62 | 0.76 | 0.02/0.15 | 0.61 | - | live d$ -44050 dd -7255 | 62.4 |
| VOL-P7 | vr_ewma5_l94_g20 stepv[1.25,0.0] | alone/down | ["book","P7"] | +47 / +31 / +13 / +48 | +133 / +7 | +51 | +8249 | - | +61 / +36 / +62 | 0.20 | 0.02/0.18 | 0.74 | - | live d$ -44971 dd +0 | 60.9 |
| VOL-pool | vr_atr_b5_n14_g20 stepv[1.25,0.0] | alone/down | ["pool"] | -8 / +13 / +37 / +53 | +72 / +13 | +28 | +12557 | - | +30 / +59 / +70 | 0.76 | 0.02/0.28 | 0.65 | - | live d$ -58996 dd -2000 | 59.3 |
| VOL-P7 | vr_rv1_w240_g20 stepv[1.25,0.0] | alone/down | ["book","P7"] | +44 / +23 / +24 / +52 | +133 / +3 | +53 | +8507 | - | +59 / +44 / +65 | 0.19 | 0.02/0.28 | 0.73 | - | live d$ -42790 dd +0 | 58.6 |

## Skip-share diagnostics for the finalists: is it vol timing or just trading less?
Placebos (B=200, stat = tolerant equal-mean cut): R = same lot ratios assigned to random trades anywhere (same count); G = permuted within book x session; M = the vol/ER feature shuffled within book x session x month (rule unchanged, timing broken, regime level kept). Mild twin = the same cell with multiplier 0.5 instead of 0 (n/a for ER t3 and hysteresis).

| cell | share lots cut | eq scale s | tol score | random-R mean/sd | feature-shuffle mean / p90 | p R / G / M | mild 0.5: tol, share cut, L6M d mean, cut L6M/PRE/X' |
|--|--|--|--|--|--|--|--|
| VOL-pool vr_gk_w30_g20 [1.25, 0.0] onQ1A | 0.54 | 0.79 | 62.0 | -20.0 / 38.6 | 4.8 / 35.2 | 0.005 / 0.005 / 0.005 | 33.3, 0.17, +3460, +23/+23/+39 |
| VOL-pool vr_park_w10_g20 [1.25, 0.0] onQ1A | 0.56 | 0.86 | 59.3 | -13.8 / 32.7 | -1.7 / 30.3 | 0.005 / 0.005 / 0.005 | 35.0, 0.18, +2686, +24/+28/+54 |
| VOL-pool vr_gk_w10_g20 [1.25, 0.0] onQ1A | 0.56 | 0.91 | 59.0 | -13.6 / 30.9 | 2.5 / 33.0 | 0.005 / 0.010 / 0.005 | 35.5, 0.18, +2096, +29/+30/+53 |
| VOL-pool vr_gk_w10_bk [1.25, 0.0] onQ1A | 0.38 | 0.88 | 59.0 | -19.9 / 38.3 | -1.6 / 25.4 | 0.005 / 0.005 / 0.005 | 34.6, 0.12, +2451, +14/+28/+38 |
| VOL-P7 vr_rv1_w240_bk [1.25, 0.0] onQ1A | 0.08 | 0.79 | 54.7 | -6.3 / 16.5 | 3.3 / 26.4 | 0.005 / 0.005 / 0.005 | 28.8, 0.07, +3677, +20/+17/+16 |
| VOL-P7 vr_park_w60_bk [1.1, 0.0] onQ1A | 0.11 | 0.86 | 50.1 | -9.2 / 18.5 | 16.9 / 36.7 | 0.005 / 0.010 / 0.010 | 25.3, 0.10, +2721, +1/+17/+27 |
| ER-NQ-P7 er_nq_b15_n20 [0.3, 0.0, 1.0] min | 0.15 | 1.05 | 41.2 | -8.6 / 21.8 | -15.2 / 23.2 | 0.005 / 0.015 / 0.020 | 18.5, 0.04, +861, +17/+15/-7 |
| ER-NQ er_nq_b3_n10 [0.2, 0.4, 0.25, 0.5, 1.0] min | 0.17 | 0.91 | 41.3 | -4.8 / 11.0 | 9.7 / 27.1 | 0.005 / 0.005 / 0.005 | n/a |
| ER-hyst-P7 hy_b15_n20_30_40 [0.5, 0.0] min | 0.17 | 1.21 | 35.2 | -7.7 / 23.2 | -12.3 / 23.5 | 0.025 / 0.020 / 0.025 | n/a |
| RANGE rr_sofar_n20 [1.5, 0.0] onQ1A | 0.29 | 1.24 | 31.5 | -19.7 / 36.9 | -28.3 / 10.6 | 0.045 / 0.025 / 0.010 | 24.4, 0.13, -1731, +10/+29/+35 |
| RANGE-P7 rr_sofar_n20 [1.5, 0.0] onQ1A | 0.08 | 0.94 | 39.0 | -6.0 / 14.8 | -15.6 / 16.9 | 0.005 / 0.015 / 0.005 | 25.9, 0.08, +1110, +6/+22/+25 |
| ER-xinst-P7 er_min3_b15_n20 [0.35, 0.0, 1.0] min | 0.21 | 1.49 | 35.9 | -15.6 / 25.0 | -10.3 / 16.8 | 0.005 / 0.040 / 0.005 | 22.3, 0.08, +412, +21/+21/+12 |

Skip share vs equal-mean scale (VOL-pool onQ1A step cells, all multipliers): 
| share of lots cut | n cells | median s | median tolerant eq score | median L6M d mean |
|--|--|--|--|--|
| (0.0, 0.1] | 357 | 1.00 | 3.4 | +0 |
| (0.1, 0.2] | 189 | 0.98 | 22.9 | +435 |
| (0.2, 0.3] | 59 | 1.03 | 27.5 | -685 |
| (0.3, 0.4] | 71 | 1.00 | 29.9 | +28 |
| (0.4, 0.5] | 34 | 1.01 | 37.0 | -153 |
| (0.5, 0.6] | 26 | 0.92 | 54.8 | +2055 |

## Controls (same cells, tolerant equal-mean score and L6M/PRE cuts on the NOCUT and UNIF bases; first-order)
| cell | tol COMB | tol NOCUT | tol UNIF | L6M cut C/N/U | PRE cut C/N/U |
|--|--|--|--|--|--|
| RANGE rr_sofar_n20 [1.5, 0.0] onQ1A | 31.5 | 36.4 | 23.9 | +8/+41/+34 | +50/+26/+37 |
| VOL-P7 vr_rv1_w240_bk [1.25, 0.0] onQ1A | 54.7 | 56.5 | 58.9 | +43/+48/+41 | +43/+42/+44 |
| VOL-P7 vr_park_w60_bk [1.1, 0.0] onQ1A | 50.1 | 63.1 | 55.3 | -3/+37/+30 | +43/+37/+48 |
| ER-NQ-P7 er_nq_b15_n20 [0.3, 0.0, 1.0] min | 41.2 | 33.9 | 44.1 | +37/+43/+36 | +47/+29/+25 |
| VOL-pool vr_park_w10_g20 [1.25, 0.0] onQ1A | 59.3 | 62.8 | 52.8 | +53/+59/+42 | +49/+29/+47 |
| VOL-pool vr_gk_w30_g20 [1.25, 0.0] onQ1A | 62.0 | 65.6 | 73.4 | +34/+59/+47 | +52/+36/+14 |
| ER-xinst-P7 er_min3_b15_n20 [0.35, 0.0, 1.0] min | 35.9 | 62.0 | 56.3 | +47/+70/+58 | +57/+50/+44 |
| VOL-pool vr_gk_w10_g20 [1.25, 0.0] onQ1A | 59.0 | 62.6 | 52.8 | +54/+63/+47 | +58/+35/+50 |
| ER-NQ er_nq_b3_n10 [0.2, 0.4, 0.25, 0.5, 1.0] min | 41.3 | 37.7 | 39.7 | +35/+42/+46 | +20/+15/+11 |
| ER-hyst-P7 hy_b15_n20_30_40 [0.5, 0.0] min | 35.2 | 15.2 | 38.9 | +30/+55/+42 | +46/+31/+25 |
| VOL-pool vr_gk_w10_bk [1.25, 0.0] onQ1A | 59.0 | 44.1 | 58.6 | +17/+47/+26 | +53/+31/+50 |
| RANGE-P7 rr_sofar_n20 [1.5, 0.0] onQ1A | 39.0 | 43.7 | 50.9 | +8/+40/+27 | +48/+41/+38 |

Across the 400 top cells (M_AB set) the tolerant score is > 0 on NOCUT for 98 % and on UNIF for 99 %; correlation of the score COMB vs NOCUT 0.51, vs UNIF 0.39.

## Hysteresis ER (enter/exit) - 184 strictly-down cells (bars 5/15, n 10/20/30, 8 enter/exit pairs, lo 0 or 0.5, pooled and P7)
Best: ER-hyst-P7 hy_b5_n30_35_50 [0.5, 0.0] (min): equal-mean cut +22/+44/+47 % L6M/PRE/X', own p 0.03, family p 1.00. Pooled hysteresis median tolerant score 4.3 vs plain ER-NQ min-mode median 9.3: hysteresis adds no robust edge beyond P7.

## Exact-engine re-runs (VOID: the first batch used the sz_exact keying bug and was withdrawn at 17:00Z; all six sets re-queued with the fixed driver, no exact verdict yet; sz_exact.py; lead cut 2026-11-09: only the top 3 finalists = AB_F00..AB_F04 (top-5: first three finalists, best ER cell, best P7-slice cell) plus AB_F12 = mild 0.5 twin of AB_F00; months L6M, then PRE, then X-prime; <=2 workers, MemAvailable >= 55 GB; the other 9 finalists stay first-order)

| set (cell) | months | window | exact: maxDD cut % | exact: d mean $/wk | exact: equal-mean cut % | exact: worst-20 d% | first-order cut % | first-order d mean |
|--|--|--|--|--|--|--|--|--|

Rows above (if any) come only from runs with the fixed driver.

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
- Cells dominating Q1-A on both mean and maxDD (down-only, L6M and HOLD d mean >= 0, tolerant equal-lots cut > 0): 3436 of 34625 (first-order means overstate; most are skip filters).
- Cells trading mean for DD: median $ weekly mean lost per $1k of maxDD cut (L6M, cells with d mean < 0 and cut > 0): 187.
- Caveats: skip cells change which trades exist, so exact re-runs (locks, re-entries, state-cut arm sizes via sqrt(lots)) will move numbers; ES/RTY ER and VIX exist only to 2026-10-16 (later signals fall back to Q1-A); the 10 v1.5 bug exits of the 11-08/09 night are not in the S1b base; live week = frozen file (180 rows), first-order.