# DS3_ZEN_LINES_D - joint top 10 x 10, L5 non-average lines, L6 robustness (D3ZLN, 2026-10-28)

**Verdict line:** best regime line / best entry line / EMA200 rank among N / effect vs random with MDE: best regime line B|rs240|WMA_100_hl2|dist40, best entry line (R1) 3-min T3_233_close tol 2 (effects inside MDE, dead in HOLD; see B and C); **the best line pair is D|rs60:LSMA_377_close:dist40|time_3m:VIDYA_377_close:tol2 with effect +6.00 pt/trade [-2.85, 13.92] (MDE80 11.59) on only n = 25 PRE trades (all 100 joint cells have n < 100: counts, not verdicts); the 5-min EMA200 / 1-min EMA200 pair is -0.22 [-0.94, 0.58] (MDE80 1.08, n 1101, below the median of every table)**; joint HOLD: 6 of 100 cells have HOLD CI lower > 0, 3 of 100 also pass X; best L5 line L5|VWAP_week_up2|tol2 PRE +2.38 [0.48, 4.19] MDE80 2.58, HOLD -0.17 [-2.70, 2.27]; reality check over N = 254: p 0.14; **nothing beats a random entry in the same regime; the EMA200/EMA200 pair is one ordinary member of the family, not a distinguished one.**

## 1. Counts block
Joint: 10 regime lines (B top 10 distinct, all 'distance <= 40' semantics on 10m-240m lines) x 10 entry lines (C top 10 R1: nine 2/3-min lines and one 1000-tick line). PRE trades per joint cell: median 34, range 15-92 (a regime that is within 40 pt of a 60-240 min line AND a hold candle at a 233-377 lookback line leaves ~35 trades in 75 weeks). L5: 70 registry clusters x 2 tolerances = 140 (128 with n >= 100) + 14 extras (swing ladder, 5m FVG midpoint, Fibonacci 50 / 61.8, OR15 / OR30 edges; all 14 have n >= 100).

## 2. Grid enumeration and screened N
100 + 140 + 14 = **254 scored, 0 skipped** (plan 240 + 14 disclosed extras). Prereg `ZEN_LINES_D_prereg.md` sha256 05a9aa14b8955f3ef64b6778d208f85b8d5aaee24a6879bf89c75910014a9cb4 (before scoring). Reality check over the 142 eligible cells (all L5/L5X; the joint cells are below n = 100): best t 2.97, p = 0.143. M4 session variants NOT run (disclosed). Joint cells: effect>0 in 69, net1>0 in 29, CI lower>0 in 4 of 100 (expected ~2.5 by chance at n < 100 with wide CIs); mean PRE effect over the 100 = +1.12 and HOLD +0.22 (selection of regime and entry lines on PRE: winner's curse).

## 3. Top-10 tables
### 3a. Joint set (regardless of n; all n < 100)
| # | cell | n | tr/wk | win | BE | net1 pts ($/tr 10 lots) | net2 | random-in-regime | effect [CI] | MDE80 | eff vs rand-dir | fw80 | PRE rank-vs-draws | HOLD effect [CI] (n) | X effect | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | D|rs60:LSMA_377_close:dist40|time_3m:VIDYA_377_close:tol2 | 25 | 0.33 | 0.600 | 0.489 | 3.44 ($688) | 1.67 | -2.56 | 6.00 [-2.85, 13.92] | 11.59 | 4.44 | 279 | - | 3.04 [-5.11, 8.49] (19) | 2.21 | G1(CI lo -2.85); G2(rd 4.44, CI lo -9.09); G5(n 25 <100: count, not verdict); G6(hold); G8(hold); G9(hold); G10 not run |
| 2 | D|time_15m:VIDYA_377_close:dist40|time_3m:VIDYA_377_hl2:tol2 | 24 | 0.32 | 0.583 | 0.466 | 3.49 ($698) | 1.30 | -2.13 | 5.62 [2.30, 8.81] | 4.37 | -3.89 | 45 | - | 7.79 [-11.43, 18.28] (7) | 4.43 | G2(rd -3.89, CI lo -9.86); G5(n 24 <100: count, not verdict); G6(hold); G8(hold); G9(hold); G10 not run |
| 3 | D|rs60:SMMA_89_hl2:dist40|time_2m:T3_377_close:tol2 | 32 | 0.43 | 0.656 | 0.526 | 3.78 ($757) | 1.79 | -1.49 | 5.28 [-1.32, 10.95] | 8.98 | 5.00 | 217 | - | -0.78 [-9.32, 10.73] (5) | -0.23 | G1(CI lo -1.32); G2(rd 5.00, CI lo -0.29); G5(n 32 <100: count, not verdict); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 4 | D|time_15m:VIDYA_377_close:dist40|tick_1000:VIDYA_233_close:tol2 | 38 | 0.51 | 0.605 | 0.505 | 3.04 ($609) | 0.81 | -2.13 | 5.17 [-1.77, 11.88] | 9.49 | 2.61 | 253 | - | 1.80 [-1.15, 10.39] (24) | -2.55 | G1(CI lo -1.77); G2(rd 2.61, CI lo -4.37); G5(n 38 <100: count, not verdict); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 5 | D|rs60:VIDYA_100_hl2:dist40|time_3m:VIDYA_377_close:tol2 | 30 | 0.40 | 0.567 | 0.481 | 2.72 ($544) | 0.66 | -2.13 | 4.85 [-2.31, 17.48] | 13.29 | 0.44 | 563 | - | 7.54 [-11.38, 18.72] (5) | 0.61 | G1(CI lo -2.31); G2(rd 0.44, CI lo -4.66); G5(n 30 <100: count, not verdict); G6(hold); G8(hold); G9(hold); G10 not run |
| 6 | D|rs240:WMA_100_hl2:dist40|time_3m:VIDYA_377_hl2:tol2 | 31 | 0.41 | 0.677 | 0.547 | 3.30 ($661) | 1.01 | -1.39 | 4.70 [1.91, 8.71] | 4.76 | 0.38 | 77 | - | -12.36 [-13.77, 3.89] (1) | 1.09 | G2(rd 0.38, CI lo -4.65); G5(n 31 <100: count, not verdict); G6(hold); G8(hold); G9(hold); G10 not run |
| 7 | D|time_15m:VIDYA_377_close:dist40|time_3m:VIDYA_377_close:tol2 | 27 | 0.36 | 0.519 | 0.449 | 2.34 ($469) | 0.41 | -2.13 | 4.47 [-2.18, 9.84] | 8.36 | 2.02 | 262 | - | 3.89 [-10.41, 10.66] (8) | 4.21 | G1(CI lo -2.18); G2(rd 2.02, CI lo -1.24); G5(n 27 <100: count, not verdict); G6(hold); G8(hold); G9(hold); G10 not run |
| 8 | D|rs60:ZLEMA_377_hl2:dist40|time_3m:SMMA_377_close:tol2 | 32 | 0.43 | 0.656 | 0.544 | 3.14 ($628) | 0.94 | -1.22 | 4.36 [-0.77, 11.63] | 8.93 | 6.12 | 315 | - | -6.19 [-8.87, -4.00] (20) | 0.18 | G1(CI lo -0.77); G5(n 32 <100: count, not verdict); G6(hold); G8(hold); G9(hold); G10 not run |
| 9 | D|rs60:ZLEMA_377_hl2:dist40|time_3m:TMA_34_close:tol2 | 40 | 0.53 | 0.750 | 0.636 | 2.74 ($549) | 0.25 | -1.22 | 3.97 [0.65, 7.35] | 4.64 | 4.99 | 103 | - | -0.14 [-4.17, 4.63] (23) | -0.20 | G2(rd 4.99, CI lo -0.91); G5(n 40 <100: count, not verdict); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 10 | D|rs60:ZLEMA_377_hl2:dist40|time_3m:LSMA_233_close:tol2 | 35 | 0.47 | 0.714 | 0.611 | 2.59 ($517) | 0.21 | -1.22 | 3.81 [0.47, 7.59] | 4.95 | 2.71 | 127 | - | -0.08 [-6.71, 4.51] (21) | -1.75 | G2(rd 2.71, CI lo -5.79); G5(n 35 <100: count, not verdict); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |

### 3b. L5 non-average lines + extras (n >= 100)
| # | cell | n | tr/wk | win | BE | net1 pts ($/tr 10 lots) | net2 | random-in-regime | effect [CI] | MDE80 | eff vs rand-dir | fw80 | PRE rank-vs-draws | HOLD effect [CI] (n) | X effect | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L5|VWAP_week_up2|tol2 | 186 | 2.48 | 0.656 | 0.632 | 0.57 ($114) | -1.59 | -1.81 | 2.38 [0.48, 4.19] | 2.58 | 2.56 | 88 | - | -0.17 [-2.70, 2.27] (58) | -0.07 | G2(rd 2.56, CI lo -0.05); G3(net1 0.57 net2 -1.59); G5(effect 2.38 < MDE80 2.58: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 2 | L5|VWAP_week_up2|tol5 | 238 | 3.17 | 0.664 | 0.645 | 0.46 ($91) | -1.72 | -1.81 | 2.27 [0.64, 3.60] | 2.13 | 2.53 | 67 | - | -0.60 [-2.74, 1.39] (80) | -0.76 | G3(net1 0.46 net2 -1.72); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 3 | L5|FIX_S2|tol2 | 115 | 1.53 | 0.557 | 0.560 | -0.10 ($-20) | -2.58 | -1.81 | 1.71 [-1.18, 4.55] | 4.09 | -0.48 | 429 | - | -2.89 [-5.35, -0.27] (70) | -0.70 | G1(CI lo -1.18); G2(rd -0.48, CI lo -2.87); G3(net1 -0.10 net2 -2.58); G4(win-BE -0.4 pp); G5(effect 1.71 < MDE80 4.09: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 4 | L5|VWAP_eth_dn2|tol5 | 248 | 3.31 | 0.565 | 0.568 | -0.10 ($-20) | -2.15 | -1.81 | 1.71 [0.01, 3.45] | 2.44 | 1.36 | 153 | - | 0.00 [-2.78, 2.76] (79) | -1.68 | G2(rd 1.36, CI lo -0.59); G3(net1 -0.10 net2 -2.15); G4(win-BE -0.4 pp); G5(effect 1.71 < MDE80 2.44: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 5 | L5|VWAP_eth_dn2|tol2 | 195 | 2.60 | 0.538 | 0.548 | -0.26 ($-53) | -2.32 | -1.81 | 1.55 [-0.19, 3.36] | 2.53 | 1.00 | 201 | - | 0.63 [-2.21, 3.51] (67) | -1.32 | G1(CI lo -0.19); G2(rd 1.00, CI lo -1.00); G3(net1 -0.26 net2 -2.32); G4(win-BE -1.0 pp); G5(effect 1.55 < MDE80 2.53: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 6 | L5|FIX_S2|tol5 | 142 | 1.89 | 0.528 | 0.550 | -0.59 ($-118) | -2.97 | -1.81 | 1.22 [-1.62, 4.33] | 4.24 | -0.31 | 906 | - | -2.29 [-4.40, -0.03] (95) | -1.74 | G1(CI lo -1.62); G2(rd -0.31, CI lo -2.50); G3(net1 -0.59 net2 -2.97); G4(win-BE -2.1 pp); G5(effect 1.22 < MDE80 4.24: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 7 | L5|VWAP_overnight|tol5 | 844 | 11.25 | 0.573 | 0.604 | -0.77 ($-154) | -2.89 | -1.81 | 1.04 [0.00, 2.03] | 1.43 | 0.43 | 142 | - | -0.10 [-1.93, 1.58] (260) | -0.94 | G2(rd 0.43, CI lo -0.86); G3(net1 -0.77 net2 -2.89); G4(win-BE -3.1 pp); G5(effect 1.04 < MDE80 1.43: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 8 | L5|VWAP_overnight|tol2 | 588 | 7.84 | 0.558 | 0.594 | -0.91 ($-181) | -2.97 | -1.81 | 0.90 [-0.27, 1.98] | 1.59 | 0.61 | 232 | - | -0.17 [-2.26, 1.87] (186) | -0.95 | G1(CI lo -0.27); G2(rd 0.61, CI lo -0.85); G3(net1 -0.91 net2 -2.97); G4(win-BE -3.6 pp); G5(effect 0.90 < MDE80 1.59: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 9 | L5|ST_10_3|tol2 | 852 | 11.36 | 0.558 | 0.599 | -1.04 ($-208) | -3.13 | -1.81 | 0.77 [-0.10, 1.63] | 1.26 | 0.40 | 199 | - | -1.43 [-2.86, -0.06] (353) | -0.36 | G1(CI lo -0.10); G2(rd 0.40, CI lo -0.73); G3(net1 -1.04 net2 -3.13); G4(win-BE -4.2 pp); G5(effect 0.77 < MDE80 1.26: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 10 | L5|FIX_VAH|tol2 | 352 | 4.69 | 0.560 | 0.602 | -1.06 ($-211) | -3.13 | -1.81 | 0.75 [-0.82, 2.37] | 2.27 | 0.46 | 680 | - | 1.99 [0.17, 4.00] (145) | -0.77 | G1(CI lo -0.82); G2(rd 0.46, CI lo -1.36); G3(net1 -1.06 net2 -3.13); G4(win-BE -4.2 pp); G5(effect 0.75 < MDE80 2.27: inside MDE); G7(hold); G8(hold); G9(hold); G10 not run |

Reference (5-min EMA200 regime x 1-min EMA200 entry, tol 2): effect -0.22 [-0.94, 0.58], MDE80 1.08, n 1101.

L5 observations: VWAP_week +2 sigma is the only cell family with a CI above 0 in PRE (tol 2 +2.38 [0.48, 4.19], tol 5 +2.27 [0.64, 3.60]); HOLD tol 2 -0.17, tol 5 -0.60: it does not persist. The 14 extras: swing ladder, FVG midpoint, Fibonacci and OR edges all sit at effect 0.0 +- 0.1 (n 750-5,000, MDE80 0.5-1.4): dead.

## 4. Holdout (all 100 joint + top 30 L5/L5X, ONE look)
Pre-holdout text DS3_ZEN_LINES_D_PREHOLD.md. Joint: G6 6 / G7 52 / G8 0 / G9 0 of 100; median HOLD trades per joint cell 15 (inconclusive). L5 top 30: G6 3, G7 9, G8 0, G9 0. **0 CANDIDATE, 0 LEAD.**

First 10 joint and all L5 rows:

| cell | PRE (re-run) effect [CI] | HOLD n | HOLD net1 | HOLD effect [CI] | rank | X (2023-04..2024-01) effect | 2024 net$ / 2025 / 2026 (10 lots, $) | G6 G7 G8 G9 |
|---|---|---|---|---|---|---|---|---|
| D|rs60:LSMA_377_close:dist40|time_3m:VIDYA_377_close:tol2 | 6.29 [-2.22, 14.65] | 19 | 1.23 | 3.04 [-5.11, 8.49] | 0.79 | 2.21 | 3604 / 18361 / -3110 | n Y n n |
| D|time_15m:VIDYA_377_close:dist40|time_3m:VIDYA_377_hl2:tol2 | 6.22 [3.01, 8.92] | 7 | 3.78 | 7.79 [-11.43, 18.28] | 0.95 | 4.43 | 13666 / 8379 / 0 | n Y n n |
| D|rs60:SMMA_89_hl2:dist40|time_2m:T3_377_close:tol2 | 5.38 [-0.73, 11.36] | 5 | -2.77 | -0.78 [-9.32, 10.73] | 0.42 | -0.23 | 25081 / -3637 / 0 | n n n n |
| D|time_15m:VIDYA_377_close:dist40|tick_1000:VIDYA_233_close:tol2 | 5.42 [-1.41, 11.78] | 24 | -2.40 | 1.80 [-1.15, 10.39] | 0.72 | -2.55 | 31796 / -20806 / 625 | n n n n |
| D|rs60:VIDYA_100_hl2:dist40|time_3m:VIDYA_377_close:tol2 | 4.88 [-3.00, 15.84] | 5 | 4.08 | 7.54 [-11.38, 18.72] | 0.95 | 0.61 | 28555 / -5113 / -3048 | n Y n n |
| D|rs240:WMA_100_hl2:dist40|time_3m:VIDYA_377_hl2:tol2 | 4.40 [1.54, 8.26] | 1 | -15.24 | -12.36 [-13.77, 3.89] | 0.00 | 1.09 | 19490 / -2053 / 0 | n Y n n |
| D|time_15m:VIDYA_377_close:dist40|time_3m:VIDYA_377_close:tol2 | 5.06 [-1.89, 10.13] | 8 | -0.10 | 3.89 [-10.41, 10.66] | 0.84 | 4.21 | 15319 / 235 / -3048 | n Y n n |
| D|rs60:ZLEMA_377_hl2:dist40|time_3m:SMMA_377_close:tol2 | 4.81 [-0.59, 12.23] | 20 | -9.18 | -6.19 [-8.87, -4.00] | 0.03 | 0.18 | 9698 / -26327 / 0 | n Y n n |
| D|rs60:ZLEMA_377_hl2:dist40|time_3m:TMA_34_close:tol2 | 3.98 [0.74, 7.42] | 23 | -3.21 | -0.14 [-4.17, 4.63] | 0.47 | -0.20 | 26262 / -16021 / -3048 | n n n n |
| D|rs60:ZLEMA_377_hl2:dist40|time_3m:LSMA_233_close:tol2 | 3.97 [0.61, 8.10] | 21 | -3.04 | -0.08 [-6.71, 4.51] | 0.51 | -1.75 | 11779 / -6455 / 0 | n n n n |
| L5|VWAP_week_up2|tol2 | 2.41 [0.57, 4.20] | 58 | -2.86 | -0.17 [-2.70, 2.27] | 0.39 | -0.07 | 43218 / -53014 / -9609 | n n n n |
| L5|VWAP_week_up2|tol5 | 2.26 [0.59, 3.61] | 80 | -3.37 | -0.60 [-2.74, 1.39] | 0.20 | -0.76 | 32161 / -58611 / -13321 | n n n n |
| L5|FIX_S2|tol2 | 1.80 [-0.93, 4.68] | 70 | -5.70 | -2.89 [-5.35, -0.27] | 0.01 | -0.70 | 24068 / -81907 / -30499 | n n n n |
| L5|VWAP_eth_dn2|tol5 | 1.81 [0.09, 3.54] | 79 | -2.86 | 0.00 [-2.78, 2.76] | 0.50 | -1.68 | 5714 / -44781 / -14441 | n n n n |
| L5|VWAP_eth_dn2|tol2 | 1.60 [-0.13, 3.46] | 67 | -2.24 | 0.63 [-2.21, 3.51] | 0.73 | -1.32 | -3673 / -31246 / -8344 | n n n n |
| L5|FIX_S2|tol5 | 1.30 [-1.44, 4.32] | 95 | -5.14 | -2.29 [-4.40, -0.03] | 0.03 | -1.74 | 20802 / -106308 / -39645 | n n n n |
| L5|VWAP_overnight|tol5 | 1.08 [0.04, 2.05] | 260 | -2.90 | -0.10 [-1.93, 1.58] | 0.43 | -0.94 | -63377 / -194757 / -29834 | n n n n |
| L5|VWAP_overnight|tol2 | 0.95 [-0.21, 2.03] | 186 | -3.01 | -0.17 [-2.26, 1.87] | 0.36 | -0.95 | -27193 / -158552 / -27173 | n n n n |
| L5|ST_10_3|tol2 | 0.81 [-0.06, 1.65] | 353 | -4.23 | -1.43 [-2.86, -0.06] | 0.00 | -0.36 | -51318 / -370722 / -84971 | n n n n |
| L5|FIX_VAH|tol2 | 0.77 [-0.77, 2.39] | 145 | -0.82 | 1.99 [0.17, 4.00] | 0.99 | -0.77 | -13358 / -98635 / 2167 | Y n n n |
| L5|FIX_VAH|tol5 | 0.66 [-0.53, 1.85] | 198 | -1.43 | 1.34 [0.07, 2.78] | 0.99 | -0.30 | -19936 / -168952 / -4231 | Y n n n |
| L5|ST_10_3|tol5 | 0.64 [0.04, 1.23] | 545 | -4.01 | -1.15 [-2.03, -0.31] | 0.00 | -0.67 | -123466 / -582731 / -82002 | n n n n |
| L5|VWAP_rth_up2|tol2 | 0.55 [-1.26, 2.26] | 78 | -4.87 | -2.06 [-5.12, 1.01] | 0.00 | -0.46 | 747 / -157663 / -4699 | n n n n |
| L5|FIX_CAM_L3|tol5 | 0.59 [-0.73, 2.00] | 190 | -2.22 | 0.61 [-1.67, 2.54] | 0.82 | -0.42 | -44340 / -166231 / 6074 | n n n n |
| L5|VWAP_week_up1|tol5 | 0.55 [-0.76, 1.86] | 259 | -2.82 | -0.06 [-1.12, 1.06] | 0.45 | 0.88 | -63000 / -202504 / -8826 | n Y n n |
| L5|FIX_PDC|tol2 | 0.51 [-0.86, 1.98] | 157 | -1.67 | 1.10 [-0.80, 3.36] | 0.93 | 0.86 | -64524 / -128369 / -6974 | n Y n n |
| L5|VWAP_week|tol2 | 0.50 [-0.71, 1.83] | 145 | -4.45 | -1.66 [-4.06, 0.60] | 0.01 | -0.61 | -88889 / -120656 / -38993 | n n n n |
| L5|KELT_20_dn2|tol2 | 0.52 [-0.48, 1.47] | 425 | -2.92 | -0.13 [-1.20, 0.96] | 0.39 | -0.18 | -150292 / -323534 / -101906 | n n n n |
| L5|VWAP_rth_up2|tol5 | 0.45 [-1.06, 2.02] | 93 | -5.06 | -2.32 [-5.22, 0.19] | 0.00 | 0.27 | 6581 / -208465 / -7748 | n Y n n |
| L5|FIX_PDC|tol5 | 0.46 [-0.65, 1.62] | 208 | -1.32 | 1.53 [0.07, 3.19] | 1.00 | 0.53 | -69295 / -166989 / -6046 | Y Y n n |
| L5|VWAP_rth_dn2|tol2 | 0.42 [-1.06, 1.99] | 127 | -1.45 | 1.32 [-0.92, 3.79] | 0.95 | 0.20 | -2940 / -126900 / -11137 | n Y n n |
| L5|VWAP_rth_dn2|tol5 | 0.39 [-0.99, 1.84] | 177 | -1.67 | 1.17 [-0.49, 3.06] | 0.93 | -0.10 | 27210 / -175946 / -23156 | n n n n |
| L5|FIX_CAM_L3|tol2 | 0.40 [-1.20, 2.03] | 143 | -2.47 | 0.37 [-2.33, 3.10] | 0.65 | -0.09 | -17896 / -155210 / 8028 | n n n n |
| L5|VWAP_week|tol5 | 0.34 [-0.60, 1.38] | 212 | -3.85 | -1.03 [-2.87, 0.69] | 0.04 | -0.58 | -151624 / -171785 / -37080 | n n n n |
| L5|VWAP_week_dn1|tol5 | 0.35 [-0.92, 1.61] | 209 | -3.13 | -0.24 [-2.26, 1.73] | 0.33 | -0.70 | -137449 / -160443 / -13179 | n n n n |
| L5|VWAP_eth_up1|tol5 | 0.35 [-0.51, 1.22] | 386 | -2.24 | 0.48 [-0.50, 1.65] | 0.87 | -0.15 | -89563 / -390515 / 398 | n n n n |
| L5|DONCH_MID_26|tol5 | 0.36 [-0.06, 0.76] | 1402 | -2.97 | -0.11 [-0.68, 0.46] | 0.28 | 0.04 | -433621 / -1361687 / -67102 | n Y n n |
| L5|VWAP_eth_dn1|tol5 | 0.23 [-0.69, 1.19] | 431 | -3.11 | -0.19 [-1.53, 1.07] | 0.31 | 0.01 | -204449 / -413376 / -1226 | n Y n n |
| L5|FIX_POC|tol5 | 0.26 [-0.96, 1.48] | 200 | -1.67 | 1.15 [-0.29, 2.81] | 0.96 | 0.79 | -75878 / -164511 / -7961 | n Y n n |
| L5|BOLL_20_up2|tol5 | 0.26 [-0.31, 0.82] | 768 | -2.92 | 0.05 [-0.79, 0.86] | 0.62 | 0.04 | -431616 / -642871 / -62123 | n Y n n |

All 100 joint rows: out/zen/lines/D_hold.json.

## 5. By window (PRE, flat 15:55), by year, long / short, mirror
Joint top 10:
| cell | 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | PRIMARY 10-14 | 14:00-15:30 | RTH pooled |
|---|---|---|---|---|---|---|---|---|
| D|rs60:LSMA_377_close:dist40|time_3m:VIDYA_377_close:tol2 | -1.35 vs -1.81 (n 3; CI -13.2..8.9) | -2.26 vs -2.69 (n 9; CI -7.2..11.0) | 13.86 vs -2.34 (n 9; CI -1.6..39.7) | 5.94 vs -1.06 (n 6; CI -14.7..25.2) | -15.24 vs -4.14 (n 2; CI -12.6..4.4) | 3.44 vs -2.60 (n 25; CI -2.3..14.4) | 1.09 vs -0.32 (n 11; CI -2.0..12.8) | 1.33 vs -2.00 (n 43; CI -1.2..7.4) |
| D|time_15m:VIDYA_377_close:dist40|time_3m:VIDYA_377_hl2:tol2 | -9.13 vs -1.27 (n 7; CI -15.8..4.3) | 2.63 vs -1.12 (n 8; CI -12.5..17.2) | 2.35 vs -2.46 (n 7; CI -1.1..7.9) | 2.53 vs -2.90 (n 3; CI -13.0..25.5) | 4.08 vs -2.71 (n 6; CI -10.8..22.9) | 2.90 vs -2.26 (n 24; CI 0.4..8.4) | -3.05 vs -1.46 (n 9; CI -9.5..7.3) | -0.55 vs -2.02 (n 40; CI -2.6..5.3) |
| D|rs60:SMMA_89_hl2:dist40|time_2m:T3_377_close:tol2 | -8.15 vs -3.21 (n 12; CI -12.3..2.4) | 4.25 vs -1.06 (n 16; CI -4.4..15.4) | 0.49 vs -1.93 (n 11; CI -8.9..7.3) | 5.30 vs -1.92 (n 4; CI -13.8..15.6) | 26.55 vs -1.02 (n 1; CI -0.4..29.2) | 3.78 vs -1.49 (n 32; CI -1.5..10.9) | -1.89 vs -1.10 (n 10; CI -13.7..14.4) | -0.32 vs -1.52 (n 59; CI -4.5..6.6) |
| D|time_15m:VIDYA_377_close:dist40|tick_1000:VIDYA_233_close:tol2 | -6.47 vs -1.27 (n 10; CI -12.2..1.7) | 4.55 vs -1.12 (n 20; CI -3.2..12.2) | 3.87 vs -2.46 (n 6; CI -12.7..11.9) | 4.97 vs -2.90 (n 5; CI -12.6..53.7) | 0.38 vs -2.71 (n 8; CI -8.5..18.8) | 3.04 vs -2.26 (n 38; CI -1.6..11.8) | -1.52 vs -1.46 (n 12; CI -6.9..5.7) | -0.19 vs -2.02 (n 67; CI -1.8..5.2) |
| D|rs60:VIDYA_100_hl2:dist40|time_3m:VIDYA_377_close:tol2 | 5.48 vs -1.93 (n 1; CI -0.6..10.0) | -2.71 vs -1.92 (n 15; CI -7.6..5.0) | 15.35 vs -2.02 (n 5; CI -11.2..44.0) | -2.84 vs -2.29 (n 5; CI -13.0..15.6) | 11.93 vs -2.70 (n 5; CI -10.7..27.2) | 2.72 vs -2.22 (n 30; CI -2.1..17.6) | 2.92 vs -1.13 (n 4; CI 0.1..7.1) | 2.40 vs -1.86 (n 39; CI -2.4..12.0) |
| D|rs240:WMA_100_hl2:dist40|time_3m:VIDYA_377_hl2:tol2 | -5.00 vs -2.32 (n 7; CI -7.6..14.0) | 8.07 vs -2.34 (n 8; CI 1.2..31.1) | 1.69 vs -2.02 (n 5; CI -5.1..16.8) | -2.15 vs -0.99 (n 8; CI -14.3..7.4) | 3.24 vs -0.50 (n 10; CI -3.4..16.2) | 2.85 vs -1.48 (n 31; CI 1.4..8.2) | -4.55 vs -2.25 (n 15; CI -8.6..4.4) | -0.45 vs -1.73 (n 54; CI -1.6..6.1) |
| D|time_15m:VIDYA_377_close:dist40|time_3m:VIDYA_377_close:tol2 | -8.12 vs -1.27 (n 6; CI -15.2..7.1) | 2.07 vs -1.12 (n 11; CI -12.8..7.5) | 9.05 vs -2.46 (n 4; CI 2.0..25.2) | -5.05 vs -2.90 (n 7; CI -13.3..12.9) | 7.95 vs -2.71 (n 5; CI -1.8..25.3) | 2.34 vs -2.26 (n 27; CI -1.9..10.5) | -0.86 vs -1.46 (n 7; CI -4.8..6.5) | 0.15 vs -2.02 (n 44; CI -3.2..7.4) |
| D|rs60:ZLEMA_377_hl2:dist40|time_3m:SMMA_377_close:tol2 | 1.07 vs -2.72 (n 7; CI -7.8..16.8) | 0.97 vs -1.61 (n 18; CI -5.0..14.0) | 12.18 vs -1.22 (n 5; CI -12.8..51.1) | 3.21 vs -1.34 (n 6; CI -7.5..13.3) | -6.17 vs -0.64 (n 3; CI -16.3..12.7) | 2.48 vs -1.24 (n 32; CI -1.5..10.8) | 4.33 vs -1.14 (n 10; CI 0.7..9.1) | 2.76 vs -1.35 (n 52; CI 0.0..8.6) |
| D|rs60:ZLEMA_377_hl2:dist40|time_3m:TMA_34_close:tol2 | -5.55 vs -2.72 (n 8; CI -8.6..6.1) | 11.95 vs -1.61 (n 11; CI 4.4..24.4) | -1.15 vs -1.22 (n 10; CI -6.6..6.6) | 1.54 vs -1.34 (n 13; CI -2.8..10.1) | -5.03 vs -0.64 (n 6; CI -15.3..7.3) | 2.74 vs -1.24 (n 40; CI 0.7..7.3) | -1.00 vs -1.14 (n 11; CI -10.5..13.3) | 0.26 vs -1.35 (n 65; CI -1.7..5.0) |
| D|rs60:ZLEMA_377_hl2:dist40|time_3m:LSMA_233_close:tol2 | -2.59 vs -2.72 (n 7; CI -12.3..16.6) | 4.43 vs -1.61 (n 15; CI 0.3..10.3) | 6.17 vs -1.22 (n 6; CI -2.8..15.8) | -2.03 vs -1.34 (n 8; CI -8.8..7.0) | 0.55 vs -0.64 (n 6; CI -8.5..13.9) | 2.59 vs -1.24 (n 35; CI 0.5..7.7) | 4.84 vs -1.14 (n 10; CI -2.7..25.2) | 2.76 vs -1.35 (n 53; CI 0.5..8.3) |

| cell | 2024 | 2025H1 | long | short | mirror |
|---|---|---|---|---|---|
| D|rs60:LSMA_377_close:dist40|time_3m:VIDYA_377_close:tol2 | net 1.39 eff 4.03 (n 24) | net 52.80 eff 55.10 (n 1) | net 1.98 eff 4.54 (n 16) | net 6.04 eff 8.60 (n 9) | net -2.24 eff -1.84 (n 36) |
| D|time_15m:VIDYA_377_close:dist40|time_3m:VIDYA_377_hl2:tol2 | net 4.02 eff 6.05 (n 17) | net 2.21 eff 4.67 (n 7) | net -3.54 eff -0.44 (n 14) | net 13.33 eff 14.73 (n 10) | net 0.12 eff 0.67 (n 22) |
| D|rs60:SMMA_89_hl2:dist40|time_2m:T3_377_close:tol2 | net 4.82 eff 6.21 (n 26) | net -0.72 eff 1.08 (n 6) | net 6.12 eff 7.88 (n 18) | net 0.78 eff 2.02 (n 14) | net -1.61 eff -0.15 (n 27) |
| D|time_15m:VIDYA_377_close:dist40|tick_1000:VIDYA_233_close:tol2 | net 6.62 eff 8.65 (n 24) | net -3.10 eff -0.63 (n 14) | net 1.10 eff 4.20 (n 18) | net 4.79 eff 6.20 (n 20) | net -3.39 eff -2.84 (n 42) |
| D|rs60:VIDYA_100_hl2:dist40|time_3m:VIDYA_377_close:tol2 | net 7.93 eff 10.00 (n 18) | net -5.10 eff -2.76 (n 12) | net -2.83 eff -0.09 (n 16) | net 9.06 eff 10.71 (n 14) | net -2.42 eff -1.63 (n 23) |
| D|rs240:WMA_100_hl2:dist40|time_3m:VIDYA_377_hl2:tol2 | net 4.06 eff 4.22 (n 24) | net 0.71 eff 5.10 (n 7) | net 0.82 eff 2.77 (n 23) | net 10.44 eff 11.15 (n 8) | net -0.65 eff 0.67 (n 22) |
| D|time_15m:VIDYA_377_close:dist40|time_3m:VIDYA_377_close:tol2 | net 4.03 eff 6.06 (n 19) | net -1.66 eff 0.81 (n 8) | net -1.11 eff 1.98 (n 15) | net 6.67 eff 8.07 (n 12) | net -2.37 eff -1.82 (n 24) |
| D|rs60:ZLEMA_377_hl2:dist40|time_3m:SMMA_377_close:tol2 | net 1.94 eff 2.69 (n 25) | net 7.42 eff 9.95 (n 7) | net 6.20 eff 7.60 (n 22) | net -3.60 eff -2.53 (n 10) | net -6.88 eff -4.98 (n 29) |
| D|rs60:ZLEMA_377_hl2:dist40|time_3m:TMA_34_close:tol2 | net 5.05 eff 5.80 (n 26) | net -1.54 eff 0.99 (n 14) | net 3.67 eff 5.06 (n 20) | net 1.82 eff 2.89 (n 20) | net -4.43 eff -2.53 (n 64) |
| D|rs60:ZLEMA_377_hl2:dist40|time_3m:LSMA_233_close:tol2 | net 2.36 eff 3.10 (n 25) | net 3.16 eff 5.68 (n 10) | net 2.64 eff 4.04 (n 18) | net 2.53 eff 3.60 (n 17) | net -2.81 eff -0.90 (n 32) |

L5 top 10:
| cell | 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | PRIMARY 10-14 | 14:00-15:30 | RTH pooled |
|---|---|---|---|---|---|---|---|---|
| L5|VWAP_week_up2|tol2 | -4.11 vs -2.21 (n 42; CI -5.6..1.9) | 0.49 vs -1.90 (n 74; CI -1.1..5.7) | 0.86 vs -1.65 (n 59; CI -0.7..4.9) | 1.75 vs -1.48 (n 31; CI -0.9..6.9) | -1.29 vs -2.17 (n 23; CI -3.6..4.4) | 0.57 vs -1.80 (n 186; CI 0.4..4.2) | -0.59 vs -1.61 (n 48; CI -3.6..5.1) | -0.33 vs -1.83 (n 281; CI -0.2..3.1) |
| L5|VWAP_week_up2|tol5 | -4.82 vs -2.21 (n 51; CI -6.5..1.0) | -0.81 vs -1.90 (n 91; CI -2.1..3.9) | 2.31 vs -1.65 (n 70; CI 1.3..5.9) | 1.16 vs -1.48 (n 43; CI -0.9..6.3) | -1.28 vs -2.17 (n 38; CI -2.3..4.0) | 0.46 vs -1.80 (n 238; CI 0.7..3.6) | -0.65 vs -1.61 (n 59; CI -3.2..5.2) | -0.58 vs -1.83 (n 359; CI -0.2..2.6) |
| L5|FIX_S2|tol2 | -3.38 vs -2.21 (n 22; CI -6.4..2.9) | 1.43 vs -1.90 (n 34; CI -1.6..9.1) | 2.12 vs -1.65 (n 25; CI -2.9..13.0) | -3.18 vs -1.48 (n 29; CI -6.6..3.8) | -0.48 vs -2.17 (n 27; CI -4.5..7.0) | -0.03 vs -1.80 (n 115; CI -1.0..4.5) | -2.68 vs -1.61 (n 30; CI -5.7..4.9) | -1.06 vs -1.83 (n 170; CI -1.2..2.8) |
| L5|VWAP_eth_dn2|tol5 | -5.94 vs -2.21 (n 33; CI -10.3..2.1) | 0.51 vs -1.90 (n 76; CI -1.0..5.8) | 0.65 vs -1.65 (n 67; CI -0.8..4.9) | -4.74 vs -1.48 (n 48; CI -7.2..0.4) | 1.88 vs -2.17 (n 60; CI -0.5..7.7) | -0.03 vs -1.80 (n 248; CI -0.0..3.5) | 1.74 vs -1.61 (n 94; CI -0.5..7.5) | -0.19 vs -1.83 (n 390; CI 0.1..3.1) |
| L5|VWAP_eth_dn2|tol2 | -5.37 vs -2.21 (n 24; CI -11.4..4.2) | 0.95 vs -1.90 (n 63; CI -1.3..6.9) | -0.46 vs -1.65 (n 55; CI -1.9..4.4) | -4.65 vs -1.48 (n 33; CI -7.1..0.8) | 1.59 vs -2.17 (n 46; CI -0.5..7.7) | -0.19 vs -1.80 (n 195; CI -0.2..3.5) | 1.69 vs -1.61 (n 71; CI -0.9..7.8) | -0.32 vs -1.83 (n 303; CI -0.0..3.2) |
| L5|FIX_S2|tol5 | -2.84 vs -2.21 (n 28; CI -6.2..4.7) | -0.26 vs -1.90 (n 45; CI -3.4..8.2) | 1.11 vs -1.65 (n 31; CI -2.7..10.4) | -2.06 vs -1.48 (n 33; CI -5.6..4.2) | -0.66 vs -2.17 (n 33; CI -4.8..8.3) | -0.47 vs -1.80 (n 142; CI -1.4..4.3) | -3.40 vs -1.61 (n 39; CI -5.6..2.6) | -1.36 vs -1.83 (n 214; CI -1.5..2.4) |
| L5|VWAP_overnight|tol5 | -2.45 vs -2.21 (n 325; CI -1.7..1.2) | -1.19 vs -1.90 (n 388; CI -0.6..2.0) | -0.43 vs -1.65 (n 219; CI -0.6..3.5) | 0.11 vs -1.48 (n 137; CI -0.6..4.0) | -0.33 vs -2.17 (n 117; CI -1.1..4.7) | -0.77 vs -1.80 (n 844; CI 0.1..2.0) | -2.64 vs -1.61 (n 147; CI -3.0..0.8) | -1.29 vs -1.83 (n 1355; CI -0.3..1.3) |
| L5|VWAP_overnight|tol2 | -2.52 vs -2.21 (n 236; CI -2.2..1.7) | -1.15 vs -1.90 (n 274; CI -0.6..2.2) | -0.60 vs -1.65 (n 158; CI -1.4..3.8) | -0.61 vs -1.48 (n 92; CI -2.1..3.6) | -0.41 vs -2.17 (n 76; CI -2.1..5.2) | -0.89 vs -1.80 (n 588; CI -0.2..2.0) | -3.32 vs -1.61 (n 97; CI -4.2..0.8) | -1.51 vs -1.83 (n 948; CI -0.6..1.3) |
| L5|ST_10_3|tol2 | -3.90 vs -2.21 (n 125; CI -4.5..1.2) | -0.61 vs -1.90 (n 233; CI -1.0..3.7) | -1.79 vs -1.65 (n 219; CI -2.0..1.7) | -0.73 vs -1.48 (n 184; CI -1.3..2.7) | -0.42 vs -2.17 (n 228; CI -0.0..3.5) | -0.94 vs -1.80 (n 852; CI -0.0..1.7) | -0.27 vs -1.61 (n 298; CI -0.1..2.7) | -1.12 vs -1.83 (n 1363; CI 0.0..1.3) |
| L5|FIX_VAH|tol2 | -1.90 vs -2.21 (n 81; CI -2.8..3.9) | -1.75 vs -1.90 (n 127; CI -2.5..3.2) | -1.56 vs -1.65 (n 100; CI -2.0..2.4) | 0.33 vs -1.48 (n 66; CI -1.2..4.6) | -0.59 vs -2.17 (n 65; CI -1.7..4.8) | -1.13 vs -1.80 (n 352; CI -0.9..2.3) | -2.51 vs -1.61 (n 89; CI -4.1..2.5) | -1.41 vs -1.83 (n 545; CI -0.8..1.9) |

| cell | 2024 | 2025H1 | long | short | mirror |
|---|---|---|---|---|---|
| L5|VWAP_week_up2|tol2 | net 1.97 eff 3.14 (n 129) | net -2.58 eff 0.28 (n 57) | net 0.57 eff 2.41 (n 186) | n 0 | net -3.36 eff -1.80 (n 216) |
| L5|VWAP_week_up2|tol5 | net 1.17 eff 2.34 (n 170) | net -1.32 eff 1.54 (n 68) | net 0.52 eff 2.36 (n 237) | net -15.24 eff -13.46 (n 1) | net -3.23 eff -1.67 (n 277) |
| L5|FIX_S2|tol2 | net 3.29 eff 4.46 (n 46) | net -2.36 eff 0.50 (n 69) | net -1.97 eff -0.13 (n 3) | net -0.05 eff 1.73 (n 112) | net -2.03 eff -0.47 (n 119) |
| L5|VWAP_eth_dn2|tol5 | net 0.26 eff 1.43 (n 173) | net -0.94 eff 1.93 (n 75) | net -4.00 eff -2.17 (n 5) | net -0.02 eff 1.76 (n 243) | net -0.24 eff 1.33 (n 328) |
| L5|VWAP_eth_dn2|tol2 | net -0.03 eff 1.15 (n 129) | net -0.73 eff 2.14 (n 66) | net -1.19 eff 0.64 (n 4) | net -0.24 eff 1.54 (n 191) | net -0.40 eff 1.16 (n 279) |
| L5|FIX_S2|tol5 | net 2.77 eff 3.94 (n 57) | net -2.84 eff 0.02 (n 85) | net 4.08 eff 5.92 (n 5) | net -0.76 eff 1.02 (n 137) | net -2.17 eff -0.60 (n 162) |
| L5|VWAP_overnight|tol5 | net -0.50 eff 0.67 (n 560) | net -1.29 eff 1.57 (n 284) | net -1.00 eff 0.84 (n 410) | net -0.56 eff 1.23 (n 450) | net -1.50 eff 0.07 (n 912) |
| L5|VWAP_overnight|tol2 | net -0.42 eff 0.75 (n 391) | net -1.87 eff 0.99 (n 197) | net -0.81 eff 1.03 (n 285) | net -1.01 eff 0.78 (n 316) | net -1.57 eff -0.01 (n 645) |
| L5|ST_10_3|tol2 | net -0.19 eff 0.99 (n 547) | net -2.57 eff 0.29 (n 305) | net -1.48 eff 0.36 (n 460) | net -0.53 eff 1.26 (n 392) | net -1.49 eff 0.07 (n 742) |
| L5|FIX_VAH|tol2 | net -0.03 eff 1.14 (n 229) | net -2.96 eff -0.09 (n 123) | net -1.73 eff 0.11 (n 257) | net 0.74 eff 2.53 (n 98) | net -1.84 eff -0.27 (n 403) |

## 6. L6 robustness
### Neighbour stability (PRE, effect vs random-in-regime; lookback either side, same type / price / timeframe / semantics)
| role | base line | base | neighbours | verdict |
|---|---|---|---|---|
| regime | WMA_100_hl2 | +1.85 (n 134) | 89 +0.21 (n 132), 144 -1.95 (n 96) | FLIPS |
| regime | WMA_50_hlc3 | +1.59 (n 188) | 34 -0.04 (n 210), 55 -0.46 (n 196) | FLIPS |
| regime | VIDYA_377_close | +1.57 (n 120) | 233 +0.92 (n 206) | same sign |
| regime | VIDYA_100_hl2 | +1.52 (n 140) | 89 +0.90 (n 175), 144 -1.81 (n 98) | FLIPS |
| regime | T3_34_hl2 | +1.51 (n 100) | 21 -0.95 (n 201), 50 -1.45 (n 119) | FLIPS |
| regime | ZLEMA_377_hl2 | +1.43 (n 118) | 233 +1.41 (n 195) | same sign |
| regime | SMMA_89_hl2 | +1.43 (n 162) | 55 -0.84 (n 197), 100 +0.74 (n 158) | FLIPS |
| regime | VIDYA_89_close | +1.42 (n 143) | 55 -0.10 (n 215), 100 -0.55 (n 131) | FLIPS |
| regime | ZLEMA_233_hl2 | +1.41 (n 195) | 200 +0.03 (n 296), 377 +1.43 (n 118) | same sign |
| regime | LSMA_377_close | +1.39 (n 146) | 233 -0.82 (n 193) | FLIPS |
| entry | T3_233_close | +2.33 (n 352) | 200 +0.20 (n 370), 377 -0.73 (n 317) | FLIPS |
| entry | TMA_377_close | +1.37 (n 511) | 233 +0.30 (n 566) | same sign |
| entry | SMMA_377_close | +1.32 (n 288) | 233 +0.11 (n 470) | same sign |
| entry | TMA_34_close | +1.21 (n 705) | 21 -0.56 (n 917), 50 +0.37 (n 656) | FLIPS |
| entry | T3_377_close | +1.14 (n 373) | 233 -2.11 (n 419) | FLIPS |
| entry | ZLEMA_233_close | +1.12 (n 603) | 200 +0.15 (n 632), 377 +0.23 (n 492) | same sign |
| entry | VIDYA_377_hl2 | +1.00 (n 266) | 233 -0.48 (n 351) | FLIPS |
| entry | LSMA_233_close | +0.99 (n 578) | 200 -0.37 (n 606), 377 +0.55 (n 534) | FLIPS |
| entry | VIDYA_233_close | +0.94 (n 437) | 200 -0.26 (n 465), 377 -0.27 (n 274) | FLIPS |
| entry | VIDYA_377_close | +0.91 (n 237) | 233 +0.53 (n 332) | same sign |

**13 of 20 base lines flip sign with a neighbouring lookback** (rule: must not flip). No top line is neighbour-stable in the sense required.


### Overlap with the live PE book (PB) and the trend books (ST / HM / WT): share of the cell's PRE trades with a book entry within +-5 min (any side; same side in brackets for the reference)
| set | PE | ST | HM | WT | KB | SM |
|---|---|---|---|---|---|---|
| B top 10 | 4.3% | 4.4% | 3.0% | 5.0% | 3.1% | 1.2% |
| C top 10 (R1 + BBEST singles) | 6.6% | 4.9% | 2.2% | 6.6% | 4.3% | 1.3% |
| EMA200/EMA200 reference | 4.8% (1.9%) | 4.1% (1.7%) | 3.2% (1.7%) | 6.2% (3.0%) | 4.6% (1.7%) | 0.5% (0.1%) |

Overlap is small (4-7% of trades share a +-5 min entry with PE or a trend book; the cells trade ~0.2-0.5 trades/week at n 100-300), so there is nothing to net: the stack add of any LINES cell is its own standalone result, and that is negative or inside the MDE (reference EMA200/EMA200: -0.22 pt/trade net of the random-in-regime pool, i.e. -$44 per trade at 10 lots versus the pool).

### Mirror, by year, 2x cost
Mirror (opposite side at the same events) is in the year tables above (column 'mirror'); by year in the same tables; 2x cost: net2 > 0 in 0 of 7,085 B cells and 0 of 3,652 C cells and in none of the 130 holdout cells' PRE rows beyond noise.

## 7. Realised stop and R:R
Stop 15.0 pt; median target distance about 10-13 pt (R:R about 0.7).

## Deviations and disclosures
- Screen is on the mapped conservative basis (1-min OHLC fills; 0.05-0.13 pts/trade more conservative than 1-s on tight stops). **G10 (direct 1-s/L2 replay) was NOT run** by this agent (needs a replay worker allow-listed in the governor; request in MORNING.md). No cell can therefore be labelled CANDIDATE; the best possible label is 'screen G1-G9 pass, G10 pending'; none reached it.
- Bracket (fixed for all LINES blocks): 15-pt stop measured from the entry price (the realised stop is exactly 15.0 pt for every trade: median = p90 = 15), target = nearest confirmed 1-min swing (k=2, last 12 swings) beyond the entry at distance 5..60 pt; entries with no such target do not exist (about 48% of bar x side rows, same rule in every placebo pool). Median realised target distance and R:R are in the tables (R:R = target distance / 15, about 0.7).
- All trades come from `Z.simulate()` (table built once per entry bar x side; identity to a fresh `simulate()` on 300 random events is a unit test). `zen_struct.grid_eval` is NOT used, so the fill_mode=1 grid bug reported by D3ZF1 does not apply (market entries only).
- The one-open-trade rule is applied to each real set; the grid placebo is the exact pool expectation (unsequenced); the top cells are re-run with `Z.placebo_in_regime` / `placebo_random_dir` (100 draws) and agree with the pool expectation to within 0.1 pt in all spot checks (D_top_pre.json).
- Gate G1 rank: in the grid the rank gate is replaced by the week-block bootstrap (CI lower > 0); the full-draw rank is reported for the top cells. G2 likewise.
- By-window tables use a separate engine with entries 09:30-15:55 and flat 15:55 (so the PRIMARY row there is the 15:55-flat variant); the screen itself is flat 14:00 only (plan table). Flat-15:55 and window re-reads are counted as disclosed additions to N.
- Holdout looks used: ONE look (HOLD) + ONE X read for this block, logged in out/zen/lines/looks.jsonl and DECISIONS.md BEFORE HOLD/X were read. The 2023 X span is in memory during the screen for line warm-up but is not scored.
- Selection effects: cells chosen on PRE effect (top 30 per prereg rule); the winner's-curse is visible: PRE effects of the selected cells average +1.3 (B), +2.0 (C) pt/trade and fall to +0.5 (B), -1.2 (C) in HOLD.
- Closed-bar rule: `out/zen/lines/zl_test.log`, 24 tests, 0 failures (events, regimes, entry lines, stacks unchanged when all later bars are deleted).
- Files: code l2vast/ds3/code/zen/lines/*.py; outputs l2vast/ds3/out/zen/lines/ ; prereg l2vast/ds3/prereg/ZEN_LINES_{B,C,D}_prereg.md(+.sha256).
- The joint cells have n < 100 in PRE: the prereg sent all 100 to the holdout anyway; HOLD counts are 3-35 trades per cell, so the holdout look is inconclusive per cell, informative only in aggregate.
- L6 neighbour reads (40 lines) are robustness reads, not selection.

DONE LINES_D
