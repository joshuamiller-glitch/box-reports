# REPORT B4 - intraday mean reversion with VWAP / standard-deviation bands (5-30 min) on ES, RTY, GC, CL, ZN

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 1 selected cells (+15 diagnostic) scored on 5 instruments; best non-diagnostic all-in additive uplift at 20% share -0.14; best pair-window standalone Sharpe +0.30.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: fade a bar close that crosses from inside to outside session VWAP +- k sigma (sigma = volume-weighted std of typical price about the session VWAP; anchor = globex 18:00 ET or the instrument RTH open). Stop s x sigma from entry, target = VWAP level at the signal (or halfway), time stop 60/180 min, flat 16:55.
- Instruments: ES, RTY, GC, CL, ZN. Grid: 192 cells per instrument = 4 bar sizes x 3 band widths x 2 anchors x 2 stops x 2 targets x 2 time stops.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection: ES/GC/CL/ZN 2013-2022 (>=7 of 10 calendar years with positive weekly Sharpe, >=300 trades); RTY 2018-2022 (>=4 of 5, >=150 trades); BTC/ETH 2022-01..2023-07 (>=2 of 3 half-year blocks, >=100 trades; low power). Top 10 per instrument; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). Clean 2023-08..2025-07, H1 2025-08-01..2026-02-06, H2 2026-02-07..2026-10-13 read once after selection. Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Selection and the false-survivor test (200 timing-destroyed replicates of the whole grid per instrument)
| sym   |   cells |   eligible |   passing |   best_sel_sharpe |   max_yrs_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|------------------:|--------------:|-----------:|-------------:|
| CL    |     192 |        192 |         0 |            -0.231 |             4 |          0 |            3 |
| ES    |     192 |        192 |         0 |            -0.211 |             3 |          0 |            3 |
| GC    |     192 |        192 |         0 |            -0.081 |             5 |          0 |            3 |
| RTY   |     192 |        192 |         1 |             0.272 |             4 |          1 |            3 |
| ZN    |     192 |        192 |         0 |            -1.592 |             1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            0.005 |               1 |      1     |                      nan    |            0.237 |           0.237 |  nan     |      nan    |                0.237 |
| RTY   |     200 |                    1 |            1.045 |               4 |      0.645 |                        0.22 |            0.296 |           0.813 |    0.385 |        0.22 |                0.852 |
| GC    |     200 |                    0 |            0.035 |               1 |      1     |                      nan    |           -0.005 |           0.295 |  nan     |      nan    |                0.295 |
| CL    |     200 |                    0 |            0.03  |               1 |      1     |                      nan    |            0.089 |           0.386 |  nan     |      nan    |                0.386 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                      nan    |          nan     |         nan     |  nan     |      nan    |              nan     |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the selection span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades sel. span | blocks pos | Sharpe sel. span | Sharpe full history | pair-window all-in Sharpe | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | 424 | 3 | -0.21 | -0.26 | -0.53 | -0.11 / -0.45 / -0.14 | -0.22 | 0.47 | 0.35 | -0.38 | 0.00 | 142 | diag |
| ES 2 (diag) | 15m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | 752 | 2 | -0.27 | -0.50 | -0.89 | -0.45 / -0.23 / 0.17 | -0.35 | -0.16 | 0.16 | -0.57 | 0.00 | 259 | diag |
| ES 3 (diag) | 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m | 1641 | 2 | -0.32 | -0.24 | 0.02 | 0.03 / -0.16 / -0.29 | -0.21 | -0.13 | 0.82 | -0.34 | 0.00 | 755 | diag |
| RTY 1 | 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | 181 | 4 | 0.22 | -0.05 | -0.52 | -0.07 / -0.28 / -0.19 | -0.16 | 0.16 | 0.42 | -0.30 | 0.00 | 94 S | NO |
| RTY 2 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=60m | 181 | 2 | 0.27 | -0.02 | -0.59 | -0.06 / -0.37 / -0.15 | -0.15 | 0.17 | 0.29 | -0.29 | 0.00 | 94 S | diag |
| RTY 3 (diag) | 10m VWAPband k=2.5 rth stop=2.0sd tgt=half time=60m | 445 | 3 | 0.26 | -0.23 | -0.96 | -0.18 / -0.49 / -0.20 | -0.25 | 0.03 | 0.21 | -0.40 | 0.00 | 196 | diag |
| RTY 4 (diag) | 10m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | 437 | 3 | 0.13 | -0.44 | -1.27 | -0.19 / -0.64 / -0.32 | -0.31 | 0.11 | 0.06 | -0.45 | 0.00 | 194 | diag |
| GC 1 (diag) | 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | 552 | 3 | -0.08 | -0.09 | -0.13 | -0.11 / -0.86 / -0.92 | -0.44 | 0.21 | 0.53 | -1.10 | 0.00 | 192 | diag |
| GC 2 (diag) | 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | 551 | 5 | -0.19 | -0.15 | -0.20 | -0.20 / -0.32 / -1.77 | -0.56 | 0.37 | 0.52 | -1.21 | 0.00 | 192 | diag |
| GC 3 (diag) | 15m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | 530 | 4 | -0.24 | -0.27 | -0.52 | -0.44 / -1.45 / -2.28 | -1.06 | 0.41 | 0.26 | -1.83 | 0.00 | 192 | diag |
| CL 1 (diag) | 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m | 894 | 3 | -0.23 | -0.20 | -0.08 | -0.23 / -0.23 / 0.69 | -0.13 | 0.09 | 0.65 | -0.28 | 0.00 | 314 | diag |
| CL 2 (diag) | 30m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | 897 | 3 | -0.33 | -0.19 | 0.30 | -0.18 / -0.11 / 0.72 | -0.06 | 0.08 | 0.79 | -0.22 | 0.33 | 316 | diag |
| CL 3 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | 356 | 3 | -0.42 | -0.56 | -1.02 | -0.26 / 0.17 / -1.31 | -0.50 | -0.14 | 0.02 | -0.86 | 0.00 | 86 S | diag |
| ZN 1 (diag) | 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m | 904 | 0 | -1.59 | -1.90 | -3.62 | -0.52 / -0.50 / -0.44 | -0.84 | -0.14 | 0.00 | -0.65 | 0.00 | 348 | diag |
| ZN 2 (diag) | 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m | 485 | 0 | -1.61 | -1.66 | -1.80 | -0.44 / -0.36 / 0.17 | -0.55 | 0.19 | 0.12 | -0.47 | 0.00 | 189 | diag |
| ZN 3 (diag) | 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=60m | 488 | 0 | -1.83 | -2.03 | -2.73 | -0.48 / -0.44 / -0.21 | -0.74 | 0.45 | 0.01 | -0.58 | 0.00 | 190 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 1 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 1 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 0 |
| worst-decile corr <= +0.30 | 12 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 3 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CL 30m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m (diag) | clean | -0.60 | -0.69 | -209601 | -154698 | 1123501 | -563023 | -0.61 | 44.8 | 1.28 | -85128 | 283395 | -90615 |
| CL 30m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m (diag) | H1 | -0.45 | -0.70 | -98666 | -88397 | 162452 | -115996 | -0.61 | 57.1 | 2.72 | -68003 | 162299 | -86423 |
| CL 30m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m (diag) | H2 | 2.43 | 5.30 | -157338 | -133525 | 324106 | -161811 | 4.28 | 25.0 | 3.01 | -83424 | 201570 | -89433 |
| CL 30m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m (diag) | all | 0.30 | 0.42 | -188941 | -144715 | 1141986 | -563023 | 0.53 | 42.9 | 1.89 | -84909 | 283395 | -90615 |
| ES 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | clean | 0.28 | 0.47 | -150872 | -131428 | 1197867 | -195734 | 0.29 | 50.5 | 1.49 | -87745 | 362725 | -107555 |
| ES 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | H1 | -0.04 | -0.07 | -225852 | -177901 | 467586 | -319212 | -0.04 | 71.4 | 2.66 | -88238 | 185032 | -90226 |
| ES 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | H2 | -0.39 | -0.62 | -244918 | -212111 | 1140334 | -258145 | -0.24 | 58.3 | 2.01 | -99098 | 240184 | -111833 |
| ES 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | all | 0.02 | 0.04 | -201740 | -164995 | 1197867 | -319212 | 0.04 | 56.0 | 1.79 | -91609 | 362725 | -111833 |
| GC 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | clean | -0.14 | -0.20 | -208170 | -169439 | 1054364 | -299434 | -0.18 | 34.3 | 1.35 | -90734 | 298730 | -116112 |
| GC 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | H1 | 0.41 | 0.52 | -1070329 | -775264 | 1936840 | -1936840 | 0.39 | 32.1 | 1.97 | -216346 | 398588 | -398588 |
| GC 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | H2 | -1.09 | -1.38 | -615649 | -486821 | 1545891 | -634937 | -0.84 | 41.7 | 1.37 | -126899 | 217425 | -159567 |
| GC 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | all | -0.13 | -0.17 | -552205 | -376582 | 2990367 | -1936840 | -0.24 | 35.7 | 1.48 | -133005 | 460904 | -398588 |
| RTY 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | clean | -0.12 | -0.18 | -149835 | -117231 | 547985 | -297188 | -0.21 | 23.8 | 1.39 | -88638 | 309508 | -102888 |
| RTY 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | H1 | -1.30 | -1.39 | -207690 | -161348 | 331239 | -218329 | -0.94 | 17.9 | 2.54 | -77222 | 177043 | -77511 |
| RTY 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | H2 | -1.50 | -1.73 | -116007 | -93060 | 413295 | -153152 | -0.75 | 22.2 | 2.10 | -86876 | 217425 | -91227 |
| RTY 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | all | -0.52 | -0.69 | -163060 | -122215 | 1168861 | -297188 | -0.63 | 22.6 | 1.72 | -87224 | 309508 | -102888 |
| ZN 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | clean | -2.51 | -2.73 | -136478 | -116995 | 2161422 | -197665 | -0.91 | 54.3 | 1.02 | -86343 | 345574 | -91999 |
| ZN 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | H1 | -2.89 | -2.94 | -85936 | -77509 | 500263 | -87958 | -0.81 | 39.3 | 2.47 | -78147 | 149991 | -85469 |
| ZN 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | H2 | 0.65 | 1.25 | -75430 | -72252 | 231473 | -75553 | 0.77 | 30.6 | 2.46 | -80672 | 217328 | -84197 |
| ZN 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | all | -1.80 | -2.15 | -123470 | -103865 | 2665123 | -197665 | -0.82 | 47.0 | 1.55 | -85004 | 345574 | -91999 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | -29.4 | -44.9 | -5.6 | -28.4 | -21.5 / 7.1 | -45.9 / -16.6 | NO |
| RTY 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | -38.3 | -7.6 | 8.6 | 13.0 | -8.5 / 8.1 | 0.9 / 15.3 | NO |
| GC 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | -38.2 | -613.6 | -104.3 | -156.4 | -37.2 / 3.9 | -652.2 / -299.3 | NO |
| CL 30m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m (diag) | -23.3 | -35.3 | 6.5 | 13.2 | -36.4 / 1.1 | 13.0 / 21.8 | NO |
| ZN 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | -54.4 | 10.2 | 15.5 | -18.1 | 9.5 / 12.5 | 16.2 / 28.3 | NO |

INSURANCE count: 0.

## 6. What this says
- Mean reversion to session VWAP does not clear costs. Over 2013-2022 not one of 192 ES cells has even a single year-consistent run (best selection-span Sharpe -0.21); GC, CL and ZN are the same (best -0.08, -0.23, -1.59). Only RTY (2018-2022, a short and low-power window) puts one cell through the rule (30-min, 2.5-sigma, RTH anchor, 60-minute time stop, selection Sharpe +0.22), and the false-survivor test says that is chance: the timing-destroyed grid passes 1.0 cells on average (p(count) = 0.65).
- That single RTY cell loses in the pair window (all-in Sharpe -0.52, uplift -0.07/-0.28/-0.19 on clean/H1/H2, small-sample at 94 trades). The 15 diagnostic cells (best failing cells on each instrument) are read only to show the closest misses; none has an uplift of +0.10 on all spans and none is a candidate by construction.
- Costs: 1 tick per side plus commission on a 1-3 sigma move is a large share of the edge; ZN (1/64 tick, thin sigma) is the worst. Bands at 2.5 sigma are always the least bad cells (fewer trades), a sign that fading more often only buys more cost.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_b4.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/b4/ (`B4_all_selected_scored.csv`).

DONE B4
