# FAILPRED STEP 2 - non-holdout results (written BEFORE the holdout was scored)
Research only. Prereg l2vast/PREREG_FAILPRED_STEP2.md (sha256 in DECISIONS.md) frozen before any scored cell. Every result is labelled **NOT PASSED (input)**: Step 1 found no cell passing the frozen rule, so the chop sets are the best WF-PRE cell at +15, +30, +60 (rule in the prereg). Score window WF-PRE 2024-02-01..2025-06-30 (73 weeks); holdout 2025-07 onward scored once in the next step. Tape ends 2026-10-16 (no extension landed, no download). Benchmark reproduced: Set A WF 2024-02..2026-10 $24,975/wk, SD $104,523, maxDD $401,293; WF-PRE $17,549/wk.
Cell count 40 (27 at +60: C0-C9 with parameters; 5 each at +15 and +30; 3 informational at +5); DSR trials 6,700 (6,660 + 40). F_P +40.

## Non-holdout summary (read before the tables)
* Chop sessions are partly predictable as-of h but the precision is mostly already-booked loss: at +60 the flag (CHOSEN, theta 0.3) picks 168 WF-PRE sessions (9 ASIA, 46 LONDON, 113 NY; 316 in WF-full) with 59% failing (P&L<0) against a 37% base; +15 picks 136 sessions with 44% vs 37%; +30 picks 254 with 45% vs 37%.
* Halting alone (C0, flatten + halt) at +60: +$14.6k/wk over Set A on WF-PRE (CI [+1.8k, +28.6k], placebo rank 0.99, capture 17% of the F-C perfect-foresight ceiling), system maxDD $382k vs $401k (-$18.8k), weekly mean $32.2k vs $17.5k. At +15 it is +$2.6k (CI spans 0), +30 +$12.4k (CI spans 0). The +60 halt gain sits mostly in 2025H1 (64% of the gain; R8 would fail for the switch itself).
* None of the nine families beat halting on the non-holdout conditions. Only one cell has a positive mean over C0 (C1 at +60: +$75/wk, CI [-10.3k, +9.3k], placebo rank 0.54, flips to -$10.1k at 2x cost = FRAGILE, a one-year result = R8 fail). Every other cell is at or below C0: C2 -$0.6k, C3 (fade the flip) -$16.1k, C4/C8-C4 -$3.5k to -$22.5k (C4 k=2.0 +/- noise, CI [-10.2k, +2.4k]), C5 -$0.2k to -$0.8k, C6/C8-C6 -$18.9k to -$21.8k, C7 -$1.0k, C9 -$14.6k (= what the switch removes).
* The new strategies lose because there is no gross edge to pay the live friction: gross (before the 1.01 pt stop join, 0.995 pt market cost, $4.84 fee) points per trade are about zero or negative for C4/C6/C7/C8 (-0.05 to -0.65), with 75-90% of trades stopped out; only C5 m=10 is gross-positive (+0.57 pt on 151 WF-PRE trades) and still nets -0.18 pt. One stopped 14-lot trade costs about $283 in join plus $68 in fees. The mean-reversion cells also deepen the full-system maxDD (R11).
* Placebos: no candidate reaches placebo A rank >= 0.95 with a positive mean; the highest ranks (0.94-0.95, C4 k=1.5 and its time-stop variants) are for strategies that still lose about $10-12k/wk (they lose less in chop sessions than in random ones only because they trade fewer bars there). Placebo B: C5 (all m) earns a little in non-chop sessions (GENERAL), C1 at +5 informational is GENERAL.
* R9: truncation test 0 mismatches for C4/C5/C6/C7/C8 (300 decisions each) and for the unchanged D2 signal code; the planted look-ahead control is caught (23/300). No fix needed.
* R11: no candidate lowers the full-system maxDD below the C0 system (382k at +60) except by tiny margins: C1 355k and C2 363k (D2 variants), C5 m5 371k, m10/m15 344k, C8 C4 k1.0 t40 381k; all fail on mean.
* Widening: not run (nothing passed).
* The informational +5 set (STACK-FB 0.3, the lone Step-1 'passer'): C0 +$12.2k/wk (CI [+0.9k, +25.7k]); C1 +$1.7k vs C0 (CI spans 0, FRAGILE, GENERAL), C3 -$9.6k.

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

## Table 2 - every cell vs C0 (score window WF-PRE 2024-02..2025-06 = 17 months, 73 weeks; $/wk at 14-lot report scale, fees $4.84 RT, live cost model)

Columns: delta vs C0 $/wk, weekly block-bootstrap 95% CI, placebo A rank (500 draws, 1.00 = best), placebo B (non-chop sessions: per-session delta, GENERAL?), ceiling capture (R5), delta at 2x cost and FRAGILE flag, trades (WF-full), R8 largest-year share, R7 DSR (6,700 trials), non-holdout verdict. Holdout column added after the holdout step.

| flag cell | cell | delta vs C0 $/wk | CI 95% | plc A rank | plc B $/session (chop $/session) | ceiling capture | 2x cost delta | trades | R8 yr share | DSR | non-holdout verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H60 | C0 (vs Set A) | +14,629 | [+1,847, +28,603] | 0.99 | -1,094 (+6,531) - | 17% | +8,910 | - | 0.64 | 0.00 | baseline |
| H60 | C1 | +75 | [-10,330, +9,298] | 0.54 | -1,008 (+33) not general | n/a | -10,091 FRAGILE | 4244 | 36.35 | 0.00 | fail pre-holdout: CI includes 0; placebo A rank 0.54; FRAGILE; R8 |
| H60 | C2 | -560 | [-15,997, +14,276] | 0.63 | -2,154 (-250) not general | n/a | -6,350 | 4244 | 0.76 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.63 |
| H60 | C3 | -16,123 | [-37,845, +4,433] | 0.09 | -2,447 (-7,198) not general | n/a | -23,010 | 4243 | 0.76 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.09; R11 maxDD worse than C0 system |
| H60 | C9 | -14,629 | [-28,603, -1,847] | 0.01 | +1,094 (-6,531) - | n/a | -8,910 | - | 0.64 | 0.00 | identity (= benchmark) |
| H60 | C4_k1.0 | -21,221 | [-30,232, -12,876] | 0.52 | -9,804 (-9,474) not general | n/a | -39,949 | 7435 | 0.62 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.52; R11 maxDD worse than C0 system |
| H60 | C4_k1.5 | -10,272 | [-18,991, -2,504] | 0.94 | -7,802 (-4,586) not general | n/a | -21,688 | 4045 | 0.67 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.94; R11 maxDD worse than C0 system |
| H60 | C4_k2.0 | -3,673 | [-10,187, +2,410] | 0.52 | -1,993 (-1,640) not general | n/a | -6,790 | 1331 | 0.77 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.52; R11 maxDD worse than C0 system |
| H60 | C5_m5 | -803 | [-2,421, +871] | 0.46 | +65 (-359) GENERAL | n/a | -1,537 | 266 | 0.54 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.46; GENERAL |
| H60 | C5_m10 | -236 | [-2,002, +1,778] | 0.50 | +107 (-105) GENERAL | n/a | -982 | 287 | 1.80 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.50; GENERAL |
| H60 | C5_m15 | -435 | [-2,363, +1,612] | 0.37 | +135 (-194) GENERAL | n/a | -1,073 | 296 | 0.91 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.37; GENERAL |
| H60 | C6_N10 | -21,709 | [-26,882, -17,235] | 0.53 | -10,413 (-9,691) not general | n/a | -41,920 | 8025 | 0.62 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.53; R11 maxDD worse than C0 system |
| H60 | C6_N15 | -20,339 | [-26,116, -14,914] | 0.19 | -8,034 (-9,080) not general | n/a | -37,661 | 7492 | 0.71 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.19; R11 maxDD worse than C0 system |
| H60 | C6_N20 | -18,905 | [-25,856, -12,422] | 0.32 | -7,048 (-8,440) not general | n/a | -35,504 | 7015 | 0.74 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.32; R11 maxDD worse than C0 system |
| H60 | C7 | -985 | [-2,650, +532] | 0.34 | -320 (-440) not general | n/a | -1,445 | 328 | 0.50 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.34; R11 maxDD worse than C0 system |
| H60 | C8_C4_k1.0_t20 | -22,461 | [-29,868, -15,198] | 0.50 | -10,284 (-10,027) not general | n/a | -42,395 | 7802 | 0.66 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.50; R11 maxDD worse than C0 system |
| H60 | C8_C4_k1.0_t40 | -22,373 | [-31,166, -14,242] | 0.50 | -10,109 (-9,988) not general | n/a | -41,689 | 7547 | 0.63 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.50 |
| H60 | C8_C4_k1.5_t20 | -11,966 | [-19,380, -4,667] | 0.95 | -8,390 (-5,342) not general | n/a | -24,793 | 4398 | 0.67 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; R11 maxDD worse than C0 system |
| H60 | C8_C4_k1.5_t40 | -11,251 | [-19,384, -3,546] | 0.95 | -8,442 (-5,023) not general | n/a | -23,269 | 4172 | 0.72 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.95; R11 maxDD worse than C0 system |
| H60 | C8_C4_k2.0_t20 | -3,468 | [-8,798, +1,334] | 0.68 | -2,690 (-1,548) not general | n/a | -7,202 | 1419 | 0.76 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.68; R11 maxDD worse than C0 system |
| H60 | C8_C4_k2.0_t40 | -2,821 | [-9,250, +2,466] | 0.81 | -3,109 (-1,259) not general | n/a | -6,288 | 1353 | 0.98 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.81; R11 maxDD worse than C0 system |
| H60 | C8_C6_N10_t20 | -21,814 | [-27,038, -17,286] | 0.52 | -10,610 (-9,738) not general | n/a | -42,083 | 8038 | 0.62 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.52; R11 maxDD worse than C0 system |
| H60 | C8_C6_N10_t40 | -21,733 | [-26,906, -17,233] | 0.55 | -10,443 (-9,702) not general | n/a | -41,961 | 8025 | 0.62 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.55; R11 maxDD worse than C0 system |
| H60 | C8_C6_N15_t20 | -20,629 | [-26,306, -15,154] | 0.21 | -8,264 (-9,209) not general | n/a | -38,181 | 7545 | 0.70 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.21; R11 maxDD worse than C0 system |
| H60 | C8_C6_N15_t40 | -20,394 | [-26,143, -15,028] | 0.21 | -8,046 (-9,104) not general | n/a | -37,759 | 7500 | 0.71 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.21; R11 maxDD worse than C0 system |
| H60 | C8_C6_N20_t20 | -18,945 | [-25,527, -12,711] | 0.43 | -7,407 (-8,458) not general | n/a | -35,886 | 7125 | 0.74 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.43; R11 maxDD worse than C0 system |
| H60 | C8_C6_N20_t40 | -18,897 | [-25,909, -12,290] | 0.34 | -7,167 (-8,436) not general | n/a | -35,707 | 7034 | 0.73 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.34; R11 maxDD worse than C0 system |
| H15 | C0 (vs Set A) | +2,596 | [-10,286, +14,935] | 0.71 | -790 (+1,432) - | 3% | +417 | - | 0.65 | 0.00 | baseline |
| H15 | C1 | -8,180 | [-22,509, +7,284] | 0.10 | -1,122 (-4,511) not general | n/a | -13,407 | 5262 | 1.62 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.10; R11 maxDD worse than C0 system |
| H15 | C2 | -13,506 | [-32,863, +6,788] | 0.10 | -1,412 (-7,448) not general | n/a | -17,477 | 5262 | 1.47 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.10; R11 maxDD worse than C0 system |
| H15 | C3 | -8,319 | [-24,871, +9,244] | 0.41 | -3,850 (-4,587) not general | n/a | -7,982 | 5262 | 1.47 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.41; R11 maxDD worse than C0 system |
| H15 | C9 | -2,596 | [-14,935, +10,286] | 0.29 | +790 (-1,432) - | n/a | -417 | - | 0.65 | 0.00 | identity (= benchmark) |
| H30 | C0 (vs Set A) | +12,399 | [-4,400, +29,560] | 0.97 | -1,264 (+3,661) - | 13% | +3,901 | - | 0.97 | 0.00 | baseline |
| H30 | C1 | -14,841 | [-34,271, +5,522] | 0.09 | -396 (-4,382) not general | n/a | -18,688 | 6927 | 0.74 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.09; R11 maxDD worse than C0 system |
| H30 | C2 | -31,787 | [-55,406, -9,378] | 0.04 | -1,514 (-9,386) not general | n/a | -34,933 | 6927 | 0.87 | 0.00 | fail pre-holdout: mean<=C0; CI below 0; placebo A rank 0.04; R11 maxDD worse than C0 system |
| H30 | C3 | -27,660 | [-57,524, +1,588] | 0.16 | -3,405 (-8,167) not general | n/a | -27,144 | 6927 | 0.77 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.16; R11 maxDD worse than C0 system |
| H30 | C9 | -12,399 | [-29,560, +4,400] | 0.03 | +1,264 (-3,661) - | n/a | -3,901 | - | 0.97 | 0.00 | identity (= benchmark) |
| H5 | C0 (vs Set A) | +12,230 | [+941, +25,656] | 0.98 | -1,881 (+7,644) - | 14% | +2,726 | - | 0.83 | 0.00 | baseline |
| H5 | C1 | +1,731 | [-10,805, +13,978] | 0.62 | +664 (+1,082) GENERAL | n/a | -3,548 FRAGILE | 5390 | 4.23 | 0.00 | fail pre-holdout: CI includes 0; placebo A rank 0.62; GENERAL; FRAGILE; R8; R11 maxDD worse than C0 system |
| H5 | C3 | -9,623 | [-25,656, +5,522] | 0.28 | -2,490 (-6,014) not general | n/a | -8,052 | 5389 | 0.53 | 0.00 | fail pre-holdout: mean<=C0; CI includes 0; placebo A rank 0.28; R11 maxDD worse than C0 system |

Notes: C0 row = halting vs Set A (not vs C0). C9 = pair as-is; its delta is minus the halt gain. For C4-C8 the delta vs C0 is the candidate standalone net P&L (isolated score, 14 lots); for C1-C3 it is the regenerated full-engine series minus C0. Ceiling capture shown only when both real and ceiling deltas are positive. Placebo B: per-session mean delta in sessions the predictor does not flag.

### Gross-edge diagnostic (candidate cells C4-C8, +60 chop sessions, WF-PRE; before join/market costs and fees)

| cell | trades | per chop session | stop / target / market exit share | gross pts per trade | net pts per trade (after 1.01 join, 0.995 market, fees 0.24 pt) |
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

## R9 look-ahead audit (truncation invariance, new entry rules)

| rule | decisions tested | order-log / fill mismatches |
|---|---|---|
| C4 k=1.0 | 300 | 0 |
| C5 m=10 | 300 | 0 |
| C6 N=15 | 300 | 0 |
| C7 | 300 | 0 |
| C8 C4 k=1.5 t20 | 300 | 0 |
| C8 C6 N=15 t40 | 300 | 0 |
| PLANTED look-ahead (positive control) | 300 | 23 |
| D2 own_signals | 4 | 0 |

Bars and 1-s data after a random cut were replaced by NaN or noise; every order placed at or before the cut and every trade fully closed before it had to be identical. The planted look-ahead (VWAP including the next bar) is caught (positive control); the five real rules and the D2 signal code show 0 hits, so no fix/re-run was needed.

## Table 3 - R11 full-system sequence test (pair + candidate as one system on the full tape, live locks/give-back/week floor, candidate = own book with the same per-book limits, 50-contract/opposite-side filter), WF-PRE

| system | weekly mean | weekly SD | maxDD | worst week | L8W mean | L8W maxDD | maxDD <= C0 system |
|---|---|---|---|---|---|---|---|
| Set A (benchmark, no switch) | 17,549 | 97,533 | 401,293 | -136,494 | 34,191 | 267,133 | - |
| **C0 = Set A + halt switch (+60 CHOSEN 0.3 (primary))** | 32,178 | 92,475 | 382,482 | -140,761 | 38,893 | 267,403 | baseline |
| **C0 = Set A + halt switch (+15 STACK-FB 0.3)** | 20,145 | 96,883 | 454,627 | -137,257 | 50,776 | 250,456 | baseline |
| **C0 = Set A + halt switch (+30 LITE-FR 0.4)** | 29,948 | 100,164 | 361,825 | -135,574 | 43,240 | 366,527 | baseline |
| **C0 = Set A + halt switch (+5 STACK-FB 0.3 (informational))** | 29,779 | 88,466 | 362,811 | -136,494 | 43,198 | 219,799 | baseline |
| (no cell passed; the rows below are the family best by delta mean, shown for information) | | | | | | | |
| C1 on top of C0 (+60) | 32,253 | 100,019 | 354,988 | -138,171 | 22,279 | 299,787 | yes |
| C5_m10 on top of C0 (+60) | 32,245 | 91,602 | 343,661 | -135,550 | 37,949 | 254,027 | yes |
| C4_k2.0 on top of C0 (+60) | 28,165 | 94,444 | 538,359 | -135,550 | 45,284 | 223,983 | NO |
| C7 on top of C0 (+60) | 30,829 | 91,944 | 390,869 | -135,550 | 38,632 | 259,557 | NO |
| C6_N20 on top of C0 (+60) | 17,347 | 94,091 | 472,551 | -135,792 | 24,730 | 358,581 | NO |
