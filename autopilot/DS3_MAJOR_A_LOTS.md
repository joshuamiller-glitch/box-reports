# DS3_MAJOR_A_LOTS: lot re-solve by book x session (W-MA, PART A)

1. Tried: 24 lot cells (K7 M7 U7 P7 H7 A7 x Asia/London/NY AM/NY PM, base lots 0..14, live = floor(1.75 x base + 0.5)) solved for min ulcer at mean >= today, max mean at ulcer <= today and a 10-point frontier, on a trade-list lot-scaling model of JL3, with walk-forward (trailing 12/6 months, hold 3), week-shuffled nulls, same-size random controls, a uniform trim/press benchmark (x0.5 ... x1.5) and exact engine runs.
2. The arithmetic model FAILS the additivity test (30 exact random vectors: median ulcer error 24%, the engine realises only ~49% of the arithmetic change in P&L), so every vector below is judged on exact JL3 engine runs, not on the arithmetic.
3. Holds: the in-sample gain (32% lower ulcer at equal mean) is mostly fit: shuffled-cell nulls give 46% on noise; walk-forward gain over the uniform benchmark is small (see section 5); proposed vector F2 = T6-F4, label BEST-AVAILABLE-NOT-PROVEN; vs uniform at equal mean / equal ulcer (exact, L6M / HOLD / all 43 mo): ulcer +19% / -23% / -9% and mean +68% / n/a / -10%.
4. Needs in DS7: a session lot table per book (panel setting, no new code); M7 London 0 is shown as a row (variant G = M7 London fixed 0, F = free); no live change until the exact JL3/JL2 and uniform comparison is read.
5. Next: stack cap / stack-cut variants on the best vector, JL2 exact runs, exact controls of the same size if the lead wants a calibrated tier, refresh every 30 min.

Header: trials counted ~1,400 integer lot vectors solved/evaluated by arithmetic (frontier 12 points x folds x 2 windows, 30 nulls, finals) + 30 random + 5 uniform + 6 final exact vectors; correction: none yet (first pass); PBO not computed; selection status: in-sample solve on landed months, WALK-FORWARD on the calibrated arithmetic, exact engine on 6 finals (3 on JL2); the final vectors are re-solved on the trailing window to 2026-10-31, so L6M/HOLD are NOT untouched for them (training window), only the walk-forward OOS days are. Data end 2026-10-31. FIRST PASS. Tiers CONFIRMED/LEAD: not issued (engine-exact same-size controls not run; the additivity test says the arithmetic controls cannot stand in).

Updated 2026-11-17 15:25Z UTC. Cell P&L landed for 43 months. Live vector today (live lots): K7 4,4,0,2,4,0; M7 0,4,0,2,0,0; U7 7,7,0,0,0,0; P7 12,7,0,7,0,0; H7 7,0,0,2,0,0; A7 2 Asia. O7 is not a decision variable (no session table in the engine; constant background in the arithmetic, in the engine runs unchanged).

## 1. Cell: lots today -> lots proposed (base/live; * = changed)

Proposed vector (package, judged jointly): **F2** (T6-F4). All finals are shown as columns. Variants F* = M7 London free, G* = M7 London fixed at 0. Rules: T12/T6 = trailing window, F0..F9 = frontier point (F0 = min ulcer at mean >= today in the window ... F9 = highest mean on the frontier), A = min ulcer at mean >= today, B = max mean at ulcer <= today.

| cell | today | F1 (T12-F6) | G1 (T12-F6) | F2 (T6-F4) | G2 (T6-F4) | F3 (T6-F5) | G3 (T6-F5) | H1 (INSAMPLE-A) | H2 (INSAMPLE-A) | H3 (INSAMPLE-F2) |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 Asia | 2/4 | 1/2 * | 2/4 | 1/2 * | 0/0 * | 2/4 | 2/4 | 0/0 * | 0/0 * | 0/0 * |
| K7 London | 2/4 | 2/4 | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 2/4 |
| K7 NY AM | 1/2 | 0/0 * | 0/0 * | 1/2 | 1/2 | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * |
| K7 NY PM | 2/4 | 3/5 * | 1/2 * | 0/0 * | 1/2 * | 1/2 * | 3/5 * | 1/2 * | 1/2 * | 0/0 * |
| M7 Asia | 0/0 | 4/7 * | 4/7 * | 3/5 * | 3/5 * | 3/5 * | 4/7 * | 0/0 | 0/0 | 0/0 |
| M7 London | 2/4 | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * |
| M7 NY AM | 1/2 | 3/5 * | 0/0 * | 0/0 * | 1/2 | 1/2 | 2/4 * | 1/2 | 1/2 | 1/2 |
| M7 NY PM | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 |
| U7 Asia | 4/7 | 1/2 * | 1/2 * | 3/5 * | 0/0 * | 0/0 * | 0/0 * | 3/5 * | 4/7 | 0/0 * |
| U7 London | 4/7 | 0/0 * | 0/0 * | 5/9 * | 0/0 * | 8/14 * | 5/9 * | 0/0 * | 0/0 * | 1/2 * |
| U7 NY AM | 0/0 | 0/0 | 0/0 | 3/5 * | 3/5 * | 4/7 * | 4/7 * | 0/0 | 0/0 | 0/0 |
| U7 NY PM | 0/0 | 0/0 | 0/0 | 3/5 * | 3/5 * | 3/5 * | 3/5 * | 0/0 | 1/2 * | 0/0 |
| P7 Asia | 7/12 | 6/11 * | 11/19 * | 7/12 | 11/19 * | 7/12 | 8/14 * | 10/18 * | 11/19 * | 14/25 * |
| P7 London | 4/7 | 7/12 * | 0/0 * | 6/11 * | 6/11 * | 6/11 * | 1/2 * | 0/0 * | 0/0 * | 0/0 * |
| P7 NY AM | 4/7 | 8/14 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 2/4 * | 2/4 * | 2/4 * |
| P7 NY PM | 0/0 | 3/5 * | 1/2 * | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 |
| H7 Asia | 4/7 | 0/0 * | 0/0 * | 3/5 * | 1/2 * | 3/5 * | 3/5 * | 2/4 * | 2/4 * | 6/11 * |
| H7 London | 0/0 | 3/5 * | 3/5 * | 0/0 | 1/2 * | 0/0 | 1/2 * | 0/0 | 0/0 | 0/0 |
| H7 NY AM | 1/2 | 0/0 * | 0/0 * | 3/5 * | 3/5 * | 3/5 * | 3/5 * | 0/0 * | 0/0 * | 0/0 * |
| H7 NY PM | 0/0 | 2/4 * | 4/7 * | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 |
| A7 Asia | 1/2 | 3/5 * | 3/5 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 2/4 * | 1/2 | 1/2 |
| A7 London | 0/0 | 4/7 * | 2/4 * | 3/5 * | 1/2 * | 3/5 * | 3/5 * | 0/0 | 0/0 | 0/0 |
| A7 NY AM | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 |
| A7 NY PM | 0/0 | 0/0 | 0/0 | 0/0 | 2/4 * | 4/7 * | 4/7 * | 0/0 | 0/0 | 0/0 |

Uniform benchmark vectors (base lots per cell, live rounding; integer base lots, so x0.67 = x0.75 on some cells): U050: 1 1 1 1 0 1 1 0 2 2 0 0 3 2 2 0 2 0 1 0 1 0 0 0; U067: 1 1 1 1 0 1 1 0 3 3 0 0 4 3 3 0 3 0 1 0 1 0 0 0; U075: 1 1 1 1 0 1 1 0 3 3 0 0 5 3 3 0 3 0 1 0 1 0 0 0; U125: 3 3 1 3 0 3 1 0 5 5 0 0 8 5 5 0 5 0 1 0 1 0 0 0; U150: 3 3 1 3 0 3 1 0 6 6 0 0 10 6 6 0 6 0 1 0 1 0 0 0

## 2. Exact engine (JL3), last 6 months first: today vs uniform trim/press vs finals

Columns: ulcer / max DD / worst week / mean per week at live lots with $4.84 round turn (primary), then mean at x1.75 live lots with the engine fee, mean at base lots (engine fee), mean at base lots with $4.84. Boot = week-clustered bootstrap (2,000) P(ulcer lower than today).

**L6M** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 19651 | -65865 | -33041 | 35826 | 37463 | 20109 | 19265 | +0.0% | +0.0% | - |
| U050 | 13966 | -39966 | -17195 | 25043 | 26374 | 13253 | 12585 | -28.9% | -30.1% | 0.96 |
| U067 | 18206 | -62954 | -28536 | 26835 | 28261 | 14480 | 13756 | -7.4% | -25.1% | 0.70 |
| U075 | 19919 | -67152 | -34793 | 29459 | 30964 | 16345 | 15571 | +1.4% | -17.8% | 0.55 |
| U125 | 20251 | -60915 | -43348 | 41489 | 43302 | 23492 | 22531 | +3.1% | +15.8% | 0.40 |
| U150 | 20117 | -55791 | -36027 | 45958 | 47896 | 26009 | 24970 | +2.4% | +28.3% | 0.70 |
| F1 | 34675 | -139511 | -62210 | 32329 | 34038 | 17660 | 16759 | +76.5% | -9.8% | 0.04 |
| G1 | 24455 | -83714 | -57710 | 44906 | 46416 | 24612 | 23803 | +24.4% | +25.3% | 0.37 |
| F2 | 16385 | -59747 | -50433 | 43846 | 45429 | 23979 | 23138 | -16.6% | +22.4% | 0.68 |
| G2 | 16659 | -60174 | -51547 | 48359 | 49985 | 26827 | 25963 | -15.2% | +35.0% | 0.65 |
| F3 | 20177 | -76989 | -68595 | 42499 | 44117 | 23458 | 22600 | +2.7% | +18.6% | 0.45 |
| G3 | 22807 | -82343 | -60714 | 41386 | 42994 | 22794 | 21945 | +16.1% | +15.5% | 0.49 |
| H1 | 21783 | -65021 | -29607 | 27653 | 28678 | 15476 | 14929 | +10.8% | -22.8% | 0.30 |
| H2 | 20136 | -63722 | -33263 | 36337 | 37412 | 20256 | 19681 | +2.5% | +1.4% | 0.34 |
| H3 | 16302 | -51330 | -32157 | 34800 | 36052 | 20363 | 19688 | -17.0% | -2.9% | 0.45 |

**L3M** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 23675 | -65865 | -33041 | 28903 | 30448 | 16721 | 15924 | +0.0% | +0.0% | - |
| U050 | 15878 | -39966 | -15521 | 20351 | 21561 | 10756 | 10148 | -32.9% | -29.6% | 0.95 |
| U067 | 23155 | -62954 | -28536 | 19899 | 21216 | 11192 | 10521 | -2.2% | -31.2% | 0.49 |
| U075 | 24418 | -67152 | -34793 | 21431 | 22834 | 12409 | 11686 | +3.1% | -25.9% | 0.46 |
| U125 | 21255 | -60915 | -32511 | 41139 | 42903 | 22880 | 21943 | -10.2% | +42.3% | 0.82 |
| U150 | 20404 | -55791 | -24820 | 45473 | 47367 | 25255 | 24239 | -13.8% | +57.3% | 0.97 |
| F1 | 45840 | -139511 | -62210 | 27729 | 29408 | 15258 | 14371 | +93.6% | -4.1% | 0.17 |
| G1 | 32293 | -83714 | -57710 | 31241 | 32692 | 17146 | 16367 | +36.4% | +8.1% | 0.32 |
| F2 | 20626 | -59747 | -50433 | 35236 | 36744 | 19354 | 18547 | -12.9% | +21.9% | 0.58 |
| G2 | 22059 | -60174 | -51547 | 36531 | 38101 | 20264 | 19425 | -6.8% | +26.4% | 0.55 |
| F3 | 25122 | -76989 | -68595 | 35578 | 37118 | 19669 | 18848 | +6.1% | +23.1% | 0.43 |
| G3 | 29683 | -82343 | -60714 | 32211 | 33735 | 17949 | 17143 | +25.4% | +11.4% | 0.44 |
| H1 | 28230 | -65021 | -29607 | 12926 | 13894 | 7959 | 7441 | +19.2% | -55.3% | 0.13 |
| H2 | 27055 | -63722 | -33263 | 20963 | 21971 | 12188 | 11646 | +14.3% | -27.5% | 0.05 |
| H3 | 20451 | -51330 | -32157 | 21330 | 22494 | 12875 | 12247 | -13.6% | -26.2% | 0.29 |

**HOLD** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 55227 | -155735 | -72626 | 18112 | 19402 | 9996 | 9332 | +0.0% | +0.0% | - |
| U050 | 45192 | -117367 | -63491 | 9958 | 10996 | 5619 | 5098 | -18.2% | -45.0% | 0.63 |
| U067 | 48686 | -116163 | -61025 | 12135 | 13250 | 6690 | 6123 | -11.8% | -33.0% | 0.63 |
| U075 | 54324 | -127426 | -62386 | 14386 | 15547 | 7696 | 7099 | -1.6% | -20.6% | 0.68 |
| U125 | 62433 | -157638 | -58113 | 18875 | 20310 | 10567 | 9805 | +13.0% | +4.2% | 0.44 |
| U150 | 62117 | -150157 | -63194 | 20679 | 22201 | 11936 | 11120 | +12.5% | +14.2% | 0.45 |
| F1 | 40945 | -141271 | -35418 | 23257 | 24621 | 13109 | 12386 | -25.9% | +28.4% | 0.92 |
| G1 | 45471 | -157459 | -94461 | 21374 | 22537 | 12586 | 11963 | -17.7% | +18.0% | 0.46 |
| F2 | 71774 | -205397 | -74309 | 18428 | 19680 | 10891 | 10221 | +30.0% | +1.7% | 0.40 |
| G2 | 78255 | -181111 | -83333 | 13146 | 14437 | 8482 | 7798 | +41.7% | -27.4% | 0.22 |
| F3 | 73978 | -199779 | -77573 | 15623 | 16945 | 9163 | 8458 | +34.0% | -13.7% | 0.29 |
| G3 | 81547 | -211750 | -77006 | 16549 | 17857 | 9719 | 9024 | +47.7% | -8.6% | 0.32 |
| H1 | 83165 | -208701 | -62605 | 7326 | 8100 | 4701 | 4288 | +50.6% | -59.6% | 0.23 |
| H2 | 70335 | -185757 | -82299 | 5359 | 6155 | 3712 | 3288 | +27.4% | -70.4% | 0.13 |
| H3 | 48620 | -132543 | -88981 | 10691 | 11622 | 6230 | 5728 | -12.0% | -41.0% | 0.23 |

**GAP** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 35577 | -86295 | -76769 | 15366 | 16229 | 8970 | 8525 | +0.0% | +0.0% | - |
| U050 | 35236 | -92635 | -72623 | 7251 | 7941 | 4124 | 3778 | -1.0% | -52.8% | 0.56 |
| U067 | 37576 | -99606 | -74704 | 7767 | 8518 | 4662 | 4280 | +5.6% | -49.5% | 0.42 |
| U075 | 37180 | -97099 | -70394 | 9104 | 9885 | 5555 | 5153 | +4.5% | -40.7% | 0.37 |
| U125 | 38169 | -96493 | -81670 | 21885 | 22878 | 12805 | 12277 | +7.3% | +42.4% | 0.26 |
| U150 | 39730 | -97734 | -85918 | 23792 | 24838 | 13820 | 13262 | +11.7% | +54.8% | 0.27 |
| F1 | 86585 | -184612 | -110642 | 8986 | 9936 | 5284 | 4782 | +143.4% | -41.5% | 0.01 |
| G1 | 76384 | -141151 | -83753 | 6946 | 7699 | 4366 | 3967 | +114.7% | -54.8% | 0.05 |
| F2 | 34392 | -79585 | -65113 | 8896 | 9738 | 5652 | 5204 | -3.3% | -42.1% | 0.28 |
| G2 | 36784 | -93929 | -85412 | 11353 | 12218 | 6809 | 6355 | +3.4% | -26.1% | 0.26 |
| F3 | 34146 | -96816 | -76725 | 12211 | 13125 | 7453 | 6967 | -4.0% | -20.5% | 0.32 |
| G3 | 32016 | -91656 | -78965 | 14161 | 15108 | 8535 | 8033 | -10.0% | -7.8% | 0.38 |
| H1 | 28322 | -70029 | -48445 | 15179 | 15669 | 8329 | 8071 | -20.4% | -1.2% | 0.93 |
| H2 | 23425 | -54073 | -45131 | 17134 | 17641 | 9526 | 9258 | -34.2% | +11.5% | 0.94 |
| H3 | 24330 | -51316 | -37992 | 15815 | 16388 | 9008 | 8698 | -31.6% | +2.9% | 0.73 |

**PRE** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 65848 | -178374 | -71328 | 11077 | 12145 | 6359 | 5811 | +0.0% | +0.0% | - |
| U050 | 37108 | -112999 | -41676 | 8752 | 9632 | 4819 | 4378 | -43.6% | -21.0% | 0.76 |
| U067 | 49173 | -138600 | -41511 | 9028 | 9966 | 5056 | 4581 | -25.3% | -18.5% | 0.74 |
| U075 | 54353 | -148270 | -40909 | 9087 | 10069 | 5326 | 4823 | -17.5% | -18.0% | 0.74 |
| U125 | 54834 | -160561 | -69063 | 13645 | 14867 | 8135 | 7490 | -16.7% | +23.2% | 0.47 |
| U150 | 57989 | -139254 | -77866 | 15468 | 16745 | 9269 | 8590 | -11.9% | +39.6% | 0.44 |
| F1 | 92824 | -264759 | -56650 | 8907 | 10078 | 5414 | 4797 | +41.0% | -19.6% | 0.23 |
| G1 | 49110 | -174808 | -65638 | 14402 | 15336 | 8486 | 7989 | -25.4% | +30.0% | 0.68 |
| F2 | 63471 | -205717 | -74811 | 10738 | 11757 | 6216 | 5672 | -3.6% | -3.1% | 0.57 |
| G2 | 60772 | -159529 | -65137 | 9326 | 10398 | 5768 | 5203 | -7.7% | -15.8% | 0.42 |
| F3 | 87287 | -242989 | -67425 | 7813 | 8931 | 4844 | 4250 | +32.6% | -29.5% | 0.37 |
| G3 | 75575 | -245034 | -66204 | 12031 | 13174 | 7105 | 6499 | +14.8% | +8.6% | 0.42 |
| H1 | 26161 | -96167 | -48962 | 11338 | 11948 | 6361 | 6038 | -60.3% | +2.4% | 0.84 |
| H2 | 36156 | -127985 | -59424 | 11578 | 12212 | 6572 | 6236 | -45.1% | +4.5% | 0.75 |
| H3 | 33179 | -83010 | -39230 | 12011 | 12729 | 7226 | 6840 | -49.6% | +8.4% | 0.94 |

**X'** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 45533 | -136464 | -72178 | 5390 | 6137 | 3241 | 2857 | +0.0% | +0.0% | - |
| U050 | 33320 | -107950 | -58226 | 4414 | 5023 | 2523 | 2218 | -26.8% | -18.1% | 0.86 |
| U067 | 39865 | -115749 | -50990 | 4668 | 5325 | 2739 | 2405 | -12.4% | -13.4% | 0.77 |
| U075 | 38243 | -115341 | -60920 | 4748 | 5429 | 2825 | 2476 | -16.0% | -11.9% | 0.79 |
| U125 | 45335 | -170813 | -93753 | 6929 | 7786 | 4246 | 3793 | -0.4% | +28.6% | 0.35 |
| U150 | 49154 | -161375 | -93347 | 7602 | 8503 | 4600 | 4120 | +8.0% | +41.0% | 0.29 |
| F1 | 87118 | -189677 | -77737 | 3202 | 4026 | 2314 | 1879 | +91.3% | -40.6% | 0.08 |
| G1 | 114471 | -229681 | -86739 | 3129 | 3765 | 2061 | 1725 | +151.4% | -42.0% | 0.14 |
| F2 | 49373 | -115441 | -53410 | 3987 | 4708 | 2452 | 2068 | +8.4% | -26.0% | 0.25 |
| G2 | 39394 | -98795 | -55756 | 7195 | 7971 | 4078 | 3673 | -13.5% | +33.5% | 0.68 |
| F3 | 105585 | -254040 | -53357 | 2697 | 3529 | 1900 | 1458 | +131.9% | -50.0% | 0.09 |
| G3 | 70279 | -211795 | -86172 | 4700 | 5567 | 2936 | 2476 | +54.3% | -12.8% | 0.13 |
| H1 | 42533 | -92183 | -40720 | 3889 | 4324 | 2310 | 2082 | -6.6% | -27.8% | 0.66 |
| H2 | 38270 | -94995 | -32640 | 4510 | 4963 | 2649 | 2411 | -16.0% | -16.3% | 0.70 |

**ALL43** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 49721 | -178374 | -76769 | 14107 | 15137 | 8022 | 7493 | +0.0% | +0.0% | - |
| U050 | 34984 | -117367 | -72623 | 9541 | 10380 | 5232 | 4811 | -29.6% | -32.4% | 0.83 |
| U067 | 41255 | -138600 | -74704 | 10531 | 11433 | 5859 | 5401 | -17.0% | -25.3% | 0.76 |
| U075 | 42847 | -148270 | -70394 | 11417 | 12357 | 6462 | 5980 | -13.8% | -19.1% | 0.75 |
| U125 | 57372 | -182466 | -103087 | 16594 | 17759 | 9649 | 9032 | +15.4% | +17.6% | 0.27 |
| U150 | 63038 | -239915 | -98776 | 18045 | 19274 | 10518 | 9861 | +26.8% | +27.9% | 0.28 |
| F1 | 81619 | -264759 | -110642 | 11972 | 13085 | 6986 | 6398 | +64.2% | -15.1% | 0.07 |
| G1 | 83397 | -229681 | -94461 | 14731 | 15641 | 8483 | 7999 | +67.7% | +4.4% | 0.18 |
| F2 | 53075 | -205717 | -74811 | 13672 | 14664 | 7832 | 7304 | +6.7% | -3.1% | 0.31 |
| G2 | 49764 | -181111 | -85412 | 14810 | 15851 | 8560 | 8012 | +0.1% | +5.0% | 0.43 |
| F3 | 88433 | -254040 | -77573 | 12040 | 13121 | 7057 | 6483 | +77.9% | -14.7% | 0.10 |
| G3 | 72741 | -245034 | -86172 | 13749 | 14850 | 7953 | 7369 | +46.3% | -2.5% | 0.14 |
| H1 | 45605 | -208701 | -62605 | 10400 | 11010 | 5945 | 5622 | -8.3% | -26.3% | 0.60 |
| H2 | 41535 | -185757 | -82299 | 11928 | 12562 | 6819 | 6483 | -16.5% | -15.4% | 0.61 |

## 3. Beats the uniform benchmark? (exact JL3; uniform ray = today and U050..U150 interpolated)

| vector | window | ulcer | mean | uniform ulcer at the SAME mean | uniform mean at the SAME ulcer | ulcer advantage at equal mean | mean advantage at equal ulcer |
|---|---|---|---|---|---|---|---|
| F1 | L6M | 34675 | 32329 | 19798 | out of range | -75.1% | - |
| F1 | L3M | 45840 | 27729 | 23792 | out of range | -92.7% | - |
| F1 | HOLD | 40945 | 23257 | out of range | out of range | - | - |
| F1 | GAP | 86585 | 8986 | 37215 | out of range | -132.7% | - |
| F1 | PRE | 92824 | 8907 | 43872 | out of range | -111.6% | - |
| F1 | X' | 87118 | 3202 | out of range | out of range | - | - |
| F1 | ALL43 | 81619 | 11972 | 44265 | out of range | -84.4% | - |
| G1 | L6M | 24455 | 44906 | 20148 | out of range | -21.4% | - |
| G1 | L3M | 32293 | 31241 | 23213 | out of range | -39.1% | - |
| G1 | HOLD | 45471 | 21374 | out of range | 10132 | - | +111.0% |
| G1 | GAP | 76384 | 6946 | out of range | out of range | - | - |
| G1 | PRE | 49110 | 14402 | 56144 | 9027 | +12.5% | +59.5% |
| G1 | X' | 114471 | 3129 | out of range | out of range | - | - |
| G1 | ALL43 | 83397 | 14731 | 51639 | out of range | -61.5% | - |
| F2 | L6M | 16385 | 43846 | 20180 | 26066 | +18.8% | +68.2% |
| F2 | L3M | 20626 | 35236 | 22423 | 44342 | +8.0% | -20.5% |
| F2 | HOLD | 71774 | 18428 | 58214 | out of range | -23.3% | - |
| F2 | GAP | 34392 | 8896 | 37242 | out of range | +7.7% | - |
| F2 | PRE | 63471 | 10738 | 63890 | 12405 | +0.7% | -13.4% |
| F2 | X' | 49373 | 3987 | out of range | out of range | - | - |
| F2 | ALL43 | 53075 | 13672 | 48610 | 15197 | -9.2% | -10.0% |
| G2 | L6M | 16659 | 48359 | out of range | 26181 | - | +84.7% |
| G2 | L3M | 22059 | 36531 | 22167 | 32156 | +0.5% | +13.6% |
| G2 | HOLD | 78255 | 13146 | 51218 | out of range | -52.8% | - |
| G2 | GAP | 36784 | 11353 | 36604 | 10652 | -0.5% | +6.6% |
| G2 | PRE | 60772 | 9326 | 55731 | 13913 | -9.0% | -33.0% |
| G2 | X' | 39394 | 7195 | 46842 | 4691 | +15.9% | +53.4% |
| G2 | ALL43 | 49764 | 14810 | 51883 | 14121 | +4.1% | +4.9% |
| F3 | L6M | 20177 | 42499 | 20220 | 43937 | +0.2% | -3.3% |
| F3 | L3M | 25122 | 35578 | 22355 | out of range | -12.4% | - |
| F3 | HOLD | 73978 | 15623 | 54623 | out of range | -35.4% | - |
| F3 | GAP | 34146 | 12211 | 36384 | out of range | +6.2% | - |
| F3 | PRE | 87287 | 7813 | out of range | out of range | - | - |
| F3 | X' | 105585 | 2697 | out of range | out of range | - | - |
| F3 | ALL43 | 88433 | 12040 | 44440 | out of range | -99.0% | - |
| G3 | L6M | 22807 | 41386 | 20240 | out of range | -12.7% | - |
| G3 | L3M | 29683 | 32211 | 23021 | out of range | -28.9% | - |
| G3 | HOLD | 81547 | 16549 | 54848 | out of range | -48.7% | - |
| G3 | GAP | 32016 | 14161 | 35885 | out of range | +10.8% | - |
| G3 | PRE | 75575 | 12031 | 61758 | out of range | -22.4% | - |
| G3 | X' | 70279 | 4700 | 39208 | out of range | -79.2% | - |
| G3 | ALL43 | 72741 | 13749 | 48807 | out of range | -49.0% | - |
| H1 | L6M | 21783 | 27653 | 18740 | out of range | -16.2% | - |
| H1 | L3M | 28230 | 12926 | out of range | out of range | - | - |
| H1 | HOLD | 83165 | 7326 | out of range | out of range | - | - |
| H1 | GAP | 28322 | 15179 | 35624 | out of range | +20.5% | - |
| H1 | PRE | 26161 | 11338 | 64731 | out of range | +59.6% | - |
| H1 | X' | 42533 | 3889 | out of range | 5771 | - | -32.6% |
| H1 | ALL43 | 45605 | 10400 | 40423 | 12496 | -12.8% | -16.8% |
| H2 | L6M | 20136 | 36337 | 19705 | 45334 | -2.2% | -19.8% |
| H2 | L3M | 27055 | 20963 | 20717 | out of range | -30.6% | - |
| H2 | HOLD | 70335 | 5359 | out of range | out of range | - | - |
| H2 | GAP | 23425 | 17134 | 36280 | out of range | +35.4% | - |
| H2 | PRE | 36156 | 11578 | 63701 | out of range | +43.2% | - |
| H2 | X' | 38270 | 4510 | 35783 | 4747 | -7.0% | -5.0% |
| H2 | ALL43 | 41535 | 11928 | 44153 | 10687 | +5.9% | +11.6% |
| H3 | L6M | 16302 | 34800 | 19694 | 26031 | +17.2% | +33.7% |
| H3 | L3M | 20451 | 21330 | 23622 | 45234 | +13.4% | -52.8% |
| H3 | HOLD | 48620 | 10691 | 46368 | 12094 | -4.9% | -11.6% |
| H3 | GAP | 24330 | 15815 | 35755 | out of range | +32.0% | - |
| H3 | PRE | 33179 | 12011 | 61845 | out of range | +46.4% | - |

Positive = better than just trading smaller/bigger. "out of range" = the vector sits outside the measured uniform ray (no extrapolation).

## 4. Exact engine on JL2 (live-equivalent stack without the persist=1 profit lines)

**L6M** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 18729 | -55033 | -28790 | 39669 | 41251 | 22076 | 21261 | +0.0% | +0.0% | - |
| F1 | 38519 | -146879 | -40765 | 41479 | 43148 | 22450 | 21570 | +105.7% | +4.6% | 0.07 |
| F2 | 18271 | -72211 | -53630 | 49473 | 51010 | 27081 | 26263 | -2.4% | +24.7% | 0.52 |
| F3 | 23049 | -90174 | -72608 | 48621 | 50192 | 26692 | 25859 | +23.1% | +22.6% | 0.38 |

**L3M** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 22892 | -55033 | -28790 | 30558 | 32044 | 17566 | 16800 | +0.0% | +0.0% | - |
| F1 | 52570 | -146879 | -40765 | 32140 | 33771 | 17456 | 16595 | +129.6% | +5.2% | 0.17 |
| F2 | 23425 | -72211 | -53630 | 36214 | 37675 | 20121 | 19341 | +2.3% | +18.5% | 0.46 |
| F3 | 30024 | -90174 | -72608 | 34517 | 35996 | 19175 | 18388 | +31.2% | +13.0% | 0.28 |

**HOLD** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 47535 | -140077 | -61474 | 14844 | 16092 | 8359 | 7716 | +0.0% | +0.0% | - |
| F1 | 36986 | -140397 | -56546 | 21511 | 22837 | 12231 | 11526 | -22.2% | +44.9% | 0.85 |
| F2 | 53785 | -158699 | -61736 | 17952 | 19152 | 10660 | 10017 | +13.1% | +20.9% | 0.60 |
| F3 | 61397 | -189850 | -65475 | 15546 | 16815 | 9271 | 8595 | +29.2% | +4.7% | 0.50 |

**GAP** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 43185 | -114581 | -85624 | 12912 | 13746 | 7592 | 7162 | +0.0% | +0.0% | - |
| F1 | 90402 | -202527 | -126720 | 9049 | 9952 | 5376 | 4900 | +109.3% | -29.9% | 0.01 |
| F2 | 35795 | -82170 | -69545 | 9424 | 10229 | 6021 | 5594 | -17.1% | -27.0% | 0.35 |
| F3 | 42466 | -124868 | -80378 | 12715 | 13595 | 7462 | 6995 | -1.7% | -1.5% | 0.36 |

**PRE** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 52451 | -144128 | -55528 | 12672 | 13701 | 7157 | 6630 | +0.0% | +0.0% | - |
| F1 | 82042 | -241585 | -65197 | 11910 | 13045 | 6914 | 6315 | +56.4% | -6.0% | 0.15 |
| F2 | 46056 | -159070 | -69704 | 13497 | 14472 | 7543 | 7023 | -12.2% | +6.5% | 0.53 |
| F3 | 73862 | -210153 | -71934 | 12522 | 13605 | 7205 | 6630 | +40.8% | -1.2% | 0.37 |

**X'** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 38065 | -144400 | -73286 | 8250 | 8972 | 4752 | 4382 | +0.0% | +0.0% | - |
| F1 | 77648 | -182590 | -81395 | 5253 | 6051 | 3327 | 2906 | +104.0% | -36.3% | 0.04 |
| F2 | 45967 | -112690 | -54123 | 6137 | 6833 | 3673 | 3302 | +20.8% | -25.6% | 0.24 |
| F3 | 109097 | -272732 | -52533 | 4003 | 4814 | 2713 | 2282 | +186.6% | -51.5% | 0.04 |

**ALL43** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 41508 | -144400 | -85624 | 15586 | 16580 | 8796 | 8285 | +0.0% | +0.0% | - |
| F1 | 76723 | -241585 | -126720 | 14729 | 15808 | 8394 | 7824 | +84.8% | -5.5% | 0.03 |
| F2 | 44366 | -159070 | -69704 | 16025 | 16980 | 9110 | 8601 | +6.9% | +2.8% | 0.37 |
| F3 | 84739 | -272732 | -80378 | 14537 | 15585 | 8402 | 7845 | +104.1% | -6.7% | 0.09 |

## 5. Walk-forward (calibrated arithmetic, theta=0.49): solve on trailing T months, hold the next 3, roll; OOS days only

**trailing 12 months** (OOS days 20240401..20261031, 944 days; uniform points computed on the same days)

| rule | OOS ulcer | OOS max DD | OOS worst week | OOS mean $/wk | d ulcer vs today | d mean vs today | uniform ulcer at same mean | advantage |
|---|---|---|---|---|---|---|---|---|
| TODAY | 50830 | -178374 | -76769 | 17948 | | | | |
| A | 34803 | -116230 | -68059 | 15020 | -31.5% | -16.3% | out of range | - |
| F0 | 38817 | -109214 | -67709 | 14108 | -23.6% | -21.4% | out of range | - |
| F1 | 38749 | -108739 | -72950 | 14691 | -23.8% | -18.1% | out of range | - |
| F2 | 46444 | -141219 | -69258 | 14851 | -8.6% | -17.3% | out of range | - |
| F3 | 45122 | -148632 | -76085 | 16448 | -11.2% | -8.4% | 48082 | +6.2% |
| F4 | 43086 | -123856 | -81657 | 17174 | -15.2% | -4.3% | 49413 | +12.8% |
| F5 | 48132 | -155603 | -94134 | 17921 | -5.3% | -0.1% | 50781 | +5.2% |
| F6 | 52964 | -159610 | -84842 | 18635 | +4.2% | +3.8% | 55403 | +4.4% |
| F7 | 63630 | -209179 | -93567 | 20797 | +25.2% | +15.9% | 67633 | +5.9% |
| F8 | 71250 | -224643 | -123972 | 21417 | +40.2% | +19.3% | out of range | - |
| F9 | 77475 | -260312 | -134537 | 22876 | +52.4% | +27.5% | out of range | - |
| B | 70754 | -241489 | -125358 | 22976 | +39.2% | +28.0% | out of range | - |

**trailing 6 months** (OOS days 20231001..20261031, 1127 days; uniform points computed on the same days)

| rule | OOS ulcer | OOS max DD | OOS worst week | OOS mean $/wk | d ulcer vs today | d mean vs today | uniform ulcer at same mean | advantage |
|---|---|---|---|---|---|---|---|---|
| TODAY | 51471 | -178374 | -76769 | 16046 | | | | |
| A | 36816 | -131088 | -69135 | 12828 | -28.5% | -20.1% | out of range | - |
| F0 | 37008 | -134140 | -69135 | 12629 | -28.1% | -21.3% | out of range | - |
| F1 | 39370 | -132847 | -75478 | 13216 | -23.5% | -17.6% | out of range | - |
| F2 | 38120 | -137867 | -67009 | 14615 | -25.9% | -8.9% | 47748 | +20.2% |
| F3 | 41725 | -139523 | -74667 | 14472 | -18.9% | -9.8% | 47375 | +11.9% |
| F4 | 44502 | -154574 | -90551 | 15088 | -13.5% | -6.0% | 48978 | +9.1% |
| F5 | 47694 | -152403 | -87439 | 16069 | -7.3% | +0.1% | 51612 | +7.6% |
| F6 | 49962 | -165042 | -85338 | 17829 | -2.9% | +11.1% | 62412 | +19.9% |
| F7 | 55630 | -185976 | -101520 | 17912 | +8.1% | +11.6% | 62923 | +11.6% |
| F8 | 67911 | -227733 | -120306 | 19182 | +31.9% | +19.5% | 67876 | -0.1% |
| F9 | 67469 | -244614 | -122836 | 20964 | +31.1% | +30.6% | out of range | - |
| B | 71205 | -244614 | -123067 | 20268 | +38.3% | +26.3% | out of range | - |

## 6. In-sample frontier (calibrated arithmetic, 43 landed months 202304..202610; FIT, not evidence)

Today: ulcer 49721, mean 14107 per week (live lots, $4.84).

| point | ulcer | mean | vector (24 cells: K7 AL-NA-NQ.. in cell order) |
|---|---|---|---|
| A | 33674 | 14184 | 1 0 0 0 1 0 1 0 1 0 0 0 6 0 0 0 2 3 0 0 2 0 0 1 |
| F0 | 34260 | 14127 | 2 0 0 1 0 0 1 0 1 0 0 0 9 0 0 0 0 0 1 0 2 0 0 0 |
| F1 | 36007 | 14795 | 2 0 0 2 2 0 1 0 1 0 0 0 7 0 0 0 3 0 0 0 1 0 0 0 |
| F2 | 35256 | 15381 | 1 0 0 0 3 0 0 0 1 0 0 0 8 0 0 0 1 2 0 0 2 0 0 1 |
| F3 | 39851 | 15936 | 2 3 0 2 0 0 1 0 1 0 0 1 8 0 4 0 6 0 1 1 2 0 0 0 |
| F4 | 38707 | 16534 | 0 1 0 0 2 0 0 0 1 0 0 0 13 0 0 0 2 0 0 0 3 0 2 1 |
| F5 | 43687 | 17161 | 4 0 0 0 3 0 1 0 1 5 0 0 7 0 8 0 2 1 0 0 2 0 0 3 |
| F6 | 45661 | 17745 | 2 2 0 4 0 0 1 0 3 2 0 3 14 0 6 0 3 3 0 0 1 0 0 0 |
| F7 | 48039 | 18346 | 2 4 0 4 0 0 2 0 4 0 0 3 12 0 4 0 3 0 2 1 2 0 0 4 |
| F8 | 45759 | 18953 | 2 2 0 0 1 0 3 0 3 6 0 0 14 0 5 0 2 3 0 0 2 0 0 2 |
| F9 | 54081 | 19572 | 4 0 0 4 3 0 3 0 1 8 0 0 7 0 6 0 6 3 0 0 2 0 1 4 |
| B | 49630 | 19553 | 4 4 0 2 0 0 3 0 4 0 0 1 12 0 0 0 3 4 2 0 3 0 0 4 |

## 7. Nulls and controls

Week-block shuffles of each cell P&L (independent per cell, 30): the same solve (min ulcer at mean >= today) finds on average **46%** lower ulcer on pure noise (real data: 32%); max-mean at ulcer <= today finds +47% mean on noise. So the in-sample gain is about 100% fit.

30 random vectors of the same total lots as the in-sample A vector: ulcer median 44320 (range 35791..54042), mean median 10931; A: ulcer 33674, mean 14184; today 49721 / 14107.

## 8. Additivity test (30 exact random vectors TL3_MA_R01..R30, L14M, live lots $4.84)

model = arithmetic lot-scaling of the JL3/ADD trade lists (uncalibrated); engine = exact run. Median ulcer error 24%, max 113%; median mean overstatement 34%; median daily RMS error 55% of the engine daily RMS. Over the 10% threshold, so the engine is in the loop (finals exact) and the arithmetic is damped by theta = 0.49 (NNLS of engine change on model change, leave-one-vector-out ulcer error 13%).

| vector | ulcer engine | ulcer model | error | mean engine | mean model |
|---|---|---|---|---|---|
| TL3_MA_R01 | 40930 | 58885 | 44% | 35083 | 44925 |
| TL3_MA_R02 | 48588 | 40812 | 16% | 23227 | 31918 |
| TL3_MA_R03 | 43222 | 51154 | 18% | 27719 | 33216 |
| TL3_MA_R04 | 45426 | 74486 | 64% | 41408 | 57753 |
| TL3_MA_R05 | 62208 | 74626 | 20% | 25391 | 35499 |
| TL3_MA_R06 | 40342 | 48696 | 21% | 29086 | 41375 |
| TL3_MA_R07 | 101728 | 78623 | 23% | 20986 | 28082 |
| TL3_MA_R08 | 83876 | 72896 | 13% | 34227 | 51638 |
| TL3_MA_R09 | 50244 | 54590 | 9% | 14976 | 21022 |
| TL3_MA_R10 | 32250 | 68584 | 113% | 35536 | 42118 |
| TL3_MA_R11 | 45889 | 69663 | 52% | 12481 | 24709 |
| TL3_MA_R12 | 50052 | 78718 | 57% | 33479 | 42875 |
| TL3_MA_R13 | 34929 | 58077 | 66% | 22734 | 25163 |
| TL3_MA_R14 | 27284 | 27715 | 2% | 25693 | 29772 |
| TL3_MA_R15 | 80533 | 65180 | 19% | 31626 | 41777 |
| TL3_MA_R16 | 52229 | 77840 | 49% | 36711 | 53806 |
| TL3_MA_R17 | 53017 | 55808 | 5% | 32700 | 44190 |
| TL3_MA_R18 | 58817 | 83862 | 43% | 34229 | 45373 |
| TL3_MA_R19 | 71626 | 90036 | 26% | 18765 | 28243 |
| TL3_MA_R20 | 57894 | 64070 | 11% | 25816 | 42052 |
| TL3_MA_R21 | 55825 | 65912 | 18% | 26728 | 35823 |
| TL3_MA_R22 | 52295 | 65701 | 26% | 32696 | 41946 |
| TL3_MA_R23 | 63465 | 65588 | 3% | 20198 | 31785 |
| TL3_MA_R24 | 54671 | 59011 | 8% | 22025 | 26716 |
| TL3_MA_R25 | 39400 | 50201 | 27% | 25867 | 26227 |
| TL3_MA_R26 | 43686 | 55633 | 27% | 21276 | 25638 |
| TL3_MA_R27 | 59915 | 81762 | 36% | 31088 | 45537 |
| TL3_MA_R28 | 61775 | 73798 | 19% | 14897 | 18990 |
| TL3_MA_R29 | 42386 | 59208 | 40% | 17217 | 22997 |
| TL3_MA_R30 | 34613 | 53576 | 55% | 17931 | 23061 |

## 9. Freed-book effects (exact JL3, proposed vector F2 vs today, mean $/wk per book, live lots $4.84)

| window | K7 | M7 | U7 | P7 | H7 | A7 | O7 | peak concurrent live lots today -> proposed |
|---|---|---|---|---|---|---|---|---|
| L6M | 5849 -> 5435 | 122 -> 12487 | 3780 -> 4513 | 20583 -> 18008 | 3351 -> 3735 | 1324 -> -1089 | 817 -> 758 | 36 -> 34 |
| HOLD | 6237 -> 1032 | -175 -> 7389 | 1291 -> 1086 | 8778 -> 8934 | -1025 -> -585 | 1379 -> -1094 | 1626 -> 1667 | 36 -> 34 |
| ALL43 | 3861 -> 1813 | -125 -> 3841 | 1358 -> 1637 | 5212 -> 4882 | 1612 -> 1610 | 1311 -> -996 | 879 -> 884 | 36 -> 34 |

## Stack cap / stack cut variants on F2 (exact JL3, last 14 months 2025-09..2026-10, live lots $4.84)

Live = London same-side cap 6 (truncate) + Asia-only 50% stack cut. C4/C8/C12/CNO = London cap 4/8/12/none; SCOFF = stack cut off; SCALL = stack cut in every session. Last column = ulcer change vs the proposed vector with the live cap/cut. The 50% share itself is not a switch in the engine (only off / Asia / all).

| variant | ulcer | max DD | worst week | mean $/wk | d ulcer vs live cap/cut |
|---|---|---|---|---|---|
| C4 | 0/14 months landed | | | | |
| C8 | 0/14 months landed | | | | |
| C12 | 0/14 months landed | | | | |
| CNO | 0/14 months landed | | | | |
| SCOFF | 0/14 months landed | | | | |
| SCALL | 0/14 months landed | | | | |


## 10. Caveats

- Today-zero cells (U7 NY AM/PM, M7 Asia/NY PM, P7 NY PM, H7 London/NY PM, A7 London/NY AM/NY PM) are scaled from one 2-lot add-one engine run each; solves are limited to 4 base lots there and to 2x today (min today+2) elsewhere, because the arithmetic is not additive.
- O7 fixed. K7/M7/U7/P7/H7/A7 pre-market and close tables unchanged.
- Stack cap (London same-side 6) and the 50% Asia stack cut are held at live in sections 1-9; variants: see the stack section when present.
- Selection of the final rules used the walk-forward on the calibrated arithmetic; the exact runs are the judgement.
