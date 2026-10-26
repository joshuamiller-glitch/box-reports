# REPORT ASSEMBLY 20261016T2318Z  (daemon)

Portfolio assembly over the book LIBRARY, pre-registered in PREREG_AUTOPILOT.md (section ASSEMBLY). Selection on CLEAN (2023-08..2025-07) weekly Sharpe only; H1 (2025-08-01..2026-02-06) and H2 (2026-02-07..2026-10-13) read once for the top 10 and the marked rows. UNTOUCHED never read.

**Headline.** Best stage-1 clean plateau-passing weekly Sharpe in the library at T=16: **6.66**; expected best-of-search by chance (timing-destroyed library, 100 replicates): mean 8.45, p50 8.42, p95 9.26, real rank 0.00. Edge-destroyed null (N2, 30 reps): mean 6.62, p95 6.99.
Best portfolio (stage 2, T=16): S8ALL/S8_mon_h1_RTY x4, B1CO/BTC_1 x6, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2, Q1CCO/NQ_6 x4; clean/H1/H2 weekly Sharpe 6.48/1.63/1.08 versus live pair 8/8 1.46/2.83/2.26.

## 1. Pool and pre-filter (pre-registered rule)

- Library rows 35446, loaded 35446, eligible (active, not WITHDRAWN, full clean coverage) 35260, after de-duplication (|corr|>=0.95) 31230, WITHDRAWN excluded 0.
- Pool = ST, HM, WT-10 + all leads (86 on the deduped set) + top 150 others by clean standalone Sharpe = **238 books**. WT-10 book(s) in pool: WT10.
- Stage-1 feasible subsets searched at T=16: 2,063,938 (k=2,3,4 books, all integer allocations summing to 16 with >=1 contract each, plateau: all +-1-contract transfers keep >=75%).

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
| 1 | S8ALL/S8_mon_h1_RTY x4, B1CO/BTC_1 x6, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2, Q1CCO/NQ_6 x4 | A1[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2]+S8ALL/S8_mon_h1_RTY x4+B1CO/BTC_1 x6+Q1CCO/NQ_6 x4 | 6.48 | 1.63 | 1.08 | -76.8k | 218k | -61.9k | 2.0k / 0.14 | 102k |  s1=6.19 plateau>=0.92 |
| 2 | B1CO/BTC_1 x7, ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x3, Q1CCO/NQ_6 x3, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3 | A1[ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x3]+B1CO/BTC_1 x7+Q1CCO/NQ_6 x3 ; A2[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3] | 6.39 | 4.26 | 2.45 | -76.8k | 210k | -61.0k | 16.6k / -0.09 | 24k | PORTFOLIO-LEAD s1=6.56 plateau>=0.79 |
| 3 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x7, ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x2, Q1CCO/NQ_6 x4 | A1[ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x2]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x7+Q1CCO/NQ_6 x4 | 6.35 | 3.13 | 1.48 | -76.8k | 168k | -62.2k | 12.0k / 0.23 | 82k |  s1=6.34 plateau>=0.93 |
| 4 | S8ALL/S8_mon_h1_RTY x4, B1CO/BTC_1 x7, ICT/C2_FVG_tf1_m0.25_CE|ALL|X1 x1, Q1CCO/NQ_6 x4 | A1[ICT/C2_FVG_tf1_m0.25_CE|ALL|X1 x1]+S8ALL/S8_mon_h1_RTY x4+B1CO/BTC_1 x7+Q1CCO/NQ_6 x4 | 6.34 | 2.13 | 3.19 | -76.8k | 193k | -62.3k | 8.9k / 0.21 | 102k |  s1=6.19 plateau>=0.82 |
| 5 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x7, ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x3, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3 | A1[ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x3]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x7 ; A2[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3] | 6.34 | 4.92 | 2.91 | -76.8k | 139k | -58.2k | 11.4k / 0.32 | 82k | PORTFOLIO-LEAD s1=6.45 plateau>=0.79 |
| 6 | S8ALL/S8_mon_h1_YM x3, B1CO/BTC_1 x7, ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x2, Q1CCO/NQ_6 x4 | A1[ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x2]+S8ALL/S8_mon_h1_YM x3+B1CO/BTC_1 x7+Q1CCO/NQ_6 x4 | 6.26 | 2.82 | 1.23 | -76.8k | 199k | -64.1k | 12.2k / 0.12 | 82k |  s1=6.26 plateau>=0.92 |
| 7 | S8ALL/S8_mon_h1_RTY x4, B1CO/BTC_1 x7, ICT/C2_FVG_tf1_m0.25_FULL|ALL|X1 x1, Q1CCO/NQ_6 x4 | A1[ICT/C2_FVG_tf1_m0.25_FULL|ALL|X1 x1]+S8ALL/S8_mon_h1_RTY x4+B1CO/BTC_1 x7+Q1CCO/NQ_6 x4 | 6.26 | 1.87 | 2.97 | -76.8k | 212k | -58.6k | 6.2k / 0.16 | 102k |  s1=6.08 plateau>=0.83 |
| 8 | WThist/ATR10_m3_ema0_tf10_X1 x5, T3S1_G_G_bb6/BB_110_p2_ts30 x3, L92_BTC_widetrail_ensemble54 x6, C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x2 | A1[WThist/ATR10_m3_ema0_tf10_X1 x5]+L92_BTC_widetrail_ensemble54 x6+C10S1_ZN/240_ema_20_60_brk_3.0_all_0 x2 ; A2[T3S1_G_G_bb6/BB_110_p2_ts30 x3] | 6.22 | 2.33 | 0.17 | -59.6k | 171k | -39.5k | 7.6k / 0.07 | 24k |  s1=6.01 plateau>=0.91 |
| 9 | B1leg_BTC/15_ST_8_2.0_20_m_3.0 x6, ICT/C2_FVG_tf3_m0.25_FULL|ALL|X1 x3, Q1CCO/NQ_6 x4, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3 | A1[ICT/C2_FVG_tf3_m0.25_FULL|ALL|X1 x3]+B1leg_BTC/15_ST_8_2.0_20_m_3.0 x6+Q1CCO/NQ_6 x4 ; A2[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3] | 6.21 | 3.29 | 2.47 | -76.8k | 246k | -65.1k | 22.6k / -0.04 | 24k | PORTFOLIO-LEAD s1=6.23 plateau>=0.79 |
| 10 | B1leg_BTC/15_ST_8_2.0_20_m_3.0 x5, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3, ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X1 x5, S8ALL/S8_mon_h1_RTY x3 | A1[ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X1 x5]+B1leg_BTC/15_ST_8_2.0_20_m_3.0 x5+S8ALL/S8_mon_h1_RTY x3 ; A2[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3] | 6.18 | 2.88 | 2.37 | -76.8k | 224k | -56.6k | 3.0k / 0.29 | 82k | PORTFOLIO-LEAD s1=5.94 plateau>=0.93 |

## 4. Top portfolios, T = 12 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 6/6 | ST x6, HM x6 | A1[ST6/HM6] | 1.46 | 2.83 | 2.26 | -61.9k | 210k | -59.4k | -58.7k / 1.00 | 18k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x5, HM x5, WT10 x2 | A1[ST5/HM5] ; A2[WT-10 x2] | 1.79 | 3.23 | 2.42 | -57.9k | 136k | -53.3k | -47.4k / -0.03 | 18k |  |
| 1 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x5, ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x2, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2 | A1[ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x2]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x5 ; A2[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2] | 6.43 | 4.69 | 2.79 | -57.6k | 119k | -43.9k | 6.5k / 0.40 | 76k | PORTFOLIO-LEAD s1=6.41 plateau>=0.79 |
| 2 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x4, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2, Q1CCO/NQ_6 x3 | A1[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x4+Q1CCO/NQ_6 x3 | 6.40 | 1.72 | 1.47 | -57.6k | 172k | -46.5k | 1.6k / 0.11 | 76k |  s1=6.14 plateau>=0.89 |
| 3 | B1CO/BTC_1 x5, ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x2, Q1CCO/NQ_6 x3, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2 | A1[ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x2]+B1CO/BTC_1 x5+Q1CCO/NQ_6 x3 ; A2[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2] | 6.36 | 3.82 | 2.33 | -57.6k | 171k | -46.5k | 12.3k / -0.13 | 18k | PORTFOLIO-LEAD s1=6.55 plateau>=0.81 |
| 4 | S8ALL/S8_mon_h1_YM x3, B1CO/BTC_1 x5, ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x2, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2 | A1[ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x2]+S8ALL/S8_mon_h1_YM x3+B1CO/BTC_1 x5 ; A2[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x2] | 6.32 | 4.25 | 2.40 | -57.6k | 107k | -42.3k | 7.4k / 0.27 | 76k | PORTFOLIO-LEAD s1=6.40 plateau>=0.81 |
| 5 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x5, ICT/C2_FVG_tf1_m0.25_CE|ALL|X1 x1, Q1CCO/NQ_6 x3 | A1[ICT/C2_FVG_tf1_m0.25_CE|ALL|X1 x1]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x5+Q1CCO/NQ_6 x3 | 6.31 | 2.31 | 3.38 | -57.6k | 147k | -49.5k | 8.2k / 0.20 | 76k |  s1=6.20 plateau>=0.82 |

## 5. Top portfolios, T = 20 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 10/10 | ST x10, HM x10 | A1[ST10/HM10] | 1.46 | 2.83 | 2.26 | -103.2k | 350k | -99.0k | -97.8k / 1.00 | 30k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x8, HM x8, WT10 x4 | A1[ST8/HM8] ; A2[WT-10 x4] | 1.87 | 3.30 | 2.45 | -96.5k | 215k | -87.2k | -75.2k / -0.06 | 30k |  |
| 1 | S8ALL/S8_mon_h1_RTY x5, B1CO/BTC_1 x7, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3, Q1CCO/NQ_6 x5 | A1[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3]+S8ALL/S8_mon_h1_RTY x5+B1CO/BTC_1 x7+Q1CCO/NQ_6 x5 | 6.46 | 1.68 | 1.32 | -96.0k | 281k | -77.2k | 2.6k / 0.12 | 128k |  s1=6.19 plateau>=0.95 |
| 2 | S8ALL/S8_mon_h1_RTY x4, B1CO/BTC_1 x8, ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x3, Q1CCO/NQ_6 x5 | A1[ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x3]+S8ALL/S8_mon_h1_RTY x4+B1CO/BTC_1 x8+Q1CCO/NQ_6 x5 | 6.33 | 3.23 | 1.96 | -96.0k | 220k | -76.6k | 17.0k / 0.26 | 108k |  s1=6.30 plateau>=0.95 |
| 3 | GAPMAP_B2356/G2__G2_GC_10_1_h5_BTC x5, B1leg_BTC/15_ST_8_2.0_20_m_3.0 x7, ICT/C2_FVG_tf3_m0.25_FULL|ALL|X1 x4, ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x4 | A1[ICT/C2_FVG_tf3_m0.25_FULL|ALL|X1 x4]+GAPMAP_B2356/G2__G2_GC_10_1_h5_BTC x5+B1leg_BTC/15_ST_8_2.0_20_m_3.0 x7 ; A2[ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x4] | 6.30 | 2.77 | 3.39 | -89.2k | 184k | -62.1k | 31.3k / 0.13 | 128k |  s1=6.45 plateau>=0.81 |
| 4 | L92_BTC_widetrail_ensemble54 x11, ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x3, Q1CCO/NQ_6 x3, ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3 | A1[ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x3]+L92_BTC_widetrail_ensemble54 x11+Q1CCO/NQ_6 x3 ; A2[ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 x3] | 6.29 | 3.37 | 2.88 | -96.0k | 224k | -61.7k | 19.6k / -0.15 | 30k | PORTFOLIO-LEAD s1=6.42 plateau>=0.76 |
| 5 | S8ALL/S8_mon_h1_YM x4, B1CO/BTC_1 x8, ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x3, Q1CCO/NQ_6 x5 | A1[ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 x3]+S8ALL/S8_mon_h1_YM x4+B1CO/BTC_1 x8+Q1CCO/NQ_6 x5 | 6.27 | 2.91 | 1.62 | -96.0k | 262k | -78.1k | 17.2k / 0.14 | 108k |  s1=6.25 plateau>=0.96 |

## 6. Chance expectation (own null)

- N1 timing-destroyed library (100 reps, independent circular shift per book, same pre-filter and plateau): best-of-search stage-1 clean Sharpe mean 8.45, sd 0.51, p95 9.26, max 10.23; real 6.66 (rank 0.00).
- N2 edge-destroyed (weekly random sign flip of de-meaned books, 30 reps): mean 6.62, p95 6.99.
- Reading: N1 keeps each book's own edge and destroys only the alignment between books, so it measures how much of the best portfolio Sharpe is combination/diversification luck given the pool; N2 measures pure selection noise.

## 7. Stage-1 context

- T=16: best stage-1 6.66, top-5 stage-1 values 6.66, 6.66, 6.64, 6.64, 6.60
- T=12: best stage-1 6.55, top-5 stage-1 values 6.55, 6.55, 6.55, 6.55, 6.55
- T=20: best stage-1 6.64, top-5 stage-1 values 6.64, 6.64, 6.62, 6.62, 6.59

Runtime 6.2 min. Pool books (first 60 by clean Sharpe): ICT/C2_FVG_tf1_m0.25_CE|ALL|X1 (3.63), ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 (3.53), ICT/C2_FVG_tf1_m0.25_FULL|ALL|X1 (3.36), ICT/C2_FVG_tf3_m0.25_CE|ALL|X1 (3.34), ICT/C2_FVG_tf3_m0.25_FULL|ALL|X1 (3.25), ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X1 (3.23), ICT/C2_FVG_tf5_m0.25_CE|ALL|X1 (2.72), ICT_FVG_P1_tickreplay (2.72), C10S1_GC/60_macd_12_26_brk_3.0_all_0 (2.70), T3S1_BOOKS_B/B_HM_20_55_150 (2.65), T3S1_BOOKS_H/H_HM_1min1 (2.64), ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 (2.63), T3S1_BOOKS_B/B_HM_20_55_200 (2.63), ICT/C2_FVG_tf1_m0.25_CE|NYPM|X1 (2.62), ICT/C2_FVG_tf1_m0.25_CE|NYAM|X1 (2.58), T3S1_G_G_v1/G_G5_obv_n120_tf1_e200_delta (2.58), C10S1_6J/60_ema_9_21_time_8_all_1 (2.56), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_t5 (2.55), T3S1_BOOKS_B/B_WT_30_1.5_50 (2.53), T3S1_BOOKS_B/B_WT_20_1.5_50 (2.52), T3S1_G_G_v1/G_G4_roc_n60_tf1_e200_adx20 (2.50), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_delta (2.49), S8ALL/S8_mon_h1_RTY (2.47), T3S1_BOOKS_B/B_ST_120_2.0_150 (2.47), T3S1_G_G_bb3/BB_054_p1_ts120 (2.45), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_none (2.42), T3S1_G_G_v1/G_G6_fvg_n20_tf5_eNone_none (2.41), T3S1_G_G_bb1/BB_169_p2_ts30 (2.41), ICT/C2_FVG_tf3_m0.25_FULL|ALL|X2 (2.40), B1CO/BTC_1 (2.40), T3S1_G_G_v1/G_G4_stochrsi_n14_lo30_hi80_tf5_e200_adx20 (2.38), S8ALL/S8_mon_h1_YM (2.37), ICT/C2_FVG_tf1_m0.25_CE|ALL|X2 (2.37), L92_BTC_widetrail_ensemble54 (2.36), T3S1_BOOKS_B/B_HM_20_55_300 (2.36), T3S1_BOOKS_B/B_WT_15_1.75_50 (2.35), ICT/C2_FVG_tf1_m0.25_FULL|NYPM|X1 (2.34), S8ALL/S8_mon_h1_NQ (2.33), T3S1_BOOKS_B/B_ST_150_2.0_150 (2.32), GAPMAP_B2356/G2__G2_GC_10_1_h5_BTC (2.29), T3S1_G_G_bb4/BB_073_p0_br60 (2.28), ICT/C2_FVG_tf15_m0.25_FULL|ALL|X1 (2.28), T3S1_G_G_bb4/BB_073_p0_ts120 (2.26), T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 (2.26), D1F4/ES_k0.75_slip0.0_ST (2.25), T3S1_G_G_v1/G_G1_macross_kindVIDYA_f5_s20_tf5_eNone_delta (2.24), T3S3/S3_12_NQ_ORB_{'N':15,'stopmode':0,'tm':1.0,'reentry':0} (2.24), ICT/C3_BRK_tf5_d1.0_e0|LONCL|X1 (2.24), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_none (2.23), WThist/ATR10_m3_ema0_tf10_X1 (2.23), ICT/C2_FVG_tf3_m0.25_FULL|LONCL|X1 (2.19), V5P2/c1174 (2.18), B1CO/ETH_1 (2.18), T3S1_BOOKS_B/B_ST_180_2.25_150 (2.18), B1CO/BTC_2 (2.18), WThist/ATR14_m3_ema0_tf10_X1 (2.15), ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 (2.15), T3S1_BOOKS_B/B_WT_20_1.75_50 (2.15), T3S1_BOOKS_B/B_WT_15_1.5_50 (2.14), Q1CCO/NQ_6 (2.14)

DONE ASSEMBLY 20261016T2318Z
