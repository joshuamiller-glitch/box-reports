# PRED ROUND 91 - block X5 round 7 - X41+X42+X44+X45+X46-union

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.548 [0.50,0.59]
Gap to FOUND: 0.132 AUC, 5 of 5 economic conditions short.
not found - short by 0.132 AUC and 5 of 5 economic conditions

prereg 530464ae5ac55b6bb6453fd7585f5cff4e64158165c5db15f80f600361e56e6d ; trials added 120 ; truncation audit {'decisions': 255, 'checks': 10605, 'mismatches': 0} ; holdout scored True ; feature store ['l2vast/pred/store/X41_sigu.parquet', 'l2vast/pred/store/X42_sigu.parquet', 'l2vast/pred/store/X44_sigu.parquet', 'l2vast/pred/store/X45_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X45-strategy-hit-rate | sig | ASIA/HM | M45R:stack | 0.538 [0.51,0.57] | 0.548 [0.50,0.59] | - | - | - | N | - | - | - | - |  | short by 0.132 AUC, 5 of 5 econ |
| X44-seasonal-te | sig | ASIA/HM | M44R:stack | 0.523 [0.49,0.56] | 0.543 [0.51,0.58] | - | - | - | N | - | - | - | - |  | short by 0.137 AUC, 5 of 5 econ |
| X44-seasonal-te | sig | ASIA | M44R:stack | 0.517 [0.49,0.54] | 0.534 [0.51,0.56] | - | - | - | N | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| X42-volume-profile | sig | LONDON/HM | M42T:stack | 0.498 [0.47,0.52] | 0.531 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.149 AUC, 5 of 5 econ |
| X45-strategy-hit-rate | sig | NY/HM | M45R:stack | 0.519 [0.49,0.55] | 0.530 [0.49,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | LONDON/ST | M42R:stack | 0.496 [0.47,0.52] | 0.529 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| X44-seasonal-te | sig | LONDON/HM | M44T:stack | 0.511 [0.48,0.54] | 0.529 [0.48,0.57] | - | - | - | N | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| X42-volume-profile | sig | ASIA/HM | M42R:stack | 0.501 [0.47,0.54] | 0.528 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| X44-seasonal-te | sig | ASIA/ST | M44R:stack | 0.512 [0.49,0.54] | 0.528 [0.49,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | POOLED/HM | M45R:stack | 0.516 [0.50,0.53] | 0.526 [0.50,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | ASIA | M45R:stack | 0.522 [0.50,0.55] | 0.524 [0.49,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | LONDON/HM | M41T:stack | 0.496 [0.47,0.52] | 0.524 [0.48,0.57] | - | - | - | N | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| X41-cross-asset | sig | ASIA/HM | M41R:stack | 0.497 [0.46,0.53] | 0.523 [0.48,0.56] | - | - | - | N | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| X44-seasonal-te | sig | ASIA/HM | M44T:stack | 0.511 [0.48,0.55] | 0.523 [0.48,0.57] | - | - | - | N | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| X46-union | sig | ASIA/ST | MVR:stack | 0.521 [0.49,0.55] | 0.523 [0.49,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | ASIA | M42R:stack | 0.505 [0.48,0.53] | 0.522 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | ASIA | MVR:stack | 0.514 [0.49,0.54] | 0.520 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | ASIA/HM | M45T:stack | 0.516 [0.48,0.55] | 0.520 [0.48,0.56] | - | - | - | N | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| X46-union | sig | ASIA/HM | MVR:stack | 0.506 [0.48,0.53] | 0.520 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | LONDON | M42R:stack | 0.492 [0.47,0.51] | 0.519 [0.49,0.55] | - | - | - | N | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| X46-union | sig | POOLED/HM | MVR:stack | 0.510 [0.49,0.53] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | LONDON | M42T:stack | 0.500 [0.48,0.52] | 0.517 [0.49,0.55] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| X45-strategy-hit-rate | sig | NY | M45R:stack | 0.517 [0.50,0.54] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | ASIA/ST | M42R:stack | 0.509 [0.48,0.54] | 0.516 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | POOLED/HM | M44R:stack | 0.509 [0.49,0.53] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | ASIA | M45T:stack | 0.509 [0.48,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| X44-seasonal-te | sig | NY/HM | M44R:stack | 0.514 [0.49,0.54] | 0.514 [0.47,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | ASIA | M44T:stack | 0.511 [0.48,0.54] | 0.514 [0.48,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X46-union | sig | NY/HM | MVR:stack | 0.520 [0.49,0.55] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | POOLED/HM | M42R:stack | 0.505 [0.49,0.52] | 0.513 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | POOLED/HM | M42T:stack | 0.502 [0.49,0.52] | 0.513 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| X41-cross-asset | sig | ASIA | M41R:stack | 0.502 [0.48,0.52] | 0.512 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | POOLED | M42R:stack | 0.508 [0.49,0.52] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | POOLED | M45R:stack | 0.510 [0.50,0.52] | 0.511 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | ASIA/ST | M45T:stack | 0.503 [0.48,0.53] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | POOLED/ST | M42R:stack | 0.509 [0.50,0.52] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | NY/HM | M42T:stack | 0.508 [0.48,0.53] | 0.509 [0.47,0.55] | - | - | - | N | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| X44-seasonal-te | sig | POOLED | M44R:stack | 0.511 [0.50,0.52] | 0.509 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | NY/ST | M45R:stack | 0.515 [0.49,0.53] | 0.508 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | LONDON/HM | M42R:stack | 0.488 [0.46,0.52] | 0.507 [0.47,0.55] | - | - | - | N | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| X44-seasonal-te | sig | POOLED/HM | M44T:stack | 0.503 [0.48,0.52] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| X46-union | sig | POOLED | MVR:stack | 0.507 [0.50,0.52] | 0.507 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | NY/HM | M42R:stack | 0.514 [0.48,0.54] | 0.506 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | LONDON | M44T:stack | 0.495 [0.47,0.52] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | ASIA/ST | MVT:stack | 0.521 [0.49,0.55] | 0.506 [0.46,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | ASIA/ST | M44T:stack | 0.510 [0.48,0.54] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | LONDON/ST | M42T:stack | 0.502 [0.48,0.53] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X41-cross-asset | sig | NY/ST | M41R:stack | 0.513 [0.49,0.53] | 0.505 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | ASIA/ST | M45R:stack | 0.507 [0.48,0.54] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | POOLED/ST | M44R:stack | 0.512 [0.50,0.53] | 0.504 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | ASIA/HM | M41T:stack | 0.503 [0.47,0.53] | 0.504 [0.46,0.55] | - | - | - | N | - | - | - | - |  | short by 0.176 AUC, 5 of 5 econ |
| X42-volume-profile | sig | POOLED | M42T:stack | 0.500 [0.49,0.51] | 0.504 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | LONDON/HM | MVR:stack | 0.483 [0.45,0.51] | 0.504 [0.46,0.54] | - | - | - | N | - | - | - | - |  | short by 0.176 AUC, 5 of 5 econ |
| X41-cross-asset | sig | NY | M41R:stack | 0.512 [0.49,0.53] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | LONDON | M41T:stack | 0.487 [0.46,0.51] | 0.503 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | ASIA/ST | M41R:stack | 0.508 [0.48,0.54] | 0.503 [0.46,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | NY | MVR:stack | 0.513 [0.50,0.53] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | NY | M42T:stack | 0.502 [0.48,0.52] | 0.502 [0.48,0.52] | - | - | - | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| X45-strategy-hit-rate | sig | LONDON/ST | M45T:stack | 0.495 [0.47,0.52] | 0.502 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | ASIA/HM | M42T:stack | 0.499 [0.47,0.53] | 0.502 [0.46,0.54] | - | - | - | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| X44-seasonal-te | sig | LONDON/ST | M44R:stack | 0.493 [0.47,0.52] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | POOLED/HM | M45T:stack | 0.496 [0.48,0.51] | 0.501 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | POOLED/ST | M45R:stack | 0.506 [0.49,0.52] | 0.501 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | POOLED/HM | M41T:stack | 0.499 [0.48,0.51] | 0.500 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | POOLED/HM | M41R:stack | 0.492 [0.48,0.51] | 0.500 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | NY/HM | M41R:stack | 0.509 [0.48,0.53] | 0.500 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | NY | M44R:stack | 0.515 [0.50,0.53] | 0.499 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | POOLED | M41R:stack | 0.498 [0.49,0.51] | 0.499 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | POOLED/ST | MVR:stack | 0.505 [0.49,0.52] | 0.499 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | NY | M42R:stack | 0.512 [0.49,0.53] | 0.498 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | POOLED/ST | M41R:stack | 0.503 [0.49,0.51] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | NY/ST | M42T:stack | 0.498 [0.48,0.52] | 0.497 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | ASIA | M41T:stack | 0.498 [0.48,0.52] | 0.497 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | LONDON | M45T:stack | 0.486 [0.46,0.51] | 0.497 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | ASIA | MVT:stack | 0.509 [0.48,0.53] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X42-volume-profile | sig | POOLED/ST | M42T:stack | 0.498 [0.48,0.51] | 0.496 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | LONDON/ST | MVT:stack | 0.491 [0.46,0.52] | 0.496 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | POOLED/ST | MVT:stack | 0.502 [0.49,0.52] | 0.496 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | NY/ST | MVR:stack | 0.507 [0.49,0.53] | 0.494 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | POOLED | M44T:stack | 0.499 [0.48,0.51] | 0.494 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | NY/ST | M42R:stack | 0.511 [0.49,0.53] | 0.493 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | POOLED | M41T:stack | 0.491 [0.48,0.50] | 0.493 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X42-volume-profile | sig | ASIA | M42T:stack | 0.497 [0.47,0.52] | 0.493 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | POOLED | M45T:stack | 0.496 [0.48,0.51] | 0.493 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | LONDON | M44R:stack | 0.483 [0.46,0.51] | 0.493 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | ASIA/ST | M41T:stack | 0.494 [0.47,0.52] | 0.492 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | LONDON/HM | M45R:stack | 0.478 [0.45,0.51] | 0.491 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | NY/ST | MVT:stack | 0.499 [0.48,0.52] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | LONDON/HM | M45T:stack | 0.475 [0.45,0.50] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | LONDON | MVR:stack | 0.480 [0.46,0.50] | 0.490 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | NY/ST | M44R:stack | 0.515 [0.50,0.53] | 0.490 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | POOLED | MVT:stack | 0.496 [0.48,0.51] | 0.489 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | POOLED/ST | M41T:stack | 0.485 [0.47,0.50] | 0.488 [0.47,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | LONDON/ST | M44T:stack | 0.482 [0.46,0.50] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | NY/HM | M45T:stack | 0.494 [0.47,0.52] | 0.488 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | NY/ST | M41T:stack | 0.485 [0.46,0.51] | 0.487 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | LONDON | MVT:stack | 0.481 [0.46,0.50] | 0.487 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | POOLED/ST | M45T:stack | 0.496 [0.48,0.51] | 0.487 [0.47,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | LONDON/ST | M41T:stack | 0.479 [0.45,0.51] | 0.486 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | ASIA/HM | MVT:stack | 0.495 [0.46,0.53] | 0.486 [0.45,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X42-volume-profile | sig | ASIA/ST | M42T:stack | 0.494 [0.46,0.52] | 0.485 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | NY | MVT:stack | 0.497 [0.48,0.52] | 0.485 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | NY | M41T:stack | 0.489 [0.47,0.51] | 0.484 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | POOLED/ST | M44T:stack | 0.496 [0.48,0.51] | 0.484 [0.47,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | LONDON | M45R:stack | 0.478 [0.45,0.50] | 0.482 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | LONDON/HM | M44R:stack | 0.471 [0.44,0.50] | 0.481 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | LONDON/ST | MVR:stack | 0.478 [0.46,0.50] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | LONDON/ST | M41R:stack | 0.473 [0.45,0.50] | 0.479 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | NY/HM | M41T:stack | 0.497 [0.47,0.52] | 0.479 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | POOLED/HM | MVT:stack | 0.487 [0.47,0.50] | 0.478 [0.45,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | LONDON | M41R:stack | 0.465 [0.44,0.49] | 0.477 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | LONDON/HM | MVT:stack | 0.468 [0.43,0.50] | 0.476 [0.43,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | NY/HM | M44T:stack | 0.490 [0.47,0.52] | 0.476 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | LONDON/ST | M45R:stack | 0.478 [0.45,0.51] | 0.475 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X41-cross-asset | sig | LONDON/HM | M41R:stack | 0.454 [0.42,0.49] | 0.475 [0.43,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X46-union | sig | NY/HM | MVT:stack | 0.493 [0.47,0.52] | 0.475 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | NY | M45T:stack | 0.492 [0.47,0.51] | 0.473 [0.45,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | NY | M44T:stack | 0.495 [0.48,0.51] | 0.472 [0.45,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X44-seasonal-te | sig | NY/ST | M44T:stack | 0.498 [0.47,0.52] | 0.469 [0.44,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X45-strategy-hit-rate | sig | NY/ST | M45T:stack | 0.492 [0.47,0.51] | 0.464 [0.44,0.49] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |

One-sentence notes:
- X41-cross-asset -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X41-cross-asset -1 ASIA: unlocked
- X41-cross-asset -1 LONDON: unlocked
- X41-cross-asset -1 NY: unlocked
- X41-cross-asset -1 POOLED: unlocked
- X41-cross-asset -1 ASIA: unlocked
- X41-cross-asset -1 LONDON: unlocked
- X41-cross-asset -1 NY: unlocked
- X41-cross-asset -1 POOLED: unlocked
- X41-cross-asset -1 ASIA: unlocked
- X41-cross-asset -1 LONDON: unlocked
- X41-cross-asset -1 NY: unlocked
- X41-cross-asset -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X41-cross-asset -1 ASIA: unlocked
- X41-cross-asset -1 LONDON: unlocked
- X41-cross-asset -1 NY: unlocked
- X41-cross-asset -1 POOLED: unlocked
- X41-cross-asset -1 ASIA: unlocked
- X41-cross-asset -1 LONDON: unlocked
- X41-cross-asset -1 NY: unlocked
- X41-cross-asset -1 POOLED: unlocked
- X41-cross-asset -1 ASIA: unlocked
- X41-cross-asset -1 LONDON: unlocked
- X41-cross-asset -1 NY: unlocked
- X42-volume-profile -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X42-volume-profile -1 ASIA: unlocked
- X42-volume-profile -1 LONDON: unlocked
- X42-volume-profile -1 NY: unlocked
- X42-volume-profile -1 POOLED: unlocked
- X42-volume-profile -1 ASIA: unlocked
- X42-volume-profile -1 LONDON: unlocked
- X42-volume-profile -1 NY: unlocked
- X42-volume-profile -1 POOLED: unlocked
- X42-volume-profile -1 ASIA: unlocked
- X42-volume-profile -1 LONDON: unlocked
- X42-volume-profile -1 NY: unlocked
- X42-volume-profile -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X42-volume-profile -1 ASIA: unlocked
- X42-volume-profile -1 LONDON: unlocked
- X42-volume-profile -1 NY: unlocked
- X42-volume-profile -1 POOLED: unlocked
- X42-volume-profile -1 ASIA: unlocked
- X42-volume-profile -1 LONDON: unlocked
- X42-volume-profile -1 NY: unlocked
- X42-volume-profile -1 POOLED: unlocked
- X42-volume-profile -1 ASIA: unlocked
- X42-volume-profile -1 LONDON: unlocked
- X42-volume-profile -1 NY: unlocked
- X44-seasonal-te -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X44-seasonal-te -1 ASIA: unlocked
- X44-seasonal-te -1 LONDON: unlocked
- X44-seasonal-te -1 NY: unlocked
- X44-seasonal-te -1 POOLED: unlocked
- X44-seasonal-te -1 ASIA: unlocked
- X44-seasonal-te -1 LONDON: unlocked
- X44-seasonal-te -1 NY: unlocked
- X44-seasonal-te -1 POOLED: unlocked
- X44-seasonal-te -1 ASIA: unlocked
- X44-seasonal-te -1 LONDON: unlocked
- X44-seasonal-te -1 NY: unlocked
- X44-seasonal-te -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X44-seasonal-te -1 ASIA: unlocked
- X44-seasonal-te -1 LONDON: unlocked
- X44-seasonal-te -1 NY: unlocked
- X44-seasonal-te -1 POOLED: unlocked
- X44-seasonal-te -1 ASIA: unlocked
- X44-seasonal-te -1 LONDON: unlocked
- X44-seasonal-te -1 NY: unlocked
- X44-seasonal-te -1 POOLED: unlocked
- X44-seasonal-te -1 ASIA: unlocked
- X44-seasonal-te -1 LONDON: unlocked
- X44-seasonal-te -1 NY: unlocked
- X45-strategy-hit-rate -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X45-strategy-hit-rate -1 ASIA: unlocked
- X45-strategy-hit-rate -1 LONDON: unlocked
- X45-strategy-hit-rate -1 NY: unlocked
- X45-strategy-hit-rate -1 POOLED: unlocked
- X45-strategy-hit-rate -1 ASIA: unlocked
- X45-strategy-hit-rate -1 LONDON: unlocked
- X45-strategy-hit-rate -1 NY: unlocked
- X45-strategy-hit-rate -1 POOLED: unlocked
- X45-strategy-hit-rate -1 ASIA: unlocked
- X45-strategy-hit-rate -1 LONDON: unlocked
- X45-strategy-hit-rate -1 NY: unlocked
- X45-strategy-hit-rate -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X45-strategy-hit-rate -1 ASIA: unlocked
- X45-strategy-hit-rate -1 LONDON: unlocked
- X45-strategy-hit-rate -1 NY: unlocked
- X45-strategy-hit-rate -1 POOLED: unlocked
- X45-strategy-hit-rate -1 ASIA: unlocked
- X45-strategy-hit-rate -1 LONDON: unlocked
- X45-strategy-hit-rate -1 NY: unlocked
- X45-strategy-hit-rate -1 POOLED: unlocked
- X45-strategy-hit-rate -1 ASIA: unlocked
- X45-strategy-hit-rate -1 LONDON: unlocked
- X45-strategy-hit-rate -1 NY: unlocked
- X46-union -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X46-union -1 ASIA: unlocked
- X46-union -1 LONDON: unlocked
- X46-union -1 NY: unlocked
- X46-union -1 POOLED: unlocked
- X46-union -1 ASIA: unlocked
- X46-union -1 LONDON: unlocked
- X46-union -1 NY: unlocked
- X46-union -1 POOLED: unlocked
- X46-union -1 ASIA: unlocked
- X46-union -1 LONDON: unlocked
- X46-union -1 NY: unlocked
- X46-union -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X46-union -1 ASIA: unlocked
- X46-union -1 LONDON: unlocked
- X46-union -1 NY: unlocked
- X46-union -1 POOLED: unlocked
- X46-union -1 ASIA: unlocked
- X46-union -1 LONDON: unlocked
- X46-union -1 NY: unlocked
- X46-union -1 POOLED: unlocked
- X46-union -1 ASIA: unlocked
- X46-union -1 LONDON: unlocked
- X46-union -1 NY: unlocked
