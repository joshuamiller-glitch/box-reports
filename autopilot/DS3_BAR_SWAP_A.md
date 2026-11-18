# DS3 BAR SWAP A (W-SWA): K7 / M7 / U7 book signal on other bars, per weak session

Header: trials counted = 1329 bar rows x 3 books x up to 9 cells (screen of 443 rows x 9 cells); correction = White reality check per cell (p reported) + neighbour agreement; selection = trailing-6M pick (in-sample for the pick window), validation = rolling walk-forward (out-of-sample), older years = tolerant AMBER/RED check; data end 2026-11-13.

1. Tried: the exact K7 (Keltner break), M7 (momentum vote) and U7 (Supertrend) signal on 443 bar rows (own epoch time bars + W-BAR event/price bars), standalone raw chassis, live 60/60 bracket, tape fills, flat at session end.
2. Holds: 0 of 6 weak cells have a gated trailing-6M pick that is not RED in older years: none.
3. Does not hold: K7 nyam (RED); M7 london (RED); K7 london (RED); K7 nypm (RED); M7 nyam (RED); U7 london (RED).
4. Needs in DS7: a custom BarsType per pick that is not Tick/Volume/Range/Renko/Minute (rule text in the rows); alt-bar slots X1-X8 are OFF today, so each swap is new wiring; nothing changes live.
5. Next: engine swap test (hook, identity first) for each non-RED pick, random-clock nulls, per-book parameter grid on the picked bar, Asia phase 2. Pick rule: trailing 6M to 2026-11-13 (3M beside), validated by rolling walk-forward.

## Input sources per book (which inputs read the NEW bar, which still read TIME bars or the clock) - from DS7 v2.0 source (DS7.cs), not re-audited line by line
| book | input | source today | after a bar swap (transplanted) | bar-native version (this page) |
|---|---|---|---|---|
| K7 | signal: EMA14 + ATR10 x 1.0 Keltner break | 3-min time bar (BIP1) | NEW bar (same numbers, so the band is a different thing on event/price bars) | NEW bar: band = m x realised vol per bar of THIS series (price bars: = bricks), lookback in bars or clock minutes, optional speed filter |
| K7 | entry fill | clock (bar close + about 1 s) | clock | clock |
| K7 | bracket 60/60 (points), day caps (USD), stack cap (count), give-back lock | points / USD / count | unchanged (no bar) | unchanged |
| K7 | session lots / session filter | clock (ET sessions) | clock | clock |
| K7 | trend-sizer ER ladder (ER(20) of 5-min closes) | 5-min TIME bar (AddDataSeries 5) | stays on 5-min time bars unless recomputed | stays (version B recomputes on the picked bar) |
| K7 | signal-state ss_size (St1Dist etc., Shadow/Live per book) | 1-min / time bar features | stays | stays |
| K7 | trade-health loss-side cut (C1-C3 conditions, adverse-points eligibility) | 1-min structure, points | stays | stays |
| K7 | flat -45 cut (EC_FLAT45K), OTE max 60 min, context-cut fresh gap 30 min, post-exit blackout | CLOCK minutes | clock | clock |
| K7 | L2 gate (depth dip) | book events | unchanged | unchanged |
| M7 | signal: z-scores of 15/30/60/120/240 BARS, sigma from the last max(L,120) bar diffs, vote 4-of-5 | 1-min time bar | NEW bar, lookbacks in BARS (so 15 bars = 15 clock minutes only on the 1-min bar) | NEW bar, lookbacks in CLOCK minutes (searchsorted on bar times), z by realised variance inside the window |
| M7 | London cap (3 closed trades), against-the-day target | count / points | unchanged | unchanged |
| U7 | signal: Supertrend ATR7 x 3.0 on median price | 10-min time bar (BIP3) | NEW bar | NEW bar: band = M x realised vol per bar of THIS series, lookback bars or clock |
| U7 | trade-health loss+profit cut, ThL2 blackout 30 min, NKD near-zone take (NKD top of book) | points / clock / another instrument | stays | stays |
| all | day-done (22 closes and day <= -4,200 USD), JN04 stack cap (London same-side 6) | counts / USD | unchanged | unchanged |
Layers that still read TIME bars (stay on time bars in the engine version A; version B recomputes them on the picked bar only where meaningful, see the engine section): trend-sizer ER ladder (5-min), signal-state / context features (1-min), trade-health conditions, ATR-based regime tags (P7 only, 5-min ATR from 1-min bars).


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
White RC (best of 289 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.926

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -747 | -448 | 63054 | 56579 | 51% | 32% | 22% | -3202/-1919 | -6328/-5091 | -9855/-10326 |
| 3M->1M | 38 | -680 | -423 | 53265 | 56701 | 42% | 45% | 3% | -2916/-1813 | -8284/-4871 | -12828/-9745 |
| 12M->1M | 31 | -483 | -538 | 47363 | 59848 | 55% | 26% | 47% | -2072/-2307 | -988/-7414 | -1522/-15444 |
| 6M->2wk | 80 | -861 | -444 | 91146 | 57221 | 46% | 34% | 38% | -3779/-1549 | -4957/-4877 | -11184/-10154 |
| 6M->3M | 12 | -240 | -428 | 22285 | 50930 | 67% | 33% | 0% | -2852/-1940 | -3092/-5509 | -6635/-10650 |

Null (random-clock rows, 150, same procedure 6M->1M): OOS +74 USD/wk, share >0 57%; best random-clock row L6M +1086 USD/wk (median -618) vs best real row +725

## M7 london (reference live bar tm60)

Reference tm60: L6M -923 USD/wk (net, 1 lot), L3M -1137, L12M -623, trades L6M 536

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | lbrk_5_20 | +782 | 118 | +508 | no |
| 2 | tm600 | +720 | 118 | +1172 | no |
| 3 | tm1200 | +709 | 83 | +433 | no |
| 4 | lbrk_3_40 | +544 | 62 | +1297 | no |
| 5 | dol_750 | +526 | 245 | +863 | no |
| 6 | tib_40000 | +492 | 34 | +403 | no |
| 7 | mrenko_40 | +486 | 110 | +126 | pass |
| 8 | lbrk_5_10 | +439 | 257 | -385 | pass |

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
White RC (best of 233 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.358

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -536 | -638 | 53698 | 64390 | 43% | 32% | 19% | -2297/-2735 | -3402/-7972 | -5544/-15122 |
| 3M->1M | 38 | -358 | -671 | 30113 | 69257 | 53% | 42% | 5% | -1532/-2876 | -3972/-8037 | -8094/-15201 |
| 12M->1M | 31 | -356 | -540 | 41686 | 42599 | 39% | 42% | 63% | -1527/-2316 | -1821/-6918 | -4154/-12509 |
| 6M->2wk | 80 | -362 | -628 | 44990 | 64369 | 41% | 40% | 51% | -1857/-2976 | -4112/-8119 | -6763/-14820 |
| 6M->3M | 12 | -229 | -588 | 38448 | 64971 | 58% | 50% | 9% | -682/-3724 | -2942/-7555 | -7962/-15660 |

Null (random-clock rows, 150, same procedure 6M->1M): OOS -344 USD/wk, share >0 43%; best random-clock row L6M +1455 USD/wk (median +77) vs best real row +782

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
White RC (best of 268 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.217

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -420 | -277 | 46628 | 19336 | 43% | 43% | 25% | -1801/-1187 | -3645/-3360 | -3315/-6662 |
| 3M->1M | 38 | -355 | -273 | 37323 | 21304 | 47% | 37% | 16% | -1521/-1170 | -6988/-3363 | -9885/-6656 |
| 12M->1M | 31 | -254 | -217 | 18059 | 18806 | 45% | 26% | 37% | -1090/-928 | -1626/-2646 | -1517/-5208 |
| 6M->2wk | 80 | -177 | -274 | 26024 | 21751 | 45% | 41% | 49% | -2016/-1468 | -4485/-3496 | -5311/-6607 |
| 6M->3M | 12 | -302 | -296 | 41603 | 19845 | 58% | 50% | 0% | -3283/-249 | -3884/-3805 | -6486/-7329 |

Null (random-clock rows, 150, same procedure 6M->1M): OOS +32 USD/wk, share >0 41%; best random-clock row L6M +1704 USD/wk (median -331) vs best real row +2034

## K7 nypm (reference live bar tm180)

Reference tm180: L6M -397 USD/wk (net, 1 lot), L3M -679, L12M -772, trades L6M 398

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | dib_40000 | +1576 | 384 | +1898 | no |
| 2 | tib_40000 | +861 | 237 | +601 | no |
| 3 | tsf_10_60 | +701 | 126 | +0 | no |
| 4 | drb_6000 | +624 | 205 | -522 | no |
| 5 | tm1800 | +603 | 65 | +222 | no |
| 6 | trb_2000 | +556 | 519 | -1046 | no |
| 7 | pnf_56 | +482 | 45 | +254 | no |
| 8 | vib_25000 | +468 | 573 | -372 | no |

PICK (trailing 6M to 2026-11-13): **dib_70000**. Trailing-3M pick: dib_70000.
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -524 | -726 | -28% | -23% | -11% |
| 2024 | +159 | +448 | +65% | -1% | -6% |
| 2025 | +67 | -300 | -122% | -34% | -31% |
| 2026 | -666 | -827 | -19% | -22% | -24% |
| older pooled (1131 covered days of 1131) | -129 | -221 | -41% | -31% | -46% |

Windows, pick (dib_70000) vs live bar (tm180), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +421 | -397 | 6284 | 13938 | 15817 | 24062 | 183 |
| L3M | +560 | -679 | 2033 | 10285 | 5990 | 15220 | 91 |
| HOLD 2025-11..2026-04 | +75 | -1191 | 13586 | 25119 | 31833 | 52445 | 181 |
| 2023-04..12 | -524 | -726 | 12100 | 15784 | 28863 | 32276 | 266 |
| 2024 | +159 | +448 | 12618 | 12792 | 26333 | 28089 | 366 |
| 2025 | +67 | -300 | 11940 | 18187 | 23059 | 33432 | 365 |
| all | -53 | -245 | 21630 | 36371 | 42147 | 78181 | 1314 |
White RC (best of 283 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.757

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -136 | -203 | 24235 | 29415 | 46% | 49% | 25% | -582/-870 | -2386/-2186 | -8486/-4072 |
| 3M->1M | 38 | +20 | -198 | 25492 | 33438 | 53% | 58% | 11% | +84/-850 | -5700/-2095 | -15903/-3861 |
| 12M->1M | 31 | -201 | -223 | 27396 | 37946 | 52% | 52% | 47% | -862/-958 | -4307/-3657 | -12853/-8985 |
| 6M->2wk | 80 | -385 | -201 | 64463 | 36018 | 51% | 46% | 42% | -1611/-1029 | -5339/-2370 | -14183/-4098 |
| 6M->3M | 12 | +30 | -183 | 15239 | 25449 | 50% | 50% | 9% | +2204/+2363 | +391/-2347 | -26/-3848 |

Null (random-clock rows, 150, same procedure 6M->1M): OOS -700 USD/wk, share >0 35%; best random-clock row L6M +618 USD/wk (median -553) vs best real row +1576

## M7 nyam (reference live bar tm60)

Reference tm60: L6M -512 USD/wk (net, 1 lot), L3M -1456, L12M -480, trades L6M 468

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tsf_10_120 | +663 | 53 | +720 | no |
| 2 | trb_15000 | +642 | 65 | +461 | no |
| 3 | vsess_50 | +597 | 80 | +981 | no |
| 4 | tm1200 | +477 | 64 | +416 | no |
| 5 | mrenko_112 | +453 | 31 | +180 | no |
| 6 | trb_40000 | +445 | 17 | +238 | no |
| 7 | tick_2000 | +441 | 269 | +64 | no |
| 8 | tib_40000 | +426 | 181 | -18 | no |

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
White RC (best of 269 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.908

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -503 | +23 | 36765 | 19749 | 35% | 27% | 19% | -2157/+99 | -7120/+962 | -10741/+2819 |
| 3M->1M | 38 | -125 | +30 | 23669 | 18952 | 47% | 39% | 8% | -537/+128 | -1389/+1051 | -3404/+2907 |
| 12M->1M | 31 | -616 | +249 | 45499 | 17890 | 39% | 42% | 23% | -2641/+1069 | -5071/+2875 | -9330/+5842 |
| 6M->2wk | 80 | -835 | +39 | 82854 | 22052 | 39% | 30% | 37% | -2767/+562 | -7403/+1364 | -13743/+3193 |
| 6M->3M | 12 | -757 | +74 | 74396 | 18051 | 17% | 17% | 9% | -2785/+585 | -9727/+951 | -12636/+2310 |

Null (random-clock rows, 150, same procedure 6M->1M): OOS -283 USD/wk, share >0 46%; best random-clock row L6M +660 USD/wk (median -195) vs best real row +663

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
White RC (best of 226 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.570

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -454 | -131 | 33719 | 17948 | 41% | 30% | 22% | -1946/-560 | -2596/-1523 | -3842/-3317 |
| 3M->1M | 38 | -337 | -160 | 40380 | 18938 | 50% | 39% | 19% | -1445/-687 | -4888/-1684 | -5153/-3423 |
| 12M->1M | 31 | -223 | -124 | 22645 | 13859 | 42% | 35% | 50% | -954/-531 | -4738/-1523 | -11772/-3086 |
| 6M->2wk | 80 | -262 | -160 | 33559 | 18001 | 46% | 42% | 41% | -1174/-680 | -1438/-1365 | -3356/-3352 |
| 6M->3M | 12 | +138 | -81 | 11424 | 15983 | 58% | 58% | 27% | -2056/-155 | +1776/-1046 | +1177/-2564 |

Null (random-clock rows, 150, same procedure 6M->1M): OOS -161 USD/wk, share >0 35%; best random-clock row L6M +783 USD/wk (median -366) vs best real row +1441

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
| 8 | trend_20 | +2149 | 694 | +2292 | pass |

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
White RC (best of 277 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.464

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +665 | +9 | 6546 | 18532 | 73% | 59% | 36% | +2851/+36 | +6009/-146 | +10966/-170 |
| 3M->1M | 38 | +86 | +13 | 27660 | 20550 | 53% | 55% | 14% | +367/+54 | +2879/-90 | +2295/-212 |
| 12M->1M | 31 | +509 | -42 | 11494 | 21021 | 71% | 45% | 37% | +2180/-180 | +1940/-771 | -2419/-2379 |
| 6M->2wk | 80 | +385 | +8 | 20163 | 21126 | 61% | 64% | 58% | +1620/-252 | +5599/-498 | +6792/-629 |
| 6M->3M | 12 | +485 | -2 | 3089 | 18765 | 67% | 75% | 18% | +2695/+1219 | +6235/-28 | +12090/-290 |

Null (random-clock rows, 150, same procedure 6M->1M): OOS +332 USD/wk, share >0 59%; best random-clock row L6M +3102 USD/wk (median +953) vs best real row +3211

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
White RC (best of 249 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.847

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +295 | +652 | 9256 | 8791 | 27% | 51% | 25% | +1265/+2794 | +3772/+8040 | +4765/+15319 |
| 3M->1M | 38 | +397 | +651 | 7901 | 5021 | 47% | 66% | 16% | +1703/+2792 | +2725/+7987 | +5390/+15113 |
| 12M->1M | 31 | +603 | +582 | 7446 | 9883 | 45% | 52% | 50% | +2585/+2496 | +6833/+7415 | +9717/+14185 |
| 6M->2wk | 80 | +412 | +646 | 10011 | 8056 | 42% | 60% | 46% | +1261/+2752 | +4165/+7814 | +5963/+14900 |
| 6M->3M | 12 | +128 | +545 | 17910 | 7062 | 33% | 42% | 0% | +2486/+498 | +1647/+7001 | +3616/+14663 |

Null (random-clock rows, 150, same procedure 6M->1M): OOS +333 USD/wk, share >0 54%; best random-clock row L6M +2332 USD/wk (median +667) vs best real row +2368

## U7 asia (reference live bar tm600)

Reference tm600: L6M +697 USD/wk (net, 1 lot), L3M +329, L12M +309, trades L6M 153

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | tick_300 | +2167 | 415 | +2193 | pass |
| 2 | dol_500 | +2161 | 376 | +2205 | pass |
| 3 | wrenko_10 | +2051 | 702 | +444 | pass |
| 4 | trend_10 | +2051 | 702 | +444 | pass |
| 5 | mrenko_14 | +2038 | 709 | +1753 | no |
| 6 | vnorm_1500 | +1996 | 479 | +1664 | pass |
| 7 | drb_400 | +1878 | 545 | +556 | no |
| 8 | vol_350 | +1820 | 502 | +285 | pass |

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
White RC (best of 252 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.809

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +55 | +264 | 9299 | 3047 | 43% | 43% | 17% | +235/+1130 | -817/+3123 | +2841/+5980 |
| 3M->1M | 38 | +70 | +234 | 10660 | 3046 | 42% | 55% | 14% | +302/+1001 | +327/+2994 | +2980/+5757 |
| 12M->1M | 31 | +20 | +280 | 18187 | 3657 | 35% | 42% | 43% | +88/+1202 | +4084/+3377 | +8277/+6497 |
| 6M->2wk | 80 | -165 | +253 | 29522 | 3738 | 34% | 38% | 32% | -187/+1223 | -253/+2893 | +1750/+5807 |
| 6M->3M | 12 | -208 | +237 | 23245 | 2652 | 50% | 42% | 0% | -1570/+1084 | -2678/+3048 | +1780/+5983 |

Null (random-clock rows, 150, same procedure 6M->1M): OOS +155 USD/wk, share >0 70%; best random-clock row L6M +1414 USD/wk (median +163) vs best real row +2167

## Parameter-grid re-fit on the bar (walk-forward, trailing 6M; best 20 rows per cell x grid)

Prereg line in DECISIONS.md. Candidates = (row, parameter combo); pick = trailing-6M best total with n>=30 (no neighbour gate on params: grid points are not ordered rows; the row-level neighbour gate stays on the page above). Reference = live book on its live bar. Shifted-window control = same rolling pick but the pick window ends 11/23/37 days earlier (stale pick); if stale picks do as well as the fresh pick the procedure is not capturing recent structure.


### K7 nyam (ref tm180@e14a10m1, 21 rows x 27 combos)

| procedure | periods | OOS USD/wk | live-bar ref USD/wk | OOS ulcer | ref ulcer | share beat ref | share >0 |
|---|---|---|---|---|---|---|---|
| rows only (default params), fresh pick | 37 | -703 | -542 | 57250 | 57458 | 46% | 38% |
| GRID re-fit, fresh pick | 37 | -703 | -542 | 42447 | 57458 | 43% | 46% |
| GRID re-fit, stale 11 d | 37 | -982 | -536 | 73142 | 55682 | 38% | 41% |
| GRID re-fit, stale 23 d | 36 | -1324 | -507 | 96121 | 55556 | 39% | 28% |
| GRID re-fit, stale 37 d | 36 | -932 | -529 | 66394 | 54762 | 39% | 42% |

Current trailing-6M grid pick: **renko_14@e14a14m0.75** L6M +1054 USD/wk (1358 trades) vs live-bar ref -2038.

### M7 london (ref tm60@t0.5v4s1, 21 rows x 27 combos)

| procedure | periods | OOS USD/wk | live-bar ref USD/wk | OOS ulcer | ref ulcer | share beat ref | share >0 |
|---|---|---|---|---|---|---|---|
| rows only (default params), fresh pick | 37 | -68 | -609 | 14770 | 63352 | 73% | 46% |
| GRID re-fit, fresh pick | 37 | -479 | -609 | 38108 | 63352 | 54% | 41% |
| GRID re-fit, stale 11 d | 37 | -261 | -587 | 28768 | 62365 | 51% | 38% |
| GRID re-fit, stale 23 d | 36 | -71 | -531 | 24369 | 59045 | 61% | 42% |
| GRID re-fit, stale 37 d | 36 | +140 | -566 | 12874 | 60567 | 69% | 42% |

Current trailing-6M grid pick: **lbrk_5_10@t0.35v3s1** L6M +1352 USD/wk (360 trades) vs live-bar ref -923.

### K7 london (ref tm180@e14a10m1, 21 rows x 27 combos)

| procedure | periods | OOS USD/wk | live-bar ref USD/wk | OOS ulcer | ref ulcer | share beat ref | share >0 |
|---|---|---|---|---|---|---|---|
| rows only (default params), fresh pick | 37 | -13 | -304 | 18803 | 19607 | 51% | 51% |
| GRID re-fit, fresh pick | 37 | -327 | -304 | 45733 | 19607 | 51% | 38% |
| GRID re-fit, stale 11 d | 37 | -553 | -313 | 53619 | 20851 | 43% | 22% |
| GRID re-fit, stale 23 d | 36 | -426 | -263 | 44799 | 18336 | 42% | 36% |
| GRID re-fit, stale 37 d | 36 | -85 | -304 | 34389 | 23127 | 47% | 39% |

Current trailing-6M grid pick: **urenko_14@e14a10m1** L6M +2034 USD/wk (745 trades) vs live-bar ref -1123.

### K7 nypm (ref tm180@e14a10m1, 21 rows x 27 combos)

| procedure | periods | OOS USD/wk | live-bar ref USD/wk | OOS ulcer | ref ulcer | share beat ref | share >0 |
|---|---|---|---|---|---|---|---|
| rows only (default params), fresh pick | 37 | -329 | -278 | 39721 | 31695 | 43% | 49% |
| GRID re-fit, fresh pick | 37 | -471 | -278 | 46248 | 31695 | 49% | 43% |
| GRID re-fit, stale 11 d | 37 | -704 | -235 | 53354 | 37883 | 43% | 27% |
| GRID re-fit, stale 23 d | 36 | -261 | -203 | 51357 | 32729 | 50% | 47% |
| GRID re-fit, stale 37 d | 36 | -434 | -259 | 58455 | 39668 | 56% | 36% |

Current trailing-6M grid pick: **dib_40000@e14a7m1** L6M +1998 USD/wk (376 trades) vs live-bar ref -641.

### M7 nyam (ref tm60@t0.5v4s1, 21 rows x 27 combos)

| procedure | periods | OOS USD/wk | live-bar ref USD/wk | OOS ulcer | ref ulcer | share beat ref | share >0 |
|---|---|---|---|---|---|---|---|
| rows only (default params), fresh pick | 37 | +241 | -15 | 14074 | 21011 | 46% | 57% |
| GRID re-fit, fresh pick | 37 | -288 | -15 | 29713 | 21011 | 43% | 43% |
| GRID re-fit, stale 11 d | 37 | -210 | +52 | 28137 | 17269 | 38% | 46% |
| GRID re-fit, stale 23 d | 36 | -320 | +102 | 23357 | 16443 | 36% | 44% |
| GRID re-fit, stale 37 d | 36 | -596 | +97 | 47860 | 17962 | 39% | 28% |

Current trailing-6M grid pick: **trb_10000@t0.35v4s1** L6M +1111 USD/wk (85 trades) vs live-bar ref -512.

### U7 london (ref tm600@a7m3, 21 rows x 9 combos)

| procedure | periods | OOS USD/wk | live-bar ref USD/wk | OOS ulcer | ref ulcer | share beat ref | share >0 |
|---|---|---|---|---|---|---|---|
| rows only (default params), fresh pick | 37 | +209 | -118 | 10904 | 17644 | 49% | 59% |
| GRID re-fit, fresh pick | 37 | -513 | -118 | 40207 | 17644 | 41% | 32% |
| GRID re-fit, stale 11 d | 37 | -260 | -124 | 28194 | 17277 | 54% | 41% |
| GRID re-fit, stale 23 d | 36 | -60 | -78 | 28659 | 18056 | 47% | 44% |
| GRID re-fit, stale 37 d | 36 | +40 | -97 | 35190 | 16491 | 50% | 50% |

Current trailing-6M grid pick: **lbrk_5_10@a5m4** L6M +1981 USD/wk (579 trades) vs live-bar ref -222.

## BAR-NATIVE versions (K7N / M7N / U7N) at native default parameters; pick rule and checks identical to the transplanted screen above

## K7 nyam (reference live bar tm180)

Reference tm180: L6M -1310 USD/wk (net, 1 lot), L3M -634, L12M -2081, trades L6M 426

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | cdr_600 | +494 | 294 | +1749 | no |
| 2 | drb_15000 | +352 | 128 | +264 | no |
| 3 | cdr_2500 | +280 | 34 | +291 | pass |
| 4 | dib_6000 | +153 | 1318 | -1794 | no |
| 5 | dol_500 | +85 | 1402 | -482 | no |
| 6 | drb_25000 | +63 | 82 | +266 | no |
| 7 | cdr_1600 | +26 | 69 | +68 | no |
| 8 | dchg_112 | +0 | 102 | +1143 | no |

PICK (trailing 6M to 2026-11-13): **cdr_2500**. Trailing-3M pick: dlt_600 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | +200 | +195 | -2% | -70% | -68% |
| 2024 | -313 | +1068 | +129% | +136% | +72% |
| 2025 | +134 | -556 | -124% | -90% | -90% |
| 2026 | -184 | -2680 | -93% | -91% | -91% |
| older pooled (1131 covered days of 1131) | -33 | -106 | -69% | -57% | -75% |

Windows, pick (cdr_2500) vs live bar (tm180), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +280 | -1310 | 1806 | 31475 | 3759 | 40318 | 183 |
| L3M | +291 | -634 | 1564 | 9608 | 2909 | 11345 | 91 |
| HOLD 2025-11..2026-04 | -104 | -2687 | 4992 | 45385 | 8053 | 80953 | 181 |
| 2023-04..12 | +200 | +195 | 3240 | 10845 | 7442 | 23530 | 266 |
| 2024 | -313 | +1068 | 11366 | 4811 | 22381 | 12978 | 366 |
| 2025 | +134 | -556 | 2734 | 26369 | 5167 | 49994 | 365 |
| all | +11 | -273 | 13795 | 56018 | 25739 | 137872 | 1314 |
White RC (best of 60 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.823

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -807 | -448 | 71779 | 56579 | 41% | 27% | 19% | -3458/-1919 | -2193/-5091 | -4199/-10326 |
| 3M->1M | 38 | -540 | -423 | 71567 | 56701 | 32% | 42% | 24% | -2316/-1813 | -5637/-4871 | -7338/-9745 |
| 12M->1M | 31 | -713 | -538 | 62162 | 59848 | 58% | 39% | 43% | -3056/-2307 | -6767/-7414 | -13341/-15444 |
| 6M->2wk | 80 | -457 | -444 | 45543 | 57221 | 44% | 38% | 41% | -2846/-1549 | -5562/-4877 | -5366/-10154 |
| 6M->3M | 12 | -158 | -428 | 39582 | 50930 | 58% | 50% | 9% | -6871/-1940 | -2034/-5509 | -3047/-10650 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## M7 london (reference live bar tm60)

Reference tm60: L6M -923 USD/wk (net, 1 lot), L3M -1137, L12M -623, trades L6M 536

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | dib_240 | +229 | 566 | -420 | no |
| 2 | cusum_112 | +185 | 17 | +470 | no |
| 3 | dchg_40 | +183 | 114 | -62 | no |
| 4 | dlt_250 | +135 | 60 | -198 | no |
| 5 | drb_1200 | +39 | 174 | +706 | no |
| 6 | dib_700 | +34 | 530 | -220 | no |
| 7 | dchg_80 | +7 | 6 | +92 | no |
| 8 | dchg_112 | +0 | 0 | +0 | no |

No row passes the gate in the trailing 6 months (n>=30, positive, neighbours positive): no swap pick; reference stays reference (BEST-AVAILABLE-NOT-PROVEN row shows best ungated).


PICK (trailing 6M to 2026-11-13): **dib_240** (ungated best, not a pick). Trailing-3M pick: dchg_10 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | +163 | +333 | +51% | +21% | +15% |
| 2024 | -825 | -1091 | -24% | -4% | -8% |
| 2025 | -161 | -279 | -42% | -22% | -24% |
| 2026 | -442 | -231 | +91% | +5% | +12% |
| older pooled (1131 covered days of 1131) | -333 | -392 | -15% | -15% | -21% |

Windows, pick (dib_240) vs live bar (tm60), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +229 | -923 | 15332 | 19014 | 25728 | 30647 | 183 |
| L3M | -420 | -1137 | 9676 | 12739 | 17816 | 21422 | 91 |
| HOLD 2025-11..2026-04 | -239 | -336 | 12106 | 14439 | 25408 | 25914 | 181 |
| 2023-04..12 | +163 | +333 | 7594 | 6285 | 16564 | 14421 | 266 |
| 2024 | -825 | -1091 | 36823 | 38388 | 58385 | 63453 | 366 |
| 2025 | -161 | -279 | 11223 | 14308 | 20919 | 27502 | 365 |
| all | -255 | -466 | 49637 | 63698 | 74659 | 110313 | 1314 |
White RC (best of 42 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.430

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -303 | -638 | 34042 | 64390 | 51% | 38% | 53% | -1298/-2735 | -3516/-7972 | -9355/-15122 |
| 3M->1M | 38 | -382 | -671 | 44339 | 69257 | 39% | 32% | 35% | -1637/-2876 | -5766/-8037 | -10551/-15201 |
| 12M->1M | 31 | -393 | -540 | 33896 | 42599 | 35% | 42% | 67% | -1684/-2316 | -3646/-6918 | -7604/-12509 |
| 6M->2wk | 80 | -413 | -628 | 39647 | 64369 | 36% | 39% | 61% | -1732/-2976 | -3944/-8119 | -9222/-14820 |
| 6M->3M | 12 | -173 | -588 | 31028 | 64971 | 50% | 33% | 18% | -943/-3724 | -2223/-7555 | -8531/-15660 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## K7 london (reference live bar tm180)

Reference tm180: L6M -856 USD/wk (net, 1 lot), L3M -392, L12M -740, trades L6M 485

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | dib_6000 | +1589 | 454 | +1683 | no |
| 2 | dib_10000 | +568 | 354 | +792 | no |
| 3 | dlt_150 | +530 | 282 | -65 | no |
| 4 | cusum_14 | +440 | 760 | +899 | no |
| 5 | cusum_56 | +393 | 366 | +121 | no |
| 6 | dchg_112 | +374 | 58 | +653 | no |
| 7 | drb_25000 | +210 | 16 | +539 | no |
| 8 | cdr_1600 | +209 | 13 | +320 | no |

No row passes the gate in the trailing 6 months (n>=30, positive, neighbours positive): no swap pick; reference stays reference (BEST-AVAILABLE-NOT-PROVEN row shows best ungated).


PICK (trailing 6M to 2026-11-13): **dib_6000** (ungated best, not a pick). Trailing-3M pick: dlt_30 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | +334 | +149 | -124% | -31% | -21% |
| 2024 | -488 | -233 | +109% | +3% | +11% |
| 2025 | +302 | +141 | -113% | -54% | -39% |
| 2026 | +449 | -786 | -157% | -47% | -51% |
| older pooled (1131 covered days of 1131) | +71 | -88 | -181% | +25% | +14% |

Windows, pick (dib_6000) vs live bar (tm180), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +1589 | -856 | 2638 | 22526 | 8938 | 38405 | 183 |
| L3M | +1683 | -392 | 2745 | 7831 | 8938 | 18037 | 91 |
| HOLD 2025-11..2026-04 | +464 | -411 | 7977 | 11685 | 15441 | 31313 | 181 |
| 2023-04..12 | +334 | +149 | 3843 | 5545 | 9856 | 12516 | 266 |
| 2024 | -488 | -233 | 17731 | 17170 | 34451 | 30932 | 366 |
| 2025 | +302 | +141 | 5330 | 11709 | 12679 | 20667 | 365 |
| all | +283 | -195 | 17591 | 22290 | 39192 | 63493 | 1314 |
White RC (best of 56 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.167

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -91 | -277 | 26883 | 19336 | 38% | 46% | 36% | -388/-1187 | -1813/-3360 | -2108/-6662 |
| 3M->1M | 38 | -251 | -273 | 20564 | 21304 | 42% | 45% | 16% | -1076/-1170 | -3416/-3363 | -5546/-6656 |
| 12M->1M | 31 | +185 | -217 | 25210 | 18806 | 45% | 55% | 53% | +792/-928 | -138/-2646 | +1677/-5208 |
| 6M->2wk | 80 | -58 | -274 | 29377 | 21751 | 49% | 49% | 58% | -292/-1468 | -1566/-3496 | -1420/-6607 |
| 6M->3M | 12 | -169 | -296 | 24689 | 19845 | 50% | 58% | 36% | +1205/-249 | -2171/-3805 | -756/-7329 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## K7 nypm (reference live bar tm180)

Reference tm180: L6M -397 USD/wk (net, 1 lot), L3M -679, L12M -772, trades L6M 398

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | dib_40000 | +448 | 341 | +1153 | no |
| 2 | cdr_400 | +396 | 320 | -543 | no |
| 3 | drb_40000 | +289 | 28 | +177 | no |
| 4 | cdr_600 | +225 | 185 | -895 | pass |
| 5 | dib_70000 | +196 | 216 | +537 | pass |
| 6 | cdr_1000 | +168 | 93 | -148 | no |
| 7 | dlt_150 | +102 | 621 | +305 | no |
| 8 | drb_25000 | +4 | 45 | -251 | no |

PICK (trailing 6M to 2026-11-13): **cdr_600**. Trailing-3M pick: dib_40000 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -391 | -726 | -46% | -35% | -47% |
| 2024 | +48 | +448 | +89% | -10% | -10% |
| 2025 | -84 | -300 | -72% | -17% | -9% |
| 2026 | -4 | -827 | -100% | -81% | -82% |
| older pooled (1131 covered days of 1131) | -104 | -221 | -53% | -41% | -53% |

Windows, pick (cdr_600) vs live bar (tm180), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +225 | -397 | 5841 | 13938 | 14641 | 24062 | 183 |
| L3M | -895 | -679 | 6590 | 10285 | 13157 | 15220 | 91 |
| HOLD 2025-11..2026-04 | -170 | -1191 | 10818 | 25119 | 18038 | 52445 | 181 |
| 2023-04..12 | -391 | -726 | 10248 | 15784 | 17144 | 32276 | 266 |
| 2024 | +48 | +448 | 11546 | 12792 | 25222 | 28089 | 366 |
| 2025 | -84 | -300 | 15017 | 18187 | 30572 | 33432 | 365 |
| all | -58 | -245 | 17179 | 36371 | 36415 | 78181 | 1314 |
White RC (best of 58 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.941

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -409 | -203 | 46410 | 29415 | 32% | 38% | 28% | -1755/-870 | -6195/-2186 | -17562/-4072 |
| 3M->1M | 38 | -400 | -198 | 61136 | 33438 | 34% | 42% | 24% | -1714/-850 | -3946/-2095 | -13420/-3861 |
| 12M->1M | 31 | -643 | -223 | 52670 | 37946 | 26% | 45% | 50% | -2754/-958 | -8271/-3657 | -18693/-8985 |
| 6M->2wk | 80 | -373 | -201 | 45662 | 36018 | 39% | 42% | 49% | -2040/-1029 | -3897/-2370 | -14380/-4098 |
| 6M->3M | 12 | -477 | -183 | 49987 | 25449 | 33% | 42% | 9% | -470/+2363 | -6137/-2347 | -21631/-3848 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## M7 nyam (reference live bar tm60)

Reference tm60: L6M -512 USD/wk (net, 1 lot), L3M -1456, L12M -480, trades L6M 468

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | cdr_1000 | +213 | 81 | +416 | no |
| 2 | cusum_112 | +204 | 190 | +210 | no |
| 3 | dchg_20 | +157 | 310 | -200 | no |
| 4 | dchg_112 | +94 | 39 | +19 | no |
| 5 | dol_4000 | -38 | 381 | -498 | no |
| 6 | cdr_2500 | -46 | 1 | +0 | no |
| 7 | drb_25000 | -46 | 1 | -93 | no |
| 8 | cusum_28 | -64 | 528 | -1058 | no |

No row passes the gate in the trailing 6 months (n>=30, positive, neighbours positive): no swap pick; reference stays reference (BEST-AVAILABLE-NOT-PROVEN row shows best ungated).


PICK (trailing 6M to 2026-11-13): **cdr_1000** (ungated best, not a pick). Trailing-3M pick: none.
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | +120 | -92 | -231% | -59% | -54% |
| 2024 | +24 | +114 | +79% | -43% | -43% |
| 2025 | +155 | +394 | +61% | -58% | -42% |
| 2026 | +135 | +156 | +14% | -65% | -60% |
| older pooled (1131 covered days of 1131) | +102 | +161 | +37% | -64% | -52% |

Windows, pick (cdr_1000) vs live bar (tm60), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +213 | -512 | 5615 | 14052 | 11115 | 26831 | 183 |
| L3M | +416 | -1456 | 2446 | 14481 | 4901 | 22485 | 91 |
| HOLD 2025-11..2026-04 | +244 | -83 | 3239 | 12032 | 8491 | 25122 | 181 |
| 2023-04..12 | +120 | -92 | 3944 | 9632 | 9271 | 20368 | 266 |
| 2024 | +24 | +114 | 7994 | 14034 | 15198 | 26868 | 366 |
| 2025 | +155 | +394 | 6968 | 16511 | 19827 | 34403 | 365 |
| all | +117 | +67 | 7522 | 22362 | 19827 | 41740 | 1314 |
White RC (best of 56 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.787

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -55 | +23 | 17081 | 19749 | 32% | 57% | 39% | -236/+99 | -858/+962 | -3308/+2819 |
| 3M->1M | 38 | +72 | +30 | 25066 | 18952 | 39% | 53% | 27% | +310/+128 | -694/+1051 | +53/+2907 |
| 12M->1M | 31 | -489 | +249 | 35601 | 17890 | 23% | 39% | 43% | -2097/+1069 | -4881/+2875 | -7761/+5842 |
| 6M->2wk | 80 | +82 | +39 | 13387 | 22052 | 38% | 50% | 57% | -83/+562 | -680/+1364 | -3182/+3193 |
| 6M->3M | 12 | -45 | +74 | 13101 | 18051 | 33% | 58% | 9% | -1277/+585 | -576/+951 | -4427/+2310 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## U7 london (reference live bar tm600)

Reference tm600: L6M -222 USD/wk (net, 1 lot), L3M -878, L12M -13, trades L6M 133

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | drb_1200 | +470 | 218 | -574 | no |
| 2 | dchg_20 | +381 | 269 | +778 | no |
| 3 | cusum_80 | +375 | 115 | +246 | no |
| 4 | cdr_400 | +286 | 65 | +875 | no |
| 5 | dchg_112 | +260 | 19 | +527 | no |
| 6 | dchg_10 | +230 | 499 | +732 | no |
| 7 | cusum_56 | +225 | 230 | +1142 | no |
| 8 | cusum_20 | +221 | 606 | +1916 | no |

No row passes the gate in the trailing 6 months (n>=30, positive, neighbours positive): no swap pick; reference stays reference (BEST-AVAILABLE-NOT-PROVEN row shows best ungated).


PICK (trailing 6M to 2026-11-13): **drb_1200** (ungated best, not a pick). Trailing-3M pick: dib_2000 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | +24 | -405 | -106% | -69% | -59% |
| 2024 | -50 | -147 | -66% | -1% | -9% |
| 2025 | -68 | -133 | -49% | +76% | +78% |
| 2026 | -303 | +170 | +278% | +154% | +94% |
| older pooled (1131 covered days of 1131) | -68 | -166 | -59% | -41% | -24% |

Windows, pick (drb_1200) vs live bar (tm600), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +470 | -222 | 5946 | 6073 | 19806 | 15538 | 183 |
| L3M | -574 | -878 | 7543 | 8034 | 19806 | 15538 | 91 |
| HOLD 2025-11..2026-04 | +25 | +467 | 5649 | 2464 | 15535 | 6047 | 181 |
| 2023-04..12 | +24 | -405 | 3471 | 11180 | 6850 | 16825 | 266 |
| 2024 | -50 | -147 | 11582 | 11708 | 19558 | 21491 | 366 |
| 2025 | -68 | -133 | 15324 | 8712 | 28068 | 15726 | 365 |
| all | +7 | -173 | 12398 | 22164 | 28068 | 36981 | 1314 |
White RC (best of 50 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.865

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | -56 | -131 | 17047 | 17948 | 30% | 46% | 53% | -238/-560 | -744/-1523 | -2506/-3317 |
| 3M->1M | 38 | -240 | -160 | 38206 | 18938 | 34% | 39% | 38% | -1030/-687 | -1208/-1684 | -2383/-3423 |
| 12M->1M | 31 | -70 | -124 | 25231 | 13859 | 29% | 52% | 73% | -302/-531 | -612/-1523 | -4884/-3086 |
| 6M->2wk | 80 | -48 | -160 | 10387 | 18001 | 24% | 49% | 73% | +108/-680 | +316/-1365 | -1751/-3352 |
| 6M->3M | 12 | +216 | -81 | 1693 | 15983 | 50% | 75% | 36% | +2137/-155 | +2774/-1046 | +323/-2564 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## K7 asia (reference live bar tm180)

Reference tm180: L6M +623 USD/wk (net, 1 lot), L3M +193, L12M -120, trades L6M 573

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | dchg_14 | +2380 | 965 | +1948 | no |
| 2 | dol_500 | +2086 | 694 | +1777 | pass |
| 3 | dol_750 | +1785 | 561 | +1407 | pass |
| 4 | dchg_10 | +1623 | 1075 | +1446 | pass |
| 5 | cdr_160 | +1525 | 464 | +1463 | no |
| 6 | dlt_250 | +1316 | 246 | +280 | pass |
| 7 | drb_2000 | +1303 | 269 | +719 | no |
| 8 | dol_2600 | +1188 | 289 | +908 | pass |

PICK (trailing 6M to 2026-11-13): **dol_500**. Trailing-3M pick: dchg_14 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -48 | +195 | +125% | +243% | +159% |
| 2024 | +211 | -37 | -669% | +8% | +16% |
| 2025 | +311 | -485 | -164% | -7% | -36% |
| 2026 | +1144 | +308 | -271% | -61% | -52% |
| older pooled (1131 covered days of 1131) | +293 | -86 | -439% | -26% | -30% |

Windows, pick (dol_500) vs live bar (tm180), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +2086 | +623 | 6677 | 21298 | 21770 | 38434 | 183 |
| L3M | +1777 | +193 | 7155 | 5085 | 21770 | 13036 | 91 |
| HOLD 2025-11..2026-04 | +1104 | -630 | 5540 | 22838 | 14107 | 37864 | 181 |
| 2023-04..12 | -48 | +195 | 9978 | 2906 | 17857 | 6892 | 266 |
| 2024 | +211 | -37 | 10446 | 9687 | 27987 | 24134 | 366 |
| 2025 | +311 | -485 | 15951 | 17122 | 29378 | 45883 | 365 |
| all | +542 | +13 | 14397 | 22124 | 39493 | 56651 | 1314 |
White RC (best of 56 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.552

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +433 | +9 | 11789 | 18532 | 62% | 57% | 36% | +1854/+36 | +2734/-146 | +4768/-170 |
| 3M->1M | 38 | +479 | +13 | 9402 | 20550 | 66% | 68% | 22% | +2054/+54 | +3387/-90 | +8476/-212 |
| 12M->1M | 31 | +230 | -42 | 16448 | 21021 | 61% | 52% | 53% | +987/-180 | +796/-771 | -2822/-2379 |
| 6M->2wk | 80 | +407 | +8 | 13380 | 21126 | 56% | 57% | 56% | +1903/-252 | +2768/-498 | +4765/-629 |
| 6M->3M | 12 | -5 | -2 | 15793 | 18765 | 58% | 67% | 18% | -664/+1219 | -64/-28 | +1427/-290 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## M7 asia (reference live bar tm60)

Reference tm60: L6M +1449 USD/wk (net, 1 lot), L3M +2353, L12M +875, trades L6M 597

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | dol_500 | +1857 | 529 | +1475 | pass |
| 2 | dlt_100 | +1782 | 418 | +1668 | pass |
| 3 | cdr_100 | +1717 | 521 | +849 | pass |
| 4 | tm60 | +1449 | 597 | +2353 | pass |
| 5 | dol_750 | +1404 | 464 | +911 | pass |
| 6 | dib_2000 | +1321 | 586 | +1084 | pass |
| 7 | cusum_40 | +1315 | 435 | +1145 | no |
| 8 | dlt_45 | +1264 | 615 | -295 | pass |

PICK (trailing 6M to 2026-11-13): **dol_500**. Trailing-3M pick: tm60 (DISAGREES with 6M).
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -92 | +136 | +168% | +59% | +15% |
| 2024 | +265 | +551 | +52% | +8% | +6% |
| 2025 | -284 | +96 | +397% | -15% | -13% |
| 2026 | +747 | +1024 | +27% | +17% | +75% |
| older pooled (1131 covered days of 1131) | +61 | +362 | +83% | +4% | -24% |

Windows, pick (dol_500) vs live bar (tm60), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +1857 | +1449 | 6434 | 4549 | 13642 | 10715 | 183 |
| L3M | +1474 | +2353 | 5201 | 4474 | 12057 | 9959 | 91 |
| HOLD 2025-11..2026-04 | +353 | +497 | 8122 | 8617 | 18412 | 19297 | 181 |
| 2023-04..12 | -92 | +136 | 9583 | 6011 | 13735 | 11948 | 266 |
| 2024 | +265 | +551 | 4595 | 4245 | 11272 | 10626 | 366 |
| 2025 | -284 | +96 | 10658 | 12571 | 22529 | 25816 | 365 |
| all | +311 | +514 | 9895 | 9332 | 23403 | 30682 | 1314 |
White RC (best of 42 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.881

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +648 | +652 | 5154 | 8791 | 35% | 70% | 56% | +2775/+2794 | +6857/+8040 | +12315/+15319 |
| 3M->1M | 38 | +392 | +651 | 5862 | 5021 | 29% | 61% | 19% | +1681/+2792 | +4526/+7987 | +8519/+15113 |
| 12M->1M | 31 | +609 | +582 | 9009 | 9883 | 29% | 55% | 63% | +2611/+2496 | +6005/+7415 | +10020/+14185 |
| 6M->2wk | 80 | +634 | +646 | 6099 | 8056 | 35% | 55% | 67% | +2216/+2752 | +5654/+7814 | +11437/+14900 |
| 6M->3M | 12 | +441 | +545 | 7618 | 7062 | 25% | 67% | 36% | +151/+498 | +5667/+7001 | +12198/+14663 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## U7 asia (reference live bar tm600)

Reference tm600: L6M +697 USD/wk (net, 1 lot), L3M +329, L12M +309, trades L6M 153

| rank | row | L6M USD/wk | L6M trades | L3M USD/wk | gate (n>=30 + neighbours>0) |
|---|---|---|---|---|---|
| 1 | dlt_100 | +2321 | 415 | +2235 | pass |
| 2 | cdr_160 | +2017 | 345 | +1250 | pass |
| 3 | dol_750 | +1928 | 440 | +1245 | pass |
| 4 | dchg_14 | +1787 | 502 | +214 | pass |
| 5 | cusum_28 | +1742 | 616 | +1169 | pass |
| 6 | cusum_40 | +1715 | 447 | +855 | pass |
| 7 | cdr_100 | +1715 | 522 | +304 | pass |
| 8 | dlt_150 | +1636 | 275 | +168 | pass |

PICK (trailing 6M to 2026-11-13): **dlt_100**. Trailing-3M pick: dlt_100.
Older-years check (before the pick window; positive pct = pick WORSE than live bar; AMBER 15-30, RED >30): status **RED**
| period | pick $/wk | ref $/wk | mean worse | ulcer worse | maxDD worse |
|---|---|---|---|---|---|
| 2023 | -349 | -3 | +9997% | +199% | +170% |
| 2024 | +293 | +128 | -128% | +63% | +47% |
| 2025 | +31 | +161 | +81% | +59% | +109% |
| 2026 | +307 | +104 | -195% | +116% | +121% |
| older pooled (1131 covered days of 1131) | +59 | +105 | +44% | +159% | +121% |

Windows, pick (dlt_100) vs live bar (tm600), USD/wk net 1 lot, ulcer, max DD (positive pct = pick worse on DD/ulcer):

| window | pick $/wk | ref $/wk | pick ulcer | ref ulcer | pick maxDD | ref maxDD | covered days |
|---|---|---|---|---|---|---|---|
| L6M | +2321 | +697 | 4459 | 2189 | 10219 | 6802 | 183 |
| L3M | +2235 | +329 | 4615 | 2748 | 10120 | 6802 | 91 |
| HOLD 2025-11..2026-04 | -125 | -76 | 10190 | 5616 | 26769 | 12127 | 181 |
| 2023-04..12 | -349 | -3 | 10305 | 3452 | 17080 | 6330 | 266 |
| 2024 | +293 | +128 | 2761 | 1693 | 6567 | 4460 | 366 |
| 2025 | +31 | +161 | 7538 | 4731 | 18097 | 8669 | 365 |
| all | +374 | +187 | 10998 | 4278 | 26769 | 12127 | 1314 |
White RC (best of 55 eligible rows vs live bar, L6M, stationary 5-day block bootstrap 2,000): p = 0.579

Rolling walk-forward (same procedure, from 2023-10; USD/wk net 1 lot; ref = live bar):

| procedure | periods | OOS $/wk | ref $/wk | OOS ulcer | ref ulcer | share beat ref | share >0 | pick same as prev | next-1M pick/ref | next-3M | next-6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6M->1M | 37 | +37 | +264 | 24105 | 3047 | 38% | 46% | 31% | +157/+1130 | -472/+3123 | +1233/+5980 |
| 3M->1M | 38 | +279 | +234 | 7917 | 3046 | 55% | 63% | 24% | +1197/+1001 | -928/+2994 | +1037/+5757 |
| 12M->1M | 31 | +198 | +280 | 13300 | 3657 | 29% | 42% | 47% | +850/+1202 | +2655/+3377 | +2453/+6497 |
| 6M->2wk | 80 | -423 | +253 | 40801 | 3738 | 34% | 40% | 44% | -156/+1223 | -215/+2893 | +1276/+5807 |
| 6M->3M | 12 | +105 | +237 | 21852 | 2652 | 50% | 42% | 18% | -1494/+1084 | +1346/+3048 | +4323/+5983 |

Null (nonsense random-clock rows): NOT BUILT YET (0 rows).

## Engine swap test (exact engine, full JL3 stack; swap ON vs JL3 today)

Identity (JL3 = 202610 691 trades 37,159.82; 202504 637 / 41,239.76):

| set | mode | month | JL3 trades / net | swap trades / net | result |
|---|---|---|---|---|---|
| TL3_SWA_ID0 | inert | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID2 | K7 replay of the native attempt | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID2 | K7 replay of the native attempt | 202504 | 637 / 41239.76 | 637 / 41239.76 | IDENTICAL |
| TL3_SWA_ID6 | K7 own live 3-min bar signals injected as bar events (ts_recv-mapped) | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID6 | K7 own live 3-min bar signals injected as bar events (ts_recv-mapped) | 202504 | 637 / 41239.76 | 637 / 41239.76 | IDENTICAL |
| TL3_SWA_ID2M7 | M7 replay | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID2M7 | M7 replay | 202504 | 637 / 41239.76 | 637 / 41239.76 | IDENTICAL |
| TL3_SWA_ID6M7 | M7 own live 1-min signals as bar events | 202610 | 691 / 37159.82 | 691 / 39005.82 | differs |
| TL3_SWA_ID6M7 | M7 own live 1-min signals as bar events | 202504 | 637 / 41239.76 | 638 / 41070.08 | differs |
| TL3_SWA_ID2U7 | U7 replay | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID2U7 | U7 replay | 202504 | 637 / 41239.76 | 637 / 41239.76 | IDENTICAL |
| TL3_SWA_ID6U7 | U7 own live 10-min signals as bar events | 202610 | 691 / 37159.82 | 691 / 37159.82 | IDENTICAL |
| TL3_SWA_ID6U7 | U7 own live 10-min signals as bar events | 202504 | 637 / 41239.76 | 637 / 41239.76 | IDENTICAL |


### K7_3_vsess_300 (TL3_SWA_K73_vsess300)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9800 | +5.1% | +20109 | +20325 | +186 | 30189/34024 | -19127/-18740 |
| L3M | 10841 | 11551 | +6.6% | +16721 | +16699 | -51 | 30189/34024 | -15066/-14580 |
| HOLD | 27872 | 26995 | -3.1% | +9996 | +8857 | -1166 | 82017/82585 | -36787/-29287 |
| OLDER | 25599 | 26945 | +5.3% | +5291 | +4971 | -335 | 88502/81578 | -38412/-39989 |
| Y2023 | 17453 | 16695 | -4.3% | +2124 | +2065 | -69 | 40010/40490 | -17197/-21098 |
| Y2024 | 26429 | 32147 | +21.6% | +5049 | +4422 | -643 | 70704/75281 | -36802/-36767 |
| Y2025 | 30332 | 27570 | -9.1% | +8447 | +8262 | -205 | 88502/81578 | -27370/-26570 |
Controls L6M: 0 valid random-clock draws; real ulcer change +5.1% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +6.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -1199.0, 'K7': 5653.0, 'M7': -70.0, 'O7': 0.0, 'P7': 1297.0, 'U7': 0.0}

### K7_3_tsf_5_700 (TL3_SWA_K73_tsf5700)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 10685 | +14.6% | +20109 | +21167 | +1065 | 30189/38513 | -19127/-23134 |
| L3M | 10841 | 13046 | +20.3% | +16721 | +17675 | +958 | 30189/38513 | -15066/-19695 |
| HOLD | 27872 | 29213 | +4.8% | +9996 | +9529 | -463 | 82017/85943 | -36787/-35697 |
| OLDER | 25599 | 26032 | +1.7% | +5291 | +5210 | -80 | 88502/96232 | -38412/-41317 |
| Y2023 | 17453 | 17763 | +1.8% | +2124 | +1963 | -165 | 40010/44335 | -17197/-21890 |
| Y2024 | 26429 | 25219 | -4.6% | +5049 | +5510 | +461 | 70704/66738 | -36802/-37202 |
| Y2025 | 30332 | 32464 | +7.0% | +8447 | +7786 | -654 | 88502/96232 | -27370/-26307 |
Controls L6M: 0 valid random-clock draws; real ulcer change +14.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +20.3% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 939.0, 'K7': 26289.0, 'M7': 2398.0, 'O7': 0.0, 'P7': -1807.0, 'U7': 0.0}

### K7_3_frenko_28 (TL3_SWA_K73_frenko28)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9841 | +5.5% | +20109 | +18715 | -1430 | 30189/33507 | -19127/-22260 |
| L3M | 10841 | 10980 | +1.3% | +16721 | +16443 | -308 | 30189/30598 | -15066/-15017 |
| HOLD | 27872 | 23449 | -15.9% | +9996 | +10648 | +622 | 82017/76441 | -36787/-24245 |
| OLDER | 25599 | 25868 | +1.0% | +5291 | +4934 | -373 | 88502/76909 | -38412/-39596 |
| Y2023 | 17453 | 18451 | +5.7% | +2124 | +1468 | -667 | 40010/50513 | -17197/-20568 |
| Y2024 | 26429 | 30010 | +13.5% | +5049 | +4527 | -538 | 70704/63852 | -36802/-36173 |
| Y2025 | 30332 | 26187 | -13.7% | +8447 | +8561 | +92 | 88502/76909 | -27370/-31615 |
Controls L6M: 0 valid random-clock draws; real ulcer change +5.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +1.3% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -3561.0, 'K7': -23733.0, 'M7': -5744.0, 'O7': 0.0, 'P7': -3600.0, 'U7': 0.0}

### K7_3_mrenko_10 (TL3_SWA_K73_mrenko10)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9964 | +6.8% | +20109 | +18893 | -1254 | 30189/34334 | -19127/-20296 |
| L3M | 10841 | 11308 | +4.3% | +16721 | +16649 | -105 | 30189/32401 | -15066/-14723 |
| HOLD | 27872 | 27431 | -1.6% | +9996 | +10230 | +196 | 82017/80141 | -36787/-27578 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +6.8% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +4.3% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -3596.0, 'K7': -24912.0, 'M7': -2991.0, 'O7': 0.0, 'P7': -462.0, 'U7': 0.0}

### K7_3_vol_350 (TL3_SWA_K73_vol350)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9888 | +6.0% | +20109 | +19723 | -430 | 30189/33524 | -19127/-18800 |
| L3M | 10841 | 11141 | +2.8% | +16721 | +17294 | +534 | 30189/31290 | -15066/-16507 |
| HOLD | 27872 | 26946 | -3.3% | +9996 | +10274 | +236 | 82017/81655 | -36787/-26026 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +6.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +2.8% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -3561.0, 'K7': 1426.0, 'M7': -7532.0, 'O7': 0.0, 'P7': -462.0, 'U7': 0.0}

### K7_3_trb_6000 (TL3_SWA_K73_trb6000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 10442 | +11.9% | +20109 | +20691 | +589 | 30189/36523 | -19127/-21902 |
| L3M | 10841 | 12634 | +16.5% | +16721 | +16448 | -268 | 30189/36523 | -15066/-18185 |
| HOLD | 27872 | 28152 | +1.0% | +9996 | +9968 | -18 | 82017/86291 | -36787/-30054 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +11.9% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +16.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': 18882.0, 'M7': -444.0, 'O7': 0.0, 'P7': -3138.0, 'U7': 0.0}

### K7_3_cdr_2500 (TL3_SWA_K73_cdr2500)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 10743 | +15.2% | +20109 | +20276 | +184 | 30189/37686 | -19127/-22884 |
| L3M | 10841 | 13107 | +20.9% | +16721 | +16921 | +217 | 30189/37686 | -15066/-19093 |
| HOLD | 27872 | 27326 | -2.0% | +9996 | +9358 | -614 | 82017/81125 | -36787/-25261 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +15.2% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +20.9% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 939.0, 'K7': 5380.0, 'M7': 1214.0, 'O7': 0.0, 'P7': -3138.0, 'U7': 0.0}

### K7_3_tm420 (TL3_SWA_K73_tm420)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 10077 | +8.0% | +20109 | +20868 | +767 | 30189/35404 | -19127/-23299 |
| L3M | 10841 | 12102 | +11.6% | +16721 | +17147 | +434 | 30189/35404 | -15066/-15232 |
| HOLD | 27872 | 27205 | -2.4% | +9996 | +10424 | +441 | 82017/84694 | -36787/-29597 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +8.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +11.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': 24296.0, 'M7': -1199.0, 'O7': 0.0, 'P7': -3138.0, 'U7': 0.0}

### M7_1_lbrk_5_20 (TL3_SWA_M71_lbrk520)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 8247 | -11.6% | +20109 | +21655 | +1593 | 30189/22450 | -19127/-15529 |
| L3M | 10841 | 8948 | -17.5% | +16721 | +18287 | +1601 | 30189/20505 | -15066/-14103 |
| HOLD | 27872 | 26893 | -3.5% | +9996 | +9982 | +31 | 82017/72689 | -36787/-32463 |
| OLDER | 25599 | 22046 | -13.9% | +5291 | +5698 | +436 | 88502/80714 | -38412/-35254 |
| Y2023 | 17453 | 18176 | +4.1% | +2124 | +2024 | -79 | 40010/44328 | -17197/-15782 |
| Y2024 | 26429 | 20453 | -22.6% | +5049 | +5314 | +294 | 70704/58261 | -36802/-27704 |
| Y2025 | 30332 | 26605 | -12.3% | +8447 | +9483 | +1072 | 88502/80714 | -27370/-27134 |
Controls L6M: 0 valid random-clock draws; real ulcer change -11.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -17.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 247.0, 'K7': 12898.0, 'M7': 25985.0, 'O7': -959.0, 'P7': -2841.0, 'U7': 5329.0}

### M7_1_tm600 (TL3_SWA_M71_tm600)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 8619 | -7.6% | +20109 | +20970 | +905 | 30189/32129 | -19127/-19451 |
| L3M | 10841 | 10410 | -4.0% | +16721 | +16911 | +228 | 30189/32129 | -15066/-15148 |
| HOLD | 27872 | 24738 | -11.2% | +9996 | +9819 | -135 | 82017/66904 | -36787/-31733 |
| OLDER | 25599 | 24690 | -3.6% | +5291 | +5868 | +604 | 88502/85396 | -38412/-35887 |
| Y2023 | 17453 | 17313 | -0.8% | +2124 | +2833 | +729 | 40010/40102 | -17197/-19055 |
| Y2024 | 26429 | 26199 | -0.9% | +5049 | +5185 | +164 | 70704/71019 | -36802/-33351 |
| Y2025 | 30332 | 28234 | -6.9% | +8447 | +9436 | +1022 | 88502/85396 | -27370/-25408 |
Controls L6M: 0 valid random-clock draws; real ulcer change -7.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -4.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -1844.0, 'K7': 20483.0, 'M7': 4436.0, 'O7': -1124.0, 'P7': -4624.0, 'U7': 5329.0}

### M7_1_tm1200 (TL3_SWA_M71_tm1200)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 8119 | -13.0% | +20109 | +22225 | +2158 | 30189/24222 | -19127/-14975 |
| L3M | 10841 | 9699 | -10.5% | +16721 | +17653 | +970 | 30189/24222 | -15066/-14748 |
| HOLD | 27872 | 26491 | -5.0% | +9996 | +9121 | -828 | 82017/67616 | -36787/-32913 |
| OLDER | 25599 | 23380 | -8.7% | +5291 | +5899 | +638 | 88502/78752 | -38412/-39316 |
| Y2023 | 17453 | 18202 | +4.3% | +2124 | +2671 | +569 | 40010/43589 | -17197/-17829 |
| Y2024 | 26429 | 24375 | -7.8% | +5049 | +5146 | +128 | 70704/63931 | -36802/-29194 |
| Y2025 | 30332 | 26146 | -13.8% | +8447 | +9725 | +1316 | 88502/78752 | -27370/-24948 |
Controls L6M: 0 valid random-clock draws; real ulcer change -13.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -10.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 396.0, 'K7': 30244.0, 'M7': 22952.0, 'O7': 98.0, 'P7': -3398.0, 'U7': 5329.0}

### M7_1_lbrk_3_40 (TL3_SWA_M71_lbrk340)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 7660 | -17.9% | +20109 | +21531 | +1471 | 30189/22450 | -19127/-18310 |
| L3M | 10841 | 8714 | -19.6% | +16721 | +17668 | +994 | 30189/22064 | -15066/-12180 |
| HOLD | 27872 | 24089 | -13.6% | +9996 | +9882 | -63 | 82017/64546 | -36787/-31617 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -17.9% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -19.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -775.0, 'K7': 28062.0, 'M7': 10869.0, 'O7': -2338.0, 'P7': -4935.0, 'U7': 6518.0}

### M7_1_dol_750 (TL3_SWA_M71_dol750)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 8167 | -12.4% | +20109 | +22338 | +2257 | 30189/28317 | -19127/-23341 |
| L3M | 10841 | 9328 | -14.0% | +16721 | +18464 | +1771 | 30189/28317 | -15066/-13958 |
| HOLD | 27872 | 28784 | +3.3% | +9996 | +9645 | -321 | 82017/76584 | -36787/-36980 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -12.4% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -14.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 421.0, 'K7': 31331.0, 'M7': 30474.0, 'O7': -3490.0, 'P7': -2876.0, 'U7': 2742.0}

### M7_1_dib_10000 (TL3_SWA_M71_dib10000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9225 | -1.1% | +20109 | +20544 | +472 | 30189/29339 | -19127/-18584 |
| L3M | 10841 | 10807 | -0.3% | +16721 | +15297 | -1384 | 30189/29339 | -15066/-15277 |
| HOLD | 27872 | 32277 | +15.8% | +9996 | +8829 | -1123 | 82017/79623 | -36787/-34147 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -1.1% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -0.3% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -1587.0, 'K7': 19026.0, 'M7': 572.0, 'O7': -1124.0, 'P7': -3582.0, 'U7': -1854.0}

### M7_1_cdr_400 (TL3_SWA_M71_cdr400)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 8778 | -5.9% | +20109 | +20777 | +716 | 30189/27732 | -19127/-16721 |
| L3M | 10841 | 10121 | -6.6% | +16721 | +16673 | -4 | 30189/27732 | -15066/-13758 |
| HOLD | 27872 | 23894 | -14.3% | +9996 | +10221 | +275 | 82017/65841 | -36787/-35383 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -5.9% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -6.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -2683.0, 'K7': 21026.0, 'M7': -5220.0, 'O7': -1762.0, 'P7': 869.0, 'U7': 5329.0}

### M7_1_vsess_300 (TL3_SWA_M71_vsess300)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9648 | +3.4% | +20109 | +20972 | +861 | 30189/34058 | -19127/-20794 |
| L3M | 10841 | 12259 | +13.1% | +16721 | +15199 | -1522 | 30189/34058 | -15066/-21032 |
| HOLD | 27872 | 28830 | +3.4% | +9996 | +10425 | +430 | 82017/88089 | -36787/-35504 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +3.4% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +13.1% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -416.0, 'K7': 12635.0, 'M7': 23009.0, 'O7': -3341.0, 'P7': -8199.0, 'U7': -1002.0}

### K7_1_urenko_14 (TL3_SWA_K71_urenko14)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9408 | +0.9% | +20109 | +19018 | -1092 | 30189/27352 | -19127/-16255 |
| L3M | 10841 | 10410 | -4.0% | +16721 | +16298 | -419 | 30189/27352 | -15066/-18321 |
| HOLD | 27872 | 31401 | +12.7% | +9996 | +7835 | -2165 | 82017/85050 | -36787/-33437 |
| OLDER | 25599 | 27942 | +9.1% | +5291 | +4933 | -364 | 88502/95964 | -38412/-37138 |
| Y2023 | 17453 | 16120 | -7.6% | +2124 | +2825 | +699 | 40010/40651 | -17197/-18338 |
| Y2024 | 26429 | 26454 | +0.1% | +5049 | +4647 | -405 | 70704/61996 | -36802/-35955 |
| Y2025 | 30332 | 36725 | +21.1% | +8447 | +7182 | -1277 | 88502/95964 | -27370/-30466 |
Controls L6M: 0 valid random-clock draws; real ulcer change +0.9% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -4.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -382.0, 'K7': -37447.0, 'M7': -3383.0, 'O7': -70.0, 'P7': 8863.0, 'U7': 3742.0}

### K7_1_vib_700 (TL3_SWA_K71_vib700)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 8488 | -9.0% | +20109 | +19985 | -130 | 30189/22107 | -19127/-17131 |
| L3M | 10841 | 9278 | -14.4% | +16721 | +17452 | +716 | 30189/22107 | -15066/-19644 |
| HOLD | 27872 | 32859 | +17.9% | +9996 | +6955 | -3050 | 82017/79406 | -36787/-34731 |
| OLDER | 25599 | 25943 | +1.3% | +5291 | +5064 | -233 | 88502/91580 | -38412/-38466 |
| Y2023 | 17453 | 18054 | +3.4% | +2124 | +2177 | +50 | 40010/45131 | -17197/-26418 |
| Y2024 | 26429 | 23231 | -12.1% | +5049 | +5004 | -54 | 70704/55464 | -36802/-38466 |
| Y2025 | 30332 | 33867 | +11.7% | +8447 | +7749 | -704 | 88502/91580 | -27370/-24989 |
Controls L6M: 0 valid random-clock draws; real ulcer change -9.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -14.4% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 941.0, 'K7': 1724.0, 'M7': -3671.0, 'O7': -1068.0, 'P7': -9598.0, 'U7': 8421.0}

### K7_1_dlt_30 (TL3_SWA_K71_dlt30)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9927 | +6.4% | +20109 | +18931 | -1191 | 30189/30715 | -19127/-15955 |
| L3M | 10841 | 11546 | +6.5% | +16721 | +16322 | -414 | 30189/30715 | -15066/-16075 |
| HOLD | 27872 | 31263 | +12.2% | +9996 | +6743 | -3259 | 82017/81364 | -36787/-35914 |
| OLDER | 25599 | 24763 | -3.3% | +5291 | +4894 | -403 | 88502/90189 | -38412/-37547 |
| Y2023 | 17453 | 15014 | -14.0% | +2124 | +3260 | +1133 | 40010/36752 | -17197/-19477 |
| Y2024 | 26429 | 24147 | -8.6% | +5049 | +4539 | -516 | 70704/57405 | -36802/-33336 |
| Y2025 | 30332 | 31618 | +4.2% | +8447 | +6798 | -1656 | 88502/90189 | -27370/-27455 |
Controls L6M: 0 valid random-clock draws; real ulcer change +6.4% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +6.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 1196.0, 'K7': -21111.0, 'M7': -5791.0, 'O7': -637.0, 'P7': -1628.0, 'U7': -2991.0}

### K7_1_dib_6000 (TL3_SWA_K71_dib6000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9158 | -1.8% | +20109 | +20494 | +391 | 30189/25846 | -19127/-19695 |
| L3M | 10841 | 10186 | -6.0% | +16721 | +17270 | +551 | 30189/25846 | -15066/-19807 |
| HOLD | 27872 | 27900 | +0.1% | +9996 | +10040 | +55 | 82017/79539 | -36787/-33303 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -1.8% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -6.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -1159.0, 'K7': 23156.0, 'M7': -3468.0, 'O7': -2400.0, 'P7': -3815.0, 'U7': -2171.0}

### K7_1_trb_700 (TL3_SWA_K71_trb700)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9239 | -0.9% | +20109 | +19757 | -343 | 30189/29556 | -19127/-20695 |
| L3M | 10841 | 10337 | -4.6% | +16721 | +17242 | +521 | 30189/25671 | -15066/-20139 |
| HOLD | 27872 | 26188 | -6.0% | +9996 | +9068 | -927 | 82017/74148 | -36787/-33863 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -0.9% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -4.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -2098.0, 'K7': 3570.0, 'M7': -7436.0, 'O7': 1929.0, 'P7': -9237.0, 'U7': 4019.0}

### K7_1_tm900 (TL3_SWA_K71_tm900)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9069 | -2.8% | +20109 | +18774 | -1303 | 30189/27480 | -19127/-12862 |
| L3M | 10841 | 10769 | -0.7% | +16721 | +15962 | -735 | 30189/27480 | -15066/-19767 |
| HOLD | 27872 | 30325 | +8.8% | +9996 | +8168 | -1809 | 82017/86572 | -36787/-36184 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -2.8% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -0.7% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -1923.0, 'K7': -23015.0, 'M7': -4590.0, 'O7': -1983.0, 'P7': -6892.0, 'U7': 3328.0}

### K7_1_dol_1700 (TL3_SWA_K71_dol1700)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 8434 | -9.6% | +20109 | +20910 | +827 | 30189/24322 | -19127/-14628 |
| L3M | 10841 | 9539 | -12.0% | +16721 | +17128 | +427 | 30189/24322 | -15066/-17318 |
| HOLD | 27872 | 28322 | +1.6% | +9996 | +8675 | -1306 | 82017/68329 | -36787/-27021 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -9.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -12.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': 25618.0, 'M7': 1626.0, 'O7': -2021.0, 'P7': -9494.0, 'U7': 5348.0}

### K7_1_vsess_120 (TL3_SWA_K71_vsess120)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 10664 | +14.3% | +20109 | +18957 | -1142 | 30189/35434 | -19127/-19369 |
| L3M | 10841 | 12222 | +12.7% | +16721 | +15684 | -1036 | 30189/35434 | -15066/-23425 |
| HOLD | 27872 | 26970 | -3.2% | +9996 | +10335 | +338 | 82017/79032 | -36787/-33104 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +14.3% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +12.7% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -2658.0, 'K7': -16531.0, 'M7': -7533.0, 'O7': -1705.0, 'P7': -6544.0, 'U7': 4698.0}

### K7_4_tsf_10_60 (TL3_SWA_K74_tsf1060)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9337 | +0.1% | +20109 | +20493 | +386 | 30189/30958 | -19127/-18853 |
| L3M | 10841 | 10791 | -0.5% | +16721 | +17354 | +635 | 30189/30958 | -15066/-16852 |
| HOLD | 27872 | 30546 | +9.6% | +9996 | +8730 | -1267 | 82017/87788 | -36787/-36752 |
| OLDER | 25599 | 26997 | +5.5% | +5291 | +4676 | -618 | 88502/82315 | -38412/-39848 |
| Y2023 | 17453 | 24180 | +38.5% | +2124 | +1259 | -868 | 40010/53660 | -17197/-17467 |
| Y2024 | 26429 | 28178 | +6.6% | +5049 | +4623 | -430 | 70704/71604 | -36802/-36802 |
| Y2025 | 30332 | 27931 | -7.9% | +8447 | +7830 | -618 | 88502/82315 | -27370/-34573 |
Controls L6M: 0 valid random-clock draws; real ulcer change +0.1% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -0.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': 10106.0, 'M7': 0.0, 'O7': 0.0, 'P7': 0.0, 'U7': 0.0}

### K7_4_drb_6000 (TL3_SWA_K74_drb6000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9385 | +0.6% | +20109 | +20061 | -31 | 30189/31656 | -19127/-18618 |
| L3M | 10841 | 10986 | +1.3% | +16721 | +16865 | +157 | 30189/31656 | -15066/-17348 |
| HOLD | 27872 | 28201 | +1.2% | +9996 | +10124 | +143 | 82017/83127 | -36787/-34860 |
| OLDER | 25599 | 25489 | -0.4% | +5291 | +5056 | -221 | 88502/73761 | -38412/-40204 |
| Y2023 | 17453 | 23651 | +35.5% | +2124 | +1539 | -572 | 40010/54005 | -17197/-18778 |
| Y2024 | 26429 | 27421 | +3.8% | +5049 | +4861 | -174 | 70704/69045 | -36802/-36802 |
| Y2025 | 30332 | 24651 | -18.7% | +8447 | +8473 | +41 | 88502/73761 | -27370/-28539 |
Controls L6M: 0 valid random-clock draws; real ulcer change +0.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +1.3% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -1242.0, 'M7': 0.0, 'O7': 0.0, 'P7': 0.0, 'U7': 0.0}

### K7_4_tm1800 (TL3_SWA_K74_tm1800)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9242 | -0.9% | +20109 | +19639 | -447 | 30189/30722 | -19127/-18618 |
| L3M | 10841 | 10729 | -1.0% | +16721 | +16696 | -5 | 30189/30722 | -15066/-16351 |
| HOLD | 27872 | 26885 | -3.5% | +9996 | +9946 | -28 | 82017/82047 | -36787/-35164 |
| OLDER | 25599 | 26476 | +3.4% | +5291 | +4902 | -367 | 88502/81775 | -38412/-39671 |
| Y2023 | 17453 | 20525 | +17.6% | +2124 | +2011 | -94 | 40010/50292 | -17197/-18173 |
| Y2024 | 26429 | 29739 | +12.5% | +5049 | +4593 | -433 | 70704/65512 | -36802/-36802 |
| Y2025 | 30332 | 27068 | -10.8% | +8447 | +7889 | -534 | 88502/81775 | -27370/-35148 |
Controls L6M: 0 valid random-clock draws; real ulcer change -0.9% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -1.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -12332.0, 'M7': 0.0, 'O7': 0.0, 'P7': 0.0, 'U7': 0.0}

### K7_4_trb_2000 (TL3_SWA_K74_trb2000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9710 | +4.1% | +20109 | +19349 | -758 | 30189/32816 | -19127/-19293 |
| L3M | 10841 | 11462 | +5.7% | +16721 | +16013 | -706 | 30189/32816 | -15066/-18916 |
| HOLD | 27872 | 27908 | +0.1% | +9996 | +9549 | -449 | 82017/87998 | -36787/-36779 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +4.1% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +5.7% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -19965.0, 'M7': 0.0, 'O7': 0.0, 'P7': 0.0, 'U7': 0.0}

### K7_4_pnf_56 (TL3_SWA_K74_pnf56)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9374 | +0.5% | +20109 | +19401 | -683 | 30189/31822 | -19127/-18618 |
| L3M | 10841 | 10953 | +1.0% | +16721 | +16477 | -223 | 30189/31822 | -15066/-17515 |
| HOLD | 27872 | 28160 | +1.0% | +9996 | +9650 | -321 | 82017/82239 | -36787/-35164 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +0.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +1.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -18586.0, 'M7': 0.0, 'O7': 0.0, 'P7': 0.0, 'U7': 0.0}

### K7_4_vsess_600 (TL3_SWA_K74_vsess600)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9288 | -0.4% | +20109 | +19573 | -556 | 30189/29227 | -19127/-19144 |
| L3M | 10841 | 10777 | -0.6% | +16721 | +16109 | -624 | 30189/29227 | -15066/-14211 |
| HOLD | 27872 | 29465 | +5.7% | +9996 | +10503 | +490 | 82017/84576 | -36787/-39509 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -0.4% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -0.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -14076.0, 'M7': 0.0, 'O7': 0.0, 'P7': 0.0, 'U7': 0.0}

### K7_4_cdr_600 (TL3_SWA_K74_cdr600)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9256 | -0.8% | +20109 | +19784 | -309 | 30189/30722 | -19127/-18618 |
| L3M | 10841 | 10716 | -1.2% | +16721 | +16657 | -50 | 30189/30722 | -15066/-14078 |
| HOLD | 27872 | 28406 | +1.9% | +9996 | +9858 | -124 | 82017/86380 | -36787/-35895 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -0.8% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -1.2% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -8537.0, 'M7': 0.0, 'O7': 0.0, 'P7': 0.0, 'U7': 0.0}

### M7_3_tsf_10_120 (TL3_SWA_M73_tsf10120)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9078 | -2.7% | +20109 | +20302 | +214 | 30189/29605 | -19127/-19067 |
| L3M | 10841 | 10687 | -1.4% | +16721 | +15803 | -902 | 30189/29605 | -15066/-14155 |
| HOLD | 27872 | 28226 | +1.3% | +9996 | +9844 | -133 | 82017/78949 | -36787/-30783 |
| OLDER | 25599 | 28653 | +11.9% | +5291 | +4902 | -377 | 88502/90859 | -38412/-36634 |
| Y2023 | 17453 | 15415 | -11.7% | +2124 | +2382 | +266 | 40010/37670 | -17197/-18986 |
| Y2024 | 26429 | 33847 | +28.1% | +5049 | +4350 | -686 | 70704/76013 | -36802/-36634 |
| Y2025 | 30332 | 30939 | +2.0% | +8447 | +7846 | -585 | 88502/90859 | -27370/-23700 |
Controls L6M: 0 valid random-clock draws; real ulcer change -2.7% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -1.4% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -1281.0, 'M7': 7583.0, 'O7': 0.0, 'P7': -1212.0, 'U7': 0.0}

### M7_3_vsess_50 (TL3_SWA_M73_vsess50)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9374 | +0.5% | +20109 | +19536 | -556 | 30189/32093 | -19127/-20196 |
| L3M | 10841 | 11157 | +2.9% | +16721 | +16203 | -505 | 30189/32093 | -15066/-16644 |
| HOLD | 27872 | 27985 | +0.4% | +9996 | +10374 | +393 | 82017/81802 | -36787/-32017 |
| OLDER | 25599 | 28169 | +10.0% | +5291 | +5131 | -148 | 88502/99552 | -38412/-37738 |
| Y2023 | 17453 | 17643 | +1.1% | +2124 | +2488 | +375 | 40010/47663 | -17197/-18958 |
| Y2024 | 26429 | 29457 | +11.5% | +5049 | +4586 | -450 | 70704/64167 | -36802/-35389 |
| Y2025 | 30332 | 33760 | +11.3% | +8447 | +8179 | -258 | 88502/99552 | -27370/-27912 |
Controls L6M: 0 valid random-clock draws; real ulcer change +0.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +2.9% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': 253.0, 'M7': -14065.0, 'O7': 0.0, 'P7': -1224.0, 'U7': 0.0}

### M7_3_tm1200 (TL3_SWA_M73_tm1200)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9082 | -2.6% | +20109 | +19955 | -127 | 30189/29605 | -19127/-20196 |
| L3M | 10841 | 10638 | -1.9% | +16721 | +15962 | -737 | 30189/29605 | -15066/-14155 |
| HOLD | 27872 | 28617 | +2.7% | +9996 | +9133 | -839 | 82017/80564 | -36787/-28144 |
| OLDER | 25599 | 27066 | +5.7% | +5291 | +4785 | -483 | 88502/90117 | -38412/-35587 |
| Y2023 | 17453 | 16128 | -7.6% | +2124 | +1971 | -134 | 40010/37772 | -17197/-18938 |
| Y2024 | 26429 | 29748 | +12.6% | +5049 | +4310 | -714 | 70704/64681 | -36802/-33256 |
| Y2025 | 30332 | 31239 | +3.0% | +8447 | +7905 | -520 | 88502/90117 | -27370/-22655 |
Controls L6M: 0 valid random-clock draws; real ulcer change -2.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -1.9% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -657.0, 'M7': -2165.0, 'O7': 0.0, 'P7': -1212.0, 'U7': 0.0}

### M7_3_mrenko_112 (TL3_SWA_M73_mrenko112)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9100 | -2.4% | +20109 | +19746 | -332 | 30189/29605 | -19127/-21394 |
| L3M | 10841 | 10715 | -1.2% | +16721 | +15717 | -978 | 30189/29605 | -15066/-14155 |
| HOLD | 27872 | 29097 | +4.4% | +9996 | +9473 | -494 | 82017/81736 | -36787/-30923 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -2.4% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -1.2% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': 524.0, 'M7': -8839.0, 'O7': 0.0, 'P7': -1212.0, 'U7': 0.0}

### M7_3_tick_2000 (TL3_SWA_M73_tick2000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9438 | +1.2% | +20109 | +19417 | -677 | 30189/29605 | -19127/-21070 |
| L3M | 10841 | 11036 | +1.8% | +16721 | +15407 | -1303 | 30189/29605 | -15066/-15347 |
| HOLD | 27872 | 27616 | -0.9% | +9996 | +9966 | -18 | 82017/79646 | -36787/-31475 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +1.2% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +1.8% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -1974.0, 'M7': -15646.0, 'O7': 0.0, 'P7': -552.0, 'U7': 0.0}

### M7_3_vnorm_80 (TL3_SWA_M73_vnorm80)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9419 | +1.0% | +20109 | +19858 | -228 | 30189/32073 | -19127/-20301 |
| L3M | 10841 | 11285 | +4.1% | +16721 | +15574 | -1128 | 30189/32073 | -15066/-15956 |
| HOLD | 27872 | 27675 | -0.7% | +9996 | +9805 | -171 | 82017/81037 | -36787/-30780 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +1.0% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +4.1% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -306.0, 'M7': -5075.0, 'O7': 0.0, 'P7': -1212.0, 'U7': 0.0}

### M7_3_trb_10000 (TL3_SWA_M73_trb10000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9196 | -1.4% | +20109 | +19517 | -565 | 30189/29605 | -19127/-20256 |
| L3M | 10841 | 10786 | -0.5% | +16721 | +15591 | -1109 | 30189/29605 | -15066/-14155 |
| HOLD | 27872 | 29167 | +4.6% | +9996 | +9340 | -632 | 82017/80327 | -36787/-31152 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -1.4% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -0.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -82.0, 'M7': -14252.0, 'O7': 0.0, 'P7': -1212.0, 'U7': 0.0}

### U7_1_vsess_450 (TL3_SWA_U71_vsess450)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 17941 | +92.3% | +20109 | +15830 | -4363 | 30189/64279 | -19127/-35485 |
| L3M | 10841 | 23271 | +114.7% | +16721 | +11840 | -4943 | 30189/64279 | -15066/-31976 |
| HOLD | 27872 | 32493 | +16.6% | +9996 | +4899 | -5183 | 82017/68630 | -36787/-40490 |
| OLDER | 25599 | 20418 | -20.2% | +5291 | +5209 | -123 | 88502/66687 | -38412/-36761 |
| Y2023 | 17453 | 18740 | +7.4% | +2124 | +4232 | +2085 | 40010/52364 | -17197/-18233 |
| Y2024 | 26429 | 22813 | -13.7% | +5049 | +4158 | -920 | 70704/66687 | -36802/-32565 |
| Y2025 | 30332 | 18730 | -38.3% | +8447 | +7357 | -1161 | 88502/50495 | -27370/-25385 |
Controls L6M: 0 valid random-clock draws; real ulcer change +92.3% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +114.7% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -2906.0, 'K7': 9672.0, 'M7': 3959.0, 'O7': 6980.0, 'P7': -2826.0, 'U7': -127341.0}

### U7_1_dib_240 (TL3_SWA_U71_dib240)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 13315 | +42.8% | +20109 | +17019 | -3201 | 30189/44597 | -19127/-17891 |
| L3M | 10841 | 16976 | +56.6% | +16721 | +13571 | -3243 | 30189/44597 | -15066/-21425 |
| HOLD | 27872 | 46587 | +67.1% | +9996 | +4317 | -5760 | 82017/93234 | -36787/-40024 |
| OLDER | 25599 | 19427 | -24.1% | +5291 | +5455 | +121 | 88502/52816 | -38412/-33648 |
| Y2023 | 17453 | 22150 | +26.9% | +2124 | +3077 | +928 | 40010/50734 | -17197/-18939 |
| Y2024 | 26429 | 18109 | -31.5% | +5049 | +5041 | -43 | 70704/52816 | -36802/-27553 |
| Y2025 | 30332 | 18265 | -39.8% | +8447 | +8106 | -409 | 88502/46651 | -27370/-22307 |
Controls L6M: 0 valid random-clock draws; real ulcer change +42.8% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +56.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -1156.0, 'K7': 4051.0, 'M7': 5689.0, 'O7': -1636.0, 'P7': 3202.0, 'U7': -91348.0}

### U7_1_vsess_600 (TL3_SWA_U71_vsess600)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 12514 | +34.2% | +20109 | +18802 | -1407 | 30189/46515 | -19127/-22218 |
| L3M | 10841 | 15864 | +46.3% | +16721 | +15313 | -1496 | 30189/46515 | -15066/-18601 |
| HOLD | 27872 | 58832 | +111.1% | +9996 | +1714 | -8368 | 82017/118499 | -36787/-48109 |
| OLDER | 25599 | 27616 | +7.9% | +5291 | +4273 | -1059 | 88502/77543 | -38412/-34097 |
| Y2023 | 17453 | 20349 | +16.6% | +2124 | +4301 | +2153 | 40010/52446 | -17197/-17998 |
| Y2024 | 26429 | 31564 | +19.4% | +5049 | +3097 | -1985 | 70704/77543 | -36802/-32290 |
| Y2025 | 30332 | 28020 | -7.6% | +8447 | +5662 | -2848 | 88502/68269 | -27370/-34406 |
Controls L6M: 0 valid random-clock draws; real ulcer change +34.2% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +46.3% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -1998.0, 'K7': 19407.0, 'M7': 19585.0, 'O7': 5057.0, 'P7': 1889.0, 'U7': -78279.0}

### U7_1_tib_700 (TL3_SWA_U71_tib700)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 14898 | +59.7% | +20109 | +18867 | -1329 | 30189/52926 | -19127/-23255 |
| L3M | 10841 | 19325 | +78.3% | +16721 | +15506 | -1289 | 30189/52926 | -15066/-27338 |
| HOLD | 27872 | 31225 | +12.0% | +9996 | +5942 | -4131 | 82017/68878 | -36787/-28780 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +59.7% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +78.3% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -2906.0, 'K7': 688.0, 'M7': 9330.0, 'O7': 965.0, 'P7': 2804.0, 'U7': -43515.0}

### U7_1_kagi_10 (TL3_SWA_U71_kagi10)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 12448 | +33.5% | +20109 | +20241 | +69 | 30189/47740 | -19127/-24281 |
| L3M | 10841 | 16205 | +49.5% | +16721 | +19236 | +2459 | 30189/47740 | -15066/-21748 |
| HOLD | 27872 | 19222 | -31.0% | +9996 | +8955 | -1108 | 82017/53678 | -36787/-25323 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +33.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +49.5% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -3129.0, 'K7': 4428.0, 'M7': 1271.0, 'O7': 3199.0, 'P7': 3214.0, 'U7': -5512.0}

### U7_1_tick_500 (TL3_SWA_U71_tick500)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9713 | +4.1% | +20109 | +19584 | -531 | 30189/32580 | -19127/-24745 |
| L3M | 10841 | 11617 | +7.2% | +16721 | +16678 | -47 | 30189/32580 | -15066/-17735 |
| HOLD | 27872 | 20691 | -25.8% | +9996 | +9494 | -507 | 82017/61438 | -36787/-23454 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +4.1% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +7.2% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 337.0, 'K7': 4656.0, 'M7': 7762.0, 'O7': 306.0, 'P7': -1043.0, 'U7': -25806.0}

### U7_1_tm1800 (TL3_SWA_U71_tm1800)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 8415 | -9.8% | +20109 | +21109 | +1014 | 30189/26260 | -19127/-20804 |
| L3M | 10841 | 9613 | -11.3% | +16721 | +19347 | +2636 | 30189/25780 | -15066/-13560 |
| HOLD | 27872 | 27510 | -1.3% | +9996 | +9257 | -721 | 82017/81905 | -36787/-35490 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -9.8% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -11.3% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 1113.0, 'K7': 23105.0, 'M7': 9007.0, 'O7': -2277.0, 'P7': -3179.0, 'U7': -1468.0}

### U7_1_cdr_160 (TL3_SWA_U71_cdr160)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9829 | +5.4% | +20109 | +19977 | -132 | 30189/30880 | -19127/-23981 |
| L3M | 10841 | 11518 | +6.2% | +16721 | +15927 | -791 | 30189/30880 | -15066/-16738 |
| HOLD | 27872 | 24615 | -11.7% | +9996 | +10330 | +335 | 82017/71648 | -36787/-33174 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change +5.4% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +6.2% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -1159.0, 'K7': -5515.0, 'M7': -3786.0, 'O7': 2871.0, 'P7': 575.0, 'U7': 3558.0}

### M7_1_tib_40000 (TL3_SWA_M71_tib40000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 8242 | -11.6% | +20109 | +21224 | +1167 | 30189/24600 | -19127/-18258 |
| L3M | 10841 | 9521 | -12.2% | +16721 | +17252 | +577 | 30189/24600 | -15066/-14889 |
| HOLD | 27872 | 22546 | -19.1% | +9996 | +9766 | -179 | 82017/62326 | -36787/-30894 |
| OLDER | not finished ||||||| |
| Y2023 | not finished ||||||| |
| Y2024 | not finished ||||||| |
| Y2025 | not finished ||||||| |
Controls L6M: 0 valid random-clock draws; real ulcer change -11.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -12.2% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': -1844.0, 'K7': 17121.0, 'M7': 10740.0, 'O7': -1762.0, 'P7': -1464.0, 'U7': 6518.0}

### K7_4_dib_40000 (TL3_SWA_K74_dib40000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9175 | -1.6% | +20109 | +20335 | +232 | 30189/28330 | -19127/-17330 |
| L3M | 10841 | 10418 | -3.9% | +16721 | +17903 | +1185 | 30189/28330 | -15066/-17009 |
| HOLD | 27872 | 28870 | +3.6% | +9996 | +9109 | -881 | 82017/85527 | -36787/-34040 |
| OLDER | 25599 | 25366 | -0.9% | +5291 | +4983 | -299 | 88502/79605 | -38412/-36802 |
| Y2023 | 17453 | 18859 | +8.1% | +2124 | +2102 | -13 | 40010/41498 | -17197/-18736 |
| Y2024 | 26429 | 29251 | +10.7% | +5049 | +4852 | -190 | 70704/67618 | -36802/-36802 |
| Y2025 | 30332 | 25449 | -16.1% | +8447 | +7748 | -691 | 88502/79605 | -27370/-32452 |
Controls L6M: 0 valid random-clock draws; real ulcer change -1.6% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change -3.9% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': 5957.0, 'M7': 0.0, 'O7': 0.0, 'P7': 0.0, 'U7': 0.0}

### K7_4_tib_40000 (TL3_SWA_K74_tib40000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9342 | +0.2% | +20109 | +20546 | +451 | 30189/31064 | -19127/-18618 |
| L3M | 10841 | 10851 | +0.1% | +16721 | +17168 | +461 | 30189/31064 | -15066/-16757 |
| HOLD | 27872 | 29103 | +4.4% | +9996 | +10001 | +21 | 82017/86526 | -36787/-35575 |
| OLDER | 25599 | 25203 | -1.5% | +5291 | +5132 | -146 | 88502/76244 | -38412/-39934 |
| Y2023 | 17453 | 19478 | +11.6% | +2124 | +1866 | -248 | 40010/42805 | -17197/-18665 |
| Y2024 | 26429 | 28167 | +6.6% | +5049 | +4989 | -47 | 70704/65191 | -36802/-36802 |
| Y2025 | 30332 | 25989 | -14.3% | +8447 | +8259 | -173 | 88502/76244 | -27370/-31453 |
Controls L6M: 0 valid random-clock draws; real ulcer change +0.2% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +0.1% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': 11496.0, 'M7': 0.0, 'O7': 0.0, 'P7': 0.0, 'U7': 0.0}

### M7_3_trb_15000 (TL3_SWA_M73_trb15000)

| window | JL3 ulcer | swap ulcer | ulcer change | JL3 USD/wk | swap USD/wk | $4.84 diff USD/wk | maxDD base/swap | worst week base/swap |
|---|---|---|---|---|---|---|---|---|
| L6M | 9327 | 9318 | -0.1% | +20109 | +19942 | -138 | 30189/31388 | -19127/-21394 |
| L3M | 10841 | 11077 | +2.2% | +16721 | +15857 | -841 | 30189/31388 | -15066/-15939 |
| HOLD | 27872 | 28699 | +3.0% | +9996 | +9527 | -443 | 82017/79737 | -36787/-29343 |
| OLDER | 25599 | 27491 | +7.4% | +5291 | +4850 | -417 | 88502/87848 | -38412/-33729 |
| Y2023 | 17453 | 16024 | -8.2% | +2124 | +2140 | +38 | 40010/36330 | -17197/-19304 |
| Y2024 | 26429 | 32488 | +22.9% | +5049 | +4053 | -970 | 70704/64141 | -36802/-33364 |
| Y2025 | 30332 | 29081 | -4.1% | +8447 | +8260 | -162 | 88502/87848 | -27370/-22613 |
Controls L6M: 0 valid random-clock draws; real ulcer change -0.1% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Controls L3M: 0 valid random-clock draws; real ulcer change +2.2% vs controls median +nan%, percentile (share of controls better or equal) nan (NOT FINISHED: < 30 valid draws)
Freed-book effects L6M (USD, swap minus JL3, per book): {'A7': 0.0, 'H7': 0.0, 'K7': -1206.0, 'M7': -1956.0, 'O7': 0.0, 'P7': -1212.0, 'U7': 0.0}
