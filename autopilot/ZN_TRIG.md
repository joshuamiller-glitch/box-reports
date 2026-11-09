# ZN_TRIG - zones as ENTRY TRIGGERS (T-ZONES-EXHAUST section 5), refreshed 2026-11-09 18:27 Z. Research only, Shadow only, no PASS claims, ROLL-EXCL stack (sz_core.Base rollw) for stack columns.
**Price source:** 1-s STATE arrays (_th_state/days, 2023-04-03 .. 2026-11-05; NOT bars1m_NQ.npz), 14 quarterly rolls back-adjusted at the roll second, round numbers on raw price. The 1-s state data runs to 2026-11-05 so no series ends 10-16; windows as of 2026-11-09; held-out live week = label days 2026-11-02..05 (never used to pick).
**Grid:** 44 level families (114 lines) x 6 triggers (touch-reject, break-through, failed-break fade, break-and-retest, delta turn at level, absorption) x bars 1m/5m x zone w x 6 sessions x 192 brackets = 888576 scored cells in 44 families run so far; 60 null draws of random same-count entries within session (same side split, same brackets).

**Plain sentence:** 33198 of 888576 cells pass the tolerant gate with |weekly corr to stack| <= .3 and a positive HOLD stack Calmar gain; 10832 of those have own placebo p <= .10; the smallest family (max-stat over all 888576 cells) p of ANY cell is 0.885, so the best trigger books are indistinguishable from the best of random entries.

## Best gate-passing cell per level family (ranked by pooled weekly t); equal-$-risk lots R=$1200, fees $4.84 RT, 1 tick slippage each side; means are $/week at those lots, carry weeks dropped from means; maxDD on all weeks
| family | trigger | bar | w | session | bracket | events | L6M | HOLD | MID | PRE | X' | maxDD HOLD | dCalmar HOLD (stack+book) | WF OOS mean/wk | live wk $ | corr wk | p own | p fam | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| KC2.5_15m | BRK | 1m | 0 | asia | stop 48 pts, tgt 3R, time 120 min | 1628 | +2418 | +1617 | +1232 | +660 | +106 | 16403 | +0.85 | +1322 | +7002 | +0.15 | 0.016 | 0.967 | CANDIDATE (own-p only; family p 0.97) |
| BB_60m | BRK | 1m | 0 | asia | stop 48 pts, tgt 3R, time 120 min | 616 | +1387 | +880 | +578 | +386 | +79 | 5963 | +0.38 | +405 | +1871 | +0.17 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| EMA200_5m | BR | 1m | 0 | nyam | stop 48 pts, tgt 1R, time 30 min | 392 | +174 | +513 | +867 | +192 | -83 | 6789 | +0.27 | +101 | +955 | -0.06 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| PD_RTH | BR | 1m | 0 | nyam | stop = structure +5, tgt 2R, time 30 min | 307 | +1173 | +921 | +1235 | +401 | +342 | 18667 | +0.17 | +98 | -1380 | -0.04 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| RN100 | BRK | 1m | 0 | asia | stop 48 pts, tgt 40 pts, time 120 min | 3513 | +2703 | +1752 | +1645 | +129 | +31 | 13735 | +1.41 | +379 | -5028 | +0.04 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| OR5 | BR | 1m | 0 | nypm | stop 32 pts, no tgt, time 60 min | 296 | +308 | +800 | +152 | +613 | +854 | 21692 | +0.30 | +651 | +390 | -0.07 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| RN50 | ABS | 5m | 3 | nyam | stop 48 pts, tgt 2R, time 120 min | 2678 | +1812 | +1409 | -648 | +873 | +938 | 14897 | +0.55 | -260 | +2836 | +0.14 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| BB_15m | BRK | 5m | 0 | asia | stop 48 pts, tgt 3R, time 120 min | 1495 | +2684 | +1347 | +511 | +543 | +7 | 16519 | +0.58 | +296 | +7091 | +0.22 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| KC1.5_60m | BR | 5m | 0 | nyam | stop = structure +5, tgt 40 pts, time 120 min | 290 | +390 | +398 | +261 | +297 | +130 | 8167 | +0.21 | +210 | +0 | +0.08 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| KC1.5_5m | DT | 1m | 2 | asia | stop 48 pts, tgt 1.5R, time 120 min | 10224 | +3841 | +1772 | +1724 | +236 | +413 | 30685 | +1.62 | +49 | +9737 | +0.26 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| KC2.5_5m | FB | 1m | 2 | pre | stop 48 pts, tgt 10 pts, time 30 min | 308 | +179 | +99 | +244 | +121 | -70 | 2939 | +0.05 | +111 | +0 | +0.03 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| EMA20_60m | DT | 1m | 2 | london | stop 48 pts, tgt 40 pts, time 60 min | 1392 | +486 | +578 | +207 | +148 | +254 | 5074 | +0.42 | +308 | +1486 | -0.16 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| SW15m2 | BR | 1m | 0 | london | stop 24 pts, tgt 10 pts, time 120 min | 502 | +607 | +286 | -21 | +164 | +181 | 4363 | +0.31 | -42 | +3513 | +0.04 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| GRID0.25 | TR | 5m | 3 | close | stop 32 pts, tgt 10 pts, time 120 min | 166 | +78 | +9 | +130 | +156 | +70 | 3138 | +0.00 | +84 | +0 | -0.07 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| KC2.5_60m | ABS | 5m | 3 | nyam | stop 48 pts, tgt 40 pts, time 120 min | 381 | +184 | +270 | +192 | +31 | +302 | 3259 | +0.36 | +62 | -175 | +0.02 | 0.033 | 1.000 | LEAD (own-p only; WF fails) |
| PD_FULL | BRK | 1m | 0 | nyam | stop 48 pts, tgt 40 pts, time 120 min | 1381 | +898 | +664 | +723 | +423 | -290 | 8205 | +0.28 | +159 | +795 | +0.06 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| EMA20_5m | TR | 5m | 3 | london | stop 48 pts, tgt 3R, time 120 min | 2624 | +1146 | +1256 | +2315 | +361 | +129 | 6392 | +0.55 | +242 | +1941 | +0.00 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| EMA50_60m | DT | 1m | 2 | london | stop 48 pts, tgt 3R, time 120 min | 694 | +966 | +407 | +50 | +197 | +324 | 6603 | +0.21 | -171 | +1905 | -0.09 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| EMA50_15m | BRK | 1m | 0 | pre | stop = structure +5, no tgt, time 60 min | 435 | +653 | +2719 | +5718 | +1235 | +979 | 14258 | +3.04 | +1018 | -1079 | -0.03 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| IB30X15 | TR | 1m | 2 | nypm | stop 48 pts, no tgt, time 30 min | 631 | +44 | +44 | +626 | +384 | -22 | 10173 | +0.01 | +34 | +1675 | +0.04 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| PD_C | BRK | 5m | 0 | london | stop 48 pts, tgt 40 pts, time 120 min | 595 | +24 | +236 | +659 | +164 | +65 | 4536 | +0.24 | -104 | -349 | -0.09 | 0.033 | 1.000 | LEAD (own-p only; WF fails) |
| IB30X2 | TR | 1m | 2 | close | stop 8 pts, tgt 2R, time 60 min | 191 | +169 | +281 | +155 | +233 | +400 | 9386 | +0.24 | +18 | +0 | +0.08 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| RVWAP1 | DT | 5m | 3 | nypm | stop 32 pts, tgt 1.5R, time 60 min | 242 | +552 | +673 | +992 | -61 | +164 | 5828 | +0.23 | +249 | +0 | -0.03 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| EMA50_5m | FB | 1m | 0 | london | stop 48 pts, tgt 1.5R, time 120 min | 1398 | +896 | +793 | +1475 | +512 | -201 | 23091 | +0.33 | +849 | +5056 | +0.20 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| EMA20_15m | TR | 5m | 3 | nyam | stop = structure +5, tgt 10 pts, time 60 min | 330 | +262 | +141 | +106 | +112 | +319 | 3668 | +0.07 | +77 | +0 | +0.02 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| BB_5m | TR | 5m | 3 | nypm | stop 48 pts, tgt 3R, time 120 min | 929 | +1130 | +730 | +1082 | +264 | +134 | 9277 | +0.34 | +52 | +1905 | -0.00 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| EMA200_15m | ABS | 1m | 2 | london | stop 16 pts, tgt 2R, time 120 min | 314 | +374 | +314 | +442 | +360 | +814 | 8014 | +0.16 | +179 | -1319 | -0.02 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| IB60 | FB | 1m | 0 | nypm | stop 48 pts, tgt 40 pts, time 60 min | 753 | +439 | +430 | +800 | +160 | +116 | 6074 | +0.23 | +47 | -175 | +0.14 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| ON | BRK | 5m | 0 | close | stop 48 pts, tgt 10 pts, time 30 min | 311 | +171 | +124 | +156 | +6 | +98 | 1389 | +0.08 | -151 | +0 | +0.02 | 0.033 | 1.000 | LEAD (own-p only; WF fails) |
| KC1.5_15m | TR | 1m | 0 | close | stop 48 pts, tgt 1R, time 30 min | 392 | +247 | +224 | +241 | +112 | +94 | 3740 | +0.08 | -153 | -165 | +0.04 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| OR15 | ABS | 1m | 2 | nyam | stop 24 pts, no tgt, time 120 min | 386 | +80 | +547 | +1565 | +405 | +969 | 21292 | +0.29 | +764 | +0 | -0.06 | 0.049 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| PWK | BRK | 1m | 0 | nypm | stop 32 pts, tgt 3R, time 60 min | 370 | +353 | +276 | +23 | +601 | +639 | 11017 | +0.38 | +199 | -1300 | -0.17 | 0.049 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| KIJUN60 | BRK | 1m | 0 | nyam | stop 48 pts, no tgt, time 120 min | 952 | +1723 | +1097 | +1418 | +74 | +183 | 15457 | +1.60 | +517 | +0 | +0.17 | 0.049 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| IB60X15 | BRK | 1m | 0 | nypm | stop 48 pts, tgt 10 pts, time 120 min | 785 | +237 | +234 | +198 | +234 | -169 | 6747 | +0.05 | -68 | +390 | -0.01 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| IB30 | FB | 1m | 0 | nyam | stop 48 pts, tgt 40 pts, time 120 min | 1223 | +694 | +645 | +1367 | -101 | -7 | 7113 | +0.08 | -42 | -970 | -0.08 | 0.066 | 1.000 | LEAD (own-p only; WF fails) |
| GRID1 | BRK | 1m | 0 | close | stop = structure +5, tgt 2R, time 120 min | 263 | +460 | +217 | -544 | +423 | -35 | 14810 | +0.11 | +58 | +0 | -0.11 | 0.016 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| EMA200_60m | BRK | 1m | 0 | nyam | stop 16 pts, tgt 3R, time 30 min | 466 | +524 | +395 | +875 | +729 | -240 | 8603 | +0.09 | -118 | +0 | +0.02 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| GRID0.5 | BRK | 5m | 0 | nyam | stop 48 pts, tgt 20 pts, time 120 min | 945 | +410 | +323 | +452 | +162 | -382 | 6177 | +0.11 | +518 | +216 | -0.15 | 0.066 | 1.000 | CANDIDATE (own-p only; family p 1.00) |
| IB60X2 | BRK | 1m | 0 | nypm | stop = structure +5, tgt 40 pts, time 30 min | 316 | +185 | -105 | -394 | +467 | +138 | 10640 | +0.11 | -118 | +3181 | +0.08 | 0.033 | 1.000 | LEAD (own-p only; WF fails) |
| MVWAP | BRK | 5m | 0 | nyam | stop 48 pts, tgt 10 pts, time 120 min | 287 | +234 | +11 | -144 | +45 | +60 | 5393 | +0.01 | -194 | +585 | -0.05 | 0.098 | 1.000 | LEAD (own-p only; WF fails) |

## Trigger x session summary (all cells; share of cells with own p <= .05 vs 5% expected; median pooled t)
| trigger | session | cells | median t | share p_own<=.05 | gate pass |
|--|--|--|--|--|--|
| ABS | asia | 21504 | -0.75 | 0.064 | 0.044 |
| ABS | close | 29952 | -0.40 | 0.078 | 0.020 |
| ABS | london | 23040 | -0.89 | 0.047 | 0.072 |
| ABS | nyam | 31872 | -0.77 | 0.044 | 0.119 |
| ABS | nypm | 15936 | -0.30 | 0.073 | 0.014 |
| ABS | pre | 22464 | -0.32 | 0.079 | 0.029 |
| BR | asia | 22464 | -0.25 | 0.108 | 0.007 |
| BR | close | 32640 | -0.30 | 0.066 | 0.005 |
| BR | london | 22848 | -0.83 | 0.033 | 0.034 |
| BR | nyam | 32640 | -0.77 | 0.062 | 0.143 |
| BR | nypm | 33600 | -0.46 | 0.054 | 0.053 |
| BR | pre | 19968 | -0.47 | 0.030 | 0.002 |
| BRK | asia | 11520 | -0.49 | 0.301 | 0.134 |
| BRK | close | 16896 | -0.85 | 0.043 | 0.110 |
| BRK | london | 11520 | -1.25 | 0.076 | 0.071 |
| BRK | nyam | 16896 | -0.73 | 0.111 | 0.095 |
| BRK | nypm | 16896 | -0.78 | 0.088 | 0.110 |
| BRK | pre | 11520 | -0.61 | 0.042 | 0.100 |
| DT | asia | 22848 | -1.07 | 0.074 | 0.066 |
| DT | close | 27840 | -0.45 | 0.064 | 0.032 |
| DT | london | 22848 | -1.13 | 0.054 | 0.105 |
| DT | nyam | 30144 | -0.64 | 0.043 | 0.036 |
| DT | nypm | 32448 | -0.63 | 0.045 | 0.054 |
| DT | pre | 20928 | -0.48 | 0.045 | 0.015 |
| FB | asia | 23040 | -0.54 | 0.093 | 0.036 |
| FB | close | 33792 | -0.38 | 0.072 | 0.071 |
| FB | london | 23040 | -0.83 | 0.086 | 0.074 |
| FB | nyam | 33408 | -0.52 | 0.085 | 0.141 |
| FB | nypm | 33792 | -0.77 | 0.040 | 0.135 |
| FB | pre | 22656 | -0.53 | 0.056 | 0.044 |
| TR | asia | 23040 | -1.17 | 0.071 | 0.067 |
| TR | close | 33024 | -0.62 | 0.060 | 0.067 |
| TR | london | 23040 | -1.25 | 0.058 | 0.110 |
| TR | nyam | 32448 | -1.03 | 0.058 | 0.102 |
| TR | nypm | 33600 | -0.86 | 0.029 | 0.120 |
| TR | pre | 22464 | -0.70 | 0.052 | 0.038 |

## Labels: CANDIDATE needs tolerant gate + corr<=.3 + stack Calmar gain>0 + own placebo p<=.10 + family p<=.10 + walk-forward of the pick (monthly, trailing 26 weeks, 192 brackets of the set) positive and stack-Calmar-up. Held-out live week shown, not used for picking. Nothing here is a PASS claim.