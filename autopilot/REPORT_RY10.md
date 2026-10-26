# REPORT RY10

RY10 retraining cadence sensitivity of K4 (monthly, quarterly, semiannual, annual; 3-seed ensembles).


| cell                                  |   trades |   sharpe |   clean |    H1 |    H2 |   nullrank |   gates | rw1   |   rw1_lo |   bhSh | era               |
|:--------------------------------------|---------:|---------:|--------:|------:|------:|-----------:|--------:|:------|---------:|-------:|:------------------|
| cad=M, delta=0.08, N=1, mode=longonly |      246 |    1.524 |   0.219 | 0.374 | 0.314 |      1.000 |       6 | FAIL  |   -0.216 |  0.681 | positive pre-2023 |
| cad=Q, delta=0.08, N=1, mode=longonly |      238 |    1.662 |   0.231 | 0.234 | 0.331 |      0.995 |       6 | FAIL  |    0.008 |  0.677 | positive pre-2023 |
| cad=S, delta=0.08, N=1, mode=longonly |      229 |    1.929 |   0.334 | 0.151 | 0.514 |      1.000 |       6 | FAIL  |    0.263 |  0.686 | positive pre-2023 |
| cad=A, delta=0.08, N=1, mode=longonly |      241 |    1.675 |   0.266 | 0.070 | 0.306 |      1.000 |       4 | FAIL  |   -0.009 |  0.677 | positive pre-2023 |

### cad=M, delta=0.08, N=1, mode=longonly
- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.219 / +0.374 / +0.314
- [PASS] 3 worst week within share: all-in worst week +2.4% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.52 vs p95 0.92 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.113, +0.395]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.214 / +0.370 / +0.308
- [PASS] 6 worst-decile corr <=+0.30: -0.24

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.52 vs scaled buy-and-hold 0.68; paired-bootstrap 90% CI of the difference [-0.22, +1.82]; exposure ES 9.1%, NQ 8.8%, RTY 7.0%, YM 5.7%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.38 | 0.49 | +0.219 | +0.037 |
| H1 | 2.15 | 1.49 | +0.374 | +0.333 |
| H2 | 1.63 | 0.74 | +0.314 | +0.117 |
| all | 1.52 | 0.68 | +0.250 | +0.084 |

### cad=Q, delta=0.08, N=1, mode=longonly
- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.231 / +0.234 / +0.331
- [PASS] 3 worst week within share: all-in worst week +1.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.66 vs p95 1.01 (rank 0.99)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.133, +0.368]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.228 / +0.231 / +0.326
- [PASS] 6 worst-decile corr <=+0.30: -0.11

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.66 vs scaled buy-and-hold 0.68; paired-bootstrap 90% CI of the difference [+0.01, +2.01]; exposure ES 8.5%, NQ 8.6%, RTY 7.0%, YM 5.6%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.47 | 0.49 | +0.231 | +0.037 |
| H1 | 2.30 | 1.50 | +0.234 | +0.335 |
| H2 | 2.30 | 0.73 | +0.331 | +0.116 |
| all | 1.66 | 0.68 | +0.246 | +0.084 |

### cad=S, delta=0.08, N=1, mode=longonly
- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.334 / +0.151 / +0.514
- [PASS] 3 worst week within share: all-in worst week +3.3% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.93 vs p95 1.05 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.186, +0.514]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.329 / +0.147 / +0.507
- [PASS] 6 worst-decile corr <=+0.30: +0.01

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.93 vs scaled buy-and-hold 0.69; paired-bootstrap 90% CI of the difference [+0.26, +2.23]; exposure ES 8.5%, NQ 8.5%, RTY 6.3%, YM 5.2%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.95 | 0.50 | +0.334 | +0.038 |
| H1 | 1.13 | 1.48 | +0.151 | +0.330 |
| H2 | 2.31 | 0.76 | +0.514 | +0.119 |
| all | 1.93 | 0.69 | +0.345 | +0.085 |

### cad=A, delta=0.08, N=1, mode=longonly
- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.266 / +0.070 / +0.306
- [PASS] 3 worst week within share: all-in worst week +1.9% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.67 vs p95 1.06 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.114, +0.369]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 0
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.263 / +0.068 / +0.302
- [PASS] 6 worst-decile corr <=+0.30: -0.06

## RW1 criterion (exposure-matched buy-and-hold)
**FAIL**: all-in Sharpe sleeve 1.67 vs scaled buy-and-hold 0.68; paired-bootstrap 90% CI of the difference [-0.01, +2.00]; exposure ES 8.5%, NQ 8.5%, RTY 6.7%, YM 6.3%

| span | sleeve Sharpe | B&H Sharpe | sleeve 20% uplift | B&H 20% uplift |
|---|---|---|---|---|
| clean | 1.76 | 0.49 | +0.266 | +0.037 |
| H1 | 0.59 | 1.51 | +0.070 | +0.340 |
| H2 | 2.02 | 0.71 | +0.306 | +0.113 |
| all | 1.67 | 0.68 | +0.237 | +0.084 |


Runtime 0.6 min, 10-worker pool.
DONE RY10