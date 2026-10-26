# REPORT ENSEMBLE - METHOD-2 item 8 and follow-up 1: equal-risk ensemble of the pair's own factor vs the live pair, now WITH the live account layer (2026-10-17; DESCRIPTIVE, NOT a PASS)

**Verdict (unchanged): not a replacement candidate.** With the live account layer applied to the ensemble (combined day lock cap 8R / arm 2R / give back 67% from 00:00, week floor -8R, per-book 5R/-2R, R = $9,600, minute-resolution marks) the equal-risk ensemble of the ST + HM + WT-10 grids in ONE account earns the live pair's return (OOS Sharpe 2.00 vs 2.10, net $2.64M vs $2.62M, 142 OOS weeks 2024-02..2026-10-16) and the same worst week (-97k vs -83k; the -8R week floor binds), but its max drawdown is still 376k against 280k, and the paired Sharpe-difference 90% interval is [-1.03, +0.85]: it does not exclude under-performance. The lock layer closes the tail gap that Part 1 showed (DD $374-455k -> 376k; worst week -$134k..-150k -> -97k) except for the drawdown. One-account is clearly better than separate accounts (Sharpe 1.26 for three separate accounts). Realisable 10-instance integer version: Sharpe 2.19, DD 276k (as good as the pair on point estimates, but the 3- and 5-instance versions are at 1.60 and the interval is as wide: the difference between 3, 5 and 10 instances is noise).

## What was built (account layer on the ensemble)
- Trade lists: every cell of the CONTROL grids (ST 229, HM 229, WT-10 270; a027 / intraday-other) re-run from parameters through the NT8-faithful engines (nt8sim.acct for ST and HM single-book accounts, WT 1-second trades) and stored as rows with minute entry/exit, side and points (outputs/methods2/acct_rows.pkl, 728 cells, ap_m2_acct_rows.py). Per-cell per-book rule 5R/-2R applied at each cell's full size (scale-invariant).
- Ensemble stream: in each 12/3/3 fold the tilt weights come from the FIT window (harness rule on the cell series of the matrices), families are scaled equal-risk to the pair's fit-window daily SD, then one global scale s is set so that the LOCKED ensemble's fit-window daily SD equals the pair's (s median 1.09 for the fractional version: the locks remove risk); the read window uses the frozen weights; rows are merged with fractional weights and passed through the combined day lock and week floor on 1-minute marks (ap_m2_acct.lock_arr, a vectorised copy of b11_nt8.lock_stage; validated: merged live ST-only + HM-only cells through it give 1.61/2.61/2.38/1.95 with net $3.05M vs the R.acct stack's identical-rule run 1.61/2.61/2.38/1.95, $3.06M).
- NOT modelled: lot netting and orphan exits ACROSS cells (each cell's rows come from its own single-book account run). On the pair itself this costs about +0.1 Sharpe in the optimistic direction in clean/H2 and -0.2 in H1 (merged no-netting 1.61/2.61/2.38/1.95 vs netted 1.46/2.83/2.48/1.90), net +3%: the account-layer numbers below are therefore 'A-lite' (locks yes, cross-cell netting no).
- Fractional weights ARE supported by the layer (the 'signal-average' version = all cells with their tilt weights, row size = weight x 8-lot rows); the integer versions take the top-n cells by fit-window Sharpe (at most ceil(n/families) per family) at max(1, round(s x 16 / n)) contracts each.
- Sets: E0 = ST + HM + WT-10 grids (the pre-specified live mechanism); E3 = ST + HM grids. E1 (6,656 cells incl. the T3S1 G chunks) NOT run: those books are library series from the b10 engine without trade lists in this format (re-running them is a separate build); E1's per-book-rules result is in Part 1.
- Accounts: A = all families in one account with the combined locks; B = one account per family (locks at the family's risk share: cap/arm/floor x 1/3); C = ST+HM in one account (share 2/3), WT-10 in its own (1/3). Same fit-window scale in all three so that they compare at equal sizing.

## Results on the concatenated OOS (2024-02..2026-10-16, 142 weeks), live pair for reference
| set | version | account | Sharpe | net | max DD | worst week | CVaR5 | % neg wk | halves Sharpe (h1 / h2) | paired weekly-mean diff 90% CI ($/wk) | Sharpe-diff 90% CI | corr with pair |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE PAIR | 2 cells | one account | 2.10 | $2.62M | 280k | -83k | -79k | 41 | 1.76 / 2.39 | - | - | 1.00 |
| E0 | fractional tilt weights (signal-average) | A | 2.00 | $2.64M | 376k | -97k | -81k | 41 | 1.79 / 2.16 | [-8,539, +9,276] | [-1.03, +0.85] | +0.57 |
| E0 | fractional tilt weights (signal-average) | B | 1.26 | $1.33M | 368k | -80k | -78k | 49 | 0.68 / 1.69 | [-16,785, -1,286] | [-1.80, +0.10] | +0.59 |
| E0 | fractional tilt weights (signal-average) | C | 1.28 | $1.47M | 553k | -79k | -78k | 48 | 0.21 / 2.09 | [-15,021, -415] | [-1.71, +0.11] | +0.57 |
| E0 | 10 instances, integer contracts | A | 2.19 | $2.52M | 276k | -80k | -78k | 37 | 1.59 / 2.62 | [-8,496, +7,136] | [-0.82, +1.04] | +0.57 |
| E0 | 10 instances, integer contracts | B | 1.65 | $1.49M | 231k | -76k | -62k | 44 | 1.75 / 1.58 | [-15,409, -895] | [-1.42, +0.49] | +0.54 |
| E0 | 10 instances, integer contracts | C | 1.44 | $1.50M | 324k | -81k | -71k | 43 | 0.83 / 1.88 | [-15,264, -169] | [-1.59, +0.28] | +0.57 |
| E0 | 5 instances, integer contracts | A | 1.60 | $2.10M | 323k | -80k | -78k | 46 | 1.21 / 1.91 | [-12,507, +5,336] | [-1.45, +0.44] | +0.45 |
| E0 | 5 instances, integer contracts | B | 1.28 | $1.24M | 354k | -80k | -71k | 45 | 0.58 / 1.82 | [-16,959, -2,309] | [-1.74, +0.12] | +0.48 |
| E0 | 5 instances, integer contracts | C | 1.71 | $1.99M | 275k | -80k | -78k | 46 | 1.73 / 1.66 | [-13,056, +4,222] | [-1.40, +0.61] | +0.42 |
| E0 | 3 instances, integer contracts | A | 1.60 | $2.08M | 322k | -79k | -78k | 42 | 1.05 / 2.08 | [-13,276, +5,288] | [-1.50, +0.45] | +0.42 |
| E0 | 3 instances, integer contracts | B | 1.46 | $1.45M | 288k | -78k | -70k | 47 | 1.33 / 1.55 | [-15,893, -77] | [-1.60, +0.38] | +0.41 |
| E0 | 3 instances, integer contracts | C | 1.36 | $1.50M | 321k | -80k | -74k | 45 | 1.20 / 1.48 | [-15,711, +68] | [-1.71, +0.18] | +0.44 |
| E3 | fractional tilt weights (signal-average) | A | 1.91 | $2.53M | 481k | -79k | -78k | 39 | 1.44 / 2.28 | [-8,251, +7,776] | [-1.03, +0.74] | +0.67 |
| E3 | fractional tilt weights (signal-average) | B | 1.72 | $2.01M | 349k | -79k | -78k | 43 | 1.62 / 1.78 | [-10,842, +2,179] | [-1.15, +0.35] | +0.74 |
| E3 | 10 instances, integer contracts | A | 1.31 | $1.81M | 525k | -82k | -79k | 44 | 0.93 / 1.60 | [-13,618, +2,377] | [-1.65, +0.05] | +0.53 |
| E3 | 10 instances, integer contracts | B | 2.03 | $2.44M | 297k | -81k | -78k | 42 | 1.51 / 2.43 | [-8,554, +6,452] | [-0.91, +0.82] | +0.55 |
| E3 | 5 instances, integer contracts | A | 1.61 | $2.19M | 335k | -80k | -79k | 42 | 1.22 / 1.96 | [-11,659, +5,252] | [-1.41, +0.43] | +0.52 |
| E3 | 5 instances, integer contracts | B | 1.31 | $1.54M | 518k | -82k | -79k | 49 | 0.68 / 1.92 | [-15,707, +683] | [-1.72, +0.14] | +0.55 |
| E3 | 3 instances, integer contracts | A | 1.01 | $1.42M | 556k | -81k | -79k | 45 | 0.74 / 1.25 | [-17,780, +754] | [-2.06, -0.17] | +0.47 |
| E3 | 3 instances, integer contracts | B | 1.06 | $1.26M | 400k | -80k | -78k | 47 | 0.96 / 1.13 | [-17,285, -1,848] | [-1.94, -0.15] | +0.49 |

Dollars are 8/8-pair dollars (6/6 = 0.75x). E3 account C is identical to A (one group).

## Reading
1. **Return and risk with the locks.** One-account fractional E0 matches the pair's return and worst week; its drawdown is 34% larger ($376k vs $280k). I did not diagnose which weeks drive the extra drawdown; the likely reasons are (i) no lot netting across the 728 cells in this A-lite layer and (ii) the ensemble's slower response to a regime break because its tilt weights are frozen for the 3-month read window.
2. **Instances.** The realisable versions scatter between Sharpe 1.01 (E3, 3 instances) and 2.19 (E0, 10 instances) with the same paired interval width (about 1.8 Sharpe): at 142 weeks the OOS data cannot rank a 3-, 5- and 10-instance implementation; the 10-instance E0 point estimate (Sharpe 2.19, DD $276k, worst week -$80k) is the only variant that matches the pair on every tail metric, and it is one of 24 reported variants.
3. **Accounts.** B (separate accounts) loses 0.4-0.7 Sharpe against A for E0 (fractional 1.26 vs 2.00; 10 instances 1.65 vs 2.19) and C (WT-10 apart) is no better than A (1.28): in this layer the WT-10 grid does not add anything to ST+HM and splitting it off does not recover what it costs (E3 A 1.91 vs E0 A 2.00). The pair's own evidence agrees (two accounts 1.75 vs one account 2.05, worst week -$155k vs -$83k).
4. **Pre-registered decision rule (ENSEMBLE_DESIGN section 6; follow-up wording: replacement candidate only if the paired interval excludes underperformance AND tails no worse):** every variant has a paired Sharpe-difference lower bound of -0.8 or lower and a weekly-mean difference interval that straddles zero from below (-$8k..-$17k per week lower bounds): FAIL. Tails no worse than the pair: only E0 INT10/A on the point estimates, not the fractional ensemble.
5. **Caveats.** Cross-cell lot netting and orphan exits are not modelled (A-lite); the pair-level comparison with netting (pair 1.46/2.83/2.48/1.90 vs merged no-netting 1.61/2.61/2.38/1.95) shows the direction is small; the per-cell rows are the control grids' single-book accounts, not signal-averaged orders; scale s was set on the locked fit-window SD (conservative against the ensemble's Sharpe being inflated by sizing).

## PART 1 - per-book rules only (earlier run; the grids carry their own single-book locks, no combined account locks)
## Set-up
- OOS: 12 / 3 / 3, rule tilt, first OOS week 2024-02, 142 weeks, concatenated 2024-02..2026-10-16 (halves 2024-02..2025-04 and 2025-05..2026-10). Each member family's tilt-weighted ensemble is scaled FOLD-WISE (fit window only, no look-ahead) so that its fit-window daily SD equals the live pair's fit-window daily SD; the ensemble of F families is the average of those series, rescaled again to the pair's fit-window SD. Dollars are 8/8-pair dollars; 6/6 = 0.75x.
- Members: E0 = the pre-specified live mechanism's grids (CTRL_ST 229 cells, CTRL_HM 229, CTRL_WT10 270; intraday-other / a027); E1 = E0 + every family with gates a-d passing and OOS correlation with the pair >= 0.5 that is not a pair overlay (T3S1_BOOKS_B B_ST / B_HM / B_WT; T3S1 G-family 5-min trend chunks G1-G6; CTRL_PAIR): 23 families in total with the three controls; E2 = the gates-a-d families only; E3 = ST + HM grids only. Overlay deltas (D2E9, D1F8, ...) are excluded: they modify the pair, they are not separate books.
- Book count: E0 728 cells; E1 6656 cells; independent bets (a778's F_CLUSTERS at OOS corr >= 0.5): E1 1-2, i.e. ONE factor represented by many cells.

## Comparison on the concatenated OOS (equal fit-window risk)
| book | cells | OOS Sharpe | net | max DD | worst week | CVaR5 | % neg wk | halves Sharpe (h1 / h2) | paired weekly-mean diff 90% CI ($/wk) | Sharpe-diff 90% CI | corr with pair |
|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE PAIR (library PAIR; 2 cells) | 2 | 2.05 | $2.56M | 280k | -83k | -79k | 42 | 1.76 / 2.30 | - | - | 1.00 |
| pair without daily rules (week floor kept) | 2 | 1.41 | $2.51M | 497k | -92k | -83k | 46 | - | - | - | - |
| E0 ST+HM+WT-10 grids (pre-specified live mechanism) | 728 | 1.93 | $2.49M | 422k | -150k | -119k | 37 | 1.49 / 2.28 | [-8,444, +7,766] | [-1.05, +0.86] | +0.64 |
| E1 = E0 + gates-a-d trend families in the pair factor | 6656 | 1.95 | $2.55M | 449k | -146k | -113k | 38 | 1.33 / 2.43 | [-8,218, +7,554] | [-0.95, +0.73] | +0.68 |
| E2 gates-a-d trend families only | 6386 | 1.95 | $2.56M | 455k | -143k | -112k | 38 | 1.34 / 2.43 | [-8,113, +7,540] | [-0.93, +0.73] | +0.68 |
| E3 ST+HM grids only | 458 | 2.12 | $2.78M | 374k | -134k | -110k | 36 | 1.73 / 2.45 | [-5,122, +8,400] | [-0.69, +0.92] | +0.74 |

Reading: at equal risk the ensemble earns the pair's return (the paired intervals straddle zero in every set; the probability that the ensemble beats the pair on weekly mean is 0.45-0.62), so spreading the parameter risk costs nothing in return. What it does not reproduce is the pair's tail protection: the live pair's combined day lock (cap 8R, give-back 67% from 00:00) and week floor (-8R) live in the account layer and are NOT in the grid cells (the control grids carry the per-book rules only). The pair without the daily rules has max DD $497k and Sharpe 1.41; the ensemble sits between (DD $374-455k, Sharpe 1.9-2.1). If the same locks removed the same share of drawdown at ensemble level (pair: $497k -> $280k, 44%), the ensemble DD would be about $210-250k: this is an extrapolation, NOT a measurement (the locks need trade-level minute equity of every member cell, which the matrices do not carry).

## Members' own numbers (E1)
| family | OOS Sharpe (own, at pair risk) | OOS corr with pair |
|---|---|---|
| CTRL_HM | 2.19 | +0.61 |
| CTRL_PAIR | 1.80 | +0.84 |
| CTRL_ST | 1.60 | +0.72 |
| CTRL_WT10 | 0.51 | +0.10 |
| T3S1_BOOKS_B:B_HM | 1.98 | +0.57 |
| T3S1_BOOKS_B:B_ST | 1.92 | +0.66 |
| T3S1_BOOKS_B:B_WT | 1.84 | +0.51 |
| T3S1_G_G_v1:G_G1@NQMNQCM#1 | 1.81 | +0.56 |
| T3S1_G_G_v1:G_G1@NQMNQCM#2 | 1.55 | +0.57 |
| T3S1_G_G_v1:G_G1@NQMNQCM#3 | 1.68 | +0.57 |
| T3S1_G_G_v1:G_G1@NQMNQCM#4 | 1.65 | +0.61 |
| T3S1_G_G_v1:G_G1@NQMNQCM#5 | 1.41 | +0.61 |
| T3S1_G_G_v1:G_G1@NQMNQCM#6 | 1.49 | +0.60 |
| T3S1_G_G_v1:G_G2@NQMNQCM#1 | 1.57 | +0.53 |
| T3S1_G_G_v1:G_G3@NQMNQCM#1 | 1.90 | +0.63 |
| T3S1_G_G_v1:G_G3@NQMNQCM#2 | 1.97 | +0.61 |
| T3S1_G_G_v1:G_G3@NQMNQCM#3 | 1.44 | +0.57 |
| T3S1_G_G_v1:G_G4@NQMNQCM#1 | 1.97 | +0.61 |
| T3S1_G_G_v1:G_G4@NQMNQCM#2 | 1.84 | +0.56 |
| T3S1_G_G_v1:G_G5@NQMNQCM#1 | 1.63 | +0.51 |
| T3S1_G_G_v1:G_G5@NQMNQCM#2 | 1.05 | +0.54 |
| T3S1_G_G_v1:G_G6@NQMNQCM#1 | 1.88 | +0.63 |
| T3S1_G_G_v1:G_G6@NQMNQCM#2 | 1.40 | +0.54 |

Drift check (ap_m2_beta.py, outputs/methods2/beta_check_passers.csv): all of these trend families have OOS weekly correlation with the index of -0.10..+0.05 (beta-explained Sharpe <= 0.08), so the sign-flip family null and a drift-matched null agree and the library scoring of ST, HM, WT, B7, B1 and the T3S1 G chunks re-scores the same.

## Accounts: one account (A) vs separate accounts (B) vs hybrid (C)
What the NT8 account layer does (my layer, ap_x_pair.account; verified against the live pair 1.46/2.81/2.54): ONE account nets the strategies' orders into one position (FIFO lots: an entry on the opposite side closes the oldest opposite lot at the entry price without a second round trip; a bracket exit with no same-side lot opens an orphan position on the other side; session flat closes all lots) and the combined day/week locks act on the account's marked equity. SEPARATE accounts have no netting and no orphans (each account's P&L is the strategy's stand-alone P&L), margin is per account, and a combined lock across accounts does not exist in NT8 (each account's strategy sees only its own equity).
Measured on the pair itself over the same OOS weeks (ST and HM as two accounts = the library's stand-alone ST and HM series summed, each with its own locks, vs the one-account pair):
| | Sharpe | net | max DD | worst week | CVaR5 |
|---|---|---|---|---|---|
| A: one account (live pair) | 2.05 | $2.56M | 280k | -83k | -79k |
| B: ST account + HM account (summed) | 1.75 | $2.73M | 348k | -155k | -139k |

Separate accounts cost Sharpe (-0.3), drawdown (+24%) and the worst week (nearly 2x), at a similar net: the tail protection comes from netting between the two books and from the combined locks, both of which exist only in one account. For the ensemble this argues for A: all trend instances in ONE account with the combined locks, WT-10-type books in a second account (the earlier WT test: as a third book in the pair's account the uplift disappeared through netting/orphans, 1.29-1.94 vs 1.86; in a separate account 2.0-2.6). C (hybrid) = trend instances that load on the pair's factor in the pair's account; books with different factor (WT-10, RW/K4-type) in a second account. A cell-level simulation of A/B/C for the ensemble needs the merged trade lists of every member cell (not stored in the family matrices): not done; the pair evidence above is the measurement.

## Realisable instances with integer contracts
Fold-wise, fit-window information only: the best cell (fit Sharpe) of each member family, the top n of those, contracts = round(m x 16 / n) (>= 1) with m set so that the unrounded ensemble's fit SD equals the pair's fit SD (16 contracts = 8/8).
| n instances | contracts per instance (median) | Sharpe | net | max DD | worst week | corr with pair | weekly-mean diff vs pair 90% CI |
|---|---|---|---|---|---|---|---|
| 3 | 6 | 1.46 | $1.67M | 586k | -126k | +0.21 | [-18,600, +5,350] |
| 5 | 4 | 1.03 | $1.29M | 536k | -155k | +0.36 | [-21,339, +2,515] |
| 10 | 2 | 1.39 | $1.70M | 430k | -163k | +0.47 | [-16,706, +3,634] |

Picking a handful of cells by fit-window Sharpe throws away the diversification and the factor: Sharpe 1.0-1.5 against 2.05 for the pair and 1.9-2.1 for the full equal-risk ensemble, correlation with the pair only 0.2-0.5. A realisable ensemble therefore has to be implemented as a signal-average (one strategy instance trading the average direction/size of the grid, or many small instances), not as a few best cells; integer rounding of a 1/N-weighted vote at 8/8 size needs roughly N >= 16 instances of 1 contract.

## Decision rule (ENSEMBLE_DESIGN section 6) and status
1. Paired Sharpe-difference 90% CI lower bound > -0.25: FAIL for every set (lower bounds -0.69..-1.05); the intervals are wide because 142 weeks cannot separate Sharpes that differ by < 0.5.
2. At least one of max DD -15%, worst week -10%, CVaR5 -10% versus the live pair: FAIL as measured (the unlocked ensemble is worse on all three); would need the account-level locks, not measured.
3. Integer-rounded 5-instance version keeps >= 80% of the fractional Sharpe: FAIL (1.03 vs 1.95 for E1).
Not a replacement candidate on the evidence in hand. What would change it: (i) the ensemble run through the account layer with the combined day lock and week floor on minute equity (needs the member cells' trade lists: the T3S1 / B-series cells can be re-run with trades kept), (ii) a signal-average implementation that preserves the diversification at integer sizes.



DONE ENSEMBLE
