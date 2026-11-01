# DS3_DD_REREAD_A11 - the L2SP family completed on the A6/A9 engine harness. A11, 2026-11-01T12:25Z. POST-HOC re-pricing, nothing promoted, no PASS claim, Shadow/NEEDS only

Prereg `l2vast/ds3/prereg/A11_L2SP_COMPLETE_prereg.md` sha256 39edff5961c0e144dc266566a1276eac27ec6a179ce6132933500d811c490fe1 (in DECISIONS.md before any engine run; this is the completion of a pre-stated sweep: A9 prereg 5656195a1ef12429fb09c10fe23f924270f0a4c67ba47031079b7582d9a41e7e and A6 prereg 8dadd44b554d0c03351bab0b63bfc2fb10f92c5e447af17590eecbc523d72339 named the full L2SP sweep; selection sha256 f9d35d64e8b13e87637cd11c994b080cce737c37a0f115940042fe0b1ec89b71, 21,081 cells in 15 seeded blocks, seed 20261111). A6/A9 engine harness unchanged (`code/ddre_a6` a6_lib/a6_ext; `code/ddre_a11` = run/score/final/er/rank/report/cluster copies of ddre_a9 with a block runner). Masks capped 20260206; no post-cap file opened (uf/loss1 stack*_daily.npz and the adduw grid untouched). Out `l2vast/ds3/out/dd_reread/a11/` (`cells_all.parquet`, `master_a11.parquet/csv`, `exit_times.parquet` = exit second of every fired trade of the A11 cells, `cluster_assign.csv`, `cluster_summary.json`).

**Plain sentence.** The L2SP sweep is complete: 23,772 of 23,772 eligible cells ran on the A6/A9 engine in both frames (A11 ran the remaining 21,081 in 15 seeded blocks, 0 errors, 0 tie-gate exclusions; tie-out null and zero-delta exactly 0.0 in both frames). **Exact L2SP counts, as-is: 2,693 RISK-KEEP cells (2,405 distinct series), 2,466 after the size-cut placebo, 1,576 after family-wise p <= 0.05, 983 FINAL (903 distinct; 568 cells / 540 distinct with HOLD cut >= 20%)**; all four A9 sampling estimates (2,575 / 2,402 / 930 / 12,505) fall inside their 95% intervals. **All three exit families together, as-is frame: 1,097 distinct series survive everything (RISK-KEEP, WY p <= 0.05 over the complete families, beat both placebos, PRE/X'/HOLD agree): L2SL 180, L2SP 903, UF-LOSS 14 (545 if HOLD must be cut by >= 20%). Composite frame: 0 FINAL** (10 L2SP RISK-KEEP cells, 2 of them with WY p <= 0.05, both deepen HOLD maxDD by 19-20%). **Independence (A10 method, rho >= 0.7):** A10's 387 re-cluster to 19 (check). Of the 710 new distinct survivors 690 join an existing A10 cluster (average rho >= 0.7; 396 of them into A10 cluster 11); 20 do not (best average rho 0.61-0.69, all L2SP p70never/thickonly variants, max single rho 0.66-0.76) and form 5 sub-groups, and in the union clustering they appear as 2 new clusters (5 series), so 22 clusters versus A10's 19: +2, not zero, but 5 of 710 series and each just under the 0.7 line. Caveats unchanged: the as-is L6M maxDD (88k) is the single week of 2026-01-19; L2SP survivors are the p70 take line plus a gate and touch a median of ~21% of the stack's gross P&L; nothing is a PASS; none of the L2 features is computable in D6.

## PAGE 1

### 1. L2SP family, exact (23,772 of 23,772 eligible L2SP cells)
| frame | L2SP cells run | carried | meets L6M | RISK-KEEP (A6 def) cells (distinct) | + size-cut placebo | + WY p<=0.05 | FINAL | FINAL strict |
|---|---|---|---|---|---|---|---|---|
| AS-IS | 23,772 | 12,282 | 16,900 | 2,693 (2,405) | 2,466 (2,253) | 1,576 (1,448) | 983 (903) | 568 (540) |
| COMPOSITE | 23,772 | 3,113 | 631 | 10 (9) | 10 (9) | 2 (2) | 0 (0) | 0 (0) |

A9's sampling estimate against the exact count:
| definition (as-is) | A9 sampling estimate [95%] | exact count, whole eligible set (cells) | inside the A9 interval? |
|---|---|---|---|
| RISK-KEEP (A6 def) | 2,575 [2,296, 2,888] | 2,693 | yes |
| RISK-KEEP + size-cut placebo | 2,402 [2,132, 2,707] | 2,466 | yes |
| FINAL | 930 [767, 1,132] | 983 | yes |
| carried | 12,505 [12,008, 13,001] | 12,282 | yes |

### 2. Final answer, all three exit families together (distinct engine series; identical series collapsed across programs, first occurrence)
| frame | distinct series with cells run | RISK-KEEP (A6 def) | + beats size-cut placebo | + WY p<=0.05 | FINAL: + PRE, X', HOLD>=0 agree | FINAL strict (HOLD>=20%) |
|---|---|---|---|---|---|---|
| AS-IS | 28,011 | 2,872 | 2,720 | 1,887 | 1,097 | 545 |
| COMPOSITE | 27,960 | 10 | 10 | 2 | 0 | 0 |

By program (first occurrence), as-is FINAL: L2SL 180, L2SP 903, UF-LOSS 14 (A9, with L2SP sampled: 387 = L2SL 180, L2SP 193, UF-LOSS 14). Composite frame FINAL by program: none.

### 3. Independence of the new survivors (A10's method: daily stack-delta series, 1 - rho, average linkage, cut 0.30 = rho >= 0.7)
| item | count |
|---|---|
| A10's 387 FINAL series re-clustered by the A10 method (check) | 19 |
| FINAL distinct series now (A10 387 + new) | 1097 |
| new FINAL distinct series (this run) | 710 |
|   of which join one of A10's 19 clusters (average rho >= 0.7 to the cluster) | 690 |
|   of which join none (candidate new independent series) | 20 |
| independent clusters among the non-joiners | 5 |
| clusters of the union (average linkage, rho >= 0.7) | 22 |
|   union clusters containing no A10 member (NEW independent clusters) | 2 |
|   union clusters with new members | 15 |
| best average rho of a new survivor to an A10 cluster: min / median / max | 0.61 / 0.86 / 0.98 |

### 4. The ledger table (cells; distinct series in brackets; engine-run cells = A6 + A9 + A11; as-is unless stated)
| program | ledger cells | eligible | engine-run | as-is carried | as-is meets L6M | as-is RISK-KEEP, A6 def: cells (distinct series) | RISK-KEEP + size-cut placebo (cells) | ... + WY p<=0.05: cells (distinct) | FINAL (+ PRE, X', HOLD>=0 agree): cells (distinct) | FINAL strict (HOLD>=20%): cells (distinct) | COMPOSITE RISK-KEEP: cells (distinct) | COMPOSITE FINAL: cells (distinct) | min WY p |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L2SL | 7,840 | 5,877 | 5,877 | 1,754 | 1,855 | 467 (412) | 467 | 437 (386) | 204 (180) | 7 (5) | 1 (1) | 0 (0) | 0.005 |
| L2SP | 23,773 | 23,772 | 23,772 | 12,282 | 16,900 | 2,693 (2,405) | 2,466 | 1,576 (1,448) | 983 (903) | 568 (540) | 10 (9) | 0 (0) | 0.005 |
| UFL1 | 480 | 406 | 406 | 35 | 61 | 14 (14) | 14 | 14 (14) | 7 (7) | 0 (0) | 0 (0) | 0 (0) | 0.005 |
| UFL2 | 522 | 480 | 480 | 96 | 195 | 44 (40) | 44 | 43 (39) | 7 (7) | 0 (0) | 0 (0) | 0 (0) | 0.005 |
| UFL3 | 402 | 352 | 352 | 16 | 20 | 1 (1) | 1 | 0 (0) | 0 (0) | 0 (0) | 0 (0) | 0 (0) | 0.005 |
| UFL5 | 576 | 576 | 576 | 23 | 49 | 0 (0) | 0 | 0 (0) | 0 (0) | 0 (0) | 0 (0) | 0 (0) | 0.050 |
| UFL6 | 336 | 334 | 334 | 0 | 79 | 0 (0) | 0 | 0 (0) | 0 (0) | 0 (0) | 0 (0) | 0 (0) | 0.592 |
| ALL | 33,929 | 31,797 | 31,797 | 14,206 | 19,159 | 3,219 (2,872) | 2,992 | 2,070 (1,887) | 1,201 (1,097) | 575 (545) | 11 (10) | 0 (0) | 0.005 |

Reading: carried = PRE and X' maxDD cut >= 20% with mean change not below -MDE in each; meets = L6M cut >= 20% and L6M and ALL mean not below -MDE; RISK-KEEP (A6 def) = carried and meets and beats the volume-matched random-skip placebo (L6M rank <= 0.05, PRE and X' <= 0.10); size-cut = also beats the random size-cut placebo; WY p = studentised Westfall-Young max-T (T = min(PRE z, X' z)) over the complete ledger of the program (every cell observed in all programs now, smallest attainable 0.005); FINAL = all of the above plus PRE cut >= 20%, X' cut >= 20% and HOLD cut >= 0 (strict: HOLD cut >= 20%). Not covered (as A6/A9): UF-LOSS C4 (48), C9 (432), 28 C1 extra and 42 C2 HM path-rule cells, C7/C8/C10, the L2SL cut actions (exact in A1).

## PAGE 2

### 5. Coverage and tie-out
| program | eligible | engine-run | coverage | max abs tie (pt) | max abs gain err |
|---|---|---|---|---|---|
| L2SL | 5,877 | 5877 | 100.0% | 3.7e-06 | 0.4942% |
| L2SP | 23,772 | 23772 | 100.0% | 0.0e+00 | 0.0000% |
| UFL1 | 406 | 406 | 100.0% | 3.7e-06 | 0.0006% |
| UFL2 | 480 | 480 | 100.0% | 3.7e-06 | 0.0017% |
| UFL3 | 352 | 352 | 100.0% | 0.0e+00 | 0.0000% |
| UFL5 | 576 | 576 | 100.0% | 0.0e+00 | 0.0000% |
| UFL6 | 334 | 334 | 100.0% | 3.7e-06 | 0.0037% |

Tie-out before any cell: null engine run (no injection) both frames max daily difference 0.0 / 0.0; zero-delta no-exit-change injection on 5,000 random rows 0.0 / 0.0 (`tieout_null.json`). Every cell: rebuilt per-trade delta equals the stored delta (gate 1e-4 pt) and total-gain error <= 1% (gate); cells failing are excluded and counted in `log_score.txt`.

### 6. Screen versus exact on the complete L2SP set (calibration)
| set | frame | n | corr PRE cut | corr X' cut | corr L6M cut | screen-carried | engine-carried | both | engine only | share missed by screen | screen only | screen RISK-KEEP | engine RISK-KEEP | both |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L2SP all run | AS-IS | 23772 | 0.79 | 0.92 | 0.54 | 10850 | 12282 | 9431 | 2851 | 23% | 1419 | 2983 | 2693 | 1071 |
| L2SP all run | COMPOSITE | 23772 | 0.96 | 0.90 | 0.73 | 3245 | 3113 | 2229 | 884 | 28% | 1016 | 20 | 10 | 10 |

### 7. Does HOLD agree? (as-is L2SP RISK-KEEP distinct series)
| group | as-is RISK-KEEP series (A6 def) | HOLD cut >= 0 | HOLD cut >= 20% | L3M cut >= 20% | L6M mean change > 0 | stack volume touched: median (range) | beat the size-cut placebo too |
|---|---|---|---|---|---|---|---|
| L2SP, all 23,772 run | 2405 | 71% | 48% | 100% | 33% | 17% (1%-38%) | 94% |

### 8. Forfeit-target accounting (as-is FINAL cells)
| program | as-is FINAL cells | median target exits forfeited (live fired) | range | median summed target distance (pts, 1 contract) | median live trades with a changed exit |
|---|---|---|---|---|---|
| L2SL | 204 | 190 | 57-261 | 11,400 | 4,081 |
| L2SP | 983 | 4,031 | 192-5,292 | 241,860 | 4,892 |
| UF-LOSS | 14 | 207 | 74-456 | 12,450 | 3,870 |

Every early-exit rule gives up targets (the mean change columns already contain the forfeited points).

### 9. Best 20 new L2SP FINAL series (as-is; rank: min(PRE, X', HOLD) cut)
| cell (L2SP) | maxDD cut L3M / L6M / HOLD / PRE / X' | maxDD after L3M / L6M / HOLD / PRE / X' / ALL | mean change $/wk (MDE) per window | skip-placebo rank L6M/PRE/X' | size-cut rank L6M/PRE/X' | WY p (23,773) | target exits forfeited | stack volume touched |
|---|---|---|---|---|---|---|---|---|
| P|t60_ahead_ge2.0|armpct0.3|d30|half10|p70always | 75% / 75% / 43% / 42% / 55% | 22k / 22k / 82k / 93k / 143k / 143k | L3M +2 (27576) ; L6M -1254 (17298) ; HOLD -901 (16088) ; PRE -3036 (10611) ; X +1920 (10049) | 0.005/0.030/0.050 | 0.005/0.050/0.005 | 0.025 | 5,283 | 28% |
| P|sess_ahead_ge2.0|armpts20|d30|trail10|p70always | 58% / 58% / 45% / 42% / 53% | 37k / 37k / 80k / 93k / 150k / 150k | L3M +2277 (26530) ; L6M -745 (15827) ; HOLD -804 (14867) ; PRE -2129 (9952) ; X +2421 (9805) | 0.015/0.040/0.070 | 0.005/0.055/0.005 | 0.040 | 5,281 | 28% |
| P|t60_ahead_ge2.0|armpct0.3|d30|take|p70always | 76% / 76% / 44% / 42% / 57% | 21k / 21k / 80k / 94k / 136k / 136k | L3M -26 (27739) ; L6M -1202 (17378) ; HOLD -798 (16193) ; PRE -3138 (10615) ; X +2029 (9895) | 0.005/0.035/0.035 | 0.005/0.055/0.005 | 0.025 | 5,284 | 28% |
| P|t60_ahead_ge2.0|armpct0.3|d30|half20|p70always | 75% / 75% / 42% / 42% / 58% | 22k / 22k / 84k / 94k / 133k / 133k | L3M -193 (26930) ; L6M -1521 (17029) ; HOLD -1128 (15831) ; PRE -2997 (10588) ; X +2637 (10105) | 0.005/0.035/0.035 | 0.005/0.050/0.005 | 0.025 | 5,279 | 27% |
| P|sess_ahead_ge2.0|armpct0.3|d30|half10|p70always | 57% / 57% / 49% / 42% / 56% | 38k / 38k / 74k / 94k / 139k / 139k | L3M +2074 (26616) ; L6M -714 (16113) ; HOLD -1102 (15507) ; PRE -1670 (10076) ; X +2828 (9562) | 0.025/0.045/0.050 | 0.005/0.065/0.005 | 0.040 | 5,282 | 29% |
| P|t60_ahead_ge2.0|armpct0.3|d30|trail5|p70always | 75% / 75% / 44% / 42% / 58% | 22k / 22k / 81k / 95k / 132k / 132k | L3M +25 (27720) ; L6M -1753 (17413) ; HOLD -1285 (16188) ; PRE -2912 (10643) ; X +2241 (9990) | 0.005/0.040/0.035 | 0.005/0.060/0.005 | 0.030 | 5,283 | 28% |
| P|sess_ahead_ge1.2|armpts40|d30|trail5|p70thickonly | 73% / 63% / 42% / 42% / 51% | 24k / 33k / 84k / 93k / 154k / 154k | L3M +3521 (23871) ; L6M -4309 (13515) ; HOLD -3079 (13132) ; PRE -1286 (8577) ; X +913 (9384) | 0.015/0.025/0.060 | 0.005/0.010/0.005 | 0.020 | 4,176 | 21% |
| P|z_tot_ge2.0|armpts40|d30|take|p70thickonly | 49% / 49% / 44% / 41% / 57% | 45k / 45k / 81k / 95k / 135k / 135k | L3M +2337 (26752) ; L6M -3789 (14270) ; HOLD -2055 (13705) ; PRE -2310 (7667) ; X +2146 (9676) | 0.030/0.030/0.020 | 0.005/0.005/0.005 | 0.040 | 3,597 | 18% |
| P|hour_ahead_ge2.0|armpts30|d30|half10|p70always | 79% / 74% / 41% / 44% / 53% | 19k / 23k / 84k / 90k / 150k / 150k | L3M +6583 (28018) ; L6M +3955 (16651) ; HOLD +3785 (15218) ; PRE -1223 (9524) ; X +2855 (9504) | 0.005/0.015/0.055 | 0.005/0.025/0.005 | 0.020 | 5,266 | 26% |
| P|hour_ahead_ge2.0|armpts30|d30|take|p70always | 79% / 76% / 41% / 44% / 51% | 19k / 21k / 84k / 91k / 154k / 154k | L3M +6539 (28024) ; L6M +3968 (16622) ; HOLD +3814 (15192) ; PRE -1203 (9514) ; X +2945 (9518) | 0.005/0.015/0.055 | 0.005/0.025/0.005 | 0.025 | 5,268 | 26% |
| P|sess_ahead_ge2.0|armpts20|d30|half20|p70always | 76% / 73% / 41% / 41% / 53% | 21k / 24k / 84k / 95k / 150k / 150k | L3M +4036 (27469) ; L6M +822 (16075) ; HOLD +470 (14988) ; PRE -2592 (9848) ; X +3265 (9857) | 0.005/0.040/0.075 | 0.005/0.065/0.005 | 0.040 | 5,277 | 28% |
| P|z_tot_ge2.0|armpts40|d30|trail5|p70thickonly | 48% / 48% / 45% / 41% / 57% | 46k / 46k / 80k / 95k / 136k / 136k | L3M +4993 (26577) ; L6M -2616 (14399) ; HOLD -1080 (13765) ; PRE -2209 (7849) ; X +2090 (9667) | 0.035/0.035/0.020 | 0.005/0.005/0.005 | 0.045 | 3,597 | 18% |
| P|sess_ahead_ge2.0|armpct0.3|d30|half20|p70always | 73% / 71% / 48% / 41% / 56% | 24k / 26k / 76k / 95k / 140k / 140k | L3M +3124 (26205) ; L6M -78 (15701) ; HOLD -416 (15080) ; PRE -2258 (10052) ; X +3389 (9666) | 0.005/0.045/0.050 | 0.005/0.065/0.005 | 0.040 | 5,277 | 28% |
| P|sess_ahead_ge2.0|armpts15|d30|trail30|p70always | 53% / 53% / 41% / 42% / 58% | 41k / 41k / 85k / 94k / 133k / 133k | L3M +1050 (28775) ; L6M -1143 (16748) ; HOLD -1157 (15359) ; PRE -853 (10325) ; X +3999 (10436) | 0.030/0.040/0.035 | 0.005/0.060/0.005 | 0.025 | 5,276 | 28% |
| P|t60_ahead_ge2.0|armpct0.3|d30|trail10|p70always | 71% / 71% / 41% / 41% / 53% | 26k / 26k / 84k / 96k / 148k / 148k | L3M -951 (27654) ; L6M -2287 (17371) ; HOLD -1858 (16111) ; PRE -2700 (10645) ; X +1868 (10225) | 0.005/0.040/0.055 | 0.005/0.065/0.005 | 0.040 | 5,283 | 28% |
| P|hour_ahead_ge1.2|armpts40|d30|trail5|p70thickonly | 71% / 62% / 41% / 48% / 55% | 25k / 34k / 86k / 84k / 141k / 141k | L3M +5705 (29027) ; L6M -2248 (15738) ; HOLD -1186 (14710) ; PRE -1846 (8911) ; X +1761 (9244) | 0.015/0.005/0.035 | 0.005/0.005/0.005 | 0.010 | 4,242 | 21% |
| P|sess_ahead_ge2.0|armpct0.3|d30|take|p70always | 69% / 56% / 41% / 42% / 53% | 28k / 39k / 86k / 94k / 148k / 148k | L3M +2601 (26472) ; L6M -439 (16196) ; HOLD -1292 (15501) ; PRE -1548 (10060) ; X +3041 (9521) | 0.030/0.045/0.075 | 0.005/0.065/0.005 | 0.040 | 5,284 | 29% |
| P|sess_ahead_ge2.0|armpct0.3|d30|trail20|p70always | 70% / 70% / 43% / 41% / 53% | 27k / 27k / 83k / 96k / 148k / 148k | L3M +4127 (27341) ; L6M +108 (16088) ; HOLD -389 (15282) ; PRE -1917 (10115) ; X +3344 (9915) | 0.005/0.045/0.060 | 0.005/0.065/0.005 | 0.040 | 5,277 | 28% |
| P|sess_ahead_ge1.2|armpts40|d30|half10|p70thickonly | 74% / 64% / 40% / 43% / 52% | 23k / 32k / 86k / 93k / 151k / 151k | L3M +3610 (23815) ; L6M -4246 (13489) ; HOLD -3115 (13142) ; PRE -890 (8535) ; X +954 (9433) | 0.010/0.025/0.045 | 0.005/0.010/0.005 | 0.020 | 4,172 | 21% |
| P|sess_ahead_ge2.0|armpct0.3|d30|trail5|p70always | 58% / 57% / 40% / 42% / 56% | 37k / 38k / 86k / 94k / 140k / 140k | L3M +2068 (26727) ; L6M -1281 (16158) ; HOLD -1943 (15425) ; PRE -1639 (10148) ; X +3123 (9618) | 0.025/0.045/0.055 | 0.005/0.065/0.005 | 0.040 | 5,283 | 29% |

### 10. dead_lookup and ledger
dead_lookup first: all 21,081 of 21,081 A11 cells found in DEAD_CELLS by (L2SP, idx<pos>) (DEAD_CELLS 1,448,164 rows before the append) i.e. re-pricings of scored cells. append_cells after: program A11EV, one row per cell and frame (as A9EV), never a rebuild.

### 11. Method notes
Placebos, WY nulls, size-cut seed 20261103, windows (L3M 14 / L6M 28 / HOLD 32 / PRE 75 / X' 44 / ALL 149 weeks) and the as-is L6M caveat (the 88k maxDD is the single week of 2026-01-19) are exactly A9's. L2SP survivors are the p70 take line plus gates and touch a median of about a fifth of the stack's gross P&L; none of the L2 features is computable in D6 (DS3_THL2_NEEDS). Nothing is proposed for Sunday.
