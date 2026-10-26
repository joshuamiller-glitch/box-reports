# DS3 T-ENTRY: entry-signal search into the fixed DS2 bracket (D3E)

Generated 2026-10-26T15:54:55Z. Research only; no execution-server/chart/live change.

## 1. Verdict

191 cells in 8 preregs (TE1 30, TE1B 25, TE2 30, TE3 30, TE4 25, TE5 15 = 155 first-pass cells; TE6 9 + TE7 27 = 36 widening cells), ledger +191. First-pass mapped verdicts: 1 PASS, 5 CANDIDATE of 155 (TE1_st_10m; kelt_3m, emax_5m, boll_3m, ice_follow x2), the other 149 DEAD; best-of-155 reported as such. 38 cells (every non-DEAD mapped cell + top 20 by mapped holdout Sharpe) were re-run by DIRECT L2 replay: 6 PASS, 14 CANDIDATE, 18 DEAD after direct pricing.

**Headline.** (1) Only bar-based trend entries survive: the 10-minute Supertrend (ATR 10 x 3.0 and its 3x3 neighbourhood: 4 of 9 PASS or CANDIDATE after direct pricing) and one EMA 30/50 5-minute cross are PASS; the 3-minute Keltner/Bollinger break entries have the largest weekly means (WF $10-17k/wk at 10 lots) but all but one fail the never-scored 2023-04..2024-01 span (negative), so they are CANDIDATE at best. (2) No tape-based entry (sweep-and-reclaim, absorption, aggressor bursts, delta divergence, cumulative-delta breakouts, large prints, VPIN, book imbalance, queue depletion, iceberg refills, OFI, microprice tilt) is a PASS; four tape cells looked strong on WF-PRE (OFI bursts, VPIN n50) but failed the holdout/second span; two iceberg-follow cells are CANDIDATE (WF CI includes 0, 7-18 trades/wk). The tape result agrees with PRED block B (gate AUC 0.50-0.54). (3) Structure entries (prior-day, overnight, VWAP-band, ORB by session) are DEAD (ORB NY 15 is positive on PRE and fails the holdout). (4) MBO seven as entries into the 60-pt/1R bracket: DEAD (all 15 cells; the reversed-direction controls are not better). (5) **Paired vs ST10 and HM10: no entry beats ST/HM on a paired basis.** Per-trade paired differences vs ST are <= 0 or CI includes 0 for every PASS/CANDIDATE (only 20-30% of trades overlap an ST trade within 15 min; paired MDE 3.5-8 pts/trade). The PASS entries are new, nearly uncorrelated books (weekly corr to ST10 0.03-0.09, to HM10 -0.06..0.23 for the ST10m/EMA cells), not better entries for ST/HM.

Power: every predicted effect (+0.3 pt/trade, ~$1.5k/wk) is BELOW the MDE (standalone weekly MDE $8-13k/wk on 143 WF weeks, $11-18k on PRE; per-trade ~3 pts; paired ~3.5-13 pts), so these are screens: verdicts rest on sign agreement across three windows, the timing-destroyed placebo and cost stress, not on a power-established effect. DSR (n_trials = 191, sr_var 0.0025) is 0.56-0.96 for the PASS cells; with the full 31k-trial ledger as n it is near 0 (CONFIRMED tier not reached for any cell).

## 2. Method (fixed bracket, mapped vs direct)

Entry signal on a completed bar -> entry at the open of the next 1-min bar -> DS2 bracket (60-pt stop, 1.0R = 60-pt target, flat 16:55 ET), one trade at a time per book, signals blocked 15:00-17:59 ET, entry blocks 18:00-18:05 / 15:00-16:54, 10 lots as S10x1 slices with XJ stop-join, per-book locks (day -2R/+5R, give-back 2R keep 50%, week floor 12R, R = $12,000), commission $4.84 RT, all in the exact 1-s mark-to-market lock engine (firmlib.Ctx.run). The row builder is the ST/HM builder (firmlib.sim_rrt): regenerated ST (8,309) and HM (6,311) rows equal ROWS_bench3 to the trade. Rows are MAPPED when priced by year x exit-type P9 corrections (screening); every cell in sections 3-4 is DIRECT: exec_engine_l2 replay on raw mbp-10 (45 months, 88,155 unique trades, prop queue model, 5 ms latency, S10x1 at 2 s gaps + XJ 3 s touch-join on stop exits; bracket 240 ticks from each fill), coverage 100% of trades. Mapping bias seen: ST10 mapped vs true P9 PRE -1.5k/wk, HM10 +3.9k/wk; direct vs mapped WF for the PASS cells: -0.1k to -2.4k/wk (ST10m n14: 9.4k -> 7.0k). Not replayed: the 20-pt catastrophe stop and the cross-book join skip rule of the live P9 policy (single-book standalone), WT. Truncation-invariance audit (te_trunc.py, 58 cells, data cut at 62%): events identical except 1 prior-day-break event at the cutoff (benign: missing-value alignment of the previous session's RTH range, no future data). Windows: WF-PRE 2024-02..2025-06 (selection), holdout 2025-07+ (one logged look per prereg group, 8 looks), second holdout 2023-04..2024-01 (looked at together; no parameter was fitted anywhere). Verdict (object = signal): trades/wk>=3, PRE mean>0, WF weekly CI excludes 0, holdout>0, second span>0, timing-destroyed placebo (40 draws, same count/side/hour mix) rank >= 0.95 on PRE, 2x-cost WF>0; PASS = all, CANDIDATE = one failure. The D3C random-library pool (pool.parquet) did not exist: equal-count random library placebo not run.

## 3. Top 20 entries (DIRECT L2 basis, 10 lots) beside ST10 and HM10

Ranked by direct holdout (2025-07+) Sharpe among tpw>=3 cells (duplicate series collapsed: TE1_st_10m = TE6_st10m_n10_m3.0, TE1B_boll_3m = TE7_boll3m_n20_m2.0, TE1_kelt_3m = TE7_kelt3m_n20_m1.5, TE1B_emax_5m = TE7_emax5m_f20_s50). All 20 are NT8-deliverable (bars). Only 38 cells had a direct replay, so the list is the top of the 38, which were chosen by mapped PRE/holdout - read as best-of-191.

| # | cell | flag | verdict (direct) | tr/wk | win | avg win $ | avg loss $ | WF $/wk | hold $/wk | 2023 span $/wk | hold Sharpe | corr ST | corr HM | paired vs ST pts/trade [CI] (MDE, n pairs) | dWK vs ST $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| - | **ST10 (DS2, true P9)** | live | benchmark | 26.1 |  |  |  | 14,512 | 16,768 | 6,055 | 1.98 | | | | |
| - | **HM10 (DS2, true P9)** | live | benchmark | 23.9 |  |  |  | 9,785 | 10,038 | 3,808 | 1.29 | | | | |
| 1 | TE1_kelt_10m | NT8-bars | DEAD | 19.7 | 0.52 | 11,249 | -11,033 | 9,377 | 17,785 | -1,925 | 2.59 | 0.38 | 0.37 | -10.8 [-14.7,-6.9] (5.4, 574) | -5,135 |
| 2 | TE7_emax5m_f30_s50 | NT8-bars | PASS | 11.8 | 0.53 | 11,245 | -11,276 | 7,142 | 9,150 | 1,349 | 1.89 | 0.07 | 0.23 | 1.0 [-4.3,6.0] (7.1, 268) | -7,370 |
| 3 | TE6_st10m_n7_m3.0 | NT8-bars | PASS | 12.2 | 0.53 | 11,184 | -11,309 | 8,749 | 8,628 | 3,468 | 1.84 | 0.09 | -0.03 | -2.3 [-7.9,3.7] (8.2, 278) | -5,763 |
| 4 | TE7_kelt3m_n20_m1.0 | NT8-bars | CANDIDATE | 26.4 | 0.52 | 11,231 | -10,836 | 17,235 | 15,580 | -6,667 | 1.84 | 0.19 | 0.17 | -2.5 [-5.1,0.3] (3.9, 942) | 2,724 |
| 5 | TE7_kelt3m_n30_m1.0 | NT8-bars | CANDIDATE | 25.1 | 0.51 | 11,275 | -10,845 | 13,603 | 14,489 | -11,612 | 1.83 | 0.32 | 0.26 | -3.4 [-6.2,-0.7] (4.0, 871) | -908 |
| 6 | TE7_boll3m_n20_m1.5 | NT8-bars | CANDIDATE | 25.8 | 0.51 | 11,287 | -10,916 | 10,602 | 13,009 | -8,783 | 1.68 | 0.16 | 0.30 | -7.6 [-10.5,-4.4] (4.2, 738) | -3,910 |
| 7 | TE6_st10m_n10_m3.0 | NT8-bars | PASS | 12.1 | 0.54 | 11,133 | -11,341 | 8,799 | 8,477 | 9,914 | 1.54 | 0.03 | -0.06 | -3.6 [-9.6,1.9] (8.3, 262) | -5,712 |
| 8 | TE1_don_15m | NT8-bars | DEAD | 18.7 | 0.51 | 11,149 | -11,130 | 5,479 | 10,620 | -3,531 | 1.44 | 0.43 | 0.44 | -6.1 [-10.1,-2.7] (5.2, 564) | -9,032 |
| 9 | TE7_kelt3m_n14_m1.0 | NT8-bars | PASS | 26.8 | 0.52 | 11,302 | -10,858 | 16,863 | 12,885 | 6,365 | 1.37 | 0.33 | 0.33 | -5.0 [-7.4,-2.5] (3.5, 900) | 2,352 |
| 10 | TE7_kelt3m_n14_m2.0 | NT8-bars | DEAD | 21.0 | 0.51 | 11,270 | -11,026 | 8,565 | 10,198 | -2,769 | 1.36 | 0.36 | 0.29 | -16.4 [-21.3,-11.8] (6.3, 586) | -5,947 |
| 11 | TE6_st10m_n14_m2.5 | NT8-bars | DEAD | 14.6 | 0.52 | 11,148 | -10,986 | 7,373 | 7,834 | 5,850 | 1.31 | 0.16 | 0.07 | -0.1 [-5.4,5.6] (7.9, 284) | -7,138 |
| 12 | TE1_kelt_5m | NT8-bars | DEAD | 23.8 | 0.50 | 11,248 | -10,946 | 5,685 | 11,048 | -3,413 | 1.30 | 0.29 | 0.24 | -9.8 [-13.0,-6.8] (4.5, 701) | -8,826 |
| 13 | TE4_vwb_k2_all | NT8-bars | DEAD | 19.5 | 0.51 | 11,300 | -11,174 | 4,363 | 8,856 | -9,552 | 1.24 | 0.29 | 0.33 | -8.9 [-12.4,-5.4] (4.8, 656) | -10,149 |
| 14 | TE6_st10m_n14_m3.0 | NT8-bars | PASS | 12.2 | 0.53 | 11,165 | -11,241 | 6,980 | 6,172 | 6,761 | 1.15 | 0.07 | 0.05 | -1.2 [-6.8,4.9] (8.2, 255) | -7,532 |
| 15 | TE7_boll3m_n20_m2.0 | NT8-bars | CANDIDATE | 24.7 | 0.51 | 11,253 | -10,887 | 10,405 | 10,395 | -11,681 | 1.10 | 0.26 | 0.15 | -8.7 [-12.1,-5.3] (5.1, 661) | -4,107 |
| 16 | TE6_st10m_n10_m3.5 | NT8-bars | CANDIDATE | 10.7 | 0.53 | 11,208 | -11,352 | 5,304 | 4,630 | 4,114 | 1.07 | 0.27 | 0.10 | -4.0 [-9.5,1.9] (8.2, 257) | -9,208 |
| 17 | TE1B_emax_5m | NT8-bars | CANDIDATE | 12.8 | 0.52 | 11,265 | -11,219 | 6,817 | 5,353 | -945 | 0.98 | 0.02 | 0.05 | 0.9 [-4.7,6.7] (8.1, 276) | -7,695 |
| 18 | TE4_vwb_k1_all | NT8-bars | DEAD | 23.6 | 0.50 | 11,315 | -11,038 | 4,675 | 7,723 | 2,273 | 0.90 | 0.39 | 0.41 | -2.4 [-5.0,0.4] (3.9, 804) | -9,837 |
| 19 | TE4_orb_london_60 | NT8-bars | DEAD | 4.9 | 0.53 | 11,483 | -11,669 | 2,704 | 3,579 | 4,007 | 0.87 | 0.18 | 0.25 | 2.4 [-5.8,12.0] (13.0, 59) | -11,808 |
| 20 | TE7_kelt3m_n20_m2.0 | NT8-bars | DEAD | 23.8 | 0.51 | 11,276 | -11,045 | 7,586 | 6,361 | -1,088 | 0.80 | 0.36 | 0.25 | -11.8 [-15.3,-8.5] (4.9, 688) | -6,926 |

Paired vs HM10 (pts/trade): TE1_kelt_10m -5.9 [-9.8,-2.2] (MDE 5.7, n 518); TE7_emax5m_f30_s50 3.5 [-2.5,9.5] (MDE 8.5, n 262); TE6_st10m_n7_m3.0 -4.8 [-10.4,0.7] (MDE 7.8, n 303); TE7_kelt3m_n20_m1.0 5.8 [2.8,8.6] (MDE 4.2, n 663); TE7_kelt3m_n30_m1.0 7.2 [3.9,10.6] (MDE 4.8, n 533); TE7_boll3m_n20_m1.5 0.8 [-1.2,3.1] (MDE 3.2, n 950); TE6_st10m_n10_m3.0 -3.3 [-8.9,2.3] (MDE 7.9, n 298); TE1_don_15m -3.6 [-7.6,0.4] (MDE 5.8, n 561). Weekly corr columns are WF-window (2024-02+) weekly P&L at 10 lots against ST10 / HM10 with true P9 points. Placebo ranks (PRE, mapped, 40 draws): PASS cells 0.98-1.00.

## 4. All non-DEAD-on-mapped cells re-run direct (38)

| cell | group | flag | mapped verdict | direct verdict | failed (direct) | tr/wk | win | WF $/wk (mapped -> direct) | PRE | hold (mapped -> direct) | 2023 span | WF CI | placebo PRE | 2x-cost WF | DSR(191) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TE7_kelt3m_n20_m1.0 | TE7 | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 26.4 | 0.52 | 17,501 -> 17,235 | 18,528 | 14,577 -> 15,580 | -6,667 | [7,897,27,169] | 1.00 | 12,996 | 0.96 |
| TE7_kelt3m_n30_m1.0 | TE7 | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 25.1 | 0.51 | 14,666 -> 13,603 | 12,607 | 14,372 -> 14,489 | -11,612 | [4,627,23,328] | 0.97 | 11,360 | 0.89 |
| TE7_boll3m_n20_m1.5 | TE7 | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 25.8 | 0.51 | 14,252 -> 10,602 | 8,246 | 17,808 -> 13,009 | -8,783 | [2,112,19,204] | 1.00 | 4,502 | 0.79 |
| TE1B_boll_3m | TE1B | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 24.7 | 0.51 | 8,993 -> 10,405 | 10,274 | 4,792 -> 10,395 | -11,681 | [631,20,188] | 0.97 | 7,058 | 0.68 |
| TE7_boll3m_n20_m2.0 | TE7 | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 24.7 | 0.51 | 8,993 -> 10,405 | 10,274 | 4,792 -> 10,395 | -11,681 | [631,20,188] | 0.97 | 7,058 | 0.68 |
| TE6_st10m_n10_m3.5 | TE6 | NT8-bars | PASS | **CANDIDATE** | WF_CI>0 | 10.7 | 0.53 | 5,737 -> 5,304 | 5,853 | 5,573 -> 4,630 | 4,114 | [-395,10,941] | 0.97 | 3,320 | 0.56 |
| TE1B_emax_5m | TE1B | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 12.8 | 0.52 | 7,132 -> 6,817 | 8,072 | 4,678 -> 5,353 | -945 | [445,13,257] | 0.97 | 4,872 | 0.64 |
| TE7_emax5m_f20_s50 | TE7 | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 12.8 | 0.52 | 7,132 -> 6,817 | 8,072 | 4,678 -> 5,353 | -945 | [445,13,257] | 1.00 | 4,872 | 0.64 |
| TE1_kelt_3m | TE1 | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 26.0 | 0.51 | 12,550 -> 13,416 | 19,976 | 5,344 -> 6,091 | -4,068 | [5,073,22,405] | 1.00 | 11,292 | 0.91 |
| TE7_kelt3m_n20_m1.5 | TE7 | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 26.0 | 0.51 | 12,550 -> 13,416 | 19,976 | 5,344 -> 6,091 | -4,068 | [5,073,22,405] | 1.00 | 11,292 | 0.91 |
| TE7_boll3m_n30_m1.5 | TE7 | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 25.7 | 0.51 | 11,464 -> 11,366 | 16,228 | 5,550 -> 5,918 | -8,165 | [2,960,20,541] | 1.00 | 6,676 | 0.79 |
| TE7_kelt3m_n14_m1.5 | TE7 | NT8-bars | CANDIDATE | **CANDIDATE** | SPAN2>0 | 25.1 | 0.50 | 9,364 -> 8,453 | 12,382 | 2,950 -> 4,060 | -3,995 | [819,16,234] | 1.00 | 4,455 | 0.67 |
| TE3_ice_follow_lb30_q0.95 | TE3 | EXEC-ONLY | CANDIDATE | **CANDIDATE** | WF_CI>0 | 17.2 | 0.51 | 5,771 -> 4,815 | 6,147 | 3,186 -> 3,297 | 4,737 | [-2,460,11,802] | 0.97 | 1,522 | 0.36 |
| TE3_ice_follow_lb30_q0.99 | TE3 | EXEC-ONLY | CANDIDATE | **CANDIDATE** | WF_CI>0 | 7.2 | 0.52 | 3,398 -> 3,269 | 5,910 | 1,090 -> 351 | 9,633 | [-1,239,7,653] | 1.00 | 2,151 | 0.39 |
| TE1_kelt_10m | TE1 | NT8-bars | DEAD | **DEAD** | SPAN2>0,plc>=.95 | 19.7 | 0.52 | 9,772 -> 9,377 | 1,517 | 16,494 -> 17,785 | -1,925 | [1,241,17,128] | 0.75 | 5,370 | 0.78 |
| TE1_don_15m | TE1 | NT8-bars | DEAD | **DEAD** | WF_CI>0,SPAN2>0,plc>=.95 | 18.7 | 0.51 | 4,493 -> 5,479 | 677 | 6,614 -> 10,620 | -3,531 | [-2,429,13,712] | 0.78 | 2,443 | 0.36 |
| TE7_kelt3m_n14_m2.0 | TE7 | NT8-bars | CANDIDATE | **DEAD** | WF_CI>0,SPAN2>0 | 21.0 | 0.51 | 9,570 -> 8,565 | 6,947 | 9,797 -> 10,198 | -2,769 | [-2,17,449] | 0.95 | 4,843 | 0.62 |
| TE6_st10m_n14_m2.5 | TE6 | NT8-bars | CANDIDATE | **DEAD** | WF_CI>0,plc>=.95 | 14.6 | 0.52 | 7,527 -> 7,373 | 6,851 | 11,020 -> 7,834 | 5,850 | [-209,13,947] | 0.90 | 4,071 | 0.65 |
| TE1_kelt_5m | TE1 | NT8-bars | DEAD | **DEAD** | WF_CI>0,SPAN2>0,plc>=.95 | 23.8 | 0.50 | 5,705 -> 5,685 | 676 | 11,758 -> 11,048 | -3,413 | [-2,974,14,269] | 0.62 | 3,237 | 0.36 |
| TE4_vwb_k2_all | TE4 | NT8-bars | DEAD | **DEAD** | WF_CI>0,SPAN2>0,plc>=.95 | 19.5 | 0.51 | 4,879 -> 4,363 | 171 | 9,011 -> 8,856 | -9,552 | [-3,618,12,394] | 0.75 | 1,389 | 0.28 |
| TE4_vwb_k1_all | TE4 | NT8-bars | DEAD | **DEAD** | WF_CI>0,plc>=.95 | 23.6 | 0.50 | 4,919 -> 4,675 | 1,809 | 9,359 -> 7,723 | 2,273 | [-4,205,13,944] | 0.78 | 1,228 | 0.26 |
| TE4_orb_london_60 | TE4 | NT8-bars | DEAD | **DEAD** | WF_CI>0,plc>=.95 | 4.9 | 0.53 | 2,743 -> 2,704 | 1,863 | 3,140 -> 3,579 | 4,007 | [-1,937,7,648] | 0.82 | 2,158 | 0.30 |
| TE7_kelt3m_n20_m2.0 | TE7 | NT8-bars | PASS | **DEAD** | WF_CI>0,SPAN2>0 | 23.8 | 0.51 | 10,055 -> 7,586 | 8,612 | 11,702 -> 6,361 | -1,088 | [-1,119,16,149] | 1.00 | 3,956 | 0.54 |
| TE1B_rsi_1m | TE1B | NT8-bars | DEAD | **DEAD** | WF_CI>0,SPAN2>0 | 25.8 | 0.51 | 7,088 -> 8,669 | 9,907 | 6,468 -> 7,198 | -2,616 | [-2,039,19,450] | 1.00 | 3,442 | 0.49 |
| TE1_st_5m | TE1 | NT8-bars | DEAD | **DEAD** | WF_CI>0,plc>=.95 | 17.0 | 0.51 | 4,220 -> 3,701 | 3,224 | 5,485 -> 4,165 | 3,698 | [-3,557,11,398] | 0.78 | 1,853 | 0.24 |
| TE4_orb_asia_60 | TE4 | NT8-bars | DEAD | **DEAD** | WF_CI>0,SPAN2>0,plc>=.95 | 4.7 | 0.52 | 1,426 -> 1,527 | 1,407 | 1,353 -> 1,635 | -4,252 | [-2,435,5,719] | 0.62 | 1,101 | 0.18 |
| TE4_vwb_k1_ny | TE4 | NT8-bars | DEAD | **DEAD** | WF_CI>0,SPAN2>0,plc>=.95 | 15.6 | 0.51 | 4,274 -> 4,373 | 5,454 | 5,500 -> 3,135 | -2,791 | [-3,193,11,421] | 0.80 | 1,030 | 0.30 |
| TE4_orb_asia_15 | TE4 | NT8-bars | DEAD | **DEAD** | WF_CI>0,SPAN2>0,plc>=.95 | 4.9 | 0.52 | 2,309 -> 2,004 | 2,405 | 2,155 -> 1,540 | -1,489 | [-2,171,6,344] | 0.68 | 1,111 | 0.24 |
| TE4_orb_asia_30 | TE4 | NT8-bars | DEAD | **DEAD** | WF_CI>0,SPAN2>0,plc>=.95 | 4.8 | 0.52 | 1,485 -> 1,629 | 2,013 | 1,184 -> 1,188 | -2,808 | [-2,741,5,755] | 0.70 | 1,211 | 0.19 |
| TE2_big_w5_q0.9 | TE2 | NT8-ticks | DEAD | **DEAD** | WF_CI>0,SPAN2>0,plc>=.95 | 26.2 | 0.50 | 5,398 -> 4,610 | 6,098 | 4,160 -> 2,927 | -5,872 | [-4,966,13,945] | 0.93 | 2,484 | 0.26 |
| TE2_big_w3_q0.95 | TE2 | NT8-ticks | DEAD | **DEAD** | WF_CI>0,SPAN2>0,plc>=.95,x2_WF>0 | 23.2 | 0.50 | 3,457 -> 390 | 116 | 3,698 -> 682 | -2,188 | [-8,570,9,878] | 0.85 | -3,059 | 0.06 |
| TE5_mbo1 | TE5 | EXEC-ONLY | DEAD | **DEAD** | WF_CI>0,HOLD>0,plc>=.95,x2_WF>0 | 4.0 | 0.51 | 2,299 -> 1,539 | 3,161 | 290 -> -245 | 1,443 | [-2,269,5,122] | 0.90 | -4 | 0.21 |
| TE7_emax5m_f30_s50 | TE7 | NT8-bars | PASS | **PASS** |  | 11.8 | 0.53 | 7,747 -> 7,142 | 5,198 | 8,668 -> 9,150 | 1,349 | [1,786,12,941] | 0.97 | 4,257 | 0.80 |
| TE6_st10m_n7_m3.0 | TE6 | NT8-bars | PASS | **PASS** |  | 12.2 | 0.53 | 9,137 -> 8,749 | 8,743 | 9,029 -> 8,628 | 3,468 | [2,653,14,349] | 1.00 | 6,716 | 0.89 |
| TE1_st_10m | TE1 | NT8-bars | PASS | **PASS** |  | 12.1 | 0.54 | 9,838 -> 8,799 | 8,979 | 9,492 -> 8,477 | 9,914 | [1,899,15,314] | 1.00 | 6,027 | 0.83 |
| TE6_st10m_n10_m3.0 | TE6 | NT8-bars | PASS | **PASS** |  | 12.1 | 0.54 | 9,838 -> 8,799 | 8,979 | 9,492 -> 8,477 | 9,914 | [1,899,15,314] | 0.97 | 6,027 | 0.83 |
| TE7_kelt3m_n14_m1.0 | TE7 | NT8-bars | PASS | **PASS** |  | 26.8 | 0.52 | 16,232 -> 16,863 | 20,298 | 11,815 -> 12,885 | 6,365 | [7,001,26,101] | 1.00 | 12,395 | 0.96 |
| TE6_st10m_n14_m3.0 | TE6 | NT8-bars | PASS | **PASS** |  | 12.2 | 0.53 | 9,360 -> 6,980 | 7,630 | 9,269 -> 6,172 | 6,761 | [79,13,911] | 0.97 | 4,170 | 0.66 |

## 5. Widening (3x3 grids, 36 cells, mapped then direct)

ST 10-min (ATR n 7/10/14 x mult 2.5/3.0/3.5): mapped: 5 PASS (n7m3.0, n10m3.0, n10m3.5, n14m3.0 and the grid centre) / 1 CANDIDATE; direct: PASS n7m3.0, n10m3.0, n14m3.0; CANDIDATE n10m3.5; DEAD n14m2.5 (placebo 0.90, CI). Neighbour signs (PRE, holdout, 2023 span) agree for all 9 cells on holdout and span; mult 3.0 column robust across n, mult 2.5 weaker. Keltner 3-min (n 14/20/30 x mult 1.0/1.5/2.0): PRE and holdout positive in 8/9 cells, 2023 span negative in 8/9 (only n14m1.0 +$6.4k direct, PASS) - the edge is a 2024+ phenomenon, so the family is CANDIDATE with a regime warning. Bollinger 3-min: PRE/holdout positive, 2023 span negative (-$2k..-$16k) in 8 of 9 cells, CANDIDATE status at best. EMA 5-min (fast 15/20/30 x slow 40/50/75): one PASS (30/50), one CANDIDATE (20/50), rest DEAD.

## 6. By family (first-pass 155 cells, mapped; counts of PRE>0 / holdout>0 / both)

| group   | fam       |   cells |   pre_pos |   hold_pos |   pass_ |   cand |   best_wf | flag      |
|:--------|:----------|--------:|----------:|-----------:|--------:|-------:|----------:|:----------|
| TE1     | don       |       5 |         2 |          4 |       0 |      0 |      4493 | NT8-bars  |
| TE1     | hma       |       5 |         0 |          2 |       0 |      0 |      -603 | NT8-bars  |
| TE1     | kelt      |       5 |         3 |          5 |       0 |      1 |     12550 | NT8-bars  |
| TE1     | macd      |       5 |         1 |          0 |       0 |      0 |      -841 | NT8-bars  |
| TE1     | psar      |       5 |         0 |          1 |       0 |      0 |     -1893 | NT8-bars  |
| TE1     | st        |       5 |         3 |          2 |       1 |      0 |      9838 | NT8-bars  |
| TE1B    | boll      |       5 |         2 |          4 |       0 |      1 |      8993 | NT8-bars  |
| TE1B    | emax      |       5 |         4 |          2 |       0 |      1 |      7132 | NT8-bars  |
| TE1B    | rsi       |       5 |         1 |          5 |       0 |      0 |      7088 | NT8-bars  |
| TE1B    | volclimax |       5 |         2 |          1 |       0 |      0 |      3466 | NT8-bars  |
| TE1B    | vwapslope |       5 |         1 |          1 |       0 |      0 |      -209 | NT8-bars  |
| TE2     | absorb    |       6 |         0 |          0 |       0 |      0 |     -8007 | NT8-ticks |
| TE2     | big       |       5 |         5 |          3 |       0 |      0 |      5398 | NT8-ticks |
| TE2     | burst     |       5 |         2 |          5 |       0 |      0 |      1825 | NT8-ticks |
| TE2     | cdb       |       3 |         0 |          3 |       0 |      0 |      7479 | NT8-ticks |
| TE2     | ddiv      |       4 |         0 |          0 |       0 |      0 |    -10668 | NT8-ticks |
| TE2     | sweep     |       4 |         0 |          0 |       0 |      0 |     -9444 | NT8-bars  |
| TE2     | sweepc    |       3 |         0 |          0 |       0 |      0 |     -8397 | EXEC-ONLY |
| TE3     | depl      |       4 |         1 |          3 |       0 |      0 |       746 | EXEC-ONLY |
| TE3     | deplF     |       1 |         1 |          0 |       0 |      0 |      -145 | EXEC-ONLY |
| TE3     | ice       |       5 |         2 |          2 |       0 |      2 |      5771 | EXEC-ONLY |
| TE3     | imbp      |       3 |         0 |          1 |       0 |      0 |     -3080 | EXEC-ONLY |
| TE3     | imbpF     |       2 |         1 |          1 |       0 |      0 |      -416 | EXEC-ONLY |
| TE3     | mtilt     |       5 |         5 |          1 |       0 |      0 |      1455 | EXEC-ONLY |
| TE3     | ofi       |       5 |         5 |          1 |       0 |      0 |      6599 | EXEC-ONLY |
| TE3     | vpin      |       4 |         4 |          0 |       0 |      0 |      1409 | NT8-ticks |
| TE3     | vpinF     |       1 |         0 |          1 |       0 |      0 |     -3601 | NT8-ticks |
| TE4     | onb       |       4 |         3 |          0 |       0 |      0 |      -605 | NT8-bars  |
| TE4     | orb       |       9 |         7 |          6 |       0 |      0 |      2743 | NT8-bars  |
| TE4     | pdb       |       6 |         0 |          4 |       0 |      0 |      -643 | NT8-bars  |
| TE4     | vwb       |       6 |         5 |          4 |       0 |      0 |      4919 | NT8-bars  |
| TE5     | mbo       |       1 |         1 |          0 |       0 |      0 |      -300 | EXEC-ONLY |
| TE5     | mbo1      |       2 |         1 |          1 |       0 |      0 |      2299 | EXEC-ONLY |
| TE5     | mbo2      |       2 |         0 |          1 |       0 |      0 |       397 | EXEC-ONLY |
| TE5     | mbo3      |       2 |         1 |          1 |       0 |      0 |       -47 | EXEC-ONLY |
| TE5     | mbo4      |       2 |         1 |          1 |       0 |      0 |      2629 | EXEC-ONLY |
| TE5     | mbo5      |       2 |         1 |          1 |       0 |      0 |      1568 | EXEC-ONLY |
| TE5     | mbo6      |       2 |         1 |          1 |       0 |      0 |       398 | EXEC-ONLY |
| TE5     | mbo7      |       2 |         1 |          1 |       0 |      0 |      1358 | EXEC-ONLY |

Best-of-N: of 155 first-pass cells 67 had PRE>0, 69 holdout>0, 31 both (a coin-flip expectation of ~39 for independent signs); 6 survive all conditions mapped. The family-level tape null is consistent with PRED block B.

## 7. NT8 vs execution-server flags

NT8-bars: all bar and structure cells, including every PASS/CANDIDATE except the two iceberg CANDIDATEs. NT8-ticks (bid/ask-classified trade ticks, no L2): absorption, aggressor bursts, delta divergence, CD breakouts, large prints, VPIN - none PASS. EXEC-ONLY (L2 at runtime): sweep confirmation, book imbalance, queue depletion, iceberg refills, OFI, microprice tilt, MBO seven. The two CANDIDATEs TE3_ice_follow (refill_n 99th/95th pct at a 30-min extreme, follow) are EXEC-ONLY and have WF CI including 0.

## 8. Prior evidence and what changed

FAILPRED STEP2 C4-C8 (VWAP/ORB/scalps lost) and STRUCT48 T3.2 (ORB 60/1.5R sleeves; negative in IS, year share > 60%): consistent - ORB and VWAP-band entries are DEAD here at 60/1.0R. PRED block B tape features (gate AUC 0.50-0.54): consistent - the tape entries do not survive three windows. HB handoff book: not re-tested. Contrasting result: the trend-turn entries at 3-10 min (Supertrend 10, Keltner 3, EMA 30/50 5) are positive in WF-PRE and holdout; whether they are independent of DS2 is a portfolio question for D3L: weekly corr to ST10 0.03-0.33, to HM10 -0.06..0.33.

## 9. Registered / files

Registered to l2vast/struct48/paper_all/ds3_TE_<cell>.json: TE1B_boll_3m, TE1B_emax_5m, TE1_kelt_3m, TE1_st_10m, TE3_ice_follow_lb30_q0.95, TE3_ice_follow_lb30_q0.99, TE6_st10m_n10_m3.0, TE6_st10m_n10_m3.5, TE6_st10m_n14_m3.0, TE6_st10m_n7_m3.0, TE7_boll3m_n20_m1.5, TE7_boll3m_n20_m2.0, TE7_boll3m_n30_m1.5, TE7_emax5m_f20_s50, TE7_emax5m_f30_s50, TE7_kelt3m_n14_m1.0, TE7_kelt3m_n14_m1.5, TE7_kelt3m_n20_m1.0, TE7_kelt3m_n20_m1.5, TE7_kelt3m_n30_m1.0. Top-20: l2vast/ds3/out/TENTRY_top20.parquet (ST10/HM10 rows first). Preregs l2vast/ds3/prereg/TE_TE*.md (+ .sha256), code l2vast/ds3/code/te/, per-cell results l2vast/ds3/out/te/res_TE*.json, direct tables /mnt/l2/l2vast/ds3_te/, daily series l2vast/ds3/out/te/direct_daily.parquet. PASS cells need identity tests (D3X) before DS3 inclusion; the 3x3 grids and the 2023 span are the robustness evidence. Caveat: TE1_st_10m is a different Supertrend configuration from the live ST10 (12 vs 29 trades/wk, weekly corr 0.03), not a re-statement of it.
