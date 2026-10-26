# REPORT K4_ALTERNATIVES - VIX-free 26, 16:32 clock 26, and the 26-cell 16:16 pack on one engine (2026-10-19)

All books below are the FULL 26 cells (Rule 0). Engine and method: the research engine (ap_sk/ap_k/ap_r/ap_rx cell code, 1 tick/side + $4.36 RT), METHOD-2 OOS 12/3/3 tilt walk-forward (first OOS week 2024-02, last 2026-10-16, ~141 weeks, halves split 2025-05), pack ES hedge (per-fold OLS beta on position days, 1 tick/side + $4.36 per ES contract RT), drift-matched long-only random-entry null (200 K4v2 worlds, counts per month kept, ~185 finite), gates a-d, best-of-F = G(s)^F with G the current pooled family-null CDF (170,400 draws). Dollars: each hedged series is scaled to weekly SD $12,534 (20% of pair risk) exactly as BANDS.json, so mean/p5/p95/net/DD/worst week are comparable across columns. Sharpe, rank and gates are scale-free. Code: code/census/night_ins/ap_k4alt_build.py, ap_k4alt_null.py, ap_k4alt_score.py, ap_k4alt_lag.py; data in outputs/autopilot/k4alt/. Nothing in outputs/k4 touched; UNTOUCHED not read; no purchases.

## Table 1 - the pack's book (26 cells + ES hedge), one column per option
| Metric | Pack 26-cell 16:16 (library series) | Pack rebuilt (same engine) | (a1) VIX-FREE 26, 16:16 | (a2) NOT DEPLOYABLE 9-cell subset | (b) FULL 26 at 16:32 | sens: pack, 6 daily-bar cells moved 16:00 to 16:16 | sens: (a1) with those cells at 16:16 | sens: (b) without SKEW in R12 |
|---|---|---|---|---|---|---|---|---|
| OOS weekly Sharpe | 1.80 | 1.84 | 1.39 | 1.56 | 0.82 | 1.29 | 0.60 | 0.85 |
| Net, OOS 2024-02..2026-10 ($, sized to weekly SD $12,534) | 441,004 | 450,294 | 344,109 | 383,387 | 201,535 | 316,841 | 147,712 | 207,773 |
| Max drawdown ($, daily) | 74,531 | 74,478 | 71,899 | 69,697 | 92,835 | 93,230 | 81,381 | 88,733 |
| Worst week ($) | -56,645 | -56,605 | -35,433 | -33,977 | -36,296 | -63,496 | -34,319 | -39,457 |
| CVaR5 weekly ($) | -19,245 | -19,232 | -21,133 | -16,448 | -21,954 | -20,446 | -22,101 | -20,739 |
| CVaR10 weekly ($) | -13,713 | -13,703 | -16,387 | -13,845 | -15,938 | -13,931 | -17,646 | -15,474 |
| Sortino (weekly) | 3.55 | 3.63 | 2.68 | 3.46 | 1.54 | 2.40 | 1.05 | 1.65 |
| MAR (net/maxDD) | 5.92 | 6.05 | 4.79 | 5.50 | 2.17 | 3.40 | 1.82 | 2.34 |
| % negative weeks | 45.4 | 45.4 | 50.7 | 46.1 | 49.6 | 50.4 | 54.9 | 50.4 |
| Weekly mean ($) | 3,128 | 3,194 | 2,423 | 2,719 | 1,429 | 2,247 | 1,040 | 1,474 |
| Weekly SD ($) | 12,534 | 12,534 | 12,534 | 12,534 | 12,534 | 12,534 | 12,534 | 12,534 |
| Weekly p5 ($) | -9,174 | -9,167 | -13,747 | -12,074 | -10,465 | -10,381 | -15,367 | -10,475 |
| Weekly p95 ($) | 26,580 | 26,561 | 21,134 | 23,948 | 21,071 | 20,371 | 19,455 | 21,151 |
| Sharpe H1 (2024-02..2025-04) | 1.87 | 1.87 | 1.45 | 1.15 | 0.87 | 1.31 | 0.42 | 0.90 |
| Sharpe H2 (2025-05..2026-10) | 1.95 | 2.05 | 1.33 | 1.97 | 0.87 | 1.60 | 0.80 | 0.87 |
| 4-wk block bootstrap 5% bound of weekly mean (unit) | 0.16 | 0.17 | 0.06 | 0.11 | -0.03 | 0.05 | -0.08 | -0.03 |
| Drift-matched null p95 (Sharpe) | 0.63 | 0.63 | 0.41 | 0.63 | 0.35 | 0.63 | 0.41 | 0.35 |
| Null rank | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 0.98 | 1.00 |
| Corr to live pair (weekly) | -0.04 | -0.04 | -0.03 | 0.04 | -0.05 | -0.05 | -0.03 | -0.05 |
| Corr to pair, worst-decile weeks | 0.44 | 0.44 | 0.02 | -0.08 | 0.10 | 0.25 | -0.11 | 0.07 |
| Corr to ES weekly change | -0.19 | -0.19 | -0.38 | -0.31 | -0.31 | -0.12 | -0.36 | -0.32 |
| Corr to NQ weekly change | -0.16 | -0.17 | -0.34 | -0.27 | -0.26 | -0.10 | -0.32 | -0.27 |
| Beta to ES (ES contracts equiv.) | -0.39 | -0.41 | -0.79 | -0.64 | -0.65 | -0.25 | -0.75 | -0.67 |
| Beta to NQ (NQ contracts equiv.) | -0.16 | -0.18 | -0.34 | -0.28 | -0.26 | -0.11 | -0.32 | -0.27 |
| Gate a (Sharpe>0, net>0) | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS |
| Gate b (null rank >= 0.95) | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS |
| Gate c (bootstrap bound > 0) | PASS | PASS | PASS | PASS | FAIL | PASS | FAIL | FAIL |
| Gate d (both halves net > 0) | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS |
| Gates a-d all | PASS | PASS | PASS | PASS | FAIL | PASS | FAIL | FAIL |
| best-of-F, F_eff 1,208 | 0.029 | 0.049 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 |
| best-of-F, F_eff 761 | 0.108 | 0.149 | 0.000 | 0.004 | 0.000 | 0.000 | 0.000 | 0.000 |
| best-of-F, F_eff 594 | 0.177 | 0.226 | 0.000 | 0.013 | 0.000 | 0.000 | 0.000 | 0.000 |
| best-of-F >= 0.95 at 1,208 | FAIL | FAIL | FAIL | FAIL | FAIL | FAIL | FAIL | FAIL |

Columns 1-2 are the baseline scored two ways: the library series in SK_K4BOOKS.npz (reproduces the pack: 1.80 hedged / 2.24 unhedged) and the same 26 cells rebuilt from the engine (1.84 / 2.24; 19 of 26 series identical to the cent, 7 (R2_PRICE, R2_PRICE+COT, R2_PRICE+CAL, R3, R4, RX7, RX7P) differ on isolated days, correlation >= 0.9992). The rebuilt column is the like-for-like base for the options.

## Table 2 - same options, unhedged book (the book the family test used)
| Metric | Pack 26-cell 16:16 (library series) | Pack rebuilt (same engine) | (a1) VIX-FREE 26, 16:16 | (a2) NOT DEPLOYABLE 9-cell subset | (b) FULL 26 at 16:32 | sens: pack, 6 daily-bar cells moved 16:00 to 16:16 | sens: (a1) with those cells at 16:16 | sens: (b) without SKEW in R12 |
|---|---|---|---|---|---|---|---|---|
| OOS weekly Sharpe | 2.24 | 2.24 | 2.05 | 2.24 | 1.48 | 1.67 | 1.27 | 1.50 |
| Net, OOS 2024-02..2026-10 ($, sized to weekly SD $12,534) | 549,777 | 548,672 | 506,717 | 548,744 | 361,970 | 408,283 | 314,528 | 367,292 |
| Max drawdown ($, daily) | 69,803 | 69,789 | 59,403 | 45,609 | 76,283 | 74,075 | 79,979 | 80,119 |
| Worst week ($) | -63,484 | -63,472 | -49,604 | -38,782 | -48,925 | -65,505 | -50,504 | -45,921 |
| CVaR5 weekly ($) | -21,075 | -21,071 | -22,180 | -20,695 | -23,293 | -19,611 | -23,533 | -22,229 |
| CVaR10 weekly ($) | -14,001 | -13,998 | -16,429 | -14,569 | -15,920 | -13,155 | -17,201 | -15,295 |
| Sortino (weekly) | 4.29 | 4.28 | 3.94 | 4.95 | 2.66 | 3.18 | 2.36 | 2.84 |
| MAR (net/maxDD) | 7.88 | 7.86 | 8.53 | 12.03 | 4.75 | 5.51 | 3.93 | 4.58 |
| % negative weeks | 30.5 | 31.2 | 35.2 | 39.0 | 34.0 | 34.8 | 42.3 | 37.6 |
| Weekly mean ($) | 3,899 | 3,891 | 3,568 | 3,892 | 2,567 | 2,896 | 2,215 | 2,605 |
| Weekly SD ($) | 12,534 | 12,534 | 12,534 | 12,534 | 12,534 | 12,534 | 12,534 | 12,534 |
| Weekly p5 ($) | -11,848 | -11,846 | -13,793 | -12,864 | -9,659 | -6,952 | -14,393 | -9,383 |
| Weekly p95 ($) | 25,963 | 25,958 | 23,553 | 23,998 | 21,740 | 19,919 | 19,855 | 20,306 |
| Sharpe H1 (2024-02..2025-04) | 1.99 | 1.99 | 1.87 | 2.10 | 1.16 | 1.40 | 0.81 | 1.19 |
| Sharpe H2 (2025-05..2026-10) | 3.13 | 3.12 | 2.25 | 2.33 | 2.40 | 2.96 | 1.98 | 2.38 |
| 4-wk block bootstrap 5% bound of weekly mean (unit) | 0.31 | 0.31 | 0.22 | 0.28 | 0.15 | 0.20 | 0.08 | 0.16 |
| Drift-matched null p95 (Sharpe) | 0.47 | 0.47 | 0.54 | 0.47 | 0.32 | 0.49 | 0.54 | 0.32 |
| Null rank | 1.00 | 1.00 | 1.00 | 1.00 | 0.99 | 1.00 | 1.00 | 0.99 |
| Corr to live pair (weekly) | -0.00 | -0.00 | 0.04 | 0.03 | 0.00 | -0.02 | 0.03 | 0.00 |
| Corr to pair, worst-decile weeks | 0.05 | 0.05 | 0.09 | -0.00 | 0.20 | -0.02 | -0.02 | 0.17 |
| Corr to ES weekly change | 0.45 | 0.45 | 0.49 | 0.34 | 0.39 | 0.44 | 0.51 | 0.37 |
| Corr to NQ weekly change | 0.42 | 0.42 | 0.46 | 0.35 | 0.37 | 0.41 | 0.47 | 0.36 |
| Beta to ES (ES contracts equiv.) | 0.94 | 0.94 | 1.03 | 0.72 | 0.80 | 0.92 | 1.08 | 0.77 |
| Beta to NQ (NQ contracts equiv.) | 0.42 | 0.43 | 0.45 | 0.36 | 0.37 | 0.42 | 0.47 | 0.35 |
| Gate a (Sharpe>0, net>0) | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS |
| Gate b (null rank >= 0.95) | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS |
| Gate c (bootstrap bound > 0) | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS |
| Gate d (both halves net > 0) | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS |
| Gates a-d all | PASS | PASS | PASS | PASS | PASS | PASS | PASS | PASS |
| best-of-F, F_eff 1,208 | 0.786 | 0.769 | 0.394 | 0.774 | 0.000 | 0.002 | 0.000 | 0.000 |
| best-of-F, F_eff 761 | 0.859 | 0.848 | 0.557 | 0.851 | 0.000 | 0.020 | 0.000 | 0.001 |
| best-of-F, F_eff 594 | 0.888 | 0.879 | 0.633 | 0.882 | 0.003 | 0.048 | 0.000 | 0.004 |
| best-of-F >= 0.95 at 1,208 | FAIL | FAIL | FAIL | FAIL | FAIL | FAIL | FAIL | FAIL |

## Verdict
Neither the VIX-free book nor the 16:32 book preserves K4: (a1) VIX-free 26 at 16:16 scores 1.39 hedged / 2.05 unhedged against 1.84 / 2.24 for the pack (best-of-F at F_eff 1,208: 0.00 / 0.39, FAIL), (b) 26 cells at 16:32 scores 0.82 / 1.48 (hedged fails gate c, best-of-F 0.00), and the pack itself is already below the multiplicity bar at 1,208 (hedged 0.05, unhedged 0.77; it passed at F_eff 455 only on the earlier null pool, 0.954 then, 0.91 on today's pool), so no option passes best-of-F and the choice among them is one of degradation, not of qualification.

## What was done, exactly
* Baseline rebuild: all 26 cells re-run through fam.run (cell dicts from the library INDEX names), volmatch-scaled per cell (lib_save.volmatch_factor, clean span), tilt weights refit per fold by the METHOD-2 rule (the same rule that makes the pack weights; CELLS_WEIGHTS.csv forward weights are the live refit of that rule, not used in OOS scoring).
* (a1) VIX-FREE. Removed from every cell's feature set and refit under the same quarterly walk-forward (LightGBM/ridge, same seeds and hyper-parameters): VIX 252d percentile, VIX/VIX3M, VVIX 252d percentile, 5-day VIX change, and the R12 extension features SKEW percentile, VIX9D/VIX, VIX6M/VIX3M, VIX 20d z (SKEW is an end-of-day series and not available at 16:16 on any clock; it is gone in a1). Cell handling: no cell's own entry rule is a VIX rule. The VIX path enters through (i) the K4 probability (K4, K4V2, R12, R12P, R2_FULL*, R2_PRICE+VIX, R3 ridge, R4, RX5, RX6, RX7, RX7P) which is refit without VIX, and (ii) cells that gate on the K4 probability (RX1 k4lo state, R10 confirmation, RX8) which inherit the refit probability. RX1's VIX states (inversion, VIX percentile) are not the pack's cell (it is the k4lo state) and are not used. Cells that never touched VIX are unchanged (R14, R9, RX2, RX3, RX11, R2_PRICE, R2_PRICE+COT, R2_PRICE+CAL, R2_FULL-VIX). Consequence: the 26 cells are kept but collapse to 18 distinct series after removal (R2_PRICE+VIX = R2_PRICE; R12 = R12P = R2_FULL = R2_FULL-VIX; R2_PRICE+COT = R2_FULL-CAL; R2_PRICE+CAL = R2_FULL-COT; K4 = K4V2; RX7 = RX7P), so the tilt ensemble is less diversified than the pack.
* (a2) REPORT-ONLY, NOT DEPLOYABLE. The literal subset of the original cells whose features need no same-day VIX: R2_PRICE, R2_PRICE+COT, R2_PRICE+CAL, R2_FULL-VIX, R14_spec_follow_0.9, R9_2.0_4, RX2_2_2_0.5, RX3_r5b_3, RX11_F_shorten (9 of 26, no refit; tilt weights re-formed over the 9). It is not deployable for two further reasons: R14 trades GC/CL/ZN/6E/6J COT, 5-day holds (not an index 16:16 cell) and R9/RX2/RX3/RX11 sit on the 16:00 daily-bar clock (see caveat 1).
* (b) 16:32. Every price in the engine moved by the same 16 minutes. Convention (identical shift of the research one, which takes the close of the last 1-minute bar whose open label is <= 16:16 ET, i.e. the 16:17:00 print): decision price and entry = close of the 1-minute bar opened 16:32 (print at 16:33:00, equal to the 16:33 open); exit = the same bar the next trading day (multi-day cells keep their exit-day count); features (returns, SMA, ADR ratios, the daily-bar cells' high/low/close) recomputed on that clock; same-day 16:15 VIX/VIX3M/VVIX closes (the research files); COT lagged as before; costs 1 tick/side + $4.36 RT; ES hedge on the 16:32 ES clock; K4v2 null worlds regenerated on the 16:32 clock with its own entry counts. Sensitivity column: R12/R12P without SKEW (not available at 16:32 either): 0.85 / 1.50, immaterial.
* Noise scale: a one-bar change in the 16:32 daily-bar cutoff moved the (b) result from 1.48 to 1.62 unhedged (0.82 to 0.99 hedged) in a first build I discarded; clock results here carry about +-0.15 Sharpe of construction noise, so read (b) as 'about 0.8-1.0 hedged', not 0.82.

## Where the Sharpe comes from (unhedged, tilt walk-forward, report-only)
| Group | pack 16:16 | VIX-free | 16:32 | pack, daily-bar cells at 16:16 |
|---|---|---|---|---|
| 19 K4-forecaster cells (K4, R12, R2 x8, R3, R4, RX5-7, RX7P) | 1.51 | 0.86 | 1.25 | 1.52 |
| 7 dip/daily-bar cells (R9, R10, RX1, RX2, RX3, RX8, RX11) | 2.19 | 2.21 | 1.72 | 1.66 |
| all 26 | 2.24 | 2.05 | 1.48 | 1.67 |
So the VIX-free book keeps most of its Sharpe only because the seven dip cells do not use VIX; the K4 forecaster itself falls from 1.51 to 0.86 without VIX (K4_d2 cell 1.48 to 1.00). Per-cell OOS Sharpes are in the build logs.

## Lag cost, 16:33 print vs the engine's 16:17 print (OOS 2024-02..2026-10, positive = a long pays more at 16:32)
| Instrument | Days | Mean (pts) | SD (pts) | Median | p5 / p95 (pts) | Mean $/contract | SD $/contract | Mean bp | SD bp |
|---|---|---|---|---|---|---|---|---|---|
| ES | 680 | -0.07 | 6.62 | +0.00 | -4.8 / 5.3 | -3.6 | 331 | -0.14 | 10.6 |
| NQ | 680 | -0.08 | 33.03 | +0.00 | -28.8 / 27.3 | -1.5 | 661 | -0.11 | 14.5 |
| RTY | 680 | -0.07 | 3.45 | +0.00 | -2.3 / 2.4 | -3.6 | 173 | -0.39 | 15.3 |
| YM | 680 | -1.63 | 35.78 | +0.00 | -36.0 / 26.1 | -8.2 | 179 | -0.36 | 7.8 |

| Instrument | K4v2 entry days | Entry-day price diff 16:33 minus 16:17, mean pts (SD) | mean $/contract (SD) | 1-day round-trip lag cost $/contract, mean (SD) |
|---|---|---|---|---|
| ES | 83 | +1.00 (7.59) | +50 (380) | +103 (840) |
| NQ | 69 | +0.00 (31.38) | +0 (628) | -42 (934) |
| RTY | 56 | -0.05 (4.56) | -3 (228) | +4 (266) |
| YM | 51 | +2.37 (52.80) | +12 (264) | -2 (347) |

Entry-lag effects are small against their noise (ES +$103 per contract round trip on K4v2 entry days, SD $840, n=83, t about 1.1; NQ -$42; RTY +$4; YM -$2): the Sharpe loss at 16:32 is not a fill-price cost, it is the signal clock (the dip cells and the forecaster features measured 16 minutes later) plus noise.

## Caveats
1. The pack baseline is not a pure 16:16 book. Six cells (R9, R10, RX1, RX2, RX3, RX11) are built on 16:00-ET daily bars (day_key +8h, close at 16:00), not on the 16:16 label price. A file written at 16:16:30 cannot trade them at 16:00. Moving those six to the 16:16/16:17 print lowers the 26-cell book to 1.67 unhedged / 1.29 hedged (best-of-F at 1,208: 0.00), and the VIX-free version of that tradable book is 1.27 unhedged / 0.60 hedged (hedged: null rank 0.978 passes b, bootstrap bound -0.08 fails gate c). That tradable 16:16 pair of numbers, not 2.24/1.80, is what a 16:16:30 deployment of 26 cells corresponds to on this engine.
2. K4 is long-index timing: unhedged book beta +0.94 ES contracts (+0.43 NQ) at the 20% size, corr to ES +0.45, to NQ +0.42. The pack hedge (fit-window OLS beta) leaves the hedged book slightly net short index (corr to ES -0.19) and the VIX-free and 16:32 books over-hedge more (-0.38, -0.31) because the beta of the position days is re-fit on a different cell mix;
3. Optimism of non-virgin sleeves: the 26 cells were chosen on data that overlaps the OOS window (library cells, feature ablations, exit variants, 3 exact duplicates in the pack, 8 more after VIX removal), the forecaster family was already selected on this history, and F_eff is itself an estimate (1,208 gate basis; 761 and 594 sensitivities shown). Best-of-F is a nearly binary read here: even the pack fails at 1,208.
4. Null: drift-matched long-only random-entry worlds of the K4v2 sleeve (not the 26-cell structure), per POWER2; every option's ranks are ~1.00 against it, so gates b and a, d are weak discriminators; gate c and best-of-F do the discriminating.
5. Hedge and null use the 1-minute offset of the research ES series (hme) as in the pack; the pack's 16:16 label is the 16:17:00 print on the continuous (post-2021 no-halt) tape; pre-2021 halt data are not in the OOS window.
6. The Yahoo 16:15 close is visible only about 16:30 (about 15 min lag); (b) assumes the 16:15 closes are read at 16:32 as the research files (same-day closes); SKEW, if wanted, is not available on any intraday clock.

## Recommendation
Of (a1), (b) and a real-time VIX feed with the 26 cells at 16:16: only the real-time feed keeps the K4 forecaster whole (K4_d2 1.48 versus 1.00 without VIX), and it is the only one that reproduces the pack's 26-cell edge on the forecaster side; (a1) is the best of the two feed-free options on headline numbers (1.39 hedged / 2.05 unhedged) but it is a dip-cell book with a crippled forecaster, and (b) loses about half the hedged Sharpe. If forced to pick today with no new feed I would not deploy either as 'K4'; if the real-time VIX/VVIX/VIX3M feed is available I would run 26 cells at 16:16 with the six daily-bar cells re-timed to the 16:17 print and expect the 16:16 tradable figures of caveat 1 (about 1.3 hedged, 1.7 unhedged), which are themselves below the multiplicity bar, so size it as a paper/forward-test sleeve, not a 20%-of-pair allocation.
