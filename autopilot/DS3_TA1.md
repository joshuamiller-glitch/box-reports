# DS3 TA1: regime-conditional entries - the volatility forecaster as a SPLITTER (D3R, addendum-2 A1)

Generated 2026-10-26T17:30:52Z. Research only; no execution-server/chart/live change.

## 1. Verdict

**Verdict: no regime gate adds anything beyond the entries' own edge. The two entries that PASS in the predicted-wide column under DIRECT L2 pricing (10-minute Supertrend 10x3.0 and 3-minute Keltner 14/1.0) also PASS unconditionally; gating to predicted-wide keeps 74-78% of the trades, a similar per-trade mean (st10m +9%, Keltner n14 -5%) and an 11-25% lower $/wk, and the predicted-quiet column has no PASS or CANDIDATE except a 1.1-trades/wk MBO cell that fails the trade-count minimum.** The per-trade wide-minus-quiet difference that is visible in the selection window (WF-PRE: wide > quiet in 41 of 60 entries) disappears in the holdout (30 of 59, median $2/trade) and reverses in the never-scored 2023-04..2024-01 span (21 of 60, median -$444/trade). A permuted-regime-label null produces MORE PASS-like cells than the real labels (null mean 4.2, p95 7.1 of 120; real 2), because a random half of a profitable entry is still profitable.

* 120 cells in 5 preregs (TA1a 30, TA1b 30, TA1c 24, TA1d 22, TA1e 14) = 60 source entries (38 T-ENTRY + 22 T-B) x {predicted-quiet, predicted-wide} at P(quiet) >= 0.6 (LightGBM). Mapped verdicts (signal rule): quiet {'CANDIDATE': np.int64(1), 'DEAD': np.int64(59), 'PASS': np.int64(0)}, wide {'CANDIDATE': np.int64(6), 'DEAD': np.int64(53), 'PASS': np.int64(1)}; unconditional ('all', re-scored on the same basis, not new trials): {'CANDIDATE': np.int64(8), 'DEAD': np.int64(49), 'PASS': np.int64(3)}.
* DIRECT L2 re-pricing of every non-DEAD regime column plus the top 10 by holdout (11 cells; coverage of trades by the existing T-ENTRY replay 92-98%, rest mapped): **wide PASS: TE1_st_10m, TE7_kelt3m_n14_m1.0; wide CANDIDATE: TE6_st10m_n14_m3.0 (placebo), TE7_kelt3m_n20_m1.0, TE7_boll3m_n20_m1.5, TE7_boll3m_n30_m1.5, TE1_kelt_3m (all fail the 2023-04..2024-01 span); quiet: none.** A wide-only PASS in the sense of the order ("passes in ONE regime only") does exist for these two, but the unconditional entry passes as well, so the regime gate is not what makes them pass.
* Paired delta vs ST (regime-specific ST, per trade, session-block bootstrap, 90% CI): every regime-specific PASS/CANDIDATE is at or below ST (-2 to -7 pts/trade; the ST10m cells' and Keltner n20/1.0 CIs include 0, Keltner n14/1.0, Keltner 20/1.5, Bollinger CIs exclude 0 on the negative side); the paired MDE is 4-9 pts/trade, so a +0.3-pt/trade predicted effect is far below detectability. They are new, weakly correlated books (weekly corr to regime-ST 0.10-0.33), not better entries for ST.
* Forecaster deliverability: the forecaster as built is **execution-server-only** (section 2). A bars-only HAR forecaster (NT8-reproducible, AUC .76 vs .86) used as the gate keeps the wide-column signs (section 7).

## 2. The splitter: as-of-open P(quiet) series, audit, deliverability

Series: `l2vast/ds3/out/TA/pquiet_series.parquet` (2858 sessions 2023-02-08..2026-10-16, 2813 with a forecast; columns ld, s (0 Asia 18:00, 1 London 02:00, 2 NY 09:30 ET), minute, q40, P_lgb, P_ridge, P_har, quiet_real). P(quiet) = Phi((q40 - mu)/e): mu/e = the walk-forward session-RV forecast / its trailing error std at the session-open instant (pairP2/firm/forecast_table.parquet, monthly refit on label days <= month start - 3 days), q40 = the 40th percentile of the previous 20 same-type sessions' realised log-RV (shifted by one session). Fixed threshold 0.6 (prereg); 0.5 and 0.7 reported as sensitivity. Rebuilt from forecast_table (not copied); it differs from the FOURTH-book series (feats_sess_q) by up to 0.07 in 40 of 2,858 sessions (Asia, Apr 2025: the old table dropped one session from the rolling-q40 window).

**AUC for 'realised session RV below its 20-day same-type p40'** (LightGBM / ridge / bars-only HAR): all 0.857 / 0.825 / 0.761; WF 2024-02+ 0.858 / 0.830 / 0.765; holdout 2025-07+ 0.834 / 0.804 / 0.722; 2023-04..2024-01 0.840 / 0.796 / 0.745. Share flagged quiet (LGB, WF) at 0.5/0.6/0.7: 40%, 31%, 22%; holdout 38%, 27%, 19%.

**Truncation-invariance audit.** (a) Feature level: pairP2/firm/trunc_check.py re-run with a new seed (10 instants x 2 conditions: bars cut at the instant, and bars after the instant replaced by random walk): 0 mismatches (`trunc_feat_seed11.log`); the original run (12 instants) and the fourth-book session-feature tests (684 + 104 + 192 checks) also 0 mismatches. (b) Series level (`pquiet_audit.json`): for 40 random sessions, the table is cut at the session-open row, that session's own target blanked, the P series rebuilt and compared: 120 comparisons, 0 mismatches. (c) Model level: the monthly refit uses only label days <= month start - 3 days (FORECAST_TABLE.md); the error scale e is lagged by the horizon. Disclosure: the first fit window is 2023-03..2023-06 (forecast_table `insample`=1 for ld < 2023-07-01), so 3 of the 10 months of the 2023-04..2024-01 'never-scored' span use an in-sample forecast.

**Forecaster feature families** (LightGBM session-RV model, share of split counts, `lgb_importance_part1.csv`): bar-derived from 1-min OHLCV (realised vol 30/60/120 min, session/day RV, HAR d/w/m, EWMA .94/.97, ATR20 and its percentile, overnight range, gap, range-so-far, log-signature features, time of day, session) 45%; external volatility indices (VIX, VXN, VIX1D, VIX3M, VVIX, term spread, dVIX5, VXN/VIX, implied/realised) 27%; L2 book-state snapshots at the session open (top-1/5/10 imbalance, relative depth, spread, 15-min flow direction, cancel/add, sp1) 24%; calendar/event flags (FOMC, CPI, PCE, NFP, opex, month/quarter end, holidays) 4%. **NT8 deliverability: NOT DELIVERABLE as built** - 24% of the model's splits use L2 book state (needs mbp-10 at runtime) and 27% use VIX-family daily/intraday indices that the chart does not carry (the free CBOE daily files are on disk, but NT8 would need its own feed). Every book that gates on this forecaster is therefore **execution-server-only**. The bars+calendar-only HAR variant (P_har: same recursion, no VIX/L2; AUC .76) is reproducible from bars and a holiday/event calendar; its use as the gate is in section 7.

## 3. Cell set, windows, rules

Cells: source entry x {predicted-quiet (P>=0.6), predicted-wide (P<0.6)}. Selection (deterministic, from UNCONDITIONAL pre-holdout results only; see the preregs `l2vast/ds3/prereg/TA1_TA1a..e_prereg.md`, sha256 in DECISIONS.md): TA1a = top 15 T-ENTRY series by mapped PRE $/wk (tpw>=3, duplicates removed, <= 3 per family); TA1b = top 15 T-B intraday books by WFPRE (<= 3 per family); TA1c/d = the best-PRE cell of each of the other 23 T-ENTRY families; TA1e = best of each of the 7 remaining T-B families. This covers all 29 T-ENTRY families and all 16 T-B families (not all 191 + 279 cells - the order asked for a restriction to keep each prereg <= 30). Gate = applied to SIGNALS before the busy filter (T-ENTRY; exact 1-s path bracket, mapped P9 pricing, exact per-book lock engine, 10 lots) or to the stitched trade list by entry bar (T-B; closed-trade lock approximation as T-B; stated approximation). Windows: WF-PRE 2024-02..2025-06 (selection), holdout 2025-07+ (ONE look, logged `DS3_TA1`; the source cells already had holdout looks), second holdout 2023-04..2024-01. PASS = trades/wk >= 3, PRE>0, WF CI>0, holdout>0, span2>0, within-regime timing-destroyed placebo (40 draws, entry bars restricted to the regime, same count/side/hour mix; T-B: 60 draws, same-day random bars) >= .95, 2x-cost WF>0; CANDIDATE = one failure.
Power: weekly MDE (80%, 5%) of these gated books is $9-25k/wk on 75 PRE weeks (e.g. kelt 14/1.0 wide 12k, st10m wide 9-10k); the predicted regime effect (+$2-6k/wk) is below it, so every verdict rests on three-window sign agreement, the placebo and cost stress.

## 4. Three columns for every cell (mapped basis; WF $/wk at 10 lots | holdout | 2023-04..2024-01; verdict)

| source | trk | all: tr/wk WF / hold / span2 [verdict] | quiet: tr/wk WF / hold / span2 [verdict] | wide: tr/wk WF / hold / span2 [verdict] |
|--|--|--|--|--|
| TE7_kelt3m_n14_m1.0 | TE | 29.5: 16,232 / 11,815 / 176 [PASS] | 9.3: -403 / -3,151 / -5,078 [DEAD] | 23.1: 14,102 / 10,400 / -1,187 [CAND] |
| TE7_kelt3m_n20_m1.0 | TE | 28.6: 17,501 / 14,577 / -7,874 [CAND] | 9.2: 45 / -231 / -4,497 [DEAD] | 22.1: 18,230 / 16,239 / -8,214 [CAND] |
| TE3_ofi_w3_q0.99 | TE | 16.9: 6,515 / -8,019 / 4,158 [DEAD] | 3.0: 1,197 / 34 / -2,137 [DEAD] | 13.7: 5,036 / -8,481 / 6,294 [DEAD] |
| TE1_kelt_3m | TE | 28.6: 12,550 / 5,344 / -4,042 [CAND] | 8.9: 242 / -3,548 / -5,166 [DEAD] | 21.9: 9,097 / 3,651 / -2,111 [CAND] |
| TE7_boll3m_n30_m1.5 | TE | 28.4: 11,464 / 5,550 / -9,488 [CAND] | 9.0: -547 / -3,075 / -7,223 [DEAD] | 22.1: 10,818 / 8,386 / -5,525 [CAND] |
| TE3_ofi_w5_q0.97 | TE | 22.7: 6,599 / -3,183 / 2,959 [DEAD] | 4.7: -12 / -656 / -114 [DEAD] | 18.2: 5,796 / -3,373 / 2,609 [DEAD] |
| TE3_ofi_w1_q0.99 | TE | 19.6: 5,863 / -2,324 / 4,982 [DEAD] | 3.6: 1,233 / 271 / 317 [DEAD] | 15.9: 4,207 / -3,807 / 4,655 [DEAD] |
| TE7_emax5m_f15_s40 | TE | 15.6: 7,407 / 890 / -4,222 [DEAD] | 4.7: 2,800 / -1,472 / -3,319 [DEAD] | 11.5: 5,926 / 4,033 / -4,242 [DEAD] |
| TE7_boll3m_n20_m2.0 | TE | 27.1: 8,993 / 4,792 / -16,070 [CAND] | 8.2: 1,320 / 1,854 / -7,665 [DEAD] | 21.0: 2,838 / 1,073 / -6,768 [DEAD] |
| TE1B_volclimax_5m | TE | 15.9: 3,466 / -4,612 / 3,985 [DEAD] | 4.4: 2,587 / -1,910 / 3,938 [DEAD] | 12.0: 2,295 / -1,161 / 582 [DEAD] |
| TE7_boll3m_n20_m1.5 | TE | 28.7: 14,252 / 17,808 / -10,700 [CAND] | 9.1: 1,174 / -129 / -13,152 [DEAD] | 22.1: 10,905 / 14,640 / -4,819 [CAND] |
| TE1_st_10m | TE | 12.5: 9,838 / 9,492 / 7,686 [PASS] | 3.6: 2,484 / -718 / 3,415 [DEAD] | 9.2: 8,707 / 11,581 / 2,235 [PASS] |
| TE6_st10m_n14_m3.0 | TE | 12.6: 9,360 / 9,269 / 4,981 [PASS] | 3.7: 1,293 / -1,814 / 4,318 [DEAD] | 9.3: 8,930 / 11,976 / 2,118 [CAND] |
| TE7_emax5m_f20_s50 | TE | 13.4: 7,132 / 4,678 / -1,847 [CAND] | 4.0: 2,600 / -619 / -97 [DEAD] | 9.9: 5,054 / 5,613 / -2,979 [DEAD] |
| TE7_emax5m_f20_s40 | TE | 14.4: 7,019 / 4,491 / -1,999 [DEAD] | 4.3: 2,028 / -1,963 / -372 [DEAD] | 10.7: 5,573 / 6,650 / -3,731 [DEAD] |
| TE2_absorb_v3_lb120 | TE | 16.5: -8,007 / -10,322 / -2,300 [DEAD] | 5.5: -1,166 / -3,982 / 5,901 [DEAD] | 12.0: -7,567 / -6,926 / -8,084 [DEAD] |
| TE2_big_w5_q0.98 | TE | 12.1: 3,141 / -2,135 / -515 [DEAD] | 2.6: 811 / 310 / -749 [DEAD] | 9.5: 2,208 / -2,819 / 1,498 [DEAD] |
| TE2_burst_w1_t0.7_v1.0 | TE | 3.7: 149 / 1,211 / -2,843 [DEAD] | 1.4: 178 / 8 / -159 [DEAD] | 2.4: -86 / 355 / -2,969 [DEAD] |
| TE2_cdb_N30 | TE | 32.4: 7,013 / 19,191 / -3,408 [DEAD] | 10.4: -923 / 2,790 / 3,136 [DEAD] | 25.3: 5,259 / 12,042 / 1,663 [DEAD] |
| TE2_ddiv_N60 | TE | 30.3: -15,949 / -24,197 / 1,651 [DEAD] | 9.4: -7,059 / -6,650 / 1,645 [DEAD] | 24.1: -13,216 / -19,122 / 780 [DEAD] |
| TE3_deplF_w5_t0.25 | TE | 13.2: -145 / -3,380 / 2,644 [DEAD] | 4.7: 2,055 / 3,345 / 2,291 [DEAD] | 9.2: -1,692 / -4,721 / 37 [DEAD] |
| TE1_don_3m | TE | 28.7: 3,621 / -637 / -9,488 [DEAD] | 9.6: 3,278 / 4,810 / -3,493 [DEAD] | 22.2: -1,191 / -6,483 / -6,405 [DEAD] |
| TE1_hma_1m | TE | 31.1: -5,770 / -10,792 / -5,285 [DEAD] | 10.2: -3,579 / -5,490 / -2,621 [DEAD] | 25.2: -2,110 / -2,361 / -2,012 [DEAD] |
| TE3_ice_follow_lb30_q0.95 | TE | 17.9: 5,771 / 3,186 / 4,194 [CAND] | 3.9: 1,237 / 271 / 6,836 [DEAD] | 13.7: 4,778 / 3,757 / -2,111 [DEAD] |
| TE3_imbpF_w5_t0.1 | TE | 15.3: -416 / -5,300 / -8,958 [DEAD] | 4.9: 2,355 / 2,700 / -3,090 [DEAD] | 11.0: -3,620 / -9,833 / -6,484 [DEAD] |
| TE1_macd_3m | TE | 28.3: -2,179 / -9,472 / -12,072 [DEAD] | 8.8: -3,479 / -5,337 / -4,493 [DEAD] | 22.1: 52 / -7,131 / -15,563 [DEAD] |
| TE5_mbo1 | TE | 4.0: 2,299 / 290 / 1,289 [DEAD] | 1.1: 2,703 / 56 / 2,140 [CAND] | 2.9: -434 / 396 / -350 [DEAD] |
| TE3_mtilt_w3_t0.15 | TE | 26.6: 1,455 / -1,541 / -4,827 [DEAD] | 8.7: 512 / 2,922 / -67 [DEAD] | 20.0: -1,514 / -5,276 / -1,249 [DEAD] |
| TE4_onb_ny_v0.0 | TE | 9.6: -605 / -4,010 / -6,156 [DEAD] | 2.3: -1,664 / -2,001 / 279 [DEAD] | 7.2: 1,220 / -1,677 / -6,435 [DEAD] |
| TE4_orb_ny_15 | TE | 4.9: 838 / -4,652 / -2,733 [DEAD] | 1.3: 1,223 / -711 / -4,310 [DEAD] | 3.5: -149 / -3,451 / 1,577 [DEAD] |
| TE4_pdb_london_v0.0 | TE | 3.7: -1,522 / -123 / -276 [DEAD] | 1.0: -724 / 637 / -94 [DEAD] | 2.7: -718 / -594 / -457 [DEAD] |
| TE1_psar_15m | TE | 20.7: -1,893 / 494 / 5,055 [DEAD] | 6.3: 775 / -1,158 / 2,138 [DEAD] | 15.6: -3,261 / 2,307 / 4,024 [DEAD] |
| TE1B_rsi_1m | TE | 28.9: 7,088 / 6,468 / -5,722 [DEAD] | 8.9: 4,485 / 7,697 / 2,700 [DEAD] | 23.0: 2,209 / -186 / -7,315 [DEAD] |
| TE2_sweep_lb30 | TE | 31.3: -9,444 / -19,146 / -4,833 [DEAD] | 10.0: -5,979 / -7,910 / 2,857 [DEAD] | 24.5: -3,653 / -12,636 / -14,426 [DEAD] |
| TE2_sweepc_lb30_n10 | TE | 29.1: -12,362 / -12,085 / 916 [DEAD] | 8.9: -6,108 / -6,335 / -3,473 [DEAD] | 22.9: -3,917 / -1,879 / 778 [DEAD] |
| TE3_vpin_n20_q0.95 | TE | 22.3: -1,349 / -11,975 / -2,947 [DEAD] | 5.8: 3,315 / -208 / -5,356 [DEAD] | 16.9: -5,585 / -13,649 / 3,792 [DEAD] |
| TE1B_vwapslope_5m | TE | 13.1: -1,437 / -3,592 / 292 [DEAD] | 4.0: 842 / 2,421 / -145 [DEAD] | 9.6: -2,515 / -6,439 / 2,693 [DEAD] |
| TE4_vwb_k1.5_ny | TE | 14.1: 3,086 / -2,812 / -1,024 [DEAD] | 3.6: 1,696 / 2,215 / 1,118 [DEAD] | 10.4: 1,164 / -5,494 / -2,142 [DEAD] |
| TB3_EMA_k5_A3_N | TB | 14.4: 10,155 / -3,315 / -3,248 [DEAD] | 6.2: 325 / 3,315 / -1,358 [DEAD] | 9.7: 10,345 / -7,602 / -640 [DEAD] |
| TB3_EMA_k5_A3_FV | TB | 18.8: 10,515 / 1,460 / -21,590 [DEAD] | 6.6: 1,125 / 7,375 / -6,183 [DEAD] | 13.2: 9,727 / -3,367 / -15,148 [DEAD] |
| TB9_RENKO_c3_k1_A3_N | TB | 9.6: 5,034 / -9,570 / -4,812 [DEAD] | 3.0: -1,522 / -4,952 / 5,205 [DEAD] | 7.3: 6,910 / -3,818 / -9,587 [DEAD] |
| TB9_RENKO_c4_k1_A3_N | TB | 10.0: 281 / -17,558 / -11,804 [DEAD] | 3.2: -1,398 / -4,235 / -389 [DEAD] | 7.4: 3,973 / -12,428 / -11,675 [DEAD] |
| TB2_WIL_k5_A3_FV | TB | 19.7: 16,764 / 19,529 / -11,771 [DEAD] | 6.8: 2,358 / 7,061 / -133 [DEAD] | 13.8: 14,650 / 13,425 / -11,298 [DEAD] |
| TB9_RENKO_c2_k1_A3_N | TB | 12.3: 10,730 / 8,070 / -34,897 [DEAD] | 4.4: 915 / 5,906 / -8,849 [DEAD] | 9.4: 8,179 / -1,887 / -28,249 [DEAD] |
| TB1_ST_k15_A3_N | TB | 16.4: 10,921 / 8,668 / -3,651 [DEAD] | 6.0: 1,281 / 9,314 / 4,347 [DEAD] | 10.9: 6,637 / -4,011 / -7,992 [DEAD] |
| TB7_ORBNY_k1_P60_N | TB | 6.4: 6,032 / -1,056 / 3,979 [DEAD] | 1.7: 3,430 / 1,819 / 2,565 [DEAD] | 4.6: 2,602 / -2,875 / 1,415 [DEAD] |
| TB7_ORBNY_k3_P60_N | TB | 6.1: 6,866 / 1,319 / 300 [CAND] | 1.6: 2,825 / 72 / 966 [DEAD] | 4.4: 4,042 / 1,246 / -666 [DEAD] |
| TB2_WIL_k15_A3_N | TB | 16.2: 1,645 / -8,257 / -12,591 [DEAD] | 5.9: -927 / -6,163 / -591 [DEAD] | 11.0: 1,908 / -1,452 / -14,223 [DEAD] |
| TB4_DON_k3_A3_N | TB | 10.9: -3,683 / -17,984 / -32,080 [DEAD] | 4.9: -1,966 / -1,633 / 7,136 [DEAD] | 7.5: 1,277 / -9,805 / -32,705 [DEAD] |
| TB4_KEL_k5_A3_N | TB | 17.5: -605 / -11,414 / -13,450 [DEAD] | 7.0: -2,820 / 13 / 5,156 [DEAD] | 12.1: -3,478 / -20,014 / -25,158 [DEAD] |
| TB2_WIL_k15_A3_FV | TB | 15.9: -3,890 / -18,013 / -11,240 [DEAD] | 5.2: 465 / 2,458 / 1,709 [DEAD] | 11.2: -6,411 / -23,574 / -13,400 [DEAD] |
| TB5_RSI_k15_A3_N | TB | 14.3: 11,028 / 13,254 / -11,086 [DEAD] | 5.1: 1,340 / 2,664 / 848 [DEAD] | 9.7: 10,021 / 10,320 / -12,263 [DEAD] |
| TB3_HMA_k15_A3_FV | TB | 17.6: 8,216 / 7,419 / -8,637 [DEAD] | 5.7: -60 / 4,956 / 39 [DEAD] | 12.4: 6,396 / 2,078 / -10,387 [DEAD] |
| TB8_CLIM_k15_T_N | TB | 12.0: -2,558 / -10,332 / 3,669 [DEAD] | 3.5: 1,150 / -2,327 / 664 [DEAD] | 8.6: -3,947 / -8,550 / 3,004 [DEAD] |
| TB5_MACD_k15_P60_N | TB | 18.5: 4,615 / 714 / -13,547 [DEAD] | 6.9: -2,672 / -3,043 / -1,068 [DEAD] | 12.6: 7,741 / 4,879 / -15,678 [DEAD] |
| TB7_ORBAS_k1_P60_N | TB | 7.6: 3,987 / -235 / -4,001 [DEAD] | 3.1: 1,326 / 1,863 / -5,892 [DEAD] | 4.5: 2,661 / -2,099 / 1,891 [DEAD] |
| TB7_ORBLON_k1_P60_N | TB | 8.9: 7,375 / 7,210 / -1,826 [DEAD] | 2.6: 2,694 / 7,187 / -890 [DEAD] | 6.4: 4,853 / 1,869 / 1,211 [DEAD] |
| TB7_PD_k1_A3_N | TB | 4.2: -9,167 / -23,755 / 11,241 [DEAD] | 1.5: -4,391 / -1,859 / 12,775 [DEAD] | 2.8: -7,085 / -22,790 / -1,534 [DEAD] |
| TB2_PSAR_k15_A3_FV | TB | 19.7: -865 / -5,205 / -17,046 [DEAD] | 6.3: 297 / 2,702 / -1,795 [DEAD] | 13.8: -4,103 / -9,641 / -16,196 [DEAD] |
| TB6_VWAP_k5_A3_N | TB | 26.0: 7,741 / 11,982 / -28,153 [DEAD] | 11.2: -3,874 / 5,848 / -6,139 [DEAD] | 17.5: 11,930 / 13,006 / -23,559 [DEAD] |

(PASS/CAND/DEAD abbreviated PASS/CAND/DEAD; 'few trades' = fewer than 60 gated trades.)

## 5. DIRECT L2 re-pricing of the regime finalists (wide column; S10x1 + XJ3 from the existing T-ENTRY replay, `ta_direct.py`)

| cell | regime | cover | tr/wk | PRE | WF $/wk [90% CI] | holdout | span2 | WF 1.5x | WF 2x | WF corr ST | paired vs regime-ST pts/trade [CI] (MDE, pairs) | verdict (direct) | failed |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TE7_kelt3m_n14_m1.0 | wide | 0.96 | 21.0 | 12,730 | 12,585 [4,572, 20,361] | 12,245 | 2,638 | 10,278 | 8,244 | 0.15 | -5.4 [-8.5, -2.2] (MDE 4.4, n 729) | **PASS** |  |
| TE1_st_10m | wide | 0.97 | 9.0 | 4,652 | 7,115 [1,405, 12,675] | 9,689 | 2,789 | 5,670 | 4,561 | 0.14 | -5.3 [-11.5, 1.2] (MDE 9.0, n 229) | **PASS** |  |
| TE7_kelt3m_n20_m1.0 | wide | 0.96 | 20.7 | 16,249 | 16,516 [9,055, 24,976] | 16,568 | -5,417 | 15,025 | 12,958 | 0.10 | -2.1 [-5.1, 1.0] (MDE 4.4, n 751) | **CANDIDATE** | SPAN2>0 |
| TE7_boll3m_n20_m1.5 | wide | 0.96 | 20.0 | 4,600 | 8,325 [1,019, 15,964] | 12,253 | -2,174 | 6,995 | 3,320 | 0.19 | -6.3 [-10.0, -2.5] (MDE 5.3, n 582) | **CANDIDATE** | SPAN2>0 |
| TE7_boll3m_n30_m1.5 | wide | 0.96 | 20.2 | 10,762 | 10,285 [2,544, 17,990] | 9,618 | -4,702 | 8,135 | 6,699 | 0.30 | -6.6 [-9.7, -3.3] (MDE 4.6, n 629) | **CANDIDATE** | SPAN2>0 |
| TE6_st10m_n14_m3.0 | wide | 0.98 | 9.0 | 4,097 | 6,242 [1,070, 11,872] | 8,482 | 3,119 | 4,993 | 3,937 | 0.16 | -5.1 [-10.8, 1.5] (MDE 8.8, n 236) | **CANDIDATE** | plc>=.95 |
| TE1_kelt_3m | wide | 0.96 | 20.1 | 12,626 | 7,804 [285, 15,435] | 2,450 | -1,593 | 6,857 | 5,181 | 0.33 | -6.3 [-9.3, -3.2] (MDE 4.3, n 706) | **CANDIDATE** | SPAN2>0 |
| TE2_cdb_N30 | wide | 0.30 | 24.3 | -1,390 | 4,663 [-3,363, 13,121] | 11,175 | -240 | 3,431 | 2,058 | 0.34 | -8.3 [-11.8, -5.0] (MDE 5.0, n 726) | **DEAD** | PRE>0,WF_CI>0,SPAN2>0,plc>=.95 |
| TE1B_rsi_1m | quiet | 0.92 | 8.6 | 2,062 | 4,791 [-1,392, 10,790] | 7,689 | 4,917 | 3,783 | 2,018 | 0.61 | 7.0 [4.1, 10.0] (MDE 4.0, n 450) | **DEAD** | WF_CI>0,plc>=.95 |
| TE7_emax5m_f20_s50 | wide | 0.96 | 9.5 | 4,258 | 5,231 [-193, 10,361] | 6,213 | -3,389 | 4,110 | 3,660 | -0.01 | -1.4 [-7.3, 4.7] (MDE 8.8, n 228) | **DEAD** | WF_CI>0,SPAN2>0 |
| TE7_emax5m_f20_s40 | wide | 0.42 | 10.5 | 5,030 | 5,217 [-918, 10,975] | 5,345 | -3,842 | 4,631 | 3,907 | -0.06 | -0.9 [-6.1, 4.4] (MDE 7.4, n 262) | **DEAD** | WF_CI>0,SPAN2>0,plc>=.95 |

Cells with cover < .9 (TE2_cdb_N30, TE7_emax5m_f20_s40) were not in the 38-cell direct replay; their uncovered trades stay MAPPED. 'all' (unconditional) direct reference from DS3_TENTRY.md: TE7_kelt3m_n14_m1.0 WF 16,863 / hold 12,885 / span2 6,365 (PASS); TE1_st_10m 8,799 / 8,477 / 9,914 (PASS); TE6_st10m_n14_m3.0 6,980 / 6,172 / 6,761 (PASS); TE7_kelt3m_n20_m1.0 17,235 / 15,580 / -6,667 (CAND). Gating to predicted-wide costs 11-25% of the weekly mean (trades -22..-26%) for the ST10m cells and Keltner n14 (direct WF: st10m 8,799 -> 7,115; Keltner n14 16,863 -> 12,585; st10m n14 6,980 -> 6,242).

## 6. Is there a regime effect at all? Per-trade wide - quiet on the UNGATED trade lists (descriptive, same trades as the 'all' column; label-day block bootstrap)

* PRE: 60 entries; wide>quiet per trade in 41; 90% CI excludes 0 upward in 3, downward in 2; mean diff $532/trade, median $366
* WF: 60 entries; wide>quiet per trade in 39; 90% CI excludes 0 upward in 4, downward in 2; mean diff $120/trade, median $177
* HOLD: 59 entries; wide>quiet per trade in 30; 90% CI excludes 0 upward in 3, downward in 3; mean diff $-227/trade, median $2
* SPAN2: 60 entries; wide>quiet per trade in 21; 90% CI excludes 0 upward in 2, downward in 4; mean diff $-536/trade, median $-444

The regime effect is a selection-window phenomenon: positive in PRE/WF, zero in the holdout, negative in the older span - the signature of noise plus a one-regime fit window, not of a stable splitter. Largest WF per-trade wide-minus-quiet differences: TB6_VWAP_k5_A3_N $1,754; TB9_RENKO_c3_k1_A3_N $1,643; TB9_RENKO_c4_k1_A3_N $1,422; TB3_EMA_k5_A3_FV $1,136; TB5_RSI_k15_A3_N $1,021. Most negative: TE5_mbo1 $-2,526; TB7_ORBNY_k1_P60_N $-1,428; TE4_orb_ny_15 $-949.

## 7. Best-of-N null, sensitivity, bars-only gate

* Best-of-N (permuted-regime-label null: session P shuffled within session type, 20 worlds, same 120 cells, PRE only; pre-holdout text `ta1_preholdout.md`): max PRE $/wk 26.5k real vs null mean 25.2k (p95 35.2k; share of worlds >= real 0.45); mean per-trade wide-quiet gap $568 real vs null 189 (p95 853; p = 0.25); entries with wide > quiet per trade 36 vs null 27.3 (p95 37); cells with PRE>0: 79 vs 80.2. None is outside the null.
* Full-criteria null ('pass-lite': tpw>=3, PRE>0, holdout>0, span2>0, WF CI>0 by normal approx; no placebo/2x), 21 worlds incl. real: real 2 cells (quiet 0, wide 2); null mean 4.25, p95 7.1, max 8; share of null worlds >= real 0.95.
* Thresholds 0.5 / 0.7 and ridge forecaster (descriptive, no placebo; 360 sensitivity cells counted in the ledger; table below for the wide-column finalists, WF / holdout / span2 $/wk):

| cell | P>=.6 LGB | theta .5 | theta .7 | ridge .6 | HAR .6 (bars-only) |
|--|--|--|--|--|--|
| TE1_kelt_3m | 21.9: 9,097 / 3,651 / -2,111 | 19.5: 7,882 / 724 / -4,490 | 23.9: 12,431 / 7,088 / -574 | 21.0: 8,947 / 1,956 / -2,682 | 22.0: 5,855 / 2,890 / -5,814 |
| TE1_st_10m | 9.2: 8,707 / 11,581 / 2,235 | 8.2: 7,310 / 9,731 / 1,368 | 10.2: 11,032 / 13,465 / 6,212 | 8.8: 8,313 / 10,744 / 4,519 | 8.9: 8,117 / 10,646 / 6,004 |
| TE2_cdb_N30 | 25.3: 5,259 / 12,042 / 1,663 | 22.8: 4,769 / 11,785 / -2,798 | 27.1: 5,839 / 18,497 / -2,354 | 24.6: 3,571 / 10,995 / -6,486 |  |
| TE6_st10m_n14_m3.0 | 9.3: 8,930 / 11,976 / 2,118 | 8.3: 6,661 / 8,128 / 415 | 10.3: 10,039 / 12,755 / 5,224 | 9.0: 7,712 / 9,077 / 3,502 | 9.2: 8,306 / 10,420 / 3,897 |
| TE7_boll3m_n20_m1.5 | 22.1: 10,905 / 14,640 / -4,819 | 19.5: 9,226 / 9,544 / -5,098 | 24.3: 11,982 / 17,324 / -5,457 | 21.8: 9,184 / 10,329 / -2,880 | 22.5: 5,959 / 5,737 / -5,828 |
| TE7_boll3m_n30_m1.5 | 22.1: 10,818 / 8,386 / -5,525 | 19.8: 7,780 / 2,577 / -6,805 | 23.8: 12,539 / 8,181 / -4,469 | 21.6: 10,679 / 5,750 / -6,787 | 22.6: 7,099 / 1,835 / -7,493 |
| TE7_emax5m_f20_s40 | 10.7: 5,573 / 6,650 / -3,731 | 9.5: 3,895 / 1,463 / -5,534 | 11.8: 6,680 / 7,376 / -1,652 | 10.3: 6,389 / 7,528 / -867 |  |
| TE7_emax5m_f20_s50 | 9.9: 5,054 / 5,613 / -2,979 | 8.9: 3,437 / 1,223 / -4,960 | 10.9: 6,436 / 5,728 / -775 | 9.5: 4,981 / 4,572 / -624 |  |
| TE7_kelt3m_n14_m1.0 | 23.1: 14,102 / 10,400 / -1,187 | 20.4: 13,289 / 8,107 / -2,944 | 25.2: 15,825 / 12,849 / 3,203 | 22.6: 11,762 / 8,434 / 6,437 | 23.0: 7,236 / 2,101 / 3,049 |
| TE7_kelt3m_n20_m1.0 | 22.1: 18,230 / 16,239 / -8,214 | 19.7: 17,342 / 10,687 / -8,148 | 24.3: 19,101 / 16,853 / -6,497 | 21.7: 14,049 / 8,718 / -2,641 | 22.5: 13,294 / 7,328 / -3,575 |

The wide-column result is stable across 0.5/0.7/ridge and holds with the bars-only HAR gate for the ST10m and Keltner-14 cells (HAR: kelt 14/1.0 wide WF 7.2k/hold 2.1k/span2 +3.0k, st10m wide 8.1k/10.6k/+6.0k), i.e. an NT8-deliverable gate exists, but it adds nothing over the unconditional entry.

## 8. T-B books
No T-B book passes or is a CANDIDATE in either column (0 of 44; the 'all' column has 0 PASS and 1 CANDIDATE, TB7_ORBNY_k3_P60_N). Wide columns are positive in PRE for 22 of 22 books but in the holdout for only 7 of 22 and negative in the 2023 span for 18 of 22 (e.g. TB3_EMA_k5_A3_N wide PRE +26k, TB2_WIL_k5_A3_FV wide WF +14.7k/hold +13.4k, TB6_VWAP_k5_A3_N wide hold +13k all fail span2 by -11k..-24k). Quiet columns are negative in PRE for 14 of 22 books and positive in the holdout for 15 of 22 - the same reversal as in section 6.

## 9. Executability, registration, files

* NT8-deliverable entry (bars) but **gate execution-server-only** (forecaster uses L2 state + VIX family); the HAR gate variant is bars-reproducible. `exec_status`: gate = EXEC-ONLY(forecaster) / HAR variant NT8-able, pending an identity test (not run: the gate does not change any PASS verdict).
* Series for D3L: `l2vast/ds3/out/SERIES/DS3_TA1__<cell>__wide.parquet` (direct basis, columns ld, pnl, pnl_1p5x, pnl_2x, trades) for the two wide PASS and five wide CANDIDATE columns; rows `l2vast/ds3/rows/DS3_TA1.json`. Registered to PAPER-ALL: `l2vast/struct48/paper_all/ds3_TA1_*.json` (PASS/CANDIDATE wide columns only, expectation = WF direct).
* Ledger: +120 verdict cells, +360 sensitivity, +7 HAR (DS3_TA1*). Holdout looks: DS3_TA1 once (disclosed that T-ENTRY/T-B source cells had looked).
* Code: `l2vast/ds3/code/ta/` (ta1_pseries.py, ta_lib.py, ta_tb.py, ta1_prereg.py, ta1_run.py, ta_direct.py, ta1_direct_run.py, ta1_effect.py, ta1_report.py).
* **Questions for the user (MORNING.md, not blocking):** none structural; the full 191+279 x 3 table was restricted per the order to preregs of <= 30; say if the remaining 340 cells should be scored as a labelled exploration.
