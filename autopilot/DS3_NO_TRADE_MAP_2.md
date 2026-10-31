# DS3_NO_TRADE_MAP_2 - T-NO-TRADE-EXPANDED section A: the no-trade map (NTE-1, 2026-10-31)

Research only; no live / execution / chart change; UNTOUCHED never read (masks own, capped 20260206). Prereg autopilot/NTE_prereg.md (sha256 b446844d...). Universe: 44,370 signals of 10 books x 6 sessions; state store out/ntexp/states.parquet (655 states -> 1,038 masks) + store-wide scan (all 1,219 TG-1 measures x 4 quantile cuts). Descriptive: P(target) = market-base target-exit rate (signal at market, bracket 60/60-ish); pts per contract on the N basis (no target-fill correction); M and LIVE in the parquet. Differences are IN minus OUT (out = all other signals where the state is defined), week-clustered SE, MDE = 2.8 SE. Nothing in this file selects a rule (selection is PRE u X' only in DS3_NO_TRADE_RULES_2.md).

## PAGE 1 - what the map says

* Of 955 masks with >= 30 signals in and out in the last 6 months (pooled), **10 have |z| > 3.3 on dP(target)** (a null of 955 independent masks gives 1.0). Across masks, the L6M lowering of P(target) correlates with the PRE u X' lowering at Spearman +0.08 (n = 927 masks with >= 100 signals in both), and PRE vs X' with each other at +0.25: a state that lowers P(target) in the old data is not reliably the same state in the recent data.
* States that lower P(target) in ALL four of PRE, X', HOLD, L6M with a PRE u X' z <= -2.5 and >= 100 signals: **31** (the 'most reliable precursors of a failed signal' list, section 4).

## 1. Ranked by how much the state LOWERS P(target) - pooled, last 6 months first (n_in >= 30 and n_out >= 30; units: P in % points; dP columns are IN minus OUT in pp; 'agree' = windows of HOLD / PRE / X' with the same sign as L6M)

| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | ptsM_N_in | ptsM_N_out | dP_L3M | dP_HOLD | dP_Y26 | dP_PRE | dP_X | agree |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.edge.close_nypm_end1500.last10 | 111 | 39.60 | 53.10 | -13.50 | -1.98 | -1.32 | 3.30 | -8.30 | -11.50 | -10.30 | -15.30 | -16.60 | 3 |
| tm.edge.close_nypm_end1500.last20 | 194 | 40.20 | 53.20 | -13 | -2.42 | -1.76 | 3.35 | -12.60 | -11.80 | -9.60 | -13.20 | -20.30 | 3 |
| st.15m.atr_ratio>=2.283 | 923 | 44.20 | 53.90 | -9.70 | -3.35 | -5.25 | 4.13 | -7 | -8.80 | -2.10 | -2.50 | -3.10 | 3 |
| st.vvix<=87.65 | 272 | 43.80 | 53.20 | -9.50 | -1.76 | -3.05 | 3.43 | -9 | -8.50 | -54.60 | -2.60 | -2.80 | 3 |
| cal.fri_after12 | 362 | 43.90 | 53.30 | -9.40 | -2.35 | -0.11 | 3.37 | -4.70 | -9.80 | 4.70 | -9.50 | -16.90 | 3 |
| cal.opex_day | 548 | 45.10 | 53.40 | -8.30 | -2.59 | -5.08 | 3.74 | -11 | -8.40 | -2.70 | 4.90 | 1.80 | 1 |
| st.rv30_ann>=46.11 | 598 | 45.20 | 53.50 | -8.30 | -2.65 | -7.19 | 3.93 | -8.60 | -7 | -12.10 | 0.60 | -0.40 | 2 |
| tm.edge.close_nypm_end1500.last30 | 291 | 45 | 53.20 | -8.20 | -1.94 | 2.59 | 3.26 | -8.50 | -7.70 | -5.70 | -14.20 | -19.20 | 3 |
| st.es_nq_open30_agree==-1 | 772 | 45.20 | 53.20 | -8 | -2.43 | -3.13 | 4.48 | -11.90 | -7.60 | -7.80 | 0.60 | -1.60 | 2 |
| tm.edge.close_nyam_end1200.last10 | 154 | 45.50 | 53.10 | -7.60 | -1.43 | -3.55 | 3.35 | -16.20 | -8.40 | -19.10 | 1.30 | 0.70 | 1 |
| cal.after_holiday | 121 | 45.50 | 53 | -7.60 | -4.99 | -4.90 | 3.35 | -7 | -6.60 | -8 | -0.40 | -11.80 | 3 |
| st.vix_chg5<=-3.38 | 465 | 45.80 | 53.30 | -7.50 | -1.71 | -3.31 | 3.57 | -10.50 | -6.50 | -5.50 | -0.10 | -1.50 | 3 |
| cal.quad_witch | 114 | 45.60 | 53 | -7.40 | -5.11 | -1.98 | 3.31 | -5.40 | -6.50 | -54.60 | 1.50 | 5.30 | 1 |
| tm.day.FOMC_before14 | 161 | 46 | 53.10 | -7.10 | -2.12 | -7.26 | 3.42 | -4.50 | -7.90 | -2.30 | 0.70 | 3.20 | 1 |
| px.late.travelled>=1 | 724 | 46.40 | 53.50 | -7.10 | -2.87 | -4.01 | 3.83 | -6.30 | -5.20 | -4.50 | 0.10 | 3.00 | 1 |
| evt.failbrk_low.within15 | 141 | 46.10 | 53.10 | -7 | -1.29 | -4.35 | 3.36 | -11.30 | -5.20 | 1.40 | -3.50 | -6.90 | 3 |
| tm.edge.open_london02.first10 | 52 | 46.20 | 53 | -6.80 | -0.71 | -4.90 | 3.29 | -17.90 | -3.70 | -27.50 | 6.60 | 8.30 | 1 |
| st.15m.atr_ratio>=1.856 | 1979 | 47.50 | 54.30 | -6.80 | -2.84 | -0.34 | 4.16 | -5 | -6.50 | -0.80 | -2.90 | -6.10 | 3 |
| st.1h.atr_ratio<=0.8093 | 1204 | 47 | 53.80 | -6.80 | -2.58 | -3.30 | 4.17 | -5.80 | -5.40 | -6.70 | 1.50 | 2.80 | 1 |
| px.bar.15m.lastrange_atr>=3 | 387 | 46.50 | 53.20 | -6.70 | -1.72 | -4.90 | 3.58 | -3.90 | -5.60 | -0.80 | 2.80 | 5.40 | 1 |
| px.ext.15m.ema50<=-3 | 110 | 46.40 | 53 | -6.70 | -0.83 | -4.92 | 3.34 | -10.50 | -5 | -14.80 | -1.20 | 3.20 | 2 |
| px.late.atDayExtreme5_run150 | 337 | 46.60 | 53.20 | -6.60 | -2.39 | 0.38 | 3.35 | -7.60 | -6.50 | -7.20 | 4.20 | 3.00 | 1 |
| evt.failbrk_low.within15.ict_against | 129 | 46.50 | 53 | -6.50 | -1.16 | -3.69 | 3.34 | -11 | -4.80 | 5.40 | -4.90 | -6 | 3 |
| xm.es_minus_nq15s<=-1.5 | 458 | 46.70 | 53.20 | -6.40 | -2.34 | -5.33 | 3.71 | -3.40 | -5.20 | 1.90 | 1.70 | 3.50 | 1 |
| st.vix>=24.84 | 274 | 46.70 | 53.10 | -6.40 | -1.34 | -5.11 | 3.49 | -12 | -5.40 | -54.60 | 1.00 | -47.70 | 2 |
| st.5m.atr_ratio<=0.68 | 691 | 47.20 | 53.40 | -6.20 | -1.63 | -1.36 | 3.60 | -6 | -5.90 | -12.80 | 1.40 | -1.00 | 2 |
| evt.rthgap_abs>=40 | 4942 | 49.60 | 55.80 | -6.20 | -1.54 | 0.17 | 7.35 | -10.20 | -3.00 | -10.50 | 2.50 | 3.80 | 1 |
| tm.day.CPI_morning | 209 | 46.90 | 53.10 | -6.20 | -0.76 | -3.28 | 3.39 | 3.70 | -3.50 | -20.90 | 1.80 | -0.70 | 2 |
| set.ahead20_set11 | 3217 | 48.90 | 55 | -6.10 | -3.71 | -0.66 | 5.17 | -5.90 | -5.40 | -4.90 | -2.30 | -2.40 | 3 |
| st.1h.er20>=0.5546 | 889 | 47.50 | 53.50 | -6 | -1.89 | -3.87 | 3.96 | -8.70 | -6.10 | -23.50 | 4.40 | -0.50 | 2 |
| st.1h.chop14<=32.55 | 844 | 47.50 | 53.50 | -6 | -2.38 | -3.92 | 3.92 | -8 | -4.80 | -6.30 | 3.60 | 1.80 | 1 |
| set.ahead20_set11_fresh | 1522 | 48 | 53.90 | -5.90 | -3.09 | -2.02 | 4.22 | -5.10 | -5.80 | -3.40 | -4.60 | -2.90 | 3 |
| evt.failbrk_high.within60.ict_with | 87 | 47.10 | 53 | -5.90 | -0.69 | -3.29 | 3.30 | -31.60 | -2.50 | -54.70 | -8.10 | -3.40 | 3 |
| set.ahead20_set8 | 2526 | 48.70 | 54.40 | -5.70 | -2.87 | -0.51 | 4.56 | -4.90 | -5.40 | -4.60 | -2.40 | -2.70 | 3 |
| st.cal_holiday_adj==0 | 8726 | 52.40 | 58 | -5.70 | -1.45 | 2.42 | 10.32 | -4.80 | -5.70 | -6.40 | 1.00 | 3.50 | 1 |
| cal.weekend_gap>=40 | 280 | 61.10 | 66.70 | -5.60 | -0.73 | 10.82 | 16.63 | -7.40 | -8.90 | -32.20 | 12.70 | 4.10 | 1 |
| st.vix<=14.45 | 323 | 47.70 | 53.10 | -5.50 | -0.88 | -0.07 | 3.36 | -10 | -4.50 | -54.60 | -1.50 | 2.50 | 2 |
| st.4h.atr_ratio<=0.9096 | 2239 | 48.80 | 54.20 | -5.40 | -2.22 | 0.05 | 4.20 | -10.20 | -5.10 | 5.20 | -1.50 | 1.40 | 2 |
| px.ext.15m.ema50<=-2 | 331 | 47.70 | 53.10 | -5.40 | -1.23 | -3.54 | 3.48 | -5.20 | -4.30 | 2.10 | 0.20 | -3.00 | 2 |
| px.late.atDayExtreme20_run150 | 1063 | 48.20 | 53.50 | -5.40 | -2.11 | 0.37 | 3.60 | -2.70 | -5 | -3.10 | 2.90 | -0.70 | 2 |

### 1b. The same ranking on PRE u X' only (what a forward user would have had), with what happened next

| state / cut | n_SEL | dP_SEL | z_SEL | dP_PRE | dP_X | n_in | dP_L6M | z_L6M | dP_HOLD | dP_L3M | dP_Y26 | dPts |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.edge.close_nypm_end1500.last30 | 1220 | -16 | -7.84 | -14.20 | -19.20 | 291 | -8.20 | -1.94 | -7.70 | -8.50 | -5.70 | -0.68 |
| tm.edge.close_nypm_end1500.last20 | 807 | -15.90 | -6.16 | -13.20 | -20.30 | 194 | -13 | -2.42 | -11.80 | -12.60 | -9.60 | -5.11 |
| st.sig_delta60_s<=-52 | 3372 | -5.10 | -5.74 | -4.10 | -7 | 916 | -3.40 | -2.04 | -4.10 | -2.40 | -5.90 | -0.51 |
| tm.edge.close_nypm_end1500.last10 | 481 | -16.10 | -5.72 | -15.30 | -16.60 | 111 | -13.50 | -1.98 | -11.50 | -8.30 | -10.30 | -4.62 |
| set.ahead20_set11_fresh | 6670 | -4.40 | -5.17 | -4.60 | -2.90 | 1522 | -5.90 | -3.09 | -5.80 | -5.10 | -3.40 | -6.23 |
| cal.fri_after12 | 1353 | -11.70 | -5.02 | -9.50 | -16.90 | 362 | -9.40 | -2.35 | -9.80 | -4.70 | 4.70 | -3.48 |
| xm.es60s<=0 | 9136 | -2.70 | -4.59 | -2.60 | -2.40 | 2283 | -0.20 | -0.14 | -1.50 | 1.50 | -4.00 | 2.49 |
| st.sig_vel120<=1.75 | 8761 | -2.50 | -3.97 | -2.90 | -0.90 | 2279 | -0.00 | -0.04 | -0.20 | -0.30 | -2.60 | 2.43 |
| st.sig_delta60_s<=-1 | 8476 | -2.40 | -3.90 | -2.00 | -3.60 | 2497 | -0.80 | -0.71 | -1.40 | -0.40 | -5.50 | 1.26 |
| st.sig_intens_rel<=0.5794 | 3357 | -4.40 | -3.85 | -4.70 | -3.70 | 945 | 1.20 | 0.45 | 0.80 | 1.00 | -2.90 | 3.74 |
| st.15m.atr_ratio>=1.856 | 8392 | -4.20 | -3.85 | -2.90 | -6.10 | 1979 | -6.80 | -2.84 | -6.50 | -5 | -0.80 | -4.50 |
| st.prev_er_rth>=0.2767 | 3373 | -6.20 | -3.78 | -6.60 | -4.80 | 669 | -0.20 | -0.04 | 0.20 | -5 | 4.90 | -2.00 |
| bk.delta60_sig<=-1 | 1025 | -5.60 | -3.75 | -5.50 | -4.80 | 247 | 2.20 | 0.69 | 1.60 | 5.50 | 1.60 | 5.83 |
| px.loc.ON.outside | 7210 | -4.50 | -3.72 | -3.40 | -6.30 | 2059 | -3.60 | -2.01 | -3.80 | -4.50 | -3.90 | -0.31 |
| st.1d.adx14<=16.94 | 3414 | -5.60 | -3.65 | -4.50 | -6.50 | 2720 | 2.40 | 1.23 | 3.40 | 3.20 | 2.40 | 3.48 |
| day.volT1 | 11189 | -3.60 | -3.62 | -1.40 | -9.50 | 3338 | 0.70 | 0.41 | 0.90 | 2.70 | 1.30 | 1.22 |
| st.prev_er_rth>=0.1843 | 8447 | -4.50 | -3.55 | -6.40 | 0.80 | 2413 | 3.70 | 2.01 | 4.50 | 3.30 | 4.00 | 3.82 |
| xm.es180s<=0 | 7357 | -2.10 | -3.46 | -2.90 | 0.10 | 1941 | -1.30 | -1.04 | -1.30 | 0.00 | -2.40 | 0.68 |
| st.on_range_atrd<=0.3029 | 2433 | -6.50 | -3.34 | -5.60 | -8.70 | 521 | -3.90 | -1.07 | -2.70 | -5.60 | -54.50 | -0.64 |
| st.prev_ret_rth>=0.7105 | 3353 | -5.70 | -3.29 | -5.70 | -5.70 | 1056 | 1.40 | 0.45 | 2.40 | 2.70 | -4.90 | 0.37 |
| st.vix9d_over_vix<=0.8937 | 8410 | -3.80 | -3.26 | -2.60 | -6.40 | 4386 | 0.00 | 0.01 | -0.80 | 0.70 | 4.20 | 1.67 |
| xm.es60s<=-2 | 2898 | -3.10 | -3.21 | -1.90 | -7.60 | 636 | -3.40 | -1.64 | -3.50 | -3.20 | -5.70 | -1.59 |
| void.lvn_ahead_50pctTD | 14718 | -2.80 | -3.11 | -2.20 | -3.30 | 4138 | -2.60 | -1.75 | -2.90 | -2.60 | -3.20 | -2.54 |
| st.1h.don20_w<=3.289 | 3359 | -5.20 | -3.03 | -5.20 | -5.50 | 669 | 4.90 | 1.31 | 3.70 | 8.60 | -1.80 | 6.35 |
| void.lvn_ahead_100pctTD | 19348 | -3.10 | -3.01 | -2.20 | -4.70 | 5548 | -3.50 | -2.03 | -3.80 | -3.70 | -6.10 | -3.45 |
| xm.es180s<=-2 | 3875 | -2.60 | -3.01 | -2.30 | -3.30 | 996 | -0.50 | -0.41 | -0.40 | 0.60 | -2.00 | 1.20 |
| st.sig_vel300<=2.25 | 8617 | -1.80 | -2.99 | -2.30 | -0.00 | 2347 | -0.30 | -0.21 | -0.40 | 0.20 | -5.30 | 2.16 |
| st.vvix<=87.65 | 8403 | -3.40 | -2.89 | -2.60 | -2.80 | 272 | -9.50 | -1.76 | -8.50 | -9 | -54.60 | -6.47 |
| set.ahead20_set11 | 12295 | -2.50 | -2.86 | -2.30 | -2.40 | 3217 | -6.10 | -3.71 | -5.40 | -5.90 | -4.90 | -5.83 |
| set.ahead20_set8 | 9872 | -2.70 | -2.85 | -2.40 | -2.70 | 2526 | -5.70 | -2.87 | -5.40 | -4.90 | -4.60 | -5.07 |

## 2. The OTHER edge: states that RAISE P(target) (most positive first; last 6 months, then PRE u X')

| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | ptsM_N_in | ptsM_N_out | dP_L3M | dP_HOLD | dP_Y26 | dP_PRE | dP_X | agree |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| day.inside2 | 109 | 67.90 | 52.80 | 15.10 | 15.27 | 18.32 | 3.07 | -52.30 | 16 | -54.60 | 1.70 | 1.40 | 3 |
| rnd.target_near_single | 56 | 66.10 | 52.90 | 13.20 | 1.69 | 6.45 | 3.23 | 10.60 | 11.90 | 37.90 | 12.20 | 20.80 | 3 |
| bk.spread_t>=2 | 9562 | 53.20 | 41.90 | 11.30 | 2.62 | 3.27 | 1.79 | 19.70 | 11.50 | 20 | 4.00 | 3.80 | 3 |
| st.1h.ribbon_w<=0.5002 | 781 | 62.60 | 52.10 | 10.50 | 3.36 | 13.19 | 2.38 | 9.10 | 7 | 8.20 | 1.30 | 4.50 | 3 |
| st.1m.st10_3_age>=77 | 860 | 62.40 | 52 | 10.40 | 3.26 | 14.06 | 2.20 | 10.80 | 9.90 | 16.20 | -3.00 | -1.20 | 1 |
| bk.es_imb10<=-0.3 | 271 | 62.70 | 52.70 | 10.10 | 3.01 | 12.65 | 2.98 | 5.20 | 9.10 | 0.40 | 0.20 | 7.20 | 3 |
| st.1h.adx14<=15.02 | 722 | 62.20 | 52.20 | 10 | 3.29 | 12.78 | 2.48 | 18 | 9 | 9.40 | 5.40 | 6.50 | 3 |
| bk.imb10_against_5min | 67 | 62.70 | 52.90 | 9.80 | 1.88 | 14.27 | 3.17 | 7.10 | 7.80 | -0.80 | 8.50 | -0.70 | 2 |
| rnd.target_near_x50x100 | 147 | 62.60 | 52.80 | 9.80 | 2.28 | 3.97 | 3.23 | 7.30 | 10.30 | 22.90 | 8.60 | 11.90 | 3 |
| bk.wall_ahead_rel>=10 | 141 | 62.40 | 52.80 | 9.60 | 2.12 | 12.22 | 3.11 | 3.80 | 8.80 | -3.40 | 1.20 | 1.80 | 3 |
| rnd.target_near_cluster | 52 | 61.50 | 52.90 | 8.60 | 1.39 | 3.69 | 3.24 | 2.20 | 8.40 | 9.70 | 4.10 | 3.30 | 3 |
| st.es_nq_open30_agree==1 | 5124 | 53.30 | 44.90 | 8.40 | 2.60 | 4.60 | -3.64 | 12.30 | 7.60 | 7.80 | -1.20 | 2.60 | 2 |
| bk.imb10<=-0.3 | 267 | 61 | 52.70 | 8.30 | 2.96 | 11.20 | 3.02 | 8 | 7.90 | 4.20 | 1.30 | -2.20 | 2 |
| st.5m.er20>=0.5145 | 862 | 60.40 | 52.20 | 8.20 | 3.95 | 11.63 | 2.43 | 12.10 | 8.20 | 10.70 | 0.90 | 1.30 | 3 |
| st.1d.chop14<=35.66 | 207 | 60.90 | 52.80 | 8.10 | 1.45 | 13.85 | 3.01 | 16.80 | -6.40 | -54.60 | -2.90 | -6.40 | 0 |
| stk.dup_within180s>=3 | 232 | 60.80 | 52.80 | 8 | 1.84 | 11.80 | 3.04 | 3.80 | 8.40 | 15 | 2.40 | -2.90 | 2 |
| st.4h.adx14>=43.93 | 259 | 60.60 | 52.70 | 7.90 | 2.67 | 11.50 | 3.02 | 9.60 | 8.80 | 12.50 | 0.50 | -2.40 | 2 |
| st.1h.ribbon_w>=3.719 | 499 | 60.30 | 52.60 | 7.80 | 2.61 | 11.62 | 2.79 | 1.50 | 8.90 | 2.20 | -1.60 | 3.70 | 2 |
| px.ext.1m.ema50>=5 | 331 | 60.40 | 52.70 | 7.70 | 1.97 | 11.72 | 2.95 | 7.20 | 5.40 | 8 | 0.50 | 7.30 | 3 |
| st.1m.st10_3_age>=47 | 2259 | 58.40 | 51.30 | 7.10 | 3.72 | 9.62 | 1.32 | 7.30 | 6.40 | 8.90 | -2.20 | -1.00 | 1 |
| st.on_range_atrd>=0.744 | 2087 | 56.80 | 49.80 | 7.10 | 2.78 | 6.71 | 1.06 | 6.70 | 6.40 | 2.10 | 6.10 | 1.70 | 3 |
| day.inside1 | 1061 | 59.10 | 52.20 | 6.90 | 2.78 | 10.82 | 2.32 | 5.90 | 4.40 | 1.60 | 1.60 | 1.90 | 3 |
| tm.rel.R830.pre30 | 57 | 59.60 | 52.90 | 6.70 | 0.72 | 8.82 | 3.21 | 1.00 | 6.40 | -0.80 | -7.50 | 10.50 | 2 |
| evt.failbrk_high.within30.ict_against | 160 | 59.40 | 52.80 | 6.50 | 0.88 | 11.27 | 3.11 | 11.70 | 6.80 | 8 | 3.30 | -2.70 | 2 |
| st.1m.adx14>=40.64 | 783 | 58.90 | 52.40 | 6.40 | 2.47 | 10.23 | 2.63 | 7.10 | 4.90 | 2.10 | -1.90 | -0.00 | 1 |
| st.vwap_z_eth>=2.076 | 701 | 58.60 | 52.60 | 6 | 1.64 | 8.54 | 3.07 | 3.00 | 5.80 | 2.30 | -3.10 | 1.20 | 2 |
| bk.wall_ahead_rel>=5 | 566 | 58.50 | 52.60 | 5.90 | 2.86 | 8.51 | 2.92 | 4.70 | 4.50 | 3.10 | -1.50 | 0.10 | 2 |
| st.15m.bbw_pct100<=0.4 | 2716 | 57.20 | 51.30 | 5.90 | 3.04 | 6.33 | 2.05 | 7.20 | 6.20 | 6.60 | 0.90 | 3.30 | 3 |
| st.cal_holiday_adj==1 | 1015 | 58 | 52.40 | 5.70 | 1.45 | 10.32 | 2.42 | 4.80 | 5.70 | 6.40 | -1.00 | -3.50 | 1 |
| px.late.travelled<=-0.7 | 272 | 58.50 | 52.80 | 5.70 | 1.14 | 8.82 | 3.08 | 5.60 | 6.20 | 5.80 | -0.40 | -14.20 | 1 |

| state / cut | n_SEL | dP_SEL | z_SEL | dP_PRE | dP_X | n_in | dP_L6M | z_L6M | dP_HOLD | dP_L3M |
|--|--|--|--|--|--|--|--|--|--|--|
| bk.spread_t>=3 | 17706 | 4.70 | 5.67 | 3.40 | 6.30 | 6523 | 2.80 | 1.68 | 3.50 | 3.90 |
| eng.opp_flip_within10 | 248 | 10.40 | 4.34 | 10.90 | -2.20 | 131 | 2.80 | 0.59 | 4.80 | 0.10 |
| st.on_range_atrd>=0.744 | 5927 | 5.60 | 4.27 | 6.10 | 1.70 | 2087 | 7.10 | 2.78 | 6.40 | 6.70 |
| rnd.target_near_x50x100 | 369 | 9.50 | 4.12 | 8.60 | 11.90 | 147 | 9.80 | 2.28 | 10.30 | 7.30 |
| xm.es60s>=1 | 19679 | 2.40 | 3.84 | 2.90 | 1.10 | 5487 | 1.20 | 1.07 | 1.80 | -1.30 |
| st.sig_rv_5m>=24.04 | 8392 | 3.50 | 3.77 | 2.80 | 2.10 | 3165 | -2.10 | -1.17 | -0.80 | -2.30 |
| stk.same_lots_live>=4 | 15310 | 3.40 | 3.63 | 3.40 | 4.10 | 4517 | 3.80 | 2.80 | 3.00 | 1.90 |
| cal.weekend_gap>=20 | 949 | 16.70 | 3.63 | 17.50 | 6 | 388 | 3.80 | 0.49 | 1.10 | 3.60 |
| rnd.target_near_single | 110 | 14.10 | 3.43 | 12.20 | 20.80 | 56 | 13.20 | 1.69 | 11.90 | 10.60 |
| stk.same_lots_live>=6 | 12720 | 3.00 | 3.43 | 3.10 | 3.20 | 3791 | 3.90 | 2.65 | 3.10 | 1.80 |
| bk.spread_t>=2 | 31283 | 5.20 | 3.40 | 4.00 | 3.80 | 9562 | 11.30 | 2.62 | 11.50 | 19.70 |
| st.sig_absorb10_s<=3.667 | 8430 | 2.60 | 3.18 | 1.80 | 4.10 | 2765 | 2.70 | 1.50 | 2.80 | 2.10 |
| st.vix>=20.03 | 8402 | 3.70 | 3.13 | 3.10 | -1.30 | 1578 | -2.50 | -0.76 | -1.30 | -4.10 |
| st.on_range_atrd>=0.9386 | 2383 | 6.20 | 3.07 | 5.40 | 4.60 | 1341 | 5.30 | 2.02 | 5.20 | 5.50 |
| evt.rthgap20.first120m | 6589 | 3.70 | 3.06 | 4.10 | 3.10 | 2185 | -0.10 | -0.02 | 0.70 | 0.80 |
| st.sig_er120>=0.2218 | 8392 | 2.20 | 3.03 | 2.90 | 0.70 | 2470 | 1.30 | 0.78 | 0.80 | 1.10 |
| eng.opp_flip_within15 | 404 | 6.50 | 2.87 | 6 | 3.60 | 188 | -0.80 | -0.19 | 1.40 | -2.40 |
| st.ret_YM_15m<=-6.334 | 3357 | 3.20 | 2.82 | 3.50 | 1.70 | 988 | -0.50 | -0.22 | -0.70 | 1.30 |
| st.rs_nq_rty_15m>=17.93 | 3357 | 3.60 | 2.82 | 4.10 | 2.20 | 762 | -3.90 | -1.33 | -3.50 | -3.40 |
| px.ext.5m.ema50>=5 | 2025 | 5.80 | 2.80 | 5.30 | 7.50 | 465 | 3.10 | 0.84 | 1.30 | 5.60 |
| st.1h.adx14<=15.02 | 3357 | 5.70 | 2.79 | 5.40 | 6.50 | 722 | 10 | 3.29 | 9 | 18 |
| cal.weekend_gap>=40 | 766 | 13.80 | 2.74 | 12.70 | 4.10 | 280 | -5.60 | -0.73 | -8.90 | -7.40 |
| bk.vpin50>=0.25 | 294 | 11.50 | 2.72 | 11.30 | 13.40 | 79 | -2.30 | -0.30 | -4.40 | 7.30 |
| st.prev_trend_day==0 | 26752 | 3.80 | 2.71 | 5.40 | -0.70 | 8362 | 0.20 | 0.07 | -0.40 | 1.00 |
| stk.same_lots_live>=8 | 9671 | 2.50 | 2.71 | 2.50 | 2.80 | 2898 | 4.30 | 2.53 | 3.10 | 3.30 |

## 3. Plain lines (pooled, last 6 months) for the 12 most lowering and 8 most raising states

* All signals fired in state [tm.edge.close_nypm_end1500.last10] reach the target 39.6% vs 53.1% otherwise (last 6 months, n=111; pts per contract -1.32 vs +3.30)
* All signals fired in state [tm.edge.close_nypm_end1500.last20] reach the target 40.2% vs 53.2% otherwise (last 6 months, n=194; pts per contract -1.76 vs +3.35)
* All signals fired in state [st.15m.atr_ratio>=2.283] reach the target 44.2% vs 53.9% otherwise (last 6 months, n=923; pts per contract -5.25 vs +4.13)
* All signals fired in state [st.vvix<=87.65] reach the target 43.8% vs 53.2% otherwise (last 6 months, n=272; pts per contract -3.05 vs +3.43)
* All signals fired in state [cal.fri_after12] reach the target 43.9% vs 53.3% otherwise (last 6 months, n=362; pts per contract -0.11 vs +3.37)
* All signals fired in state [cal.opex_day] reach the target 45.1% vs 53.4% otherwise (last 6 months, n=548; pts per contract -5.08 vs +3.74)
* All signals fired in state [st.rv30_ann>=46.11] reach the target 45.2% vs 53.5% otherwise (last 6 months, n=598; pts per contract -7.19 vs +3.93)
* All signals fired in state [tm.edge.close_nypm_end1500.last30] reach the target 45.0% vs 53.2% otherwise (last 6 months, n=291; pts per contract +2.59 vs +3.26)
* All signals fired in state [st.es_nq_open30_agree==-1] reach the target 45.2% vs 53.2% otherwise (last 6 months, n=772; pts per contract -3.13 vs +4.48)
* All signals fired in state [tm.edge.close_nyam_end1200.last10] reach the target 45.5% vs 53.1% otherwise (last 6 months, n=154; pts per contract -3.55 vs +3.35)
* All signals fired in state [cal.after_holiday] reach the target 45.5% vs 53.0% otherwise (last 6 months, n=121; pts per contract -4.90 vs +3.35)
* All signals fired in state [st.vix_chg5<=-3.38] reach the target 45.8% vs 53.3% otherwise (last 6 months, n=465; pts per contract -3.31 vs +3.57)
* (raises) All signals fired in state [day.inside2] reach the target 67.9% vs 52.8% otherwise (last 6 months, n=109; pts per contract +18.32 vs +3.07)
* (raises) All signals fired in state [rnd.target_near_single] reach the target 66.1% vs 52.9% otherwise (last 6 months, n=56; pts per contract +6.45 vs +3.23)
* (raises) All signals fired in state [bk.spread_t>=2] reach the target 53.2% vs 41.9% otherwise (last 6 months, n=9562; pts per contract +3.27 vs +1.79)
* (raises) All signals fired in state [st.1h.ribbon_w<=0.5002] reach the target 62.6% vs 52.1% otherwise (last 6 months, n=781; pts per contract +13.19 vs +2.38)
* (raises) All signals fired in state [st.1m.st10_3_age>=77] reach the target 62.4% vs 52.0% otherwise (last 6 months, n=860; pts per contract +14.06 vs +2.20)
* (raises) All signals fired in state [bk.es_imb10<=-0.3] reach the target 62.7% vs 52.7% otherwise (last 6 months, n=271; pts per contract +12.65 vs +2.98)
* (raises) All signals fired in state [st.1h.adx14<=15.02] reach the target 62.2% vs 52.2% otherwise (last 6 months, n=722; pts per contract +12.78 vs +2.48)
* (raises) All signals fired in state [bk.imb10_against_5min] reach the target 62.7% vs 52.9% otherwise (last 6 months, n=67; pts per contract +14.27 vs +3.17)

## 4. The states that most reliably precede a failed signal (lower P(target) in PRE, X', HOLD and L6M; PRE u X' z <= -2.5)

| state / cut | n_SEL | dP_SEL | z_SEL | dP_PRE | dP_X | dP_HOLD | dP_L6M | z_L6M | dP_L3M | dP_Y26 | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.edge.close_nypm_end1500.last30 | 1220 | -16 | -7.84 | -14.20 | -19.20 | -7.70 | -8.20 | -1.94 | -8.50 | -5.70 | 2.59 | 3.26 |
| tm.edge.close_nypm_end1500.last20 | 807 | -15.90 | -6.16 | -13.20 | -20.30 | -11.80 | -13 | -2.42 | -12.60 | -9.60 | -1.76 | 3.35 |
| st.sig_delta60_s<=-52 | 3372 | -5.10 | -5.74 | -4.10 | -7 | -4.10 | -3.40 | -2.04 | -2.40 | -5.90 | 2.79 | 3.29 |
| tm.edge.close_nypm_end1500.last10 | 481 | -16.10 | -5.72 | -15.30 | -16.60 | -11.50 | -13.50 | -1.98 | -8.30 | -10.30 | -1.32 | 3.30 |
| set.ahead20_set11_fresh | 6670 | -4.40 | -5.17 | -4.60 | -2.90 | -5.80 | -5.90 | -3.09 | -5.10 | -3.40 | -2.02 | 4.22 |
| cal.fri_after12 | 1353 | -11.70 | -5.02 | -9.50 | -16.90 | -9.80 | -9.40 | -2.35 | -4.70 | 4.70 | -0.11 | 3.37 |
| xm.es60s<=0 | 9136 | -2.70 | -4.59 | -2.60 | -2.40 | -1.50 | -0.20 | -0.14 | 1.50 | -4.00 | 5.10 | 2.61 |
| st.sig_vel120<=1.75 | 8761 | -2.50 | -3.97 | -2.90 | -0.90 | -0.20 | -0.00 | -0.04 | -0.30 | -2.60 | 5.10 | 2.68 |
| st.sig_delta60_s<=-1 | 8476 | -2.40 | -3.90 | -2.00 | -3.60 | -1.40 | -0.80 | -0.71 | -0.40 | -5.50 | 4.18 | 2.92 |
| st.15m.atr_ratio>=1.856 | 8392 | -4.20 | -3.85 | -2.90 | -6.10 | -6.50 | -6.80 | -2.84 | -5 | -0.80 | -0.34 | 4.16 |
| px.loc.ON.outside | 7210 | -4.50 | -3.72 | -3.40 | -6.30 | -3.80 | -3.60 | -2.01 | -4.50 | -3.90 | 3.37 | 3.67 |
| st.on_range_atrd<=0.3029 | 2433 | -6.50 | -3.34 | -5.60 | -8.70 | -2.70 | -3.90 | -1.07 | -5.60 | -54.50 | 2.21 | 2.85 |
| xm.es60s<=-2 | 2898 | -3.10 | -3.21 | -1.90 | -7.60 | -3.50 | -3.40 | -1.64 | -3.20 | -5.70 | 1.76 | 3.35 |
| void.lvn_ahead_50pctTD | 14718 | -2.80 | -3.11 | -2.20 | -3.30 | -2.90 | -2.60 | -1.75 | -2.60 | -3.20 | 1.78 | 4.33 |
| void.lvn_ahead_100pctTD | 19348 | -3.10 | -3.01 | -2.20 | -4.70 | -3.80 | -3.50 | -2.03 | -3.70 | -6.10 | 1.76 | 5.21 |
| xm.es180s<=-2 | 3875 | -2.60 | -3.01 | -2.30 | -3.30 | -0.40 | -0.50 | -0.41 | 0.60 | -2.00 | 4.48 | 3.27 |
| st.sig_vel300<=2.25 | 8617 | -1.80 | -2.99 | -2.30 | -0.00 | -0.40 | -0.30 | -0.21 | 0.20 | -5.30 | 4.88 | 2.72 |
| st.vvix<=87.65 | 8403 | -3.40 | -2.89 | -2.60 | -2.80 | -8.50 | -9.50 | -1.76 | -9 | -54.60 | -3.05 | 3.43 |
| set.ahead20_set11 | 12295 | -2.50 | -2.86 | -2.30 | -2.40 | -5.40 | -6.10 | -3.71 | -5.90 | -4.90 | -0.66 | 5.17 |
| set.ahead20_set8 | 9872 | -2.70 | -2.85 | -2.40 | -2.70 | -5.40 | -5.70 | -2.87 | -4.90 | -4.60 | -0.51 | 4.56 |
| st.sig_intens_rel<=0.8973 | 8393 | -2.40 | -2.85 | -2.30 | -2.70 | -2.10 | -1.80 | -0.93 | -2.50 | -1.90 | 4.02 | 3.03 |
| px.ext.1m.ema50<=-1 | 952 | -4.80 | -2.81 | -5.50 | -2.80 | -3.20 | -2.10 | -0.67 | 0.20 | -14.70 | 2.81 | 3.26 |
| px.loc.ON.sidedloc<=0.2 | 1263 | -6.40 | -2.69 | -5.50 | -7.80 | -4.30 | -3.10 | -0.80 | 0.80 | 0.80 | 2.02 | 3.67 |
| xm.es180s<=-1 | 4996 | -1.90 | -2.66 | -2.10 | -0.90 | -1.20 | -1.30 | -0.94 | -0.20 | -2.10 | 3.93 | 3.31 |
| st.5m.squeeze==1 | 3705 | -3.00 | -2.61 | -3.00 | -3.60 | -4.40 | -5.20 | -2.24 | -7 | -2.30 | -1.87 | 3.95 |
| tm.lunch.1130_1330 | 4748 | -3.70 | -2.60 | -2.70 | -6.10 | -4.60 | -3.10 | -1.20 | -6 | 1.20 | 3.55 | 3.20 |
| st.sig_vel120<=-5.25 | 3368 | -2.20 | -2.60 | -2.10 | -3.50 | -1.60 | -1.80 | -1.35 | -0.70 | -3.40 | 3.29 | 3.24 |
| st.1m.range_pos60>=0.4716 | 3361 | -2.70 | -2.58 | -2.70 | -2.20 | -2.70 | -3.00 | -1.66 | -2.30 | -1.20 | 0.44 | 3.57 |
| px.ext.1m.ema50<=-1.5 | 494 | -5.90 | -2.56 | -7.10 | -2.60 | -2.70 | -1.90 | -0.51 | -1.10 | -13.40 | 3.77 | 3.24 |
| bk.intens_rel<=0.7 | 8964 | -1.90 | -2.52 | -2.30 | -1.20 | -1.80 | -1.80 | -1.04 | -2.30 | -6.70 | 3.28 | 3.23 |
| st.sig_er120<=0.08571 | 8424 | -1.70 | -2.50 | -2.20 | -0.10 | -0.80 | -0.60 | -0.66 | -1.90 | -1.40 | 3.87 | 3.04 |

## 5. Scheduled releases (calendar: CPI / NFP / FOMC VERIFIED; claims, PCE, 10:00 data, FOMC minutes RULES-BASED; 13:00 auctions and earnings nights NOT AVAILABLE)

P(target) in state vs out, last 6 months, market base (n signals in the state; blank = < 10):

| state | ALL | KB | PE | SM | HM | MV | PB | ST | WT | DN | MA |
|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.rel.CORE830.pre5 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.CORE830.pre10 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.CORE830.pre15 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.CORE830.pre30 | 67% vs 53% (n=12) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.CORE830.post2 | 59% vs 53% (n=17) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.CORE830.post5 | 50% vs 53% (n=34) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.CORE830.post10 | 50% vs 53% (n=40) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.R830.pre5 | 93% vs 53% (n=14) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.R830.pre10 | 65% vs 53% (n=23) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.R830.pre15 | 59% vs 53% (n=37) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.R830.pre30 | 60% vs 53% (n=57) |  |  |  |  |  |  |  | 57% vs 60% (n=14) |  |  |
| tm.rel.R830.post2 | 62% vs 53% (n=32) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.R830.post5 | 57% vs 53% (n=56) |  |  |  |  | 60% vs 51% (n=10) |  |  | 73% vs 60% (n=11) |  |  |
| tm.rel.R830.post10 | 58% vs 53% (n=69) | 33% vs 50% (n=12) |  |  |  | 58% vs 51% (n=12) |  |  | 77% vs 59% (n=13) |  |  |
| tm.rel.R1000.pre5 | 50% vs 53% (n=12) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.R1000.pre10 | 52% vs 53% (n=42) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.R1000.pre15 | 56% vs 53% (n=71) | 36% vs 50% (n=14) |  |  |  | 64% vs 51% (n=11) |  | 70% vs 52% (n=10) | 64% vs 60% (n=11) |  |  |
| tm.rel.R1000.pre30 | 49% vs 53% (n=161) | 43% vs 50% (n=28) | 42% vs 49% (n=19) |  | 56% vs 52% (n=16) | 41% vs 51% (n=22) |  | 55% vs 52% (n=20) | 52% vs 60% (n=29) | 54% vs 54% (n=13) |  |
| tm.rel.R1000.post2 | 43% vs 53% (n=14) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.R1000.post5 | 54% vs 53% (n=24) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.R1000.post10 | 46% vs 53% (n=39) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMC.pre5 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMC.pre10 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMC.pre15 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMC.pre30 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMC.post2 | 40% vs 53% (n=10) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMC.post5 | 38% vs 53% (n=13) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMC.post10 | 35% vs 53% (n=17) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMCMIN.pre5 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMCMIN.pre10 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMCMIN.pre15 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMCMIN.pre30 | 14% vs 53% (n=14) |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMCMIN.post2 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMCMIN.post5 |  |  |  |  |  |  |  |  |  |  |  |
| tm.rel.FOMCMIN.post10 |  |  |  |  |  |  |  |  |  |  |  |
| tm.day.FOMC_whole | 51% vs 53% (n=334) | 58% vs 50% (n=40) | 47% vs 49% (n=43) | 42% vs 51% (n=12) | 53% vs 52% (n=38) | 50% vs 51% (n=38) | 48% vs 54% (n=23) | 48% vs 52% (n=44) | 57% vs 60% (n=60) | 50% vs 54% (n=22) | 57% vs 54% (n=14) |
| tm.day.FOMC_after14 | 57% vs 53% (n=173) | 54% vs 50% (n=24) | 50% vs 49% (n=26) |  | 64% vs 52% (n=22) | 61% vs 51% (n=18) |  | 56% vs 52% (n=25) | 57% vs 60% (n=28) |  |  |
| tm.day.FOMC_before14 | 46% vs 53% (n=161) | 62% vs 50% (n=16) | 41% vs 49% (n=17) |  | 38% vs 52% (n=16) | 40% vs 51% (n=20) | 36% vs 55% (n=14) | 37% vs 52% (n=19) | 56% vs 60% (n=32) | 46% vs 54% (n=13) |  |
| tm.day.CPI_morning | 47% vs 53% (n=209) | 41% vs 50% (n=27) | 38% vs 49% (n=26) | 33% vs 52% (n=12) | 47% vs 52% (n=17) | 38% vs 51% (n=29) | 44% vs 54% (n=18) | 52% vs 52% (n=29) | 58% vs 60% (n=31) | 67% vs 53% (n=15) |  |
| tm.day.NFP_morning | 56% vs 53% (n=307) | 54% vs 50% (n=39) | 55% vs 49% (n=38) | 60% vs 51% (n=10) | 50% vs 52% (n=24) | 46% vs 51% (n=35) | 56% vs 54% (n=27) | 61% vs 51% (n=49) | 69% vs 59% (n=51) | 42% vs 54% (n=24) | 70% vs 54% (n=10) |
| tm.day.CPINFP_morning | 53% vs 53% (n=516) | 48% vs 50% (n=66) | 48% vs 49% (n=64) | 45% vs 51% (n=22) | 49% vs 52% (n=41) | 42% vs 51% (n=64) | 51% vs 54% (n=45) | 58% vs 51% (n=78) | 65% vs 59% (n=82) | 51% vs 54% (n=39) | 67% vs 54% (n=15) |

Plain lines, the release states, KB first (last 6 months):

* KB signals fired in state [tm.rel.CORE830.pre10] reach the target 50.0% vs 50.0% otherwise (last 6 months, n=2; pts per contract -0.75 vs +1.66); PRE u X': 0.0% vs 49.3% (n=2)
* ALL signals fired in state [tm.rel.CORE830.pre10] reach the target 66.7% vs 52.9% otherwise (last 6 months, n=6; pts per contract +21.92 vs +3.23); PRE u X': 27.3% vs 50.5% (n=11)
* KB signals fired in state [tm.rel.R830.pre10] reach the target 33.3% vs 50.1% otherwise (last 6 months, n=3; pts per contract -20.92 vs +1.71); PRE u X': 33.3% vs 49.3% (n=6)
* ALL signals fired in state [tm.rel.R830.pre10] reach the target 65.2% vs 52.9% otherwise (last 6 months, n=23; pts per contract +14.90 vs +3.22); PRE u X': 40.4% vs 50.6% (n=52)
* KB signals fired in state [tm.rel.R830.pre30] reach the target 50.0% vs 50.0% otherwise (last 6 months, n=4; pts per contract -0.75 vs +1.66); PRE u X': 42.9% vs 49.3% (n=21)
* ALL signals fired in state [tm.rel.R830.pre30] reach the target 59.6% vs 52.9% otherwise (last 6 months, n=57; pts per contract +8.82 vs +3.21); PRE u X': 47.5% vs 50.6% (n=179)
* KB signals fired in state [tm.rel.R830.post5] reach the target 33.3% vs 50.2% otherwise (last 6 months, n=9; pts per contract -20.92 vs +1.82); PRE u X': 55.6% vs 49.2% (n=54)
* ALL signals fired in state [tm.rel.R830.post5] reach the target 57.1% vs 52.9% otherwise (last 6 months, n=56; pts per contract +4.95 vs +3.23); PRE u X': 59.9% vs 50.4% (n=322)
* KB signals fired in state [tm.rel.R1000.pre10] reach the target 25.0% vs 50.2% otherwise (last 6 months, n=8; pts per contract -31.00 vs +1.86); PRE u X': 70.0% vs 49.2% (n=10)
* ALL signals fired in state [tm.rel.R1000.pre10] reach the target 52.4% vs 53.0% otherwise (last 6 months, n=42; pts per contract +0.62 vs +3.26); PRE u X': 50.8% vs 50.5% (n=118)
* KB signals fired in state [tm.rel.FOMC.pre30] reach the target 0.0% vs 50.0% otherwise (last 6 months, n=0; pts per contract +0.00 vs +1.66); PRE u X': 40.0% vs 49.3% (n=5)
* ALL signals fired in state [tm.rel.FOMC.pre30] reach the target 20.0% vs 53.0% otherwise (last 6 months, n=5; pts per contract -34.05 vs +3.26); PRE u X': 36.7% vs 50.6% (n=30)
* KB signals fired in state [tm.rel.FOMC.post10] reach the target 100.0% vs 50.0% otherwise (last 6 months, n=2; pts per contract +59.76 vs +1.56); PRE u X': 60.0% vs 49.2% (n=10)
* ALL signals fired in state [tm.rel.FOMC.post10] reach the target 35.3% vs 53.0% otherwise (last 6 months, n=17; pts per contract -19.87 vs +3.29); PRE u X': 43.2% vs 50.6% (n=74)
* KB signals fired in state [tm.day.FOMC_whole] reach the target 57.5% vs 49.8% otherwise (last 6 months, n=40; pts per contract +8.33 vs +1.44); PRE u X': 53.8% vs 49.1% (n=119)
* ALL signals fired in state [tm.day.FOMC_whole] reach the target 51.5% vs 53.0% otherwise (last 6 months, n=334; pts per contract -0.44 vs +3.38); PRE u X': 53.6% vs 50.4% (n=1048)

## 6. Per book: the five most lowering and the five most raising states (n_in >= 30 in L6M; same display; 'SEL' = PRE u X')

### KB (signals in L6M: )

lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.1d.er20>=0.4625 | 60 | 33.30 | 50.90 | -17.50 | -4.26 | -17 | 1.90 | 3.20 | 2.30 | -17.29 | 2.61 |
| vol.r60_pts>=40 | 63 | 36.50 | 50.80 | -14.20 | -2.50 | -13.10 | -0.70 | -4.50 | 0.80 | -17.07 | 2.64 |
| st.15m.ribbon_w<=0.4227 | 116 | 37.90 | 51.30 | -13.30 | -2.54 | -12.70 | -3.60 | -7.20 | -4.00 | -12.35 | 3.08 |
| px.bar.15m.lastrange_atr>=3 | 35 | 37.10 | 50.40 | -13.30 | -1.58 | -14.40 | 3.10 | 9.70 | 4.70 | -14.96 | 2.13 |
| st.1m.don20_w<=3.229 | 77 | 37.70 | 50.80 | -13.20 | -2.61 | -11.70 | -11.50 | 1.20 | -8.10 | -12.78 | 2.60 |
| st.rv30_ann>=46.11 | 82 | 37.80 | 50.90 | -13.10 | -2.71 | -10.30 | 0.10 | 9.80 | 2.20 | -15.50 | 2.85 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| bk.imb10_run>=10 | 40 | 72.50 | 49.30 | 23.20 | 3.11 | 19.80 | -5.90 | -8.80 | -5.60 | 26.48 | 0.84 |
| st.1h.ribbon_w>=3.719 | 55 | 67.30 | 49.30 | 18 | 3.25 | 19.10 | 3.10 | -0.90 | 1.70 | 20.89 | 0.78 |
| stk.dup_within60s>=2 | 47 | 63.80 | 49.50 | 14.30 | 2.35 | 10.20 | -0.20 | -2.00 | -0.40 | 15.99 | 1.10 |
| st.1m.ribbon_w>=3.037 | 30 | 63.30 | 49.70 | 13.60 | 1.76 | 13.80 | 1.50 | 8.50 | 3.30 | 17.02 | 1.28 |

### PE (signals in L6M: )

lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.edge.close_nypm_end1500.last20 | 31 | 22.60 | 49.80 | -27.20 | -4.57 | -24.40 | -10.20 | -23.30 | -14 | -18.11 | 1.16 |
| xm.es_minus_nq15s<=-1.5 | 43 | 27.90 | 50.30 | -22.40 | -3.23 | -21 | 0.60 | 8.90 | 2.10 | -25.06 | 2.31 |
| tm.edge.close_nyam_end1200.last20 | 41 | 31.70 | 49.70 | -18 | -2.12 | -16 | 4.20 | -6.80 | 1.00 | -21.80 | 1.46 |
| tm.edge.close_nypm_end1500.last30 | 42 | 33.30 | 49.70 | -16.30 | -2.98 | -14.40 | -13.60 | -21.30 | -15.70 | -6.08 | 0.91 |
| st.sig_delta60_s<=-52 | 65 | 33.80 | 50 | -16.10 | -3.55 | -14.70 | -2.90 | 4.30 | -1.10 | -15.17 | 1.57 |
| evt.sweep_high.within15.ict_with | 32 | 34.40 | 49.50 | -15.10 | -1.55 | -13.10 | -0.20 | 12.20 | 2.40 | -19.65 | 1.22 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| bk.es_imb10<=-0.3 | 30 | 70 | 48.50 | 21.50 | 2.68 | 17.20 | 3.80 | -27.10 | 1.00 | 23.45 | 0.07 |
| stk.same_lots_live>=8 | 42 | 66.70 | 48.40 | 18.20 | 2.89 | 20 | 6.90 | 4.20 | 6.20 | 21.62 | -0.10 |
| vol.r30m_vs_med20d<=0.5 | 35 | 65.70 | 48.60 | 17.10 | 2.15 | 12.60 | -1.60 | 2.10 | -0.70 | 24.56 | -0.06 |
| st.1h.ribbon_w>=3.719 | 50 | 64 | 48.40 | 15.60 | 2.62 | 16.50 | 1.40 | 8.20 | 3.00 | 18.17 | -0.10 |

### SM (signals in L6M: )

lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| evt.rthgap_abs>=40 | 136 | 44.10 | 70 | -25.90 | -3.30 | -18.20 | 15.70 | -8 | 7.30 | -4.92 | 24.52 |
| st.f60_vs_med<=0.814 | 40 | 35 | 56 | -21 | -1.93 | -18.10 | 2.40 | 1.20 | 2.20 | -12.51 | 7.78 |
| evt.sweep_high.within15.ict_against | 33 | 33.30 | 53 | -19.70 | -2.20 | -15.20 | 5.80 | 4.80 | 5.30 | -19.31 | 4.90 |
| void.gap_ahead_100pctTD | 172 | 42.40 | 61.30 | -18.80 | -3.18 | -17 | 2.10 | -13 | -3.00 | -7.12 | 13.83 |
| st.4h.atr_ratio<=0.7884 | 40 | 35 | 53.30 | -18.30 | -2.23 | -17.50 | -1.70 | 1.20 | -0.10 | -16.44 | 5.10 |
| px.ext.15m.ema20>=2 | 39 | 35.90 | 53.10 | -17.20 | -2.05 | -15.80 | -2.50 | 4.80 | -0.10 | -17.81 | 5.22 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.15m.ribbon_w<=0.4227 | 45 | 68.90 | 48 | 20.90 | 2.41 | 17.80 | -0.50 | -2.50 | -0.50 | 22.11 | -0.95 |
| st.sig_imb5_s<=-0.2381 | 32 | 68.80 | 48.90 | 19.80 | 2.28 | 21.40 | -4.00 | 4.90 | -0.90 | 23.94 | -0.09 |
| st.1d.er20>=0.355 | 37 | 67.60 | 48.70 | 18.80 | 5.29 | 14.70 | -1.70 | 7.40 | 1.30 | 22.45 | -0.33 |
| day.inside1 | 31 | 67.70 | 49.10 | 18.60 | 1.95 | 14.30 | 1.90 | -5.30 | 0.40 | 21.96 | 0.21 |

### HM (signals in L6M: )

lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.edge.close_nypm_end1500.last30 | 31 | 29 | 52.70 | -23.70 | -2.97 | -24.10 | -9.40 | -7.60 | -9 | -3.07 | 5.01 |
| cal.fri_after12 | 39 | 35.90 | 52.60 | -16.70 | -2.00 | -15.30 | -11.60 | -7.40 | -10.50 | -3.17 | 5.09 |
| st.15m.atr_ratio>=2.283 | 77 | 37.70 | 53.20 | -15.60 | -2.73 | -16.80 | -3.00 | -8.30 | -5.10 | -10.46 | 6.15 |
| vol.r30m_vs_med20d<=0.5 | 35 | 37.10 | 52.50 | -15.40 | -1.80 | -14.30 | -3.00 | 2.70 | -1.50 | -7.33 | 5.22 |
| stk.opp_lots_res>=30 | 94 | 38.30 | 53.50 | -15.20 | -4.35 | -13.50 | -3.60 | 1.00 | -2.40 | -10.71 | 6.52 |
| st.5m.range_pos60<=-0.07456 | 80 | 38.80 | 53.20 | -14.40 | -2.23 | -11.60 | 1.90 | 2.20 | 2.00 | -10.55 | 6.21 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.5m.hma_slope>=0.527 | 75 | 72 | 50.10 | 21.90 | 4.00 | 23 | -2.50 | 7.50 | 0.40 | 27.89 | 2.66 |
| px.ext.1m.ema50>=5 | 53 | 71.70 | 50.70 | 21 | 3.53 | 22.60 | -0.50 | 5.60 | 1.20 | 26.28 | 3.41 |
| st.15m.chop14<=33.29 | 65 | 69.20 | 50.60 | 18.60 | 3.83 | 17.30 | 13.40 | 0.30 | 8.70 | 23.97 | 3.26 |
| px.ext.5m.ema20>=3 | 113 | 68.10 | 49.60 | 18.50 | 4.71 | 17.10 | -5.90 | 7.40 | -2.00 | 21.70 | 2.33 |

### MV (signals in L6M: )

lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| bk.depth_rel>=1.5 | 30 | 30 | 51.30 | -21.30 | -2.58 | -16.90 | -3.50 | 14.90 | 0.80 | -17.56 | 2.82 |
| st.es_nq_open30_agree==-1 | 90 | 37.80 | 52.80 | -15 | -2.63 | -14.30 | -1.00 | -2.30 | -2.40 | -10.10 | 5.57 |
| tm.edge.open_rth0930.first10 | 39 | 38.50 | 51.20 | -12.70 | -1.68 | -11.50 | 0.10 | 1.00 | 0.20 | -14.71 | 2.89 |
| st.vvix<=87.65 | 31 | 38.70 | 51.10 | -12.40 | -3.26 | -11.30 | -3.40 | -3.30 | -4.80 | -8.00 | 2.57 |
| st.1m.squeeze==1 | 106 | 39.60 | 51.90 | -12.30 | -2.65 | -9.40 | -1.10 | -8 | -2.80 | -8.69 | 3.41 |
| st.sig_rty_nq_div5<=-1.812 | 97 | 40.20 | 51.60 | -11.40 | -2.51 | -9.20 | 3.60 | 2.90 | 3.10 | -10.77 | 3.42 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.4h.adx14>=43.93 | 30 | 66.70 | 50.30 | 16.30 | 6.60 | 17.40 | -0.70 | -1.30 | -0.80 | 21.07 | 1.77 |
| st.1h.ribbon_w<=0.5002 | 86 | 65.10 | 49.60 | 15.50 | 2.26 | 10.40 | 3.50 | 10.50 | 5.30 | 19.44 | 0.87 |
| st.es_nq_open30_agree==1 | 605 | 52.90 | 37.60 | 15.30 | 2.74 | 14.20 | 0.50 | 3.70 | 2.40 | 5.70 | -10.45 |
| st.vix9d_over_vix>=1.017 | 41 | 63.40 | 50.30 | 13.10 | 4.86 | 14.20 | 1.50 | -1.40 | 2.40 | 17.19 | 1.72 |

### PB (signals in L6M: )

lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.1m.bbw_pct100>=0.95 | 43 | 37.20 | 55.20 | -18 | -2.32 | -18.30 | 1.30 | -6.70 | -0.70 | -16.23 | 8.19 |
| evt.failbrk_low.within60.ict_against | 43 | 37.20 | 55.20 | -18 | -2.80 | -15.90 | 0.30 | 4.90 | 1.70 | -10.90 | 7.92 |
| aft.book_winner_within10 | 53 | 37.70 | 55.40 | -17.60 | -2.96 | -17.70 | 2.50 | 3.80 | 2.90 | -14.11 | 8.36 |
| st.1h.range_pos60<=-0.3645 | 36 | 38.90 | 54.90 | -16.10 | -2.03 | -15.40 | -7.10 | 1.90 | -4.90 | -10.41 | 7.74 |
| xm.es180s<=-1 | 746 | 52.80 | 68.90 | -16 | -2.46 | -7.20 | 5.30 | -1.20 | 3.60 | 5.47 | 23.98 |
| st.5m.st10_3_dist>=3.015 | 106 | 40.60 | 56.20 | -15.60 | -3.01 | -14.40 | 4.80 | 0.10 | 3.70 | -8.90 | 9.20 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.1h.ribbon_w<=0.5002 | 57 | 70.20 | 53.20 | 17 | 3.69 | 15.30 | -2.30 | -2.30 | -2.30 | 25.18 | 5.70 |
| st.sig_rv_5m<=5.882 | 40 | 70 | 53.50 | 16.50 | 2.20 | 11.20 | -0.80 | 7.70 | 2.50 | 23.45 | 6.18 |
| st.open_drive30<=-0.2624 | 64 | 67.20 | 51.20 | 16 | 2.44 | 12.80 | 1.50 | 1.90 | 1.60 | 20.05 | 5.08 |
| stk.opp_lots_live>=4 | 72 | 68.10 | 53 | 15 | 2.47 | 11.10 | -0.10 | 14.70 | 4.00 | 23.41 | 5.49 |

### ST (signals in L6M: )

lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| evt.sweep_low.within15.ict_with | 41 | 36.60 | 52.30 | -15.80 | -2.20 | -13 | -3.40 | 5.60 | -1.00 | -16.98 | 4.60 |
| st.15m.atr_ratio>=2.283 | 136 | 40.40 | 53.20 | -12.80 | -3.00 | -9.80 | -5.10 | -6.50 | -5.70 | -7.72 | 5.31 |
| xm.es15s<=-2 | 35 | 40 | 51.80 | -11.80 | -1.62 | -8.90 | 1.90 | 6 | 2.90 | -12.85 | 4.07 |
| st.prev_rng_atrd<=0.5293 | 80 | 41.20 | 52.60 | -11.30 | -2.18 | -10.10 | 3.20 | -10.30 | 0.90 | -7.51 | 4.67 |
| px.loc.DEAL1H.sidedloc<=0.2 | 51 | 41.20 | 52.30 | -11.10 | -1.40 | -11.50 | -2.20 | 17.10 | 1.10 | -10.67 | 4.52 |
| st.4h.er20>=0.5451 | 46 | 41.30 | 52.20 | -10.90 | -1.85 | -9.70 | -1.30 | -5.60 | -2.70 | -5.00 | 4.24 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.1m.st10_3_age>=77 | 94 | 67 | 50.60 | 16.40 | 3.25 | 15.70 | -1.30 | 2.30 | -0.40 | 19.85 | 2.61 |
| st.sig_es_nq_div5>=0.6062 | 69 | 66.70 | 51.10 | 15.50 | 2.75 | 14.90 | 5.30 | 3.00 | 4.30 | 21.68 | 3.16 |
| st.1h.ribbon_w<=0.5002 | 97 | 66 | 50.60 | 15.30 | 4.87 | 10.70 | 1.10 | 11.60 | 3.70 | 19.49 | 2.59 |
| st.vwap_z_rth<=0.0491 | 55 | 61.80 | 48.20 | 13.60 | 1.82 | 12.20 | 2.90 | -9.90 | 1.10 | 15.00 | 2.88 |

### WT (signals in L6M: )

lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| cal.weekend_gap>=80 | 39 | 56.40 | 75 | -18.60 | -1.64 | -18 | 4.80 | -0.80 | 5.60 | -1.26 | 13.57 |
| cal.weekend_gap>=40 | 51 | 60.80 | 75 | -14.20 | -1.39 | -14.80 | 7.80 | -0.80 | 7.90 | 2.23 | 13.57 |
| bk.wall_behind_rel>=5 | 35 | 45.70 | 59.90 | -14.20 | -1.93 | -11.60 | 1.50 | 2.50 | 1.80 | -9.19 | 2.01 |
| st.rv30_ann>=46.11 | 79 | 46.80 | 60.20 | -13.40 | -3.39 | -11.70 | 3.40 | -2.10 | 3.10 | -8.90 | 2.30 |
| vol.r15m_vs_med20d<=0.5 | 54 | 48.10 | 60 | -11.80 | -1.30 | -11.60 | 2.40 | -23.20 | -0.90 | -3.93 | 1.97 |
| day.chop_er_chop | 96 | 49 | 60.20 | -11.30 | -2.87 | -9.80 | 4.00 | 7.40 | 4.60 | -7.20 | 2.32 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| bk.depth_rel>=1.5 | 40 | 72.50 | 59.30 | 13.20 | 1.31 | 8.20 | -0.20 | -10.70 | -2.80 | 12.10 | 1.53 |
| st.1m.st10_3_age>=77 | 120 | 71.70 | 58.70 | 13 | 3.38 | 12.60 | 3.60 | -3.00 | 1.60 | 10.91 | 1.09 |
| st.1m.adx14>=40.64 | 74 | 71.60 | 59.10 | 12.60 | 2.87 | 11.50 | 3.90 | 2.50 | 3.50 | 10.87 | 1.37 |
| st.1h.adx14<=15.02 | 126 | 70.60 | 58.70 | 11.90 | 3.33 | 9.60 | 3.30 | 5 | 3.80 | 10.32 | 1.10 |

### DN (signals in L6M: )

lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.gap_atrd>=0.5322 | 35 | 28.60 | 51.70 | -23.10 | -3.94 | -22.90 | 4.60 | 2.00 | 4.30 | -23.54 | 5.80 |
| evt.sweep_low.within15.ict_with | 30 | 36.70 | 54.50 | -17.90 | -2.41 | -14.60 | -7.40 | -16.90 | -10.80 | -16.88 | 7.27 |
| st.rs_nq_rty_15m>=17.93 | 62 | 38.70 | 55.20 | -16.50 | -3.06 | -11.30 | 4.30 | -1.90 | 2.30 | -12.01 | 8.01 |
| cal.opex_day | 34 | 38.20 | 54.60 | -16.30 | -2.56 | -17.40 | 8.20 | -2.40 | 5 | -14.98 | 7.32 |
| st.sig_rty_move20_atr<=-2.297 | 50 | 40 | 54.70 | -14.70 | -2.25 | -16.10 | 6.60 | 3.70 | 5.80 | -7.88 | 7.16 |
| st.4h.atr_ratio<=0.7884 | 73 | 41.10 | 55.30 | -14.20 | -2.85 | -11.10 | 1.80 | 0.50 | 2.60 | -8.94 | 8.00 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.vwap_z_eth>=2.076 | 66 | 68.20 | 52.20 | 16 | 2.93 | 13.90 | -8.20 | -7.80 | -8.20 | 21.25 | 4.54 |
| st.1d.er20>=0.355 | 62 | 67.70 | 52.40 | 15.30 | 2.63 | 10 | 0.10 | 3.70 | 1.10 | 23.99 | 4.52 |
| px.ext.1m.ema50>=2 | 651 | 54.80 | 40 | 14.80 | 2.50 | 11.70 | 1.40 | 5.30 | 2.30 | 7.32 | -7.87 |
| st.1d.chop14<=40.58 | 49 | 67.30 | 52.80 | 14.60 | 2.17 | 5.30 | 2.30 | 1.90 | 2.00 | 21.55 | 5.09 |

### MA (signals in L6M: )

lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.rv1m_vs_med20d>=5.811 | 30 | 33.30 | 56.20 | -22.90 | -2.95 | -22.20 | -8.40 | -24.50 | -12.40 | -17.45 | 8.70 |
| st.5m.bbw_pct100<=0.13 | 45 | 35.60 | 56.90 | -21.40 | -2.41 | -16.30 | 7.10 | 0.40 | 4.50 | -17.49 | 9.79 |
| st.15m.macd_hist>=0.2832 | 51 | 39.20 | 56.70 | -17.50 | -2.46 | -16.40 | -1.30 | -11.70 | -4.90 | -12.29 | 9.50 |
| st.rs_nq_es_15m<=-0.5707 | 71 | 40.80 | 57.40 | -16.60 | -2.57 | -10 | 4.30 | 3.50 | 4.20 | -7.11 | 9.71 |
| cal.month_last2 | 42 | 40.50 | 56.20 | -15.70 | -1.86 | -8.10 | 6.10 | -7.90 | 1.80 | -11.48 | 8.87 |
| st.5m.atr_ratio<=0.8632 | 109 | 43.10 | 58.70 | -15.60 | -3.11 | -17.40 | -1.30 | 5.50 | 0.90 | -6.42 | 11.60 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|--|
| st.1h.adx14<=15.02 | 32 | 75 | 52.80 | 22.20 | 2.68 | 26.90 | 13.10 | -0.10 | 9 | 29.51 | 4.83 |
| st.1h.atr_ratio<=0.9103 | 132 | 66.70 | 48.70 | 17.90 | 4.20 | 14.20 | 8.10 | -4.50 | 5 | 21.04 | -0.08 |
| st.1m.rsi14>=68.17 | 46 | 69.60 | 52.60 | 16.90 | 1.92 | 9.20 | -2.30 | 6.90 | 0.70 | 22.93 | 4.71 |
| st.1m.chop14<=34.86 | 52 | 69.20 | 52.40 | 16.80 | 1.87 | 8.60 | -4.20 | -8.40 | -5.40 | 22.52 | 4.47 |

## 7. Per session (pooled books)

### asia
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL |
|--|--|--|--|--|--|--|--|--|--|
| st.5m.atr_ratio>=1.604 | 46 | 39.10 | 55.90 | -16.70 | -1.15 | -23.40 | 1.40 | -20.30 | -2.70 |
| st.rs_nq_es_15m<=-3.331 | 73 | 39.70 | 56 | -16.30 | -1.97 | -13.10 | 5.10 | -0.50 | 4.30 |
| st.es_nq_open30_agree==-1 | 251 | 42.60 | 57.20 | -14.60 | -2.20 | -13.10 | 1.80 | -0.40 | 0.60 |
| st.ret_RTY_15m>=30.98 | 31 | 41.90 | 55.70 | -13.80 | -1.15 | -21.30 | 2.30 | -17.40 | 1.60 |
| void.fvg_ahead_tgt | 2109 | 52.80 | 65.90 | -13.10 | -4.96 | -11.30 | 1.00 | 6.50 | 2.80 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL |
|--|--|--|--|--|--|--|--|--|--|
| day.inside2 | 31 | 100 | 55 | 45 | 28.05 | 46.20 | -4.70 | 37.20 | 5 |
| rnd.target_near_x50x100 | 36 | 86.10 | 55.10 | 31 | 4.69 | 30.30 | 4.10 | 13.80 | 6.20 |
| st.1m.st10_3_age>=77 | 339 | 74 | 52.90 | 21.20 | 5.59 | 21.50 | 4.90 | -5 | 1.70 |

### london
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL |
|--|--|--|--|--|--|--|--|--|--|
| tm.day.FOMC_before14 | 56 | 28.60 | 56.50 | -27.90 | -3.00 | -28.60 | -0.60 | -21.70 | -5 |
| tm.day.FOMC_whole | 56 | 28.60 | 56.50 | -27.90 | -3.00 | -28.60 | -0.60 | -21.70 | -5 |
| px.late.travelled>=1 | 61 | 34.40 | 56.40 | -22 | -2.33 | -21.60 | 11.30 | -53.50 | 10.80 |
| st.4h.er20>=0.5451 | 72 | 34.70 | 56.50 | -21.80 | -2.52 | -21.40 | 0.80 | -10.60 | -2.00 |
| st.1h.squeeze==0 | 1908 | 54.50 | 72.50 | -18 | -2.82 | -17 | -6.40 | -7.20 | -6.40 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL |
|--|--|--|--|--|--|--|--|--|--|
| st.15m.bbw_pct100>=0.97 | 61 | 80.30 | 55 | 25.30 | 3.65 | 22.50 | -2.80 | 15.30 | 1.30 |
| bk.es_imb10<=-0.3 | 39 | 74.40 | 55.40 | 19 | 3.08 | 13.90 | -4.80 | -14.30 | -6.30 |
| st.1h.squeeze==1 | 142 | 72.50 | 54.50 | 18 | 2.82 | 17 | 6.40 | 7.20 | 6.40 |

### pre
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL |
|--|--|--|--|--|--|--|--|--|--|
| px.bar.15m.lastrange_atr>=3 | 37 | 27 | 55.10 | -28.10 | -2.30 | -19.10 | 2.20 | 5.90 | 3.20 |
| st.15m.rng_exp1>=3.505 | 37 | 27 | 55.10 | -28.10 | -2.30 | -19.10 | -6.10 | 5.10 | -2.60 |
| st.prev_rng_atrd<=0.5293 | 35 | 28.60 | 54.80 | -26.30 | -1.59 | -23.10 | -2.50 | 18.70 | 0.50 |
| st.5m.bbw_pct100>=1 | 94 | 33 | 57.70 | -24.70 | -2.22 | -23.60 | -7.10 | 1.70 | -4.60 |
| st.1h.swing_run>=3 | 90 | 33.30 | 57.40 | -24.10 | -2.81 | -14.20 | -8.40 | 8.50 | -4.10 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL |
|--|--|--|--|--|--|--|--|--|--|
| st.1h.swing_run<=-3 | 67 | 77.60 | 49.10 | 28.60 | 4.15 | 23.30 | 0.80 | 6.10 | 2.50 |
| evt.sweep_low.within15.ict_against | 39 | 76.90 | 50.90 | 26 | 2.18 | 16.40 | -8.20 | -11.30 | -9.10 |
| evt.sweep_low.within15 | 50 | 74 | 50.60 | 23.40 | 1.75 | 16.50 | -1.10 | -0.80 | -1.00 |

### nyam
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL |
|--|--|--|--|--|--|--|--|--|--|
| cal.after_holiday | 33 | 27.30 | 53 | -25.80 | -4.36 | -25.10 | -0.10 | -30.60 | -4.30 |
| px.ext.5m.ema200>=8 | 86 | 33.70 | 53.30 | -19.60 | -3.23 | -20.40 | 16.40 | 7 | 13.30 |
| st.rv30m_vs_med20d<=1.063 | 48 | 35.40 | 53 | -17.60 | -3.13 | -19.10 | -8.50 | -3.90 | -7.20 |
| st.prev_close_loc>=0.4225 | 170 | 36.50 | 53.80 | -17.30 | -2.19 | -13.10 | -0.90 | 0.70 | -0.40 |
| cal.quad_witch | 36 | 36.10 | 52.90 | -16.80 | -1.13 | -16.20 | 0.90 | 13.30 | 4.30 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL |
|--|--|--|--|--|--|--|--|--|--|
| tm.day.FOMC_before14 | 66 | 71.20 | 52.30 | 18.90 | 4.70 | 14.90 | -1.00 | 14.10 | 3.50 |
| tm.day.FOMC_whole | 66 | 71.20 | 52.30 | 18.90 | 4.70 | 14.90 | -1.00 | 14.10 | 3.50 |
| rnd.target_near_x50x100 | 38 | 71.10 | 52.50 | 18.60 | 2.21 | 15.60 | 11.30 | -4.00 | 6.30 |

### nypm
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL |
|--|--|--|--|--|--|--|--|--|--|
| st.rv30_ann<=7.067 | 35 | 14.30 | 46.80 | -32.50 | -3.58 | -33.10 | -45.30 | 13 | -26.30 |
| st.5m.bbw_pct100<=0.13 | 30 | 16.70 | 46.70 | -30 | -4.07 | -28.90 | -8.80 | 3.00 | -5.70 |
| xm.es_minus_nq15s<=-1.5 | 31 | 19.40 | 46.60 | -27.30 | -4.01 | -22.50 | 2.90 | 3.60 | 3.90 |
| px.ext.5m.ema50>=5 | 43 | 20.90 | 46.80 | -25.90 | -2.85 | -19 | 0.30 | 11.40 | 3.50 |
| st.rv30m_vs_med20d<=1.063 | 130 | 23.80 | 48 | -24.10 | -5.37 | -25.60 | -14.60 | -1.50 | -11.60 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | dP_SEL |
|--|--|--|--|--|--|--|--|--|--|
| st.15m.bbw_pct100<=0.4 | 30 | 86.70 | 45.40 | 41.20 | 4.88 | 35 | 3.50 | -16.10 | 1.60 |
| st.1h.ribbon_w>=3.719 | 33 | 72.70 | 45.60 | 27.10 | 15.63 | 28.20 | -1.40 | 2.00 | -0.70 |
| evt.failbrk_high.within60.ict_against | 31 | 71 | 45.70 | 25.30 | 1.79 | 21.30 | 11.50 | 0.30 | 8.10 |

## 8. Book x session (live cells first; n_in >= 30 in L6M): five most lowering and three most raising

### KB|asia (live lots 2)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.es_nq_open30_agree==-1 | 31 | 22.60 | 54.70 | -32.10 | -4.08 | -28.50 | 1.30 | 1.60 | -33.93 | 5.01 |
| st.1m.st10_3_age<=1 | 30 | 26.70 | 54.10 | -27.40 | -2.96 | -23.40 | 6.10 | 4.90 | -28.98 | 4.32 |
| st.15m.ribbon_w<=0.7542 | 57 | 35.10 | 55 | -19.90 | -2.72 | -20.40 | -0.50 | 1.90 | -18.79 | 5.47 |
| st.1h.range_pos60<=-0.2152 | 98 | 38.80 | 57 | -18.20 | -3.46 | -17.90 | 0.60 | -7.10 | -14.33 | 7.82 |
| st.1m.st10_3_age<=7 | 120 | 40.80 | 57.70 | -16.80 | -3.00 | -19.40 | -3.70 | 3.90 | -11.55 | 8.54 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| aft.pooled_winner_within10 | 37 | 83.80 | 47.70 | 36.10 | 6.33 | 35.10 | -5.60 | 2.60 | 40.13 | -3.47 |
| st.es_nq_open30_agree==1 | 257 | 54.90 | 21.90 | 33 | 4.26 | 27.10 | -1.60 | 2.70 | 5.27 | -34.78 |
| px.ext.15m.ema20>=2 | 49 | 73.50 | 47.90 | 25.60 | 3.32 | 22.40 | 5.30 | 14.30 | 27.65 | -3.17 |

### KB|london (live lots 2)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| bk.imb10_run>=3 | 32 | 40.60 | 60.40 | -19.80 | -2.30 | -16.70 | -0.10 | -5.10 | -12.09 | 12.42 |
| st.1m.swing_run>=4 | 34 | 41.20 | 60.50 | -19.30 | -2.15 | -18.10 | 4.60 | -5.20 | -7.93 | 11.96 |
| st.ret_RTY_15m>=14.65 | 46 | 43.50 | 61.20 | -17.70 | -3.15 | -16.80 | 1.00 | -1.40 | -8.64 | 13.40 |
| st.1m.er20>=0.3378 | 74 | 45.90 | 63.10 | -17.20 | -3.44 | -18.90 | 2.50 | -2.40 | -5.23 | 15.68 |
| st.5m.swing_run<=-1 | 90 | 47.80 | 63.90 | -16.10 | -2.40 | -13.50 | -5.20 | -15.10 | -3.09 | 16.67 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.1h.ribbon_w>=2.608 | 63 | 71.40 | 52.60 | 18.80 | 2.19 | 19.70 | -5.80 | -8.10 | 25.18 | 3.13 |
| st.15m.adx14>=43.19 | 30 | 73.30 | 55.40 | 17.90 | 1.66 | 19.40 | 10.70 | 22.80 | 27.49 | 6.36 |
| st.sig_vol60<=66 | 35 | 71.40 | 55.30 | 16.20 | 2.08 | 10.10 | 9.50 | 26.30 | 27.69 | 5.79 |

### KB|nyam (live lots 2)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.1m.don20_w<=3.229 | 34 | 26.50 | 49.30 | -22.80 | -3.33 | -19.50 | -6.60 | 17.30 | -27.32 | 0.50 |
| st.1h.chop14>=58.42 | 36 | 27.80 | 49.30 | -21.50 | -3.48 | -18.10 | -1.80 | -3.30 | -26.28 | 0.55 |
| st.15m.ribbon_w<=0.4227 | 42 | 28.60 | 49.60 | -21 | -2.72 | -14.80 | -6.80 | -2.60 | -26.68 | 1.06 |
| st.prev_rng_atrd>=1.697 | 42 | 28.60 | 49.60 | -21 | -2.93 | -19.90 | -11.70 | -1.50 | -26.68 | 1.06 |
| st.rv30_ann>=46.11 | 55 | 30.90 | 50 | -19.10 | -2.76 | -15.20 | 0.10 | 2.10 | -23.85 | 1.67 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.1h.adx14<=15.02 | 34 | 70.60 | 45.10 | 25.50 | 3.26 | 22.20 | 8.10 | 0.20 | 26.20 | -4.60 |
| st.prev_close_loc<=-0.4225 | 30 | 66.70 | 45.70 | 21 | 3.11 | 22.90 | 4.30 | -11.80 | 20.54 | -3.79 |
| st.1m.chop14<=34.86 | 44 | 65.90 | 45 | 21 | 2.75 | 17.10 | 18.80 | -16.30 | 20.83 | -4.80 |

### KB|nypm (live lots 2)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.5m.hma_slope>=0.3501 | 30 | 30 | 48.30 | -18.30 | -1.73 | -12.40 | 5.60 | 4.30 | -11.27 | 4.72 |
| st.15m.chop14<=39.91 | 53 | 32.10 | 50 | -17.90 | -3.08 | -16.20 | 1.70 | 5.60 | -8.31 | 5.88 |
| st.vix_chg5<=-1.2 | 38 | 31.60 | 48.70 | -17.20 | -1.80 | -15.80 | -2.80 | -2.10 | 0.09 | 3.18 |
| st.15m.don20_w>=5.908 | 96 | 36.50 | 52.50 | -16.10 | -2.73 | -15.40 | -4.20 | -1.10 | -7.08 | 9.42 |
| px.struct.1h.with | 64 | 34.40 | 50.30 | -15.90 | -3.12 | -12.80 | 8.20 | -0.70 | -9.77 | 7.33 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.ret_RTY_15m>=30.98 | 44 | 63.60 | 41.90 | 21.80 | 3.38 | 23 | 0.00 | 28.30 | 15.75 | -0.34 |
| st.sig_vel300>=22.5 | 131 | 55 | 34.60 | 20.30 | 3.73 | 20.60 | 7.40 | 14.60 | 9.93 | -6.46 |
| bk.sweep_against10>=1 | 180 | 50.60 | 30.90 | 19.60 | 2.94 | 18.50 | 0.10 | 3.10 | 6.25 | -9.01 |

### PE|asia (live lots 7)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.sig_rv_5m>=24.04 | 33 | 36.40 | 55.10 | -18.70 | -1.73 | -16.20 | 3.00 | -3.50 | -17.25 | 5.65 |
| st.1m.swing_run>=4 | 50 | 38 | 56 | -18 | -2.78 | -16.10 | -9.30 | -11.80 | -15.27 | 6.70 |
| st.1m.hma_slope<=-0.2194 | 59 | 39 | 56.30 | -17.40 | -1.90 | -15.70 | -8.70 | -6.70 | -14.08 | 7.17 |
| evt.rthgap_abs>=200 | 49 | 38.80 | 55.40 | -16.60 | -1.85 | -15.70 | -0.70 | -25.60 | -14.33 | 5.97 |
| aft.engine6_loser_within30 | 100 | 43 | 57.70 | -14.70 | -2.88 | -14.10 | -4.70 | 22 | -9.22 | 8.87 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| vol.r15m_vs_med20d<=0.7 | 53 | 71.70 | 49.60 | 22.10 | 4.06 | 21.80 | -1.30 | 3.80 | 26.00 | -1.05 |
| stk.same_lots_live>=6 | 74 | 68.90 | 48.60 | 20.30 | 4.13 | 20.50 | 0.20 | -3.10 | 22.15 | -2.16 |
| st.1m.don20_w<=3.229 | 34 | 70.60 | 51.20 | 19.40 | 2.41 | 18.40 | 0.60 | -1.40 | 24.17 | 0.92 |

### PE|london (live lots 7)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.sig_imb10_s<=-0.1171 | 45 | 37.80 | 58 | -20.20 | -3.87 | -20.50 | 2.70 | -15.90 | -15.54 | 9.40 |
| st.1d.sg_st==1 | 101 | 43.60 | 62.50 | -18.90 | -3.45 | -17 | 6.60 | 6.10 | -7.62 | 14.38 |
| st.1d.st10_3_dir==1 | 101 | 43.60 | 62.50 | -18.90 | -3.45 | -17 | 6.60 | 6.10 | -7.62 | 14.38 |
| st.5m.hma_slope<=-0.001963 | 45 | 40 | 57.40 | -17.40 | -2.45 | -15.50 | -2.20 | -15.20 | -10.80 | 8.19 |
| st.days_since_trend<=1 | 69 | 42 | 59.20 | -17.20 | -2.65 | -17.90 | -4.40 | 4.00 | -10.39 | 11.01 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| vol.spike1m_vs_sessmed>=2 | 35 | 71.40 | 50.30 | 21.20 | 2.34 | 20 | -0.80 | 12 | 25.18 | 0.09 |
| st.rs_nq_es_15m<=-0.5707 | 47 | 70.20 | 49.40 | 20.80 | 2.61 | 21.40 | -0.00 | 6.30 | 25.68 | -1.44 |
| st.1m.rng_exp1>=2.059 | 34 | 70.60 | 50.80 | 19.80 | 2.07 | 20.80 | -1.30 | 2.40 | 24.17 | 0.72 |

### PE|nyam (live lots 7)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.open_drive5<=-0.1444 | 39 | 25.60 | 48.60 | -23 | -3.49 | -21.10 | -6.10 | -1.10 | -30.22 | 0.00 |
| st.sig_vel30<=-3.6 | 62 | 29 | 51 | -22 | -2.91 | -20.80 | -0.00 | 10.10 | -26.12 | 2.91 |
| xm.es_minus_nq15s<=-1.5 | 32 | 28.10 | 49.80 | -21.70 | -2.45 | -20.60 | 1.40 | 2.30 | -23.97 | 1.04 |
| xm.es30s<=-1 | 60 | 30 | 51.70 | -21.70 | -3.19 | -19.70 | -0.10 | 5.80 | -24.95 | 3.84 |
| evt.sweep_high.within5 | 37 | 29.70 | 49.20 | -19.50 | -2.58 | -19.60 | 2.70 | -0.10 | -21.86 | 0.11 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.sig_es_nq_div5>=0.6062 | 30 | 66.70 | 45.30 | 21.30 | 2.81 | 15 | 5.60 | -2.00 | 19.42 | -4.22 |
| st.rv1m_vs_med20d<=1.252 | 35 | 65.70 | 45.10 | 20.60 | 2.51 | 16.70 | 9.50 | -3.20 | 19.49 | -4.60 |
| st.1h.ribbon_w<=0.5002 | 42 | 64.30 | 44.80 | 19.40 | 2.94 | 21 | -1.00 | 1.80 | 16.54 | -4.74 |

### SM|asia (live lots 4)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.1h.rng_exp1<=0.8902 | 62 | 45.20 | 67.60 | -22.50 | -2.23 | -15.90 | 3.00 | -5.60 | -5.57 | 20.61 |
| st.rv30m_vs_med20d<=1.063 | 63 | 46 | 66.70 | -20.60 | -1.81 | -10.80 | -10.80 | 3.10 | -4.53 | 19.42 |
| st.sig_absorb10_s<=3.667 | 66 | 47 | 66.70 | -19.70 | -1.88 | -13.10 | 7.80 | -3.70 | -3.44 | 19.42 |
| st.rv5m_vs_med20d<=1.147 | 52 | 44.20 | 63.60 | -19.40 | -2.03 | -10.40 | -4.00 | 2.30 | -6.50 | 15.75 |
| px.ext.5m.ema200>=3 | 30 | 40 | 59.10 | -19.10 | -1.98 | -15.80 | 5.90 | 19.80 | -12.85 | 11.22 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.prev_close_loc<=-0.2896 | 33 | 72.70 | 42.90 | 29.90 | 3.44 | 24.40 | 2.10 | 2.60 | 26.76 | -8.37 |
| st.sig_delta60_s<=-1 | 37 | 70.30 | 42.40 | 27.90 | 2.72 | 21.90 | 0.30 | -2.00 | 23.78 | -8.89 |
| st.1h.macd_hist<=-0.1108 | 48 | 64.60 | 41.70 | 22.90 | 3.43 | 22.10 | -9.50 | -1.70 | 16.90 | -9.50 |

### SM|london (live lots 4)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.1d.sg_c200==-1 | 43 | 37.20 | 65.90 | -28.60 | -2.49 | -25 | 2.60 | -3.50 | -16.23 | 21.25 |
| st.5m.rsi14<=39.39 | 41 | 36.60 | 65.10 | -28.50 | -2.64 | -24.80 | 4.20 | -7.10 | -16.98 | 20.23 |
| st.1h.rng_exp1<=0.8902 | 46 | 39.10 | 65.80 | -26.70 | -2.79 | -17.50 | -7.80 | 3.50 | -13.90 | 21.39 |
| stk.opp_lots_live>=2 | 47 | 40.40 | 64.90 | -24.40 | -2.43 | -22.70 | 10.60 | 1.00 | -9.88 | 17.24 |
| void.gap_ahead_100pctTD | 45 | 40 | 64.10 | -24.10 | -2.18 | -22.10 | 9 | -7.90 | -10.29 | 16.32 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.5m.rsi14>=61.1 | 33 | 69.70 | 39.20 | 30.50 | 2.42 | 24.60 | -2.80 | 3.90 | 23.09 | -11.54 |
| st.1d.sg_c200==1 | 41 | 65.90 | 37.20 | 28.60 | 2.49 | 25 | -2.60 | 3.50 | 21.25 | -16.23 |
| st.1m.rsi14>=61.82 | 32 | 68.80 | 40.40 | 28.40 | 2.39 | 24.60 | -7.40 | 2.00 | 21.94 | -10.17 |

### HM|asia (live lots 4)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.5m.rng_exp1<=0.4748 | 63 | 36.50 | 62.20 | -25.70 | -4.39 | -22 | 2.30 | -2.20 | -16.61 | 14.25 |
| st.5m.st10_3_dist<=-0.9631 | 38 | 39.50 | 58.80 | -19.30 | -1.98 | -13.80 | 0.60 | 1.60 | -13.48 | 10.22 |
| st.1h.chop14>=53.15 | 49 | 40.80 | 59.50 | -18.70 | -1.90 | -20.50 | -0.50 | 9.30 | -11.86 | 11.08 |
| px.loc.DEAL1H.discount | 42 | 40.50 | 59 | -18.50 | -2.30 | -14.80 | 0.10 | -5.40 | -12.27 | 10.42 |
| st.5m.range_pos60<=-0.07456 | 35 | 40 | 58.50 | -18.50 | -2.64 | -14.40 | 3.60 | 4.40 | -12.85 | 9.80 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.15m.don20_w>=5.908 | 46 | 76.10 | 51.60 | 24.40 | 3.99 | 24.40 | 5 | -6.60 | 31.57 | 1.38 |
| px.loc.PDR.outside | 54 | 74.10 | 51.20 | 22.90 | 3.20 | 24.80 | 3.00 | 13.40 | 28.39 | 1.04 |
| px.late.atDayExtreme20_run100 | 33 | 75.80 | 53.10 | 22.70 | 2.19 | 22.20 | 5.30 | -49 | 30.42 | 3.28 |

### HM|nyam (live lots 2)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.gap_atrd>=0.2374 | 54 | 40.70 | 61.50 | -20.80 | -3.18 | -18.40 | 1.40 | 6.30 | -9.40 | 14.01 |
| aft.book_loser_within30 | 45 | 40 | 60.70 | -20.70 | -3.16 | -15.90 | 3.60 | -5.80 | -11.61 | 13.39 |
| st.4h.chop14<=39.02 | 43 | 41.90 | 60 | -18.10 | -2.03 | -15.90 | 4.70 | 1.20 | -8.41 | 12.34 |
| st.15m.ich_cloud_sgn==0 | 38 | 42.10 | 59.50 | -17.40 | -1.90 | -15.90 | -2.80 | -3.50 | -7.83 | 11.66 |
| st.1m.adx14<=15.24 | 38 | 42.10 | 59.50 | -17.40 | -2.16 | -15.40 | 5.80 | 8.20 | -9.05 | 11.92 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.5m.macd_hist>=0.3864 | 30 | 76.70 | 53.40 | 23.30 | 3.02 | 26.70 | -0.60 | 11.10 | 31.52 | 4.74 |
| st.1m.adx14>=32.39 | 49 | 73.50 | 51.70 | 21.70 | 3.10 | 14.10 | -3.10 | 11.70 | 28.79 | 2.58 |
| st.15m.hma_slope<=-0.1192 | 32 | 75 | 53.40 | 21.60 | 2.56 | 22.60 | -4.40 | 6.20 | 29.51 | 4.80 |

### MV|london (live lots 2)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| px.late.atDayExtreme20_run100 | 46 | 32.60 | 59 | -26.40 | -3.89 | -28.30 | 1.90 | -7.50 | -21.79 | 10.83 |
| st.15m.bos_state==1 | 183 | 49.20 | 71.70 | -22.60 | -3.21 | -23.40 | -1.50 | 21.50 | -1.07 | 25.56 |
| st.1d.st10_3_dir==1 | 101 | 43.60 | 61.70 | -18.20 | -3.30 | -17 | 1.60 | 1.20 | -7.72 | 13.74 |
| st.1d.sg_st==1 | 101 | 43.60 | 61.70 | -18.20 | -3.30 | -17 | 1.60 | 1.20 | -7.72 | 13.74 |
| st.idx3_agree_1h>=3 | 194 | 51 | 68.60 | -17.50 | -2.38 | -11.90 | -1.40 | -10.70 | 0.92 | 22.86 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.15m.bos_state==-1 | 46 | 71.70 | 49.20 | 22.60 | 3.21 | 23.40 | 1.50 | -21.50 | 25.56 | -1.07 |
| st.1m.rsi14>=61.82 | 57 | 70.20 | 48.30 | 21.90 | 3.72 | 21.80 | -3.20 | 20 | 25.11 | -2.63 |
| st.idx3_agree_1h<=1 | 32 | 71.90 | 50.80 | 21.10 | 2.54 | 14.80 | 2.10 | 9.10 | 26.97 | 0.59 |

### MV|nyam (live lots 2)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.f60_vs_med<=0.814 | 33 | 39.40 | 58 | -18.60 | -2.62 | -20.80 | 2.70 | -3.00 | -10.78 | 11.53 |
| st.gap_atrd>=0.5322 | 36 | 36.10 | 54.10 | -18 | -2.18 | -16.10 | -2.40 | 8.60 | -16.47 | 5.87 |
| bk.iceberg_behind10>=100 | 71 | 39.40 | 55.60 | -16.20 | -2.52 | -14.80 | 1.30 | -3.40 | -13.53 | 8.09 |
| bk.sweep_with30>=12 | 222 | 46.80 | 63 | -16.10 | -3.39 | -11.80 | 6.30 | -0.40 | -4.08 | 18.89 |
| tm.block.0900_1000 | 98 | 40.80 | 56.90 | -16.10 | -2.91 | -10.60 | 0.70 | -8 | -11.86 | 9.90 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.1h.ribbon_w<=0.5002 | 30 | 73.30 | 50 | 23.30 | 1.99 | 13.30 | 7.10 | 6.70 | 27.49 | 1.03 |
| st.sig_vel120<=1.75 | 56 | 67.90 | 48.90 | 19 | 3.23 | 13.90 | 3.70 | 3.80 | 22.78 | -0.52 |
| st.sig_rty_move20_atr>=4.959 | 31 | 67.70 | 50.50 | 17.20 | 1.65 | 20.90 | -3.00 | -1.90 | 23.13 | 1.40 |

### PB|asia (live lots 1)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| evt.bigbar3atr.within30 | 57 | 42.10 | 65.30 | -23.20 | -3.33 | -17.20 | -5.40 | -2.20 | -9.51 | 17.72 |
| void.sandwich_set11_lt15 | 30 | 40 | 62.70 | -22.70 | -2.62 | -26.90 | -15 | 0.80 | -12.85 | 14.80 |
| st.rs_nq_rty_15m<=-4.268 | 34 | 41.20 | 62.90 | -21.70 | -2.41 | -18.60 | 6 | -26.20 | -11.42 | 15.09 |
| px.loc.DEAL4H.discount | 36 | 41.70 | 63 | -21.40 | -2.84 | -17.90 | 0.10 | -23.80 | -10.83 | 15.24 |
| st.1m.atr_ratio>=1.197 | 40 | 42.50 | 63.30 | -20.80 | -3.15 | -15.80 | 4.60 | -12.40 | -8.69 | 15.33 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.15m.squeeze==1 | 35 | 77.10 | 57.10 | 20.10 | 2.82 | 17.90 | -6.50 | 3.40 | 33.39 | 7.82 |
| st.sig_imb10_s>=0.1667 | 63 | 74.60 | 54.90 | 19.70 | 2.91 | 16.20 | -0.50 | -3.70 | 29.03 | 5.42 |
| st.5m.swing_run<=-1 | 69 | 73.90 | 54.50 | 19.40 | 3.18 | 18.10 | -2.60 | -8.60 | 28.19 | 4.95 |

### PB|london (live lots 1)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.rs_nq_es_15m<=-3.331 | 33 | 39.40 | 60.80 | -21.40 | -2.77 | -15.50 | 2.00 | -9.10 | -13.58 | 12.96 |
| st.1m.st10_3_age<=1 | 33 | 39.40 | 60.80 | -21.40 | -1.93 | -19.80 | -7.10 | 1.10 | -13.58 | 12.96 |
| st.vix>=20.03 | 35 | 40 | 60.90 | -20.90 | -2.38 | -19.20 | 3.10 | 12.40 | -12.85 | 13.13 |
| st.sig_vel120<=-5.25 | 149 | 53 | 71.40 | -18.40 | -2.28 | -19.10 | 3.40 | 3.60 | 3.41 | 25.99 |
| px.loc.SESS.mid_third | 71 | 46.50 | 64 | -17.60 | -2.19 | -14.80 | 0.40 | -15.50 | -5.01 | 17.19 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.1h.bbw_pct100<=0.22 | 34 | 70.60 | 54.10 | 16.40 | 2.02 | 21.40 | 5.90 | 3.30 | 24.17 | 4.95 |
| st.15m.bbw_pct100>=0.83 | 33 | 69.70 | 54.40 | 15.30 | 2.25 | 18.40 | 2.50 | -11.40 | 24.11 | 5.09 |
| st.1m.st10_3_age>=47 | 36 | 69.40 | 54.20 | 15.30 | 1.89 | 11.80 | 10.30 | -8.90 | 22.78 | 5.03 |

### PB|nyam (live lots 1)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| evt.failbrk_low.within60.ict_against | 33 | 33.30 | 55.30 | -22 | -2.90 | -18.50 | 2.70 | 8.20 | -15.91 | 8.51 |
| evt.failbrk_low.within60 | 39 | 35.90 | 55.50 | -19.60 | -2.68 | -16.40 | 3.20 | 8.80 | -13.57 | 8.82 |
| px.chase.book>=3 | 55 | 38.20 | 56.60 | -18.40 | -2.23 | -15 | 18 | 7.40 | -13.12 | 10.82 |
| aft.pooled_winner_within10 | 73 | 39.70 | 58.10 | -18.40 | -3.48 | -14.40 | 2.40 | 4.00 | -10.59 | 12.49 |
| evt.rthgap_abs>=40 | 168 | 48.20 | 64.70 | -16.50 | -2.51 | -14.80 | 3.30 | 8.90 | 1.23 | 17.05 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.f30_vs_med>=1.393 | 57 | 64.90 | 45.20 | 19.70 | 2.83 | 17.10 | -2.20 | 8.90 | 17.30 | -0.49 |
| st.sig_er120>=0.2218 | 34 | 67.60 | 49.20 | 18.40 | 2.40 | 14.60 | -10.90 | 4.70 | 20.61 | 2.00 |
| px.loc.OR30.mid_third | 46 | 65.20 | 46.80 | 18.40 | 2.70 | 17 | 3.70 | -1.80 | 19.21 | 0.37 |

### PB|nypm (live lots 1)
lowering:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| st.1m.swing_run>=2 | 54 | 27.80 | 55 | -27.30 | -3.56 | -26 | 0.10 | -0.90 | -13.80 | 11.04 |
| st.prev_ret_rth>=0.3548 | 32 | 25 | 51.10 | -26.10 | -3.13 | -26.40 | -10.30 | 9 | -17.71 | 7.83 |
| st.5m.st10_3_age>=40 | 53 | 32.10 | 52.70 | -20.70 | -3.40 | -18.80 | -4.40 | -6.10 | -10.56 | 9.26 |
| px.ext.5m.ema200>=1 | 124 | 41.10 | 61.50 | -20.40 | -2.19 | -19 | -3.50 | 9.80 | -3.08 | 21.55 |
| st.1h.bos_state==1 | 116 | 40.50 | 59.60 | -19.10 | -2.22 | -18 | -2.30 | 17.60 | -3.03 | 17.23 |

raising:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | dP_HOLD | dP_PRE | dP_X | ptsM_N_in | ptsM_N_out |
|--|--|--|--|--|--|--|--|--|--|--|
| px.loc.PDR.sidedloc<=0.2 | 30 | 66.70 | 41.40 | 25.30 | 3.08 | 23.30 | -2.50 | -18.90 | 25.19 | -2.23 |
| bk.cons_ahead10>=10 | 30 | 66.70 | 41.40 | 25.30 | 2.32 | 25.10 | 12.90 | 12.60 | 25.86 | -2.39 |
| st.idx3_agree_15m<=-1 | 108 | 52.80 | 32.70 | 20.10 | 2.45 | 20.20 | 7.70 | 0.30 | 9.71 | -10.72 |

## 9. Both edges of every continuous state (pooled, L6M dP in pp, then PRE u X' dP): low-tail cuts and high-tail cuts

| state | family | low tail  L6M/SEL dP pp | high tail  L6M/SEL dP pp |
|--|--|--|--|
| aft._dayR | AFT |  | >=66.3: -3.6/+3.9 (n935) |
| px.loc.DEAL1H.sidedloc | PX | <=0.2: -3.3/+0.2 (n622) | >=0.8: +0.5/-0.1 (n4100) |
| px.loc.DEAL4H.sidedloc | PX | <=0.2: -1.1/+0.0 (n1078) | >=0.8: -1.0/+0.8 (n3707) |
| px.loc.ON.sidedloc | PX | <=0.2: -3.1/-6.4 (n374) | >=0.8: +0.0/-0.1 (n3839) |
| px.loc.OR30.sidedloc | PX | <=0.2: -4.6/-0.7 (n727) | >=0.8: +3.7/+0.6 (n3502) |
| px.loc.PDR.sidedloc | PX | <=0.2: -1.1/-0.8 (n1548) | >=0.8: -0.5/-0.3 (n4121) |
| px.loc.SESS.sidedloc | PX | <=0.2: -0.3/-7.2 (n79) | >=0.8: +1.9/-0.7 (n4935) |
| st.15m.adx14 | ST | <=15.7: +1.0/-0.8 (n865); <=19.8: +0.1/-1.6 (n2283) | >=34: +0.2/+0.7 (n2715); >=43.2: -3.1/+1.3 (n1087) |
| st.15m.atr_ratio | ST | <=0.692: +4.3/+3.4 (n822); <=0.907: +3.3/+2.5 (n2755) | >=1.86: -6.8/-4.2 (n1979); >=2.28: -9.7/-3.0 (n923) |
| st.15m.bbw_pct100 | ST | <=0.2: +0.1/+1.7 (n1100); <=0.4: +5.9/+1.8 (n2716) | >=0.83: -2.0/-0.9 (n2708); >=0.97: -0.1/+4.1 (n1005) |
| st.15m.bos_state | ST |  |  |
| st.15m.chop14 | ST | <=33.3: +2.7/+3.3 (n868); <=39.9: +3.1/+2.6 (n2368) | >=54: +0.6/-0.2 (n2568); >=59.6: +2.7/-2.3 (n1019) |
| st.15m.don20_w | ST | <=3.35: +2.9/+1.0 (n1083); <=3.98: +3.0/+1.7 (n2517) | >=5.91: -3.0/-0.3 (n2292); >=7.13: -2.8/+1.2 (n814) |
| st.15m.er20 | ST | <=0.0408: +2.6/+1.9 (n1009); <=0.105: +2.5/+0.6 (n2475) | >=0.373: +0.7/+1.5 (n2674); >=0.528: +1.7/+4.0 (n996) |
| st.15m.hma_slope | ST | <=-0.119: -2.0/-0.6 (n948); <=0.0506: -1.6/-0.4 (n2518) | >=0.407: +3.8/+0.9 (n2229); >=0.595: +2.4/+0.4 (n830) |
| st.15m.ich_cloud_sgn | ST |  |  |
| st.15m.macd_hist | ST | <=-0.116: -0.6/+1.2 (n1020); <=0.0147: +0.5/+0.2 (n2485) | >=0.283: +2.1/+0.8 (n2433); >=0.415: +1.1/+1.3 (n860) |
| st.15m.range_pos60 | ST | <=-0.237: -0.1/+0.7 (n975); <=-0.0426: -0.7/+1.3 (n2417) | >=0.392: +1.0/-0.2 (n2381); >=0.455: +1.1/+0.5 (n969) |
| st.15m.ribbon_w | ST | <=0.423: -3.7/-0.5 (n926); <=0.754: -1.3/-0.7 (n2234) | >=2.38: -0.9/+2.2 (n2546); >=3.54: +0.2/+2.1 (n817) |
| st.15m.rng_exp1 | ST | <=0.557: +1.4/+1.6 (n837); <=0.857: +2.7/+2.4 (n2428) | >=2.25: -2.4/-0.7 (n2405); >=3.51: -5.1/+1.9 (n1019) |
| st.15m.rsi14 | ST | <=30.9: +1.8/+2.8 (n1148); <=40: +3.5/+0.5 (n2588) | >=60.2: -1.4/-0.8 (n2321); >=69.3: -1.9/+2.1 (n844) |
| st.15m.squeeze | ST |  |  |
| st.15m.st10_3_age | ST | <=2: +1.4/+0.7 (n1162); <=6: +1.7/+1.9 (n2333) | >=37: -0.0/+1.3 (n2602); >=68: -2.0/+3.0 (n1003) |
| st.15m.st10_3_dist | ST | <=-1.89: -4.8/+0.5 (n979); <=-0.671: -0.1/+0.2 (n2450) | >=3.08: -0.5/-1.1 (n2304); >=3.52: -1.4/+0.2 (n896) |
| st.15m.swing_run | ST | <=-3: -3.0/+1.5 (n1335); <=-1: +1.8/-0.3 (n4126) | >=2: -1.1/-0.7 (n3554); >=4: -4.0/+1.4 (n1254) |
| st.1d.adx14 | ST | <=16.9: +2.4/-5.6 (n2720); <=19.9: +2.8/-1.8 (n5729) |  |
| st.1d.atr_ratio | ST | <=0.825: +4.3/-0.1 (n959); <=0.936: +2.4/-0.4 (n2651) | >=1.19: +1.1/+1.7 (n3418) |
| st.1d.chop14 | ST | <=35.7: +8.1/-3.3 (n207); <=40.6: +4.8/+0.9 (n653) | >=56: +1.6/-1.1 (n2953); >=60.4: -1.1/-2.4 (n1466) |
| st.1d.er20 | ST | <=0.0396: +0.9/-2.8 (n1832); <=0.0979: +0.7/-1.8 (n4529) | >=0.355: +1.4/+1.4 (n830); >=0.463: -1.6/-1.8 (n509) |
| st.1d.sg_c200 | ST |  |  |
| st.1d.sg_st | ST |  |  |
| st.1d.squeeze | ST |  |  |
| st.1d.st10_3_dir | ST |  |  |
| st.1h.adx14 | ST | <=15: +10.0/+5.7 (n722); <=19.6: -0.7/+1.6 (n2386) | >=35.3: +0.4/+0.1 (n2707); >=46.2: +2.7/-1.0 (n857) |
| st.1h.atr_ratio | ST | <=0.809: -6.8/+2.0 (n1204); <=0.91: +0.9/+1.8 (n2633) | >=1.18: -1.8/-0.7 (n2894); >=1.36: -2.9/-0.1 (n1303) |
| st.1h.bbw_pct100 | ST | <=0.07: +1.0/-1.0 (n668); <=0.22: +3.6/-1.6 (n2305) | >=0.75: +1.7/+1.7 (n2824); >=0.92: -0.7/+3.7 (n1207) |
| st.1h.bos_state | ST |  |  |
| st.1h.chop14 | ST | <=32.5: -6.0/+3.1 (n844); <=39.3: -4.0/+1.4 (n2442) | >=53.1: -2.0/-0.9 (n2273); >=58.4: -2.8/-0.9 (n1009) |
| st.1h.don20_w | ST | <=3.29: +4.9/-5.2 (n669); <=3.87: +1.1/-1.8 (n2011) | >=6.11: -0.2/+0.7 (n2336); >=7.43: -1.7/+0.5 (n808) |
| st.1h.er20 | ST | <=0.0458: +2.2/+0.1 (n1009); <=0.111: +1.9/-1.1 (n2442) | >=0.4: -0.1/+1.3 (n2353); >=0.555: -6.0/+3.1 (n889) |
| st.1h.hma_slope | ST | <=-0.314: -1.8/-2.0 (n943); <=-0.125: +1.7/-1.1 (n2370) | >=0.289: -1.2/-0.2 (n2513); >=0.495: -1.7/+0.9 (n947) |
| st.1h.ich_cloud_sgn | ST |  |  |
| st.1h.macd_hist | ST | <=-0.264: -3.6/-1.0 (n917); <=-0.111: -1.3/+0.2 (n2365) | >=0.215: -2.2/-1.0 (n2395); >=0.364: -1.0/-1.3 (n826) |
| st.1h.range_pos60 | ST | <=-0.364: -0.4/+0.3 (n985); <=-0.215: -2.2/-1.2 (n2385) | >=0.356: +0.3/+2.5 (n2449); >=0.462: -2.1/+3.4 (n874) |
| st.1h.ribbon_w | ST | <=0.5: +10.5/+2.2 (n781); <=0.851: +2.3/+0.6 (n2352) | >=2.61: +1.0/+0.3 (n1901); >=3.72: +7.8/-0.2 (n499) |
| st.1h.rng_exp1 | ST | <=0.6: -3.1/-0.8 (n805); <=0.89: -2.2/+1.7 (n2343) | >=2.39: -2.6/-1.8 (n2462); >=3.42: -1.3/-1.0 (n1046) |
| st.1h.rsi14 | ST | <=31.4: +4.1/+4.1 (n1163); <=40.4: +1.6/+0.5 (n2793) | >=60.2: -0.4/+1.3 (n2256); >=68.9: -2.2/+1.4 (n739) |
| st.1h.squeeze | ST |  |  |
| st.1h.st10_3_age | ST | <=2: -0.4/-1.5 (n1229); <=8: -3.5/-1.4 (n2627) | >=42: +0.6/+1.0 (n2110); >=68: +3.0/-0.7 (n676) |
| st.1h.st10_3_dist | ST | <=-2.7: -0.3/+2.6 (n870); <=-1.89: -0.0/+1.2 (n2352) | >=2.99: +1.1/+1.2 (n2578); >=3.51: -4.2/-1.1 (n942) |
| st.1h.swing_run | ST | <=-3: -0.1/+0.7 (n1667); <=-2: -1.5/-0.0 (n3163) | >=2: -2.3/+2.1 (n2704); >=3: -4.6/-0.0 (n1449) |
| st.1m.adx14 | ST | <=15.2: -3.6/+1.8 (n1198); <=18.9: -2.7/+1.1 (n2699) | >=32.4: +3.3/-0.6 (n2040); >=40.6: +6.4/-1.4 (n783) |
| st.1m.atr_ratio | ST | <=0.837: +1.1/-1.0 (n1028); <=0.918: +1.7/+0.0 (n2513) | >=1.2: -0.2/+1.7 (n2476); >=1.62: -0.3/+1.4 (n1103) |
| st.1m.bbw_pct100 | ST | <=0.12: -2.0/-1.9 (n1037); <=0.28: +0.5/-0.4 (n2428) | >=0.79: +0.5/-0.1 (n2577); >=0.95: +0.7/-0.9 (n1080) |
| st.1m.bos_state | ST |  |  |
| st.1m.chop14 | ST | <=34.9: +2.9/-0.3 (n865); <=41.9: -0.6/-0.3 (n2213) | >=55.4: -3.2/-0.8 (n2580); >=60.5: -0.9/-0.7 (n1039) |
| st.1m.don20_w | ST | <=3.23: -2.3/-0.7 (n1008); <=3.73: -0.6/-0.2 (n2462) | >=5.5: +0.4/+0.2 (n2288); >=6.64: -0.6/+1.1 (n858) |
| st.1m.er20 | ST | <=0.04: +0.6/+1.8 (n996); <=0.101: -0.3/+1.3 (n2488) | >=0.338: +0.3/+0.0 (n2267); >=0.469: +0.9/+2.0 (n876) |
| st.1m.hma_slope | ST | <=-0.219: -0.4/-1.8 (n969); <=-0.0194: +0.1/-1.3 (n2447) | >=0.375: +0.5/-0.2 (n2346); >=0.548: +0.2/-0.6 (n899) |
| st.1m.ich_cloud_sgn | ST |  |  |
| st.1m.macd_hist | ST | <=-0.236: -0.9/-0.9 (n903); <=-0.0992: +0.3/-1.3 (n2371) | >=0.204: -1.2/+0.2 (n2335); >=0.331: +0.6/+0.0 (n965) |
| st.1m.range_pos60 | ST | <=-0.0347: +0.1/+0.1 (n941); <=0.163: +0.5/-0.5 (n2398) | >=0.43: -1.0/-1.1 (n2511); >=0.472: -3.0/-2.7 (n1025) |
| st.1m.ribbon_w | ST | <=0.511: -0.9/+1.1 (n1049); <=0.913: -1.9/+1.3 (n2561) | >=2.31: +3.0/-1.3 (n2287); >=3.04: +5.3/-0.7 (n876) |
| st.1m.rng_exp1 | ST | <=0.7: +0.6/-0.6 (n1066); <=0.949: +1.3/-1.3 (n2576) | >=2.06: +1.3/+1.6 (n2400); >=3.33: +1.6/+1.0 (n1022) |
| st.1m.rsi14 | ST | <=31.7: +2.6/-0.5 (n851); <=38.4: +2.3/+0.5 (n2315) | >=61.8: -0.8/-1.2 (n2282); >=68.2: +2.3/-0.3 (n879) |
| st.1m.squeeze | ST |  |  |
| st.1m.st10_3_age | ST | <=1: -2.1/+0.8 (n1098); <=7: -1.3/+0.6 (n2673) | >=47: +7.1/-2.0 (n2259); >=77: +10.4/-2.6 (n860) |
| st.1m.st10_3_dist | ST | <=-1.21: -0.6/-2.2 (n981); <=0.198: -0.2/+0.9 (n2522) | >=3.25: -0.8/+0.2 (n2330); >=3.64: +0.5/-0.8 (n964) |
| st.1m.swing_run | ST | <=-3: +3.5/+1.5 (n1231); <=-1: +2.6/+0.2 (n4295) | >=2: -2.0/-1.0 (n3465); >=4: -2.3/-1.4 (n1486) |
| st.4h.adx14 | ST | <=15.1: +1.3/+2.7 (n1144); <=19.6: -0.3/+1.4 (n3074) | >=34.4: -0.6/+1.6 (n1555); >=43.9: +7.9/-0.3 (n259) |
| st.4h.atr_ratio | ST | <=0.788: -5.0/+0.3 (n911); <=0.91: -5.4/-0.5 (n2239) | >=1.14: +1.2/+1.5 (n3886); >=1.36: -2.8/+0.8 (n967) |
| st.4h.chop14 | ST | <=32.3: +1.5/-1.7 (n469); <=39: +0.6/-2.4 (n1846) | >=53.3: +0.5/+2.1 (n2372); >=58.6: +2.0/+2.3 (n660) |
| st.4h.er20 | ST | <=0.0492: -0.7/-1.7 (n801); <=0.122: -1.3/+0.4 (n2617) | >=0.406: +1.5/-1.9 (n1606); >=0.545: -1.9/-0.9 (n356) |
| st.4h.sg_c200 | ST |  |  |
| st.4h.sg_st | ST |  |  |
| st.4h.squeeze | ST |  |  |
| st.4h.st10_3_dir | ST |  |  |
| st.5m.adx14 | ST | <=15.4: -1.1/-2.2 (n954); <=19.7: -1.7/-2.0 (n2503) | >=34.8: +3.7/+3.1 (n2321); >=44.2: +3.9/+4.1 (n974) |
| st.5m.atr_ratio | ST | <=0.68: -6.2/-0.1 (n691); <=0.863: -4.2/-2.0 (n2283) | >=1.6: -1.0/+1.8 (n2384); >=2.2: -1.6/+1.4 (n1013) |
| st.5m.bbw_pct100 | ST | <=0.13: -5.0/+1.9 (n903); <=0.44: -3.3/+0.5 (n2594) | >=0.94: +0.1/+0.0 (n2143); >=1: -0.6/-0.6 (n1302) |
| st.5m.bos_state | ST |  |  |
| st.5m.chop14 | ST | <=33.8: +1.3/-0.9 (n846); <=39.8: +2.7/-0.6 (n2260) | >=53.8: -3.1/+0.5 (n2599); >=59.7: -4.9/+1.6 (n1094) |
| st.5m.don20_w | ST | <=3.39: -2.1/-1.7 (n1026); <=4.03: -4.6/-1.6 (n2595) | >=5.97: +4.0/-0.0 (n2304); >=7.06: +1.5/+0.3 (n911) |
| st.5m.er20 | ST | <=0.0514: -4.3/-0.3 (n952); <=0.129: -1.7/+0.5 (n2538) | >=0.386: +4.3/+1.1 (n2372); >=0.514: +8.2/+0.9 (n862) |
| st.5m.hma_slope | ST | <=-0.166: -1.2/+2.1 (n1008); <=-0.00196: -2.7/+2.2 (n2569) | >=0.35: +1.2/+0.5 (n2406); >=0.527: +1.5/+0.2 (n956) |
| st.5m.ich_cloud_sgn | ST |  |  |
| st.5m.macd_hist | ST | <=-0.152: -2.8/+1.3 (n977); <=-0.0156: -3.3/+1.5 (n2576) | >=0.266: +1.5/-0.2 (n2248); >=0.386: +0.2/+0.9 (n915) |
| st.5m.range_pos60 | ST | <=-0.0746: -1.7/+1.1 (n1000); <=0.114: -2.6/+0.4 (n2408) | >=0.397: +1.7/-1.3 (n2538); >=0.451: -1.3/+0.0 (n1047) |
| st.5m.ribbon_w | ST | <=0.464: -0.8/+0.0 (n890); <=0.804: -1.0/-0.4 (n2342) | >=2.5: +2.0/+1.4 (n2428); >=3.54: +2.5/+3.7 (n807) |
| st.5m.rng_exp1 | ST | <=0.475: -2.7/+2.5 (n676); <=0.859: +1.5/+0.6 (n2431) | >=2.28: -1.1/+0.5 (n2457); >=3.56: -1.5/+0.6 (n1062) |
| st.5m.rsi14 | ST | <=32.3: +1.3/+2.7 (n1039); <=39.4: +3.7/+0.6 (n2604) | >=61.1: +0.5/-0.8 (n2290); >=68: +3.0/-0.3 (n828) |
| st.5m.squeeze | ST |  |  |
| st.5m.st10_3_age | ST | <=3: -1.2/-1.0 (n1105); <=8: +0.8/-0.9 (n2500) | >=40: -1.7/+0.1 (n2785); >=71: -0.2/+2.1 (n1056) |
| st.5m.st10_3_dist | ST | <=-0.963: -0.1/+1.5 (n950); <=1.64: -0.9/+0.5 (n2548) | >=3.02: -0.4/-1.2 (n2393); >=3.4: +1.2/+0.6 (n916) |
| st.5m.swing_run | ST | <=-2: -3.1/-0.6 (n1463); <=-1: -3.5/-0.6 (n2969) | >=3: +5.2/-0.3 (n3064); >=5: +0.4/+0.8 (n1204) |
| st.cal_holiday_adj | ST |  |  |
| st.days_since_trend | DAYT | <=0: -0.2/-3.8 (n1379); <=1: -0.1/-2.9 (n2650) | >=5: +1.9/+2.1 (n5041); >=9: +3.1/+0.9 (n3127) |
| st.es_nq_open30_agree | DAYT |  |  |
| st.f30_vs_med | DAYT | <=0.646: -0.0/-2.1 (n535); <=0.813: -1.1/-2.2 (n1391) | >=1.39: +0.1/+0.4 (n2191); >=1.74: +2.1/-0.7 (n1237) |
| st.f60_vs_med | DAYT | <=0.647: +0.3/-4.9 (n575); <=0.814: +0.5/-2.3 (n1269) | >=1.4: +0.2/+4.2 (n1958); >=1.81: -4.8/+2.0 (n1138) |
| st.gap_atrd | DAYT | <=-0.523: +2.3/+3.3 (n635); <=-0.236: -0.3/+1.4 (n1194) | >=0.237: -3.4/+2.5 (n1092); >=0.532: -4.4/+3.6 (n416) |
| st.idx3_agree_15m | CROSS | <=-3: -0.5/+0.2 (n1558); <=-1: -1.1/+1.1 (n2677) | >=3: +1.4/-0.7 (n5331) |
| st.idx3_agree_1h | CROSS | <=-1: -2.6/+0.7 (n1850); <=1: -1.3/+0.9 (n3284) | >=3: +1.4/-1.0 (n6373) |
| st.idx4_agree_15m | CROSS | <=-4: -0.8/-0.1 (n1173); <=0: -0.8/+0.8 (n2982) | >=4: +1.2/-0.7 (n5115) |
| st.impulse30 | VOLS | <=0.27: +0.3/-0.3 (n1140); <=0.324: -0.7/-0.8 (n2608) | >=0.505: -1.2/+1.7 (n2421); >=0.632: -0.9/+0.8 (n974) |
| st.on_range_atrd | DAYT | <=0.303: -3.9/-6.5 (n521); <=0.386: +0.7/-3.3 (n1537) | >=0.744: +7.1/+5.6 (n2087); >=0.939: +5.3/+6.2 (n1341) |
| st.open_drive30 | DAYT | <=-0.262: +3.0/-2.1 (n794); <=-0.113: +0.5/-1.4 (n1604) | >=0.183: +1.0/+2.8 (n2052); >=0.328: +1.7/+2.9 (n983) |
| st.open_drive5 | DAYT | <=-0.144: +0.1/-0.4 (n881); <=-0.066: +0.2/+0.2 (n1834) | >=0.0854: +2.4/+3.7 (n2198); >=0.164: +4.2/+2.9 (n1044) |
| st.prev_close_loc | DAYT | <=-0.423: +4.5/-1.8 (n765); <=-0.29: +5.1/+0.7 (n1963) | >=0.29: +1.1/-1.3 (n2058); >=0.423: -3.9/-1.9 (n637) |
| st.prev_er_rth | DAYT | <=0.0226: -2.7/+1.6 (n861); <=0.0495: -2.0/+2.6 (n2108) | >=0.184: +3.7/-4.5 (n2413); >=0.277: -0.2/-6.2 (n669) |
| st.prev_ret_rth | DAYT | <=-0.766: +3.4/-1.7 (n942); <=-0.366: +3.8/-0.6 (n2422) | >=0.355: +0.4/-2.5 (n2414); >=0.71: +1.4/-5.7 (n1056) |
| st.prev_rng_atrd | DAYT | <=0.529: -4.9/+0.6 (n670); <=0.733: -2.6/+1.0 (n2077) | >=1.3: +1.3/-2.3 (n3284); >=1.7: -1.6/-2.5 (n1247) |
| st.prev_trend_day | DAYT |  |  |
| st.ret_ES_15m | CROSS | <=-4.07: -0.6/+0.2 (n903); <=0.414: +0.8/-0.2 (n2704) | >=10.6: +0.1/-0.2 (n2056); >=21.6: +0.2/-0.1 (n606) |
| st.ret_RTY_15m | CROSS | <=-11.3: -2.9/+1.3 (n873); <=-1.92: -2.0/+1.2 (n2446) | >=14.7: -0.1/-0.1 (n2029); >=31: +1.5/-0.3 (n661) |
| st.ret_YM_15m | CROSS | <=-6.33: -0.5/+3.2 (n988); <=-1.05: -0.9/+1.0 (n2587) | >=8.84: -0.2/-0.9 (n2099); >=19.2: -0.2/-0.1 (n728) |
| st.rs_nq_es_15m | CROSS | <=-3.33: -2.6/-0.5 (n754); <=-0.571: -0.3/-0.1 (n2294) | >=5.01: -1.8/+0.7 (n2073); >=10.5: -1.8/+1.1 (n720) |
| st.rs_nq_rty_15m | CROSS | <=-13.2: +0.5/-0.2 (n711); <=-4.27: -0.3/+0.3 (n2167) | >=7.37: -4.0/+0.6 (n2156); >=17.9: -3.9/+3.6 (n762) |
| st.rv1m_vs_med20d | VOLS | <=0.512: -1.3/-1.2 (n882); <=1.25: -0.4/-0.9 (n2284) | >=5.81: -0.8/+0.5 (n2387); >=10.3: -1.5/+2.3 (n971) |
| st.rv30_ann | VOLS | <=7.07: +2.3/+0.1 (n1052); <=11.5: +1.5/+1.5 (n2877) | >=31.2: -2.9/+2.4 (n1886); >=46.1: -8.3/+1.3 (n598) |
| st.rv30m_vs_med20d | VOLS | <=0.677: +3.8/+0.6 (n621); <=1.06: +0.1/+1.6 (n2049) | >=2.94: -1.2/+2.5 (n2623); >=4.32: -2.9/+2.4 (n1106) |
| st.rv5m_vs_med20d | VOLS | <=0.697: +1.3/+1.2 (n728); <=1.15: -0.7/+1.1 (n2078) | >=3.51: -1.1/+0.8 (n2604); >=5.53: -2.3/+2.2 (n1042) |
| st.sig_absorb10_s | ST | <=1: +1.4/+0.8 (n1345); <=3.67: +2.7/+2.6 (n2765) | >=61: -1.0/-0.1 (n2315); >=140: -0.2/+1.8 (n906) |
| st.sig_delta10_s | ST | <=-26: -2.2/-2.7 (n948); <=-6: -1.4/-1.5 (n2472) | >=23: -1.3/-0.0 (n2157); >=66: -0.9/+2.2 (n793) |
| st.sig_delta60_s | ST | <=-52: -3.4/-5.1 (n916); <=-1: -0.8/-2.4 (n2497) | >=131: -0.6/-0.2 (n2175); >=286: -1.4/+0.4 (n796) |
| st.sig_er120 | ST | <=0.0387: +0.5/-0.6 (n1002); <=0.0857: -0.6/-1.7 (n2422) | >=0.222: +1.3/+2.2 (n2470); >=0.291: +2.0/+2.6 (n970) |
| st.sig_er30 | ST | <=0.0407: -0.2/+0.6 (n997); <=0.104: -0.6/+1.4 (n2491) | >=0.355: +2.9/+1.0 (n2544); >=0.5: +2.1/+0.4 (n1044) |
| st.sig_er300 | ST | <=0.0224: -1.3/-0.5 (n1017); <=0.0505: -1.9/-0.9 (n2508) | >=0.135: +1.3/+1.0 (n2339); >=0.184: +2.2/+1.8 (n892) |
| st.sig_es_move20_atr | CROSS | <=-1.25: -0.0/+0.9 (n945); <=0.175: -2.1/+0.7 (n2337) | >=3.23: +1.4/-0.5 (n2213); >=4.64: +1.9/+1.6 (n922) |
| st.sig_es_nq_div5 | CROSS | <=-0.756: -1.2/-0.1 (n629); <=-0.379: -1.6/+0.4 (n1988) | >=0.273: +0.2/+0.7 (n2099); >=0.606: +1.2/+2.0 (n677) |
| st.sig_imb10_s | ST | <=-0.216: +4.3/+0.9 (n695); <=-0.117: +1.2/-1.0 (n1962) | >=0.0769: -1.1/+0.8 (n2512); >=0.167: +1.7/+1.1 (n973) |
| st.sig_imb5_s | ST | <=-0.238: +3.1/+1.1 (n1007); <=-0.125: +1.5/+0.3 (n2319) | >=0.103: +0.8/+1.0 (n2588); >=0.2: +1.8/+0.8 (n1212) |
| st.sig_intens_rel | VOLS | <=0.579: +1.2/-4.4 (n945); <=0.897: -1.8/-2.4 (n2137) | >=2.18: +0.4/+0.9 (n2858); >=3.57: +3.7/+1.9 (n1051) |
| st.sig_rty_move20_atr | CROSS | <=-2.3: -2.5/+2.5 (n927); <=-0.543: -2.8/+0.8 (n2310) | >=3.22: +0.6/+0.3 (n2262); >=4.96: -0.2/+1.6 (n913) |
| st.sig_rty_nq_div5 | CROSS | <=-1.81: +0.5/+1.1 (n864); <=-0.953: -1.2/-0.5 (n2163) | >=0.48: +2.4/+0.0 (n2346); >=1.17: +1.4/+1.7 (n894) |
| st.sig_rv_5m | VOLS | <=5.88: +1.2/+0.5 (n362); <=9.4: +2.3/+0.6 (n1611) | >=24: -2.1/+3.5 (n3165); >=37.8: -2.0/+1.7 (n1248) |
| st.sig_vel120 | ST | <=-5.25: -1.8/-2.2 (n1060); <=1.75: -0.0/-2.5 (n2279) | >=16.5: -0.2/+1.9 (n2893); >=30: -1.7/+2.0 (n1256) |
| st.sig_vel30 | ST | <=-3.6: -1.4/+0.4 (n1087); <=-0.5: -0.7/-0.4 (n2659) | >=5.5: +0.5/+0.6 (n2995); >=11.2: +0.4/+0.3 (n1312) |
| st.sig_vel300 | ST | <=-8.5: -2.4/-1.8 (n1073); <=2.25: -0.3/-1.8 (n2347) | >=22.5: +0.6/+1.4 (n2950); >=41.2: -0.6/+2.7 (n1198) |
| st.sig_vol60 | VOLS | <=66: +4.3/+1.6 (n1048); <=151: +3.6/+2.5 (n2759) | >=1.48e+03: -0.7/+1.3 (n2243); >=2.53e+03: -1.3/+0.6 (n843) |
| st.vix | CROSS | <=14.4: -5.5/-1.1 (n323) | >=20: -2.5/+3.7 (n1578); >=24.8: -6.4/+2.2 (n274) |
| st.vix9d_over_vix | CROSS | <=0.85: -2.0/-3.0 (n2731); <=0.894: +0.0/-3.8 (n4386) | >=1.02: +5.4/+2.7 (n332) |
| st.vix_chg5 | CROSS | <=-3.38: -7.5/+0.6 (n465); <=-1.2: -4.1/-1.1 (n1723) | >=2.09: -2.0/+1.1 (n2138); >=4.25: -2.7/+1.6 (n1098) |
| st.vvix | CROSS | <=87.7: -9.5/-3.4 (n272) | >=107: -0.8/+2.1 (n1922); >=119: -4.9/+1.8 (n530) |
| st.vwap_dist_pts_eth | ST | <=-3.74: -1.9/-0.5 (n1128); <=10.2: -1.8/+0.9 (n2162) | >=77: -2.3/+0.1 (n3088); >=131: -2.3/-0.7 (n1323) |
| st.vwap_z_eth | ST | <=-0.125: -2.9/-0.4 (n1029); <=0.541: -2.0/-0.3 (n2278) | >=1.71: +2.2/-0.8 (n2021); >=2.08: +6.0/-2.0 (n701) |
| st.vwap_z_rth | ST | <=0.0491: +2.8/+0.4 (n415); <=0.638: +0.0/+1.2 (n968) | >=1.68: -0.3/-2.8 (n781); >=2.04: +3.6/-2.0 (n256) |
| vol.r60_pts | VOL |  | >=20: -0.7/+1.7 (n2926); >=40: -3.4/+2.2 (n771) |

## 10. Best and worst state per family (pooled L6M)

| family | masks | most lowering | dP L6M pp | SEL pp | most raising | dP L6M pp  | SEL pp  |
|--|--|--|--|--|--|--|--|
| AFT | 25 | aft._dayR>=66.32 | -3.6 | 3.9 | aft.stackday_R_q20 | 2.7 | -2.7 |
| BOOK | 27 | bk.imb10_run<=-10 | -3.3 | -1.0 | bk.spread_t>=2 | 11.3 | 5.2 |
| CROSS | 87 | st.vvix<=87.65 | -9.5 | -3.4 | st.vix9d_over_vix>=1.017 | 5.4 | 2.7 |
| DAY | 4 | day.afterbigday2pct | -0.7 | 1.3 | day.inside2 | 15.1 | 1.9 |
| DAYT | 57 | st.es_nq_open30_agree==-1 | -8.0 | -0.7 | st.es_nq_open30_agree==1 | 8.4 | 0.6 |
| ENG | 5 | eng.same_side_within10 | -3.0 | 1.5 | eng.opp_flip_within10 | 2.8 | 10.4 |
| EVT | 7 | evt.rthgap_abs>=40 | -6.2 | 3.4 | evt.rthgap_sided>=20 | 3.0 | 1.9 |
| PX | 206 | px.late.travelled>=1 | -7.1 | 0.9 | rnd.target_near_single | 13.2 | 14.1 |
| ST | 371 | st.15m.atr_ratio>=2.283 | -9.7 | -3.0 | st.1h.ribbon_w<=0.5002 | 10.5 | 2.2 |
| STK | 28 | stk.opp_lots_live>=1 | -2.4 | 0.6 | stk.dup_within180s>=3 | 8.0 | 1.6 |
| TAPE | 32 | bk.iceberg_behind10>=100 | -4.0 | 0.6 | bk.es_imb10<=-0.3 | 10.1 | 1.3 |
| TIME | 50 | tm.edge.close_nypm_end1500.last10 | -13.5 | -16.1 | tm.rel.R830.pre30 | 6.7 | -3.1 |
| VOL | 20 | px.bar.15m.lastrange_atr>=3 | -6.7 | 3.5 | px.bar.1m.lastrange_atr>=3 | 4.5 | 1.7 |
| VOLS | 36 | st.rv30_ann>=46.11 | -8.3 | 1.3 | st.sig_vol60<=66 | 4.3 | 1.6 |

## 11. Store-wide scan (4470 masks from all 1,219 TG-1 measures; labelled SCAN, multiplicity 4470): 66 have |z| > 3.3 in L6M; SEL-vs-L6M Spearman +0.06

Most lowering L6M:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | ptsM_N_in | ptsM_N_out | dP_L3M | dP_HOLD | dP_Y26 | dP_PRE | dP_X | agree |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| sw.1d.sepHMA_20_50>=1.659 | 52 | 25 | 53.10 | -28.10 | -27.44 | -18.51 | 3.36 | -52.30 | -27.10 | -54.60 | 5.80 | -2.10 | 2 |
| sw.1d.vortex14>=0.4718 | 99 | 33.30 | 53.20 | -19.80 | -4.93 | -10.88 | 3.39 | -32.50 | -23 | -54.60 | 0.20 | 0.10 | 1 |
| sw.1d.sep_9_21>=0.93 | 310 | 38.70 | 53.40 | -14.70 | -5.41 | -9.84 | 3.67 | -52.30 | -12.50 | -54.60 | -1.30 | 0.30 | 2 |
| sw.vix3m_over_vix<=0.9757 | 155 | 40.60 | 53.20 | -12.50 | -12.75 | -13.18 | 3.51 | -12 | -11.50 | -54.60 | 2.20 | -47.70 | 2 |
| sw.1d.ext_s50>=3.657 | 166 | 41 | 53.20 | -12.20 | -2.85 | -9.67 | 3.47 | -52.30 | -13 | -54.60 | -3.10 | 3.90 | 2 |
| sw.4h.st7_2_ages>=3.258 | 590 | 41.90 | 53.70 | -11.80 | -3.18 | -7.16 | 3.92 | -15 | -12.80 | -32.50 | -0.40 | -2.20 | 3 |
| sw.1d.sep_8_21>=1.056 | 231 | 41.60 | 53.20 | -11.70 | -5.34 | -7.24 | 3.50 | -52.30 | -11.90 | -54.60 | -1.50 | 0.30 | 2 |
| sw.1d.hma_run>=12 | 402 | 42 | 53.40 | -11.40 | -2.54 | -7.21 | 3.69 | -13.50 | -14.10 | -54.60 | -0.30 | -3.60 | 3 |
| sw.4h.lr_slope100>=0.1071 | 203 | 41.90 | 53.20 | -11.30 | -2.94 | -6.39 | 3.45 | -8.70 | -13.90 | -54.60 | 1.40 | -4.00 | 2 |
| sw.1d.slope_e20_5>=0.1842 | 274 | 42.30 | 53.30 | -10.90 | -2.64 | -4.78 | 3.48 | -52.30 | -9.20 | -54.60 | -2.20 | 1.60 | 2 |
| sw.4h.hurst200>=0.6776 | 135 | 42.20 | 53.10 | -10.90 | -1.19 | -5.85 | 3.37 | -19.80 | -9.90 | -54.60 | -1.00 | 4.60 | 2 |
| sw.4h.lr_dir_r2_100>=0.7725 | 250 | 42.40 | 53.20 | -10.80 | -1.89 | -4.16 | 3.44 | -2.30 | -11.80 | -54.60 | 0.70 | -3.10 | 2 |
| sw.tsmom_z_20d>=1.436 | 259 | 42.50 | 53.20 | -10.80 | -1.79 | -9.02 | 3.58 | -18.90 | -15.10 | -54.60 | -0.30 | -0.50 | 3 |
| sw.1d.adx14_x_di>=24 | 322 | 42.50 | 53.30 | -10.80 | -2.56 | -9.15 | 3.67 | -8.50 | -7.40 | -54.60 | 0.10 | 0.90 | 1 |
| sw.tsmom_ret_20d>=686.9 | 150 | 42.70 | 53.10 | -10.40 | -1.90 | -9.95 | 3.45 | -14.40 | -9.50 | -54.60 | 2.40 | -3.00 | 2 |
| sw.4h.sep_50_200>=4.767 | 361 | 43.50 | 53.30 | -9.80 | -1.71 | -7.01 | 3.64 | -52.30 | -9.90 | -54.60 | -6.50 | 0.10 | 2 |
| sw.4h.st7_2_age>=35 | 619 | 43.80 | 53.60 | -9.80 | -3.28 | -5.28 | 3.82 | -8.90 | -9.40 | -54.60 | 0.60 | 1.90 | 1 |
| sw.15m.atr_ratio>=2.283 | 923 | 44.20 | 53.90 | -9.70 | -3.35 | -5.25 | 4.13 | -7 | -8.80 | -2.10 | -2.50 | -3.10 | 3 |
| sw.1d.macd_hist>=0.3087 | 193 | 43.50 | 53.10 | -9.60 | -2.46 | -9.38 | 3.50 | -9.10 | -8.60 | -54.60 | 3.70 | 3.30 | 1 |
| sw.vvix<=87.65 | 272 | 43.80 | 53.20 | -9.50 | -1.76 | -3.05 | 3.43 | -9 | -8.50 | -54.60 | -2.60 | -2.80 | 3 |

Most lowering on PRE u X' (and what happened):
| state / cut | n_SEL | dP_SEL | z_SEL | dP_PRE | dP_X | n_in | dP_L6M | z_L6M | dP_HOLD |
|--|--|--|--|--|--|--|--|--|--|
| sw.sgn_acf_240m<=0.2184 | 3357 | -9.20 | -6.32 | -6.10 | -9.50 | 86 | 6.40 | 1.74 | 3.80 |
| sw.sig_delta60_s<=-52 | 3372 | -5.10 | -5.74 | -4.10 | -7 | 916 | -3.40 | -2.04 | -4.10 |
| sw.sgn_acf_60m<=0.2416 | 8393 | -6.10 | -5.51 | -4.70 | -6.20 | 617 | -6.50 | -1.78 | -6.10 |
| sw.sgn_acf_15m<=0.211 | 3357 | -6.50 | -5.21 | -6 | -4.90 | 179 | 3.50 | 0.81 | -1.10 |
| sw.sgn_acf_15m<=0.2381 | 8392 | -5.50 | -5.07 | -4.10 | -5.40 | 783 | -6.10 | -1.98 | -6.70 |
| sw.sgn_acf_240m<=0.238 | 8392 | -5.10 | -4.85 | -2.40 | -6.60 | 473 | 5.50 | 1.35 | 2.90 |
| sw.sgn_acf_60m<=0.2173 | 3357 | -5.80 | -4.41 | -2.00 | -6 | 93 | -1.40 | -0.13 | -11.30 |
| sw.1m.ext_20<=-0.2437 | 3357 | -3.70 | -4.32 | -4.30 | -1.90 | 968 | -0.90 | -0.55 | -1.50 |
| sw.1m.slope_e20_1<=-0.02566 | 3357 | -3.70 | -4.32 | -4.30 | -1.90 | 968 | -0.90 | -0.55 | -1.50 |
| sw.1h.rng_exp5>=1.959 | 8397 | -5.10 | -4.24 | -3.00 | -9.40 | 2393 | -4.50 | -2.42 | -3.80 |
| sw.30m.hurst100>=0.6464 | 8392 | -4.40 | -4.20 | -4.50 | -4.60 | 2353 | 1.50 | 0.74 | 2.50 |
| sw.iv0_over_rv30>=1.382 | 4029 | -6.40 | -4.17 | -7.10 | -5.80 | 698 | -7.70 | -2.42 | -10.40 |
| sw.iv0_over_rv30>=1.693 | 1612 | -7.80 | -4.11 | -8.70 | -6.90 | 266 | -3.00 | -0.69 | -7.20 |
| sw.sig_vel120<=1.75 | 8761 | -2.50 | -3.97 | -2.90 | -0.90 | 2279 | -0.00 | -0.04 | -0.20 |
| sw.1h.rng_exp5>=2.527 | 3358 | -6.50 | -3.96 | -5 | -9.90 | 998 | -5.10 | -1.94 | -3.40 |
| sw.sig_delta60_s<=-1 | 8476 | -2.40 | -3.90 | -2.00 | -3.60 | 2497 | -0.80 | -0.71 | -1.40 |
| sw.sig_intens_rel<=0.5794 | 3357 | -4.40 | -3.85 | -4.70 | -3.70 | 945 | 1.20 | 0.45 | 0.80 |
| sw.15m.atr_ratio>=1.856 | 8392 | -4.20 | -3.85 | -2.90 | -6.10 | 1979 | -6.80 | -2.84 | -6.50 |
| sw.exhaust_net_60m>=0 | 23836 | -3.60 | -3.81 | -4.10 | -2.00 | 7163 | -5.90 | -2.75 | -4.80 |
| sw.prev_er_rth>=0.2767 | 3373 | -6.20 | -3.78 | -6.60 | -4.80 | 669 | -0.20 | -0.04 | 0.20 |

Most raising L6M:
| state / cut | n_in | hitM_in | hitM_out | dP_L6M | z_L6M | ptsM_N_in | ptsM_N_out | dP_L3M | dP_HOLD | dP_Y26 | dP_PRE | dP_X | agree |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| sw.1d.vortex14<=-0.4718 | 167 | 71.90 | 52.60 | 19.20 | 17.08 | 24.42 | 2.88 | 19.50 | 7 | -54.60 | 3.00 | 1.50 | 3 |
| sw.30m.sg_aroon==0 | 78 | 70.50 | 52.80 | 17.70 | 2.20 | 23.91 | 3.08 | 18.10 | 11 | 26.80 | -12.10 | -2.60 | 1 |
| sw.1d.sep_8_21<=-1.066 | 379 | 69.70 | 52.30 | 17.40 | 4.86 | 21.24 | 2.52 | -52.30 | 7.60 | -54.60 | 4.30 | 0.70 | 3 |
| sw.1d.rsi_run50<=-31 | 76 | 69.70 | 52.80 | 16.90 | 16.29 | 21.96 | 3.10 | -52.30 | -5 | -54.60 | 1.00 | 1.40 | 2 |
| sw.1d.st7_2_ages<=-3.401 | 76 | 69.70 | 52.80 | 16.90 | 16.29 | 21.96 | 3.10 | -52.30 | -5 | -54.60 | 0.10 | -5.40 | 1 |
| sw.1d.sep_9_21<=-0.9679 | 227 | 67.80 | 52.60 | 15.20 | 4.26 | 20.23 | 2.84 | -52.30 | 0.20 | -54.60 | 2.70 | 0.70 | 3 |
| sw.1d.sepSMA_20_50<=-2.112 | 154 | 67.50 | 52.70 | 14.80 | 5.69 | 19.01 | 2.99 | -52.30 | -2.90 | -54.60 | -5.10 | 0.20 | 1 |
| sw.1d.slope_e20_5<=-0.1868 | 334 | 66.80 | 52.50 | 14.30 | 4.67 | 17.93 | 2.72 | -52.30 | 12.40 | -54.60 | 3.60 | 0.40 | 3 |
| sw.1d.don55_w>=9.718 | 148 | 66.90 | 52.70 | 14.20 | 2.38 | 18.07 | 3.02 | -52.30 | -6.50 | -54.60 | -1.70 | 4.30 | 1 |
| sw.4h.lr_dir_r2_100<=-0.78 | 350 | 65.40 | 52.50 | 12.90 | 2.32 | 16.34 | 2.76 | 11.30 | 6.70 | -54.60 | 2.90 | 4.20 | 3 |
| sw.4h.lr_slope100<=-0.1087 | 308 | 65.30 | 52.50 | 12.70 | 3.18 | 16.39 | 2.82 | 6.20 | 3.10 | -54.60 | 3.10 | 3.10 | 3 |
| sw.1d.slope_e20_3<=-0.1953 | 250 | 64.80 | 52.60 | 12.20 | 2.52 | 16.02 | 2.91 | -52.30 | 10.80 | -54.60 | 5.80 | -1.40 | 2 |
| sw.4h.adx20>=37.54 | 120 | 63.30 | 52.80 | 10.50 | 9.54 | 12.83 | 3.13 | 11.20 | 11.50 | -54.60 | 2.30 | -0.40 | 2 |
| sw.1h.ribbon_w<=0.5002 | 781 | 62.60 | 52.10 | 10.50 | 3.36 | 13.19 | 2.38 | 9.10 | 7 | 8.20 | 1.30 | 4.50 | 3 |
| sw.1d.slope_k20_5<=-0.2427 | 432 | 63 | 52.50 | 10.50 | 2.49 | 14.58 | 2.72 | -52.30 | 5.10 | -54.60 | 2.30 | -0.80 | 2 |

## 12. Gaps and caveats (named, nothing fabricated)
* Release calendar: CPI / NFP / FOMC verified; claims / PCE / 10:00 / minutes are rules and approximate; 13:00 auctions, earnings nights, PPI / retail sales / GDP exact dates not on the box. Engine signals stop about 15:15 ET: the 15:50-16:00 MOC window, the 17:00-18:00 break and the flatten-edge states have n = 0.
* Book wall 'within 10 pts' is not observable: the visible book is 10 levels (about 2.25 pts); wall states are about the visible book. Sweeps are 10 / 30 s (60 s not built); absorption is the L2EA iceberg / refill / consumption columns, not a labelled 30-s absorption event. VIX intraday does not exist on the box (prior-day proxies only). Spread_t is the l2feat measure (modal 3 ticks), thresholds 2/3/5/8.
* Engine-specific states: KB band-break closure %, PE/PB pullback depth and MV vote count are NOT reconstructible from the signal list (engine internals not in the store): named gaps; the whipsaw / flip (opposite signal within N min) and the HMA-slope / Supertrend-age (TG-1 store) versions are built.
* Live-lot mapping K6=KB, P6=PE, U6=SM, H6=HM, M6=MV, A6=PB is ASSUMED. Crowding states use the market-base exit times of the other trades (a simulation of when each position closes).
* P(target) is the market-base target-exit rate; pts per contract N basis (target-fill correction removed). 70/30 columns are in map_named.parquet (hitS, ptsS_pc).
