# DS3 BAR SWAP A (W-SWA): K7 / M7 / U7 book signal on other bars, per weak session

Header: trials counted = 855 bar rows x 3 books x up to 9 cells (screen of 285 rows x 9 cells); correction = White reality check per cell (p reported) + neighbour agreement; selection = trailing-6M pick (in-sample for the pick window), validation = rolling walk-forward (out-of-sample), older years = tolerant AMBER/RED check; data end 2026-11-13.

1. Tried: the exact K7 (Keltner break), M7 (momentum vote) and U7 (Supertrend) signal on 285 bar rows (own epoch time bars + W-BAR event/price bars), standalone raw chassis, live 60/60 bracket, tape fills, flat at session end.
2. Holds: 0 of 6 weak cells have a gated trailing-6M pick that is not RED in older years: none.
3. Does not hold: K7 nyam (RED); M7 london (RED); K7 london (RED); K7 nypm (RED); M7 nyam (RED); U7 london (RED).
4. Needs in DS7: a custom BarsType per pick that is not Tick/Volume/Range/Renko/Minute (rule text in the rows); alt-bar slots X1-X8 are OFF today, so each swap is new wiring; nothing changes live.
5. Next: engine swap test (hook, identity first) for each non-RED pick, random-clock nulls, per-book parameter grid on the picked bar, Asia phase 2. Pick rule: trailing 6M to 2026-11-13 (3M beside), validated by rolling walk-forward.

## K7 nyam (reference live bar tm180)

Reference tm180: L6M -1310 USD/wk (net, 1 lot), L3M -634, L12M -2081, trades L6M 426

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | vsess_300 | +725 | 271 | +1045 | no |
| 2 | tsf_5_700 | +580 | 64 | +476 | no |
| 3 | frenko_28 | +557 | 1316 | -1273 | no |
| 4 | mrenko_10 | +512 | 1635 | +2543 | no |
| 5 | vol_350 | +449 | 1589 | +3024 | no |
| 6 | renko_14 | +351 | 1413 | -664 | no |
| 7 | trb_6000 | +259 | 313 | +758 | no |
| 8 | renko_10 | +217 | 1590 | +3531 | pass |

PICK (trailing 6M to 2026-11-13): **renko_10**. Trailing-3M pick: mrenko_10 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | +183 | +195 | +6% | -36% | -33% |
| 2024 | -249 | +1068 | +123% | +229% | +136% |
| 2025 | -46 | -556 | -92% | -10% | -6% |
| 2026 | -2206 | -2680 | -18% | +12% | +5% |
| older pooled (1131 covered days of 1131) | -314 | -106 | +197% | +5% | -21% |

Windows, pick (renko_10) vs live bar (tm180), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +217 | -1310 | 41960 | 31475 | 73770 | 40318 | 183 |
| L3M | +3531 | -634 | 4524 | 9608 | 18113 | 11345 | 91 |
| HOLD 2025-11..2026-04 | -1921 | -2687 | 43604 | 45385 | 75888 | 80953 | 181 |
| 2023-04..12 | +183 | +195 | 6926 | 10845 | 15695 | 23530 | 266 |
| 2024 | -249 | +1068 | 15834 | 4811 | 30686 | 12978 | 366 |
| 2025 | -46 | -556 | 23600 | 26369 | 46861 | 49994 | 365 |
| all | -240 | -273 | 45201 | 56018 | 118862 | 137872 | 1314 |
White RC (best of 252 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.923

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -723 | -448 | 65132 | 56579 | 51% | 30% | 22% | -3100/-1919 | -6501/-5091 | -8684/-10326 |
| 3M->1M | 38 | -778 | -423 | 62830 | 56701 | 39% | 42% | 3% | -3336/-1813 | -9319/-4871 | -13475/-9745 |
| 12M->1M | 31 | -239 | -538 | 22646 | 59848 | 58% | 26% | 50% | -1023/-2307 | +106/-7414 | -162/-15444 |
| 6M->2wk | 80 | -675 | -444 | 74256 | 57221 | 50% | 32% | 41% | -3529/-1549 | -5268/-4877 | -11120/-10154 |
| 6M->3M | 12 | -240 | -428 | 22285 | 50930 | 67% | 33% | 0% | -2852/-1940 | -3092/-5509 | -6635/-10650 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS +88 USD/wk, share >0 57%; best random-clock row L6M +814 USD/wk (median -603) vs best real row +725

## M7 london (reference live bar tm60)

Reference tm60: L6M -923 USD/wk (net, 1 lot), L3M -1137, L12M -623, trades L6M 536

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | lbrk_5_20 | +782 | 118 | +508 | no |
| 2 | tm600 | +720 | 118 | +1172 | no |
| 3 | tm1200 | +709 | 83 | +433 | no |
| 4 | lbrk_3_40 | +544 | 62 | +1297 | no |
| 5 | dol_750 | +526 | 245 | +863 | no |
| 6 | mrenko_40 | +486 | 110 | +126 | pass |
| 7 | lbrk_5_10 | +439 | 257 | -385 | pass |
| 8 | lbrk_4_40 | +437 | 49 | +712 | no |

PICK (trailing 6M to 2026-11-13): **mrenko_40**. Trailing-3M pick: tm300 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | +32 | +333 | +91% | -70% | -72% |
| 2024 | -377 | -1091 | -65% | -62% | -65% |
| 2025 | -315 | -279 | +13% | -8% | -24% |
| 2026 | -476 | -231 | +106% | -30% | -43% |
| older pooled (1131 covered days of 1131) | -272 | -392 | -31% | -56% | -48% |

Windows, pick (mrenko_40) vs live bar (tm60), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +486 | -923 | 3866 | 19014 | 8009 | 30647 | 183 |
| L3M | +126 | -1137 | 1752 | 12739 | 4146 | 21422 | 91 |
| HOLD 2025-11..2026-04 | -571 | -336 | 10420 | 14439 | 18424 | 25914 | 181 |
| 2023-04..12 | +32 | +333 | 1862 | 6285 | 4033 | 14421 | 266 |
| 2024 | -377 | -1091 | 14741 | 38388 | 22244 | 63453 | 366 |
| 2025 | -315 | -279 | 13206 | 14308 | 20765 | 27502 | 365 |
| all | -167 | -466 | 26664 | 63698 | 48688 | 110313 | 1314 |
White RC (best of 210 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.354

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -522 | -638 | 52591 | 64390 | 43% | 32% | 22% | -2238/-2735 | -3346/-7972 | -5499/-15122 |
| 3M->1M | 38 | -359 | -671 | 31373 | 69257 | 53% | 39% | 8% | -1539/-2876 | -4157/-8037 | -7353/-15201 |
| 12M->1M | 31 | -356 | -540 | 41686 | 42599 | 39% | 42% | 63% | -1527/-2316 | -1821/-6918 | -4154/-12509 |
| 6M->2wk | 80 | -350 | -628 | 44163 | 64369 | 41% | 40% | 51% | -1789/-2976 | -4030/-8119 | -6732/-14820 |
| 6M->3M | 12 | -267 | -588 | 40777 | 64971 | 58% | 42% | 9% | -730/-3724 | -3439/-7555 | -8253/-15660 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS -248 USD/wk, share >0 46%; best random-clock row L6M +1455 USD/wk (median -63) vs best real row +782

## K7 london (reference live bar tm180)

Reference tm180: L6M -856 USD/wk (net, 1 lot), L3M -392, L12M -740, trades L6M 485

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | urenko_14 | +2034 | 745 | +1092 | no |
| 2 | vib_700 | +1214 | 799 | +1415 | no |
| 3 | dlt_30 | +1031 | 775 | +1594 | no |
| 4 | dib_6000 | +997 | 485 | -580 | no |
| 5 | trb_700 | +757 | 500 | +646 | no |
| 6 | tm900 | +755 | 263 | +1056 | no |
| 7 | tm60 | +676 | 730 | +2505 | no |
| 8 | mrenko_80 | +656 | 110 | -74 | no |

PICK (trailing 6M to 2026-11-13): **tm780**. Trailing-3M pick: dlt_30 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -193 | +149 | +229% | +61% | +52% |
| 2024 | -375 | -233 | +61% | +27% | +7% |
| 2025 | +85 | +141 | +40% | -41% | -12% |
| 2026 | +22 | -786 | -103% | -63% | -65% |
| older pooled (1131 covered days of 1131) | -137 | -88 | +55% | +83% | +37% |

Windows, pick (tm780) vs live bar (tm180), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +651 | -856 | 7128 | 22526 | 25336 | 38405 | 183 |
| L3M | -498 | -392 | 9826 | 7831 | 25336 | 18037 | 91 |
| HOLD 2025-11..2026-04 | +16 | -411 | 10711 | 11685 | 17909 | 31313 | 181 |
| 2023-04..12 | -193 | +149 | 8931 | 5545 | 19017 | 12516 | 266 |
| 2024 | -375 | -233 | 21798 | 17170 | 33086 | 30932 | 366 |
| 2025 | +85 | +141 | 6951 | 11709 | 18224 | 20667 | 365 |
| all | -27 | -195 | 26208 | 22290 | 47307 | 63493 | 1314 |
White RC (best of 239 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.217

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -420 | -277 | 46628 | 19336 | 43% | 43% | 25% | -1801/-1187 | -3645/-3360 | -3315/-6662 |
| 3M->1M | 38 | -414 | -273 | 43750 | 21304 | 47% | 37% | 16% | -1773/-1170 | -7312/-3363 | -10300/-6656 |
| 12M->1M | 31 | -254 | -217 | 18059 | 18806 | 45% | 26% | 37% | -1090/-928 | -1626/-2646 | -1517/-5208 |
| 6M->2wk | 80 | -192 | -274 | 25023 | 21751 | 45% | 40% | 49% | -2032/-1468 | -4483/-3496 | -5115/-6607 |
| 6M->3M | 12 | -302 | -296 | 41603 | 19845 | 58% | 50% | 0% | -3283/-249 | -3884/-3805 | -6486/-7329 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS -415 USD/wk, share >0 38%; best random-clock row L6M +981 USD/wk (median -293) vs best real row +2034

## K7 nypm (reference live bar tm180)

Reference tm180: L6M -397 USD/wk (net, 1 lot), L3M -679, L12M -772, trades L6M 398

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tsf_10_60 | +701 | 126 | +0 | no |
| 2 | drb_6000 | +624 | 205 | -522 | no |
| 3 | tm1800 | +603 | 65 | +222 | no |
| 4 | trb_2000 | +556 | 519 | -1046 | no |
| 5 | pnf_56 | +482 | 45 | +254 | no |
| 6 | cusum_28 | +464 | 825 | +78 | no |
| 7 | vsess_600 | +419 | 218 | +169 | no |
| 8 | cusum_112 | +416 | 176 | +3 | no |

PICK (trailing 6M to 2026-11-13): **tsf_10_30**. Trailing-3M pick: tsf_5_1200 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -335 | -726 | -54% | -14% | -36% |
| 2024 | +406 | +448 | +9% | -22% | -30% |
| 2025 | -377 | -300 | +25% | -3% | -7% |
| 2026 | -2989 | -827 | +262% | +108% | +58% |
| older pooled (1131 covered days of 1131) | -423 | -221 | +92% | -10% | +18% |

Windows, pick (tsf_10_30) vs live bar (tm180), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +391 | -397 | 5362 | 13938 | 21509 | 24062 | 183 |
| L3M | -343 | -679 | 7602 | 10285 | 21509 | 15220 | 91 |
| HOLD 2025-11..2026-04 | -2971 | -1191 | 47339 | 25119 | 82956 | 52445 | 181 |
| 2023-04..12 | -335 | -726 | 13581 | 15784 | 20763 | 32276 | 266 |
| 2024 | +406 | +448 | 9968 | 12792 | 19661 | 28089 | 366 |
| 2025 | -377 | -300 | 17613 | 18187 | 31204 | 33432 | 365 |
| all | -310 | -245 | 37771 | 36371 | 92543 | 78181 | 1314 |
White RC (best of 249 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.965

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -344 | -203 | 28363 | 29415 | 41% | 38% | 14% | -1473/-870 | -4109/-2186 | -9676/-4072 |
| 3M->1M | 38 | -184 | -198 | 38235 | 33438 | 45% | 53% | 19% | -790/-850 | -7176/-2095 | -17326/-3861 |
| 12M->1M | 31 | -654 | -223 | 52820 | 37946 | 35% | 29% | 40% | -2803/-958 | -6339/-3657 | -14878/-8985 |
| 6M->2wk | 80 | -473 | -201 | 52608 | 36018 | 50% | 39% | 41% | -2378/-1029 | -7104/-2370 | -15454/-4098 |
| 6M->3M | 12 | +51 | -183 | 7016 | 25449 | 50% | 42% | 9% | +1109/+2363 | +657/-2347 | +1331/-3848 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS -578 USD/wk, share >0 41%; best random-clock row L6M +213 USD/wk (median -537) vs best real row +701

## M7 nyam (reference live bar tm60)

Reference tm60: L6M -512 USD/wk (net, 1 lot), L3M -1456, L12M -480, trades L6M 468

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tsf_10_120 | +663 | 53 | +720 | no |
| 2 | vsess_50 | +597 | 80 | +981 | no |
| 3 | tm1200 | +477 | 64 | +416 | no |
| 4 | mrenko_112 | +453 | 31 | +180 | no |
| 5 | tick_2000 | +441 | 269 | +64 | no |
| 6 | tsf_5_400 | +396 | 49 | +324 | pass |
| 7 | urenko_56 | +394 | 170 | -28 | no |
| 8 | tsf_2_1200 | +366 | 79 | +539 | no |

PICK (trailing 6M to 2026-11-13): **tsf_5_400**. Trailing-3M pick: tick_8000 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -186 | -92 | +102% | -25% | -36% |
| 2024 | +43 | +114 | +62% | -52% | -52% |
| 2025 | -544 | +394 | +238% | -7% | -15% |
| 2026 | +209 | +156 | -33% | -34% | -34% |
| older pooled (1131 covered days of 1131) | -181 | +161 | +212% | -10% | -3% |

Windows, pick (tsf_5_400) vs live bar (tm60), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +396 | -512 | 788 | 14052 | 3890 | 26831 | 183 |
| L3M | +324 | -1456 | 858 | 14481 | 3890 | 22485 | 91 |
| HOLD 2025-11..2026-04 | -313 | -83 | 10838 | 12032 | 18550 | 25122 | 181 |
| 2023-04..12 | -186 | -92 | 7263 | 9632 | 13096 | 20368 | 266 |
| 2024 | +43 | +114 | 6741 | 14034 | 12895 | 26868 | 366 |
| 2025 | -544 | +394 | 15376 | 16511 | 29156 | 34403 | 365 |
| all | -100 | +67 | 19939 | 22362 | 40579 | 41740 | 1314 |
White RC (best of 237 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.905

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -561 | +23 | 39612 | 19749 | 35% | 24% | 19% | -2403/+99 | -6987/+962 | -11287/+2819 |
| 3M->1M | 38 | -76 | +30 | 23081 | 18952 | 47% | 39% | 11% | -328/+128 | -1254/+1051 | -3398/+2907 |
| 12M->1M | 31 | -632 | +249 | 48261 | 17890 | 35% | 35% | 20% | -2709/+1069 | -4610/+2875 | -10105/+5842 |
| 6M->2wk | 80 | -853 | +39 | 83854 | 22052 | 39% | 29% | 34% | -2679/+562 | -6631/+1364 | -13804/+3193 |
| 6M->3M | 12 | -688 | +74 | 73065 | 18051 | 25% | 17% | 9% | -2772/+585 | -8846/+951 | -12812/+2310 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS -364 USD/wk, share >0 35%; best random-clock row L6M +536 USD/wk (median -119) vs best real row +663

## U7 london (reference live bar tm600)

Reference tm600: L6M -222 USD/wk (net, 1 lot), L3M -878, L12M -13, trades L6M 133

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | vsess_450 | +1441 | 148 | +1633 | pass |
| 2 | dib_240 | +1328 | 812 | +1943 | no |
| 3 | vsess_600 | +1001 | 161 | +1572 | pass |
| 4 | tib_700 | +958 | 645 | +1277 | no |
| 5 | dchg_10 | +860 | 533 | +700 | no |
| 6 | kagi_10 | +860 | 533 | +700 | no |
| 7 | vrb_240 | +858 | 657 | +2694 | pass |
| 8 | tib_1200 | +855 | 552 | +1159 | pass |

PICK (trailing 6M to 2026-11-13): **vsess_450**. Trailing-3M pick: vrb_240 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -42 | -405 | -90% | -48% | -27% |
| 2024 | -213 | -147 | +44% | +8% | +41% |
| 2025 | -301 | -133 | +127% | +63% | +77% |
| 2026 | -1376 | +170 | +910% | +684% | +334% |
| older pooled (1131 covered days of 1131) | -339 | -166 | +105% | +43% | +110% |

Windows, pick (vsess_450) vs live bar (tm600), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +1441 | -222 | 1532 | 6073 | 4463 | 15538 | 183 |
| L3M | +1633 | -878 | 749 | 8034 | 4449 | 15538 | 91 |
| HOLD 2025-11..2026-04 | -1279 | +467 | 24134 | 2464 | 43036 | 6047 | 181 |
| 2023-04..12 | -42 | -405 | 5855 | 11180 | 12241 | 16825 | 266 |
| 2024 | -213 | -147 | 12607 | 11708 | 30333 | 21491 | 366 |
| 2025 | -301 | -133 | 14214 | 8712 | 27773 | 15726 | 365 |
| all | -91 | -173 | 34934 | 22164 | 77537 | 36981 | 1314 |
White RC (best of 205 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.568

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -511 | -131 | 37452 | 17948 | 38% | 30% | 19% | -2192/-560 | -1943/-1523 | -2842/-3317 |
| 3M->1M | 38 | -354 | -160 | 42144 | 18938 | 47% | 39% | 19% | -1517/-687 | -4521/-1684 | -4895/-3423 |
| 12M->1M | 31 | -223 | -124 | 22645 | 13859 | 42% | 35% | 50% | -954/-531 | -4738/-1523 | -11772/-3086 |
| 6M->2wk | 80 | -256 | -160 | 31602 | 18001 | 45% | 42% | 42% | -1093/-680 | -1200/-1365 | -3019/-3352 |
| 6M->3M | 12 | +116 | -81 | 13746 | 15983 | 50% | 58% | 27% | -3197/-155 | +1489/-1046 | +1106/-2564 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS +36 USD/wk, share >0 54%; best random-clock row L6M +464 USD/wk (median -374) vs best real row +1441

## K7 asia (reference live bar tm180)

Reference tm180: L6M +623 USD/wk (net, 1 lot), L3M +193, L12M -120, trades L6M 573

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | vrb_700 | +3211 | 700 | +1329 | no |
| 2 | dol_500 | +2299 | 713 | +93 | pass |
| 3 | dchg_14 | +2273 | 1093 | +2332 | pass |
| 4 | kagi_14 | +2273 | 1093 | +2332 | pass |
| 5 | pnf_5 | +2189 | 1045 | +1208 | pass |
| 6 | tm600 | +2183 | 386 | +2502 | pass |
| 7 | wrenko_20 | +2149 | 694 | +2292 | pass |
| 8 | tm240 | +2114 | 638 | +2318 | pass |

PICK (trailing 6M to 2026-11-13): **dol_500**. Trailing-3M pick: tm600 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -146 | +195 | +175% | +175% | +120% |
| 2024 | +576 | -37 | -1653% | -86% | -77% |
| 2025 | -107 | -485 | -78% | +19% | +8% |
| 2026 | -165 | +308 | +154% | +1% | -11% |
| older pooled (1131 covered days of 1131) | +98 | -86 | -214% | -10% | -4% |

Windows, pick (dol_500) vs live bar (tm180), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +2299 | +623 | 7142 | 21298 | 18784 | 38434 | 183 |
| L3M | +93 | +193 | 8426 | 5085 | 18784 | 13036 | 91 |
| HOLD 2025-11..2026-04 | -608 | -630 | 17951 | 22838 | 31668 | 37864 | 181 |
| 2023-04..12 | -146 | +195 | 8002 | 2906 | 15165 | 6892 | 266 |
| 2024 | +576 | -37 | 1362 | 9687 | 5503 | 24134 | 366 |
| 2025 | -107 | -485 | 20324 | 17122 | 49681 | 45883 | 365 |
| all | +405 | +13 | 18273 | 22124 | 54506 | 56651 | 1314 |
White RC (best of 244 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.461

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +644 | +9 | 6544 | 18532 | 70% | 62% | 39% | +2762/+36 | +5742/-146 | +10575/-170 |
| 3M->1M | 38 | +159 | +13 | 14538 | 20550 | 55% | 58% | 11% | +681/+54 | +3045/-90 | +1608/-212 |
| 12M->1M | 31 | +509 | -42 | 11494 | 21021 | 71% | 45% | 37% | +2180/-180 | +1940/-771 | -2419/-2379 |
| 6M->2wk | 80 | +358 | +8 | 20163 | 21126 | 60% | 62% | 56% | +1651/-252 | +5563/-498 | +6915/-629 |
| 6M->3M | 12 | +472 | -2 | 3089 | 18765 | 67% | 75% | 18% | +2841/+1219 | +6069/-28 | +11519/-290 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS +550 USD/wk, share >0 73%; best random-clock row L6M +2114 USD/wk (median +988) vs best real row +3211

## M7 asia (reference live bar tm60)

Reference tm60: L6M +1449 USD/wk (net, 1 lot), L3M +2353, L12M +875, trades L6M 597

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tm120 | +2368 | 442 | +2953 | pass |
| 2 | frenko_10 | +2286 | 903 | +1805 | pass |
| 3 | tib_400 | +2208 | 866 | +808 | pass |
| 4 | dlt_45 | +1812 | 544 | +2569 | no |
| 5 | rng_10 | +1797 | 925 | +1549 | pass |
| 6 | dib_240 | +1519 | 949 | +1448 | pass |
| 7 | mrenko_10 | +1511 | 669 | +2483 | pass |
| 8 | tm30 | +1486 | 798 | +1518 | no |

PICK (trailing 6M to 2026-11-13): **tm120**. Trailing-3M pick: tm120.
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -204 | +136 | +250% | +74% | +41% |
| 2024 | +45 | +551 | +92% | +157% | +147% |
| 2025 | +347 | +96 | -263% | -66% | -60% |
| 2026 | +322 | +1024 | +69% | +13% | +12% |
| older pooled (1131 covered days of 1131) | +117 | +362 | +68% | +12% | -14% |

Windows, pick (tm120) vs live bar (tm60), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +2368 | +1449 | 4233 | 4549 | 12471 | 10715 | 183 |
| L3M | +2953 | +2353 | 3993 | 4474 | 12471 | 9959 | 91 |
| HOLD 2025-11..2026-04 | +215 | +497 | 6689 | 8617 | 13262 | 19297 | 181 |
| 2023-04..12 | -204 | +136 | 10431 | 6011 | 16838 | 11948 | 266 |
| 2024 | +45 | +551 | 10914 | 4245 | 26298 | 10626 | 366 |
| 2025 | +347 | +96 | 4299 | 12571 | 10416 | 25816 | 365 |
| all | +431 | +514 | 10364 | 9332 | 26298 | 30682 | 1314 |
White RC (best of 225 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.847

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +266 | +652 | 10627 | 8791 | 27% | 51% | 25% | +1140/+2794 | +3463/+8040 | +4407/+15319 |
| 3M->1M | 38 | +425 | +651 | 7029 | 5021 | 47% | 66% | 16% | +1820/+2792 | +3033/+7987 | +6094/+15113 |
| 12M->1M | 31 | +603 | +582 | 7446 | 9883 | 45% | 52% | 50% | +2585/+2496 | +6833/+7415 | +9717/+14185 |
| 6M->2wk | 80 | +433 | +646 | 9934 | 8056 | 44% | 60% | 46% | +1325/+2752 | +4068/+7814 | +6166/+14900 |
| 6M->3M | 12 | +128 | +545 | 17910 | 7062 | 33% | 42% | 0% | +2486/+498 | +1647/+7001 | +3616/+14663 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS +366 USD/wk, share >0 62%; best random-clock row L6M +1587 USD/wk (median +686) vs best real row +2368

## U7 asia (reference live bar tm600)

Reference tm600: L6M +697 USD/wk (net, 1 lot), L3M +329, L12M +309, trades L6M 153

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tick_300 | +2167 | 415 | +2193 | pass |
| 2 | dol_500 | +2161 | 376 | +2205 | pass |
| 3 | wrenko_10 | +2051 | 702 | +444 | pass |
| 4 | mrenko_14 | +2038 | 709 | +1753 | no |
| 5 | vnorm_1500 | +1996 | 479 | +1664 | pass |
| 6 | drb_400 | +1878 | 545 | +556 | no |
| 7 | vol_350 | +1820 | 502 | +285 | pass |
| 8 | dlt_70 | +1745 | 460 | +2177 | pass |

PICK (trailing 6M to 2026-11-13): **tick_300**. Trailing-3M pick: mom_20 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -63 | -3 | +1724% | +37% | +29% |
| 2024 | +27 | +128 | +79% | +184% | +137% |
| 2025 | +235 | +161 | -46% | +52% | +130% |
| 2026 | +1579 | +104 | -1419% | +20% | +50% |
| older pooled (1131 covered days of 1131) | +257 | +105 | -145% | +85% | +64% |

Windows, pick (tick_300) vs live bar (tm600), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +2167 | +697 | 4212 | 2189 | 10189 | 6802 | 183 |
| L3M | +2193 | +329 | 4630 | 2748 | 10189 | 6802 | 91 |
| HOLD 2025-11..2026-04 | +176 | -76 | 12190 | 5616 | 19602 | 12127 | 181 |
| 2023-04..12 | -63 | -3 | 4742 | 3452 | 8178 | 6330 | 266 |
| 2024 | +27 | +128 | 4801 | 1693 | 10562 | 4460 | 366 |
| 2025 | +235 | +161 | 7168 | 4731 | 19907 | 8669 | 365 |
| all | +523 | +187 | 7668 | 4278 | 19907 | 12127 | 1314 |
White RC (best of 227 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.808

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +1 | +264 | 11947 | 3047 | 38% | 38% | 17% | +3/+1130 | +225/+3123 | +2811/+5980 |
| 3M->1M | 38 | +79 | +234 | 10645 | 3046 | 45% | 55% | 19% | +338/+1001 | +329/+2994 | +2705/+5757 |
| 12M->1M | 31 | +20 | +280 | 18187 | 3657 | 35% | 42% | 43% | +88/+1202 | +4065/+3377 | +8258/+6497 |
| 6M->2wk | 80 | -132 | +253 | 25494 | 3738 | 35% | 42% | 38% | -226/+1223 | +73/+2893 | +2500/+5807 |
| 6M->3M | 12 | -241 | +237 | 26388 | 2652 | 42% | 33% | 0% | -1818/+1084 | -3099/+3048 | +1762/+5983 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS -144 USD/wk, share >0 51%; best random-clock row L6M +1414 USD/wk (median +266) vs best real row +2167

## Engine swap test (exact engine, full JL3 stack; swap ON vs JL3 today)

Identity (JL3 = 202610 691 trades 37,159.82; 202504 637 / 41,239.76):

| set | mode | month | JL3 trades / net | swap trades / net | result |
|---|---|---|---|---|---|
| TL3_SWA_ID0 | inert | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID2 | K7 replay of the native attempt | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID2 | K7 replay of the native attempt | 202504 | 637 / 41239.76 | 637 / 41239.76 | IDENTICAL |
| TL3_SWA_ID3 | K7 own live 3-min bar signals injected (+0.245 ms ts_recv offset) | 202610 | 691 / 37159.82 | 690 / 36173.82 | differs |
| TL3_SWA_ID3 | K7 own live 3-min bar signals injected (+0.245 ms ts_recv offset) | 202504 | 637 / 41239.76 | 638 / 43355.58 | differs |
| TL3_SWA_ID2U7 | U7 replay | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID2U7 | U7 replay | 202504 | 637 / 41239.76 | 637 / 41239.76 | IDENTICAL |
| TL3_SWA_ID3U7 | U7 own live 10-min signals | 202610 | 691 / 37159.82 | 683 / 32154.70 | differs |
| TL3_SWA_ID3U7 | U7 own live 10-min signals | 202504 | 637 / 41239.76 | 637 / 41673.58 | differs |

