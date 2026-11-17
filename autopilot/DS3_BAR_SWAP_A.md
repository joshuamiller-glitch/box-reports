# DS3 BAR SWAP A (W-SWA): K7 / M7 / U7 book signal on other bars, per weak session

Header: trials counted = 171 bar rows x 3 books x up to 9 cells (screen of 57 rows x 9 cells); correction = White reality check per cell (p reported) + neighbour agreement; selection = trailing-6M pick (in-sample for the pick window), validation = rolling walk-forward (out-of-sample), older years = tolerant AMBER/RED check; data end 2026-11-13.

1. Tried: the exact K7 (Keltner break), M7 (momentum vote) and U7 (Supertrend) signal on 57 bar rows (own epoch time bars + W-BAR event/price bars), standalone raw chassis, live 60/60 bracket, tape fills, flat at session end.
2. Holds: 0 of 6 weak cells have a gated trailing-6M pick that is not RED in older years: none.
3. Does not hold: K7 nyam (NOT FINISHED (older-year coverage < 60%)); M7 london (RED); K7 london (RED); K7 nypm (no gated pick); M7 nyam (NOT FINISHED (older-year coverage < 60%)); U7 london (NOT FINISHED (older-year coverage < 60%)).
4. Needs in DS7: a custom BarsType per pick that is not Tick/Volume/Range/Renko/Minute (rule text in the rows); alt-bar slots X1-X8 are OFF today, so each swap is new wiring; nothing changes live.
5. Next: engine swap test (hook, identity first) for each non-RED pick, random-clock nulls, per-book parameter grid on the picked bar, Asia phase 2. Pick rule: trailing 6M to 2026-11-13 (3M beside), validated by rolling walk-forward.

## K7 nyam (reference live bar tm180)

Reference tm180: L6M -1310 USD/wk (net, 1 lot), L3M -634, L12M -1383, trades L6M 426

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | vsess_600 | +588 | 175 | +1182 | no |
| 2 | vsess_300 | +519 | 149 | +1045 | no |
| 3 | vnorm_80 | +276 | 44 | +555 | no |
| 4 | tsf_25_150 | +241 | 16 | +484 | no |
| 5 | tsf_5_700 | +237 | 37 | +476 | no |
| 6 | tsf_10_30 | +235 | 102 | +472 | no |
| 7 | tsf_10_700 | +224 | 20 | +450 | no |
| 8 | vnorm_40 | +201 | 30 | +403 | pass |

PICK (trailing 6M to 2026-11-13): **vnorm_40**. Trailing-3M pick: tsf_25_150 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **NOT FINISHED (older-year coverage < 60%)**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| older pooled (14 covered days of 1131) | +0 | +1652 | +100% | -100% | -100% |
White RC (best of 51 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.371

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 34 | +24 | -195 | 19625 | 37057 | 29% | 62% | 55% | +104/-835 | -739/-910 | -305/-2045 |
| 3M->1M | 35 | -787 | -221 | 57945 | 40022 | 23% | 51% | 18% | -3374/-949 | -4599/-1612 | -3476/-1811 |
| 12M->1M | 28 | -44 | -269 | 23344 | 40115 | 29% | 50% | 59% | -189/-1152 | -1972/-2677 | -6244/-5924 |
| 6M->2wk | 75 | -282 | -231 | 34355 | 40805 | 23% | 49% | 61% | -1297/-598 | -2186/-1359 | -2182/-2467 |
| 6M->3M | 10 | -195 | +20 | 17382 | 18750 | 10% | 40% | 33% | -1529/-1581 | -2505/+262 | -3223/+623 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## M7 london (reference live bar tm60)

Reference tm60: L6M -923 USD/wk (net, 1 lot), L3M -1137, L12M -667, trades L6M 536

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tm600 | +720 | 118 | +1172 | no |
| 2 | tm1200 | +709 | 83 | +433 | no |
| 3 | tm300 | +435 | 225 | +2092 | no |
| 4 | tm780 | +367 | 102 | +461 | pass |
| 5 | tm2700 | +292 | 40 | +208 | no |
| 6 | tm180 | +289 | 266 | +485 | no |
| 7 | tm900 | +252 | 96 | +478 | pass |
| 8 | tm45 | +232 | 572 | -168 | no |

PICK (trailing 6M to 2026-11-13): **tm780**. Trailing-3M pick: tm300 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -23 | +333 | +107% | -28% | -37% |
| 2024 | -394 | -1091 | -64% | -60% | -56% |
| 2025 | -112 | -279 | -60% | -47% | -51% |
| 2026 | -841 | -643 | +31% | -34% | -32% |
| older pooled (1070 covered days of 1131) | -236 | -429 | -45% | -58% | -54% |
White RC (best of 31 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.226

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 34 | -753 | -731 | 66937 | 64070 | 9% | 26% | 70% | -3229/-3135 | -8537/-8251 | -16567/-15841 |
| 3M->1M | 35 | -722 | -787 | 61269 | 70226 | 17% | 34% | 50% | -3094/-3371 | -7594/-8607 | -14518/-16049 |
| 12M->1M | 28 | -658 | -621 | 44626 | 42623 | 4% | 32% | 93% | -2819/-2662 | -6786/-6832 | -12872/-12818 |
| 6M->2wk | 75 | -653 | -695 | 59752 | 64267 | 11% | 37% | 82% | -3181/-3259 | -8540/-8557 | -16025/-15465 |
| 6M->3M | 10 | -604 | -594 | 60668 | 59186 | 10% | 10% | 56% | -2724/-2819 | -7765/-7637 | -17961/-16658 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## K7 london (reference live bar tm180)

Reference tm180: L6M -856 USD/wk (net, 1 lot), L3M -392, L12M -601, trades L6M 485

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tm900 | +755 | 263 | +1056 | no |
| 2 | tm60 | +676 | 730 | +2505 | no |
| 3 | tm780 | +651 | 294 | -498 | pass |
| 4 | tm3600 | +316 | 80 | +226 | no |
| 5 | tm600 | +123 | 349 | -350 | no |
| 6 | tsf_25_150 | +48 | 3 | +96 | no |
| 7 | tsf_5_1200 | +23 | 4 | +46 | no |
| 8 | tm1800 | -12 | 148 | -231 | no |

PICK (trailing 6M to 2026-11-13): **tm780**. Trailing-3M pick: none (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -193 | +149 | +229% | +61% | +52% |
| 2024 | -375 | -233 | +61% | +27% | +7% |
| 2025 | +85 | +141 | +40% | -41% | -12% |
| 2026 | -475 | -748 | -37% | -25% | -48% |
| older pooled (1070 covered days of 1131) | -180 | -46 | +294% | +89% | +37% |
White RC (best of 39 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.400

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 34 | -203 | -202 | 17022 | 14942 | 21% | 47% | 61% | -871/-867 | -396/-1616 | +928/-3394 |
| 3M->1M | 35 | -110 | -137 | 14148 | 14122 | 34% | 51% | 53% | -470/-588 | -1203/-1694 | -2259/-3191 |
| 12M->1M | 28 | -184 | -138 | 18754 | 14135 | 11% | 43% | 74% | -790/-591 | +310/-485 | +705/-1074 |
| 6M->2wk | 75 | -137 | -194 | 18770 | 17389 | 23% | 44% | 77% | -725/-1071 | -1614/-2073 | -1906/-3781 |
| 6M->3M | 10 | +111 | -164 | 10514 | 14235 | 50% | 70% | 44% | +1024/+515 | +1424/-2114 | +4405/-2695 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## K7 nypm (reference live bar tm180)

Reference tm180: L6M -397 USD/wk (net, 1 lot), L3M -679, L12M -498, trades L6M 398

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tm1800 | +603 | 65 | +222 | no |
| 2 | tm120 | +384 | 552 | -1479 | no |
| 3 | tm10 | +303 | 994 | +157 | no |
| 4 | tsf_5_1200 | +202 | 28 | +406 | no |
| 5 | vsess_600 | +84 | 134 | +169 | no |
| 6 | tsf_5_100 | +63 | 106 | +126 | no |
| 7 | vsess_30 | +31 | 51 | +63 | no |
| 8 | tsf_5_700 | +27 | 46 | +54 | no |

No row passes the gate in the trailing 6 months (n>=30, positive, neighbours positive): no swap pick; reference stays reference (BEST-AVAILABLE-NOT-PROVEN row shows best ungated).


PICK (trailing 6M to 2026-11-13): **tm1800** (ungated best, not a pick). Trailing-3M pick: tsf_5_1200 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -17 | -726 | -98% | -75% | -75% |
| 2024 | -646 | +448 | +244% | +9% | +20% |
| 2025 | -193 | -300 | -36% | +12% | -5% |
| 2026 | -1067 | -148 | +621% | +1% | -5% |
| older pooled (1070 covered days of 1131) | -364 | -140 | +160% | +13% | +15% |
White RC (best of 48 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.671

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 34 | -387 | -178 | 42748 | 24790 | 15% | 44% | 55% | -1658/-761 | -5401/-1702 | -8683/-1642 |
| 3M->1M | 35 | +243 | -117 | 19016 | 25906 | 40% | 54% | 50% | +1042/-503 | -1420/-1258 | -7257/-1182 |
| 12M->1M | 28 | -657 | -169 | 54259 | 32353 | 4% | 32% | 89% | -2814/-726 | -8578/-2900 | -11779/-6325 |
| 6M->2wk | 75 | -65 | -120 | 32021 | 29456 | 13% | 49% | 74% | -1195/-801 | -4385/-1526 | -7274/-1473 |
| 6M->3M | 10 | -55 | -42 | 23199 | 13818 | 10% | 40% | 56% | +3479/+2356 | -712/-535 | -2734/-638 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## M7 nyam (reference live bar tm60)

Reference tm60: L6M -512 USD/wk (net, 1 lot), L3M -1456, L12M -415, trades L6M 468

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | vsess_50 | +488 | 55 | +981 | no |
| 2 | tm1200 | +477 | 64 | +416 | no |
| 3 | tsf_10_120 | +358 | 32 | +720 | no |
| 4 | tsf_5_100 | +333 | 75 | +669 | pass |
| 5 | tsf_10_700 | +320 | 7 | +644 | no |
| 6 | tm600 | +314 | 122 | +1428 | no |
| 7 | tm780 | +302 | 88 | +1038 | no |
| 8 | tm2700 | +277 | 41 | -222 | no |

PICK (trailing 6M to 2026-11-13): **tsf_5_100**. Trailing-3M pick: tsf_5_100.
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **NOT FINISHED (older-year coverage < 60%)**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| older pooled (14 covered days of 1131) | +0 | +2404 | +100% | -100% | -100% |
White RC (best of 43 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.597

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 34 | -65 | +80 | 12518 | 17758 | 24% | 41% | 64% | -278/+345 | -3932/+1173 | -6550/+3731 |
| 3M->1M | 35 | -168 | +57 | 20035 | 18310 | 29% | 43% | 53% | -722/+243 | -3372/+1072 | -3545/+4055 |
| 12M->1M | 28 | -212 | +305 | 21484 | 15115 | 4% | 36% | 67% | -908/+1309 | -713/+3213 | +1851/+7384 |
| 6M->2wk | 75 | +37 | +51 | 17797 | 21307 | 23% | 49% | 74% | +448/+674 | -1834/+1559 | -4379/+4052 |
| 6M->3M | 10 | -313 | +115 | 24687 | 17047 | 30% | 40% | 33% | -1377/-661 | -4028/+1481 | -7588/+3404 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## U7 london (reference live bar tm600)

Reference tm600: L6M -222 USD/wk (net, 1 lot), L3M -878, L12M -112, trades L6M 133

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | vsess_450 | +812 | 89 | +1633 | pass |
| 2 | vsess_600 | +782 | 93 | +1572 | pass |
| 3 | vnorm_1500 | +550 | 67 | +1106 | no |
| 4 | vsess_300 | +523 | 76 | +1051 | pass |
| 5 | tm1800 | +346 | 42 | +388 | no |
| 6 | tsf_2_200 | +262 | 50 | +526 | no |
| 7 | tm780 | +259 | 96 | +190 | no |
| 8 | tm2700 | +212 | 21 | +73 | no |

PICK (trailing 6M to 2026-11-13): **vsess_450**. Trailing-3M pick: vsess_450.
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **NOT FINISHED (older-year coverage < 60%)**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| older pooled (14 covered days of 1131) | +0 | -1923 | -100% | -100% | -100% |
White RC (best of 30 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.590

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 34 | -139 | -148 | 21458 | 18032 | 26% | 47% | 48% | -595/-633 | -2255/-1980 | -5095/-4406 |
| 3M->1M | 35 | -163 | -174 | 20716 | 18954 | 31% | 51% | 50% | -699/-744 | -1827/-2027 | -4032/-4515 |
| 12M->1M | 28 | -92 | -154 | 10935 | 14369 | 36% | 50% | 70% | -393/-659 | -2637/-2077 | -8147/-4297 |
| 6M->2wk | 75 | -27 | -205 | 10585 | 19021 | 31% | 55% | 73% | -204/-808 | -1576/-1835 | -4244/-4520 |
| 6M->3M | 10 | -71 | -170 | 18872 | 17333 | 30% | 60% | 33% | -1406/-441 | -913/-2185 | -4244/-4747 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## K7 asia (reference live bar tm180)

Reference tm180: L6M +623 USD/wk (net, 1 lot), L3M +193, L12M +27, trades L6M 573

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tm600 | +2183 | 386 | +2502 | pass |
| 2 | tm240 | +2114 | 638 | +2318 | pass |
| 3 | tm120 | +1816 | 771 | +948 | pass |
| 4 | tm300 | +1777 | 573 | +2182 | pass |
| 5 | tm60 | +1602 | 907 | -616 | no |
| 6 | tm420 | +1454 | 485 | +2271 | pass |
| 7 | tm780 | +1187 | 339 | +367 | pass |
| 8 | tm180 | +623 | 573 | +193 | pass |

PICK (trailing 6M to 2026-11-13): **tm600**. Trailing-3M pick: tm600.
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -39 | +195 | +120% | +59% | +29% |
| 2024 | +299 | -37 | -907% | -56% | -51% |
| 2025 | -35 | -485 | -93% | -34% | -49% |
| 2026 | -267 | +1302 | +121% | +128% | +70% |
| older pooled (1070 covered days of 1131) | +62 | -41 | -253% | -48% | -47% |
White RC (best of 43 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.504

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 34 | +338 | +50 | 8373 | 14803 | 44% | 71% | 61% | +1447/+214 | +3133/-998 | +8221/+181 |
| 3M->1M | 35 | +233 | +34 | 14035 | 17725 | 46% | 60% | 35% | +1000/+144 | -480/-1010 | +1567/-159 |
| 12M->1M | 28 | +317 | +42 | 9292 | 16672 | 46% | 68% | 70% | +1359/+178 | +3578/-1983 | +9256/-2242 |
| 6M->2wk | 75 | +264 | +75 | 12474 | 18651 | 41% | 53% | 72% | +1133/+199 | +2194/-1062 | +6840/+87 |
| 6M->3M | 10 | +305 | -220 | 7184 | 20760 | 60% | 60% | 33% | +1092/+225 | +3923/-2834 | +9262/-3665 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## M7 asia (reference live bar tm60)

Reference tm60: L6M +1449 USD/wk (net, 1 lot), L3M +2353, L12M +677, trades L6M 597

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tm120 | +2368 | 442 | +2953 | pass |
| 2 | tm30 | +1486 | 798 | +1518 | no |
| 3 | tm60 | +1449 | 597 | +2353 | pass |
| 4 | tm10 | +1445 | 1007 | +2116 | pass |
| 5 | tm15 | +1319 | 938 | +169 | no |
| 6 | tm300 | +871 | 237 | +433 | pass |
| 7 | tm45 | +808 | 705 | +2285 | pass |
| 8 | tsf_2_100 | +679 | 80 | +1366 | pass |

PICK (trailing 6M to 2026-11-13): **tm120**. Trailing-3M pick: tm120.
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -204 | +136 | +250% | +74% | +41% |
| 2024 | +45 | +551 | +92% | +157% | +147% |
| 2025 | +347 | +96 | -263% | -66% | -60% |
| 2026 | -414 | +889 | +147% | +34% | -3% |
| older pooled (1070 covered days of 1131) | +55 | +316 | +83% | +14% | -14% |
White RC (best of 35 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.615

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 34 | +583 | +628 | 11046 | 8987 | 18% | 76% | 67% | +2499/+2692 | +7233/+7320 | +11317/+12886 |
| 3M->1M | 35 | +395 | +622 | 4872 | 5281 | 37% | 69% | 35% | +1692/+2667 | +4564/+7168 | +8153/+13350 |
| 12M->1M | 28 | +580 | +534 | 10079 | 10441 | 29% | 61% | 63% | +2485/+2289 | +6924/+6530 | +7113/+10875 |
| 6M->2wk | 75 | +768 | +652 | 7261 | 8022 | 29% | 68% | 76% | +2718/+2680 | +6989/+7146 | +11719/+12942 |
| 6M->3M | 10 | +418 | +439 | 10728 | 7829 | 10% | 80% | 22% | +825/+829 | +5373/+5650 | +11847/+11960 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## U7 asia (reference live bar tm600)

Reference tm600: L6M +697 USD/wk (net, 1 lot), L3M +329, L12M +369, trades L6M 153

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tm420 | +710 | 217 | +860 | no |
| 2 | tm600 | +697 | 153 | +329 | no |
| 3 | tm120 | +650 | 473 | -1448 | no |
| 4 | vnorm_1500 | +599 | 92 | +1204 | pass |
| 5 | vnorm_1000 | +407 | 72 | +818 | no |
| 6 | tm240 | +382 | 314 | +69 | no |
| 7 | tm1800 | +334 | 38 | +359 | no |
| 8 | tm180 | +287 | 325 | -1153 | pass |

PICK (trailing 6M to 2026-11-13): **vnorm_1500**. Trailing-3M pick: vnorm_1500.
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **NOT FINISHED (older-year coverage < 60%)**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| older pooled (14 covered days of 1131) | +0 | -38 | -100% | -100% | -100% |
White RC (best of 33 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.990

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 34 | +254 | +293 | 3008 | 2834 | 29% | 68% | 48% | +1088/+1255 | +2968/+3182 | +5119/+5595 |
| 3M->1M | 35 | -37 | +256 | 19184 | 2779 | 29% | 57% | 38% | -160/+1098 | +1172/+3131 | +2411/+5309 |
| 12M->1M | 28 | +138 | +334 | 10678 | 3456 | 29% | 61% | 59% | +590/+1433 | +2224/+3549 | +4423/+6017 |
| 6M->2wk | 75 | +212 | +281 | 4885 | 2861 | 20% | 59% | 65% | +806/+1372 | +2504/+3129 | +4593/+5547 |
| 6M->3M | 10 | +213 | +243 | 1518 | 2629 | 20% | 70% | 22% | +633/+610 | +2740/+3123 | +6488/+5355 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).
