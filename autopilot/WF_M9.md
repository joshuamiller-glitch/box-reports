# WF M9: bracket scaled to range (W-M9 ran it, 2026-11-27; design W-WF49)

## ANSWER FIRST
**S2 (equal-weight Test 5 primary qualifiers, quick screen, real re-simulation with a per-bar bracket multiplier): M9 cuts the chained out-of-sample drawdown by about three quarters and lifts income by about half, but it passes the programme rule only at the 13-week step, and only in LO, NY and NP; at the 2-week step (Josh's standing rhythm) and the 4-week step NOTHING passes. S1 (live-mix stand-in): FAIL at every step and session. Nothing here is called "works": the benefit is one 2026 regime episode.**
- Rule tested: stop and target x FM, FM = clip(trailing 20-day median daily NQ range at the bar's trading day / median daily range of all days before the decision date, 0.6, 1.6); lots x 1/FM (dollars at risk equal, cost scales with lots). Mean FM over the span 1.27-1.29: NQ's range ran 2-3x its early level, so FM sits near the 1.6 clip in 2026; the treated book averages ~21% smaller lots with ~27% wider brackets, much more in 2026.
- 2-WEEK STEP FIRST, S2: chained out-of-sample max DD untouched -> treated: AS -7177 -> -5862, LO -12620 -> -7423, NY -19583 -> -6007, NP -20989 -> -6800, ALL (sum of four) -33036 -> -8338; weekly income ALL 407 -> 612. Per-period counts do not reach two thirds (need 52 of 77): good periods AS 33, LO 45, NY 40, NP 42, ALL 40 -> FAIL everywhere (LO closest, plain p 0.086). 2-week periods hold at most two weeks, so drawdown comparisons are mostly ties or noise: the gain is one big drawdown (2026), not a consistent every-fortnight edge.
- 4-week step, S2: FAIL everywhere (good 19-23 of 39, need 26; ALL 19/39). Chained DD ALL -31746 -> -8221, income 367 -> 603.
- 13-week step, S2: PASS LO (11/12 shallower, income -57 -> +22/wk), NY (8/12, 130 -> 226), NP (9/12, 144 -> 205); FAIL AS (9/12 shallower, income 194 -> 158 = -19%, below the -10% limit) and FAIL ALL (7/12 shallower, plain p 0.39) although the chained curve is far shallower (-33036 -> -8128). PASS here = the programme rule; plain sign-test p-values are NOT corrected: M9 alone is 3 steps x 5 sessions x 2 subjects = 30 tries (programme: 10 methods), LO's 0.003 is ~0.09 after a 30-try Bonferroni; 12 periods are not independent.
- Best step: 13 weeks passes most simply because short periods rarely contain a drawdown to compare. Faster refit does not help (FM already moves daily through the 20-day median; refreshing the fit-period denominator every 2 weeks changes it very little) and does not hurt the rule; it only makes the test noisier.
- Size-only control (reference, approximate: untouched series divided by the weekly mean FM, bracket NOT widened): ALL chained DD -33036 -> -20734 (13 wk) versus M9 -8128, income 410 -> 387 (down) versus M9 611 (up). The control passes the count rule MORE often (steps 4 and 13: NY, NP; LO at 4; ALL at 4 and 13), because any size cut makes most periods shallower, so the pass counts are not evidence for the bracket idea; the depth and income gain beyond the size cut is. Reading: Test 5's fixed-point brackets (60/60, 30/30 ...) went stale as NQ's range rose 2-3x in 2026; M9 re-scales them. A bracket-staleness repair, not proof of an edge.
- S1 stand-in: FAIL 15 of 15 cells. AS and NP get deeper at all steps (chained AS -14492 -> -18450, NP -33512 -> -48398 at 2 weeks); LO and NY chained DD fall (-28293 -> -16918, -53761 -> -33948) but income falls 20-35% and per-period counts fail; ALL income 8760 -> 5853/wk at 2 weeks.
- NOT tested / limits: (1) exact engine layers (stack caps, daily-loss halts, sizer, live cut) are not in the quick screen, and the engine has no bracket-multiplier input, so exact S1 was NOT run: it would be about 4 live sets x ~36 forward months = 144 set-months per decision step (the multiplier differs per decision date: the 2-week step needs its own rows per date, roughly 6x the 13-week count). NOT queued; LEAD to decide. (2) S1 here = the 17 mapped live books of Test 9 (old list; Asia 3, London 3, NY AM 7, NY PM 4), 1 lot each, fixed over the span (chosen on the same weeks: hindsight), no live layers or lots tables. (3) Lots 1/FM are fractional (0.6-1.7 of base), not rounded. (4) ~0.2% of S2 cell-periods fell back to untouched (own-stop modules / no result, cannot be scaled). (5) The pessimistic-fill re-score (fee 4.84/lot, stop slippage) was NOT run; no PASS is registered as a forward candidate until it is. (6) L3M/L6M below are the forward chain only.

## Method, validation, honesty
- Quick screen = gcore2x per-entry re-simulation on the 1-second tape on server C; own copy m9core.py = gcore2x.sim_slice with FM[b] multiplying (stop, target) at each entry and net points divided by FM[b]. FM per bar from the bar's trading day (sess_id//10) and the decision step.
- Validation: variant FM=1 was run for every cell and compared with the stored walk5 grid weekly points: 3572 of 4070 cells (87.8%) reproduce to within 0.05 point (max error 6e-5); 498 do not (mostly bar rows changed since the grid was written: same 84% reproduction caveat as Test 7). To keep untouched and treated on ONE basis, the UNTOUCHED series is the FM=1 re-simulation of the same cells, not the stored grid points (an earlier version of this page mixed the two; those 60 scoreboard lines are superseded by 60 new lines carrying supersedes_earlier_m9_lines=true). Using stored points instead, or only the 3572 validated cells, gives the same chained-drawdown picture (ALL chain -30936 -> -6636 at 2 weeks, validated subset) and the same LO/NY/NP 13-week PASSes; on the validated subset ALL also passes at 13 weeks via the income branch (7/12 shallower, 8/12 higher income), so ALL is borderline either way.
- Cells: Test 5 primary (r=5) ever-held cells 4075 in 2098 (row, module) jobs plus the 17 Test 9 mapped live books = 2110 jobs, 4092 cells, 2091 result files (19 own-stop or empty). 4 sims each (FM=1, steps 2/4/13); 32 niced procs on C, ~85 min; 12 MB of npz (C: /mnt/l2/l2vast/_wf_m9/out; copy /mnt/l2/l2vast/_wf/m9/out). No engine rows queued, nothing deleted, no process killed.
- S2 series: weekly $ = mean over the held cells of 20 x weekly points per lot (equal weight); held list = latest 13-week Test 5 list at or before the period start (so at steps 2 and 4 the first one or two weeks of a period use the previous list: M4 convention). Nov 2025 weeks excluded. L3M = weeks 169-181, L6M = 156-181.
- Caveats: qualifiers are walk-forward (Test 5) but Test 5 itself was tuned on these weeks; M9's constants (20 days, 0.6-1.6 clip, fit = all days before the decision) were fixed in advance and nothing was fitted. The benefit is concentrated in 2026 (by-year table): in 2023 the treated drawdown is similar or worse (ALL 2023 -1868 -> -3283, 2024 -5431 -> -6172), 2025 mildly better, 2026 -33036 -> -5837.

## S2 side by side (drawdown first; U = untouched, T = M9; good = shallower, or higher income at no deeper DD; 2-week step first)
| session | step | periods good / shallower (of n) | mean period DD U -> T | chained DD U -> T | worst week U -> T | weekly income U -> T | verdict (plain p) |
|---|---|---|---|---|---|---|---|
| AS | 2 | 33 / 21 (of 77) | -336 -> -292 | -7177 -> -5862 | -4016 -> -3223 | 180 -> 153 | FAIL (0.914) |
| LO | 2 | 45 / 22 (of 77) | -301 -> -216 | -12620 -> -7423 | -5882 -> -4106 | -56 -> 5 | FAIL (0.086) |
| NY | 2 | 40 / 20 (of 77) | -559 -> -404 | -19583 -> -6007 | -6241 -> -3375 | 131 -> 218 | FAIL (0.410) |
| NP | 2 | 42 / 29 (of 77) | -557 -> -311 | -20989 -> -6800 | -4221 -> -3824 | 152 -> 236 | FAIL (0.247) |
| ALL | 2 | 40 / 17 (of 77) | -778 -> -485 | -33036 -> -8338 | -12307 -> -8338 | 407 -> 612 | FAIL (0.410) |
| AS | 4 | 20 / 18 (of 39) | -933 -> -806 | -7177 -> -5872 | -4016 -> -3223 | 218 -> 174 | FAIL (0.500) |
| LO | 4 | 22 / 21 (of 39) | -1157 -> -881 | -19640 -> -12903 | -5882 -> -4397 | -94 -> -49 | FAIL (0.261) |
| NY | 4 | 21 / 18 (of 39) | -1589 -> -1146 | -20496 -> -6539 | -6241 -> -3385 | 119 -> 217 | FAIL (0.375) |
| NP | 4 | 23 / 21 (of 39) | -1600 -> -1155 | -20635 -> -6151 | -4221 -> -3824 | 125 -> 260 | FAIL (0.168) |
| ALL | 4 | 19 / 16 (of 39) | -2351 -> -1857 | -31746 -> -8221 | -12307 -> -8221 | 367 -> 603 | FAIL (0.625) |
| AS | 13 | 9 / 9 (of 12) | -2686 -> -2297 | -7177 -> -5940 | -4016 -> -3223 | 194 -> 158 | FAIL (0.073) |
| LO | 13 | 11 / 11 (of 12) | -3445 -> -2352 | -13010 -> -8024 | -5882 -> -4006 | -57 -> 22 | PASS (0.003) |
| NY | 13 | 8 / 8 (of 12) | -4168 -> -2569 | -21104 -> -6347 | -6241 -> -3274 | 130 -> 226 | PASS (0.194) |
| NP | 13 | 9 / 9 (of 12) | -4580 -> -2886 | -20989 -> -6774 | -4221 -> -3740 | 144 -> 205 | PASS (0.073) |
| ALL | 13 | 7 / 7 (of 12) | -7153 -> -4786 | -33036 -> -8128 | -12307 -> -8128 | 410 -> 611 | FAIL (0.387) |

## L3M / L6M (S2, forward chain; income per week)
| session | step | L3M DD U -> T | L3M worst wk U -> T | L3M income/wk U -> T | L6M DD U -> T | L6M worst wk U -> T | L6M income/wk U -> T |
|---|---|---|---|---|---|---|---|
| AS | 2 | -2999 -> -2147 | -1816 -> -1405 | 151 -> 189 | -4116 -> -4345 | -2628 -> -2912 | 577 -> 315 |
| LO | 2 | -5342 -> -2135 | -2731 -> -1187 | 353 -> 550 | -5342 -> -3065 | -2731 -> -1259 | 179 -> 247 |
| NY | 2 | -4498 -> -3264 | -2386 -> -2630 | 251 -> 147 | -7851 -> -3299 | -2836 -> -2630 | -97 -> 133 |
| NP | 2 | -2871 -> -2713 | -1876 -> -1413 | 542 -> 622 | -10582 -> -3323 | -4221 -> -2404 | 165 -> 456 |
| ALL | 2 | -8731 -> -5700 | -4060 -> -2990 | 1298 -> 1507 | -9692 -> -5700 | -6351 -> -4831 | 825 -> 1152 |
| AS | 4 | -2999 -> -2147 | -1816 -> -1405 | 151 -> 187 | -4116 -> -4345 | -2628 -> -2912 | 603 -> 328 |
| LO | 4 | -5342 -> -2135 | -2731 -> -1187 | 353 -> 549 | -5342 -> -3065 | -2731 -> -1259 | 173 -> 218 |
| NY | 4 | -4498 -> -3264 | -2386 -> -2630 | 251 -> 152 | -7851 -> -3277 | -3223 -> -2630 | -132 -> 115 |
| NP | 4 | -2871 -> -2709 | -1876 -> -1409 | 542 -> 623 | -9978 -> -3312 | -4221 -> -2393 | 231 -> 444 |
| ALL | 4 | -8731 -> -5648 | -4060 -> -2937 | 1298 -> 1511 | -8731 -> -5648 | -6351 -> -4831 | 875 -> 1105 |
| AS | 13 | -2999 -> -2146 | -1816 -> -1405 | 154 -> 141 | -4116 -> -4391 | -2628 -> -2947 | 578 -> 286 |
| LO | 13 | -5342 -> -2151 | -2731 -> -1187 | 348 -> 631 | -5342 -> -3052 | -2731 -> -1257 | 177 -> 288 |
| NY | 13 | -4498 -> -3264 | -2386 -> -2630 | 134 -> 129 | -9372 -> -3846 | -2836 -> -2630 | -155 -> 131 |
| NP | 13 | -2871 -> -2694 | -1876 -> -1394 | 365 -> 545 | -10582 -> -3531 | -4221 -> -2381 | 77 -> 438 |
| ALL | 13 | -8731 -> -5684 | -4060 -> -2893 | 1002 -> 1446 | -9692 -> -5684 | -6351 -> -4831 | 677 -> 1143 |

## By year (S2, 2-week step; max DD of the chained curve in the year, weekly income)
| session (step 2) | year | max DD U -> T | weekly income U -> T |
|---|---|---|---|
| AS | 2023 | -270 -> -330 | 121 -> 95 |
| AS | 2024 | -4502 -> -3312 | 163 -> 172 |
| AS | 2025 | -4296 -> -4043 | 133 -> 157 |
| AS | 2026 | -7177 -> -5862 | 290 -> 140 |
| LO | 2023 | -1822 -> -1224 | -186 -> -146 |
| LO | 2024 | -9163 -> -7108 | -21 -> -24 |
| LO | 2025 | -8839 -> -6009 | -129 -> -54 |
| LO | 2026 | -5342 -> -3065 | 53 -> 197 |
| NY | 2023 | -2096 -> -1818 | 42 -> 61 |
| NY | 2024 | -5035 -> -3581 | 195 -> 216 |
| NY | 2025 | -6610 -> -4361 | 275 -> 281 |
| NY | 2026 | -19583 -> -6007 | -114 -> 199 |
| NP | 2023 | -1112 -> -2354 | 112 -> -6 |
| NP | 2024 | -5961 -> -6024 | 66 -> 101 |
| NP | 2025 | -8844 -> -4928 | 447 -> 261 |
| NP | 2026 | -20989 -> -3959 | -70 -> 413 |
| ALL | 2023 | -1868 -> -3283 | 89 -> 5 |
| ALL | 2024 | -5431 -> -6172 | 403 -> 466 |
| ALL | 2025 | -10169 -> -8338 | 727 -> 645 |
| ALL | 2026 | -33036 -> -5837 | 159 -> 948 |

## S1 stand-in (Test 9 mapped live books, quick screen, no live layers)
| session | step | periods good / shallower (of n) | mean period DD U -> T | chained DD U -> T | worst week U -> T | weekly income U -> T | verdict (plain p) |
|---|---|---|---|---|---|---|---|
| AS | 2 | 30 / 13 (of 77) | -556 -> -571 | -14492 -> -18450 | -9157 -> -8886 | 1354 -> 764 | FAIL (0.980) |
| LO | 2 | 39 / 17 (of 77) | -1174 -> -1064 | -28293 -> -16918 | -15590 -> -11767 | 1408 -> 1124 | FAIL (0.500) |
| NY | 2 | 37 / 20 (of 77) | -2745 -> -2641 | -53761 -> -33948 | -25303 -> -20073 | 4204 -> 2820 | FAIL (0.676) |
| NP | 2 | 39 / 21 (of 77) | -1260 -> -1380 | -33512 -> -48398 | -12601 -> -23155 | 1794 -> 1146 | FAIL (0.500) |
| ALL | 2 | 29 / 11 (of 77) | -1991 -> -2246 | -60062 -> -43846 | -33566 -> -27114 | 8760 -> 5853 | FAIL (0.989) |
| AS | 4 | 20 / 16 (of 39) | -1988 -> -2196 | -14492 -> -18468 | -9157 -> -8886 | 1364 -> 736 | FAIL (0.500) |
| LO | 4 | 24 / 21 (of 39) | -3784 -> -3044 | -28293 -> -16904 | -15590 -> -11767 | 1461 -> 1160 | FAIL (0.100) |
| NY | 4 | 20 / 19 (of 39) | -8068 -> -7107 | -53761 -> -32002 | -25303 -> -20073 | 4152 -> 2807 | FAIL (0.500) |
| NP | 4 | 22 / 21 (of 39) | -3846 -> -4145 | -33512 -> -48386 | -12601 -> -23155 | 1836 -> 1084 | FAIL (0.261) |
| ALL | 4 | 19 / 16 (of 39) | -7046 -> -7407 | -60062 -> -41790 | -33566 -> -28430 | 8814 -> 5787 | FAIL (0.625) |
| AS | 13 | 5 / 5 (of 12) | -4982 -> -5824 | -14492 -> -18621 | -9157 -> -8886 | 1343 -> 747 | FAIL (0.806) |
| LO | 13 | 7 / 7 (of 12) | -8216 -> -7010 | -28293 -> -15910 | -15590 -> -11767 | 1432 -> 1213 | FAIL (0.387) |
| NY | 13 | 7 / 7 (of 12) | -17254 -> -15898 | -53761 -> -32177 | -25303 -> -20073 | 4119 -> 2749 | FAIL (0.387) |
| NP | 13 | 4 / 4 (of 12) | -10570 -> -13700 | -33512 -> -47146 | -12601 -> -23155 | 1705 -> 1114 | FAIL (0.927) |
| ALL | 13 | 7 / 7 (of 12) | -18953 -> -19492 | -60062 -> -42631 | -33566 -> -28341 | 8599 -> 5822 | FAIL (0.387) |

## Files
- Scoreboard: /mnt/l2/l2vast/_wf/scoreboard_rows.jsonl has 120 M9 lines: the first 60 (mixed basis) are SUPERSEDED by the last 60 (take the last line per method/version/session/subject/step_weeks; supersedes_earlier_m9_lines=true). Versions: primary and ref:lots_only_approx, AS/LO/NY/NP/ALL, S1/S2, steps 2/4/13.
- Code on C: /mnt/l2/l2vast/_wf_m9 (build_jobs_m9.py, merge_jobs.py, gen_core.py -> m9core.py, m9_run.py, run_m9.sh, val.py, val2.py). Analysis (local): /mnt/l2/l2vast/_wf/m9/m9_an.py (M9MODE=A is the page basis), m9_sb.py, m9_resA.pkl, m9_serA.pkl.
