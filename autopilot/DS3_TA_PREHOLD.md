# DS3_TA pre-holdout text (D3A) - WF-PRE 2024-02..2025-06 only, holdout and 2023-04..2024-01 span NOT computed
Prereg sha256 09c68b514ee3b5567be78bb05f0a2cee9d8a915d4850816e7311e43c88017be8. 3-lot sizes; marginal Sharpe = change in WF-PRE annualised weekly Sharpe of DS2 books (ST10+HM10+WT7 per-book locks) when the book is added at 3 lots. Placebo lib = rank vs 500 random library books scaled to the same weekly SD; shift = rank vs 500 circular shifts of its own series.

| cell | exec | trades/wk | WF-PRE mean/wk | SD | Sharpe | CI mean | marg Sharpe | plc lib | plc shift |
|---|---|---|---|---|---|---|---|---|---|
| TA_NQ_RSI2C_s20 | DELIVERABLE | 0.49 | 2112 | 11863 | 1.28 | [118,3997] | 0.099 | 0.886 | 0.478 |
| TA_ES_RSI2_t10 | DELIVERABLE | 0.42 | 1655 | 9808 | 1.22 | [611,3327] | 0.082 | 0.890 | 0.500 |
| TA_DIPBUY_ONE | DELIVERABLE | 0.92 | 3768 | 20312 | 1.34 | [1150,6736] | 0.162 | 0.922 | 0.514 |
| TA_NQ_IBS_t20_n1 | DELIVERABLE | 0.75 | 2183 | 20503 | 0.77 | [-598,5260] | 0.130 | 0.858 | 0.334 |
| TA_NQ_RSI2_t10_plain | DELIVERABLE | 0.49 | 2763 | 16533 | 1.21 | [533,5353] | 0.132 | 0.898 | 0.544 |
| TA_NQ_ON_none | DELIVERABLE | 4.67 | 2437 | 23319 | 0.75 | [-3850,6509] | 0.023 | 0.710 | 0.338 |
| TA_GSHORT_t90 | NOT DELIVERABLE | 0.22 | 337 | 5618 | 0.43 | [-652,2380] | 0.016 | 0.764 | 0.442 |
| TA_ORB_ASIA_15_s60 | DELIVERABLE | 0.84 | 382 | 4325 | 0.64 | [-635,1190] | 0.004 | 0.686 | 0.578 |
| TA_ORB_ASIA_15_s75 | DELIVERABLE | 0.84 | 145 | 5353 | 0.20 | [-1168,1034] | -0.014 | 0.532 | 0.442 |
| TA_ORB_ASIA_30_s60 | DELIVERABLE | 0.81 | 277 | 4380 | 0.46 | [-732,1034] | 0.008 | 0.716 | 0.472 |
| TA_WT_LIVE_ATR20_2.0 | DELIVERABLE | 37.39 | 4044 | 18232 | 1.60 | [262,9054] | 0.105 | 0.820 | 0.618 |
| TA_WThist_ATR20_m2_ema100_tf1 | DELIVERABLE | 37.34 | 4135 | 18072 | 1.65 | [539,9007] | 0.113 | 0.846 | 0.754 |
| TA_WThist_ATR10_m3_ema0_tf10 | DELIVERABLE | 4.75 | 2723 | 11158 | 1.76 | [-236,5072] | 0.193 | 0.990 | 0.720 |
| TA_MBO7_composite | NOT DELIVERABLE | 22.23 | 2607 | 18931 | 0.99 | [126,5273] | 0.164 | 0.928 | 0.992 |
| TA_MBO7_H120000_competing_dir_xgboost_Q725 | NOT DELIVERABLE | 1.97 | 3645 | 25709 | 1.02 | [-491,7887] | 0.153 | 0.870 | 0.916 |
| TA_MBO7_H250_tb_long_xgboost_Q750 | NOT DELIVERABLE | 2.78 | 857 | 25480 | 0.24 | [-4328,5136] | 0.019 | 0.712 | 0.592 |
| TA_MBO7_H300000_competing_dir_extratrees_Q575 | NOT DELIVERABLE | 4.47 | -341 | 22710 | -0.11 | [-4312,2711] | -0.021 | 0.644 | 0.104 |
| TA_MBO7_H300000_competing_dir_histgb_Q700 | NOT DELIVERABLE | 3.19 | 2197 | 13179 | 1.20 | [-608,4898] | 0.168 | 0.952 | 0.960 |
| TA_MBO7_H60000_competing_dir_histgb_Q675 | NOT DELIVERABLE | 1.87 | 5078 | 26027 | 1.41 | [784,12857] | 0.290 | 0.974 | 0.936 |
| TA_MBO7_H60000_y_exec_best_catboost_Q625 | NOT DELIVERABLE | 5.23 | 4125 | 25531 | 1.17 | [-2783,8390] | 0.300 | 0.972 | 0.974 |
| TA_MBO7_H60000_y_exec_best_lightgbm_Q700 | NOT DELIVERABLE | 2.72 | 2685 | 24578 | 0.79 | [-348,6447] | 0.111 | 0.822 | 0.934 |
