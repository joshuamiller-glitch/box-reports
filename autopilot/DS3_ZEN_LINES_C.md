# DS3_ZEN_LINES_C - entry-line search (regime 5m EMA200 and the best B line) and stack variants (D3ZLN, 2026-10-28)

**Verdict line:** best regime line / best entry line / EMA200 rank among N / effect vs random with MDE: best regime line = B|rs240|WMA_100_hl2|dist40 (LINES_B; inside MDE, dead in HOLD); **best entry line (regime 5-min EMA200) = C|time_3m|T3_233_close|tol2|R1: effect +2.33 pt/trade [0.86, 3.90] vs random-in-regime, MDE80 2.19 (n 352, win 60.2% vs BE 58.2%, net1 +0.52 but net2 -1.63), HOLD -1.45 [-3.35, 0.45], X +0.07**; the 1-min EMA200 (tol 2, regime 5m EMA200) ranks 1523 of 2266 R1 cells (2071 of 3652 all eligible) with effect -0.22 [-0.94, 0.58] (MDE80 1.08); 1 cell(s) beat the 1-min EMA200 paired by more than the MDE (the 3-min T3-233 line, difference +2.55 vs MDE80 2.33) but it fails the reality check (p 0.74 over N = 4,712) and HOLD: **no entry line, no stack, adds anything over a random entry in the same regime; the EMA200 is an ordinary member (below median).**

## 1. Counts block
Entry clusters 1,133 (1m 165, 30s 128, 15s 81, 2m 193, 3m 209, 500-tick 164, 1000-tick 193). Events per cell mapped to a 10:00-14:00 PRE entry minute are in C_pre.parquet (`n_events_raw`, `dropped`). Cells with n < 100: 1060 of 4,712 (counts, not verdicts); eligible: 3652 (R1 2266, BBEST 1380, stacks 6). Entry bars of sub-minute / tick lines are mapped to the next 1-min open (documented delay, up to 1 min).

## 2. Grid enumeration and screened N
1,133 clusters x tol {2,5} x regime {R1, BBEST} = 4,532 + 180 stack variants (45 pairs of the top-10 R1 lines x distance {3,5} x regime {R1,BBEST}) = **4,712 scored, 0 skipped**. Prereg `ZEN_LINES_C_prereg.md` sha256 8f2949a6c50ddb13223ad6f08b9b778c07daea4e796e6121f12d5ff821c5e380. BBEST = B|rs240|WMA_100_hl2|dist40 (rule fixed in the prereg). Reality check (studentised max, 2,000 week-block draws) over the eligible cells: best t 2.98, **p = 0.739** (raw-max p 0.411).

Eligible cells: effect>0 in 1130, CI lower>0 in 23 (23 of 3,652; 14 R1, 9 BBEST), mean net1>0 in 40, **net2>0 in 0**, effect >= MDE80 in 1. The stacks: 6 of 180 have n >= 100; best stack effect +0.50 (MDE80 2.10) - a stack adds nothing (ZM2 generalised is dead).


By entry timeframe (eligible cells: median effect / best / CI>0 count): tick_1000: -0.18 / 1.92 / 1; tick_500: -0.20 / 1.51 / 1; time_15s: -0.18 / 2.06 / 0; time_1m: -0.16 / 3.40 / 7; time_2m: -0.21 / 1.48 / 1; time_30s: -0.17 / 2.95 / 3; time_3m: -0.00 / 2.33 / 10. The 3-minute lines are the only timeframe whose median is near 0; sub-minute and tick lines are worse than the pool (the mapped one-minute delay costs).

## 3. Top-10 tables
### 3a. Regime = 5-min EMA200 (R1), single lines
| # | cell | n | tr/wk | win | BE | net1 pts ($/tr 10 lots) | net2 | random-in-regime | effect [CI] | MDE80 | eff vs rand-dir | fw80 | PRE rank-vs-draws | HOLD effect [CI] (n) | X effect | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | C|time_3m|T3_233_close|tol2|R1 | 352 | 4.69 | 0.602 | 0.582 | 0.52 ($103) | -1.63 | -1.81 | 2.33 [0.86, 3.90] | 2.19 | 1.23 | 66 | - | -1.45 [-3.35, 0.45] (101) | 0.07 | G2(rd 1.23, CI lo -0.57); G3(net1 0.52 net2 -1.63); G6(hold); G8(hold); G9(hold); G10 not run |
| 2 | C|time_3m|T3_233_close|tol5|R1 | 460 | 6.13 | 0.583 | 0.585 | -0.07 ($-14) | -2.14 | -1.81 | 1.74 [0.57, 3.02] | 1.80 | 0.47 | 80 | - | -0.91 [-2.67, 0.85] (137) | -0.39 | G2(rd 0.47, CI lo -0.90); G3(net1 -0.07 net2 -2.14); G4(win-BE -0.3 pp); G5(effect 1.74 < MDE80 1.80: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 3 | C|time_3m|TMA_377_close|tol5|R1 | 511 | 6.81 | 0.585 | 0.603 | -0.44 ($-88) | -2.63 | -1.81 | 1.37 [0.26, 2.46] | 1.59 | 0.76 | 101 | - | -0.89 [-2.32, 0.38] (191) | 0.27 | G2(rd 0.76, CI lo -0.58); G3(net1 -0.44 net2 -2.63); G4(win-BE -1.8 pp); G5(effect 1.37 < MDE80 1.59: inside MDE); G6(hold); G8(hold); G9(hold); G10 not run |
| 4 | C|time_3m|TMA_377_close|tol2|R1 | 372 | 4.96 | 0.581 | 0.598 | -0.45 ($-89) | -2.64 | -1.81 | 1.36 [-0.04, 2.74] | 2.01 | 1.03 | 163 | - | -0.78 [-2.38, 0.46] (149) | 0.57 | G1(CI lo -0.04); G2(rd 1.03, CI lo -0.63); G3(net1 -0.45 net2 -2.64); G4(win-BE -1.8 pp); G5(effect 1.36 < MDE80 2.01: inside MDE); G6(hold); G8(hold); G9(hold); G10 not run |
| 5 | C|time_3m|SMMA_377_close|tol2|R1 | 288 | 3.84 | 0.573 | 0.592 | -0.49 ($-98) | -2.50 | -1.81 | 1.32 [-0.22, 2.85] | 2.25 | 1.55 | 216 | - | -0.85 [-4.39, 2.21] (119) | 0.27 | G1(CI lo -0.22); G2(rd 1.55, CI lo -0.47); G3(net1 -0.49 net2 -2.50); G4(win-BE -1.9 pp); G5(effect 1.32 < MDE80 2.25: inside MDE); G6(hold); G8(hold); G9(hold); G10 not run |
| 6 | C|time_3m|TMA_34_close|tol2|R1 | 705 | 9.40 | 0.620 | 0.646 | -0.60 ($-119) | -2.84 | -1.81 | 1.21 [0.34, 2.15] | 1.30 | 0.99 | 85 | - | -1.36 [-2.91, 0.31] (273) | -0.51 | G2(rd 0.99, CI lo -0.13); G3(net1 -0.60 net2 -2.84); G4(win-BE -2.6 pp); G5(effect 1.21 < MDE80 1.30: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 7 | C|time_2m|T3_377_close|tol2|R1 | 373 | 4.97 | 0.568 | 0.595 | -0.67 ($-134) | -2.86 | -1.81 | 1.14 [-0.37, 2.73] | 2.26 | 0.26 | 294 | - | -0.34 [-2.27, 1.64] (127) | -0.52 | G1(CI lo -0.37); G2(rd 0.26, CI lo -1.54); G3(net1 -0.67 net2 -2.86); G4(win-BE -2.6 pp); G5(effect 1.14 < MDE80 2.26: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 8 | C|time_3m|ZLEMA_233_close|tol2|R1 | 603 | 8.04 | 0.579 | 0.607 | -0.69 ($-137) | -2.77 | -1.81 | 1.12 [0.14, 2.06] | 1.39 | 0.88 | 115 | - | 1.62 [0.10, 3.21] (219) | -0.49 | G2(rd 0.88, CI lo -0.52); G3(net1 -0.69 net2 -2.77); G4(win-BE -2.8 pp); G5(effect 1.12 < MDE80 1.39: inside MDE); G7(hold); G8(hold); G9(hold); G10 not run |
| 9 | C|time_3m|VIDYA_377_hl2|tol2|R1 | 266 | 3.55 | 0.560 | 0.592 | -0.81 ($-162) | -2.86 | -1.81 | 1.00 [-0.62, 2.70] | 2.37 | 0.75 | 417 | - | 2.94 [-1.01, 6.93] (72) | 0.28 | G1(CI lo -0.62); G2(rd 0.75, CI lo -1.40); G3(net1 -0.81 net2 -2.86); G4(win-BE -3.2 pp); G5(effect 1.00 < MDE80 2.37: inside MDE); G6(hold); G8(hold); G9(hold); G10 not run |
| 10 | C|time_3m|LSMA_233_close|tol2|R1 | 578 | 7.71 | 0.571 | 0.604 | -0.82 ($-164) | -2.99 | -1.81 | 0.99 [-0.03, 2.07] | 1.49 | 0.12 | 170 | - | 0.70 [-1.04, 2.42] (234) | -0.47 | G1(CI lo -0.03); G2(rd 0.12, CI lo -1.18); G3(net1 -0.82 net2 -2.99); G4(win-BE -3.3 pp); G5(effect 0.99 < MDE80 1.49: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |

### 3b. Regime = best B line (BBEST; a selected regime, trade counts 100-150, winner's-curse prone)
| # | cell | n | tr/wk | win | BE | net1 pts ($/tr 10 lots) | net2 | random-in-regime | effect [CI] | MDE80 | eff vs rand-dir | fw80 | PRE rank-vs-draws | HOLD effect [CI] (n) | X effect | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | C|time_1m|VIDYA_50_close|tol5|BBEST | 109 | 1.45 | 0.661 | 0.579 | 2.01 ($402) | -0.41 | -1.39 | 3.40 [0.85, 6.43] | 3.97 | 0.89 | 102 | - | -2.26 [-5.09, 0.68] (39) | -1.08 | G2(rd 0.89, CI lo -3.82); G3(net1 2.01 net2 -0.41); G5(effect 3.40 < MDE80 3.97: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 2 | C|time_30s|SMMA_144_close|tol2|BBEST | 109 | 1.45 | 0.670 | 0.604 | 1.56 ($312) | -0.83 | -1.39 | 2.95 [0.28, 5.75] | 3.88 | 1.47 | 129 | - | -3.30 [-7.26, -0.59] (38) | -0.21 | G2(rd 1.47, CI lo -1.35); G3(net1 1.56 net2 -0.83); G5(effect 2.95 < MDE80 3.88: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 3 | C|time_1m|EMA_200_close|tol5|BBEST | 109 | 1.45 | 0.679 | 0.615 | 1.51 ($302) | -0.87 | -1.39 | 2.90 [0.11, 6.56] | 4.66 | 1.03 | 194 | - | -1.95 [-5.73, 0.22] (29) | -0.25 | G2(rd 1.03, CI lo -2.08); G3(net1 1.51 net2 -0.87); G5(effect 2.90 < MDE80 4.66: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 4 | C|time_1m|SMA_144_close|tol5|BBEST | 116 | 1.55 | 0.664 | 0.615 | 1.13 ($226) | -1.24 | -1.39 | 2.52 [0.25, 5.02] | 3.46 | 1.38 | 141 | - | -2.68 [-6.22, 2.40] (24) | -0.60 | G2(rd 1.38, CI lo -2.41); G3(net1 1.13 net2 -1.24); G5(effect 2.52 < MDE80 3.46: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 5 | C|time_1m|KAMA_200_close|tol5|BBEST | 118 | 1.57 | 0.653 | 0.609 | 1.05 ($210) | -1.48 | -1.39 | 2.44 [-0.10, 5.19] | 3.75 | 2.15 | 177 | - | -3.95 [-7.49, -1.16] (34) | -1.30 | G1(CI lo -0.10); G2(rd 2.15, CI lo -0.80); G3(net1 1.05 net2 -1.48); G5(effect 2.44 < MDE80 3.75: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 6 | C|time_1m|SMMA_89_close|tol5|BBEST | 122 | 1.63 | 0.648 | 0.608 | 0.95 ($190) | -1.40 | -1.39 | 2.34 [-0.79, 6.06] | 4.96 | -0.67 | 337 | - | -2.62 [-6.25, -0.16] (32) | -0.48 | G1(CI lo -0.79); G2(rd -0.67, CI lo -4.08); G3(net1 0.95 net2 -1.40); G5(effect 2.34 < MDE80 4.96: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 7 | C|time_1m|KAMA_377_hl2|tol5|BBEST | 115 | 1.53 | 0.652 | 0.613 | 0.91 ($182) | -1.39 | -1.39 | 2.30 [-0.04, 4.72] | 3.38 | 1.45 | 161 | - | -1.91 [-5.97, 0.86] (34) | -2.23 | G1(CI lo -0.04); G2(rd 1.45, CI lo -2.46); G3(net1 0.91 net2 -1.39); G5(effect 2.30 < MDE80 3.38: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 8 | C|time_30s|WMA_377_close|tol2|BBEST | 107 | 1.43 | 0.626 | 0.595 | 0.76 ($153) | -1.52 | -1.39 | 2.16 [-0.16, 4.91] | 3.66 | 1.80 | 216 | - | -1.94 [-6.78, 2.32] (28) | -1.99 | G1(CI lo -0.16); G2(rd 1.80, CI lo -2.27); G3(net1 0.76 net2 -1.52); G5(effect 2.16 < MDE80 3.66: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 9 | C|time_1m|ALMA_100_hl2|tol2|BBEST | 134 | 1.79 | 0.687 | 0.654 | 0.76 ($151) | -1.64 | -1.39 | 2.15 [0.13, 4.09] | 2.77 | 2.96 | 125 | - | -1.44 [-3.49, 1.82] (57) | -0.28 | G3(net1 0.76 net2 -1.64); G5(effect 2.15 < MDE80 2.77: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 10 | C|time_1m|VIDYA_89_hl2|tol5|BBEST | 104 | 1.39 | 0.635 | 0.605 | 0.73 ($146) | -1.64 | -1.39 | 2.12 [-1.32, 6.43] | 5.56 | 0.13 | 516 | - | -2.54 [-7.16, -0.02] (27) | 0.30 | G1(CI lo -1.32); G2(rd 0.13, CI lo -3.92); G3(net1 0.73 net2 -1.64); G5(effect 2.12 < MDE80 5.56: inside MDE); G6(hold); G8(hold); G9(hold); G10 not run |

### 3c. All cells incl. stacks
| # | cell | n | tr/wk | win | BE | net1 pts ($/tr 10 lots) | net2 | random-in-regime | effect [CI] | MDE80 | eff vs rand-dir | fw80 | PRE rank-vs-draws | HOLD effect [CI] (n) | X effect | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | C|time_1m|VIDYA_50_close|tol5|BBEST | 109 | 1.45 | 0.661 | 0.579 | 2.01 ($402) | -0.41 | -1.39 | 3.40 [0.85, 6.43] | 3.97 | 0.89 | 102 | - | -2.26 [-5.09, 0.68] (39) | -1.08 | G2(rd 0.89, CI lo -3.82); G3(net1 2.01 net2 -0.41); G5(effect 3.40 < MDE80 3.97: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 2 | C|time_30s|SMMA_144_close|tol2|BBEST | 109 | 1.45 | 0.670 | 0.604 | 1.56 ($312) | -0.83 | -1.39 | 2.95 [0.28, 5.75] | 3.88 | 1.47 | 129 | - | -3.30 [-7.26, -0.59] (38) | -0.21 | G2(rd 1.47, CI lo -1.35); G3(net1 1.56 net2 -0.83); G5(effect 2.95 < MDE80 3.88: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 3 | C|time_1m|EMA_200_close|tol5|BBEST | 109 | 1.45 | 0.679 | 0.615 | 1.51 ($302) | -0.87 | -1.39 | 2.90 [0.11, 6.56] | 4.66 | 1.03 | 194 | - | -1.95 [-5.73, 0.22] (29) | -0.25 | G2(rd 1.03, CI lo -2.08); G3(net1 1.51 net2 -0.87); G5(effect 2.90 < MDE80 4.66: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 4 | C|time_1m|SMA_144_close|tol5|BBEST | 116 | 1.55 | 0.664 | 0.615 | 1.13 ($226) | -1.24 | -1.39 | 2.52 [0.25, 5.02] | 3.46 | 1.38 | 141 | - | -2.68 [-6.22, 2.40] (24) | -0.60 | G2(rd 1.38, CI lo -2.41); G3(net1 1.13 net2 -1.24); G5(effect 2.52 < MDE80 3.46: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 5 | C|time_1m|KAMA_200_close|tol5|BBEST | 118 | 1.57 | 0.653 | 0.609 | 1.05 ($210) | -1.48 | -1.39 | 2.44 [-0.10, 5.19] | 3.75 | 2.15 | 177 | - | -3.95 [-7.49, -1.16] (34) | -1.30 | G1(CI lo -0.10); G2(rd 2.15, CI lo -0.80); G3(net1 1.05 net2 -1.48); G5(effect 2.44 < MDE80 3.75: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 6 | C|time_1m|SMMA_89_close|tol5|BBEST | 122 | 1.63 | 0.648 | 0.608 | 0.95 ($190) | -1.40 | -1.39 | 2.34 [-0.79, 6.06] | 4.96 | -0.67 | 337 | - | -2.62 [-6.25, -0.16] (32) | -0.48 | G1(CI lo -0.79); G2(rd -0.67, CI lo -4.08); G3(net1 0.95 net2 -1.40); G5(effect 2.34 < MDE80 4.96: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 7 | C|time_3m|T3_233_close|tol2|R1 | 352 | 4.69 | 0.602 | 0.582 | 0.52 ($103) | -1.63 | -1.81 | 2.33 [0.86, 3.90] | 2.19 | 1.23 | 66 | - | -1.45 [-3.35, 0.45] (101) | 0.07 | G2(rd 1.23, CI lo -0.57); G3(net1 0.52 net2 -1.63); G6(hold); G8(hold); G9(hold); G10 not run |
| 8 | C|time_1m|KAMA_377_hl2|tol5|BBEST | 115 | 1.53 | 0.652 | 0.613 | 0.91 ($182) | -1.39 | -1.39 | 2.30 [-0.04, 4.72] | 3.38 | 1.45 | 161 | - | -1.91 [-5.97, 0.86] (34) | -2.23 | G1(CI lo -0.04); G2(rd 1.45, CI lo -2.46); G3(net1 0.91 net2 -1.39); G5(effect 2.30 < MDE80 3.38: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 9 | C|time_30s|WMA_377_close|tol2|BBEST | 107 | 1.43 | 0.626 | 0.595 | 0.76 ($153) | -1.52 | -1.39 | 2.16 [-0.16, 4.91] | 3.66 | 1.80 | 216 | - | -1.94 [-6.78, 2.32] (28) | -1.99 | G1(CI lo -0.16); G2(rd 1.80, CI lo -2.27); G3(net1 0.76 net2 -1.52); G5(effect 2.16 < MDE80 3.66: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |
| 10 | C|time_1m|ALMA_100_hl2|tol2|BBEST | 134 | 1.79 | 0.687 | 0.654 | 0.76 ($151) | -1.64 | -1.39 | 2.15 [0.13, 4.09] | 2.77 | 2.96 | 125 | - | -1.44 [-3.49, 1.82] (57) | -0.28 | G3(net1 0.76 net2 -1.64); G5(effect 2.15 < MDE80 2.77: inside MDE); G6(hold); G7(hold); G8(hold); G9(hold); G10 not run |

EMA200 references: C|time_1m|EMA_200_close|tol2|R1: effect -0.22 [-0.94, 0.58], n 1101, rank 2071.0; C|time_1m|EMA_200_close|tol2|BBEST: effect +2.80 [-0.25, 7.06], n 77, rank nan; C|time_1m|EMA_200_close|tol5|R1: effect -0.08 [-0.69, 0.54], n 1551, rank 1454.0; C|time_1m|EMA_200_close|tol5|BBEST: effect +2.90 [0.11, 6.56], n 109, rank 3.0.

Paired vs the 1-min EMA200 (same tolerance and regime), cells with difference CI lower > 0 AND > MDE80 of the difference: **1** (C|time_3m|T3_233_close|tol2|R1 diff +2.55 vs MDE80 2.33).

## 4. Holdout (top 30 + 10 R1 cells, ONE look) and gates
Pre-holdout text DS3_ZEN_LINES_C_PREHOLD.md. 38 cells looked at. G6 pass 2, G7 18, G8 0 (none), G9 1. Cells passing G6 (HOLD CI lower > 0): C|time_1m|SMMA_34_close|tol2|BBEST (HOLD +3.96, X -0.75), C|time_3m|ZLEMA_233_close|tol2|R1 (HOLD +1.62, X -0.49). Both fail G7 or G8 or the 2x-cost gate; **0 CANDIDATE, 0 LEAD.** Mean HOLD effect of the cells = -1.15 vs PRE 1.97.

| cell | PRE (re-run) effect [CI] | HOLD n | HOLD net1 | HOLD effect [CI] | rank | X (2023-04..2024-01) effect | 2024 net$ / 2025 / 2026 (10 lots, $) | G6 G7 G8 G9 |
|---|---|---|---|---|---|---|---|---|
| C|time_1m|VIDYA_50_close|tol5|BBEST | 3.46 [0.80, 6.52] | 39 | -4.22 | -2.26 [-5.09, 0.68] | 0.05 | -1.08 | 53850 / -17785 / -23051 | n n n n |
| C|time_30s|SMMA_144_close|tol2|BBEST | 3.00 [0.36, 5.63] | 38 | -5.29 | -3.30 [-7.26, -0.59] | 0.00 | -0.21 | 57548 / -45874 / -16103 | n n n n |
| C|time_1m|EMA_200_close|tol5|BBEST | 2.94 [0.01, 6.65] | 29 | -3.95 | -1.95 [-5.73, 0.22] | 0.04 | -0.25 | 58142 / -38413 / -9869 | n n n n |
| C|time_1m|SMA_144_close|tol5|BBEST | 2.63 [0.32, 5.11] | 24 | -4.71 | -2.68 [-6.22, 2.40] | 0.00 | -0.60 | 32232 / -12364 / -12381 | n n n n |
| C|time_1m|KAMA_200_close|tol5|BBEST | 2.54 [0.04, 5.26] | 34 | -6.00 | -3.95 [-7.49, -1.16] | 0.00 | -1.30 | 19201 / -19147 / -16142 | n n n n |
| C|time_1m|SMMA_89_close|tol5|BBEST | 2.40 [-0.71, 6.14] | 32 | -4.63 | -2.62 [-6.25, -0.16] | 0.01 | -0.48 | 64474 / -52317 / -14931 | n n n n |
| C|time_3m|T3_233_close|tol2|R1 | 2.33 [0.88, 3.89] | 101 | -4.09 | -1.45 [-3.35, 0.45] | 0.05 | 0.07 | 55407 / -90239 / -7734 | n Y n n |
| C|time_1m|KAMA_377_hl2|tol5|BBEST | 2.39 [0.02, 4.85] | 34 | -3.94 | -1.91 [-5.97, 0.86] | 0.07 | -2.23 | 34588 / -27584 / -8246 | n n n n |
| C|time_30s|WMA_377_close|tol2|BBEST | 2.18 [-0.30, 4.98] | 28 | -3.90 | -1.94 [-6.78, 2.32] | 0.05 | -1.99 | 20351 / -12222 / -13629 | n n n n |
| C|time_1m|ALMA_100_hl2|tol2|BBEST | 2.23 [0.38, 4.04] | 57 | -3.39 | -1.44 [-3.49, 1.82] | 0.10 | -0.28 | 41573 / -32469 / -21101 | n n n n |
| C|time_1m|VIDYA_89_hl2|tol5|BBEST | 2.14 [-1.16, 6.38] | 27 | -4.49 | -2.54 [-7.16, -0.02] | 0.01 | 0.30 | 45606 / -37222 / -14517 | n Y n n |
| C|time_15s|VIDYA_200_close|tol2|BBEST | 2.14 [0.12, 4.82] | 42 | -2.10 | -0.14 [-2.78, 2.77] | 0.52 | 0.35 | 32499 / -14066 / -13468 | n Y n n |
| C|time_30s|EMA_377_close|tol5|BBEST | 2.20 [-0.17, 4.72] | 39 | -4.34 | -2.30 [-6.48, 0.13] | 0.01 | 0.14 | 41410 / -38823 / -19927 | n Y n n |
| C|time_30s|VIDYA_100_close|tol2|BBEST | 2.04 [-0.78, 4.98] | 33 | -3.69 | -1.67 [-5.84, 1.70] | 0.08 | 0.08 | 38516 / -27600 / -19064 | n Y n n |
| C|time_1m|TMA_100_close|tol5|BBEST | 2.07 [0.11, 4.29] | 37 | -5.20 | -3.21 [-6.22, -0.71] | 0.00 | -0.11 | 17061 / -16641 / -22428 | n n n n |
| C|time_1m|VIDYA_20_hl2|tol2|BBEST | 2.10 [-0.02, 4.01] | 60 | -0.95 | 1.00 [-1.54, 4.44] | 0.74 | 0.30 | 33590 / -19351 / -5718 | n Y n n |
| C|time_1m|ALMA_100_hl2|tol5|BBEST | 2.10 [0.64, 3.77] | 76 | -3.45 | -1.48 [-3.30, 2.19] | 0.05 | 1.16 | 38385 / -40347 / -25050 | n Y n n |
| C|time_1m|KAMA_233_hl2|tol5|BBEST | 2.05 [-1.28, 5.24] | 32 | -3.96 | -1.93 [-5.41, 1.62] | 0.05 | -0.65 | 22530 / -22249 / -13891 | n n n n |
| C|tick_1000|EMA_100_close|tol5|BBEST | 2.02 [-0.48, 4.26] | 46 | -1.65 | 0.33 [-3.17, 3.76] | 0.63 | 0.15 | 38226 / -23701 / -12418 | n Y n n |
| C|time_30s|EMA_377_close|tol2|BBEST | 1.90 [-0.56, 4.64] | 27 | -4.26 | -2.34 [-7.31, 0.89] | 0.03 | 0.77 | 27249 / -24419 / -13855 | n Y n n |
| C|time_1m|SMMA_34_close|tol2|BBEST | 1.93 [-0.38, 4.49] | 41 | 1.97 | 3.96 [1.06, 9.78] | 1.00 | -0.75 | 5757 / 13599 / 3864 | Y n n Y |
| C|time_1m|WMA_55_close|tol5|BBEST | 1.98 [0.63, 3.39] | 80 | -4.27 | -2.26 [-4.34, 1.19] | 0.00 | 1.09 | 34917 / -48520 / -35822 | n Y n n |
| C|time_1m|KAMA_50_hl2|tol2|BBEST | 1.90 [-0.41, 4.03] | 66 | -0.97 | 0.99 [-1.63, 4.16] | 0.73 | 0.79 | 3873 / -6872 / -3308 | n Y n n |
| C|time_1m|KAMA_89_hl2|tol2|BBEST | 1.81 [-0.37, 4.04] | 46 | -1.71 | 0.31 [-3.61, 5.40] | 0.62 | 2.73 | 29926 / -19293 / -11613 | n Y n n |
| C|time_30s|VIDYA_144_close|tol5|BBEST | 1.88 [-0.94, 5.11] | 43 | -3.12 | -1.06 [-4.52, 1.24] | 0.20 | 0.01 | 32402 / -37156 / -15681 | n Y n n |
| C|time_30s|SMA_233_close|tol2|BBEST | 1.81 [-0.66, 3.93] | 28 | -4.72 | -2.71 [-7.06, 2.35] | 0.00 | -0.36 | 11025 / -22474 / -6747 | n n n n |
| C|time_3m|T3_233_close|tol5|R1 | 1.77 [0.60, 3.05] | 137 | -3.71 | -0.91 [-2.67, 0.85] | 0.12 | -0.39 | 55303 / -162587 / 963 | n n n n |
| C|time_1m|WMA_233_close|tol5|BBEST | 1.74 [-1.16, 5.02] | 30 | -2.91 | -0.84 [-4.15, 1.48] | 0.28 | -1.56 | 33438 / -33383 / -9757 | n n n n |
| C|time_30s|TMA_233_close|tol5|BBEST | 1.77 [-0.28, 3.95] | 48 | -4.78 | -2.77 [-6.75, -0.96] | 0.00 | -0.05 | 19967 / -35345 / -22066 | n n n n |
| C|time_30s|T3_233_close|tol5|BBEST | 1.69 [0.26, 3.33] | 25 | -3.67 | -1.57 [-4.88, 2.40] | 0.09 | 0.88 | 16451 / -16201 / -8772 | n Y n n |
| C|time_3m|TMA_377_close|tol5|R1 | 1.43 [0.30, 2.52] | 191 | -3.70 | -0.89 [-2.32, 0.38] | 0.11 | 0.27 | -27570 / -135256 / -21400 | n Y n n |
| C|time_3m|TMA_377_close|tol2|R1 | 1.36 [-0.06, 2.74] | 149 | -3.55 | -0.78 [-2.38, 0.46] | 0.17 | 0.57 | -18510 / -93106 / -18328 | n Y n n |
| C|time_3m|SMMA_377_close|tol2|R1 | 1.37 [-0.18, 2.94] | 119 | -3.57 | -0.85 [-4.39, 2.21] | 0.23 | 0.27 | 2128 / -113016 / -12569 | n Y n n |
| C|time_3m|TMA_34_close|tol2|R1 | 1.26 [0.37, 2.21] | 273 | -4.19 | -1.36 [-2.91, 0.31] | 0.00 | -0.51 | 16206 / -321150 / -24324 | n n n n |
| C|time_2m|T3_377_close|tol2|R1 | 1.14 [-0.37, 2.76] | 127 | -3.12 | -0.34 [-2.27, 1.64] | 0.35 | -0.52 | 13278 / -138032 / -11818 | n n n n |
| C|time_3m|ZLEMA_233_close|tol2|R1 | 1.18 [0.17, 2.13] | 219 | -1.19 | 1.62 [0.10, 3.21] | 0.99 | -0.49 | 31260 / -170641 / -8324 | Y n n n |
| C|time_3m|VIDYA_377_hl2|tol2|R1 | 1.04 [-0.63, 2.79] | 72 | 0.29 | 2.94 [-1.01, 6.93] | 0.98 | 0.28 | -15585 / -37334 / -5557 | n Y n n |
| C|time_3m|LSMA_233_close|tol2|R1 | 1.03 [0.01, 2.11] | 234 | -2.10 | 0.70 [-1.04, 2.42] | 0.85 | -0.47 | -66902 / -138239 / -5138 | n n n n |

## 5. By window (PRE, first 10 of the holdout list; flat 15:55), by year, long / short, mirror
| cell | 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | PRIMARY 10-14 | 14:00-15:30 | RTH pooled |
|---|---|---|---|---|---|---|---|---|
| C|time_1m|VIDYA_50_close|tol5|BBEST | 0.64 vs -2.32 (n 13; CI -6.0..12.1) | 4.47 vs -2.34 (n 32; CI 1.6..12.7) | -0.97 vs -2.02 (n 30; CI -3.3..6.5) | 3.18 vs -0.99 (n 26; CI -1.6..10.1) | 0.74 vs -0.50 (n 21; CI -3.8..7.6) | 1.95 vs -1.48 (n 109; CI 0.9..6.6) | -0.10 vs -2.25 (n 39; CI -1.4..5.4) | 1.17 vs -1.73 (n 170; CI 0.8..5.1) |
| C|time_30s|SMMA_144_close|tol2|BBEST | 0.47 vs -2.32 (n 18; CI -5.0..13.0) | 3.24 vs -2.34 (n 41; CI -0.2..10.5) | -0.60 vs -2.02 (n 27; CI -4.1..6.5) | 0.63 vs -0.99 (n 24; CI -4.8..7.6) | 1.10 vs -0.50 (n 17; CI -4.9..9.0) | 1.38 vs -1.48 (n 109; CI 0.2..5.7) | 2.72 vs -2.25 (n 35; CI 1.6..9.0) | 1.60 vs -1.73 (n 172; CI 1.4..5.3) |
| C|time_1m|EMA_200_close|tol5|BBEST | -4.93 vs -2.32 (n 12; CI -9.6..3.4) | 0.18 vs -2.34 (n 34; CI -1.7..9.7) | -0.16 vs -2.02 (n 35; CI -2.7..8.7) | 3.01 vs -0.99 (n 25; CI 1.0..7.1) | 4.96 vs -0.50 (n 16; CI -0.7..14.1) | 1.56 vs -1.48 (n 109; CI 0.2..6.6) | 1.73 vs -2.25 (n 25; CI 0.2..8.3) | 1.24 vs -1.73 (n 158; CI 0.6..5.3) |
| C|time_1m|SMA_144_close|tol5|BBEST | 1.75 vs -2.32 (n 16; CI -3.8..12.4) | 0.21 vs -2.34 (n 34; CI -2.1..7.5) | 0.20 vs -2.02 (n 30; CI -1.9..6.0) | 1.84 vs -0.99 (n 32; CI -0.8..6.8) | 1.90 vs -0.50 (n 20; CI -4.1..12.2) | 0.95 vs -1.48 (n 116; CI 0.1..5.1) | 0.26 vs -2.25 (n 31; CI -1.7..7.9) | 1.04 vs -1.73 (n 170; CI 0.8..5.0) |
| C|time_1m|KAMA_200_close|tol5|BBEST | -4.70 vs -2.32 (n 21; CI -7.4..2.9) | 2.26 vs -2.34 (n 45; CI 0.1..9.4) | 0.80 vs -2.02 (n 32; CI -1.3..5.7) | 2.58 vs -0.99 (n 20; CI -2.2..8.8) | -1.87 vs -0.50 (n 24; CI -6.0..5.0) | 0.87 vs -1.48 (n 118; CI -0.2..5.2) | 0.37 vs -2.25 (n 38; CI -1.6..7.0) | 0.36 vs -1.73 (n 190; CI 0.0..4.2) |
| C|time_1m|SMMA_89_close|tol5|BBEST | -0.66 vs -2.32 (n 14; CI -6.7..12.0) | -0.75 vs -2.34 (n 38; CI -5.4..10.2) | -0.86 vs -2.02 (n 40; CI -2.4..6.4) | 4.52 vs -0.99 (n 30; CI 2.3..9.6) | 5.05 vs -0.50 (n 14; CI -2.6..16.0) | 1.17 vs -1.48 (n 122; CI -0.5..6.6) | 2.56 vs -2.25 (n 31; CI 1.9..8.6) | 1.49 vs -1.73 (n 177; CI 0.6..6.0) |
| C|time_3m|T3_233_close|tol2|R1 | -2.99 vs -2.21 (n 80; CI -3.4..2.0) | 0.58 vs -1.90 (n 123; CI 0.1..5.0) | 2.23 vs -1.65 (n 84; CI 1.3..7.0) | -0.36 vs -1.48 (n 81; CI -2.5..5.7) | -0.97 vs -2.17 (n 65; CI -2.2..4.9) | 0.52 vs -1.80 (n 352; CI 0.9..3.9) | 0.19 vs -1.61 (n 78; CI -1.4..5.8) | -0.24 vs -1.83 (n 532; CI 0.5..2.7) |
| C|time_1m|KAMA_377_hl2|tol5|BBEST | -1.13 vs -2.32 (n 13; CI -7.8..10.4) | 0.85 vs -2.34 (n 36; CI -2.4..9.2) | -0.68 vs -2.02 (n 27; CI -2.7..5.5) | 2.49 vs -0.99 (n 34; CI -0.5..6.8) | 0.97 vs -0.50 (n 23; CI -2.6..7.0) | 0.83 vs -1.48 (n 115; CI -0.1..4.6) | -1.26 vs -2.25 (n 26; CI -3.1..5.4) | 0.59 vs -1.73 (n 156; CI 0.4..4.3) |
| C|time_30s|WMA_377_close|tol2|BBEST | 1.11 vs -2.32 (n 20; CI -3.8..10.8) | 2.46 vs -2.34 (n 32; CI -0.3..10.0) | -0.64 vs -2.02 (n 29; CI -3.0..6.1) | -2.29 vs -0.99 (n 23; CI -6.5..6.3) | 3.11 vs -0.50 (n 25; CI -1.8..10.9) | 0.65 vs -1.48 (n 107; CI -0.2..4.9) | -0.94 vs -2.25 (n 34; CI -1.9..6.7) | 0.59 vs -1.73 (n 172; CI 0.4..4.4) |
| C|time_1m|ALMA_100_hl2|tol2|BBEST | 2.27 vs -2.32 (n 21; CI -0.5..9.2) | 5.16 vs -2.34 (n 32; CI 4.2..11.5) | -1.16 vs -2.02 (n 32; CI -2.6..4.1) | -2.85 vs -0.99 (n 40; CI -5.6..1.9) | 2.55 vs -0.50 (n 30; CI -2.0..7.2) | 0.67 vs -1.48 (n 134; CI 0.2..4.0) | -3.26 vs -2.25 (n 46; CI -4.6..3.0) | -0.22 vs -1.73 (n 218; CI -0.1..3.0) |

| cell | 2024 | 2025H1 | long | short | mirror |
|---|---|---|---|---|---|
| C|time_1m|VIDYA_50_close|tol5|BBEST | net 3.86 eff 4.02 (n 67) | net -0.94 eff 3.45 (n 42) | net 0.98 eff 2.93 (n 47) | net 2.79 eff 3.50 (n 62) | net -2.63 eff -1.32 (n 107) |
| C|time_30s|SMMA_144_close|tol2|BBEST | net 4.16 eff 4.32 (n 67) | net -2.59 eff 1.80 (n 42) | net 0.10 eff 2.05 (n 49) | net 2.18 eff 2.88 (n 62) | net -2.52 eff -1.21 (n 106) |
| C|time_1m|EMA_200_close|tol5|BBEST | net 4.28 eff 4.44 (n 68) | net -3.09 eff 1.30 (n 41) | net -0.12 eff 1.83 (n 50) | net 2.85 eff 3.56 (n 60) | net -1.56 eff -0.24 (n 112) |
| C|time_1m|SMA_144_close|tol5|BBEST | net 1.86 eff 2.03 (n 76) | net -0.27 eff 4.13 (n 40) | net 1.15 eff 3.10 (n 51) | net 1.11 eff 1.82 (n 65) | net -1.57 eff -0.25 (n 110) |
| C|time_1m|KAMA_200_close|tol5|BBEST | net 1.37 eff 1.53 (n 70) | net 0.58 eff 4.97 (n 48) | net 0.17 eff 2.12 (n 51) | net 1.26 eff 1.96 (n 70) | net -1.15 eff 0.16 (n 133) |
| C|time_1m|SMMA_89_close|tol5|BBEST | net 4.22 eff 4.38 (n 72) | net -3.76 eff 0.63 (n 50) | net -1.03 eff 0.92 (n 55) | net 2.57 eff 3.28 (n 67) | net -1.57 eff -0.26 (n 113) |
| C|time_3m|T3_233_close|tol2|R1 | net 1.07 eff 2.24 (n 242) | net -0.70 eff 2.16 (n 110) | net -0.33 eff 1.50 (n 197) | net 1.60 eff 3.38 (n 155) | net -1.76 eff -0.20 (n 403) |
| C|time_1m|KAMA_377_hl2|tol5|BBEST | net 1.92 eff 2.08 (n 78) | net -1.22 eff 3.17 (n 37) | net 0.46 eff 2.41 (n 50) | net 1.26 eff 1.97 (n 65) | net -0.40 eff 0.92 (n 116) |
| C|time_30s|WMA_377_close|tol2|BBEST | net 1.45 eff 1.62 (n 70) | net -0.54 eff 3.85 (n 37) | net -0.47 eff 1.49 (n 49) | net 1.27 eff 1.98 (n 62) | net -3.06 eff -1.74 (n 98) |
| C|time_1m|ALMA_100_hl2|tol2|BBEST | net 2.09 eff 2.25 (n 84) | net -1.49 eff 2.90 (n 50) | net 0.57 eff 2.52 (n 86) | net 1.18 eff 1.89 (n 49) | net -3.03 eff -1.71 (n 167) |

Full tables: out/zen/lines/C_extra.json.

## 6. Heat table: line type x lookback, close price, 1-min entry, tol 2, regime 5m EMA200 (effect vs random-in-regime)
| type \ lookback | 9 | 20 | 21 | 34 | 50 | 55 | 89 | 100 | 144 | 200 | 233 | 377 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALMA |  |  |  |  |  |  |  |  |  | -0.1 | -0.3 | 0.3 |
| DEMA | -0.2 | -0.3 |  | -0.2 | -0.3 |  | -0.1 | -0.3 | -0.3 | 0.3 | 0.2 | -0.3 |
| EMA |  | -0.1 |  | 0.1 | -0.7 |  | -0.4 | -0.2 | 0.2 | -0.2 | 0.1 | 0.3 |
| FAMA |  |  |  |  |  |  |  |  |  |  |  |  |
| FRAMA | 0.1 | -0.3 |  | 0.1 | -0.1 |  | 0.1 |  | -0.1 | -0.0 | -0.3 | -0.0 |
| HMA | -0.2 | -0.3 |  | -0.3 | -0.4 |  | -0.5 | -0.4 | -0.1 | -0.3 | -0.3 | -0.4 |
| KAMA | 0.1 | -0.2 |  | 0.2 | -0.0 |  | -0.4 |  | 0.2 | -0.2 | -0.0 | -0.3 |
| LSMA |  | -0.3 |  | -0.2 | -0.1 | -0.0 | 0.1 | -0.3 | -0.4 | -0.4 | -0.7 | -0.4 |
| MAMA |  |  |  |  |  |  |  |  |  |  |  |  |
| SMA | 0.0 | -0.3 |  | 0.4 | 0.1 |  | -0.5 | -0.9 | 0.3 | 0.1 | 0.1 | 0.1 |
| SMMA |  |  | -0.1 | 0.0 |  |  | 0.1 |  | -0.5 |  | 0.5 | 0.1 |
| T3 | -0.2 | -0.6 |  | -0.3 | -0.5 | -0.1 | -0.3 | -0.5 | -0.2 | -0.6 | -1.0 | -0.2 |
| TEMA |  | -0.2 |  |  | -0.3 |  | -0.6 | -0.4 | -0.1 | -0.8 | -0.3 | 0.5 |
| TMA |  |  |  | -0.1 | 0.0 | 0.1 | -0.1 | -0.1 | -0.2 | -0.5 | -0.2 | 0.0 |
| VIDYA | 0.1 | -0.1 |  | -0.0 | -0.2 | -0.3 | -0.5 | 0.2 | 0.1 | 0.3 | -0.1 | -0.1 |
| VWMA |  |  |  |  |  |  | -0.6 | -1.0 | -0.5 | -0.1 | 0.0 | -0.6 |
| WMA | -0.1 | -0.1 |  | -0.4 |  | 0.0 | -0.3 | -0.1 | -0.5 | 0.3 | 0.3 | 0.3 |
| ZLEMA |  |  |  | -0.3 | -0.0 |  | -0.5 | 0.1 | -0.4 | -0.3 | -0.3 | -0.4 |

3-minute lines:

| type \ lookback | 9 | 20 | 34 | 50 | 55 | 89 | 100 | 144 | 200 | 233 | 377 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALMA | -0.1 |  |  |  |  | -0.0 | 0.0 | 0.6 | 0.0 | 0.3 | -0.5 |
| DEMA | -0.2 | -0.5 | 0.0 | 0.1 | -0.2 | 0.2 | -0.5 | -0.5 | 0.2 | 0.2 | 0.3 |
| EMA | 0.3 | -0.1 | -0.2 | 0.5 | 0.5 | 0.3 | 0.4 | -0.1 | 0.5 | 0.2 | -0.2 |
| FAMA |  |  |  |  |  |  |  |  |  |  |  |
| FRAMA | 0.1 | -0.2 | -0.1 | -0.1 | -0.2 | -0.4 | -0.2 | 0.1 | 0.1 | -0.0 | 0.1 |
| HMA | -0.3 | -0.4 | -0.1 | -0.4 | -0.7 | -0.7 | -0.5 | 0.6 | 0.5 | 0.4 | -0.4 |
| ITREND |  |  |  |  |  |  |  |  |  |  |  |
| KAMA | 0.4 | 0.2 | 0.3 | 0.2 |  | -0.7 | 0.1 | 0.3 | 0.2 | 0.9 | 0.6 |
| LSMA | 0.0 | -0.0 | 0.2 | -0.5 | -0.5 | -0.7 | -0.5 | 0.3 | -0.4 | 1.0 | 0.6 |
| MAMA |  |  |  |  |  |  |  |  |  |  |  |
| MCG |  | -0.1 |  |  |  |  | 0.4 |  |  |  |  |
| SMA | -0.2 | -0.0 | 0.6 | 0.6 | 0.3 | 0.4 | 0.3 | -0.3 | -0.1 | -0.3 | 0.7 |
| SMMA | -0.4 | -0.2 | 0.1 |  | 0.5 | 0.3 |  | 0.5 | -0.1 | 0.1 | 1.3 |
| T3 | -0.2 | 0.1 | -0.2 | 0.4 | 0.7 | -0.6 | -0.3 | -0.8 | 0.2 | 2.3 | -0.7 |
| TEMA | -0.1 | -0.5 | -0.5 | -0.3 | -0.2 | -0.5 | -0.4 | -0.4 | -0.2 | -0.1 | -0.4 |
| TMA |  | -0.5 | 1.2 | 0.4 | 0.2 | 0.5 | -0.4 | -0.3 | 0.0 | 0.7 | 1.4 |
| VIDYA | 0.0 | -0.0 | -0.2 | -0.2 | -1.0 | 0.6 | 0.2 | -1.1 | -0.7 | 0.5 | 0.9 |
| VWMA |  |  | -0.8 | -0.1 |  | -0.2 |  | 0.3 | -0.2 |  | 0.0 |
| WMA | -0.2 | -0.3 | 0.4 | -0.1 | -0.2 | 0.3 | 0.4 | 0.6 | -0.2 | -0.2 | 0.8 |
| ZLEMA |  | -0.2 | 0.0 | -0.5 | 0.3 | 0.3 | -0.0 | 0.4 | 0.2 | 1.1 | 0.2 |

## 7. Realised stop and R:R
Stop 15.0 pt; target distance medians in the top cells 11.2, 10.2, 9.8, 8.8, 10.8, 9.5, 10.5, 9.2, 10.0, 8.5 pt (R:R 0.5-0.9).

## Deviations and disclosures
- Screen is on the mapped conservative basis (1-min OHLC fills; 0.05-0.13 pts/trade more conservative than 1-s on tight stops). **G10 (direct 1-s/L2 replay) was NOT run** by this agent (needs a replay worker allow-listed in the governor; request in MORNING.md). No cell can therefore be labelled CANDIDATE; the best possible label is 'screen G1-G9 pass, G10 pending'; none reached it.
- Bracket (fixed for all LINES blocks): 15-pt stop measured from the entry price (the realised stop is exactly 15.0 pt for every trade: median = p90 = 15), target = nearest confirmed 1-min swing (k=2, last 12 swings) beyond the entry at distance 5..60 pt; entries with no such target do not exist (about 48% of bar x side rows, same rule in every placebo pool). Median realised target distance and R:R are in the tables (R:R = target distance / 15, about 0.7).
- All trades come from `Z.simulate()` (table built once per entry bar x side; identity to a fresh `simulate()` on 300 random events is a unit test). `zen_struct.grid_eval` is NOT used, so the fill_mode=1 grid bug reported by D3ZF1 does not apply (market entries only).
- The one-open-trade rule is applied to each real set; the grid placebo is the exact pool expectation (unsequenced); the top cells are re-run with `Z.placebo_in_regime` / `placebo_random_dir` (100 draws) and agree with the pool expectation to within 0.1 pt in all spot checks (C_top_pre.json).
- Gate G1 rank: in the grid the rank gate is replaced by the week-block bootstrap (CI lower > 0); the full-draw rank is reported for the top cells. G2 likewise.
- By-window tables use a separate engine with entries 09:30-15:55 and flat 15:55 (so the PRIMARY row there is the 15:55-flat variant); the screen itself is flat 14:00 only (plan table). Flat-15:55 and window re-reads are counted as disclosed additions to N.
- Holdout looks used: ONE look (HOLD) + ONE X read for this block, logged in out/zen/lines/looks.jsonl and DECISIONS.md BEFORE HOLD/X were read. The 2023 X span is in memory during the screen for line warm-up but is not scored.
- Selection effects: cells chosen on PRE effect (top 30 per prereg rule); the winner's-curse is visible: PRE effects of the selected cells average +1.3 (B), +2.0 (C) pt/trade and fall to +0.5 (B), -1.2 (C) in HOLD.
- Closed-bar rule: `out/zen/lines/zl_test.log`, 24 tests, 0 failures (events, regimes, entry lines, stacks unchanged when all later bars are deleted).
- Files: code l2vast/ds3/code/zen/lines/*.py; outputs l2vast/ds3/out/zen/lines/ ; prereg l2vast/ds3/prereg/ZEN_LINES_{B,C,D}_prereg.md(+.sha256).
- 38 cells (30 + 8 R1 not already in the 30) went to the holdout look instead of 30 (disclosed in the pre-holdout text) so that the EMA200-regime results also face HOLD.

DONE LINES_C
