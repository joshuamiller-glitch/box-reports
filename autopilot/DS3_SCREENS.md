# DS3_SCREENS - what a discretionary desk watches, as features for NQ (T-SCREENS, W-S)
Page written 2026-11-13T17:11Z (date -u). Shadow only; no PASS claims. Method: every feature is scored first-order on the exact LPB_BASE trade list (20,807 trades) in the uses A (loss cut confirm), B (early cut), C (near-zone take), D (entry skip/half), E (P7 re-entry gate); regime flag F and learned G below. Four windows L6M / HOLD / PRE / X-prime, thresholds from events before 2025-11-11 only, family null by permuting each feature within month among its finite values (availability pattern kept), 60 permutations for the best-cell null, 20 for the entrant counts.
Spend: T-SCREENS $290.40, T-CROSS $143.52, total $433.92 of $1,000. Loop: nohup page/exact loop pid 2309711 (see below); exact runner pid 3065008. Exact stage: JN05W_S6_C22 43 of 43 months done, 0 errors; JN05W_S6_N22 0 of 43 months done, 0 errors; JN05W_S6_C18 43 of 43 months done, 0 errors; JN05W_S6_C14 43 of 43 months done, 0 errors; JN05W_S6_L10 0 of 43 months done, 0 errors.

## How many would pass by chance
Across all scored families 4120 cells beat the live rule in every window; the same pipeline on permuted features gives 3910 on average. A family is only credited where it exceeds its own placebo.

## Per family
### S1 VIX family (daily, prior close)
Data: Cboe free daily CSV (VIX, VIX9D, VIX3M, VIX6M, VVIX, SKEW) to 2026-11-10; cost $0. Proxy/limits: real index values, prior close only.
Scored: 14 features, 12290 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 21 cells beat the live rule in every window (chance with permuted features 15.0, p95 21), best-cell family p = 0.05; first-order stack entrants 3 (chance 1.3).
- loss-cut confirm (cut OFF when the cell is true): 72 cells beat the live rule in every window (chance with permuted features 68.4, p95 79), best-cell family p = 0.62; first-order stack entrants 3 (chance 2.4).
- early cut at -15 pts: 3 cells beat the live rule in every window (chance with permuted features 2.4, p95 6), best-cell family p = 0.02; first-order stack entrants 0 (chance 0.2).
- early cut at -25 pts: 7 cells beat the live rule in every window (chance with permuted features 4.6, p95 8), best-cell family p = 0.58; first-order stack entrants 0 (chance 0.5).
- near-zone take at 80% of target: 83 cells beat the live rule in every window (chance with permuted features 59.8, p95 71), best-cell family p = 0.33; first-order stack entrants 1 (chance 1.6).
- P7 Asia-type re-entry gate (P7 entries within 120 min of a same-side P7 loser): 16 cells beat the live rule in every window (chance with permuted features 17.1, p95 24), best-cell family p = 0.88; first-order stack entrants 0 (chance 0.4).
Best first-order stack cell (nominal): D book ALL session 3: s1_vvix >= 104.5 (acted on 35 L6M events). Stack maxDD cut / change in mean $ per week: L6M 6.9% / +726; HOLD 31.9% / +671; PRE -12.0% / +77; X' 2.2% / +8. In the worst-20 weeks it changes P&L by +848 $/wk and in the 20 best (trend) weeks by -726 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): daily CSV or a second NT8 data series ^VIX/^VIX9D/^VIX3M/^VVIX; v1.8 fields vix_lvl, vix_t3, vix_t9, vvix, vix_d1, skew_z.

### S1 VIX family intraday (DBIX.CORE 1-min, from 2025-12-07)
Data: Databento DBIX.CORE ohlcv-1m from 2025-12-07 (quote $0.00); RECENT-ONLY: no PRE/X history exists. Proxy/limits: real index values; history starts 2025-12-07.
Scored: 14 features, 3836 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 313 cells beat the live rule in every window (chance with permuted features 308.9, p95 331), best-cell family p = 0.08; first-order stack entrants 19 (chance 13.2).
- loss-cut confirm (cut OFF when the cell is true): 227 cells beat the live rule in every window (chance with permuted features 215.2, p95 226), best-cell family p = 0.13; first-order stack entrants 0 (chance 0.1).
- early cut at -15 pts: 50 cells beat the live rule in every window (chance with permuted features 74.3, p95 88), best-cell family p = 0.07; first-order stack entrants 2 (chance 11.9).
- early cut at -25 pts: 58 cells beat the live rule in every window (chance with permuted features 74.0, p95 88), best-cell family p = 0.33; first-order stack entrants 13 (chance 14.2).
- near-zone take at 80% of target: 103 cells beat the live rule in every window (chance with permuted features 136.3, p95 154), best-cell family p = 0.47; first-order stack entrants 1 (chance 3.1).
Best first-order stack cell (nominal): D book ALL all sessions: s1i_vix_s5 <= 35.48 (acted on 1463 L6M events). Stack maxDD cut / change in mean $ per week: L6M 40.0% / +4034; HOLD 22.9% / +1599. In the worst-20 weeks it changes P&L by +4818 $/wk and in the 20 best (trend) weeks by -6958 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): live index feed ^VIX ^VIX9D ^VVIX (1-min) in NT8; v1.8 fields ivix_s5, ivix9d_s5.

### S1 Dealer gamma from EOD open interest (NDX + NDXP)
Data: Databento OPRA.PILLAR statistics NDX.OPT + NDXP.OPT 2023-04-01..2026-11-10: $251.37 (of which $27.82 was the definition files, not needed because the OSI symbol carries strike/expiry); intraday OPRA quote only: cbbo-1s QQQ $23.52/day, NDX $3.96/day, NDXP $12.36/day (not planned). Proxy/limits: PROXY: flat sigma = 1.25 x VIX (no IV bought); NDX spot from NQ with a fair-basis estimate; dealers long calls / short puts convention.
Scored: 12 features, 9430 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 14 cells beat the live rule in every window (chance with permuted features 18.4, p95 25), best-cell family p = 0.50; first-order stack entrants 0 (chance 2.1).
- loss-cut confirm (cut OFF when the cell is true): 68 cells beat the live rule in every window (chance with permuted features 69.9, p95 80), best-cell family p = 0.10; first-order stack entrants 1 (chance 0.8).
- early cut at -15 pts: 9 cells beat the live rule in every window (chance with permuted features 7.4, p95 12), best-cell family p = 0.02; first-order stack entrants 0 (chance 0.5).
- early cut at -25 pts: 22 cells beat the live rule in every window (chance with permuted features 11.9, p95 18), best-cell family p = 0.17; first-order stack entrants 0 (chance 0.6).
- near-zone take at 80% of target: 32 cells beat the live rule in every window (chance with permuted features 37.6, p95 48), best-cell family p = 0.98; first-order stack entrants 1 (chance 0.6).
- P7 Asia-type re-entry gate (P7 entries within 120 min of a same-side P7 loser): 25 cells beat the live rule in every window (chance with permuted features 24.8, p95 32), best-cell family p = 0.17; first-order stack entrants 0 (chance 0.5).
Best first-order stack cell (nominal): C book U7 all sessions: s1g_callwall_dist <= -708.3 (acted on 52 L6M events). Stack maxDD cut / change in mean $ per week: L6M 8.4% / +306; HOLD 2.1% / +532; PRE 10.6% / +32; X' -0.7% / +152. In the worst-20 weeks it changes P&L by +2913 $/wk and in the 20 best (trend) weeks by -724 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): one daily file written before the open from the OPRA open-interest statistic (published about 05:30 ET): gex_net_bn, gex_z60, zero_gamma_nq, call_wall_nq, put_wall_nq, top0dte_nq, share0dte; read by DS7 as a level table (like the zone table).

### S2 Internals proxy: breadth of the 4 index futures (NQ ES RTY YM)
Data: owned 1-min bars; cost $0. Proxy/limits: PROXY, NOT NYSE TICK/TRIN: vote of 4 index futures over 1-30 min, persistence above zero since the 09:30 open, share at a 30-min extreme. NYSE/Nasdaq TICK/TRIN/AD are computed indices not sold by Databento; whole-market ohlcv-1m would be $336.78 for L6M (not bought).
Scored: 9 features, 5442 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 13 cells beat the live rule in every window (chance with permuted features 11.3, p95 17), best-cell family p = 0.70; first-order stack entrants 3 (chance 2.2).
- loss-cut confirm (cut OFF when the cell is true): 61 cells beat the live rule in every window (chance with permuted features 62.6, p95 76), best-cell family p = 0.02; first-order stack entrants 1 (chance 1.5).
- early cut at -15 pts: 1 cells beat the live rule in every window (chance with permuted features 2.5, p95 5), best-cell family p = 0.00; first-order stack entrants 0 (chance 0.2).
- early cut at -25 pts: 3 cells beat the live rule in every window (chance with permuted features 5.0, p95 9), best-cell family p = 0.65; first-order stack entrants 0 (chance 0.8).
- near-zone take at 80% of target: 8 cells beat the live rule in every window (chance with permuted features 18.2, p95 25), best-cell family p = 0.77; first-order stack entrants 0 (chance 0.5).
- P7 Asia-type re-entry gate (P7 entries within 120 min of a same-side P7 loser): 20 cells beat the live rule in every window (chance with permuted features 14.4, p95 20), best-cell family p = 0.93; first-order stack entrants 2 (chance 0.7).
Best first-order stack cell (nominal): E book ALL all sessions: s2_brd30 <= 0 (acted on 105 L6M events). Stack maxDD cut / change in mean $ per week: L6M 27.7% / +2407; HOLD 0.7% / +596; PRE 11.2% / +639; X' -0.6% / +39. In the worst-20 weeks it changes P&L by +2179 $/wk and in the 20 best (trend) weeks by +133 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): NT8 multi-series with ES/RTY/YM 1-min on the NQ chart; v1.8 fields brd15, brd30, persist_open, adv_ext30.

### S2 Internals proxy: megacap + ETF breadth
Data: T-CROSS megacap L6M package (W-CX, $98) - RECENT-ONLY. Proxy/limits: PROXY (8 stocks + QQQ + SMH).
Status: not scored yet (waiting for data or run).
Live feed it would need in NT8 (v1.8): NT8 multi-series for the 8 stocks; v1.8 fields adv8_5, upvol8_5.

### S3 Session leaders from owned bars (NKD, 6J, MBT, 6E, ZN) and the 03:00/11:30/Tokyo/HK clocks
Data: owned 1-min bars; cost $0. Proxy/limits: real bars; clocks are rules.
Scored: 31 features, 24626 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 57 cells beat the live rule in every window (chance with permuted features 45.6, p95 57), best-cell family p = 0.03; first-order stack entrants 6 (chance 7.8).
- loss-cut confirm (cut OFF when the cell is true): 240 cells beat the live rule in every window (chance with permuted features 146.8, p95 173), best-cell family p = 0.05; first-order stack entrants 2 (chance 2.9).
- early cut at -15 pts: 9 cells beat the live rule in every window (chance with permuted features 11.7, p95 17), best-cell family p = 0.07; first-order stack entrants 1 (chance 1.8).
- early cut at -25 pts: 18 cells beat the live rule in every window (chance with permuted features 21.4, p95 32), best-cell family p = 0.12; first-order stack entrants 5 (chance 4.3).
- near-zone take at 80% of target: 156 cells beat the live rule in every window (chance with permuted features 110.9, p95 129), best-cell family p = 0.17; first-order stack entrants 1 (chance 2.4).
- P7 Asia-type re-entry gate (P7 entries within 120 min of a same-side P7 loser): 59 cells beat the live rule in every window (chance with permuted features 53.4, p95 66), best-cell family p = 0.17; first-order stack entrants 4 (chance 2.6).
Best first-order stack cell (nominal): E book P7 all sessions: s3_e6_s60 <= -0.4372 (acted on 113 L6M events). Stack maxDD cut / change in mean $ per week: L6M 28.2% / +2716; HOLD 3.2% / +730; PRE 11.8% / +106; X' 3.2% / +501. In the worst-20 weeks it changes P&L by +3296 $/wk and in the 20 best (trend) weeks by +1176 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): NT8 multi-series NKD/6J/MBT/6E/ZN 1-min; v1.8 fields nkd_s15, nkd_nq_resid15, mbt_s60, c0300_min, c1130_min.

### S3 FDAX and FESX (Eurex) 1-min, from 2025-03-10
Data: Databento XEUR.EOBI ohlcv-1m 2025-03-10..2026-11-10 (part of the $39.03 package); Hang Seng and China A50 are not carried by any Databento dataset on the list: not buyable here. RECENT-ONLY (HOLD/L6M). Proxy/limits: real bars.
Scored: 10 features, 7542 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 212 cells beat the live rule in every window (chance with permuted features 199.2, p95 218), best-cell family p = 0.27; first-order stack entrants 14 (chance 16.7).
- loss-cut confirm (cut OFF when the cell is true): 260 cells beat the live rule in every window (chance with permuted features 242.8, p95 263), best-cell family p = 0.08; first-order stack entrants 0 (chance 2.6).
- early cut at -15 pts: 134 cells beat the live rule in every window (chance with permuted features 110.3, p95 120), best-cell family p = 0.05; first-order stack entrants 16 (chance 13.0).
- early cut at -25 pts: 135 cells beat the live rule in every window (chance with permuted features 134.6, p95 148), best-cell family p = 0.88; first-order stack entrants 16 (chance 16.6).
- near-zone take at 80% of target: 343 cells beat the live rule in every window (chance with permuted features 377.4, p95 395), best-cell family p = 0.45; first-order stack entrants 0 (chance 1.5).
- P7 Asia-type re-entry gate (P7 entries within 120 min of a same-side P7 loser): 32 cells beat the live rule in every window (chance with permuted features 46.0, p95 58), best-cell family p = 1.00; first-order stack entrants 12 (chance 8.8).
Best first-order stack cell (nominal): D book ALL all sessions: s3_fesx_nq_resid15 >= 4.163 (acted on 513 L6M events). Stack maxDD cut / change in mean $ per week: L6M 22.8% / +3526; HOLD 32.7% / +530. In the worst-20 weeks it changes P&L by +8765 $/wk and in the 20 best (trend) weeks by -5312 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): NT8 data series FDAX/FESX (Eurex via the data provider); v1.8 fields fdax_s15, fesx_nq_resid15.

### S3 SMH, XLK, HYG (RTH leaders / credit)
Data: Databento DBEQ.BASIC ohlcv-1s FULL for the 3 ETFs (part of the $39.03 package, about $14.3). Proxy/limits: real bars.
Scored: 15 features, 8840 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 33 cells beat the live rule in every window (chance with permuted features 30.2, p95 44), best-cell family p = 0.92; first-order stack entrants 4 (chance 3.5).
- loss-cut confirm (cut OFF when the cell is true): 331 cells beat the live rule in every window (chance with permuted features 323.9, p95 353), best-cell family p = 0.72; first-order stack entrants 0 (chance 0.1).
- early cut at -15 pts: 7 cells beat the live rule in every window (chance with permuted features 6.8, p95 12), best-cell family p = 0.38; first-order stack entrants 1 (chance 0.7).
- early cut at -25 pts: 7 cells beat the live rule in every window (chance with permuted features 9.4, p95 13), best-cell family p = 0.98; first-order stack entrants 2 (chance 1.6).
- near-zone take at 80% of target: 1 cells beat the live rule in every window (chance with permuted features 4.9, p95 9), best-cell family p = 0.97; first-order stack entrants 0 (chance 0.1).
- P7 Asia-type re-entry gate (P7 entries within 120 min of a same-side P7 loser): 20 cells beat the live rule in every window (chance with permuted features 33.5, p95 45), best-cell family p = 0.97; first-order stack entrants 0 (chance 1.3).
Best first-order stack cell (nominal): D book P7 all sessions: s3_xlk_nq_resid15 >= 2.544 (acted on 57 L6M events). Stack maxDD cut / change in mean $ per week: L6M 4.6% / +15; HOLD 8.0% / +857; PRE 1.7% / +168; X' -8.1% / +609. In the worst-20 weeks it changes P&L by +1947 $/wk and in the 20 best (trend) weeks by -1559 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): NT8 multi-series SMH/XLK/HYG; v1.8 fields smh_nq_resid15, xlk_nq_resid15, hyg_s30.

### S4 Shock detector: NQ/ES/RTY 1-s range and activity burst vs the slot norm
Data: owned NQ/ES/RTY 1-s state base (NQ volume = print sizes; ES/RTY activity = book events per second, a proxy: the slim ES/RTY state has no print sizes; ES/RTY exist only from 2023-08); scheduled-release calendar from DISCOVER_CALENDAR.csv (bls.gov, federalreserve.gov, bea.gov, census.gov, fiscaldata, ALFRED); cost $0. Proxy/limits: burst = min over NQ/ES/RTY of (3-s range, 3-s activity) / 20-day median slot norm.
Scored: 12 features, 9182 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 11 cells beat the live rule in every window (chance with permuted features 18.6, p95 25), best-cell family p = 0.13; first-order stack entrants 2 (chance 3.0).
- loss-cut confirm (cut OFF when the cell is true): 75 cells beat the live rule in every window (chance with permuted features 63.4, p95 79), best-cell family p = 0.35; first-order stack entrants 5 (chance 2.9).
- early cut at -15 pts: 3 cells beat the live rule in every window (chance with permuted features 5.5, p95 11), best-cell family p = 0.88; first-order stack entrants 2 (chance 0.8).
- early cut at -25 pts: 5 cells beat the live rule in every window (chance with permuted features 8.3, p95 14), best-cell family p = 0.50; first-order stack entrants 1 (chance 1.9).
- near-zone take at 80% of target: 61 cells beat the live rule in every window (chance with permuted features 36.2, p95 46), best-cell family p = 1.00; first-order stack entrants 0 (chance 0.9).
- P7 Asia-type re-entry gate (P7 entries within 120 min of a same-side P7 loser): 28 cells beat the live rule in every window (chance with permuted features 17.4, p95 27), best-cell family p = 0.42; first-order stack entrants 2 (chance 1.0).
Best first-order stack cell (nominal): A book M7 all sessions: s4_rty_burst60 <= 3.298 (acted on 315 L6M events). Stack maxDD cut / change in mean $ per week: L6M 5.3% / +1898; HOLD 10.4% / +2076; PRE 1.1% / +451; X' 0.0% / +373. In the worst-20 weeks it changes P&L by +919 $/wk and in the 20 best (trend) weeks by +1395 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): 1-s ES/RTY/NQ range and event counts in NT8 (needs the tick/L2 handler already used by DS7 for NQ, extended to ES/RTY); v1.8 fields shock_max60, since_shock5, shock_sched.

### S5 Calendar
Data: DISCOVER_CALENDAR.csv (BLS, Fed, BEA, Census, Treasury FiscalData, ALFRED vintages: source-confirmed; opex, month/quarter end, roll weeks: rule-derived; Treasury auction dates source-confirmed 2023-04..2026-11 only) and SEC EDGAR 8-K item 2.02 acceptance times for the megacap CIKs on the box (data/gap/edgar: AAPL MSFT AMZN NVDA COST and others); NOT verifiable on the box: Fed speaker dates, index rebalance dates other than the quarterly opex rule; cost $0. Proxy/limits: Fed speakers and rebalance effective dates are not in any verified source: not used.
Scored: 30 features, 6992 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 1 cells beat the live rule in every window (chance with permuted features 5.8, p95 10), best-cell family p = 0.02; first-order stack entrants 0 (chance 0.9).
- loss-cut confirm (cut OFF when the cell is true): 37 cells beat the live rule in every window (chance with permuted features 29.5, p95 38), best-cell family p = 0.55; first-order stack entrants 1 (chance 0.6).
- early cut at -15 pts: 2 cells beat the live rule in every window (chance with permuted features 1.4, p95 3), best-cell family p = 0.00; first-order stack entrants 0 (chance 0.1).
- early cut at -25 pts: 3 cells beat the live rule in every window (chance with permuted features 2.5, p95 6), best-cell family p = 0.08; first-order stack entrants 1 (chance 0.7).
- near-zone take at 80% of target: 24 cells beat the live rule in every window (chance with permuted features 20.4, p95 27), best-cell family p = 0.92; first-order stack entrants 0 (chance 0.1).
- P7 Asia-type re-entry gate (P7 entries within 120 min of a same-side P7 loser): 13 cells beat the live rule in every window (chance with permuted features 6.8, p95 11), best-cell family p = 1.00; first-order stack entrants 0 (chance 0.2).
Best first-order stack cell (nominal): B25 book ALL session 3: s5_dow <= 0 (acted on 86 L6M events). Stack maxDD cut / change in mean $ per week: L6M 1.5% / +74; HOLD 4.5% / +228; PRE -4.8% / +307; X' 11.1% / +608. In the worst-20 weeks it changes P&L by +712 $/wk and in the 20 best (trend) weeks by +74 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): calendar file read by DS7 (like the NTZ table): min_to_hi, min_since_hi, opex_month, month_end, in_1550, earn_day.

### S6 Desk state from the exact stack trade list
Data: LPB_BASE exact trade lists (code/th_sz/sz_exact.py lpb_reference_trades); cost $0. Proxy/limits: causal (exits <= T only).
Scored: 10 features, 7890 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 18 cells beat the live rule in every window (chance with permuted features 13.6, p95 20), best-cell family p = 0.00; first-order stack entrants 5 (chance 3.1).
- loss-cut confirm (cut OFF when the cell is true): 67 cells beat the live rule in every window (chance with permuted features 52.0, p95 63), best-cell family p = 0.00; first-order stack entrants 0 (chance 2.1).
- early cut at -15 pts: 3 cells beat the live rule in every window (chance with permuted features 3.1, p95 6), best-cell family p = 0.00; first-order stack entrants 0 (chance 0.6).
- early cut at -25 pts: 7 cells beat the live rule in every window (chance with permuted features 5.2, p95 10), best-cell family p = 0.00; first-order stack entrants 1 (chance 1.4).
- near-zone take at 80% of target: 31 cells beat the live rule in every window (chance with permuted features 36.8, p95 50), best-cell family p = 0.10; first-order stack entrants 0 (chance 1.4).
- P7 Asia-type re-entry gate (P7 entries within 120 min of a same-side P7 loser): 15 cells beat the live rule in every window (chance with permuted features 15.9, p95 22), best-cell family p = 0.08; first-order stack entrants 0 (chance 0.5).
Best first-order stack cell (nominal): D book ALL all sessions: s6_day_n >= 22 (acted on 1668 L6M events). Stack maxDD cut / change in mean $ per week: L6M 29.2% / +1493; HOLD 17.4% / +1007; PRE 20.6% / +813; X' 1.8% / +209. In the worst-20 weeks it changes P&L by +5692 $/wk and in the 20 best (trend) weeks by -5137 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): NT8 already knows its own fills: v1.8 fields stack_day_n, stack_cons_losers, stack_wr10, min_since_win, book_side_losers_today.

### S7 Tape and structure from the NQ state base
Data: owned NQ state base: prints (large-lot >= 5 and >= 10 contracts), 1-min bars for the prior-day value area/POC, anchored VWAPs, opening measures; cost $0. Proxy/limits: large-lot threshold 5/10 contracts (p95 print size is 3); VA = 70% of the prior RTH volume at 1-pt bins.
Scored: 28 features, 20012 cells (uses x books x sessions x thresholds x direction); thresholds are quantiles of the pre-2025-11-11 events only, so HOLD and L6M are forward of the thresholds.
- entry skip (half = the same cells at half effect): 63 cells beat the live rule in every window (chance with permuted features 43.1, p95 56), best-cell family p = 0.20; first-order stack entrants 5 (chance 6.8).
- loss-cut confirm (cut OFF when the cell is true): 233 cells beat the live rule in every window (chance with permuted features 197.4, p95 223), best-cell family p = 0.40; first-order stack entrants 0 (chance 0.5).
- early cut at -15 pts: 7 cells beat the live rule in every window (chance with permuted features 11.0, p95 17), best-cell family p = 0.00; first-order stack entrants 0 (chance 1.6).
- early cut at -25 pts: 7 cells beat the live rule in every window (chance with permuted features 17.0, p95 23), best-cell family p = 0.10; first-order stack entrants 1 (chance 3.9).
- near-zone take at 80% of target: 72 cells beat the live rule in every window (chance with permuted features 78.5, p95 94), best-cell family p = 0.37; first-order stack entrants 3 (chance 1.4).
- P7 Asia-type re-entry gate (P7 entries within 120 min of a same-side P7 loser): 51 cells beat the live rule in every window (chance with permuted features 52.0, p95 70), best-cell family p = 0.77; first-order stack entrants 0 (chance 3.8).
Best first-order stack cell (nominal): D book ALL session 3: s7_in_va >= 1 (acted on 320 L6M events). Stack maxDD cut / change in mean $ per week: L6M 9.6% / +1452; HOLD 14.6% / +1400; PRE 0.6% / +520; X' 11.7% / +851. In the worst-20 weeks it changes P&L by +3644 $/wk and in the 20 best (trend) weeks by -3445 $/wk.
Does NOT enter the joint set: the number of cells that help the stack is not above what permuted features give, or the family p is above 0.05. Treat the best cell as noise-level.
Live feed it would need in NT8 (v1.8): NT8 tick handler: large-lot net 30/120 s, sweep_rev15/60, poc_dist, va_in, avwap_open_dist, avwap_week_dist, open_er30.

## F - regime flag for T-WORKS B1
Weekly mean of each unsigned/signed screen feature vs the 20 best (trend) and 20 worst weeks of the stack: 163 features, 2 separate them by AUC >= 0.75 or <= 0.25, a permutation of the week labels gives 1.0 on average (p95 4). Top: s3_fesx_s5 AUC 0.25; s2_brd15 AUC 0.25; s2_brd30 AUC 0.26; s3_fdax_s5 AUC 0.26. Side-signed features average out over a week and are weak flags by construction; the VIX family and the calendar are unsigned and are the honest candidates. The S6 desk features are excluded (they are built from the same week P&L).

## Candidates sent to the exact engine (queue exact_queue_Z_screens.txt, SZ-CORE, behind P7 FIX / T-CROSS / near-zone / early-cut)
S6 desk state: skip every new entry once N stack trades have already closed in the label day (N = 22, 18, 14; sets SCR_S6_DAYN22/18/14). First-order: positive mean and a maxDD cut in all four windows for N = 14, 18 and 22 (a plateau) and negative from N = 26 up, so it is a day-count cap, not a fitted point; one exact month already run (2026-10): 769 -> 503 trades, +$12.2k -> +$32.2k. S7 tape: skip NY-AM entries while price sits inside the prior RTH 70% value area (SCR_S7_INVA_NYAM). Neither is counted as entering the joint set until its exact four windows, bi-weekly blocks and scorecard are in (below).
Why these two and not the others: they are the only first-order cells whose mean is positive in all four windows with a maxDD cut on L6M and HOLD, on a plateau; every other family is at or under its own placebo count.

## Notes
Scorecard a-e, bi-weekly WF and exact results are appended below per candidate as they complete.

#### Exact sets (one set per job, TP engine, engine = base + screen gate hook th_screens/scr_hooks.py; bases LPB_BASE and JN04RM)
- JN05W_S6_C22 vs LPB_BASE: 43 of 43 months done.
  months better/worse/equal vs the base (of 43 done): 23 / 7 / 13; sum +163314 $.
  window L6M: stack maxDD 51253 -> 36697 (cut 28.4%), mean per week +3371 $ (18898 -> 22270), trades 4651 -> 4004; weeks: set minus base in the base 20 worst weeks +nan $/wk, in its 20 best +nan $/wk.
  L6M contiguous 2-week blocks: set beat or equalled the base in 7 of 8.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window HOLD: stack maxDD 78842 -> 70281 (cut 10.9%), mean per week +2359 $ (16775 -> 19134), trades 8303 -> 7346; weeks: set minus base in the base 20 worst weeks +4097 $/wk, in its 20 best +196 $/wk.
  HOLD contiguous 2-week blocks: set beat or equalled the base in 15 of 20.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window PRE: stack maxDD 99479 -> 85153 (cut 14.4%), mean per week +697 $ (13304 -> 14001), trades 7801 -> 7294; weeks: set minus base in the base 20 worst weeks +1002 $/wk, in its 20 best -187 $/wk.
  PRE contiguous 2-week blocks: set beat or equalled the base in 25 of 35.
  window X': stack maxDD 73615 -> 73615 (cut 0.0%), mean per week +0 $ (3567 -> 3567), trades 3029 -> 3029; weeks: set minus base in the base 20 worst weeks +0 $/wk, in its 20 best +0 $/wk.
  X' contiguous 2-week blocks: set beat or equalled the base in 11 of 11.
- JN05W_S6_C22_RM vs JN04RM: 43 of 43 months done.
  months better/worse/equal vs the base (of 43 done): 22 / 10 / 11; sum +120989 $.
  window L6M: stack maxDD 39092 -> 39221 (cut -0.3%), mean per week +1831 $ (19528 -> 21359), trades 5078 -> 4238; weeks: set minus base in the base 20 worst weeks +nan $/wk, in its 20 best +nan $/wk.
  L6M contiguous 2-week blocks: set beat or equalled the base in 6 of 8.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window HOLD: stack maxDD 72757 -> 54311 (cut 25.4%), mean per week +1364 $ (12732 -> 14095), trades 8896 -> 7610; weeks: set minus base in the base 20 worst weeks +2715 $/wk, in its 20 best +580 $/wk.
  HOLD contiguous 2-week blocks: set beat or equalled the base in 13 of 20.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window PRE: stack maxDD 66714 -> 45095 (cut 32.4%), mean per week +291 $ (10301 -> 10592), trades 8121 -> 7531; weeks: set minus base in the base 20 worst weeks +875 $/wk, in its 20 best -603 $/wk.
  PRE contiguous 2-week blocks: set beat or equalled the base in 21 of 35.
  window X': stack maxDD 57041 -> 57041 (cut 0.0%), mean per week +0 $ (1873 -> 1873), trades 3056 -> 3056; weeks: set minus base in the base 20 worst weeks +0 $/wk, in its 20 best +0 $/wk.
  X' contiguous 2-week blocks: set beat or equalled the base in 11 of 11.
- JN05W_S6_N22 vs LPB_BASE: 0 of 43 months done.
- JN05W_S6_N22_RM vs JN04RM: 0 of 43 months done.
- JN05W_S6_C18 vs LPB_BASE: 43 of 43 months done.
  months better/worse/equal vs the base (of 43 done): 20 / 16 / 7; sum +87698 $.
  window L6M: stack maxDD 51253 -> 32588 (cut 36.4%), mean per week +1657 $ (18898 -> 20555), trades 4651 -> 3738; weeks: set minus base in the base 20 worst weeks +nan $/wk, in its 20 best +nan $/wk.
  L6M contiguous 2-week blocks: set beat or equalled the base in 5 of 8.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window HOLD: stack maxDD 78842 -> 65763 (cut 16.6%), mean per week +623 $ (16775 -> 17398), trades 8303 -> 6922; weeks: set minus base in the base 20 worst weeks +2603 $/wk, in its 20 best -1809 $/wk.
  HOLD contiguous 2-week blocks: set beat or equalled the base in 12 of 20.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window PRE: stack maxDD 99479 -> 79203 (cut 20.4%), mean per week +765 $ (13304 -> 14069), trades 7801 -> 7000; weeks: set minus base in the base 20 worst weeks +1205 $/wk, in its 20 best +71 $/wk.
  PRE contiguous 2-week blocks: set beat or equalled the base in 21 of 35.
  window X': stack maxDD 73615 -> 73622 (cut -0.0%), mean per week -81 $ (3567 -> 3486), trades 3029 -> 3003; weeks: set minus base in the base 20 worst weeks -93 $/wk, in its 20 best -93 $/wk.
  X' contiguous 2-week blocks: set beat or equalled the base in 9 of 11.
- JN05W_S6_C18_RM vs JN04RM: 43 of 43 months done.
  months better/worse/equal vs the base (of 43 done): 20 / 18 / 5; sum +88162 $.
  window L6M: stack maxDD 39092 -> 29873 (cut 23.6%), mean per week +2072 $ (19528 -> 21600), trades 5078 -> 4020; weeks: set minus base in the base 20 worst weeks +nan $/wk, in its 20 best +nan $/wk.
  L6M contiguous 2-week blocks: set beat or equalled the base in 5 of 8.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window HOLD: stack maxDD 72757 -> 46484 (cut 36.1%), mean per week +1291 $ (12732 -> 14023), trades 8896 -> 7213; weeks: set minus base in the base 20 worst weeks +3878 $/wk, in its 20 best -488 $/wk.
  HOLD contiguous 2-week blocks: set beat or equalled the base in 12 of 20.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window PRE: stack maxDD 66714 -> 36447 (cut 45.4%), mean per week +352 $ (10301 -> 10653), trades 8121 -> 7276; weeks: set minus base in the base 20 worst weeks +1876 $/wk, in its 20 best -1127 $/wk.
  PRE contiguous 2-week blocks: set beat or equalled the base in 21 of 35.
  window X': stack maxDD 57041 -> 58309 (cut -2.2%), mean per week -136 $ (1873 -> 1737), trades 3056 -> 3044; weeks: set minus base in the base 20 worst weeks -156 $/wk, in its 20 best -156 $/wk.
  X' contiguous 2-week blocks: set beat or equalled the base in 9 of 11.
- JN05W_S6_N18 vs LPB_BASE: 0 of 43 months done.
- JN05W_S6_N18_RM vs JN04RM: 0 of 43 months done.
- JN05W_S6_C14 vs LPB_BASE: 43 of 43 months done.
  months better/worse/equal vs the base (of 43 done): 22 / 20 / 1; sum +58512 $.
  window L6M: stack maxDD 51253 -> 25105 (cut 51.0%), mean per week +2389 $ (18898 -> 21287), trades 4651 -> 3384; weeks: set minus base in the base 20 worst weeks +nan $/wk, in its 20 best +nan $/wk.
  L6M contiguous 2-week blocks: set beat or equalled the base in 5 of 8.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window HOLD: stack maxDD 78842 -> 69365 (cut 12.0%), mean per week +434 $ (16775 -> 17209), trades 8303 -> 6381; weeks: set minus base in the base 20 worst weeks +5250 $/wk, in its 20 best -3583 $/wk.
  HOLD contiguous 2-week blocks: set beat or equalled the base in 11 of 20.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window PRE: stack maxDD 99479 -> 81184 (cut 18.4%), mean per week +813 $ (13304 -> 14117), trades 7801 -> 6585; weeks: set minus base in the base 20 worst weeks +2163 $/wk, in its 20 best +1069 $/wk.
  PRE contiguous 2-week blocks: set beat or equalled the base in 17 of 35.
  window X': stack maxDD 73615 -> 66545 (cut 9.6%), mean per week +523 $ (3567 -> 4090), trades 3029 -> 2934; weeks: set minus base in the base 20 worst weeks +602 $/wk, in its 20 best +430 $/wk.
  X' contiguous 2-week blocks: set beat or equalled the base in 10 of 11.
- JN05W_S6_C14_RM vs JN04RM: 43 of 43 months done.
  months better/worse/equal vs the base (of 43 done): 19 / 22 / 2; sum -22943 $.
  window L6M: stack maxDD 39092 -> 21304 (cut 45.5%), mean per week +5219 $ (19528 -> 24747), trades 5078 -> 3763; weeks: set minus base in the base 20 worst weeks +nan $/wk, in its 20 best +nan $/wk.
  L6M contiguous 2-week blocks: set beat or equalled the base in 6 of 8.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window HOLD: stack maxDD 72757 -> 67178 (cut 7.7%), mean per week +1866 $ (12732 -> 14598), trades 8896 -> 6794; weeks: set minus base in the base 20 worst weeks +4217 $/wk, in its 20 best -151 $/wk.
  HOLD contiguous 2-week blocks: set beat or equalled the base in 13 of 20.
  scorecard failed: ModuleNotFoundError("No module named 'scr_card'")
  window PRE: stack maxDD 66714 -> 45677 (cut 31.5%), mean per week -231 $ (10301 -> 10069), trades 8121 -> 6845; weeks: set minus base in the base 20 worst weeks +2529 $/wk, in its 20 best -2404 $/wk.
  PRE contiguous 2-week blocks: set beat or equalled the base in 17 of 35.
  window X': stack maxDD 57041 -> 50888 (cut 10.8%), mean per week +207 $ (1873 -> 2079), trades 3056 -> 2976; weeks: set minus base in the base 20 worst weeks +312 $/wk, in its 20 best +6 $/wk.
  X' contiguous 2-week blocks: set beat or equalled the base in 9 of 11.
- JN05W_S6_N14 vs LPB_BASE: 0 of 43 months done.
- JN05W_S6_N14_RM vs JN04RM: 0 of 43 months done.
- JN05W_S6_L10 vs LPB_BASE: 0 of 43 months done.
- JN05W_S6_L10_RM vs JN04RM: 0 of 43 months done.


#### Extras for s1_ best cell (D ALL 3 s1_vvix 104.5)
Bi-weekly walk-forward (re-pick on the trailing 52 weeks, apply to the next 2 weeks, 26 blocks 2025-11-11..2026-10-30): the picks were made in 26 blocks and gained in 12, lost in 10; total +13026 $, +251 $ per week versus the live rule. Placebo (features permuted) gives +562 $/wk on average (range -398 to +1222).
Behavioural scorecard a-e, first-order (cached LPB_BASE path features; exact sets use behavior_scorecard.py), fixed cell, before to after:
- L6M per week (stack): a full stops 24.5 -> 24.3 ($-40052 -> $-39815); b give-backs 9.1 -> 9.1 ($-14009 -> $-14009), round-trips 9.0 -> 9.0; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -51344 -> -51119; d no-new-evidence re-entries 37.3 -> 37.1 ($-363 -> $-230); e recoveries cut 13.7 -> 13.5 ($46863 -> $46438), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $20230.
- HOLD per week (stack): a full stops 23.0 -> 22.0 ($-37923 -> $-36826); b give-backs 8.0 -> 7.6 ($-12167 -> $-11868), round-trips 7.8 -> 7.5; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -43521 -> -41756; d no-new-evidence re-entries 30.0 -> 28.3 ($732 -> $1202); e recoveries cut 12.2 -> 11.4 ($41657 -> $39869), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $16130.
- PRE per week (stack): a full stops 16.9 -> 15.8 ($-28859 -> $-27672); b give-backs 5.2 -> 4.7 ($-7549 -> $-7074), round-trips 4.8 -> 4.3; c same-side loss runs max 11 -> 11, p95 4 -> 4, $ on 3rd+ -22384 -> -20720; d no-new-evidence re-entries 12.7 -> 11.3 ($-160 -> $-0); e recoveries cut 6.7 -> 6.0 ($22256 -> $20462), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $11895.
- X' per week (stack): a full stops 17.5 -> 17.0 ($-28195 -> $-27726); b give-backs 3.6 -> 3.6 ($-4902 -> $-4902), round-trips 3.0 -> 3.0; c same-side loss runs max 7 -> 7, p95 4 -> 4, $ on 3rd+ -12302 -> -12090; d no-new-evidence re-entries 2.7 -> 2.7 ($569 -> $537); e recoveries cut 2.5 -> 2.5 ($9968 -> $9901), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1361.


#### Extras for s1i_i best cell (D ALL -1 s1i_vix_s5 35.48)
Bi-weekly walk-forward (re-pick on the trailing 52 weeks, apply to the next 2 weeks, 26 blocks 2025-11-11..2026-10-30): the picks were made in 23 blocks and gained in 10, lost in 13; total -80470 $, -1547 $ per week versus the live rule. Placebo (features permuted) gives -687 $/wk on average (range -1703 to +459).
Behavioural scorecard a-e, first-order (cached LPB_BASE path features; exact sets use behavior_scorecard.py), fixed cell, before to after:
- L6M per week (stack): a full stops 24.5 -> 16.5 ($-40052 -> $-26880); b give-backs 9.1 -> 6.1 ($-14009 -> $-9754), round-trips 9.0 -> 6.1; c same-side loss runs max 12 -> 12, p95 6 -> 5, $ on 3rd+ -51344 -> -34189; d no-new-evidence re-entries 37.3 -> 22.9 ($-363 -> $-110); e recoveries cut 13.7 -> 8.4 ($46863 -> $31890), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $20668.
- HOLD per week (stack): a full stops 23.0 -> 16.4 ($-37923 -> $-27354); b give-backs 8.0 -> 5.6 ($-12167 -> $-8850), round-trips 7.8 -> 5.5; c same-side loss runs max 12 -> 12, p95 6 -> 5, $ on 3rd+ -43521 -> -29714; d no-new-evidence re-entries 30.0 -> 20.3 ($732 -> $1085); e recoveries cut 12.2 -> 8.1 ($41657 -> $29151), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $15498.
- PRE per week (stack): a full stops 16.9 -> 16.9 ($-28859 -> $-28859); b give-backs 5.2 -> 5.2 ($-7549 -> $-7549), round-trips 4.8 -> 4.8; c same-side loss runs max 11 -> 11, p95 4 -> 4, $ on 3rd+ -22384 -> -22384; d no-new-evidence re-entries 12.7 -> 12.7 ($-160 -> $-160); e recoveries cut 6.7 -> 6.7 ($22256 -> $22256), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $11882.
- X' per week (stack): a full stops 17.5 -> 17.5 ($-28195 -> $-28195); b give-backs 3.6 -> 3.6 ($-4902 -> $-4902), round-trips 3.0 -> 3.0; c same-side loss runs max 7 -> 7, p95 4 -> 4, $ on 3rd+ -12302 -> -12302; d no-new-evidence re-entries 2.7 -> 2.7 ($569 -> $569); e recoveries cut 2.5 -> 2.5 ($9968 -> $9968), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1342.


#### Extras for s2 best cell (E ALL -1 s2_brd30 0)
Bi-weekly walk-forward (re-pick on the trailing 52 weeks, apply to the next 2 weeks, 26 blocks 2025-11-11..2026-10-30): the picks were made in 26 blocks and gained in 9, lost in 14; total +20233 $, +389 $ per week versus the live rule. Placebo (features permuted) gives -272 $/wk on average (range -811 to +287).
Behavioural scorecard a-e, first-order (cached LPB_BASE path features; exact sets use behavior_scorecard.py), fixed cell, before to after:
- L6M per week (stack): a full stops 24.5 -> 24.5 ($-40052 -> $-39862); b give-backs 9.1 -> 8.8 ($-14009 -> $-13307), round-trips 9.0 -> 8.7; c same-side loss runs max 12 -> 10, p95 6 -> 6, $ on 3rd+ -51344 -> -46374; d no-new-evidence re-entries 37.3 -> 34.0 ($-363 -> $2391); e recoveries cut 13.7 -> 13.2 ($46863 -> $43820), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $22091.
- HOLD per week (stack): a full stops 23.0 -> 22.9 ($-37923 -> $-37735); b give-backs 8.0 -> 7.8 ($-12167 -> $-11623), round-trips 7.8 -> 7.6; c same-side loss runs max 12 -> 10, p95 6 -> 6, $ on 3rd+ -43521 -> -40111; d no-new-evidence re-entries 30.0 -> 27.1 ($732 -> $1283); e recoveries cut 12.2 -> 11.9 ($41657 -> $39933), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $15931.
- PRE per week (stack): a full stops 16.9 -> 16.8 ($-28859 -> $-28789); b give-backs 5.2 -> 5.1 ($-7549 -> $-7439), round-trips 4.8 -> 4.7; c same-side loss runs max 11 -> 11, p95 4 -> 4, $ on 3rd+ -22384 -> -20577; d no-new-evidence re-entries 12.7 -> 11.4 ($-160 -> $537); e recoveries cut 6.7 -> 6.5 ($22256 -> $21307), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $12596.
- X' per week (stack): a full stops 17.5 -> 17.5 ($-28195 -> $-28195); b give-backs 3.6 -> 3.5 ($-4902 -> $-4770), round-trips 3.0 -> 3.0; c same-side loss runs max 7 -> 7, p95 4 -> 4, $ on 3rd+ -12302 -> -11823; d no-new-evidence re-entries 2.7 -> 2.3 ($569 -> $518); e recoveries cut 2.5 -> 2.4 ($9968 -> $9364), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1676.


#### Extras for s3 best cell (E P7 -1 s3_e6_s60 -0.4372)
Bi-weekly walk-forward (re-pick on the trailing 52 weeks, apply to the next 2 weeks, 26 blocks 2025-11-11..2026-10-30): the picks were made in 26 blocks and gained in 12, lost in 13; total +15924 $, +306 $ per week versus the live rule. Placebo (features permuted) gives -576 $/wk on average (range -1871 to +532).
Behavioural scorecard a-e, first-order (cached LPB_BASE path features; exact sets use behavior_scorecard.py), fixed cell, before to after:
- L6M per week (stack): a full stops 24.5 -> 24.5 ($-40052 -> $-39862); b give-backs 9.1 -> 9.0 ($-14009 -> $-13725), round-trips 9.0 -> 8.9; c same-side loss runs max 12 -> 11, p95 6 -> 6, $ on 3rd+ -51344 -> -46169; d no-new-evidence re-entries 37.3 -> 34.3 ($-363 -> $1155); e recoveries cut 13.7 -> 13.3 ($46863 -> $44167), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $21928.
- HOLD per week (stack): a full stops 23.0 -> 22.9 ($-37923 -> $-37735); b give-backs 8.0 -> 7.9 ($-12167 -> $-11893), round-trips 7.8 -> 7.7; c same-side loss runs max 12 -> 11, p95 6 -> 6, $ on 3rd+ -43521 -> -39853; d no-new-evidence re-entries 30.0 -> 27.5 ($732 -> $826); e recoveries cut 12.2 -> 11.9 ($41657 -> $39882), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $15660.
- PRE per week (stack): a full stops 16.9 -> 16.8 ($-28859 -> $-28768); b give-backs 5.2 -> 5.1 ($-7549 -> $-7402), round-trips 4.8 -> 4.7; c same-side loss runs max 11 -> 9, p95 4 -> 4, $ on 3rd+ -22384 -> -20473; d no-new-evidence re-entries 12.7 -> 11.1 ($-160 -> $-100); e recoveries cut 6.7 -> 6.5 ($22256 -> $21192), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $12075.
- X' per week (stack): a full stops 17.5 -> 17.5 ($-28195 -> $-28144); b give-backs 3.6 -> 3.5 ($-4902 -> $-4860), round-trips 3.0 -> 3.0; c same-side loss runs max 7 -> 7, p95 4 -> 4, $ on 3rd+ -12302 -> -11715; d no-new-evidence re-entries 2.7 -> 2.3 ($569 -> $823); e recoveries cut 2.5 -> 2.4 ($9968 -> $9391), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1941.


#### Extras for s3_fdax_s3_fesx_eu best cell (D ALL -1 s3_fesx_nq_resid15 4.163)
Bi-weekly walk-forward (re-pick on the trailing 52 weeks, apply to the next 2 weeks, 26 blocks 2025-11-11..2026-10-30): the picks were made in 26 blocks and gained in 10, lost in 16; total -178550 $, -3434 $ per week versus the live rule. Placebo (features permuted) gives -1916 $/wk on average (range -3465 to +47).
Behavioural scorecard a-e, first-order (cached LPB_BASE path features; exact sets use behavior_scorecard.py), fixed cell, before to after:
- L6M per week (stack): a full stops 24.5 -> 22.1 ($-40052 -> $-35804); b give-backs 9.1 -> 7.9 ($-14009 -> $-12282), round-trips 9.0 -> 7.8; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -51344 -> -42255; d no-new-evidence re-entries 37.3 -> 32.5 ($-363 -> $-1206); e recoveries cut 13.7 -> 12.1 ($46863 -> $40150), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $21910.
- HOLD per week (stack): a full stops 23.0 -> 20.1 ($-37923 -> $-32932); b give-backs 8.0 -> 6.7 ($-12167 -> $-10356), round-trips 7.8 -> 6.6; c same-side loss runs max 12 -> 12, p95 6 -> 5, $ on 3rd+ -43521 -> -33629; d no-new-evidence re-entries 30.0 -> 25.5 ($732 -> $422); e recoveries cut 12.2 -> 10.3 ($41657 -> $35081), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $15685.
- PRE per week (stack): a full stops 16.9 -> 16.0 ($-28859 -> $-27284); b give-backs 5.2 -> 5.0 ($-7549 -> $-7227), round-trips 4.8 -> 4.6; c same-side loss runs max 11 -> 8, p95 4 -> 4, $ on 3rd+ -22384 -> -20126; d no-new-evidence re-entries 12.7 -> 11.6 ($-160 -> $33); e recoveries cut 6.7 -> 6.3 ($22256 -> $20941), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $13093.
- X' per week (stack): a full stops 17.5 -> 17.5 ($-28195 -> $-28195); b give-backs 3.6 -> 3.6 ($-4902 -> $-4902), round-trips 3.0 -> 3.0; c same-side loss runs max 7 -> 7, p95 4 -> 4, $ on 3rd+ -12302 -> -12302; d no-new-evidence re-entries 2.7 -> 2.7 ($569 -> $569); e recoveries cut 2.5 -> 2.5 ($9968 -> $9968), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1342.


#### Extras for s3_smh_s3_xlk_s3_hyg_etf best cell (D P7 -1 s3_xlk_nq_resid15 2.544)
Bi-weekly walk-forward (re-pick on the trailing 52 weeks, apply to the next 2 weeks, 26 blocks 2025-11-11..2026-10-30): the picks were made in 26 blocks and gained in 17, lost in 9; total +39560 $, +761 $ per week versus the live rule. Placebo (features permuted) gives +864 $/wk on average (range -351 to +1634).
Behavioural scorecard a-e, first-order (cached LPB_BASE path features; exact sets use behavior_scorecard.py), fixed cell, before to after:
- L6M per week (stack): a full stops 24.5 -> 24.5 ($-40052 -> $-39872); b give-backs 9.1 -> 9.0 ($-14009 -> $-13791), round-trips 9.0 -> 8.9; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -51344 -> -49756; d no-new-evidence re-entries 37.3 -> 36.8 ($-363 -> $120); e recoveries cut 13.7 -> 13.4 ($46863 -> $45508), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $20779.
- HOLD per week (stack): a full stops 23.0 -> 22.9 ($-37923 -> $-37652); b give-backs 8.0 -> 7.9 ($-12167 -> $-11993), round-trips 7.8 -> 7.7; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -43521 -> -41809; d no-new-evidence re-entries 30.0 -> 29.5 ($732 -> $1051); e recoveries cut 12.2 -> 11.9 ($41657 -> $39968), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $16414.
- PRE per week (stack): a full stops 16.9 -> 16.9 ($-28859 -> $-28859); b give-backs 5.2 -> 5.0 ($-7549 -> $-7286), round-trips 4.8 -> 4.6; c same-side loss runs max 11 -> 11, p95 4 -> 4, $ on 3rd+ -22384 -> -21618; d no-new-evidence re-entries 12.7 -> 12.5 ($-160 -> $-161); e recoveries cut 6.7 -> 6.4 ($22256 -> $21212), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $12120.
- X' per week (stack): a full stops 17.5 -> 17.5 ($-28195 -> $-28195); b give-backs 3.6 -> 3.5 ($-4902 -> $-4843), round-trips 3.0 -> 3.0; c same-side loss runs max 7 -> 6, p95 4 -> 4, $ on 3rd+ -12302 -> -10922; d no-new-evidence re-entries 2.7 -> 2.6 ($569 -> $504); e recoveries cut 2.5 -> 2.4 ($9968 -> $9068), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1447.


#### Extras for s4 best cell (A M7 -1 s4_rty_burst60 3.298)
Bi-weekly walk-forward (re-pick on the trailing 52 weeks, apply to the next 2 weeks, 26 blocks 2025-11-11..2026-10-30): the picks were made in 26 blocks and gained in 14, lost in 12; total +66468 $, +1278 $ per week versus the live rule. Placebo (features permuted) gives +739 $/wk on average (range +116 to +1411).
Behavioural scorecard a-e, first-order (cached LPB_BASE path features; exact sets use behavior_scorecard.py), fixed cell, before to after:
- L6M per week (stack): a full stops 24.5 -> 34.1 ($-40052 -> $-53112); b give-backs 9.1 -> 9.0 ($-14009 -> $-14334), round-trips 9.0 -> 8.9; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -51344 -> -51093; d no-new-evidence re-entries 37.3 -> 37.3 ($-363 -> $608); e recoveries cut 13.7 -> 10.7 ($46863 -> $40502), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $21042.
- HOLD per week (stack): a full stops 23.0 -> 31.3 ($-37923 -> $-49161); b give-backs 8.0 -> 7.9 ($-12167 -> $-12413), round-trips 7.8 -> 7.7; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -43521 -> -43268; d no-new-evidence re-entries 30.0 -> 30.0 ($732 -> $1403); e recoveries cut 12.2 -> 9.5 ($41657 -> $35758), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $16885.
- PRE per week (stack): a full stops 16.9 -> 21.0 ($-28859 -> $-34462); b give-backs 5.2 -> 5.0 ($-7549 -> $-7559), round-trips 4.8 -> 4.6; c same-side loss runs max 11 -> 11, p95 4 -> 4, $ on 3rd+ -22384 -> -22619; d no-new-evidence re-entries 12.7 -> 12.7 ($-160 -> $-9); e recoveries cut 6.7 -> 5.5 ($22256 -> $19647), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $12357.
- X' per week (stack): a full stops 17.5 -> 18.7 ($-28195 -> $-29953); b give-backs 3.6 -> 3.5 ($-4902 -> $-4950), round-trips 3.0 -> 3.0; c same-side loss runs max 7 -> 7, p95 4 -> 4, $ on 3rd+ -12302 -> -12274; d no-new-evidence re-entries 2.7 -> 2.7 ($569 -> $622); e recoveries cut 2.5 -> 2.2 ($9968 -> $9104), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1552.


#### Extras for s5 best cell (B25 ALL 3 s5_dow 0)
Bi-weekly walk-forward (re-pick on the trailing 52 weeks, apply to the next 2 weeks, 26 blocks 2025-11-11..2026-10-30): the picks were made in 23 blocks and gained in 12, lost in 10; total +1959 $, +38 $ per week versus the live rule. Placebo (features permuted) gives +21 $/wk on average (range -471 to +551).
Behavioural scorecard a-e, first-order (cached LPB_BASE path features; exact sets use behavior_scorecard.py), fixed cell, before to after:
- L6M per week (stack): a full stops 24.5 -> 24.0 ($-40052 -> $-39425); b give-backs 9.1 -> 9.4 ($-14009 -> $-14182), round-trips 9.0 -> 9.4; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -51344 -> -51262; d no-new-evidence re-entries 37.3 -> 37.3 ($-363 -> $-329); e recoveries cut 13.7 -> 14.1 ($46863 -> $47455), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $19944.
- HOLD per week (stack): a full stops 23.0 -> 22.2 ($-37923 -> $-37088); b give-backs 8.0 -> 8.5 ($-12167 -> $-12442), round-trips 7.8 -> 8.3; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -43521 -> -43316; d no-new-evidence re-entries 30.0 -> 30.0 ($732 -> $833); e recoveries cut 12.2 -> 12.7 ($41657 -> $42401), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $15560.
- PRE per week (stack): a full stops 16.9 -> 16.0 ($-28859 -> $-27856); b give-backs 5.2 -> 5.7 ($-7549 -> $-7885), round-trips 4.8 -> 5.3; c same-side loss runs max 11 -> 11, p95 4 -> 4, $ on 3rd+ -22384 -> -22117; d no-new-evidence re-entries 12.7 -> 12.7 ($-160 -> $-135); e recoveries cut 6.7 -> 7.2 ($22256 -> $23249), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $12187.
- X' per week (stack): a full stops 17.5 -> 16.1 ($-28195 -> $-26650); b give-backs 3.6 -> 4.0 ($-4902 -> $-5075), round-trips 3.0 -> 3.4; c same-side loss runs max 7 -> 7, p95 4 -> 4, $ on 3rd+ -12302 -> -11924; d no-new-evidence re-entries 2.7 -> 2.7 ($569 -> $662); e recoveries cut 2.5 -> 2.9 ($9968 -> $10665), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1851.


#### Extras for s6 best cell (D ALL -1 s6_day_n 22)
Bi-weekly walk-forward (re-pick on the trailing 52 weeks, apply to the next 2 weeks, 26 blocks 2025-11-11..2026-10-30): the picks were made in 26 blocks and gained in 14, lost in 12; total -127559 $, -2453 $ per week versus the live rule. Placebo (features permuted) gives -1939 $/wk on average (range -4852 to -984).
Behavioural scorecard a-e, first-order (cached LPB_BASE path features; exact sets use behavior_scorecard.py), fixed cell, before to after:
- L6M per week (stack): a full stops 24.5 -> 15.7 ($-40052 -> $-26423); b give-backs 9.1 -> 5.8 ($-14009 -> $-9607), round-trips 9.0 -> 5.7; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -51344 -> -35700; d no-new-evidence re-entries 37.3 -> 19.3 ($-363 -> $258); e recoveries cut 13.7 -> 8.0 ($46863 -> $32970), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $20181.
- HOLD per week (stack): a full stops 23.0 -> 16.3 ($-37923 -> $-27616); b give-backs 8.0 -> 5.6 ($-12167 -> $-9284), round-trips 7.8 -> 5.4; c same-side loss runs max 12 -> 12, p95 6 -> 5, $ on 3rd+ -43521 -> -31427; d no-new-evidence re-entries 30.0 -> 16.5 ($732 -> $1620); e recoveries cut 12.2 -> 7.5 ($41657 -> $29471), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $16473.
- PRE per week (stack): a full stops 16.9 -> 14.7 ($-28859 -> $-25778); b give-backs 5.2 -> 4.3 ($-7549 -> $-6546), round-trips 4.8 -> 4.0; c same-side loss runs max 11 -> 7, p95 4 -> 4, $ on 3rd+ -22384 -> -19760; d no-new-evidence re-entries 12.7 -> 9.4 ($-160 -> $278); e recoveries cut 6.7 -> 5.3 ($22256 -> $18532), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $13027.
- X' per week (stack): a full stops 17.5 -> 17.2 ($-28195 -> $-27865); b give-backs 3.6 -> 3.5 ($-4902 -> $-4908), round-trips 3.0 -> 3.0; c same-side loss runs max 7 -> 7, p95 4 -> 4, $ on 3rd+ -12302 -> -12274; d no-new-evidence re-entries 2.7 -> 2.6 ($569 -> $627); e recoveries cut 2.5 -> 2.5 ($9968 -> $9968), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1432.


#### S6 cap family, first-order detail (LPB_BASE trade list; exact sets JN05W_S6_* run one set per job on LPB_BASE and JN04RM, see exact block)
- stack closes >= 22 AND day P&L <= -2 R: removes 1275 entries over 3.5 years. Stack maxDD cut / mean change per week: L6M 28% / +3575; HOLD 10% / +2340; PRE 6% / +705; X' 0% / +0. Months (43): 24 better, 6 worse, 13 unchanged; 2-week blocks: 75 of 93 not worse over all history, 19 of 25 in HOLD. Removed trades change P&L by +4725 $/wk in the 20 worst weeks and -585 $/wk in the 20 best (trend) weeks. Frozen live week replay (first-order, live trade list, 180 trades, +$102830): it would have skipped 2 trades worth +4066 $ (4% of the week).
  months lost: 202408 -2196, 202411 -927, 202505 -12736, 202509 -1943, 202601 -9733, 202607 -21294.
  scorecard a-e L6M per week (stack): a full stops 24.5 -> 20.8 ($-40052 -> $-34136); b give-backs 9.1 -> 7.8 ($-14009 -> $-12246), round-trips 9.0 -> 7.7; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -51344 -> -47244; d no-new-evidence re-entries 37.3 -> 31.0 ($-363 -> $-643); e recoveries cut 13.7 -> 12.0 ($46863 -> $42899), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $22612.
  scorecard a-e HOLD per week (stack): a full stops 23.0 -> 20.3 ($-37923 -> $-33790); b give-backs 8.0 -> 7.2 ($-12167 -> $-11159), round-trips 7.8 -> 7.0; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -43521 -> -40198; d no-new-evidence re-entries 30.0 -> 25.3 ($732 -> $865); e recoveries cut 12.2 -> 10.7 ($41657 -> $37778), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $17688.
  scorecard a-e PRE per week (stack): a full stops 16.9 -> 16.0 ($-28859 -> $-27636); b give-backs 5.2 -> 4.8 ($-7549 -> $-7191), round-trips 4.8 -> 4.4; c same-side loss runs max 11 -> 7, p95 4 -> 4, $ on 3rd+ -22384 -> -21187; d no-new-evidence re-entries 12.7 -> 11.1 ($-160 -> $272); e recoveries cut 6.7 -> 6.1 ($22256 -> $20810), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $12705.
  scorecard a-e X' per week (stack): a full stops 17.5 -> 17.5 ($-28195 -> $-28195); b give-backs 3.6 -> 3.6 ($-4902 -> $-4902), round-trips 3.0 -> 3.0; c same-side loss runs max 7 -> 7, p95 4 -> 4, $ on 3rd+ -12302 -> -12302; d no-new-evidence re-entries 2.7 -> 2.7 ($569 -> $569); e recoveries cut 2.5 -> 2.5 ($9968 -> $9968), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1342.
- stack closes >= 18 AND day P&L <= -2 R: removes 1891 entries over 3.5 years. Stack maxDD cut / mean change per week: L6M 36% / +2442; HOLD 16% / +1545; PRE 7% / +809; X' -0% / -81. Months (43): 23 better, 13 worse, 7 unchanged; 2-week blocks: 62 of 93 not worse over all history, 14 of 25 in HOLD. Removed trades change P&L by +6973 $/wk in the 20 worst weeks and -1802 $/wk in the 20 best (trend) weeks. Frozen live week replay (first-order, live trade list, 180 trades, +$102830): it would have skipped 2 trades worth +4066 $ (4% of the week).
  months lost: 202306 -1101, 202308 -7286, 202401 -1856, 202408 -1129, 202410 -3116, 202411 -6443, 202505 -17382, 202508 -7737, 202509 -1928, 202510 -6311, 202511 -1750, 202601 -18545, 202607 -17382.
  scorecard a-e L6M per week (stack): a full stops 24.5 -> 19.7 ($-40052 -> $-32471); b give-backs 9.1 -> 7.4 ($-14009 -> $-11599), round-trips 9.0 -> 7.3; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -51344 -> -45310; d no-new-evidence re-entries 37.3 -> 28.9 ($-363 -> $-625); e recoveries cut 13.7 -> 11.5 ($46863 -> $41573), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $21967.
  scorecard a-e HOLD per week (stack): a full stops 23.0 -> 19.5 ($-37923 -> $-32512); b give-backs 8.0 -> 6.8 ($-12167 -> $-10713), round-trips 7.8 -> 6.7; c same-side loss runs max 12 -> 12, p95 6 -> 5, $ on 3rd+ -43521 -> -38752; d no-new-evidence re-entries 30.0 -> 23.6 ($732 -> $688); e recoveries cut 12.2 -> 10.3 ($41657 -> $36764), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $17314.
  scorecard a-e PRE per week (stack): a full stops 16.9 -> 15.5 ($-28859 -> $-26869); b give-backs 5.2 -> 4.7 ($-7549 -> $-6976), round-trips 4.8 -> 4.3; c same-side loss runs max 11 -> 7, p95 4 -> 4, $ on 3rd+ -22384 -> -20566; d no-new-evidence re-entries 12.7 -> 10.3 ($-160 -> $24); e recoveries cut 6.7 -> 5.8 ($22256 -> $19762), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $12837.
  scorecard a-e X' per week (stack): a full stops 17.5 -> 17.4 ($-28195 -> $-28055); b give-backs 3.6 -> 3.5 ($-4902 -> $-4833), round-trips 3.0 -> 3.0; c same-side loss runs max 7 -> 7, p95 4 -> 4, $ on 3rd+ -12302 -> -12302; d no-new-evidence re-entries 2.7 -> 2.7 ($569 -> $560); e recoveries cut 2.5 -> 2.5 ($9968 -> $9899), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1165.
- stack closes >= 14 AND day P&L <= -2 R: removes 2725 entries over 3.5 years. Stack maxDD cut / mean change per week: L6M 55% / +3454; HOLD 11% / +1486; PRE 20% / +984; X' 10% / +523. Months (43): 22 better, 20 worse, 1 unchanged; 2-week blocks: 59 of 93 not worse over all history, 13 of 25 in HOLD. Removed trades change P&L by +10201 $/wk in the 20 worst weeks and -1623 $/wk in the 20 best (trend) weeks. Frozen live week replay (first-order, live trade list, 180 trades, +$102830): it would have skipped 7 trades worth +10074 $ (10% of the week).
  months lost: 202308 -10421, 202309 -864, 202310 -1727, 202312 -1623, 202405 -2415, 202407 -1160, 202410 -8042, 202411 -13259, 202503 -18053, 202505 -25077, 202506 -8353, 202508 -12682, 202509 -2775, 202510 -17037, 202511 -12413, 202601 -11588, 202603 -5095, 202606 -1461, 202607 -9430, 202608 -30432.
- stack LOSING closes >= 10: removes 5518 entries over 3.5 years. Stack maxDD cut / mean change per week: L6M 63% / +3381; HOLD 18% / +649; PRE 36% / +1807; X' 11% / +500. Months (43): 24 better, 18 worse, 1 unchanged; 2-week blocks: 52 of 93 not worse over all history, 13 of 25 in HOLD. Removed trades change P&L by +13081 $/wk in the 20 worst weeks and -7544 $/wk in the 20 best (trend) weeks. Frozen live week replay (first-order, live trade list, 180 trades, +$102830): it would have skipped 105 trades worth +60515 $ (59% of the week).
  months lost: 202306 -2948, 202308 -11215, 202310 -48, 202311 -1054, 202405 -3614, 202411 -16718, 202503 -21993, 202505 -5502, 202506 -7544, 202508 -11781, 202509 -813, 202510 -12404, 202511 -66030, 202601 -20458, 202604 -14057, 202606 -36327, 202607 -35530, 202608 -47767.
- stack closes >= 22: removes 3879 entries over 3.5 years. Stack maxDD cut / mean change per week: L6M 29% / +1493; HOLD 17% / +1007; PRE 21% / +813; X' 2% / +209. Months (43): 22 better, 13 worse, 8 unchanged; 2-week blocks: 68 of 93 not worse over all history, 14 of 25 in HOLD. Removed trades change P&L by +5692 $/wk in the 20 worst weeks and -5137 $/wk in the 20 best (trend) weeks. Frozen live week replay (first-order, live trade list, 180 trades, +$102830): it would have skipped 87 trades worth +44268 $ (43% of the week).
  months lost: 202307 -69, 202308 -2052, 202404 -10772, 202407 -3904, 202409 -1967, 202411 -5374, 202412 -4750, 202506 -6277, 202510 -2342, 202511 -33016, 202601 -12050, 202606 -9134, 202607 -53642.
- stack closes >= 18: removes 5494 entries over 3.5 years. Stack maxDD cut / mean change per week: L6M 38% / +2549; HOLD 30% / +2050; PRE 23% / +146; X' 3% / +377. Months (43): 22 better, 17 worse, 4 unchanged; 2-week blocks: 61 of 93 not worse over all history, 15 of 25 in HOLD. Removed trades change P&L by +10143 $/wk in the 20 worst weeks and -7876 $/wk in the 20 best (trend) weeks. Frozen live week replay (first-order, live trade list, 180 trades, +$102830): it would have skipped 105 trades worth +41689 $ (41% of the week).
  months lost: 202304 -1258, 202306 -675, 202307 -2861, 202308 -14133, 202404 -16484, 202406 -3857, 202407 -3416, 202412 -23834, 202505 -46348, 202506 -1310, 202508 -3464, 202510 -701, 202511 -33839, 202601 -8287, 202606 -10814, 202607 -18555, 202609 -535.
- stack closes >= 14: removes 7703 entries over 3.5 years. Stack maxDD cut / mean change per week: L6M 39% / +782; HOLD 20% / +745; PRE 55% / +153; X' 5% / +477. Months (43): 18 better, 25 worse, 0 unchanged; 2-week blocks: 53 of 93 not worse over all history, 16 of 25 in HOLD. Removed trades change P&L by +15945 $/wk in the 20 worst weeks and -11052 $/wk in the 20 best (trend) weeks. Frozen live week replay (first-order, live trade list, 180 trades, +$102830): it would have skipped 121 trades worth +61276 $ (60% of the week).
  months lost: 202307 -4911, 202308 -23297, 202310 -4761, 202311 -3, 202312 -1095, 202403 -2945, 202404 -23372, 202405 -6524, 202406 -3009, 202407 -6421, 202411 -19985, 202412 -9923, 202503 -10241, 202505 -55900, 202506 -6221, 202508 -16239, 202509 -4670, 202511 -40033, 202601 -11971, 202603 -12365, 202604 -13073, 202606 -32069, 202607 -46746, 202608 -41446, 202609 -18813.


#### Extras for s7 best cell (D ALL 3 s7_in_va 1)
Bi-weekly walk-forward (re-pick on the trailing 52 weeks, apply to the next 2 weeks, 26 blocks 2025-11-11..2026-10-30): the picks were made in 26 blocks and gained in 16, lost in 10; total +34860 $, +670 $ per week versus the live rule. Placebo (features permuted) gives +343 $/wk on average (range -614 to +1366).
Behavioural scorecard a-e, first-order (cached LPB_BASE path features; exact sets use behavior_scorecard.py), fixed cell, before to after:
- L6M per week (stack): a full stops 24.5 -> 22.7 ($-40052 -> $-37978); b give-backs 9.1 -> 8.5 ($-14009 -> $-13594), round-trips 9.0 -> 8.5; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -51344 -> -48650; d no-new-evidence re-entries 37.3 -> 34.5 ($-363 -> $140); e recoveries cut 13.7 -> 12.6 ($46863 -> $44194), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $19784 -> $21638.
- HOLD per week (stack): a full stops 23.0 -> 21.0 ($-37923 -> $-35679); b give-backs 8.0 -> 7.3 ($-12167 -> $-11748), round-trips 7.8 -> 7.2; c same-side loss runs max 12 -> 12, p95 6 -> 6, $ on 3rd+ -43521 -> -40361; d no-new-evidence re-entries 30.0 -> 27.3 ($732 -> $1374); e recoveries cut 12.2 -> 10.9 ($41657 -> $38345), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $15351 -> $17061.
- PRE per week (stack): a full stops 16.9 -> 14.9 ($-28859 -> $-26659); b give-backs 5.2 -> 4.4 ($-7549 -> $-6776), round-trips 4.8 -> 4.1; c same-side loss runs max 11 -> 11, p95 4 -> 4, $ on 3rd+ -22384 -> -19770; d no-new-evidence re-entries 12.7 -> 10.7 ($-160 -> $-272); e recoveries cut 6.7 -> 5.6 ($22256 -> $19766), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $11882 -> $11965.
- X' per week (stack): a full stops 17.5 -> 14.1 ($-28195 -> $-24441); b give-backs 3.6 -> 3.0 ($-4902 -> $-4560), round-trips 3.0 -> 2.6; c same-side loss runs max 7 -> 6, p95 4 -> 4, $ on 3rd+ -12302 -> -10051; d no-new-evidence re-entries 2.7 -> 1.9 ($569 -> $461); e recoveries cut 2.5 -> 1.8 ($9968 -> $8082), fills clipped 0.0 -> 0.0 ($0 -> $0); P&L $1342 -> $1995.

