# D8 TIME WINDOWS (family TW): no new entry while the order time is inside a 30-minute window

Research only, 2 lots per book, written 2026-11-23 23:29 UTC by code/th_tw/tw_score.py. Definition: a new-entry signal of a governed book is skipped when its order time (ET wall clock, follows daylight time) falls in [start, end); open trades, brackets and all layers untouched; hook code/th_tw/tw_hooks.py (engine key = hook module tw_hooks, par {tags, win:[[start_min,end_min]]} in ET minutes of the day). Bases: Asia BF2_JT19, NY AM BF2_JT68, London BF2 bare, NY PM BF2 bare (swap when its joint lands). Pick window end 2026-10 (L6M = 2026-05..10, L3M = 2026-08..10); prior years 2023-04..2025-12 (no 2025-11); data end 2026-10. Reference "none" = the pick row (reference only). Selection rule: pick on L6M with L3M beside, drawdown (ulcer) first; walk-forward >= 0.58, prior years not RED (>30% worse equal-risk $/wk), best-of-many null 4 of 5; refit with the next joint.

**NY PM tables are on the BARE base (TL3_SR_NP_STKd893133bd8_BF2_BASE); they will be re-scored on the BF2_JT209 pick (second family NP_STKd893133bd8_JT209, queued rank 4.5, see MORNING.md).**

**Guard (23 Nov 2330Z): any block that removes more than 40%% of the trades of a period is flagged CHECK, never PASS. Plumbing bug found and fixed: the four Asia windows after midnight ET (00:00, 00:30, 01:00, 01:30) were built with a minute-of-day window [0,1440] (length taken after the mod-1440 reduction in tw_gen.to_win), i.e. every entry blocked; fixed sets are the __v1 versions and are re-running. Rows for them read BROKEN, re-running until they land.**

Prior-year rows landed for every window: NO (partial: windows without prior years show verdict LEAD-ONLY).

## Asia (AS_STKd8106b26ef)

### unit ALL (reference pick: L6M ulcer 2733, maxDD -8694, $/wk 9849, worst wk -3660, worst day -7635; L3M ulcer 2013)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 20:00-20:30 | -7.0 | -16.1 | 9150 | -8545 | -5905 | -6882 | 124 | 46 | -34 / +5 / +6 | 0.65 | PASS |
| 22:00-22:30 | -6.5 | -22.1 | 9517 | -9477 | -7492 | -6310 | 95 | 49 | +16 / -1 / -14 | 0.71 | FAIL |
| 21:00-21:30 | -4.0 | -10.7 | 10267 | -9387 | -1161 | -9387 | 113 | 47 | -4 / +29 / -30 | 0.59 | PASS |
| 19:00-19:30 | +0.4 | +26.3 | 9037 | -11239 | -4143 | -8633 | 66 | 10 | -9 / +20 / -30 | 0.48 | FAIL |
| 20:30-21:00 | +17.5 | +17.1 | 8718 | -10749 | -4051 | -10749 | 115 | 60 | -26 / +3 / -9 | 0.56 | FAIL |
| 19:30-20:00 | +21.2 | -6.0 | 9507 | -10609 | -6377 | -7635 | 87 | 38 | +19 / +5 / -18 | 0.52 | FAIL |
| 18:30-19:00 | +21.8 | +28.7 | 9085 | -9903 | -3140 | -6711 | 54 | 19 | +5 / -17 / +30 | 0.53 | FAIL |
| 00:00-00:30 | +22.8 | +33.1 | 9910 | -11765 | -1718 | -8035 | 55 | 30 | -100 / -100 / -100 | 0.21 | CHECK (removes 100% of trades, > 40%) |
| 23:00-23:30 | +28.0 | +19.0 | 9190 | -12145 | -4539 | -7635 | 53 | 17 | -5 / -5 / +1 | 0.54 | FAIL |
| 18:00-18:30 | +46.9 | +91.6 | 8342 | -11671 | -1870 | -10948 | 143 | 54 | +138 / +48 / +45 | 0.43 | FAIL |
| 21:30-22:00 | +60.1 | +38.6 | 9087 | -14383 | -4560 | -9878 | 116 | 55 | +8 / -7 / -17 | 0.58 | FAIL |
| 22:30-23:00 | +62.9 | +13.8 | 9098 | -18176 | -12290 | -7635 | 54 | 18 | +19 / -22 / +11 | 0.55 | FAIL |
| 23:30-00:00 | +81.9 | +5.2 | 8770 | -17365 | -8079 | -7635 | 51 | 13 | -22 / -7 / +12 | 0.62 | FAIL |
| 00:30 | BROKEN, re-running | | | | | | | | | | |
| 01:00 | BROKEN, re-running | | | | | | | | | | |
| 01:30 | BROKEN, re-running | | | | | | | | | | |

### unit M1 (reference pick: L6M ulcer 5080, maxDD -15205, $/wk 2346, worst wk -7850, worst day -5674; L3M ulcer 6036)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 18:30-19:00 | -24.2 | -28.6 | 2497 | -12281 | -7666 | -5544 | 12 | 9 | -9 / -12 / -25 | 0.60 | PASS |
| 21:00-21:30 | -19.0 | -21.7 | 2591 | -12015 | -6301 | -5674 | 10 | 2 | -17 / +2 / +25 | 0.73 | FAIL |
| 23:30-00:00 | -2.5 | -6.8 | 2258 | -14295 | -7990 | -5674 | 7 | 2 | -8 / +10 / +8 | 0.82 | FAIL |
| 20:00-20:30 | -2.4 | -2.0 | 2337 | -13591 | -7056 | -5699 | 2 | 2 | +2 / +31 / -30 | 0.64 | FAIL |
| 20:30-21:00 | -2.1 | -0.3 | 1680 | -12947 | -5571 | -5674 | 35 | 16 | -20 / +5 / -1 | 0.75 | FAIL |
| 22:00-22:30 | -1.6 | -2.6 | 2220 | -14035 | -6582 | -5674 | 20 | 11 | -5 / -15 / +5 | 0.77 | FAIL |
| 19:30-20:00 | +0.1 | -8.1 | 2341 | -13991 | -7046 | -5674 | 15 | 5 | +18 / -2 / +16 | 0.65 | FAIL |
| 23:00-23:30 | +7.6 | -4.9 | 2057 | -15258 | -11761 | -5674 | 9 | 4 | -14 / -27 / +8 | 0.69 | FAIL |
| 21:30-22:00 | +8.5 | -13.0 | 2478 | -14760 | -9645 | -5544 | 21 | 13 | +9 / -18 / -35 | 0.77 | PASS |
| 19:00-19:30 | +20.6 | +31.8 | 1842 | -16675 | -7041 | -5674 | 4 | 7 | -0 / +20 / +4 | 0.64 | FAIL |
| 22:30-23:00 | +20.6 | +30.1 | 1961 | -17564 | -7172 | -5674 | 7 | 2 | -1 / -25 / +13 | 0.75 | FAIL |
| 18:00-18:30 | +23.1 | +37.3 | 1963 | -15205 | -7660 | -5544 | 11 | -2 | +5 / -34 / -3 | 0.58 | FAIL |
| 00:00 | BROKEN, re-running | | | | | | | | | | |
| 00:30 | BROKEN, re-running | | | | | | | | | | |
| 01:00 | BROKEN, re-running | | | | | | | | | | |
| 01:30 | BROKEN, re-running | | | | | | | | | | |

### unit M2 (reference pick: L6M ulcer 744, maxDD -2869, $/wk 2419, worst wk -1380, worst day -2574; L3M ulcer 815)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 23:00-23:30 | +0.0 | +0.0 | 2419 | -2869 | -1380 | -2574 | 0 | 0 | +0 / +0 / +0 | 1.00 | PASS |
| 20:00-20:30 | +1.2 | -45.6 | 2449 | -3168 | -3168 | -2415 | 22 | 11 | -54 / +5 / +25 | 0.69 | FAIL |
| 22:00-22:30 | +2.6 | +7.8 | 2380 | -3049 | -1380 | -2574 | 9 | 6 | +0 / -10 / -18 | 0.82 | FAIL |
| 19:00-19:30 | +6.3 | +13.5 | 2393 | -2869 | -1380 | -2574 | 7 | 2 | -0 / +11 / +24 | 0.71 | FAIL |
| 22:30-23:00 | +8.2 | -18.9 | 2415 | -3149 | -1380 | -2415 | 5 | 2 | +7 / -10 / +12 | 0.89 | FAIL |
| 21:00-21:30 | +10.0 | -3.3 | 2479 | -3509 | -2014 | -2574 | 10 | 1 | -5 / +0 / -23 | 0.86 | PASS |
| 18:00-18:30 | +10.7 | +17.6 | 2254 | -2869 | -1023 | -2574 | 15 | 6 | +3 / +7 / -11 | 0.75 | FAIL |
| 23:30-00:00 | +20.3 | +3.5 | 2110 | -3214 | -1380 | -2919 | 11 | 5 | -1 / +0 / +5 | 0.86 | PASS |
| 18:30-19:00 | +28.6 | +22.7 | 2099 | -3392 | -2269 | -2574 | 15 | 6 | +5 / -20 / +23 | 0.73 | FAIL |
| 20:30-21:00 | +31.6 | +38.0 | 2134 | -3392 | -1200 | -2574 | 9 | 5 | -9 / -35 / -9 | 0.77 | FAIL |
| 19:30-20:00 | +32.7 | +3.9 | 2080 | -3328 | -1380 | -2574 | 9 | 1 | +0 / -9 / -33 | 0.80 | PASS |
| 21:30-22:00 | +35.2 | -10.8 | 2236 | -3382 | -3353 | -2574 | 10 | 5 | -0 / -16 / -22 | 0.83 | FAIL |
| 00:00 | BROKEN, re-running | | | | | | | | | | |
| 00:30 | BROKEN, re-running | | | | | | | | | | |
| 01:00 | BROKEN, re-running | | | | | | | | | | |
| 01:30 | BROKEN, re-running | | | | | | | | | | |

### unit M3 (reference pick: L6M ulcer 6749, maxDD -13586, $/wk 194, worst wk -5208, worst day -3849; L3M ulcer 2010)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 21:00-21:30 | -36.5 | -13.6 | 491 | -9874 | -3458 | -3624 | 19 | 9 | +56 / +13 / +0 | 0.83 | FAIL |
| 19:00-19:30 | -24.0 | -3.7 | 301 | -10496 | -3253 | -3624 | 12 | 3 | -39 / +9 / -2 | 0.76 | FAIL |
| 19:30-20:00 | -18.6 | +8.2 | 194 | -11962 | -5208 | -3849 | 17 | 7 | +0 / -36 / -13 | 0.77 | FAIL |
| 20:30-21:00 | -15.2 | +10.2 | 201 | -11146 | -5208 | -3849 | 6 | 4 | -21 / +15 / -22 | 0.74 | PASS |
| 18:00-18:30 | -8.0 | +2.0 | 144 | -12381 | -5208 | -3849 | 4 | 2 | +4 / +0 / -24 | 0.88 | PASS |
| 23:00-23:30 | -3.7 | -3.0 | 329 | -13157 | -5793 | -3849 | 13 | 3 | -9 / +12 / +15 | 0.83 | FAIL |
| 21:30-22:00 | +4.6 | +0.1 | 57 | -12238 | -4003 | -3849 | 24 | 15 | +17 / -11 / +14 | 0.72 | FAIL |
| 22:30-23:00 | +6.0 | -0.5 | 130 | -14191 | -5208 | -3849 | 13 | 7 | +26 / -24 / -11 | 0.82 | FAIL |
| 20:00-20:30 | +11.3 | -32.2 | 158 | -13378 | -4103 | -3849 | 23 | 8 | -18 / -3 / +4 | 0.74 | PASS |
| 23:30-00:00 | +16.7 | -5.3 | 113 | -15521 | -6479 | -3849 | 6 | 3 | -45 / -0 / -5 | 0.88 | FAIL |
| 22:00-22:30 | +16.9 | +4.3 | 80 | -15413 | -5793 | -4434 | 12 | 6 | -11 / -18 / -3 | 0.82 | PASS |
| 18:30-19:00 | +27.3 | +1.0 | 101 | -16204 | -4303 | -3849 | 15 | 4 | -17 / -1 / +12 | 0.71 | FAIL |
| 00:00 | BROKEN, re-running | | | | | | | | | | |
| 00:30 | BROKEN, re-running | | | | | | | | | | |
| 01:00 | BROKEN, re-running | | | | | | | | | | |
| 01:30 | BROKEN, re-running | | | | | | | | | | |

### unit M4 (reference pick: L6M ulcer 3148, maxDD -9944, $/wk 2123, worst wk -6564, worst day -7082; L3M ulcer 2904)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 18:00-18:30 | -20.0 | -33.8 | 2413 | -10192 | -5029 | -5592 | 67 | 32 | -17 / -44 / -4 | 0.65 | FAIL |
| 21:30-22:00 | -15.7 | -6.2 | 2362 | -8310 | -7557 | -6357 | 39 | 18 | -5 / +9 / -25 | 0.77 | PASS |
| 18:30-19:00 | -13.5 | -1.7 | 2236 | -9944 | -3909 | -7082 | 16 | 8 | -10 / +14 / -10 | 0.73 | FAIL |
| 20:00-20:30 | -6.3 | -15.9 | 2064 | -8657 | -6285 | -7503 | 50 | 23 | -9 / +13 / +23 | 0.64 | FAIL |
| 22:00-22:30 | -0.5 | +7.8 | 2188 | -10318 | -5783 | -7082 | 21 | 7 | +6 / -25 / -2 | 0.78 | PASS |
| 21:00-21:30 | -0.1 | -30.1 | 1997 | -8920 | -7759 | -6314 | 40 | 13 | -5 / +11 / -40 | 0.80 | PASS |
| 20:30-21:00 | +8.7 | +2.4 | 2206 | -10510 | -5987 | -8091 | 33 | 13 | -14 / -1 / +6 | 0.74 | PASS |
| 19:30-20:00 | +8.8 | +0.8 | 2190 | -9944 | -7579 | -7082 | 12 | 11 | +7 / +1 / -2 | 0.67 | FAIL |
| 23:30-00:00 | +8.9 | -13.7 | 1948 | -10251 | -6564 | -7082 | 10 | 1 | -8 / -10 / +8 | 0.78 | PASS |
| 19:00-19:30 | +9.5 | +21.5 | 1707 | -9901 | -6744 | -7082 | 22 | 11 | -12 / -37 / -29 | 0.72 | PASS |
| 23:00-23:30 | +11.9 | +25.6 | 2024 | -10412 | -5821 | -7082 | 19 | 5 | -1 / -5 / +10 | 0.78 | PASS |
| 22:30-23:00 | +23.9 | +10.7 | 1533 | -10803 | -9738 | -7082 | 15 | 5 | +0 / +2 / -5 | 0.79 | PASS |
| 00:00 | BROKEN, re-running | | | | | | | | | | |
| 00:30 | BROKEN, re-running | | | | | | | | | | |
| 01:00 | BROKEN, re-running | | | | | | | | | | |
| 01:30 | BROKEN, re-running | | | | | | | | | | |

### unit M5 (reference pick: L6M ulcer 4724, maxDD -15956, $/wk 2847, worst wk -5807, worst day -5429; L3M ulcer 6334)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 22:00-22:30 | -24.6 | -36.7 | 2647 | -12140 | -5077 | -5429 | 28 | 14 | +10 / +4 / +2 | 0.66 | FAIL |
| 19:30-20:00 | -15.2 | -15.6 | 2592 | -12982 | -6890 | -5429 | 33 | 14 | +1 / +3 / -14 | 0.65 | PASS |
| 23:00-23:30 | -11.5 | -17.8 | 2537 | -11835 | -5807 | -5429 | 13 | 6 | +2 / +21 / -1 | 0.74 | PASS |
| 22:30-23:00 | -7.2 | -10.7 | 3162 | -15282 | -5132 | -4214 | 16 | 5 | +11 / -7 / +10 | 0.74 | PASS |
| 21:00-21:30 | +1.8 | -10.9 | 2729 | -17164 | -7518 | -4834 | 32 | 20 | -3 / +59 / +13 | 0.71 | FAIL |
| 20:00-20:30 | +6.6 | -1.9 | 2270 | -16947 | -7092 | -6727 | 25 | 1 | -39 / -8 / -6 | 0.77 | PASS |
| 23:30-00:00 | +9.0 | +1.3 | 2391 | -16072 | -5792 | -5429 | 18 | 3 | -17 / +7 / +18 | 0.72 | FAIL |
| 20:30-21:00 | +9.7 | -24.1 | 2531 | -15769 | -6381 | -5429 | 32 | 22 | -23 / +3 / -25 | 0.73 | PASS |
| 18:30-19:00 | +15.1 | +16.8 | 2230 | -17836 | -7727 | -5429 | -3 | -7 | +0 / +7 / +49 | 0.52 | FAIL |
| 19:00-19:30 | +20.5 | +23.8 | 2710 | -16804 | -5517 | -5429 | 16 | -11 | -1 / -15 / -26 | 0.72 | PASS |
| 18:00-18:30 | +26.1 | -36.3 | 2049 | -16447 | -5823 | -6218 | 44 | 20 | +70 / +70 / +90 | 0.42 | FAIL |
| 21:30-22:00 | +47.6 | +38.0 | 1998 | -23329 | -8936 | -4949 | 23 | 8 | -14 / -7 / -2 | 0.68 | PASS |
| 00:00 | BROKEN, re-running | | | | | | | | | | |
| 00:30 | BROKEN, re-running | | | | | | | | | | |
| 01:00 | BROKEN, re-running | | | | | | | | | | |
| 01:30 | BROKEN, re-running | | | | | | | | | | |

Null (best-of-16 windows, stack unit, emulated by signal-clock shift, 20 draws): real best L6M ulcer change -7.0%, null best median -13.9%; real beats 1 of the first 5 draws (needs 4), beats 3 of 20 draws (p of null doing as well = 0.850). Windows that look good by luck (L6M ulcer <= -10% and L3M lower): real 0 of 16, null mean 1.1 of 16.

## London (LO_L19201dfc_R0BRF90_30)

### unit ALL (reference pick: L6M ulcer 2658, maxDD -7836, $/wk 3265, worst wk -5371, worst day -6629; L3M ulcer 3056)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 06:30-07:00 | -21.4 | -20.4 | 3405 | -6577 | -4376 | -4604 | 14 | 5 | -100 / -100 / -100 | 0.71 | CHECK (removes 100% of trades, > 40%) |
| 08:00-08:30 | -11.1 | -4.0 | 3243 | -7836 | -4903 | -6629 | 24 | 8 | -100 / -100 / -100 | 0.57 | CHECK (removes 100% of trades, > 40%) |
| 03:00-03:30 | +0.8 | -4.5 | 3080 | -9021 | -5371 | -5774 | 24 | 11 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |
| 02:30-03:00 | +0.9 | +6.2 | 3412 | -9026 | -5371 | -6629 | 9 | 5 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 06:00-06:30 | +3.6 | -3.2 | 2883 | -8382 | -5371 | -6629 | 15 | 7 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 03:30-04:00 | +4.0 | -0.2 | 3048 | -8372 | -6556 | -6629 | 6 | 1 | -100 / -100 / -100 | 0.57 | CHECK (removes 100% of trades, > 40%) |
| 07:30-08:00 | +4.3 | +3.9 | 3001 | -8045 | -5562 | -6629 | 16 | 6 | -100 / -100 / -100 | 0.36 | CHECK (removes 100% of trades, > 40%) |
| 05:00-05:30 | +17.2 | +25.5 | 2806 | -9853 | -6762 | -6629 | 12 | 6 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |
| 07:00-07:30 | +20.3 | -3.7 | 3098 | -10762 | -7751 | -6629 | 15 | 6 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |
| 04:30-05:00 | +20.7 | +27.2 | 3032 | -9004 | -7289 | -6629 | 21 | 9 | -100 / -100 / -100 | 0.36 | CHECK (removes 100% of trades, > 40%) |
| 02:00-02:30 | +28.3 | +23.3 | 2734 | -9410 | -6767 | -6629 | 8 | 6 | +0 / -29 / +21 | 0.78 | FAIL |
| 05:30-06:00 | +38.5 | +55.4 | 2845 | -10862 | -5958 | -6629 | 9 | 7 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 04:00-04:30 | +45.0 | +20.7 | 2593 | -12108 | -4903 | -6629 | 35 | 17 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |

Null (best-of-13 windows, stack unit, emulated by signal-clock shift, 20 draws): real best L6M ulcer change +28.3%, null best median -13.5%; real beats 0 of the first 5 draws (needs 4), beats 0 of 20 draws (p of null doing as well = 1.000). Windows that look good by luck (L6M ulcer <= -10% and L3M lower): real 0 of 13, null mean 0.8 of 13.

## NYPM (NP_STKd893133bd8)

### unit ALL (reference pick: L6M ulcer 5573, maxDD -24257, $/wk 8736, worst wk -8566, worst day -16735; L3M ulcer 4143)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 15:30-16:00 | -10.2 | +4.5 | 9566 | -25294 | -10123 | -20171 | 211 | 85 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |
| 15:00-15:30 | -1.5 | +0.2 | 7191 | -16324 | -9602 | -12566 | 123 | 43 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 14:30-15:00 | +13.9 | +42.6 | 6825 | -19968 | -13997 | -16735 | 114 | 47 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 12:30-13:00 | +27.3 | -18.2 | 6327 | -25838 | -12945 | -17126 | 133 | 58 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |
| 13:30-14:00 | +38.7 | +61.5 | 7670 | -23854 | -16407 | -14741 | 118 | 42 | -100 / -100 / -100 | 0.57 | CHECK (removes 100% of trades, > 40%) |
| 14:00-14:30 | +44.6 | +69.3 | 7463 | -24258 | -7478 | -16725 | 109 | 42 | -100 / -100 / -100 | 0.21 | CHECK (removes 100% of trades, > 40%) |
| 12:00-12:30 | +64.8 | +103.5 | 6133 | -26557 | -12073 | -11981 | 159 | 70 | -100 / -100 / -100 | 0.14 | CHECK (removes 100% of trades, > 40%) |
| 13:00-13:30 | +76.5 | +92.3 | 7126 | -29941 | -17292 | -15951 | 130 | 61 | -100 / -100 / -100 | 0.36 | CHECK (removes 100% of trades, > 40%) |

### unit M1 (reference pick: L6M ulcer 4159, maxDD -12771, $/wk 2243, worst wk -6449, worst day -4808; L3M ulcer 4912)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 15:30-16:00 | -20.5 | -41.3 | 1922 | -8909 | -5755 | -4808 | 100 | 42 | -100 / -100 / -100 | 0.57 | CHECK (removes 100% of trades, > 40%) |
| 13:00-13:30 | -5.9 | -1.4 | 2108 | -12418 | -6449 | -4768 | 69 | 32 | -100 / -100 / -100 | 0.71 | CHECK (removes 100% of trades, > 40%) |
| 14:30-15:00 | -5.4 | +7.7 | 2329 | -14674 | -4538 | -4808 | 68 | 31 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 12:00-12:30 | -4.5 | -19.8 | 1767 | -11597 | -7635 | -5998 | 81 | 42 | -100 / -100 / -100 | 0.29 | CHECK (removes 100% of trades, > 40%) |
| 12:30-13:00 | -3.6 | -29.9 | 1964 | -11707 | -8812 | -4768 | 69 | 29 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 13:30-14:00 | +10.1 | +4.5 | 1959 | -13862 | -8739 | -5758 | 60 | 24 | -100 / -100 / -100 | 0.57 | CHECK (removes 100% of trades, > 40%) |
| 15:00-15:30 | +26.7 | +22.2 | 2142 | -16210 | -8835 | -4684 | 70 | 26 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 14:00-14:30 | +75.3 | +84.2 | 1262 | -21893 | -7897 | -5228 | 74 | 32 | -100 / -100 / -100 | 0.36 | CHECK (removes 100% of trades, > 40%) |

### unit M2 (reference pick: L6M ulcer 5298, maxDD -19168, $/wk 2384, worst wk -6144, worst day -19168; L3M ulcer 3509)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 15:30-16:00 | -16.0 | -15.9 | 3123 | -19019 | -4129 | -19019 | 20 | 5 | -100 / -100 / -100 | 0.93 | CHECK (removes 100% of trades, > 40%) |
| 15:00-15:30 | -7.4 | +3.5 | 1651 | -14374 | -6144 | -14374 | 11 | 2 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 12:30-13:00 | +13.4 | +66.1 | 1271 | -19168 | -6144 | -19168 | 9 | 4 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 13:30-14:00 | +16.5 | +82.8 | 2007 | -16168 | -11062 | -14404 | 13 | 3 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 14:00-14:30 | +22.2 | +27.5 | 2382 | -19158 | -6144 | -19158 | 2 | 1 | -100 / -100 / -100 | 0.86 | CHECK (removes 100% of trades, > 40%) |
| 14:30-15:00 | +37.4 | +15.5 | 1332 | -19381 | -9524 | -19168 | 5 | 2 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 12:00-12:30 | +53.6 | +79.5 | 408 | -15753 | -9033 | -14414 | 16 | 3 | -100 / -100 / -100 | 0.36 | CHECK (removes 100% of trades, > 40%) |
| 13:00-13:30 | +155.5 | -19.4 | 1803 | -29223 | -21366 | -19168 | 11 | 6 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |

### unit M3 (reference pick: L6M ulcer 3876, maxDD -11193, $/wk 2117, worst wk -4757, worst day -6264; L3M ulcer 3350)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 15:30-16:00 | -24.7 | -12.1 | 2278 | -7874 | -4813 | -6264 | 21 | 8 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 13:30-14:00 | -20.7 | -43.1 | 2250 | -9914 | -4724 | -3574 | 17 | 6 | -100 / -100 / -100 | 0.57 | CHECK (removes 100% of trades, > 40%) |
| 12:30-13:00 | -3.7 | -4.7 | 1622 | -9660 | -6353 | -6264 | 24 | 11 | -100 / -100 / -100 | 0.57 | CHECK (removes 100% of trades, > 40%) |
| 12:00-12:30 | +4.9 | -2.8 | 1944 | -11214 | -4724 | -6319 | 31 | 13 | -100 / -100 / -100 | 0.36 | CHECK (removes 100% of trades, > 40%) |
| 15:00-15:30 | +10.6 | -19.1 | 1827 | -12864 | -4923 | -6264 | 20 | 10 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 13:00-13:30 | +12.2 | +18.6 | 1333 | -11193 | -6343 | -6344 | 20 | 13 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |
| 14:30-15:00 | +16.5 | +19.3 | 1923 | -14379 | -6353 | -6264 | 11 | 5 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 14:00-14:30 | +43.7 | +22.1 | 1783 | -15969 | -6314 | -6264 | 13 | 4 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |

### unit M4 (reference pick: L6M ulcer 6304, maxDD -18892, $/wk 2080, worst wk -10289, worst day -7223; L3M ulcer 4742)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 15:30-16:00 | -15.4 | -6.4 | 2358 | -14520 | -6951 | -7083 | 70 | 30 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 14:00-14:30 | -12.7 | +1.1 | 2125 | -15222 | -12680 | -9108 | 20 | 5 | -100 / -100 / -100 | 0.79 | CHECK (removes 100% of trades, > 40%) |
| 15:00-15:30 | -4.6 | +2.4 | 1632 | -16493 | -10289 | -7223 | 22 | 5 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 12:30-13:00 | +2.0 | -11.6 | 1517 | -22237 | -8409 | -8204 | 31 | 14 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |
| 12:00-12:30 | +3.7 | +63.5 | 2029 | -17209 | -5567 | -7223 | 31 | 12 | -100 / -100 / -100 | 0.57 | CHECK (removes 100% of trades, > 40%) |
| 13:30-14:00 | +21.2 | -9.7 | 1529 | -23709 | -15104 | -9618 | 28 | 9 | -100 / -100 / -100 | 0.71 | CHECK (removes 100% of trades, > 40%) |
| 14:30-15:00 | +34.6 | +3.6 | 1290 | -21288 | -15179 | -9608 | 30 | 9 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 13:00-13:30 | +35.9 | +77.1 | 1949 | -21323 | -6777 | -9108 | 30 | 10 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |

Null (best-of-8 windows, stack unit, emulated by signal-clock shift, 20 draws): real best L6M ulcer change +0.0%, null best median -13.4%; real beats 0 of the first 5 draws (needs 4), beats 0 of 20 draws (p of null doing as well = 1.000). Windows that look good by luck (L6M ulcer <= -10% and L3M lower): real 0 of 8, null mean 0.9 of 8.

## NYAM (NY_STKd8b76ecd35)

### unit ALL (reference pick: L6M ulcer 3521, maxDD -10218, $/wk 6076, worst wk -4550, worst day -5504; L3M ulcer 4181)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 10:30-11:00 | -6.6 | -21.4 | 6113 | -11004 | -4830 | -7694 | 263 | 125 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 11:00-11:30 | -4.9 | -8.5 | 6016 | -9524 | -2172 | -6684 | 184 | 78 | -100 / -100 / -100 | 0.71 | CHECK (removes 100% of trades, > 40%) |
| 11:30-12:00 | +6.1 | +11.7 | 5785 | -10759 | -4315 | -5954 | 210 | 97 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 10:00-10:30 | +21.9 | +29.0 | 5473 | -14571 | -5873 | -7618 | 316 | 120 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |
| 09:30-10:00 | +98.1 | +79.1 | 2124 | -20860 | -19626 | -12244 | 506 | 224 | -100 / -100 / -100 | 0.29 | CHECK (removes 100% of trades, > 40%) |

### unit M1 (reference pick: L6M ulcer 3010, maxDD -10124, $/wk 1614, worst wk -6262, worst day -3965; L3M ulcer 1672)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 10:30-11:00 | -26.2 | -43.8 | 1844 | -7586 | -4821 | -3965 | 77 | 34 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |
| 11:00-11:30 | -8.5 | +33.3 | 1511 | -8312 | -5609 | -4511 | 55 | 22 | -100 / -100 / -100 | 0.57 | CHECK (removes 100% of trades, > 40%) |
| 11:30-12:00 | +7.4 | -34.1 | 1596 | -12084 | -6421 | -4106 | 70 | 34 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 10:00-10:30 | +13.5 | +67.0 | 910 | -10335 | -6067 | -3856 | 128 | 46 | -100 / -100 / -100 | 0.36 | CHECK (removes 100% of trades, > 40%) |
| 09:30-10:00 | +43.9 | -7.4 | 705 | -10680 | -4005 | -3117 | 214 | 99 | -100 / -100 / -100 | 0.71 | CHECK (removes 100% of trades, > 40%) |

### unit M2 (reference pick: L6M ulcer 5040, maxDD -16270, $/wk 511, worst wk -10109, worst day -5194; L3M ulcer 5727)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 10:30-11:00 | -27.3 | -33.7 | 691 | -10702 | -8464 | -6150 | 110 | 52 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 11:00-11:30 | -26.0 | -26.2 | 674 | -10946 | -9639 | -5194 | 72 | 32 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 09:30-10:00 | -19.5 | -7.6 | 1623 | -15084 | -12238 | -5749 | 126 | 53 | -100 / -100 / -100 | 0.86 | CHECK (removes 100% of trades, > 40%) |
| 11:30-12:00 | +18.9 | -2.4 | 249 | -16913 | -6650 | -5042 | 84 | 40 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 10:00-10:30 | +115.0 | +50.3 | -90 | -23133 | -11751 | -5879 | 98 | 41 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |

### unit M3 (reference pick: L6M ulcer 6212, maxDD -14981, $/wk 2534, worst wk -7749, worst day -9554; L3M ulcer 7333)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 11:00-11:30 | -19.0 | -22.9 | 2732 | -14638 | -7218 | -9554 | 7 | 1 | -100 / -100 / -100 | 0.79 | CHECK (removes 100% of trades, > 40%) |
| 10:00-10:30 | -14.1 | -24.6 | 2966 | -13662 | -7954 | -9554 | 35 | 11 | -100 / -100 / -100 | 0.57 | CHECK (removes 100% of trades, > 40%) |
| 10:30-11:00 | -10.8 | -22.1 | 2785 | -19543 | -8124 | -9554 | 18 | 7 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 11:30-12:00 | -4.4 | -5.6 | 2691 | -14638 | -7749 | -9554 | 16 | 8 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 09:30-10:00 | +225.6 | +60.1 | -1269 | -34817 | -22238 | -11919 | 97 | 39 | -100 / -100 / -100 | 0.50 | CHECK (removes 100% of trades, > 40%) |

### unit M4 (reference pick: L6M ulcer 3131, maxDD -7868, $/wk 582, worst wk -5154, worst day -2625; L3M ulcer 3650)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 10:00-10:30 | -28.5 | -50.9 | 832 | -4873 | -2714 | -1785 | 37 | 15 | -100 / -100 / -100 | 0.77 | CHECK (removes 100% of trades, > 40%) |
| 11:00-11:30 | -12.3 | -18.6 | 368 | -6043 | -5154 | -2625 | 26 | 10 | -100 / -100 / -100 | 0.54 | CHECK (removes 100% of trades, > 40%) |
| 10:30-11:00 | -11.3 | -15.2 | 580 | -6208 | -4224 | -2625 | 19 | 14 | -100 / -100 / -100 | 0.69 | CHECK (removes 100% of trades, > 40%) |
| 11:30-12:00 | +7.6 | -1.7 | 448 | -7897 | -5154 | -2625 | 10 | 4 | -100 / -100 / -100 | 0.77 | CHECK (removes 100% of trades, > 40%) |
| 09:30-10:00 | +46.5 | +9.4 | 156 | -9459 | -4444 | -4214 | 43 | 20 | -100 / -100 / -100 | 0.61 | CHECK (removes 100% of trades, > 40%) |

### unit M5 (reference pick: L6M ulcer 1580, maxDD -4737, $/wk 900, worst wk -2519, worst day -2329; L3M ulcer 1600)

| window ET | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | removed L6M | removed L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 09:30-10:00 | -17.4 | -38.6 | 927 | -4408 | -3109 | -1715 | 26 | 13 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 10:00-10:30 | -6.8 | -13.5 | 948 | -4173 | -2214 | -1810 | 18 | 7 | -100 / -100 / -100 | 0.71 | CHECK (removes 100% of trades, > 40%) |
| 11:30-12:00 | +13.0 | -17.1 | 850 | -4249 | -3154 | -2329 | 30 | 11 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 11:00-11:30 | +14.7 | -2.4 | 771 | -4848 | -2519 | -2329 | 24 | 13 | -100 / -100 / -100 | 0.64 | CHECK (removes 100% of trades, > 40%) |
| 10:30-11:00 | +88.6 | +75.0 | 276 | -5964 | -2944 | -2329 | 39 | 18 | -100 / -100 / -100 | 0.43 | CHECK (removes 100% of trades, > 40%) |

Null (best-of-5 windows, stack unit, emulated by signal-clock shift, 20 draws): real best L6M ulcer change +0.0%, null best median -6.2%; real beats 1 of the first 5 draws (needs 4), beats 4 of 20 draws (p of null doing as well = 0.800). Windows that look good by luck (L6M ulcer <= -10% and L3M lower): real 0 of 5, null mean 0.2 of 5.
