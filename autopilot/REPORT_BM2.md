# REPORT BM2 - Amihud illiquidity day (BM batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 13 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.08; best pair-window standalone Sharpe +0.95.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see IDEAS_BM.md / PREREG_AUTOPILOT.md BATCH BM. Amihud illiquidity day. Null: drift- and clock-matched random entries.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      12 |         12 |         0 |               1.167 |                1 |          0 |            3 |
| CL    |      12 |         12 |         0 |               0.831 |                1 |          0 |            3 |
| ES    |      12 |         12 |         0 |               0.207 |                1 |          0 |            3 |
| GC    |      12 |         12 |         0 |               0.302 |                1 |          0 |            3 |
| NQ    |      12 |         12 |         2 |               0.687 |                2 |          2 |            3 |
| RTY   |      12 |         12 |         4 |               0.758 |                2 |          4 |            3 |
| YM    |      12 |         12 |         6 |               1.061 |                2 |          6 |            3 |
| ZN    |      12 |          6 |         1 |               0.294 |                2 |          1 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            1.895 |               5 |      1     |                     nan     |            0.748 |           1.24  |  nan     |     nan     |                1.582 |
| NQ    |     200 |                    2 |            2.415 |               6 |      0.74  |                       0.253 |            0.815 |           1.232 |    0.88  |       0.42  |                1.739 |
| RTY   |     200 |                    4 |            1.53  |               5 |      0.055 |                       0.422 |            0.747 |           1.257 |    0.7   |       0.758 |                1.62  |
| YM    |     200 |                    6 |            2.045 |               5 |      0     |                       0.568 |            0.765 |           1.275 |    0.72  |       1.061 |                1.693 |
| GC    |     200 |                    0 |            1.985 |               6 |      1     |                     nan     |            0.773 |           1.371 |  nan     |     nan     |                1.754 |
| CL    |     200 |                    0 |            1.425 |               5 |      1     |                     nan     |            0.703 |           1.303 |  nan     |     nan     |                1.658 |
| ZN    |     200 |                    1 |            0.31  |               2 |      0.265 |                       0.294 |            0.5   |           1.132 |    0.205 |       0.294 |                1.133 |
| BTC   |     200 |                    0 |            1.555 |               4 |      1     |                     nan     |            0.758 |           1.381 |  nan     |     nan     |                1.658 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | prior-day |ret|/volume pct>=90 of 60d mode=against | 68 | 1 | 0.21 | 0.24 | 0.04 | -0.36 / 1.20 | -0.00 / 0.11 / -0.18 | -0.04 | 0.29 | 0.61 | -0.15 | 0.00 | 102 | diag |
| ES 2 (diag) | prior-day |ret|/volume pct>=80 of 120d mode=against | 125 | 1 | 0.16 | -0.24 | -0.01 | -0.51 / 1.46 | -0.01 / 0.04 / -0.09 | -0.04 | 0.51 | 0.62 | -0.13 | 0.00 | 191 | diag |
| ES 3 (diag) | prior-day |ret|/volume pct>=80 of 60d mode=with | 120 | 1 | 0.13 | -0.07 | 0.21 | 0.36 / 1.41 | -0.00 / -0.20 / 0.06 | -0.03 | -0.47 | 0.68 | -0.19 | 0.00 | 187 | diag |
| NQ 1 | prior-day |ret|/volume pct>=80 of 120d mode=against | 123 | 2 | 0.42 | 0.29 | 0.12 | -0.31 / 1.33 | 0.05 / 0.13 / -0.13 | 0.02 | -0.53 | 0.68 | -0.14 | 0.75 | 200 | NO |
| NQ 2 | prior-day |ret|/volume pct>=90 of 60d mode=with | 64 | 2 | 0.09 | -0.57 | 0.18 | 0.32 / 1.60 | -0.04 / -0.10 / 0.02 | -0.04 | 0.53 | 0.56 | -0.20 | 0.00 | 104 | NO |
| NQ 3 (diag) | prior-day |ret|/volume pct>=90 of 120d mode=against | 69 | 1 | 0.69 | 0.59 | 0.05 | -0.95 / 1.47 | 0.09 / -0.05 / -0.26 | -0.01 | -0.23 | 0.61 | -0.16 | 0.00 | 109 | diag |
| NQ 4 (diag) | prior-day |ret|/volume pct>=90 of 120d mode=long | 69 | 1 | 0.37 | 0.16 | 0.33 | 0.28 / 1.56 | 0.04 / 0.11 / -0.20 | -0.01 | 0.56 | 0.69 | -0.21 | 0.00 | 109 | diag |
| NQ 5 (diag) | prior-day |ret|/volume pct>=80 of 60d mode=against | 109 | 1 | 0.17 | 0.28 | 0.13 | 0.08 / 1.50 | -0.00 / 0.17 / -0.21 | -0.01 | -0.12 | 0.62 | -0.16 | 0.00 | 181 | diag |
| RTY 1 | prior-day |ret|/volume pct>=90 of 60d mode=with | 64 | 2 | 0.76 | -0.36 | 0.75 | 0.72 / 1.20 | 0.07 / 0.19 / 0.16 | 0.08 | -0.26 | 0.94 | -0.08 | 0.67 | 100 | NO |
| RTY 2 | prior-day |ret|/volume pct>=90 of 120d mode=with | 64 | 2 | 0.56 | -0.26 | 0.67 | 0.82 / 1.49 | 0.02 / 0.10 / 0.21 | 0.04 | -0.29 | 0.85 | -0.12 | 0.33 | 99 S | NO |
| RTY 3 | prior-day |ret|/volume pct>=90 of 60d mode=long | 64 | 2 | 0.20 | -0.87 | 0.29 | 0.42 / 1.57 | 0.05 / 0.26 / -0.10 | 0.04 | 0.46 | 0.79 | -0.11 | 0.33 | 100 | NO |
| RTY 4 | prior-day |ret|/volume pct>=80 of 120d mode=with | 114 | 2 | 0.16 | -0.45 | 0.04 | -0.03 / 1.58 | -0.04 / 0.12 / -0.10 | -0.06 | -0.30 | 0.50 | -0.28 | 0.00 | 181 | NO |
| RTY 5 (diag) | prior-day |ret|/volume pct>=80 of 60d mode=with | 112 | 1 | 0.39 | -0.50 | 0.51 | 0.74 / 1.44 | 0.02 / 0.25 / 0.23 | 0.07 | -0.08 | 0.84 | -0.11 | 0.25 | 179 | diag |
| RTY 6 (diag) | prior-day |ret|/volume pct>=90 of 120d mode=long | 64 | 1 | 0.10 | -0.47 | 0.08 | 0.05 / 1.58 | 0.04 / 0.00 / -0.04 | 0.01 | 0.40 | 0.55 | -0.13 | 0.67 | 99 S | diag |
| RTY 7 (diag) | prior-day |ret|/volume pct>=80 of 120d mode=long | 114 | 1 | -0.28 | -0.57 | 0.12 | 0.69 / 1.70 | -0.05 / 0.62 / -0.11 | 0.02 | 0.14 | 0.62 | -0.16 | 0.50 | 181 | diag |
| YM 1 | prior-day |ret|/volume pct>=80 of 60d mode=with | 125 | 2 | 1.06 | -0.30 | 0.21 | -1.15 / 1.39 | 0.18 / -0.11 / -0.41 | -0.00 | -0.19 | 0.62 | -0.16 | 0.25 | 189 | NO |
| YM 2 | prior-day |ret|/volume pct>=80 of 120d mode=with | 132 | 2 | 1.02 | -0.11 | 0.19 | -1.28 / 1.57 | 0.18 / -0.11 / -0.44 | -0.01 | -0.14 | 0.60 | -0.17 | 0.25 | 201 | NO |
| YM 3 | prior-day |ret|/volume pct>=80 of 120d mode=long | 132 | 2 | 0.56 | -0.17 | 0.44 | 0.21 / 1.65 | 0.08 / 0.18 / 0.06 | 0.07 | 0.03 | 0.73 | -0.08 | 0.50 | 201 | NO |
| YM 4 | prior-day |ret|/volume pct>=90 of 120d mode=with | 79 | 2 | 0.34 | -0.45 | 0.07 | -0.47 / 1.45 | 0.06 / -0.03 / -0.25 | -0.02 | -0.11 | 0.59 | -0.16 | 0.00 | 110 | NO |
| YM 5 | prior-day |ret|/volume pct>=80 of 60d mode=long | 125 | 2 | 0.28 | -0.40 | 0.03 | -0.34 / 1.45 | 0.03 / 0.08 / -0.03 | 0.00 | -0.01 | 0.42 | -0.17 | 0.75 | 189 | NO |
| YM 6 | prior-day |ret|/volume pct>=90 of 60d mode=with | 71 | 2 | 0.16 | -0.41 | 0.09 | -0.07 / 1.50 | 0.01 / -0.08 / -0.10 | -0.03 | -0.19 | 0.56 | -0.17 | 0.00 | 107 | NO |
| YM 7 (diag) | prior-day |ret|/volume pct>=90 of 120d mode=long | 79 | 1 | 0.65 | -0.15 | 0.22 | -0.49 / 1.67 | 0.10 / 0.11 / -0.25 | 0.01 | -0.11 | 0.61 | -0.15 | 0.33 | 110 | diag |
| YM 8 (diag) | prior-day |ret|/volume pct>=90 of 60d mode=long | 71 | 1 | 0.46 | -0.24 | 0.16 | -0.38 / 1.22 | 0.05 / 0.05 / -0.19 | -0.02 | -0.23 | 0.58 | -0.16 | 0.00 | 107 | diag |
| YM 9 (diag) | prior-day |ret|/volume pct>=90 of 60d mode=against | 71 | 0 | -0.25 | 0.25 | -0.19 | -0.05 / 1.47 | -0.08 / 0.03 / 0.04 | -0.06 | 0.18 | 0.45 | -0.19 | 0.00 | 107 | diag |
| GC 1 (diag) | prior-day |ret|/volume pct>=80 of 60d mode=with | 124 | 1 | 0.30 | -0.05 | -0.35 | -0.88 / 1.67 | 0.03 / -0.39 / -0.89 | -0.24 | 0.02 | 0.31 | -0.51 | 0.00 | 193 | diag |
| GC 2 (diag) | prior-day |ret|/volume pct>=90 of 120d mode=against | 73 | 1 | 0.16 | -0.20 | 0.34 | 0.54 / 1.40 | 0.00 / -0.15 / 0.11 | 0.01 | 0.01 | 0.73 | -0.31 | 0.33 | 113 | diag |
| GC 3 (diag) | prior-day |ret|/volume pct>=90 of 60d mode=against | 70 | 1 | -0.00 | -0.23 | 0.27 | 0.54 / 1.53 | -0.05 / -0.51 / 0.39 | -0.02 | -0.03 | 0.69 | -0.33 | 0.00 | 107 | diag |
| CL 1 (diag) | prior-day |ret|/volume pct>=80 of 120d mode=against | 111 | 1 | 0.83 | -0.25 | -0.44 | -1.26 / 1.30 | 0.09 / -0.02 / -1.21 | -0.28 | -0.05 | 0.29 | -0.53 | 0.00 | 192 | diag |
| CL 2 (diag) | prior-day |ret|/volume pct>=80 of 60d mode=against | 114 | 1 | 0.67 | -0.30 | -0.29 | -1.04 / 1.38 | 0.07 / -0.11 / -0.78 | -0.19 | 0.08 | 0.41 | -0.40 | 0.00 | 180 | diag |
| CL 3 (diag) | prior-day |ret|/volume pct>=90 of 120d mode=against | 64 | 1 | 0.28 | -0.30 | -0.33 | -0.84 / 1.27 | 0.02 / -0.10 / -0.68 | -0.19 | 0.34 | 0.29 | -0.42 | 0.00 | 99 S | diag |
| ZN 1 | prior-day |ret|/volume pct>=80 of 120d mode=long | 96 | 2 | 0.29 | -0.92 | -0.08 | -0.71 / 0.28 | 0.03 / -0.29 / -0.15 | -0.20 | -0.12 | 0.94 | -0.22 | 0.00 | 154 | NO |
| ZN 2 (diag) | prior-day |ret|/volume pct>=90 of 60d mode=with | 59 | 1 | 0.02 | -0.72 | -0.09 | -0.32 / 0.57 | -0.05 / 0.04 / -0.14 | -0.18 | 0.24 | 0.81 | -0.23 | 0.00 | 94 S | diag |
| ZN 3 (diag) | prior-day |ret|/volume pct>=90 of 120d mode=long | 54 | 1 | -0.06 | -0.54 | -0.16 | -0.41 / 0.58 | -0.03 / -0.07 / -0.16 | -0.16 | -0.09 | 0.85 | -0.22 | 0.00 | 83 S | diag |
| ZN 4 (diag) | prior-day |ret|/volume pct>=90 of 60d mode=long | 59 | 0 | -0.16 | -0.50 | 0.00 | 0.36 / 0.30 | -0.03 / -0.06 / -0.01 | -0.14 | -0.20 | 0.88 | -0.18 | 0.00 | 94 S | diag |
| BTC 1 (diag) | prior-day |ret|/volume pct>=90 of 120d mode=against | 86 | 1 | 1.17 | -0.02 | 0.81 | 0.06 / 1.52 | 0.19 / -0.12 / 0.04 | 0.10 | 0.26 | 0.95 | -0.04 | 1.00 | 108 | diag |
| BTC 2 (diag) | prior-day |ret|/volume pct>=80 of 120d mode=against | 146 | 1 | 1.12 | 0.64 | 0.95 | 0.69 / 1.47 | 0.16 / 0.18 / 0.02 | 0.12 | 0.23 | 0.95 | -0.03 | 1.00 | 187 | diag |
| BTC 3 (diag) | prior-day |ret|/volume pct>=90 of 60d mode=against | 70 | 1 | 0.90 | 0.27 | 0.23 | -0.74 / 1.42 | 0.08 / -0.41 / -0.05 | -0.04 | 0.25 | 0.71 | -0.20 | 0.00 | 95 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 13 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 15 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 2 |
| worst-decile corr <= +0.30 | 31 |
| plateau >= 0.75 | 4 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 7 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC prior-day |ret|/volume pct>=80 of 120d mode=against (diag) | clean | 1.07 | 2.04 | -98896 | -86378 | 757747 | -139802 | 1.29 | 36.2 | 1.62 | -86068 | 318133 | -100117 |
| BTC prior-day |ret|/volume pct>=80 of 120d mode=against (diag) | H1 | 1.03 | 1.94 | -111556 | -93895 | 274252 | -123363 | 0.93 | 21.4 | 3.01 | -80996 | 156681 | -83706 |
| BTC prior-day |ret|/volume pct>=80 of 120d mode=against (diag) | H2 | 0.30 | 0.49 | -88003 | -56025 | 192092 | -126955 | 0.30 | 16.7 | 2.50 | -81143 | 220008 | -81178 |
| BTC prior-day |ret|/volume pct>=80 of 120d mode=against (diag) | all | 0.95 | 1.77 | -104827 | -86927 | 757747 | -139802 | 1.70 | 29.8 | 2.02 | -84987 | 318133 | -100117 |
| CL prior-day |ret|/volume pct>=80 of 60d mode=against (diag) | clean | 0.62 | 1.26 | -93853 | -80648 | 404399 | -127827 | 1.40 | 36.2 | 1.53 | -90280 | 271845 | -97493 |
| CL prior-day |ret|/volume pct>=80 of 60d mode=against (diag) | H1 | -1.74 | -2.09 | -59555 | -56797 | 258502 | -61511 | -0.71 | 42.9 | 2.72 | -77633 | 146587 | -78333 |
| CL prior-day |ret|/volume pct>=80 of 60d mode=against (diag) | H2 | -1.18 | -1.49 | -454223 | -369389 | 1997959 | -517232 | -0.51 | 41.7 | 1.70 | -106767 | 262257 | -118587 |
| CL prior-day |ret|/volume pct>=80 of 60d mode=against (diag) | all | -0.29 | -0.40 | -240743 | -163439 | 1997959 | -517232 | -0.32 | 38.7 | 1.73 | -93034 | 271845 | -118587 |
| ES prior-day |ret|/volume pct>=80 of 60d mode=with (diag) | clean | 0.13 | 0.16 | -150590 | -108783 | 611232 | -421308 | 0.19 | 31.4 | 1.46 | -80641 | 267539 | -86105 |
| ES prior-day |ret|/volume pct>=80 of 60d mode=with (diag) | H1 | -0.79 | -1.02 | -134922 | -107392 | 273794 | -186299 | -0.61 | 42.9 | 2.63 | -77848 | 157411 | -78764 |
| ES prior-day |ret|/volume pct>=80 of 60d mode=with (diag) | H2 | 1.10 | 1.82 | -149721 | -103336 | 355785 | -154431 | 1.02 | 27.8 | 2.54 | -77281 | 217425 | -77416 |
| ES prior-day |ret|/volume pct>=80 of 60d mode=with (diag) | all | 0.21 | 0.29 | -155157 | -110711 | 857112 | -421308 | 0.36 | 32.7 | 1.89 | -79791 | 267539 | -86105 |
| GC prior-day |ret|/volume pct>=90 of 120d mode=against (diag) | clean | 0.13 | 0.19 | -142960 | -110356 | 379384 | -243900 | 0.31 | 25.7 | 1.46 | -83546 | 261704 | -92603 |
| GC prior-day |ret|/volume pct>=90 of 120d mode=against (diag) | H1 | 0.40 | 0.54 | -444621 | -328198 | 1334694 | -696944 | 0.22 | 14.3 | 2.68 | -118211 | 295623 | -150609 |
| GC prior-day |ret|/volume pct>=90 of 120d mode=against (diag) | H2 | 0.87 | 1.63 | -193425 | -118778 | 479706 | -228151 | 0.81 | 11.1 | 2.59 | -81089 | 217425 | -82524 |
| GC prior-day |ret|/volume pct>=90 of 120d mode=against (diag) | all | 0.34 | 0.50 | -227900 | -155842 | 1334694 | -696944 | 0.60 | 20.8 | 1.92 | -91351 | 308923 | -150609 |
| NQ prior-day |ret|/volume pct>=80 of 120d mode=against | clean | 0.42 | 0.72 | -109977 | -84316 | 450885 | -265079 | 0.85 | 37.1 | 1.51 | -79795 | 267200 | -82544 |
| NQ prior-day |ret|/volume pct>=80 of 120d mode=against | H1 | 1.00 | 2.19 | -86607 | -75413 | 287749 | -95623 | 0.83 | 32.1 | 2.95 | -76816 | 162570 | -76932 |
| NQ prior-day |ret|/volume pct>=80 of 120d mode=against | H2 | -1.13 | -1.37 | -190547 | -167473 | 643306 | -202826 | -0.67 | 44.4 | 2.36 | -81174 | 217425 | -84243 |
| NQ prior-day |ret|/volume pct>=80 of 120d mode=against | all | 0.12 | 0.19 | -145504 | -108012 | 643306 | -265079 | 0.30 | 38.1 | 1.92 | -79837 | 267200 | -84243 |
| RTY prior-day |ret|/volume pct>=90 of 60d mode=with | clean | 0.75 | 1.55 | -104661 | -81545 | 488287 | -190654 | 1.40 | 18.1 | 1.53 | -86742 | 304313 | -101514 |
| RTY prior-day |ret|/volume pct>=90 of 60d mode=with | H1 | 0.50 | 0.88 | -116588 | -101336 | 299038 | -135538 | 0.42 | 21.4 | 3.02 | -79239 | 131092 | -81546 |
| RTY prior-day |ret|/volume pct>=90 of 60d mode=with | H2 | 0.89 | 1.24 | -162769 | -94229 | 331044 | -251625 | 0.83 | 16.7 | 2.64 | -82444 | 211933 | -87472 |
| RTY prior-day |ret|/volume pct>=90 of 60d mode=with | all | 0.75 | 1.33 | -124907 | -93329 | 544217 | -251625 | 1.99 | 18.5 | 1.98 | -85243 | 304313 | -101514 |
| YM prior-day |ret|/volume pct>=80 of 120d mode=long | clean | 0.56 | 0.84 | -138716 | -109876 | 533489 | -272996 | 0.95 | 33.3 | 1.54 | -83525 | 292749 | -93913 |
| YM prior-day |ret|/volume pct>=80 of 120d mode=long | H1 | 1.10 | 2.19 | -44836 | -43099 | 124618 | -49117 | 1.17 | 32.1 | 3.01 | -74459 | 145849 | -79794 |
| YM prior-day |ret|/volume pct>=80 of 120d mode=long | H2 | -0.14 | -0.19 | -155541 | -128330 | 323110 | -172852 | -0.14 | 27.8 | 2.54 | -88041 | 244322 | -90697 |
| YM prior-day |ret|/volume pct>=80 of 120d mode=long | all | 0.44 | 0.65 | -140439 | -110692 | 533489 | -272996 | 1.14 | 32.1 | 1.98 | -84114 | 292749 | -93913 |
| ZN prior-day |ret|/volume pct>=80 of 120d mode=long | clean | 0.22 | 0.32 | -137909 | -114296 | 404545 | -209644 | 0.50 | 33.3 | 1.49 | -87428 | 255732 | -94523 |
| ZN prior-day |ret|/volume pct>=80 of 120d mode=long | H1 | -1.39 | -1.50 | -102968 | -83817 | 218779 | -141889 | -0.84 | 28.6 | 2.54 | -82161 | 146736 | -86035 |
| ZN prior-day |ret|/volume pct>=80 of 120d mode=long | H2 | -0.43 | -0.59 | -133656 | -115791 | 709528 | -146630 | -0.18 | 36.1 | 2.33 | -86075 | 250385 | -86519 |
| ZN prior-day |ret|/volume pct>=80 of 120d mode=long | all | -0.08 | -0.11 | -137406 | -113969 | 709528 | -209644 | -0.16 | 33.3 | 1.85 | -87123 | 255732 | -94523 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES prior-day |ret|/volume pct>=80 of 60d mode=with (diag) | -26.6 | 9.9 | 23.0 | 19.4 | 15.5 / 23.2 | 5.0 / 16.3 | NO |
| NQ prior-day |ret|/volume pct>=80 of 120d mode=against | -27.9 | 24.1 | 27.0 | 36.9 | 24.0 / 26.3 | 31.2 / 31.5 | NO |
| RTY prior-day |ret|/volume pct>=90 of 60d mode=with | -18.1 | -13.6 | 14.3 | 17.0 | -14.5 / 9.5 | 23.8 / 26.9 | NO |
| YM prior-day |ret|/volume pct>=80 of 120d mode=long | -23.4 | 3.9 | 18.0 | 21.0 | 3.1 / 17.3 | 25.7 / 36.1 | NO |
| GC prior-day |ret|/volume pct>=90 of 120d mode=against (diag) | -21.3 | -162.9 | -4.1 | -37.3 | 6.6 / 20.7 | -177.1 / -83.0 | NO |
| CL prior-day |ret|/volume pct>=80 of 60d mode=against (diag) | -37.0 | -46.6 | -2.7 | -68.4 | -0.6 / 7.7 | 29.9 / 30.0 | NO |
| ZN prior-day |ret|/volume pct>=80 of 120d mode=long | -31.2 | -20.5 | 8.6 | 24.4 | -21.4 / 8.5 | 13.8 / 21.2 | NO |
| BTC prior-day |ret|/volume pct>=80 of 120d mode=against (diag) | -15.9 | -2.6 | 17.6 | 8.8 | -3.4 / 13.6 | 18.2 / 23.5 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) prior-day |ret|/volume pct>=90 of 60d mode=against | positive pre-2023 | 329 | 92.3 | 63.0 | 77.2 | 29.4 | 0.35 / 0.24 / 0.29 | 143.8 / 114.4 |
| ES 2 (diag) prior-day |ret|/volume pct>=80 of 120d mode=against | negative pre-2023 | 558 | -21.0 | -50.4 | -36.2 | 29.4 | -0.10 / -0.24 / -0.17 | 120.2 / 90.8 |
| ES 3 (diag) prior-day |ret|/volume pct>=80 of 60d mode=with | gross-positive, cost-negative pre-2023 | 574 | 15.5 | -13.9 | 0.3 | 29.4 | 0.08 / -0.07 / -0.00 | 71.1 / 41.8 |
| NQ 1 prior-day |ret|/volume pct>=80 of 120d mode=against | positive pre-2023 | 565 | 100.4 | 86.0 | 94.5 | 14.4 | 0.34 / 0.29 / 0.32 | 256.7 / 242.4 |
| NQ 2 prior-day |ret|/volume pct>=90 of 60d mode=with | negative pre-2023 | 311 | -233.9 | -248.2 | -239.8 | 14.4 | -0.54 / -0.57 / -0.55 | 87.1 / 72.7 |
| NQ 3 (diag) prior-day |ret|/volume pct>=90 of 120d mode=against | positive pre-2023 | 300 | 279.3 | 265.0 | 273.4 | 14.4 | 0.63 / 0.59 / 0.61 | 573.0 / 558.7 |
| NQ 4 (diag) prior-day |ret|/volume pct>=90 of 120d mode=long | positive pre-2023 | 300 | 81.9 | 67.6 | 76.0 | 14.4 | 0.19 / 0.16 / 0.17 | 291.0 / 276.7 |
| NQ 5 (diag) prior-day |ret|/volume pct>=80 of 60d mode=against | positive pre-2023 | 579 | 92.6 | 78.2 | 86.7 | 14.4 | 0.33 / 0.28 / 0.31 | 119.4 / 105.0 |
| RTY 1 prior-day |ret|/volume pct>=90 of 60d mode=with | negative pre-2023 | 172 | -59.1 | -73.5 | -71.3 | 14.4 | -0.29 / -0.36 / -0.34 | 187.8 / 173.5 |
| RTY 2 prior-day |ret|/volume pct>=90 of 120d mode=with | negative pre-2023 | 147 | -45.6 | -59.9 | -57.6 | 14.4 | -0.20 / -0.26 / -0.25 | 138.0 / 123.6 |
| RTY 3 prior-day |ret|/volume pct>=90 of 60d mode=long | negative pre-2023 | 172 | -164.5 | -178.8 | -176.7 | 14.4 | -0.81 / -0.87 / -0.86 | 57.0 / 42.7 |
| RTY 4 prior-day |ret|/volume pct>=80 of 120d mode=with | negative pre-2023 | 295 | -49.8 | -64.2 | -61.9 | 14.4 | -0.36 / -0.45 / -0.44 | 28.9 / 14.5 |
| RTY 5 (diag) prior-day |ret|/volume pct>=80 of 60d mode=with | negative pre-2023 | 318 | -52.4 | -66.7 | -64.6 | 14.4 | -0.40 / -0.50 / -0.48 | 63.9 / 49.6 |
| RTY 6 (diag) prior-day |ret|/volume pct>=90 of 120d mode=long | negative pre-2023 | 147 | -90.6 | -105.0 | -102.7 | 14.4 | -0.40 / -0.47 / -0.46 | 36.9 / 22.5 |
| RTY 7 (diag) prior-day |ret|/volume pct>=80 of 120d mode=long | negative pre-2023 | 295 | -70.5 | -84.8 | -82.6 | 14.4 | -0.48 / -0.57 / -0.56 | -34.3 / -48.7 |
| YM 1 prior-day |ret|/volume pct>=80 of 60d mode=with | negative pre-2023 | 566 | -28.8 | -43.2 | -37.5 | 14.4 | -0.20 / -0.30 / -0.26 | 212.1 / 197.8 |
| YM 2 prior-day |ret|/volume pct>=80 of 120d mode=with | negative pre-2023 | 549 | -3.0 | -17.3 | -11.7 | 14.4 | -0.02 / -0.11 / -0.07 | 224.4 / 210.1 |
| YM 3 prior-day |ret|/volume pct>=80 of 120d mode=long | negative pre-2023 | 549 | -8.2 | -22.6 | -16.9 | 14.4 | -0.06 / -0.17 / -0.12 | 117.5 / 103.2 |
| YM 4 prior-day |ret|/volume pct>=90 of 120d mode=with | negative pre-2023 | 293 | -82.4 | -96.7 | -91.0 | 14.4 | -0.39 / -0.45 / -0.43 | 100.8 / 86.4 |
| YM 5 prior-day |ret|/volume pct>=80 of 60d mode=long | negative pre-2023 | 566 | -43.1 | -57.4 | -51.7 | 14.4 | -0.30 / -0.40 / -0.36 | 61.2 / 46.9 |
| YM 6 prior-day |ret|/volume pct>=90 of 60d mode=with | negative pre-2023 | 323 | -61.4 | -75.8 | -70.0 | 14.4 | -0.33 / -0.41 / -0.38 | 59.9 / 45.5 |
| YM 7 (diag) prior-day |ret|/volume pct>=90 of 120d mode=long | negative pre-2023 | 293 | -14.5 | -28.8 | -23.1 | 14.4 | -0.07 / -0.15 / -0.12 | 157.6 / 143.2 |
| YM 8 (diag) prior-day |ret|/volume pct>=90 of 60d mode=long | negative pre-2023 | 323 | -28.0 | -42.3 | -36.6 | 14.4 | -0.16 / -0.24 / -0.21 | 124.1 / 109.7 |
| YM 9 (diag) prior-day |ret|/volume pct>=90 of 60d mode=against | positive pre-2023 | 323 | 61.4 | 47.0 | 52.8 | 14.4 | 0.33 / 0.25 / 0.28 | -59.9 / -74.2 |
| GC 1 (diag) prior-day |ret|/volume pct>=80 of 60d mode=with | gross-positive, cost-negative pre-2023 | 560 | 17.5 | -6.9 | 3.0 | 24.4 | 0.10 / -0.05 / 0.01 | 116.0 / 91.6 |
| GC 2 (diag) prior-day |ret|/volume pct>=90 of 120d mode=against | negative pre-2023 | 271 | -30.7 | -55.1 | -45.4 | 24.4 | -0.11 / -0.20 / -0.16 | 69.7 / 45.4 |
| GC 3 (diag) prior-day |ret|/volume pct>=90 of 60d mode=against | negative pre-2023 | 292 | -36.6 | -61.0 | -51.3 | 24.4 | -0.14 / -0.23 / -0.19 | 10.3 / -14.1 |
| CL 1 (diag) prior-day |ret|/volume pct>=80 of 120d mode=against | negative pre-2023 | 532 | -17.8 | -42.2 | -39.3 | 24.4 | -0.11 / -0.25 / -0.23 | 127.3 / 102.9 |
| CL 2 (diag) prior-day |ret|/volume pct>=80 of 60d mode=against | negative pre-2023 | 567 | -23.4 | -47.7 | -45.2 | 24.4 | -0.15 / -0.30 / -0.29 | 118.5 / 94.1 |
| CL 3 (diag) prior-day |ret|/volume pct>=90 of 120d mode=against | negative pre-2023 | 295 | -49.9 | -74.3 | -71.4 | 24.4 | -0.21 / -0.30 / -0.29 | 74.2 / 49.9 |
| ZN 1 prior-day |ret|/volume pct>=80 of 120d mode=long | negative pre-2023 | 538 | -8.5 | -44.1 | -49.1 | 35.6 | -0.18 / -0.92 / -1.02 | 44.4 / 8.8 |
| ZN 2 (diag) prior-day |ret|/volume pct>=90 of 60d mode=with | negative pre-2023 | 316 | -16.4 | -52.0 | -57.2 | 35.6 | -0.23 / -0.72 / -0.79 | 36.5 / 0.9 |
| ZN 3 (diag) prior-day |ret|/volume pct>=90 of 120d mode=long | negative pre-2023 | 292 | -0.4 | -36.0 | -41.2 | 35.6 | -0.01 / -0.54 / -0.61 | 32.4 / -3.2 |
| ZN 4 (diag) prior-day |ret|/volume pct>=90 of 60d mode=long | gross-positive, cost-negative pre-2023 | 316 | 2.9 | -32.7 | -37.9 | 35.6 | 0.04 / -0.50 / -0.58 | 27.5 / -8.1 |
| BTC 1 (diag) prior-day |ret|/volume pct>=90 of 120d mode=against | gross-positive, cost-negative pre-2023 | 25 | 101.0 | 46.6 | 79.9 | 54.4 | 0.11 / -0.02 / 0.06 | 1459.0 / 1404.7 |
| BTC 2 (diag) prior-day |ret|/volume pct>=80 of 120d mode=against | positive pre-2023 | 48 | 411.5 | 357.1 | 390.7 | 54.4 | 0.75 / 0.64 / 0.71 | 899.5 / 845.1 |
| BTC 3 (diag) prior-day |ret|/volume pct>=90 of 60d mode=against | positive pre-2023 | 29 | 226.7 | 172.4 | 205.5 | 54.4 | 0.38 / 0.27 / 0.33 | 933.2 / 878.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 1.00); ES: 0 cells pass the clean rule against a replicate mean of 1.9 (p(count) = 1.00); GC: 0 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 1.00); NQ: 2 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 0.74, p(top) = 0.88); RTY: 4 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 0.06, p(top) = 0.70); YM: 6 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.00, p(top) = 0.72); ZN: 1 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 0.27, p(top) = 0.20).
- Of 13 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.08 (RTY prior-day |ret|/volume pct>=90 of 60d mode=with); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 12, 'positive pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_2.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm2/ (`BM2_CO_all_selected_scored.csv`).

DONE BM2
