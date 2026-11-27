# Two-sided candidates vs MATCHED random control (W-NEGBOOK, 1-s race, fee 0.24 pt + 0.25 pt stop slip, events not one-position)

Qualify (pre-written): both sides n>=80, week-clustered excess z>=2 each side (excess = EV minus matched control: same session, 15-min offset to bell, side, 30-min range tercile, 13-wk block), at the bracket; FULL = also each of 2024 and 2025 excess > -1 pt/trade on each side, L6M excess > 0 each side, L3M excess > -0.5 each side. Brackets = target/stop pairs 8/60 8/90 10/60 10/90 15/60 15/90. Cells = Test 5 qualifier cells + supertrend/psar/heikin/hma/ema flips (8,957 cells; NOT the whole grid). Excess already nets out each side's own market drift.


## Asia: cells scored (both sides present) 8360, z>=2 both sides at some bracket 244, FULL at some bracket 155; chance expectation for z>=2 on both sides independently about 4.3 (cells are correlated, so read the count with the shuffle charge W-PLAN-AS runs)

| # | cell (row / module / variant / params) | brackets FULL | best | zL / zS | exL / exS | ev L / S | 24 ex L/S | 25 ex L/S | L6M ex L/S | L3M ex L/S | n L/S | ev per wk (L+S) | sudden-loss share L/S |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_3 / trig_momentum_mvote / v3of5_native / {"scale": 1.0, "thr": 1.0} | 6 | 15/60 | 4.0 / 3.6 | 2.54 / 2.80 | 2.36 / 2.03 | 1.00 / 2.95 | 2.91 / -0.03 | 4.08 / 6.11 | 5.16 / 5.41 | 1524 / 1293 | 15.6 | 1% / 4% |
| 2 | time_m_3 / trig_momentum_mvote / v3of5 / {"scale": 1.0, "thr": 1.0} | 6 | 15/60 | 4.0 / 3.6 | 2.54 / 2.80 | 2.36 / 2.03 | 1.00 / 2.95 | 2.91 / -0.03 | 4.08 / 6.11 | 5.16 / 5.41 | 1524 / 1293 | 15.6 | 1% / 4% |
| 3 | tsf_10_120 / trig_levels_profile_va / false_break_native / {"M": 2, "k": 0.5} | 6 | 15/90 | 2.7 / 2.9 | 3.19 / 2.83 | 2.82 / 1.49 | 3.39 / 1.03 | 1.92 / 2.59 | 4.76 / 5.82 | 8.34 / 6.53 | 667 / 723 | 7.9 | 6% / 12% |
| 4 | vsess_30 / trig_momentum_roc / break_native / {"len": 60, "wd": 1.5} | 5 | 10/60 | 3.4 / 3.6 | 2.24 / 2.88 | 1.96 / 1.85 | 2.78 / 3.37 | 1.85 / 2.87 | 3.05 / 3.45 | 7.86 / 1.94 | 771 / 736 | 8.9 | 2% / 6% |
| 5 | cusum_20 / trig_bands_vwap / break_native / {"clk": 6, "k": 1.5} | 5 | 15/90 | 3.2 / 3.3 | 1.90 / 2.11 | 1.28 / 0.33 | 1.47 / 1.87 | 2.76 / 1.61 | 2.27 / 3.16 | 1.59 / 1.59 | 5092 / 5541 | 57.5 | 7% / 11% |
| 6 | vsess_30 / trig_bands_atrchan / break_ema / {"atr": 14, "k": 1.5, "n": 20} | 5 | 10/60 | 2.9 / 3.3 | 1.50 / 1.75 | 1.14 / 0.83 | 1.85 / 0.91 | 1.10 / 2.37 | 0.76 / 2.51 | 1.60 / 1.46 | 1482 / 1338 | 15.2 | 1% / 4% |
| 7 | tsf_10_120 / trig_trend_ma_kama / price_native / {"len": 50, "width": 1.0} | 5 | 8/90 | 3.6 / 2.9 | 3.54 / 3.49 | 2.90 / 2.18 | 3.54 / 5.85 | 6.60 / 4.59 | 2.34 / 7.40 | 4.98 / 7.86 | 262 / 231 | 3.4 | 0% / 21% |
| 8 | vol_1100 / trig_pullback_st / st / {"arm": 30, "ema": 30, "st_mult": 2.0} | 4 | 10/60 | 3.0 / 3.0 | 1.96 / 2.14 | 1.49 / 1.20 | 0.93 / 0.74 | 2.05 / 0.13 | 2.48 / 5.07 | 5.66 / 4.28 | 913 / 877 | 10.2 | 3% / 3% |
| 9 | tsf_25_150 / trig_levels_swsr5 / retest / {"M": 6, "tol": 0.5} | 4 | 15/60 | 3.1 / 3.0 | 3.60 / 4.44 | 3.11 / 3.55 | 3.97 / 2.64 | 3.79 / 2.50 | 2.22 / 7.04 | 4.02 / 8.40 | 333 / 277 | 4.6 | 5% / 5% |
| 10 | vol_1100 / trig_pullback_st / st / {"arm": 10, "ema": 30, "st_mult": 2.0} | 4 | 10/60 | 3.0 / 3.1 | 1.92 / 2.22 | 1.44 / 1.27 | 0.89 / 1.07 | 2.02 / 0.19 | 2.45 / 5.06 | 5.63 / 4.28 | 909 / 876 | 10.2 | 3% / 3% |
| 11 | time_m_7 / trig_momentum_stoch / zone_break_native / {"len": 21, "lvl": 90} | 4 | 15/90 | 3.2 / 2.9 | 1.80 / 1.78 | 1.29 / 0.74 | 0.99 / 3.11 | 2.11 / 0.86 | 4.30 / 2.48 | 4.46 / 2.05 | 3116 / 2442 | 30.0 | 1% / 2% |
| 12 | time_m_7 / trig_momentum_stoch / zone_break / {"len": 21, "lvl": 90} | 4 | 15/90 | 3.2 / 2.9 | 1.80 / 1.78 | 1.29 / 0.74 | 0.99 / 3.11 | 2.11 / 0.86 | 4.30 / 2.48 | 4.46 / 2.05 | 3116 / 2442 | 30.0 | 1% / 2% |
| 13 | tm300 / trig_live_seven / A7 / {"live": 1} | 4 | 10/90 | 3.4 / 2.9 | 2.39 / 3.05 | 1.86 / 1.94 | 0.79 / 6.84 | 3.42 / 1.40 | 2.16 / 2.75 | 3.09 / 0.24 | 1189 / 423 | 9.9 | 0% / 0% |
| 14 | tick_500 / trig_momentum_mvote / v4of5_native / {"scale": 0.5, "thr": 0.25} | 4 | 15/60 | 3.0 / 2.8 | 1.99 / 2.05 | 1.54 / 1.15 | 3.15 / 4.67 | 1.63 / -0.92 | 1.86 / 4.15 | 0.86 / 4.22 | 1806 / 1644 | 18.6 | 2% / 2% |
| 15 | drb_700 / trig_bands_bollinger / walk_native / {"N": 3, "clk": 10, "k": 1.5} | 4 | 15/60 | 2.8 / 3.1 | 2.33 / 3.01 | 1.85 / 1.89 | 2.26 / 4.99 | 1.63 / 1.55 | 3.94 / 4.24 | 3.61 / 1.61 | 900 / 856 | 9.8 | 3% / 5% |
| 16 | drb_400 / trig_momentum_roc / break_native / {"len": 5, "wd": 1.5} | 4 | 10/60 | 2.6 / 3.0 | 1.64 / 1.94 | 1.07 / 1.06 | 0.61 / 4.73 | 2.33 / 0.35 | 0.85 / 2.54 | -0.38 / 1.80 | 1464 / 1379 | 16.1 | 2% / 5% |
| 17 | vol_500 / trig_momentum_cci / zero_native / {"len": 30, "lvl": 50} | 4 | 8/90 | 2.7 / 2.6 | 1.51 / 1.47 | 0.87 / 0.43 | 0.57 / 1.48 | 1.37 / 0.45 | 2.09 / 2.94 | 3.30 / 2.78 | 2013 / 1957 | 21.5 | 4% / 3% |
| 18 | drb_700 / trig_bands_bollinger / walk / {"N": 3, "k": 1.5, "n": 30} | 4 | 10/60 | 2.6 / 2.6 | 1.76 / 2.21 | 1.39 / 1.32 | 1.21 / 3.17 | 1.94 / 0.00 | 2.79 / 4.55 | 3.79 / 2.21 | 865 / 839 | 9.5 | 0% / 6% |
| 19 | tsf_5_400 / trig_levels_piv_floor / break_native / {"k": 0.25, "n": 2} | 4 | 8/60 | 3.4 / 2.5 | 2.14 / 1.81 | 1.76 / 1.00 | 1.03 / -0.84 | 1.02 / 4.77 | 3.77 / 1.51 | 4.18 / 2.48 | 644 / 586 | 6.8 | 2% / 9% |
| 20 | mom_10 / trig_bands_vwap / break / {"k": 1.5, "minbars": 10} | 3 | 15/90 | 2.9 / 3.2 | 1.67 / 2.10 | 1.02 / 0.44 | 1.13 / 2.27 | 2.28 / 1.68 | 1.30 / 3.62 | 1.26 / 0.49 | 8185 / 8593 | 90.7 | 6% / 9% |
| 21 | vol_1100 / trig_trend_ma_ema / cross_native / {"len": 30, "ratio": 3, "width": 0.5} | 3 | 15/90 | 3.5 / 2.9 | 6.39 / 5.38 | 5.71 / 3.69 | 5.29 / 5.72 | 6.78 / 7.63 | 7.23 / 1.97 | 7.63 / 5.09 | 177 / 171 | 3.1 | 9% / 13% |
| 22 | vol_2600 / trig_bands_envelope / break_sma / {"n": 10, "pct": 0.05} | 3 | 15/60 | 3.0 / 2.8 | 2.10 / 1.95 | 1.79 / 0.99 | -0.03 / 1.78 | 2.19 / 0.60 | 2.63 / 2.56 | 3.69 / 3.76 | 1215 / 1112 | 12.6 | 0% / 5% |
| 23 | cusum_80 / trig_levels_profile_nodes / false_break_native / {"M": 3, "k": 0.5} | 3 | 10/90 | 2.8 / 3.6 | 1.87 / 2.49 | 1.31 / 1.26 | 2.74 / 4.15 | 5.09 / 0.47 | 1.44 / 4.07 | 0.39 / 2.35 | 1295 / 1251 | 14.1 | 4% / 16% |
| 24 | tsf_2_400 / trig_levels_vwap / break / {"k": 0.5, "n": 3} | 3 | 15/90 | 2.8 / 3.2 | 1.64 / 2.13 | 1.17 / 0.82 | 0.53 / 1.77 | 2.58 / -0.26 | 2.47 / 5.68 | 2.52 / 1.59 | 2358 / 2239 | 24.8 | 3% / 1% |
| 25 | vsess_30 / trig_bands_envelope / break_ema / {"n": 20, "pct": 0.1} | 3 | 10/90 | 2.9 / 2.8 | 1.71 / 1.71 | 1.04 / 0.50 | 1.14 / 2.36 | 2.07 / 0.71 | 1.69 / 1.73 | 2.14 / 1.97 | 1575 / 1343 | 16.0 | 1% / 2% |

Live books (same test, 10/60): AS_MF1 zL 0.9 zS 1.5 exL 0.36 exS 0.54; AS_MF2 zL 1.6 zS 1.9 exL 1.68 exS 2.24; AS_MF3 zL 1.5 zS 2.2 exL 0.69 exS 0.98; AS_MF4 zL 1.4 zS 2.1 exL 1.10 exS 1.61


## London: cells scored (both sides present) 8620, z>=2 both sides at some bracket 7, FULL at some bracket 4; chance expectation for z>=2 on both sides independently about 4.5 (cells are correlated, so read the count with the shuffle charge W-PLAN-AS runs)

| # | cell (row / module / variant / params) | brackets FULL | best | zL / zS | exL / exS | ev L / S | 24 ex L/S | 25 ex L/S | L6M ex L/S | L3M ex L/S | n L/S | ev per wk (L+S) | sudden-loss share L/S |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | vol_750 / trig_bands_atrchan / break_ext / {"atr": 14, "k": 4.0, "n": 20} | 1 | 15/60 | 2.2 / 2.4 | 1.32 / 1.56 | 1.55 / 0.86 | -0.15 / 1.48 | 1.65 / 0.44 | 3.12 / 3.16 | 2.20 / 1.08 | 2202 / 1874 | 22.0 | 3% / 2% |
| 2 | lbrk_3_20 / trig_tape_div / div_fade / {"N": 20, "k": 0.5} | 1 | 15/90 | 2.1 / 3.1 | 5.10 / 7.12 | 5.45 / 7.24 | 5.06 / 9.52 | 1.61 / 8.02 | 13.08 / 6.55 | 13.26 / 2.19 | 107 / 111 | 3.6 | 11% / 40% |
| 3 | tick_500 / trig_pullback_st / st / {"arm": 30, "ema": 14, "st_mult": 3.0} | 1 | 15/90 | 2.4 / 2.1 | 1.51 / 1.52 | 1.60 / 0.57 | 1.22 / 1.36 | -0.03 / 1.96 | 1.79 / 0.38 | 5.38 / 2.86 | 2942 / 2589 | 29.9 | 4% / 3% |
| 4 | vnorm_400 / trig_xmarket_nkd / follow / {"thr": 1.0, "w": 3} | 1 | 8/60 | 2.0 / 2.1 | 0.98 / 1.00 | 0.88 / 0.21 | 0.26 / 0.70 | 0.61 / 1.36 | 0.89 / 1.34 | 2.79 / 0.57 | 1937 / 1916 | 21.4 | 9% / 7% |

Live books (same test, 10/60): LO_MF1 zL 0.4 zS 2.0 exL 0.29 exS 1.44; LO_MF3 zL 0.8 zS -0.8 exL 0.27 exS -0.26


## NY AM: cells scored (both sides present) 8764, z>=2 both sides at some bracket 58, FULL at some bracket 33; chance expectation for z>=2 on both sides independently about 4.6 (cells are correlated, so read the count with the shuffle charge W-PLAN-AS runs)

| # | cell (row / module / variant / params) | brackets FULL | best | zL / zS | exL / exS | ev L / S | 24 ex L/S | 25 ex L/S | L6M ex L/S | L3M ex L/S | n L/S | ev per wk (L+S) | sudden-loss share L/S |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | typ_micro_B080 / trig_bands_envelope / break_sma_native / {"clk": 20, "k": 1.5} | 4 | 10/90 | 3.8 / 3.2 | 3.21 / 3.17 | 2.95 / 2.40 | 1.71 / 3.52 | 2.07 / 1.08 | 6.57 / 6.34 | 4.25 / 8.56 | 657 / 727 | 8.1 | 18% / 21% |
| 2 | typ_qmid_B080 / trig_bands_envelope / break_sma_native / {"clk": 20, "k": 1.5} | 4 | 10/90 | 3.6 / 3.2 | 3.07 / 3.14 | 2.83 / 2.39 | 1.80 / 3.39 | 2.05 / 1.05 | 5.51 / 6.38 | 4.31 / 8.56 | 662 / 729 | 8.2 | 19% / 21% |
| 3 | ha_bmsg_B080 / trig_pullback_ema / depth_native / {"len": 5, "w": 1.5} | 4 | 8/60 | 3.0 / 2.3 | 1.15 / 0.92 | 0.89 / 0.39 | -0.02 / 0.96 | 1.98 / 0.56 | 2.41 / 0.94 | 2.43 / 1.62 | 2480 / 3123 | 30.3 | 18% / 19% |
| 4 | cdr_160 / trig_tape_block / b10_follow / {"L": 50, "z": 1.5} | 3 | 8/90 | 2.4 / 2.6 | 0.72 / 0.75 | 0.36 / 0.13 | 0.34 / 1.12 | 0.50 / 0.76 | 2.48 / 0.97 | 3.17 / 1.31 | 8929 / 8180 | 92.5 | 14% / 13% |
| 5 | dib_25000 / trig_bands_avwap0830 / walk_0830 / {"N": 3, "k": 1.0, "minbars": 30} | 3 | 8/90 | 3.5 / 2.3 | 2.26 / 1.45 | 2.14 / 1.16 | 2.32 / 1.70 | 3.42 / 0.65 | 1.60 / 1.95 | 5.91 / 1.36 | 1366 / 1241 | 14.3 | 11% / 15% |
| 6 | urenko_56 / trig_momentum_er / trend_native / {"len": 30, "thr": 0.3} | 2 | 8/90 | 4.1 / 3.6 | 3.92 / 3.31 | 3.30 / 2.80 | 4.95 / 4.82 | 5.23 / 4.93 | 1.16 / 4.47 | 8.62 / 4.13 | 475 / 553 | 6.7 | 30% / 22% |
| 7 | dlt_100 / trig_bands_atrchan / break_ema_native / {"clk": 20, "k": 1.5} | 2 | 10/90 | 3.9 / 3.1 | 5.50 / 4.46 | 5.10 / 4.04 | 5.27 / 4.14 | 7.32 / 2.15 | 10.66 / 8.50 | 11.14 / 7.16 | 160 / 212 | 4.6 | 22% / 19% |
| 8 | vsess_50 / trig_bands_atrchan / break_ema / {"atr": 14, "k": 3.0, "n": 10} | 2 | 15/90 | 2.9 / 2.7 | 6.68 / 6.40 | 5.88 / 4.72 | 2.16 / 2.23 | 12.07 / 5.71 | 11.92 / 12.61 | 11.40 / 8.01 | 154 / 160 | 3.2 | 21% / 28% |
| 9 | rng_56 / trig_book_ofi / follow_sm / {"L": 50, "sm": 3, "z": 2.0} | 2 | 15/60 | 2.7 / 3.1 | 1.49 / 2.44 | 1.27 / 2.01 | 2.37 / 1.46 | 0.85 / 3.40 | 2.24 / 2.69 | 1.03 / 3.17 | 3140 / 1334 | 24.2 | 13% / 27% |
| 10 | t3_micro_B200 / trig_bands_keltner / break / {"atr": 10, "ema": 14, "mult": 1.5} | 2 | 10/90 | 2.6 / 2.9 | 2.33 / 2.81 | 2.14 / 2.11 | 1.15 / 2.46 | 5.27 / 0.51 | 2.80 / 4.55 | 3.25 / 4.91 | 714 / 716 | 8.0 | 19% / 24% |
| 11 | drb_2000 / trig_book_ofi / follow_sm / {"L": 100, "sm": 3, "z": 2.0} | 2 | 15/60 | 2.5 / 3.5 | 1.62 / 3.23 | 1.40 / 2.68 | 1.38 / 4.64 | 1.80 / 2.29 | 5.09 / 0.52 | -0.23 / 0.25 | 2374 / 869 | 17.5 | 9% / 20% |
| 12 | pasl_14 / trig_pullback_st / st / {"arm": 30, "ema": 20, "st_mult": 3.0} | 2 | 15/60 | 2.4 / 3.0 | 1.52 / 2.10 | 1.03 / 1.64 | 2.40 / 1.26 | 1.50 / 2.76 | 0.04 / 0.83 | 4.08 / 0.79 | 2433 / 2227 | 25.2 | 19% / 21% |
| 13 | dchg_56 / trig_book_ofi / follow_sm / {"L": 50, "sm": 3, "z": 1.5} | 2 | 15/90 | 2.3 / 2.6 | 1.58 / 2.42 | 1.22 / 1.90 | 1.53 / 3.72 | 2.59 / 2.78 | 1.45 / 0.82 | 4.54 / 2.24 | 2492 / 1204 | 20.0 | 18% / 32% |
| 14 | kagi_56 / trig_book_ofi / follow_sm / {"L": 50, "sm": 3, "z": 1.5} | 2 | 15/90 | 2.3 / 2.6 | 1.58 / 2.42 | 1.22 / 1.90 | 1.53 / 3.72 | 2.59 / 2.78 | 1.45 / 0.82 | 4.54 / 2.24 | 2492 / 1204 | 20.0 | 18% / 32% |
| 15 | swing_atr_0.25 / trig_tape_block / b10_follow_sm / {"L": 100, "sm": 3, "z": 1.5} | 2 | 8/90 | 2.1 / 2.8 | 0.57 / 0.77 | 0.20 / 0.14 | 0.65 / 1.39 | 0.38 / 0.53 | 0.78 / 0.74 | 1.70 / -0.25 | 10956 / 10015 | 113.4 | 18% / 20% |
| 16 | urenko_56 / trig_momentum_er / trend_z_native / {"len": 30, "thr": 0.3} | 1 | 8/90 | 4.2 / 3.7 | 4.02 / 3.43 | 3.42 / 2.95 | 5.01 / 4.78 | 5.07 / 5.52 | 2.48 / 4.39 | 8.47 / 3.96 | 474 / 550 | 6.7 | 27% / 23% |
| 17 | time_s_10 / trig_bands_keltner / walk_native / {"N": 3, "clk": 10, "k": 1.5} | 1 | 15/90 | 2.8 / 2.7 | 5.59 / 5.23 | 5.51 / 4.17 | 6.32 / 6.15 | 5.70 / 1.44 | 15.35 / 10.62 | 16.54 / 10.10 | 150 / 197 | 4.0 | 15% / 20% |
| 18 | t3_sessrng_B200 / trig_bands_atrchan / break_ema / {"atr": 14, "k": 1.5, "n": 10} | 1 | 10/90 | 2.7 / 3.5 | 3.45 / 4.37 | 3.16 / 2.99 | 2.91 / 4.80 | 3.64 / 5.60 | 3.47 / 3.82 | 1.14 / 1.64 | 346 / 324 | 4.2 | 30% / 33% |
| 19 | vol_4000 / trig_book_ofi / follow_sm / {"L": 50, "sm": 3, "z": 2.0} | 1 | 15/60 | 2.6 / 3.5 | 1.47 / 3.25 | 1.26 / 2.68 | 2.28 / 3.46 | 1.12 / 1.15 | 2.50 / 4.78 | 3.29 / 0.26 | 2521 / 917 | 18.7 | 10% / 14% |
| 20 | mrenko_14 / trig_bands_avwap0830 / walk_0830_native / {"N": 3, "clk": 25, "k": 1.0} | 1 | 15/90 | 3.4 / 2.5 | 2.32 / 1.55 | 1.85 / 0.79 | 4.10 / 0.70 | 1.39 / 2.00 | 0.76 / 1.62 | 3.01 / 1.00 | 3929 / 4333 | 44.7 | 22% / 23% |
| 21 | frenko_28 / trig_book_ofi / follow / {"L": 100, "z": 2.0} | 1 | 15/60 | 2.8 / 2.5 | 1.01 / 1.03 | 0.61 / 0.59 | 0.20 / 1.59 | 1.61 / 0.79 | 0.79 / 1.12 | -0.18 / -0.28 | 10061 / 6308 | 88.5 | 17% / 21% |
| 22 | trb_3500 / trig_book_ofi / follow_sm / {"L": 200, "sm": 3, "z": 2.0} | 1 | 10/60 | 2.5 / 3.5 | 1.34 / 3.28 | 1.22 / 2.88 | 1.87 / 5.28 | 1.08 / 0.78 | 1.43 / 2.71 | 2.67 / 1.35 | 1600 / 474 | 11.5 | 9% / 32% |
| 23 | entropy_B080 / trig_bands_atrchan / break_ema / {"atr": 14, "k": 3.0, "n": 20} | 1 | 15/90 | 2.4 / 2.6 | 3.07 / 2.97 | 2.67 / 2.04 | 6.93 / 1.00 | 4.45 / 4.94 | 2.00 / 3.85 | 2.76 / 3.31 | 669 / 817 | 8.6 | 24% / 20% |
| 24 | vsess_200 / trig_momentum_mvote / v5of5_native / {"scale": 0.5, "thr": 1.0} | 1 | 15/90 | 2.7 / 2.4 | 2.79 / 2.21 | 2.29 / 1.30 | 1.11 / 3.24 | 3.29 / 1.83 | 5.76 / 1.41 | 6.07 / 3.54 | 1204 / 1352 | 14.9 | 21% / 26% |
| 25 | pasl_14 / trig_pullback_st / st / {"arm": 10, "ema": 20, "st_mult": 3.0} | 1 | 15/60 | 2.3 / 3.6 | 1.47 / 2.34 | 0.94 / 1.86 | 2.74 / 1.40 | 0.22 / 3.20 | 2.87 / 0.63 | 7.15 / 0.25 | 2728 / 2545 | 28.5 | 16% / 20% |

Live books (same test, 10/60): NY_MF1 zL 0.3 zS 0.1 exL 0.07 exS 0.03; NY_MF2 zL 1.1 zS -1.3 exL 0.50 exS -0.54; NY_MF3 zL 0.7 zS 0.4 exL 0.33 exS 0.26; NY_MF4 zL -0.1 zS -0.7 exL -0.03 exS -0.21; NY_MF5 zL 1.3 zS -0.0 exL 0.46 exS -0.01; NY_MF8 zL 2.7 zS -2.2 exL 2.21 exS -2.19


## NY PM: cells scored (both sides present) 8763, z>=2 both sides at some bracket 5, FULL at some bracket 3; chance expectation for z>=2 on both sides independently about 4.6 (cells are correlated, so read the count with the shuffle charge W-PLAN-AS runs)

| # | cell (row / module / variant / params) | brackets FULL | best | zL / zS | exL / exS | ev L / S | 24 ex L/S | 25 ex L/S | L6M ex L/S | L3M ex L/S | n L/S | ev per wk (L+S) | sudden-loss share L/S |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_13 / trig_levels_prior_day / reject_native / {"conf": "body", "tol": 0.5} | 2 | 10/60 | 2.7 / 2.1 | 2.09 / 1.73 | 1.38 / 1.55 | 1.12 / 1.17 | 2.65 / 2.56 | 3.38 / 0.53 | 4.93 / 3.62 | 843 / 766 | 9.1 | 10% / 6% |
| 2 | time_m_13 / trig_levels_prior_day / reject_native / {"conf": "body", "tol": 1.0} | 1 | 10/60 | 2.3 / 2.2 | 1.49 / 1.44 | 0.84 / 1.25 | 1.17 / 1.98 | 1.13 / 1.46 | 3.97 / 2.03 | 4.98 / 3.93 | 1161 / 1051 | 12.3 | 10% / 4% |
| 3 | ha_rngor_B200 / trig_momentum_roc / zero_native / {"len": 40, "wd": 1} | 1 | 15/90 | 2.4 / 2.1 | 3.26 / 2.64 | 3.00 / 2.67 | 0.69 / 2.12 | 3.75 / 5.40 | 0.48 / 3.73 | 4.84 / 3.17 | 1103 / 1107 | 15.7 | 17% / 12% |

Live books (same test, 10/60): NP_MF1 zL 2.1 zS 0.9 exL 1.10 exS 0.41; NP_MF2 zL 0.4 zS 0.2 exL 0.32 exS 0.13; NP_MF3 zL 1.9 zS 1.6 exL 1.52 exS 1.30; NP_MF4 zL 0.3 zS -0.8 exL 0.13 exS -0.48
