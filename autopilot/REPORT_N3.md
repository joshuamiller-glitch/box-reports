# REPORT N3

**LEAD (not FOUND) - VX curve slope (backwardation/flat) -> long ES NQ RTY: best selected cell N3_flat_h1_NQ: standalone Sharpe 2013-22 0.54, pair window 1.20, own-null rank pair window 0.99; additive uplift at 20% clean/H1/H2 +0.12/+0.42/+0.28, bootstrap lo +0.02; FOUND 0. N3 completed-plateau and long-only-null diagnostics (run after the pre-registered pipeline; the pipeline's random-SIDE null flatters a long-only sleeve in an up market, so the long-only random-entry null on the same VX-covered days is the relevant one): NQ flat-curve days (29% of days) long open-to-close next day: pair-window Sharpe 1.20 vs all-days long 0.75 vs steep-curve days 0.08; long-only null p95 1.04 (rank 0.98); RTY 1.12 (null p95 0.64, rank 0.99; steep days -0.71); ES 1.07 (null p95 0.98, rank 0.97). Plateau on the slope threshold 0.03 +-25% (0.0225 / 0.0375): NQ keep 0.50 (the 0.0225 neighbour gives all-in 0.10 vs 0.135 needed). Worst week +35% at 20% share (long equity beta) fails the worst-week rule; wd corr +0.30 (NQ), +0.37 (RTY), +0.34 (ES); bootstrap lower bound +0.02 at 10-20% share; 2x slippage holds (clean +0.11, H1 +0.42, H2 +0.28). Mechanism: after the VIX curve flattens/inverts (stress), next-day equity open-to-close returns are large (stress premium / vol risk premium); VX data 2018-11+ only (ERA: positive 2018-22). Fails: plateau (0.50), worst week, 10% share, wd corr for RTY/ES; signal needs VX settles (data feed), execution in NQ/ES/RTY outright or micros.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea N3: VX F2/F1-1 < 0 or < 0.03, hold 1/5, 12 cells; clean-only selection.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022), top 10 of 12 cells; eligible 6
| cell           |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:---------------|-----------------:|-------------:|----------:|
| N3_flat_h1_RTY |       1000000000 |         0.86 |        10 |
| N3_flat_h1_NQ  |       1000000000 |         0.84 |        10 |
| N3_flat_h1_ES  |       1000000000 |         0.78 |        10 |
| N3_flat_h5_NQ  |       1000000000 |         0.7  |        10 |
| N3_flat_h5_ES  |       1000000000 |         0.59 |        10 |
| N3_back_h5_ES  |                0 |         0.36 |         0 |
| N3_back_h5_RTY |                0 |         0.35 |         0 |
| N3_back_h5_NQ  |                0 |         0.33 |         0 |
| N3_flat_h5_RTY |       1000000000 |         0.25 |        10 |
| N3_back_h1_NQ  |                0 |         0.14 |         0 |

Multiplicity: 12 cells x 5% = 0.6 expected chance passes of a p95 null.

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| N3_flat_h1_RTY | 0.24 | 3 | 0.86 | 2.35 | 1.68 | 1.12 | 0.51 | 0.70 | 1.00 | 0.52 | 0.81 |
| N3_flat_h1_NQ | 0.54 | 4 | 0.84 | 1.97 | 2.16 | 1.20 | 0.77 | 0.94 | 0.99 | 0.46 | 0.98 |
| N3_flat_h1_ES | 0.43 | 4 | 0.78 | 1.94 | 1.93 | 1.07 | 0.63 | 0.92 | 0.98 | 0.38 | 0.96 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N3_flat_h1_RTY | 7.6 | 10% | 0.07 | 0.21 | 0.10 | 0.09 | 21 | 0.02 | 0.47 | 0.37 | 0.00 | NO |
| N3_flat_h1_RTY | 7.6 | 20% | 0.13 | 0.42 | 0.18 | 0.16 | 43 | 0.02 | 0.47 | 0.37 | 0.00 | NO |
| N3_flat_h1_RTY | 7.6 | 30% | 0.16 | 0.63 | 0.26 | 0.22 | 65 | 0.00 | 0.47 | 0.37 | 0.00 | NO |
| N3_flat_h1_RTY | 7.6 | 50% | 0.20 | 1.03 | 0.38 | 0.29 | 108 | -0.07 | 0.47 | 0.37 | 0.00 | NO |
| N3_flat_h1_NQ | 8.1 | 10% | 0.07 | 0.21 | 0.15 | 0.10 | 17 | 0.02 | 0.49 | 0.30 | 0.01 | NO |
| N3_flat_h1_NQ | 8.1 | 20% | 0.12 | 0.42 | 0.28 | 0.18 | 35 | 0.02 | 0.49 | 0.30 | 0.01 | NO |
| N3_flat_h1_NQ | 8.1 | 30% | 0.15 | 0.62 | 0.40 | 0.25 | 52 | 0.00 | 0.49 | 0.30 | 0.01 | NO |
| N3_flat_h1_NQ | 8.1 | 50% | 0.18 | 0.96 | 0.60 | 0.32 | 88 | -0.07 | 0.49 | 0.30 | 0.01 | NO |
| N3_flat_h1_ES | 7.3 | 10% | 0.06 | 0.20 | 0.12 | 0.09 | 20 | 0.01 | 0.47 | 0.34 | 0.00 | NO |
| N3_flat_h1_ES | 7.3 | 20% | 0.11 | 0.40 | 0.23 | 0.16 | 41 | 0.00 | 0.47 | 0.34 | 0.00 | NO |
| N3_flat_h1_ES | 7.3 | 30% | 0.13 | 0.59 | 0.33 | 0.21 | 62 | -0.03 | 0.47 | 0.34 | 0.00 | NO |
| N3_flat_h1_ES | 7.3 | 50% | 0.15 | 0.94 | 0.50 | 0.27 | 104 | -0.12 | 0.47 | 0.34 | 0.00 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| N3_flat_h1_RTY | 10% | -4.7 | -11.1 | 7.5 | 8.3 | -12/6 | 18/21 | NO |
| N3_flat_h1_RTY | 20% | -9.4 | -23.0 | 14.4 | 16.1 | -24/11 | 36/42 | NO |
| N3_flat_h1_RTY | 30% | -14.1 | -34.9 | 21.1 | 18.4 | -36/16 | 53/57 | NO |
| N3_flat_h1_RTY | 50% | -23.5 | -58.7 | 20.0 | -5.7 | -60/6 | 73/73 | NO |
| N3_flat_h1_NQ | 10% | -4.2 | -7.0 | 8.5 | 4.4 | -8/7 | 16/20 | NO |
| N3_flat_h1_NQ | 20% | -8.3 | -14.8 | 16.1 | 8.6 | -16/14 | 33/39 | NO |
| N3_flat_h1_NQ | 30% | -12.5 | -22.6 | 23.7 | 7.2 | -24/20 | 49/55 | NO |
| N3_flat_h1_NQ | 50% | -20.9 | -38.2 | 12.2 | -32.4 | -39/-2 | 72/72 | NO |
| N3_flat_h1_ES | 10% | -4.9 | -10.3 | 8.0 | 4.7 | -11/6 | 16/20 | NO |
| N3_flat_h1_ES | 20% | -9.8 | -21.4 | 15.2 | 9.3 | -22/12 | 32/40 | NO |
| N3_flat_h1_ES | 30% | -14.7 | -32.5 | 22.3 | 10.5 | -34/18 | 49/55 | NO |
| N3_flat_h1_ES | 50% | -24.5 | -54.7 | 15.3 | -26.6 | -56/-1 | 73/73 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| N3_flat_h1_RTY | 0.16 | 0 | n/a | n/a / n/a | 0.11 / 0.42 / 0.18 / 0.15 | 1.06 | 0.12 / 0.33 / 0.15 / 0.16 |
| N3_flat_h1_NQ | 0.18 | 0 | n/a | n/a / n/a | 0.11 / 0.42 / 0.28 / 0.18 | 1.18 | 0.11 / 0.32 / 0.24 / 0.17 |
| N3_flat_h1_ES | 0.16 | 0 | n/a | n/a / n/a | 0.09 / 0.39 / 0.22 / 0.14 | 0.99 | 0.10 / 0.30 / 0.19 / 0.15 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| N3_flat_h1_RTY | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (n/a) | PASS | fail (0.37) | NO |
| N3_flat_h1_NQ | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (n/a) | PASS | PASS (0.30) | NO |
| N3_flat_h1_ES | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | fail (n/a) | fail | fail (0.34) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N3_flat_h1_RTY | clean | 0.86 | 786,334 | -270,142 | -141,251 | -100,028 | 531,519 | 1.37 | 1.48 | 19 | 1.62 | -135,881 | -89,486 | 302,909 | 5.17 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| N3_flat_h1_RTY | H1 | 2.35 | 290,429 | -34,185 | -24,136 | -16,091 | 107,247 | 10.70 | 2.71 | 7 | 3.46 | -59,946 | -51,423 | 139,654 | 4.88 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| N3_flat_h1_RTY | H2 | 1.68 | 346,324 | -133,917 | -88,090 | -53,942 | 199,195 | 2.84 | 1.74 | 14 | 2.52 | -82,524 | -79,970 | 217,425 | 3.98 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| N3_flat_h1_RTY | all | 1.12 | 1,423,087 | -270,142 | -123,826 | -82,869 | 531,519 | 1.83 | 2.68 | 16 | 2.08 | -135,881 | -86,001 | 302,909 | 10.27 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |
| N3_flat_h1_NQ | clean | 0.84 | 765,953 | -281,478 | -161,229 | -114,634 | 681,032 | 1.18 | 1.12 | 16 | 1.61 | -125,717 | -86,427 | 334,341 | 4.67 | 41 | 1.46 | -81,874 | -78,736 | 280,110 |
| N3_flat_h1_NQ | H1 | 1.97 | 297,736 | -109,616 | -60,461 | -40,307 | 133,765 | 3.68 | 2.23 | 7 | 3.45 | -63,573 | -55,355 | 169,126 | 4.04 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| N3_flat_h1_NQ | H2 | 2.16 | 500,514 | -87,171 | -70,214 | -54,230 | 198,197 | 5.13 | 2.53 | 14 | 2.66 | -82,524 | -79,970 | 217,425 | 4.19 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| N3_flat_h1_NQ | all | 1.20 | 1,564,203 | -281,478 | -139,997 | -94,416 | 681,032 | 1.80 | 2.30 | 14 | 2.10 | -125,717 | -83,962 | 334,341 | 9.43 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |
| N3_flat_h1_ES | clean | 0.78 | 709,784 | -304,092 | -158,533 | -113,723 | 645,813 | 1.11 | 1.10 | 17 | 1.59 | -133,917 | -88,150 | 325,137 | 4.75 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| N3_flat_h1_ES | H1 | 1.94 | 270,154 | -93,025 | -47,806 | -31,871 | 128,578 | 3.96 | 2.10 | 7 | 3.42 | -63,690 | -54,660 | 159,564 | 4.23 | 36 | 2.83 | -78,287 | -77,610 | 151,713 |
| N3_flat_h1_ES | H2 | 1.93 | 387,755 | -79,125 | -71,277 | -48,856 | 194,557 | 4.18 | 1.99 | 16 | 2.59 | -82,524 | -79,970 | 217,425 | 4.04 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| N3_flat_h1_ES | all | 1.07 | 1,367,693 | -304,092 | -134,001 | -92,706 | 645,813 | 1.61 | 2.12 | 15 | 2.07 | -133,917 | -85,110 | 325,137 | 9.52 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.


DONE N3
