## IRL / ERL Step D: SCREEN of the proposed books (own 1m simulation, NOT the exact engine; no tuning; fixed small grid)

**Verdict line: Book 1 (fade external sweeps) averages -0.041 R/trade across range definitions and targets vs -0.053 R on its internal-sweep control; Book 2 (internal continuation) -0.069 R vs -0.176 R on external-sweep control. Screening only; positive cells: Book 1 ext 14 of 52, Book 1 control 0 of 52.**
Book 1 = fade the sweep of the range high/low at the close back inside, stop = poke extreme +2 pts, target 1R/1.5R/2R/range midpoint, time stop min(120 min, session end), cost 0.5 pt per trade. Control = the SAME book on internal sweeps. Book 2 = internal-sweep continuation: after an internal level is swept (poke direction), enter at the first retest of the level within 30 min, stop 1 ATR back inside, target the external boundary beyond (must be >1.5 ATR away); control = same on external sweeps. Table: expectancy in R per trade (net of cost), trades; full history and L6M. Per-session / per-side cells are in /mnt/l2/l2vast/_confl/irl/stepD.parquet. An exact-engine run through the CF hook is still to do for anything that looks interesting; screening results here are NOT leads.

**B1_ext_reversal, target 1.5R**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | ext | 450 | 0.032 | 0.45 | 70 | -0.114 |
| a_pd | int_control | 31662 | -0.049 | 0.41 | 4700 | 0.005 |
| b_ps | ext | 1451 | -0.049 | 0.40 | 206 | -0.103 |
| b_ps | int_control | 28208 | -0.051 | 0.40 | 4698 | -0.008 |
| b_cs60 | ext | 15732 | -0.056 | 0.40 | 2493 | -0.028 |
| b_cs60 | int_control | 26695 | -0.052 | 0.41 | 4263 | -0.011 |
| c_on | ext | 678 | -0.074 | 0.39 | 83 | -0.031 |
| c_on | int_control | 10154 | -0.052 | 0.40 | 1467 | -0.002 |
| d_wk | ext | 97 | 0.024 | 0.44 |  |  |
| d_wk | int_control | 32360 | -0.063 | 0.40 | 4922 | -0.022 |
| e15_10 | ext | 1384 | -0.037 | 0.42 | 203 | -0.062 |
| e15_10 | int_control | 27332 | -0.059 | 0.40 | 4427 | 0.011 |
| e15_20 | ext | 698 | 0.039 | 0.45 | 107 | -0.150 |
| e15_20 | int_control | 31924 | -0.054 | 0.40 | 4804 | -0.005 |
| e60_10 | ext | 376 | 0.041 | 0.44 | 51 | -0.179 |
| e60_10 | int_control | 31662 | -0.055 | 0.40 | 4541 | -0.001 |
| e60_20 | ext | 209 | -0.086 | 0.39 | 28 | -0.171 |
| e60_20 | int_control | 28491 | -0.062 | 0.40 | 4475 | -0.018 |
| e240_10 | ext | 101 | -0.072 | 0.41 |  |  |
| e240_10 | int_control | 28559 | -0.057 | 0.40 | 4375 | -0.022 |
| e240_20 | ext | 38 | -0.103 | 0.39 |  |  |
| e240_20 | int_control | 28709 | -0.057 | 0.40 | 5273 | -0.039 |
| f_or30 | ext | 2040 | -0.058 | 0.40 | 301 | 0.012 |
| f_or30 | int_control | 8987 | -0.038 | 0.41 | 1431 | 0.023 |
| f_or60 | ext | 1883 | -0.041 | 0.41 | 272 | 0.050 |
| f_or60 | int_control | 10753 | -0.045 | 0.41 | 1715 | 0.018 |

**B1_ext_reversal, target mid**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | ext | 445 | -0.122 | 0.33 | 69 | -0.450 |
| a_pd | int_control | 15573 | -0.093 | 0.33 | 2379 | -0.149 |
| b_ps | ext | 1407 | -0.043 | 0.38 | 198 | -0.201 |
| b_ps | int_control | 14408 | -0.060 | 0.40 | 2488 | -0.071 |
| b_cs60 | ext | 15452 | -0.076 | 0.33 | 2464 | -0.039 |
| b_cs60 | int_control | 15644 | -0.060 | 0.41 | 2463 | -0.041 |
| c_on | ext | 674 | -0.055 | 0.38 | 82 | -0.141 |
| c_on | int_control | 5501 | -0.026 | 0.43 | 809 | 0.067 |
| d_wk | ext | 97 | 0.113 | 0.33 |  |  |
| d_wk | int_control | 15926 | -0.045 | 0.28 | 2418 | 0.003 |
| e15_10 | ext | 1341 | -0.054 | 0.37 | 201 | -0.148 |
| e15_10 | int_control | 14263 | -0.076 | 0.39 | 2421 | -0.046 |
| e15_20 | ext | 688 | 0.027 | 0.37 | 107 | -0.431 |
| e15_20 | int_control | 16691 | -0.076 | 0.35 | 2595 | -0.127 |
| e60_10 | ext | 375 | 0.064 | 0.32 | 51 | -0.525 |
| e60_10 | int_control | 16475 | -0.066 | 0.32 | 2347 | -0.167 |
| e60_20 | ext | 209 | -0.156 | 0.28 | 28 | -0.431 |
| e60_20 | int_control | 14454 | -0.047 | 0.30 | 2277 | -0.024 |
| e240_10 | ext | 101 | -0.069 | 0.28 |  |  |
| e240_10 | int_control | 14366 | -0.048 | 0.29 | 2214 | -0.069 |
| e240_20 | ext | 38 | -0.047 | 0.24 |  |  |
| e240_20 | int_control | 14350 | -0.053 | 0.28 | 2683 | -0.013 |
| f_or30 | ext | 1911 | -0.056 | 0.47 | 289 | 0.176 |
| f_or30 | int_control | 3554 | -0.063 | 0.53 | 559 | 0.047 |
| f_or60 | ext | 1802 | -0.033 | 0.43 | 265 | 0.089 |
| f_or60 | int_control | 4630 | -0.050 | 0.49 | 757 | 0.049 |

**B2_int_continuation, target ext_level**

| range | ext/int group | n full | expR full | win full | n L6M | expR L6M |
|---|---|---|---|---|---|---|
| a_pd | int | 21550 | -0.099 | 0.25 | 3084 | -0.068 |
| b_ps | int | 16616 | -0.096 | 0.27 | 2859 | -0.103 |
| b_cs60 | int | 12122 | -0.068 | 0.29 | 1956 | -0.029 |
| b_cs60 | ext_control | 307 | -0.176 | 0.32 | 40 | -0.089 |
| c_on | int | 5287 | -0.058 | 0.28 | 789 | -0.085 |
| d_wk | int | 23720 | -0.040 | 0.25 | 3563 | -0.097 |
| e15_10 | int | 16369 | -0.065 | 0.27 | 2644 | -0.095 |
| e15_20 | int | 21185 | -0.082 | 0.26 | 3127 | -0.080 |
| e60_10 | int | 22212 | -0.082 | 0.25 | 3099 | -0.081 |
| e60_20 | int | 20525 | -0.065 | 0.25 | 3197 | -0.138 |
| e240_10 | int | 21068 | -0.042 | 0.25 | 3192 | -0.087 |
| e240_20 | int | 21264 | -0.051 | 0.25 | 3891 | -0.110 |
| f_or30 | int | 3225 | -0.073 | 0.31 | 556 | -0.076 |
| f_or60 | int | 4627 | -0.073 | 0.30 | 779 | -0.055 |
