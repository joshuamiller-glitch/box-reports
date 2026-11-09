# FD_NOL2 - T-FIND-DRESSED, NO-L2 STACK (FD-NOL2), 2026-11-09 19:50Z

Research only, Shadow only, no PASS claims, first-order (no exact engine covers YM GC CL ZN ZB 6E 6J MBT NKD BTC). Every row is labelled **NO-L2 STACK** (ER sizer, price-path TH loss + profit, structural zones, locks/cooldowns, stack rules, near-target take / BE lock; the L2 state cut, book zones and L2 gate are NOT available: no depth on the box). Prereg line in DECISIONS.md (2026-11-09T19:25Z, code outputs/code/fd_nol2/). Windows as of 2026-11-09 (sz_core.WIN); **data end 2026-10-16** for every instrument here (L1M = 10-11..10-16 only, the live weeks 11-02..05 and 11-08.. are NOT in these lists: live-week column is n/a and nothing is labelled cleared).

Pool: every FD-CORE NOL2 candidate with prices on disk (has_px) and >= 60 trades since 2023-04: **2819 candidates dressed** (YM GC CL ZN ZB 6E 6J MBT NKD BTC), each with its OWN best stack found jointly: layer screens on its own trades -> top-3 per layer -> full factorial of the 3^6 = 729 joint stacks, every layer ON (standing rule), objective J = mean/wk - maxDD/weeks on 2023-04..2026-10 with layer retention >= 70% of lots (relaxed stepwise) and joint >= 30%. Not covered here (no price path in the lists): has_px = 0 rows (730 NOL2 rows incl. the 546 6E+6J relative-value pairs and the DAILY books) -> sizer/locks/stack-only pass pending.

## 1. Counts
| instrument | dressed | naked_pos_FULL | dressed_pos_FULL | finalists | WF_ok | p_proc<=.10 | seat_ok_any | LEAD+ |
|--|--|--|--|--|--|--|--|--|
| 6E | 15 | 0 | 5 | 3 | 0 | 0 | 3 | 0 |
| 6J | 22 | 0 | 6 | 0 |  |  |  |  |
| BTC | 55 | 11 | 20 | 9 | 2 | 0 | 9 | 0 |
| CL | 460 | 4 | 51 | 15 | 3 | 3 | 15 | 1 |
| GC | 717 | 107 | 257 | 152 | 26 | 7 | 136 | 6 |
| MBT | 60 | 8 | 28 | 20 | 4 | 0 | 20 | 0 |
| NKD | 31 | 0 | 2 | 0 |  |  |  |  |
| YM | 595 | 10 | 121 | 51 | 10 | 3 | 46 | 0 |
| ZB | 465 | 0 | 0 | 0 |  |  |  |  |
| ZN | 399 | 0 | 0 | 0 |  |  |  |  |

finalist = dressed FULL, L6M, PRE and HOLD means all > 0 (screen for the validation stage, not a verdict). WF_ok = purged monthly walk-forward of the WHOLE dress-and-pick procedure (expanding train, 7-day embargo, test months 2024-03..2026-10): OOS dressed mean > 0, > naked OOS mean, maxDD <= naked OOS maxDD. p_proc = selection-aware null of the dressing GAIN (J_dressed - J_naked): B=100 null worlds per cell (random side + shifted entries, same count/lots/brackets), the whole screen + joint selection re-run in each; p = share of null gains >= the real gain; p_fam = max-stat over all finalists standardised null gains (independent cells, conservative, LOWER BOUND for the whole pool). seat_ok_any = F.clears-style (eq-mean maxDD cut on L6M and PRE, tolerant -3 pts on one) in at least one of add / replace-weakest (credit above the drop-only row) / replace-correlated, from fd_core.seat_test.

## 2. Ranked finalists (top 40 by label, then dressed L6M + PRE at seat-add equal-mean cut)
| instr | sess | book (family / id) | naked L6M / PRE $/wk | naked dd L6M | dressed L6M / PRE $/wk | dressed dd L6M | carries | seat add cut L6M/PRE % (eq mean) | repl-weakest inc | repl-corr inc | corr | WF OOS dressed vs naked $/wk | p_proc | p_fam | p_plc | held-out 6 wk dressed / naked $ | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| GC | asia | T2FGC GC.T2FGC.ec6a3e8d | 685 / -234 | 5,820 | 628 / 79 | 3,864 | SIZ | +1.6 / +3.5 | +1.3 / +4.2 | +6.0 / +2.9 | -0.08 | 4 vs -59 | 0.89 | 1.00 | 0.08 | 459 / -1,310 | LEAD |
| GC | asia | T2FGC GC.T2FGC.3f595fd7 | 1,114 / -287 | 6,463 | 814 / 41 | 3,864 | SIZ | +2.2 / +1.7 | +2.0 / +1.6 | +6.7 / +1.2 | -0.04 | 46 vs -26 | 0.87 | 1.00 | 0.06 | 2,125 / 1,640 | LEAD |
| GC | nypm | T2FGC GC.T2FGC.23e6c972 | -41 / -69 | 6,137 | 402 / 99 | 2,305 | THP | +1.2 / +1.0 | +1.1 / +0.7 | +25.3 / +5.3 | 0.01 | 70 vs -27 | 0.01 | 0.95 | 0.14 | -242 / 1,863 | LEAD |
| GC | nypm | T2FGC GC.T2FGC.d0fd1884 | 39 / -6 | 5,062 | 402 / 96 | 2,305 | THP | +1.2 / +1.0 | +1.1 / +0.7 | +2.7 / +1.8 | 0.00 | 98 vs -17 | 0.05 | 1.00 | 0.16 | -1,005 / 1,863 | LEAD |
| CL | nypm | T2FCL CL.T2FCL.c246d8e1 | -305 / -176 | 8,746 | 221 / 1 | 794 | ZON | +0.6 / +0.5 | +0.6 / +0.5 | +1.6 / +1.5 | 0.06 | 5 vs -31 | 0.01 | 0.50 | 0.12 | 2,187 / -4,385 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.140552d8 | 263 / -399 | 11,197 | 118 / 207 | 8,478 | ZON | -0.2 / -0.7 | +0.2 / -0.1 | +0.2 / -1.7 | -0.04 | 16 vs -172 | 0.02 | 1.00 | 0.31 | -511 / 4,053 | LEAD |
| GC | nyam | T2FGC GC.T2FGC.be193059 | 279 / -299 | 9,467 | 64 / 143 | 9,157 | ZON | -0.3 / -1.4 | -0.0 / -1.0 | +2.1 / -0.5 | -0.00 | 109 vs -42 | 0.08 | 1.00 | 0.45 | 7,602 / 5,663 | LEAD |
| YM | nyam | orb_fade YM.orb_fade.9fdaa654 | 405 / -244 | 10,661 | 675 / 163 | 2,202 | THP | +1.8 / +6.4 | +1.3 / +5.9 | +0.7 / +4.7 | -0.04 | 133 vs 18 | 0.50 | 1.00 | 0.22 | 1,020 / 1,716 | NOW-ONLY (own p fails) |
| BTC | london | CAPBREACH_gp_h15_london_q0.7_atr_3.0_2R_ BTC.CAPBREACH_gp_h15_london_q0.7_atr_3.0_2R_.ae5b045a | 952 / 70 | 10,384 | 1,085 / 742 | 4,543 | LCK | +2.1 / +4.1 | +2.4 / +4.4 | +2.1 / +3.5 | 0.05 | 97 vs 82 | 0.94 | 1.00 | 0.27 | -5,406 / -4,335 | NOW-ONLY (own p fails) |
| YM | nyam | orb_fade YM.orb_fade.76862175 | 396 / -293 | 10,661 | 566 / 145 | 2,979 | THP | +1.3 / +4.7 | +0.9 / +4.3 | +3.5 / +7.1 | -0.07 | 110 vs 29 | 0.67 | 1.00 | 0.30 | 1,641 / 2,526 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.398a806e | 469 / -40 | 4,841 | 341 / 84 | 1,998 | STK | +1.7 / +1.8 | +0.8 / +0.9 | +1.6 / +1.6 | 0.12 | 48 vs 46 | 0.79 | 1.00 | 0.17 | 3,899 / 6,191 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.fea033f9 | 469 / -40 | 4,841 | 341 / 84 | 1,998 | STK | +1.7 / +1.8 | +0.8 / +0.9 | +1.6 / +1.6 | 0.12 | 48 vs 46 | 0.81 | 1.00 | 0.17 | 3,899 / 6,191 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.08b84e1c | -582 / 33 | 13,383 | 325 / 183 | 2,364 | STK | +0.7 / +1.6 | +0.6 / +1.6 | +4.8 / +0.8 | 0.04 | 34 vs -360 | 0.26 | 1.00 | 0.25 | 1,826 / -5,952 | NOW-ONLY (own p fails) |
| BTC | close | 30 BTC.30.02e1038e | 518 / -342 | 7,794 | 433 / 579 | 3,440 | ZON | +0.6 / +1.6 | +0.7 / +1.7 | +20.5 / -2.2 | 0.09 | 66 vs 2 | 0.88 | 1.00 | 0.40 | -702 / 6,250 | NOW-ONLY (own p fails) |
| YM | asia | T2FYM YM.T2FYM.c1190b45 | 51 / -174 | 4,209 | 155 / 8 | 2,312 | SIZ | +0.9 / +0.8 | +0.4 / +0.4 | +0.8 / +0.7 | 0.14 | 10 vs -19 | 0.82 | 1.00 | 0.12 | 461 / -146 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.0bbd1fd8 | 106 / -4 | 9,153 | 122 / 59 | 3,706 | ZON | +0.8 / +0.9 | +0.7 / +0.6 | +0.8 / +0.9 | 0.09 | 32 vs -23 | 0.95 | 1.00 | 0.14 | 3,152 / 2,488 | NOW-ONLY (own p fails) |
| YM | asia | T2FYM YM.T2FYM.58b66d03 | 147 / -184 | 4,209 | 330 / 54 | 2,062 | SIZ | +0.8 / +0.7 | +1.0 / +1.0 | +2.2 / +1.4 | 0.14 | 29 vs 21 | 0.62 | 1.00 | 0.11 | 1,661 / -2,386 | NOW-ONLY (own p fails) |
| CL | nypm | T2FCL CL.T2FCL.1cff3bf8 | -81 / -262 | 10,019 | 347 / 18 | 2,898 | STK | +0.8 / +0.8 | +1.6 / +1.7 | +3.8 / +1.8 | -0.09 | 23 vs -71 | 0.97 | 1.00 | 0.32 | 616 / -5,150 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.23a92c2d | -350 / 154 | 12,897 | 278 / 206 | 3,564 | STK | +0.5 / +1.0 | +0.9 / +1.9 | +16.9 / +2.9 | 0.00 | 17 vs 11 | 0.86 | 1.00 | 0.36 | 439 / -1,467 | NOW-ONLY (own p fails) |
| YM | asia | T2FYM YM.T2FYM.5a947621 | -201 / 8 | 5,531 | 58 / 65 | 2,801 | THP | +0.0 / +1.4 | +0.1 / +1.6 | +3.6 / +5.2 | 0.07 | 1 vs -4 | 0.96 | 1.00 | 0.49 | -248 / -1,356 | NOW-ONLY (own p fails) |
| YM | asia | T2FYM YM.T2FYM.8864ad19 | 153 / -148 | 4,209 | 263 / 53 | 2,312 | SIZ | +0.7 / +0.6 | +0.8 / +0.7 | +1.9 / +1.1 | 0.17 | 42 vs -1 | 0.79 | 1.00 | 0.15 | 1,861 / 104 | NOW-ONLY (own p fails) |
| GC | asia | T2FGC GC.T2FGC.4722bad0 | 58 / -19 | 9,886 | 503 / 125 | 1,534 | SIZ | +0.7 / +0.1 | +0.4 / -0.1 | +19.5 / +3.2 | -0.03 | 20 vs -57 | 0.98 | 1.00 | 0.42 | 268 / -7,323 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.6c920936 | 30 / -119 | 2,779 | 191 / 32 | 370 | SIZ | +0.3 / +0.4 | +0.6 / +0.6 | +0.7 / +0.8 | 0.02 | 26 vs 9 | 0.81 | 1.00 | 0.18 | 921 / -14 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.bb7c28d7 | -71 / -147 | 4,099 | 173 / 38 | 490 | SIZ | +0.2 / +0.3 | +0.5 / +0.5 | +0.6 / +0.7 | 0.08 | 23 vs -4 | 0.72 | 1.00 | 0.30 | 921 / -554 | NOW-ONLY (own p fails) |
| MBT | nypm | donchian MBT.donchian.2f510a06 | 340 / -363 | 2,802 | 153 / 177 | 1,894 | ZON | -0.9 / +1.4 | +0.5 / +1.5 | +1.5 / +2.5 | 0.16 | 31 vs 12 | 0.39 | 1.00 | 0.82 | 126 / 559 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.df3b46e5 | 200 / -27 | 8,483 | 188 / 52 | 3,708 | ZON | +0.1 / +0.3 | +0.6 / +0.7 | +0.9 / +1.2 | 0.03 | 9 vs -10 | 0.92 | 1.00 | 0.39 | 3,497 / 4,348 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.524b5460 | -3 / -77 | 8,377 | 226 / 112 | 2,305 | STK | +0.5 / -0.2 | +0.7 / -0.2 | +0.7 / -0.2 | 0.04 | 4 vs -10 | 0.18 | 1.00 | 0.27 | -898 / -3,297 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.cf6cd25f | 77 / -82 | 2,779 | 209 / 74 | 395 | ZON | +0.1 / +0.3 | +0.7 / +0.7 | +0.7 / +0.8 | -0.05 | 25 vs 11 | 0.90 | 1.00 | 0.35 | 650 / -74 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.5ac2e0fb | -71 / -90 | 4,099 | 156 / 95 | 490 | SIZ | +0.1 / +0.2 | +0.4 / +0.4 | +0.5 / +0.6 | -0.04 | 20 vs -6 | 0.96 | 1.00 | 0.38 | 1,305 / -284 | NOW-ONLY (own p fails) |
| MBT | close | 60 MBT.60.06c25a82 | -61 / 41 | 3,242 | 76 / 87 | 1,614 | ZON | +0.2 / -0.1 | +0.2 / -0.1 | +1.0 / +0.7 | -0.03 | 3 vs -31 | 0.92 | 1.00 | 0.49 | 1,319 / 138 | NOW-ONLY (own p fails) |
| GC | asia | T2FGC GC.T2FGC.b73d4f64 | 142 / -32 | 9,886 | 454 / 141 | 1,389 | SIZ | +0.5 / -0.4 | +0.2 / -0.6 | +14.9 / +2.0 | -0.01 | 29 vs -79 | 0.98 | 1.00 | 0.45 | 338 / -6,283 | NOW-ONLY (own p fails) |
| YM | close | T2FYM YM.T2FYM.50f3f8aa | 486 / -132 | 4,992 | 341 / 221 | 3,247 | SIZ | -0.6 / +0.4 | +1.3 / +1.0 | +9.7 / +2.3 | 0.11 | 137 vs 121 | 0.99 | 1.00 | 0.52 | -1,043 / 3,503 | NOW-ONLY (own p fails) |
| YM | asia | T2FYM YM.T2FYM.c6c637f7 | 159 / -182 | 2,252 | 154 / 18 | 1,721 | SIZ | -0.3 / +0.1 | +0.8 / +0.1 | -2.3 / -4.3 | 0.15 | 1 vs -37 | 0.57 | 1.00 | 0.49 | 2,824 / 523 | NOW-ONLY (own p fails) |
| YM | asia | T2FYM YM.T2FYM.a0d42803 | 66 / -254 | 5,552 | 75 / 19 | 1,912 | SIZ | -0.2 / -0.1 | +0.2 / +0.2 | +0.2 / +0.3 | 0.13 | 6 vs -62 | 0.42 | 1.00 | 0.43 | -839 / -1,886 | NOW-ONLY (own p fails) |
| MBT | close | 60 MBT.60.1442dccc | 110 / 38 | 2,420 | 60 / 50 | 1,536 | STK | -0.1 / -0.3 | +0.3 / -0.0 | -1.4 / -0.4 | 0.08 | 6 vs -10 | 1.00 | 1.00 | 0.48 | 631 / 620 | NOW-ONLY (own p fails) |
| YM | nyam | T2FYM YM.T2FYM.b78805cf | -573 / -347 | 16,688 | 37 / 171 | 6,062 | ZON | -1.0 / +0.5 | +0.1 / +1.0 | -10.8 / +3.4 | 0.01 | 2 vs -144 | 0.71 | 1.00 | 0.66 | 4,249 / 1,035 | NOW-ONLY (own p fails) |
| GC | london | T2FGC GC.T2FGC.c5386fee | 261 / 9 | 4,053 | 134 / 95 | 3,842 | ZON | -0.1 / -0.8 | +0.5 / -0.3 | +0.8 / +0.2 | 0.09 | 22 vs -16 | 0.98 | 1.00 | 0.52 | 3,362 / 3,028 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.1132e76a | 436 / -300 | 19,407 | 388 / 91 | 3,568 | STK | +0.6 / -1.8 | +1.2 / -1.4 | +42.8 / -2.0 | 0.16 | 5 vs -55 | 0.45 | 1.00 | 0.29 | -538 / -2,543 | NOW-ONLY (own p fails) |
| GC | nypm | T2FGC GC.T2FGC.7de2b0e2 | 436 / -300 | 19,407 | 388 / 91 | 3,568 | STK | +0.6 / -1.8 | +1.2 / -1.4 | +42.8 / -2.0 | 0.16 | 5 vs -55 | 0.44 | 1.00 | 0.29 | -538 / -2,543 | NOW-ONLY (own p fails) |
| CL | nypm | T2FCL CL.T2FCL.1a3ea7ee | -11 / -94 | 7,296 | 294 / 185 | 4,687 | THP | -1.3 / -0.4 | +1.5 / +0.4 | -1.8 / -0.9 | 0.03 | 19 vs 0 | 0.19 | 1.00 | 0.84 | 6,792 / 5,013 | NOW-ONLY (own p fails) |

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
| instrument | session | finalists | WF ok | LEAD or better | best dressed L6M $/wk |
|--|--|--|--|--|--|
| 6E | london | 3.0 | 0.0 | 0.0 | 80 |
| BTC | close | 5.0 | 1.0 | 0.0 | 476 |
| BTC | london | 2.0 | 1.0 | 0.0 | 1,085 |
| BTC | nypm | 2.0 | 0.0 | 0.0 | 548 |
| CL | nyam | 2.0 | 0.0 | 0.0 | 162 |
| CL | nypm | 13.0 | 3.0 | 1.0 | 467 |
| GC | asia | 17.0 | 5.0 | 2.0 | 814 |
| GC | close | 24.0 | 0.0 | 0.0 | 263 |
| GC | london | 25.0 | 8.0 | 0.0 | 1,090 |
| GC | nyam | 28.0 | 2.0 | 2.0 | 2,595 |
| GC | nypm | 39.0 | 11.0 | 2.0 | 907 |
| GC | pre | 5.0 | 0.0 | 0.0 | 549 |
| MBT | close | 10.0 | 2.0 | 0.0 | 231 |
| MBT | nyam | 4.0 | 1.0 | 0.0 | 342 |
| MBT | nypm | 3.0 | 1.0 | 0.0 | 153 |
| MBT | pre | 3.0 | 0.0 | 0.0 | 368 |
| YM | asia | 11.0 | 6.0 | 0.0 | 330 |
| YM | close | 10.0 | 1.0 | 0.0 | 629 |
| YM | london | 3.0 | 0.0 | 0.0 | 205 |
| YM | nyam | 11.0 | 3.0 | 0.0 | 1,053 |
| YM | nypm | 5.0 | 0.0 | 0.0 | 164 |
| YM | pre | 6.0 | 0.0 | 0.0 | 559 |

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
| GC | 138 | 98 | 94 | 93 | 111 -> 23 | 124 | 68 |

## 7. Method limits and open items
* First-order: per-trade re-simulation on 1-min bars; no re-entries after a changed exit, no slice/queue effects, lock/cooldown layer recomputed sequentially on the cell's own trades. Not an engine run. Layers are selected in-sample (2023-04..2026-10) with the WF as the honest read.
* 1-s: section 6 (GC, CL); YM/ZB/6E/6J/NKD/MBT/BTC have 1-min bars only. ZN and ZB produced no finalist (no dressed stack has FULL, L6M, PRE and HOLD means all > 0), so no 1-s run was needed.
* Price-path TH is a portable re-parameterisation (votes in R and in fractions of the book's planned hold D), NOT NQ's DS7 points grid; D7 panel values for these instruments do not exist (nothing is live).
* held-out = the last 6 data weeks (2026-09-07..10-16, train <= 2026-08-31), not the frozen NQ live file.
