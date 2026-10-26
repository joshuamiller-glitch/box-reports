# REPORT P1-DECOMP - cost decomposition of the 2013-2026 scaled re-test (pair; WT-10 pending in REPORT_WT2)

**Plain statement: the 2013-22 failure is a loss of gross edge, not a fixed-dollar cost eating an edge that was there.** At the price-scaled bracket (scaling a) the pair's gross move per trade over 2013-22 is +0.0003 R (se 0.008, t 0.04; 16,127 trades) against +0.036 R in 2023-26 (t 3.0). At the live fixed 60-pt bracket it is -0.016 R in 2013-22 (t -1.9) against +0.057 R in 2023-26 (t 4.9). So before any cost the signals have ~zero edge pre-2023 (we cannot rule out a gross edge below ~+0.016 R/trade at 2 se). Fixed-dollar costs then make it worse in 2013-16: the tick is 0.83 bp of price in 2013 against 0.09 bp in 2026, and the bracket is only 36-54 ticks, so costs run 0.05-0.08 R per trade at the real fixed cost, about 0.005-0.01 R at price-scaled cost, and ~0.00-0.01 R in 2024-26. Costs deepen the loss; they are not the cause.

Net per trade (R): see the per-year table. Pair at scaling a, 2013-22: gross +0.000, net real -0.04 (sum over years -605 R), net price-scaled -0.01 (-170 R); 2023-26 gross +0.036, real +0.027 (+227 R), scaled +0.028. Gross yearly values swing +-0.06 R (2018 +0.053, 2022 -0.064): no stable sign.

## Per-year table (pair, scaling a = 60 x price/20,000; real = fixed live cost; scaled = cost x price/20,000)
|   year |   price |   tick_bp |   bracket_ticks |   trades_day |   gross_R_per_trade |   avg_gross_move_ticks |   net_R_per_trade_real |   net_R_per_trade_scaled |   netR_year_real |   netR_year_scaled |
|-------:|--------:|----------:|----------------:|-------------:|--------------------:|-----------------------:|-----------------------:|-------------------------:|-----------------:|-------------------:|
|   2013 |    3008 |     0.831 |              36 |        5.378 |              -0.03  |                 -1.164 |                 -0.106 |                   -0.038 |         -137.286 |            -51.072 |
|   2014 |    3816 |     0.655 |              46 |        5.794 |               0.002 |                 -0.008 |                 -0.055 |                   -0.003 |          -77.687 |             -3.817 |
|   2015 |    4434 |     0.564 |              53 |        6.066 |               0.002 |                  0.117 |                 -0.045 |                   -0.016 |          -69.034 |            -24.676 |
|   2016 |    4530 |     0.552 |              54 |        6.156 |              -0.034 |                 -1.833 |                 -0.094 |                   -0.038 |         -140.056 |            -60.862 |
|   2017 |    5798 |     0.431 |              70 |        4.965 |               0.034 |                  2.206 |                 -0.018 |                    0.021 |          -22.114 |             26.392 |
|   2018 |    6965 |     0.359 |              83 |        7.398 |               0.053 |                  4.463 |                  0.013 |                    0.033 |           24.661 |             62.519 |
|   2019 |    7688 |     0.325 |              92 |        6.327 |              -0.026 |                 -2.795 |                 -0.066 |                   -0.042 |         -105.164 |            -67.848 |
|   2020 |   10353 |     0.241 |             124 |        7.973 |               0.023 |                  2.739 |                  0     |                    0.007 |            0.337 |             15.338 |
|   2021 |   14559 |     0.172 |             171 |        6.736 |               0.037 |                  6.573 |                  0.023 |                    0.028 |           39.296 |             48.225 |
|   2022 |   12434 |     0.201 |             148 |        7.163 |              -0.064 |                 -9.88  |                 -0.064 |                   -0.062 |         -118.129 |           -113.886 |
|   2023 |   14823 |     0.169 |             177 |        6.659 |              -0.024 |                 -3.882 |                 -0.027 |                   -0.027 |          -47.232 |            -45.976 |
|   2024 |   19092 |     0.131 |             228 |        6.619 |               0.06  |                 13.383 |                  0.065 |                    0.066 |          111.389 |            112.483 |
|   2025 |   22856 |     0.109 |             264 |        7.604 |               0.075 |                 19.185 |                  0.062 |                    0.063 |          119.824 |            122.35  |
|   2026 |   28908 |     0.086 |             345 |        7.936 |               0.027 |                  9.621 |                  0.026 |                    0.024 |           42.012 |             39.198 |

## Same, live fixed 60-pt bracket (gross and real only)
|   year |   price |   bracket_ticks |   trades_day |   gross_R_per_trade |   avg_gross_move_ticks |   net_R_per_trade_real |   netR_year_real |
|-------:|--------:|----------------:|-------------:|--------------------:|-----------------------:|-----------------------:|-----------------:|
|   2013 |    3008 |             240 |        2.06  |               0.002 |                  0.458 |                 -0.01  |           -5.16  |
|   2014 |    3816 |             240 |        2.278 |              -0.015 |                 -3.504 |                 -0.03  |          -16.932 |
|   2015 |    4434 |             240 |        2.57  |               0.03  |                  7.224 |                  0.02  |           12.657 |
|   2016 |    4530 |             240 |        2.623 |               0.009 |                  2.12  |                  0.003 |            2.303 |
|   2017 |    5798 |             240 |        2.369 |               0.015 |                  3.526 |                  0.004 |            2.118 |
|   2018 |    6965 |             240 |        3.787 |              -0.025 |                 -6.051 |                 -0.036 |          -34.385 |
|   2019 |    7688 |             240 |        3.468 |               0.016 |                  3.9   |                 -0.003 |           -2.838 |
|   2020 |   10353 |             240 |        5.804 |              -0.026 |                 -6.26  |                 -0.043 |          -63.952 |
|   2021 |   14559 |             240 |        5.675 |              -0.02  |                 -4.812 |                 -0.021 |          -29.999 |
|   2022 |   12434 |             240 |        6.786 |              -0.061 |                -14.568 |                 -0.055 |          -95.949 |
|   2023 |   14823 |             240 |        5.953 |               0.027 |                  6.525 |                  0.005 |            7.056 |
|   2024 |   19092 |             240 |        6.521 |               0.061 |                 14.71  |                  0.062 |          104.669 |
|   2025 |   22856 |             240 |        7.695 |               0.082 |                 19.674 |                  0.058 |          113.947 |
|   2026 |   28908 |             240 |        9.505 |               0.05  |                 12.084 |                  0.037 |           71.242 |

## Structural series vs the pair's rolling 26-week GROSS Sharpe (run_a_gross), 2013-2026 (695 weeks)
Series: RTH share of NQ volume (from 1-minute bars), MNQ share of NQ-equivalent volume (10 MNQ = 1 NQ; zero before 2019-05), log NQ weekly volume, NQ options volume share (total options volume, all expiries: NQ.OPT daily bars bought for $17.14; weekly/0DTE identification needs the definition files, still downloading).

| series | corr of levels (26w) | corr of 13-week changes | corr of yearly values |
|---|---|---|---|
| rth_share | -0.02 | +0.21 | -0.11 |
| mnq_share | +0.10 | -0.40 | +0.23 |
| nq_volume | +0.20 | +0.20 | +0.25 |
| opt_vol_share | -0.13 | +0.08 | -0.13 |

Reading: none of the four series tracks the pair's gross Sharpe (|r| <= 0.20 in levels; the one non-trivial figure, MNQ share vs 13-week changes -0.40, has the opposite sign to its level correlation +0.10, i.e. no stable relation). Levels of trending series correlate spuriously, so the change and yearly columns are the fairer test; with 14 years the yearly column has ~12 degrees of freedom. RTH share fell from 0.83 (2013) to 0.73-0.78 (2019+); MNQ share went from 0 to ~95% of NQ-equivalent volume by 2020. Neither lines up with the pair's 2023+ profitability (which starts in 2024). Weekly/0DTE options share (identifiable via expiry in the definition files) is pending; total options share has correlation -0.13.
Not a test of cause: with ~1 regime change in the sample, any slow-moving structural series can only be matched by chance. Limits: 1-minute engine (fidelity 0.88 weekly corr), back-adjusted to raw price by undoing roll gaps, costs 1 tick/side + $34.88/8 per contract.

DONE P1-DECOMP
