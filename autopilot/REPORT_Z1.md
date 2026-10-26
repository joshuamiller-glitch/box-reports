# REPORT Z1

**NO - X1 does NOT survive path-resolved execution: on the same markets, ET-session label days with true first-touch resolution on 30-min bars give 2013-22 Sharpe 0.2-0.4 (vs 0.9-1.0 in the daily UTC-day bars) and pair-window Sharpe -0.6..0.0 (vs +0.7..+1.0); the two cells that pass the dev screen (union, NQ ES RTY GC CL ZN) have pair-window Sharpe -0.58/-0.59, own-null rank 0.44/0.49, additive uplift at 20% clean/H1/H2 -0.03/-0.37/-0.35. 52% of triggered X1 trades in the daily bars were both-touch days (both levels hit), whose order the daily bar cannot resolve: the X1/Y6 LEAD is a fill-model artefact and is withdrawn. FOUND 0.**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Check Z1: the X1 mechanics re-run on 30-min path data (ET label days 18:00-17:00, setups from label-day OHLC, stop-entry resolved on the first touching 30-min bar, both-in-one-bar -> side nearer the bar open, ATR20 stop, exit at the close of the day's last bar), markets NQ ES RTY GC CL (M5) and + ZN (M6); 8 cells.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-22) and spans, all 8 cells
| cell           |   2013-22 |   clean |    H1 |    H2 |   pairwin |   long |
|:---------------|----------:|--------:|------:|------:|----------:|-------:|
| Z1_union_k2_M5 |      0.37 |    0.16 | -0.08 | -1.25 |     -0.19 |   0.21 |
| Z1_union_k2_M6 |      0.24 |   -0.04 | -1.35 | -1.49 |     -0.58 |   0.01 |
| Z1_union_k3_M5 |      0.36 |    0.08 | -0.08 | -1.2  |     -0.21 |   0.19 |
| Z1_union_k3_M6 |      0.22 |   -0.11 | -1.35 | -1.45 |     -0.59 |  -0.01 |
| Z1_nr4_k2_M5   |      0.27 |    0.63 | -1.11 | -0.68 |      0    |   0.12 |
| Z1_nr4_k2_M6   |      0.13 |    0.41 | -1.46 | -0.96 |     -0.24 |  -0.06 |
| Z1_nr4_k3_M5   |      0.25 |    0.57 | -1.11 | -0.68 |     -0.02 |   0.1  |
| Z1_nr4_k3_M6   |      0.11 |    0.36 | -1.46 | -0.96 |     -0.26 |  -0.08 |

Daily-bar (UTC-day, X1 engine) comparison on the same markets and the same union setup, hold 1:

| cell                  |   trades |   2013-22 |   clean |   H1 |   H2 |   pairwin |   long |
|:----------------------|---------:|----------:|--------:|-----:|-----:|----------:|-------:|
| daily-UTC union k2 M5 |     4151 |      1.02 |    0.56 | 0.91 | 2.44 |      0.97 |   0.96 |
| daily-UTC union k3 M5 |     4151 |      0.96 |    0.51 | 0.8  | 2.56 |      0.92 |   0.92 |
| daily-UTC union k2 M6 |     5032 |      0.94 |    0.52 | 0.27 | 1.93 |      0.77 |   0.88 |
| daily-UTC union k3 M6 |     5032 |      0.91 |    0.48 | 0.16 | 2.01 |      0.73 |   0.85 |

Both-touch share (daily UTC bars, union setups on NQ ES GC CL 6E HO): 5,859 setup days, 91% trigger at least one level, 47% touch BOTH levels, i.e. 52% of triggered trades are ambiguous in a daily bar. The daily engine resolves them by proximity to the open and then applies the stop rule on the whole bar; the real path decides differently, and after a compressed bar the next day usually exceeds both levels.

## Selected cells (dev screen), full gates
### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Z1_union_k2_M6 | 0.24 | 7 | -0.04 | -1.35 | -1.49 | -0.58 | 0.01 | 0.37 | 0.44 | -0.21 | 1.00 |
| Z1_union_k3_M6 | 0.22 | 7 | -0.11 | -1.35 | -1.45 | -0.59 | -0.01 | 0.39 | 0.49 | -0.28 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Z1_union_k2_M6 | 5.0 | 10% | -0.01 | -0.17 | -0.17 | -0.07 | 7 | -0.15 | 0.37 | 0.11 | 0.02 | NO |
| Z1_union_k2_M6 | 5.0 | 20% | -0.03 | -0.37 | -0.35 | -0.15 | 33 | -0.32 | 0.37 | 0.11 | 0.02 | NO |
| Z1_union_k2_M6 | 5.0 | 30% | -0.05 | -0.57 | -0.54 | -0.24 | 64 | -0.50 | 0.37 | 0.11 | 0.02 | NO |
| Z1_union_k2_M6 | 5.0 | 50% | -0.14 | -0.99 | -0.91 | -0.44 | 124 | -0.85 | 0.37 | 0.11 | 0.02 | NO |
| Z1_union_k3_M6 | 4.9 | 10% | -0.01 | -0.17 | -0.15 | -0.07 | 7 | -0.16 | 0.44 | 0.13 | 0.01 | NO |
| Z1_union_k3_M6 | 4.9 | 20% | -0.04 | -0.36 | -0.32 | -0.15 | 25 | -0.32 | 0.44 | 0.13 | 0.01 | NO |
| Z1_union_k3_M6 | 4.9 | 30% | -0.08 | -0.57 | -0.49 | -0.24 | 52 | -0.50 | 0.44 | 0.13 | 0.01 | NO |
| Z1_union_k3_M6 | 4.9 | 50% | -0.18 | -0.98 | -0.84 | -0.44 | 104 | -0.87 | 0.44 | 0.13 | 0.01 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| Z1_union_k2_M6 | 10% | -13.0 | 3.0 | 4.1 | 12.2 | 3/4 | 12/15 | NO |
| Z1_union_k2_M6 | 20% | -25.9 | -18.7 | 4.6 | 24.5 | 4/8 | 22/30 | NO |
| Z1_union_k2_M6 | 30% | -38.9 | -41.6 | 5.2 | 24.4 | 4/11 | 32/32 | NO |
| Z1_union_k2_M6 | 50% | -64.8 | -87.4 | -1.7 | 18.5 | 2/13 | 3/16 | NO |
| Z1_union_k3_M6 | 10% | -13.1 | 3.1 | 4.7 | 12.2 | 3/4 | 12/15 | NO |
| Z1_union_k3_M6 | 20% | -26.1 | -10.8 | 5.9 | 24.5 | 6/8 | 22/30 | NO |
| Z1_union_k3_M6 | 30% | -39.2 | -29.7 | 7.1 | 20.8 | 8/12 | 32/32 | NO |
| Z1_union_k3_M6 | 50% | -65.3 | -67.6 | -2.8 | 12.5 | -5/7 | 3/16 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| Z1_union_k2_M6 | -0.15 | 2 | 0.00 | -0.15 / -0.14 | -0.10 / -0.48 / -0.41 / -0.22 | -0.99 | -0.02 / -0.26 / -0.33 / -0.13 |
| Z1_union_k3_M6 | -0.15 | 2 | 0.00 | -0.16 / -0.15 | -0.11 / -0.47 / -0.38 / -0.22 | -1.00 | -0.03 / -0.26 / -0.29 / -0.13 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| Z1_union_k2_M6 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.11) | NO |
| Z1_union_k3_M6 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | fail | fail | fail (0.00) | fail | PASS (0.13) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Z1_union_k2_M6 | clean | -0.04 | -31,511 | -195,413 | -115,310 | -90,746 | 595,385 | -0.06 | -0.05 | 57 | 1.41 | -102,162 | -93,175 | 267,704 | 4.93 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| Z1_union_k2_M6 | H1 | -1.35 | -292,442 | -134,210 | -120,765 | -109,877 | 378,395 | -1.58 | -0.77 | 46 | 2.26 | -76,261 | -67,068 | 184,078 | 2.75 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| Z1_union_k2_M6 | H2 | -1.49 | -469,517 | -249,102 | -187,036 | -138,836 | 570,293 | -1.64 | -0.82 | 50 | 1.76 | -134,935 | -119,813 | 244,186 | 2.54 | 44 | 2.30 | -82,524 | -81,089 | 217,425 |
| Z1_union_k2_M6 | all | -0.58 | -793,471 | -249,102 | -140,909 | -111,450 | 1,195,791 | -0.75 | -0.66 | 54 | 1.62 | -134,935 | -98,022 | 267,704 | 9.14 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |
| Z1_union_k3_M6 | clean | -0.11 | -101,402 | -253,362 | -128,217 | -99,392 | 587,520 | -0.16 | -0.17 | 55 | 1.38 | -99,581 | -92,561 | 277,771 | 4.68 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| Z1_union_k3_M6 | H1 | -1.35 | -291,292 | -133,682 | -120,290 | -109,445 | 376,907 | -1.58 | -0.77 | 46 | 2.26 | -76,264 | -66,990 | 183,895 | 2.75 | 43 | 2.83 | -78,287 | -77,610 | 151,713 |
| Z1_union_k3_M6 | H2 | -1.45 | -431,296 | -216,374 | -170,426 | -129,197 | 531,675 | -1.63 | -0.81 | 50 | 1.80 | -125,117 | -114,854 | 234,376 | 2.70 | 44 | 2.30 | -82,524 | -81,089 | 217,425 |
| Z1_union_k3_M6 | all | -0.59 | -823,990 | -253,362 | -144,844 | -113,586 | 1,224,728 | -0.76 | -0.67 | 52 | 1.62 | -125,117 | -96,509 | 277,771 | 8.78 | 43 | 1.86 | -82,524 | -79,220 | 280,110 |


## Reading
The compression-breakout lead (X1, Y6) came from the daily-bar fill model, not from the market. Under path-resolved execution the pair-window Sharpe is negative for the cells that pass the dev screen, the best clean-window cell (nr4 M5, clean 0.63) is -1.11 in H1, and none beats its own null. X1, Y6, Z6 and Z7 (same mechanism, daily-bar engine) must be re-read as UNCONFIRMED; B2-D (same fill model) carries the same caveat. Lesson for every stop-entry sleeve evaluated on daily bars: require path resolution before reporting.

## Executability (G7)
Not applicable: the sleeve is withdrawn.


DONE Z1
