# DS3_DD_REREAD_A6 - engine verification of the exit families the A1 screen could not label (UF-LOSS, L2SL tighten/half, L2SP). A6, 2026-11-01T04:11Z. POST-HOC re-pricing, nothing promoted, no PASS claim, Shadow only with the L2 feature gap

Prereg `l2vast/ds3/prereg/A6_EXITVERIFY_prereg.md` sha256 8dadd44b554d0c03351bab0b63bfc2fb10f92c5e447af17590eecbc523d72339 (in DECISIONS.md before any engine run; selection list sha256 7cf6d14c...dc2b0). Masks capped 20260206; no post-cap file opened (UF-LOSS C7/C8/C10 stack*_daily.npz and the adduw 953-day grid untouched). Code `l2vast/ds3/code/ddre_a6/`, out `l2vast/ds3/out/dd_reread/a6/` (`exit_times.parquet` = the exit second per fired trade of every simulated cell, reusable; `cells_exact_final.parquet`, `master_a6.parquet/csv`, `extrapolation_random.csv`), rows `out/recent_wins/dd_reread_a6.csv`.

**Plain sentence.** The three families the A1 screen could not label (UF-LOSS cycles 1/2/3/5/6, L2SL tighten/half actions, L2SP profit-health settings; 31,797 eligible cells of the 33,929 ledger cells in these programs) were made engine-verifiable by re-deriving one exit second per fired trade from the programs' own triggers (rebuilt per-trade delta equals the stored delta in every cell, max difference 4e-6 pt) and 1,721 cells (1,454 top by the PRE+X' screen, stratified by family and action; 300 uniform random inside the families) were re-run on the one-convention lock engine at live lots in both frames. **On the as-is stack 414 distinct engine series are RISK-KEEP (cut maxDD >= 20% in PRE and X' and in L6M, mean inside its MDE, and beat the same-volume random-skip placebo): L2SL tighten/half 95, L2SP 285, UF-LOSS 34; on the Sunday composite 0 are** (9 composite cells meet the three drawdown tests but not the placebo): the composite already takes the drawdown these rules would take in L6M, so no exit rule adds a RISK-KEEP on top of it. The screen was wrong in the direction A1 feared: in the random samples it called 50 of 300 cells carried as-is where the engine carries 79 (L2SL: screen 1 of 70, engine 22 of 70), and of the screen-carried top cells 699 of 750 stay carried while 289 cells the screen did not carry are carried exactly. Family-wise p over the full swept program is <= 0.05 for 271 of the as-is RISK-KEEP series, but the L2SP rows are the p70 take line plus a book gate (the D6 pct>=0.70 line alone cuts as-is PRE 24%, X' 45%, L6M 44% and is by itself only a volume effect, PRE placebo rank 0.21; 261 of the 285 L2SP series cut more than it in PRE and X'), they trade 4-34% of the stack's gross P&L (median 22%) and cost thousands of target exits, the L2SL/UF-LOSS tighten rows have HOLD (includes July 2025) deeper in 31% / 76% of cases, and the L6M as-is maxDD (88k) is one week (2026-01-19). The closest composite-frame candidate is the L2SL tighten 'A40 / share0.2@5s / newext / t10': composite PRE maxDD 241k to 172k, X' 121k to 59k, L6M 23k to 18k, mean inside MDE, family-wise p 0.015 over 7,840 cells, but its L6M placebo rank is 0.085 (volume effect), so it is not RISK-KEEP. Nothing is a PASS; no cell goes live; Shadow slots need the L2 features D6 does not compute.

## PAGE 1

### 1. Coverage
| family | ledger cells | eligible (live fires) | re-simulated | top-by-screen | random sample | distinct as-is series | median fired trades | median live fired (as-is) | exit time changed | tie-out: max abs(rebuilt - stored delta) pts | tie-out: max gain error |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L2SL | 7,840 | 5,877 | 518 | 450 | 70 | 480 | 16,723 | 4,887 | 70% | 3.7e-06 | 0.0011% |
| L2SP | 23,773 | 23,772 | 691 | 606 | 90 | 587 | 18,563 | 5,147 | 98% | 0.0e+00 | 0.0000% |
| UFL1 | 480 | 406 | 101 | 80 | 28 | 101 | 7,577 | 2,216 | 75% | 3.7e-06 | 0.0006% |
| UFL2 | 522 | 480 | 103 | 80 | 28 | 97 | 19,112 | 5,172 | 73% | 3.7e-06 | 0.0002% |
| UFL3 | 402 | 352 | 104 | 78 | 28 | 104 | 3,290 | 636 | 47% | 0.0e+00 | 0.0000% |
| UFL5 | 576 | 576 | 104 | 80 | 28 | 104 | 3,049 | 805 | 76% | 0.0e+00 | 0.0000% |
| UFL6 | 336 | 334 | 100 | 80 | 28 | 100 | 8,154 | 2,443 | 72% | 3.7e-06 | 0.0016% |

Not covered: UF-LOSS C4 (48 chains), C9 (432 ES-open cells, engine file not located), 28 C1 extra and 42 C2 HM path-rule cells, C7/C8/C10 (stack-level files span the cap), the L2SL cut actions (already exact in A1). 1,721 cells re-simulated, both frames, on the 1-s path / 10-s L2 cache with the programs' own trigger definitions; `exit_times.parquet` holds 26,950,687 fired-trade rows (sid, tid, tr = index in tidx_cut, drow = engine d-row, fire_sec = decision second [L2SP: the kernel exit-row second; UFL5 half: 0 = not stored], exit_sec = exit second when exit_changed, delta_pts = the program's stored per-trade delta, live_A / live_C; cell list `exit_times_cells.csv` maps sid to family, position, cell name).

### 2. Screen versus exact (calibration). Random-sample columns are the unbiased family estimate; 'top' columns are conditional on the screen choice
| family | frame | random n | corr PRE cut | corr X' cut | corr L6M cut | random: screen-carried | exact-carried | both | exact only (screen missed) | top n | top: screen-carried | stay carried exactly | carried exactly, screen did not |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L2SL | AS-IS | 70 | 0.69 | 0.54 | 0.53 | 1 | 22 | 1 | 21 | 450 | 126 | 114 | 216 |
| L2SL | COMPOSITE | 70 | 0.85 | 0.82 | 0.84 | 1 | 2 | 1 | 1 | 450 | 178 | 176 | 0 |
| L2SP | AS-IS | 90 | 0.81 | 0.93 | 0.48 | 47 | 46 | 37 | 9 | 606 | 606 | 572 | 0 |
| L2SP | COMPOSITE | 90 | 0.96 | 0.89 | 0.70 | 9 | 10 | 8 | 2 | 606 | 273 | 211 | 78 |
| UFL1 | AS-IS | 28 | 0.51 | 0.67 | 0.37 | 1 | 3 | 0 | 3 | 80 | 5 | 1 | 18 |
| UFL1 | COMPOSITE | 28 | 0.82 | 0.54 | 0.96 | 0 | 0 | 0 | 0 | 80 | 15 | 12 | 1 |
| UFL2 | AS-IS | 28 | 0.33 | 0.70 | 0.35 | 1 | 7 | 1 | 6 | 80 | 5 | 4 | 32 |
| UFL2 | COMPOSITE | 28 | 0.75 | 0.92 | 0.87 | 4 | 3 | 3 | 0 | 80 | 25 | 23 | 11 |
| UFL3 | AS-IS | 28 | 0.75 | 0.56 | 0.88 | 0 | 0 | 0 | 0 | 78 | 0 | 0 | 12 |
| UFL3 | COMPOSITE | 28 | 0.91 | 0.99 | 0.95 | 0 | 0 | 0 | 0 | 78 | 2 | 0 | 1 |
| UFL5 | AS-IS | 28 | 0.63 | 0.81 | 0.29 | 0 | 1 | 0 | 1 | 80 | 8 | 8 | 11 |
| UFL5 | COMPOSITE | 28 | 0.93 | 0.82 | 0.81 | 0 | 1 | 0 | 1 | 80 | 16 | 7 | 2 |
| UFL6 | AS-IS | 28 | 0.50 | 0.36 | 0.55 | 0 | 0 | 0 | 0 | 80 | 0 | 0 | 0 |
| UFL6 | COMPOSITE | 28 | 0.61 | n/a | 0.71 | 0 | 0 | 0 | 0 | 80 | 0 | 0 | 0 |

Reading: L2SP was screened tolerably (random sample: screen-carried 47, exact-carried 46, 37 in common; PRE/X' cut correlations 0.81/0.93 as-is, 0.96/0.89 composite; the L6M correlation is low, 0.48, because the as-is L6M figure is one week). L2SL tighten/half and UF-LOSS C1/C2 were badly under-selected as-is: the screen flagged 1 of 70 (L2SL), 1 of 28 (UFL1), 1 of 28 (UFL2) random cells as carried where the engine carries 22, 3 and 7, and in the top-by-screen sets 216 (L2SL), 18 (UFL1) and 32 (UFL2) cells are carried exactly although the screen did not carry them. The composite frame is better calibrated (correlations 0.75-0.99, except UFL6 and UFL1's X'). Ranking by the screen is therefore not a reliable way to find RISK-KEEPs for tighten/half actions; the random-sample rows are the unbiased family-level estimate.

### 3. RISK-KEEP table, top 30, as-is stack (rank: tier, then min(PRE,X') maxDD cut, round-robin over L2SL / L2SP / UF-LOSS; columns recent-first; identical engine series collapsed). Selection PRE and X' only; ONE recent look per family; swept count and family-wise p beside each row
| family | cell | frame | session | label | maxDD cut L3M / L6M / HOLD / PRE / X' | L6M maxDD before>after | PRE maxDD before>after | X' maxDD before>after | ALL worst-20 before>after | ALL weekly SD before>after | ALL Calmar before>after | ALL mean/worst-20 before>after | mean change $/wk (MDE): L6M ; PRE ; X' | equal-risk mean change ALL / L6M $/wk (engine lot table) | placebo rank L6M/PRE/X' | PRE and X' agree | family-wise p (swept cells) | targets lost (live fired, this frame) | vs p70-take line: dPRE/dX'/dL6M cut |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L2SL | A45 / mult20@5s / ne0 / none / t5 | AS-IS | all | RK | 59% / 59% / 8% / 50% / 55% | 88k>36k | 162k>80k | 317k>142k | -1161k>-950k | 47.2k>45.1k | 0.04>0.13 | 0.011>0.020 | +2809 (12578) ; +4069 (6652) ; +9274 (6840) | +9598 / +8250 | 0.005/0.005/0.005 | yes | 0.005 of 7,840 | 201 |  |
| L2SP | P / hour_ahead_ge1.2 / armpts40 / d10 / trail10 / p70thickonly | AS-IS | all | RK | 66% / 61% / 40% / 50% / 54% | 88k>34k | 162k>81k | 317k>146k | -1161k>-872k | 47.2k>39.6k | 0.04>0.08 | 0.011>0.013 | -5681 (15321) ; -3188 (9129) ; +1965 (10704) | +1698 / -355 | 0.015/0.010/0.045 | yes | 0.020 of 23,773 | 4,311 | +26/+9/+18 pts |
| UFL2 | loss / a=30 / rt=F3 / win=10 / mode=delay / act=t15 | AS-IS | all | RK | 44% / 44% / 7% / 45% / 59% | 88k>49k | 162k>89k | 317k>131k | -1161k>-988k | 47.2k>44.7k | 0.04>0.12 | 0.011>0.017 | +1542 (14836) ; +1454 (8580) ; +8284 (9337) | +6506 / +5609 | 0.050/0.015/0.020 | yes | 0.015 of 522 | 456 |  |
| L2SL | A45 / mult20@5s / ne0 / SWP / t5 | AS-IS | all | RK | 58% / 58% / 7% / 50% / 54% | 88k>37k | 162k>81k | 317k>146k | -1161k>-956k | 47.2k>45.3k | 0.04>0.13 | 0.011>0.019 | +2189 (12629) ; +4141 (6419) ; +9084 (6912) | +9286 / +7319 | 0.005/0.005/0.005 | yes | 0.005 of 7,840 | 198 |  |
| L2SP | P / z_tot_ge2.0 / armpts40 / d0 / trail20 / p70never | AS-IS | all | RK | 72% / 64% / 16% / 50% / 63% | 88k>32k | 162k>81k | 317k>117k | -1161k>-869k | 47.2k>38.4k | 0.04>0.08 | 0.011>0.011 | -4217 (13709) ; -7202 (9502) ; +4060 (10083) | +85 / +1662 | 0.010/0.005/0.010 | yes | 0.010 of 23,773 | 2,158 | +26/+18/+20 pts |
| UFL1 | A40 / GATE / NE / t10 [+4 identical] | AS-IS | all | RK | 45% / 45% / -6% / 42% / 64% | 88k>48k | 162k>93k | 317k>115k | -1161k>-1020k | 47.2k>45.1k | 0.04>0.12 | 0.011>0.017 | +2080 (12082) ; +3345 (7690) ; +8794 (8430) | +7162 / +5361 | 0.010/0.005/0.005 | yes | 0.010 of 480 | 251 |  |
| L2SP | P / hour_ahead_ge1.2 / armpts40 / d10 / half20 / p70thickonly | AS-IS | all | RK | 75% / 61% / 40% / 50% / 52% | 88k>34k | 162k>81k | 317k>152k | -1161k>-900k | 47.2k>39.5k | 0.04>0.07 | 0.011>0.012 | -3225 (14807) ; -3925 (9017) ; +1487 (10632) | +1212 / +2126 | 0.015/0.010/0.045 | yes | 0.020 of 23,773 | 4,287 | +26/+7/+18 pts |
| L2SL | A40 / share0.2@5s / ne1 / ICESWP / t5 | AS-IS | all | RK | 41% / 41% / -22% / 49% / 69% | 88k>52k | 162k>82k | 317k>100k | -1161k>-1065k | 47.2k>47.4k | 0.04>0.10 | 0.011>0.017 | +4294 (14614) ; +3518 (7682) ; +8163 (8247) | +6470 / +6639 | 0.050/0.005/0.005 | yes | 0.010 of 7,840 | 360 |  |
| UFL2 | loss / a=40 / rt=F1 / win=10 / mode=veto / act=t10 | AS-IS | all | RK | 42% / 42% / -8% / 42% / 63% | 88k>51k | 162k>93k | 317k>116k | -1161k>-1025k | 47.2k>45.1k | 0.04>0.11 | 0.011>0.017 | +1431 (11106) ; +3360 (7808) ; +8296 (8293) | +6728 / +4504 | 0.010/0.005/0.005 | yes | 0.010 of 522 | 246 |  |
| L2SP | P / t60_ahead_ge1.2 / armpts40 / d10 / trail5 / p70thickonly | AS-IS | all | RK | 72% / 60% / 39% / 50% / 49% | 88k>36k | 162k>81k | 317k>160k | -1161k>-838k | 47.2k>39.3k | 0.04>0.07 | 0.011>0.014 | -3998 (17055) ; -2824 (9702) ; +1756 (11631) | +2849 / +2829 | 0.015/0.010/0.095 | yes | 0.060 of 23,773 | 4,812 | +26/+4/+16 pts |
| L2SL | A40 / share0.2@5s / ne1 / K2 / t5 | AS-IS | all | RK | 42% / 42% / -22% / 49% / 69% | 88k>51k | 162k>82k | 317k>98k | -1161k>-1059k | 47.2k>46.8k | 0.04>0.10 | 0.011>0.017 | +4133 (14515) ; +3007 (7709) ; +8352 (8286) | +6322 / +6613 | 0.050/0.005/0.005 | yes | 0.010 of 7,840 | 367 |  |
| UFL2 | loss / a=40 / rt=T1 / win=10 / mode=delay / act=t10 | AS-IS | all | RK | 57% / 57% / -6% / 42% / 64% | 88k>38k | 162k>93k | 317k>115k | -1161k>-1010k | 47.2k>45.0k | 0.04>0.12 | 0.011>0.018 | +2448 (12459) ; +3318 (7693) ; +8779 (8427) | +7431 / +6064 | 0.005/0.005/0.005 | yes | 0.010 of 522 | 251 |  |
| L2SP | P / z_tot_ge2.0 / armpts40 / d0 / half20 / p70never | AS-IS | all | RK | 60% / 60% / 26% / 49% / 55% | 88k>35k | 162k>82k | 317k>143k | -1161k>-889k | 47.2k>39.0k | 0.04>0.07 | 0.011>0.011 | -4781 (15105) ; -5619 (9441) ; +2983 (9745) | +265 / +397 | 0.015/0.005/0.045 | yes | 0.010 of 23,773 | 2,158 | +25/+9/+16 pts |
| L2SL | A40 / share0.3@5s / ne1 / ICESWP / t5 | AS-IS | all | RK | 41% / 41% / -22% / 49% / 68% | 88k>52k | 162k>83k | 317k>101k | -1161k>-1068k | 47.2k>47.3k | 0.04>0.10 | 0.011>0.017 | +4232 (14611) ; +3243 (7629) ; +8026 (8188) | +6216 / +6505 | 0.050/0.005/0.005 | yes | 0.010 of 7,840 | 360 |  |
| UFL2 | loss / a=40 / rt=T1 / win=10 / mode=veto / act=t10 | AS-IS | all | RK | 57% / 57% / -7% / 42% / 64% | 88k>38k | 162k>93k | 317k>115k | -1161k>-1010k | 47.2k>45.0k | 0.04>0.12 | 0.011>0.018 | +2396 (12458) ; +3238 (7698) ; +8900 (8634) | +7404 / +6005 | 0.005/0.005/0.005 | yes | 0.010 of 522 | 250 |  |
| L2SP | P / z_tot_ge1.5 / armpts40 / d0 / half20 / p70thickonly | AS-IS | all | RK | 73% / 61% / 38% / 49% / 50% | 88k>34k | 162k>82k | 317k>157k | -1161k>-856k | 47.2k>38.5k | 0.04>0.07 | 0.011>0.013 | -2514 (15695) ; -3499 (9791) ; +1789 (10663) | +2583 / +4319 | 0.010/0.010/0.060 | yes | 0.025 of 23,773 | 4,098 | +25/+5/+17 pts |
| L2SL | A40 / share0.3@5s / ne1 / K2 / t5 | AS-IS | all | RK | 42% / 42% / -22% / 49% / 69% | 88k>51k | 162k>83k | 317k>99k | -1161k>-1062k | 47.2k>46.7k | 0.04>0.10 | 0.011>0.016 | +4036 (14536) ; +2732 (7654) ; +8216 (8228) | +6060 / +6440 | 0.050/0.005/0.005 | yes | 0.010 of 7,840 | 367 |  |
| UFL2 | loss / a=40 / rt=T2 / win=10 / mode=delay / act=t10 | AS-IS | all | RK | 45% / 45% / -6% / 42% / 64% | 88k>48k | 162k>93k | 317k>115k | -1161k>-1020k | 47.2k>45.1k | 0.04>0.12 | 0.011>0.017 | +2080 (12082) ; +3366 (7674) ; +8794 (8430) | +7175 / +5361 | 0.010/0.005/0.005 | yes | 0.010 of 522 | 251 |  |
| L2SP | P / hour_ahead_ge1.2 / armpts40 / d10 / half10 / p70thickonly | AS-IS | all | RK | 73% / 61% / 40% / 51% / 49% | 88k>34k | 162k>80k | 317k>161k | -1161k>-893k | 47.2k>39.6k | 0.04>0.07 | 0.011>0.012 | -4067 (15113) ; -3548 (9125) ; +1562 (10589) | +1364 / +1219 | 0.015/0.010/0.055 | yes | 0.040 of 23,773 | 4,311 | +27/+4/+17 pts |
| L2SL | A45 / mult20@5s / ne1 / none / t5 | AS-IS | all | RK | 61% / 61% / 15% / 53% / 49% | 88k>34k | 162k>76k | 317k>162k | -1161k>-957k | 47.2k>44.5k | 0.04>0.11 | 0.011>0.019 | +3177 (12401) ; +3514 (6231) ; +8611 (6213) | +9027 / +8477 | 0.005/0.005/0.005 | yes | 0.005 of 7,840 | 174 |  |
| UFL2 | loss / a=40 / rt=T2 / win=10 / mode=veto / act=t10 | AS-IS | all | RK | 45% / 45% / -6% / 42% / 64% | 88k>48k | 162k>93k | 317k>115k | -1161k>-1020k | 47.2k>45.0k | 0.04>0.12 | 0.011>0.017 | +2080 (12082) ; +3354 (7676) ; +8794 (8430) | +7168 / +5361 | 0.010/0.005/0.005 | yes | 0.010 of 522 | 251 |  |
| L2SP | P / t60_ahead_ge1.2 / armpts40 / d10 / half10 / p70thickonly | AS-IS | all | RK | 71% / 66% / 39% / 49% / 50% | 88k>30k | 162k>83k | 317k>160k | -1161k>-838k | 47.2k>39.0k | 0.04>0.07 | 0.011>0.014 | -2450 (16506) ; -2487 (9583) ; +1872 (11423) | +3398 / +4975 | 0.005/0.015/0.095 | yes | 0.060 of 23,773 | 4,800 | +25/+4/+22 pts |
| L2SL | A40 / share0.5@30s / ne0 / ICESWP / t10 | AS-IS | all | RK | 51% / 51% / -3% / 49% / 60% | 88k>43k | 162k>83k | 317k>127k | -1161k>-997k | 47.2k>45.4k | 0.04>0.12 | 0.011>0.018 | +2368 (11203) ; +4338 (6568) ; +8332 (8162) | +8131 / +6321 | 0.005/0.005/0.005 | yes | 0.005 of 7,840 | 212 |  |
| UFL2 | loss / a=40 / rt=C1 / win=30 / mode=delay / act=t10 | AS-IS | all | RK | 45% / 45% / -6% / 42% / 63% | 88k>48k | 162k>93k | 317k>116k | -1161k>-1025k | 47.2k>45.0k | 0.04>0.11 | 0.011>0.017 | +1035 (11553) ; +3287 (7756) ; +8750 (8426) | +6797 / +4050 | 0.010/0.005/0.005 | yes | 0.010 of 522 | 251 |  |
| L2SP | P / sess_ahead_ge1.2 / armpts40 / d0 / trail15 / p70thickonly | AS-IS | all | RK | 67% / 54% / 33% / 48% / 56% | 88k>41k | 162k>83k | 317k>138k | -1161k>-909k | 47.2k>38.1k | 0.04>0.07 | 0.011>0.011 | -7488 (15129) ; -5658 (9708) ; +2148 (10601) | -840 / -3534 | 0.035/0.015/0.050 | yes | 0.010 of 23,773 | 4,388 | +24/+11/+10 pts |
| L2SL | A45 / mult20@5s / ne1 / SWP / t5 | AS-IS | all | RK | 60% / 60% / 8% / 52% / 48% | 88k>35k | 162k>77k | 317k>166k | -1161k>-971k | 47.2k>44.8k | 0.04>0.11 | 0.011>0.019 | +2774 (12426) ; +3358 (6137) ; +8622 (6239) | +8469 / +7580 | 0.005/0.005/0.005 | yes | 0.005 of 7,840 | 172 |  |
| UFL2 | loss / a=40 / rt=F1 / win=10 / mode=delay / act=t10 | AS-IS | all | RK | 43% / 43% / -7% / 42% / 64% | 88k>50k | 162k>93k | 317k>115k | -1161k>-1027k | 47.2k>45.1k | 0.04>0.11 | 0.011>0.017 | +1077 (11397) ; +3361 (7732) ; +8662 (8439) | +6768 / +4043 | 0.010/0.005/0.005 | yes | 0.010 of 522 | 251 |  |
| L2SP | P / z_ahead_ge1.0 / armpts40 / d30 / trail10 / p70thickonly | AS-IS | all | RK | 73% / 60% / 39% / 48% / 64% | 88k>35k | 162k>84k | 317k>113k | -1161k>-880k | 47.2k>40.8k | 0.04>0.12 | 0.011>0.015 | -1189 (15910) ; -1472 (8877) ; +2866 (9608) | +4152 / +5368 | 0.015/0.005/0.010 | yes | 0.010 of 23,773 | 4,304 | +24/+19/+16 pts |
| L2SL | A40 / share0.5@5s / ne1 / ICESWP / t5 | AS-IS | all | RK | 41% / 41% / -24% / 47% / 61% | 88k>52k | 162k>85k | 317k>123k | -1161k>-1055k | 47.2k>47.4k | 0.04>0.10 | 0.011>0.017 | +3946 (14664) ; +3689 (7659) ; +7976 (8060) | +6597 / +6525 | 0.040/0.005/0.005 | yes | 0.010 of 7,840 | 343 |  |
| UFL2 | loss / a=40 / rt=T3 / win=10 / mode=delay / act=t10 | AS-IS | all | RK | 45% / 45% / -6% / 42% / 64% | 88k>48k | 162k>93k | 317k>115k | -1161k>-1021k | 47.2k>45.1k | 0.04>0.12 | 0.011>0.017 | +2024 (12094) ; +3369 (7658) ; +8966 (8641) | +7202 / +5276 | 0.010/0.005/0.005 | yes | 0.010 of 522 | 250 |  |

Sunday composite frame, best 12 cells of any tier (no cell is RISK-KEEP here; 'RK volume effect' = three drawdown tests pass but not the placebo, 'RK L6M only' = L6M test only):
| family | cell | frame | session | label | maxDD cut L3M / L6M / HOLD / PRE / X' | L6M maxDD before>after | PRE maxDD before>after | X' maxDD before>after | ALL worst-20 before>after | ALL weekly SD before>after | ALL Calmar before>after | ALL mean/worst-20 before>after | mean change $/wk (MDE): L6M ; PRE ; X' | equal-risk mean change ALL / L6M $/wk (engine lot table) | placebo rank L6M/PRE/X' | PRE and X' agree | family-wise p (swept cells) | targets lost (live fired, this frame) | vs p70-take line: dPRE/dX'/dL6M cut |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L2SP | P / z_ahead_ge2.0 / armpct0.7 / d30 / lock10 / p70never | COMPOSITE | all | RK (volume effect) | 61% / 31% / 12% / 30% / 31% | 23k>16k | 241k>168k | 121k>83k | -1098k>-1085k | 50.3k>49.5k | 0.09>0.14 | 0.020>0.022 | -3713 (5676) ; +2035 (5349) ; +2963 (6158) | +1256 / -3835 | 0.050/0.015/0.109 | yes | 0.080 of 23,773 | 401 |  |
| L2SL | A40 / share0.2@5s / ne1 / none / t10 | COMPOSITE | all | RK (volume effect) | 25% / 21% / 30% / 29% / 51% | 23k>18k | 241k>172k | 121k>59k | -1098k>-1042k | 50.3k>48.8k | 0.09>0.14 | 0.020>0.023 | -1284 (9550) ; +2963 (4943) ; +1721 (5142) | +3593 / +1219 | 0.085/0.025/0.005 | yes | 0.015 of 7,840 | 218 |  |
| L2SL | A40 / share0.3@5s / ne1 / none / t10 | COMPOSITE | all | RK (volume effect) | 25% / 21% / 30% / 29% / 54% | 23k>18k | 241k>172k | 121k>55k | -1098k>-1024k | 50.3k>48.5k | 0.09>0.14 | 0.020>0.024 | -1332 (9556) ; +3563 (4771) ; +1884 (5198) | +3282 / +1544 | 0.090/0.025/0.005 | yes | 0.015 of 7,840 | 215 |  |
| L2SP | P / t60_ahead_ge2.0 / armpts10 / d30 / half20 / p70always | COMPOSITE | all | RK (volume effect) | 16% / 22% / 16% / 61% / 28% | 23k>18k | 241k>95k | 121k>87k | -1098k>-843k | 50.3k>43.8k | 0.09>0.23 | 0.020>0.026 | -8689 (14280) ; +3375 (10657) ; -1524 (9203) | +5864 / +2194 | 0.025/0.020/0.274 | yes | 0.433 of 23,773 | 4,972 |  |
| L2SP | P / sess_ahead_ge2.0 / armpts30 / d10 / lock5 / p70always [+1 identical] | COMPOSITE | all | RK (volume effect) | 47% / 26% / -4% / 35% / 27% | 23k>17k | 241k>156k | 121k>88k | -1098k>-853k | 50.3k>43.4k | 0.09>0.15 | 0.020>0.027 | -5579 (14278) ; +2790 (9851) ; +3320 (9934) | +7446 / +5359 | 0.015/0.194/0.279 | yes | 0.438 of 23,773 | 4,965 |  |
| L2SP | P / sess_ahead_ge2.0 / armpts30 / d10 / lock10 / p70always [+1 identical] | COMPOSITE | all | RK (volume effect) | 49% / 30% / -2% / 40% / 26% | 23k>16k | 241k>145k | 121k>90k | -1098k>-836k | 50.3k>42.9k | 0.09>0.16 | 0.020>0.028 | -4802 (14289) ; +2798 (9895) ; +3097 (9856) | +6244 / +5374 | 0.015/0.129/0.294 | yes | 0.498 of 23,773 | 4,966 |  |
| L2SP | P / hour_ahead_ge2.0 / armpct0.3 / d30 / lock5 / p70always | COMPOSITE | all | RK (volume effect) | 33% / 28% / 4% / 39% / 23% | 23k>16k | 241k>147k | 121k>93k | -1098k>-896k | 50.3k>45.3k | 0.09>0.15 | 0.020>0.025 | -8281 (14583) ; +3764 (10565) ; +488 (9096) | +4117 / -735 | 0.015/0.134/0.323 | yes | 0.557 of 23,773 | 4,962 |  |
| L2SP | P / sess_ahead_ge2.0 / armpts30 / d10 / half10 / p70always [+1 identical] | COMPOSITE | all | RK (L6M only) | 40% / 22% / -12% / 35% / 17% | 23k>18k | 241k>157k | 121k>100k | -1098k>-843k | 50.3k>43.4k | 0.09>0.14 | 0.020>0.027 | -3978 (14799) ; +2646 (10015) ; +2115 (9771) | +7213 / +7194 | 0.025/0.219/0.378 | no | 0.682 of 23,773 | 4,970 |  |
| L2SL | A45 / mult100@30s / ne1 / K2 / half | COMPOSITE | all | RK (L6M only) | -47% / 26% / 15% / 19% / 17% | 23k>17k | 241k>195k | 121k>100k | -1098k>-1048k | 50.3k>46.9k | 0.09>0.11 | 0.020>0.020 | -5304 (6207) ; +205 (3820) ; -1135 (3754) | -1142 / -5535 | 0.090/0.104/0.279 | no | 0.502 of 7,840 | 0 |  |
| UFL1 | A20 / SEQ / SEQ(kP2>kWC>kS)&NE / cut | COMPOSITE | all | RK (L6M only) | -101% / 33% / 4% / 4% / 11% | 23k>15k | 241k>231k | 121k>108k | -1098k>-1087k | 50.3k>50.2k | 0.09>0.10 | 0.020>0.021 | +1786 (6075) ; +2150 (2875) ; -1495 (3755) | +1394 / +1349 | 0.040/0.393/0.254 | no | 0.697 of 480 | 112 |  |
| L2SP | P / sess_ahead_ge2.0 / armpts30 / d10 / take / p70always [+1 identical] | COMPOSITE | all | RK (L6M only) | 41% / 24% / -14% / 37% / 16% | 23k>17k | 241k>153k | 121k>101k | -1098k>-843k | 50.3k>43.2k | 0.09>0.15 | 0.020>0.027 | -4303 (14570) ; +2755 (10055) ; +2021 (9824) | +7367 / +7702 | 0.020/0.189/0.378 | no | 0.687 of 23,773 | 4,973 |  |
| L2SL | A45 / mult100@30s / ne1 / ICESWP / half | COMPOSITE | all | RK (L6M only) | -47% / 26% / 15% / 19% / 16% | 23k>17k | 241k>196k | 121k>101k | -1098k>-1048k | 50.3k>46.9k | 0.09>0.11 | 0.020>0.020 | -5293 (6246) ; -71 (3686) ; -880 (3866) | -1079 / -5344 | 0.090/0.100/0.274 | no | 0.502 of 7,840 | 0 |  |

Composite, post-hoc PRE-fix leads (NOT RISK-KEEP: carried in PRE and X', L6M maxDD not deeper than +10%, L6M and ALL mean inside MDE, PRE and X' placebo rank <= 0.10; defined after seeing the table):
| family | cell | frame | session | label | maxDD cut L3M / L6M / HOLD / PRE / X' | L6M maxDD before>after | PRE maxDD before>after | X' maxDD before>after | ALL worst-20 before>after | ALL weekly SD before>after | ALL Calmar before>after | ALL mean/worst-20 before>after | mean change $/wk (MDE): L6M ; PRE ; X' | equal-risk mean change ALL / L6M $/wk (engine lot table) | placebo rank L6M/PRE/X' | PRE and X' agree | family-wise p (swept cells) | targets lost (live fired, this frame) | vs p70-take line: dPRE/dX'/dL6M cut |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L2SP | P / hour_tot_ge1.2 / armpct0.7 / d30 / lock0 / p70thickonly | COMPOSITE | all | no | 45% / -1% / 22% / 48% / 37% | 23k>23k | 241k>125k | 121k>76k | -1098k>-1015k | 50.3k>48.6k | 0.09>0.19 | 0.020>0.024 | -5842 (12435) ; +4406 (8144) ; +2267 (9142) | +2810 / -2406 | 0.159/0.020/0.095 | yes | 0.159 of 23,773 | 3,289 |  |
| L2SP | P / z_ahead_ge1.0 / armpct0.7 / d30 / lock10 / p70never | COMPOSITE | all | no | 61% / -1% / -1% / 42% / 31% | 23k>23k | 241k>139k | 121k>83k | -1098k>-1081k | 50.3k>49.8k | 0.09>0.17 | 0.020>0.022 | -1648 (6326) ; +2769 (5878) ; +2792 (6441) | +1877 / -1730 | 0.164/0.010/0.095 | yes | 0.119 of 23,773 | 563 |  |
| L2SL | A40 / share0.2@5s / ne1 / none / t10 | COMPOSITE | all | RK (volume effect) | 25% / 21% / 30% / 29% / 51% | 23k>18k | 241k>172k | 121k>59k | -1098k>-1042k | 50.3k>48.8k | 0.09>0.14 | 0.020>0.023 | -1284 (9550) ; +2963 (4943) ; +1721 (5142) | +3593 / +1219 | 0.085/0.025/0.005 | yes | 0.015 of 7,840 | 218 |  |
| L2SL | A40 / share0.3@5s / ne1 / none / t10 | COMPOSITE | all | RK (volume effect) | 25% / 21% / 30% / 29% / 54% | 23k>18k | 241k>172k | 121k>55k | -1098k>-1024k | 50.3k>48.5k | 0.09>0.14 | 0.020>0.024 | -1332 (9556) ; +3563 (4771) ; +1884 (5198) | +3282 / +1544 | 0.090/0.025/0.005 | yes | 0.015 of 7,840 | 215 |  |


### 4. Counts by family
| family | frame | swept (ledger) | re-simulated | carried (PRE and X' cut>=20%, mean ok) | meets L6M def. | RISK-KEEP (distinct series) | volume effect | L6M only | RISK-KEEP with family-wise p <= 0.05 (distinct) | min family-wise p |
|---|---|---|---|---|---|---|---|---|---|---|
| L2SL | AS-IS | 7,840 | 518 | 350 | 253 | 114 (95) | 71 | 68 | 92 | 0.005 |
| L2SL | COMPOSITE | 7,840 | 518 | 178 | 17 | 0 (0) | 2 | 15 | 0 | 0.005 |
| L2SP | AS-IS | 23,773 | 691 | 613 | 647 | 309 (285) | 279 | 59 | 147 | 0.005 |
| L2SP | COMPOSITE | 23,773 | 691 | 299 | 16 | 0 (0) | 7 | 9 | 0 | 0.030 |
| UFL1 | AS-IS | 480 | 101 | 20 | 32 | 13 (13) | 3 | 16 | 13 | 0.005 |
| UFL1 | COMPOSITE | 480 | 101 | 13 | 1 | 0 (0) | 0 | 1 | 0 | 0.005 |
| UFL2 | AS-IS | 522 | 103 | 41 | 60 | 24 (20) | 12 | 24 | 19 | 0.005 |
| UFL2 | COMPOSITE | 522 | 103 | 36 | 0 | 0 (0) | 0 | 0 | 0 | 0.005 |
| UFL3 | AS-IS | 402 | 104 | 12 | 11 | 1 (1) | 2 | 8 | 0 | 0.005 |
| UFL3 | COMPOSITE | 402 | 104 | 1 | 2 | 0 (0) | 0 | 2 | 0 | 0.085 |
| UFL5 | AS-IS | 576 | 104 | 19 | 21 | 0 (0) | 10 | 11 | 0 | 0.050 |
| UFL5 | COMPOSITE | 576 | 104 | 10 | 0 | 0 (0) | 0 | 0 | 0 | 0.070 |
| UFL6 | AS-IS | 336 | 100 | 0 | 23 | 0 (0) | 0 | 23 | 0 | 0.592 |
| UFL6 | COMPOSITE | 336 | 100 | 0 | 0 | 0 (0) | 0 | 0 | 0 | 0.816 |

Reading: 'carried' = PRE and X' maxDD cut >= 20% in both with the mean change not below -MDE in each (selection on PRE+X' only). 'meets' = the user's definition, one recent look (L6M cut >= 20%, L6M and ALL mean not below -MDE). RISK-KEEP = carried and meets and beats the same-volume random-skip placebo (L6M rank <= 0.05, PRE and X' <= 0.10). Family-wise p = studentised Westfall-Young max-T over the whole swept program (every ledger cell of the family, A1 volume-matched null, 200 draws, smallest attainable 0.005), not only the re-simulated subset. Counts in the RISK-KEEP column are cells (distinct engine series in brackets: cells that differ only in an arm/trigger that never binds produce the same series).

## PAGE 2

### 5. What the random sample implies for the cells not re-simulated
| family | frame | random n | RISK-KEEP in sample | rate [95% Wilson] | implied RISK-KEEP in the eligible family (not re-simulated beyond the sample) | exact-carried in sample | implied carried |
|---|---|---|---|---|---|---|---|
| L2SL | AS-IS | 70 | 3 | 4.3% [1.5, 11.9] | 252 [86, 697] | 22 | 1,847 |
| L2SL | COMPOSITE | 70 | 0 | 0.0% [0.0, 5.2] | 0 [0, 306] | 2 | 168 |
| L2SP | AS-IS | 90 | 14 | 15.6% [9.5, 24.4] | 3,698 [2,258, 5,808] | 46 | 12,150 |
| L2SP | COMPOSITE | 90 | 0 | 0.0% [0.0, 4.1] | 0 [0, 973] | 10 | 2,641 |
| UFL1 | AS-IS | 28 | 1 | 3.6% [0.6, 17.7] | 14 [3, 72] | 3 | 44 |
| UFL1 | COMPOSITE | 28 | 0 | 0.0% [0.0, 12.1] | 0 [0, 49] | 0 | 0 |
| UFL2 | AS-IS | 28 | 3 | 10.7% [3.7, 27.2] | 51 [18, 131] | 7 | 120 |
| UFL2 | COMPOSITE | 28 | 0 | 0.0% [0.0, 12.1] | 0 [0, 58] | 3 | 51 |
| UFL3 | AS-IS | 28 | 0 | 0.0% [0.0, 12.1] | 0 [0, 42] | 0 | 0 |
| UFL3 | COMPOSITE | 28 | 0 | 0.0% [0.0, 12.1] | 0 [0, 42] | 0 | 0 |
| UFL5 | AS-IS | 28 | 0 | 0.0% [0.0, 12.1] | 0 [0, 69] | 1 | 21 |
| UFL5 | COMPOSITE | 28 | 0 | 0.0% [0.0, 12.1] | 0 [0, 69] | 1 | 21 |
| UFL6 | AS-IS | 28 | 0 | 0.0% [0.0, 12.1] | 0 [0, 40] | 0 | 0 |
| UFL6 | COMPOSITE | 28 | 0 | 0.0% [0.0, 12.1] | 0 [0, 40] | 0 | 0 |

These are sampling estimates with their Wilson intervals; they say how many RISK-KEEP series a full engine sweep of the eligible family would contain (as-is), not which ones.

### 5b. Does HOLD agree? (as-is RISK-KEEP distinct series)
| group | RISK-KEEP series (as-is) | HOLD cut >= 0 | HOLD cut >= 20% | L3M cut >= 20% | L6M mean change > 0 | stack volume touched: median (range) | ALL worst-20 better | ALL SD lower | ALL Calmar higher |
|---|---|---|---|---|---|---|---|---|---|
| L2SL | 95 | 69% | 2% | 100% | 96% | 9% (3%-13%) | 100% | 96% | 100% |
| L2SP | 285 | 91% | 74% | 100% | 20% | 22% (4%-34%) | 100% | 100% | 100% |
| UF-LOSS | 34 | 24% | 0% | 100% | 94% | 10% (2%-17%) | 100% | 97% | 100% |

HOLD (2025-07-01..2026-02-06) includes July 2025; the RISK-KEEP definition uses L6M, PRE and X' only, so HOLD is the extra multi-episode check. L2SP rows hold up in HOLD (91% do not deepen it, 74% cut it by 20% or more: a take/trail rule also cuts the July drawdown) but the L2SP mean change is negative inside the MDE in 80% of the rows (the price of taking profit early; the equal-risk column converts the lower risk into mean). The L2SL tighten rows leave HOLD no deeper in 69% but reach a 20% HOLD cut in only 2%, and 76% of the UF-LOSS rows deepen HOLD: their L6M/X' cuts come from other weeks than July 2025.

### 6. Forfeit-target accounting (DS3_RISK_OFF_FINAL lesson), as-is RISK-KEEP cells
| family | as-is RISK-KEEP cells | median targets lost (live fired trades whose original exit was a target and now exit earlier) | range | median summed target distance of the lost trades (pts, 1 contract) | median live trades with a changed exit |
|---|---|---|---|---|---|
| L2SL | 114 | 216 | 0-367 | 12,960 | 4,358 |
| L2SP | 309 | 4,106 | 173-5,302 | 246,360 | 4,935 |
| UFL1 | 13 | 223 | 0-251 | 13,380 | 3,875 |
| UFL2 | 24 | 251 | 240-466 | 15,060 | 4,500 |
| UFL3 | 1 | 107 | 107-107 | 6,420 | 1,072 |

Every early-exit rule gives up targets: a L2SP take/trail rule exits thousands of live trades before their target (the p70 take line exits at 70% of the target by design), the L2SL tighten rules a few hundred. The mean change columns already contain the forfeited points; the count is shown so a reader sees what the drawdown cut costs in target hits.

### 7. Yardstick: the D6 pct>=0.70 take line (L2SP REF cell, run outside the selection)
As-is: maxDD cut L3M 80%, L6M 44%, HOLD 28%, PRE 24%, X' 45%; mean L6M +3064 (MDE 16678); placebo rank L6M/PRE/X' 0.129/0.214/0.085; label RISK-KEEP (volume effect). Composite: PRE 48%, X' -6%, L6M 10%, label no. Of the 285 distinct as-is L2SP RISK-KEEP series, 261 cut maxDD more than this line in both PRE and X' and 256 in all three windows: the thick/thin-book gate and the arm/trail variants add drawdown protection on top of the plain take line in the as-is frame (last column of the table shows the difference per row), but they touch a median 22% (range 4-34%) of the stack's gross P&L, which is why the placebo ranks sit at 0.005-0.10 rather than at the bottom.

### 8. Tie-out and method
- Null engine run (no injection), both frames: max daily difference vs the one-convention frames 0.0. Zero-delta, exit-unchanged injection on 5,000 random rows, both frames: 0.0 (`tieout_null.json` holds all four numbers).
- Rebuilt per-trade deltas vs the programs' stored arrays: max abs difference 3.7e-6 pt (float32), total-gain error <= 0.002% in every one of the 1,721 cells (L2SP re-run through the program's own numba kernel, `lp_kern.run`, with the exit row XR; L2SL tighten re-walked on the same 1-s path with the program's stop-market walk; UF-LOSS C1/C2/C6 first-fire rows re-derived from the program's condition engines; C3 hm_fire trigger + stored XI; C5 stored XI). The 'own-frame per-contract gain within 1%' gate is met with margin (<=2e-5).
- Reuse check: five cells rebuilt only from `exit_times.parquet` (drow, delta, exit second) reproduce the stored engine daily delta to $0.002 (float32 storage) in the as-is frame (`reuse_check.json`).
- Engine injection: rows' pts += stored delta; exit sample = searchsorted(SS, exit second) with a market-exit type for trades whose exit changes; half cuts and scale-out remainders that never exit early are delta-only (the engine holds the full position to its original exit, which is conservative for the lock governors, but the half-sized exposure after the cut is not modelled); L2SP half/lock actions: trades with W=2 exit at the last kernel exit row with the summed delta, W=1 (half taken, remainder runs) delta-only.
- Placebo: A1's 200-draw volume-matched random skip (36-point volume grid, volume = sum |delta| x engine size x PV over the cell's fired trades, as share of the frame's gross trade P&L); a random size-cut placebo was not run (a volume-matched skip is the stricter of the two for DD, A1 convention kept so the ranks are comparable with A1/A2).
- Equal-risk mean: the engine lot-table line (lscale on LN, integer half-up min-1 rounding, secant on ALL worst-20 = baseline) for every row shown in the tables plus the top 80 per frame; the linear scale (A1) for all other cells is in `cells_exact_final.parquet` (`*_ALL_er_dmean`).
- Deviations from the prereg (all after the scoring run, none changes a label definition): (a) the engine equal-risk coverage is the 30 rows of each table (both frames) plus the top 80 RISK-KEEP/volume-effect/L6M-only/carried series per frame in table order, not the 150 cells per frame in PRE+X' order the prereg named; (b) tables collapse engine-identical series and rank by tier then min(PRE,X') cut round-robin over L2SL / L2SP / UF-LOSS (a first draft ranked by L6M cut and was flooded by one family); (c) the REF cell (p70 take line) was run as a yardstick outside the selection; (d) the composite PRE-fix list is post-hoc (definition in the heading). Addendum with sha256 in DECISIONS.md.
- Windows: L3M 14 / L6M 28 / HOLD 32 / PRE 75 / X' 44 / ALL 149 weeks; the L6M as-is maxDD (88k) is the single week of 2026-01-19, the composite's is 23k.

### 9. D6 / D7 mapping and the L2 feature gap (Shadow/NEEDS only)
- L2SL tighten/half: D7 slot after the HM path rule; needs pulled_sup5/10/30, new-adverse-extreme flags, iceberg/sweep against, own-side depth ratio (DS3_THL2_NEEDS L2SL section); D6 computes only pct, imb10, pulled_sup10. Not computable in D6 today.
- L2SP: D6 profit line for the p70 take; the gated variants need ahead/total 8-tick depth vs the same-ET-hour median (hour_), vs the trailing 60 min (t60_), z vs the 30-minute bucket (z_), session median (sess_), thick-duration latch (DS3_THL2_NEEDS L2SP section); not computable in D6.
- UF-LOSS C1/C2: pulled-liquidity z, iceberg, sweep, wall-behind collapse, ES imbalance, refill/consumption flags; only the HM path rule exists in D6. C3/C5/C6: path-rule triggers (computable in D6) with remainder policies (stop-market tighten at MAE+X is a D6 loss line 'tighten') and book/trajectory flags that are not.
Nothing here is proposed for Sunday.

### 10. dead_lookup and ledger
dead_lookup first: all 1,721 simulated cells were found in DEAD_CELLS by (program, cell_id) (L2SL 518, L2SP 692 incl. REF, UFL1 101, UFL2 103, UFL3 104, UFL5 104, UFL6 100), i.e. these are re-pricings of scored cells, not new cells. append_cells after: program A6EV, one row per cell and frame (never rebuilt).

### 11. Questions (non-blocking)
1. Run the full engine sweep of L2SL tighten/half (5,877 cells, about 1.7 h on 3 workers) and the UF-LOSS main cells (about 2,200 cells, 40 min)? The random-sample rates say the screen misses most of the as-is RISK-KEEPs there (L2SL implied about 252 series), and a complete list would remove the screen from the selection.
2. L2SP is 23,772 cells; a full sweep is about 7 h on 3 workers. A stratified second tranche (another 2,000 cells chosen at random) would tighten the implied-count interval (now 2,258-5,808).
3. Which frame is the decision frame for Sunday's Shadow list: the composite (no RISK-KEEP) or the as-is stack (the research frame)? This report keeps both and ranks the as-is table; the composite PRE-fix leads are post-hoc and listed separately.
