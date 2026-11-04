# DS3_P3_EXEC - execution realism (program P3, Z2, 2026-11-04). Shadow only, research only, no PASS claims.

Prereg: l2vast/ds3/prereg/P3_EXEC_prereg.md sha256 9a8790c0c1f051623d5ca0716944e72fca4157fb3305954e5488f0e1dbe91e07 (+ addendum in DECISIONS.md: fades also at 2 lots, paired-row rule). dead_lookup before: NOT FOUND. Ledger after: 144 cells, program P3_EXEC. P3_NTESTED: 144 simulated cells, no hypothesis tests.
Code: l2vast/ds3/code/p3/ (p3_run.py sims, p3_an.py weekly cost + bootstrap, p3_dec.py decomposition, p3_sum.py tables, p3_append.py ledger). Results: /mnt/l2/l2vast/ds3_zones3_new/Z2_p3/ (p3_sims.pkl, p3_cost_table.csv, p3_decomp.csv, p3_native_gain.csv, p3_tables.md).

## Headline (read this first)
1. The latency cost of entering 1 s after the bar close and slicing 1 lot / 2 s is SMALL and NOT significantly different from zero for 14 of 18 book lines at the path-close level (entry latency): entry-adverse move +1 s is within +-$90/wk at live lots, the S=2 slice drift within +-$60/wk (Table 2). Entry-latency CIs excluding zero: L_KB (-78 [-162,-9], the 1-s delay helps), F1/F2_ORBF (helps), F1_PD (+10 [3,18], hurts); slice drift excluding zero: F2_ORBF (+42), F2_PD (+59).
2. The total paired difference live-minus-idealised ($/wk, Table 1) is dominated by bracket re-anchoring noise (stop and target are re-anchored on the shifted first fill, so some trades flip outcome): L_PE -766 [-1689,+399], L6M -3390 [-6595,+974]; same signal rows, same costs. It changes sign with L (Table 4: L_PE L=0 -172, L=1 -766, L=2 -33, L=3 +7). Treat it as an uncertainty band of the idealised engine P&L, not a cost. Significant totals only: L_SM L6M/HOLD (live earns MORE, -577 / -397), L_PB (+65 [13,144] ALL), F1_OR15 L6M (+368), F2_PD ALL (+89), F2_OR15 L6M/HOLD; none is a robust cost across windows.
3. The one mechanical lever is the stop-fill: native stop-market (1.28 pt, n=8) instead of join-then-market (2.45 pt, n=21) is worth +$1,711/wk on L_PE [1,429, 2,004], +531 L_KB, +325 L_HM, +256 L_MV, +208 L_SM, +66 L_PB (sum of the six live books +$3,097/wk) at the full-history live lots (CIs are on the path bootstrap only; the 1.17 pt difference itself rests on 8 vs 21 stops of FORWARD_STOP_AB and is the dominant uncertainty).
4. The idealised library already charges the join-style 2.45 pt per stop (LIVE basis), so the numbers above are not a double count of stop cost; against the older library basis M (1.01 pt stop) the extra stop cost would add roughly (2.45-1.01)/(2.45-1.28) = 1.2x the native-gain figure per stop (not simulated here).
5. Most latency-sensitive (Table 6, by the stop-fill lever, then the latency spread): L_PE (spread of total over L 0..3 $773/wk; native gain 1,711), then L_KB, L_HM, L_MV, L_SM; fades are 1-2 orders smaller (F2 lines $50-150/wk), F2_ORBF and F2_PD have the largest deterministic entry+slice drift among fades ($109, $83/wk).

## Method
Same signal rows in every scenario (rows kept by the library no-overlap simulation; so differences are paired). Live books: plain-bracket proxy of ts2 library rows (signal second = D._d().sin, 60/60 pt brackets, live Q1-A ts2 lots; excludes the 70/30 split, PE tape confirmation, locks, zone skips; PB keeps 1,171 of 5,403 rows because a plain bracket without the live PB logic overlaps itself, so PB numbers are indicative only). Fades: FADE_XI NQ trade lists (Z1 variant), 1 lot (F1) and the list's native 2 lots (F2), time stop 3,600 s. Library = entry at path close of the signal second, stop 2.45 / market 0.80, fee 0.242 pt/lot, no slicing. Live = first fill at path close of second B+L, slice i at +S*i s, stop/target resting on the first fill, same costs; `_sim_nq_live` from multi_harness. CI = 4-week moving-block bootstrap, 2,000 draws, seed 20261104, over 187 weeks (ALL, 2023-04-03..2026-10-30), 27 (L6M), 52 (HOLD).
Sanity: L=0 with 1 lot reproduces the library exactly (all F1 lines, difference 0.0).

### Table 1. Cost of the live model vs the idealised engine, $/week at live lots (positive = live earns less); 95% 4-wk block bootstrap CI

| book | n trades | lib $/wk ALL | cost ALL | cost L6M | cost HOLD | cost pt/lot ALL |
|---|---|---|---|---|---|---|
| L_KB | 7909 | 556 | +119 [-116, +355] | +41 [-517, +759] | +94 [-389, +688] | +0.12 |
| L_PE | 6035 | 3499 | -766 [-1689, +399] | -3390 [-6595, +974] | -2006 [-3672, +1052] | -0.25 |
| L_SM | 1368 | 1296 | -178 [-511, +120] | -577 [-1283, -82] | -397 [-807, -102] | -0.45 |
| L_HM | 3266 | 1989 | +169 [-65, +465] | -254 [-658, +273] | -135 [-490, +194] | +0.28 |
| L_MV | 3636 | 182 | -123 [-271, +19] | -159 [-678, +365] | -277 [-595, +204] | -0.27 |
| L_PB | 1171 | 585 | +65 [+13, +144] | +272 [+0, +726] | +188 [-0, +471] | +0.52 |
| F1_ONRTH | 537 | 144 | -50 [-117, +6] | -182 [-454, +0] | -188 [-378, -46] | -0.86 |
| F2_ONRTH | 537 | 288 | -101 [-230, +22] | -362 [-946, +47] | -378 [-769, -74] | -0.88 |
| F1_VWAPF | 1444 | 313 | -6 [-139, +121] | +275 [-278, +836] | +47 [-289, +385] | -0.04 |
| F2_VWAPF | 1444 | 626 | -15 [-270, +246] | +437 [-785, +1841] | +52 [-580, +824] | -0.05 |
| F1_ORBF | 905 | -334 | -66 [-223, +75] | +155 [-269, +670] | -62 [-379, +288] | -0.68 |
| F2_ORBF | 905 | -669 | -92 [-371, +181] | +369 [-371, +1467] | -69 [-652, +569] | -0.47 |
| F1_VB2 | 522 | 84 | -2 [-38, +41] | -39 [-134, +34] | -36 [-124, +37] | -0.03 |
| F2_VB2 | 522 | 147 | -81 [-250, +85] | -237 [-749, +177] | -156 [-598, +197] | -0.23 |
| F1_OR15 | 953 | 40 | +50 [-67, +185] | +368 [+54, +943] | +223 [-21, +576] | +0.49 |
| F2_OR15 | 953 | -22 | +112 [-84, +324] | +408 [+88, +1008] | +337 [+39, +722] | +0.42 |
| F1_PD | 659 | -12 | +14 [-0, +31] | -8 [-65, +31] | +2 [-30, +28] | +0.19 |
| F2_PD | 659 | -407 | +89 [+30, +156] | +51 [-73, +156] | +56 [-39, +150] | +0.26 |

### Table 2. Components ALL window ($/wk adverse = cost; CI): entry latency +1 s, slice drift (S=2), native stop-market gain (negative cost), residual bracket re-anchoring

| book | lat +1 s | slice S=2 | native stop gain | total (L1,S2,join) | residual = total - lat1 - slc2 |
|---|---|---|---|---|---|
| L_KB | -78 [-162, -9] | -9 [-32, +15] | +531 [+437, +618] | +119 [-116, +355] | +207 |
| L_PE | -90 [-246, +84] | -39 [-310, +243] | +1711 [+1429, +2004] | -766 [-1689, +399] | -637 |
| L_SM | +32 [-2, +68] | +24 [-19, +75] | +208 [+183, +233] | -178 [-511, +120] | -233 |
| L_HM | -24 [-66, +13] | -20 [-52, +16] | +325 [+279, +371] | +169 [-65, +465] | +213 |
| L_MV | -20 [-61, +15] | -3 [-14, +7] | +256 [+216, +294] | -123 [-271, +19] | -100 |
| L_PB | +1 [-8, +9] | +0 [+0, +0] | +66 [+53, +78] | +65 [+13, +144] | +64 |
| F1_ONRTH | -3 [-17, +12] | +0 [+0, +0] | +25 [+22, +28] | -50 [-117, +6] | -47 |
| F2_ONRTH | -5 [-35, +24] | -1 [-21, +20] | +50 [+44, +56] | -101 [-230, +22] | -94 |
| F1_VWAPF | +12 [-11, +37] | +0 [+0, +0] | +74 [+65, +86] | -6 [-139, +121] | -18 |
| F2_VWAPF | +25 [-26, +77] | -2 [-42, +34] | +149 [+129, +173] | -15 [-270, +246] | -37 |
| F1_ORBF | -34 [-58, -10] | +0 [+0, +0] | +52 [+48, +56] | -66 [-223, +75] | -32 |
| F2_ORBF | -67 [-113, -21] | +42 [+7, +75] | +103 [+96, +113] | -92 [-371, +181] | -66 |
| F1_VB2 | +2 [-6, +10] | +0 [+0, +0] | +18 [+15, +21] | -2 [-38, +41] | -4 |
| F2_VB2 | +6 [-21, +37] | -11 [-67, +50] | +120 [+93, +146] | -81 [-250, +85] | -76 |
| F1_OR15 | +5 [-11, +22] | +0 [+0, +0] | +39 [+35, +43] | +50 [-67, +185] | +44 |
| F2_OR15 | +14 [-16, +43] | +22 [-6, +52] | +107 [+91, +124] | +112 [-84, +324] | +75 |
| F1_PD | +10 [+3, +18] | +0 [+0, +0] | +10 [+8, +13] | +14 [-0, +31] | +4 |
| F2_PD | +24 [-7, +57] | +59 [+24, +94] | +56 [+42, +72] | +89 [+30, +156] | +7 |

### Table 3. Slice-schedule sensitivity (L=1 s, join stop): total cost $/wk ALL window and slice drift component

| book | total S=1 | total S=2 | total S=4 | drift S=1 | drift S=2 | drift S=4 |
|---|---|---|---|---|---|---|
| L_KB | +122 | +119 | +99 | -7 | -9 | -31 |
| L_PE | -731 | -766 | -842 | -43 | -39 | -102 |
| L_SM | -180 | -178 | -193 | +20 | +24 | +8 |
| L_HM | +172 | +169 | +162 | -15 | -20 | -16 |
| L_MV | -123 | -123 | -128 | -3 | -3 | -11 |
| L_PB | +65 | +65 | +65 | +0 | +0 | +0 |
| F1_ONRTH | -50 | -50 | -50 | +0 | +0 | +0 |
| F2_ONRTH | -93 | -101 | -91 | +6 | -1 | +8 |
| F1_VWAPF | -6 | -6 | -6 | +0 | +0 | +0 |
| F2_VWAPF | -22 | -15 | -24 | -10 | -2 | -12 |
| F1_ORBF | -66 | -66 | -66 | +0 | +0 | +0 |
| F2_ORBF | -108 | -92 | -79 | +25 | +42 | +47 |
| F1_VB2 | -2 | -2 | -2 | +0 | +0 | +0 |
| F2_VB2 | -70 | -81 | -45 | -6 | -11 | +27 |
| F1_OR15 | +50 | +50 | +50 | +0 | +0 | +0 |
| F2_OR15 | +110 | +112 | +118 | +19 | +22 | +29 |
| F1_PD | +14 | +14 | +14 | +0 | +0 | +0 |
| F2_PD | +82 | +89 | +106 | +47 | +59 | +73 |

### Table 4. Latency sweep, total cost $/wk ALL (S=2, join): L=0,1,2,3 s

| book | L=0 | L=1 | L=2 | L=3 | spread (max-min) | entry-adverse pt/lot at +1/+2/+3 s |
|---|---|---|---|---|---|---|
| L_KB | -21 | +119 | -112 | +29 | 231 | -0.080 / -0.153 / -0.156 |
| L_PE | -172 | -766 | -33 | +7 | 773 | -0.029 / -0.036 / -0.019 |
| L_SM | +37 | -178 | -55 | -54 | 215 | +0.080 / +0.126 / +0.189 |
| L_HM | -21 | +169 | +111 | -100 | 270 | -0.040 / -0.064 / -0.091 |
| L_MV | -7 | -123 | -16 | -137 | 130 | -0.044 / -0.069 / -0.078 |
| L_PB | +0 | +65 | +26 | +72 | 72 | +0.011 / +0.067 / +0.057 |
| F1_ONRTH | +0 | -50 | -49 | -27 | 50 | -0.047 / +0.055 / -0.068 |
| F2_ONRTH | +3 | -101 | -98 | -44 | 104 | -0.047 / +0.055 / -0.068 |
| F1_VWAPF | +0 | -6 | -57 | +14 | 71 | +0.080 / +0.017 / +0.064 |
| F2_VWAPF | +2 | -15 | -113 | +18 | 131 | +0.080 / +0.017 / +0.064 |
| F1_ORBF | +0 | -66 | -57 | +16 | 82 | -0.348 / -0.086 / +0.082 |
| F2_ORBF | -10 | -92 | -96 | +38 | 134 | -0.348 / -0.086 / +0.082 |
| F1_VB2 | +0 | -2 | +18 | +3 | 20 | +0.034 / +0.040 / +0.036 |
| F2_VB2 | -12 | -81 | +116 | +73 | 197 | +0.017 / +0.066 / +0.057 |
| F1_OR15 | +0 | +50 | +39 | +44 | 50 | +0.053 / +0.221 / +0.265 |
| F2_OR15 | +28 | +112 | +125 | +88 | 97 | +0.055 / +0.197 / +0.231 |
| F1_PD | +0 | +14 | +21 | +19 | 21 | +0.142 / +0.222 / +0.293 |
| F2_PD | +60 | +89 | +123 | +112 | 63 | +0.068 / +0.177 / +0.248 |

### Table 5. By session, L1 S2 join, cost $/wk ALL window (CI), sessions with >= 20 trades

| book | session | n | cost $/wk | lat+1s $/wk |
|---|---|---|---|---|
| L_KB | asia | 2277 | -27 [-127, +70] | -23 [-48, -2] |
| L_KB | london | 1700 | +49 [-2, +121] | -27 [-54, -6] |
| L_KB | nyam | 2318 | -92 [-225, +61] | -22 [-50, +6] |
| L_KB | nypm | 1614 | +190 [+52, +339] | -6 [-41, +25] |
| L_PE | asia | 2165 | -136 [-589, +398] | +20 [-32, +95] |
| L_PE | london | 1671 | -162 [-617, +242] | +4 [-110, +93] |
| L_PE | nyam | 2199 | -468 [-1050, +271] | -115 [-229, +6] |
| L_SM | asia | 690 | +0 [-204, +231] | +37 [+13, +61] |
| L_SM | london | 678 | -178 [-432, -2] | -5 [-27, +18] |
| L_HM | asia | 1799 | +152 [-43, +430] | -3 [-33, +25] |
| L_HM | nyam | 1467 | +17 [-93, +127] | -21 [-50, +4] |
| L_MV | london | 1578 | -95 [-186, -16] | -16 [-51, +8] |
| L_MV | nyam | 2058 | -29 [-172, +105] | -4 [-31, +25] |
| L_PB | asia | 1171 | +65 [+13, +144] | +1 [-7, +9] |
| F1_ONRTH | nyam | 537 | -50 [-119, +12] | -3 [-17, +12] |
| F2_ONRTH | nyam | 537 | -101 [-238, +26] | -5 [-33, +25] |
| F1_VWAPF | nyam | 1444 | -6 [-140, +128] | +12 [-12, +39] |
| F2_VWAPF | nyam | 1444 | -15 [-287, +239] | +25 [-24, +77] |
| F1_ORBF | nyam | 893 | -63 [-210, +82] | -34 [-57, -11] |
| F2_ORBF | nyam | 893 | -87 [-373, +192] | -68 [-115, -22] |
| F1_VB2 | nypm | 521 | -2 [-40, +44] | +2 [-6, +11] |
| F2_VB2 | nypm | 521 | -81 [-260, +91] | +6 [-20, +39] |
| F1_OR15 | nyam | 953 | +50 [-73, +179] | +5 [-10, +22] |
| F2_OR15 | nyam | 953 | +112 [-87, +321] | +14 [-15, +45] |
| F1_PD | asia | 659 | +14 [-1, +29] | +10 [+3, +18] |
| F2_PD | asia | 659 | +89 [+29, +157] | +24 [-6, +57] |

### Table 6. Sensitivity ranking (ALL window)

| rank | book | latency spread over L=0..3 ($/wk) | |lat1|+|slice S2| ($/wk) | native stop-market gain ($/wk) | native gain / lib $/wk |
|---|---|---|---|---|---|
| 1 | L_PE | 773 | 129 | +1711 | 0.49 |
| 2 | L_KB | 231 | 87 | +531 | 0.95 |
| 3 | L_HM | 270 | 44 | +325 | 0.16 |
| 4 | L_MV | 130 | 23 | +256 | 1.40 |
| 5 | L_SM | 215 | 55 | +208 | 0.16 |
| 6 | F2_VWAPF | 131 | 27 | +149 | 0.24 |
| 7 | F2_VB2 | 197 | 17 | +120 | 0.82 |
| 8 | F2_OR15 | 97 | 36 | +107 | n/a |
| 9 | F2_ORBF | 134 | 109 | +103 | -0.15 |
| 10 | F1_VWAPF | 71 | 12 | +74 | 0.24 |
| 11 | L_PB | 72 | 1 | +66 | 0.11 |
| 12 | F2_PD | 63 | 83 | +56 | -0.14 |
| 13 | F1_ORBF | 82 | 34 | +52 | -0.15 |
| 14 | F2_ONRTH | 104 | 7 | +50 | 0.17 |
| 15 | F1_OR15 | 50 | 5 | +39 | n/a |
| 16 | F1_ONRTH | 50 | 3 | +25 | 0.17 |
| 17 | F1_VB2 | 20 | 2 | +18 | 0.21 |
| 18 | F1_PD | 21 | 10 | +10 | n/a |

## Caveats (all stated, none resolved here)
- Fills are at 1-s path closes (last trade of the second): no bid/ask, no queue, no entry slippage in either model, so both ends are optimistic by the same unknown amount; the measured latency effect is the change in last-trade price, not a spread cost. Real entry slippage is a flat cost that does not differ between the two models and is not in these numbers.
- The live model scans the stop from the first-fill second itself, so a low/high printed in that second before the fill can stop the position (small pessimism, same in all L); targets are scanned from the next second.
- Re-anchoring noise is real execution risk in the other direction too: with a 1-s lag the live account will sometimes win and sometimes lose a 60-pt bracket the idealised engine decides differently.
- Weekly figures use the ts2 live lots by trade (includes the Q1-A ER half-size ladder via live_lots) but the plain-bracket proxy is not the live P&L; absolute $/wk vs the live ledger will differ.
- BT swing-flip Shadow line: a skip flag on the live books' signals, no trades of its own (forward_register/bt empty); its exposure is the exposure of the skipped trades inside the six books.
- ES/RTY not simulated (NQ 1-s G2 path only); the instr_1s paths could extend this if wanted.
- Per-session cells with < 20 trades dropped; CIs on small sessions are wide.
