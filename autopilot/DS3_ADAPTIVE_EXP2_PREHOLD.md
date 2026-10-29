# DS3_ADAPTIVE_EXP2 PREHOLD - part (b) PRE-only walk-forward tables (IN-SAMPLE selection span; HOLD and X' not indexed)

Prereg l2vast/ds3/prereg/EXP2_prereg.md. 122 cells (120 chains + 2 frozen). White RC on PRE over all cells: max weekly t 1.84, p = 0.760; shuffled-key null max t over the same 120 chains 1.04.

Units: U1 rows in pts/trade per lot (M10) vs 60/60; U2/U3 rows in $/trade at parity lots vs 60/60 at live lots. Weekly stack path = 11 books, PRE span, parity lots vs 60/60 live lots.

## Top 10 by PRE mean (own unit)
| cell | unit | PRE_n | PRE_mean | PRE_lo | PRE_hi | PRE_mde | PRE_pts | PRE_usd | PRE_usd_wk | PRE_diff | PRE_pol_maxdd | PRE_ctl_maxdd | PRE_pol_w20 | PRE_ctl_w20 | PRE_pol_sd | PRE_ctl_sd |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| FROZEN|perbook_bestPRE | U2 | 26022 | 285.47 | -88.95 | 659.89 | 534.89 | 2.72 | 285.47 | 99046 | 1.00 | 3868445 | 1696829 | -15663151 | -8149331 | 770881 | 341076 |
| s|book|U2|z0|ew20 | U2 | 26022 | 108.06 | -184.26 | 400.39 | 417.60 | 1.36 | 108.06 | 37493 | 0.86 | 3635752 | 1696829 | -14042170 | -8149331 | 624992 | 341076 |
| rs|pooled|U2|z0|ew20 | U2 | 26022 | 89.48 | -222.23 | 401.19 | 445.30 | 1.77 | 89.48 | 31046 | 0.80 | 4482032 | 1696829 | -14888589 | -8149331 | 664536 | 341076 |
| s|book|U2|z0|3m | U2 | 26022 | 83.28 | -190.81 | 357.37 | 391.56 | 0.97 | 83.28 | 28896 | 0.87 | 3199719 | 1696829 | -13525707 | -8149331 | 605742 | 341076 |
| rs|pooled|U2|z0|6m | U2 | 26022 | 79.65 | -245.47 | 404.77 | 464.46 | 1.03 | 79.65 | 27636 | 0.85 | 4035989 | 1696829 | -14088054 | -8149331 | 686850 | 341076 |
| s|book|U2|z0|6m | U2 | 26022 | 57.98 | -252.82 | 368.79 | 444.01 | 0.80 | 57.98 | 20118 | 0.90 | 3583569 | 1696829 | -15122458 | -8149331 | 659012 | 341076 |
| rs|book|U2|z0|6m | U2 | 26022 | 50.05 | -239.40 | 339.50 | 413.50 | 0.63 | 50.05 | 17365 | 0.87 | 3407520 | 1696829 | -13705123 | -8149331 | 641473 | 341076 |
| s|book|U3|z0|3m | U3 | 26022 | 42.59 | -3.39 | 88.56 | 65.68 | 0.41 | 42.59 | 14776 | 0.05 | 1683596 | 1696829 | -8061019 | -8149331 | 354551 | 341076 |
| 0|book|U2|z0|12m | U2 | 26022 | 39.39 | -360.68 | 439.45 | 571.52 | 1.05 | 39.39 | 13666 | 0.94 | 5363414 | 1696829 | -17453286 | -8149331 | 783706 | 341076 |
| s|book|U2|z1|ew20 | U2 | 26022 | 38.12 | -113.93 | 190.18 | 217.22 | 0.76 | 38.12 | 13227 | 0.31 | 2086579 | 1696829 | -10401298 | -8149331 | 458770 | 341076 |

## Frozen cells
| cell | unit | PRE_n | PRE_mean | PRE_lo | PRE_hi | PRE_mde | PRE_pts | PRE_usd | PRE_usd_wk | PRE_diff | PRE_pol_maxdd | PRE_ctl_maxdd | PRE_pol_w20 | PRE_ctl_w20 | PRE_pol_sd | PRE_ctl_sd |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| FROZEN|abs120|OR|none | U1 | 26022 | 2.33 | -2.04 | 6.70 | 6.24 | 2.33 | 164.78 | 57171 | 1.00 | 3918025 | 1696829 | -14506257 | -8149331 | 670574 | 341076 |
| FROZEN|perbook_bestPRE | U2 | 26022 | 285.47 | -88.95 | 659.89 | 534.89 | 2.72 | 285.47 | 99046 | 1.00 | 3868445 | 1696829 | -15663151 | -8149331 | 770881 | 341076 |

## Placebo ranks (PRE mean, share of 20 draws below the cell; shuffled keys and random assignment)
- s|book|U2|z0|ew20: real 108.063, shuffled rank 0.95 (mean 42.214), random rank 1.00 (mean 41.990)
- rs|pooled|U2|z0|ew20: real 89.479, shuffled rank 0.80 (mean 44.965), random rank 0.70 (mean 72.713)
- s|book|U2|z0|3m: real 83.283, shuffled rank 0.70 (mean 51.874), random rank 0.90 (mean 31.632)
- rs|pooled|U2|z0|6m: real 79.653, shuffled rank 0.50 (mean 76.498), random rank 0.00 (mean 162.439)
- s|book|U2|z0|6m: real 57.984, shuffled rank 0.40 (mean 62.494), random rank 0.20 (mean 89.186)
- rs|book|U2|z0|6m: real 50.050, shuffled rank 0.40 (mean 67.509), random rank 0.20 (mean 104.940)
- s|book|U3|z0|3m: real 42.587, shuffled rank 1.00 (mean -0.999), random rank 0.85 (mean 21.192)
- 0|book|U2|z0|12m: real 39.387, shuffled rank 0.00 (mean 39.387), random rank 0.35 (mean 55.213)
- s|book|U2|z1|ew20: real 38.124, shuffled rank 0.90 (mean -14.160), random rank 0.70 (mean 22.626)

## PRE mean by family (mean over cells, own unit; U1 pts, U2/U3 $)
obj  ks       
U1   0/book        0.18
     r/book        0.08
     rs/book      -0.23
     rs/pooled    -0.37
     s/book        0.35
U2   0/book        8.34
     r/book      -50.29
     rs/book     -49.20
     rs/pooled   -45.85
     s/book        9.42
U3   0/book       -0.00
     r/book       -0.36
     rs/book      -2.08
     rs/pooled   -11.95
     s/book        6.10
obj  win 
U1   12m     -0.37
     3m      -0.09
     6m       0.13
     ew20     0.33
U2   12m    -56.18
     3m     -24.19
     6m     -22.33
     ew20     0.65
U3   12m     -1.40
     3m      -3.20
     6m      -1.64
     ew20    -0.39