# REPORT PX34 (N3R: cure attempt of the N3 VX-curve lead)

**NO - the fresh pre-registered ladder cure does not reproduce N3: selected cell PX34_ladder_h2_k1.0 (VX F2/F1-1 ladder 0.01/0.02/0.03/0.04, long NQ next open, hold 2d, 1.0 ATR stop): additive uplift at 20% +0.08/+0.11/+0.26 (clean/H1/H2), clean below the +0.10 gate at 10/20% and H1 below at 10%, worst week +54% vs 20% allowed, bootstrap lo -0.06, own null rank 0.80 (needs 0.95), long-only null rank 0.74, 2x slippage fail, wd corr 0.31; plateau passes (4/4 neighbours) but only because the uplift is uniformly small; replication 1 of 3 testable (ES+RTY hold, H0 +0.01 and alternating months fail). N3 stays a LEAD at best; the long-equity-beta explanation (ladder = all-days-long, 0.81 vs 0.79) is now the better reading. FOUND 0.**

## Pre-registration and disclosure
Registered in PREREG_AUTOPILOT.md ('PX34 N3R') at 2026-10-16 ~23:00Z before the first run: 4 cells (hold {1,2} x stop {none,1.0 ATR}, ladder L=0.02 fixed), clean-only selection, plateau = one-at-a-time perturbation of L and stop x{0.75,1.25} (>= 75% of neighbours keep >= 75% of uplift), replication legs defined up front. Non-virgin spans for the parent lead: clean, H1, H2 and ES/RTY 2023-26 were all read in REPORT_N3 and the 0.03 level and the idea come from that reading; only H0 and the alternating-month design were unread by the parent. Variant results on H1/H2 are therefore non-virgin; no rerun was done, no cell was added after the run. Runtime 21 s (4 cells, 200 + 200 + 200 replicates).

Why the two changes (ladder, stop) were meant to cure the parent failures: plateau (binary 0.03 cut -> continuous ladder) and worst week (long-beta tail -> ATR stop). Result: the plateau failure is cured on paper but the uplift it was protecting is not there; the worst week is still worse than the share (sleeve worst week -226k clean vs pair -82k; ww change +27/54/81/136% at 10/20/30/50% against the allowed 10/20/30/50%).

Fill model: entry at the open of the label day after the VX settle; time exit at the close of day t+hold; stop at pe - kst*ATR20 (gap-through at the open); 1 tick/side + T4 daily commission; 2x slippage = 2 ticks; overlapping trades allowed; back-adjusted prices, extra round trip on a roll inside a trade. VX signal: F2/F1-1 of the two nearest alive VX months with volume (data/databento/B10/vx_1d, 2018-11-04..2026-10-12).

## Development (clean, selection only)
| cell                |   trades_legs |   pairwin_entry_days |   sh_clean |   sh_H1 |   sh_H2 |   sh_pairwin | elig   |
|:--------------------|--------------:|---------------------:|-----------:|--------:|--------:|-------------:|:-------|
| PX34_ladder_h1_k0.0 |          2694 |                  363 |       0.64 |    1.75 |    2.39 |         1.04 | True   |
| PX34_ladder_h1_k1.0 |          2694 |                  363 |       0.64 |    1.63 |    2.08 |         0.95 | True   |
| PX34_ladder_h2_k0.0 |          2694 |                  363 |       0.59 |    1.26 |    1.77 |         0.81 | True   |
| PX34_ladder_h2_k1.0 |          2694 |                  363 |       0.68 |    0.05 |    1.8  |         0.81 | True   |

## Standalone and nulls
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PX34_ladder_h2_k1.0 | 0.53 | 3 | 0.68 | 0.05 | 1.80 | 0.81 | 0.61 | 1.12 | 0.80 | 0.47 | 0.99 |


## Nulls
- Own block-shuffle null (200 replicates, 10-day blocks of the slope within calendar year; selected cell): real pair-window Sharpe 0.81 vs p95 1.12 (rank 0.80) -> FAIL.
- Selection-corrected null (full 4-cell selection rule re-run on each shuffled replicate; selected replicate pair-window Sharpe p95 1.34, clean Sharpe p95 1.60, all-in add@20% uplift p95 0.22): real pair-window 0.81, clean 0.68, uplift 0.11 -> all below p95 -> FAIL.
- Long-only random-day null (200, same entry-day counts per year per rung): p95 1.07, rank 0.74 -> FAIL. All-days long, same hold/stop, pair-window Sharpe 0.79: the ladder (0.81) is indistinguishable from owning NQ every day.
- Circular-shift null (reported): rank 0.45.

## Additive framing
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PX34_ladder_h2_k1.0 | 5.6 | 10% | 0.05 | 0.06 | 0.14 | 0.06 | 27 | -0.02 | 0.45 | 0.31 | 0.01 | NO |
| PX34_ladder_h2_k1.0 | 5.6 | 20% | 0.08 | 0.11 | 0.26 | 0.11 | 54 | -0.06 | 0.45 | 0.31 | 0.01 | NO |
| PX34_ladder_h2_k1.0 | 5.6 | 30% | 0.10 | 0.14 | 0.38 | 0.14 | 81 | -0.11 | 0.45 | 0.31 | 0.01 | NO |
| PX34_ladder_h2_k1.0 | 5.6 | 50% | 0.10 | 0.17 | 0.56 | 0.16 | 136 | -0.23 | 0.45 | 0.31 | 0.01 | NO |

## Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| PX34_ladder_h2_k1.0 | 10% | -6.1 | -16.6 | 6.9 | 1.8 | -18/5 | 18/18 | NO |
| PX34_ladder_h2_k1.0 | 20% | -12.2 | -34.0 | 13.3 | 3.6 | -35/9 | 35/36 | NO |
| PX34_ladder_h2_k1.0 | 30% | -18.3 | -51.3 | 19.6 | 1.4 | -53/14 | 51/53 | NO |
| PX34_ladder_h2_k1.0 | 50% | -30.4 | -86.1 | 20.6 | -6.5 | -88/7 | 45/51 | NO |

## Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| PX34_ladder_h2_k1.0 | 0.11 | 4 | 1.00 | 0.08 / 0.10 | 0.08 / 0.11 / 0.26 / 0.11 | 0.80 | 0.07 / 0.06 / 0.20 / 0.10 |

## Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| PX34_ladder_h2_k1.0 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | PASS (1.00) | fail | fail (0.31) | NO |


## Replication legs (pre-registered; need >= 2 of 4, each same sign and >= 50% of the selected cell's all-in uplift 0.11)
| leg | result | pass |
|---|---|---|
| (a) newest live weeks | n/a (VX file ends 2026-10-12 = pair end) | n/a |
| (b) H0 2023-02-10..07-31 (26 weeks) | uplift@20% +0.007, sleeve Sharpe 0.09 | NO |
| (c) ES AND RTY, selected cell unchanged, 2023-08..2026-10 | ES +0.068 (clean +0.06, H1 -0.01, H2 +0.18); RTY +0.066 (clean +0.05, H1 +0.12, H2 +0.14) | yes (threshold 0.055; non-virgin for the parent) |
| (d) alternating months, both directions | odd->even picked PX34_ladder_h2_k0.0 uplift +0.111; even->odd picked PX34_ladder_h1_k1.0 uplift -0.043 | NO |

Replication count 1 of 3 testable (needed 2). Since the replication count is below 2 on its own and the primary gates fail, no FOUND-PENDING status is possible.


## ERA FLAG (window 2018-11..2022-12, VX data start; reported, not gating): **positive pre-2023**
| cost model | per leg-trade $ (R=$7,000 sizing) | leg trades | weekly Sharpe of the ladder |
|---|---|---|---|
| gross (zero cost) | 821 | 1579 | 0.85 |
| net at fixed cost (1 tick/side + commission) | 798 | 1579 | 0.83 |
| net at price-scaled cost (x0.54) | 809 | 1579 | 0.84 |
The edge is cost-insensitive (one round trip a day on a ~600-pt-ATR-scaled position): the cost decomposition changes nothing; the pre-2023 positive Sharpe is long-beta drift (all-days long same cell: 2018-22 0.81, pair window 0.79).

## Insurance metrics (sleeve scaled to pair clean vol; combined = pair + 30% sleeve)
| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PX34_ladder_h2_k1.0 | clean | 0.68 | 622,108 | -226,002 | -141,201 | -103,659 | 564,000 | 1.08 | 1.10 | 20 | 1.56 | -149,442 | -91,293 | 350,681 | 4.32 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| PX34_ladder_h2_k1.0 | H1 | 0.05 | 6,829 | -152,676 | -96,797 | -72,429 | 210,854 | 0.06 | 0.03 | 11 | 2.97 | -61,469 | -59,531 | 170,943 | 3.49 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| PX34_ladder_h2_k1.0 | H2 | 1.80 | 422,219 | -92,098 | -79,167 | -52,227 | 249,834 | 4.14 | 1.69 | 19 | 2.64 | -82,524 | -79,985 | 217,425 | 4.08 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| PX34_ladder_h2_k1.0 | all | 0.81 | 1,051,156 | -226,002 | -129,260 | -91,462 | 564,000 | 1.29 | 1.86 | 18 | 2.00 | -149,442 | -87,238 | 350,681 | 8.56 | 41 | 1.86 | -82,524 | -79,220 | 280,110 |

## Executability
Orders are NQ/MNQ market-on-open (plus a resting stop) at NinjaTrader Brokerage via Rithmic: trivially executable. The signal needs the VX F1/F2 settlement prices of the previous day: CFE data are NOT on the Rithmic/NT8 feed at NTB; they need an IBKR (CFE) market-data subscription or the free CFE daily settlement file loaded by a script into an NT8 indicator before the open. VX itself is never traded. Margin: only NQ initial margin (same per-contract margin as ST/HM) at about the pair's per-book contract count; combined with the pair this must sit in a separate account because it nets against ST/HM NQ positions (netting class NQ_INTRADAY). Saved to the library as PX34_N3R_ladder_NQ (volmatch).

DONE PX34
