# REPORT RU3 - why depth matters on some markets (tick-to-stop ratio and cost table)


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