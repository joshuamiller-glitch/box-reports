# REPORT RX5
**Verdict: LEAD** (8/9 gates; H0 +0.094 FAIL; odd/even months +0.232/+0.272 PASS). Cell {'var': 'base', 'ss': 'A', 'delta': 0.08, 'N': 1, 'mode': 'longonly'}: additive 20% uplift clean/H1/H2/all +0.28/+0.20/+0.33/+0.27; standalone all-in weekly Sharpe 1.78; 225 trades. 10-worker pool.

RX5 K4 with the probability averaged over 5 seeds (single pre-declared cell, plateau defined up front).


Fill model: 16:16 ET px entry/exit, 1 tick/side + $4.36 per contract RT, 1 ADR-dollar per trade; additive and constant-risk framings below.

| share | framing | clean | H1 | H2 | all | worst wk chg % | boot 90% CI |
|---|---|---|---|---|---|---|---|
| 10% | add | +0.149 | +0.107 | +0.169 | +0.145 | +0.7 | [+0.082, +0.215] |
| 20% | add | +0.277 | +0.202 | +0.326 | +0.270 | +2.2 | [+0.151, +0.403] |
| 30% | add | +0.385 | +0.284 | +0.469 | +0.376 | +3.8 | [+0.204, +0.562] |
| 50% | add | +0.540 | +0.411 | +0.704 | +0.530 | +6.8 | [+0.259, +0.810] |
| 10% | const | +0.164 | +0.118 | +0.187 | +0.159 | -9.2 | [+0.090, +0.237] |
| 20% | const | +0.334 | +0.245 | +0.399 | +0.326 | -17.6 | [+0.180, +0.487] |
| 30% | const | +0.493 | +0.372 | +0.628 | +0.484 | -26.0 | [+0.249, +0.732] |
| 50% | const | +0.688 | +0.536 | +1.002 | +0.664 | -35.7 | [+0.201, +1.152] |

Correlation: worst-decile +0.13, all +0.04. Per-instrument own-scaled 20% uplift: ES +0.252; NQ +0.232; RTY +0.248; YM +0.159

## Gate checklist

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.277 / +0.202 / +0.326
- [PASS] 3 worst week within share: all-in worst week +2.2% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.78 vs p95 1.04 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.151, +0.403]
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.273 / +0.199 / +0.321
- [PASS] 6 worst-decile corr <=+0.30: +0.13
- [PASS] 4 drift-matched (month-stratified) null p95: real 1.78 vs p95 0.67 (rank 1.00)
- [PASS] 4 beta test alpha CI lower >0: beta +0.111; alpha Sharpe 1.58 CI [+0.81, +2.25]; always-long Sharpe 0.65
- [FAIL] 5 plateau (pre-registered: >= 7 of 8 keep >= 75%): 75% of 8

Plateau neighbours (all-in uplift; selected +0.270): {'var': 'base', 'ss': 'A', 'delta': '0.06', 'N': '1', 'mode': 'longonly'}: +0.406; {'var': 'base', 'ss': 'A', 'delta': '0.1', 'N': '1', 'mode': 'longonly'}: +0.105; {'var': 't112', 'ss': 'A', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.237; {'var': 't188', 'ss': 'A', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.285; {'var': 'l0375', 'ss': 'A', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.197; {'var': 'l0625', 'ss': 'A', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.305; {'var': 'base', 'ss': 'B', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.213; {'var': 'base', 'ss': 'C', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.220

## ERA (walk-forward 2016-22): positive pre-2023; weekly Sharpe gross/fixed/scaled 0.43/0.27/0.33 on 1916 trades

NT8: daily signal file after the 16:15 ET model refresh; seed ensemble = mean of five LightGBM models retrained quarterly offline; market entry 16:16 ET, exit next 16:16 ET. Margin as K4v2 (contracts per signal scale with 1/ADR; see REPORT_K4V2.md).

DONE RX5