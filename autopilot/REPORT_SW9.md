# REPORT SW9 - overnight cross-asset driver move -> RTH direction (D07 H4)

**Verdict: LEAD (weak). The automatic 'FOUND-CANDIDATE' tag (YM driver NKD overnight, section 7) was downgraded after verification. FOUND 0, LEAD 10, INSURANCE 3.** 75 selected cells (+3 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.34; best pair-window standalone Sharpe +1.79.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: driver (NKD, 6J, 6E, ZN, CL, GC, ES, NQ except self) move over an overnight window (asia 18:00-02:00, eur 02:00-08:20, ovn 18:00-08:20 ET) in sigma units, |z| >= theta (0/1): enter at RTH open + d (0/30) with or against the sign; hold to the 16:55 flatten or 120 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: about 336 cells per instrument = 7 drivers x 3 windows x 2 theta x 2 delays x 2 directions x 2 holds.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     384 |        260 |        55 |               1.77  |                2 |         10 |            0 |
| CL    |     336 |        240 |        28 |               1.394 |                2 |         10 |            0 |
| ES    |     336 |        248 |        29 |               1.424 |                2 |         10 |            0 |
| GC    |     336 |        232 |        33 |               2.124 |                2 |         10 |            0 |
| NQ    |     336 |        248 |        35 |               1.296 |                2 |         10 |            0 |
| RTY   |     384 |        280 |        56 |               1.901 |                2 |         10 |            0 |
| YM    |     384 |        280 |        46 |               1.588 |                2 |         10 |            0 |
| ZN    |     336 |        256 |         5 |               0.928 |                2 |          5 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                   29 |            28.58 |              39 |       0.48 |                       0.899 |            1.109 |           1.308 |     0.94 |       1.054 |                2.176 |
| NQ    |     100 |                   35 |            44.17 |              59 |       0.94 |                       1.037 |            1.351 |           1.542 |     0.99 |       1.296 |                2.368 |
| RTY   |     100 |                   56 |            38.12 |              54 |       0    |                       1.532 |            1.228 |           1.416 |     0    |       1.901 |                2.154 |
| YM    |     100 |                   46 |            38.28 |              54 |       0.11 |                       1.234 |            1.232 |           1.424 |     0.48 |       1.588 |                2.234 |
| GC    |     100 |                   33 |            29.53 |              42 |       0.32 |                       1.005 |            1.153 |           1.403 |     0.85 |       1.245 |                2.123 |
| CL    |     100 |                   28 |            23.07 |              36 |       0.16 |                       1.071 |            1.029 |           1.225 |     0.39 |       1.394 |                2.073 |
| ZN    |     100 |                    5 |             1.74 |               5 |       0.04 |                       0.396 |            0.542 |           1.045 |     0.52 |       0.606 |                1.496 |
| BTC   |     100 |                   55 |            46.63 |              65 |       0.1  |                       1.308 |            1.325 |           1.526 |     0.6  |       1.77  |                2.363 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | driver 6J asia |z|>=0.0 RTHopen+30 dir=against hold=120m | 510 | 2 | 1.05 | -0.46 | 0.88 | 0.57 / 0.80 | 0.14 / -0.25 / 0.37 | 0.06 | -0.46 | 1.00 | -0.06 | 1.00 | 808 | NO |
| ES 2 | driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=120m | 113 | 2 | 1.05 | -0.22 | -0.15 | -1.55 / 0.83 | 0.18 / -0.45 / -0.59 | -0.10 | 0.35 | 0.63 | -0.28 | 0.00 | 180 | NO |
| ES 3 | driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | 511 | 2 | 1.05 | -0.10 | 1.02 | 1.16 / 1.60 | 0.18 / 0.06 / 0.18 | 0.14 | -0.10 | 0.97 | 0.03 | 0.00 | 817 | NO |
| ES 4 | driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | 511 | 2 | 0.95 | -0.14 | 0.89 | 0.94 / 1.03 | 0.16 / 0.08 / 0.19 | 0.13 | -0.17 | 0.98 | 0.01 | 0.00 | 817 | NO |
| ES 5 | driver NQ eur |z|>=1.0 RTHopen+30 dir=against hold=120m | 113 | 2 | 0.88 | -0.13 | -0.01 | -1.54 / 0.71 | 0.12 / -0.21 / -0.40 | -0.08 | -0.04 | 0.66 | -0.22 | 0.00 | 180 | NO |
| ES 6 | driver 6J eur |z|>=0.0 RTHopen+30 dir=with hold=flat | 511 | 2 | 0.83 | -0.72 | 0.10 | -1.39 / 1.32 | 0.11 / -0.42 / -0.14 | -0.07 | -0.07 | 0.64 | -0.20 | 0.00 | 811 | NO |
| ES 7 | driver 6E ovn |z|>=0.0 RTHopen+0 dir=with hold=120m | 514 | 2 | 0.82 | -0.36 | 0.72 | 0.58 / 0.65 | 0.13 / 0.06 / -0.08 | 0.01 | 0.61 | 1.00 | -0.12 | 0.50 | 820 | NO |
| ES 8 | driver GC ovn |z|>=1.0 RTHopen+30 dir=against hold=120m | 120 | 2 | 0.80 | -0.31 | 0.76 | 0.62 / 1.16 | 0.08 / 0.46 / -0.28 | 0.02 | 0.28 | 0.97 | -0.11 | 0.75 | 205 | NO |
| ES 9 | driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | 107 | 2 | 0.79 | -0.53 | 0.73 | 0.62 / 1.27 | 0.21 / -0.13 / 0.17 | 0.15 | 0.11 | 0.96 | -0.02 | 0.50 | 179 | NO |
| ES 10 | driver GC asia |z|>=1.0 RTHopen+30 dir=against hold=120m | 100 | 2 | 0.78 | -0.75 | 1.10 | 1.51 / 1.17 | 0.05 / 0.85 / -0.10 | 0.11 | 0.05 | 0.99 | -0.04 | 0.50 | 192 | NO |
| NQ 1 | driver 6J asia |z|>=0.0 RTHopen+30 dir=against hold=120m | 510 | 2 | 1.30 | -0.03 | 1.16 | 0.97 / 1.36 | 0.19 / -0.17 / 0.59 | 0.20 | -0.45 | 1.00 | 0.00 | 1.00 | 808 | NO |
| NQ 2 | driver GC ovn |z|>=1.0 RTHopen+30 dir=against hold=120m | 120 | 2 | 1.29 | 0.11 | 1.36 | 1.42 / 1.48 | 0.18 / 0.72 / -0.16 | 0.18 | 0.39 | 0.99 | 0.01 | 0.75 | 205 | NO |
| NQ 3 | driver GC asia |z|>=1.0 RTHopen+30 dir=against hold=120m | 100 | 2 | 1.26 | -0.38 | 1.61 | 2.05 / 1.72 | 0.16 / 1.08 / 0.01 | 0.26 | 0.01 | 1.00 | 0.07 | 0.75 | 192 | NO |
| NQ 4 | driver 6E ovn |z|>=0.0 RTHopen+0 dir=with hold=120m | 514 | 2 | 1.17 | 0.02 | 0.87 | 0.62 / 1.51 | 0.19 / 0.13 / -0.10 | 0.10 | 0.68 | 0.96 | -0.11 | 0.50 | 820 | NO |
| NQ 5 | driver 6E ovn |z|>=0.0 RTHopen+0 dir=with hold=flat | 514 | 2 | 1.00 | -0.11 | 1.02 | 1.15 / 1.65 | 0.14 / 0.28 / 0.06 | 0.14 | 0.40 | 0.95 | -0.04 | 0.00 | 820 | NO |
| NQ 6 | driver ZN asia |z|>=0.0 RTHopen+0 dir=against hold=120m | 482 | 2 | 0.93 | 0.07 | 0.48 | -0.04 / 1.49 | 0.19 / -0.55 / 0.24 | 0.09 | -0.37 | 0.87 | -0.13 | 1.00 | 773 | NO |
| NQ 7 | driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | 511 | 2 | 0.90 | 0.06 | 0.71 | 0.54 / 1.50 | 0.15 / -0.00 / 0.14 | 0.12 | -0.07 | 0.89 | -0.04 | 0.00 | 817 | NO |
| NQ 8 | driver 6E ovn |z|>=0.0 RTHopen+30 dir=with hold=120m | 514 | 2 | 0.87 | -0.19 | 0.05 | -1.11 / 1.02 | 0.13 / -0.11 / -0.60 | -0.08 | 0.54 | 0.55 | -0.25 | 0.00 | 820 | NO |
| NQ 9 | driver 6J asia |z|>=0.0 RTHopen+0 dir=against hold=120m | 510 | 2 | 0.84 | -0.04 | 1.26 | 1.71 / 1.42 | 0.12 / 0.22 / 0.49 | 0.20 | -0.66 | 0.99 | -0.00 | 1.00 | 808 | LEAD |
| NQ 10 | driver 6E ovn |z|>=0.0 RTHopen+30 dir=with hold=flat | 514 | 2 | 0.81 | -0.37 | 0.66 | 0.53 / 1.28 | 0.11 / 0.28 / -0.19 | 0.07 | 0.18 | 0.89 | -0.12 | 0.00 | 820 | NO |
| RTY 1 | driver CL ovn |z|>=1.0 RTHopen+30 dir=against hold=flat | 107 | 2 | 1.90 | -0.31 | 1.18 | 0.21 / 1.57 | 0.39 / 0.26 / -0.06 | 0.25 | 0.15 | 0.96 | 0.06 | 0.00 | 179 | NO |
| RTY 2 | driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | 511 | 2 | 1.89 | 0.70 | 1.45 | 0.69 / 1.37 | 0.38 / -0.06 / 0.14 | 0.25 | 0.27 | 1.00 | 0.10 | 0.00 | 817 | NO |
| RTY 3 | driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | 107 | 2 | 1.80 | 0.05 | 1.36 | 0.69 / 1.59 | 0.40 / 0.27 / 0.04 | 0.29 | 0.18 | 1.00 | 0.09 | 0.50 | 179 | NO |
| RTY 4 | driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=120m | 112 | 2 | 1.54 | 0.06 | 0.13 | -1.32 / 0.98 | 0.23 / -1.04 / -0.24 | -0.08 | 0.00 | 0.78 | -0.29 | 0.00 | 172 | NO |
| RTY 5 | driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=120m | 113 | 2 | 1.53 | 0.42 | 0.12 | -1.43 / 1.16 | 0.23 / -0.72 / -0.47 | -0.07 | -0.04 | 0.73 | -0.28 | 0.00 | 180 | NO |
| RTY 6 | driver 6J eur |z|>=0.0 RTHopen+30 dir=with hold=flat | 511 | 2 | 1.48 | -0.63 | 0.64 | -0.73 / 1.37 | 0.25 / -0.50 / 0.07 | 0.06 | -0.16 | 0.93 | -0.11 | 0.00 | 811 | NO |
| RTY 7 | driver 6J eur |z|>=0.0 RTHopen+0 dir=with hold=flat | 511 | 2 | 1.41 | -0.18 | 0.65 | -0.67 / 1.33 | 0.22 / -0.24 / -0.09 | 0.05 | -0.19 | 0.92 | -0.12 | 0.00 | 811 | NO |
| RTY 8 | driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | 511 | 2 | 1.29 | 0.49 | 0.90 | 0.28 / 1.35 | 0.26 / -0.15 / 0.11 | 0.15 | 0.15 | 0.97 | 0.00 | 0.00 | 817 | NO |
| RTY 9 | driver CL eur |z|>=0.0 RTHopen+0 dir=against hold=flat | 513 | 2 | 1.27 | 0.23 | 1.06 | 0.59 / 1.46 | 0.31 / 0.24 / 0.02 | 0.22 | 0.15 | 0.95 | 0.05 | 0.00 | 820 | NO |
| RTY 10 | driver CL asia |z|>=0.0 RTHopen+30 dir=against hold=flat | 504 | 2 | 1.21 | -0.27 | 0.19 | -1.16 / 1.10 | 0.16 / -0.38 / -0.37 | -0.06 | 0.12 | 0.72 | -0.22 | 0.00 | 806 | NO |
| YM 1 | driver 6J eur |z|>=1.0 RTHopen+30 dir=with hold=flat | 138 | 2 | 1.59 | -0.19 | 1.79 | 1.98 / 1.48 | 0.29 / 0.42 / 0.12 | 0.26 | -0.18 | 1.00 | 0.10 | 0.50 | 205 | LEAD(gate3-7 fail: plateau ) |
| YM 2 | driver 6J eur |z|>=1.0 RTHopen+0 dir=with hold=flat | 138 | 2 | 1.57 | -0.23 | 1.72 | 1.77 / 1.31 | 0.28 / 0.30 / 0.23 | 0.26 | 0.05 | 0.99 | 0.09 | 0.50 | 205 | LEAD(gate3-7 fail: plateau ) |
| YM 3 | driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | 511 | 2 | 1.46 | -0.02 | 1.59 | 1.99 / 1.27 | 0.28 / 0.12 / 0.31 | 0.26 | 0.14 | 1.00 | 0.14 | 0.00 | 817 | LEAD(gate3-7 fail: plateau ) |
| YM 4 | driver 6J eur |z|>=0.0 RTHopen+0 dir=with hold=flat | 511 | 2 | 1.23 | -0.42 | 0.69 | -0.38 / 1.34 | 0.19 / -0.31 / -0.01 | 0.05 | 0.01 | 0.90 | -0.11 | 0.00 | 811 | NO |
| YM 5 | driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | 107 | 2 | 1.22 | -0.35 | 1.29 | 1.34 / 1.36 | 0.30 / 0.10 / 0.34 | 0.28 | -0.14 | 1.00 | 0.11 | 0.50 | 179 | LEAD(gate3-7 fail: plateau ) |
| YM 6 | driver 6J eur |z|>=0.0 RTHopen+30 dir=with hold=flat | 511 | 2 | 1.12 | -0.65 | 0.50 | -0.77 / 1.47 | 0.18 / -0.34 / -0.06 | 0.03 | -0.05 | 0.92 | -0.12 | 0.00 | 811 | NO |
| YM 7 | driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | 511 | 2 | 1.11 | -0.01 | 1.33 | 1.92 / 1.45 | 0.20 / 0.14 / 0.37 | 0.21 | -0.21 | 1.00 | 0.10 | 0.00 | 817 | LEAD(gate3-7 fail: plateau ) |
| YM 8 | driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=120m | 112 | 2 | 1.11 | -0.53 | -0.23 | -1.80 / 1.40 | 0.16 / -1.14 / -0.32 | -0.15 | 0.07 | 0.45 | -0.37 | 0.00 | 172 | NO |
| YM 9 | driver CL eur |z|>=0.0 RTHopen+0 dir=against hold=flat | 513 | 2 | 0.97 | -0.31 | 1.21 | 1.59 / 1.48 | 0.24 / 0.43 / 0.13 | 0.24 | -0.19 | 0.98 | 0.10 | 0.00 | 820 | LEAD(gate3-7 fail: plateau ) |
| YM 10 | driver NKD ovn |z|>=0.0 RTHopen+30 dir=with hold=120m | 379 | 2 | 0.95 | 0.20 | 1.15 | 1.67 / 1.17 | 0.13 / 0.15 / 0.25 | 0.14 | 0.14 | 0.99 | 0.00 | 1.00 | 546 | FOUND-CAND |
| GC 1 | driver ES ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | 509 | 2 | 1.25 | -0.43 | -0.51 | -1.77 / 1.51 | 0.17 / -1.98 / -0.53 | -0.35 | -0.29 | 0.23 | -0.67 | 0.00 | 812 | NO |
| GC 2 | driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m | 508 | 2 | 1.18 | 0.23 | -0.58 | -1.74 / 1.21 | 0.17 / -1.32 / -1.39 | -0.47 | 0.17 | 0.35 | -0.83 | 0.00 | 812 | NO |
| GC 3 | driver ES ovn |z|>=0.0 RTHopen+0 dir=against hold=120m | 509 | 2 | 1.09 | -0.30 | -1.18 | -3.09 / 1.27 | 0.18 / -1.71 / -1.46 | -0.53 | 0.20 | 0.05 | -0.78 | 0.00 | 812 | NO |
| GC 4 | driver NKD eur |z|>=0.0 RTHopen+30 dir=with hold=120m | 503 | 2 | 1.06 | -0.71 | 0.03 | -0.58 / 1.42 | 0.14 / -1.47 / -0.30 | -0.25 | 0.40 | 0.63 | -0.54 | 0.00 | 802 | NO |
| GC 5 | driver NQ asia |z|>=0.0 RTHopen+0 dir=against hold=120m | 511 | 2 | 1.05 | -0.11 | -0.51 | -1.49 / 1.23 | 0.14 / -1.38 / -1.26 | -0.46 | 0.23 | 0.30 | -0.84 | 0.00 | 817 | NO |
| GC 6 | driver 6E eur |z|>=1.0 RTHopen+0 dir=with hold=120m | 171 | 2 | 0.99 | -0.72 | 0.63 | 0.44 / 1.29 | 0.16 / -0.80 / -0.02 | -0.03 | 0.30 | 0.93 | -0.30 | 0.50 | 280 | NO |
| GC 7 | driver ZN eur |z|>=0.0 RTHopen+30 dir=against hold=120m | 504 | 2 | 0.97 | -0.75 | 0.81 | 0.89 / 1.01 | 0.10 / 1.30 / -0.39 | 0.11 | -0.25 | 1.00 | -0.18 | 0.50 | 797 | NO |
| GC 8 | driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | 510 | 2 | 0.92 | -0.70 | -0.11 | -0.75 / 1.69 | 0.10 / -0.60 / -0.84 | -0.25 | 0.28 | 0.44 | -0.58 | 0.00 | 815 | NO |
| GC 9 | driver ZN asia |z|>=0.0 RTHopen+0 dir=with hold=flat | 482 | 2 | 0.79 | -0.25 | -0.08 | -0.70 / 1.50 | 0.11 / -0.40 / -0.71 | -0.18 | 0.43 | 0.52 | -0.45 | 0.00 | 770 | NO |
| GC 10 | driver 6E asia |z|>=0.0 RTHopen+30 dir=with hold=flat | 506 | 2 | 0.76 | -0.30 | 0.84 | 1.02 / 1.51 | 0.16 / 0.25 / 0.07 | 0.12 | 0.08 | 0.96 | -0.18 | 0.00 | 811 | NO |
| CL 1 | driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=flat | 113 | 2 | 1.39 | -0.51 | 1.57 | 2.01 / 1.34 | 0.24 / -0.13 / 0.56 | 0.25 | -0.01 | 1.00 | 0.06 | 1.00 | 180 | NO |
| CL 2 | driver ES ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | 510 | 2 | 1.20 | -0.60 | 1.18 | 1.27 / 1.40 | 0.21 / -0.20 / 0.36 | 0.14 | 0.18 | 1.00 | -0.03 | 0.00 | 816 | NO |
| CL 3 | driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=120m | 113 | 2 | 1.13 | -0.51 | 1.04 | 1.08 / 0.89 | 0.18 / -0.35 / 0.13 | 0.08 | 0.15 | 1.00 | -0.09 | 0.75 | 180 | NO |
| CL 4 | driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=flat | 112 | 2 | 1.08 | -0.65 | 0.86 | 0.53 / 1.40 | 0.25 / -0.14 / 0.16 | 0.16 | 0.20 | 0.97 | -0.03 | 1.00 | 172 | NO |
| CL 5 | driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=120m | 112 | 2 | 1.03 | -0.81 | 0.54 | -0.18 / 1.15 | 0.21 / -0.35 / -0.20 | 0.02 | 0.08 | 0.92 | -0.13 | 0.50 | 172 | NO |
| CL 6 | driver GC ovn |z|>=0.0 RTHopen+30 dir=with hold=flat | 510 | 2 | 1.02 | -0.20 | 0.98 | 1.01 / 1.08 | 0.16 / -0.05 / 0.46 | 0.13 | -0.32 | 1.00 | -0.02 | 0.00 | 815 | NO |
| CL 7 | driver 6J ovn |z|>=1.0 RTHopen+30 dir=with hold=flat | 144 | 2 | 0.99 | -0.28 | 0.57 | -0.23 / 1.37 | 0.13 / -0.15 / 0.04 | 0.03 | -0.24 | 0.88 | -0.11 | 0.50 | 221 | NO |
| CL 8 | driver GC asia |z|>=0.0 RTHopen+30 dir=with hold=flat | 512 | 2 | 0.97 | -0.54 | 1.06 | 1.19 / 1.13 | 0.19 / 0.15 / 0.50 | 0.20 | -0.20 | 0.99 | 0.02 | 0.00 | 817 | LEAD |
| CL 9 | driver NKD eur |z|>=0.0 RTHopen+0 dir=against hold=flat | 505 | 2 | 0.97 | -0.61 | 1.02 | 1.20 / 1.29 | 0.15 / -0.18 / 0.39 | 0.11 | 0.13 | 1.00 | -0.05 | 0.00 | 805 | NO |
| CL 10 | driver NQ eur |z|>=1.0 RTHopen+30 dir=against hold=flat | 113 | 2 | 0.93 | -0.44 | 1.11 | 1.53 / 1.29 | 0.11 / -0.10 / 0.43 | 0.14 | -0.05 | 0.99 | -0.04 | 1.00 | 180 | NO |
| ZN 1 | driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=flat | 112 | 2 | 0.61 | -0.20 | -0.00 | -1.06 / 0.41 | 0.07 / -0.04 / -0.21 | -0.15 | 0.32 | 0.90 | -0.21 | 0.00 | 172 | NO |
| ZN 2 | driver NKD eur |z|>=0.0 RTHopen+0 dir=against hold=flat | 505 | 2 | 0.48 | -1.77 | -0.51 | -2.47 / 0.05 | 0.02 / -0.40 / -0.37 | -0.44 | 0.30 | 0.93 | -0.31 | 0.00 | 802 | NO |
| ZN 3 | driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=flat | 113 | 2 | 0.41 | -0.28 | -0.13 | -0.83 / 0.39 | 0.00 / -0.04 / -0.15 | -0.19 | 0.45 | 0.87 | -0.24 | 0.00 | 180 | NO |
| ZN 4 | driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=120m | 112 | 2 | 0.31 | -0.64 | -0.51 | -1.79 / -0.89 | 0.01 / -0.33 / -0.31 | -0.32 | -0.08 | 1.00 | -0.32 | 0.00 | 172 | NO |
| ZN 5 | driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=120m | 113 | 2 | 0.17 | -0.90 | -0.54 | -1.47 / -1.20 | -0.03 / -0.13 / -0.35 | -0.34 | 0.42 | 1.00 | -0.31 | 0.00 | 180 | NO |
| ZN 6 (diag) | driver CL asia |z|>=1.0 RTHopen+30 dir=against hold=flat | 34 | 2 | 0.93 | -0.21 | -0.12 | -2.08 / 0.84 | 0.13 / -0.32 / -0.55 | -0.18 | 0.17 | 0.76 | -0.27 | 0.00 | 69 S | diag |
| ZN 7 (diag) | driver CL asia |z|>=1.0 RTHopen+0 dir=against hold=flat | 35 | 2 | 0.83 | -0.05 | -0.29 | -2.14 / 0.67 | 0.12 / -0.34 / -0.67 | -0.21 | -0.00 | 0.62 | -0.31 | 0.00 | 69 S | diag |
| ZN 8 (diag) | driver 6E ovn |z|>=1.0 RTHopen+30 dir=against hold=flat | 95 | 1 | 0.60 | -1.22 | 0.08 | -1.08 / 0.64 | 0.12 / 0.06 / -0.24 | -0.14 | -0.27 | 0.90 | -0.15 | 0.00 | 156 | diag |
| BTC 1 | driver CL eur |z|>=1.0 RTHopen+30 dir=against hold=flat | 166 | 2 | 1.77 | -1.22 | 0.70 | -0.96 / 1.10 | 0.36 / -0.15 / -0.25 | 0.13 | -0.34 | 0.94 | -0.04 | 0.50 | 274 | NO |
| BTC 2 | driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | 489 | 2 | 1.73 | -0.26 | 0.62 | -1.22 / 1.27 | 0.31 / -0.38 / -0.19 | 0.08 | -0.19 | 0.91 | -0.09 | 0.00 | 760 | NO |
| BTC 3 | driver CL eur |z|>=1.0 RTHopen+0 dir=against hold=flat | 153 | 2 | 1.51 | -1.07 | 0.49 | -1.20 / 1.45 | 0.31 / -0.38 / -0.14 | 0.09 | -0.06 | 0.81 | -0.08 | 0.50 | 251 | NO |
| BTC 4 | driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m | 430 | 2 | 1.31 | -0.04 | 1.75 | 2.29 / 1.39 | 0.30 / 0.58 / 0.12 | 0.31 | -0.24 | 1.00 | 0.15 | 0.50 | 663 | LEAD(gate3-7 fail: plateau ) |
| BTC 5 | driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | 438 | 2 | 1.24 | 0.37 | 0.30 | -1.32 / 1.36 | 0.20 / -0.50 / -0.16 | 0.00 | 0.03 | 0.74 | -0.16 | 0.00 | 677 | NO |
| BTC 6 | driver GC ovn |z|>=1.0 RTHopen+30 dir=against hold=120m | 115 | 2 | 1.21 | -0.71 | 1.14 | 0.99 / 1.38 | 0.21 / 0.51 / -0.01 | 0.18 | 0.18 | 0.99 | 0.02 | 0.50 | 190 | NO |
| BTC 7 | driver 6E eur |z|>=0.0 RTHopen+0 dir=with hold=120m | 430 | 2 | 1.11 | 0.20 | 0.78 | 0.19 / 1.30 | 0.21 / -0.10 / -0.11 | 0.07 | 0.46 | 0.93 | -0.08 | 0.50 | 665 | NO |
| BTC 8 | driver CL ovn |z|>=1.0 RTHopen+30 dir=against hold=flat | 103 | 2 | 1.10 | -0.72 | 0.57 | -0.37 / 1.52 | 0.22 / 0.13 / -0.14 | 0.12 | -0.25 | 0.85 | -0.05 | 0.50 | 169 | NO |
| BTC 9 | driver GC ovn |z|>=1.0 RTHopen+30 dir=against hold=flat | 118 | 2 | 1.07 | -0.74 | 0.98 | 0.61 / 1.02 | 0.19 / 0.20 / 0.03 | 0.14 | 0.40 | 0.98 | -0.03 | 0.50 | 194 | NO |
| BTC 10 | driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=flat | 435 | 2 | 1.04 | 0.64 | 1.07 | 0.97 / 1.21 | 0.23 / 0.03 / 0.13 | 0.18 | -0.28 | 0.98 | 0.01 | 0.00 | 675 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 75 |
| diagnostic cells read | 3 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 1 / 10 / 9 / 9 |
| all-in uplift @20% > 0 (all scored) | 56 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 22 |
| standalone pair-window Sharpe above own random-entry null p95 | 41 |
| worst-decile corr <= +0.30 | 63 |
| plateau >= 0.75 | 12 |
| all-in uplift at 2x slippage >= +0.10 | 37 |
| small-sample (<100 trades pair window) | 2 |
| gate_add PASS at any share (non-diag) | 21 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m | clean | 1.35 | 2.57 | -98094 | -84101 | 474301 | -119716 | 2.58 | 46.7 | 1.76 | -80994 | 267857 | -90576 |
| BTC driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m | H1 | 4.06 | 14.96 | -74045 | -64542 | 219586 | -82871 | 6.03 | 32.1 | 3.40 | -78252 | 129563 | -80232 |
| BTC driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m | H2 | 0.75 | 1.32 | -119606 | -99236 | 247826 | -127344 | 1.04 | 47.2 | 2.41 | -86490 | 215087 | -92947 |
| BTC driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m | all | 1.75 | 3.67 | -101183 | -86699 | 474301 | -127344 | 5.91 | 44.0 | 2.19 | -82293 | 267857 | -92947 |
| CL driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=flat | clean | 1.27 | 2.35 | -101650 | -90346 | 399490 | -120133 | 2.92 | 27.6 | 1.70 | -86101 | 267625 | -101746 |
| CL driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=flat | H1 | 0.06 | 0.08 | -113256 | -102503 | 213754 | -126451 | 0.05 | 39.3 | 2.70 | -77542 | 147818 | -78818 |
| CL driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=flat | H2 | 2.94 | 6.93 | -152896 | -100052 | 272301 | -240942 | 5.68 | 25.0 | 2.85 | -92731 | 188994 | -102938 |
| CL driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=flat | all | 1.57 | 3.02 | -129362 | -101477 | 399490 | -240942 | 6.82 | 28.6 | 2.13 | -86998 | 267625 | -102938 |
| ES driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | clean | 0.97 | 1.79 | -118463 | -89157 | 256130 | -185938 | 3.46 | 41.9 | 1.64 | -79771 | 240371 | -86083 |
| ES driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | H1 | 0.43 | 0.74 | -94930 | -77647 | 162608 | -140147 | 0.56 | 50.0 | 2.89 | -78330 | 137697 | -82921 |
| ES driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | H2 | 1.89 | 3.52 | -61129 | -53093 | 151410 | -62850 | 2.60 | 41.7 | 2.48 | -85696 | 221519 | -88525 |
| ES driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | all | 1.02 | 1.85 | -111065 | -82756 | 256130 | -185938 | 5.35 | 42.9 | 2.02 | -81491 | 240371 | -88525 |
| GC driver ZN eur |z|>=0.0 RTHopen+30 dir=against hold=120m | clean | 0.95 | 1.60 | -110277 | -94311 | 627629 | -137943 | 1.37 | 43.8 | 1.56 | -91729 | 302633 | -104342 |
| GC driver ZN eur |z|>=0.0 RTHopen+30 dir=against hold=120m | H1 | 2.37 | 6.19 | -247672 | -194812 | 428267 | -277622 | 4.11 | 35.7 | 4.13 | -71014 | 154952 | -81339 |
| GC driver ZN eur |z|>=0.0 RTHopen+30 dir=against hold=120m | H2 | -0.33 | -0.46 | -391095 | -309361 | 1625291 | -496935 | -0.18 | 52.8 | 1.91 | -121178 | 270116 | -125307 |
| GC driver ZN eur |z|>=0.0 RTHopen+30 dir=against hold=120m | all | 0.81 | 1.39 | -246473 | -183145 | 1625291 | -496935 | 1.43 | 44.6 | 2.02 | -98642 | 302633 | -125307 |
| NQ driver GC asia |z|>=1.0 RTHopen+30 dir=against hold=120m | clean | 1.27 | 2.60 | -98313 | -82828 | 221199 | -127997 | 5.22 | 31.4 | 1.62 | -81133 | 299673 | -92692 |
| NQ driver GC asia |z|>=1.0 RTHopen+30 dir=against hold=120m | H1 | 4.76 | 26.01 | -52483 | -34989 | 103510 | -75904 | 14.99 | 7.1 | 3.91 | -76726 | 133694 | -78287 |
| NQ driver GC asia |z|>=1.0 RTHopen+30 dir=against hold=120m | H2 | 0.56 | 0.92 | -210439 | -166419 | 461277 | -234720 | 0.68 | 33.3 | 2.31 | -97533 | 237656 | -101003 |
| NQ driver GC asia |z|>=1.0 RTHopen+30 dir=against hold=120m | all | 1.61 | 3.24 | -135815 | -108176 | 461277 | -234720 | 6.54 | 28.0 | 2.12 | -85167 | 299673 | -101003 |
| RTY driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | clean | 1.90 | 4.19 | -99898 | -72169 | 314779 | -163772 | 5.44 | 25.7 | 1.86 | -84774 | 242004 | -105319 |
| RTY driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | H1 | 0.79 | 1.14 | -182406 | -137775 | 314948 | -266437 | 0.79 | 28.6 | 3.10 | -72422 | 182567 | -76585 |
| RTY driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | H2 | 0.60 | 0.98 | -144134 | -125665 | 324507 | -167500 | 0.74 | 41.7 | 2.33 | -95013 | 217425 | -102358 |
| RTY driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | all | 1.36 | 2.42 | -140687 | -103468 | 324507 | -266437 | 6.78 | 29.8 | 2.15 | -86414 | 242004 | -105319 |
| YM driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | clean | 1.25 | 1.75 | -135727 | -96380 | 591633 | -377415 | 1.91 | 23.8 | 1.76 | -81144 | 254666 | -87840 |
| YM driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | H1 | 0.71 | 0.98 | -179804 | -143978 | 275857 | -252205 | 0.76 | 28.6 | 2.93 | -79672 | 182776 | -91398 |
| YM driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | H2 | 1.93 | 3.89 | -108271 | -81218 | 176769 | -118140 | 3.41 | 33.3 | 2.63 | -79421 | 217425 | -80940 |
| YM driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | all | 1.29 | 1.89 | -148308 | -104523 | 591633 | -377415 | 3.28 | 26.8 | 2.15 | -81918 | 254666 | -91398 |
| ZN driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=flat | clean | 0.58 | 0.78 | -168992 | -124920 | 517426 | -283637 | 1.03 | 27.6 | 1.53 | -90487 | 313117 | -112604 |
| ZN driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=flat | H1 | -0.36 | -0.59 | -130145 | -114934 | 540581 | -134293 | -0.18 | 35.7 | 2.79 | -77642 | 157951 | -83420 |
| ZN driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=flat | H2 | -1.94 | -2.00 | -153652 | -121655 | 589010 | -153652 | -0.74 | 30.6 | 2.09 | -82536 | 228884 | -82548 |
| ZN driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=flat | all | -0.00 | -0.00 | -162428 | -127415 | 862283 | -283637 | -0.00 | 29.2 | 1.83 | -87935 | 313117 | -112604 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | -14.7 | 16.3 | 23.2 | 41.7 | 17.5 / 25.2 | 19.7 / 28.6 | NO |
| NQ driver GC asia |z|>=1.0 RTHopen+30 dir=against hold=120m | 3.7 | -8.5 | 14.3 | 19.5 | 8.2 / 18.5 | 30.0 / 31.7 | NO |
| RTY driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | -5.4 | -16.7 | 12.2 | 44.1 | -17.7 / 17.2 | 24.9 / 28.4 | NO |
| YM driver 6J eur |z|>=1.0 RTHopen+30 dir=with hold=flat | -2.9 | 14.9 | 25.9 | 45.2 | 31.7 / 31.2 | 10.2 / 14.9 | INSURANCE |
| YM driver 6J eur |z|>=1.0 RTHopen+0 dir=with hold=flat | -2.7 | 5.4 | 24.2 | 47.6 | 16.8 / 27.6 | 0.3 / 12.1 | INSURANCE |
| YM driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | -8.3 | 8.5 | 20.7 | 43.6 | 14.4 / 21.6 | 3.5 / 11.7 | NO |
| GC driver ZN eur |z|>=0.0 RTHopen+30 dir=against hold=120m | -4.0 | -52.7 | -22.2 | 8.6 | -15.9 / 3.8 | -29.5 / -1.9 | NO |
| CL driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=flat | 0.4 | -34.0 | 11.7 | 34.5 | -10.5 / 14.8 | 29.0 / 30.1 | NO |
| ZN driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=flat | -30.0 | -25.3 | 4.7 | 12.3 | -26.3 / -2.2 | 20.2 / 26.7 | NO |
| BTC driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m | 1.3 | 6.1 | 21.6 | 31.6 | 9.4 / 21.7 | 26.3 / 28.8 | INSURANCE |

INSURANCE count: 3.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 driver 6J asia |z|>=0.0 RTHopen+30 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2638 | 8.3 | -21.1 | -6.8 | 29.4 | 0.18 / -0.46 / -0.15 | 106.5 / 77.1 |
| ES 2 driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 566 | 4.7 | -24.6 | -10.9 | 29.4 | 0.04 / -0.22 / -0.10 | 177.4 / 148.1 |
| ES 3 driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2636 | 20.8 | -8.6 | 5.6 | 29.4 | 0.26 / -0.10 / 0.07 | 199.3 / 170.0 |
| ES 4 driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2642 | 18.2 | -11.2 | 3.0 | 29.4 | 0.23 / -0.14 / 0.04 | 173.9 / 144.6 |
| ES 5 driver NQ eur |z|>=1.0 RTHopen+30 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 566 | 15.3 | -14.1 | -0.4 | 29.4 | 0.15 / -0.13 / -0.00 | 166.4 / 137.0 |
| ES 6 driver 6J eur |z|>=0.0 RTHopen+30 dir=with hold=flat | negative pre-2023 | 2656 | -28.3 | -57.7 | -43.5 | 29.4 | -0.35 / -0.72 / -0.54 | 143.7 / 114.4 |
| ES 7 driver 6E ovn |z|>=0.0 RTHopen+0 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 2655 | 11.0 | -18.3 | -4.1 | 29.4 | 0.22 / -0.36 / -0.08 | 88.9 / 59.5 |
| ES 8 driver GC ovn |z|>=1.0 RTHopen+30 dir=against hold=120m | negative pre-2023 | 532 | -1.8 | -31.1 | -16.7 | 29.4 | -0.02 / -0.31 / -0.16 | 160.4 / 131.1 |
| ES 9 driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | negative pre-2023 | 427 | -74.7 | -104.1 | -90.5 | 29.4 | -0.38 / -0.53 / -0.46 | 285.3 / 255.9 |
| ES 10 driver GC asia |z|>=1.0 RTHopen+30 dir=against hold=120m | negative pre-2023 | 397 | -58.0 | -87.3 | -73.3 | 29.4 | -0.50 / -0.75 / -0.63 | 169.5 / 140.1 |
| NQ 1 driver 6J asia |z|>=0.0 RTHopen+30 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2638 | 12.1 | -2.2 | 6.3 | 14.4 | 0.16 / -0.03 / 0.08 | 181.3 / 166.9 |
| NQ 2 driver GC ovn |z|>=1.0 RTHopen+30 dir=against hold=120m | positive pre-2023 | 532 | 32.4 | 18.1 | 26.7 | 14.4 | 0.19 / 0.11 / 0.16 | 355.5 / 341.1 |
| NQ 3 driver GC asia |z|>=1.0 RTHopen+30 dir=against hold=120m | negative pre-2023 | 397 | -57.8 | -72.2 | -63.7 | 14.4 | -0.30 / -0.38 / -0.33 | 421.1 / 406.7 |
| NQ 4 driver 6E ovn |z|>=0.0 RTHopen+0 dir=with hold=120m | positive pre-2023 | 2655 | 16.4 | 2.0 | 10.6 | 14.4 | 0.20 / 0.02 / 0.13 | 183.2 / 168.9 |
| NQ 5 driver 6E ovn |z|>=0.0 RTHopen+0 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2655 | 0.6 | -13.8 | -5.2 | 14.4 | 0.00 / -0.11 / -0.04 | 261.1 / 246.7 |
| NQ 6 driver ZN asia |z|>=0.0 RTHopen+0 dir=against hold=120m | positive pre-2023 | 2525 | 21.2 | 6.9 | 15.4 | 14.4 | 0.23 / 0.07 / 0.16 | 176.4 / 162.1 |
| NQ 7 driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | positive pre-2023 | 2642 | 21.1 | 6.7 | 15.3 | 14.4 | 0.18 / 0.06 / 0.13 | 248.7 / 234.4 |
| NQ 8 driver 6E ovn |z|>=0.0 RTHopen+30 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 2662 | 0.3 | -14.0 | -5.5 | 14.4 | 0.00 / -0.19 / -0.08 | 141.6 / 127.3 |
| NQ 9 driver 6J asia |z|>=0.0 RTHopen+0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2630 | 10.3 | -4.1 | 4.5 | 14.4 | 0.11 / -0.04 / 0.05 | 153.7 / 139.3 |
| NQ 10 driver 6E ovn |z|>=0.0 RTHopen+30 dir=with hold=flat | negative pre-2023 | 2662 | -29.3 | -43.7 | -35.1 | 14.4 | -0.25 / -0.37 / -0.30 | 203.3 / 188.9 |
| RTY 1 driver CL ovn |z|>=1.0 RTHopen+30 dir=against hold=flat | negative pre-2023 | 280 | -29.5 | -43.9 | -41.5 | 14.4 | -0.21 / -0.31 / -0.29 | 274.0 / 259.7 |
| RTY 2 driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 1504 | 62.5 | 48.1 | 50.3 | 14.4 | 0.90 / 0.70 / 0.73 | 175.1 / 160.8 |
| RTY 3 driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 274 | 18.1 | 3.7 | 6.0 | 14.4 | 0.14 / 0.05 / 0.06 | 317.7 / 303.3 |
| RTY 4 driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=120m | positive pre-2023 | 335 | 18.1 | 3.7 | 5.8 | 14.4 | 0.21 / 0.06 / 0.08 | 140.4 / 126.0 |
| RTY 5 driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=120m | positive pre-2023 | 351 | 56.8 | 42.5 | 44.6 | 14.4 | 0.56 / 0.42 / 0.44 | 154.6 / 140.3 |
| RTY 6 driver 6J eur |z|>=0.0 RTHopen+30 dir=with hold=flat | negative pre-2023 | 1524 | -22.9 | -37.3 | -35.0 | 14.4 | -0.39 / -0.63 / -0.59 | 110.9 / 96.5 |
| RTY 7 driver 6J eur |z|>=0.0 RTHopen+0 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 1514 | 1.9 | -12.4 | -10.2 | 14.4 | 0.04 / -0.18 / -0.15 | 116.7 / 102.4 |
| RTY 8 driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | positive pre-2023 | 1513 | 44.2 | 29.9 | 32.1 | 14.4 | 0.72 / 0.49 / 0.52 | 111.6 / 97.2 |
| RTY 9 driver CL eur |z|>=0.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 1520 | 29.8 | 15.4 | 17.7 | 14.4 | 0.44 / 0.23 / 0.27 | 112.3 / 97.9 |
| RTY 10 driver CL asia |z|>=0.0 RTHopen+30 dir=against hold=flat | negative pre-2023 | 1504 | -2.2 | -16.5 | -14.3 | 14.4 | -0.04 / -0.27 / -0.23 | 87.3 / 72.9 |
| YM 1 driver 6J eur |z|>=1.0 RTHopen+30 dir=with hold=flat | negative pre-2023 | 629 | -12.5 | -26.8 | -21.5 | 14.4 | -0.09 / -0.19 / -0.16 | 293.1 / 278.7 |
| YM 2 driver 6J eur |z|>=1.0 RTHopen+0 dir=with hold=flat | negative pre-2023 | 628 | -19.7 | -34.0 | -28.7 | 14.4 | -0.13 / -0.23 / -0.19 | 298.1 / 283.8 |
| YM 3 driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2638 | 12.6 | -1.8 | 4.0 | 14.4 | 0.20 / -0.02 / 0.07 | 178.8 / 164.4 |
| YM 4 driver 6J eur |z|>=0.0 RTHopen+0 dir=with hold=flat | negative pre-2023 | 2648 | -14.2 | -28.6 | -22.9 | 14.4 | -0.21 / -0.42 / -0.33 | 134.6 / 120.2 |
| YM 5 driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat | negative pre-2023 | 430 | -40.5 | -54.8 | -49.4 | 14.4 | -0.25 / -0.35 / -0.31 | 284.0 / 269.7 |
| YM 6 driver 6J eur |z|>=0.0 RTHopen+30 dir=with hold=flat | negative pre-2023 | 2653 | -25.7 | -40.0 | -34.3 | 14.4 | -0.42 / -0.65 / -0.56 | 115.0 / 100.7 |
| YM 7 driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2642 | 13.4 | -0.9 | 4.8 | 14.4 | 0.22 / -0.01 / 0.08 | 127.7 / 113.4 |
| YM 8 driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=120m | negative pre-2023 | 525 | -34.2 | -48.6 | -43.2 | 14.4 | -0.37 / -0.53 / -0.47 | 140.2 / 125.8 |
| YM 9 driver CL eur |z|>=0.0 RTHopen+0 dir=against hold=flat | negative pre-2023 | 2662 | -4.2 | -18.6 | -12.9 | 14.4 | -0.07 / -0.31 / -0.21 | 106.8 / 92.4 |
| YM 10 driver NKD ovn |z|>=0.0 RTHopen+30 dir=with hold=120m | positive pre-2023 | 2053 | 22.1 | 7.8 | 13.4 | 14.4 | 0.57 / 0.20 / 0.34 | 61.9 / 47.5 |
| GC 1 driver ES ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | negative pre-2023 | 2620 | -5.1 | -29.5 | -19.7 | 24.4 | -0.07 / -0.43 / -0.28 | 178.7 / 154.3 |
| GC 2 driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m | positive pre-2023 | 2603 | 36.1 | 11.7 | 21.5 | 24.4 | 0.72 / 0.23 / 0.43 | 117.0 / 92.6 |
| GC 3 driver ES ovn |z|>=0.0 RTHopen+0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2619 | 9.1 | -15.3 | -5.5 | 24.4 | 0.19 / -0.30 / -0.10 | 98.1 / 73.7 |
| GC 4 driver NKD eur |z|>=0.0 RTHopen+30 dir=with hold=120m | negative pre-2023 | 2562 | -10.0 | -34.3 | -24.6 | 24.4 | -0.21 / -0.71 / -0.51 | 95.9 / 71.5 |
| GC 5 driver NQ asia |z|>=0.0 RTHopen+0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 2628 | 19.7 | -4.7 | 5.1 | 24.4 | 0.40 / -0.11 / 0.10 | 106.0 / 81.7 |
| GC 6 driver 6E eur |z|>=1.0 RTHopen+0 dir=with hold=120m | negative pre-2023 | 791 | -45.6 | -69.9 | -60.5 | 24.4 | -0.47 / -0.72 / -0.63 | 165.6 / 141.3 |
| GC 7 driver ZN eur |z|>=0.0 RTHopen+30 dir=against hold=120m | negative pre-2023 | 2574 | -10.3 | -34.7 | -24.9 | 24.4 | -0.22 / -0.75 / -0.54 | 91.4 / 67.1 |
| GC 8 driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | negative pre-2023 | 2614 | -18.7 | -43.0 | -33.2 | 24.4 | -0.30 / -0.70 / -0.54 | 110.2 / 85.9 |
| GC 9 driver ZN asia |z|>=0.0 RTHopen+0 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2508 | 5.9 | -18.5 | -8.7 | 24.4 | 0.08 / -0.25 / -0.12 | 118.5 / 94.1 |
| GC 10 driver 6E asia |z|>=0.0 RTHopen+30 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2604 | 4.2 | -20.1 | -10.3 | 24.4 | 0.06 / -0.30 / -0.16 | 105.7 / 81.3 |
| CL 1 driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=flat | negative pre-2023 | 566 | -59.4 | -83.8 | -80.9 | 24.4 | -0.36 / -0.51 / -0.49 | 196.8 / 172.5 |
| CL 2 driver ES ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | negative pre-2023 | 2639 | -19.3 | -43.7 | -41.1 | 24.4 | -0.26 / -0.60 / -0.56 | 99.3 / 74.9 |
| CL 3 driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=120m | negative pre-2023 | 566 | -36.3 | -60.6 | -57.8 | 24.4 | -0.30 / -0.51 / -0.48 | 121.4 / 97.1 |
| CL 4 driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=flat | negative pre-2023 | 523 | -89.1 | -113.4 | -110.7 | 24.4 | -0.51 / -0.65 / -0.63 | 180.4 / 156.0 |
| CL 5 driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=120m | negative pre-2023 | 523 | -79.3 | -103.6 | -100.9 | 24.4 | -0.62 / -0.81 / -0.79 | 125.2 / 100.8 |
| CL 6 driver GC ovn |z|>=0.0 RTHopen+30 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2644 | 11.4 | -13.0 | -10.4 | 24.4 | 0.17 / -0.20 / -0.16 | 86.3 / 61.9 |
| CL 7 driver 6J ovn |z|>=1.0 RTHopen+30 dir=with hold=flat | negative pre-2023 | 602 | -18.6 | -43.0 | -39.4 | 24.4 | -0.12 / -0.28 / -0.25 | 166.0 / 141.6 |
| CL 8 driver GC asia |z|>=0.0 RTHopen+30 dir=with hold=flat | negative pre-2023 | 2627 | -9.0 | -33.4 | -30.8 | 24.4 | -0.14 / -0.54 / -0.50 | 88.2 / 63.8 |
| CL 9 driver NKD eur |z|>=0.0 RTHopen+0 dir=against hold=flat | negative pre-2023 | 2585 | -18.9 | -43.3 | -40.6 | 24.4 | -0.26 / -0.61 / -0.57 | 89.9 / 65.5 |
| CL 10 driver NQ eur |z|>=1.0 RTHopen+30 dir=against hold=flat | negative pre-2023 | 566 | -40.7 | -65.0 | -62.2 | 24.4 | -0.27 / -0.44 / -0.42 | 124.9 / 100.5 |
| ZN 1 driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 523 | 26.2 | -9.4 | -14.5 | 35.6 | 0.58 / -0.20 / -0.32 | 62.5 / 26.9 |
| ZN 2 driver NKD eur |z|>=0.0 RTHopen+0 dir=against hold=flat | negative pre-2023 | 2580 | -1.8 | -37.5 | -42.6 | 35.6 | -0.09 / -1.77 / -2.01 | 45.0 / 9.3 |
| ZN 3 driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 564 | 23.1 | -12.5 | -17.7 | 35.6 | 0.51 / -0.28 / -0.39 | 49.1 / 13.5 |
| ZN 4 driver ES eur |z|>=1.0 RTHopen+0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 523 | 13.4 | -22.2 | -27.4 | 35.6 | 0.40 / -0.64 / -0.78 | 45.2 / 9.6 |
| ZN 5 driver NQ eur |z|>=1.0 RTHopen+0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 564 | 7.3 | -28.4 | -33.6 | 35.6 | 0.23 / -0.90 / -1.06 | 38.7 / 3.1 |
| ZN 6 (diag) driver CL asia |z|>=1.0 RTHopen+30 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 186 | 20.9 | -14.7 | -20.3 | 35.6 | 0.30 / -0.21 / -0.30 | 118.1 / 82.5 |
| ZN 7 (diag) driver CL asia |z|>=1.0 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 187 | 31.9 | -3.7 | -9.3 | 35.6 | 0.46 / -0.05 / -0.14 | 112.1 / 76.4 |
| ZN 8 (diag) driver 6E ovn |z|>=1.0 RTHopen+30 dir=against hold=flat | negative pre-2023 | 449 | -20.8 | -56.5 | -61.7 | 35.6 | -0.46 / -1.22 / -1.33 | 60.9 / 25.2 |
| BTC 1 driver CL eur |z|>=1.0 RTHopen+30 dir=against hold=flat | negative pre-2023 | 113 | -411.7 | -466.1 | -433.4 | 54.4 | -1.08 / -1.22 / -1.14 | 1288.3 / 1233.9 |
| BTC 2 driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat | negative pre-2023 | 362 | -5.1 | -59.5 | -27.0 | 54.4 | -0.03 / -0.26 / -0.12 | 853.3 / 798.9 |
| BTC 3 driver CL eur |z|>=1.0 RTHopen+0 dir=against hold=flat | negative pre-2023 | 105 | -353.1 | -407.5 | -374.7 | 54.4 | -0.93 / -1.07 / -0.98 | 1213.7 / 1159.4 |
| BTC 4 driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 327 | 45.5 | -8.9 | 23.7 | 54.4 | 0.32 / -0.04 / 0.18 | 490.5 / 436.1 |
| BTC 5 driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 334 | 159.8 | 105.4 | 138.0 | 54.4 | 0.57 / 0.37 / 0.49 | 721.5 / 667.1 |
| BTC 6 driver GC ovn |z|>=1.0 RTHopen+30 dir=against hold=120m | negative pre-2023 | 63 | -223.0 | -277.4 | -244.7 | 54.4 | -0.57 / -0.71 / -0.62 | 829.3 / 775.0 |
| BTC 7 driver 6E eur |z|>=0.0 RTHopen+0 dir=with hold=120m | positive pre-2023 | 334 | 83.5 | 29.2 | 61.7 | 54.4 | 0.53 / 0.20 / 0.40 | 397.3 / 342.9 |
| BTC 8 driver CL ovn |z|>=1.0 RTHopen+30 dir=against hold=flat | negative pre-2023 | 74 | -301.0 | -355.4 | -323.3 | 54.4 | -0.62 / -0.72 / -0.66 | 1404.6 / 1350.3 |
| BTC 9 driver GC ovn |z|>=1.0 RTHopen+30 dir=against hold=flat | negative pre-2023 | 65 | -483.1 | -537.4 | -504.9 | 54.4 | -0.67 / -0.74 / -0.70 | 1190.5 / 1136.1 |
| BTC 10 driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 331 | 223.0 | 168.6 | 201.2 | 54.4 | 0.84 / 0.64 / 0.76 | 569.1 / 514.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 55 cells pass the clean rule against a replicate mean of 46.6 (p(count) = 0.10, p(top) = 0.60); CL: 28 cells pass the clean rule against a replicate mean of 23.1 (p(count) = 0.16, p(top) = 0.39); ES: 29 cells pass the clean rule against a replicate mean of 28.6 (p(count) = 0.48, p(top) = 0.94); GC: 33 cells pass the clean rule against a replicate mean of 29.5 (p(count) = 0.32, p(top) = 0.85); NQ: 35 cells pass the clean rule against a replicate mean of 44.2 (p(count) = 0.94, p(top) = 0.99); RTY: 56 cells pass the clean rule against a replicate mean of 38.1 (p(count) = 0.00, p(top) = 0.00); YM: 46 cells pass the clean rule against a replicate mean of 38.3 (p(count) = 0.11, p(top) = 0.48); ZN: 5 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.04, p(top) = 0.52).
- Of 75 selected cells, 10 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.34 (BTC driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m); bootstrap lower bound > 0 for 22 cells; plateau >= 0.75 for 12; 2x-slippage all-in uplift >= +0.10 for 37; gate_add PASS at some share: 21 (cell-share pairs).
- Gate-3 cell NQ driver 6J asia |z|>=0.0 RTHopen+0 dir=against hold=120m: uplift +0.12/+0.22/+0.49, boot lo -0.00, plateau 1.00, 2x-slip +0.20, wd corr -0.66, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- Gate-3 cell YM driver 6J eur |z|>=1.0 RTHopen+30 dir=with hold=flat: uplift +0.29/+0.42/+0.12, boot lo +0.10, plateau 0.50, 2x-slip +0.26, wd corr -0.18, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell YM driver 6J eur |z|>=1.0 RTHopen+0 dir=with hold=flat: uplift +0.28/+0.30/+0.23, boot lo +0.09, plateau 0.50, 2x-slip +0.26, wd corr +0.05, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell YM driver CL ovn |z|>=0.0 RTHopen+0 dir=against hold=flat: uplift +0.28/+0.12/+0.31, boot lo +0.14, plateau 0.00, 2x-slip +0.26, wd corr +0.14, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- Gate-3 cell YM driver CL ovn |z|>=1.0 RTHopen+0 dir=against hold=flat: uplift +0.30/+0.10/+0.34, boot lo +0.11, plateau 0.50, 2x-slip +0.28, wd corr -0.14, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell YM driver CL ovn |z|>=0.0 RTHopen+30 dir=against hold=flat: uplift +0.20/+0.14/+0.37, boot lo +0.10, plateau 0.00, 2x-slip +0.21, wd corr -0.21, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- Gate-3 cell YM driver CL eur |z|>=0.0 RTHopen+0 dir=against hold=flat: uplift +0.24/+0.43/+0.13, boot lo +0.10, plateau 0.00, 2x-slip +0.24, wd corr -0.19, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell YM driver NKD ovn |z|>=0.0 RTHopen+30 dir=with hold=120m: uplift +0.13/+0.15/+0.25, boot lo +0.00, plateau 1.00, 2x-slip +0.14, wd corr +0.14, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell CL driver GC asia |z|>=0.0 RTHopen+30 dir=with hold=flat: uplift +0.19/+0.15/+0.50, boot lo +0.02, plateau 0.00, 2x-slip +0.20, wd corr -0.20, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell BTC driver ES asia |z|>=0.0 RTHopen+0 dir=against hold=120m: uplift +0.30/+0.58/+0.12, boot lo +0.15, plateau 0.50, 2x-slip +0.31, wd corr -0.24, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 37, 'gross-positive, cost-negative pre-2023': 23, 'positive pre-2023': 15}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_9.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw9/ (`SW9_CO_all_selected_scored.csv`).

## 7. Verification of the one automatic FOUND-CANDIDATE: YM, driver NKD overnight (18:00-08:20 ET) move, RTH open + 30 min, WITH the NKD direction, hold 120 min (cell 37)
Verdict: **LEAD (weak margins), not FOUND-PENDING.**
- Passes at 20% share only (gate_add 10/30/50% = NO). Additive uplift clean/H1/H2 +0.13/+0.15/+0.25 (clean barely above +0.10), bootstrap 90% lower bound +0.002, worst week +8.9%, standalone pair-window Sharpe 1.15 vs own null p95 0.66 (rank 0.99), H1+H2 standalone 1.67 vs null p95 1.17 (rank 0.98), 2x-slip +0.14, wd corr +0.14, 546 pair-window trades, plateau 2 of 2 neighbours (only hold is a non-zero numeric parameter besides the delay; weak test).
- ERA: pre-2023 weekly Sharpe +0.20 net (2,053 trades, +$7.8 net per trade, +$22.1 gross) = positive but small; per-year standalone Sharpe 2013-2017 -0.9..-1.5, 2018-2026 +0.4..+1.8.
- Selection-aware: YM grid best clean Sharpe 1.59 vs replicate best p95 2.23; passing cells 46 vs replicate mean 38 (p 0.11): nothing beyond chance in the YM grid.
- Replication: H0 (2023-02-10..07-31) sleeve Sharpe -0.99, uplift -0.14 (FAIL); alternating months odd +0.23 / even +0.11 (both >= 50% of the all-in 0.17 = 0.085, PASS); same cell on ES / NQ / RTY positive standalone Sharpe in clean, H1 and H2 but uplift on clean only +0.02/+0.05/+0.04 (does not reach +0.10); GC / CL / ZN / BTC negative or mixed.
- Why not higher: margins at the gates, a single share passes, H0 fails, the YM grid shows no structure beyond chance, and 5 of the 7 other YM gate-3 cells in this family are the same overnight-driver-to-open mechanism (non-independent cells).
```
== R1/R2 on YM cell 37 driver NKD ovn |z|>=0.0 RTHopen+30 dir=with hold=120m scale 42.85
                        n_wk  sleeve_sh  pair_sh  uplift
H0 2023-02..07          25.0      -0.99     0.72   -0.14
clean                  104.0       0.95     1.39    0.15
H1                      28.0       1.31     3.09    0.10
H2                      35.0       1.58     2.40    0.22
odd months 2023-08..    85.0       1.54     2.22    0.23
even months 2023-08..   83.0       0.83     1.46    0.11
per-year weekly Sharpe (sleeve standalone): {2013: -0.88, 2014: -1.06, 2015: -0.88, 2016: -1.49, 2017: -1.13, 2018: 0.82, 2019: 0.88, 2020: 0.37, 2021: 1.12, 2022: 0.55, 2023: 0.63, 2024: 0.88, 2025: 1.13, 2026: 1.81}
== R3 same cell, other instruments (no re-selection)
   sym  scale  sh_pre2023  sh_clean  sh_H1  sh_H2  up_clean  up_H1  up_H2  H0_sh
0   ES   30.5       -0.06      0.25   1.93   1.40      0.02   0.21   0.19   0.31
1   NQ   16.9        0.39      0.39   2.32   1.56      0.05   0.30   0.29   2.12
2  RTY   50.0        0.06      0.44   1.44   0.75      0.04   0.07   0.06  -0.91
3   GC   24.2       -0.98      0.36   1.50   0.84     -0.03   0.82  -0.02   0.30
4   CL   42.2       -0.73     -0.69   1.92  -0.45     -0.19   0.31  -0.10   0.16
5   ZN  179.4       -2.80     -2.36  -5.62  -1.68     -0.48  -0.69  -0.29  -1.32
6  BTC    7.6       -0.36     -0.54   2.06  -0.89     -0.12   0.24  -0.22  -1.25

```

DONE SW9
