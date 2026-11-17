# DS3_BAR_PROPS - property screen of every W-BAR bar type x size x session (descriptive; no book fitted)
VERDICT (data ends 2026-11-13; pick window: none, descriptive screen; trailing 6M = 2026-05-13 .. 2026-11-13, 3M beside it, years secondary; refit: with each 2-week book refit): see five lines below. PREREG_BAR_PROPS.md (sha in DECISIONS.md). Trials counted: 1034 (series x session) rows x 2 rules (momentum/reversal) as one family; correction BH on |t| in the table; in-sample screen, NOT a pick.

1. Tried: 259 bar series (all W-BAR registry rows built so far) x 4 sessions: bars per session, serial correlation lag 1-5, efficiency ratio, variance ratio, and a plain momentum/reversal rule filled on the next bar open (tape-style).
2. Holds: 43 of 1034 (series,session) rows have L3M and L6M agreeing in sign, >=3 of 4 years agreeing and |t(L6M)|>=2.5 (about 12 expected by chance at |t|>2.5 ignoring clustering, so read only the clusters of neighbouring sizes).
3. Does not: most clocks have lag-1 autocorrelation within +-0.05 and variance ratio near 1; a rule with mean < ~1.2 ticks per trade does not pay $4.84 RT + slippage.
4. Needs in DS7: nothing yet; W-SWA/W-SWB start from the "carry" rows below for the swap tests (neighbours of the same type must agree).
5. Next: complete the registry builds (information/price types), refresh this page every 3 h, then book-on-bar.

## Reference (1-minute time bars, REFERENCE ONLY)
| session   |   bars_per_sess_ALL |   ac1_ALL |   er20_ALL |   vr5_ALL |   mom_t_L6M |   mom_ticks_L6M |   mom_t_L3M |   yr_agree |
|:----------|--------------------:|----------:|-----------:|----------:|------------:|----------------:|------------:|-----------:|
| Asia      |               478.4 |    -0.009 |      0.217 |     0.991 |       0.301 |           0.039 |       1.81  |          3 |
| London    |               389   |     0     |      0.219 |     0.975 |      -0.745 |          -0.115 |       1.561 |          2 |
| NYAM      |               148.9 |     0.002 |      0.225 |     1.002 |      -0.338 |          -0.188 |      -1.524 |          3 |
| NYPM      |               232.7 |    -0.009 |      0.22  |     1.01  |       0.44  |           0.124 |       1.552 |          2 |

## London: top 25 series by |t| of the plain rule on trailing 6M (rule = sign of the sign of t)
| series     | rule     |   bars_per_sess_L6M |   mom_t_L6M |   mom_ticks_L6M |   mom_t_L3M |   mom_ticks_L3M |   yr_agree |   ac1_L6M |   er20_L6M |   vr5_L6M | carry   |
|:-----------|:---------|--------------------:|------------:|----------------:|------------:|----------------:|-----------:|----------:|-----------:|----------:|:--------|
| time_s_20  | reversal |              1165.9 |      -4.382 |          -0.189 |      -2.852 |          -0.177 |          4 |    -0.025 |      0.225 |     0.97  | True    |
| time_s_30  | reversal |               778.2 |      -3.508 |          -0.274 |      -0.857 |          -0.088 |          2 |    -0.019 |      0.226 |     0.997 | False   |
| lbrk_5_40  | momentum |                10.5 |       3.208 |          16.331 |       3.102 |          21.961 |          4 |     0.096 |      0.428 |     1.56  | True    |
| dib_240    | momentum |              1293.2 |       3.12  |           0.132 |       2.451 |           0.147 |          4 |    -0.003 |      0.238 |     0.997 | True    |
| frenko_112 | reversal |                 8.6 |      -3.052 |         -16.19  |      -2.029 |         -10.468 |          4 |    -0.093 |      0.186 |     0.905 | True    |
| vib_240    | momentum |              1301.6 |       2.955 |           0.125 |       2.215 |           0.131 |          4 |    -0.003 |      0.239 |     1.001 | True    |
| time_s_15  | reversal |              1549.5 |      -2.881 |          -0.097 |      -3.002 |          -0.15  |          4 |    -0.024 |      0.226 |     0.962 | True    |
| time_m_15  | reversal |                25   |      -2.721 |          -6.216 |      -0.537 |          -1.761 |          4 |    -0.029 |      0.211 |     0.962 | True    |
| time_s_10  | reversal |              2297.9 |      -2.688 |          -0.058 |      -1.723 |          -0.049 |          4 |    -0.03  |      0.221 |     0.937 | True    |
| time_s_5   | reversal |              4321.4 |      -2.597 |          -0.042 |      -1.383 |          -0.026 |          4 |    -0.042 |      0.216 |     0.927 | True    |
| frenko_40  | reversal |                68.3 |      -2.464 |          -1.924 |      -2.508 |          -2.472 |          4 |    -0.018 |      0.186 |     1.01  | False   |
| tsf_5_400  | reversal |                 9.1 |      -2.445 |         -10.807 |      -1.826 |         -12.088 |          1 |    -0.045 |      0.221 |     1.261 | False   |
| time_s_45  | reversal |               518.8 |      -2.354 |          -0.27  |      -0.105 |          -0.016 |          3 |    -0.008 |      0.229 |     0.975 | False   |
| dol_350    | reversal |               162.1 |      -2.326 |          -0.748 |      -1.09  |          -0.512 |          2 |    -0.019 |      0.221 |     0.964 | False   |
| time_m_30  | reversal |                12   |      -2.279 |          -8.593 |      -0.645 |          -3.188 |          3 |    -0.044 |    nan     |     0.857 | False   |
| lbrk_4_20  | momentum |                32.1 |       2.111 |           3.563 |       2.337 |           4.726 |          4 |     0.041 |      0.271 |     1.107 | False   |
| time_m_2   | reversal |               194   |      -2.076 |          -0.554 |      -2.168 |          -0.766 |          4 |    -0.017 |      0.213 |     0.958 | False   |
| frenko_56  | reversal |                35   |      -2.069 |          -3.331 |      -1.118 |          -1.995 |          4 |    -0.035 |      0.178 |     0.942 | False   |
| tib_240    | momentum |              1185.1 |       2.036 |           0.088 |       2.757 |           0.129 |          4 |    -0.004 |      0.232 |     0.982 | False   |
| lbrk_4_40  | momentum |                11.4 |       2.029 |           9.247 |       2.281 |          14.674 |          4 |     0.032 |      0.304 |     1.225 | False   |
| vib_10000  | momentum |                61.1 |       1.993 |           1.536 |       0.785 |           0.811 |          3 |     0.008 |      0.197 |     0.977 | False   |
| vsess_200  | reversal |               213.1 |      -1.894 |          -0.54  |      -1.66  |          -0.69  |          3 |    -0.014 |      0.224 |     0.977 | False   |
| cdr_400    | reversal |                 8.8 |      -1.886 |         -11.163 |      -1.247 |          -9.633 |          2 |    -0.054 |    nan     |     1.511 | False   |
| vnorm_700  | reversal |               126.3 |      -1.878 |          -0.909 |      -0.045 |          -0.03  |          3 |    -0.01  |      0.217 |     0.98  | False   |
| mom_20     | reversal |               137.7 |      -1.868 |          -0.719 |      -1.775 |          -0.839 |          3 |    -0.026 |      0.172 |     0.947 | False   |

## NYAM: top 25 series by |t| of the plain rule on trailing 6M (rule = sign of the sign of t)
| series     | rule     |   bars_per_sess_L6M |   mom_t_L6M |   mom_ticks_L6M |   mom_t_L3M |   mom_ticks_L3M |   yr_agree |   ac1_L6M |   er20_L6M |   vr5_L6M | carry   |
|:-----------|:---------|--------------------:|------------:|----------------:|------------:|----------------:|-----------:|----------:|-----------:|----------:|:--------|
| vib_240    | momentum |              4713.1 |       5.52  |           0.117 |       4.568 |           0.114 |          4 |    -0.002 |      0.238 |     0.988 | True    |
| dib_240    | momentum |              4700.7 |       5.383 |           0.116 |       4.515 |           0.112 |          4 |    -0.002 |      0.237 |     0.982 | True    |
| dib_400    | momentum |              3194.8 |       4.845 |           0.137 |       4.251 |           0.138 |          4 |    -0.002 |      0.236 |     0.979 | True    |
| vib_400    | momentum |              3208.5 |       4.759 |           0.134 |       4.198 |           0.131 |          4 |    -0.003 |      0.236 |     0.985 | True    |
| tib_240    | momentum |              4162.2 |       4.36  |           0.097 |       2.172 |           0.054 |          4 |    -0.006 |      0.231 |     0.981 | True    |
| time_s_30  | reversal |               297.6 |      -3.499 |          -1.065 |      -3.365 |          -1.206 |          3 |    -0.014 |      0.226 |     0.978 | True    |
| dol_1700   | reversal |               133.8 |      -2.978 |          -1.8   |      -2.338 |          -1.76  |          4 |    -0.03  |      0.229 |     0.968 | True    |
| frenko_10  | momentum |              2206.4 |       2.932 |           0.177 |       1.762 |           0.087 |          4 |     0.051 |      0.189 |     1.051 | True    |
| tib_400    | momentum |              2728.4 |       2.909 |           0.103 |       1.513 |           0.055 |          4 |    -0.008 |      0.227 |     0.975 | True    |
| rng_10     | momentum |              1932   |       2.868 |           0.194 |       1.669 |           0.103 |          4 |     0.141 |      0.22  |     1.198 | True    |
| vnorm_700  | reversal |               297.4 |      -2.789 |          -0.793 |      -1.831 |          -0.634 |          2 |    -0.018 |      0.221 |     0.981 | False   |
| vnorm_1000 | reversal |               423.1 |      -2.545 |          -0.434 |      -1.591 |          -0.38  |          3 |    -0.015 |      0.228 |     0.982 | True    |
| time_m_3   | reversal |                48.8 |      -2.395 |          -3.511 |      -0.883 |          -1.701 |          3 |    -0.011 |      0.23  |     1.107 | False   |
| cusum_10   | momentum |              1983.5 |       2.303 |           0.146 |       0.928 |           0.054 |          4 |    -0.015 |      0.19  |     0.976 | False   |
| vrb_2000   | reversal |               146.6 |      -2.159 |          -1.222 |      -2.724 |          -1.934 |          2 |    -0.016 |      0.227 |     0.981 | False   |
| rng_14     | momentum |              1050.8 |       2.143 |           0.22  |      -0.392 |          -0.034 |          4 |     0.107 |      0.209 |     1.14  | False   |
| tsf_2_700  | reversal |               145.6 |      -2.086 |          -1.09  |      -0.907 |          -0.58  |          2 |    -0.025 |      0.229 |     0.962 | False   |
| vib_1200   | momentum |              1388.9 |       2.073 |           0.122 |       1.37  |           0.106 |          4 |    -0.007 |      0.226 |     0.977 | False   |
| cusum_14   | momentum |              1077.2 |       2.063 |           0.212 |      -0.25  |          -0.023 |          4 |    -0.009 |      0.189 |     0.973 | False   |
| dlt_400    | reversal |                28.7 |      -2.034 |          -5.593 |       0.446 |           1.6   |          2 |    -0.032 |      0.219 |     0.998 | False   |
| vrb_240    | momentum |              2628.5 |       2.005 |           0.068 |       1.552 |           0.049 |          4 |    -0.008 |      0.227 |     0.98  | False   |
| tsf_5_1200 | momentum |                15.1 |       1.983 |           9.641 |       1.292 |           7.399 |          3 |     0.06  |      0.266 |     1.167 | False   |
| vol_2600   | reversal |                94.4 |      -1.94  |          -1.659 |      -1.165 |          -0.971 |          4 |    -0.024 |      0.226 |     0.982 | False   |
| vol_1700   | reversal |               144.5 |      -1.924 |          -1.131 |      -1.796 |          -1.197 |          4 |    -0.02  |      0.228 |     0.989 | False   |
| tsf_5_100  | reversal |               173.5 |      -1.922 |          -0.882 |      -1.641 |          -0.733 |          1 |    -0.017 |      0.24  |     0.972 | False   |

## NYPM: top 25 series by |t| of the plain rule on trailing 6M (rule = sign of the sign of t)
| series     | rule     |   bars_per_sess_L6M |   mom_t_L6M |   mom_ticks_L6M |   mom_t_L3M |   mom_ticks_L3M |   yr_agree |   ac1_L6M |   er20_L6M |   vr5_L6M | carry   |
|:-----------|:---------|--------------------:|------------:|----------------:|------------:|----------------:|-----------:|----------:|-----------:|----------:|:--------|
| vib_240    | momentum |              3673.7 |       5.987 |           0.129 |       4.887 |           0.14  |          4 |    -0.003 |      0.235 |     0.994 | True    |
| dib_240    | momentum |              3666.6 |       5.971 |           0.129 |       4.893 |           0.14  |          4 |    -0.002 |      0.234 |     0.986 | True    |
| tib_240    | momentum |              3117.9 |       3.846 |           0.09  |       3.108 |           0.1   |          4 |    -0.009 |      0.227 |     0.981 | True    |
| lbrk_5_40  | momentum |                12   |       3.373 |          15.889 |       2.371 |          13.878 |          4 |     0.066 |      0.302 |     1.19  | True    |
| time_s_20  | reversal |               702.2 |      -3.178 |          -0.295 |      -1.511 |          -0.173 |          4 |    -0.009 |      0.22  |     1.041 | True    |
| dib_400    | momentum |              2513.2 |       3.056 |           0.096 |       3.056 |           0.111 |          4 |    -0.008 |      0.231 |     0.98  | True    |
| vib_400    | momentum |              2521.6 |       2.916 |           0.093 |       2.911 |           0.104 |          4 |    -0.009 |      0.231 |     0.985 | True    |
| time_m_4   | reversal |                57.6 |      -2.682 |          -2.752 |      -2.082 |          -2.643 |          3 |    -0.027 |      0.221 |     0.999 | True    |
| lbrk_5_20  | momentum |                34.1 |       2.488 |           3.883 |       0.404 |           0.921 |          4 |     0.023 |      0.32  |     1.127 | False   |
| time_m_5   | reversal |                45.9 |      -2.424 |          -3.21  |      -2.131 |          -3.559 |          2 |    -0.025 |      0.209 |     1.01  | False   |
| lbrk_4_40  | momentum |                13.3 |       2.307 |          10.244 |       1.039 |           5.785 |          4 |     0.039 |      0.27  |     1.155 | False   |
| time_s_30  | reversal |               467.8 |      -2.271 |          -0.368 |      -1.582 |          -0.318 |          4 |     0.003 |      0.223 |     1.021 | False   |
| tsf_25_80  | reversal |                14.6 |      -2.199 |          -7.795 |      -1.681 |          -8.607 |          2 |    -0.002 |      0.323 |     1.065 | False   |
| lbrk_4_20  | momentum |                40.7 |       2.161 |           3.057 |       1.389 |           3.081 |          4 |     0.013 |      0.27  |     1.106 | False   |
| vrb_240    | momentum |              2028.9 |       2.077 |           0.071 |       1.537 |           0.052 |          4 |    -0.007 |      0.224 |     0.978 | False   |
| time_s_10  | reversal |              1404.5 |      -1.974 |          -0.108 |      -1.115 |          -0.057 |          4 |    -0.018 |      0.222 |     0.961 | False   |
| tib_700    | momentum |              1291.4 |       1.965 |           0.109 |       2.102 |           0.14  |          3 |    -0.009 |      0.222 |     0.972 | False   |
| wrenko_112 | momentum |                 3.4 |       1.965 |          43.435 |       0.815 |          23.508 |          4 |     0.099 |      0.154 |     1.203 | False   |
| renko_112  | momentum |                 3.4 |       1.965 |          43.435 |       0.815 |          23.508 |          4 |     0.099 |      0.154 |     1.203 | False   |
| frenko_10  | momentum |              1345.8 |       1.94  |           0.108 |       0.737 |           0.057 |          4 |     0.041 |      0.19  |     1.027 | False   |
| lbrk_3_40  | momentum |                15.5 |       1.923 |           7.056 |       1.135 |           4.988 |          4 |     0.033 |      0.231 |     1.066 | False   |
| vsess_450  | reversal |               471.4 |      -1.898 |          -0.223 |      -0.431 |          -0.057 |          3 |    -0.012 |      0.228 |     0.978 | False   |
| tsf_10_120 | reversal |                39.5 |      -1.898 |          -3.072 |      -1.398 |          -2.562 |          4 |     0.003 |      0.243 |     0.934 | False   |
| time_m_3   | reversal |                77.1 |      -1.832 |          -1.407 |      -2.594 |          -1.95  |          3 |     0.01  |      0.214 |     0.97  | False   |
| tsf_25_40  | reversal |                22.5 |      -1.825 |          -4.73  |      -0.738 |          -2.488 |          2 |     0.001 |      0.299 |     0.994 | False   |

## Asia: top 25 series by |t| of the plain rule on trailing 6M (rule = sign of the sign of t)
| series     | rule     |   bars_per_sess_L6M |   mom_t_L6M |   mom_ticks_L6M |   mom_t_L3M |   mom_ticks_L3M |   yr_agree |   ac1_L6M |   er20_L6M |   vr5_L6M | carry   |
|:-----------|:---------|--------------------:|------------:|----------------:|------------:|----------------:|-----------:|----------:|-----------:|----------:|:--------|
| vib_240    | momentum |              1525.2 |       4.768 |           0.209 |       1.867 |           0.089 |          4 |    -0.001 |      0.235 |     1.004 | True    |
| dib_240    | momentum |              1518.1 |       4.629 |           0.202 |       1.777 |           0.083 |          4 |     0     |      0.236 |     1.003 | True    |
| lbrk_4_20  | momentum |                40.6 |       3.854 |           6.252 |       2.381 |           5.55  |          4 |     0.047 |      0.283 |     1.109 | True    |
| time_s_5   | reversal |              5157   |      -3.36  |          -0.056 |      -0.953 |          -0.021 |          4 |    -0.044 |      0.213 |     0.928 | True    |
| rng_10     | momentum |              1030.5 |       3.307 |           0.212 |       1.661 |           0.136 |          3 |     0.143 |      0.231 |     1.19  | True    |
| wrenko_56  | momentum |                11.7 |       3.262 |          16.884 |       2.251 |          15.39  |          4 |     0.079 |      0.201 |     1.074 | True    |
| renko_56   | momentum |                11.7 |       3.262 |          16.884 |       2.251 |          15.39  |          4 |     0.079 |      0.201 |     1.074 | True    |
| tib_400    | momentum |               950.3 |       3.165 |           0.202 |       1.054 |           0.088 |          3 |     0.001 |      0.225 |     0.987 | True    |
| lbrk_5_20  | momentum |                34.5 |       3.119 |           5.726 |       2.198 |           5.209 |          4 |     0.021 |      0.304 |     1.116 | True    |
| dib_400    | momentum |              1052.6 |       3.109 |           0.181 |       2.304 |           0.176 |          3 |    -0.001 |      0.23  |     0.993 | True    |
| frenko_10  | momentum |              1188.9 |       3.073 |           0.205 |       1.374 |           0.115 |          3 |     0.089 |      0.197 |     1.101 | True    |
| vib_400    | momentum |              1058.4 |       3.043 |           0.177 |       2.105 |           0.167 |          3 |    -0.002 |      0.229 |     0.992 | True    |
| tick_3200  | momentum |                13.3 |       3.019 |          14.436 |       1.795 |           9.533 |          2 |     0.034 |      0.237 |     0.913 | False   |
| time_s_20  | reversal |              1429.2 |      -2.996 |          -0.151 |      -3.353 |          -0.212 |          4 |    -0.023 |      0.223 |     0.953 | True    |
| mrenko_56  | momentum |                14.9 |       2.567 |          10.913 |       1.84  |          10.661 |          4 |     0.056 |      0.165 |     1.1   | True    |
| tsf_10_700 | momentum |                 1.9 |       2.534 |         101.192 |       2.788 |         127.549 |          2 |     0.282 |    nan     |   nan     | False   |
| vrb_3500   | momentum |                14   |       2.507 |           9.998 |       2.053 |          11.053 |          4 |     0.037 |      0.227 |     0.989 | True    |
| dlt_250    | momentum |                14.8 |       2.384 |           9.669 |       2.257 |          10.65  |          2 |     0.063 |      0.291 |     0.999 | False   |
| drb_2000   | momentum |                21   |       2.38  |           6.641 |       1.219 |           4.47  |          4 |     0.029 |      0.239 |     1.033 | False   |
| time_s_10  | reversal |              2790   |      -2.372 |          -0.054 |      -1.361 |          -0.039 |          4 |    -0.031 |      0.216 |     0.946 | False   |
| cusum_10   | momentum |              1041.5 |       2.365 |           0.164 |       1.066 |           0.09  |          3 |    -0.02  |      0.191 |     0.968 | False   |
| tib_240    | momentum |              1428.5 |       2.328 |           0.113 |       0.531 |           0.033 |          3 |    -0.004 |      0.227 |     0.995 | False   |
| cdr_400    | momentum |                10.8 |       2.32  |          14.889 |       2.387 |          17.778 |          3 |     0.058 |      0.27  |     1.055 | False   |
| tsf_2_2000 | momentum |                12.3 |       2.289 |          13.162 |       1.289 |           8.621 |          3 |     0.046 |      0.204 |     1.006 | False   |
| lbrk_3_40  | momentum |                15.6 |       2.288 |          10.309 |       1.615 |           9.139 |          4 |     0.057 |      0.272 |     1.055 | False   |

## Carry rows (L3M and L6M same sign, >=3/4 years same sign, |t L6M|>=2.5), grouped by type and session
| id     | session   | sizes      |   mean_abs_ticks | rule     |
|:-------|:----------|:-----------|-----------------:|:---------|
| dib    | Asia      | 240,400    |             0.19 | momentum |
| dib    | London    | 240        |             0.13 | momentum |
| dib    | NYAM      | 240,400    |             0.13 | momentum |
| dib    | NYPM      | 240,400    |             0.11 | momentum |
| dol    | NYAM      | 1700       |             1.8  | reversal |
| frenko | Asia      | 10         |             0.2  | momentum |
| frenko | London    | 112        |            16.19 | reversal |
| frenko | NYAM      | 10         |             0.18 | momentum |
| lbrk   | Asia      | 4_20,5_20  |             5.99 | momentum |
| lbrk   | London    | 5_40       |            16.33 | momentum |
| lbrk   | NYPM      | 5_40       |            15.89 | momentum |
| mrenko | Asia      | 56         |            10.91 | momentum |
| renko  | Asia      | 56         |            16.88 | momentum |
| rng    | Asia      | 10         |             0.21 | momentum |
| rng    | NYAM      | 10         |             0.19 | momentum |
| tib    | Asia      | 400        |             0.2  | momentum |
| tib    | NYAM      | 240,400    |             0.1  | momentum |
| tib    | NYPM      | 240        |             0.09 | momentum |
| time_m | London    | 15         |             6.22 | reversal |
| time_m | NYPM      | 4          |             2.75 | reversal |
| time_s | Asia      | 20,5       |             0.1  | reversal |
| time_s | London    | 10,15,20,5 |             0.1  | reversal |
| time_s | NYAM      | 30         |             1.07 | reversal |
| time_s | NYPM      | 20         |             0.29 | reversal |
| vib    | Asia      | 240,400    |             0.19 | momentum |
| vib    | London    | 240        |             0.13 | momentum |
| vib    | NYAM      | 240,400    |             0.13 | momentum |
| vib    | NYPM      | 240,400    |             0.11 | momentum |
| vnorm  | NYAM      | 1000       |             0.43 | reversal |
| vrb    | Asia      | 3500       |            10    | momentum |
| wrenko | Asia      | 56         |            16.88 | momentum |

## By-type summary (median over sizes), trailing 6M
| id     | session   |   ac1_L6M |   er20_L6M |   vr5_L6M |   mom_t_L6M |
|:-------|:----------|----------:|-----------:|----------:|------------:|
| cdr    | Asia      |     0.028 |      0.247 |     1.055 |       0.708 |
| cdr    | London    |    -0.002 |      0.234 |     0.996 |      -0.35  |
| cdr    | NYAM      |    -0.012 |      0.222 |     0.984 |      -0.652 |
| cdr    | NYPM      |    -0.009 |      0.225 |     0.986 |      -0.162 |
| cusum  | Asia      |    -0.01  |      0.192 |     0.978 |       1.659 |
| cusum  | London    |    -0.014 |      0.187 |     0.966 |      -0.599 |
| cusum  | NYAM      |    -0.011 |      0.188 |     0.974 |      -0.159 |
| cusum  | NYPM      |    -0.014 |      0.189 |     0.974 |       0.209 |
| dchg   | Asia      |    -0.792 |      0.09  |     0.373 |     nan     |
| dchg   | London    |    -0.808 |      0.09  |     0.37  |     nan     |
| dchg   | NYAM      |    -0.803 |      0.089 |     0.366 |     nan     |
| dchg   | NYPM      |    -0.8   |      0.088 |     0.357 |     nan     |
| dib    | Asia      |     0.001 |      0.221 |     0.998 |       1.232 |
| dib    | London    |    -0.002 |      0.227 |     0.993 |       0.9   |
| dib    | NYAM      |    -0.008 |      0.225 |     0.977 |       0.84  |
| dib    | NYPM      |    -0.009 |      0.224 |     0.98  |       0.982 |
| dlt    | Asia      |    -0.003 |      0.237 |     1.006 |       0.715 |
| dlt    | London    |    -0.005 |      0.236 |     0.983 |       0.293 |
| dlt    | NYAM      |    -0.01  |      0.233 |     0.971 |      -0.007 |
| dlt    | NYPM      |    -0.014 |      0.23  |     0.967 |       0.456 |
| dol    | Asia      |     0.003 |      0.238 |     1.006 |       0.477 |
| dol    | London    |    -0.006 |      0.222 |     0.981 |      -1.198 |
| dol    | NYAM      |    -0.012 |      0.229 |     0.974 |      -0.568 |
| dol    | NYPM      |     0.001 |      0.223 |     0.994 |      -0.076 |
| drb    | Asia      |     0.013 |      0.231 |     1.013 |       0.957 |
| drb    | London    |    -0.003 |      0.221 |     1.005 |      -0.105 |
| drb    | NYAM      |    -0.007 |      0.226 |     0.987 |       0.319 |
| drb    | NYPM      |    -0.011 |      0.223 |     0.988 |       0.125 |
| frenko | Asia      |     0.029 |      0.188 |     1.047 |       0.275 |
| frenko | London    |    -0.003 |      0.186 |     0.995 |      -1.387 |
| frenko | NYAM      |     0.002 |      0.182 |     0.987 |       0.183 |
| frenko | NYPM      |    -0.002 |      0.188 |     1.005 |      -0.255 |
| kagi   | Asia      |    -0.792 |      0.09  |     0.373 |     nan     |
| kagi   | London    |    -0.808 |      0.09  |     0.37  |     nan     |
| kagi   | NYAM      |    -0.803 |      0.089 |     0.366 |     nan     |
| kagi   | NYPM      |    -0.8   |      0.088 |     0.357 |     nan     |
| lbrk   | Asia      |     0.021 |      0.283 |     1.084 |       2.231 |
| lbrk   | London    |     0.022 |      0.271 |     1.07  |       1.528 |
| lbrk   | NYAM      |     0.019 |      0.265 |     1.016 |       0.779 |
| lbrk   | NYPM      |     0.023 |      0.27  |     1.066 |       1.923 |
| mom    | Asia      |    -0.006 |      0.18  |     0.993 |       0.745 |
| mom    | London    |    -0.023 |      0.177 |     0.953 |      -0.853 |
| mom    | NYAM      |    -0.012 |      0.176 |     0.979 |      -0.106 |
| mom    | NYPM      |    -0.01  |      0.177 |     0.991 |       0.421 |
| mrenko | Asia      |     0.028 |      0.192 |     1.036 |       1.381 |
| mrenko | London    |     0.008 |      0.185 |     1.029 |       0.025 |
| mrenko | NYAM      |     0     |      0.182 |     0.991 |      -0.406 |
| mrenko | NYPM      |    -0.002 |      0.187 |     1.019 |       0.208 |
| pnf    | Asia      |    -0.75  |      0.105 |     0.382 |     nan     |
| pnf    | London    |    -0.773 |      0.099 |     0.405 |     nan     |
| pnf    | NYAM      |    -0.758 |      0.098 |     0.392 |     nan     |
| pnf    | NYPM      |    -0.755 |      0.103 |     0.403 |     nan     |
| renko  | Asia      |     0.019 |      0.203 |     1.059 |       1.047 |
| renko  | London    |     0.003 |      0.196 |     1.016 |      -0.084 |
| renko  | NYAM      |     0.006 |      0.199 |     0.998 |       0.134 |
| renko  | NYPM      |     0.007 |      0.197 |     1.035 |       0.869 |
| rng    | Asia      |     0.05  |      0.21  |     1.097 |       1.503 |
| rng    | London    |     0.045 |      0.2   |     1.079 |      -0.557 |
| rng    | NYAM      |     0.032 |      0.199 |     1.06  |      -0.131 |
| rng    | NYPM      |     0.037 |      0.202 |     1.057 |       0.246 |
| swing  | Asia      |    -0.793 |      0.091 |     0.368 |     nan     |
| swing  | London    |    -0.806 |      0.086 |     0.364 |     nan     |
| swing  | NYAM      |    -0.804 |      0.087 |     0.363 |     nan     |
| swing  | NYPM      |    -0.802 |      0.09  |     0.359 |     nan     |
| tib    | Asia      |    -0.005 |      0.22  |     0.984 |       0.462 |
| tib    | London    |    -0.006 |      0.221 |     0.984 |       0.335 |
| tib    | NYAM      |    -0.009 |      0.218 |     0.975 |       0.461 |
| tib    | NYPM      |    -0.011 |      0.219 |     0.976 |       1.342 |
| tick   | Asia      |     0.003 |      0.239 |     1.007 |      -0.012 |
| tick   | London    |    -0.011 |      0.222 |     0.999 |      -1.175 |
| tick   | NYAM      |    -0.005 |      0.228 |     0.981 |      -0.749 |
| tick   | NYPM      |     0.002 |      0.227 |     0.99  |      -0.424 |
| time_m | Asia      |    -0.001 |      0.239 |     1.013 |       0.245 |
| time_m | London    |    -0.017 |      0.213 |     0.958 |      -1.138 |
| time_m | NYAM      |    -0.004 |      0.227 |     1.001 |      -0.551 |
| time_m | NYPM      |    -0.025 |      0.22  |     0.942 |      -0.561 |
| time_s | Asia      |    -0.022 |      0.222 |     0.958 |      -1.612 |
| time_s | London    |    -0.024 |      0.225 |     0.966 |      -2.785 |
| time_s | NYAM      |    -0.01  |      0.225 |     0.978 |      -1.55  |
| time_s | NYPM      |    -0.007 |      0.223 |     1.016 |      -1.525 |
| trb    | Asia      |     0.018 |      0.234 |     1.038 |       0.523 |
| trb    | London    |    -0.015 |      0.217 |     1.019 |      -0.649 |
| trb    | NYAM      |    -0.009 |      0.225 |     0.991 |      -0.275 |
| trb    | NYPM      |    -0.005 |      0.223 |     0.972 |       0.164 |
| tsf    | Asia      |     0.011 |      0.259 |     1.047 |       0.877 |
| tsf    | London    |    -0.007 |      0.253 |     0.984 |      -0.354 |
| tsf    | NYAM      |    -0.002 |      0.243 |     1.015 |      -0.14  |
| tsf    | NYPM      |    -0.002 |      0.243 |     0.991 |      -0.31  |
| urenko | Asia      |     0.019 |      0.183 |     1.037 |       0.905 |
| urenko | London    |    -0.005 |      0.178 |     0.962 |      -0.938 |
| urenko | NYAM      |     0.001 |      0.177 |     0.992 |       0.159 |
| urenko | NYPM      |     0     |      0.178 |     1.01  |       0.157 |
| vib    | Asia      |    -0.001 |      0.223 |     1.005 |       1.06  |
| vib    | London    |    -0.005 |      0.225 |     0.986 |       0.771 |
| vib    | NYAM      |    -0.008 |      0.225 |     0.979 |       0.848 |
| vib    | NYPM      |    -0.008 |      0.225 |     0.984 |       1.164 |
| vnorm  | Asia      |    -0.003 |      0.23  |     0.99  |       0.889 |
| vnorm  | London    |    -0.008 |      0.22  |     0.985 |      -0.913 |
| vnorm  | NYAM      |    -0.01  |      0.22  |     0.989 |      -0.669 |
| vnorm  | NYPM      |    -0.009 |      0.224 |     0.982 |      -0.52  |
| vol    | Asia      |     0     |      0.246 |     1.012 |       0.576 |
| vol    | London    |    -0.011 |      0.222 |     1.003 |      -0.845 |
| vol    | NYAM      |    -0.013 |      0.229 |     0.99  |      -1.161 |
| vol    | NYPM      |     0.001 |      0.228 |     0.977 |       0.264 |
| vrb    | Asia      |     0.011 |      0.231 |     1.01  |       1.087 |
| vrb    | London    |    -0.006 |      0.227 |     0.981 |      -0.58  |
| vrb    | NYAM      |    -0.009 |      0.227 |     0.984 |       0.031 |
| vrb    | NYPM      |    -0.01  |      0.224 |     0.976 |      -0.326 |
| vsess  | Asia      |    -0.005 |      0.235 |     1.001 |       0.137 |
| vsess  | London    |    -0.01  |      0.222 |     0.977 |      -0.673 |
| vsess  | NYAM      |    -0.008 |      0.228 |     0.973 |      -0.74  |
| vsess  | NYPM      |    -0.006 |      0.225 |     0.982 |      -0.677 |
| wrenko | Asia      |     0.019 |      0.203 |     1.059 |       1.047 |
| wrenko | London    |     0.003 |      0.196 |     1.016 |      -0.084 |
| wrenko | NYAM      |     0.006 |      0.199 |     0.998 |       0.134 |
| wrenko | NYPM      |     0.007 |      0.197 |     1.035 |       0.869 |
