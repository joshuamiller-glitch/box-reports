# REPORT_NETBOOK (updated 2026-10-19 for the FEES standard; the $4.36-per-micro analysis below is kept as history)

## 0. NEW FIRST TABLE - net-book live forms at the FEES.md standard (per contract round trip: MNQ/MES/M2K/MYM 1.78, MCL 2.08; NQ/ES 4.84 not traded in the net books)
Same net-book method as section 2 (cells summed before rounding to micros, half away, 1 tick/side on net turnover, M2 12/3/3 tilt OOS 2024-02..2026-10, 1,000 null worlds). Columns: STD = FEES.md with routing; no-routing = 1.28 (MCL 1.58) sensitivity; 2 ticks/side = STD fees with 2-tick slippage; $4.36 = historical per-micro reference (the section 1 headline). Sharpe is the adjusted/registry basis. WT432 is disabled on NT8: report-only.
| row | cell-sum ideal | net STD fees | net no-routing | net STD, 2 ticks/side | $4.36 historical | net $ (STD) | maxDD | worst wk | CVaR5 / CVaR10 | Sortino | MAR | %neg wk | wk mean / SD / p5 / p95 | gates a-d | null rank | best-of-F 1208 / 761 / 594 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| WT432 | 1.117 | 0.622 | 0.805 | 0.256 | -0.320 | 153,571 | 102,178 | -43,305 | -23,904 / -19,963 | 0.96 | 1.50 | 46 | 1,081 / 12,542 / -18,305 / 24,297 | FAIL(bc) | 0.860 | 6.2e-90 / 6.3e-57 / 1.4e-44 |
| WT432:ATR30_m4 | 0.967 | 0.627 | 0.755 | 0.373 | -0.029 | 155,037 | 95,494 | -44,118 | -23,591 / -19,298 | 1.00 | 1.62 | 49 | 1,092 / 12,549 / -18,495 / 22,306 | FAIL(bc) | 0.848 | 1.3e-88 / 4.4e-56 / 6.1e-44 |
| WT432:ATR20_m4 | 1.004 | 0.578 | 0.730 | 0.274 | -0.204 | 142,740 | 117,877 | -33,729 | -23,688 / -20,237 | 0.88 | 1.21 | 45 | 1,005 / 12,540 / -17,816 / 23,131 | FAIL(bc) | 0.825 | 6.3e-101 / 7.5e-64 / 5.3e-50 |
| WT432:ATR10_m3 | 1.132 | 0.476 | 0.725 | -0.023 | -0.808 | 117,425 | 88,430 | -43,288 | -25,133 / -20,841 | 0.70 | 1.33 | 46 | 827 / 12,534 / -19,530 / 20,563 | FAIL(bc) | 0.802 | 3.4e-131 / 6.4e-83 / 7.0e-65 |
| WT432 no locks | 0.718 | 0.226 | 0.405 | -0.132 | -0.694 | 55,635 | 116,565 | -46,270 | -26,363 / -21,728 | 0.33 | 0.48 | 44 | 392 / 12,518 / -19,427 / 23,739 | FAIL(bcd) | 0.663 | 5.8e-233 / 5.0e-147 / 6.3e-115 |
| WT432 targets on touch | 1.140 | 0.646 | 0.831 | 0.277 | -0.303 | 159,814 | 100,016 | -42,698 | -24,032 / -20,027 | 1.00 | 1.60 | 47 | 1,125 / 12,560 / -19,085 / 24,095 | FAIL(bc) | 0.868 | 3.9e-84 / 2.8e-53 / 9.7e-42 |
| WT432:ATR30_m3 | 0.731 | 0.269 | 0.443 | -0.080 | -0.628 | 66,475 | 185,361 | -37,084 | -24,411 / -20,696 | 0.40 | 0.36 | 45 | 468 / 12,552 / -19,951 / 19,961 | FAIL(bcd) | 0.706 | 1.6e-212 / 3.8e-134 / 7.2e-105 |
| WT432:ATR14_m4 | 0.608 | 0.195 | 0.352 | -0.120 | -0.617 | 48,023 | 134,018 | -38,974 | -25,623 / -21,369 | 0.28 | 0.36 | 46 | 338 / 12,534 / -19,977 / 21,210 | FAIL(bc) | 0.630 | 1.6e-248 / 7.9e-157 / 1.4e-122 |
| WT432:ATR10_m2 | 0.427 | -0.190 | 0.035 | -0.641 | -1.356 | -46,646 | 224,559 | -45,222 | -25,590 / -21,735 | -0.27 | -0.21 | 53 | -328 / 12,474 / -20,114 / 20,462 | FAIL(abcd) | 0.393 | 0.0e+00 / 3.2e-319 / 2.5e-249 |
| WT432:ATR20_m2 | 0.322 | -0.282 | -0.050 | -0.745 | -1.476 | -69,460 | 241,224 | -33,491 | -28,255 / -23,721 | -0.38 | -0.29 | 51 | -489 / 12,514 / -22,022 / 20,023 | FAIL(abcd) | 0.340 | 0.0e+00 / 0.0e+00 / 1.2e-289 |
| WT432:ATR20_m3 | 0.400 | -0.150 | 0.054 | -0.559 | -1.203 | -37,193 | 189,662 | -47,557 | -26,239 / -21,693 | -0.21 | -0.20 | 47 | -262 / 12,552 / -17,830 / 21,288 | FAIL(abcd) | 0.416 | 0.0e+00 / 6.2e-299 / 1.7e-233 |
| WT432:ATR14_m3 (does not reproduce) | 1.100 | 0.580 | 0.779 | 0.181 | -0.448 | 143,197 | 107,444 | -42,438 | -27,221 / -22,822 | 0.84 | 1.33 | 45 | 1,008 / 12,547 / -23,031 / 21,088 | FAIL(bc) | 0.851 | 1.5e-100 / 1.3e-63 / 8.1e-50 |
| C11DIP | 1.446 | 1.432 | 1.436 | 1.418 | 1.408 | 352,277 | 74,495 | -33,287 | -26,856 / -17,349 | 2.65 | 4.73 | 59 | 2,481 / 12,494 / -17,524 / 25,334 | PASS | 0.987 | 8.4e-07 / 1.5e-04 / 1.0e-03 |
| CL240 (40 cells; C10S1_CL240) | 1.643 | 1.569 | 1.592 | 1.478 | 1.465 | 386,327 | 46,487 | -34,622 | -19,591 / -15,103 | 3.46 | 8.31 | 46 | 2,721 / 12,501 / -13,320 / 19,850 | PASS | 0.995 | 1.8e-04 / 4.4e-03 / 1.4e-02 |
| CL240 trade-through | 1.640 | 1.567 | 1.589 | 1.476 | 1.463 | 386,093 | 46,842 | -34,614 | -19,610 / -15,122 | 3.45 | 8.24 | 46 | 2,719 / 12,515 / -13,320 / 19,934 | PASS | 0.994 | 1.7e-04 / 4.2e-03 / 1.4e-02 |
| C10S1_CL:240_lr | 1.645 | 1.596 | 1.612 | 1.533 | 1.524 | 392,488 | 34,622 | -20,156 | -15,453 / -11,925 | 4.67 | 11.34 | 56 | 2,764 / 12,485 / -10,070 / 19,414 | PASS | 0.995 | 4.1e-04 / 7.4e-03 / 2.2e-02 |
| C10S1_CL:240_macd | 1.359 | 1.285 | 1.306 | 1.202 | 1.190 | 316,687 | 53,829 | -38,470 | -23,136 / -16,728 | 2.50 | 5.88 | 23 | 2,230 / 12,512 / -11,765 / 24,714 | PASS | 0.984 | 4.8e-11 / 3.2e-07 / 8.4e-06 |
| BM13_NQ 6-cell | 1.769 | 1.660 | 1.701 | 1.579 | 1.449 | 409,702 | 57,078 | -40,501 | -21,439 / -16,420 | 3.28 | 7.18 | 42 | 2,885 / 12,530 / -13,876 / 25,691 | PASS | 0.998 | 1.9e-03 / 1.9e-02 / 4.6e-02 |
| BM13 3-cell | 1.913 | 1.796 | 1.839 | 1.709 | 1.572 | 441,847 | 59,371 | -38,519 | -19,395 / -15,383 | 3.80 | 7.44 | 42 | 3,112 / 12,496 / -13,403 / 29,668 | PASS | 0.999 | 2.8e-02 / 1.1e-01 / 1.7e-01 |

Readings: **WT432 at the standard fees: 0.62 (no-routing 0.81), gates b and c FAIL (null rank 0.860, bootstrap lower bound <0), best-of-F FAIL; no locks 0.23.** Report-only (disabled on NT8). C11DIP 1.432 (cost nearly irrelevant), CL240 1.569, C10S1_CL:240_lr 1.596, macd 1.285, BM13 6-cell 1.660, BM13 3-cell 1.796 (selection-contaminated): gates a-d PASS for all four; best-of-F FAIL for all (best: BM13 3-cell 0.028 / 0.11 / 0.17 at F_eff 1,208 / 761 / 594, still < 0.95). The six extra WT432 grids and ATR14_m3 (non-reproducing) are for completeness. Fee flags: NQ/MNQ/M2K/MYM/MCL components are proxies or weak evidence (FEES.md flags 1-3); a real NT statement settles them. Series: NET_SERIES*.csv now also carry net_adj_feeSTD / net_adj_feeNOROUT / net_raw_feeSTD / net_raw_feeNOROUT; BANDS_NET.json carries fee_standard and rows[*].bands_fee_standard.

---

Task: user note (AUTOPILOT.md, NET-POSITION): the NT8 WT432Strat and the chart-3 strategies hold the NET position (cells summed before rounding to micros). B7X and BTCWT are disabled on NT8 as of 2026-10-19 (negative at real fees): report-only in PAPER-ALL, not rescored. ET clock; UNTOUCHED not read; no purchases; research only.

## 1. Table (adjusted/registry-basis OOS Sharpe, M2 12/3/3 tilt, OOS 2024-02..2026-10; columns = commission per MICRO contract round trip, 1 tick/side slippage on net turnover)
| row | cell-sum ideal | net frac $0.436 | $0.436 | $0.50 | $1.00 | $2.00 | $4.36 (headline) | slip 2 tk @ $4.36 | gates a-d @4.36 | null rank @4.36 | best-of-F @4.36 1208/761/594 | edge dies (adj Sharpe < 0.5) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| WT432 | 1.117 | 1.131 | 1.115 | 1.092 | 0.908 | 0.541 | -0.320 | -0.684 | FAIL | 0.299 | 0.0e+00 / 0.0e+00 / 1.6e-307 | $2.25 |
| WT432:ATR30_m4 | 0.967 | 0.971 | 0.971 | 0.954 | 0.826 | 0.571 | -0.029 | -0.282 | FAIL | 0.483 | 0.0e+00 / 1.2e-241 / 8.9e-189 | $2.50 |
| WT432:ATR20_m4 | 1.004 | 1.011 | 0.988 | 0.968 | 0.816 | 0.511 | -0.204 | -0.506 | FAIL | 0.352 | 0.0e+00 / 0.0e+00 / 1.4e-255 | $2.25 |
| WT432:ATR10_m3 | 1.132 | 1.147 | 1.147 | 1.115 | 0.865 | 0.366 | -0.808 | -1.303 | FAIL | 0.089 | 0.0e+00 / 0.0e+00 / 0.0e+00 | $1.75 |
| WT432_nolock | 0.718 | 0.732 | 0.709 | 0.686 | 0.506 | 0.147 | -0.694 | -1.048 | FAIL | 0.126 | 0.0e+00 / 0.0e+00 / 0.0e+00 | $1.25 |
| WT432_touch | 1.140 | 1.154 | 1.143 | 1.119 | 0.934 | 0.565 | -0.303 | -0.669 | FAIL | 0.306 | 0.0e+00 / 0.0e+00 / 1.8e-299 | $2.25 |
| WT432:ATR30_m3 | 0.731 | 0.739 | 0.739 | 0.716 | 0.541 | 0.192 | -0.628 | -0.974 | FAIL | 0.155 | 0.0e+00 / 0.0e+00 / 0.0e+00 | $1.25 |
| WT432:ATR14_m4 | 0.608 | 0.615 | 0.618 | 0.598 | 0.440 | 0.125 | -0.617 | -0.931 | FAIL | 0.160 | 0.0e+00 / 0.0e+00 / 0.0e+00 | $1.00 |
| WT432:ATR10_m2 | 0.427 | 0.439 | 0.413 | 0.385 | 0.161 | -0.289 | -1.356 | -1.811 | FAIL | 0.013 | 0.0e+00 / 0.0e+00 / 0.0e+00 | $0.25 |
| WT432:ATR20_m2 | 0.322 | 0.335 | 0.342 | 0.312 | 0.080 | -0.384 | -1.476 | -1.937 | FAIL | 0.004 | 0.0e+00 / 0.0e+00 / 0.0e+00 | $0.25 |
| WT432:ATR20_m3 | 0.400 | 0.411 | 0.399 | 0.372 | 0.168 | -0.240 | -1.203 | -1.610 | FAIL | 0.024 | 0.0e+00 / 0.0e+00 / 0.0e+00 | $0.25 |
| WT432:ATR14_m3 | 1.100 | 1.114 | 1.116 | 1.090 | 0.891 | 0.492 | -0.448 | -0.845 | FAIL | 0.225 | 0.0e+00 / 0.0e+00 / 0.0e+00 | $2.00 |
| C11DIP | 1.446 | 1.446 | 1.444 | 1.444 | 1.439 | 1.430 | 1.408 | 1.394 | PASS | 0.987 | 2.2e-07 / 6.5e-05 / 5.4e-04 | > 4.5 |
| CL240 | 1.643 | 1.641 | 1.644 | 1.641 | 1.618 | 1.573 | 1.465 | 1.374 | PASS | 0.992 | 3.0e-06 / 3.4e-04 / 1.9e-03 | > 4.5 |
| CL240_tt | 1.640 | 1.638 | 1.641 | 1.638 | 1.615 | 1.570 | 1.463 | 1.372 | PASS | 0.992 | 2.8e-06 / 3.2e-04 / 1.9e-03 | > 4.5 |
| CL240_lr | 1.645 | 1.642 | 1.648 | 1.646 | 1.630 | 1.599 | 1.524 | 1.460 | PASS | 0.992 | 4.3e-05 / 1.8e-03 / 7.1e-03 | > 4.5 |
| CL240_macd | 1.359 | 1.357 | 1.354 | 1.351 | 1.330 | 1.289 | 1.190 | 1.107 | PASS | 0.973 | 2.3e-15 / 6.1e-10 / 6.4e-08 | > 4.5 |
| BM13_6 | 1.769 | 1.770 | 1.770 | 1.765 | 1.724 | 1.643 | 1.449 | 1.366 | PASS | 0.993 | 1.6e-06 / 2.2e-04 / 1.4e-03 | > 4.5 |
| BM13_3 | 1.913 | 1.913 | 1.911 | 1.905 | 1.863 | 1.777 | 1.572 | 1.485 | PASS | 0.999 | 2.0e-04 / 4.7e-03 / 1.5e-02 | > 4.5 |

Reading: "cell-sum ideal" = the K4-EXACT live-form book (cells booked separately, fractional, $4.36 per full contract) and reproduces the audit (WT432 1.117, C11DIP 1.446, CL240 1.643, BM13 1.769). "net frac" nets the cells but does not round. $0.436 per micro = the scored cost basis ($4.36 per full contract). The headline column is the standing $4.36 per contract applied per MICRO. Gates are a-d of the registry (null = common-week sign-flip, 1,000 worlds, MC se about 0.007 on the rank). Best-of-F is G(Sharpe)^F with the pooled null; a pass needs >= 0.95: nothing passes.

### Verdict per pack
- **WT432 - NOT VIABLE at $4.36 per micro (Sharpe -0.32, net -$79k), CONDITIONAL on the real MNQ round-trip fee.** Net-book Sharpe 1.115 at $0.436, 1.09 at $0.50, 0.91 at $1.00, 0.54 at $2.00, -0.32 at $4.36. Gates a-d PASS up to about $0.50 and FAIL (b: null rank 0.938; c: bootstrap lower bound <0) at $1.00. Sharpe falls below 0.5 above about $2.1; net P&L is negative above about $3.5. With 2 ticks/side slippage: 0.72 at $0.50, 0.54 at $1.00, 0.18 at $2.00. Without the per-cell account locks (unmapped; the netted-account lock variant has no spec) it is 0.71 at $0.436 and fails the gates at every fee. WT432:ATR20_m4 fails gate c even at $0.436 (null rank 0.948, boot lo -7). Best-of-F FAIL (about 1e-20 / 1e-12 / 1e-9 at $0.436). The audit's 1.711 / 0.049 (fixed in-sample weights) is reproduced on the same footing (1.662 / 0.001, window 2024-02..2026-10); the walk-forward OOS numbers here are the honest ones.
- **C11DIP - unchanged by netting; gates PASS at every fee; best-of-F FAIL.** 1.444 cost-neutral, 1.408 at $4.36 per micro (raw realised 1.745). Long-only cells: nothing cancels, rounding to micros costs 0.002 (truncation instead of rounding 0.03). Still PROVISIONAL (best-of-F 2e-7 / 6.5e-5 / 5.4e-4 at $4.36).
- **CL240 - gates PASS at every fee; best-of-F FAIL.** 40-cell net book 1.644 / 1.465 at $4.36 per MCL; lr alone 1.524, macd alone 1.190 at $4.36. Targets needing trade-through 1.463; 2 ticks/side 1.374. Best-of-F 3.0e-6 / 3.4e-4 / 1.9e-3 at $4.36 (1.4e-3 / 1.6e-2 / 4.0e-2 at the scored cost). Maximum concurrent exposure 217 MCL (21.7 CL).
- **BM13 - gates PASS at every fee; best-of-F FAIL.** 6-cell mechanical book 1.770 / 1.449 at $4.36 per MNQ; the pack's 3 hand-picked cells 1.911 / 1.572 (selection-contaminated, use the 6-cell as the honest number). Best-of-F 3-cell 2e-4 / 4.7e-3 / 1.5e-2 at $4.36 (still < 0.95).
- **No codepack sleeve passes best-of-F in the net form; none changes verdict class versus the K4-EXACT live form except WT432 at a per-micro $4.36, where it dies.**

## 2. Method (netlib.py, runner.py in outputs/autopilot/netbook)
1. Cells: the audit's live-form cells (WT432 `block+clock+tgt+early` with the per-cell virtual lock engine, X identical to the audit matrices to 0.0; C11DIP 16:00-open fills; CL240 current ap_c10_s1_core with the 16:55 flatten fix, targets on touch, `tt` = 1 tick through; BM13 as audited). Each cell contributes a signed leg (entry bar, last held bar, side x lock flag).
2. Weights: M2 12/3/3 tilt refit per fold on the drift-adjusted cell matrix (the registry route), WT432 per grid then equal-risk 1/3. Scale f fixed so the fractional cell-sum book has weekly SD $12,534 (the common 20% size).
3. Net book: per bar N = sum_cells coef x s x leg (native contracts, signed, BEFORE rounding), micro target T = round(10 N) half away from zero (the packs state no rounding rule; CELLS_WEIGHTS uses Python round per cell; NT8 integer cast not stated). Sensitivities: half-even (identical to half-away except ties), truncation toward zero, hysteresis 0.25 / 0.5 micro.
4. P&L: net = per-cell ideal + added-back per-cell costs + rounding-error P&L ((T-N)/10 x price move x point value over each bar) - net turnover cost |dT| x (slip ticks x micro tick value + RT commission / 2). Fills: next print +1 tick per side on every net change (2 ticks sensitivity). Entry/exit prices of the cells are the audited ones. Approximations: rounding error is booked on the bar close-open (1-min) or close-close (daily) move; stop exits on daily bars are carried to the bar close for position purposes; net turnover charges the slippage on target (limit) exits too (conservative for brk cells).
5. Null: common-week sign flip on the drift-adjusted matrix with weights refit per world (1,000 worlds); the actual net delta (rounding error + cost) is added with the same weekly sign. Gates a-d, boot lower bound, best-of-F (pooled G^F) as in scorelib. Frozen pack weights over the OOS window are also run (informational, weights in-sample).
6. Account locks: the per-cell lock engine (as scored). The pack gives no netted-account lock spec, so the `no locks` WT432 variant bounds it.
7. Window 2023-02..2026-10-16 as in the audit (OOS from 2024-02-01, 155 weeks incl. stub). UNTOUCHED files were not opened; forward weeks from 2026-10-19 remain the only holdout.

## 3. Netting effect, turnover and size (headline row, $4.36)
| row | cell trades (legs) | cell orders (2 x legs) | net order bars (dT != 0) | orders cancelled/merged | cell-sum turnover (micros) | net fractional turnover | net integer turnover | turnover cancelled by netting | integer vs fractional | mean abs micros held (all bars) | in-position p50 / p90 / p99 / max |
|---|---|---|---|---|---|---|---|---|---|---|---|
| WT432 | 141,751 | 283,502 | 59,766 | 78.9% | 185,536 | 180,805 | 180,618 | 2.5% | -0.1% | NQ(MNQ) 10.3 / 9 24 45 76 |
| WT432:ATR30_m4 | 34,917 | 69,834 | 25,688 | 63.2% | 127,270 | 125,799 | 125,746 | 1.2% | -0.0% | NQ(MNQ) 8.4 / 8 23 46 69 |
| WT432:ATR20_m4 | 39,018 | 78,036 | 27,304 | 65.0% | 151,848 | 149,650 | 149,876 | 1.4% | +0.2% | NQ(MNQ) 9.5 / 9 26 48 64 |
| WT432:ATR10_m3 | 67,816 | 135,632 | 43,545 | 67.9% | 251,510 | 246,421 | 246,120 | 2.0% | -0.1% | NQ(MNQ) 12.6 / 11 31 54 79 |
| WT432_nolock | 177,427 | 354,854 | 66,121 | 81.4% | 181,508 | 176,632 | 176,644 | 2.7% | +0.0% | NQ(MNQ) 9.3 / 8 20 39 68 |
| WT432_touch | 142,819 | 285,638 | 59,875 | 79.0% | 186,943 | 182,059 | 182,200 | 2.6% | +0.1% | NQ(MNQ) 10.4 / 9 24 45 76 |
| WT432:ATR30_m3 | 46,379 | 92,758 | 34,238 | 63.1% | 174,732 | 172,040 | 172,312 | 1.5% | +0.2% | NQ(MNQ) 9.7 / 9 24 44 64 |
| WT432:ATR14_m4 | 32,931 | 65,862 | 24,062 | 63.5% | 158,023 | 155,596 | 155,368 | 1.5% | -0.1% | NQ(MNQ) 10.6 / 10 29 49 64 |
| WT432:ATR10_m2 | 46,085 | 92,170 | 37,381 | 59.4% | 225,505 | 221,215 | 220,920 | 1.9% | -0.1% | NQ(MNQ) 11.4 / 11 28 48 57 |
| WT432:ATR20_m2 | 43,977 | 87,954 | 35,981 | 59.1% | 232,970 | 228,711 | 228,650 | 1.8% | -0.0% | NQ(MNQ) 11.9 / 11 30 52 61 |
| WT432:ATR20_m3 | 43,519 | 87,038 | 34,411 | 60.5% | 205,950 | 202,131 | 201,928 | 1.9% | -0.1% | NQ(MNQ) 10.8 / 10 26 47 69 |
| WT432:ATR14_m3 | 43,052 | 86,104 | 34,044 | 60.5% | 201,495 | 196,734 | 196,904 | 2.4% | +0.1% | NQ(MNQ) 11.0 / 9 28 48 71 |
| C11DIP | 1,213 | 2,426 | 537 | 77.9% | 5,054 | 4,851 | 4,844 | 4.0% | -0.1% | NQ(MNQ) 1.4 / 5 10 14 14; ES(MES) 4.7 / 13 46 70 70; RTY(M2K) 5.2 / 13 40 78 78; YM(MYM) 3.2 / 6 27 87 92 |
| CL240 | 2,346 | 4,692 | 843 | 82.0% | 23,322 | 22,927 | 22,920 | 1.7% | -0.0% | CL(MCL) 13.9 / 28 101 155 217 |
| CL240_tt | 2,322 | 4,644 | 833 | 82.1% | 23,298 | 22,904 | 22,888 | 1.7% | -0.1% | CL(MCL) 13.9 / 28 101 155 217 |
| CL240_lr | 1,167 | 2,334 | 482 | 79.3% | 17,279 | 17,318 | 17,310 | -0.2% | -0.0% | CL(MCL) 10.3 / 23 106 173 192 |
| CL240_macd | 1,179 | 2,358 | 448 | 81.0% | 20,855 | 20,529 | 20,520 | 1.6% | -0.0% | CL(MCL) 12.8 / 51 154 208 208 |
| BM13_6 | 999 | 1,998 | 896 | 55.2% | 42,031 | 41,819 | 41,806 | 0.5% | -0.0% | NQ(MNQ) 0.8 / 51 74 112 145 |
| BM13_3 | 966 | 1,932 | 884 | 54.2% | 44,370 | 44,370 | 44,376 | -0.0% | +0.0% | NQ(MNQ) 0.8 / 51 103 106 106 |

"orders cancelled/merged" = 1 - net order bars / (2 x cell trades): simultaneous cell orders collapse into one net order. "turnover cancelled by netting" = 1 - net fractional micros traded / cell-sum micros: opposite cell orders that really offset. Integer vs fractional = extra churn from the rounding. Netting is almost purely an order-count benefit, not a cost benefit: the cost saving is 0.5-4% of contract turnover, so per-micro commission decides the outcome exactly as the cell-sum book at the same per-micro rate.
Size distribution: WT432 holds on average 10.3 MNQ (p50 9, p90 24, p99 45, max 76) while the sum of the cell sizes at the forward weights is 46.8 MNQ; BM13 holds 51 MNQ (5.1 NQ) in its 35-minute window; CL240 up to 217 MCL; C11DIP per instrument (MNQ 14 max, MES 70, M2K 78, MYM 92).

## 4. Full metric tables (adjusted/registry basis; raw realised in column 3)

### WT432 combined (pack row)
| fee/micro RT | adj Sharpe | raw Sharpe | net $ (adj) | maxDD | worst wk | CVaR5 | CVaR10 | Sortino | MAR | %neg wk | wk mean | wk SD | wk p5 | wk p95 | gates | null rank | boot lo | best-of-F 1208 / 761 / 594 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.436 | 1.115 | 1.127 | 274,946 | 88,383 | -42,309 | -22,925 | -19,061 | 1.82 | 3.11 | 42 | 1,936 | 12,521 | -17,255 | 25,312 | PASS | 0.974 | 294 | 5.8e-20 / 7.6e-13 / 3.5e-10 |
| 1.0 | 0.908 | 0.920 | 224,012 | 94,172 | -42,727 | -23,336 | -19,439 | 1.44 | 2.38 | 45 | 1,578 | 12,529 | -17,696 | 24,886 | FAIL(bc) | 0.938 | -62 | 5.2e-39 / 7.6e-25 / 1.5e-19 |
| 4.36 | -0.320 | -0.308 | -79,426 | 192,495 | -45,217 | -25,782 | -21,743 | -0.44 | -0.41 | 52 | -559 | 12,588 | -20,320 | 22,361 | FAIL(abcd) | 0.299 | -2236 | 0.0e+00 / 0.0e+00 / 1.6e-307 |
| ideal cell-sum | 1.117 | 1.129 | 275,645 | 89,601 | -42,791 | -22,965 | -19,085 | 1.82 | 3.08 | 42 | 1,941 | 12,534 | -17,750 | 25,039 | PASS | 0.973 | 310 | 7.6e-20 / 9.0e-13 / 4.0e-10 |

Rounding / slippage variants (adjusted Sharpe):

| variant | fee $0.50 | fee $1.00 | fee $2.00 | fee $4.36 |
|---|---|---|---|---|
| round half away (headline) | 1.092 | 0.908 | 0.541 | -0.320 |
| round half even | 1.092 | 0.908 | - | -0.320 |
| truncate toward 0 | 1.127 | 0.943 | - | -0.288 |
| hysteresis 0.25 | 1.104 | 0.924 | 0.566 | -0.275 |
| hysteresis 0.50 | 1.144 | 0.969 | 0.619 | -0.204 |
| half away, 2 ticks/side | 0.724 | 0.541 | 0.175 | -0.684 |

Frozen pack weights over the OOS window (informational; ideal -> net): 1.662 -> 1.662 ($0.436) / 0.001 ($4.36)

### WT432:ATR30_m4
| fee/micro RT | adj Sharpe | raw Sharpe | net $ (adj) | maxDD | worst wk | CVaR5 | CVaR10 | Sortino | MAR | %neg wk | wk mean | wk SD | wk p5 | wk p95 | gates | null rank | boot lo | best-of-F 1208 / 761 / 594 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.436 | 0.971 | 0.948 | 239,539 | 85,960 | -43,410 | -22,952 | -18,655 | 1.62 | 2.79 | 47 | 1,687 | 12,534 | -17,949 | 22,974 | PASS | 0.952 | 114 | 7.3e-32 / 2.4e-20 / 4.9e-16 |
| 1.0 | 0.826 | 0.803 | 204,078 | 89,961 | -43,707 | -23,214 | -18,925 | 1.35 | 2.27 | 48 | 1,437 | 12,540 | -18,136 | 22,693 | FAIL(bc) | 0.920 | -139 | 4.0e-50 / 7.6e-32 / 5.1e-25 |
| 4.36 | -0.029 | -0.052 | -7,175 | 124,523 | -45,478 | -24,878 | -20,533 | -0.04 | -0.06 | 54 | -51 | 12,583 | -19,984 | 21,040 | FAIL(abcd) | 0.483 | -1647 | 0.0e+00 / 1.2e-241 / 8.9e-189 |
| ideal cell-sum | 0.967 | 0.944 | 238,695 | 85,847 | -43,492 | -22,976 | -18,707 | 1.61 | 2.78 | 47 | 1,681 | 12,534 | -18,543 | 22,832 | PASS | 0.951 | 94 | 3.5e-32 / 1.5e-20 / 3.4e-16 |

Rounding / slippage variants (adjusted Sharpe):

| variant | fee $0.50 | fee $1.00 | fee $2.00 | fee $4.36 |
|---|---|---|---|---|
| round half away (headline) | 0.954 | 0.826 | 0.571 | -0.029 |
| round half even | 0.954 | 0.826 | - | -0.029 |
| truncate toward 0 | 0.935 | 0.808 | - | -0.040 |
| hysteresis 0.25 | 0.967 | 0.841 | 0.588 | -0.005 |
| hysteresis 0.50 | 0.973 | 0.848 | 0.598 | 0.012 |
| half away, 2 ticks/side | 0.699 | 0.571 | 0.317 | -0.282 |

Frozen pack weights over the OOS window (informational; ideal -> net): 1.559 -> 1.553 ($0.436) / 0.152 ($4.36)

### WT432:ATR20_m4
| fee/micro RT | adj Sharpe | raw Sharpe | net $ (adj) | maxDD | worst wk | CVaR5 | CVaR10 | Sortino | MAR | %neg wk | wk mean | wk SD | wk p5 | wk p95 | gates | null rank | boot lo | best-of-F 1208 / 761 / 594 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.436 | 0.988 | 1.008 | 243,457 | 106,299 | -32,815 | -22,865 | -19,450 | 1.58 | 2.29 | 44 | 1,714 | 12,517 | -17,065 | 23,725 | FAIL(bc) | 0.948 | -7 | 3.7e-30 / 2.9e-19 / 3.4e-15 |
| 1.0 | 0.816 | 0.836 | 201,192 | 110,942 | -33,199 | -23,209 | -19,780 | 1.28 | 1.81 | 44 | 1,417 | 12,527 | -17,371 | 23,476 | FAIL(bc) | 0.904 | -311 | 8.5e-52 / 6.7e-33 / 7.7e-26 |
| 4.36 | -0.204 | -0.184 | -50,600 | 210,012 | -35,484 | -25,315 | -21,748 | -0.29 | -0.24 | 51 | -356 | 12,589 | -19,604 | 21,990 | FAIL(abcd) | 0.352 | -2106 | 0.0e+00 / 0.0e+00 / 1.4e-255 |
| ideal cell-sum | 1.004 | 1.024 | 247,833 | 105,377 | -32,736 | -22,763 | -19,444 | 1.62 | 2.35 | 43 | 1,745 | 12,534 | -17,141 | 24,380 | FAIL | 0.949 | 31 | 1.4e-28 / 2.9e-18 / 2.0e-14 |

Rounding / slippage variants (adjusted Sharpe):

| variant | fee $0.50 | fee $1.00 | fee $2.00 | fee $4.36 |
|---|---|---|---|---|
| round half away (headline) | 0.968 | 0.816 | 0.511 | -0.204 |
| round half even | 0.968 | 0.816 | - | -0.204 |
| truncate toward 0 | 1.008 | 0.856 | - | -0.158 |
| hysteresis 0.25 | 0.964 | 0.812 | 0.511 | -0.198 |
| hysteresis 0.50 | 0.964 | 0.814 | 0.514 | -0.189 |
| half away, 2 ticks/side | 0.663 | 0.511 | 0.207 | -0.506 |

Frozen pack weights over the OOS window (informational; ideal -> net): 1.421 -> 1.422 ($0.436) / -0.016 ($4.36)

### WT432:ATR10_m3
| fee/micro RT | adj Sharpe | raw Sharpe | net $ (adj) | maxDD | worst wk | CVaR5 | CVaR10 | Sortino | MAR | %neg wk | wk mean | wk SD | wk p5 | wk p95 | gates | null rank | boot lo | best-of-F 1208 / 761 / 594 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.436 | 1.147 | 1.193 | 282,818 | 72,051 | -42,040 | -23,902 | -19,648 | 1.82 | 3.93 | 42 | 1,992 | 12,519 | -18,424 | 21,784 | PASS | 0.971 | 541 | 6.4e-18 / 1.5e-11 / 3.5e-09 |
| 1.0 | 0.865 | 0.911 | 213,412 | 78,071 | -42,564 | -24,418 | -20,143 | 1.33 | 2.73 | 43 | 1,503 | 12,525 | -18,888 | 21,272 | FAIL(b) | 0.937 | 50 | 1.4e-44 / 2.3e-28 / 2.7e-22 |
| 4.36 | -0.808 | -0.762 | -200,070 | 250,039 | -45,682 | -27,496 | -23,213 | -1.04 | -0.80 | 54 | -1,409 | 12,572 | -21,652 | 18,545 | FAIL(abcd) | 0.089 | -2889 | 0.0e+00 / 0.0e+00 / 0.0e+00 |
| ideal cell-sum | 1.132 | 1.178 | 279,507 | 73,344 | -41,940 | -23,869 | -19,702 | 1.79 | 3.81 | 43 | 1,968 | 12,534 | -18,386 | 21,721 | PASS | 0.969 | 504 | 8.0e-19 / 4.0e-12 / 1.3e-09 |

Rounding / slippage variants (adjusted Sharpe):

| variant | fee $0.50 | fee $1.00 | fee $2.00 | fee $4.36 |
|---|---|---|---|---|
| round half away (headline) | 1.115 | 0.865 | 0.366 | -0.808 |
| round half even | 1.115 | 0.865 | - | -0.808 |
| truncate toward 0 | 1.131 | 0.880 | - | -0.803 |
| hysteresis 0.25 | 1.109 | 0.860 | 0.364 | -0.804 |
| hysteresis 0.50 | 1.101 | 0.853 | 0.360 | -0.800 |
| half away, 2 ticks/side | 0.616 | 0.366 | -0.132 | -1.303 |

Frozen pack weights over the OOS window (informational; ideal -> net): 1.721 -> 1.747 ($0.436) / -0.200 ($4.36)

### C11DIP
| fee/micro RT | adj Sharpe | raw Sharpe | net $ (adj) | maxDD | worst wk | CVaR5 | CVaR10 | Sortino | MAR | %neg wk | wk mean | wk SD | wk p5 | wk p95 | gates | null rank | boot lo | best-of-F 1208 / 761 / 594 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.436 | 1.444 | 1.780 | 355,532 | 74,329 | -33,221 | -26,804 | -17,296 | 2.69 | 4.78 | 59 | 2,504 | 12,501 | -17,497 | 25,396 | PASS | 0.987 | 775 | 1.3e-06 / 2.0e-04 / 1.3e-03 |
| 1.0 | 1.439 | 1.775 | 354,166 | 74,399 | -33,249 | -26,826 | -17,318 | 2.67 | 4.76 | 59 | 2,494 | 12,498 | -17,508 | 25,370 | PASS | 0.987 | 765 | 1.1e-06 / 1.8e-04 / 1.2e-03 |
| 4.36 | 1.408 | 1.745 | 346,029 | 74,814 | -33,412 | -26,956 | -17,450 | 2.60 | 4.63 | 60 | 2,437 | 12,479 | -17,575 | 25,214 | PASS | 0.987 | 710 | 2.2e-07 / 6.5e-05 / 5.4e-04 |
| ideal cell-sum | 1.446 | 1.781 | 356,807 | 74,708 | -33,663 | -26,969 | -17,308 | 2.68 | 4.78 | 59 | 2,513 | 12,534 | -17,334 | 25,790 | PASS | 0.988 | 770 | 1.5e-06 / 2.1e-04 / 1.3e-03 |

Rounding / slippage variants (adjusted Sharpe):

| variant | fee $0.50 | fee $1.00 | fee $2.00 | fee $4.36 |
|---|---|---|---|---|
| round half away (headline) | 1.444 | 1.439 | 1.430 | 1.408 |
| round half even | 1.444 | 1.439 | - | 1.408 |
| truncate toward 0 | 1.416 | 1.411 | - | 1.380 |
| hysteresis 0.25 | 1.440 | 1.436 | 1.427 | 1.405 |
| hysteresis 0.50 | 1.452 | 1.448 | 1.439 | 1.417 |
| half away, 2 ticks/side | 1.430 | 1.425 | 1.416 | 1.394 |

Frozen pack weights over the OOS window (informational; ideal -> net): 1.677 -> 1.692 ($0.436) / 1.656 ($4.36)

### CL240 40 cells
| fee/micro RT | adj Sharpe | raw Sharpe | net $ (adj) | maxDD | worst wk | CVaR5 | CVaR10 | Sortino | MAR | %neg wk | wk mean | wk SD | wk p5 | wk p95 | gates | null rank | boot lo | best-of-F 1208 / 761 / 594 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.436 | 1.644 | 1.656 | 405,167 | 43,591 | -34,129 | -19,267 | -14,829 | 3.70 | 9.29 | 46 | 2,853 | 12,517 | -12,998 | 20,080 | PASS | 0.995 | 1144 | 1.4e-03 / 1.6e-02 / 4.0e-02 |
| 1.0 | 1.618 | 1.630 | 398,704 | 44,584 | -34,298 | -19,378 | -14,923 | 3.61 | 8.94 | 46 | 2,808 | 12,511 | -13,109 | 20,001 | PASS | 0.995 | 1096 | 7.6e-04 / 1.1e-02 / 2.9e-02 |
| 4.36 | 1.465 | 1.477 | 360,198 | 50,503 | -35,306 | -20,042 | -15,489 | 3.14 | 7.13 | 47 | 2,537 | 12,482 | -13,765 | 19,532 | PASS | 0.992 | 804 | 3.0e-06 / 3.4e-04 / 1.9e-03 |
| ideal cell-sum | 1.643 | 1.655 | 405,571 | 43,659 | -34,135 | -19,364 | -14,893 | 3.69 | 9.29 | 46 | 2,856 | 12,534 | -13,025 | 20,099 | PASS | 0.995 | 1140 | 1.4e-03 / 1.6e-02 / 3.9e-02 |

Rounding / slippage variants (adjusted Sharpe):

| variant | fee $0.50 | fee $1.00 | fee $2.00 | fee $4.36 |
|---|---|---|---|---|
| round half away (headline) | 1.641 | 1.618 | 1.573 | 1.465 |
| round half even | 1.641 | 1.618 | - | 1.465 |
| truncate toward 0 | 1.644 | 1.621 | - | 1.469 |
| hysteresis 0.25 | 1.639 | 1.616 | 1.571 | 1.463 |
| hysteresis 0.50 | 1.641 | 1.618 | 1.573 | 1.465 |
| half away, 2 ticks/side | 1.550 | 1.527 | 1.482 | 1.374 |

Frozen pack weights over the OOS window (informational; ideal -> net): 2.049 -> 2.047 ($0.436) / 1.861 ($4.36)

### BM13 6-cell (BANDS basis)
| fee/micro RT | adj Sharpe | raw Sharpe | net $ (adj) | maxDD | worst wk | CVaR5 | CVaR10 | Sortino | MAR | %neg wk | wk mean | wk SD | wk p5 | wk p95 | gates | null rank | boot lo | best-of-F 1208 / 761 / 594 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.436 | 1.770 | 1.770 | 437,796 | 55,980 | -40,286 | -21,203 | -16,192 | 3.56 | 7.82 | 40 | 3,083 | 12,562 | -13,606 | 26,129 | PASS | 0.999 | 1474 | 1.9e-02 / 8.3e-02 / 1.4e-01 |
| 1.0 | 1.724 | 1.724 | 426,006 | 56,441 | -40,376 | -21,302 | -16,288 | 3.44 | 7.55 | 42 | 3,000 | 12,549 | -13,719 | 25,945 | PASS | 0.998 | 1390 | 7.7e-03 / 4.7e-02 / 9.1e-02 |
| 4.36 | 1.449 | 1.449 | 355,772 | 59,593 | -40,914 | -21,891 | -16,859 | 2.77 | 5.97 | 42 | 2,505 | 12,470 | -14,393 | 24,852 | PASS | 0.993 | 916 | 1.6e-06 / 2.2e-04 / 1.4e-03 |
| ideal cell-sum | 1.769 | 1.769 | 436,610 | 56,101 | -40,084 | -21,139 | -16,166 | 3.55 | 7.78 | 41 | 3,075 | 12,534 | -13,641 | 26,119 | PASS | 0.999 | 1474 | 1.9e-02 / 8.2e-02 / 1.4e-01 |

Rounding / slippage variants (adjusted Sharpe):

| variant | fee $0.50 | fee $1.00 | fee $2.00 | fee $4.36 |
|---|---|---|---|---|
| round half away (headline) | 1.765 | 1.724 | 1.643 | 1.449 |
| round half even | 1.765 | 1.724 | - | 1.449 |
| truncate toward 0 | 1.763 | 1.723 | - | 1.447 |
| hysteresis 0.25 | 1.765 | 1.724 | 1.643 | 1.449 |
| hysteresis 0.50 | 1.765 | 1.724 | 1.643 | 1.449 |
| half away, 2 ticks/side | 1.683 | 1.643 | 1.561 | 1.366 |

Frozen pack weights over the OOS window (informational; ideal -> net): 1.953 -> 1.951 ($0.436) / 1.593 ($4.36)

### BM13 3-cell (as the pack runs)
| fee/micro RT | adj Sharpe | raw Sharpe | net $ (adj) | maxDD | worst wk | CVaR5 | CVaR10 | Sortino | MAR | %neg wk | wk mean | wk SD | wk p5 | wk p95 | gates | null rank | boot lo | best-of-F 1208 / 761 / 594 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.436 | 1.911 | 1.911 | 471,668 | 58,239 | -38,315 | -19,131 | -15,134 | 4.12 | 8.10 | 41 | 3,322 | 12,536 | -13,006 | 30,195 | PASS | 0.999 | 1664 | 1.3e-01 / 2.7e-01 / 3.6e-01 |
| 1.0 | 1.863 | 1.863 | 459,154 | 58,714 | -38,401 | -19,242 | -15,238 | 3.98 | 7.82 | 42 | 3,233 | 12,519 | -13,172 | 29,974 | PASS | 0.999 | 1577 | 6.8e-02 / 1.8e-01 / 2.7e-01 |
| 4.36 | 1.572 | 1.572 | 384,602 | 62,288 | -38,911 | -19,903 | -15,860 | 3.20 | 6.17 | 42 | 2,708 | 12,422 | -14,165 | 28,657 | PASS | 0.999 | 1076 | 2.0e-04 / 4.7e-03 / 1.5e-02 |
| ideal cell-sum | 1.913 | 1.913 | 472,238 | 58,257 | -38,248 | -19,152 | -15,117 | 4.13 | 8.11 | 41 | 3,326 | 12,534 | -12,990 | 30,241 | PASS | 0.999 | 1666 | 1.3e-01 / 2.8e-01 / 3.7e-01 |

Rounding / slippage variants (adjusted Sharpe):

| variant | fee $0.50 | fee $1.00 | fee $2.00 | fee $4.36 |
|---|---|---|---|---|
| round half away (headline) | 1.905 | 1.863 | 1.777 | 1.572 |
| round half even | 1.905 | 1.863 | - | 1.572 |
| truncate toward 0 | 1.909 | 1.867 | - | 1.577 |
| hysteresis 0.25 | 1.905 | 1.863 | 1.777 | 1.572 |
| hysteresis 0.50 | 1.905 | 1.863 | 1.777 | 1.572 |
| half away, 2 ticks/side | 1.820 | 1.777 | 1.690 | 1.485 |

Frozen pack weights over the OOS window (informational; ideal -> net): 1.953 -> 1.951 ($0.436) / 1.593 ($4.36)

## 5. Other WT432 variants (adjusted Sharpe; fee columns as in section 1)
- Targets on touch (no trade-through): $0.436 1.143, $1.00 0.934, $4.36 -0.303 (live form with trade-through is the headline).
- No account locks: $0.436 0.709, $4.36 -0.694; gates fail at every fee.
- Six further PAPER-ALL WT432 grids (ATR30_m3, ATR14_m4, ATR10_m2, ATR20_m2, ATR20_m3, ATR14_m3) were never rescored by the audit: their live-form ideal Sharpes are 0.73 / 0.61 / 0.43 / 0.32 / 0.40 / 1.10 (scored rebuild 0.75 / 0.72 / 0.68 / 0.68 / 0.61 / 0.86 versus PAPER-ALL 0.77 / 0.71 / 0.67 / 0.66 / 0.59 / 0.53) and all are negative at $4.36 per micro. WT432:ATR14_m3 does NOT reproduce the PAPER-ALL row (PAPER-ALL has 35 cells, this rebuild 36; scored 0.86 vs 0.53): report-only, do not freeze its numbers.

## 6. Pack-doc fixes made
- WT-10: the CODEPACK table "OOS 2.03" is the 2023-08+ selection-window Sharpe; M2 OOS is 1.867 (live-form 2.087). WT10/BANDS.json weekly_sd 8,353 corrected to 12,534 with mean 3,244 and p5/p95 -17,782 / 24,750 (scored; live-form values recorded alongside); old values kept under bands_before_2026-10-19_fix. WT10 is a single cell, no netting.
- BM13: BANDS.json was the 6-cell walk-forward series while the pack runs cells 003-005; warning added, BANDS_NET.json carries both (main = 6-cell, _3cell). CODEPACK table row annotated.
- Files written: outputs/codepack/{WT432,C11DIP,CL240,BM13}/BANDS_NET.json and NET_SERIES*.csv (columns: label day, ideal cell-sum adj/raw, net adj at fee 0.436/0.5/1/2/4.36, net raw at 0.436/1/4.36). codepack/CODEPACK.md flag block updated; DECISIONS.md appended.

## 7. PAPER-ALL rows to re-freeze (names only; PAPER-ALL files not edited)
Series format: outputs/codepack/<pack>/NET_SERIES<suffix>.csv, column `date` (YYYYMMDD label day) + `net_adj_fee<f>` (registry basis; use fee 4.36 for the standing rule, 0.436 for the scored-equivalent) or `net_raw_fee<f>`; bands in BANDS_NET.json rows[<suffix>].bands_by_fee_per_micro_rt[<fee>].adj_registry_basis.
- WT432 pack row -> NET_SERIES.csv (main); WT432:ATR30_m4 -> NET_SERIES_ATR30_m4.csv; WT432:ATR20_m4 -> _ATR20_m4; WT432:ATR10_m3 -> _ATR10_m3.
- Top-10 WT432 rows: WT432:ATR30_m3, WT432:ATR14_m4, WT432:ATR10_m2, WT432:ATR20_m2, WT432:ATR20_m3 -> NET_SERIES_<grid>.csv (WT432:ATR14_m3 not reproducible: leave on its old numbers, flagged).
- C11DIP -> codepack/C11DIP/NET_SERIES.csv.
- C10S1_CL:240_lr -> codepack/CL240/NET_SERIES_lr.csv; C10S1_CL:240_macd -> NET_SERIES_macd.csv; pack/forward row C10S1_CL240 (and C10S1_CL_240_lr / _macd audit names) -> NET_SERIES.csv (40 cells).
- BM13_NQ -> codepack/BM13/NET_SERIES.csv (6-cell); optional new row for the 3 cells the pack runs -> NET_SERIES_3cell.csv.
- Not rescored (same engines, need the same treatment if kept): BM11_NQ, BM12_NQ, ESDIP lead, C11R_IDX, T3S1_BOOKS_B:B_WT, other C10S1_CL:* family rows.
- Report-only: B7X and BTCWT (disabled on NT8).

## 8. Caveats
- Bar-level approximation of the rounding-error P&L and net costs; NT8 fills and the real micro fee schedule (Rithmic) are not on disk. The real MNQ/MES/MCL round-trip commission is the one number that decides WT432: please confirm it.
- Null worlds add the actual net delta with the weekly sign rather than re-simulating rounding in each world; the rank has MC se about 0.007.
- Netted-account lock behaviour for WT432 is unspecified; per-cell virtual locks are an NT8 engine requirement (81-108 virtual cells inside one strategy).
- Hysteresis (rebalance only when |N - T| > 0.5 + h) is a cheap implementation option: it recovers 0.05-0.12 Sharpe on WT432 at $0.50-$4.36 but does not rescue it at $4.36.
