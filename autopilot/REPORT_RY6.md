# REPORT RY6
**Verdict: LEAD** (8/9 gates; H0 +0.032 FAIL; odd/even months +0.144/+0.197 PASS). Cell {'var': 'base', 'ss': 'C', 'delta': 0.08, 'N': 1, 'mode': 'longonly'}: additive 20% uplift clean/H1/H2/all +0.19/+0.24/+0.20/+0.19; standalone all-in weekly Sharpe 1.41; 234 trades. 10-worker pool.

RY6 fresh pre-registration of RX5 with seeds 10-14 and the standard plateau (>= 75% of 8 neighbours).


Fill model: 16:16 ET px entry/exit, 1 tick/side + $4.36 per contract RT, 1 ADR-dollar per trade; additive and constant-risk framings below.

| share | framing | clean | H1 | H2 | all | worst wk chg % | boot 90% CI |
|---|---|---|---|---|---|---|---|
| 10% | add | +0.106 | +0.129 | +0.105 | +0.105 | +1.4 | [+0.043, +0.172] |
| 20% | add | +0.193 | +0.245 | +0.203 | +0.193 | +3.6 | [+0.074, +0.319] |
| 30% | add | +0.262 | +0.345 | +0.291 | +0.264 | +5.7 | [+0.094, +0.444] |
| 50% | add | +0.351 | +0.500 | +0.439 | +0.357 | +13.7 | [+0.096, +0.634] |
| 10% | const | +0.116 | +0.143 | +0.116 | +0.116 | -8.5 | [+0.047, +0.190] |
| 20% | const | +0.230 | +0.297 | +0.248 | +0.231 | -16.3 | [+0.086, +0.385] |
| 30% | const | +0.326 | +0.452 | +0.391 | +0.331 | -22.4 | [+0.103, +0.574] |
| 50% | const | +0.399 | +0.656 | +0.630 | +0.396 | -33.0 | [-0.065, +0.874] |

Correlation: worst-decile +0.06, all +0.06. Per-instrument own-scaled 20% uplift: ES +0.193; NQ +0.228; RTY +0.106; YM +0.135

## Gate checklist

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.193 / +0.245 / +0.203
- [PASS] 3 worst week within share: all-in worst week +3.6% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 1.41 vs p95 1.09 (rank 0.99)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.074, +0.319]
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.189 / +0.242 / +0.198
- [PASS] 6 worst-decile corr <=+0.30: +0.06
- [PASS] 4 drift-matched (month-stratified) null p95: real 1.41 vs p95 0.74 (rank 1.00)
- [PASS] 4 beta test alpha CI lower >0: beta +0.128; alpha Sharpe 1.20 CI [+0.38, +1.85]; always-long Sharpe 0.65
- [FAIL] 5 plateau (pre-registered: share >= 0.750): 62% of 8

Plateau neighbours (all-in uplift; selected +0.193): {'var': 'base', 'ss': 'C', 'delta': '0.06', 'N': '1', 'mode': 'longonly'}: +0.326; {'var': 'base', 'ss': 'C', 'delta': '0.1', 'N': '1', 'mode': 'longonly'}: +0.114; {'var': 't112', 'ss': 'C', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.135; {'var': 't188', 'ss': 'C', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.235; {'var': 'l0375', 'ss': 'C', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.141; {'var': 'l0625', 'ss': 'C', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.224; {'var': 'base', 'ss': 'A', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.235; {'var': 'base', 'ss': 'B', 'delta': '0.08', 'N': '1', 'mode': 'longonly'}: +0.187

## ERA (walk-forward 2016-22): positive pre-2023; weekly Sharpe gross/fixed/scaled 0.50/0.34/0.40 on 1859 trades

NT8: daily signal file after the 16:15 ET model refresh; seed ensemble = mean of five LightGBM models retrained quarterly offline; market entry 16:16 ET, exit next 16:16 ET. Margin as K4v2 (contracts per signal scale with 1/ADR; see REPORT_K4V2.md).

DONE RY6