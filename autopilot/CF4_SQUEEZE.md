# CF4_SQUEEZE - squeeze-on-at-entry columns, fire events and each-alone result by book x session

**Verdict (data ends 2026-11-11) line (): squeeze-on at entry (standard Bollinger-in-Keltner) on 1/5/15-min and the alternate bars: 141 of 20400 each-alone tests pass the full rule (0.69% vs nonsense 0.44%); see the per-cell tables for P7 / K7 / session cells.**
Squeeze-on-at-entry columns + fire events (user priority, for W-CF3).
DEFINITIONS (PUBLIC formula unless stated), evaluated on completed bars of each bar set:
  kc_on   : Bollinger(20,2) inside Keltner(20, 1.5 x SMA20 of true range, SMA20 centre)  [LazyBear / TTM Squeeze; same as c4_sqzm_on]
  kc_on_F / kc_on_S : same with length 12 / 34
  bw20_on / bw10_on : Bollinger bandwidth (BB(20,2) width / SMA20) percentile rank within the previous 250 bars <= 20% / 10%   [APPROXIMATION of 'bandwidth squeeze', thresholds fixed in advance]
  kc_len6 : kc_on and the squeeze has lasted >= 6 bars
  fired   : kc_on turned off on this bar (release); direction = sign of the momentum histogram linreg(close - avg(avg(HH20,LL20),SMA20),20) at the release bar
  fired5_any / fired5_with / fired5_against : a release within the last 5 completed bars (any / in the trade's direction / against)
  mom_with / mom_rise_with : momentum histogram sign with the trade / rising with the trade
Bar sets: time bars 1m,3m,5m,15m,60m and the 12 alternate sets (range8/16, renko8/16, vol500/2000, tick2000, ha1/3/5/15/60). Columns cf4_squeeze.parquet: c4_sqz_<set>_<cond>, key sid=sig_id (1/0/-1). Fire events (for wait-until-it-fires forms): cols_cf4/squeeze_fires/<set>.parquet with tend (epoch s the release bar COMPLETES), dir (+1/-1 momentum sign), on_len (bars the squeeze lasted), kind (kc / kcF / kcS).

COLUMNS (key sid = sig_id, 1 yes / 0 no / -1 unknown; universe 193,245 signals to 2026-11-11): /mnt/l2/l2vast/_confl/cols_cf4/cf4_squeeze.parquet, names c4_sqz_<set>_<cond>, set in 1m,3m,5m,15m,60m,alt_range8,...; cond in on, len6, fired5_any, fired5_with, fired5_against, mom_with, mom_rise_with (standard length 20; suffix F = 12, S = 34), bw20_on, bw10_on, on_or_bw20. Closest to the phrase "squeeze on at entry": c4_sqz_5m_on (and 1m / 15m); the definition uses only market state (on, fired) plus the trade side for the direction columns (fired5_with/against, mom_with).
WAIT FORM (FUTURE-LOOKING by construction, valid only as the entry timing of a "wait until it fires" simulation, never as a condition at the signal second): /mnt/l2/l2vast/_confl/cols_cf4/cf4_squeeze_wait.parquet: c4_sqzwait_<1m|3m|5m|15m|60m>_dt = seconds from the signal to the end of the first standard squeeze release bar after it (NaN if none), _dir = momentum sign at that release, _by5/_by15/_by30 = released within 5/15/30 min after the signal, _by*_with = and the release direction = the trade side. Entry for the wait form = signal second + dt. Raw event list: cols_cf4/squeeze_fires/<set>.parquet (tend, dir, on_len, kind kc/kcF/kcS).

**c4_sqz_1m_on** (each alone; lift in R per signal, weekly cluster-robust zw, nonsense bar99 of the same cell; PASS = full rule)

| cell | book | sess | n yes | share | lift R | zw | bar99 | years pos/n | lift L6M | pass |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 21281 | 0.26 | -0.008 | -0.6 | 2.3 | 2/4 | 0.006 |  |
| book | A7 |  | 2804 | 0.16 | 0.036 | 1.0 | 2.4 | 4/4 | 0.088 |  |
| book | H7 |  | 379 | 0.12 | -0.022 | 0.7 | 2.4 | 2/4 | -0.168 |  |
| book | K7 |  | 2144 | 0.14 | -0.011 | -0.1 | 2.6 | 2/4 | 0.015 |  |
| book | M7 |  | 4098 | 0.25 | -0.016 | -1.5 | 2.2 | 1/4 | 0.041 |  |
| book | O7 |  | 10 | 0.02 | 0.019 | nan | 3.7 | 0/0 | 0.465 |  |
| book | P7 |  | 11703 | 0.42 | -0.011 | -0.5 | 2.2 | 1/4 | -0.035 |  |
| book | U7 |  | 143 | 0.06 | -0.096 | 0.1 | 2.5 | 0/3 | -0.080 |  |
| sess |  | asia | 2173 | 0.20 | -0.005 | -0.5 | 2.8 | 1/4 | -0.050 |  |
| sess |  | london | 3424 | 0.19 | -0.005 | -0.2 | 2.5 | 2/4 | 0.013 |  |
| sess |  | pre | 1438 | 0.26 | 0.024 | 0.4 | 2.8 | 2/4 | 0.085 |  |
| sess |  | nyam | 4365 | 0.25 | -0.026 | -1.3 | 2.0 | 1/4 | -0.083 |  |
| sess |  | nypm | 5999 | 0.31 | -0.001 | 0.5 | 2.4 | 2/4 | 0.047 |  |
| sess |  | close | 3882 | 0.31 | 0.011 | 0.3 | 2.5 | 3/4 | 0.096 |  |

**c4_sqz_5m_on** (each alone; lift in R per signal, weekly cluster-robust zw, nonsense bar99 of the same cell; PASS = full rule)

| cell | book | sess | n yes | share | lift R | zw | bar99 | years pos/n | lift L6M | pass |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 17186 | 0.21 | -0.022 | -1.4 | 2.3 | 1/4 | -0.032 |  |
| book | A7 |  | 1800 | 0.10 | -0.012 | -0.3 | 2.4 | 2/4 | -0.146 |  |
| book | H7 |  | 771 | 0.24 | -0.007 | 0.5 | 2.4 | 2/4 | 0.031 |  |
| book | K7 |  | 3864 | 0.26 | -0.033 | -0.7 | 2.6 | 0/4 | -0.053 |  |
| book | M7 |  | 3877 | 0.23 | -0.013 | -0.4 | 2.2 | 2/4 | -0.004 |  |
| book | O7 |  | 71 | 0.14 | 0.001 | nan | 3.7 | 0/0 | 0.294 |  |
| book | P7 |  | 6585 | 0.24 | -0.026 | -1.3 | 2.2 | 1/4 | -0.015 |  |
| book | U7 |  | 218 | 0.08 | 0.064 | 0.8 | 2.5 | 3/4 | 0.152 |  |
| sess |  | asia | 2077 | 0.19 | -0.025 | -1.1 | 2.8 | 1/4 | 0.092 |  |
| sess |  | london | 3122 | 0.17 | -0.006 | 1.8 | 2.5 | 3/4 | -0.130 |  |
| sess |  | pre | 981 | 0.18 | 0.070 | 1.1 | 2.8 | 3/4 | 0.123 |  |
| sess |  | nyam | 3598 | 0.21 | -0.008 | 1.0 | 2.0 | 2/4 | -0.031 |  |
| sess |  | nypm | 4136 | 0.21 | -0.047 | -0.4 | 2.4 | 0/4 | -0.041 |  |
| sess |  | close | 3272 | 0.26 | -0.044 | -1.3 | 2.5 | 1/4 | -0.043 |  |
| book_sess | M7 | nyam | 856 | 0.24 | 0.059 | 2.0 | 2.6 | 3/4 | 0.046 |  |

**c4_sqz_15m_on** (each alone; lift in R per signal, weekly cluster-robust zw, nonsense bar99 of the same cell; PASS = full rule)

| cell | book | sess | n yes | share | lift R | zw | bar99 | years pos/n | lift L6M | pass |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 17935 | 0.22 | -0.001 | 0.2 | 2.3 | 2/4 | 0.017 |  |
| book | A7 |  | 2382 | 0.14 | -0.005 | 0.6 | 2.4 | 2/4 | 0.017 |  |
| book | H7 |  | 1098 | 0.34 | -0.064 | -1.5 | 2.4 | 0/4 | -0.041 |  |
| book | K7 |  | 3301 | 0.22 | 0.030 | 2.6 | 2.6 | 2/4 | 0.045 |  |
| book | M7 |  | 3900 | 0.24 | 0.044 | 2.2 | 2.2 | 4/4 | 0.083 | PASS |
| book | O7 |  | 127 | 0.25 | -0.239 | -0.5 | 3.7 | 0/3 | 0.001 |  |
| book | P7 |  | 6261 | 0.22 | -0.031 | -0.8 | 2.2 | 1/4 | -0.049 |  |
| book | U7 |  | 866 | 0.33 | -0.020 | -0.8 | 2.5 | 2/4 | 0.100 |  |
| sess |  | asia | 2358 | 0.22 | -0.044 | -1.0 | 2.8 | 0/4 | -0.048 |  |
| sess |  | london | 3583 | 0.20 | 0.014 | 1.5 | 2.5 | 2/4 | 0.071 |  |
| sess |  | pre | 1412 | 0.26 | -0.007 | 0.1 | 2.8 | 2/4 | 0.070 |  |
| sess |  | nyam | 3808 | 0.22 | 0.021 | 2.4 | 2.0 | 2/4 | 0.037 |  |
| sess |  | nypm | 3456 | 0.18 | -0.034 | -0.5 | 2.4 | 1/4 | -0.121 |  |
| sess |  | close | 3318 | 0.26 | 0.026 | 1.2 | 2.5 | 2/4 | 0.106 |  |
| book_sess | A7 | asia | 188 | 0.14 | -0.068 | -2.7 | 2.4 | 1/3 | -0.182 |  |
| book_sess | H7 | nyam | 246 | 0.38 | -0.079 | -2.7 | 2.4 | 1/4 | -0.163 |  |
| book_sess | K7 | nyam | 783 | 0.23 | 0.088 | 3.3 | 2.3 | 4/4 | 0.010 | PASS |
| book_sess | M7 | nyam | 828 | 0.24 | 0.062 | 2.7 | 2.6 | 3/4 | 0.047 |  |

**c4_sqz_1m_fired5_with** (each alone; lift in R per signal, weekly cluster-robust zw, nonsense bar99 of the same cell; PASS = full rule)

| cell | book | sess | n yes | share | lift R | zw | bar99 | years pos/n | lift L6M | pass |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 11051 | 0.13 | -0.009 | -1.3 | 2.3 | 1/4 | -0.020 |  |
| book | A7 |  | 2001 | 0.11 | -0.024 | -0.9 | 2.4 | 1/4 | 0.062 |  |
| book | H7 |  | 252 | 0.08 | -0.068 | -2.2 | 2.4 | 0/4 | -0.018 |  |
| book | K7 |  | 3702 | 0.25 | -0.004 | 0.0 | 2.6 | 1/4 | -0.026 |  |
| book | M7 |  | 2502 | 0.15 | -0.011 | -0.4 | 2.2 | 2/4 | -0.045 |  |
| book | O7 |  | 39 | 0.08 | -0.011 | nan | 3.7 | 0/0 | -0.286 |  |
| book | P7 |  | 2230 | 0.08 | 0.021 | 0.7 | 2.2 | 3/4 | -0.006 |  |
| book | U7 |  | 325 | 0.13 | -0.031 | -0.3 | 2.5 | 2/4 | 0.058 |  |
| sess |  | asia | 1464 | 0.14 | -0.047 | -1.1 | 2.8 | 1/4 | -0.081 |  |
| sess |  | london | 2237 | 0.12 | -0.012 | -0.7 | 2.5 | 1/4 | -0.017 |  |
| sess |  | pre | 722 | 0.13 | 0.016 | 0.3 | 2.8 | 3/4 | -0.168 |  |
| sess |  | nyam | 2399 | 0.14 | 0.002 | 0.7 | 2.0 | 3/4 | 0.052 |  |
| sess |  | nypm | 2548 | 0.13 | -0.038 | -1.7 | 2.4 | 0/4 | -0.085 |  |
| sess |  | close | 1681 | 0.13 | 0.043 | 2.3 | 2.5 | 3/4 | 0.122 |  |
| book_sess | K7 | close | 488 | 0.24 | 0.086 | 2.1 | 2.6 | 3/4 | 0.138 |  |
| book_sess | P7 | nyam | 385 | 0.08 | 0.126 | 2.4 | 2.9 | 4/4 | 0.122 |  |

**c4_sqz_5m_fired5_with** (each alone; lift in R per signal, weekly cluster-robust zw, nonsense bar99 of the same cell; PASS = full rule)

| cell | book | sess | n yes | share | lift R | zw | bar99 | years pos/n | lift L6M | pass |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 11126 | 0.13 | 0.009 | 0.6 | 2.3 | 2/4 | -0.001 |  |
| book | A7 |  | 3063 | 0.18 | 0.021 | 0.7 | 2.4 | 2/4 | 0.046 |  |
| book | H7 |  | 838 | 0.26 | 0.038 | 1.1 | 2.4 | 3/4 | -0.011 |  |
| book | K7 |  | 1335 | 0.09 | 0.013 | 1.4 | 2.6 | 2/4 | 0.014 |  |
| book | M7 |  | 2155 | 0.13 | -0.011 | -0.1 | 2.2 | 2/4 | -0.071 |  |
| book | O7 |  | 102 | 0.20 | 0.202 | nan | 3.7 | 0/1 | 1.335 |  |
| book | P7 |  | 2903 | 0.10 | -0.011 | 0.0 | 2.2 | 2/4 | -0.022 |  |
| book | U7 |  | 730 | 0.28 | -0.021 | -0.1 | 2.5 | 2/4 | -0.014 |  |
| sess |  | asia | 1261 | 0.12 | 0.032 | 0.8 | 2.8 | 4/4 | 0.033 |  |
| sess |  | london | 2768 | 0.15 | 0.046 | 1.4 | 2.5 | 4/4 | -0.008 |  |
| sess |  | pre | 786 | 0.14 | -0.074 | 0.2 | 2.8 | 1/4 | 0.035 |  |
| sess |  | nyam | 2391 | 0.14 | -0.017 | -0.0 | 2.0 | 2/4 | 0.005 |  |
| sess |  | nypm | 2354 | 0.12 | -0.017 | -0.8 | 2.4 | 2/4 | 0.008 |  |
| sess |  | close | 1566 | 0.12 | 0.046 | 0.3 | 2.5 | 3/4 | -0.057 |  |
| book_sess | A7 | asia | 216 | 0.16 | 0.061 | 2.3 | 2.4 | 2/3 | 0.038 |  |

**c4_sqz_15m_fired5_with** (each alone; lift in R per signal, weekly cluster-robust zw, nonsense bar99 of the same cell; PASS = full rule)

| cell | book | sess | n yes | share | lift R | zw | bar99 | years pos/n | lift L6M | pass |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 10871 | 0.13 | -0.008 | -0.8 | 2.3 | 2/4 | -0.063 |  |
| book | A7 |  | 3172 | 0.18 | -0.031 | -1.7 | 2.4 | 1/4 | -0.144 |  |
| book | H7 |  | 306 | 0.09 | -0.004 | 0.5 | 2.4 | 1/4 | -0.167 |  |
| book | K7 |  | 1498 | 0.10 | -0.007 | -0.4 | 2.6 | 2/4 | -0.057 |  |
| book | M7 |  | 2046 | 0.12 | 0.014 | -0.0 | 2.2 | 2/4 | 0.004 |  |
| book | O7 |  | 45 | 0.09 | 0.165 | nan | 3.7 | 0/0 | 0.174 |  |
| book | P7 |  | 3581 | 0.13 | 0.000 | -0.1 | 2.2 | 2/4 | -0.038 |  |
| book | U7 |  | 223 | 0.09 | -0.095 | -1.4 | 2.5 | 0/4 | -0.239 |  |
| sess |  | asia | 1381 | 0.13 | -0.009 | 0.0 | 2.8 | 2/4 | -0.114 |  |
| sess |  | london | 2466 | 0.14 | -0.018 | -1.8 | 2.5 | 2/4 | -0.036 |  |
| sess |  | pre | 822 | 0.15 | -0.094 | -0.7 | 2.8 | 0/4 | -0.292 |  |
| sess |  | nyam | 2822 | 0.16 | -0.038 | -2.4 | 2.0 | 1/4 | -0.115 |  |
| sess |  | nypm | 1635 | 0.08 | 0.050 | -0.7 | 2.4 | 2/4 | 0.106 |  |
| sess |  | close | 1745 | 0.14 | 0.022 | -0.3 | 2.5 | 2/4 | -0.009 |  |
| book_sess | K7 | pre | 98 | 0.10 | -0.242 | -2.4 | 2.3 | 0/1 | -0.339 |  |
| book_sess | U7 | asia | 115 | 0.16 | 0.008 | -2.3 | 2.9 | 1/2 | -0.107 |  |

**c4_sqz_1m_mom_with** (each alone; lift in R per signal, weekly cluster-robust zw, nonsense bar99 of the same cell; PASS = full rule)

| cell | book | sess | n yes | share | lift R | zw | bar99 | years pos/n | lift L6M | pass |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 66729 | 0.80 | -0.006 | -0.5 | 2.3 | 1/4 | -0.004 |  |
| book | A7 |  | 15979 | 0.92 | -0.016 | -0.3 | 2.4 | 1/4 | -0.086 |  |
| book | H7 |  | 2961 | 0.92 | -0.022 | 0.1 | 2.4 | 1/4 | 0.239 |  |
| book | K7 |  | 13067 | 0.87 | -0.015 | -0.8 | 2.6 | 2/4 | 0.014 |  |
| book | M7 |  | 13156 | 0.80 | -0.020 | 0.2 | 2.2 | 1/4 | 0.029 |  |
| book | O7 |  | 511 | 1.00 | -2.023 | nan | 3.7 | 0/0 | nan |  |
| book | P7 |  | 18519 | 0.66 | -0.004 | -0.6 | 2.2 | 1/4 | -0.003 |  |
| book | U7 |  | 2536 | 0.98 | 0.079 | nan | 2.5 | 0/0 | -0.228 |  |
| sess |  | asia | 8351 | 0.78 | -0.042 | -1.5 | 2.8 | 1/4 | -0.013 |  |
| sess |  | london | 14722 | 0.82 | -0.029 | -1.4 | 2.5 | 1/4 | -0.009 |  |
| sess |  | pre | 4290 | 0.79 | -0.012 | -0.3 | 2.8 | 1/4 | 0.100 |  |
| sess |  | nyam | 14111 | 0.82 | 0.058 | 2.6 | 2.0 | 3/4 | 0.059 |  |
| sess |  | nypm | 15505 | 0.80 | -0.023 | -1.0 | 2.4 | 0/4 | -0.051 |  |
| sess |  | close | 9750 | 0.78 | 0.004 | 0.2 | 2.5 | 3/4 | -0.037 |  |
| book_sess | K7 | close | 1750 | 0.87 | 0.066 | 2.5 | 2.6 | 3/4 | 0.111 |  |
| book_sess | P7 | nyam | 3325 | 0.67 | 0.071 | 2.4 | 2.9 | 3/4 | -0.012 |  |

**c4_sqz_5m_mom_with** (each alone; lift in R per signal, weekly cluster-robust zw, nonsense bar99 of the same cell; PASS = full rule)

| cell | book | sess | n yes | share | lift R | zw | bar99 | years pos/n | lift L6M | pass |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 67678 | 0.81 | -0.002 | -0.5 | 2.3 | 2/4 | 0.014 |  |
| book | A7 |  | 16923 | 0.97 | -0.055 | -1.4 | 2.4 | 1/4 | -0.222 |  |
| book | H7 |  | 2453 | 0.76 | -0.049 | -1.8 | 2.4 | 0/4 | -0.046 |  |
| book | K7 |  | 9684 | 0.64 | 0.016 | 1.0 | 2.6 | 3/4 | 0.049 |  |
| book | M7 |  | 13777 | 0.83 | -0.006 | -0.6 | 2.2 | 1/4 | 0.066 |  |
| book | O7 |  | 343 | 0.67 | 0.119 | 0.7 | 3.7 | 2/3 | 0.294 |  |
| book | P7 |  | 22094 | 0.79 | -0.008 | -0.4 | 2.2 | 1/4 | -0.024 |  |
| book | U7 |  | 2404 | 0.93 | 0.002 | -0.3 | 2.5 | 1/4 | 0.047 |  |
| sess |  | asia | 8039 | 0.75 | 0.060 | 3.0 | 2.8 | 4/4 | -0.011 |  |
| sess |  | london | 15212 | 0.84 | 0.064 | 1.1 | 2.5 | 3/4 | 0.050 |  |
| sess |  | pre | 4654 | 0.85 | -0.119 | -1.7 | 2.8 | 1/4 | -0.153 |  |
| sess |  | nyam | 14244 | 0.82 | -0.019 | -1.6 | 2.0 | 1/4 | -0.046 |  |
| sess |  | nypm | 15577 | 0.81 | -0.046 | -2.2 | 2.4 | 1/4 | 0.086 |  |
| sess |  | close | 9952 | 0.79 | 0.000 | -0.5 | 2.5 | 2/4 | 0.061 |  |
| book_sess | K7 | asia | 1981 | 0.61 | 0.080 | 2.7 | 2.3 | 4/4 | 0.056 | PASS |
| book_sess | K7 | london | 1845 | 0.67 | 0.131 | 2.6 | 2.4 | 4/4 | 0.179 | PASS |
| book_sess | P7 | nyam | 4327 | 0.87 | -0.065 | -2.2 | 2.9 | 0/4 | 0.035 |  |

**c4_sqz_15m_mom_with** (each alone; lift in R per signal, weekly cluster-robust zw, nonsense bar99 of the same cell; PASS = full rule)

| cell | book | sess | n yes | share | lift R | zw | bar99 | years pos/n | lift L6M | pass |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 59621 | 0.72 | 0.011 | 0.2 | 2.3 | 2/4 | 0.047 |  |
| book | A7 |  | 14753 | 0.85 | 0.013 | 0.3 | 2.4 | 2/4 | -0.095 |  |
| book | H7 |  | 2486 | 0.77 | 0.013 | -0.4 | 2.4 | 2/4 | 0.093 |  |
| book | K7 |  | 8320 | 0.55 | 0.011 | 0.3 | 2.6 | 1/4 | 0.030 |  |
| book | M7 |  | 12102 | 0.73 | -0.005 | -1.1 | 2.2 | 2/4 | 0.090 |  |
| book | O7 |  | 256 | 0.50 | -0.017 | -0.7 | 3.7 | 1/4 | 0.100 |  |
| book | P7 |  | 20695 | 0.74 | 0.032 | 1.0 | 2.2 | 3/4 | 0.105 |  |
| book | U7 |  | 1009 | 0.39 | -0.054 | -0.8 | 2.5 | 0/4 | -0.102 |  |
| sess |  | asia | 7274 | 0.68 | 0.066 | 2.0 | 2.8 | 3/4 | 0.068 |  |
| sess |  | london | 12863 | 0.71 | 0.036 | 1.7 | 2.5 | 3/4 | 0.030 |  |
| sess |  | pre | 3873 | 0.71 | 0.016 | 0.2 | 2.8 | 2/4 | 0.149 |  |
| sess |  | nyam | 12039 | 0.70 | -0.021 | -0.9 | 2.0 | 1/4 | 0.088 |  |
| sess |  | nypm | 14536 | 0.75 | 0.008 | 0.4 | 2.4 | 2/4 | 0.137 |  |
| sess |  | close | 9036 | 0.72 | -0.016 | 0.1 | 2.5 | 2/4 | -0.157 |  |
| book_sess | A7 | close | 1446 | 0.87 | -0.283 | -2.1 | 2.4 | 0/4 | -1.055 |  |
| book_sess | K7 | asia | 1781 | 0.55 | 0.073 | 2.2 | 2.3 | 3/4 | 0.078 |  |
| book_sess | M7 | nyam | 2642 | 0.75 | -0.064 | -2.3 | 2.6 | 1/4 | 0.001 |  |

**Passing tests among all 408 squeeze conditions: 141 (0.69% of 20400 tests; nonsense 0.44%).**

| cell | book | sess | condition | n yes | lift R | zw | bar99 | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|
| ALL |  |  | c4_sqz_alt_ha60_fired5_against | 7165 | -0.083 | -5.2 | 2.3 | 0/4 | -0.171 |
| sess |  | close | c4_sqz_alt_ha15_onF | 8934 | 0.121 | 4.5 | 2.5 | 4/4 | 0.071 |
| book | P7 |  | c4_sqz_alt_ha60_fired5_against | 2550 | -0.103 | -4.0 | 2.2 | 0/4 | -0.249 |
| sess |  | close | c4_sqz_alt_ha15_fired5_with | 1841 | -0.095 | -4.0 | 2.5 | 0/4 | -0.175 |
| ALL |  |  | c4_sqz_alt_ha60_len6 | 21854 | 0.037 | 4.0 | 2.3 | 4/4 | 0.008 |
| book_sess | A7 | close | c4_sqz_alt_ha15_onF | 959 | 0.212 | 3.8 | 2.4 | 4/4 | 0.043 |
| sess |  | nyam | c4_sqz_alt_ha60_fired5_against | 1671 | -0.144 | -3.8 | 2.0 | 0/4 | -0.146 |
| book_sess | H7 | asia | c4_sqz_alt_ha15_mom_rise_withF | 346 | -0.094 | -3.8 | 2.2 | 0/4 | -0.206 |
| book_sess | M7 | close | c4_sqz_alt_ha15_onF | 2533 | 0.163 | 3.7 | 2.8 | 4/4 | 0.061 |
| book_sess | K7 | pre | c4_sqz_15m_fired5_any | 160 | -0.201 | -3.7 | 2.3 | 0/3 | -0.425 |
| sess |  | nypm | c4_sqz_alt_ha60_fired5_against | 2102 | -0.144 | -3.7 | 2.4 | 0/4 | -0.447 |
| book_sess | H7 | london | c4_sqz_alt_ha1_mom_rise_with | 418 | -0.197 | -3.6 | 2.9 | 0/4 | -0.077 |
| book_sess | M7 | close | c4_sqz_15m_onF | 1806 | 0.120 | 3.5 | 2.8 | 4/4 | 0.015 |
| sess |  | close | c4_sqz_15m_onF | 6149 | 0.080 | 3.5 | 2.5 | 4/4 | 0.021 |
| book_sess | K7 | pre | c4_sqz_3m_mom_with | 769 | -0.182 | -3.5 | 2.3 | 0/3 | -0.335 |
| book | H7 |  | c4_sqz_alt_vol500_len6F | 695 | 0.110 | 3.5 | 2.4 | 4/4 | 0.095 |
| book | M7 |  | c4_sqz_alt_ha60_fired5_against | 1455 | -0.094 | -3.5 | 2.2 | 0/4 | -0.125 |
| book_sess | K7 | nyam | c4_sqz_15m_len6F | 739 | 0.114 | 3.5 | 2.3 | 4/4 | 0.003 |
| book_sess | U7 | asia | c4_sqz_15m_mom_rise_withF | 581 | 0.205 | 3.5 | 2.9 | 3/3 | 0.212 |
| book_sess | M7 | close | c4_sqz_60m_bw10_on | 284 | 0.282 | 3.4 | 2.8 | 4/4 | 0.223 |
| book_sess | P7 | asia | c4_sqz_alt_tick2000_mom_rise_with | 3124 | 0.118 | 3.4 | 3.1 | 4/4 | 0.220 |
| book_sess | H7 | london | c4_sqz_alt_renko8_mom_rise_with | 426 | -0.169 | -3.4 | 2.9 | 0/4 | -0.249 |
| sess |  | nyam | c4_sqz_alt_ha60_bw20_on | 5140 | -0.079 | -3.4 | 2.0 | 0/4 | -0.213 |
| book_sess | M7 | close | c4_sqz_alt_vol500_mom_rise_withS | 2275 | -0.089 | -3.3 | 2.8 | 0/4 | -0.091 |
| book_sess | K7 | nyam | c4_sqz_15m_on | 783 | 0.088 | 3.3 | 2.3 | 4/4 | 0.010 |
| book_sess | K7 | nyam | c4_sqz_15m_on_or_bw20 | 811 | 0.080 | 3.3 | 2.3 | 4/4 | 0.012 |
| ALL |  |  | c4_sqz_1m_mom_rise_withF | 56899 | -0.023 | -3.3 | 2.3 | 0/4 | -0.019 |
| book_sess | A7 | nypm | c4_sqz_alt_ha1_mom_withF | 3244 | -0.051 | -3.3 | 2.5 | 0/4 | -0.069 |
| book | A7 |  | c4_sqz_alt_ha60_len6 | 4458 | 0.089 | 3.2 | 2.4 | 4/4 | 0.109 |
| book_sess | M7 | nyam | c4_sqz_15m_len6F | 787 | 0.093 | 3.2 | 2.6 | 4/4 | 0.096 |
