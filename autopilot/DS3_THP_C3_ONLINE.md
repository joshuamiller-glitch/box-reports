# DS3_THP_C3_ONLINE - online learners, changepoint and flow-HMM walk-forward chains, profit AND loss (THPC3, 2026-10-29)

Research only; nothing here is a live recommendation. Prereg l2vast/ds3/prereg/THPC3_prereg.md (sha256 in DECISIONS.md; amendment A1 widened the margin grid before any chain statistic was read); PRE-only text autopilot/DS3_THP_C3_PREHOLD.md sha256 9d4b0bc78ac9b414dd3cd6480ba514667e4b20addd52baa9dc8cf6d68b3fdd33; one logged HOLD look per side (tracks THPC3_P, THPC3_L). UNTOUCHED (> 2026-02-06) never read. Fees identical in both arms. Code l2vast/ds3/code/thp_c3/; decisions parquets and cell tables in l2vast/ds3/out/thp/wf/c3/ (schema SCHEMA.md; decisions_<family>_<profit|loss>.parquet, placebo=0 rows for every cell; the placebo draw distributions are in cache/plc1_*.parquet and cpplc1_*.parquet, random-exit draws are summarised in the cell tables as ranks).

## Verdict (plain)
**0 PASS, 0 CANDIDATE, 2,468 DEAD of 2,468 cells (1,234 per side).** Re-fitting or updating after every closed trade (rls/rlog/ogbm/btab with forgetting from ~100 trades to no forgetting), CUSUM and Bayesian-online changepoint exits (fixed cells and walk-forward re-selection over 10 windows x 4 steps x 2 scopes), and a forward-filtered 2/3-state flow HMM (10 windows x 4 steps, 8 rules, K 2/3) add NOTHING over hold-to-bracket (profit) or hold-to-stop (loss) out of sample. White reality check on PRE: p = 0.988 profit, 0.972 loss (best-of-1,234). Cells with PRE > 0: 10 profit, 20 loss (chance expectation ~600 of 1,234 if signs were coin flips is NOT the right comparison because exits cost 0.995 pt each; all of these have CIs spanning 0 and MDE 0.3-1.1 pts). PRE>0 AND HOLD>0: 2 profit, 1 loss. Every cell fails paired_CI_excludes0, placebo>=0.90, neighbours_agree, RC_p>0.05, 2x_cost and NOTC (profit) - the gates are as in the prereg and none is softened.

Plain sentence: re-fitting on the last N weeks/months, or updating after every trade, the profit policy adds +0.0 pts/trade out of sample (best PRE cell +0.09 [-0.25,+0.43], MDE 0.49, HOLD -0.36 [-0.86,+0.14], MDE 0.71) and the loss policy +0.0 (best PRE ogbm m8 +0.20, HOLD -0.73): nothing adaptive beats holding on any book.

**Why the few positives are not signal.** (1) The M basis charges every target exit the year target correction (1.4/1.5/4.2/4.3 pts); a RANDOM exit at the cell's own rate and relative timing earns about +0.6..+0.9 pts/trade on the profit side at small exit rates (the artefact THPB flagged), so placebo rank vs random exits is 0.00 for every profit cell and every real cell loses to it; on the N basis (no target correction) the best cells are -0.04 or worse. (2) The HMM profit cell with HOLD +0.43 (MDE 1.76) has X-span -0.93 and PRE +0.06: sign flips between spans, year_share > 60%. (3) The loss side: shuffled-label models beat the real ogbm (rank 0.00) in PRE.

## Answers to the asked questions
* Online vs batch refit: online learners are worse than the batch-reselected changepoint chains, which are worse than "do nothing": rls -1.1..-1.3, rlog -0.7..-1.0, ogbm -0.3..-0.8, btab -0.4 (mean over cells, PRE, profit pts/trade) - the learners fire on noise at 70-85% of trades at margin <= 2 and each exit costs 0.995 pt. Larger margin (m 4, 8) cuts the damage, never makes it positive in HOLD. Forgetting: shorter memory (lam 0.99, ~100 trades) is not better than lam 1.0 in either span (rls PRE profit -1.13 at lam .99 per-book vs -1.27 pooled mean; HOLD about the same); no learning-rate/forgetting setting gives a CI above 0. Tighten (8-pt trail profit; 10-pt stop pull loss) is WORSE than take-only on average (btab profit -0.67 vs -0.38 PRE, -0.77 vs -0.35 HOLD).
* Recency (changepoint re-selection, mean over cells): short windows (1w, 2w, 1m, EWMA 5/10) are worse than long ones (12m, YTD, 6m) in PRE profit (cusum -0.51/-0.57/-0.58 vs -0.30/-0.15/-0.30; bocpd -0.48/-0.54/-0.37 vs -0.12/-0.24/-0.18) - recency adds noise, not signal. Intraday re-fits (09:30/12:00) are no better than daily: cusum PRE -0.35 intraday vs -0.42 daily, bocpd -0.39 vs -0.41, hmm -0.70 vs -0.70 (profit); all inside noise.
* Flow HMM: forward-filtered states exit 36-49% of profit trades at the best cells; PRE +0.06 / HOLD +0.43 / X -0.93 (MDE 1.0/1.8/1.9) - no stable sign. Loss side HMM best HOLD negative for every window except 1w (-0.83 vs -1.4), still negative.
* GRU: NOT RUN. PyTorch is not installed on this box and no installs are allowed; a numpy GRU was not attempted within the time budget (the simpler learners show no signal to chase).
* Drift: ridge coefficients flip sign between quarters (table below); the "top feature" is a session or book dummy or the bias in almost every snapshot, i.e. the fit tracks the target-correction regime change (2025: 4.2 vs 1.5), not the path.
* Distilled candidate: l2vast/ds3/out/thp/wf/c3/policy_candidate.txt (6 profit + 4 loss rules over pct, mins, secs_ext, dd, recov, vel30, eff120, delta60; tree fitted on all rows <= 20250630 to the remaining-P&L label; every rule is a long-hold (hours) leaf; HOLD out-of-sample -0.011 profit, +0.04 loss, MDE ~1-2; header says NOT for live). Retained gain versus the best walk-forward teacher: UNDEFINED - the teacher's own HOLD delta is negative (profit -0.36, loss -0.73) and the 12-leaf student of the teacher never fires (0 of 80% target met; there is no positive gain to retain). The honest policy file is hold-everything.

## Multiplicity
Per side: 380 online cells (38 configs x 5 margins x {take, take+tighten}) + 54 fixed changepoint cells + 160 adaptive changepoint chains + 640 HMM chains = 1,234; both sides 2,468. Plus 38 x 10 shuffled-label retrains, 20 random-exit draws per cell. Reality-check p and per-family p are printed per side.

## Look log
Disclosed: a 3-config smoke test printed PRE means only (prereg A1). PREHOLD sha above; HOLD and X read once after it. No config, grid or gate changed after the PREHOLD line. GRU skipped. A memory incident: one of my own test processes (a registry loader that retained a 60 MB array per cell) reached ~80 GB RSS before I stopped it through the task tool (MemAvailable fell to 43 GB, above the 32 GB floor); fixed, no other process touched.

## Notes on method (deviations stated)
Decisions of the learners and the HMM are on 1-min bar closes (a trade's first firing row); CUSUM on 1-s closes; BOCPD on a 10-s grid; mfe/mae arming in CUSUM/BOCPD uses close-based extremes. The HMM is fit on <=40k rows of <=220 sampled closed trades per refit (EWMA windows by recency-weighted sampling), warm-started. CR excluded. Tighten uses close-based trail checks (market at close - 0.995). Per-eligible-trade means are not printed (all means are over all scored trades); per-book rows are descriptive.

# DETAIL TABLES

# PROFIT SIDE (hold / tighten / take vs hold-to-bracket)

**Verdict counts over 1234 cells: {'DEAD': 1234}.** White reality check on PRE over all 1234 cells: p = 0.988; per family: bocpd_adapt 0.965, bocpd_fixed 0.987, btab 0.889, cusum_adapt 0.949, cusum_fixed 0.874, hmm 0.769, ogbm 0.905, rlog 0.977, rls 0.985.

Gates failed (count of cells): paired_CI_excludes0 1234, placebo>=0.90 1234, neighbours_agree 1234, RC_p>0.05 1234, 2x_cost<=0 1234, NOTC<=0 1234, SPAN2<=0 1233, year_share(total<=0) 1233, mean_up 1224, holdout_sign_agrees 1200, maxDD_not_worse 907, year_share>60% 1.

## OOS chain, best cell per family by PRE (IN-SAMPLE selection; HOLD and X are the confirmation spans)

| cell | PRE | HOLD | X | usd_wk | exit | saved_forf | win | plc | N_C | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bocpd_adapt|12m|1m|pooled | +0.02 [-0.17,+0.21] (MDE 0.27) | -0.07 [-0.13,+0.00] (MDE 0.10) | -0.87 (MDE 1.88) | +1,589|-3,829 | 0.04|0.00 | +0.82|-0.80 | 0.53>0.54 | 1.00|0.00 | -0.02|-0.02 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| bocpd_fixed|17|{'hz': 1, 'p': 2, 'X': 2} | -0.20 [-0.48,+0.09] (MDE 0.41) | -0.20 [-0.64,+0.25] (MDE 0.64) | -0.23 (MDE 1.04) | -10,968|-11,848 | 0.08|0.09 | +1.73|-1.92 | 0.53>0.55 | nan|0.00 | -0.33|-0.28 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| btab|disc0.9995|pooled|z1|m2|take | +0.09 [-0.25,+0.43] (MDE 0.49) | -0.36 [-0.86,+0.14] (MDE 0.71) | -0.83 (MDE 1.57) | +6,023|-20,306 | 0.09|0.10 | +2.24|-2.15 | 0.53>0.56 | 1.00|0.00 | -0.04|+0.00 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| cusum_adapt|YTD|1m|pooled | +0.02 [-0.52,+0.57] (MDE 0.78) | -0.04 [-1.10,+1.02] (MDE 1.52) | -1.13 (MDE 2.16) | -175|-5,380 | 0.26|0.54 | +5.58|-5.55 | 0.53>0.60 | 0.10|0.00 | -0.62|-0.23 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| cusum_fixed|35|{'X': 2, 'k': 2, 'h': 3} | +0.01 [-0.27,+0.29] (MDE 0.40) | -0.12 [-0.53,+0.29] (MDE 0.58) | -0.00 (MDE 0.94) | +1,299|-6,496 | 0.06|0.06 | +1.54|-1.53 | 0.53>0.55 | nan|0.00 | -0.09|-0.05 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|2w|1d|flip|q0.6|a1 | +0.06 [-0.66,+0.78] (MDE 1.02) | +0.43 [-0.80,+1.66] (MDE 1.76) | -0.93 (MDE 1.90) | +2,789|+24,332 | 0.38|0.49 | +8.62|-8.56 | 0.53>0.65 | nan|0.00 | -0.64|-0.32 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share>60% |
| ogbm|lr0.05|phi0.99|pooled|m8|take | -0.25 [-1.06,+0.56] (MDE 1.16) | -0.59 [-1.81,+0.64] (MDE 1.74) | -1.21 (MDE 2.36) | -15,047|-35,566 | 0.43|0.43 | +11.19|-11.44 | 0.53>0.65 | 0.00|1.00 | -0.89|-0.68 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| rlog|lr0.02|rho0.99|pooled|m8|take | -0.66 [-1.62,+0.29] (MDE 1.36) | -0.88 [-2.33,+0.57] (MDE 2.07) | -1.83 (MDE 2.96) | -39,997|-52,818 | 0.61|0.63 | +15.31|-15.98 | 0.53>0.68 | 0.00|0.00 | -1.57|-1.27 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| rls|lam0.99|perbook|m0|take | -1.13 [-2.31,+0.05] (MDE 1.69) | -1.16 [-2.96,+0.64] (MDE 2.57) | -1.80 (MDE 3.33) | -64,987|-71,247 | 0.84|0.85 | +21.64|-22.76 | 0.53>0.75 | 0.00|0.25 | -2.41|-1.97 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |

Columns: pts/trade over ALL scored trades of the span (cluster-robust CI, MDE = 2.8 SE); $/wk = PRE|HOLD at the book lots; exit = share of trades with an added exit; saved|forfeited = sum of positive|negative paired deltas per trade (PRE); win = base>rule win rate (PRE); plc = placebo ranks (shuffled labels | random exits at the same rate; n/a where the fit uses no labels); N|C = PRE mean without the target correction | with doubled exit friction.

## Top 10 by PRE delta (IN-SAMPLE selection) and what killed each

| cell | PRE | HOLD | X | usd_wk | exit | saved_forf | win | plc | N_C | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| btab|disc0.9995|pooled|z1|m2|take | +0.09 [-0.25,+0.43] (MDE 0.49) | -0.36 [-0.86,+0.14] (MDE 0.71) | -0.83 (MDE 1.57) | +6,023|-20,306 | 0.09|0.10 | +2.24|-2.15 | 0.53>0.56 | 1.00|0.00 | -0.04|+0.00 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|2w|1d|flip|q0.6|a1 | +0.06 [-0.66,+0.78] (MDE 1.02) | +0.43 [-0.80,+1.66] (MDE 1.76) | -0.93 (MDE 1.90) | +2,789|+24,332 | 0.38|0.49 | +8.62|-8.56 | 0.53>0.65 | nan|0.00 | -0.64|-0.32 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share>60% |
| btab|disc0.9995|pooled|z1|m1|take | +0.05 [-0.34,+0.45] (MDE 0.57) | -0.45 [-1.05,+0.14] (MDE 0.85) | -1.12 (MDE 1.72) | +3,530|-23,998 | 0.12|0.14 | +2.95|-2.89 | 0.53>0.57 | 0.90|0.00 | -0.12|-0.06 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|2w|1d|flip|q0.85|a1 | +0.03 [-0.66,+0.73] (MDE 0.99) | +0.34 [-0.87,+1.55] (MDE 1.73) | -1.05 (MDE 1.85) | +1,396|+18,900 | 0.36|0.47 | +8.07|-8.04 | 0.53>0.64 | nan|0.00 | -0.62|-0.32 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| cusum_adapt|YTD|1m|pooled | +0.02 [-0.52,+0.57] (MDE 0.78) | -0.04 [-1.10,+1.02] (MDE 1.52) | -1.13 (MDE 2.16) | -175|-5,380 | 0.26|0.54 | +5.58|-5.55 | 0.53>0.60 | 0.10|0.00 | -0.62|-0.23 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| bocpd_adapt|12m|1m|pooled | +0.02 [-0.17,+0.21] (MDE 0.27) | -0.07 [-0.13,+0.00] (MDE 0.10) | -0.87 (MDE 1.88) | +1,589|-3,829 | 0.04|0.00 | +0.82|-0.80 | 0.53>0.54 | 1.00|0.00 | -0.02|-0.02 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| cusum_adapt|YTD|1w|pooled | +0.01 [-0.53,+0.56] (MDE 0.78) | -0.18 [-1.19,+0.83] (MDE 1.45) | -0.64 (MDE 1.87) | -527|-14,051 | 0.27|0.48 | +5.78|-5.77 | 0.53>0.61 | 0.10|0.00 | -0.64|-0.25 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| cusum_fixed|35|{'X': 2, 'k': 2, 'h': 3} | +0.01 [-0.27,+0.29] (MDE 0.40) | -0.12 [-0.53,+0.29] (MDE 0.58) | -0.00 (MDE 0.94) | +1,299|-6,496 | 0.06|0.06 | +1.54|-1.53 | 0.53>0.55 | nan|0.00 | -0.09|-0.05 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| bocpd_adapt|12m|1d|pooled | +0.00 [-0.19,+0.20] (MDE 0.27) | -0.04 [-0.11,+0.03] (MDE 0.10) | -0.87 (MDE 1.82) | +1,125|-2,199 | 0.04|0.00 | +0.82|-0.82 | 0.53>0.54 | 1.00|0.00 | -0.03|-0.03 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| bocpd_adapt|12m|1w|pooled | +0.00 [-0.19,+0.19] (MDE 0.28) | -0.09 [-0.19,+0.00] (MDE 0.13) | -0.91 (MDE 1.83) | +793|-4,966 | 0.04|0.01 | +0.83|-0.83 | 0.53>0.54 | 0.00|0.00 | -0.04|-0.04 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |

## Top 10 by HOLD delta (selection on the holdout, labelled, not a candidate)

| cell | PRE | HOLD | X | usd_wk | exit | saved_forf | win | plc | N_C | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| hmm|K3|2w|1d|flip|q0.6|a1 | +0.06 [-0.66,+0.78] (MDE 1.02) | +0.43 [-0.80,+1.66] (MDE 1.76) | -0.93 (MDE 1.90) | +2,789|+24,332 | 0.38|0.49 | +8.62|-8.56 | 0.53>0.65 | nan|0.00 | -0.64|-0.32 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share>60% |
| hmm|K3|2w|intraday|flip|q0.6|a1 | -0.01 [-0.73,+0.70] (MDE 1.02) | +0.42 [-0.81,+1.65] (MDE 1.75) | -0.99 (MDE 1.90) | -1,086|+24,004 | 0.38|0.49 | +8.53|-8.54 | 0.53>0.65 | nan|0.00 | -0.71|-0.39 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|1m|intraday|flip|q0.6|a1 | -0.00 [-0.71,+0.71] (MDE 1.01) | +0.41 [-0.81,+1.63] (MDE 1.74) | -0.94 (MDE 1.87) | -497|+24,239 | 0.37|0.48 | +8.40|-8.41 | 0.53>0.64 | nan|0.00 | -0.69|-0.37 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|1m|intraday|flip|q0.85|a1 | -0.12 [-0.81,+0.57] (MDE 0.99) | +0.39 [-0.82,+1.60] (MDE 1.72) | -1.06 (MDE 1.84) | -7,122|+22,421 | 0.35|0.47 | +7.80|-7.93 | 0.53>0.64 | nan|0.00 | -0.77|-0.47 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|2w|1d|flip|q0.85|a1 | +0.03 [-0.66,+0.73] (MDE 0.99) | +0.34 [-0.87,+1.55] (MDE 1.73) | -1.05 (MDE 1.85) | +1,396|+18,900 | 0.36|0.47 | +8.07|-8.04 | 0.53>0.64 | nan|0.00 | -0.62|-0.32 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|2w|1w|flip|q0.6|a1 | -0.02 [-0.74,+0.70] (MDE 1.02) | +0.34 [-0.89,+1.56] (MDE 1.75) | -0.83 (MDE 1.89) | -1,255|+19,361 | 0.38|0.48 | +8.56|-8.58 | 0.53>0.65 | nan|0.00 | -0.72|-0.40 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|1m|1d|flip|q0.85|a1 | -0.11 [-0.80,+0.58] (MDE 0.99) | +0.34 [-0.87,+1.54] (MDE 1.72) | -1.02 (MDE 1.83) | -6,459|+18,852 | 0.35|0.47 | +7.79|-7.90 | 0.53>0.64 | nan|0.00 | -0.75|-0.46 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|1m|1d|flip|q0.6|a1 | -0.06 [-0.77,+0.65] (MDE 1.01) | +0.33 [-0.89,+1.55] (MDE 1.74) | -0.78 (MDE 1.89) | -4,084|+19,344 | 0.37|0.48 | +8.35|-8.41 | 0.53>0.64 | nan|0.00 | -0.74|-0.43 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|2w|intraday|flip|q0.85|a1 | -0.04 [-0.73,+0.65] (MDE 0.99) | +0.31 [-0.90,+1.52] (MDE 1.73) | -1.08 (MDE 1.84) | -3,429|+17,818 | 0.35|0.48 | +7.98|-8.02 | 0.53>0.64 | nan|0.00 | -0.69|-0.39 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| hmm|K3|2w|1m|flip|q0.6|a1 | -0.09 [-0.81,+0.62] (MDE 1.02) | +0.31 [-0.90,+1.51] (MDE 1.72) | -0.81 (MDE 1.90) | -5,089|+18,663 | 0.38|0.48 | +8.45|-8.55 | 0.53>0.64 | nan|0.00 | -0.78|-0.47 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |

## Online learners: PRE chain mean pts/trade by config (forgetting / learning rate) x policy (margin m, take or take+tighten)

| cfg | m0|take | m0|tt | m1|take | m1|tt | m2|take | m2|tt | m4|take | m4|tt | m8|take | m8|tt |
|---|---|---|---|---|---|---|---|---|---|---|
| btab|disc0.998|pooled|z0 | -0.71 | -0.8 | -0.81 | -0.81 | -0.59 | -0.8 | -0.61 | -0.79 | -0.2 | -0.82 |
| btab|disc0.998|pooled|z1 | -0.22 | -0.39 | -0.16 | -0.38 | -0.14 | -0.39 | -0.13 | -0.4 | -0.07 | -0.39 |
| btab|disc0.9995|pooled|z0 | -0.7 | -1.17 | -0.74 | -1.17 | -0.72 | -1.2 | -0.28 | -1.21 | -0.1 | -1.22 |
| btab|disc0.9995|pooled|z1 | -0.07 | -0.21 | 0.05 | -0.21 | 0.09 | -0.22 | -0.12 | -0.21 | -0.02 | -0.21 |
| btab|disc0.99|pooled|z0 | -0.63 | -0.58 | -0.68 | -0.61 | -0.65 | -0.62 | -0.57 | -0.63 | -0.71 | -0.66 |
| btab|disc0.99|pooled|z1 | -0.6 | -0.6 | -0.44 | -0.6 | -0.42 | -0.61 | -0.5 | -0.61 | -0.39 | -0.58 |
| btab|disc1.0|pooled|z0 | -0.75 | -0.95 | -0.61 | -0.98 | -0.51 | -0.98 | -0.3 | -1.0 | -0.01 | -1.01 |
| btab|disc1.0|pooled|z1 | -0.32 | -0.57 | -0.41 | -0.55 | -0.42 | -0.56 | -0.14 | -0.57 | 0.0 | -0.57 |
| ogbm|lr0.05|phi0.999|pooled | -1.11 | -1.15 | -1.05 | -1.15 | -1.05 | -1.15 | -0.86 | -1.17 | -0.8 | -1.16 |
| ogbm|lr0.05|phi0.99|pooled | -0.6 | -0.71 | -0.53 | -0.74 | -0.41 | -0.73 | -0.29 | -0.76 | -0.25 | -0.8 |
| ogbm|lr0.05|phi1.0|pooled | -1.26 | -1.28 | -1.24 | -1.29 | -1.23 | -1.28 | -1.23 | -1.29 | -1.16 | -1.28 |
| ogbm|lr0.2|phi0.999|pooled | -0.84 | -0.77 | -0.81 | -0.78 | -0.75 | -0.77 | -0.69 | -0.77 | -0.62 | -0.79 |
| ogbm|lr0.2|phi0.99|pooled | -0.39 | -0.42 | -0.39 | -0.42 | -0.38 | -0.41 | -0.36 | -0.42 | -0.29 | -0.41 |
| ogbm|lr0.2|phi1.0|pooled | -0.99 | -0.99 | -0.95 | -1.0 | -0.9 | -1.0 | -0.88 | -1.0 | -0.74 | -1.0 |
| rlog|lr0.02|rho0.999|pooled | -1.04 | -1.05 | -1.02 | -1.05 | -1.01 | -1.06 | -0.94 | -1.07 | -0.86 | -1.07 |
| rlog|lr0.02|rho0.99|pooled | -0.87 | -0.9 | -0.84 | -0.91 | -0.79 | -0.91 | -0.84 | -0.91 | -0.66 | -0.9 |
| rlog|lr0.02|rho1.0|pooled | -1.05 | -1.04 | -1.04 | -1.05 | -1.03 | -1.06 | -1.08 | -1.07 | -1.07 | -1.08 |
| rlog|lr0.05|rho0.999|pooled | -1.09 | -1.12 | -1.1 | -1.12 | -1.12 | -1.13 | -1.08 | -1.13 | -1.01 | -1.13 |
| rlog|lr0.05|rho0.99|pooled | -0.77 | -0.82 | -0.77 | -0.82 | -0.78 | -0.83 | -0.77 | -0.83 | -0.84 | -0.85 |
| rlog|lr0.05|rho1.0|pooled | -1.12 | -1.11 | -1.14 | -1.12 | -1.16 | -1.12 | -1.19 | -1.11 | -1.11 | -1.11 |
| rlog|lr0.1|rho0.999|pooled | -1.11 | -1.11 | -1.13 | -1.12 | -1.1 | -1.12 | -1.07 | -1.11 | -1.06 | -1.12 |
| rlog|lr0.1|rho0.99|perbook | -0.86 | -0.85 | -0.85 | -0.85 | -0.84 | -0.85 | -0.81 | -0.86 | -0.81 | -0.87 |
| rlog|lr0.1|rho0.99|pooled | -0.83 | -0.84 | -0.84 | -0.84 | -0.83 | -0.84 | -0.85 | -0.83 | -0.84 | -0.83 |
| rlog|lr0.1|rho1.0|perbook | -0.9 | -0.9 | -0.88 | -0.91 | -0.86 | -0.91 | -0.84 | -0.92 | -0.81 | -0.92 |
| rlog|lr0.1|rho1.0|pooled | -1.14 | -1.15 | -1.16 | -1.16 | -1.16 | -1.16 | -1.12 | -1.16 | -1.14 | -1.17 |
| rlog|lr0.3|rho0.999|pooled | -1.15 | -1.13 | -1.14 | -1.14 | -1.15 | -1.14 | -1.14 | -1.14 | -1.15 | -1.14 |
| rlog|lr0.3|rho0.99|pooled | -1.1 | -1.11 | -1.12 | -1.11 | -1.13 | -1.12 | -1.14 | -1.12 | -1.13 | -1.11 |
| rlog|lr0.3|rho1.0|pooled | -1.22 | -1.21 | -1.22 | -1.21 | -1.22 | -1.21 | -1.21 | -1.21 | -1.23 | -1.21 |
| rls|lam0.995|perbook | -1.28 | -1.26 | -1.25 | -1.27 | -1.26 | -1.27 | -1.21 | -1.27 | -1.18 | -1.29 |
| rls|lam0.995|pooled | -1.28 | -1.29 | -1.28 | -1.29 | -1.27 | -1.29 | -1.32 | -1.3 | -1.3 | -1.29 |
| rls|lam0.998|perbook | -1.29 | -1.3 | -1.29 | -1.3 | -1.26 | -1.3 | -1.26 | -1.31 | -1.25 | -1.32 |
| rls|lam0.998|pooled | -1.29 | -1.29 | -1.26 | -1.29 | -1.25 | -1.29 | -1.23 | -1.28 | -1.21 | -1.3 |
| rls|lam0.9995|perbook | -1.29 | -1.3 | -1.31 | -1.29 | -1.33 | -1.28 | -1.34 | -1.29 | -1.36 | -1.31 |
| rls|lam0.9995|pooled | -1.33 | -1.32 | -1.31 | -1.32 | -1.29 | -1.33 | -1.3 | -1.33 | -1.28 | -1.33 |
| rls|lam0.99|perbook | -1.13 | -1.17 | -1.13 | -1.17 | -1.13 | -1.17 | -1.2 | -1.18 | -1.15 | -1.17 |
| rls|lam0.99|pooled | -1.19 | -1.2 | -1.2 | -1.2 | -1.17 | -1.21 | -1.15 | -1.23 | -1.26 | -1.25 |
| rls|lam1.0|perbook | -1.32 | -1.3 | -1.32 | -1.29 | -1.33 | -1.29 | -1.35 | -1.29 | -1.37 | -1.31 |
| rls|lam1.0|pooled | -1.3 | -1.3 | -1.3 | -1.3 | -1.31 | -1.31 | -1.32 | -1.31 | -1.32 | -1.31 |

Same, HOLD span (all configs shown; none selected on it):

| cfg | m0|take | m0|tt | m1|take | m1|tt | m2|take | m2|tt | m4|take | m4|tt | m8|take | m8|tt |
|---|---|---|---|---|---|---|---|---|---|---|
| btab|disc0.998|pooled|z0 | -0.56 | -0.65 | -0.42 | -0.76 | -0.31 | -0.82 | -0.13 | -0.94 | -0.39 | -0.99 |
| btab|disc0.998|pooled|z1 | -0.42 | -0.33 | -0.41 | -0.35 | -0.49 | -0.35 | -0.45 | -0.36 | -0.3 | -0.39 |
| btab|disc0.9995|pooled|z0 | -0.22 | -0.68 | -0.41 | -0.84 | -0.4 | -0.92 | -0.51 | -1.0 | -0.31 | -1.03 |
| btab|disc0.9995|pooled|z1 | -0.58 | -0.65 | -0.45 | -0.65 | -0.36 | -0.65 | -0.2 | -0.68 | -0.06 | -0.7 |
| btab|disc0.99|pooled|z0 | -0.98 | -0.96 | -0.76 | -0.99 | -0.84 | -1.03 | -0.49 | -1.14 | -0.23 | -1.18 |
| btab|disc0.99|pooled|z1 | -0.34 | -0.43 | -0.34 | -0.43 | -0.43 | -0.46 | -0.29 | -0.47 | 0.06 | -0.5 |
| btab|disc1.0|pooled|z0 | -0.4 | -1.02 | -0.67 | -1.12 | -0.26 | -1.11 | -0.01 | -1.15 | 0.0 | -1.15 |
| btab|disc1.0|pooled|z1 | -0.51 | -0.81 | -0.1 | -0.79 | 0.07 | -0.78 | 0.0 | -0.78 | 0.0 | -0.78 |
| ogbm|lr0.05|phi0.999|pooled | -1.49 | -1.51 | -1.59 | -1.51 | -1.69 | -1.51 | -1.74 | -1.54 | -1.67 | -1.55 |
| ogbm|lr0.05|phi0.99|pooled | -1.12 | -1.38 | -1.08 | -1.37 | -1.11 | -1.37 | -1.1 | -1.39 | -0.59 | -1.5 |
| ogbm|lr0.05|phi1.0|pooled | -1.37 | -1.31 | -1.38 | -1.3 | -1.44 | -1.32 | -1.54 | -1.31 | -1.69 | -1.32 |
| ogbm|lr0.2|phi0.999|pooled | -1.61 | -1.6 | -1.51 | -1.6 | -1.58 | -1.6 | -1.62 | -1.63 | -1.51 | -1.65 |
| ogbm|lr0.2|phi0.99|pooled | -0.91 | -1.03 | -0.8 | -1.04 | -0.8 | -1.04 | -0.64 | -1.07 | -0.6 | -1.08 |
| ogbm|lr0.2|phi1.0|pooled | -1.54 | -1.53 | -1.48 | -1.52 | -1.49 | -1.53 | -1.49 | -1.55 | -1.6 | -1.61 |
| rlog|lr0.02|rho0.999|pooled | -1.62 | -1.56 | -1.64 | -1.58 | -1.67 | -1.58 | -1.85 | -1.6 | -1.84 | -1.59 |
| rlog|lr0.02|rho0.99|pooled | -0.95 | -1.04 | -0.98 | -1.06 | -1.1 | -1.1 | -1.08 | -1.12 | -0.88 | -1.13 |
| rlog|lr0.02|rho1.0|pooled | -1.72 | -1.67 | -1.73 | -1.68 | -1.77 | -1.69 | -1.8 | -1.71 | -1.83 | -1.73 |
| rlog|lr0.05|rho0.999|pooled | -1.7 | -1.68 | -1.71 | -1.68 | -1.73 | -1.69 | -1.77 | -1.69 | -1.72 | -1.7 |
| rlog|lr0.05|rho0.99|pooled | -0.99 | -1.0 | -1.04 | -1.03 | -1.08 | -1.04 | -1.02 | -1.05 | -0.99 | -1.07 |
| rlog|lr0.05|rho1.0|pooled | -1.76 | -1.75 | -1.76 | -1.77 | -1.76 | -1.78 | -1.82 | -1.79 | -1.77 | -1.78 |
| rlog|lr0.1|rho0.999|pooled | -1.58 | -1.55 | -1.57 | -1.56 | -1.58 | -1.57 | -1.59 | -1.58 | -1.55 | -1.57 |
| rlog|lr0.1|rho0.99|perbook | -1.45 | -1.48 | -1.44 | -1.5 | -1.41 | -1.5 | -1.39 | -1.51 | -1.32 | -1.49 |
| rlog|lr0.1|rho0.99|pooled | -1.24 | -1.27 | -1.26 | -1.28 | -1.2 | -1.29 | -1.22 | -1.29 | -1.19 | -1.3 |
| rlog|lr0.1|rho1.0|perbook | -1.33 | -1.33 | -1.36 | -1.34 | -1.36 | -1.34 | -1.34 | -1.34 | -1.39 | -1.36 |
| rlog|lr0.1|rho1.0|pooled | -1.56 | -1.57 | -1.57 | -1.58 | -1.6 | -1.58 | -1.63 | -1.59 | -1.61 | -1.62 |
| rlog|lr0.3|rho0.999|pooled | -1.39 | -1.4 | -1.38 | -1.41 | -1.37 | -1.41 | -1.39 | -1.41 | -1.42 | -1.42 |
| rlog|lr0.3|rho0.99|pooled | -1.15 | -1.12 | -1.15 | -1.14 | -1.15 | -1.15 | -1.13 | -1.14 | -1.12 | -1.15 |
| rlog|lr0.3|rho1.0|pooled | -1.45 | -1.44 | -1.47 | -1.45 | -1.47 | -1.45 | -1.48 | -1.45 | -1.5 | -1.45 |
| rls|lam0.995|perbook | -1.21 | -1.21 | -1.24 | -1.19 | -1.25 | -1.18 | -1.3 | -1.18 | -1.27 | -1.19 |
| rls|lam0.995|pooled | -1.26 | -1.25 | -1.28 | -1.25 | -1.26 | -1.25 | -1.32 | -1.26 | -1.48 | -1.28 |
| rls|lam0.998|perbook | -1.21 | -1.19 | -1.19 | -1.21 | -1.21 | -1.2 | -1.31 | -1.19 | -1.21 | -1.2 |
| rls|lam0.998|pooled | -1.2 | -1.18 | -1.19 | -1.18 | -1.19 | -1.18 | -1.26 | -1.19 | -1.53 | -1.19 |
| rls|lam0.9995|perbook | -1.2 | -1.16 | -1.18 | -1.17 | -1.18 | -1.16 | -1.18 | -1.15 | -1.27 | -1.16 |
| rls|lam0.9995|pooled | -1.16 | -1.17 | -1.19 | -1.18 | -1.2 | -1.19 | -1.24 | -1.19 | -1.36 | -1.18 |
| rls|lam0.99|perbook | -1.16 | -1.17 | -1.18 | -1.17 | -1.19 | -1.16 | -1.21 | -1.18 | -1.23 | -1.19 |
| rls|lam0.99|pooled | -1.32 | -1.29 | -1.31 | -1.3 | -1.36 | -1.31 | -1.37 | -1.31 | -1.35 | -1.3 |
| rls|lam1.0|perbook | -1.14 | -1.13 | -1.15 | -1.13 | -1.13 | -1.13 | -1.17 | -1.13 | -1.24 | -1.15 |
| rls|lam1.0|pooled | -1.14 | -1.11 | -1.13 | -1.12 | -1.13 | -1.12 | -1.16 | -1.13 | -1.29 | -1.15 |

### cusum_adapt: mean over its cells of the PRE chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.506 | nan |
| 2w | -0.458 | -0.59 | -0.602 | -0.624 |
| 1m | nan | nan | nan | -0.579 |
| 3m | -0.31 | -0.363 | -0.42 | -0.294 |
| 6m | -0.302 | -0.357 | -0.258 | -0.291 |
| 12m | -0.292 | -0.31 | -0.308 | -0.283 |
| YTD | -0.165 | -0.171 | -0.137 | -0.123 |
| ew5 | -0.375 | -0.548 | -0.612 | -0.514 |
| ew10 | -0.549 | -0.551 | -0.611 | -0.342 |
| ew20 | -0.366 | -0.477 | -0.464 | -0.343 |

### cusum_adapt: mean over its cells of the HOLD chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.436 | nan |
| 2w | -0.346 | -0.514 | -0.601 | -0.396 |
| 1m | nan | nan | nan | -0.511 |
| 3m | -0.525 | -0.604 | -0.458 | -0.458 |
| 6m | -0.531 | -0.561 | -0.25 | -0.192 |
| 12m | -0.14 | -0.054 | -0.057 | -0.071 |
| YTD | -0.151 | -0.177 | -0.271 | -0.065 |
| ew5 | -0.22 | -0.166 | -0.639 | -0.234 |
| ew10 | -0.392 | -0.373 | -0.614 | -0.295 |
| ew20 | -0.431 | -0.411 | -0.53 | -0.397 |

### bocpd_adapt: mean over its cells of the PRE chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.478 | nan |
| 2w | -0.593 | -0.623 | -0.531 | -0.399 |
| 1m | nan | nan | nan | -0.371 |
| 3m | -0.397 | -0.407 | -0.422 | -0.46 |
| 6m | -0.15 | -0.178 | -0.217 | -0.186 |
| 12m | -0.121 | -0.126 | -0.139 | -0.11 |
| YTD | -0.217 | -0.224 | -0.268 | -0.237 |
| ew5 | -0.644 | -0.666 | -0.559 | -0.335 |
| ew10 | -0.533 | -0.582 | -0.51 | -0.349 |
| ew20 | -0.475 | -0.482 | -0.386 | -0.334 |

### bocpd_adapt: mean over its cells of the HOLD chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.495 | nan |
| 2w | -0.634 | -0.658 | -0.613 | -0.508 |
| 1m | nan | nan | nan | -0.451 |
| 3m | -0.625 | -0.632 | -0.705 | -0.382 |
| 6m | -0.54 | -0.513 | -0.45 | -0.416 |
| 12m | -0.33 | -0.33 | -0.325 | -0.275 |
| YTD | -0.396 | -0.389 | -0.542 | -0.438 |
| ew5 | -0.458 | -0.438 | -0.64 | -0.362 |
| ew10 | -0.448 | -0.51 | -0.736 | -0.597 |
| ew20 | -0.495 | -0.49 | -0.676 | -0.519 |

### hmm: mean over its cells of the PRE chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.624 | nan |
| 2w | -0.573 | -0.536 | -0.577 | -0.591 |
| 1m | nan | nan | nan | -0.602 |
| 3m | -0.619 | -0.633 | -0.621 | -0.631 |
| 6m | -0.64 | -0.65 | -0.643 | -0.664 |
| 12m | -0.644 | -0.663 | -0.656 | -0.66 |
| YTD | -0.619 | -0.614 | -0.619 | -0.664 |
| ew5 | -0.842 | -0.842 | -0.841 | -0.833 |
| ew10 | -0.834 | -0.834 | -0.833 | -0.822 |
| ew20 | -0.832 | -0.829 | -0.836 | -0.833 |

### hmm: mean over its cells of the HOLD chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.293 | nan |
| 2w | -0.314 | -0.308 | -0.34 | -0.34 |
| 1m | nan | nan | nan | -0.353 |
| 3m | -0.487 | -0.513 | -0.476 | -0.457 |
| 6m | -0.48 | -0.485 | -0.505 | -0.487 |
| 12m | -0.496 | -0.496 | -0.524 | -0.479 |
| YTD | -0.466 | -0.502 | -0.484 | -0.459 |
| ew5 | -0.578 | -0.578 | -0.572 | -0.6 |
| ew10 | -0.578 | -0.579 | -0.584 | -0.629 |
| ew20 | -0.58 | -0.583 | -0.593 | -0.602 |

## Breakdown: btab|disc0.9995|pooled|z1|m2|take

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | +0.14 | -0.43..+0.70 | 0.81 | +1,102 | 0.08 |
| HM | 2285 | -0.01 | -0.72..+0.70 | 1.01 | -55 | 0.10 |
| WT | 4265 | +0.04 | -0.20..+0.27 | 0.33 | +301 | 0.05 |
| KB | 3093 | +0.03 | -0.56..+0.62 | 0.84 | +125 | 0.09 |
| SM | 904 | -0.11 | -1.40..+1.18 | 1.84 | -194 | 0.12 |
| PE | 3049 | -0.07 | -0.65..+0.52 | 0.84 | -297 | 0.09 |
| PB | 2261 | +0.16 | -0.56..+0.87 | 1.03 | +935 | 0.10 |
| DN | 1762 | +0.26 | -0.58..+1.09 | 1.19 | +1,201 | 0.10 |
| MV | 2922 | +0.36 | -0.24..+0.96 | 0.86 | +2,815 | 0.09 |
| MA | 1093 | +0.03 | -1.11..+1.17 | 1.63 | +92 | 0.12 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.15 | -0.63..+0.93 | 1.12 | +1,300 | 0.09 |
| HM | 1008 | -0.58 | -1.56..+0.39 | 1.39 | -3,668 | 0.11 |
| WT | 1893 | +0.10 | -0.30..+0.49 | 0.57 | +802 | 0.07 |
| KB | 1374 | -0.42 | -1.18..+0.35 | 1.10 | -1,859 | 0.09 |
| SM | 363 | -0.70 | -2.87..+1.47 | 3.10 | -1,172 | 0.16 |
| PE | 1311 | -0.55 | -1.45..+0.34 | 1.28 | -2,543 | 0.11 |
| PB | 965 | -1.30 | -2.35..-0.24 | 1.50 | -7,819 | 0.12 |
| DN | 782 | -0.27 | -1.44..+0.89 | 1.66 | -1,335 | 0.11 |
| MV | 1253 | -0.41 | -1.26..+0.44 | 1.21 | -3,177 | 0.10 |
| MA | 474 | -0.28 | -1.89..+1.33 | 2.30 | -836 | 0.14 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -0.67 | -2.68..+1.34 | 2.87 | -2,232 | 0.28 |
| HM | 621 | -0.58 | -2.71..+1.54 | 3.03 | -1,683 | 0.28 |
| WT | 1112 | -1.12 | -1.84..-0.40 | 1.03 | -4,056 | 0.16 |
| KB | 765 | -0.65 | -2.60..+1.29 | 2.78 | -1,208 | 0.28 |
| SM | 320 | -0.21 | -3.28..+2.86 | 4.38 | -229 | 0.30 |
| PE | 727 | -0.71 | -2.71..+1.29 | 2.85 | -1,348 | 0.27 |
| PB | 595 | -1.71 | -3.94..+0.53 | 3.19 | -4,730 | 0.30 |
| DN | 530 | -0.79 | -3.16..+1.58 | 3.38 | -1,940 | 0.28 |
| MV | 732 | -0.65 | -2.58..+1.28 | 2.75 | -2,203 | 0.27 |
| MA | 368 | -0.88 | -3.85..+2.10 | 4.25 | -1,501 | 0.31 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.59 | -1.62..+0.45 | 1.48 | -7,160 | 0.21 |
| london | 5303 | +0.41 | -0.41..+1.23 | 1.18 | +4,808 | 0.10 |
| pre | 1479 | +0.10 | -0.25..+0.44 | 0.50 | +290 | 0.01 |
| nyam | 6580 | +0.42 | +0.07..+0.77 | 0.50 | +6,372 | 0.03 |
| nypm | 4901 | +0.17 | -0.16..+0.50 | 0.48 | +1,690 | 0.04 |
| close | 72 | +0.17 | -0.16..+0.49 | 0.46 | +24 | 0.01 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | -0.49 | -1.91..+0.92 | 2.02 | -7,363 | 0.19 |
| london | 2243 | -0.46 | -1.46..+0.53 | 1.42 | -6,603 | 0.11 |
| pre | 540 | +0.68 | -0.13..+1.49 | 1.16 | +2,408 | 0.02 |
| nyam | 3095 | -0.26 | -0.90..+0.39 | 0.92 | -3,757 | 0.05 |
| nypm | 1898 | -0.47 | -1.21..+0.27 | 1.06 | -4,999 | 0.06 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.744 | -4066.901 |
| 2024.0 | 14562.0 | -0.151 | -2200.5 |
| 2025.0 | 19687.0 | -0.072 | -1419.034 |
| 2026.0 | 2229.0 | 0.3 | 668.34 |
**drift: monthly mean pts/trade** 202307:-2.78 202308:+0.44 202309:-1.03 202310:-0.63 202311:+0.84 202312:-1.85 202401:-1.31 202402:+0.00 202403:-0.19 202404:-0.34 202405:+0.18 202406:+1.12 202407:+0.12 202408:+0.07 202409:-0.02 202410:-0.59 202411:+0.03 202412:-0.85 202501:-0.05 202502:-0.30 202503:+0.06 202504:+0.53 202505:-0.08 202506:+1.51 202507:-0.82 202508:-1.76 202509:-0.00 202510:-0.28 202511:-0.05 202512:-0.65 202601:+0.42 202602:+0.01

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +0.73 | -0.50..+1.97 | 1.76 | +10,011 | 0.15 |
| 1 | 2264 | -0.73 | -2.11..+0.65 | 1.97 | -7,524 | 0.14 |
| 2 | 5854 | -0.71 | -1.21..-0.22 | 0.71 | -22,792 | 0.07 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | -1.17 | -2.52..+0.18 | 1.93 | -3,507 | 0.12 |
| VIX_mid | 6933 | -0.21 | -0.93..+0.51 | 1.03 | -6,992 | 0.13 |
| VIX_high | 3307 | -0.53 | -1.11..+0.05 | 0.83 | -9,807 | 0.03 |

## Breakdown: hmm|K3|2w|1d|flip|q0.6|a1

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | +0.20 | -0.99..+1.39 | 1.70 | +1,600 | 0.37 |
| HM | 2285 | +0.53 | -0.90..+1.97 | 2.05 | +3,235 | 0.42 |
| WT | 4265 | +0.22 | -0.27..+0.71 | 0.70 | +1,763 | 0.30 |
| KB | 3093 | -0.06 | -1.16..+1.05 | 1.58 | -244 | 0.37 |
| SM | 904 | -1.22 | -3.56..+1.12 | 3.34 | -2,178 | 0.45 |
| PE | 3049 | +0.39 | -0.79..+1.57 | 1.69 | +1,754 | 0.39 |
| PB | 2261 | +0.04 | -1.43..+1.50 | 2.09 | +235 | 0.45 |
| DN | 1762 | -0.62 | -2.22..+0.98 | 2.29 | -2,919 | 0.39 |
| MV | 2922 | +0.23 | -0.95..+1.41 | 1.68 | +1,769 | 0.37 |
| MA | 1093 | -0.76 | -2.85..+1.32 | 2.98 | -2,226 | 0.46 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.76 | -1.17..+2.69 | 2.76 | +6,549 | 0.51 |
| HM | 1008 | +1.08 | -1.31..+3.46 | 3.40 | +6,780 | 0.54 |
| WT | 1893 | +1.03 | +0.17..+1.89 | 1.22 | +8,531 | 0.38 |
| KB | 1374 | -0.32 | -2.26..+1.63 | 2.78 | -1,413 | 0.48 |
| SM | 363 | +2.22 | -1.83..+6.26 | 5.78 | +3,722 | 0.55 |
| PE | 1311 | +0.31 | -1.63..+2.25 | 2.77 | +1,420 | 0.51 |
| PB | 965 | -1.20 | -3.75..+1.36 | 3.65 | -7,223 | 0.55 |
| DN | 782 | +1.21 | -1.52..+3.95 | 3.91 | +5,933 | 0.51 |
| MV | 1253 | +0.35 | -1.74..+2.44 | 2.99 | +2,777 | 0.49 |
| MA | 474 | -0.93 | -4.49..+2.64 | 5.09 | -2,743 | 0.53 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -1.17 | -3.40..+1.05 | 3.18 | -3,910 | 0.38 |
| HM | 621 | -1.22 | -3.64..+1.21 | 3.47 | -3,513 | 0.40 |
| WT | 1112 | -0.57 | -1.52..+0.37 | 1.35 | -2,067 | 0.29 |
| KB | 765 | -0.42 | -2.57..+1.72 | 3.07 | -781 | 0.35 |
| SM | 320 | -1.00 | -4.91..+2.92 | 5.59 | -1,096 | 0.47 |
| PE | 727 | -1.35 | -3.46..+0.77 | 3.02 | -2,554 | 0.37 |
| PB | 595 | -1.37 | -3.93..+1.19 | 3.65 | -3,798 | 0.40 |
| DN | 530 | -2.02 | -4.81..+0.76 | 3.98 | -4,983 | 0.40 |
| MV | 732 | -0.32 | -2.60..+1.97 | 3.27 | -1,081 | 0.37 |
| MA | 368 | -0.22 | -3.87..+3.43 | 5.22 | -377 | 0.47 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.97 | -2.98..+1.03 | 2.86 | -13,234 | 0.70 |
| london | 5303 | +0.10 | -1.93..+2.14 | 2.91 | +645 | 0.60 |
| pre | 1479 | -0.20 | -2.34..+1.93 | 3.05 | -1,297 | 0.23 |
| nyam | 6580 | +0.60 | +0.10..+1.09 | 0.71 | +8,042 | 0.08 |
| nypm | 4901 | +0.70 | -0.01..+1.41 | 1.01 | +8,651 | 0.18 |
| close | 72 | -0.09 | -0.58..+0.39 | 0.69 | -18 | 0.10 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | +0.35 | -2.69..+3.38 | 4.34 | +5,895 | 0.73 |
| london | 2243 | -1.39 | -4.52..+1.73 | 4.47 | -17,883 | 0.66 |
| pre | 540 | +3.92 | -1.10..+8.95 | 7.18 | +11,206 | 0.41 |
| nyam | 3095 | +0.50 | -0.91..+1.90 | 2.01 | +7,006 | 0.26 |
| nypm | 1898 | +1.61 | -0.60..+3.83 | 3.16 | +17,946 | 0.31 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.528 | -2886.433 |
| 2024.0 | 14562.0 | -0.226 | -3297.904 |
| 2025.0 | 19687.0 | 0.307 | 6053.195 |
| 2026.0 | 2229.0 | 0.094 | 208.47 |
**drift: monthly mean pts/trade** 202307:-1.57 202308:+0.98 202309:-0.05 202310:-1.27 202311:-0.11 202312:-1.75 202401:-3.11 202402:-0.32 202403:+0.48 202404:+1.52 202405:+0.43 202406:+0.41 202407:-1.16 202408:-0.19 202409:+0.58 202410:+0.17 202411:+0.87 202412:-2.46 202501:-0.60 202502:+1.50 202503:-0.79 202504:-0.27 202505:+1.05 202506:+0.93 202507:+1.67 202508:-0.79 202509:+0.37 202510:+0.52 202511:+0.54 202512:+0.84 202601:-0.41 202602:+1.35

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +2.49 | +0.25..+4.73 | 3.20 | +36,779 | 0.46 |
| 1 | 2264 | +0.99 | -1.61..+3.60 | 3.72 | +14,078 | 0.50 |
| 2 | 5854 | -0.73 | -2.47..+1.01 | 2.49 | -26,525 | 0.50 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | -1.39 | -7.68..+4.90 | 8.99 | -3,941 | 0.61 |
| VIX_mid | 6933 | -0.04 | -1.58..+1.50 | 2.20 | +2,322 | 0.49 |
| VIX_high | 3307 | +1.72 | -0.39..+3.84 | 3.02 | +25,951 | 0.47 |

## Breakdown: btab|disc0.9995|pooled|z1|m1|take

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | +0.42 | -0.25..+1.09 | 0.96 | +3,358 | 0.11 |
| HM | 2285 | -0.22 | -1.01..+0.58 | 1.14 | -1,324 | 0.13 |
| WT | 4265 | +0.03 | -0.25..+0.31 | 0.40 | +228 | 0.07 |
| KB | 3093 | -0.06 | -0.74..+0.62 | 0.97 | -251 | 0.12 |
| SM | 904 | -0.42 | -1.89..+1.05 | 2.10 | -747 | 0.16 |
| PE | 3049 | +0.11 | -0.56..+0.79 | 0.96 | +513 | 0.12 |
| PB | 2261 | +0.04 | -0.79..+0.87 | 1.18 | +243 | 0.14 |
| DN | 1762 | +0.20 | -0.77..+1.17 | 1.39 | +922 | 0.14 |
| MV | 2922 | +0.14 | -0.55..+0.83 | 0.98 | +1,108 | 0.13 |
| MA | 1093 | -0.18 | -1.47..+1.11 | 1.84 | -520 | 0.16 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.11 | -0.81..+1.03 | 1.32 | +955 | 0.13 |
| HM | 1008 | -0.26 | -1.41..+0.90 | 1.65 | -1,621 | 0.16 |
| WT | 1893 | +0.37 | -0.10..+0.84 | 0.68 | +3,070 | 0.09 |
| KB | 1374 | -0.82 | -1.75..+0.10 | 1.32 | -3,670 | 0.13 |
| SM | 363 | -1.64 | -3.99..+0.70 | 3.35 | -2,761 | 0.19 |
| PE | 1311 | -0.98 | -2.00..+0.04 | 1.45 | -4,493 | 0.14 |
| PB | 965 | -1.32 | -2.54..-0.10 | 1.74 | -7,947 | 0.16 |
| DN | 782 | -0.13 | -1.50..+1.23 | 1.94 | -654 | 0.15 |
| MV | 1253 | -0.30 | -1.33..+0.73 | 1.47 | -2,338 | 0.15 |
| MA | 474 | -1.53 | -3.27..+0.20 | 2.48 | -4,538 | 0.18 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -1.25 | -3.39..+0.90 | 3.06 | -4,154 | 0.32 |
| HM | 621 | -1.06 | -3.31..+1.19 | 3.22 | -3,070 | 0.31 |
| WT | 1112 | -0.93 | -1.75..-0.12 | 1.17 | -3,379 | 0.20 |
| KB | 765 | -0.75 | -2.81..+1.32 | 2.95 | -1,378 | 0.30 |
| SM | 320 | -0.64 | -3.96..+2.67 | 4.73 | -708 | 0.34 |
| PE | 727 | -1.47 | -3.55..+0.62 | 2.98 | -2,778 | 0.31 |
| PB | 595 | -1.85 | -4.27..+0.58 | 3.46 | -5,110 | 0.35 |
| DN | 530 | -1.24 | -3.82..+1.34 | 3.69 | -3,054 | 0.34 |
| MV | 732 | -0.96 | -3.06..+1.14 | 3.00 | -3,274 | 0.31 |
| MA | 368 | -0.93 | -4.12..+2.27 | 4.56 | -1,584 | 0.36 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.49 | -1.71..+0.72 | 1.74 | -6,519 | 0.27 |
| london | 5303 | +0.20 | -0.75..+1.16 | 1.36 | +2,078 | 0.13 |
| pre | 1479 | +0.09 | -0.36..+0.54 | 0.64 | +509 | 0.02 |
| nyam | 6580 | +0.30 | -0.11..+0.71 | 0.59 | +4,682 | 0.04 |
| nypm | 4901 | +0.26 | -0.17..+0.68 | 0.61 | +2,758 | 0.05 |
| close | 72 | +0.17 | -0.16..+0.49 | 0.46 | +24 | 0.01 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | -0.75 | -2.38..+0.87 | 2.32 | -10,999 | 0.25 |
| london | 2243 | -1.13 | -2.40..+0.14 | 1.82 | -13,427 | 0.15 |
| pre | 540 | +1.40 | -0.56..+3.36 | 2.80 | +4,335 | 0.04 |
| nyam | 3095 | -0.08 | -0.77..+0.62 | 1.00 | -179 | 0.07 |
| nypm | 1898 | -0.32 | -1.26..+0.62 | 1.34 | -3,666 | 0.09 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.983 | -5377.571 |
| 2024.0 | 14562.0 | -0.275 | -4003.225 |
| 2025.0 | 19687.0 | -0.035 | -682.849 |
| 2026.0 | 2229.0 | -0.329 | -734.14 |
**drift: monthly mean pts/trade** 202307:-3.15 202308:+0.10 202309:-0.78 202310:-1.44 202311:+1.37 202312:-2.20 202401:-1.82 202402:+0.71 202403:+0.66 202404:-0.25 202405:+0.07 202406:+0.67 202407:-0.70 202408:-0.19 202409:-0.29 202410:-0.60 202411:+0.04 202412:-0.99 202501:-0.10 202502:-0.03 202503:-0.24 202504:+0.68 202505:+0.09 202506:+1.49 202507:+0.43 202508:-2.39 202509:+0.30 202510:-0.39 202511:-0.07 202512:-0.86 202601:-0.16 202602:-0.76

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +0.86 | -0.47..+2.20 | 1.90 | +12,684 | 0.18 |
| 1 | 2264 | -1.19 | -2.82..+0.43 | 2.32 | -11,871 | 0.18 |
| 2 | 5854 | -0.77 | -1.42..-0.12 | 0.93 | -24,811 | 0.10 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | -0.93 | -2.89..+1.04 | 2.81 | -2,589 | 0.16 |
| VIX_mid | 6933 | -0.36 | -1.21..+0.49 | 1.21 | -11,046 | 0.18 |
| VIX_high | 3307 | -0.57 | -1.25..+0.11 | 0.97 | -10,364 | 0.05 |

## Breakdown: bocpd_adapt|12m|1m|pooled

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | +0.11 | -0.26..+0.47 | 0.53 | +851 | 0.04 |
| HM | 2285 | -0.06 | -0.48..+0.36 | 0.60 | -394 | 0.05 |
| WT | 4265 | +0.06 | -0.02..+0.15 | 0.12 | +511 | 0.01 |
| KB | 3093 | -0.13 | -0.48..+0.22 | 0.50 | -548 | 0.04 |
| SM | 904 | +0.25 | -0.58..+1.09 | 1.19 | +451 | 0.06 |
| PE | 3049 | -0.10 | -0.44..+0.25 | 0.49 | -442 | 0.04 |
| PB | 2261 | +0.32 | -0.15..+0.79 | 0.67 | +1,911 | 0.05 |
| DN | 1762 | +0.08 | -0.44..+0.60 | 0.74 | +383 | 0.05 |
| MV | 2922 | -0.03 | -0.38..+0.31 | 0.49 | -270 | 0.04 |
| MA | 1093 | -0.30 | -0.87..+0.28 | 0.82 | -865 | 0.05 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | -0.13 | -0.26..+0.00 | 0.19 | -1,110 | 0.00 |
| HM | 1008 | -0.14 | -0.29..+0.00 | 0.21 | -895 | 0.00 |
| WT | 1893 | -0.02 | -0.05..+0.02 | 0.04 | -132 | 0.00 |
| KB | 1374 | -0.04 | -0.19..+0.10 | 0.21 | -197 | 0.00 |
| SM | 363 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| PE | 1311 | -0.13 | -0.32..+0.07 | 0.28 | -583 | 0.01 |
| PB | 965 | -0.02 | -0.05..+0.02 | 0.05 | -101 | 0.00 |
| DN | 782 | -0.09 | -0.20..+0.03 | 0.17 | -418 | 0.00 |
| MV | 1253 | -0.01 | -0.17..+0.15 | 0.23 | -104 | 0.00 |
| MA | 474 | -0.10 | -0.29..+0.09 | 0.27 | -289 | 0.00 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -1.52 | -3.87..+0.83 | 3.36 | -5,066 | 0.43 |
| HM | 621 | -0.46 | -2.96..+2.05 | 3.58 | -1,318 | 0.43 |
| WT | 1112 | -0.53 | -1.26..+0.20 | 1.04 | -1,927 | 0.16 |
| KB | 765 | -0.22 | -2.57..+2.13 | 3.36 | -406 | 0.41 |
| SM | 320 | -0.93 | -4.77..+2.92 | 5.49 | -1,023 | 0.48 |
| PE | 727 | -0.67 | -3.11..+1.76 | 3.48 | -1,274 | 0.45 |
| PB | 595 | -2.83 | -5.41..-0.26 | 3.68 | -7,839 | 0.42 |
| DN | 530 | -1.08 | -4.04..+1.87 | 4.22 | -2,674 | 0.46 |
| MV | 732 | -0.04 | -2.40..+2.31 | 3.36 | -141 | 0.41 |
| MA | 368 | -1.18 | -4.41..+2.04 | 4.61 | -2,024 | 0.44 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | +0.06 | -0.47..+0.59 | 0.76 | +1,506 | 0.07 |
| london | 5303 | +0.01 | -0.32..+0.34 | 0.48 | -395 | 0.03 |
| pre | 1479 | +0.76 | -0.08..+1.59 | 1.19 | +2,582 | 0.02 |
| nyam | 6580 | -0.06 | -0.34..+0.22 | 0.40 | -594 | 0.02 |
| nypm | 4901 | -0.17 | -0.52..+0.17 | 0.49 | -1,796 | 0.04 |
| close | 72 | +1.49 | -0.60..+3.59 | 2.99 | +287 | 0.06 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | -0.12 | -0.32..+0.09 | 0.30 | -1,799 | 0.01 |
| london | 2243 | -0.13 | -0.29..+0.02 | 0.22 | -1,779 | 0.00 |
| pre | 540 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| nyam | 3095 | -0.02 | -0.07..+0.02 | 0.07 | -251 | 0.00 |
| nypm | 1898 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.666 | -3643.986 |
| 2024.0 | 14562.0 | -0.109 | -1582.75 |
| 2025.0 | 19687.0 | 0.0 | 0.0 |
| 2026.0 | 2229.0 | -0.325 | -724.08 |
**drift: monthly mean pts/trade** 202307:-2.74 202308:+1.24 202309:-0.07 202310:-1.70 202311:+0.15 202312:-1.36 202401:-1.96 202402:+0.12 202403:+0.96 202404:+1.22 202405:-0.72 202406:-1.61 202407:+0.00 202408:+0.00 202409:+0.00 202410:+0.00 202411:+0.00 202412:+0.00 202501:+0.00 202502:+0.00 202503:+0.00 202504:+0.00 202505:+0.00 202506:+0.00 202507:+0.00 202508:+0.00 202509:+0.00 202510:+0.00 202511:+0.00 202512:+0.00 202601:+0.00 202602:-1.14

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | -0.03 | -0.09..+0.04 | 0.10 | -424 | 0.00 |
| 1 | 2264 | -0.20 | -0.50..+0.10 | 0.42 | -2,393 | 0.01 |
| 2 | 5854 | -0.03 | -0.07..+0.00 | 0.06 | -1,012 | 0.00 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| VIX_mid | 6933 | -0.02 | -0.05..+0.01 | 0.04 | -720 | 0.00 |
| VIX_high | 3307 | -0.18 | -0.39..+0.03 | 0.30 | -3,109 | 0.01 |

## Breakdown: bocpd_fixed|17|{'hz': 1, 'p': 2, 'X': 2}

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | -0.29 | -0.81..+0.22 | 0.74 | -2,366 | 0.09 |
| HM | 2285 | -0.23 | -0.88..+0.43 | 0.94 | -1,374 | 0.11 |
| WT | 4265 | +0.03 | -0.08..+0.13 | 0.15 | +210 | 0.01 |
| KB | 3093 | -0.20 | -0.74..+0.34 | 0.77 | -840 | 0.09 |
| SM | 904 | -0.37 | -1.54..+0.80 | 1.67 | -658 | 0.13 |
| PE | 3049 | -0.29 | -0.82..+0.25 | 0.77 | -1,312 | 0.09 |
| PB | 2261 | +0.09 | -0.61..+0.78 | 0.99 | +525 | 0.10 |
| DN | 1762 | +0.14 | -0.61..+0.88 | 1.07 | +638 | 0.10 |
| MV | 2922 | -0.16 | -0.73..+0.40 | 0.80 | -1,273 | 0.10 |
| MA | 1093 | -1.55 | -2.46..-0.64 | 1.30 | -4,518 | 0.11 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | -0.06 | -0.86..+0.74 | 1.14 | -513 | 0.09 |
| HM | 1008 | -0.53 | -1.48..+0.42 | 1.36 | -3,355 | 0.11 |
| WT | 1893 | -0.07 | -0.20..+0.05 | 0.17 | -613 | 0.01 |
| KB | 1374 | -0.26 | -1.02..+0.50 | 1.09 | -1,160 | 0.09 |
| SM | 363 | +1.32 | -0.68..+3.33 | 2.86 | +2,221 | 0.12 |
| PE | 1311 | -0.21 | -1.11..+0.68 | 1.27 | -984 | 0.11 |
| PB | 965 | +0.07 | -1.05..+1.19 | 1.60 | +431 | 0.12 |
| DN | 782 | -0.42 | -1.45..+0.60 | 1.47 | -2,070 | 0.09 |
| MV | 1253 | -0.16 | -0.98..+0.66 | 1.18 | -1,242 | 0.09 |
| MA | 474 | -1.54 | -3.01..-0.08 | 2.09 | -4,564 | 0.13 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -0.36 | -1.67..+0.95 | 1.87 | -1,208 | 0.15 |
| HM | 621 | +0.52 | -1.07..+2.11 | 2.27 | +1,497 | 0.17 |
| WT | 1112 | +0.03 | -0.20..+0.26 | 0.33 | +107 | 0.01 |
| KB | 765 | -0.22 | -1.46..+1.01 | 1.77 | -415 | 0.15 |
| SM | 320 | -0.79 | -2.94..+1.36 | 3.08 | -871 | 0.17 |
| PE | 727 | -0.53 | -1.97..+0.92 | 2.06 | -995 | 0.16 |
| PB | 595 | -0.62 | -2.16..+0.93 | 2.21 | -1,710 | 0.16 |
| DN | 530 | -0.62 | -2.10..+0.86 | 2.12 | -1,530 | 0.14 |
| MV | 732 | -0.15 | -1.45..+1.14 | 1.85 | -526 | 0.14 |
| MA | 368 | +0.08 | -1.89..+2.05 | 2.82 | +137 | 0.16 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.51 | -1.37..+0.35 | 1.23 | -6,460 | 0.17 |
| london | 5303 | -0.33 | -0.94..+0.27 | 0.86 | -4,635 | 0.08 |
| pre | 1479 | +0.00 | -0.81..+0.82 | 1.17 | +4 | 0.04 |
| nyam | 6580 | -0.07 | -0.40..+0.26 | 0.47 | -942 | 0.03 |
| nypm | 4901 | +0.11 | -0.30..+0.51 | 0.58 | +954 | 0.05 |
| close | 72 | +0.77 | -1.82..+3.37 | 3.70 | +111 | 0.06 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | +0.29 | -1.10..+1.69 | 2.00 | +3,639 | 0.17 |
| london | 2243 | -0.75 | -1.64..+0.14 | 1.27 | -9,572 | 0.10 |
| pre | 540 | +0.13 | -0.37..+0.62 | 0.71 | +532 | 0.02 |
| nyam | 3095 | -0.29 | -0.62..+0.03 | 0.47 | -4,418 | 0.03 |
| nypm | 1898 | -0.24 | -0.68..+0.20 | 0.63 | -2,028 | 0.05 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.002 | -9.13 |
| 2024.0 | 14562.0 | -0.432 | -6293.595 |
| 2025.0 | 19687.0 | -0.098 | -1931.239 |
| 2026.0 | 2229.0 | -0.094 | -208.995 |
**drift: monthly mean pts/trade** 202307:+0.89 202308:+0.35 202309:-0.18 202310:-1.09 202311:+0.73 202312:-0.35 202401:-1.46 202402:-0.21 202403:-0.17 202404:-0.23 202405:+0.16 202406:-0.61 202407:-1.11 202408:+0.21 202409:-0.42 202410:-0.30 202411:+0.03 202412:-1.27 202501:-1.04 202502:+0.46 202503:+0.21 202504:+0.10 202505:-0.31 202506:+0.62 202507:-0.23 202508:-1.38 202509:+0.38 202510:+0.46 202511:-0.49 202512:-0.09 202601:+0.32 202602:-1.14

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +0.37 | -0.63..+1.36 | 1.42 | +4,220 | 0.12 |
| 1 | 2264 | -0.32 | -1.45..+0.81 | 1.62 | -3,266 | 0.11 |
| 2 | 5854 | -0.40 | -0.94..+0.13 | 0.76 | -12,802 | 0.06 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | +0.02 | -2.19..+2.23 | 3.16 | -136 | 0.13 |
| VIX_mid | 6933 | -0.25 | -0.83..+0.33 | 0.83 | -9,138 | 0.09 |
| VIX_high | 3307 | -0.12 | -0.83..+0.60 | 1.02 | -2,574 | 0.06 |

## Breakdown: cusum_adapt|YTD|1m|pooled

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | +0.26 | -0.77..+1.28 | 1.46 | +2,088 | 0.28 |
| HM | 2285 | -0.18 | -1.27..+0.90 | 1.55 | -1,119 | 0.29 |
| WT | 4265 | +0.30 | -0.01..+0.61 | 0.45 | +2,394 | 0.12 |
| KB | 3093 | +0.27 | -0.70..+1.24 | 1.39 | +1,155 | 0.29 |
| SM | 904 | +0.72 | -1.14..+2.58 | 2.66 | +1,285 | 0.30 |
| PE | 3049 | -0.21 | -1.16..+0.73 | 1.35 | -965 | 0.27 |
| PB | 2261 | -0.19 | -1.33..+0.94 | 1.63 | -1,171 | 0.30 |
| DN | 1762 | -0.98 | -2.27..+0.32 | 1.85 | -4,594 | 0.30 |
| MV | 2922 | -0.01 | -1.01..+0.99 | 1.43 | -82 | 0.28 |
| MA | 1093 | +0.29 | -1.35..+1.93 | 2.34 | +835 | 0.28 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.52 | -1.44..+2.48 | 2.80 | +4,461 | 0.60 |
| HM | 1008 | -1.14 | -3.34..+1.05 | 3.14 | -7,191 | 0.59 |
| WT | 1893 | +0.45 | +0.01..+0.89 | 0.63 | +3,724 | 0.22 |
| KB | 1374 | +0.27 | -1.60..+2.14 | 2.67 | +1,203 | 0.59 |
| SM | 363 | +1.06 | -3.10..+5.21 | 5.94 | +1,773 | 0.64 |
| PE | 1311 | -0.24 | -2.07..+1.59 | 2.61 | -1,098 | 0.58 |
| PB | 965 | -0.22 | -2.63..+2.19 | 3.45 | -1,326 | 0.64 |
| DN | 782 | +0.85 | -1.88..+3.57 | 3.89 | +4,140 | 0.63 |
| MV | 1253 | -0.14 | -2.17..+1.89 | 2.90 | -1,105 | 0.58 |
| MA | 474 | -3.36 | -6.64..-0.09 | 4.68 | -9,962 | 0.64 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -3.02 | -5.79..-0.25 | 3.96 | -10,070 | 0.59 |
| HM | 621 | -0.48 | -3.57..+2.62 | 4.42 | -1,380 | 0.61 |
| WT | 1112 | -0.90 | -1.78..-0.02 | 1.26 | -3,246 | 0.27 |
| KB | 765 | +0.03 | -2.77..+2.82 | 3.99 | +48 | 0.58 |
| SM | 320 | -0.23 | -4.67..+4.22 | 6.35 | -249 | 0.61 |
| PE | 727 | -2.71 | -5.43..+0.01 | 3.89 | -5,131 | 0.58 |
| PB | 595 | -1.80 | -4.85..+1.25 | 4.36 | -4,978 | 0.56 |
| DN | 530 | -0.28 | -3.64..+3.08 | 4.80 | -691 | 0.59 |
| MV | 732 | -0.39 | -3.07..+2.29 | 3.82 | -1,328 | 0.54 |
| MA | 368 | -0.91 | -4.99..+3.17 | 5.83 | -1,559 | 0.62 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.46 | -1.75..+0.82 | 1.83 | -7,016 | 0.34 |
| london | 5303 | +0.40 | -1.00..+1.79 | 1.99 | +4,763 | 0.29 |
| pre | 1479 | -0.36 | -2.33..+1.62 | 2.82 | -2,030 | 0.22 |
| nyam | 6580 | +0.09 | -0.71..+0.90 | 1.15 | +669 | 0.19 |
| nypm | 4901 | +0.26 | -0.71..+1.24 | 1.39 | +3,284 | 0.22 |
| close | 72 | +0.59 | -5.06..+6.24 | 8.07 | +156 | 0.24 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | +0.41 | -2.02..+2.83 | 3.46 | +4,434 | 0.58 |
| london | 2243 | -1.61 | -3.79..+0.58 | 3.12 | -19,950 | 0.54 |
| pre | 540 | +2.93 | -1.94..+7.80 | 6.96 | +8,463 | 0.47 |
| nyam | 3095 | +0.25 | -1.56..+2.06 | 2.59 | +4,946 | 0.52 |
| nypm | 1898 | -0.25 | -2.33..+1.82 | 2.97 | -3,263 | 0.51 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.6 | -3280.761 |
| 2024.0 | 14562.0 | -0.435 | -6338.41 |
| 2025.0 | 19687.0 | 0.137 | 2694.022 |
| 2026.0 | 2229.0 | -0.116 | -258.11 |
**drift: monthly mean pts/trade** 202307:-2.97 202308:+0.98 202309:-1.34 202310:+1.06 202311:-0.43 202312:-2.67 202401:-3.96 202402:+0.00 202403:+0.00 202404:+0.00 202405:+1.60 202406:-1.28 202407:-0.93 202408:+0.00 202409:-0.12 202410:-0.67 202411:+0.00 202412:+0.00 202501:-0.51 202502:+1.07 202503:-1.01 202504:-0.10 202505:+0.94 202506:+2.32 202507:+0.35 202508:-1.02 202509:+0.03 202510:-1.07 202511:+0.04 202512:+1.50 202601:-0.12 202602:-0.10

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +1.51 | -0.58..+3.60 | 2.99 | +21,774 | 0.53 |
| 1 | 2264 | -0.60 | -2.91..+1.71 | 3.30 | -5,299 | 0.55 |
| 2 | 5854 | -0.54 | -1.99..+0.91 | 2.07 | -21,854 | 0.53 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | +0.50 | -4.89..+5.89 | 7.70 | +776 | 0.59 |
| VIX_mid | 6933 | -0.40 | -1.72..+0.93 | 1.89 | -12,768 | 0.55 |
| VIX_high | 3307 | +0.60 | -1.25..+2.45 | 2.65 | +6,612 | 0.50 |

## Breakdown: cusum_fixed|35|{'X': 2, 'k': 2, 'h': 3}

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | -0.23 | -0.70..+0.24 | 0.67 | -1,833 | 0.07 |
| HM | 2285 | +0.30 | -0.33..+0.93 | 0.90 | +1,852 | 0.08 |
| WT | 4265 | -0.05 | -0.14..+0.04 | 0.13 | -428 | 0.01 |
| KB | 3093 | -0.26 | -0.77..+0.25 | 0.73 | -1,108 | 0.08 |
| SM | 904 | +0.60 | -0.46..+1.65 | 1.51 | +1,065 | 0.08 |
| PE | 3049 | +0.07 | -0.43..+0.56 | 0.70 | +306 | 0.07 |
| PB | 2261 | +0.45 | -0.18..+1.07 | 0.90 | +2,687 | 0.08 |
| DN | 1762 | +0.34 | -0.38..+1.06 | 1.03 | +1,578 | 0.08 |
| MV | 2922 | -0.15 | -0.67..+0.37 | 0.75 | -1,161 | 0.08 |
| MA | 1093 | -0.57 | -1.43..+0.29 | 1.23 | -1,659 | 0.08 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.06 | -0.67..+0.79 | 1.04 | +517 | 0.07 |
| HM | 1008 | -0.16 | -1.02..+0.69 | 1.22 | -1,024 | 0.08 |
| WT | 1893 | -0.01 | -0.11..+0.08 | 0.13 | -95 | 0.01 |
| KB | 1374 | -0.23 | -0.93..+0.47 | 1.00 | -1,036 | 0.07 |
| SM | 363 | -0.71 | -2.41..+0.99 | 2.43 | -1,190 | 0.10 |
| PE | 1311 | -0.11 | -0.88..+0.65 | 1.09 | -526 | 0.07 |
| PB | 965 | -0.22 | -1.13..+0.70 | 1.31 | -1,315 | 0.08 |
| DN | 782 | -0.10 | -1.07..+0.86 | 1.38 | -509 | 0.08 |
| MV | 1253 | +0.25 | -0.48..+0.98 | 1.04 | +1,950 | 0.07 |
| MA | 474 | -1.10 | -2.56..+0.35 | 2.08 | -3,269 | 0.11 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | +0.15 | -1.07..+1.36 | 1.74 | +484 | 0.10 |
| HM | 621 | +0.15 | -1.18..+1.48 | 1.90 | +426 | 0.12 |
| WT | 1112 | -0.08 | -0.15..-0.00 | 0.10 | -273 | 0.00 |
| KB | 765 | -0.70 | -1.68..+0.28 | 1.40 | -1,295 | 0.09 |
| SM | 320 | +0.81 | -1.14..+2.75 | 2.78 | +888 | 0.12 |
| PE | 727 | -0.09 | -1.30..+1.12 | 1.73 | -173 | 0.11 |
| PB | 595 | -0.06 | -1.42..+1.31 | 1.95 | -165 | 0.11 |
| DN | 530 | -0.11 | -1.40..+1.19 | 1.85 | -261 | 0.09 |
| MV | 732 | +0.24 | -0.91..+1.39 | 1.64 | +820 | 0.10 |
| MA | 368 | +0.40 | -1.44..+2.25 | 2.64 | +686 | 0.13 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.21 | -1.01..+0.60 | 1.15 | -1,893 | 0.12 |
| london | 5303 | +0.21 | -0.41..+0.83 | 0.89 | +2,567 | 0.07 |
| pre | 1479 | +0.42 | -0.44..+1.29 | 1.24 | +1,314 | 0.04 |
| nyam | 6580 | -0.01 | -0.35..+0.34 | 0.49 | -419 | 0.03 |
| nypm | 4901 | -0.03 | -0.39..+0.34 | 0.52 | -286 | 0.04 |
| close | 72 | +0.11 | -2.02..+2.24 | 3.04 | +16 | 0.04 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | +0.01 | -1.13..+1.15 | 1.63 | +1,060 | 0.11 |
| london | 2243 | -0.54 | -1.43..+0.36 | 1.28 | -6,985 | 0.07 |
| pre | 540 | +1.52 | -0.40..+3.43 | 2.73 | +4,309 | 0.05 |
| nyam | 3095 | -0.10 | -0.49..+0.30 | 0.56 | -1,531 | 0.03 |
| nypm | 1898 | -0.36 | -0.93..+0.22 | 0.82 | -3,349 | 0.04 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | 0.227 | 1243.255 |
| 2024.0 | 14562.0 | -0.156 | -2271.13 |
| 2025.0 | 19687.0 | 0.001 | 27.481 |
| 2026.0 | 2229.0 | -0.03 | -66.165 |
**drift: monthly mean pts/trade** 202307:+0.54 202308:+1.82 202309:+0.16 202310:-0.20 202311:-1.34 202312:-0.55 202401:-1.22 202402:-0.07 202403:+0.35 202404:+0.99 202405:+0.94 202406:-1.51 202407:-0.45 202408:-0.02 202409:-0.04 202410:+0.15 202411:-0.10 202412:-1.00 202501:-0.68 202502:+0.34 202503:+0.10 202504:-0.20 202505:+0.40 202506:+1.22 202507:-1.07 202508:-0.49 202509:+0.50 202510:-0.40 202511:+0.08 202512:+0.26 202601:+0.18 202602:-0.56

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +0.01 | -0.84..+0.86 | 1.22 | +689 | 0.08 |
| 1 | 2264 | -0.32 | -1.37..+0.73 | 1.50 | -4,079 | 0.08 |
| 2 | 5854 | -0.11 | -0.61..+0.40 | 0.72 | -3,106 | 0.04 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | -0.03 | -1.67..+1.60 | 2.34 | -241 | 0.07 |
| VIX_mid | 6933 | -0.04 | -0.58..+0.51 | 0.78 | +95 | 0.07 |
| VIX_high | 3307 | -0.32 | -0.97..+0.32 | 0.92 | -6,350 | 0.04 |

## Breakdown: ogbm|lr0.05|phi0.99|pooled|m8|take

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | -0.41 | -1.78..+0.96 | 1.95 | -3,307 | 0.42 |
| HM | 2285 | -0.53 | -2.08..+1.01 | 2.20 | -3,250 | 0.44 |
| WT | 4265 | +0.15 | -0.53..+0.82 | 0.96 | +1,156 | 0.38 |
| KB | 3093 | -0.16 | -1.49..+1.16 | 1.90 | -707 | 0.44 |
| SM | 904 | -4.39 | -7.09..-1.69 | 3.86 | -7,830 | 0.54 |
| PE | 3049 | +0.39 | -0.87..+1.66 | 1.81 | +1,791 | 0.42 |
| PB | 2261 | +1.03 | -0.50..+2.56 | 2.18 | +6,189 | 0.41 |
| DN | 1762 | -0.14 | -1.90..+1.62 | 2.51 | -668 | 0.44 |
| MV | 2922 | -0.06 | -1.36..+1.25 | 1.87 | -436 | 0.42 |
| MA | 1093 | -2.74 | -5.26..-0.22 | 3.60 | -7,987 | 0.55 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | -0.49 | -2.26..+1.28 | 2.53 | -4,236 | 0.43 |
| HM | 1008 | -0.93 | -3.16..+1.31 | 3.19 | -5,828 | 0.44 |
| WT | 1893 | +0.41 | -0.64..+1.46 | 1.50 | +3,391 | 0.40 |
| KB | 1374 | +0.08 | -1.77..+1.93 | 2.64 | +342 | 0.42 |
| SM | 363 | -0.87 | -5.09..+3.35 | 6.04 | -1,461 | 0.54 |
| PE | 1311 | -1.45 | -3.33..+0.43 | 2.69 | -6,638 | 0.41 |
| PB | 965 | -2.66 | -4.83..-0.49 | 3.11 | -16,045 | 0.40 |
| DN | 782 | -1.14 | -3.79..+1.50 | 3.78 | -5,593 | 0.44 |
| MV | 1253 | +0.72 | -1.37..+2.81 | 2.98 | +5,661 | 0.43 |
| MA | 474 | -1.74 | -5.62..+2.14 | 5.54 | -5,159 | 0.56 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -1.73 | -4.66..+1.20 | 4.19 | -5,778 | 0.48 |
| HM | 621 | -2.88 | -5.90..+0.14 | 4.32 | -8,320 | 0.47 |
| WT | 1112 | -1.77 | -3.18..-0.36 | 2.01 | -6,419 | 0.44 |
| KB | 765 | -1.22 | -3.93..+1.48 | 3.86 | -2,262 | 0.48 |
| SM | 320 | +0.05 | -4.50..+4.60 | 6.50 | +58 | 0.55 |
| PE | 727 | -1.14 | -4.02..+1.74 | 4.11 | -2,165 | 0.50 |
| PB | 595 | -0.52 | -3.55..+2.50 | 4.32 | -1,451 | 0.46 |
| DN | 530 | -0.67 | -4.18..+2.84 | 5.01 | -1,650 | 0.51 |
| MV | 732 | -0.40 | -3.32..+2.52 | 4.17 | -1,368 | 0.51 |
| MA | 368 | -0.43 | -4.63..+3.76 | 5.99 | -740 | 0.55 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -1.25 | -2.99..+0.49 | 2.48 | -18,221 | 0.45 |
| london | 5303 | +0.22 | -1.53..+1.97 | 2.50 | +2,965 | 0.43 |
| pre | 1479 | +3.19 | -0.37..+6.74 | 5.08 | +9,635 | 0.46 |
| nyam | 6580 | -0.95 | -2.41..+0.50 | 2.08 | -15,322 | 0.40 |
| nypm | 4901 | +0.38 | -1.33..+2.10 | 2.45 | +5,424 | 0.42 |
| close | 72 | +2.74 | -6.16..+11.64 | 12.71 | +472 | 0.38 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | +1.08 | -1.50..+3.66 | 3.69 | +17,833 | 0.48 |
| london | 2243 | -2.19 | -4.94..+0.56 | 3.92 | -27,406 | 0.44 |
| pre | 540 | -1.55 | -6.66..+3.57 | 7.31 | -5,377 | 0.43 |
| nyam | 3095 | -1.07 | -3.14..+1.00 | 2.95 | -17,258 | 0.39 |
| nypm | 1898 | -0.37 | -3.09..+2.36 | 3.90 | -4,099 | 0.42 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.713 | -3899.032 |
| 2024.0 | 14562.0 | -0.49 | -7133.394 |
| 2025.0 | 19687.0 | -0.258 | -5088.69 |
| 2026.0 | 2229.0 | -1.92 | -4280.375 |
**drift: monthly mean pts/trade** 202307:-1.18 202308:+0.02 202309:+0.64 202310:-0.31 202311:-1.61 202312:-3.12 202401:-3.90 202402:-0.12 202403:+0.02 202404:+2.54 202405:-0.97 202406:+1.52 202407:-0.71 202408:-0.26 202409:+0.93 202410:-2.66 202411:+0.19 202412:-2.82 202501:+0.60 202502:-0.48 202503:-1.05 202504:-0.91 202505:-1.27 202506:+2.59 202507:+4.93 202508:-1.60 202509:-0.97 202510:-2.70 202511:-0.86 202512:+1.25 202601:-1.84 202602:-2.12

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +2.34 | -0.36..+5.03 | 3.85 | +33,977 | 0.52 |
| 1 | 2264 | -2.28 | -4.86..+0.30 | 3.69 | -25,538 | 0.43 |
| 2 | 5854 | -1.27 | -2.85..+0.31 | 2.26 | -44,005 | 0.38 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | -0.92 | -5.62..+3.78 | 6.72 | -2,143 | 0.46 |
| VIX_mid | 6933 | -0.22 | -1.77..+1.33 | 2.22 | -6,728 | 0.43 |
| VIX_high | 3307 | -1.29 | -3.46..+0.87 | 3.09 | -26,695 | 0.42 |

# LOSS SIDE (hold / tighten / cut vs hold-to-stop)

**Verdict counts over 1234 cells: {'DEAD': 1234}.** White reality check on PRE over all 1234 cells: p = 0.972; per family: bocpd_adapt 0.988, bocpd_fixed 0.836, btab 1.000, cusum_adapt 0.999, cusum_fixed 0.997, hmm 0.982, ogbm 0.665, rlog 0.940, rls 0.761.

Gates failed (count of cells): paired_CI_excludes0 1234, neighbours_agree 1234, RC_p>0.05 1234, 2x_cost<=0 1234, NOTC<=0 1234, year_share(total<=0) 1231, holdout_sign_agrees 1230, mean_up 1214, SPAN2<=0 1200, maxDD_not_worse 1157, placebo>=0.90 514, placebo<0.95 4, year_share>60% 3.

## OOS chain, best cell per family by PRE (IN-SAMPLE selection; HOLD and X are the confirmation spans)

| cell | PRE | HOLD | X | usd_wk | exit | saved_forf | win | plc | N_C | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bocpd_adapt|12m|1m|pooled | -0.13 [-0.58,+0.31] (MDE 0.63) | +0.00 [+0.00,+0.00] (MDE 0.00) | +0.23 (MDE 1.49) | -7,942|+0 | 0.20|0.00 | +4.12|-4.25 | 0.53>0.47 | 0.00|1.00 | -0.25|-0.33 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,year_share(total<=0),maxDD_not_worse |
| bocpd_fixed|17|{'hz': 1, 'p': 2, 'X': 2} | -0.04 [-0.49,+0.41] (MDE 0.64) | -0.43 [-1.05,+0.19] (MDE 0.88) | +0.03 (MDE 1.19) | -3,175|-21,741 | 0.21|0.18 | +4.24|-4.28 | 0.53>0.47 | nan|1.00 | -0.19|-0.25 | DEAD | mean_up,paired_CI_excludes0,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,year_share(total<=0),maxDD_not_worse |
| btab|disc1.0|pooled|z1|m8|take | +0.00 [+0.00,+0.00] (MDE 0.00) | +0.00 [+0.00,+0.00] (MDE 0.00) | -0.07 (MDE 0.32) | +0|+0 | 0.00|0.00 | +0.00|+0.00 | 0.53>0.53 | 0.00|0.00 | +0.00|+0.00 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| cusum_adapt|12m|1m|pooled | -0.25 [-0.69,+0.18] (MDE 0.62) | +0.00 [+0.00,+0.00] (MDE 0.00) | -0.56 (MDE 1.75) | -13,783|+0 | 0.17|0.00 | +3.74|-3.99 | 0.53>0.48 | 1.00|1.00 | -0.33|-0.42 | DEAD | mean_up,paired_CI_excludes0,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| cusum_fixed|23|{'X': 1, 'k': 2, 'h': 3} | -0.42 [-0.98,+0.15] (MDE 0.81) | -0.62 [-1.42,+0.17] (MDE 1.13) | -0.07 (MDE 1.36) | -23,692|-39,435 | 0.28|0.25 | +6.28|-6.69 | 0.53>0.44 | nan|1.00 | -0.68|-0.70 | DEAD | mean_up,paired_CI_excludes0,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| hmm|K3|1w|1w|level|q0.6|a1 | -0.35 [-1.06,+0.36] (MDE 1.01) | +0.00 [+0.00,+0.00] (MDE 0.00) | -0.54 (MDE 1.67) | -20,853|+0 | 0.38|0.00 | +9.07|-9.42 | 0.53>0.39 | nan|1.00 | -0.72|-0.73 | DEAD | mean_up,paired_CI_excludes0,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| ogbm|lr0.2|phi0.999|pooled|m8|take | +0.20 [-0.44,+0.84] (MDE 0.91) | -0.73 [-1.60,+0.15] (MDE 1.25) | -0.96 (MDE 1.60) | +12,495|-38,976 | 0.33|0.31 | +7.76|-7.56 | 0.53>0.42 | 0.00|1.00 | -0.09|-0.13 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| rlog|lr0.02|rho0.99|pooled|m8|take | -0.34 [-1.13,+0.44] (MDE 1.12) | -1.01 [-2.16,+0.14] (MDE 1.65) | -1.57 (MDE 2.26) | -21,346|-56,293 | 0.45|0.45 | +11.40|-11.74 | 0.53>0.34 | 0.00|1.00 | -0.84|-0.79 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| rls|lam0.995|perbook|m8|take | +0.05 [-0.55,+0.65] (MDE 0.86) | -0.81 [-1.65,+0.03] (MDE 1.21) | -0.39 (MDE 1.68) | +5,385|-49,116 | 0.45|0.42 | +8.89|-8.85 | 0.53>0.42 | 0.70|1.00 | -0.25|-0.40 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |

Columns: pts/trade over ALL scored trades of the span (cluster-robust CI, MDE = 2.8 SE); $/wk = PRE|HOLD at the book lots; exit = share of trades with an added exit; saved|forfeited = sum of positive|negative paired deltas per trade (PRE); win = base>rule win rate (PRE); plc = placebo ranks (shuffled labels | random exits at the same rate; n/a where the fit uses no labels); N|C = PRE mean without the target correction | with doubled exit friction.

## Top 10 by PRE delta (IN-SAMPLE selection) and what killed each

| cell | PRE | HOLD | X | usd_wk | exit | saved_forf | win | plc | N_C | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ogbm|lr0.2|phi0.999|pooled|m8|take | +0.20 [-0.44,+0.84] (MDE 0.91) | -0.73 [-1.60,+0.15] (MDE 1.25) | -0.96 (MDE 1.60) | +12,495|-38,976 | 0.33|0.31 | +7.76|-7.56 | 0.53>0.42 | 0.00|1.00 | -0.09|-0.13 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| ogbm|lr0.2|phi0.999|pooled|m4|take | +0.19 [-0.52,+0.90] (MDE 1.01) | -0.76 [-1.76,+0.25] (MDE 1.43) | -0.99 (MDE 1.79) | +11,124|-40,145 | 0.40|0.37 | +9.35|-9.16 | 0.53>0.39 | 0.00|1.00 | -0.17|-0.20 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| ogbm|lr0.2|phi0.999|pooled|m1|take | +0.17 [-0.59,+0.93] (MDE 1.08) | -0.96 [-2.03,+0.12] (MDE 1.54) | -1.14 (MDE 1.94) | +7,790|-51,100 | 0.44|0.43 | +10.54|-10.37 | 0.53>0.37 | 0.00|1.00 | -0.24|-0.27 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| ogbm|lr0.2|phi0.999|pooled|m2|take | +0.16 [-0.58,+0.90] (MDE 1.06) | -0.84 [-1.89,+0.20] (MDE 1.50) | -0.97 (MDE 1.89) | +7,895|-44,695 | 0.43|0.41 | +10.14|-9.97 | 0.53>0.38 | 0.00|1.00 | -0.23|-0.26 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| ogbm|lr0.2|phi0.999|pooled|m1|tt | +0.12 [-0.65,+0.89] (MDE 1.10) | -1.02 [-2.11,+0.08] (MDE 1.56) | -1.18 (MDE 1.96) | +5,564|-56,553 | 0.46|0.44 | +10.75|-10.63 | 0.53>0.37 | 0.00|1.00 | -0.30|-0.33 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| ogbm|lr0.2|phi0.999|pooled|m2|tt | +0.09 [-0.66,+0.85] (MDE 1.08) | -0.97 [-2.06,+0.11] (MDE 1.55) | -1.07 (MDE 1.92) | +4,319|-53,872 | 0.45|0.43 | +10.51|-10.41 | 0.53>0.38 | 0.00|1.00 | -0.31|-0.36 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| ogbm|lr0.2|phi0.99|pooled|m0|take | +0.08 [-0.63,+0.80] (MDE 1.02) | -0.66 [-1.69,+0.37] (MDE 1.47) | -0.63 (MDE 1.80) | +4,793|-38,055 | 0.38|0.36 | +9.44|-9.36 | 0.53>0.38 | 0.00|1.00 | -0.32|-0.29 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| ogbm|lr0.2|phi0.999|pooled|m0|take | +0.08 [-0.69,+0.86] (MDE 1.11) | -0.99 [-2.09,+0.12] (MDE 1.58) | -1.17 (MDE 1.96) | +3,190|-54,338 | 0.46|0.44 | +10.93|-10.85 | 0.53>0.37 | 0.00|1.00 | -0.35|-0.37 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| ogbm|lr0.2|phi0.999|pooled|m4|tt | +0.08 [-0.66,+0.82] (MDE 1.06) | -0.93 [-1.99,+0.13] (MDE 1.52) | -1.08 (MDE 1.86) | +5,050|-50,377 | 0.44|0.42 | +10.05|-9.97 | 0.53>0.39 | 0.00|1.00 | -0.30|-0.36 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| ogbm|lr0.2|phi0.999|pooled|m0|tt | +0.07 [-0.71,+0.85] (MDE 1.11) | -1.05 [-2.16,+0.06] (MDE 1.59) | -1.24 (MDE 1.98) | +2,891|-58,511 | 0.46|0.45 | +11.03|-10.96 | 0.53>0.37 | 0.00|1.00 | -0.36|-0.39 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |

## Top 10 by HOLD delta (selection on the holdout, labelled, not a candidate)

| cell | PRE | HOLD | X | usd_wk | exit | saved_forf | win | plc | N_C | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ogbm|lr0.05|phi0.99|pooled|m8|take | +0.02 [-0.22,+0.25] (MDE 0.33) | +0.10 [-0.24,+0.44] (MDE 0.48) | -0.19 (MDE 0.33) | +492|+3,421 | 0.04|0.04 | +1.00|-0.98 | 0.53>0.52 | 0.00|1.00 | -0.02|-0.03 | DEAD | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share>60% |
| ogbm|lr0.05|phi0.99|pooled|m4|take | -0.28 [-0.66,+0.10] (MDE 0.54) | +0.09 [-0.44,+0.62] (MDE 0.75) | -0.42 (MDE 0.74) | -16,064|+5,408 | 0.12|0.11 | +2.77|-3.04 | 0.53>0.49 | 0.00|1.00 | -0.40|-0.40 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| ogbm|lr0.05|phi0.999|pooled|m8|take | -0.08 [-0.49,+0.33] (MDE 0.59) | +0.00 [-0.57,+0.57] (MDE 0.82) | -0.44 (MDE 1.04) | -5,306|+10 | 0.18|0.15 | +3.63|-3.71 | 0.53>0.48 | 0.00|1.00 | -0.20|-0.26 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| cusum_adapt|1m|1m|pooled | -0.38 [-1.01,+0.25] (MDE 0.89) | +0.00 [-0.96,+0.96] (MDE 1.37) | -0.98 (MDE 1.87) | -19,169|+1,187 | 0.33|0.31 | +7.45|-7.83 | 0.53>0.42 | 0.00|1.00 | -0.64|-0.70 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0) |
| cusum_adapt|6m|1d|pooled | -0.76 [-1.21,-0.31] (MDE 0.64) | +0.00 [+0.00,+0.00] (MDE 0.00) | -0.60 (MDE 1.87) | -42,398|+0 | 0.18|0.00 | +3.61|-4.38 | 0.53>0.47 | 1.00|1.00 | -0.86|-0.94 | DEAD | mean_up,paired_CI_excludes0,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| hmm|K3|1w|1d|flip|q0.6|a1 | -0.49 [-1.20,+0.21] (MDE 1.01) | +0.00 [+0.00,+0.00] (MDE 0.00) | -0.29 (MDE 1.71) | -28,392|+0 | 0.39|0.00 | +9.29|-9.78 | 0.53>0.39 | nan|1.00 | -0.88|-0.88 | DEAD | mean_up,paired_CI_excludes0,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| cusum_adapt|6m|intraday|pooled | -0.65 [-1.10,-0.21] (MDE 0.63) | +0.00 [+0.00,+0.00] (MDE 0.00) | -0.47 (MDE 1.88) | -35,623|+0 | 0.18|0.00 | +3.64|-4.30 | 0.53>0.47 | 0.00|1.00 | -0.75|-0.83 | DEAD | mean_up,paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| hmm|K3|1w|intraday|level|q0.85|a1 | -0.52 [-1.21,+0.16] (MDE 0.98) | +0.00 [+0.00,+0.00] (MDE 0.00) | -0.46 (MDE 1.64) | -29,967|+0 | 0.35|0.00 | +8.43|-8.95 | 0.53>0.40 | nan|1.00 | -0.87|-0.87 | DEAD | mean_up,paired_CI_excludes0,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| hmm|K3|1w|intraday|level|q0.85|a0 | -0.69 [-1.45,+0.08] (MDE 1.10) | +0.00 [+0.00,+0.00] (MDE 0.00) | -1.25 (MDE 2.04) | -40,857|+0 | 0.40|0.00 | +9.99|-10.68 | 0.53>0.36 | nan|1.00 | -1.14|-1.09 | DEAD | mean_up,paired_CI_excludes0,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |
| hmm|K3|1w|1d|level|q0.6|a1 | -0.37 [-1.08,+0.33] (MDE 1.01) | +0.00 [+0.00,+0.00] (MDE 0.00) | -0.39 (MDE 1.66) | -22,504|+0 | 0.38|0.00 | +9.12|-9.50 | 0.53>0.39 | nan|1.00 | -0.74|-0.75 | DEAD | mean_up,paired_CI_excludes0,neighbours_agree,RC_p>0.05,holdout_sign_agrees,2x_cost<=0,NOTC<=0,SPAN2<=0,year_share(total<=0),maxDD_not_worse |

## Online learners: PRE chain mean pts/trade by config (forgetting / learning rate) x policy (margin m, take or take+tighten)

| cfg | m0|take | m0|tt | m1|take | m1|tt | m2|take | m2|tt | m4|take | m4|tt | m8|take | m8|tt |
|---|---|---|---|---|---|---|---|---|---|---|
| btab|disc0.998|pooled|z0 | -1.22 | -1.23 | -1.19 | -1.27 | -1.12 | -1.29 | -0.95 | -1.31 | -0.49 | -1.23 |
| btab|disc0.998|pooled|z1 | -0.49 | -0.52 | -0.53 | -0.51 | -0.47 | -0.55 | -0.13 | -0.43 | -0.15 | -0.47 |
| btab|disc0.9995|pooled|z0 | -1.04 | -1.2 | -0.87 | -1.21 | -0.75 | -1.33 | -0.42 | -1.36 | -0.22 | -1.38 |
| btab|disc0.9995|pooled|z1 | -0.31 | -0.43 | -0.1 | -0.35 | -0.28 | -0.41 | -0.12 | -0.39 | -0.07 | -0.42 |
| btab|disc0.99|pooled|z0 | -0.83 | -0.9 | -0.9 | -0.97 | -0.8 | -0.92 | -0.76 | -1.04 | -0.44 | -0.94 |
| btab|disc0.99|pooled|z1 | -0.28 | -0.31 | -0.18 | -0.26 | -0.11 | -0.25 | -0.27 | -0.3 | -0.26 | -0.38 |
| btab|disc1.0|pooled|z0 | -1.03 | -1.14 | -0.84 | -1.29 | -0.89 | -1.22 | -0.12 | -1.22 | -0.0 | -1.23 |
| btab|disc1.0|pooled|z1 | -0.8 | -0.91 | -0.5 | -0.84 | -0.17 | -0.79 | -0.05 | -0.81 | 0.0 | -0.82 |
| ogbm|lr0.05|phi0.999|pooled | -0.04 | -0.04 | -0.12 | -0.11 | -0.02 | -0.06 | -0.15 | -0.2 | -0.08 | -0.31 |
| ogbm|lr0.05|phi0.99|pooled | -0.12 | -0.18 | -0.2 | -0.27 | -0.29 | -0.34 | -0.28 | -0.33 | 0.02 | -0.3 |
| ogbm|lr0.05|phi1.0|pooled | -0.3 | -0.29 | -0.25 | -0.32 | -0.17 | -0.27 | -0.19 | -0.36 | -0.02 | -0.42 |
| ogbm|lr0.2|phi0.999|pooled | 0.08 | 0.07 | 0.17 | 0.12 | 0.16 | 0.09 | 0.19 | 0.08 | 0.2 | -0.05 |
| ogbm|lr0.2|phi0.99|pooled | 0.08 | 0.07 | 0.04 | 0.01 | 0.0 | 0.02 | -0.12 | -0.06 | -0.17 | -0.15 |
| ogbm|lr0.2|phi1.0|pooled | -0.26 | -0.26 | -0.15 | -0.22 | -0.03 | -0.14 | -0.08 | -0.15 | 0.04 | -0.15 |
| rlog|lr0.02|rho0.999|pooled | -0.68 | -0.67 | -0.65 | -0.64 | -0.65 | -0.65 | -0.61 | -0.65 | -0.46 | -0.69 |
| rlog|lr0.02|rho0.99|pooled | -0.48 | -0.48 | -0.46 | -0.49 | -0.43 | -0.5 | -0.44 | -0.53 | -0.34 | -0.49 |
| rlog|lr0.02|rho1.0|pooled | -0.75 | -0.76 | -0.72 | -0.77 | -0.7 | -0.77 | -0.65 | -0.73 | -0.63 | -0.77 |
| rlog|lr0.05|rho0.999|pooled | -0.59 | -0.6 | -0.59 | -0.6 | -0.54 | -0.59 | -0.53 | -0.58 | -0.54 | -0.58 |
| rlog|lr0.05|rho0.99|pooled | -0.63 | -0.62 | -0.64 | -0.63 | -0.62 | -0.62 | -0.64 | -0.65 | -0.63 | -0.64 |
| rlog|lr0.05|rho1.0|pooled | -0.7 | -0.73 | -0.7 | -0.74 | -0.7 | -0.74 | -0.71 | -0.74 | -0.69 | -0.75 |
| rlog|lr0.1|rho0.999|pooled | -0.58 | -0.57 | -0.57 | -0.57 | -0.55 | -0.56 | -0.55 | -0.55 | -0.55 | -0.55 |
| rlog|lr0.1|rho0.99|perbook | -0.82 | -0.84 | -0.83 | -0.84 | -0.83 | -0.85 | -0.8 | -0.82 | -0.76 | -0.8 |
| rlog|lr0.1|rho0.99|pooled | -0.74 | -0.73 | -0.76 | -0.73 | -0.78 | -0.74 | -0.77 | -0.73 | -0.76 | -0.74 |
| rlog|lr0.1|rho1.0|perbook | -0.83 | -0.82 | -0.84 | -0.83 | -0.83 | -0.83 | -0.8 | -0.81 | -0.81 | -0.84 |
| rlog|lr0.1|rho1.0|pooled | -0.61 | -0.62 | -0.62 | -0.64 | -0.62 | -0.65 | -0.58 | -0.61 | -0.58 | -0.62 |
| rlog|lr0.3|rho0.999|pooled | -0.54 | -0.54 | -0.56 | -0.56 | -0.55 | -0.55 | -0.54 | -0.54 | -0.54 | -0.54 |
| rlog|lr0.3|rho0.99|pooled | -0.88 | -0.88 | -0.87 | -0.87 | -0.88 | -0.87 | -0.85 | -0.84 | -0.88 | -0.85 |
| rlog|lr0.3|rho1.0|pooled | -0.7 | -0.71 | -0.7 | -0.71 | -0.68 | -0.69 | -0.65 | -0.67 | -0.66 | -0.67 |
| rls|lam0.995|perbook | -0.27 | -0.28 | -0.22 | -0.28 | -0.16 | -0.26 | -0.14 | -0.31 | 0.05 | -0.32 |
| rls|lam0.995|pooled | -0.61 | -0.63 | -0.59 | -0.65 | -0.63 | -0.7 | -0.54 | -0.68 | -0.46 | -0.66 |
| rls|lam0.998|perbook | -0.29 | -0.31 | -0.34 | -0.35 | -0.38 | -0.39 | -0.31 | -0.44 | -0.19 | -0.42 |
| rls|lam0.998|pooled | -0.33 | -0.32 | -0.25 | -0.29 | -0.2 | -0.27 | -0.12 | -0.25 | -0.17 | -0.38 |
| rls|lam0.9995|perbook | -0.49 | -0.5 | -0.5 | -0.53 | -0.53 | -0.59 | -0.46 | -0.6 | -0.34 | -0.66 |
| rls|lam0.9995|pooled | -0.12 | -0.14 | -0.12 | -0.18 | -0.04 | -0.16 | 0.03 | -0.21 | 0.01 | -0.36 |
| rls|lam0.99|perbook | -0.37 | -0.41 | -0.26 | -0.4 | -0.14 | -0.36 | -0.17 | -0.46 | -0.09 | -0.54 |
| rls|lam0.99|pooled | -0.71 | -0.79 | -0.71 | -0.79 | -0.69 | -0.83 | -0.59 | -0.83 | -0.46 | -0.81 |
| rls|lam1.0|perbook | -0.51 | -0.53 | -0.52 | -0.55 | -0.64 | -0.71 | -0.49 | -0.64 | -0.39 | -0.74 |
| rls|lam1.0|pooled | -0.62 | -0.67 | -0.59 | -0.68 | -0.54 | -0.67 | -0.47 | -0.71 | -0.3 | -0.61 |

Same, HOLD span (all configs shown; none selected on it):

| cfg | m0|take | m0|tt | m1|take | m1|tt | m2|take | m2|tt | m4|take | m4|tt | m8|take | m8|tt |
|---|---|---|---|---|---|---|---|---|---|---|
| btab|disc0.998|pooled|z0 | -1.6 | -1.56 | -1.48 | -1.43 | -1.25 | -1.34 | -0.86 | -1.2 | -0.43 | -1.16 |
| btab|disc0.998|pooled|z1 | -0.64 | -0.57 | -0.45 | -0.44 | -0.43 | -0.34 | -0.43 | -0.31 | -0.16 | -0.31 |
| btab|disc0.9995|pooled|z0 | -1.72 | -1.98 | -1.29 | -1.74 | -1.15 | -1.65 | -0.51 | -1.44 | -0.45 | -1.5 |
| btab|disc0.9995|pooled|z1 | -0.49 | -0.54 | -0.53 | -0.6 | -0.49 | -0.51 | -0.36 | -0.59 | -0.11 | -0.54 |
| btab|disc0.99|pooled|z0 | -1.61 | -1.72 | -1.36 | -1.53 | -1.14 | -1.55 | -1.0 | -1.47 | -0.59 | -1.26 |
| btab|disc0.99|pooled|z1 | -0.32 | -0.39 | -0.42 | -0.44 | -0.43 | -0.46 | -0.4 | -0.38 | -0.26 | -0.34 |
| btab|disc1.0|pooled|z0 | -1.52 | -1.83 | -0.91 | -1.66 | -0.21 | -1.55 | -0.13 | -1.52 | 0.0 | -1.53 |
| btab|disc1.0|pooled|z1 | -0.76 | -1.26 | -0.38 | -1.18 | -0.22 | -1.14 | 0.0 | -1.15 | 0.0 | -1.15 |
| ogbm|lr0.05|phi0.999|pooled | -0.4 | -0.42 | -0.36 | -0.4 | -0.24 | -0.34 | -0.19 | -0.38 | 0.0 | -0.42 |
| ogbm|lr0.05|phi0.99|pooled | -0.14 | -0.19 | -0.06 | -0.2 | -0.06 | -0.22 | 0.09 | -0.18 | 0.1 | -0.15 |
| ogbm|lr0.05|phi1.0|pooled | -0.75 | -0.8 | -0.67 | -0.75 | -0.67 | -0.74 | -0.41 | -0.63 | -0.14 | -0.53 |
| ogbm|lr0.2|phi0.999|pooled | -0.99 | -1.05 | -0.96 | -1.02 | -0.84 | -0.97 | -0.76 | -0.93 | -0.73 | -0.94 |
| ogbm|lr0.2|phi0.99|pooled | -0.66 | -0.73 | -0.6 | -0.7 | -0.62 | -0.73 | -0.44 | -0.68 | -0.11 | -0.66 |
| ogbm|lr0.2|phi1.0|pooled | -1.52 | -1.53 | -1.39 | -1.51 | -1.34 | -1.45 | -1.42 | -1.45 | -1.08 | -1.36 |
| rlog|lr0.02|rho0.999|pooled | -2.08 | -2.06 | -2.02 | -2.0 | -1.97 | -1.98 | -1.94 | -1.99 | -1.94 | -1.92 |
| rlog|lr0.02|rho0.99|pooled | -1.08 | -1.09 | -1.11 | -1.13 | -1.14 | -1.14 | -1.07 | -1.14 | -1.01 | -1.08 |
| rlog|lr0.02|rho1.0|pooled | -2.39 | -2.37 | -2.37 | -2.36 | -2.34 | -2.32 | -2.23 | -2.26 | -2.03 | -2.14 |
| rlog|lr0.05|rho0.999|pooled | -2.11 | -2.1 | -2.07 | -2.05 | -2.01 | -1.99 | -1.97 | -1.97 | -1.8 | -1.84 |
| rlog|lr0.05|rho0.99|pooled | -1.16 | -1.14 | -1.13 | -1.12 | -1.12 | -1.1 | -1.1 | -1.12 | -1.06 | -1.13 |
| rlog|lr0.05|rho1.0|pooled | -2.3 | -2.32 | -2.23 | -2.26 | -2.18 | -2.23 | -2.14 | -2.15 | -2.09 | -2.14 |
| rlog|lr0.1|rho0.999|pooled | -1.84 | -1.84 | -1.83 | -1.83 | -1.84 | -1.84 | -1.82 | -1.81 | -1.79 | -1.74 |
| rlog|lr0.1|rho0.99|perbook | -1.53 | -1.53 | -1.48 | -1.49 | -1.51 | -1.51 | -1.46 | -1.5 | -1.37 | -1.47 |
| rlog|lr0.1|rho0.99|pooled | -1.23 | -1.22 | -1.23 | -1.24 | -1.22 | -1.25 | -1.21 | -1.27 | -1.26 | -1.36 |
| rlog|lr0.1|rho1.0|perbook | -1.75 | -1.74 | -1.75 | -1.75 | -1.71 | -1.72 | -1.67 | -1.71 | -1.64 | -1.72 |
| rlog|lr0.1|rho1.0|pooled | -2.15 | -2.15 | -2.17 | -2.14 | -2.19 | -2.17 | -2.2 | -2.15 | -2.14 | -2.12 |
| rlog|lr0.3|rho0.999|pooled | -1.85 | -1.86 | -1.86 | -1.87 | -1.88 | -1.88 | -1.88 | -1.87 | -1.86 | -1.84 |
| rlog|lr0.3|rho0.99|pooled | -1.27 | -1.29 | -1.28 | -1.29 | -1.26 | -1.27 | -1.23 | -1.23 | -1.32 | -1.31 |
| rlog|lr0.3|rho1.0|pooled | -1.87 | -1.87 | -1.87 | -1.87 | -1.88 | -1.87 | -1.89 | -1.88 | -1.88 | -1.88 |
| rls|lam0.995|perbook | -1.06 | -1.12 | -1.01 | -1.07 | -0.99 | -1.09 | -0.9 | -1.0 | -0.81 | -0.87 |
| rls|lam0.995|pooled | -1.55 | -1.6 | -1.37 | -1.48 | -1.33 | -1.45 | -1.22 | -1.41 | -0.85 | -1.26 |
| rls|lam0.998|perbook | -1.0 | -1.05 | -0.83 | -0.95 | -0.79 | -0.94 | -0.73 | -1.01 | -0.59 | -0.82 |
| rls|lam0.998|pooled | -0.74 | -0.76 | -0.69 | -0.73 | -0.65 | -0.76 | -0.67 | -0.83 | -0.33 | -0.78 |
| rls|lam0.9995|perbook | -0.94 | -0.97 | -0.96 | -0.99 | -0.93 | -0.94 | -0.77 | -0.86 | -0.38 | -0.68 |
| rls|lam0.9995|pooled | -0.77 | -0.72 | -0.67 | -0.7 | -0.58 | -0.64 | -0.23 | -0.5 | -0.14 | -0.48 |
| rls|lam0.99|perbook | -0.97 | -1.01 | -0.91 | -0.98 | -0.87 | -0.96 | -0.83 | -0.91 | -0.84 | -1.06 |
| rls|lam0.99|pooled | -1.6 | -1.66 | -1.49 | -1.62 | -1.41 | -1.54 | -1.41 | -1.6 | -1.25 | -1.58 |
| rls|lam1.0|perbook | -1.07 | -1.11 | -0.97 | -1.05 | -1.0 | -1.06 | -0.84 | -0.89 | -0.48 | -0.75 |
| rls|lam1.0|pooled | -1.03 | -1.04 | -1.14 | -1.24 | -0.95 | -1.11 | -0.75 | -0.95 | -0.46 | -0.74 |

### cusum_adapt: mean over its cells of the PRE chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.867 | nan |
| 2w | -0.85 | -1.156 | -0.888 | -0.827 |
| 1m | nan | nan | nan | -0.758 |
| 3m | -0.599 | -0.638 | -0.685 | -0.483 |
| 6m | -0.665 | -0.75 | -0.587 | -0.53 |
| 12m | -0.583 | -0.655 | -0.425 | -0.393 |
| YTD | -0.888 | -0.929 | -0.813 | -0.706 |
| ew5 | -0.919 | -0.987 | -0.662 | -0.697 |
| ew10 | -0.952 | -0.977 | -0.717 | -0.697 |
| ew20 | -0.781 | -0.818 | -0.782 | -0.556 |

### cusum_adapt: mean over its cells of the HOLD chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.723 | nan |
| 2w | -0.617 | -0.727 | -0.691 | -0.892 |
| 1m | nan | nan | nan | -0.645 |
| 3m | -0.753 | -0.808 | -0.951 | -0.72 |
| 6m | -0.355 | -0.309 | -0.313 | -0.311 |
| 12m | -0.295 | -0.262 | -0.218 | -0.268 |
| YTD | -0.511 | -0.54 | -0.499 | -0.593 |
| ew5 | -0.27 | -0.346 | -0.57 | -0.616 |
| ew10 | -0.407 | -0.638 | -0.685 | -0.765 |
| ew20 | -0.349 | -0.349 | -0.502 | -0.637 |

### bocpd_adapt: mean over its cells of the PRE chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.582 | nan |
| 2w | -0.424 | -0.461 | -0.553 | -0.577 |
| 1m | nan | nan | nan | -0.632 |
| 3m | -0.314 | -0.349 | -0.371 | -0.2 |
| 6m | -0.287 | -0.289 | -0.305 | -0.17 |
| 12m | -0.304 | -0.307 | -0.215 | -0.181 |
| YTD | -0.376 | -0.401 | -0.411 | -0.32 |
| ew5 | -0.547 | -0.682 | -0.554 | -0.491 |
| ew10 | -0.557 | -0.589 | -0.609 | -0.457 |
| ew20 | -0.456 | -0.479 | -0.463 | -0.333 |

### bocpd_adapt: mean over its cells of the HOLD chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.536 | nan |
| 2w | -0.385 | -0.41 | -0.625 | -0.432 |
| 1m | nan | nan | nan | -0.5 |
| 3m | -0.586 | -0.674 | -0.576 | -0.735 |
| 6m | -0.406 | -0.441 | -0.476 | -0.372 |
| 12m | -0.208 | -0.216 | -0.255 | -0.251 |
| YTD | -0.347 | -0.347 | -0.385 | -0.558 |
| ew5 | -0.414 | -0.468 | -0.47 | -0.513 |
| ew10 | -0.515 | -0.514 | -0.495 | -0.606 |
| ew20 | -0.401 | -0.39 | -0.353 | -0.801 |

### hmm: mean over its cells of the PRE chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.704 | nan |
| 2w | -0.741 | -0.712 | -0.752 | -0.739 |
| 1m | nan | nan | nan | -0.766 |
| 3m | -0.739 | -0.751 | -0.746 | -0.759 |
| 6m | -0.779 | -0.793 | -0.769 | -0.762 |
| 12m | -0.768 | -0.794 | -0.79 | -0.777 |
| YTD | -0.749 | -0.721 | -0.757 | -0.762 |
| ew5 | -0.912 | -0.914 | -0.92 | -0.899 |
| ew10 | -0.909 | -0.909 | -0.909 | -0.908 |
| ew20 | -0.898 | -0.894 | -0.895 | -0.906 |

### hmm: mean over its cells of the HOLD chain pts/trade by window x re-fit step

| window | intraday | 1d | 1w | 1m |
|---|---|---|---|---|
| 1w | nan | nan | -0.832 | nan |
| 2w | -1.365 | -1.373 | -1.396 | -1.363 |
| 1m | nan | nan | nan | -1.396 |
| 3m | -1.371 | -1.391 | -1.332 | -1.348 |
| 6m | -1.363 | -1.391 | -1.378 | -1.356 |
| 12m | -1.362 | -1.345 | -1.38 | -1.365 |
| YTD | -1.349 | -1.376 | -1.37 | -1.359 |
| ew5 | -1.585 | -1.586 | -1.592 | -1.604 |
| ew10 | -1.595 | -1.595 | -1.589 | -1.602 |
| ew20 | -1.569 | -1.571 | -1.545 | -1.56 |

## Breakdown: ogbm|lr0.2|phi0.999|pooled|m8|take

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | +0.57 | -0.57..+1.71 | 1.63 | +4,572 | 0.35 |
| HM | 2285 | +0.59 | -0.64..+1.83 | 1.76 | +3,605 | 0.35 |
| WT | 4265 | +0.49 | -0.10..+1.07 | 0.83 | +3,865 | 0.28 |
| KB | 3093 | -0.56 | -1.65..+0.53 | 1.56 | -2,412 | 0.33 |
| SM | 904 | -2.07 | -4.37..+0.23 | 3.29 | -3,692 | 0.41 |
| PE | 3049 | +0.74 | -0.31..+1.80 | 1.51 | +3,388 | 0.34 |
| PB | 2261 | +0.46 | -0.71..+1.63 | 1.68 | +2,778 | 0.31 |
| DN | 1762 | +0.02 | -1.41..+1.45 | 2.04 | +79 | 0.33 |
| MV | 2922 | +0.47 | -0.63..+1.57 | 1.57 | +3,639 | 0.34 |
| MA | 1093 | -1.14 | -3.20..+0.91 | 2.94 | -3,327 | 0.39 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.05 | -1.46..+1.57 | 2.17 | +458 | 0.30 |
| HM | 1008 | -0.55 | -2.34..+1.24 | 2.56 | -3,471 | 0.31 |
| WT | 1893 | -0.04 | -0.90..+0.82 | 1.23 | -325 | 0.27 |
| KB | 1374 | -0.72 | -2.23..+0.79 | 2.16 | -3,204 | 0.31 |
| SM | 363 | -1.43 | -4.81..+1.95 | 4.83 | -2,403 | 0.39 |
| PE | 1311 | -1.71 | -3.32..-0.10 | 2.30 | -7,852 | 0.31 |
| PB | 965 | -1.48 | -3.15..+0.18 | 2.38 | -8,955 | 0.25 |
| DN | 782 | -1.92 | -4.07..+0.22 | 3.07 | -9,402 | 0.33 |
| MV | 1253 | -0.71 | -2.47..+1.05 | 2.52 | -5,527 | 0.35 |
| MA | 474 | +0.58 | -2.21..+3.37 | 3.99 | +1,706 | 0.36 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -1.85 | -3.99..+0.30 | 3.07 | -6,154 | 0.32 |
| HM | 621 | -1.38 | -3.58..+0.82 | 3.14 | -3,990 | 0.32 |
| WT | 1112 | -1.75 | -2.90..-0.61 | 1.63 | -6,345 | 0.26 |
| KB | 765 | -0.51 | -2.62..+1.60 | 3.02 | -939 | 0.34 |
| SM | 320 | -0.49 | -3.89..+2.91 | 4.86 | -544 | 0.39 |
| PE | 727 | -1.48 | -3.64..+0.69 | 3.09 | -2,797 | 0.34 |
| PB | 595 | -0.71 | -3.05..+1.64 | 3.35 | -1,953 | 0.32 |
| DN | 530 | -1.31 | -3.95..+1.34 | 3.78 | -3,222 | 0.36 |
| MV | 732 | +0.38 | -1.85..+2.60 | 3.17 | +1,281 | 0.37 |
| MA | 368 | +1.01 | -2.14..+4.16 | 4.50 | +1,734 | 0.37 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.70 | -2.03..+0.64 | 1.90 | -10,880 | 0.32 |
| london | 5303 | +0.02 | -1.37..+1.40 | 1.98 | +1,974 | 0.36 |
| pre | 1479 | +2.84 | +0.43..+5.26 | 3.45 | +9,259 | 0.36 |
| nyam | 6580 | +0.18 | -0.98..+1.33 | 1.65 | +2,279 | 0.30 |
| nypm | 4901 | +0.63 | -0.83..+2.10 | 2.09 | +8,094 | 0.34 |
| close | 72 | +11.25 | +3.12..+19.39 | 11.63 | +1,770 | 0.44 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | -0.40 | -2.30..+1.49 | 2.70 | -4,577 | 0.31 |
| london | 2243 | -2.03 | -3.86..-0.19 | 2.62 | -24,112 | 0.29 |
| pre | 540 | -0.40 | -3.04..+2.25 | 3.78 | -1,253 | 0.24 |
| nyam | 3095 | -0.41 | -1.91..+1.09 | 2.15 | -6,437 | 0.29 |
| nypm | 1898 | -0.38 | -2.50..+1.74 | 3.03 | -2,941 | 0.35 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.888 | -4855.701 |
| 2024.0 | 14562.0 | 0.299 | 4358.196 |
| 2025.0 | 19687.0 | -0.263 | -5177.238 |
| 2026.0 | 2229.0 | -1.53 | -3409.685 |
**drift: monthly mean pts/trade** 202307:-0.17 202308:-0.82 202309:-1.95 202310:-0.22 202311:+0.32 202312:-2.99 202401:-1.33 202402:-0.49 202403:+0.97 202404:+3.16 202405:-0.35 202406:+1.08 202407:-1.11 202408:+1.32 202409:+2.55 202410:-0.97 202411:-0.37 202412:-1.99 202501:+0.15 202502:-0.34 202503:-1.07 202504:-0.58 202505:-0.27 202506:+2.83 202507:+2.66 202508:-0.26 202509:-1.85 202510:-1.83 202511:-0.94 202512:+0.00 202601:-1.76 202602:-0.96

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +0.05 | -1.98..+2.08 | 2.90 | +2,794 | 0.37 |
| 1 | 2264 | -1.66 | -3.50..+0.18 | 2.63 | -19,070 | 0.29 |
| 2 | 5854 | -0.72 | -1.83..+0.39 | 1.58 | -22,700 | 0.29 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | -1.29 | -5.67..+3.09 | 6.26 | -2,636 | 0.33 |
| VIX_mid | 6933 | -0.58 | -1.72..+0.56 | 1.62 | -18,883 | 0.31 |
| VIX_high | 3307 | -0.94 | -2.34..+0.46 | 2.00 | -17,456 | 0.30 |

## Breakdown: ogbm|lr0.2|phi0.999|pooled|m4|take

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | +0.63 | -0.61..+1.88 | 1.78 | +5,105 | 0.41 |
| HM | 2285 | +0.81 | -0.55..+2.17 | 1.94 | +4,954 | 0.41 |
| WT | 4265 | +0.40 | -0.25..+1.05 | 0.93 | +3,175 | 0.34 |
| KB | 3093 | -0.49 | -1.69..+0.71 | 1.71 | -2,090 | 0.40 |
| SM | 904 | -2.38 | -4.87..+0.10 | 3.56 | -4,253 | 0.49 |
| PE | 3049 | +0.97 | -0.17..+2.12 | 1.63 | +4,426 | 0.40 |
| PB | 2261 | +0.67 | -0.62..+1.97 | 1.85 | +4,067 | 0.37 |
| DN | 1762 | -0.16 | -1.75..+1.43 | 2.27 | -766 | 0.40 |
| MV | 2922 | +0.31 | -0.90..+1.51 | 1.72 | +2,397 | 0.40 |
| MA | 1093 | -2.02 | -4.27..+0.23 | 3.22 | -5,889 | 0.48 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.10 | -1.56..+1.76 | 2.37 | +904 | 0.36 |
| HM | 1008 | -0.74 | -2.72..+1.25 | 2.83 | -4,631 | 0.38 |
| WT | 1893 | -0.16 | -1.14..+0.81 | 1.39 | -1,345 | 0.34 |
| KB | 1374 | -0.89 | -2.57..+0.79 | 2.40 | -3,955 | 0.38 |
| SM | 363 | -1.63 | -5.30..+2.05 | 5.25 | -2,733 | 0.44 |
| PE | 1311 | -1.63 | -3.44..+0.19 | 2.60 | -7,464 | 0.39 |
| PB | 965 | -1.74 | -3.56..+0.07 | 2.59 | -10,516 | 0.33 |
| DN | 782 | -1.47 | -3.85..+0.91 | 3.40 | -7,195 | 0.39 |
| MV | 1253 | -0.20 | -2.09..+1.70 | 2.71 | -1,540 | 0.39 |
| MA | 474 | -0.56 | -3.79..+2.66 | 4.61 | -1,669 | 0.43 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -2.20 | -4.54..+0.13 | 3.33 | -7,350 | 0.39 |
| HM | 621 | -1.69 | -4.16..+0.79 | 3.54 | -4,871 | 0.39 |
| WT | 1112 | -1.84 | -3.03..-0.65 | 1.70 | -6,653 | 0.33 |
| KB | 765 | -0.36 | -2.64..+1.91 | 3.25 | -674 | 0.40 |
| SM | 320 | +0.11 | -3.54..+3.75 | 5.21 | +116 | 0.45 |
| PE | 727 | -1.50 | -3.87..+0.88 | 3.40 | -2,834 | 0.41 |
| PB | 595 | -0.77 | -3.36..+1.83 | 3.70 | -2,119 | 0.38 |
| DN | 530 | -1.32 | -4.19..+1.56 | 4.11 | -3,243 | 0.42 |
| MV | 732 | +0.49 | -1.95..+2.94 | 3.49 | +1,672 | 0.44 |
| MA | 368 | +1.05 | -2.42..+4.52 | 4.96 | +1,802 | 0.45 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.98 | -2.48..+0.51 | 2.14 | -14,726 | 0.39 |
| london | 5303 | +0.16 | -1.35..+1.68 | 2.16 | +3,495 | 0.43 |
| pre | 1479 | +3.19 | +0.52..+5.85 | 3.81 | +10,169 | 0.42 |
| nyam | 6580 | +0.05 | -1.25..+1.35 | 1.85 | +330 | 0.36 |
| nypm | 4901 | +0.83 | -0.75..+2.41 | 2.26 | +9,748 | 0.40 |
| close | 72 | +13.04 | +4.88..+21.20 | 11.66 | +2,108 | 0.51 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | -0.02 | -2.16..+2.13 | 3.06 | +2,510 | 0.38 |
| london | 2243 | -2.26 | -4.36..-0.15 | 3.01 | -26,446 | 0.36 |
| pre | 540 | -0.58 | -3.82..+2.66 | 4.62 | -2,053 | 0.32 |
| nyam | 3095 | -0.40 | -2.14..+1.34 | 2.48 | -6,613 | 0.35 |
| nypm | 1898 | -0.83 | -3.25..+1.59 | 3.46 | -7,496 | 0.42 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.911 | -4982.317 |
| 2024.0 | 14562.0 | 0.405 | 5891.09 |
| 2025.0 | 19687.0 | -0.338 | -6651.273 |
| 2026.0 | 2229.0 | -1.865 | -4157.49 |
**drift: monthly mean pts/trade** 202307:-0.24 202308:-0.85 202309:-1.97 202310:+0.48 202311:-0.57 202312:-3.32 202401:-1.40 202402:+0.07 202403:+0.99 202404:+3.11 202405:+0.74 202406:+1.65 202407:-0.86 202408:+1.20 202409:+2.48 202410:-1.42 202411:+0.23 202412:-2.41 202501:+0.68 202502:-1.32 202503:-1.49 202504:-0.39 202505:-0.73 202506:+2.60 202507:+3.59 202508:-0.65 202509:-2.25 202510:-1.99 202511:-1.14 202512:+0.68 202601:-2.06 202602:-1.38

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +0.68 | -1.49..+2.84 | 3.09 | +11,671 | 0.42 |
| 1 | 2264 | -2.05 | -4.20..+0.10 | 3.08 | -23,802 | 0.37 |
| 2 | 5854 | -0.92 | -2.23..+0.40 | 1.88 | -28,014 | 0.35 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | -0.39 | -5.18..+4.40 | 6.85 | -326 | 0.37 |
| VIX_mid | 6933 | -0.67 | -1.95..+0.61 | 1.83 | -21,257 | 0.37 |
| VIX_high | 3307 | -1.00 | -2.70..+0.70 | 2.43 | -18,561 | 0.37 |

## Breakdown: ogbm|lr0.2|phi0.999|pooled|m1|take

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | +0.68 | -0.66..+2.01 | 1.91 | +5,459 | 0.45 |
| HM | 2285 | +0.49 | -0.96..+1.93 | 2.07 | +2,961 | 0.46 |
| WT | 4265 | +0.19 | -0.50..+0.88 | 0.99 | +1,493 | 0.39 |
| KB | 3093 | -0.35 | -1.60..+0.91 | 1.80 | -1,488 | 0.44 |
| SM | 904 | -1.93 | -4.52..+0.66 | 3.70 | -3,443 | 0.54 |
| PE | 3049 | +1.49 | +0.26..+2.72 | 1.76 | +6,805 | 0.45 |
| PB | 2261 | +0.75 | -0.67..+2.16 | 2.02 | +4,511 | 0.43 |
| DN | 1762 | -0.19 | -1.85..+1.47 | 2.37 | -894 | 0.44 |
| MV | 2922 | -0.04 | -1.35..+1.27 | 1.87 | -338 | 0.44 |
| MA | 1093 | -2.50 | -4.91..-0.08 | 3.45 | -7,277 | 0.55 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | -0.20 | -1.96..+1.57 | 2.52 | -1,706 | 0.41 |
| HM | 1008 | -0.74 | -2.81..+1.32 | 2.95 | -4,686 | 0.43 |
| WT | 1893 | -0.02 | -1.07..+1.02 | 1.49 | -207 | 0.38 |
| KB | 1374 | -0.85 | -2.66..+0.95 | 2.58 | -3,817 | 0.44 |
| SM | 363 | -2.56 | -6.56..+1.43 | 5.71 | -4,305 | 0.51 |
| PE | 1311 | -2.29 | -4.22..-0.37 | 2.75 | -10,530 | 0.44 |
| PB | 965 | -2.01 | -4.00..-0.02 | 2.84 | -12,104 | 0.38 |
| DN | 782 | -2.28 | -4.84..+0.28 | 3.66 | -11,157 | 0.44 |
| MV | 1253 | -0.35 | -2.37..+1.67 | 2.89 | -2,761 | 0.45 |
| MA | 474 | +0.06 | -3.41..+3.53 | 4.96 | +173 | 0.50 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -2.44 | -4.96..+0.07 | 3.60 | -8,153 | 0.45 |
| HM | 621 | -2.08 | -4.75..+0.59 | 3.81 | -6,017 | 0.44 |
| WT | 1112 | -1.87 | -3.16..-0.59 | 1.83 | -6,782 | 0.38 |
| KB | 765 | -0.17 | -2.62..+2.29 | 3.50 | -307 | 0.46 |
| SM | 320 | +0.01 | -3.88..+3.90 | 5.55 | +11 | 0.51 |
| PE | 727 | -1.57 | -4.15..+1.01 | 3.68 | -2,971 | 0.47 |
| PB | 595 | -1.20 | -4.00..+1.60 | 4.00 | -3,309 | 0.44 |
| DN | 530 | -1.14 | -4.24..+1.96 | 4.43 | -2,801 | 0.48 |
| MV | 732 | +0.10 | -2.56..+2.75 | 3.79 | +323 | 0.49 |
| MA | 368 | +0.73 | -2.98..+4.44 | 5.30 | +1,243 | 0.51 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -1.22 | -2.79..+0.35 | 2.24 | -17,748 | 0.44 |
| london | 5303 | +0.14 | -1.51..+1.79 | 2.36 | +2,379 | 0.48 |
| pre | 1479 | +3.55 | +0.64..+6.47 | 4.17 | +11,080 | 0.46 |
| nyam | 6580 | +0.01 | -1.37..+1.38 | 1.97 | -1,325 | 0.41 |
| nypm | 4901 | +0.98 | -0.73..+2.69 | 2.44 | +11,053 | 0.45 |
| close | 72 | +14.61 | +6.73..+22.49 | 11.25 | +2,351 | 0.56 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | -0.43 | -2.73..+1.86 | 3.27 | -3,320 | 0.45 |
| london | 2243 | -2.54 | -4.75..-0.34 | 3.15 | -29,921 | 0.42 |
| pre | 540 | -1.06 | -5.08..+2.95 | 5.74 | -2,938 | 0.38 |
| nyam | 3095 | -0.45 | -2.33..+1.44 | 2.70 | -8,347 | 0.39 |
| nypm | 1898 | -0.75 | -3.36..+1.85 | 3.73 | -6,634 | 0.46 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -1.194 | -6527.562 |
| 2024.0 | 14562.0 | 0.404 | 5880.785 |
| 2025.0 | 19687.0 | -0.416 | -8198.262 |
| 2026.0 | 2229.0 | -2.085 | -4647.97 |
**drift: monthly mean pts/trade** 202307:-0.42 202308:-0.99 202309:-2.45 202310:+0.06 202311:-0.13 202312:-4.26 202401:-0.83 202402:-1.75 202403:+1.09 202404:+3.20 202405:+0.33 202406:+2.16 202407:-0.39 202408:+1.23 202409:+2.61 202410:-1.50 202411:+0.27 202412:-2.60 202501:+0.78 202502:-1.34 202503:-2.08 202504:+0.15 202505:-1.11 202506:+2.76 202507:+3.61 202508:+0.03 202509:-3.03 202510:-2.62 202511:-1.14 202512:+0.27 202601:-2.22 202602:-1.75

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +0.62 | -1.77..+3.00 | 3.41 | +11,275 | 0.48 |
| 1 | 2264 | -2.20 | -4.47..+0.06 | 3.23 | -25,170 | 0.42 |
| 2 | 5854 | -1.19 | -2.60..+0.21 | 2.01 | -37,205 | 0.40 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | -0.90 | -6.25..+4.46 | 7.65 | -1,830 | 0.42 |
| VIX_mid | 6933 | -0.96 | -2.33..+0.40 | 1.95 | -31,064 | 0.42 |
| VIX_high | 3307 | -0.95 | -2.78..+0.89 | 2.62 | -18,206 | 0.43 |

## Breakdown: bocpd_adapt|12m|1m|pooled

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | -0.09 | -0.91..+0.73 | 1.17 | -744 | 0.21 |
| HM | 2285 | +0.54 | -0.43..+1.50 | 1.38 | +3,265 | 0.23 |
| WT | 4265 | -0.39 | -0.77..-0.02 | 0.54 | -3,141 | 0.14 |
| KB | 3093 | +0.40 | -0.39..+1.19 | 1.13 | +1,697 | 0.21 |
| SM | 904 | -0.87 | -2.46..+0.73 | 2.28 | -1,545 | 0.23 |
| PE | 3049 | -0.11 | -0.91..+0.69 | 1.14 | -497 | 0.20 |
| PB | 2261 | -0.05 | -1.04..+0.94 | 1.41 | -292 | 0.23 |
| DN | 1762 | -0.67 | -1.76..+0.43 | 1.57 | -3,125 | 0.20 |
| MV | 2922 | -0.02 | -0.85..+0.81 | 1.19 | -192 | 0.21 |
| MA | 1093 | -1.16 | -2.65..+0.34 | 2.13 | -3,368 | 0.24 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| HM | 1008 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| WT | 1893 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| KB | 1374 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| SM | 363 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| PE | 1311 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| PB | 965 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| DN | 782 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| MV | 1253 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| MA | 474 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -0.61 | -2.76..+1.53 | 3.06 | -2,048 | 0.36 |
| HM | 621 | +0.20 | -2.21..+2.60 | 3.43 | +564 | 0.38 |
| WT | 1112 | +0.03 | -0.98..+1.05 | 1.45 | +118 | 0.25 |
| KB | 765 | -0.84 | -2.99..+1.32 | 3.08 | -1,546 | 0.35 |
| SM | 320 | +1.15 | -2.19..+4.48 | 4.76 | +1,264 | 0.39 |
| PE | 727 | +0.15 | -1.93..+2.24 | 2.98 | +285 | 0.35 |
| PB | 595 | +0.96 | -1.60..+3.51 | 3.65 | +2,651 | 0.39 |
| DN | 530 | -0.44 | -3.07..+2.20 | 3.76 | -1,074 | 0.38 |
| MV | 732 | +2.49 | +0.47..+4.52 | 2.89 | +8,493 | 0.36 |
| MA | 368 | -0.65 | -3.99..+2.68 | 4.77 | -1,121 | 0.39 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.27 | -1.50..+0.97 | 1.76 | -2,980 | 0.35 |
| london | 5303 | +0.38 | -0.60..+1.35 | 1.40 | +3,815 | 0.21 |
| pre | 1479 | -0.47 | -2.12..+1.19 | 2.37 | -1,229 | 0.15 |
| nyam | 6580 | -0.33 | -0.91..+0.24 | 0.82 | -5,561 | 0.11 |
| nypm | 4901 | -0.18 | -0.88..+0.52 | 1.00 | -2,411 | 0.14 |
| close | 72 | +3.18 | -0.03..+6.38 | 4.58 | +423 | 0.15 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| london | 2243 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| pre | 540 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| nyam | 3095 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| nypm | 1898 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | 0.008 | 41.944 |
| 2024.0 | 14562.0 | 0.214 | 3118.052 |
| 2025.0 | 19687.0 | -0.25 | -4927.385 |
| 2026.0 | 2229.0 | 0.0 | 0.0 |
**drift: monthly mean pts/trade** 202307:-1.61 202308:+0.52 202309:+0.28 202310:-0.94 202311:+2.68 202312:-0.41 202401:+1.41 202402:-0.50 202403:-0.19 202404:+1.50 202405:-0.83 202406:-0.21 202407:-0.18 202408:+0.53 202409:+0.28 202410:+1.74 202411:-0.35 202412:-1.42 202501:-1.92 202502:+0.00 202503:-0.49 202504:-0.23 202505:+0.00 202506:+0.00 202507:+0.00 202508:+0.00 202509:+0.00 202510:+0.00 202511:+0.00 202512:+0.00 202601:+0.00 202602:+0.00

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| 1 | 2264 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| 2 | 5854 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| VIX_mid | 6933 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| VIX_high | 3307 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |

## Breakdown: bocpd_fixed|17|{'hz': 1, 'p': 2, 'X': 2}

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | -0.33 | -1.15..+0.50 | 1.18 | -2,618 | 0.21 |
| HM | 2285 | +0.84 | -0.13..+1.82 | 1.39 | +5,137 | 0.24 |
| WT | 4265 | -0.22 | -0.58..+0.14 | 0.51 | -1,767 | 0.14 |
| KB | 3093 | +0.30 | -0.50..+1.11 | 1.15 | +1,303 | 0.21 |
| SM | 904 | -0.68 | -2.28..+0.92 | 2.29 | -1,218 | 0.24 |
| PE | 3049 | +0.14 | -0.66..+0.94 | 1.14 | +653 | 0.21 |
| PB | 2261 | +0.15 | -0.85..+1.14 | 1.42 | +880 | 0.25 |
| DN | 1762 | -0.58 | -1.70..+0.53 | 1.59 | -2,732 | 0.21 |
| MV | 2922 | -0.09 | -0.93..+0.75 | 1.20 | -673 | 0.22 |
| MA | 1093 | -0.73 | -2.21..+0.74 | 2.11 | -2,139 | 0.25 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | -0.12 | -1.22..+0.99 | 1.58 | -1,013 | 0.19 |
| HM | 1008 | +0.03 | -1.33..+1.38 | 1.93 | +170 | 0.19 |
| WT | 1893 | +0.06 | -0.45..+0.57 | 0.73 | +479 | 0.12 |
| KB | 1374 | -0.79 | -1.93..+0.34 | 1.62 | -3,542 | 0.19 |
| SM | 363 | -1.28 | -3.83..+1.27 | 3.65 | -2,152 | 0.24 |
| PE | 1311 | -0.96 | -2.16..+0.23 | 1.71 | -4,420 | 0.19 |
| PB | 965 | -0.21 | -1.60..+1.18 | 1.99 | -1,246 | 0.19 |
| DN | 782 | -0.82 | -2.54..+0.90 | 2.45 | -4,001 | 0.22 |
| MV | 1253 | -0.14 | -1.30..+1.02 | 1.66 | -1,091 | 0.19 |
| MA | 474 | -1.66 | -4.05..+0.72 | 3.41 | -4,924 | 0.26 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -0.46 | -2.18..+1.26 | 2.46 | -1,548 | 0.24 |
| HM | 621 | +0.06 | -1.86..+1.98 | 2.75 | +173 | 0.26 |
| WT | 1112 | +0.05 | -0.73..+0.83 | 1.11 | +196 | 0.16 |
| KB | 765 | -0.56 | -2.23..+1.11 | 2.38 | -1,033 | 0.23 |
| SM | 320 | +1.02 | -1.59..+3.63 | 3.73 | +1,125 | 0.27 |
| PE | 727 | +0.01 | -1.70..+1.71 | 2.44 | +13 | 0.25 |
| PB | 595 | -0.31 | -2.40..+1.78 | 2.99 | -853 | 0.27 |
| DN | 530 | +0.01 | -2.17..+2.20 | 3.13 | +36 | 0.27 |
| MV | 732 | +1.04 | -0.64..+2.72 | 2.40 | +3,551 | 0.26 |
| MA | 368 | -0.18 | -2.85..+2.48 | 3.80 | -316 | 0.26 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.42 | -1.70..+0.86 | 1.83 | -5,516 | 0.38 |
| london | 5303 | +0.59 | -0.39..+1.58 | 1.40 | +5,923 | 0.22 |
| pre | 1479 | -0.52 | -2.14..+1.11 | 2.32 | -1,211 | 0.15 |
| nyam | 6580 | -0.05 | -0.61..+0.50 | 0.79 | -1,592 | 0.11 |
| nypm | 4901 | -0.12 | -0.74..+0.50 | 0.89 | -1,283 | 0.13 |
| close | 72 | +3.30 | +0.26..+6.34 | 4.34 | +504 | 0.17 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | +0.61 | -0.92..+2.14 | 2.19 | +12,008 | 0.28 |
| london | 2243 | -1.34 | -2.82..+0.14 | 2.12 | -14,350 | 0.22 |
| pre | 540 | +1.01 | -0.92..+2.94 | 2.76 | +2,458 | 0.14 |
| nyam | 3095 | -0.40 | -1.22..+0.43 | 1.18 | -7,185 | 0.11 |
| nypm | 1898 | -1.44 | -2.51..-0.37 | 1.53 | -14,237 | 0.13 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.105 | -576.436 |
| 2024.0 | 14562.0 | 0.233 | 3393.448 |
| 2025.0 | 19687.0 | -0.415 | -8164.224 |
| 2026.0 | 2229.0 | -0.045 | -101.17 |
**drift: monthly mean pts/trade** 202307:-2.33 202308:+0.14 202309:+1.29 202310:-1.25 202311:+3.04 202312:-0.97 202401:+0.75 202402:-0.95 202403:+0.32 202404:+1.06 202405:+0.46 202406:-0.63 202407:-0.32 202408:+0.92 202409:-0.08 202410:+1.49 202411:+0.32 202412:-1.25 202501:-1.92 202502:+1.27 202503:-0.49 202504:-0.23 202505:-0.45 202506:+0.18 202507:+0.54 202508:-0.80 202509:-1.21 202510:-0.89 202511:-1.18 202512:+0.74 202601:+0.36 202602:-1.06

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | -0.16 | -1.65..+1.33 | 2.13 | -1,580 | 0.27 |
| 1 | 2264 | -0.78 | -2.25..+0.70 | 2.10 | -7,644 | 0.21 |
| 2 | 5854 | -0.42 | -1.14..+0.30 | 1.02 | -12,517 | 0.13 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | -0.11 | -3.70..+3.47 | 5.12 | +442 | 0.29 |
| VIX_mid | 6933 | -0.41 | -1.20..+0.37 | 1.12 | -14,487 | 0.20 |
| VIX_high | 3307 | -0.52 | -1.52..+0.48 | 1.43 | -7,697 | 0.14 |

## Breakdown: btab|disc1.0|pooled|z1|m8|take

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| HM | 2285 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| WT | 4265 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| KB | 3093 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| SM | 904 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| PE | 3049 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| PB | 2261 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| DN | 1762 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| MV | 2922 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| MA | 1093 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| HM | 1008 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| WT | 1893 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| KB | 1374 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| SM | 363 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| PE | 1311 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| PB | 965 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| DN | 782 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| MV | 1253 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| MA | 474 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -0.09 | -0.40..+0.21 | 0.44 | -313 | 0.01 |
| HM | 621 | +0.08 | -0.35..+0.51 | 0.62 | +225 | 0.01 |
| WT | 1112 | -0.12 | -0.31..+0.08 | 0.28 | -417 | 0.01 |
| KB | 765 | -0.16 | -0.60..+0.27 | 0.62 | -300 | 0.01 |
| SM | 320 | -0.14 | -0.64..+0.36 | 0.72 | -158 | 0.01 |
| PE | 727 | +0.09 | -0.26..+0.44 | 0.50 | +174 | 0.01 |
| PB | 595 | -0.06 | -0.48..+0.36 | 0.60 | -163 | 0.01 |
| DN | 530 | -0.33 | -0.92..+0.27 | 0.85 | -808 | 0.01 |
| MV | 732 | -0.19 | -0.55..+0.16 | 0.51 | -651 | 0.01 |
| MA | 368 | +0.34 | -0.04..+0.72 | 0.55 | +579 | 0.01 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| london | 5303 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| pre | 1479 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| nyam | 6580 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| nypm | 4901 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| close | 72 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| london | 2243 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| pre | 540 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| nyam | 3095 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| nypm | 1898 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.087 | -474.325 |
| 2024.0 | 14562.0 | 0.0 | 0.0 |
| 2025.0 | 19687.0 | 0.0 | 0.0 |
| 2026.0 | 2229.0 | 0.0 | 0.0 |
**drift: monthly mean pts/trade** 202307:-0.57 202308:+0.00 202309:+0.00 202310:+0.00 202311:+0.00 202312:+0.00 202401:+0.00 202402:+0.00 202403:+0.00 202404:+0.00 202405:+0.00 202406:+0.00 202407:+0.00 202408:+0.00 202409:+0.00 202410:+0.00 202411:+0.00 202412:+0.00 202501:+0.00 202502:+0.00 202503:+0.00 202504:+0.00 202505:+0.00 202506:+0.00 202507:+0.00 202508:+0.00 202509:+0.00 202510:+0.00 202511:+0.00 202512:+0.00 202601:+0.00 202602:+0.00

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| 1 | 2264 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| 2 | 5854 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| VIX_mid | 6933 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| VIX_high | 3307 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |

## Breakdown: cusum_adapt|12m|1m|pooled

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | -0.23 | -1.01..+0.56 | 1.12 | -1,826 | 0.17 |
| HM | 2285 | -0.09 | -0.99..+0.81 | 1.28 | -543 | 0.19 |
| WT | 4265 | -0.19 | -0.60..+0.21 | 0.58 | -1,552 | 0.14 |
| KB | 3093 | -0.19 | -0.99..+0.61 | 1.14 | -806 | 0.18 |
| SM | 904 | -0.19 | -1.64..+1.25 | 2.07 | -346 | 0.19 |
| PE | 3049 | -0.37 | -1.12..+0.38 | 1.07 | -1,673 | 0.17 |
| PB | 2261 | +0.50 | -0.44..+1.44 | 1.35 | +3,014 | 0.20 |
| DN | 1762 | -0.25 | -1.27..+0.78 | 1.46 | -1,153 | 0.18 |
| MV | 2922 | -0.72 | -1.52..+0.08 | 1.14 | -5,600 | 0.17 |
| MA | 1093 | -1.13 | -2.60..+0.34 | 2.09 | -3,297 | 0.20 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| HM | 1008 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| WT | 1893 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| KB | 1374 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| SM | 363 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| PE | 1311 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| PB | 965 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| DN | 782 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| MV | 1253 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| MA | 474 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -1.42 | -3.90..+1.06 | 3.54 | -4,723 | 0.47 |
| HM | 621 | -0.01 | -2.72..+2.70 | 3.87 | -33 | 0.47 |
| WT | 1112 | -0.49 | -1.64..+0.65 | 1.64 | -1,791 | 0.35 |
| KB | 765 | +0.79 | -1.54..+3.12 | 3.32 | +1,465 | 0.46 |
| SM | 320 | -1.83 | -5.64..+1.98 | 5.44 | -2,017 | 0.46 |
| PE | 727 | -0.39 | -2.75..+1.98 | 3.38 | -733 | 0.46 |
| PB | 595 | -0.84 | -3.70..+2.02 | 4.09 | -2,322 | 0.50 |
| DN | 530 | -0.54 | -3.66..+2.59 | 4.46 | -1,323 | 0.50 |
| MV | 732 | +0.11 | -2.38..+2.59 | 3.55 | +359 | 0.48 |
| MA | 368 | -2.91 | -6.61..+0.80 | 5.29 | -4,974 | 0.46 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -0.22 | -1.30..+0.85 | 1.54 | -2,375 | 0.24 |
| london | 5303 | -0.06 | -0.92..+0.80 | 1.23 | -116 | 0.15 |
| pre | 1479 | -0.60 | -2.27..+1.07 | 2.38 | -1,837 | 0.16 |
| nyam | 6580 | -0.40 | -1.17..+0.37 | 1.10 | -6,161 | 0.15 |
| nypm | 4901 | -0.19 | -1.00..+0.62 | 1.16 | -3,170 | 0.14 |
| close | 72 | -1.20 | -4.06..+1.66 | 4.08 | -124 | 0.10 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| london | 2243 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| pre | 540 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| nyam | 3095 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| nypm | 1898 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.904 | -4941.447 |
| 2024.0 | 14562.0 | -0.337 | -4904.069 |
| 2025.0 | 19687.0 | 0.0 | 0.0 |
| 2026.0 | 2229.0 | 0.0 | 0.0 |
**drift: monthly mean pts/trade** 202307:-2.09 202308:+0.28 202309:-0.12 202310:-0.65 202311:-1.70 202312:-2.26 202401:+1.31 202402:-3.35 202403:-1.40 202404:+0.00 202405:-0.99 202406:+0.00 202407:+0.00 202408:+0.05 202409:-0.34 202410:+1.48 202411:-0.97 202412:-1.22 202501:+0.00 202502:+0.00 202503:+0.00 202504:+0.00 202505:+0.00 202506:+0.00 202507:+0.00 202508:+0.00 202509:+0.00 202510:+0.00 202511:+0.00 202512:+0.00 202601:+0.00 202602:+0.00

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| 1 | 2264 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| 2 | 5854 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| VIX_mid | 6933 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |
| VIX_high | 3307 | +0.00 | +0.00..+0.00 | 0.00 | +0 | 0.00 |

## Breakdown: cusum_fixed|23|{'X': 1, 'k': 2, 'h': 3}

**by book, PRE**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 3020 | -1.04 | -2.10..+0.01 | 1.51 | -8,391 | 0.29 |
| HM | 2285 | -0.37 | -1.54..+0.79 | 1.66 | -2,278 | 0.30 |
| WT | 4265 | -0.41 | -0.91..+0.09 | 0.72 | -3,285 | 0.22 |
| KB | 3093 | -0.26 | -1.24..+0.72 | 1.40 | -1,124 | 0.29 |
| SM | 904 | -0.51 | -2.43..+1.41 | 2.74 | -907 | 0.30 |
| PE | 3049 | -0.25 | -1.27..+0.77 | 1.46 | -1,119 | 0.29 |
| PB | 2261 | +0.49 | -0.73..+1.72 | 1.75 | +2,974 | 0.33 |
| DN | 1762 | -0.82 | -2.16..+0.52 | 1.92 | -3,850 | 0.29 |
| MV | 2922 | -0.59 | -1.62..+0.44 | 1.47 | -4,613 | 0.30 |
| MA | 1093 | -0.38 | -2.20..+1.44 | 2.60 | -1,099 | 0.31 |
**by book, HOLD**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 1382 | +0.12 | -1.35..+1.59 | 2.11 | +1,033 | 0.27 |
| HM | 1008 | -0.84 | -2.43..+0.76 | 2.28 | -5,277 | 0.24 |
| WT | 1893 | +0.10 | -0.64..+0.85 | 1.07 | +858 | 0.20 |
| KB | 1374 | -0.43 | -1.80..+0.94 | 1.96 | -1,924 | 0.26 |
| SM | 363 | -2.16 | -5.27..+0.96 | 4.45 | -3,620 | 0.30 |
| PE | 1311 | -0.02 | -1.53..+1.49 | 2.15 | -94 | 0.27 |
| PB | 965 | -1.42 | -3.15..+0.31 | 2.47 | -8,572 | 0.26 |
| DN | 782 | -1.37 | -3.28..+0.55 | 2.74 | -6,691 | 0.26 |
| MV | 1253 | -0.92 | -2.47..+0.63 | 2.22 | -7,231 | 0.26 |
| MA | 474 | -2.67 | -5.40..+0.06 | 3.90 | -7,917 | 0.33 |
**by book, X**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| ST | 717 | -0.43 | -2.28..+1.43 | 2.65 | -1,424 | 0.26 |
| HM | 621 | -0.31 | -2.29..+1.68 | 2.83 | -894 | 0.26 |
| WT | 1112 | +0.25 | -0.57..+1.08 | 1.18 | +919 | 0.16 |
| KB | 765 | +0.19 | -1.55..+1.93 | 2.49 | +356 | 0.25 |
| SM | 320 | -0.22 | -3.12..+2.68 | 4.14 | -243 | 0.27 |
| PE | 727 | +0.27 | -1.55..+2.10 | 2.61 | +518 | 0.26 |
| PB | 595 | -0.22 | -2.42..+1.97 | 3.14 | -617 | 0.28 |
| DN | 530 | +0.52 | -1.53..+2.58 | 2.93 | +1,293 | 0.25 |
| MV | 732 | -0.32 | -2.20..+1.57 | 2.69 | -1,073 | 0.27 |
| MA | 368 | -1.25 | -4.16..+1.66 | 4.16 | -2,142 | 0.29 |
**by entry session, PRE|HOLD**

PRE:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 6319 | -1.12 | -2.55..+0.30 | 2.03 | -16,325 | 0.41 |
| london | 5303 | +0.20 | -1.08..+1.47 | 1.82 | +2,021 | 0.27 |
| pre | 1479 | -1.93 | -4.09..+0.23 | 3.09 | -5,612 | 0.27 |
| nyam | 6580 | -0.16 | -1.04..+0.72 | 1.26 | -2,719 | 0.23 |
| nypm | 4901 | -0.14 | -1.08..+0.80 | 1.35 | -1,957 | 0.21 |
| close | 72 | +5.55 | +0.70..+10.40 | 6.92 | +900 | 0.22 |
HOLD:

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| asia | 3004 | -0.29 | -1.96..+1.37 | 2.38 | -2,015 | 0.28 |
| london | 2243 | -1.54 | -3.30..+0.22 | 2.51 | -18,526 | 0.25 |
| pre | 540 | +1.92 | -1.29..+5.12 | 4.58 | +4,773 | 0.27 |
| nyam | 3095 | -0.57 | -2.06..+0.92 | 2.13 | -12,456 | 0.25 |
| nypm | 1898 | -0.89 | -2.43..+0.65 | 2.20 | -11,095 | 0.22 |
**by year**

| year | count | mean | sum |
|---|---|---|---|
| 2023.0 | 5468.0 | -0.409 | -2238.886 |
| 2024.0 | 14562.0 | -0.163 | -2367.374 |
| 2025.0 | 19687.0 | -0.713 | -14041.333 |
| 2026.0 | 2229.0 | 0.521 | 1160.365 |
**drift: monthly mean pts/trade** 202307:-1.35 202308:-0.63 202309:+0.39 202310:-0.09 202311:+1.78 202312:-2.87 202401:+1.72 202402:-3.15 202403:-2.05 202404:+0.60 202405:+1.00 202406:-0.32 202407:+0.24 202408:+0.45 202409:-0.55 202410:+0.28 202411:+0.12 202412:-1.37 202501:-0.90 202502:+0.78 202503:-0.54 202504:-0.22 202505:-2.40 202506:-0.02 202507:+2.23 202508:-3.18 202509:-3.20 202510:-1.79 202511:-0.08 202512:+0.10 202601:+0.88 202602:-0.37

**regime (vol_tag, PRE+HOLD)**

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| 0 | 2687 | -0.77 | -2.44..+0.89 | 2.37 | -10,419 | 0.31 |
| 1 | 2264 | -1.86 | -3.82..+0.10 | 2.81 | -22,152 | 0.28 |
| 2 | 5854 | -0.08 | -1.06..+0.91 | 1.41 | -6,865 | 0.22 |

(VIX tercile)

| group | n | pts/trade | 95% CI | MDE | $/wk | exit rate |
|---|---|---|---|---|---|---|
| VIX_low | 565 | -0.98 | -4.89..+2.93 | 5.58 | -3,291 | 0.28 |
| VIX_mid | 6933 | -0.94 | -1.93..+0.06 | 1.42 | -36,522 | 0.27 |
| VIX_high | 3307 | +0.09 | -1.29..+1.47 | 1.97 | +378 | 0.22 |

# Drift of the online ridge (rls lam 0.998 pooled): top-6 features by |standardised coefficient|, snapshot at each quarter end

## side P

| snapshot | top features (coef x50 pts per SD) |
|---|---|
| 2023-07 | bias +20.7, se_london -12.4, bk_ST +12.3, pct -12.1, se_nyam +12.1, mfe_R -11.8 |
| 2023-10 | se_nypm +14.1, pct -12.3, mod_cos +10.3, dist_tgt_R -9.9, mins +7.5, dd_mfe_pct -6.2 |
| 2024-01 | mod_cos -12.1, se_pre +11.6, pct -10.6, dd_mfe_pct -9.1, se_nyam -9.0, dd_mfe +7.2 |
| 2024-04 | pct -15.3, bias -12.4, mfe_R +10.3, pulled_sup10 -8.0, recov_pts +8.0, bk_ST -7.6 |
| 2024-07 | bias -26.0, mod_cos -14.6, se_pre +13.1, recov_pts +9.9, z_vwap_eth -9.4, pct -8.8 |
| 2024-10 | bk_ST +18.8, pct -13.5, mins +12.8, bk_MV +12.7, se_nypm +11.5, se_close +10.6 |
| 2025-01 | se_nyam +20.8, bias -20.3, pct -18.7, se_pre +14.2, se_close -13.3, bk_PE +13.1 |
| 2025-04 | bk_ST +31.9, mfe_R +15.0, pct -13.3, pulled_opp10 -12.8, se_pre +12.7, mod_cos -10.3 |
| 2025-07 | bias +34.4, se_pre -22.2, bk_ST -15.7, se_nypm -10.7, dd_mfe_pct -9.8, dd_mfe +9.2 |
| 2025-10 | pct -13.3, se_nypm -13.2, mins +11.6, se_nyam +9.2, dist_tgt_R -9.0, mae_R -7.0 |
| 2026-01 | bias -11.2, se_pre +10.4, se_london +9.7, bk_PE -9.6, mod_cos -8.6, pct -8.0 |

## side L

| snapshot | top features (coef x50 pts per SD) |
|---|---|
| 2023-07 | bk_ST +15.3, se_nyam +10.9, stk_n_opp +10.7, bk_DN +9.4, vol_lo -9.3, z_vwap_eth +9.0 |
| 2023-10 | bias -17.2, se_close -14.1, se_london +11.8, dd_mfe -9.6, se_nypm +9.0, bk_PE -8.5 |
| 2024-01 | se_nyam -15.4, se_london +11.0, mod_cos -10.3, stk_n_opp +10.2, sec_uw -7.7, stk_n_same +6.9 |
| 2024-04 | bk_ST -8.9, es_move_atr +7.8, d_sess_behind -7.7, stk_n_opp +7.0, bk_WT -6.6, se_london -6.6 |
| 2024-07 | bias -17.8, mod_cos -13.8, se_pre +11.9, d_sess_behind +11.0, se_nyam -10.8, z_vwap_eth -10.6 |
| 2024-10 | bias -23.6, bk_ST +15.8, se_nypm +12.4, se_london +11.9, se_pre +11.5, dd_mfe -10.3 |
| 2025-01 | bias -33.2, se_nyam +23.7, se_pre +21.0, se_nypm +15.6, se_close -13.0, bk_ST +12.5 |
| 2025-04 | bk_ST +37.5, se_pre +28.8, se_london +16.5, es_move_atr -10.4, bk_MV +10.2, mod_sin -10.1 |
| 2025-07 | bk_ST -30.4, bias +16.1, se_nypm -13.8, bk_PE +12.7, se_close -10.5, se_pre -10.5 |
| 2025-10 | se_london +20.6, se_nypm -15.7, mae_R -10.9, mod_cos -10.1, se_pre +9.3, rty_move_atr -8.2 |
| 2026-01 | bk_ST +15.1, bk_DN +13.5, se_nypm +11.2, se_asia +10.6, vol_lo -8.7, vol_hi -8.6 |

