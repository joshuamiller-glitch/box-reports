# DS3_L2_UF_LOSS_C2 - L2-UNTIL-FOUND cycle 2, LOSS side: recovery-trigger hold-through / cut-wait (agent UF-LOSS, 2026-10-30)
Research only. UNTOUCHED (> 2026-02-06) never read. Own masks: 2026=20260101..0206 (~5 real weeks), L6M=20250801..0206, HOLD=20250701..0206, PRE=20240201..20250630, X'=20230401..20240131. Prereg `l2vast/ds3/prereg/UF_LOSS_C2_prereg.md` sha256 f5edd55fb05d036e055dca1a9579e11e6cfb9933f58463d48daa8b6626244337; selection `out/uf/loss1/selection2_PRE.json` sha256 bde2056756ab9a0908c8119277561ec90620d4b0f43421d536b13be177c7c353 (PRE+X' only, N basis, logged before the single recent look). dead_lookup over all 520 candidate specs before the prereg: 0 EXACT / 0 NEAR hits (catalogue holds loss tape and footprint only as descriptive THL2 maps; CUTWAIT is path-only).
**Gate basis this cycle: N (no target correction, M stop cost) AND selectivity (fire < 50% of arm-reaching trades).** LIVE-CAL (stop 2.45 vs nominal, market M, target corr 0) and M are shown beside; credit share = (LC - N)/LC = share of the LIVE-CAL gain that is the stop-cost credit (shown only when LC > 0). Numbers: pts/trade vs hold-to-stop, `mean [n fired] (MDE)`, MDE = 2.8 SE, day x ENTRY-session clusters. Cell count 522 (520 prereg + the 2 ungated HM-base cells for the HM-only report); cumulative N = 144,064 + 522 = 144,586 (distinct specs 81,198 + 1,002 across the two cycles).

## 1. Settings table (recent first)
Result: no PASS. Selectivity is the first filter: **only 8 of 480 non-HM cells fire on < 50% of arm-reaching trades** (all T4 win=30 veto); the other 472 fire on 88-99% (not selective). Recovery triggers are present on 70-80% of 30-s windows, so a rule that cuts only when none is present still cuts most trades in delay mode, and veto mode barely vetoes. Selected cells (chosen on PRE+X' by max PRE N, X' N >= 0, fire < 50%):
| group | cell | fire % L6M | 2026 N | L6M N | HOLD N | PRE N | X' N | L6M M / LC | credit share of LC (L6M) | shuffled-trigger rank (L6M/HOLD) | random-cut rank | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | loss|a=30|rt=T4|win=30|mode=veto|act=t15 | 48 | +0.00 [649] (1.14) | -0.33 [2735] (0.56) | -0.27 [2989] (0.52) | +0.13 [6852] (0.32) | +0.35 [2321] (0.55) | -0.25 / -0.23 | nan% | 0.70/0.45 | 0.00/0.00 | BEST-AVAILABLE-NEGATIVE |
| ST | loss|a=40|rt=T4|win=30|mode=veto|act=cut | 37 | +0.11 [48] (2.63) | +0.17 [232] (1.34) | +0.10 [254] (1.27) | +0.02 [592] (0.90) | +0.54 [197] (1.47) | +0.27 / +0.40 | 58% | 0.55/0.30 | 1.00/1.00 | CANDIDATE-RECENT (N>=0 all windows, MDE>>effect, placebo<0.9) |
| HM | loss|HM|a30w10|rt=F3|win=10|veto|act=cut | 22 | +0.87 [26] (2.83) | +0.19 [118] (1.40) | +0.22 [130] (1.30) | +0.59 [331] (0.87) | +0.48 [55] (0.85) | +0.27 / +0.34 | 44% | random-veto 0.79/0.79 | - | CANDIDATE-RECENT (N>=0 all windows, MDE>>effect, placebo<0.9) |
| WT | loss|a=30|rt=T4|win=30|mode=veto|act=t15 | 48 | +0.00 [91] (0.00) | +0.00 [374] (0.00) | +0.00 [413] (0.00) | +0.00 [887] (0.00) | +0.00 [336] (0.00) | +0.00 / +0.00 | nan% | 0.00/0.00 | 0.00/0.00 | CANDIDATE-RECENT (N>=0 all windows, MDE>>effect, placebo<0.9) |
| KB | loss|a=40|rt=T4|win=30|mode=veto|act=t15 | 38 | -0.16 [66] (1.14) | -0.09 [254] (0.45) | -0.15 [277] (0.48) | +0.15 [612] (0.17) | +0.14 [206] (0.45) | -0.08 / -0.03 | nan% | 0.90/0.65 | 0.00/0.00 | BEST-AVAILABLE-NEGATIVE |
| SM | loss|a=30|rt=T4|win=30|mode=veto|act=half | 48 | +0.33 [12] (3.34) | +0.10 [90] (2.01) | -0.39 [99] (1.92) | -0.07 [237] (1.18) | +1.17 [113] (1.29) | +0.23 / +0.26 | 61% | 0.60/0.40 | 1.00/0.85 | BEST-AVAILABLE-NEGATIVE |
| PE | loss|a=30|rt=T4|win=30|mode=veto|act=t15 | 51 | +0.59 [106] (2.72) | -0.02 [389] (1.33) | +0.06 [412] (1.22) | +0.14 [923] (0.79) | +0.17 [282] (1.44) | +0.07 / +0.12 | 119% | 1.00/0.90 | 0.05/0.15 | BEST-AVAILABLE-NEGATIVE |
| HMbase | loss|HM|a30w10|ungated|act=cut | 25 | +0.14 [30] (3.23) | -0.00 [135] (1.50) | +0.06 [149] (1.39) | +0.20 [414] (1.04) | +0.94 [81] (0.97) | +0.10 / +0.17 | 102% | - | - | BASE (registered, not new) |
Reading of the tiers: ALL fails N in L6M/HOLD (-0.33 / -0.27; the unconditional A30 cut is -0.45 / -0.31). **ST**: N >= 0 in all windows but +0.02 PRE, +0.10 HOLD (MDE 1.3), shuffled-trigger rank 0.55/0.30 and the unconditional A40 cut (N +0.29 L6M, +0.49 HOLD) is better than the rule: CANDIDATE-RECENT in sign only. **WT** is a null: the t15 tightened stop (A30 + 15 = 45 pts) never executes inside WT's 33.75-pt stop, so it equals hold (all zeros; the selection rule picked it because nothing can be negative). **PE** shows credit share 119% (N slightly negative in L6M). **HM** (see 4) is the interesting row. Placebo beaten (rank >= 0.9) only for the PE and KB shuffled-trigger ranks at L6M, where the rule itself is negative.
Cumulative-adjusted reality check. (i) White RC on PRE daily sums (N basis) over the cycle's 522 cells: p = 0.36 (best loss|HM|a30w10|rt=F3|win=30|veto|act=cut, t 1.85); restricted to the 8 selective n>=100 cells p = 0.42. (ii) cumulative: Bonferroni p with N_cum = 144,586 is 1.00 for every selected cell (best single L6M N t = +0.35, ST). n_effective = 2.0: the cells are near-copies of the path rule (appended to UF_TRIALS.json).

## 2. Family
| mode   |   win |   cells |   fire_median |   selective_cells |   PRE_N_median |   PRE_N_max |
|:-------|------:|--------:|--------------:|------------------:|---------------:|------------:|
| delay  |    10 |     120 |         0.989 |                 0 |         -0.532 |       0.072 |
| delay  |    30 |     120 |         0.983 |                 0 |         -0.501 |       0.162 |
| veto   |    10 |     120 |         0.974 |                 0 |         -0.519 |       0.104 |
| veto   |    30 |     120 |         0.942 |                 8 |         -0.378 |       0.129 |
By trigger (all 480 non-HM cells; medians over cells; PRE):
| rt   |   fire_med |   PRE_N_med |   PRE_N_max |   PRE_LC_med |   PRE_M_med |
|:-----|-----------:|------------:|------------:|-------------:|------------:|
| C1   |      0.993 |      -0.53  |       0.08  |       -0.164 |      -0.346 |
| C2   |      0.993 |      -0.516 |       0.09  |       -0.158 |      -0.335 |
| F1   |      0.976 |      -0.541 |       0.054 |       -0.13  |      -0.333 |
| F2   |      0.948 |      -0.522 |       0.127 |       -0.124 |      -0.334 |
| F3   |      0.878 |      -0.319 |       0.09  |       -0.057 |      -0.169 |
| T1   |      0.986 |      -0.479 |       0.102 |       -0.11  |      -0.287 |
| T2   |      0.989 |      -0.529 |       0.086 |       -0.169 |      -0.342 |
| T3   |      0.98  |      -0.505 |       0.162 |       -0.121 |      -0.323 |
| T4   |      0.938 |      -0.368 |       0.144 |       -0.077 |      -0.23  |
| T5   |      0.972 |      -0.524 |       0.058 |       -0.181 |      -0.35  |
Reading. (a) Prediction confirmed: delay mode fires on 98-99% (a trigger-free row always eventually appears), win=10 veto on 97%; only T4 (delta_acc > 0 and delta10 > 0) over a 30-s window is common enough to veto > 50% of path firings. (b) No trigger improves the path rule in PRE on N (medians -0.32..-0.54 pt, equal to the path rule's own drag; best single cell +0.16). (c) Footprint triggers add nothing beyond tape (F1/F2 median PRE N -0.54/-0.52, F3 -0.32 which is only fewer cuts; C1/C2 conjunctions -0.53/-0.52). (d) LIVE-CAL medians (-0.06..-0.18) are better than N (-0.32..-0.54) by the stop-cost credit (+0.3..+0.4 for cut-heavy cells); M medians (-0.17..-0.35) sit between because M keeps the target correction in the base.

## 3. Controls and sessions (selected pooled cell, N basis, 20 draws)
Shuffled trigger within day: rank L6M 0.70 / HOLD 0.45 (PRE 0.95, X' 0.80); random cut at the same rate: rank 0.00 / 0.00 in L6M/HOLD (the real cell is worse than a random single-row cut at the same rate); unconditional fixed A30 tighten: N -0.45 L6M / -0.31 HOLD. Placebo beaten: NO. Sessions L6M N (MDE, n fired): asia -0.41 (1.10, 675), london -0.58 (1.28, 532), pre +0.83 (1.62, 158), nyam -0.35 (1.12, 938), nypm -0.22 (1.17, 430); PRE: asia +0.13, london +0.00, pre +0.63, nyam +0.31, nypm -0.18. Nothing outside MDE.

## 4. HM-only report (registered a30_w10 UNALTERED, vetoed at its firing second when the trigger is present; HM-book trades re-implemented as in cycle 1)
Base (ungated) a30_w10, N: 2026 +0.14, L6M -0.00 (MDE 1.50), HOLD +0.06, PRE +0.20, X' +0.94; fire 25%; LIVE-CAL +0.17 L6M = 102% stop-cost credit; M +0.10. PRE/X' N of every gate (cut action), fire % of arm-reaching HM trades in PRE:
| HM a30_w10 gate (veto when present) | fire % of arm-reaching PRE | n fired PRE | PRE N | X' N |
|---|---|---|---|---|
| ungated | 30 | 414 | +0.20 | +0.94 |
| rt=T1|win=10|veto | 23 | 320 | +0.28 | +1.03 |
| rt=T1|win=30|veto | 10 | 142 | +0.13 | +0.41 |
| rt=T2|win=10|veto | 28 | 388 | +0.28 | +1.02 |
| rt=T2|win=30|veto | 23 | 328 | +0.44 | +0.80 |
| rt=T3|win=10|veto | 27 | 378 | +0.35 | +0.83 |
| rt=T3|win=30|veto | 20 | 282 | +0.39 | +0.78 |
| rt=T4|win=10|veto | 19 | 270 | -0.06 | +0.94 |
| rt=T4|win=30|veto | 8 | 105 | -0.09 | +0.23 |
| rt=T5|win=10|veto | 28 | 397 | +0.14 | +0.83 |
| rt=T5|win=30|veto | 27 | 383 | +0.20 | +0.82 |
| rt=F1|win=10|veto | 29 | 404 | +0.34 | +0.86 |
| rt=F1|win=30|veto | 28 | 398 | +0.35 | +0.86 |
| rt=F2|win=10|veto | 26 | 370 | +0.28 | +0.81 |
| rt=F2|win=30|veto | 25 | 352 | +0.23 | +0.89 |
| rt=F3|win=10|veto | 24 | 331 | +0.59 | +0.48 |
| rt=F3|win=30|veto | 21 | 298 | +0.57 | +0.46 |
| rt=C1|win=10|veto | 29 | 411 | +0.33 | +0.89 |
| rt=C1|win=30|veto | 29 | 405 | +0.34 | +0.89 |
| rt=C2|win=10|veto | 29 | 410 | +0.17 | +0.91 |
| rt=C2|win=30|veto | 29 | 402 | +0.21 | +0.86 |
Selected on PRE+X' (max PRE N, X' N >= 0): **F3 win=10 veto** (hold when the 1-min footprint bar had delta with the trade AND the extreme was finished, i.e. no both-sided trading at the bar's low/high behind): fire 22%, N 2026 +0.87, L6M +0.19, HOLD +0.22, PRE +0.59, X' +0.48 (MDEs 1.4/1.3/0.87/0.85), M L6M +0.27, LC +0.34 (credit share 44%). Gain over the base: +0.19 L6M, +0.16 HOLD, +0.39 PRE, but -0.46 X'. The veto removes 20% of the base cuts (n fired 118 vs 135 L6M); random veto at the same rate: rank 0.79 / 0.79 (L6M/HOLD), 0.99 PRE, 0.01 in X' (the gate lost in X'). It is the only cell this cycle >= 0 on N in all five windows and selective, but: all deltas inside MDE, placebo rank < 0.9, selected from 21 HM gates x PRE+X', cumulative p = 1.00. Tier CANDIDATE-RECENT (sign only), not PASS; the registered base stays untouched.

## 5. Stack (exact 6-book lock engine, M-basis engine; $/wk delta vs base, MDE in brackets) and equal-risk scaling
| stream | 2026 d$/wk (MDE) | L6M | HOLD | PRE | X' | maxDD L6M base->rule |
|---|---|---|---|---|---|---|
| ALL_sel_T4_t15 | +10,973 (18,958) | -4,162 (15,030) | -4,324 (13,430) | -6,177 (12,458) | +3,935 (11,031) | 466,422 -> 404,155 |
| HM_base | +4,598 (7,549) | +3,470 (6,072) | +3,566 (5,667) | +132 (6,137) | +1,544 (3,430) | 466,422 -> 468,198 |
| HM_F3gate_w10 | +4,340 (7,328) | +2,853 (6,134) | +2,943 (5,693) | +3,033 (4,347) | +686 (2,584) | 466,422 -> 470,370 |
EQR first-order (worst-20 weeks matched, maxDD in brackets): ALL cell c 0.993 L6M -4,588 / HOLD -4,657 (-7,588 / -7,004); HM base c 1.044 L6M +6,479 / HOLD +6,003; HM F3 gate c 1.033 L6M +5,142 / HOLD +4,793 / PRE +4,608 / X' +1,397. The F3 gate is worse than the ungated HM rule in L6M/HOLD on the stack (+2.9k vs +3.5k) and better in PRE (+3.0k vs +0.1k): no stable gain from the gate.

## 6. Learned
1. A recovery trigger from tape (delta/OFI/aggression/big prints) or the 1-min footprint does not improve the path rule: 472 of 480 non-HM cells are not selective, and the 8 selective ones are N-negative in L6M/HOLD (pooled) or inside MDE.
2. The tape/footprint triggers are state descriptors that are true most of the time near a new MAE; they do not discriminate recoveries from continuations enough to veto cuts selectively.
3. HM: gating the registered a30_w10 cut by the footprint (F3) raises PRE and recent N slightly but lowers X'; within noise, placebo rank 0.79.
4. Credit share: LIVE-CAL gains are 44-100% stop-cost credit; on N almost nothing survives (ST +0.17, HM F3 +0.19 L6M, MDE 1.4).
5. Two cycles (RARE/SEQ/DRAIN/GATE book danger triggers; tape/footprint recovery triggers) leave the path rule untouched in effect: L2 state does not separate losers that recover from losers that run at the -20..-40 pt arm.

## 7. Next family (differs from cycles 1 and 2)
Change what is managed rather than when to cut: a stop-geometry / size-down rule (reduce the position at the arm instead of exiting, cut-half with the second half on a trail), or an ENTRY-conditioned loss rule (book state at the entry second predicting which trades ever reach -30: an avoid-the-entry filter scored per trade, not an exit trigger) using the L2P library hazard on the entry second. Both avoid the 98%-fire path rule problem.

## 8. D6 needs (also in DS3_THL2_NEEDS.md)
delta60 is in D6. NOT in D6: delta10, ofi5_10/ofi5_30 (CKS order-flow imbalance over 5 levels summed over 1-s bins, sided), delta_acc = delta10/10 - (delta60 - delta10)/50, vol10-based aggression share delta10/vol10, big25_net30 (net aggressor volume of prints >= 25 contracts in 30 s), 1-min footprint fields fp_delta_norm, fp_stack_with/against (3 consecutive diagonal 3x imbalances, min 4 contracts), fp_unfin_behind (both aggressor sides traded at the bar's behind extreme). The HM F3 gate needs fp_delta_norm > 0 and fp_unfin_behind == 0 on the latest completed 1-min bar. Not promoted.
Files: code/uf/uf2_{cells,build,engine,stageB,stack,report}.py; out/uf/loss1/{cells2_PRE_X.csv,selection2_PRE.json,stageB2.pkl,stack2.json}; DEAD_CELLS.csv +522 rows (program UFL2).
