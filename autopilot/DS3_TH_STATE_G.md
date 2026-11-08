# DS3_TH_STATE_G - learned TH rule on S1-COMB (program G, S2-G)
**Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched; the per-book COMB procedure fails the out-of-sample walk-forward (DS3_TH_STATE.md section 5) so S1-COMB is an in-sample base.** Prereg: th_redo/prereg/TH_REDO_PREREG_G_S2_ADDENDUM.md (sha 07686515..., DECISIONS.md, filed before any number). Code: code/th_redo/s2g_build.py, s2g_fit.py, s2g_an.py. Data/tree: /mnt/l2/l2vast/_th_state/s2/G/.

## Verdict
**No learned rule ENTERS vs S1-COMB. Best learned add-on per book is flat or negative out of sample in every book; the family null is not rejected.** The learned trees mostly learn elapsed_s (time in trade, i.e. the long-hold tail), not book state.

## Method (as pre-registered)
18.0M G rows (every 5th wall second per open S1-COMB trade, 32 L1+L2+path features + session + clock hour), 21,067 trades, 2023-04..2026-10. Label y_h = P(t+h) - (P(t) - 0.80) pts (P = S1-COMB mark path, realized S1-COMB exit if the trade ends first), h 30/60/120 s. ADD-ON exit: first row with predicted y_h < thr (thr 0 / -1 / -2.5 pts) exits at row mid -+ 0.80 (bracket touches inside the 5 s gap ignored). Grid 7 books x loss/profit side (sign of upnl) x h x thr x learner {tree <= 6 leaves; lightgbm depth-3 80 trees as non-codable upper reference} x 3 seeds = 756 cells. Walk-forward: quarterly refit 2024Q1..2026Q4, expanding train capped at 24 months, 7-day purge, 80k-row train samples, targets clipped +-30. Windows are OOS only (X' 2023-04..2024-01 has no OOS value). Delta USD/week vs S1-COMB, carrying week dropped, MDE 2.8 sd/sqrt(n).
Deviations: replacement mode NOT evaluable on this path (rows after an S1-COMB state cut do not exist; needs an engine run); null worlds W = 50 (not 100: the box cap forced the pool down; 50 worlds completed); random-exit placebo not run because no cell passes the pre-gate (L6M > 0 and PRE > 0 above MDE); Stage 2 engine cascade NOT run for the same reason (no finalist). Live week: G rows for 2026-11 do not exist in the S1-COMB tree (months end 202610), so the held-out live-week table is NOT AVAILABLE.

## Best learned rule per book (tree, loss rule + profit rule chosen by median-over-seeds S = min(L6M, PRE); OOS add-on delta USD/week vs S1-COMB; MDE in brackets)
| book | loss rule | profit rule | fires | OOS total | L1M | L2M | L3M | L6M | HOLD | MID | PRE | maxDD L6M base/rule | maxDD PRE base/rule |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | h30 thr-2.5 | h120 thr-2.5 | 349 | -25999 | 0 | -105 | -119 | +103 (335) | -117 | -245 (627) | 42654/40083 | 23160/23160 |
| P7 | h30 thr0 | h120 thr-1 | 431 | -117933 | -2637 | -1557 | -702 | -294 (1491) | -281 | 1710 | -536 (3080)* | 47774/39304 | 115751/116996 |
| M7 | h120 thr0 | h30 thr0 | 143 | -25650 | 0 | 96 | 0 | -20 | 13 | -70 | -209 | 42281/40412 | 27743/28103 |
| U7 | h30 thr-2.5 | h30 thr-1 | 122 | -24109 | 0 | -646 | -252 | -149 | 251 | -279 | -140 | 16039/16039 | 38773/42436 |
| A7 | h30 thr-2.5 | h30 thr-2.5 | 210 | -19453 | 0 | -215 | -200 | -155 | -49 | -201 | -97 | 9155/9235 | 7216/7151 |
| H7 | h60 thr-2.5 | h30 thr-2.5 | 114 | -22542 | 66 | 28 | -67 | -30 | -56 | -178 | -121 | 7489/7489 | 12321/10939 |
| O7 | h120 thr-2.5 | h60 thr-2.5 | 36 | -5001 | 792 | -155 | 142 | 29 | 14 | 0 | -23 | 8892/8892 | 4489/4489 |
(Columns as in file final_table.csv; the K7 row's MDE per window is in that CSV. * P7 PRE shown with MDE.) Every book has a negative OOS total and PRE <= 0 (K7 L6M +103 is below MDE 335 with PRE -245; O7 L6M +29, far below MDE 506, PRE -23). Not one book has L6M > 0 and PRE > 0 above MDE.

## Nulls
- Shuffled-label family null (W = 50, 126 tree cells refit per world, same walk-forward): observed max OOS t-stat 1.25 vs null max median 1.73 (90% 2.23, max 2.63): p_family = 0.80. Observed max S = +3.8 USD/week vs null median 0.2, 90% 29.9: p = 0.47. The trees do not beat what shuffled labels produce.
- Fire rate: the 0 / -1 / -2.5 pt thresholds fire on very few rows because 6-leaf trees shrink toward the mean (y mean +0.7 with the 0.80 exit cost); best-case fires 36-431 trades over 34 months per book.
- lightgbm reference (not codable): best cell K7 loss h120 thr -1, S = +114 USD/week (L6M +221, PRE +236, OOS total +13373, t about 1); 7 of 126 gbdt cells have S > 0, all small; M7 profit h30 thr-1 L6M +120 PRE +35. None cleared MDE or the family null (not tested against the gbdt-specific null: the family null was tree-only, so these are best-of-F, not evidence).

## Decision functions (exact trees, fit on the last 24 months through 2026-10-31, 200k rows; for the record, NOT recommended)
See /mnt/l2/l2vast/_th_state/s2/G/final_trees.md (all 14 trees with thresholds, leaf values, importances). Sample (K7 loss: exit if predicted y_30 < -2.5): the tree reads elapsed_s (> 49,781 s and pct_tgt > -0.535 gives -3.9), importances elapsed_s 0.48, pct_tgt 0.32, atr5 0.20. K7 profit and P7 profit trees are pure time-in-trade ladders (elapsed_s importance 0.86 for K7; P7 loss rule: recov_pts 0.38, elapsed_s 0.28, pull_pts 0.26). Across books the only stable features are elapsed_s, recov_pts, pct_tgt, atr5: path/time features, not the 1-s book state (pulled5, imb, iceberg, delta features carry ~0 importance), consistent with the void program's finding of no signal beyond regime/clock features.
Policy-file lines: none (nothing ENTERs). Grammar gaps if it ever did: predicted-value rules need a tree/table primitive; the closest D7 form is a conjunction of elapsed_s / pct_tgt / atr5 thresholds, and the grammar has no per-rule hold time-in-trade >= 20,000 s field mixing with pct-of-target.

## Verdict vs S1-COMB: DO NOT ENTER (all seven books). Best-of-F labels apply to everything above.
