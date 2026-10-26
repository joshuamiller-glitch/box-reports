# REPORT B4 - intraday mean reversion with VWAP / standard-deviation bands (5-30 min) on ES, RTY, GC, CL, ZN

**Verdict: LEAD. FOUND 0, LEAD 2, INSURANCE 0.** 12 selected cells (+20 diagnostic) scored on 7 instruments; best non-diagnostic all-in additive uplift at 20% share +0.19; best pair-window standalone Sharpe +1.01.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: fade a bar close that crosses from inside to outside session VWAP +- k sigma (sigma = volume-weighted std of typical price about the session VWAP; anchor = globex 18:00 ET or the instrument RTH open). Stop s x sigma from entry, target = VWAP level at the signal (or halfway), time stop 60/180 min, flat 16:55.
- Instruments: ES, RTY, GC, CL, ZN, YM, BTC. Grid: 192 cells per instrument = 4 bar sizes x 3 band widths x 2 anchors x 2 stops x 2 targets x 2 time stops.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     192 |        176 |         4 |               0.669 |                2 |          4 |            3 |
| CL    |     192 |        176 |         0 |              -0.282 |                1 |          0 |            3 |
| ES    |     192 |        192 |         0 |               0.259 |                1 |          0 |            3 |
| GC    |     192 |        184 |         0 |               0.61  |                2 |          0 |            3 |
| RTY   |     192 |        184 |         8 |               1.033 |                2 |          8 |            2 |
| YM    |     192 |        192 |         0 |               0.093 |                1 |          0 |            3 |
| ZN    |     192 |        184 |         0 |              -1.491 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            3.23  |              11 |      1     |                     nan     |            0.589 |           0.994 |  nan     |     nan     |                1.611 |
| RTY   |     200 |                    8 |            5.335 |              12 |      0.19  |                       0.556 |            0.633 |           0.975 |    0.65  |       1.033 |                1.694 |
| GC    |     200 |                    0 |            4.12  |              10 |      1     |                     nan     |            0.595 |           0.991 |  nan     |     nan     |                1.667 |
| CL    |     200 |                    0 |            2.94  |               8 |      1     |                     nan     |            0.595 |           0.989 |  nan     |     nan     |                1.416 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| YM    |     200 |                    0 |            4.515 |              10 |      1     |                     nan     |            0.552 |           0.823 |  nan     |     nan     |                1.466 |
| BTC   |     200 |                    4 |            3.465 |              10 |      0.505 |                       0.443 |            0.591 |           1.022 |    0.745 |       0.669 |                1.451 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m | 513 | 1 | 0.26 | -0.39 | 0.02 | -0.26 / 1.12 | 0.03 / -0.08 / -0.18 | -0.14 | -0.13 | 0.78 | -0.24 | 0.00 | 755 | diag |
| ES 2 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | 102 | 1 | -0.01 | -0.82 | -0.24 | -0.34 / 0.96 | -0.03 / -0.27 / -0.17 | -0.14 | 0.24 | 0.66 | -0.28 | 0.00 | 144 | diag |
| ES 3 (diag) | 10m VWAPband k=2.0 globex stop=2.0sd tgt=vwap time=180m | 1835 | 1 | -0.06 | -1.65 | -0.54 | -1.12 / 0.92 | -0.03 / 0.01 / -0.37 | -0.34 | -0.16 | 0.85 | -0.31 | 0.00 | 2803 | diag |
| RTY 1 | 30m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | 253 | 2 | 1.03 | -0.89 | 0.43 | -0.52 / 0.89 | 0.18 / -0.46 / 0.31 | 0.07 | -0.42 | 0.96 | -0.06 | 0.17 | 388 | NO |
| RTY 2 | 30m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=180m | 269 | 2 | 0.96 | -0.73 | 0.48 | -0.27 / 0.53 | 0.11 / -0.28 / 0.07 | -0.01 | 0.13 | 0.99 | -0.15 | 0.33 | 411 | NO |
| RTY 3 | 15m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=180m | 385 | 2 | 0.87 | -0.77 | 0.31 | -0.62 / 0.53 | 0.13 / -0.26 / -0.04 | -0.03 | -0.00 | 0.99 | -0.14 | 0.50 | 608 | NO |
| RTY 4 | 30m VWAPband k=2.0 rth stop=2.0sd tgt=half time=180m | 263 | 2 | 0.47 | -1.05 | -0.03 | -0.90 / 0.90 | 0.09 / -0.41 / 0.25 | 0.01 | -0.47 | 0.77 | -0.12 | 0.17 | 400 | NO |
| RTY 5 | 15m VWAPband k=2.0 rth stop=1.0sd tgt=half time=180m | 392 | 2 | 0.43 | -1.01 | 0.10 | -0.34 / 0.20 | 0.05 / -0.15 / 0.03 | -0.06 | 0.27 | 0.98 | -0.18 | 0.17 | 621 | NO |
| RTY 6 | 5m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=180m | 603 | 2 | 0.29 | -1.26 | -0.21 | -0.90 / -0.14 | 0.05 / -0.77 / 0.05 | -0.14 | 0.35 | 1.00 | -0.25 | 0.00 | 958 | NO |
| RTY 7 | 30m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=60m | 270 | 2 | 0.23 | -1.12 | -0.49 | -1.47 / 0.31 | -0.04 / -0.24 / -0.33 | -0.22 | 0.51 | 0.84 | -0.34 | 0.00 | 413 | NO |
| RTY 8 | 30m VWAPband k=1.5 rth stop=2.0sd tgt=vwap time=180m | 509 | 2 | 0.17 | -0.99 | -0.05 | -0.44 / 0.46 | 0.03 / -0.66 / 0.28 | -0.07 | -0.31 | 0.95 | -0.20 | 0.00 | 800 | NO |
| RTY 9 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | 67 | 2 | 0.87 | 0.07 | 0.43 | -0.70 / 1.07 | 0.09 / -0.17 / -0.04 | -0.01 | 0.34 | 0.96 | -0.13 | 0.33 | 95 S | diag |
| RTY 10 (diag) | 10m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | 413 | 1 | 0.65 | -0.72 | 0.13 | -0.89 / 0.22 | 0.15 / -0.43 / 0.13 | 0.01 | -0.59 | 1.00 | -0.10 | 0.17 | 633 | diag |
| GC 1 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | 64 | 2 | 0.61 | -0.76 | 0.18 | -0.03 / 1.70 | 0.06 / -0.29 / -0.58 | -0.12 | -0.06 | 0.68 | -0.44 | 0.00 | 97 S | diag |
| GC 2 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=60m | 64 | 2 | 0.53 | -0.45 | 0.15 | 0.02 / 1.56 | 0.04 / -0.19 / -0.64 | -0.13 | -0.06 | 0.72 | -0.46 | 0.00 | 97 S | diag |
| GC 3 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | 64 | 1 | 0.16 | -0.32 | 0.22 | 0.30 / 1.23 | -0.04 / -0.12 / -0.37 | -0.11 | -0.14 | 0.77 | -0.42 | 0.00 | 97 S | diag |
| CL 1 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | 42 | 0 | -0.28 | -0.42 | -0.71 | -1.10 / 1.12 | -0.10 / -0.27 / -0.98 | -0.37 | -0.09 | 0.31 | -0.68 | 0.00 | 86 S | diag |
| CL 2 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | 42 | 0 | -0.31 | -0.37 | -0.64 | -0.96 / 1.28 | -0.10 / -0.00 / -0.81 | -0.29 | -0.04 | 0.39 | -0.56 | 0.00 | 86 S | diag |
| CL 3 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | 42 | 1 | -0.32 | -0.43 | -0.73 | -1.13 / 1.16 | -0.10 / -0.33 / -0.97 | -0.38 | -0.02 | 0.23 | -0.70 | 0.00 | 86 S | diag |
| ZN 1 (diag) | 15m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | 100 | 0 | -1.49 | -2.10 | -1.93 | -3.06 / -0.26 | -0.35 / -0.25 / -0.56 | -0.62 | 0.35 | 0.51 | -0.56 | 0.00 | 161 | diag |
| ZN 2 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | 64 | 0 | -1.63 | -2.03 | -1.77 | -2.28 / -0.38 | -0.35 / 0.10 / -0.46 | -0.51 | 0.30 | 0.27 | -0.50 | 0.00 | 95 S | diag |
| ZN 3 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | 65 | 0 | -1.92 | -2.01 | -1.67 | -1.17 / 0.35 | -0.39 / -0.01 / -0.26 | -0.50 | -0.09 | 0.23 | -0.50 | 0.00 | 96 S | diag |
| YM 1 (diag) | 15m VWAPband k=2.0 globex stop=2.0sd tgt=vwap time=180m | 1763 | 1 | 0.09 | -0.95 | -0.36 | -1.00 / 0.26 | -0.00 / -0.37 / -0.18 | -0.20 | 0.11 | 0.78 | -0.27 | 0.00 | 2761 | diag |
| YM 2 (diag) | 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | 236 | 1 | 0.08 | -0.60 | -0.46 | -1.38 / 1.04 | 0.03 / -0.52 / -0.10 | -0.11 | 0.23 | 0.67 | -0.25 | 0.00 | 336 | diag |
| YM 3 (diag) | 10m VWAPband k=2.0 globex stop=2.0sd tgt=vwap time=180m | 2023 | 1 | 0.05 | -0.69 | -0.70 | -1.53 / 0.50 | -0.01 / -0.45 / -0.48 | -0.31 | -0.05 | 0.52 | -0.38 | 0.00 | 3158 | diag |
| BTC 1 | 10m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | 112 | 2 | 0.67 | -0.12 | 0.89 | 1.22 / 0.91 | 0.14 / 0.27 / 0.15 | 0.14 | 0.29 | 1.00 | -0.03 | 0.33 | 167 | LEAD |
| BTC 2 | 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | 112 | 2 | 0.53 | -0.44 | 0.48 | 0.40 / 1.35 | 0.14 / -0.19 / 0.09 | 0.06 | 0.37 | 0.99 | -0.09 | 0.17 | 167 | NO |
| BTC 3 | 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | 183 | 2 | 0.43 | -1.79 | 1.01 | 1.91 / 0.82 | 0.11 / 0.32 / 0.26 | 0.15 | -0.12 | 1.00 | -0.00 | 0.67 | 275 | LEAD |
| BTC 4 | 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | 183 | 2 | 0.15 | -1.62 | 0.70 | 1.62 / 0.97 | 0.01 / 0.33 / 0.24 | 0.08 | 0.31 | 1.00 | -0.08 | 0.67 | 275 | NO |
| BTC 5 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | 37 | 2 | 0.57 | -0.56 | 0.17 | -0.82 / 1.36 | 0.16 / -0.40 / 0.01 | 0.04 | -0.01 | 0.83 | -0.11 | 0.33 | 52 S | diag |
| BTC 6 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | 37 | 1 | 0.46 | -0.33 | 0.10 | -0.87 / 1.49 | 0.11 / -0.37 / -0.05 | -0.00 | 0.13 | 0.78 | -0.15 | 0.17 | 52 S | diag |
| BTC 7 (diag) | 10m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | 112 | 1 | 0.45 | -0.10 | 0.77 | 1.28 / 1.49 | 0.11 / 0.24 / 0.17 | 0.12 | 0.00 | 1.00 | -0.04 | 0.50 | 167 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 12 |
| diagnostic cells read | 20 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 2 / 2 / 2 |
| all-in uplift @20% > 0 (all scored) | 14 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 13 |
| worst-decile corr <= +0.30 | 25 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 11 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | clean | 0.43 | 0.67 | -119989 | -98971 | 410681 | -234640 | 0.94 | 39.0 | 1.57 | -85969 | 248776 | -98863 |
| BTC 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | H1 | 1.68 | 3.64 | -121334 | -103952 | 242669 | -128830 | 2.32 | 32.1 | 3.15 | -76082 | 139063 | -83529 |
| BTC 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | H2 | 2.39 | 5.97 | -67065 | -50949 | 112968 | -75578 | 5.08 | 25.0 | 2.55 | -80324 | 199063 | -86512 |
| BTC 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | all | 1.01 | 1.80 | -116371 | -94311 | 410681 | -234640 | 3.71 | 35.1 | 2.05 | -84644 | 248776 | -98863 |
| CL 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m (diag) | clean | -0.31 | -0.40 | -160794 | -115422 | 913569 | -409430 | -0.31 | 14.3 | 1.36 | -91262 | 301832 | -121543 |
| CL 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m (diag) | H1 | 0.55 | 0.93 | -64061 | -58150 | 82449 | -79457 | 0.93 | 25.0 | 2.82 | -73102 | 153272 | -76932 |
| CL 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m (diag) | H2 | -1.40 | -1.55 | -491620 | -370172 | 1220731 | -718891 | -0.96 | 25.0 | 1.48 | -123238 | 233156 | -133401 |
| CL 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m (diag) | all | -0.64 | -0.73 | -287943 | -198054 | 1826483 | -718891 | -0.76 | 18.5 | 1.60 | -97449 | 301832 | -133401 |
| ES 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | clean | 0.28 | 0.47 | -111207 | -96875 | 882945 | -144275 | 0.29 | 50.5 | 1.49 | -84813 | 328950 | -99604 |
| ES 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | H1 | -0.04 | -0.07 | -166475 | -131130 | 344656 | -235290 | -0.04 | 71.4 | 2.75 | -78799 | 172571 | -84156 |
| ES 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | H2 | -0.39 | -0.62 | -180529 | -156347 | 840538 | -190278 | -0.24 | 58.3 | 2.12 | -91546 | 234201 | -98260 |
| ES 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | all | 0.02 | 0.04 | -148702 | -121618 | 882945 | -235290 | 0.04 | 56.0 | 1.83 | -86733 | 328950 | -99604 |
| GC 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | clean | 0.19 | 0.34 | -114165 | -94667 | 559882 | -159309 | 0.30 | 24.8 | 1.42 | -86754 | 297816 | -98646 |
| GC 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | H1 | 0.98 | 2.20 | -417272 | -326332 | 672543 | -669856 | 1.72 | 17.9 | 2.71 | -96885 | 231144 | -145191 |
| GC 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | H2 | -0.79 | -0.90 | -414123 | -261914 | 981579 | -704954 | -0.57 | 25.0 | 1.93 | -79970 | 217425 | -82524 |
| GC 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | all | 0.22 | 0.39 | -259137 | -182239 | 981579 | -704954 | 0.79 | 23.8 | 1.78 | -91740 | 297816 | -145191 |
| RTY 30m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | clean | 0.95 | 1.47 | -130859 | -96066 | 491113 | -283012 | 1.77 | 39.0 | 1.64 | -84747 | 230788 | -89736 |
| RTY 30m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | H1 | -2.95 | -3.05 | -137107 | -116405 | 659376 | -159488 | -0.84 | 60.7 | 2.37 | -71113 | 153286 | -75581 |
| RTY 30m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | H2 | 0.94 | 1.58 | -119509 | -93777 | 195593 | -138546 | 1.47 | 36.1 | 2.61 | -77899 | 204970 | -78650 |
| RTY 30m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | all | 0.43 | 0.63 | -135845 | -103227 | 846826 | -283012 | 0.71 | 42.3 | 1.96 | -82758 | 230788 | -89736 |
| YM 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m (diag) | clean | 0.05 | 0.07 | -137536 | -101495 | 391879 | -391879 | 0.12 | 44.8 | 1.49 | -81673 | 292970 | -88065 |
| YM 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m (diag) | H1 | -1.74 | -1.86 | -209011 | -162657 | 523319 | -316075 | -0.93 | 35.7 | 2.31 | -73027 | 180604 | -76343 |
| YM 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m (diag) | H2 | -0.99 | -1.33 | -68488 | -64926 | 390667 | -72235 | -0.51 | 52.8 | 2.20 | -91862 | 226998 | -95266 |
| YM 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m (diag) | all | -0.46 | -0.57 | -146163 | -107554 | 848419 | -391879 | -0.76 | 45.2 | 1.78 | -84326 | 292970 | -95266 |
| ZN 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m (diag) | clean | -1.91 | -1.99 | -195600 | -163746 | 1735458 | -254978 | -1.00 | 27.6 | 1.07 | -90372 | 347245 | -128166 |
| ZN 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m (diag) | H1 | -0.26 | -0.31 | -118767 | -102753 | 211703 | -162347 | -0.21 | 14.3 | 2.82 | -72729 | 133118 | -78287 |
| ZN 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m (diag) | H2 | -1.83 | -2.02 | -123409 | -105536 | 489811 | -135709 | -0.85 | 25.0 | 2.03 | -89198 | 225278 | -95872 |
| ZN 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m (diag) | all | -1.67 | -1.77 | -180183 | -148006 | 2268676 | -254978 | -0.97 | 25.0 | 1.54 | -88768 | 347245 | -128166 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m (diag) | -29.6 | -20.2 | 7.6 | -9.3 | -6.9 / 15.1 | -13.8 / 1.6 | NO |
| RTY 30m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | -23.2 | 15.8 | 20.3 | 38.0 | 15.1 / 18.0 | 15.8 / 24.1 | NO |
| GC 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | -21.4 | -153.0 | -15.9 | 4.0 | -5.3 / 14.4 | -166.7 / -53.4 | NO |
| CL 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m (diag) | -45.5 | -152.5 | -24.4 | -24.5 | -83.9 / -1.3 | 31.2 / 38.7 | NO |
| ZN 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m (diag) | -54.5 | -58.2 | 10.1 | -14.0 | -59.4 / 5.1 | 30.0 / 38.5 | NO |
| YM 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m (diag) | -37.2 | 5.0 | 16.8 | 17.2 | 4.3 / 19.2 | 33.7 / 35.0 | NO |
| BTC 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | -13.0 | -5.0 | 16.1 | 33.7 | -5.8 / 15.0 | 12.3 / 14.7 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) 15m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m | gross-positive, cost-negative pre-2023 | 1792 | 11.0 | -14.8 | -2.9 | 25.8 | 0.29 / -0.39 / -0.07 | 34.9 / 9.7 |
| ES 2 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | negative pre-2023 | 452 | -18.2 | -43.0 | -31.2 | 24.8 | -0.35 / -0.82 / -0.60 | 13.3 / -11.2 |
| ES 3 (diag) 10m VWAPband k=2.0 globex stop=2.0sd tgt=vwap time=180m | gross-positive, cost-negative pre-2023 | 8128 | 0.7 | -24.5 | -12.5 | 25.2 | 0.05 / -1.65 / -0.84 | 22.6 / -2.3 |
| RTY 1 30m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 814 | -24.3 | -37.5 | -35.4 | 13.2 | -0.58 / -0.89 / -0.84 | 54.4 / 41.4 |
| RTY 2 30m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 865 | -9.0 | -22.4 | -20.3 | 13.4 | -0.29 / -0.73 / -0.66 | 43.0 / 29.7 |
| RTY 3 15m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 1307 | -5.0 | -18.3 | -16.1 | 13.3 | -0.21 / -0.77 / -0.68 | 34.7 / 21.5 |
| RTY 4 30m VWAPband k=2.0 rth stop=2.0sd tgt=half time=180m | negative pre-2023 | 840 | -25.9 | -37.8 | -35.9 | 12.0 | -0.72 / -1.05 / -0.99 | 26.7 / 15.2 |
| RTY 5 15m VWAPband k=2.0 rth stop=1.0sd tgt=half time=180m | negative pre-2023 | 1342 | -6.5 | -18.8 | -16.7 | 12.3 | -0.35 / -1.01 / -0.90 | 19.8 / 7.8 |
| RTY 6 5m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 2114 | -9.4 | -22.7 | -20.5 | 13.3 | -0.53 / -1.26 / -1.14 | 19.1 / 6.0 |
| RTY 7 30m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=60m | negative pre-2023 | 873 | -14.4 | -28.3 | -26.1 | 13.9 | -0.57 / -1.12 / -1.03 | 16.5 / 2.7 |
| RTY 8 30m VWAPband k=1.5 rth stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 1588 | -14.9 | -27.8 | -25.7 | 12.9 | -0.54 / -0.99 / -0.92 | 18.8 / 6.0 |
| RTY 9 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | positive pre-2023 | 206 | 18.4 | 4.8 | 7.2 | 13.5 | 0.25 / 0.07 / 0.10 | 77.7 / 64.3 |
| RTY 10 (diag) 10m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 1398 | -9.8 | -22.8 | -20.7 | 13.0 | -0.31 / -0.72 / -0.65 | 32.9 / 20.1 |
| GC 1 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | negative pre-2023 | 321 | -12.3 | -33.7 | -25.0 | 21.5 | -0.28 / -0.76 / -0.56 | 79.3 / 58.8 |
| GC 2 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=60m | gross-positive, cost-negative pre-2023 | 321 | 1.5 | -20.3 | -11.4 | 21.8 | 0.03 / -0.45 / -0.26 | 64.1 / 43.3 |
| GC 3 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | gross-positive, cost-negative pre-2023 | 321 | 6.5 | -17.0 | -7.4 | 23.5 | 0.12 / -0.32 / -0.14 | 40.1 / 16.5 |
| CL 1 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | gross-positive, cost-negative pre-2023 | 373 | 2.8 | -20.7 | -17.8 | 23.4 | 0.06 / -0.42 / -0.36 | -2.0 / -25.6 |
| CL 2 (diag) 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | gross-positive, cost-negative pre-2023 | 370 | 1.1 | -21.9 | -19.1 | 23.0 | 0.02 / -0.37 / -0.33 | -11.9 / -35.3 |
| CL 3 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 373 | -2.4 | -25.2 | -22.4 | 22.9 | -0.04 / -0.43 / -0.39 | -8.5 / -31.2 |
| ZN 1 (diag) 15m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 620 | -5.7 | -38.1 | -42.8 | 32.3 | -0.34 / -2.10 / -2.34 | 1.8 / -29.9 |
| ZN 2 (diag) 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 347 | -10.0 | -42.9 | -47.7 | 32.8 | -0.52 / -2.03 / -2.22 | -4.5 / -36.4 |
| ZN 3 (diag) 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | negative pre-2023 | 348 | -8.4 | -37.7 | -42.0 | 29.4 | -0.51 / -2.01 / -2.19 | -6.0 / -34.8 |
| YM 1 (diag) 15m VWAPband k=2.0 globex stop=2.0sd tgt=vwap time=180m | gross-positive, cost-negative pre-2023 | 7423 | 0.9 | -11.8 | -6.8 | 12.7 | 0.07 / -0.95 / -0.55 | 13.8 / 1.2 |
| YM 2 (diag) 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | negative pre-2023 | 1098 | -3.7 | -16.2 | -11.3 | 12.5 | -0.14 / -0.60 / -0.42 | 14.4 / 2.1 |
| YM 3 (diag) 10m VWAPband k=2.0 globex stop=2.0sd tgt=vwap time=180m | gross-positive, cost-negative pre-2023 | 8908 | 4.7 | -7.9 | -2.9 | 12.7 | 0.41 / -0.69 / -0.25 | 12.3 / -0.3 |
| BTC 1 10m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | gross-positive, cost-negative pre-2023 | 121 | 36.5 | -13.3 | 16.3 | 49.8 | 0.33 / -0.12 / 0.14 | 258.6 / 209.6 |
| BTC 2 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | gross-positive, cost-negative pre-2023 | 122 | 8.0 | -37.2 | -10.4 | 45.1 | 0.10 / -0.44 / -0.12 | 169.4 / 125.5 |
| BTC 3 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | negative pre-2023 | 192 | -91.9 | -144.3 | -112.6 | 52.4 | -1.16 / -1.79 / -1.41 | 146.6 / 95.4 |
| BTC 4 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 191 | -101.3 | -151.9 | -121.5 | 50.6 | -1.10 / -1.62 / -1.30 | 88.2 / 39.4 |
| BTC 5 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | negative pre-2023 | 49 | -43.5 | -89.2 | -62.5 | 45.7 | -0.28 / -0.56 / -0.39 | 306.9 / 264.0 |
| BTC 6 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 49 | -9.5 | -60.8 | -31.0 | 51.3 | -0.05 / -0.33 / -0.17 | 335.4 / 286.5 |
| BTC 7 (diag) 10m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | gross-positive, cost-negative pre-2023 | 121 | 42.8 | -9.1 | 21.9 | 51.9 | 0.49 / -0.10 / 0.25 | 182.0 / 130.8 |


## 6b. Replication tests (leads only)
BTC 1 (cell 89): (a) live weeks N/A. (b) H0 2023-02..07 standalone Sharpe +1.63 on 38 trades: holds (>= 30 trades). (c) cross-instrument ES -0.12, RTY -0.25: fails. (d) alternating months odd +0.17 / even +0.10 vs +0.17: holds. 2 of 4: replicated. BTC 3 (cell 40): (b) H0 -0.40 fails; (c) ES -0.16, RTY -0.21 fails; (d) odd +0.16 / even +0.17 holds: 1 of 4, not replicated. Files outputs/autopilot/b/b4_co/repl_BTC_89.json, repl_BTC_40.json.


## 6. What this says
- **Equity index, metals, energy, rates: nothing.** ES, YM, GC, CL, ZN have no cell with positive weekly Sharpe in both clean halves and >= 100 trades (best clean Sharpe: GC +0.61, ES +0.26, YM +0.09, CL -0.28, ZN -1.49). RTY passes the rule with 8 cells (30m/15m, k = 2.0 sigma, RTH anchor, VWAP target, 180-minute time stop; clean Sharpe 0.17-1.03) but the replicate grid passes 5.3 cells on average (p(count) = 0.19, p(top) = 0.65) and all 8 lose in H1 (uplift -0.15 to -0.77 at 20%); out-of-selection (H1+H2) standalone Sharpe is negative for all 8. ERA flag for the RTY cells: negative pre-2023 (net weekly Sharpe -0.73 to -1.26 in 2017-22).
- **BTC (GAPMAP D11 cell): two gate-3 leads, both weak.** BTC passes the rule with 4 cells (chance level: replicates pass 3.5, p(count) = 0.51, p(top) = 0.75). Of these, BTC 1 (10-minute, 2.5 sigma, RTH-anchored (09:30 ET reference), stop 1 sigma, VWAP target, 180-minute time stop) has uplifts +0.14 / +0.27 / +0.15 at 20% and BTC 3 (5-minute, 60-minute time stop) +0.11 / +0.32 / +0.26. Both fail the bootstrap (90% lower bounds -0.03 and -0.00 at 20%), the plateau (0.33 and 0.67), and both are small samples (167 and 275 trades in the pair window). Replication: BTC 1 holds H0 (+1.63 on 38 trades) and alternating months (odd +0.17, even +0.10 against +0.17), fails ES/RTY (-0.12, -0.25): 2 of 4. BTC 3 holds alternating months only (H0 -0.40): 1 of 4, not replicated. Their ERA flags are 'negative pre-2023'-type for BTC 2022 (net Sharpe -0.12 and -1.79 on the 2022 sample).
- Reading: a BTC VWAP-band fade with a 2.5-sigma trigger is a rare-event rule (about 70-110 trades a year) and the evidence is a small sample on a market regime; this is a LEAD for the BTC gap cell with failing gates (bootstrap, plateau, small-sample), not a candidate for trading.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_b4.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/b4/ (`B4_CO_all_selected_scored.csv`).

DONE B4
