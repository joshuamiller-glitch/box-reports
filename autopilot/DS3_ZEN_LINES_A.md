# DS3_ZEN_LINES_A - line registry, equivalence clusters, screened N (D3ZLN, 2026-10-28)

**Verdict line:** descriptive only (no P&L): 666 average lines per timeframe collapse to 2,414 regime clusters (7 timeframes) and 1,133 entry clusters (7 timeframes), 78 non-average lines collapse to 70; the 20/20 spot-checked clusters re-verify (corr > 0.995 and median distance < 2 pt) and 0/6 random cross-cluster rep pairs would have merged, so the screened N for LINES is the plan's upper bound 12,194 (B 7,242 + C 4,712 + D 240) plus the disclosed additions in section 4.

## 1. Counts block (restated from `out/zen/lines_clusters_summary.json`; clustering done by D3ZN0, line paths only, 10:00-14:00 PRE sample, no P&L)

| role:timeframe | bars (to 2025-06-30, from 2023-02) | sample pts | raw lines | undefined | clusters |
|---|---|---|---|---|---|
| regime:time_3m | 284519 | 20000 | 666 | 0 | 209 |
| regime:time_5m | 170712 | 17277 | 666 | 0 | 234 |
| regime:rs10 | 85359 | 8640 | 666 | 0 | 290 |
| regime:time_15m | 56904 | 5759 | 666 | 0 | 306 |
| regime:time_30m | 28455 | 2881 | 666 | 0 | 353 |
| regime:rs60 | 14231 | 1442 | 666 | 0 | 459 |
| regime:rs240 | 3712 | 363 | 666 | 0 | 563 |
| entry:time_1m | 853342 | 20000 | 666 | 0 | 165 |
| entry:time_30s | 1702612 | 20000 | 666 | 0 | 128 |
| entry:time_15s | 3354086 | 20000 | 666 | 0 | 81 |
| entry:time_2m | 426772 | 20000 | 666 | 0 | 193 |
| entry:time_3m | 284519 | 20000 | 666 | 0 | 209 |
| entry:tick_500 | 468027 | 20000 | 666 | 0 | 164 |
| entry:tick_1000 | 233867 | 20000 | 666 | 0 | 193 |
| non-average (L5) + fixed | - | - | 78 | 0 | 70 |

Totals: regime clusters **2414** (of 4,662 raw), entry clusters **1133** (of 4,662 raw), non-average **70** of 78. Clustering is within a timeframe only (identical paths across timeframes are NOT merged: conservative for best-of-N). Long-timeframe cluster counts are inflated because the sample is sparse there (363 points at 240-min) - conservative. Jurik (JMA/RSX) skipped (no public definition); the 'DS4 MA engine' was not found under that name - the on-disk tr1_sig MAMA/FAMA/KAMA/FRAMA recursions are used (MORNING Q7).

## 2. The reference line: EMA 200 close

- 5-min regime: cluster rep `EMA_200_close`, members EMA_200_close, EMA_200_hl2, EMA_200_hlc3, SMMA_100_close, SMMA_100_hl2, SMMA_100_hlc3. This is exactly the T-ZEN regime R1 (checked: `Eng.regime_line('time_5m','EMA_200_close','side')` equals `Z.regimes(ctx)['R1']` on all 86,252 PRE entry bars). Sanity: EMA200 clusters with Wilder SMMA(100) as it should (Wilder 100 = EMA 199).
- 1-min entry line: cluster rep `EMA_200_close`, members EMA_200_close, EMA_200_hl2, EMA_200_hlc3, SMMA_100_close, SMMA_100_hl2, SMMA_100_hlc3.

## 3. Spot-check of 20 random multi-member clusters (random over all 14 role:timeframe sets, seed 20261028; rep vs one random member recomputed from the line formulas on the 10:00-14:00 PRE sample)

| role | tf | rep | members | member checked | corr | median dist (pt) | ok |
|---|---|---|---|---|---|---|---|
| entry | time_30s | TEMA_21_hlc3 | 13 | LSMA_21_hl2 | 0.99999 | 1.743 | yes |
| regime | rs10 | TEMA_100_close | 2 | TEMA_100_hlc3 | 1.00000 | 1.375 | yes |
| regime | rs10 | EMA_200_close | 6 | EMA_200_hl2 | 1.00000 | 0.684 | yes |
| regime | time_5m | SMMA_377_close | 3 | SMMA_377_hl2 | 1.00000 | 0.321 | yes |
| entry | time_30s | ZLEMA_377_close | 3 | ZLEMA_377_hlc3 | 1.00000 | 0.138 | yes |
| regime | time_3m | VWMA_144_close | 6 | RVWAP_144_hl2 | 1.00000 | 0.799 | yes |
| entry | time_2m | HMA_200_close | 3 | HMA_200_hl2 | 1.00000 | 0.709 | yes |
| entry | time_1m | SMA_20_close | 30 | RVWAP_21_close | 0.99999 | 1.164 | yes |
| regime | time_3m | ALMA_377_close | 3 | ALMA_377_hl2 | 1.00000 | 0.387 | yes |
| entry | time_1m | TEMA_233_close | 3 | TEMA_233_hlc3 | 1.00000 | 0.286 | yes |
| regime | time_3m | TEMA_9_hl2 | 3 | ZLEMA_9_hl2 | 1.00000 | 1.573 | yes |
| regime | time_3m | DEMA_9_close | 2 | DEMA_9_hlc3 | 1.00000 | 1.481 | yes |
| regime | time_5m | VWMA_89_close | 6 | RVWAP_89_close | 1.00000 | 1.360 | yes |
| regime | rs60 | TEMA_144_hl2 | 2 | TEMA_144_hlc3 | 1.00000 | 1.149 | yes |
| regime | time_3m | LSMA_89_close | 3 | LSMA_89_hlc3 | 1.00000 | 0.745 | yes |
| regime | time_5m | TEMA_50_close | 3 | TEMA_50_hlc3 | 1.00000 | 1.253 | yes |
| entry | time_15s | ZLEMA_377_close | 3 | ZLEMA_377_hlc3 | 1.00000 | 0.083 | yes |
| entry | time_3m | VIDYA_55_hl2 | 2 | VIDYA_55_hlc3 | 1.00000 | 0.911 | yes |
| entry | tick_1000 | SMMA_89_close | 6 | MCG_144_hl2 | 1.00000 | 0.723 | yes |
| entry | time_30s | LSMA_233_close | 3 | LSMA_233_hl2 | 1.00000 | 0.257 | yes |

20 of 20 pass. Reverse check (6 random pairs of DIFFERENT reps on the same timeframe, which must NOT satisfy the merge rule):

| role | tf | rep A | rep B | corr | median dist | would merge |
|---|---|---|---|---|---|---|
| regime | time_5m | ITREND_0.04_hl2 | FRAMA_144_close | 0.9995 | 14.24 | False |
| entry | time_30s | HMA_200_close | HMA_89_close | 0.9997 | 12.20 | False |
| entry | time_1m | SMA_20_close | WMA_89_close | 0.9997 | 14.03 | False |
| entry | time_3m | KAMA_89_close | FAMA_0_hl2 | 0.9994 | 21.29 | False |
| regime | time_15m | ZLEMA_34_close | ALMA_50_hl2 | 0.9987 | 28.40 | False |
| regime | time_3m | VIDYA_20_close | FAMA_0_close | 0.9997 | 15.51 | False |

## 4. Screened N for the LINES family (honest; copied to the preregs)

| block | formula | N |
|---|---|---|
| B regime search | 2,414 regime clusters x 3 semantics (side; side + 5-bar slope of the line on its own TF; side + |price - line| <= 40) | 7,242 |
| C entry search | 1,133 entry clusters x 2 tolerances (2, 5) x 2 regimes (5m EMA200; best B line) = 4,532; stacks 45 pairs of the top 10 x 2 distances (3, 5) x 2 regimes = 180 | 4,712 |
| D joint + L5 | top 10 x top 10 = 100; L5 non-average 70 clusters x 2 tolerances = 140 | 240 |
| **plan total** | | **12,194** |
| additions disclosed by D3ZLN | D: L5 extras not in the 78-line registry: 1-min swing-low ladder (k = 2, 3) x 2 tol = 4, 5-min FVG midpoint x 2 tol = 2, Fibonacci 50 / 61.8 of the last impulse x 2 tol = 4, opening-range edges OR15 / OR30 x 2 tol = 4 -> **+14**; B/C/D top-30 flat-15:55 re-runs (3 x 30 = 90 reads of cells already counted; counted as +90 conservatively); M4 session variants on the top cells (+10 if run). Neighbour-lookback checks (L6) are robustness reads of at most 40 lines, never used for selection, and not added. | +14 / +90 / +10 |

Program N used for the program-level best-of-N is 291,130 (plan); this family's N for its own reality check is the number of cells actually scored in the stage (stated in B/C/D reports).

## 5. Registry reminder
18 averages (SMA EMA WMA DEMA TEMA HMA ZLEMA T3 KAMA FRAMA VIDYA ALMA LSMA TMA SMMA McGinley VWMA rolling VWAP) x 12 lookbacks (9 20 21 34 50 55 89 100 144 200 233 377) x 3 prices + MAMA/FAMA x 3 + Ehlers instantaneous trendline x 4 alphas x 3 = 666 per timeframe. Regime timeframes 3 / 5 / 10 / 15 / 30 / 60 / 240 min; entry timeframes 1-min, 30-s, 15-s, 2-min, 3-min, 500-tick, 1000-tick. L5/fixed: VWAP (ETH, RTH, week; +-1/2/3 sigma; anchored to the day high/low; overnight), Keltner / Bollinger (20, 50), SuperTrend (10,2), (10,3), (14,3), parabolic SAR x 3, Donchian mid x 13 incl. Kijun 26 / Tenkan 9, prior-day H/L/C, overnight H/L, classic and Camarilla pivots, POC/VAH/VAL. Cluster member lists: `l2vast/ds3/out/zen/lines_clusters_<tf>.json` (members of every representative are listed there; the B/C/D tables carry the rep and its member count).

Files: `l2vast/ds3/out/zen/lines/lines_a_check.json`, `l2vast/ds3/code/zen/lines/zl_a.py`.

DONE LINES_A