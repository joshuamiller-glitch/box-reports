# WHAT_MOVES_NQ_BREADTH: does NYSE breadth (TICK, TICKQ, ADD, ADV share, DVOL, TRIN, TRINQ, PCR) lead NQ at 1-60 minutes? DISCOVERY, NOT A RESULT
Generated 2026-11-28T15:12Z. Order: relay 14:42Z. Label: DISCOVERY; it only feeds which feeds sit on which desk seat. Code: code/th_dynl/wm_br_run.py (lead/lag, reuses wm_run null machinery and wm1s_agg.py for BH/labels/half-years), wm_br_turns.py (turns). Derived counts: /dev/shm only plus the JSONs copied to /mnt/l2/l2vast/_dynexit/wm_breadth/. Ran on box 1 at nice 19 (small: 2.1M-minute arrays), not server C.

## ANSWER FIRST
Months covered by EVERY row below: 2023-02 .. 2026-10 (45 months; NQ 1-s feed starts 2023-02 so 2023-01 internals are unused; ^VIX has only 6 weeks and is not tested). Fit = first 27 months (2023-02..2025-04), judge = last 18 (2025-05..2026-10); half-years: 2023H1 = Feb-Jun, ..., 2026H2 = Jul-Oct. Internals exist only 09:31-16:00 ET, so only NY AM and NY PM can be scored (Asia/London not testable). 85 feed-window rows x 1-2 horizons x 2 sessions x 2 variants = 611 grid cells, BH over all.

1. DOES BREADTH LEAD NQ AT 1-60 MINUTES? NO, in neither session. Of 611 grid cells 0 reach BH q <= 0.10 (smallest q 0.30). Selected-on-fit rows judged once: 0 STEADY LEADER, 0 BH-significant. The cleanest-looking cell, TICK extreme count over 1 min then NQ over 60 min in NY AM, is +15.3 pp (z 3.3) but on only 228 fires, absent in 4 of 8 half-years and BH q 0.30 = luck-compatible. Breadth moves WITH NQ in the same window (15-min correlation NY PM: ADD slope +0.68, ADV share slope +0.67, DVOL slope -0.64, TICK level +0.53; NY AM 0.2-0.4), so it is a confirmation/regime gauge for the NY seats, not an early warning.
2. DO TICK EXTREMES LEAD NQ TURNS? NO (after control). Naive study: in NY PM 45% of NQ turns (1,907 turns total over 45 months from 3-sigma 15-min runs with >= 40% give-back) have a TICK high/low extreme (98th pct of fit bars, |TICK| >= 694) in the 10 minutes before the NQ extreme versus 15% for random NQ-window extremes (z 13, positive all half-years, shrinking 2023H1 +54 pp to 2026H2 +5 pp). That is CONFOUNDED: TICK extremes accompany big runs, and random windows have no run. The controlled test, among all 3,415 three-sigma runs, asks whether a TICK extreme in the run direction in the 10 minutes up to detection changes the share that go on to turn: NY AM +3.0 pp (z 0.9), NY PM -1.0 pp (z -0.3); TICKQ +2.2 pp (z 0.7) and -3.2 pp (z -1.0). So extremes tell you a run is under way, not that it turns. Lead-time study (does the feed's own turn precede NQ's turn): best rows TICKQ-extreme NY AM +4.5 pp (z 1.8), TICK-extreme NY AM +4.0 pp (z 1.3); nothing at z >= 2.

Plain statement: nothing in the breadth set leads NQ at 1-60 minutes or its turns. All numbers below are for the record.

## 1. Method (as WHAT_MOVES_NQ.md, on a minute grid)
- Feeds per window w = 1/5/15/30/60 min: _lvl = mean over w (deviation from its own previous-3600-minute mean, in sigma), _slope = change over w, _ext (TICK, TICKQ) = number of minutes with an extreme high (bar high >= 98th percentile of |high|,|low| on the fit months: TICK 694, TICKQ 663) minus extreme lows over w. ADV share = ADV/(ADV+DECL-like) from the feed file; TRIN, TRINQ in log. FIRE at >= 2 sigma; NQ-FLAT variant = NQ itself moved < 0.5 sigma over the same w. Outcome: NQ return over the next h = w and h = 60 min; HIT = same sign as the feed (sign fixed on the first 60% of months from same-moment covariance); refractory max(w,h); MATCHED NULL = same fires scored against NQ outcomes 30-120 minutes later; edge = hit minus null; BH over all cells; labels as in wm1s_agg.py (STEADY needs >= 3 half-years with >= 200 fires, edge >= 1 pp, q <= 0.10, positive L3M and L6M).
- LOOK-AHEAD CHECK: the feed 'sec' is bar END + 5 s (bar complete at its stamp). The decision time is second 60*m+5 of the bar-end minute m; NQ price at decision = last NQ mid at or before that second (<= 120 s stale); outcomes are strictly later. Same-moment correlations are measured on the same stamp, so they are NOT lead evidence.
- Turns: wm_br_turns.py, definitions in its docstring (3-sigma 15-min run, >= 40% give-back within 15 min, NY AM/PM only).

## 2. Best cells by BH q (whole window, NQ-FLAT and all fires; the top of the grid)
| feed | session | variant | w | h | fires | edge pp | z | BH q | by half-year edge pp |
|---|---|---|---|---|---|---|---|---|---|
| TICK_ext | NY AM | nqflat | 1 | 60 | 228 | +15.3 | 3.3 | 0.300 | 23H1 +10.7 / 23H2 +20.0 / 24H1 +9.4 / 24H2 na / 25H1 +24.3 / 25H2 na / 26H1 na / 26H2 na |
| ADD_lvl | NY AM | all | 1 | 1 | 32522 | +0.2 | 0.5 | 0.911 | 23H1 -0.7 / 23H2 +0.8 / 24H1 -1.0 / 24H2 -1.2 / 25H1 -0.3 / 25H2 -0.3 / 26H1 +1.6 / 26H2 +2.5 |
| ADD_lvl | NY PM | all | 1 | 1 | 10271 | +1.3 | 1.8 | 0.911 | 23H1 +2.2 / 23H2 +3.4 / 24H1 +3.0 / 24H2 +5.1 / 25H1 -1.6 / 25H2 -0.7 / 26H1 +2.3 / 26H2 -2.8 |
| ADD_lvl | NY AM | nqflat | 1 | 1 | 7607 | +1.2 | 1.5 | 0.911 | 23H1 -0.4 / 23H2 +1.4 / 24H1 -0.1 / 24H2 +0.5 / 25H1 +2.1 / 25H2 +1.7 / 26H1 +1.5 / 26H2 +2.2 |
| ADD_lvl | NY PM | nqflat | 1 | 1 | 3201 | +0.6 | 0.5 | 0.911 | 23H1 +6.2 / 23H2 +6.6 / 24H1 +0.4 / 24H2 +8.9 / 25H1 -3.4 / 25H2 -3.0 / 26H1 -2.2 / 26H2 -6.0 |
| ADD_lvl | NY AM | all | 1 | 60 | 912 | +1.5 | 0.7 | 0.911 | 23H1 +8.0 / 23H2 +0.4 / 24H1 +0.6 / 24H2 +5.6 / 25H1 -6.5 / 25H2 +2.0 / 26H1 -5.4 / 26H2 +9.1 |
| ADD_lvl | NY PM | all | 1 | 60 | 272 | +2.3 | 0.5 | 0.911 | 23H1 na / 23H2 na / 24H1 +5.0 / 24H2 na / 25H1 -6.6 / 25H2 +4.8 / 26H1 na / 26H2 na |
| ADD_lvl | NY AM | nqflat | 1 | 60 | 793 | +1.5 | 0.6 | 0.911 | 23H1 -0.7 / 23H2 +0.9 / 24H1 -0.7 / 24H2 +7.8 / 25H1 -3.6 / 25H2 +4.9 / 26H1 -4.6 / 26H2 +7.6 |
| ADD_lvl | NY PM | nqflat | 1 | 60 | 231 | +5.5 | 1.1 | 0.911 | 23H1 na / 23H2 na / 24H1 na / 24H2 na / 25H1 -14.3 / 25H2 na / 26H1 na / 26H2 na |
| ADD_lvl | NY PM | all | 5 | 5 | 2212 | +1.6 | 1.1 | 0.911 | 23H1 +1.1 / 23H2 +7.1 / 24H1 +5.3 / 24H2 +5.4 / 25H1 -0.1 / 25H2 -1.8 / 26H1 -1.0 / 26H2 -3.6 |
| ADD_lvl | NY AM | nqflat | 5 | 5 | 3440 | +0.5 | 0.4 | 0.911 | 23H1 -1.3 / 23H2 +1.8 / 24H1 -2.8 / 24H2 +0.1 / 25H1 -0.6 / 25H2 -0.3 / 26H1 -0.9 / 26H2 +7.1 |
| ADD_lvl | NY PM | nqflat | 5 | 5 | 1310 | +1.8 | 0.9 | 0.911 | 23H1 +1.5 / 23H2 +12.0 / 24H1 +0.4 / 24H2 +12.2 / 25H1 -4.0 / 25H2 +0.1 / 26H1 +0.0 / 26H2 -4.4 |
| ADD_lvl | NY AM | all | 5 | 60 | 881 | +2.1 | 0.9 | 0.911 | 23H1 -8.2 / 23H2 +6.2 / 24H1 -0.4 / 24H2 +4.9 / 25H1 -0.7 / 25H2 +3.4 / 26H1 -2.7 / 26H2 +11.8 |
| ADD_lvl | NY PM | all | 5 | 60 | 265 | +6.1 | 1.3 | 0.911 | 23H1 na / 23H2 na / 24H1 na / 24H2 na / 25H1 -2.5 / 25H2 +9.9 / 26H1 na / 26H2 na |
| ADD_lvl | NY AM | nqflat | 5 | 60 | 769 | +3.2 | 1.3 | 0.911 | 23H1 +4.1 / 23H2 +2.5 / 24H1 -3.7 / 24H2 +12.7 / 25H1 -3.2 / 25H2 -1.4 / 26H1 +8.9 / 26H2 +7.4 |
| ADD_lvl | NY PM | nqflat | 5 | 60 | 230 | -0.7 | -0.1 | 0.911 | 23H1 na / 23H2 na / 24H1 na / 24H2 na / 25H1 -17.3 / 25H2 na / 26H1 na / 26H2 na |
| ADD_lvl | NY AM | all | 15 | 15 | 2446 | +0.9 | 0.7 | 0.911 | 23H1 -1.0 / 23H2 +0.5 / 24H1 -5.1 / 24H2 +1.3 / 25H1 -1.8 / 25H2 +1.0 / 26H1 +5.0 / 26H2 +7.4 |
| ADD_lvl | NY PM | all | 15 | 15 | 821 | +3.8 | 1.5 | 0.911 | 23H1 +8.2 / 23H2 +2.8 / 24H1 -3.6 / 24H2 +19.1 / 25H1 -1.5 / 25H2 +5.2 / 26H1 +13.4 / 26H2 -7.5 |
| ADD_lvl | NY AM | nqflat | 15 | 15 | 1510 | +1.3 | 0.7 | 0.911 | 23H1 -4.5 / 23H2 +1.2 / 24H1 -7.5 / 24H2 +2.0 / 25H1 -1.7 / 25H2 +4.1 / 26H1 +1.3 / 26H2 +13.8 |
| ADD_lvl | NY PM | nqflat | 15 | 15 | 572 | +2.7 | 0.9 | 0.911 | 23H1 -7.0 / 23H2 +5.7 / 24H1 +4.2 / 24H2 +12.7 / 25H1 -2.5 / 25H2 +1.4 / 26H1 +12.1 / 26H2 -7.2 |
| ADD_lvl | NY AM | all | 15 | 60 | 844 | +0.3 | 0.1 | 0.911 | 23H1 +0.0 / 23H2 -3.1 / 24H1 -2.2 / 24H2 +11.3 / 25H1 -5.4 / 25H2 -2.5 / 26H1 -7.2 / 26H2 +13.0 |
| ADD_lvl | NY PM | all | 15 | 60 | 253 | +7.5 | 1.6 | 0.911 | 23H1 na / 23H2 na / 24H1 +11.8 / 24H2 na / 25H1 +1.2 / 25H2 +11.5 / 26H1 na / 26H2 na |
| ADD_lvl | NY AM | nqflat | 15 | 60 | 690 | +3.6 | 1.3 | 0.911 | 23H1 +11.4 / 23H2 -0.5 / 24H1 -5.9 / 24H2 +11.5 / 25H1 -7.2 / 25H2 +7.8 / 26H1 +3.0 / 26H2 +11.9 |
| ADD_lvl | NY PM | nqflat | 15 | 60 | 218 | +5.5 | 1.1 | 0.911 | 23H1 na / 23H2 na / 24H1 na / 24H2 na / 25H1 na / 25H2 na / 26H1 na / 26H2 na |
| ADD_lvl | NY AM | all | 30 | 30 | 1312 | +2.9 | 1.5 | 0.911 | 23H1 +4.1 / 23H2 +1.0 / 24H1 -4.1 / 24H2 +7.7 / 25H1 -3.9 / 25H2 +2.9 / 26H1 +1.2 / 26H2 +15.2 |

## 3. Selected on fit months, judged once on the last 18 months (NQ-FLAT variant, all non-NEVER labels)
| feed | session | w | h | fires/mo | edge pp | z | q | L3M | L6M | by half-year | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ADD_lvl | NY AM | 5 | 60 | 17 | +4.0 | 1.0 | 0.84 | +4.5 | +6.5 | 23H1 +4.1 / 23H2 +2.5 / 24H1 -3.7 / 24H2 +12.7 / 25H1 -3.2 / 25H2 -1.4 / 26H1 +8.9 / 26H2 +7.4 | SOMETIMES (noise level, q>0.10) |
| ADVSH_lvl | NY AM | 1 | 60 | 19 | +3.7 | 1.0 | 0.84 | +21.2 | +8.1 | 23H1 +0.7 / 23H2 +2.3 / 24H1 -5.1 / 24H2 +14.8 / 25H1 -1.5 / 25H2 +2.7 / 26H1 -2.0 / 26H2 +13.7 | SOMETIMES (noise level, q>0.10) |
| ADVSH_slope | NY AM | 30 | 60 | 10 | +8.2 | 1.5 | 0.84 | +2.6 | +2.6 | 23H1 +2.9 / 23H2 +7.7 / 24H1 +9.8 / 24H2 +9.4 / 25H1 +5.0 / 25H2 +23.2 / 26H1 -1.6 / 26H2 +0.0 | SOMETIMES (noise level, q>0.10) |
| DVOL_slope | NY AM | 15 | 60 | 13 | +4.5 | 1.0 | 0.84 | +5.0 | +11.0 | 23H1 +8.6 / 23H2 +6.2 / 24H1 -3.8 / 24H2 +9.9 / 25H1 -0.7 / 25H2 +2.9 / 26H1 +10.0 / 26H2 +9.8 | SOMETIMES (noise level, q>0.10) |
| PCR_lvl | NY AM | 1 | 60 | 12 | +3.2 | 0.7 | 0.84 | +1.2 | +1.2 | 23H1 +9.6 / 23H2 +8.4 / 24H1 +5.4 / 24H2 +7.2 / 25H1 +6.0 / 25H2 -0.7 / 26H1 -6.2 / 26H2 +5.3 | SOMETIMES (noise level, q>0.10) |
| PCR_slope | NY AM | 1 | 60 | 12 | +4.8 | 1.0 | 0.84 | +0.0 | +6.4 | 23H1 -5.6 / 23H2 -4.1 / 24H1 +1.7 / 24H2 +17.8 / 25H1 +2.5 / 25H2 -2.2 / 26H1 +6.5 / 26H2 +6.1 | SOMETIMES (noise level, q>0.10) |
| TICKQ_ext | NY AM | 1 | 1 | 22 | +3.3 | 0.9 | 0.84 | -2.4 | +1.9 | 23H1 -4.5 / 23H2 +4.4 / 24H1 +4.2 / 24H2 +12.2 / 25H1 +5.6 / 25H2 +6.6 / 26H1 +2.7 / 26H2 +5.5 | SOMETIMES (noise level, q>0.10) |
| TICK_slope | NY AM | 15 | 60 | 12 | +5.7 | 1.2 | 0.84 | +3.6 | +8.0 | 23H1 +8.9 / 23H2 -1.0 / 24H1 +9.1 / 24H2 +0.7 / 25H1 +21.2 / 25H2 +3.9 / 26H1 +9.9 / 26H2 +1.7 | SOMETIMES (noise level, q>0.10) |
| TRINQ_slope | NY AM | 1 | 60 | 18 | +1.0 | 0.2 | 0.92 | +0.0 | +0.8 | 23H1 +5.4 / 23H2 -1.2 / 24H1 +13.0 / 24H2 -0.2 / 25H1 +9.3 / 25H2 -0.7 / 26H1 -3.9 / 26H2 +4.1 | SOMETIMES (noise level, q>0.10) |
| TICKQ_slope | NY PM | 1 | 1 | 34 | +0.8 | 0.3 | 0.92 | +7.5 | +2.5 | 23H1 +5.6 / 23H2 +2.1 / 24H1 +2.3 / 24H2 +10.6 / 25H1 +6.7 / 25H2 -4.0 / 26H1 -5.2 / 26H2 +11.1 | SOMETIMES (noise level, q>0.10) |

Label counts (all variants): {'SOMETIMES (noise level, q>0.10)': 18, 'NEVER': 49}

## 4. Same moment (15-min window, correlation with NQ)
| session | top feeds |
|---|---|
| NY AM | DVOL_slope -0.40, TICKQ_lvl 0.37, ADD_slope 0.36, TICKQ_slope 0.35, ADVSH_slope 0.34, TICK_lvl 0.33, TICKQ_ext 0.27, TICK_slope 0.23, TICK_ext 0.22, PCR_slope -0.20 |
| NY PM | ADD_slope 0.68, ADVSH_slope 0.67, DVOL_slope -0.64, TICK_lvl 0.53, TICKQ_lvl 0.50, TICK_ext 0.49, TICKQ_ext 0.46, TICKQ_slope 0.43, TRIN_slope -0.35, TICK_slope 0.30 |

## 5. Turns
### 5a. Naive TICK/TICKQ extreme before NQ turn vs random NQ-window extremes (CONFOUNDED, see answer 2)
| feed | session | turns | with extreme | null | diff pp | z | by half-year diff pp (n) |
|---|---|---|---|---|---|---|---|
| TICK | NY AM | 1105 | 0.110 | 0.073 | +3.7 | 3.3 | 23H1 +19 (125) / 23H2 +7 (162) / 24H1 +1 (138) / 24H2 +5 (172) / 25H1 +9 (124) / 25H2 -3 (155) / 26H1 -2 (140) / 26H2 -7 (89) |
| TICK | NY PM | 550 | 0.449 | 0.153 | +29.6 | 13.3 | 23H1 +54 (71) / 23H2 +33 (78) / 24H1 +32 (88) / 24H2 +22 (80) / 25H1 +32 (76) / 25H2 +24 (73) / 26H1 +16 (55) / 26H2 +5 (29) |
| TICKQ | NY AM | 1105 | 0.176 | 0.118 | +5.9 | 4.3 | 23H1 +5 (125) / 23H2 -2 (162) / 24H1 -2 (138) / 24H2 +5 (172) / 25H1 +8 (124) / 25H2 +9 (155) / 26H1 +21 (140) / 26H2 +3 (89) |
| TICKQ | NY PM | 550 | 0.482 | 0.173 | +30.9 | 13.8 | 23H1 +35 (71) / 23H2 +26 (78) / 24H1 +25 (88) / 24H2 +21 (80) / 25H1 +35 (76) / 25H2 +33 (73) / 26H1 +44 (55) / 26H2 +34 (29) |

### 5b. CONTROLLED: among all 3-sigma 15-min runs, share that turn with vs without a same-direction TICK extreme in the preceding 10 min
| feed | session | runs | with extreme | P(turn|ext) | P(turn|no ext) | diff pp | z | by half-year diff pp (n with ext) |
|---|---|---|---|---|---|---|---|---|
| TICK | NY AM | 1773 | 234 | 0.611 | 0.581 | +3.0 | 0.9 | 23H1 -2 (72) / 23H2 -2 (47) / 24H1 -1 (23) / 24H2 +12 (29) / 25H1 +14 (28) / 25H2 +10 (16) / 26H1 +6 (15) |
| TICK | NY PM | 1024 | 512 | 0.523 | 0.533 | -1.0 | -0.3 | 23H1 -1 (84) / 23H2 +5 (90) / 24H1 -13 (99) / 24H2 +5 (64) / 25H1 +6 (76) / 25H2 -2 (51) / 26H1 +0 (37) / 26H2 +5 (11) |
| TICKQ | NY AM | 1773 | 327 | 0.602 | 0.581 | +2.2 | 0.7 | 23H1 -1 (43) / 23H2 +1 (27) / 24H1 +5 (26) / 24H2 +7 (42) / 25H1 +4 (45) / 25H2 -3 (40) / 26H1 -0 (72) / 26H2 +3 (32) |
| TICKQ | NY PM | 1024 | 515 | 0.513 | 0.544 | -3.2 | -1.0 | 23H1 -13 (62) / 23H2 -1 (66) / 24H1 -9 (78) / 24H2 +3 (60) / 25H1 -1 (84) / 25H2 -4 (71) / 26H1 -7 (63) / 26H2 -4 (31) |

### 5c. Lead-time of each breadth series' own turn (share of NQ turns where the feed's extreme came >= 3 min earlier, vs random windows; signed by same-moment sign on the fit months)
| feed | session | turns | median lead min | null median | early share | null | diff pp | z |
|---|---|---|---|---|---|---|---|---|
| TICKQ_ext | NY AM | 616 | -1 | 0 | 0.456 | 0.411 | +4.5 | 1.8 |
| TICK | NY AM | 1250 | 0 | 1 | 0.390 | 0.366 | +2.3 | 1.4 |
| TICK_ext | NY AM | 443 | -1 | 0 | 0.456 | 0.416 | +4.0 | 1.3 |
| TRIN | NY AM | 1250 | -2 | -0 | 0.479 | 0.459 | +2.0 | 1.2 |
| TRINQ | NY AM | 1251 | -2 | -1 | 0.488 | 0.467 | +2.0 | 1.2 |
| TICKQ | NY AM | 1251 | 0 | 1 | 0.392 | 0.378 | +1.4 | 0.8 |
| TRINQ | NY PM | 550 | -3 | -3 | 0.504 | 0.502 | +0.1 | 0.1 |
| PCR | NY AM | 1251 | 1 | 1 | 0.440 | 0.445 | -0.5 | -0.3 |
| ADD | NY AM | 1250 | 2 | 2 | 0.366 | 0.371 | -0.5 | -0.3 |
| TICK | NY PM | 550 | -2 | -2 | 0.489 | 0.496 | -0.7 | -0.3 |
| DVOL | NY AM | 1250 | 2 | 2 | 0.371 | 0.382 | -1.0 | -0.6 |
| ADVSH | NY AM | 1250 | 2 | 2 | 0.368 | 0.381 | -1.3 | -0.7 |
| TICKQ_ext | NY PM | 412 | 1 | 1 | 0.328 | 0.350 | -2.2 | -0.8 |
| TICK_ext | NY PM | 386 | 0 | 1 | 0.326 | 0.353 | -2.6 | -1.0 |
| PCR | NY PM | 550 | 4 | 1 | 0.384 | 0.444 | -6.0 | -2.7 |
| TRIN | NY PM | 550 | 1 | -1 | 0.396 | 0.462 | -6.6 | -2.9 |
| TICKQ | NY PM | 550 | -1 | -2 | 0.411 | 0.480 | -6.9 | -3.0 |
| ADVSH | NY PM | 550 | 3 | 2 | 0.235 | 0.344 | -11.0 | -5.4 |
| ADD | NY PM | 550 | 3 | 2 | 0.227 | 0.347 | -12.0 | -6.0 |
| DVOL | NY PM | 550 | 3 | 2 | 0.205 | 0.328 | -12.2 | -6.3 |

Caveats: turn study descriptive (turn time defined with hindsight; no BH); VIX and Asia/London not testable; breadth minute bars have no sub-minute resolution so 'below one minute' is not addressed here.
