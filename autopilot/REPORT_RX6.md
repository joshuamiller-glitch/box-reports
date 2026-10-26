# REPORT RX6
**Verdict: NO** (4/9 gates; H0 +0.045 FAIL; odd/even months +0.166/+0.214 PASS). Cell {'var': 'base', 'ss': 'A', 'delta': 0.08, 'N': 1, 'mode': 'longonly'}: additive 20% uplift clean/H1/H2/all +0.23/+0.20/+0.10/+0.19; standalone all-in weekly Sharpe 1.16; 218 trades. 10-worker pool.

RX6 K4-lean: PRICE + VIX features only, 5-seed ensemble (single pre-declared cell).


Fill model: 16:16 ET px entry/exit, 1 tick/side + $4.36 per contract RT, 1 ADR-dollar per trade; additive and constant-risk framings below.

| share | framing | clean | H1 | H2 | all | worst wk chg % | boot 90% CI |
|---|---|---|---|---|---|---|---|
| 10% | add | +0.123 | +0.115 | +0.057 | +0.105 | +7.9 | [+0.025, +0.188] |
| 20% | add | +0.228 | +0.203 | +0.096 | +0.190 | +21.0 | [+0.035, +0.352] |
| 30% | add | +0.313 | +0.261 | +0.114 | +0.255 | +34.1 | [+0.029, +0.492] |
| 50% | add | +0.430 | +0.301 | +0.091 | +0.327 | +60.3 | [-0.029, +0.688] |
| 10% | const | +0.136 | +0.127 | +0.063 | +0.116 | -1.5 | [+0.027, +0.208] |
| 20% | const | +0.273 | +0.235 | +0.107 | +0.225 | +2.1 | [+0.036, +0.426] |
| 30% | const | +0.396 | +0.297 | +0.108 | +0.309 | +5.7 | [-0.005, +0.629] |
| 50% | const | +0.508 | +0.127 | -0.185 | +0.292 | +12.9 | [-0.302, +0.909] |

Correlation: worst-decile -0.01, all -0.01. Per-instrument own-scaled 20% uplift: ES +0.164; NQ +0.206; RTY +0.104; YM +0.080

## Gate checklist

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.228 / +0.203 / +0.096
- [FAIL] 3 worst week within share: all-in worst week +21.0% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.16 vs p95 1.00 (rank 0.97)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.035, +0.352]
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.224 / +0.197 / +0.090
- [PASS] 6 worst-decile corr <=+0.30: -0.01
- [PASS] 4 drift-matched (month-stratified) null p95: real 1.16 vs p95 0.60 (rank 1.00)
- [FAIL] 4 beta test alpha CI lower >0: beta +0.108; alpha Sharpe 0.87 CI [-0.03, +1.65]; always-long Sharpe 0.65
- [FAIL] 5 plateau (pre-registered: >= 7 of 8 keep >= 75%): 75% of 8

Plateau neighbours (all-in uplift; selected +0.190): {'var': 'base', 'ss': 'A', 'delta': '0.06', 'N': '1', 'mode': 'longonly'}: +0.434; {'var': 'base', 'ss': 'A', 'delta': '0.1', 'N': '1', 'mode': 'longonly'}: +0.105; {'var': 't112', 'ss': 'A', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.140; {'var': 't188', 'ss': 'A', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.237; {'var': 'l0375', 'ss': 'A', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.182; {'var': 'l0625', 'ss': 'A', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.225; {'var': 'base', 'ss': 'B', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.205; {'var': 'base', 'ss': 'C', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.194

## ERA (walk-forward 2016-22): positive pre-2023; weekly Sharpe gross/fixed/scaled 0.30/0.17/0.22 on 1715 trades

NT8: daily signal file after the 16:15 ET model refresh; seed ensemble = mean of five LightGBM models retrained quarterly offline; market entry 16:16 ET, exit next 16:16 ET. Margin as K4v2 (contracts per signal scale with 1/ADR; see REPORT_K4V2.md).

DONE RX6