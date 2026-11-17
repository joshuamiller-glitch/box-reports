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
| 2023 | +0 | -332 | -100% | -100% | -100% |
| 2024 | -114 | +1068 | +111% | -74% | -33% |
| 2025 | -46 | -556 | -92% | -10% | -6% |
| 2026 | -2206 | -2680 | -18% | +12% | +5% |
| older pooled (926 covered days of 1131) | -383 | -207 | +85% | -24% | -28% |
White RC (best of 252 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.923

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -278 | -448 | 44571 | 56579 | 41% | 49% | 36% | -1190/-1919 | -1871/-5091 | -1852/-10326 |
| 3M->1M | 38 | -775 | -423 | 62326 | 56701 | 29% | 50% | 5% | -3321/-1813 | -5128/-4871 | -6279/-9745 |
| 12M->1M | 31 | +113 | -538 | 17563 | 59848 | 52% | 45% | 47% | +486/-2307 | +1688/-7414 | +2149/-15444 |
| 6M->2wk | 80 | -110 | -444 | 54972 | 57221 | 40% | 49% | 46% | -2035/-1549 | -2602/-4877 | -4329/-10154 |
| 6M->3M | 12 | -120 | -428 | 21071 | 50930 | 50% | 42% | 18% | -2532/-1940 | -1546/-5509 | -3058/-10650 |

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
| 2023 | +0 | +127 | +100% | -100% | -100% |
| 2024 | +0 | -1091 | -100% | -100% | -100% |
| 2025 | -315 | -279 | +13% | -8% | -24% |
| 2026 | -476 | -231 | +106% | -30% | -43% |
| older pooled (926 covered days of 1131) | -193 | -566 | -66% | -78% | -65% |
White RC (best of 210 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.354

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -542 | -638 | 58259 | 64390 | 35% | 35% | 50% | -2324/-2735 | -5466/-7972 | -10231/-15122 |
| 3M->1M | 38 | -601 | -671 | 63701 | 69257 | 37% | 39% | 30% | -2575/-2876 | -6284/-8037 | -8861/-15201 |
| 12M->1M | 31 | -346 | -540 | 40900 | 42599 | 45% | 39% | 60% | -1482/-2316 | -4779/-6918 | -8738/-12509 |
| 6M->2wk | 80 | -473 | -628 | 58588 | 64369 | 32% | 39% | 62% | -2138/-2976 | -5441/-8119 | -9455/-14820 |
| 6M->3M | 12 | -467 | -588 | 68137 | 64971 | 33% | 33% | 18% | -2051/-3724 | -6000/-7555 | -13879/-15660 |

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
White RC (best of 239 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.217

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -192 | -277 | 23309 | 19336 | 32% | 46% | 36% | -824/-1187 | -916/-3360 | +1619/-6662 |
| 3M->1M | 38 | -315 | -273 | 30011 | 21304 | 37% | 42% | 30% | -1352/-1170 | -3995/-3363 | -4759/-6656 |
| 12M->1M | 31 | -215 | -217 | 17060 | 18806 | 32% | 42% | 57% | -921/-928 | -812/-2646 | +1967/-5208 |
| 6M->2wk | 80 | -327 | -274 | 29335 | 21751 | 30% | 38% | 52% | -1858/-1468 | -3047/-3496 | -2828/-6607 |
| 6M->3M | 12 | +27 | -296 | 12188 | 19845 | 58% | 75% | 18% | +1335/-249 | +346/-3805 | +2820/-7329 |

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
| 2023 | +0 | -1576 | -100% | -100% | -100% |
| 2024 | +6 | +448 | +99% | -92% | -69% |
| 2025 | -377 | -300 | +25% | -3% | -7% |
| 2026 | -2989 | -827 | +262% | +108% | +58% |
| older pooled (987 covered days of 1131) | -543 | -252 | +115% | -15% | +18% |
White RC (best of 249 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.965

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -292 | -203 | 26907 | 29415 | 41% | 41% | 17% | -1251/-870 | -4788/-2186 | -10034/-4072 |
| 3M->1M | 38 | +115 | -198 | 22516 | 33438 | 50% | 61% | 24% | +494/-850 | -5682/-2095 | -16631/-3861 |
| 12M->1M | 31 | -791 | -223 | 68025 | 37946 | 29% | 32% | 47% | -3391/-958 | -9176/-3657 | -17778/-8985 |
| 6M->2wk | 80 | -96 | -201 | 30538 | 36018 | 42% | 44% | 44% | -1676/-1029 | -7188/-2370 | -15191/-4098 |
| 6M->3M | 12 | -30 | -183 | 23312 | 25449 | 42% | 33% | 18% | +1881/+2363 | -389/-2347 | -1037/-3848 |

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
| 2023 | +0 | -764 | -100% | -100% | -100% |
| 2024 | +20 | +114 | +82% | -92% | -73% |
| 2025 | -544 | +394 | +238% | -7% | -15% |
| 2026 | +209 | +156 | -33% | -34% | -34% |
| older pooled (987 covered days of 1131) | -165 | +115 | +244% | -33% | -15% |
White RC (best of 237 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.905

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -521 | +23 | 39775 | 19749 | 30% | 32% | 39% | -2232/+99 | -5200/+962 | -9389/+2819 |
| 3M->1M | 38 | -63 | +30 | 21532 | 18952 | 34% | 42% | 30% | -271/+128 | -1401/+1051 | -2040/+2907 |
| 12M->1M | 31 | -822 | +249 | 66292 | 17890 | 23% | 26% | 37% | -3521/+1069 | -4897/+2875 | -5268/+5842 |
| 6M->2wk | 80 | -443 | +39 | 41799 | 22052 | 31% | 40% | 52% | -1046/+562 | -4434/+1364 | -10757/+3193 |
| 6M->3M | 12 | -319 | +74 | 32402 | 18051 | 33% | 42% | 27% | -1143/+585 | -4106/+951 | -10175/+2310 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS -364 USD/wk, share >0 35%; best random-clock row L6M +536 USD/wk (median -119) vs best real row +663

## U7 london (reference live bar tm600)

Reference tm600: L6M -222 USD/wk (net, 1 lot), L3M -878, L12M -13, trades L6M 133

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | vsess_450 | +1441 | 148 | +1633 | pass |
| 2 | dib_240 | +1328 | 812 | +1943 | no |
| 3 | vsess_600 | +1001 | 161 | +1572 | pass |
| 4 | tib_700 | +958 | 645 | +1277 | no |
| 5 | kagi_10 | +860 | 533 | +700 | no |
| 6 | dchg_10 | +860 | 533 | +700 | no |
| 7 | vrb_240 | +858 | 657 | +2694 | pass |
| 8 | tib_1200 | +855 | 552 | +1159 | pass |

PICK (trailing 6M to 2026-11-13): **vsess_450**. Trailing-3M pick: vrb_240 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | +0 | -402 | -100% | -100% | -100% |
| 2024 | -282 | -147 | +92% | -64% | -20% |
| 2025 | -301 | -133 | +127% | +63% | +77% |
| 2026 | -1376 | +170 | +910% | +684% | +334% |
| older pooled (987 covered days of 1131) | -403 | -130 | +209% | +24% | +96% |
White RC (best of 205 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.568

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -423 | -131 | 37801 | 17948 | 30% | 38% | 28% | -1812/-560 | -4460/-1523 | -7022/-3317 |
| 3M->1M | 38 | -503 | -160 | 51315 | 18938 | 39% | 39% | 22% | -2154/-687 | -5554/-1684 | -6157/-3423 |
| 12M->1M | 31 | -289 | -124 | 18643 | 13859 | 39% | 45% | 47% | -1241/-531 | -4777/-1523 | -10791/-3086 |
| 6M->2wk | 80 | -95 | -160 | 24105 | 18001 | 40% | 49% | 49% | -999/-680 | -3380/-1365 | -5745/-3352 |
| 6M->3M | 12 | -119 | -81 | 26401 | 15983 | 33% | 50% | 18% | -3050/-155 | -1530/-1046 | -3373/-2564 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS +36 USD/wk, share >0 54%; best random-clock row L6M +464 USD/wk (median -374) vs best real row +1441

## K7 asia (reference live bar tm180)

Reference tm180: L6M +623 USD/wk (net, 1 lot), L3M +193, L12M -120, trades L6M 573

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | vrb_700 | +3211 | 700 | +1329 | no |
| 2 | dol_500 | +2299 | 713 | +93 | pass |
| 3 | kagi_14 | +2273 | 1093 | +2332 | pass |
| 4 | dchg_14 | +2273 | 1093 | +2332 | pass |
| 5 | pnf_5 | +2189 | 1045 | +1208 | pass |
| 6 | tm600 | +2183 | 386 | +2502 | pass |
| 7 | wrenko_20 | +2149 | 694 | +2292 | pass |
| 8 | tm240 | +2114 | 638 | +2318 | pass |

PICK (trailing 6M to 2026-11-13): **dol_500**. Trailing-3M pick: tm600 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | +0 | +429 | +100% | -100% | -100% |
| 2024 | +0 | -37 | -100% | -100% | -100% |
| 2025 | -107 | -485 | -78% | +19% | +8% |
| 2026 | -165 | +308 | +154% | +1% | -11% |
| older pooled (1018 covered days of 1131) | -60 | -82 | -27% | -12% | -4% |
White RC (best of 244 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.461

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +355 | +9 | 16373 | 18532 | 59% | 62% | 36% | +1522/+36 | +4245/-146 | +10535/-170 |
| 3M->1M | 38 | +36 | +13 | 9414 | 20550 | 50% | 61% | 16% | +153/+54 | +1017/-90 | +157/-212 |
| 12M->1M | 31 | +375 | -42 | 11220 | 21021 | 65% | 58% | 53% | +1607/-180 | +3511/-771 | +2258/-2379 |
| 6M->2wk | 80 | +338 | +8 | 9896 | 21126 | 57% | 61% | 58% | +1025/-252 | +4960/-498 | +7787/-629 |
| 6M->3M | 12 | +403 | -2 | 3517 | 18765 | 58% | 75% | 18% | +784/+1219 | +5175/-28 | +11560/-290 |

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
White RC (best of 225 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.847

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +439 | +652 | 9432 | 8791 | 32% | 65% | 44% | +1882/+2794 | +5615/+8040 | +8277/+15319 |
| 3M->1M | 38 | +343 | +651 | 6299 | 5021 | 45% | 66% | 19% | +1469/+2792 | +3163/+7987 | +6180/+15113 |
| 12M->1M | 31 | +521 | +582 | 8405 | 9883 | 39% | 61% | 57% | +2233/+2496 | +6659/+7415 | +9128/+14185 |
| 6M->2wk | 80 | +567 | +646 | 7000 | 8056 | 44% | 65% | 59% | +2066/+2752 | +5570/+7814 | +8361/+14900 |
| 6M->3M | 12 | +183 | +545 | 17776 | 7062 | 25% | 58% | 0% | +2189/+498 | +2357/+7001 | +5973/+14663 |

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
| 2023 | +0 | +167 | +100% | -100% | -100% |
| 2024 | +24 | +128 | +81% | -82% | -51% |
| 2025 | +235 | +161 | -46% | +52% | +130% |
| 2026 | +1579 | +104 | -1419% | +20% | +50% |
| older pooled (1018 covered days of 1131) | +301 | +142 | -111% | +32% | +64% |
White RC (best of 227 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.808

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +37 | +264 | 11625 | 3047 | 27% | 49% | 33% | +158/+1130 | +988/+3123 | +4323/+5980 |
| 3M->1M | 38 | +76 | +234 | 16451 | 3046 | 39% | 53% | 30% | +327/+1001 | -306/+2994 | +2549/+5757 |
| 12M->1M | 31 | -99 | +280 | 32108 | 3657 | 23% | 45% | 43% | -423/+1202 | +2773/+3377 | +5908/+6497 |
| 6M->2wk | 80 | -93 | +253 | 24450 | 3738 | 21% | 46% | 46% | -223/+1223 | +895/+2893 | +4811/+5807 |
| 6M->3M | 12 | -101 | +237 | 21932 | 2652 | 33% | 50% | 9% | -759/+1084 | -1304/+3048 | +4273/+5983 |

Null (random-clock rows, 30, same procedure 6M->1M): OOS -144 USD/wk, share >0 51%; best random-clock row L6M +1414 USD/wk (median +266) vs best real row +2167

## Engine swap test (exact engine, full JL3 stack; swap ON vs JL3 today)

Identity (JL3 = 202610 691 trades 37,159.82; 202504 637 / 41,239.76):

| set | mode | month | JL3 trades / net | swap trades / net | result |
|---|---|---|---|---|---|
| TL3_SWA_ID0 | inert | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID2 | replay of the native attempt | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID3 | own live 3-min bar signals injected (+0.245 ms ts_recv offset) | 202610 | 691 / 37159.82 | 690 / 36173.82 | differs |

