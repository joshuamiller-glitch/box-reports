# DS3_FADE_OOS - pre-2023 out-of-sample of the four fade survivors (DIS-AA), BASE-4, 2026-11-04T21:49Z

**Signal-level object, not live P&L.** 1 lot, next-1-minute-bar-open fills (+0.25 pt adverse), stop first on a same-bar touch, stop slip 1.5, flat/time-stop slip 0.5, fee 0.242 pt, flat 16:55 ET, one position per book, no live exits, no Trade-Health, no locks; percent (V2) convention: 60-pt brackets, the VWAPF 10-pt threshold, the VB2 shape thresholds and all costs scaled by r = close/20,620 and results expressed at the 2023-26 price scale (ZL-2, DS3_SIGNALS_2013.md; the 1-minute approximation of the LIVE stack failed validation, which is why nothing here is the live stack's P&L). Descriptive, Shadow-watch only, no PASS, no purchases. Scope note l2vast/ds3/prereg/DISAA_scope.md sha256 5927ec85d2caa1991a1fdeb43473019ec5c435047e75a099ee3cdf11600a6792 (DECISIONS.md, before any pre-2023 statistic). Code l2vast/ds3/code/disaa/ (fo_core, fo_sim, fo_run, fo_calib, fo_an); data /mnt/l2/l2vast/ds3_base4/ (fo_panel_post.pkl, fo_calib.pkl, disaa_cells.csv). Data: NQ volume-front 1-min 2013-01..2026-10 (additive back-adjust at the 55 rolls), PRE = label days 2013-01-02..2023-04-02 (488 weeks), POST 2023-04-03..2026-10-30 (187 weeks). Scope-note correction: ONRTH is coded with a 60-minute time stop (T60), not T120 as the note says; the code was used as written.

**Plain sentence (DIS-AA):** before 2023 the raw 1-minute signals of the four fade survivors earned about nothing (mean pts per trade N_REL_rev -0.41, ORBF +0.27, VB2 NYPM T1 -1.11, the NYAM bundle -0.49; $/wk at 1 lot -11, +26, -61, -148) against clearly positive post-2023 means for N_REL_rev and VB2 (and a negative post-2023 mean for ORBF and the bundle in this 1-minute object); their excess over drift is positive in point estimate before 2023 (bundle +331 $/wk vs P1c, +549 vs other-day fade, +589 vs delayed fade) mostly because the benchmarks themselves lose money, with confidence intervals that include zero for every line except ORBF and the bundle against the other-day and delayed-fade benchmarks and ONRTH against the delayed-fade benchmark (strong version) - so the pre-2023 evidence is weak-to-neutral, not a 2026-only artefact in sign but far smaller than the post-2023 excess in size.

## Answer
Question: do the fade survivors have a positive excess over drift BEFORE 2023, or are they 2026-only? Verdicts under the pre-registered rule (same-sign positive excess in >= 5 of 10 pre-2023 years AND the pre-2023 bootstrap CI of the mean weekly excess not entirely below 0, against EACH of P1c, (a), (b), (c)): N_REL_rev: SURVIVES PRE-2023 (weak rule; not a PASS) [strong version, CI lower limit > 0: against none]; ORBF: SURVIVES PRE-2023 (weak rule; not a PASS) [strong version, CI lower limit > 0: vs a, c]; ONRTH: SURVIVES PRE-2023 (weak rule; not a PASS) [strong version, CI lower limit > 0: vs c]; VWAPF: POST-2023 ONLY / not supported before 2023 (fails vs P1c) [strong version, CI lower limit > 0: against none]; VB2NYPM_T1: SURVIVES PRE-2023 (weak rule; not a PASS) [strong version, CI lower limit > 0: against none]; NYAM_bundle: SURVIVES PRE-2023 (weak rule; not a PASS) [strong version, CI lower limit > 0: vs a, c].

## Calibration on 2023-04..2026-10 against the 1-s lists (V1 convention, unscaled; signal recall = same-side 1-min signal within 120 s of a 1-s trade the harness took)
| line | 1-s trades | 1-min trades | signal recall | precision | per-trade corr (matched) | weekly corr | mean pts/trade 1-min / 1-s | $/wk 1-min / 1-s |
|--|--|--|--|--|--|--|--|--|
| N_REL_rev_post | 304 | 302 | 0.993 | 1.000 | 0.898 | 0.910 | +2.81 / +3.74 | +91 / +122 |
| N_REL_rev_pre | 304 | 299 | 0.984 | 1.000 | 0.898 | 0.909 | +3.09 / +3.74 | +99 / +122 |
| ORBF | 914 | 905 | 0.987 | 0.997 | 0.857 | 0.849 | -3.23 / -2.43 | -312 / -237 |
| ONRTH | 543 | 537 | 0.989 | 1.000 | 0.935 | 0.938 | +2.16 / +3.32 | +124 / +193 |
| VWAPF | 1435 | 1432 | 0.978 | 0.980 | 0.938 | 0.937 | +1.68 / +2.26 | +258 / +347 |
| VB2NYPM_T1 | 523 | 518 | 0.985 | 0.994 | 0.865 | 0.805 | +1.14 / +1.54 | +63 / +86 |

The 1-min fill model is later and rougher than the 1-s model (mean pts per trade lower than the 1-s harness for four of five lines, as in DW), so levels are not comparable to the 1-s tables; per-trade correlations 0.86-0.94 and recall 0.98-0.99 say the entry rules are reproduced, the exits are an approximation. N_REL_rev: the post-bar ATR convention (ATR including the 08:25-08:29 bucket) matches the list better (recall 0.993 vs 0.984) and is the one used. ORBF is a minute version of a 1-s rule (range needs >= 20 bars).

## Pre vs post summary (V2 scaled; $/wk at 1 lot; excess = real minus benchmark)
| line | n pre / post | pts/trade pre / post | $/wk 1 lot pre / post | excess vs P1c pre / post | vs (a) pre / post | vs (b) pre / post | vs (c) pre / post | years positive (P1c / a / b / c) | CI of pre mean excess vs P1c / a / b / c | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| N_REL_rev | 723 / 302 | -0.41 / +2.13 | -11 / +69 | +45 / +72 | +57 / +223 | +51 / +46 | +38 / +139 | 7/6/6/5 | (-59,+153) ; (-42,+157) ; (-110,+216) ; (-64,+142) | SURVIVES PRE-2023 (weak rule; not a PASS) [strong version, CI lower limit > 0: against none] |
| ORBF | 2582 / 905 | +0.27 / -5.01 | +26 / -490 | +171 / -100 | +197 / -193 | +272 / -747 | +264 / -388 | 6/7/6/7 | (-8,+357) ; (+32,+364) ; (-104,+669) ; (+73,+446) | SURVIVES PRE-2023 (weak rule; not a PASS) [strong version, CI lower limit > 0: vs a, c] |
| ONRTH | 1546 / 537 | +0.05 / +1.07 | +3 / +62 | +127 / +224 | +120 / +371 | +140 / +271 | +152 / +164 | 7/7/6/7 | (-33,+285) ; (-24,+257) ; (-159,+427) ; (+10,+299) | SURVIVES PRE-2023 (weak rule; not a PASS) [strong version, CI lower limit > 0: vs c] |
| VWAPF | 3927 / 1415 | -1.21 / +0.18 | -177 / +27 | +33 / +171 | +232 / +769 | -12 / +423 | +173 / +137 | 4/7/5/6 | (-226,+284) ; (-30,+487) ; (-542,+505) ; (-95,+442) | POST-2023 ONLY / not supported before 2023 (fails vs P1c) [strong version, CI lower limit > 0: against none] |
| VB2NYPM_T1 | 1476 / 518 | -1.11 / +1.09 | -61 / +61 | +7 / +139 | +28 / +251 | +19 / +139 | +21 / +103 | 5/6/6/6 | (-61,+75) ; (-35,+95) ; (-98,+133) ; (-49,+96) | SURVIVES PRE-2023 (weak rule; not a PASS) [strong version, CI lower limit > 0: against none] |
| NYAM_bundle | 8055 / 2857 | -0.49 / -1.30 | -148 / -401 | +331 / +295 | +549 / +947 | +400 / -52 | +589 / -87 | 6/8/5/9 | (-33,+724) ; (+220,+882) ; (-336,+1163) ; (+186,+970) | SURVIVES PRE-2023 (weak rule; not a PASS) [strong version, CI lower limit > 0: vs a, c] |

## Year by year (2013-2026; 2023 and 2026 partial; benchmark columns are the mean of 100 draws, (b) is the deterministic opposite side)

### N_REL_rev

| year | n | mean pts/trade (2023-26 price scale) | $/wk 1 lot | excess vs P1c | vs (a) | vs (b) | vs (c) | benchmark $/wk P1c / (a) / (b) / (c) |
|--|--|--|--|--|--|--|--|--|
| 2013 | 69 | +0.20 | +1 | +89 | -6 | -83 | +56 | -88 / +7 / +84 / -55 |
| 2014 | 70 | -0.61 | -12 | +51 | -5 | +170 | +64 | -63 / -7 / -182 / -76 |
| 2015 | 53 | -3.82 | -78 | -73 | -24 | +168 | -52 | -5 / -54 / -246 / -26 |
| 2016 | 70 | +3.56 | +96 | +244 | +159 | +55 | +171 | -149 / -64 / +41 / -75 |
| 2017 | 66 | -2.08 | -53 | -23 | +5 | -18 | -16 | -30 / -58 / -35 / -36 |
| 2018 | 76 | -1.71 | -49 | +4 | +63 | -16 | +15 | -53 / -112 / -33 / -64 |
| 2019 | 71 | -2.84 | -70 | +34 | -46 | -191 | -36 | -104 / -25 / +120 / -34 |
| 2020 | 65 | -3.95 | -106 | +4 | +19 | +110 | -110 | -110 / -126 / -216 / +4 |
| 2021 | 70 | -1.13 | -31 | -4 | +81 | +1 | -34 | -26 / -112 / -31 / +4 |
| 2022 | 90 | +8.93 | +309 | +342 | +434 | +466 | +476 | -33 / -125 / -157 / -167 |
| 2023 (PRE|POST split Apr) | 85 | -6.63 | -217 | -323 | -122 | -435 | -211 | +106 / -95 / +218 / -6 |
| 2024 | 102 | +7.60 | +284 | +311 | +408 | +397 | +405 | -27 / -124 / -113 / -121 |
| 2025 | 75 | -5.96 | -163 | -165 | -54 | -374 | -113 | +2 / -109 / +211 / -50 |
| 2026 | 63 | +8.91 | +274 | +275 | +585 | +548 | +337 | -1 / -311 / -274 / -63 |

Pre-2023 verdict inputs (excess in $/wk; years 2013-2022; 95%% stationary-block bootstrap CI of the mean weekly excess over the 488 pre weeks): P1c: positive in 7 of 10 years, mean +45 (CI -59, +153), post-2023 mean +72; a: positive in 6 of 10 years, mean +57 (CI -42, +157), post-2023 mean +223; b: positive in 6 of 10 years, mean +51 (CI -110, +216), post-2023 mean +46; c: positive in 5 of 10 years, mean +38 (CI -64, +142), post-2023 mean +139

### ORBF

| year | n | mean pts/trade (2023-26 price scale) | $/wk 1 lot | excess vs P1c | vs (a) | vs (b) | vs (c) | benchmark $/wk P1c / (a) / (b) / (c) |
|--|--|--|--|--|--|--|--|--|
| 2013 | 246 | +3.43 | +318 | +225 | +366 | +821 | +530 | +93 / -48 / -503 / -212 |
| 2014 | 246 | +4.08 | +363 | +640 | +517 | +1017 | +552 | -277 / -153 / -653 / -188 |
| 2015 | 256 | +4.01 | +418 | +403 | +382 | +1046 | +617 | +16 / +37 / -628 / -199 |
| 2016 | 253 | -0.10 | -10 | +124 | +83 | +220 | +182 | -133 / -93 / -230 / -192 |
| 2017 | 254 | -1.97 | -192 | -63 | -79 | -173 | +25 | -129 / -113 / -20 / -218 |
| 2018 | 253 | -0.17 | -40 | -119 | +183 | +118 | +370 | +79 / -223 / -158 / -410 |
| 2019 | 249 | +2.42 | +286 | +537 | +436 | +777 | +540 | -251 / -150 / -492 / -254 |
| 2020 | 255 | -3.77 | -399 | -166 | -53 | -541 | -35 | -232 / -346 / +142 / -364 |
| 2021 | 253 | -2.94 | -286 | +95 | +62 | -366 | -32 | -381 / -348 / +79 / -254 |
| 2022 | 253 | -3.39 | -330 | -105 | -54 | -467 | -139 | -225 / -276 / +137 / -191 |
| 2023 (PRE|POST split Apr) | 254 | -2.04 | -199 | +83 | -144 | -158 | -142 | -283 / -55 / -41 / -58 |
| 2024 | 257 | -10.90 | -1012 | -396 | -571 | -1830 | -926 | -616 / -441 / +818 / -86 |
| 2025 | 256 | -4.47 | -510 | -164 | -158 | -824 | -351 | -345 / -352 / +315 / -159 |
| 2026 | 202 | +1.42 | +170 | +403 | +472 | +653 | +177 | -233 / -302 / -483 / -7 |

Pre-2023 verdict inputs (excess in $/wk; years 2013-2022; 95%% stationary-block bootstrap CI of the mean weekly excess over the 488 pre weeks): P1c: positive in 6 of 10 years, mean +171 (CI -8, +357), post-2023 mean -100; a: positive in 7 of 10 years, mean +197 (CI +32, +364), post-2023 mean -193; b: positive in 6 of 10 years, mean +272 (CI -104, +669), post-2023 mean -747; c: positive in 7 of 10 years, mean +264 (CI +73, +446), post-2023 mean -388

### ONRTH

| year | n | mean pts/trade (2023-26 price scale) | $/wk 1 lot | excess vs P1c | vs (a) | vs (b) | vs (c) | benchmark $/wk P1c / (a) / (b) / (c) |
|--|--|--|--|--|--|--|--|--|
| 2013 | 181 | +1.41 | +96 | +358 | +162 | +398 | +225 | -262 / -66 / -302 / -129 |
| 2014 | 172 | +4.91 | +348 | +528 | +412 | +817 | +469 | -180 / -64 / -469 / -121 |
| 2015 | 141 | -1.70 | -115 | +70 | -74 | -123 | -21 | -185 / -41 / +8 / -94 |
| 2016 | 143 | -3.24 | -178 | -32 | -59 | -239 | -2 | -146 / -119 / +61 / -176 |
| 2017 | 160 | +3.13 | +193 | +152 | +285 | +507 | +341 | +41 / -92 / -315 / -148 |
| 2018 | 148 | -1.36 | -76 | -3 | +56 | -41 | +214 | -74 / -132 / -36 / -290 |
| 2019 | 129 | +1.28 | +64 | +48 | +197 | +225 | +155 | +16 / -133 / -161 / -91 |
| 2020 | 128 | +3.11 | +153 | +251 | +313 | +450 | +283 | -98 / -161 / -297 / -131 |
| 2021 | 150 | +5.79 | +334 | +634 | +457 | +808 | +486 | -299 / -123 / -474 / -152 |
| 2022 | 161 | -12.21 | -756 | -733 | -499 | -1320 | -656 | -22 / -257 / +564 / -100 |
| 2023 (PRE|POST split Apr) | 153 | -0.18 | -10 | +211 | +193 | +156 | +71 | -221 / -203 / -167 / -82 |
| 2024 | 153 | +0.97 | +56 | +175 | +302 | +278 | +235 | -119 / -246 / -222 / -179 |
| 2025 | 152 | -3.09 | -158 | -47 | +121 | -199 | -33 | -110 / -279 / +41 / -125 |
| 2026 | 112 | +7.42 | +376 | +613 | +858 | +860 | +468 | -236 / -482 / -484 / -91 |

Pre-2023 verdict inputs (excess in $/wk; years 2013-2022; 95%% stationary-block bootstrap CI of the mean weekly excess over the 488 pre weeks): P1c: positive in 7 of 10 years, mean +127 (CI -33, +285), post-2023 mean +224; a: positive in 7 of 10 years, mean +120 (CI -24, +257), post-2023 mean +371; b: positive in 6 of 10 years, mean +140 (CI -159, +427), post-2023 mean +271; c: positive in 7 of 10 years, mean +152 (CI +10, +299), post-2023 mean +164

### VWAPF

| year | n | mean pts/trade (2023-26 price scale) | $/wk 1 lot | excess vs P1c | vs (a) | vs (b) | vs (c) | benchmark $/wk P1c / (a) / (b) / (c) |
|--|--|--|--|--|--|--|--|--|
| 2013 | 286 | +4.30 | +495 | +589 | +732 | +1214 | +729 | -94 / -238 / -719 / -234 |
| 2014 | 323 | -0.99 | -178 | -84 | -3 | +32 | +139 | -93 / -175 / -209 / -317 |
| 2015 | 378 | +0.30 | +67 | +588 | +78 | +422 | +545 | -521 / -11 / -355 / -478 |
| 2016 | 334 | +1.59 | +205 | +388 | +362 | +740 | +286 | -184 / -157 / -535 / -81 |
| 2017 | 274 | -4.59 | -483 | -276 | -262 | -729 | -179 | -207 / -221 / +246 / -304 |
| 2018 | 423 | -6.68 | -1091 | -862 | -540 | -1829 | -277 | -229 / -552 / +738 / -814 |
| 2019 | 326 | -2.20 | -269 | -97 | +119 | -158 | -153 | -172 / -388 / -112 / -116 |
| 2020 | 490 | -2.41 | -435 | -191 | +329 | -364 | +295 | -244 / -763 / -71 / -729 |
| 2021 | 370 | -4.20 | -598 | -400 | +84 | -947 | -383 | -197 / -681 / +349 / -214 |
| 2022 | 590 | +1.17 | +266 | +535 | +1142 | +981 | +608 | -269 / -877 / -716 / -343 |
| 2023 (PRE|POST split Apr) | 423 | +1.75 | +285 | +431 | +659 | +926 | +202 | -146 / -374 / -641 / +83 |
| 2024 | 367 | +1.16 | +135 | +248 | +1005 | +545 | +167 | -113 / -870 / -411 / -32 |
| 2025 | 426 | -2.09 | -294 | -181 | +664 | -116 | -51 | -113 / -958 / -178 / -242 |
| 2026 | 332 | +1.58 | +227 | +334 | +927 | +839 | +416 | -107 / -700 / -611 / -188 |

Pre-2023 verdict inputs (excess in $/wk; years 2013-2022; 95%% stationary-block bootstrap CI of the mean weekly excess over the 488 pre weeks): P1c: positive in 4 of 10 years, mean +33 (CI -226, +284), post-2023 mean +171; a: positive in 7 of 10 years, mean +232 (CI -30, +487), post-2023 mean +769; b: positive in 5 of 10 years, mean -12 (CI -542, +505), post-2023 mean +423; c: positive in 6 of 10 years, mean +173 (CI -95, +442), post-2023 mean +137

### VB2NYPM_T1

| year | n | mean pts/trade (2023-26 price scale) | $/wk 1 lot | excess vs P1c | vs (a) | vs (b) | vs (c) | benchmark $/wk P1c / (a) / (b) / (c) |
|--|--|--|--|--|--|--|--|--|
| 2013 | 137 | +0.95 | +51 | +137 | +88 | +145 | +137 | -86 / -37 / -94 / -86 |
| 2014 | 130 | -1.78 | -91 | -9 | -22 | -19 | -14 | -82 / -69 / -72 / -77 |
| 2015 | 174 | -2.95 | -197 | -127 | -131 | -162 | -119 | -71 / -66 / -35 / -78 |
| 2016 | 147 | -3.11 | -176 | -118 | -140 | -178 | -121 | -57 / -35 / +3 / -55 |
| 2017 | 118 | -0.28 | -13 | +26 | +60 | +173 | +44 | -38 / -73 / -186 / -57 |
| 2018 | 164 | -0.51 | -24 | +46 | +68 | +107 | +75 | -71 / -93 / -131 / -100 |
| 2019 | 147 | -0.37 | -39 | -30 | +28 | +116 | +0 | -9 / -67 / -155 / -39 |
| 2020 | 149 | +0.65 | +48 | +60 | +176 | +80 | +67 | -12 / -128 / -32 / -19 |
| 2021 | 129 | -7.16 | -355 | -297 | -241 | -492 | -276 | -59 / -115 / +136 / -80 |
| 2022 | 147 | +2.13 | +121 | +298 | +316 | +196 | +359 | -177 / -195 / -75 / -238 |
| 2023 (PRE|POST split Apr) | 155 | +1.99 | +119 | +203 | +260 | +383 | +142 | -85 / -142 / -264 / -24 |
| 2024 | 146 | +1.56 | +75 | +138 | +262 | +136 | +104 | -63 / -188 / -62 / -29 |
| 2025 | 157 | -0.94 | -46 | +43 | +148 | -47 | +4 | -89 / -193 / +1 / -50 |
| 2026 | 94 | +3.17 | +145 | +236 | +386 | +314 | +224 | -91 / -240 / -168 / -79 |

Pre-2023 verdict inputs (excess in $/wk; years 2013-2022; 95%% stationary-block bootstrap CI of the mean weekly excess over the 488 pre weeks): P1c: positive in 5 of 10 years, mean +7 (CI -61, +75), post-2023 mean +139; a: positive in 6 of 10 years, mean +28 (CI -35, +95), post-2023 mean +251; b: positive in 6 of 10 years, mean +19 (CI -98, +133), post-2023 mean +139; c: positive in 6 of 10 years, mean +21 (CI -49, +96), post-2023 mean +103

### NYAM_bundle

| year | n | mean pts/trade (2023-26 price scale) | $/wk 1 lot | excess vs P1c | vs (a) | vs (b) | vs (c) | benchmark $/wk P1c / (a) / (b) / (c) |
|--|--|--|--|--|--|--|--|--|
| 2013 | 713 | n/a | +909 | +1172 | +1260 | +2434 | +1484 | -263 / -352 / -1525 / -575 |
| 2014 | 741 | n/a | +534 | +1083 | +926 | +1865 | +1160 | -550 / -392 / -1331 / -626 |
| 2015 | 775 | n/a | +370 | +1061 | +386 | +1345 | +1142 | -691 / -15 / -975 / -772 |
| 2016 | 730 | n/a | +17 | +480 | +385 | +720 | +466 | -463 / -369 / -704 / -450 |
| 2017 | 688 | n/a | -483 | -188 | -57 | -395 | +187 | -295 / -426 / -88 / -670 |
| 2018 | 824 | n/a | -1208 | -984 | -301 | -1752 | +307 | -224 / -907 / +544 / -1514 |
| 2019 | 704 | n/a | +81 | +488 | +752 | +845 | +542 | -407 / -671 / -765 / -461 |
| 2020 | 873 | n/a | -681 | -106 | +589 | -455 | +543 | -574 / -1269 / -226 / -1224 |
| 2021 | 773 | n/a | -550 | +328 | +603 | -505 | +71 | -878 / -1153 / -45 / -620 |
| 2022 | 1004 | n/a | -820 | -303 | +589 | -805 | -187 | -517 / -1410 / -15 / -633 |
| 2023 (PRE|POST split Apr) | 830 | n/a | +75 | +726 | +708 | +924 | +132 | -650 / -632 / -849 / -57 |
| 2024 | 777 | n/a | -821 | +27 | +735 | -1006 | -524 | -848 / -1557 / +185 / -297 |
| 2025 | 834 | n/a | -961 | -393 | +628 | -1139 | -435 | -568 / -1589 / +178 / -526 |
| 2026 | 646 | n/a | +773 | +1349 | +2257 | +2351 | +1060 | -576 / -1484 / -1578 / -287 |

Pre-2023 verdict inputs (excess in $/wk; years 2013-2022; 95%% stationary-block bootstrap CI of the mean weekly excess over the 488 pre weeks): P1c: positive in 6 of 10 years, mean +331 (CI -33, +724), post-2023 mean +295; a: positive in 8 of 10 years, mean +549 (CI +220, +882), post-2023 mean +947; b: positive in 5 of 10 years, mean +400 (CI -336, +1163), post-2023 mean -52; c: positive in 9 of 10 years, mean +589 (CI +186, +970), post-2023 mean -87

## Sensitivities and limits
* V1 (unscaled 60/60, VWAPF D = 10 pt; pre-2023 these are huge brackets relative to price): ORBF V1 (unscaled 60/60) $/wk pre -188 / post -316; ONRTH V1 (unscaled 60/60) $/wk pre -39 / post +125; VWAPF V1 (unscaled 60/60) $/wk pre -95 / post +261.
* N_REL_rev has no release-day filter in the code; 47% of its post-2023 trades fall on a DISCOVER_CALENDAR 08:30 release day (calendar starts 2023-04-05; no 08:30 release dates exist on disk before that and none were downloaded; all pre-2023 days with an 08:29-08:34 move >= 0.5 ATR are traded as the code does).
* Roll days (DW drops 110 roll days; I keep them): real mean pts per trade all vs excluding roll-day trades: N_REL_rev +0.33 (all) vs +0.59 (excl. 41 roll-day trades); ORBF -1.10 (all) vs -1.13 (excl. 107 roll-day trades); ONRTH +0.31 (all) vs +0.41 (excl. 65 roll-day trades); VWAPF -0.84 (all) vs -0.74 (excl. 149 roll-day trades); VB2NYPM_T1 -0.54 (all) vs -0.43 (excl. 63 roll-day trades).
* Cross-check with ZL-1 DIS-W (calibration there: VB2NYPM_T1 weekly corr 0.80, ONRTH 0.92, VWAPF 0.875 vs 0.90 bar): the same lines were run independently; DW covers VB2NYPM_T1, ONRTH, VWAPF (no ORBF, no bundle), I own all four plus the bundle and the benchmarks.
* Costs at 2023-26 tick conditions in every year; pre-2021 halt/session-hour changes not modelled; fills are 1-minute; benchmarks (a)-(c) draw 100 worlds, p-values are not computed here (the verdict rule uses year signs and the block bootstrap of the weekly excess); bundle benchmark = sum of the three books' benchmark means; the bundle row is not independent of its members.
* The verdict rule's CI criterion is weak by design (upper limit >= 0); the strong version (lower limit > 0) is in the summary table CI column.
