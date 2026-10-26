# REPORT C10-S1 - higher-timeframe (30/60/240-minute) trend and mean-reversion on NQ, ES, ZN, 6E, 6J, GC, CL

**Verdict: NO. FOUND 0, LEAD 0.** None of the 62 selected cells keeps a +0.10 Sharpe uplift on clean, H1 and H2 together at 20% share (or at 10, 30, 50%).

## Protocol (pre-registered in PREREG_AUTOPILOT.md, exact grid appended before the first full run)
- 600 cells per instrument (3 bar sizes x 10 rules x 5 exits x 2 sessions x EMA(200 bars) filter), 4,200 cells in total. Rules: EMA 9/21, EMA 20/60, MACD 12/26, Supertrend 10/2 and 14/3, Donchian 20 and 50, linreg-slope 20, RSI(14) 30/70 MR, VWAP-z(3) MR. Exits: opposite signal, ATR(14) trail 2.5x, stop=target 1.5 or 3 ATR(14) of the bar, time stop 8 bars. 30/60-min positions flatten at the 16:55 ET bar open; 240-min positions may carry across the 17:00-18:00 ET break into the next consecutive trading day (not across a weekend) and flatten at that day's 16:55 bar open; gaps realise at the next open.
- Data: purchased 1-minute bars 2013-2026 (RTY excluded), difference back-adjusted at contract rolls; CL 2020-04-17..23 invalidated.
- **Selection on 2013-2022 only**: positive weekly Sharpe in >=7 of 10 calendar years and >=300 trades in 2013-2022; top 10 per instrument by 2013-2022 weekly Sharpe. Clean (2023-08..2025-07), H1 and H2 were read once afterwards. The sleeve is volatility-matched to the pair's clean weekly sigma, then added at 20% (also 10/30/50%).
- Pair = B.Cfg(wk_floor=8, wk_loss_pb=None), computed in a clean process (t3_score imported first). Fill model: 1-minute bars, stop-first, gap fills at the next open. Slippage NQ 1 tick/side, ES/ZN/6E/6J 0.5, GC/CL 1, plus $4.36 per contract round trip (assumption, not calibrated). No netting against the pair's lots.

## 1. Selection and the false-survivor test (200 timing-destroyed replicates per instrument, full grid)
| sym   |   n_rep |   cells pass (>=7/10 yrs, >=300 tr) |   replicate mean |   replicate max |   p(count) |   real top-10 mean Sharpe |   replicate mean |   replicate p95 |   p(top-10) |   real best |   replicate best p95 |
|:------|--------:|------------------------------------:|-----------------:|----------------:|-----------:|--------------------------:|-----------------:|----------------:|------------:|------------:|---------------------:|
| NQ    |     200 |                                  83 |           33.065 |              47 |      0     |                     1.16  |            0.598 |           0.691 |        0    |       1.267 |                1.073 |
| ES    |     200 |                                  48 |           21.87  |              35 |      0     |                     0.791 |            0.509 |           0.619 |        0    |       0.874 |                0.96  |
| ZN    |     200 |                                   8 |            1.715 |               5 |      0     |                     0.178 |            0.204 |           0.408 |        0.51 |       0.337 |                0.599 |
| 6E    |     200 |                                   6 |            8.52  |              17 |      0.86  |                     0.28  |            0.28  |           0.424 |        0.49 |       1.058 |                0.832 |
| 6J    |     200 |                                  13 |            7.155 |              16 |      0.055 |                     0.433 |            0.269 |           0.398 |        0.03 |       0.828 |                0.791 |
| GC    |     200 |                                   8 |           13.325 |              22 |      0.94  |                     0.125 |            0.347 |           0.479 |        0.99 |       0.364 |                0.889 |
| CL    |     200 |                                  49 |           20.19  |              32 |      0     |                     0.65  |            0.441 |           0.566 |        0    |       0.896 |                0.943 |

Reading: for NQ, ES and CL the number of year-consistent cells and the top-10 Sharpe in 2013-2022 are well above what timing-destroyed grids give (p = 0.00), and 6J's top-10 is marginal (p = 0.03). So 30/60-minute trend rules carry real in-sample structure on NQ and ES over 2013-2022 (NQ top-10 mean Sharpe 1.16 against a replicate p95 of 0.69). ZN, 6E and GC show nothing beyond chance (only 6-8 cells pass the year rule, below the replicate mean for 6E and GC).

## 2. Pair-window read of ALL 62 selected cells (nothing omitted)
| cell | description | trades 2013-22 | yrs pos | Sharpe 2013-22 | pair-window all-in Sharpe | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E 1 | 60m rsi[14, 30] exit=brk3.0 day | 797 | 7 | 1.06 | 0.40 | 0.05 / -0.27 / 0.10 | -0.00 | 0.18 | 0.91 | -0.09 | 0.00 | 255 | NO |
| 6E 2 | 60m rsi[14, 30] exit=opp all | 1268 | 8 | 0.30 | 0.39 | 0.00 / -0.18 / 0.16 | -0.01 | 0.52 | 0.95 | -0.16 | 0.00 | 405 | NO |
| 6E 3 | 240m st[10, 2] exit=opp all ema200 | 303 | 7 | 0.21 | 0.68 | 0.19 / 0.03 / -0.09 | 0.10 | -0.54 | 0.93 | -0.03 | 0.50 | 108 | NO |
| 6E 4 | 30m rsi[14, 30] exit=opp all | 1943 | 7 | 0.15 | -0.81 | -0.15 / -0.57 / 0.09 | -0.18 | 0.45 | 0.30 | -0.31 | 0.00 | 606 | NO |
| 6E 5 | 240m st[14, 3] exit=time8 all | 332 | 7 | 0.02 | 0.30 | 0.11 / 0.10 / -0.27 | 0.00 | -0.23 | 0.70 | -0.17 | 0.33 | 111 | NO |
| 6E 6 | 240m st[14, 3] exit=opp all | 351 | 7 | -0.05 | 0.19 | 0.14 / -0.07 / -0.30 | -0.01 | -0.18 | 0.65 | -0.18 | 0.25 | 118 | NO |
| 6J 1 | 240m lr[20] exit=time8 all | 550 | 8 | 0.83 | -0.83 | -0.13 / 0.05 / -0.25 | -0.13 | -0.02 | 0.08 | -0.27 | 0.00 | 171 | NO |
| 6J 2 | 240m st[10, 2] exit=brk3.0 all | 536 | 8 | 0.62 | -0.38 | -0.12 / 0.06 / -0.00 | -0.09 | 0.18 | 0.28 | -0.22 | 0.00 | 184 | NO |
| 6J 3 | 240m lr[20] exit=opp all | 647 | 8 | 0.59 | -0.76 | -0.13 / 0.20 / -0.26 | -0.12 | -0.02 | 0.13 | -0.26 | 0.00 | 204 | NO |
| 6J 4 | 240m st[10, 2] exit=opp all | 598 | 8 | 0.49 | -0.40 | -0.11 / -0.22 / 0.17 | -0.09 | 0.21 | 0.34 | -0.22 | 0.00 | 212 | NO |
| 6J 5 | 240m lr[20] exit=brk3.0 all | 564 | 7 | 0.42 | -0.37 | -0.05 / 0.18 / -0.15 | -0.04 | 0.21 | 0.37 | -0.16 | 0.00 | 180 | NO |
| 6J 6 | 240m st[14, 3] exit=opp all | 359 | 8 | 0.37 | -0.01 | -0.10 / 0.13 / 0.18 | -0.02 | 0.32 | 0.55 | -0.17 | 0.00 | 120 | NO |
| 6J 7 | 60m don[50] exit=time8 all ema200 | 417 | 7 | 0.31 | 0.53 | 0.02 / 0.13 / 0.17 | 0.06 | 0.28 | 0.78 | -0.05 | 0.50 | 128 | NO |
| 6J 8 | 240m ema[9, 21] exit=time8 all | 447 | 7 | 0.27 | 0.71 | 0.12 / -0.02 / 0.17 | 0.10 | 0.19 | 0.88 | -0.01 | 0.33 | 145 | NO |
| 6J 9 | 240m st[14, 3] exit=brk3.0 all | 357 | 8 | 0.26 | -0.32 | -0.13 / 0.10 / 0.06 | -0.06 | 0.33 | 0.32 | -0.21 | 0.00 | 118 | NO |
| 6J 10 | 240m don[20] exit=opp all | 319 | 7 | 0.18 | -0.40 | -0.13 / -0.10 / 0.17 | -0.07 | 0.19 | 0.35 | -0.19 | 0.00 | 98 | NO |
| CL 1 | 60m st[14, 3] exit=brk1.5 day ema200 | 573 | 9 | 0.90 | -0.94 | -0.06 / -0.61 / -0.75 | -0.35 | 0.31 | 0.04 | -0.53 | 0.00 | 184 | NO |
| CL 2 | 60m st[14, 3] exit=brk3.0 day ema200 | 572 | 8 | 0.69 | -1.08 | -0.15 / -0.40 / -0.72 | -0.35 | 0.16 | 0.03 | -0.53 | 0.00 | 183 | NO |
| CL 3 | 240m lr[20] exit=brk1.5 all | 564 | 7 | 0.66 | -0.14 | -0.13 / -0.14 / -0.12 | -0.13 | 0.08 | 0.40 | -0.35 | 0.00 | 190 | NO |
| CL 4 | 60m st[14, 3] exit=opp day ema200 | 573 | 8 | 0.66 | -1.18 | -0.23 / -0.31 / -0.76 | -0.41 | 0.14 | 0.02 | -0.60 | 0.00 | 184 | NO |
| CL 5 | 240m lr[20] exit=time8 all | 522 | 7 | 0.63 | 0.41 | -0.15 / 0.01 / 0.34 | -0.02 | -0.01 | 0.82 | -0.21 | 0.00 | 174 | NO |
| CL 6 | 60m macd[12, 26] exit=opp all | 1848 | 7 | 0.63 | 0.29 | 0.15 / 0.02 / -0.08 | 0.02 | -0.30 | 0.82 | -0.12 | 0.50 | 586 | NO |
| CL 7 | 30m don[50] exit=brk3.0 all ema200 | 753 | 7 | 0.60 | 0.82 | 0.14 / -0.01 / 0.52 | 0.18 | -0.14 | 0.95 | -0.03 | 0.25 | 262 | NO |
| CL 8 | 30m ema[20, 60] exit=opp all | 1883 | 7 | 0.58 | -0.22 | 0.07 / -0.12 / -0.29 | -0.10 | -0.37 | 0.48 | -0.24 | 0.00 | 613 | NO |
| CL 9 | 240m lr[20] exit=brk1.5 all ema200 | 303 | 8 | 0.57 | 0.48 | 0.10 / -0.10 / 0.15 | 0.07 | 0.06 | 0.80 | -0.13 | 0.75 | 107 | NO |
| CL 10 | 240m lr[20] exit=brk3.0 all | 536 | 7 | 0.57 | 0.08 | -0.09 / -0.18 / 0.06 | -0.07 | -0.33 | 0.65 | -0.31 | 0.00 | 175 | NO |
| ES 1 | 60m st[14, 3] exit=trail2.5 day ema200 | 631 | 8 | 0.87 | 0.37 | -0.07 / 0.26 / -0.19 | -0.08 | -0.30 | 0.78 | -0.31 | 0.00 | 210 | NO |
| ES 2 | 30m ema[20, 60] exit=trail2.5 day | 979 | 7 | 0.84 | -0.33 | -0.15 / 0.37 / -0.52 | -0.20 | -0.19 | 0.27 | -0.36 | 0.00 | 332 | NO |
| ES 3 | 60m ema[9, 21] exit=opp all ema200 | 1265 | 9 | 0.82 | 0.17 | -0.12 / -0.08 / -0.44 | -0.20 | -0.13 | 0.70 | -0.48 | 0.00 | 397 | NO |
| ES 4 | 60m st[14, 3] exit=trail2.5 all ema200 | 881 | 7 | 0.81 | 0.24 | -0.13 / -0.10 / 0.07 | -0.11 | -0.22 | 0.73 | -0.32 | 0.00 | 277 | NO |
| ES 5 | 60m ema[9, 21] exit=trail2.5 all ema200 | 1181 | 8 | 0.81 | 0.11 | -0.02 / -0.05 / -0.67 | -0.21 | -0.18 | 0.75 | -0.45 | 0.00 | 364 | NO |
| ES 6 | 60m macd[12, 26] exit=trail2.5 all ema200 | 981 | 7 | 0.81 | -0.75 | -0.25 / -0.67 / -0.46 | -0.39 | -0.08 | 0.10 | -0.60 | 0.00 | 296 | NO |
| ES 7 | 240m st[14, 3] exit=brk1.5 all | 345 | 7 | 0.75 | -0.60 | -0.72 / -0.44 / -0.15 | -0.58 | -0.05 | 0.10 | -1.16 | 0.00 | 138 | NO |
| ES 8 | 30m macd[12, 26] exit=trail2.5 all ema200 | 1943 | 7 | 0.75 | -1.15 | -0.22 / -0.80 / -1.30 | -0.61 | -0.23 | 0.04 | -0.92 | 0.00 | 618 | NO |
| ES 9 | 30m st[14, 3] exit=trail2.5 all ema200 | 1678 | 8 | 0.72 | -0.99 | -0.22 / -0.28 / -1.35 | -0.53 | 0.08 | 0.06 | -0.77 | 0.00 | 601 | NO |
| ES 10 | 60m don[20] exit=trail2.5 all ema200 | 737 | 7 | 0.72 | -0.38 | -0.19 / -0.25 / -0.54 | -0.32 | -0.12 | 0.34 | -0.55 | 0.00 | 253 | NO |
| GC 1 | 30m ema[20, 60] exit=time8 all ema200 | 1198 | 7 | 0.36 | -0.76 | -0.09 / -1.33 / -1.24 | -0.58 | 0.01 | 0.05 | -0.99 | 0.00 | 365 | NO |
| GC 2 | 60m macd[12, 26] exit=trail2.5 day | 907 | 7 | 0.28 | -0.53 | -0.12 / -0.48 / -1.68 | -0.62 | 0.41 | 0.15 | -1.00 | 0.00 | 264 | NO |
| GC 3 | 30m ema[20, 60] exit=time8 day ema200 | 661 | 7 | 0.16 | -0.04 | 0.14 / -0.28 / -0.76 | -0.14 | -0.04 | 0.41 | -0.46 | 0.00 | 167 | NO |
| GC 4 | 60m don[50] exit=trail2.5 all ema200 | 396 | 7 | 0.15 | 0.04 | -0.04 / 0.31 / -1.06 | -0.21 | -0.16 | 0.46 | -0.69 | 0.00 | 123 | NO |
| GC 5 | 60m don[50] exit=time8 all | 518 | 7 | 0.14 | -0.04 | 0.01 / 1.25 / -1.77 | -0.25 | -0.36 | 0.52 | -0.81 | 0.00 | 160 | NO |
| GC 6 | 60m don[20] exit=trail2.5 all ema200 | 734 | 7 | 0.07 | -0.51 | -0.30 / -1.30 / -0.70 | -0.56 | 0.18 | 0.10 | -1.01 | 0.00 | 211 | NO |
| GC 7 | 60m st[10, 2] exit=brk3.0 all ema200 | 1277 | 7 | -0.05 | 0.49 | 0.03 / 1.19 / -0.85 | -0.06 | 0.20 | 0.74 | -0.54 | 0.00 | 418 | NO |
| GC 8 | 60m don[20] exit=brk1.5 day ema200 | 447 | 7 | -0.12 | -0.92 | -0.48 / -0.13 / -0.76 | -0.53 | -0.01 | 0.02 | -0.89 | 0.00 | 110 | NO |
| NQ 1 | 60m ema[9, 21] exit=trail2.5 day | 1260 | 9 | 1.27 | 0.33 | 0.07 / -0.30 / -0.73 | -0.16 | -0.18 | 0.72 | -0.51 | 0.00 | 390 | NO |
| NQ 2 | 60m don[20] exit=trail2.5 day ema200 | 547 | 8 | 1.21 | 0.62 | -0.04 / 0.32 / -0.10 | 0.01 | -0.50 | 0.95 | -0.26 | 0.25 | 182 | NO |
| NQ 3 | 60m ema[9, 21] exit=brk3.0 day ema200 | 714 | 7 | 1.20 | -0.10 | -0.25 / 0.59 / -0.75 | -0.25 | -0.16 | 0.44 | -0.60 | 0.00 | 218 | NO |
| NQ 4 | 60m ema[9, 21] exit=opp day ema200 | 758 | 7 | 1.17 | -0.20 | -0.23 / 0.22 / -0.86 | -0.31 | -0.01 | 0.41 | -0.64 | 0.00 | 233 | NO |
| NQ 5 | 60m don[20] exit=opp day ema200 | 547 | 8 | 1.17 | 0.86 | -0.00 / 0.54 / -0.04 | 0.08 | -0.63 | 0.95 | -0.20 | 0.00 | 182 | NO |
| NQ 6 | 60m don[20] exit=brk3.0 day ema200 | 547 | 8 | 1.15 | 0.77 | -0.04 / 0.38 / 0.15 | 0.06 | -0.66 | 0.86 | -0.28 | 0.25 | 182 | NO |
| NQ 7 | 60m ema[9, 21] exit=trail2.5 day ema200 | 737 | 7 | 1.14 | -0.31 | -0.28 / 0.14 / -0.64 | -0.30 | -0.13 | 0.25 | -0.62 | 0.00 | 224 | NO |
| NQ 8 | 30m ema[20, 60] exit=trail2.5 all | 1717 | 7 | 1.12 | 0.75 | -0.05 / 1.08 / -0.26 | 0.02 | -0.41 | 0.94 | -0.28 | 0.33 | 555 | NO |
| NQ 9 | 30m ema[20, 60] exit=trail2.5 day | 1006 | 7 | 1.09 | 0.33 | 0.11 / 0.73 / -0.95 | -0.07 | -0.49 | 0.74 | -0.38 | 0.00 | 327 | NO |
| NQ 10 | 30m st[14, 3] exit=trail2.5 all ema200 | 1753 | 8 | 1.08 | 0.16 | -0.11 / -0.32 / -0.51 | -0.24 | -0.13 | 0.53 | -0.54 | 0.00 | 595 | NO |
| ZN 1 | 240m rsi[14, 30] exit=time8 all | 343 | 7 | 0.34 | 0.38 | 0.11 / 0.02 / -0.07 | 0.00 | -0.55 | 0.84 | -0.13 | 0.33 | 117 | NO |
| ZN 2 | 240m rsi[14, 30] exit=opp all | 341 | 8 | 0.29 | 0.32 | 0.09 / 0.04 / -0.07 | -0.00 | -0.55 | 0.85 | -0.11 | 0.25 | 115 | NO |
| ZN 3 | 60m st[14, 3] exit=brk3.0 day ema200 | 587 | 7 | 0.23 | -0.46 | -0.17 / -0.20 / -0.26 | -0.33 | -0.03 | 0.58 | -0.42 | 0.00 | 213 | NO |
| ZN 4 | 240m st[10, 2] exit=opp all ema200 | 352 | 7 | 0.20 | -0.33 | -0.02 / -0.40 / -0.00 | -0.13 | 0.34 | 0.44 | -0.25 | 0.00 | 123 | NO |
| ZN 5 | 240m st[10, 2] exit=time8 all ema200 | 330 | 7 | 0.16 | -0.44 | -0.06 / -0.48 / -0.02 | -0.17 | 0.34 | 0.29 | -0.31 | 0.00 | 114 | NO |
| ZN 6 | 240m ema[9, 21] exit=trail2.5 all | 462 | 7 | 0.12 | -0.92 | -0.08 / -0.63 / -0.24 | -0.26 | 0.05 | 0.18 | -0.39 | 0.00 | 165 | NO |
| ZN 7 | 240m ema[9, 21] exit=opp all | 531 | 7 | 0.09 | -0.37 | 0.05 / -0.52 / -0.20 | -0.15 | 0.13 | 0.41 | -0.25 | 0.00 | 195 | NO |
| ZN 8 | 240m rsi[14, 30] exit=brk1.5 all | 380 | 7 | 0.01 | 0.61 | 0.14 / 0.12 / -0.08 | 0.03 | -0.58 | 0.96 | -0.05 | 0.17 | 127 | NO |

(uplift = change in the pair's weekly Sharpe from adding the vol-matched sleeve at 20% share; verdict = additive SURVIVOR gate: +0.10 on clean, H1 and H2 each, worst week within the share, standalone Sharpe above the own random-entry null p95, bootstrap 90% lower bound > 0, worst-decile correlation <= +0.30.)

## 3. Gate counts over the 62 selected cells (20% share)
| gate | cells passing |
|---|---|
| uplift >= +0.10 on clean, H1 and H2 together | 0 |
| all-in uplift > 0 | 17 |
| bootstrap 90% lower bound > 0 | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 5 (the random-entry null itself is cost-dominated, so this is weak) |
| worst-decile correlation <= +0.30 | 54 |
| plateau (>=75% of +-25% neighbours keep >=75% of the all-in uplift) | 1 |
| small-sample (<100 trades in the pair window) | 1 (smallest: 98) |
| all gates (verdict PASS at 20%) | 0 |

Per span at 20% share: clean uplift >= +0.10 in 10 cells, H1 in 18, H2 in 10 - never the same cells. The mean all-in uplift is -0.13; at 2x slippage it is -0.16.

## 4. What this says
- Selecting on 2013-2022 finds structure on NQ and ES (better than chance by the replicate test), but it does not carry into 2023-2026 as an addition to the pair: NQ top cells earn pair-window Sharpe up to 0.86 yet their uplift on the pair is negative or inconsistent across spans (H2 uplift is negative for most NQ and ES cells), and every bootstrap lower bound is at or below zero. NQ trend rules are, in the pair window, positively exposed to the same flips as the pair (the sleeves are not hedges: worst-decile correlation spans -0.66 to 0.52 on 17 weeks, too noisy to call).
- The 240-minute FX/rates cells (6E, 6J, ZN) have pair-window Sharpe that swings sign with the cell and few trades (98-212), no plateau.
- The few cells that look good on one span (e.g. NQ 30m EMA 20/60 trail: H1 uplift +1.08) fail the other (H2 -0.26) - consistent with a period-specific rather than structural effect.

## 5. Constant-risk framing
Constant-risk (total risk fixed; the pair shrinks to fund the sleeve), 30% share, all-in: net cost is -3.1% at best and -33% at the median (range -64% to -3%) against the 5% limit. 7 of the 62 cells reach a 20% better CVaR5 or worst week (6E 240m ST(10,2) opposite +ema200: CVaR5 +21.6%; 6J 240m linreg exit brk3: +21.9%; 6J 60m Donchian 50 time8: worst week +21.2%, CVaR5 +25.7%; 6J 240m EMA 9/21 time8: worst week +23.1%, CVaR5 +25.1%; ZN 240m ST(10,2) opp and time8; ZN 240m RSI brk1.5), but each costs 21-38% of net, so none is INSURANCE. Full numbers: columns const10..const50 in `C10_S1_all_selected_scored.csv`.

## 6. Executability and margin
All seven are CME-group futures (CME/CBOT/COMEX/NYMEX): executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's list). Margins unverified: GC ~9% of notional (~$37k per contract) is the only figure from earlier work; 240-minute positions are held overnight so overnight margin applies. Nothing passes, so no margin decision is needed.

## 7. Limitations
1-minute bars with stop-first fills; no queue model; costs are assumptions; no netting against the pair's lots; the false-survivor test uses random bar-end entries with the same trade count (alternating sides), which loses to cost, so own-null ranks above 0.95 are weak evidence; 6E/GC/ZN/6J selected fewer than 10 year-consistent cells (6/8/8/13 pass), so they have fewer than 10 rows; the sleeve's vol-matching scale factor is estimated on 2013-2022.

Runtime: real runs ~2 s per instrument; 200 replicates over the full grid ~3 minutes per instrument on 4 workers; scoring (bootstrap, nulls, plateau) ~10 minutes. Code: ap_c10_s1_*.py in code/census/night_ins/; data in outputs/autopilot/c10/s1/.

DONE C10_S1
