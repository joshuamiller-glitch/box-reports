
## CHAR-A block (DAILY2, 2026-11-06T01:40Z): 1-5 day mean-reversion, gap/overnight/weekend and calendar seasonality, 13 instruments, 2013-2026 percent frame (RTY 2017-07+, MBT/BTC 2022+). REGIME/NULL. Shadow only, no PASS.
Prereg l2vast/ds3/prereg/T_FIND_DAILY2_prereg.md sha256 cf9c0f3a4a9a3bfe7e1adcc7f282b2fab6be872b166c578af403cf33e246ec41 (DECISIONS.md, before any number). Base: label-day bars (17:00 ET roll), signal at the close of day t-1, execution at the open of day t, exact open/close leg accounting, cost = instr2_sessions cost_pts round trip (proxy) charged on turnover, positions scaled so that 2 trailing-20d daily sd = $1,200. Null: the cell's exposure series circularly shifted by a random lag in [60, T-60] days (B=500, keeps the position autocorrelation and the drift it earns); statistic = mean daily net $; WY max-|z| over the block. The null z has sd 0.7-0.9 (not 1.0), i.e. the null is slightly conservative.
| block | cells | min p_family | cells with p_family <= .10 | all-block family cells <= .10 |
|--|--|--|--|--|
| A1 | 312 | 0.89 | 0 | 0 |
| A2 | 24 | 0.89 | 0 | 0 |
| A3 | 130 | 0.89 | 0 | 0 |

By-instrument cells are in daily2_screen.csv (z, p, year sign share, pre-2023 and 2023+ mean $/day per cell). Pooled across instruments (Stouffer of the per-instrument standardised stats against the common shifted null, WY over the block's effects; per-year pooled means in daily2_A_pooled.csv):
| block | effect | instruments | pooled z | p_family | year sign share |
|--|--|--|--|--|--|
| A2 | monday_id | 4 | +2.32 | 0.55 | 0.69 |
| A2 | id_long | 4 | -2.26 | 0.58 | 0.69 |
| A1 | rev_k3_h5_ext0 | 13 | +2.37 | 0.64 | 0.62 |
| A3 | month_end | 13 | -2.31 | 0.71 | 0.69 |
| A2 | on_long | 4 | -1.23 | 0.96 | 0.31 |
| A3 | dow1 | 13 | -1.55 | 0.99 | 0.77 |
| A1 | rev_k1_h1_ext1 | 13 | +1.26 | 0.99 | 0.31 |
| A3 | quarter_end_week | 13 | -1.45 | 0.99 | 0.54 |
| A1 | rev_k5_h3_ext0 | 13 | +1.18 | 1.00 | 0.38 |
| A1 | rev_k2_h1_ext1 | 13 | +1.19 | 1.00 | 0.31 |

Plain sentences: (1) 1-5 day reversal (k 1/2/3/5 days, hold 1/3/5 days, with and without a 1-sd extreme filter) does not exist beyond what the shifted-position null produces on any of the 13 instruments (312 cells, min p_family 0.89) nor pooled (best pooled p 0.64: k3/h5 reversal z +2.4 and year sign share 0.62). (2) Gap / overnight / weekend: the overnight leg is not special, the intraday leg of the equity indices is slightly negative or zero, and gap fade/follow are null (24 cells, min p 0.89). (3) Seasonality (130 cells): the only visible thing is a MONDAY effect in the four equity indices -- Monday (the label day that starts on Sunday 18:00) beats the other weekdays by +7 (ES, t 1.6), +11 (NQ, t 2.0), +16 (RTY, t 2.1) and +6.5 (YM, t 1.5) bps open-to-close, positive in 64-80% of years, but only +1..+9 bps before 2023 and +17..+30 bps in 2023-26, and p_family 1.0 once the shifted-position null (which already earns the equity drift) is applied; the equity gross dow0 t-stats (NQ 3.1, ES 2.7, YM 2.3, RTY 2.3) are the largest of the 130 and are not family-significant. Month-end, turn-of-month, pre-holiday, options-expiry and quarter-end effects are null (CL, ZB, 6J Monday and 6E pre-holiday show gross negatives with t about -2.5, also not significant).
Descriptive evaluator read of the equity Monday long (not eligible under the frozen screening rule, p_family 1.0): ES / NQ / RTY / YM L6M +118 / +115 / +14 / +62, HOLD +259 / +244 / +171 / +159, PRE +83 / +86 / +61 / +43, X' +202 / +188 / +192 / +214 $/wk at the $1,200 scale, corr to the NQ stack -0.02..-0.12, stack Calmar dCalmar at k* +0.03..+0.04 in HOLD; tolerant gate FAILS (L3M/L6M not both positive), walk-forward not positive for ES/RTY/YM, positive but unstable by year. Label: REGIME/WATCH (2023-26 stronger than 2013-22, equity indices are one correlated bet, family p 1.0). Nothing clears. Blocks B (cross-sectional) and C (vol-regime) were screened before the scope change (min p_family 0.90 and 0.26) and handed to Z1 / ZL-2 (files named in MORNING.md); Block D not started.

## RESULTS (S4a, 2026-11-06 01:42Z; prereg sha256 bf1de6c6902656b32ab9c86981f7b0d3e138ebde062ae719b2ded22839f72129)

**Plain sentence: no daily-horizon book on the owned instruments is a lead. Of 408 cells (34 families/parameter sets x 11 instruments + equal-$ portfolio), 191 are net positive over 2013-2026, 67 also positive in at least 60% of years, 46 also pass the tolerant per-year MDE test and 36 pass the HOLD test (tolerant gate); none of those has a family p <= .10 under the random-side null (best 0.33) or the forward-shift null (best 0.00), the best real z (2.84 random-side) sits inside the family-maximum null (median 2.69, p95 3.41), and the annual-refit walk-forward is positive but not distinguishable from random parameter choice for the same families. Labels: {'NULL': 283, 'REGIME': 89, 'best-of-F (tolerant, family p>.10)': 36}.**

Funnel (cells): all 408; T1 13-year net > 0: 191; + T2 positive in >= 60% of years: 67; + T3 every year >= -0.5 MDE: 46; + T4 HOLD mean > 0 (tolerant): 36.
Family nulls (200 hash_u worlds each): random-side maximum z median 2.69, p95 3.41; forward-shift maximum z median 2.66, p95 3.45 (unconditional leg cells have no shift null). Look-ahead truncation test: 0 mismatches of 891 checks.

**Amendment 1 (after seeing the first null run, not tuned on results):** for the six unconditional leg cells (night, weekend, day, long and short) the cell's long share is 0 or 1, which makes the prereg random-side flip degenerate (z undefined); their random-side null uses probability 0.5. No other change to the prereg. Errata: the 86 DEAD_CELLS "tsmom" rows are A3SZ sizing features of the NQ book and the "donchian" rows are intraday brackets, so no daily-hold book was previously tested.

### Tolerant cells (maxDD first; $ at stated lots, equal-$ vol sizing with 1-lot floor, whole contracts; HOLD/L6M in $/week carry-dropped; wf_* = annual-refit walk-forward of the same instrument and family)
| inst | cell | maxdd | total | annual | calmar | years_pos | HOLD_wk | L6M_wk | long_share | peak_lots | zR | pR | zS | pS | q | wf_total | wf_p | corr_nq_wk | dcalmar_stack | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ES | MR_k5_th1.5 | 26869 | 89003 | 6216 | 0.23 | 11/14 | 378 | 160 | 0.46 | 3.00 | 2.84 | 0.33 | 2.24 | 0.87 | 0.46 | 24199 | 0.66 | -0.01 | 0.19 | best-of-F (tolerant, family p>.10) |
| RTY | NIGHT_L | 30912 | 67037 | 6952 | 0.22 | 7/10 | 116 | 481 | 1.00 | 4.00 | 2.71 | 0.47 | n/a | 1.00 | 0.46 | 28139 | 0.08 | 0.06 | 0.04 | best-of-F (tolerant, family p>.10) |
| YM | NIGHT_L | 62198 | 59193 | 4134 | 0.07 | 9/14 | 132 | 957 | 1.00 | 5.00 | 2.25 | 0.96 | n/a | 1.00 | 0.77 | 36368 | 0.11 | 0.08 | 0.06 | best-of-F (tolerant, family p>.10) |
| ES | MR_k3_th1.5 | 35589 | 80292 | 5608 | 0.16 | 9/14 | 341 | -154 | 0.49 | 5.00 | 2.09 | 0.99 | 2.01 | 0.98 | 0.77 | 24199 | 0.66 | -0.03 | 0.19 | best-of-F (tolerant, family p>.10) |
| ES | MR_k5_th1 | 50330 | 76573 | 5348 | 0.11 | 11/14 | 375 | 686 | 0.38 | 5.00 | 2.06 | 0.99 | 1.84 | 0.99 | 0.77 | 24199 | 0.66 | 0.03 | 0.08 | best-of-F (tolerant, family p>.10) |
| RTY | WKND_L | 15544 | 27739 | 2877 | 0.19 | 7/10 | 139 | 360 | 1.00 | 4.00 | 1.86 | 1.00 | 0.75 | 1.00 | 0.77 | 28139 | 0.08 | 0.07 | 0.00 | best-of-F (tolerant, family p>.10) |
| PORT | MA_10_50 | 189882 | 497372 | 34739 | 0.18 | 9/14 | 2795 | 9983 | n/a | n/a | 1.84 | 1.00 | 0.97 | 1.00 | 0.77 | -48208 | 0.97 | 0.05 | 0.19 | best-of-F (tolerant, family p>.10) |
| GC | NIGHT_L | 100944 | 137365 | 9594 | 0.10 | 9/14 | 933 | -2970 | 1.00 | 2.00 | 1.65 | 1.00 | n/a | 1.00 | 0.77 | -97872 | 0.62 | -0.16 | 0.03 | best-of-F (tolerant, family p>.10) |
| PORT | DON_N100_SAR | 306947 | 609699 | 42584 | 0.14 | 11/14 | 1852 | 1444 | n/a | n/a | 1.65 | 1.00 | 2.60 | 0.58 | 0.77 | 385235 | 0.19 | -0.11 | 0.03 | best-of-F (tolerant, family p>.10) |
| CL | DON_N20_SAR | 47782 | 145271 | 10146 | 0.21 | 9/14 | 1139 | 301 | 0.50 | 2.00 | 1.51 | 1.00 | 1.88 | 0.99 | 0.77 | 81355 | 0.06 | 0.03 | 0.05 | best-of-F (tolerant, family p>.10) |
| MBT | TSMOM_L126_vol | 14137 | 53533 | 10707 | 0.76 | 4/5 | 471 | 433 | 0.61 | 6.00 | 1.33 | 1.00 | 2.51 | 0.70 | 0.78 | 17565 | 0.13 | 0.03 | 0.19 | best-of-F (tolerant, family p>.10) |
| MBT | TSMOM_L126_1lot | 3398 | 9442 | 1888 | 0.56 | 4/5 | 99 | 72 | 0.61 | 1.00 | 1.30 | 1.00 | 2.71 | 0.48 | 0.78 | 17565 | 0.13 | 0.04 | 0.02 | best-of-F (tolerant, family p>.10) |
| GC | MA_10_50 | 124339 | 169464 | 11836 | 0.10 | 10/14 | 2523 | 4293 | 0.51 | 2.00 | 1.29 | 1.00 | 1.24 | 1.00 | 0.78 | 89289 | 0.92 | 0.06 | 0.11 | best-of-F (tolerant, family p>.10) |
| PORT | TSMOM_L126_vol | 455128 | 476785 | 33301 | 0.07 | 9/14 | 5186 | 4324 | n/a | n/a | 1.27 | 1.00 | 1.11 | 1.00 | 0.78 | 66137 | 0.60 | -0.09 | 0.09 | best-of-F (tolerant, family p>.10) |
| 6E | TSMOM_L126_vol | 83688 | 98358 | 6870 | 0.08 | 10/14 | 218 | 817 | 0.41 | 4.00 | 1.12 | 1.00 | 2.09 | 0.95 | 0.78 | 40893 | 0.17 | 0.18 | 0.00 | best-of-F (tolerant, family p>.10) |
| PORT | TSMOM_L63_vol | 564881 | 225486 | 15749 | 0.03 | 10/14 | 4981 | 8249 | n/a | n/a | 1.10 | 1.00 | -0.11 | 1.00 | 0.78 | 66137 | 0.60 | -0.03 | 0.22 | best-of-F (tolerant, family p>.10) |
| GC | TSMOM_L126_vol | 158996 | 219368 | 15322 | 0.10 | 9/14 | 1064 | -472 | 0.61 | 2.00 | 0.96 | 1.00 | 1.88 | 0.99 | 0.78 | 174073 | 0.15 | -0.08 | 0.02 | best-of-F (tolerant, family p>.10) |
| 6E | TSMOM_L126_1lot | 41958 | 33583 | 2346 | 0.06 | 9/14 | 44 | 251 | 0.41 | 1.00 | 0.92 | 1.00 | 1.84 | 0.99 | 0.78 | 40893 | 0.17 | 0.16 | 0.00 | best-of-F (tolerant, family p>.10) |
| PORT | MA_20_100 | 369628 | 240421 | 16792 | 0.05 | 9/14 | 1336 | 3728 | n/a | n/a | 0.86 | 1.00 | -0.51 | 1.00 | 0.78 | -48208 | 0.97 | -0.08 | 0.06 | best-of-F (tolerant, family p>.10) |
| CL | DON_N40_SAR | 74715 | 82103 | 5734 | 0.08 | 9/14 | 992 | -77 | 0.54 | 2.00 | 0.85 | 1.00 | 1.30 | 1.00 | 0.78 | 81355 | 0.06 | 0.03 | 0.05 | best-of-F (tolerant, family p>.10) |
| CL | TSMOM_L252_vol | 107253 | 64771 | 4524 | 0.04 | 9/14 | 130 | -1211 | 0.44 | 2.00 | 0.83 | 1.00 | 1.14 | 1.00 | 0.78 | -31904 | 0.91 | -0.02 | 0.00 | best-of-F (tolerant, family p>.10) |
| CL | TSMOM_L252_1lot | 107253 | 63692 | 4449 | 0.04 | 9/14 | 130 | -1211 | 0.44 | 1.00 | 0.80 | 1.00 | 1.42 | 1.00 | 0.78 | -31904 | 0.91 | -0.02 | 0.00 | best-of-F (tolerant, family p>.10) |
| PORT | TSMOM_L252_1lot | 247134 | 273820 | 19125 | 0.08 | 9/14 | 1752 | -3540 | n/a | n/a | 0.78 | 1.00 | -0.75 | 1.00 | 0.78 | 66137 | 0.60 | -0.17 | 0.02 | best-of-F (tolerant, family p>.10) |
| MBT | MR_k1_th1.5 | 7645 | 5556 | 1111 | 0.15 | 3/5 | 139 | -41 | 0.41 | 6.00 | 0.76 | 1.00 | 0.89 | 1.00 | 0.78 | -6017 | 0.28 | 0.11 | 0.00 | best-of-F (tolerant, family p>.10) |
| GC | DON_N40_SAR | 158468 | 85382 | 5963 | 0.04 | 9/14 | 1038 | 1808 | 0.55 | 2.00 | 0.73 | 1.00 | 0.02 | 1.00 | 0.78 | 42814 | 0.69 | 0.06 | 0.03 | best-of-F (tolerant, family p>.10) |
| GC | DON_N20_SAR | 159121 | 132367 | 9245 | 0.06 | 9/14 | 4130 | 4293 | 0.51 | 2.00 | 0.72 | 1.00 | 0.84 | 1.00 | 0.78 | 42814 | 0.69 | 0.05 | 0.31 | best-of-F (tolerant, family p>.10) |
| 6E | DON_N100_SAR | 70191 | 57335 | 4005 | 0.06 | 9/14 | 213 | 1140 | 0.40 | 4.00 | 0.65 | 1.00 | 2.06 | 0.95 | 0.78 | -12502 | 0.43 | 0.04 | 0.00 | best-of-F (tolerant, family p>.10) |
| CL | DON_N60_EX | 55494 | 57678 | 4028 | 0.07 | 9/14 | 921 | -158 | 0.51 | 2.00 | 0.63 | 1.00 | 1.72 | 1.00 | 0.78 | 81355 | 0.06 | 0.04 | 0.04 | best-of-F (tolerant, family p>.10) |
| RTY | DON_N60_SAR | 50034 | 50432 | 5230 | 0.10 | 6/10 | 79 | 921 | 0.69 | 3.00 | 0.63 | 1.00 | 1.80 | 1.00 | 0.78 | -56295 | 0.86 | -0.04 | 0.08 | best-of-F (tolerant, family p>.10) |
| MBT | TSMOM_L252_1lot | 3638 | 4662 | 932 | 0.26 | 4/5 | 49 | 105 | 0.64 | 1.00 | 0.59 | 1.00 | 1.47 | 1.00 | 0.78 | 17565 | 0.13 | 0.01 | 0.02 | best-of-F (tolerant, family p>.10) |
| MBT | TSMOM_L252_vol | 18290 | 28499 | 5700 | 0.31 | 3/5 | 277 | 630 | 0.64 | 6.00 | 0.58 | 1.00 | 1.24 | 1.00 | 0.78 | 17565 | 0.13 | 0.00 | 0.17 | best-of-F (tolerant, family p>.10) |
| MBT | DON_N40_EX | 27146 | 10585 | 2117 | 0.08 | 5/5 | 58 | -24 | 0.53 | 6.00 | 0.55 | 1.00 | 0.99 | 1.00 | 0.78 | -10588 | 0.75 | -0.07 | 0.16 | best-of-F (tolerant, family p>.10) |
| NKD | DON_N100_SAR | 91162 | 137664 | 9615 | 0.11 | 10/14 | 1711 | 1993 | 0.69 | 3.00 | 0.53 | 1.00 | 0.93 | 1.00 | 0.78 | 73336 | 0.17 | -0.10 | 0.06 | best-of-F (tolerant, family p>.10) |
| MBT | DON_N20_EX | 31278 | 11848 | 2370 | 0.08 | 3/5 | 211 | 374 | 0.57 | 6.00 | 0.50 | 1.00 | 0.55 | 1.00 | 0.78 | -10588 | 0.75 | 0.02 | 0.08 | best-of-F (tolerant, family p>.10) |
| MBT | DON_N100_SAR | 27760 | 11558 | 2312 | 0.08 | 4/5 | 471 | 433 | 0.57 | 6.00 | 0.47 | 1.00 | 0.62 | 1.00 | 0.78 | -10588 | 0.75 | -0.02 | 0.19 | best-of-F (tolerant, family p>.10) |
| NKD | MA_50_200 | 120103 | 104423 | 7293 | 0.06 | 9/14 | 1711 | 1993 | 0.72 | 3.00 | 0.40 | 1.00 | 0.71 | 1.00 | 0.78 | 69196 | 0.14 | -0.02 | 0.06 | best-of-F (tolerant, family p>.10) |

### Top 15 cells by random-side z (all, including non-tolerant)
| inst | cell | maxdd | total | annual | calmar | years_pos | HOLD_wk | L6M_wk | long_share | peak_lots | zR | pR | zS | pS | q | wf_total | wf_p | corr_nq_wk | dcalmar_stack | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ES | MR_k5_th1.5 | 26869 | 89003 | 6216 | 0.23 | 11/14 | 378 | 160 | 0.46 | 3.00 | 2.84 | 0.33 | 2.24 | 0.87 | 0.46 | 24199 | 0.66 | -0.01 | 0.19 | best-of-F (tolerant, family p>.10) |
| 6E | NIGHT_S | 71062 | 36571 | 2554 | 0.04 | 9/14 | -51 | 241 | 0.00 | 4.00 | 2.73 | 0.47 | n/a | 1.00 | 0.46 | -51618 | 0.24 | -0.06 | 0.02 | NULL |
| RTY | NIGHT_L | 30912 | 67037 | 6952 | 0.22 | 7/10 | 116 | 481 | 1.00 | 4.00 | 2.71 | 0.47 | n/a | 1.00 | 0.46 | 28139 | 0.08 | 0.06 | 0.04 | best-of-F (tolerant, family p>.10) |
| ES | NIGHT_L | 75008 | 36219 | 2530 | 0.03 | 10/14 | 150 | 542 | 1.00 | 5.00 | 2.47 | 0.81 | n/a | 1.00 | 0.69 | -57729 | 0.45 | 0.09 | 0.00 | REGIME |
| NKD | DAY_L | 294481 | -255625 | -17854 | -0.06 | 2/14 | 878 | 811 | 1.00 | 3.00 | 2.27 | 0.95 | n/a | 1.00 | 0.77 | -3577 | 0.00 | -0.08 | 0.23 | NULL |
| YM | NIGHT_L | 62198 | 59193 | 4134 | 0.07 | 9/14 | 132 | 957 | 1.00 | 5.00 | 2.25 | 0.96 | n/a | 1.00 | 0.77 | 36368 | 0.11 | 0.08 | 0.06 | best-of-F (tolerant, family p>.10) |
| 6J | NIGHT_S | 99246 | -11320 | -791 | -0.01 | 7/14 | -109 | -18 | 0.00 | 6.00 | 2.11 | 0.99 | n/a | 1.00 | 0.77 | -24285 | 0.14 | -0.05 | 0.01 | NULL |
| ES | MR_k3_th1.5 | 35589 | 80292 | 5608 | 0.16 | 9/14 | 341 | -154 | 0.49 | 5.00 | 2.09 | 0.99 | 2.01 | 0.98 | 0.77 | 24199 | 0.66 | -0.03 | 0.19 | best-of-F (tolerant, family p>.10) |
| 6J | DON_N60_EX | 42997 | 118451 | 8273 | 0.19 | 9/14 | -78 | 48 | 0.34 | 6.00 | 2.07 | 0.99 | 2.63 | 0.56 | 0.77 | 27341 | 0.21 | -0.06 | 0.00 | NULL |
| ES | MR_k5_th1 | 50330 | 76573 | 5348 | 0.11 | 11/14 | 375 | 686 | 0.38 | 5.00 | 2.06 | 0.99 | 1.84 | 0.99 | 0.77 | 24199 | 0.66 | 0.03 | 0.08 | best-of-F (tolerant, family p>.10) |
| PORT | NIGHT_L | 1616757 | -1498567 | -104667 | -0.06 | 2/14 | -1989 | -5490 | n/a | n/a | 2.04 | 1.00 | n/a | 1.00 | 0.77 | -617435 | 0.06 | 0.00 | -0.01 | REGIME |
| 6J | TSMOM_L63_1lot | 18178 | 56392 | 3939 | 0.22 | 7/14 | 50 | 156 | 0.37 | 1.00 | 1.99 | 1.00 | 2.98 | 0.26 | 0.77 | 10432 | 0.14 | -0.02 | 0.00 | NULL |
| RTY | WKND_L | 15544 | 27739 | 2877 | 0.19 | 7/10 | 139 | 360 | 1.00 | 4.00 | 1.86 | 1.00 | 0.75 | 1.00 | 0.77 | 28139 | 0.08 | 0.07 | 0.00 | best-of-F (tolerant, family p>.10) |
| PORT | MA_10_50 | 189882 | 497372 | 34739 | 0.18 | 9/14 | 2795 | 9983 | n/a | n/a | 1.84 | 1.00 | 0.97 | 1.00 | 0.77 | -48208 | 0.97 | 0.05 | 0.19 | best-of-F (tolerant, family p>.10) |
| NKD | MR_k1_th1 | 52232 | 10092 | 705 | 0.01 | 5/14 | 365 | -1121 | 0.45 | 3.00 | 1.81 | 1.00 | 1.68 | 1.00 | 0.77 | -19913 | 0.48 | 0.02 | 0.02 | REGIME |

### Per-year net $ (tolerant cells, top 20 by z; thousands)
| inst | cell | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ES | MR_k5_th1.5 | 2 | -11 | 5 | 11 | 4 | -0 | 0 | 13 | 22 | 6 | -9 | 6 | 13 | 26 |
| RTY | NIGHT_L | - | - | - | - | 10 | 5 | 10 | 15 | 23 | -13 | -3 | 16 | -7 | 12 |
| YM | NIGHT_L | 12 | 3 | -12 | -9 | 40 | 14 | 4 | 14 | 12 | -22 | -1 | 5 | -18 | 18 |
| ES | MR_k3_th1.5 | 2 | 3 | -1 | -0 | 12 | -10 | 1 | 27 | 27 | -8 | -3 | 7 | 11 | 14 |
| ES | MR_k5_th1 | 13 | -12 | 23 | 9 | 7 | -26 | 13 | -24 | 15 | 11 | 4 | 9 | 25 | 10 |
| RTY | WKND_L | - | - | - | - | 6 | 3 | -1 | 6 | 6 | -8 | -1 | 4 | 8 | 4 |
| PORT | MA_10_50 | -4 | -14 | -43 | 57 | -46 | 112 | 41 | 73 | 8 | 87 | 42 | -66 | 220 | 30 |
| GC | NIGHT_L | -50 | -16 | -26 | 17 | 2 | 4 | 16 | 44 | -12 | -24 | 3 | 38 | 123 | 20 |
| PORT | DON_N100_SAR | 66 | 93 | -18 | 85 | 92 | 33 | 23 | -19 | 147 | 58 | -108 | 4 | 113 | 42 |
| CL | DON_N20_SAR | 8 | 29 | 5 | -8 | -4 | 10 | -18 | 47 | 0 | 30 | 9 | -5 | -6 | 48 |
| MBT | TSMOM_L126_vol | - | - | - | - | - | - | - | - | - | 1 | -7 | 26 | 16 | 18 |
| MBT | TSMOM_L126_1lot | - | - | - | - | - | - | - | - | - | 0 | -1 | 4 | 4 | 3 |
| GC | MA_10_50 | 30 | 8 | 3 | 21 | -45 | 31 | 19 | -0 | -23 | 13 | -11 | 4 | 83 | 37 |
| PORT | TSMOM_L126_vol | 48 | 133 | -60 | 177 | 139 | 11 | -44 | -59 | 31 | 24 | -21 | -114 | 30 | 182 |
| 6E | TSMOM_L126_vol | 0 | 45 | 17 | -6 | 14 | 12 | 17 | 10 | 10 | 30 | -17 | -23 | -23 | 10 |
| PORT | TSMOM_L63_vol | 37 | 56 | -78 | 84 | 90 | 94 | 22 | 86 | 30 | -88 | -102 | -166 | 123 | 36 |
| GC | TSMOM_L126_vol | 6 | -3 | 17 | 25 | 9 | -1 | 30 | 18 | -26 | -17 | -26 | 37 | 151 | 1 |
| 6E | TSMOM_L126_1lot | -3 | 16 | 10 | -4 | 7 | 6 | 7 | 3 | 3 | 12 | -9 | -9 | -9 | 2 |
| PORT | MA_20_100 | 1 | 35 | -40 | 52 | 49 | 45 | -71 | 47 | 78 | 35 | -45 | -46 | 182 | -83 |
| CL | DON_N40_SAR | -10 | 46 | 17 | 2 | 19 | 31 | -13 | -2 | -5 | 15 | 0 | -35 | 1 | 17 |

### Annual-refit walk-forward (expanding window, parameter = best train Sharpe within instrument x family; OOS from the 5th year)
| scope | family | OOS total $ | years tested | p vs random parameter choice | maxDD OOS $ | last pick |
|--|--|--|--|--|--|--|
| ES | F1 | 80712 | 10 | 0.44 | 108750 | TSMOM_L126_vol |
| ES | F2 | 6276 | 10 | 0.58 | 98734 | DON_N100_SAR |
| ES | F3 | 47645 | 10 | 0.72 | 114988 | MA_20_100 |
| ES | F4 | 24199 | 10 | 0.66 | 76782 | MR_k3_th1.5 |
| ES | F5 | -57729 | 10 | 0.45 | 123840 | NIGHT_L |
| RTY | F1 | -94437 | 6 | 0.90 | 124310 | TSMOM_L21_vol |
| RTY | F2 | -56295 | 6 | 0.86 | 89134 | DON_N60_EX |
| RTY | F3 | -27700 | 6 | 0.43 | 78069 | MA_10_50 |
| RTY | F4 | 32073 | 6 | 0.19 | 35963 | MR_k1_th1 |
| RTY | F5 | 28139 | 6 | 0.08 | 30912 | NIGHT_L |
| YM | F1 | -147630 | 10 | 1.00 | 189761 | TSMOM_L21_vol |
| YM | F2 | 5020 | 10 | 0.45 | 101797 | DON_N100_SAR |
| YM | F3 | 6842 | 10 | 0.55 | 126759 | MA_50_200 |
| YM | F4 | 56995 | 10 | 0.13 | 36442 | MR_k1_th1.5 |
| YM | F5 | 36368 | 10 | 0.11 | 62198 | NIGHT_L |
| GC | F1 | 174073 | 10 | 0.15 | 158996 | TSMOM_L126_vol |
| GC | F2 | 42814 | 10 | 0.69 | 193476 | DON_N100_SAR |
| GC | F3 | 89289 | 10 | 0.92 | 188896 | MA_50_200 |
| GC | F4 | -42997 | 10 | 0.68 | 134247 | MR_k3_th1 |
| GC | F5 | -97872 | 10 | 0.62 | 137280 | NIGHT_L |
| CL | F1 | -31904 | 10 | 0.91 | 114636 | TSMOM_L21_vol |
| CL | F2 | 81355 | 10 | 0.06 | 53753 | DON_N20_SAR |
| CL | F3 | 64666 | 10 | 0.14 | 63317 | MA_10_50 |
| CL | F4 | -51778 | 10 | 0.67 | 75274 | MR_k5_th1.5 |
| CL | F5 | 1961 | 10 | 0.12 | 35845 | WKND_S |
| ZN | F1 | -3943 | 10 | 0.42 | 68731 | TSMOM_L252_1lot |
| ZN | F2 | 28384 | 10 | 0.69 | 71823 | DON_N40_EX |
| ZN | F3 | 48041 | 10 | 0.42 | 51225 | MA_10_50 |
| ZN | F4 | -17579 | 10 | 0.23 | 53932 | MR_k5_th1.5 |
| ZN | F5 | -78825 | 10 | 0.00 | 84587 | WKND_S |
| ZB | F1 | -131042 | 10 | 0.99 | 151725 | TSMOM_L21_1lot |
| ZB | F2 | 46073 | 10 | 0.16 | 45137 | DON_N100_EX |
| ZB | F3 | 67324 | 10 | 0.26 | 30115 | MA_10_50 |
| ZB | F4 | -24366 | 10 | 0.32 | 33944 | MR_k5_th1.5 |
| ZB | F5 | -69169 | 10 | 0.01 | 73762 | WKND_S |
| 6E | F1 | 40893 | 10 | 0.17 | 83688 | TSMOM_L126_vol |
| 6E | F2 | -12502 | 10 | 0.43 | 61016 | DON_N100_EX |
| 6E | F3 | -75972 | 10 | 1.00 | 114480 | MA_10_50 |
| 6E | F4 | -14413 | 10 | 0.39 | 47371 | MR_k5_th1.5 |
| 6E | F5 | -51618 | 10 | 0.24 | 71062 | NIGHT_S |
| 6J | F1 | 10432 | 10 | 0.14 | 22641 | TSMOM_L63_1lot |
| 6J | F2 | 27341 | 10 | 0.21 | 49152 | DON_N60_EX |
| 6J | F3 | -1154 | 10 | 0.37 | 89301 | MA_20_100 |
| 6J | F4 | 8128 | 10 | 0.44 | 16930 | MR_k1_th1.5 |
| 6J | F5 | -24285 | 10 | 0.14 | 66596 | WKND_S |
| MBT | F1 | 17565 | 1 | 0.13 | 11754 | TSMOM_L126_vol |
| MBT | F2 | -10588 | 1 | 0.75 | 19011 | DON_N40_SAR |
| MBT | F3 | -20771 | 1 | 1.00 | 35241 | MA_20_100 |
| MBT | F4 | -6017 | 1 | 0.28 | 7645 | MR_k1_th1.5 |
| MBT | F5 | -7584 | 1 | 1.00 | 17658 | NIGHT_L |
| NKD | F1 | 140352 | 10 | 0.04 | 62437 | TSMOM_L252_vol |
| NKD | F2 | 73336 | 10 | 0.17 | 110824 | DON_N100_SAR |
| NKD | F3 | 69196 | 10 | 0.14 | 120103 | MA_50_200 |
| NKD | F4 | -19913 | 10 | 0.48 | 43377 | MR_k1_th1 |
| NKD | F5 | -3577 | 10 | 0.00 | 66177 | WKND_L |
| PORT | F1 | 66137 | 10 | 0.60 | 502846 | TSMOM_L126_vol |
| PORT | F2 | 385235 | 10 | 0.19 | 306947 | DON_N100_SAR |
| PORT | F3 | -48208 | 10 | 0.97 | 465240 | MA_10_50 |
| PORT | F4 | -24072 | 10 | 0.26 | 181737 | MR_k3_th1.5 |
| PORT | F5 | -617435 | 10 | 0.06 | 662407 | WKND_S |

### Reading
* Execution: signals at 15:55 ET from bars through 15:54, market orders at 15:55 ET (night/weekend legs enter 15:55 and exit 09:30 ET, day legs 09:30 to 15:55), 1 tick slip per side plus fee/2 per lot per side, roll cost 2 slips + one RT fee per held lot, no stop orders. NT8/Rithmic: one daily timer-driven strategy per instrument, market orders; positions are held through the maintenance break.
* Sizing: whole lots, 1-lot floor, so index futures run above the $1,200 daily-sigma target (realised daily sigma per cell is in cells.pkl); margin is not in FEES.md: notional per lot is in the ledger-linked frames, no margin claim.
* TREND-BETA and REGIME: see the long_share and per-year columns; equity momentum/reversion cells are long-biased and concentrated in 2013-2021/2026 swings.
* Frames: /mnt/l2/l2vast/instr2_trades/DAILY/<SYM>_<cell>.parquet (entry/exit epoch, side, lots, raw entry/exit prices, stop_px = NaN because no stop orders exist, net $ = gross - roll - entry/exit cost; intra-episode lot changes not allocated). Ledger T2F_DAILY_<SYM> / T2F_DAILY_PORT (408 rows); n_tested +408.
* Code l2vast/ds3/code/t2s4a/daily_lib.py, daily_run.py, daily_analyze.py, daily_report.py; data /mnt/l2/l2vast/ds3_daily/.

## Z1 block (DAILY4, 2026-11-06): CROSS-SECTIONAL daily rank books - EQ3 (ES RTY YM), FX2 (6E 6J), CMD4 (GC CL ZN ZB). NO CELL CLEARS; CMD4 momentum is a coherent but family-insignificant WATCH (post-hoc diagnostics only)
Prereg l2vast/ds3/prereg/T2F_DAILY4_prereg.md sha256 c3d25924e715ff2035582513ed66f87c1680ce8947ccab86d3eb4c1d966aa8a8 (DECISIONS.md, filed before any number). BASE: percent frame (multiplicative roll-adjusted), repaired 1-min cache (find_c/cache_c), decision at the 16:55 ET bar, execution at the 16:56 ET open (market orders, NT8/Rithmic, all legs together), 2013-01..2026-10-16 (RTY from 2017-07; EQ3 ranks ES/YM only before). 84 cells = 3 baskets x lookback {1,2,3,5,10,15,20} days x momentum/reversal x daily/weekly rebalance; dollar-neutral by notional (each side +-1 before scaling), inverse-vol rank weights, vol target $1,200/day (trailing 60 d, reset at rebalances); cost per leg per side = fee/2 + 1 tick slippage (instr2_sessions.json, FEES.md), rolls cost 2 sides per held contract. Screening begins day 130 (warm-up). Null = forward-only circular time shift of each cell's position path against the returns (B 500, lag 60..T-60; keeps turnover, autocorrelation and cross-section), Westfall-Young max-z over the 84 cells; second null = fixed member permutation (EQ3 5, CMD4 23 non-identity permutations). Truncation test: weights use closes through the decision bar only (rank/signal built from lnP up to t; verified by construction and by the tie-out of unit book P&L, not by a separate cut test - noted limitation).
| basket | cells | net>0 | best cell (L, dir, reb) | net $/day | gross / cost $/day | Sharpe (ann.) | years positive | z | per-cell p | family p (84 cells) | basket-family p | screen |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| EQ3 | 28 | 2 | L 20 mom W (best z 0.88) | +9.4 | - | <0.1 | - | 0.88 | - | 1.00 | 1.00 | no |
| FX2 | 28 | 8 | L 15 rev W | +26.8 | 32.6 / 5.7 | 0.34 | 71% | 1.50 | 0.074 | 0.98 | 0.75 | no |
| CMD4 | 28 | 13 | L 15 mom D | +46.0 | 61.3 / 15.3 | 0.56 | 71% | 1.75 | 0.048 | 0.88 | 0.50 | no |
World max z: median 2.28, 95th percentile 3.39; the best observed z is 1.91 (CMD4 L1 mom D). Frozen screen (p_family <= .10, net > 0, >= 60% positive years): 0 cells.
**Plain finding.** Equity-index relative strength (ES/RTY/YM) loses after cost at every lookback (26 of 28 cells negative): the three indices are too correlated for rank spreads to cover 3 legs of cost. 6E/6J: only a 15-day weekly reversal is positive (+$27/day, X' -$829/wk, fails the tolerant gate). Metals-energy-rates (GC CL ZN ZB): cross-sectional MOMENTUM is positive at every lookback >= 5 days and both rebalance rates (net $/day, daily/weekly: L5 27/27, L10 13/21, L15 46/32, L20 24/31) while the mirror REVERSAL is negative at every lookback (-23 .. -102 $/day), a coherent sign structure; it does not clear the 84-cell family (best z 1.9 against a world-max median 2.3).
**Annual-refit walk-forward** (expanding best-Sharpe choice from 2016, per basket; null = random cell choice each year, B 500): EQ3 OOS -$43/day (year share 36%, p .85); FX2 +$8/day (64%, p .15); CMD4 +$41/day, Sharpe 0.50, 8 of 11 years positive (73%), chosen cell L15 momentum daily in every year, p vs random choice .014 (Bonferroni over the 3 baskets .04; a t-test of the OOS mean against zero is t about 1.6, one-sided p about .05, about .15 over 3 baskets): the WF supports 'CMD4 momentum is better than the average cell', not 'different from zero beyond multiplicity'.
**Post-hoc diagnostic (NOT the frozen screen; selected by max): CMD4 L15 momentum daily, full evaluator** (instr2_eval, run_placebo False, weekly $ at the $1,200/day vol book): L1M +$348/wk, L3M +$592, L6M +$1,029 (maxDD $2.3k), HOLD +$569 (maxDD $9.8k), MID +$637, PRE +$121 (maxDD $17k), X' -$508. Tolerant gate PASSES (NOW-ONLY ok, persistence 87.5%, min sample ok, gate_v2a True), weekly P&L correlation to the NQ stack -0.03 (V0) and -0.01 (V2), stack Calmar L6M 0.736 -> 0.753 at k=1 (HOLD not up, optimum stack weight k* = 0). The neighbours: L5 weekly fails NOW-ONLY (L1M -$192, PRE -$473), FX2 L15 reversal fails (X' -$829). Failed items: family p .88, placebo and own-parameter walk-forward not run by the evaluator.
**Executable lots (CMD4 L15 mom D, integer contracts, 2013-2026 whole sample):** at the 1.0x risk scale the legs average GC 0.4, CL 0.7, ZN 0.6, ZB 0.4 contracts (95th percentile 0.9 / 1.5 / 1.0 / 0.8), i.e. rounding to whole contracts changes the book; rounded contracts at x1: net +$35/day, sd $1,381, Sharpe 0.40, maxDD $61.6k, median margin proxy $9.0k; x2: +$79/day, sd $2.6k, maxDD $89.8k, margin median $24.5k (max $64k); x3: +$130/day, maxDD $148k, margin median $33.5k; x5: +$200/day, maxDD $234k. Margin proxies are stated assumptions (ES 13,000, RTY 7,500, YM 10,500, 6E 3,200, 6J 3,800, GC 12,000, CL 7,000, ZN 2,000, ZB 3,500), unverified. Order types: market orders at 16:56 ET on every leg, roll days market into the new front month.
Label: EQ3 NEGATIVE; FX2 NEGATIVE (15-day weekly reversal fails the gate); CMD4 momentum PER-CELL ONLY / WATCH (diagnostic tolerant pass, NQ-stack corr about 0, but family p .88, 13-year maxDD $62k at 1x, PRE and X' weak: PRE +$121/wk, X' -$508/wk). No PASS claim; nothing live. Ledger T2F_DAILY4_EQ3/FX2/CMD4 (84 rows), n_tested +87 (total 1,935,195 -> see registry).
Code: l2vast/ds3/code/daily4/ (build.py, model.py, run.py, analyze.py, wf.py, evalbook.py, lots.py); series /mnt/l2/l2vast/daily4/.
Z1 DAILY4 correction (2026-11-06): the truncation test required by the prereg was run after the block above was written: weights at 72 random decision days (3 baskets x L 1/5/15 x both directions, data cut at the decision day) are identical to the full-data weights, 72/72; the 'not a separate cut test' limitation in the block is withdrawn.

## CORRECTION and reading notes (S4a, appended; the plain sentence above summarised the walk-forward and the minimum family p loosely)
* Family p among the 36 TOLERANT cells: minimum 0.33 under the random-side null (ES MR_k5_th1.5, z 2.84 vs null maximum median 2.69) and 0.48 under the forward-shift null. The smallest forward-shift p over ALL 408 cells is 0.005 (6E TSMOM_L252_vol, z 3.95) but that cell is not tolerant (positive in 7 of 14 years < 60%), its random-side p is 1.00, its walk-forward p is 0.17 and its pre-2023 record alternates (2014-15 +$50k, 2018 -$18k, 2023 -$16k): exploratory, not a lead. Both nulls must be passed by the prereg.
* Walk-forward (annual refit): 30 of 60 instrument/portfolio x family groups have a positive out-of-sample total; three of those also have p vs random parameter choice <= .10: RTY F5 (night/weekend long, +$28k, p .08, 6 test years), CL F2 Donchian (+$81k, p .06; maxDD OOS $54k) and NKD F1 TSMOM (+$140k, p .04; NKD costs are CAP-BREACH proxies). The tolerant CL cells behind CL F2 (DON_N20_SAR: 13-year +$145k, maxDD $47.8k at 1 lot, 9 of 14 years positive, corr to the NQ stack +0.03, stack Calmar up) have family p 1.00 (random-side) and 0.99 (shift), so they are best-of-F, not leads. WATCH only: CL daily Donchian 20 stop-and-reverse is the one tolerant cell with a stack Calmar gain and a positive walk-forward with p <= .10; it would need a new, separately preregistered confirmation on data not used here (none exists before 2013; forward Shadow only).
* No cell meets the full LEAD rule (tolerant gate, both family p <= .10, walk-forward positive with p <= .10, |corr| <= .3, stack Calmar up). Labels: NULL 283, REGIME 89, best-of-F 36, LEAD 0. The answer to "is there a diversifier at the daily horizon" is no on this evidence; the 13 years are real out-of-sample history, and the strongest-looking items (ES 3-5 day reversal, CL Donchian, GC trend) are inside what random sign draws produce over the 408-cell family.
* Costs are decisive: the one-tick slippage proxy plus fee turns the index-futures night/day leg books and NKD negative; the 1-lot floor makes index lots run above the $1,200 daily-sigma target (larger maxDD than the table's dollar target suggests).

## CHAR-A block (MONDAY follow-up, 2026-11-06T01:44Z): equity-index Monday label day (Sunday 18:00 ET -> 16:55 ET). LABEL: WATCH / REGIME, best-of-F (follow-up to a descriptive hit). Shadow only, no PASS.
Prereg l2vast/ds3/prereg/T_FIND_MONDAY_prereg.md sha256 78e4395266aa7cb52dfa8b9a9209a270b9b9e6e8dfe9b99ace45cb7e94e319b3 (DECISIONS.md, before any follow-up number). Base: label-day bars 2013-2026 percent frame, 1-min approximation; ES NQ YM 2013+, RTY 2017-07+.

### (1) Weekday-label permutation null (paired by week, drift cancels), 2,000 draws; Monday excess over the other days of the same week, bps
| instrument | Monday excess (bps) | z | raw p | p_family JOINT equity family (20 cells, same permutation across the 4 indices) | p_family independent draws (equity 20 / all13 65 cells) |
|--|--|--|--|--|--|
| ES | +8.1 | +1.82 | 0.075 | 0.52 | 0.72 / 0.98 |
| NQ | +12.2 | +2.15 | 0.034 | 0.29 | 0.41 / 0.80 |
| RTY | +19.4 | +2.44 | 0.013 | 0.15 | 0.20 / 0.51 |
| YM | +7.2 | +1.69 | 0.103 | 0.63 | 0.79 / 0.99 |
| 4 indices as ONE bet (equal-notional average) | +9.8 | +2.06 | 0.038 | 0.17 (5-cell combined family) | - |
Control family (GC CL ZN ZB 6E 6J NKD MBT BTC x 5 weekdays, 45 cells): min p_family 0.46; the largest control hits are ZB Monday -7.0 bps (raw p .012), CL Monday -26 bps, MBT Monday +59 bps, BTC Thursday -53 bps, i.e. raw |z| about 2.1-2.4 appear in the controls too. Joint equity-family minimum p is 0.15 (RTY Monday), above the frozen .10.

### (2) Year-by-year Monday excess with 95% week-bootstrap CIs (bps) and the 2023-04-01 break test
* ES: 2013: -10 [-33,+11]; 2014: -13 [-34,+7]; 2015: +8 [-27,+41]; 2016: +2 [-23,+25]; 2017: +4 [-6,+16]; 2018: -16 [-52,+19]; 2019: -13 [-41,+11]; 2020: +54 [-5,+113]; 2021: +8 [-21,+35]; 2022: +1 [-39,+39]; 2023: +19 [-1,+38]; 2024: +6 [-13,+23]; 2025: +27 [-4,+57]; 2026: +38 [+11,+63]
* EQ4: 2013: -12 [-35,+9]; 2014: -13 [-36,+7]; 2015: +10 [-27,+43]; 2016: +3 [-20,+27]; 2017: +6 [-7,+19]; 2018: -18 [-57,+18]; 2019: -13 [-43,+14]; 2020: +69 [+13,+127]; 2021: +7 [-26,+39]; 2022: +5 [-38,+49]; 2023: +18 [-2,+39]; 2024: +9 [-12,+30]; 2025: +25 [-9,+56]; 2026: +40 [+11,+69]
| series | pre-2023 mean | 2023+ mean | Delta | 95% CI of Delta | split-2023 permutation p | sup-|t| over break dates 2016..2025: p |
|--|--|--|--|--|--|--|
| ES | +2.7 | +21.9 | +19.2 | [+3.1, +36.1] | 0.051 | 0.009 |
| NQ | +5.8 | +28.4 | +22.6 | [+0.8, +44.3] | 0.064 | 0.005 |
| RTY | +16.4 | +23.2 | +6.9 | [-21.3, +34.2] | 0.648 | 0.849 |
| YM | +4.0 | +15.6 | +11.6 | [-3.5, +26.9] | 0.216 | 0.023 |
| EQ4 | +4.9 | +22.3 | +17.4 | [-0.1, +33.7] | 0.077 | 0.003 |
Reading: the Monday excess is close to zero before 2023 (ES +2.7, YM +4.0, NQ +5.8 bps; RTY +16 but only from 2017-07) and +16..+28 bps from 2023; the break is supported for ES / NQ / YM / the 4-index average (sup-t permutation p .003-.023, split p .05-.08, Delta CIs mostly above 0) but not for RTY (already +16 before). Year by year only 2020 (ES +54, CI [-5,+113]; 4-index +69, CI [13,127]) and 2026 (ES +38, CI [11,63]) have CIs excluding zero; 2023-25 point estimates are +6..+27 with CIs that include zero. This is a level shift that coincides with the 2023+ regime of strong weekend/Sunday-open drift, not a stable 13-year anomaly; it cannot be separated from the NQ-stack's own 2023+ regime.

### (3) Exact tradable definition (long Monday, market order at the leg start and end; ES-class = 1 contract; micro = 1 MES-class contract with the $1.28 published fee, proxy for the other micros)
| index | leg | Monday mean bps | excess bps (t) | years positive | pre-2023 / 2023+ bps | cost bps (1 contract) | net $/trade 1 contract (2023+ only) | net $/trade 1 micro |
|--|--|--|--|--|--|--|--|--|
| ES | FULL | +12.7 | +8.1 (1.9) | 0.79 | +8.5 / +24.5 | 1.4 | +330 (+677) | +32 |
| ES | RTH | +4.7 | +3.4 (1.1) | 0.71 | +1.0 / +15.0 | 1.4 | +95 (+398) | +9 |
| ES | SUNNIGHT | +2.9 | +1.7 (0.9) | 0.64 | +3.0 / +2.4 | 1.4 | +42 (+29) | +3 |
| ES | ASIALON | +6.9 | +4.3 (1.6) | 0.86 | +6.0 / +9.3 | 1.4 | +159 (+230) | +15 |
| ES | H4 | +2.2 | +2.0 (1.3) | 0.71 | +1.9 / +3.2 | 1.4 | +23 (+51) | +2 |
| ES | POST | +1.2 | +0.4 (0.8) | 0.79 | +1.5 / +0.2 | 1.4 | -9 (-36) | -2 |
| NQ | FULL | +17.5 | +12.2 (2.3) | 0.79 | +12.1 / +32.5 | 1.1 | +678 (+1297) | +67 |
| NQ | RTH | +9.0 | +8.4 (2.1) | 0.79 | +4.9 / +20.6 | 1.1 | +328 (+806) | +32 |
| NQ | SUNNIGHT | +3.6 | +1.6 (0.7) | 0.64 | +3.8 / +3.2 | 1.1 | +105 (+87) | +10 |
| NQ | ASIALON | +6.7 | +3.4 (1.1) | 0.71 | +5.0 / +11.4 | 1.1 | +230 (+424) | +22 |
| NQ | H4 | +3.2 | +2.3 (1.3) | 0.57 | +2.7 / +4.7 | 1.1 | +88 (+147) | +8 |
| NQ | POST | +1.8 | +0.4 (0.7) | 0.71 | +2.3 / +0.5 | 1.1 | +31 (-23) | +2 |
| RTY | FULL | +21.2 | +19.4 (2.6) | 0.78 | +17.9 / +25.9 | 1.8 | +214 (+266) | +21 |
| RTY | RTH | +5.0 | +7.5 (1.2) | 0.56 | -0.2 / +12.5 | 1.8 | +35 (+119) | +3 |
| RTY | SUNNIGHT | +4.1 | +2.6 (0.7) | 0.56 | +6.2 / +1.0 | 1.8 | +25 (-9) | +2 |
| RTY | ASIALON | +13.8 | +10.2 (2.2) | 0.78 | +15.1 / +12.1 | 1.8 | +133 (+114) | +13 |
| RTY | H4 | +3.1 | +2.5 (0.9) | 0.67 | +3.8 / +2.1 | 1.8 | +15 (+4) | +1 |
| RTY | POST | +2.3 | +1.7 (1.9) | 0.89 | +3.0 / +1.3 | 1.8 | +6 (-6) | -0 |
| YM | FULL | +11.6 | +7.2 (1.7) | 0.71 | +9.9 / +16.6 | 0.9 | +228 (+334) | +22 |
| YM | RTH | +4.5 | +3.6 (1.2) | 0.64 | +2.9 / +9.1 | 0.9 | +76 (+174) | +7 |
| YM | SUNNIGHT | +2.2 | +0.9 (0.5) | 0.50 | +2.9 / +0.4 | 0.9 | +27 (-12) | +2 |
| YM | ASIALON | +5.7 | +3.4 (1.3) | 0.79 | +5.2 / +7.1 | 0.9 | +101 (+131) | +9 |
| YM | H4 | +1.9 | +1.6 (1.1) | 0.71 | +2.4 / +0.7 | 0.9 | +21 (-5) | +1 |
| YM | POST | +1.4 | +0.3 (0.5) | 0.86 | +1.8 / +0.4 | 0.9 | +10 (-12) | +0 |
Reading: the FULL leg (Sunday 18:00 open to the 16:55 flat) is the only one worth its cost (ES +12.7 bps raw, +11.3 net of 1.4 bps; the first 1-4 hours and the post-RTH close do not cover cost); the money is spread over the Asia/London part (+6.9 bps raw, ES excess t 1.6) and RTH (+4.7), not in the thin first hours. Execution: market order at 17:59-18:00 Sunday (thin-book open, wider spread than assumed: INSTR2_SESSIONS rates asia ILLIQUID for ES/RTY/YM) and market exit at 16:55; one position, no stop in the leg definition (a protective stop would be a separate variant). A micro earns about a tenth: $20-30 per trade after the $1.28 fee.

### (4)+(5) Overlap with the live NQ stack and the 4 indices as one bet (descriptive instr2_eval, $1,200 scale, carry weeks dropped; NOT eligible under the frozen rule)
| book | L1M | L3M | L6M | HOLD | MID | PRE | X' | HOLD maxDD | corr to stack daily / Mondays-only | weekly corr V0 / V2 | stack dCalmar at k* HOLD / L6M | tolerant gate | walk-forward 6m / 12m |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ES Monday FULL | +78 | -54 | +139 | +256 | +485 | +89 | +209 | 801 | +0.03 / +0.05 | -0.02 / -0.05 | +0.036 / +0.012 | False | +53 (True) / +59 (True) |
| NQ Monday FULL | +9 | -128 | +139 | +238 | +420 | +95 | +191 | 687 | +0.06 / +0.12 | +0.02 / -0.01 | +0.036 / +0.012 | False | +28 (True) / +71 (True) |
| RTY Monday FULL | +35 | -70 | +47 | +172 | +467 | +55 | +199 | 1229 | +0.01 / +0.01 | -0.08 / -0.11 | +0.025 / +0.004 | False | +59 (True) / +67 (True) |
| YM Monday FULL | +91 | -13 | +98 | +161 | +382 | +47 | +224 | 2156 | +0.02 / +0.03 | -0.04 / -0.06 | +0.029 / +0.008 | False | +6 (True) / +31 (True) |
| EQ4 Monday FULL | +53 | -67 | +106 | +207 | +438 | +72 | +206 | 1080 | +0.03 / +0.06 | -0.03 / -0.06 | +0.032 / +0.009 | False | +53 (True) / +59 (True) |
The live stack already earns on Mondays (V2 mean $3.3k/day on Mondays vs $3.5k Tue, $0.8k Wed, $2.5k Thu, $3.0k Fri since 2023-04) but the Monday index-long book is uncorrelated with it (daily corr +0.01..+0.06, Monday-only +0.01..+0.12, weekly -0.11..+0.02), so the Sunday-night overlap is not a correlation problem; the equal-risk stack Calmar gain at k*=5 is small and positive (HOLD +0.025..+0.036, L6M +0.004..+0.012). The 4 indices are one bet: the average has the same Monday excess (+9.8 bps, z 2.1, p .04 raw / .18 combined-family) and a slightly better HOLD maxDD per $ than RTY or YM alone; ES alone carries most of the signal at the lowest cost.
Verdict by the frozen rule: weekday-permutation joint family p = .15 (RTY) to .63 > .10, tolerant gate FAILS (L3M negative), walk-forward positive (6m / 12m, legs as variants) -> WATCH / REGIME (best-of-F of 130 seasonality cells, 2023+ level shift, correlated indices). Not eligible for the full evaluator; no live use.

# ZL-2 block: T2F_DAILY3 - vol-regime books (Block C) and stack-regime detection (Block D) (2026-11-06T01:44Z)
Prereg: l2vast/ds3/prereg/T2F_DAILY3_zl2_prereg.md sha256 ffd01e8b92cab06d13f8f1103b49c44a0aa77ba071946880ea817c1b094d2fa0 (filed before any number; Block C = CHAR-A Block C verbatim, Block D widened). n_tested 684 (156 + 2 bases x 264). Data: cache_te2 1-min .v.0, multiplicative roll adjustment, label days, through 2026-10-16. Prior cited, not repeated: WHAT_IS_DEAD F12 (R_F40 lag 29 d, break-even OFF stretch > 178 d; DIS-U one mean shift; Q8 AUC .56; ERA_2023 no state variable explains 2023-26).

## Plain sentences
**Block C (vol-regime books): no vol band makes a daily trend or reversal book pay.** Of 156 cells (13 instruments x trend20 / rev5 x 6 vol bands) 29 have a positive net mean, 7 have a raw shuffled-position p <= .05 (about 8 expected by chance), none has a family p <= .10 (best .69), 0 pass the frozen screen. **Block D (stack-regime detection): none of 132 features x direction x threshold rules (x2 scales) predicts the next week of the live-stack object out of sample in 2023-04..2026-10 (family p >= .97 on V0 and V2); the pre-2023 descriptive period shows a few rules with family p <= .10 (NQ VR(5) high, 6E range percentile high, NQ-RTY correlation high, ZN trend persistence high) that do not carry into 2023-26.** Detection lag stated: one week (Friday-close features, applied from Monday); the trailing-P&L features lag by their window (4/8/13 weeks).

## Block C detail
- cells 156: mean net > 0 in 29; p_raw <= .05 in 7; p_family <= .10 in 0; frozen survivors (p_family <= .10, mean > 0, year-sign share >= .6): 0.
- Look-ahead control: my first run of this block shifted the position by zero days instead of one (signal at the close of t earned the return of day t). That run showed 72 "survivors" with z up to 9.4, i.e. the screening detects a one-day look-ahead; it was found by comparing the conditional next-day return table with the book P&L, fixed (position now earns day t+1 open->close), and ALL numbers here are from the fixed run. Truncation of the features: 0 failures in 8 cut checks.

Best 8 cells by family p:

| instrument | signal | band | active days | mean net \$/day | z | p_family | p_raw | years positive | total \$ |
|--|--|--|--|--|--|--|--|--|--|
| GC | rev5 | rv67-100 | 1041 | +14.2 | 2.44 | 0.687 | 0.008 | 0.57 | 50,897 |
| MBT | rev5 | rv67-100 | 290 | +24.8 | 2.39 | 0.729 | 0.024 | 1.00 | 26,452 |
| ZN | rev5 | rv33-67 | 1151 | -23.7 | 2.21 | 0.868 | 0.022 | 0.21 | -89,551 |
| BTC | rev5 | rv67-100 | 296 | +25.3 | 2.20 | 0.874 | 0.028 | 1.00 | 27,875 |
| GC | trend20 | rv0-33 | 1210 | +13.7 | 2.10 | 0.942 | 0.018 | 0.71 | 44,143 |
| GC | trend20 | vov<50 | 1777 | +14.6 | 1.95 | 0.990 | 0.026 | 0.79 | 39,919 |
| NQ | trend20 | vov<50 | 1665 | +1.3 | -0.37 | 1.000 | 0.639 | 0.64 | 12,894 |
| NQ | trend20 | rv33-67 | 1076 | +6.4 | 0.29 | 1.000 | 0.395 | 0.57 | 21,079 |

## Block D detail
Target: weekly P&L of the 14-cell live-stack object (DS3_NQ13 object, bracket 60/60, percent frame); E1 = 2023-04..2026-10-16 on the 1-s object (146 evaluated weeks after dropping the carrying weeks), formal; E2 = 2014-01..2023-03 on the 1-min object (483 weeks), descriptive (calibration < .90). Statistic A = P&L avoided by zeroing flagged weeks (scale 0.5 gives half), WY max over 132 rules per base, 1,000 shuffled-week feature worlds.

- V0: E1 rules with A > 0: 26 of 132; min family p 0.984; rules with family p <= .10: 0; best raw p 0.044. E2 (descriptive): rules with family p <= .10: 3.
- V2: E1 rules with A > 0: 13 of 132; min family p 0.976; rules with family p <= .10: 0; best raw p 0.044. E2 (descriptive): rules with family p <= .10: 6.

Top 5 E1 rules by raw p (V0 and V2), with the E2 value:

| base | feature | dir | tail | E1 A (s=0) \$ | E1 flagged share | E1 family p | E1 raw p | E2 A \$ | E2 family p |
|--|--|--|--|--|--|--|--|--|--|
| V0 | corrNQ_GC | high | terc | 89,583 | 0.26 | 0.984 | 0.044 | 383,778 | 1.000 |
| V0 | GC_rng5pct | low | terc | 76,505 | 0.20 | 0.998 | 0.058 | 74,447 | 1.000 |
| V0 | ZN_rv20pct | low | terc | 50,229 | 0.36 | 1.000 | 0.086 | 488,965 | 1.000 |
| V0 | NQ_rng5pct | low | quint | 71,131 | 0.21 | 1.000 | 0.087 | 125,435 | 1.000 |
| V0 | ZN_er20 | high | terc | 55,069 | 0.31 | 1.000 | 0.094 | 1,106,736 | 0.124 |
| V2 | RTY_er20 | low | quint | 76,017 | 0.20 | 0.976 | 0.044 | 218,846 | 1.000 |
| V2 | GC_rng5pct | low | terc | 26,397 | 0.20 | 0.992 | 0.051 | -89,623 | 1.000 |
| V2 | NQ_er20 | high | quint | 39,082 | 0.23 | 0.998 | 0.082 | 386,744 | 1.000 |
| V2 | ES_vr5 | high | terc | 13,662 | 0.35 | 0.999 | 0.083 | 808,589 | 0.825 |
| V2 | ZN_er20 | high | terc | 3,424 | 0.31 | 0.999 | 0.086 | 1,043,459 | 0.052 |

E2 rules with family p <= .10 (descriptive) and what they do in E1:

| base | feature | dir | tail | E2 A \$ | E2 family p | E1 A \$ | E1 raw p |
|--|--|--|--|--|--|--|--|
| V2 | corrNQ_RTY | high | quint | 738,729 | 0.004 | -240,601 | 0.988 |
| V0 | NQ_vr5 | high | terc | 1,232,035 | 0.005 | -60,291 | 0.381 |
| V0 | corrNQ_RTY | high | quint | 747,870 | 0.008 | -212,321 | 0.989 |
| V2 | NQ_vr5 | high | terc | 1,145,461 | 0.017 | -117,051 | 0.449 |
| V2 | 6E_rng5pct | high | quint | 796,750 | 0.036 | 18,943 | 0.124 |
| V2 | corrNQ_RTY | high | terc | 845,190 | 0.037 | -97,857 | 0.509 |
| V2 | ZN_er20 | high | terc | 1,043,459 | 0.052 | 3,424 | 0.086 |
| V0 | 6E_rng5pct | high | quint | 887,117 | 0.057 | -11,070 | 0.313 |
| V2 | ZN_er20 | high | quint | 757,316 | 0.086 | 41,016 | 0.087 |

Reading: the E2 rules flag weeks of a stack object that LOST money on average before 2023 (-\$3.1k/wk), so any rule that flags a third of weeks avoids loss; the shuffled-week null accounts for this, and a handful survive it, but the same rules have A <= 0 or raw p > .3 in the formal 2023-26 period. No rule is a lead: the frozen rule needs E1 family p <= .10, A > 0 in E1, A >= 0 in E2 and a flagged share between 5% and 50%; 0 rules pass on either base. Caveats: object not engine; the stack target is the plain-signal object (calibration .90 on 7 of 14 pairs); 146 E1 weeks give wide uncertainty; features are daily/weekly and cover NQ, ES, RTY, 6E, GC, ZN only; the stack object was chosen with hindsight on 2023-26. Never up-size: scales 0.5 and 0 only; the engine core series (bj_out) sensitivity was not run because no rule reached the sensitivity stage.

Precision (ZL-2, same block): the sentence 'the same rules have A <= 0 or raw p > .3 in 2023-26' is true for NQ VR(5) high (E1 A -\$60k V0 / -\$117k V2), 6E range percentile high (-\$11k V0, +\$19k V2 with raw p .12) and NQ-RTY correlation high (-\$212k / -\$98k / -\$241k), but NOT for ZN trend persistence high (V2): E1 A +\$3.4k (tercile) and +\$41k (quintile), flagged share 0.31 / 0.15, raw p .086 / .087, E1 family p >= .97. That rule has a mild same-sign echo in the formal period and is a WATCH item only (best-of-264, one rule, no mechanism, the stack object chosen with hindsight).


## FOLLOW-UP STRESS of the CL Donchian-20 stop-and-reverse cell (and a lighter one for RTY night/weekend long and NKD momentum) - S4a, 2026-11-06
Prereg l2vast/ds3/prereg/FIND_DAILY_CL_STRESS_prereg.md sha256 2c0008b7988dc46cda4511746e581c4fe6311ea36bbbd95fe78ea4b5562c7dd9 (filed before any statistic; follow-up on a BEST-OF-F cell: it cannot make a LEAD, only decide the watch list). Code l2vast/ds3/code/t2s4a/cl_stress.py, results /mnt/l2/l2vast/ds3_daily/cl_stress.pkl. (An early run of the surface had a coding bug in the stop-and-reverse branch; it was caught because the cell did not reproduce $145,271 / maxDD $47,782, fixed and rerun before anything was written; only the corrected numbers appear here.)
**Plain sentence: the CL cell is not on a plateau - only 3 of the 8 stop-and-reverse lengths have a positive 13-year total with Calmar >= 0.10 (needed 6), the profit is a narrow ridge at N = 15-30 that fades beyond N = 40 and no volatility filter helps; 89% of the net comes from its 3 best trades and 86% from 3 years (2026, 2020, 2022), the other 71 trades together made +$15.9k; it is ~$10k a year at about 1.1 lots (maxDD $47.8k, Calmar 0.22), 0.7% of the live stack's HOLD weekly mean at 1 lot and about 3% at the 4 lots the stack could absorb, and vol-targeting does not improve the Calmar (0.13-0.17 at 2-5 lots). It stays a best-of-F cell: a Shadow-only forward watch is specified (WATCH_CL_DONCHIAN_SPEC.md) that can kill it but cannot confirm it (about 50 years of data would be needed to separate $10k a year from zero at this volatility).**
### S1 plateau surface (Calmar = annual mean / maxDD, 13 years, 1.1 lots average; rows N, columns exit rule)
No filter:
| N | SAR | N/4 | N/2 | N |
|--|--|--|--|--|
| 10 | 0.04 | 0.00 | 0.02 | 0.01 |
| 15 | 0.13 | 0.08 | 0.09 | 0.11 |
| 20 | 0.22 | 0.11 | 0.07 | 0.18 |
| 30 | 0.12 | 0.19 | 0.15 | 0.15 |
| 40 | 0.08 | 0.08 | 0.13 | 0.05 |
| 60 | 0.02 | 0.06 | 0.07 | -0.01 |
| 80 | -0.01 | 0.03 | 0.02 | 0.01 |
| 100 | 0.01 | 0.04 | 0.02 | 0.01 |
No filter, 13-year net total ($):
| N | SAR | N/4 | N/2 | N |
|--|--|--|--|--|
| 10 | 59452 | 4322 | 37589 | 17797 |
| 15 | 140063 | 94069 | 114839 | 100278 |
| 20 | 145271 | 111923 | 76692 | 127010 |
| 30 | 119866 | 111149 | 100686 | 103250 |
| 40 | 82103 | 71281 | 79213 | 56948 |
| 60 | 22291 | 56521 | 57678 | -14232 |
| 80 | -11580 | 32806 | 28108 | 9948 |
| 100 | 23249 | 53235 | 27834 | 16423 |
Low-vol entries only (Calmar):
| N | SAR | N/4 | N/2 | N |
|--|--|--|--|--|
| 10 | -0.05 | 0.02 | 0.02 | -0.03 |
| 15 | -0.02 | 0.04 | -0.00 | 0.05 |
| 20 | 0.03 | 0.05 | -0.00 | 0.11 |
| 30 | 0.05 | 0.01 | 0.15 | 0.17 |
| 40 | 0.00 | -0.02 | 0.10 | 0.06 |
| 60 | 0.00 | 0.04 | 0.12 | 0.02 |
| 80 | -0.00 | 0.04 | 0.03 | 0.02 |
| 100 | -0.03 | 0.02 | 0.01 | -0.01 |
High-vol entries only (Calmar):
| N | SAR | N/4 | N/2 | N |
|--|--|--|--|--|
| 10 | -0.00 | -0.02 | 0.00 | 0.07 |
| 15 | 0.04 | 0.07 | 0.16 | 0.10 |
| 20 | 0.00 | 0.07 | 0.08 | 0.11 |
| 30 | -0.03 | 0.13 | 0.08 | 0.01 |
| 40 | 0.01 | 0.10 | 0.11 | 0.02 |
| 60 | -0.01 | 0.11 | 0.05 | 0.00 |
| 80 | -0.01 | 0.07 | 0.02 | 0.02 |
| 100 | 0.07 | 0.11 | 0.07 | 0.10 |
Plateau rule (prereg): (a) SAR/no-filter N values with total > 0 and Calmar >= .10: 3 of 8 -> FAIL (needs 6); (b) median neighbour Calmar 0.114 vs 50% of the cell's 0.108 -> pass. Both are required: **no plateau, single ridge N 15-30.**
### S2 April 2020 and rolls
* The volume-front CL series never contains a negative price: minimum raw price in the series 12.64. On 2020-04-20 the volume-front moved from the May contract (last close 17.18 on 04-17) to June (raw 21.00 at 15:55 on 04-20); the May contract's -$37 settlement on that day is not in the series. The 2020-04-21 -36% day is the June contract's genuine fall (13.47 from 21.00). Adjusted daily returns range -35.9% .. +23.6%, no day with P <= 0.
* Percent-frame identity: on every non-roll day the cell's P&L per lot equals pv x raw price change (max absolute difference $0.00), so the multiplicative frame changes only roll-day bridging and sizing, not P&L.
* Roll lags: the volume-front switches a median of 1 business day (153 of 165 rolls within 2 business days) before the approximate monthly expiry, i.e. later than a trader would roll; the spec uses a calendar roll (below). The cell was SHORT through April 2020 (best trade 2020-01-13 to 2020-05-15, +$48.1k), so the missing May settlement is neither a hidden gain nor a hidden loss in the series.
* **Excluding 2020 (all 2020 P&L set to zero): total $97,805 (was $145,271), maxDD unchanged $47,782, Calmar 0.15 (was 0.22).**
### S3 concentration
Per-year net ($ thousand, 1 lot):
| 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 7.7 | 29.0 | 5.1 | -8.0 | -3.7 | 9.6 | -18.0 | 47.5 | 0.1 | 29.8 | 9.3 | -5.1 | -6.1 | 48.1 |
| regime | net $ | maxDD $ | years positive |
|--|--|--|--|
| 2013-16 | 33,823 | 24,410 | 3/4 |
| 2017-19 | -12,150 | 37,616 | 1/3 |
| 2020-22 | 77,356 | 29,130 | 3/3 |
| 2023-26 | 46,241 | 32,411 | 2/4 |
Trades: 74 episodes, win rate 41%, average $1,965. Top 3 trades: 20200113 to 20200515 short $48,081, 20140709 to 20150203 short $48,039, 20220106 to 20220622 long $33,416 = $129,536 = 89% of net; the other 71 trades sum to $15,859. Top 3 years = 86% of net (2026 48,126, 2020 47,465, 2022 29,822).
### S4 dollars, lots, margin, live stack
At 1.1 average lots (max 2): $10,321 a year, daily-P&L sigma $26,761 a year, maxDD $47,782, Calmar 0.22. Notional per lot $12,640 to $124,040 (median $66,700); margin is not in the repository: a PROXY of 8-10% of notional is $5-7k per lot (check the broker schedule; overnight margin applies because positions are held for days). Live stack V2 HOLD (carry weeks dropped): $28,158 a week mean, maxDD $91,168; the CL cell at 1 lot: $1,139 a week in HOLD (2026 was its best year), $198 a week over 13 years; weekly corr to the stack +0.03; the stack can absorb k* = 4.0 lots before its HOLD maxDD rises, with a Calmar gain of +0.052 (HOLD) / +0.020 (L6M): +$4,517 a week in HOLD. Plainly: at 1 lot it is immaterial next to the stack (about 1% of its weekly mean), at the 4 lots the stack could absorb it is a few percent; it is a diversifying drip, not a book that carries weight.
Vol-targeted versions (lots = round(T / daily $ sigma), floor 1, cap 6):
| target T | 13y net $ | maxDD $ | Calmar | mean lots |
|--|--|--|--|--|
| base(1200, floor 1) | 145,271 | 47,782 | 0.22 | 1.10 |
| 1200 | 145,271 | 47,782 | 0.22 | 1.10 |
| 2400 | 204,260 | 114,821 | 0.13 | 2.05 |
| 4000 | 334,118 | 180,030 | 0.13 | 3.37 |
| 6000 | 550,880 | 235,319 | 0.17 | 4.75 |
| fixed 1 lot | 132,164 | 42,947 | 0.22 | 1.00 |
Vol targeting does not fix it: scaling the lots up raises the net but the Calmar falls from 0.22 to 0.13-0.17 (the cell's profits arrive in low-vol-lot periods; more lots in high-vol periods add drawdown). Calmar is the quantity to look at; a uniform lot multiple leaves it unchanged.
### Light stress: other two walk-forward p <= .10 groups (same code; no new tests)
| book | net $ | maxDD $ | Calmar | years + | ex-2020 net | ex-2020 Calmar | 2013-16 | 2017-19 | 2020-22 | 2023-26 | top-3-year share | mean lots | notional/lot |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| CL DON_N20_SAR | 145,271 | 47,782 | 0.22 | 9/14 | 97,805 | 0.15 | 33,823 | -12,150 | 77,356 | 46,241 | 0.86 | 1.08 | 66,700 |
| RTY NIGHT_L | 67,037 | 30,912 | 0.23 | 7/10 | 52,450 | 0.18 | 0 | 24,311 | 24,341 | 18,385 | 0.80 | 1.24 | 94,265 |
| RTY WKND_L | 27,739 | 15,544 | 0.19 | 7/10 | 21,283 | 0.16 | 0 | 7,568 | 5,050 | 15,122 | 0.76 | 0.25 | 94,265 |
| NKD TSMOM_L252_1lot | 141,313 | 66,522 | 0.15 | 8/14 | 146,829 | 0.18 | -23,150 | 3,789 | -1,266 | 161,940 | 0.98 | 0.93 | 113,675 |
| NKD TSMOM_L252_vol | 167,025 | 60,982 | 0.19 | 8/14 | 172,541 | 0.20 | -22,322 | 28,673 | -1,266 | 161,940 | 0.84 | 1.04 | 113,675 |
NKD momentum neighbours (vol-scaled lots): L=126: $-26,206, maxDD $176,428, Calmar -0.01, 6/14; L=189: $187,259, maxDD $95,330, Calmar 0.14, 10/14; L=252: $167,025, maxDD $60,982, Calmar 0.19, 8/14; L=315: $65,035, maxDD $83,697, Calmar 0.06, 8/14.
Reading: RTY night/weekend long is the equity overnight drift (long beta, 10 years of data, 2017 on, mostly in a rising market, 80% of the profit in 3 years; label TREND-BETA, not a diversifier of the NQ book in return terms even though the weekly correlation to the stack is +0.06); NKD momentum is entirely 2023-26 (2013-22 is negative or flat), only L = 189-252 works (L = 126 loses 26k), and its costs are CAP-BREACH proxies: REGIME. Only the CL cell is carried to the watch list, as best-of-F with the caveats above.
Note (appended): the sentence "the cell's profits arrive in low-vol-lot periods" in the vol-target paragraph is an untested explanation, not a result; the result is only the Calmar table (0.22 at fixed 1 lot or the base sizing, 0.13-0.17 at 2-5 lots).

## CHAR-A block (MONDAY diagnosis + watch, 2026-11-06T01:47Z): where does the 2023+ level shift of the equity Monday sit? Shadow only.
Forward watch frozen in autopilot/WATCH_MONDAY_LONG_SPEC.md (sha256 in DECISIONS.md); log script code/find/monday_watch_log.py (week 1 = Monday 2026-11-09; the forward NQ feed ends 2026-11-05 today, so no week-1 row exists yet; Monday 2026-11-02, already in the feed, was NQ -132 bps FULL and is excluded as pre-spec).

### Decomposition of the Monday excess (vs Tue-Fri of the same week, bps) by leg; ex-top5 = without the 5 weeks with the largest Monday excess; ex-2020 / ex-2026 = without that year
| index | leg | excess all (t) | pre-2023 | 2023+ | ex-top5 (2023+ ex-top5) | ex-2020 | ex-2026 | ex-2020 and 2026 | top-5 weeks' share of total |
|--|--|--|--|--|--|--|--|--|--|
| ES | SunEve 18-20h | +1.0 (0.9) | +0.5 | +2.4 | +0.3 (+1.9) | +1.4 | +1.0 | +1.4 | 0.70 |
| ES | Asia 20-02h | +0.7 (0.5) | +1.3 | -0.8 | -0.8 (-0.8) | -1.0 | +0.5 | -1.3 | 2.16 |
| ES | London 02-08:30 | +3.4 (1.8) | +2.5 | +5.7 | +1.2 (+3.6) | +2.3 | +2.7 | +1.4 | 0.65 |
| ES | Pre 08:30-09:30 | -0.9 (-0.8) | -1.0 | -0.5 | -1.7 (-0.5) | -0.1 | -1.0 | -0.3 | -0.90 |
| ES | RTH 09:30-16:00 | +3.4 (1.1) | -1.1 | +15.0 | +1.2 (+15.0) | +1.5 | +2.5 | +0.4 | 0.65 |
| ES | Post 16:00-16:55 | +0.4 (0.8) | +0.5 | +0.1 | -0.0 (-0.8) | +0.4 | +0.5 | +0.5 | 1.05 |
| ES | FULL | +8.1 (1.9) | +2.7 | +21.9 | +4.5 (+20.3) | +4.5 | +6.2 | +2.2 | 0.45 |
| NQ | SunEve 18-20h | +1.3 (0.9) | +0.3 | +3.8 | +0.5 (+3.2) | +1.6 | +0.9 | +1.2 | 0.65 |
| NQ | Asia 20-02h | +0.2 (0.1) | +1.0 | -1.6 | -1.4 (-2.4) | -1.6 | +0.2 | -1.9 | 6.43 |
| NQ | London 02-08:30 | +2.1 (1.0) | +0.3 | +6.7 | -0.1 (+2.5) | +1.6 | +1.2 | +0.5 | 1.03 |
| NQ | Pre 08:30-09:30 | -0.3 (-0.3) | -0.2 | -0.7 | -1.2 (-0.7) | +0.2 | -0.6 | -0.0 | -2.57 |
| NQ | RTH 09:30-16:00 | +8.4 (2.1) | +3.6 | +20.5 | +6.0 (+20.5) | +4.6 | +7.5 | +3.4 | 0.30 |
| NQ | Post 16:00-16:55 | +0.4 (0.7) | +0.7 | -0.3 | -0.0 (-1.4) | +0.4 | +0.7 | +0.6 | 1.10 |
| NQ | FULL | +12.2 (2.3) | +5.8 | +28.4 | +8.2 (+28.4) | +6.8 | +9.8 | +3.8 | 0.33 |
| RTY | SunEve 18-20h | +1.5 (0.7) | +1.1 | +2.0 | -0.2 (+1.4) | +2.0 | +1.8 | +2.4 | 1.11 |
| RTY | Asia 20-02h | +1.1 (0.4) | +3.1 | -1.5 | -2.1 (-1.5) | -3.6 | +0.7 | -4.5 | 2.99 |
| RTY | London 02-08:30 | +9.3 (2.3) | +7.4 | +11.8 | +3.8 (+8.8) | +6.7 | +7.6 | +4.5 | 0.59 |
| RTY | Pre 08:30-09:30 | -1.7 (-0.8) | -1.0 | -2.7 | -3.1 (-2.7) | +0.3 | -1.6 | +0.7 | -0.80 |
| RTY | RTH 09:30-16:00 | +7.5 (1.2) | +3.8 | +12.3 | +2.4 (+12.3) | +2.5 | +6.5 | +0.7 | 0.68 |
| RTY | Post 16:00-16:55 | +1.7 (1.9) | +2.0 | +1.3 | +0.9 (-0.2) | +1.6 | +2.0 | +1.9 | 0.49 |
| RTY | FULL | +19.4 (2.6) | +16.4 | +23.2 | +13.3 (+23.2) | +9.6 | +17.0 | +5.7 | 0.32 |
| YM | SunEve 18-20h | +1.0 (0.8) | +0.9 | +1.2 | +0.3 (+1.2) | +1.4 | +1.2 | +1.7 | 0.73 |
| YM | Asia 20-02h | -0.1 (-0.1) | +0.3 | -1.0 | -1.7 (-1.0) | -1.7 | -0.3 | -2.0 | -22.13 |
| YM | London 02-08:30 | +3.7 (1.9) | +2.5 | +7.0 | +1.4 (+5.8) | +2.7 | +3.0 | +1.8 | 0.64 |
| YM | Pre 08:30-09:30 | -1.3 (-1.2) | -1.5 | -0.6 | -2.0 (-0.6) | -0.4 | -1.4 | -0.5 | -0.58 |
| YM | RTH 09:30-16:00 | +3.6 (1.2) | +1.8 | +8.3 | +1.1 (+8.3) | +0.9 | +2.8 | -0.1 | 0.70 |
| YM | Post 16:00-16:55 | +0.3 (0.5) | +0.1 | +0.6 | -0.1 (-0.2) | +0.2 | +0.3 | +0.3 | 1.44 |
| YM | FULL | +7.2 (1.7) | +4.0 | +15.6 | +3.5 (+13.7) | +3.2 | +5.6 | +1.1 | 0.53 |

### Weekend gap / Friday effect (Monday FULL return on the Sunday-open gap vs the previous 16:55 close and on Friday's FULL return, bps)
| index | era | n | Monday mean | beta on gap (t) | beta on Friday return (t) | mean after gap down / up | mean after Friday down / up |
|--|--|--|--|--|--|--|--|
| ES | all | 684 | +13.8 | -0.42 (-4.0) | +0.02 (0.6) | +13.7 / +13.8 | +11.9 / +15.4 |
| ES | pre2023 | 503 | +9.4 | -0.44 (-3.2) | +0.07 (1.5) | +8.3 / +10.4 | +3.7 / +14.2 |
| ES | 2023+ | 181 | +26.1 | -0.36 (-2.6) | -0.13 (-2.5) | +31.1 / +22.2 | +34.6 / +18.9 |
| NQ | all | 674 | +18.4 | -0.41 (-3.1) | +0.03 (0.9) | +13.0 / +23.5 | +15.1 / +21.3 |
| NQ | pre2023 | 493 | +12.6 | -0.46 (-2.5) | +0.10 (2.2) | +4.5 / +21.3 | +4.7 / +19.7 |
| NQ | 2023+ | 181 | +34.1 | -0.32 (-1.9) | -0.15 (-2.6) | +42.3 / +28.5 | +44.5 / +25.3 |
| RTY | all | 424 | +24.0 | -0.64 (-4.2) | -0.01 (-0.3) | +25.5 / +22.6 | +29.4 / +19.0 |
| RTY | pre2023 | 249 | +21.2 | -0.74 (-2.9) | +0.02 (0.3) | +15.5 / +27.0 | +18.7 / +23.6 |
| RTY | 2023+ | 175 | +28.0 | -0.54 (-3.4) | -0.06 (-1.1) | +40.4 / +16.6 | +44.5 / +12.5 |
| YM | all | 676 | +13.1 | -0.29 (-2.2) | -0.03 (-0.9) | +10.8 / +15.2 | +14.9 / +11.6 |
| YM | pre2023 | 497 | +11.1 | -0.23 (-1.4) | +0.00 (0.0) | +5.3 / +17.0 | +9.5 / +12.4 |
| YM | 2023+ | 179 | +18.6 | -0.43 (-2.5) | -0.15 (-2.7) | +28.3 / +11.0 | +30.5 / +9.5 |

### Tail table: ten worst Monday FULL legs, long 1 contract / 1 micro, no stop (bps and $ at that day's price)
* ES: 20200309: -644 bps = $-8,810 (1 ES) / $-881 (1 micro), weekend gap -151; 20180205: -501 bps = $-6,570 (1 ES) / $-657 (1 micro), weekend gap +2; 20150824: -450 bps = $-4,228 (1 ES) / $-423 (1 micro), weekend gap -25; 20190805: -367 bps = $-5,179 (1 ES) / $-518 (1 micro), weekend gap -17; 20220613: -303 bps = $-5,688 (1 ES) / $-569 (1 micro), weekend gap -89; 20220307: -287 bps = $-6,013 (1 ES) / $-601 (1 micro), weekend gap -25; 20181224: -276 bps = $-3,230 (1 ES) / $-323 (1 micro), weekend gap -51; 20130415: -254 bps = $-1,962 (1 ES) / $-196 (1 micro), weekend gap +0; 20200224: -245 bps = $-3,951 (1 ES) / $-395 (1 micro), weekend gap -88; 20220509: -241 bps = $-4,804 (1 ES) / $-480 (1 micro), weekend gap -66
* NQ: 20200309: -558 bps = $-8,829 (1 NQ) / $-883 (1 micro), weekend gap -154; 20190805: -446 bps = $-6,576 (1 NQ) / $-658 (1 micro), weekend gap -6; 20180205: -422 bps = $-5,463 (1 NQ) / $-546 (1 micro), weekend gap -6; 20150824: -397 bps = $-3,196 (1 NQ) / $-320 (1 micro), weekend gap -29; 20220613: -373 bps = $-8,465 (1 NQ) / $-846 (1 micro), weekend gap -75; 20220307: -359 bps = $-9,546 (1 NQ) / $-955 (1 micro), weekend gap -26; 20250310: -340 bps = $-13,228 (1 NQ) / $-1,323 (1 micro), weekend gap -30; 20220509: -321 bps = $-7,848 (1 NQ) / $-785 (1 micro), weekend gap -53; 20210510: -304 bps = $-8,091 (1 NQ) / $-809 (1 micro), weekend gap -2; 20190513: -304 bps = $-4,442 (1 NQ) / $-444 (1 micro), weekend gap -103

Diagnosis (plain): (a) Where: NOT the Sunday evening or Asia (ES +1.0 / +0.7 bps, NQ +1.3 / +0.2, |t| < 1 and unchanged across eras) and not the pre-market; the shift is the Monday 09:30-16:00 RTH leg (ES -1.1 pre-2023 -> +15.0 from 2023, NQ +3.6 -> +20.5) plus London (ES +2.5 -> +5.7, NQ +0.3 -> +6.7): the NQ stack's own session. (b) One-off? Partly amplified, not only: the five largest Monday-excess weeks carry 40% (ES) / 30% (NQ) of the 13-year total and removing them cuts ES FULL from +8.1 to +4.5 and NQ from +12.2 to +8.2, but the 2023+ excess stays +20 (ES) / +28 (NQ) without them; 2020 alone is +54 bps ES. NQ by year 2023 / 2024 / 2025 / 2026 = +19 / +15 / +34 / +49 bps, so 2023-25 are positive without 2026, but over the whole sample ES drops to +2.2 and NQ to +3.8 bps when both 2020 and 2026 are removed (the 2013-22 years are flat). (c) Weekend news / Friday close: the Monday return mean-reverts the weekend gap (beta -0.3 to -0.7 per bp of gap, t -1.9 to -4.2 in both eras) and, from 2023, follows weak Fridays up (NQ +44 bps after a down Friday vs +25 after an up Friday; ES +35 / +19) -- a buy-the-weakness component that is stronger in the 2023+ up-trend regime, which also explains why the effect has the stack's sign. (d) Same regime as the NQ stack: the stack's Monday V2 mean is -$2.1k / +$1.0k / +$6.3k / +$7.6k per day in 2023 / 24 / 25 / 26 (other days +1.0k / +3.1k / +1.5k / +4.1k) while the NQ Monday excess is +19 / +15 / +34 / +49 bps, so the two strengthen together in 2025-26; their day-level correlation is only +0.11 (stack Monday $ vs NQ Monday FULL bps), i.e. the same regime, not the same P&L. (e) Tail: no-stop long is exposed to -$3k to -$9k per ES (-$300 to -$900 per micro) on the worst Mondays (2020-03-09 -644 bps; 2018-02-05 -501 bps), which dwarfs the +$330 mean per trade; a stop variant is in the watch spec. Conclusion: a 2023+ RTH/London Monday-dip-buying regime shared with the stack, amplified by 2020 and 2026, not a stable 13-year seasonal; stays WATCH/REGIME.
## RECONCILIATION of the CL Donchian-20 stop-and-reverse 13-year totals (S4a, 2026-11-06; asked by the lead after ZL-2's plugin replay)
Same rule everywhere (Donchian 20 on prior 20 label days' H/L, S = close of the 15:54 bar, stop-and-reverse, execution at the 15:55 ET bar open, 1 tick $10 + $2.42 per side per lot). **All runs use the volume-front roll of the series; none uses a calendar roll** (the calendar roll in the spec is an execution recommendation that has not been backtested). Roll cost (2 slips + one RT fee per lot held) = $4,074 over 13 years at 1 lot where charged. Reference: the multiplicative series is anchored at the last contract (CL $101.57 on 2026-10-16); "raw $" = P&L in the actual contract prices of each year, "adjusted $" = P&L in percent-frame dollars at the 2026-10 price level (old segments scaled by 1.69 in 2013, 1.0 in 2017-19, 0.64-0.74 in 2020-23, 0.94 in 2026).
| # | definition | lots | $ basis | H/L window | days | roll cost | 13-year net | maxDD |
|--|--|--|--|--|--|--|--|--|
| 1 | DS3_FIND_DAILY / stress | vol lots (mean 1.1) | raw $ | whole label day (evening session included) | 3,547 | charged | $145,271 | $47,782 |
| 2 | WATCH spec text ("1-lot version") | 1 | raw $ | same | 3,547 | charged | $132,164 | $42,947 |
| 3 | same at 1 lot, adjusted $ | 1 | adjusted $ | same | 3,547 | charged | $147,485 | $48,338 |
| 4 | + H/L from 00:00-15:54 only (ZL-2 convention) | 1 | adjusted $ | calendar bars 00:00-15:54 | 3,547 | charged | $152,290 | $48,338 |
| 5 | + ZL-2's day set (128 label days with < 200 bars before 15:55 dropped) | 1 | adjusted $ | same | 3,419 | charged | $152,276 | $50,487 |
| 6 | ZL-2 plugin replay | 1 | adjusted $ | same | 3,419 | NOT charged (its roll flag is never set, so $3,701 is missing) | $155,978 | $50,487 |
Steps: 2 to 3 (+$15.3k) is the dollar basis (the profitable 2013-15 years, when CL traded near $90-100 raw, are scaled to a 1.7x larger factor than the loss years, and the 2020-23 years are scaled down); 3 to 4 (+$4.8k) is the H/L window; 4 to 5 (-$0.01k) the day set; 5 to 6 (+$3.7k) the missing roll cost. Row 6 reproduces ZL-2's number exactly ($155,978 net, $157,754 gross, $1,776 trade cost) and row 1 differs from row 6 only by the vol-lots (+0.09 lots), the dollar basis, the H/L window, the day set and the roll cost. No row is wrong; they are different definitions. Which one is the frozen spec: the spec text says "H/L = day high/low through 15:54" and the research code used the label day (row 1-3); the plugin uses calendar bars 00:00-15:54 (row 4-6) and omits roll costs. **Recommendation: ZL-2 aligns the plugin to the spec (label-day H/L from the session open, roll cost charged) or the lead approves the plugin definition by a dated amendment; the forward effect is small (+/- a few signals in 20 days after the first week).**
### Thresholds K1 / K2 and the forward-dollar basis
The forward Shadow runs at 1 lot in then-current dollars (a CL point = $1,000 at today's ~$100 level), which is the ADJUSTED-$ 1-lot basis (rows 3-6), not the raw-$ vol-lots series the thresholds were computed from. Like-for-like comparison:
| series | maxDD | annual sigma of daily P&L |
|--|--|--|
| K source: raw $, vol lots (row 1) | $47,782 | $26,761 |
| raw $, 1 lot (row 2) | $42,947 | $25,716 |
| **adjusted $, 1 lot (rows 3/4; forward-dollar equivalent)** | **$48,338** | **$25,149** |
| adjusted $, vol lots | $53,071 | $26,584 |
| plugin definition, ZL-2 day set (rows 5/6) | $50,487 | n/a |
So K1 ($47,782) is 1.2% below the like-for-like historical maximum drawdown ($48,338; 5.4% below the plugin definition's $50,487), i.e. slightly conservative (it can fire a little early), and K2 (-$26,761) is 6% looser than one annual sigma on the forward basis ($25,149). **Both stay on the forward-dollar basis in the sense that matters: a forward drawdown/cumulative loss in dollars of the then-current contract is compared with them directly. No amendment is needed; if the lead wants strict like-for-like, the dated amendment would be K1 = $48,338 and K2 = -$25,149 (adjusted $, 1 lot, spec definition) - NOT applied; the frozen spec file and its sha256 ce175343cad55acd4304ce35d2dccd3a85afebb6f3f416b449ce6a0c82b88de0 are unchanged.**
### Correction found while reconciling (S4a code bug, results unchanged in substance)
daily_lib.build computed the daily high/low on roll days as raw max/min times the adjustment factor of the extreme bar instead of max/min of the adjusted bars; this changed H on 23 CL days (and a similar few days on other instruments). Rebuilt and rerun: the CL Donchian-20 SAR cell is unchanged ($145,271, maxDD $47,782); in the 96-cell CL surface 8 cells with N = 10-15 changed (largest +$20k for N = 10 / exit N, high-vol filter), the plateau count stays 3 of 8; in FIND_DAILY 10 Donchian cells changed total (YM DON N20/N40/N60/N100, 6J DON_N20_EX, five PORT DON cells, largest +$14k), no tolerant flag, no label and no family-p statement changed (labels NULL 283 / REGIME 89 / best-of-F 36 / LEAD 0; best tolerant p .33 / .48). The pre-fix files are kept in /mnt/l2/l2vast/ds3_daily/v1/.
## DAILY-R6 (S4a, 2026-11-06): the FIND_DAILY 34-cell daily-horizon design on the 16 unscored outrights SI HG PL NG RB HO ZF ZT 6B 6A 6C ZC ZS ZW LE HE (IDEAS_ROUND2 R6)
Prereg l2vast/ds3/prereg/DAILY_R6_prereg.md sha256 fb13144effb0b24ed4820c152c333cd3eb8459074d2c558718a517191d776f1b (filed before any statistic; inherits FIND_DAILY bf1de6c6...; per the R5 finding the RANDOM-SIDE null governs trend cells, the shift null is a cross-check). Code l2vast/ds3/code/t2s4a/daily6_lib.py, daily6_run.py, daily6_analyze.py, daily6_follow.py; data /mnt/l2/l2vast/ds3_daily6/ (/mnt/l2 only). Ledger T2F_DAILY6_<SYM> (612 rows), n_tested + 612.
**Set.** The owned 26-outright 1-minute set (data_autopilot/ohlcv1m, .v.0 volume-front with instrument_id, 2013-01..2026-10-14) holds ES NQ RTY YM GC SI HG PL CL NG RB HO ZN ZB ZF ZT 6E 6J 6B 6A 6C ZC ZS ZW LE HE (+ NKD). Already scored in FIND_DAILY: ES RTY YM GC CL ZN ZB 6E 6J NKD; NQ is the live stack. **New: the 16 above; nothing else in the set was uncovered.** Overlap cited, not repeated: T4 Family A (outputs/t4, daily trend book Donchian 20/10-100/50, EMA 20/100, 50/200, 12-month TSMOM, Supertrend on these outrights, sleeve scoring vs the NQ pair), IDEAS50K N7 (weekly-range position, REPORT_N7.md: NO), N10 (cross-sectional daily rank books, candle patterns: 3 gate a-d passes, all one beta bet), N13 (cross-sectional momentum commodities: N13-CSMOM-COMMXX gate a-d True only under an invalid beta null); none of the 34 time-series cells per product is a repeat.
**Repair scan first (DATA_BAD_PRINTS rule).** Bad-bar share by product (max by year): 6A 1.37% (2013), 6C 1.07% (2013), 6B 1.06% (2013), all three below 0.05% from 2016 on (the same early-FX print problem as 6E / 6J, repaired); LE 0.36% (2015) and HE 0.23% (2014); ZW 0.13% (2022); the other ten products at most 0.05% every year. The repaired copy is used. Rolls (volume-front changes, 2013-2026): SI 71, HG 69, PL 55, NG 169, RB 222, HO 179, ZF 57, ZT 55, 6B / 6A / 6C 55 each, ZC 90, ZS 80, ZW 77, LE 121, HE 123.
**Anchors (ET; execution P = open of the anchor bar, signal inputs = bars before it; stated per product) and PROXY specs (not in FEES.md):** SI HG PL 13:25 (COMEX close 13:30; day open Q 08:20); NG RB HO 14:25 (settlement 14:30; Q 09:00); ZF ZT 14:55 (CBOT Treasuries day close 15:00; Q 08:20); 6B 6A 6C 15:55 (24-hour FX; Q 08:20); ZC ZS ZW 14:15 (grain close 14:20; Q 09:30); LE HE 14:00 (livestock close 14:05; Q 09:30). Point value / tick: SI 5000 / 0.005, HG 25000 / 0.0005, PL 50 / 0.1, NG 10000 / 0.001, RB HO 42000 / 0.0001, ZF 1000 / 1/128, ZT 2000 / 1/256, 6B 62500 / 0.0001, 6A 100000 / 0.0001, 6C 100000 / 0.00005, ZC ZS ZW 50 / 0.25, LE HE 400 / 0.025; fee $4.84 RT (PROXY-STD), 1 tick per market leg, roll = 2 slips + one RT fee per held lot. Thin products (PL, LE, HE, ZT) carry a liquidity caveat; margin not in the repository.
**Plain sentence: none of the 16 new outrights yields a daily book: of 578 cells (34 per product x 16 + the 16-product portfolio) 197 are net positive over 13 years, 41 also positive in at least 60% of years, 19 also pass the per-year MDE test and 14 the HOLD test (tolerant: HE 2, HG 1, HO 3, NG 4, SI 1, ZT 1, ZW 1, portfolio 1); the smallest family p of a tolerant cell is 0.78 in the new-set family and 0.92 in the joint family with the 11 earlier instruments (1,000 random-side worlds; the family-maximum null has median 2.90 / 3.03 and p95 3.53 / 3.68), no cell is a LEAD (labels NULL 464, REGIME 130, best-of-F 18 over 612 rows incl. PORT27), and eight of the 13 tolerant instrument cells survive a 1.5x cost stress.**
Funnel and nulls: new-set family 578 cells; random-side maximum z median 2.90, p95 3.53; forward-shift median 2.70, p95 3.47; joint family 1,020 cells (374 earlier + 544 new instrument cells + PORT11 / PORT16 / PORT27): random-side median 3.03, p95 3.68; shift median 2.91, p95 3.65. Truncation audit 0 of 1,296 mismatches.
### Tolerant cells (maxDD first; $ at stated lots, vol lots with 1-lot floor; HOLD $/wk carry-dropped)
| cell | maxDD $ | 13y net $ | years + | HOLD $/wk | z random-side | family p random-side A / B | family p shift A | walk-forward OOS (p) | corr to NQ stack (weekly) | survives 1.5x cost |
|--|--|--|--|--|--|--|--|--|--|--|
| NG MR_k5_th1.5 | 27453 | 69331 | 11/14 | 76 | 2.66 | 0.776 / 0.916 | 0.60 | 45061 (p 0.39) | 0.02 | yes |
| HO NIGHT_L | 56974 | 244468 | 10/14 | 1806 | 2.59 | 0.833 / 0.946 | 1.00 | 114324 (p 0.10) | 0.01 | yes |
| HG TSMOM_L252_vol | 87587 | 114230 | 9/14 | 291 | 1.40 | 1.000 / 1.000 | 1.00 | 33286 (p 0.05) | -0.14 | yes |
| NG TSMOM_L21_1lot | 42301 | 76886 | 9/14 | 102 | 1.30 | 1.000 / 1.000 | 1.00 | 6060 (p 0.49) | 0.00 | yes |
| ZT DON_N100_EX | 36046 | 84139 | 9/14 | 281 | 1.25 | 1.000 / 1.000 | 1.00 | 73591 (p 0.52) | 0.07 | yes |
| ZW MR_k3_th1.5 | 29398 | 8103 | 9/14 | 510 | 1.23 | 1.000 / 1.000 | 1.00 | 7002 (p 0.19) | 0.07 | no |
| HO NIGHT_MOM20 | 60092 | 113942 | 9/14 | 2224 | 1.19 | 1.000 / 1.000 | 1.00 | 114324 (p 0.10) | 0.15 | no |
| SI MR_k1_th1.5 | 69804 | 88594 | 9/14 | 2174 | 1.12 | 1.000 / 1.000 | 1.00 | 50877 (p 0.43) | 0.09 | no |
| NG MR_k2_th1 | 55442 | 35253 | 9/14 | 43 | 1.07 | 1.000 / 1.000 | 1.00 | 45061 (p 0.39) | 0.03 | no |
| NG MR_k3_th1 | 56052 | 26320 | 9/14 | 111 | 0.94 | 1.000 / 1.000 | 1.00 | 45061 (p 0.39) | 0.02 | yes |
| HE DON_N40_SAR | 76740 | 52799 | 9/14 | 158 | 0.92 | 1.000 / 1.000 | 1.00 | -41690 (p 0.68) | -0.04 | no |
| PORT16 MA_50_200 | 548873 | 289523 | 9/14 | 4181 | 0.86 | 1.000 / 1.000 | 1.00 | -167497 (p 0.73) | -0.09 | n/a |
| HE DON_N40_EX | 40490 | 39440 | 10/14 | 232 | 0.82 | 1.000 / 1.000 | 1.00 | -41690 (p 0.68) | -0.01 | yes |
| HO DON_N100_EX | 139808 | 87274 | 9/14 | 863 | 0.61 | 1.000 / 1.000 | 1.00 | 192586 (p 0.03) | -0.05 | yes |
The portfolio (PORT27 = 11 earlier + 16 new products) has 4 tolerant cells and the 16-product portfolio 1 (MA 50/200, 13-year net $290k, maxDD $549k); the best portfolio family p is 0.15 / 0.26 (PORT27 night long, whose 13-year net is -$4.2M: a cost-eaten leg, below).
### Cross-check with the forward-shift null
Only one of the 612 rows has a shift-null family p <= .10: HE night momentum (z 3.36, p 0.06), with a random-side p of 0.26 and not tolerant; among the tolerant cells the smallest shift p is 0.60. The 6E TSMOM-252 pattern (shift p .005, random-side 1.00) does not recur here, and the random-side null governs.
### Annual-refit walk-forward: 7 of 90 groups positive with p <= .10, none distinguishable from chance after the multiplicity
The 90 groups (16 products + PORT16 + PORT27 x 5 families) are expected to give about 9 with p <= .10; 7 are positive. The smallest p is 0.004, Bonferroni over 90 groups 0.36. Each is dominated by one or two years and has a family p of 1.00 for its cells: p_rand tests whether refit beats a RANDOM parameter pick (many parameter sets in each family lose), not whether the family earns.
| group | OOS total $ | p vs random pick | OOS maxDD $ | OOS Calmar | years + | best year $ | best year share of total | stack dCalmar HOLD / L6M | corr to NQ stack |
|--|--|--|--|--|--|--|--|--|--|
| SI F1 | 182686 | 0.005 | 261083 | 0.07 | 7/10 | 164089 | 0.90 | +0.021 / +0.019 | -0.07 |
| HG F1 | 33286 | 0.046 | 87587 | 0.04 | 6/10 | 35401 | 1.06 | +0.018 / +0.005 | -0.14 |
| NG F3 | 75836 | 0.007 | 61441 | 0.12 | 8/10 | 32283 | 0.43 | +0.000 / +0.000 | +0.05 |
| HO F2 | 192586 | 0.034 | 119920 | 0.16 | 6/10 | 151169 | 0.78 | +0.049 / +0.002 | -0.01 |
| ZF F1 | 93693 | 0.004 | 17482 | 0.54 | 6/10 | 46293 | 0.49 | +0.008 / +0.004 | +0.02 |
| ZT F1 | 86317 | 0.020 | 19691 | 0.44 | 6/10 | 52485 | 0.61 | +0.004 / +0.003 | -0.03 |
| 6B F2 | 6916 | 0.056 | 78300 | 0.01 | 5/10 | 34510 | 4.99 | +0.000 / +0.000 | +0.06 |
ZF and ZT momentum (OOS +$94k and +$86k, maxDD $17-20k, Calmar 0.5) are the best-looking: about half of each comes from 2022 (+$46k and +$52k, the rate sell-off) and 2023-2026 is flat to negative, so they are a one-regime result; SI +$183k is 90% 2025; HO +$193k is 78% 2026.
### Unconditional night / day legs: a real overnight drift in ZS, LE (and mirror cases in HE, 6C) that the costs eat
The random-side null is a gross-drift test for the six constant-sign leg cells (probability 0.5 for the sign). LE night long (z 5.0, family p < .001 in A and B), ZS night long (z 4.3, < .001), 6C night short (z 3.7, 0.03 / 0.06) and HE night long (z 3.4, 0.08 / 0.14) beat the family-maximum null, i.e. the direction of the overnight move is not random, but every one has a NEGATIVE 13-year net at one tick per leg (LE -$68k, ZS -$20k, HE -$107k, 6C -$31k), so none is tolerant. Gross vs net (13 years, vol lots):
| leg | gross $ | net at 1 tick / leg $ | net at 0.5 tick / leg $ (COSTCAL S1 proxy) | cost at 1 tick $ |
|--|--|--|--|--|
| ZS NIGHT_L | +199096 | -19631 | +71994 | +218727 |
| ZS NIGHT_S | -199096 | -417823 | -326198 | +218727 |
| ZS DAY_S | +94082 | -124645 | -33020 | +218727 |
| LE NIGHT_L | +144326 | -68354 | +17266 | +212680 |
| LE NIGHT_S | -144326 | -357006 | -271386 | +212680 |
| LE DAY_S | +92984 | -119696 | -34076 | +212680 |
| HE NIGHT_L | +99200 | -106773 | -23853 | +205973 |
| HE NIGHT_S | -99200 | -305173 | -222253 | +205973 |
| HE DAY_S | +176591 | -29382 | +53538 | +205973 |
| 6C NIGHT_L | -180065 | -391505 | -320265 | +211440 |
| 6C NIGHT_S | +180065 | -31376 | +39864 | +211440 |
| 6C DAY_S | -39440 | -250880 | -179640 | +211440 |
The day leg mirrors the night leg (ZS day short +$94k gross vs night long +$199k; LE +$93k vs +$144k; HE +$177k vs +$99k): the anchor-to-open interval earns, the open-to-anchor interval gives it back. At a half-tick per leg ZS night long would be +$72k over 13 years (about $5.5k a year at 1-2 lots) and LE +$17k: a product-session microstructure effect of a few dollars per lot per day against round-trip costs of $25-30, unmeasured spreads (no order-book table for ZS / LE / HE / 6C), with the ZS evening session as the likely source. Not a book; a candidate for a measured-spread look if 1-s tables for ZS / LE are ever owned.
Limits: costs and specs are PROXY; thin products (PL, LE, HE, ZT) have wider true spreads than one tick; no frames saved (no cell is a lead); the joint family reuses the earlier 1,000-world totals for the 11 instruments (ids 1000-1999, independent of the new ids 2000-2999).
Correction (appended, DAILY-R6): in the unconditional-leg paragraph 'a few dollars per lot per day' should read: gross edge of $30-60 per day at the cells' vol lots (ZS night long $57, LE $42, HE $29) against round-trip costs of $25-30 per lot; and 'the ZS evening session as the likely source' is an untested hypothesis, not a result.
## RATES-MOM STRESS (S4a, 2026-11-06): ZF / ZT daily momentum, stressed like the CL cell - follow-up on best-of-F cells
Prereg l2vast/ds3/prereg/RATES_MOM_STRESS_prereg.md sha256 8ae2c02534d2aeb72d3dd76cb0d02b50ca45f32fd354e27207691822b154fdac (filed before any statistic). Code l2vast/ds3/code/t2s4a/rates_stress.py, rates_stress2.py; results /mnt/l2/l2vast/ds3_daily6/rates_stress_*.pkl, rates_fine.pkl. The engine reproduces the earlier cells (ZF L126 vol 18,713; ZF L252 1-lot 13,402; ZT L252 vol 96,637). Products: ZF, ZT (daily6 builds, anchor 14:55 ET) and ZN, ZB (FIND_DAILY builds, 15:55 ET) as the rates group.
**Plain sentence: the ZF / ZT momentum result is not on a plateau and does not survive the stress: the 13-year profit sits on a narrow band of lookbacks (189-231 days; L = 126, 168 and 252 next to it are flat or weak, and only 2-3 of 8 lookbacks pass the pre-stated Calmar >= 0.10 test, 5 were required), 98-99% of the net of the L189 books comes from their three best trades (the other 74-77 trades sum to about +$1k to +$3k, win rate 29-31%), 76-78% from three years (2022, 2020, 2024 / 2026), the walk-forward OOS drops to +$47k (ZF) and +$34k (ZT) without 2022, and the four rates books are one bet (effective 1.6-1.7 independent bets, P&L correlations 0.4-0.9) whose only significant version (L189, common-flip null p 0.015 before the correction for choosing the best of 8 lookbacks, about 0.12 after) is the post-hoc best lookback. At the lots the vol target implies (5-6 contracts, the cap) the books are worth $0-300 a week against the live stack's $28k, so there is no WATCH spec and nothing for ZL-2 to register.**
### S1 plateau surface (128 cells per product; trailing stop = m x monthly sigma from the best close, flat until the signal flips)
Pre-stated plateau rule on the reference sizing ($1,200 vol lots, no stop): (a) >= 5 of 8 lookbacks with 13-year net > 0 and Calmar >= .10; (b) >= 4 of 8 the same ex-2022; (c) neighbour median Calmar >= 50% of the best cell. Result: ZF a = 2, b = 1, best L189 Calmar 0.34, neighbour median 0.16 (< 0.17): FAIL; ZT a = 3, b = 2, best L189 0.38, neighbours 0.16 (< 0.19): FAIL; ZN a = 2, b = 2, (c) 0.13 vs 0.13 passes but (a) and (b) fail; ZB a = 1, b = 1: FAIL. **No product survives at a plateau.**
**ZF** - Calmar, vol lots $1,200, by trailing stop (columns: none, 1.0, 1.5, 2.0 x monthly sigma):
| L | 0.0 | 1.0 | 1.5 | 2.0 |
|--|--|--|--|--|
| 21 | -0.06 | -0.05 | -0.06 | -0.06 |
| 42 | 0.11 | 0.07 | 0.11 | 0.11 |
| 63 | -0.01 | -0.05 | -0.01 | -0.00 |
| 84 | 0.01 | -0.01 | 0.02 | 0.01 |
| 126 | 0.01 | -0.03 | 0.05 | 0.04 |
| 189 | 0.34 | 0.15 | 0.18 | 0.25 |
| 252 | 0.05 | -0.03 | -0.02 | -0.01 |
| 315 | 0.09 | -0.04 | 0.01 | 0.09 |

**ZF** - Calmar, no stop, by sizing (600 / 1,200 / 2,400 daily-sigma target, 1 lot), full sample:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.05 | -0.06 | -0.06 | -0.06 |
| 42 | 0.11 | 0.11 | 0.10 | 0.09 |
| 63 | -0.01 | -0.01 | -0.02 | -0.02 |
| 84 | 0.01 | 0.01 | 0.00 | 0.00 |
| 126 | 0.02 | 0.01 | 0.02 | 0.02 |
| 189 | 0.31 | 0.34 | 0.44 | 0.44 |
| 252 | 0.02 | 0.05 | 0.08 | 0.08 |
| 315 | 0.08 | 0.09 | 0.14 | 0.14 |

**ZF** - Calmar EX-2022, no stop, by sizing:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.06 | -0.06 | -0.06 | -0.06 |
| 42 | 0.08 | 0.08 | 0.06 | 0.06 |
| 63 | -0.02 | -0.03 | -0.04 | -0.05 |
| 84 | -0.02 | -0.02 | -0.04 | -0.04 |
| 126 | -0.01 | -0.02 | -0.03 | -0.03 |
| 189 | 0.24 | 0.25 | 0.28 | 0.29 |
| 252 | -0.03 | -0.01 | 0.00 | 0.01 |
| 315 | 0.03 | 0.03 | 0.05 | 0.05 |
**ZT** - Calmar, vol lots $1,200, by trailing stop (columns: none, 1.0, 1.5, 2.0 x monthly sigma):
| L | 0.0 | 1.0 | 1.5 | 2.0 |
|--|--|--|--|--|
| 21 | -0.06 | -0.06 | -0.06 | -0.06 |
| 42 | 0.01 | -0.01 | 0.01 | 0.01 |
| 63 | 0.03 | 0.02 | 0.02 | 0.02 |
| 84 | 0.03 | 0.02 | 0.04 | 0.03 |
| 126 | -0.01 | -0.05 | -0.03 | -0.00 |
| 189 | 0.38 | 0.08 | 0.19 | 0.19 |
| 252 | 0.14 | -0.05 | 0.03 | 0.06 |
| 315 | 0.30 | 0.11 | 0.23 | 0.24 |

**ZT** - Calmar, no stop, by sizing (600 / 1,200 / 2,400 daily-sigma target, 1 lot), full sample:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.07 | -0.06 | -0.06 | -0.06 |
| 42 | -0.02 | 0.01 | 0.03 | 0.03 |
| 63 | 0.03 | 0.03 | 0.01 | 0.00 |
| 84 | 0.00 | 0.03 | 0.04 | 0.05 |
| 126 | -0.01 | -0.01 | -0.00 | -0.00 |
| 189 | 0.34 | 0.38 | 0.40 | 0.40 |
| 252 | 0.13 | 0.14 | 0.17 | 0.18 |
| 315 | 0.28 | 0.30 | 0.32 | 0.33 |

**ZT** - Calmar EX-2022, no stop, by sizing:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.07 | -0.07 | -0.07 | -0.07 |
| 42 | -0.05 | -0.03 | -0.03 | -0.02 |
| 63 | -0.01 | -0.02 | -0.03 | -0.04 |
| 84 | -0.05 | -0.04 | -0.04 | -0.03 |
| 126 | -0.04 | -0.04 | -0.04 | -0.04 |
| 189 | 0.25 | 0.25 | 0.25 | 0.26 |
| 252 | 0.08 | 0.07 | 0.08 | 0.09 |
| 315 | 0.19 | 0.19 | 0.19 | 0.20 |
The trailing stop never helps the L189 cells (ZF Calmar 0.34 -> 0.15 / 0.18 / 0.25, ZT 0.38 -> 0.08 / 0.19 / 0.19), and the Calmar is nearly independent of the sizing target (600 / 1,200 / 2,400 / 1 lot), so the vol scaling is not what drives the result.
**Exploratory finer lookback grid (not part of the pre-stated rule, labelled post-hoc):**
| L | ZF | ZT | ZN | ZB | PORT4 net $k | PORT4 Calmar | PORT4 ex-2022 $k | PORT4 Calmar ex-2022 |
|--|--|--|--|--|--|--|--|--|
| 42 | 0.11 | 0.01 | 0.13 | 0.11 | 299 | 0.12 | 216 | 0.09 |
| 63 | -0.01 | 0.03 | 0.00 | 0.02 | 51 | 0.01 | -35 | -0.01 |
| 84 | 0.01 | 0.03 | 0.00 | 0.02 | 60 | 0.01 | -73 | -0.02 |
| 105 | 0.06 | 0.03 | 0.04 | 0.04 | 194 | 0.04 | 25 | 0.01 |
| 126 | 0.01 | -0.01 | -0.01 | 0.01 | 9 | 0.00 | -160 | -0.03 |
| 147 | 0.06 | 0.05 | 0.06 | 0.07 | 260 | 0.07 | 97 | 0.02 |
| 168 | 0.05 | 0.03 | 0.06 | 0.03 | 181 | 0.05 | 23 | 0.01 |
| 189 | 0.34 | 0.38 | 0.25 | -0.01 | 394 | 0.24 | 253 | 0.17 |
| 210 | 0.22 | 0.37 | 0.15 | -0.01 | 354 | 0.17 | 212 | 0.11 |
| 231 | 0.20 | 0.24 | 0.09 | -0.03 | 250 | 0.10 | 90 | 0.04 |
| 252 | 0.05 | 0.14 | -0.04 | -0.06 | -39 | -0.01 | -201 | -0.05 |
| 273 | 0.03 | 0.09 | -0.04 | -0.05 | -8 | -0.00 | -180 | -0.04 |
| 294 | 0.08 | 0.09 | -0.01 | -0.05 | 81 | 0.02 | -92 | -0.02 |
| 315 | 0.09 | 0.30 | 0.01 | -0.05 | 114 | 0.04 | -58 | -0.02 |
| 378 | 0.07 | 0.17 | 0.02 | 0.00 | 175 | 0.05 | 2 | 0.00 |
The good zone is L = 189-231 for ZF and ZT (ZN positive to 210, ZB never): Calmar 0.2-0.4, flanked by 0.03-0.06 at 168 and 0.05-0.14 at 252; as ONE bet (PORT4 = ZF + ZT + ZN + ZB) Calmar 0.24 / 0.17 / 0.10 at 189 / 210 / 231 and 0.17 / 0.11 / 0.04 ex-2022. It is a band about three lookbacks wide out of fifteen tried, not a plateau.
### S2 per year and regime (reference books, $1,200 vol lots, no stop; $k)
| book | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 13y net | maxDD |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ZF L189 | 3.9 | -11.1 | 11.0 | 4.9 | -19.6 | 13.6 | 17.8 | 35.2 | 9.8 | 46.3 | -1.7 | 27.9 | -12.2 | 15.1 | 140.9 | 29.2 |
| ZF L252 | 0.0 | -11.4 | 8.6 | -15.7 | -14.3 | 2.7 | 10.1 | 35.2 | -7.7 | 46.3 | -0.3 | -2.4 | -23.5 | 10.8 | 38.2 | 57.9 |
| ZT L189 | -1.2 | 6.8 | 6.7 | -5.5 | -0.5 | 5.9 | 5.7 | 26.4 | 1.5 | 52.5 | 2.5 | 20.0 | -9.8 | 24.8 | 135.8 | 25.5 |
| ZT L252 | 0.0 | 6.8 | 5.9 | -1.3 | -1.3 | 4.2 | 1.2 | 27.4 | -0.3 | 52.5 | 2.5 | -7.6 | -18.1 | 24.8 | 96.6 | 49.8 |
| ZN L189 | 3.0 | 4.6 | 0.1 | 4.4 | -24.6 | 23.8 | 26.7 | 21.2 | 12.7 | 33.9 | -7.9 | 22.6 | -3.4 | 15.1 | 132.1 | 36.8 |
Regimes (net $k) 2013-16 / 2017-19 / 2020-22 / 2023-26: ZF L189 8.7 / 11.8 / 91.3 / 29.1; ZF L252 -18.5 / -1.6 / 73.8 / -15.5; ZT L189 6.8 / 11.1 / 80.5 / 37.5; ZT L252 11.3 / 4.1 / 79.6 / 1.6; ZN L189 12.0 / 25.9 / 67.7 / 26.4. The 2013 taper tantrum (May-Sep 2013) is a non-event for L189 / L252 (no position yet: the 189-252 day sign was still flat) and a -$6.8k loss for ZF L126; 2020 pays +$21k to +$35k per book (the COVID rate collapse) and 2022 +$34k to +$53k (the sell-off): 2020-22 is 65-87% of every book's 13-year net.
Ex-2022 and ex-2022-23 (13-year net, Calmar): ZF L189 +$94.6k (0.25) / +$96.3k; ZT L189 +$83.4k (0.25) / +$80.9k; ZN L189 +$98.2k (0.20) / +$106.1k; but ZF L252 -$8.1k, ZF L126 -$27.6k, ZT L252 +$44.2k (0.07), ZT L126 -$65.1k. The walk-forward OOS (annual refit among the 8 TSMOM cells): ZF +$93.7k all years, +$47.4k ex-2022 (Calmar 0.27), +$49.2k ex-2022-23; ZT +$86.3k, +$33.8k ex-2022 (Calmar 0.19), +$31.5k ex-2022-23; the refit picked L126 (ZF, 2018-22) and L252 (ZT) - not the L189 that the surface favours - so the OOS rows and the surface rest on different cells.
### S3 concentration (episodes = runs of constant sign)
| book | episodes | win rate | top-3 trades share of net | net excluding the top 3 | top-3 years share |
|--|--|--|--|--|--|
| ZF L189 | 77 | 29% | 99% | +$1.1k | 78% (2022, 2020, 2024) |
| ZT L189 | 80 | 31% | 98% | +$2.6k | 76% (2022, 2020, 2026) |
| ZT L315 | 54 | 31% | 89% | +$13.4k | 70% |
| ZF L252 | 49 | 27% | 315% | -$83.4k | 242% |
| ZT L252 | 58 | 28% | 127% | -$26.0k | 108% |
### S4 realism: lots, margin, live stack
ZF notional $118k per contract (tick $7.81, daily sigma about $212 per contract); ZT notional $216k per contract (tick $7.81, sigma about $131). The $1,200 daily-sigma target asks for 5.2 ZF and 5.7 ZT contracts on average and sits AT the cap of 6 contracts 58% (ZF) and 82% (ZT) of the days; at $2,400 it is at the cap 97-98% of the days: the 'vol-targeted' books are fixed 6-contract books (ZN 3.6 and ZB 1.6 contracts). Margin is not in the repository: PROXY (T4 assumed ZF $1.5k, ZT $1k per contract, unverified) = $9k and $6k at 6 contracts, notional about $0.7M (ZF) and $1.3M (ZT). Next to the live stack (V2 HOLD $28.2k a week mean, maxDD $91.2k): ZF L189 earns -$73 a week in HOLD, ZT L189 +$162, ZT L252 +$306 (0.6-1.1% of the stack); the stack can absorb k* = 5 books (the search limit) with a Calmar gain of +0.03 to +0.06; weekly correlation to the stack -0.02 to +0.05. Diversifying and immaterial.
### S5 ZF + ZT + ZN + ZB as ONE rates bet
P&L correlations (L189): ZF-ZT 0.77, ZF-ZN 0.84, ZF-ZB 0.58, ZT-ZN 0.61, ZT-ZB 0.39, ZN-ZB 0.75; effective independent bets 1.70 (L189) and 1.59 (L252); the signs agree 87-91% of the days. PORT4 at L189: net $393.9k, maxDD $113.6k, Calmar 0.24, 10 of 14 years positive, +$253.4k ex-2022; at L252: -$39.1k, maxDD $276k. Common-flip null (one shared random sign per calendar month for all four books, 1,000 worlds ids 3000-3999, counts the four as one bet): L189 z 2.14, p 0.015; L252 z 0.22, p 0.40. The L189 result is the best of 8 lookbacks (about 0.12 after the correction) and of a band that the prereg's coarser grid happened to hit.
### S6 regime feature ('momentum works in rates only when the Fed trends')
Causal regime = tercile of |ZT 252-day return| ranked against its own expanding history. P&L by regime tercile (net $k): ZF L189 6.8 (undefined, first 3 years) / 23.8 (low) / 20.7 (mid) / **89.6 (high)**; ZT L189 14.9 / 26.8 / 5.1 / **88.9**; ZN L189 9.1 / 2.0 / 29.1 / **91.8**; ZF L252 2.6 / -24.1 / -28.2 / **+87.9**; ZT L252 16.1 / -2.8 / -7.0 / **+90.4**: 60-100% of every book's profit arrives in the high-trend tercile (1,381 of 3,550 days) - descriptively, the reading holds. It is not usable causally: trading only when the regime is above its expanding median LOWERS the L189 books (ZF 140.9k -> 83.3k, ex-2022 +37.0k with Calmar 0.08; ZT 135.8k -> 86.3k, ex-2022 +33.8k, Calmar 0.07; ZN 132.1k -> 103.5k, ex-2022 Calmar 0.18) because the 252-day filter switches on after the trend began, and helps only the L252 books (ZF 38.2k -> 63.1k, ex-2022 +16.8k; ZT 96.6k -> 89.2k); the walk-forward with the on/off switch as an extra candidate gives no gain (ZF OOS +$118.0k vs +$132.2k without the switch; ZT +$96.1k vs +$96.1k). The pre-stated usability test (conditioned book keeps Calmar >= .10 ex-2022 and the WF OOS ex-2022 stays positive) is met only by ZN. **The regime is a description of where the P&L was, not a feature the walk-forward can use.**
### Verdict and next step
Plateau rule failed for ZF, ZT, ZN and ZB; ex-2022 the surviving cells are the post-hoc L189 band; the one-bet significance (p 0.015) does not survive the choice among 8 lookbacks; the economics are $0-300 a week against a $28k stack. **Label: best-of-F, REGIME-concentrated (2020-22), cells on a narrow ridge. No WATCH_ZF_MOM_SPEC.md is written and ZL-2 has nothing to register.** A genuinely new, separately preregistered test would be the only way to use the L189-231 band (the 2023-2026 years are +$29k to +$38k for the L189 books, so the band is not dead out of sample, but 2023-26 contains the band's own selection).
Corrections (appended, RATES-MOM STRESS): (1) '2020-22 is 65-87% of every book's net' should read 51% (ZN L189), 59% (ZT L189), 65% (ZF L189), 82% (ZT L252), 193% (ZF L252, whose other years net negative). (2) The 2013 taper tantrum cannot be tested for lookbacks >= 189 days: the series starts 2013-01-02, so these books have no signal until about October 2013 (warm-up, not a flat sign); only ZF L126 (-$6.8k, May-Sep 2013) and ZB L42 (-$6.1k) saw it. (3) '60-100% of every book's profit arrives in the high-trend tercile' should read 64% (ZF L189), 65% (ZT L189), 69% (ZN L189), 94% (ZT L252) and 230% (ZF L252). (4) The L189 books' 2023-26 net is +$26k to +$38k (ZN 26.4, ZF 29.1, ZT 37.5).

## REPAIRED-DAILY (S4a, 2026-11-06): daily books on original vs repaired bars - summary (full per-cell tables in REPAIRED_BARS_RERUN.md)
Read first: the repaired 1-minute copy that CHAR-C publishes for the te2 feed (find_c/cache_c_feeds/te2/<SYM>.npz) is byte-identical to find_c/cache_c/<SYM>.npz (REPAIRED_BARS_PATHS.md), which is the file all of my daily programs (FIND_DAILY, rates momentum, CL stress, REPLICATION R4/R5, COSTCAL daily) were built from; DAILY-R6 repaired its 16 products in the build with the same rule (cc_audit v1). So the published daily numbers are already the REPAIRED numbers; this block runs the daily books on the ORIGINAL bars (cache_te2 for the 11 FIND_DAILY instruments; the raw ohlcv1m for the 16 R6 products, repair switched off) and reports original vs repaired. Code l2vast/ds3/code/t2s4a/repaired_cmp.py, repaired_k.py (env DAILY_OUT / DAILY_SRC / DAILY6_OUT / DAILY6_REPAIR); data /mnt/l2/l2vast/ds3_daily_orig, ds3_daily6_orig (originals untouched).
#### Watch cell, frozen thresholds, plateau counts, walk-forward
* **CL Donchian-20 stop-and-reverse (watch cell): identical on original and repaired bars** (all three bases): vol lots raw $ net $145,270.5, maxDD $47,781.8, annual sigma $26,760.8; 1 lot raw $ $132,163.6 / $42,946.5 / $25,716.1; 1 lot adjusted $ (forward-dollar basis) $147,485.1 / $48,338.4 / $25,148.8; ex-2020 $97.8k. **K1 ($47,782) and K2 (-$26,761) and the reconciliation table of WATCH_CL_DONCHIAN_RECON.md do not move; no amendment.** The ZL-2 plugin reads cache_c (repaired) as well.
* CL 96-cell surface: 2 of 96 cells change (N = 10, exit N/4, no-filter and high-vol: +$24.7k vs +$12.7k and -$12.9k vs -$24.9k), the plateau count stays 3 of 8, neighbour median Calmar 0.114 both, top-3-trades share 89.1% both.
* Rates momentum (ZF, ZT, ZN, ZB): 0 of 512 surface cells change (TSMOM uses the closes only; no bad print reaches them); plateau counts identical (ZF a 2 / b 1, ZT 3 / 2, ZN 2 / 2, ZB 1 / 1), L189 cells identical ($140.9k, $135.8k, $132.1k), so the ZF / ZT verdict, the WATCH_ZF_MOM decision (none written) and the S5 / S6 numbers stand.
* Walk-forward groups: FIND_DAILY 60 groups, positive with p <= .10: 3 original, 3 repaired (RTY F5, CL F2, NKD F1, same totals); the repaired F2 (Donchian) refits differ by +$28.9k (GC), +$5.5k (6J), +$44.2k (PORT); DAILY-R6 85 groups, 7 positive with p <= .10 in both (SI F1, HG F1, NG F3, HO F2, ZF F1, ZT F1, 6B F2 with +$6.0k vs +$6.9k, p .066 vs .056); the largest change is ZF F2 (+$12.1k, p .67 -> .50).
#### Labels moved
FIND_DAILY: one: 6J Donchian-60 stop-and-reverse is tolerant on the ORIGINAL bars (13-year net $126.4k, 9 years positive) and NOT on the repaired bars (net $109.2k, 8 years positive, maxDD $51.1k -> $63.5k): best-of-F -> NULL; it was never a family-p candidate (p 1.00 both). Counts: best-of-F 37 -> 36 (the published figure), NULL 282 -> 283, REGIME 89 = 89. DAILY-R6: no tolerant flag moves (14 = 14); two NULL cells (ZT Donchian-20 SAR and EX) become REGIME on the repaired bars; best tolerant family p 0.777 -> 0.776 (A); no LEAD either way.
**Plain sentence: the repair moves 42 of 408 FIND_DAILY cells and 73 of 578 DAILY-R6 cells by more than $1 (up to $17k and $21k over 13 years), but only the Donchian cells (the ones that read daily highs and lows), a handful of closes-based cells and the portfolios built from them; one tolerant flag moves (6J Donchian-60, to NULL), no family p crosses .10, no LEAD appears or disappears, and the frozen CL watch thresholds (K1 $47,782, K2 -$26,761), the CL plateau count and the rates plateau counts are unchanged. Since the published daily results were already computed on the repaired copy, nothing published needs a correction.**
