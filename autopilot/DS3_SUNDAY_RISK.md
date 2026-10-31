# DS3_SUNDAY_RISK - weekly mean, SD, maxDD, worst-20 of Sunday's D6 v2.3b as coded vs the stack as it is, leave-one-out, equal-risk (agent RK-1, follow-up order section 1)

Research only. Masks capped 20260206, UNTOUCHED never read. No new rules: every series is the stored SS-2 lock-engine output (`l2vast/ds3/out/sundaystack2/loo_<lots>_N_runmax.pkl`, causal running-max governors, basis N, D6 with the Native 1.28 stop) or the same SS-2 engine re-run with the stop at 2.45 for LIVE-CAL (`code/sundayrisk/rk_series.py`; tie-outs to SS-2 `s1_*` are exact, max abs difference 0.0 on D6 N, D6 CAL and as-is). Windows (own masks): L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131, ALL = 20230401..20260206. Weeks = ISO weeks of the engine calendar (edge weeks partial), so n is 14 / 28 / 32 / 75 / 44 / 149. $k per week. LIVE lots: K6 2, P6 7, U6 4, H6 4 Asia / 2 NY-AM, M6 2, A6 1 (user sessions; ST, WT, O6 not live). RESEARCH lots: ST10 HM10 WT7 KB5.2 SM7.4 PE5.6. "Stack as it is" = market entries, no rules, join stop 2.45 (identical in N and CAL, as in SS-2); "D6 as coded" = 70/30 @3 + PE 45-s confirm NY + ER(20) sizer with running-max locks + Asia-stopped cut50 + 8-line zone skip + Native 1.28 stop (N) or the same with the 2.45 join stop (LIVE-CAL).

## 0. Page 1: stack as it is vs Sunday's D6 as coded, LIVE lots, $k/week (basis N, Native 1.28)

| window (weeks) | as-is mean | SD | maxDD | worst-20 | D6 mean | SD | maxDD | worst-20 | D6-as-is mean [CI] | D6-as-is worst-20 [CI] |
|---|---|---|---|---|---|---|---|---|---|---|
| L3M (14) | 13.8 | 48 | 92 | 193 | 33.2 | 46 | 27 | 464 | +19.4 [+5.6, +33.1] | +271.1 [+77.8, +463.7] |
| L6M (28) | 24.0 | 47 | 92 | 68 | 42.6 | 42 | 27 | 401 | +18.5 [+9.4, +26.3] | +333.3 [+172.4, +506.3] |
| HOLD (32) | 23.7 | 56 | 144 | -178 | 39.9 | 52 | 93 | 165 | +16.2 [+7.5, +23.8] | +343.0 [+164.8, +493.4] |
| PRE (75) | 17.7 | 53 | 210 | -874 | 22.4 | 57 | 232 | -905 | +4.7 [-5.0, +16.1] | -31.2 [-295.7, +288.3] |
| X' (44) | -3.6 | 29 | 317 | -588 | 9.0 | 33 | 132 | -395 | +12.5 [+4.2, +21.0] | +193.5 [-26.9, +441.1] |

maxDD = peak-to-trough of the cumulative weekly $ inside the window (the SS-2 page used the daily path: L6M as-is 98 / D6 102, HOLD 155 / 109, PRE 232 / 267, X' 330 / 154; both in section 2). Worst-20 = sum of the 20 worst weeks; in L3M (14 wk), L6M (28), HOLD (32) it is nearly the window total, so it is edge, not tail, there (use CVaR5 / maxDD / worst week). CIs: 4-week block bootstrap (4,000 draws) of the paired weekly difference.

**Plain verdict, LIVE lots (tail measure: worst-20 where the window has >= 40 weeks, CVaR5 otherwise): L3M LOWERS (D6 tail lighter; CVaR5 difference +64.6k, CI +23.7..+64.6; maxDD -65k); L6M LOWERS (D6 tail lighter; CVaR5 difference +44.0k, CI +8.8..+64.6; maxDD -65k); HOLD LEAVES (D6 tail lighter; CVaR5 difference +18.3k, CI -17.4..+64.6; maxDD -50k); PRE LEAVES (D6 tail heavier; worst-20 difference -31.2k, CI -295.7..+288.3; maxDD +23k); X' LEAVES (D6 tail lighter; worst-20 difference +193.5k, CI -26.9..+441.1; maxDD -185k).**
**Research lots: L3M LOWERS (D6 tail lighter; CVaR5 difference +117.3k, CI +29.9..+248.1; maxDD -118k); L6M LOWERS (D6 tail lighter; CVaR5 difference +93.8k, CI +7.6..+193.9; maxDD -118k); HOLD LOWERS (D6 tail lighter; CVaR5 difference +67.3k, CI +17.3..+157.6; maxDD -313k); PRE LEAVES (D6 tail lighter; worst-20 difference +354.3k, CI -242.1..+1037.4; maxDD -252k); X' LEAVES (D6 tail lighter; worst-20 difference +233.4k, CI -337.6..+867.1; maxDD +24k).**
**LIVE-CAL (join 2.45), live lots: L3M LOWERS (D6 tail lighter; CVaR5 difference +69.0k, CI +23.2..+69.0; maxDD -69k); L6M LOWERS (D6 tail lighter; CVaR5 difference +44.7k, CI +5.9..+69.0; maxDD -69k); HOLD LEAVES (D6 tail lighter; CVaR5 difference +16.2k, CI -19.2..+69.0; maxDD -44k); PRE LEAVES (D6 tail heavier; worst-20 difference -87.5k, CI -360.5..+232.5; maxDD +43k); X' LEAVES (D6 tail lighter; worst-20 difference +156.7k, CI -64.7..+400.7; maxDD -173k).**
Over ALL 2023-04..2026-02 at live lots: worst-20 -1218 (as-is) vs -1124 (D6), maxDD 317 vs 232, SD 49 vs 51, mean 13.0 vs 22.5.
Equal risk (D6 scaled by 1.083 at live lots so its ALL-period worst-20 equals the stack as it is): the mean advantage is L3M +22.1k [+7.1, +37.0]; L6M +22.1k [+12.9, +30.1]; HOLD +19.5k [+10.3, +27.7]; PRE +6.6k [-3.7, +18.4]; X' +13.3k [+4.7, +22.2]; ALL 2023-04..2026-02 +11.4k [+4.8, +17.7]; section 4. Research lots (c on ALL-period worst-20): L3M +108.6k [+59.5, +169.5]; L6M +98.0k [+56.4, +136.4]; HOLD +90.9k [+59.0, +129.1]; PRE +34.8k [+13.6, +61.8]; X' +15.6k [-7.3, +37.9]; ALL 2023-04..2026-02 +41.6k [+23.7, +59.2].

**Caveat on the L3M / L6M / HOLD verdicts: they rest on very few weeks.** The single worst week of all three windows is 2026-01-19 (as-is -91.8k, D6 -27.2k at live lots); CVaR5 is that week (L3M) or the worst 2 weeks (L6M, 2) / 2 (HOLD). In the long windows (PRE 75 wk, X' 44 wk, ALL 149 wk), which carry the real tail evidence, no difference in worst-20 is distinguishable from zero in either direction.

## 1. Verdict per window (tail risk of the stack with D6 vs without)
Rule (stated before reading the intervals): LOWERS / RAISES only if the 95% block-bootstrap CI of the paired difference in the tail measure excludes 0; otherwise "LEAVES (not distinguishable)" and the point direction is given. Tail measure = worst-20 sum for windows with >= 40 weeks (PRE, X', ALL), CVaR5 (mean of the worst ceil(5% n) weeks) for L3M / L6M / HOLD. Difference is D6 minus as-is: positive = D6's bad weeks are less bad.

#### LIVE lots, N (Native 1.28)
| window | tail measure used | D6 - as-is | 95% CI | maxDD D6 vs as-is (wk-cum) | verdict |
|---|---|---|---|---|---|
| L3M | CVaR5 (n<40: worst-20 ~ the window sum) | +64.6k | [+23.7, +64.6] | -65k (lower; CI [-93, -24]) | **LOWERS**; D6 tail point estimate lighter |
| L6M | CVaR5 (n<40: worst-20 ~ the window sum) | +44.0k | [+8.8, +64.6] | -65k (lower; CI [-86, -7]) | **LOWERS**; D6 tail point estimate lighter |
| HOLD | CVaR5 (n<40: worst-20 ~ the window sum) | +18.3k | [-17.4, +64.6] | -50k (lower; CI [-101, +17]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |
| PRE | worst-20 sum | -31.2k | [-295.7, +288.3] | +23k (higher; CI [-131, +200]) | **LEAVES (not distinguishable)**; D6 tail point estimate heavier |
| X' | worst-20 sum | +193.5k | [-26.9, +441.1] | -185k (lower; CI [-415, -4]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |
| ALL 2023-04..2026-02 | worst-20 sum | +93.9k | [-152.1, +391.0] | -85k (lower; CI [-221, +117]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |

#### LIVE lots, LIVE-CAL (join 2.45)
| window | tail measure used | D6 - as-is | 95% CI | maxDD D6 vs as-is (wk-cum) | verdict |
|---|---|---|---|---|---|
| L3M | CVaR5 (n<40: worst-20 ~ the window sum) | +69.0k | [+23.2, +69.0] | -69k (lower; CI [-97, -23]) | **LOWERS**; D6 tail point estimate lighter |
| L6M | CVaR5 (n<40: worst-20 ~ the window sum) | +44.7k | [+5.9, +69.0] | -69k (lower; CI [-90, -4]) | **LOWERS**; D6 tail point estimate lighter |
| HOLD | CVaR5 (n<40: worst-20 ~ the window sum) | +16.2k | [-19.2, +69.0] | -44k (lower; CI [-96, +19]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |
| PRE | worst-20 sum | -87.5k | [-360.5, +232.5] | +43k (higher; CI [-112, +252]) | **LEAVES (not distinguishable)**; D6 tail point estimate heavier |
| X' | worst-20 sum | +156.7k | [-64.7, +400.7] | -173k (lower; CI [-399, +5]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |
| ALL 2023-04..2026-02 | worst-20 sum | +40.2k | [-205.8, +350.7] | -64k (lower; CI [-202, +157]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |

#### RESEARCH lots, N
| window | tail measure used | D6 - as-is | 95% CI | maxDD D6 vs as-is (wk-cum) | verdict |
|---|---|---|---|---|---|
| L3M | CVaR5 (n<40: worst-20 ~ the window sum) | +117.3k | [+29.9, +248.1] | -118k (lower; CI [-498, -53]) | **LOWERS**; D6 tail point estimate lighter |
| L6M | CVaR5 (n<40: worst-20 ~ the window sum) | +93.8k | [+7.6, +193.9] | -118k (lower; CI [-418, -22]) | **LOWERS**; D6 tail point estimate lighter |
| HOLD | CVaR5 (n<40: worst-20 ~ the window sum) | +67.3k | [+17.3, +157.6] | -313k (lower; CI [-744, -34]) | **LOWERS**; D6 tail point estimate lighter |
| PRE | worst-20 sum | +354.3k | [-242.1, +1037.4] | -252k (lower; CI [-577, +121]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |
| X' | worst-20 sum | +233.4k | [-337.6, +867.1] | +24k (higher; CI [-517, +231]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |
| ALL 2023-04..2026-02 | worst-20 sum | +472.1k | [-156.0, +1206.5] | -111k (lower; CI [-805, +73]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |

#### RESEARCH lots, LIVE-CAL
| window | tail measure used | D6 - as-is | 95% CI | maxDD D6 vs as-is (wk-cum) | verdict |
|---|---|---|---|---|---|
| L3M | CVaR5 (n<40: worst-20 ~ the window sum) | +109.8k | [+22.4, +242.0] | -110k (lower; CI [-487, -40]) | **LOWERS**; D6 tail point estimate lighter |
| L6M | CVaR5 (n<40: worst-20 ~ the window sum) | +86.0k | [-0.1, +188.2] | -110k (lower; CI [-406, -0]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |
| HOLD | CVaR5 (n<40: worst-20 ~ the window sum) | +59.2k | [+8.7, +152.5] | -296k (lower; CI [-724, -23]) | **LOWERS**; D6 tail point estimate lighter |
| PRE | worst-20 sum | +233.0k | [-331.7, +858.7] | -256k (lower; CI [-535, +150]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |
| X' | worst-20 sum | +108.3k | [-453.4, +741.5] | +65k (higher; CI [-447, +337]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |
| ALL 2023-04..2026-02 | worst-20 sum | +369.3k | [-220.2, +1080.2] | -70k (lower; CI [-740, +131]) | **LEAVES (not distinguishable)**; D6 tail point estimate lighter |

## 2. All statistics, as-is vs D6 (mean, SD, maxDD both ways, worst-20, worst-5, CVaR5, worst week and date, % negative weeks, longest losing streak)
(* = fewer than 20 weeks: the "worst-20" is the sum of all weeks.) CIs on the "D6 minus as-is" rows are 4-week block bootstrap.

#### LIVE lots, N
| window | config | n wk | mean | SD | maxDD (wk-cum) | maxDD (daily path) | worst-20 sum | worst-5 sum | CVaR5 (mean of worst k wk, k) | worst week (Mon) | % neg wk | longest losing streak (wk) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | stack as it is | 14 | 13.8 | 48 | 92 | 98 | 193* | -199 | -91.8 (1) | -91.8 (2026-01-19) | 36% | 1 |
|  | D6 as coded | 14 | 33.2 | 46 | 27 | 102 | 464* | -25 | -27.2 (1) | -27.2 (2026-01-19) | 14% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +19.4 [+5.6, +33.1] | -2.1 [-18.8, +5.7] | -64.6 [-93.0, -23.7] |  | +271.1 [+77.8, +463.7] |  | +64.6 [+23.7, +64.6] |  |  |  |
| L6M | stack as it is | 28 | 24.0 | 47 | 92 | 98 | 68 | -199 | -64.7 (2) | -91.8 (2026-01-19) | 29% | 1 |
|  | D6 as coded | 28 | 42.6 | 42 | 27 | 102 | 401 | -37 | -20.7 (2) | -27.2 (2026-01-19) | 7% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +18.5 [+9.4, +26.3] | -5.0 [-16.0, +7.2] | -64.6 [-85.8, -6.9] |  | +333.3 [+172.4, +506.3] |  | +44.0 [+8.8, +64.6] |  |  |  |
| HOLD | stack as it is | 32 | 23.7 | 56 | 144 | 155 | -178 | -278 | -85.3 (2) | -91.8 (2026-01-19) | 34% | 3 |
|  | D6 as coded | 32 | 39.9 | 52 | 93 | 109 | 165 | -175 | -67.0 (2) | -74.8 (2025-07-07) | 12% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +16.2 [+7.5, +23.8] | -4.6 [-13.7, +4.1] | -50.4 [-101.4, +17.4] |  | +343.0 [+164.8, +493.4] |  | +18.3 [-17.4, +64.6] |  |  |  |
| PRE | stack as it is | 75 | 17.7 | 53 | 210 | 232 | -874 | -435 | -91.2 (4) | -101.4 (2024-09-30) | 41% | 4 |
|  | D6 as coded | 75 | 22.4 | 57 | 232 | 267 | -905 | -413 | -86.7 (4) | -117.9 (2024-09-30) | 37% | 5 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +4.7 [-5.0, +16.1] | +4.0 [-4.6, +12.9] | +22.6 [-130.7, +199.7] |  | -31.2 [-295.7, +288.3] |  | +4.5 [-16.7, +26.9] |  |  |  |
| X' | stack as it is | 44 | -3.6 | 29 | 317 | 330 | -588 | -252 | -58.8 (3) | -71.0 (2023-06-26) | 48% | 6 |
|  | D6 as coded | 44 | 9.0 | 33 | 132 | 154 | -395 | -236 | -55.4 (3) | -67.2 (2023-12-18) | 43% | 5 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +12.5 [+4.2, +21.0] | +3.9 [-5.0, +10.5] | -185.4 [-414.7, -3.8] |  | +193.5 [-26.9, +441.1] |  | +3.4 [-21.2, +38.4] |  |  |  |
| ALL 2023-04..2026-02 | stack as it is | 149 | 13.0 | 49 | 317 | 330 | -1218 | -459 | -84.6 (8) | -101.4 (2024-09-30) | 41% | 6 |
|  | D6 as coded | 149 | 22.5 | 51 | 232 | 267 | -1124 | -422 | -76.8 (8) | -117.9 (2024-09-30) | 33% | 5 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +9.6 [+3.3, +15.1] | +1.8 [-4.3, +7.0] | -84.9 [-221.2, +117.0] |  | +93.9 [-152.1, +391.0] |  | +7.8 [-8.4, +24.2] |  |  |  |

#### LIVE lots, LIVE-CAL
| window | config | n wk | mean | SD | maxDD (wk-cum) | maxDD (daily path) | worst-20 sum | worst-5 sum | CVaR5 (mean of worst k wk, k) | worst week (Mon) | % neg wk | longest losing streak (wk) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | stack as it is | 14 | 13.8 | 48 | 92 | 98 | 193* | -199 | -91.8 (1) | -91.8 (2026-01-19) | 36% | 1 |
|  | D6 as coded | 14 | 30.9 | 45 | 23 | 111 | 433* | -28 | -22.8 (1) | -22.8 (2026-01-19) | 29% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +17.1 [+2.8, +31.6] | -2.9 [-19.8, +5.2] | -69.0 [-97.4, -23.2] |  | +239.9 [+39.7, +442.9] |  | +69.0 [+23.2, +69.0] |  |  |  |
| L6M | stack as it is | 28 | 24.0 | 47 | 92 | 98 | 68 | -199 | -64.7 (2) | -91.8 (2026-01-19) | 29% | 1 |
|  | D6 as coded | 28 | 40.2 | 42 | 23 | 111 | 355 | -40 | -20.0 (2) | -22.8 (2026-01-19) | 14% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +16.2 [+6.7, +24.6] | -5.6 [-16.5, +6.8] | -69.0 [-90.2, -4.0] |  | +287.4 [+119.3, +478.2] |  | +44.7 [+5.9, +69.0] |  |  |  |
| HOLD | stack as it is | 32 | 23.7 | 56 | 144 | 155 | -178 | -278 | -85.3 (2) | -91.8 (2026-01-19) | 34% | 3 |
|  | D6 as coded | 32 | 37.6 | 51 | 99 | 115 | 117 | -181 | -69.1 (2) | -77.1 (2025-07-07) | 19% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +13.9 [+4.8, +22.0] | -4.9 [-14.2, +3.9] | -44.4 [-95.6, +19.2] |  | +295.1 [+111.3, +464.1] |  | +16.2 [-19.2, +69.0] |  |  |  |
| PRE | stack as it is | 75 | 17.7 | 53 | 210 | 232 | -874 | -435 | -91.2 (4) | -101.4 (2024-09-30) | 41% | 4 |
|  | D6 as coded | 75 | 20.0 | 57 | 253 | 289 | -961 | -428 | -89.8 (4) | -121.8 (2024-09-30) | 41% | 5 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +2.3 [-7.6, +13.8] | +4.3 [-4.2, +13.2] | +43.2 [-111.6, +252.3] |  | -87.5 [-360.5, +232.5] |  | +1.4 [-20.4, +23.6] |  |  |  |
| X' | stack as it is | 44 | -3.6 | 29 | 317 | 330 | -588 | -252 | -58.8 (3) | -71.0 (2023-06-26) | 48% | 6 |
|  | D6 as coded | 44 | 7.3 | 33 | 144 | 166 | -431 | -246 | -57.2 (3) | -69.0 (2023-12-18) | 45% | 5 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +10.8 [+2.5, +19.2] | +4.1 [-4.8, +10.8] | -172.7 [-399.2, +5.4] |  | +156.7 [-64.7, +400.7] |  | +1.6 [-22.9, +36.4] |  |  |  |
| ALL 2023-04..2026-02 | stack as it is | 149 | 13.0 | 49 | 317 | 330 | -1218 | -459 | -84.6 (8) | -101.4 (2024-09-30) | 41% | 6 |
|  | D6 as coded | 149 | 20.3 | 51 | 253 | 289 | -1178 | -436 | -79.6 (8) | -121.8 (2024-09-30) | 37% | 5 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +7.3 [+0.9, +13.0] | +1.9 [-4.1, +7.1] | -64.3 [-202.5, +156.9] |  | +40.2 [-205.8, +350.7] |  | +5.0 [-11.0, +21.3] |  |  |  |

#### RESEARCH lots, N
| window | config | n wk | mean | SD | maxDD (wk-cum) | maxDD (daily path) | worst-20 sum | worst-5 sum | CVaR5 (mean of worst k wk, k) | worst week (Mon) | % neg wk | longest losing streak (wk) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | stack as it is | 14 | -1.0 | 141 | 274 | 417 | -14* | -677 | -273.2 (1) | -273.2 (2026-01-19) | 43% | 2 |
|  | D6 as coded | 14 | 94.2 | 153 | 156 | 453 | 1318* | -216 | -155.9 (1) | -155.9 (2025-12-01) | 29% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +95.2 [+52.3, +147.5] | +12.3 [-27.0, +23.6] | -117.7 [-497.5, -53.4] |  | +1332.8 [+732.5, +2064.9] |  | +117.3 [+29.9, +248.1] |  |  |  |
| L6M | stack as it is | 28 | 50.0 | 145 | 274 | 417 | -372 | -820 | -229.5 (2) | -273.2 (2026-01-19) | 29% | 2 |
|  | D6 as coded | 28 | 129.5 | 145 | 156 | 453 | 1268 | -415 | -135.7 (2) | -155.9 (2025-12-01) | 18% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +79.5 [+41.3, +113.7] | +0.3 [-28.8, +29.6] | -117.7 [-417.8, -21.6] |  | +1640.0 [+1137.7, +2185.0] |  | +93.8 [+7.6, +193.9] |  |  |  |
| HOLD | stack as it is | 32 | 37.2 | 173 | 684 | 684 | -1321 | -1154 | -287.0 (2) | -300.9 (2025-07-07) | 34% | 3 |
|  | D6 as coded | 32 | 112.1 | 168 | 372 | 453 | 288 | -786 | -219.7 (2) | -283.5 (2025-07-07) | 22% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +74.9 [+45.0, +108.6] | -4.9 [-27.5, +20.5] | -312.7 [-743.8, -33.6] |  | +1608.7 [+1162.6, +2129.1] |  | +67.3 [+17.3, +157.6] |  |  |  |
| PRE | stack as it is | 75 | 46.1 | 137 | 636 | 778 | -2620 | -1090 | -231.8 (4) | -322.6 (2024-11-18) | 39% | 3 |
|  | D6 as coded | 75 | 70.9 | 154 | 384 | 525 | -2265 | -1078 | -235.7 (4) | -304.1 (2024-03-11) | 29% | 3 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +24.7 [+5.0, +47.6] | +16.7 [-6.6, +38.6] | -252.2 [-576.7, +120.8] |  | +354.3 [-242.1, +1037.4] |  | -3.9 [-82.2, +113.3] |  |  |  |
| X' | stack as it is | 44 | 7.0 | 104 | 550 | 560 | -1661 | -833 | -180.4 (3) | -198.8 (2023-08-14) | 52% | 4 |
|  | D6 as coded | 44 | 19.8 | 107 | 573 | 625 | -1427 | -855 | -190.3 (3) | -217.7 (2023-04-03) | 39% | 3 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +12.8 [-8.9, +33.2] | +2.4 [-18.6, +18.9] | +23.6 [-517.3, +231.4] |  | +233.4 [-337.6, +867.1] |  | -9.9 [-51.8, +62.7] |  |  |  |
| ALL 2023-04..2026-02 | stack as it is | 149 | 33.3 | 139 | 684 | 778 | -3791 | -1362 | -243.9 (8) | -322.6 (2024-11-18) | 42% | 4 |
|  | D6 as coded | 149 | 65.6 | 149 | 573 | 625 | -3319 | -1289 | -224.7 (8) | -304.1 (2024-03-11) | 31% | 3 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +32.3 [+15.7, +47.1] | +10.1 [-5.6, +23.6] | -111.1 [-804.7, +73.2] |  | +472.1 [-156.0, +1206.5] |  | +19.2 [-34.8, +83.5] |  |  |  |

#### RESEARCH lots, LIVE-CAL
| window | config | n wk | mean | SD | maxDD (wk-cum) | maxDD (daily path) | worst-20 sum | worst-5 sum | CVaR5 (mean of worst k wk, k) | worst week (Mon) | % neg wk | longest losing streak (wk) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | stack as it is | 14 | -1.0 | 141 | 274 | 417 | -14* | -677 | -273.2 (1) | -273.2 (2026-01-19) | 43% | 2 |
|  | D6 as coded | 14 | 84.4 | 153 | 163 | 473 | 1182* | -264 | -163.4 (1) | -163.4 (2025-12-01) | 36% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +85.5 [+44.1, +137.3] | +12.0 [-26.3, +21.0] | -110.2 [-486.9, -40.5] |  | +1196.3 [+616.8, +1921.9] |  | +109.8 [+22.4, +242.0] |  |  |  |
| L6M | stack as it is | 28 | 50.0 | 145 | 274 | 417 | -372 | -820 | -229.5 (2) | -273.2 (2026-01-19) | 29% | 2 |
|  | D6 as coded | 28 | 118.2 | 143 | 163 | 473 | 1078 | -455 | -143.5 (2) | -163.4 (2025-12-01) | 21% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +68.2 [+28.6, +104.0] | -1.1 [-31.7, +28.4] | -110.2 [-405.7, -0.1] |  | +1450.1 [+948.4, +1977.1] |  | +86.0 [-0.1, +188.2] |  |  |  |
| HOLD | stack as it is | 32 | 37.2 | 173 | 684 | 684 | -1321 | -1154 | -287.0 (2) | -300.9 (2025-07-07) | 34% | 3 |
|  | D6 as coded | 32 | 101.4 | 166 | 388 | 473 | 136 | -820 | -227.8 (2) | -292.1 (2025-07-07) | 25% | 1 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +64.2 [+31.8, +99.0] | -6.4 [-30.7, +19.4] | -296.4 [-724.1, -23.1] |  | +1457.0 [+1013.5, +1956.8] |  | +59.2 [+8.7, +152.5] |  |  |  |
| PRE | stack as it is | 75 | 46.1 | 137 | 636 | 778 | -2620 | -1090 | -231.8 (4) | -322.6 (2024-11-18) | 39% | 3 |
|  | D6 as coded | 75 | 60.8 | 151 | 380 | 497 | -2387 | -1066 | -230.6 (4) | -280.7 (2024-09-30) | 33% | 4 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +14.7 [-5.4, +36.8] | +13.4 [-7.8, +34.2] | -255.9 [-534.6, +149.6] |  | +233.0 [-331.7, +858.7] |  | +1.2 [-61.6, +105.5] |  |  |  |
| X' | stack as it is | 44 | 7.0 | 104 | 550 | 560 | -1661 | -833 | -180.4 (3) | -198.8 (2023-08-14) | 52% | 4 |
|  | D6 as coded | 44 | 13.6 | 107 | 614 | 664 | -1553 | -881 | -196.4 (3) | -225.0 (2023-04-03) | 45% | 3 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +6.6 [-14.9, +26.7] | +2.3 [-18.3, +18.4] | +64.6 [-447.0, +336.9] |  | +108.3 [-453.4, +741.5] |  | -16.1 [-57.1, +57.8] |  |  |  |
| ALL 2023-04..2026-02 | stack as it is | 149 | 33.3 | 139 | 684 | 778 | -3791 | -1362 | -243.9 (8) | -322.6 (2024-11-18) | 42% | 4 |
|  | D6 as coded | 149 | 56.4 | 146 | 614 | 664 | -3422 | -1276 | -225.5 (8) | -292.1 (2025-07-07) | 36% | 4 |
|  | D6 minus as-is [4-wk block 95% CI] |  | +23.1 [+6.6, +38.0] | +7.6 [-7.7, +20.4] | -70.1 [-740.0, +131.3] |  | +369.3 [-220.2, +1080.2] |  | +18.4 [-28.6, +79.7] |  |  |  |

## 3. Leave-one-out and each piece alone
Cell = mean / SD / maxDD (weekly-cum) / worst-20 sum, $k per week. "Without X" = D6 with X switched off (SS-2 definitions: without the split the PE confirmation enters the whole lot at market; without the stop piece the join 2.45 applies; without ER the multiplier is 1). "Alone" = X on the stack as it is. Under LIVE-CAL every config uses the 2.45 stop, so the stop row does not exist.

Reading (live, N): the ER sizer ALONE on the stack is the one piece that heavies the tail (ALL worst-20 -1593 vs -1218, SD 60 vs 49, PRE worst-20 -1256 vs -874); inside the full D6 the running-max locks and the other pieces bring it back (D6 -1124), and removing the ER piece from D6 gives the lightest D6 tail (-957) at 3k/wk less mean in ALL. Removing the zone skip makes the D6 tail worst (-1312, maxDD 307).

#### LIVE lots, N
| config | L3M | L6M | HOLD | PRE | X' | ALL 2023-04..2026-02 |
|---|---|---|---|---|---|---|
| stack as it is | 13.8 / 48 / 92 / 193 | 24.0 / 47 / 92 / 68 | 23.7 / 56 / 144 / -178 | 17.7 / 53 / 210 / -874 | -3.6 / 29 / 317 / -588 | 13.0 / 49 / 317 / -1218 |
| D6 as coded (all pieces) | 33.2 / 46 / 27 / 464 | 42.6 / 42 / 27 / 401 | 39.9 / 52 / 93 / 165 | 22.4 / 57 / 232 / -905 | 9.0 / 33 / 132 / -395 | 22.5 / 51 / 232 / -1124 |
| D6 without 70/30 split | 27.9 / 49 / 51 / 391 | 39.8 / 45 / 51 / 341 | 36.9 / 55 / 120 / 75 | 20.5 / 57 / 231 / -993 | 8.2 / 33 / 138 / -401 | 20.7 / 52 / 231 / -1220 |
| D6 without PE 45-s confirm | 28.1 / 46 / 21 / 393 | 40.3 / 43 / 21 / 356 | 36.8 / 51 / 121 / 93 | 23.6 / 59 / 213 / -941 | 8.9 / 38 / 151 / -492 | 22.4 / 53 / 213 / -1166 |
| D6 without ER sizer + running-max locks | 21.6 / 40 / 58 / 302 | 32.3 / 42 / 58 / 228 | 30.1 / 46 / 81 / 34 | 21.0 / 47 / 174 / -716 | 8.3 / 28 / 152 / -356 | 19.5 / 43 / 174 / -957 |
| D6 without Asia-stopped cut50 | 34.0 / 45 / 20 / 476 | 43.1 / 45 / 26 / 376 | 40.9 / 53 / 79 / 157 | 23.3 / 58 / 231 / -887 | 7.8 / 34 / 147 / -426 | 22.8 / 52 / 231 / -1122 |
| D6 without 8-line zone skip | 30.8 / 55 / 67 / 432 | 40.4 / 44 / 67 / 397 | 39.1 / 59 / 131 / 117 | 20.6 / 61 / 307 / -1013 | 5.6 / 35 / 101 / -496 | 20.4 / 55 / 307 / -1312 |
| D6 without Native 1.28 stop | 30.9 / 45 / 23 / 433 | 40.2 / 42 / 23 / 355 | 37.6 / 51 / 99 / 117 | 20.0 / 57 / 253 / -961 | 7.3 / 33 / 144 / -431 | 20.3 / 51 / 253 / -1178 |
| 70/30 split alone on the stack | 14.1 / 43 / 70 / 197 | 24.4 / 44 / 70 / 81 | 24.1 / 52 / 126 / -134 | 17.5 / 50 / 198 / -834 | -0.7 / 29 / 219 / -533 | 13.8 / 46 / 219 / -1145 |
| PE 45-s confirm alone on the stack | 15.8 / 43 / 94 / 221 | 25.6 / 46 / 94 / 115 | 25.0 / 55 / 143 / -126 | 18.2 / 52 / 224 / -876 | -2.2 / 26 / 280 / -520 | 13.9 / 48 / 280 / -1210 |
| ER sizer + running-max locks alone on the stack | 18.3 / 60 / 93 / 257 | 30.6 / 51 / 93 / 180 | 29.9 / 64 / 172 / -121 | 14.7 / 65 / 284 / -1256 | 0.2 / 42 / 258 / -759 | 13.9 / 60 / 284 / -1593 |
| Asia-stopped cut50 alone on the stack | 14.8 / 43 / 74 / 207 | 26.2 / 43 / 74 / 143 | 25.2 / 55 / 162 / -122 | 18.8 / 51 / 180 / -834 | 0.4 / 28 / 166 / -499 | 15.0 / 48 / 180 / -1151 |
| 8-line zone skip alone on the stack | 11.7 / 41 / 90 / 164 | 27.1 / 45 / 90 / 158 | 25.9 / 48 / 90 / -22 | 18.2 / 51 / 197 / -863 | 2.0 / 30 / 292 / -494 | 15.3 / 46 / 292 / -1145 |
| Native 1.28 stop alone on the stack | 16.5 / 48 / 88 / 231 | 26.7 / 47 / 88 / 124 | 26.4 / 56 / 135 / -119 | 20.4 / 52 / 178 / -812 | -1.2 / 29 / 253 / -536 | 15.6 / 49 / 253 / -1154 |

#### LIVE lots, LIVE-CAL
| config | L3M | L6M | HOLD | PRE | X' | ALL 2023-04..2026-02 |
|---|---|---|---|---|---|---|
| stack as it is | 13.8 / 48 / 92 / 193 | 24.0 / 47 / 92 / 68 | 23.7 / 56 / 144 / -178 | 17.7 / 53 / 210 / -874 | -3.6 / 29 / 317 / -588 | 13.0 / 49 / 317 / -1218 |
| D6 as coded (all pieces) | 30.9 / 45 / 23 / 433 | 40.2 / 42 / 23 / 355 | 37.6 / 51 / 99 / 117 | 20.0 / 57 / 253 / -961 | 7.3 / 33 / 144 / -431 | 20.3 / 51 / 253 / -1178 |
| D6 without 70/30 split | 25.7 / 48 / 47 / 360 | 37.8 / 44 / 47 / 301 | 35.0 / 55 / 124 / 35 | 17.9 / 57 / 258 / -1057 | 6.4 / 33 / 150 / -436 | 18.4 / 52 / 258 / -1274 |
| D6 without PE 45-s confirm | 24.6 / 49 / 43 / 345 | 37.3 / 44 / 43 / 281 | 33.9 / 52 / 128 / 23 | 20.7 / 59 / 224 / -1009 | 7.2 / 38 / 165 / -530 | 19.8 / 53 / 224 / -1228 |
| D6 without ER sizer + running-max locks | 18.7 / 39 / 61 / 262 | 30.3 / 42 / 61 / 193 | 28.2 / 46 / 83 / -2.9 | 19.3 / 47 / 189 / -755 | 6.6 / 28 / 163 / -389 | 17.7 / 43 / 189 / -989 |
| D6 without Asia-stopped cut50 | 30.6 / 45 / 24 / 429 | 40.0 / 45 / 30 / 310 | 37.9 / 54 / 82 / 89 | 20.5 / 58 / 255 / -947 | 6.1 / 34 / 160 / -465 | 20.3 / 52 / 255 / -1180 |
| D6 without 8-line zone skip | 29.0 / 53 / 63 / 406 | 37.9 / 43 / 63 / 349 | 36.7 / 59 / 139 / 74 | 18.0 / 61 / 340 / -1067 | 3.3 / 35 / 126 / -559 | 17.9 / 55 / 340 / -1370 |
| 70/30 split alone on the stack | 14.1 / 43 / 70 / 197 | 24.4 / 44 / 70 / 81 | 24.1 / 52 / 126 / -134 | 17.5 / 50 / 198 / -834 | -0.7 / 29 / 219 / -533 | 13.8 / 46 / 219 / -1145 |
| PE 45-s confirm alone on the stack | 15.8 / 43 / 94 / 221 | 25.6 / 46 / 94 / 115 | 25.0 / 55 / 143 / -126 | 18.2 / 52 / 224 / -876 | -2.2 / 26 / 280 / -520 | 13.9 / 48 / 280 / -1210 |
| ER sizer + running-max locks alone on the stack | 18.3 / 60 / 93 / 257 | 30.6 / 51 / 93 / 180 | 29.9 / 64 / 172 / -121 | 14.7 / 65 / 284 / -1256 | 0.2 / 42 / 258 / -759 | 13.9 / 60 / 284 / -1593 |
| Asia-stopped cut50 alone on the stack | 14.8 / 43 / 74 / 207 | 26.2 / 43 / 74 / 143 | 25.2 / 55 / 162 / -122 | 18.8 / 51 / 180 / -834 | 0.4 / 28 / 166 / -499 | 15.0 / 48 / 180 / -1151 |
| 8-line zone skip alone on the stack | 11.7 / 41 / 90 / 164 | 27.1 / 45 / 90 / 158 | 25.9 / 48 / 90 / -22 | 18.2 / 51 / 197 / -863 | 2.0 / 30 / 292 / -494 | 15.3 / 46 / 292 / -1145 |

#### RESEARCH lots, N
| config | L3M | L6M | HOLD | PRE | X' | ALL 2023-04..2026-02 |
|---|---|---|---|---|---|---|
| stack as it is | -1.0 / 141 / 274 / -14 | 50.0 / 145 / 274 / -372 | 37.2 / 173 / 684 / -1321 | 46.1 / 137 / 636 / -2620 | 7.0 / 104 / 550 / -1661 | 33.3 / 139 / 684 / -3791 |
| D6 as coded (all pieces) | 94.2 / 153 / 156 / 1318 | 129.5 / 145 / 156 / 1268 | 112.1 / 168 / 372 / 288 | 70.9 / 154 / 384 / -2265 | 19.8 / 107 / 573 / -1427 | 65.6 / 149 / 573 / -3319 |
| D6 without 70/30 split | 84.1 / 151 / 167 / 1177 | 118.4 / 141 / 167 / 1073 | 101.1 / 165 / 417 / 90 | 60.0 / 154 / 355 / -2320 | 19.0 / 107 / 581 / -1439 | 57.5 / 148 / 581 / -3349 |
| D6 without PE 45-s confirm | 84.7 / 155 / 185 / 1186 | 125.9 / 148 / 185 / 1144 | 107.2 / 170 / 412 / 154 | 72.2 / 157 / 380 / -2309 | 22.0 / 114 / 594 / -1499 | 65.9 / 152 / 594 / -3419 |
| D6 without ER sizer + running-max locks | 84.4 / 110 / 138 / 1182 | 106.2 / 125 / 167 / 994 | 88.2 / 147 / 470 / 143 | 60.6 / 129 / 782 / -1833 | 15.5 / 97 / 452 / -1364 | 54.0 / 128 / 782 / -3086 |
| D6 without Asia-stopped cut50 | 82.1 / 142 / 161 / 1149 | 126.3 / 141 / 161 / 1293 | 111.7 / 160 / 291 / 356 | 73.8 / 149 / 315 / -2189 | 21.7 / 104 / 563 / -1287 | 67.6 / 143 / 563 / -3148 |
| D6 without 8-line zone skip | 69.2 / 182 / 220 / 969 | 112.2 / 157 / 220 / 734 | 100.8 / 183 / 434 / -199 | 64.6 / 173 / 337 / -2834 | 20.6 / 120 / 495 / -1643 | 60.3 / 164 / 495 / -3731 |
| D6 without Native 1.28 stop | 84.4 / 153 / 163 / 1182 | 118.2 / 143 / 163 / 1078 | 101.4 / 166 / 388 / 136 | 60.8 / 151 / 380 / -2387 | 13.6 / 107 / 614 / -1553 | 56.4 / 146 / 614 / -3422 |
| 70/30 split alone on the stack | 15.1 / 135 / 266 / 211 | 65.1 / 139 / 266 / 51 | 53.2 / 171 / 650 / -927 | 50.0 / 139 / 571 / -2540 | 9.5 / 103 / 511 / -1599 | 39.4 / 139 / 650 / -3585 |
| PE 45-s confirm alone on the stack | 5.9 / 138 / 272 / 83 | 54.6 / 144 / 272 / -261 | 41.5 / 173 / 682 / -1226 | 46.6 / 135 / 632 / -2523 | 7.7 / 102 / 525 / -1624 | 34.6 / 137 / 682 / -3684 |
| ER sizer + running-max locks alone on the stack | 59.5 / 193 / 294 / 833 | 93.2 / 159 / 294 / 395 | 79.4 / 182 / 529 / -582 | 46.6 / 175 / 445 / -3285 | 9.9 / 133 / 698 / -2021 | 43.5 / 167 / 698 / -4071 |
| Asia-stopped cut50 alone on the stack | 14.3 / 142 / 293 / 200 | 67.6 / 142 / 293 / -11 | 51.8 / 172 / 697 / -1034 | 46.1 / 139 / 728 / -2649 | 10.5 / 105 / 513 / -1649 | 37.4 / 139 / 728 / -3756 |
| 8-line zone skip alone on the stack | 38.3 / 111 / 209 / 537 | 72.4 / 134 / 209 / 224 | 56.6 / 151 / 523 / -609 | 49.5 / 130 / 778 / -2293 | 14.1 / 99 / 488 / -1430 | 41.2 / 128 / 778 / -3261 |
| Native 1.28 stop alone on the stack | 8.4 / 140 / 266 / 118 | 59.4 / 146 / 266 / -199 | 46.3 / 173 / 657 / -1142 | 56.0 / 139 / 581 / -2465 | 14.1 / 103 / 480 / -1494 | 42.3 / 139 / 657 / -3600 |

#### RESEARCH lots, LIVE-CAL
| config | L3M | L6M | HOLD | PRE | X' | ALL 2023-04..2026-02 |
|---|---|---|---|---|---|---|
| stack as it is | -1.0 / 141 / 274 / -14 | 50.0 / 145 / 274 / -372 | 37.2 / 173 / 684 / -1321 | 46.1 / 137 / 636 / -2620 | 7.0 / 104 / 550 / -1661 | 33.3 / 139 / 684 / -3791 |
| D6 as coded (all pieces) | 84.4 / 153 / 163 / 1182 | 118.2 / 143 / 163 / 1078 | 101.4 / 166 / 388 / 136 | 60.8 / 151 / 380 / -2387 | 13.6 / 107 / 614 / -1553 | 56.4 / 146 / 614 / -3422 |
| D6 without 70/30 split | 76.1 / 151 / 175 / 1065 | 109.3 / 141 / 175 / 902 | 91.9 / 165 / 437 / -94 | 50.0 / 152 / 444 / -2514 | 11.9 / 109 / 618 / -1612 | 48.4 / 147 / 618 / -3574 |
| D6 without PE 45-s confirm | 74.6 / 155 / 193 / 1044 | 113.9 / 147 / 193 / 945 | 95.9 / 169 / 429 / -38 | 60.9 / 155 / 380 / -2519 | 15.6 / 114 / 635 / -1640 | 55.9 / 150 / 635 / -3539 |
| D6 without ER sizer + running-max locks | 77.7 / 108 / 149 / 1088 | 98.9 / 123 / 164 / 849 | 81.8 / 145 / 477 / 9.3 | 53.8 / 129 / 833 / -2001 | 9.4 / 98 / 487 / -1510 | 47.5 / 128 / 833 / -3173 |
| D6 without Asia-stopped cut50 | 71.5 / 141 / 172 / 1001 | 115.9 / 141 / 172 / 1088 | 101.9 / 159 / 306 / 194 | 63.1 / 149 / 353 / -2392 | 15.0 / 104 / 613 / -1422 | 58.1 / 143 / 613 / -3332 |
| D6 without 8-line zone skip | 57.7 / 183 / 266 / 808 | 99.9 / 158 / 266 / 509 | 89.1 / 183 / 455 / -426 | 55.1 / 172 / 394 / -3019 | 10.7 / 121 / 541 / -1864 | 50.0 / 164 / 541 / -3939 |
| 70/30 split alone on the stack | 15.1 / 135 / 266 / 211 | 65.1 / 139 / 266 / 51 | 53.2 / 171 / 650 / -927 | 50.0 / 139 / 571 / -2540 | 9.5 / 103 / 511 / -1599 | 39.4 / 139 / 650 / -3585 |
| PE 45-s confirm alone on the stack | 5.9 / 138 / 272 / 83 | 54.6 / 144 / 272 / -261 | 41.5 / 173 / 682 / -1226 | 46.6 / 135 / 632 / -2523 | 7.7 / 102 / 525 / -1624 | 34.6 / 137 / 682 / -3684 |
| ER sizer + running-max locks alone on the stack | 59.5 / 193 / 294 / 833 | 93.2 / 159 / 294 / 395 | 79.4 / 182 / 529 / -582 | 46.6 / 175 / 445 / -3285 | 9.9 / 133 / 698 / -2021 | 43.5 / 167 / 698 / -4071 |
| Asia-stopped cut50 alone on the stack | 14.3 / 142 / 293 / 200 | 67.6 / 142 / 293 / -11 | 51.8 / 172 / 697 / -1034 | 46.1 / 139 / 728 / -2649 | 10.5 / 105 / 513 / -1649 | 37.4 / 139 / 728 / -3756 |
| 8-line zone skip alone on the stack | 38.3 / 111 / 209 / 537 | 72.4 / 134 / 209 / 224 | 56.6 / 151 / 523 / -609 | 49.5 / 130 / 778 / -2293 | 14.1 / 99 / 488 / -1430 | 41.2 / 128 / 778 / -3261 |

#### Contribution of each piece (D6 minus D6 without it), LIVE lots, N, with 4-week block bootstrap CIs
| piece (D6 minus D6-without) | L3M | L6M | HOLD | PRE | X' | ALL 2023-04..2026-02 |
|---|---|---|---|---|---|---|
| 70/30 split | mean +5.2 [+0.3, +11.9]; w20 +73 [+4.1, +166.7]; maxDD -24 | mean +2.8 [-0.5, +6.9]; w20 +61 [-5.3, +163.1]; maxDD -24 | mean +3.0 [-0.2, +6.6]; w20 +90 [+5.8, +179.2]; maxDD -26 | mean +1.9 [+0.0, +4.5]; w20 +88 [+8.4, +187.8]; maxDD +1 | mean +0.8 [-0.4, +2.3]; w20 +7 [-14.2, +33.9]; maxDD -6 | mean +1.8 [+0.5, +3.2]; w20 +96 [+15, +168.8]; maxDD +1 |
| PE 45-s confirm | mean +5.1 [-4.4, +15.7]; w20 +71 [-61.1, +219.8]; maxDD +7 | mean +2.3 [-2.8, +9.6]; w20 +46 [-52.6, +203.5]; maxDD +7 | mean +3.1 [-1.3, +9.4]; w20 +73 [-52.5, +204.6]; maxDD -28 | mean -1.1 [-5.1, +3.0]; w20 +37 [-123.4, +175.3]; maxDD +19 | mean +0.1 [-3.1, +3.9]; w20 +98 [+22.1, +193.7]; maxDD -19 | mean +0.1 [-2.4, +3.0]; w20 +42 [-108.5, +173.2]; maxDD +19 |
| ER sizer + running-max locks | mean +11.6 [-3.7, +21.1]; w20 +162 [-51.5, +295.4]; maxDD -31 | mean +10.2 [+2.9, +16.7]; w20 +173 [-35.6, +354.8]; maxDD -31 | mean +9.8 [+2.0, +15.7]; w20 +131 [-56.3, +310.7]; maxDD +12 | mean +1.4 [-5.2, +8.8]; w20 -189 [-395.6, +21.6]; maxDD +59 | mean +0.7 [-8.2, +6.9]; w20 -39 [-283.7, +79.6]; maxDD -20 | mean +3.0 [-1.7, +7.1]; w20 -167 [-360.4, +3.5]; maxDD +59 |
| Asia-stopped cut50 | mean -0.8 [-3.5, +2.1]; w20 -11 [-49.5, +29.2]; maxDD +7 | mean -0.6 [-3.2, +0.9]; w20 +26 [-4.7, +44]; maxDD +1 | mean -1.0 [-3.4, +0.5]; w20 +8 [-48.9, +44.2]; maxDD +14 | mean -0.9 [-2.9, +0.6]; w20 -18 [-115.3, +55.9]; maxDD +1 | mean +1.2 [+0.3, +2.1]; w20 +32 [+15.3, +52.3]; maxDD -15 | mean -0.3 [-1.5, +0.6]; w20 -2 [-74.3, +59]; maxDD +1 |
| 8-line zone skip | mean +2.3 [-4.9, +8.3]; w20 +33 [-68.5, +116.5]; maxDD -39 | mean +2.2 [-1.8, +5.7]; w20 +4 [-116.6, +133.1]; maxDD -39 | mean +0.7 [-2.0, +4.5]; w20 +48 [-103.1, +170.4]; maxDD -37 | mean +1.8 [-3.9, +8.0]; w20 +108 [-67, +297.9]; maxDD -75 | mean +3.3 [-0.5, +8.7]; w20 +102 [-17, +280]; maxDD +31 | mean +2.1 [-1.2, +5.6]; w20 +188 [+26.7, +364.7]; maxDD -75 |
| Native 1.28 stop | mean +2.2 [+1.2, +3.1]; w20 +31 [+17.5, +43.6]; maxDD +4 | mean +2.3 [+1.5, +3.0]; w20 +46 [+23.1, +61.6]; maxDD +4 | mean +2.3 [+1.6, +3.0]; w20 +48 [+25.1, +64.6]; maxDD -6 | mean +2.4 [+2.1, +2.9]; w20 +56 [+47.1, +73.5]; maxDD -21 | mean +1.7 [+1.5, +2.1]; w20 +37 [+31.9, +48.9]; maxDD -13 | mean +2.2 [+1.9, +2.5]; w20 +54 [+37.1, +65.1]; maxDD -21 |

(Research-lot and LIVE-CAL contributions: `out/sundayrisk/risk_boot.csv`, cmp `FULL-LOO|<piece>`.)

## 4. Equal risk: D6 scaled to the stack's tail, so that variance is separated from edge
Lot factor c multiplies EVERY D6 lot (the governor R is proportional to lots, so the weekly $ scale exactly linearly in c; integer-lot rounding ignored). c is solved on the ALL 2023-04..2026-02 window (149 weeks), the only window where the 20 worst weeks are a tail and both stacks' worst-20 sums are negative; windows PRE and X' have their own factor where defined. c > 1 means D6 has the LIGHTER tail and can be run at more size for the same worst-20.

#### LIVE lots, N
| factor basis | c | window | D6 x c mean | D6 x c SD | D6 x c maxDD | D6 x c worst-20 | as-is mean / SD / maxDD / worst-20 | mean difference at equal risk [CI] |
|---|---|---|---|---|---|---|---|---|
| worst-20 over ALL 2023-04..2026-02 | 1.083 | L3M | 35.9 | 50 | 29 | 503 | 13.8 / 48 / 92 / 193 | +22.1 [+7.1, +37.0] |
| worst-20 over ALL 2023-04..2026-02 | 1.083 | L6M | 46.1 | 46 | 29 | 435 | 24.0 / 47 / 92 / 68 | +22.1 [+12.9, +30.1] |
| worst-20 over ALL 2023-04..2026-02 | 1.083 | HOLD | 43.2 | 56 | 101 | 179 | 23.7 / 56 / 144 / -178 | +19.5 [+10.3, +27.7] |
| worst-20 over ALL 2023-04..2026-02 | 1.083 | PRE | 24.3 | 61 | 252 | -980 | 17.7 / 53 / 210 / -874 | +6.6 [-3.7, +18.4] |
| worst-20 over ALL 2023-04..2026-02 | 1.083 | X' | 9.7 | 36 | 143 | -428 | -3.6 / 29 / 317 / -588 | +13.3 [+4.7, +22.2] |
| worst-20 over ALL 2023-04..2026-02 | 1.083 | ALL 2023-04..2026-02 | 24.4 | 55 | 252 | -1218 | 13.0 / 49 / 317 / -1218 | +11.4 [+4.8, +17.7] |
| maxDD over ALL | 1.366 | L3M | 45.3 | 63 | 37 | 634 | 13.8 / 48 / 92 / 193 | +31.5 [+13.6, +49.4] |
| maxDD over ALL | 1.366 | L6M | 58.1 | 58 | 37 | 548 | 24.0 / 47 / 92 / 68 | +34.1 [+24.2, +42.9] |
| maxDD over ALL | 1.366 | HOLD | 54.5 | 71 | 127 | 226 | 23.7 / 56 / 144 / -178 | +30.8 [+20.3, +40.4] |
| maxDD over ALL | 1.366 | PRE | 30.6 | 77 | 317 | -1236 | 17.7 / 53 / 210 / -874 | +12.9 [-0.2, +28.6] |
| maxDD over ALL | 1.366 | X' | 12.3 | 45 | 180 | -539 | -3.6 / 29 / 317 / -588 | +15.8 [+6.4, +26.5] |
| maxDD over ALL | 1.366 | ALL 2023-04..2026-02 | 30.7 | 69 | 317 | -1535 | 13.0 / 49 / 317 / -1218 | +17.8 [+9.5, +26.0] |
| SD over ALL | 0.965 | L3M | 32.0 | 44 | 26 | 448 | 13.8 / 48 / 92 / 193 | +18.2 [+4.7, +31.9] |
| SD over ALL | 0.965 | L6M | 41.1 | 41 | 26 | 387 | 24.0 / 47 / 92 / 68 | +17.0 [+7.6, +24.8] |
| SD over ALL | 0.965 | HOLD | 38.5 | 50 | 90 | 159 | 23.7 / 56 / 144 / -178 | +14.8 [+5.7, +22.6] |
| SD over ALL | 0.965 | PRE | 21.6 | 55 | 224 | -873 | 17.7 / 53 / 210 / -874 | +3.9 [-5.1, +14.3] |
| SD over ALL | 0.965 | X' | 8.7 | 32 | 127 | -381 | -3.6 / 29 / 317 / -588 | +12.2 [+3.9, +20.5] |
| SD over ALL | 0.965 | ALL 2023-04..2026-02 | 21.7 | 49 | 224 | -1085 | 13.0 / 49 / 317 / -1218 | +8.8 [+2.7, +14.3] |

Per-window factor on worst-20:

| window | c (D6 scaled to the as-is worst-20 in that window) |
|---|---|
| L3M | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| L6M | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| HOLD | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| PRE | 0.966 |
| X' | 1.490 |
| ALL 2023-04..2026-02 | 1.083 |

#### LIVE lots, LIVE-CAL
| factor basis | c | window | D6 x c mean | D6 x c SD | D6 x c maxDD | D6 x c worst-20 | as-is mean / SD / maxDD / worst-20 | mean difference at equal risk [CI] |
|---|---|---|---|---|---|---|---|---|
| worst-20 over ALL 2023-04..2026-02 | 1.034 | L3M | 32.0 | 47 | 24 | 448 | 13.8 / 48 / 92 / 193 | +18.2 [+3.2, +33.2] |
| worst-20 over ALL 2023-04..2026-02 | 1.034 | L6M | 41.6 | 43 | 24 | 368 | 24.0 / 47 / 92 / 68 | +17.6 [+7.8, +26.0] |
| worst-20 over ALL 2023-04..2026-02 | 1.034 | HOLD | 38.9 | 53 | 103 | 121 | 23.7 / 56 / 144 / -178 | +15.2 [+5.5, +23.7] |
| worst-20 over ALL 2023-04..2026-02 | 1.034 | PRE | 20.7 | 59 | 261 | -994 | 17.7 / 53 / 210 / -874 | +2.9 [-7.0, +14.2] |
| worst-20 over ALL 2023-04..2026-02 | 1.034 | X' | 7.5 | 35 | 149 | -446 | -3.6 / 29 / 317 / -588 | +11.1 [+2.6, +19.6] |
| worst-20 over ALL 2023-04..2026-02 | 1.034 | ALL 2023-04..2026-02 | 21.0 | 53 | 261 | -1218 | 13.0 / 49 / 317 / -1218 | +8.0 [+1.6, +14.0] |
| maxDD over ALL | 1.255 | L3M | 38.8 | 57 | 29 | 544 | 13.8 / 48 / 92 / 193 | +25.0 [+7.7, +42.4] |
| maxDD over ALL | 1.255 | L6M | 50.5 | 52 | 29 | 446 | 24.0 / 47 / 92 / 68 | +26.4 [+16.5, +35.6] |
| maxDD over ALL | 1.255 | HOLD | 47.2 | 64 | 125 | 147 | 23.7 / 56 / 144 / -178 | +23.5 [+13.1, +33.1] |
| maxDD over ALL | 1.255 | PRE | 25.1 | 71 | 317 | -1206 | 17.7 / 53 / 210 / -874 | +7.4 [-4.8, +21.5] |
| maxDD over ALL | 1.255 | X' | 9.1 | 42 | 181 | -541 | -3.6 / 29 / 317 / -588 | +12.7 [+3.7, +22.5] |
| maxDD over ALL | 1.255 | ALL 2023-04..2026-02 | 25.4 | 64 | 317 | -1478 | 13.0 / 49 / 317 / -1218 | +12.5 [+4.8, +20.0] |
| SD over ALL | 0.963 | L3M | 29.8 | 43 | 22 | 417 | 13.8 / 48 / 92 / 193 | +16.0 [+1.9, +30.3] |
| SD over ALL | 0.963 | L6M | 38.7 | 40 | 22 | 342 | 24.0 / 47 / 92 / 68 | +14.7 [+4.8, +23.0] |
| SD over ALL | 0.963 | HOLD | 36.2 | 49 | 96 | 113 | 23.7 / 56 / 144 / -178 | +12.5 [+2.9, +20.8] |
| SD over ALL | 0.963 | PRE | 19.2 | 55 | 243 | -925 | 17.7 / 53 / 210 / -874 | +1.5 [-7.7, +12.0] |
| SD over ALL | 0.963 | X' | 7.0 | 32 | 139 | -415 | -3.6 / 29 / 317 / -588 | +10.6 [+2.2, +18.7] |
| SD over ALL | 0.963 | ALL 2023-04..2026-02 | 19.5 | 49 | 243 | -1134 | 13.0 / 49 / 317 / -1218 | +6.6 [+0.5, +12.2] |

Per-window factor on worst-20:

| window | c (D6 scaled to the as-is worst-20 in that window) |
|---|---|
| L3M | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| L6M | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| HOLD | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| PRE | 0.909 |
| X' | 1.363 |
| ALL 2023-04..2026-02 | 1.034 |

#### RESEARCH lots, N
| factor basis | c | window | D6 x c mean | D6 x c SD | D6 x c maxDD | D6 x c worst-20 | as-is mean / SD / maxDD / worst-20 | mean difference at equal risk [CI] |
|---|---|---|---|---|---|---|---|---|
| worst-20 over ALL 2023-04..2026-02 | 1.142 | L3M | 107.6 | 175 | 178 | 1506 | -1.0 / 141 / 274 / -14 | +108.6 [+59.5, +169.5] |
| worst-20 over ALL 2023-04..2026-02 | 1.142 | L6M | 148.0 | 165 | 178 | 1449 | 50.0 / 145 / 274 / -372 | +98.0 [+56.4, +136.4] |
| worst-20 over ALL 2023-04..2026-02 | 1.142 | HOLD | 128.1 | 192 | 425 | 329 | 37.2 / 173 / 684 / -1321 | +90.9 [+59.0, +129.1] |
| worst-20 over ALL 2023-04..2026-02 | 1.142 | PRE | 80.9 | 176 | 438 | -2588 | 46.1 / 137 / 636 / -2620 | +34.8 [+13.6, +61.8] |
| worst-20 over ALL 2023-04..2026-02 | 1.142 | X' | 22.6 | 122 | 655 | -1631 | 7.0 / 104 / 550 / -1661 | +15.6 [-7.3, +37.9] |
| worst-20 over ALL 2023-04..2026-02 | 1.142 | ALL 2023-04..2026-02 | 74.9 | 170 | 655 | -3791 | 33.3 / 139 / 684 / -3791 | +41.6 [+23.7, +59.2] |
| maxDD over ALL | 1.194 | L3M | 112.4 | 183 | 186 | 1574 | -1.0 / 141 / 274 / -14 | +113.4 [+62.1, +177.6] |
| maxDD over ALL | 1.194 | L6M | 154.6 | 173 | 186 | 1514 | 50.0 / 145 / 274 / -372 | +104.6 [+62.2, +144.6] |
| maxDD over ALL | 1.194 | HOLD | 133.9 | 200 | 444 | 344 | 37.2 / 173 / 684 / -1321 | +96.7 [+63.6, +136.6] |
| maxDD over ALL | 1.194 | PRE | 84.6 | 184 | 458 | -2704 | 46.1 / 137 / 636 / -2620 | +38.4 [+16.5, +66.8] |
| maxDD over ALL | 1.194 | X' | 23.6 | 128 | 684 | -1704 | 7.0 / 104 / 550 / -1661 | +16.6 [-6.7, +39.9] |
| maxDD over ALL | 1.194 | ALL 2023-04..2026-02 | 78.3 | 178 | 684 | -3962 | 33.3 / 139 / 684 / -3791 | +45.0 [+26.3, +63.6] |
| SD over ALL | 0.932 | L3M | 87.8 | 143 | 145 | 1229 | -1.0 / 141 / 274 / -14 | +88.8 [+47.9, +136.0] |
| SD over ALL | 0.932 | L6M | 120.8 | 135 | 145 | 1182 | 50.0 / 145 / 274 / -372 | +70.8 [+31.6, +103.9] |
| SD over ALL | 0.932 | HOLD | 104.5 | 156 | 347 | 268 | 37.2 / 173 / 684 / -1321 | +67.3 [+36.1, +99.4] |
| SD over ALL | 0.932 | PRE | 66.1 | 144 | 358 | -2112 | 46.1 / 137 / 636 / -2620 | +19.9 [+1.7, +42.2] |
| SD over ALL | 0.932 | X' | 18.4 | 100 | 535 | -1331 | 7.0 / 104 / 550 / -1661 | +11.4 [-9.2, +30.1] |
| SD over ALL | 0.932 | ALL 2023-04..2026-02 | 61.1 | 139 | 535 | -3094 | 33.3 / 139 / 684 / -3791 | +27.9 [+12.5, +41.7] |

Per-window factor on worst-20:

| window | c (D6 scaled to the as-is worst-20 in that window) |
|---|---|
| L3M | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| L6M | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| HOLD | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| PRE | 1.156 |
| X' | 1.163 |
| ALL 2023-04..2026-02 | 1.142 |

#### RESEARCH lots, LIVE-CAL
| factor basis | c | window | D6 x c mean | D6 x c SD | D6 x c maxDD | D6 x c worst-20 | as-is mean / SD / maxDD / worst-20 | mean difference at equal risk [CI] |
|---|---|---|---|---|---|---|---|---|
| worst-20 over ALL 2023-04..2026-02 | 1.108 | L3M | 93.5 | 169 | 181 | 1310 | -1.0 / 141 / 274 / -14 | +94.6 [+48.3, +152.9] |
| worst-20 over ALL 2023-04..2026-02 | 1.108 | L6M | 130.9 | 159 | 181 | 1195 | 50.0 / 145 / 274 / -372 | +80.9 [+37.3, +119.7] |
| worst-20 over ALL 2023-04..2026-02 | 1.108 | HOLD | 112.4 | 184 | 430 | 151 | 37.2 / 173 / 684 / -1321 | +75.2 [+42.0, +113.1] |
| worst-20 over ALL 2023-04..2026-02 | 1.108 | PRE | 67.3 | 167 | 421 | -2644 | 46.1 / 137 / 636 / -2620 | +21.2 [+0.4, +46.4] |
| worst-20 over ALL 2023-04..2026-02 | 1.108 | X' | 15.1 | 118 | 681 | -1720 | 7.0 / 104 / 550 / -1661 | +8.1 [-14.2, +29.6] |
| worst-20 over ALL 2023-04..2026-02 | 1.108 | ALL 2023-04..2026-02 | 62.5 | 162 | 681 | -3791 | 33.3 / 139 / 684 / -3791 | +29.2 [+12.2, +45.7] |
| maxDD over ALL | 1.114 | L3M | 94.1 | 170 | 182 | 1317 | -1.0 / 141 / 274 / -14 | +95.1 [+48.5, +153.8] |
| maxDD over ALL | 1.114 | L6M | 131.6 | 160 | 182 | 1201 | 50.0 / 145 / 274 / -372 | +81.6 [+37.9, +120.7] |
| maxDD over ALL | 1.114 | HOLD | 113.0 | 185 | 432 | 152 | 37.2 / 173 / 684 / -1321 | +75.8 [+42.6, +113.9] |
| maxDD over ALL | 1.114 | PRE | 67.7 | 168 | 423 | -2659 | 46.1 / 137 / 636 / -2620 | +21.6 [+0.8, +46.8] |
| maxDD over ALL | 1.114 | X' | 15.2 | 119 | 684 | -1730 | 7.0 / 104 / 550 / -1661 | +8.2 [-14.1, +29.9] |
| maxDD over ALL | 1.114 | ALL 2023-04..2026-02 | 62.8 | 163 | 684 | -3812 | 33.3 / 139 / 684 / -3791 | +29.6 [+12.5, +46.1] |
| SD over ALL | 0.948 | L3M | 80.0 | 145 | 155 | 1120 | -1.0 / 141 / 274 / -14 | +81.1 [+40.2, +129.1] |
| SD over ALL | 0.948 | L6M | 112.0 | 136 | 155 | 1022 | 50.0 / 145 / 274 / -372 | +62.0 [+21.0, +96.7] |
| SD over ALL | 0.948 | HOLD | 96.2 | 158 | 368 | 129 | 37.2 / 173 / 684 / -1321 | +59.0 [+26.6, +92.2] |
| SD over ALL | 0.948 | PRE | 57.6 | 143 | 360 | -2262 | 46.1 / 137 / 636 / -2620 | +11.5 [-7.4, +33.3] |
| SD over ALL | 0.948 | X' | 12.9 | 101 | 582 | -1472 | 7.0 / 104 / 550 / -1661 | +5.9 [-14.7, +24.7] |
| SD over ALL | 0.948 | ALL 2023-04..2026-02 | 53.5 | 139 | 582 | -3244 | 33.3 / 139 / 684 / -3791 | +20.2 [+5.0, +34.1] |

Per-window factor on worst-20:

| window | c (D6 scaled to the as-is worst-20 in that window) |
|---|---|
| L3M | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| L6M | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| HOLD | undefined (one or both worst-20 sums are positive: there is no tail loss to match) |
| PRE | 1.098 |
| X' | 1.070 |
| ALL 2023-04..2026-02 | 1.108 |

## 5. Notes and limits
* maxDD in the tables is weekly-cumulative as ordered; SS-2/SS used the daily path (column "maxDD (daily path)" in section 2 reproduces SS-2's table to the dollar: as-is L6M 98, D6 102, etc.).
* L3M has 14 weeks: worst-20 is the sum of all of them and its CI is the CI of the 14-week total; read CVaR5 (the single worst week) instead. A single week (2026-01-19 for the as-is stack, the same week for D6) sets L3M/L6M/HOLD maxDD for the as-is stack; CVaR5 in these windows is 1-2 weeks, so those verdicts rest on very few observations.
* The pieces were chosen after seeing L6M/HOLD (tier CANDIDATE-RECENT, SS-2); this report only measures the risk of the already-coded stack and adds no selection. Block bootstrap uses blocks of 4 weeks (windows with n < 4 are not present); with 14-75 weeks the tail statistics are noisy and the CIs of order-statistics are conservative at best.
* Linear lot scaling is exact for dollars in the engine's fractional-lot form; the live engine uses whole contracts (SS-2 section 3b: integer split costs -0.5k..0 mean; ER rounding half-up raises the mean).
* Not done: LIVE lots + ST/WT (live+) series; they exist for Native 1.28 in the SS-2 pickles (`loo_live+_N_runmax.pkl`) but were not scored here. Machine-readable results: `l2vast/ds3/out/sundayrisk/risk_stats.csv` (every config, window, metric), `risk_boot.csv` (all CIs and equal-risk factors), weekly series `series_<lots>.pkl` (daily totals). Code: `l2vast/ds3/code/sundayrisk/` (rk_series.py, rk_an.py, rk_md.py).
