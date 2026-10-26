# REPORT SW7 - scheduled-release event bars: weekly Thursday 08:30 claims, NFP, CPI, FOMC (D10 H1/H2)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 26 selected cells (+21 diagnostic) scored on 7 instruments; best non-diagnostic all-in additive uplift at 20% share +0.21; best pair-window standalone Sharpe +1.18.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: release sets THU (all Thursdays 08:30 ET, rule-based), TNC (THU + NFP + CPI 08:30), ALL (TNC + FOMC 14:00). Enter k min (1/2/5) after the release in the direction of (or against) the move since the minute before the release; exact hold 5/15/30/60 min. Calendars: 2023-26 verified lists (ap_c2_g3_events), pre-2023 NFP by BLS rule and FOMC from memory (ERA flag only; CPI pre-2023 unavailable).
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN. Grid: 72 cells per instrument = 3 sets x 3 k x 2 directions x 4 holds.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| CL    |      72 |         56 |         5 |               1.354 |                2 |          5 |            3 |
| ES    |      72 |         64 |         0 |               0.432 |                1 |          0 |            3 |
| GC    |      72 |         72 |         7 |               1.255 |                2 |          7 |            3 |
| NQ    |      72 |         72 |         6 |               1.088 |                2 |          6 |            3 |
| RTY   |      72 |         72 |         4 |               0.904 |                2 |          4 |            3 |
| YM    |      72 |         70 |         4 |               0.936 |                2 |          4 |            3 |
| ZN    |      72 |         56 |         0 |              -0.524 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    0 |             2.07 |               6 |       1    |                     nan     |            0.633 |           1.056 |   nan    |     nan     |                1.39  |
| NQ    |     100 |                    6 |             9.98 |              18 |       0.97 |                       0.546 |            0.744 |           0.981 |     0.94 |       1.088 |                1.899 |
| RTY   |     100 |                    4 |             3.39 |               8 |       0.48 |                       0.459 |            0.593 |           0.985 |     0.73 |       0.772 |                1.388 |
| YM    |     100 |                    4 |             3.82 |               9 |       0.5  |                       0.478 |            0.659 |           0.976 |     0.84 |       0.722 |                1.469 |
| GC    |     100 |                    7 |             3.28 |               7 |       0.01 |                       0.549 |            0.634 |           0.99  |     0.61 |       1.255 |                1.457 |
| CL    |     100 |                    5 |             1.35 |               4 |       0    |                       0.79  |            0.569 |           1.236 |     0.12 |       1.354 |                1.275 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | THU release+2m dir=against hold=15m | 103 | 1 | 0.43 | -0.25 | -0.00 | -1.12 / 0.76 | 0.01 / -0.14 / -0.19 | -0.15 | 0.07 | 0.89 | -0.22 | 0.00 | 162 | diag |
| ES 2 (diag) | THU release+5m dir=against hold=60m | 96 | 1 | 0.29 | -0.40 | 0.48 | 0.84 / 0.77 | 0.01 / 0.32 / -0.01 | -0.02 | -0.41 | 0.88 | -0.14 | 0.50 | 155 | diag |
| ES 3 (diag) | ALL release+1m dir=against hold=15m | 158 | 1 | 0.26 | -0.56 | 0.38 | 0.57 / 0.72 | -0.00 / 0.09 / -0.09 | -0.09 | -0.15 | 1.00 | -0.17 | 0.00 | 246 | diag |
| NQ 1 | TNC release+5m dir=against hold=60m | 145 | 2 | 1.09 | 0.11 | 1.18 | 1.51 / 1.30 | 0.18 / -0.04 / 0.38 | 0.20 | -0.46 | 0.99 | 0.01 | 0.25 | 226 | NO |
| NQ 2 | TNC release+2m dir=with hold=5m | 146 | 2 | 0.73 | -1.08 | 0.68 | 0.63 / 0.96 | 0.15 / -0.04 / 0.29 | 0.13 | -0.03 | 0.97 | -0.03 | 0.00 | 228 | NO |
| NQ 3 | TNC release+1m dir=with hold=5m | 146 | 2 | 0.56 | -0.77 | -0.22 | -1.23 / 1.05 | 0.11 / -0.25 / -0.35 | -0.08 | -0.02 | 0.68 | -0.24 | 0.00 | 228 | NO |
| NQ 4 | ALL release+2m dir=with hold=5m | 160 | 2 | 0.48 | -0.85 | 0.59 | 0.80 / 1.09 | 0.08 / 0.01 / 0.50 | 0.12 | -0.50 | 0.96 | -0.05 | 0.00 | 251 | NO |
| NQ 5 | ALL release+2m dir=with hold=60m | 159 | 2 | 0.26 | -0.77 | 0.07 | -0.49 / 1.40 | 0.04 / -0.13 / -0.17 | -0.05 | 0.24 | 0.58 | -0.21 | 0.00 | 249 | NO |
| NQ 6 | ALL release+2m dir=with hold=30m | 160 | 2 | 0.15 | -0.61 | -0.02 | -0.19 / 1.42 | 0.01 / -0.10 / -0.06 | -0.03 | 0.36 | 0.66 | -0.20 | 0.00 | 251 | NO |
| NQ 7 (diag) | THU release+5m dir=against hold=60m | 104 | 1 | 0.74 | -0.28 | 0.67 | 0.78 / 1.25 | 0.09 / -0.15 / 0.05 | 0.05 | -0.36 | 0.92 | -0.14 | 0.25 | 164 | diag |
| NQ 8 (diag) | THU release+2m dir=against hold=15m | 105 | 1 | 0.63 | 0.33 | 0.14 | -0.83 / 1.18 | 0.04 / -0.13 / -0.17 | -0.06 | 0.05 | 0.75 | -0.21 | 0.00 | 165 | diag |
| NQ 9 (diag) | THU release+1m dir=with hold=5m | 105 | 1 | 0.54 | -0.77 | -0.11 | -0.79 / 0.94 | 0.13 / -0.35 / -0.29 | -0.06 | -0.22 | 0.67 | -0.25 | 0.00 | 165 | diag |
| RTY 1 | TNC release+2m dir=with hold=5m | 142 | 2 | 0.77 | -0.67 | 0.65 | 0.40 / 0.47 | 0.15 / -0.17 / 0.12 | 0.04 | 0.17 | 1.00 | -0.06 | 0.00 | 223 | NO |
| RTY 2 | ALL release+2m dir=with hold=5m | 155 | 2 | 0.64 | -0.47 | 0.66 | 0.74 / 0.11 | 0.10 / -0.07 / 0.30 | 0.05 | -0.27 | 1.00 | -0.06 | 0.00 | 245 | NO |
| RTY 3 | THU release+5m dir=against hold=15m | 103 | 2 | 0.27 | -0.35 | 0.33 | 0.57 / 0.59 | -0.03 / -0.10 / 0.18 | -0.07 | -0.25 | 0.96 | -0.17 | 0.00 | 163 | NO |
| RTY 4 | THU release+5m dir=with hold=30m | 103 | 2 | 0.15 | -0.20 | -0.21 | -0.91 / 0.83 | 0.05 / -0.09 / -0.29 | -0.09 | 0.10 | 0.78 | -0.22 | 0.00 | 163 | NO |
| RTY 5 (diag) | ALL release+1m dir=with hold=30m | 159 | 1 | 0.90 | -0.14 | 0.37 | -0.64 / 0.68 | 0.13 / -0.15 / -0.07 | 0.00 | 0.27 | 0.93 | -0.12 | 0.00 | 247 | diag |
| RTY 6 (diag) | ALL release+2m dir=with hold=30m | 155 | 1 | 0.74 | -0.32 | 0.39 | -0.15 / 1.09 | 0.11 / -0.02 / -0.09 | 0.00 | 0.30 | 0.93 | -0.12 | 0.00 | 245 | diag |
| RTY 7 (diag) | TNC release+2m dir=with hold=30m | 142 | 1 | 0.71 | -0.42 | 0.46 | 0.01 / 1.22 | 0.13 / -0.02 / -0.10 | 0.02 | 0.39 | 0.96 | -0.10 | 1.00 | 223 | diag |
| YM 1 | ALL release+1m dir=with hold=60m | 154 | 2 | 0.72 | -0.16 | 0.16 | -0.46 / 0.87 | 0.05 / -0.23 / -0.06 | -0.05 | 0.29 | 0.78 | -0.20 | 0.00 | 240 | NO |
| YM 2 | ALL release+5m dir=with hold=60m | 156 | 2 | 0.62 | -0.69 | -0.05 | -1.48 / 1.25 | 0.11 / -0.39 / -0.35 | -0.09 | 0.45 | 0.69 | -0.24 | 0.00 | 246 | NO |
| YM 3 | TNC release+1m dir=with hold=60m | 140 | 2 | 0.36 | 0.03 | -0.08 | -0.61 / 1.03 | 0.03 / -0.26 / -0.14 | -0.09 | 0.34 | 0.72 | -0.24 | 0.00 | 217 | NO |
| YM 4 | ALL release+2m dir=against hold=15m | 158 | 2 | 0.21 | -0.37 | 0.14 | 0.02 / 0.67 | 0.01 / -0.12 / 0.04 | -0.05 | -0.32 | 0.87 | -0.17 | 0.00 | 247 | NO |
| YM 5 (diag) | THU release+1m dir=with hold=60m | 99 | 2 | 0.94 | 0.25 | 0.48 | 0.08 / 1.21 | 0.14 / -0.17 / -0.02 | 0.03 | -0.04 | 0.90 | -0.15 | 0.00 | 155 | diag |
| YM 6 (diag) | ALL release+1m dir=against hold=15m | 155 | 1 | 0.56 | -0.36 | 0.85 | 1.52 / 1.08 | 0.09 / 0.10 / 0.16 | 0.06 | -0.27 | 1.00 | -0.05 | 0.00 | 242 | diag |
| YM 7 (diag) | THU release+1m dir=against hold=15m | 100 | 1 | 0.56 | -0.52 | 0.34 | -0.21 / 0.70 | 0.05 / -0.05 / -0.05 | -0.05 | -0.05 | 0.95 | -0.17 | 0.00 | 156 | diag |
| GC 1 | TNC release+1m dir=against hold=60m | 142 | 2 | 1.25 | -0.62 | 0.57 | 0.12 / 1.18 | 0.21 / -0.74 / 0.26 | 0.06 | 0.04 | 0.92 | -0.18 | 0.00 | 222 | NO |
| GC 2 | TNC release+2m dir=against hold=60m | 141 | 2 | 0.73 | -0.50 | 0.30 | -0.08 / 1.48 | 0.12 / -0.39 / 0.04 | 0.01 | 0.18 | 0.81 | -0.21 | 0.00 | 220 | NO |
| GC 3 | TNC release+5m dir=against hold=60m | 144 | 2 | 0.50 | -0.58 | 0.42 | 0.39 / 1.40 | 0.09 / -0.26 / 0.35 | 0.07 | -0.13 | 0.82 | -0.16 | 0.50 | 224 | NO |
| GC 4 | TNC release+5m dir=against hold=30m | 144 | 2 | 0.39 | -0.65 | 0.16 | 0.01 / 1.39 | 0.06 / 0.07 / -0.33 | -0.06 | -0.17 | 0.74 | -0.33 | 0.00 | 224 | NO |
| GC 5 | THU release+2m dir=against hold=60m | 100 | 2 | 0.37 | -0.35 | 0.03 | -0.27 / 1.59 | 0.06 / 0.22 / -0.55 | -0.08 | 0.24 | 0.60 | -0.31 | 0.00 | 158 | NO |
| GC 6 | ALL release+5m dir=against hold=30m | 157 | 2 | 0.33 | -0.69 | -0.15 | -0.50 / 1.49 | 0.05 / 0.20 / -0.83 | -0.19 | 0.25 | 0.60 | -0.46 | 0.00 | 246 | NO |
| GC 7 | THU release+1m dir=against hold=60m | 102 | 2 | 0.27 | -0.53 | -0.34 | -0.88 / 1.52 | 0.01 / -0.47 / -0.62 | -0.23 | 0.10 | 0.41 | -0.45 | 0.00 | 161 | NO |
| GC 8 (diag) | ALL release+1m dir=against hold=60m | 155 | 1 | 0.81 | -0.56 | -0.08 | -0.66 / 1.63 | 0.14 / -1.16 / -0.20 | -0.15 | 0.41 | 0.58 | -0.43 | 0.00 | 244 | diag |
| GC 9 (diag) | ALL release+5m dir=against hold=60m | 157 | 1 | 0.40 | -0.62 | -0.01 | -0.33 / 1.44 | 0.07 / -0.05 / -0.22 | -0.04 | 0.28 | 0.56 | -0.28 | 0.00 | 246 | diag |
| GC 10 (diag) | ALL release+2m dir=against hold=60m | 154 | 1 | 0.40 | -0.53 | -0.11 | -0.50 / 1.26 | 0.07 / -0.36 / -0.37 | -0.12 | 0.51 | 0.52 | -0.38 | 0.00 | 242 | diag |
| CL 1 | ALL release+1m dir=against hold=60m | 148 | 2 | 1.35 | -0.36 | 1.03 | 0.56 / 1.35 | 0.24 / -0.10 / 0.27 | 0.12 | 0.33 | 0.99 | -0.01 | 0.50 | 231 | NO |
| CL 2 | ALL release+1m dir=against hold=30m | 148 | 2 | 1.10 | -0.32 | 0.48 | -0.01 / 0.95 | 0.15 / 0.14 / -0.11 | -0.04 | 0.01 | 0.98 | -0.17 | 0.50 | 231 | NO |
| CL 3 | TNC release+1m dir=against hold=30m | 138 | 2 | 0.66 | -0.44 | 0.38 | 0.13 / 0.79 | 0.09 / 0.18 / 0.03 | -0.03 | -0.11 | 0.98 | -0.17 | 0.50 | 213 | NO |
| CL 4 | ALL release+5m dir=against hold=60m | 152 | 2 | 0.57 | -0.51 | 0.52 | 0.54 / 0.91 | 0.10 / -0.19 / 0.42 | 0.05 | 0.49 | 0.97 | -0.09 | 0.00 | 234 | NO |
| CL 5 | ALL release+2m dir=against hold=15m | 157 | 2 | 0.28 | -0.72 | -0.36 | -0.81 / 0.75 | 0.03 / 0.20 / -0.88 | -0.37 | 0.01 | 0.80 | -0.46 | 0.00 | 243 | NO |
| CL 6 (diag) | THU release+1m dir=against hold=60m | 99 | 2 | 1.11 | -0.23 | 0.13 | -1.29 / 1.31 | 0.19 / -0.08 / -0.40 | -0.05 | 0.24 | 0.87 | -0.19 | 0.50 | 155 | diag |
| CL 7 (diag) | TNC release+1m dir=against hold=60m | 138 | 1 | 1.07 | -0.36 | 0.79 | 0.37 / 1.39 | 0.20 / -0.03 / 0.19 | 0.10 | 0.36 | 0.97 | -0.04 | 0.50 | 213 | diag |
| CL 8 (diag) | THU release+1m dir=against hold=30m | 99 | 2 | 0.83 | -0.14 | 0.01 | -0.98 / 1.30 | 0.12 / 0.12 / -0.47 | -0.10 | -0.14 | 0.82 | -0.25 | 0.00 | 155 | diag |
| ZN 1 (diag) | THU release+1m dir=against hold=60m | 94 | 1 | -0.52 | -1.96 | -1.02 | -2.25 / -1.36 | -0.18 / -0.42 / -0.30 | -0.50 | 0.03 | 1.00 | -0.41 | 0.00 | 140 | diag |
| ZN 2 (diag) | THU release+2m dir=against hold=60m | 101 | 0 | -0.63 | -1.65 | -0.92 | -1.59 / -1.68 | -0.19 / -0.17 / -0.27 | -0.48 | 0.05 | 1.00 | -0.38 | 0.00 | 155 | diag |
| ZN 3 (diag) | TNC release+2m dir=against hold=60m | 142 | 0 | -0.84 | -1.61 | -0.64 | -0.14 / -2.35 | -0.23 / -0.14 / 0.07 | -0.40 | -0.30 | 1.00 | -0.33 | 0.00 | 216 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 26 |
| diagnostic cells read | 21 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 22 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 18 |
| worst-decile corr <= +0.30 | 37 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 4 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CL ALL release+1m dir=against hold=60m | clean | 1.36 | 2.73 | -93245 | -78866 | 330531 | -114187 | 3.73 | 41.9 | 1.70 | -86912 | 334033 | -98234 |
| CL ALL release+1m dir=against hold=60m | H1 | -0.67 | -0.89 | -100628 | -87277 | 264211 | -102525 | -0.46 | 46.4 | 2.73 | -78085 | 150677 | -83432 |
| CL ALL release+1m dir=against hold=60m | H2 | 1.09 | 1.65 | -209366 | -150185 | 358951 | -235619 | 1.36 | 41.7 | 2.56 | -87425 | 209324 | -93315 |
| CL ALL release+1m dir=against hold=60m | all | 1.03 | 1.74 | -124880 | -100805 | 436288 | -235619 | 3.66 | 42.3 | 2.05 | -86639 | 334033 | -98234 |
| ES THU release+5m dir=against hold=60m (diag) | clean | 0.22 | 0.35 | -117655 | -98173 | 753205 | -144042 | 0.27 | 47.6 | 1.47 | -89856 | 270874 | -101201 |
| ES THU release+5m dir=against hold=60m (diag) | H1 | 0.73 | 1.18 | -120367 | -110996 | 424348 | -130725 | 0.48 | 42.9 | 3.14 | -63556 | 166574 | -69046 |
| ES THU release+5m dir=against hold=60m (diag) | H2 | 0.92 | 1.44 | -126286 | -112599 | 354942 | -133684 | 0.93 | 47.2 | 2.29 | -102538 | 260541 | -104152 |
| ES THU release+5m dir=against hold=60m (diag) | all | 0.48 | 0.76 | -121847 | -107225 | 753205 | -144042 | 0.98 | 47.0 | 1.90 | -91444 | 270874 | -104152 |
| GC TNC release+5m dir=against hold=60m | clean | 0.50 | 0.79 | -128058 | -104227 | 394041 | -176675 | 1.16 | 48.6 | 1.55 | -83881 | 235495 | -88306 |
| GC TNC release+5m dir=against hold=60m | H1 | -0.35 | -0.46 | -223057 | -185561 | 637977 | -287553 | -0.21 | 42.9 | 2.57 | -95411 | 181012 | -135798 |
| GC TNC release+5m dir=against hold=60m | H2 | 0.81 | 1.42 | -224978 | -176693 | 629504 | -306764 | 0.85 | 44.4 | 2.64 | -81444 | 230303 | -85458 |
| GC TNC release+5m dir=against hold=60m | all | 0.42 | 0.67 | -177537 | -144934 | 818523 | -306764 | 1.05 | 47.0 | 1.96 | -89344 | 235495 | -135798 |
| NQ TNC release+5m dir=against hold=60m | clean | 0.95 | 1.60 | -103137 | -93471 | 504307 | -108625 | 1.74 | 44.8 | 1.64 | -83964 | 241968 | -97531 |
| NQ TNC release+5m dir=against hold=60m | H1 | 0.37 | 0.62 | -91211 | -87450 | 373057 | -97097 | 0.25 | 50.0 | 2.79 | -73627 | 168330 | -82568 |
| NQ TNC release+5m dir=against hold=60m | H2 | 2.20 | 3.91 | -138917 | -124438 | 330348 | -152039 | 2.90 | 33.3 | 2.68 | -92608 | 231436 | -107555 |
| NQ TNC release+5m dir=against hold=60m | all | 1.18 | 2.00 | -118531 | -104544 | 504307 | -152989 | 3.82 | 42.9 | 2.07 | -85730 | 241968 | -107555 |
| RTY ALL release+2m dir=with hold=5m | clean | 0.61 | 0.96 | -134507 | -106020 | 572737 | -169840 | 0.96 | 47.6 | 1.56 | -88228 | 307859 | -109286 |
| RTY ALL release+2m dir=with hold=5m | H1 | 0.28 | 0.48 | -110203 | -94019 | 289165 | -112571 | 0.24 | 53.6 | 2.76 | -84779 | 156381 | -86515 |
| RTY ALL release+2m dir=with hold=5m | H2 | 1.11 | 2.03 | -88899 | -81048 | 252004 | -93979 | 1.27 | 36.1 | 2.59 | -80889 | 216061 | -88289 |
| RTY ALL release+2m dir=with hold=5m | all | 0.66 | 1.08 | -124603 | -101071 | 590324 | -169840 | 1.59 | 45.8 | 1.97 | -87469 | 307859 | -109286 |
| YM ALL release+2m dir=against hold=15m | clean | 0.20 | 0.32 | -118115 | -93933 | 742705 | -224288 | 0.24 | 52.4 | 1.47 | -90082 | 239987 | -93462 |
| YM ALL release+2m dir=against hold=15m | H1 | -0.71 | -1.00 | -63153 | -58369 | 304892 | -71673 | -0.30 | 53.6 | 2.70 | -72173 | 168251 | -73952 |
| YM ALL release+2m dir=against hold=15m | H2 | 0.34 | 0.51 | -132052 | -100751 | 291972 | -148721 | 0.34 | 41.7 | 2.34 | -86208 | 238703 | -86564 |
| YM ALL release+2m dir=against hold=15m | all | 0.14 | 0.22 | -117544 | -92221 | 742705 | -224288 | 0.26 | 50.0 | 1.85 | -88708 | 239987 | -93462 |
| ZN TNC release+2m dir=against hold=60m (diag) | clean | -0.86 | -1.11 | -149915 | -124956 | 1001842 | -199584 | -0.78 | 57.1 | 1.23 | -96040 | 304892 | -116925 |
| ZN TNC release+2m dir=against hold=60m (diag) | H1 | -1.09 | -1.26 | -116463 | -102180 | 324522 | -154160 | -0.56 | 57.1 | 2.68 | -79155 | 148940 | -79574 |
| ZN TNC release+2m dir=against hold=60m (diag) | H2 | 0.66 | 1.26 | -57506 | -47438 | 187594 | -61533 | 0.70 | 47.2 | 2.36 | -83126 | 216264 | -89998 |
| ZN TNC release+2m dir=against hold=60m (diag) | all | -0.64 | -0.83 | -142630 | -112720 | 1274944 | -199584 | -0.65 | 54.8 | 1.69 | -92457 | 304892 | -116925 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES THU release+5m dir=against hold=60m (diag) | -21.8 | -14.3 | 2.3 | 19.6 | -9.5 / 5.1 | 32.6 / 38.9 | NO |
| NQ TNC release+5m dir=against hold=60m | -8.5 | -20.7 | 13.4 | 33.2 | -2.7 / 18.5 | 20.4 / 25.5 | NO |
| RTY ALL release+2m dir=with hold=5m | -19.5 | -23.5 | 12.5 | 15.1 | -24.4 / 10.1 | 12.9 / 16.1 | NO |
| YM ALL release+2m dir=against hold=15m | -27.9 | 6.9 | 10.3 | 30.9 | 6.1 / 7.4 | 38.3 / 40.5 | NO |
| GC TNC release+5m dir=against hold=60m | -20.4 | -70.9 | 7.8 | 31.3 | 14.2 / 19.5 | -80.2 / -19.7 | NO |
| CL ALL release+1m dir=against hold=60m | -12.1 | -4.0 | 13.5 | 1.1 | -4.8 / 14.1 | 18.8 / 29.1 | NO |
| ZN TNC release+2m dir=against hold=60m (diag) | -39.3 | -37.9 | 3.8 | 3.6 | -39.0 / -4.4 | 26.2 / 27.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) THU release+2m dir=against hold=15m | gross-positive, cost-negative pre-2023 | 486 | 21.0 | -8.4 | 5.7 | 29.4 | 0.63 / -0.25 / 0.17 | 53.3 / 23.9 |
| ES 2 (diag) THU release+5m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 499 | 5.3 | -24.0 | -10.0 | 29.4 | 0.09 / -0.40 / -0.17 | 47.3 / 17.9 |
| ES 3 (diag) ALL release+1m dir=against hold=15m | gross-positive, cost-negative pre-2023 | 678 | 7.7 | -21.7 | -7.7 | 29.4 | 0.20 / -0.56 / -0.20 | 46.1 / 16.8 |
| NQ 1 TNC release+5m dir=against hold=60m | positive pre-2023 | 650 | 23.1 | 8.7 | 17.2 | 14.4 | 0.29 / 0.11 / 0.21 | 137.6 / 123.2 |
| NQ 2 TNC release+2m dir=with hold=5m | negative pre-2023 | 652 | -24.5 | -38.9 | -30.4 | 14.4 | -0.68 / -1.08 / -0.85 | 61.4 / 47.0 |
| NQ 3 TNC release+1m dir=with hold=5m | negative pre-2023 | 642 | -15.0 | -29.4 | -20.9 | 14.4 | -0.39 / -0.77 / -0.55 | 44.8 / 30.4 |
| NQ 4 ALL release+2m dir=with hold=5m | negative pre-2023 | 731 | -19.4 | -33.8 | -25.3 | 14.4 | -0.49 / -0.85 / -0.63 | 44.5 / 30.1 |
| NQ 5 ALL release+2m dir=with hold=60m | negative pre-2023 | 728 | -64.3 | -78.7 | -70.2 | 14.4 | -0.63 / -0.77 / -0.68 | 88.7 / 74.3 |
| NQ 6 ALL release+2m dir=with hold=30m | negative pre-2023 | 731 | -28.1 | -42.4 | -34.0 | 14.4 | -0.40 / -0.61 / -0.49 | 24.0 / 9.6 |
| NQ 7 (diag) THU release+5m dir=against hold=60m | negative pre-2023 | 529 | -11.2 | -25.6 | -17.1 | 14.4 | -0.12 / -0.28 / -0.19 | 103.7 / 89.3 |
| NQ 8 (diag) THU release+2m dir=against hold=15m | positive pre-2023 | 524 | 29.0 | 14.7 | 23.1 | 14.4 | 0.65 / 0.33 / 0.52 | 73.5 / 59.2 |
| NQ 9 (diag) THU release+1m dir=with hold=5m | negative pre-2023 | 513 | -12.8 | -27.2 | -18.7 | 14.4 | -0.36 / -0.77 / -0.53 | 40.0 / 25.6 |
| RTY 1 TNC release+2m dir=with hold=5m | negative pre-2023 | 365 | -0.0 | -14.4 | -12.2 | 14.4 | -0.00 / -0.67 / -0.57 | 38.8 / 24.4 |
| RTY 2 ALL release+2m dir=with hold=5m | gross-positive, cost-negative pre-2023 | 409 | 3.5 | -10.9 | -8.7 | 14.4 | 0.15 / -0.47 / -0.37 | 33.5 / 19.2 |
| RTY 3 THU release+5m dir=against hold=15m | gross-positive, cost-negative pre-2023 | 292 | 6.4 | -8.0 | -5.7 | 14.4 | 0.28 / -0.35 / -0.25 | 21.4 / 7.0 |
| RTY 4 THU release+5m dir=with hold=30m | gross-positive, cost-negative pre-2023 | 292 | 7.8 | -6.6 | -4.3 | 14.4 | 0.24 / -0.20 / -0.13 | 20.4 / 6.0 |
| RTY 5 (diag) ALL release+1m dir=with hold=30m | gross-positive, cost-negative pre-2023 | 404 | 9.1 | -5.3 | -3.2 | 14.4 | 0.24 / -0.14 / -0.08 | 63.9 / 49.5 |
| RTY 6 (diag) ALL release+2m dir=with hold=30m | gross-positive, cost-negative pre-2023 | 409 | 2.8 | -11.5 | -9.4 | 14.4 | 0.08 / -0.32 / -0.26 | 46.0 / 31.7 |
| RTY 7 (diag) TNC release+2m dir=with hold=30m | negative pre-2023 | 365 | -0.9 | -15.3 | -13.1 | 14.4 | -0.02 / -0.42 / -0.36 | 46.4 / 32.0 |
| YM 1 ALL release+1m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 711 | 5.9 | -8.4 | -2.7 | 14.4 | 0.11 / -0.16 / -0.05 | 47.8 / 33.4 |
| YM 2 ALL release+5m dir=with hold=60m | negative pre-2023 | 723 | -23.3 | -37.7 | -32.0 | 14.4 | -0.43 / -0.69 / -0.59 | 67.1 / 52.7 |
| YM 3 TNC release+1m dir=with hold=60m | positive pre-2023 | 630 | 15.7 | 1.4 | 7.0 | 14.4 | 0.33 / 0.03 / 0.15 | 30.3 / 15.9 |
| YM 4 ALL release+2m dir=against hold=15m | gross-positive, cost-negative pre-2023 | 723 | 4.4 | -9.9 | -4.3 | 14.4 | 0.16 / -0.37 / -0.16 | 22.1 / 7.7 |
| YM 5 (diag) THU release+1m dir=with hold=60m | positive pre-2023 | 506 | 26.9 | 12.6 | 18.3 | 14.4 | 0.54 / 0.25 / 0.36 | 59.1 / 44.8 |
| YM 6 (diag) ALL release+1m dir=against hold=15m | gross-positive, cost-negative pre-2023 | 714 | 4.0 | -10.3 | -4.6 | 14.4 | 0.14 / -0.36 / -0.16 | 39.4 / 25.0 |
| YM 7 (diag) THU release+1m dir=against hold=15m | gross-positive, cost-negative pre-2023 | 506 | 0.4 | -14.0 | -8.3 | 14.4 | 0.01 / -0.52 / -0.31 | 35.0 / 20.6 |
| GC 1 TNC release+1m dir=against hold=60m | negative pre-2023 | 642 | -21.9 | -46.2 | -36.5 | 24.4 | -0.29 / -0.62 / -0.49 | 157.9 / 133.5 |
| GC 2 TNC release+2m dir=against hold=60m | negative pre-2023 | 649 | -11.2 | -35.6 | -25.9 | 24.4 | -0.16 / -0.50 / -0.36 | 112.2 / 87.8 |
| GC 3 TNC release+5m dir=against hold=60m | negative pre-2023 | 652 | -16.1 | -40.4 | -30.7 | 24.4 | -0.23 / -0.58 / -0.44 | 81.9 / 57.6 |
| GC 4 TNC release+5m dir=against hold=30m | negative pre-2023 | 652 | -10.6 | -35.0 | -25.3 | 24.4 | -0.20 / -0.65 / -0.47 | 57.8 / 33.5 |
| GC 5 THU release+2m dir=against hold=60m | negative pre-2023 | 524 | -1.3 | -25.7 | -15.9 | 24.4 | -0.02 / -0.35 / -0.22 | 63.9 / 39.5 |
| GC 6 ALL release+5m dir=against hold=30m | negative pre-2023 | 728 | -11.5 | -35.9 | -26.1 | 24.4 | -0.22 / -0.69 / -0.50 | 52.5 / 28.1 |
| GC 7 THU release+1m dir=against hold=60m | negative pre-2023 | 518 | -14.7 | -39.1 | -29.4 | 24.4 | -0.20 / -0.53 / -0.40 | 49.9 / 25.5 |
| GC 8 (diag) ALL release+1m dir=against hold=60m | negative pre-2023 | 718 | -17.4 | -41.8 | -32.1 | 24.4 | -0.23 / -0.56 / -0.43 | 108.5 / 84.1 |
| GC 9 (diag) ALL release+5m dir=against hold=60m | negative pre-2023 | 728 | -18.9 | -43.3 | -33.6 | 24.4 | -0.27 / -0.62 / -0.48 | 69.8 / 45.4 |
| GC 10 (diag) ALL release+2m dir=against hold=60m | negative pre-2023 | 725 | -13.9 | -38.3 | -28.6 | 24.4 | -0.19 / -0.53 / -0.40 | 70.1 / 45.7 |
| CL 1 ALL release+1m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 688 | 2.1 | -22.3 | -19.8 | 24.4 | 0.03 / -0.36 / -0.32 | 99.7 / 75.4 |
| CL 2 ALL release+1m dir=against hold=30m | gross-positive, cost-negative pre-2023 | 688 | 9.3 | -15.1 | -12.6 | 24.4 | 0.20 / -0.32 / -0.27 | 58.0 / 33.6 |
| CL 3 TNC release+1m dir=against hold=30m | gross-positive, cost-negative pre-2023 | 609 | 3.2 | -21.2 | -18.6 | 24.4 | 0.07 / -0.44 / -0.39 | 48.0 / 23.7 |
| CL 4 ALL release+5m dir=against hold=60m | negative pre-2023 | 708 | -6.8 | -31.2 | -28.7 | 24.4 | -0.11 / -0.51 / -0.47 | 52.8 / 28.5 |
| CL 5 ALL release+2m dir=against hold=15m | gross-positive, cost-negative pre-2023 | 711 | 4.1 | -20.2 | -17.7 | 24.4 | 0.15 / -0.72 / -0.63 | 27.7 / 3.3 |
| CL 6 (diag) THU release+1m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 490 | 7.3 | -17.0 | -14.5 | 24.4 | 0.10 / -0.23 / -0.20 | 100.9 / 76.5 |
| CL 7 (diag) TNC release+1m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 609 | 1.0 | -23.3 | -20.8 | 24.4 | 0.02 / -0.36 / -0.32 | 87.8 / 63.5 |
| CL 8 (diag) THU release+1m dir=against hold=30m | gross-positive, cost-negative pre-2023 | 490 | 16.9 | -7.5 | -4.9 | 24.4 | 0.31 / -0.14 / -0.09 | 63.0 / 38.7 |
| ZN 1 (diag) THU release+1m dir=against hold=60m | negative pre-2023 | 463 | -11.7 | -47.3 | -52.4 | 35.6 | -0.49 / -1.96 / -2.17 | 23.9 / -11.7 |
| ZN 2 (diag) THU release+2m dir=against hold=60m | negative pre-2023 | 461 | -2.3 | -37.9 | -42.9 | 35.6 | -0.10 / -1.65 / -1.87 | 20.9 / -14.7 |
| ZN 3 (diag) TNC release+2m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 585 | 0.1 | -35.6 | -40.6 | 35.6 | 0.00 / -1.61 / -1.84 | 14.3 / -21.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): CL: 5 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 0.00, p(top) = 0.12); ES: 0 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 1.00); GC: 7 cells pass the clean rule against a replicate mean of 3.3 (p(count) = 0.01, p(top) = 0.61); NQ: 6 cells pass the clean rule against a replicate mean of 10.0 (p(count) = 0.97, p(top) = 0.94); RTY: 4 cells pass the clean rule against a replicate mean of 3.4 (p(count) = 0.48, p(top) = 0.73); YM: 4 cells pass the clean rule against a replicate mean of 3.8 (p(count) = 0.50, p(top) = 0.84); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 26 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.21 (NQ TNC release+5m dir=against hold=60m); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 4; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 15, 'gross-positive, cost-negative pre-2023': 9, 'positive pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_7.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw7/ (`SW7_CO_all_selected_scored.csv`).

DONE SW7
