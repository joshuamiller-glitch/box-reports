# FD_NOL2 - T-FIND-DRESSED, NO-L2 STACK (FD-NOL2), 2026-11-10 19:50Z

Research only, Shadow only, no PASS claims, first-order (no exact engine covers YM GC CL ZN ZB 6E 6J MBT NKD BTC). Every row is labelled **NO-L2 STACK** (ER sizer, price-path TH loss + profit, structural zones, locks/cooldowns, stack rules, near-target take / BE lock; the L2 state cut, book zones and L2 gate are NOT available: no depth on the box). Prereg line in DECISIONS.md (2026-11-09T19:25Z, code outputs/code/fd_nol2/). Windows as of 2026-11-09 (sz_core.WIN); **data end 2026-10-16** for every instrument here (L1M = 10-11..10-16 only, the live weeks 11-02..05 and 11-08.. are NOT in these lists: live-week column is n/a and nothing is labelled cleared).

Pool: every FD-CORE NOL2 candidate with prices on disk (has_px) and >= 60 trades since 2023-04: **2819 candidates dressed** (YM GC CL ZN ZB 6E 6J MBT NKD BTC), each with its OWN best stack found jointly: layer screens on its own trades -> top-3 per layer -> full factorial of the 3^6 = 729 joint stacks, every layer ON (standing rule), objective J = mean/wk - maxDD/weeks on 2023-04..2026-10 with layer retention >= 70% of lots (relaxed stepwise) and joint >= 30%. Not covered here (no price path in the lists): has_px = 0 rows (730 NOL2 rows incl. the 546 6E+6J relative-value pairs and the DAILY books) -> sizer/locks/stack-only pass pending.

## 1. Counts
| instrument | dressed | naked_pos_FULL | dressed_pos_FULL | finalists | bw_beat>=50%&dd_cut>0 | p_proc<=.10 | seat_ok_any | LEAD+ |
|--|--|--|--|--|--|--|--|--|
| 6E | 15 | 0 | 5 | 3 | 0 | 0 | 3 | 0 |
| 6J | 22 | 0 | 6 | 0 |  |  |  |  |
| BTC | 55 | 11 | 20 | 9 | 3 | 0 | 9 | 0 |
| CL | 460 | 4 | 51 | 15 | 6 | 3 | 15 | 1 |
| GC | 717 | 107 | 257 | 152 | 44 | 7 | 136 | 5 |
| MBT | 60 | 8 | 28 | 20 | 11 | 0 | 20 | 1 |
| NKD | 31 | 0 | 2 | 0 |  |  |  |  |
| YM | 595 | 10 | 121 | 51 | 22 | 3 | 46 | 2 |
| ZB | 465 | 0 | 0 | 0 |  |  |  |  |
| ZN | 399 | 0 | 0 | 0 |  |  |  |  |

finalist = dressed FULL, L6M, PRE and HOLD means all > 0 (screen for the validation stage, not a verdict). PRIMARY OOS = bw_*: bi-weekly re-pick of the whole procedure (train trailing 26 wk, purge 7 d, next 2 wk, 2024-01..2026-10-16; min 20 training trades) vs the NAKED candidate as the reference (no live setting exists for these books); beat = lower period maxDD. The monthly WF (WF_ok in the ledger) is secondary: purged monthly walk-forward of the WHOLE dress-and-pick procedure (expanding train, 7-day embargo, test months 2024-03..2026-10): OOS dressed mean > 0, > naked OOS mean, maxDD <= naked OOS maxDD. p_proc = selection-aware null of the dressing GAIN (J_dressed - J_naked): B=100 null worlds per cell (random side + shifted entries, same count/lots/brackets), the whole screen + joint selection re-run in each; p = share of null gains >= the real gain; p_fam = max-stat over all finalists standardised null gains (independent cells, conservative, LOWER BOUND for the whole pool). seat_ok_any = F.clears-style (eq-mean maxDD cut on L6M and PRE, tolerant -3 pts on one) in at least one of add / replace-weakest (credit above the drop-only row) / replace-correlated, from fd_core.seat_test.

## 2. Ranked finalists (rank key: label, then dressed L6M mean; recents first per STANDING RULE 2)
| instr | sess | book (family / id) | naked L6M / PRE $/wk | naked dd L6M | dressed L6M / PRE $/wk | dressed dd L6M | carries | seat add cut L6M/PRE % (eq mean) | repl-weakest inc | repl-corr inc | corr | bi-weekly WF OOS (maxDD cut %, d mean $/wk, % periods beat, n) | p_proc | p_fam | p_plc | held-out 6 wk dressed / naked $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| YM | pre | T2FYM YM.T2FYM.a26b5100 | 96 / 100 | 11,552 | 559 / 185 | 4,373 | SIZ | +1.8 / +3.7 | +1.4 / +3.0 | +3.1 / +4.7 | 0.07 | +43.2% / +121.3 / 72% / 72 | 0.82 | 1.00 | 0.07 | -39 / -4,518 | LEAD |
| GC | pre | T2FGC GC.T2FGC.5113826e | 422 / -370 | 8,074 | 549 / 12 | 2,045 | THP | +1.6 / +1.2 | +1.7 / +1.4 | +3.0 / +2.0 | -0.01 | +49.6% / +225.4 / 75% / 72 | 0.18 | 1.00 | 0.06 | -715 / 7,850 | LEAD |
| CL | nypm | T2FCL CL.T2FCL.ca380ff7 | 22 / -515 | 7,341 | 467 / 46 | 2,644 | SIZ | +1.4 / +2.9 | +1.2 / +2.8 | +11.6 / +6.7 | 0.09 | +41.8% / +118.3 / 77% / 71 | 0.72 | 1.00 | 0.10 | 384 / -1,696 | LEAD |
| MBT | pre | donchian MBT.donchian.e7096026 | 346 / -147 | 2,960 | 368 / 40 | 1,325 | STK | +1.0 / +0.7 | +1.3 / +1.1 | +1.0 / +0.2 | -0.13 | +64.3% / +128.7 / 68% / 72 | 0.20 | 1.00 | 0.05 | 826 / 490 | LEAD |
| GC | nypm | T2FGC GC.T2FGC.4780f85a | -470 / -349 | 14,026 | 340 / 36 | 1,677 | STK | +1.0 / +1.5 | +1.6 / +2.5 | +1.5 / +2.0 | 0.12 | +41.1% / +163.7 / 65% / 72 | 0.49 | 1.00 | 0.10 | -482 / -8,750 | LEAD |
| GC | nypm | T2FGC GC.T2FGC.62cc8c4d | -470 / -349 | 14,026 | 340 / 36 | 1,677 | STK | +1.0 / +1.5 | +1.6 / +2.5 | +1.5 / +2.0 | 0.12 | +41.1% / +163.7 / 65% / 72 | 0.42 | 1.00 | 0.10 | -482 / -8,750 | LEAD |
| YM | pre | T2FYM YM.T2FYM.bfb909c2 | 155 / -149 | 8,942 | 271 / 52 | 5,797 | STK | +1.3 / +3.7 | +0.5 / +3.5 | +2.2 / +3.9 | 0.03 | +52.5% / +147.2 / 64% / 72 | 0.87 | 1.00 | 0.10 | 1,452 / 3,952 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.140552d8 | 263 / -399 | 11,197 | 118 / 207 | 8,478 | ZON | -0.2 / -0.7 | +0.2 / -0.1 | +0.2 / -1.7 | -0.04 | +62.0% / +217.3 / 81% / 72 | 0.02 | 1.00 | 0.31 | -511 / 4,053 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.be193059 | 279 / -299 | 9,467 | 64 / 143 | 9,157 | ZON | -0.3 / -1.4 | -0.0 / -1.0 | +2.1 / -0.5 | -0.00 | +63.4% / +209.0 / 65% / 72 | 0.08 | 1.00 | 0.45 | 7,602 / 5,663 | LEAD |
| BTC | nypm | CAPBREACH_gp_h30_nypm_q0.85_atr_3.0_None BTC.CAPBREACH_gp_h30_nypm_q0.85_atr_3.0_None.b7bf2328 | 261 / -443 | 6,417 | 548 / 149 | 4,979 | ZON | +0.4 / +0.3 | +1.5 / +1.5 | +28.6 / +3.9 | 0.17 | +64.6% / +271.8 / 53% / 70 | 0.63 | 1.00 | 0.34 | 3,473 / 2,339 | NOW-ONLY (own p fails) |
| GC | asia | T2FGC GC.T2FGC.4722bad0 | 58 / -19 | 9,886 | 503 / 125 | 1,534 | SIZ | +0.7 / +0.1 | +0.4 / -0.1 | +19.5 / +3.2 | -0.03 | +73.2% / +137.9 / 56% / 72 | 0.98 | 1.00 | 0.42 | 268 / -7,323 | NOW-ONLY (own p fails) |
| GC | asia | T2FGC GC.T2FGC.b73d4f64 | 142 / -32 | 9,886 | 454 / 141 | 1,389 | SIZ | +0.5 / -0.4 | +0.2 / -0.6 | +14.9 / +2.0 | -0.01 | +35.3% / +82.6 / 57% / 72 | 0.98 | 1.00 | 0.45 | 338 / -6,283 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.0481bdc8 | 338 / -141 | 12,777 | 419 / 86 | 2,193 | STK | +0.9 / -1.9 | +1.0 / -2.1 | +65.6 / -1.7 | 0.10 | +58.7% / +122.1 / 63% / 68 | 0.50 | 1.00 | 0.28 | 423 / -3,933 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.2940ca9e | 338 / -141 | 12,777 | 419 / 86 | 2,193 | STK | +0.9 / -1.9 | +1.0 / -2.1 | +65.6 / -1.7 | 0.10 | +58.7% / +122.1 / 63% / 68 | 0.46 | 1.00 | 0.28 | 423 / -3,933 | NOW-ONLY (own p fails) |
| GC | nyam | T2FGC GC.T2FGC.8816beed | -134 / -244 | 11,834 | 418 / 15 | 2,479 | THL | +0.9 / +1.7 | +0.7 / +1.6 | +24.7 / +6.2 | -0.05 | +8.1% / +76.2 / 61% / 71 | 0.15 | 1.00 | 0.26 | -1,554 / -10,278 | NOW-ONLY (own p fails) |
| GC | nyam | T2FGC GC.T2FGC.c478779e | -95 / -188 | 17,078 | 418 / 113 | 3,859 | STK | +0.7 / +3.0 | +0.5 / +2.9 | +5.5 / +2.5 | -0.09 | +24.6% / +149.1 / 58% / 71 | 0.16 | 1.00 | 0.34 | -2,934 / -15,928 | NOW-ONLY (own p fails) |
| YM | nyam | T2FYM YM.T2FYM.0d80268b | 959 / -338 | 5,605 | 413 / 67 | 1,783 | THP | -0.5 / +0.5 | +1.3 / +0.7 | +1.3 / +0.7 | -0.07 | +55.3% / +31.2 / 59% / 71 | 0.31 | 1.00 | 0.51 | -4,197 / -2,208 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.4d02584a | 36 / -225 | 14,473 | 396 / 80 | 2,564 | ZON | +0.9 / -0.7 | +1.7 / -0.3 | +2.0 / -1.6 | 0.04 | +25.7% / +6.1 / 60% / 72 | 0.90 | 1.00 | 0.25 | -84 / -3,227 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.1132e76a | 436 / -300 | 19,407 | 388 / 91 | 3,568 | STK | +0.6 / -1.8 | +1.2 / -1.4 | +42.8 / -2.0 | 0.16 | +55.6% / +156.9 / 66% / 68 | 0.45 | 1.00 | 0.29 | -538 / -2,543 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.7de2b0e2 | 436 / -300 | 19,407 | 388 / 91 | 3,568 | STK | +0.6 / -1.8 | +1.2 / -1.4 | +42.8 / -2.0 | 0.16 | +55.6% / +156.9 / 66% / 68 | 0.44 | 1.00 | 0.29 | -538 / -2,543 | NOW-ONLY (own p fails) |
| CL | nypm | T2FCL CL.T2FCL.1cff3bf8 | -81 / -262 | 10,019 | 347 / 18 | 2,898 | STK | +0.8 / +0.8 | +1.6 / +1.7 | +3.8 / +1.8 | -0.09 | +64.0% / +95.4 / 66% / 71 | 0.97 | 1.00 | 0.32 | 616 / -5,150 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.398a806e | 469 / -40 | 4,841 | 341 / 84 | 1,998 | STK | +1.7 / +1.8 | +0.8 / +0.9 | +1.6 / +1.6 | 0.12 | +48.9% / +9.2 / 51% / 67 | 0.79 | 1.00 | 0.17 | 3,899 / 6,191 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.fea033f9 | 469 / -40 | 4,841 | 341 / 84 | 1,998 | STK | +1.7 / +1.8 | +0.8 / +0.9 | +1.6 / +1.6 | 0.12 | +48.9% / +9.2 / 51% / 67 | 0.81 | 1.00 | 0.17 | 3,899 / 6,191 | NOW-ONLY (own p fails) |
| YM | close | T2FYM YM.T2FYM.50f3f8aa | 486 / -132 | 4,992 | 341 / 221 | 3,247 | SIZ | -0.6 / +0.4 | +1.3 / +1.0 | +9.7 / +2.3 | 0.11 | +57.1% / +7.6 / 60% / 72 | 0.99 | 1.00 | 0.52 | -1,043 / 3,503 | NOW-ONLY (own p fails) |
| MBT | nyam | donchian MBT.donchian.ec38d391 | 196 / -272 | 12,064 | 337 / 185 | 3,082 | THP | -1.2 / +0.5 | +1.0 / +1.4 | +27.7 / +3.5 | 0.19 | +17.8% / +4.0 / 61% / 72 | 0.86 | 1.00 | 0.67 | 1,794 / 7,065 | NOW-ONLY (own p fails) |
| GC | nyam | T2FGC GC.T2FGC.56c1e879 | 459 / -156 | 4,639 | 331 / 14 | 1,490 | STK | +0.7 / +0.5 | +1.2 / +1.0 | +2.0 / +1.7 | 0.09 | +73.1% / +84.2 / 52% / 63 | 0.32 | 1.00 | 0.30 | 2,451 / 3,976 | NOW-ONLY (own p fails) |
| YM | asia | T2FYM YM.T2FYM.58b66d03 | 147 / -184 | 4,209 | 330 / 54 | 2,062 | SIZ | +0.8 / +0.7 | +1.0 / +1.0 | +2.2 / +1.4 | 0.14 | +56.8% / +84.0 / 66% / 62 | 0.62 | 1.00 | 0.11 | 1,661 / -2,386 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.08b84e1c | -582 / 33 | 13,383 | 325 / 183 | 2,364 | STK | +0.7 / +1.6 | +0.6 / +1.6 | +4.8 / +0.8 | 0.04 | +74.7% / +355.7 / 71% / 72 | 0.26 | 1.00 | 0.25 | 1,826 / -5,952 | NOW-ONLY (own p fails) |
| GC | nyam | T2FGC GC.T2FGC.feb85183 | 698 / -132 | 4,639 | 323 / 49 | 2,934 | STK | +0.5 / +0.4 | +1.2 / +1.1 | +2.1 / +1.9 | 0.01 | +65.2% / +103.8 / 52% / 63 | 0.56 | 1.00 | 0.38 | -95 / 2,816 | NOW-ONLY (own p fails) |
| GC | asia | T2FGC GC.T2FGC.e480d279 | 32 / -34 | 9,886 | 319 / 188 | 4,009 | STK | -0.0 / -1.9 | -0.3 / -2.0 | +13.6 / -2.8 | -0.14 | +60.5% / +166.9 / 62% / 72 | 0.99 | 1.00 | 0.44 | -3,005 / -6,633 | NOW-ONLY (own p fails) |
| MBT | pre | mom_h60_pre_q0.7_atr_3.0_None_s1 MBT.mom_h60_pre_q0.7_atr_3.0_None_s1.9e80489f | 161 / -165 | 4,862 | 282 / 83 | 1,024 | SIZ | +0.8 / +1.1 | +0.7 / +1.2 | +1.4 / +1.8 | 0.06 | +32.2% / +17.2 / 56% / 48 | 0.47 | 1.00 | 0.19 | 3,464 / 2,430 | NOW-ONLY (own p fails) |
| GC | asia | T2FGC GC.T2FGC.c527f3a7 | -133 / -139 | 9,188 | 266 / 8 | 1,957 | SIZ | -0.7 / -0.2 | +1.0 / +0.4 | +0.2 / +0.6 | -0.04 | +52.9% / +111.3 / 78% / 65 | 0.83 | 1.00 | 0.53 | -85 / -41 | NOW-ONLY (own p fails) |
| GC | close | T2FGC GC.T2FGC.3a97643b | -383 / -222 | 10,028 | 263 / 28 | 2,594 | ZON | +0.6 / +1.3 | +0.7 / +1.5 | +2.5 / +3.8 | 0.05 | +28.4% / +99.0 / 73% / 70 | 0.79 | 1.00 | 0.20 | -1,082 / -6,283 | NOW-ONLY (own p fails) |
| GC | close | T2FGC GC.T2FGC.fb051a4c | -383 / -222 | 10,028 | 263 / 28 | 2,594 | ZON | +0.6 / +1.3 | +0.7 / +1.5 | +2.5 / +3.8 | 0.05 | +28.4% / +99.0 / 73% / 70 | 0.76 | 1.00 | 0.20 | -1,082 / -6,283 | NOW-ONLY (own p fails) |
| YM | asia | T2FYM YM.T2FYM.8864ad19 | 153 / -148 | 4,209 | 263 / 53 | 2,312 | SIZ | +0.7 / +0.6 | +0.8 / +0.7 | +1.9 / +1.1 | 0.17 | +43.5% / +65.9 / 63% / 62 | 0.79 | 1.00 | 0.15 | 1,861 / 104 | NOW-ONLY (own p fails) |
| GC | nyam | T2FGC GC.T2FGC.a6f08616 | -167 / -229 | 10,973 | 260 / 49 | 3,024 | THL | +0.5 / +3.0 | +0.4 / +2.9 | -0.6 / +1.2 | -0.03 | +20.4% / +115.7 / 61% / 71 | 0.21 | 1.00 | 0.26 | -3,024 / -9,568 | NOW-ONLY (own p fails) |
| MBT | nyam | donchian MBT.donchian.69e3710b | 43 / -271 | 15,779 | 223 / 264 | 5,722 | THP | -1.6 / +2.8 | +1.0 / +4.3 | -2.1 / +2.4 | 0.08 | +29.9% / +25.4 / 65% / 72 | 0.88 | 1.00 | 0.65 | 1,279 / 6,797 | NOW-ONLY (own p fails) |
| CL | nypm | T2FCL CL.T2FCL.f5dc8789 | -459 / 61 | 13,126 | 222 / 30 | 1,907 | ZON | -1.7 / +1.5 | +1.1 / +2.3 | -1.0 / +2.3 | 0.09 | +41.5% / +133.1 / 67% / 67 | 1.00 | 1.00 | 0.82 | 1,394 / 584 | NOW-ONLY (own p fails) |
| GC | nyam | T2FGC GC.T2FGC.ad632fba | 990 / -204 | 2,979 | 222 / 44 | 1,825 | STK | +0.4 / -0.0 | +1.0 / +0.5 | +0.9 / +0.5 | 0.09 | +67.8% / +124.4 / 59% / 63 | 0.16 | 1.00 | 0.31 | 1,329 / 5,316 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.10426526 | -91 / -92 | 17,410 | 211 / 175 | 3,573 | STK | +0.2 / +1.1 | +0.1 / +1.1 | +6.0 / +1.9 | -0.03 | +68.7% / +270.2 / 76% / 72 | 0.53 | 1.00 | 0.26 | -2,474 / -3,292 | NOW-ONLY (own p fails) |

Equal-$-risk lots R = $1,200/trade (fd_core.lots_for, participation caps fd_core.LOT_CAP), fees/slippage as in each source screen (te2 cost proxies; no FEES.md line per instrument beyond ES/NQ/MES/6E: PROXY-STD), exits changed by TH/take/BE re-simulated on the 1-min path (fill at the next bar open - 1 tick; trail/BE on bar extremes; same-bar ambiguity keeps the baseline). 1-s refinement for GC/CL/ZN: see section 6.

## 3. Which layer carries it (finalists; J contribution = J(stack) - J(stack with that layer at reference))
| instrument | finalists | SIZ | THL | THP | ZON | LCK | STK | most frequent carrier |
|--|--|--|--|--|--|--|--|--|
| 6E | 3 | +21.6 | -1.4 | +1.4 | +5.0 | +0.0 | +38.1 | STK |
| BTC | 9 | +78.9 | -1.7 | +19.1 | +79.4 | +58.1 | +84.8 | ZON |
| CL | 15 | +47.6 | +17.1 | +5.2 | +84.8 | +0.0 | +46.8 | ZON |
| GC | 138 | +30.3 | +2.3 | +17.2 | +41.1 | +0.0 | +32.6 | STK |
| MBT | 20 | +23.4 | -1.5 | +9.4 | +28.0 | +6.6 | +12.0 | ZON |
| YM | 46 | +62.6 | +6.3 | +20.4 | +50.7 | +0.0 | +33.6 | SIZ |
median J contribution per layer ($/wk-equivalent of the objective). THL/THP = price-path loss/profit rule, SIZ = ER sizer, ZON = zones, LCK = locks/cooldowns, STK = stack rules.

## 4. Session-by-session registry (SESSION BOOKs are never killed by the pooled row)
| instrument | session | finalists | bi-weekly beat >= 50% | LEAD or better | best dressed L6M $/wk |
|--|--|--|--|--|--|
| 6E | london | 3.0 | 0.0 | 0.0 | 80 |
| BTC | close | 5.0 | 4.0 | 0.0 | 476 |
| BTC | london | 2.0 | 2.0 | 0.0 | 1,085 |
| BTC | nypm | 2.0 | 1.0 | 0.0 | 548 |
| CL | nyam | 2.0 | 1.0 | 0.0 | 162 |
| CL | nypm | 13.0 | 6.0 | 1.0 | 467 |
| GC | asia | 17.0 | 11.0 | 0.0 | 814 |
| GC | close | 24.0 | 6.0 | 0.0 | 263 |
| GC | london | 25.0 | 11.0 | 0.0 | 1,090 |
| GC | nyam | 28.0 | 23.0 | 2.0 | 2,595 |
| GC | nypm | 39.0 | 19.0 | 2.0 | 907 |
| GC | pre | 5.0 | 2.0 | 1.0 | 549 |
| MBT | close | 10.0 | 6.0 | 0.0 | 231 |
| MBT | nyam | 4.0 | 4.0 | 0.0 | 342 |
| MBT | nypm | 3.0 | 3.0 | 0.0 | 153 |
| MBT | pre | 3.0 | 3.0 | 1.0 | 368 |
| YM | asia | 11.0 | 5.0 | 0.0 | 330 |
| YM | close | 10.0 | 5.0 | 0.0 | 629 |
| YM | london | 3.0 | 3.0 | 0.0 | 205 |
| YM | nyam | 11.0 | 11.0 | 0.0 | 1,053 |
| YM | nypm | 5.0 | 5.0 | 0.0 | 164 |
| YM | pre | 6.0 | 6.0 | 2.0 | 559 |

## 5. Depth quote (Databento metadata.get_cost only, nothing bought; account spend $7,327.93 of $8,000 = $672 left)
mbp-10, GLBX.MDP3, continuous .v.0. History quoted for 2023-04..2026-10 (the window every row above is scored on) and for the last 12 months; forward = one 5-day week (2026-10-18..10-23) as proxy of the weekly pull (the live feed is a separate Databento Live licence not quotable through get_cost; the per-week batch pull is the comparable figure).

| symbol | mbp-10 history 2023-04..2026-10 $ | last 12 months $ | forward $/week (5-day proxy) | records/week (M) | GB/week | on the box |
|--|--|--|--|--|--|--|
| YM | 527 | 152 | 2.25 | 13.1 | 4.8 | no |
| GC | 408 | 174 | 3.36 | 19.6 | 7.2 | no |
| CL | 374 | 107 | 2.28 | 13.3 | 4.9 | no |
| ZN | 439 | 147 | 3.71 | 21.7 | 8.0 | no |
| ZB | 227 | 68 | 1.78 | 10.4 | 3.8 | no |
| 6E | 280 | 73 | 1.20 | 7.0 | 2.6 | no |
| 6J | 194 | 51 | 0.96 | 5.6 | 2.1 | no |
| MBT | 691 | 301 | 4.09 | 23.9 | 8.8 | no |
| NKD | 72 | 24 | 0.51 | 3.0 | 1.1 | no |
| NQ | 2,019 | 813 | 16.56 | 96.6 | 35.6 | yes (full MBP-10) |
| ES | 1,436 | 494 | 8.85 | 51.6 | 19.0 | yes (full MBP-10) |
| RTY | 596 | 198 | 2.51 | 14.7 | 5.4 | yes (full MBP-10) |

**YM + GC + CL together: full history $1,309, last 12 months $433, forward $7.89/week (about $410/year).** Against $672 of budget left: the 12-month history of the three is affordable only if nothing else is bought; the 2023-04..2026-10 history of the three is not. What L2 adds on NQ/ES/RTY for the same book family (the price the user is weighing) is published in FD_LIQ.md (FD-LIQ): see that page; this page prints only the NO-L2 side.

## 6. 1-s refinement (GC, CL; the only instruments with 1-s bars 2023-02..2026-10-16)
| instrument | finalists re-run on 1-s | dressed L6M > 0 on 1-s (same configs) | PRE > 0 | FULL > 0 | median FULL $/wk 1-min -> 1-s | after re-picking TH loss/profit on 1-s: FULL > 0 | median |
|--|--|--|--|--|--|--|--|
| CL | 15 | 8 | 9 | 5 | 65 -> -10 | 10 | 13 |
| GC | 138 | 98 | 94 | 93 | 111 -> 23 | 124 | 68 |

## REFIT 2026-11-22 (settings the bi-weekly procedure picks today; train = trailing 26 weeks to the data end 2026-10-16) - top 12 by bi-weekly OOS and L6M
* YM.T2FYM.a26b5100 (pre): {"SIZ": "ER20(1-min bars) < 0.25 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.7R; cut when >= 3 of 4 votes (momentum 0.2R/0.15D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "near-target take at 0.75 of target distance", "ZON": "zones RN: ahead < 1.0R -> lots x0.0", "LCK": "lock/cooldown: 60 min after a loser, max 2 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 0 min / last 15 min of session; DOW none"}
* GC.T2FGC.5113826e (pre): {"SIZ": "ER40(1-min bars) < 0.15 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.5R; cut when >= 3 of 4 votes (momentum 0.2R/0.3D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "break-even lock: after +0.8R stop to entry+0.2R", "ZON": "zones RN: NOT within 1.5R of support behind entry -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW skip Fri"}
* BTC.CAPBREACH_gp_h30_nypm_q0.85_atr_3.0_None.b7bf2328 (nypm): {"SIZ": "ER40(1-min bars) > 0.35 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.5R; cut when >= 3 of 4 votes (momentum 0.4R/0.15D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "near-target take at 0.9 of target distance", "ZON": "zones SW: ahead < 0.5R -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 2 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW skip Mon"}
* GC.T2FGC.4722bad0 (asia): {"SIZ": "ER80(1-min bars) > 0.35 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.5R; cut when >= 3 of 4 votes (momentum 0.4R/0.15D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "TH-profit(price path): PhMin 0.8R, PhReq 2/4 votes (window 0.15D), PhTrail 0.35R behind extreme", "ZON": "zones SW: ahead < 1.0R -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW Mon+Fri x.5"}
* CL.T2FCL.ca380ff7 (nypm): {"SIZ": "ER20(1-min bars) < 0.35 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.7R; cut when >= 3 of 4 votes (momentum 0.2R/0.3D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "TH-profit(price path): PhMin 0.3R, PhReq 3/4 votes (window 0.15D), PhTrail 0.2R behind extreme", "ZON": "zones VW: ahead < 0.5R -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 30 min / last 0 min of session; DOW skip Fri"}
* GC.T2FGC.b73d4f64 (asia): {"SIZ": "ER80(1-min bars) > 0.35 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 3 of 4 votes (momentum 0.2R/0.15D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "TH-profit(price path): PhMin 0.8R, PhReq 2/4 votes (window 0.15D), PhTrail 0.2R behind extreme", "ZON": "zones SW: ahead < 1.0R -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW Mon+Fri x.5"}
* GC.T2FGC.0481bdc8 (nypm): {"SIZ": "ER80(1-min bars) < 0.15 -> lots x0.5", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 3 of 4 votes (momentum 0.4R/0.3D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "near-target take at 0.9 of target distance", "ZON": "zones SW: NOT within 0.5R of support behind entry -> lots x0.0", "LCK": "lock/cooldown: 120 min after a loser, max 3 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 30 min / last 15 min of session; DOW skip Fri"}
* GC.T2FGC.2940ca9e (nypm): {"SIZ": "ER80(1-min bars) < 0.15 -> lots x0.5", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 3 of 4 votes (momentum 0.4R/0.3D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "near-target take at 0.9 of target distance", "ZON": "zones SW: NOT within 0.5R of support behind entry -> lots x0.0", "LCK": "lock/cooldown: 120 min after a loser, max 3 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 30 min / last 15 min of session; DOW skip Fri"}
* GC.T2FGC.8816beed (nyam): {"SIZ": "ER80(1-min bars) > 0.25 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 2 of 4 votes (momentum 0.4R/0.15D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "TH-profit(price path): PhMin 0.3R, PhReq 3/4 votes (window 0.3D), PhTrail 0.2R behind extreme", "ZON": "zones PD: at < 0.5R -> lots x0.0", "LCK": "lock/cooldown: 30 min after a loser, max 3 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW skip Mon"}
* GC.T2FGC.c478779e (nyam): {"SIZ": "ER40(1-min bars) > 0.25 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 2 of 4 votes (momentum 0.2R/0.3D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "TH-profit(price path): PhMin 0.3R, PhReq 3/4 votes (window 0.3D), PhTrail 0.5R behind extreme", "ZON": "zones PD: at < 0.5R -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW skip Mon"}
* YM.T2FYM.0d80268b (nyam): {"SIZ": "ER20(1-min bars) < 0.25 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.5R; cut when >= 3 of 4 votes (momentum 0.4R/0.15D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "near-target take at 0.75 of target distance", "ZON": "zones PD: ahead < 1.5R -> lots x0.0", "LCK": "lock/cooldown: 30 min after a loser, max 2 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 0 min / last 15 min of session; DOW none"}
* GC.T2FGC.4d02584a (nypm): {"SIZ": "ER10(1-min bars) < 0.35 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.5R; cut when >= 3 of 4 votes (momentum 0.4R/0.3D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "near-target take at 0.9 of target distance", "ZON": "zones RN: NOT within 1.0R of support behind entry -> lots x0.5", "LCK": "lock/cooldown: 60 min after a loser, max 3 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 0 min / last 15 min of session; DOW none"}

Prior check (TOLERANT, never kills): RECENT-ONLY = dressed PRE maxDD more than 15% deeper than the naked reference or PRE mean more than $1k/wk below it; the tag is appended to the label.

## 7. Method limits and open items
* First-order: per-trade re-simulation on 1-min bars; no re-entries after a changed exit, no slice/queue effects, lock/cooldown layer recomputed sequentially on the cell's own trades. Not an engine run. Layers are selected in-sample (2023-04..2026-10) with the WF as the honest read.
* 1-s: section 6 (GC, CL); YM/ZB/6E/6J/NKD/MBT/BTC have 1-min bars only. ZN and ZB produced no finalist (no dressed stack has FULL, L6M, PRE and HOLD means all > 0), so no 1-s run was needed.
* Price-path TH is a portable re-parameterisation (votes in R and in fractions of the book's planned hold D), NOT NQ's DS7 points grid; D7 panel values for these instruments do not exist (nothing is live).
* held-out = the last 6 data weeks (2026-09-07..10-16, train <= 2026-08-31), not the frozen NQ live file.
