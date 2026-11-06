# DATA_BAD_PRINTS.md - bad-print audit of the owned 1-minute series (CHAR-C, 2026-11-06, lead request). Research only; originals untouched.

Rule (cc_audit.py, prereg FIND_C_scope_addendum3.md; sha256 in DECISIONS.md before the scan): a 1-min bar with confirmed neighbours (t-1 and t+1 one minute away, same instrument id) is BAD if its close, high or low lies outside [min(c_prev, c_next, open) - K, max(c_prev, c_next, open) + K], K = 10 sigma + 4 ticks, sigma = 1.4826 x median |close change| of the previous 240 bars. Source: cache_te2 (.v.0 front-month 1-min = the ohlcv1m / t4 files). Repair = clamp o/h/l/c into the band (persistent moves are never touched because the next close confirms them). Repaired copies for all 13: /mnt/l2/l2vast/find_c/cache_c/<SYM>.npz (the rule was applied to every instrument; only 6E and 6J exceed the 0.5% threshold).

## Bad-bar share (% of bars) per instrument-year
| year | ES | NQ | RTY | YM | GC | CL | ZN | ZB | 6E | 6J | NKD | BTC | MBT |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 2013 | 0.004 | 0.007 | - | 0.009 | 0.038 | 0.011 | 0.012 | 0.015 | **1.83** | **2.01** | 0.004 | - | - |
| 2014 | 0.006 | 0.012 | - | 0.006 | 0.045 | 0.011 | 0.022 | 0.016 | **1.89** | **1.15** | 0.006 | - | - |
| 2015 | 0.009 | 0.018 | - | 0.013 | 0.034 | 0.012 | 0.017 | 0.012 | **2.08** | **0.96** | 0.009 | - | - |
| 2016 | 0.003 | 0.016 | - | 0.006 | 0.038 | 0.012 | 0.010 | 0.011 | 0.023 | 0.037 | 0.012 | - | - |
| 2017 | 0.005 | 0.025 | 0.014 | 0.009 | 0.034 | 0.015 | 0.008 | 0.014 | 0.017 | 0.018 | 0.006 | - | - |
| 2018 | 0.004 | 0.012 | 0.016 | 0.010 | 0.017 | 0.012 | 0.007 | 0.009 | 0.013 | 0.011 | 0.001 | - | - |
| 2019 | 0.014 | 0.031 | 0.028 | 0.023 | 0.022 | 0.011 | 0.010 | 0.012 | 0.018 | 0.017 | 0.009 | - | - |
| 2020 | 0.129 | 0.108 | 0.019 | 0.066 | 0.024 | 0.011 | 0.005 | 0.008 | 0.008 | 0.012 | 0.001 | - | - |
| 2021 | 0.008 | 0.020 | 0.013 | 0.012 | 0.025 | 0.005 | 0.012 | 0.013 | 0.008 | 0.006 | 0.001 | - | - |
| 2022 | 0.018 | 0.023 | 0.021 | 0.018 | 0.024 | 0.005 | 0.006 | 0.009 | 0.012 | 0.030 | 0.004 | 0.018 | 0.012 |
| 2023 | 0.017 | 0.025 | 0.030 | 0.023 | 0.030 | 0.007 | 0.022 | 0.025 | 0.018 | 0.037 | 0.004 | 0.037 | 0.013 |
| 2024 | 0.017 | 0.023 | 0.043 | 0.035 | 0.022 | 0.005 | 0.019 | 0.023 | 0.018 | 0.043 | 0.007 | 0.015 | 0.010 |
| 2025 | 0.026 | 0.028 | 0.041 | 0.034 | 0.016 | 0.015 | 0.015 | 0.019 | 0.021 | 0.016 | 0.009 | 0.005 | 0.007 |
| 2026 | 0.022 | 0.017 | 0.028 | 0.031 | 0.021 | 0.024 | 0.013 | 0.012 | 0.016 | 0.049 | 0.005 | 0.006 | 0.016 |

## Bad-bar counts and totals
| instrument | bars | bad bars | bad close (isolated spike close) | share % | worst year (share %) |
|--|--|--|--|--|--|
| ES | 4819789 | 979 | 247 | 0.0203 | 2020 (0.129) |
| NQ | 4729577 | 1257 | 262 | 0.0266 | 2020 (0.108) |
| RTY | 3067540 | 801 | 162 | 0.0261 | 2024 (0.043) |
| YM | 4710231 | 995 | 199 | 0.0211 | 2020 (0.066) |
| GC | 4784485 | 1334 | 144 | 0.0279 | 2014 (0.045) |
| CL | 4787820 | 523 | 51 | 0.0109 | 2026 (0.024) |
| ZN | 4451650 | 565 | 97 | 0.0127 | 2014 (0.022) |
| ZB | 4133041 | 583 | 89 | 0.0141 | 2023 (0.025) |
| 6E | 4730908 | 19721 | 2215 | 0.4169 | 2015 (2.081) |
| 6J | 4715000 | 14455 | 2131 | 0.3066 | 2013 (2.007) |
| NKD | 3284254 | 189 | 44 | 0.0058 | 2016 (0.012) |
| BTC | 1132723 | 185 | 23 | 0.0163 | 2023 (0.037) |
| MBT | 1228991 | 138 | 18 | 0.0112 | 2026 (0.016) |

## Reading
* Only 6E and 6J are affected, and only 2013-2015 (6E 1.8-2.1% of bars per year, 6J 1.0-2.0%; 2016 onward 0.01-0.05%, the same level as every other instrument). The bad bars are isolated prints in the high/low/close (volume present, same instrument id, reverting next bar): 6E 2015-06-02 10:07 low/close 1.0935 against neighbours near 1.1135 (a 200-pip print), 6E 2015-01-23 08:01 is NOT one (a persistent 175-pip move, the ECB QE reaction, untouched by the rule).
* ES, NQ, RTY, YM, GC, CL, ZN, ZB, NKD, BTC, MBT: worst year 0.13% (ES 2020, NQ 0.11% 2020, YM 0.07% 2020: the March-2020 limit moves, mostly genuine) and 0.00-0.05% elsewhere; no repair is needed for any 2016+ result, and 2013-2015 for these instruments is clean.
* The recents windows (2023-04 onward) are not affected for any instrument (6E/6J 2023-26 bad share 0.016-0.049%).

## Which earlier results used the affected 6E/6J years, and what the repaired re-run says
All re-runs use the same code and parameters with only the bar file swapped to the repaired copy (copies rep_*.py in code/find_c; original pickles untouched, new files *_repaired.pkl).

| result | where | re-run | change |
|--|--|--|--|
| ZL-1 stage 3, 13-year percent-frame check of the 30 stage-2 finalists, 6E | DS3_INSTR2_6E.md section 'Stage 3' | rep_t2_stage3.py | mean $/trade >0 in 0 of 30 before and after; majority-positive years 0 -> 1 cell; negative-every-year 3 -> 3; median mean/trade -78 -> -60. Verdict unchanged (no 6E book). |
| same, 6J | DS3_INSTR2_6J.md | rep_t2_stage3.py | mean $/trade >0 in 1 -> 0 of 30; majority-positive years 0 -> 0; median -35.5 -> -34.3. Unchanged. |
| ZL-1 ALLINST 13-year yearly tables (top 30 tolerant cells), 6E | DS3_INSTR2_ALLINST.md | rep_allinst_y13.py | mean $/trade >0 in 0 -> 0; negative-every-year 17 -> 17; max years positive 2 -> 2. Unchanged. |
| same, 6J | DS3_INSTR2_ALLINST.md | rep_allinst_y13.py | mean $/trade >0 in 1 -> 0; negative-every-year 2 -> 2; majority-positive years 0 -> 2 cells. Unchanged verdict (no lead). |
| ZL-2 block B 'pre-2023 years (+/n)' column, 6E (90 tolerant cells re-run) | DS3_INSTR2_6E_B.md | rep_blockB.py | negative-every-year 4 -> 2; majority-positive years 1 -> 6 cells; median pre-2023 total -$33.5k -> -$18.9k; 5 cells (all prior-day-high/low BREAK in the 08:30-09:30 pre-market) turn from -$17k...-$42k to about break-even (-$8k...+$5k) over 10 years. FLAGGED: the 'negative before 2023' / REGIME reading of those cells is withdrawn; their formal verdict (family p 1.00, gate_v2a False, HOLD -85...+27 per week, X' negative) is unchanged because the 2023-26 windows are unaffected. |
| same, 6J (72 tolerant cells re-run) | DS3_INSTR2_6J_B.md | rep_blockB.py | negative-every-year 15 -> 16; majority-positive 0 -> 0; median pre-2023 total -$59.5k -> -$65.2k; no cell turns positive. Unchanged. |
| CHAR-C maps and books 6E/6J | DS3_FIND_CHARACTER.md, DS3_FIND.md | built on the repaired copy from the start | n/a |
| T-INSTR transfer / INSTR_RF/CM (6E U7), Z3 stage A, ZL-1 T2_6E/T2_6J stage 1/2 | WHAT_IS_DEAD, DS3_INSTR2_6E/6J | not re-run | those scored 2023-04..2026-10 windows (unaffected); only their 13-year addenda are listed above. T2_6E/6J stage-1 cells start 2022-01 in the grid code (T0), so 2013-2015 never entered them. |

## Flagged for owners
ZL-2 (6E block B): re-read the pre-2023 columns of the nine prior-day-break pre-market cells (list in /mnt/l2/l2vast/find_c/blockB_repaired_6E.pkl); suggested follow-up is an evaluate() run of the best of them (pdhl_break, rth 570-960, x .25, pre-market, stop 4 ATR, no target: L6M +281, HOLD +27, PRE +141, X' -85, pre-2023 total about +$2.9k, 5 of 10 years positive), since it matches the CHAR-C map reading that breaks of prior-day levels stick in 6E. No verdict has been changed by this audit.
