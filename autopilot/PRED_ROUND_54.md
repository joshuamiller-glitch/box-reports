# PRED ROUND 54 - block X5 round 6 - X31+X32+X33+X34+X35+X22-trade-geometry+X36-micro-union+X37-micro-plus-base+X27-signal-flow

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.560 [0.53,0.60]
Gap to FOUND: 0.120 AUC, 5 of 5 economic conditions short.
not found - short by 0.120 AUC and 5 of 5 economic conditions

prereg 8e40348eba2dc03c8e34a50f2d801113d70ee17037503a62f03c9e42066ad062 ; trials added 216 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'audit/X5_microu_trunc.json (unlocked signals)'} ; holdout scored True ; feature store ['l2vast/pred/store/X31_sigu.parquet', 'l2vast/pred/store/X32_sigu.parquet', 'l2vast/pred/store/X33_sigu.parquet', 'l2vast/pred/store/X34_sigu.parquet', 'l2vast/pred/store/X35_sigu.parquet', 'l2vast/pred/store/X22_geo_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X22-trade-geometry | sig | NY/HM | M22R:stack | 0.546 [0.52,0.57] | 0.560 [0.53,0.60] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | NY/HM | MBR:stack | 0.535 [0.51,0.56] | 0.552 [0.52,0.59] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X22-trade-geometry | sig | NY | M22R:stack | 0.543 [0.53,0.56] | 0.551 [0.53,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | LONDON/HM | M31T:stack | 0.525 [0.50,0.55] | 0.550 [0.51,0.58] | - | - | - | N | - | - | - | - |  | short by 0.130 AUC, 5 of 5 econ |
| X35-whipsaw-neighbours | sig | NY | M35R:stack | 0.536 [0.52,0.55] | 0.548 [0.52,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | NY/HM | M35R:stack | 0.537 [0.51,0.56] | 0.547 [0.51,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | NY/ST | M35R:stack | 0.535 [0.52,0.55] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | ASIA/HM | M35R:stack | 0.524 [0.50,0.55] | 0.545 [0.51,0.58] | - | - | - | N | - | - | - | - |  | short by 0.135 AUC, 5 of 5 econ |
| X32-book-depth | sig | ASIA/ST | M32R:stack | 0.526 [0.50,0.56] | 0.545 [0.51,0.58] | - | - | - | N | - | - | - | - |  | short by 0.135 AUC, 5 of 5 econ |
| X36-micro-union | sig | NY/HM | MUR:stack | 0.537 [0.51,0.56] | 0.544 [0.51,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | NY/HM | M33R:stack | 0.547 [0.52,0.57] | 0.544 [0.51,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | NY/ST | M22R:stack | 0.540 [0.52,0.56] | 0.543 [0.51,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | LONDON/HM | M33T:stack | 0.510 [0.47,0.54] | 0.542 [0.50,0.58] | - | - | - | N | - | - | - | - |  | short by 0.138 AUC, 5 of 5 econ |
| X37-micro-plus-base | sig | NY | MBR:stack | 0.537 [0.52,0.55] | 0.542 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X34-level-proximity | sig | NY/HM | M34R:stack | 0.538 [0.51,0.56] | 0.542 [0.51,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | NY | M34R:stack | 0.541 [0.52,0.56] | 0.540 [0.51,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | NY/ST | M34R:stack | 0.542 [0.52,0.56] | 0.538 [0.51,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | NY | MUR:stack | 0.534 [0.52,0.55] | 0.536 [0.51,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | NY/HM | M32R:stack | 0.529 [0.50,0.56] | 0.535 [0.50,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | ASIA/HM | MUR:stack | 0.540 [0.51,0.57] | 0.535 [0.49,0.58] | - | - | - | N | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| X34-level-proximity | sig | ASIA/HM | M34R:stack | 0.522 [0.50,0.55] | 0.535 [0.50,0.57] | - | - | - | N | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| X37-micro-plus-base | sig | NY/ST | MBR:stack | 0.538 [0.52,0.56] | 0.534 [0.51,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X32-book-depth | sig | NY | M32R:stack | 0.532 [0.51,0.55] | 0.532 [0.51,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | POOLED | M22R:stack | 0.524 [0.51,0.54] | 0.532 [0.52,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | ASIA/HM | M22R:stack | 0.518 [0.49,0.55] | 0.531 [0.50,0.56] | - | - | - | N | - | - | - | - |  | short by 0.149 AUC, 5 of 5 econ |
| X22-trade-geometry | sig | POOLED/HM | M22R:stack | 0.521 [0.51,0.54] | 0.531 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | POOLED/ST | M22R:stack | 0.526 [0.51,0.54] | 0.530 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | NY/HM | MFR:stack | 0.524 [0.50,0.55] | 0.529 [0.49,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | NY/ST | MUR:stack | 0.531 [0.51,0.55] | 0.529 [0.50,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | ASIA | M35R:stack | 0.512 [0.49,0.53] | 0.529 [0.50,0.56] | - | - | - | N | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| X33-approach-dynamics | sig | NY | M33R:stack | 0.533 [0.52,0.55] | 0.528 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | NY/ST | M32R:stack | 0.533 [0.51,0.55] | 0.528 [0.50,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | ASIA/HM | M31R:stack | 0.520 [0.49,0.55] | 0.527 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| X35-whipsaw-neighbours | sig | POOLED/HM | M35R:stack | 0.524 [0.51,0.54] | 0.527 [0.50,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | LONDON/ST | M22R:stack | 0.513 [0.49,0.54] | 0.527 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| X34-level-proximity | sig | POOLED/ST | M34R:stack | 0.527 [0.52,0.54] | 0.526 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | ASIA/HM | M33R:stack | 0.510 [0.48,0.54] | 0.526 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| X34-level-proximity | sig | ASIA | M34R:stack | 0.517 [0.50,0.54] | 0.526 [0.50,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | POOLED | M34R:stack | 0.526 [0.52,0.54] | 0.526 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | ASIA | M22R:stack | 0.510 [0.49,0.53] | 0.525 [0.50,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | POOLED/HM | MBR:stack | 0.517 [0.50,0.53] | 0.525 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X37-micro-plus-base | sig | ASIA/ST | MBT:stack | 0.505 [0.48,0.53] | 0.524 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X32-book-depth | sig | POOLED/ST | M32R:stack | 0.524 [0.51,0.54] | 0.524 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | POOLED/HM | M34R:stack | 0.525 [0.51,0.54] | 0.524 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | POOLED | M35R:stack | 0.520 [0.51,0.53] | 0.523 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | ASIA | M32R:stack | 0.519 [0.50,0.54] | 0.523 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | LONDON/ST | M34R:stack | 0.510 [0.49,0.53] | 0.523 [0.49,0.55] | - | - | - | N | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| X27-signal-flow | sig | ASIA/HM | MFR:stack | 0.494 [0.47,0.52] | 0.522 [0.48,0.56] | - | - | - | N | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| X36-micro-union | sig | POOLED/HM | MUR:stack | 0.523 [0.51,0.54] | 0.522 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | NY/HM | M34T:stack | 0.507 [0.48,0.53] | 0.521 [0.48,0.56] | - | - | - | N | - | - | - | - |  | short by 0.159 AUC, 5 of 5 econ |
| X33-approach-dynamics | sig | POOLED/HM | M33R:stack | 0.518 [0.50,0.54] | 0.521 [0.50,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | ASIA | MUR:stack | 0.520 [0.50,0.54] | 0.520 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | POOLED | M32R:stack | 0.520 [0.51,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | POOLED | MBR:stack | 0.517 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X32-book-depth | sig | ASIA/HM | M32T:stack | 0.515 [0.49,0.54] | 0.520 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| X35-whipsaw-neighbours | sig | POOLED/ST | M35R:stack | 0.516 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | NY/ST | M33R:stack | 0.525 [0.51,0.54] | 0.518 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | NY/HM | M31R:stack | 0.515 [0.49,0.54] | 0.518 [0.48,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | ASIA | M33R:stack | 0.503 [0.48,0.53] | 0.518 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | ASIA/HM | M35T:stack | 0.514 [0.48,0.54] | 0.517 [0.48,0.56] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| X36-micro-union | sig | POOLED | MUR:stack | 0.518 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | POOLED/HM | M31R:stack | 0.509 [0.49,0.53] | 0.517 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | ASIA/ST | M22R:stack | 0.503 [0.48,0.53] | 0.516 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | NY | MFR:stack | 0.515 [0.50,0.53] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | POOLED/ST | MBR:stack | 0.517 [0.50,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-signal-flow | sig | POOLED/HM | MFR:stack | 0.505 [0.49,0.52] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | ASIA/ST | M34R:stack | 0.513 [0.49,0.54] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | NY | M34T:stack | 0.504 [0.49,0.52] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| X32-book-depth | sig | POOLED/HM | M32R:stack | 0.514 [0.50,0.53] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | LONDON | M31T:stack | 0.501 [0.48,0.52] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| X35-whipsaw-neighbours | sig | ASIA | M35T:stack | 0.512 [0.49,0.54] | 0.514 [0.48,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X33-approach-dynamics | sig | POOLED | M33R:stack | 0.513 [0.50,0.52] | 0.514 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | ASIA/HM | M22T:stack | 0.508 [0.48,0.54] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| X35-whipsaw-neighbours | sig | ASIA/ST | M35R:stack | 0.501 [0.47,0.53] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | ASIA/HM | MBR:stack | 0.507 [0.48,0.54] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X32-book-depth | sig | NY/HM | M32T:stack | 0.506 [0.48,0.53] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| X37-micro-plus-base | sig | ASIA | MBR:stack | 0.504 [0.48,0.53] | 0.513 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X36-micro-union | sig | POOLED/ST | MUR:stack | 0.515 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | ASIA | MBT:stack | 0.499 [0.48,0.52] | 0.512 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-signal-flow | sig | ASIA | MFR:stack | 0.494 [0.47,0.52] | 0.512 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | NY/ST | M34T:stack | 0.502 [0.48,0.52] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| X31-aggressor-flow | sig | POOLED/HM | M31T:stack | 0.500 [0.48,0.52] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| X35-whipsaw-neighbours | sig | ASIA/ST | M35T:stack | 0.511 [0.48,0.54] | 0.511 [0.47,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | ASIA/ST | MBR:stack | 0.500 [0.47,0.53] | 0.511 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X22-trade-geometry | sig | ASIA | M22T:stack | 0.508 [0.48,0.53] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X32-book-depth | sig | POOLED/HM | M32T:stack | 0.499 [0.48,0.51] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| X22-trade-geometry | sig | LONDON/HM | M22T:stack | 0.495 [0.47,0.52] | 0.510 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | NY/HM | M35T:stack | 0.496 [0.47,0.52] | 0.509 [0.47,0.55] | - | - | - | N | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| X32-book-depth | sig | ASIA | M32T:stack | 0.509 [0.49,0.53] | 0.509 [0.48,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X33-approach-dynamics | sig | ASIA/ST | M33R:stack | 0.497 [0.47,0.52] | 0.509 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | POOLED/HM | M35T:stack | 0.499 [0.49,0.51] | 0.509 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| X33-approach-dynamics | sig | POOLED/ST | M33R:stack | 0.510 [0.50,0.52] | 0.508 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | ASIA/ST | M22T:stack | 0.507 [0.48,0.54] | 0.508 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | ASIA/ST | MUR:stack | 0.503 [0.47,0.53] | 0.508 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | ASIA | M31R:stack | 0.508 [0.48,0.53] | 0.507 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | NY/ST | MFR:stack | 0.509 [0.49,0.53] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | LONDON/ST | MBT:stack | 0.486 [0.46,0.51] | 0.506 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X33-approach-dynamics | sig | LONDON | M33T:stack | 0.496 [0.47,0.52] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | NY/HM | MUT:stack | 0.521 [0.50,0.54] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| X37-micro-plus-base | sig | LONDON | MBT:stack | 0.490 [0.47,0.51] | 0.505 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | NY | M35T:stack | 0.498 [0.48,0.51] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| X37-micro-plus-base | sig | LONDON/HM | MBT:stack | 0.496 [0.47,0.52] | 0.505 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X32-book-depth | sig | NY | M32T:stack | 0.507 [0.49,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| X34-level-proximity | sig | POOLED/HM | M34T:stack | 0.505 [0.49,0.52] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.176 AUC, 5 of 5 econ |
| X22-trade-geometry | sig | LONDON | M22R:stack | 0.495 [0.47,0.52] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | NY/ST | M22T:stack | 0.501 [0.48,0.52] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| X27-signal-flow | sig | ASIA/ST | MFR:stack | 0.494 [0.46,0.52] | 0.503 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | POOLED | M34T:stack | 0.505 [0.49,0.52] | 0.503 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | POOLED | MFR:stack | 0.501 [0.49,0.51] | 0.503 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | ASIA/ST | MUT:stack | 0.518 [0.49,0.55] | 0.503 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | POOLED | M35T:stack | 0.499 [0.49,0.51] | 0.503 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | ASIA/HM | M34T:stack | 0.506 [0.48,0.54] | 0.502 [0.47,0.54] | - | - | - | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| X33-approach-dynamics | sig | POOLED/HM | M33T:stack | 0.503 [0.49,0.52] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | LONDON | M34R:stack | 0.503 [0.48,0.53] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X34-level-proximity | sig | POOLED/ST | M34T:stack | 0.505 [0.49,0.52] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | NY/ST | M35T:stack | 0.500 [0.48,0.52] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| X34-level-proximity | sig | ASIA | M34T:stack | 0.509 [0.49,0.53] | 0.502 [0.47,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X32-book-depth | sig | POOLED | M32T:stack | 0.501 [0.49,0.51] | 0.501 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | ASIA/ST | M34T:stack | 0.512 [0.49,0.54] | 0.501 [0.46,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | ASIA/ST | M32T:stack | 0.505 [0.48,0.53] | 0.501 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | POOLED/ST | MBT:stack | 0.489 [0.48,0.50] | 0.500 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X31-aggressor-flow | sig | NY/HM | M31T:stack | 0.484 [0.46,0.50] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | ASIA/HM | MFT:stack | 0.490 [0.46,0.52] | 0.500 [0.46,0.54] | - | - | - | N | - | - | - | - |  | short by 0.180 AUC, 5 of 5 econ |
| X33-approach-dynamics | sig | ASIA/HM | M33T:stack | 0.509 [0.48,0.54] | 0.500 [0.46,0.54] | - | - | - | N | - | - | - | - |  | short by 0.180 AUC, 5 of 5 econ |
| X31-aggressor-flow | sig | POOLED | M31R:stack | 0.503 [0.49,0.51] | 0.500 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | NY/ST | M32T:stack | 0.508 [0.49,0.53] | 0.499 [0.47,0.53] | - | - | - | N | - | - | - | - |  | short by 0.181 AUC, 5 of 5 econ |
| X37-micro-plus-base | sig | ASIA/HM | MBT:stack | 0.491 [0.46,0.52] | 0.499 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.181 AUC, 5 of 5 econ |
| X36-micro-union | sig | NY | MUT:stack | 0.507 [0.49,0.52] | 0.499 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | POOLED | M31T:stack | 0.496 [0.48,0.51] | 0.498 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | POOLED/ST | M35T:stack | 0.499 [0.49,0.51] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | POOLED/ST | M22T:stack | 0.497 [0.49,0.51] | 0.498 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | LONDON/ST | MFT:stack | 0.487 [0.46,0.51] | 0.498 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | POOLED | M22T:stack | 0.498 [0.49,0.51] | 0.497 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | LONDON/HM | M35T:stack | 0.488 [0.46,0.51] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | NY/HM | MFT:stack | 0.523 [0.50,0.55] | 0.497 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | POOLED/HM | M22T:stack | 0.500 [0.48,0.52] | 0.496 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | NY | M31T:stack | 0.494 [0.48,0.51] | 0.496 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | POOLED | MBT:stack | 0.489 [0.48,0.50] | 0.496 [0.48,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X32-book-depth | sig | ASIA/HM | M32R:stack | 0.512 [0.48,0.54] | 0.496 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | LONDON/HM | M32T:stack | 0.474 [0.44,0.51] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | ASIA | MUT:stack | 0.513 [0.49,0.54] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X32-book-depth | sig | LONDON/ST | M32R:stack | 0.500 [0.47,0.53] | 0.495 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | LONDON | M32R:stack | 0.493 [0.47,0.52] | 0.495 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | POOLED/ST | M32T:stack | 0.502 [0.49,0.52] | 0.495 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | POOLED/ST | MUT:stack | 0.500 [0.49,0.52] | 0.495 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | LONDON/HM | M32R:stack | 0.484 [0.45,0.51] | 0.494 [0.46,0.53] | - | - | - | N | - | - | - | - |  | short by 0.186 AUC, 5 of 5 econ |
| X33-approach-dynamics | sig | ASIA | M33T:stack | 0.501 [0.48,0.53] | 0.494 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | LONDON/HM | M31R:stack | 0.473 [0.44,0.50] | 0.494 [0.45,0.53] | - | - | - | N | - | - | - | - |  | short by 0.186 AUC, 5 of 5 econ |
| X36-micro-union | sig | NY/ST | MUT:stack | 0.497 [0.48,0.52] | 0.494 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | NY | M31R:stack | 0.507 [0.49,0.53] | 0.494 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | NY/ST | M31T:stack | 0.501 [0.48,0.52] | 0.494 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | LONDON | M22T:stack | 0.488 [0.47,0.51] | 0.493 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | POOLED/HM | MFT:stack | 0.503 [0.49,0.52] | 0.493 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | POOLED/ST | MFR:stack | 0.499 [0.49,0.51] | 0.493 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | POOLED | MUT:stack | 0.504 [0.49,0.52] | 0.493 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | LONDON | MFT:stack | 0.488 [0.46,0.51] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | NY | MFT:stack | 0.512 [0.49,0.53] | 0.491 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | NY | M22T:stack | 0.499 [0.48,0.52] | 0.491 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | LONDON | M31R:stack | 0.477 [0.45,0.50] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | POOLED/HM | MUT:stack | 0.509 [0.49,0.52] | 0.490 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | POOLED | MFT:stack | 0.498 [0.49,0.51] | 0.490 [0.48,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | ASIA/HM | M31T:stack | 0.497 [0.47,0.53] | 0.489 [0.45,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X33-approach-dynamics | sig | POOLED | M33T:stack | 0.495 [0.48,0.51] | 0.489 [0.48,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | POOLED/HM | MBT:stack | 0.488 [0.47,0.50] | 0.489 [0.47,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X31-aggressor-flow | sig | ASIA/ST | M31R:stack | 0.498 [0.47,0.53] | 0.489 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | ASIA/ST | M33T:stack | 0.494 [0.46,0.53] | 0.489 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | LONDON/HM | MBR:stack | 0.491 [0.46,0.52] | 0.489 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X31-aggressor-flow | sig | POOLED/ST | M31T:stack | 0.493 [0.48,0.51] | 0.488 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | ASIA | MFT:stack | 0.486 [0.46,0.51] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | ASIA/HM | MUT:stack | 0.509 [0.48,0.54] | 0.488 [0.45,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X34-level-proximity | sig | LONDON/ST | M34T:stack | 0.505 [0.48,0.53] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X27-signal-flow | sig | POOLED/ST | MFT:stack | 0.494 [0.48,0.51] | 0.488 [0.47,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | LONDON | M35T:stack | 0.487 [0.47,0.51] | 0.487 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | NY/ST | MFT:stack | 0.505 [0.49,0.52] | 0.487 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | POOLED/ST | M31R:stack | 0.499 [0.49,0.51] | 0.487 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | LONDON/ST | M31R:stack | 0.481 [0.46,0.51] | 0.487 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | LONDON/ST | M31T:stack | 0.482 [0.45,0.51] | 0.487 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | LONDON | M32T:stack | 0.483 [0.46,0.51] | 0.487 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | LONDON/ST | MUT:stack | 0.490 [0.46,0.52] | 0.486 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | LONDON | MBR:stack | 0.487 [0.46,0.51] | 0.486 [0.46,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X36-micro-union | sig | LONDON/ST | MUR:stack | 0.493 [0.47,0.51] | 0.486 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | LONDON | M34T:stack | 0.504 [0.48,0.53] | 0.486 [0.45,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X31-aggressor-flow | sig | ASIA | M31T:stack | 0.493 [0.47,0.52] | 0.485 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | LONDON/ST | M33R:stack | 0.479 [0.46,0.50] | 0.485 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | LONDON/HM | MFT:stack | 0.488 [0.46,0.52] | 0.484 [0.44,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | LONDON/ST | MBR:stack | 0.484 [0.46,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X37-micro-plus-base | sig | NY/ST | MBT:stack | 0.485 [0.47,0.50] | 0.483 [0.46,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X34-level-proximity | sig | LONDON/HM | M34T:stack | 0.502 [0.47,0.53] | 0.482 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-aggressor-flow | sig | ASIA/ST | M31T:stack | 0.490 [0.47,0.52] | 0.482 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-book-depth | sig | LONDON/ST | M32T:stack | 0.489 [0.46,0.52] | 0.481 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | LONDON/ST | M35R:stack | 0.486 [0.46,0.51] | 0.481 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | POOLED/ST | M33T:stack | 0.488 [0.48,0.50] | 0.480 [0.46,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | LONDON/ST | M22T:stack | 0.482 [0.46,0.50] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | LONDON | MUT:stack | 0.491 [0.47,0.51] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | LONDON/ST | M35T:stack | 0.486 [0.46,0.51] | 0.479 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | ASIA/ST | MFT:stack | 0.482 [0.45,0.51] | 0.479 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | LONDON | M33R:stack | 0.474 [0.45,0.50] | 0.479 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | LONDON | MUR:stack | 0.487 [0.47,0.51] | 0.479 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | NY | MBT:stack | 0.483 [0.47,0.50] | 0.479 [0.46,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X31-aggressor-flow | sig | NY/ST | M31R:stack | 0.502 [0.48,0.52] | 0.478 [0.45,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | LONDON/ST | M33T:stack | 0.485 [0.46,0.51] | 0.477 [0.45,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | LONDON/HM | MFR:stack | 0.473 [0.44,0.50] | 0.477 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X34-level-proximity | sig | LONDON/HM | M34R:stack | 0.493 [0.46,0.52] | 0.476 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | NY/ST | M33T:stack | 0.487 [0.47,0.51] | 0.476 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | NY | M33T:stack | 0.490 [0.47,0.51] | 0.476 [0.45,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | NY/HM | M33T:stack | 0.495 [0.47,0.52] | 0.475 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X22-trade-geometry | sig | LONDON/HM | M22R:stack | 0.472 [0.44,0.50] | 0.474 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | LONDON | M35R:stack | 0.487 [0.47,0.51] | 0.473 [0.45,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X37-micro-plus-base | sig | NY/HM | MBT:stack | 0.480 [0.46,0.50] | 0.472 [0.44,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X22-trade-geometry | sig | NY/HM | M22T:stack | 0.497 [0.47,0.52] | 0.471 [0.43,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X33-approach-dynamics | sig | LONDON/HM | M33R:stack | 0.466 [0.43,0.50] | 0.471 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | LONDON/HM | MUT:stack | 0.491 [0.46,0.52] | 0.471 [0.43,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X36-micro-union | sig | LONDON/HM | MUR:stack | 0.479 [0.45,0.51] | 0.469 [0.43,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X35-whipsaw-neighbours | sig | LONDON/HM | M35R:stack | 0.489 [0.46,0.52] | 0.463 [0.42,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | LONDON | MFR:stack | 0.471 [0.45,0.49] | 0.461 [0.43,0.49] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-signal-flow | sig | LONDON/ST | MFR:stack | 0.469 [0.45,0.49] | 0.449 [0.42,0.48] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |

One-sentence notes:
- X31-aggressor-flow -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X31-aggressor-flow -1 ASIA: unlocked
- X31-aggressor-flow -1 LONDON: unlocked
- X31-aggressor-flow -1 NY: unlocked
- X31-aggressor-flow -1 POOLED: unlocked
- X31-aggressor-flow -1 ASIA: unlocked
- X31-aggressor-flow -1 LONDON: unlocked
- X31-aggressor-flow -1 NY: unlocked
- X31-aggressor-flow -1 POOLED: unlocked
- X31-aggressor-flow -1 ASIA: unlocked
- X31-aggressor-flow -1 LONDON: unlocked
- X31-aggressor-flow -1 NY: unlocked
- X31-aggressor-flow -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X31-aggressor-flow -1 ASIA: unlocked
- X31-aggressor-flow -1 LONDON: unlocked
- X31-aggressor-flow -1 NY: unlocked
- X31-aggressor-flow -1 POOLED: unlocked
- X31-aggressor-flow -1 ASIA: unlocked
- X31-aggressor-flow -1 LONDON: unlocked
- X31-aggressor-flow -1 NY: unlocked
- X31-aggressor-flow -1 POOLED: unlocked
- X31-aggressor-flow -1 ASIA: unlocked
- X31-aggressor-flow -1 LONDON: unlocked
- X31-aggressor-flow -1 NY: unlocked
- X32-book-depth -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X32-book-depth -1 ASIA: unlocked
- X32-book-depth -1 LONDON: unlocked
- X32-book-depth -1 NY: unlocked
- X32-book-depth -1 POOLED: unlocked
- X32-book-depth -1 ASIA: unlocked
- X32-book-depth -1 LONDON: unlocked
- X32-book-depth -1 NY: unlocked
- X32-book-depth -1 POOLED: unlocked
- X32-book-depth -1 ASIA: unlocked
- X32-book-depth -1 LONDON: unlocked
- X32-book-depth -1 NY: unlocked
- X32-book-depth -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X32-book-depth -1 ASIA: unlocked
- X32-book-depth -1 LONDON: unlocked
- X32-book-depth -1 NY: unlocked
- X32-book-depth -1 POOLED: unlocked
- X32-book-depth -1 ASIA: unlocked
- X32-book-depth -1 LONDON: unlocked
- X32-book-depth -1 NY: unlocked
- X32-book-depth -1 POOLED: unlocked
- X32-book-depth -1 ASIA: unlocked
- X32-book-depth -1 LONDON: unlocked
- X32-book-depth -1 NY: unlocked
- X33-approach-dynamics -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X33-approach-dynamics -1 ASIA: unlocked
- X33-approach-dynamics -1 LONDON: unlocked
- X33-approach-dynamics -1 NY: unlocked
- X33-approach-dynamics -1 POOLED: unlocked
- X33-approach-dynamics -1 ASIA: unlocked
- X33-approach-dynamics -1 LONDON: unlocked
- X33-approach-dynamics -1 NY: unlocked
- X33-approach-dynamics -1 POOLED: unlocked
- X33-approach-dynamics -1 ASIA: unlocked
- X33-approach-dynamics -1 LONDON: unlocked
- X33-approach-dynamics -1 NY: unlocked
- X33-approach-dynamics -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X33-approach-dynamics -1 ASIA: unlocked
- X33-approach-dynamics -1 LONDON: unlocked
- X33-approach-dynamics -1 NY: unlocked
- X33-approach-dynamics -1 POOLED: unlocked
- X33-approach-dynamics -1 ASIA: unlocked
- X33-approach-dynamics -1 LONDON: unlocked
- X33-approach-dynamics -1 NY: unlocked
- X33-approach-dynamics -1 POOLED: unlocked
- X33-approach-dynamics -1 ASIA: unlocked
- X33-approach-dynamics -1 LONDON: unlocked
- X33-approach-dynamics -1 NY: unlocked
- X34-level-proximity -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X34-level-proximity -1 ASIA: unlocked
- X34-level-proximity -1 LONDON: unlocked
- X34-level-proximity -1 NY: unlocked
- X34-level-proximity -1 POOLED: unlocked
- X34-level-proximity -1 ASIA: unlocked
- X34-level-proximity -1 LONDON: unlocked
- X34-level-proximity -1 NY: unlocked
- X34-level-proximity -1 POOLED: unlocked
- X34-level-proximity -1 ASIA: unlocked
- X34-level-proximity -1 LONDON: unlocked
- X34-level-proximity -1 NY: unlocked
- X34-level-proximity -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X34-level-proximity -1 ASIA: unlocked
- X34-level-proximity -1 LONDON: unlocked
- X34-level-proximity -1 NY: unlocked
- X34-level-proximity -1 POOLED: unlocked
- X34-level-proximity -1 ASIA: unlocked
- X34-level-proximity -1 LONDON: unlocked
- X34-level-proximity -1 NY: unlocked
- X34-level-proximity -1 POOLED: unlocked
- X34-level-proximity -1 ASIA: unlocked
- X34-level-proximity -1 LONDON: unlocked
- X34-level-proximity -1 NY: unlocked
- X35-whipsaw-neighbours -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X35-whipsaw-neighbours -1 ASIA: unlocked
- X35-whipsaw-neighbours -1 LONDON: unlocked
- X35-whipsaw-neighbours -1 NY: unlocked
- X35-whipsaw-neighbours -1 POOLED: unlocked
- X35-whipsaw-neighbours -1 ASIA: unlocked
- X35-whipsaw-neighbours -1 LONDON: unlocked
- X35-whipsaw-neighbours -1 NY: unlocked
- X35-whipsaw-neighbours -1 POOLED: unlocked
- X35-whipsaw-neighbours -1 ASIA: unlocked
- X35-whipsaw-neighbours -1 LONDON: unlocked
- X35-whipsaw-neighbours -1 NY: unlocked
- X35-whipsaw-neighbours -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X35-whipsaw-neighbours -1 ASIA: unlocked
- X35-whipsaw-neighbours -1 LONDON: unlocked
- X35-whipsaw-neighbours -1 NY: unlocked
- X35-whipsaw-neighbours -1 POOLED: unlocked
- X35-whipsaw-neighbours -1 ASIA: unlocked
- X35-whipsaw-neighbours -1 LONDON: unlocked
- X35-whipsaw-neighbours -1 NY: unlocked
- X35-whipsaw-neighbours -1 POOLED: unlocked
- X35-whipsaw-neighbours -1 ASIA: unlocked
- X35-whipsaw-neighbours -1 LONDON: unlocked
- X35-whipsaw-neighbours -1 NY: unlocked
- X22-trade-geometry -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X22-trade-geometry -1 ASIA: unlocked
- X22-trade-geometry -1 LONDON: unlocked
- X22-trade-geometry -1 NY: unlocked
- X22-trade-geometry -1 POOLED: unlocked
- X22-trade-geometry -1 ASIA: unlocked
- X22-trade-geometry -1 LONDON: unlocked
- X22-trade-geometry -1 NY: unlocked
- X22-trade-geometry -1 POOLED: unlocked
- X22-trade-geometry -1 ASIA: unlocked
- X22-trade-geometry -1 LONDON: unlocked
- X22-trade-geometry -1 NY: unlocked
- X22-trade-geometry -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X22-trade-geometry -1 ASIA: unlocked
- X22-trade-geometry -1 LONDON: unlocked
- X22-trade-geometry -1 NY: unlocked
- X22-trade-geometry -1 POOLED: unlocked
- X22-trade-geometry -1 ASIA: unlocked
- X22-trade-geometry -1 LONDON: unlocked
- X22-trade-geometry -1 NY: unlocked
- X22-trade-geometry -1 POOLED: unlocked
- X22-trade-geometry -1 ASIA: unlocked
- X22-trade-geometry -1 LONDON: unlocked
- X22-trade-geometry -1 NY: unlocked
- X36-micro-union -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X36-micro-union -1 ASIA: unlocked
- X36-micro-union -1 LONDON: unlocked
- X36-micro-union -1 NY: unlocked
- X36-micro-union -1 POOLED: unlocked
- X36-micro-union -1 ASIA: unlocked
- X36-micro-union -1 LONDON: unlocked
- X36-micro-union -1 NY: unlocked
- X36-micro-union -1 POOLED: unlocked
- X36-micro-union -1 ASIA: unlocked
- X36-micro-union -1 LONDON: unlocked
- X36-micro-union -1 NY: unlocked
- X36-micro-union -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X36-micro-union -1 ASIA: unlocked
- X36-micro-union -1 LONDON: unlocked
- X36-micro-union -1 NY: unlocked
- X36-micro-union -1 POOLED: unlocked
- X36-micro-union -1 ASIA: unlocked
- X36-micro-union -1 LONDON: unlocked
- X36-micro-union -1 NY: unlocked
- X36-micro-union -1 POOLED: unlocked
- X36-micro-union -1 ASIA: unlocked
- X36-micro-union -1 LONDON: unlocked
- X36-micro-union -1 NY: unlocked
- X37-micro-plus-base -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X37-micro-plus-base -1 ASIA: unlocked
- X37-micro-plus-base -1 LONDON: unlocked
- X37-micro-plus-base -1 NY: unlocked
- X37-micro-plus-base -1 POOLED: unlocked
- X37-micro-plus-base -1 ASIA: unlocked
- X37-micro-plus-base -1 LONDON: unlocked
- X37-micro-plus-base -1 NY: unlocked
- X37-micro-plus-base -1 POOLED: unlocked
- X37-micro-plus-base -1 ASIA: unlocked
- X37-micro-plus-base -1 LONDON: unlocked
- X37-micro-plus-base -1 NY: unlocked
- X37-micro-plus-base -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X37-micro-plus-base -1 ASIA: unlocked
- X37-micro-plus-base -1 LONDON: unlocked
- X37-micro-plus-base -1 NY: unlocked
- X37-micro-plus-base -1 POOLED: unlocked
- X37-micro-plus-base -1 ASIA: unlocked
- X37-micro-plus-base -1 LONDON: unlocked
- X37-micro-plus-base -1 NY: unlocked
- X37-micro-plus-base -1 POOLED: unlocked
- X37-micro-plus-base -1 ASIA: unlocked
- X37-micro-plus-base -1 LONDON: unlocked
- X37-micro-plus-base -1 NY: unlocked
- X27-signal-flow -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X27-signal-flow -1 ASIA: unlocked
- X27-signal-flow -1 LONDON: unlocked
- X27-signal-flow -1 NY: unlocked
- X27-signal-flow -1 POOLED: unlocked
- X27-signal-flow -1 ASIA: unlocked
- X27-signal-flow -1 LONDON: unlocked
- X27-signal-flow -1 NY: unlocked
- X27-signal-flow -1 POOLED: unlocked
- X27-signal-flow -1 ASIA: unlocked
- X27-signal-flow -1 LONDON: unlocked
- X27-signal-flow -1 NY: unlocked
- X27-signal-flow -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X27-signal-flow -1 ASIA: unlocked
- X27-signal-flow -1 LONDON: unlocked
- X27-signal-flow -1 NY: unlocked
- X27-signal-flow -1 POOLED: unlocked
- X27-signal-flow -1 ASIA: unlocked
- X27-signal-flow -1 LONDON: unlocked
- X27-signal-flow -1 NY: unlocked
- X27-signal-flow -1 POOLED: unlocked
- X27-signal-flow -1 ASIA: unlocked
- X27-signal-flow -1 LONDON: unlocked
- X27-signal-flow -1 NY: unlocked
