# DS3_SESSION_2_LEDGER - every cell with trade rows, re-scored by entry session (D3SS2, T-SESSION item 2)

Written 2026-10-28 18:11Z. Research only; no live, execution-server or chart change; label days after 2026-02-06 dropped at load. Code l2vast/ds3/code/ss2/, outputs l2vast/ds3/out/ss2/. Prereg l2vast/ds3/prereg/SS2_prereg.md sha256 39ac21baf6d0ed6f4599eb3619b2c7ca2973f212e5b9d8b918a4195ebc4922f3 (DECISIONS.md). PREHOLD list autopilot/DS3_SESSION_2_PREHOLD.md sha256 fdb443f58e2b4c7bea0cb547dbbe541f66915e93a392080609cbe7af54020fd7 (written before HOLD/X were read; one HOLD look and one X look logged in out/ss2/looks.jsonl).

## 1. Count and multiplicity
- Cells with trade rows on disk: **3098** (15,497,142 trades, label days 2023-02..2026-02-06); 3086 have PRE trades. Index: out/ss2/ledger_index.parquet (family, cell, rows path, entry-time column, pnl column, basis, instrument, verdict as labelled; 1491 cells have no verdict label in rows/*.json).
- F = cells x 6 sessions = **18,588**. Cells share trades (the same ST/HM/KB entries carry 420 bracket variants, the ba/rows, rows2, rows3 and ba/rows3 'seq_' copies, e1 vs e1_v1 etc.). Effectively independent cells = overlap clusters (connected components, Jaccard >= 0.5 on PRE entry minute+side): **1205** (917 at Jaccard 0.3, 1,712 at 0.8), so F_eff = 1205 x 6 = **7,230**.
- PRE tests with n >= 100: 11,692 cell-sessions = 3,995 independent (cluster x session). PRE-selected (CI > 0): **761** cell-sessions = 228 independent (cluster x session); chance expectation at a 2.5% one-sided rate is about 100 independent. HOLD sign persistence of the selected list: 80% positive, 54% pass the three-part HOLD gate (a null without persistence would pass about 25-30%).
- Best-of-F is printed as a label only. Cleared at F: 1 cell-session; cleared at F_eff: 3.

### Conventions and limits (read before using any $)
- Session = ENTRY time ET (ASIA 18:00-02:00, LONDON 02:00-08:30, PREOPEN 08:30-09:30 [the directive's PRE; renamed to avoid the PRE window], NY-AM 09:30-12:00, NY-PM 12:00-15:00, CLOSE 15:00-16:54); 16:54-18:00 entries are OFF (pooled only).
- $ per trade as stored in the source tables: F1-type tables (TP, SF, IC, FP, PRO, TR1, H4) = stored net at 10 NQ lots incl. the source's costs; SB = net pts x lots x 20; points-only tables (ba, tso, g3, pb4/e1, xte, xtr1, T-BRACKET entries, D4a pts) = pts x 200 - 100.13 per trade (10 lots, the stored cost); CHOP B* = cell pnl at its own base lots; struct48 = net_usd per cell lots. Magnitudes are therefore comparable within a family, not strictly across families. Basis label (mapped/direct) is the source's where the rows/*.json carried one, else 'rows-as-stored'. Conservative fills are as in the source (no re-fill). WEAK-fee ceiling (MCL, 6E) applied; no ledger cell is on those instruments.
- Placebo: the cell-session's own entry clock with the direction randomised (weekly sign-flip of the cell-session sums, 200 draws); the placebo mean is 0 by construction, so 'effect' equals the net mean and is conservative (random direction would earn minus the cost). Random-in-regime placebo draws exist as per-trade rows only for the CHOP B10 orders and could not be attached per cell x session; stated limitation.
- CI and MDE: week-clustered (all label weeks of the window), 95% t interval; MDE = 2.8 x SE. Weeks in PRE = 75.
- HOLD year segments are 2025-07..12 (about 26 weeks) and 2026-01-01..02-06 (about 5.5 weeks); the 2026 stub is short, so 'both HOLD years positive' is a weak test.
- The 2023 span (2023-04..2024-01), by year and X-span are printed, never used as a gate (user rule).

## 2. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_cells | alive_clusters | best | best_eff | best_mde | best_tpw |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 2571 | 341 | 96 | 190 | 0 | 190 | 58 | IF_30s_eb | 337 | 202 | 41.5 |
| LONDON | 02:00-08:30 | 2563 | 62 | 36 | 39 | 1 | 40 | 21 | CRT_M15_M1_close_ib | 258 | 138 | 17.4 |
| PREOPEN | 08:30-09:30 | 1549 | 38 | 16 | 16 | 0 | 16 | 8 | IF_30s_eb | 392 | 423 | 9.55 |
| NY-AM | 09:30-12:00 | 2555 | 291 | 52 | 154 | 0 | 154 | 29 | IF_15s_eb | 446 | 267 | 40.7 |
| NY-PM | 12:00-15:00 | 2406 | 29 | 28 | 9 | 0 | 9 | 8 | TB4B_tick_28_tick_2000_ST10_E20_1_T3 | 1207 | 1279 | 5.99 |
| CLOSE | 15:00-16:54 | 48 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |  |

'cells_n100' = cell-sessions with >= 100 PRE trades; 'pre_sig' = selected on PRE (CI > 0); 'alive' = SESSION-CANDIDATE or SESSION-PASS after the one HOLD look. NY (NY-AM + NY-PM) is derived: see out/ss2/pre_stats.parquet (sess 7). CLOSE has no PRE-significant cell.

Tier totals: SESSION-PASS 1, SESSION-CANDIDATE 408, DEAD-IN-HOLD 352 (PRE-selected cell-sessions 761); distinct alive cells 326, alive overlap clusters 94. 2023-span (X) positive in 41% of the alive cell-sessions (ASIA/LONDON/ICT-type cells earn from 2024 on and lose in 2023; NY-AM is positive in 2023 in 65%).

## 3. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates (tier shows CANDIDATE/PASS). mde = per-trade MDE $; 'mean' per trade $; hold_* are the single HOLD look.
| cell | family | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | verdict_label | basis | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CRT_M15_M1_close_ib | ICT-SF (silver/fvg SF) | LONDON | 1302 | 17.4 | 262 | 138 | 5.33 | 0.41 | 574 | 110 | 91.9 | 172 | -322 | -347 | 142 | 259 | 172 | SESSION-PASS |  | BOF_F:clear | DEAD | MAPPED | 100.0 | 94 |
| IF_30s_eb | ICT-IC (IC blocks) | ASIA | 3116 | 41.5 | 347 | 202 | 4.80 | 0.19 | 1763 | 387 | 438 | 200 | -232 | -234 | 186 | 468 | 200 | SESSION-CANDIDATE |  | BOF_Feff:clear | DEAD | MAPPED | 200 | 267 |
| IF_15s_eb | ICT-IC (IC blocks) | NY-AM | 3056 | 40.7 | 446 | 267 | 4.67 | 0.15 | 1493 | 603 | 655 | 306 | -128 | -175 | 357 | 620 | 306 | SESSION-CANDIDATE |  | BOF_Feff:clear | CANDIDATE | MAPPED | 271 | 252 |
| CRT_M15_M1_close | ICT-SF (silver/fvg SF) | LONDON | 3136 | 41.8 | 170 | 109 | 4.35 | 0.41 | 1399 | 209 | 200 | 248 | -233 | -272 | 36.1 | 280 | 248 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 92.1 | 93 |
| IF_15s_eb | ICT-IC (IC blocks) | ASIA | 3868 | 51.6 | 268 | 173 | 4.34 | 0.18 | 2086 | 394 | 399 | 373 | -59.3 | -39.8 | 68.7 | 433 | 373 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 271 | 252 |
| PB7_PB_HMA55_EMA1_T1_W60_s+3 | T-PB (pullback/PBX TP) | ASIA | 690 | 9.20 | 1384 | 981 | 3.95 | 0.56 | 313 | 112 | 146 | -7.13 | -427 | -468 | 1308 | 841 | -7.13 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD | MAPPED | 325 | 27 |
| E1A_RENKOC5_A3_r48 | T-ENTRY e1 | ASIA | 424 | 5.65 | 2341 | 1686 | 3.89 | 0.27 | 188 | 2321 | 1658 | 4151 | -12.7 | -48.8 | 2450 | 2022 | 4151 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 117 | 990 |
| IF_30s_ea | ICT-IC (IC blocks) | ASIA | 3012 | 40.2 | 277 | 205 | 3.78 | 0.22 | 1609 | 285 | 326 | 118 | -103 | -98.1 | 198 | 334 | 118 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 178 | 266 |
| CRT_M30_M1_close | ICT-SF (silver/fvg SF) | ASIA | 1431 | 19.1 | 231 | 172 | 3.76 | 0.35 | 752 | 420 | 394 | 516 | -307 | -299 | -48.2 | 449 | 516 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 146 | 98 |
| FV_15s_ea | ICT-IC (IC blocks) | ASIA | 3697 | 49.3 | 199 | 149 | 3.75 | 0.22 | 2200 | 381 | 349 | 516 | -264 | -300 | 11.0 | 371 | 516 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 142 | 227 |
| PB_HMA55_EMA1_T1 | T-PB (pullback/PBX TP) | ASIA | 695 | 9.27 | 1425 | 1077 | 3.70 | 0.56 | 302 | 414 | 705 | -514 | -1182 | -1308 | 1091 | 1294 | -514 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | PASS | DIRECT L2 | 412 | 20 |
| PB7_PB_HMA55_EMA1_T1_W15_s+0 | T-PB (pullback/PBX TP) | ASIA | 696 | 9.28 | 1461 | 1106 | 3.70 | 0.57 | 306 | 730 | 1005 | -146 | -1278 | -1540 | 1308 | 1357 | -146 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | PASS | DIRECT L2 | 479 | 20 |
| PB7_PB_HMA55_EMA1_T1_W30_s+3 | T-PB (pullback/PBX TP) | ASIA | 691 | 9.21 | 1335 | 1012 | 3.69 | 0.56 | 317 | -153 | -59.3 | -479 | -517 | -401 | 1274 | 651 | -479 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD | MAPPED | 350 | 27 |
| IF_15s_grBL | ICT-IC (IC blocks) | ASIA | 2122 | 28.3 | 303 | 234 | 3.64 | 0.18 | 1096 | 328 | 303 | 431 | -124 | -114 | 74.4 | 448 | 431 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 270 | 257 |
| d4a/don_tt_cons | D4a rows (net) don | NY-AM | 504 | 6.72 | 1399 | 1085 | 3.61 | 0.36 | 257 | -140 | -73.7 | -396 | -141 | 68.5 | 1616 | 265 | -396 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | UNLABELLED | rows-as-stored | 789 | 1052 |
| ba2/EM_t20_s40 | BA bracket-assign rows2 | ASIA | 299 | 3.99 | 1091 | 847 | 3.60 | 0.77 | 150 | 300 | -198 | 2567 | 48.0 | 140 | 870 | 493 | 2567 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | UNLABELLED | rows-as-stored | 500 | 771 |
| ba2/HM_t75_s90 | BA bracket-assign rows2 | NY-AM | 427 | 5.69 | 2443 | 1904 | 3.59 | 0.61 | 197 | 1798 | 816 | 5651 | 2103 | 2889 | 2768 | 1038 | 5651 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 889 | 781 |
| ba2/EM_t40_s40 | BA bracket-assign rows2 | ASIA | 281 | 3.75 | 1466 | 1143 | 3.59 | 0.60 | 145 | 915 | 330 | 3592 | 2.14 | 10.8 | 1154 | 1042 | 3592 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 741 | 771 |
| CRT_H1_30s_close | ICT-SF (silver/fvg SF) | LONDON | 891 | 11.9 | 339 | 272 | 3.49 | 0.27 | 399 | 409 | 515 | 23.7 | -77.9 | -115 | 152 | 544 | 23.7 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 203 | 72 |
| ba2/KB_t60_s75 | BA bracket-assign rows2 | ASIA | 704 | 9.39 | 1445 | 1175 | 3.44 | 0.61 | 321 | 600 | 494 | 954 | 84.2 | 659 | 1113 | 991 | 954 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 566 | 788 |
| ba/SS_KB_ASIA_t60_s75 | BA bracket-assign rows | ASIA | 704 | 9.39 | 1445 | 1175 | 3.44 | 0.61 | 321 | 600 | 494 | 954 | 84.2 | 659 | 1113 | 991 | 954 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 1445 | 821 |
| ba3/seq_KB_ASIA_t60_s75 | BA bracket-assign rows3 | ASIA | 704 | 9.39 | 1445 | 1175 | 3.44 | 0.61 | 321 | 600 | 494 | 954 | 84.2 | 659 | 1113 | 991 | 954 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 780 | 788 |
| IF_15s_ea | ICT-IC (IC blocks) | NY-AM | 2417 | 32.2 | 367 | 300 | 3.43 | 0.17 | 1364 | 440 | 402 | 677 | -274 | -301 | 253 | 466 | 677 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 197 | 251 |
| IF_15s_grBS | ICT-IC (IC blocks) | ASIA | 2329 | 31.1 | 270 | 221 | 3.43 | 0.18 | 1226 | 290 | 283 | 321 | -99.2 | -83.6 | 75.4 | 389 | 321 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 249 | 257 |
| IF_30s_ec | ICT-IC (IC blocks) | ASIA | 2207 | 29.4 | 319 | 262 | 3.41 | 0.26 | 1298 | 107 | 91.6 | 178 | -147 | -135 | 198 | 257 | 178 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 253 | 268 |
| CRT_M30_M1_close | ICT-SF (silver/fvg SF) | LONDON | 1937 | 25.8 | 170 | 139 | 3.40 | 0.36 | 861 | 285 | 301 | 220 | -89.8 | -118 | -5.13 | 366 | 220 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 146 | 98 |
| IF_15s_ed | ICT-IC (IC blocks) | ASIA | 2474 | 33.0 | 330 | 274 | 3.37 | 0.26 | 1409 | 309 | 280 | 446 | 66.2 | 82.3 | 147 | 407 | 446 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 178 | 254 |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | T-ENTRY pb4 (TB4) | ASIA | 450 | 6.00 | 1842 | 1537 | 3.36 | 0.58 | 200 | -1060 | -1271 | -100 | 46.0 | -146 | 1601 | 594 | -100 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | PASS | mapped | 714 | 884 |
| IF_3m_eb | ICT-IC (IC blocks) | ASIA | 1213 | 16.2 | 371 | 312 | 3.33 | 0.23 | 600 | 560 | 489 | 855 | -237 | -206 | 68.6 | 598 | 855 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 223 | 275 |
| PB7_PB5_depth_atr0.5_W15_s+0 | T-PB (pullback/PBX TP) | ASIA | 342 | 4.56 | 2372 | 2020 | 3.29 | 0.61 | 192 | 905 | 1097 | 374 | 777 | 356 | 2313 | 1841 | 374 | SESSION-CANDIDATE |  | BOF:not cleared | PASS | DIRECT L2 | 598 | 0 |


### Same, one cell per overlap cluster (top 30 clusters)
| cell | family | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | verdict_label | basis | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CRT_M15_M1_close_ib | ICT-SF (silver/fvg SF) | LONDON | 1302 | 17.4 | 262 | 138 | 5.33 | 0.41 | 574 | 110 | 91.9 | 172 | -322 | -347 | 142 | 259 | 172 | SESSION-PASS |  | BOF_F:clear | DEAD | MAPPED | 100.0 | 94 |
| IF_30s_eb | ICT-IC (IC blocks) | ASIA | 3116 | 41.5 | 347 | 202 | 4.80 | 0.19 | 1763 | 387 | 438 | 200 | -232 | -234 | 186 | 468 | 200 | SESSION-CANDIDATE |  | BOF_Feff:clear | DEAD | MAPPED | 200 | 267 |
| IF_15s_eb | ICT-IC (IC blocks) | NY-AM | 3056 | 40.7 | 446 | 267 | 4.67 | 0.15 | 1493 | 603 | 655 | 306 | -128 | -175 | 357 | 620 | 306 | SESSION-CANDIDATE |  | BOF_Feff:clear | CANDIDATE | MAPPED | 271 | 252 |
| CRT_M15_M1_close | ICT-SF (silver/fvg SF) | LONDON | 3136 | 41.8 | 170 | 109 | 4.35 | 0.41 | 1399 | 209 | 200 | 248 | -233 | -272 | 36.1 | 280 | 248 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 92.1 | 93 |
| PB7_PB_HMA55_EMA1_T1_W60_s+3 | T-PB (pullback/PBX TP) | ASIA | 690 | 9.20 | 1384 | 981 | 3.95 | 0.56 | 313 | 112 | 146 | -7.13 | -427 | -468 | 1308 | 841 | -7.13 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD | MAPPED | 325 | 27 |
| E1A_RENKOC5_A3_r48 | T-ENTRY e1 | ASIA | 424 | 5.65 | 2341 | 1686 | 3.89 | 0.27 | 188 | 2321 | 1658 | 4151 | -12.7 | -48.8 | 2450 | 2022 | 4151 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 117 | 990 |
| IF_30s_ea | ICT-IC (IC blocks) | ASIA | 3012 | 40.2 | 277 | 205 | 3.78 | 0.22 | 1609 | 285 | 326 | 118 | -103 | -98.1 | 198 | 334 | 118 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 178 | 266 |
| CRT_M30_M1_close | ICT-SF (silver/fvg SF) | ASIA | 1431 | 19.1 | 231 | 172 | 3.76 | 0.35 | 752 | 420 | 394 | 516 | -307 | -299 | -48.2 | 449 | 516 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 146 | 98 |
| FV_15s_ea | ICT-IC (IC blocks) | ASIA | 3697 | 49.3 | 199 | 149 | 3.75 | 0.22 | 2200 | 381 | 349 | 516 | -264 | -300 | 11.0 | 371 | 516 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 142 | 227 |
| PB_HMA55_EMA1_T1 | T-PB (pullback/PBX TP) | ASIA | 695 | 9.27 | 1425 | 1077 | 3.70 | 0.56 | 302 | 414 | 705 | -514 | -1182 | -1308 | 1091 | 1294 | -514 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | PASS | DIRECT L2 | 412 | 20 |
| IF_15s_grBL | ICT-IC (IC blocks) | ASIA | 2122 | 28.3 | 303 | 234 | 3.64 | 0.18 | 1096 | 328 | 303 | 431 | -124 | -114 | 74.4 | 448 | 431 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 270 | 257 |
| d4a/don_tt_cons | D4a rows (net) don | NY-AM | 504 | 6.72 | 1399 | 1085 | 3.61 | 0.36 | 257 | -140 | -73.7 | -396 | -141 | 68.5 | 1616 | 265 | -396 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | UNLABELLED | rows-as-stored | 789 | 1052 |
| ba2/EM_t20_s40 | BA bracket-assign rows2 | ASIA | 299 | 3.99 | 1091 | 847 | 3.60 | 0.77 | 150 | 300 | -198 | 2567 | 48.0 | 140 | 870 | 493 | 2567 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | UNLABELLED | rows-as-stored | 500 | 771 |
| ba2/HM_t75_s90 | BA bracket-assign rows2 | NY-AM | 427 | 5.69 | 2443 | 1904 | 3.59 | 0.61 | 197 | 1798 | 816 | 5651 | 2103 | 2889 | 2768 | 1038 | 5651 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 889 | 781 |
| CRT_H1_30s_close | ICT-SF (silver/fvg SF) | LONDON | 891 | 11.9 | 339 | 272 | 3.49 | 0.27 | 399 | 409 | 515 | 23.7 | -77.9 | -115 | 152 | 544 | 23.7 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 203 | 72 |
| ba2/KB_t60_s75 | BA bracket-assign rows2 | ASIA | 704 | 9.39 | 1445 | 1175 | 3.44 | 0.61 | 321 | 600 | 494 | 954 | 84.2 | 659 | 1113 | 991 | 954 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 566 | 788 |
| ba/SS_KB_ASIA_t60_s75 | BA bracket-assign rows | ASIA | 704 | 9.39 | 1445 | 1175 | 3.44 | 0.61 | 321 | 600 | 494 | 954 | 84.2 | 659 | 1113 | 991 | 954 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 1445 | 821 |
| IF_15s_ea | ICT-IC (IC blocks) | NY-AM | 2417 | 32.2 | 367 | 300 | 3.43 | 0.17 | 1364 | 440 | 402 | 677 | -274 | -301 | 253 | 466 | 677 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 197 | 251 |
| IF_30s_ec | ICT-IC (IC blocks) | ASIA | 2207 | 29.4 | 319 | 262 | 3.41 | 0.26 | 1298 | 107 | 91.6 | 178 | -147 | -135 | 198 | 257 | 178 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 253 | 268 |
| IF_15s_ed | ICT-IC (IC blocks) | ASIA | 2474 | 33.0 | 330 | 274 | 3.37 | 0.26 | 1409 | 309 | 280 | 446 | 66.2 | 82.3 | 147 | 407 | 446 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 178 | 254 |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | T-ENTRY pb4 (TB4) | ASIA | 450 | 6.00 | 1842 | 1537 | 3.36 | 0.58 | 200 | -1060 | -1271 | -100 | 46.0 | -146 | 1601 | 594 | -100 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | PASS | mapped | 714 | 884 |
| IF_3m_eb | ICT-IC (IC blocks) | ASIA | 1213 | 16.2 | 371 | 312 | 3.33 | 0.23 | 600 | 560 | 489 | 855 | -237 | -206 | 68.6 | 598 | 855 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | MAPPED | 223 | 275 |
| PB7_PB5_depth_atr0.5_W15_s+0 | T-PB (pullback/PBX TP) | ASIA | 342 | 4.56 | 2372 | 2020 | 3.29 | 0.61 | 192 | 905 | 1097 | 374 | 777 | 356 | 2313 | 1841 | 374 | SESSION-CANDIDATE |  | BOF:not cleared | PASS | DIRECT L2 | 598 | 0 |
| PB7_PB5_depth_atr0.5_W15_s-3 | T-PB (pullback/PBX TP) | ASIA | 387 | 5.16 | 1851 | 1607 | 3.23 | 0.58 | 215 | 1570 | 2084 | 38.2 | 898 | 517 | 1603 | 2239 | 38.2 | SESSION-CANDIDATE |  | BOF:not cleared | PASS | DIRECT L2 | 619 | 24 |
| FV_15s_grAmL | ICT-IC (IC blocks) | ASIA | 3710 | 49.5 | 181 | 158 | 3.21 | 0.22 | 2075 | 444 | 389 | 677 | -159 | -221 | 33.1 | 361 | 677 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 111 | 228 |
| FV_3m_ea_far0 | ICT-IC (IC blocks) | LONDON | 2731 | 36.4 | 178 | 156 | 3.20 | 0.29 | 1129 | 356 | 437 | -75.5 | -163 | -213 | 42.6 | 435 | -75.5 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | DEAD | MAPPED | 174 | 237 |
| TB4W_03_time_15s_ST3_E20_1_T2_ntime14 | T-ENTRY pb4 (TB4) | ASIA | 800 | 10.7 | 1237 | 1083 | 3.20 | 0.56 | 369 | 494 | 40.9 | 1878 | -106 | 2.14 | 1301 | 601 | 1878 | SESSION-CANDIDATE |  | BOF:not cleared | CANDIDATE | mapped | 391 | 976 |
| IF_3m_ea_far0 | ICT-IC (IC blocks) | ASIA | 1555 | 20.7 | 265 | 236 | 3.14 | 0.33 | 743 | 376 | 325 | 580 | -61.5 | -66.2 | 24.3 | 456 | 580 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 186 | 270 |
| ba2/SM_t60_sst | BA bracket-assign rows2 | ASIA | 264 | 3.52 | 1539 | 1380 | 3.12 | 0.41 | 123 | 459 | 246 | 1339 | 953 | 926 | 1228 | 1148 | 1339 | SESSION-CANDIDATE |  | BOF:not cleared | UNLABELLED | rows-as-stored | 435 | 802 |
| FV_1m_eb | ICT-IC (IC blocks) | ASIA | 3389 | 45.2 | 199 | 180 | 3.10 | 0.20 | 1718 | 350 | 325 | 454 | -323 | -360 | 38.0 | 354 | 454 | SESSION-CANDIDATE |  | BOF:not cleared | DEAD | MAPPED | 170 | 233 |


## 4. Cells DEAD pooled but alive in one session
Selection: index verdict label DEAD, or pooled all-hours PRE mean <= 0 (any label), and tier SESSION-CANDIDATE/PASS. 108 cell-sessions, 79 cells, 61 independent (cluster x session); full list out/ss2/dead_pooled_alive_in_session.csv. Top 40 independent:
| cell | family | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | verdict_label | pool_pre_mean | pool_pre_lo | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CRT_M15_M1_close_ib | ICT-SF (silver/fvg SF) | LONDON | 1302 | 17.4 | 262 | 138 | 5.33 | 574 | 110 | 91.9 | 172 | -322 | -347 | 142 | 259 | 172 | SESSION-PASS | BOF_F:clear | DEAD | 100.0 | 18.8 | 94 |
| IF_30s_eb | ICT-IC (IC blocks) | ASIA | 3116 | 41.5 | 347 | 202 | 4.80 | 1763 | 387 | 438 | 200 | -232 | -234 | 186 | 468 | 200 | SESSION-CANDIDATE | BOF_Feff:clear | DEAD | 200 | 112 | 267 |
| CRT_M15_M1_close | ICT-SF (silver/fvg SF) | LONDON | 3136 | 41.8 | 170 | 109 | 4.35 | 1399 | 209 | 200 | 248 | -233 | -272 | 36.1 | 280 | 248 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 92.1 | 31.1 | 93 |
| CRT_M30_M1_close | ICT-SF (silver/fvg SF) | ASIA | 1431 | 19.1 | 231 | 172 | 3.76 | 752 | 420 | 394 | 516 | -307 | -299 | -48.2 | 449 | 516 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 146 | 55.6 | 98 |
| FV_15s_ea | ICT-IC (IC blocks) | ASIA | 3697 | 49.3 | 199 | 149 | 3.75 | 2200 | 381 | 349 | 516 | -264 | -300 | 11.0 | 371 | 516 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 142 | 66.5 | 227 |
| CRT_H1_30s_close | ICT-SF (silver/fvg SF) | LONDON | 891 | 11.9 | 339 | 272 | 3.49 | 399 | 409 | 515 | 23.7 | -77.9 | -115 | 152 | 544 | 23.7 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 203 | 28.3 | 72 |
| CRT_M30_M1_close | ICT-SF (silver/fvg SF) | LONDON | 1937 | 25.8 | 170 | 139 | 3.40 | 861 | 285 | 301 | 220 | -89.8 | -118 | -5.13 | 366 | 220 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 146 | 55.6 | 98 |
| IF_15s_ed | ICT-IC (IC blocks) | ASIA | 2474 | 33.0 | 330 | 274 | 3.37 | 1409 | 309 | 280 | 446 | 66.2 | 82.3 | 147 | 407 | 446 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 178 | 47.6 | 254 |
| FV_15s_grAmL | ICT-IC (IC blocks) | ASIA | 3710 | 49.5 | 181 | 158 | 3.21 | 2075 | 444 | 389 | 677 | -159 | -221 | 33.1 | 361 | 677 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 111 | 33.3 | 228 |
| IF_3m_ea_far0 | ICT-IC (IC blocks) | ASIA | 1555 | 20.7 | 265 | 236 | 3.14 | 743 | 376 | 325 | 580 | -61.5 | -66.2 | 24.3 | 456 | 580 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 186 | 82.1 | 270 |
| FV_1m_eb | ICT-IC (IC blocks) | ASIA | 3389 | 45.2 | 199 | 180 | 3.10 | 1718 | 350 | 325 | 454 | -323 | -360 | 38.0 | 354 | 454 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 170 | 97.1 | 233 |
| SB_HM_tg_fib2618 | SB (silver-bullet SB) | ASIA | 469 | 6.25 | 1702 | 1594 | 2.99 | 232 | 1403 | 1469 | 1137 | -642 | -510 | 1599 | 1501 | 1137 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 472 | -217 | 781 |
| IF_3m_ea_shift60 | ICT-IC (IC blocks) | LONDON | 1642 | 21.9 | 242 | 232 | 2.92 | 748 | 379 | 303 | 698 | -106 | -162 | 225 | 288 | 698 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 112 | -25.1 | 274 |
| FV_1m_eb | ICT-IC (IC blocks) | LONDON | 3817 | 50.9 | 155 | 151 | 2.87 | 1631 | 359 | 333 | 495 | -186 | -179 | -13.4 | 353 | 495 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 170 | 97.1 | 233 |
| IF_5m_tg_so | ICT-IC (IC blocks) | LONDON | 822 | 11.0 | 446 | 438 | 2.85 | 346 | 727 | 546 | 1731 | 56.5 | 40.2 | 298 | 601 | 1731 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 255 | 31.7 | 287 |
| SB_HM_st_vw_5 | SB (silver-bullet SB) | NY-AM | 341 | 4.55 | 1865 | 1853 | 2.82 | 146 | 640 | 703 | 267 | -34.4 | -384 | 2039 | 1175 | 267 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 33.8 | -690 | 781 |
| TR1B_reg5m_n20_t2_r0.5 | T-TREND TR1 | NY-AM | 292 | 3.89 | 1426 | 1466 | 2.72 | 140 | 167 | 126 | 429 | 1069 | 1032 | 1798 | 468 | 429 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 230 | -324 | 670 |
| ba2/EM_t40_s60 | BA bracket-assign rows2 | ASIA | 260 | 3.47 | 1487 | 1539 | 2.71 | 134 | 700 | 149 | 3100 | -424 | -281 | 1116 | 886 | 3100 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 788 | 210 | 771 |
| IF_30s_eb | ICT-IC (IC blocks) | PREOPEN | 716 | 9.55 | 406 | 423 | 2.68 | 294 | 550 | 500 | 815 | -132 | -110 | 308 | 479 | 815 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 200 | 112 | 267 |
| IF_3m_ea_shift60 | ICT-IC (IC blocks) | ASIA | 1283 | 17.1 | 366 | 383 | 2.68 | 599 | 318 | 275 | 496 | -251 | -309 | 207 | 434 | 496 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 112 | -25.1 | 274 |
| FV_3m_ea_far0 | ICT-IC (IC blocks) | ASIA | 2554 | 34.1 | 180 | 191 | 2.63 | 1204 | 461 | 464 | 450 | -116 | -122 | -22.7 | 461 | 450 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 174 | 84.5 | 237 |
| CRT_M15_M1_close | ICT-SF (silver/fvg SF) | ASIA | 2246 | 29.9 | 128 | 137 | 2.61 | 1183 | 265 | 228 | 407 | -128 | -138 | -60.2 | 262 | 407 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 92.1 | 31.1 | 93 |
| FV_5m_eb | ICT-IC (IC blocks) | ASIA | 1391 | 18.5 | 264 | 283 | 2.61 | 669 | 477 | 401 | 784 | -273 | -359 | 93.7 | 458 | 784 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 185 | 62.4 | 243 |
| IF_3m_ea | ICT-IC (IC blocks) | PREOPEN | 248 | 3.31 | 928 | 1008 | 2.58 | 119 | 531 | 439 | 1017 | 66.0 | 110 | 484 | 978 | 1017 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 149 | 25.4 | 270 |
| ba/A_t30_s90 | BA bracket-assign rows | NY-AM | 1636 | 21.8 | 578 | 628 | 2.58 | 791 | 704 | 358 | 2048 | -116 | 27.9 | 545 | 398 | 2048 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 176 | -120 | 809 |
| IF_3m_tg_f60 | ICT-IC (IC blocks) | LONDON | 1278 | 17.0 | 408 | 447 | 2.55 | 527 | 578 | 530 | 770 | -222 | -281 | 296 | 532 | 770 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 328 | 192 | 270 |
| TB4B_tick_28_tick_2000_ST10_E20_1_T3 | T-ENTRY pb4 (TB4) | NY-PM | 449 | 5.99 | 1163 | 1279 | 2.55 | 170 | 1556 | 1726 | 901 | -89.5 | -568 | 978 | 1712 | 901 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 282 | -263 | 886 |
| FV_15s_grBL | ICT-IC (IC blocks) | LONDON | 1955 | 26.1 | 223 | 247 | 2.53 | 924 | 288 | 293 | 266 | -265 | -273 | 110 | 326 | 266 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 202 | 95.5 | 230 |
| PB6_ST3m_EMA20_1m_T1 | T-PB (pullback/PBX TP) | ASIA | 703 | 9.37 | 998 | 1109 | 2.52 | 315 | 999 | 951 | 1137 | -384 | -546 | 687 | 1182 | 1137 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 234 | -215 | 20 |
| FV_3m_eb | ICT-IC (IC blocks) | LONDON | 2134 | 28.5 | 188 | 209 | 2.51 | 925 | 131 | 151 | 28.8 | -166 | -207 | 66.1 | 275 | 28.8 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 196 | 88.3 | 239 |
| ba/A_t30_s60 | BA bracket-assign rows | ASIA | 1826 | 24.3 | 516 | 584 | 2.48 | 879 | 507 | 391 | 915 | 94.5 | 108 | 397 | 518 | 915 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 239 | 45.8 | 809 |
| PB6_ST3m_EMA20_2m_T1 | T-PB (pullback/PBX TP) | ASIA | 645 | 8.60 | 1143 | 1297 | 2.47 | 280 | 1026 | 513 | 2657 | -180 | -11.5 | 661 | 1102 | 2657 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 382 | -153 | 17 |
| FV_3m_eb | ICT-IC (IC blocks) | NY-AM | 1196 | 15.9 | 386 | 438 | 2.47 | 503 | 160 | 163 | 143 | -294 | -320 | 252 | 367 | 143 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 196 | 88.3 | 239 |
| CRT_M15_M1_close_ib | ICT-SF (silver/fvg SF) | ASIA | 984 | 13.1 | 164 | 186 | 2.46 | 476 | 286 | 308 | 206 | -264 | -255 | -36.3 | 303 | 206 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 100.0 | 18.8 | 94 |
| CRT_H1_M5_close | ICT-SF (silver/fvg SF) | PREOPEN | 230 | 3.07 | 845 | 963 | 2.46 | 92.0 | 334 | 383 | 143 | -258 | -322 | 615 | 807 | 143 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 149 | -13.5 | 78 |
| PB_HMA55_EMA1_T3 | T-PB (pullback/PBX TP) | ASIA | 661 | 8.81 | 1050 | 1218 | 2.41 | 306 | 717 | 607 | 1055 | -1661 | -2092 | 859 | 1000 | 1055 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 76.5 | -455 | 46 |
| PRO1_AGG_RL3_EMA200_VWAP | T-PRO1 | NY-PM | 134 | 1.79 | 2073 | 2439 | 2.38 | 46.0 | 1221 | 469 | 3613 | -2063 | -1959 | 1800 | 1257 | 3613 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 180 | -460 | 490 |
| PB7_PB_HMA55_EMA1_T1_W30_s-3 | T-PB (pullback/PBX TP) | ASIA | 647 | 8.63 | 988 | 1172 | 2.36 | 286 | 269 | 25.5 | 1049 | 52.8 | -325 | 824 | 790 | 1049 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 325 | -138 | 28 |
| TR1E_bos_1m_c2 | T-TREND TR1 | ASIA | 670 | 8.93 | 874 | 1053 | 2.32 | 308 | 973 | 735 | 1629 | -1216 | -1590 | 190 | 1307 | 1629 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 284 | -178 | 719 |
| IF_30s_eb | ICT-IC (IC blocks) | LONDON | 3614 | 48.2 | 150 | 183 | 2.29 | 1664 | 505 | 451 | 774 | -49.4 | -78.1 | -17.6 | 429 | 774 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 200 | 112 | 267 |


## 5. Ledger by family (rows on disk)
| family | cells | rows |
|---|---|---|
| T4-G2 bracket variants | 420 | 2909303 |
| BA bracket-assign rows3 | 305 | 1446298 |
| SB (silver-bullet SB) | 300 | 758752 |
| BA bracket-assign rows2 | 270 | 1249794 |
| T-CHOP cells (B*) | 267 | 528115 |
| ICT-IC (IC blocks) | 192 | 1163264 |
| ICT-SF (silver/fvg SF) | 181 | 361577 |
| T-ENTRY pb4 (TB4) | 177 | 693552 |
| Footprint FP | 169 | 633048 |
| T-PB (pullback/PBX TP) | 157 | 464602 |
| T-TREND TR1 | 133 | 360484 |
| T-PRO1 | 118 | 253740 |
| T-PRO2 | 104 | 271500 |
| T-ENTRY e1 | 57 | 3653679 |
| BA bracket-assign rows | 45 | 270391 |
| T-BRACKET entries | 45 | 166555 |
| T-PRO3 | 42 | 58395 |
| H4 (trades_) | 27 | 56276 |
| DV2D kept | 16 | 11745 |
| struct48 base cells (multi-inst) | 16 | 2759 |
| xte trades | 7 | 16422 |
| G3 rep | 6 | 3214 |
| TSO ST10 | 5 | 28030 |
| TSO SM | 5 | 8930 |
| TSO EM | 5 | 8695 |
| TSO HM10 | 5 | 21665 |
| TSO KB | 5 | 28605 |
| D4a rows (net) | 4 | 11550 |
| G3 fam | 4 | 19185 |
| D4a rows (pts) | 4 | 13700 |
| D4a rows (net) don | 2 | 6830 |
| D4a rows (pts) crt_T | 2 | 5775 |
| xtr1 trades | 2 | 7569 |
| T-PB (pullback base) | 1 | 3143 |


## 6. Families with NO trade rows on disk (summary-only; cell counts from rows/*.json; re-run needed to score by session)
| file | cells | with_rows | no_rows |
|---|---|---|---|
| DS3_TOPEN_B2_ORcond.json | 5442 | 0 | 5442 |
| DS3_TH_G1.json | 4800 | 0 | 4800 |
| DS3_TBRACKET_G1.json | 4800 | 0 | 4800 |
| DS3_TOPEN_B2_DRcond.json | 2007 | 0 | 2007 |
| DS3_TWASHOUT.json | 1488 | 0 | 1488 |
| DS3_TOPEN_B2_ORbase.json | 910 | 0 | 910 |
| DS3_TOPEN_B2_B3GRID.json | 894 | 0 | 894 |
| DS3_TOPEN_B2_ORre.json | 848 | 0 | 848 |
| DS3_TOPEN_B2_PB.json | 579 | 0 | 579 |
| DS3_TBRACKET_T4G1.json | 420 | 0 | 420 |
| DS3_TBRACKET_T4G2.json | 420 | 0 | 420 |
| DS3_TPYRAMID_T4.json | 420 | 0 | 420 |
| DS3_TBRACKET_T4A.json | 392 | 0 | 392 |
| DS3_TBRACKET_SESSION.json | 300 | 0 | 300 |
| DS3_TE2E3.json | 293 | 0 | 293 |
| DS3_TOPEN_B2_DRbase.json | 288 | 0 | 288 |
| DS3_TB.json | 279 | 3 | 276 |
| DS3_TBRACKET.json | 286 | 21 | 265 |
| DS3_TOPEN_B2_SECONDOPENS.json | 264 | 0 | 264 |
| DS3_TPYRAMID.json | 215 | 0 | 215 |
| DS3_TPYRAMID_plainmap.json | 215 | 0 | 215 |
| DS3_TOPEN_B2_PM.json | 201 | 0 | 201 |
| DS3_TFOOTPRINT.json | 366 | 168 | 198 |
| DS3_TOPEN_B2_FADE.json | 197 | 0 | 197 |
| DS3_TOPEN_B2_GAP.json | 163 | 0 | 163 |
| DS3_TOPEN_B2_CONF.json | 160 | 0 | 160 |
| DS3_TH_G2.json | 150 | 0 | 150 |
| DS3_TBRACKET_G2.json | 150 | 0 | 150 |
| DS3_TPULLBACK3.json | 141 | 0 | 141 |
| DS3_TH_G3.json | 138 | 0 | 138 |
| DS3_TBRACKET_G3.json | 138 | 0 | 138 |
| DS3_TA1.json | 120 | 0 | 120 |
| DS3_TSESSLOCK_HM.json | 114 | 0 | 114 |
| DS3_TSESSLOCK_PS.json | 114 | 0 | 114 |
| DS3_TSESSLOCK_KB.json | 114 | 0 | 114 |
| DS3_TSESSLOCK_ST.json | 114 | 0 | 114 |
| DS3_TSESSLOCK_PB.json | 114 | 0 | 114 |
| DS3_TSESSLOCK_SM.json | 114 | 0 | 114 |
| DS3_TSESSLOCK_WT.json | 114 | 0 | 114 |
| DS3_TPBX_B2.json | 112 | 0 | 112 |
| DS3_TR2.json | 74 | 0 | 74 |
| DS3_TC6PB.json | 72 | 0 | 72 |
| DS3_TC4R4.json | 70 | 0 | 70 |
| DS3_TR4.json | 58 | 0 | 58 |
| DS3_TPULLBACK2.json | 52 | 0 | 52 |
| DS3_TC1C2.json | 48 | 0 | 48 |
| DS3_TB7.json | 39 | 0 | 39 |
| DS3_TC3C4.json | 32 | 0 | 32 |
| DS3_TPBX_PB3B_R60_P2.json | 32 | 0 | 32 |
| DS3_TPBX_PB3B_R5_P1.json | 32 | 0 | 32 |
| DS3_TPBX_PRO_ER4_EMA5.json | 32 | 0 | 32 |
| DS3_TPBX_PRO_ER5_EMA5.json | 32 | 0 | 32 |
| DS3_TPBX_PB_ST10_SWZ_T3.json | 32 | 0 | 32 |
| DS3_TPBX_PB3B_R5_P2.json | 32 | 0 | 32 |
| DS3_TB_P8_final.json | 30 | 0 | 30 |
| DS3_TB_P2_final.json | 30 | 0 | 30 |
| DS3_TB_P3_final.json | 30 | 0 | 30 |
| DS3_TPBX_B4.json | 30 | 0 | 30 |
| DS3_TB_P4_final.json | 30 | 0 | 30 |
| DS3_TB_P5_final.json | 30 | 0 | 30 |
| DS3_TB_P6_final.json | 30 | 0 | 30 |
| DS3_TB3.json | 29 | 0 | 29 |
| DS3_TB_P7_final.json | 30 | 1 | 29 |
| DS3_TB_P9_final.json | 30 | 1 | 29 |
| DS3_TB_P1_final.json | 30 | 1 | 29 |
| DS3_TC.json | 28 | 0 | 28 |
| DS3_TB6.json | 25 | 0 | 25 |
| DS3_TI.json | 24 | 0 | 24 |
| DS3_TC5.json | 24 | 0 | 24 |
| DS3_TPBX_B3.json | 24 | 0 | 24 |
| DS3_H2_TAPE1S.json | 24 | 0 | 24 |
| DS3_TA.json | 22 | 0 | 22 |
| DS3_TB8.json | 20 | 0 | 20 |
| DS3_TK.json | 19 | 0 | 19 |
| DS3_TD3.json | 18 | 0 | 18 |
| DS3_TSBS.json | 161 | 144 | 17 |
| DS3_TPBX_B3B.json | 16 | 0 | 16 |
| DS3_TPORTFOLIO.json | 14 | 0 | 14 |
| DS3_TD1.json | 14 | 0 | 14 |
| DS3_TH.json | 14 | 0 | 14 |
| DS3_TB_P10_final.json | 9 | 0 | 9 |
| DS3_TSF.json | 46 | 37 | 9 |
| DS3_TICT.json | 172 | 163 | 9 |
| DS3_TD.json | 7 | 0 | 7 |
| DS3_TD2.json | 7 | 0 | 7 |
| DS3_TCHOP.json | 13 | 7 | 6 |
| DS3_TF.json | 4 | 0 | 4 |
| DS3_TG2.json | 4 | 0 | 4 |
| DS3_TG.json | 4 | 0 | 4 |
| DS3_TJ.json | 3 | 0 | 3 |
| DS3_PRO3.json | 45 | 42 | 3 |
| DS3_PRO1.json | 117 | 114 | 3 |
| DS3_TE.json | 3 | 0 | 3 |
| DS3_STRUCTBRACKET.json | 300 | 299 | 1 |
| DS3_TR1.json | 134 | 133 | 1 |

Plus the 31,097-series pool (out/pool.parquet; daily series only: C5M1, C7P1, C10S1, T3S1, V5P2, B1/B4/B7/B10, FU3, WT432, T3S3 ...). T-OPEN B2 pickles (topen_b2/*.pkl) hold day-level pre_trades (ld, net, lots) without an entry clock; T-PBX pickles hold daily series; T-B/T-B TB* trade files carry entry and exit label days only (no clock). These are the first re-runs to order if session scoring is wanted.

## 7. SESSION-CANDIDATE forward-register entries (text only; live register files not edited)
One entry per independent (cluster x session) shown below (124); all 409 cell-sessions are in out/ss2/forward_register_entries_all.txt. Cells in the same cluster are the same trades under another label; register one.

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_M15_M1_close_ib [ICT-SF (silver/fvg SF)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_M15_M1_close_ib.parquet | tier SESSION-PASS (BOF_F:clear) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1302 trades (17.4/wk) mean $262/trade (MDE $138), HOLD 574 trades mean $110, 2023-span $-322 | overlap cluster 94 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_30s_eb [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_30s_eb.parquet | tier SESSION-CANDIDATE (BOF_Feff:clear) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3116 trades (41.5/wk) mean $347/trade (MDE $202), HOLD 1763 trades mean $387, 2023-span $-232 | overlap cluster 267 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_eb [ICT-IC (IC blocks)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_eb.parquet | tier SESSION-CANDIDATE (BOF_Feff:clear) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3056 trades (40.7/wk) mean $446/trade (MDE $267), HOLD 1493 trades mean $603, 2023-span $-128 | overlap cluster 252 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_M15_M1_close [ICT-SF (silver/fvg SF)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_M15_M1_close.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3136 trades (41.8/wk) mean $170/trade (MDE $109), HOLD 1399 trades mean $209, 2023-span $-233 | overlap cluster 93 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_eb [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3868 trades (51.6/wk) mean $268/trade (MDE $173), HOLD 2086 trades mean $394, 2023-span $-59 | overlap cluster 252 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | E1A_RENKOC5_A3_r48 [T-ENTRY e1] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/e1/E1A_RENKOC5_A3_r48_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 424 trades (5.7/wk) mean $2341/trade (MDE $1686), HOLD 188 trades mean $2321, 2023-span $-13 | overlap cluster 990 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_30s_ea [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_30s_ea.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3012 trades (40.2/wk) mean $277/trade (MDE $205), HOLD 1609 trades mean $285, 2023-span $-103 | overlap cluster 266 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_M30_M1_close [ICT-SF (silver/fvg SF)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_M30_M1_close.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1431 trades (19.1/wk) mean $231/trade (MDE $172), HOLD 752 trades mean $420, 2023-span $-307 | overlap cluster 98 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_15s_ea [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_15s_ea.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3697 trades (49.3/wk) mean $199/trade (MDE $149), HOLD 2200 trades mean $381, 2023-span $-264 | overlap cluster 227 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_grBL [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_grBL.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2122 trades (28.3/wk) mean $303/trade (MDE $234), HOLD 1096 trades mean $328, 2023-span $-124 | overlap cluster 257 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba2/HM_t75_s90 [BA bracket-assign rows2] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows2_HM_t75_s90.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 427 trades (5.7/wk) mean $2443/trade (MDE $1904), HOLD 197 trades mean $1798, 2023-span $2103 | overlap cluster 781 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba2/EM_t40_s40 [BA bracket-assign rows2] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows2_EM_t40_s40.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 281 trades (3.7/wk) mean $1466/trade (MDE $1143), HOLD 145 trades mean $915, 2023-span $2 | overlap cluster 771 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_H1_30s_close [ICT-SF (silver/fvg SF)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_H1_30s_close.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 891 trades (11.9/wk) mean $339/trade (MDE $272), HOLD 399 trades mean $409, 2023-span $-78 | overlap cluster 72 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba3/seq_KB_ASIA_t60_s75 [BA bracket-assign rows3] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows3/seq_KB_ASIA_t60_s75.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 704 trades (9.4/wk) mean $1445/trade (MDE $1175), HOLD 321 trades mean $600, 2023-span $84 | overlap cluster 788 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba/SS_KB_ASIA_t60_s75 [BA bracket-assign rows] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows_SS_KB_ASIA_t60_s75.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 704 trades (9.4/wk) mean $1445/trade (MDE $1175), HOLD 321 trades mean $600, 2023-span $84 | overlap cluster 821 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_ea [ICT-IC (IC blocks)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_ea.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2417 trades (32.2/wk) mean $367/trade (MDE $300), HOLD 1364 trades mean $440, 2023-span $-274 | overlap cluster 251 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_30s_ec [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_30s_ec.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2207 trades (29.4/wk) mean $319/trade (MDE $262), HOLD 1298 trades mean $107, 2023-span $-147 | overlap cluster 268 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_M30_M1_close [ICT-SF (silver/fvg SF)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_M30_M1_close.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1937 trades (25.8/wk) mean $170/trade (MDE $139), HOLD 861 trades mean $285, 2023-span $-90 | overlap cluster 98 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_ed [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_ed.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2474 trades (33.0/wk) mean $330/trade (MDE $274), HOLD 1409 trades mean $309, 2023-span $66 | overlap cluster 254 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_eb [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1213 trades (16.2/wk) mean $371/trade (MDE $312), HOLD 600 trades mean $560, 2023-span $-237 | overlap cluster 275 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB7_PB5_depth_atr0.5_W15_s+0 [T-PB (pullback/PBX TP)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB7_PB5_depth_atr0.5_W15_s+0.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 342 trades (4.6/wk) mean $2372/trade (MDE $2020), HOLD 192 trades mean $905, 2023-span $777 | overlap cluster 0 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_ea [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_ea.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3455 trades (46.1/wk) mean $225/trade (MDE $193), HOLD 1939 trades mean $324, 2023-span $11 | overlap cluster 251 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB7_PB5_depth_atr0.5_W15_s-3 [T-PB (pullback/PBX TP)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB7_PB5_depth_atr0.5_W15_s-3.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 387 trades (5.2/wk) mean $1851/trade (MDE $1607), HOLD 215 trades mean $1570, 2023-span $898 | overlap cluster 24 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_15s_grAmL [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_15s_grAmL.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3710 trades (49.5/wk) mean $181/trade (MDE $158), HOLD 2075 trades mean $444, 2023-span $-159 | overlap cluster 228 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TB4W_03_time_15s_ST3_E20_1_T2_ntime14 [T-ENTRY pb4 (TB4)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/pb4/TB4W_03_time_15s_ST3_E20_1_T2_ntime14_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis mapped instr NQ | PRE 800 trades (10.7/wk) mean $1237/trade (MDE $1083), HOLD 369 trades mean $494, 2023-span $-106 | overlap cluster 976 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_ea_far0 [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_ea_far0.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1555 trades (20.7/wk) mean $265/trade (MDE $236), HOLD 743 trades mean $376, 2023-span $-62 | overlap cluster 270 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba2/SM_t60_sst [BA bracket-assign rows2] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows2_SM_t60_sst.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 264 trades (3.5/wk) mean $1539/trade (MDE $1380), HOLD 123 trades mean $459, 2023-span $953 | overlap cluster 802 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_1m_eb [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_1m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3389 trades (45.2/wk) mean $199/trade (MDE $180), HOLD 1718 trades mean $350, 2023-span $-323 | overlap cluster 233 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB7_PB_HMA55_EMA1_T2_W60_s-3 [T-PB (pullback/PBX TP)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB7_PB_HMA55_EMA1_T2_W60_s-3.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 432 trades (5.8/wk) mean $1462/trade (MDE $1362), HOLD 204 trades mean $653, 2023-span $646 | overlap cluster 31 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | SB_HM_tg_fib2618 [SB (silver-bullet SB)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SB/trades_SB_HM_tg_fib2618.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis CONSERVATIVE instr NQ | PRE 469 trades (6.3/wk) mean $1702/trade (MDE $1594), HOLD 232 trades mean $1403, 2023-span $-642 | overlap cluster 781 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_ea_shift60 [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_ea_shift60.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1642 trades (21.9/wk) mean $242/trade (MDE $232), HOLD 748 trades mean $379, 2023-span $-106 | overlap cluster 274 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba/SS_HM_NY_t60_s75 [BA bracket-assign rows] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows_SS_HM_NY_t60_s75.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 523 trades (7.0/wk) mean $1363/trade (MDE $1316), HOLD 237 trades mean $1134, 2023-span $358 | overlap cluster 820 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | E1C_KEL_range_40 [T-ENTRY e1] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/e1/E1C_KEL_range_40_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 1364 trades (18.2/wk) mean $871/trade (MDE $846), HOLD 613 trades mean $355, 2023-span $872 | overlap cluster 1020 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_1m_eb [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_1m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3817 trades (50.9/wk) mean $155/trade (MDE $151), HOLD 1631 trades mean $359, 2023-span $-186 | overlap cluster 233 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba2/EM_t50_s40 [BA bracket-assign rows2] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows2_EM_t50_s40.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 211 trades (2.8/wk) mean $1579/trade (MDE $1540), HOLD 85 trades mean $673, 2023-span $1171 | overlap cluster 771 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_eb [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 4200 trades (56.0/wk) mean $161/trade (MDE $157), HOLD 1963 trades mean $389, 2023-span $-125 | overlap cluster 252 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | tsoST10/r0.5 [TSO ST10] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/tso/ST10/rows_r0.5.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 712 trades (9.5/wk) mean $695/trade (MDE $679), HOLD 347 trades mean $159, 2023-span $360 | overlap cluster 809 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_5m_tg_so [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_5m_tg_so.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 822 trades (11.0/wk) mean $446/trade (MDE $438), HOLD 346 trades mean $727, 2023-span $57 | overlap cluster 287 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_5m_tg_pd_shift60 [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_5m_tg_pd_shift60.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 448 trades (6.0/wk) mean $1066/trade (MDE $1062), HOLD 205 trades mean $936, 2023-span $135 | overlap cluster 295 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB_HMA55_SWZ_T1 [T-PB (pullback/PBX TP)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB_HMA55_SWZ_T1.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 600 trades (8.0/wk) mean $1339/trade (MDE $1337), HOLD 261 trades mean $403, 2023-span $-121 | overlap cluster 51 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TR1A_ens_s0.5_k4 [T-TREND TR1] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TR1/trades_TR1A_ens_s0.5_k4.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED + DIRECT L2 instr NQ | PRE 522 trades (7.0/wk) mean $1383/trade (MDE $1408), HOLD 210 trades mean $393, 2023-span $-1490 | overlap cluster 640 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TR1B_reg5m_n20_t3_r0.5 [T-TREND TR1] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TR1/trades_TR1B_reg5m_n20_t3_r0.5.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 292 trades (3.9/wk) mean $1426/trade (MDE $1466), HOLD 140 trades mean $167, 2023-span $1069 | overlap cluster 670 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | H4M_k15_f0.5_s0.05 [H4 (trades_)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/H4/trades_H4M_k15_f0.5_s0.05.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 176 trades (2.3/wk) mean $2090/trade (MDE $2150), HOLD 72 trades mean $410, 2023-span $-178 | overlap cluster 760 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_1m_eb [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_1m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2467 trades (32.9/wk) mean $164/trade (MDE $171), HOLD 1330 trades mean $346, 2023-span $-135 | overlap cluster 260 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_30s_eb [ICT-IC (IC blocks)] | session PREOPEN entries only, 08:30-09:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_30s_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 716 trades (9.5/wk) mean $406/trade (MDE $423), HOLD 294 trades mean $550, 2023-span $-132 | overlap cluster 267 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_ea_shift60 [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_ea_shift60.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1283 trades (17.1/wk) mean $366/trade (MDE $383), HOLD 599 trades mean $318, 2023-span $-251 | overlap cluster 274 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba2/ST_t40_s60 [BA bracket-assign rows2] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows2_ST_t40_s60.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 1111 trades (14.8/wk) mean $734/trade (MDE $776), HOLD 579 trades mean $1004, 2023-span $-385 | overlap cluster 809 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_3m_ea_far0 [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_3m_ea_far0.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2554 trades (34.1/wk) mean $180/trade (MDE $191), HOLD 1204 trades mean $461, 2023-span $-116 | overlap cluster 237 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | H4M_k10_f0.75_s0.02 [H4 (trades_)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/H4/trades_H4M_k10_f0.75_s0.02.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 253 trades (3.4/wk) mean $1667/trade (MDE $1782), HOLD 112 trades mean $557, 2023-span $912 | overlap cluster 754 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_M15_M1_close [ICT-SF (silver/fvg SF)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_M15_M1_close.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2246 trades (29.9/wk) mean $128/trade (MDE $137), HOLD 1183 trades mean $265, 2023-span $-128 | overlap cluster 93 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_5m_eb [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_5m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1391 trades (18.5/wk) mean $264/trade (MDE $283), HOLD 669 trades mean $477, 2023-span $-273 | overlap cluster 243 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_ea_merged [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_ea_merged.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 365 trades (4.9/wk) mean $556/trade (MDE $597), HOLD 163 trades mean $239, 2023-span $-211 | overlap cluster 271 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB6_ST5m_EMA20_1m_T1 [T-PB (pullback/PBX TP)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB6_ST5m_EMA20_1m_T1.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 693 trades (9.2/wk) mean $959/trade (MDE $1032), HOLD 310 trades mean $1115, 2023-span $-764 | overlap cluster 20 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_f_deliv [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_f_deliv.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 417 trades (5.6/wk) mean $439/trade (MDE $476), HOLD 186 trades mean $505, 2023-span $-56 | overlap cluster 278 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_ea [ICT-IC (IC blocks)] | session PREOPEN entries only, 08:30-09:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_ea.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 248 trades (3.3/wk) mean $928/trade (MDE $1008), HOLD 119 trades mean $531, 2023-span $66 | overlap cluster 270 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TE7_emax5m_f20_s50 [T-BRACKET entries] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/bracket/entries/TE7_emax5m_f20_s50_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 221 trades (2.9/wk) mean $1689/trade (MDE $1833), HOLD 88 trades mean $1335, 2023-span $375 | overlap cluster 1039 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_tg_pd [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_tg_pd.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 549 trades (7.3/wk) mean $874/trade (MDE $951), HOLD 239 trades mean $1197, 2023-span $-610 | overlap cluster 270 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_1m_tg_liq [ICT-IC (IC blocks)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_1m_tg_liq.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1467 trades (19.6/wk) mean $407/trade (MDE $446), HOLD 683 trades mean $245, 2023-span $108 | overlap cluster 259 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TB4B_tick_28_tick_2000_ST10_E20_1_T3 [T-ENTRY pb4 (TB4)] | session NY-PM entries only, 12:00-15:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/pb4/TB4B_tick_28_tick_2000_ST10_E20_1_T3_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis mapped instr NQ | PRE 449 trades (6.0/wk) mean $1163/trade (MDE $1279), HOLD 170 trades mean $1556, 2023-span $-89 | overlap cluster 886 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_15s_grBL [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_15s_grBL.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1955 trades (26.1/wk) mean $223/trade (MDE $247), HOLD 924 trades mean $288, 2023-span $-265 | overlap cluster 230 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_3m_eb [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_3m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2134 trades (28.5/wk) mean $188/trade (MDE $209), HOLD 925 trades mean $131, 2023-span $-166 | overlap cluster 239 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB_HMA55_EMA1_T2 [T-PB (pullback/PBX TP)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB_HMA55_EMA1_T2.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 608 trades (8.1/wk) mean $1147/trade (MDE $1281), HOLD 281 trades mean $733, 2023-span $240 | overlap cluster 29 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB_HMA55_SWZ_T3 [T-PB (pullback/PBX TP)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB_HMA55_SWZ_T3.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 611 trades (8.1/wk) mean $1062/trade (MDE $1188), HOLD 280 trades mean $602, 2023-span $-1568 | overlap cluster 53 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB6_ST3m_EMA20_2m_T1 [T-PB (pullback/PBX TP)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB6_ST3m_EMA20_2m_T1.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 645 trades (8.6/wk) mean $1143/trade (MDE $1297), HOLD 280 trades mean $1026, 2023-span $-180 | overlap cluster 17 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_3m_eb [ICT-IC (IC blocks)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_3m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1196 trades (15.9/wk) mean $386/trade (MDE $438), HOLD 503 trades mean $160, 2023-span $-294 | overlap cluster 239 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_5m_eb [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_5m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 898 trades (12.0/wk) mean $297/trade (MDE $337), HOLD 417 trades mean $604, 2023-span $-21 | overlap cluster 288 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_M15_M1_close_ib [ICT-SF (silver/fvg SF)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_M15_M1_close_ib.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 984 trades (13.1/wk) mean $164/trade (MDE $186), HOLD 476 trades mean $286, 2023-span $-264 | overlap cluster 94 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_H1_M5_close [ICT-SF (silver/fvg SF)] | session PREOPEN entries only, 08:30-09:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_H1_M5_close.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 230 trades (3.1/wk) mean $845/trade (MDE $963), HOLD 92 trades mean $334, 2023-span $-258 | overlap cluster 78 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_eb [ICT-IC (IC blocks)] | session PREOPEN entries only, 08:30-09:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 250 trades (3.3/wk) mean $660/trade (MDE $753), HOLD 121 trades mean $656, 2023-span $170 | overlap cluster 275 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TB4C_range_24_range_80_ST5_SW38_T1 [T-ENTRY pb4 (TB4)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/pb4/TB4C_range_24_range_80_ST5_SW38_T1_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis mapped instr NQ | PRE 595 trades (7.9/wk) mean $1268/trade (MDE $1453), HOLD 266 trades mean $728, 2023-span $84 | overlap cluster 911 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB_HMA55_EMA1_T3 [T-PB (pullback/PBX TP)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB_HMA55_EMA1_T3.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 661 trades (8.8/wk) mean $1050/trade (MDE $1218), HOLD 306 trades mean $717, 2023-span $-1661 | overlap cluster 46 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_15m_ea [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_15m_ea.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 608 trades (8.1/wk) mean $714/trade (MDE $831), HOLD 291 trades mean $179, 2023-span $-275 | overlap cluster 217 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_1m_eb [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_1m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2931 trades (39.1/wk) mean $191/trade (MDE $224), HOLD 1303 trades mean $365, 2023-span $-124 | overlap cluster 260 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_15m_ec [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_15m_ec.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 371 trades (4.9/wk) mean $872/trade (MDE $1025), HOLD 171 trades mean $625, 2023-span $-195 | overlap cluster 221 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PRO1_AGG_RL3_EMA200_VWAP [T-PRO1] | session NY-PM entries only, 12:00-15:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/PRO1/trades_PRO1_AGG_RL3_EMA200_VWAP.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis mapped instr NQ | PRE 134 trades (1.8/wk) mean $2073/trade (MDE $2439), HOLD 46 trades mean $1221, 2023-span $-2063 | overlap cluster 490 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba3/seq_KB_LONDON_t30_s60 [BA bracket-assign rows3] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows3/seq_KB_LONDON_t30_s60.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 811 trades (10.8/wk) mean $728/trade (MDE $859), HOLD 361 trades mean $503, 2023-span $330 | overlap cluster 788 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB7_PB_HMA55_EMA1_T1_W60_s-3 [T-PB (pullback/PBX TP)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB7_PB_HMA55_EMA1_T1_W60_s-3.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 647 trades (8.6/wk) mean $988/trade (MDE $1172), HOLD 285 trades mean $388, 2023-span $53 | overlap cluster 28 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | d4a/x_don_trades_oco [D4a rows (pts)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/d4a/x_don_trades_oco.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 423 trades (5.6/wk) mean $1337/trade (MDE $1588), HOLD 204 trades mean $1872, 2023-span $551 | overlap cluster 1052 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | H4M_k10_f0.5_s0.1 [H4 (trades_)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/H4/trades_H4M_k10_f0.5_s0.1.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 225 trades (3.0/wk) mean $1670/trade (MDE $2003), HOLD 102 trades mean $1838, 2023-span $749 | overlap cluster 753 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba2/KB_t90_s90 [BA bracket-assign rows2] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows2_KB_t90_s90.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 567 trades (7.6/wk) mean $1862/trade (MDE $2236), HOLD 252 trades mean $733, 2023-span $1997 | overlap cluster 788 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TR1E_bos_1m_c2 [T-TREND TR1] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TR1/trades_TR1E_bos_1m_c2.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 670 trades (8.9/wk) mean $874/trade (MDE $1053), HOLD 308 trades mean $973, 2023-span $-1216 | overlap cluster 719 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_30s_eb [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_30s_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3614 trades (48.2/wk) mean $150/trade (MDE $183), HOLD 1664 trades mean $505, 2023-span $-49 | overlap cluster 267 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | G2_BE_p20 [T4-G2 bracket variants] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/t4/G2/PB3F_D_R3_P2_60_2R_bracket/G2_BE_p20.tr.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 523 trades (7.0/wk) mean $5/trade (MDE $6), HOLD 254 trades mean $4, 2023-span $0 | overlap cluster 1034 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | E1C_KEL_unirenko_40_60 [T-ENTRY e1] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/e1/E1C_KEL_unirenko_40_60_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 450 trades (6.0/wk) mean $1101/trade (MDE $1354), HOLD 153 trades mean $627, 2023-span $-267 | overlap cluster 1029 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB7_PB_HMA55_EMA1_T2_W15_s+0 [T-PB (pullback/PBX TP)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB7_PB_HMA55_EMA1_T2_W15_s+0.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 460 trades (6.1/wk) mean $1136/trade (MDE $1409), HOLD 198 trades mean $427, 2023-span $505 | overlap cluster 29 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PRO_ST10_AVWAP_flip_T2 [T-PRO2] | session NY-PM entries only, 12:00-15:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/PRO2/trades_PRO_ST10_AVWAP_flip_T2.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 165 trades (2.2/wk) mean $1655/trade (MDE $2057), HOLD 73 trades mean $1538, 2023-span $-182 | overlap cluster 575 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TR1A_ens_s1.0_k3 [T-TREND TR1] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TR1/trades_TR1A_ens_s1.0_k3.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED + DIRECT L2 instr NQ | PRE 607 trades (8.1/wk) mean $1029/trade (MDE $1287), HOLD 285 trades mean $541, 2023-span $-18 | overlap cluster 641 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TB4D_volume_07_volume_500_ST15_E20_1_T1 [T-ENTRY pb4 (TB4)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/pb4/TB4D_volume_07_volume_500_ST15_E20_1_T1_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis mapped instr NQ | PRE 1111 trades (14.8/wk) mean $675/trade (MDE $846), HOLD 494 trades mean $704, 2023-span $108 | overlap cluster 924 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | H4M_k15_f0.5_s0.1 [H4 (trades_)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/H4/trades_H4M_k15_f0.5_s0.1.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 188 trades (2.5/wk) mean $1717/trade (MDE $2156), HOLD 71 trades mean $873, 2023-span $69 | overlap cluster 761 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_tg_pd_shift60 [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_tg_pd_shift60.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 599 trades (8.0/wk) mean $650/trade (MDE $816), HOLD 276 trades mean $1120, 2023-span $-91 | overlap cluster 285 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PRO3B_OPEN0930_DRV38_T1 [T-PRO3] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/PRO3/trades_PRO3B_OPEN0930_DRV38_T1.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis mapped instr NQ | PRE 219 trades (2.9/wk) mean $1926/trade (MDE $2421), HOLD 100 trades mean $1991, 2023-span $-551 | overlap cluster 630 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba3/seq_PE_ASIA_t45_s40 [BA bracket-assign rows3] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows3/seq_PE_ASIA_t45_s40.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 753 trades (10.0/wk) mean $668/trade (MDE $843), HOLD 361 trades mean $612, 2023-span $-552 | overlap cluster 795 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB7_PB_HMA55_EMA1_T1_W15_s-3 [T-PB (pullback/PBX TP)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB7_PB_HMA55_EMA1_T1_W15_s-3.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 512 trades (6.8/wk) mean $1128/trade (MDE $1435), HOLD 221 trades mean $983, 2023-span $388 | overlap cluster 28 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_grAmS [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_grAmS.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3168 trades (42.2/wk) mean $165/trade (MDE $209), HOLD 1784 trades mean $341, 2023-span $-128 | overlap cluster 255 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_M30_M1_close_ib [ICT-SF (silver/fvg SF)] | session NY-PM entries only, 12:00-15:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_M30_M1_close_ib.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 598 trades (8.0/wk) mean $325/trade (MDE $417), HOLD 219 trades mean $1113, 2023-span $-295 | overlap cluster 99 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_ea_mirror [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_ea_mirror.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1607 trades (21.4/wk) mean $221/trade (MDE $284), HOLD 739 trades mean $431, 2023-span $-84 | overlap cluster 272 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TB4B_tick_17_tick_1000_ST60_SW38_T3 [T-ENTRY pb4 (TB4)] | session PREOPEN entries only, 08:30-09:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/pb4/TB4B_tick_17_tick_1000_ST60_SW38_T3_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis mapped instr NQ | PRE 118 trades (1.6/wk) mean $2341/trade (MDE $3028), HOLD 39 trades mean $2497, 2023-span $-327 | overlap cluster 876 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_tg_eq2 [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_tg_eq2.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 333 trades (4.4/wk) mean $721/trade (MDE $937), HOLD 104 trades mean $426, 2023-span $-346 | overlap cluster 282 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | H4M_k5_f0.25_s0.1 [H4 (trades_)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/H4/trades_H4M_k5_f0.25_s0.1.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 238 trades (3.2/wk) mean $1474/trade (MDE $1920), HOLD 113 trades mean $842, 2023-span $-1458 | overlap cluster 766 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | BK_5m_ea_tg_sess [ICT-IC (IC blocks)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_BK_5m_ea_tg_sess.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 183 trades (2.4/wk) mean $1597/trade (MDE $2080), HOLD 81 trades mean $241, 2023-span $-472 | overlap cluster 206 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | BK_1m_eb [ICT-IC (IC blocks)] | session PREOPEN entries only, 08:30-09:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_BK_1m_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 267 trades (3.6/wk) mean $483/trade (MDE $635), HOLD 149 trades mean $638, 2023-span $-268 | overlap cluster 204 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_tg_pd_shift60 [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_tg_pd_shift60.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 724 trades (9.7/wk) mean $628/trade (MDE $827), HOLD 314 trades mean $677, 2023-span $-386 | overlap cluster 285 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba/SS_HM_ASIA_t75_s60 [BA bracket-assign rows] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows_SS_HM_ASIA_t75_s60.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 580 trades (7.7/wk) mean $1097/trade (MDE $1444), HOLD 270 trades mean $1478, 2023-span $-250 | overlap cluster 818 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | FV_15s_ea [ICT-IC (IC blocks)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_FV_15s_ea.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 3979 trades (53.1/wk) mean $123/trade (MDE $161), HOLD 1820 trades mean $205, 2023-span $-174 | overlap cluster 227 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_grBS [ICT-IC (IC blocks)] | session NY-PM entries only, 12:00-15:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_grBS.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1024 trades (13.7/wk) mean $421/trade (MDE $556), HOLD 416 trades mean $435, 2023-span $107 | overlap cluster 257 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | S3_B_N12_tf5m [ICT-SF (silver/fvg SF)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_S3_B_N12_tf5m.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 341 trades (4.5/wk) mean $992/trade (MDE $1313), HOLD 186 trades mean $1017, 2023-span $360 | overlap cluster 142 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | G2_BE_p10 [T4-G2 bracket variants] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/t4/G2/PB3F_D_R3_P2_60_2R_bracket/G2_BE_p10.tr.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 501 trades (6.7/wk) mean $3/trade (MDE $4), HOLD 245 trades mean $4, 2023-span $-1 | overlap cluster 1034 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_ec [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_ec.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2737 trades (36.5/wk) mean $179/trade (MDE $238), HOLD 1552 trades mean $272, 2023-span $113 | overlap cluster 253 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | SB_HM_st_sig0 [SB (silver-bullet SB)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SB/trades_SB_HM_st_sig0.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis CONSERVATIVE instr NQ | PRE 184 trades (2.5/wk) mean $2426/trade (MDE $3244), HOLD 99 trades mean $859, 2023-span $2835 | overlap cluster 783 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | G2_m40_r4_t8_s1 [T4-G2 bracket variants] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/t4/G2/PB3B_R5_P3/G2_m40_r4_t8_s1.tr.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 650 trades (8.7/wk) mean $4/trade (MDE $5), HOLD 295 trades mean $5, 2023-span $-3 | overlap cluster 1032 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TB4D_volume_21_volume_500_ST5_E20_1_T2 [T-ENTRY pb4 (TB4)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/pb4/TB4D_volume_21_volume_500_ST5_E20_1_T2_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis mapped instr NQ | PRE 549 trades (7.3/wk) mean $1000/trade (MDE $1341), HOLD 253 trades mean $1465, 2023-span $-301 | overlap cluster 938 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB_HMA55_SWZ_T2 [T-PB (pullback/PBX TP)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB_HMA55_SWZ_T2.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis DIRECT L2 instr NQ | PRE 578 trades (7.7/wk) mean $960/trade (MDE $1293), HOLD 245 trades mean $466, 2023-span $-79 | overlap cluster 52 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_15s_eb [ICT-IC (IC blocks)] | session NY-PM entries only, 12:00-15:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_15s_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 1556 trades (20.7/wk) mean $246/trade (MDE $332), HOLD 882 trades mean $373, 2023-span $-152 | overlap cluster 252 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | PB_EMA200_VWAP_T3 [T-PB (pullback/PBX TP)] | session NY-PM entries only, 12:00-15:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/TP/trades_PB_EMA200_VWAP_T3.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 128 trades (1.7/wk) mean $1894/trade (MDE $2576), HOLD 53 trades mean $364, 2023-span $-1143 | overlap cluster 45 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | ba/SS_SM_ASIA_t40_s60 [BA bracket-assign rows] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/ba/rows_SS_SM_ASIA_t40_s60.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 248 trades (3.3/wk) mean $1261/trade (MDE $1720), HOLD 116 trades mean $941, 2023-span $-236 | overlap cluster 825 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TB4C_range_00_range_40_ST3_E20_1_T1 [T-ENTRY pb4 (TB4)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/pb4/TB4C_range_00_range_40_ST3_E20_1_T1_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis mapped instr NQ | PRE 1133 trades (15.1/wk) mean $678/trade (MDE $930), HOLD 491 trades mean $814, 2023-span $565 | overlap cluster 888 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_H1_M1_close [ICT-SF (silver/fvg SF)] | session PREOPEN entries only, 08:30-09:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_H1_M1_close.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 216 trades (2.9/wk) mean $485/trade (MDE $669), HOLD 91 trades mean $398, 2023-span $-135 | overlap cluster 73 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | TE7_kelt3m_n14_m1.5 [T-BRACKET entries] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/bracket/entries/TE7_kelt3m_n14_m1.5_trades.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 684 trades (9.1/wk) mean $905/trade (MDE $1253), HOLD 307 trades mean $401, 2023-span $-10 | overlap cluster 1048 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_30s_eb [ICT-IC (IC blocks)] | session NY-AM entries only, 09:30-12:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_30s_eb.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 2593 trades (34.6/wk) mean $179/trade (MDE $249), HOLD 1274 trades mean $518, 2023-span $-107 | overlap cluster 267 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_5m_tg_pd_shift60 [ICT-IC (IC blocks)] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_5m_tg_pd_shift60.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 479 trades (6.4/wk) mean $714/trade (MDE $994), HOLD 210 trades mean $1344, 2023-span $-329 | overlap cluster 295 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_30s_ea [ICT-IC (IC blocks)] | session PREOPEN entries only, 08:30-09:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_30s_ea.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 632 trades (8.4/wk) mean $410/trade (MDE $572), HOLD 256 trades mean $556, 2023-span $13 | overlap cluster 266 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | CRT_H1_M1_ote [ICT-SF (silver/fvg SF)] | session LONDON entries only, 02:00-08:30 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/SF/trades_CRT_H1_M1_ote.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 347 trades (4.6/wk) mean $296/trade (MDE $414), HOLD 130 trades mean $378, 2023-span $-16 | overlap cluster 77 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | IF_3m_tg_eqm [ICT-IC (IC blocks)] | session NY-PM entries only, 12:00-15:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/IC/trades_IF_3m_tg_eqm.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis MAPPED instr NQ | PRE 437 trades (5.8/wk) mean $603/trade (MDE $845), HOLD 196 trades mean $605, 2023-span $-298 | overlap cluster 283 | start: shadow/paper from the next label week, no live change

- FORWARD-REGISTER (session book, text only; main to enter) | G2_m40_r3_t8_s1 [T4-G2 bracket variants] | session ASIA entries only, 18:00-02:00 ET, flat rule: no entries outside the window; exits run to the source bracket/exit as in ds3/out/t4/G2/PRO_Z20_t1.0/G2_m40_r3_t8_s1.tr.parquet | tier SESSION-CANDIDATE (BOF:not cleared) | CANDIDATE lots = 0.5 x PASS lots | basis rows-as-stored instr NQ | PRE 1049 trades (14.0/wk) mean $3/trade (MDE $4), HOLD 497 trades mean $4, 2023-span $3 | overlap cluster 601 | start: shadow/paper from the next label week, no live change

## 8. Reading guide / honest caveats
- 'Alive' here means: positive and CI above 0 on PRE in that session, positive on HOLD overall and in both HOLD year-segments. It is not a stack-add verdict (item 3 does that) and it ignores fills at live latency; the ICT/IC and CRT 15s-30s cells in particular were labelled DEAD/CANDIDATE on pooled all-hours numbers from engines with stored (not live-latency) fills.
- The 2023 span is negative for most alive ASIA/LONDON cells: if the program is regime-dependent, 2023 is the contrary year; this is printed beside every cell and left to the reader.
- Duplicates: many cells are the same trades; use the cluster column.


## B-section washout: dead pooled, alive in a session (31 independent; 2026-10-28T19:16:13Z)
Source DS3_SESSION2_B_washout.md. Basis per that report.
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | x_mean | y2023_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| WO_TE7_boll3m_n30_m1.5_rsi_b5_k18 | NY-AM | 169 | 2.25 | 2731 | 2459 | 3.11 | 75.0 | 1039 | -1897 | -1907 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1365 | 104 |
| WO_TE1B_emax_5m_pb_b5_x1.5_k10 | NY-AM | 209 | 2.79 | 1984 | 1845 | 3.01 | 84.0 | 1367 | 698 | 878 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 943 | 88 |
| WO_SM_cci_b5_n27_k10 | NY-AM | 127 | 1.69 | 2861 | 2680 | 2.99 | 61.0 | 679 | -398 | -244 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1462 | 76 |
| WO_PB3E_R3_P2_40_1.5R_pb_b5_x1.5_k10 | ASIA | 473 | 6.31 | 1158 | 1086 | 2.99 | 206 | 330 | 366 | 414 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 652 | 34 |
| WO_TE7_kelt3m_n30_m1.0_cci_b3_n14_k18 | ASIA | 473 | 6.31 | 1552 | 1469 | 2.96 | 213 | 436 | -410 | -614 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 578 | 114 |
| WO_TE7_boll3m_n30_m1.5_pb_b5_x1.0_k10 | NY | 1328 | 17.7 | 752 | 717 | 2.94 | 588 | 51.3 | -496 | -695 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 540 | 104 |
| WO_HM_cci_b1_n14_k10 | ASIA | 339 | 4.52 | 1782 | 1777 | 2.81 | 153 | 1242 | -144 | -241 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 928 | 5 |
| WO_TE7_kelt3m_n14_m1.5_cci_b5_n20_k18 | ASIA | 307 | 4.09 | 1754 | 1763 | 2.79 | 179 | 266 | -1951 | -1812 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 639 | 108 |
| WO_SM_cci_b5_n20_k30 | ASIA | 171 | 2.28 | 2331 | 2369 | 2.76 | 86.0 | 327 | 497 | 394 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 794 | 76 |
| WO_KB_rsi_b3_k18 | NY | 258 | 3.44 | 1806 | 1858 | 2.72 | 96.0 | 455 | -60.2 | -364 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1112 | 9 |
| WO_KB_rsi_b3_k10 | NY | 105 | 1.40 | 2881 | 3011 | 2.68 | 41.0 | 335 | -853 | -1302 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 2125 | 10 |
| WO_PB3B_R5_P1_cci_b1_n14_k18 | ASIA | 521 | 6.95 | 1245 | 1311 | 2.66 | 236 | 1287 | -1159 | -1206 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 88.6 | 18 |
| WO_PRO2_RIB1m_q30_cci_b1_n14_k10 | ASIA | 210 | 2.80 | 2114 | 2276 | 2.60 | 89.0 | 1635 | 276 | 23.6 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1089 | 56 |
| WO_TE6_st10m_n10_m3.5_cci_b5_n40_k10 | NY | 132 | 1.76 | 2161 | 2336 | 2.59 | 64.0 | 812 | -1732 | -1304 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 885 | 76 |
| WO_TE7_kelt3m_n14_m1.5_cci_b3_n40_k10 | NY-AM | 158 | 2.11 | 2287 | 2494 | 2.57 | 88.0 | 1116 | -1953 | -2085 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 506 | 108 |
| WO_HM_pb_b5_x1.5_k10 | NY-AM | 508 | 6.77 | 1065 | 1168 | 2.55 | 232 | 599 | 50.3 | 76.3 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 365 | 5 |
| WO_TE1_kelt_3m_rsi_b5_k18 | NY-AM | 174 | 2.32 | 2085 | 2286 | 2.55 | 66.0 | 1724 | -812 | -701 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 996 | 92 |
| WO_EM_cci_b5_n27_k30 | NY | 281 | 3.75 | 1455 | 1612 | 2.53 | 117 | 1097 | -12.8 | -120 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 770 | 1 |
| WO_TE1B_emax_5m_cci_b5_n27_k18 | NY | 255 | 3.40 | 1438 | 1606 | 2.51 | 100 | 1476 | -57.8 | -199 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1251 | 88 |
| WO_PRO2_Z20_t1.0_cci_b5_n20_k30 | ASIA | 579 | 7.72 | 925 | 1079 | 2.40 | 279 | 1084 | 696 | 641 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 86.7 | 65 |
| WO_TE7_kelt3m_n30_m1.0_rsi_b5_k18 | NY-AM | 187 | 2.49 | 1813 | 2160 | 2.35 | 73.0 | 1074 | -229 | -87.1 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1045 | 114 |
| WO_TE1B_emax_5m_cci_b5_n40_k10 | NY-AM | 114 | 1.52 | 1954 | 2348 | 2.33 | 51.0 | 1549 | -2436 | -2436 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 772 | 87 |
| WO_TE1_kelt_3m_rsi_b3_k18 | NY-AM | 102 | 1.36 | 2349 | 2837 | 2.32 | 38.0 | 752 | -1680 | -1488 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1523 | 94 |
| WO_TE7_boll3m_n20_m1.5_pb_b3_x1.5_k10 | NY | 1268 | 16.9 | 711 | 859 | 2.32 | 548 | 251 | -187 | -331 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 579 | 101 |
| WO_TE1_kelt_3m_rsi_b3_k18 | NY | 146 | 1.95 | 2034 | 2480 | 2.30 | 51.0 | 251 | -977 | -1061 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1523 | 94 |
| WO_EM_pb_b5_x1.5_k10 | NY-AM | 180 | 2.40 | 1641 | 2092 | 2.20 | 77.0 | 415 | 1402 | 1474 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 813 | 1 |
| WO_TE1_kelt_3m_cci_b5_n40_k10 | NY | 385 | 5.13 | 1199 | 1541 | 2.18 | 167 | 182 | -1253 | -1241 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1142 | 92 |
| WO_TE3_ice_q99_pb_b5_x1.5_k10 | NY | 506 | 6.75 | 985 | 1272 | 2.17 | 251 | 776 | 926 | 1114 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1001 | 100 |
| WO_TE7_kelt3m_n30_m1.0_rsi_b3_k18 | NY | 181 | 2.41 | 1647 | 2154 | 2.14 | 59.0 | 1173 | -2354 | -2566 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1219 | 114 |
| WO_ST_pb_b5_x1.5_k10 | NY | 1411 | 18.8 | 594 | 792 | 2.10 | 674 | 925 | -96.7 | -59.7 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 372 | 78 |
| WO_PB3E_R3_P2_40_1.5R_cci_b5_n40_k18 | NY-AM | 174 | 2.32 | 1695 | 2260 | 2.10 | 90.0 | 915 | -287 | 267 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1014 | 34 |


## B-section pyramid: dead pooled, alive in a session (2 independent; 2026-10-28T20:52:20Z)
Source DS3_SESSION2_B_pyramid.md. Basis per that report.
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | x_mean | y2023_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T4PY_PB3B_R5_P1_D1_PB_f50_m1_s30_G1 | ASIA | 806 | 10.7 | 1061 | 1264 | 2.35 | 387 | 1266 | -637 | -744 | SESSION-CANDIDATE | BOF:not cleared | nan | -114 | 6 |
| T4PY_PB3B_R5_P3_D2_N20_f50_m1_s30_G1 | ASIA | 898 | 12.0 | 539 | 722 | 2.09 | 429 | 78.6 | -481 | -521 | SESSION-CANDIDATE | BOF:not cleared | nan | -20.7 | 5 |


## B-section tb: dead pooled, alive in a session (3 independent; 2026-10-28T20:54:15Z)
Source DS3_SESSION2_B_tb.md. Basis per that report.
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | x_mean | y2023_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB1_ST_k15_T_N | NY-AM | 361 | 4.81 | 2295 | 2116 | 3.04 | 139 | 420 | -586 | -576 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 411 | 2 |
| TB1_ST_k5_T_N | NY | 605 | 8.07 | 1218 | 1601 | 2.13 | 218 | 688 | 34.9 | -139 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 245 | 17 |
| TB7_ORBNY_k1_T_N | NY-AM | 609 | 8.12 | 1145 | 1538 | 2.08 | 248 | 567 | 109 | 294 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 588 | 131 |


## Section: T-OPEN B2 (D3SB1, item B1) - dead pooled, alive in a session
11,941 cells with entry clock re-scored by session and 09:30-11:00 sub-window (prereg sha 766047a3...99ac, PREHOLD sha 42ad1b9b7989...). SESSION-CANDIDATE 938 cell-windows / 44 clusters (SESSION-PASS 0); MEASURED-alive 823 / 41 clusters; all NY-AM or its sub-windows; 730 alive windows fail the harness beats_beta gate. Report DS3_SESSION2_B_TOPEN.md.
| cell | window | n | tpw | PRE mean $ | MDE $ | t | HOLD n | HOLD mean | H25 | H26 | 2023 span | 2023 | 2024 | 2025 | PRE meas | HOLD meas | HOLD 2x | tier | tier MEAS | failed gate | BOF | pooled verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DR15m_pb3_mv10__c2_X20_120 | W2_0945-1000 | 290 | 3.9 | 2,496 | 1,736 | 4.02 | 118 | 2,024 | 1,036 | 6,587 | -408 | -388 | 2,796 | 1,289 | 1,951 | 1,917 | 1,776 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X20_120 | NY-AM | 304 | 4.1 | 2,390 | 1,682 | 3.98 | 126 | 1,858 | 960 | 6,102 | -395 | -349 | 2,553 | 1,299 | 1,860 | 1,740 | 1,610 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_90 | W2_0945-1000 | 290 | 3.9 | 2,063 | 1,493 | 3.87 | 118 | 1,100 | 427 | 4,209 | 124 | 314 | 2,173 | 910 | 1,617 | 505 | 852 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_90 | NY-AM | 304 | 4.1 | 1,976 | 1,489 | 3.72 | 126 | 1,164 | 619 | 3,740 | 151 | 218 | 2,118 | 1,000 | 1,540 | 583 | 916 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv10__c3_X60_120 | NY-AM | 261 | 3.5 | 3,755 | 2,879 | 3.65 | 105 | 847 | 345 | 2,984 | -419 | -353 | 3,115 | 2,401 | 3,639 | 442 | 599 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c3_X40_120 | NY-AM | 304 | 4.1 | 2,999 | 2,300 | 3.65 | 126 | 1,822 | 1,087 | 5,297 | 367 | 337 | 3,107 | 1,794 | 3,029 | 1,505 | 1,574 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| LV_RN_BH_F60 | NY-AM | 160 | 2.1 | 2,699 | 2,075 | 3.64 | 89 | 690 | 192 | 3,362 | 359 | -157 | 3,339 | 826 | 2,021 | 142 | 442 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c3_X40_120 | W2_0945-1000 | 290 | 3.9 | 3,025 | 2,327 | 3.64 | 118 | 1,786 | 888 | 5,935 | 337 | 466 | 3,039 | 1,713 | 2,958 | 1,472 | 1,538 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| OR15m_stp_le1_F60 | NY-AM | 179 | 2.4 | 2,579 | 1,987 | 3.63 | 72 | 1,560 | 869 | 5,393 | -1,627 | -1,595 | 2,727 | 1,326 | 2,190 | 978 | 1,312 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv20_F60 | W2_0945-1000 | 188 | 2.5 | 2,789 | 2,162 | 3.61 | 90 | 864 | 789 | 1,129 | -399 | -439 | 2,811 | 1,559 | 2,128 | 565 | 616 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv20_F60 | NY-AM | 208 | 2.8 | 2,786 | 2,167 | 3.60 | 97 | 1,169 | 1,179 | 1,129 | -320 | -411 | 2,513 | 2,058 | 2,145 | 841 | 920 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_hl_mv20_F45 | W2_0945-1000 | 188 | 2.5 | 2,135 | 1,666 | 3.59 | 90 | 1,634 | 1,606 | 1,732 | -538 | -223 | 1,932 | 1,620 | 1,457 | 1,034 | 1,385 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_120 | W2_0945-1000 | 290 | 3.9 | 2,436 | 1,908 | 3.58 | 118 | 1,150 | 306 | 5,051 | 202 | 484 | 2,940 | 592 | 2,255 | 963 | 691 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |
| PB_ORX_T_SCALE | NY-AM | 119 | 1.6 | 3,107 | 2,466 | 3.53 | 58 | 573 | 655 | 258 | -288 | -344 | 3,528 | 1,167 | 3,033 | 326 | 324 | SESSION-CANDIDATE | FAILS-MEASURED | - | BOF:not cleared | DEAD |
| DR15m_pb3_mv10__c2_X30_120 | NY-AM | 304 | 4.1 | 2,388 | 1,895 | 3.53 | 126 | 1,293 | 605 | 4,546 | 294 | 419 | 2,925 | 768 | 2,208 | 1,107 | 829 | SESSION-CANDIDATE | SESSION-CANDIDATE | - | BOF:not cleared | DEAD |



## B-section te2: dead pooled, alive in a session (2 independent; 2026-10-28T20:57:21Z)
Source DS3_SESSION2_B_te2.md. Basis per that report.
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | x_mean | y2023_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TE2_NQ_ST_k15 | NY-AM | 523 | 6.97 | 1293 | 1150 | 3.15 | 197 | 774 | 246 | 220 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 91.3 | 167 |
| TE2_NQ_ST_k15 | NY | 725 | 9.67 | 854 | 907 | 2.63 | 243 | 747 | 342 | 188 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 91.3 | 167 |


## B-section tb2: dead pooled, alive in a session (2 independent; 2026-10-28T20:59:04Z)
Source DS3_SESSION2_B_tb2.md. Basis per that report.
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | x_mean | y2023_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB6_t1000_follow_L31 | NY-AM | 363 | 4.84 | 1325 | 1517 | 2.45 | 157 | 369 | -1083 | -1313 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1325 | 40 |
| TB6_t1000_follow_L31 | NY | 363 | 4.84 | 1325 | 1517 | 2.45 | 157 | 369 | -1083 | -1313 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1325 | 40 |


## B-section tr2: dead pooled, alive in a session (1 independent; 2026-10-28T20:59:33Z)
Source DS3_SESSION2_B_tr2.md. Basis per that report.
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | x_mean | y2023_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR2_KB_LV1 | NY-AM | 445 | 5.93 | 1025 | 1367 | 2.10 | 196 | 934 | -598 | -785 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 375 | 15 |


## B-section tr4: dead pooled, alive in a session (2 independent; 2026-10-28T20:59:35Z)
Source DS3_SESSION2_B_tr4.md. Basis per that report.
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | x_mean | y2023_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R5_QUIET_KB | NY-PM | 188 | 2.51 | 2227 | 2369 | 2.63 | 95.0 | 338 | 318 | -635 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 864 | 19 |
| R5_DW_HM | NY-AM | 217 | 2.89 | 1500 | 1837 | 2.29 | 79.0 | 1236 | -835 | -845 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 774 | 2 |
