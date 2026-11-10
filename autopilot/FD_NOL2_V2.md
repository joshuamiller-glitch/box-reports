# FD_NOL2_V2 - T-FIND-DRESSED, NO-L2 STACK (FD-NOL2), 2026-11-10 22:25Z

Research only, Shadow only, no PASS claims, first-order (no exact engine covers YM GC CL ZN ZB 6E 6J MBT NKD BTC). Every row is labelled **NO-L2 STACK** (ER sizer, price-path TH loss + profit, structural zones, locks/cooldowns, stack rules, near-target take / BE lock; the L2 state cut, book zones and L2 gate are NOT available: no depth on the box). Prereg line in DECISIONS.md (2026-11-09T19:25Z, code outputs/code/fd_nol2/). Windows as of 2026-11-09 (sz_core.WIN); **V2: candidate lists regenerated on FD-CORE core_bars to 2026-11-09/10 (L1M and L2M are real, 10-11..11-09); candidates whose generator could not be re-run (listed in section 8) still end 2026-10-16 and carry v2=False. The frozen NQ live file is not applicable to these books: live-week column is n/a and nothing is labelled cleared**.

Pool: every FD-CORE NOL2 candidate with prices on disk (has_px) and >= 60 trades since 2023-04: **1958 candidates dressed** (YM GC CL ZN ZB 6E 6J MBT NKD BTC), each with its OWN best stack found jointly: layer screens on its own trades -> top-3 per layer -> full factorial of the 3^6 = 729 joint stacks, every layer ON (standing rule), objective J = mean/wk - maxDD/weeks on 2023-04..2026-10 with layer retention >= 70% of lots (relaxed stepwise) and joint >= 30%. Not covered here (no price path in the lists): has_px = 0 rows (730 NOL2 rows incl. the 546 6E+6J relative-value pairs and the DAILY books) -> sizer/locks/stack-only pass pending.

## 1. Counts
| instrument | dressed | naked_pos_FULL | dressed_pos_FULL | screen finalists (validated = ledger rows: GC 138, YM 49, others equal) | bw_beat>=50%&dd_cut>0 | p_proc<=.10 | seat_ok_any | LEAD+ |
|--|--|--|--|--|--|--|--|--|
| 6E | 15 | 0 | 5 | 3 | 0 | 0 | 3 | 0 |
| 6J | 22 | 0 | 6 | 0 |  |  |  |  |
| BTC | 55 | 11 | 20 | 9 | 3 | 0 | 9 | 0 |
| CL | 459 | 4 | 52 | 14 | 6 | 1 | 14 | 1 |
| GC | 721 | 110 | 257 | 149 | 46 | 6 | 135 | 12 |
| MBT | 60 | 8 | 28 | 20 | 12 | 0 | 20 | 0 |
| NKD | 31 | 0 | 2 | 0 |  |  |  |  |
| YM | 595 | 9 | 128 | 54 | 22 | 2 | 48 | 1 |

RECONCILIATION: 249 screen finalists (GC 149, YM 54) minus 16 (GC 11, YM 5) for which the validation re-pick found no joint stack under the stricter checks = 233 validated finalists, which are the rows in ledger_NOL2_v2.parquet and nol2_v2/dressed (GC 138, YM 49, MBT 20, CL 14, BTC 9, 6E 3). The 16 are not validated and carry no label. finalist = dressed FULL, L6M, PRE and HOLD means all > 0 (screen for the validation stage, not a verdict). PRIMARY OOS = bw_*: bi-weekly re-pick of the whole procedure (train trailing 26 wk, purge 7 d, next 2 wk, 2024-01..2026-10-16; min 20 training trades) vs the NAKED candidate as the reference (no live setting exists for these books); beat = lower period maxDD. The monthly WF (WF_ok in the ledger) is secondary: purged monthly walk-forward of the WHOLE dress-and-pick procedure (expanding train, 7-day embargo, test months 2024-03..2026-10): OOS dressed mean > 0, > naked OOS mean, maxDD <= naked OOS maxDD. p_proc = selection-aware null of the dressing GAIN (J_dressed - J_naked): B=100 null worlds per cell (random side + shifted entries, same count/lots/brackets), the whole screen + joint selection re-run in each; p = share of null gains >= the real gain; p_fam = max-stat over all finalists standardised null gains (independent cells, conservative, LOWER BOUND for the whole pool). seat_ok_any = F.clears-style (eq-mean maxDD cut on L6M and PRE, tolerant -3 pts on one) in at least one of add / replace-weakest (credit above the drop-only row) / replace-correlated, from fd_core.seat_test.

## 2. Ranked finalists (rank key: label, then dressed L6M mean; recents first per STANDING RULE 2)
| instr | sess | book (family / id) | naked L6M / PRE $/wk | naked dd L6M | dressed L6M / PRE $/wk | dressed dd L6M | carries | seat add cut L6M/PRE % (eq mean) | repl-weakest inc | repl-corr inc | corr | bi-weekly WF OOS (maxDD cut %, d mean $/wk, % periods beat, n) | p_proc | p_fam | p_plc | held-out 6 wk dressed / naked $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| GC | asia | T2FGC GC.T2FGC.5cf492de | 446 / -326 | 19,596 | 1,449 / 5 | 5,376 | STK | +4.0 / +3.4 | +3.0 / +3.0 | +10.2 / +3.5 | -0.08 | +26.3% / +82.7 / 76% / 72 | 0.77 | 1.00 | 0.04 | -2,331 / -16,510 | LEAD |
| GC | pre | T2FGC GC.T2FGC.5571faa5 | 395 / -429 | 8,074 | 538 / 2 | 2,399 | THP | +3.3 / +1.2 | +3.3 / +1.3 | +20.6 / +3.7 | -0.04 | +52.3% / +233.7 / 73% / 74 | 0.08 | 1.00 | 0.06 | 6,267 / 1,210 | LEAD |
| GC | pre | T2FGC GC.T2FGC.ea208d8d | 408 / -438 | 6,964 | 538 / 14 | 2,399 | THL | +3.3 / +1.2 | +3.3 / +1.3 | +20.6 / +3.7 | -0.03 | +49.0% / +215.6 / 73% / 74 | 0.24 | 1.00 | 0.07 | 2,895 / 1,210 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.c478779e | 77 / -188 | 17,078 | 517 / 113 | 3,859 | STK | +6.7 / +3.7 | +7.2 / +3.5 | +10.1 / +5.9 | -0.12 | +25.6% / +101.0 / 58% / 73 | 0.12 | 1.00 | 0.01 | 2,826 / -2,897 | LEAD |
| GC | asia | T2FGC GC.T2FGC.4722bad0 | -29 / -19 | 12,267 | 504 / 125 | 1,534 | SIZ | +2.5 / +0.3 | +3.2 / +0.2 | +20.4 / +4.0 | -0.03 | +73.2% / +158.0 / 57% / 74 | 0.99 | 1.00 | 0.10 | 898 / -4,818 | LEAD |
| YM | pre | T2FYM YM.T2FYM.a26b5100 | 97 / 100 | 11,552 | 492 / 185 | 4,373 | SIZ | +2.4 / +3.7 | +1.8 / +3.0 | +1.3 / +1.9 | 0.07 | +43.2% / +127.0 / 72% / 74 | 0.86 | 1.00 | 0.08 | 3,507 / 2,652 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.8816beed | 14 / -244 | 11,834 | 460 / 15 | 2,479 | THL | +5.2 / +2.2 | +5.3 / +2.0 | +26.0 / +7.3 | -0.06 | +13.3% / +73.0 / 60% / 73 | 0.18 | 1.00 | 0.01 | 696 / -2,097 | LEAD |
| CL | nypm | T2FCL CL.T2FCL.8469f21e | 425 / -248 | 7,147 | 372 / 29 | 3,503 | STK | +3.3 / +0.9 | +4.2 / +1.7 | +2.6 / +0.2 | 0.02 | +47.0% / +24.4 / 56% / 73 | 1.00 | 1.00 | 0.03 | 1,385 / -916 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.a6f08616 | -91 / -229 | 10,973 | 369 / 49 | 3,024 | ZON | +4.8 / +3.8 | +6.9 / +3.5 | +9.1 / +5.3 | -0.06 | +24.8% / +87.2 / 60% / 73 | 0.16 | 1.00 | 0.01 | 1,833 / -4,432 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.709934a8 | -130 / -173 | 12,914 | 335 / 64 | 4,743 | THL | +3.8 / +1.6 | +6.9 / +1.5 | +22.4 / +6.1 | -0.06 | +40.7% / +120.9 / 59% / 73 | 0.24 | 1.00 | 0.04 | 2,129 / -3,057 | LEAD |
| GC | nypm | T2FGC GC.T2FGC.4d02584a | -271 / -225 | 19,448 | 299 / 26 | 7,742 | SIZ | +1.0 / +0.5 | +2.3 / +0.6 | +31.9 / +6.5 | 0.14 | +23.5% / +40.5 / 59% / 74 | 0.92 | 1.00 | 0.10 | -2,198 / -7,191 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.140552d8 | 284 / -399 | 11,197 | 188 / 207 | 8,478 | ZON | +1.6 / -0.2 | +3.4 / +0.1 | +0.6 / -1.2 | -0.05 | +62.0% / +200.4 / 80% / 74 | 0.02 | 1.00 | 0.18 | 3,276 / -492 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.be193059 | 250 / -299 | 9,467 | 112 / 143 | 9,157 | ZON | +1.5 / -1.1 | +2.1 / -0.8 | +2.4 / -0.3 | -0.01 | +63.4% / +216.8 / 65% / 74 | 0.08 | 1.00 | 0.17 | 3,920 / -292 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.6fd681fb | 28 / -291 | 10,297 | 14 / 139 | 8,913 | ZON | -0.7 / -1.6 | +1.0 / -0.7 | -1.8 / -2.7 | -0.00 | +51.6% / +179.5 / 76% / 74 | 0.08 | 1.00 | 0.49 | 2,786 / -52 | LEAD |
| GC | asia | T2FGC GC.T2FGC.2e386e7b | 262 / -375 | 16,728 | 789 / 7 | 2,943 | STK | -0.1 / +3.7 | -1.1 / +3.9 | +5.9 / +3.4 | -0.22 | +51.2% / +134.4 / 72% / 72 | 0.27 | 1.00 | 0.33 | -3,798 / -14,020 | NOW-ONLY (own p fails) |
| BTC | nypm | CAPBREACH_gp_h30_nypm_q0.85_atr_3.0_None BTC.CAPBREACH_gp_h30_nypm_q0.85_atr_3.0_None.b7bf2328 | 222 / -443 | 6,417 | 467 / 149 | 4,979 | ZON | +0.4 / +0.3 | +1.5 / +1.5 | +28.6 / +3.9 | 0.17 | +64.6% / +285.6 / 54% / 71 | 0.66 | 1.00 | 0.34 | 1,792 / -882 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.6e10f673 | -619 / -596 | 39,935 | 429 / 12 | 7,524 | STK | -3.1 / +6.0 | +9.0 / +6.8 | -3.8 / +5.4 | -0.06 | +60.2% / +282.0 / 69% / 74 | 0.89 | 1.00 | 0.60 | 7,601 / 12,798 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.a6af1a8a | -619 / -596 | 39,935 | 429 / 12 | 7,524 | STK | -3.1 / +6.0 | +9.0 / +6.8 | -3.8 / +5.4 | -0.06 | +60.2% / +282.0 / 69% / 74 | 0.90 | 1.00 | 0.60 | 7,601 / 12,798 | NOW-ONLY (own p fails) |
| GC | asia | T2FGC GC.T2FGC.b73d4f64 | 140 / -32 | 9,886 | 427 / 141 | 1,389 | SIZ | +1.0 / -0.4 | +1.7 / -0.5 | +15.2 / +2.3 | -0.00 | +35.3% / +76.5 / 57% / 74 | 0.99 | 1.00 | 0.28 | 433 / -2,028 | NOW-ONLY (own p fails) |
| MBT | nyam | donchian MBT.donchian.bcf9a6e5 | 17 / -221 | 10,907 | 409 / -10 | 3,334 | STK | +0.4 / +1.6 | +0.8 / +2.2 | +35.3 / +8.3 | 0.09 | +28.3% / +20.3 / 62% / 74 | 0.96 | 1.00 | 0.29 | -2,129 / -4,551 | NOW-ONLY (own p fails) |
| YM | nyam | T2FYM YM.T2FYM.0d80268b | 759 / -338 | 6,151 | 385 / 67 | 1,783 | THP | -0.2 / +0.9 | +4.5 / +1.0 | +3.2 / +1.9 | -0.08 | +55.3% / +49.2 / 60% / 73 | 0.41 | 1.00 | 0.50 | -534 / -4,143 | NOW-ONLY (own p fails) |
| YM | asia | T2FYM YM.T2FYM.58b66d03 | 413 / -184 | 4,209 | 382 / 30 | 2,079 | SIZ | +2.3 / +1.2 | +3.3 / +1.3 | +2.9 / +1.9 | 0.13 | +61.4% / +133.7 / 67% / 64 | 0.82 | 1.00 | 0.11 | 1,577 / 7,756 | NOW-ONLY (own p fails) |
| MBT | pre | donchian MBT.donchian.e7096026 | 395 / -147 | 2,960 | 370 / 40 | 1,325 | STK | +0.4 / +1.0 | +0.7 / +1.4 | +1.2 / +0.5 | -0.13 | +64.3% / +130.5 / 68% / 74 | 0.25 | 1.00 | 0.18 | 1,987 / 3,233 | NOW-ONLY (own p fails) |
| GC | asia | T2FGC GC.T2FGC.e480d279 | 67 / -34 | 9,886 | 365 / 188 | 4,009 | STK | +0.8 / -1.8 | +0.8 / -1.9 | +13.5 / -2.9 | -0.14 | +60.2% / +166.5 / 62% / 74 | 1.00 | 1.00 | 0.32 | 898 / -1,458 | NOW-ONLY (own p fails) |
| GC | nyam | T2FGC GC.T2FGC.56c1e879 | 491 / -156 | 4,639 | 351 / 13 | 1,490 | STK | +1.0 / +0.6 | +3.4 / +1.1 | +4.7 / +2.0 | 0.09 | +73.1% / +56.7 / 52% / 65 | 0.33 | 1.00 | 0.24 | 2,623 / 3,302 | NOW-ONLY (own p fails) |
| GC | nyam | T2FGC GC.T2FGC.feb85183 | 654 / -132 | 4,639 | 327 / 49 | 2,934 | STK | +0.7 / +0.6 | +2.4 / +1.3 | +3.6 / +2.3 | 0.01 | +65.2% / +95.6 / 52% / 65 | 0.58 | 1.00 | 0.33 | 1,771 / 1,242 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.0481bdc8 | 229 / -141 | 12,777 | 322 / 86 | 2,193 | STK | +1.1 / -1.9 | +1.9 / -2.0 | +65.3 / -2.0 | 0.10 | +58.7% / +126.4 / 63% / 70 | 0.41 | 1.00 | 0.34 | 414 / 2,356 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.2940ca9e | 229 / -141 | 12,777 | 322 / 86 | 2,193 | STK | +1.1 / -1.9 | +1.9 / -2.0 | +65.3 / -2.0 | 0.10 | +58.7% / +126.4 / 63% / 70 | 0.54 | 1.00 | 0.34 | 414 / 2,356 | NOW-ONLY (own p fails) |
| YM | close | T2FYM YM.T2FYM.35295767 | 67 / -150 | 4,387 | 321 / 22 | 1,228 | SIZ | -0.6 / +0.8 | +6.1 / +1.2 | +9.7 / +3.0 | 0.07 | +53.5% / +165.9 / 52% / 62 | 0.11 | 1.00 | 0.67 | 3,624 / 503 | NOW-ONLY (own p fails) |
| YM | asia | T2FYM YM.T2FYM.8864ad19 | 424 / -148 | 4,209 | 320 / 34 | 2,312 | SIZ | +1.7 / +0.9 | +2.8 / +1.1 | +2.4 / +1.6 | 0.14 | +43.5% / +72.3 / 62% / 64 | 0.92 | 1.00 | 0.15 | 1,712 / 8,331 | NOW-ONLY (own p fails) |
| GC | nyam | T2FGC GC.T2FGC.2a936618 | 307 / -91 | 7,197 | 320 / 152 | 5,585 | SIZ | -0.2 / +0.6 | +1.5 / +1.3 | +1.4 / +1.5 | 0.02 | +52.9% / +153.9 / 68% / 74 | 0.84 | 1.00 | 0.38 | -2,895 / -1,944 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.1132e76a | 398 / -300 | 19,407 | 317 / 91 | 3,568 | STK | +0.9 / -1.8 | +2.1 / -1.3 | +42.5 / -2.2 | 0.16 | +55.6% / +111.9 / 66% / 70 | 0.39 | 1.00 | 0.25 | 783 / 7,516 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.7de2b0e2 | 398 / -300 | 19,407 | 317 / 91 | 3,568 | STK | +0.9 / -1.8 | +2.1 / -1.3 | +42.5 / -2.2 | 0.16 | +55.6% / +111.9 / 66% / 70 | 0.58 | 1.00 | 0.25 | 783 / 7,516 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.4780f85a | -400 / -349 | 14,026 | 307 / 36 | 1,677 | STK | +1.2 / +1.6 | +3.0 / +2.6 | +1.6 / +2.1 | 0.11 | +41.1% / +164.1 / 65% / 74 | 0.54 | 1.00 | 0.16 | -873 / -155 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.62cc8c4d | -400 / -349 | 14,026 | 307 / 36 | 1,677 | STK | +1.2 / +1.6 | +3.0 / +2.6 | +1.6 / +2.1 | 0.11 | +41.1% / +164.1 / 65% / 74 | 0.50 | 1.00 | 0.16 | -873 / -155 | NOW-ONLY (own p fails) |
| YM | london | T2FYM YM.T2FYM.7fb19bc3 | 150 / -241 | 13,286 | 300 / 26 | 3,178 | SIZ | +0.7 / +2.3 | +6.1 / +3.0 | +8.6 / +5.4 | -0.03 | +48.8% / +144.3 / 60% / 68 | 0.73 | 1.00 | 0.20 | 4,943 / 7,952 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.02f618b6 | 76 / -19 | 4,861 | 259 / 75 | 1,765 | ZON | +0.4 / +0.9 | +2.2 / +1.1 | +1.3 / +1.8 | 0.08 | +47.4% / +56.0 / 54% / 69 | 0.66 | 1.00 | 0.44 | -1,777 / 858 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.c6440e21 | 76 / -19 | 4,861 | 259 / 75 | 1,765 | ZON | +0.4 / +0.9 | +2.2 / +1.1 | +1.3 / +1.8 | 0.08 | +47.4% / +56.0 / 54% / 69 | 0.79 | 1.00 | 0.44 | -1,777 / 858 | NOW-ONLY (own p fails) |
| YM | london | T2FYM YM.T2FYM.93606c3a | 40 / -161 | 16,921 | 243 / 22 | 7,370 | SIZ | -0.2 / +2.0 | +6.0 / +2.8 | -1.6 / +0.7 | -0.02 | +36.8% / +89.7 / 65% / 68 | 0.76 | 1.00 | 0.50 | 4,220 / 8,382 | NOW-ONLY (own p fails) |
| CL | nypm | T2FCL CL.T2FCL.f5dc8789 | -255 / 60 | 13,066 | 243 / 36 | 2,439 | ZON | -0.1 / +0.2 | +3.0 / +1.3 | +3.0 / +1.3 | 0.03 | +26.0% / +71.1 / 64% / 69 | 1.00 | 1.00 | 0.39 | -528 / -521 | NOW-ONLY (own p fails) |

Equal-$-risk lots R = $1,200/trade (fd_core.lots_for, participation caps fd_core.LOT_CAP), fees/slippage as in each source screen (te2 cost proxies; no FEES.md line per instrument beyond ES/NQ/MES/6E: PROXY-STD), exits changed by TH/take/BE re-simulated on the 1-min path (fill at the next bar open - 1 tick; trail/BE on bar extremes; same-bar ambiguity keeps the baseline). 1-s refinement for GC/CL/ZN: see section 6.

## 3. Which layer carries it (finalists; J contribution = J(stack) - J(stack with that layer at reference))
| instrument | finalists | SIZ | THL | THP | ZON | LCK | STK | most frequent carrier |
|--|--|--|--|--|--|--|--|--|
| 6E | 3 | +21.2 | -1.3 | +1.4 | +4.9 | +0.0 | +37.3 | STK |
| BTC | 9 | +77.2 | -1.7 | +18.7 | +77.7 | +56.9 | +83.0 | ZON |
| CL | 14 | +75.8 | +15.2 | +15.5 | +60.2 | +0.0 | +38.4 | SIZ |
| GC | 138 | +32.2 | +4.9 | +14.7 | +41.7 | +0.0 | +37.6 | STK |
| MBT | 20 | +17.6 | -0.1 | +9.2 | +27.3 | +11.7 | +12.6 | ZON |
| YM | 49 | +63.0 | +3.8 | +19.3 | +53.4 | +0.0 | +35.6 | SIZ |
median J contribution per layer ($/wk-equivalent of the objective). THL/THP = price-path loss/profit rule, SIZ = ER sizer, ZON = zones, LCK = locks/cooldowns, STK = stack rules.

## 4. Session-by-session registry (SESSION BOOKs are never killed by the pooled row)
| instrument | session | finalists | bi-weekly beat >= 50% | LEAD or better | best dressed L6M $/wk |
|--|--|--|--|--|--|
| 6E | london | 3.0 | 0.0 | 0.0 | 68 |
| BTC | close | 5.0 | 3.0 | 0.0 | 405 |
| BTC | london | 2.0 | 2.0 | 0.0 | 924 |
| BTC | nypm | 2.0 | 1.0 | 0.0 | 467 |
| CL | london | 1.0 | 1.0 | 0.0 | 175 |
| CL | nyam | 2.0 | 0.0 | 0.0 | 43 |
| CL | nypm | 11.0 | 8.0 | 1.0 | 497 |
| GC | asia | 12.0 | 12.0 | 2.0 | 1,449 |
| GC | close | 21.0 | 6.0 | 0.0 | 211 |
| GC | london | 29.0 | 12.0 | 0.0 | 1,174 |
| GC | nyam | 28.0 | 23.0 | 7.0 | 2,588 |
| GC | nypm | 42.0 | 17.0 | 1.0 | 699 |
| GC | pre | 6.0 | 3.0 | 2.0 | 538 |
| MBT | close | 10.0 | 5.0 | 0.0 | 178 |
| MBT | nyam | 4.0 | 4.0 | 0.0 | 409 |
| MBT | nypm | 3.0 | 3.0 | 0.0 | 94 |
| MBT | pre | 3.0 | 3.0 | 0.0 | 370 |
| YM | asia | 9.0 | 5.0 | 0.0 | 382 |
| YM | close | 12.0 | 5.0 | 0.0 | 419 |
| YM | london | 4.0 | 4.0 | 0.0 | 300 |
| YM | nyam | 13.0 | 13.0 | 0.0 | 908 |
| YM | nypm | 5.0 | 4.0 | 0.0 | 160 |
| YM | pre | 6.0 | 6.0 | 1.0 | 492 |

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
pending

## REFIT 2026-11-22 (settings the bi-weekly procedure picks today; train = trailing 26 weeks to the data end 2026-10-16) - top 12 by bi-weekly OOS and L6M
* GC.T2FGC.5cf492de (asia): {"SIZ": "ER20(1-min bars) > 0.5 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 3 of 4 votes (momentum 0.2R/0.3D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "TH-profit(price path): PhMin 0.5R, PhReq 3/4 votes (window 0.3D), PhTrail 0.2R behind extreme", "ZON": "zones ALL: NOT within 0.5R of support behind entry -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW Mon x.5"}
* GC.T2FGC.2e386e7b (asia): {"SIZ": "ER20(1-min bars) > 0.5 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 3 of 4 votes (momentum 0.4R/0.15D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "break-even lock: after +0.8R stop to entry+0.2R", "ZON": "zones RN: NOT within 1.5R of support behind entry -> lots x0.5", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW Mon x.5"}
* GC.T2FGC.ea208d8d (pre): {"SIZ": "ER40(1-min bars) < 0.15 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.5R; cut when >= 3 of 4 votes (momentum 0.2R/0.3D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "near-target take at 0.9 of target distance", "ZON": "zones RN: NOT within 1.5R of support behind entry -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW Fri x.5"}
* GC.T2FGC.5571faa5 (pre): {"SIZ": "ER40(1-min bars) < 0.15 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.5R; cut when >= 3 of 4 votes (momentum 0.2R/0.3D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "near-target take at 0.9 of target distance", "ZON": "zones RN: NOT within 1.5R of support behind entry -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW Fri x.5"}
* GC.T2FGC.c478779e (nyam): {"SIZ": "ER80(1-min bars) > 0.25 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 2 of 4 votes (momentum 0.2R/0.3D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "TH-profit(price path): PhMin 0.3R, PhReq 3/4 votes (window 0.15D), PhTrail 0.5R behind extreme", "ZON": "zones PD: ahead < 1.0R -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW skip Mon"}
* GC.T2FGC.4722bad0 (asia): {"SIZ": "ER80(1-min bars) > 0.35 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 2 of 4 votes (momentum 0.4R/0.15D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "near-target take at 0.9 of target distance", "ZON": "zones PD: at < 1.0R -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW skip Mon"}
* YM.T2FYM.a26b5100 (pre): {"SIZ": "ER20(1-min bars) < 0.25 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.7R; cut when >= 3 of 4 votes (momentum 0.2R/0.15D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "near-target take at 0.75 of target distance", "ZON": "zones RN: ahead < 1.0R -> lots x0.0", "LCK": "lock/cooldown: 60 min after a loser, max 2 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 0 min / last 15 min of session; DOW none"}
* BTC.CAPBREACH_gp_h30_nypm_q0.85_atr_3.0_None.b7bf2328 (nypm): {"SIZ": "ER10(1-min bars) < 0.15 -> lots x0.5", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 2 of 4 votes (momentum 0.4R/0.15D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "TH-profit(price path): PhMin 0.3R, PhReq 3/4 votes (window 0.3D), PhTrail 0.5R behind extreme", "ZON": "zones SW: ahead < 0.5R -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 2 losers/day, weekly stop at -99.0R", "STK": "stack rule: skip first 0 min / last 15 min of session; DOW skip Mon"}
* GC.T2FGC.8816beed (nyam): {"SIZ": "ER80(1-min bars) > 0.25 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.3R; cut when >= 2 of 4 votes (momentum 0.4R/0.15D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "TH-profit(price path): PhMin 0.3R, PhReq 3/4 votes (window 0.3D), PhTrail 0.2R behind extreme", "ZON": "zones PD: at < 0.5R -> lots x0.0", "LCK": "lock/cooldown: 30 min after a loser, max 2 losers/day, weekly stop at -4.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW skip Mon"}
* GC.T2FGC.6e10f673 (london): {"SIZ": "ER40(1-min bars) < 0.35 -> lots x0.5", "THL": "TH-loss(price path): arm at adverse >= 0.7R; cut when >= 2 of 4 votes (momentum 0.4R/0.3D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "TH-profit(price path): PhMin 0.5R, PhReq 2/4 votes (window 0.15D), PhTrail 0.5R behind extreme", "ZON": "zones VW: at < 1.0R -> lots x0.5", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 15 min of session; DOW Mon+Fri x.5"}
* GC.T2FGC.a6af1a8a (london): {"SIZ": "ER40(1-min bars) < 0.35 -> lots x0.5", "THL": "TH-loss(price path): arm at adverse >= 0.7R; cut when >= 2 of 4 votes (momentum 0.4R/0.3D, stall .4D, efficiency<.3, depth 0.6R)", "THP": "TH-profit(price path): PhMin 0.5R, PhReq 2/4 votes (window 0.15D), PhTrail 0.5R behind extreme", "ZON": "zones VW: at < 1.0R -> lots x0.5", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 15 min of session; DOW Mon+Fri x.5"}
* GC.T2FGC.b73d4f64 (asia): {"SIZ": "ER80(1-min bars) > 0.35 -> lots x0.0", "THL": "TH-loss(price path): arm at adverse >= 0.7R; cut when >= 3 of 4 votes (momentum 0.4R/0.3D, stall .4D, efficiency<.3, depth 0.3R)", "THP": "near-target take at 0.9 of target distance", "ZON": "zones PD: at < 0.5R -> lots x0.0", "LCK": "lock/cooldown: 0 min after a loser, max 99 losers/day, weekly stop at -2.0R", "STK": "stack rule: skip first 0 min / last 0 min of session; DOW skip Mon"}

Prior check (TOLERANT, never kills): RECENT-ONLY = dressed PRE maxDD more than 15% deeper than the naked reference or PRE mean more than $1k/wk below it; the tag is appended to the label.

## 7. Method limits and open items
* First-order: per-trade re-simulation on 1-min bars; no re-entries after a changed exit, no slice/queue effects, lock/cooldown layer recomputed sequentially on the cell's own trades. Not an engine run. Layers are selected in-sample (2023-04..2026-10) with the WF as the honest read.
* 1-s: section 6 (GC, CL); YM/ZB/6E/6J/NKD/MBT/BTC have 1-min bars only. ZN and ZB produced no finalist (no dressed stack has FULL, L6M, PRE and HOLD means all > 0), so no 1-s run was needed.
* Price-path TH is a portable re-parameterisation (votes in R and in fractions of the book's planned hold D), NOT NQ's DS7 points grid; D7 panel values for these instruments do not exist (nothing is live).
* held-out = the last 6 data weeks (2026-09-28..11-09, train <= 2026-09-21), not the frozen NQ live file.

## 8. Regeneration audit (v1 lists -> v2 lists on core_bars)
Regenerated with the original generator code on a bar cache = old cache + core_bars rows after 2026-10-16: all T2F cells YM GC CL ZN ZB (2,699), block-B donchian/vwap/orb_fade finalists YM GC MBT (22), YM T2F-LRS finalists (6). On the 2023-04..2026-10-16 overlap every trade matches v1 (entry, side) and P&L matches 100% except 7 CL T2F cells:
| id | differing trades | first differing entry | exit_ts differs | sum of P&L difference $/lot (new - old) |
|--|--|--|--|--|
| CL.T2FCL.2577fc67 | 3 | 2025-09-17 | 2 | -30 |
| CL.T2FCL.39b01f22 | 5 | 2023-10-09 | 1 | +10 |
| CL.T2FCL.7dd3d21f | 11 | 2023-04-04 | 2 | -10 |
| CL.T2FCL.940d28e0 | 8 | 2023-04-04 | 2 | +20 |
| CL.T2FCL.c246d8e1 | 2 | 2023-04-20 | 0 | -20 |
| CL.T2FCL.c66e4ce1 | 3 | 2025-09-17 | 2 | +30 |
| CL.T2FCL.f5dc8789 | 7 | 2023-10-09 | 2 | -10 |
Cause: NOT the CL roll gap. The bars are identical: o/h/l/c/v of core_bars equal the v1 cache on every overlapping minute (0 differences in 1.67M bars), the differing trades sit a median of 76-222 hours from the nearest roll second, and the differences are one tick ($10/lot) on the exit fill and in 0-2 trades per cell an exit one bar earlier. The v1 lists came from an earlier run of the generator; the v2 run uses the current code on identical bars. Differences are immaterial (<= $222/lot over 3.5 years per cell). Which version is right cannot be decided from the bars; no roll adjustment is involved in either (raw .v.0 frame, the trade frame is the raw frame in both). FD-CORE can drop the blanket CL-ROLL? flag for these lists.
Not regenerated (still end 2026-10-16, v2 = False in the ledger): 6E FIND_ac (3 finalists), MBT FIND/LRS finalists (13), CL LRS (1), BTC (9; BTC bars have no new data), other non-T2F pool cells beyond the finalists. The 1-s check for GC/CL is not re-run (1-s bars end 2026-10-16).
