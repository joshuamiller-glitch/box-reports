# DS3_STACK_B_PREHOLD - PRE-only (2024-02..2025-06) text written before HOLD / X were read (D3SKB)
Prereg sha256 3393cdd663086347b900ccd71aa242d22aba24236f066fea4eb98037c8a9c753. Label days <= 2026-02-06 only. FLIP threshold (PRE p75 of first-hour direction flips) = 32. Note: the prereg said 14 candidate labels; the actual list is 12 (3x3 range labels + OVL + FLIP + ESDIS), so the stage-1 selection is over 12, not 14.

## Stage 1: label screen (PRE, post-10:30 trend-book P&L per day, unflagged minus flagged, Welch t)
| label    |   share |   n_flag |   mean_flag |   mean_unflag |      t | eligible   |
|:---------|--------:|---------:|------------:|--------------:|-------:|:-----------|
| ON_085   |   0.357 |      130 |   -1088.13  |       3825.92 |  1.535 | True       |
| FLIP     |   0.269 |       98 |   -1552.42  |       3405.81 |  1.425 | True       |
| FH60_07  |   0.198 |       72 |     690.642 |       2411.24 |  0.497 | True       |
| FH30_05  |   0.058 |       21 |     374.002 |       2174.79 |  0.477 | False      |
| OVL      |   0.288 |      105 |    1505.25  |       2300.22 |  0.233 | True       |
| ESDIS    |   0.165 |       60 |    1290.27  |       2224.97 |  0.22  | True       |
| ON_05    |   0.047 |       17 |     868.699 |       2129.8  |  0.139 | False      |
| FH30_085 |   0.332 |      121 |    1799.39  |       2206.1  |  0.131 | True       |
| FH60_05  |   0.066 |       24 |    1835.62  |       2087.51 |  0.062 | False      |
| ON_07    |   0.198 |       72 |    2312.29  |       2011.38 | -0.074 | False      |
| FH60_085 |   0.332 |      121 |    2697.53  |       1758.88 | -0.302 | False      |
| FH30_07  |   0.214 |       78 |    3416.12  |       1704.02 | -0.513 | False      |

Selected: L1=ON_085 L2=FLIP L3=FH60_07. B11 group: None (none flags if None).

## Group screen for B11 (PRE)
| group    |   n |    mean |    ci_lo |   ci_hi |    t | flags   |
|:---------|----:|--------:|---------:|--------:|-----:|:--------|
| Mon      |  74 |  -543.8 |  -5883.6 |  5179.2 |  1   | False   |
| Tue      |  73 |  2230.3 |  -4677.3 |  9384.7 | -0.1 | False   |
| Wed      |  71 |  2293   |  -5402.8 |  9957.3 | -0.1 | False   |
| Thu      |  74 |  2053.8 |  -4628   |  8595   |  0   | False   |
| Fri      |  72 |  4395.2 |  -1508.1 | 10904.3 | -0.8 | False   |
| opexweek |  84 |  1668.1 |  -3556.7 |  7078.6 |  0.1 | False   |
| opexday  |  16 |  5151.1 | -11617.2 | 25732.6 | -0.3 | False   |
| monthend |  51 |  4537.8 |  -1348.5 | 11302.1 | -0.7 | False   |
| hol_eve  |   4 | 22041.9 |      0   | 47519.4 | -1.6 | False   |

## PRE cells (paired weekly vs unchanged stack; 74 PRE weeks; worst-20 sets: fixed on all weeks <=2026-02-06 restricted to PRE, and PRE-only)
| cell   | rule                                         |   days_flag |   d_raw |   MDE | ci           |   d_LM |   dmaxDD_LM |   dworst_LM |   w20_fixed_LM |   w20_PRE_LM |   rank_shuf |   rank_shift |
|:-------|:---------------------------------------------|------------:|--------:|------:|:-------------|-------:|------------:|------------:|---------------:|-------------:|------------:|-------------:|
| B01    | ON_085 halve ALL                             |        0.36 |     -23 |  6399 | [-4632,4547] |    997 |      -64870 |         915 |         113711 |       142869 |       0.87  |          0.7 |
| B02    | ON_085 halve trend books, SM unchanged       |        0.36 |     514 |  5947 | [-3845,4766] |   1460 |      -61582 |        1501 |         103106 |       146828 |       0.91  |          0.9 |
| B03    | ON_085 stop trend-book entries               |        0.36 |    1028 | 11893 | [-7690,9533] |   2983 |       15672 |        3067 |         210709 |       300059 |       0.93  |          0.9 |
| B04    | ON_085 stop ALL entries                      |        0.36 |     -47 | 12797 | [-9264,9095] |   2041 |        9244 |        1874 |         232847 |       292554 |       0.89  |          0.7 |
| B05    | FLIP halve ALL                               |        0.27 |    1295 |  5303 | [-2208,4981] |   1930 |       11269 |        4117 |          82365 |        24318 |       0.925 |          0.7 |
| B06    | FLIP halve trend books                       |        0.27 |    1065 |  5114 | [-2451,4597] |   1657 |       22108 |        4382 |          76371 |        20913 |       0.945 |          0.7 |
| B07    | FLIP stop trend-book entries                 |        0.27 |    2130 | 10227 | [-4903,9193] |   3357 |       44807 |        8880 |         154782 |        42385 |       0.905 |          0.7 |
| B08    | ON_085 OR FLIP halve trend books             |        0.53 |     -57 |  6831 | [-4789,4719] |   1230 |      -33557 |        7647 |         108500 |       148790 |       0.95  |          0.8 |
| B09    | >=2 of ON_085,FLIP,FH60_07 halve trend books |        0.23 |    1160 |  4778 | [-2097,4571] |   1769 |       -8081 |       -4151 |          84091 |        35945 |       0.955 |          1   |
| B10    | ON_085 0.25x trend books                     |        0.36 |     771 |  8920 | [-5767,7149] |   2213 |      -23371 |        2275 |         156328 |       222617 |       0.915 |          0.9 |
| B12    | ON_085 CONTROL 1.5x trend books              |        0.36 |    -514 |  5947 | [-4766,3845] |  -1400 |       63588 |       -1439 |         -98886 |      -140817 |       0.085 |          0.1 |

## Ex-post reference (range days known only after 16:00; PRE)
| ref              |   d_raw |   d_LM |   w20_PRE_raw |   dmaxDD |
|:-----------------|--------:|-------:|--------------:|---------:|
| R_halve          |   11525 |  12885 |        410799 |  -110880 |
| R_stop           |   23050 |  26419 |        821597 |  -119196 |
| R_all_halve      |   11710 |  13207 |        423330 |  -110880 |
| R_halve_wholeday |   12394 |  27983 |       1020653 |  -188341 |