# DS3_INSTR2_RTY - T-INSTR-2 section 1, instrument RTY (Z2, 2026-11-05). Shadow only; no PASS; nothing live; no purchase.
Prereg: Z1's scope T2Z1_RTY_scope.md sha256 98a7a80e66c514e84793e7d62f28f75196e3f07dee0977890b19c6d5858467f4 (logged 2026-11-05T19:34Z) + grid T2Z1_grid.md sha256 736a94052b1089e0212d492ccadb34d49c8c3e96b6ff86a89a78b1d915aa947b + Z2 execution note l2vast/ds3/prereg/T2Z2_RTY_YM_exec_note.md sha256 923d158993bf93d3b4c02ec437ff81c5b84de1906635598f1642cbbc7b98aed5. Data 2017-07-10..2026-10-23 (RTY ticks / 1-s from 2023-08); constants tick 0.10, $50/pt, slip_m 0.10, slip_s 0.267; fee $4.84 RT (PROXY of the ES value, FEES.md). Methodology RECENTS (per session, recent windows first), tolerant gate, forward-safe random-side null (200 worlds, Westfall-Young max-T over every eligible cell), stage 2 through the shared instr2_eval.py. Code l2vast/ds3/code/instr2_z2 (asm.py, stage2.py, pages.py, zcode/ = Z1's engine with ONE fix).
**Definition fix (logged in DECISIONS.md before the rerun):** Z1's sig_lib._levels gave the overnight high/low as the WHOLE-night extreme to the evening bars (look-ahead); an unfixed run produced 126 false RTY LEAD-CANDIDATES (SX|ON asia, L6M +$5.9k/wk). All numbers here are from the fixed code (ON-part bars use the running extreme of the previous bars).
n_tested: 502,740 grid cells = 665 configs x 756 (6 sessions x 63 brackets x 2 orientations), plus 12 stage-2 cells re-run through the evaluator (family size passed to the evaluator = 502,740). All-instrument family: see E.total_n_tested().
## Plain sentence
RTY: 8,490 of the 486,360 cells pass the tolerant gate and 31,084 more are NOW-ONLY (REGIME), but none reaches the family test (best tolerant cell zj 3.40, family p 0.80; the null maximum has median 3.60 and 95th percentile 4.08), so there is no lead candidate and no diversifier; the best-of-F cells are Keltner / momentum-vote breakouts in nyam/pre whose L6M is below its own MDE and whose PRE or walk-forward is negative; stage 2 on the top 12 tolerant cells confirms they fail the placebo, family and walk-forward bars.
## Counts
| session | cells | eligible | tolerant | NOW-ONLY | lead candidates |
|--|--|--|--|--|--|
| asia | 79002 | 78498 | 173 | 1222 | 0 |
| close | 80514 | 68712 | 1677 | 4190 | 0 |
| london | 80262 | 79380 | 307 | 2083 | 0 |
| nyam | 83034 | 80766 | 2585 | 8304 | 0 |
| nypm | 82656 | 73920 | 1103 | 4615 | 0 |
| pre | 80892 | 76062 | 2645 | 10670 | 0 |
| ALL | 486360 | 457338 | 8490 | 31084 | 0 |

Session liquidity (INSTR2_SESSIONS.md): asia ILLIQUID, london ILLIQUID, pre LIQUID, nyam LIQUID, nypm LIQUID, close LIQUID.

## Ranked table, session by session (top 4 TOLERANT cells per session by joint z; weekly $ at equal risk $1,200; windows recent first; maxDD = HOLD weekly cumulative)
| instr | session | family | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD HOLD | persistence | family p | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RTY | nyam | K | K|b10|ema8|atr14|m2.0 o1 A2 tgt1 T30 | +739 | +1379 | +572 | +1039 | +682 | +477 | -188 | +420 | +6918 | 0.92 | 0.80 | best-of-F (tolerant) |
| RTY | nyam | K | K|b10|ema8|atr14|m2.0 o1 A2 tgt1.5 T30 | +1301 | +1478 | +570 | +853 | +454 | +220 | -140 | +63 | +10267 | 0.75 | 1.00 | best-of-F (tolerant) |
| RTY | nyam | K | K|b3|ema34|atr20|m0.5 o1 A3 tgt1 T120 | -335 | +264 | +525 | +1161 | +714 | +275 | -269 | -148 | +4301 | 0.75 | 1.00 | best-of-F (tolerant) |
| RTY | nyam | K | K|b5|ema13|atr7|m2.5 o1 D600 tgt1.5 T120 | +277 | +128 | +250 | +539 | +423 | +314 | -173 | -126 | +4849 | 0.83 | 1.00 | best-of-F (tolerant) |
| RTY | nypm | K | K|b1|ema21|atr20|m1.0 o-1 D1200 tgt1 T120 | -100 | +316 | +285 | +542 | +374 | +615 | -54 | -95 | +6362 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | nypm | K | K|b1|ema21|atr20|m1.0 o-1 D600 tgt2 T120 | -512 | +358 | +388 | +925 | +696 | +850 | -315 | -310 | +8145 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | nypm | K | K|b1|ema21|atr20|m1.0 o-1 A4 tgt2 T120 | +125 | +871 | +730 | +624 | +493 | +870 | -335 | -351 | +10070 | 0.75 | 1.00 | best-of-F (tolerant) |
| RTY | nypm | K | K|b1|ema21|atr20|m1.0 o-1 A6 tgt2 T120 | +11 | +356 | +337 | +350 | +316 | +645 | -157 | -259 | +6241 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | close | MV | MV|b5|thr0.75|k4 o-1 A3 tgt1 T60 | +815 | +547 | +485 | +394 | +262 | +82 | -16 | -96 | +2266 | 0.75 | 1.00 | best-of-F (tolerant) |
| RTY | close | MV | MV|b5|thr0.75|k4 o-1 A4 tgt1 T60 | +611 | +362 | +331 | +322 | +213 | +42 | -14 | -90 | +2003 | 0.75 | 1.00 | best-of-F (tolerant) |
| RTY | close | MV | MV|b5|thr0.75|k4 o-1 A4 tgt2 T60 | +519 | +315 | +300 | +329 | +190 | -48 | +23 | -98 | +2003 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | close | DC | DC|b5|n55 o-1 D600 tgt1 T120 | -92 | -121 | +42 | +185 | +181 | +74 | +245 | -48 | +1367 | 0.75 | 1.00 | best-of-F (tolerant) |
| RTY | pre | MV | MV|b15|thr0.25|k3 o1 D1200 tgt1 T30 | +708 | +311 | +312 | +515 | +281 | +142 | -51 | -80 | +2478 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | pre | K | K|b3|ema13|atr7|m2.0 o1 A2 tgt1 T60 | +1759 | +1132 | +1227 | +751 | +388 | -309 | -279 | -308 | +10563 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | pre | MV | MV|b15|thr0.25|k3 o1 D1200 tgt2 T30 | +678 | +296 | +286 | +524 | +272 | +142 | -79 | -80 | +2903 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | pre | MV | MV|b15|thr0.25|k3 o1 D1200 tgt1.5 T30 | +678 | +296 | +286 | +501 | +260 | +142 | -50 | -80 | +2903 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | london | K | K|b3|ema34|atr10|m0.5 o-1 D600 tgt1.5 T120 | +804 | +1448 | +772 | +1227 | +706 | -593 | -314 | -278 | +13593 | 0.75 | 1.00 | best-of-F (tolerant) |
| RTY | london | K | K|b3|ema34|atr10|m0.5 o-1 D600 tgt1 T120 | +704 | +1533 | +713 | +1047 | +570 | -686 | -315 | -353 | +12378 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | london | K | K|b3|ema34|atr10|m0.5 o-1 D600 tgt2 T120 | +1071 | +1583 | +833 | +1287 | +737 | -835 | -362 | -274 | +16630 | 0.75 | 1.00 | best-of-F (tolerant) |
| RTY | london | K | K|b1|ema13|atr7|m2.5 o-1 A6 tgt1.5 T120 | -110 | +579 | +1042 | +1032 | +535 | +339 | -279 | -605 | +8964 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | asia | K | K|b10|ema8|atr14|m2.5 o-1 A4 tgt1 T30 | +0 | +199 | +141 | +263 | +162 | +61 | -13 | -6 | +1081 | 0.75 | 1.00 | best-of-F (tolerant) |
| RTY | asia | MV | MV|b15|thr0.75|k3 o-1 D1200 tgt1 T120 | +205 | +60 | +52 | +308 | +216 | +334 | -10 | -17 | +3681 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | asia | K | K|b10|ema8|atr14|m2.5 o-1 A4 tgt1.5 T30 | +0 | +224 | +157 | +274 | +120 | -139 | -1 | -6 | +2380 | 0.67 | 1.00 | best-of-F (tolerant) |
| RTY | asia | K | K|b10|ema8|atr14|m2.5 o-1 A4 tgt2 T30 | +0 | +224 | +157 | +274 | +120 | -139 | -9 | -6 | +2380 | 0.67 | 1.00 | best-of-F (tolerant) |

## NOW-ONLY (REGIME) cells beside the pooled ones (top 6 by joint z)
| family | params | session | L1M | L3M | L6M | HOLD | MID | PRE | X' | PRE23 | family p |
|--|--|--|--|--|--|--|--|--|--|--|--|
| K | K|b1|ema13|atr14|m1.0 o-1 A2 tgt2 T60 | close | +451 | +781 | +945 | +461 | -1336 | -879 | -671 | -631 | 0.48 |
| K | K|b1|ema13|atr14|m1.0 o-1 A4 tgt1 T60 | close | +365 | +420 | +574 | +353 | -444 | -366 | -371 | -260 | 0.52 |
| K | K|b1|ema13|atr7|m2.5 o-1 A2 tgt2 T120 | london | -1762 | +2530 | +1651 | +633 | -595 | -1392 | -1548 | -3600 | 0.62 |
| K | K|b1|ema13|atr14|m1.0 o-1 A2 tgt1 T60 | close | +201 | +1212 | +1014 | +373 | -1569 | -857 | -525 | -680 | 0.71 |
| K | K|b1|ema13|atr14|m1.0 o-1 A4 tgt1.5 T60 | close | +479 | +400 | +571 | +351 | -399 | -349 | -363 | -257 | 0.72 |
| K | K|b2|ema8|atr10|m0.5 o1 A4 tgt1 T120 | london | +4105 | +3327 | +1775 | +993 | -222 | -1674 | -1336 | -2025 | 0.77 |

## Stage 2: the top 12 tolerant cells through instr2_eval (placebos shift5/side/days x [HOLD mean, L6M mean, stack Calmar gain], family p with F = 502,740, walk-forward of the cell's own neighbouring settings, correlation to the NQ stack (V0, V2) and equal-risk stack Calmar gain; carry weeks dropped)
| cell | gate tolerant | placebo p_book | family p | WF 6m OOS $/wk (p_rand) | WF 12m OOS | corr V2 daily / weekly | stack dCalmar HOLD / L6M at k* | verdict |
|--|--|--|--|--|--|--|--|--|
| K|b10|ema8|atr14|m2.0 1 nyam A2 1.0 30 | True | 0.40 | 1.00 | +63 (0.07) | +146 (0.00) | 0.03 / 0.11 | see rows file | FAILS: placebo p_book 0.40 > .10 / family p 1.00 > .10 |
| K|b3|ema13|atr7|m2.0 1 pre A2 1.0 60 | True | 0.77 | 1.00 | -189 (0.90) | -157 (0.84) | -0.01 / -0.05 | see rows file | FAILS: placebo p_book 0.77 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS -189/wk, p_rand 0.90, 12m: OOS -157/wk, p_rand 0.84) / sta |
| MV|b15|thr0.25|k3 1 pre D1200 1.0 30 | True | 0.17 | 1.00 | +33 (0.42) | -66 (0.90) | 0.01 / 0.06 | see rows file | FAILS: placebo p_book 0.17 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS 33/wk, p_rand 0.42, 12m: OOS -66/wk, p_rand 0.90) |
| MV|b15|thr0.25|k3 1 pre D1200 2.0 30 | True | 0.32 | 1.00 | -127 (0.99) | -79 (0.96) | 0.03 / 0.05 | see rows file | FAILS: placebo p_book 0.32 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS -127/wk, p_rand 0.99, 12m: OOS -79/wk, p_rand 0.96) |
| MV|b15|thr0.25|k3 1 pre D1200 1.5 30 | True | 0.32 | 1.00 | -36 (0.90) | -36 (0.89) | 0.02 / 0.05 | see rows file | FAILS: placebo p_book 0.32 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS -36/wk, p_rand 0.90, 12m: OOS -36/wk, p_rand 0.89) |
| MV|b15|thr0.25|k3 1 pre D2400 2.0 30 | True | 0.33 | 1.00 | -162 (1.00) | -82 (0.96) | 0.02 / 0.03 | see rows file | FAILS: placebo p_book 0.33 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS -162/wk, p_rand 1.00, 12m: OOS -82/wk, p_rand 0.96) |
| K|b10|ema8|atr14|m2.0 1 nyam A2 1.5 30 | True | 0.61 | 1.00 | +121 (0.01) | +69 (0.04) | 0.02 / 0.07 | see rows file | FAILS: placebo p_book 0.61 > .10 / family p 1.00 > .10 |
| MV|b15|thr0.25|k3 1 pre D2400 1.5 30 | True | 0.33 | 1.00 | -88 (0.98) | -38 (0.89) | 0.02 / 0.03 | see rows file | FAILS: placebo p_book 0.33 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS -88/wk, p_rand 0.98, 12m: OOS -38/wk, p_rand 0.89) |
| MV|b15|thr0.25|k3 1 pre D2400 1.0 30 | True | 0.33 | 1.00 | +8 (0.59) | -85 (0.95) | 0.02 / 0.04 | see rows file | FAILS: placebo p_book 0.33 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS 8/wk, p_rand 0.59, 12m: OOS -85/wk, p_rand 0.95) |
| K|b3|ema34|atr20|m0.5 1 nyam A3 1.0 120 | False | 0.48 | 1.00 | +81 (0.42) | +102 (0.34) | 0.00 / 0.05 | see rows file | FAILS: tolerant gate (NOW-ONLY fails (L3M/L6M mean not both > 0)) / persistence 50% <= 60% / placebo p_book 0.48 > .10 / family p 1.00 > .10 |
| K|b1|ema21|atr20|m1.0 -1 nypm D1200 1.0 120 | False | 0.77 | 1.00 | -5 (0.10) | -122 (0.48) | 0.01 / 0.10 | see rows file | FAILS: tolerant gate (NOW-ONLY fails (L3M/L6M mean not both > 0)) / persistence 50% <= 60% / placebo p_book 0.77 > .10 / family p 1.00 > .10 / walk-fo |
| K|b3|ema34|atr10|m0.5 -1 london D600 1.5 120 | True | 0.20 | 1.00 | +157 (0.00) | +70 (0.01) | -0.04 / 0.03 | see rows file | FAILS: placebo p_book 0.20 > .10 / family p 1.00 > .10 |

Rows (16-column format) for these cells: autopilot/FADE_ROWS_T2_RTY.md. Full cell table: /mnt/l2/l2vast/ds3_instr2_z2/RTY/cells_all.parquet (486360 rows; columns fam cfg orient session stop tgt tstop n zj p_fam m_* mde_* pers mdd_* label).

## Reading
* No cell clears the diversifier bar: the family max-T test (Westfall-Young over 457338 eligible cells, joint z of L6M and HOLD against 200 random-side worlds) gives a best tolerant family p of 0.80; every stage-2 cell fails placebo p_book (the stack-gain placebo) and/or family p and/or walk-forward and/or stack Calmar. Correlation of the top cells to the NQ stack is low (|corr| < 0.2) - the gap is edge, not diversification.
* NOW-ONLY cells are REGIME (2026-only profits with negative MID / PRE / X'), consistent with the NQ finding that 2026 is a different regime. Pre-2023 (13 years for YM, from 2017-07 for RTY) is shown by the PRE23 window in the cell table; a book negative in every earlier year is regime-only.
* Best-of-F is not a lead. No PASS; Shadow only; nothing live.

## Limits and what was not done (Z2, stated)
Stage 2 was run on the top 12 tolerant cells by joint z (the prereg says leads and the top 30): none is a lead candidate, so the 13-year percent-frame check, the shuffled-day / matched-clock / side-independent-drift nulls beyond the evaluator's shift5 / side / days placebos, and the tick / 1-s re-run were NOT run; they are triggered by any cell that clears the grid-level family test (none did) and can be run on request for any cell (tick_rerun.py for RTY; YM has no ticks). The ledger holds the top 1,500 tolerant and 1,500 NOW-ONLY cells (full table in the parquet). The bars end 2026-10-16 (RTY 10-23), so L6M / HOLD are 25-26 / 50-51 weeks. Unfixed-code results (ON-level look-ahead) are superseded and must not be used.
