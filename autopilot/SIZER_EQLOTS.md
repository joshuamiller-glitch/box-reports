# SIZER EQUAL-MEAN-LOTS (S4a, 2026-11-03 00:05Z)

Prereg ZL_S4A_PREREG_S1_EQUAL_MEAN_LOTS.md. ts base; ladder engine mean lots 3.010. Multiplier rescaled to the closest achievable engine mean lots (tiered cells give a staircase, so some cells cannot hit 3.01: see eng_mean_lots). PA9 = genuine (scoring week key shifted -4..+4). Cuts are fractions vs the ladder; dmean in $/wk. Placebo rank = share of draws below the real cell at the same mean lots (formula-matched, so placebo lots are approx).

## Per cell

| cell                                 |   eng_mean_lots |   cut_L6M |   cut_PRE |   cut_HOLD |   cut_MID |   cut_X' |   drop_L6M |   dmean_L6M |   dmean_PRE |   pa9_L6M |   pa9_PRE |   pa9_MID | harm_ok   | flag   |
|:-------------------------------------|----------------:|----------:|----------:|-----------:|----------:|---------:|-----------:|------------:|------------:|----------:|----------:|----------:|:----------|:-------|
| ('g13', 'ers_15m_20', 1, 'SIG', 'A') |           3.011 |     0.354 |     0.115 |     -0.177 |    -1.664 |   -0.142 |      0.354 |     1621.54 |     175.658 |     0.224 |     0.084 |    -1.07  | False     | False  |
| ('g12', 'er_3m_100', 'L3', 'D')      |           2.999 |     0.34  |     0.212 |     -0.166 |    -1.651 |   -0.349 |      0.317 |    -3938.28 |   -1218.41  |     0.23  |     0.107 |    -0.888 | False     | False  |
| ('g13', 'ers_15m_20', 1, 'L3', 'A')  |           3.115 |     0.315 |     0.041 |     -0.067 |    -1.422 |    0.006 |      0.469 |     4935.19 |    1158.68  |     0.197 |     0.032 |    -1.006 | False     | False  |
| ('g12', 'er_10m_30', 'L3', 'D')      |           3     |     0.349 |     0.281 |     -0.15  |    -1.655 |   -0.449 |      0.186 |    -5831.88 |   -1384.8   |     0.297 |     0.163 |    -0.942 | False     | False  |
| ('g13', 'ers_15m_20', 1, 'SIG', 'D') |           3.002 |     0.507 |     0.142 |      0.005 |    -1.518 |   -0.265 |      0.103 |    -3589.36 |   -2388.33  |     0.379 |     0.107 |    -0.852 | False     | False  |
| ('g12', 'er_30m_10', 'LIN', 'B')     |           3.017 |     0.256 |     0.103 |      0.178 |    -1.156 |   -0.305 |      0.386 |      821.87 |    1776.47  |     0.21  |     0.051 |    -0.551 | False     | False  |
| ('g12', 'er_15m_20', 'L3', 'A')      |           3.087 |     0.227 |     0.128 |     -0.053 |    -1.587 |   -0.278 |      0.414 |     1869.84 |    1023.1   |     0.163 |     0.061 |    -0.792 | False     | False  |
| ('g12', 'er_15m_20', 'LIVE', 'A')    |           3.185 |     0.112 |    -0.016 |      0.111 |    -1.097 |   -0.137 |      0.227 |     7830.43 |     692.757 |     0.082 |    -0.037 |    -0.703 | False     | False  |
| ('g13', 'ers_10m_20', 1, 'LIN', 'B') |           3.011 |     0.247 |     0.25  |      0.042 |    -1.031 |   -0.092 |      0.157 |     3119.29 |    -492.904 |     0.117 |     0.099 |    -0.585 | False     | False  |
| ('g12', 'er_10m_30', 'LIN', 'B')     |           3.016 |     0.135 |     0.066 |      0.084 |    -1.156 |   -0.103 |      0.389 |     4913.44 |    -656.664 |     0.115 |     0.002 |    -0.62  | False     | False  |
| ('g12', 'er_15m_20', 'LIN', 'B')     |           3.013 |     0.152 |     0.015 |      0.021 |    -1.38  |   -0.002 |      0.4   |     3152.88 |     468.72  |     0.096 |    -0.011 |    -0.715 | False     | False  |

## Placebo ranks

| cell                                 |   rk_cutL6M_perm |   rk_cutPRE_perm |   rk_meanL6M_perm |   rk_meanPRE_perm |
|:-------------------------------------|-----------------:|-----------------:|------------------:|------------------:|
| ('g13', 'ers_15m_20', 1, 'SIG', 'A') |              0.2 |             0.53 |              0.98 |                 1 |
| ('g12', 'er_3m_100', 'L3', 'D')      |            nan   |           nan    |            nan    |               nan |
| ('g13', 'ers_15m_20', 1, 'L3', 'A')  |            nan   |           nan    |            nan    |               nan |
| ('g12', 'er_10m_30', 'L3', 'D')      |            nan   |           nan    |            nan    |               nan |
| ('g13', 'ers_15m_20', 1, 'SIG', 'D') |            nan   |           nan    |            nan    |               nan |
| ('g12', 'er_30m_10', 'LIN', 'B')     |            nan   |           nan    |            nan    |               nan |
| ('g12', 'er_15m_20', 'L3', 'A')      |            nan   |           nan    |            nan    |               nan |
| ('g12', 'er_15m_20', 'LIVE', 'A')    |            nan   |           nan    |            nan    |               nan |
| ('g13', 'ers_10m_20', 1, 'LIN', 'B') |            nan   |           nan    |            nan    |               nan |
| ('g12', 'er_10m_30', 'LIN', 'B')     |            nan   |           nan    |            nan    |               nan |
| ('g12', 'er_15m_20', 'LIN', 'B')     |            nan   |           nan    |            nan    |               nan |
