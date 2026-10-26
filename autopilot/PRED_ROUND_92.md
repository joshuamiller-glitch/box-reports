# PRED ROUND 92 - block X5 round 8 - X47+X48+X49+X50+X51

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.556 [0.52,0.59]
Gap to FOUND: 0.124 AUC, 5 of 5 economic conditions short.
not found - short by 0.124 AUC and 5 of 5 economic conditions

prereg 1658166f61d92322764ec9223cb4f1bd986a0d29d969cd7a72666039bed52d6a ; trials added 120 ; truncation audit {'decisions': 252, 'checks': 12444, 'mismatches': 0} ; holdout scored True ; feature store ['l2vast/pred/store/X47_sigu.parquet', 'l2vast/pred/store/X48_sigu.parquet', 'l2vast/pred/store/X49_sigu.parquet', 'l2vast/pred/store/X50_sigu.parquet', 'l2vast/pred/store/X51_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X49-stop-dist-quantiles | sig | NY/HM | M49R:stack | 0.547 [0.52,0.57] | 0.556 [0.52,0.59] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | NY/HM | M50R:stack | 0.541 [0.51,0.57] | 0.548 [0.51,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | NY | M49R:stack | 0.537 [0.52,0.55] | 0.541 [0.52,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | LONDON/HM | M49T:stack | 0.511 [0.48,0.54] | 0.535 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| X50-entry-bar-shape | sig | NY | M50R:stack | 0.535 [0.52,0.55] | 0.534 [0.51,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | LONDON/HM | M48T:stack | 0.512 [0.48,0.54] | 0.534 [0.49,0.58] | - | - | - | N | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| X49-stop-dist-quantiles | sig | ASIA/HM | M49T:stack | 0.508 [0.48,0.54] | 0.533 [0.50,0.57] | - | - | - | N | - | - | - | - |  | short by 0.147 AUC, 5 of 5 econ |
| X49-stop-dist-quantiles | sig | POOLED/HM | M49R:stack | 0.524 [0.51,0.54] | 0.532 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | NY/HM | M47R:stack | 0.516 [0.49,0.54] | 0.530 [0.49,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | NY/ST | M49R:stack | 0.530 [0.51,0.55] | 0.529 [0.50,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | NY/HM | M48R:stack | 0.520 [0.49,0.55] | 0.528 [0.49,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | ASIA/HM | M47R:stack | 0.511 [0.48,0.54] | 0.527 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| X49-stop-dist-quantiles | sig | POOLED | M49R:stack | 0.519 [0.51,0.53] | 0.527 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | ASIA/HM | M49R:stack | 0.513 [0.48,0.54] | 0.525 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.155 AUC, 5 of 5 econ |
| X50-entry-bar-shape | sig | NY/ST | M50R:stack | 0.531 [0.51,0.55] | 0.524 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | ASIA | M47R:stack | 0.508 [0.48,0.53] | 0.523 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | LONDON/ST | M49R:stack | 0.488 [0.46,0.51] | 0.523 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| X48-stop-runs | sig | POOLED/HM | M48T:stack | 0.508 [0.49,0.53] | 0.522 [0.49,0.55] | - | - | - | N | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| X49-stop-dist-quantiles | sig | POOLED/ST | M49R:stack | 0.514 [0.50,0.53] | 0.522 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | ASIA/HM | M51R:stack | 0.508 [0.48,0.54] | 0.522 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| X47-level-touches | sig | NY | M47R:stack | 0.514 [0.50,0.53] | 0.521 [0.50,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | POOLED/HM | M49T:stack | 0.506 [0.49,0.52] | 0.521 [0.50,0.54] | - | - | - | N | - | - | - | - |  | short by 0.159 AUC, 5 of 5 econ |
| X51-confirmation-timing | sig | NY/HM | M51R:stack | 0.521 [0.49,0.55] | 0.520 [0.48,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | NY/HM | M48T:stack | 0.520 [0.49,0.55] | 0.520 [0.48,0.56] | - | - | - | N | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| X47-level-touches | sig | ASIA/ST | M47R:stack | 0.505 [0.48,0.54] | 0.519 [0.48,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | POOLED/HM | M50R:stack | 0.516 [0.50,0.53] | 0.519 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | NY | M48T:stack | 0.516 [0.50,0.53] | 0.518 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| X51-confirmation-timing | sig | NY | M51R:stack | 0.518 [0.50,0.54] | 0.518 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | POOLED | M50R:stack | 0.515 [0.50,0.53] | 0.517 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | NY/ST | M48T:stack | 0.513 [0.49,0.53] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| X50-entry-bar-shape | sig | POOLED/ST | M50R:stack | 0.514 [0.50,0.53] | 0.516 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | NY | M48R:stack | 0.517 [0.50,0.54] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | ASIA | M49T:stack | 0.492 [0.47,0.52] | 0.515 [0.49,0.55] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| X51-confirmation-timing | sig | NY/ST | M51R:stack | 0.516 [0.50,0.54] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | NY/ST | M47R:stack | 0.513 [0.49,0.53] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | POOLED/ST | M47R:stack | 0.512 [0.50,0.53] | 0.515 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | POOLED | M47R:stack | 0.510 [0.50,0.52] | 0.514 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | ASIA/HM | M48T:stack | 0.487 [0.45,0.52] | 0.514 [0.47,0.56] | - | - | - | N | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| X49-stop-dist-quantiles | sig | ASIA | M49R:stack | 0.508 [0.48,0.53] | 0.514 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | ASIA/ST | M48R:stack | 0.509 [0.48,0.53] | 0.514 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | LONDON | M48T:stack | 0.502 [0.48,0.53] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| X47-level-touches | sig | ASIA/HM | M47T:stack | 0.509 [0.48,0.54] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| X47-level-touches | sig | POOLED/HM | M47R:stack | 0.508 [0.49,0.52] | 0.514 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | LONDON/HM | M50T:stack | 0.493 [0.46,0.52] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | ASIA | M48R:stack | 0.509 [0.49,0.53] | 0.513 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | LONDON/HM | M51T:stack | 0.499 [0.47,0.53] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | POOLED | M48T:stack | 0.506 [0.49,0.52] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| X50-entry-bar-shape | sig | ASIA/HM | M50R:stack | 0.502 [0.47,0.54] | 0.512 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | ASIA/HM | M48R:stack | 0.507 [0.48,0.54] | 0.511 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | ASIA/ST | M50R:stack | 0.500 [0.47,0.53] | 0.511 [0.47,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | POOLED/ST | M48R:stack | 0.508 [0.50,0.52] | 0.511 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | ASIA | M50R:stack | 0.499 [0.47,0.52] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | ASIA | M47T:stack | 0.506 [0.48,0.53] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | POOLED | M48R:stack | 0.506 [0.49,0.52] | 0.510 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | LONDON | M49T:stack | 0.495 [0.47,0.52] | 0.509 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | POOLED/HM | M51R:stack | 0.510 [0.49,0.53] | 0.509 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | POOLED/HM | M48R:stack | 0.504 [0.49,0.52] | 0.509 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | LONDON | M49R:stack | 0.487 [0.47,0.51] | 0.508 [0.48,0.54] | - | - | - | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| X51-confirmation-timing | sig | LONDON | M51T:stack | 0.501 [0.48,0.52] | 0.508 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | NY/ST | M48R:stack | 0.515 [0.49,0.53] | 0.508 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | ASIA/HM | M50T:stack | 0.501 [0.47,0.53] | 0.507 [0.47,0.55] | - | - | - | N | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| X48-stop-runs | sig | LONDON/ST | M48R:stack | 0.482 [0.46,0.50] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | POOLED/HM | M50T:stack | 0.501 [0.48,0.52] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| X50-entry-bar-shape | sig | LONDON | M50T:stack | 0.493 [0.47,0.51] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | ASIA/ST | M47T:stack | 0.503 [0.47,0.53] | 0.506 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | ASIA/ST | M49R:stack | 0.504 [0.48,0.53] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | POOLED/ST | M48T:stack | 0.504 [0.49,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | POOLED | M51R:stack | 0.506 [0.49,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | LONDON/ST | M47R:stack | 0.506 [0.48,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X51-confirmation-timing | sig | LONDON/ST | M51T:stack | 0.502 [0.48,0.53] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X51-confirmation-timing | sig | ASIA | M51R:stack | 0.501 [0.48,0.53] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | ASIA | M48T:stack | 0.493 [0.47,0.52] | 0.503 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | NY/HM | M50T:stack | 0.508 [0.48,0.53] | 0.503 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | NY/ST | M51T:stack | 0.507 [0.49,0.53] | 0.502 [0.47,0.53] | - | - | - | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| X49-stop-dist-quantiles | sig | POOLED | M49T:stack | 0.496 [0.48,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | POOLED/ST | M51R:stack | 0.503 [0.49,0.52] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | LONDON/ST | M50R:stack | 0.485 [0.46,0.51] | 0.501 [0.46,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | ASIA/ST | M49T:stack | 0.477 [0.45,0.51] | 0.501 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | LONDON/ST | M50T:stack | 0.492 [0.47,0.52] | 0.500 [0.46,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | POOLED | M50T:stack | 0.495 [0.48,0.51] | 0.499 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | NY/HM | M49T:stack | 0.500 [0.47,0.52] | 0.499 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | LONDON/ST | M48T:stack | 0.493 [0.47,0.52] | 0.498 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | POOLED/ST | M51T:stack | 0.503 [0.49,0.52] | 0.498 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | POOLED/HM | M47T:stack | 0.507 [0.49,0.52] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | ASIA | M50T:stack | 0.492 [0.47,0.51] | 0.497 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | POOLED | M47T:stack | 0.499 [0.49,0.51] | 0.496 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | NY | M50T:stack | 0.499 [0.48,0.52] | 0.496 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | POOLED | M51T:stack | 0.501 [0.49,0.51] | 0.495 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | POOLED/ST | M47T:stack | 0.492 [0.48,0.51] | 0.495 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | ASIA/ST | M48T:stack | 0.499 [0.47,0.53] | 0.495 [0.46,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | NY/ST | M47T:stack | 0.489 [0.47,0.51] | 0.493 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | ASIA/HM | M51T:stack | 0.490 [0.46,0.52] | 0.493 [0.45,0.54] | - | - | - | N | - | - | - | - |  | short by 0.187 AUC, 5 of 5 econ |
| X47-level-touches | sig | NY | M47T:stack | 0.496 [0.48,0.51] | 0.493 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | POOLED/ST | M50T:stack | 0.490 [0.48,0.50] | 0.493 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | NY/HM | M47T:stack | 0.506 [0.48,0.53] | 0.493 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | POOLED/HM | M51T:stack | 0.498 [0.48,0.51] | 0.491 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | NY/ST | M50T:stack | 0.492 [0.47,0.51] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | LONDON | M48R:stack | 0.473 [0.45,0.49] | 0.491 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | ASIA/ST | M51R:stack | 0.496 [0.47,0.52] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | LONDON/HM | M49R:stack | 0.485 [0.45,0.52] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | NY | M51T:stack | 0.504 [0.49,0.52] | 0.490 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | POOLED/ST | M49T:stack | 0.489 [0.48,0.50] | 0.489 [0.47,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | NY | M49T:stack | 0.499 [0.48,0.51] | 0.489 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | LONDON | M47R:stack | 0.492 [0.47,0.51] | 0.488 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | LONDON/ST | M49T:stack | 0.484 [0.46,0.51] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | ASIA/ST | M50T:stack | 0.484 [0.46,0.51] | 0.488 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | LONDON/ST | M51R:stack | 0.477 [0.45,0.50] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | ASIA | M51T:stack | 0.494 [0.47,0.52] | 0.487 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | LONDON | M50R:stack | 0.482 [0.46,0.51] | 0.487 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | LONDON/ST | M47T:stack | 0.486 [0.46,0.51] | 0.486 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | LONDON | M47T:stack | 0.494 [0.47,0.52] | 0.485 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | LONDON/HM | M47T:stack | 0.505 [0.48,0.54] | 0.484 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X49-stop-dist-quantiles | sig | NY/ST | M49T:stack | 0.499 [0.48,0.52] | 0.483 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | ASIA/ST | M51T:stack | 0.497 [0.47,0.53] | 0.482 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | LONDON | M51R:stack | 0.480 [0.46,0.50] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | LONDON/HM | M51R:stack | 0.484 [0.45,0.52] | 0.471 [0.43,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X51-confirmation-timing | sig | NY/HM | M51T:stack | 0.500 [0.47,0.53] | 0.470 [0.43,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X50-entry-bar-shape | sig | LONDON/HM | M50R:stack | 0.479 [0.45,0.51] | 0.470 [0.43,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X48-stop-runs | sig | LONDON/HM | M48R:stack | 0.460 [0.43,0.49] | 0.470 [0.44,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X47-level-touches | sig | LONDON/HM | M47R:stack | 0.474 [0.44,0.50] | 0.466 [0.43,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |

One-sentence notes:
- X47-level-touches -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X47-level-touches -1 ASIA: unlocked
- X47-level-touches -1 LONDON: unlocked
- X47-level-touches -1 NY: unlocked
- X47-level-touches -1 POOLED: unlocked
- X47-level-touches -1 ASIA: unlocked
- X47-level-touches -1 LONDON: unlocked
- X47-level-touches -1 NY: unlocked
- X47-level-touches -1 POOLED: unlocked
- X47-level-touches -1 ASIA: unlocked
- X47-level-touches -1 LONDON: unlocked
- X47-level-touches -1 NY: unlocked
- X47-level-touches -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X47-level-touches -1 ASIA: unlocked
- X47-level-touches -1 LONDON: unlocked
- X47-level-touches -1 NY: unlocked
- X47-level-touches -1 POOLED: unlocked
- X47-level-touches -1 ASIA: unlocked
- X47-level-touches -1 LONDON: unlocked
- X47-level-touches -1 NY: unlocked
- X47-level-touches -1 POOLED: unlocked
- X47-level-touches -1 ASIA: unlocked
- X47-level-touches -1 LONDON: unlocked
- X47-level-touches -1 NY: unlocked
- X48-stop-runs -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X48-stop-runs -1 ASIA: unlocked
- X48-stop-runs -1 LONDON: unlocked
- X48-stop-runs -1 NY: unlocked
- X48-stop-runs -1 POOLED: unlocked
- X48-stop-runs -1 ASIA: unlocked
- X48-stop-runs -1 LONDON: unlocked
- X48-stop-runs -1 NY: unlocked
- X48-stop-runs -1 POOLED: unlocked
- X48-stop-runs -1 ASIA: unlocked
- X48-stop-runs -1 LONDON: unlocked
- X48-stop-runs -1 NY: unlocked
- X48-stop-runs -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X48-stop-runs -1 ASIA: unlocked
- X48-stop-runs -1 LONDON: unlocked
- X48-stop-runs -1 NY: unlocked
- X48-stop-runs -1 POOLED: unlocked
- X48-stop-runs -1 ASIA: unlocked
- X48-stop-runs -1 LONDON: unlocked
- X48-stop-runs -1 NY: unlocked
- X48-stop-runs -1 POOLED: unlocked
- X48-stop-runs -1 ASIA: unlocked
- X48-stop-runs -1 LONDON: unlocked
- X48-stop-runs -1 NY: unlocked
- X49-stop-dist-quantiles -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X49-stop-dist-quantiles -1 ASIA: unlocked
- X49-stop-dist-quantiles -1 LONDON: unlocked
- X49-stop-dist-quantiles -1 NY: unlocked
- X49-stop-dist-quantiles -1 POOLED: unlocked
- X49-stop-dist-quantiles -1 ASIA: unlocked
- X49-stop-dist-quantiles -1 LONDON: unlocked
- X49-stop-dist-quantiles -1 NY: unlocked
- X49-stop-dist-quantiles -1 POOLED: unlocked
- X49-stop-dist-quantiles -1 ASIA: unlocked
- X49-stop-dist-quantiles -1 LONDON: unlocked
- X49-stop-dist-quantiles -1 NY: unlocked
- X49-stop-dist-quantiles -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X49-stop-dist-quantiles -1 ASIA: unlocked
- X49-stop-dist-quantiles -1 LONDON: unlocked
- X49-stop-dist-quantiles -1 NY: unlocked
- X49-stop-dist-quantiles -1 POOLED: unlocked
- X49-stop-dist-quantiles -1 ASIA: unlocked
- X49-stop-dist-quantiles -1 LONDON: unlocked
- X49-stop-dist-quantiles -1 NY: unlocked
- X49-stop-dist-quantiles -1 POOLED: unlocked
- X49-stop-dist-quantiles -1 ASIA: unlocked
- X49-stop-dist-quantiles -1 LONDON: unlocked
- X49-stop-dist-quantiles -1 NY: unlocked
- X50-entry-bar-shape -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X50-entry-bar-shape -1 ASIA: unlocked
- X50-entry-bar-shape -1 LONDON: unlocked
- X50-entry-bar-shape -1 NY: unlocked
- X50-entry-bar-shape -1 POOLED: unlocked
- X50-entry-bar-shape -1 ASIA: unlocked
- X50-entry-bar-shape -1 LONDON: unlocked
- X50-entry-bar-shape -1 NY: unlocked
- X50-entry-bar-shape -1 POOLED: unlocked
- X50-entry-bar-shape -1 ASIA: unlocked
- X50-entry-bar-shape -1 LONDON: unlocked
- X50-entry-bar-shape -1 NY: unlocked
- X50-entry-bar-shape -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X50-entry-bar-shape -1 ASIA: unlocked
- X50-entry-bar-shape -1 LONDON: unlocked
- X50-entry-bar-shape -1 NY: unlocked
- X50-entry-bar-shape -1 POOLED: unlocked
- X50-entry-bar-shape -1 ASIA: unlocked
- X50-entry-bar-shape -1 LONDON: unlocked
- X50-entry-bar-shape -1 NY: unlocked
- X50-entry-bar-shape -1 POOLED: unlocked
- X50-entry-bar-shape -1 ASIA: unlocked
- X50-entry-bar-shape -1 LONDON: unlocked
- X50-entry-bar-shape -1 NY: unlocked
- X51-confirmation-timing -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X51-confirmation-timing -1 ASIA: unlocked
- X51-confirmation-timing -1 LONDON: unlocked
- X51-confirmation-timing -1 NY: unlocked
- X51-confirmation-timing -1 POOLED: unlocked
- X51-confirmation-timing -1 ASIA: unlocked
- X51-confirmation-timing -1 LONDON: unlocked
- X51-confirmation-timing -1 NY: unlocked
- X51-confirmation-timing -1 POOLED: unlocked
- X51-confirmation-timing -1 ASIA: unlocked
- X51-confirmation-timing -1 LONDON: unlocked
- X51-confirmation-timing -1 NY: unlocked
- X51-confirmation-timing -1 POOLED: unlocked; econ not run (holdout stop_vs_target AUC < 0.58)
- X51-confirmation-timing -1 ASIA: unlocked
- X51-confirmation-timing -1 LONDON: unlocked
- X51-confirmation-timing -1 NY: unlocked
- X51-confirmation-timing -1 POOLED: unlocked
- X51-confirmation-timing -1 ASIA: unlocked
- X51-confirmation-timing -1 LONDON: unlocked
- X51-confirmation-timing -1 NY: unlocked
- X51-confirmation-timing -1 POOLED: unlocked
- X51-confirmation-timing -1 ASIA: unlocked
- X51-confirmation-timing -1 LONDON: unlocked
- X51-confirmation-timing -1 NY: unlocked
