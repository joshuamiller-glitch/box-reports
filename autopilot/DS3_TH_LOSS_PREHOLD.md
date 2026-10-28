# DS3_TH_LOSS_PREHOLD - D3TH E, WF-PRE (2024-02..2025-06) results only; HOLD 2025-07+ and SPAN2 2023-04..2024-01 NOT read
Prereg sha256: books f523fc35..., basket e5201adf... (autopilot/DECISIONS.md). Effects are paired pts per trade, cut minus uncut, + = Trade Health helped.

## books (KB SM PE MV MA DN)
| unit | arm | n | cut share | effect pts | 95% CI | MDE (bootstrap) | ev per cut | cut better | random-trade placebo mean / rank | $/wk |
|--|--|--|--|--|--|--|--|--|--|--|
| KB | TIME_ONLY | 3093 | - | -2.21 (sd 0.52) | - | - | - | - | - | - |
| KB | TH_LIVE | 3093 | 0.61 | -1.41 | [-3.06, +0.09] | 2.20 | -2.31 | 0.67 | -2.21 / 0.93 | -6129 |
| KB | MAE15 | 3093 | 0.78 | -2.84 | [-4.74, -1.01] | 2.70 | -3.62 | 0.59 | -3.16 / 0.76 | -12374 |
| SM | TIME_ONLY | 904 | - | -2.82 (sd 0.89) | - | - | - | - | - | - |
| SM | TH_LIVE | 904 | 0.62 | -2.50 | [-5.36, +0.16] | 4.01 | -4.07 | 0.65 | -2.82 / 0.62 | -3188 |
| SM | MAE15 | 904 | 0.78 | -3.52 | [-6.94, -0.39] | 4.75 | -4.50 | 0.58 | -3.85 / 0.66 | -4480 |
| PE | TIME_ONLY | 3050 | - | -1.17 (sd 0.52) | - | - | - | - | - | - |
| PE | TH_LIVE | 3050 | 0.62 | -1.05 | [-2.66, +0.47] | 2.14 | -1.69 | 0.67 | -1.17 / 0.60 | -4493 |
| PE | MAE15 | 3050 | 0.79 | -1.31 | [-3.10, +0.66] | 2.63 | -1.66 | 0.61 | -1.47 / 0.67 | -5646 |
| MV | TIME_ONLY | 2923 | - | -2.05 (sd 0.55) | - | - | - | - | - | - |
| MV | TH_LIVE | 2923 | 0.61 | -1.98 | [-3.54, -0.40] | 2.21 | -3.23 | 0.66 | -2.05 / 0.57 | -8160 |
| MV | MAE15 | 2923 | 0.80 | -3.49 | [-5.47, -1.45] | 2.85 | -4.38 | 0.59 | -2.88 / 0.12 | -14349 |
| MA | TIME_ONLY | 1094 | - | -2.38 (sd 0.88) | - | - | - | - | - | - |
| MA | TH_LIVE | 1094 | 0.62 | -2.74 | [-5.18, -0.20] | 3.55 | -4.41 | 0.65 | -2.38 / 0.36 | -4223 |
| MA | MAE15 | 1094 | 0.77 | -2.12 | [-5.09, +1.00] | 4.49 | -2.75 | 0.59 | -3.00 / 0.87 | -3274 |
| DN | TIME_ONLY | 1762 | - | -2.13 (sd 0.66) | - | - | - | - | - | - |
| DN | TH_LIVE | 1762 | 0.59 | -1.64 | [-3.55, +0.15] | 2.73 | -2.76 | 0.66 | -2.13 / 0.78 | -4062 |
| DN | MAE15 | 1762 | 0.76 | -1.92 | [-4.20, +0.24] | 3.18 | -2.54 | 0.60 | -3.02 / 0.96 | -4756 |

## dip-buy basket legs (pts per leg, instrument points)
| unit | arm | n | cut share | effect pts | 95% CI | MDE (bootstrap) | ev per cut | cut better | random-trade placebo mean / rank | $/wk |
|--|--|--|--|--|--|--|--|--|--|--|
| NQ | TIME_ONLY | 78 | - | -20.21 (sd 13.92) | - | - | - | - | - | - |
| NQ | TH_LIVE | 78 | 0.82 | -7.26 | [-52.75, +42.33] | 69.27 | -8.85 | 0.42 | -20.21 / 0.83 | -80 |
| NQ | MAE15 | 78 | 0.92 | -22.14 | [-76.17, +30.72] | 75.63 | -23.98 | 0.40 | -23.23 / 0.52 | -243 |
| ES | TIME_ONLY | 80 | - | -1.65 (sd 3.07) | - | - | - | - | - | - |
| ES | TH_LIVE | 80 | 0.80 | -2.26 | [-11.54, +7.09] | 13.53 | -2.82 | 0.42 | -1.65 / 0.40 | -64 |
| ES | MAE15 | 80 | 0.89 | -2.19 | [-12.30, +8.33] | 15.22 | -2.47 | 0.45 | -2.29 / 0.47 | -62 |
| ES | TH_LIVE_LITERAL | 80 | 0.33 | -0.54 | [-7.49, +6.28] | 9.68 | -1.65 | 0.54 | -0.05 / 0.42 | -15 |
| RTY | TIME_ONLY | 80 | - | -1.18 (sd 1.44) | - | - | - | - | - | - |
| RTY | TH_LIVE | 80 | 0.78 | -0.46 | [-5.40, +4.64] | 7.24 | -0.60 | 0.44 | -1.18 / 0.68 | -13 |
| RTY | MAE15 | 80 | 0.93 | -1.01 | [-6.43, +4.71] | 7.98 | -1.09 | 0.39 | -1.52 / 0.69 | -28 |
| RTY | TH_LIVE_LITERAL | 80 | 0.06 | +0.26 | [-1.56, +1.91] | 2.42 | +4.24 | 0.80 | -0.07 / 0.71 | +7 |

Note: realised cut share is ~0.6 (books) vs the 0.25 assumed in the prereg MDE; the bootstrap MDE above is the one used in the verdict text. PLC_TIME (uniform random exit time on TH's own cut trades) is informational only: it can exit before the adverse excursion that selected the trade and is look-ahead-favourable; it is not a gate.
