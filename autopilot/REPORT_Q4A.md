# REPORT Q4A - Q4A: B4 grid on metals/energy (SI, HG, PL, HO, RB, NG)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 12 selected cells (+18 diagnostic) scored on 6 instruments; best non-diagnostic all-in additive uplift at 20% share +0.30; best pair-window standalone Sharpe +1.12.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: fade a bar close that crosses from inside to outside session VWAP +- k sigma (sigma = volume-weighted std of typical price about the session VWAP; anchor = globex 18:00 ET or the instrument RTH open). Stop s x sigma from entry, target = VWAP level at the signal (or halfway), time stop 60/180 min, flat 16:55.
- Instruments: SI, HG, PL, HO, RB, NG. Grid: 192 cells per instrument = 4 bar sizes x 3 band widths x 2 anchors x 2 stops x 2 targets x 2 time stops.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| HG    |     192 |        184 |         5 |               0.701 |                2 |          5 |            3 |
| HO    |     192 |        192 |         5 |               0.836 |                2 |          5 |            3 |
| NG    |     192 |        176 |         0 |               0.598 |                2 |          0 |            3 |
| PL    |     192 |        176 |         0 |              -0.164 |                1 |          0 |            3 |
| RB    |     192 |        192 |         2 |               0.817 |                2 |          2 |            3 |
| SI    |     192 |        174 |         0 |               0.448 |                2 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| SI    |     100 |                    0 |             1.01 |               3 |       1    |                     nan     |            0.543 |           1.147 |   nan    |     nan     |                1.528 |
| HG    |     100 |                    5 |             0.88 |               3 |       0    |                       0.32  |            0.501 |           1.004 |     0.37 |       0.701 |                1.314 |
| PL    |     100 |                    0 |             0.72 |               4 |       1    |                     nan     |            0.552 |           1.198 |   nan    |     nan     |                1.325 |
| HO    |     100 |                    5 |             5.44 |              12 |       0.6  |                       0.573 |            0.573 |           0.812 |     0.51 |       0.836 |                1.561 |
| RB    |     100 |                    2 |             5.68 |              12 |       0.97 |                       0.432 |            0.601 |           0.873 |     0.87 |       0.517 |                1.554 |
| NG    |     100 |                    0 |             0.43 |               3 |       1    |                     nan     |            0.525 |           1.009 |   nan    |     nan     |                1.141 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SI 1 (diag) | 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | 74 | 2 | 0.45 | -0.45 | -0.08 | -0.25 / 0.93 | 0.01 / 0.31 / -1.57 | -0.37 | -0.19 | 0.73 | -0.79 | 0.00 | 149 | diag |
| SI 2 (diag) | 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=60m | 74 | 2 | 0.43 | -0.63 | -0.30 | -0.59 / 1.01 | -0.01 / -0.70 / -1.22 | -0.49 | -0.14 | 0.59 | -0.87 | 0.00 | 150 | diag |
| SI 3 (diag) | 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | 71 | 2 | 0.20 | -0.30 | -0.21 | -0.35 / 1.24 | -0.06 / -1.25 / -0.66 | -0.45 | -0.13 | 0.55 | -0.94 | 0.00 | 144 | diag |
| HG 1 | 5m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | 698 | 2 | 0.70 | -1.69 | 0.43 | -0.05 / 0.57 | 0.18 / -0.41 / 0.22 | -0.06 | -0.39 | 0.99 | -0.09 | 0.33 | 1066 | NO |
| HG 2 | 30m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | 181 | 2 | 0.41 | -1.03 | 0.34 | 0.15 / 1.15 | 0.11 / 0.30 / -0.08 | 0.02 | -0.20 | 0.93 | -0.08 | 0.83 | 277 | NO |
| HG 3 | 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m | 180 | 2 | 0.17 | -1.02 | -0.30 | -1.12 / 1.15 | 0.07 / -0.65 / 0.01 | -0.12 | -0.25 | 0.59 | -0.25 | 0.00 | 276 | NO |
| HG 4 | 15m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | 336 | 2 | 0.16 | -1.36 | 0.56 | 1.16 / 0.98 | 0.05 / 0.36 / 0.23 | 0.03 | -0.34 | 0.99 | -0.07 | 0.83 | 520 | NO |
| HG 5 | 30m VWAPband k=2.5 globex stop=2.0sd tgt=half time=60m | 182 | 2 | 0.15 | -1.09 | 0.13 | 0.03 / 1.10 | 0.05 / 0.12 / -0.05 | -0.03 | -0.27 | 0.93 | -0.13 | 0.50 | 279 | NO |
| HG 6 (diag) | 10m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | 463 | 1 | 0.49 | -1.21 | -0.07 | -0.87 / 0.81 | 0.14 / -0.48 / -0.17 | -0.15 | -0.35 | 0.86 | -0.23 | 0.00 | 706 | diag |
| HG 7 (diag) | 30m VWAPband k=2.5 globex stop=1.0sd tgt=half time=180m | 183 | 1 | 0.42 | -1.26 | 0.12 | -0.69 / 1.08 | 0.09 / -0.07 / 0.00 | -0.03 | -0.32 | 0.91 | -0.11 | 0.83 | 279 | diag |
| HG 8 (diag) | 5m VWAPband k=2.5 globex stop=2.0sd tgt=half time=60m | 703 | 1 | 0.25 | -2.00 | 0.09 | -0.23 / 0.21 | 0.07 / -0.53 / 0.18 | -0.17 | -0.50 | 1.00 | -0.17 | 0.33 | 1072 | diag |
| PL 1 (diag) | 30m VWAPband k=2.5 globex stop=1.0sd tgt=half time=180m | 205 | 1 | -0.16 | -0.32 | 0.13 | 0.33 / 1.34 | -0.07 / -0.98 / 0.43 | -0.16 | -0.04 | 0.83 | -0.61 | 0.00 | 283 | diag |
| PL 2 (diag) | 10m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | 129 | 1 | -0.21 | -0.70 | -0.45 | -0.67 / 1.28 | -0.01 / -1.09 / -0.73 | -0.40 | 0.42 | 0.55 | -0.76 | 0.00 | 227 | diag |
| PL 3 (diag) | 30m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=180m | 205 | 1 | -0.22 | -0.45 | 0.03 | 0.14 / 1.10 | -0.06 / -0.38 / -0.50 | -0.24 | 0.09 | 0.74 | -0.64 | 0.00 | 283 | diag |
| HO 1 | 30m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=60m | 1051 | 2 | 0.84 | -0.82 | 0.28 | 0.06 / 0.93 | 0.11 / -0.14 / -0.23 | -0.11 | 0.30 | 0.92 | -0.27 | 0.00 | 1628 | NO |
| HO 2 | 30m VWAPband k=2.0 globex stop=2.0sd tgt=vwap time=60m | 1037 | 2 | 0.76 | -0.89 | -0.03 | -0.43 / 0.60 | 0.10 / 0.07 / -0.72 | -0.20 | 0.28 | 0.81 | -0.41 | 0.00 | 1604 | NO |
| HO 3 | 15m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=180m | 1640 | 2 | 0.52 | -1.38 | -0.59 | -1.38 / 0.81 | 0.01 / 0.08 / -1.27 | -0.42 | 0.20 | 0.55 | -0.62 | 0.00 | 2538 | NO |
| HO 4 | 30m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=180m | 1037 | 2 | 0.49 | -0.68 | 0.44 | 0.59 / 0.83 | 0.02 / -0.03 / 0.29 | -0.02 | -0.07 | 0.97 | -0.24 | 0.50 | 1605 | NO |
| HO 5 | 30m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=180m | 390 | 2 | 0.26 | -0.49 | -0.13 | -0.38 / 0.95 | -0.00 / -0.09 / -0.18 | -0.10 | -0.75 | 0.67 | -0.34 | 0.00 | 621 | NO |
| HO 6 (diag) | 15m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=60m | 1662 | 1 | 0.50 | -1.63 | -0.61 | -1.64 / 0.69 | 0.03 / 0.05 / -1.11 | -0.37 | 0.31 | 0.51 | -0.49 | 0.00 | 2574 | diag |
| HO 7 (diag) | 30m VWAPband k=2.0 globex stop=1.0sd tgt=half time=60m | 1054 | 1 | 0.27 | -0.79 | -0.14 | -0.34 / 0.84 | 0.00 / -0.31 / -0.28 | -0.21 | 0.33 | 0.88 | -0.38 | 0.00 | 1632 | diag |
| HO 8 (diag) | 15m VWAPband k=2.0 globex stop=1.0sd tgt=half time=60m | 1689 | 1 | 0.24 | -1.58 | -0.50 | -1.09 / -0.12 | -0.01 / -0.17 / -0.84 | -0.37 | 0.20 | 0.84 | -0.49 | 0.00 | 2616 | diag |
| RB 1 | 30m VWAPband k=1.5 globex stop=1.0sd tgt=vwap time=180m | 2173 | 2 | 0.52 | -1.55 | 1.12 | 1.87 / 1.16 | 0.10 / 0.05 / 1.03 | 0.17 | -0.09 | 1.00 | 0.07 | 0.33 | 3461 | NO |
| RB 2 | 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | 408 | 2 | 0.35 | -0.32 | -0.24 | -0.78 / 0.19 | -0.00 / -0.10 / -0.27 | -0.13 | -0.10 | 0.92 | -0.29 | 0.00 | 676 | NO |
| RB 3 (diag) | 30m VWAPband k=1.5 rth stop=1.0sd tgt=vwap time=180m | 893 | 1 | 0.82 | -0.98 | 0.16 | -0.20 / -0.06 | 0.17 / -0.14 / -0.44 | -0.11 | -0.28 | 1.00 | -0.32 | 0.00 | 1442 | diag |
| RB 4 (diag) | 15m VWAPband k=1.5 globex stop=2.0sd tgt=vwap time=180m | 2620 | 1 | 0.27 | -1.67 | 0.92 | 1.76 / 0.95 | 0.05 / 0.23 / 0.79 | 0.13 | 0.04 | 1.00 | 0.01 | 0.33 | 4167 | diag |
| RB 5 (diag) | 5m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | 954 | 1 | 0.23 | -1.34 | -0.18 | -0.59 / -0.16 | -0.02 / 0.06 / -0.37 | -0.16 | -0.31 | 1.00 | -0.32 | 0.00 | 1517 | diag |
| NG 1 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=60m | 50 | 1 | 0.60 | -0.12 | -0.02 | -1.12 / 0.71 | 0.19 / -0.12 / -0.44 | -0.10 | 0.11 | 0.97 | -0.20 | 0.33 | 82 S | diag |
| NG 2 (diag) | 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=60m | 89 | 1 | 0.50 | -0.44 | -0.15 | -1.35 / 0.01 | 0.11 / -0.30 / -0.49 | -0.20 | 0.58 | 0.99 | -0.26 | 0.00 | 158 | diag |
| NG 3 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | 50 | 2 | 0.26 | -0.48 | 0.06 | -0.33 / 0.69 | 0.10 / 0.28 / -0.39 | -0.09 | 0.08 | 0.99 | -0.20 | 0.33 | 82 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 12 |
| diagnostic cells read | 18 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 11 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 2 |
| standalone pair-window Sharpe above own random-entry null p95 | 11 |
| worst-decile corr <= +0.30 | 26 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 2 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HG 15m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | clean | 0.19 | 0.34 | -111093 | -90359 | 750148 | -169134 | 0.23 | 44.8 | 1.51 | -84824 | 320857 | -93111 |
| HG 15m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | H1 | 0.98 | 1.46 | -108886 | -85773 | 201385 | -167743 | 0.99 | 39.3 | 3.19 | -65817 | 129254 | -81095 |
| HG 15m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | H2 | 1.28 | 2.22 | -128700 | -100399 | 245033 | -145781 | 1.80 | 41.7 | 2.53 | -88529 | 252311 | -99739 |
| HG 15m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | all | 0.56 | 0.95 | -122023 | -95626 | 750148 | -169134 | 1.09 | 43.5 | 1.98 | -85233 | 320857 | -99739 |
| HO 30m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=180m | clean | 0.31 | 0.44 | -124999 | -106535 | 702325 | -216898 | 0.39 | 45.7 | 1.48 | -89722 | 299493 | -97498 |
| HO 30m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=180m | H1 | -1.19 | -1.69 | -84298 | -77131 | 501495 | -99917 | -0.49 | 64.3 | 2.80 | -77118 | 142403 | -83968 |
| HO 30m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=180m | H2 | 1.06 | 1.89 | -305726 | -274647 | 887059 | -318160 | 1.21 | 38.9 | 2.58 | -97109 | 220162 | -98257 |
| HO 30m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=180m | all | 0.44 | 0.74 | -222647 | -168150 | 901097 | -318160 | 1.23 | 47.0 | 1.92 | -90724 | 299493 | -98257 |
| NG 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | clean | 0.39 | 0.63 | -134860 | -110592 | 606895 | -182518 | 0.59 | 19.0 | 1.56 | -87009 | 275839 | -100507 |
| NG 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | H1 | 0.77 | 1.45 | -207660 | -177171 | 282295 | -230066 | 1.26 | 17.9 | 3.11 | -86593 | 154965 | -94265 |
| NG 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | H2 | -2.68 | -2.87 | -107985 | -99656 | 727122 | -112888 | -0.83 | 30.6 | 1.91 | -83588 | 224918 | -84651 |
| NG 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | all | 0.06 | 0.10 | -150989 | -122523 | 816120 | -230066 | 0.13 | 21.4 | 1.88 | -87229 | 275839 | -100507 |
| PL 30m VWAPband k=2.5 globex stop=1.0sd tgt=half time=180m (diag) | clean | -0.27 | -0.39 | -130288 | -111167 | 792832 | -190720 | -0.31 | 48.6 | 1.38 | -86834 | 285631 | -93430 |
| PL 30m VWAPband k=2.5 globex stop=1.0sd tgt=half time=180m (diag) | H1 | -0.02 | -0.03 | -885053 | -666849 | 2600939 | -944501 | -0.01 | 28.6 | 1.85 | -181520 | 528793 | -200468 |
| PL 30m VWAPband k=2.5 globex stop=1.0sd tgt=half time=180m (diag) | H2 | 0.86 | 2.02 | -186215 | -168112 | 669709 | -204027 | 1.18 | 41.7 | 2.73 | -98940 | 250634 | -109619 |
| PL 30m VWAPband k=2.5 globex stop=1.0sd tgt=half time=180m (diag) | all | 0.13 | 0.20 | -334880 | -233363 | 2707692 | -944501 | 0.19 | 44.0 | 1.77 | -111428 | 528793 | -200468 |
| RB 30m VWAPband k=1.5 globex stop=1.0sd tgt=vwap time=180m | clean | 0.42 | 0.71 | -98456 | -89157 | 831872 | -109439 | 0.46 | 48.6 | 1.56 | -81658 | 240893 | -85537 |
| RB 30m VWAPband k=1.5 globex stop=1.0sd tgt=vwap time=180m | H1 | 0.25 | 0.47 | -66845 | -62801 | 184674 | -69973 | 0.24 | 64.3 | 2.88 | -72319 | 151782 | -87875 |
| RB 30m VWAPband k=1.5 globex stop=1.0sd tgt=vwap time=180m | H2 | 2.60 | 6.13 | -172772 | -150809 | 382577 | -178982 | 4.51 | 38.9 | 3.33 | -69801 | 181682 | -72114 |
| RB 30m VWAPband k=1.5 globex stop=1.0sd tgt=vwap time=180m | all | 1.12 | 2.27 | -122059 | -103361 | 831872 | -178982 | 2.59 | 48.8 | 2.16 | -81135 | 240893 | -87875 |
| SI 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m (diag) | clean | 0.34 | 0.53 | -119505 | -103862 | 544674 | -153528 | 0.57 | 25.7 | 1.47 | -85297 | 295124 | -94929 |
| SI 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m (diag) | H1 | 1.28 | 4.44 | -252439 | -233584 | 1244591 | -262216 | 1.40 | 39.3 | 3.13 | -97669 | 302451 | -104935 |
| SI 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m (diag) | H2 | -1.79 | -2.02 | -612320 | -549620 | 2428269 | -637006 | -1.00 | 41.7 | 0.73 | -127212 | 336854 | -137399 |
| SI 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m (diag) | all | -0.08 | -0.13 | -459068 | -336547 | 3672860 | -637006 | -0.10 | 31.5 | 1.60 | -101141 | 509243 | -137399 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| SI 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m (diag) | -34.2 | -122.8 | -58.3 | -200.4 | 4.1 / 12.2 | -30.4 / -26.8 | NO |
| HG 15m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | -20.9 | -6.2 | 16.1 | 8.2 | 7.5 / 17.4 | 24.6 / 42.4 | NO |
| PL 30m VWAPband k=2.5 globex stop=1.0sd tgt=half time=180m (diag) | -24.3 | -253.2 | -50.7 | -169.6 | 6.9 / 13.1 | -272.3 / -246.2 | NO |
| HO 30m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=180m | -17.6 | -19.9 | -4.3 | 6.5 | -7.3 / 6.7 | 19.1 / 31.0 | NO |
| RB 30m VWAPband k=1.5 globex stop=1.0sd tgt=vwap time=180m | -5.9 | 14.9 | 23.6 | 24.3 | 19.2 / 22.3 | 10.2 / 27.7 | NO |
| NG 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m (diag) | -28.8 | -8.0 | 7.9 | 23.1 | -8.8 / 11.9 | -8.4 / -6.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| SI 1 (diag) 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | gross-positive, cost-negative pre-2023 | 538 | 24.1 | -21.2 | -4.9 | 45.3 | 0.51 / -0.45 / -0.11 | 68.8 / 24.2 |
| SI 2 (diag) 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=60m | gross-positive, cost-negative pre-2023 | 541 | 16.2 | -30.9 | -14.0 | 47.1 | 0.33 / -0.63 / -0.29 | 67.7 / 21.1 |
| SI 3 (diag) 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | gross-positive, cost-negative pre-2023 | 526 | 24.1 | -18.8 | -3.4 | 42.9 | 0.40 / -0.30 / -0.06 | 44.3 / 1.9 |
| HG 1 5m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | negative pre-2023 | 3275 | -2.5 | -25.4 | -19.7 | 22.9 | -0.17 / -1.69 / -1.31 | 37.2 / 15.3 |
| HG 2 30m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | negative pre-2023 | 923 | -7.6 | -30.9 | -24.9 | 23.4 | -0.26 / -1.03 / -0.83 | 47.7 / 25.0 |
| HG 3 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 915 | -9.6 | -36.1 | -29.2 | 26.6 | -0.27 / -1.02 / -0.82 | 36.3 / 10.9 |
| HG 4 15m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | negative pre-2023 | 1685 | -5.0 | -28.1 | -22.3 | 23.1 | -0.25 / -1.36 / -1.08 | 30.0 / 7.5 |
| HG 5 30m VWAPband k=2.5 globex stop=2.0sd tgt=half time=60m | negative pre-2023 | 928 | -1.6 | -26.9 | -20.3 | 25.3 | -0.07 / -1.09 / -0.82 | 33.9 / 9.7 |
| HG 6 (diag) 10m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | gross-positive, cost-negative pre-2023 | 2154 | 1.2 | -21.8 | -16.1 | 23.0 | 0.07 / -1.21 / -0.90 | 36.6 / 14.5 |
| HG 7 (diag) 30m VWAPband k=2.5 globex stop=1.0sd tgt=half time=180m | negative pre-2023 | 933 | -5.1 | -29.8 | -23.3 | 24.7 | -0.22 / -1.26 / -0.99 | 46.3 / 22.0 |
| HG 8 (diag) 5m VWAPband k=2.5 globex stop=2.0sd tgt=half time=60m | negative pre-2023 | 3339 | -0.1 | -24.5 | -18.4 | 24.4 | -0.01 / -2.00 / -1.50 | 28.9 / 5.6 |
| PL 1 (diag) 30m VWAPband k=2.5 globex stop=1.0sd tgt=half time=180m | gross-positive, cost-negative pre-2023 | 923 | 5.9 | -6.4 | -7.3 | 12.3 | 0.30 / -0.32 / -0.37 | 7.6 / -4.6 |
| PL 2 (diag) 10m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | negative pre-2023 | 752 | -1.8 | -15.4 | -16.9 | 13.6 | -0.08 / -0.70 / -0.77 | 8.0 / -5.5 |
| PL 3 (diag) 30m VWAPband k=2.5 globex stop=1.0sd tgt=vwap time=180m | gross-positive, cost-negative pre-2023 | 921 | 3.6 | -9.7 | -10.7 | 13.3 | 0.17 / -0.45 / -0.49 | 9.2 / -4.0 |
| HO 1 30m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=60m | negative pre-2023 | 4591 | -0.7 | -13.0 | -11.5 | 12.2 | -0.07 / -0.82 / -0.74 | 21.3 / 9.2 |
| HO 2 30m VWAPband k=2.0 globex stop=2.0sd tgt=vwap time=60m | negative pre-2023 | 4523 | -5.1 | -17.2 | -15.8 | 12.2 | -0.28 / -0.89 / -0.82 | 21.3 / 9.4 |
| HO 3 15m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 7149 | -10.7 | -22.5 | -21.1 | 11.8 | -0.67 / -1.38 / -1.29 | 17.4 / 5.9 |
| HO 4 30m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 4555 | -2.4 | -14.2 | -12.8 | 11.8 | -0.14 / -0.68 / -0.61 | 16.8 / 5.2 |
| HO 5 30m VWAPband k=2.0 rth stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 2002 | -6.8 | -18.7 | -17.2 | 11.9 | -0.19 / -0.49 / -0.45 | 18.2 / 6.4 |
| HO 6 (diag) 15m VWAPband k=2.0 globex stop=1.0sd tgt=vwap time=60m | negative pre-2023 | 7233 | -7.7 | -20.0 | -18.5 | 12.2 | -0.64 / -1.63 / -1.50 | 17.1 / 5.1 |
| HO 7 (diag) 30m VWAPband k=2.0 globex stop=1.0sd tgt=half time=60m | negative pre-2023 | 4601 | -0.5 | -11.9 | -10.5 | 11.4 | -0.05 / -0.79 / -0.70 | 12.5 / 1.3 |
| HO 8 (diag) 15m VWAPband k=2.0 globex stop=1.0sd tgt=half time=60m | negative pre-2023 | 7304 | -5.7 | -17.0 | -15.7 | 11.3 | -0.55 / -1.58 / -1.45 | 12.7 / 1.6 |
| RB 1 30m VWAPband k=1.5 globex stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 9739 | -8.8 | -20.4 | -19.4 | 11.6 | -0.67 / -1.55 / -1.47 | 16.1 / 4.6 |
| RB 2 5m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | gross-positive, cost-negative pre-2023 | 1930 | 1.2 | -10.7 | -10.0 | 11.9 | 0.02 / -0.32 / -0.30 | 18.7 / 6.9 |
| RB 3 (diag) 30m VWAPband k=1.5 rth stop=1.0sd tgt=vwap time=180m | negative pre-2023 | 4390 | -8.7 | -20.4 | -19.6 | 11.7 | -0.42 / -0.98 / -0.94 | 23.1 / 11.5 |
| RB 4 (diag) 15m VWAPband k=1.5 globex stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 12220 | -12.1 | -23.3 | -22.4 | 11.2 | -0.87 / -1.67 / -1.60 | 12.6 / 1.6 |
| RB 5 (diag) 5m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | negative pre-2023 | 4623 | -21.8 | -33.2 | -32.4 | 11.4 | -0.89 / -1.34 / -1.31 | 15.1 / 3.8 |
| NG 1 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=60m | gross-positive, cost-negative pre-2023 | 284 | 14.0 | -7.2 | -12.0 | 21.2 | 0.24 / -0.12 / -0.21 | 43.4 / 22.7 |
| NG 2 (diag) 15m VWAPband k=2.5 rth stop=1.0sd tgt=half time=60m | gross-positive, cost-negative pre-2023 | 487 | 5.6 | -15.2 | -20.3 | 20.9 | 0.16 / -0.44 / -0.58 | 37.0 / 16.5 |
| NG 3 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=60m | negative pre-2023 | 284 | -3.8 | -27.1 | -32.4 | 23.2 | -0.07 / -0.48 / -0.57 | 36.6 / 13.2 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): HG: 5 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.00, p(top) = 0.37); HO: 5 cells pass the clean rule against a replicate mean of 5.4 (p(count) = 0.60, p(top) = 0.51); NG: 0 cells pass the clean rule against a replicate mean of 0.4 (p(count) = 1.00); PL: 0 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 1.00); RB: 2 cells pass the clean rule against a replicate mean of 5.7 (p(count) = 0.97, p(top) = 0.87); SI: 0 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 1.00).
- Of 12 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.30 (RB 30m VWAPband k=1.5 globex stop=1.0sd tgt=vwap time=180m); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 1; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 11, 'gross-positive, cost-negative pre-2023': 1}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q4a.py (= ap_b4.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q4a/ (`Q4A_CO_all_selected_scored.csv`).

DONE Q4A
