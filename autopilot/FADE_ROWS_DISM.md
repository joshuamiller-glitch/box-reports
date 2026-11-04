# FADE_ROWS_DISM - DIS-M drift benchmark (BASE-4; prereg DISM_prereg.md sha256 f32b531299744a09a4088c010839c53dbe7dde12df48d3f56bf6aaae52b10104 + addendum 1 e28ad121ccbeb072e43b94df6e4d5c381e263e4909ca5c380fc328231231a3d3). $/wk. Nothing is a PASS.

## 1. Unconditional benchmark books, RANDOM-TIME (100 draws, one trade per day-session-side), 1 lot, live fill model
| session | side | exit | L6M | HOLD | MID | PRE | X' | MDE_L6M | 5-95% L6M |
|--|--|--|--|--|--|--|--|--|--|
| asia | LONG | X1 | -184 | -168 | -123 | -41 | -131 | 1017 | -769 .. +321 |
| asia | LONG | X2 | -77 | -103 | -254 | +43 | -146 | 1390 | -821 .. +900 |
| asia | LONG | X3 | +5 | +26 | +362 | +18 | -312 | 1402 | -646 .. +719 |
| asia | SHORT | X1 | -30 | -36 | -107 | -164 | -98 | 1026 | -610 .. +574 |
| asia | SHORT | X2 | -177 | -111 | +11 | -184 | -83 | 1445 | -942 .. +537 |
| asia | SHORT | X3 | -311 | -277 | -483 | -315 | +6 | 1393 | -918 .. +538 |
| london | LONG | X1 | -214 | -172 | -187 | -56 | -54 | 1098 | -831 .. +438 |
| london | LONG | X2 | -461 | -319 | -162 | -139 | -40 | 1545 | -1196 .. +387 |
| london | LONG | X3 | -344 | -256 | -74 | -241 | +249 | 1450 | -1027 .. +357 |
| london | SHORT | X1 | -6 | -70 | -99 | -153 | -139 | 1084 | -543 .. +668 |
| london | SHORT | X2 | -76 | -13 | +26 | -186 | -158 | 1563 | -875 .. +759 |
| london | SHORT | X3 | +116 | -25 | -285 | -75 | -529 | 1452 | -693 .. +992 |
| nyam | LONG | X1 | -96 | -81 | +227 | -45 | +121 | 1338 | -1011 .. +670 |
| nyam | LONG | X2 | -254 | -52 | +232 | -59 | +313 | 1737 | -981 .. +501 |
| nyam | LONG | X3 | +70 | +14 | +234 | -194 | +359 | 1406 | -579 .. +742 |
| nyam | SHORT | X1 | -108 | -143 | -449 | -206 | -320 | 1315 | -720 .. +635 |
| nyam | SHORT | X2 | -350 | -385 | -745 | -193 | -618 | 1796 | -1260 .. +574 |
| nyam | SHORT | X3 | -188 | -249 | -576 | -79 | -745 | 1399 | -882 .. +608 |
| nypm | LONG | X1 | -321 | -385 | -615 | -214 | +23 | 1217 | -969 .. +272 |
| nypm | LONG | X2 | -697 | -602 | -769 | -350 | +212 | 1643 | -1346 .. -102 |
| nypm | LONG | X3 | -395 | -390 | -234 | -308 | +181 | 1469 | -1169 .. +197 |
| nypm | SHORT | X1 | +53 | +94 | +267 | -10 | -255 | 1218 | -614 .. +668 |
| nypm | SHORT | X2 | +154 | +87 | +125 | -101 | -399 | 1767 | -681 .. +857 |
| nypm | SHORT | X3 | +180 | +148 | -16 | +68 | -410 | 1457 | -500 .. +871 |

Exit shapes: X1 60/60 T60 min; X2 stop 60 / target 120 / T120 min; X3 live 60/60 flat 16:55. Fixed-clock C15 / C60 and the half-hour profile: /mnt/l2/l2vast/ds3_base4/dism_bench.csv, dism_bench_profile.csv.

## 2. Live groups: real replica vs matched drift (P1c = same side, entry delayed 5..120 min; P1x = look-ahead control, entry anywhere in the session)
| cell | L6M real / drift_c / drift_x | HOLD real / drift_c / drift_x | PRE real / drift_c | X' real / drift_c | P1c p (L6M / HOLD) | P2 side p | P3 day p | family max-T (L6M / HOLD) | label |
|--|--|--|--|--|--|--|--|--|--|
| LIVE KB|asia | +1402 / +262 / +3083 | +1217 / +500 / +2618 | +871 / +762 | -848 / -242 | 0.12 / 0.13 | 0.11 / 0.06 | 0.04 / 0.04 | 0.99 / 0.98 | DRIFT ONLY / inside the placebo band |
| LIVE KB|london | -368 / -1125 / +1406 | -156 / -454 / +1753 | +33 / -111 | -175 / -37 | 0.20 / 0.31 | 0.41 / 0.32 | 0.58 / 0.46 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE KB|nyam | -1915 / -550 / +1203 | -2010 / -273 / +1689 | +914 / +333 | +277 / -290 | 0.97 / 1.00 | 0.93 / 0.99 | 0.99 / 1.00 | 1.00 / 1.00 | NEGATIVE EXCESS (below the causal drift) |
| LIVE KB|nypm | +122 / +89 / +2200 | -441 / +383 / +1955 | +119 / -299 | -204 / -294 | 0.48 / 0.94 | 0.28 / 0.54 | 0.42 / 0.70 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE PE|asia | +9003 / +5374 / +15391 | +5736 / +3894 / +13641 | +2802 / +770 | -1337 / -362 | 0.17 / 0.23 | 0.02 / 0.03 | 0.02 / 0.01 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE PE|london | +4375 / -1309 / +10918 | +2798 / +164 / +10602 | -1949 / -1434 | +334 / +663 | 0.02 / 0.07 | 0.09 / 0.09 | 0.06 / 0.08 | 0.49 / 0.92 | DRIFT ONLY / inside the placebo band |
| LIVE PE|nyam | -5438 / -239 / +9145 | -5265 / -1570 / +9521 | +3459 / +1542 | +2602 / +46 | 0.93 / 0.96 | 0.68 / 0.80 | 0.89 / 0.95 | 1.00 / 1.00 | NEGATIVE EXCESS (below the causal drift) |
| LIVE SM|asia | +1627 / -1477 / +1914 | +773 / -824 / +1791 | +1175 / +690 | +1226 / +1318 | 0.02 / 0.03 | 0.07 / 0.17 | 0.12 / 0.11 | 0.14 / 0.48 | DRIFT ONLY / inside the placebo band |
| LIVE SM|london | -140 / -716 / +2579 | -146 / -835 / +2342 | +630 / +339 | +67 / -214 | 0.30 / 0.16 | 0.38 / 0.43 | 0.41 / 0.38 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE HM|asia | +2007 / +1841 / +7609 | +4259 / +1950 / +6560 | +865 / +479 | -550 / -831 | 0.45 / 0.02 | 0.10 / 0.01 | 0.08 / 0.01 | 1.00 / 0.35 | DRIFT ONLY / inside the placebo band |
| LIVE HM|nyam | -235 / -302 / +1346 | +305 / -179 / +1592 | +485 / +64 | -260 / -112 | 0.48 / 0.11 | 0.52 / 0.13 | 0.43 / 0.12 | 1.00 / 0.94 | DRIFT ONLY / inside the placebo band |
| LIVE MV|london | -362 / -405 / +3543 | +62 / +121 / +3514 | -145 / -325 | +25 / +393 | 0.49 / 0.61 | 0.38 / 0.26 | 0.57 / 0.34 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE MV|nyam | -168 / -360 / +1610 | +19 / -174 / +1945 | +917 / +211 | -546 / -7 | 0.41 / 0.31 | 0.32 / 0.20 | 0.45 / 0.28 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE PB|asia | +12 / +532 / +5992 | +213 / +359 / +5044 | +988 / +579 | +227 / +318 | 0.81 / 0.66 | 0.38 / 0.27 | 0.29 / 0.14 | 1.00 / 1.00 | NEGATIVE EXCESS (below the causal drift) |
| LIVE KB|pooled | -759 / -1323 / +7891 | -1391 / +156 / +8015 | +1937 / +685 | -951 / -863 | 0.36 / 0.93 | 0.28 / 0.36 | 0.51 / 0.66 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE PE|pooled | +7941 / +3826 / +35454 | +3269 / +2487 / +33764 | +4313 / +878 | +1599 / +347 | 0.18 / 0.40 | 0.06 / 0.04 | 0.05 / 0.08 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE SM|pooled | +1487 / -2193 / +4492 | +627 / -1659 / +4132 | +1805 / +1029 | +1293 / +1104 | 0.01 / 0.01 | 0.10 / 0.26 | 0.09 / 0.13 | 0.36 / 0.42 | DRIFT ONLY / inside the placebo band |
| LIVE HM|pooled | +1772 / +1538 / +8954 | +4563 / +1770 / +8152 | +1350 / +543 | -809 / -943 | 0.45 / 0.01 | 0.09 / 0.01 | 0.11 / 0.01 | 1.00 / 0.15 | DRIFT ONLY / inside the placebo band |
| LIVE MV|pooled | -530 / -765 / +5153 | +81 / -53 / +5460 | +772 / -115 | -521 / +385 | 0.43 / 0.38 | 0.36 / 0.11 | 0.50 / 0.26 | 1.00 / 1.00 | DRIFT ONLY / inside the placebo band |
| LIVE PB|pooled | +12 / +532 / +5992 | +213 / +359 / +5044 | +988 / +579 | +227 / +318 | 0.81 / 0.66 | 0.38 / 0.27 | 0.29 / 0.14 | 1.00 / 1.00 | NEGATIVE EXCESS (below the causal drift) |

## 3. Candidates re-expressed as EXCESS over the matched drift
| book | trades | L1M | L3M | L6M | HOLD | MID | PRE | X' | drift_c L6M / HOLD | excess L6M / HOLD | P1c p (L6M / HOLD) | P2 p | P3 p | family max-T (L6M / HOLD) | BH q (L6M / HOLD) | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| SHADOW NYAM ONRTH (1 lot) | 543 | +169 | +24 | +485 | +794 | +1958 | -25 | +35 | -174 / -287 | +660 / +1081 | 0.03 / 0.01 | 0.08 / 0.01 | 0.03 / 0.01 | 0.31 / 0.01 | 0.11 / 0.05 | DRIFT ONLY / inside the placebo band |
| SHADOW NYAM VWAPF (1 lot) | 3273 | -117 | +427 | +663 | +1247 | +3855 | -202 | +43 | -219 / -272 | +882 / +1519 | 0.08 / 0.01 | 0.08 / 0.01 | 0.09 / 0.01 | 0.93 / 0.08 | 0.21 / 0.05 | DRIFT ONLY / inside the placebo band |
| SHADOW NYAM ORBF (1 lot) | 914 | +1101 | +769 | +1052 | +745 | +790 | -811 | -406 | -150 / -292 | +1201 / +1037 | 0.01 / 0.01 | 0.01 / 0.01 | 0.02 / 0.01 | 0.08 / 0.02 | 0.06 / 0.05 | EXCESS SURVIVES (nothing is a PASS) |
| SHADOW FADE VB2NYPM_T1 (1 lot) | 523 | +212 | +128 | +384 | +238 | +17 | +38 | +20 | -72 / -104 | +456 / +342 | 0.01 / 0.01 | 0.01 / 0.03 | 0.01 / 0.01 | 0.05 / 0.03 | 0.06 / 0.05 | EXCESS SURVIVES (nothing is a PASS) |
| SHADOW FADE PDASIA_T2 (1 lot) | 317 | +695 | +604 | +234 | +299 | +576 | +0 | -16 | +20 / +12 | +214 / +287 | 0.09 / 0.01 | 0.05 / 0.02 | 0.03 / 0.01 | 0.99 / 0.16 | 0.22 / 0.05 | DRIFT ONLY / inside the placebo band |
| SHADOW FADE VB2NYAM_T3 (1 lot) | 893 | +10 | +631 | +402 | +356 | -20 | +15 | -107 | -59 / -109 | +461 / +466 | 0.07 / 0.04 | 0.12 / 0.04 | 0.03 / 0.02 | 0.95 / 0.63 | 0.21 / 0.13 | DRIFT ONLY / inside the placebo band |
| SHADOW FADE OR15NYAM_T2 (1 lot) | 935 | +900 | +2439 | +2663 | +738 | -1592 | +6 | -196 | +766 / +787 | +1897 / -49 | 0.01 / 0.56 | 0.01 / 0.17 | 0.01 / 0.03 | 0.02 / 1.00 | 0.06 / 0.71 | DRIFT ONLY / inside the placebo band |
| DIS-C Sunday 18:30 with-trend (re-derived, 1 lot) | 185 | +584 | +272 | +509 | +320 | +623 | +118 | -13 | +150 / +103 | +358 / +217 | 0.03 / 0.06 | 0.03 / 0.17 | 0.01 / 0.04 | 0.67 / 0.86 | 0.11 / 0.17 | DRIFT ONLY / inside the placebo band |
| DIS-B P_REL_cont all sides (re-derived, 1 lot) | 227 | +155 | -3 | -54 | +3 | -1 | +20 | -31 | -50 / -87 | -4 / +90 | 0.50 / 0.15 | 0.60 / 0.38 | 0.57 / 0.35 | 1.00 / 1.00 | 0.59 / 0.30 | DRIFT ONLY / inside the placebo band |
| DIS-B P_REL_cont shorts only (re-derived, 1 lot) | 108 | -9 | -50 | -47 | -12 | -34 | +81 | -17 | +33 / -14 | -80 / +2 | 0.79 / 0.48 | 0.61 / 0.48 | 0.90 / 0.63 | 1.00 / 1.00 | 0.86 / 0.62 | DRIFT ONLY / inside the placebo band |
| DIS-I ROLL_WEEK|nyam|FADE|SH2 ($1200 risk) | 56 | +0 | +45 | +19 | +147 | +493 | -116 | +155 | +55 / +106 | -36 / +41 | 0.59 / 0.33 | 0.40 / 0.24 | 0.32 / 0.05 | 1.00 / 1.00 | 0.68 / 0.51 | DRIFT ONLY / inside the placebo band |
| DIS-I ME3|asia|CONT|SH2 ($1200 risk) | 81 | +364 | +453 | +310 | +284 | +161 | +7 | -76 | +58 / +187 | +253 / +97 | 0.07 / 0.23 | 0.01 / 0.01 | 0.01 / 0.02 | 0.82 / 1.00 | 0.21 / 0.40 | DRIFT ONLY / inside the placebo band |
| DIS-I MS3|asia|CONT|SH1 ($1200 risk) | 86 | +997 | +493 | +226 | +216 | +47 | +60 | +19 | +84 / +201 | +142 / +15 | 0.08 / 0.46 | 0.01 / 0.14 | 0.19 / 0.16 | 0.94 / 1.00 | 0.21 / 0.61 | DRIFT ONLY / inside the placebo band |
| DIS-I TOM|asia|CONT|SH1 ($1200 risk) | 113 | +1244 | +501 | +312 | +333 | -55 | +110 | -37 | +59 / +301 | +253 / +33 | 0.01 / 0.39 | 0.01 / 0.03 | 0.15 / 0.07 | 0.56 / 1.00 | 0.06 / 0.55 | DRIFT ONLY / inside the placebo band |
| DIS-I NFP|nypm|DRIFT_S|SH1 ($1200 risk) | 40 | +125 | +52 | +267 | +193 | +33 | +26 | -78 | +97 / +63 | +170 / +129 | 0.01 / 0.01 | 0.06 / 0.04 | 0.23 / 0.17 | 0.02 / 0.16 | 0.06 / 0.05 | DRIFT ONLY / inside the placebo band |
| DIS-I RETAIL|nypm|DRIFT_S|SH2 ($1200 risk) | 43 | -247 | +87 | +184 | +194 | +289 | +44 | +179 | -41 / +1 | +224 / +193 | 0.03 / 0.03 | 0.10 / 0.04 | 0.04 / 0.03 | 0.41 / 0.20 | 0.11 / 0.11 | DRIFT ONLY / inside the placebo band |
| Q11 TD1_20 WITH PB_asia LONG SH1 (live lots) | 2193 | +293 | +321 | +366 | +290 | +502 | +109 | -15 | +155 / +154 | +212 / +136 | 0.12 / 0.11 | 0.13 / 0.03 | 0.13 / 0.07 | 0.99 / 0.95 | 0.26 / 0.25 | DRIFT ONLY / inside the placebo band |
| Q11 TD3_50 COUNTER PE_nyam ALL SH1 (live lots) | 1189 | +4446 | +8391 | +4368 | +4253 | -1200 | +2057 | +2876 | +2282 / +1009 | +2085 / +3244 | 0.20 / 0.06 | 0.22 / 0.11 | 0.07 / 0.04 | 1.00 / 0.79 | 0.35 / 0.17 | DRIFT ONLY / inside the placebo band |
| Q11 TD3_20 COUNTER PE_asia SHORT SH2 (live lots) | 604 | +950 | +1455 | +3488 | +2536 | -658 | +2 | -547 | +2677 / +2793 | +811 / -257 | 0.36 / 0.60 | 0.10 / 0.10 | 0.06 / 0.04 | 1.00 / 1.00 | 0.56 / 0.73 | DRIFT ONLY / inside the placebo band |

## 4. Replica stack with the drift hedged out (carrying weeks dropped for maxDD)
| window | engine core mean | replica mean | causal drift mean | hedged mean | replica maxDD | hedged maxDD | look-ahead drift mean (P1x) |
|--|--|--|--|--|--|--|--|
| L1M | +5305 | -20211 | +25533 | -45744 | +136044 | +228719 | +64812 |
| L2M | +13860 | +13415 | +18008 | -4593 | +136044 | +174738 | +72358 |
| L3M | +7746 | -320 | +9030 | -9351 | +136044 | +174738 | +65760 |
| L6M | +26999 | +9923 | +1616 | +8308 | +136044 | +174738 | +67936 |
| HOLD | +22589 | +7363 | +3062 | +4302 | +237460 | +210861 | +64566 |
| MID | +16851 | -4433 | -2342 | -2091 | +198904 | +196519 | +54304 |
| PRE | +13202 | +11164 | +3599 | +7565 | +190841 | +106930 | +38822 |
| X' | +3293 | +838 | +349 | +489 | +132199 | +91036 | +17386 |

Genuine PA9 maxDD cut of the hedged vs the replica stack (+ = hedging reduces the drawdown): L6M -53.4%, HOLD +10.1%, MID +5.2%, PRE +33.5%, X' +25.3%; daily correlation replica vs engine core 0.76; replica total / engine core total 0.63.
