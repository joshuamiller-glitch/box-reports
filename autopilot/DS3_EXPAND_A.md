# DS3_EXPAND_A - family A: the session's own early result sets the size

**VERDICT: Exact engine queue is waiting for admission (box load over the cap); the hook is built and a first-order screen of 33,227 cells picked the first 33 exact cells. No exact EA result yet.**

W-EA, T-EXPAND family A. Page built 2026-11-14 21:45 UTC. Prereg autopilot/EXPAND_A_PREREG.md (sha f0ad23f9cef5e77e). Hook code/th_expand_a/ea_hooks.py, builder mk_ea.py (cell name = rule), driver ea_driver.py, first-order screen fo_ea.py. Exact engine (TP_ENGINE=1, JN05W2, all layers ON, engine dollars = base lots, live = x1.75). Shadow only, no PASS claim.

## 0. Identity and parent

- empty-hook identity: TL3_EA_ID 202610: not run yet (waiting for admission)
- parent SM_A6_halfNP7 replicated in the hook as TL3_EA_A6 (F1 loss, K7 M7 U7 H7 A7, x0.5, never reset): not run yet

- Parent exact numbers (DS3_SMART_A2): 43 months, L6M DD cut 11.8%, d mean +383 $/wk, HOLD cut 11.6%, +724 $/wk.

## 1. What is tested

Triggers: F1 book first trade; F2 first two; SF first trade of any book (stack-wide); LS last closed trade; N0/N5/N1 session net below 0 / -0.5R / -1R (R = $1,200); CY carry (previous session net sets the opening trade). Actions x0.5 / x0.67 / x0.75 after a loss, x1.25 / x1.5 after a win. Resets never / flip (next opposite-sign trade) / 30, 60, 120 min / state. P7 on its own, Asia and London separately. Context fresh / chasing / reentry. WL_E1 is already inside JN05W2 (c_gov noevid, rule on P7); the WL_E1ALL combination follows.

## 2. First-order screen of the queued cells (lots change only, no cap/re-entry effects; used ONLY to order the exact queue)

| cell | trades affected | L3M DD cut % | L6M DD cut % | L6M d mean | L6M eq-mean cut % | HOLD cut % | HOLD d mean | PRE cut % | X' cut % | random-label placebo L6M cut % (3 seeds) |
|--|--|--|--|--|--|--|--|--|--|--|
| TL3_EA_A6 | 4346 | 9.2 | 9.2 | -1128 | 4.6 | 12.4 | -971 | -4.8 | 14.6 | -3.0 / 3.7 / 19.3 |
| TL3_EA_F1_P7_S0_H75_RN_CXN | 549 | 13.3 | 13.3 | -442 | 11.7 | 2.3 | -646 | 3.6 | -1.5 | 9.6 / 10.6 / 14.2 |
| TL3_EA_F1_P7_S01_H75_RN | 1126 | 8.7 | 8.7 | -737 | 5.9 | 3.7 | -880 | 6.7 | -3.8 | 9.6 / 9.3 / 14.2 |
| TL3_EA_F1_NP_ALL_H50_RF_CXC | 1912 | 8.9 | 8.9 | -551 | 6.8 | 9.3 | -337 | 2.0 | 10.8 | 6.1 / 0.4 / 11.8 |
| TL3_EA_F1_ALL_ALL_H50_R120 | 4018 | 10.2 | 10.2 | -918 | 6.7 | 7.8 | -1379 | 7.0 | 10.9 | 4.6 / -5.1 / 11.0 |
| TL3_EA_F2_ALL_S01_H67_RN_CXC | 1103 | 11.9 | 11.9 | -29 | 11.8 | 1.6 | -555 | 8.1 | 0.4 | 11.4 / 11.2 / 16.9 |
| TL3_EA_F2_ALL_ALL_H75_RN_CXC | 1350 | 10.7 | 10.7 | -84 | 10.4 | 1.2 | -367 | 5.6 | 0.2 | 8.7 / 8.5 / 12.8 |
| TL3_EA_F2_P7_S01_H67_RN_CXC | 312 | 9.3 | 9.3 | 45 | 9.4 | 0.6 | -312 | 5.5 | 0.4 | 10.2 / 11.8 / 11.4 |
| TL3_EA_LS_P7_S0_H50_R30 | 365 | 20.5 | 20.5 | 303 | 21.6 | 6.7 | -112 | 7.9 | -6.9 | 21.0 / 11.2 / 20.3 |
| TL3_EA_LS_ALL_ALL_H50_R30_CXC | 2210 | 17.0 | 17.0 | 99 | 17.3 | 3.7 | -523 | 10.2 | 11.3 | 26.6 / 13.4 / 23.7 |
| TL3_EA_LS_P7_S01_H50_R30 | 685 | 18.2 | 18.2 | -76 | 18.0 | 3.8 | -138 | 7.0 | -7.2 | 21.0 / 13.5 / 20.3 |
| TL3_EA_LS_NP_ALL_H50_R30 | 2963 | -0.7 | -0.7 | -1512 | -6.6 | 7.8 | -1098 | 4.6 | 15.1 | -1.1 / 5.7 / 15.1 |
| TL3_EA_N0_K7_S01_H67_RN | 2369 | 9.7 | 9.7 | -524 | 7.8 | 3.1 | -703 | 2.6 | 4.5 | - / - / - |
| TL3_EA_N1_K7_S01_H50_RN | 1758 | 13.3 | 13.3 | -553 | 11.3 | 3.7 | -853 | 5.2 | 0.0 | - / - / - |
| TL3_EA_N5_K7_S0_H50_RN | 1267 | 10.0 | 10.0 | -450 | 8.3 | 4.3 | -755 | 5.6 | 5.4 | - / - / - |
| TL3_EA_N5_ALL_ALL_H75_RS | 6959 | -5.5 | -5.5 | -2884 | -20.0 | 18.4 | -2057 | 19.1 | 6.2 | - / - / - |
| TL3_EA_N1_ALL_ALL_H67_RS | 5145 | -16.0 | -16.0 | -3888 | -38.7 | 22.7 | -2574 | 15.6 | 8.0 | - / - / - |
| TL3_EA_SF_ALL_ALL_H50_RN | 7373 | -1.4 | -1.4 | -4942 | -29.0 | 29.4 | -3579 | 13.0 | 5.1 | 0.4 / -29.0 / -7.4 |
| TL3_EA_SF_NP_ALL_H67_RF | 3077 | 0.1 | 0.1 | -793 | -3.1 | 10.6 | -587 | 5.3 | 9.8 | -8.1 / -3.3 / 0.0 |
| TL3_EA_CYS1_P7_ALL_H50_RN_CXC | 577 | 8.5 | 8.5 | -389 | 7.1 | 4.9 | -183 | -1.0 | 11.3 | 8.5 / 8.5 / 8.5 |
| TL3_EA_CYS1_ALL_ALL_H67_RN | 4477 | 4.0 | 4.0 | -2253 | -4.7 | 8.8 | -800 | 6.4 | 35.8 | 4.0 / 4.0 / 4.0 |
| TL3_EA_SF_ALL_S1_U150_R120 | 908 | 9.2 | 9.2 | -195 | 8.4 | 8.2 | -318 | -7.8 | 2.0 | -5.5 / 0.0 / 0.0 |
| TL3_EA_SF_NP_S1_U150_R120_CXN | 597 | 7.5 | 7.5 | -128 | 7.0 | 2.0 | -157 | -1.0 | 3.1 | -2.2 / 0.0 / 0.0 |
| TL3_EA_N5_U7_S1_U150_RN | 152 | 6.6 | 6.6 | 296 | 7.7 | 0.4 | -58 | -4.7 | 0.0 | - / - / - |
| TL3_EA_CYS1_NP_S1_U150_RN | 1150 | 7.2 | 7.2 | 632 | 9.6 | 0.9 | 541 | -9.3 | -12.3 | 7.2 / 7.2 / 7.2 |
| TL3_EA_F2_K7_ALL_U150_R60_CXC | 374 | 5.8 | 5.8 | 201 | 6.5 | 0.7 | -7 | -5.0 | -0.2 | 3.6 / -0.5 / -0.5 |
| TL3_EA_F1_NP_ALL_U125_RF | 1910 | -1.3 | -1.3 | 238 | -0.3 | -0.6 | 284 | -5.1 | 4.9 | -4.1 / -1.9 / -11.8 |
| TL3_EA_N1_ALL_S0_U125_RN_CXN | 2227 | -38.7 | -38.7 | 2706 | -26.3 | -20.6 | 1833 | -4.4 | -2.0 | - / - / - |
| TL3_EA_N0_ALL_ALL_U125_RN_CXN | 6500 | -35.3 | -35.3 | 2517 | -24.0 | -16.8 | 1338 | -10.2 | 0.5 | - / - / - |
| TL3_EA_F1_P7_S1_H75_RN | 533 | 0.0 | 0.0 | -23 | -0.1 | -0.2 | -124 | 3.1 | -0.2 | 0.0 / 0.0 / 0.0 |
| TL3_EA_F1_P7_S1_H50_RN_CXN | 482 | 0.0 | 0.0 | 17 | 0.1 | 1.5 | -92 | 0.3 | -0.4 | 0.0 / 0.0 / 0.0 |
| TL3_EA_N1_P7_S0_H67_RN | 778 | 2.2 | 2.2 | -1571 | -4.4 | 15.0 | -1335 | 4.0 | -2.0 | - / - / - |
| TL3_EA_CYB1_P7_ALL_H50_RN | 684 | 0.0 | 0.0 | -1195 | -5.1 | -5.4 | -804 | -3.6 | 18.3 | 0.0 / 0.0 / 0.0 |
| TL3_EA_CYS1_ALL_S1_H75_RN | 1295 | 6.9 | 6.9 | -63 | 6.7 | -5.6 | -46 | 6.4 | -6.7 | 6.9 / 6.9 / 6.9 |

## 4. Queue state

- exact cell-months done: 0; pending lines: 82; cells in cells.txt: 35
- last promotions: none yet

## 5. Not yet done (in order)

exact placebos (random first-trade labels, seeds 1-3, cells TL3_EA_*_PBk) for every cell that passes L6M; walk-forward every 2 weeks; W44-removed DD (column dd44); competent-trader test and session-by-session table; WL_E1ALL combination; carry variants; P7 per-session finer grid.

