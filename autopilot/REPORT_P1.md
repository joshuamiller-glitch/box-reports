# REPORT P1 - SCALED-BRACKET LONG-HISTORY RE-TEST OF THE LIVE PAIR (NQ 2013-2026, 1-minute engine)

**Verdict: the 2013-22 failure is NOT the unscaled bracket. With the bracket scaled three ways the pair's gross (zero-cost) weekly Sharpe over 2013-2022 is ~0.0 (a +0.06, b +0.05, c -0.28; fixed 60 -0.41), real-cost Sharpe -1.4 / -1.6 / -2.0, and even with costs scaled in proportion to the bracket it is -0.38 / -0.31 / -0.79. The edge exists only in 2023-26 (gross 1.2-2.3), and scaling the bracket REDUCES it there (real Sharpe a 1.25, b 1.13, c 0.90 vs fixed-60 1.78).**

Engine: `d1_f4_core`-style 1-minute bars (copy `p1_core.py`, `ap_p1_scaled.py`); live rules in R units (per-book 5R/-2R, day lock 8R/2R/67%/0000, week floor -8R, per-book week rule off), EMA200 filters, 8/8, R = $9,600 per full stop in every year (contracts = R / (bracket x $20), so $ at 8/8 = R-units x 9,600). Raw NQ price = back-adjusted price minus later roll gaps (2013 median 3,008; 2019 7,688; 2024 19,092). Fidelity vs live 1-second engine: 90% entry match, weekly corr 0.88 (C3-H2); no cross-book netting.

Scalings (all fixed before the run, no performance used): **a** bracket = 60 x raw price / 20,000 (signal bar); **b** = k x ADR20 with k = 60 / clean median ADR20 = 0.2109; **c** = m x ATR(120, 1-min) with m = 60 / clean median = 10.57. Tick-rounded, min 2 ticks. Costs: **real** (1 tick/side + $34.88/8 per contract RT, absolute, so a 20-pt bracket pays 3x the relative cost of 60 pts), **scaled** (costs x bracket/60: same relative cost as the live cell), **gross** (none).

**Which scaling is faithful:** (a). The parameter 60 pts is a statement about price level, (a) preserves the bracket/price ratio exactly and uses only information known at the signal. (b) and (c) tie the bracket to realised volatility, a different strategy (the bracket then varies day to day and within the day for c). Of the cost modes 'scaled' isolates signal edge; 'real' is what trading it would have cost. Neither gives edge in 2013-22.

## Weekly Sharpe by span

| run         |   2013-22 |   clean |   H1 |   H2 |   2023-26 |
|:------------|----------:|--------:|-----:|-----:|----------:|
| a_gross     |      0.06 |    2.05 | 2.68 | 1.31 |      1.62 |
| a_real      |     -1.38 |    1.67 | 2.15 | 1.05 |      1.25 |
| a_scaled    |     -0.38 |    1.71 | 2.21 | 0.99 |      1.28 |
| b_gross     |      0.05 |    1.8  | 1.57 | 1.34 |      1.36 |
| b_real      |     -1.57 |    1.51 | 1.44 | 1.23 |      1.13 |
| b_scaled    |     -0.31 |    1.57 | 1.32 | 1.03 |      1.12 |
| c_gross     |     -0.28 |    0.58 | 4.4  | 2.05 |      1.18 |
| c_real      |     -2.04 |    0.31 | 4.04 | 2.01 |      0.9  |
| c_scaled    |     -0.79 |    0.31 | 3.98 | 1.89 |      0.89 |
| fixed_gross |     -0.41 |    2.07 | 3.55 | 2.56 |      2.31 |
| fixed_real  |     -0.78 |    1.65 | 2.6  | 2.04 |      1.78 |

## Net in R units (x $9,600 = $ at 8/8)
| run         |   2013-22 |   2023-26 |
|:------------|----------:|----------:|
| a_gross     |        26 |       300 |
| a_real      |      -605 |       227 |
| a_scaled    |      -170 |       234 |
| b_gross     |        22 |       235 |
| b_real      |      -652 |       191 |
| b_scaled    |      -136 |       189 |
| c_gross     |      -116 |       189 |
| c_real      |      -824 |       141 |
| c_scaled    |      -327 |       139 |
| fixed_gross |      -122 |       401 |
| fixed_real  |      -232 |       308 |

## Per year - a_real
| span    |   net_R |          net_$8/8 |   sharpe |   maxDD_R |   trades/day |   avg pts/trade (bracket units) |   net R/trade |     n |   median bracket pts |
|:--------|--------:|------------------:|---------:|----------:|-------------:|--------------------------------:|--------------:|------:|---------------------:|
| 2013    | -137.29 |      -1.31794e+06 |    -3.44 |    146.58 |         5.15 |                           -0.04 |         -0.11 |  1293 |                 9    |
| 2014    |  -77.69 | -745796           |    -1.99 |     80.98 |         5.7  |                            0.01 |         -0.05 |  1414 |                11.5  |
| 2015    |  -69.03 | -662728           |    -1.53 |     87.55 |         5.93 |                            0.01 |         -0.05 |  1530 |                13.25 |
| 2016    | -140.06 |      -1.34453e+06 |    -3.73 |    158.84 |         5.79 |                           -0.05 |         -0.09 |  1487 |                13.5  |
| 2017    |  -22.11 | -212295           |    -0.59 |     40.49 |         4.8  |                            0.03 |         -0.02 |  1220 |                17.5  |
| 2018    |   24.66 |  236750           |     0.5  |     50.83 |         7.41 |                            0.05 |          0.01 |  1896 |                20.75 |
| 2019    | -105.16 |      -1.00957e+06 |    -2.41 |    133.82 |         6.23 |                           -0.03 |         -0.07 |  1583 |                22.75 |
| 2020    |    0.34 |    3238.55        |     0.01 |     74.91 |         7.95 |                            0.02 |          0    |  2042 |                31.25 |
| 2021    |   39.3  |  377246           |     0.85 |     30.48 |         6.73 |                            0.03 |          0.02 |  1737 |                42.75 |
| 2022    | -118.13 |      -1.13404e+06 |    -2.39 |    140.52 |         7.15 |                           -0.05 |         -0.06 |  1844 |                37.25 |
| 2023    |  -47.23 | -453431           |    -1.18 |     60.98 |         6.68 |                           -0.02 |         -0.03 |  1724 |                44.25 |
| 2024    |  111.39 |       1.06933e+06 |     2.55 |     35.81 |         6.62 |                            0.07 |          0.07 |  1701 |                57    |
| 2025    |  119.82 |       1.15031e+06 |     2.14 |     20.83 |         7.61 |                            0.08 |          0.06 |  1941 |                65.75 |
| 2026    |   42.01 |  403316           |     0.98 |     25.01 |         7.93 |                            0.03 |          0.03 |  1618 |                86.25 |
| 2013-22 | -605.17 |      -5.80967e+06 |    -1.38 |    623.26 |         6.29 |                           -0    |         -0.04 | 16046 |                20.75 |
| 2023-26 |  227.06 |       2.17976e+06 |     1.25 |     60.98 |         7.17 |                            0.04 |          0.03 |  6773 |                61.5  |

## Per year - a_scaled
| span    |   net_R |          net_$8/8 |   sharpe |   maxDD_R |   trades/day |   avg pts/trade (bracket units) |   net R/trade |     n |   median bracket pts |
|:--------|--------:|------------------:|---------:|----------:|-------------:|--------------------------------:|--------------:|------:|---------------------:|
| 2013    |  -51.07 | -490287           |    -1.21 |     62.45 |         5.38 |                           -0.03 |         -0.04 |  1350 |                 9    |
| 2014    |   -3.82 |  -36638.6         |    -0.1  |     40.3  |         5.79 |                            0.01 |         -0    |  1437 |                11.5  |
| 2015    |  -24.68 | -236891           |    -0.54 |     50.22 |         6.07 |                           -0    |         -0.02 |  1565 |                13.25 |
| 2016    |  -60.86 | -584274           |    -1.5  |     96.52 |         6.16 |                           -0.03 |         -0.04 |  1582 |                13.5  |
| 2017    |   26.39 |  253362           |     0.68 |     20.16 |         4.96 |                            0.03 |          0.02 |  1261 |                17.5  |
| 2018    |   62.52 |  600182           |     1.24 |     41.76 |         7.4  |                            0.05 |          0.03 |  1894 |                20.75 |
| 2019    |  -67.85 | -651339           |    -1.52 |    109.8  |         6.33 |                           -0.03 |         -0.04 |  1607 |                23    |
| 2020    |   15.34 |  147242           |     0.32 |     66.97 |         7.97 |                            0.01 |          0.01 |  2049 |                31    |
| 2021    |   48.23 |  462963           |     1.04 |     27.11 |         6.74 |                            0.03 |          0.03 |  1738 |                42.75 |
| 2022    | -113.89 |      -1.0933e+06  |    -2.29 |    136.28 |         7.16 |                           -0.05 |         -0.06 |  1848 |                37    |
| 2023    |  -45.98 | -441372           |    -1.15 |     55.76 |         6.66 |                           -0.03 |         -0.03 |  1718 |                44.25 |
| 2024    |  112.48 |       1.07983e+06 |     2.57 |     35.75 |         6.62 |                            0.07 |          0.07 |  1701 |                57    |
| 2025    |  122.35 |       1.17456e+06 |     2.16 |     20.97 |         7.6  |                            0.08 |          0.06 |  1939 |                66    |
| 2026    |   39.2  |  376305           |     0.92 |     25.56 |         7.94 |                            0.03 |          0.02 |  1619 |                86.25 |
| 2013-22 | -169.69 |      -1.62898e+06 |    -0.38 |    188.29 |         6.4  |                            0    |         -0.01 | 16331 |                20.5  |
| 2023-26 |  234.43 |       2.25057e+06 |     1.28 |     55.76 |         7.17 |                            0.04 |          0.03 |  6771 |                61.5  |

## Per year - a_gross
| span    |   net_R |          net_$8/8 |   sharpe |   maxDD_R |   trades/day |   avg pts/trade (bracket units) |   net R/trade |     n |   median bracket pts |
|:--------|--------:|------------------:|---------:|----------:|-------------:|--------------------------------:|--------------:|------:|---------------------:|
| 2013    |  -34.83 | -334345           |    -0.82 |     51.37 |         5.29 |                           -0.03 |         -0.03 |  1329 |                 9    |
| 2014    |    8.73 |   83804.1         |     0.21 |     29.69 |         5.6  |                            0    |          0.01 |  1389 |                11.5  |
| 2015    |   -2.93 |  -28130.2         |    -0.06 |     38.86 |         6.19 |                            0    |         -0    |  1596 |                13.25 |
| 2016    |  -50.61 | -485856           |    -1.26 |     85.47 |         6.14 |                           -0.03 |         -0.03 |  1577 |                13.5  |
| 2017    |   47.53 |  456267           |     1.2  |     18.58 |         4.94 |                            0.03 |          0.04 |  1254 |                17.5  |
| 2018    |   88.77 |  852144           |     1.76 |     26.61 |         7.18 |                            0.05 |          0.05 |  1839 |                20.75 |
| 2019    |  -38.44 | -368988           |    -0.91 |     91.66 |         6.27 |                           -0.03 |         -0.02 |  1592 |                23    |
| 2020    |   52.93 |  508140           |     1.1  |     43.39 |         7.87 |                            0.02 |          0.03 |  2022 |                30.25 |
| 2021    |   66.03 |  633917           |     1.43 |     22.54 |         6.72 |                            0.04 |          0.04 |  1734 |                42.75 |
| 2022    | -111.03 |      -1.06594e+06 |    -2.24 |    127.14 |         6.96 |                           -0.06 |         -0.06 |  1795 |                37.5  |
| 2023    |  -21.35 | -204977           |    -0.51 |     45.46 |         6.59 |                           -0.02 |         -0.01 |  1699 |                44.25 |
| 2024    |  117.87 |       1.13156e+06 |     2.72 |     33.74 |         6.5  |                            0.06 |          0.07 |  1670 |                57    |
| 2025    |  144.92 |       1.39126e+06 |     2.49 |     19.95 |         7.52 |                            0.08 |          0.08 |  1918 |                66    |
| 2026    |   53.12 |  509967           |     1.25 |     23.19 |         7.92 |                            0.03 |          0.03 |  1616 |                86.25 |
| 2013-22 |   26.15 |  251016           |     0.06 |    128.44 |         6.32 |                            0    |          0    | 16127 |                20.5  |
| 2023-26 |  299.58 |       2.87597e+06 |     1.62 |     45.46 |         7.08 |                            0.04 |          0.04 |  6695 |                61.5  |

## Per year - fixed_real
| span    |   net_R |          net_$8/8 |   sharpe |   maxDD_R |   trades/day |   avg pts/trade (bracket units) |   net R/trade |    n |   median bracket pts |
|:--------|--------:|------------------:|---------:|----------:|-------------:|--------------------------------:|--------------:|-----:|---------------------:|
| 2013    |   -5.16 |  -49533.4         |    -0.48 |     12.89 |         2.06 |                            0    |         -0.01 |  513 |                   60 |
| 2014    |  -16.93 | -162543           |    -1.09 |     20.23 |         2.28 |                           -0.01 |         -0.03 |  558 |                   60 |
| 2015    |   12.66 |  121502           |     0.62 |     11.81 |         2.57 |                            0.03 |          0.02 |  645 |                   60 |
| 2016    |    2.3  |   22104.3         |     0.13 |     14.35 |         2.62 |                            0.01 |          0    |  661 |                   60 |
| 2017    |    2.12 |   20336.6         |     0.13 |     17.79 |         2.37 |                            0.01 |          0    |  597 |                   60 |
| 2018    |  -34.38 | -330095           |    -1.18 |     47.35 |         3.79 |                           -0.03 |         -0.04 |  958 |                   60 |
| 2019    |   -2.84 |  -27245.1         |    -0.09 |     44.15 |         3.47 |                            0.02 |         -0    |  874 |                   60 |
| 2020    |  -63.95 | -613942           |    -1.43 |     71.41 |         5.8  |                           -0.03 |         -0.04 | 1480 |                   60 |
| 2021    |  -30    | -287991           |    -0.75 |     72.01 |         5.67 |                           -0.02 |         -0.02 | 1447 |                   60 |
| 2022    |  -95.95 | -921111           |    -2.09 |    124.04 |         6.79 |                           -0.06 |         -0.06 | 1744 |                   60 |
| 2023    |    7.06 |   67741.4         |     0.2  |     21.67 |         5.95 |                            0.03 |          0    | 1512 |                   60 |
| 2024    |  104.67 |       1.00482e+06 |     2.18 |     38.35 |         6.52 |                            0.06 |          0.06 | 1676 |                   60 |
| 2025    |  113.95 |       1.09389e+06 |     2.25 |     30.28 |         7.7  |                            0.08 |          0.06 | 1970 |                   60 |
| 2026    |   71.24 |  683928           |     1.68 |     24.3  |         9.5  |                            0.05 |          0.04 | 1939 |                   60 |
| 2013-22 | -232.14 |      -2.22852e+06 |    -0.78 |    262.99 |         3.76 |                           -0.02 |         -0.02 | 9477 |                   60 |
| 2023-26 |  307.6  |       2.95291e+06 |     1.78 |     38.35 |         7.36 |                            0.06 |          0.04 | 6936 |                   60 |

## Reading
- Average gross move per trade is ~0.00 bracket units in 2013-22 under every scaling (see 'avg pts/trade'): the entry signals carry no directional information there before costs. Real costs then take ~0.04 R per trade on 6 trades/day under scaled brackets.
- Under scaling the pair trades ~6 times a day (median bracket ~20 pts in 2013-22) against 3.8 under the fixed 60; the extra trades are cost with no edge.
- In 2023-26 the scaled brackets keep a positive edge but lower than the live fixed-60 cell (a: 1.25 real vs 1.78). So the live 60 pts is not a price-ratio parameter that happens to travel; it is a 2023-26 choice.
- Conclusion for EXEC_SUMMARY: **'no edge 2013-22 holds under scaled brackets'.**
- Limits: 1-minute bars, stop-first; tick slippage stays 1 tick/side with up to ~50 contracts at 3,000-level NQ (liquidity/impact not modelled - favours the scaled runs); back-adjusted levels only used via raw price reconstruction.

DONE P1
