# WF M9: bracket scaled to range (W-M9 ran it, 2026-11-27; design W-WF49)

## ANSWER FIRST
**S2 (equal-weight Test 5 primary qualifiers, quick screen, REAL RE-SIMULATION with a per-bar bracket multiplier): drawdown falls a lot, at the 13-week step it PASSES in 3 of 4 sessions (LO, NY, NP) and in ALL; at 4 weeks only NP passes; at the 2-week step (Josh's rhythm) NOTHING passes. S1 (live mix stand-in): FAIL everywhere at every step. Nothing here is called "works".**
- Rule: stop and target x FM, FM = clip(trailing 20-day median daily NQ range at the bar's trading day / median daily range of all days before the decision date, 0.6, 1.6); lots x 1/FM so dollars at risk are equal. Decision steps 2, 4, 13 weeks (only the denominator is refreshed at the decision date; held cells follow the Test 5 13-week list as in M4/Test 12). Mean FM over the span = 1.27-1.29 (the range drifted up 2-3x; FM sits near the 1.6 clip in 2026), so the treated book runs ~21% smaller lots with ~27% wider brackets on average, much more in 2026.
- 2-WEEK STEP FIRST (standing rhythm), S2 primary: chained out-of-sample max DD untouched -> treated: AS -7630 -> -5862, LO -12211 -> -7423, NY -20874 -> -6007, NP -22899 -> -6800, ALL (sum of four) -34757 -> -8338; weekly income ALL 401 -> 612. But the per-period counts are weak: periods "good" (shallower, or higher income at no deeper DD) are only 38-46 of 77 (need 52): FAIL in every session (NP 46/77 p=0.055 closest; ALL 38/77). The drawdown gain is lumpy: it is one big 2026 episode, not a consistent every-2-week edge.
- 13-week step, S2: PASS LO (11/12 shallower, income -60 -> +22/wk), NY (9/12, income 139 -> 226), NP (9/12, 135 -> 205), ALL (9/12, 420 -> 611); FAIL AS (10/12 shallower but weekly income 206 -> 158 = -23%, rule needs >= -10%). 4-week step: only NP PASS (26/39 = exactly two thirds, p=0.027). Plain sign-test p-values are NOT corrected: M9 alone is 3 steps x 5 sessions x 2 subjects = 30 trials (plus the 9 other methods in the programme); best p 0.003 (LO at 13 weeks) is roughly 0.09 after a 30-trial Bonferroni, and 12 periods are not independent.
- Which step is best: the SLOWEST (13 weeks) passes most, because short periods have almost no drawdown to compare. Faster refit does not help here: FM already moves daily through the 20-day median; refreshing the fit-period denominator every 2 weeks changes it very little. So "faster" neither helps nor hurts the rule itself; it only makes the test noisier.
- Size-only control (reference, approximate): the same untouched series divided by the weekly mean FM (lots shrink, bracket NOT widened). It cuts ALL chained DD only -34757 -> -21927 (step 13) versus the primary -8128, and lifts income only 420 -> 389 (down) versus primary 611. So the bracket widening, not just smaller lots, carries most of the S2 gain. The control reflects the mechanical story: Test 5's fixed-point brackets (60/60, 30/30 ...) became too tight as NQ's range rose 2-3x in 2026; M9 re-scales them. That is a bracket-staleness repair, not evidence of a new edge.
- S1 stand-in (NOT the exact live mix; see below): FAIL in all 15 session/step cells; Asia and NP get deeper (chained DD AS -14492 -> -18450, NP -33512 -> -48398 at 2 weeks) and income falls ~35-45% in every session (ALL 8760 -> 5853 per week at 2 weeks). Where S1 books use fixed point brackets the wider bracket and 1/FM lots lowered income without a consistent DD gain.
- Not tested / limits: (1) exact engine layers (stack caps, daily-loss halts, sizer, kfix, live cut) are NOT in the quick screen; the engine has no bracket-multiplier input, so exact S1 was NOT run: it would be ~4 live sets x ~36 forward months = 144 set-months per decision step (and the multiplier differs per decision date, so the 2-week step needs its own rows: ~ 12 x more), NOT queued; LEAD to decide. (2) S1 here = the 17 mapped live books of Test 9 (old list; Asia 3, London 3, NY AM 7, NY PM 4), 1 lot each, fixed over the span (chosen on the same weeks: hindsight), no live layers or lots tables. (3) Lots 1/FM are fractional (0.625-1.67 of base), not rounded; NQ integer lots will blur it. (4) 0.2% of S2 cell-periods fell back to untouched (own-stop modules / no result, not scalable). (5) Pessimistic fill re-score (fee 4.84/lot, stop slippage) NOT run: wider stops would pay slippage on fewer points, so it is likely kinder to M9 than to untouched, but that is unproven. A PASS goes to the forward register as a candidate only.

## Method, validation, honesty
- Quick screen = gcore2x per-entry re-simulation on the 1-second tape (server C), own copy m9core.py = gcore2x.sim_slice with FM[b] multiplying (stop, target) at each entry and net points divided by FM[b] (lots 1/FM, cost scaled too). FM computed per bar from the trading day (sess_id//10) and the decision step. Variant 0 (FM=1) was run for every cell and compared with the stored walk5 grid weekly points: 4 pilot cells max error 6e-5 point; full comparison run on all cells that have a walk5 entry is in /mnt/l2/l2vast/_wf_m9 (val.py; see below).
- Cells: Test 5 primary (r=5) ever-held cells: 4075 cells in 2098 (row, module) jobs, plus the 17 Test 9 mapped live books; 2110 jobs, 4092 cells, 2091 result files (19 jobs = own-stop signal modules or empty, fallback untouched). 4 sims each (FM=1, steps 2/4/13), 32 niced procs, ~85 minutes, small npz (12 MB) in /mnt/l2/l2vast/_wf/m9/out (copy) and /mnt/l2/l2vast/_wf_m9/out on C.
- Subject S2 series: weekly $ = mean over the held cells of 20 x weekly points (per lot, equal weight), held list = latest 13-week Test 5 list at or before the period start (so at steps 2/4 the first week or two of a period use the previous list: same convention as M4). Nov 2025 weeks excluded. Untouched and treated use the same cells.
- Caveats: qualifiers are walk-forward (Test 5) so not hindsight, but Test 5 itself was tuned on these weeks; M9's parameters (20-day, 0.6-1.6 clip, fit = all days before decision) were fixed in advance, nothing was fitted. The benefit is concentrated in 2026 (below), when range ran 2-3x the early history: in 2023 and part of 2024 the treated drawdown is similar or worse. One regime episode is one data point.
- DD in $ at one lot per cell, equal-weight basket (basket dollars are per-cell averages x session).

## S2 side by side (drawdown first; U = untouched, T = M9; "good/shallower (of n)": good = shallower or higher income at no deeper DD)
| session | step | periods good/shallower (of n) | mean period DD U -> T | chained DD U -> T | worst week U -> T | weekly income U -> T | verdict (p) |
|---|---|---|---|---|---|---|---|
| AS | 2 | 39 / 25 (of 77) | -347 -> -292 | -7630 -> -5862 | -3877 -> -3223 | 189 -> 153 | FAIL (0.500) |
| AS | 4 | 23 / 21 (of 39) | -968 -> -806 | -7083 -> -5872 | -3877 -> -3223 | 223 -> 174 | FAIL (0.168) |
| AS | 13 | 10 / 10 (of 12) | -2726 -> -2297 | -7083 -> -5940 | -3877 -> -3223 | 206 -> 158 | FAIL (0.019) |
| LO | 2 | 43 / 20 (of 77) | -287 -> -216 | -12211 -> -7423 | -6462 -> -4106 | -59 -> 5 | FAIL (0.181) |
| LO | 4 | 20 / 18 (of 39) | -1133 -> -881 | -17452 -> -12903 | -6462 -> -4397 | -101 -> -49 | FAIL (0.500) |
| LO | 13 | 11 / 11 (of 12) | -3517 -> -2352 | -11940 -> -8024 | -6462 -> -4006 | -60 -> 22 | PASS (0.003) |
| NY | 2 | 43 / 22 (of 77) | -584 -> -404 | -20874 -> -6007 | -6438 -> -3375 | 140 -> 218 | FAIL (0.181) |
| NY | 4 | 25 / 21 (of 39) | -1644 -> -1146 | -21801 -> -6539 | -6438 -> -3385 | 131 -> 217 | FAIL (0.054) |
| NY | 13 | 9 / 9 (of 12) | -4381 -> -2569 | -22269 -> -6347 | -6438 -> -3274 | 139 -> 226 | PASS (0.073) |
| NP | 2 | 46 / 28 (of 77) | -621 -> -311 | -22899 -> -6800 | -4339 -> -3824 | 131 -> 236 | FAIL (0.055) |
| NP | 4 | 26 / 24 (of 39) | -1800 -> -1155 | -22405 -> -6151 | -4339 -> -3824 | 94 -> 260 | PASS (0.027) |
| NP | 13 | 9 / 9 (of 12) | -5265 -> -2886 | -23091 -> -6774 | -4339 -> -3740 | 135 -> 205 | PASS (0.073) |
| ALL | 2 | 38 / 17 (of 77) | -824 -> -485 | -34757 -> -8338 | -12299 -> -8338 | 401 -> 612 | FAIL (0.590) |
| ALL | 4 | 23 / 20 (of 39) | -2588 -> -1857 | -34285 -> -8221 | -12299 -> -8221 | 347 -> 603 | FAIL (0.168) |
| ALL | 13 | 9 / 9 (of 12) | -7954 -> -4786 | -34757 -> -8128 | -12299 -> -8128 | 420 -> 611 | PASS (0.073) |

## L3M / L6M (S2; DD over the window chained from the forward periods; income per week; L3M = weeks 169-181, L6M = 156-181)
| session | step | L3M DD U -> T | L3M worst wk U -> T | L3M income/wk U -> T | L6M DD U -> T | L6M worst wk U -> T | L6M income/wk U -> T |
|---|---|---|---|---|---|---|---|
| AS | 2 | -3189 -> -2147 | -1920 -> -1405 | 159 -> 189 | -3999 -> -4345 | -2455 -> -2912 | 614 -> 315 |
| LO | 2 | -5858 -> -2135 | -3458 -> -1187 | 200 -> 550 | -5858 -> -3065 | -3458 -> -1259 | 133 -> 247 |
| NY | 2 | -4696 -> -3264 | -2501 -> -2630 | 343 -> 147 | -9115 -> -3299 | -3134 -> -2630 | -73 -> 133 |
| NP | 2 | -5097 -> -2713 | -2559 -> -1413 | 398 -> 622 | -12126 -> -3323 | -4339 -> -2404 | 189 -> 456 |
| ALL | 2 | -10529 -> -5700 | -5280 -> -2990 | 1100 -> 1507 | -11188 -> -5700 | -6280 -> -4831 | 863 -> 1152 |
| AS | 4 | -3189 -> -2147 | -1920 -> -1405 | 159 -> 187 | -3999 -> -4345 | -2455 -> -2912 | 628 -> 328 |
| LO | 4 | -5858 -> -2135 | -3458 -> -1187 | 200 -> 549 | -5858 -> -3065 | -3458 -> -1259 | 116 -> 218 |
| NY | 4 | -4696 -> -3264 | -2501 -> -2630 | 343 -> 152 | -9115 -> -3277 | -3172 -> -2630 | -108 -> 115 |
| NP | 4 | -5097 -> -2709 | -2559 -> -1409 | 398 -> 623 | -10865 -> -3312 | -4339 -> -2393 | 245 -> 444 |
| ALL | 4 | -10529 -> -5648 | -5280 -> -2937 | 1100 -> 1511 | -10529 -> -5648 | -6280 -> -4831 | 881 -> 1105 |
| AS | 13 | -3189 -> -2146 | -1920 -> -1405 | 167 -> 141 | -3999 -> -4391 | -2455 -> -2947 | 618 -> 286 |
| LO | 13 | -5858 -> -2151 | -3458 -> -1187 | 187 -> 631 | -5858 -> -3052 | -3458 -> -1257 | 126 -> 288 |
| NY | 13 | -4696 -> -3264 | -2501 -> -2630 | 235 -> 129 | -10511 -> -3846 | -3134 -> -2630 | -126 -> 131 |
| NP | 13 | -5097 -> -2694 | -2559 -> -1394 | 271 -> 545 | -12126 -> -3531 | -4339 -> -2381 | 125 -> 438 |
| ALL | 13 | -10529 -> -5684 | -5280 -> -2893 | 860 -> 1446 | -11188 -> -5684 | -6280 -> -4831 | 743 -> 1143 |

## By year (S2, 2-week step; max DD of the chained curve in the year, weekly income)
| session (step 2) | year | max DD U -> T | weekly income U -> T |
|---|---|---|---|
| AS | 2023 | -511 -> -330 | 88 -> 95 |
| AS | 2024 | -5066 -> -3312 | 155 -> 172 |
| AS | 2025 | -4177 -> -4043 | 147 -> 157 |
| AS | 2026 | -7083 -> -5862 | 330 -> 140 |
| LO | 2023 | -1935 -> -1224 | -198 -> -146 |
| LO | 2024 | -8958 -> -7108 | 2 -> -24 |
| LO | 2025 | -7861 -> -6009 | -125 -> -54 |
| LO | 2026 | -5858 -> -3065 | 21 -> 197 |
| NY | 2023 | -2173 -> -1818 | 21 -> 61 |
| NY | 2024 | -4765 -> -3581 | 213 -> 216 |
| NY | 2025 | -7722 -> -4361 | 285 -> 281 |
| NY | 2026 | -20874 -> -6007 | -110 -> 199 |
| NP | 2023 | -1558 -> -2354 | -36 -> -6 |
| NP | 2024 | -6162 -> -6024 | 14 -> 101 |
| NP | 2025 | -9980 -> -4928 | 473 -> 261 |
| NP | 2026 | -22899 -> -3959 | -55 -> 413 |
| ALL | 2023 | -3118 -> -3283 | -125 -> 5 |
| ALL | 2024 | -5481 -> -6172 | 384 -> 466 |
| ALL | 2025 | -12634 -> -8338 | 781 -> 645 |
| ALL | 2026 | -34757 -> -5837 | 185 -> 948 |

## S1 stand-in (Test 9 mapped live books, quick screen, no live layers: FAIL everywhere)
| session | step | periods good/shallower (of n) | mean period DD U -> T | chained DD U -> T | worst week U -> T | weekly income U -> T | verdict (p) |
|---|---|---|---|---|---|---|---|
| AS | 2 | 30 / 13 (of 77) | -556 -> -571 | -14492 -> -18450 | -9157 -> -8886 | 1354 -> 764 | FAIL (0.980) |
| AS | 4 | 20 / 16 (of 39) | -1988 -> -2196 | -14492 -> -18468 | -9157 -> -8886 | 1364 -> 736 | FAIL (0.500) |
| AS | 13 | 5 / 5 (of 12) | -4982 -> -5824 | -14492 -> -18621 | -9157 -> -8886 | 1343 -> 747 | FAIL (0.806) |
| LO | 2 | 39 / 17 (of 77) | -1174 -> -1064 | -28293 -> -16918 | -15590 -> -11767 | 1408 -> 1124 | FAIL (0.500) |
| LO | 4 | 24 / 21 (of 39) | -3784 -> -3044 | -28293 -> -16904 | -15590 -> -11767 | 1461 -> 1160 | FAIL (0.100) |
| LO | 13 | 7 / 7 (of 12) | -8216 -> -7010 | -28293 -> -15910 | -15590 -> -11767 | 1432 -> 1213 | FAIL (0.387) |
| NY | 2 | 37 / 20 (of 77) | -2745 -> -2641 | -53761 -> -33948 | -25303 -> -20073 | 4204 -> 2820 | FAIL (0.676) |
| NY | 4 | 20 / 19 (of 39) | -8068 -> -7107 | -53761 -> -32002 | -25303 -> -20073 | 4152 -> 2807 | FAIL (0.500) |
| NY | 13 | 7 / 7 (of 12) | -17254 -> -15898 | -53761 -> -32177 | -25303 -> -20073 | 4119 -> 2749 | FAIL (0.387) |
| NP | 2 | 39 / 21 (of 77) | -1260 -> -1380 | -33512 -> -48398 | -12601 -> -23155 | 1794 -> 1146 | FAIL (0.500) |
| NP | 4 | 22 / 21 (of 39) | -3846 -> -4145 | -33512 -> -48386 | -12601 -> -23155 | 1836 -> 1084 | FAIL (0.261) |
| NP | 13 | 4 / 4 (of 12) | -10570 -> -13700 | -33512 -> -47146 | -12601 -> -23155 | 1705 -> 1114 | FAIL (0.927) |
| ALL | 2 | 29 / 11 (of 77) | -1991 -> -2246 | -60062 -> -43846 | -33566 -> -27114 | 8760 -> 5853 | FAIL (0.989) |
| ALL | 4 | 19 / 16 (of 39) | -7046 -> -7407 | -60062 -> -41790 | -33566 -> -28430 | 8814 -> 5787 | FAIL (0.625) |
| ALL | 13 | 7 / 7 (of 12) | -18953 -> -19492 | -60062 -> -42631 | -33566 -> -28341 | 8599 -> 5822 | FAIL (0.387) |

## Files
- Scoreboard: 60 lines (method M9: primary and ref:lots_only_approx x AS/LO/NY/NP/ALL x S1/S2 x steps 2/4/13) appended to /mnt/l2/l2vast/_wf/scoreboard_rows.jsonl (fields incl. step_weeks, chain_maxdd_U, chain_maxdd_T).
- Code: /mnt/l2/l2vast/_wf_m9 on C (build_jobs_m9.py, merge_jobs.py, gen_core.py -> m9core.py, m9_run.py, run_m9.sh, val.py); analysis /mnt/l2/l2vast/_wf/m9/m9_an.py, m9_sb.py, m9_res.pkl, m9_ser.pkl (local).
