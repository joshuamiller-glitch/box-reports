# REPORT Q5ENS - macro12 monthly cross-sectional momentum, the whole 12-cell grid as ONE ensemble book

**LEAD-weak (not FOUND-PENDING): ensemble pair-window Sharpe 0.87; additive uplift at 20% share 0.22/0.16/0.02 on clean/H1/H2 (all-in 0.18) - H2 +0.02 fails the +0.10 gate; plateau on the ensemble weights 1.00 (7 of 7 leave-one-group-out books keep >= 75%); hedge-claim circular-shift null passes (rank 0.96, wd corr -0.39); bootstrap lower bound only +0.01 at 10-20% and negative at 30-50%; fails the conservative own null (higher of ensemble p95 0.39, single-cell p95 0.73, Bonferroni 98.75th pct 1.12); modern-era replication holds in 1 of 3 (alternating months); ERA FLAG positive pre-2023 (2013-22 Sharpe gross 0.41 / fixed-cost 0.32 / price-scaled 0.33).** FOUND 0.

Pre-registered in PREREG_AUTOPILOT.md ("Q5 GRID ENSEMBLE BOOK") before it was run. Book = equal-risk (1/clean weekly vol) average of all 12 Q5 cells (macro12 = ES NQ RTY ZN ZB GC CL 6E 6J 6B 6A HG; cross-sectional momentum z = (c_t - c_(t-L))/(ATR20 sqrt L), L in 15/20/25/30 days, long top-k / short bottom-k, k in 2/3/4, month-end rebalance, entry next open, 19-day hold); no selection among the 12 cells. Family accounting: Q5, Q10 (commodities), R9 (20d, k=3/5) and Q3 (63-252 day) count as ONE family (four sub-families considered). Fill model: next-open entry, exit close of day t+19, 1 tick/side + commission (T4 A table), 2x slippage = 2 ticks. Baseline B.Cfg(wk_floor=8, wk_loss_pb=None). Selection on clean not needed (no selection); scale = pair clean vol using the book's clean vol. Library: Q5_grid_ensemble (lib_save.save_book).

## Standalone and nulls
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| BOOK | 0.32 | 7 | 1.06 | 1.34 | -0.10 | 0.87 | 0.42 | 0.39 | 1.00 | 0.19 | 0.96 |

Nulls (pair-window standalone Sharpe): real 0.87; independent-replicate ensemble p95 0.39 (105 draws, understates the null because independent random books diversify); single-cell random-entry p95 0.73 (conservative; rank of the real book 0.97); Bonferroni (1-0.05/4) 1.12. Gate (pre-registered max of the three): FAIL.

## Additive framing, constant-risk, plateau, 2x slippage
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BOOK | 2.5 | 10% | 0.12 | 0.09 | 0.02 | 0.10 | 3 | 0.01 | 0.96 | -0.39 | -0.14 | NO |
| BOOK | 2.5 | 20% | 0.22 | 0.16 | 0.02 | 0.18 | 12 | 0.00 | 0.96 | -0.39 | -0.14 | NO |
| BOOK | 2.5 | 30% | 0.31 | 0.21 | 0.01 | 0.24 | 22 | -0.02 | 0.96 | -0.39 | -0.14 | NO |
| BOOK | 2.5 | 50% | 0.42 | 0.24 | -0.06 | 0.31 | 41 | -0.11 | 0.96 | -0.39 | -0.14 | NO |

| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| BOOK | 10% | -5.6 | 6.3 | 7.2 | 14.6 | 6/6 | 4/13 | NO |
| BOOK | 20% | -11.2 | 6.3 | 12.4 | 28.7 | 6/10 | 8/25 | NO |
| BOOK | 30% | -16.7 | 6.1 | 14.6 | 34.4 | 5/11 | 13/32 | NO |
| BOOK | 50% | -27.9 | 5.8 | 17.4 | 38.3 | 5/10 | 13/16 | NO |

| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| BOOK | 0.18 | 7 | 1.00 | 0.14 / 0.18 | 0.21 / 0.14 / 0.00 / 0.17 | 0.79 | 0.22 / 0.20 / -0.00 / 0.17 |

Leave-one-group-out books (all-in uplift @20%): dropL15 0.24, dropL20 0.19, dropL25 0.14, dropL30 0.15, dropk2 0.18, dropk3 0.18, dropk4 0.17 (base 0.18).

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BOOK | clean | 1.06 | 962,705 | -167,953 | -110,520 | -95,290 | 248,752 | 1.80 | 3.87 | 34 | 1.77 | -100,557 | -91,267 | 252,727 | 6.41 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| BOOK | H1 | 1.34 | 250,664 | -143,938 | -105,653 | -85,472 | 230,193 | 2.01 | 1.09 | 32 | 3.03 | -91,820 | -71,392 | 143,745 | 4.65 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| BOOK | H2 | -0.10 | -26,579 | -130,606 | -106,403 | -86,992 | 312,054 | -0.14 | -0.09 | 46 | 2.27 | -79,900 | -77,657 | 205,607 | 3.66 | 43 | 2.26 | -82,524 | -81,089 | 217,425 |
| BOOK | all | 0.87 | 1,186,790 | -167,953 | -114,213 | -94,650 | 312,054 | 1.41 | 3.80 | 37 | 2.10 | -100,557 | -89,178 | 252,727 | 12.03 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |


## Modern-era replication (GATE AMENDMENT 2; ES/RTY not applicable to a macro book -> alternating months, H0, disjoint market halves)
| test | result | holds (same sign and >= 50% of all-in uplift 0.18) |
|---|---|---|
| H0 2023-02..07 | uplift 0.01 | False |
| alternating months 2023-26 | odd months 0.19, even months 0.18 | True |
| disjoint macro12 halves, k=2, L grid | half A (ES NQ ZN GC 6E HG) all-in 0.16 (pair-window Sharpe 1.03); half B (RTY ZB CL 6J 6B 6A) all-in 0.05 (Sharpe 0.10) | False |
| live weeks | none yet | pending |

One of three holds (alternating months); two are needed. The momentum effect is concentrated in half A (equity/gold/euro/copper/bonds mix); half B shows almost none.

## Reading
The family survives the plateau test as an ensemble (it was a spike for the single Q5 cell at 19 days / k=3), has a negative worst-decile correlation and passes the hedge shift null, and the 2013-22 flag is positive (fixed-cost Sharpe 0.32), so it is not a modern-only artefact. What fails is magnitude and breadth: the H2 uplift is nil, the bootstrap lower bound hugs zero, the ensemble Sharpe 0.87 does not beat the Bonferroni-corrected null, and the effect does not replicate on half the markets. Monthly rebalance means ~38 independent decisions in the pair window. Status: LEAD-weak; re-score on the weekly extension.

## Executability (G7)
NT8 monthly rebalance script over 12 outright futures (micro contracts MES/MNQ/M2K/MGC/MCL for granularity; ZN/ZB/6x/HG outrights), long top-k/short bottom-k by 15-30 day z, 19-day hold, ATR20 risk sizing; margin at 20% share modest; separate account not required (different instruments than the NQ pair).

DONE Q5ENS
