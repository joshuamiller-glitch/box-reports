# REPORT SW1 - regime-gated trend sleeves: ST/Donchian/EMA-cross entries only after a high or low prior-day-range day (D08 H3/H4)

**Verdict: LEAD. FOUND 0, LEAD 3, INSURANCE 1.** 60 selected cells (+9 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.31; best pair-window standalone Sharpe +1.78.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: bar signal ST(14,2) flip / Donchian-20 break / EMA 9-21 cross on 5- or 15-min bars, with or against, exact hold 60 or 180 min (no stop), taken only when the prior label day's range/open percentile among the 250 days before it is >= 0.67 ('hi') or <= 0.33 ('lo'); sessions all or day.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 96 cells per instrument = 2 bar sizes x 3 signals x 2 directions x 2 holds x 2 sessions x 2 regimes.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |        19 |               1.787 |                2 |         10 |            0 |
| CL    |      96 |         96 |         3 |               1.214 |                2 |          3 |            3 |
| ES    |      96 |         96 |        10 |               1.601 |                2 |         10 |            0 |
| GC    |      96 |         96 |         8 |               1.13  |                2 |          8 |            2 |
| NQ    |      96 |         96 |        20 |               1.262 |                2 |         10 |            0 |
| RTY   |      96 |         96 |        16 |               1.03  |                2 |         10 |            0 |
| YM    |      96 |         96 |         9 |               1.036 |                2 |          9 |            1 |
| ZN    |      96 |         96 |         0 |              -0.024 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                   10 |             5.79 |              12 |       0.03 |                       0.954 |            0.631 |           0.855 |     0.03 |       1.601 |                1.516 |
| NQ    |     100 |                   20 |            15.25 |              28 |       0.1  |                       0.904 |            0.877 |           1.119 |     0.38 |       1.262 |                2.124 |
| RTY   |     100 |                   16 |             7.16 |              12 |       0    |                       0.804 |            0.67  |           0.898 |     0.16 |       1.03  |                1.985 |
| YM    |     100 |                    9 |             7.84 |              17 |       0.39 |                       0.59  |            0.659 |           0.89  |     0.69 |       1.036 |                1.794 |
| GC    |     100 |                    8 |             5.96 |              12 |       0.18 |                       0.458 |            0.678 |           0.961 |     0.9  |       1.13  |                1.769 |
| CL    |     100 |                    3 |             3.4  |               9 |       0.69 |                       0.61  |            0.608 |           1.064 |     0.45 |       1.214 |                1.704 |
| ZN    |     100 |                    0 |             0.05 |               1 |       1    |                     nan     |            0.531 |           0.913 |   nan    |     nan     |                0.913 |
| BTC   |     100 |                   19 |            11.33 |              21 |       0.03 |                       1.019 |            0.768 |           0.992 |     0.03 |       1.787 |                2.135 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m don[20] dir=against hold=180m all pdrange hi0.67 | 567 | 2 | 1.60 | 0.09 | 1.27 | 0.82 / 0.95 | 0.27 / -0.27 / 0.49 | 0.15 | 0.09 | 1.00 | 0.06 | 0.17 | 846 | NO |
| ES 2 | 15m st[14, 2.0] dir=with hold=180m day pdrange lo0.33 | 189 | 2 | 1.38 | -0.28 | 0.18 | -1.57 / 0.68 | 0.21 / -0.54 / -0.40 | -0.08 | 0.22 | 0.83 | -0.21 | 0.00 | 311 | NO |
| ES 3 | 5m emax[9, 21] dir=with hold=180m day pdrange lo0.33 | 240 | 2 | 1.37 | -0.25 | 0.60 | -0.50 / 0.78 | 0.20 / -0.42 / -0.17 | -0.01 | 0.35 | 0.99 | -0.13 | 0.38 | 402 | NO |
| ES 4 | 5m st[14, 2.0] dir=with hold=180m day pdrange hi0.67 | 284 | 2 | 1.34 | -0.24 | 1.04 | 0.51 / 1.24 | 0.24 / 0.15 / -0.09 | 0.13 | 0.14 | 0.99 | 0.01 | 0.38 | 407 | NO |
| ES 5 | 15m st[14, 2.0] dir=with hold=180m all pdrange lo0.33 | 434 | 2 | 1.15 | -0.85 | -0.14 | -2.09 / 0.72 | 0.17 / -0.58 / -0.23 | -0.15 | 0.19 | 0.88 | -0.22 | 0.00 | 755 | NO |
| ES 6 | 15m emax[9, 21] dir=against hold=180m day pdrange hi0.67 | 138 | 2 | 0.64 | 0.44 | 0.22 | -0.37 / 1.41 | 0.14 / -0.46 / -0.07 | -0.01 | 0.21 | 0.81 | -0.17 | 0.00 | 200 | NO |
| ES 7 | 15m st[14, 2.0] dir=with hold=60m day pdrange lo0.33 | 299 | 2 | 0.64 | -0.69 | -0.41 | -1.44 / 0.37 | 0.08 / -0.60 / -0.63 | -0.28 | 0.64 | 0.85 | -0.41 | 0.00 | 496 | NO |
| ES 8 | 15m st[14, 2.0] dir=with hold=60m all pdrange lo0.33 | 638 | 2 | 0.55 | -1.68 | -0.60 | -1.70 / -0.00 | 0.05 / -0.88 / -0.51 | -0.42 | 0.67 | 0.99 | -0.43 | 0.00 | 1113 | NO |
| ES 9 | 5m emax[9, 21] dir=with hold=180m all pdrange lo0.33 | 710 | 2 | 0.51 | -1.78 | -0.26 | -1.30 / 0.75 | 0.04 / -0.56 / -0.13 | -0.24 | 0.06 | 0.91 | -0.28 | 0.00 | 1206 | NO |
| ES 10 | 15m st[14, 2.0] dir=with hold=60m day pdrange hi0.67 | 305 | 2 | 0.37 | -0.40 | -0.15 | -0.91 / 1.10 | 0.05 / -0.45 / -0.09 | -0.11 | -0.26 | 0.74 | -0.24 | 0.00 | 448 | NO |
| NQ 1 | 15m emax[9, 21] dir=with hold=60m day pdrange lo0.33 | 238 | 2 | 1.26 | -0.25 | 0.29 | -0.91 / 1.02 | 0.23 / 0.13 / -0.74 | -0.02 | -0.04 | 0.84 | -0.22 | 0.62 | 352 | NO |
| NQ 2 | 15m st[14, 2.0] dir=with hold=180m day pdrange lo0.33 | 213 | 2 | 1.20 | 0.13 | 0.53 | -0.23 / 1.45 | 0.19 / -0.49 / 0.14 | 0.07 | 0.11 | 0.86 | -0.12 | 0.38 | 311 | NO |
| NQ 3 | 15m don[20] dir=against hold=180m all pdrange hi0.67 | 550 | 2 | 1.03 | 0.52 | 0.61 | 0.16 / 1.55 | 0.23 / -0.15 / -0.03 | 0.11 | 0.57 | 0.91 | -0.10 | 0.50 | 929 | NO |
| NQ 4 | 5m st[14, 2.0] dir=with hold=60m day pdrange lo0.33 | 604 | 2 | 1.01 | -0.08 | 0.46 | -0.36 / 0.97 | 0.16 / -0.18 / -0.06 | 0.03 | 0.31 | 0.94 | -0.14 | 0.50 | 900 | NO |
| NQ 5 | 5m emax[9, 21] dir=against hold=180m all pdrange hi0.67 | 652 | 2 | 0.88 | -0.02 | -0.19 | -1.12 / 1.20 | 0.09 / -1.04 / -0.36 | -0.20 | 0.45 | 0.52 | -0.46 | 0.00 | 1091 | NO |
| NQ 6 | 15m don[20] dir=against hold=180m day pdrange lo0.33 | 236 | 2 | 0.80 | -0.20 | 0.70 | 0.57 / 1.48 | 0.20 / -0.26 / 0.38 | 0.17 | 0.22 | 0.93 | -0.01 | 0.67 | 349 | NO |
| NQ 7 | 5m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | 226 | 2 | 0.77 | 0.00 | 0.70 | 0.58 / 1.59 | 0.08 / 0.51 / -0.26 | 0.06 | -0.26 | 0.90 | -0.08 | 0.75 | 363 | NO |
| NQ 8 | 5m st[14, 2.0] dir=with hold=180m day pdrange lo0.33 | 311 | 2 | 0.76 | 0.36 | 0.51 | 0.21 / 1.25 | 0.14 / 0.06 / -0.06 | 0.09 | 0.14 | 0.87 | -0.10 | 0.38 | 464 | NO |
| NQ 9 | 5m st[14, 2.0] dir=with hold=180m day pdrange hi0.67 | 264 | 2 | 0.68 | 0.40 | 0.85 | 1.09 / 1.20 | 0.14 / 0.06 / 0.27 | 0.16 | -0.39 | 0.95 | -0.03 | 0.25 | 429 | NO |
| NQ 10 | 15m don[20] dir=against hold=180m day pdrange hi0.67 | 215 | 2 | 0.66 | 0.24 | 0.39 | -0.09 / 1.34 | 0.16 / -0.14 / -0.04 | 0.07 | 0.43 | 0.83 | -0.09 | 0.67 | 347 | NO |
| RTY 1 | 15m don[20] dir=against hold=180m day pdrange hi0.67 | 217 | 2 | 1.03 | 0.14 | 0.79 | 0.54 / 1.33 | 0.15 / -0.40 / 0.40 | 0.10 | -0.38 | 0.96 | -0.08 | 0.50 | 328 | NO |
| RTY 2 | 5m st[14, 2.0] dir=with hold=180m day pdrange hi0.67 | 293 | 2 | 1.03 | 0.47 | 0.56 | -0.27 / 1.06 | 0.12 / -0.01 / -0.22 | 0.01 | -0.28 | 0.90 | -0.14 | 0.50 | 426 | NO |
| RTY 3 | 15m don[20] dir=against hold=180m all pdrange hi0.67 | 575 | 2 | 0.97 | 0.04 | 0.82 | 0.56 / 1.31 | 0.13 / -0.15 / 0.40 | 0.09 | -0.61 | 1.00 | -0.03 | 0.50 | 873 | NO |
| RTY 4 | 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | 218 | 2 | 0.95 | 0.10 | 0.68 | 0.30 / 0.74 | 0.15 / 0.39 / -0.19 | 0.07 | 0.05 | 0.98 | -0.05 | 0.75 | 310 | NO |
| RTY 5 | 15m don[20] dir=against hold=60m day pdrange lo0.33 | 374 | 2 | 0.81 | -0.82 | -0.09 | -1.46 / 0.92 | 0.13 / -0.94 / 0.04 | -0.11 | -0.18 | 0.88 | -0.25 | 0.00 | 602 | NO |
| RTY 6 | 15m emax[9, 21] dir=with hold=180m day pdrange lo0.33 | 137 | 2 | 0.80 | -0.17 | 0.03 | -1.13 / 1.65 | 0.16 / -0.11 / -0.47 | -0.03 | 0.13 | 0.70 | -0.21 | 0.00 | 213 | NO |
| RTY 7 | 5m emax[9, 21] dir=with hold=180m day pdrange lo0.33 | 249 | 2 | 0.78 | -0.06 | 0.24 | -0.46 / 1.15 | 0.11 / -0.38 / -0.16 | -0.04 | -0.18 | 0.86 | -0.19 | 0.00 | 409 | NO |
| RTY 8 | 15m st[14, 2.0] dir=against hold=60m day pdrange hi0.67 | 301 | 2 | 0.67 | -0.14 | 0.49 | 0.15 / 0.77 | 0.08 / -0.32 / 0.01 | -0.03 | 0.28 | 0.96 | -0.17 | 0.25 | 449 | NO |
| RTY 9 | 5m st[14, 2.0] dir=with hold=180m all pdrange hi0.67 | 826 | 2 | 0.56 | -0.25 | 0.01 | -0.81 / 0.89 | 0.04 / -0.01 / -0.28 | -0.10 | 0.21 | 0.84 | -0.23 | 0.00 | 1249 | NO |
| RTY 10 | 5m st[14, 2.0] dir=against hold=180m day pdrange lo0.33 | 290 | 2 | 0.44 | -0.43 | 0.68 | 0.96 / 1.35 | 0.05 / 0.60 / 0.03 | 0.07 | 0.05 | 0.96 | -0.09 | 0.50 | 475 | NO |
| YM 1 | 5m don[20] dir=against hold=180m day pdrange lo0.33 | 313 | 2 | 1.04 | -0.51 | 0.82 | 0.63 / 1.10 | 0.22 / 0.02 / 0.15 | 0.15 | 0.11 | 0.99 | -0.02 | 0.50 | 505 | NO |
| YM 2 | 15m emax[9, 21] dir=against hold=180m all pdrange hi0.67 | 394 | 2 | 0.88 | 0.67 | 0.62 | 0.44 / 1.19 | 0.10 / -0.34 / 0.40 | 0.05 | -0.19 | 0.96 | -0.15 | 0.00 | 582 | NO |
| YM 3 | 15m don[20] dir=against hold=180m all pdrange hi0.67 | 577 | 2 | 0.87 | 0.19 | 0.53 | 0.13 / 1.09 | 0.19 / -0.66 / 0.39 | 0.07 | 0.16 | 0.91 | -0.09 | 0.00 | 880 | NO |
| YM 4 | 15m don[20] dir=against hold=180m day pdrange lo0.33 | 223 | 2 | 0.68 | -0.61 | 0.85 | 1.12 / 1.21 | 0.11 / 0.13 / 0.51 | 0.16 | 0.01 | 0.99 | -0.03 | 0.33 | 347 | LEAD |
| YM 5 | 15m emax[9, 21] dir=against hold=180m day pdrange hi0.67 | 162 | 2 | 0.53 | 0.23 | 0.69 | 0.91 / 1.52 | 0.05 / -0.04 / 0.33 | 0.08 | 0.03 | 0.92 | -0.10 | 0.50 | 221 | NO |
| YM 6 | 5m st[14, 2.0] dir=against hold=180m all pdrange hi0.67 | 830 | 2 | 0.52 | -0.36 | 0.80 | 1.19 / 1.22 | 0.06 / 0.20 / 0.06 | 0.03 | -0.22 | 0.99 | -0.09 | 0.25 | 1258 | NO |
| YM 7 | 5m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | 260 | 2 | 0.48 | -0.38 | -0.16 | -1.32 / 1.21 | 0.08 / -0.06 / -0.41 | -0.08 | 0.40 | 0.47 | -0.22 | 0.00 | 380 | NO |
| YM 8 | 15m don[20] dir=against hold=180m all pdrange lo0.33 | 557 | 2 | 0.24 | -0.74 | 0.29 | 0.36 / 0.70 | 0.01 / -0.03 / 0.34 | -0.02 | -0.13 | 0.95 | -0.14 | 0.33 | 901 | NO |
| YM 9 | 5m st[14, 2.0] dir=against hold=60m day pdrange hi0.67 | 612 | 2 | 0.06 | -0.47 | 0.38 | 1.01 / 0.87 | 0.04 / 0.05 / 0.25 | 0.04 | -0.50 | 0.94 | -0.09 | 0.25 | 902 | NO |
| YM 10 (diag) | 15m st[14, 2.0] dir=with hold=60m day pdrange hi0.67 | 345 | 1 | 0.72 | -0.21 | -0.13 | -1.52 / 0.97 | 0.07 / -0.37 / -0.32 | -0.13 | -0.07 | 0.73 | -0.26 | 0.00 | 497 | diag |
| GC 1 | 5m st[14, 2.0] dir=against hold=60m day pdrange hi0.67 | 597 | 2 | 1.13 | -0.57 | 0.07 | -0.22 / 1.25 | 0.15 / -2.17 / 0.42 | -0.38 | 0.24 | 0.84 | -1.04 | 0.00 | 1024 | NO |
| GC 2 | 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | 147 | 2 | 0.76 | -0.67 | 0.24 | -0.02 / 1.23 | 0.11 / 0.09 / -0.57 | -0.05 | 0.52 | 0.76 | -0.36 | 0.00 | 244 | NO |
| GC 3 | 5m st[14, 2.0] dir=against hold=180m day pdrange lo0.33 | 238 | 2 | 0.50 | -0.12 | 0.43 | 0.48 / 1.35 | 0.05 / -0.26 / 0.29 | 0.03 | 0.37 | 0.85 | -0.18 | 0.38 | 328 | NO |
| GC 4 | 15m emax[9, 21] dir=against hold=180m all pdrange hi0.67 | 440 | 2 | 0.38 | 0.49 | 0.68 | 1.00 / 1.56 | 0.03 / -0.10 / 0.23 | 0.05 | -0.19 | 0.91 | -0.29 | 0.12 | 746 | NO |
| GC 5 | 15m st[14, 2.0] dir=with hold=180m day pdrange lo0.33 | 155 | 2 | 0.33 | -0.26 | -0.20 | -0.82 / 1.16 | 0.08 / -0.01 / -0.80 | -0.16 | -0.46 | 0.44 | -0.44 | 0.00 | 214 | NO |
| GC 6 | 5m don[20] dir=with hold=180m day pdrange hi0.67 | 361 | 2 | 0.25 | -0.69 | -0.75 | -1.50 / 1.31 | -0.05 / -0.20 / -1.14 | -0.38 | 0.45 | 0.15 | -0.68 | 0.00 | 595 | NO |
| GC 7 | 5m emax[9, 21] dir=with hold=180m day pdrange lo0.33 | 214 | 2 | 0.22 | -0.64 | -0.56 | -1.12 / 1.41 | -0.00 / -0.33 / -0.94 | -0.32 | -0.46 | 0.35 | -0.62 | 0.00 | 297 | NO |
| GC 8 | 15m don[20] dir=against hold=180m day pdrange hi0.67 | 226 | 2 | 0.09 | -0.13 | 0.68 | 1.14 / 1.20 | 0.07 / 0.67 / -0.17 | 0.12 | -0.22 | 0.95 | -0.21 | 0.33 | 374 | NO |
| GC 9 (diag) | 5m st[14, 2.0] dir=against hold=180m day pdrange hi0.67 | 309 | 1 | 0.79 | 0.14 | 1.70 | 2.70 / 1.34 | 0.08 / 1.50 / 1.02 | 0.41 | -0.25 | 1.00 | 0.20 | 0.75 | 529 | diag |
| GC 10 (diag) | 15m emax[9, 21] dir=against hold=60m all pdrange lo0.33 | 474 | 1 | 0.55 | -2.37 | 0.10 | -0.18 / 1.21 | 0.07 / -0.40 / -0.62 | -0.25 | 0.58 | 0.97 | -0.44 | 0.00 | 686 | diag |
| CL 1 | 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | 179 | 2 | 1.21 | -0.50 | 0.53 | 0.10 / 0.97 | 0.25 / 0.19 / -0.23 | 0.02 | -0.42 | 1.00 | -0.20 | 0.38 | 336 | NO |
| CL 2 | 15m st[14, 2.0] dir=with hold=60m day pdrange hi0.67 | 256 | 2 | 0.50 | -0.58 | -0.05 | -0.38 / 0.66 | 0.08 / -0.23 / -0.71 | -0.29 | -0.07 | 0.92 | -0.50 | 0.00 | 472 | NO |
| CL 3 | 15m don[20] dir=against hold=180m day pdrange lo0.33 | 247 | 2 | 0.12 | -0.73 | 0.31 | 0.79 / 0.93 | -0.03 / -0.14 / 0.17 | -0.06 | 0.25 | 0.93 | -0.15 | 0.00 | 320 | NO |
| CL 4 (diag) | 15m emax[9, 21] dir=with hold=180m day pdrange lo0.33 | 153 | 1 | 0.62 | -0.12 | 0.09 | -1.58 / 0.98 | 0.08 / -0.01 / -0.19 | -0.05 | -0.19 | 0.85 | -0.18 | 0.00 | 198 | diag |
| CL 5 (diag) | 5m emax[9, 21] dir=against hold=180m day pdrange hi0.67 | 215 | 1 | 0.61 | -0.27 | -0.21 | -0.88 / 1.38 | 0.07 / -0.12 / -0.88 | -0.24 | 0.44 | 0.62 | -0.44 | 0.00 | 424 | diag |
| CL 6 (diag) | 15m emax[9, 21] dir=against hold=180m all pdrange hi0.67 | 343 | 1 | 0.28 | -0.13 | -0.55 | -1.14 / 1.05 | -0.05 / -0.42 / -0.98 | -0.44 | -0.31 | 0.51 | -0.66 | 0.00 | 675 | diag |
| ZN 1 (diag) | 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | 107 | 1 | -0.02 | -1.48 | -0.64 | -2.09 / -1.43 | -0.04 / -0.22 / -0.45 | -0.38 | -0.13 | 1.00 | -0.34 | 0.00 | 171 | diag |
| ZN 2 (diag) | 15m don[20] dir=against hold=180m day pdrange lo0.33 | 221 | 1 | -0.46 | -2.12 | -1.36 | -3.13 / -1.82 | -0.11 / -0.93 / -0.30 | -0.56 | -0.19 | 0.98 | -0.44 | 0.00 | 347 | diag |
| ZN 3 (diag) | 5m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | 187 | 0 | -0.77 | -1.82 | -1.04 | -1.90 / -0.81 | -0.16 / -0.23 / -0.26 | -0.44 | -0.15 | 0.92 | -0.37 | 0.00 | 309 | diag |
| BTC 1 | 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | 129 | 2 | 1.79 | -1.26 | 1.78 | 1.77 / 1.70 | 0.36 / 0.23 / 0.13 | 0.29 | -0.18 | 0.99 | 0.14 | 0.50 | 190 | LEAD(gate3-7 fail: plateau ) |
| BTC 2 | 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | 186 | 2 | 1.23 | -0.52 | 1.04 | 0.65 / 1.36 | 0.26 / -0.20 / 0.14 | 0.15 | -0.00 | 0.99 | 0.02 | 0.38 | 279 | NO |
| BTC 3 | 15m emax[9, 21] dir=with hold=180m all pdrange hi0.67 | 362 | 2 | 1.22 | -2.42 | 0.96 | 0.53 / 1.44 | 0.23 / -0.31 / 0.19 | 0.12 | 0.07 | 0.99 | -0.02 | 0.50 | 552 | NO |
| BTC 4 | 15m st[14, 2.0] dir=with hold=180m day pdrange hi0.67 | 177 | 2 | 1.07 | 0.03 | 0.29 | -0.71 / 1.35 | 0.20 / -0.96 / 0.21 | 0.02 | -0.06 | 0.78 | -0.20 | 0.38 | 272 | NO |
| BTC 5 | 15m st[14, 2.0] dir=against hold=180m day pdrange lo0.33 | 181 | 2 | 0.99 | 0.65 | 0.65 | 0.05 / 1.32 | 0.18 / 0.20 / -0.19 | 0.08 | 0.32 | 0.94 | -0.09 | 0.38 | 281 | NO |
| BTC 6 | 15m st[14, 2.0] dir=with hold=60m all pdrange lo0.33 | 684 | 2 | 0.82 | -0.27 | 0.88 | 1.18 / 0.90 | 0.08 / 0.32 / -0.02 | 0.02 | -0.06 | 0.99 | -0.07 | 0.38 | 1064 | NO |
| BTC 7 | 5m st[14, 2.0] dir=with hold=180m all pdrange lo0.33 | 827 | 2 | 0.81 | -1.36 | 0.22 | -0.54 / 1.15 | 0.16 / -0.33 / -0.02 | -0.02 | 0.42 | 0.79 | -0.15 | 0.50 | 1292 | NO |
| BTC 8 | 5m st[14, 2.0] dir=against hold=180m all pdrange hi0.67 | 845 | 2 | 0.79 | -0.77 | 0.86 | 0.95 / 1.00 | 0.14 / 0.39 / 0.07 | 0.11 | 0.41 | 0.99 | -0.04 | 0.25 | 1317 | NO |
| BTC 9 | 5m emax[9, 21] dir=against hold=60m day pdrange hi0.67 | 431 | 2 | 0.75 | -0.67 | 1.23 | 1.94 / 0.91 | 0.10 / 0.62 / 0.15 | 0.13 | 0.17 | 1.00 | 0.00 | 0.50 | 668 | LEAD |
| BTC 10 | 15m emax[9, 21] dir=with hold=60m all pdrange hi0.67 | 495 | 2 | 0.73 | -0.76 | -0.00 | -1.29 / 1.33 | 0.16 / -0.83 / 0.04 | -0.08 | 0.12 | 0.82 | -0.20 | 0.00 | 758 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 60 |
| diagnostic cells read | 9 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 3 / 2 / 2 |
| all-in uplift @20% > 0 (all scored) | 42 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 6 |
| standalone pair-window Sharpe above own random-entry null p95 | 27 |
| worst-decile corr <= +0.30 | 53 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 15 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 3 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | clean | 1.78 | 4.67 | -75586 | -64672 | 233271 | -106278 | 6.91 | 24.8 | 1.82 | -80111 | 229300 | -92598 |
| BTC 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | H1 | 2.12 | 4.25 | -106659 | -79892 | 318165 | -152001 | 1.64 | 17.9 | 3.06 | -80246 | 137633 | -83559 |
| BTC 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | H2 | 1.44 | 3.53 | -50805 | -40668 | 119050 | -62801 | 2.36 | 25.0 | 2.43 | -82753 | 216083 | -84350 |
| BTC 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | all | 1.78 | 4.33 | -81071 | -65230 | 363809 | -152001 | 6.64 | 23.8 | 2.16 | -81081 | 229300 | -92598 |
| CL 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | clean | 1.26 | 2.58 | -102926 | -83059 | 345876 | -142770 | 3.31 | 25.7 | 1.71 | -78855 | 268874 | -85202 |
| CL 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | H1 | 1.21 | 2.76 | -44114 | -39778 | 130037 | -48328 | 1.27 | 25.0 | 3.01 | -75888 | 151579 | -76932 |
| CL 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | H2 | -0.03 | -0.04 | -573200 | -411322 | 1039831 | -691775 | -0.03 | 41.7 | 2.07 | -88404 | 217528 | -93646 |
| CL 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | all | 0.53 | 0.72 | -245155 | -161132 | 1039831 | -691775 | 1.23 | 29.2 | 1.98 | -81083 | 268874 | -93646 |
| ES 15m don[20] dir=against hold=180m all pdrange hi0.67 | clean | 1.59 | 3.30 | -99710 | -81491 | 410708 | -168568 | 3.52 | 23.8 | 1.73 | -83743 | 251928 | -96055 |
| ES 15m don[20] dir=against hold=180m all pdrange hi0.67 | H1 | -1.61 | -1.82 | -133325 | -123889 | 416010 | -138493 | -0.81 | 28.6 | 2.55 | -63749 | 150501 | -70172 |
| ES 15m don[20] dir=against hold=180m all pdrange hi0.67 | H2 | 2.07 | 6.02 | -94182 | -81008 | 351881 | -96777 | 2.50 | 25.0 | 2.78 | -91326 | 217425 | -99009 |
| ES 15m don[20] dir=against hold=180m all pdrange hi0.67 | all | 1.27 | 2.54 | -111234 | -93864 | 563961 | -168568 | 3.52 | 25.0 | 2.09 | -84725 | 251928 | -99009 |
| GC 15m don[20] dir=against hold=180m day pdrange hi0.67 | clean | 0.09 | 0.13 | -140530 | -117554 | 478248 | -178058 | 0.17 | 37.1 | 1.53 | -84690 | 273677 | -95793 |
| GC 15m don[20] dir=against hold=180m day pdrange hi0.67 | H1 | 2.05 | 4.13 | -350081 | -288173 | 842556 | -532904 | 2.17 | 28.6 | 3.50 | -115584 | 245764 | -184868 |
| GC 15m don[20] dir=against hold=180m day pdrange hi0.67 | H2 | 0.33 | 0.48 | -412149 | -349582 | 994414 | -497546 | 0.33 | 41.7 | 2.12 | -109772 | 283905 | -111616 |
| GC 15m don[20] dir=against hold=180m day pdrange hi0.67 | all | 0.68 | 1.13 | -292512 | -220180 | 994414 | -532904 | 2.25 | 36.9 | 2.02 | -104243 | 283905 | -184868 |
| NQ 15m don[20] dir=against hold=180m day pdrange lo0.33 | clean | 0.81 | 1.33 | -118583 | -97702 | 330371 | -150815 | 2.22 | 40.0 | 1.66 | -81409 | 238130 | -85853 |
| NQ 15m don[20] dir=against hold=180m day pdrange lo0.33 | H1 | -0.53 | -0.80 | -131315 | -113263 | 394463 | -166577 | -0.35 | 42.9 | 2.56 | -77173 | 143848 | -78551 |
| NQ 15m don[20] dir=against hold=180m day pdrange lo0.33 | H2 | 1.20 | 2.43 | -159140 | -114699 | 290678 | -228517 | 1.88 | 25.0 | 2.68 | -81061 | 218981 | -82524 |
| NQ 15m don[20] dir=against hold=180m day pdrange lo0.33 | all | 0.70 | 1.21 | -134566 | -107005 | 394463 | -228517 | 2.90 | 37.5 | 2.04 | -81122 | 238130 | -85853 |
| RTY 15m don[20] dir=against hold=180m all pdrange hi0.67 | clean | 0.99 | 2.46 | -77941 | -64006 | 215213 | -99087 | 4.15 | 36.2 | 1.59 | -83334 | 277390 | -85878 |
| RTY 15m don[20] dir=against hold=180m all pdrange hi0.67 | H1 | -1.33 | -1.50 | -103054 | -86912 | 301622 | -104487 | -0.64 | 28.6 | 2.68 | -71603 | 172212 | -75552 |
| RTY 15m don[20] dir=against hold=180m all pdrange hi0.67 | H2 | 1.27 | 3.11 | -114046 | -95759 | 255000 | -145081 | 2.08 | 33.3 | 2.70 | -78118 | 217425 | -78820 |
| RTY 15m don[20] dir=against hold=180m all pdrange hi0.67 | all | 0.82 | 1.84 | -95780 | -77167 | 426372 | -145081 | 2.88 | 34.5 | 1.99 | -81490 | 277390 | -85878 |
| YM 15m don[20] dir=against hold=180m day pdrange lo0.33 | clean | 0.63 | 0.99 | -117441 | -100208 | 591480 | -166978 | 0.96 | 32.4 | 1.57 | -82438 | 240503 | -87459 |
| YM 15m don[20] dir=against hold=180m day pdrange lo0.33 | H1 | -0.11 | -0.17 | -191561 | -175005 | 553097 | -208131 | -0.08 | 42.9 | 2.96 | -84516 | 147456 | -102242 |
| YM 15m don[20] dir=against hold=180m day pdrange lo0.33 | H2 | 2.18 | 4.98 | -140121 | -103543 | 187783 | -187783 | 5.58 | 33.3 | 2.80 | -83202 | 212134 | -90226 |
| YM 15m don[20] dir=against hold=180m day pdrange lo0.33 | all | 0.85 | 1.43 | -152173 | -123359 | 941241 | -208131 | 1.67 | 34.5 | 2.05 | -84906 | 240503 | -102242 |
| ZN 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 (diag) | clean | 0.03 | 0.05 | -153222 | -124783 | 964480 | -207757 | 0.03 | 26.7 | 1.42 | -92242 | 297904 | -116257 |
| ZN 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 (diag) | H1 | -2.23 | -2.38 | -84604 | -74519 | 279250 | -90767 | -0.89 | 21.4 | 2.60 | -77610 | 163546 | -78287 |
| ZN 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 (diag) | H2 | -2.17 | -2.34 | -169209 | -124301 | 679408 | -247650 | -0.94 | 50.0 | 1.85 | -85539 | 217425 | -93663 |
| ZN 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 (diag) | all | -0.64 | -0.82 | -151914 | -119942 | 964480 | -247650 | -0.89 | 31.0 | 1.69 | -89327 | 297904 | -116257 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m don[20] dir=against hold=180m all pdrange hi0.67 | -7.8 | -2.7 | 16.8 | 38.8 | 4.0 / 18.6 | 23.3 / 33.9 | NO |
| NQ 15m don[20] dir=against hold=180m day pdrange lo0.33 | -17.2 | 20.3 | 23.7 | 43.3 | 19.7 / 21.7 | 24.9 / 26.5 | NO |
| RTY 15m don[20] dir=against hold=180m all pdrange hi0.67 | -16.3 | 18.6 | 23.7 | 31.5 | 18.0 / 19.6 | 33.9 / 34.8 | NO |
| YM 15m don[20] dir=against hold=180m day pdrange lo0.33 | -12.4 | -9.9 | 16.9 | 33.1 | 15.2 / 21.7 | -15.9 / 4.1 | NO |
| GC 15m don[20] dir=against hold=180m day pdrange hi0.67 | -5.0 | -160.1 | -36.7 | -21.3 | -0.1 / 17.8 | -174.2 / -69.7 | NO |
| CL 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | -15.7 | -113.6 | -3.4 | 6.5 | 19.2 / 28.5 | 31.2 / 33.3 | NO |
| ZN 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 (diag) | -39.6 | -36.5 | 6.1 | 3.8 | -37.6 / 3.7 | 30.0 / 30.0 | NO |
| BTC 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | -3.0 | 6.6 | 25.1 | 40.8 | 5.8 / 26.3 | 19.9 / 24.9 | INSURANCE |

INSURANCE count: 1.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m don[20] dir=against hold=180m all pdrange hi0.67 | positive pre-2023 | 2582 | 34.5 | 5.1 | 19.0 | 29.4 | 0.58 / 0.09 / 0.32 | 108.8 / 79.5 |
| ES 2 15m st[14, 2.0] dir=with hold=180m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 839 | 9.5 | -19.8 | -6.5 | 29.4 | 0.13 / -0.28 / -0.09 | 188.6 / 159.3 |
| ES 3 5m emax[9, 21] dir=with hold=180m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 1170 | 15.1 | -14.2 | -0.9 | 29.4 | 0.27 / -0.25 / -0.02 | 166.0 / 136.7 |
| ES 4 5m st[14, 2.0] dir=with hold=180m day pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 1298 | 5.7 | -23.6 | -9.6 | 29.4 | 0.06 / -0.24 / -0.10 | 200.7 / 171.3 |
| ES 5 15m st[14, 2.0] dir=with hold=180m all pdrange lo0.33 | negative pre-2023 | 2073 | -1.4 | -30.8 | -17.5 | 29.4 | -0.04 / -0.85 / -0.49 | 88.0 / 58.7 |
| ES 6 15m emax[9, 21] dir=against hold=180m day pdrange hi0.67 | positive pre-2023 | 637 | 89.6 | 60.3 | 74.3 | 29.4 | 0.65 / 0.44 / 0.54 | 130.2 / 100.8 |
| ES 7 15m st[14, 2.0] dir=with hold=60m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 1419 | 8.1 | -21.3 | -8.0 | 29.4 | 0.26 / -0.69 / -0.26 | 53.7 / 24.4 |
| ES 8 15m st[14, 2.0] dir=with hold=60m all pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 3040 | 1.5 | -27.8 | -14.6 | 29.4 | 0.09 / -1.68 / -0.90 | 38.9 / 9.5 |
| ES 9 5m emax[9, 21] dir=with hold=180m all pdrange lo0.33 | negative pre-2023 | 3552 | -11.1 | -40.5 | -27.2 | 29.4 | -0.50 / -1.78 / -1.20 | 45.4 / 16.0 |
| ES 10 15m st[14, 2.0] dir=with hold=60m day pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 1404 | 7.4 | -21.9 | -7.9 | 29.4 | 0.14 / -0.40 / -0.14 | 55.0 / 25.6 |
| NQ 1 15m emax[9, 21] dir=with hold=60m day pdrange lo0.33 | negative pre-2023 | 970 | -1.3 | -15.7 | -7.7 | 14.4 | -0.02 / -0.25 / -0.12 | 148.4 / 134.0 |
| NQ 2 15m st[14, 2.0] dir=with hold=180m day pdrange lo0.33 | positive pre-2023 | 835 | 31.7 | 17.4 | 25.4 | 14.4 | 0.24 / 0.13 / 0.19 | 214.4 / 200.0 |
| NQ 3 15m don[20] dir=against hold=180m all pdrange hi0.67 | positive pre-2023 | 2756 | 55.4 | 41.1 | 49.4 | 14.4 | 0.70 / 0.52 / 0.63 | 135.3 / 121.0 |
| NQ 4 5m st[14, 2.0] dir=with hold=60m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 2506 | 11.9 | -2.5 | 5.5 | 14.4 | 0.38 / -0.08 / 0.18 | 82.7 / 68.3 |
| NQ 5 5m emax[9, 21] dir=against hold=180m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 3567 | 12.9 | -1.5 | 6.9 | 14.4 | 0.19 / -0.02 / 0.10 | 88.6 / 74.2 |
| NQ 6 15m don[20] dir=against hold=180m day pdrange lo0.33 | negative pre-2023 | 963 | -8.4 | -22.7 | -14.8 | 14.4 | -0.07 / -0.20 / -0.13 | 176.4 / 162.1 |
| NQ 7 5m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | positive pre-2023 | 1184 | 14.7 | 0.3 | 8.7 | 14.4 | 0.09 / 0.00 / 0.06 | 293.5 / 279.2 |
| NQ 8 5m st[14, 2.0] dir=with hold=180m day pdrange lo0.33 | positive pre-2023 | 1240 | 50.5 | 36.1 | 44.1 | 14.4 | 0.50 / 0.36 / 0.44 | 134.7 / 120.4 |
| NQ 9 5m st[14, 2.0] dir=with hold=180m day pdrange hi0.67 | positive pre-2023 | 1368 | 72.5 | 58.1 | 66.5 | 14.4 | 0.50 / 0.40 / 0.46 | 192.6 / 178.3 |
| NQ 10 15m don[20] dir=against hold=180m day pdrange hi0.67 | positive pre-2023 | 1054 | 54.5 | 40.1 | 48.5 | 14.4 | 0.32 / 0.24 / 0.28 | 271.5 / 257.1 |
| RTY 1 15m don[20] dir=against hold=180m day pdrange hi0.67 | positive pre-2023 | 522 | 26.7 | 12.3 | 15.1 | 14.4 | 0.30 / 0.14 / 0.17 | 84.0 / 69.6 |
| RTY 2 5m st[14, 2.0] dir=with hold=180m day pdrange hi0.67 | positive pre-2023 | 702 | 52.3 | 37.9 | 40.7 | 14.4 | 0.64 / 0.47 / 0.50 | 87.0 / 72.6 |
| RTY 3 15m don[20] dir=against hold=180m all pdrange hi0.67 | positive pre-2023 | 1406 | 16.1 | 1.7 | 4.5 | 14.4 | 0.37 / 0.04 / 0.11 | 55.3 / 41.0 |
| RTY 4 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | positive pre-2023 | 489 | 21.1 | 6.8 | 9.6 | 14.4 | 0.32 / 0.10 / 0.15 | 58.1 / 43.7 |
| RTY 5 15m don[20] dir=against hold=60m day pdrange lo0.33 | negative pre-2023 | 886 | -12.1 | -26.5 | -25.2 | 14.4 | -0.38 / -0.82 / -0.79 | 40.3 / 25.9 |
| RTY 6 15m emax[9, 21] dir=with hold=180m day pdrange lo0.33 | negative pre-2023 | 345 | -1.8 | -16.2 | -14.9 | 14.4 | -0.02 / -0.17 / -0.16 | 81.4 / 67.1 |
| RTY 7 5m emax[9, 21] dir=with hold=180m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 588 | 10.6 | -3.8 | -2.5 | 14.4 | 0.18 / -0.06 / -0.04 | 62.9 / 48.5 |
| RTY 8 15m st[14, 2.0] dir=against hold=60m day pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 784 | 7.2 | -7.1 | -4.3 | 14.4 | 0.14 / -0.14 / -0.09 | 42.4 / 28.0 |
| RTY 9 5m st[14, 2.0] dir=with hold=180m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 2016 | 5.4 | -9.0 | -6.2 | 14.4 | 0.15 / -0.25 / -0.17 | 33.9 / 19.5 |
| RTY 10 5m st[14, 2.0] dir=against hold=180m day pdrange lo0.33 | negative pre-2023 | 663 | -9.8 | -24.1 | -22.9 | 14.4 | -0.18 / -0.43 / -0.41 | 42.6 / 28.3 |
| YM 1 5m don[20] dir=against hold=180m day pdrange lo0.33 | negative pre-2023 | 1512 | -9.0 | -23.4 | -18.1 | 14.4 | -0.20 / -0.51 / -0.40 | 70.1 / 55.7 |
| YM 2 15m emax[9, 21] dir=against hold=180m all pdrange hi0.67 | positive pre-2023 | 1818 | 46.4 | 32.1 | 37.6 | 14.4 | 0.97 / 0.67 / 0.79 | 48.7 / 34.3 |
| YM 3 15m don[20] dir=against hold=180m all pdrange hi0.67 | positive pre-2023 | 2643 | 23.2 | 8.8 | 14.4 | 14.4 | 0.51 / 0.19 / 0.32 | 48.0 / 33.6 |
| YM 4 15m don[20] dir=against hold=180m day pdrange lo0.33 | negative pre-2023 | 939 | -23.0 | -37.3 | -32.1 | 14.4 | -0.38 / -0.61 / -0.53 | 49.5 / 35.1 |
| YM 5 15m emax[9, 21] dir=against hold=180m day pdrange hi0.67 | positive pre-2023 | 622 | 38.1 | 23.8 | 29.4 | 14.4 | 0.37 / 0.23 / 0.29 | 71.5 / 57.1 |
| YM 6 5m st[14, 2.0] dir=against hold=180m all pdrange hi0.67 | negative pre-2023 | 3899 | -0.7 | -15.1 | -9.4 | 14.4 | -0.02 / -0.36 / -0.22 | 33.5 / 19.2 |
| YM 7 5m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | negative pre-2023 | 1174 | -19.3 | -33.7 | -28.0 | 14.4 | -0.22 / -0.38 / -0.31 | 48.2 / 33.8 |
| YM 8 15m don[20] dir=against hold=180m all pdrange lo0.33 | negative pre-2023 | 2602 | -4.1 | -18.4 | -13.3 | 14.4 | -0.16 / -0.74 / -0.54 | 20.4 / 6.0 |
| YM 9 5m st[14, 2.0] dir=against hold=60m day pdrange hi0.67 | negative pre-2023 | 2742 | -0.0 | -14.4 | -8.7 | 14.4 | -0.00 / -0.47 / -0.29 | 16.6 / 2.3 |
| YM 10 (diag) 15m st[14, 2.0] dir=with hold=60m day pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 1399 | 4.0 | -10.3 | -4.7 | 14.4 | 0.08 / -0.21 / -0.10 | 44.8 / 30.5 |
| GC 1 5m st[14, 2.0] dir=against hold=60m day pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 2287 | 7.3 | -17.0 | -7.5 | 24.4 | 0.25 / -0.57 / -0.25 | 65.5 / 41.2 |
| GC 2 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | negative pre-2023 | 605 | -36.8 | -61.2 | -51.6 | 24.4 | -0.40 / -0.67 / -0.56 | 144.0 / 119.7 |
| GC 3 5m st[14, 2.0] dir=against hold=180m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 1358 | 18.3 | -6.1 | 3.8 | 24.4 | 0.29 / -0.12 / 0.05 | 64.4 / 40.1 |
| GC 4 15m emax[9, 21] dir=against hold=180m all pdrange hi0.67 | positive pre-2023 | 1828 | 43.9 | 19.5 | 29.1 | 24.4 | 1.10 / 0.49 / 0.73 | 49.0 / 24.6 |
| GC 5 15m st[14, 2.0] dir=with hold=180m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 795 | 2.0 | -22.4 | -12.6 | 24.4 | 0.03 / -0.26 / -0.14 | 83.7 / 59.3 |
| GC 6 5m don[20] dir=with hold=180m day pdrange hi0.67 | negative pre-2023 | 1319 | -21.6 | -46.0 | -36.4 | 24.4 | -0.33 / -0.69 / -0.55 | 43.4 / 19.0 |
| GC 7 5m emax[9, 21] dir=with hold=180m day pdrange lo0.33 | negative pre-2023 | 1244 | -11.9 | -36.3 | -26.5 | 24.4 | -0.21 / -0.64 / -0.47 | 31.6 / 7.2 |
| GC 8 15m don[20] dir=against hold=180m day pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 780 | 13.6 | -10.7 | -1.2 | 24.4 | 0.17 / -0.13 / -0.01 | 32.6 / 8.2 |
| GC 9 (diag) 5m st[14, 2.0] dir=against hold=180m day pdrange hi0.67 | positive pre-2023 | 1200 | 35.4 | 11.1 | 20.7 | 24.4 | 0.44 / 0.14 / 0.26 | 118.7 / 94.4 |
| GC 10 (diag) 15m emax[9, 21] dir=against hold=60m all pdrange lo0.33 | negative pre-2023 | 2793 | -16.7 | -41.1 | -31.3 | 24.4 | -0.98 / -2.37 / -1.83 | 41.4 / 17.1 |
| CL 1 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | negative pre-2023 | 983 | -3.8 | -28.2 | -23.9 | 24.4 | -0.07 / -0.50 / -0.43 | 78.5 / 54.1 |
| CL 2 15m st[14, 2.0] dir=with hold=60m day pdrange hi0.67 | negative pre-2023 | 1329 | -3.7 | -28.1 | -23.9 | 24.4 | -0.08 / -0.58 / -0.49 | 43.5 / 19.2 |
| CL 3 15m don[20] dir=against hold=180m day pdrange lo0.33 | negative pre-2023 | 940 | -27.3 | -51.6 | -48.7 | 24.4 | -0.39 / -0.73 / -0.69 | 30.7 / 6.3 |
| CL 4 (diag) 15m emax[9, 21] dir=with hold=180m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 634 | 14.7 | -9.7 | -7.0 | 24.4 | 0.18 / -0.12 / -0.09 | 70.8 / 46.5 |
| CL 5 (diag) 5m emax[9, 21] dir=against hold=180m day pdrange hi0.67 | negative pre-2023 | 1181 | -0.2 | -24.5 | -20.5 | 24.4 | -0.00 / -0.27 / -0.23 | 67.0 / 42.6 |
| CL 6 (diag) 15m emax[9, 21] dir=against hold=180m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 1956 | 17.9 | -6.5 | -2.5 | 24.4 | 0.37 / -0.13 / -0.05 | 33.1 / 8.7 |
| ZN 1 (diag) 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | negative pre-2023 | 648 | -4.8 | -40.4 | -45.4 | 35.6 | -0.18 / -1.48 / -1.65 | 36.5 / 0.9 |
| ZN 2 (diag) 15m don[20] dir=against hold=180m day pdrange lo0.33 | negative pre-2023 | 824 | -12.1 | -47.7 | -52.9 | 35.6 | -0.56 / -2.12 / -2.32 | 25.3 / -10.3 |
| ZN 3 (diag) 5m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | negative pre-2023 | 1240 | -0.8 | -36.4 | -41.4 | 35.6 | -0.04 / -1.82 / -2.04 | 17.0 / -18.6 |
| BTC 1 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67 | negative pre-2023 | 30 | -387.5 | -441.9 | -409.0 | 54.4 | -1.12 / -1.26 / -1.18 | 1070.5 / 1016.2 |
| BTC 2 15m emax[9, 21] dir=with hold=60m day pdrange hi0.67 | negative pre-2023 | 53 | -17.5 | -71.8 | -38.9 | 54.4 | -0.13 / -0.52 / -0.29 | 475.1 / 420.8 |
| BTC 3 15m emax[9, 21] dir=with hold=180m all pdrange hi0.67 | negative pre-2023 | 72 | -478.1 | -532.5 | -499.7 | 54.4 | -2.28 / -2.42 / -2.34 | 417.3 / 362.9 |
| BTC 4 15m st[14, 2.0] dir=with hold=180m day pdrange hi0.67 | positive pre-2023 | 35 | 62.9 | 8.5 | 41.2 | 54.4 | 0.22 / 0.03 / 0.14 | 753.4 / 699.0 |
| BTC 5 15m st[14, 2.0] dir=against hold=180m day pdrange lo0.33 | positive pre-2023 | 82 | 210.7 | 156.3 | 189.9 | 54.4 | 0.90 / 0.65 / 0.80 | 543.9 / 489.6 |
| BTC 6 15m st[14, 2.0] dir=with hold=60m all pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 282 | 35.0 | -19.3 | 14.3 | 54.4 | 0.56 / -0.27 / 0.24 | 150.0 / 95.7 |
| BTC 7 5m st[14, 2.0] dir=with hold=180m all pdrange lo0.33 | negative pre-2023 | 357 | -24.9 | -79.2 | -45.4 | 54.4 | -0.44 / -1.36 / -0.80 | 173.0 / 118.6 |
| BTC 8 5m st[14, 2.0] dir=against hold=180m all pdrange hi0.67 | negative pre-2023 | 155 | -65.8 | -120.2 | -87.3 | 54.4 | -0.43 / -0.77 / -0.57 | 189.4 / 135.0 |
| BTC 9 5m emax[9, 21] dir=against hold=60m day pdrange hi0.67 | negative pre-2023 | 81 | -26.9 | -81.2 | -48.2 | 54.4 | -0.23 / -0.67 / -0.41 | 186.4 / 132.1 |
| BTC 10 15m emax[9, 21] dir=with hold=60m all pdrange hi0.67 | negative pre-2023 | 110 | -13.0 | -67.3 | -34.4 | 54.4 | -0.15 / -0.76 / -0.40 | 146.7 / 92.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 19 cells pass the clean rule against a replicate mean of 11.3 (p(count) = 0.03, p(top) = 0.03); CL: 3 cells pass the clean rule against a replicate mean of 3.4 (p(count) = 0.69, p(top) = 0.45); ES: 10 cells pass the clean rule against a replicate mean of 5.8 (p(count) = 0.03, p(top) = 0.03); GC: 8 cells pass the clean rule against a replicate mean of 6.0 (p(count) = 0.18, p(top) = 0.90); NQ: 20 cells pass the clean rule against a replicate mean of 15.2 (p(count) = 0.10, p(top) = 0.38); RTY: 16 cells pass the clean rule against a replicate mean of 7.2 (p(count) = 0.00, p(top) = 0.16); YM: 9 cells pass the clean rule against a replicate mean of 7.8 (p(count) = 0.39, p(top) = 0.69); ZN: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00).
- Of 60 selected cells, 3 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.31 (BTC 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67); bootstrap lower bound > 0 for 5 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 14; gate_add PASS at some share: 3 (cell-share pairs).
- Gate-3 cell YM 15m don[20] dir=against hold=180m day pdrange lo0.33: uplift +0.11/+0.13/+0.51, boot lo -0.03, plateau 0.33, 2x-slip +0.16, wd corr +0.01, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 15m emax[9, 21] dir=with hold=180m day pdrange hi0.67: uplift +0.36/+0.23/+0.13, boot lo +0.14, plateau 0.50, 2x-slip +0.29, wd corr -0.18, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC 5m emax[9, 21] dir=against hold=60m day pdrange hi0.67: uplift +0.10/+0.62/+0.15, boot lo +0.00, plateau 0.50, 2x-slip +0.13, wd corr +0.17, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 26, 'positive pre-2023': 18, 'gross-positive, cost-negative pre-2023': 16}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_1.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw1/ (`SW1_CO_all_selected_scored.csv`).

DONE SW1
