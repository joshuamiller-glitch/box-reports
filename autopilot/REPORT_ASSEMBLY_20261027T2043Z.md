# REPORT ASSEMBLY 20261027T2043Z  (daemon)

Portfolio assembly over the book LIBRARY, pre-registered in PREREG_AUTOPILOT.md (section ASSEMBLY). Selection on CLEAN (2023-08..2025-07) weekly Sharpe only; H1 (2025-08-01..2026-02-06) and H2 (2026-02-07..2026-10-13) read once for the top 10 and the marked rows. UNTOUCHED never read.

**Headline.** Best stage-1 clean plateau-passing weekly Sharpe in the library at T=16: **7.26**; expected best-of-search by chance (timing-destroyed library, 100 replicates): mean 7.92, p50 7.78, p95 9.07, real rank 0.20. Edge-destroyed null (N2, 30 reps): mean 6.76, p95 7.25.
Best portfolio (stage 2, T=16): S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x6, Q1CCO/NQ_6 x3, RU11_GC_IMP3_5_1.5 x4; clean/H1/H2 weekly Sharpe 7.31/2.86/3.03 versus live pair 8/8 1.46/2.83/2.26.

## 1. Pool and pre-filter (pre-registered rule)

- Library rows 38452, loaded 38434, eligible (active, not WITHDRAWN, full clean coverage) 38229, after de-duplication (|corr|>=0.95) 34149, WITHDRAWN excluded 0.
- Pool = ST, HM, WT-10 + all leads (93 on the deduped set) + top 150 others by clean standalone Sharpe = **245 books**. WT-10 book(s) in pool: WT10.
- Stage-1 feasible subsets searched at T=16: 3,006,616 (k=2,3,4 books, all integer allocations summing to 16 with >=1 contract each, plateau: all +-1-contract transfers keep >=75%).

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
| 1 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x6, Q1CCO/NQ_6 x3, RU11_GC_IMP3_5_1.5 x4 | A1[]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x6+Q1CCO/NQ_6 x3+RU11_GC_IMP3_5_1.5 x4 | 7.31 | 2.86 | 3.03 | -76.8k | 156k | -54.5k | 14.7k / 0.30 | 82k | PORTFOLIO-LEAD s1=7.26 plateau>=0.95 |
| 2 | WThist/ATR10_m3_ema0_tf10_X1 x5, T3S1_G_G_bb6/BB_110_p2_ts30 x3, RU11_GC_IMP3_5_1.5 x4, B1CO/BTC_1 x4 | A1[WThist/ATR10_m3_ema0_tf10_X1 x5]+RU11_GC_IMP3_5_1.5 x4+B1CO/BTC_1 x4 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 7.21 | 5.56 | 4.65 | -71.5k | 135k | -41.2k | 14.6k / 0.08 | 24k | PORTFOLIO-LEAD s1=7.01 plateau>=0.94 |
| 3 | B1CO/BTC_7 x5, Q1CCO/NQ_6 x3, RU11_GC_IMP3_5_1.5 x4, S8ALL/S8_mon_h1_RTY x4 | A1[]+B1CO/BTC_7 x5+Q1CCO/NQ_6 x3+RU11_GC_IMP3_5_1.5 x4+S8ALL/S8_mon_h1_RTY x4 | 7.20 | 2.38 | 2.78 | -76.8k | 238k | -62.0k | 13.4k / 0.46 | 102k |  s1=7.07 plateau>=0.97 |
| 4 | T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 x4, S8ALL/S8_mon_h1_RTY x4, Q1CCO/NQ_6 x3, RU11_GC_IMP3_5_1.5 x5 | A1[T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 x4]+S8ALL/S8_mon_h1_RTY x4+Q1CCO/NQ_6 x3+RU11_GC_IMP3_5_1.5 x5 | 7.19 | 3.04 | 3.03 | -76.8k | 342k | -61.1k | 19.7k / 0.15 | 102k | PORTFOLIO-LEAD s1=7.12 plateau>=0.96 |
| 5 | T3S1_G_G_bb6/BB_110_p2_ts30 x3, B1leg_BTC/15_ST_8_2.0_20_m_3.0 x4, RU11_GC_IMP3_5_1.5 x4, WThist/ATR10_m3_ema0_tf10_X1 x5 | A1[WThist/ATR10_m3_ema0_tf10_X1 x5]+B1leg_BTC/15_ST_8_2.0_20_m_3.0 x4+RU11_GC_IMP3_5_1.5 x4 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 7.11 | 5.61 | 3.93 | -64.1k | 140k | -42.7k | 18.0k / 0.29 | 24k | PORTFOLIO-LEAD s1=6.98 plateau>=0.94 |
| 6 | WThist/ATR10_m3_ema0_tf10_X1 x4, T3S1_G_G_bb6/BB_110_p2_ts30 x2, RU11_GC_IMP3_5_1.5 x3, L92_BTC_widetrail_ensemble54 x7 | A1[WThist/ATR10_m3_ema0_tf10_X1 x4]+RU11_GC_IMP3_5_1.5 x3+L92_BTC_widetrail_ensemble54 x7 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x2] | 7.06 | 5.49 | 4.75 | -47.0k | 100k | -32.5k | 13.6k / 0.04 | 24k | PORTFOLIO-LEAD s1=7.01 plateau>=0.92 |
| 7 | WThist/ATR14_m3_ema0_tf10_X1 x4, T3S1_G_G_bb6/BB_110_p2_ts30 x3, RU11_GC_IMP3_5_1.5 x4, B1CO/BTC_1 x5 | A1[WThist/ATR14_m3_ema0_tf10_X1 x4]+RU11_GC_IMP3_5_1.5 x4+B1CO/BTC_1 x5 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 7.06 | 6.86 | 5.16 | -69.7k | 125k | -41.9k | 16.0k / 0.11 | 24k | PORTFOLIO-LEAD s1=6.76 plateau>=0.92 |
| 8 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_2 x6, Q1CCO/NQ_6 x3, RU11_GC_IMP3_5_1.5 x4 | A1[]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_2 x6+Q1CCO/NQ_6 x3+RU11_GC_IMP3_5_1.5 x4 | 7.06 | 3.07 | 2.88 | -73.2k | 214k | -51.5k | 12.5k / 0.41 | 82k | PORTFOLIO-LEAD s1=7.04 plateau>=0.95 |
| 9 | T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 x4, S8ALL/S8_mon_h1_RTY x4, RU11_GC_IMP3_5_1.5 x5, RU5_basket_GC_SI_HO_NG_NQ x3 | A1[T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 x4]+S8ALL/S8_mon_h1_RTY x4+RU11_GC_IMP3_5_1.5 x5+RU5_basket_GC_SI_HO_NG_NQ x3 | 7.06 | 4.03 | 2.91 | -76.8k | 347k | -61.9k | 22.6k / 0.15 | 102k | PORTFOLIO-LEAD s1=6.96 plateau>=0.97 |
| 10 | B1leg_BTC/15_ST_8_2.0_20_m_3.0 x5, Q1CCO/NQ_6 x3, RU11_GC_IMP3_5_1.5 x5, S8ALL/S8_mon_h1_RTY x3 | A1[]+B1leg_BTC/15_ST_8_2.0_20_m_3.0 x5+Q1CCO/NQ_6 x3+RU11_GC_IMP3_5_1.5 x5+S8ALL/S8_mon_h1_RTY x3 | 7.05 | 2.87 | 3.27 | -76.8k | 239k | -57.1k | 20.9k / 0.39 | 82k | PORTFOLIO-LEAD s1=7.02 plateau>=0.95 |

## 4. Top portfolios, T = 12 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 6/6 | ST x6, HM x6 | A1[ST6/HM6] | 1.46 | 2.83 | 2.26 | -61.9k | 210k | -59.4k | -58.7k / 1.00 | 18k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x5, HM x5, WT10 x2 | A1[ST5/HM5] ; A2[WT-10 x2] | 1.79 | 3.23 | 2.42 | -57.9k | 136k | -53.3k | -47.4k / -0.03 | 18k |  |
| 1 | WThist/ATR10_m3_ema0_tf10_X1 x3, L92_BTC_widetrail_ensemble54 x5, RU11_GC_IMP3_5_1.5 x2, T3S1_G_G_bb6/BB_110_p2_ts30 x2 | A1[WThist/ATR10_m3_ema0_tf10_X1 x3]+L92_BTC_widetrail_ensemble54 x5+RU11_GC_IMP3_5_1.5 x2 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x2] | 7.23 | 5.42 | 4.33 | -33.5k | 82k | -24.8k | 9.4k / 0.04 | 18k | PORTFOLIO-LEAD s1=7.01 plateau>=0.85 |
| 2 | S8ALL/S8_mon_h1_RTY x2, B1CO/BTC_1 x4, Q1CCO/NQ_6 x3, RU11_GC_IMP3_5_1.5 x3 | A1[]+S8ALL/S8_mon_h1_RTY x2+B1CO/BTC_1 x4+Q1CCO/NQ_6 x3+RU11_GC_IMP3_5_1.5 x3 | 7.20 | 2.46 | 2.95 | -57.6k | 143k | -42.9k | 12.0k / 0.23 | 57k |  s1=7.19 plateau>=0.89 |
| 3 | B1CO/BTC_7 x4, Q1CCO/NQ_6 x2, RU11_GC_IMP3_5_1.5 x3, S8ALL/S8_mon_h1_RTY x3 | A1[]+B1CO/BTC_7 x4+Q1CCO/NQ_6 x2+RU11_GC_IMP3_5_1.5 x3+S8ALL/S8_mon_h1_RTY x3 | 7.17 | 2.49 | 2.80 | -57.6k | 171k | -45.9k | 10.0k / 0.46 | 76k |  s1=7.04 plateau>=0.93 |
| 4 | T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 x3, S8ALL/S8_mon_h1_RTY x3, Q1CCO/NQ_6 x2, RU11_GC_IMP3_5_1.5 x4 | A1[T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 x3]+S8ALL/S8_mon_h1_RTY x3+Q1CCO/NQ_6 x2+RU11_GC_IMP3_5_1.5 x4 | 7.16 | 3.23 | 3.19 | -57.6k | 256k | -45.1k | 15.4k / 0.15 | 76k | PORTFOLIO-LEAD s1=7.08 plateau>=0.93 |
| 5 | B1leg_BTC/15_ST_8_2.0_20_m_3.0 x3, S8ALL/S8_mon_h1_RTY x3, Q1CCO/NQ_6 x3, RU11_GC_IMP3_5_1.5 x3 | A1[]+B1leg_BTC/15_ST_8_2.0_20_m_3.0 x3+S8ALL/S8_mon_h1_RTY x3+Q1CCO/NQ_6 x3+RU11_GC_IMP3_5_1.5 x3 | 7.14 | 2.26 | 2.70 | -57.6k | 208k | -48.1k | 13.1k / 0.42 | 76k |  s1=6.97 plateau>=0.90 |

## 5. Top portfolios, T = 20 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 10/10 | ST x10, HM x10 | A1[ST10/HM10] | 1.46 | 2.83 | 2.26 | -103.2k | 350k | -99.0k | -97.8k / 1.00 | 30k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x8, HM x8, WT10 x4 | A1[ST8/HM8] ; A2[WT-10 x4] | 1.87 | 3.30 | 2.45 | -96.5k | 215k | -87.2k | -75.2k / -0.06 | 30k |  |
| 1 | S8ALL/S8_mon_h1_RTY x4, B1CO/BTC_1 x7, RU11_GC_IMP3_5_1.5 x5, Q1CCO/NQ_6 x4 | A1[]+S8ALL/S8_mon_h1_RTY x4+B1CO/BTC_1 x7+RU11_GC_IMP3_5_1.5 x5+Q1CCO/NQ_6 x4 | 7.37 | 2.74 | 3.02 | -96.0k | 212k | -69.2k | 18.5k / 0.31 | 108k |  s1=7.30 plateau>=0.97 |
| 2 | T3S1_G_G_bb6/BB_110_p2_ts30 x4, B1CO/BTC_1 x5, RU11_GC_IMP3_5_1.5 x5, WThist/ATR10_m3_ema0_tf10_X1 x6 | A1[WThist/ATR10_m3_ema0_tf10_X1 x6]+B1CO/BTC_1 x5+RU11_GC_IMP3_5_1.5 x5 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x4] | 7.26 | 5.57 | 4.61 | -89.4k | 170k | -49.4k | 19.2k / 0.12 | 30k | PORTFOLIO-LEAD s1=7.01 plateau>=0.94 |
| 3 | T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 x5, S8ALL/S8_mon_h1_RTY x5, Q1CCO/NQ_6 x4, RU11_GC_IMP3_5_1.5 x6 | A1[T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 x5]+S8ALL/S8_mon_h1_RTY x5+Q1CCO/NQ_6 x4+RU11_GC_IMP3_5_1.5 x6 | 7.18 | 2.94 | 2.93 | -96.0k | 429k | -77.4k | 23.9k / 0.16 | 128k | PORTFOLIO-LEAD s1=7.12 plateau>=0.97 |
| 4 | WThist/ATR10_m3_ema0_tf10_X1 x6, T3S1_G_G_bb6/BB_110_p2_ts30 x4, RU11_GC_IMP3_5_1.5 x5, B1leg_BTC/15_ST_8_2.0_20_m_3.0 x5 | A1[WThist/ATR10_m3_ema0_tf10_X1 x6]+RU11_GC_IMP3_5_1.5 x5+B1leg_BTC/15_ST_8_2.0_20_m_3.0 x5 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x4] | 7.16 | 5.62 | 3.90 | -80.1k | 174k | -53.3k | 22.4k / 0.29 | 30k | PORTFOLIO-LEAD s1=6.98 plateau>=0.96 |
| 5 | WThist/ATR10_m3_ema0_tf10_X1 x5, T3S1_G_G_bb6/BB_110_p2_ts30 x3, RU11_GC_IMP3_5_1.5 x4, L92_BTC_widetrail_ensemble54 x8 | A1[WThist/ATR10_m3_ema0_tf10_X1 x5]+RU11_GC_IMP3_5_1.5 x4+L92_BTC_widetrail_ensemble54 x8 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 7.15 | 5.50 | 4.83 | -59.6k | 132k | -41.8k | 17.7k / 0.06 | 30k | PORTFOLIO-LEAD s1=7.02 plateau>=0.95 |

## 6. Chance expectation (own null)

- N1 timing-destroyed library (100 reps, independent circular shift per book, same pre-filter and plateau): best-of-search stage-1 clean Sharpe mean 7.92, sd 0.66, p95 9.07, max 9.29; real 7.26 (rank 0.20).
- N2 edge-destroyed (weekly random sign flip of de-meaned books, 30 reps): mean 6.76, p95 7.25.
- Reading: N1 keeps each book's own edge and destroys only the alignment between books, so it measures how much of the best portfolio Sharpe is combination/diversification luck given the pool; N2 measures pure selection noise.

## 7. Stage-1 context

- T=16: best stage-1 7.26, top-5 stage-1 values 7.26, 7.26, 7.26, 7.26, 7.12
- T=12: best stage-1 7.19, top-5 stage-1 values 7.19, 7.19, 7.19, 7.19, 7.08
- T=20: best stage-1 7.30, top-5 stage-1 values 7.30, 7.30, 7.30, 7.30, 7.12

Runtime 2.8 min. Pool books (first 60 by clean Sharpe): RU11_GC_IMP3_5_1.5 (4.36), C10S1_GC/60_macd_12_26_brk_3.0_all_0 (2.70), T3S1_BOOKS_B/B_HM_20_55_150 (2.65), RU5_basket_GC_SI_HO_NG_NQ (2.64), T3S1_BOOKS_H/H_HM_1min1 (2.64), T3S1_BOOKS_B/B_HM_20_55_200 (2.63), SW10CO/NQ_1 (2.63), T3S1_G_G_v1/G_G5_obv_n120_tf1_e200_delta (2.58), SW10CO/NQ_2 (2.56), C10S1_6J/60_ema_9_21_time_8_all_1 (2.56), SW26CO/NQ_1 (2.55), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_t5 (2.55), T3S1_BOOKS_B/B_WT_30_1.5_50 (2.53), T3S1_BOOKS_B/B_WT_20_1.5_50 (2.52), T3S1_G_G_v1/G_G4_roc_n60_tf1_e200_adx20 (2.50), RU11_ES_IMP3_3_1.5 (2.50), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_delta (2.49), S8ALL/S8_mon_h1_RTY (2.47), T3S1_BOOKS_B/B_ST_120_2.0_150 (2.47), T3S1_G_G_bb3/BB_054_p1_ts120 (2.45), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_none (2.42), SW10CO/NQ_3 (2.42), T3S1_G_G_v1/G_G6_fvg_n20_tf5_eNone_none (2.41), T3S1_G_G_bb1/BB_169_p2_ts30 (2.41), SW32CO/NQ_1 (2.40), B1CO/BTC_1 (2.40), T3S1_G_G_v1/G_G4_stochrsi_n14_lo30_hi80_tf5_e200_adx20 (2.38), S8ALL/S8_mon_h1_YM (2.37), L92_BTC_widetrail_ensemble54 (2.36), T3S1_BOOKS_B/B_HM_20_55_300 (2.36), T3S1_BOOKS_B/B_WT_15_1.75_50 (2.35), SW18CO/NQ_1 (2.34), S8ALL/S8_mon_h1_NQ (2.33), T3S1_BOOKS_B/B_ST_150_2.0_150 (2.32), GAPMAP_B2356/G2__G2_GC_10_1_h5_BTC (2.29), T3S1_G_G_bb4/BB_073_p0_br60 (2.28), SW5CO/YM_1 (2.28), Q19CO/BTC_1 (2.27), T3S1_G_G_bb4/BB_073_p0_ts120 (2.26), T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 (2.26), D1F4/ES_k0.75_slip0.0_ST (2.25), SW5CO/YM_2 (2.25), T3S1_G_G_v1/G_G1_macross_kindVIDYA_f5_s20_tf5_eNone_delta (2.24), T3S3/S3_12_NQ_ORB_{'N':15,'stopmode':0,'tm':1.0,'reentry':0} (2.24), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_none (2.23), SW17CO/NQ_1 (2.23), WThist/ATR10_m3_ema0_tf10_X1 (2.23), SW14CO/ES_1 (2.22), SW18CO/ES_1 (2.18), V5P2/c1174 (2.18), B1leg_ETH/15_WT_20_3.0_100_k_0.15 (2.18), T3S1_BOOKS_B/B_ST_180_2.25_150 (2.18), B1CO/BTC_2 (2.18), SW31CO/BTC_1 (2.17), SW20CO/RTY_1 (2.15), WThist/ATR14_m3_ema0_tf10_X1 (2.15), SW4CO/RTY_1 (2.15), SW26CO/NQ_2 (2.15), T3S1_BOOKS_B/B_WT_20_1.75_50 (2.15), T3S1_BOOKS_B/B_WT_15_1.5_50 (2.14)

DONE ASSEMBLY 20261027T2043Z
