# DS3_BLOCKED_SHADOW - value of the Shadow trades the live no-new-entry windows would block, and the restated DIS-AJ family test (DIS-BU, Z1, 2026-11-04T23:32Z; research only, no PASS claims, nothing live)
Scope note l2vast/ds3/prereg/DISBU_scope.md sha256 299ed68c05e4a48d452f9c5ad355fcb6b8a84c3bffc38c5a8041a19454730e91 and addendum 1 sha256 9e4787fb8111dde368c00f260c6d413640613d153b3d110bb9fad9ce4bbe7f70 (both in DECISIONS.md before any number); ledger DIS_BU; n_tested line DISBU; code l2vast/ds3/code/disbu/ (bu_lib, bu_prep, bu_run, bu_an, bu_seeds, bu_seed_an, bu_lots, bu_doc); results /mnt/l2/l2vast/ds3_base4/disbu_*.pkl/csv. The stack under the same windows is ZL-2 DIS-BJ / BASE-4 DIS-BR: NOT recomputed here, so no stack-marginal or maxDD-change column is restated.
## 0. Plain sentence
**Under the 09:00-09:59 block the NY-AM fade bundle (now essentially VWAPF + ORBF; ONRTH keeps 5 of 543 trades) loses its only family-level clearance in L6M (family p L6M 0.14-0.21 over five seeds, was 0.04-0.10; HOLD stays 0.005-0.01) and is a per-cell survivor with a significant excess; N_REL_rev, Q13GAP_T1, the Q4 amplifiers and the DIS-Q late-day books are blocked entirely (their research P&L is not obtainable live), DISE_PDF, G1, DIS-J, OR15NYAM_T2 and the Z1 swing line lose 36-67% of their trades and their remaining excess weakens to DRIFT-EXPLAINED or per-cell only; the 18:00-18:05 and 15:00-16:54 windows and the 18:05/18:06 edge change almost nothing (PDASIA_T2 loses 5 trades at edge-B, VB2 NYPM T1 one).** Whether the 09:00-09:59 block is live for D6/D7 is the open user question; if it is not (the 10-22 "no RTH-open block" reading) nothing here changes (W2/W0 = DIS-AJ).
## 1. Variants, edges, method (as logged)
Entry minute m = ET minute of the order bar (signal bar closes at m:00). L = no block (the DIS-AJ lists). **W0** = 09:00-09:29 + 15:00-16:54 (engine as is). **W2A / W2B** = W0 + 18:00-18:05 (edge-A, m <= 18:05) / + 18:06 (edge-B). **W1A / W1B** = W2 + 09:30-09:59 (the recorded live windows; B = edge-B). **W1A-10 / W1B-10** = also block the 10:00 minute (the "09:00-10:00 block" wording of the 10-31 texts). Variants that remove the same trades share one computation. Lists = the 21 DIS-AJ cells (disy_lists.build) + DIS-Q 15:50 DRIFT (value only) + the bundle ex-ONRTH. Statistics as DIS-AJ: weekly $ (gate_v3 windows, carrying weeks dropped, FadeHarness live fills, the lists' own lots), excess over the side-independent random-minute drift W1 redrawn among ALLOWED minutes only, W2 day shuffle, W3 matched clock, 200 worlds; family max-T over the 21 searched cells, family p = larger of W1- and W2-based. **Family treatment (stated both ways):** `searched` (headline) keeps the cells whose trades were all removed in the null maximum with their original worlds, because they were tried; `remaining` drops them (scope note text) and is more liberal. L variant reproduces the DIS-AJ labels (bundle CLEARS TRUE DRIFT + FAMILY, fam .060/.005).
**Monte-Carlo noise (important):** the per-cell family p depends on 200 simulated worlds; five independent seeds for the key cells give the ranges below, and the single-seed table in section 3 must be read with them.
| cell | variant | family p L6M min-max | family p HOLD min-max | seeds that CLEAR the family (of 5) |
|--|--|--|--|--|
| 01 Z1 swing failed break v2a | W1A | 0.557 - 0.657 | 0.259 - 0.537 | 0 |
| 08 DIS-J N_CENT NYAM | W1A | 0.055 - 0.100 | 0.816 - 0.900 | 0 |
| 15 NYAM fade ORBF (1 lot) | L | 0.139 - 0.219 | 0.139 - 0.289 | 0 |
| 15 NYAM fade ORBF (1 lot) | W1A-10 | 0.408 - 0.587 | 0.672 - 0.806 | 0 |
| 16 NYAM fade bundle (ONRTH+VWAPF+ORBF) | L | 0.040 - 0.100 | 0.005 - 0.005 | 5 |
| 16 NYAM fade bundle (ONRTH+VWAPF+ORBF) | W1A | 0.139 - 0.214 | 0.005 - 0.010 | 0 |
| 16 NYAM fade bundle (ONRTH+VWAPF+ORBF) | W1A-10 | 0.308 - 0.483 | 0.015 - 0.040 | 0 |
| 17 FADE VB2NYPM_T1 (1 lot) | L | 0.060 - 0.229 | 0.104 - 0.224 | 0 |
| 17 FADE VB2NYPM_T1 (1 lot) | W0 | 0.090 - 0.204 | 0.065 - 0.169 | 1 |
| 20 FADE OR15NYAM_T2 (1 lot) | W1A | 0.070 - 0.204 | 0.687 - 0.831 | 0 |
Reading: the bundle clears the family in 5 of 5 seeds under L (L6M family p .04-.10) and in 0 of 5 under W1A (.14-.21) and W1A-10 (.31-.48); VB2 NYPM T1 straddles .10 in every variant (0-1 of 5), so its single-seed "CLEARS" under W0/W1A is noise and its label stays CLEARS PER-CELL ONLY; DIS-J W1A is borderline per cell (HOLD p .085-.14); OR15NYAM_T2 W1A is borderline per cell (HOLD p ~.10).
## 2. How many trades are blocked, and what they were worth
Weekly $ (L6M / HOLD / PRE / X') at the lists' own research lots; "kept" = after removal, "removed" = the blocked trades alone (simulated by themselves, so values are not exactly additive where the harness skips overlapping trades). Equal-risk lots = clip(round(1200/(stop x 20)), 1, 6).
| cell | variants (same removal) | n kept / removed | kept: L6M HOLD PRE X' (research lots) | REMOVED alone: L6M HOLD PRE X' | kept equal-risk | removed equal-risk |
|--|--|--|--|--|--|--|
| 01 Z1 swing failed break v2a | W1A/W1B | 336 / 356 | +542 +450 +143 -27 | +297 -33 -133 -100 | +686 +522 +168 +30 | +282 -88 -138 -178 |
| 01 Z1 swing failed break v2a | W1A-10/W1B-10 | 334 / 358 | +542 +450 +128 +1 | +297 -33 -133 -129 | +686 +522 +155 +62 | +282 -88 -138 -209 |
| 03 DIS-B N_REL_rev_m0.5 NYAM | W1A/W1B/W1A-10/W1B-10 | 0 / 304 | n/a n/a n/a n/a | +1404 +1207 +144 -550 | n/a n/a n/a n/a | +648 +561 +158 -222 |
| 06 DIS-E prevday|FAILURE NYAM | W1A/W1B | 202 / 115 | +565 +254 +54 +106 | +796 +224 +259 -83 | +177 -54 +34 +74 | +390 +109 +205 -68 |
| 06 DIS-E prevday|FAILURE NYAM | W1A-10/W1B-10 | 199 / 118 | +652 +335 +59 +106 | +710 +143 +255 -83 | +226 -2 +41 +74 | +341 +57 +197 -68 |
| 07 DIS-G G1 ratio reversion NYAM | W1A/W1B | 339 / 691 | +436 +274 -80 +39 | +342 +499 +123 -321 | +596 +321 -121 -34 | +221 +416 +117 -415 |
| 07 DIS-G G1 ratio reversion NYAM | W1A-10/W1B-10 | 336 / 694 | +436 +324 -80 -13 | +342 +448 +123 -269 | +596 +376 -121 -87 | +221 +361 +117 -363 |
| 08 DIS-J N_CENT NYAM | W1A/W1B | 189 / 118 | +873 +254 -214 +0 | +399 +266 +65 +0 | +890 +225 -285 +0 | +399 +280 +44 +0 |
| 08 DIS-J N_CENT NYAM | W1A-10/W1B-10 | 187 / 120 | +873 +291 -202 +0 | +399 +266 +65 +0 | +890 +263 -273 +0 | +399 +280 +44 +0 |
| 09 DIS-Q 15:00 IMB fade | W0/W2A/W2B/W1A/W1B/W1A-10/W1B-10 | 0 / 881 | n/a n/a n/a n/a | +439 +1254 +511 +166 | n/a n/a n/a n/a | +224 +626 +254 +84 |
| 10 Q13 middle-tercile gap-fill | W1A/W1B/W1A-10/W1B-10 | 0 / 275 | n/a n/a n/a n/a | +574 +388 +41 -5 | n/a n/a n/a n/a | +823 +457 +26 -293 |
| 13 NYAM fade ONRTH (1 lot) | W1A/W1B | 5 / 538 | +44 +46 -17 +27 | +441 +748 -8 +8 | +44 +46 -17 +27 | +441 +748 -8 +8 |
| 13 NYAM fade ONRTH (1 lot) | W1A-10/W1B-10 | 0 / 543 | n/a n/a n/a n/a | +485 +794 -25 +35 | n/a n/a n/a n/a | +485 +794 -25 +35 |
| 15 NYAM fade ORBF (1 lot) | W1A-10/W1B-10 | 605 / 309 | +726 +381 -506 -158 | +326 +364 -305 -247 | +726 +381 -506 -158 | +326 +364 -305 -247 |
| 16 NYAM fade bundle (ONRTH+VWAPF+ORBF) | W1A/W1B | 4192 / 538 | +1759 +2038 -1030 -335 | +441 +748 -8 +8 | +1759 +2038 -1030 -335 | +441 +748 -8 +8 |
| 16 NYAM fade bundle (ONRTH+VWAPF+ORBF) | W1A-10/W1B-10 | 3878 / 852 | +1389 +1628 -708 -115 | +811 +1159 -329 -212 | +1389 +1628 -708 -115 | +811 +1159 -329 -212 |
| 17 FADE VB2NYPM_T1 (1 lot) | W0/W2A/W2B/W1A/W1B/W1A-10/W1B-10 | 522 / 1 | +384 +238 +33 +20 | +0 +0 +6 +0 | +472 +301 +69 -125 | +0 +0 +6 +0 |
| 18 FADE PDASIA_T2 (1 lot) | W2B/W1B/W1B-10 | 312 / 5 | +216 +290 -6 -16 | +18 +9 +6 +0 | +293 +335 -70 -100 | +18 +9 +3 +1 |
| 20 FADE OR15NYAM_T2 (1 lot) | W1A/W1B | 599 / 336 | +1724 +636 -487 -380 | +916 +108 +388 +115 | +1723 +621 -431 -605 | +885 +75 +319 +354 |
| 20 FADE OR15NYAM_T2 (1 lot) | W1A-10/W1B-10 | 586 / 349 | +1350 +340 -528 -370 | +1220 +368 +419 +104 | +1348 +325 -502 -575 | +1189 +334 +368 +323 |
| 21 Q4 amplifier A: OMF10 day-after-earnings F1 | W1A/W1B/W1A-10/W1B-10 | 0 / 128 | n/a n/a n/a n/a | +125 +200 -269 +81 | n/a n/a n/a n/a | +72 +138 -248 +186 |
| 22 Q4 amplifier B: GO MEGA5 S1 | W1A/W1B/W1A-10/W1B-10 | 0 / 57 | n/a n/a n/a n/a | +154 +210 +280 +367 | n/a n/a n/a n/a | +82 +109 +138 +186 |
| 16  NYAM fade bundle ex-ONRTH (VWAPF+ORBF) | W1A-10/W1B-10 | 3878 / 309 | +1389 +1628 -708 -115 | +326 +364 -305 -247 | +1389 +1628 -708 -115 | +326 +364 -305 -247 |
| 23 DIS-Q 15:50 DRIFT fade (value only) | W0/W2A/W2B/W1A/W1B/W1A-10/W1B-10 | 0 / 891 | n/a n/a n/a n/a | +1306 +1140 -585 -426 | n/a n/a n/a n/a | +635 +555 -292 -214 |
Cells with no trade inside any window (unchanged under every variant): 02 DIS-B P_REL_cont (entry 08:35), 04 DIS-K, 05 DIS-C Sunday 18:30, 11 Q9 London sleeve, 14 VWAPF, 19 VB2NYAM_T3. ORBF (entries from 10:00:0x) is unchanged under W1A and loses 309 of 914 trades (L6M weekly $1,052 -> 726, HOLD 745 -> 381) only if the 10:00 minute is blocked. 18:05/18:06 edge: only PDASIA_T2 is touched (5 of 317 trades at edge-B; L6M 234 -> 216, HOLD 299 -> 290); the 15:00 edge touches one VB2 NYPM T1 trade (value ~0). DIS-Q 15:50 DRIFT (value only, 891 trades, 100% inside 15:00-16:54): L6M +1,306, HOLD +1,140, PRE -585, X' -426 per week at research lots, all removed.
## 3. (a) DIS-AJ true-drift family result restated (headline family treatment = searched; bold = label changed vs L)
| cell | n all | L | W0 | W1A (09:00-09:59 block) | W1A-10 | W2B |
|--|--|--|--|--|--|--|
| 01 Z1 swing failed break v2a | 692 | per-cell only (p 0.01/0.04; fam 0.16/0.65) | per-cell only (p 0.01/0.04; fam 0.17/0.63) | per-cell only (p 0.05/0.03; fam 0.64/0.38) | per-cell only (p 0.05/0.01; fam 0.54/0.33) | per-cell only (p 0.01/0.04; fam 0.17/0.63) |
| 02 DIS-B P_REL_cont_m1.0 | 379 | drift-expl (p 0.14/0.03; fam 0.97/0.33) | drift-expl (p 0.14/0.03; fam 0.97/0.32) | drift-expl (p 0.14/0.03; fam 0.96/0.29) | drift-expl (p 0.14/0.03; fam 0.95/0.29) | drift-expl (p 0.14/0.03; fam 0.96/0.32) |
| 03 DIS-B N_REL_rev_m0.5 NYAM | 304 | per-cell only (p 0.02/0.01; fam 0.35/0.10) | per-cell only (p 0.02/0.01; fam 0.35/0.11) | ALL REMOVED (n kept 0) | ALL REMOVED (n kept 0) | per-cell only (p 0.02/0.01; fam 0.35/0.10) |
| 04 DIS-K COMP_HI BO NYAM | 282 | per-cell only (p 0.03/0.03; fam 0.58/0.49) | per-cell only (p 0.03/0.03; fam 0.59/0.49) | per-cell only (p 0.03/0.03; fam 0.56/0.42) | per-cell only (p 0.03/0.03; fam 0.54/0.44) | per-cell only (p 0.03/0.03; fam 0.59/0.47) |
| 05 DIS-C Sunday 18:30 with-trend | 182 | per-cell only (p 0.06/0.06; fam 0.65/0.79) | per-cell only (p 0.06/0.06; fam 0.65/0.78) | per-cell only (p 0.06/0.06; fam 0.63/0.71) | per-cell only (p 0.06/0.06; fam 0.62/0.78) | per-cell only (p 0.06/0.06; fam 0.65/0.78) |
| 06 DIS-E prevday|FAILURE NYAM | 317 | drift-expl (p 0.05/0.13; fam 0.61/0.94) | drift-expl (p 0.05/0.13; fam 0.61/0.94) | drift-expl (p 0.13/0.22; fam 0.98/1.00) | drift-expl (p 0.11/0.18; fam 0.88/0.98) | drift-expl (p 0.05/0.13; fam 0.62/0.94) |
| 07 DIS-G G1 ratio reversion NYAM | 1030 | per-cell only (p 0.05/0.02; fam 0.70/0.36) | per-cell only (p 0.05/0.02; fam 0.71/0.35) | **drift-expl** (p 0.10/0.13; fam 0.80/0.93) | per-cell only (p 0.04/0.06; fam 0.85/0.94) | per-cell only (p 0.05/0.02; fam 0.72/0.34) |
| 08 DIS-J N_CENT NYAM | 307 | per-cell only (p 0.00/0.02; fam 0.06/0.28) | per-cell only (p 0.00/0.02; fam 0.06/0.27) | **drift-expl** (p 0.00/0.12; fam 0.06/0.88) | per-cell only (p 0.01/0.09; fam 0.16/0.86) | per-cell only (p 0.00/0.02; fam 0.07/0.27) |
| 09 DIS-Q 15:00 IMB fade | 881 | drift-expl (p 0.15/0.00; fam 0.98/0.03) | ALL REMOVED (n kept 0) | ALL REMOVED (n kept 0) | ALL REMOVED (n kept 0) | ALL REMOVED (n kept 0) |
| 10 Q13 middle-tercile gap-fill | 275 | per-cell only (p 0.01/0.01; fam 0.27/0.24) | per-cell only (p 0.01/0.01; fam 0.26/0.24) | ALL REMOVED (n kept 0) | ALL REMOVED (n kept 0) | per-cell only (p 0.01/0.01; fam 0.27/0.24) |
| 11 Q9 London sleeve OFF (A_wide&A_ER_low) | 1389 | drift-expl (p 0.15/0.09; fam 0.97/0.91) | drift-expl (p 0.15/0.09; fam 0.97/0.91) | drift-expl (p 0.15/0.09; fam 0.96/0.86) | drift-expl (p 0.15/0.09; fam 0.95/0.89) | drift-expl (p 0.15/0.09; fam 0.96/0.91) |
| 13 NYAM fade ONRTH (1 lot) | 543 | per-cell only (p 0.08/0.00; fam 0.86/0.02) | per-cell only (p 0.08/0.00; fam 0.87/0.02) | ALL REMOVED (n kept 5) | ALL REMOVED (n kept 0) | per-cell only (p 0.08/0.00; fam 0.85/0.02) |
| 14 NYAM fade VWAPF (1 lot) | 3273 | drift-expl (p 0.13/0.00; fam 0.94/0.11) | drift-expl (p 0.13/0.00; fam 0.94/0.12) | drift-expl (p 0.13/0.00; fam 0.92/0.11) | drift-expl (p 0.13/0.00; fam 0.91/0.11) | drift-expl (p 0.13/0.00; fam 0.92/0.11) |
| 15 NYAM fade ORBF (1 lot) | 914 | per-cell only (p 0.01/0.02; fam 0.17/0.18) | per-cell only (p 0.01/0.02; fam 0.17/0.19) | per-cell only (p 0.01/0.02; fam 0.17/0.18) | per-cell only (p 0.03/0.07; fam 0.50/0.77) | per-cell only (p 0.01/0.02; fam 0.18/0.20) |
| 16 NYAM fade bundle (ONRTH+VWAPF+ORBF) | 4730 | CLEARS+FAM (p 0.01/0.00; fam 0.06/0.00) | CLEARS+FAM (p 0.01/0.00; fam 0.06/0.00) | **per-cell only** (p 0.02/0.00; fam 0.17/0.00) | **per-cell only** (p 0.03/0.01; fam 0.45/0.04) | CLEARS+FAM (p 0.01/0.00; fam 0.06/0.00) |
| 17 FADE VB2NYPM_T1 (1 lot) | 523 | per-cell only (p 0.00/0.01; fam 0.14/0.17) | **CLEARS+FAM** (p 0.00/0.01; fam 0.09/0.06) | **CLEARS+FAM** (p 0.00/0.01; fam 0.09/0.07) | **CLEARS+FAM** (p 0.00/0.01; fam 0.09/0.08) | **CLEARS+FAM** (p 0.00/0.01; fam 0.09/0.06) |
| 18 FADE PDASIA_T2 (1 lot) | 317 | per-cell only (p 0.04/0.00; fam 0.65/0.01) | per-cell only (p 0.04/0.00; fam 0.65/0.01) | per-cell only (p 0.04/0.00; fam 0.63/0.02) | per-cell only (p 0.04/0.00; fam 0.62/0.02) | per-cell only (p 0.06/0.01; fam 0.80/0.02) |
| 19 FADE VB2NYAM_T3 (1 lot) | 893 | per-cell only (p 0.09/0.04; fam 0.93/0.63) | per-cell only (p 0.09/0.04; fam 0.93/0.61) | per-cell only (p 0.09/0.04; fam 0.89/0.56) | per-cell only (p 0.09/0.04; fam 0.88/0.58) | per-cell only (p 0.09/0.04; fam 0.91/0.61) |
| 20 FADE OR15NYAM_T2 (1 lot) | 935 | per-cell only (p 0.00/0.08; fam 0.01/0.77) | per-cell only (p 0.00/0.08; fam 0.01/0.76) | **drift-expl** (p 0.01/0.11; fam 0.20/0.83) | **drift-expl** (p 0.02/0.18; fam 0.37/0.99) | per-cell only (p 0.00/0.08; fam 0.01/0.76) |
| 21 Q4 amplifier A: OMF10 day-after-earnings F1 | 128 | drift-expl (p 0.33/0.09; fam 1.00/0.91) | drift-expl (p 0.33/0.09; fam 1.00/0.91) | ALL REMOVED (n kept 0) | ALL REMOVED (n kept 0) | drift-expl (p 0.33/0.09; fam 1.00/0.91) |
| 22 Q4 amplifier B: GO MEGA5 S1 | 57 | drift-expl (p 0.35/0.14; fam 1.00/0.93) | drift-expl (p 0.35/0.14; fam 1.00/0.93) | ALL REMOVED (n kept 0) | ALL REMOVED (n kept 0) | drift-expl (p 0.35/0.14; fam 1.00/0.93) |
Single-seed labels: read with the seed table in section 1 (VB2 NYPM T1 W0/W1A "CLEARS+FAM" is MC noise: 0-1 of 5 seeds; the bundle W1A "per-cell only" is stable: 0 of 5 seeds clear).
**Bundle under W1 (the lead's item (a)).** ONRTH keeps 5 of 543 trades, so the bundle is VWAPF + ORBF + 5 trades. W1A: weekly $ L6M +1759 / HOLD +2038 / PRE -1030 / X' -335 at 1 lot each (L: 2,200 / 2,786 / -1,038 / -327); excess over true drift W1: +2231 / +2624; per-cell p 0.025 / 0.005 (still significant), family p (searched) L6M 0.174 (seed range .139-.214) / HOLD 0.005, so the label moves from CLEARS TRUE DRIFT + FAMILY to CLEARS PER-CELL ONLY. W1A-10 (10:00 minute blocked as well): L6M +1389 / HOLD +1628, family L6M .31-.48 / HOLD .015-.04. VWAPF + ORBF only (bundle ex-ONRTH, 4,187 trades, the same set as W1A): L6M 1,715 / HOLD 1,992 / PRE -1,013 / X' -363, excess +2,287 / +2,488 (p .010 / .005); added to the 21-cell null as a candidate its family p is L6M 0.17-0.32 / HOLD 0.010-0.020 (5 seeds): it does NOT clear the family test in L6M under any variant (including L). So the family-level clearance of the DIS-AJ bundle rested on ONRTH being part of the sum.
Family size: under W1A 6 of the 21 searched cells have no trade left (N_REL_rev, Q13, DIS-Q 15:00, ONRTH, Q4 A, Q4 B); the `remaining` treatment (15 cells) gives bundle family p L6M .104 / HOLD .005 under W1A (one seed), the `searched` treatment .17; both are above or at .10 in L6M. DIS-Q 15:00 IMB had HOLD per-cell p .005 and family .035 (DRIFT-EXPLAINED via L6M); under any variant it disappears.
## 4. (b) SHADOW_LOT_TABLE rows for the affected lines (restated; stack columns NOT recomputed)
Convention: naive weekly $ over 2026 (all weeks) / pre-2026 / HOLD (2026 W29-W39 dropped, as in the published table) / ALL; conservative = DIS-T estimator mean - SE x median max of F normals (F = the line's program n_tested, as published). Sizing: 1 lot per trade; 0.5x equal-risk ($600) and equal-risk ($1,200) lots = clip(round(R/(stop x 20)), 1, 6) per trade (this study's integer rule; the published table used mean-risk-matched integer lots, so compare variants WITHIN this table; the L rows reproduce the published naive ALL / 2026 / pre-2026 to within a few % and cons ALL exactly; HOLD and EARLY carrying-week conventions differ by up to ~70). "W1A" = the recorded live windows; "W1A-10" adds the 10:00 minute.
| line | window variant | sizing | trades | mean lots | naive 2026 | pre-2026 | HOLD | ALL | cons ALL | cons HOLD | cons EARLY |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ONRTH | L | 1 lot | 543 | 1.00 | +703 | +35 | +966 | +193 | -271 | -145 | -686 |
| ONRTH | L | 0.5x equal-risk ($600) | 543 | 1.00 | +703 | +35 | +966 | +193 | -271 | -145 | -686 |
| ONRTH | L | equal-risk ($1,200) | 543 | 1.00 | +703 | +35 | +966 | +193 | -271 | -145 | -686 |
| ONRTH | W1A | 1 lot | 5 | 1.00 | +54 | +8 | +58 | +19 | -27 | -72 | -71 |
| ONRTH | W1A | 0.5x equal-risk ($600) | 5 | 1.00 | +54 | +8 | +58 | +19 | -27 | -72 | -71 |
| ONRTH | W1A | equal-risk ($1,200) | 5 | 1.00 | +54 | +8 | +58 | +19 | -27 | -72 | -71 |
| ONRTH | W1A-10 | - | **0 (all blocked)** | - | - | - | - | - | - | - | - |
| ORBF | L | 1 lot | 914 | 1.00 | +746 | -536 | +815 | -237 | -870 | -592 | -1846 |
| ORBF | L | 0.5x equal-risk ($600) | 914 | 1.00 | +746 | -536 | +815 | -237 | -870 | -592 | -1846 |
| ORBF | L | equal-risk ($1,200) | 914 | 1.00 | +746 | -536 | +815 | -237 | -870 | -592 | -1846 |
| ORBF | W1A | 1 lot | 914 | 1.00 | +746 | -536 | +815 | -237 | -870 | -592 | -1846 |
| ORBF | W1A | 0.5x equal-risk ($600) | 914 | 1.00 | +746 | -536 | +815 | -237 | -870 | -592 | -1846 |
| ORBF | W1A | equal-risk ($1,200) | 914 | 1.00 | +746 | -536 | +815 | -237 | -870 | -592 | -1846 |
| ORBF | W1A-10 | 1 lot | 605 | 1.00 | +445 | -364 | +315 | -175 | -666 | -707 | -1402 |
| ORBF | W1A-10 | 0.5x equal-risk ($600) | 605 | 1.00 | +445 | -364 | +315 | -175 | -666 | -707 | -1402 |
| ORBF | W1A-10 | equal-risk ($1,200) | 605 | 1.00 | +445 | -364 | +315 | -175 | -666 | -707 | -1402 |
| NYAM_bundle | L | 1 lot | 4730 | 1.00 | +2993 | -523 | +3026 | +302 | -894 | -48 | -2836 |
| NYAM_bundle | L | 0.5x equal-risk ($600) | 4730 | 1.00 | +2993 | -523 | +3026 | +302 | -894 | -48 | -2836 |
| NYAM_bundle | L | equal-risk ($1,200) | 4730 | 1.00 | +2993 | -523 | +3026 | +302 | -894 | -48 | -2836 |
| NYAM_bundle | W1A | 1 lot | 4192 | 1.00 | +2344 | -550 | +2118 | +128 | -924 | -347 | -2652 |
| NYAM_bundle | W1A | 0.5x equal-risk ($600) | 4192 | 1.00 | +2344 | -550 | +2118 | +128 | -924 | -347 | -2652 |
| NYAM_bundle | W1A | equal-risk ($1,200) | 4192 | 1.00 | +2344 | -550 | +2118 | +128 | -924 | -347 | -2652 |
| NYAM_bundle | W1A-10 | 1 lot | 3878 | 1.00 | +1988 | -385 | +1560 | +171 | -732 | -624 | -2132 |
| NYAM_bundle | W1A-10 | 0.5x equal-risk ($600) | 3878 | 1.00 | +1988 | -385 | +1560 | +171 | -732 | -624 | -2132 |
| NYAM_bundle | W1A-10 | equal-risk ($1,200) | 3878 | 1.00 | +1988 | -385 | +1560 | +171 | -732 | -624 | -2132 |
| VWAPF+ORBF (bundle ex-ONRTH) | L | 1 lot | 4187 | 1.00 | +2290 | -558 | +2060 | +109 | -940 | -387 | -2646 |
| VWAPF+ORBF (bundle ex-ONRTH) | L | 0.5x equal-risk ($600) | 4187 | 1.00 | +2290 | -558 | +2060 | +109 | -940 | -387 | -2646 |
| VWAPF+ORBF (bundle ex-ONRTH) | L | equal-risk ($1,200) | 4187 | 1.00 | +2290 | -558 | +2060 | +109 | -940 | -387 | -2646 |
| VWAPF+ORBF (bundle ex-ONRTH) | W1A | 1 lot | 4187 | 1.00 | +2290 | -558 | +2060 | +109 | -940 | -387 | -2646 |
| VWAPF+ORBF (bundle ex-ONRTH) | W1A | 0.5x equal-risk ($600) | 4187 | 1.00 | +2290 | -558 | +2060 | +109 | -940 | -387 | -2646 |
| VWAPF+ORBF (bundle ex-ONRTH) | W1A | equal-risk ($1,200) | 4187 | 1.00 | +2290 | -558 | +2060 | +109 | -940 | -387 | -2646 |
| VWAPF+ORBF (bundle ex-ONRTH) | W1A-10 | 1 lot | 3878 | 1.00 | +1988 | -385 | +1560 | +171 | -732 | -624 | -2132 |
| VWAPF+ORBF (bundle ex-ONRTH) | W1A-10 | 0.5x equal-risk ($600) | 3878 | 1.00 | +1988 | -385 | +1560 | +171 | -732 | -624 | -2132 |
| VWAPF+ORBF (bundle ex-ONRTH) | W1A-10 | equal-risk ($1,200) | 3878 | 1.00 | +1988 | -385 | +1560 | +171 | -732 | -624 | -2132 |
| Q13GAP_T1 | L | 1 lot | 275 | 1.00 | +445 | -12 | +136 | +96 | -161 | -560 | -363 |
| Q13GAP_T1 | L | 0.5x equal-risk ($600) | 275 | 1.60 | +475 | -71 | +115 | +57 | -227 | -611 | -433 |
| Q13GAP_T1 | L | equal-risk ($1,200) | 275 | 2.61 | +495 | -108 | +127 | +33 | -367 | -775 | -694 |
| Q13GAP_T1 | W1A | - | **0 (all blocked)** | - | - | - | - | - | - | - | - |
| Q13GAP_T1 | W1A-10 | - | **0 (all blocked)** | - | - | - | - | - | - | - | - |
| DISE_PDF | L | 1 lot | 317 | 1.00 | +278 | -13 | +158 | +55 | -199 | -612 | -306 |
| DISE_PDF | L | 0.5x equal-risk ($600) | 317 | 1.51 | +261 | +22 | +116 | +79 | -223 | -687 | -349 |
| DISE_PDF | L | equal-risk ($1,200) | 317 | 2.92 | +212 | +34 | -14 | +76 | -450 | -1230 | -583 |
| DISE_PDF | W1A | 1 lot | 202 | 1.00 | +196 | -27 | +165 | +25 | -211 | -543 | -295 |
| DISE_PDF | W1A | 0.5x equal-risk ($600) | 202 | 1.32 | +196 | -15 | +144 | +35 | -227 | -577 | -348 |
| DISE_PDF | W1A | equal-risk ($1,200) | 202 | 2.51 | +9 | -39 | -36 | -27 | -455 | -1060 | -566 |
| DISE_PDF | W1A-10 | 1 lot | 199 | 1.00 | +229 | -23 | +201 | +36 | -199 | -495 | -292 |
| DISE_PDF | W1A-10 | 0.5x equal-risk ($600) | 199 | 1.32 | +229 | -11 | +180 | +46 | -216 | -530 | -344 |
| DISE_PDF | W1A-10 | equal-risk ($1,200) | 199 | 2.52 | +71 | -35 | +30 | -10 | -436 | -971 | -564 |
| OR15NYAM_T2 | L | 1 lot | 935 | 1.00 | +926 | -150 | +99 | +102 | -791 | -2622 | -1048 |
| OR15NYAM_T2 | L | 0.5x equal-risk ($600) | 935 | 1.03 | +916 | -148 | +89 | +101 | -795 | -2637 | -1040 |
| OR15NYAM_T2 | L | equal-risk ($1,200) | 935 | 1.32 | +902 | -199 | +34 | +59 | -891 | -2713 | -1130 |
| OR15NYAM_T2 | W1A | 1 lot | 599 | 1.00 | +651 | -396 | +309 | -152 | -839 | -1618 | -1487 |
| OR15NYAM_T2 | W1A | 0.5x equal-risk ($600) | 599 | 1.03 | +651 | -397 | +309 | -152 | -840 | -1618 | -1475 |
| OR15NYAM_T2 | W1A | equal-risk ($1,200) | 599 | 1.28 | +666 | -501 | +287 | -229 | -952 | -1645 | -1595 |
| OR15NYAM_T2 | W1A-10 | 1 lot | 586 | 1.00 | +435 | -452 | -67 | -246 | -919 | -1882 | -1557 |
| OR15NYAM_T2 | W1A-10 | 0.5x equal-risk ($600) | 586 | 1.03 | +435 | -453 | -67 | -246 | -920 | -1882 | -1545 |
| OR15NYAM_T2 | W1A-10 | equal-risk ($1,200) | 586 | 1.28 | +450 | -567 | -89 | -330 | -1038 | -1913 | -1708 |
| N_REL_rev | L | 1 lot | 304 | 1.00 | +409 | +21 | +460 | +113 | -226 | -582 | -468 |
| N_REL_rev | L | 0.5x equal-risk ($600) | 304 | 1.31 | +414 | +75 | +464 | +155 | -218 | -579 | -447 |
| N_REL_rev | L | equal-risk ($1,200) | 304 | 2.43 | +482 | +39 | +651 | +144 | -429 | -764 | -765 |
| N_REL_rev | W1A | - | **0 (all blocked)** | - | - | - | - | - | - | - | - |
| N_REL_rev | W1A-10 | - | **0 (all blocked)** | - | - | - | - | - | - | - | - |
| VB2NYPM_T1 | L | 1 lot | 523 | 1.00 | +270 | +29 | +226 | +86 | -85 | -159 | -283 |
| VB2NYPM_T1 | L | 0.5x equal-risk ($600) | 523 | 1.60 | +263 | +1 | +244 | +62 | -146 | -165 | -386 |
| VB2NYPM_T1 | L | equal-risk ($1,200) | 523 | 3.06 | +315 | +36 | +318 | +102 | -248 | -340 | -624 |
| VB2NYPM_T1 | W1A | 1 lot | 522 | 1.00 | +270 | +26 | +226 | +84 | -87 | -159 | -287 |
| VB2NYPM_T1 | W1A | 0.5x equal-risk ($600) | 522 | 1.60 | +263 | -2 | +244 | +60 | -148 | -165 | -390 |
| VB2NYPM_T1 | W1A | equal-risk ($1,200) | 522 | 3.06 | +315 | +33 | +318 | +99 | -250 | -340 | -628 |
| VB2NYPM_T1 | W1A-10 | 1 lot | 522 | 1.00 | +270 | +26 | +226 | +84 | -87 | -159 | -287 |
| VB2NYPM_T1 | W1A-10 | 0.5x equal-risk ($600) | 522 | 1.60 | +263 | -2 | +244 | +60 | -148 | -165 | -390 |
| VB2NYPM_T1 | W1A-10 | equal-risk ($1,200) | 522 | 3.06 | +315 | +33 | +318 | +99 | -250 | -340 | -628 |
| PDASIA_T2 | L | 1 lot | 317 | 1.00 | +307 | +28 | +367 | +94 | -58 | -44 | -146 |
| PDASIA_T2 | L | 0.5x equal-risk ($600) | 317 | 1.52 | +310 | +7 | +380 | +78 | -88 | -39 | -204 |
| PDASIA_T2 | L | equal-risk ($1,200) | 317 | 2.63 | +341 | -20 | +406 | +65 | -158 | -73 | -312 |
| PDASIA_T2 | W2B | 1 lot | 312 | 1.00 | +296 | +25 | +367 | +89 | -63 | -44 | -146 |
| PDASIA_T2 | W2B | 0.5x equal-risk ($600) | 312 | 1.53 | +299 | +3 | +380 | +73 | -93 | -39 | -204 |
| PDASIA_T2 | W2B | equal-risk ($1,200) | 312 | 2.65 | +330 | -22 | +406 | +61 | -163 | -73 | -309 |
Suggested SHADOW_LOT_TABLE edits: add a column "share of research trades inside the live no-new-entry windows" (ONRTH 99%, Q13GAP_T1 100%, DISE_PDF 36%, OR15NYAM_T2 36%, Z1 swing 51%, G1 67%, DIS-J 38%, N_REL_rev 100%, DIS-Q 15:00/15:50 100%; VWAPF, ORBF, VB2NYPM_T1 (1 trade), VB2NYAM_T3, DISK_BO_CH, DISB_PREL, DISC_SUN30, PDASIA_T2 (0 / 5 at edge-B) ~0) and replace the NYAM_bundle row by VWAPF + ORBF (+ the ONRTH remnant) if the live windows apply to Shadow lines.
## 5. (c) Watch-list entries whose status changes (label under the recorded live windows W1A, headline `searched` family; L = DIS-AJ as published)
| watch-list entry | DIS-AJ label (L) | under W1A |
|--|--|--|
| 03 DIS-B N_REL_rev_m0.5 NYAM | CLEARS PER-CELL ONLY | ALL TRADES BLOCKED |
| 07 DIS-G G1 ratio reversion NYAM | CLEARS PER-CELL ONLY | DRIFT-EXPLAINED |
| 08 DIS-J N_CENT NYAM | CLEARS PER-CELL ONLY | DRIFT-EXPLAINED |
| 09 DIS-Q 15:00 IMB fade | DRIFT-EXPLAINED | ALL TRADES BLOCKED |
| 10 Q13 middle-tercile gap-fill | CLEARS PER-CELL ONLY | ALL TRADES BLOCKED |
| 13 NYAM fade ONRTH (1 lot) | CLEARS PER-CELL ONLY | ALL TRADES BLOCKED |
| 16 NYAM fade bundle (ONRTH+VWAPF+ORBF) | CLEARS TRUE DRIFT + FAMILY | CLEARS PER-CELL ONLY |
| 17 FADE VB2NYPM_T1 (1 lot) | CLEARS PER-CELL ONLY | CLEARS TRUE DRIFT + FAMILY |
| 20 FADE OR15NYAM_T2 (1 lot) | CLEARS PER-CELL ONLY | DRIFT-EXPLAINED |
| 21 Q4 amplifier A: OMF10 day-after-earnings F1 | DRIFT-EXPLAINED | ALL TRADES BLOCKED |
| 22 Q4 amplifier B: GO MEGA5 S1 | DRIFT-EXPLAINED | ALL TRADES BLOCKED |
Unchanged labels (single-seed, noise-qualified): 02 DIS-B P_REL_cont (drift-explained), 04 DIS-K COMP_HI, 05 DIS-C Sunday 18:30, 11 Q9 London sleeve, 14 VWAPF, 15 ORBF (per-cell only; family L6M .10-.17 depending on treatment), 17 VB2 NYPM T1 (per-cell only; family p straddles .10), 18 PDASIA_T2, 19 VB2NYAM_T3, and the Z1 swing failed break (per-cell only). Shadow-line consequences: the NY-AM fade bundle register should be read as VWAPF + ORBF (+ ONRTH tail), N_REL_rev and Q13GAP_T1 produce no live-comparable trades, DISE_PDF and OR15NYAM_T2 lose a third of their sample (already thin), and the DIS-Q regime watch item (15:50 DRIFT fade) is not a live-executable line at all.
## 6. Limits
Lists are the owners' (NQ, 2023-04..2026-10), simulated with the live fill model; the windows are applied to entry minutes only (exits are not constrained); whether the Shadow logger itself follows the windows is a user question; Monte-Carlo noise in the family p is +-0.05-0.1 around .10 (section 1), so labels at the boundary (bundle W1 L6M, VB2 NYPM T1, DIS-J, OR15) are not decided by this run; edge-A/B matter only for PDASIA_T2 and the 10:00 minute only for ORBF/ONRTH/bundle; the stack numbers are DIS-BJ / DIS-BR's. No PASS; nothing live.
