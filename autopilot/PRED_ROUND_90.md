# PRED ROUND 90 - block G round 7 - G-regime-sequence-unlocked-G

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.562 [0.54,0.58]
Gap to FOUND: 0.118 AUC, 5 of 5 economic conditions short.
not found - short by 0.118 AUC and 5 of 5 economic conditions

prereg 4d7e6aabbed2ce9a8f996357310ed3940e53deeef933466ed5805b6e4f3604e1 ; trials added 500 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': True, 'note': 'same feature functions as locked stores (audits 0 mismatches; first G1-G7 audit had 266 mismatches from HMM param-file mismatch, fixed); taken-subset sigu features reproduce the locked-store features exactly (max rel diff 0 for G1,G2,G4,G5,G6,G7)'} ; holdout scored True ; feature store ['l2vast/pred/store/G9_sigu.parquet', 'l2vast/pred/store/G10_sigu.parquet', 'l2vast/pred/store/G12_sigu.parquet', 'l2vast/pred/store/G13_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G-sigu7-G13 | sig | NY | rf | 0.551 [0.54,0.57] | 0.562 [0.54,0.58] | - | - | - | N | - | - | - | - |  | short by 0.118 AUC, 5 of 5 econ |
| G-sigu7-G9 | sig | NY | rf | 0.540 [0.52,0.56] | 0.559 [0.54,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F | sig | NY | logit2 | 0.552 [0.54,0.57] | 0.556 [0.53,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-ALLG13+BASE | sig | NY | stack | 0.550 [0.53,0.57] | 0.553 [0.53,0.58] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G4F+BASE | sig | NY | logit2 | 0.550 [0.53,0.57] | 0.551 [0.53,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G10 | sig | NY | gbt3 | 0.546 [0.53,0.56] | 0.542 [0.52,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G13 | sig | POOLED/ST | rf | 0.538 [0.53,0.55] | 0.542 [0.53,0.55] | - | - | - | N | - | - | - | - |  | short by 0.138 AUC, 5 of 5 econ |
| G-sigu7-G9 | sig | POOLED/ST | rf | 0.533 [0.52,0.54] | 0.535 [0.52,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G13 | sig | POOLED | rf | 0.531 [0.52,0.54] | 0.532 [0.52,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G10 | sig | POOLED/ST | rf | 0.531 [0.52,0.54] | 0.530 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G13 | sig | NY | rf | 0.518 [0.50,0.53] | 0.529 [0.51,0.55] | - | - | - | N | - | - | - | - |  | promising: short by 0.151 AUC, 5 of 5 econ |
| G-sigu7-G9 | sig | POOLED | rf | 0.523 [0.51,0.53] | 0.527 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F | sig | POOLED/ST | logit2 | 0.530 [0.52,0.54] | 0.527 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G13 | sig | POOLED/ST | rf | 0.521 [0.51,0.53] | 0.526 [0.51,0.54] | - | - | - | N | - | - | - | - |  | promising: short by 0.154 AUC, 5 of 5 econ |
| G-sigu7-ALLG13+BASE | sig | POOLED/ST | gbt3 | 0.529 [0.52,0.54] | 0.526 [0.51,0.55] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-ALLG13+BASE | sig | NY | logit2 | 0.525 [0.51,0.54] | 0.525 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| G-sigu7-G4F+BASE | sig | POOLED/ST | gbt3 | 0.525 [0.51,0.54] | 0.525 [0.51,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-ALLG13+BASE | sig | POOLED | gbt3 | 0.528 [0.52,0.54] | 0.525 [0.51,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G4F+BASE | sig | NY | logit2 | 0.528 [0.51,0.55] | 0.525 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| G-sigu7-G10 | sig | POOLED | rf | 0.525 [0.52,0.53] | 0.524 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G12 | sig | POOLED | gbt3 | 0.521 [0.51,0.53] | 0.522 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G12 | sig | NY | stack | 0.521 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-ALLG13+BASE | sig | LONDON | rf | 0.516 [0.49,0.54] | 0.522 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| G-sigu7-G4F | sig | POOLED | logit2 | 0.526 [0.51,0.54] | 0.522 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-ALLG13+BASE | sig | POOLED/HM | logit2 | 0.528 [0.51,0.54] | 0.521 [0.50,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G12 | sig | POOLED/ST | gbt3 | 0.524 [0.51,0.54] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G13 | sig | POOLED | rf | 0.515 [0.51,0.53] | 0.519 [0.51,0.53] | - | - | - | N | - | - | - | - |  | promising: short by 0.161 AUC, 5 of 5 econ |
| G-sigu7-G4F+BASE | sig | POOLED | gbt3 | 0.521 [0.51,0.53] | 0.519 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G13 | sig | POOLED/HM | rf | 0.520 [0.50,0.53] | 0.517 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F | sig | NY | logit2 | 0.509 [0.49,0.53] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| G-sigu7-G4F+BASE | sig | POOLED/HM | logit2 | 0.524 [0.51,0.54] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| G-sigu7-G10 | sig | POOLED/ST | rf | 0.506 [0.49,0.52] | 0.517 [0.50,0.54] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| G-sigu7-G9 | sig | POOLED/HM | rf | 0.511 [0.50,0.52] | 0.515 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F+BASE | sig | POOLED | logit2 | 0.518 [0.51,0.53] | 0.515 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| G-sigu7-ALLG13+BASE | sig | POOLED/HM | logit2 | 0.516 [0.50,0.53] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| G-sigu7-G9 | sig | POOLED | rf | 0.507 [0.49,0.53] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G12 | sig | POOLED/HM | stack | 0.509 [0.49,0.52] | 0.514 [0.49,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-ALLG13+BASE | sig | POOLED | logit2 | 0.513 [0.50,0.53] | 0.514 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| G-sigu7-G4F | sig | POOLED/HM | logit2 | 0.520 [0.50,0.53] | 0.514 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-ALLG13+BASE | sig | POOLED/ST | logit2 | 0.510 [0.49,0.52] | 0.514 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| G-sigu7-G4F+BASE | sig | POOLED/ST | logit2 | 0.514 [0.50,0.53] | 0.514 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| G-sigu7-G10 | sig | POOLED/HM | gbt3 | 0.517 [0.50,0.53] | 0.514 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G12 | sig | POOLED/HM | rf | 0.512 [0.50,0.53] | 0.513 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| G-sigu7-G4F+BASE | sig | POOLED/HM | logit2 | 0.519 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G4F | sig | POOLED/ST | logit2 | 0.512 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| G-sigu7-G10 | sig | POOLED | logit2 | 0.516 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G12 | sig | POOLED | stack | 0.515 [0.50,0.53] | 0.511 [0.48,0.54] | - | - | - | ok | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| G-sigu7-G4F+BASE | sig | POOLED | stack | 0.513 [0.50,0.53] | 0.511 [0.48,0.53] | - | - | - | ok | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| G-sigu7-G12 | sig | POOLED | gbt3 | 0.513 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G9 | sig | ASIA | stack | 0.502 [0.48,0.52] | 0.509 [0.48,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F | sig | POOLED | logit2 | 0.508 [0.50,0.52] | 0.508 [0.49,0.52] | - | - | - | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| G-sigu7-G12 | sig | ASIA | gbt3 | 0.508 [0.49,0.53] | 0.508 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F+BASE | sig | LONDON | gbt3 | 0.503 [0.48,0.53] | 0.508 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| G-sigu7-G13 | sig | LONDON | rf | 0.511 [0.49,0.53] | 0.508 [0.48,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu7-ALLG13+BASE | sig | POOLED | logit2 | 0.505 [0.49,0.52] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| G-sigu7-G9 | sig | NY | gbt3 | 0.501 [0.48,0.52] | 0.506 [0.48,0.52] | - | - | - | N | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| G-sigu7-G10 | sig | ASIA | stack | 0.504 [0.48,0.52] | 0.506 [0.48,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G13 | sig | LONDON | rf | 0.510 [0.49,0.53] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| G-sigu7-G13 | sig | ASIA | gbt3 | 0.507 [0.49,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu7-G10 | sig | POOLED | gbt3 | 0.509 [0.49,0.52] | 0.504 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G13 | sig | POOLED | rf | 0.509 [0.49,0.53] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G10 | sig | ASIA | rf | 0.509 [0.49,0.53] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu7-ALLG13+BASE | sig | ASIA | stack | 0.504 [0.48,0.53] | 0.503 [0.47,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G13 | sig | POOLED | stack | 0.504 [0.48,0.52] | 0.502 [0.48,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F | sig | POOLED/HM | logit2 | 0.503 [0.49,0.52] | 0.502 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F | sig | ASIA | stack | 0.503 [0.48,0.52] | 0.499 [0.47,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G9 | sig | POOLED/HM | stack | 0.504 [0.48,0.52] | 0.499 [0.47,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-ALLG13+BASE | sig | ASIA | gbt3 | 0.507 [0.48,0.53] | 0.499 [0.47,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G4F | sig | POOLED | logit2 | 0.501 [0.48,0.52] | 0.498 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-ALLG13+BASE | sig | LONDON | gbt3 | 0.503 [0.48,0.53] | 0.498 [0.47,0.53] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| G-sigu7-G10 | sig | POOLED/HM | gbt3 | 0.513 [0.50,0.53] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu7-G10 | sig | POOLED | gbt3 | 0.501 [0.49,0.51] | 0.498 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-ALLG13+BASE | sig | POOLED | logit2 | 0.514 [0.50,0.53] | 0.496 [0.48,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G13 | sig | ASIA | rf | 0.499 [0.48,0.52] | 0.496 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G12 | sig | ASIA | gbt3 | 0.502 [0.48,0.52] | 0.495 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G12 | sig | POOLED | stack | 0.501 [0.49,0.51] | 0.495 [0.48,0.51] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G12 | sig | LONDON | rf | 0.502 [0.48,0.52] | 0.495 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F+BASE | sig | ASIA | stack | 0.504 [0.48,0.53] | 0.494 [0.47,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G13 | sig | POOLED/HM | gbt3 | 0.500 [0.48,0.52] | 0.493 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F | sig | ASIA | stack | 0.500 [0.48,0.52] | 0.492 [0.46,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F | sig | LONDON | gbt3 | 0.502 [0.48,0.52] | 0.492 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F | sig | POOLED | logit2 | 0.499 [0.48,0.52] | 0.492 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F+BASE | sig | POOLED | rf | 0.505 [0.49,0.52] | 0.491 [0.47,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G12 | sig | NY | stack | 0.501 [0.48,0.52] | 0.491 [0.47,0.51] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G9 | sig | POOLED | stack | 0.501 [0.49,0.51] | 0.491 [0.47,0.51] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G10 | sig | LONDON | gbt3 | 0.500 [0.48,0.52] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G10 | sig | LONDON | logit2 | 0.505 [0.48,0.53] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu7-G9 | sig | ASIA | stack | 0.507 [0.48,0.53] | 0.489 [0.46,0.52] | - | - | - | ok | - | - | - | - |  | WF-only (dead) |
| G-sigu7-G10 | sig | NY | gbt3 | 0.493 [0.48,0.51] | 0.488 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G12 | sig | POOLED/ST | stack | 0.498 [0.49,0.51] | 0.487 [0.47,0.50] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G9 | sig | LONDON | stack | 0.511 [0.49,0.53] | 0.485 [0.46,0.51] | - | - | - | ok | - | - | - | - |  | WF-only (dead) |
| G-sigu7-G9 | sig | POOLED/ST | stack | 0.499 [0.48,0.51] | 0.484 [0.47,0.50] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F | sig | LONDON | gbt3 | 0.512 [0.49,0.53] | 0.484 [0.46,0.51] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu7-G9 | sig | POOLED | stack | 0.496 [0.48,0.52] | 0.484 [0.45,0.51] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| G-sigu7-G4F+BASE | sig | ASIA | gbt3 | 0.494 [0.47,0.52] | 0.483 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| G-sigu7-G9 | sig | LONDON | rf | 0.502 [0.48,0.52] | 0.481 [0.45,0.51] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| G-sigu7-G4F+BASE | sig | LONDON | gbt3 | 0.504 [0.48,0.53] | 0.476 [0.44,0.51] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| G-sigu7-G12 | sig | LONDON | logit2 | 0.486 [0.46,0.51] | 0.471 [0.45,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |

One-sentence notes:
- G-sigu7-ALLG13+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G10 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G12 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G13 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G4F -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G4F+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G9 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-ALLG13+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-ALLG13+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G10 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G10 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G12 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G12 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G13 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G13 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G4F -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G4F+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G4F+BASE -1 POOLED: sub-metric TAKEN = signals taken by the locked system
- G-sigu7-G9 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 ASIA: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 LONDON: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 NY: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 POOLED: no gate economics (WF-PRE AUC below R0u+0.02)
- G-sigu7-G9 -1 POOLED: sub-metric TAKEN = signals taken by the locked system
