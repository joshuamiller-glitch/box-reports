# DS3_DIV2_D_STATE - stack-state conditional books (T-DIVERSIFY-2 section D, agent D3D2D, 2026-10-28)
Research only; no live / execution / chart change; no account number; no download or purchase; UNTOUCHED (label day > 2026-02-06) never read. Prereg `l2vast/ds3/prereg/DV2D_prereg.md` sha256 `3abb1a96e72c322ea7d76607621f783777b51d6dd51c7500fcbaefb854bf3064` (16 cells, F = 16, frozen in DECISIONS.md before any candidate P&L); PRE-only text `DS3_DIV2_D_PREHOLD.md` sha256 `9c0907789218cc5bc2148b9c129945ac272ed3dec2f9ed4634d04f6a0b9f25ae`, logged (tracks DS3_DV2D, DS3_DV2D_SPAN2) before HOLD 2025-07-01..2026-02-06 and the second holdout 2023-04..2024-01 were scored (one look, both read together). Code `l2vast/ds3/code/dv2d/` (d_lib, d_trig, d_cells, d_thcuts, d_score, d_placebo, d_prehold, d_report), outputs `l2vast/ds3/out/dv2d/`.

## 1. Verdict (plain)
**0 CONFIRMED, 0 LEAD, 0 CANDIDATE, 16 DEAD. None of the four stack-state books earns money out of sample on the conservative basis, and none is a worst-weeks hedge worth its cost.** Where the stack loses (chop weeks) the state-triggered books do not reliably win: the best worst-20-weeks result is a book that loses overall.
- **The one number (section D):** $ in the stack's 20 worst weeks (ALL window 2023-04-03..2026-02-06, stack alone -$3,534,170) at 20% risk, best cell regardless of verdict = **+$127,831 (D1_C60, counter-trend after a stop-out cluster, 60/60, 11.3 lots), but that cell loses -$2,055/wk in PRE (CI [-7,805, +3,913]) and -$7,444/wk in HOLD; DEAD.** No CONFIRMED cell, so the CONFIRMED worst-20 number is $0 (nothing to add). Next: D1_K60 +$75,611, D2_LF +$36,735; the other 13 cells lose money in the worst weeks (D2_NB -$342,598, D2_LB -$218,334, D4_RNT -$240,359).
- Per book: **D1 counter-trend after a loss cluster: DEAD x4** (PRE -$1.8k to -$2.7k/wk at 10 lots on the 60/60 and 40/40 cluster cells, HOLD more negative; KB-keyed ~0 in PRE, negative in HOLD). **D2 idle-hours: DEAD x4** (lunch fade is the only positive PRE cell, +2.4 pts/trade, then HOLD -$5.6k/wk and X -$2.2k/wk at 10 lots; both night cells (22:00-02:00) are significantly NEGATIVE, CI excludes 0). **D3 TH-cut re-entry: DEAD x4** (pooled book +$5.1k/wk PRE at 10 lots, P1/P2 ranks 0.94/0.90, but X -$3.5k/wk, fails best-of-F and a worst-20-weeks add of -$173k at 20% risk). **D4 reversal-day: DEAD x4** (24 PRE trades for the 1.0x cells, MDE 7-10x the mean; the 0.5x cell has PRE +$1.9k/wk book CI [73, 3,953], P1/P2 rank 0.95/0.95, then HOLD -$0.8k/wk).
- Best-of-F null (max over the 16 cells of the P1 PRE weekly mean): 95th pct $6,944/wk, 99th $9,123/wk; the best observed cell (D3_ALL PRE $5,124/wk) does not reach it (p = 0.20). Every cell fails g8.
- The plain read behind it: the stack's losses come from false breakouts in a chop day; a mean-reversion counter on the same stop-out events fills at the band only after the move has gone, and after the conservative costs (limit needs 1 tick through, stop -2 ticks, commission 4.84) the expectation is 0 to -2.5 pts per trade. On ex-post RANGE days the D1 books do earn (D1_C60 +$455k over ALL at 20%) and on trend days they give it back (-$403k, plus -$307k on reversal days): the hedge exists only with the hindsight day label, which is not tradable (see 4).

## 2. What was run (rules fixed in the prereg; deviations in 7)
- Stack = A's per-trade table (`l2vast/ds3/out/dv2a/stack_trades.parquet`, exact lock engine, DS3 monthly weights, sweep netted), CUT at 2026-02-06 (A's own table runs to 2026-10-16; the cut rows are never used). 149 weeks (2023-04-03..2026-02-06): mean $39,564/wk, PRE 74 wk $47,945/wk SD $133,462, HOLD 31 wk, X 44 wk.
- Windows: PRE 2024-02..2025-06 (selection / first look), HOLD 2025-07..2026-02-06, X 2023-04..2024-01. No parameter was tuned; PRE is the first look.
- Basis (conservative, direct-style on the 1-s DS2 path): limit fills need 1 tick THROUGH and fill at the level; stop-type entries trigger 1 tick through and fill 2 ticks worse; stop exits -2 ticks (gap = previous close); targets need 1 tick through; time exit market -1 tick; commission $4.84 RT. No mapped stop-exit credit anywhere. Own lock (o2_eng.run_ext, R_own = 10 lots x median stop x $20) at 10 nominal lots, scaled linearly to 10/20/30% of the stack's PRE weekly SD (the stack's weights are applied the same way); s113 size surcharge applied post hoc above 14 lots; entry blocks as live (09:00-09:59, 15:00-16:54, 18:00-18:04) except where the cell has its own window.
- VWAP / 1-sigma band: volume-weighted typical price, anchored 18:00 ET (Globex) and re-anchored 09:30 (RTH); band as of the last completed bar, usable after 30 bars. D1 order live 60 min after the trigger, opposite side to the stopped trades, fade at that side's band. D2 windows lunch 11:30-14:30 (55/55, RTH VWAP) and 22:00-02:00 (15/15, Globex VWAP), from the stack's PRE-only slot P&L and the window's median 30-min range on PRE days (53.25 -> 55; 17.0 -> 15); fade = limit at the band, break = stop-entry at the prior-20-bar high/low. D3 base rows = ST/HM (firmlib) and KB 60/60 rows, TH_LIVE cut by ap_th_port.th_scan (as DS3_THL), re-entry on a 1-tick break of the pre-cut extreme within 30 min while the last completed 5-min Supertrend(10,3) agrees; stop-type entry, 60/60, flat 16:55. D4 flag = A's fh_rev construction at 10:30 (m = 1.0, 0.5), limit at the developing RTH VWAP on the reversal side, flat 15:55.
- Placebos (PRE weekly mean of the 10-lot book through the same lock engine, 200 draws each): P1 random-trigger (same side and hour slot, random other day, entry at the second close with NO slip = flatters the placebo), P2 random-direction (same entries, side flipped w.p. 0.5, exit re-simulated). Rank = share of draws below the cell; gate 0.90. Informational mirror (all sides flipped) in the PRE text.

## 3. Verdict table (per cell; tiers by the prereg gates g1-g8, failed gates listed)
| cell | tier | failed gates | PRE trades | pts/tr PRE (CI) | book10 $/wk PRE | HOLD | X | MDE PRE | P1 / P2 rank |
|---|---|---|---|---|---|---|---|---|---|
| D1_C60 | DEAD | g1 PRE add CI>0; g2 HOLD add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g7 2x-cost PRE>0; g8 best-of-F | 342 | -1.73 [-8.0,4.1] | -1,811 [-7,220,3,421] | -6,559 (n 133) | 1,660 (n 110) | 7,656 | 0.36 / 0.34 |
| D1_C40 | DEAD | g1 PRE add CI>0; g2 HOLD add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g7 2x-cost PRE>0; g8 best-of-F | 358 | -2.50 [-6.8,1.6] | -2,734 [-6,600,954] | -8,070 (n 139) | 927 (n 124) | 5,313 | 0.12 / 0.18 |
| D1_K60 | DEAD | g1 PRE add CI>0; g2 HOLD add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g7 2x-cost PRE>0; g8 best-of-F | 180 | -0.02 [-8.5,9.0] | -127 [-3,986,3,941] | -1,575 (n 80) | 1,442 (n 73) | 5,633 | 0.52 / 0.56 |
| D1_K40 | DEAD | g1 PRE add CI>0; g2 HOLD add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g7 2x-cost PRE>0; g8 best-of-F | 185 | -0.78 [-6.7,5.1] | -489 [-2,939,2,060] | -736 (n 82) | 541 (n 76) | 3,710 | 0.47 / 0.47 |
| D2_LF | DEAD | g1 PRE add CI>0; g2 HOLD add>0; g3 X add>0; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g8 best-of-F | 575 | 2.43 [-1.9,6.6] | 3,589 [-3,526,11,502] | -5,597 (n 220) | -2,174 (n 271) | 10,379 | 0.95 / 0.91 |
| D2_LB | DEAD | g1 PRE add CI>0; g2 HOLD add>0; g3 X add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g7 2x-cost PRE>0; g8 best-of-F | 947 | 1.30 [-2.1,4.7] | 2,756 [-6,414,11,203] | -10,095 (n 412) | -2,918 (n 401) | 12,547 | 0.88 / 0.83 |
| D2_NF | DEAD | g1 PRE add CI>0; g2 HOLD add>0; g3 X add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g7 2x-cost PRE>0; g8 best-of-F | 678 | -1.00 [-2.1,0.1] | -2,361 [-4,126,-563] | -2,783 (n 333) | -195 (n 303) | 2,575 | 0.05 / 0.13 |
| D2_NB | DEAD | g1 PRE add CI>0; g2 HOLD add>0; g3 X add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g7 2x-cost PRE>0; g8 best-of-F | 1266 | -0.62 [-1.4,0.2] | -3,135 [-5,820,-234] | -7,070 (n 558) | -4,249 (n 447) | 4,026 | 0.06 / 0.21 |
| D3_ST | DEAD | g1 PRE add CI>0; g3 X add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g7 2x-cost PRE>0; g8 best-of-F | 392 | 0.48 [-5.0,5.8] | 547 [-5,098,5,677] | 1,838 (n 179) | -2,863 (n 108) | 8,108 | 0.66 / 0.68 |
| D3_HM | DEAD | g1 PRE add CI>0; g3 X add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g8 best-of-F | 282 | 2.52 [-4.3,9.2] | 1,959 [-3,583,7,279] | 436 (n 144) | -2,656 (n 93) | 7,841 | 0.86 / 0.84 |
| D3_KB | DEAD | g1 PRE add CI>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g7 2x-cost PRE>0; g8 best-of-F | 433 | -0.00 [-6.1,5.7] | -358 [-6,283,6,121] | 13,065 (n 193) | 948 (n 107) | 9,594 | 0.55 / 0.56 |
| D3_ALL | DEAD | g1 PRE add CI>0; g3 X add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g8 best-of-F | 719 | 2.66 [-2.1,7.0] | 5,124 [-2,560,13,405] | 12,314 (n 336) | -3,543 (n 210) | 12,055 | 0.94 / 0.90 |
| D4_R60 | DEAD (UNDERPOWERED n<60) | g1 PRE add CI>0; g2 HOLD add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g8 best-of-F | 24 | 4.40 [-18.6,26.6] | 269 [-1,090,1,726] | -1,074 (n 10) | 1,120 (n 7) | 2,088 | 0.64 / 0.59 |
| D4_R40 | DEAD (UNDERPOWERED n<60) | g1 PRE add CI>0; g2 HOLD add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g7 2x-cost PRE>0; g8 best-of-F | 24 | -3.60 [-20.4,13.2] | -249 [-1,235,838] | -1,070 (n 10) | 533 (n 7) | 1,503 | 0.28 / 0.26 |
| D4_RNT | DEAD (UNDERPOWERED n<60) | g1 PRE add CI>0; g2 HOLD add>0; g4 P1,P2 rank>=0.90; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g7 2x-cost PRE>0; g8 best-of-F | 24 | 7.83 [-32.1,60.9] | -957 [-2,498,709] | -685 (n 10) | 1,950 (n 7) | 2,235 | 0.14 / 0.17 |
| D4_RLO | DEAD | g1 PRE add CI>0; g2 HOLD add>0; g5 dSharpe>0 PRE&HOLD, dMaxDD<=0 WF; g6 worst-20(ALL) add>=0; g8 best-of-F | 60 | 12.11 [-2.7,24.6] | 1,924 [73,3,953] | -754 (n 38) | 1,140 (n 35) | 2,779 | 0.95 / 0.95 |

Gates: g1 PRE add (20% risk) 95% CI lower bound > 0; g2 HOLD add > 0; g3 X add > 0; g4 P1 and P2 rank >= 0.90; g5 d_Sharpe > 0 in PRE and HOLD and d_maxDD <= 0 over the joined PRE+HOLD; g6 add $ in the stack's 20 worst weeks (ALL) >= 0; g7 2x-cost PRE add > 0; g8 cell PRE book mean >= the 95th percentile of the best-of-16 null. MDE column = 2.8 x SD(weekly book)/sqrt(74): every PRE mean is below its MDE in absolute value; only D2_NF and D2_NB (downside) and D4_RLO (upside, book CI [73, 3,953]) have a 95% CI that excludes 0. D4 cells with 24 trades are UNDERPOWERED by construction (m = 1.0 days: PRE 33 flagged days, 24 filled).

## 4. Stack-add at 10 / 20 / 30% risk (paired by week vs the baseline stack; add scaled to p% of the stack PRE weekly SD)
| cell | risk | lots | PRE add $/wk [CI] | d_Sharpe PRE | d_maxDD PRE | HOLD add | d_Sharpe HOLD | X add | d_Sharpe X | WF d_maxDD | worst-20 wks (ALL) $ add | worst-20 PRE $ add | corr to stack | 2x-cost PRE | MDE PRE |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D1_C60 | 10% | 5.7 | -1,027 [-3,903,1,956] | -0.031 | 11,032 | -3,722 | -0.095 | 942 | +0.065 | -11,583 | 63,915 | 44,861 | -0.22 | -1,276 | 4,344 |
| D1_C60 | 20% | 11.3 | -2,055 [-7,805,3,913] | -0.089 | 22,064 | -7,444 | -0.219 | 1,883 | +0.120 | -23,167 | 127,831 | 89,723 | -0.22 | -2,553 | 8,688 |
| D1_C60 | 30% | 17.0 | -3,338 [-11,943,5,626] | -0.185 | 36,153 | -11,402 | -0.385 | 2,687 | +0.155 | -34,253 | 186,776 | 128,951 | -0.22 | -4,084 | 13,035 |
| D1_C40 | 10% | 8.2 | -2,235 [-5,148,923] | -0.113 | 51,132 | -6,598 | -0.301 | 758 | +0.052 | -14,974 | -21,047 | -33,178 | -0.10 | -2,626 | 4,344 |
| D1_C40 | 20% | 16.4 | -4,670 [-10,485,1,653] | -0.262 | 103,792 | -13,381 | -0.631 | 1,400 | +0.087 | -19,523 | -46,140 | -70,731 | -0.10 | -5,451 | 8,691 |
| D1_C40 | 30% | 24.5 | -7,987 [-16,710,1,528] | -0.478 | 163,191 | -20,981 | -1.011 | 1,528 | +0.079 | 39,877 | -89,083 | -127,592 | -0.10 | -9,158 | 13,052 |
| D1_K60 | 10% | 7.7 | -98 [-2,997,2,857] | -0.009 | 3,991 | -1,215 | +0.006 | 1,112 | +0.066 | -27,501 | 38,478 | 58,790 | -0.11 | -282 | 4,344 |
| D1_K60 | 20% | 15.4 | -254 [-6,054,5,661] | -0.047 | 8,359 | -2,490 | -0.017 | 2,186 | +0.117 | -54,884 | 75,611 | 116,425 | -0.11 | -621 | 8,691 |
| D1_K60 | 30% | 23.1 | -829 [-9,553,8,053] | -0.129 | 35,126 | -4,211 | -0.091 | 2,973 | +0.138 | -32,033 | 102,905 | 165,601 | -0.11 | -1,380 | 13,057 |
| D1_K40 | 10% | 11.7 | -572 [-3,470,2,310] | -0.010 | 39,137 | -862 | -0.044 | 634 | +0.026 | -18,161 | -5,102 | 37,972 | -0.07 | -859 | 4,344 |
| D1_K40 | 20% | 23.4 | -1,716 [-7,505,4,014] | -0.078 | 82,160 | -2,329 | -0.139 | 873 | +0.016 | -34,950 | -23,464 | 64,742 | -0.07 | -2,289 | 8,710 |
| D1_K40 | 30% | 35.1 | -3,389 [-12,065,5,213] | -0.198 | 128,783 | -4,355 | -0.277 | 746 | -0.027 | 5,468 | -54,107 | 81,137 | -0.06 | -4,248 | 13,099 |
| D2_LF | 10% | 4.2 | 1,502 [-1,353,4,399] | +0.110 | -41,538 | -2,343 | -0.140 | -910 | -0.069 | 2,667 | 18,368 | 83,048 | -0.04 | 1,068 | 4,344 |
| D2_LF | 20% | 8.4 | 3,004 [-2,707,8,797] | +0.195 | -47,422 | -4,685 | -0.291 | -1,820 | -0.142 | 5,334 | 36,735 | 166,097 | -0.04 | 2,137 | 8,688 |
| D2_LF | 30% | 12.6 | 4,506 [-4,060,13,196] | +0.250 | -27,008 | -7,028 | -0.448 | -2,730 | -0.219 | 8,000 | 55,103 | 249,145 | -0.04 | 3,205 | 13,032 |
| D2_LB | 10% | 3.5 | 954 [-2,245,4,128] | -0.039 | -2,305 | -3,495 | -0.191 | -1,010 | -0.091 | 28,012 | -109,167 | -102,376 | +0.25 | -274 | 4,344 |
| D2_LB | 20% | 6.9 | 1,909 [-4,491,8,255] | -0.095 | -4,610 | -6,990 | -0.385 | -2,021 | -0.186 | 56,025 | -218,334 | -204,752 | +0.25 | -547 | 8,688 |
| D2_LB | 30% | 10.4 | 2,863 [-6,736,12,383] | -0.162 | 15,555 | -10,485 | -0.581 | -3,031 | -0.281 | 84,037 | -327,502 | -307,128 | +0.25 | -821 | 13,032 |
| D2_NF | 10% | 16.9 | -4,460 [-7,376,-1,290] | -0.221 | 13,340 | -5,253 | -0.251 | -686 | -0.020 | -16,384 | 23,780 | -29,076 | -0.14 | -5,983 | 4,329 |
| D2_NF | 20% | 33.7 | -13,552 [-19,293,-7,399] | -0.714 | 128,352 | -15,938 | -0.769 | -4,855 | -0.282 | 5,037 | -39,911 | -146,129 | -0.15 | -16,599 | 8,536 |
| D2_NF | 30% | 50.6 | -24,969 [-33,702,-15,910] | -1.346 | 373,305 | -29,348 | -1.411 | -10,770 | -0.671 | 249,990 | -147,491 | -307,325 | -0.16 | -29,540 | 12,721 |
| D2_NB | 10% | 10.8 | -3,383 [-6,386,-252] | -0.240 | -22,642 | -7,628 | -0.351 | -4,584 | -0.315 | 9,902 | -145,315 | -101,907 | +0.13 | -8,184 | 4,344 |
| D2_NB | 20% | 21.6 | -9,740 [-15,765,-3,444] | -0.638 | 97,256 | -18,385 | -0.867 | -10,934 | -0.724 | 27,798 | -342,598 | -258,909 | +0.13 | -19,375 | 8,657 |
| D2_NB | 30% | 32.4 | -19,620 [-28,569,-10,300] | -1.196 | 317,425 | -32,849 | -1.562 | -19,376 | -1.233 | 194,110 | -601,456 | -481,195 | +0.12 | -34,128 | 12,959 |
| D3_ST | 10% | 5.4 | 293 [-2,627,3,056] | -0.056 | -12,053 | 985 | -0.034 | -1,534 | -0.102 | 13,544 | -25,948 | -37,098 | +0.22 | -471 | 4,344 |
| D3_ST | 20% | 10.7 | 586 [-5,254,6,113] | -0.129 | 3,766 | 1,970 | -0.083 | -3,068 | -0.211 | 27,089 | -51,897 | -74,197 | +0.22 | -943 | 8,688 |
| D3_ST | 30% | 16.1 | 690 [-8,049,8,981] | -0.222 | 41,340 | 2,748 | -0.150 | -4,690 | -0.328 | 41,062 | -80,456 | -114,764 | +0.22 | -1,604 | 13,020 |
| D3_HM | 10% | 5.5 | 1,085 [-1,827,4,101] | +0.014 | 15,985 | 242 | +0.015 | -1,471 | -0.089 | 466 | -15,732 | -24,977 | +0.05 | 579 | 4,344 |
| D3_HM | 20% | 11.1 | 2,170 [-3,654,8,202] | +0.004 | 31,970 | 484 | +0.018 | -2,943 | -0.184 | 933 | -31,465 | -49,954 | +0.05 | 1,159 | 8,688 |
| D3_HM | 30% | 16.6 | 3,077 [-5,667,12,145] | -0.035 | 49,310 | 508 | +0.001 | -4,513 | -0.291 | 1,633 | -50,188 | -78,296 | +0.05 | 1,560 | 13,029 |
| D3_KB | 10% | 4.5 | -162 [-3,127,2,836] | -0.077 | -10,257 | 5,915 | +0.187 | 429 | +0.014 | 267 | -104,309 | -13,942 | +0.25 | -808 | 4,344 |
| D3_KB | 20% | 9.1 | -324 [-6,254,5,672] | -0.170 | -15,681 | 11,831 | +0.344 | 859 | +0.024 | 535 | -208,619 | -27,885 | +0.25 | -1,616 | 8,688 |
| D3_KB | 30% | 13.6 | -487 [-9,382,8,509] | -0.274 | 40,778 | 17,746 | +0.474 | 1,288 | +0.032 | 802 | -312,928 | -41,827 | +0.25 | -2,424 | 13,032 |
| D3_ALL | 10% | 3.6 | 1,847 [-1,054,4,935] | +0.008 | 18,631 | 4,437 | +0.143 | -1,277 | -0.095 | 9,484 | -86,676 | 337 | +0.28 | 1,044 | 4,344 |
| D3_ALL | 20% | 7.2 | 3,693 [-2,109,9,870] | -0.004 | 37,262 | 8,875 | +0.261 | -2,554 | -0.191 | 18,969 | -173,352 | 674 | +0.28 | 2,088 | 8,688 |
| D3_ALL | 30% | 10.8 | 5,540 [-3,163,14,804] | -0.032 | 106,866 | 13,312 | +0.357 | -3,831 | -0.287 | 28,453 | -260,029 | 1,011 | +0.28 | 3,131 | 13,032 |
| D4_R60 | 10% | 20.8 | 511 [-2,419,3,556] | +0.007 | 1,427 | -2,283 | -0.193 | 2,305 | +0.115 | 50,853 | -76,992 | -1,427 | +0.15 | 448 | 4,344 |
| D4_R60 | 20% | 41.6 | 802 [-5,102,6,882] | -0.023 | 5,568 | -4,784 | -0.391 | 4,502 | +0.209 | 103,062 | -157,377 | -5,568 | +0.15 | 675 | 8,692 |
| D4_R60 | 30% | 62.4 | 1,060 [-7,838,10,174] | -0.076 | 65,581 | -7,319 | -0.582 | 6,683 | +0.287 | 155,477 | -238,275 | -10,119 | +0.15 | 870 | 13,040 |
| D4_R40 | 10% | 28.9 | -858 [-3,755,2,079] | -0.082 | -733 | -3,230 | -0.214 | 1,473 | +0.083 | 47,938 | -119,845 | -2,831 | +0.13 | -954 | 4,357 |
| D4_R40 | 20% | 57.8 | -2,017 [-7,900,3,954] | -0.201 | 123,747 | -6,759 | -0.441 | 2,799 | +0.151 | 97,730 | -244,326 | -9,370 | +0.13 | -2,209 | 8,743 |
| D4_R40 | 30% | 86.7 | -3,026 [-11,850,5,931] | -0.326 | 245,910 | -10,138 | -0.655 | 4,199 | +0.216 | 146,595 | -366,489 | -14,055 | +0.13 | -3,314 | 13,114 |
| D4_RNT | 10% | 19.4 | -1,897 [-4,708,1,145] | -0.151 | 47,871 | -1,368 | -0.157 | 3,773 | +0.175 | 47,456 | -118,639 | -94,911 | +0.22 | -1,966 | 4,349 |
| D4_RNT | 20% | 38.9 | -3,994 [-9,688,2,106] | -0.327 | 98,206 | -2,935 | -0.326 | 7,448 | +0.310 | 96,144 | -240,359 | -192,287 | +0.21 | -4,131 | 8,728 |
| D4_RNT | 30% | 58.3 | -6,161 [-14,772,3,006] | -0.514 | 231,664 | -4,572 | -0.493 | 11,088 | +0.411 | 145,266 | -363,165 | -290,532 | +0.21 | -6,367 | 13,118 |
| D4_RLO | 10% | 15.6 | 2,986 [50,5,917] | +0.169 | 16,740 | -1,213 | -0.134 | 1,760 | +0.058 | 20,104 | -81,019 | 73,722 | +0.09 | 2,875 | 4,344 |
| D4_RLO | 20% | 31.3 | 5,602 [-291,11,489] | +0.288 | 38,033 | -2,984 | -0.314 | 3,158 | +0.076 | 43,395 | -172,968 | 139,247 | +0.10 | 5,380 | 8,681 |
| D4_RLO | 30% | 46.9 | 8,025 [-796,16,895] | +0.366 | 61,714 | -5,048 | -0.511 | 4,366 | +0.069 | 68,358 | -270,646 | 200,474 | +0.10 | 7,692 | 13,016 |

Read: the sign of the stack-add is the sign of the book; nothing adds Sharpe in both PRE and HOLD. D1_C60 / D1_K60 and D2_LF have positive worst-20-weeks adds (weekly correlation to the stack -0.22 / -0.11 / -0.04), D4_RLO is the only cell with PRE d_Sharpe > +0.25 (+0.288) and it reverses in HOLD (-0.314).

## 5. Performance on A's loss hours and loss day types (add $ at 20% risk over ALL; by-year are weekly means)
| cell | 2023 | 2024 | 2025 | 2026 (to 02-06) | add $ in A loss slots (n trades) | add $ in PRE weak slots | ex-post range / trend / reversal days | ex-ante FHnarrow / FHwide (entries >=10:30) |
|---|---|---|---|---|---|---|---|---|
| D1_C60 | 2,148 (n39) | 1,678 | -7,470 | -13,759 (n6) | -20,054 (143) | -3,377 | 455,061 / -402,692 / -306,933 | 170,992 / -260,470 |
| D1_C40 | 1,964 (n39) | -1,350 | -11,397 | -18,764 (n6) | -118,991 (151) | -108,453 | 72,983 / -490,994 / -234,893 | -205,290 / -326,884 |
| D1_K60 | 2,012 (n39) | 2,058 | -2,767 | -6,897 (n6) | 94,078 (70) | -57,808 | 355,997 / -364,122 / 70,125 | -7,137 / 126,860 |
| D1_K40 | 2,518 (n39) | 550 | -3,867 | -14,405 (n6) | 41,762 (71) | -93,193 | 115,383 / -294,269 / 84,622 | 4,141 / 61,751 |
| D2_LF | -1,909 (n39) | 2,258 | 124 | -8,739 (n6) | -165,953 (788) | 118,067 | 701,307 / -461,558 / -242,758 | 38,416 / -41,425 |
| D2_LB | -2,729 (n39) | 2,333 | -2,094 | -11,727 (n6) | -239,659 (1367) | -205,795 | -519,302 / 186,714 / 168,216 | -220,906 / 56,533 |
| D2_NF | -5,835 (n39) | -11,155 | -15,358 | -17,378 (n6) | -621,504 (576) | -1,710,537 | -870,424 / -785,195 / -2,956 | -444,520 / -776,317 |
| D2_NB | -12,230 (n39) | -6,211 | -17,445 | -10,787 (n6) | -798,007 (1195) | -1,771,804 | -877,507 / -545,724 / -208,625 | -694,323 / -552,289 |
| D3_ST | -1,254 (n39) | -1,177 | 526 | 8,708 (n6) | -99,499 (182) | -111,865 | -864,257 / 614,295 / 207,779 | -67,352 / -119,156 |
| D3_HM | -1,258 (n39) | -1,705 | 4,219 | -5,918 (n6) | 25,691 (148) | 3,177 | -529,803 / 471,124 / 83,244 | -60,506 / 44,378 |
| D3_KB | 213 (n39) | 1,958 | 2,586 | 22,652 (n6) | 77,277 (211) | -237 | -407,644 / 709,111 / 28,432 | 115,526 / 185,014 |
| D3_ALL | -1,436 (n39) | -956 | 9,333 | 9,407 (n6) | 88,557 (329) | -5,129 | -618,687 / 839,777 / 173,104 | 41,838 / 338,813 |
| D4_R60 | 5,079 (n39) | -1,617 | -40 | -464 (n6) | 149,735 (12) | 709 | -256,947 / 469,171 / -103,062 | 0 / 109,162 |
| D4_R40 | 3,158 (n39) | -1,751 | -5,059 | -781 (n6) | -28,109 (12) | 113,801 | -316,615 / 178,737 / -97,730 | 0 / -235,608 |
| D4_RNT | 8,403 (n39) | -7,722 | 972 | -5,916 (n6) | -83,713 (12) | -143,329 | -652,714 / 690,056 / -96,144 | 0 / -58,802 |
| D4_RLO | 3,647 (n39) | 4,554 | 941 | 5,501 (n6) | 170,002 (32) | 69,639 | -314,376 / 1,044,788 / -269,421 | -274,871 / 735,862 |

- A loss slots = A's published 12 (03:30, 05:00, 05:30, 07:00, 08:00, 11:30, 12:00, 13:00, 14:30, 16:30, 22:00, 23:30 ET; mined on A's full window, descriptive only here); PRE weak slots = the 16 slots net negative in the stack's own table up to 2025-06-30 (00:00-01:30, 03:30, 05:00, 05:30, 08:00, 11:30, 12:30, 14:30, 16:30, 22:00-23:30). In A's loss slots D1_K60 (+$94k), D1_K40 (+$42k), D3_HM (+$26k), D3_KB (+$77k), D3_ALL (+$89k), D4_R60 (+$150k, 12 trades) and D4_RLO (+$170k, 32 trades) are positive; the others lose there (D2_NB -$798k, D2_NF -$622k, D2_LB -$240k, D2_LF -$166k). None of these positives survives the full gate set.
- LOOK-AHEAD FLAG: the range / trend / reversal day columns use A's ex-post day type (needs the 16:00 close); they describe, they are not a tradable filter. The ex-ante proxies (first-hour range vs prior-20-day median, known 10:30) are valid only for entries at or after 10:30 and are shown in the last column: D1_C60 +$171k on FHnarrow days and -$260k on FHwide days (the same direction as the ex-post split: the counter-trend book earns where the first hour was narrow). That one is a hypothesis for a new prereg (gate D1 by a narrow first hour), NOT a result: it was seen after the PRE/HOLD/X look and is not scored here.
- D1 fills: 33% overnight (before 09:30 or after 18:00, where no ex-ante first-hour label exists), 46% in RTH 10:30-15:00 (where the narrow-first-hour split is valid), the rest 09:30-10:30 / other.

## 6. 50-lot cap conflicts and the cost of the cap (stack gross lots from A's table + book lots at 20%; DS3_CONFIRM_C rule floor(50 - peak stack gross over the hold), P&L scaled linearly, lock NOT re-run = approximation)
| cell | lots @20% | stack gross + book lots > 50 | book cut to 0 | partial | median stack gross over hold | PRE uncapped -> capped $/wk | HOLD uncapped -> capped | X uncapped -> capped |
|---|---|---|---|---|---|---|---|---|
| D1_C60 | 11.3 | 8.4% | 0.2% | 9.7% | 20.1 | -2,055 -> -1,705 | -7,444 -> -7,202 | 1,883 -> 2,445 |
| D1_C40 | 16.4 | 14.3% | 0.0% | 15.5% | 17.0 | -4,670 -> -4,901 | -13,381 -> -12,352 | 1,400 -> 1,485 |
| D1_K60 | 15.4 | 13.5% | 0.0% | 14.7% | 20.8 | -254 -> -362 | -2,490 -> -2,729 | 2,186 -> 2,205 |
| D1_K40 | 23.4 | 29.2% | 0.0% | 31.5% | 17.0 | -1,716 -> -2,031 | -2,329 -> -1,815 | 873 -> 1,288 |
| D2_LF | 8.4 | 5.0% | 0.4% | 4.8% | 17.0 | 3,004 -> 3,319 | -4,685 -> -4,603 | -1,820 -> -1,296 |
| D2_LB | 6.9 | 3.1% | 0.2% | 2.8% | 16.3 | 1,909 -> 2,041 | -6,990 -> -7,061 | -2,021 -> -2,378 |
| D2_NF | 33.7 | 92.0% | 1.3% | 90.7% | 38.0 | -13,552 -> -3,967 | -15,938 -> -4,413 | -4,855 -> -6 |
| D2_NB | 21.6 | 83.7% | 1.3% | 82.7% | 37.1 | -9,740 -> -6,206 | -18,385 -> -14,194 | -10,934 -> -4,720 |
| D3_ST | 10.7 | 7.5% | 0.0% | 8.8% | 19.3 | 586 -> 783 | 1,970 -> 1,510 | -3,068 -> -2,825 |
| D3_HM | 11.1 | 12.7% | 0.2% | 15.8% | 24.3 | 2,170 -> 2,106 | 484 -> 372 | -2,943 -> -3,238 |
| D3_KB | 9.1 | 5.9% | 0.0% | 6.7% | 20.0 | -324 -> -270 | 11,831 -> 11,455 | 859 -> 997 |
| D3_ALL | 7.2 | 5.6% | 0.1% | 6.3% | 22.0 | 3,693 -> 3,671 | 8,875 -> 8,731 | -2,554 -> -2,551 |
| D4_R60 | 41.6 | 68.3% | 0.0% | 68.3% | 16.8 | 802 -> 1,588 | -4,784 -> -5,650 | 4,502 -> 1,885 |
| D4_R40 | 57.8 | 100.0% | 0.0% | 100.0% | 12.8 | -2,017 -> -1,886 | -6,759 -> -4,742 | 2,799 -> 429 |
| D4_RNT | 38.9 | 63.4% | 0.0% | 63.4% | 17.0 | -3,994 -> -2,608 | -2,935 -> -5,579 | 7,448 -> 3,327 |
| D4_RLO | 31.3 | 45.9% | 0.0% | 46.6% | 17.0 | 5,602 -> 4,942 | -2,984 -> -3,538 | 3,158 -> 997 |

Reading: the D1/D3 books (7-16 lots) conflict with the 50-lot cap in 6-15% of trades (D1_K40, 23 lots, 29%) and the cap costs them little; D2_NF / D2_NB / D4 books need 22-58 lots at 20% risk because their weekly SD is tiny (15-pt or 24-trade books), so the cap cuts 46-100% of their trades; the cap does not turn any losing cell positive (cells that look better capped are losing books).

## 7. D3 re-entry vs the no-re-entry baseline (cite DS3_TH_LOSS)
TH_LIVE alone is negative on every book it was scored on (DS3_TH_LOSS: KB -0.91 pts/trade WF, sequence KB WF $16,202 -> $6,182 per week at 10 lots, G3 control ST -0.97 / HM -1.28 pts/trade, all DEAD); this cell asks whether the cut-then-recover subset is a continuation signal that earns the cost back. Answer: PRE re-entry book at 10 lots = ST +$547, HM +$1,959, KB -$358, pooled +$5,124/wk with MDE $8-12k (CIs include 0), HOLD ST +$1.8k / HM +$0.4k / KB +$13.1k / pooled +$12.3k, X ST -$2.9k / HM -$2.7k / pooled -$3.5k. The pooled book beats P1/P2 at rank 0.94/0.90 in PRE, but its sign flips in X, it loses $173k in the stack's 20 worst weeks at 20% risk, and its gain (about +$3.7k/wk at 20% risk) is far below the TH_LIVE sequence cost it would have to repair (KB alone -$10.0k/wk at 10 lots). Re-entry does not rescue TH-loss; it does not matter for the live TH rule.

## 8. Disclosures
1. Stop-outs in the triggers are defined from A's table as gross points per contract <= -40 (stop 60 / WT 45); the exact-engine stack has NO TH exit, so TH cuts are in D3 only. A 2-KB-stop cluster occurs 26 times in 3.6 years, so 'keyed to the KB stop only' was read as 'every KB stop-out' (D1_K cells), stated in the prereg.
2. The counter-trend side is the opposite of the stopped trades entered as a FADE at that side's VWAP band; the alternative reading (join the move through the opposite band) is the informational mirror, also negative in PRE (-$297 / +$972 for 60/60 / 40/40 at 10 lots, inside noise).
3. D2 night window 22:00-02:00 was chosen from the stack's PRE-only slot table (A's published full-window list has different negatives at 00:00-01:30). A's tables were mined on a window that includes dates after 2025-06-30 and past 2026-02-06 (A's FLAG); this study cuts the A trade table at 2026-02-06 and uses A's published slot list only to report the 'A loss slots' split.
4. Bug / fix log: (a) importing the harness (firmlib / te_core) clears sys.argv, scripts now capture ARGV first; (b) the first PRE table printed pts/trade CIs from a mean-of-day-means estimator that did not match the trade-weighted mean; replaced by a day-cluster ratio bootstrap BEFORE the PRE text was hashed; (c) the VWAP-band limit prices were first left off the tick grid (E = 16584.60); fixed by rounding buy limits down and sell limits up to the tick BEFORE any aggregate P&L was read (cells rebuilt). (d) the lock engine's book_from_legs of o2_eng keys days by calendar date (right for RTH-only O2 cells) - not used; the books here are keyed by label day (ET+6h), with weeks from EN.WK.
5. The trade tables were generated for all dates <= 2026-02-06 in one pass, but only PRE aggregates were read before the logged look. The TH cut scan skips rows after 2026-02-06 (UNTOUCHED never scanned).
6. P1 enters at the second close without slippage (favours the placebo); P2 flips the side at the same entry price (a stop-type vs limit mismatch is ignored). g8 uses the 95th percentile of the max-over-cells P1 distribution (cells' draws independent). Lock engine at 10 lots then linear scaling; the stack-add cap analysis does not re-run the lock.
7. D4: m = 1.5 has 8 PRE days and was dropped before scoring (replaced by m = 0.5); the 1.0x cells have 24 PRE / 10 HOLD / 7 X trades: UNDERPOWERED, MDE far above any mean.
8. Scaling to 20% risk implies absurd lot counts for tiny books (D4 31-58 lots, D2_NF 34); the numbers are the prereg'd arithmetic, not a recommendation.

## 9. Request for a direct L2 replay
None warranted: no cell is a LEAD or CONFIRMED. If the user wants to chase the only structural idea that survived the reading (D1_C60 gated by an ex-ante narrow first hour, entries >= 10:30), it needs a new prereg first (<= 6 cells, WFPRE only) before any replay; D4_RLO (m = 0.5, 60 PRE / 133 total fills) would need a queue-position replay of its 133 VWAP limit fills (5/10 lots) only if its HOLD sign were to be re-tested on new weeks.

## 10. Hand-back line
Verdicts: D1 DEAD, D2 DEAD, D3 DEAD, D4 DEAD (16/16); CONFIRMED = none; worst-20-weeks $ at 20% risk: CONFIRMED $0, best cell regardless of verdict +$127,831 (D1_C60, loses overall); F = 16.
