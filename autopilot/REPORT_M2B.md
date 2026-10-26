# REPORT M2B - pair-modifier families as METHOD-2 DELTA families (owner ap_m2b)
Registered 69 families with a matrix (14 new PY/PZ + 55 earlier G/H/J/K) and 16 rows `no matrix`. Registry rows in outputs/methods2/FAMILY_REGISTRY.csv (owner ap_m2b), matrices outputs/methods2/fam/<id>.npz, per-family OOS table outputs/methods2/M2B_OOS.csv. Code: code/census/night_ins/ap_m2b_build.py (matrices + registry) and ap_m2b_oos.py (OOS read). No re-simulation, no UNTOUCHED, no live change, no key use.

## How the delta matrices were built
- The stored clean-process pickles (`*_all.pkl`: containers R / xall / allx / X) already hold every cell's MODIFIED-pair daily USD P&L (live size, B.Cfg(wk_floor=8,wk_loss_pb=None), 1 tick/side + commission). X = modified - live pair (pair series = `base` in the same pickle, identical across files: 1.46 / 2.83 / 2.30 / all-in 1.86).
- Every cell was verified before writing: the per-span weekly Sharpe recomputed from the stored series matches the stored `st1` (or summary `cells` uplift + base) with max abs error <= 3e-15 for all 69 families, base Sharpe error 0 (asserted in the build; the build aborts otherwise). Whole pre-registered grids, not only the carried cell.
- Layout per FAMILY_FORMAT: days (950 label days 2023-02-10..2026-10-13; the stored pair axis ends 3 label days before 2026-10-16; K96/K96b carry 951 days incl. 2023-02-09 where the pair has no row), X float32 (D, C) delta USD, names, first/last (full span for every cell; days where the overlay does not act are 0.0 = a true zero delta, not missing), meta size_basis='pair_delta_live_size', order_form `pair_overlay`, pair_dependent=1.
- Status: PY1..PZ4 `ready` as instructed (PY7, PY8, PY10, PZ2 have 4 cells and PZ3 has 6, below the 10-cell guideline; flagged in notes). Earlier families follow the format rule (`tiny: <10 cells` below 10 cells, which most of them are; the harness may merge them by mechanism, e.g. J5W_A..D, K19..K27 as a "risk-rule" super-family).
- NOT available as matrices (16 rows, status `no matrix`, reason in notes): G0A, G0B, G0C, G8_A, G8_B, G8_C, G8_D, G11_A, G11_B, G11_C, H8_A, H8_B, H8_C, H11_A, H11_C, K15. G0a-c pickles hold only per-cell Sharpe tables; G8/G11/H8/H11-A,C hold only the stage-1 clean table and the selected cell's stage-2 series; K15 has no output at all. Rebuild needs re-running the engine grid (not cheap).
- H0D: its baseline is the pickle's own control series (verified = live pair).
- Caveats: K96/K96b are stop-entry orders replayed on 1-second bars at the order level (registered as pair_overlay; no basis-audit rule). The delta of a size-tilt cell is a function of the live pair, so family correlations between PY/PZ/H7/J9P members are high; count one bet per mechanism.

## OOS read (ap_m2.py, rolling walk-forward 9/3/3 months, `ew` rule, equal-risk ensemble of the family's delta cells, 155 OOS weeks from 2023-11)
Dollars = the equal-risk ensemble (cells scaled to fit-window SD, averaged) rescaled by the weighted mean fit SD of the active cells, i.e. a typical-cell-sized delta at live size; Sharpe/null/bootstrap are the harness's (unit-SD) numbers. Null = 200 demeaned common-offset shifts of the family (harness default). Best-of-F rank = rank against the max of F pooled-null families (F=14 for PY/PZ, F=69 for all registered here; independent-draw approximation). Gates: a OOS Sharpe and net > 0; b null rank >= 0.95; c 4-week block bootstrap 90% lower bound of the weekly mean > 0; d both halves net > 0 (split 2025-05-01).

### New families PY1..PZ4 (F=14)
| family | cells | OOS mean wk delta ($) | OOS net ($) | OOS Sharpe(delta) | H1 / H2 Sharpe | boot90 lo | null rank | null p95 | best-of-F rank | corr w/ pair | OOS maxDD ($) | worst wk ($) | gates a/b/c/d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PY4_HMTILT | 12 | 603 | 93,505 | +0.45 | +0.12 / +0.95 | -0.13 | 0.815 | +0.87 | 0.042 | -0.19 | 194,937 | -63,384 | Y/n/n/Y |
| PY8_MINSKIP | 4 | 562 | 87,137 | +0.42 | +0.20 / +0.84 | -0.19 | 0.810 | +1.00 | 0.032 | -0.07 | 116,768 | -48,962 | Y/n/n/Y |
| PY9_PMWHIP | 8 | -12 | -1,820 | +0.37 | +0.66 / -0.30 | -0.27 | 0.645 | +0.97 | 0.019 | -0.10 | 121,116 | -43,751 | Y/n/n/n |
| PY7_TWOFEAT | 4 | 914 | 141,714 | +0.32 | +0.25 / +0.40 | -0.25 | 0.755 | +0.86 | 0.012 | -0.09 | 361,445 | -109,259 | Y/n/n/Y |
| PZ2_PARTEXIT | 4 | 1,181 | 183,026 | +0.10 | -1.44 / +2.21 | -0.28 | 0.610 | +0.85 | 0.001 | -0.09 | 269,804 | -59,234 | Y/n/n/n |
| PY5_STTILT | 12 | -97 | -15,085 | +0.08 | -0.41 / +0.80 | -0.26 | 0.560 | +1.02 | 0.000 | -0.16 | 320,759 | -103,610 | Y/n/n/n |
| PY10_GAPFLIP | 4 | -232 | -36,006 | -0.12 | -0.31 / +0.07 | -0.36 | 0.415 | +0.92 | 0.000 | +0.03 | 242,828 | -93,379 | n/n/n/n |
| PZ3_PARTSTATE | 6 | -49 | -7,619 | -0.32 | -1.65 / +1.03 | -0.37 | 0.335 | +1.00 | 0.000 | -0.12 | 253,752 | -42,533 | n/n/n/n |
| PY3_VIXSKEW | 12 | -884 | -136,984 | -0.42 | -0.69 / -0.15 | -0.36 | 0.255 | +0.75 | 0.000 | -0.23 | 388,971 | -86,061 | n/n/n/n |
| PY1_VIXCHG | 12 | -1,526 | -236,454 | -0.56 | -0.74 / -0.34 | -0.43 | 0.130 | +0.79 | 0.000 | -0.24 | 483,143 | -98,557 | n/n/n/n |
| PY2_VIXVXS | 12 | -1,953 | -302,673 | -0.60 | -0.87 / -0.31 | -0.47 | 0.155 | +0.98 | 0.000 | -0.27 | 544,442 | -96,249 | n/n/n/n |
| PZ4_XINDEX | 12 | -1,696 | -262,856 | -0.64 | -1.16 / -0.16 | -0.39 | 0.140 | +0.84 | 0.000 | -0.30 | 479,511 | -79,672 | n/n/n/n |
| PZ1_NQREGIME | 12 | -2,438 | -377,873 | -0.76 | -0.95 / -0.57 | -0.44 | 0.095 | +0.97 | 0.000 | -0.29 | 602,547 | -133,727 | n/n/n/n |
| PY6_HEALTH | 8 | -2,534 | -392,722 | -0.81 | -0.96 / -0.64 | -0.44 | 0.100 | +0.88 | 0.000 | -0.29 | 601,360 | -104,694 | n/n/n/n |

### Earlier pair-modifier families (best-of-F against all 69)
| family | cells | OOS mean wk delta ($) | OOS net ($) | OOS Sharpe(delta) | H1 / H2 Sharpe | boot90 lo | null rank | null p95 | best-of-F rank | corr w/ pair | OOS maxDD ($) | worst wk ($) | gates a/b/c/d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J5W_C | 4 | 1,049 | 162,521 | +1.16 | +1.26 / +1.04 | +0.16 | 0.990 | +0.87 | 0.253 | +0.01 | 66,589 | -49,839 | Y/Y/Y/Y |
| J5W_B | 6 | 1,322 | 204,943 | +1.05 | +1.12 / +0.98 | +0.07 | 0.975 | +0.87 | 0.111 | -0.10 | 96,364 | -63,148 | Y/Y/Y/Y |
| J5W_D | 2 | 1,666 | 258,190 | +0.91 | +0.97 / +0.96 | +0.07 | 0.935 | +0.94 | 0.021 | -0.14 | 94,928 | -67,908 | Y/n/Y/Y |
| K96B | 1 | 4,376 | 678,236 | +0.81 | +1.53 / -0.07 | -0.06 | 0.925 | +0.96 | 0.003 | -0.37 | 440,850 | -153,265 | Y/n/n/n |
| H11_B | 12 | 428 | 66,351 | +0.50 | +0.78 / +0.04 | -0.23 | 0.770 | +0.91 | 0.000 | -0.12 | 128,735 | -48,433 | Y/n/n/Y |
| K25 | 2 | -527 | -81,746 | +0.43 | +0.71 / -0.44 | -0.30 | 0.635 | +0.75 | 0.000 | -0.11 | 203,049 | -68,548 | Y/n/n/n |
| G10_3 | 9 | 142 | 22,072 | +0.16 | +0.10 / +0.21 | -0.22 | 0.630 | +0.95 | 0.000 | -0.12 | 138,997 | -41,444 | Y/n/n/Y |
| J5W_A | 4 | 201 | 31,129 | +0.15 | -0.08 / +0.35 | -0.42 | 0.560 | +0.91 | 0.000 | -0.19 | 121,720 | -70,274 | Y/n/n/n |
| K96 | 2 | 1,790 | 277,414 | +0.03 | -0.66 / +1.00 | -0.34 | 0.555 | +1.04 | 0.000 | -0.35 | 572,864 | -150,737 | Y/n/n/n |
| J7V | 9 | -223 | -34,593 | -0.08 | -0.08 / -0.07 | -0.27 | 0.475 | +0.87 | 0.000 | -0.29 | 224,803 | -60,678 | n/n/n/n |
| K22 | 2 | -1,183 | -183,331 | -0.16 | -0.29 / -0.08 | -0.41 | 0.410 | +1.01 | 0.000 | -0.06 | 365,505 | -110,919 | n/n/n/n |
| H10_B | 6 | -183 | -28,371 | -0.16 | -0.97 / +0.52 | -0.53 | 0.360 | +0.94 | 0.000 | -0.19 | 108,820 | -31,949 | n/n/n/n |
| K20 | 1 | -306 | -47,389 | -0.17 | -0.20 / -0.13 | -0.44 | 0.395 | +0.79 | 0.000 | -0.04 | 164,712 | -132,900 | n/n/n/n |
| J9P_A | 12 | -654 | -101,314 | -0.18 | +0.08 / -0.44 | -0.24 | 0.385 | +1.07 | 0.000 | -0.28 | 286,722 | -118,648 | n/n/n/n |
| G6C | 5 | -203 | -31,491 | -0.20 | -0.28 / -0.13 | -0.27 | 0.415 | +0.95 | 0.000 | -0.18 | 73,495 | -30,759 | n/n/n/n |
| H7_A | 12 | -917 | -142,183 | -0.20 | -0.25 / -0.13 | -0.24 | 0.345 | +0.87 | 0.000 | -0.34 | 369,755 | -82,000 | n/n/n/n |
| J0C | 9 | -575 | -89,186 | -0.27 | -0.21 / -0.35 | -0.28 | 0.295 | +0.97 | 0.000 | -0.25 | 265,865 | -48,996 | n/n/n/n |
| K11 | 4 | -1,839 | -285,006 | -0.29 | -0.73 / +0.23 | -0.42 | 0.335 | +1.11 | 0.000 | -0.36 | 755,080 | -110,498 | n/n/n/n |
| K21 | 3 | -1,020 | -158,129 | -0.29 | +0.16 / -0.79 | -0.46 | 0.300 | +0.94 | 0.000 | -0.20 | 363,348 | -96,583 | n/n/n/n |
| J9P_B | 18 | -713 | -110,474 | -0.32 | -0.84 / +0.24 | -0.47 | 0.260 | +1.02 | 0.000 | -0.17 | 325,536 | -146,054 | n/n/n/n |
| K24 | 1 | -983 | -152,383 | -0.38 | -0.29 / -0.47 | -0.46 | 0.275 | +1.09 | 0.000 | -0.17 | 425,539 | -101,780 | n/n/n/n |
| H7_C | 18 | -731 | -113,245 | -0.42 | -1.09 / +0.36 | -0.28 | 0.230 | +0.86 | 0.000 | -0.26 | 277,176 | -61,865 | n/n/n/n |
| H0B | 18 | -892 | -138,310 | -0.42 | -0.82 / +0.43 | -0.46 | 0.215 | +0.93 | 0.000 | -0.08 | 255,368 | -91,829 | n/n/n/n |
| K100 | 1 | -1,363 | -211,333 | -0.45 | -0.77 / -0.11 | -0.48 | 0.225 | +0.96 | 0.000 | -0.17 | 371,479 | -100,344 | n/n/n/n |
| K17 | 3 | -664 | -102,893 | -0.51 | -0.22 / -0.95 | -0.64 | 0.155 | +0.91 | 0.000 | -0.06 | 170,190 | -56,211 | n/n/n/n |
| H7_B | 12 | -976 | -151,328 | -0.51 | -0.24 / -0.88 | -0.29 | 0.175 | +0.96 | 0.000 | -0.28 | 242,878 | -85,692 | n/n/n/n |
| H10_A | 8 | -180 | -27,859 | -0.52 | -0.86 / +0.15 | -0.78 | 0.170 | +0.97 | 0.000 | -0.08 | 62,466 | -31,930 | n/n/n/n |
| J0A | 9 | -2,087 | -323,505 | -0.55 | -0.22 / -1.23 | -0.31 | 0.175 | +0.94 | 0.000 | -0.45 | 612,365 | -74,696 | n/n/n/n |
| G10_2 | 8 | -445 | -68,937 | -0.56 | -0.25 / -1.21 | -0.44 | 0.180 | +0.90 | 0.000 | -0.04 | 92,919 | -40,360 | n/n/n/n |
| J6A | 8 | -2,139 | -331,472 | -0.64 | -0.96 / -0.24 | -0.41 | 0.120 | +0.99 | 0.000 | -0.40 | 525,553 | -61,229 | n/n/n/n |
| H10_C | 6 | -877 | -135,923 | -0.67 | +0.37 / -1.99 | -0.44 | 0.095 | +0.89 | 0.000 | -0.21 | 208,668 | -31,653 | n/n/n/n |
| H6B | 8 | -2,010 | -311,572 | -0.68 | -1.02 / -0.38 | -0.40 | 0.120 | +0.90 | 0.000 | -0.29 | 561,902 | -66,702 | n/n/n/n |
| G6A | 15 | -2,247 | -348,344 | -0.70 | -0.83 / -0.53 | -0.42 | 0.095 | +0.91 | 0.000 | -0.19 | 593,136 | -127,855 | n/n/n/n |
| K13 | 8 | -2,539 | -393,510 | -0.71 | -0.70 / -0.71 | -0.34 | 0.110 | +0.96 | 0.000 | -0.38 | 601,492 | -71,805 | n/n/n/n |
| H6A | 10 | -2,110 | -327,054 | -0.71 | -0.90 / -0.52 | -0.43 | 0.090 | +0.84 | 0.000 | -0.24 | 586,961 | -73,470 | n/n/n/n |
| K23 | 3 | -2,961 | -458,933 | -0.72 | -1.48 / -0.03 | -0.50 | 0.135 | +0.87 | 0.000 | -0.49 | 930,539 | -100,185 | n/n/n/n |
| K19 | 4 | -2,313 | -358,591 | -0.74 | -0.69 / -0.78 | -0.48 | 0.100 | +0.91 | 0.000 | -0.30 | 401,321 | -86,316 | n/n/n/n |
| J9P_C | 9 | -3,120 | -483,643 | -0.77 | -0.37 / -1.24 | -0.44 | 0.070 | +0.86 | 0.000 | -0.30 | 612,252 | -131,420 | n/n/n/n |
| G10_1 | 6 | -886 | -137,380 | -0.78 | -1.39 / -0.09 | -0.77 | 0.050 | +0.94 | 0.000 | -0.14 | 147,019 | -37,365 | n/n/n/n |
| H0A | 15 | -2,877 | -445,859 | -0.85 | -1.24 / -0.49 | -0.38 | 0.045 | +0.90 | 0.000 | -0.48 | 667,021 | -88,537 | n/n/n/n |
| J6B | 6 | -2,653 | -411,189 | -0.87 | -1.77 / +0.30 | -0.54 | 0.080 | +0.91 | 0.000 | -0.33 | 621,473 | -94,639 | n/n/n/n |
| G6B | 10 | -2,448 | -379,486 | -0.93 | -1.17 / -0.70 | -0.52 | 0.020 | +0.90 | 0.000 | -0.24 | 612,456 | -93,393 | n/n/n/n |
| H0C | 9 | -2,660 | -412,258 | -1.06 | -1.10 / -1.02 | -0.67 | 0.025 | +0.92 | 0.000 | -0.36 | 491,243 | -119,302 | n/n/n/n |
| K27 | 1 | -771 | -119,548 | -1.17 | -1.41 / -0.86 | -0.54 | 0.030 | +0.82 | 0.000 | -0.17 | 144,329 | -23,635 | n/n/n/n |
| J0B | 6 | -3,261 | -505,513 | -1.21 | -0.67 / -2.03 | -0.44 | 0.015 | +0.89 | 0.000 | -0.25 | 577,204 | -62,096 | n/n/n/n |
| K26 | 2 | -7,210 | -1,117,593 | -1.33 | -1.58 / -1.03 | -0.68 | 0.005 | +0.89 | 0.000 | -0.58 | 1,435,288 | -112,026 | n/n/n/n |
| K16 | 6 | -7,168 | -1,111,036 | -1.45 | -1.57 / -1.30 | -0.61 | 0.010 | +1.01 | 0.000 | -0.38 | 1,305,604 | -104,736 | n/n/n/n |
| H6C | 6 | -2,643 | -409,666 | -1.50 | -1.41 / -1.58 | -0.57 | 0.005 | +0.92 | 0.000 | -0.47 | 446,207 | -59,688 | n/n/n/n |
| K14 | 6 | -9,496 | -1,471,837 | -1.52 | -0.84 / -2.29 | -0.63 | 0.020 | +0.90 | 0.000 | -0.60 | 1,720,449 | -147,144 | n/n/n/n |
| J6C | 6 | -8,018 | -1,242,848 | -1.69 | -1.59 / -1.85 | -0.61 | 0.005 | +0.85 | 0.000 | -0.49 | 1,403,276 | -106,606 | n/n/n/n |
| H0D | 12 | -10,785 | -1,671,642 | -1.80 | -2.03 / -1.53 | -0.67 | 0.000 | +0.93 | 0.000 | -0.81 | 1,801,122 | -152,741 | n/n/n/n |
| K12 | 8 | -10,134 | -1,570,814 | -2.44 | -2.60 / -2.25 | -0.85 | 0.000 | +1.05 | 0.000 | -0.28 | 1,665,310 | -153,257 | n/n/n/n |
| K18 | 8 | -12,228 | -1,895,299 | -2.81 | -2.99 / -2.58 | -1.03 | 0.000 | +1.02 | 0.000 | -0.27 | 1,966,707 | -160,898 | n/n/n/n |
| K18B | 8 | -13,481 | -2,089,498 | -3.32 | -4.07 / -2.53 | -1.07 | 0.000 | +0.94 | 0.000 | -0.38 | 2,208,616 | -119,193 | n/n/n/n |
| K99 | 4 | -26,144 | -4,052,323 | -6.23 | -6.68 / -5.76 | -2.14 | 0.000 | +0.99 | 0.000 | -0.47 | 4,115,738 | -150,795 | n/n/n/n |

## Reading
- Of the 14 new families only the HM-tilt PY4 (+0.45), minute-skip PY8 (+0.42), afternoon whipsaw halt PY9 (+0.37) and two-feature PY7 (+0.32) have a positive OOS delta Sharpe; none passes gate b (null ranks 0.81, 0.81, 0.65, 0.76) or c, none has a best-of-14 rank above 0.05. PY1-PY3, PY6, PZ1, PZ4, PY10 and PZ3 are negative OOS: the VIX, health, NQ-regime and cross-index tilts do not improve the live pair out of sample. PY8's null_p95 (0.996 Sharpe units) shows how wide the family null is for sparse delta series.
- Only J5W_B, J5W_C (book-scoped/expiring/smooth whipsaw halts, 6 and 4 cells) pass gates a-d on their own (OOS delta Sharpe +1.05 / +1.16, null rank 0.975 / 0.990, boot lo >0, both halves positive; J5W_D has rank 0.935). Multiplicity: best-of-69 rank 0.11 / 0.25 (they are close variants of one whipsaw-halt mechanism, F is really lower, ~ 3-4 mechanism groups) so not a PASS under item 4 without an independent replication; the mechanism family (H11_B, PY9, J5W_A-D) is the one to carry into the factor section. Mean OOS delta is only about +$1.0-1.7k per week for a typical cell versus a pair OOS drawdown scale of $210k; corr with the pair near zero.
- K96B (+0.81, rank 0.925, one cell) is a one-cell stop-entry variant, not usable for a verdict.
- Everything else (most exits, brackets, bracket-scaling K12/K14/K16/K18/K99, session/time rules, event rules) has a clearly negative OOS delta; these are real negative-delta families, which is what a pair-modifier null should look like.
