# DS3_ORBF_B2 - preregistered confirmation of the close-confirmed 1-minute ORBF (DIS-BK, Z2, 2026-11-04). Shadow-watch candidate only; no PASS; nothing live.
Prereg l2vast/ds3/prereg/DISBK_prereg.md sha256 cb3b3f78aee15b8a34959e7ddfb59a3fa5feb692992ffeac32ce0b7e026f7855 (DECISIONS.md, before any number). Ledger DIS_BK (9 cells); DISBK_NTESTED 9. Code l2vast/ds3/code/bg/ (bk_run.py, bk_pre.py, bk_final.py, bk_doc.py, bk_stream.py), streaming class l2vast/ds3/code/zones3/nyam/orbf_b2.py, results /mnt/l2/l2vast/ds3_zones3_new/Z2_bg/. dead_lookup: DIS_BG (my cells), FADE_XI / DIS_AJ / DIS_AG / FADE_GM ORBF rows (per-second ORBF only).
**Candidate (frozen):** B2 = first 1-minute bar CLOSE beyond the 09:30-10:00 range (range from 1-minute bars, >= 20 bars, first bar <= 09:32), from 10:00 to 14:00, fade at that close, stop 60 / target 60 / time stop to 14:00 (ORBF's own, not retuned), 2 lots (study) / 1 lot (register). Provenance: found post hoc in DIS-BG as a variant of the surviving per-second ORBF; ORBF itself came from the T-DISCOVER D family of 346 books; the ORBF family tested here is the fixed set of 5 variants (A, B1, B2, C1, C2); selection N = 346 + 4 = 350.

## Plain sentence
B2 is nearly as good as per-second ORBF after 2023 (L6M +1,799 vs +2,053 a week at 2 lots, HOLD +1,957 vs +1,441, same L6M drawdown) and beats every placebo kind on its own (p 0.005-0.06), and before 2023 its signal-level excess over drift is positive in 7-8 of 10 years; but it fails the preregistered tolerant gate (PRE -$1,403 and X' -$594 a week, like every ORBF variant), once the family of 5 evaluation variants is charged its L6M family p is 0.075-0.119 (HOLD 0.005-0.015), its marginal effect on the live stack is tiny (HOLD Calmar +0.011 at 2 lots, PA9 worst shift -0.002), and after the selection charge the L6M expectation is about +$0.8k to +$1.3k a week instead of +$1.8k; the label is REGIME (NOW-ONLY: L3M and L6M positive, PRE and X' beyond tolerance) / Shadow-watch, not a lead. The streaming rule reproduces the research list with diff 0.

## 1. Post-2023 live fill model, 5 variants (NQ 1-s path 2023-04-03..2026-10-30, 2 lots, gate_v3 windows; $/wk)
| variant | trades | L6M | HOLD | PRE | MID | X' | maxDD L6M | mean pts/trade L6M | tolerant | v2a |
|--|--|--|--|--|--|--|--|--|--|--|
| A 1-s bin high/low (study) | 914 | +2053 | +1441 | -1675 | +1607 | -821 | +11784 | 10.91 | n | n |
| B1 1-min bar high/low (ORBF-M) | 914 | +783 | +717 | -1487 | +1491 | -443 | +18649 | 4.16 | n | n |
| B2 1-min CLOSE beyond (candidate) | 907 | +1799 | +1957 | -1403 | +2988 | -594 | +10964 | 9.64 | n | n |
| C1 5-min bar high/low | 914 | +905 | +392 | -1473 | -1273 | -421 | +18228 | 4.81 | n | n |
| C2 5-min close beyond | 894 | +550 | +569 | -805 | +745 | -345 | +21670 | 3.02 | n | n |

Drawdown first (L6M maxDD at 2 lots): A $11.8k, B1 $18.6k, **B2 $11.0k**, C1 $18.2k, C2 $21.7k; HOLD worst-20 in the CSV. PRE is negative for every variant (B2 -1,403 vs A -1,675): none is a 2023-25 earner at the live fill model.

## 2. Placebos (200 draws per kind; p = share of draws >= real, +1/(N+1); 'family' = max over the 5 variants in the same world; statistic = weekly $ mean)
| placebo kind | statistic | B2 real | placebo median (B2) | B2 own p | B2 family-of-5 p | A own / family | B1 own / family | C1 own / family | C2 own / family |
|--|--|--|--|--|--|--|--|--|--|
| shifted time (shift5) | L6M | +1799 | +448 | 0.060 | 0.114 | 0.010 / 0.065 | 0.179 / 0.667 | 0.045 / 0.582 | 0.428 / 0.816 |
| shifted time (shift5) | HOLD | +1957 | -299 | 0.005 | 0.005 | 0.010 / 0.020 | 0.040 / 0.164 | 0.030 / 0.403 | 0.090 / 0.274 |
| random side | L6M | +1799 | -210 | 0.025 | 0.104 | 0.030 / 0.050 | 0.149 / 0.502 | 0.139 / 0.448 | 0.219 / 0.662 |
| random side | HOLD | +1957 | -146 | 0.010 | 0.010 | 0.010 / 0.040 | 0.090 / 0.308 | 0.174 / 0.577 | 0.154 / 0.438 |
| other-day | L6M | +1799 | -232 | 0.025 | 0.095 | 0.010 / 0.045 | 0.169 / 0.428 | 0.104 / 0.373 | 0.234 / 0.622 |
| other-day | HOLD | +1957 | -176 | 0.015 | 0.015 | 0.010 / 0.035 | 0.109 / 0.303 | 0.159 / 0.562 | 0.124 / 0.423 |
| matched-clock | L6M | +1799 | -347 | 0.030 | 0.119 | 0.010 / 0.065 | 0.159 / 0.468 | 0.164 / 0.418 | 0.199 / 0.567 |
| matched-clock | HOLD | +1957 | -343 | 0.005 | 0.005 | 0.005 / 0.030 | 0.100 / 0.303 | 0.189 / 0.547 | 0.104 / 0.398 |
| true random-minute drift | L6M | +1799 | -30 | 0.025 | 0.075 | 0.015 / 0.035 | 0.124 / 0.333 | 0.085 / 0.279 | 0.209 / 0.458 |
| true random-minute drift | HOLD | +1957 | -264 | 0.005 | 0.005 | 0.015 / 0.025 | 0.075 / 0.244 | 0.184 / 0.438 | 0.134 / 0.333 |

Reading: B2 beats all five nulls on its own at p <= 0.06 in L6M and p <= 0.015 in HOLD; charged for the family of 5 the L6M family p is 0.114 / 0.104 / 0.095 / 0.119 / 0.075 (0.10 threshold missed on 3 of 5 kinds), the HOLD family p is 0.005 / 0.010 / 0.015 / 0.005 / 0.005. The matched-clock null (same days, own entry-time distribution, random side) and the true random-minute drift (random minute of the same day, independent side, own long/short share) are both beaten, so the result is not drift or a clock artefact; the open question is only the family charge in the 27-week L6M window. For comparison the per-second A has own p 0.010 / 0.010 (L6M shift5 / HOLD shift5) and family p 0.065 / 0.020.

## 3. Pre-2023 behaviour (signal-level, V2 convention, owned NQ 1-min 2013-01..2026-10, DIS-AA machinery; 1 lot; next-bar-open fills +0.25, stop slip 1.5; PRE = 2013-01-02..2023-04-02, 488 weeks)
Object caveat: this is the 1-minute approximation (DIS-AA), not the live fill model; post-2023 it is much weaker than the 1-s live model (B2 -1.11 pts/trade post-2023 here vs +9 per trade in the live model's L6M), so pre/post levels are not comparable; the question is the excess over the benchmarks before 2023 (P1c delayed same side, (a) other-day fade, (c) delayed fade; 100 draws each).
| variant | trades pre / post | pts/trade pre / post | $/wk pre / post | years positive excess (P1c / a / c) of 10 | mean weekly excess PRE P1c / a / c ($/wk) | 95% CI lower, upper (P1c / a / c) | weak rule | strong (CI lower > 0) |
|--|--|--|--|--|--|--|--|--|
| B1 1-min bar high/low (ORBF-M) | 2582 / 905 | +0.27 / -5.01 | +29 / -485 | 6 / 7 / 8 | +176 / +198 / +276 | [-13, +350] / [+31, +364] / [+77, +472] | PASS | vs a, c |
| B2 1-min CLOSE beyond (candidate) | 2554 / 898 | +0.61 / -1.11 | +64 / -107 | 7 / 8 / 8 | +170 / +219 / +295 | [-12, +354] / [+48, +389] / [+93, +485] | PASS | vs a, c |
| C1 5-min bar high/low | 2582 / 905 | -0.46 / -3.82 | -49 / -369 | 7 / 7 / 8 | +106 / +48 / +193 | [-65, +278] / [-136, +220] / [-7, +399] | PASS | none |
| C2 5-min close beyond | 2503 / 884 | -0.87 / -2.41 | -90 / -228 | 4 / 5 / 7 | +35 / +59 / +173 | [-140, +216] / [-89, +223] / [-8, +358] | FAIL | none |

### B2 year by year (1 lot, V2 scaled; excess = real weekly $ - benchmark weekly $)
| year | trades | pts/trade | $/wk | excess vs P1c | vs (a) | vs (c) | benchmark pts/trade P1c / a / c |
|--|--|--|--|--|--|--|--|
| 2013 | 245 | +5.43 | +501 | +226 | +552 | +693 | 3.22 / -0.88 / -2.18 |
| 2014 | 246 | +3.76 | +333 | +625 | +443 | +489 | -3.31 / -1.73 / -1.58 |
| 2015 | 249 | +3.12 | +323 | +389 | +307 | +654 | -0.73 / 0.20 / -3.55 |
| 2016 | 252 | -0.30 | -29 | +145 | +75 | +8 | -1.80 / -1.59 / -0.39 |
| 2017 | 252 | -0.38 | -37 | +13 | +79 | +164 | -0.52 / -1.78 / -2.10 |
| 2018 | 252 | +1.06 | +77 | -15 | +309 | +500 | 1.16 / -2.88 / -4.28 |
| 2019 | 242 | +2.93 | +326 | +391 | +501 | +672 | -1.35 / -3.03 / -4.07 |
| 2020 | 253 | -4.24 | -441 | -167 | -169 | -141 | -2.39 / -3.39 / -3.00 |
| 2021 | 251 | -0.19 | -19 | +199 | +316 | +216 | -2.27 / -4.23 / -2.46 |
| 2022 | 250 | -5.07 | -487 | -133 | -252 | -292 | -3.70 / -2.79 / -2.05 |
| 2023 | 251 | -1.99 | -192 | +111 | -143 | -121 | -3.14 / -0.61 / -0.73 |
| 2024 | 255 | -6.06 | -538 | -32 | -118 | -423 | -5.50 / -5.21 / -1.25 |
| 2025 | 253 | -0.49 | -117 | +272 | +222 | +64 | -3.66 / -4.11 / -1.82 |
| 2026 | 201 | +6.38 | +656 | +715 | +877 | +724 | -0.71 / -2.45 / -0.69 |

B2 passes the DIS-AA weak pre-2023 rule against all three benchmarks (positive in 7 / 8 / 8 of the 10 pre-2023 years; CIs upper limits > 0) and the strong version (CI lower > 0) against (a) other-day fade and (c) delayed fade, not against P1c (CI [-12, +354]). B1 (the 1-min high/low version) passes the same way; C1 and C2 do not pass the strong version and C2 fails vs P1c. As in DIS-AA, the excess is partly because the benchmarks themselves lose before 2023; the raw B2 mean before 2023 is only +0.61 pt per trade (+$58/wk at 1 lot).

## 4. Stack marginal on the live Q1-A ts2 stack (carrying weeks dropped, corrected constants; Calmar change from adding the series; genuine PA9 = scoring week-key shift -4..+4)
| variant | lots | HOLD Calmar change | HOLD maxDD change | HOLD mean change | L6M Calmar change | L6M maxDD change | PRE Calmar change | PA9 HOLD min / median | PA9 L6M min / median |
|--|--|--|--|--|--|--|--|--|--|
| A | 2 | -0.010 | +12805 | +1582 | +0.104 | -4588 | -0.021 | -0.020 / -0.007 | +0.071 / +0.227 |
| A | 1 | -0.005 | +6563 | +815 | +0.051 | -2332 | -0.005 | -0.010 / -0.003 | +0.034 / +0.101 |
| B1 | 2 | +0.002 | +3204 | +923 | +0.079 | -4613 | -0.019 | -0.025 / -0.003 | +0.049 / +0.189 |
| B1 | 1 | +0.001 | +1665 | +465 | +0.038 | -2332 | -0.006 | -0.008 / +0.000 | +0.023 / +0.085 |
| B2 | 2 | +0.011 | +2979 | +2037 | +0.089 | -4658 | -0.004 | -0.002 / +0.010 | +0.059 / +0.206 |
| B2 | 1 | +0.005 | +1665 | +1013 | +0.042 | -2332 | +0.002 | -0.002 / +0.005 | +0.028 / +0.093 |
| C1 | 2 | -0.018 | +13565 | +588 | +0.158 | -9501 | -0.026 | -0.048 / -0.018 | +0.091 / +0.308 |
| C1 | 1 | -0.009 | +6563 | +302 | +0.073 | -4781 | -0.012 | -0.021 / -0.009 | +0.043 / +0.134 |
| C2 | 2 | +0.005 | -809 | +381 | +0.126 | -9501 | -0.028 | -0.007 / +0.004 | -0.001 / +0.046 |
| C2 | 1 | +0.003 | -784 | +204 | +0.058 | -4781 | -0.013 | -0.003 / +0.003 | -0.000 / +0.023 |

B2 at 2 lots adds +$2,037/wk to the HOLD mean with a HOLD Calmar change of only +0.011 (the stack's HOLD maxDD rises by $2,979); L6M Calmar +0.089, maxDD lower by $4,658; PRE Calmar -0.004. PA9 over the nine week-key shifts: HOLD min -0.002 / median +0.010 (not positive at the worst shift), L6M min +0.059. At the register's 1 lot the numbers are half. The marginal value is small and mixed in sign in HOLD; the stack gain is not a reason to prefer B2 over A (A: HOLD Calmar -0.010 at 2 lots).

## 5. Streaming reproduction (Shadow pack)
`orbf_b2.py` (class OrbFadeB2, on_minute, O(1) state) vs the research list, fields signal_sec / side / stop_pts / tgt_pts / tstop_s: (a) research bars 2023-04..2026-10: 907 / 907 rows, diff 0 (0 only-research, 0 only-streaming); (b) the 2013-2026 1-minute history: 3,452 / 3,452, diff 0 against the independently coded vector generator; (c) bars rebuilt from the raw 1-s path with the live print-time minute convention (minute = timestamp // 60): 907 / 907 matched, diff 0 (2-lot L6M +1,799 / HOLD +1,957 / PRE -1,403); with the alternative one-second-shifted minute convention ((timestamp - 1) // 60) only 749 of 907 signals match (158 only-research, 156 only-streaming; L6M +1,832 / HOLD +1,521): the rule is sensitive to the 1-s clock convention at the bar boundary on about 17% of signals, so D7's bar definition must follow the live print-time convention exactly. Log fields as NYAM_SHADOW_SPEC section 5 (book ORBF_B2, session nyam, flags: range_high, range_low, break_close).


## 6. Selection-deflated expectation
Selection count: ORBF came from 346 books (DISCOVER_D); the family tested here is 5 variants; N = 350. Bonferroni with N = 350 cannot be met by 200 draws (smallest possible p 0.005 -> 1.0), so the honest tools are the null maxima (weekly $, family-of-5 maximum per world):
| null | L6M median / 95th pct of the family max | HOLD median / 95th pct |
|--|--|--|
| shifted time (shift5) | +1044 / +2106 | +282 / +962 |
| random side | +780 / +2040 | +467 / +1372 |
| other-day | +697 / +2031 | +485 / +1268 |
| matched-clock | +724 / +2073 | +423 / +1340 |
| true random-minute drift | +479 / +1896 | +276 / +1063 |

B2 minus the family-max null median: under the true random-minute drift L6M +1320, HOLD +1681; under the shifted-time null L6M +756, HOLD +1675 (the shifted-time deflation is the more demanding one for L6M). B2 minus the family-max null 95th percentile (drift): L6M -97, HOLD +894. Read: the selection charge removes about $0.5k (drift) to $1.0k (shifted time) of the L6M +1799 a week, leaving roughly +1320 to +756 at 2 lots in L6M, and +1681 to +1675 in HOLD after the null maxima. These are in-sample deflations on the 187-week window; PRE is negative for every variant.

## 7. Label and use
Preregistered LEAD criteria: TOLERANT + gate_v2a: B2 tolerant = n, v2a = n (reason: PRE -1403 and X' -594 a week against MDEs of +1689 and +1941); all five placebo p <= 0.10 on L6M and HOLD: own p <= 0.06 yes; family-of-5 p <= 0.10: L6M fails on 3 of 5 kinds (range 0.075-0.119), HOLD passes (<= 0.015); pre-2023 weak rule: passes. Label: **REGIME (NOW-ONLY) / Shadow-watch (not a lead; it does not reach the best-of-F tier because the tolerant gate fails)**; CONFIRMED is not reached (PA9 HOLD min -0.002, stack HOLD Calmar +0.011 at best).
For the user's decision item (can ORBF be evaluated every second live): if D7 can act only at 1-minute closes, B2 is the version to register as ORBF-M2 (shadow-only; streaming class diff 0); in this sample it keeps most of the per-second ORBF's dollars, but it is a post-hoc variant of a 2026-weighted line and its pre-2023 evidence is the 1-minute signal-level object only. No PASS; nothing live.
