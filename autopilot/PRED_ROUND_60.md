# PRED ROUND 60 - block E round 5 - S1-S5 per-signal cross-asset (unlocked)

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.558 [0.53,0.58]
Gap to FOUND: 0.122 AUC, 5 of 5 economic conditions short.
not found - short by 0.122 AUC and 5 of 5 economic conditions

prereg b58c2e11392bd26e400b15cef807cfc1feed3f14fa4c6bc672beffa9c181b6ae ; trials added 1500 ; truncation audit {'decisions': 720, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/E4_sig.parquet', 'l2vast/pred/store/E1_sigu.parquet', 'l2vast/pred/store/E2_sigu.parquet', 'l2vast/pred/store/E3_sigu.parquet', 'l2vast/pred/store/E4_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S+E+allblocks-G | sig | NY/ST | gbt3 | 0.549 [0.53,0.57] | 0.558 [0.53,0.58] | - | - | - | - | - | - | - | - |  | short by 0.122 AUC, 5 of 5 econ |
| G-baseline-FAILPRED | sig | NY/HM | gbt3 | 0.560 [0.54,0.59] | 0.553 [0.52,0.59] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S+E+allblocks-G | sig | NY | gbt3 | 0.552 [0.53,0.57] | 0.550 [0.53,0.57] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | NY/ST | logit2 | 0.540 [0.52,0.56] | 0.549 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | NY | gbt3 | 0.548 [0.53,0.57] | 0.547 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | NY/HM | rf | 0.546 [0.52,0.57] | 0.547 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E1-E12-G-NEVER | sig | POOLED | gbt3 | 0.549 [0.50,0.60] | 0.547 [0.49,0.60] | - | - | - | - | - | - | - | - |  | short by 0.133 AUC, 5 of 5 econ |
| G-baseline-FAILPRED | sig | NY | logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base | sig | NY/ST | gbt3 | 0.541 [0.52,0.56] | 0.546 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base | sig | NY | logit2 | 0.547 [0.53,0.56] | 0.545 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G | sig | NY | stack | 0.545 [0.53,0.56] | 0.544 [0.52,0.57] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base | sig | NY/HM | gbt3 | 0.547 [0.52,0.57] | 0.542 [0.51,0.58] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E1-E12-G | sig | ASIA/HM | logit2 | 0.541 [0.51,0.57] | 0.541 [0.50,0.58] | - | - | - | - | - | - | - | - |  | short by 0.139 AUC, 5 of 5 econ |
| S+E+allblocks+base-G | sig | NY/ST | rf | 0.538 [0.52,0.56] | 0.539 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks-G-NEVER | sig | POOLED | gbt3 | 0.541 [0.53,0.56] | 0.536 [0.51,0.56] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S1-S5-G | sig | ASIA/HM | logit2 | 0.541 [0.51,0.57] | 0.535 [0.50,0.57] | - | - | - | - | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| S+E+allblocks-G | sig | LONDON/ST | gbt3 | 0.536 [0.51,0.56] | 0.535 [0.50,0.57] | - | - | - | - | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| S1-S5-G+base-NEVER | sig | POOLED/HM | rf | 0.534 [0.51,0.56] | 0.534 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G | sig | ASIA | stack | 0.521 [0.50,0.54] | 0.534 [0.51,0.56] | - | - | - | - | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| S+E+allblocks+base-G | sig | LONDON/ST | gbt3 | 0.534 [0.51,0.56] | 0.533 [0.50,0.57] | - | - | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| S+E1-E12-G-TAKEN | sig | POOLED/ST | logit2 | 0.511 [0.49,0.53] | 0.532 [0.51,0.56] | - | - | - | - | - | - | - | - |  | short by 0.148 AUC, 5 of 5 econ |
| S+E+allblocks+base-G-NEVER | sig | POOLED | gbt3 | 0.539 [0.53,0.55] | 0.532 [0.51,0.55] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S+E1-E12-G | sig | LONDON/ST | logit2 | 0.540 [0.51,0.57] | 0.532 [0.49,0.57] | - | - | - | - | - | - | - | - |  | short by 0.148 AUC, 5 of 5 econ |
| S+E+allblocks+base-G-NEVER | sig | POOLED/HM | gbt3 | 0.535 [0.52,0.56] | 0.532 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base | sig | POOLED/ST | logit2 | 0.524 [0.51,0.54] | 0.531 [0.51,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED-TAKEN | sig | POOLED/ST | gbt3 | 0.520 [0.50,0.54] | 0.531 [0.50,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base-TAKEN | sig | POOLED/ST | gbt3 | 0.516 [0.49,0.54] | 0.531 [0.50,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED-NEVER | sig | POOLED/HM | gbt3 | 0.535 [0.52,0.56] | 0.530 [0.50,0.56] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S1-S5-G-TAKEN | sig | POOLED/HM | logit2 | 0.536 [0.51,0.56] | 0.530 [0.50,0.56] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S1-S5-G+base-NEVER | sig | POOLED/ST | logit2 | 0.529 [0.51,0.55] | 0.530 [0.51,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks-G | sig | ASIA | gbt3 | 0.538 [0.52,0.56] | 0.530 [0.50,0.56] | - | - | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| S1-S5-G | sig | NY/HM | gbt3 | 0.525 [0.50,0.55] | 0.529 [0.50,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G-TAKEN | sig | POOLED/ST | rf | 0.506 [0.48,0.53] | 0.529 [0.49,0.56] | - | - | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| S+E1-E12-G | sig | NY/HM | logit2 | 0.525 [0.50,0.55] | 0.529 [0.50,0.57] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G-TAKEN | sig | POOLED | stack | 0.521 [0.50,0.54] | 0.529 [0.50,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | NY | stack | 0.529 [0.51,0.55] | 0.528 [0.50,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G-NEVER | sig | POOLED/ST | gbt3 | 0.530 [0.52,0.55] | 0.528 [0.50,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | POOLED | gbt3 | 0.532 [0.52,0.54] | 0.528 [0.51,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G | sig | POOLED/HM | logit2 | 0.531 [0.52,0.55] | 0.528 [0.51,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G | sig | POOLED | rf | 0.528 [0.52,0.54] | 0.528 [0.51,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G-NEVER | sig | POOLED/ST | logit2 | 0.531 [0.51,0.55] | 0.527 [0.50,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | POOLED/ST | logit2 | 0.525 [0.51,0.54] | 0.527 [0.51,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G-NEVER | sig | POOLED | rf | 0.534 [0.52,0.55] | 0.527 [0.51,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G-TAKEN | sig | POOLED/ST | gbt3 | 0.515 [0.49,0.54] | 0.526 [0.49,0.56] | - | - | - | - | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| G-baseline-FAILPRED | sig | POOLED/ST | logit2 | 0.522 [0.51,0.53] | 0.526 [0.51,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G-NEVER | sig | POOLED/HM | logit2 | 0.526 [0.51,0.55] | 0.526 [0.50,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G | sig | NY/ST | stack | 0.522 [0.50,0.54] | 0.525 [0.49,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | ASIA | rf | 0.517 [0.50,0.54] | 0.525 [0.50,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED-NEVER | sig | POOLED/ST | logit2 | 0.525 [0.51,0.54] | 0.525 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks-G | sig | POOLED/ST | gbt3 | 0.524 [0.51,0.54] | 0.524 [0.51,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | NY/HM | gbt3 | 0.540 [0.52,0.56] | 0.524 [0.50,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | LONDON/ST | stack | 0.516 [0.49,0.55] | 0.524 [0.49,0.56] | - | - | - | - | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| S1-S5-G+base-NEVER | sig | POOLED | stack | 0.535 [0.48,0.58] | 0.523 [0.46,0.60] | - | - | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| G-baseline-FAILPRED | sig | NY/HM | logit2 | 0.513 [0.49,0.54] | 0.523 [0.49,0.56] | - | - | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| S+E+allblocks+base-G | sig | ASIA | rf | 0.523 [0.50,0.55] | 0.523 [0.49,0.55] | - | - | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| S1-S5-G+base-NEVER | sig | POOLED | logit2 | 0.527 [0.51,0.54] | 0.523 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E1-E12-G-TAKEN | sig | POOLED/HM | logit2 | 0.530 [0.51,0.55] | 0.522 [0.50,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | ASIA/HM | rf | 0.535 [0.51,0.57] | 0.522 [0.48,0.57] | - | - | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| S+E1-E12-G | sig | POOLED/ST | logit2 | 0.516 [0.50,0.53] | 0.522 [0.51,0.54] | - | - | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| S1-S5-G-TAKEN | sig | POOLED | stack | 0.522 [0.50,0.55] | 0.522 [0.49,0.55] | - | - | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| S+E1-E12-G-TAKEN | sig | POOLED | rf | 0.519 [0.50,0.54] | 0.521 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G-TAKEN | sig | POOLED | gbt3 | 0.522 [0.51,0.54] | 0.521 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks-G | sig | POOLED | stack | 0.529 [0.52,0.54] | 0.521 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | ASIA/HM | rf | 0.525 [0.50,0.55] | 0.520 [0.48,0.56] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| G-context-NEVER | sig | POOLED | rf | 0.533 [0.48,0.58] | 0.520 [0.46,0.58] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| S+E+allblocks-G-TAKEN | sig | POOLED | gbt3 | 0.526 [0.51,0.54] | 0.520 [0.49,0.55] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| S+E1-E12-G | sig | NY/ST | stack | 0.525 [0.50,0.55] | 0.520 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | ASIA/ST | logit2 | 0.505 [0.48,0.54] | 0.519 [0.49,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | POOLED | rf | 0.525 [0.51,0.54] | 0.519 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | ASIA | gbt3 | 0.510 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| S+E+allblocks+base-G | sig | ASIA | gbt3 | 0.515 [0.49,0.54] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context | sig | ASIA | logit2 | 0.511 [0.49,0.54] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G-TAKEN | sig | POOLED/ST | rf | 0.514 [0.49,0.54] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | NY/ST | rf | 0.516 [0.50,0.54] | 0.518 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| S1-S5-G+base | sig | POOLED | logit2 | 0.520 [0.51,0.53] | 0.518 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | LONDON | logit2 | 0.513 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| S1-S5-G+base-TAKEN | sig | POOLED | rf | 0.518 [0.50,0.54] | 0.518 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | ASIA/HM | logit2 | 0.518 [0.49,0.55] | 0.518 [0.48,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E1-E12-G | sig | NY/ST | logit2 | 0.510 [0.49,0.53] | 0.517 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| G-baseline-FAILPRED-NEVER | sig | POOLED | logit2 | 0.519 [0.51,0.53] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| S+E+allblocks-G | sig | ASIA/HM | rf | 0.532 [0.50,0.56] | 0.517 [0.48,0.56] | - | - | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| G-baseline-FAILPRED | sig | ASIA/ST | stack | 0.526 [0.50,0.55] | 0.517 [0.48,0.55] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S+E+allblocks-G-NEVER | sig | POOLED/HM | gbt3 | 0.531 [0.51,0.55] | 0.517 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | ASIA | logit2 | 0.511 [0.48,0.54] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | ASIA | logit2 | 0.515 [0.49,0.54] | 0.516 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | POOLED | logit2 | 0.515 [0.49,0.54] | 0.516 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | POOLED | logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E1-E12-G-NEVER | sig | POOLED | rf | 0.514 [0.50,0.53] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| S+E1-E12-G-NEVER | sig | POOLED | stack | 0.528 [0.51,0.55] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G-TAKEN | sig | POOLED/ST | gbt3 | 0.513 [0.49,0.54] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | NY | logit2 | 0.521 [0.50,0.54] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| S1-S5-G+base-NEVER | sig | POOLED | gbt3 | 0.524 [0.47,0.58] | 0.516 [0.45,0.58] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context-TAKEN | sig | POOLED | logit2 | 0.508 [0.48,0.53] | 0.516 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G-TAKEN | sig | POOLED/ST | stack | 0.509 [0.48,0.53] | 0.516 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | POOLED | logit2 | 0.511 [0.48,0.54] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | ASIA | logit2 | 0.511 [0.48,0.54] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E1-E12-G-NEVER | sig | POOLED/ST | logit2 | 0.518 [0.50,0.53] | 0.515 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| S1-S5-G+base-NEVER | sig | POOLED | logit2 | 0.518 [0.50,0.53] | 0.515 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| S1-S5-G+base | sig | POOLED/HM | logit2 | 0.521 [0.51,0.54] | 0.515 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G-NEVER | sig | POOLED | gbt3 | 0.531 [0.48,0.59] | 0.515 [0.45,0.58] | - | - | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| S1-S5-G | sig | ASIA/ST | stack | 0.521 [0.49,0.55] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | POOLED/ST | rf | 0.521 [0.51,0.54] | 0.514 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | POOLED | logit2 | 0.510 [0.48,0.53] | 0.514 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| S+E1-E12-G | sig | ASIA | logit2 | 0.510 [0.48,0.53] | 0.514 [0.48,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S1-S5-G | sig | POOLED | stack | 0.515 [0.49,0.54] | 0.514 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| S1-S5-G | sig | ASIA | stack | 0.515 [0.49,0.54] | 0.514 [0.49,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S1-S5-G-NEVER | sig | POOLED/ST | logit2 | 0.517 [0.50,0.53] | 0.514 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G-NEVER | sig | POOLED | gbt3 | 0.526 [0.47,0.58] | 0.514 [0.45,0.59] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context | sig | LONDON/ST | rf | 0.521 [0.49,0.55] | 0.514 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| S+E+allblocks-G | sig | POOLED/HM | rf | 0.524 [0.51,0.54] | 0.514 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | LONDON | stack | 0.512 [0.49,0.53] | 0.514 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| S+E+allblocks-G | sig | POOLED/ST | gbt3 | 0.515 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| S+E1-E12-G | sig | ASIA/ST | rf | 0.497 [0.47,0.52] | 0.513 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | POOLED/ST | gbt3 | 0.509 [0.50,0.52] | 0.513 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| S+E+allblocks+base-G-TAKEN | sig | POOLED | gbt3 | 0.513 [0.49,0.53] | 0.513 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| S+E1-E12-G | sig | POOLED | rf | 0.507 [0.50,0.52] | 0.513 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| G-baseline-FAILPRED-NEVER | sig | POOLED | gbt3 | 0.520 [0.51,0.53] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context | sig | NY/ST | rf | 0.505 [0.48,0.52] | 0.512 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| S1-S5-G+base-NEVER | sig | POOLED/HM | gbt3 | 0.513 [0.49,0.53] | 0.512 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| G-context | sig | POOLED/ST | stack | 0.512 [0.50,0.52] | 0.512 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | NY | gbt3 | 0.506 [0.49,0.52] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| S1-S5-G+base | sig | NY/HM | gbt3 | 0.517 [0.49,0.54] | 0.512 [0.48,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| G-baseline-FAILPRED-NEVER | sig | POOLED/HM | stack | 0.511 [0.49,0.53] | 0.512 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| S1-S5-G+base | sig | ASIA | stack | 0.513 [0.49,0.54] | 0.512 [0.48,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | POOLED | rf | 0.515 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| S+E+allblocks+base-G-TAKEN | sig | POOLED/ST | gbt3 | 0.518 [0.50,0.54] | 0.512 [0.48,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | POOLED/HM | gbt3 | 0.521 [0.51,0.54] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | LONDON | rf | 0.516 [0.49,0.53] | 0.511 [0.48,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| S+E1-E12-G-NEVER | sig | POOLED/ST | rf | 0.525 [0.51,0.54] | 0.511 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| G-context | sig | POOLED/ST | rf | 0.511 [0.50,0.52] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| G-context-TAKEN | sig | POOLED/ST | rf | 0.524 [0.50,0.54] | 0.511 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| G-baseline-FAILPRED | sig | LONDON/HM | rf | 0.518 [0.49,0.55] | 0.511 [0.46,0.56] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| G-context | sig | NY/ST | stack | 0.513 [0.49,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base | sig | NY | logit2 | 0.518 [0.50,0.54] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| S+E1-E12-G | sig | ASIA/HM | stack | 0.517 [0.48,0.55] | 0.510 [0.47,0.55] | - | - | - | - | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| G-context-NEVER | sig | POOLED | stack | 0.505 [0.49,0.52] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | POOLED/ST | rf | 0.509 [0.49,0.52] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| S1-S5-G | sig | ASIA/ST | logit2 | 0.492 [0.46,0.52] | 0.510 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | POOLED/HM | rf | 0.523 [0.51,0.54] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G | sig | POOLED/ST | stack | 0.508 [0.49,0.52] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base | sig | POOLED | logit2 | 0.511 [0.50,0.52] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| S+E+allblocks+base-G | sig | ASIA | logit2 | 0.511 [0.49,0.53] | 0.510 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S+E+allblocks+base-G | sig | POOLED | logit2 | 0.511 [0.49,0.53] | 0.510 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| S1-S5-G | sig | NY | rf | 0.510 [0.49,0.53] | 0.510 [0.48,0.53] | - | - | - | - | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| S+E+allblocks-G-TAKEN | sig | POOLED | rf | 0.508 [0.48,0.54] | 0.510 [0.47,0.55] | - | - | - | - | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| S+E1-E12-G | sig | POOLED | logit2 | 0.513 [0.49,0.54] | 0.509 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | ASIA | logit2 | 0.513 [0.49,0.54] | 0.509 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context-TAKEN | sig | POOLED/HM | logit2 | 0.515 [0.49,0.54] | 0.509 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | ASIA | stack | 0.509 [0.48,0.53] | 0.509 [0.48,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context | sig | POOLED/HM | rf | 0.509 [0.49,0.53] | 0.509 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G-TAKEN | sig | POOLED | rf | 0.518 [0.50,0.54] | 0.509 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | ASIA/ST | rf | 0.511 [0.48,0.54] | 0.508 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED-TAKEN | sig | POOLED | rf | 0.510 [0.49,0.53] | 0.508 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context-TAKEN | sig | POOLED/ST | stack | 0.520 [0.50,0.54] | 0.508 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | ASIA | rf | 0.507 [0.48,0.53] | 0.508 [0.48,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S+E+allblocks-G | sig | POOLED | rf | 0.507 [0.48,0.53] | 0.508 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| S+E1-E12-G-NEVER | sig | POOLED/HM | stack | 0.524 [0.50,0.55] | 0.507 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | POOLED/HM | rf | 0.520 [0.51,0.54] | 0.507 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | POOLED | gbt3 | 0.520 [0.51,0.53] | 0.507 [0.49,0.52] | - | - | - | - | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| S+E+allblocks+base-G-NEVER | sig | POOLED | rf | 0.517 [0.50,0.53] | 0.506 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S1-S5-G-NEVER | sig | POOLED | rf | 0.508 [0.49,0.52] | 0.506 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | NY/HM | stack | 0.510 [0.48,0.54] | 0.506 [0.47,0.55] | - | - | - | - | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| S+E+allblocks-G-NEVER | sig | POOLED/ST | gbt3 | 0.515 [0.50,0.53] | 0.506 [0.48,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-context-NEVER | sig | POOLED/ST | stack | 0.497 [0.48,0.52] | 0.506 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base | sig | ASIA/HM | stack | 0.522 [0.49,0.55] | 0.506 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.174 AUC, 5 of 5 econ |
| G-context | sig | ASIA | logit2 | 0.511 [0.49,0.54] | 0.505 [0.48,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-context | sig | POOLED | logit2 | 0.511 [0.49,0.54] | 0.505 [0.48,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S1-S5-G | sig | NY/HM | rf | 0.508 [0.48,0.53] | 0.505 [0.47,0.54] | - | - | - | - | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| G-context | sig | ASIA/HM | logit2 | 0.515 [0.49,0.54] | 0.504 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G | sig | POOLED | gbt3 | 0.506 [0.49,0.52] | 0.504 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | LONDON/ST | gbt3 | 0.524 [0.50,0.55] | 0.504 [0.46,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-context | sig | ASIA | logit2 | 0.505 [0.48,0.53] | 0.504 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | POOLED | logit2 | 0.505 [0.48,0.53] | 0.504 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G | sig | POOLED/HM | rf | 0.512 [0.50,0.53] | 0.504 [0.48,0.53] | - | - | - | - | - | - | - | - |  | short by 0.176 AUC, 5 of 5 econ |
| S+E+allblocks+base-G-TAKEN | sig | POOLED | logit2 | 0.502 [0.47,0.53] | 0.503 [0.46,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E1-E12-G | sig | ASIA | stack | 0.511 [0.49,0.53] | 0.503 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S+E+allblocks-G | sig | NY | gbt3 | 0.515 [0.50,0.53] | 0.503 [0.48,0.52] | - | - | - | - | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| S1-S5-G+base | sig | ASIA/HM | gbt3 | 0.510 [0.49,0.54] | 0.503 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G-TAKEN | sig | POOLED/HM | rf | 0.517 [0.49,0.54] | 0.503 [0.47,0.54] | - | - | - | - | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| G-baseline-FAILPRED-TAKEN | sig | POOLED | logit2 | 0.502 [0.48,0.52] | 0.503 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | POOLED | logit2 | 0.501 [0.48,0.52] | 0.503 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | ASIA | logit2 | 0.501 [0.48,0.52] | 0.503 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks-G-TAKEN | sig | POOLED | logit2 | 0.505 [0.48,0.53] | 0.503 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G-TAKEN | sig | POOLED | logit2 | 0.503 [0.48,0.53] | 0.502 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | NY/ST | gbt3 | 0.506 [0.49,0.53] | 0.502 [0.48,0.53] | - | - | - | - | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| S1-S5-G-NEVER | sig | POOLED | gbt3 | 0.513 [0.46,0.57] | 0.502 [0.44,0.57] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base-TAKEN | sig | POOLED | logit2 | 0.501 [0.48,0.52] | 0.502 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G-NEVER | sig | POOLED/HM | rf | 0.505 [0.48,0.53] | 0.502 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | NY/ST | rf | 0.505 [0.48,0.53] | 0.501 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.179 AUC, 5 of 5 econ |
| S+E1-E12-G | sig | ASIA/ST | logit2 | 0.507 [0.48,0.53] | 0.501 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G-TAKEN | sig | POOLED | logit2 | 0.507 [0.48,0.53] | 0.501 [0.46,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G-NEVER | sig | POOLED/ST | gbt3 | 0.512 [0.49,0.53] | 0.501 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| G-context-NEVER | sig | POOLED/HM | stack | 0.497 [0.48,0.52] | 0.500 [0.48,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | LONDON | gbt3 | 0.517 [0.49,0.54] | 0.500 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S1-S5-G+base | sig | ASIA/ST | gbt3 | 0.495 [0.46,0.52] | 0.500 [0.46,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | POOLED/HM | stack | 0.503 [0.49,0.52] | 0.500 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context-NEVER | sig | POOLED/HM | rf | 0.504 [0.48,0.53] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G-NEVER | sig | POOLED/HM | rf | 0.513 [0.49,0.53] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S1-S5-G | sig | LONDON/HM | rf | 0.518 [0.49,0.55] | 0.499 [0.46,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-baseline-FAILPRED-TAKEN | sig | POOLED | logit2 | 0.500 [0.47,0.53] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base-TAKEN | sig | POOLED | logit2 | 0.496 [0.47,0.52] | 0.499 [0.46,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks-G | sig | ASIA/ST | gbt3 | 0.497 [0.47,0.52] | 0.499 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | POOLED/HM | rf | 0.511 [0.50,0.53] | 0.498 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| G-context-TAKEN | sig | POOLED | gbt3 | 0.504 [0.48,0.52] | 0.498 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | ASIA/ST | stack | 0.510 [0.48,0.54] | 0.498 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED-TAKEN | sig | POOLED | stack | 0.506 [0.48,0.53] | 0.498 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks-G-NEVER | sig | POOLED | gbt3 | 0.515 [0.50,0.53] | 0.498 [0.48,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S+E+allblocks+base-G-TAKEN | sig | POOLED/HM | rf | 0.518 [0.50,0.54] | 0.498 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S+E1-E12-G-TAKEN | sig | POOLED | logit2 | 0.507 [0.48,0.53] | 0.498 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base | sig | POOLED/HM | gbt3 | 0.509 [0.49,0.52] | 0.497 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | NY | gbt3 | 0.506 [0.49,0.53] | 0.497 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED-NEVER | sig | POOLED | gbt3 | 0.516 [0.47,0.57] | 0.497 [0.44,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context | sig | NY/HM | rf | 0.511 [0.49,0.54] | 0.497 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | LONDON | rf | 0.511 [0.49,0.53] | 0.496 [0.46,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-baseline-FAILPRED-NEVER | sig | POOLED/ST | gbt3 | 0.507 [0.49,0.52] | 0.496 [0.48,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks-G-TAKEN | sig | POOLED/HM | stack | 0.524 [0.50,0.55] | 0.496 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S1-S5-G+base | sig | LONDON/ST | gbt3 | 0.504 [0.48,0.53] | 0.496 [0.46,0.53] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S1-S5-G+base | sig | LONDON/HM | rf | 0.515 [0.48,0.55] | 0.496 [0.45,0.54] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| G-context | sig | ASIA | gbt3 | 0.501 [0.47,0.53] | 0.496 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | LONDON/ST | logit2 | 0.504 [0.48,0.52] | 0.496 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| G-context | sig | POOLED | gbt3 | 0.496 [0.48,0.51] | 0.495 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | NY/HM | rf | 0.502 [0.48,0.53] | 0.495 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | POOLED/HM | stack | 0.503 [0.49,0.52] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G-TAKEN | sig | POOLED/HM | rf | 0.521 [0.50,0.54] | 0.495 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base | sig | LONDON/ST | logit2 | 0.502 [0.48,0.52] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S1-S5-G+base | sig | ASIA | stack | 0.494 [0.47,0.52] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base | sig | POOLED | stack | 0.494 [0.47,0.52] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | ASIA/HM | gbt3 | 0.501 [0.48,0.53] | 0.495 [0.46,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G-NEVER | sig | POOLED | stack | 0.506 [0.46,0.56] | 0.495 [0.43,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | ASIA/ST | gbt3 | 0.508 [0.48,0.53] | 0.495 [0.46,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G | sig | ASIA/HM | rf | 0.505 [0.47,0.54] | 0.494 [0.45,0.54] | - | - | - | - | - | - | - | - |  | short by 0.186 AUC, 5 of 5 econ |
| S1-S5-G | sig | POOLED | logit2 | 0.502 [0.48,0.53] | 0.494 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G | sig | ASIA | logit2 | 0.502 [0.48,0.53] | 0.494 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G-TAKEN | sig | POOLED | stack | 0.491 [0.47,0.51] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | ASIA | stack | 0.506 [0.48,0.53] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | POOLED | stack | 0.506 [0.48,0.53] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E1-E12-G | sig | LONDON | rf | 0.523 [0.50,0.55] | 0.494 [0.46,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S1-S5-G+base-TAKEN | sig | POOLED/HM | gbt3 | 0.509 [0.49,0.53] | 0.494 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G-TAKEN | sig | POOLED | logit2 | 0.501 [0.48,0.53] | 0.494 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | NY/HM | rf | 0.503 [0.48,0.52] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base | sig | LONDON | gbt3 | 0.500 [0.48,0.52] | 0.494 [0.46,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G-TAKEN | sig | POOLED | gbt3 | 0.501 [0.48,0.52] | 0.493 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base | sig | ASIA/ST | stack | 0.503 [0.47,0.53] | 0.493 [0.46,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context-NEVER | sig | POOLED | gbt3 | 0.491 [0.48,0.51] | 0.493 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G | sig | LONDON | gbt3 | 0.499 [0.48,0.52] | 0.493 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | NY | stack | 0.507 [0.49,0.53] | 0.493 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | POOLED/HM | rf | 0.506 [0.49,0.52] | 0.493 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G-NEVER | sig | POOLED | stack | 0.499 [0.46,0.54] | 0.492 [0.45,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G-TAKEN | sig | POOLED/HM | stack | 0.506 [0.48,0.53] | 0.492 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G-NEVER | sig | POOLED/ST | stack | 0.503 [0.48,0.52] | 0.492 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G-NEVER | sig | POOLED | rf | 0.515 [0.46,0.57] | 0.492 [0.43,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G | sig | POOLED/ST | stack | 0.501 [0.49,0.52] | 0.492 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | LONDON | gbt3 | 0.511 [0.49,0.53] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S1-S5-G-TAKEN | sig | POOLED/ST | stack | 0.499 [0.47,0.52] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G-TAKEN | sig | POOLED/HM | rf | 0.520 [0.50,0.54] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G | sig | LONDON/HM | logit2 | 0.517 [0.49,0.54] | 0.491 [0.45,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-context-TAKEN | sig | POOLED/HM | stack | 0.510 [0.49,0.53] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-baseline-FAILPRED-TAKEN | sig | POOLED/ST | stack | 0.498 [0.48,0.52] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context | sig | POOLED | gbt3 | 0.499 [0.49,0.51] | 0.491 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context-NEVER | sig | POOLED/ST | gbt3 | 0.494 [0.48,0.51] | 0.491 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | LONDON | gbt3 | 0.497 [0.47,0.52] | 0.490 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G | sig | ASIA | stack | 0.495 [0.47,0.52] | 0.490 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | ASIA/HM | logit2 | 0.512 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S+E+allblocks+base-G-NEVER | sig | POOLED/HM | gbt3 | 0.501 [0.48,0.52] | 0.489 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base | sig | LONDON | rf | 0.494 [0.47,0.52] | 0.489 [0.46,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED-TAKEN | sig | POOLED/HM | gbt3 | 0.505 [0.48,0.53] | 0.489 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | ASIA/ST | rf | 0.496 [0.47,0.52] | 0.489 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base-NEVER | sig | POOLED/ST | stack | 0.502 [0.48,0.52] | 0.488 [0.47,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | ASIA/ST | stack | 0.495 [0.46,0.53] | 0.488 [0.45,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base | sig | POOLED/ST | stack | 0.498 [0.49,0.51] | 0.487 [0.47,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G | sig | LONDON/ST | logit2 | 0.504 [0.47,0.53] | 0.487 [0.45,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S+E+allblocks-G | sig | POOLED/HM | rf | 0.509 [0.50,0.52] | 0.487 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context-TAKEN | sig | POOLED | stack | 0.497 [0.47,0.52] | 0.486 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base-TAKEN | sig | POOLED/ST | stack | 0.491 [0.47,0.52] | 0.486 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E1-E12-G-NEVER | sig | POOLED | stack | 0.506 [0.46,0.55] | 0.486 [0.43,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G | sig | LONDON | rf | 0.498 [0.48,0.52] | 0.485 [0.46,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | NY/HM | rf | 0.503 [0.48,0.52] | 0.485 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | LONDON/ST | gbt3 | 0.495 [0.47,0.52] | 0.484 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context | sig | NY | rf | 0.489 [0.47,0.51] | 0.483 [0.46,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | LONDON/HM | logit2 | 0.474 [0.45,0.50] | 0.483 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base | sig | NY/ST | stack | 0.505 [0.48,0.52] | 0.481 [0.45,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | LONDON/ST | logit2 | 0.509 [0.48,0.54] | 0.481 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| S1-S5-G+base-TAKEN | sig | POOLED/HM | gbt3 | 0.503 [0.48,0.53] | 0.479 [0.45,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED-NEVER | sig | POOLED | gbt3 | 0.506 [0.46,0.55] | 0.478 [0.42,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks-G | sig | LONDON/ST | logit2 | 0.505 [0.48,0.53] | 0.478 [0.44,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S1-S5-G+base | sig | ASIA | stack | 0.490 [0.46,0.52] | 0.477 [0.44,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S+E+allblocks-G | sig | LONDON | logit2 | 0.513 [0.49,0.53] | 0.477 [0.44,0.51] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| S+E+allblocks-G-NEVER | sig | POOLED/HM | rf | 0.500 [0.48,0.52] | 0.477 [0.45,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G | sig | LONDON/ST | gbt3 | 0.487 [0.46,0.51] | 0.476 [0.44,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base | sig | LONDON/HM | logit2 | 0.496 [0.47,0.52] | 0.476 [0.44,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED-TAKEN | sig | POOLED/HM | gbt3 | 0.492 [0.47,0.51] | 0.476 [0.44,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G | sig | NY/ST | stack | 0.503 [0.48,0.53] | 0.475 [0.44,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | LONDON/HM | stack | 0.485 [0.46,0.52] | 0.473 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S1-S5-G+base-TAKEN | sig | POOLED | stack | 0.482 [0.46,0.51] | 0.471 [0.44,0.50] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-context-TAKEN | sig | POOLED | gbt3 | 0.501 [0.48,0.52] | 0.471 [0.45,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | LONDON/HM | rf | 0.495 [0.47,0.52] | 0.470 [0.43,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base | sig | POOLED | stack | 0.483 [0.46,0.51] | 0.468 [0.44,0.49] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| S1-S5-G+base | sig | ASIA | stack | 0.483 [0.46,0.51] | 0.468 [0.44,0.49] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | LONDON/HM | logit2 | 0.493 [0.46,0.52] | 0.466 [0.43,0.50] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-baseline-FAILPRED | sig | ASIA/HM | stack | 0.492 [0.46,0.52] | 0.464 [0.43,0.50] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| G-context-NEVER | sig | POOLED | logit2 | 0.496 [0.44,0.55] | 0.462 [0.40,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | LONDON/HM | rf | 0.494 [0.46,0.53] | 0.458 [0.42,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-context | sig | LONDON | gbt3 | 0.472 [0.45,0.50] | 0.455 [0.43,0.48] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | LONDON/HM | rf | 0.503 [0.47,0.53] | 0.455 [0.42,0.49] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E1-E12-G | sig | LONDON/HM | rf | 0.494 [0.46,0.53] | 0.453 [0.41,0.49] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks-G | sig | LONDON/HM | rf | 0.490 [0.46,0.52] | 0.447 [0.41,0.48] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| S+E+allblocks+base-G | sig | LONDON/HM | rf | 0.486 [0.45,0.52] | 0.445 [0.41,0.49] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- S+E+allblocks-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- G-baseline-FAILPRED-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks+base-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- G-context-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- G-baseline-FAILPRED -1 NY: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- G-context-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks-G -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks-G -1 NY: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G+base -1 NY: per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S1-S5-G -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G -1 NY: per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks+base-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks+base-G -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks-G -1 NY: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S1-S5-G -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S+E1-E12-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- S1-S5-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks+base-G -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- G-context-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- S+E1-E12-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- G-context -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G -1 NY: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base -1 NY: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G+base-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S1-S5-G+base-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- G-baseline-FAILPRED-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- G-baseline-FAILPRED -1 NY: per-signal cross-asset S1-S5; scope=ST
- G-baseline-FAILPRED -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- G-context -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- S+E1-E12-G -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G -1 NY: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks+base-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- G-context -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G -1 NY: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base -1 NY: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks+base-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks+base-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- G-context -1 NY: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- G-context-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks+base-G -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 NY: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- G-context-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S1-S5-G+base -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- G-baseline-FAILPRED-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S+E1-E12-G -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- S+E1-E12-G -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G -1 NY: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G+base-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S1-S5-G+base -1 NY: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- S1-S5-G -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G+base-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- G-context -1 NY: per-signal cross-asset S1-S5; scope=pooled
- G-context-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S1-S5-G+base-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks+base-G -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ASIA
- G-baseline-FAILPRED -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- G-baseline-FAILPRED -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- G-context -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks+base-G -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S+E1-E12-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- G-context-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- G-context -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- G-context -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks+base-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks-G -1 NY: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G -1 NY: per-signal cross-asset S1-S5; scope=ST
- G-context -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks-G -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks+base-G -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks+base-G -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- G-context-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- G-context -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- G-context -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED -1 NY: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks+base-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- G-context-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- G-context -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S+E1-E12-G -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 ASIA: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G+base -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks+base-G -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks+base-G -1 NY: per-signal cross-asset S1-S5; scope=HM
- G-context-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S1-S5-G-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G -1 NY: per-signal cross-asset S1-S5; scope=ST
- G-context -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- S1-S5-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- G-context -1 NY: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=HM
- S1-S5-G -1 NY: per-signal cross-asset S1-S5; scope=HM
- S+E+allblocks-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- G-baseline-FAILPRED -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- G-context -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks-G -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S+E1-E12-G -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S+E1-E12-G -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- S+E1-E12-G -1 NY: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- G-baseline-FAILPRED -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks+base-G -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G -1 NY: per-signal cross-asset S1-S5; scope=ST
- G-context -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- G-context -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- S+E1-E12-G -1 NY: per-signal cross-asset S1-S5; scope=ST
- G-context -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- G-baseline-FAILPRED -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- G-baseline-FAILPRED -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- G-baseline-FAILPRED -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- G-context-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- G-context -1 POOLED: per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- S+E+allblocks+base-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- G-baseline-FAILPRED -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- G-context -1 NY: per-signal cross-asset S1-S5; scope=ST
- G-context -1 ASIA: per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED -1 NY: per-signal cross-asset S1-S5; scope=HM
- S+E1-E12-G -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G -1 POOLED: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G -1 LONDON: per-signal cross-asset S1-S5; scope=ST
- G-baseline-FAILPRED-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- G-baseline-FAILPRED-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- G-baseline-FAILPRED -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- S1-S5-G+base-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 NY: per-signal cross-asset S1-S5; scope=pooled
- G-context-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- G-baseline-FAILPRED -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- G-baseline-FAILPRED -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- G-context -1 POOLED: per-signal cross-asset S1-S5; scope=pooled
- G-context-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- G-context -1 NY: per-signal cross-asset S1-S5; scope=ST
- S+E+allblocks-G -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- G-baseline-FAILPRED -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base -1 ASIA: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base -1 POOLED: per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- G-context -1 NY: per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- S1-S5-G+base-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ASIA
- S1-S5-G+base -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- G-context -1 LONDON: per-signal cross-asset S1-S5; scope=HM
- G-context-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=ST
- G-context -1 LONDON: per-signal cross-asset S1-S5; scope=pooled
- G-context -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- S+E1-E12-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=pooled
- S+E+allblocks+base-G-TAKEN -1 POOLED: subset TAKEN; per-signal cross-asset S1-S5; scope=ST
- G-context-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=HM
- G-context-NEVER -1 POOLED: subset NEVER; per-signal cross-asset S1-S5; scope=pooled
- S+E1-E12-G -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- S1-S5-G -1 ASIA: per-signal cross-asset S1-S5; scope=ST
- G-context -1 LONDON: per-signal cross-asset S1-S5; scope=HM
