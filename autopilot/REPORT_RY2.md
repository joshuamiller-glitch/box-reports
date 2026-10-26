# REPORT RY2

RY2 per-instrument standalone tests (ES, NQ, RTY, YM) of the RX5 signal and the RY1 rule, each against its own exposure-matched buy-and-hold.


| cell               |   trades |   sharpe |   clean |     H1 |     H2 |   nullrank |   gates | rw1   |   rw1_lo |   bhSh | era                                    |
|:-------------------|---------:|---------:|--------:|-------:|-------:|-----------:|--------:|:------|---------:|-------:|:---------------------------------------|
| inst=ES, sig=rx5   |       66 |    1.670 |   0.256 |  0.165 |  0.307 |      1.000 |       6 | FAIL  |   -0.121 |  0.761 | gross-positive, cost-negative pre-2023 |
| inst=ES, sig=rule  |      420 |    0.959 |   0.196 |  0.216 |  0.085 |      0.920 |       1 | FAIL  |   -0.541 |  0.761 | positive pre-2023                      |
| inst=NQ, sig=rx5   |       61 |    1.523 |   0.257 |  0.117 |  0.275 |      0.980 |       5 | FAIL  |   -0.367 |  0.849 | positive pre-2023                      |
| inst=NQ, sig=rule  |      420 |    1.064 |   0.210 |  0.129 |  0.125 |      0.900 |       3 | FAIL  |   -0.547 |  0.849 | positive pre-2023                      |
| inst=RTY, sig=rx5  |       58 |    1.486 |   0.229 |  0.322 |  0.311 |      1.000 |       6 | FAIL  |    0.293 |  0.206 | negative pre-2023                      |
| inst=RTY, sig=rule |      420 |   -0.289 |  -0.022 | -0.070 | -0.227 |      0.185 |       1 | FAIL  |   -1.256 |  0.206 | positive pre-2023                      |
| inst=YM, sig=rx5   |       40 |    1.130 |   0.187 |  0.028 |  0.154 |      0.980 |       4 | FAIL  |   -0.614 |  0.519 | positive pre-2023                      |
| inst=YM, sig=rule  |      420 |    0.592 |   0.086 |  0.288 |  0.022 |      0.810 |       2 | FAIL  |   -0.638 |  0.519 | positive pre-2023                      |

### inst=ES, sig=rx5
- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.256 / +0.165 / +0.307
- [PASS] 3 worst week within share: all-in worst week +10.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.67 vs p95 0.94 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.112, +0.404]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.250 / +0.160 / +0.301
- [PASS] 6 worst-decile corr <=+0.30: +0.18

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.67 vs scaled buy-and-hold 0.76; paired-bootstrap 90% CI of the difference [-0.12, +1.89]; exposure ES 8.2%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.56 | 0.63 | +0.256 | +0.063 |
| H1 | 1.80 | 1.10 | +0.165 | +0.260 |
| H2 | 2.08 | 0.99 | +0.307 | +0.154 |
| all | 1.67 | 0.76 | +0.252 | +0.100 |

### inst=ES, sig=rule
- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.196 / +0.216 / +0.085
- [FAIL] 3 worst week within share: all-in worst week +24.6% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.96 vs p95 1.04 (rank 0.92)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.028, +0.346]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.167 / +0.188 / +0.065
- [PASS] 6 worst-decile corr <=+0.30: -0.05

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 0.96 vs scaled buy-and-hold 0.76; paired-bootstrap 90% CI of the difference [-0.54, +0.94]; exposure ES 52.4%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.24 | 0.63 | +0.196 | +0.063 |
| H1 | 0.27 | 1.10 | +0.216 | +0.260 |
| H2 | 0.65 | 0.99 | +0.085 | +0.154 |
| all | 0.96 | 0.76 | +0.159 | +0.100 |

### inst=NQ, sig=rx5
- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.257 / +0.117 / +0.275
- [PASS] 3 worst week within share: all-in worst week +2.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.52 vs p95 1.16 (rank 0.98)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.103, +0.368]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.256 / +0.116 / +0.274
- [FAIL] 6 worst-decile corr <=+0.30: +0.38

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.52 vs scaled buy-and-hold 0.85; paired-bootstrap 90% CI of the difference [-0.37, +1.64]; exposure NQ 7.6%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.61 | 0.68 | +0.257 | +0.061 |
| H1 | 0.59 | 0.72 | +0.117 | +0.149 |
| H2 | 2.20 | 1.47 | +0.275 | +0.228 |
| all | 1.52 | 0.85 | +0.232 | +0.101 |

### inst=NQ, sig=rule
- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.210 / +0.129 / +0.125
- [FAIL] 3 worst week within share: all-in worst week +28.9% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 1.06 vs p95 1.21 (rank 0.90)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.017, +0.345]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.205 / +0.124 / +0.121
- [PASS] 6 worst-decile corr <=+0.30: -0.13

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.06 vs scaled buy-and-hold 0.85; paired-bootstrap 90% CI of the difference [-0.55, +0.99]; exposure NQ 52.4%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.35 | 0.68 | +0.210 | +0.061 |
| H1 | -0.04 | 0.72 | +0.129 | +0.149 |
| H2 | 0.98 | 1.47 | +0.125 | +0.228 |
| all | 1.06 | 0.85 | +0.166 | +0.101 |

### inst=RTY, sig=rx5
- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.229 / +0.322 / +0.311
- [PASS] 3 worst week within share: all-in worst week +0.0% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.49 vs p95 0.92 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.118, +0.388]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.225 / +0.319 / +0.306
- [PASS] 6 worst-decile corr <=+0.30: -0.09

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.49 vs scaled buy-and-hold 0.21; paired-bootstrap 90% CI of the difference [+0.29, +2.29]; exposure RTY 7.2%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.38 | -0.02 | +0.229 | -0.047 |
| H1 | 1.40 | 2.13 | +0.322 | +0.375 |
| H2 | 1.86 | -0.47 | +0.311 | -0.035 |
| all | 1.49 | 0.21 | +0.248 | +0.008 |

### inst=RTY, sig=rule
- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.022 / -0.070 / -0.227
- [FAIL] 3 worst week within share: all-in worst week +26.2% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.29 vs p95 0.67 (rank 0.18)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.263, +0.092]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.040 / -0.087 / -0.240
- [PASS] 6 worst-decile corr <=+0.30: -0.01

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve -0.29 vs scaled buy-and-hold 0.21; paired-bootstrap 90% CI of the difference [-1.26, +0.22]; exposure RTY 52.4%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 0.05 | -0.02 | -0.022 | -0.047 |
| H1 | -0.76 | 2.13 | -0.070 | +0.375 |
| H2 | -1.10 | -0.47 | -0.227 | -0.035 |
| all | -0.29 | 0.21 | -0.083 | +0.008 |

### inst=YM, sig=rx5
- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.187 / +0.028 / +0.154
- [PASS] 3 worst week within share: all-in worst week +0.0% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.13 vs p95 0.93 (rank 0.98)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.011, +0.315]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.184 / +0.025 / +0.149
- [PASS] 6 worst-decile corr <=+0.30: -0.05

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.13 vs scaled buy-and-hold 0.52; paired-bootstrap 90% CI of the difference [-0.61, +1.74]; exposure YM 5.0%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.33 | 0.39 | +0.187 | +0.030 |
| H1 | 1.51 | 1.91 | +0.028 | +0.491 |
| H2 | 0.31 | -0.14 | +0.154 | -0.001 |
| all | 1.13 | 0.52 | +0.159 | +0.070 |

### inst=YM, sig=rule
- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.086 / +0.288 / +0.022
- [PASS] 3 worst week within share: all-in worst week +13.7% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.59 vs p95 0.91 (rank 0.81)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.089, +0.268]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.071 / +0.274 / +0.012
- [PASS] 6 worst-decile corr <=+0.30: +0.03

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 0.59 vs scaled buy-and-hold 0.52; paired-bootstrap 90% CI of the difference [-0.64, +0.73]; exposure YM 52.4%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 0.59 | 0.39 | +0.086 | +0.030 |
| H1 | 0.99 | 1.91 | +0.288 | +0.491 |
| H2 | 0.28 | -0.14 | +0.022 | -0.001 |
| all | 0.59 | 0.52 | +0.089 | +0.070 |


Rule used for the per-instrument rule cells (selected in RY1): r3

Runtime 1.0 min, 10-worker pool.
DONE RY2