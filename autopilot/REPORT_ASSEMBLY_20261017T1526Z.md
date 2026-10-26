# REPORT ASSEMBLY 20261017T1526Z  (basisvoid2)

Portfolio assembly over the book LIBRARY, pre-registered in PREREG_AUTOPILOT.md (section ASSEMBLY). Selection on CLEAN (2023-08..2025-07) weekly Sharpe only; H1 (2025-08-01..2026-02-06) and H2 (2026-02-07..2026-10-13) read once for the top 10 and the marked rows. UNTOUCHED never read.

**Headline.** Best stage-1 clean plateau-passing weekly Sharpe in the library at T=16: **7.68**; expected best-of-search by chance (timing-destroyed library, 100 replicates): mean 8.23, p50 8.20, p95 8.90, real rank 0.07. Edge-destroyed null (N2, 30 reps): mean 6.66, p95 7.16.
Best portfolio (stage 2, T=16): C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3, RY5_E1_K4_a0.25_sg+1 x6, SW10CO/NQ_3 x4, SW14CO/ES_1 x3; clean/H1/H2 weekly Sharpe 7.60/2.48/2.48 versus live pair 8/8 1.46/2.83/2.26.

## 1. Pool and pre-filter (pre-registered rule)

- Library rows 38422, loaded 38404, eligible (active, not WITHDRAWN, full clean coverage) 38200, after de-duplication (|corr|>=0.95) 34119, WITHDRAWN excluded 0.
- Pool = ST, HM, WT-10 + all leads (91 on the deduped set) + top 150 others by clean standalone Sharpe = **243 books**. WT-10 book(s) in pool: WT10.
- Stage-1 feasible subsets searched at T=16: 2,884,686 (k=2,3,4 books, all integer allocations summing to 16 with >=1 contract each, plateau: all +-1-contract transfers keep >=75%).

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
| 1 | C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3, RY5_E1_K4_a0.25_sg+1 x6, SW10CO/NQ_3 x4, SW14CO/ES_1 x3 | A1[RY5_E1_K4_a0.25_sg+1 x6]+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3+SW10CO/NQ_3 x4+SW14CO/ES_1 x3 | 7.60 | 2.48 | 2.48 | -76.8k | 238k | -73.2k | 10.4k / 0.14 | 24k |  s1=7.61 plateau>=0.95 |
| 2 | C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3, RY5_E1_K4_a0.25_sg+1 x5, SW10CO/NQ_3 x5, SW36CO/GC_1 x3 | A1[RY5_E1_K4_a0.25_sg+1 x5]+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3+SW10CO/NQ_3 x5+SW36CO/GC_1 x3 | 7.53 | 0.04 | 1.44 | -76.8k | 379k | -76.8k | 18.0k / 0.32 | 24k |  s1=7.50 plateau>=0.94 |
| 3 | B1leg_BTC/5_ST_14_3.0_200_k_0.2 x3, RY5_E1_K4_a0.25_sg+1 x5, SW10CO/NQ_3 x4, C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4 | A1[RY5_E1_K4_a0.25_sg+1 x5]+B1leg_BTC/5_ST_14_3.0_200_k_0.2 x3+SW10CO/NQ_3 x4+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4 | 7.47 | 1.95 | 1.55 | -76.8k | 280k | -73.5k | 12.0k / 0.12 | 24k |  s1=7.39 plateau>=0.89 |
| 4 | C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3, RY5_E1_K4_a0.5_sg-1 x5, SW10CO/NQ_3 x5, SW36CO/GC_1 x3 | A1[RY5_E1_K4_a0.5_sg-1 x5]+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3+SW10CO/NQ_3 x5+SW36CO/GC_1 x3 | 7.43 | -0.16 | 1.43 | -76.8k | 417k | -76.8k | 19.4k / 0.23 | 24k |  s1=7.43 plateau>=0.94 |
| 5 | B1leg_BTC/15_WT_20_3.0_100_m_2.0 x4, RY5_E1_K4_a0.25_sg+1 x5, SW10CO/NQ_3 x4, SW36CO/GC_1 x3 | A1[RY5_E1_K4_a0.25_sg+1 x5]+B1leg_BTC/15_WT_20_3.0_100_m_2.0 x4+SW10CO/NQ_3 x4+SW36CO/GC_1 x3 | 7.42 | 0.65 | 3.04 | -76.8k | 320k | -67.4k | 22.0k / 0.28 | 24k |  s1=7.41 plateau>=0.92 |
| 6 | T3S1_G_G_bb3/BB_054_p1_ts120 x3, C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4, RY5_E1_K4_a0.25_sg+1 x5, SW10CO/NQ_3 x4 | A1[RY5_E1_K4_a0.25_sg+1 x5]+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4+SW10CO/NQ_3 x4 ; A2[T3S1_G_G_bb3/BB_054_p1_ts120 x3] | 7.42 | 0.90 | 1.30 | -76.8k | 312k | -70.3k | 13.2k / 0.12 | 24k |  s1=7.68 plateau>=0.95 |
| 7 | RY5_E1_K4_a0.25_sg+1 x5, SW10CO/NQ_3 x5, SW14CO/ES_1 x3, SW36CO/GC_1 x3 | A1[RY5_E1_K4_a0.25_sg+1 x5]+SW10CO/NQ_3 x5+SW14CO/ES_1 x3+SW36CO/GC_1 x3 | 7.37 | 0.59 | 2.75 | -76.8k | 343k | -70.5k | 19.9k / 0.29 | 24k |  s1=7.44 plateau>=0.91 |
| 8 | S8ALL/S8_mon_h1_YM x3, RY5_E1_K4_a0.25_sg+1 x6, SW10CO/NQ_3 x4, SW26CO/NQ_1 x3 | A1[RY5_E1_K4_a0.25_sg+1 x6]+S8ALL/S8_mon_h1_YM x3+SW10CO/NQ_3 x4+SW26CO/NQ_1 x3 | 7.36 | 3.19 | 4.18 | -76.8k | 169k | -59.2k | 22.4k / 0.09 | 82k | PORTFOLIO-LEAD s1=7.27 plateau>=0.95 |
| 9 | RY5_E1_K4_a0.25_sg+1 x6, SW10CO/NQ_3 x5, Q11CO/BTC_1 x2, C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3 | A1[RY5_E1_K4_a0.25_sg+1 x6]+SW10CO/NQ_3 x5+Q11CO/BTC_1 x2+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3 | 7.33 | 1.44 | 2.45 | -76.8k | 271k | -74.7k | 19.7k / 0.20 | 24k |  s1=7.26 plateau>=0.94 |
| 10 | B1leg_BTC/15_WT_20_3.0_100_m_2.0 x3, RY5_E1_K4_a0.25_sg+1 x6, SW10CO/NQ_3 x4, C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3 | A1[RY5_E1_K4_a0.25_sg+1 x6]+B1leg_BTC/15_WT_20_3.0_100_m_2.0 x3+SW10CO/NQ_3 x4+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3 | 7.33 | 2.46 | 2.54 | -76.8k | 249k | -68.7k | 14.5k / 0.07 | 24k |  s1=7.32 plateau>=0.92 |

## 4. Top portfolios, T = 12 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 6/6 | ST x6, HM x6 | A1[ST6/HM6] | 1.46 | 2.83 | 2.26 | -61.9k | 210k | -59.4k | -58.7k / 1.00 | 18k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x5, HM x5, WT10 x2 | A1[ST5/HM5] ; A2[WT-10 x2] | 1.79 | 3.23 | 2.42 | -57.9k | 136k | -53.3k | -47.4k / -0.03 | 18k |  |
| 1 | C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3, RY5_E1_K4_a0.25_sg+1 x4, SW10CO/NQ_3 x3, SW14CO/ES_1 x2 | A1[RY5_E1_K4_a0.25_sg+1 x4]+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3+SW10CO/NQ_3 x3+SW14CO/ES_1 x2 | 7.60 | 1.77 | 1.66 | -57.6k | 198k | -56.6k | 5.9k / 0.16 | 18k |  s1=7.57 plateau>=0.88 |
| 2 | B1leg_BTC/5_ST_14_3.0_200_k_0.2 x2, C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3, RY5_E1_K4_a0.25_sg+1 x4, SW10CO/NQ_3 x3 | A1[RY5_E1_K4_a0.25_sg+1 x4]+B1leg_BTC/5_ST_14_3.0_200_k_0.2 x2+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3+SW10CO/NQ_3 x3 | 7.46 | 2.00 | 1.68 | -57.6k | 198k | -56.0k | 9.4k / 0.12 | 18k |  s1=7.40 plateau>=0.88 |
| 3 | B1leg_BTC/15_WT_20_3.0_100_m_2.0 x3, RY5_E1_K4_a0.25_sg+1 x4, SW10CO/NQ_3 x3, SW36CO/GC_1 x2 | A1[RY5_E1_K4_a0.25_sg+1 x4]+B1leg_BTC/15_WT_20_3.0_100_m_2.0 x3+SW10CO/NQ_3 x3+SW36CO/GC_1 x2 | 7.40 | 0.88 | 3.28 | -57.6k | 223k | -50.6k | 16.8k / 0.24 | 18k |  s1=7.38 plateau>=0.87 |
| 4 | C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3, RY5_E1_K4_a0.25_sg+1 x4, SW10CO/NQ_3 x3, T3S1_G_G_bb3/BB_054_p1_ts120 x2 | A1[RY5_E1_K4_a0.25_sg+1 x4]+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3+SW10CO/NQ_3 x3 ; A2[T3S1_G_G_bb3/BB_054_p1_ts120 x2] | 7.39 | 1.05 | 1.39 | -57.6k | 223k | -53.2k | 10.2k / 0.12 | 18k |  s1=7.67 plateau>=0.94 |
| 5 | S8ALL/S8_mon_h1_YM x3, RY5_E1_K4_a0.25_sg+1 x4, SW10CO/NQ_3 x3, SW26CO/NQ_1 x2 | A1[RY5_E1_K4_a0.25_sg+1 x4]+S8ALL/S8_mon_h1_YM x3+SW10CO/NQ_3 x3+SW26CO/NQ_1 x2 | 7.39 | 2.85 | 3.89 | -57.6k | 135k | -45.2k | 14.4k / 0.16 | 76k | PORTFOLIO-LEAD s1=7.25 plateau>=0.94 |

## 5. Top portfolios, T = 20 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 10/10 | ST x10, HM x10 | A1[ST10/HM10] | 1.46 | 2.83 | 2.26 | -103.2k | 350k | -99.0k | -97.8k / 1.00 | 30k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x8, HM x8, WT10 x4 | A1[ST8/HM8] ; A2[WT-10 x4] | 1.87 | 3.30 | 2.45 | -96.5k | 215k | -87.2k | -75.2k / -0.06 | 30k |  |
| 1 | C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4, RY5_E1_K4_a0.25_sg+1 x7, SW10CO/NQ_3 x5, SW14CO/ES_1 x4 | A1[RY5_E1_K4_a0.25_sg+1 x7]+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4+SW10CO/NQ_3 x5+SW14CO/ES_1 x4 | 7.62 | 2.27 | 2.24 | -96.0k | 309k | -91.4k | 11.5k / 0.15 | 30k |  s1=7.63 plateau>=0.96 |
| 2 | B1leg_BTC/5_ST_14_3.0_200_k_0.2 x4, RY5_E1_K4_a0.25_sg+1 x7, SW10CO/NQ_3 x5, C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4 | A1[RY5_E1_K4_a0.25_sg+1 x7]+B1leg_BTC/5_ST_14_3.0_200_k_0.2 x4+SW10CO/NQ_3 x5+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4 | 7.51 | 2.76 | 2.10 | -96.0k | 285k | -91.5k | 18.7k / 0.09 | 30k |  s1=7.43 plateau>=0.94 |
| 3 | B1leg_BTC/15_WT_20_3.0_100_m_2.0 x6, RY5_E1_K4_a0.25_sg+1 x6, SW10CO/NQ_3 x5, SW36CO/GC_1 x3 | A1[RY5_E1_K4_a0.25_sg+1 x6]+B1leg_BTC/15_WT_20_3.0_100_m_2.0 x6+SW10CO/NQ_3 x5+SW36CO/GC_1 x3 | 7.44 | 0.83 | 3.14 | -96.0k | 341k | -82.5k | 26.4k / 0.21 | 30k |  s1=7.42 plateau>=0.91 |
| 4 | C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4, RY5_E1_K4_a0.5_sg-1 x6, SW10CO/NQ_3 x6, SW36CO/GC_1 x4 | A1[RY5_E1_K4_a0.5_sg-1 x6]+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4+SW10CO/NQ_3 x6+SW36CO/GC_1 x4 | 7.44 | -0.25 | 1.21 | -96.0k | 527k | -96.0k | 23.3k / 0.25 | 30k |  s1=7.44 plateau>=0.94 |
| 5 | T4E/STHM_BTC_k=4.0_ALL_slip1t_fullsz$0.20/micro-eq x3, RY5_E1_K4_a0.25_sg+1 x7, SW10CO/NQ_3 x6, C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4 | A1[RY5_E1_K4_a0.25_sg+1 x7]+T4E/STHM_BTC_k=4.0_ALL_slip1t_fullsz$0.20/micro-eq x3+SW10CO/NQ_3 x6+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x4 | 7.42 | 2.70 | 2.35 | -96.0k | 300k | -89.8k | 23.2k / 0.07 | 30k |  s1=7.38 plateau>=0.95 |

## 6. Chance expectation (own null)

- N1 timing-destroyed library (100 reps, independent circular shift per book, same pre-filter and plateau): best-of-search stage-1 clean Sharpe mean 8.23, sd 0.42, p95 8.90, max 9.57; real 7.68 (rank 0.07).
- N2 edge-destroyed (weekly random sign flip of de-meaned books, 30 reps): mean 6.66, p95 7.16.
- Reading: N1 keeps each book's own edge and destroys only the alignment between books, so it measures how much of the best portfolio Sharpe is combination/diversification luck given the pool; N2 measures pure selection noise.

## 7. Stage-1 context

- T=16: best stage-1 7.68, top-5 stage-1 values 7.68, 7.68, 7.68, 7.68, 7.61
- T=12: best stage-1 7.67, top-5 stage-1 values 7.67, 7.67, 7.67, 7.67, 7.57
- T=20: best stage-1 7.66, top-5 stage-1 values 7.66, 7.66, 7.66, 7.66, 7.63

Runtime 2.5 min. Pool books (first 60 by clean Sharpe): RY5_E1_K4_a0.25_sg+1 (4.15), RY5_E1_K4_a0.5_sg-1 (3.68), C10S1_GC/60_macd_12_26_brk_3.0_all_0 (2.70), T3S1_BOOKS_B/B_HM_20_55_150 (2.65), T3S1_BOOKS_H/H_HM_1min1 (2.64), T3S1_BOOKS_B/B_HM_20_55_200 (2.63), SW10CO/NQ_1 (2.63), T3S1_G_G_v1/G_G5_obv_n120_tf1_e200_delta (2.58), SW10CO/NQ_2 (2.56), C10S1_6J/60_ema_9_21_time_8_all_1 (2.56), SW26CO/NQ_1 (2.55), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_t5 (2.55), T3S1_BOOKS_B/B_WT_30_1.5_50 (2.53), T3S1_BOOKS_B/B_WT_20_1.5_50 (2.52), T3S1_G_G_v1/G_G4_roc_n60_tf1_e200_adx20 (2.50), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_delta (2.49), S8ALL/S8_mon_h1_RTY (2.47), T3S1_BOOKS_B/B_ST_120_2.0_150 (2.47), T3S1_G_G_bb3/BB_054_p1_ts120 (2.45), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_none (2.42), SW10CO/NQ_3 (2.42), T3S1_G_G_v1/G_G6_fvg_n20_tf5_eNone_none (2.41), T3S1_G_G_bb1/BB_169_p2_ts30 (2.41), SW32CO/NQ_1 (2.40), B1CO/BTC_1 (2.40), T3S1_G_G_v1/G_G4_stochrsi_n14_lo30_hi80_tf5_e200_adx20 (2.38), S8ALL/S8_mon_h1_YM (2.37), L92_BTC_widetrail_ensemble54 (2.36), T3S1_BOOKS_B/B_HM_20_55_300 (2.36), T3S1_BOOKS_B/B_WT_15_1.75_50 (2.35), SW18CO/NQ_1 (2.34), S8ALL/S8_mon_h1_NQ (2.33), T3S1_BOOKS_B/B_ST_150_2.0_150 (2.32), GAPMAP_B2356/G2__G2_GC_10_1_h5_BTC (2.29), T3S1_G_G_bb4/BB_073_p0_br60 (2.28), SW5CO/YM_1 (2.28), Q19CO/BTC_1 (2.27), T3S1_G_G_bb4/BB_073_p0_ts120 (2.26), T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 (2.26), D1F4/ES_k0.75_slip0.0_ST (2.25), SW5CO/YM_2 (2.25), T3S1_G_G_v1/G_G1_macross_kindVIDYA_f5_s20_tf5_eNone_delta (2.24), T3S3/S3_12_NQ_ORB_{'N':15,'stopmode':0,'tm':1.0,'reentry':0} (2.24), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_none (2.23), SW17CO/NQ_1 (2.23), WThist/ATR10_m3_ema0_tf10_X1 (2.23), SW14CO/ES_1 (2.22), SW18CO/ES_1 (2.18), V5P2/c1174 (2.18), B1leg_ETH/15_WT_20_3.0_100_k_0.15 (2.18), T3S1_BOOKS_B/B_ST_180_2.25_150 (2.18), B1CO/BTC_2 (2.18), SW31CO/BTC_1 (2.17), SW20CO/RTY_1 (2.15), WThist/ATR14_m3_ema0_tf10_X1 (2.15), SW4CO/RTY_1 (2.15), SW26CO/NQ_2 (2.15), T3S1_BOOKS_B/B_WT_20_1.75_50 (2.15), T3S1_BOOKS_B/B_WT_15_1.5_50 (2.14), Q1CCO/NQ_6 (2.14)

DONE ASSEMBLY 20261017T1526Z
