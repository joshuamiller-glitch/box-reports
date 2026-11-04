# SHADOW_OC - operating characteristics of the Shadow verdict rules (DIS-BH), BASE-4, 2026-11-04T23:02Z

Research only, nothing live, no PASS. Scope note l2vast/ds3/prereg/DISBH_scope.md sha256 f05c6b92579b9bd689c8967fb2869b5144011b9b8fbec531a5cb63a996184c75 (DECISIONS.md, before any simulation output). Rules are read from code (shadow2_weekly.rows_for, fade_forward_weekly.summarize, nyam_forward_weekly.summarize). Simulation: stationary block bootstrap of research WEEKS (mean block 4, 5,000 paths, 104 weeks; counts, P&L, tails and clustering of 2023-04..2026-10 kept; every trade shifted so the per-trade mean equals the stated truth). Code l2vast/ds3/code/disbh/ (bh_data, bh_sim, bh_sim2, bh_monday_test, bh_doc); data /mnt/l2/l2vast/ds3_base4/bh_*.pkl.

## Answer
**The SHADOW-2 verdict rule cannot decide four of the five lines within two years, even when the line is exactly as good as its H1 (DIS-K is the exception: 18% of paths reach CONSISTENT by week 104 at the design truth, 63% if the 2026 mean is true).** With alpha = beta = .10 and H1 = half the 2026 research mean, the expected SPRT length at the design truth is 336-1009 trades per line (Wald), i.e. 223-1005 weeks at the observed rates (Q13 1.47, DIS-K 1.51, DIS-B 2.03, DIS-E 1.70, DIS-C 0.97 trades/week over 2023-26; 1.65 / 1.51 / 1.67 / 2.26 / 1.00 in 2026): 4.3 to 19 years. In the simulation the probability that any of the five lines reaches CONSISTENT within 104 weeks is 0.63 for DIS-K and at most 0.20 for the other four if the 2026 mean is the truth, and 0.18 (DIS-K) / at most 0.02 (the others) at the design truth; the lower bound is never reached by the SPRT itself (<= 0.00 by week 104 under zero truth), and the only decisions that appear are the z-rule CONTRADICTED after week 26 (zero truth: 0.08 to 0.36 of paths by week 104; selection-deflated truth: 0.41 to 0.74). INCONCLUSIVE persists on 0.76 to 0.99 of paths at week 104 under H1 and 0.63 to 0.92 under zero. The SPRT cannot resolve the lines because the information per trade is tiny: mu/sd = 0.059 to 0.102 per trade.
**Pooling the five lines is what works:** a single SPRT on all five lines (each trade with its own H1; the lines are nearly independent, DIS-T) decides in a median of about 58 weeks at the design truth (64% of paths decided within 104 weeks, CONSISTENT 61% / CONTRADICTED 3% by week 104) and in 37 weeks when the 2026 mean is the truth (all paths decided by week 104). alpha = beta = .10 per line is not sensible at 1-2 trades per week; the proposal is in section 6.

## 1. Design numbers (Wald approximation; per-trade information = mu^2 / (2 sd^2); alpha = beta = .10, bounds +-2.197; expected trades E[N] = (0.9 x 2.197 - 0.1 x 2.197) / KL under H1 and the same under H0)
| line | rule | H1 mu / sd (pt per lot-trade) | trades/week 2023-26 / 2026 | KL per trade | expected trades to decide | weeks at 2023-26 rate / 2026 rate |
|--|--|--|--|--|--|--|
| Q13GAP_T1 | SHADOW-2 (z from week 26, n >= 30) | 6.90 / 82.55 | 1.47 / 1.65 | 0.00349 | 503 | 342 / 305 |
| DISK_BO_CH | SHADOW-2 (z from week 26, n >= 30) | 5.86 / 57.37 | 1.51 / 1.51 | 0.00522 | 337 | 223 / 223 |
| DISB_PREL | SHADOW-2 (z from week 26, n >= 30) | 2.36 / 39.85 | 2.03 / 1.67 | 0.00175 | 1002 | 495 / 599 |
| DISE_PDF | SHADOW-2 (z from week 26, n >= 30) | 3.20 / 54.23 | 1.70 / 2.26 | 0.00174 | 1010 | 596 / 448 |
| DISC_SUN30 | SHADOW-2 (z from week 26, n >= 30) | 2.45 / 40.88 | 0.97 / 1.00 | 0.00180 | 979 | 1006 / 979 |
| VB2NYPM_T1 | fade runner (z from week 13) | 2.99 / 23.23 | 2.80 / 2.33 | 0.00828 | 212 | 76 / 91 |
| PDASIA_T2 | fade runner (z from week 13) | 3.30 / 35.00 | 1.70 / 2.37 | 0.00444 | 395 | 233 / 167 |
| VB2NYAM_T3 | fade runner (z from week 13) | 1.07 / 48.50 | 4.78 / 4.81 | 0.00024 | 7223 | 1513 / 1500 |
| OR15NYAM_T2 | fade runner (z from week 13) | 5.25 / 121.14 | 4.41 / 4.51 | 0.00094 | 1872 | 425 / 415 |
| ONRTH | NYAM runner (z from week 13) | 6.60 / 59.20 | 2.90 / 2.74 | 0.00621 | 283 | 97 / 103 |
| VWAPF | NYAM runner (z from week 13) | 4.00 / 60.20 | 7.67 / 9.86 | 0.00221 | 796 | 104 / 81 |
| ORBF | NYAM runner (z from week 13) | 3.90 / 59.60 | 4.89 / 4.91 | 0.00214 | 821 | 168 / 167 |
(The lead's 2026 rates Q13 1.65, DIS-K 1.51, DIS-B 1.67, DIS-E 2.26, DIS-C 1.0 are the 2026 column; DIS-B and DIS-E ran more often in 2026 than over 2023-26.) The NYAM bundle pools three books at about 15 trades/week: it is the only monitored object with enough trades to decide in under a year.

## 2. SHADOW-2 lines: first decision by week 26 / 52 / 104 under each truth (P(CONSISTENT) / P(CONTRADICTED by llr or z) / P(undecided))
Truths per trade: (i) 2026 research mean (= 2 x H1 mean), (ii) half of it (= H1, the design point), (iii) zero, (iv) regime-off = pre-2026 pool mean, (v) selection-deflated (DIS-T estimator A, 1 lot, ALL window). Expected weeks to decision: mean over the decided paths (share decided by week 104).

**Q13GAP_T1** (H1 6.90 / 82.55; 1.47 trades/week)
| truth (pt/trade) | wk 26 | wk 52 | wk 104 | weeks to decision (decided share) |
|--|--|--|--|--|
| (i) 2026 research mean (13.80) | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.20 / 0.00 / 0.80 | 85 (20%) |
| (ii) half of it (= H1) (6.90) | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.02 / 0.00 / 0.98 | 83 (2%) |
| (iii) zero (0.00) | 0.00 / 0.00 / 1.00 | 0.00 / 0.03 / 0.97 | 0.00 / 0.11 / 0.89 | 70 (11%) |
| (iv) regime-off (pre-2026 mean) (-0.42) | 0.00 / 0.00 / 1.00 | 0.00 / 0.03 / 0.97 | 0.00 / 0.13 / 0.87 | 70 (13%) |
| (v) selection-deflated (DIS-T A, ALL) (-5.48) | 0.00 / 0.03 / 0.97 | 0.00 / 0.21 / 0.79 | 0.00 / 0.54 / 0.46 | 63 (54%) |

**DISK_BO_CH** (H1 5.86 / 57.37; 1.51 trades/week)
| truth (pt/trade) | wk 26 | wk 52 | wk 104 | weeks to decision (decided share) |
|--|--|--|--|--|
| (i) 2026 research mean (11.72) | 0.01 / 0.00 / 0.99 | 0.17 / 0.01 / 0.82 | 0.63 / 0.01 / 0.36 | 67 (64%) |
| (ii) half of it (= H1) (5.86) | 0.00 / 0.01 / 0.99 | 0.02 / 0.04 / 0.94 | 0.18 / 0.06 / 0.76 | 69 (24%) |
| (iii) zero (0.00) | 0.00 / 0.05 / 0.95 | 0.00 / 0.19 / 0.81 | 0.01 / 0.36 / 0.63 | 55 (37%) |
| (iv) regime-off (pre-2026 mean) (2.84) | 0.00 / 0.03 / 0.97 | 0.01 / 0.10 / 0.89 | 0.05 / 0.17 / 0.78 | 57 (22%) |
| (v) selection-deflated (DIS-T A, ALL) (-4.02) | 0.00 / 0.12 / 0.88 | 0.00 / 0.40 / 0.60 | 0.00 / 0.70 / 0.30 | 52 (70%) |

**DISB_PREL** (H1 2.36 / 39.85; 2.03 trades/week)
| truth (pt/trade) | wk 26 | wk 52 | wk 104 | weeks to decision (decided share) |
|--|--|--|--|--|
| (i) 2026 research mean (4.72) | 0.00 / 0.00 / 1.00 | 0.00 / 0.01 / 0.99 | 0.04 / 0.01 / 0.95 | 86 (5%) |
| (ii) half of it (= H1) (2.36) | 0.00 / 0.01 / 0.99 | 0.00 / 0.02 / 0.98 | 0.00 / 0.03 / 0.97 | 46 (3%) |
| (iii) zero (0.00) | 0.00 / 0.02 / 0.98 | 0.00 / 0.07 / 0.93 | 0.00 / 0.14 / 0.86 | 56 (14%) |
| (iv) regime-off (pre-2026 mean) (0.73) | 0.00 / 0.02 / 0.98 | 0.00 / 0.05 / 0.95 | 0.00 / 0.09 / 0.91 | 53 (9%) |
| (v) selection-deflated (DIS-T A, ALL) (-3.53) | 0.00 / 0.10 / 0.90 | 0.00 / 0.33 / 0.67 | 0.00 / 0.67 / 0.33 | 56 (67%) |

**DISE_PDF** (H1 3.20 / 54.23; 1.70 trades/week)
| truth (pt/trade) | wk 26 | wk 52 | wk 104 | weeks to decision (decided share) |
|--|--|--|--|--|
| (i) 2026 research mean (6.40) | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.02 / 0.00 / 0.98 | 86 (2%) |
| (ii) half of it (= H1) (3.20) | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.00 / 0.01 / 0.99 | 53 (1%) |
| (iii) zero (0.00) | 0.00 / 0.01 / 0.99 | 0.00 / 0.03 / 0.97 | 0.00 / 0.08 / 0.92 | 62 (8%) |
| (iv) regime-off (pre-2026 mean) (-0.43) | 0.00 / 0.01 / 0.99 | 0.00 / 0.04 / 0.96 | 0.00 / 0.10 / 0.90 | 63 (10%) |
| (v) selection-deflated (DIS-T A, ALL) (-5.87) | 0.00 / 0.09 / 0.91 | 0.00 / 0.36 / 0.64 | 0.00 / 0.74 / 0.26 | 56 (74%) |

**DISC_SUN30** (H1 2.45 / 40.88; 0.97 trades/week)
| truth (pt/trade) | wk 26 | wk 52 | wk 104 | weeks to decision (decided share) |
|--|--|--|--|--|
| (i) 2026 research mean (4.90) | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.01 / 0.00 / 0.99 | 74 (1%) |
| (ii) half of it (= H1) (2.45) | 0.00 / 0.00 / 1.00 | 0.00 / 0.01 / 0.99 | 0.00 / 0.03 / 0.97 | 59 (3%) |
| (iii) zero (0.00) | 0.00 / 0.00 / 1.00 | 0.00 / 0.06 / 0.94 | 0.00 / 0.13 / 0.87 | 61 (13%) |
| (iv) regime-off (pre-2026 mean) (3.46) | 0.00 / 0.00 / 1.00 | 0.00 / 0.01 / 0.99 | 0.00 / 0.02 / 0.98 | 58 (2%) |
| (v) selection-deflated (DIS-T A, ALL) (-3.06) | 0.00 / 0.00 / 1.00 | 0.00 / 0.20 / 0.80 | 0.00 / 0.41 / 0.59 | 57 (41%) |

## 3. Fade runners (z from week 13, no n >= 30) and the NYAM bundle (pooled three books, z with sd 60 from week 13)

**VB2NYPM_T1**
| truth | wk 13 | wk 26 | wk 52 | wk 104 | weeks to decision (decided share) |
|--|--|--|--|--|--|
| (i) 2026 research mean | 0.04 / 0.01 / 0.95 | 0.41 / 0.01 / 0.58 | 0.87 / 0.01 / 0.12 | 0.98 / 0.01 / 0.00 | 33 (100%) |
| (ii) half of it (= H1) | 0.01 / 0.03 / 0.96 | 0.09 / 0.07 / 0.84 | 0.35 / 0.10 / 0.55 | 0.66 / 0.13 / 0.20 | 51 (80%) |
| (iii) zero | 0.00 / 0.11 / 0.89 | 0.01 / 0.27 / 0.72 | 0.04 / 0.47 / 0.49 | 0.07 / 0.72 / 0.21 | 44 (79%) |
| (iv) regime-off (pre-2026 mean) | 0.00 / 0.09 / 0.91 | 0.01 / 0.23 / 0.76 | 0.06 / 0.39 / 0.55 | 0.12 / 0.61 / 0.28 | 45 (72%) |
| (v) selection-deflated (DIS-T A, ALL) | 0.00 / 0.20 / 0.80 | 0.00 / 0.46 / 0.53 | 0.01 / 0.74 / 0.26 | 0.01 / 0.95 / 0.05 | 35 (95%) |

**PDASIA_T2**
| truth | wk 13 | wk 26 | wk 52 | wk 104 | weeks to decision (decided share) |
|--|--|--|--|--|--|
| (i) 2026 research mean | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.09 / 0.00 / 0.91 | 0.57 / 0.00 / 0.43 | 74 (57%) |
| (ii) half of it (= H1) | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.01 / 0.01 / 0.99 | 0.08 / 0.01 / 0.91 | 77 (9%) |
| (iii) zero | 0.00 / 0.01 / 0.99 | 0.00 / 0.03 / 0.97 | 0.00 / 0.09 / 0.91 | 0.00 / 0.25 / 0.75 | 62 (25%) |
| (iv) regime-off (pre-2026 mean) | 0.00 / 0.00 / 1.00 | 0.00 / 0.01 / 0.99 | 0.00 / 0.04 / 0.96 | 0.01 / 0.11 / 0.88 | 65 (12%) |
| (v) selection-deflated (DIS-T A, ALL) | 0.00 / 0.02 / 0.98 | 0.00 / 0.08 / 0.92 | 0.00 / 0.26 / 0.74 | 0.00 / 0.60 / 0.40 | 58 (60%) |

**VB2NYAM_T3**
| truth | wk 13 | wk 26 | wk 52 | wk 104 | weeks to decision (decided share) |
|--|--|--|--|--|--|
| (i) 2026 research mean | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 33 (0%) |
| (ii) half of it (= H1) | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 36 (0%) |
| (iii) zero | 0.00 / 0.00 / 1.00 | 0.00 / 0.01 / 0.99 | 0.00 / 0.01 / 0.99 | 0.00 / 0.03 / 0.97 | 53 (3%) |
| (iv) regime-off (pre-2026 mean) | 0.00 / 0.00 / 1.00 | 0.00 / 0.00 / 1.00 | 0.00 / 0.01 / 0.99 | 0.00 / 0.02 / 0.98 | 54 (2%) |
| (v) selection-deflated (DIS-T A, ALL) | 0.00 / 0.01 / 0.99 | 0.00 / 0.07 / 0.93 | 0.00 / 0.22 / 0.78 | 0.00 / 0.55 / 0.45 | 60 (55%) |

**OR15NYAM_T2**
| truth | wk 13 | wk 26 | wk 52 | wk 104 | weeks to decision (decided share) |
|--|--|--|--|--|--|
| (i) 2026 research mean | 0.00 / 0.00 / 1.00 | 0.00 / 0.01 / 0.99 | 0.01 / 0.01 / 0.98 | 0.17 / 0.01 / 0.82 | 78 (18%) |
| (ii) half of it (= H1) | 0.00 / 0.01 / 0.99 | 0.00 / 0.03 / 0.97 | 0.00 / 0.04 / 0.96 | 0.04 / 0.06 / 0.91 | 55 (9%) |
| (iii) zero | 0.00 / 0.02 / 0.98 | 0.00 / 0.06 / 0.94 | 0.00 / 0.13 / 0.87 | 0.00 / 0.23 / 0.77 | 51 (23%) |
| (iv) regime-off (pre-2026 mean) | 0.00 / 0.03 / 0.97 | 0.00 / 0.08 / 0.92 | 0.00 / 0.17 / 0.83 | 0.00 / 0.34 / 0.66 | 53 (34%) |
| (v) selection-deflated (DIS-T A, ALL) | 0.00 / 0.07 / 0.93 | 0.00 / 0.25 / 0.75 | 0.00 / 0.55 / 0.45 | 0.00 / 0.83 / 0.17 | 45 (83%) |

**NYAM_bundle**
| truth | wk 13 | wk 26 | wk 52 | wk 104 | weeks to decision (decided share) |
|--|--|--|--|--|--|
| (i) 2026 research mean | 0.40 / 0.01 / 0.59 | 0.79 / 0.02 / 0.19 | 0.96 / 0.02 / 0.02 | 0.98 / 0.02 / 0.00 | 18 (100%) |
| (ii) half of it (= H1) | 0.17 / 0.06 / 0.77 | 0.40 / 0.13 / 0.48 | 0.63 / 0.19 / 0.18 | 0.74 / 0.23 / 0.02 | 31 (98%) |
| (iii) zero | 0.04 / 0.23 / 0.74 | 0.09 / 0.49 / 0.42 | 0.14 / 0.72 / 0.14 | 0.16 / 0.82 / 0.02 | 29 (98%) |
| (iv) regime-off (pre-2026 mean) | 0.02 / 0.35 / 0.63 | 0.06 / 0.65 / 0.29 | 0.07 / 0.85 / 0.07 | 0.08 / 0.92 / 0.00 | 23 (100%) |
| (v) selection-deflated (DIS-T A, ALL) | 0.01 / 0.43 / 0.55 | 0.03 / 0.75 / 0.22 | 0.03 / 0.93 / 0.03 | 0.03 / 0.97 / 0.00 | 20 (100%) |

## 4. False alarms and misses (by week 104; first decision)
| line | false CONSISTENT (truth zero) | wrong CONTRADICTED at the design truth (ii) | wrong CONTRADICTED if the 2026 mean is true (i) | miss: no CONSISTENT at (i) | miss: no CONTRADICTED at zero | undecided at design truth (ii) |
|--|--|--|--|--|--|--|
| Q13GAP_T1 | 0.00 | 0.00 | 0.00 | 0.80 | 0.89 | 0.98 |
| DISK_BO_CH | 0.01 | 0.06 | 0.01 | 0.37 | 0.64 | 0.76 |
| DISB_PREL | 0.00 | 0.03 | 0.01 | 0.96 | 0.86 | 0.97 |
| DISE_PDF | 0.00 | 0.01 | 0.00 | 0.98 | 0.92 | 0.99 |
| DISC_SUN30 | 0.00 | 0.03 | 0.00 | 0.99 | 0.87 | 0.97 |
| VB2NYPM_T1 | 0.07 | 0.13 | 0.01 | 0.02 | 0.28 | 0.20 |
| PDASIA_T2 | 0.00 | 0.01 | 0.00 | 0.43 | 0.75 | 0.91 |
| VB2NYAM_T3 | 0.00 | 0.00 | 0.00 | 1.00 | 0.97 | 1.00 |
| OR15NYAM_T2 | 0.00 | 0.06 | 0.01 | 0.83 | 0.77 | 0.91 |
| NYAM_bundle | 0.16 | 0.23 | 0.02 | 0.02 | 0.18 | 0.02 |
For the SHADOW-2 lines the error rates are small only because the rule almost never decides; for the NYAM bundle the nominal .10 is NOT delivered: at the design truth it reaches CONTRADICTED on 0.23 of paths (the z test is repeated every week from week 13: 90 looks at -2 SE inflate the false-reject rate) and at zero truth it declares CONSISTENT on 0.16.

## 5. Pooled five-line SPRT and alternatives (joint calendar weeks, same truths for all five lines)
| truth | alpha = beta | wk 26 CONS / CONTRA | wk 52 CONS / CONTRA | wk 104 CONS / CONTRA | median-ish weeks to decision (decided share) | fixed-sample z at wk 52: supports (z0 > 1.645) / contradicts H1 (z < -1.645) |
|--|--|--|--|--|--|--|
| (i) 2026 research mean | 0.10 | 0.31 / 0.00 | 0.83 / 0.00 | 1.00 / 0.00 | 37 (100%) | 0.92 / 0.00 |
| (i) 2026 research mean | 0.20 | 0.65 / 0.00 | 0.95 / 0.00 | 1.00 / 0.00 | 24 (100%) | 0.93 / 0.00 |
| (ii) half of it (= H1) | 0.10 | 0.06 / 0.01 | 0.27 / 0.02 | 0.61 / 0.03 | 58 (64%) | 0.39 / 0.02 |
| (ii) half of it (= H1) | 0.20 | 0.26 / 0.03 | 0.54 / 0.07 | 0.80 / 0.11 | 42 (88%) | 0.40 / 0.02 |
| (iii) zero | 0.10 | 0.01 / 0.12 | 0.02 / 0.37 | 0.04 / 0.69 | 53 (73%) | 0.03 / 0.41 |
| (iii) zero | 0.20 | 0.05 / 0.23 | 0.10 / 0.55 | 0.14 / 0.82 | 42 (92%) | 0.03 / 0.42 |
| (iv) regime-off (pre-2026 mean) | 0.10 | 0.01 / 0.06 | 0.05 / 0.22 | 0.12 / 0.45 | 56 (57%) | 0.07 / 0.26 |
| (iv) regime-off (pre-2026 mean) | 0.20 | 0.10 / 0.13 | 0.19 / 0.35 | 0.30 / 0.58 | 45 (84%) | 0.07 / 0.26 |
| (v) selection-deflated (DIS-T A, ALL) | 0.10 | 0.00 / 0.60 | 0.00 / 0.94 | 0.00 / 1.00 | 30 (100%) | 0.00 / 0.95 |
| (v) selection-deflated (DIS-T A, ALL) | 0.20 | 0.01 / 0.74 | 0.01 / 0.97 | 0.01 / 1.00 | 22 (100%) | 0.00 / 0.95 |
(The pooled CONTRA column includes the z rule from week 26 with n >= 30 on the pooled mean.) Sensitivity: sampling weeks only from 2026 (higher rates for DIS-B / DIS-E; 43-week pool) changes the single-line numbers little: P(CONSISTENT by 104) under the 2026 truth Q13 0.96, DIS-K 0.96, DIS-B 0.23, DIS-E 0.70, DIS-C 0.03.

## 6. Is alpha = beta = .10 sensible, and a better monitoring rule (text proposal, nothing implemented)
Not per line. At 1-2.3 trades a week and 6.9 / 82 points of signal-to-noise, a per-line SPRT needs 340-1,000 trades; the design point is only reachable for the pooled bundle. Proposal: (1) monitor the five SHADOW-2 lines as ONE equal-risk sleeve (the DIS-T finding that they are nearly independent: pooled information about 5 x the single line); run one SPRT on the pooled trade stream with alpha = beta = .20 (bounds +-1.386) and H1 = half the pooled 2026 research mean, which decides in about 42 weeks at the design truth (88% decided within 104 weeks; vs 64% at alpha = .10), at the price of 14% false CONSISTENT at zero truth by week 104. (2) Replace the repeated weekly z test by a LATCHED rule evaluated at fixed looks (weeks 26, 52, 104) with a one-sided boundary (e.g. z < -2.5 at wk 26, -2.3 at wk 52, -2.0 at wk 104 against H1) so that 90 looks do not inflate the error. (3) Report the pooled mean and its 90% interval every Monday instead of a verdict word: at one year the pooled sleeve resolves a mean of the 2026 level from zero (fixed-sample z0 > 1.645 on 0.92 of paths if the 2026 mean is true) but not H1 from zero (0.39). (4) Latch the first SPRT crossing in a state file (see section 7). (5) Treat a line that has not produced >= 30 trades by week 26 as INCONCLUSIVE by design and re-read the pooled sleeve instead. (6) For the NYAM bundle the same latched-looks z rule, because its weekly z test over 90 looks gives 0.23 false CONTRADICTED at the design truth.

## 7. Monday table check (crafted registers through shadow2_weekly.rows_for; the real code)
| case | week used | n | llr | z vs H1 | printed verdict |
|--|--|--|--|--|--|
| 1 no trades, week 30 | 30 | 0 | 0.0 | None | no data yet |
| 2 five small trades, week 12 | 12 | 5 | -0.0 | -0.11 | EARLY (keep logging) |
| 3 40 trades mean 7 sd 80, week 25 | 25 | 40 | 0.14 | 0.01 | EARLY (keep logging) |
| 3b same trades, week 26 | 26 | 40 | 0.14 | 0.01 | INCONCLUSIVE (keep logging) |
| 4 40 trades all -40, week 25 (z far below -2) | 25 | 40 | -1.76 | -3.59 | EARLY (keep logging) |
| 4b same, week 26 | 26 | 40 | -1.76 | -3.59 | CONTRADICTED |
| 5 29 trades all -40, week 26 (n < 30) | 26 | 29 | -1.28 | -3.06 | INCONCLUSIVE (keep logging) |
| 6 60 trades all +80, week 5 (upper bound) | 5 | 15 | 1.16 | 3.43 | EARLY (keep logging) |
| 7a winners then losers: read at week 12 | 12 | 36 | 2.79 | 5.31 | CONSISTENT |
| 7b same, read at week 20 | 20 | 48 | 1.29 | 1.94 | EARLY (keep logging) |
| 8 last trade in week 20, calendar week 30, week taken from sim.ld.max() | 20 | 20 | -0.05 | None | EARLY (keep logging) |
| 8b same register, week 30 forced | 30 | 20 | -0.05 | -0.32 | INCONCLUSIVE (keep logging) |
Reading: **no data and EARLY are handled correctly** (n = 0 prints "no data yet" at any week; EARLY until week 25, INCONCLUSIVE from week 26; the z rule needs week >= 26 AND n >= 30: 29 trades or week 25 stay undecided even at z = -3.6). Three issues: (a) **the display is not latched** (case 7: CONSISTENT at week 12, EARLY again at week 20 after losses): a Wald SPRT stops at the first crossing, the table re-evaluates the cumulative llr each Monday, so CONSISTENT/CONTRADICTED can appear and disappear; (b) **the week index is the week of the last trade in the register, not the calendar week** (case 8: a register whose last trade is in week 20 prints EARLY at calendar week 30, INCONCLUSIVE only if the week is forced); a quiet fortnight postpones the week-26 switch; (c) CONTRADICTED means "significantly below H1 (half the research mean)", not "loses money". Also: the fade and NYAM runners use week 13 for the z rule while SHADOW-2 uses week 26 (and n >= 30), so the same word has a different meaning in different rows. Nothing was changed (these are findings; fixes only on request).

## Limits
* The bootstrap resamples 187 weeks of history, so forward draws cannot contain regimes outside 2023-26; shifting every trade by a constant keeps the dispersion of the history (the 2026 sd is above the full-history sd for several lines, so the true llr increments are noisier than the sd the rule assumes). * Truth (v) uses DIS-T estimator A at 1 lot over ALL weeks converted to points per trade by the pool's trades/week. * BT flip uses a different (flag-count) rule and was not simulated. * The weekly looks are Mondays on cumulative trades, as coded; intra-week looks are not modelled.
