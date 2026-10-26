# REPORT ASSEMBLY 20261016T2348Z  (daemon)

Portfolio assembly over the book LIBRARY, pre-registered in PREREG_AUTOPILOT.md (section ASSEMBLY). Selection on CLEAN (2023-08..2025-07) weekly Sharpe only; H1 (2025-08-01..2026-02-06) and H2 (2026-02-07..2026-10-13) read once for the top 10 and the marked rows. UNTOUCHED never read.

**Headline.** Best stage-1 clean plateau-passing weekly Sharpe in the library at T=16: **7.14**; expected best-of-search by chance (timing-destroyed library, 100 replicates): mean 8.45, p50 8.42, p95 9.21, real rank 0.00. Edge-destroyed null (N2, 30 reps): mean 6.73, p95 7.25.
Best portfolio (stage 2, T=16): B1leg_BTC/15_WT_20_3.0_100_m_3.0 x5, S8ALL/S8_mon_h1_YM x3, ICT_FVG_E1_tickreplay x4, T3S1_G_G_bb1/BB_169_p2_ts30 x4; clean/H1/H2 weekly Sharpe 7.12/3.68/3.37 versus live pair 8/8 1.46/2.83/2.26.

## 1. Pool and pre-filter (pre-registered rule)

- Library rows 35511, loaded 35511, eligible (active, not WITHDRAWN, full clean coverage) 35323, after de-duplication (|corr|>=0.95) 31274, WITHDRAWN excluded 0.
- Pool = ST, HM, WT-10 + all leads (88 on the deduped set) + top 150 others by clean standalone Sharpe = **240 books**. WT-10 book(s) in pool: WT10.
- Stage-1 feasible subsets searched at T=16: 2,077,456 (k=2,3,4 books, all integer allocations summing to 16 with >=1 contract each, plateau: all +-1-contract transfers keep >=75%).

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
| 1 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x5, S8ALL/S8_mon_h1_YM x3, ICT_FVG_E1_tickreplay x4, T3S1_G_G_bb1/BB_169_p2_ts30 x4 | A1[ICT_FVG_E1_tickreplay x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x5+S8ALL/S8_mon_h1_YM x3 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x4] | 7.12 | 3.68 | 3.37 | -73.8k | 125k | -49.7k | 11.9k / 0.15 | 82k | PORTFOLIO-LEAD s1=7.13 plateau>=0.88 |
| 2 | B1leg_BTC/15_ST_8_2.0_20_m_3.0 x5, ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x4, ICT_FVG_E1_tickreplay x4, B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x3 | A1[ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x4]+B1leg_BTC/15_ST_8_2.0_20_m_3.0 x5+B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x3 ; A2[ICT_FVG_E1_tickreplay x4] | 7.03 | 5.31 | 3.89 | -66.8k | 163k | -45.1k | 2.9k / 0.10 | 82k | PORTFOLIO-LEAD s1=7.13 plateau>=0.85 |
| 3 | T3S1_G_G_bb1/BB_169_p2_ts30 x3, B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6, S8ALL/S8_mon_h1_RTY x3, ICT_FVG_E1_tickreplay x4 | A1[ICT_FVG_E1_tickreplay x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6+S8ALL/S8_mon_h1_RTY x3 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x3] | 6.93 | 4.72 | 3.49 | -76.8k | 127k | -51.2k | 10.5k / 0.26 | 82k | PORTFOLIO-LEAD s1=7.14 plateau>=0.94 |
| 4 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6, S8ALL/S8_mon_h1_RTY x3, Q1CCO/NQ_6 x3, ICT_FVG_E1_tickreplay x4 | A1[ICT_FVG_E1_tickreplay x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6+S8ALL/S8_mon_h1_RTY x3+Q1CCO/NQ_6 x3 | 6.90 | 4.15 | 3.06 | -76.8k | 120k | -51.1k | 10.4k / 0.27 | 82k | PORTFOLIO-LEAD s1=6.86 plateau>=0.93 |
| 5 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6, S8ALL/S8_mon_h1_YM x3, Q1CCO/NQ_6 x3, ICT_FVG_E1_tickreplay x4 | A1[ICT_FVG_E1_tickreplay x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6+S8ALL/S8_mon_h1_YM x3+Q1CCO/NQ_6 x3 | 6.87 | 3.87 | 2.72 | -76.8k | 106k | -52.4k | 10.5k / 0.14 | 82k | PORTFOLIO-LEAD s1=6.85 plateau>=0.94 |
| 6 | T3S1_G_G_bb3/BB_054_p1_ts120 x4, B1leg_BTC/15_WT_20_3.0_100_m_3.0 x5, ICT_FVG_E1_tickreplay x4, C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3 | A1[T3S1_G_G_bb3/BB_054_p1_ts120 x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x5+C10S1_GC/60_macd_12_26_brk_3.0_all_0 x3 ; A2[ICT_FVG_E1_tickreplay x4] | 6.79 | 2.35 | 1.21 | -76.8k | 158k | -63.5k | 10.0k / 0.13 | 24k |  s1=6.84 plateau>=0.89 |
| 7 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x5, S8ALL/S8_mon_h1_ES x3, ICT_FVG_E1_tickreplay x4, T3S1_G_G_bb1/BB_169_p2_ts30 x4 | A1[ICT_FVG_E1_tickreplay x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x5+S8ALL/S8_mon_h1_ES x3 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x4] | 6.79 | 4.53 | 3.72 | -70.8k | 111k | -48.0k | 11.7k / 0.21 | 82k | PORTFOLIO-LEAD s1=6.71 plateau>=0.90 |
| 8 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6, Q5ALL/Q5_mom_25_XS_3_as_M_h19_MACRO12 x3, ICT_FVG_E1_tickreplay x4, S8ALL/S8_mon_h1_YM x3 | A1[ICT_FVG_E1_tickreplay x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6+Q5ALL/Q5_mom_25_XS_3_as_M_h19_MACRO12 x3+S8ALL/S8_mon_h1_YM x3 | 6.77 | 4.63 | 3.23 | -59.7k | 124k | -43.7k | 8.4k / 0.08 | 141k | PORTFOLIO-LEAD s1=6.76 plateau>=0.95 |
| 9 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6, S8ALL/S8_mon_h1_YM x3, ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X1 x3, ICT_FVG_E1_tickreplay x4 | A1[ICT_FVG_E1_tickreplay x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6+S8ALL/S8_mon_h1_YM x3 ; A2[ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X1 x3] | 6.76 | 4.50 | 3.80 | -66.8k | 119k | -47.3k | 7.0k / 0.22 | 82k | PORTFOLIO-LEAD s1=6.70 plateau>=0.92 |
| 10 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6, S8ALL/S8_mon_h1_RTY x3, ICT_FVG_E1_tickreplay x4, Q5ALL/Q5_mom_25_XS_3_as_M_h19_MACRO12 x3 | A1[ICT_FVG_E1_tickreplay x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x6+S8ALL/S8_mon_h1_RTY x3+Q5ALL/Q5_mom_25_XS_3_as_M_h19_MACRO12 x3 | 6.75 | 5.07 | 3.48 | -59.7k | 142k | -43.8k | 8.3k / 0.20 | 141k | PORTFOLIO-LEAD s1=6.73 plateau>=0.95 |

## 4. Top portfolios, T = 12 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 6/6 | ST x6, HM x6 | A1[ST6/HM6] | 1.46 | 2.83 | 2.26 | -61.9k | 210k | -59.4k | -58.7k / 1.00 | 18k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x5, HM x5, WT10 x2 | A1[ST5/HM5] ; A2[WT-10 x2] | 1.79 | 3.23 | 2.42 | -57.9k | 136k | -53.3k | -47.4k / -0.03 | 18k |  |
| 1 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x4, S8ALL/S8_mon_h1_YM x2, ICT_FVG_E1_tickreplay x3, T3S1_G_G_bb1/BB_169_p2_ts30 x3 | A1[ICT_FVG_E1_tickreplay x3]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x4+S8ALL/S8_mon_h1_YM x2 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x3] | 7.09 | 3.84 | 3.44 | -53.6k | 96k | -36.4k | 9.2k / 0.13 | 57k | PORTFOLIO-LEAD s1=7.10 plateau>=0.86 |
| 2 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x4, S8ALL/S8_mon_h1_RTY x2, ICT_FVG_E1_tickreplay x3, T3S1_G_G_bb1/BB_169_p2_ts30 x3 | A1[ICT_FVG_E1_tickreplay x3]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x4+S8ALL/S8_mon_h1_RTY x2 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x3] | 7.04 | 4.52 | 3.56 | -57.6k | 89k | -37.4k | 8.9k / 0.22 | 57k | PORTFOLIO-LEAD s1=7.11 plateau>=0.86 |
| 3 | B1leg_BTC/15_ST_8_2.0_20_m_3.0 x3, ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x3, ICT_FVG_E1_tickreplay x3, B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x3 | A1[ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x3]+B1leg_BTC/15_ST_8_2.0_20_m_3.0 x3+B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x3 ; A2[ICT_FVG_E1_tickreplay x3] | 6.94 | 5.22 | 4.01 | -46.4k | 128k | -36.4k | 2.2k / -0.07 | 76k | PORTFOLIO-LEAD s1=7.10 plateau>=0.85 |
| 4 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x4, S8ALL/S8_mon_h1_YM x3, ICT_FVG_E1_tickreplay x3, Q1CCO/NQ_6 x2 | A1[ICT_FVG_E1_tickreplay x3]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x4+S8ALL/S8_mon_h1_YM x3+Q1CCO/NQ_6 x2 | 6.92 | 3.65 | 2.71 | -57.6k | 85k | -42.0k | 6.8k / 0.21 | 76k | PORTFOLIO-LEAD s1=6.78 plateau>=0.92 |
| 5 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x5, S8ALL/S8_mon_h1_RTY x2, ICT_FVG_E1_tickreplay x3, Q1CCO/NQ_6 x2 | A1[ICT_FVG_E1_tickreplay x3]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x5+S8ALL/S8_mon_h1_RTY x2+Q1CCO/NQ_6 x2 | 6.80 | 4.36 | 3.05 | -57.6k | 82k | -37.9k | 7.6k / 0.25 | 57k | PORTFOLIO-LEAD s1=6.80 plateau>=0.91 |

## 5. Top portfolios, T = 20 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 10/10 | ST x10, HM x10 | A1[ST10/HM10] | 1.46 | 2.83 | 2.26 | -103.2k | 350k | -99.0k | -97.8k / 1.00 | 30k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x8, HM x8, WT10 x4 | A1[ST8/HM8] ; A2[WT-10 x4] | 1.87 | 3.30 | 2.45 | -96.5k | 215k | -87.2k | -75.2k / -0.06 | 30k |  |
| 1 | B1leg_BTC/15_ST_8_2.0_20_m_3.0 x6, ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x5, ICT_FVG_E1_tickreplay x5, B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x4 | A1[ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x5]+B1leg_BTC/15_ST_8_2.0_20_m_3.0 x6+B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x4 ; A2[ICT_FVG_E1_tickreplay x5] | 7.05 | 5.30 | 3.92 | -82.2k | 204k | -57.2k | 3.5k / 0.06 | 108k | PORTFOLIO-LEAD s1=7.16 plateau>=0.87 |
| 2 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x7, S8ALL/S8_mon_h1_YM x4, ICT_FVG_E1_tickreplay x5, T3S1_G_G_bb1/BB_169_p2_ts30 x4 | A1[ICT_FVG_E1_tickreplay x5]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x7+S8ALL/S8_mon_h1_YM x4 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x4] | 7.02 | 3.89 | 3.27 | -92.4k | 163k | -62.7k | 13.6k / 0.18 | 108k | PORTFOLIO-LEAD s1=7.16 plateau>=0.95 |
| 3 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x8, S8ALL/S8_mon_h1_RTY x4, ICT_FVG_E1_tickreplay x4, Q1CCO/NQ_6 x4 | A1[ICT_FVG_E1_tickreplay x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x8+S8ALL/S8_mon_h1_RTY x4+Q1CCO/NQ_6 x4 | 7.00 | 3.86 | 2.52 | -96.0k | 157k | -63.7k | 11.2k / 0.28 | 108k | PORTFOLIO-LEAD s1=6.92 plateau>=0.96 |
| 4 | T3S1_G_G_bb1/BB_169_p2_ts30 x4, B1leg_BTC/15_WT_20_3.0_100_m_3.0 x7, S8ALL/S8_mon_h1_RTY x4, ICT_FVG_E1_tickreplay x5 | A1[ICT_FVG_E1_tickreplay x5]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x7+S8ALL/S8_mon_h1_RTY x4 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x4] | 6.99 | 4.58 | 3.55 | -96.0k | 155k | -64.1k | 13.4k / 0.25 | 108k | PORTFOLIO-LEAD s1=7.17 plateau>=0.95 |
| 5 | B1leg_BTC/15_WT_20_3.0_100_m_3.0 x8, S8ALL/S8_mon_h1_YM x4, ICT_FVG_E1_tickreplay x4, Q1CCO/NQ_6 x4 | A1[ICT_FVG_E1_tickreplay x4]+B1leg_BTC/15_WT_20_3.0_100_m_3.0 x8+S8ALL/S8_mon_h1_YM x4+Q1CCO/NQ_6 x4 | 6.91 | 3.60 | 2.11 | -96.0k | 139k | -68.1k | 11.4k / 0.13 | 108k |  s1=6.86 plateau>=0.96 |

## 6. Chance expectation (own null)

- N1 timing-destroyed library (100 reps, independent circular shift per book, same pre-filter and plateau): best-of-search stage-1 clean Sharpe mean 8.45, sd 0.46, p95 9.21, max 9.95; real 7.14 (rank 0.00).
- N2 edge-destroyed (weekly random sign flip of de-meaned books, 30 reps): mean 6.73, p95 7.25.
- Reading: N1 keeps each book's own edge and destroys only the alignment between books, so it measures how much of the best portfolio Sharpe is combination/diversification luck given the pool; N2 measures pure selection noise.

## 7. Stage-1 context

- T=16: best stage-1 7.14, top-5 stage-1 values 7.14, 7.14, 7.14, 7.14, 7.13
- T=12: best stage-1 7.11, top-5 stage-1 values 7.11, 7.11, 7.11, 7.11, 7.10
- T=20: best stage-1 7.17, top-5 stage-1 values 7.17, 7.17, 7.17, 7.17, 7.16

Runtime 7.0 min. Pool books (first 60 by clean Sharpe): ICT_FVG_E1_tickreplay (3.81), ICT/C2_FVG_tf1_m0.25_CE|ALL|X1 (3.63), ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 (3.53), ICT/C2_FVG_tf1_m0.25_FULL|ALL|X1 (3.36), ICT/C2_FVG_tf3_m0.25_CE|ALL|X1 (3.34), ICT/C2_FVG_tf3_m0.25_FULL|ALL|X1 (3.25), ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X1 (3.23), ICT/C2_FVG_tf5_m0.25_CE|ALL|X1 (2.72), C10S1_GC/60_macd_12_26_brk_3.0_all_0 (2.70), T3S1_BOOKS_B/B_HM_20_55_150 (2.65), T3S1_BOOKS_H/H_HM_1min1 (2.64), ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 (2.63), T3S1_BOOKS_B/B_HM_20_55_200 (2.63), ICT/C2_FVG_tf1_m0.25_CE|NYPM|X1 (2.62), ICT/C2_FVG_tf1_m0.25_CE|NYAM|X1 (2.58), T3S1_G_G_v1/G_G5_obv_n120_tf1_e200_delta (2.58), C10S1_6J/60_ema_9_21_time_8_all_1 (2.56), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_t5 (2.55), T3S1_BOOKS_B/B_WT_30_1.5_50 (2.53), T3S1_BOOKS_B/B_WT_20_1.5_50 (2.52), ICT_FVG_P1_tickreplay (2.51), T3S1_G_G_v1/G_G4_roc_n60_tf1_e200_adx20 (2.50), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_delta (2.49), S8ALL/S8_mon_h1_RTY (2.47), T3S1_BOOKS_B/B_ST_120_2.0_150 (2.47), T3S1_G_G_bb3/BB_054_p1_ts120 (2.45), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_none (2.42), T3S1_G_G_v1/G_G6_fvg_n20_tf5_eNone_none (2.41), T3S1_G_G_bb1/BB_169_p2_ts30 (2.41), ICT/C2_FVG_tf3_m0.25_FULL|ALL|X2 (2.40), B1leg_BTC/15_WT_20_3.0_100_m_3.0 (2.40), T3S1_G_G_v1/G_G4_stochrsi_n14_lo30_hi80_tf5_e200_adx20 (2.38), S8ALL/S8_mon_h1_YM (2.37), ICT/C2_FVG_tf1_m0.25_CE|ALL|X2 (2.37), L92_BTC_widetrail_ensemble54 (2.36), T3S1_BOOKS_B/B_HM_20_55_300 (2.36), T3S1_BOOKS_B/B_WT_15_1.75_50 (2.35), ICT/C2_FVG_tf1_m0.25_FULL|NYPM|X1 (2.34), S8ALL/S8_mon_h1_NQ (2.33), T3S1_BOOKS_B/B_ST_150_2.0_150 (2.32), GAPMAP_B2356/G2__G2_GC_10_1_h5_BTC (2.29), T3S1_G_G_bb4/BB_073_p0_br60 (2.28), ICT/C2_FVG_tf15_m0.25_FULL|ALL|X1 (2.28), T3S1_G_G_bb4/BB_073_p0_ts120 (2.26), T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 (2.26), D1F4/ES_k0.75_slip0.0_ST (2.25), T3S1_G_G_v1/G_G1_macross_kindVIDYA_f5_s20_tf5_eNone_delta (2.24), T3S3/S3_12_NQ_ORB_{'N':15,'stopmode':0,'tm':1.0,'reentry':0} (2.24), ICT/C3_BRK_tf5_d1.0_e0|LONCL|X1 (2.24), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_none (2.23), WThist/ATR10_m3_ema0_tf10_X1 (2.23), ICT/C2_FVG_tf3_m0.25_FULL|LONCL|X1 (2.19), V5P2/c1174 (2.18), B1CO/ETH_1 (2.18), T3S1_BOOKS_B/B_ST_180_2.25_150 (2.18), B1CO/BTC_2 (2.18), WThist/ATR14_m3_ema0_tf10_X1 (2.15), ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 (2.15), T3S1_BOOKS_B/B_WT_20_1.75_50 (2.15), T3S1_BOOKS_B/B_WT_15_1.5_50 (2.14)

DONE ASSEMBLY 20261016T2348Z
