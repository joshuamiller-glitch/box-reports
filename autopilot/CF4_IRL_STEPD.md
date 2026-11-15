## IRL / ERL Step D: SCREEN of the proposed books (own 1m simulation, NOT the exact engine; no tuning; fixed small grid)

**Verdict line: Book 1 (fade external sweeps) averages -0.043 R/trade across range definitions and targets vs -0.053 R on its internal-sweep control; Book 2 (internal continuation) -0.070 R vs -0.161 R on external-sweep control. Screening only; positive cells: Book 1 ext 14 of 52, Book 1 control 0 of 52.**
Book 1 = fade the sweep of the range high/low at the close back inside, stop = poke extreme +2 pts, target 1R/1.5R/2R/range midpoint, time stop min(120 min, session end), cost 0.5 pt per trade. Control = the SAME book on internal sweeps. Book 2 = internal-sweep continuation: after an internal level is swept (poke direction), enter at the first retest of the level within 30 min, stop 1 ATR back inside, target the external boundary beyond (must be >1.5 ATR away); control = same on external sweeps. Table: expectancy in R per trade (net of cost), trades; full history and L6M. Per-session / per-side cells are in /mnt/l2/l2vast/_confl/irl/stepD.parquet. An exact-engine run through the CF hook is still to do for anything that looks interesting; screening results here are NOT leads.

**B1_ext_reversal, target 1.5R**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | ext | 460 | 0.035 | 0.45 | 80 | -0.082 |
| a_pd | int_control | 32377 | -0.048 | 0.41 | 5415 | 0.003 |
| b_ps | ext | 1488 | -0.045 | 0.41 | 243 | -0.072 |
| b_ps | int_control | 28981 | -0.050 | 0.40 | 5471 | -0.007 |
| b_cs60 | ext | 16137 | -0.056 | 0.40 | 2898 | -0.037 |
| b_cs60 | int_control | 27330 | -0.052 | 0.41 | 4898 | -0.015 |
| c_on | ext | 689 | -0.068 | 0.39 | 94 | 0.004 |
| c_on | int_control | 10374 | -0.052 | 0.40 | 1687 | -0.011 |
| d_wk | ext | 100 | 0.011 | 0.44 |  |  |
| d_wk | int_control | 33332 | -0.061 | 0.40 | 5894 | -0.017 |
| e15_10 | ext | 1413 | -0.041 | 0.41 | 232 | -0.086 |
| e15_10 | int_control | 28042 | -0.057 | 0.40 | 5137 | 0.009 |
| e15_20 | ext | 715 | 0.041 | 0.45 | 124 | -0.116 |
| e15_20 | int_control | 32647 | -0.054 | 0.40 | 5527 | -0.009 |
| e60_10 | ext | 382 | 0.042 | 0.44 | 57 | -0.152 |
| e60_10 | int_control | 32288 | -0.053 | 0.40 | 5167 | 0.004 |
| e60_20 | ext | 214 | -0.096 | 0.39 | 33 | -0.224 |
| e60_20 | int_control | 29175 | -0.061 | 0.40 | 5159 | -0.018 |
| e240_10 | ext | 102 | -0.081 | 0.40 |  |  |
| e240_10 | int_control | 29125 | -0.055 | 0.40 | 4941 | -0.018 |
| e240_20 | ext | 39 | -0.127 | 0.38 |  |  |
| e240_20 | int_control | 29049 | -0.056 | 0.40 | 5613 | -0.034 |
| f_or30 | ext | 2087 | -0.058 | 0.40 | 348 | 0.001 |
| f_or30 | int_control | 9231 | -0.039 | 0.41 | 1675 | 0.009 |
| f_or60 | ext | 1922 | -0.044 | 0.41 | 311 | 0.019 |
| f_or60 | int_control | 11009 | -0.044 | 0.41 | 1971 | 0.016 |

**B1_ext_reversal, target mid**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | ext | 455 | -0.114 | 0.33 | 79 | -0.361 |
| a_pd | int_control | 15933 | -0.092 | 0.33 | 2739 | -0.137 |
| b_ps | ext | 1443 | -0.034 | 0.38 | 234 | -0.117 |
| b_ps | int_control | 14816 | -0.064 | 0.39 | 2896 | -0.091 |
| b_cs60 | ext | 15855 | -0.076 | 0.33 | 2867 | -0.044 |
| b_cs60 | int_control | 16015 | -0.059 | 0.41 | 2834 | -0.037 |
| c_on | ext | 685 | -0.055 | 0.38 | 93 | -0.132 |
| c_on | int_control | 5608 | -0.029 | 0.42 | 916 | 0.043 |
| d_wk | ext | 100 | 0.098 | 0.33 |  |  |
| d_wk | int_control | 16414 | -0.047 | 0.28 | 2906 | -0.018 |
| e15_10 | ext | 1370 | -0.054 | 0.36 | 230 | -0.140 |
| e15_10 | int_control | 14652 | -0.083 | 0.38 | 2810 | -0.086 |
| e15_20 | ext | 705 | 0.044 | 0.37 | 124 | -0.274 |
| e15_20 | int_control | 17094 | -0.076 | 0.35 | 2998 | -0.117 |
| e60_10 | ext | 381 | 0.064 | 0.32 | 57 | -0.462 |
| e60_10 | int_control | 16826 | -0.065 | 0.32 | 2698 | -0.147 |
| e60_20 | ext | 214 | -0.176 | 0.27 | 33 | -0.521 |
| e60_20 | int_control | 14800 | -0.047 | 0.30 | 2623 | -0.022 |
| e240_10 | ext | 102 | -0.078 | 0.27 |  |  |
| e240_10 | int_control | 14653 | -0.051 | 0.29 | 2501 | -0.083 |
| e240_20 | ext | 39 | -0.072 | 0.23 |  |  |
| e240_20 | int_control | 14526 | -0.052 | 0.28 | 2859 | -0.011 |
| f_or30 | ext | 1955 | -0.056 | 0.47 | 333 | 0.148 |
| f_or30 | int_control | 3684 | -0.057 | 0.53 | 689 | 0.058 |
| f_or60 | ext | 1840 | -0.037 | 0.43 | 303 | 0.050 |
| f_or60 | int_control | 4762 | -0.045 | 0.49 | 889 | 0.059 |

**B2_int_continuation, target ext_level**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | int | 22038 | -0.099 | 0.25 | 3572 | -0.076 |
| b_ps | int | 17085 | -0.095 | 0.27 | 3328 | -0.097 |
| b_cs60 | int | 12437 | -0.067 | 0.29 | 2271 | -0.031 |
| b_cs60 | ext_control | 312 | -0.161 | 0.32 | 45 | 0.001 |
| c_on | int | 5406 | -0.062 | 0.28 | 908 | -0.104 |
| d_wk | int | 24449 | -0.043 | 0.25 | 4292 | -0.107 |
| e15_10 | int | 16812 | -0.066 | 0.27 | 3087 | -0.099 |
| e15_20 | int | 21662 | -0.081 | 0.26 | 3604 | -0.078 |
| e60_10 | int | 22649 | -0.085 | 0.25 | 3536 | -0.099 |
| e60_20 | int | 21029 | -0.064 | 0.25 | 3701 | -0.127 |
| e240_10 | int | 21495 | -0.046 | 0.25 | 3619 | -0.105 |
| e240_20 | int | 21513 | -0.055 | 0.25 | 4140 | -0.130 |
| f_or30 | int | 3315 | -0.075 | 0.31 | 646 | -0.086 |
| f_or60 | int | 4749 | -0.075 | 0.30 | 901 | -0.072 |
