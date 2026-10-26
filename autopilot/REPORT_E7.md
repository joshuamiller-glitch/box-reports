# REPORT E7 - K4v2 symmetric: long-short and beta-neutral versions (pre-registered, PREREG_AUTOPILOT.md E-block)
## E7a long-short (unhedged), d2 N=1 delta 0.08
**Verdict: FOUND-PENDING (all gates pass; replication short: H0 not met, and the alternating-month and cross-instrument checks here reuse the pooled model so they are weaker than the Amendment-2 select/read and train-elsewhere tests of K4v2)** (9/9 gates; replications 2/3: H0 FAIL (+0.081), alternating months PASS (odd +0.145 / even +0.145), cross-instrument (each single-instrument sleeve, own-scaled to the pair clean sd, 20% uplift >= 50% of the pooled uplift; ES and RTY where traded) PASS). Additive 20% clean/H1/H2/all +0.14/+0.37/+0.18/+0.17; standalone all-in weekly Sharpe 1.22; 274 trades; ERA flag positive pre-2023.

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.139 / +0.372 / +0.183
- [PASS] 3 worst week within share: all-in worst week +11.1% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.22 vs p95 1.06 (rank 0.98)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.051, +0.292]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 78% of 9
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.134 / +0.369 / +0.179
- [PASS] 6 worst-decile corr <=+0.30: +0.26
- [PASS] 4 drift-matched (month-stratified) null p95: real 1.22 vs p95 0.50 (rank 1.00)
- [PASS] 4 beta test alpha CI lower >0: beta +0.178; alpha Sharpe 1.02 CI [+0.10, +1.83]; always-long Sharpe 0.60

| share | framing | clean | H1 | H2 | all | worst wk chg % | boot 90% CI |
|---|---|---|---|---|---|---|---|
| 10% | add | +0.078 | +0.192 | +0.094 | +0.093 | +5.2 | [+0.032, +0.159] |
| 20% | add | +0.139 | +0.372 | +0.183 | +0.170 | +11.1 | [+0.051, +0.292] |
| 30% | add | +0.183 | +0.537 | +0.266 | +0.231 | +17.0 | [+0.057, +0.409] |
| 50% | add | +0.229 | +0.814 | +0.412 | +0.308 | +28.9 | [+0.026, +0.586] |
| 10% | const | +0.085 | +0.213 | +0.105 | +0.103 | -4.8 | [+0.035, +0.175] |
| 20% | const | +0.163 | +0.457 | +0.226 | +0.203 | -8.7 | [+0.055, +0.354] |
| 30% | const | +0.218 | +0.724 | +0.363 | +0.287 | -12.7 | [+0.044, +0.531] |
| 50% | const | +0.197 | +1.187 | +0.647 | +0.313 | -6.7 | [-0.187, +0.813] |

Per-instrument standalone Sharpe / own-scaled 20% uplift: ES 1.62 / +0.278; NQ 1.08 / +0.153; RTY 0.70 / +0.099; YM 0.57 / +0.041
Correlation: worst-decile +0.26, all +0.03. ERA: gross/fixed/scaled weekly Sharpe 2013-22 0.46/0.27/0.35 on 2169 trades.

## E7b beta-neutral long-only vs ES (NQ, RTY, YM legs)
**Verdict: NO** (2/9 gates; replications 1/3: H0 PASS (-0.016), alternating months FAIL (odd -0.008 / even -0.216), cross-instrument (each single-instrument sleeve, own-scaled to the pair clean sd, 20% uplift >= 50% of the pooled uplift; ES and RTY where traded) FAIL). Additive 20% clean/H1/H2/all -0.11/+0.13/-0.17/-0.10; standalone all-in weekly Sharpe -0.33; 183 trades; ERA flag gross-positive, cost-negative pre-2023.

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.112 / +0.130 / -0.168
- [PASS] 3 worst week within share: all-in worst week +19.9% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.33 vs p95 0.43 (rank 0.59)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.250, +0.052]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 9
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.156 / +0.098 / -0.206
- [PASS] 6 worst-decile corr <=+0.30: -0.13
- [FAIL] 4 drift-matched (month-stratified) null p95: real -0.33 vs p95 0.46 (rank 0.53)
- [FAIL] 4 beta test alpha CI lower >0: beta +0.004; alpha Sharpe -0.36 CI [-1.26, +0.58]; always-long Sharpe 0.60

| share | framing | clean | H1 | H2 | all | worst wk chg % | boot 90% CI |
|---|---|---|---|---|---|---|---|
| 10% | add | -0.050 | +0.072 | -0.078 | -0.042 | +6.8 | [-0.117, +0.034] |
| 20% | add | -0.112 | +0.130 | -0.168 | -0.098 | +19.9 | [-0.250, +0.052] |
| 30% | add | -0.184 | +0.173 | -0.267 | -0.165 | +33.2 | [-0.395, +0.056] |
| 50% | add | -0.342 | +0.215 | -0.483 | -0.323 | +59.7 | [-0.700, +0.036] |
| 10% | const | -0.056 | +0.079 | -0.087 | -0.047 | -2.7 | [-0.131, +0.037] |
| 20% | const | -0.147 | +0.154 | -0.217 | -0.130 | +1.2 | [-0.322, +0.056] |
| 30% | const | -0.284 | +0.207 | -0.404 | -0.264 | +5.2 | [-0.590, +0.046] |
| 50% | const | -0.718 | +0.096 | -1.004 | -0.731 | +41.6 | [-1.388, -0.100] |

Per-instrument standalone Sharpe / own-scaled 20% uplift: NQ 0.45 / +0.026; RTY -0.41 / -0.097; YM -0.59 / -0.156
Correlation: worst-decile -0.13, all +0.02. ERA: gross/fixed/scaled weekly Sharpe 2013-22 0.15/-0.93/-0.54 on 1415 trades.

## E7c beta-neutral long-short vs ES
**Verdict: NO** (2/9 gates; replications 1/3: H0 PASS (-0.013), alternating months FAIL (odd -0.000 / even -0.272), cross-instrument (each single-instrument sleeve, own-scaled to the pair clean sd, 20% uplift >= 50% of the pooled uplift; ES and RTY where traded) FAIL). Additive 20% clean/H1/H2/all -0.17/+0.11/-0.13/-0.13; standalone all-in weekly Sharpe -0.59; 187 trades; ERA flag gross-positive, cost-negative pre-2023.

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.173 / +0.106 / -0.126
- [PASS] 3 worst week within share: all-in worst week +13.9% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real -0.59 vs p95 0.37 (rank 0.43)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.289, +0.013]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 9
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.210 / +0.081 / -0.156
- [PASS] 6 worst-decile corr <=+0.30: -0.13
- [FAIL] 4 drift-matched (month-stratified) null p95: real -0.59 vs p95 0.36 (rank 0.38)
- [FAIL] 4 beta test alpha CI lower >0: beta +0.002; alpha Sharpe -0.60 CI [-1.37, +0.34]; always-long Sharpe 0.60

| share | framing | clean | H1 | H2 | all | worst wk chg % | boot 90% CI |
|---|---|---|---|---|---|---|---|
| 10% | add | -0.081 | +0.057 | -0.059 | -0.058 | +4.5 | [-0.136, +0.011] |
| 20% | add | -0.173 | +0.106 | -0.126 | -0.129 | +13.9 | [-0.289, +0.013] |
| 30% | add | -0.275 | +0.146 | -0.199 | -0.211 | +24.2 | [-0.456, +0.005] |
| 50% | add | -0.487 | +0.199 | -0.360 | -0.393 | +94.7 | [-0.801, -0.028] |
| 10% | const | -0.090 | +0.063 | -0.066 | -0.066 | -5.1 | [-0.152, +0.012] |
| 20% | const | -0.223 | +0.127 | -0.162 | -0.169 | -4.7 | [-0.371, +0.010] |
| 30% | const | -0.411 | +0.184 | -0.301 | -0.326 | +11.6 | [-0.677, -0.013] |
| 50% | const | -0.959 | +0.181 | -0.780 | -0.850 | +120.9 | [-1.541, -0.174] |

Per-instrument standalone Sharpe / own-scaled 20% uplift: NQ 0.45 / +0.026; RTY -0.64 / -0.127; YM -0.80 / -0.174
Correlation: worst-decile -0.13, all -0.00. ERA: gross/fixed/scaled weekly Sharpe 2013-22 0.03/-1.18/-0.69 on 1574 trades.

Reading: if the edge were beta the symmetric and beta-neutral versions would die; see verdict lines. Fill model: 16:16 ET px entry/exit, 1 tick/side + $4.36 per contract per leg (hedge leg costed), 2x slippage in the gate table. NT8: daily signal file; the hedge leg is a short (long) ES order of beta x q contracts; margin = X legs + ES hedge margins (hedge reduces net exposure). K4 predictions unchanged (frozen ap_k_fams).

DONE E7