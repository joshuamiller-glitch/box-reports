# PRED ROUND 68 - block G round 6 - G-regime-sequence-unlocked-G

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.554 [0.53,0.58]
Gap to FOUND: 0.126 AUC, 5 of 5 economic conditions short.
not found - short by 0.126 AUC and 5 of 5 economic conditions

prereg 2fa5c9a260b645aaed6ba76df0f29f734dabd0434afba0ddd21ddd230fbb605f ; trials added 900 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': True, 'note': 'same feature functions as locked stores (audits 0 mismatches; first G1-G7 audit had 266 mismatches from HMM param-file mismatch, fixed); taken-subset sigu features reproduce the locked-store features exactly (max rel diff 0 for G1,G2,G4,G5,G6,G7)'} ; holdout scored True ; feature store ['l2vast/pred/store/G1_sigu.parquet', 'l2vast/pred/store/G2_sigu.parquet', 'l2vast/pred/store/G3_sigu.parquet', 'l2vast/pred/store/G4_sigu.parquet', 'l2vast/pred/store/G5_sigu.parquet', 'l2vast/pred/store/G6_sigu.parquet', 'l2vast/pred/store/G7_sigu.parquet', 'l2vast/pred/store/G8_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G-sigu-G1 | sig | NY | logit2 | 0.549 [0.53,0.57] | 0.554 [0.53,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G6 | sig | NY | logit2 | 0.542 [0.52,0.56] | 0.549 [0.53,0.57] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL | sig | NY | logit2 | 0.547 [0.53,0.56] | 0.547 [0.53,0.57] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G6+BASE | sig | NY | logit2 | 0.546 [0.53,0.56] | 0.546 [0.53,0.57] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-ALLG+BASE | sig | NY | gbt3 | 0.548 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | NY | logit2 | 0.543 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-BASE | sig | NY | logit2 | 0.543 [0.53,0.56] | 0.545 [0.52,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3+BASE | sig | NY | logit2 | 0.543 [0.53,0.56] | 0.545 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-GALL+BASE | sig | NY | logit2 | 0.546 [0.53,0.56] | 0.543 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G8 | sig | NY | logit2 | 0.534 [0.52,0.55] | 0.542 [0.52,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8 | sig | POOLED/ST | logit2 | 0.531 [0.52,0.54] | 0.535 [0.52,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G7 | sig | ASIA | logit2 | 0.525 [0.50,0.54] | 0.530 [0.50,0.56] | - | - | - | N | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| G-sigu-G3 | sig | POOLED/ST | gbt3 | 0.523 [0.51,0.54] | 0.530 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8 | sig | POOLED | logit2 | 0.526 [0.52,0.54] | 0.529 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G1 | sig | POOLED/HM | logit2 | 0.527 [0.51,0.54] | 0.527 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G7 | sig | NY | rf | 0.538 [0.52,0.55] | 0.526 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL | sig | POOLED/HM | logit2 | 0.528 [0.51,0.54] | 0.526 [0.50,0.55] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL | sig | POOLED | logit2 | 0.528 [0.52,0.54] | 0.525 [0.51,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL | sig | NY | rf | 0.520 [0.51,0.53] | 0.524 [0.50,0.54] | - | - | - | N | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| G-sigu-GALL | sig | POOLED/ST | logit2 | 0.527 [0.51,0.54] | 0.522 [0.51,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8 | sig | ASIA | stack | 0.514 [0.49,0.54] | 0.521 [0.49,0.55] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G2 | sig | NY | stack | 0.531 [0.52,0.55] | 0.521 [0.50,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-ALLG+BASE | sig | LONDON | rf | 0.508 [0.49,0.53] | 0.521 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| G-sigu-ALLG+BASE | sig | POOLED/ST | logit2 | 0.525 [0.51,0.54] | 0.521 [0.50,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G8 | sig | NY | gbt3 | 0.516 [0.50,0.53] | 0.520 [0.50,0.55] | - | - | - | N | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| G-sigu-GALL | sig | POOLED/HM | logit2 | 0.509 [0.49,0.52] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| G-sigu-G8 | sig | POOLED/HM | logit2 | 0.520 [0.51,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G6 | sig | POOLED | logit2 | 0.524 [0.51,0.54] | 0.520 [0.51,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL+BASE | sig | NY | logit2 | 0.525 [0.51,0.55] | 0.519 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| G-sigu-ALLG+BASE | sig | POOLED | logit2 | 0.524 [0.51,0.53] | 0.519 [0.50,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G6+BASE | sig | POOLED/ST | logit2 | 0.520 [0.51,0.53] | 0.519 [0.50,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-BASE | sig | LONDON | logit2 | 0.512 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | N | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| G-sigu-G3+BASE | sig | LONDON | logit2 | 0.512 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| G-sigu-G3 | sig | POOLED/ST | gbt3 | 0.521 [0.51,0.53] | 0.518 [0.50,0.54] | - | - | - | N | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| G-sigu-G7 | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.517 [0.50,0.54] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| G-sigu-GALL | sig | ASIA | stack | 0.498 [0.47,0.52] | 0.517 [0.48,0.55] | - | - | - | ok | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| G-sigu-G8+BASE | sig | LONDON | logit2 | 0.508 [0.49,0.53] | 0.517 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| G-sigu-G7 | sig | POOLED/ST | logit2 | 0.521 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| G-sigu-ALLG+BASE | sig | NY | logit2 | 0.523 [0.51,0.54] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| G-sigu-GALL+BASE | sig | POOLED | logit2 | 0.523 [0.51,0.54] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G1 | sig | POOLED/ST | gbt3 | 0.527 [0.51,0.54] | 0.516 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G2 | sig | POOLED/ST | rf | 0.523 [0.51,0.54] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL+BASE | sig | POOLED/ST | logit2 | 0.523 [0.51,0.54] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G6 | sig | POOLED/HM | logit2 | 0.523 [0.51,0.54] | 0.516 [0.49,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3+BASE | sig | NY | logit2 | 0.521 [0.50,0.54] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| G-sigu-BASE | sig | NY | logit2 | 0.522 [0.50,0.54] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| G-sigu-G8 | sig | POOLED | logit2 | 0.514 [0.50,0.53] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL+BASE | sig | POOLED/HM | logit2 | 0.523 [0.51,0.54] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-GALL | sig | POOLED | logit2 | 0.501 [0.48,0.52] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| G-sigu-GALL+BASE | sig | POOLED/ST | logit2 | 0.513 [0.50,0.53] | 0.515 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| G-sigu-G1 | sig | POOLED | gbt3 | 0.523 [0.51,0.53] | 0.515 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3 | sig | NY | stack | 0.517 [0.50,0.53] | 0.515 [0.49,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL | sig | POOLED | logit2 | 0.520 [0.50,0.54] | 0.514 [0.49,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G4 | sig | POOLED/HM | rf | 0.514 [0.50,0.53] | 0.514 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G6+BASE | sig | POOLED | logit2 | 0.518 [0.51,0.53] | 0.514 [0.50,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G3 | sig | POOLED/HM | stack | 0.505 [0.49,0.52] | 0.514 [0.49,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G7 | sig | ASIA | logit2 | 0.513 [0.49,0.54] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G6 | sig | POOLED/ST | gbt3 | 0.520 [0.51,0.53] | 0.513 [0.50,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-ALLG+BASE | sig | POOLED/HM | gbt3 | 0.519 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G3 | sig | POOLED | gbt3 | 0.505 [0.49,0.52] | 0.513 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3 | sig | POOLED | stack | 0.510 [0.50,0.52] | 0.513 [0.50,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-BASE | sig | POOLED/ST | logit2 | 0.512 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| G-sigu-G3+BASE | sig | POOLED/ST | logit2 | 0.512 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| G-sigu-GALL+BASE | sig | POOLED | logit2 | 0.513 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| G-sigu-G6+BASE | sig | NY | logit2 | 0.518 [0.50,0.54] | 0.513 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| G-sigu-G7 | sig | POOLED/ST | rf | 0.522 [0.51,0.53] | 0.512 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL | sig | POOLED | rf | 0.507 [0.50,0.52] | 0.512 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| G-sigu-G6 | sig | POOLED/ST | logit2 | 0.506 [0.49,0.52] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| G-sigu-G4 | sig | ASIA | gbt3 | 0.507 [0.49,0.53] | 0.512 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G1 | sig | NY | rf | 0.512 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| G-sigu-ALLG+BASE | sig | POOLED/HM | logit2 | 0.515 [0.50,0.53] | 0.512 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| G-sigu-ALLG+BASE | sig | POOLED | logit2 | 0.512 [0.50,0.52] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| G-sigu-ALLG+BASE | sig | POOLED/ST | logit2 | 0.509 [0.49,0.52] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-GALL | sig | ASIA | stack | 0.518 [0.50,0.54] | 0.511 [0.48,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | NY | logit2 | 0.518 [0.50,0.54] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-G6+BASE | sig | POOLED/HM | logit2 | 0.517 [0.50,0.53] | 0.511 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-G6+BASE | sig | POOLED | logit2 | 0.514 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-G4 | sig | POOLED/HM | stack | 0.514 [0.50,0.53] | 0.511 [0.49,0.54] | - | - | - | ok | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-BASE | sig | POOLED | logit2 | 0.513 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-G3+BASE | sig | POOLED | logit2 | 0.513 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-G6+BASE | sig | POOLED/ST | logit2 | 0.513 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-BASE | sig | POOLED | rf | 0.516 [0.50,0.53] | 0.511 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3+BASE | sig | POOLED | rf | 0.515 [0.50,0.53] | 0.511 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | POOLED/HM | logit2 | 0.515 [0.50,0.53] | 0.511 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-G6 | sig | NY | gbt3 | 0.509 [0.49,0.52] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-G8+BASE | sig | POOLED | rf | 0.515 [0.50,0.53] | 0.511 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G4 | sig | POOLED | stack | 0.512 [0.50,0.53] | 0.511 [0.49,0.54] | - | - | - | ok | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| G-sigu-G1 | sig | POOLED | logit2 | 0.516 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8 | sig | POOLED/HM | gbt3 | 0.513 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| G-sigu-G3 | sig | LONDON | rf | 0.509 [0.49,0.53] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| G-sigu-G4 | sig | POOLED | gbt3 | 0.510 [0.50,0.52] | 0.510 [0.50,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-BASE | sig | POOLED/ST | gbt3 | 0.513 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3+BASE | sig | POOLED/ST | gbt3 | 0.513 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | POOLED/ST | gbt3 | 0.513 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-GALL+BASE | sig | POOLED/HM | logit2 | 0.512 [0.50,0.53] | 0.510 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| G-sigu-G8+BASE | sig | POOLED | logit2 | 0.511 [0.50,0.52] | 0.509 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| G-sigu-G2 | sig | POOLED | rf | 0.519 [0.51,0.53] | 0.509 [0.50,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-BASE | sig | POOLED/HM | logit2 | 0.515 [0.50,0.53] | 0.509 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| G-sigu-G7 | sig | POOLED | logit2 | 0.510 [0.50,0.52] | 0.508 [0.49,0.52] | - | - | - | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| G-sigu-G3+BASE | sig | POOLED/HM | logit2 | 0.515 [0.50,0.53] | 0.508 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| G-sigu-G3 | sig | ASIA | gbt3 | 0.503 [0.48,0.53] | 0.508 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G1 | sig | POOLED/HM | rf | 0.509 [0.49,0.52] | 0.508 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| G-sigu-G8 | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.508 [0.49,0.52] | - | - | - | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| G-sigu-G2 | sig | ASIA | stack | 0.514 [0.49,0.54] | 0.508 [0.48,0.53] | - | - | - | ok | - | - | - | - |  | WF-only (dead) |
| G-sigu-G7 | sig | POOLED | rf | 0.519 [0.51,0.53] | 0.508 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | POOLED/ST | logit2 | 0.508 [0.49,0.52] | 0.508 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G6+BASE | sig | POOLED | rf | 0.510 [0.49,0.53] | 0.508 [0.48,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G4 | sig | POOLED/ST | gbt3 | 0.511 [0.50,0.52] | 0.507 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8 | sig | POOLED/ST | gbt3 | 0.511 [0.50,0.52] | 0.507 [0.49,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu-G6+BASE | sig | POOLED/HM | rf | 0.517 [0.50,0.53] | 0.507 [0.49,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G6 | sig | POOLED/HM | rf | 0.505 [0.49,0.52] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| G-sigu-G7 | sig | LONDON | gbt3 | 0.510 [0.49,0.53] | 0.506 [0.47,0.54] | - | - | - | N | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| G-sigu-GALL | sig | POOLED/ST | rf | 0.510 [0.50,0.52] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu-GALL+BASE | sig | POOLED | logit2 | 0.503 [0.48,0.52] | 0.506 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G3+BASE | sig | ASIA | rf | 0.505 [0.48,0.53] | 0.506 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G3 | sig | NY | gbt3 | 0.507 [0.49,0.52] | 0.506 [0.48,0.52] | - | - | - | N | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| G-sigu-G3 | sig | POOLED | gbt3 | 0.507 [0.50,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-BASE | sig | ASIA | rf | 0.507 [0.48,0.53] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu-G3 | sig | LONDON | gbt3 | 0.506 [0.49,0.52] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu-G1 | sig | ASIA | stack | 0.507 [0.49,0.53] | 0.504 [0.48,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G2 | sig | NY | rf | 0.505 [0.49,0.52] | 0.504 [0.48,0.52] | - | - | - | N | - | - | - | - |  | short by 0.176 AUC, 5 of 5 econ |
| G-sigu-G1 | sig | POOLED | rf | 0.505 [0.50,0.51] | 0.504 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G2 | sig | POOLED | rf | 0.504 [0.49,0.52] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | POOLED | rf | 0.507 [0.49,0.52] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-BASE | sig | POOLED | rf | 0.508 [0.49,0.52] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3+BASE | sig | POOLED | rf | 0.508 [0.49,0.53] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-ALLG+BASE | sig | POOLED | logit2 | 0.505 [0.49,0.52] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-BASE | sig | POOLED/HM | rf | 0.516 [0.50,0.53] | 0.503 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3+BASE | sig | POOLED/HM | rf | 0.516 [0.50,0.53] | 0.503 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-GALL+BASE | sig | POOLED | logit2 | 0.515 [0.50,0.53] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G4 | sig | ASIA | stack | 0.504 [0.48,0.53] | 0.503 [0.47,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G4 | sig | POOLED | gbt3 | 0.508 [0.49,0.52] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8 | sig | POOLED | gbt3 | 0.507 [0.49,0.52] | 0.503 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | POOLED/HM | rf | 0.515 [0.50,0.53] | 0.503 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G8 | sig | LONDON | logit2 | 0.511 [0.49,0.53] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu-G6+BASE | sig | POOLED | logit2 | 0.509 [0.49,0.53] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | POOLED | logit2 | 0.504 [0.48,0.52] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G2 | sig | POOLED/ST | rf | 0.505 [0.49,0.52] | 0.502 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-BASE | sig | POOLED | logit2 | 0.504 [0.48,0.52] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3+BASE | sig | POOLED | logit2 | 0.504 [0.48,0.52] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G6+BASE | sig | LONDON | gbt3 | 0.507 [0.48,0.53] | 0.502 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| G-sigu-G7 | sig | POOLED/HM | rf | 0.516 [0.50,0.53] | 0.501 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3 | sig | ASIA | gbt3 | 0.506 [0.49,0.53] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL | sig | LONDON | logit2 | 0.503 [0.48,0.53] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu-G7 | sig | POOLED | rf | 0.510 [0.49,0.53] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G1 | sig | POOLED/ST | rf | 0.502 [0.49,0.52] | 0.500 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G7 | sig | LONDON | logit2 | 0.502 [0.48,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8 | sig | ASIA | stack | 0.514 [0.49,0.54] | 0.500 [0.47,0.52] | - | - | - | ok | - | - | - | - |  | WF-only (dead) |
| G-sigu-G5 | sig | ASIA | stack | 0.504 [0.49,0.52] | 0.500 [0.47,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G4 | sig | NY | stack | 0.513 [0.50,0.53] | 0.499 [0.48,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G7 | sig | NY | logit2 | 0.505 [0.49,0.52] | 0.499 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G4 | sig | NY | stack | 0.505 [0.49,0.52] | 0.499 [0.48,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G6 | sig | POOLED | logit2 | 0.518 [0.50,0.53] | 0.498 [0.47,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G6 | sig | POOLED | rf | 0.499 [0.49,0.51] | 0.498 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G4 | sig | POOLED | stack | 0.504 [0.49,0.52] | 0.497 [0.48,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G5 | sig | LONDON | rf | 0.493 [0.47,0.51] | 0.497 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G2 | sig | POOLED | stack | 0.498 [0.48,0.51] | 0.497 [0.47,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G2 | sig | POOLED/HM | rf | 0.512 [0.50,0.53] | 0.497 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL+BASE | sig | ASIA | logit2 | 0.498 [0.47,0.52] | 0.497 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G7 | sig | POOLED/HM | logit2 | 0.495 [0.48,0.51] | 0.496 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G5 | sig | NY | stack | 0.513 [0.50,0.53] | 0.496 [0.47,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G5 | sig | POOLED | stack | 0.498 [0.48,0.51] | 0.496 [0.47,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL+BASE | sig | LONDON | gbt3 | 0.501 [0.48,0.53] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | ASIA | rf | 0.497 [0.47,0.52] | 0.495 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G4 | sig | LONDON | gbt3 | 0.503 [0.48,0.52] | 0.495 [0.47,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu-BASE | sig | ASIA | rf | 0.496 [0.47,0.52] | 0.495 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3+BASE | sig | ASIA | rf | 0.497 [0.47,0.52] | 0.495 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G8 | sig | LONDON | gbt3 | 0.505 [0.49,0.53] | 0.495 [0.47,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu-G5 | sig | POOLED/ST | gbt3 | 0.503 [0.49,0.52] | 0.494 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G6 | sig | POOLED | rf | 0.499 [0.48,0.52] | 0.494 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G2 | sig | POOLED | rf | 0.501 [0.49,0.51] | 0.494 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G5 | sig | POOLED | stack | 0.500 [0.49,0.51] | 0.493 [0.48,0.51] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G5 | sig | POOLED | gbt3 | 0.505 [0.49,0.52] | 0.493 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G5 | sig | POOLED/HM | stack | 0.502 [0.49,0.52] | 0.493 [0.47,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-ALLG+BASE | sig | ASIA | logit2 | 0.494 [0.47,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G2 | sig | ASIA | stack | 0.492 [0.47,0.51] | 0.492 [0.47,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-ALLG+BASE | sig | POOLED | logit2 | 0.511 [0.49,0.53] | 0.492 [0.47,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G4 | sig | LONDON | stack | 0.504 [0.48,0.52] | 0.491 [0.46,0.52] | - | - | - | ok | - | - | - | - |  | WF-only (dead) |
| G-sigu-G5 | sig | POOLED/HM | stack | 0.493 [0.48,0.51] | 0.489 [0.47,0.51] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G1 | sig | LONDON | logit2 | 0.497 [0.48,0.52] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | ASIA | rf | 0.495 [0.47,0.52] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G6 | sig | ASIA | rf | 0.501 [0.48,0.52] | 0.489 [0.46,0.51] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-ALLG+BASE | sig | LONDON | logit2 | 0.495 [0.47,0.51] | 0.489 [0.46,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G6+BASE | sig | ASIA | stack | 0.509 [0.49,0.53] | 0.489 [0.46,0.52] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| G-sigu-GALL | sig | LONDON | gbt3 | 0.504 [0.48,0.53] | 0.488 [0.46,0.51] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu-G6 | sig | LONDON | gbt3 | 0.500 [0.48,0.52] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3 | sig | POOLED/HM | stack | 0.488 [0.47,0.51] | 0.487 [0.47,0.51] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G4 | sig | POOLED/ST | stack | 0.496 [0.48,0.51] | 0.486 [0.47,0.50] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL+BASE | sig | ASIA | stack | 0.499 [0.47,0.53] | 0.486 [0.45,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G2 | sig | LONDON | rf | 0.506 [0.48,0.53] | 0.485 [0.46,0.51] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu-G6 | sig | ASIA | rf | 0.495 [0.47,0.52] | 0.485 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G5 | sig | ASIA | gbt3 | 0.502 [0.48,0.52] | 0.485 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G6 | sig | LONDON | logit2 | 0.506 [0.48,0.53] | 0.484 [0.46,0.51] | - | - | - | ok | - | - | - | - |  | WF-only (dead) |
| G-sigu-G1 | sig | ASIA | gbt3 | 0.505 [0.48,0.53] | 0.484 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-GALL+BASE | sig | LONDON | logit2 | 0.497 [0.47,0.52] | 0.483 [0.46,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G5 | sig | POOLED | stack | 0.495 [0.48,0.51] | 0.483 [0.47,0.50] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G1 | sig | LONDON | gbt3 | 0.498 [0.48,0.52] | 0.483 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3 | sig | POOLED | gbt3 | 0.488 [0.47,0.50] | 0.483 [0.46,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G2 | sig | POOLED/HM | rf | 0.494 [0.48,0.51] | 0.482 [0.46,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-ALLG+BASE | sig | ASIA | logit2 | 0.494 [0.47,0.51] | 0.482 [0.45,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G6+BASE | sig | ASIA | logit2 | 0.490 [0.47,0.51] | 0.482 [0.46,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G2 | sig | LONDON | rf | 0.499 [0.48,0.52] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G1 | sig | POOLED | gbt3 | 0.489 [0.47,0.50] | 0.479 [0.46,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G5 | sig | NY | stack | 0.501 [0.48,0.52] | 0.478 [0.46,0.50] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G6+BASE | sig | LONDON | rf | 0.495 [0.47,0.51] | 0.477 [0.45,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G5 | sig | LONDON | logit2 | 0.483 [0.46,0.50] | 0.477 [0.46,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G5 | sig | POOLED/ST | stack | 0.490 [0.48,0.50] | 0.476 [0.46,0.49] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-BASE | sig | LONDON | rf | 0.490 [0.47,0.51] | 0.475 [0.44,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu-G3+BASE | sig | LONDON | rf | 0.490 [0.47,0.51] | 0.475 [0.44,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu-G8+BASE | sig | LONDON | rf | 0.486 [0.46,0.51] | 0.475 [0.44,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- G-sigu-ALLG+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G1 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G2 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G3 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G3+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G4 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G5 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G6 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G6+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G7 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G8 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G8+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-GALL -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-GALL+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-ALLG+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-ALLG+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G1 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G1 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G2 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G2 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G3 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G3+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G3+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G4 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G4 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G5 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G5 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G6 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G6+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G6+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G7 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G7 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G8 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-G8+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-G8+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-GALL -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu-GALL+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu-GALL+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
