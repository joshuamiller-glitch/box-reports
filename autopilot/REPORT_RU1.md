# REPORT RU1 - depth-permutation family null, NQ vs GC/CL side by side

Pre-registered in PREREG_AUTOPILOT.md BATCH RU. 1-minute RZ simulator; cells fixed (IMP3 tf3 m1.5 = ICT cell, FVG tf5 m0.25 = ICT P1 definition, FVG tf15 m0.25 = RZ cell); statistic = clean weekly Sharpe in R units (sample 2023-02..2026-10 trades). Null A = ICT permutation (depth below signal close and stop distance permuted jointly across setups, ap_fv_gates.depth_perm_one); null B = entry fraction redrawn U(0.25,0.75) with the original stop (RV1). 200 worlds each. ICT own tick-replay figure for IMP3 (fv/g7_x.pkl): real 4.37 vs best-of-20 null mean 1.93, p95 2.62, max 3.36.

| market | cell | trades | real | null A median / p95 / rank | null B median / p95 / rank | real - null B median | verdict |
|---|---|---|---|---|---|---|---|
| NQ | IMP3_tf3 | 14031 | 3.95 | -0.44 / 0.43 / 1.00 | 3.13 / 3.82 / 0.96 | +0.82 | DEPTH MATTERS |
| NQ | FVG_tf5_P1 | 10855 | 2.98 | -2.05 / -1.11 / 1.00 | 2.96 / 3.43 / 0.53 | +0.02 | DEPTH-FREE |
| NQ | FVG_tf15 | 3881 | 2.32 | -0.87 / 0.21 / 1.00 | 2.36 / 2.76 / 0.43 | -0.05 | DEPTH-FREE |
| GC | IMP3_tf3 | 10022 | 3.83 | 2.31 / 3.14 / 0.99 | 2.99 / 3.67 / 0.97 | +0.84 | DEPTH MATTERS |
| GC | FVG_tf5_P1 | 8635 | 1.81 | 0.15 / 0.93 / 1.00 | 1.88 / 2.29 / 0.38 | -0.07 | DEPTH-FREE |
| GC | FVG_tf15 | 3701 | 2.59 | 0.34 / 1.26 / 1.00 | 2.56 / 2.95 / 0.60 | +0.03 | DEPTH-FREE |
| CL | IMP3_tf3 | 5670 | 0.07 | 0.83 / 1.73 / 0.04 | 0.30 / 0.87 / 0.28 | -0.22 | DEPTH-FREE |
| CL | FVG_tf5_P1 | 5853 | 1.63 | -0.13 / 0.66 / 1.00 | 1.25 / 1.64 / 0.94 | +0.38 | DEPTH-FREE |
| CL | FVG_tf15 | 3463 | 2.27 | -0.07 / 0.81 / 1.00 | 2.17 / 2.69 / 0.62 | +0.10 | DEPTH-FREE |
| ES | IMP3_tf3 | 6136 | 2.50 | 1.31 / 1.98 / 0.99 | 1.75 / 2.30 / 0.99 | +0.75 | DEPTH MATTERS |
| ES | FVG_tf5_P1 | 6028 | 2.22 | -0.08 / 0.57 / 1.00 | 1.64 / 2.12 / 0.97 | +0.58 | DEPTH MATTERS |
| ES | FVG_tf15 | 3348 | 0.93 | 0.16 / 1.13 / 0.90 | 0.79 / 1.23 / 0.71 | +0.14 | DEPTH-FREE |
| RTY | IMP3_tf3 | 8776 | 1.41 | 0.68 / 1.53 / 0.91 | 1.05 / 1.75 / 0.82 | +0.35 | DEPTH-FREE |
| RTY | FVG_tf5_P1 | 7964 | 2.18 | -1.51 / -0.76 / 1.00 | 2.20 / 2.63 / 0.43 | -0.02 | DEPTH-FREE |
| RTY | FVG_tf15 | 3708 | 1.36 | -0.84 / 0.12 / 1.00 | 1.30 / 1.67 / 0.61 | +0.06 | DEPTH-FREE |

Reading: null A is destructive on every market (permuting the stop distance also breaks the stop geometry), so passing it alone does not isolate the 50% level; null B changes only the entry depth. Verdict requires both p95 tests.

## RU3 why depth matters (explanatory)

Clean weekly Sharpe as a function of entry fraction f (0 = far edge of the gap/move, 0.5 = CE, 1 = near edge, shallow), with the market geometry. depth-effect = Sh(0.5) - mean(Sh(0.25), Sh(0.75)).

| market | cell | stop (ticks) | stop (USD/contract) | ATR (ticks) | round-trip cost (R) | Sh f=0 | 0.25 | 0.5 | 0.75 | 1.0 | depth-effect |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E | FVG_tf15 | 30 | 188 | 13 | 0.090 | -0.51 | 0.13 | 0.77 | 1.07 | 0.21 | +0.17 |
| BTC | FVG_tf15 | 45 | 1,123 | 44 | 0.048 | 1.26 | 1.79 | 2.24 | 2.17 | 2.69 | +0.26 |
| CL | FVG_tf15 | 30 | 300 | 17 | 0.081 | 2.06 | 2.86 | 2.27 | 1.38 | 0.66 | +0.15 |
| CL | IMP3_tf3 | 30 | 300 | 11 | 0.081 | 0.29 | 0.40 | 0.07 | 0.70 | -1.64 | -0.48 |
| ES | FVG_tf15 | 30 | 375 | 21 | 0.078 | 0.55 | 0.46 | 0.93 | 1.21 | 1.56 | +0.09 |
| ETH | FVG_tf15 | 43 | 541 | 42 | 0.054 | 0.30 | 1.46 | 2.04 | 3.00 | 1.98 | -0.20 |
| GC | FVG_tf15 | 37 | 367 | 30 | 0.066 | 2.32 | 2.55 | 2.59 | 2.54 | 3.32 | +0.04 |
| GC | IMP3_tf3 | 30 | 300 | 15 | 0.081 | 0.70 | 1.48 | 3.83 | 3.46 | -0.74 | +1.36 |
| NQ | FVG_tf15 | 124 | 621 | 102 | 0.023 | 1.69 | 1.93 | 2.32 | 2.60 | 2.72 | +0.05 |
| NQ | IMP3_tf3 | 53 | 263 | 41 | 0.055 | 1.62 | 2.81 | 3.95 | 2.55 | -0.20 | +1.27 |
| RTY | FVG_tf15 | 34 | 172 | 29 | 0.083 | 0.81 | 1.56 | 1.36 | 1.02 | 0.93 | +0.07 |
| YM | FVG_tf15 | 42 | 211 | 35 | 0.068 | 0.84 | 0.70 | 0.78 | 1.18 | 0.68 | -0.16 |

Spearman (depth-effect vs stop ticks), FVG_tf15, 9 markets: rho -0.33 (p 0.38)

Spearman (depth-effect vs cost in R), FVG_tf15, 9 markets: rho +0.32 (p 0.41)

DONE RU1 RU3