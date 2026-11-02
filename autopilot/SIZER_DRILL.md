# SIZER DRILL of the flag-rule cells (S4a, 2026-11-02 21:44Z)

Post-hoc, Shadow only. S1 flag cells (12; 11 distinct multiplier vectors) re-run on the TS base (run_v13t_ts, sequential rounding, phase-invariant so PA9 = the single run). Band = V13T PA9 flip-5 noise band (L6M .219, HOLD .205, MID .322, PRE .099, X' .182). harm_ok = no window below minus-band; above_band = L6M and PRE cut above band. Equal-risk = mean at the ladder's fitted maxDD minus ladder fitted mean ($/wk, 11-point lscale fit). Placebo rank = share of 100 draws below the real cut (L6M/PRE), high = real beats chance.

| cell                                 |   dups |   mean_lots |   live |   cut_L6M |   cut_HOLD |   cut_MID |   cut_PRE |   cut_X' |   drop_L6M |   drop_PRE |   dmean_L6M |   dmean_PRE | harm_ok   | above_band   |
|:-------------------------------------|-------:|------------:|-------:|----------:|-----------:|----------:|----------:|---------:|-----------:|-----------:|------------:|------------:|:----------|:-------------|
| ('g13', 'ers_15m_20', 1, 'SIG', 'A') |      1 |        3.17 |   3.22 |     0.374 |     -0.072 |    -1.552 |     0.138 |   -0.034 |      0.29  |      0.138 |         951 |          27 | False     | True         |
| ('g12', 'er_3m_100', 'L3', 'D')      |      1 |        3.74 |   3.22 |     0.247 |     -0.298 |    -2.17  |     0.089 |   -0.36  |      0.218 |      0.089 |        2252 |        1757 | False     | False        |
| ('g13', 'ers_15m_20', 1, 'L3', 'A')  |      1 |        3.33 |   3.22 |     0.319 |     -0.056 |    -1.382 |     0.041 |    0.006 |      0.438 |      0.041 |        4849 |        1018 | False     | False        |
| ('g12', 'er_10m_30', 'L3', 'D')      |      1 |        3.74 |   3.22 |     0.292 |     -0.302 |    -2.136 |     0.132 |   -0.463 |      0.114 |      0.132 |         826 |        2161 | False     | True         |
| ('g13', 'ers_15m_20', 1, 'SIG', 'D') |      1 |        3.85 |   3.22 |     0.401 |     -0.259 |    -1.989 |     0.024 |   -0.698 |      0.12  |      0.024 |        -764 |        -183 | False     | False        |
| ('g12', 'er_30m_10', 'LIN', 'B')     |      1 |        3.59 |   3.22 |     0.141 |      0.123 |    -1.346 |     0.017 |   -0.342 |      0.216 |      0.017 |        2504 |        3197 | False     | False        |
| ('g12', 'er_15m_20', 'L3', 'A')      |      2 |        3.31 |   3.22 |     0.227 |     -0.053 |    -1.587 |     0.128 |   -0.278 |      0.382 |      0.128 |        1761 |        1023 | False     | True         |
| ('g12', 'er_15m_20', 'LIVE', 'A')    |      1 |        3.4  |   3.22 |     0.112 |      0.111 |    -1.097 |    -0.016 |   -0.137 |      0.195 |     -0.016 |        7715 |         693 | False     | False        |
| ('g13', 'ers_10m_20', 1, 'LIN', 'B') |      1 |        3.64 |   3.22 |     0.092 |     -0.094 |    -1.111 |     0.173 |   -0.221 |      0.088 |      0.173 |        4516 |        2691 | False     | False        |
| ('g12', 'er_10m_30', 'LIN', 'B')     |      1 |        3.61 |   3.22 |     0.059 |     -0.016 |    -1.526 |    -0.003 |   -0.179 |      0.292 |     -0.003 |       11544 |        2442 | False     | False        |
| ('g12', 'er_15m_20', 'LIN', 'B')     |      1 |        3.6  |   3.22 |     0.053 |     -0.077 |    -1.528 |    -0.124 |   -0.082 |      0.29  |     -0.124 |        9078 |        3386 | False     | False        |
