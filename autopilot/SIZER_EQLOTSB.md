# SIZER EQUAL-MEAN-LOTS (S4a, 2026-11-03 01:21Z)

Prereg ZL_S4A_PREREG_S1_EQUAL_MEAN_LOTS.md. ts base; ladder engine mean lots 3.010. Multiplier rescaled to the closest achievable engine mean lots (tiered cells give a staircase, so some cells cannot hit 3.01: see eng_mean_lots). PA9 = genuine (scoring week key shifted -4..+4). Cuts are fractions vs the ladder; dmean in $/wk. Placebo rank = share of draws below the real cell at the same mean lots (formula-matched, so placebo lots are approx).

## Per cell

| cell                      |   eng_mean_lots |   cut_L6M |   cut_PRE |   cut_HOLD |   cut_MID |   cut_X' |   drop_L6M |   dmean_L6M |   dmean_PRE |   pa9_L6M |   pa9_PRE |   pa9_MID | harm_ok   | flag   |
|:--------------------------|----------------:|----------:|----------:|-----------:|----------:|---------:|-----------:|------------:|------------:|----------:|----------:|----------:|:----------|:-------|
| A|PE|london|t0.20_0.5_1.0 |           3.029 |     0.288 |     0.012 |      0.098 |    -0.014 |   -0.167 |     -0.042 |     3498.05 |    -128.351 |     0.269 |     0.012 |    -0.041 | True      | False  |
| A|PE|london|t0.25_0.5_1.0 |           2.997 |     0.256 |     0.023 |      0.218 |    -0.027 |   -0.167 |     -0.067 |     2617.67 |     -26.475 |     0.247 |     0.024 |    -0.036 | True      | False  |
| A|KB|asia|t0.50_0.5_1.5   |           2.997 |     0.25  |    -0.015 |      0.227 |    -0.03  |    0.094 |     -0.063 |     2188.18 |     310.637 |     0.219 |    -0.031 |    -0.044 | True      | False  |
| A|KB|asia|t0.50_0.75_1.25 |           3.047 |     0.182 |     0.024 |      0.164 |    -0.227 |   -0.01  |      0.035 |     1901.78 |      63.341 |     0.173 |     0.024 |    -0.144 | True      | True   |

## Placebo ranks

| cell                      |   rk_cutL6M_perm |   rk_cutPRE_perm |   rk_meanL6M_perm |   rk_meanPRE_perm |   rk_cutL6M_dayshuf |   rk_cutPRE_dayshuf |   rk_meanL6M_dayshuf |   rk_meanPRE_dayshuf |   rk_cutL6M_ar1 |   rk_cutPRE_ar1 |   rk_meanL6M_ar1 |   rk_meanPRE_ar1 |
|:--------------------------|-----------------:|-----------------:|------------------:|------------------:|--------------------:|--------------------:|---------------------:|---------------------:|----------------:|----------------:|-----------------:|-----------------:|
| A|PE|london|t0.20_0.5_1.0 |             0.3  |             0.19 |              0.98 |              0.79 |                0.3  |                0.28 |                 0.95 |                 0.9  |            0.3  |            0.2  |             0.99 |             0.85 |
| A|PE|london|t0.25_0.5_1.0 |             0.28 |             0.21 |              0.93 |              0.65 |                0.28 |                0.36 |                 0.91 |                 0.86 |            0.32 |            0.29 |             0.94 |             0.8  |
| A|KB|asia|t0.50_0.5_1.5   |             0.24 |             0.29 |              0.95 |              0.94 |                0.24 |                0.4  |                 0.87 |                 0.9  |            0.25 |            0.24 |             0.96 |             0.89 |
| A|KB|asia|t0.50_0.75_1.25 |             0.18 |             0.28 |              0.98 |              0.91 |                0.13 |                0.35 |                 0.91 |                 0.93 |            0.19 |            0.34 |             0.96 |             0.89 |

## Reading
S1B type-A cells rescaled to the ladder's engine mean lots (ts). A|KB|asia|t0.50_0.75_1.25 (lots 3.047) satisfies the mechanical flag rule: cut L6M .182, PRE .024, carrying-week-dropped L6M cut .035, dmean L6M +1.9k and PRE +63, genuine PA9 L6M .173 / PRE .024 / MID -.144 / X' -.010 (no-harm). It is a FLAG only: PRE and carried-dropped cuts are below the flip-5 band, and placebo cut ranks at equal lots are .13-.19 L6M, .28-.35 PRE (placebos match or beat it). The two PE london cells lose their PRE cut at equal lots (.012, .023) and their carried-dropped L6M cut turns negative (-.042, -.067): their earlier cut came from running fewer lots (2.90-2.93 vs 3.01).
