# REPORT IDEAS-50K N5 + FINAL F_eff / best-of-F / PAPER-ALL (ORDER 10-19 item 2), 2026-10-19

## Part A: N5 microstructure (NQ/ES trades with aggressor side, 1-60 s)
- 88 families (10 types x NQ/ES x 4 blocks + 8 lead-lag), 21,712 cells scored after spec/series dedupe and the 20-active-day filter (planned 22,528), METHOD-2 12/3/3 tilt, custom drift-matched random-entry null (200 reps), gates a-d, first OOS week 2024-02. Code ap_n5.py / ap_n5_run.py (tables stage then score stage, 16 processes, about 52 min). Runtime 3,107 s per job-batch; ~100 families/hour.
- Result: **0 of 88 pass gates a-d** (chance 4.4). Best: N5-FADEC-NQ-OPEN OOS Sharpe 0.29 (null rank 0.915, fails b, c), N5-BURST-NQ-CLOSE 0.20 (rank 0.925). Everything else negative or flat. 51 families have NaN Sharpe: the tilt gave no cell a positive fit-window Sharpe, so the OOS book is flat (counted as scored, gates fail). Reading: one NQ round trip costs $14.36 before any edge (2 ticks + commission); at 5-60 s holds the aggressor-flow signals do not clear it.
- Gate 0 / order-state: every N5 entry and exit is a market order (order_form market); no resting orders, so gate 0 is not applicable. Pair-corr is stored per row in FAMILY_RESULTS (all near 0).
- Note: FAMILY_LIST says 88 families (prereg text 80 planned).

## Part B: final F_eff, best-of-F, PAPER-ALL (snapshot at 2026-10-19 ~18:00Z; N9-N21 blocks are still being appended by the n9 agent, re-run ap_m2_final_f.py --recluster / ap_m2_fclusters.py when they finish)
- F_eff, greedy clusters at correlation >= 0.5, two bases: (i) full-coverage equal-risk weekly ensemble per family from the matrices (ap_m2_fclusters.py, F_CLUSTERS.csv): 3,680 families -> **1,208 clusters** (participation ratio 48.1); this is used as the GATE F_eff (largest, hence strictest, and it covers every registered family). (ii) OOS-series basis (descending OOS Sharpe leaders, only the 1,244 families with a stored OOS series): 761 clusters (F_CLUSTERS_oosbasis.csv). Previous F_eff was 594. Pooled null G: methods2/null/*.npy (170,189 draws), sensitivity with every stored family null (264,652 draws): same outcome.
- best-of-F rank = G(s)^F_eff. **Best-of-F passers (>= 0.95): 0** at F_eff 1,208, 761 and 594. Only the optimistic PR-based F=56 gives 2 (not used). Highest best-of-F among IDEAS-50K gate passers: N1-EN_HO_RB-5m-MR 0.045 (F 1208). FAMILY_RESULTS.best_of_F_rank rewritten (under the methods2 lock, only that column) for all 3,592 rows.
- True gate a-d count, IDEAS-50K (latest row per family, K-refill neighbours excluded): **20** (N1 1, N2 1, N3 5, N4 1, N7 4, N8 3, N10 3, N13 1, N16 1) against chance 104 (5% of 2,081 families; 2-3% POWER2 rate gives about 40-60). N5 0, N6 0, N9 0, N11 0, N12 0, N14 0, N15 0, N17-N21 0. Passes sit well below chance overall: no evidence of discoverable edge in the new spaces. ap_m50k_status.py now covers N1-N21 (output in the summary below).
- Not counted: N11-FIRSTBAR-MET (Sharpe 1.21) and N13-CSMOM-COMMXX (0.99) have gates a-d True under a sign-flip null that the n9 agent marked invalid for beta-exposed books; gates_pass=False pending a drift-matched null. Not softened here.
- PAPER-ALL: appended 5 rows (ap_m2_paperall.py freeze --append, the post-N1-RT-fix version with OOS_CUT 20261009 and SPARSE logic, untouched; existing 169 rows kept; refit date 2026-07-31): N10-CSMAX-MENR, N10-CSMAX-COMM, N10-CSVOL-MENR (flag "NG-short beta, not independent"), N13-XLEAD-HO, N16-F1-RTY. N5 contributed none. All 20 IDEAS-50K passers are now in PAPER-ALL (174 rows). Passers not registered by existing rule: -K refill neighbours (12), superseded B7, and pre-existing non-IDEAS C9R1 / D1F8 / D2E9 (outside this task). Scored: LEAGUE.json / PAPERALL_WEEKS.csv; no row is promoted or killed (all under 6 weeks).

| passer | OOS Sharpe | null rank | best-of-F (F 1208) | weekly Sharpe @common size | worst week $ | max DD $ (OOS, common size) | forward z (1 wk) |
|---|---|---|---|---|---|---|---|
| N1-EN_HO_RB-5m-MR | 1.83 | 0.980 | 0.045 | 1.85 | -26,923 | 126,640 | -0.14 |
| N7-RSI-ES | 1.52 | 0.995 | 0.000 | 1.56 | -39,924 | 80,869 | -0.47 |
| N16-F1-RTY | 1.49 | 0.994 | 0.000 | 1.45 | -25,735 | 88,508 | +0.98 |
| N2-ISM_S-RANGE-MET | 1.35 | 0.995 | 0.000 | 1.35 | -24,942 | 49,857 | 0.00 |
| N4-NR7-ENR-c570 | 1.31 | 0.983 | 0.000 | 1.30 | -29,072 | 104,506 | +0.21 |
| N10-CSMAX-MENR | 1.31 | 0.988 | 0.000 | 1.31 | -34,166 | 89,927 | +0.23 |
| N8-DISP-6B | 1.30 | 1.000 | 0.000 | 1.27 | -37,083 | 71,139 | +0.75 |
| N3-ROLL-ZB | 1.27 | 1.000 | 0.000 | 1.27 | -48,040 | 48,040 | 0.00 |
| N10-CSMAX-COMM | 1.16 | 0.979 | 0.000 | 1.19 | -33,831 | 86,299 | -0.61 |
| N3-ROLL-ZN | 1.16 | 1.000 | 0.000 | 1.16 | -35,641 | 57,943 | 0.00 |
| N13-XLEAD-HO | 1.14 | 0.976 | 0.000 | 1.16 | -35,180 | 107,276 | -0.54 |
| N3-ROLL-ZF | 1.13 | 0.995 | 0.000 | 1.14 | -43,381 | 70,402 | 0.00 |
| N10-CSVOL-MENR | 1.09 | 0.960 | 0.000 | 1.19 | -34,599 | 87,972 | -1.75 |
| N3-CARRY-ES | 1.07 | 0.965 | 0.000 | 1.00 | -34,734 | 117,002 | +1.56 |
| N7-MRZ-HG | 1.07 | 0.995 | 0.000 | 1.08 | -50,549 | 108,230 | -0.08 |
| N3-ROLL-6J | 1.02 | 0.965 | 0.000 | 1.03 | -35,894 | 62,379 | 0.00 |
| N7-MRZ-YM | 1.00 | 0.985 | 0.000 | 0.99 | -68,550 | 92,378 | +0.16 |
| N7-RSI-HE | 0.97 | 1.000 | 0.000 | 0.94 | -55,075 | 106,616 | +0.64 |
| N8-CORR-6B | 0.95 | 0.995 | 0.000 | 0.91 | -36,236 | 107,711 | +1.00 |
| N8-RISK-6A | 0.85 | 1.000 | 0.000 | 0.87 | -83,516 | 104,548 | -0.31 |
Forward z is one week (W42) and is not evidence. N3-ROLL-* / ZB-ZN-ZF-6J are one bet. The three N10 rows are one NG-short bet. N1 passer is a rates/energy spread; its W42 contribution is negligible (REPORT_N1RT_FLAG).

## Files
outputs/methods2/FAMILY_RESULTS.csv (best_of_F_rank), F_CLUSTERS.csv (matrix basis, 1,208), F_CLUSTERS_oosbasis.csv (761), outputs/autopilot/REPORT_FAMILIES.md (regenerated by ap_m2_final_f.py), forward/m2/PRED_PAPERALL.json, PAPERALL_WEIGHTS.csv, LEAGUE.json; code/census/night_ins/ap_m2_final_f.py (lock-safe variant of ap_m2_compile.py with flat-series exclusion and F_CLUSTERS output), ap_m50k_status.py, ap_n5*.py; outputs/ideas50k/THROUGHPUT.csv, n5_score.log.
