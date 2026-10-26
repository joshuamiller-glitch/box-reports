# PRED ROUND 89 - block E round 6 - S6-S10 per-signal cross-asset (unlocked)

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.577 [0.51,0.65]
Gap to FOUND: 0.103 AUC, 5 of 5 economic conditions short.
not found - short by 0.103 AUC and 5 of 5 economic conditions

prereg d5c8cb55d2ddf4f49269d5143a9371d43a099f7bff6eeebbaf30a8e193e0bb4b ; trials added 1200 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/E5_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E-S6-S10-T_s7-NEVER | sig | POOLED | stack | 0.554 [0.50,0.61] | 0.577 [0.51,0.65] | - | - | - | - | - | - | - | - |  | promising: short by 0.103 AUC, 5 of 5 econ |
| E-S6-S10-Tall-NEVER | sig | POOLED | gbt3 | 0.566 [0.52,0.61] | 0.574 [0.52,0.63] | - | - | - | - | - | - | - | - |  | promising: short by 0.106 AUC, 5 of 5 econ |
| E-S6-S10-T_s6-NEVER | sig | POOLED | stack | 0.570 [0.50,0.63] | 0.569 [0.49,0.64] | - | - | - | - | - | - | - | - |  | short by 0.111 AUC, 5 of 5 econ |
| E-S6-S10-T_s9-NEVER | sig | POOLED | stack | 0.561 [0.51,0.61] | 0.561 [0.50,0.62] | - | - | - | - | - | - | - | - |  | short by 0.119 AUC, 5 of 5 econ |
| E-S6-S10-Tbase | sig | NY/ST | gbt3 | 0.548 [0.53,0.57] | 0.559 [0.53,0.58] | - | - | - | - | - | - | - | - | stack | short by 0.121 AUC, 5 of 5 econ |
| E-S6-S10-Tbase | sig | NY/HM | gbt3 | 0.559 [0.53,0.58] | 0.558 [0.53,0.59] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| E-S6-S10-base | sig | NY/HM | gbt3 | 0.560 [0.54,0.59] | 0.553 [0.52,0.59] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| E-S6-S10-Tbase | sig | NY | logit2 | 0.547 [0.53,0.56] | 0.550 [0.53,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-base | sig | NY/ST | logit2 | 0.540 [0.52,0.56] | 0.549 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-base | sig | NY | logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s7 | sig | POOLED | rf | 0.519 [0.49,0.54] | 0.536 [0.51,0.57] | - | - | - | - | - | - | - | - |  | promising: short by 0.144 AUC, 5 of 5 econ |
| E-S6-S10-T_s7 | sig | ASIA | rf | 0.519 [0.49,0.54] | 0.536 [0.51,0.57] | - | - | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| E-S6-S10-Tbase-NEVER | sig | POOLED/HM | gbt3 | 0.539 [0.52,0.56] | 0.535 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| E-S6-S10-Tall | sig | LONDON/ST | logit2 | 0.544 [0.52,0.57] | 0.535 [0.50,0.57] | - | - | - | - | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| E-S6-S10-Tbase-TAKEN | sig | POOLED/ST | gbt3 | 0.521 [0.50,0.54] | 0.534 [0.50,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s7 | sig | ASIA | logit2 | 0.515 [0.49,0.54] | 0.534 [0.51,0.56] | - | - | - | - | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| E-S6-S10-Tall | sig | NY | rf | 0.531 [0.51,0.55] | 0.533 [0.50,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | LONDON/ST | logit2 | 0.542 [0.52,0.57] | 0.532 [0.50,0.57] | - | - | - | - | - | - | - | - |  | short by 0.148 AUC, 5 of 5 econ |
| E-S6-S10-Tall | sig | NY/ST | rf | 0.524 [0.50,0.55] | 0.532 [0.50,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base-TAKEN | sig | POOLED/ST | gbt3 | 0.520 [0.50,0.54] | 0.531 [0.50,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-base-NEVER | sig | POOLED/HM | gbt3 | 0.535 [0.52,0.56] | 0.530 [0.50,0.56] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| E-S6-S10-T_s7-NEVER | sig | POOLED | stack | 0.534 [0.48,0.58] | 0.530 [0.47,0.59] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase-NEVER | sig | POOLED | logit2 | 0.528 [0.51,0.54] | 0.529 [0.51,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s8 | sig | NY | gbt3 | 0.518 [0.50,0.53] | 0.529 [0.51,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6-NEVER | sig | POOLED | rf | 0.539 [0.48,0.59] | 0.529 [0.45,0.59] | - | - | - | - | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| E-S6-S10-T | sig | NY | stack | 0.525 [0.51,0.54] | 0.528 [0.50,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | POOLED/ST | logit2 | 0.523 [0.51,0.54] | 0.527 [0.51,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tall-TAKEN | sig | POOLED/ST | logit2 | 0.511 [0.49,0.53] | 0.527 [0.50,0.55] | - | - | - | - | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| E-S6-S10-T_s7-TAKEN | sig | POOLED | logit2 | 0.521 [0.49,0.55] | 0.527 [0.49,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | ASIA/ST | stack | 0.517 [0.49,0.55] | 0.527 [0.49,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s9-TAKEN | sig | POOLED | rf | 0.529 [0.50,0.56] | 0.527 [0.49,0.56] | - | - | - | - | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| E-S6-S10-base | sig | POOLED/ST | logit2 | 0.522 [0.51,0.53] | 0.526 [0.51,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s10-TAKEN | sig | POOLED | gbt3 | 0.523 [0.50,0.55] | 0.526 [0.49,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8-TAKEN | sig | POOLED | stack | 0.514 [0.50,0.53] | 0.525 [0.50,0.55] | - | - | - | - | - | - | - | - |  | short by 0.155 AUC, 5 of 5 econ |
| E-S6-S10-base-NEVER | sig | POOLED/ST | logit2 | 0.525 [0.51,0.54] | 0.525 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T-NEVER | sig | POOLED | rf | 0.521 [0.51,0.54] | 0.525 [0.51,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | NY/HM | stack | 0.524 [0.50,0.55] | 0.524 [0.49,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | LONDON/ST | stack | 0.516 [0.49,0.55] | 0.524 [0.49,0.56] | - | - | - | - | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| E-S6-S10-Tbase | sig | NY/HM | gbt3 | 0.509 [0.48,0.53] | 0.524 [0.49,0.56] | - | - | - | - | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| E-S6-S10-Tall-TAKEN | sig | POOLED/ST | stack | 0.513 [0.49,0.54] | 0.523 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10 | sig | ASIA | rf | 0.517 [0.49,0.55] | 0.523 [0.48,0.56] | - | - | - | - | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| E-S6-S10-Tbase-NEVER | sig | POOLED/ST | logit2 | 0.525 [0.51,0.54] | 0.523 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-base | sig | NY/HM | logit2 | 0.513 [0.49,0.54] | 0.523 [0.49,0.56] | - | - | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| E-S6-S10-T_s9 | sig | ASIA | rf | 0.531 [0.51,0.55] | 0.523 [0.49,0.55] | - | - | - | - | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| E-S6-S10-T_s9 | sig | POOLED | rf | 0.531 [0.51,0.55] | 0.523 [0.49,0.55] | - | - | - | - | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| E-S6-S10-T_s8 | sig | ASIA | logit2 | 0.512 [0.49,0.54] | 0.523 [0.49,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10 | sig | ASIA | gbt3 | 0.508 [0.48,0.54] | 0.521 [0.48,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s9 | sig | POOLED | rf | 0.528 [0.50,0.55] | 0.520 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s9 | sig | ASIA | rf | 0.528 [0.50,0.55] | 0.520 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-TAKEN | sig | POOLED/ST | logit2 | 0.513 [0.49,0.54] | 0.520 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx-NEVER | sig | POOLED | rf | 0.533 [0.48,0.58] | 0.520 [0.46,0.58] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| E-S6-S10-Tall-NEVER | sig | POOLED/HM | rf | 0.526 [0.51,0.55] | 0.520 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s7-TAKEN | sig | POOLED | logit2 | 0.511 [0.48,0.54] | 0.520 [0.49,0.55] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| E-S6-S10-T_s7 | sig | POOLED | logit2 | 0.517 [0.49,0.54] | 0.520 [0.48,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s7 | sig | ASIA | logit2 | 0.517 [0.49,0.54] | 0.520 [0.48,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | NY/ST | stack | 0.527 [0.51,0.54] | 0.520 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | POOLED/ST | logit2 | 0.516 [0.50,0.53] | 0.520 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| E-S6-S10-Tall | sig | NY/ST | logit2 | 0.512 [0.49,0.53] | 0.520 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| E-S6-S10-Tall | sig | ASIA/HM | stack | 0.521 [0.49,0.55] | 0.520 [0.48,0.56] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| E-S6-S10-ctx | sig | ASIA/ST | logit2 | 0.505 [0.48,0.54] | 0.519 [0.49,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall-NEVER | sig | POOLED | rf | 0.532 [0.52,0.55] | 0.519 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s9-TAKEN | sig | POOLED | rf | 0.524 [0.50,0.55] | 0.519 [0.48,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | ASIA | gbt3 | 0.510 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| E-S6-S10-ctx | sig | ASIA | logit2 | 0.511 [0.49,0.54] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | POOLED | logit2 | 0.519 [0.51,0.53] | 0.518 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T-NEVER | sig | POOLED/HM | rf | 0.520 [0.50,0.54] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | NY/ST | rf | 0.516 [0.50,0.54] | 0.518 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| E-S6-S10-base | sig | LONDON | logit2 | 0.513 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| E-S6-S10-T_s10 | sig | POOLED | gbt3 | 0.517 [0.50,0.54] | 0.517 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10 | sig | ASIA | gbt3 | 0.517 [0.50,0.54] | 0.517 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8-NEVER | sig | POOLED | logit2 | 0.535 [0.48,0.58] | 0.517 [0.45,0.58] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base-NEVER | sig | POOLED | logit2 | 0.519 [0.51,0.53] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| E-S6-S10-Tall | sig | POOLED | rf | 0.523 [0.51,0.54] | 0.517 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | ASIA/ST | stack | 0.526 [0.50,0.55] | 0.517 [0.48,0.55] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| E-S6-S10-Tbase-TAKEN | sig | POOLED/ST | rf | 0.498 [0.48,0.52] | 0.516 [0.49,0.55] | - | - | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| E-S6-S10-Tall | sig | ASIA | logit2 | 0.515 [0.49,0.54] | 0.516 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | POOLED | logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | POOLED/HM | rf | 0.508 [0.49,0.52] | 0.516 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| E-S6-S10-base | sig | NY | logit2 | 0.521 [0.50,0.54] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| E-S6-S10-Tall-TAKEN | sig | POOLED | gbt3 | 0.515 [0.50,0.53] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase-NEVER | sig | POOLED | logit2 | 0.514 [0.50,0.53] | 0.516 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| E-S6-S10-ctx-TAKEN | sig | POOLED | logit2 | 0.508 [0.48,0.53] | 0.516 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8 | sig | ASIA | logit2 | 0.517 [0.49,0.54] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8 | sig | POOLED | logit2 | 0.517 [0.49,0.54] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall-NEVER | sig | POOLED/ST | logit2 | 0.518 [0.50,0.53] | 0.515 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| E-S6-S10-T-TAKEN | sig | POOLED | rf | 0.518 [0.49,0.54] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | LONDON | logit2 | 0.514 [0.49,0.54] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| E-S6-S10-T_s8-TAKEN | sig | POOLED | logit2 | 0.513 [0.49,0.54] | 0.514 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | NY | logit2 | 0.513 [0.49,0.53] | 0.514 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| E-S6-S10-ctx | sig | LONDON/ST | rf | 0.521 [0.49,0.55] | 0.514 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| E-S6-S10-Tall | sig | POOLED/ST | rf | 0.520 [0.50,0.53] | 0.514 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6 | sig | ASIA | logit2 | 0.515 [0.49,0.54] | 0.514 [0.48,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-Tall-NEVER | sig | POOLED/ST | gbt3 | 0.531 [0.51,0.55] | 0.514 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | POOLED/HM | gbt3 | 0.520 [0.51,0.53] | 0.514 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | LONDON | stack | 0.512 [0.49,0.53] | 0.514 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| E-S6-S10-T_s9 | sig | NY | gbt3 | 0.517 [0.50,0.53] | 0.514 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10 | sig | NY | gbt3 | 0.518 [0.50,0.54] | 0.513 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | POOLED/ST | stack | 0.520 [0.51,0.53] | 0.513 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s9-TAKEN | sig | POOLED | gbt3 | 0.505 [0.49,0.52] | 0.513 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | LONDON/HM | rf | 0.521 [0.49,0.55] | 0.513 [0.47,0.56] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| E-S6-S10-T | sig | NY/HM | rf | 0.514 [0.49,0.53] | 0.513 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | ASIA | logit2 | 0.517 [0.50,0.54] | 0.513 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | POOLED | logit2 | 0.517 [0.50,0.54] | 0.513 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base-NEVER | sig | POOLED | gbt3 | 0.520 [0.51,0.53] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | NY/ST | rf | 0.505 [0.48,0.52] | 0.512 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| E-S6-S10-ctx | sig | POOLED/ST | stack | 0.512 [0.50,0.52] | 0.512 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall-NEVER | sig | POOLED | logit2 | 0.515 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| E-S6-S10-T_s10-TAKEN | sig | POOLED | rf | 0.510 [0.49,0.53] | 0.512 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| E-S6-S10-base-NEVER | sig | POOLED/HM | stack | 0.511 [0.49,0.53] | 0.512 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| E-S6-S10-T_s9-TAKEN | sig | POOLED | stack | 0.509 [0.49,0.53] | 0.512 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| E-S6-S10-T_s7 | sig | ASIA | logit2 | 0.509 [0.49,0.53] | 0.512 [0.48,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-base | sig | POOLED/HM | gbt3 | 0.521 [0.51,0.54] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-base | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| E-S6-S10-ctx | sig | POOLED/ST | rf | 0.511 [0.50,0.52] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| E-S6-S10-ctx-TAKEN | sig | POOLED/ST | rf | 0.524 [0.50,0.54] | 0.511 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| E-S6-S10-T | sig | LONDON/HM | stack | 0.511 [0.48,0.54] | 0.511 [0.47,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | LONDON/HM | rf | 0.518 [0.49,0.55] | 0.511 [0.46,0.56] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| E-S6-S10-ctx | sig | NY/ST | stack | 0.513 [0.49,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8-NEVER | sig | POOLED | logit2 | 0.508 [0.49,0.52] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-TAKEN | sig | POOLED | logit2 | 0.516 [0.49,0.54] | 0.510 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| E-S6-S10-ctx-NEVER | sig | POOLED | stack | 0.505 [0.49,0.52] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8 | sig | POOLED | gbt3 | 0.507 [0.50,0.52] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | NY/HM | gbt3 | 0.509 [0.48,0.53] | 0.510 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| E-S6-S10-base | sig | POOLED/ST | rf | 0.509 [0.49,0.52] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| E-S6-S10-T_s6 | sig | POOLED | logit2 | 0.515 [0.49,0.54] | 0.510 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6 | sig | ASIA | logit2 | 0.515 [0.49,0.54] | 0.510 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | ASIA | logit2 | 0.506 [0.48,0.53] | 0.510 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | POOLED | logit2 | 0.506 [0.48,0.53] | 0.510 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| E-S6-S10-Tall | sig | POOLED/HM | rf | 0.521 [0.51,0.54] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-NEVER | sig | POOLED | logit2 | 0.523 [0.48,0.56] | 0.510 [0.46,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase-NEVER | sig | POOLED | gbt3 | 0.529 [0.48,0.58] | 0.509 [0.45,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | POOLED | logit2 | 0.507 [0.49,0.52] | 0.509 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| E-S6-S10-T | sig | POOLED | gbt3 | 0.513 [0.50,0.53] | 0.509 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | ASIA | gbt3 | 0.504 [0.48,0.53] | 0.509 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx-TAKEN | sig | POOLED/HM | logit2 | 0.515 [0.49,0.54] | 0.509 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6-TAKEN | sig | POOLED | logit2 | 0.516 [0.49,0.54] | 0.509 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | ASIA | stack | 0.509 [0.48,0.53] | 0.509 [0.48,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s10-TAKEN | sig | POOLED | logit2 | 0.508 [0.48,0.53] | 0.509 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| E-S6-S10-ctx | sig | POOLED/HM | rf | 0.509 [0.49,0.53] | 0.509 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s9 | sig | POOLED | gbt3 | 0.512 [0.50,0.52] | 0.508 [0.50,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | ASIA/ST | rf | 0.511 [0.48,0.54] | 0.508 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base-TAKEN | sig | POOLED | rf | 0.510 [0.49,0.53] | 0.508 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s10-TAKEN | sig | POOLED | gbt3 | 0.505 [0.49,0.52] | 0.508 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx-TAKEN | sig | POOLED/ST | stack | 0.520 [0.50,0.54] | 0.508 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10-NEVER | sig | POOLED | gbt3 | 0.511 [0.50,0.53] | 0.508 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | ASIA/HM | gbt3 | 0.501 [0.47,0.53] | 0.508 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8 | sig | POOLED | stack | 0.508 [0.50,0.52] | 0.508 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| E-S6-S10-T_s10 | sig | POOLED | gbt3 | 0.508 [0.50,0.52] | 0.507 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | ASIA | logit2 | 0.515 [0.49,0.54] | 0.507 [0.48,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-T | sig | POOLED | logit2 | 0.515 [0.49,0.54] | 0.507 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| E-S6-S10-Tall | sig | POOLED | logit2 | 0.511 [0.49,0.53] | 0.507 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | ASIA | logit2 | 0.511 [0.49,0.53] | 0.507 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s9-NEVER | sig | POOLED | gbt3 | 0.517 [0.50,0.53] | 0.507 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8-TAKEN | sig | POOLED | gbt3 | 0.508 [0.49,0.53] | 0.507 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | ASIA/ST | gbt3 | 0.500 [0.47,0.53] | 0.507 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s7 | sig | POOLED | gbt3 | 0.504 [0.49,0.52] | 0.506 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10-NEVER | sig | POOLED | stack | 0.527 [0.47,0.59] | 0.506 [0.43,0.59] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-ctx | sig | NY/HM | stack | 0.510 [0.48,0.54] | 0.506 [0.47,0.55] | - | - | - | - | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| E-S6-S10-ctx-NEVER | sig | POOLED/ST | stack | 0.497 [0.48,0.52] | 0.506 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | POOLED/HM | rf | 0.504 [0.49,0.52] | 0.506 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6-TAKEN | sig | POOLED | logit2 | 0.505 [0.48,0.53] | 0.505 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | ASIA/HM | rf | 0.521 [0.49,0.55] | 0.505 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | POOLED | logit2 | 0.511 [0.49,0.54] | 0.505 [0.48,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-ctx | sig | ASIA | logit2 | 0.511 [0.49,0.54] | 0.505 [0.48,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-T_s6-NEVER | sig | POOLED | gbt3 | 0.510 [0.50,0.52] | 0.505 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | ASIA | stack | 0.506 [0.48,0.53] | 0.505 [0.47,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-T_s6 | sig | NY | gbt3 | 0.515 [0.49,0.53] | 0.505 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-NEVER | sig | POOLED | gbt3 | 0.523 [0.47,0.57] | 0.505 [0.44,0.56] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-Tbase-TAKEN | sig | POOLED | rf | 0.508 [0.49,0.53] | 0.504 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | ASIA/HM | logit2 | 0.515 [0.49,0.54] | 0.504 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s9 | sig | ASIA | stack | 0.504 [0.48,0.53] | 0.504 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6 | sig | ASIA | logit2 | 0.506 [0.48,0.53] | 0.504 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6 | sig | POOLED | logit2 | 0.506 [0.48,0.53] | 0.504 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-NEVER | sig | POOLED/ST | stack | 0.519 [0.50,0.53] | 0.504 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall-NEVER | sig | POOLED/HM | rf | 0.513 [0.49,0.54] | 0.504 [0.48,0.53] | - | - | - | - | - | - | - | - |  | short by 0.176 AUC, 5 of 5 econ |
| E-S6-S10-T_s8 | sig | LONDON | gbt3 | 0.499 [0.48,0.52] | 0.504 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | ASIA/ST | stack | 0.510 [0.49,0.54] | 0.504 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | ASIA | logit2 | 0.505 [0.48,0.53] | 0.504 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | POOLED | logit2 | 0.505 [0.48,0.53] | 0.504 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase-TAKEN | sig | POOLED/HM | rf | 0.504 [0.48,0.53] | 0.504 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.176 AUC, 5 of 5 econ |
| E-S6-S10-T_s7 | sig | NY | stack | 0.507 [0.49,0.53] | 0.504 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-TAKEN | sig | POOLED | gbt3 | 0.512 [0.50,0.53] | 0.504 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | ASIA/ST | gbt3 | 0.503 [0.48,0.53] | 0.504 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8 | sig | ASIA | logit2 | 0.507 [0.48,0.53] | 0.504 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-Tbase-NEVER | sig | POOLED/HM | stack | 0.502 [0.48,0.53] | 0.503 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| E-S6-S10-base-TAKEN | sig | POOLED | logit2 | 0.502 [0.48,0.52] | 0.503 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T | sig | ASIA/ST | stack | 0.504 [0.48,0.53] | 0.503 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | ASIA | stack | 0.513 [0.49,0.54] | 0.503 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-base | sig | POOLED | logit2 | 0.501 [0.48,0.52] | 0.503 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-base | sig | ASIA | logit2 | 0.501 [0.48,0.52] | 0.503 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s9 | sig | ASIA | gbt3 | 0.495 [0.47,0.52] | 0.502 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-TAKEN | sig | POOLED/ST | stack | 0.501 [0.48,0.52] | 0.502 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall-TAKEN | sig | POOLED | stack | 0.506 [0.49,0.53] | 0.502 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10-NEVER | sig | POOLED | stack | 0.503 [0.49,0.52] | 0.501 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8 | sig | NY | stack | 0.505 [0.49,0.52] | 0.501 [0.48,0.53] | - | - | - | - | - | - | - | - |  | short by 0.179 AUC, 5 of 5 econ |
| E-S6-S10-Tbase | sig | ASIA | rf | 0.500 [0.48,0.52] | 0.501 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s6 | sig | POOLED | gbt3 | 0.508 [0.50,0.52] | 0.500 [0.49,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx-NEVER | sig | POOLED/HM | stack | 0.497 [0.48,0.52] | 0.500 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | POOLED/HM | stack | 0.503 [0.49,0.52] | 0.500 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s9 | sig | POOLED | stack | 0.502 [0.49,0.51] | 0.500 [0.49,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx-NEVER | sig | POOLED/HM | rf | 0.504 [0.48,0.53] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10 | sig | ASIA | logit2 | 0.502 [0.48,0.52] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10 | sig | POOLED | logit2 | 0.502 [0.48,0.52] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s7-NEVER | sig | POOLED | stack | 0.500 [0.49,0.51] | 0.499 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | LONDON/ST | rf | 0.504 [0.48,0.53] | 0.499 [0.46,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-base-TAKEN | sig | POOLED | logit2 | 0.500 [0.47,0.53] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | NY | logit2 | 0.499 [0.48,0.52] | 0.499 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s7-NEVER | sig | POOLED | rf | 0.503 [0.49,0.52] | 0.498 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx-TAKEN | sig | POOLED | gbt3 | 0.504 [0.48,0.52] | 0.498 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base-TAKEN | sig | POOLED | stack | 0.506 [0.48,0.53] | 0.498 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T | sig | LONDON | gbt3 | 0.499 [0.48,0.52] | 0.498 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall-TAKEN | sig | POOLED | logit2 | 0.499 [0.47,0.52] | 0.498 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase-NEVER | sig | POOLED/ST | gbt3 | 0.509 [0.49,0.53] | 0.498 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s9-NEVER | sig | POOLED | stack | 0.536 [0.48,0.59] | 0.498 [0.43,0.55] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-Tbase | sig | ASIA | stack | 0.501 [0.48,0.52] | 0.497 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s8-NEVER | sig | POOLED | stack | 0.503 [0.49,0.52] | 0.497 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base-NEVER | sig | POOLED | gbt3 | 0.516 [0.47,0.57] | 0.497 [0.44,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tall-TAKEN | sig | POOLED | logit2 | 0.504 [0.48,0.53] | 0.497 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | NY/HM | rf | 0.511 [0.49,0.54] | 0.497 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-NEVER | sig | POOLED/HM | stack | 0.502 [0.48,0.52] | 0.497 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base-NEVER | sig | POOLED/ST | gbt3 | 0.507 [0.49,0.52] | 0.496 [0.48,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s10 | sig | POOLED | rf | 0.499 [0.49,0.51] | 0.496 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | ASIA | stack | 0.504 [0.48,0.53] | 0.496 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | POOLED | stack | 0.504 [0.48,0.53] | 0.496 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | ASIA | gbt3 | 0.501 [0.47,0.53] | 0.496 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | LONDON/ST | logit2 | 0.504 [0.48,0.52] | 0.496 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| E-S6-S10-ctx | sig | POOLED | gbt3 | 0.496 [0.48,0.51] | 0.495 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | POOLED/HM | stack | 0.503 [0.49,0.52] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | POOLED/HM | rf | 0.505 [0.49,0.52] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | LONDON | stack | 0.505 [0.48,0.53] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-T_s7 | sig | POOLED | stack | 0.499 [0.49,0.51] | 0.495 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | ASIA/HM | gbt3 | 0.501 [0.48,0.53] | 0.495 [0.46,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | POOLED/ST | gbt3 | 0.497 [0.48,0.51] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | ASIA/HM | gbt3 | 0.499 [0.47,0.52] | 0.495 [0.46,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s8-TAKEN | sig | POOLED | logit2 | 0.506 [0.48,0.53] | 0.494 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | ASIA | stack | 0.506 [0.48,0.53] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-base | sig | POOLED | stack | 0.506 [0.48,0.53] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tall-TAKEN | sig | POOLED/HM | rf | 0.515 [0.49,0.54] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6 | sig | POOLED | stack | 0.498 [0.49,0.51] | 0.494 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase-TAKEN | sig | POOLED | stack | 0.503 [0.48,0.53] | 0.493 [0.46,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s7-TAKEN | sig | POOLED | gbt3 | 0.504 [0.48,0.52] | 0.493 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6-TAKEN | sig | POOLED | gbt3 | 0.506 [0.49,0.53] | 0.493 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx-NEVER | sig | POOLED | gbt3 | 0.491 [0.48,0.51] | 0.493 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | LONDON/ST | logit2 | 0.500 [0.48,0.52] | 0.493 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| E-S6-S10-ctx | sig | NY | stack | 0.507 [0.49,0.53] | 0.493 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-TAKEN | sig | POOLED/HM | logit2 | 0.494 [0.47,0.52] | 0.493 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s9-NEVER | sig | POOLED | stack | 0.496 [0.48,0.51] | 0.493 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8 | sig | POOLED | logit2 | 0.506 [0.48,0.53] | 0.493 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8 | sig | ASIA | logit2 | 0.506 [0.48,0.53] | 0.493 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | POOLED/ST | stack | 0.495 [0.48,0.51] | 0.492 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | POOLED | stack | 0.498 [0.49,0.51] | 0.492 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | NY/ST | stack | 0.504 [0.48,0.52] | 0.492 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T-TAKEN | sig | POOLED/HM | gbt3 | 0.491 [0.47,0.51] | 0.492 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6 | sig | LONDON | stack | 0.490 [0.47,0.51] | 0.492 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s7-TAKEN | sig | POOLED | stack | 0.497 [0.48,0.51] | 0.491 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | NY | gbt3 | 0.496 [0.48,0.51] | 0.491 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx-TAKEN | sig | POOLED/HM | stack | 0.510 [0.49,0.53] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-base-TAKEN | sig | POOLED/ST | stack | 0.498 [0.48,0.52] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | POOLED | gbt3 | 0.499 [0.49,0.51] | 0.491 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s9 | sig | LONDON | gbt3 | 0.496 [0.47,0.52] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | LONDON/ST | rf | 0.493 [0.47,0.52] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-ctx-NEVER | sig | POOLED/ST | gbt3 | 0.494 [0.48,0.51] | 0.491 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | LONDON | gbt3 | 0.497 [0.47,0.52] | 0.490 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tbase-TAKEN | sig | POOLED | stack | 0.495 [0.48,0.51] | 0.490 [0.47,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | ASIA/HM | logit2 | 0.512 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-T_s9 | sig | NY | stack | 0.502 [0.48,0.52] | 0.489 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | LONDON | rf | 0.520 [0.50,0.55] | 0.489 [0.46,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-base-TAKEN | sig | POOLED/HM | gbt3 | 0.505 [0.48,0.53] | 0.489 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s6 | sig | ASIA | gbt3 | 0.500 [0.48,0.52] | 0.489 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s7 | sig | NY | stack | 0.505 [0.49,0.52] | 0.489 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s9 | sig | LONDON | gbt3 | 0.499 [0.48,0.52] | 0.489 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | ASIA/ST | rf | 0.492 [0.47,0.52] | 0.488 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | ASIA/ST | stack | 0.495 [0.46,0.53] | 0.488 [0.45,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tbase-TAKEN | sig | POOLED/HM | gbt3 | 0.498 [0.48,0.52] | 0.488 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s10-NEVER | sig | POOLED | gbt3 | 0.495 [0.44,0.54] | 0.487 [0.42,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | POOLED | stack | 0.495 [0.48,0.51] | 0.487 [0.47,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | LONDON/HM | stack | 0.481 [0.45,0.51] | 0.487 [0.44,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-NEVER | sig | POOLED/ST | stack | 0.491 [0.47,0.51] | 0.487 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | POOLED/HM | logit2 | 0.490 [0.47,0.51] | 0.487 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx-TAKEN | sig | POOLED | stack | 0.497 [0.47,0.52] | 0.486 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s7 | sig | LONDON | gbt3 | 0.488 [0.47,0.51] | 0.486 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-NEVER | sig | POOLED | stack | 0.497 [0.48,0.51] | 0.486 [0.47,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6-TAKEN | sig | POOLED | gbt3 | 0.501 [0.48,0.52] | 0.486 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | LONDON | rf | 0.492 [0.47,0.51] | 0.486 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T_s10 | sig | NY | rf | 0.495 [0.48,0.51] | 0.485 [0.46,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6-NEVER | sig | POOLED | stack | 0.493 [0.48,0.51] | 0.485 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base | sig | LONDON/ST | gbt3 | 0.495 [0.47,0.52] | 0.484 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T | sig | NY/ST | stack | 0.495 [0.47,0.52] | 0.484 [0.46,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6 | sig | NY | stack | 0.499 [0.48,0.52] | 0.484 [0.46,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | NY | rf | 0.489 [0.47,0.51] | 0.483 [0.46,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | LONDON/HM | logit2 | 0.474 [0.45,0.50] | 0.483 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s7 | sig | LONDON | rf | 0.488 [0.47,0.51] | 0.482 [0.45,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase-NEVER | sig | POOLED | gbt3 | 0.508 [0.45,0.56] | 0.482 [0.42,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | LONDON | rf | 0.505 [0.48,0.53] | 0.482 [0.45,0.51] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-Tall-TAKEN | sig | POOLED/HM | rf | 0.494 [0.47,0.52] | 0.481 [0.45,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10 | sig | LONDON | logit2 | 0.484 [0.46,0.51] | 0.480 [0.45,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s6 | sig | LONDON | logit2 | 0.488 [0.46,0.51] | 0.480 [0.45,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall-NEVER | sig | POOLED | stack | 0.500 [0.45,0.56] | 0.479 [0.41,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T | sig | NY/HM | logit2 | 0.491 [0.47,0.51] | 0.478 [0.44,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-base-NEVER | sig | POOLED | gbt3 | 0.506 [0.46,0.55] | 0.478 [0.42,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T | sig | ASIA/HM | logit2 | 0.490 [0.45,0.53] | 0.477 [0.43,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-base-TAKEN | sig | POOLED/HM | gbt3 | 0.492 [0.47,0.51] | 0.476 [0.44,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-T | sig | LONDON/ST | logit2 | 0.503 [0.48,0.53] | 0.475 [0.44,0.51] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-Tbase | sig | ASIA/HM | stack | 0.495 [0.47,0.53] | 0.474 [0.45,0.50] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| E-S6-S10-ctx | sig | LONDON/HM | stack | 0.485 [0.46,0.52] | 0.473 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T-TAKEN | sig | POOLED | gbt3 | 0.489 [0.47,0.51] | 0.471 [0.45,0.49] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8 | sig | LONDON | gbt3 | 0.482 [0.46,0.51] | 0.471 [0.44,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-ctx-TAKEN | sig | POOLED | gbt3 | 0.501 [0.48,0.52] | 0.471 [0.45,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s10 | sig | LONDON | gbt3 | 0.484 [0.46,0.51] | 0.469 [0.44,0.49] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | POOLED | stack | 0.485 [0.46,0.51] | 0.469 [0.44,0.49] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | ASIA | stack | 0.485 [0.46,0.51] | 0.469 [0.44,0.49] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tbase | sig | LONDON/HM | logit2 | 0.485 [0.46,0.51] | 0.468 [0.43,0.50] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | LONDON/HM | rf | 0.505 [0.47,0.54] | 0.467 [0.43,0.51] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| E-S6-S10-base | sig | LONDON/HM | logit2 | 0.493 [0.46,0.52] | 0.466 [0.43,0.50] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-base | sig | ASIA/HM | stack | 0.492 [0.46,0.52] | 0.464 [0.43,0.50] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| E-S6-S10-ctx-NEVER | sig | POOLED | logit2 | 0.496 [0.44,0.55] | 0.462 [0.40,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tbase-TAKEN | sig | POOLED | stack | 0.479 [0.46,0.50] | 0.460 [0.43,0.49] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| E-S6-S10-ctx | sig | LONDON | gbt3 | 0.472 [0.45,0.50] | 0.455 [0.43,0.48] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-Tall | sig | LONDON/HM | rf | 0.498 [0.47,0.53] | 0.454 [0.41,0.49] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| E-S6-S10-T_s8-NEVER | sig | POOLED | stack | 0.462 [0.42,0.51] | 0.409 [0.35,0.47] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |

One-sentence notes:
- E-S6-S10-T_s9-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-Tbase-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-T_s9-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-base-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-T_s8-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-ctx-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-base -1 NY: scope=HM
- E-S6-S10-base-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-T_s6-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-ctx-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-T-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-Tbase -1 NY: scope=HM
- E-S6-S10-T_s10-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-T_s6-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-T_s7-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-Tbase-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-Tall -1 LONDON: scope=ST
- E-S6-S10-Tall -1 LONDON: scope=ST
- E-S6-S10-Tall-NEVER -1 POOLED: scope=ST
- E-S6-S10-Tall-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-T-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-Tall -1 LONDON: scope=HM
- E-S6-S10-Tall -1 LONDON: scope=HM
- E-S6-S10-base -1 NY: scope=pooled
- E-S6-S10-Tbase -1 NY: scope=pooled
- E-S6-S10-Tall -1 LONDON: scope=pooled
- E-S6-S10-T-NEVER -1 POOLED: scope=ST
- E-S6-S10-Tall-NEVER -1 POOLED: scope=pooled
- E-S6-S10-Tall-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-Tbase-NEVER -1 POOLED: scope=HM
- E-S6-S10-T_s8-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-T_s9 -1 ASIA: scope=ASIA
- E-S6-S10-T_s9 -1 POOLED: scope=ASIA
- E-S6-S10-base -1 ASIA: scope=ST
- E-S6-S10-base-NEVER -1 POOLED: scope=HM
- E-S6-S10-ctx-TAKEN -1 POOLED: scope=ST
- E-S6-S10-T_s9 -1 POOLED: scope=ASIA
- E-S6-S10-T_s9 -1 ASIA: scope=ASIA
- E-S6-S10-Tbase -1 NY: scope=ST
- E-S6-S10-ctx -1 ASIA: scope=HM
- E-S6-S10-Tall -1 ASIA: scope=HM
- E-S6-S10-Tall-NEVER -1 POOLED: scope=HM
- E-S6-S10-T_s9-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-T_s9-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-Tbase -1 LONDON: scope=HM
- E-S6-S10-Tall -1 POOLED: scope=HM
- E-S6-S10-Tall-TAKEN -1 POOLED: scope=HM
- E-S6-S10-base-NEVER -1 POOLED: scope=pooled
- E-S6-S10-base -1 NY: scope=ST
- E-S6-S10-T -1 NY: scope=ST
- E-S6-S10-base -1 POOLED: scope=HM
- E-S6-S10-Tbase-NEVER -1 POOLED: scope=ST
- E-S6-S10-Tbase-NEVER -1 POOLED: scope=pooled
- E-S6-S10-T_s9-NEVER -1 POOLED: scope=pooled
- E-S6-S10-base -1 LONDON: scope=HM
- E-S6-S10-Tall -1 POOLED: scope=pooled
- E-S6-S10-T -1 LONDON: scope=ST
- E-S6-S10-Tall -1 ASIA: scope=pooled
- E-S6-S10-Tall -1 LONDON: scope=pooled
- E-S6-S10-ctx -1 LONDON: scope=ST
- E-S6-S10-Tall -1 NY: scope=pooled
- E-S6-S10-base-NEVER -1 POOLED: scope=ST
- E-S6-S10-T -1 POOLED: scope=ST
- E-S6-S10-base -1 NY: scope=pooled
- E-S6-S10-ctx -1 ASIA: scope=HM
- E-S6-S10-Tall -1 POOLED: scope=ST
- E-S6-S10-T_s6 -1 NY: scope=pooled
- E-S6-S10-Tbase -1 POOLED: scope=HM
- E-S6-S10-ctx -1 NY: scope=HM
- E-S6-S10-T_s6-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-T-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-ctx-TAKEN -1 POOLED: scope=ST
- E-S6-S10-T_s10 -1 NY: scope=pooled
- E-S6-S10-T -1 ASIA: scope=ASIA
- E-S6-S10-T -1 POOLED: scope=ASIA
- E-S6-S10-Tall-NEVER -1 POOLED: scope=HM
- E-S6-S10-Tall-NEVER -1 POOLED: scope=ST
- E-S6-S10-ctx-TAKEN -1 POOLED: scope=HM
- E-S6-S10-T -1 ASIA: scope=ASIA
- E-S6-S10-T -1 POOLED: scope=ASIA
- E-S6-S10-T-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-Tbase-NEVER -1 POOLED: scope=ST
- E-S6-S10-T_s6-NEVER -1 POOLED: scope=pooled
- E-S6-S10-T -1 NY: scope=pooled
- E-S6-S10-base-NEVER -1 POOLED: scope=pooled
- E-S6-S10-base -1 POOLED: scope=pooled
- E-S6-S10-Tbase -1 POOLED: scope=pooled
- E-S6-S10-T_s6 -1 POOLED: scope=ASIA
- E-S6-S10-T_s6 -1 ASIA: scope=ASIA
- E-S6-S10-T-NEVER -1 POOLED: scope=HM
- E-S6-S10-Tall -1 NY: scope=HM
- E-S6-S10-T_s7 -1 NY: scope=pooled
- E-S6-S10-base-NEVER -1 POOLED: scope=ST
- E-S6-S10-T_s9 -1 NY: scope=pooled
- E-S6-S10-T_s8 -1 POOLED: scope=ASIA
- E-S6-S10-T_s8 -1 ASIA: scope=ASIA
- E-S6-S10-T_s8 -1 ASIA: scope=ASIA
- E-S6-S10-T_s8 -1 POOLED: scope=ASIA
- E-S6-S10-T-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-ctx -1 NY: scope=pooled
- E-S6-S10-ctx-TAKEN -1 POOLED: scope=HM
- E-S6-S10-Tbase -1 POOLED: scope=ST
- E-S6-S10-base-TAKEN -1 POOLED: scope=HM
- E-S6-S10-T_s10-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-Tall -1 NY: scope=ST
- E-S6-S10-base -1 ASIA: scope=ASIA
- E-S6-S10-base -1 POOLED: scope=ASIA
- E-S6-S10-T_s10-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-T -1 POOLED: scope=pooled
- E-S6-S10-ctx -1 LONDON: scope=ST
- E-S6-S10-T_s8-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-T -1 ASIA: scope=ST
- E-S6-S10-base -1 POOLED: scope=ST
- E-S6-S10-ctx-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-Tall -1 POOLED: scope=ASIA
- E-S6-S10-Tall -1 ASIA: scope=ASIA
- E-S6-S10-T -1 LONDON: scope=HM
- E-S6-S10-T_s10-NEVER -1 POOLED: scope=pooled
- E-S6-S10-T_s6 -1 POOLED: scope=pooled
- E-S6-S10-T_s10 -1 POOLED: scope=ASIA
- E-S6-S10-T_s10 -1 ASIA: scope=ASIA
- E-S6-S10-T -1 LONDON: scope=pooled
- E-S6-S10-T-NEVER -1 POOLED: scope=pooled
- E-S6-S10-T_s9 -1 POOLED: scope=pooled
- E-S6-S10-ctx -1 POOLED: scope=ASIA
- E-S6-S10-ctx -1 ASIA: scope=ASIA
- E-S6-S10-Tbase -1 ASIA: scope=HM
- E-S6-S10-base -1 LONDON: scope=HM
- E-S6-S10-Tall-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-Tall-NEVER -1 POOLED: scope=pooled
- E-S6-S10-ctx -1 ASIA: scope=ST
- E-S6-S10-T_s6-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-base -1 ASIA: scope=HM
- E-S6-S10-Tbase -1 NY: scope=pooled
- E-S6-S10-Tall-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-T -1 NY: scope=HM
- E-S6-S10-Tbase-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-T_s6 -1 NY: scope=pooled
- E-S6-S10-base -1 ASIA: scope=HM
- E-S6-S10-T_s7-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-base-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-ctx-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-Tbase-NEVER -1 POOLED: scope=pooled
- E-S6-S10-T_s8-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-Tbase -1 NY: scope=ST
- E-S6-S10-T_s8 -1 ASIA: scope=pooled
- E-S6-S10-Tbase -1 ASIA: scope=ASIA
- E-S6-S10-Tbase -1 POOLED: scope=ASIA
- E-S6-S10-base -1 POOLED: scope=pooled
- E-S6-S10-ctx -1 ASIA: scope=pooled
- E-S6-S10-ctx -1 LONDON: scope=pooled
- E-S6-S10-T_s6 -1 ASIA: scope=pooled
- E-S6-S10-T_s9 -1 NY: scope=pooled
- E-S6-S10-base -1 NY: scope=ST
- E-S6-S10-Tall -1 POOLED: scope=HM
- E-S6-S10-Tall -1 POOLED: scope=ST
- E-S6-S10-T_s6-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-Tbase-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-Tall -1 ASIA: scope=pooled
- E-S6-S10-T_s7 -1 POOLED: scope=ASIA
- E-S6-S10-T_s7 -1 ASIA: scope=ASIA
- E-S6-S10-T_s7-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-Tall-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-base-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-Tbase -1 ASIA: scope=HM
- E-S6-S10-T_s7-NEVER -1 POOLED: scope=ASIA
- E-S6-S10-ctx-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-Tall -1 NY: scope=HM
- E-S6-S10-ctx -1 POOLED: scope=ST
- E-S6-S10-T_s8 -1 NY: scope=pooled
- E-S6-S10-T-NEVER -1 POOLED: scope=pooled
- E-S6-S10-Tbase -1 LONDON: scope=pooled
- E-S6-S10-T -1 NY: scope=ST
- E-S6-S10-T_s8-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-T-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-T -1 LONDON: scope=ST
- E-S6-S10-T_s7 -1 NY: scope=pooled
- E-S6-S10-T_s7-NEVER -1 POOLED: scope=pooled
- E-S6-S10-ctx-NEVER -1 POOLED: scope=HM
- E-S6-S10-ctx -1 POOLED: scope=HM
- E-S6-S10-Tall -1 ASIA: scope=HM
- E-S6-S10-ctx -1 NY: scope=HM
- E-S6-S10-base-TAKEN -1 POOLED: scope=HM
- E-S6-S10-T_s8-NEVER -1 POOLED: scope=pooled
- E-S6-S10-T_s10 -1 POOLED: scope=pooled
- E-S6-S10-T_s10 -1 NY: scope=pooled
- E-S6-S10-T_s6 -1 ASIA: scope=ASIA
- E-S6-S10-T_s6 -1 POOLED: scope=ASIA
- E-S6-S10-Tbase-TAKEN -1 POOLED: scope=ST
- E-S6-S10-Tbase-TAKEN -1 POOLED: scope=HM
- E-S6-S10-base -1 POOLED: scope=ST
- E-S6-S10-ctx -1 POOLED: scope=ST
- E-S6-S10-T_s8 -1 NY: scope=pooled
- E-S6-S10-T -1 ASIA: scope=pooled
- E-S6-S10-T_s10-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-T-NEVER -1 POOLED: scope=HM
- E-S6-S10-Tbase -1 LONDON: scope=ST
- E-S6-S10-T -1 LONDON: scope=pooled
- E-S6-S10-Tall -1 NY: scope=ST
- E-S6-S10-base -1 LONDON: scope=ST
- E-S6-S10-T-TAKEN -1 POOLED: scope=ST
- E-S6-S10-base -1 LONDON: scope=ST
- E-S6-S10-T_s8-NEVER -1 POOLED: scope=pooled
- E-S6-S10-T_s8 -1 POOLED: scope=pooled
- E-S6-S10-T_s9-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-ctx -1 ASIA: scope=ASIA
- E-S6-S10-ctx -1 POOLED: scope=ASIA
- E-S6-S10-ctx -1 POOLED: scope=pooled
- E-S6-S10-base-NEVER -1 POOLED: scope=HM
- E-S6-S10-T_s9 -1 LONDON: scope=pooled
- E-S6-S10-base-TAKEN -1 POOLED: scope=ST
- E-S6-S10-T_s6 -1 ASIA: scope=pooled
- E-S6-S10-base -1 ASIA: scope=pooled
- E-S6-S10-T_s8 -1 POOLED: scope=pooled
- E-S6-S10-T_s7 -1 ASIA: scope=pooled
- E-S6-S10-T_s10-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-base -1 POOLED: scope=HM
- E-S6-S10-base -1 LONDON: scope=pooled
- E-S6-S10-T -1 ASIA: scope=HM
- E-S6-S10-ctx-NEVER -1 POOLED: scope=pooled
- E-S6-S10-ctx -1 POOLED: scope=HM
- E-S6-S10-T -1 POOLED: scope=pooled
- E-S6-S10-Tbase -1 POOLED: scope=pooled
- E-S6-S10-T_s6-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-T_s6-NEVER -1 POOLED: scope=pooled
- E-S6-S10-T -1 ASIA: scope=ST
- E-S6-S10-T_s9 -1 ASIA: scope=pooled
- E-S6-S10-Tall -1 ASIA: scope=ST
- E-S6-S10-T_s10 -1 ASIA: scope=ASIA
- E-S6-S10-T_s10 -1 POOLED: scope=ASIA
- E-S6-S10-Tall -1 POOLED: scope=pooled
- E-S6-S10-Tall -1 ASIA: scope=ASIA
- E-S6-S10-Tall -1 POOLED: scope=ASIA
- E-S6-S10-Tbase -1 POOLED: scope=ASIA
- E-S6-S10-Tbase -1 ASIA: scope=ASIA
- E-S6-S10-Tbase-TAKEN -1 POOLED: scope=HM
- E-S6-S10-T -1 NY: scope=HM
- E-S6-S10-T_s8-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-base -1 ASIA: scope=pooled
- E-S6-S10-ctx -1 NY: scope=ST
- E-S6-S10-T_s9 -1 POOLED: scope=pooled
- E-S6-S10-T_s7 -1 POOLED: scope=pooled
- E-S6-S10-ctx -1 ASIA: scope=pooled
- E-S6-S10-T_s7-NEVER -1 POOLED: scope=pooled
- E-S6-S10-T_s10 -1 ASIA: scope=pooled
- E-S6-S10-T_s6 -1 POOLED: scope=pooled
- E-S6-S10-T_s10-NEVER -1 POOLED: scope=pooled
- E-S6-S10-Tall-TAKEN -1 POOLED: scope=HM
- E-S6-S10-base -1 NY: scope=HM
- E-S6-S10-T_s7 -1 POOLED: scope=pooled
- E-S6-S10-T -1 NY: scope=pooled
- E-S6-S10-T_s10 -1 POOLED: scope=pooled
- E-S6-S10-T -1 POOLED: scope=HM
- E-S6-S10-Tall-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-Tbase -1 ASIA: scope=pooled
- E-S6-S10-T-TAKEN -1 POOLED: scope=ST
- E-S6-S10-base-TAKEN -1 POOLED: scope=ST
- E-S6-S10-Tbase -1 ASIA: scope=ST
- E-S6-S10-Tbase -1 POOLED: scope=HM
- E-S6-S10-Tbase -1 ASIA: scope=pooled
- E-S6-S10-T_s9-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-T_s7-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-T_s7-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-base-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-T -1 ASIA: scope=pooled
- E-S6-S10-Tbase -1 LONDON: scope=HM
- E-S6-S10-Tall-TAKEN -1 POOLED: scope=ST
- E-S6-S10-Tbase -1 POOLED: scope=ST
- E-S6-S10-T_s10-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-base-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-Tbase-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-T_s9-NEVER -1 POOLED: scope=pooled
- E-S6-S10-Tbase-TAKEN -1 POOLED: scope=pooled
- E-S6-S10-T_s9 -1 LONDON: scope=pooled
- E-S6-S10-base -1 LONDON: scope=pooled
- E-S6-S10-T -1 POOLED: scope=ST
- E-S6-S10-ctx-TAKEN -1 POOLED: scope=ASIA
- E-S6-S10-T-NEVER -1 POOLED: scope=ST
- E-S6-S10-base -1 POOLED: scope=ASIA
- E-S6-S10-base -1 ASIA: scope=ASIA
- E-S6-S10-T_s8 -1 ASIA: scope=pooled
- E-S6-S10-ctx -1 POOLED: scope=pooled
- E-S6-S10-Tall -1 ASIA: scope=ST
- E-S6-S10-T -1 ASIA: scope=HM
- E-S6-S10-Tall -1 NY: scope=pooled
- E-S6-S10-T_s8 -1 LONDON: scope=pooled
- E-S6-S10-Tbase-NEVER -1 POOLED: scope=HM
- E-S6-S10-Tall-TAKEN -1 POOLED: scope=ST
- E-S6-S10-ctx-NEVER -1 POOLED: scope=ST
- E-S6-S10-ctx -1 NY: scope=ST
- E-S6-S10-T-TAKEN -1 POOLED: scope=HM
- E-S6-S10-T_s10 -1 LONDON: scope=pooled
- E-S6-S10-T_s7 -1 LONDON: scope=pooled
- E-S6-S10-T_s6 -1 LONDON: scope=pooled
- E-S6-S10-Tbase -1 LONDON: scope=ST
- E-S6-S10-Tbase -1 LONDON: scope=pooled
- E-S6-S10-Tbase -1 NY: scope=HM
- E-S6-S10-T_s7 -1 POOLED: scope=ASIA
- E-S6-S10-T_s7 -1 ASIA: scope=ASIA
- E-S6-S10-T_s8 -1 LONDON: scope=pooled
- E-S6-S10-base -1 ASIA: scope=ST
- E-S6-S10-T -1 POOLED: scope=HM
- E-S6-S10-T_s7 -1 LONDON: scope=pooled
- E-S6-S10-T-TAKEN -1 POOLED: scope=HM
- E-S6-S10-Tbase -1 ASIA: scope=ST
- E-S6-S10-ctx -1 NY: scope=pooled
- E-S6-S10-T_s6 -1 LONDON: scope=pooled
- E-S6-S10-T_s7 -1 ASIA: scope=pooled
- E-S6-S10-T_s9 -1 ASIA: scope=pooled
- E-S6-S10-ctx -1 LONDON: scope=HM
- E-S6-S10-ctx-NEVER -1 POOLED: scope=ST
- E-S6-S10-ctx -1 LONDON: scope=pooled
- E-S6-S10-T_s10 -1 ASIA: scope=pooled
- E-S6-S10-ctx -1 ASIA: scope=ST
- E-S6-S10-T_s10 -1 LONDON: scope=pooled
- E-S6-S10-ctx-NEVER -1 POOLED: scope=HM
- E-S6-S10-ctx-NEVER -1 POOLED: scope=pooled
- E-S6-S10-Tbase-TAKEN -1 POOLED: scope=ST
- E-S6-S10-T -1 LONDON: scope=HM
- E-S6-S10-ctx -1 LONDON: scope=HM
