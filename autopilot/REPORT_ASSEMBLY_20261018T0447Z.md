# REPORT ASSEMBLY 20261018T0447Z  (daemon)

Portfolio assembly over the book LIBRARY, pre-registered in PREREG_AUTOPILOT.md (section ASSEMBLY). Selection on CLEAN (2023-08..2025-07) weekly Sharpe only; H1 (2025-08-01..2026-02-06) and H2 (2026-02-07..2026-10-13) read once for the top 10 and the marked rows. UNTOUCHED never read.

**Headline.** Best stage-1 clean plateau-passing weekly Sharpe in the library at T=16: **6.42**; expected best-of-search by chance (timing-destroyed library, 100 replicates): mean 7.07, p50 7.05, p95 7.46, real rank 0.00. Edge-destroyed null (N2, 30 reps): mean 6.67, p95 7.00.
Best portfolio (stage 2, T=16): S8ALL/S8_mon_h1_RTY x4, Q1CCO/NQ_6 x4, SW26CO/NQ_1 x3, B1CO/BTC_1 x5; clean/H1/H2 weekly Sharpe 6.26/1.98/0.41 versus live pair 8/8 1.46/2.83/2.26.

## 1. Pool and pre-filter (pre-registered rule)

- Library rows 38412, loaded 38394, eligible (active, not WITHDRAWN, full clean coverage) 38190, after de-duplication (|corr|>=0.95) 34111, WITHDRAWN excluded 0.
- Pool = ST, HM, WT-10 + all leads (91 on the deduped set) + top 150 others by clean standalone Sharpe = **243 books**. WT-10 book(s) in pool: WT10.
- Stage-1 feasible subsets searched at T=16: 2,916,185 (k=2,3,4 books, all integer allocations summing to 16 with >=1 contract each, plateau: all +-1-contract transfers keep >=75%).

## 2. Method and approximations (as pre-registered)

- Unit: stored book series / 8 per contract-equivalent. Accounts: max 2; NQ_INTRADAY books net, so ST/HM share one account (live) and any other NQ_INTRADAY book sits in a different account; OTHER_INSTR books ride in account 1.
- ST/HM block = EXACT corrected-engine series for that (wST,wHM) mix at R_acct = 9600*(wST+wHM)/16 (b11_nt8 bookscale grid, library/work/pairgrid.npz). All other members: stored series x contracts/8 through a DAY-LEVEL account approximation (day P&L capped at +8R_acct, week cumulative floored at -8R_acct with remaining days of that week zeroed, R_acct = 9600*contracts/16); the 2R/67% give-back and -2R day stop need intraday paths and are NOT applied; exact B11 re-simulation is only possible for ST/HM mixes.
- Stage 1 selects on the linear (unlocked, standalone-series) clean weekly Sharpe; stage 2 re-scores the top 2000 with the exact block + approximation and re-checks the plateau with the same engine; rank on stage-2 clean Sharpe; distinct book sets and weekly corr < 0.98 to higher-ranked rows.
- Stored series are at the stored cost model of each book (1 tick/side + commission unless the book note says otherwise); margin proxy = contracts x $1,500 (intraday) or $21,000 (multi-day) - unverified proxy.

## 3. Top portfolios, T = 16 contracts-equivalent (primary)

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 8/8 | ST x8, HM x8 | A1[ST8/HM8] | 1.46 | 2.83 | 2.26 | -82.5k | 280k | -79.2k | -78.2k / 1.00 | 24k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x6, HM x6, WT10 x4 | A1[ST6/HM6] ; A2[WT-10 x4] | 1.98 | 3.41 | 2.47 | -77.1k | 170k | -68.0k | -55.6k / -0.09 | 24k |  |
| 1 | S8ALL/S8_mon_h1_RTY x4, Q1CCO/NQ_6 x4, SW26CO/NQ_1 x3, B1CO/BTC_1 x5 | A1[]+S8ALL/S8_mon_h1_RTY x4+Q1CCO/NQ_6 x4+SW26CO/NQ_1 x3+B1CO/BTC_1 x5 | 6.26 | 1.98 | 0.41 | -76.8k | 331k | -64.3k | 10.0k / 0.30 | 102k |  s1=6.12 plateau>=0.92 |
| 2 | WThist/ATR10_m3_ema0_tf10_X1 x5, T3S1_G_G_bb6/BB_110_p2_ts30 x3, L92_BTC_widetrail_ensemble54 x6, C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x2 | A1[WThist/ATR10_m3_ema0_tf10_X1 x5]+L92_BTC_widetrail_ensemble54 x6+C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x2 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 6.22 | 2.33 | 0.11 | -59.6k | 171k | -39.5k | 7.6k / 0.07 | 24k |  s1=6.01 plateau>=0.91 |
| 3 | WThist/ATR10_m3_ema0_tf10_X1 x7, T3S1_G_G_bb6/BB_110_p2_ts30 x3, Q19CO/BTC_1 x3, C10S1_ZN/240_ema_20_60_opp_0_all_0 x3 | A1[WThist/ATR10_m3_ema0_tf10_X1 x7]+Q19CO/BTC_1 x3+C10S1_ZN/240_ema_20_60_opp_0_all_0 x3 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 6.22 | 1.24 | 0.79 | -72.5k | 207k | -53.9k | 12.5k / -0.05 | 24k |  s1=6.02 plateau>=0.92 |
| 4 | WThist/ATR10_m3_ema0_tf10_X1 x7, T3S1_G_G_bb6/BB_110_p2_ts30 x3, Q19CO/BTC_1 x3, C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x3 | A1[WThist/ATR10_m3_ema0_tf10_X1 x7]+Q19CO/BTC_1 x3+C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x3 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 6.20 | 0.87 | 0.69 | -76.8k | 218k | -56.9k | 15.7k / 0.03 | 24k |  s1=6.09 plateau>=0.91 |
| 5 | WThist/ATR10_m3_ema0_tf10_X1 x5, T3S1_G_G_bb6/BB_110_p2_ts30 x3, L92_BTC_widetrail_ensemble54 x6, SW10CO/NQ_3 x2 | A1[WThist/ATR10_m3_ema0_tf10_X1 x5]+L92_BTC_widetrail_ensemble54 x6+SW10CO/NQ_3 x2 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 6.18 | 2.83 | 1.10 | -61.3k | 138k | -40.5k | 7.3k / -0.18 | 24k |  s1=5.94 plateau>=0.92 |
| 6 | T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 x3, S8ALL/S8_mon_h1_RTY x4, B1CO/BTC_1 x5, Q1CCO/NQ_6 x4 | A1[T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 x3]+S8ALL/S8_mon_h1_RTY x4+B1CO/BTC_1 x5+Q1CCO/NQ_6 x4 | 6.14 | 1.32 | -0.36 | -76.8k | 343k | -66.0k | 3.0k / 0.10 | 102k |  s1=5.95 plateau>=0.93 |
| 7 | S8ALL/S8_mon_h1_RTY x4, B1CO/BTC_1 x5, Q1CCO/NQ_6 x4, Q16CO/CL_1 x3 | A1[]+S8ALL/S8_mon_h1_RTY x4+B1CO/BTC_1 x5+Q1CCO/NQ_6 x4+Q16CO/CL_1 x3 | 6.14 | 0.06 | -0.55 | -76.8k | 396k | -76.7k | 10.3k / 0.08 | 102k |  s1=6.06 plateau>=0.94 |
| 8 | WThist/ATR10_m3_ema0_tf10_X1 x5, T3S1_G_G_bb6/BB_110_p2_ts30 x3, C10S1_ZN/240_ema_20_60_opp_0_all_0 x2, L92_BTC_widetrail_ensemble54 x6 | A1[WThist/ATR10_m3_ema0_tf10_X1 x5]+C10S1_ZN/240_ema_20_60_opp_0_all_0 x2+L92_BTC_widetrail_ensemble54 x6 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 6.14 | 2.65 | 0.21 | -59.6k | 171k | -39.8k | 5.5k / -0.00 | 24k |  s1=5.83 plateau>=0.93 |
| 9 | T3S1_G_G_bb1/BB_169_p2_ts30 x3, S8ALL/S8_mon_h1_RTY x4, B1CO/BTC_1 x6, Q1CCO/NQ_6 x3 | A1[T3S1_G_G_bb1/BB_169_p2_ts30 x3]+S8ALL/S8_mon_h1_RTY x4+B1CO/BTC_1 x6+Q1CCO/NQ_6 x3 | 6.11 | 0.28 | 0.32 | -76.8k | 253k | -65.3k | 7.8k / 0.23 | 102k |  s1=5.93 plateau>=0.90 |
| 10 | T3S1_G_G_v1/G_G5_obv_n120_tf1_e200_delta x4, SW14CO/ES_1 x3, SW20CO/RTY_1 x4, SW32CO/NQ_1 x5 | A1[T3S1_G_G_v1/G_G5_obv_n120_tf1_e200_delta x4]+SW14CO/ES_1 x3+SW20CO/RTY_1 x4+SW32CO/NQ_1 x5 | 6.10 | -1.33 | 2.03 | -76.8k | 436k | -73.7k | 6.4k / 0.13 | 24k |  s1=6.09 plateau>=0.86 |

## 4. Top portfolios, T = 12 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 6/6 | ST x6, HM x6 | A1[ST6/HM6] | 1.46 | 2.83 | 2.26 | -61.9k | 210k | -59.4k | -58.7k / 1.00 | 18k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x5, HM x5, WT10 x2 | A1[ST5/HM5] ; A2[WT-10 x2] | 1.79 | 3.23 | 2.42 | -57.9k | 136k | -53.3k | -47.4k / -0.03 | 18k |  |
| 1 | WThist/ATR10_m3_ema0_tf10_X1 x5, T3S1_G_G_bb6/BB_110_p2_ts30 x3, Q19CO/BTC_1 x2, C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x2 | A1[WThist/ATR10_m3_ema0_tf10_X1 x5]+Q19CO/BTC_1 x2+C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x2 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 6.38 | 1.03 | 0.83 | -57.6k | 154k | -42.3k | 10.8k / 0.04 | 18k |  s1=6.04 plateau>=0.88 |
| 2 | WThist/ATR10_m3_ema0_tf10_X1 x5, T3S1_G_G_bb6/BB_110_p2_ts30 x3, Q19CO/BTC_1 x2, C10S1_ZN/240_ema_20_60_opp_0_all_0 x2 | A1[WThist/ATR10_m3_ema0_tf10_X1 x5]+Q19CO/BTC_1 x2+C10S1_ZN/240_ema_20_60_opp_0_all_0 x2 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 6.35 | 1.34 | 0.91 | -56.0k | 147k | -39.4k | 8.6k / -0.04 | 18k |  s1=5.93 plateau>=0.89 |
| 3 | S8ALL/S8_mon_h1_RTY x3, Q1CCO/NQ_6 x3, SW26CO/NQ_1 x2, B1CO/BTC_1 x4 | A1[]+S8ALL/S8_mon_h1_RTY x3+Q1CCO/NQ_6 x3+SW26CO/NQ_1 x2+B1CO/BTC_1 x4 | 6.28 | 1.91 | 0.33 | -57.6k | 248k | -47.8k | 6.9k / 0.29 | 76k |  s1=6.11 plateau>=0.89 |
| 4 | WThist/ATR10_m3_ema0_tf10_X1 x4, T3S1_G_G_bb6/BB_110_p2_ts30 x3, B1CO/BTC_1 x3, C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x2 | A1[WThist/ATR10_m3_ema0_tf10_X1 x4]+B1CO/BTC_1 x3+C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x2 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 6.20 | 2.50 | -0.47 | -50.8k | 159k | -35.4k | 5.4k / 0.14 | 18k |  s1=5.78 plateau>=0.89 |
| 5 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x4, Q1CCO/NQ_6 x3, Q16CO/CL_1 x2 | A1[]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x4+Q1CCO/NQ_6 x3+Q16CO/CL_1 x2 | 6.18 | 0.14 | -0.54 | -57.6k | 268k | -56.0k | 7.2k / 0.08 | 76k |  s1=6.08 plateau>=0.91 |

## 5. Top portfolios, T = 20 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 10/10 | ST x10, HM x10 | A1[ST10/HM10] | 1.46 | 2.83 | 2.26 | -103.2k | 350k | -99.0k | -97.8k / 1.00 | 30k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x8, HM x8, WT10 x4 | A1[ST8/HM8] ; A2[WT-10 x4] | 1.87 | 3.30 | 2.45 | -96.5k | 215k | -87.2k | -75.2k / -0.06 | 30k |  |
| 1 | S8ALL/S8_mon_h1_RTY x5, B1CO/BTC_1 x7, Q1CCO/NQ_6 x4, SW26CO/NQ_1 x4 | A1[]+S8ALL/S8_mon_h1_RTY x5+B1CO/BTC_1 x7+Q1CCO/NQ_6 x4+SW26CO/NQ_1 x4 | 6.32 | 2.38 | 0.28 | -96.0k | 416k | -79.2k | 11.5k / 0.32 | 128k |  s1=6.13 plateau>=0.95 |
| 2 | WThist/ATR10_m3_ema0_tf10_X1 x8, T3S1_G_G_bb6/BB_110_p2_ts30 x4, Q19CO/BTC_1 x4, C10S1_ZN/240_ema_20_60_opp_0_all_0 x4 | A1[WThist/ATR10_m3_ema0_tf10_X1 x8]+Q19CO/BTC_1 x4+C10S1_ZN/240_ema_20_60_opp_0_all_0 x4 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x4] | 6.30 | 1.13 | 0.80 | -85.2k | 260k | -67.7k | 15.9k / -0.05 | 30k |  s1=6.00 plateau>=0.95 |
| 3 | WThist/ATR10_m3_ema0_tf10_X1 x8, T3S1_G_G_bb6/BB_110_p2_ts30 x4, Q19CO/BTC_1 x4, C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x4 | A1[WThist/ATR10_m3_ema0_tf10_X1 x8]+Q19CO/BTC_1 x4+C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x4 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x4] | 6.29 | 0.76 | 0.70 | -96.0k | 274k | -71.8k | 20.2k / 0.04 | 30k |  s1=6.11 plateau>=0.93 |
| 4 | S8ALL/S8_mon_h1_RTY x5, B1CO/BTC_1 x7, Q1CCO/NQ_6 x5, Q16CO/CL_1 x3 | A1[]+S8ALL/S8_mon_h1_RTY x5+B1CO/BTC_1 x7+Q1CCO/NQ_6 x5+Q16CO/CL_1 x3 | 6.18 | 0.21 | -0.62 | -96.0k | 439k | -93.1k | 11.2k / 0.10 | 128k |  s1=6.06 plateau>=0.96 |
| 5 | WThist/ATR10_m3_ema0_tf10_X1 x7, T3S1_G_G_bb6/BB_110_p2_ts30 x4, B1CO/BTC_1 x6, C10S1_ZN/240_ema_20_60_opp_0_all_0 x3 | A1[WThist/ATR10_m3_ema0_tf10_X1 x7]+B1CO/BTC_1 x6+C10S1_ZN/240_ema_20_60_opp_0_all_0 x3 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x4] | 6.18 | 3.20 | -0.64 | -83.3k | 273k | -56.7k | 5.5k / 0.04 | 30k |  s1=5.88 plateau>=0.94 |

## 6. Chance expectation (own null)

- N1 timing-destroyed library (100 reps, independent circular shift per book, same pre-filter and plateau): best-of-search stage-1 clean Sharpe mean 7.07, sd 0.26, p95 7.46, max 8.23; real 6.42 (rank 0.00).
- N2 edge-destroyed (weekly random sign flip of de-meaned books, 30 reps): mean 6.67, p95 7.00.
- Reading: N1 keeps each book's own edge and destroys only the alignment between books, so it measures how much of the best portfolio Sharpe is combination/diversification luck given the pool; N2 measures pure selection noise.

## 7. Stage-1 context

- T=16: best stage-1 6.42, top-5 stage-1 values 6.42, 6.42, 6.42, 6.42, 6.42
- T=12: best stage-1 6.42, top-5 stage-1 values 6.42, 6.42, 6.42, 6.42, 6.42
- T=20: best stage-1 6.42, top-5 stage-1 values 6.42, 6.42, 6.42, 6.42, 6.42

Runtime 2.1 min. Pool books (first 60 by clean Sharpe): C10S1_GC/60_macd_12_26_brk_3.0_all_0 (2.70), T3S1_BOOKS_B/B_HM_20_55_150 (2.65), T3S1_BOOKS_H/H_HM_1min1 (2.64), T3S1_BOOKS_B/B_HM_20_55_200 (2.63), SW10CO/NQ_1 (2.63), T3S1_G_G_v1/G_G5_obv_n120_tf1_e200_delta (2.58), SW10CO/NQ_2 (2.56), C10S1_6J/60_ema_9_21_time_8_all_1 (2.56), SW26CO/NQ_1 (2.55), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_t5 (2.55), T3S1_BOOKS_B/B_WT_30_1.5_50 (2.53), T3S1_BOOKS_B/B_WT_20_1.5_50 (2.52), T3S1_G_G_v1/G_G4_roc_n60_tf1_e200_adx20 (2.50), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_delta (2.49), S8ALL/S8_mon_h1_RTY (2.47), T3S1_BOOKS_B/B_ST_120_2.0_150 (2.47), T3S1_G_G_bb3/BB_054_p1_ts120 (2.45), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_none (2.42), SW10CO/NQ_3 (2.42), T3S1_G_G_v1/G_G6_fvg_n20_tf5_eNone_none (2.41), T3S1_G_G_bb1/BB_169_p2_ts30 (2.41), SW32CO/NQ_1 (2.40), B1CO/BTC_1 (2.40), T3S1_G_G_v1/G_G4_stochrsi_n14_lo30_hi80_tf5_e200_adx20 (2.38), S8ALL/S8_mon_h1_YM (2.37), L92_BTC_widetrail_ensemble54 (2.36), T3S1_BOOKS_B/B_HM_20_55_300 (2.36), T3S1_BOOKS_B/B_WT_15_1.75_50 (2.35), SW18CO/NQ_1 (2.34), S8ALL/S8_mon_h1_NQ (2.33), T3S1_BOOKS_B/B_ST_150_2.0_150 (2.32), GAPMAP_B2356/G2__G2_GC_10_1_h5_BTC (2.29), T3S1_G_G_bb4/BB_073_p0_br60 (2.28), SW5CO/YM_1 (2.28), Q19CO/BTC_1 (2.27), T3S1_G_G_bb4/BB_073_p0_ts120 (2.26), T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 (2.26), D1F4/ES_k0.75_slip0.0_ST (2.25), SW5CO/YM_2 (2.25), T3S1_G_G_v1/G_G1_macross_kindVIDYA_f5_s20_tf5_eNone_delta (2.24), T3S3/S3_12_NQ_ORB_{'N':15,'stopmode':0,'tm':1.0,'reentry':0} (2.24), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_none (2.23), SW17CO/NQ_1 (2.23), WThist/ATR10_m3_ema0_tf10_X1 (2.23), SW14CO/ES_1 (2.22), SW18CO/ES_1 (2.18), V5P2/c1174 (2.18), B1leg_ETH/15_WT_20_3.0_100_k_0.15 (2.18), T3S1_BOOKS_B/B_ST_180_2.25_150 (2.18), B1CO/BTC_2 (2.18), SW31CO/BTC_1 (2.17), SW20CO/RTY_1 (2.15), WThist/ATR14_m3_ema0_tf10_X1 (2.15), SW4CO/RTY_1 (2.15), SW26CO/NQ_2 (2.15), T3S1_BOOKS_B/B_WT_20_1.75_50 (2.15), T3S1_BOOKS_B/B_WT_15_1.5_50 (2.14), Q1CCO/NQ_6 (2.14), T3S1_G_G_v1/G_G1_macross_kindKAMA_f10_s50_tf5_e200_t5 (2.14), B1CO/BTC_3 (2.13)

DONE ASSEMBLY 20261018T0447Z
