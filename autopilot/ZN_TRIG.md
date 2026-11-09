# ZN_TRIG - zones as ENTRY TRIGGERS (T-ZONES-EXHAUST section 5), refreshed 2026-11-09 18:43 Z. Research only, Shadow only, no PASS claims, ROLL-EXCL stack (sz_core.Base rollw) for stack columns.
**Price source:** 1-s STATE arrays (_th_state/days, 2023-04-03 .. 2026-11-05; NOT bars1m_NQ.npz), 14 quarterly rolls back-adjusted at the roll second, round numbers on raw price. The 1-s state data runs to 2026-11-05 so no series ends 10-16; windows as of 2026-11-09; held-out live week = label days 2026-11-02..05 (never used to pick).
**Grid:** 68 level families (114 lines) x 6 triggers (touch-reject, break-through, failed-break fade, break-and-retest, delta turn at level, absorption) x bars 1m/5m x zone w x 6 sessions x 192 brackets = 1334592 scored cells in 68 families run so far; 60 null draws of random same-count entries within session (same side split, same brackets).

**Plain sentence:** 51890 of 1334592 cells pass the tolerant gate with |weekly corr to stack| <= .3 and a positive HOLD stack Calmar gain; 17040 of those have own placebo p <= .10; the smallest family (max-stat over all 1334592 cells) p of ANY cell is 0.951, so the best trigger books are indistinguishable from the best of random entries.

## Best gate-passing cell per level family (ranked by pooled weekly t); equal-$-risk lots R=$1200, fees $4.84 RT, 1 tick slippage each side; means are $/week at those lots, carry weeks dropped from means; maxDD on all weeks
| family | trigger | bar | w | session | bracket | events | L6M | HOLD | MID | PRE | X' | maxDD HOLD | dCalmar HOLD (stack+book) | WF OOS mean/wk | live wk $ | corr wk | p own | p fam | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| KC2.5_15m | BRK | 1m | 0 | asia | stop 48 pts, tgt 3R, time 120 min | 1628 | +2418 | +1617 | +1232 | +660 | +106 | 16403 | +0.85 | +1322 | +7002 | +0.15 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| RN25 | BR | 1m | 0 | nyam | stop 48 pts, tgt 1R, time 120 min | 3637 | +1324 | +1321 | +1328 | +1122 | -280 | 36443 | +1.14 | +486 | +2733 | -0.01 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| BB_60m | BRK | 1m | 0 | asia | stop 48 pts, tgt 3R, time 120 min | 616 | +1387 | +880 | +578 | +386 | +79 | 5963 | +0.38 | +405 | +1871 | +0.17 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| EMA200_5m | BR | 1m | 0 | nyam | stop 48 pts, tgt 1R, time 30 min | 392 | +174 | +513 | +867 | +192 | -83 | 6789 | +0.27 | +101 | +955 | -0.06 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| PD_RTH | BR | 1m | 0 | nyam | stop = structure +5, tgt 2R, time 30 min | 307 | +1173 | +921 | +1235 | +401 | +342 | 18667 | +0.17 | +98 | -1380 | -0.04 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| VWAP1 | BR | 1m | 0 | nypm | stop 32 pts, tgt 1.5R, time 60 min | 390 | +819 | +1185 | +1827 | +170 | +470 | 9255 | +0.80 | +247 | +0 | +0.01 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| RN100 | BRK | 1m | 0 | asia | stop 48 pts, tgt 40 pts, time 120 min | 3513 | +2703 | +1752 | +1645 | +129 | +31 | 13735 | +1.41 | +379 | -5028 | +0.04 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| OR5 | BR | 1m | 0 | nypm | stop 32 pts, no tgt, time 60 min | 296 | +308 | +800 | +152 | +613 | +854 | 21692 | +0.30 | +651 | +390 | -0.07 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| S_PRE | BR | 1m | 0 | nyam | stop 48 pts, tgt 2R, time 120 min | 796 | +862 | +772 | +666 | +723 | -54 | 8698 | +0.67 | +142 | +2860 | +0.11 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| RN50 | ABS | 5m | 3 | nyam | stop 48 pts, tgt 2R, time 120 min | 2678 | +1812 | +1409 | -648 | +873 | +938 | 14897 | +0.55 | -260 | +2836 | +0.14 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| T_P1000 | BR | 1m | 0 | nyam | stop 32 pts, no tgt, time 60 min | 391 | +2029 | +2296 | +3968 | +303 | +141 | 12236 | +0.82 | +516 | +4740 | +0.24 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| SW15m3 | BRK | 5m | 0 | asia | stop 48 pts, tgt 2R, time 120 min | 1859 | +3011 | +1434 | +664 | +329 | +109 | 13116 | +0.54 | +622 | +1237 | +0.14 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| RVWAP0 | BRK | 5m | 0 | close | stop 8 pts, tgt 1R, time 30 min | 318 | +683 | +665 | +582 | +114 | +36 | 15764 | +0.43 | -1 | +0 | +0.02 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| SW5m2 | DT | 5m | 3 | nypm | stop = structure +2, tgt 3R, time 120 min | 325 | +856 | +428 | +787 | +545 | -337 | 14810 | +0.11 | +78 | +0 | +0.08 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| BB_15m | BRK | 5m | 0 | asia | stop 48 pts, tgt 3R, time 120 min | 1495 | +2684 | +1347 | +511 | +543 | +7 | 16519 | +0.58 | +296 | +7091 | +0.22 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| T_P0930 | ABS | 5m | 0 | nyam | stop 48 pts, tgt 1R, time 120 min | 397 | +246 | +252 | +307 | +272 | +220 | 5548 | +0.13 | +339 | +955 | +0.04 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| KC1.5_60m | BR | 5m | 0 | nyam | stop = structure +5, tgt 40 pts, time 120 min | 290 | +390 | +398 | +261 | +297 | +130 | 8167 | +0.21 | +210 | +0 | +0.08 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| KC1.5_5m | DT | 1m | 2 | asia | stop 48 pts, tgt 1.5R, time 120 min | 10224 | +3841 | +1772 | +1724 | +236 | +413 | 30685 | +1.62 | +49 | +9737 | +0.26 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| KC2.5_5m | FB | 1m | 2 | pre | stop 48 pts, tgt 10 pts, time 30 min | 308 | +179 | +99 | +244 | +121 | -70 | 2939 | +0.05 | +111 | +0 | +0.03 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| EMA20_60m | DT | 1m | 2 | london | stop 48 pts, tgt 40 pts, time 60 min | 1392 | +486 | +578 | +207 | +148 | +254 | 5074 | +0.42 | +308 | +1486 | -0.16 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| VWAP0 | BRK | 1m | 0 | pre | stop 48 pts, tgt 20 pts, time 60 min | 398 | +398 | +198 | +42 | +163 | +335 | 1508 | +0.14 | +575 | -180 | -0.08 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| VWAP2 | BR | 5m | 3 | nyam | stop 24 pts, tgt 1R, time 120 min | 293 | +553 | +188 | +300 | +303 | +279 | 5996 | +0.18 | +68 | -1959 | +0.01 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| SW15m2 | BR | 1m | 0 | london | stop 24 pts, tgt 10 pts, time 120 min | 502 | +607 | +286 | -21 | +164 | +181 | 4363 | +0.31 | -42 | +3513 | +0.04 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| GRID0.25 | TR | 5m | 3 | close | stop 32 pts, tgt 10 pts, time 120 min | 166 | +78 | +9 | +130 | +156 | +70 | 3138 | +0.00 | +84 | +0 | -0.07 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| KC2.5_60m | ABS | 5m | 3 | nyam | stop 48 pts, tgt 40 pts, time 120 min | 381 | +184 | +270 | +192 | +31 | +302 | 3259 | +0.36 | +62 | -175 | +0.02 | 0.033 | 1.000 | LEAD (own-p only; WF fails) |
| PD_FULL | BRK | 1m | 0 | nyam | stop 48 pts, tgt 40 pts, time 120 min | 1381 | +898 | +664 | +723 | +423 | -290 | 8205 | +0.28 | +159 | +795 | +0.06 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| EMA20_5m | TR | 5m | 3 | london | stop 48 pts, tgt 3R, time 120 min | 2624 | +1146 | +1256 | +2315 | +361 | +129 | 6392 | +0.55 | +242 | +1941 | +0.00 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| EMA50_60m | DT | 1m | 2 | london | stop 48 pts, tgt 3R, time 120 min | 694 | +966 | +407 | +50 | +197 | +324 | 6603 | +0.21 | -171 | +1905 | -0.09 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| SW1m3 | BR | 5m | 3 | nyam | stop = structure +5, no tgt, time 60 min | 1216 | +93 | +836 | +1369 | +1012 | -253 | 53918 | +0.38 | -21 | -3739 | +0.06 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| EMA50_15m | BRK | 1m | 0 | pre | stop = structure +5, no tgt, time 60 min | 435 | +653 | +2719 | +5718 | +1235 | +979 | 14258 | +3.04 | +1018 | -1079 | -0.03 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| IB30X15 | TR | 1m | 2 | nypm | stop 48 pts, no tgt, time 30 min | 631 | +44 | +44 | +626 | +384 | -22 | 10173 | +0.01 | +34 | +1675 | +0.04 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| S_ASIA | FB | 1m | 2 | nyam | stop 48 pts, tgt 3R, time 30 min | 1207 | +1778 | +999 | +703 | +606 | -132 | 14092 | +0.89 | -449 | +1786 | +0.01 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| SW5m3 | ABS | 5m | 3 | pre | stop 24 pts, no tgt, time 60 min | 547 | +1133 | +519 | -207 | +682 | +259 | 12281 | +1.56 | +997 | -980 | -0.07 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| PD_C | BRK | 5m | 0 | london | stop 48 pts, tgt 40 pts, time 120 min | 595 | +24 | +236 | +659 | +164 | +65 | 4536 | +0.24 | -104 | -349 | -0.09 | 0.033 | 1.000 | LEAD (own-p only; WF fails) |
| IB30X2 | TR | 1m | 2 | close | stop 8 pts, tgt 2R, time 60 min | 191 | +169 | +281 | +155 | +233 | +400 | 9386 | +0.24 | +18 | +0 | +0.08 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| RVWAP1 | DT | 5m | 3 | nypm | stop 32 pts, tgt 1.5R, time 60 min | 242 | +552 | +673 | +992 | -61 | +164 | 5828 | +0.23 | +249 | +0 | -0.03 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| EMA50_5m | FB | 1m | 0 | london | stop 48 pts, tgt 1.5R, time 120 min | 1398 | +896 | +793 | +1475 | +512 | -201 | 23091 | +0.33 | +849 | +5056 | +0.20 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| YVWAP | ABS | 1m | 2 | asia | stop 48 pts, tgt 2R, time 60 min | 375 | +945 | +483 | +639 | -34 | +68 | 3089 | +0.22 | -41 | +0 | +0.00 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| EMA20_15m | TR | 5m | 3 | nyam | stop = structure +5, tgt 10 pts, time 60 min | 330 | +262 | +141 | +106 | +112 | +319 | 3668 | +0.07 | +77 | +0 | +0.02 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| BB_5m | TR | 5m | 3 | nypm | stop 48 pts, tgt 3R, time 120 min | 929 | +1130 | +730 | +1082 | +264 | +134 | 9277 | +0.34 | +52 | +1905 | -0.00 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| SW1m2 | DT | 1m | 2 | nyam | stop 48 pts, no tgt, time 120 min | 2491 | +3028 | +2125 | +2420 | +242 | -596 | 9420 | +0.92 | -520 | +6455 | +0.21 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| S_LONDON | BR | 1m | 2 | nypm | stop 48 pts, tgt 10 pts, time 120 min | 337 | +67 | +111 | +261 | +64 | +154 | 4654 | +0.09 | -251 | +195 | +0.07 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| EMA200_15m | ABS | 1m | 2 | london | stop 16 pts, tgt 2R, time 120 min | 314 | +374 | +314 | +442 | +360 | +814 | 8014 | +0.16 | +179 | -1319 | -0.02 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| SW60m2 | BRK | 5m | 0 | asia | stop 24 pts, tgt 3R, time 60 min | 844 | +2031 | +929 | -692 | +415 | -98 | 35843 | +0.78 | +408 | +5972 | -0.00 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| WVWAP | BRK | 1m | 0 | asia | stop 24 pts, tgt 20 pts, time 30 min | 579 | +686 | +700 | +948 | +73 | -19 | 13149 | +0.35 | +94 | -1169 | -0.05 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| IB60 | FB | 1m | 0 | nypm | stop 48 pts, tgt 40 pts, time 60 min | 753 | +439 | +430 | +800 | +160 | +116 | 6074 | +0.23 | +47 | -175 | +0.14 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| VWAP3 | BRK | 5m | 0 | london | stop 12 pts, tgt 1R, time 120 min | 269 | +529 | +14 | -361 | +155 | -10 | 18295 | +0.00 | -207 | +0 | +0.00 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| ON | BRK | 5m | 0 | close | stop 48 pts, tgt 10 pts, time 30 min | 311 | +171 | +124 | +156 | +6 | +98 | 1389 | +0.08 | -151 | +0 | +0.02 | 0.033 | 1.000 | LEAD (own-p only; WF fails) |
| KC1.5_15m | TR | 1m | 0 | close | stop 48 pts, tgt 1R, time 30 min | 392 | +247 | +224 | +241 | +112 | +94 | 3740 | +0.08 | -153 | -165 | +0.04 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| T_P1130 | BR | 5m | 3 | nypm | stop = structure +2, tgt 1.5R, time 60 min | 260 | +1077 | +650 | +1007 | +137 | -18 | 5490 | +0.34 | -49 | +3456 | -0.00 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| S_NYPM | FB | 1m | 0 | close | stop 32 pts, no tgt, time 120 min | 441 | +1196 | +760 | +680 | +324 | +37 | 18149 | +1.37 | -174 | -2599 | +0.06 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| OR15 | ABS | 1m | 2 | nyam | stop 24 pts, no tgt, time 120 min | 386 | +80 | +547 | +1565 | +405 | +969 | 21292 | +0.29 | +764 | +0 | -0.06 | 0.049 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| PWK | BRK | 1m | 0 | nypm | stop 32 pts, tgt 3R, time 60 min | 370 | +353 | +276 | +23 | +601 | +639 | 11017 | +0.38 | +199 | -1300 | -0.17 | 0.049 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| KIJUN60 | BRK | 1m | 0 | nyam | stop 48 pts, no tgt, time 120 min | 952 | +1723 | +1097 | +1418 | +74 | +183 | 15457 | +1.60 | +517 | +0 | +0.17 | 0.049 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| RVWAP2 | FB | 1m | 0 | close | stop 48 pts, tgt 1R, time 60 min | 214 | +255 | +93 | +84 | +249 | -8 | 3879 | +0.05 | +138 | +1910 | +0.05 | 0.033 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| IB60X15 | BRK | 1m | 0 | nypm | stop 48 pts, tgt 10 pts, time 120 min | 785 | +237 | +234 | +198 | +234 | -169 | 6747 | +0.05 | -68 | +390 | -0.01 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| IB30 | FB | 1m | 0 | nyam | stop 48 pts, tgt 40 pts, time 120 min | 1223 | +694 | +645 | +1367 | -101 | -7 | 7113 | +0.08 | -42 | -970 | -0.08 | 0.066 | 1.000 | LEAD (own-p only; WF fails) |
| T_P1500 | FB | 5m | 0 | close | stop 32 pts, tgt 20 pts, time 30 min | 352 | +695 | +345 | +146 | +22 | +257 | 7664 | +0.18 | -183 | +0 | -0.00 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| S_NYAM | TR | 1m | 0 | nypm | stop 48 pts, no tgt, time 120 min | 597 | +250 | +125 | -43 | +269 | +426 | 12830 | +0.10 | -28 | +0 | -0.04 | 0.066 | 1.000 | LEAD (own-p only; WF fails) |
| GRID1 | BRK | 1m | 0 | close | stop = structure +5, tgt 2R, time 120 min | 263 | +460 | +217 | -544 | +423 | -35 | 14810 | +0.11 | +58 | +0 | -0.11 | 0.016 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| EMA200_60m | BRK | 1m | 0 | nyam | stop 16 pts, tgt 3R, time 30 min | 466 | +524 | +395 | +875 | +729 | -240 | 8603 | +0.09 | -118 | +0 | +0.02 | 0.016 | 1.000 | LEAD (own-p only; WF fails) |
| GRID0.5 | BRK | 5m | 0 | nyam | stop 48 pts, tgt 20 pts, time 120 min | 945 | +410 | +323 | +452 | +162 | -382 | 6177 | +0.11 | +518 | +216 | -0.15 | 0.066 | 1.000 | best-of-F, NOT a candidate (own p ok, WF ok, family p 1.00) |
| IB60X2 | BRK | 1m | 0 | nypm | stop = structure +5, tgt 40 pts, time 30 min | 316 | +185 | -105 | -394 | +467 | +138 | 10640 | +0.11 | -118 | +3181 | +0.08 | 0.033 | 1.000 | LEAD (own-p only; WF fails) |
| MVWAP | BRK | 5m | 0 | nyam | stop 48 pts, tgt 10 pts, time 120 min | 287 | +234 | +11 | -144 | +45 | +60 | 5393 | +0.01 | -194 | +585 | -0.05 | 0.098 | 1.000 | LEAD (own-p only; WF fails) |

## Trigger x session summary (all cells; share of cells with own p <= .05 vs 5% expected; median pooled t)
| trigger | session | cells | median t | share p_own<=.05 | gate pass |
|--|--|--|--|--|--|
| ABS | asia | 31488 | -0.84 | 0.065 | 0.068 |
| ABS | close | 47232 | -0.43 | 0.062 | 0.026 |
| ABS | london | 33792 | -1.10 | 0.037 | 0.085 |
| ABS | nyam | 47232 | -0.86 | 0.043 | 0.122 |
| ABS | nypm | 25152 | -0.41 | 0.059 | 0.018 |
| ABS | pre | 33984 | -0.36 | 0.076 | 0.053 |
| BR | asia | 32448 | -0.35 | 0.099 | 0.018 |
| BR | close | 50688 | -0.37 | 0.056 | 0.014 |
| BR | london | 33600 | -0.87 | 0.035 | 0.035 |
| BR | nyam | 48768 | -0.76 | 0.059 | 0.141 |
| BR | nypm | 50304 | -0.47 | 0.061 | 0.070 |
| BR | pre | 30720 | -0.58 | 0.032 | 0.006 |
| BRK | asia | 16512 | -0.54 | 0.334 | 0.141 |
| BRK | close | 26112 | -0.81 | 0.048 | 0.122 |
| BRK | london | 16896 | -1.49 | 0.066 | 0.070 |
| BRK | nyam | 24960 | -0.80 | 0.109 | 0.089 |
| BRK | nypm | 25344 | -0.83 | 0.079 | 0.112 |
| BRK | pre | 17280 | -0.70 | 0.047 | 0.092 |
| DT | asia | 32832 | -1.37 | 0.060 | 0.064 |
| DT | close | 44544 | -0.59 | 0.044 | 0.029 |
| DT | london | 33600 | -1.30 | 0.056 | 0.095 |
| DT | nyam | 45696 | -0.61 | 0.043 | 0.051 |
| DT | nypm | 49152 | -0.65 | 0.049 | 0.047 |
| DT | pre | 32064 | -0.52 | 0.045 | 0.025 |
| FB | asia | 33024 | -0.64 | 0.094 | 0.051 |
| FB | close | 52224 | -0.39 | 0.080 | 0.075 |
| FB | london | 33792 | -0.92 | 0.082 | 0.078 |
| FB | nyam | 49536 | -0.60 | 0.081 | 0.137 |
| FB | nypm | 50688 | -0.85 | 0.034 | 0.143 |
| FB | pre | 34176 | -0.60 | 0.044 | 0.055 |
| TR | asia | 33024 | -1.51 | 0.056 | 0.067 |
| TR | close | 51072 | -0.64 | 0.051 | 0.056 |
| TR | london | 33792 | -1.46 | 0.048 | 0.110 |
| TR | nyam | 48576 | -1.07 | 0.045 | 0.098 |
| TR | nypm | 50496 | -0.90 | 0.029 | 0.120 |
| TR | pre | 33792 | -0.77 | 0.048 | 0.043 |

## Labels: CANDIDATE needs tolerant gate + corr<=.3 + stack Calmar gain>0 + own placebo p<=.10 + family p<=.10 + walk-forward of the pick (monthly, trailing 26 weeks, 192 brackets of the set) positive and stack-Calmar-up. Held-out live week shown, not used for picking. Nothing here is a PASS claim.