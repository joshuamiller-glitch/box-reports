# CF4_DEEPEN_PART1 - state at the entry second (squeeze / RSI / CCI / stochastic / MACD, 1-5-15-60 min) read relative to the trade side

**Verdict (data ends 2026-11-11) line (): of 317 state conditions (320 columns, 4 timeframes) tested in 50 cells each, 125 (condition x cell) tests clear the cell's nonsense bar with the full rule (0.79% vs nonsense 0.44%); 121 of these also beat 95% of matched-count random subsets on expectancy and 39 on expectancy AND drawdown. Family rates: A squeeze 0.81% (1.8x); B oscillators 0.72% (1.6x); C macd 0.58% (1.3x); D agreement 1.05% (2.4x). FIRST PASS; engine actions (skip / half / x1.5 / wait N=3,6,12) and the engine random-skip control belong to W-CF3.**

Columns: /mnt/l2/l2vast/_confl/cols_cf4/cf4_state.parquet (sid = sig_id; definitions below = code/th_confl_cf4/c4_state.py docstring). Wait-form entry times for every passing state: cf4_state_wait.parquet (stw_<state>_dt_{true|false}_N{3,6,12}; future-looking, entry-timing only). Passing list with all metrics: /mnt/l2/l2vast/_confl/cf4_candidates/state_passers.csv and cols_cf4/state_passers.parquet.

PART 1 of DIRECTIVE_CONFLUENCE_DEEPEN: indicator STATE AT THE ENTRY SECOND (not a fresh signal) on 1/5/15/60-min bars, read relative to the trade side. Causal: last COMPLETED bar of each timeframe at the signal second.
Columns cf4_state.parquet, key sid=sig_id, int8 1 yes / 0 no / -1 unknown: c4_st_<tf>_<name>, tf in 1m,5m,15m,60m.
A SQUEEZE (Bollinger 20,2 inside Keltner 20, k x SMA20 true range; k = 1.0 / 1.5 / 2.0 -> tags k10 k15 k20; momentum histogram = linreg(close - avg(avg(HH20,LL20),SMA20),20)):
   A1 sqz<k>_on_1_5 / on_6_12 / on_13p      ON now (not yet fired), bars in squeeze 1-5 / 6-12 / 13+
   A2 sqz<k>_fw_1_3 / fw_4_8 / fw_9p         FIRED (off now, last release 1-3 / 4-8 / 9+ bars ago, release bar counts 1), histogram sign WITH the trade side
   A3 sqz<k>_fa_1_3 / fa_4_8 / fa_9p         same with histogram AGAINST the trade side
   A4 sqz<k>_none30                          no squeeze bar in the last 30 bars
   A5 sqz<k>_slope_with / slope_against      histogram change over the last bar with / against the trade side; combos mom_with_slope_with (strengthening), mom_with_slope_against (fading), mom_against_slope_with (turning), mom_against_slope_against
B OSCILLATORS read relative to the trade side (RSI14 30/70, RSI2 10/90, CCI20 -100/100, Stoch(14,3) %K-smoothed-3 20/80): <ind>_ext_against (long in overbought / short in oversold), <ind>_ext_with (long from oversold / short from overbought), <ind>_mid, <ind>_xin_with / <ind>_xin_against (was in the with / against extreme within the last 3 bars and is back inside now)
C MACD(12,26,9) histogram: macd_hist_with / macd_hist_against (sign), macd_slope_with / macd_slope_against (change over 1 bar), macd_with_rising (sign with and slope with), macd_against_falling
D AGREEMENT over the 4 timeframes (column group c4_st_agree_<A|B|C>_*): A_with = squeeze (k=1.5) FIRED with histogram with the trade (A2 any age); B_with = RSI14 on the trade's side of 50 and not at the against-extreme; C_with = macd_with_rising. n = number of the 4 timeframes with the state (0-4): _n (raw), _eq0.._eq4, _ge2, _ge3.

BOOK GROUPS (USER ANSWER 2026-11-16, autopilot/ANSWER_BOOK_TYPES_20261116.md): NO book is mean-reversion. Breakout / trend = K7 (Keltner break 3-min), M7 (momentum vote 4-of-5), U7 (Supertrend 10-min), H7 (HMA 20/55 cross + EMA200); pullback = P7 (pullback inside a Supertrend 5-min regime), A7 (Asia pullback), O7 (opening drive with pullback). The earlier grouping K7 = mean-reversion was wrong and is replaced; the per-book table below is unchanged. The sign of the measured lift is kept per row.

Rule for a pass (W-CF1): |zw| (weekly cluster-robust t, >= 8 weeks) above the 99th percentile of |zw| of the 200 nonsense controls in the same cell, lift keeps its sign in every calendar year with >= 30 per side and in L6M. Matched-count: 300 random subsets of the kept set's size and book x session x month composition drawn from the cell; pct_expect = share with lower mean R, pct_drawdown = share with larger max drawdown (R units) than the kept set; kept set = the state if lift>0, its complement if lift<0.

## Passing states by book group

| group | passing tests | with lift>0 | median lift R | median pct_expect | median pct_drawdown | both >= 0.95 |
|---|---|---|---|---|---|---|
| breakout / trend (K7, M7, U7, H7) | 61 | 19 | -0.073 | 1.00 | 0.86 | 18 |
| pooled (ALL or session cell) | 35 | 10 | -0.069 | 1.00 | 0.91 | 13 |
| pullback (P7, A7, O7) | 29 | 14 | -0.060 | 1.00 | 0.86 | 8 |

## Sign of the passing lifts by state type and book group (breakout / trend vs pullback)

| state type | group | passing tests | lift>0 | lift<0 |
|---|---|---|---|---|
| osc_mid | breakout / trend (K7, M7, U7, H7) | 3 | 1 | 2 |
| osc_xin_against | breakout / trend (K7, M7, U7, H7) | 5 | 1 | 4 |
| sqz_fa_4_8 | breakout / trend (K7, M7, U7, H7) | 3 | 0 | 3 |
| sqz_fa_9p | breakout / trend (K7, M7, U7, H7) | 5 | 1 | 4 |
| sqz_fw_1_3 | pullback (P7, A7, O7) | 3 | 1 | 2 |
| sqz_mom_against_slope_with | breakout / trend (K7, M7, U7, H7) | 6 | 0 | 6 |
| sqz_mom_with_slope_against | pullback (P7, A7, O7) | 3 | 3 | 0 |
| sqz_mom_with_slope_with | breakout / trend (K7, M7, U7, H7) | 6 | 3 | 3 |
| sqz_on_1_5 | breakout / trend (K7, M7, U7, H7) | 3 | 0 | 3 |
| sqz_on_1_5 | pullback (P7, A7, O7) | 3 | 0 | 3 |
| sqz_slope_against | breakout / trend (K7, M7, U7, H7) | 3 | 3 | 0 |
| sqz_slope_against | pullback (P7, A7, O7) | 3 | 3 | 0 |
| sqz_slope_with | breakout / trend (K7, M7, U7, H7) | 3 | 0 | 3 |
| sqz_slope_with | pullback (P7, A7, O7) | 3 | 0 | 3 |

## Passing states by individual book (no grouping assumed)

| book | passing tests | lift>0 | median lift R | median pct_expect | median pct_drawdown | both >= 0.95 |
|---|---|---|---|---|---|---|
| A7 | 6 | 2 | -0.083 | 1.00 | 0.70 | 1 |
| H7 | 7 | 3 | -0.098 | 1.00 | 0.95 | 4 |
| K7 | 28 | 10 | -0.102 | 1.00 | 0.84 | 8 |
| M7 | 24 | 5 | -0.058 | 1.00 | 0.84 | 6 |
| P7 | 23 | 12 | 0.071 | 1.00 | 0.87 | 7 |
| U7 | 2 | 1 | 0.000 | 0.99 | 0.89 | 0 |

## Passing states that also beat the matched-count control on expectancy AND drawdown (>= 0.95 each)

| cell | book | sess | state | n yes | R yes | R cell | $ yes | $ cell | lift R | zw | bar99 | pct expect | pct DD | by year lift | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | c4_st_60m_sqzk20_fa_1_3 | 3107 | -0.071 | 0.019 | 18 | 26 | -0.093 | -5.1 | 2.3 | 1.00 | 0.99 | 2023:-0.09 2024:-0.13 2025:-0.07 2026:-0.09 | -0.147 |
| sess |  | nyam | c4_st_15m_sqzk20_fw_1_3 | 2166 | -0.093 | 0.023 | -21 | 8 | -0.133 | -4.4 | 2.0 | 1.00 | 1.00 | 2023:-0.18 2024:-0.12 2025:-0.10 2026:-0.15 | -0.282 |
| sess |  | nyam | c4_st_60m_rsi14_xin_with | 1075 | -0.137 | 0.023 | -67 | 8 | -0.170 | -4.3 | 2.0 | 1.00 | 1.00 | 2023:-0.10 2024:-0.20 2025:-0.18 2026:-0.18 | -0.219 |
| sess |  | london | c4_st_1m_stoch14_xin_with | 1139 | 0.127 | 0.025 | 116 | 10 | 0.109 | 3.7 | 2.5 | 1.00 | 1.00 | 2023:+0.05 2024:+0.12 2025:+0.14 2026:+0.10 | 0.065 |
| book_sess | M7 | close | c4_st_15m_sqzk20_on_13p | 792 | 0.162 | 0.017 | 0 | 0 | 0.189 | 3.6 | 2.8 | 1.00 | 1.00 | 2023:+0.14 2024:+0.28 2025:+0.06 2026:+0.25 | 0.355 |
| book | H7 |  | c4_st_agree_C_ge2 | 2276 | 0.011 | 0.046 | 18 | 52 | -0.118 | -3.5 | 2.4 | 1.00 | 1.00 | 2023:-0.14 2024:-0.13 2025:-0.17 2026:-0.04 | -0.039 |
| book_sess | H7 | london | c4_st_agree_B_eq2 | 176 | -0.077 | 0.052 | 0 | 0 | -0.161 | -3.3 | 2.9 | 0.98 | 0.95 | 2023:-0.20 2024:-0.14 2025:-0.12 2026:-0.20 | -0.341 |
| sess |  | close | c4_st_60m_cci20_xin_with | 2544 | -0.083 | 0.001 | 0 | 0 | -0.105 | -3.3 | 2.5 | 1.00 | 1.00 | 2023:-0.06 2024:-0.19 2025:-0.06 2026:-0.10 | -0.002 |
| book_sess | K7 | nyam | c4_st_agree_B_ge2 | 2658 | -0.027 | 0.006 | 2 | 5 | -0.150 | -3.2 | 2.3 | 1.00 | 1.00 | 2023:-0.09 2024:-0.12 2025:-0.18 2026:-0.17 | -0.231 |
| book | M7 |  | c4_st_60m_sqzk15_mom_against_slope_with | 4574 | -0.034 | 0.008 | 1 | 4 | -0.059 | -3.2 | 2.2 | 1.00 | 0.99 | 2023:-0.14 2024:-0.08 2025:-0.04 2026:-0.02 | -0.058 |
| book | M7 |  | c4_st_60m_sqzk20_mom_against_slope_with | 4574 | -0.034 | 0.008 | 1 | 4 | -0.059 | -3.2 | 2.2 | 1.00 | 1.00 | 2023:-0.14 2024:-0.08 2025:-0.04 2026:-0.02 | -0.058 |
| book | M7 |  | c4_st_60m_sqzk10_mom_against_slope_with | 4574 | -0.034 | 0.008 | 1 | 4 | -0.059 | -3.2 | 2.2 | 1.00 | 1.00 | 2023:-0.14 2024:-0.08 2025:-0.04 2026:-0.02 | -0.058 |
| book_sess | P7 | london | c4_st_1m_sqzk20_fw_1_3 | 158 | 0.158 | 0.017 | 36 | 8 | 0.145 | 3.1 | 2.2 | 0.98 | 0.98 | 2023:na 2024:na 2025:+0.12 2026:+0.26 | 0.266 |
| sess |  | nypm | c4_st_60m_sqzk10_fw_1_3 | 564 | -0.249 | -0.001 | -26 | 4 | -0.256 | -3.1 | 2.4 | 1.00 | 0.99 | 2023:-0.17 2024:-0.25 2025:-0.01 2026:-0.72 | -0.423 |
| book_sess | P7 | close | c4_st_60m_stoch14_ext_with | 560 | 0.192 | 0.004 | 0 | 0 | 0.212 | 3.1 | 2.6 | 1.00 | 0.95 | 2023:+0.35 2024:+0.12 2025:+0.13 2026:+0.27 | 0.446 |
| book | H7 |  | c4_st_agree_C_eq2 | 1163 | -0.017 | 0.046 | -33 | 52 | -0.098 | -3.0 | 2.4 | 1.00 | 1.00 | 2023:-0.12 2024:-0.05 2025:-0.12 2026:-0.11 | -0.120 |
| book_sess | P7 | nyam | c4_st_15m_sqzk20_fw_1_3 | 661 | -0.144 | 0.007 | -49 | -7 | -0.175 | -2.9 | 2.9 | 1.00 | 1.00 | 2023:-0.24 2024:-0.13 2025:-0.17 2026:-0.18 | -0.353 |
| book_sess | K7 | pre | c4_st_15m_sqzk15_slope_against | 302 | 0.133 | -0.001 | 0 | 0 | 0.197 | 2.9 | 2.3 | 1.00 | 0.98 | 2023:na 2024:+0.46 2025:+0.29 2026:+0.00 | 0.076 |
| book_sess | K7 | pre | c4_st_15m_sqzk20_slope_against | 302 | 0.133 | -0.001 | 0 | 0 | 0.197 | 2.9 | 2.3 | 1.00 | 0.99 | 2023:na 2024:+0.46 2025:+0.29 2026:+0.00 | 0.076 |
| book_sess | K7 | pre | c4_st_15m_sqzk20_slope_with | 634 | -0.064 | -0.001 | 0 | 0 | -0.197 | -2.9 | 2.3 | 1.00 | 0.99 | 2023:na 2024:-0.46 2025:-0.29 2026:-0.00 | -0.076 |
| book_sess | K7 | pre | c4_st_15m_sqzk10_slope_against | 302 | 0.133 | -0.001 | 0 | 0 | 0.197 | 2.9 | 2.3 | 1.00 | 1.00 | 2023:na 2024:+0.46 2025:+0.29 2026:+0.00 | 0.076 |
| book_sess | K7 | pre | c4_st_15m_sqzk10_slope_with | 634 | -0.064 | -0.001 | 0 | 0 | -0.197 | -2.9 | 2.3 | 1.00 | 0.99 | 2023:na 2024:-0.46 2025:-0.29 2026:-0.00 | -0.076 |
| book_sess | K7 | pre | c4_st_15m_sqzk15_slope_with | 634 | -0.064 | -0.001 | 0 | 0 | -0.197 | -2.9 | 2.3 | 1.00 | 0.98 | 2023:na 2024:-0.46 2025:-0.29 2026:-0.00 | -0.076 |
| book_sess | K7 | nyam | c4_st_5m_rsi14_xin_against | 277 | -0.086 | 0.006 | -24 | 5 | -0.101 | -2.8 | 2.3 | 0.97 | 1.00 | 2023:-0.10 2024:-0.07 2025:-0.01 2026:-0.25 | -0.249 |
| ALL |  |  | c4_st_15m_sqzk20_fw_1_3 | 8516 | -0.032 | 0.019 | 6 | 26 | -0.056 | -2.8 | 2.3 | 1.00 | 1.00 | 2023:-0.06 2024:-0.06 2025:-0.08 2026:-0.02 | -0.084 |
| sess |  | pre | c4_st_5m_rsi14_xin_against | 620 | -0.161 | -0.004 | 0 | 0 | -0.177 | -2.8 | 2.8 | 1.00 | 1.00 | 2023:-0.45 2024:-0.12 2025:-0.17 2026:-0.06 | -0.003 |
| sess |  | nypm | c4_st_1m_sqzk15_fa_4_8 | 280 | -0.146 | -0.001 | 11 | 4 | -0.148 | -2.7 | 2.4 | 1.00 | 1.00 | 2023:-0.01 2024:-0.21 2025:-0.15 2026:-0.18 | -0.053 |
| book_sess | P7 | london | c4_st_1m_stoch14_xin_with | 581 | 0.132 | 0.017 | 92 | 8 | 0.130 | 2.7 | 2.2 | 1.00 | 1.00 | 2023:+0.13 2024:+0.10 2025:+0.14 2026:+0.14 | 0.109 |
| sess |  | nyam | c4_st_15m_rsi2_xin_against | 4082 | -0.030 | 0.023 | -12 | 8 | -0.068 | -2.7 | 2.0 | 1.00 | 0.99 | 2023:-0.14 2024:-0.01 2025:-0.08 2026:-0.07 | -0.018 |
| book_sess | P7 | close | c4_st_1m_macd_against_falling | 633 | 0.076 | 0.004 | 0 | 0 | 0.082 | 2.6 | 2.6 | 0.99 | 0.95 | 2023:+0.08 2024:+0.03 2025:+0.03 2026:+0.19 | 0.202 |
| book_sess | A7 | close | c4_st_15m_sqzk15_fw_9p | 783 | -0.118 | -0.023 | 0 | 0 | -0.179 | -2.6 | 2.4 | 1.00 | 0.97 | 2023:-0.16 2024:-0.21 2025:-0.05 2026:-0.32 | -0.718 |
| sess |  | close | c4_st_60m_stoch14_xin_with | 1649 | -0.105 | 0.001 | 0 | 0 | -0.122 | -2.5 | 2.5 | 1.00 | 1.00 | 2023:-0.06 2024:-0.21 2025:-0.00 2026:-0.16 | -0.077 |
| book | H7 |  | c4_st_60m_cci20_xin_against | 303 | 0.179 | 0.046 | 72 | 52 | 0.147 | 2.5 | 2.4 | 1.00 | 0.97 | 2023:+0.15 2024:+0.22 2025:+0.10 2026:+0.13 | 0.273 |
| book_sess | P7 | pre | c4_st_15m_sqzk10_none30 | 1302 | 0.073 | 0.026 | 0 | 0 | 0.216 | 2.5 | 2.4 | 1.00 | 1.00 | 2023:+0.43 2024:+0.34 2025:+0.17 2026:+0.07 | 0.208 |
| book | M7 |  | c4_st_5m_stoch14_xin_against | 2353 | -0.025 | 0.008 | 19 | 4 | -0.039 | -2.4 | 2.2 | 0.98 | 0.98 | 2023:-0.08 2024:-0.03 2025:-0.03 2026:-0.04 | -0.014 |
| sess |  | nyam | c4_st_5m_rsi2_ext_with | 128 | -0.259 | 0.023 | -10 | 8 | -0.284 | -2.3 | 2.0 | 0.99 | 1.00 | 2023:na 2024:na 2025:-0.14 2026:-0.43 | -0.474 |
| book | M7 |  | c4_st_60m_macd_slope_against | 4063 | 0.050 | 0.008 | 10 | 4 | 0.055 | 2.3 | 2.2 | 1.00 | 0.95 | 2023:+0.08 2024:+0.05 2025:+0.06 2026:+0.04 | 0.080 |
| book | P7 |  | c4_st_15m_sqzk15_on_1_5 | 3021 | -0.036 | 0.018 | -3 | 34 | -0.060 | -2.2 | 2.2 | 1.00 | 0.98 | 2023:-0.09 2024:-0.07 2025:-0.06 2026:-0.05 | -0.028 |
| sess |  | nyam | c4_st_15m_sqzk10_fw_4_8 | 635 | -0.163 | 0.023 | -21 | 8 | -0.193 | -2.0 | 2.0 | 1.00 | 0.96 | 2023:-0.24 2024:-0.16 2025:-0.22 2026:-0.17 | -0.282 |

## All other passing tests (expectancy beats matched random, drawdown does not)

| cell | book | sess | state | n yes | lift R | zw | pct expect | pct DD | by year lift |
|---|---|---|---|---|---|---|---|---|---|
| book_sess | U7 | nyam | c4_st_1m_cci20_ext_against | 427 | -0.237 | -4.1 | 0.99 | 0.92 | 2023:na 2024:-0.41 2025:-0.13 2026:na |
| book_sess | U7 | nyam | c4_st_1m_cci20_mid | 143 | 0.237 | 4.1 | 0.99 | 0.86 | 2023:na 2024:+0.41 2025:+0.13 2026:na |
| sess |  | close | c4_st_5m_sqzk15_fa_1_3 | 176 | 0.220 | 4.1 | 1.00 | 0.89 | 2023:na 2024:+0.30 2025:+0.06 2026:+0.47 |
| book_sess | P7 | nypm | c4_st_1m_sqzk15_fa_4_8 | 160 | -0.135 | -4.0 | 0.95 | 0.94 | 2023:-0.12 2024:-0.14 2025:-0.16 2026:-0.11 |
| sess |  | london | c4_st_agree_C_eq4 | 1225 | -0.069 | -3.8 | 1.00 | 0.91 | 2023:-0.03 2024:-0.05 2025:-0.10 2026:-0.08 |
| book_sess | K7 | nyam | c4_st_60m_sqzk20_on_1_5 | 757 | -0.126 | -3.6 | 1.00 | 0.94 | 2023:-0.23 2024:-0.10 2025:-0.12 2026:-0.12 |
| ALL |  |  | c4_st_60m_stoch14_xin_with | 11522 | -0.050 | -3.5 | 1.00 | 0.35 | 2023:-0.06 2024:-0.07 2025:-0.03 2026:-0.04 |
| sess |  | london | c4_st_1m_sqzk15_fa_4_8 | 234 | 0.216 | 3.4 | 1.00 | 0.94 | 2023:na 2024:+0.02 2025:+0.17 2026:+0.27 |
| book | M7 |  | c4_st_60m_stoch14_xin_with | 2362 | -0.086 | -3.4 | 1.00 | 0.49 | 2023:-0.14 2024:-0.06 2025:-0.07 2026:-0.09 |
| book | P7 |  | c4_st_60m_sqzk20_fa_1_3 | 1039 | -0.117 | -3.3 | 1.00 | 0.87 | 2023:-0.13 2024:-0.03 2025:-0.12 2026:-0.17 |
| book_sess | K7 | pre | c4_st_5m_cci20_xin_with | 138 | 0.184 | 3.2 | 0.98 | 0.83 | 2023:na 2024:+0.33 2025:+0.06 2026:+0.30 |
| book_sess | M7 | pre | c4_st_60m_macd_hist_against | 443 | 0.313 | 3.2 | 1.00 | 0.39 | 2023:+0.08 2024:+0.07 2025:+0.48 2026:+0.41 |
| book_sess | M7 | pre | c4_st_60m_macd_hist_with | 837 | -0.313 | -3.2 | 1.00 | 0.47 | 2023:-0.08 2024:-0.07 2025:-0.48 2026:-0.41 |
| book_sess | P7 | london | c4_st_5m_sqzk10_mom_with_slope_against | 1610 | 0.094 | 3.2 | 1.00 | 0.90 | 2023:+0.14 2024:+0.21 2025:+0.15 2026:+0.00 |
| book_sess | P7 | london | c4_st_5m_sqzk15_mom_with_slope_against | 1610 | 0.094 | 3.2 | 1.00 | 0.86 | 2023:+0.14 2024:+0.21 2025:+0.15 2026:+0.00 |
| book_sess | P7 | london | c4_st_5m_sqzk20_mom_with_slope_against | 1610 | 0.094 | 3.2 | 1.00 | 0.87 | 2023:+0.14 2024:+0.21 2025:+0.15 2026:+0.00 |
| book_sess | M7 | pre | c4_st_15m_sqzk20_on_6_12 | 205 | 0.251 | 3.2 | 1.00 | 0.91 | 2023:na 2024:+0.32 2025:+0.12 2026:+0.44 |
| sess |  | close | c4_st_5m_sqzk20_fa_1_3 | 97 | 0.175 | 3.2 | 0.96 | 0.61 | 2023:na 2024:+0.10 2025:na 2026:+0.38 |
| book_sess | A7 | nypm | c4_st_agree_C_eq4 | 390 | -0.085 | -3.1 | 1.00 | 0.67 | 2023:-0.11 2024:-0.10 2025:-0.03 2026:-0.10 |
| book_sess | K7 | nyam | c4_st_agree_B_eq0 | 116 | 0.275 | 3.1 | 1.00 | 0.89 | 2023:na 2024:+0.27 2025:+0.43 2026:na |
| sess |  | close | c4_st_60m_rsi2_ext_against | 3250 | -0.049 | -3.1 | 1.00 | 0.68 | 2023:-0.08 2024:-0.00 2025:-0.06 2026:-0.05 |
| book | M7 |  | c4_st_60m_sqzk15_fa_4_8 | 924 | -0.100 | -3.1 | 1.00 | 0.93 | 2023:-0.08 2024:-0.16 2025:-0.08 2026:-0.07 |
| ALL |  |  | c4_st_60m_rsi14_ext_against | 11824 | 0.094 | -3.1 | 1.00 | 0.02 | 2023:+0.12 2024:+0.16 2025:+0.02 2026:+0.09 |
| book | H7 |  | c4_st_agree_C_eq1 | 832 | 0.119 | 3.1 | 1.00 | 0.91 | 2023:+0.13 2024:+0.13 2025:+0.20 2026:+0.04 |
| sess |  | asia | c4_st_5m_sqzk10_mom_against_slope_with | 1828 | -0.080 | -3.0 | 1.00 | 0.17 | 2023:-0.02 2024:-0.17 2025:-0.10 2026:-0.04 |
| sess |  | asia | c4_st_5m_sqzk20_mom_against_slope_with | 1828 | -0.080 | -3.0 | 1.00 | 0.16 | 2023:-0.02 2024:-0.17 2025:-0.10 2026:-0.04 |
| sess |  | asia | c4_st_5m_sqzk15_mom_against_slope_with | 1828 | -0.080 | -3.0 | 1.00 | 0.20 | 2023:-0.02 2024:-0.17 2025:-0.10 2026:-0.04 |
| book_sess | H7 | london | c4_st_5m_sqzk15_fa_9p | 121 | 0.168 | 3.0 | 0.96 | 0.90 | 2023:na 2024:na 2025:+0.25 2026:+0.21 |
| book_sess | A7 | nyam | c4_st_60m_sqzk15_on_1_5 | 713 | -0.209 | -3.0 | 1.00 | 0.84 | 2023:-0.30 2024:-0.26 2025:-0.22 2026:-0.10 |
| sess |  | nypm | c4_st_60m_sqzk20_fa_1_3 | 873 | -0.166 | -3.0 | 1.00 | 0.94 | 2023:-0.27 2024:-0.15 2025:-0.11 2026:-0.09 |
| book | M7 |  | c4_st_15m_sqzk15_fw_9p | 6736 | -0.035 | -3.0 | 1.00 | 0.48 | 2023:-0.01 2024:-0.05 2025:-0.03 2026:-0.04 |
| book | P7 |  | c4_st_60m_sqzk20_fa_4_8 | 1876 | -0.100 | -2.9 | 1.00 | 0.10 | 2023:-0.02 2024:-0.24 2025:-0.04 2026:-0.10 |
| book_sess | K7 | nypm | c4_st_60m_rsi14_mid | 2219 | -0.160 | -2.9 | 1.00 | 0.92 | 2023:-0.19 2024:-0.10 2025:-0.17 2026:-0.18 |
| sess |  | london | c4_st_5m_sqzk20_mom_with_slope_against | 4151 | 0.066 | 2.9 | 1.00 | 0.36 | 2023:+0.12 2024:+0.16 2025:+0.08 2026:+0.00 |
| sess |  | london | c4_st_5m_sqzk15_mom_with_slope_against | 4151 | 0.066 | 2.9 | 1.00 | 0.41 | 2023:+0.12 2024:+0.16 2025:+0.08 2026:+0.00 |
| sess |  | london | c4_st_5m_sqzk10_mom_with_slope_against | 4151 | 0.066 | 2.9 | 1.00 | 0.42 | 2023:+0.12 2024:+0.16 2025:+0.08 2026:+0.00 |
| book | H7 |  | c4_st_15m_macd_with_rising | 1862 | -0.102 | -2.9 | 1.00 | 0.51 | 2023:-0.01 2024:-0.21 2025:-0.14 2026:-0.02 |
| sess |  | nyam | c4_st_60m_sqzk20_fa_1_3 | 900 | -0.104 | -2.8 | 1.00 | 0.93 | 2023:-0.01 2024:-0.04 2025:-0.16 2026:-0.15 |
| book | P7 |  | c4_st_15m_sqzk20_fw_1_3 | 2802 | -0.076 | -2.8 | 1.00 | 0.94 | 2023:-0.08 2024:-0.08 2025:-0.12 2026:-0.03 |
| book_sess | M7 | nyam | c4_st_15m_sqzk15_mom_with_slope_with | 2152 | -0.057 | -2.8 | 0.99 | 0.74 | 2023:-0.08 2024:-0.02 2025:-0.10 2026:-0.02 |

D10 / D7-live note: every state uses only D7's own completed 1/5/15/60-min bars, so D7 can compute all of them live today.
