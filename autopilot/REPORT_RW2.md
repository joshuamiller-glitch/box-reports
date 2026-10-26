# REPORT RW2 - K4 feature-block ablation (pre-registered, no selection)

Rule for every model: d2, N=1, delta 0.08, longonly, walk-forward from 2016 (same code as K4); gates are the J-gate set per cell (7 gate lines; plateau neighbours only delta +-25%), null 200 draws.

| fs        |   trades |   sharpe |   clean |     H1 |     H2 |   allup |   nullrank |   gates | era                                    |
|:----------|---------:|---------:|--------:|-------:|-------:|--------:|-----------:|--------:|:---------------------------------------|
| PRICE     |      315 |    0.922 |   0.113 |  0.176 |  0.031 |   0.090 |      0.940 |       1 | gross-positive, cost-negative pre-2023 |
| PRICE+VIX |      265 |    1.590 |   0.306 |  0.256 |  0.239 |   0.276 |      1.000 |       6 | positive pre-2023                      |
| PRICE+COT |      352 |    0.383 |  -0.003 |  0.245 | -0.015 |   0.008 |      0.635 |       2 | positive pre-2023                      |
| PRICE+CAL |      325 |    0.884 |   0.195 | -0.077 |  0.023 |   0.111 |      0.875 |       2 | gross-positive, cost-negative pre-2023 |
| FULL-VIX  |      394 |    1.338 |   0.184 |  0.357 |  0.077 |   0.168 |      0.990 |       4 | positive pre-2023                      |
| FULL-COT  |      254 |    1.717 |   0.235 |  0.307 |  0.320 |   0.258 |      0.995 |       6 | positive pre-2023                      |
| FULL-CAL  |      265 |    1.338 |   0.213 |  0.265 |  0.157 |   0.195 |      0.970 |       6 | positive pre-2023                      |
| FULL      |      265 |    1.805 |   0.243 |  0.472 |  0.369 |   0.287 |      0.995 |       6 | positive pre-2023                      |

- Block VIX: removing it moves the all-in uplift from +0.287 to +0.168 (-42%); PRICE+VIX gives +0.276; PRICE alone +0.090.
- Block COT: removing it moves the all-in uplift from +0.287 to +0.258 (-10%); PRICE+COT gives +0.008; PRICE alone +0.090.
- Block CAL: removing it moves the all-in uplift from +0.287 to +0.195 (-32%); PRICE+CAL gives +0.111; PRICE alone +0.090.

Blocks that satisfy the pre-registered carrier rule (removal lowers the uplift >= 50 percent AND the block with PRICE restores >= 50 percent): none. PRICE-only uplift +0.090 (31% of FULL): the price block alone does not carry the signal.

Runtime 1.0 min. DONE R2