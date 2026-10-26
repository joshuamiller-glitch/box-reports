# REPORT ASSEMBLY 20261017T0638Z  (daemon)

Portfolio assembly over the book LIBRARY, pre-registered in PREREG_AUTOPILOT.md (section ASSEMBLY). Selection on CLEAN (2023-08..2025-07) weekly Sharpe only; H1 (2025-08-01..2026-02-06) and H2 (2026-02-07..2026-10-13) read once for the top 10 and the marked rows. UNTOUCHED never read.

**Headline.** Best stage-1 clean plateau-passing weekly Sharpe in the library at T=16: **11.16**; expected best-of-search by chance (timing-destroyed library, 100 replicates): mean 13.77, p50 13.69, p95 14.93, real rank 0.00. Edge-destroyed null (N2, 30 reps): mean 6.67, p95 7.16.
Best portfolio (stage 2, T=16): SW10CO/NQ_2 x4, ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/BTC_1 x4, Q18CO/HO_2 x5; clean/H1/H2 weekly Sharpe 11.87/8.09/10.20 versus live pair 8/8 1.46/2.83/2.26.

## 1. Pool and pre-filter (pre-registered rule)

- Library rows 37491, loaded 37491, eligible (active, not WITHDRAWN, full clean coverage) 37300, after de-duplication (|corr|>=0.95) 33202, WITHDRAWN excluded 0.
- Pool = ST, HM, WT-10 + all leads (101 on the deduped set) + top 150 others by clean standalone Sharpe = **253 books**. WT-10 book(s) in pool: WT10.
- Stage-1 feasible subsets searched at T=16: 3,600,183 (k=2,3,4 books, all integer allocations summing to 16 with >=1 contract each, plateau: all +-1-contract transfers keep >=75%).

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
| 1 | SW10CO/NQ_2 x4, ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/BTC_1 x4, Q18CO/HO_2 x5 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x3]+SW10CO/NQ_2 x4+Q18CO/BTC_1 x4+Q18CO/HO_2 x5 | 11.87 | 8.09 | 10.20 | -76.8k | 151k | -33.2k | 66.3k / 0.00 | 24k | PORTFOLIO-LEAD s1=11.12 plateau>=0.95 |
| 2 | ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/BTC_1 x5, Q18CO/HO_2 x4, SW10CO/NQ_3 x4 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x3]+Q18CO/BTC_1 x5+Q18CO/HO_2 x4+SW10CO/NQ_3 x4 | 11.64 | 7.59 | 11.86 | -36.4k | 106k | -21.9k | 67.3k / 0.07 | 24k | PORTFOLIO-LEAD s1=11.16 plateau>=0.96 |
| 3 | SW10CO/NQ_1 x3, ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/HO_2 x5, Q18CO/BTC_1 x5 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x3]+SW10CO/NQ_1 x3+Q18CO/HO_2 x5+Q18CO/BTC_1 x5 | 11.56 | 8.63 | 10.12 | -76.8k | 152k | -36.7k | 64.4k / 0.06 | 24k | PORTFOLIO-LEAD s1=10.71 plateau>=0.96 |
| 4 | ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/BTC_1 x5, Q18CO/HO_1 x4, SW10CO/NQ_3 x4 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x3]+Q18CO/BTC_1 x5+Q18CO/HO_1 x4+SW10CO/NQ_3 x4 | 11.47 | 7.97 | 11.46 | -76.8k | 77k | -25.8k | 70.4k / 0.08 | 24k | PORTFOLIO-LEAD s1=10.85 plateau>=0.94 |
| 5 | SW10CO/NQ_2 x3, ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/HO_1 x5, Q18CO/BTC_1 x5 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x3]+SW10CO/NQ_2 x3+Q18CO/HO_1 x5+Q18CO/BTC_1 x5 | 11.47 | 9.22 | 11.01 | -76.8k | 103k | -29.5k | 71.2k / 0.03 | 24k | PORTFOLIO-LEAD s1=10.62 plateau>=0.95 |
| 6 | ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/BTC_1 x5, Q18CO/HO_5 x4, SW10CO/NQ_3 x4 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x3]+Q18CO/BTC_1 x5+Q18CO/HO_5 x4+SW10CO/NQ_3 x4 | 11.40 | 7.63 | 10.93 | -48.6k | 121k | -24.1k | 64.7k / 0.13 | 24k | PORTFOLIO-LEAD s1=10.67 plateau>=0.94 |
| 7 | ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/BTC_1 x5, Q18CO/HO_2 x5, C10S1_ZN/240_ema_20_60_opp_0_all_0 x3 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x3]+Q18CO/BTC_1 x5+Q18CO/HO_2 x5+C10S1_ZN/240_ema_20_60_opp_0_all_0 x3 | 11.40 | 8.81 | 10.40 | -76.8k | 148k | -35.1k | 66.5k / 0.14 | 24k | PORTFOLIO-LEAD s1=10.83 plateau>=0.92 |
| 8 | ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/BTC_1 x5, Q18CO/HO_5 x4, SW10CO/NQ_2 x4 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x3]+Q18CO/BTC_1 x5+Q18CO/HO_5 x4+SW10CO/NQ_2 x4 | 11.37 | 8.27 | 10.25 | -71.0k | 116k | -25.9k | 61.2k / 0.09 | 24k | PORTFOLIO-LEAD s1=10.29 plateau>=0.96 |
| 9 | ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/BTC_1 x5, Q18CO/HO_3 x4, SW10CO/NQ_2 x4 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x3]+Q18CO/BTC_1 x5+Q18CO/HO_3 x4+SW10CO/NQ_2 x4 | 11.33 | 7.65 | 10.59 | -76.8k | 84k | -27.0k | 65.7k / 0.04 | 24k | PORTFOLIO-LEAD s1=10.49 plateau>=0.93 |
| 10 | B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x3, ICT_FVG_IMP3_tf2_m1.125_tickreplay x3, Q18CO/BTC_1 x5, Q18CO/HO_2 x5 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x3]+B2356ERA/Q5__Q5_mom_25_XS_4_as_M_h19_MACRO12 x3+Q18CO/BTC_1 x5+Q18CO/HO_2 x5 | 11.26 | 9.17 | 10.85 | -76.8k | 156k | -43.0k | 66.6k / -0.06 | 82k | PORTFOLIO-LEAD s1=10.68 plateau>=0.94 |

## 4. Top portfolios, T = 12 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 6/6 | ST x6, HM x6 | A1[ST6/HM6] | 1.46 | 2.83 | 2.26 | -61.9k | 210k | -59.4k | -58.7k / 1.00 | 18k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x5, HM x5, WT10 x2 | A1[ST5/HM5] ; A2[WT-10 x2] | 1.79 | 3.23 | 2.42 | -57.9k | 136k | -53.3k | -47.4k / -0.03 | 18k |  |
| 1 | ICT_FVG_IMP3_tf2_m1.125_tickreplay x2, Q18CO/BTC_1 x3, Q18CO/HO_2 x4, SW10CO/NQ_2 x3 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x2]+Q18CO/BTC_1 x3+Q18CO/HO_2 x4+SW10CO/NQ_2 x3 | 11.85 | 8.04 | 9.01 | -57.6k | 108k | -29.7k | 48.8k / -0.04 | 18k | PORTFOLIO-LEAD s1=11.11 plateau>=0.87 |
| 2 | SW10CO/NQ_3 x3, ICT_FVG_IMP3_tf2_m1.125_tickreplay x2, Q18CO/HO_2 x3, Q18CO/BTC_1 x4 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x2]+SW10CO/NQ_3 x3+Q18CO/HO_2 x3+Q18CO/BTC_1 x4 | 11.66 | 7.55 | 11.48 | -23.1k | 81k | -16.3k | 48.6k / 0.04 | 18k | PORTFOLIO-LEAD s1=11.17 plateau>=0.89 |
| 3 | SW10CO/NQ_1 x2, ICT_FVG_IMP3_tf2_m1.125_tickreplay x2, Q18CO/HO_2 x4, Q18CO/BTC_1 x4 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x2]+SW10CO/NQ_1 x2+Q18CO/HO_2 x4+Q18CO/BTC_1 x4 | 11.51 | 8.76 | 9.88 | -57.6k | 106k | -26.8k | 47.9k / 0.02 | 18k | PORTFOLIO-LEAD s1=10.71 plateau>=0.88 |
| 4 | ICT_FVG_IMP3_tf2_m1.125_tickreplay x2, Q18CO/BTC_1 x4, Q18CO/HO_1 x3, SW10CO/NQ_3 x3 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x2]+Q18CO/BTC_1 x4+Q18CO/HO_1 x3+SW10CO/NQ_3 x3 | 11.47 | 7.95 | 11.18 | -57.6k | 58k | -19.4k | 50.9k / 0.05 | 18k | PORTFOLIO-LEAD s1=10.84 plateau>=0.88 |
| 5 | ICT_FVG_IMP3_tf2_m1.125_tickreplay x2, Q18CO/BTC_1 x4, Q18CO/HO_2 x4, C10S1_ZN/240_ema_20_60_opp_0_all_0 x2 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x2]+Q18CO/BTC_1 x4+Q18CO/HO_2 x4+C10S1_ZN/240_ema_20_60_opp_0_all_0 x2 | 11.43 | 8.89 | 10.13 | -57.6k | 103k | -26.6k | 49.3k / 0.11 | 18k | PORTFOLIO-LEAD s1=10.85 plateau>=0.89 |

## 5. Top portfolios, T = 20 contracts-equivalent

| # | members (contracts) | accounts | clean Sh | H1 Sh | H2 Sh | worst wk (all) | max DD (all) | CVaR5 wk | worst-decile wks: mean / corr w pair | margin proxy | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LIVE PAIR** 10/10 | ST x10, HM x10 | A1[ST10/HM10] | 1.46 | 2.83 | 2.26 | -103.2k | 350k | -99.0k | -97.8k / 1.00 | 30k |  |
| **LIVE PAIR + WT-10 (separate acct)** | ST x8, HM x8, WT10 x4 | A1[ST8/HM8] ; A2[WT-10 x4] | 1.87 | 3.30 | 2.45 | -96.5k | 215k | -87.2k | -75.2k / -0.06 | 30k |  |
| 1 | SW10CO/NQ_2 x4, ICT_FVG_IMP3_tf2_m1.125_tickreplay x4, Q18CO/BTC_1 x6, Q18CO/HO_2 x6 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x4]+SW10CO/NQ_2 x4+Q18CO/BTC_1 x6+Q18CO/HO_2 x6 | 11.80 | 8.55 | 11.45 | -96.0k | 180k | -32.8k | 85.2k / 0.03 | 30k | PORTFOLIO-LEAD s1=11.09 plateau>=0.96 |
| 2 | SW10CO/NQ_3 x5, ICT_FVG_IMP3_tf2_m1.125_tickreplay x4, Q18CO/BTC_1 x6, Q18CO/HO_2 x5 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x4]+SW10CO/NQ_3 x5+Q18CO/BTC_1 x6+Q18CO/HO_2 x5 | 11.58 | 7.59 | 12.07 | -50.6k | 131k | -28.1k | 86.0k / 0.09 | 30k | PORTFOLIO-LEAD s1=11.12 plateau>=0.97 |
| 3 | SW10CO/NQ_2 x4, ICT_FVG_IMP3_tf2_m1.125_tickreplay x4, Q18CO/BTC_1 x6, Q18CO/HO_1 x6 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x4]+SW10CO/NQ_2 x4+Q18CO/BTC_1 x6+Q18CO/HO_1 x6 | 11.47 | 9.09 | 11.16 | -96.0k | 124k | -37.8k | 89.3k / 0.04 | 30k | PORTFOLIO-LEAD s1=10.62 plateau>=0.97 |
| 4 | SW10CO/NQ_3 x5, ICT_FVG_IMP3_tf2_m1.125_tickreplay x4, Q18CO/BTC_1 x6, Q18CO/HO_1 x5 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x4]+SW10CO/NQ_3 x5+Q18CO/BTC_1 x6+Q18CO/HO_1 x5 | 11.42 | 7.97 | 11.60 | -96.0k | 96k | -33.0k | 89.8k / 0.10 | 30k | PORTFOLIO-LEAD s1=10.82 plateau>=0.94 |
| 5 | SW10CO/NQ_1 x3, ICT_FVG_IMP3_tf2_m1.125_tickreplay x4, Q18CO/BTC_1 x6, Q18CO/HO_2 x7 | A1[ICT_FVG_IMP3_tf2_m1.125_tickreplay x4]+SW10CO/NQ_1 x3+Q18CO/BTC_1 x6+Q18CO/HO_2 x7 | 11.40 | 8.86 | 10.32 | -96.0k | 192k | -48.2k | 85.6k / 0.07 | 30k | PORTFOLIO-LEAD s1=10.69 plateau>=0.97 |

## 6. Chance expectation (own null)

- N1 timing-destroyed library (100 reps, independent circular shift per book, same pre-filter and plateau): best-of-search stage-1 clean Sharpe mean 13.77, sd 0.63, p95 14.93, max 15.18; real 11.16 (rank 0.00).
- N2 edge-destroyed (weekly random sign flip of de-meaned books, 30 reps): mean 6.67, p95 7.16.
- Reading: N1 keeps each book's own edge and destroys only the alignment between books, so it measures how much of the best portfolio Sharpe is combination/diversification luck given the pool; N2 measures pure selection noise.

## 7. Stage-1 context

- T=16: best stage-1 11.16, top-5 stage-1 values 11.16, 11.16, 11.16, 11.12, 11.12
- T=12: best stage-1 11.17, top-5 stage-1 values 11.17, 11.17, 11.17, 11.11, 11.11
- T=20: best stage-1 11.12, top-5 stage-1 values 11.12, 11.12, 11.12, 11.09, 11.09

Runtime 12.5 min. Pool books (first 60 by clean Sharpe): ICT_FVG_IMP3_tf2_m1.125_tickreplay (6.94), ICT_FVG_IMP3_tf2_m1.5_tickreplay (6.19), ICT_FVG_IMP3_tf3_m1.125_tickreplay (5.77), Q18CO/BTC_1 (5.10), Q18CO/BTC_2 (4.95), RZ9_basket_ES_RTY_YM_GC_CL_ZN_6E_BTC_ETH (4.89), Q18CO/GC_1 (4.81), Q18CO/BTC_3 (4.51), Q18CO/HO_1 (4.39), Q18CO/GC_2 (4.39), ICT_FVG_IMP3_tf3_tickreplay (4.37), Q18CO/GC_3 (4.18), Q18CO/HO_2 (4.16), RY5_E1_K4_a0.25_sg+1 (4.15), RZ6_E1_thr0.33_m0.0 (4.03), Q18CO/BTC_4 (3.95), Q18CO/GC_4 (3.93), ICT_FVG_E1_tickreplay (3.81), Q18CO/RTY_1 (3.71), RY5_E1_K4_a0.5_sg-1 (3.68), Q18CO/HO_3 (3.65), Q18CO/RTY_2 (3.65), ICT/C2_FVG_tf1_m0.25_CE|ALL|X1 (3.63), Q18CO/GC_5 (3.63), Q18CO/HO_4 (3.58), Q18CO/BTC_5 (3.57), Q18CO/CL_1 (3.56), Q18CO/BTC_6 (3.55), ICT/C2_FVG_tf3_m0.25_CE|ALL|X2 (3.53), Q18CO/HO_5 (3.45), Q18CO/RTY_3 (3.38), Q18CO/CL_2 (3.36), ICT/C2_FVG_tf1_m0.25_FULL|ALL|X1 (3.36), ICT/C2_FVG_tf3_m0.25_CE|ALL|X1 (3.34), Q18CO/BTC_7 (3.33), ICT/C2_FVG_tf3_m0.25_FULL|ALL|X1 (3.25), ICT/C2_FVG_tf1_m0.25_FULL|NYAM|X1 (3.23), Q18CO/ES_1 (3.22), Q18CO/BTC_8 (3.21), Q18CO/ES_2 (3.11), RZ6_E1_thr0.5_m0.0 (3.08), Q18CO/RTY_4 (3.08), Q18CO/HO_6 (3.07), Q18CO/BTC_9 (3.06), Q18CO/NQ_1 (3.02), Q18CO/ES_3 (3.00), Q18CO/BTC_10 (3.00), Q18CO/GC_6 (2.97), Q18CO/GC_7 (2.87), Q18CO/NQ_2 (2.84), Q18CO/HO_7 (2.83), Q18CO/CL_3 (2.81), Q18CO/CL_4 (2.81), Q18CO/GC_8 (2.72), ICT/C2_FVG_tf5_m0.25_CE|ALL|X1 (2.72), C10S1_GC/60_macd_12_26_brk_3.0_all_0 (2.70), T3S1_BOOKS_B/B_HM_20_55_150 (2.65), T3S1_BOOKS_H/H_HM_1min1 (2.64), ICT/C2_FVG_tf15_m0.25_CE|ALL|X1 (2.63), T3S1_BOOKS_B/B_HM_20_55_200 (2.63)

DONE ASSEMBLY 20261017T0638Z
