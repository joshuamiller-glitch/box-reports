# REPORT ASSEMBLY 20261017T0019Z  (daemon)

Portfolio assembly over the book LIBRARY, pre-registered in PREREG_AUTOPILOT.md (section ASSEMBLY). Selection on CLEAN (2023-08..2025-07) weekly Sharpe only; H1 (2025-08-01..2026-02-06) and H2 (2026-02-07..2026-10-13) read once for the top 10 and the marked rows. UNTOUCHED never read.

**Headline.** Best stage-1 clean plateau-passing weekly Sharpe in the library at T=16: **7.47**; expected best-of-search by chance (timing-destroyed library, 100 replicates): mean 8.77, p50 8.76, p95 9.49, real rank 0.00. Edge-destroyed null (N2, 30 reps): mean 6.71, p95 7.16.
Best portfolio (stage 2, T=16): S8ALL/S8_mon_h1_YM x3, B1CO/BTC_1 x5, RY5_E1_K4_a0.25_sg+1 x5, T3S1_G_G_bb1/BB_169_p2_ts30 x3; clean/H1/H2 weekly Sharpe 7.12/3.87/4.11 versus live pair 8/8 1.46/2.83/2.26.

## 1. Pool and pre-filter (pre-registered rule)

- Library rows 35642, loaded 35642, eligible (active, not WITHDRAWN, full clean coverage) 35454, after de-duplication (|corr|>=0.95) 31405, WITHDRAWN excluded 0.
- Pool = ST, HM, WT-10 + all leads (96 on the deduped set) + top 150 others by clean standalone Sharpe = **248 books**. WT-10 book(s) in pool: WT10.
- Stage-1 feasible subsets searched at T=16: 2,368,402 (k=2,3,4 books, all integer allocations summing to 16 with >=1 contract each, plateau: all +-1-contract transfers keep >=75%).

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
| 1 | S8ALL/S8_mon_h1_YM x3, B1CO/BTC_1 x5, RY5_E1_K4_a0.25_sg+1 x5, T3S1_G_G_bb1/BB_169_p2_ts30 x3 | A1[RY5_E1_K4_a0.25_sg+1 x5]+S8ALL/S8_mon_h1_YM x3+B1CO/BTC_1 x5 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x3] | 7.12 | 3.87 | 4.11 | -69.5k | 125k | -50.6k | 13.7k / 0.11 | 82k | PORTFOLIO-LEAD s1=7.32 plateau>=0.95 |
| 2 | S8ALL/S8_mon_h1_YM x3, B1CO/BTC_1 x5, ICT_FVG_E1_tickreplay x4, T3S1_G_G_bb1/BB_169_p2_ts30 x4 | A1[ICT_FVG_E1_tickreplay x4]+S8ALL/S8_mon_h1_YM x3+B1CO/BTC_1 x5 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x4] | 7.12 | 3.68 | 3.37 | -73.8k | 125k | -49.7k | 11.9k / 0.15 | 82k | PORTFOLIO-LEAD s1=7.13 plateau>=0.88 |
| 3 | S8ALL/S8_mon_h1_YM x3, B1CO/BTC_1 x6, Q1CCO/NQ_6 x3, RY5_E1_K4_a0.25_sg+1 x4 | A1[RY5_E1_K4_a0.25_sg+1 x4]+S8ALL/S8_mon_h1_YM x3+B1CO/BTC_1 x6+Q1CCO/NQ_6 x3 | 7.10 | 3.39 | 2.63 | -76.8k | 114k | -53.8k | 11.3k / 0.06 | 82k | PORTFOLIO-LEAD s1=7.08 plateau>=0.95 |
| 4 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x6, Q1CCO/NQ_6 x3, RY5_E1_K4_a0.25_sg+1 x4 | A1[RY5_E1_K4_a0.25_sg+1 x4]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x6+Q1CCO/NQ_6 x3 | 7.07 | 3.65 | 3.00 | -76.8k | 120k | -51.9k | 11.2k / 0.21 | 82k | PORTFOLIO-LEAD s1=7.03 plateau>=0.95 |
| 5 | B1CO/BTC_3 x5, ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x4, RY5_E1_K4_a0.25_sg+1 x4, B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x3 | A1[ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x4]+B1CO/BTC_3 x5+B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x3 ; A2[RY5_E1_K4_a0.25_sg+1 x4] | 7.07 | 5.22 | 4.31 | -64.2k | 163k | -40.4k | 3.6k / -0.03 | 82k | PORTFOLIO-LEAD s1=7.47 plateau>=0.91 |
| 6 | S8ALL/S8_mon_h1_YM x3, Q1CCO/NQ_6 x3, RY5_E1_K4_a0.5_sg-1 x4, B1CO/BTC_1 x6 | A1[RY5_E1_K4_a0.5_sg-1 x4]+S8ALL/S8_mon_h1_YM x3+Q1CCO/NQ_6 x3+B1CO/BTC_1 x6 | 7.07 | 2.99 | 2.45 | -76.8k | 124k | -59.4k | 11.5k / -0.00 | 82k | PORTFOLIO-LEAD s1=7.04 plateau>=0.94 |
| 7 | B1CO/BTC_3 x5, ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x4, ICT_FVG_E1_tickreplay x4, B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x3 | A1[ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x4]+B1CO/BTC_3 x5+B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x3 ; A2[ICT_FVG_E1_tickreplay x4] | 7.03 | 5.31 | 3.89 | -66.8k | 163k | -45.1k | 2.9k / 0.10 | 82k | PORTFOLIO-LEAD s1=7.13 plateau>=0.85 |
| 8 | S8ALL/S8_mon_h1_YM x3, B1CO/BTC_1 x5, RY5_E1_K4_a0.25_sg+1 x5, Q5ALL/Q5_mom_25_XS_3_as_M_h19_MACRO12 x3 | A1[RY5_E1_K4_a0.25_sg+1 x5]+S8ALL/S8_mon_h1_YM x3+B1CO/BTC_1 x5+Q5ALL/Q5_mom_25_XS_3_as_M_h19_MACRO12 x3 | 7.02 | 4.40 | 4.14 | -59.6k | 113k | -42.3k | 11.4k / 0.01 | 141k | PORTFOLIO-LEAD s1=7.01 plateau>=0.96 |
| 9 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x6, Q1CCO/NQ_6 x3, RY5_E1_K4_a0.5_sg-1 x4 | A1[RY5_E1_K4_a0.5_sg-1 x4]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x6+Q1CCO/NQ_6 x3 | 7.00 | 3.41 | 2.83 | -76.8k | 121k | -52.5k | 11.4k / 0.13 | 82k | PORTFOLIO-LEAD s1=6.96 plateau>=0.94 |
| 10 | T3S1_G_G_bb1/BB_169_p2_ts30 x3, S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x5, RY5_E1_K4_a0.25_sg+1 x5 | A1[RY5_E1_K4_a0.25_sg+1 x5]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x5 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x3] | 6.97 | 4.51 | 4.20 | -75.5k | 114k | -49.2k | 13.4k / 0.23 | 82k | PORTFOLIO-LEAD s1=7.21 plateau>=0.95 |

## 4. Top portfolios, T = 12 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 6/6 | ST x6, HM x6 | A1[ST6/HM6] | 1.46 | 2.83 | 2.26 | -61.9k | 210k | -59.4k | -58.7k / 1.00 | 18k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x5, HM x5, WT10 x2 | A1[ST5/HM5] ; A2[WT-10 x2] | 1.79 | 3.23 | 2.42 | -57.9k | 136k | -53.3k | -47.4k / -0.03 | 18k |  |
| 1 | S8ALL/S8_mon_h1_YM x3, B1CO/BTC_1 x4, RY5_E1_K4_a0.5_sg-1 x3, Q1CCO/NQ_6 x2 | A1[RY5_E1_K4_a0.5_sg-1 x3]+S8ALL/S8_mon_h1_YM x3+B1CO/BTC_1 x4+Q1CCO/NQ_6 x2 | 7.17 | 2.82 | 2.53 | -57.6k | 90k | -45.7k | 7.5k / 0.09 | 76k |  s1=7.00 plateau>=0.92 |
| 2 | S8ALL/S8_mon_h1_YM x3, B1CO/BTC_1 x4, RY5_E1_K4_a0.25_sg+1 x3, Q1CCO/NQ_6 x2 | A1[RY5_E1_K4_a0.25_sg+1 x3]+S8ALL/S8_mon_h1_YM x3+B1CO/BTC_1 x4+Q1CCO/NQ_6 x2 | 7.16 | 3.18 | 2.63 | -57.6k | 90k | -42.9k | 7.4k / 0.15 | 76k | PORTFOLIO-LEAD s1=7.01 plateau>=0.92 |
| 3 | S8ALL/S8_mon_h1_RTY x2, B1CO/BTC_1 x4, RY5_E1_K4_a0.25_sg+1 x3, T3S1_G_G_bb1/BB_169_p2_ts30 x3 | A1[RY5_E1_K4_a0.25_sg+1 x3]+S8ALL/S8_mon_h1_RTY x2+B1CO/BTC_1 x4 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x3] | 7.14 | 4.28 | 3.76 | -56.6k | 89k | -34.5k | 9.5k / 0.19 | 57k | PORTFOLIO-LEAD s1=7.16 plateau>=0.84 |
| 4 | S8ALL/S8_mon_h1_YM x2, B1CO/BTC_1 x4, ICT_FVG_E1_tickreplay x3, T3S1_G_G_bb1/BB_169_p2_ts30 x3 | A1[ICT_FVG_E1_tickreplay x3]+S8ALL/S8_mon_h1_YM x2+B1CO/BTC_1 x4 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x3] | 7.09 | 3.84 | 3.44 | -53.6k | 96k | -36.4k | 9.2k / 0.13 | 57k | PORTFOLIO-LEAD s1=7.10 plateau>=0.86 |
| 5 | S8ALL/S8_mon_h1_RTY x3, B1CO/BTC_1 x4, Q1CCO/NQ_6 x2, RY5_E1_K4_a0.5_sg-1 x3 | A1[RY5_E1_K4_a0.5_sg-1 x3]+S8ALL/S8_mon_h1_RTY x3+B1CO/BTC_1 x4+Q1CCO/NQ_6 x2 | 7.07 | 3.43 | 2.92 | -57.6k | 97k | -39.7k | 7.5k / 0.25 | 76k | PORTFOLIO-LEAD s1=6.88 plateau>=0.92 |

## 5. Top portfolios, T = 20 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 10/10 | ST x10, HM x10 | A1[ST10/HM10] | 1.46 | 2.83 | 2.26 | -103.2k | 350k | -99.0k | -97.8k / 1.00 | 30k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x8, HM x8, WT10 x4 | A1[ST8/HM8] ; A2[WT-10 x4] | 1.87 | 3.30 | 2.45 | -96.5k | 215k | -87.2k | -75.2k / -0.06 | 30k |  |
| 1 | T3S1_G_G_bb1/BB_169_p2_ts30 x4, S8ALL/S8_mon_h1_YM x4, RY5_E1_K4_a0.25_sg+1 x6, B1CO/BTC_1 x6 | A1[RY5_E1_K4_a0.25_sg+1 x6]+S8ALL/S8_mon_h1_YM x4+B1CO/BTC_1 x6 ; A2[T3S1_G_G_bb1/BB_169_p2_ts30 x4] | 7.21 | 3.69 | 3.98 | -89.4k | 154k | -63.0k | 16.6k / 0.12 | 108k | PORTFOLIO-LEAD s1=7.35 plateau>=0.94 |
| 2 | S8ALL/S8_mon_h1_YM x4, B1CO/BTC_1 x7, Q1CCO/NQ_6 x4, RY5_E1_K4_a0.25_sg+1 x5 | A1[RY5_E1_K4_a0.25_sg+1 x5]+S8ALL/S8_mon_h1_YM x4+B1CO/BTC_1 x7+Q1CCO/NQ_6 x4 | 7.14 | 3.23 | 2.59 | -96.0k | 158k | -69.3k | 14.4k / 0.07 | 108k | PORTFOLIO-LEAD s1=7.09 plateau>=0.96 |
| 3 | S8ALL/S8_mon_h1_YM x4, B1CO/BTC_1 x7, RY5_E1_K4_a0.5_sg-1 x5, Q1CCO/NQ_6 x4 | A1[RY5_E1_K4_a0.5_sg-1 x5]+S8ALL/S8_mon_h1_YM x4+B1CO/BTC_1 x7+Q1CCO/NQ_6 x4 | 7.12 | 2.84 | 2.46 | -96.0k | 163k | -75.0k | 14.6k / 0.01 | 108k | PORTFOLIO-LEAD s1=7.07 plateau>=0.96 |
| 4 | B1CO/BTC_3 x6, ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x5, RY5_E1_K4_a0.25_sg+1 x5, B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x4 | A1[ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X2 x5]+B1CO/BTC_3 x6+B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x4 ; A2[RY5_E1_K4_a0.25_sg+1 x5] | 7.10 | 5.22 | 4.34 | -79.0k | 204k | -51.5k | 4.5k / -0.07 | 108k | PORTFOLIO-LEAD s1=7.50 plateau>=0.92 |
| 5 | S8ALL/S8_mon_h1_RTY x4, B1CO/BTC_1 x7, Q1CCO/NQ_6 x4, RY5_E1_K4_a0.25_sg+1 x5 | A1[RY5_E1_K4_a0.25_sg+1 x5]+S8ALL/S8_mon_h1_RTY x4+B1CO/BTC_1 x7+Q1CCO/NQ_6 x4 | 7.10 | 3.57 | 2.98 | -96.0k | 162k | -65.3k | 14.2k / 0.23 | 108k | PORTFOLIO-LEAD s1=7.03 plateau>=0.96 |

## 6. Chance expectation (own null)

- N1 timing-destroyed library (100 reps, independent circular shift per book, same pre-filter and plateau): best-of-search stage-1 clean Sharpe mean 8.77, sd 0.41, p95 9.49, max 9.67; real 7.47 (rank 0.00).
- N2 edge-destroyed (weekly random sign flip of de-meaned books, 30 reps): mean 6.71, p95 7.16.
- Reading: N1 keeps each book's own edge and destroys only the alignment between books, so it measures how much of the best portfolio Sharpe is combination/diversification luck given the pool; N2 measures pure selection noise.

## 7. Stage-1 context

- T=16: best stage-1 7.47, top-5 stage-1 values 7.47, 7.47, 7.47, 7.47, 7.47
- T=12: best stage-1 7.43, top-5 stage-1 values 7.43, 7.43, 7.43, 7.43, 7.43
- T=20: best stage-1 7.50, top-5 stage-1 values 7.50, 7.50, 7.50, 7.50, 7.50

Runtime 6.3 min. Pool books (first 60 by clean Sharpe): RY5_E1_K4_a0.25_sg+1 (4.15), ICT_FVG_E1_tickreplay (3.81), RY5_E1_K4_a0.5_sg-1 (3.68), ICT/C2_FVG_tf1_m0.25_CE|ALL|X1 (3.63), ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 (3.53), ICT/C2_FVG_tf1_m0.25_FULL|ALL|X1 (3.36), ICT/C2_FVG_tf3_m0.25_CE|ALL|X1 (3.34), ICT/C2_FVG_tf3_m0.25_FULL|ALL|X1 (3.25), ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X1 (3.23), ICT/C2_FVG_tf5_m0.25_CE|ALL|X1 (2.72), C10S1_GC/60_macd_12_26_brk_3.0_all_0 (2.70), T3S1_BOOKS_B/B_HM_20_55_150 (2.65), T3S1_BOOKS_H/H_HM_1min1 (2.64), ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 (2.63), T3S1_BOOKS_B/B_HM_20_55_200 (2.63), ICT/C2_FVG_tf1_m0.25_CE|NYPM|X1 (2.62), ICT/C2_FVG_tf1_m0.25_CE|NYAM|X1 (2.58), T3S1_G_G_v1/G_G5_obv_n120_tf1_e200_delta (2.58), C10S1_6J/60_ema_9_21_time_8_all_1 (2.56), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_t5 (2.55), T3S1_BOOKS_B/B_WT_30_1.5_50 (2.53), T3S1_BOOKS_B/B_WT_20_1.5_50 (2.52), ICT_FVG_P1_tickreplay (2.51), T3S1_G_G_v1/G_G4_roc_n60_tf1_e200_adx20 (2.50), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_delta (2.49), S8ALL/S8_mon_h1_RTY (2.47), T3S1_BOOKS_B/B_ST_120_2.0_150 (2.47), T3S1_G_G_bb3/BB_054_p1_ts120 (2.45), T3S1_G_G_v1/G_G5_obv_n120_tf1_eNone_none (2.42), T3S1_G_G_v1/G_G6_fvg_n20_tf5_eNone_none (2.41), T3S1_G_G_bb1/BB_169_p2_ts30 (2.41), ICT/C2_FVG_tf3_m0.25_FULL|ALL|X2 (2.40), B1CO/BTC_1 (2.40), T3S1_G_G_v1/G_G4_stochrsi_n14_lo30_hi80_tf5_e200_adx20 (2.38), S8ALL/S8_mon_h1_YM (2.37), ICT/C2_FVG_tf1_m0.25_CE|ALL|X2 (2.37), L92_BTC_widetrail_ensemble54 (2.36), T3S1_BOOKS_B/B_HM_20_55_300 (2.36), T3S1_BOOKS_B/B_WT_15_1.75_50 (2.35), ICT/C2_FVG_tf1_m0.25_FULL|NYPM|X1 (2.34), S8ALL/S8_mon_h1_NQ (2.33), T3S1_BOOKS_B/B_ST_150_2.0_150 (2.32), GAPMAP_B2356/G2__G2_GC_10_1_h5_BTC (2.29), T3S1_G_G_bb4/BB_073_p0_br60 (2.28), ICT/C2_FVG_tf15_m0.25_FULL|ALL|X1 (2.28), SW5CO/YM_1 (2.28), T3S1_G_G_bb4/BB_073_p0_ts120 (2.26), T3S1_G_G_v1/G_G2_orb_n15_tf1_e200_t5 (2.26), D1F4/ES_k0.75_slip0.0_ST (2.25), SW5CO/YM_2 (2.25), T3S1_G_G_v1/G_G1_macross_kindVIDYA_f5_s20_tf5_eNone_delta (2.24), T3S3/S3_12_NQ_ORB_{'N':15,'stopmode':0,'tm':1.0,'reentry':0} (2.24), ICT/C3_BRK_tf5_d1.0_e0|LONCL|X1 (2.24), T3S1_G_G_v1/G_G6_fvg_n20_tf5_e200_none (2.23), WThist/ATR10_m3_ema0_tf10_X1 (2.23), ICT/C2_FVG_tf3_m0.25_FULL|LONCL|X1 (2.19), V5P2/c1174 (2.18), B1leg_ETH/15_WT_20_3.0_100_k_0.15 (2.18), T3S1_BOOKS_B/B_ST_180_2.25_150 (2.18), B1CO/BTC_2 (2.18)

DONE ASSEMBLY 20261017T0019Z
