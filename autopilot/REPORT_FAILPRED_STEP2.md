# FAILPRED STEP 2 - REPORT (trackFAILPRED2, 2026-10-23)
Research only: no execution-server/chart/live change, no download, UNTOUCHED never read, Databento key not printed. Prereg l2vast/PREREG_FAILPRED_STEP2.md (sha256 13b54ed40b4dd52de73ce1c9b8135015fc53bbfd599afbf6ba81302c7b749e6b, in DECISIONS.md) frozen before any scored cell. **Every result is NOT PASSED (input)**: Step 1 found no cell passing its frozen rule, so the flagged sets are the best WF-PRE cell at +15, +30, +60. Benchmark: Set A on the corrected P9 replay, reproduced exactly (WF $24,975/wk, SD $104,523, maxDD $401,293). Costs: live model (limit fills only through the level by >=1 tick, stop join 1.01 pt, market exits 0.995 pt = 3.98 ticks at 14 lots, $4.84 RT), 14 lots per candidate, 1-s tape ending 2026-10-16. Cells 40 (F_P +40), DSR trials 6,700.

## Verdict (exact form)

**Chop sessions are predictable at horizon +60 min with precision 59% (against a 37% base rate; 168 chop sessions in WF-PRE, 316 in WF-full; late-horizon AUC is largely the session already having failed; NOT PASSED input). Halting alone is worth +$14.6k/wk on WF-PRE (+$8.1k/wk on WF-full), maxDD -$18.8k. Of 9 families, 0 beat halting: none. Best: C1 (D2 bracket x0.5, +60), +$75/wk over halting, CI [-$10.3k, +$9.3k], placebo rank 0.54, holdout -$2.9k/wk (sign disagrees), ceiling capture n/a (negative, -0.2%).**

(Plain restatement: no candidate cell passes; the closest cells fail at least 4 conditions; widening was not run.)

Holdout order (logged in DECISIONS.md): all non-holdout results and their text were written first (autopilot/REPORT_FAILPRED_STEP2_PREHOLD.md, sha256 in DECISIONS.md); the holdout (2025-07..2026-10, 68 weeks) was scored once afterwards (hold2.py). The non-holdout text below is unchanged except two corrections noted in section "Corrections".

## Table 1 - chop sessions per type and precision (WF-PRE 2024-02..2025-06; WF-full in brackets)

| horizon / flag cell | type | chop sessions | share of sessions flagged | precision F-A (P&L<0) vs base | precision F-B (bottom quartile) vs base | precision F-C (loss>=1R) vs base | recall of F-A | mean pair P&L in chop sessions |
|---|---|---|---|---|---|---|---|---|
| +15 STACK-FB 0.3 | ASIA | 32 [59] of 364 | 8.8% | 46.9% vs 43.1% [39.0% vs 41.8%] | 25.0% vs 25.8% | 34.4% vs 30.8% | 9.6% | -1,101 |
| +15 STACK-FB 0.3 | LONDON | 61 [132] of 364 | 16.8% | 55.7% vs 41.8% [49.2% vs 39.4%] | 36.1% vs 26.9% | 27.9% vs 19.8% | 22.4% | -1,900 |
| +15 STACK-FB 0.3 | NY | 43 [86] of 363 | 11.8% | 25.6% vs 26.2% [36.0% vs 24.7%] | 23.3% vs 22.9% | 14.0% vs 12.7% | 11.6% | +8,355 |
| +15 STACK-FB 0.3 | ALL | 136 [277] of 1091 | 12.5% | 44.1% vs 37.0% [43.0% vs 35.3%] | 29.4% vs 25.2% | 25.0% vs 21.1% | 14.9% | +1,530 |
| +30 LITE-FR 0.4 | ASIA | 131 [178] of 364 | 36.0% | 43.5% vs 43.1% [47.2% vs 41.8%] | 26.0% vs 25.8% | 29.8% vs 30.8% | 36.3% | +3,555 |
| +30 LITE-FR 0.4 | LONDON | 116 [167] of 364 | 31.9% | 47.4% vs 41.8% [44.3% vs 39.4%] | 31.9% vs 26.9% | 22.4% vs 19.8% | 36.2% | -779 |
| +30 LITE-FR 0.4 | NY | 7 [27] of 363 | 1.9% | 28.6% vs 26.2% [44.4% vs 24.7%] | 28.6% vs 22.9% | 14.3% vs 12.7% | 2.1% | -4,517 |
| +30 LITE-FR 0.4 | ALL | 254 [372] of 1091 | 23.3% | 44.9% vs 37.0% [45.7% vs 35.3%] | 28.7% vs 25.2% | 26.0% vs 21.1% | 28.2% | +1,353 |
| +60 CHOSEN 0.3 (primary) | ASIA | 9 [22] of 364 | 2.5% | 33.3% vs 43.1% [54.5% vs 41.8%] | 33.3% vs 25.8% | 33.3% vs 30.8% | 1.9% | +1,499 |
| +60 CHOSEN 0.3 (primary) | LONDON | 46 [74] of 364 | 12.6% | 54.3% vs 41.8% [47.3% vs 39.4%] | 43.5% vs 26.9% | 32.6% vs 19.8% | 16.4% | -5,485 |
| +60 CHOSEN 0.3 (primary) | NY | 113 [220] of 363 | 31.1% | 62.8% vs 26.2% [62.7% vs 24.7%] | 54.9% vs 22.9% | 35.4% vs 12.7% | 74.7% | -4,287 |
| +60 CHOSEN 0.3 (primary) | ALL | 168 [316] of 1091 | 15.4% | 58.9% vs 37.0% [58.5% vs 35.3%] | 50.6% vs 25.2% | 34.5% vs 21.1% | 24.5% | -4,305 |
| +5 STACK-FB 0.3 (informational) | ASIA | 21 [44] of 364 | 5.8% | 47.6% vs 43.1% [43.2% vs 41.8%] | 33.3% vs 25.8% | 42.9% vs 30.8% | 6.4% | -7,990 |
| +5 STACK-FB 0.3 (informational) | LONDON | 48 [129] of 364 | 13.2% | 47.9% vs 41.8% [49.6% vs 39.4%] | 37.5% vs 26.9% | 33.3% vs 19.8% | 15.1% | -11,055 |
| +5 STACK-FB 0.3 (informational) | NY | 51 [113] of 363 | 14.0% | 27.5% vs 26.2% [38.9% vs 24.7%] | 23.5% vs 22.9% | 15.7% vs 12.7% | 14.7% | +517 |
| +5 STACK-FB 0.3 (informational) | ALL | 120 [286] of 1091 | 11.0% | 39.2% vs 37.0% [44.4% vs 35.3%] | 30.8% vs 25.2% | 27.5% vs 21.1% | 11.6% | -5,600 |

Read against the base rate: the flag lifts the failing share from 37% to 59% at +60 (pooled F-A), but most of that is already-booked P&L (late-horizon AUC is largely the session having already failed; the residual-failure AUC, the part a halt can act on, is 0.65-0.66 at +15/+30/+60). Flags are as-of h, walk-forward, monthly refit (Step 1 predictions, unchanged).


## Table 2 - every cell vs C0 (WF-PRE 2024-02..2025-06 score window; holdout 2025-07+ and WF-full added). $/wk, 14-lot report scale, live cost model

| flag cell | cell | delta vs C0 WF-PRE | CI 95% | plc A rank | plc B $/session (chop $/session) | ceiling capture | 2x-cost delta | trades (WF-full) | R8 largest-year share | DSR | holdout delta | WF-full delta | result |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H60 | C0 (vs Set A) | +14,629 | [+1,847, +28,603] | 0.99 | -1,094 (+6,531) - | 17% | +8,910 | - | 0.64 | 0.00 | +675 | +8,050 | baseline |
| H60 | C1 | +75 | [-10,330, +9,298] | 0.54 | -1,008 (+33) not general | n/a | -10,091 FRAGILE | 4244 | 36.35 | 0.00 | -2,938 | -1,367 | fails CI, placebo A, FRAGILE, R8, holdout |
| H60 | C2 | -560 | [-15,997, +14,276] | 0.63 | -2,154 (-250) not general | n/a | -6,350 | 4244 | 0.76 | 0.00 | -3,744 | -2,088 | fails mean<=C0, CI, placebo A, holdout |
| H60 | C3 | -16,123 | [-37,845, +4,433] | 0.09 | -2,447 (-7,198) not general | n/a | -23,010 | 4243 | 0.76 | 0.00 | -620 | -8,813 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C9 | -14,629 | [-28,603, -1,847] | 0.01 | +1,094 (-6,531) - | n/a | -8,910 | - | 0.64 | 0.00 | -675 | -8,050 | identity |
| H60 | C4_k1.0 | -21,221 | [-30,232, -12,876] | 0.52 | -9,804 (-9,474) not general | n/a | -39,949 | 7435 | 0.62 | 0.00 | -26,306 | -23,806 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C4_k1.5 | -10,272 | [-18,991, -2,504] | 0.94 | -7,802 (-4,586) not general | n/a | -21,688 | 4045 | 0.67 | 0.00 | -12,418 | -11,372 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C4_k2.0 | -3,673 | [-10,187, +2,410] | 0.52 | -1,993 (-1,640) not general | n/a | -6,790 | 1331 | 0.77 | 0.00 | -958 | -2,399 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C5_m5 | -803 | [-2,421, +871] | 0.46 | +65 (-359) GENERAL | n/a | -1,537 | 266 | 0.54 | 0.00 | -114 | -479 | fails mean<=C0, CI, placebo A, GENERAL, holdout |
| H60 | C5_m10 | -236 | [-2,002, +1,778] | 0.50 | +107 (-105) GENERAL | n/a | -982 | 287 | 1.80 | 0.00 | -210 | -225 | fails mean<=C0, CI, placebo A, GENERAL, holdout |
| H60 | C5_m15 | -435 | [-2,363, +1,612] | 0.37 | +135 (-194) GENERAL | n/a | -1,073 | 296 | 0.91 | 0.00 | -197 | -324 | fails mean<=C0, CI, placebo A, GENERAL, holdout |
| H60 | C6_N10 | -21,709 | [-26,882, -17,235] | 0.53 | -10,413 (-9,691) not general | n/a | -41,920 | 8025 | 0.62 | 0.00 | -20,597 | -21,329 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C6_N15 | -20,339 | [-26,116, -14,914] | 0.19 | -8,034 (-9,080) not general | n/a | -37,661 | 7492 | 0.71 | 0.00 | -21,050 | -20,823 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C6_N20 | -18,905 | [-25,856, -12,422] | 0.32 | -7,048 (-8,440) not general | n/a | -35,504 | 7015 | 0.74 | 0.00 | -23,102 | -21,048 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C7 | -985 | [-2,650, +532] | 0.34 | -320 (-440) not general | n/a | -1,445 | 328 | 0.50 | 0.00 | -1,273 | -1,129 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C8_C4_k1.0_t20 | -22,461 | [-29,868, -15,198] | 0.50 | -10,284 (-10,027) not general | n/a | -42,395 | 7802 | 0.66 | 0.00 | -27,018 | -24,801 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C8_C4_k1.0_t40 | -22,373 | [-31,166, -14,242] | 0.50 | -10,109 (-9,988) not general | n/a | -41,689 | 7547 | 0.63 | 0.00 | -27,330 | -24,904 | fails mean<=C0, CI, placebo A, holdout |
| H60 | C8_C4_k1.5_t20 | -11,966 | [-19,380, -4,667] | 0.95 | -8,390 (-5,342) not general | n/a | -24,793 | 4398 | 0.67 | 0.00 | -7,114 | -9,726 | fails mean<=C0, CI, holdout, R11 maxDD |
| H60 | C8_C4_k1.5_t40 | -11,251 | [-19,384, -3,546] | 0.95 | -8,442 (-5,023) not general | n/a | -23,269 | 4172 | 0.72 | 0.00 | -8,374 | -9,952 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C8_C4_k2.0_t20 | -3,468 | [-8,798, +1,334] | 0.68 | -2,690 (-1,548) not general | n/a | -7,202 | 1419 | 0.76 | 0.00 | -2,395 | -2,979 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C8_C4_k2.0_t40 | -2,821 | [-9,250, +2,466] | 0.81 | -3,109 (-1,259) not general | n/a | -6,288 | 1353 | 0.98 | 0.00 | -1,095 | -2,014 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C8_C6_N10_t20 | -21,814 | [-27,038, -17,286] | 0.52 | -10,610 (-9,738) not general | n/a | -42,083 | 8038 | 0.62 | 0.00 | -20,547 | -21,361 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C8_C6_N10_t40 | -21,733 | [-26,906, -17,233] | 0.55 | -10,443 (-9,702) not general | n/a | -41,961 | 8025 | 0.62 | 0.00 | -20,619 | -21,353 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C8_C6_N15_t20 | -20,629 | [-26,306, -15,154] | 0.21 | -8,264 (-9,209) not general | n/a | -38,181 | 7545 | 0.70 | 0.00 | -21,010 | -20,957 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C8_C6_N15_t40 | -20,394 | [-26,143, -15,028] | 0.21 | -8,046 (-9,104) not general | n/a | -37,759 | 7500 | 0.71 | 0.00 | -20,993 | -20,824 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C8_C6_N20_t20 | -18,945 | [-25,527, -12,711] | 0.43 | -7,407 (-8,458) not general | n/a | -35,886 | 7125 | 0.74 | 0.00 | -23,888 | -21,446 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H60 | C8_C6_N20_t40 | -18,897 | [-25,909, -12,290] | 0.34 | -7,167 (-8,436) not general | n/a | -35,707 | 7034 | 0.73 | 0.00 | -23,274 | -21,126 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H15 | C0 (vs Set A) | +2,596 | [-10,286, +14,935] | 0.71 | -790 (+1,432) - | 3% | +417 | - | 0.65 | 0.00 | -9,996 | -3,416 | baseline |
| H15 | C1 | -8,180 | [-22,509, +7,284] | 0.10 | -1,122 (-4,511) not general | n/a | -13,407 | 5262 | 1.62 | 0.00 | +10,947 | +922 | fails mean<=C0, CI, placebo A, R11 maxDD |
| H15 | C2 | -13,506 | [-32,863, +6,788] | 0.10 | -1,412 (-7,448) not general | n/a | -17,477 | 5262 | 1.47 | 0.00 | +4,313 | -5,068 | fails mean<=C0, CI, placebo A, R11 maxDD |
| H15 | C3 | -8,319 | [-24,871, +9,244] | 0.41 | -3,850 (-4,587) not general | n/a | -7,982 | 5262 | 1.47 | 0.00 | -10,453 | -9,399 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H15 | C9 | -2,596 | [-14,935, +10,286] | 0.29 | +790 (-1,432) - | n/a | -417 | - | 0.65 | 0.00 | +9,996 | +3,416 | identity |
| H30 | C0 (vs Set A) | +12,399 | [-4,400, +29,560] | 0.97 | -1,264 (+3,661) - | 13% | +3,901 | - | 0.97 | 0.00 | +1,315 | +7,178 | baseline |
| H30 | C1 | -14,841 | [-34,271, +5,522] | 0.09 | -396 (-4,382) not general | n/a | -18,688 | 6927 | 0.74 | 0.00 | -1,577 | -8,594 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H30 | C2 | -31,787 | [-55,406, -9,378] | 0.04 | -1,514 (-9,386) not general | n/a | -34,933 | 6927 | 0.87 | 0.00 | -11,140 | -22,124 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H30 | C3 | -27,660 | [-57,524, +1,588] | 0.16 | -3,405 (-8,167) not general | n/a | -27,144 | 6927 | 0.77 | 0.00 | -22,653 | -25,457 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |
| H30 | C9 | -12,399 | [-29,560, +4,400] | 0.03 | +1,264 (-3,661) - | n/a | -3,901 | - | 0.97 | 0.00 | -1,315 | -7,178 | identity |
| H5 | C0 (vs Set A) | +12,230 | [+941, +25,656] | 0.98 | -1,881 (+7,644) - | 14% | +2,726 | - | 0.83 | 0.00 | +933 | +6,906 | baseline |
| H5 | C1 | +1,731 | [-10,805, +13,978] | 0.62 | +664 (+1,082) GENERAL | n/a | -3,548 FRAGILE | 5390 | 4.23 | 0.00 | +952 | +1,370 | fails CI, placebo A, GENERAL, FRAGILE, R8, R11 maxDD |
| H5 | C3 | -9,623 | [-25,656, +5,522] | 0.28 | -2,490 (-6,014) not general | n/a | -8,052 | 5389 | 0.53 | 0.00 | -14,288 | -11,924 | fails mean<=C0, CI, placebo A, holdout, R11 maxDD |

C0 row = the halt switch vs Set A (not vs C0); C9 = minus that. Candidate cells C4-C8: delta = candidate standalone net P&L (isolated score); C1-C3: full-engine regenerated minus C0. R10: every candidate cell has >=150 WF-full trades (lowest C5 m=5 at 266), so R10 fails nothing. The result column lists every failed condition; the closest cell fails 4.

### Gross-edge diagnostic (C4-C8, +60 chop sessions, WF-PRE)

| cell | trades | per chop session | stop / target / market share | gross pts per trade (before join, market cost, fees) | net pts per trade |
|---|---|---|---|---|---|
| C4_k1.0 | 3977 | 23.7 | 90% / 8% / 2% | -0.26 | -1.19 |
| C4_k1.5 | 2300 | 13.7 | 85% / 10% / 5% | -0.05 | -0.95 |
| C4_k2.0 | 759 | 4.5 | 75% / 16% / 10% | -0.20 | -1.05 |
| C5_m5 | 146 | 0.9 | 74% / 25% / 1% | -0.47 | -1.23 |
| C5_m10 | 151 | 0.9 | 73% / 26% / 1% | +0.57 | -0.18 |
| C5_m15 | 156 | 0.9 | 73% / 26% / 1% | +0.25 | -0.51 |
| C6_N10 | 4557 | 27.1 | 79% / 21% / 0% | -0.24 | -1.03 |
| C6_N15 | 4061 | 24.2 | 81% / 18% / 1% | -0.27 | -1.10 |
| C6_N20 | 3719 | 22.1 | 83% / 16% / 1% | -0.27 | -1.12 |
| C7 | 184 | 1.1 | 52% / 47% / 1% | -0.65 | -1.19 |
| C8_C4_k1.0_t20 | 4165 | 24.8 | 84% / 6% / 10% | -0.26 | -1.20 |
| C8_C4_k1.0_t40 | 4038 | 24.0 | 87% / 7% / 5% | -0.31 | -1.24 |
| C8_C4_k1.5_t20 | 2475 | 14.7 | 74% / 5% / 22% | -0.09 | -1.05 |
| C8_C4_k1.5_t40 | 2361 | 14.1 | 80% / 8% / 12% | -0.10 | -1.03 |
| C8_C4_k2.0_t20 | 815 | 4.9 | 56% / 6% / 38% | +0.04 | -0.90 |
| C8_C4_k2.0_t40 | 773 | 4.6 | 66% / 10% / 25% | +0.17 | -0.74 |
| C8_C6_N10_t20 | 4563 | 27.2 | 78% / 21% / 1% | -0.24 | -1.04 |
| C8_C6_N10_t40 | 4557 | 27.1 | 78% / 21% / 0% | -0.24 | -1.04 |
| C8_C6_N15_t20 | 4092 | 24.4 | 80% / 18% / 2% | -0.28 | -1.11 |
| C8_C6_N15_t40 | 4065 | 24.2 | 81% / 18% / 1% | -0.28 | -1.10 |
| C8_C6_N20_t20 | 3794 | 22.6 | 81% / 14% / 5% | -0.23 | -1.10 |
| C8_C6_N20_t40 | 3733 | 22.2 | 82% / 16% / 2% | -0.26 | -1.11 |

### R8 - gain by year (WF-PRE 2024 vs 2025H1, plus 2026 in WF-full) and by session type, $ over the window (selected rows; all rows in l2vast/failpred2/out/res_final.csv)

| set | cell | 2024 | 2025H1 | ASIA $/wk | LONDON $/wk | NY $/wk |
|---|---|---|---|---|---|---|
| H60 | C0 | +389,978 | +707,226 | -1,386 | +12,470 | +2,549 |
| H60 | C1 | +204,010 | -198,397 | -311 | -1,787 | +1,969 |
| H60 | C3 | -917,375 | -291,876 | -1,548 | -3,338 | -12,241 |
| H60 | C4_k2.0 | -213,190 | -62,259 | +460 | -3,581 | -552 |
| H60 | C5_m10 | +14,237 | -31,949 | +141 | +26 | -403 |
| H60 | C7 | -36,779 | -37,065 | -22 | -97 | -865 |
| H30 | C0 | +906,476 | +23,440 | +210 | +5,717 | +309 |
| H5 | C0 | +762,824 | +154,442 | -555 | +7,504 | +3,562 |

Halting alone: LONDON and NY carry the +60 gain; 2025H1 carries 64% of it (WF-full by year: see res_final.csv columns y2024/y2025/y2026). The halt itself fails R8.

## Table 3 - R11 full-system sequence test (pair + candidate on the full tape with live locks / give-back / week floor; candidate is its own book with the same per-book limits; 50-contract and opposite-side filters), $ per week and $

| system | WF-PRE mean / SD / maxDD / worst week | HOLDOUT mean / SD / maxDD / worst week | WF-full mean / SD / maxDD / worst week | L8W mean / maxDD |
|---|---|---|---|---|
| Set A (benchmark) | 17,549 / 97,533 / 401,293 / -136,494 | 32,799 / 110,543 / 267,133 / -137,081 | 24,975 / 104,523 / 401,293 / -137,081 | 34,191 / 267,133 |
| **C0 = Set A + halt switch, +60 CHOSEN 0.3 (primary)** | 32,178 / 92,475 / 382,482 / -140,761 | 33,474 / 99,315 / 267,403 / -137,022 | 33,026 / 96,222 / 382,482 / -140,761 | 38,893 / 267,403 |
| **C0 = Set A + halt switch, +15 STACK-FB 0.3** | 20,145 / 96,883 / 454,627 / -137,257 | 22,803 / 105,326 / 304,691 / -137,081 | 21,560 / 101,322 / 454,627 / -137,257 | 50,776 / 250,456 |
| **C0 = Set A + halt switch, +30 LITE-FR 0.4** | 29,948 / 100,164 / 361,825 / -135,574 | 34,114 / 113,638 / 446,992 / -136,892 | 32,154 / 106,350 / 452,519 / -136,892 | 43,240 / 366,527 |
| **C0 = Set A + halt switch, +5 STACK-FB 0.3 (informational)** | 29,779 / 88,466 / 362,811 / -136,494 | 33,732 / 98,410 / 256,860 / -138,295 | 31,882 / 93,520 / 362,811 / -138,295 | 43,198 / 219,799 |
| no cell passed; family bests shown for information (on top of C0, +60) | | | | |
| C1 + C0 | 32,253 / 100,019 / 354,988 / -138,171 | 30,536 / 107,144 / 354,673 / -136,204 | 31,658 / 103,777 / 354,988 / -138,171 | 22,279 / 299,787 |
| C5_m10 + C0 | 32,245 / 91,602 / 343,661 / -135,550 | 35,202 / 100,904 / 254,027 / -139,015 | 33,888 / 96,661 / 343,661 / -139,015 | 37,949 / 254,027 |
| C4_k2.0 + C0 | 28,165 / 94,444 / 538,359 / -135,550 | 33,869 / 105,710 / 320,070 / -140,313 | 31,095 / 100,546 / 538,359 / -140,313 | 45,284 / 223,983 |
| C7 + C0 | 30,829 / 91,944 / 390,869 / -135,550 | 33,919 / 99,010 / 259,557 / -137,441 | 32,526 / 95,753 / 390,869 / -137,441 | 38,632 / 259,557 |
| C8_C4_k1.0_t40 + C0 | 14,771 / 92,832 / 381,366 / -149,370 | 19,587 / 106,615 / 530,381 / -150,208 | 17,181 / 100,197 / 530,381 / -150,208 | 38,078 / 316,353 |

### R9 look-ahead audit

| rule | decisions tested | mismatches |
|---|---|---|
| C4 k=1.0 | 300 | 0 |
| C5 m=10 | 300 | 0 |
| C6 N=15 | 300 | 0 |
| C7 | 300 | 0 |
| C8 C4 k=1.5 t20 | 300 | 0 |
| C8 C6 N=15 t40 | 300 | 0 |
| PLANTED look-ahead (positive control) | 300 | 23 |
| D2 own_signals | 4 | 0 |

Truncation-invariance (bars and 1-s data after a random cut replaced by NaN or noise; every order placed and every trade closed before the cut must be identical). Planted look-ahead caught; no hit on the real rules; no fix or re-run needed.

## What this says

1. The only thing in this family that works is the halt itself (flatten + halt in sessions flagged at +60): +$14.6k/wk WF-PRE, system maxDD $382k vs $401k, but it is a 2025H1-heavy gain, its WF-full value is +$8.1k/wk, the holdout is only +$0.7k/wk (68 weeks), and at +15 it is +$2.6k WF-PRE and -$10.0k in the holdout.
2. Replacing the halt with another action loses money in every cell: after a flag the market is not exploitable by the nine tested ideas under the live cost model. D2 with tighter brackets (C1/C2) trades 4,244 extra times for +$75/-$560 per week; fading the flip (C3) loses $16.1k/wk; the VWAP/limit-scalp families (C4, C6, C8) have no gross edge (75-90% stop-outs, -0.05 to -0.3 pt gross per trade) and lose $3.5k-$22.5k/wk after $283 join + $68 fee per stopped 14-lot trade; the opening-range fade (C5) is the only gross-positive idea (+0.57 pt at m=10, 151 trades) and nets -$0.2k/wk; prior-day-level fades (C7) -$1.0k/wk.
3. Because nothing passed, no widening grid was run. No new family is a candidate; the best use of the flag remains the halt/flatten (not recommended on this evidence either: fails the Step-1 holdout rule).
4. Limits: chop sets are small (168/136/254 WF-PRE sessions, 120 for the +5 set); scored on 1-s highs/lows (the 1-tick through-trade rule is a conservative proxy for queue position); netting and the 50-contract limit are approximated in R11; C6 holds long and short virtual positions together as specified; the C4/C6 stop (1.5 x distance from VWAP) is a reading of the directive stated in the prereg.

## Corrections to the pre-holdout text
- "75-90% of trades stopped out" should read 52-90% (C7 52%, C8 C4 k=2.0 t20 56%). - The R10 sentence in the pre-holdout text does not apply: every candidate cell has >=150 WF-full trades (C5 266-296 is the lowest); R10 fails nothing.

## Files
l2vast/PREREG_FAILPRED_STEP2.md; l2vast/failpred2/{fp2lib,candsim,d2mod,score2,assemble2,audit,hold2,rep_final}.py; out/{res_pre.csv,res_final.csv,table1.csv,diag_gross.csv,audit_r9.pkl,cand_trades.pkl}; autopilot/FAILPRED2_PROGRESS.md; autopilot/REPORT_FAILPRED_STEP2_PREHOLD.md.
