# REPORT RY3

RY3 NKD cross-check: the VIX rule and the US-trained K4 transfer model applied to Nikkei futures.


| cell         |   trades |   sharpe |   clean |    H1 |    H2 |   nullrank |   gates | rw1   |   rw1_lo |   bhSh | era                                    |
|:-------------|---------:|---------:|--------:|------:|------:|-----------:|--------:|:------|---------:|-------:|:---------------------------------------|
| sig=rule     |      420 |    0.666 |   0.108 | 0.150 | 0.165 |      0.695 |       2 | FAIL  |   -1.116 |  1.012 | gross-positive, cost-negative pre-2023 |
| sig=transfer |       70 |    1.058 |   0.097 | 0.291 | 0.341 |      0.955 |       3 | FAIL  |   -1.075 |  1.012 | positive pre-2023                      |

### sig=rule
- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.108 / +0.150 / +0.165
- [FAIL] 3 worst week within share: all-in worst week +21.6% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.67 vs p95 1.14 (rank 0.69)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.066, +0.324]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.058 / +0.112 / +0.146
- [PASS] 6 worst-decile corr <=+0.30: -0.20

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 0.67 vs scaled buy-and-hold 1.01; paired-bootstrap 90% CI of the difference [-1.12, +0.39]; exposure NKD 52.3%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 0.57 | 0.40 | +0.108 | +0.072 |
| H1 | 0.72 | 3.33 | +0.150 | +0.691 |
| H2 | 0.91 | 1.22 | +0.165 | +0.258 |
| all | 0.67 | 1.01 | +0.128 | +0.199 |

### sig=transfer
- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.097 / +0.291 / +0.341
- [PASS] 3 worst week within share: all-in worst week +13.5% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.06 vs p95 1.05 (rank 0.95)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.018, +0.364]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.083 / +0.275 / +0.330
- [PASS] 6 worst-decile corr <=+0.30: -0.11

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.06 vs scaled buy-and-hold 1.01; paired-bootstrap 90% CI of the difference [-1.07, +1.11]; exposure NKD 8.7%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 0.85 | 0.40 | +0.097 | +0.072 |
| H1 | 1.45 | 3.33 | +0.291 | +0.691 |
| H2 | 1.32 | 1.22 | +0.341 | +0.258 |
| all | 1.06 | 1.01 | +0.167 | +0.199 |


Runtime 0.3 min, 10-worker pool.
DONE RY3