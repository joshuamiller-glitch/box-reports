# DS3_L2_UF_LOSS_C3 - L2-UNTIL-FOUND cycle 3, LOSS side: scale-out of a loser (cut 50% at a path trigger, manage the remainder) (agent UF-LOSS, 2026-10-30)
Research only. UNTOUCHED (> 2026-02-06) never read. Own masks: 2026=20260101..0206 (~5 real weeks), L6M=20250801..0206, HOLD=20250701..0206, PRE=20240201..20250630, X'=20230401..20240131. Prereg `l2vast/ds3/prereg/UF_LOSS_C3_prereg.md` sha256 a75b3dedcaaf06a87346f026e2a6f90951cdfff2e0451ee3714425aaa3793fa8; dead_lookup over all 402 specs before the prereg: 0 EXACT / 0 NEAR / 0 PARTIAL hits (the catalogue holds cut-half only on L2SL path+L2 conditions, never on the L6 path trigger or a remainder policy).
**DEFECT AND AMENDMENT A1 (read first).** The first run gated by `vol_tag_entry_day` = `vol_tag_today`, which is known only at 09:30 ET of the label day: LOOK-AHEAD for asia/london/pre entries. I found it after the first recent look. The first selection (sha256 35c4bbd18abab8808a16e250d9adc3e119675e208e53bd00ade272b9dcf27ab5, files `*_v0` kept) and its recent look are VOID for every regime-gated cell. Corrected gate (vol_tag_prev for sess <= 2, vol_tag_today for nyam/nypm, as EXP1 did) was logged in DECISIONS.md BEFORE re-running; cells otherwise unchanged; re-selection on PRE+X' only (sha256 6ef4e14a3e9da11f1f66ebbb98b122d4988a26ca591049ad860d9eabceb9bbdc), then a SECOND recent look. So **cycle 3 has two recent looks (the first void for reg-gated cells; session-gated SM cell identical in both)**. Void v0 recent numbers for reference: pooled reg2/TR20 L6M N +0.08, WT reg2/FULL L6M +0.36; the corrected values below are the ones that count.
Gate basis: **N + selectivity** (fire < 50% of arm-reaching trades). LIVE-CAL (stop-class 2.45 incl. tightened/trailing stops, market M, target correction 0) and M beside; credit share = (LC-N)/LC. Numbers pts/trade vs hold-to-stop, `mean [n fired] (MDE)`, MDE = 2.8 SE, day x ENTRY-session clusters. Trigger L6(A,W) = the registered HM path rule family evaluated on every book's 1-s path (HM a30_w10 = L6(30,10) on HM, unaltered). Cells 402 (396 + 6 entry-avoid controls); cumulative N = 144,586 + 402 = 144,988; n_effective 8.8.

## 1. Settings table (recent first; corrected regime gate; second look)
Selected on PRE+X' (max PRE N, X' N >= 0, fire < 50%, n fired PRE >= 100 / 60 per book). `R0 / FULL` = the same trigger+gate with cut-half-original-stop and with 100% cut (comparators, N L6M). Rank = share of 20 random cut-half draws (same per-day count of arm-reaching trades, decision at the arm second, same remainder policy) that the real cell beats.
| group | cell | fire % (L6M) | 2026 N | L6M N | HOLD N | PRE N | X' N | L6M M / LC (credit share) | R0 / FULL N L6M | rank random cut-half (L6M/HOLD) | unconditional same-policy L6M N | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | loss|trig=L6a20w10|gate=reg2|rem=TR20 | 17 | -0.21 [236] (1.17) | +0.05 [1162] (0.65) | +0.07 [1187] (0.59) | +0.24 [2731] (0.40) | +0.12 [411] (0.37) | +0.15 / +0.13 (63%) | +0.05 / +0.09 | 1.00/1.00 | -2.44 | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X', 2026 <0 or placebo<0.9) |
| ST | loss|trig=L6a20w10|gate=reg2|rem=FULL | 17 | -0.16 [30] (2.71) | +0.00 [156] (1.43) | +0.04 [158] (1.30) | +0.50 [392] (0.95) | +0.01 [49] (0.85) | +0.13 / +0.14 (97%) | +0.00 / +0.00 | 0.85/0.80 | -3.30 | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X', 2026 <0 or placebo<0.9) |
| HM | loss|trig=L6a30w30|gate=reg0|rem=TR20 | 19 | -0.07 [8] (1.76) | +0.14 [104] (1.18) | +0.17 [127] (1.17) | +0.47 [326] (0.85) | +0.45 [144] (1.50) | +0.20 / +0.22 (37%) | +0.07 / +0.15 | 0.20/0.10 | -1.39 | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X', 2026 <0 or placebo<0.9) |
| WT | loss|trig=L6a20w10|gate=reg2|rem=FULL | 11 | +0.78 [17] (0.80) | +0.33 [114] (0.47) | +0.30 [116] (0.42) | +0.29 [250] (0.31) | +0.13 [49] (0.35) | +0.37 / +0.41 (20%) | +0.16 / +0.33 | 1.00/1.00 | -1.80 | CANDIDATE-RECENT (N>=0 in all 5 windows, selective, placebo>=0.9; cumulative RC fails) |
| KB | loss|trig=L6a30w30|gate=reg2|rem=TI10 | 39 | -0.23 [65] (2.59) | +0.32 [318] (1.32) | +0.35 [329] (1.22) | +0.23 [678] (0.78) | +0.35 [229] (1.38) | +0.44 / +0.51 (39%) | +0.18 / +0.37 | 0.60/0.50 | -1.03 | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X', 2026 <0 or placebo<0.9) |
| SM | loss|trig=L6a20w10|gate=sess3|rem=RC10 | 12 | +1.21 [3] (2.06) | +0.99 [28] (1.93) | +0.76 [30] (1.70) | +0.59 [70] (0.91) | +0.26 [11] (0.75) | +1.03 / +1.07 (8%) | +0.49 / +0.99 | 0.25/0.25 | -0.67 | CANDIDATE-RECENT-weak (N>=0 L6M/HOLD/PRE/X', 2026 <0 or placebo<0.9) |
| PE | loss|trig=L6a20w10|gate=reg2|rem=TR20 | 18 | -0.56 [31] (2.26) | -0.01 [157] (1.25) | +0.08 [162] (1.15) | +0.40 [384] (0.81) | +0.28 [50] (0.81) | +0.10 / +0.08 (117%) | -0.08 / -0.15 | 0.40/0.45 | -1.58 | BEST-AVAILABLE-NEGATIVE |
**Best this cycle: WT `L6(20,10) | high-vol regime | FULL cut`**: N >= 0 in all five windows (2026 +0.78 [17], L6M +0.33 [114] (MDE 0.47), HOLD +0.30 (0.42), PRE +0.29 (0.31), X' +0.13 (0.35)), fire 11% (selective), M +0.37 / LC +0.41 in L6M (credit 20%), random-cut rank 1.00 in L6M/HOLD/2026/PRE, the unconditional A20 cut is -1.80. Stack WT-only +0.9k/wk L6M (MDE 2.7k), +0.8k HOLD, +0.2k PRE, +0.04k X', +3.1k 2026. Why it is NOT a PASS: single book (WT, 33.75-pt stop, lots 7), selected from 156 eligible WT cells, single-cell L6M t = +1.98 (p1 0.024) -> cumulative-adjusted p = 1.00 (N_cum 144,988; cycle Bonferroni 1.00), L6M effect < MDE, and the regime gate is a day-level volatility tag. CANDIDATE-RECENT, nothing more. It is also not a scale-out result: FULL (+0.33) beats cut-half R0 (+0.16).
Pooled ALL (TR20 remainder, fire 17%): L6M +0.05 (MDE 0.65), HOLD +0.07, PRE +0.24, X' +0.12, 2026 -0.21: N >= 0 in four windows, all inside MDE, FULL is no worse (+0.09); stack on the six stack books -3.8k/wk L6M. Reality check (i) White RC on PRE daily sums over the 402 cells (N): p = 0.45 (best loss|avoid|z10_ge=2.0); restricted to selective n>=100 trigger cells p = 0.64. (ii) cumulative: Bonferroni p = 1.00 for every selected cell.

## 2. Does managing the remainder help? No.
PRE and X' N medians over the 385 selective n>=100 trigger cells, by remainder policy (ALL group; share_both_pos = share of cells with N > 0 in PRE and X'):
| pol   |   cells |   PRE_N_med |   X_N_med |   share_PRE_pos |   share_both_pos |
|:------|--------:|------------:|----------:|----------------:|-----------------:|
| FULL  |      35 |      -0.069 |     0.068 |           0.2   |            0.114 |
| R0    |      35 |      -0.034 |     0.034 |           0.2   |            0.114 |
| RC10  |      35 |      -0.045 |     0.045 |           0.2   |            0.143 |
| RC20  |      35 |      -0.03  |     0.029 |           0.257 |            0.2   |
| TI10  |      35 |      -0.034 |     0.044 |           0.229 |            0.171 |
| TI15  |      35 |      -0.026 |     0.041 |           0.229 |            0.143 |
| TI20  |      35 |      -0.035 |     0.027 |           0.257 |            0.2   |
| TR20  |      35 |      -0.036 |     0.067 |           0.343 |            0.229 |
| TR30  |      35 |      -0.038 |     0.048 |           0.257 |            0.171 |
| TS300 |      35 |      -0.061 |     0.05  |           0.229 |            0.171 |
| TS900 |      35 |      -0.042 |     0.05  |           0.314 |            0.143 |
No remainder policy is better than R0 or FULL by more than 0.04 pt (median), and every policy median is negative in PRE. TR20 (trail 20) has the highest share of positive cells (0.34 PRE, 0.23 both) but not a better cell mean. By gate (selective n>=100 cells):
| gate   |   cells |   fire_med |   PRE_N_med |   X_N_med |
|:-------|--------:|-----------:|------------:|----------:|
| none   |      33 |      0.268 |      -0.068 |     0.11  |
| reg0   |      44 |      0.074 |      -0.099 |     0.129 |
| reg1   |      44 |      0.063 |      -0.09  |    -0.025 |
| reg2   |      44 |      0.148 |       0.07  |     0.013 |
| sess0  |      44 |      0.033 |      -0.047 |     0.1   |
| sess1  |      44 |      0.054 |      -0.023 |     0.083 |
| sess2  |      44 |      0.03  |       0.038 |    -0.003 |
| sess3  |      44 |      0.106 |      -0.041 |    -0.105 |
| sess4  |      44 |      0.06  |      -0.015 |     0.076 |
By trigger:
| trig     |   cells |   fire_med |   PRE_N_med |   X_N_med |
|:---------|--------:|-----------:|------------:|----------:|
| L6a20w10 |      99 |      0.067 |      -0.019 |     0.081 |
| L6a30w10 |      99 |      0.059 |      -0.039 |     0.044 |
| L6a30w30 |      88 |      0.17  |      -0.078 |     0.111 |
| L6a40w10 |      99 |      0.044 |      -0.017 |     0.024 |
Reading: only the high-vol-regime gate (reg2: PRE N median +0.07) and the 'pre' session gate (sess2: +0.04) are positive; every other gate is negative in PRE; X' disagrees (reg2 +0.01, sess2 0.00). The L6 path trigger alone (gate none) is -0.07 PRE / +0.11 X'. The scale-out structure itself adds nothing: R0 (cut-half) is half of FULL by construction and the tightened/trailed/time-stopped remainders land between them.

## 3. Entry-second AVOID control (small, per the coordinator; PRE and X' only, not selected, no recent look)
Skip the trade when the first book row (entry second) shows the state; N = -(trade's hold-to-stop result) on skipped trades; fire = share of ALL trades skipped:
| cell                     |   ALL_fire_PRE |   ALL_PRE_N |   ALL_PRE_LC |   ALL_PRE_mde |   ALL_X_N |
|:-------------------------|---------------:|------------:|-------------:|--------------:|----------:|
| loss|avoid|cumb_le=0.5   |          0.059 |       0.299 |        0.343 |         0.376 |     0.17  |
| loss|avoid|cumb_ge=1.5   |          0.051 |      -0.096 |       -0.064 |         0.291 |     0.148 |
| loss|avoid|imb10_le=-0.3 |          0.013 |       0.051 |        0.06  |         0.134 |    -0.07  |
| loss|avoid|drel_le=0.5   |          0.054 |       0.224 |        0.263 |         0.346 |     0.095 |
| loss|avoid|drel_ge=1.5   |          0.03  |      -0.014 |        0.005 |         0.234 |    -0.127 |
| loss|avoid|z10_ge=2.0    |          0.177 |       0.574 |        0.703 |         0.692 |     0.4   |
The own-side pulled z >= 2 at the entry second skips 17.7% of trades and the skipped trades lose: PRE N +0.57 (MDE 0.69), X' +0.40, LC +0.70. It is the largest PRE/X' number of the cycle (it is also the RC maximiser) but is an ENTRY filter that overlaps L2EA (which found thick-book skip -0.065 L6M and a session-gating filter); no recent look was taken, so it stays an unlooked LEAD for the entry side.

## 4. HM-only report (registered a30_w10 = L6(30,10) on HM, unaltered)
| HM trades, trigger L6(30,10) gate none, remainder | fire % PRE | n fired PRE | PRE N | X' N | PRE LC | PRE M |
|---|---|---|---|---|---|---|
| R0 | 29 | 414 | +0.10 | +0.47 | +0.21 | +0.14 |
| TI10 | 29 | 414 | +0.17 | +0.67 | +0.30 | +0.22 |
| TI15 | 29 | 414 | +0.14 | +0.54 | +0.26 | +0.19 |
| TI20 | 29 | 414 | +0.21 | +0.49 | +0.33 | +0.25 |
| TS300 | 29 | 414 | +0.10 | +0.79 | +0.26 | +0.18 |
| TS900 | 29 | 414 | +0.10 | +0.71 | +0.23 | +0.16 |
| RC10 | 29 | 414 | +0.04 | +0.59 | +0.18 | +0.09 |
| RC20 | 29 | 414 | +0.15 | +0.49 | +0.26 | +0.19 |
| TR20 | 29 | 414 | +0.22 | +0.95 | +0.33 | +0.29 |
| TR30 | 29 | 414 | +0.16 | +0.75 | +0.27 | +0.22 |
| FULL | 29 | 414 | +0.20 | +0.94 | +0.41 | +0.27 |
Registered base (FULL, N): 2026 +0.14, L6M -0.00 (MDE 1.50), HOLD +0.06, PRE +0.20, X' +0.94, fire 25% of arm-reaching HM trades, LIVE-CAL +0.17 L6M = 100% stop-cost credit. Scale-out R0 (cut-half): L6M -0.00, HOLD +0.03, PRE +0.10, X' +0.47. Any remainder policy on the base: PRE +0.04..+0.22, X' +0.49..+0.95, i.e. none beats FULL (PRE +0.20, X' +0.94); TR20 equals FULL (+0.22/+0.95). The HM cell selected on PRE+X' among all HM cells (297 eligible: trigger x gate x policy) is `L6(30,30) | regime 0 | TR20`: N 2026 -0.07, L6M +0.14 (MDE 1.18), HOLD +0.17, PRE +0.47, X' +0.45, fire 19%, random cut-half rank 0.20/0.10: worse than random draws of the same count - BEST-AVAILABLE, not a candidate. Stack: HM base FULL +3.5k/wk L6M (MDE 6.1k), +3.6k HOLD, +0.1k PRE, +1.5k X'; HM base R0 +1.5k L6M.

## 5. Stack (exact 6-book lock engine, M-basis engine; $/wk delta vs base, MDE in brackets) and equal-risk scaling
| stream | 2026 d$/wk (MDE) | L6M | HOLD | PRE | X' | maxDD L6M base->rule |
|---|---|---|---|---|---|---|
| ALL_sel | -5,138 (35,348) | -3,766 (10,448) | -3,266 (9,246) | -3,312 (8,373) | -325 (6,383) | 466,422 -> 485,586 |
| WT_sel | +3,086 (5,885) | +869 (2,653) | +760 (2,321) | +229 (1,372) | +40 (1,713) | 466,422 -> 459,290 |
| COMBO_perbook5 | +3,109 (7,973) | -5,442 (11,963) | -4,623 (10,515) | -2,520 (6,113) | -682 (5,949) | 466,422 -> 509,301 |
| HM_base_FULL | +4,598 (7,549) | +3,485 (6,058) | +3,578 (5,656) | +63 (6,176) | +1,544 (3,430) | 466,422 -> 468,198 |
| HM_base_R0 | +1,731 (6,833) | +1,482 (3,655) | +1,446 (3,322) | +260 (4,042) | +409 (2,685) | 466,422 -> 470,301 |
| COMBO5+HMbase | +7,707 (14,151) | -1,957 (11,272) | -1,045 (9,993) | -2,457 (9,425) | +862 (7,944) | 466,422 -> 505,240 |
EQR first-order (worst-20 weeks matched): ALL_sel c 1.006: L6M -3,382 / HOLD -2,961; WT_sel c 1.0: L6M +853 / HOLD +748 / PRE +219 / X' +35; per-book five c 0.991: L6M -5,991 / HOLD -5,059; HM base FULL c 1.044: L6M +6,494 / HOLD +6,016. The WT effect is real in sign on the stack but 1/3 of its MDE; the pooled and per-book-five picks are negative on the stack.
Sessions (ENTRY, N pts/trade, MDE, n fired) pooled selected cell L6M: asia +0.01 (0.59, 122), london -0.12 (1.46, 192), pre -0.27 (2.71, 66), nyam +0.19 (1.55, 504), nypm +0.18 (1.65, 271); PRE: asia -0.04, london +0.48 (0.88), pre +0.46, nyam +0.42 (0.85), nypm +0.03. WT cell L6M: nyam +0.74 (1.06, 49), pre +1.26 (1.45, 8), nypm +0.42, asia/london ~0 (these ARE the D6 session variants, all inside MDE).

## 6. Learned
1. The remainder policy is irrelevant: tighten / time-stop / recover / trail on the second half moves the N median by <= 0.04 pt; FULL >= R0 in every selected cell except PE (R0 -0.08, FULL -0.15 in L6M). Scale-out is not a source of edge.
2. The only thing that separates cells is the trigger+gate: the L6 path trigger cut only on high-volatility days (reg2) is N-positive in PRE (+0.07 median) and, on WT, in all five windows (best this cycle, CANDIDATE-RECENT, cumulative p 1.00).
3. The regime tag in the data was a look-ahead for pre-09:30 entries (defect found, amended, disclosed); with the causal tag the results are weaker for ALL (L6M +0.05 vs +0.08) and unchanged in direction.
4. Credit share is 8-117% (WT 20%, HM 37%, ALL 63%, ST 97%, PE 117%): WT's N gain is real, not stop-cost credit.
5. The entry-second pull-z avoid control is the strongest PRE/X' number (+0.57/+0.40) and belongs to the entry side.

## 7. Next family
Entry filter from the entry-second book (pulled_sup z at the first row, cum_behind rel) scored per trade on N with the 70/30 split base, walk-forward, recent look once - handed to the ENTRY agent as a LEAD; for LOSS: the high-vol regime gate on the registered path rule (regime x path-trigger) with causal tags only (vol_tag_prev + today's overnight range at 09:30), and its walk-forward stability, since it is the only structure that produced N >= 0 in all windows on one book.

## 8. Needed in D6 (also in DS3_THL2_NEEDS.md)
The L6(A,W) path rule on every book (HM already live) and a causal day-volatility tag: vol_tag_prev (previous label day's range / 20-day median: lo < 0.85, mid, hi > 1.15) for entries before 09:30 ET, today's tag (overnight 18:00-09:30 complete) from 09:30 ET. Remainder policies need nothing new (stop modification exists), but none helped. The avoid control needs pulled_sup10 z-score at the entry second (see cycle 1 definition).
Files: code/uf/uf3_{cells,engine,stageA,stageB,stack,report}.py; out/uf/loss1/{cells3_PRE_X.csv,selection3_PRE.json,stageB3.pkl,stack3.json} (+ *_v0 void first run); DEAD_CELLS.csv +402 (program UFL3).

## 9. Void first-run reference (look-ahead regime gate; do not use)
| group | v0 cell (look-ahead regime gate) | L6M N | HOLD N | 2026 N |
|---|---|---|---|---|
| ALL | loss|trig=L6a20w10|gate=reg2|rem=TR20 | +0.08 | +0.09 | -0.11 |
| ST | loss|trig=L6a20w10|gate=reg2|rem=TR20 | +0.18 | +0.21 | +0.13 |
| HM | loss|trig=L6a30w30|gate=reg0|rem=TS300 | +0.10 | +0.34 | -0.03 |
| WT | loss|trig=L6a20w10|gate=reg2|rem=FULL | +0.36 | +0.33 | +0.77 |
| KB | loss|trig=L6a30w30|gate=sess2|rem=TR30 | +0.00 | +0.08 | -0.28 |
| SM | loss|trig=L6a20w10|gate=sess3|rem=RC10 | +0.99 | +0.76 | +1.21 |
| PE | loss|trig=L6a20w10|gate=reg2|rem=TR20 | -0.17 | -0.15 | -0.51 |
