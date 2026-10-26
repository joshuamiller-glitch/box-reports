# REPORT RX7P - confirmation of RX7 (K4 with an asymmetric short threshold), K4v2 protocol
**Verdict: FOUND-PENDING (all gates pass; replication short)** (9/9 gates; replications 1/3 countable, newest weeks unavailable). Cell {'model': 'd2', 'N': 1, 'dl': 0.08, 'ds': 0.04}: additive 20% clean/H1/H2/all +0.15/+0.29/+0.17/+0.16; standalone Sharpe 1.19; 325 trades. 10-worker pool.

Registered after the RX7 result (PREREG_AUTOPILOT.md RX7P).

## Gates

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.152 / +0.291 / +0.165
- [PASS] 3 worst week within share: all-in worst week +9.8% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.19 vs p95 1.10 (rank 0.96)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.041, +0.290]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 82% of 11
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.146 / +0.288 / +0.162
- [PASS] 6 worst-decile corr <=+0.30: +0.23
- [PASS] 4 drift-matched (month-stratified) null p95: real 1.19 vs p95 0.54 (rank 1.00)
- [PASS] 4 beta test alpha CI lower >0: beta +0.097; alpha Sharpe 1.03 CI [+0.13, +1.82]

Plateau: {'model': 'd2', 'N': '1', 'dl': '0.06', 'ds': '0.04'}: +0.279; {'model': 'd2', 'N': '1', 'dl': '0.1', 'ds': '0.04'}: +0.096; {'model': 'd2', 'N': '1', 'dl': '0.08', 'ds': '0.03'}: +0.152; {'model': 'd2', 'N': '1', 'dl': '0.08', 'ds': '0.05'}: +0.168; {'model': 'd2_t112', 'N': '1', 'dl': '0.08', 'ds': '0.04'}: +0.103; {'model': 'd2_t188', 'N': '1', 'dl': '0.08', 'ds': '0.04'}: +0.163; {'model': 'd2_l0375', 'N': '1', 'dl': '0.08', 'ds': '0.04'}: +0.144; {'model': 'd2_l0625', 'N': '1', 'dl': '0.08', 'ds': '0.04'}: +0.213; {'model': 'd2_s1', 'N': '1', 'dl': '0.08', 'ds': '0.04'}: +0.202; {'model': 'd2_s2', 'N': '1', 'dl': '0.08', 'ds': '0.04'}: +0.141; {'model': 'd2_s3', 'N': '1', 'dl': '0.08', 'ds': '0.04'}: +0.196

## Replication (each >= +0.081)
- R2 H0: +0.021 FAIL
- R3 NQ+ES-trained model on RTY+YM (same rule): +0.038 FAIL
- R4 alternating months select/read over the 12-cell grid: odd-selected (0.08, 0.03) read on even +0.108; even-selected (0.06, 0.05) read on odd +0.128 PASS

## Legs (report only)
- long-only: standalone all-in Sharpe 1.43, 20% uplift +0.176, pair-window trades 267
- short-only: standalone all-in Sharpe -0.08, 20% uplift -0.013, pair-window trades 58

ERA 2016-22 walk-forward: positive pre-2023; weekly Sharpe gross/fixed/scaled 0.26/0.04/0.14 (2477 trades).

DONE RX7P