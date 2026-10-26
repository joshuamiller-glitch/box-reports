# REPORT C11-HM - HM-health trigger as a size switch on HM only

**Verdict: NO.** Selected cell sharpe8_q10_m0.0 (statistic sharpe8, threshold q=0.1, HM size 0.0 when fired). Weekly Sharpe uplift vs B.Cfg(wk_floor=8,wk_loss_pb=None): clean +0.20 / H1 -0.32 / H2 -0.23 (all-in +0.03); gate needs +0.10 on each span, so the pair-change fails on H1 and H2 (the switch helps only on the span it was selected on); the rep_common-style formula also prints INSURANCE (all-in max DD 22% smaller at -2.4% net) but that comes from the clean span it was selected on, H1 net falls 15%, and it was not tested against the matched null on max DD, so I do not claim it. Runtime: selection 45 s, scoring ~20-25 min on 5 workers (500 matched random-switch full B.run replays).

## 1. Protocol (pre-registered in PREREG_AUTOPILOT.md, Cycle 11, before the first run)
- Statistic from UNRULED full-size HM raw rows of the corrected engine (so it does not depend on the switch), assigned to weeks by exit label: sharpe8 / sharpe13 (rolling weekly-net Sharpe) or apl50 (mean gross points of the last 50 closed HM trades). Walk-forward threshold: fires for the next week's HM entries if S(w) < the q-quantile of all S observed through week w (>= 20 observations), q in {10%, 20%}; no hysteresis; HM size m in {0.5, 0} x full, ST untouched, open trades untouched; live rules (per-book 5R/-2R, day lock 8R/2R/67%, week floor -8R) applied on the resized rows. 12 cells. Fill model: NT8-faithful corrected engine, 1 tick/side + $34.88 NT8 commission per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and switch.
- Selection on clean 2023-08..2025-07 only (cells with >= 4 triggered clean weeks): highest clean pair weekly Sharpe. Baseline computed in a clean process (no b10_core import): weekly Sharpe 1.46 / 2.83 / 2.30 clean/H1/H2.
- Disclosure: D3 S3 built its statistics list while looking at the Aug-Sep 2026 HM collapse, which sits in H2. H2 is therefore not an independent test of the statistic family, only of this exact walk-forward cell; a pass in H2 would not be independent evidence.

## 2. Selection table (clean only)
| cell | ntrig_clean | clean_sh | baseline_clean | clean_uplift |
|---|---|---|---|---|
| sharpe8_q10_m0.5 | 16 | 1.39 | 1.46 | -0.07 |
| sharpe8_q10_m0.0 | 16 | 1.66 | 1.46 | 0.20 |
| sharpe8_q20_m0.5 | 33 | 1.23 | 1.46 | -0.23 |
| sharpe8_q20_m0.0 | 33 | 1.64 | 1.46 | 0.18 |
| sharpe13_q10_m0.5 | 11 | 1.44 | 1.46 | -0.02 |
| sharpe13_q10_m0.0 | 11 | 1.60 | 1.46 | 0.14 |
| sharpe13_q20_m0.5 | 18 | 1.37 | 1.46 | -0.09 |
| sharpe13_q20_m0.0 | 18 | 1.56 | 1.46 | 0.10 |
| apl50_q10_m0.5 | 15 | 1.28 | 1.46 | -0.18 |
| apl50_q10_m0.0 | 15 | 1.27 | 1.46 | -0.19 |
| apl50_q20_m0.5 | 23 | 1.24 | 1.46 | -0.22 |
| apl50_q20_m0.0 | 23 | 1.51 | 1.46 | 0.05 |

## 3. Result for the selected cell (H1 and H2 read once)
| span | base_sharpe | switch_sharpe | uplift | flag_weeks | null_p95 | null_mean | null_rank | net_change_pct | ww_base | ww_switch |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.66 | 0.20 | 16/105 | 0.30 | 0.01 | 0.88 | 11.52 | -81873.92 | -79867.84 |
| H1 | 2.83 | 2.51 | -0.32 | 2/28 | 0.02 | -0.03 | 0.04 | -14.84 | -78287.36 | -78287.36 |
| H2 | 2.30 | 2.06 | -0.23 | 4/37 | 0.12 | -0.21 | 0.34 | -17.18 | -82524.48 | -82524.48 |
| all | 1.86 | 1.88 | 0.03 | 21/168 | 0.18 | -0.04 | 0.67 | -2.45 | -82524.48 | -82524.48 |

Bootstrap 90% CI of the all-in uplift: [-0.20, +0.25]; per span clean [-0.03, +0.49], H1 [-1.16, +0.25], H2 [-0.68, +0.11].
Matched random-switch null (500 draws: the cell's on/off run lengths reshuffled in random order over the same eligible weeks, so same exposure and episode count; full replay each): null_p95/mean/rank columns above are for the uplift in each span.

## 4. Gates for a pair change
| gate | result | number |
|---|---|---|
| pre-registered, selection on clean only | PASS | |
| uplift >= +0.10 on clean, H1, H2 separately | FAIL | +0.20 / -0.32 / -0.23 |
| worst week not worse (clean, H1, H2, all-in) | PASS | base/switch all-in $-82,524 / $-82,524 |
| matched random-switch null p95 (all-in uplift) | FAIL | real +0.03 vs p95 +0.18 (rank 0.674) |
| bootstrap 90% CI of all-in uplift > 0 | FAIL | [-0.20, +0.25] |
| plateau (>= 75% of +-25% neighbours keep >= 75% of all-in uplift) | FAIL | 60% of 5 |
| 2x slippage keeps +0.10 on each span | FAIL | +0.25 / -0.33 / -0.24 |
| rep_common-style verdict (SURVIVES needs H2 net +5% and DD -10%, H1 >= 90%, clean >= 95%) | INSURANCE | H2 False, H1 False, clean True |

## 5. Plateau detail
| neighbour | trigger_weeks | clean | H1 | H2 | all_in | keeps75 |
|---|---|---|---|---|---|---|
| sharpe6_q10_m0.0 | 15 | 0.14 | 0.00 | -0.23 | 0.04 | True |
| sharpe10_q10_m0.0 | 19 | 0.20 | -0.32 | -0.32 | 0.00 | False |
| sharpe8_q7_m0.0 | 13 | 0.28 | 0.11 | -0.18 | 0.15 | True |
| sharpe8_q12_m0.0 | 24 | 0.19 | -0.32 | -0.23 | 0.01 | False |
| sharpe8_q10_m0.125 | 21 | 0.19 | -0.15 | -0.16 | 0.06 | True |

## 6. Insurance metric set (pair weekly P&L, $)
| book | span | net | weekly_sharpe | sortino | MAR | maxDD | worst_week | CVaR5 | CVaR10 | pct_neg_wk |
|---|---|---|---|---|---|---|---|---|---|---|
| baseline | clean | 1329959 | 1.46 | 2.78 | 4.75 | 280110 | -81874 | -78736 | -78009 | 42.86 |
| HM switch | clean | 1483149 | 1.66 | 3.23 | 6.80 | 218153 | -79868 | -78037 | -77615 | 41.90 |
| baseline | H1 | 593797 | 2.83 | 6.09 | 3.91 | 151713 | -78287 | -77610 | -66030 | 39.29 |
| HM switch | H1 | 505691 | 2.51 | 5.18 | 3.33 | 151713 | -78287 | -77610 | -66030 | 42.86 |
| baseline | H2 | 761254 | 2.30 | 4.69 | 3.50 | 217425 | -82524 | -81089 | -79185 | 44.44 |
| HM switch | H2 | 630487 | 2.06 | 4.02 | 3.48 | 181407 | -82524 | -81089 | -75149 | 44.44 |
| baseline | all | 2685011 | 1.86 | 3.63 | 9.59 | 280110 | -82524 | -79220 | -78243 | 42.86 |
| HM switch | all | 2619327 | 1.88 | 3.67 | 12.01 | 218153 | -82524 | -78743 | -77956 | 42.86 |

Cost of the switch in net: clean +11.5%, H1 -14.8%, H2 -17.2%, all-in -2.4%.

## 7. Executability and margin
HM entry quantity becomes 8 x m (m = 0 skips HM entries) as a function of a weekly flag. NT8 spec: an external weekly script (Sunday evening) reads the HM trade list (exit time, net, points), computes the statistic and the expanding quantile, and writes a flag file (0/1) that DualStrat/HM would have to read before each HM entry; this needs a DualStrat change (a file-read or an ATI-driven quantity switch), which is outside this program's mandate. Margin: never increases (HM contracts reduced). Executable at NinjaTrader Brokerage via Rithmic: same instrument as the live pair (NQ).

## 8. Limits
The HM series has 3.7 years; the collapse is a single event; the statistic family was seen on H2 before pre-registration; each cell's trigger count in clean is small (selected: 16 flagged weeks of 105); the matched null controls for exposure and episode count but not for the correlation between statistic and drawdown timing.

Code: ap_c11_hm_core.py, ap_c11_hm_sel.py, ap_c11_hm_score.py, ap_c11_hm_rep.py; data outputs/autopilot/c11/.

DONE C11-HM
