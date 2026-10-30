# DS3_L2_UF_LOSS_C1 - L2-UNTIL-FOUND cycle 1, LOSS side (agent UF-LOSS, 2026-10-30)
Research only. UNTOUCHED (> 2026-02-06) never read. Own masks: 2026=20260101..0206 (~5 real weeks, nearly uninformative), L6M=20250801..0206, HOLD=20250701..0206, PRE=20240201..20250630, X'=20230401..20240131. Prereg `l2vast/ds3/prereg/UF_LOSS_C1_prereg.md` sha256 13db0ff4a7a7f2f0aa191298b85c8203de582f55306f8323599ef4a52162f9df (logged in DECISIONS.md before any statistic of the new cells). Selection file `out/uf/loss1/selection_PRE.json` sha256 f674c9ad4b147d3e28fb16d7c86f259381bc93a45d0a590c25dbcb17c4cc1731 (PRE+X' only, logged before the recent look). ONE recent look, selected cells + controls only.
Basis: **LIVE-CAL is primary** (stop-class exit 2.45 pt worse than nominal instead of M's 1.01, market exits at M, target correction 0), M is the stress case, N also shown. LIVE-CAL = N + 1.44 pt per cut/tighten that avoids a base stop - (2.45 - stop walk) per executed tightened stop. **"credit" = how much of the LC mean is that stop-cost credit** (LC - N). Numbers: pts/trade vs hold-to-stop, `mean [n fired] (MDE)`, MDE = 2.8 SE, day x ENTRY-session clusters. N-basis note: a cut changes target exits only by forfeiting a touched target, so N differs from M by -corr_y (1.4/1.5/4.2/4.3) on every fired trade whose base exit is the target (N is lower than M for cuts); tightening likewise only when it executes.

## 1. Settings table (recent first). Result: no PASS, no CANDIDATE; the best-available is NEGATIVE in L6M/HOLD
Fire % = share of arm-reaching trades with a decision row (< 50% required; every published cell is selective). Selection rule: fire < 50% in PRE and X', n fired PRE >= 100 (60 per book), X' LC mean >= 0, max PRE LC; hazard cells are not selectable (no X' fit); the HM cell is the HM a30_w10 path rule gated by the book (section 4).
| group | cell (selected on PRE+X' only) | fire % (L6M) | 2026 | L6M | HOLD | PRE | X' | L6M M / N | credit in L6M LC | rank shuffled-book (L6M/HOLD) | rank random-cut | fixed same-arm cut L6M/HOLD | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | A30|SEQ|SEQ(kWC>kP2)&NE|cut | 26 | -1.40 [381] (1.68) | -0.17 [1489] (0.76) | -0.07 [1597] (0.70) | +0.15 [3161] (0.45) | +0.19 [1106] (0.70) | -0.24 / -0.35 | +0.18 | 0.00/0.25 | 1.00/1.00 | -1.27/-0.93 | BEST-AVAILABLE-NEGATIVE |
| ST | A20|RARE|P2&I&S&ESA|cut | 5 | -0.44 [12] (1.87) | -0.86 [44] (0.96) | -0.71 [48] (0.88) | +0.28 [120] (0.47) | +0.11 [26] (0.61) | -0.82 / -0.89 | +0.03 | 0.00/0.00 | 0.10/0.10 | -2.69/-1.91 | BEST-AVAILABLE-NEGATIVE |
| HM | HM|a30w10|veto TH3|cut | 25 | +0.32 [30] (3.27) | +0.17 [135] (1.52) | +0.23 [149] (1.41) | +0.43 [407] (1.04) | +0.96 [78] (0.97) | +0.10 / -0.00 | +0.17 | n/a | n/a | n/a | CANDIDATE-RECENT (no gate fail on sign; MDE>>effect) |
| WT | A30|SEQ|SEQ(kWC>kP2)&NE|cut | 19 | -0.62 [32] (1.29) | -0.04 [148] (0.54) | -0.03 [154] (0.48) | +0.09 [284] (0.29) | +0.19 [100] (0.42) | -0.10 / -0.15 | +0.11 | 0.25/0.20 | 0.95/1.00 | -0.45/-0.26 | BEST-AVAILABLE-NEGATIVE |
| KB | A20|SEQ|SEQ(kWC>kP3)&NE|cut | 5 | -0.61 [8] (1.46) | +0.03 [43] (0.76) | -0.05 [48] (0.72) | +0.29 [100] (0.39) | +0.12 [60] (0.89) | +0.02 / -0.01 | +0.04 | 0.40/0.30 | 1.00/0.95 | -2.01/-1.49 | BEST-AVAILABLE-NEGATIVE |
| SM | A30|SEQ|SEQ(kWC>kP2)&NE|t15 | 24 | -0.69 [14] (4.85) | -0.17 [44] (1.43) | -0.06 [48] (1.25) | +0.11 [117] (0.63) | +0.22 [59] (0.49) | -0.19 / -0.22 | +0.04 | 0.00/0.15 | 0.15/0.20 | -0.31/-0.28 | BEST-AVAILABLE-NEGATIVE |
| PE | A30|RARE|ANY30(P2,I,WC,S)|cut | 42 | -0.93 [86] (3.92) | -0.37 [316] (1.96) | -0.20 [340] (1.82) | +0.62 [725] (1.08) | +0.41 [242] (1.90) | -0.45 / -0.66 | +0.29 | 0.25/0.30 | 1.00/1.00 | -1.18/-1.23 | BEST-AVAILABLE-NEGATIVE |

Pooled selected cell, all windows, dollars at live lots (LIVE-CAL; saved = sum of positive deltas, forfeited = recoveries given up):
| window | n | fired | LC pts/trade (MDE) | M | N | $/wk LC (saved / forfeited) |
|---|---|---|---|---|---|---|
| 2026 | 2229 | 381 | -1.40 (1.68) | -1.42 | -1.58 | -82,779 (+150,033 / -232,812) |
| L6M | 9743 | 1489 | -0.17 (0.76) | -0.24 | -0.35 | -9,725 (+140,055 / -149,781) |
| HOLD | 10805 | 1597 | -0.07 (0.70) | -0.14 | -0.24 | -3,190 (+132,111 / -135,301) |
| PRE | 24654 | 3161 | +0.15 (0.45) | +0.05 | -0.01 | +6,800 (+113,890 / -107,090) |
| X | 8926 | 1106 | +0.19 (0.70) | +0.06 | +0.04 | +4,658 (+66,319 / -61,662) |

Cumulative-adjusted reality check. (i) White RC over the cycle's 480 cells on PRE daily sums (LC): p = 0.000, but the maximiser is `A40|DRAIN|DR1&NE|t15`, PRE +0.008 pt/trade (MDE 0.004, 294 fired, about $1/wk): a studentisation artefact of a near-zero-variance cell, economically nothing, not selected (no recent look). Restricted to the 168 cells with n fired >= 100 and fire < 50% it is the same cell (p 0.000). (ii) cumulative: N_cum = 143,584 (DEADCAT exact; distinct specs 81,198) + 480 = 144,064; selected pooled cell L6M LC t = -0.63, one-sided p 0.74, Bonferroni-cumulative p = 1.00 (every selected cell p_adj = 1.00; best single L6M t is +0.12, KB). n_effective of the 480 cells = 13.7 (18.1 over the 168 cells with n>=100). Appended to UF_TRIALS.json (cycle 1, loss, 480 cells).

## 2. What the 480 cells show (PRE and X' only for unselected cells; fire < 50% cells; LIVE-CAL)
| fam   |   cells |   fire_med |   PRE_LC_med |   PRE_LC_max |   X_LC_med |   pos_both |   all_cells |   not_selective(>=50%) |
|:------|--------:|-----------:|-------------:|-------------:|-----------:|-----------:|------------:|-----------------------:|
| DRAIN |      84 |     0.0003 |       0      |       0.0376 |     0      |         24 |          84 |                      0 |
| ES    |      36 |     0.0044 |       0.0029 |       0.0138 |     0      |          2 |          36 |                      0 |
| HAZ   |      12 |     0.1046 |       0.0642 |       0.3177 |     0.0315 |         12 |          24 |                     12 |
| HM    |       4 |     0.027  |       0.0375 |       0.0401 |     0.0911 |          4 |           4 |                      0 |
| RARE  |      80 |     0.0365 |      -0.0046 |       0.0566 |     0.0054 |         18 |          80 |                      0 |
| SEQ   |     144 |     0.0028 |       0.0006 |       0.1452 |     0      |         36 |         144 |                      0 |
Top 10 selective cells by PRE LC (pooled; M and N beside; MDE = PRE LC MDE):
| cell                          |   fire_PRE |   nfire_PRE |   PRE_LC |   PRE_M |   PRE_N |   PRE_mde |   X_LC |
|:------------------------------|-----------:|------------:|---------:|--------:|--------:|----------:|-------:|
| A20|HAZ|p>=0.9|cut            |      0.439 |        7375 |    0.318 |   0.013 |  -0.07  |     0.483 |  0.163 |
| A20|HAZ|p>=0.9|half           |      0.439 |        7375 |    0.159 |   0.006 |  -0.035 |     0.241 |  0.082 |
| A30|SEQ|SEQ(kWC>kP2)&NE|cut   |      0.218 |        3161 |    0.145 |   0.052 |  -0.007 |     0.445 |  0.185 |
| A20|HAZ|p>=0.95|cut           |      0.091 |        1529 |    0.141 |   0.066 |   0.056 |     0.153 |  0.063 |
| A30|HAZ|p>=0.95|cut           |      0.105 |        1517 |    0.131 |   0.056 |   0.047 |     0.147 |  0.063 |
| A20|SEQ|SEQ(kWC>kP3)&NE|cut   |      0.046 |         770 |    0.119 |   0.097 |   0.082 |     0.21  |  0.02  |
| A30|SEQ|SEQ(kWC>kP3)&NE|cut   |      0.041 |         595 |    0.093 |   0.072 |   0.063 |     0.153 |  0.073 |
| A30|SEQ|SEQ(kP2>kI>kS)&NE|cut |      0.082 |        1184 |    0.089 |   0.05  |   0.03  |     0.249 |  0.107 |
| A20|SEQ|SEQ(kWC>kP3)&NE|t10   |      0.046 |         770 |    0.086 |   0.085 |   0.081 |     0.119 | -0.036 |
| A20|SEQ|SEQ(kP2>kI>kS)&NE|cut |      0.102 |        1719 |    0.083 |   0.045 |   0.003 |     0.357 |  0.081 |
Reading. (a) No cell is above its PRE MDE except hazard cells, whose PRE LC gain is nearly all stop-cost credit (A20 p>=0.9 cut: LC +0.32, M +0.01, N -0.07). (b) **Sequence carries no information**: forward order pull->wall-collapse (A30 z2: PRE +0.07, X' +0.14) is not better than the reversed order wall-collapse->pull (+0.145 / +0.185 = the selected cell), and pull->iceberg->sweep +0.09 vs sweep->iceberg->pull +0.01 (n 37): the selected pooled cell is the reversed-order CONTROL, a co-occurrence of two rare states, not a cascade sequence. (c) ES confirmation (es_imb5 <= -0.3/-0.5) alone or inside RARE/SEQ is almost never true together with the other flags (fire 0.1-0.4%), PRE medians 0.00. (d) Queue-drain rules (refill < 0.5 and consumption > 0 on the own-side best, at a new MAE) fire on 0.03% (DR2) to 2.4% (DR1 at A40): refill_ratio_behind10 has median 5.8, drain is rare and carries nothing (PRE LC -0.04..+0.04). (e) GATE: the path rule itself (cut at -A on a new adverse extreme) fires on 98% of arm-reaching trades (NOT selective, median over GATE cells); thick+refilling gates remove too few cuts to change that; the >= 2/3-of-5-rare-flags versions fire 8-45% with PRE LC median -0.11.

## 3. Controls and placebos (selected cells, LIVE-CAL, 20 draws each; rank = share of placebo draws below the real mean)
Pooled A30 SEQ(kWC>kP2) cut: shuffled book within day rank L6M 0.00 / HOLD 0.25 (PRE 1.00): the real rule is WORSE than a shuffled book in the recent windows. Random cuts at the same per-trade rate rank 1.00 / 1.00, but the unconditional fixed A30 cut is -1.27 L6M / -0.93 HOLD, so any selective rule "beats" random and fixed cuts by construction; the right comparator is hold-to-stop (0): the rule is -0.17 / -0.07. Per-book shuffled-book ranks are in the table (<= 0.40 in every recent window). Placebo beaten: NO.
Session cells (ENTRY session, pooled selected cell, LC pts/trade, MDE, n fired), L6M: asia -0.24 (2.09, 835), london -0.71 (2.14, 423), pre +0.59 (2.00, 50), nyam -0.16 (0.41, 37), nypm +0.39 (0.74, 139); PRE: asia -0.06, london +0.63 (1.08), pre +0.38, nyam -0.05, nypm +0.05. Nothing outside MDE; London (the thin-book session) is negative in L6M.

## 4. HOLD side: path rule gated by the book (HM base = a30_w10)
HM a30_w10 path rule (frozen primary, definition unaltered: arm 30, C1 4.0 pt worse than 10 s ago, C2 no new extreme for 10 s and recovery <= 4, C3 efficiency < 0.35) re-implemented on the 1-s path of the THP HM-book trades (4,156 trades; the retest's 2,924-trade stack stream has no stored exit second), then vetoed (hold to stop, no re-arm) when the own-side book at its firing second is thick and refilling. LC, M beside:
| cell | window | fire % of arm-reaching | LC | M | MDE(LC) | $/wk LC (saved / forfeited) |
|---|---|---|---|---|---|---|
| HM|a30w10|ungated|cut | 2026 | 26 | +0.32 | +0.25 | 3.27 | +2,155 (+18,021 / -15,866) |
| HM|a30w10|ungated|cut | L6M | 25 | +0.17 | +0.10 | 1.52 | +1,079 (+17,089 / -16,010) |
| HM|a30w10|ungated|cut | HOLD | 25 | +0.23 | +0.15 | 1.41 | +1,431 (+16,170 / -14,738) |
| HM|a30w10|ungated|cut | PRE | 30 | +0.41 | +0.27 | 1.05 | +2,517 (+18,796 / -16,279) |
| HM|a30w10|ungated|cut | X | 16 | +1.06 | +0.95 | 0.99 | +4,162 (+6,862 / -2,700) |
| HM|a30w10|veto TH1|cut | 2026 | 25 | +0.16 | +0.10 | 3.25 | +1,090 (+16,956 / -15,866) |
| HM|a30w10|veto TH1|cut | L6M | 23 | +0.05 | -0.01 | 1.47 | +310 (+15,615 / -15,305) |
| HM|a30w10|veto TH1|cut | HOLD | 22 | +0.06 | +0.00 | 1.36 | +391 (+14,437 / -14,046) |
| HM|a30w10|veto TH1|cut | PRE | 27 | +0.40 | +0.26 | 1.01 | +2,407 (+17,238 / -14,831) |
| HM|a30w10|veto TH1|cut | X | 12 | +0.93 | +0.84 | 0.75 | +3,649 (+4,992 / -1,343) |
| HM|a30w10|veto TH2|cut | 2026 | 25 | +0.16 | +0.10 | 3.25 | +1,090 (+16,956 / -15,866) |
| HM|a30w10|veto TH2|cut | L6M | 23 | +0.05 | -0.01 | 1.47 | +310 (+15,615 / -15,305) |
| HM|a30w10|veto TH2|cut | HOLD | 22 | +0.06 | +0.00 | 1.36 | +391 (+14,437 / -14,046) |
| HM|a30w10|veto TH2|cut | PRE | 27 | +0.40 | +0.26 | 1.01 | +2,407 (+17,238 / -14,831) |
| HM|a30w10|veto TH2|cut | X | 12 | +0.93 | +0.84 | 0.75 | +3,649 (+4,992 / -1,343) |
| HM|a30w10|veto TH3|cut | 2026 | 26 | +0.32 | +0.25 | 3.27 | +2,155 (+18,021 / -15,866) |
| HM|a30w10|veto TH3|cut | L6M | 25 | +0.17 | +0.10 | 1.52 | +1,079 (+17,089 / -16,010) |
| HM|a30w10|veto TH3|cut | HOLD | 25 | +0.23 | +0.15 | 1.41 | +1,431 (+16,170 / -14,738) |
| HM|a30w10|veto TH3|cut | PRE | 29 | +0.43 | +0.29 | 1.04 | +2,639 (+18,614 / -15,975) |
| HM|a30w10|veto TH3|cut | X | 15 | +0.96 | +0.85 | 0.97 | +3,746 (+6,446 / -2,700) |
The gate is a null: TH3 (own-side depth >= 1.5x normal AND net adds >= pulls AND queue refill >= 1) vetoes 10 of 644 cuts; TH1/TH2 veto about 20 and make L6M worse (+0.05). Random veto at the same rate: rank 0.61 (L6M), 0.62 (HOLD), 0.73 (PRE). The un-gated HM rule is >= 0 on LC in every window and fires on 25% of arm-reaching HM trades (selective) but its effect (+0.17 L6M, +0.23 HOLD) is inside MDE 1.4-1.5 (M +0.10 / +0.15; N 0.00 / +0.06): the LC sign is the stop-cost credit (+0.17). It is the already registered forward primary, not a new finding; it stays LEAD (tier: CANDIDATE-RECENT at most, cumulative RC fails).

## 5. Stack (exact 6-book lock engine, M-basis engine, $/wk delta vs base; MDE in brackets) and equal-risk scaling
| stream | L6M d$/wk (MDE) | HOLD | PRE | X' | maxDD L6M base->rule | worst-20 L6M base->rule |
|---|---|---|---|---|---|---|
| ALL_SEQcut | -16,256 (24,707) | -12,986 (22,325) | -6,533 (15,048) | -1,631 (11,984) | 466,422 -> 457,997 | 204,018 -> -46,527 |
| COMBO_perbook5 | -15,984 (12,860) | -13,989 (11,870) | -1,263 (7,493) | +2,473 (6,911) | 466,422 -> 562,098 | 204,018 -> -148,535 |
| HM_a30w10 | +3,470 (6,072) | +3,566 (5,667) | +132 (6,137) | +1,544 (3,430) | 466,422 -> 468,198 | 204,018 -> 256,283 |
| COMBO_perbook5+HM | -12,514 (14,107) | -10,424 (12,753) | -1,132 (9,411) | +4,017 (7,897) | 466,422 -> 563,874 | 204,018 -> -77,337 |
Equal-risk (EQR frame, first-order: stack scaled by c so that WF (PRE+HOLD) worst-20 weeks (maxDD in brackets) equals base; no lot-rounding sweep): pooled SEQ cut c 0.95 (1.10): L6M -18.7k (-11.2k), HOLD -15.0k (-8.9k); per-book 5 c 0.97: L6M -17.6k, HOLD -15.2k; HM a30_w10 c 1.04 (1.01): L6M +6.5k (+4.4k), HOLD +6.0k (+4.3k), PRE +2.1k, X' +2.5k; per-book 5 + HM: L6M -11.6k, HOLD -9.7k. LIVE-CAL credit on the stack is first-order (+0.17 pt per fired HM cut; +0.18 pooled per arm-reaching trade); engine exits not re-run on LIVE-CAL.

## 6. Learned
1. The rare-state/cascade family (pull z, iceberg, wall collapse, sweep, ES) gives selective cells (0.1-40% fire), slightly positive in PRE and X' (+0.1 pt, inside MDE), negative in L6M/HOLD/2026 (pooled LC -0.17 / -0.07 / -1.40), and worse than a shuffled book recently. Cutting a loser at -20/-30 from book signals does not work in the recent regime.
2. Event ORDER has no information (reversed order as good or better).
3. ES confirmation and queue drain are too rare to evaluate (n fired < 100 in most cells; MDE > any plausible effect).
4. Gating the path rule by a thick, refilling book is a null (vetoes 0-3% of firings).
5. A large part of every LC gain is stop-cost credit (0.03-0.34 pt/trade); on N the selected recent numbers are -0.35..+0.06.
6. Hazard (walk-forward logistic on rare rows): PRE LC +0.32 but M +0.01 / N -0.07: pure credit; not evaluated recent (not selectable).

## 7. Next family (must differ from RARE/SEQ/DRAIN/GATE)
Management that is not a danger trigger from the 10-s book: (a) cut-WAIT conditioned on 1-min footprint at the new MAE (t3 fp_* absorption / stacked imbalance at the extreme), a different data source; (b) HOLD-through when delta60 and OFI turn with the trade within 30 s of the new MAE (a recovery trigger instead of a danger trigger), scored on the stop-avoided vs recovery asymmetry with LIVE-CAL.

## 8. Needed in D6 (also in DS3_THL2_NEEDS.md)
Selected pooled cell: pulledZ10 = z of log1p(pulled_sup10) vs the same 15-min ET bucket of PRIOR calendar months (>= 2 / >= 3); wallCollapse30 = cum_behind5 now <= 0.5 x max of cum_behind5 over the previous 3 ten-second rows (own-side levels 1-5; long bids, short asks); newAdvExt10; last-true-row offsets within 60 s (sequence state). Not in D6 today: pulledZ10, wallCollapse30, sequence state, es_imb5, refill_ratio_behind10, cons_behind10, added_sup10, TH1-3 (cum_behind10_rel >= 1 / 1.5, added_sup10 >= pulled_sup10, refill >= 1). D6 has imb5/imb10/delta60/curDepthRel/pulled_sup10 and the path set only.
Files: code/uf/uf_*.py; out/uf/loss1/{cells_PRE_X.csv,selection_PRE.json,stageB.pkl,stack.json,hm_ctl.pkl}; DEAD_CELLS.csv +480 rows (program UFL1).
