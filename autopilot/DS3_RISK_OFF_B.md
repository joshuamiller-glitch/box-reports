# DS3_RISK_OFF_B - T-RISK-OFF part B (NTE-2): combinations, four-legged, staged ratchets, learned policy (2026-10-31)

Research only; no live / execution / chart change. UNTOUCHED never read (every frame capped at label day 20260206). Prereg autopilot/RISK_OFF_NTE2_prereg.md sha256 822fca42ad9314ffe22e4a8d940a6a47577434c4d77bc56342f11a5e38fb0f2e (addenda B and C appended before the combination / learned / staged cells were read; sha logged in DECISIONS.md at each stage); carry-list hashes: pass 1 950235a7566ea7110fcdc60d88c4072d8466a5fa455b2d425ede396259e16031, combinations b92495ab33e01ef5cdf9240928ba34db9de630e971a7bd865ce212f32ba5ad7b (each logged in autopilot/RISK_OFF_NTE2_looks.txt BEFORE its single recent look). Engine l2vast/ds3/code/riskoff/ (ro_engine = the moved-stop hook shared with RO-2; ro_trig, ro_pass1, ro_select, ro_look, ro_finalists, ro_stack, ro_combo, ro_staged, ro_learn*), outputs l2vast/ds3/out/riskoff/.

## Page 1 (the answer)
**NULL with one post-selection LEAD family. 0 PASS.** Combinations of the carried atoms (NTE-2 confirmation / volatility / time / decay / stack atoms and RO-2's order-book and progress atoms): 201,344 cell-scopes (AND pairs across families, AND triples, the four-legged path x book x confirmation x stack, any-2-of-8, any-3-of-8; x 8 destinations x 3 states x 2 ages). 17,308 are positive in both selection windows; 224 were carried; 143 of the 224 are positive in L6M and HOLD at the single look (the carried AND3 / AND4 cells average +0.24 / +0.17 in L6M, the AND2 cells -0.04). The finalists with the stack line: 46 LEAD-weak (recent > 0, placebo not beaten on both), 12 LEAD (placebo beaten; stack fails a window), 6 CANDIDATE-RECENT (stack >= 0 in all windows; inside MDE) (parts A and B together). The best cell is **`AND2[V_spike3 & S_same_stop]` -> stop to MAE+10, any state, age 0**: a 1-minute bar with range >= 3 x the 60-bar median printing AGAINST the trade, AND another D6 book on the same side having already been stopped while this trade is open. It is positive in all five windows (PRE +0.124, X' +0.150, L3M -0.002, L6M +0.078, HOLD +0.049 pts per contract per trade, ALL D6 books), beats both placebos in L6M (ranks 1.00 / 1.00; HOLD 0.93 / 1.00), touches 355 trades in L6M (3.7%; 218 stops avoided, 20 targets forfeited), and its lock-engine stack delta at live lots is positive in every window: L6M +978 $/wk (MDE 2,576), HOLD +451, PRE +1,084, X' +504, L3M +1,123. **It is inside its MDE in every window, was chosen from 201,344 cells, and its L3M per-contract gain is -0.002 (fading): tier CANDIDATE-RECENT at best (post-selection; program-level reality check not passed - Sidak over the 224 carried cells p = 1.00; single-cell one-sided p in L6M about 0.08).** At equal worst-20-weeks the stack allows 0.98x lots (worst-20-weeks -1,107,239 base vs -1,126,393 with the rule).

## 1. Method
Atoms (named before the combination run from the PRE u X' ranks of pass 1 and RO-2's tables; list in the prereg addendum B): confirm K_st5 K_st10 K_sub30_8 K_swbrk_tf15 K_ema8_21; volatility V_bar2atr V_spike3; time T_nextbound30 T_flat60; decay D_PE_ema20; order book (RO-2 definitions) IMB_A PUL_2 DEL_A SWP_3 ICE_30 MIC_A; progress (RO-2) PB_50_25 VEL_10 STL_600 MAER_10; stack S_same_stop S_opp_entry S_same_tgt (state = the event has occurred while the trade is open). Combination = AND (or k-of-n) of the atoms' row masks, then the move rule of part A. Selection PRE u X' only (gain > 0 in both, touched >= 150, rank by min t, top 10 per family x scope); one recent look at the carry list (sha b92495ab33e01ef5cdf9240928ba34db9de630e971a7bd865ce212f32ba5ad7b); finalists = positive in L6M and HOLD, deduplicated, placebos (60 draws) and the stack line.

## 2. Combination table
| combination family | cells x scopes | selected (both > 0, touched >= 150) | carried | positive L6M and HOLD | carried mean PRE | mean L6M | mean HOLD |
|---|---|---|---|---|---|---|---|
| COMBO_AND2 | 80,256 | 5,374 | 80 | 37 | +0.326 | -0.043 | -0.092 |
| COMBO_AND3 | 32,512 | 3,398 | 70 | 57 | +0.265 | +0.242 | +0.149 |
| COMBO_AND4 | 87,808 | 8,532 | 70 | 49 | +0.223 | +0.165 | +0.114 |
| COMBO_KOF2 | 384 | 0 | 0 | 0 | +nan | +nan | +nan |
| COMBO_KOF3 | 384 | 4 | 4 | 0 | +0.177 | -0.555 | -0.392 |

Per-book carried cells and the finalists with all columns:
| family | trigger | scope | dest | state | age s | PRE | X' | L6M [MDE] | HOLD | L6M @1.28 / @0.5 | touched L6M | avoided / forfeited L6M | P(tgt|held) | placebo rank L6M (rand / timing) | HOLD plc | stack L6M [MDE] / HOLD / PRE / X' ($/wk, live lots) | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| COMBO_AND2 | `AND2[V_bar2atr&VEL_10]` | SM | mae10 | always | 120 | +0.547 | +1.224 | +1.318 [2.10] | +1.090 | +1.333 / +1.343 | 59 | 30 / 4 | 0.80 | 0.07 / 0.15 | 0.38 | -6,683 [11,203] / -4,534 / -3,020 / -1,035 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND2 | `AND2[K_st5&MIC_A]` | SM | mae10 | profit | 0 | +0.503 | +0.719 | +0.717 [1.60] | +0.127 | +0.728 / +0.736 | 33 | 14 / 3 | 0.88 | 0.17 / 0.97 | 0.17 | -5,242 [7,769] / -5,286 / -1,571 / -1,303 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND4 | `AND4[PB_50_25&SWP_3&K_sub30_8&S_same_stop]` | SM | atr15 | always | 120 | +0.405 | +0.572 | +0.597 [1.39] | +0.215 | +0.608 / +0.616 | 36 | 25 / 3 | 0.75 | 1.00 / 0.00 | 0.95 | -2,843 [7,646] / -2,566 / -579 / +2,142 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND3 | `AND3[K_st5&PUL_2&STL_600]` | SM | mae10 | profit | 120 | +0.412 | +0.569 | +0.584 [1.32] | +0.328 | +0.595 / +0.602 | 37 | 15 / 3 | 0.89 | 0.02 / 0.75 | 0.03 | -3,681 [7,542] / -3,382 / -2,250 / -2,343 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND4 | `AND4[MAER_10&PUL_2&K_sub30_8&S_same_tgt]` | HM | mae5 | always | 120 | +0.324 | +0.371 | +0.228 [0.67] | +0.186 | +0.235 / +0.239 | 106 | 46 / 4 | 0.84 | 0.60 / 1.00 | 0.60 | -1,329 [6,063] / -1,159 / +59 / +45 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND4 | `AND4[MAER_10&PUL_2&K_st10&S_opp_entry]` | MV | mae5 | always | 0 | +0.188 | +0.561 | +0.206 [0.44] | +0.211 | +0.209 / +0.211 | 66 | 42 / 2 | 0.81 | 0.97 / 1.00 | 0.82 | +443 [3,083] / -115 / -402 / -424 | LEAD (placebo beaten; stack fails a window) |
| COMBO_AND2 | `AND2[V_bar2atr&ICE_30]` | MV | mae5 | profit | 120 | +0.128 | +0.323 | +0.198 [0.42] | +0.075 | +0.202 / +0.205 | 39 | 12 / 2 | 0.70 | 0.98 / 1.00 | 0.98 | +964 [4,385] / +1,114 / +403 / +1,316 | CANDIDATE-RECENT (stack >= 0 in all windows; inside MDE) |
| COMBO_AND4 | `AND4[MAER_10&SWP_3&K_sub30_8&S_same_tgt]` | HM | mae5 | always | 120 | +0.360 | +0.576 | +0.167 [0.83] | +0.183 | +0.181 / +0.191 | 135 | 58 / 4 | 0.89 | 0.22 / 1.00 | 0.22 | -1,703 [6,621] / -1,505 / -504 / -637 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND3 | `AND3[K_st5&IMB_A&S_same_stop]` | PB | sw5 | under | 120 | +0.360 | +0.647 | +0.165 [0.97] | +0.008 | +0.176 / +0.184 | 74 | 49 / 8 | 0.76 | 1.00 / 1.00 | 1.00 | -698 [5,341] / -727 / +556 / +1,763 | LEAD (placebo beaten; stack fails a window) |
| COMBO_AND4 | `AND4[VEL_10&DEL_A&K_st5&S_same_stop]` | PE | mae5 | under | 120 | +0.242 | +0.320 | +0.159 [0.50] | +0.147 | +0.163 / +0.166 | 57 | 42 / 4 | 0.45 | 0.98 / 0.00 | 1.00 | +703 [3,967] / +778 / +1,620 / +1,271 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND3 | `AND3[K_st5&MAER_10&S_same_stop]` | PB | atr15 | under | 120 | +0.564 | +0.990 | +0.129 [1.16] | +0.269 | +0.154 / +0.170 | 160 | 109 / 14 | 0.52 | 1.00 / 0.00 | 1.00 | +969 [6,348] / +692 / +1,317 / +1,357 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND3 | `AND3[K_st5&S_same_stop&DEL_A]` | ALL | mae5 | always | 120 | +0.107 | +0.260 | +0.125 [0.31] | +0.091 | +0.131 / +0.135 | 527 | 395 / 40 | 0.54 | 1.00 / 0.02 | 1.00 | +864 [5,897] / +553 / +1,525 / +1,343 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND4 | `AND4[MAER_10&ICE_30&K_st10&S_opp_entry]` | MV | mae5 | always | 120 | +0.193 | +0.493 | +0.116 [0.43] | +0.168 | +0.123 / +0.127 | 70 | 46 / 3 | 0.89 | 1.00 / 0.93 | 0.95 | +2,102 [2,076] / +1,324 / +373 / -450 | LEAD (placebo beaten; stack fails a window) |
| COMBO_AND3 | `AND3[K_st5&V_bar2atr&S_same_stop]` | ALL | atr1 | always | 120 | +0.093 | +0.131 | +0.104 [0.19] | +0.081 | +0.106 / +0.108 | 177 | 132 / 14 | 0.32 | 1.00 / 0.00 | 1.00 | +1,682 [3,223] / +966 / +2,260 / +210 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND4 | `AND4[VEL_10&DEL_A&K_st5&S_same_stop]` | KB | mae5 | under | 120 | +0.182 | +0.234 | +0.096 [0.51] | +0.131 | +0.099 / +0.102 | 53 | 35 / 3 | 0.50 | 0.98 / 0.00 | 1.00 | +703 [3,967] / +778 / +1,620 / +1,271 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND4 | `AND4[MAER_10&SWP_3&K_sub30_8&S_opp_entry]` | HM | mae10 | under | 0 | +0.236 | +0.345 | +0.079 [0.40] | +0.086 | +0.082 / +0.084 | 55 | 27 / 2 | 0.77 | 0.18 / 1.00 | 0.08 | -1,047 [3,971] / -1,088 / -210 / +488 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND4 | `AND4[MAER_10&PUL_2&K_sub30_8&S_same_tgt]` | HM | atr1 | always | 0 | +0.597 | +0.861 | +0.079 [1.49] | +0.174 | +0.138 / +0.178 | 121 | 52 / 37 | 0.83 | 0.88 / 1.00 | 0.90 | -2,852 [8,915] / -2,691 / -1,571 / -92 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND2 | `AND2[V_spike3&S_same_stop]` | ALL | mae10 | always | 0 | +0.124 | +0.150 | +0.078 [0.16] | +0.049 | +0.081 / +0.083 | 355 | 218 / 20 | 0.65 | 1.00 / 1.00 | 0.93 | +978 [2,576] / +451 / +1,084 / +504 | CANDIDATE-RECENT (stack >= 0 in all windows; inside MDE) |
| COMBO_AND3 | `AND3[V_bar2atr&STL_600&S_same_stop]` | ALL | atr15 | always | 0 | +0.095 | +0.147 | +0.076 [0.21] | +0.063 | +0.080 / +0.083 | 232 | 154 / 26 | 0.52 | 0.98 / 0.00 | 0.98 | +1,742 [2,692] / +2,116 / +1,071 / +289 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND4 | `AND4[VEL_10&DEL_A&K_st5&S_same_stop]` | ALL | mae5 | under | 0 | +0.120 | +0.127 | +0.064 [0.20] | +0.082 | +0.068 / +0.070 | 316 | 221 / 24 | 0.39 | 0.98 / 0.00 | 1.00 | +703 [3,967] / +778 / +1,620 / +1,271 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND2 | `AND2[V_spike3&S_same_stop]` | PE | atr15 | under | 0 | +0.261 | +0.534 | +0.062 [0.65] | +0.091 | +0.075 / +0.084 | 81 | 49 / 8 | 0.63 | 0.98 / 0.00 | 0.93 | +1,310 [4,624] / +938 / +2,431 / +1,682 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND2 | `AND2[V_spike3&S_same_stop]` | PE | mae10 | always | 0 | +0.154 | +0.323 | +0.061 [0.41] | +0.091 | +0.066 / +0.069 | 62 | 41 / 4 | 0.62 | 1.00 / 0.97 | 0.95 | +978 [2,576] / +451 / +1,084 / +504 | CANDIDATE-RECENT (stack >= 0 in all windows; inside MDE) |
| COMBO_AND2 | `AND2[K_st10&T_nextbound30]` | PE | atr1 | profit | 0 | +0.536 | +0.691 | +0.058 [1.17] | +0.145 | +0.093 / +0.117 | 75 | 33 / 28 | 1.00 | 1.00 / 1.00 | 1.00 | -1,504 [7,242] / -401 / -805 / -381 | LEAD (placebo beaten; stack fails a window) |
| COMBO_AND3 | `AND3[K_st5&PUL_2&S_same_stop]` | KB | mae5 | under | 120 | +0.173 | +0.317 | +0.052 [0.65] | +0.096 | +0.060 / +0.066 | 96 | 67 / 7 | 0.55 | 1.00 / 0.00 | 1.00 | +226 [6,018] / -124 / +856 / -519 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND4 | `AND4[MAER_10&PUL_2&K_st10&S_opp_entry]` | MV | mae10 | always | 120 | +0.139 | +0.295 | +0.034 [0.41] | +0.046 | +0.037 / +0.038 | 51 | 27 / 2 | 0.64 | 0.47 / 0.98 | 0.28 | -162 [3,227] / -699 / -396 / -968 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND3 | `AND3[PUL_2&MAER_10&S_same_stop]` | KB | mae10 | always | 120 | +0.156 | +0.157 | +0.034 [0.51] | +0.036 | +0.039 / +0.042 | 93 | 57 / 5 | 0.77 | 0.48 / 0.82 | 0.08 | +633 [2,982] / +315 / -156 / -561 | LEAD-weak (recent > 0, placebo not beaten on both) |
| COMBO_AND3 | `AND3[K_st5&IMB_A&S_same_stop]` | ALL | mae10 | profit | 0 | +0.022 | +0.047 | +0.017 [0.05] | +0.005 | +0.018 / +0.018 | 54 | 23 / 3 | 0.89 | 0.98 / 1.00 | 0.80 | +321 [565] / +119 / +133 / +333 | CANDIDATE-RECENT (stack >= 0 in all windows; inside MDE) |
| COMBO_AND4 | `AND4[STL_600&IMB_A&K_st5&S_same_stop]` | ALL | mae10 | profit | 120 | +0.021 | +0.047 | +0.013 [0.05] | +0.006 | +0.014 / +0.014 | 52 | 22 / 3 | 0.89 | 0.98 / 0.97 | 0.80 | +321 [565] / +113 / +156 / +333 | CANDIDATE-RECENT (stack >= 0 in all windows; inside MDE) |
| COMBO_AND4 | `AND4[PB_50_25&IMB_A&K_st5&S_same_stop]` | ALL | mae10 | profit | 0 | +0.017 | +0.046 | +0.010 [0.06] | +0.013 | +0.011 / +0.011 | 46 | 21 / 3 | 0.86 | 0.92 / 0.90 | 0.98 | +321 [565] / +281 / +156 / +328 | CANDIDATE-RECENT (stack >= 0 in all windows; inside MDE) |

Reading. (1) Every part-B cell that is positive in all recent windows contains the stack atom S_same_stop (another same-side book already stopped): that atom alone, paired with the volatility atom, carries the whole candidate; the order-book and progress atoms add nothing (the AND3 / AND4 cells that add IMB_A, K_st5, STL_600 touch 50-200 trades in 6 months and their stack gain is a fraction of the AND2's: the same 50 trades). (2) The timing placebo is NOT beaten by the cells that use K_st5 / V_bar2atr + S_same_stop with ATR destinations (ranks 0.00): when the same trades are tightened at other times the gain is as large, so the information is in WHICH trades (a second book has already been stopped = the market is against the side), not in WHEN. (3) The per-book HM / MV cells with S_same_tgt / S_opp_entry have +0.1 to +0.3 pts but MDE 0.4-0.8 and a stack that fails at least one window.

## 3. Staged ratchets and asymmetric re-widen (6 pre-specified rules, PRE / X' only)
| staged rule (stage 1 -> 2 -> 3, destination) | re-widen | PRE gain | X' gain | touched PRE |
|---|---|---|---|---|
| V_spike3 -> MAE+10 ; K_st5 -> 5-min swing ; S_same_stop -> 1 ATR | no | -0.267 | +0.057 | 5,860 |
| same | yes (to the original stop when the book is WITH) | -0.203 | -0.290 | 5,860 |
| S_same_stop -> MAE+10 ; K_st5 -> 1 ATR ; IMB_A -> 5-min swing | no | -0.102 | +0.019 | 2,616 |
| same | yes | -0.071 | +0.063 | 2,616 |
| V_spike3 -> MAE+10 ; S_same_stop -> MAE+10 ; K_st5 -> 1 ATR | no | -0.325 | +0.248 | 5,860 |
| control: V_spike3 -> MAE+10 alone | no | -0.325 | +0.248 | 5,860 |
No staged rule is positive in PRE; none was carried. Re-widening to the original stop when the book is WITH again (RO-2's gate) makes the staged rules worse in X' for the first rule and slightly better in PRE, never positive: the 'do not tighten when support is holding' gate does not help.

## 4. Learned policy (walk-forward)
Rows: every 5 minutes of every open D6 trade (601,358 rows, >= 60 s in); labels: gain_j(row) = pnl(stop moved to destination j at this row, held to the original exit) - pnl(hold) for j in {BE+4t, MAE+10, 5-m swing, 1 ATR, lock 50%, halfway} (NaN when the move is not allowed at the row); 33 path / book features + 23 bar-state mirrors + 3 stack-event flags + book / session / side; LightGBM regression per destination, retrained monthly (or every 3 months) on the previous 12 months of rows from trades that closed before the test month (first test month 2023-10; 487,626 out-of-sample rows), fits v0 (unweighted rows) and w (each row weighted by 1 / rows of its trade); policy: at the first sampled row where max_j prediction > theta, move to the argmax destination; placebos: label-shuffled training, prediction-row-shuffled.
| fit | policy | theta (pts) | PRE | X' | L6M | HOLD | touched share L6M |
|---|---|---|---|---|---|---|---|
| v0 unweighted, monthly refit | model | 0.25 | -0.814 | -0.244 | -1.256 | -1.077 | 0.46 |
| v0 unweighted, monthly refit | model | 1.0 | -0.766 | -0.257 | -1.269 | -1.094 | 0.46 |
| v0 unweighted, monthly refit | model | 2.0 | -0.774 | -0.229 | -1.289 | -1.123 | 0.45 |
| v0 unweighted, monthly refit | label-shuffled placebo | 0.25 | -0.917 | -0.378 | -1.234 | -1.054 | 0.46 |
| v0 unweighted, monthly refit | label-shuffled placebo | 1.0 | -0.913 | -0.378 | -1.255 | -1.073 | 0.46 |
| v0 unweighted, monthly refit | label-shuffled placebo | 2.0 | -0.907 | -0.370 | -1.272 | -1.088 | 0.46 |
| v0 unweighted, monthly refit | feature(prediction)-shuffled placebo | 0.25 | -0.929 | -0.465 | -1.488 | -1.344 | 0.46 |
| v0 unweighted, monthly refit | feature(prediction)-shuffled placebo | 1.0 | -0.913 | -0.466 | -1.486 | -1.318 | 0.46 |
| v0 unweighted, monthly refit | feature(prediction)-shuffled placebo | 2.0 | -0.895 | -0.473 | -1.510 | -1.368 | 0.45 |
| v0 unweighted, 3-month refit | model | 0.25 | -0.795 | -0.283 | -1.137 | -0.969 | 0.46 |
| v0 unweighted, 3-month refit | model | 1.0 | -0.781 | -0.288 | -1.143 | -0.980 | 0.46 |
| v0 unweighted, 3-month refit | model | 2.0 | -0.730 | -0.250 | -1.131 | -0.979 | 0.45 |
| v0 unweighted, 3-month refit | label-shuffled placebo | 0.25 | -0.884 | -0.378 | -1.323 | -1.129 | 0.46 |
| v0 unweighted, 3-month refit | label-shuffled placebo | 1.0 | -0.898 | -0.378 | -1.320 | -1.126 | 0.46 |
| v0 unweighted, 3-month refit | label-shuffled placebo | 2.0 | -0.893 | -0.378 | -1.281 | -1.095 | 0.46 |
| v0 unweighted, 3-month refit | feature(prediction)-shuffled placebo | 0.25 | -0.832 | -0.571 | -1.339 | -1.166 | 0.46 |
| v0 unweighted, 3-month refit | feature(prediction)-shuffled placebo | 1.0 | -0.833 | -0.562 | -1.299 | -1.130 | 0.46 |
| v0 unweighted, 3-month refit | feature(prediction)-shuffled placebo | 2.0 | -0.855 | -0.591 | -1.253 | -1.091 | 0.45 |
| weighted, monthly refit | model | 0.25 | -0.811 | -0.280 | -1.236 | -1.074 | 0.46 |
| weighted, monthly refit | model | 1.0 | -0.808 | -0.278 | -1.223 | -1.065 | 0.46 |
| weighted, monthly refit | model | 2.0 | -0.788 | -0.282 | -1.232 | -1.092 | 0.45 |
| weighted, monthly refit | label-shuffled placebo | 0.25 | -0.839 | -0.342 | -1.276 | -1.105 | 0.46 |
| weighted, monthly refit | label-shuffled placebo | 1.0 | -0.857 | -0.333 | -1.280 | -1.105 | 0.46 |
| weighted, monthly refit | label-shuffled placebo | 2.0 | -0.879 | -0.353 | -1.281 | -1.110 | 0.45 |
| weighted, monthly refit | feature(prediction)-shuffled placebo | 0.25 | -0.926 | -0.526 | -1.479 | -1.313 | 0.46 |
| weighted, monthly refit | feature(prediction)-shuffled placebo | 1.0 | -0.958 | -0.507 | -1.505 | -1.343 | 0.46 |
| weighted, monthly refit | feature(prediction)-shuffled placebo | 2.0 | -1.000 | -0.493 | -1.482 | -1.313 | 0.46 |
| weighted, 3-month refit | model | 0.25 | -0.791 | -0.279 | -1.346 | -1.180 | 0.46 |
| weighted, 3-month refit | model | 1.0 | -0.795 | -0.276 | -1.339 | -1.177 | 0.46 |
| weighted, 3-month refit | model | 2.0 | -0.761 | -0.283 | -1.367 | -1.220 | 0.45 |
| weighted, 3-month refit | label-shuffled placebo | 0.25 | -0.771 | -0.373 | -1.336 | -1.185 | 0.46 |
| weighted, 3-month refit | label-shuffled placebo | 1.0 | -0.773 | -0.366 | -1.315 | -1.166 | 0.46 |
| weighted, 3-month refit | label-shuffled placebo | 2.0 | -0.782 | -0.382 | -1.295 | -1.155 | 0.46 |
| weighted, 3-month refit | feature(prediction)-shuffled placebo | 0.25 | -0.838 | -0.615 | -1.391 | -1.215 | 0.46 |
| weighted, 3-month refit | feature(prediction)-shuffled placebo | 1.0 | -0.828 | -0.610 | -1.334 | -1.154 | 0.46 |
| weighted, 3-month refit | feature(prediction)-shuffled placebo | 2.0 | -0.816 | -0.644 | -1.318 | -1.146 | 0.46 |
**Verdict: no skill.** The policy touches 45% of trades and loses -0.7 to -1.3 pts per contract per trade in every window at theta <= 2 pts; the label-shuffled and prediction-shuffled placebos lose about the same (-0.9 to -1.5); raising theta to 16 pts cuts the touch rate to 9% and the loss to -0.14 L6M / -0.05 HOLD (-0.30 PRE) - still negative, and the label-shuffled placebo goes to 0.00 only because it never fires. Calibration (out-of-sample, decile of predicted gain vs realised gain of the argmax destination, PRE u X'): predicted -0.3 ... +14.0 pts, realised -0.7 ... -6.6; the correlation is -0.03 (v0) / -0.01 (be4 head); L6M deciles are flat at -2 to -4. The labels are dominated by month-to-month regime swings of +-10 pts (mean label -1.2 to -1.8, median 0), which a 12-month window cannot forecast.
Extracted tree (<= 6 leaves per destination on the PRE u X' row labels; descriptive, in words): MAE+10 pays on rows where the trade has recovered >= 24 pts off its MAE or MAE is deep (MAE > 13) in Asia / London; 5-m swing and 1-ATR destinations pay on under-water rows (upnl <= 0.9 ... -7 to -11 pts) and lose on in-profit rows with pct > 0.26 (the row-level means are +4 to +10 pts). Policy 'fire at the first row in a positive leaf': MAE+10 {PRE -0.905, X' -0.359, L6M -1.277, HOLD -1.081}, 5-m swing {-0.775, -0.557, -1.011, -0.914}, 1 ATR {-0.731, -0.676, -1.198, -1.082}: the retained gain is negative in every window including the selection windows - the row-level label average (time-weighted) is positive because long under-water trades contribute many rows, while the first-fire policy moves early in every trade.

## 5. Not done
Learned E[remaining]; a learned policy with the stack state as an explicit sequential context; 3-month WEEKLY refits (monthly and 3-monthly done); the four-legged cells beyond path x book x confirmation(4) x stack; re-widen on the NTE-2 carried cells except the six staged rules (RO-2 covers re-widen for its carried cells).
