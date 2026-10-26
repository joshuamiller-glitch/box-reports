# REPORT Q18 - Q18: distance from the RTH open in ADR20 units, with/against, time exit

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 52 selected cells (+12 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.15; best pair-window standalone Sharpe +1.53.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: distance from the RTH open in ADR20 units, with/against, time exit. No stop, full holds before the 16:55 flatten.
- Instruments: ES, NQ, RTY, GC, CL, ZN, BTC, HO. Grid: 96 cells = 2 bar sizes (5,15) x 3 parameter pairs x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         40 |        10 |               1.143 |                2 |         10 |            0 |
| CL    |      96 |         48 |         6 |               1.074 |                2 |          6 |            3 |
| ES    |      96 |         48 |        10 |               1.29  |                2 |         10 |            0 |
| GC    |      96 |         44 |         2 |               1.687 |                2 |          2 |            3 |
| HO    |      96 |         48 |         4 |               0.809 |                2 |          4 |            3 |
| NQ    |      96 |         52 |        26 |               1.022 |                2 |         10 |            0 |
| RTY   |      96 |         48 |        10 |               1.147 |                2 |         10 |            0 |
| ZN    |      96 |         56 |         0 |               0.055 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   10 |            9.455 |              18 |      0.47  |                       0.568 |            0.704 |           0.973 |     0.8  |       0.837 |                1.778 |
| NQ    |     200 |                   26 |           17.74  |              28 |      0.01  |                       0.831 |            1.027 |           1.252 |     0.91 |       1.022 |                2.134 |
| RTY   |     200 |                   10 |           11.455 |              21 |      0.765 |                       0.654 |            0.787 |           1.018 |     0.82 |       1.147 |                1.952 |
| GC    |     200 |                    2 |            9.79  |              23 |      1     |                       0.158 |            0.72  |           0.98  |     1    |       0.158 |                1.907 |
| CL    |     200 |                    6 |            5.605 |              13 |      0.47  |                       0.451 |            0.653 |           0.955 |     0.88 |       0.719 |                1.724 |
| ZN    |     200 |                    0 |            0.05  |               1 |      1     |                     nan     |            0.446 |           0.787 |   nan    |     nan     |                0.787 |
| BTC   |     200 |                   10 |           12.965 |              22 |      0.855 |                       0.618 |            0.845 |           1.136 |     0.93 |       1.143 |                1.904 |
| HO    |     200 |                    4 |           13.125 |              24 |      1     |                       0.425 |            0.875 |           1.117 |     1    |       0.61  |                2.124 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m openDist(0,0.5) dir=with hold 60m day | 353 | 2 | 0.84 | -0.26 | 0.34 | -0.43 / 0.96 | 0.07 / 0.27 / -0.33 | -0.06 | -0.06 | 0.96 | -0.15 | 0.00 | 565 | NO |
| ES 2 | 15m openDist(0,0.5) dir=with hold 60m all | 353 | 2 | 0.84 | -0.26 | 0.34 | -0.43 / 0.74 | 0.07 / 0.27 / -0.33 | -0.06 | -0.06 | 0.98 | -0.15 | 0.00 | 565 | NO |
| ES 3 | 5m openDist(0,0.75) dir=with hold 120m all | 122 | 2 | 0.80 | -0.20 | 0.67 | 0.37 / 1.20 | 0.06 / -0.08 / 0.07 | 0.01 | -0.31 | 0.97 | -0.11 | 0.25 | 187 | NO |
| ES 4 | 5m openDist(0,0.75) dir=with hold 120m day | 122 | 2 | 0.80 | -0.20 | 0.67 | 0.37 / 1.26 | 0.06 / -0.08 / 0.07 | 0.01 | -0.31 | 0.97 | -0.11 | 0.25 | 187 | NO |
| ES 5 | 5m openDist(0,0.5) dir=with hold 60m day | 419 | 2 | 0.53 | -0.39 | 0.44 | 0.22 / 0.91 | 0.02 / 0.28 / -0.23 | -0.06 | 0.36 | 0.96 | -0.14 | 0.00 | 662 | NO |
| ES 6 | 5m openDist(0,0.5) dir=with hold 60m all | 419 | 2 | 0.53 | -0.39 | 0.44 | 0.22 / 0.49 | 0.02 / 0.28 / -0.23 | -0.06 | 0.36 | 1.00 | -0.14 | 0.00 | 662 | NO |
| ES 7 | 5m openDist(0,0.5) dir=against hold 180m day | 223 | 2 | 0.42 | -0.32 | 0.04 | -0.51 / 1.41 | 0.11 / -0.21 / -0.01 | 0.00 | -0.25 | 0.64 | -0.14 | 0.00 | 364 | NO |
| ES 8 | 5m openDist(0,0.5) dir=against hold 180m all | 223 | 2 | 0.42 | -0.32 | 0.04 | -0.51 / 0.99 | 0.11 / -0.21 / -0.01 | 0.00 | -0.25 | 0.80 | -0.14 | 0.00 | 364 | NO |
| ES 9 | 5m openDist(0,0.75) dir=with hold 60m day | 171 | 2 | 0.25 | -0.32 | -0.06 | -0.41 / 0.94 | -0.06 / -0.16 / -0.11 | -0.13 | -0.15 | 0.81 | -0.26 | 0.00 | 269 | NO |
| ES 10 | 5m openDist(0,0.75) dir=with hold 60m all | 171 | 2 | 0.25 | -0.32 | -0.06 | -0.41 / 1.11 | -0.06 / -0.16 / -0.11 | -0.13 | -0.15 | 0.84 | -0.26 | 0.00 | 269 | NO |
| NQ 1 | 15m openDist(0,0.75) dir=with hold 120m all | 110 | 2 | 1.02 | 0.60 | 0.50 | -0.03 / 1.65 | 0.12 / -0.21 / -0.03 | 0.03 | -0.47 | 0.82 | -0.16 | 0.50 | 184 | NO |
| NQ 2 | 15m openDist(0,0.75) dir=with hold 120m day | 110 | 2 | 1.02 | 0.60 | 0.50 | -0.03 / 1.20 | 0.12 / -0.21 / -0.03 | 0.03 | -0.47 | 0.92 | -0.16 | 0.50 | 184 | NO |
| NQ 3 | 5m openDist(0,0.75) dir=with hold 120m day | 131 | 2 | 0.92 | 0.58 | 0.47 | -0.09 / 1.18 | 0.10 / -0.09 / -0.05 | 0.03 | -0.50 | 0.77 | -0.14 | 1.00 | 216 | NO |
| NQ 4 | 5m openDist(0,0.75) dir=with hold 120m all | 131 | 2 | 0.92 | 0.58 | 0.47 | -0.09 / 1.11 | 0.10 / -0.09 / -0.05 | 0.03 | -0.50 | 0.87 | -0.14 | 1.00 | 216 | NO |
| NQ 5 | 5m openDist(0,0.75) dir=with hold 60m day | 181 | 2 | 0.76 | 0.23 | 0.32 | -0.29 / 1.69 | 0.05 / -0.10 / -0.16 | -0.03 | -0.39 | 0.73 | -0.20 | 0.00 | 289 | NO |
| NQ 6 | 5m openDist(0,0.75) dir=with hold 60m all | 181 | 2 | 0.76 | 0.23 | 0.32 | -0.29 / 1.07 | 0.05 / -0.10 / -0.16 | -0.03 | -0.39 | 0.83 | -0.20 | 0.00 | 289 | NO |
| NQ 7 | 15m openDist(0,0.5) dir=with hold 60m all | 352 | 2 | 0.73 | 0.11 | 0.43 | -0.17 / 1.37 | 0.04 / -0.08 / -0.13 | -0.03 | 0.30 | 0.82 | -0.16 | 0.00 | 554 | NO |
| NQ 8 | 15m openDist(0,0.5) dir=with hold 60m day | 352 | 2 | 0.73 | 0.11 | 0.43 | -0.17 / 1.51 | 0.04 / -0.08 / -0.13 | -0.03 | 0.30 | 0.85 | -0.16 | 0.00 | 554 | NO |
| NQ 9 | 5m openDist(0,0.5) dir=with hold 120m all | 322 | 2 | 0.73 | 0.44 | 1.18 | 2.08 / 1.18 | 0.02 / 0.21 / 0.26 | 0.08 | 0.16 | 0.99 | -0.06 | 0.00 | 494 | NO |
| NQ 10 | 5m openDist(0,0.5) dir=with hold 120m day | 322 | 2 | 0.73 | 0.44 | 1.18 | 2.08 / 1.38 | 0.02 / 0.21 / 0.26 | 0.08 | 0.16 | 0.99 | -0.06 | 0.00 | 494 | NO |
| RTY 1 | 15m openDist(0,0.75) dir=against hold 60m day | 144 | 2 | 1.15 | -0.25 | 0.49 | -0.71 / 1.17 | 0.20 / -0.25 / -0.15 | 0.02 | 0.04 | 0.96 | -0.09 | 0.75 | 221 | NO |
| RTY 2 | 15m openDist(0,0.75) dir=against hold 60m all | 144 | 2 | 1.15 | -0.25 | 0.49 | -0.71 / 1.07 | 0.20 / -0.25 / -0.15 | 0.02 | 0.04 | 0.96 | -0.09 | 0.75 | 221 | NO |
| RTY 3 | 5m openDist(0,0.5) dir=with hold 60m day | 392 | 2 | 0.66 | -0.62 | 0.19 | -0.81 / 0.90 | 0.05 / 0.14 / -0.41 | -0.08 | 0.40 | 0.89 | -0.18 | 0.00 | 662 | NO |
| RTY 4 | 5m openDist(0,0.5) dir=with hold 60m all | 392 | 2 | 0.66 | -0.62 | 0.19 | -0.81 / 0.43 | 0.05 / 0.14 / -0.41 | -0.08 | 0.40 | 1.00 | -0.18 | 0.00 | 662 | NO |
| RTY 5 | 15m openDist(0,0.5) dir=against hold 240m all | 169 | 2 | 0.59 | 0.00 | 0.58 | 0.59 / 0.88 | 0.11 / -0.56 / 0.48 | 0.08 | -0.29 | 0.98 | -0.10 | 0.25 | 292 | NO |
| RTY 6 | 15m openDist(0,0.5) dir=against hold 240m day | 169 | 2 | 0.59 | 0.00 | 0.58 | 0.59 / 1.20 | 0.11 / -0.56 / 0.48 | 0.08 | -0.29 | 0.90 | -0.10 | 0.25 | 292 | NO |
| RTY 7 | 15m openDist(0,0.5) dir=against hold 180m all | 203 | 2 | 0.54 | 0.13 | 0.32 | 0.07 / 1.03 | 0.11 / -0.69 / 0.41 | 0.04 | -0.39 | 0.90 | -0.14 | 0.25 | 346 | NO |
| RTY 8 | 15m openDist(0,0.5) dir=against hold 180m day | 203 | 2 | 0.54 | 0.13 | 0.32 | 0.07 / 1.24 | 0.11 / -0.69 / 0.41 | 0.04 | -0.39 | 0.81 | -0.14 | 0.25 | 346 | NO |
| RTY 9 | 15m openDist(0,0.5) dir=with hold 60m all | 335 | 2 | 0.33 | -0.74 | -0.40 | -1.43 / 0.78 | 0.00 / -0.14 / -0.70 | -0.21 | 0.59 | 0.70 | -0.35 | 0.00 | 556 | NO |
| RTY 10 | 15m openDist(0,0.5) dir=with hold 60m day | 335 | 2 | 0.33 | -0.74 | -0.40 | -1.43 / 0.92 | 0.00 / -0.14 / -0.70 | -0.21 | 0.59 | 0.48 | -0.35 | 0.00 | 556 | NO |
| GC 1 | 15m openDist(0,0.5) dir=against hold 180m all | 204 | 2 | 0.16 | -0.37 | 0.13 | 0.10 / 1.32 | 0.06 / -1.73 / 0.74 | -0.08 | -0.31 | 0.73 | -0.42 | 0.00 | 292 | NO |
| GC 2 | 15m openDist(0,0.5) dir=against hold 180m day | 204 | 2 | 0.16 | -0.37 | 0.13 | 0.10 / 1.31 | 0.06 / -1.73 / 0.74 | -0.08 | -0.31 | 0.73 | -0.42 | 0.00 | 292 | NO |
| GC 3 (diag) | 15m openDist(0,1.0) dir=with hold 180m all | 32 | 2 | 1.69 | 0.08 | 1.53 | 1.66 / 1.69 | 0.30 / 0.92 / 0.38 | 0.41 | 0.07 | 1.00 | 0.15 | 0.50 | 50 S | diag |
| GC 4 (diag) | 15m openDist(0,1.0) dir=with hold 180m day | 32 | 2 | 1.69 | 0.08 | 1.53 | 1.66 / 1.25 | 0.30 / 0.92 / 0.38 | 0.41 | 0.07 | 1.00 | 0.15 | 0.50 | 50 S | diag |
| GC 5 (diag) | 15m openDist(0,1.0) dir=with hold 120m all | 42 | 2 | 1.54 | 0.02 | 0.79 | 0.70 / 1.54 | 0.32 / -1.13 / 0.56 | 0.11 | 0.16 | 0.92 | -0.33 | 0.50 | 66 S | diag |
| CL 1 | 15m openDist(0,0.5) dir=with hold 240m all | 179 | 2 | 0.72 | 0.31 | 0.15 | -0.61 / 1.56 | 0.10 / -0.15 / -0.23 | -0.05 | 0.20 | 0.77 | -0.21 | 0.00 | 249 | NO |
| CL 2 | 15m openDist(0,0.5) dir=with hold 240m day | 179 | 2 | 0.72 | 0.31 | 0.15 | -0.61 / 1.28 | 0.10 / -0.15 / -0.23 | -0.05 | 0.20 | 0.75 | -0.21 | 0.00 | 249 | NO |
| CL 3 | 5m openDist(0,0.5) dir=with hold 240m day | 201 | 2 | 0.54 | 0.26 | 0.28 | -0.07 / 1.00 | 0.08 / -0.05 / -0.06 | -0.01 | 0.04 | 0.90 | -0.16 | 0.00 | 279 | NO |
| CL 4 | 5m openDist(0,0.5) dir=with hold 240m all | 201 | 2 | 0.54 | 0.26 | 0.28 | -0.07 / 1.13 | 0.08 / -0.05 / -0.06 | -0.01 | 0.04 | 0.90 | -0.16 | 0.00 | 279 | NO |
| CL 5 | 15m openDist(0,0.5) dir=with hold 120m day | 259 | 2 | 0.09 | -0.01 | -0.52 | -1.30 / 1.21 | -0.02 / -0.25 / -0.53 | -0.24 | 0.21 | 0.56 | -0.36 | 0.00 | 367 | NO |
| CL 6 | 15m openDist(0,0.5) dir=with hold 120m all | 259 | 2 | 0.09 | -0.01 | -0.52 | -1.30 / 0.89 | -0.02 / -0.25 / -0.53 | -0.24 | 0.21 | 0.48 | -0.36 | 0.00 | 367 | NO |
| CL 7 (diag) | 15m openDist(0,1.0) dir=against hold 240m all | 20 | 1 | 1.07 | -0.04 | 0.36 | -0.76 / 1.25 | 0.20 / -0.00 / -0.30 | 0.05 | -0.24 | 0.82 | -0.14 | 0.00 | 27 S | diag |
| CL 8 (diag) | 15m openDist(0,1.0) dir=against hold 240m day | 20 | 1 | 1.07 | -0.04 | 0.36 | -0.76 / 1.74 | 0.20 / -0.00 / -0.30 | 0.05 | -0.24 | 0.83 | -0.14 | 0.00 | 27 S | diag |
| CL 9 (diag) | 5m openDist(0,1.0) dir=against hold 240m day | 22 | 1 | 0.86 | -0.03 | 0.33 | -0.56 / 1.19 | 0.15 / 0.15 / -0.28 | 0.04 | -0.24 | 0.85 | -0.14 | 0.50 | 32 S | diag |
| ZN 1 (diag) | 5m openDist(0,0.75) dir=against hold 180m day | 128 | 1 | 0.06 | -0.90 | -0.34 | -1.14 / -0.88 | -0.05 / -0.40 / 0.02 | -0.35 | 0.03 | 1.00 | -0.27 | 0.00 | 190 | diag |
| ZN 2 (diag) | 5m openDist(0,0.75) dir=against hold 180m all | 128 | 1 | 0.06 | -0.90 | -0.34 | -1.14 / -1.92 | -0.05 / -0.40 / 0.02 | -0.35 | 0.03 | 1.00 | -0.27 | 0.00 | 190 | diag |
| ZN 3 (diag) | 5m openDist(0,0.75) dir=against hold 240m day | 97 | 1 | 0.01 | -0.95 | -0.12 | -0.43 / -0.76 | -0.05 / -0.26 / 0.16 | -0.22 | -0.05 | 1.00 | -0.20 | 0.00 | 143 | diag |
| BTC 1 | 15m openDist(0,0.5) dir=with hold 120m all | 192 | 2 | 1.14 | 1.61 | 0.50 | -0.51 / 1.46 | 0.30 / 0.01 / -0.32 | 0.11 | 0.08 | 0.97 | -0.05 | 0.50 | 297 | NO |
| BTC 2 | 15m openDist(0,0.5) dir=with hold 120m day | 192 | 2 | 1.14 | 1.61 | 0.50 | -0.51 / 1.44 | 0.30 / 0.01 / -0.32 | 0.11 | 0.08 | 0.90 | -0.05 | 0.50 | 297 | NO |
| BTC 3 | 15m openDist(0,0.5) dir=with hold 240m all | 116 | 2 | 0.85 | 0.92 | 0.76 | 0.65 / 1.36 | 0.22 / 0.21 / -0.20 | 0.14 | -0.06 | 0.95 | -0.03 | 0.50 | 188 | NO |
| BTC 4 | 15m openDist(0,0.5) dir=with hold 240m day | 116 | 2 | 0.85 | 0.92 | 0.76 | 0.65 / 1.48 | 0.22 / 0.21 / -0.20 | 0.14 | -0.06 | 0.95 | -0.03 | 0.50 | 188 | NO |
| BTC 5 | 15m openDist(0,0.5) dir=with hold 180m day | 150 | 2 | 0.51 | 1.17 | 0.46 | 0.42 / 0.99 | 0.12 / 0.22 / -0.30 | 0.05 | 0.19 | 0.87 | -0.12 | 1.00 | 234 | NO |
| BTC 6 | 15m openDist(0,0.5) dir=with hold 180m all | 150 | 2 | 0.51 | 1.17 | 0.46 | 0.42 / 1.46 | 0.12 / 0.22 / -0.30 | 0.05 | 0.19 | 0.81 | -0.12 | 1.00 | 234 | NO |
| BTC 7 | 5m openDist(0,0.5) dir=with hold 120m day | 229 | 2 | 0.41 | 1.62 | 0.32 | 0.22 / 1.00 | 0.12 / 0.50 / -0.30 | 0.06 | 0.13 | 0.90 | -0.10 | 0.75 | 347 | NO |
| BTC 8 | 5m openDist(0,0.5) dir=with hold 120m all | 229 | 2 | 0.41 | 1.62 | 0.32 | 0.22 / 1.11 | 0.12 / 0.50 / -0.30 | 0.06 | 0.13 | 0.84 | -0.10 | 0.75 | 347 | NO |
| BTC 9 | 5m openDist(0,0.75) dir=against hold 60m all | 126 | 2 | 0.18 | -1.66 | -0.07 | -0.51 / 1.16 | -0.03 / -0.31 / -0.04 | -0.10 | 0.32 | 0.73 | -0.26 | 0.00 | 189 | NO |
| BTC 10 | 5m openDist(0,0.75) dir=against hold 60m day | 126 | 2 | 0.18 | -1.66 | -0.07 | -0.51 / 1.44 | -0.03 / -0.31 / -0.04 | -0.10 | 0.32 | 0.58 | -0.26 | 0.00 | 189 | NO |
| HO 1 | 5m openDist(0,0.5) dir=with hold 180m day | 251 | 2 | 0.61 | 0.03 | -0.12 | -0.59 / 1.29 | 0.10 / -0.52 / -0.36 | -0.10 | 0.26 | 0.49 | -0.40 | 0.00 | 382 | NO |
| HO 2 | 5m openDist(0,0.5) dir=with hold 180m all | 251 | 2 | 0.61 | 0.03 | -0.12 | -0.59 / 1.59 | 0.10 / -0.52 / -0.36 | -0.10 | 0.26 | 0.57 | -0.40 | 0.00 | 382 | NO |
| HO 3 | 5m openDist(0,0.5) dir=with hold 120m day | 317 | 2 | 0.24 | -0.21 | 0.01 | -0.17 / 1.58 | 0.04 / -0.28 / -0.33 | -0.10 | 0.06 | 0.57 | -0.36 | 0.00 | 483 | NO |
| HO 4 | 5m openDist(0,0.5) dir=with hold 120m all | 317 | 2 | 0.24 | -0.21 | 0.01 | -0.17 / 1.42 | 0.04 / -0.28 / -0.33 | -0.10 | 0.06 | 0.60 | -0.36 | 0.00 | 483 | NO |
| HO 5 (diag) | 5m openDist(0,1.0) dir=against hold 240m all | 26 | 1 | 0.81 | 0.40 | 0.58 | 0.50 / 1.45 | 0.10 / 0.00 / -0.29 | -0.01 | -0.24 | 0.88 | -0.23 | 0.00 | 37 S | diag |
| HO 6 (diag) | 5m openDist(0,1.0) dir=against hold 240m day | 26 | 1 | 0.81 | 0.40 | 0.58 | 0.50 / 1.60 | 0.10 / 0.00 / -0.29 | -0.01 | -0.24 | 0.81 | -0.23 | 0.00 | 37 S | diag |
| HO 7 (diag) | 15m openDist(0,1.0) dir=against hold 240m all | 24 | 1 | 0.76 | 0.15 | -0.12 | -0.67 / 1.46 | 0.09 / -0.06 / -0.97 | -0.20 | -0.24 | 0.43 | -0.60 | 0.00 | 33 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 52 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 32 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 2 |
| standalone pair-window Sharpe above own random-entry null p95 | 20 |
| worst-decile corr <= +0.30 | 54 |
| plateau >= 0.75 | 8 |
| all-in uplift at 2x slippage >= +0.10 | 7 |
| small-sample (<100 trades pair window) | 9 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 15m openDist(0,0.5) dir=with hold 240m day | clean | 0.84 | 1.26 | -147219 | -102372 | 373659 | -290726 | 2.04 | 29.5 | 1.68 | -80333 | 221748 | -88242 |
| BTC 15m openDist(0,0.5) dir=with hold 240m day | H1 | 1.92 | 4.42 | -139777 | -109259 | 398518 | -144665 | 1.72 | 35.7 | 3.03 | -92505 | 154465 | -103910 |
| BTC 15m openDist(0,0.5) dir=with hold 240m day | H2 | -1.17 | -1.39 | -111228 | -104578 | 504793 | -111738 | -0.54 | 33.3 | 2.29 | -93567 | 215559 | -104872 |
| BTC 15m openDist(0,0.5) dir=with hold 240m day | all | 0.76 | 1.23 | -147929 | -111048 | 598335 | -290726 | 1.96 | 31.5 | 2.05 | -86331 | 221748 | -104872 |
| CL 5m openDist(0,0.5) dir=with hold 240m all | clean | 0.52 | 0.76 | -145733 | -108248 | 540833 | -239248 | 0.87 | 41.0 | 1.54 | -94981 | 263374 | -125108 |
| CL 5m openDist(0,0.5) dir=with hold 240m all | H1 | 0.05 | 0.07 | -47795 | -43457 | 145035 | -52491 | 0.03 | 39.3 | 2.78 | -82859 | 160382 | -86907 |
| CL 5m openDist(0,0.5) dir=with hold 240m all | H2 | -0.11 | -0.17 | -193936 | -152227 | 794833 | -195650 | -0.06 | 38.9 | 2.43 | -92602 | 212082 | -102679 |
| CL 5m openDist(0,0.5) dir=with hold 240m all | all | 0.28 | 0.41 | -155841 | -119454 | 794833 | -239248 | 0.53 | 39.9 | 1.93 | -93660 | 263374 | -125108 |
| ES 5m openDist(0,0.5) dir=against hold 180m day | clean | 0.37 | 0.54 | -148722 | -110138 | 468397 | -229739 | 0.71 | 42.9 | 1.57 | -82714 | 281604 | -98112 |
| ES 5m openDist(0,0.5) dir=against hold 180m day | H1 | -1.33 | -1.71 | -128975 | -119674 | 393529 | -156862 | -0.77 | 53.6 | 2.62 | -71705 | 187149 | -84800 |
| ES 5m openDist(0,0.5) dir=against hold 180m day | H2 | 0.07 | 0.11 | -128083 | -109660 | 264401 | -141526 | 0.09 | 41.7 | 2.47 | -82825 | 198657 | -83125 |
| ES 5m openDist(0,0.5) dir=against hold 180m day | all | 0.04 | 0.05 | -146194 | -117312 | 804334 | -229739 | 0.07 | 44.6 | 1.93 | -83145 | 281604 | -98112 |
| GC 15m openDist(0,0.5) dir=against hold 180m all | clean | 0.23 | 0.33 | -147862 | -116618 | 471889 | -191620 | 0.43 | 41.0 | 1.52 | -85737 | 257892 | -96162 |
| GC 15m openDist(0,0.5) dir=against hold 180m all | H1 | -2.60 | -2.64 | -439144 | -402801 | 1680634 | -456876 | -0.90 | 53.6 | 1.10 | -131575 | 238951 | -144310 |
| GC 15m openDist(0,0.5) dir=against hold 180m all | H2 | 1.98 | 3.76 | -316059 | -253198 | 632118 | -340989 | 2.63 | 19.4 | 3.23 | -115344 | 225587 | -124503 |
| GC 15m openDist(0,0.5) dir=against hold 180m all | all | 0.13 | 0.19 | -294922 | -219725 | 1799097 | -456876 | 0.19 | 38.1 | 1.85 | -106009 | 267209 | -144310 |
| HO 5m openDist(0,0.5) dir=with hold 120m all | clean | 0.27 | 0.40 | -138319 | -113436 | 564638 | -199072 | 0.44 | 42.9 | 1.50 | -82410 | 301603 | -89113 |
| HO 5m openDist(0,0.5) dir=with hold 120m all | H1 | -0.94 | -1.25 | -75706 | -69747 | 360534 | -93583 | -0.42 | 50.0 | 2.55 | -92479 | 164140 | -97004 |
| HO 5m openDist(0,0.5) dir=with hold 120m all | H2 | -0.08 | -0.10 | -500319 | -327606 | 1405775 | -835180 | -0.05 | 44.4 | 2.15 | -89015 | 274543 | -90188 |
| HO 5m openDist(0,0.5) dir=with hold 120m all | all | 0.01 | 0.01 | -232570 | -170778 | 1405775 | -835180 | 0.02 | 44.6 | 1.82 | -87355 | 301603 | -97004 |
| NQ 5m openDist(0,0.5) dir=with hold 120m day | clean | 0.72 | 1.43 | -108959 | -82838 | 422870 | -173619 | 1.55 | 42.9 | 1.48 | -92030 | 349640 | -116598 |
| NQ 5m openDist(0,0.5) dir=with hold 120m day | H1 | 2.13 | 4.23 | -68441 | -60491 | 134044 | -90143 | 3.06 | 39.3 | 3.04 | -81398 | 150308 | -94961 |
| NQ 5m openDist(0,0.5) dir=with hold 120m day | H2 | 2.02 | 4.19 | -70938 | -64725 | 166089 | -78427 | 3.28 | 36.1 | 2.74 | -88564 | 222980 | -91971 |
| NQ 5m openDist(0,0.5) dir=with hold 120m day | all | 1.18 | 2.35 | -98907 | -77984 | 422870 | -173619 | 3.81 | 41.1 | 1.99 | -91585 | 349640 | -116598 |
| RTY 15m openDist(0,0.5) dir=against hold 240m all | clean | 0.57 | 0.78 | -148475 | -107324 | 398861 | -346089 | 1.30 | 33.3 | 1.57 | -85762 | 241957 | -97450 |
| RTY 15m openDist(0,0.5) dir=against hold 240m all | H1 | -1.69 | -1.88 | -209268 | -186758 | 802544 | -243528 | -0.63 | 46.4 | 2.27 | -85680 | 188276 | -93241 |
| RTY 15m openDist(0,0.5) dir=against hold 240m all | H2 | 2.28 | 7.13 | -77112 | -65379 | 125280 | -87418 | 7.53 | 36.1 | 2.97 | -81195 | 226892 | -82524 |
| RTY 15m openDist(0,0.5) dir=against hold 240m all | all | 0.58 | 0.86 | -166339 | -119275 | 1050172 | -346089 | 0.91 | 36.3 | 2.00 | -85708 | 241957 | -97450 |
| ZN 5m openDist(0,0.75) dir=against hold 240m day (diag) | clean | 0.01 | 0.02 | -116761 | -105171 | 640780 | -141803 | 0.01 | 30.5 | 1.41 | -87302 | 331250 | -94369 |
| ZN 5m openDist(0,0.75) dir=against hold 240m day (diag) | H1 | -1.99 | -2.14 | -118543 | -101344 | 347020 | -166827 | -0.99 | 35.7 | 2.57 | -72220 | 153146 | -76932 |
| ZN 5m openDist(0,0.75) dir=against hold 240m day (diag) | H2 | 0.87 | 1.25 | -100150 | -67961 | 200299 | -153032 | 0.89 | 22.2 | 2.64 | -81089 | 206902 | -82524 |
| ZN 5m openDist(0,0.75) dir=against hold 240m day (diag) | all | -0.12 | -0.18 | -124253 | -105173 | 640780 | -166827 | -0.24 | 29.8 | 1.86 | -84811 | 331250 | -94369 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 5m openDist(0,0.5) dir=against hold 180m day | -29.4 | -27.8 | 19.1 | 9.3 | -28.8 / 17.0 | 17.5 / 27.0 | NO |
| NQ 5m openDist(0,0.5) dir=with hold 120m day | -12.4 | -32.6 | 4.4 | -7.2 | -33.6 / 2.5 | -3.3 / 19.5 | NO |
| RTY 15m openDist(0,0.5) dir=against hold 240m all | -19.6 | -10.4 | 10.2 | 30.5 | -10.0 / 13.0 | -16.4 / -9.2 | NO |
| GC 15m openDist(0,0.5) dir=against hold 180m all | -26.2 | -86.4 | -44.6 | -7.9 | -0.9 / 11.6 | -96.5 / -92.5 | NO |
| CL 5m openDist(0,0.5) dir=with hold 240m all | -25.4 | -52.5 | -0.3 | 27.9 | -53.7 / -2.4 | 13.5 / 19.9 | NO |
| ZN 5m openDist(0,0.75) dir=against hold 240m day (diag) | -31.7 | 3.7 | 15.6 | -10.5 | 2.9 / 9.8 | 31.2 / 36.5 | NO |
| BTC 15m openDist(0,0.5) dir=with hold 240m day | -17.2 | -14.3 | 13.4 | 36.1 | 13.6 / 22.3 | -20.5 / 1.2 | NO |
| HO 5m openDist(0,0.5) dir=with hold 120m all | -29.7 | -89.9 | -7.8 | -40.4 | -2.9 / 14.9 | -5.9 / 1.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m openDist(0,0.5) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 1567 | 18.2 | -11.1 | 3.1 | 29.4 | 0.42 / -0.26 / 0.07 | 96.9 / 67.6 |
| ES 2 15m openDist(0,0.5) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 1567 | 18.2 | -11.1 | 3.1 | 29.4 | 0.42 / -0.26 / 0.07 | 96.9 / 67.6 |
| ES 3 5m openDist(0,0.75) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 655 | 4.8 | -24.6 | -10.2 | 29.4 | 0.04 / -0.20 / -0.09 | 225.2 / 195.8 |
| ES 4 5m openDist(0,0.75) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 655 | 4.8 | -24.6 | -10.2 | 29.4 | 0.04 / -0.20 / -0.09 | 225.2 / 195.8 |
| ES 5 5m openDist(0,0.5) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 1875 | 10.0 | -19.4 | -5.1 | 29.4 | 0.20 / -0.39 / -0.10 | 81.3 / 51.9 |
| ES 6 5m openDist(0,0.5) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 1875 | 10.0 | -19.4 | -5.1 | 29.4 | 0.20 / -0.39 / -0.10 | 81.3 / 51.9 |
| ES 7 5m openDist(0,0.5) dir=against hold 180m day | negative pre-2023 | 1049 | -1.8 | -31.2 | -16.9 | 29.4 | -0.02 / -0.32 / -0.17 | 82.3 / 53.0 |
| ES 8 5m openDist(0,0.5) dir=against hold 180m all | negative pre-2023 | 1049 | -1.8 | -31.2 | -16.9 | 29.4 | -0.02 / -0.32 / -0.17 | 82.3 / 53.0 |
| ES 9 5m openDist(0,0.75) dir=with hold 60m day | gross-positive, cost-negative pre-2023 | 906 | 5.9 | -23.4 | -9.1 | 29.4 | 0.08 / -0.32 / -0.12 | 41.3 / 11.9 |
| ES 10 5m openDist(0,0.75) dir=with hold 60m all | gross-positive, cost-negative pre-2023 | 906 | 5.9 | -23.4 | -9.1 | 29.4 | 0.08 / -0.32 / -0.12 | 41.3 / 11.9 |
| NQ 1 15m openDist(0,0.75) dir=with hold 120m all | positive pre-2023 | 625 | 97.6 | 83.2 | 91.9 | 14.4 | 0.70 / 0.60 / 0.66 | 387.9 / 373.5 |
| NQ 2 15m openDist(0,0.75) dir=with hold 120m day | positive pre-2023 | 625 | 97.6 | 83.2 | 91.9 | 14.4 | 0.70 / 0.60 / 0.66 | 387.9 / 373.5 |
| NQ 3 5m openDist(0,0.75) dir=with hold 120m day | positive pre-2023 | 743 | 81.3 | 66.9 | 75.6 | 14.4 | 0.70 / 0.58 / 0.65 | 354.6 / 340.2 |
| NQ 4 5m openDist(0,0.75) dir=with hold 120m all | positive pre-2023 | 743 | 81.3 | 66.9 | 75.6 | 14.4 | 0.70 / 0.58 / 0.65 | 354.6 / 340.2 |
| NQ 5 5m openDist(0,0.75) dir=with hold 60m day | positive pre-2023 | 1010 | 33.5 | 19.1 | 27.8 | 14.4 | 0.39 / 0.23 / 0.33 | 166.9 / 152.5 |
| NQ 6 5m openDist(0,0.75) dir=with hold 60m all | positive pre-2023 | 1010 | 33.5 | 19.1 | 27.8 | 14.4 | 0.39 / 0.23 / 0.33 | 166.9 / 152.5 |
| NQ 7 15m openDist(0,0.5) dir=with hold 60m all | positive pre-2023 | 1747 | 21.3 | 6.9 | 15.4 | 14.4 | 0.33 / 0.11 / 0.24 | 139.8 / 125.4 |
| NQ 8 15m openDist(0,0.5) dir=with hold 60m day | positive pre-2023 | 1747 | 21.3 | 6.9 | 15.4 | 14.4 | 0.33 / 0.11 / 0.24 | 139.8 / 125.4 |
| NQ 9 5m openDist(0,0.5) dir=with hold 120m all | positive pre-2023 | 1628 | 52.4 | 38.1 | 46.7 | 14.4 | 0.61 / 0.44 / 0.55 | 178.4 / 164.0 |
| NQ 10 5m openDist(0,0.5) dir=with hold 120m day | positive pre-2023 | 1628 | 52.4 | 38.1 | 46.7 | 14.4 | 0.61 / 0.44 / 0.55 | 178.4 / 164.0 |
| RTY 1 15m openDist(0,0.75) dir=against hold 60m day | gross-positive, cost-negative pre-2023 | 486 | 1.5 | -12.8 | -10.6 | 14.4 | 0.03 / -0.25 / -0.21 | 81.5 / 67.1 |
| RTY 2 15m openDist(0,0.75) dir=against hold 60m all | gross-positive, cost-negative pre-2023 | 486 | 1.5 | -12.8 | -10.6 | 14.4 | 0.03 / -0.25 / -0.21 | 81.5 / 67.1 |
| RTY 3 5m openDist(0,0.5) dir=with hold 60m day | negative pre-2023 | 1331 | -4.8 | -19.1 | -16.9 | 14.4 | -0.15 / -0.62 / -0.55 | 53.1 / 38.7 |
| RTY 4 5m openDist(0,0.5) dir=with hold 60m all | negative pre-2023 | 1331 | -4.8 | -19.1 | -16.9 | 14.4 | -0.15 / -0.62 / -0.55 | 53.1 / 38.7 |
| RTY 5 15m openDist(0,0.5) dir=against hold 240m all | positive pre-2023 | 598 | 14.4 | 0.1 | 2.3 | 14.4 | 0.22 / 0.00 / 0.03 | 71.6 / 57.2 |
| RTY 6 15m openDist(0,0.5) dir=against hold 240m day | positive pre-2023 | 598 | 14.4 | 0.1 | 2.3 | 14.4 | 0.22 / 0.00 / 0.03 | 71.6 / 57.2 |
| RTY 7 15m openDist(0,0.5) dir=against hold 180m all | positive pre-2023 | 673 | 22.3 | 8.0 | 10.2 | 14.4 | 0.37 / 0.13 / 0.17 | 55.5 / 41.2 |
| RTY 8 15m openDist(0,0.5) dir=against hold 180m day | positive pre-2023 | 673 | 22.3 | 8.0 | 10.2 | 14.4 | 0.37 / 0.13 / 0.17 | 55.5 / 41.2 |
| RTY 9 15m openDist(0,0.5) dir=with hold 60m all | negative pre-2023 | 1084 | -9.9 | -24.2 | -22.1 | 14.4 | -0.30 / -0.74 / -0.68 | 29.2 / 14.9 |
| RTY 10 15m openDist(0,0.5) dir=with hold 60m day | negative pre-2023 | 1084 | -9.9 | -24.2 | -22.1 | 14.4 | -0.30 / -0.74 / -0.68 | 29.2 / 14.9 |
| GC 1 15m openDist(0,0.5) dir=against hold 180m all | negative pre-2023 | 962 | -6.4 | -30.7 | -21.1 | 24.4 | -0.07 / -0.37 / -0.25 | 51.2 / 26.9 |
| GC 2 15m openDist(0,0.5) dir=against hold 180m day | negative pre-2023 | 962 | -6.4 | -30.7 | -21.1 | 24.4 | -0.07 / -0.37 / -0.25 | 51.2 / 26.9 |
| GC 3 (diag) 15m openDist(0,1.0) dir=with hold 180m all | positive pre-2023 | 187 | 37.3 | 13.0 | 22.3 | 24.4 | 0.22 / 0.08 / 0.13 | 363.1 / 338.8 |
| GC 4 (diag) 15m openDist(0,1.0) dir=with hold 180m day | positive pre-2023 | 187 | 37.3 | 13.0 | 22.3 | 24.4 | 0.22 / 0.08 / 0.13 | 363.1 / 338.8 |
| GC 5 (diag) 15m openDist(0,1.0) dir=with hold 120m all | positive pre-2023 | 246 | 27.6 | 3.2 | 12.6 | 24.4 | 0.19 / 0.02 / 0.09 | 267.4 / 243.0 |
| CL 1 15m openDist(0,0.5) dir=with hold 240m all | positive pre-2023 | 864 | 52.5 | 28.2 | 30.5 | 24.4 | 0.58 / 0.31 / 0.34 | 81.0 / 56.6 |
| CL 2 15m openDist(0,0.5) dir=with hold 240m day | positive pre-2023 | 864 | 52.5 | 28.2 | 30.5 | 24.4 | 0.58 / 0.31 / 0.34 | 81.0 / 56.6 |
| CL 3 5m openDist(0,0.5) dir=with hold 240m day | positive pre-2023 | 988 | 46.6 | 22.3 | 24.5 | 24.4 | 0.55 / 0.26 / 0.29 | 65.3 / 40.9 |
| CL 4 5m openDist(0,0.5) dir=with hold 240m all | positive pre-2023 | 988 | 46.6 | 22.3 | 24.5 | 24.4 | 0.55 / 0.26 / 0.29 | 65.3 / 40.9 |
| CL 5 15m openDist(0,0.5) dir=with hold 120m day | gross-positive, cost-negative pre-2023 | 1324 | 23.9 | -0.5 | 1.9 | 24.4 | 0.45 / -0.01 / 0.04 | 27.5 / 3.1 |
| CL 6 15m openDist(0,0.5) dir=with hold 120m all | gross-positive, cost-negative pre-2023 | 1324 | 23.9 | -0.5 | 1.9 | 24.4 | 0.45 / -0.01 / 0.04 | 27.5 / 3.1 |
| CL 7 (diag) 15m openDist(0,1.0) dir=against hold 240m all | gross-positive, cost-negative pre-2023 | 118 | 11.2 | -13.2 | -9.4 | 24.4 | 0.03 / -0.04 / -0.03 | 325.0 / 300.6 |
| CL 8 (diag) 15m openDist(0,1.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 118 | 11.2 | -13.2 | -9.4 | 24.4 | 0.03 / -0.04 / -0.03 | 325.0 / 300.6 |
| CL 9 (diag) 5m openDist(0,1.0) dir=against hold 240m day | gross-positive, cost-negative pre-2023 | 139 | 16.3 | -8.1 | -4.5 | 24.4 | 0.05 / -0.03 / -0.01 | 243.2 / 218.8 |
| ZN 1 (diag) 5m openDist(0,0.75) dir=against hold 180m day | gross-positive, cost-negative pre-2023 | 500 | 5.9 | -29.7 | -34.8 | 35.6 | 0.18 / -0.90 / -1.05 | 36.1 / 0.5 |
| ZN 2 (diag) 5m openDist(0,0.75) dir=against hold 180m all | gross-positive, cost-negative pre-2023 | 500 | 5.9 | -29.7 | -34.8 | 35.6 | 0.18 / -0.90 / -1.05 | 36.1 / 0.5 |
| ZN 3 (diag) 5m openDist(0,0.75) dir=against hold 240m day | negative pre-2023 | 402 | -5.1 | -40.7 | -45.8 | 35.6 | -0.12 / -0.95 / -1.07 | 35.9 / 0.3 |
| BTC 1 15m openDist(0,0.5) dir=with hold 120m all | positive pre-2023 | 106 | 483.3 | 428.9 | 459.9 | 54.4 | 1.81 / 1.61 / 1.72 | 491.1 / 436.8 |
| BTC 2 15m openDist(0,0.5) dir=with hold 120m day | positive pre-2023 | 106 | 483.3 | 428.9 | 459.9 | 54.4 | 1.81 / 1.61 / 1.72 | 491.1 / 436.8 |
| BTC 3 15m openDist(0,0.5) dir=with hold 240m all | positive pre-2023 | 57 | 514.5 | 460.1 | 490.9 | 54.4 | 1.03 / 0.92 / 0.98 | 699.1 / 644.8 |
| BTC 4 15m openDist(0,0.5) dir=with hold 240m day | positive pre-2023 | 57 | 514.5 | 460.1 | 490.9 | 54.4 | 1.03 / 0.92 / 0.98 | 699.1 / 644.8 |
| BTC 5 15m openDist(0,0.5) dir=with hold 180m day | positive pre-2023 | 80 | 434.4 | 380.0 | 411.1 | 54.4 | 1.34 / 1.17 / 1.26 | 313.0 / 258.6 |
| BTC 6 15m openDist(0,0.5) dir=with hold 180m all | positive pre-2023 | 80 | 434.4 | 380.0 | 411.1 | 54.4 | 1.34 / 1.17 / 1.26 | 313.0 / 258.6 |
| BTC 7 5m openDist(0,0.5) dir=with hold 120m day | positive pre-2023 | 123 | 427.4 | 373.1 | 403.7 | 54.4 | 1.85 / 1.62 / 1.75 | 201.4 / 147.1 |
| BTC 8 5m openDist(0,0.5) dir=with hold 120m all | positive pre-2023 | 123 | 427.4 | 373.1 | 403.7 | 54.4 | 1.85 / 1.62 / 1.75 | 201.4 / 147.1 |
| BTC 9 5m openDist(0,0.75) dir=against hold 60m all | negative pre-2023 | 72 | -388.9 | -443.2 | -412.3 | 54.4 | -1.48 / -1.66 / -1.56 | 138.5 / 84.1 |
| BTC 10 5m openDist(0,0.75) dir=against hold 60m day | negative pre-2023 | 72 | -388.9 | -443.2 | -412.3 | 54.4 | -1.48 / -1.66 / -1.56 | 138.5 / 84.1 |
| HO 1 5m openDist(0,0.5) dir=with hold 180m day | positive pre-2023 | 1267 | 16.2 | 3.4 | 4.8 | 12.8 | 0.17 / 0.03 / 0.05 | 65.3 / 52.5 |
| HO 2 5m openDist(0,0.5) dir=with hold 180m all | positive pre-2023 | 1267 | 16.2 | 3.4 | 4.8 | 12.8 | 0.17 / 0.03 / 0.05 | 65.3 / 52.5 |
| HO 3 5m openDist(0,0.5) dir=with hold 120m day | negative pre-2023 | 1692 | -1.4 | -14.1 | -12.7 | 12.8 | -0.02 / -0.21 / -0.19 | 31.0 / 18.2 |
| HO 4 5m openDist(0,0.5) dir=with hold 120m all | negative pre-2023 | 1692 | -1.4 | -14.1 | -12.7 | 12.8 | -0.02 / -0.21 / -0.19 | 31.0 / 18.2 |
| HO 5 (diag) 5m openDist(0,1.0) dir=against hold 240m all | positive pre-2023 | 144 | 236.4 | 223.6 | 224.9 | 12.8 | 0.43 / 0.40 / 0.41 | 265.7 / 253.0 |
| HO 6 (diag) 5m openDist(0,1.0) dir=against hold 240m day | positive pre-2023 | 144 | 236.4 | 223.6 | 224.9 | 12.8 | 0.43 / 0.40 / 0.41 | 265.7 / 253.0 |
| HO 7 (diag) 15m openDist(0,1.0) dir=against hold 240m all | positive pre-2023 | 128 | 105.2 | 92.4 | 93.7 | 12.8 | 0.17 / 0.15 / 0.15 | 217.5 / 204.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 10 cells pass the clean rule against a replicate mean of 13.0 (p(count) = 0.85, p(top) = 0.93); CL: 6 cells pass the clean rule against a replicate mean of 5.6 (p(count) = 0.47, p(top) = 0.88); ES: 10 cells pass the clean rule against a replicate mean of 9.5 (p(count) = 0.47, p(top) = 0.80); GC: 2 cells pass the clean rule against a replicate mean of 9.8 (p(count) = 1.00, p(top) = 1.00); HO: 4 cells pass the clean rule against a replicate mean of 13.1 (p(count) = 1.00, p(top) = 1.00); NQ: 26 cells pass the clean rule against a replicate mean of 17.7 (p(count) = 0.01, p(top) = 0.91); RTY: 10 cells pass the clean rule against a replicate mean of 11.5 (p(count) = 0.77, p(top) = 0.82); ZN: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00).
- Of 52 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.15 (BTC 15m openDist(0,0.5) dir=with hold 240m all); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 8; 2x-slippage all-in uplift >= +0.10 for 4; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 28, 'gross-positive, cost-negative pre-2023': 12, 'negative pre-2023': 12}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q18.py (ap_q_sig.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q18/ (`Q18_CO_all_selected_scored.csv`).

DONE Q18
