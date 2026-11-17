# DS3_MAJOR_A_LOTS: lot re-solve by book x session (W-MA, PART A)

1. Tried: 24 lot cells (K7 M7 U7 P7 H7 A7 x Asia/London/NY AM/NY PM, base lots 0..14, live = floor(1.75 x base + 0.5)) solved for min ulcer at mean >= today, max mean at ulcer <= today and a 10-point frontier, on a trade-list lot-scaling model of JL3, with walk-forward (trailing 12/6 months, hold 3), week-shuffled nulls, same-size random controls, a uniform trim/press benchmark (x0.5 ... x1.5) and exact engine runs.
2. The arithmetic model FAILS the additivity test (30 exact random vectors: median ulcer error 24%, the engine realises only ~49% of the arithmetic change in P&L), so every vector below is judged on exact JL3 engine runs, not on the arithmetic.
3. Holds: in-sample gain 35% lower ulcer at equal mean, but week-shuffled nulls give 49% on noise; exact runs of the finals and the uniform benchmark are still landing; interim vector G1 (arithmetic) labelled BEST-AVAILABLE-NOT-PROVEN.
4. Needs in DS7: a session lot table per book (panel setting, no new code); M7 London 0 is shown as a row (variant G = M7 London fixed 0, F = free); no live change until the exact JL3/JL2 and uniform comparison is read.
5. Next: stack cap / stack-cut variants on the best vector, JL2 exact runs, exact controls of the same size if the lead wants a calibrated tier, refresh every 30 min.

Header: trials counted ~1,400 integer lot vectors solved/evaluated by arithmetic (frontier 12 points x folds x 2 windows, 30 nulls, finals) + 30 random + 5 uniform + 6 final exact vectors; correction: none yet (first pass); PBO not computed; selection status: in-sample solve on landed months, WALK-FORWARD on the calibrated arithmetic, exact engine on 6 finals (3 on JL2); the final vectors are re-solved on the trailing window to 2026-10-31, so L6M/HOLD are NOT untouched for them (training window), only the walk-forward OOS days are. Data end 2026-10-31. FIRST PASS. Tiers CONFIRMED/LEAD: not issued (engine-exact same-size controls not run; the additivity test says the arithmetic controls cannot stand in).

Updated 2026-11-17 14:54Z UTC. Cell P&L landed for 39 months. Live vector today (live lots): K7 4,4,0,2,4,0; M7 0,4,0,2,0,0; U7 7,7,0,0,0,0; P7 12,7,0,7,0,0; H7 7,0,0,2,0,0; A7 2 Asia. O7 is not a decision variable (no session table in the engine; constant background in the arithmetic, in the engine runs unchanged).

## 1. Cell: lots today -> lots proposed (base/live; * = changed)

Proposed vector (package, judged jointly): **G1** (T12-F6, M7 London 0). All finals are shown as columns. Variants F* = M7 London free, G* = M7 London fixed at 0. Rules: T12/T6 = trailing window, F0..F9 = frontier point (F0 = min ulcer at mean >= today in the window ... F9 = highest mean on the frontier), A = min ulcer at mean >= today, B = max mean at ulcer <= today.

| cell | today | F1 (T12-F6) | G1 (T12-F6) | F2 (T6-F4) | G2 (T6-F4) | F3 (T6-F5) | G3 (T6-F5) |
|---|---|---|---|---|---|---|---|
| K7 Asia | 2/4 | 1/2 * | 2/4 | 1/2 * | 0/0 * | 2/4 | 2/4 |
| K7 London | 2/4 | 2/4 | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * |
| K7 NY AM | 1/2 | 0/0 * | 0/0 * | 1/2 | 1/2 | 0/0 * | 0/0 * |
| K7 NY PM | 2/4 | 3/5 * | 1/2 * | 0/0 * | 1/2 * | 1/2 * | 3/5 * |
| M7 Asia | 0/0 | 4/7 * | 4/7 * | 3/5 * | 3/5 * | 3/5 * | 4/7 * |
| M7 London | 2/4 | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * |
| M7 NY AM | 1/2 | 3/5 * | 0/0 * | 0/0 * | 1/2 | 1/2 | 2/4 * |
| M7 NY PM | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 |
| U7 Asia | 4/7 | 1/2 * | 1/2 * | 3/5 * | 0/0 * | 0/0 * | 0/0 * |
| U7 London | 4/7 | 0/0 * | 0/0 * | 5/9 * | 0/0 * | 8/14 * | 5/9 * |
| U7 NY AM | 0/0 | 0/0 | 0/0 | 3/5 * | 3/5 * | 4/7 * | 4/7 * |
| U7 NY PM | 0/0 | 0/0 | 0/0 | 3/5 * | 3/5 * | 3/5 * | 3/5 * |
| P7 Asia | 7/12 | 6/11 * | 11/19 * | 7/12 | 11/19 * | 7/12 | 8/14 * |
| P7 London | 4/7 | 7/12 * | 0/0 * | 6/11 * | 6/11 * | 6/11 * | 1/2 * |
| P7 NY AM | 4/7 | 8/14 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * |
| P7 NY PM | 0/0 | 3/5 * | 1/2 * | 0/0 | 0/0 | 0/0 | 0/0 |
| H7 Asia | 4/7 | 0/0 * | 0/0 * | 3/5 * | 1/2 * | 3/5 * | 3/5 * |
| H7 London | 0/0 | 3/5 * | 3/5 * | 0/0 | 1/2 * | 0/0 | 1/2 * |
| H7 NY AM | 1/2 | 0/0 * | 0/0 * | 3/5 * | 3/5 * | 3/5 * | 3/5 * |
| H7 NY PM | 0/0 | 2/4 * | 4/7 * | 0/0 | 0/0 | 0/0 | 0/0 |
| A7 Asia | 1/2 | 3/5 * | 3/5 * | 0/0 * | 0/0 * | 0/0 * | 0/0 * |
| A7 London | 0/0 | 4/7 * | 2/4 * | 3/5 * | 1/2 * | 3/5 * | 3/5 * |
| A7 NY AM | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 | 0/0 |
| A7 NY PM | 0/0 | 0/0 | 0/0 | 0/0 | 2/4 * | 4/7 * | 4/7 * |

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

**L3M** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 23675 | -65865 | -33041 | 28903 | 30448 | 16721 | 15924 | +0.0% | +0.0% | - |
| U050 | 15878 | -39966 | -15521 | 20351 | 21561 | 10756 | 10148 | -32.9% | -29.6% | 0.95 |
| U067 | 23155 | -62954 | -28536 | 19899 | 21216 | 11192 | 10521 | -2.2% | -31.2% | 0.49 |
| U075 | 24418 | -67152 | -34793 | 21431 | 22834 | 12409 | 11686 | +3.1% | -25.9% | 0.46 |
| U125 | 21255 | -60915 | -32511 | 41139 | 42903 | 22880 | 21943 | -10.2% | +42.3% | 0.82 |
| U150 | 20404 | -55791 | -24820 | 45473 | 47367 | 25255 | 24239 | -13.8% | +57.3% | 0.97 |

**HOLD** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 55227 | -155735 | -72626 | 18112 | 19402 | 9996 | 9332 | +0.0% | +0.0% | - |
| U050 | 45192 | -117367 | -63491 | 9958 | 10996 | 5619 | 5098 | -18.2% | -45.0% | 0.63 |
| U067 | 48686 | -116163 | -61025 | 12135 | 13250 | 6690 | 6123 | -11.8% | -33.0% | 0.63 |
| U075 | 54324 | -127426 | -62386 | 14386 | 15547 | 7696 | 7099 | -1.6% | -20.6% | 0.68 |
| U125 | 62433 | -157638 | -58113 | 18875 | 20310 | 10567 | 9805 | +13.0% | +4.2% | 0.44 |
| U150 | 62117 | -150157 | -63194 | 20679 | 22201 | 11936 | 11120 | +12.5% | +14.2% | 0.45 |

**GAP** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 35577 | -86295 | -76769 | 15366 | 16229 | 8970 | 8525 | +0.0% | +0.0% | - |
| U067 | 37576 | -99606 | -74704 | 7767 | 8518 | 4662 | 4280 | +5.6% | -49.5% | 0.42 |
| U075 | 37180 | -97099 | -70394 | 9104 | 9885 | 5555 | 5153 | +4.5% | -40.7% | 0.37 |
| U125 | 38169 | -96493 | -81670 | 21885 | 22878 | 12805 | 12277 | +7.3% | +42.4% | 0.26 |
| U150 | 39730 | -97734 | -85918 | 23792 | 24838 | 13820 | 13262 | +11.7% | +54.8% | 0.27 |

**PRE** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 65848 | -178374 | -71328 | 11077 | 12145 | 6359 | 5811 | +0.0% | +0.0% | - |

**X'** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 45533 | -136464 | -72178 | 5390 | 6137 | 3241 | 2857 | +0.0% | +0.0% | - |

**ALL43** (exact JL3)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 49721 | -178374 | -76769 | 14107 | 15137 | 8022 | 7493 | +0.0% | +0.0% | - |

## 3. Beats the uniform benchmark? (exact JL3; uniform ray = today and U050..U150 interpolated)

| vector | window | ulcer | mean | uniform ulcer at the SAME mean | uniform mean at the SAME ulcer | ulcer advantage at equal mean | mean advantage at equal ulcer |
|---|---|---|---|---|---|---|---|

Positive = better than just trading smaller/bigger. "out of range" = the vector sits outside the measured uniform ray (no extrapolation).

## 4. Exact engine on JL2 (live-equivalent stack without the persist=1 profit lines)

**L6M** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 18729 | -55033 | -28790 | 39669 | 41251 | 22076 | 21261 | +0.0% | +0.0% | - |

**L3M** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 22892 | -55033 | -28790 | 30558 | 32044 | 17566 | 16800 | +0.0% | +0.0% | - |

**HOLD** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 47535 | -140077 | -61474 | 14844 | 16092 | 8359 | 7716 | +0.0% | +0.0% | - |

**GAP** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 43185 | -114581 | -85624 | 12912 | 13746 | 7592 | 7162 | +0.0% | +0.0% | - |

**PRE** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 52451 | -144128 | -55528 | 12672 | 13701 | 7157 | 6630 | +0.0% | +0.0% | - |

**X'** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 38065 | -144400 | -73286 | 8250 | 8972 | 4752 | 4382 | +0.0% | +0.0% | - |

**ALL43** (exact JL2)

| vector | ulcer (live lots, $4.84) | max DD | worst week | mean $/wk | mean x1.75 live (engine fee) | mean base lots (engine fee) | mean base lots $4.84 | d ulcer | d mean | boot P(ulcer lower) |
|---|---|---|---|---|---|---|---|---|---|---|
| TODAY | 41508 | -144400 | -85624 | 15586 | 16580 | 8796 | 8285 | +0.0% | +0.0% | - |

## 5. Walk-forward (calibrated arithmetic, theta=0.49): solve on trailing T months, hold the next 3, roll; OOS days only

**trailing 12 months** (OOS days 20240401..20261031, 944 days; uniform points computed on the same days)

| rule | OOS ulcer | OOS max DD | OOS worst week | OOS mean $/wk | d ulcer vs today | d mean vs today | uniform ulcer at same mean | advantage |
|---|---|---|---|---|---|---|---|---|
| TODAY | 50830 | -178374 | -76769 | 17948 | | | | |
| A | 40053 | -107967 | -71319 | 14346 | -21.2% | -20.1% | out of range | - |
| F0 | 36524 | -106300 | -71319 | 14176 | -28.1% | -21.0% | out of range | - |
| F1 | 37731 | -110202 | -70282 | 15454 | -25.8% | -13.9% | 45783 | +17.6% |
| F2 | 43509 | -130268 | -70625 | 15785 | -14.4% | -12.1% | 47321 | +8.1% |
| F3 | 46025 | -135986 | -94361 | 17230 | -9.5% | -4.0% | 49514 | +7.0% |
| F4 | 46540 | -135393 | -83777 | 17695 | -8.4% | -1.4% | 50367 | +7.6% |
| F5 | 48741 | -152009 | -89727 | 19519 | -4.1% | +8.8% | 61280 | +20.5% |
| F6 | 59058 | -170074 | -93171 | 19110 | +16.2% | +6.5% | 58562 | -0.8% |
| F7 | 59535 | -228826 | -129772 | 20807 | +17.1% | +15.9% | 67676 | +12.0% |
| F8 | 69491 | -216281 | -125649 | 20743 | +36.7% | +15.6% | 67413 | -3.1% |
| F9 | 73842 | -248746 | -122510 | 22927 | +45.3% | +27.7% | out of range | - |
| B | 74828 | -248746 | -127822 | 22822 | +47.2% | +27.2% | out of range | - |

**trailing 6 months** (OOS days 20240101..20261031, 1035 days; uniform points computed on the same days)

| rule | OOS ulcer | OOS max DD | OOS worst week | OOS mean $/wk | d ulcer vs today | d mean vs today | uniform ulcer at same mean | advantage |
|---|---|---|---|---|---|---|---|---|
| TODAY | 52698 | -178374 | -76769 | 17005 | | | | |
| A | 44028 | -148590 | -69135 | 13575 | -16.5% | -20.2% | out of range | - |
| F0 | 43503 | -142588 | -69135 | 12695 | -17.4% | -25.3% | out of range | - |
| F1 | 39327 | -133074 | -69196 | 14310 | -25.4% | -15.8% | out of range | - |
| F2 | 44201 | -141332 | -70091 | 15751 | -16.1% | -7.4% | 49540 | +10.8% |
| F3 | 45803 | -158312 | -70959 | 15829 | -13.1% | -6.9% | 49737 | +7.9% |
| F4 | 42314 | -153146 | -80607 | 17485 | -19.7% | +2.8% | 55763 | +24.1% |
| F5 | 48592 | -156438 | -89587 | 18164 | -7.8% | +6.8% | 60096 | +19.1% |
| F6 | 50238 | -160835 | -99084 | 18120 | -4.7% | +6.6% | 59812 | +16.0% |
| F7 | 55395 | -184142 | -107140 | 20147 | +5.1% | +18.5% | 69844 | +20.7% |
| F8 | 64078 | -184234 | -112615 | 20212 | +21.6% | +18.9% | 70092 | +8.6% |
| F9 | 73920 | -244614 | -115975 | 22335 | +40.3% | +31.3% | out of range | - |
| B | 70257 | -244614 | -115594 | 21971 | +33.3% | +29.2% | out of range | - |

## 6. In-sample frontier (calibrated arithmetic, 39 landed months 202307..202610; FIT, not evidence)

Today: ulcer 50371, mean 15439 per week (live lots, $4.84).

| point | ulcer | mean | vector (24 cells: K7 AL-NA-NQ.. in cell order) |
|---|---|---|---|
| A | 32676 | 15700 | 2 0 0 0 1 0 1 0 0 1 0 0 6 0 0 0 2 0 1 0 3 0 0 0 |
| F0 | 33743 | 15513 | 1 1 0 0 2 0 0 0 0 0 0 2 6 0 0 0 2 0 1 0 2 0 0 0 |
| F1 | 34563 | 16128 | 1 0 0 0 0 0 1 0 1 0 0 0 13 0 0 0 2 0 0 0 1 0 0 2 |
| F2 | 34237 | 16713 | 2 0 0 0 1 0 0 0 1 0 0 0 9 0 2 0 2 0 1 0 3 0 0 0 |
| F3 | 36041 | 17372 | 2 1 0 0 0 0 2 0 0 0 0 1 11 0 0 0 2 0 0 0 3 0 0 0 |
| F4 | 39854 | 18090 | 2 1 0 1 4 0 0 0 1 0 0 0 7 0 0 0 6 0 3 0 1 0 0 0 |
| F5 | 40077 | 18603 | 2 2 0 3 0 0 1 0 1 0 0 2 11 0 0 0 6 0 0 0 2 0 0 0 |
| F6 | 42087 | 19246 | 2 4 0 1 0 0 1 0 3 0 0 2 14 0 0 0 2 0 0 0 2 0 0 0 |
| F7 | 42820 | 19872 | 1 2 0 4 3 0 2 0 1 0 0 4 7 0 5 0 6 0 1 0 3 0 0 0 |
| F8 | 46044 | 20550 | 4 2 0 1 4 0 3 0 3 4 0 2 4 0 0 0 6 0 1 0 3 0 0 0 |
| F9 | 48385 | 21150 | 2 4 0 4 4 0 1 0 4 0 0 2 6 0 0 0 6 3 3 0 3 0 0 0 |
| B | 50169 | 21133 | 2 2 0 4 4 0 1 0 3 4 0 4 7 0 8 0 6 0 3 0 3 0 3 0 |

## 7. Nulls and controls

Week-block shuffles of each cell P&L (independent per cell, 30): the same solve (min ulcer at mean >= today) finds on average **49%** lower ulcer on pure noise (real data: 35%); max-mean at ulcer <= today finds +48% mean on noise. So the in-sample gain is about 100% fit.

30 random vectors of the same total lots as the in-sample A vector: ulcer median 40693 (range 35471..48159), mean median 11600; A: ulcer 32676, mean 15700; today 50371 / 15439.

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

## 10. Caveats

- Today-zero cells (U7 NY AM/PM, M7 Asia/NY PM, P7 NY PM, H7 London/NY PM, A7 London/NY AM/NY PM) are scaled from one 2-lot add-one engine run each; solves are limited to 4 base lots there and to 2x today (min today+2) elsewhere, because the arithmetic is not additive.
- O7 fixed. K7/M7/U7/P7/H7/A7 pre-market and close tables unchanged.
- Stack cap (London same-side 6) and the 50% Asia stack cut are held at live in sections 1-9; variants: see the stack section when present.
- Selection of the final rules used the walk-forward on the calibrated arithmetic; the exact runs are the judgement.
