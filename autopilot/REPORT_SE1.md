# REPORT SE1 - PAIR ENTRY-EXECUTION TIMING ON THE 1-SECOND ENGINE (entry delay, limit-at-signal-close, sub-minute flow confirmation; D01/D02 x M6, H1-H2)
**Verdict: NO. FOUND 0. Selected delay_1 (clean-only among 11 cells): weekly Sharpe uplift +0.019 clean / +0.345 H1 / -0.464 H2 (needed +0.10 each), all-in -0.038; own timing-destroyed null (200) all-in rank 0.98 (p95 -0.22); failed: uplift>=0.10 clean/H1/H2, own null all-in > p95 (and clean), bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold. Cost of delay: signal-level drift is +8.2 $ per signal at 1 s and +17.9 $ at 300 s (8 lots; no systematic slope); account-level -7 $/trade at 1 s, -63 at 5 s, -165 at 30 s; break-even delay not defined: the signal-level drift is not systematically adverse (only 3 of 10 delays differ from zero at 1.96 SE and the sign alternates), so no delay up to 300 s erases the edge on this measure.**

## Set-up and fill model
- Engine: the corrected order-level account on 1-second bars (ap_k96_core.acct_se, copy of nt8sim.acct) with entries at (bar, second, price). Control = market at the next 1-min open (reproduces the live account: clean 1.46, H1 2.83 weekly Sharpe asserted at start; H2 2.48 on this axis because it ends 2026-10-16). Clean process; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) series via the live rows (7,346 accepted trades). Fill model: 1 tick/side + $34.88 commission per 8 lots (account), 2x slippage = SLIP_PT 1.0 on both candidate and baseline.
- Cells (pre-registered in PREREG_AUTOPILOT.md 'BATCH SE'): delay 1/5/15/30 s (fill = close of the d-th second after the bar open, time-based across bars), limit at the signal-bar close -0/1 tick resting 15/60 s (no chase, unfilled = missed), flow-confirmed market after 5/15/30 s (tick-rule signed volume from second volumes agrees with the side). Diagnostics 60/120/300 s delay for the curve. Limit fills are charged engine slippage (conservative).
- Null: delay cells -> entry at a uniformly random second inside the entry bar; limit/flow cells -> same-fraction random skip at random seconds; 200 replicates. Framing: pair-change (the execution replaces the live fill, same size); constant-risk statement = INSURANCE flags below (same size, so cost % equals the net change).

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| delay_1 **(selected)** | +0.019 | +0.345 | -0.464 | -0.038 |
| delay_5 | -0.127 | +0.242 | -1.681 | -0.427 |
| delay_15 | -0.269 | -0.816 | -0.863 | -0.466 |
| delay_30 | -0.344 | -1.215 | -1.409 | -0.699 |
| limit_0_15 | -0.133 | -0.511 | -0.326 | -0.231 |
| limit_0_60 | -0.133 | -0.511 | -0.326 | -0.231 |
| limit_1_15 | -0.727 | -0.701 | -1.444 | -0.861 |
| limit_1_60 | -0.963 | -0.591 | -1.937 | -1.104 |
| flow_5 | -0.116 | -1.860 | -1.281 | -0.645 |
| flow_15 | -1.823 | -0.534 | +0.298 | -1.071 |
| flow_30 | -0.728 | +0.461 | -0.023 | -0.318 |

## Result for the carried cell: delay_1
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.48 | +0.019 | +0.054 |
| H1 | 2.83 | 3.17 | +0.345 | +0.386 |
| H2 | 2.48 | 2.02 | -0.464 | -0.746 |
| all | 1.90 | 1.86 | -0.038 | -0.083 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean +0.019 vs +0.086 / 0.91; H1 +0.345 vs +0.067 / 0.98; H2 -0.464 vs -0.248 / 0.88; all -0.038 vs -0.215 / 0.98
- bootstrap 90% CI of all-in uplift: [-0.271, +0.193]
- plateau: 0.00 of 1 neighbours keep >= 75% of the all-in uplift; neighbours: delay_1 -0.038
- alternating-month split (pre-registered): select delay_1 (-0.053) reads +0.108 on the other half; select limit_0_15 (+0.156) reads -0.390 on the other half
- H0 (2023-02-10..07-31) uplift: -0.172; replications counted (alt-month, H0): 0 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -79.7k vs -81.9k; H1 -78.3k vs -78.3k; H2 -82.0k vs -82.5k; all -82.0k vs -82.5k; weekly corr with pair 0.966 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.48 | 2.79 | 4.79 | -78.3k | -77.8k | 278k | -79.7k | 44.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 3.17 | 7.31 | 4.48 | -77.9k | -65.8k | 151k | -78.3k | 35.7 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 2.02 | 3.83 | 3.32 | -80.7k | -79.7k | 215k | -82.0k | 36.1 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.86 | 3.58 | 9.77 | -79.1k | -78.3k | 278k | -82.0k | 41.7 |

## Reading
Weekly-Sharpe uplifts of single cells are noisy because small price differences change which brackets trade and how the two books net (the delay curve below is not monotone in Sharpe), so the cost of delay is also measured at signal level, where it is clean: adverse drift of the fill relative to the next-bar open averages +0.05 pt after 1 s, +0.01 pt after 5 s, -0.05 pt after 30 s and +0.11 pt after 300 s (positive = worse), i.e. a fitted slope of +0.052 $ per second per signal at 8 lots with a sign that alternates across delays (the drift is within noise); the pair earns about $391 net per accepted trade. Break-even delay: not defined: the signal-level drift is not systematically adverse (only 3 of 10 delays differ from zero at 1.96 SE and the sign alternates), so no delay up to 300 s erases the edge on this measure. The account-level $ per trade below is NOT a clean cost: it mixes the fill price with changed bracket paths, busy-book skips and netting (non-monotone: -$63 at 5 s, +$15 at 120 s), so it measures how fragile the account is to the exact fill second rather than the price of waiting.

## Executability / era / replication
NT8: delay = not applicable (a latency to be minimised; market at bar open as live); limit-at-close and flow-confirmation need sub-minute order handling in the strategy (OnMarketData / 1-s secondary series) and are executable at NinjaTrader Brokerage via Rithmic; no data purchase. Code: ap_sw_exec.py, ap_sw_exec_run.py, ap_sw_exec_rep.py (uses ap_k96_core/ap_k_lib); outputs/autopilot/se1/. ERA n/a (pair rows start 2023-02-10; 1-second bars exist only for the pair period). Newest live weeks: none after 2026-10-13.


## Cost of delay (signal level, all 50,199 market signals; adverse = worse than the next-bar open fill)
|   delay_s |   mean_adverse_pts |   se_pts |   median_pts |   mean_$_per_signal(8 lots) |   share_adverse |     n |
|----------:|-------------------:|---------:|-------------:|----------------------------:|----------------:|------:|
|         1 |              0.052 |    0.006 |         0    |                       8.249 |           0.39  | 50199 |
|         2 |              0.042 |    0.01  |         0    |                       6.689 |           0.405 | 50199 |
|         3 |              0.032 |    0.012 |         0    |                       5.185 |           0.419 | 50199 |
|         5 |              0.011 |    0.014 |         0    |                       1.743 |           0.431 | 50199 |
|        10 |             -0.015 |    0.019 |         0    |                      -2.457 |           0.445 | 50199 |
|        15 |             -0.003 |    0.021 |         0    |                      -0.466 |           0.452 | 50199 |
|        30 |             -0.052 |    0.027 |         0    |                      -8.323 |           0.46  | 50199 |
|        60 |             -0.017 |    0.034 |         0    |                      -2.736 |           0.471 | 50199 |
|       120 |              0.056 |    0.047 |         0    |                       9.003 |           0.477 | 50199 |
|       300 |              0.112 |    0.074 |        -0.25 |                      17.898 |           0.484 | 50199 |

- Linear slope +0.052 $ per second per signal (8 lots); pair net per accepted trade $391 (all-in, 7,346 trades); break-even delay: not defined: the signal-level drift is not systematically adverse (only 3 of 10 delays differ from zero at 1.96 SE and the sign alternates), so no delay up to 300 s erases the edge on this measure; no round-trip cost (1 tick/side + $34.88) is added in this table.

## Account-level view per delay cell (change in all-in net $ and per accepted trade vs the control; noisy, see Reading)
|            |         d_net_all |   trades |   d_$_per_trade |
|:-----------|------------------:|---------:|----------------:|
| delay_1    |  -53813.8         |     7285 |            -7.4 |
| delay_5    | -458646           |     7263 |           -63.1 |
| delay_15   | -656462           |     7260 |           -90.4 |
| delay_30   |      -1.18378e+06 |     7194 |          -164.6 |
| limit_0_15 | -238288           |     7372 |           -32.3 |
| limit_0_60 | -238288           |     7372 |           -32.3 |
| limit_1_15 |      -1.43521e+06 |     7125 |          -201.4 |
| limit_1_60 |      -1.65172e+06 |     7177 |          -230.1 |
| flow_5     |      -1.15057e+06 |     6336 |          -181.6 |
| flow_15    |      -1.79912e+06 |     6486 |          -277.4 |
| flow_30    | -960573           |     6491 |          -148   |
| delay_60   | -962603           |     7123 |          -135.1 |
| delay_120  |  113587           |     7372 |            15.4 |
| delay_300  | -518844           |     7365 |           -70.4 |

## Weekly Sharpe by delay (clean / H1 / H2 / all)
|             |   clean |   H1 |   H2 |   all |
|:------------|--------:|-----:|-----:|------:|
| delay_1     |    1.48 | 3.17 | 2.02 |  1.86 |
| delay_5     |    1.33 | 3.07 | 0.8  |  1.47 |
| delay_15    |    1.19 | 2.01 | 1.62 |  1.43 |
| delay_30    |    1.12 | 1.61 | 1.07 |  1.2  |
| delay_60    |    1.37 | 1.13 | 1.03 |  1.25 |
| delay_120   |    1.17 | 2.5  | 2.8  |  1.79 |
| delay_300   |    1.13 | 1.97 | 2.46 |  1.59 |
| 0 (control) |    1.46 | 2.83 | 2.48 |  1.9  |

## Constant-risk / insurance flags of the selected cell (INS?, cost %, CVaR5 impr %, worst-week impr %, maxDD impr %)
clean (False, 0.2, 0.5, 2.6, 0.6); H1 (False, 13.9, -0.3, -0.1, 0.4); H2 (False, -13.2, 0.5, 0.6, 1.3); all (False, -0.8, 0.2, 0.6, 0.6)

DONE SE1
