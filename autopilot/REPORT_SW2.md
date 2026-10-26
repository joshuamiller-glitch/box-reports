# REPORT SW2 - regime-gated fade sleeves: VWAP-band and RSI fades after a high or low prior-day-range day (D08 H3/H4)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 59 selected cells (+10 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.26; best pair-window standalone Sharpe +1.48.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: fade (or follow) VWAP-band 2.0 globex / 2.5 RTH crossings and RSI(14,30) cross-ins on 5/15-min bars, exact hold 60 or 180 min (no stop), same prior-day-range regime gate as SW1.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 96 cells per instrument = 2 x 3 signals x 2 directions x 2 holds x 2 sessions x 2 regimes.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         70 |        14 |               1.462 |                2 |         10 |            0 |
| CL    |      96 |         84 |         8 |               0.972 |                2 |          8 |            2 |
| ES    |      96 |         88 |        14 |               2.057 |                2 |         10 |            0 |
| GC    |      96 |         82 |         8 |               0.966 |                2 |          8 |            2 |
| NQ    |      96 |         88 |        23 |               1.494 |                2 |         10 |            0 |
| RTY   |      96 |         86 |        20 |               2.025 |                2 |         10 |            0 |
| YM    |      96 |         92 |         3 |               0.797 |                2 |          3 |            3 |
| ZN    |      96 |         68 |         0 |              -0.097 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                   14 |             6.59 |              12 |       0    |                       0.971 |            0.667 |           0.949 |     0.05 |       1.746 |                1.66  |
| NQ    |     100 |                   23 |            16.82 |              25 |       0.07 |                       1.025 |            0.937 |           1.195 |     0.33 |       1.419 |                1.919 |
| RTY   |     100 |                   20 |             8.23 |              15 |       0    |                       1.288 |            0.698 |           0.973 |     0    |       2.025 |                1.947 |
| YM    |     100 |                    3 |             8.71 |              17 |       1    |                       0.6   |            0.663 |           0.949 |     0.63 |       0.797 |                1.842 |
| GC    |     100 |                    8 |             6.9  |              13 |       0.42 |                       0.469 |            0.654 |           0.895 |     0.87 |       0.685 |                1.716 |
| CL    |     100 |                    8 |             4.42 |              10 |       0.05 |                       0.527 |            0.598 |           0.884 |     0.62 |       0.972 |                1.613 |
| ZN    |     100 |                    0 |             0.06 |               1 |       1    |                     nan     |            0.367 |           0.576 |   nan    |     nan     |                0.576 |
| BTC   |     100 |                   14 |            12.8  |              22 |       0.41 |                       0.855 |            0.788 |           1.101 |     0.31 |       1.462 |                1.952 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | 410 | 2 | 1.75 | -0.05 | 1.31 | 0.68 / 1.27 | 0.29 / -0.11 / 0.16 | 0.15 | -0.23 | 1.00 | 0.02 | 0.50 | 590 | NO |
| ES 2 | 15m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | 225 | 2 | 1.44 | -0.48 | 0.78 | 0.21 / 0.58 | 0.26 / 0.01 / -0.27 | 0.01 | 0.35 | 1.00 | -0.10 | 0.50 | 344 | NO |
| ES 3 | 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | 142 | 2 | 1.26 | 0.47 | 1.20 | 1.08 / 1.23 | 0.24 / 0.07 / 0.18 | 0.19 | -0.35 | 1.00 | 0.04 | 0.50 | 197 | NO |
| ES 4 | 5m vwz[2.5, 'rth'] dir=follow hold=60m day pdrange lo0.33 | 159 | 2 | 1.26 | -0.12 | 0.46 | -0.34 / 0.59 | 0.23 / -0.41 / -0.35 | -0.05 | 0.27 | 1.00 | -0.21 | 0.33 | 266 | NO |
| ES 5 | 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | 533 | 2 | 1.08 | -0.21 | 0.67 | 0.03 / 0.90 | 0.20 / -0.21 / -0.06 | 0.02 | 0.15 | 0.98 | -0.11 | 0.50 | 763 | NO |
| ES 6 | 5m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | 373 | 2 | 0.82 | -0.65 | 0.13 | -0.53 / -0.08 | 0.15 / -0.56 / -0.34 | -0.19 | 0.30 | 1.00 | -0.28 | 0.00 | 620 | NO |
| ES 7 | 5m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | 173 | 2 | 0.72 | 0.33 | 0.72 | 0.76 / 1.26 | 0.14 / 0.09 / 0.06 | 0.10 | -0.32 | 0.97 | -0.05 | 0.33 | 238 | NO |
| ES 8 | 15m vwz[2.0, 'globex'] dir=fade hold=60m all pdrange hi0.67 | 564 | 2 | 0.56 | -0.71 | 0.44 | 0.19 / 0.42 | 0.08 / -0.28 / 0.16 | -0.05 | 0.17 | 1.00 | -0.13 | 0.50 | 814 | NO |
| ES 9 | 5m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | 206 | 2 | 0.47 | -0.36 | 0.54 | 0.67 / 1.16 | 0.12 / -0.29 / 0.30 | 0.09 | -0.06 | 0.91 | -0.07 | 0.62 | 297 | NO |
| ES 10 | 15m vwz[2.0, 'globex'] dir=fade hold=60m day pdrange hi0.67 | 194 | 2 | 0.36 | 0.11 | 0.48 | 0.81 / 0.95 | 0.06 / -0.08 / 0.20 | 0.03 | 0.23 | 0.92 | -0.09 | 0.50 | 276 | NO |
| NQ 1 | 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | 523 | 2 | 1.42 | 0.53 | 0.42 | -0.74 / 1.78 | 0.28 / -0.46 / -0.33 | 0.03 | -0.08 | 0.83 | -0.17 | 0.83 | 839 | NO |
| NQ 2 | 15m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | 218 | 2 | 1.39 | 0.35 | 1.13 | 0.89 / 1.49 | 0.21 / -0.00 / 0.17 | 0.16 | -0.23 | 0.99 | -0.00 | 0.50 | 315 | NO |
| NQ 3 | 5m vwz[2.5, 'rth'] dir=follow hold=60m day pdrange lo0.33 | 153 | 2 | 1.28 | -0.04 | 0.86 | 0.51 / 1.37 | 0.15 / 0.05 / 0.22 | 0.13 | 0.16 | 0.94 | -0.05 | 0.17 | 221 | NO |
| NQ 4 | 15m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | 403 | 2 | 1.12 | 0.24 | 0.53 | -0.31 / 1.53 | 0.21 / -0.33 / -0.10 | 0.05 | -0.11 | 0.88 | -0.14 | 0.67 | 644 | NO |
| NQ 5 | 5m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | 201 | 2 | 1.07 | 0.43 | 0.65 | 0.01 / 1.36 | 0.26 / -0.15 / -0.19 | 0.10 | 0.45 | 0.93 | -0.08 | 0.12 | 319 | NO |
| NQ 6 | 5m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | 407 | 2 | 1.02 | -0.13 | 0.95 | 1.00 / 1.25 | 0.11 / -0.13 / 0.48 | 0.13 | -0.17 | 0.98 | -0.05 | 0.00 | 591 | NO |
| NQ 7 | 15m rsi[14, 30] dir=fade hold=180m day pdrange lo0.33 | 155 | 2 | 0.85 | -0.02 | -0.05 | -1.69 / 1.38 | 0.20 / -0.67 / 0.03 | 0.03 | 0.19 | 0.58 | -0.15 | 0.38 | 221 | NO |
| NQ 8 | 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | 266 | 2 | 0.74 | 0.40 | 0.51 | 0.16 / 1.36 | 0.17 / -0.49 / 0.11 | 0.07 | -0.18 | 0.86 | -0.11 | 0.62 | 445 | NO |
| NQ 9 | 15m vwz[2.5, 'rth'] dir=fade hold=60m all pdrange hi0.67 | 194 | 2 | 0.72 | 0.30 | 0.97 | 1.36 / 1.50 | 0.08 / 0.04 / 0.33 | 0.11 | -0.33 | 0.98 | -0.04 | 0.50 | 302 | NO |
| NQ 10 | 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | 140 | 2 | 0.65 | 0.49 | 0.52 | 0.30 / 1.40 | 0.13 / -0.11 / -0.03 | 0.06 | -0.13 | 0.84 | -0.10 | 0.67 | 209 | NO |
| RTY 1 | 5m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | 523 | 2 | 2.03 | 0.23 | 0.75 | -1.03 / 1.07 | 0.38 / -0.78 / 0.05 | 0.10 | -0.43 | 0.99 | -0.07 | 0.50 | 795 | NO |
| RTY 2 | 5m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | 196 | 2 | 1.85 | 0.24 | 1.16 | -0.08 / 1.49 | 0.35 / -0.23 / 0.05 | 0.19 | -0.46 | 0.98 | 0.04 | 0.50 | 303 | NO |
| RTY 3 | 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | 312 | 2 | 1.56 | 0.12 | 0.71 | -1.12 / 0.57 | 0.34 / -0.55 / 0.01 | 0.10 | -0.40 | 1.00 | -0.02 | 0.50 | 494 | NO |
| RTY 4 | 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | 284 | 2 | 1.48 | 0.58 | 0.90 | 0.22 / 0.87 | 0.31 / -0.23 / 0.21 | 0.18 | -0.18 | 1.00 | 0.01 | 0.50 | 434 | NO |
| RTY 5 | 15m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | 130 | 2 | 1.40 | 0.10 | 0.68 | 0.14 / 1.25 | 0.27 / -0.15 / -0.07 | 0.13 | -0.36 | 0.94 | -0.09 | 0.88 | 205 | NO |
| RTY 6 | 5m rsi[14, 30] dir=fade hold=60m all pdrange hi0.67 | 794 | 2 | 1.01 | -0.16 | 0.37 | -0.90 / 0.67 | 0.24 / -0.51 / 0.04 | -0.01 | -0.41 | 1.00 | -0.08 | 0.38 | 1221 | NO |
| RTY 7 | 15m vwz[2.0, 'globex'] dir=follow hold=60m day pdrange lo0.33 | 145 | 2 | 0.99 | -1.18 | 0.61 | 0.00 / 0.63 | 0.17 / 0.35 / -0.26 | 0.05 | -0.32 | 1.00 | -0.09 | 0.50 | 249 | NO |
| RTY 8 | 15m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | 416 | 2 | 0.92 | -0.08 | 0.46 | -0.28 / 0.89 | 0.14 / -0.29 / 0.09 | 0.02 | -0.26 | 0.95 | -0.11 | 0.17 | 625 | NO |
| RTY 9 | 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | 554 | 2 | 0.87 | -0.42 | 0.37 | -0.29 / 1.04 | 0.15 / -0.54 / 0.15 | -0.00 | -0.45 | 0.98 | -0.14 | 0.33 | 830 | NO |
| RTY 10 | 5m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | 158 | 2 | 0.78 | 0.15 | 0.13 | -0.87 / 1.25 | 0.11 / -0.37 / -0.12 | -0.03 | -0.14 | 0.75 | -0.20 | 0.00 | 237 | NO |
| YM 1 | 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | 160 | 2 | 0.80 | 0.29 | 0.05 | -1.88 / 1.27 | 0.14 / -0.26 / -0.26 | -0.02 | -0.29 | 0.64 | -0.13 | 0.00 | 230 | NO |
| YM 2 | 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | 344 | 2 | 0.56 | -0.01 | 0.26 | -0.48 / 0.80 | 0.14 / -0.14 / 0.03 | 0.05 | -0.08 | 0.90 | -0.07 | 0.25 | 507 | NO |
| YM 3 | 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | 294 | 2 | 0.44 | 0.12 | -0.12 | -1.13 / 1.26 | 0.07 / -0.65 / 0.05 | -0.07 | 0.26 | 0.66 | -0.22 | 0.00 | 440 | NO |
| YM 4 (diag) | 15m vwz[2.5, 'rth'] dir=follow hold=60m day pdrange lo0.33 | 102 | 1 | 0.79 | -0.42 | 0.60 | 0.39 / 1.00 | 0.11 / -0.15 / -0.13 | 0.01 | 0.16 | 0.97 | -0.16 | 0.33 | 150 | diag |
| YM 5 (diag) | 15m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | 457 | 1 | 0.54 | -0.38 | -0.24 | -1.42 / 1.37 | 0.09 / -0.61 / -0.20 | -0.12 | -0.10 | 0.57 | -0.26 | 0.00 | 687 | diag |
| YM 6 (diag) | 15m vwz[2.5, 'rth'] dir=fade hold=180m all pdrange hi0.67 | 194 | 1 | 0.45 | -0.20 | 0.74 | 1.27 / 1.36 | 0.06 / 0.06 / 0.29 | 0.09 | 0.39 | 0.95 | -0.06 | 0.17 | 312 | diag |
| GC 1 | 15m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | 117 | 2 | 0.68 | -0.36 | -0.19 | -0.78 / 1.32 | 0.21 / -1.31 / -0.43 | -0.19 | -0.03 | 0.51 | -0.54 | 0.00 | 201 | NO |
| GC 2 | 5m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | 144 | 2 | 0.64 | -0.21 | 0.16 | -0.06 / 1.16 | 0.18 / -1.07 / -0.14 | -0.09 | 0.05 | 0.82 | -0.43 | 0.00 | 241 | NO |
| GC 3 | 5m rsi[14, 30] dir=fade hold=60m day pdrange lo0.33 | 238 | 2 | 0.50 | -1.36 | 0.30 | 0.28 / 1.30 | 0.06 / 0.06 / 0.08 | 0.02 | -0.62 | 0.94 | -0.22 | 0.25 | 333 | NO |
| GC 4 | 15m vwz[2.0, 'globex'] dir=fade hold=60m day pdrange lo0.33 | 122 | 2 | 0.43 | -0.46 | 0.00 | -0.09 / 1.09 | 0.01 / -0.47 / -0.13 | -0.11 | -0.64 | 0.84 | -0.37 | 0.00 | 162 | NO |
| GC 5 | 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | 110 | 2 | 0.42 | -0.23 | 0.45 | 0.54 / 1.28 | 0.15 / 0.59 / -0.55 | 0.07 | -0.10 | 0.86 | -0.20 | 0.50 | 188 | NO |
| GC 6 | 15m vwz[2.5, 'rth'] dir=fade hold=60m all pdrange hi0.67 | 185 | 2 | 0.40 | 0.06 | 0.26 | 0.32 / 1.14 | 0.03 / -0.44 / -0.31 | -0.13 | 0.05 | 0.79 | -0.62 | 0.00 | 294 | NO |
| GC 7 | 15m rsi[14, 30] dir=fade hold=60m day pdrange lo0.33 | 131 | 2 | 0.40 | -0.93 | 0.37 | 0.51 / 1.36 | 0.00 / -0.14 / 0.58 | 0.06 | -0.62 | 0.87 | -0.19 | 0.75 | 184 | NO |
| GC 8 | 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | 311 | 2 | 0.27 | -0.01 | -0.09 | -0.32 / 1.36 | 0.08 / -0.33 / -0.76 | -0.20 | 0.16 | 0.62 | -0.51 | 0.00 | 529 | NO |
| GC 9 (diag) | 15m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange lo0.33 | 26 | 1 | 0.97 | -0.23 | 0.08 | -0.55 / 1.37 | 0.14 / 0.45 / -0.90 | -0.11 | -0.16 | 0.65 | -0.46 | 0.00 | 37 S | diag |
| GC 10 (diag) | 15m rsi[14, 30] dir=fade hold=180m day pdrange lo0.33 | 100 | 1 | 0.67 | -0.21 | 0.49 | 0.57 / 1.44 | 0.08 / -0.28 / 0.50 | 0.11 | -0.60 | 0.85 | -0.21 | 0.38 | 133 | diag |
| CL 1 | 5m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange lo0.33 | 169 | 2 | 0.97 | -0.61 | 0.78 | 0.32 / 1.12 | 0.15 / -0.19 / 0.14 | 0.05 | 0.27 | 1.00 | -0.05 | 0.33 | 216 | NO |
| CL 2 | 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange lo0.33 | 129 | 2 | 0.80 | -0.57 | 0.46 | -0.88 / 1.18 | 0.09 / -0.24 / 0.05 | -0.01 | 0.16 | 0.97 | -0.11 | 0.00 | 160 | NO |
| CL 3 | 15m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange lo0.33 | 484 | 2 | 0.70 | -1.43 | 0.36 | -0.79 / 0.57 | 0.08 / -0.10 / -0.09 | -0.10 | 0.04 | 0.98 | -0.15 | 0.17 | 623 | NO |
| CL 4 | 15m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | 131 | 2 | 0.63 | -0.67 | 0.54 | 0.67 / 0.67 | 0.09 / -0.13 / 0.57 | 0.10 | -0.24 | 0.98 | -0.25 | 0.25 | 236 | NO |
| CL 5 | 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | 239 | 2 | 0.44 | -0.24 | 0.14 | 0.01 / 0.93 | 0.08 / -0.28 / -0.19 | -0.13 | -0.50 | 0.95 | -0.37 | 0.00 | 465 | NO |
| CL 6 | 5m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | 135 | 2 | 0.26 | -0.11 | 0.13 | 0.05 / 1.22 | 0.07 / 0.08 / 0.16 | 0.05 | -0.46 | 0.72 | -0.18 | 0.17 | 220 | NO |
| CL 7 | 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | 504 | 2 | 0.25 | -0.49 | 0.58 | 0.86 / 0.94 | 0.07 / 0.18 / 0.45 | 0.07 | -0.30 | 0.98 | -0.11 | 0.50 | 907 | NO |
| CL 8 | 5m vwz[2.5, 'rth'] dir=fade hold=60m day pdrange lo0.33 | 124 | 2 | 0.16 | -1.28 | 0.08 | -0.09 / 0.53 | 0.04 / -0.36 / 0.24 | -0.04 | 0.08 | 0.99 | -0.14 | 0.17 | 157 | NO |
| CL 9 (diag) | 5m vwz[2.5, 'rth'] dir=fade hold=180m day pdrange lo0.33 | 103 | 1 | 0.94 | -0.99 | 0.47 | -0.65 / 0.82 | 0.21 / -0.35 / -0.00 | 0.05 | 0.21 | 0.97 | -0.08 | 0.33 | 129 | diag |
| CL 10 (diag) | 15m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | 94 | 2 | 0.85 | -0.27 | 0.46 | 0.41 / 1.41 | 0.13 / -0.06 / 0.47 | 0.14 | -0.29 | 0.89 | -0.19 | 0.25 | 163 | diag |
| ZN 1 (diag) | 5m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange lo0.33 | 73 | 1 | -0.10 | -0.45 | -0.85 | -2.13 / -1.79 | -0.09 / -0.77 / -0.14 | -0.39 | -0.17 | 0.99 | -0.37 | 0.00 | 125 | diag |
| ZN 2 (diag) | 15m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange hi0.67 | 29 | 1 | -0.12 | -1.16 | -0.37 | -1.07 / -0.50 | -0.03 / -0.20 / -0.14 | -0.18 | -0.54 | 0.97 | -0.25 | 0.00 | 44 S | diag |
| ZN 3 (diag) | 5m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange hi0.67 | 50 | 1 | -0.26 | -1.26 | -0.89 | -2.48 / -0.78 | -0.04 / -0.21 / -0.43 | -0.30 | 0.40 | 0.95 | -0.32 | 0.00 | 87 S | diag |
| BTC 1 | 5m rsi[14, 30] dir=follow hold=60m all pdrange lo0.33 | 729 | 2 | 1.46 | 1.56 | 1.48 | 1.45 / 0.49 | 0.24 / 1.03 / -0.17 | 0.18 | 0.05 | 1.00 | 0.07 | 0.62 | 1152 | NO |
| BTC 2 | 5m rsi[14, 30] dir=follow hold=60m day pdrange lo0.33 | 299 | 2 | 1.15 | 1.26 | 0.44 | -0.86 / 0.79 | 0.19 / -0.24 / -0.23 | 0.00 | 0.12 | 0.93 | -0.14 | 0.50 | 468 | NO |
| BTC 3 | 15m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | 140 | 2 | 1.10 | -0.86 | 0.55 | -0.59 / 1.26 | 0.14 / -0.46 / 0.13 | 0.03 | -0.40 | 0.95 | -0.12 | 0.25 | 226 | NO |
| BTC 4 | 5m rsi[14, 30] dir=follow hold=180m all pdrange lo0.33 | 483 | 2 | 0.94 | 1.74 | 0.53 | 0.18 / 1.56 | 0.15 / 0.84 / -0.32 | 0.07 | 0.32 | 0.93 | -0.10 | 0.75 | 771 | NO |
| BTC 5 | 15m rsi[14, 30] dir=follow hold=180m day pdrange lo0.33 | 106 | 2 | 0.81 | 0.98 | 0.18 | -0.57 / 1.38 | 0.17 / -0.48 / 0.02 | 0.03 | 0.32 | 0.73 | -0.18 | 0.12 | 170 | NO |
| BTC 6 | 5m rsi[14, 30] dir=follow hold=180m day pdrange lo0.33 | 176 | 2 | 0.70 | 1.19 | -0.25 | -1.55 / 1.47 | 0.11 / -0.62 / -0.18 | -0.08 | 0.37 | 0.52 | -0.26 | 0.00 | 275 | NO |
| BTC 7 | 5m vwz[2.5, 'rth'] dir=fade hold=180m all pdrange lo0.33 | 197 | 2 | 0.70 | -0.96 | 0.57 | 0.36 / 1.10 | 0.09 / -0.35 / 0.12 | 0.01 | -0.07 | 0.94 | -0.17 | 0.00 | 313 | NO |
| BTC 8 | 5m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange hi0.67 | 288 | 2 | 0.66 | -0.68 | -0.38 | -2.18 / 1.02 | 0.10 / -0.53 / -0.42 | -0.15 | -0.40 | 0.60 | -0.30 | 0.00 | 453 | NO |
| BTC 9 | 15m rsi[14, 30] dir=follow hold=180m all pdrange lo0.33 | 261 | 2 | 0.65 | 0.71 | 0.42 | 0.11 / 1.10 | 0.12 / 0.23 / 0.06 | 0.06 | 0.29 | 0.89 | -0.11 | 0.38 | 416 | NO |
| BTC 10 | 5m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | 483 | 2 | 0.39 | 1.30 | -0.21 | -1.33 / 1.26 | 0.04 / -0.59 / 0.10 | -0.08 | -0.32 | 0.55 | -0.23 | 0.00 | 740 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 59 |
| diagnostic cells read | 10 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 51 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 5 |
| standalone pair-window Sharpe above own random-entry null p95 | 34 |
| worst-decile corr <= +0.30 | 62 |
| plateau >= 0.75 | 4 |
| all-in uplift at 2x slippage >= +0.10 | 13 |
| small-sample (<100 trades pair window) | 3 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 5m rsi[14, 30] dir=follow hold=60m all pdrange lo0.33 | clean | 1.48 | 3.17 | -94200 | -77284 | 206950 | -129171 | 6.47 | 37.1 | 1.70 | -85164 | 231862 | -89945 |
| BTC 5m rsi[14, 30] dir=follow hold=60m all pdrange lo0.33 | H1 | 3.43 | 9.51 | -100410 | -79562 | 141093 | -125332 | 7.77 | 25.0 | 3.86 | -70200 | 133835 | -78287 |
| BTC 5m rsi[14, 30] dir=follow hold=60m all pdrange lo0.33 | H2 | -1.04 | -1.22 | -124735 | -94480 | 463506 | -170923 | -0.50 | 41.7 | 2.13 | -82356 | 252766 | -85173 |
| BTC 5m rsi[14, 30] dir=follow hold=60m all pdrange lo0.33 | all | 1.48 | 3.04 | -107154 | -84051 | 463506 | -170923 | 4.76 | 36.3 | 2.11 | -83776 | 252766 | -89945 |
| CL 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | clean | 0.30 | 0.45 | -135550 | -101252 | 519222 | -266171 | 0.52 | 36.2 | 1.53 | -80028 | 265784 | -88979 |
| CL 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | H1 | 1.67 | 5.39 | -34292 | -31298 | 94432 | -39111 | 2.89 | 35.7 | 3.01 | -84052 | 149865 | -84755 |
| CL 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | H2 | 0.89 | 1.53 | -425291 | -290170 | 707707 | -504587 | 1.25 | 50.0 | 2.75 | -83452 | 246523 | -86527 |
| CL 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | all | 0.58 | 0.97 | -220428 | -152697 | 707707 | -504587 | 2.02 | 39.3 | 2.04 | -81990 | 265784 | -88979 |
| ES 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | clean | 1.25 | 2.50 | -112406 | -86038 | 425660 | -151248 | 2.67 | 26.7 | 1.70 | -81910 | 280086 | -95443 |
| ES 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | H1 | 0.72 | 1.19 | -130751 | -100304 | 318203 | -206637 | 0.60 | 17.9 | 2.89 | -77610 | 178960 | -78287 |
| ES 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | H2 | 1.46 | 2.80 | -90443 | -75128 | 326033 | -102483 | 1.14 | 19.4 | 2.48 | -85253 | 217425 | -85645 |
| ES 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | all | 1.20 | 2.26 | -117995 | -88732 | 638679 | -206637 | 2.66 | 23.8 | 2.07 | -82865 | 280086 | -95443 |
| GC 15m rsi[14, 30] dir=fade hold=60m day pdrange lo0.33 | clean | 0.24 | 0.37 | -140298 | -115451 | 583973 | -179065 | 0.38 | 28.6 | 1.46 | -82941 | 292373 | -91660 |
| GC 15m rsi[14, 30] dir=fade hold=60m day pdrange lo0.33 | H1 | -0.17 | -0.27 | -164726 | -160617 | 624092 | -170538 | -0.10 | 32.1 | 2.69 | -77610 | 137633 | -78287 |
| GC 15m rsi[14, 30] dir=fade hold=60m day pdrange lo0.33 | H2 | 0.83 | 1.66 | -318722 | -242644 | 502885 | -373232 | 1.46 | 16.7 | 2.88 | -78400 | 227738 | -79653 |
| GC 15m rsi[14, 30] dir=fade hold=60m day pdrange lo0.33 | all | 0.37 | 0.64 | -212316 | -164088 | 861463 | -373232 | 1.03 | 26.2 | 1.96 | -81519 | 292373 | -91660 |
| NQ 15m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | clean | 1.32 | 2.96 | -86889 | -76159 | 279484 | -117928 | 4.29 | 26.7 | 1.67 | -90606 | 273743 | -100527 |
| NQ 15m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | H1 | 0.28 | 0.48 | -153652 | -131409 | 334496 | -154064 | 0.27 | 32.1 | 2.83 | -67403 | 193424 | -72683 |
| NQ 15m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | H2 | 1.42 | 4.43 | -70695 | -59531 | 131881 | -84629 | 3.97 | 25.0 | 2.47 | -77464 | 190335 | -82524 |
| NQ 15m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | all | 1.13 | 2.46 | -103183 | -85457 | 504003 | -154064 | 3.60 | 27.4 | 2.03 | -86945 | 273743 | -100527 |
| RTY 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | clean | 1.48 | 2.67 | -123318 | -86418 | 347089 | -195076 | 3.86 | 29.5 | 1.77 | -79766 | 257085 | -88247 |
| RTY 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | H1 | -0.50 | -0.67 | -137487 | -122155 | 296760 | -174476 | -0.38 | 32.1 | 2.60 | -76847 | 177940 | -82152 |
| RTY 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | H2 | 0.55 | 0.92 | -231105 | -163907 | 374289 | -235376 | 0.75 | 22.2 | 2.50 | -80085 | 217425 | -82755 |
| RTY 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | all | 0.90 | 1.50 | -163993 | -116432 | 451062 | -235376 | 3.35 | 28.6 | 2.07 | -80102 | 257085 | -88247 |
| YM 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | clean | 0.56 | 0.76 | -144752 | -97636 | 533999 | -375613 | 0.94 | 29.5 | 1.60 | -79342 | 285463 | -86200 |
| YM 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | H1 | -0.49 | -0.67 | -105425 | -89564 | 305309 | -106389 | -0.28 | 21.4 | 2.69 | -81315 | 147924 | -88498 |
| YM 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | H2 | -0.46 | -0.63 | -88770 | -68868 | 186225 | -113519 | -0.44 | 41.7 | 2.32 | -79333 | 216152 | -82524 |
| YM 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | all | 0.26 | 0.36 | -134602 | -94002 | 533999 | -375613 | 0.63 | 31.0 | 1.93 | -80446 | 285463 | -88498 |
| ZN 15m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange hi0.67 (diag) | clean | -0.12 | -0.18 | -155995 | -110540 | 742279 | -313252 | -0.15 | 14.3 | 1.43 | -84226 | 273043 | -114815 |
| ZN 15m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange hi0.67 (diag) | H1 | -2.34 | -2.26 | -88077 | -79509 | 238526 | -96646 | -0.97 | 10.7 | 2.63 | -77610 | 164187 | -78287 |
| ZN 15m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange hi0.67 (diag) | H2 | -0.54 | -0.68 | -136400 | -92959 | 165195 | -165195 | -0.73 | 13.9 | 2.16 | -81089 | 217425 | -82524 |
| ZN 15m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange hi0.67 (diag) | all | -0.37 | -0.51 | -145046 | -106281 | 850479 | -313252 | -0.55 | 13.7 | 1.77 | -82880 | 273043 | -114815 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | -11.0 | 1.5 | 18.5 | 30.0 | 0.7 / 22.6 | -2.8 / 12.9 | NO |
| NQ 15m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | -9.7 | -8.1 | 11.6 | 33.4 | -9.0 / 6.8 | 3.5 / 31.7 | NO |
| RTY 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | -13.1 | 14.3 | 24.9 | 26.1 | 13.6 / 27.0 | 10.1 / 14.9 | NO |
| YM 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | -26.2 | 15.0 | 25.6 | 24.9 | 17.9 / 26.3 | 10.4 / 22.8 | NO |
| GC 15m rsi[14, 30] dir=fade hold=60m day pdrange lo0.33 | -20.1 | 2.1 | 18.4 | 23.4 | 1.3 / 12.0 | 30.0 / 30.0 | NO |
| CL 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | -14.1 | -0.1 | 15.8 | 17.8 | 15.0 / 26.3 | 16.2 / 17.5 | NO |
| ZN 15m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange hi0.67 (diag) | -35.2 | -58.1 | 19.7 | 13.9 | -59.4 / 14.5 | 30.0 / 30.0 | NO |
| BTC 5m rsi[14, 30] dir=follow hold=60m all pdrange lo0.33 | -5.4 | 6.6 | 17.2 | 26.7 | 10.6 / 16.9 | 30.0 / 35.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 1736 | 26.4 | -2.9 | 10.8 | 29.4 | 0.43 / -0.05 / 0.18 | 157.7 / 128.3 |
| ES 2 15m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 772 | 14.5 | -14.9 | -2.5 | 29.4 | 0.48 / -0.48 / -0.08 | 87.1 / 57.7 |
| ES 3 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | positive pre-2023 | 451 | 108.8 | 79.5 | 93.1 | 29.4 | 0.64 / 0.47 / 0.55 | 269.0 / 239.7 |
| ES 4 5m vwz[2.5, 'rth'] dir=follow hold=60m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 691 | 24.2 | -5.2 | 7.5 | 29.4 | 0.56 / -0.12 / 0.17 | 123.7 / 94.4 |
| ES 5 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 2371 | 19.6 | -9.8 | 4.1 | 29.4 | 0.41 / -0.21 / 0.09 | 95.7 / 66.3 |
| ES 6 5m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 1461 | 13.1 | -16.2 | -3.7 | 29.4 | 0.54 / -0.65 / -0.15 | 57.0 / 27.6 |
| ES 7 5m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | positive pre-2023 | 642 | 78.7 | 49.4 | 63.1 | 29.4 | 0.53 / 0.33 / 0.43 | 173.3 / 143.9 |
| ES 8 15m vwz[2.0, 'globex'] dir=fade hold=60m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 2363 | 5.9 | -23.5 | -9.8 | 29.4 | 0.18 / -0.71 / -0.29 | 55.6 / 26.2 |
| ES 9 5m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | negative pre-2023 | 881 | -17.3 | -46.7 | -32.9 | 29.4 | -0.13 / -0.36 / -0.25 | 117.1 / 87.7 |
| ES 10 15m vwz[2.0, 'globex'] dir=fade hold=60m day pdrange hi0.67 | positive pre-2023 | 729 | 38.8 | 9.4 | 23.2 | 29.4 | 0.44 / 0.11 / 0.26 | 72.9 / 43.6 |
| NQ 1 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | positive pre-2023 | 2609 | 53.0 | 38.7 | 47.0 | 14.4 | 0.73 / 0.53 / 0.65 | 191.1 / 176.7 |
| NQ 2 15m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | positive pre-2023 | 783 | 33.6 | 19.2 | 27.2 | 14.4 | 0.61 / 0.35 / 0.50 | 147.8 / 133.4 |
| NQ 3 5m vwz[2.5, 'rth'] dir=follow hold=60m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 593 | 10.7 | -3.7 | 4.3 | 14.4 | 0.11 / -0.04 / 0.05 | 190.7 / 176.3 |
| NQ 4 15m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | positive pre-2023 | 1933 | 35.7 | 21.4 | 29.7 | 14.4 | 0.39 / 0.24 / 0.33 | 170.9 / 156.6 |
| NQ 5 5m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | positive pre-2023 | 978 | 95.3 | 80.9 | 89.2 | 14.4 | 0.51 / 0.43 / 0.48 | 442.0 / 427.6 |
| NQ 6 5m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 1570 | 8.7 | -5.6 | 2.3 | 14.4 | 0.21 / -0.13 / 0.05 | 71.2 / 56.8 |
| NQ 7 15m rsi[14, 30] dir=fade hold=180m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 664 | 10.9 | -3.5 | 4.5 | 14.4 | 0.07 / -0.02 / 0.03 | 232.9 / 218.5 |
| NQ 8 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | positive pre-2023 | 1368 | 54.5 | 40.1 | 48.4 | 14.4 | 0.54 / 0.40 / 0.48 | 166.6 / 152.2 |
| NQ 9 15m vwz[2.5, 'rth'] dir=fade hold=60m all pdrange hi0.67 | positive pre-2023 | 926 | 37.7 | 23.4 | 31.6 | 14.4 | 0.48 / 0.30 / 0.40 | 114.6 / 100.3 |
| NQ 10 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | positive pre-2023 | 531 | 129.7 | 115.4 | 123.7 | 14.4 | 0.55 / 0.49 / 0.52 | 301.1 / 286.7 |
| RTY 1 5m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | positive pre-2023 | 1295 | 25.9 | 11.5 | 14.3 | 14.4 | 0.52 / 0.23 / 0.29 | 97.4 / 83.0 |
| RTY 2 5m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | positive pre-2023 | 472 | 38.3 | 23.9 | 26.6 | 14.4 | 0.38 / 0.24 / 0.26 | 223.7 / 209.3 |
| RTY 3 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | positive pre-2023 | 791 | 20.3 | 6.0 | 8.8 | 14.4 | 0.40 / 0.12 / 0.17 | 91.5 / 77.2 |
| RTY 4 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | positive pre-2023 | 692 | 53.9 | 39.5 | 42.3 | 14.4 | 0.79 / 0.58 / 0.62 | 91.0 / 76.6 |
| RTY 5 15m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | positive pre-2023 | 325 | 25.1 | 10.8 | 13.5 | 14.4 | 0.24 / 0.10 / 0.13 | 134.9 / 120.5 |
| RTY 6 5m rsi[14, 30] dir=fade hold=60m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 1979 | 10.9 | -3.5 | -0.7 | 14.4 | 0.49 / -0.16 / -0.03 | 33.8 / 19.5 |
| RTY 7 15m vwz[2.0, 'globex'] dir=follow hold=60m day pdrange lo0.33 | negative pre-2023 | 421 | -43.4 | -57.8 | -56.4 | 14.4 | -0.90 / -1.18 / -1.16 | 61.8 / 47.5 |
| RTY 8 15m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 956 | 10.3 | -4.1 | -1.4 | 14.4 | 0.21 / -0.08 / -0.03 | 54.6 / 40.2 |
| RTY 9 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | negative pre-2023 | 1297 | -3.3 | -17.7 | -15.1 | 14.4 | -0.08 / -0.42 / -0.36 | 41.2 / 26.9 |
| RTY 10 5m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | positive pre-2023 | 372 | 31.5 | 17.1 | 19.7 | 14.4 | 0.27 / 0.15 / 0.17 | 85.7 / 71.3 |
| YM 1 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | positive pre-2023 | 517 | 52.5 | 38.1 | 43.6 | 14.4 | 0.40 / 0.29 / 0.33 | 107.8 / 93.5 |
| YM 2 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 1585 | 13.7 | -0.6 | 5.0 | 14.4 | 0.31 / -0.01 / 0.11 | 49.1 / 34.7 |
| YM 3 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | positive pre-2023 | 1327 | 22.0 | 7.6 | 13.3 | 14.4 | 0.34 / 0.12 / 0.20 | 46.9 / 32.5 |
| YM 4 (diag) 15m vwz[2.5, 'rth'] dir=follow hold=60m day pdrange lo0.33 | negative pre-2023 | 333 | -9.9 | -24.3 | -19.3 | 14.4 | -0.17 / -0.42 / -0.34 | 68.4 / 54.1 |
| YM 5 (diag) 15m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | negative pre-2023 | 1884 | -4.0 | -18.4 | -12.8 | 14.4 | -0.08 / -0.38 / -0.27 | 38.3 / 23.9 |
| YM 6 (diag) 15m vwz[2.5, 'rth'] dir=fade hold=180m all pdrange hi0.67 | negative pre-2023 | 750 | -0.3 | -14.7 | -9.1 | 14.4 | -0.00 / -0.20 / -0.12 | 51.1 / 36.8 |
| GC 1 15m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | negative pre-2023 | 434 | -25.8 | -50.2 | -40.8 | 24.4 | -0.18 / -0.36 / -0.29 | 124.9 / 100.5 |
| GC 2 5m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 565 | 1.6 | -22.8 | -13.5 | 24.4 | 0.01 / -0.21 / -0.12 | 102.5 / 78.1 |
| GC 3 5m rsi[14, 30] dir=fade hold=60m day pdrange lo0.33 | negative pre-2023 | 1477 | -28.2 | -52.5 | -42.7 | 24.4 | -0.73 / -1.36 / -1.10 | 50.6 / 26.3 |
| GC 4 15m vwz[2.0, 'globex'] dir=fade hold=60m day pdrange lo0.33 | negative pre-2023 | 618 | -3.8 | -28.2 | -18.6 | 24.4 | -0.05 / -0.46 / -0.30 | 37.5 / 13.1 |
| GC 5 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | negative pre-2023 | 419 | -6.0 | -30.4 | -21.0 | 24.4 | -0.05 / -0.23 / -0.16 | 84.1 / 59.7 |
| GC 6 15m vwz[2.5, 'rth'] dir=fade hold=60m all pdrange hi0.67 | positive pre-2023 | 566 | 28.1 | 3.8 | 13.3 | 24.4 | 0.44 / 0.06 / 0.21 | 44.9 / 20.6 |
| GC 7 15m rsi[14, 30] dir=fade hold=60m day pdrange lo0.33 | negative pre-2023 | 861 | -21.6 | -46.0 | -35.9 | 24.4 | -0.43 / -0.93 / -0.73 | 46.0 / 21.7 |
| GC 8 15m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 1092 | 23.4 | -0.9 | 8.6 | 24.4 | 0.33 / -0.01 / 0.12 | 49.3 / 24.9 |
| GC 9 (diag) 15m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange lo0.33 | negative pre-2023 | 161 | -15.3 | -39.7 | -29.5 | 24.4 | -0.09 / -0.23 / -0.17 | 232.3 / 207.9 |
| GC 10 (diag) 15m rsi[14, 30] dir=fade hold=180m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 609 | 6.1 | -18.3 | -8.4 | 24.4 | 0.07 / -0.21 / -0.10 | 98.6 / 74.2 |
| CL 1 5m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange lo0.33 | negative pre-2023 | 687 | -21.2 | -45.6 | -42.5 | 24.4 | -0.28 / -0.61 / -0.57 | 94.5 / 70.1 |
| CL 2 15m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange lo0.33 | negative pre-2023 | 518 | -23.3 | -47.7 | -44.6 | 24.4 | -0.28 / -0.57 / -0.53 | 91.3 / 67.0 |
| CL 3 15m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange lo0.33 | negative pre-2023 | 1726 | -25.3 | -49.6 | -46.8 | 24.4 | -0.72 / -1.43 / -1.35 | 47.0 / 22.6 |
| CL 4 15m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | negative pre-2023 | 825 | -19.8 | -44.1 | -40.2 | 24.4 | -0.30 / -0.67 / -0.61 | 54.7 / 30.4 |
| CL 5 5m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 1478 | 12.8 | -11.5 | -7.6 | 24.4 | 0.27 / -0.24 / -0.16 | 41.7 / 17.3 |
| CL 6 5m vwz[2.0, 'globex'] dir=fade hold=180m day pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 713 | 12.2 | -12.1 | -8.1 | 24.4 | 0.11 / -0.11 / -0.07 | 55.0 / 30.6 |
| CL 7 5m vwz[2.0, 'globex'] dir=fade hold=180m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 2498 | 3.3 | -21.0 | -17.2 | 24.4 | 0.08 / -0.49 / -0.40 | 36.1 / 11.7 |
| CL 8 5m vwz[2.5, 'rth'] dir=fade hold=60m day pdrange lo0.33 | negative pre-2023 | 524 | -51.5 | -75.8 | -73.2 | 24.4 | -0.88 / -1.28 / -1.24 | 32.8 / 8.5 |
| CL 9 (diag) 5m vwz[2.5, 'rth'] dir=fade hold=180m day pdrange lo0.33 | negative pre-2023 | 408 | -91.9 | -116.3 | -113.5 | 24.4 | -0.78 / -0.99 / -0.96 | 109.6 / 85.3 |
| CL 10 (diag) 15m rsi[14, 30] dir=fade hold=180m day pdrange hi0.67 | negative pre-2023 | 567 | -9.3 | -33.7 | -29.7 | 24.4 | -0.07 / -0.27 / -0.24 | 111.9 / 87.6 |
| ZN 1 (diag) 5m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange lo0.33 | gross-positive, cost-negative pre-2023 | 240 | 16.7 | -18.9 | -24.2 | 35.6 | 0.40 / -0.45 / -0.57 | 27.4 / -8.2 |
| ZN 2 (diag) 15m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange hi0.67 | negative pre-2023 | 201 | -25.5 | -61.1 | -66.1 | 35.6 | -0.52 / -1.16 / -1.24 | 28.6 / -7.1 |
| ZN 3 (diag) 5m vwz[2.5, 'rth'] dir=follow hold=180m day pdrange hi0.67 | negative pre-2023 | 385 | -13.4 | -49.0 | -54.0 | 35.6 | -0.36 / -1.26 / -1.37 | 26.9 / -8.7 |
| BTC 1 5m rsi[14, 30] dir=follow hold=60m all pdrange lo0.33 | positive pre-2023 | 285 | 183.6 | 129.2 | 162.8 | 54.4 | 2.16 / 1.56 / 1.94 | 228.1 / 173.7 |
| BTC 2 5m rsi[14, 30] dir=follow hold=60m day pdrange lo0.33 | positive pre-2023 | 127 | 252.2 | 197.8 | 231.7 | 54.4 | 1.59 / 1.26 / 1.47 | 325.2 / 270.8 |
| BTC 3 15m rsi[14, 30] dir=fade hold=60m day pdrange hi0.67 | negative pre-2023 | 29 | -179.3 | -233.7 | -200.9 | 54.4 | -0.67 / -0.86 / -0.75 | 568.6 / 514.2 |
| BTC 4 5m rsi[14, 30] dir=follow hold=180m all pdrange lo0.33 | positive pre-2023 | 195 | 226.7 | 172.3 | 206.0 | 54.4 | 2.21 / 1.74 / 2.04 | 220.3 / 165.9 |
| BTC 5 15m rsi[14, 30] dir=follow hold=180m day pdrange lo0.33 | positive pre-2023 | 49 | 318.4 | 264.0 | 298.1 | 54.4 | 1.14 / 0.98 / 1.08 | 583.7 / 529.4 |
| BTC 6 5m rsi[14, 30] dir=follow hold=180m day pdrange lo0.33 | positive pre-2023 | 77 | 291.6 | 237.2 | 271.1 | 54.4 | 1.43 / 1.19 / 1.34 | 356.8 / 302.5 |
| BTC 7 5m vwz[2.5, 'rth'] dir=fade hold=180m all pdrange lo0.33 | negative pre-2023 | 77 | -119.8 | -174.2 | -140.9 | 54.4 | -0.65 / -0.96 / -0.77 | 314.3 / 260.0 |
| BTC 8 5m vwz[2.5, 'rth'] dir=follow hold=60m all pdrange hi0.67 | gross-positive, cost-negative pre-2023 | 63 | 7.1 | -47.2 | -14.4 | 54.4 | 0.11 / -0.68 / -0.22 | 223.4 / 169.0 |
| BTC 9 15m rsi[14, 30] dir=follow hold=180m all pdrange lo0.33 | positive pre-2023 | 116 | 154.7 | 100.4 | 133.9 | 54.4 | 1.05 / 0.71 / 0.92 | 277.2 / 222.8 |
| BTC 10 5m rsi[14, 30] dir=fade hold=180m all pdrange hi0.67 | positive pre-2023 | 82 | 312.8 | 258.4 | 291.2 | 54.4 | 1.51 / 1.30 / 1.43 | 169.0 / 114.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 14 cells pass the clean rule against a replicate mean of 12.8 (p(count) = 0.41, p(top) = 0.31); CL: 8 cells pass the clean rule against a replicate mean of 4.4 (p(count) = 0.05, p(top) = 0.62); ES: 14 cells pass the clean rule against a replicate mean of 6.6 (p(count) = 0.00, p(top) = 0.05); GC: 8 cells pass the clean rule against a replicate mean of 6.9 (p(count) = 0.42, p(top) = 0.87); NQ: 23 cells pass the clean rule against a replicate mean of 16.8 (p(count) = 0.07, p(top) = 0.33); RTY: 20 cells pass the clean rule against a replicate mean of 8.2 (p(count) = 0.00, p(top) = 0.00); YM: 3 cells pass the clean rule against a replicate mean of 8.7 (p(count) = 1.00, p(top) = 0.63); ZN: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00).
- Of 59 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.26 (BTC 5m rsi[14, 30] dir=follow hold=60m all pdrange lo0.33); bootstrap lower bound > 0 for 5 cells; plateau >= 0.75 for 4; 2x-slippage all-in uplift >= +0.10 for 11; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 26, 'gross-positive, cost-negative pre-2023': 18, 'negative pre-2023': 15}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_2.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw2/ (`SW2_CO_all_selected_scored.csv`).

DONE SW2
