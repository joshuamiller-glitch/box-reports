# REPORT K4_M2 - SK_K4BOOKS under METHOD-2: plateau / power class and the ES-hedged book (2026-10-17)

**Verdict: the K4 book keeps its edge after hedging the index beta, at a lower and more even level; the unhedged book is the better-posed book for the family test, the hedged one is the better-posed book to trade.** Unhedged OOS Sharpe 2.24 (141 weeks, 2024-02..2026-10-16; halves 1.99 / 3.13), drift-matched long-only null rank 1.00 (null mean -0.35, p95 0.47, 183 finite worlds of 200), bootstrap lower bound 0.31 > 0, gates a-d PASS, best-of-F at F_eff 447 = 0.955 (>= 0.95: borderline PASS; F=30: 0.997, F=1,723: 0.85). ES-hedged (short ES futures, beta from the fit window): OOS Sharpe 1.80 (halves 1.87 / 1.95: the H2 'bull-market' advantage 3.13 vs 1.99 disappears), hedged-null rank 1.00 (null p95 0.63), bootstrap lower bound 0.16 > 0, gates a-d PASS, best-of-F at F_eff 447 = 0.54 (FAIL). The K4 alpha after the hedge is real in this sample (Sharpe 1.8, both halves ~1.9) but it is not significant at the family-multiplicity bar.

## What the book contains
26 cells (library daily series, volmatch-scaled to 8-NQ-contract equivalents), all long-only ES/NQ/RTY/YM daily timing with the K4 LightGBM probability, entry and exit at 16:16 ET, 1-day hold: K4v2 (=K4_d2_1_0.08_longonly, identical series) and RW12P (=R12_d2_1_0.08_longonly, identical series); RX5_ens and RX6_ens (5-seed ensembles); the 8 R2 feature ablations (PRICE, PRICE+VIX/COT/CAL, FULL, FULL-VIX/COT/CAL); R3 ridge, R4 fixed-threshold, R14 spec-follow, R10, R9; RX1 (k4lo half-size), RX2, RX3 (r5b), RX7 / RX7P (asymmetric), RX8 (rsi65 exit), RX11 (shorten). NOT in the book: RW5 (K4 size tilt of the PAIR: it is in SK_K4_PAIRVAR), RY5 (E1-based sleeves: basis-void FVG, excluded). Three duplicate pairs (K4v2/K4_d2, RW12P/R12, RX7P/RX7) make the effective cell count 23.

## Plateau breadth / power class (ap_m2c method and variants)
- Share of cells with positive full-window Sharpe: 1.00 (26/26); cell Sharpes 0.53 .. 1.99, median 1.39.
- Adjacent-cell ratio (cell k+1 / cell k, registered order, ap_m2c method): 1.00 (flat (~97%)); per read window (fold) median 1.00; nearest-neighbour-by-correlation ratio 1.00 - but this is inflated by the two exact duplicates. Excluding duplicates: nearest-neighbour ratio 1.01 (flat (~97% class)), registered-order ratio over the 23 unique cells 1.01 (flat (~97% class)).
- Reading: the 26 cells are NOT a parameter grid around one centre; they are variants of one forecaster (feature sets, model classes, exit rules). Dropping features lowers the Sharpe in a graded way (PRICE only 0.99, PRICE+COT 0.58, FULL 1.69, FULL-COT 1.69), so the edge is not a single-cell accident, but the 'power class' is only a statement about how wide the plateau of VARIANTS is: best cell Sharpe 1.99 vs median 1.39. Class: flat (~97% class) on unique cells; treat as intermediate evidence rather than a certified flat plateau.

## ES hedge construction (no look-ahead; cost 1 tick/side on the hedge legs)
- In every 12/3/3 fold the tilt ensemble of the book in library dollars E_t is regressed (OLS with intercept) on the ES 16:16-ET label-day price change in dollars (ES $50/point, back-adjusted close at the last bar at or before 16:16 ET) over the FIT days on which the book holds a position (E_t != 0); the slope b (ES contracts equivalent; fit-window betas 2.5 .. 4.2, median 2.9 contracts for a book sized at the library standard) is frozen for the read window.
- On read days with a position (E_t != 0) the hedge is short b ES contracts for the same 1-day holding period: P&L_h = -b x dES_t - |b| x $29.36 (2 x 1 tick = $25 + $4.36 commission per contract round trip; fractional contracts, rolls ignored; a position-day starts at the 16:16 entry of the K4 signal and ends at the next 16:16, so the hedge is entered and exited with the K4 legs).
- Null (custom drift-matched) for the hedged book: the same 200 long-only random-entry worlds of the K4v2 sleeve (counts per month kept; each world scaled to the real ensemble's daily SD and hedged with its OWN fit-window beta; 17 of 200 worlds are degenerate and dropped, as in the unhedged null).
- Not modelled: the hedge's margin and basis, the ES-NQ-RTY-YM mismatch of the hedge (the long legs are spread over four indices; the hedge uses ES only), execution slippage beyond 1 tick.

## Results (OOS 12/3/3 tilt, first OOS week 2024-02, concatenated to 2026-10-16)
| | unhedged | ES-hedged |
|---|---|---|
| OOS Sharpe | 2.24 | 1.80 |
| halves Sharpe (2024-02..2025-04 / 2025-05..2026-10) | 1.99 / 3.13 | 1.87 / 1.95 |
| halves net (unit) | 40.0 / 33.1 | 32.8 / 19.3 |
| weekly-mean bootstrap 90% interval (unit) | [0.31, 0.73] | [0.16, 0.60] |
| null (drift-matched, 200 worlds): mean / p95 / rank | -0.35 / 0.47 / 1.00 | -0.39 / 0.63 / 1.00 |
| gates a-d | PASS | PASS |
| best-of-F: F_eff 447 / F=30 / PR 56 / nominal 1,723 | 0.957 / 0.997 / 0.995 / 0.845 | 0.552 / 0.961 / 0.928 / 0.101 |
| OOS weekly corr with the ES price change | +0.45 | -0.19 (slightly over-hedged) |
| weekly corr with the live pair (worst decile) | -0.00 (+0.05) | -0.04 (+0.44) |
| at the pair 6/6 DD match ($210k max DD): net | $1.65M | $1.24M |
| worst week at the match | -$191k | -$160k |
| max DD at the match | $210k | $210k |

K4 alpha after hedge: the hedge costs 29% of the net at the same DD (unit net 73.1 -> 52.1; weekly mean 0.52 -> 0.37) and 0.45 of Sharpe, i.e. about 71% of the mean return and 80% of the Sharpe is index-neutral alpha in this sample; the removed part is long-index beta earned in the 2025-26 rally (H2 Sharpe 3.13 -> 1.95). Beta-explained Sharpe of the unhedged book is 0.37 (corr +0.43 x index Sharpe 0.86); the hedged book's residual correlation with ES is -0.19, so a hedge ratio about 20% smaller would be closer to neutral.

## Open-position note and the matrix extension
The SK_K4BOOKS matrix now runs to 2026-10-16 (one more OOS week). The re-run of K4v2, RW12P and RX5 on the extended daily view has no realised trade after 2026-09-24 (last exit labels 20260924 / 20260911 / 20260924), so 2026-10-12..16 carry zero P&L for those cells; the other 18 cells keep their library coverage (last day 2026-10-09). The 2026-10-16 ES long signal (per the weekly extension) exits on Monday 2026-10-19: it is an OPEN position at the end of the data and is not in any P&L figure above.

OOS series saved: outputs/methods2/oos/SK_K4BOOKS.npz (unhedged) and oos/SK_K4BOOKS_ESHEDGED.npz (od = days, op = daily OOS series in harness units). FAMILY_RESULTS.csv carries both rows (the hedged row is a variant of the same book: not an additional independent family for F). Code: ap_m2_k4h.py, ap_m2_k4ext.py, ap_m2_k4_final.py, ap_m2_k4_rep.py.


CORRECTION (F_eff update, 2026-10-17): a778's final compile uses F_eff = 524 (not 447). With the same pooled null the unhedged book's best-of-F rank is about 0.947, i.e. just BELOW 0.95: SK_K4BOOKS does not pass the multiplicity gate (the 0.955 above was at F_eff 447); the ES-hedged book is lower still (about 0.45). Gates a-d and the drift-matched null results are unchanged.

DONE K4M2
