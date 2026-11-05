# DS3_INSTR2_YM - T-INSTR-2 section 1, instrument YM (Z2, 2026-11-05). Shadow only; no PASS; nothing live; no purchase.
Prereg: Z1's scope T2Z1_YM_scope.md sha256 abb661bd1e7ae9303459980f5c97e24c4786daf5f53b69c977bf11a4a975c3d4 (logged 2026-11-05T19:34Z) + grid T2Z1_grid.md sha256 736a94052b1089e0212d492ccadb34d49c8c3e96b6ff86a89a78b1d915aa947b + Z2 execution note l2vast/ds3/prereg/T2Z2_RTY_YM_exec_note.md sha256 923d158993bf93d3b4c02ec437ff81c5b84de1906635598f1642cbbc7b98aed5. Data 2013-01-02..2026-10-16 (no ticks / L2: finalists stay on 1-min); constants tick 1, $5/pt, slip_m 1.0, slip_s 3.06; fee $4.84 RT (PROXY of the ES value, FEES.md). Methodology RECENTS (per session, recent windows first), tolerant gate, forward-safe random-side null (200 worlds, Westfall-Young max-T over every eligible cell), stage 2 through the shared instr2_eval.py. Code l2vast/ds3/code/instr2_z2 (asm.py, stage2.py, pages.py, zcode/ = Z1's engine with ONE fix).
**Definition fix (logged in DECISIONS.md before the rerun):** Z1's sig_lib._levels gave the overnight high/low as the WHOLE-night extreme to the evening bars (look-ahead); an unfixed run produced 126 false RTY LEAD-CANDIDATES (SX|ON asia, L6M +$5.9k/wk). All numbers here are from the fixed code (ON-part bars use the running extreme of the previous bars).
n_tested: 502,740 grid cells = 665 configs x 756 (6 sessions x 63 brackets x 2 orientations), plus 12 stage-2 cells re-run through the evaluator (family size passed to the evaluator = 502,740). All-instrument family: see E.total_n_tested().
## Plain sentence
YM: 11,605 of the 487,872 cells pass the tolerant gate and 42,330 more are NOW-ONLY (REGIME), but none reaches the family test (best tolerant cell zj 3.36, family p 0.88; the null maximum has median 3.57 and 95th percentile 4.07), so there is no lead candidate and no diversifier; the best-of-F cells are Keltner / momentum-vote breakouts in nyam/pre whose L6M is below its own MDE and whose PRE or walk-forward is negative; stage 2 on the top 12 tolerant cells confirms they fail the placebo, family and walk-forward bars.
## Counts
| session | cells | eligible | tolerant | NOW-ONLY | lead candidates |
|--|--|--|--|--|--|
| asia | 79002 | 78120 | 365 | 2452 | 0 |
| close | 81900 | 70182 | 4220 | 5956 | 0 |
| london | 80262 | 79380 | 392 | 6306 | 0 |
| nyam | 83034 | 80808 | 2704 | 8151 | 0 |
| nypm | 82782 | 74130 | 1938 | 7192 | 0 |
| pre | 80892 | 75054 | 1986 | 12273 | 0 |
| ALL | 487872 | 457674 | 11605 | 42330 | 0 |

Session liquidity (INSTR2_SESSIONS.md): asia ILLIQUID, london THIN, pre LIQUID, nyam LIQUID, nypm LIQUID, close LIQUID.

## Ranked table, session by session (top 4 TOLERANT cells per session by joint z; weekly $ at equal risk $1,200; windows recent first; maxDD = HOLD weekly cumulative)
| instr | session | family | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD HOLD | persistence | family p | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| YM | nyam | K | K|b1|ema13|atr7|m1.0 o1 A3 tgt1.5 T120 | +3068 | +2268 | +1304 | +1296 | +1008 | +28 | -413 | -284 | +6574 | 0.92 | 0.88 | best-of-F (tolerant) |
| YM | nyam | K | K|b1|ema13|atr7|m1.0 o1 A2 tgt2 T120 | +4752 | +2964 | +1656 | +1582 | +1226 | +249 | -497 | -487 | +11820 | 0.83 | 0.92 | best-of-F (tolerant) |
| YM | nyam | K | K|b1|ema13|atr7|m1.0 o1 D600 tgt2 T120 | +4705 | +2948 | +1755 | +1885 | +1237 | +254 | -156 | -36 | +9821 | 0.92 | 0.93 | best-of-F (tolerant) |
| YM | nyam | K | K|b1|ema13|atr7|m1.0 o1 D600 tgt1 T120 | +4398 | +2547 | +1346 | +1274 | +887 | +673 | -263 | +57 | +11021 | 0.83 | 0.97 | best-of-F (tolerant) |
| YM | nypm | HV | HV|b1|hma20|f0 o-1 D1200 tgt2 T120 | -285 | +283 | +298 | +591 | +308 | +526 | +130 | +80 | +4603 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | nypm | HV | HV|b1|hma20|f0 o-1 D2400 tgt1 T120 | -142 | +142 | +149 | +272 | +156 | +326 | +69 | +21 | +2431 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | nypm | HV | HV|b1|hma20|f0 o-1 D2400 tgt2 T120 | -142 | +276 | +234 | +340 | +191 | +331 | +49 | +21 | +2431 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | nypm | HV | HV|b1|hma20|f1 o-1 D1200 tgt2 T120 | -285 | +359 | +346 | +563 | +319 | +583 | +132 | +212 | +4063 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | close | K | K|b1|ema8|atr14|m1.0 o-1 A6 tgt2 T60 | +328 | +219 | +410 | +444 | +335 | +425 | -96 | -183 | +3109 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | close | K | K|b1|ema8|atr14|m1.0 o-1 A6 tgt1.5 T60 | +328 | +219 | +410 | +444 | +328 | +375 | -96 | -183 | +3109 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | close | K | K|b1|ema8|atr14|m1.0 o-1 A6 tgt1 T60 | +384 | +244 | +406 | +442 | +304 | +330 | -112 | -178 | +3109 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | close | K | K|b1|ema8|atr20|m1.5 o-1 A3 tgt1 T60 | +255 | +512 | +869 | +804 | +441 | -22 | -63 | -119 | +6171 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | pre | K | K|b2|ema13|atr10|m0.5 o-1 A2 tgt2 T120 | +2701 | +3124 | +1794 | +661 | +512 | -1075 | -416 | -701 | +18593 | 0.75 | 0.93 | best-of-F (tolerant) |
| YM | pre | K | K|b2|ema13|atr10|m0.5 o-1 A3 tgt1.5 T120 | +722 | +2168 | +996 | +722 | +781 | -373 | -187 | -603 | +9222 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | pre | K | K|b2|ema13|atr10|m0.5 o-1 A2 tgt1.5 T120 | +1701 | +3231 | +2201 | +847 | +514 | -712 | -379 | -543 | +13294 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | pre | K | K|b2|ema13|atr20|m0.5 o-1 A2 tgt1.5 T120 | +1695 | +3415 | +2158 | +895 | +728 | -121 | -360 | +93 | +9344 | 0.75 | 1.00 | best-of-F (tolerant) |
| YM | london | S | S|b15|atr7|m2.0 o1 D2400 tgt1.5 T120 | +821 | +798 | +568 | +342 | +201 | +91 | -47 | -5 | +1922 | 0.75 | 1.00 | best-of-F (tolerant) |
| YM | london | S | S|b15|atr7|m2.0 o1 D2400 tgt2 T120 | +821 | +798 | +568 | +342 | +201 | +91 | -49 | -5 | +1922 | 0.75 | 1.00 | best-of-F (tolerant) |
| YM | london | S | S|b15|atr7|m2.0 o1 D2400 tgt1 T120 | +821 | +798 | +568 | +342 | +201 | +91 | -46 | -5 | +1922 | 0.75 | 1.00 | best-of-F (tolerant) |
| YM | london | S | S|b15|atr10|m2.0 o1 A6 tgt1.5 T120 | +72 | +1289 | +622 | +841 | +459 | +469 | -392 | -529 | +8721 | 0.67 | 1.00 | best-of-F (tolerant) |
| YM | asia | S | S|b15|atr7|m2.0 o-1 D600 tgt1 T30 | +48 | +397 | +369 | +245 | +197 | +100 | -54 | -51 | +2308 | 0.75 | 0.88 | best-of-F (tolerant) |
| YM | asia | S | S|b15|atr7|m2.0 o-1 D600 tgt2 T30 | +48 | +397 | +369 | +245 | +186 | +51 | -91 | -51 | +2381 | 0.75 | 0.99 | best-of-F (tolerant) |
| YM | asia | S | S|b15|atr7|m2.0 o-1 D600 tgt1.5 T30 | +48 | +397 | +369 | +245 | +212 | +161 | -91 | -51 | +1831 | 0.75 | 0.99 | best-of-F (tolerant) |
| YM | asia | S | S|b15|atr7|m2.0 o-1 D1200 tgt1 T30 | +24 | +199 | +184 | +123 | +84 | -10 | -51 | -25 | +1620 | 0.75 | 1.00 | best-of-F (tolerant) |

## NOW-ONLY (REGIME) cells beside the pooled ones (top 6 by joint z)
| family | params | session | L1M | L3M | L6M | HOLD | MID | PRE | X' | PRE23 | family p |
|--|--|--|--|--|--|--|--|--|--|--|--|
| FB | FB|PD|dep0.25|w3 o-1 A3 tgt1.5 T60 | asia | +781 | +1113 | +968 | +439 | +77 | -211 | -288 | -221 | 0.12 |
| FB | FB|PD|dep0.25|w3 o-1 A3 tgt1 T60 | asia | +581 | +942 | +832 | +445 | +394 | -228 | -259 | -247 | 0.13 |
| FB | FB|PD|dep0.25|w10 o-1 A3 tgt1.5 T60 | asia | +373 | +1065 | +818 | +493 | +536 | -207 | -405 | -247 | 0.28 |
| K | K|b1|ema13|atr7|m0.5 o-1 A2 tgt2 T60 | london | +5338 | +3335 | +3136 | +1031 | -1027 | -5389 | -5989 | -8913 | 0.38 |
| FB | FB|PD|dep0.25|w10 o-1 A3 tgt1 T60 | asia | +173 | +894 | +690 | +445 | +611 | -212 | -360 | -289 | 0.40 |
| K | K|b1|ema13|atr7|m0.5 o-1 A2 tgt1.5 T60 | london | +5651 | +2128 | +2007 | +330 | -1077 | -5191 | -5592 | -8742 | 0.49 |

## Stage 2: the top 12 tolerant cells through instr2_eval (placebos shift5/side/days x [HOLD mean, L6M mean, stack Calmar gain], family p with F = 502,740, walk-forward of the cell's own neighbouring settings, correlation to the NQ stack (V0, V2) and equal-risk stack Calmar gain; carry weeks dropped)
| cell | gate tolerant | placebo p_book | family p | WF 6m OOS $/wk (p_rand) | WF 12m OOS | corr V2 daily / weekly | stack dCalmar HOLD / L6M at k* | verdict |
|--|--|--|--|--|--|--|--|--|
| S|b15|atr7|m2.0 -1 asia D600 1.0 30 | True | 0.06 | 1.00 | -20 (0.18) | -34 (0.27) | -0.12 / -0.07 | see rows file | FAILS: family p 1.00 > .10 / walk-forward not positive (6m: OOS -20/wk, p_rand 0.18, 12m: OOS -34/wk, p_rand 0.27) |
| K|b1|ema13|atr7|m1.0 1 nyam A3 1.5 120 | False | 0.10 | 1.00 | +15 (0.51) | -17 (0.61) | 0.00 / -0.03 | see rows file | FAILS: tolerant gate (PRE mean -483 < -0.5 MDE (-447)) / family p 1.00 > .10 / walk-forward not positive (6m: OOS 15/wk, p_rand 0.51, 12m: OOS -17/wk, |
| K|b1|ema13|atr7|m1.0 1 nyam A2 2.0 120 | True | 0.07 | 1.00 | +0 (0.58) | +129 (0.29) | -0.00 / -0.01 | see rows file | FAILS: family p 1.00 > .10 |
| K|b2|ema13|atr10|m0.5 -1 pre A2 2.0 120 | True | 0.89 | 1.00 | -204 (0.80) | +40 (0.27) | 0.02 / 0.00 | see rows file | FAILS: placebo p_book 0.89 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS -204/wk, p_rand 0.80, 12m: OOS 40/wk, p_rand 0.27) / stack |
| K|b1|ema13|atr7|m1.0 1 nyam D600 2.0 120 | True | 0.37 | 1.00 | +48 (0.55) | -94 (0.86) | 0.01 / 0.03 | see rows file | FAILS: placebo p_book 0.37 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS 48/wk, p_rand 0.55, 12m: OOS -94/wk, p_rand 0.86) |
| K|b1|ema13|atr7|m1.0 1 nyam D600 1.0 120 | True | 0.59 | 1.00 | -152 (0.89) | -110 (0.82) | 0.02 / 0.03 | see rows file | FAILS: placebo p_book 0.59 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS -152/wk, p_rand 0.89, 12m: OOS -110/wk, p_rand 0.82) |
| K|b1|ema13|atr7|m1.0 1 nyam A4 1.0 120 | False | 0.05 | 1.00 | +105 (0.30) | +89 (0.34) | 0.02 / 0.01 | see rows file | FAILS: tolerant gate (PRE mean -367 < -0.5 MDE (-329)) / family p 1.00 > .10 |
| K|b2|ema8|atr14|m2.0 -1 nyam A2 1.0 60 | False | 0.35 | 1.00 | -245 (0.95) | -104 (0.66) | -0.00 / -0.03 | see rows file | FAILS: tolerant gate (NOW-ONLY fails (L3M/L6M mean not both > 0)) / persistence 50% <= 60% / placebo p_book 0.35 > .10 / family p 1.00 > .10 / walk-fo |
| S|b15|atr7|m2.0 -1 asia D600 2.0 30 | True | 0.06 | 1.00 | -30 (0.33) | -31 (0.34) | -0.12 / -0.06 | see rows file | FAILS: family p 1.00 > .10 / walk-forward not positive (6m: OOS -30/wk, p_rand 0.33, 12m: OOS -31/wk, p_rand 0.34) |
| S|b15|atr7|m2.0 -1 asia D600 1.5 30 | True | 0.06 | 1.00 | -30 (0.30) | -31 (0.31) | -0.12 / -0.05 | see rows file | FAILS: family p 1.00 > .10 / walk-forward not positive (6m: OOS -30/wk, p_rand 0.30, 12m: OOS -31/wk, p_rand 0.31) |
| K|b1|ema34|atr14|m1.5 1 nyam D600 2.0 120 | True | 0.58 | 1.00 | -337 (1.00) | -55 (0.85) | 0.01 / 0.07 | see rows file | FAILS: placebo p_book 0.58 > .10 / family p 1.00 > .10 / walk-forward not positive (6m: OOS -337/wk, p_rand 1.00, 12m: OOS -55/wk, p_rand 0.85) |
| K|b1|ema13|atr7|m1.0 1 nyam D600 1.5 120 | True | 0.63 | 1.00 | +227 (0.12) | +209 (0.16) | 0.02 / 0.04 | see rows file | FAILS: placebo p_book 0.63 > .10 / family p 1.00 > .10 |

Rows (16-column format) for these cells: autopilot/FADE_ROWS_T2_YM.md. Full cell table: /mnt/l2/l2vast/ds3_instr2_z2/YM/cells_all.parquet (487872 rows; columns fam cfg orient session stop tgt tstop n zj p_fam m_* mde_* pers mdd_* label).

## Reading
* No cell clears the diversifier bar: the family max-T test (Westfall-Young over 457674 eligible cells, joint z of L6M and HOLD against 200 random-side worlds) gives a best tolerant family p of 0.88; every stage-2 cell fails placebo p_book (the stack-gain placebo) and/or family p and/or walk-forward and/or stack Calmar. Correlation of the top cells to the NQ stack is low (|corr| < 0.2) - the gap is edge, not diversification.
* NOW-ONLY cells are REGIME (2026-only profits with negative MID / PRE / X'), consistent with the NQ finding that 2026 is a different regime. Pre-2023 (13 years for YM, from 2017-07 for RTY) is shown by the PRE23 window in the cell table; a book negative in every earlier year is regime-only.
* Best-of-F is not a lead. No PASS; Shadow only; nothing live.

## Limits and what was not done (Z2, stated)
Stage 2 was run on the top 12 tolerant cells by joint z (the prereg says leads and the top 30): none is a lead candidate, so the 13-year percent-frame check, the shuffled-day / matched-clock / side-independent-drift nulls beyond the evaluator's shift5 / side / days placebos, and the tick / 1-s re-run were NOT run; they are triggered by any cell that clears the grid-level family test (none did) and can be run on request for any cell (tick_rerun.py for RTY; YM has no ticks). The ledger holds the top 1,500 tolerant and 1,500 NOW-ONLY cells (full table in the parquet). The bars end 2026-10-16 (RTY 10-23), so L6M / HOLD are 25-26 / 50-51 weeks. Unfixed-code results (ON-level look-ahead) are superseded and must not be used.
