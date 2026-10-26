# PRED ROUND 78 - block X1 round 7 - X31-X32

Best HOLDOUT F-R AUC: +15 POOLED 0.547 [0.51,0.59] | ASIA 0.547 [0.49,0.60] | LONDON 0.570 [0.51,0.63] | NY 0.516 [0.45,0.59]
Best HOLDOUT F-R AUC: +30 POOLED 0.519 [0.49,0.55] | ASIA 0.531 [0.47,0.59] | LONDON 0.475 [0.41,0.55] | NY 0.491 [0.42,0.56]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.099 AUC, 5 of 5 economic conditions short.
not found - short by 0.099 AUC and 5 of 5 economic conditions

prereg 075de2dd570485d33d34d5e2d1e9fcdb65232d0f3b0ff61ff800ea6ab4b1ab53 ; trials added 700 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X4u_round5.parquet', 'l2vast/pred/store/X5u_round5.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X32-perbook | +15 | LONDON | bkavg_pair | 0.526 [0.48,0.57] | 0.570 [0.51,0.63] | - | 0.566 | 0.562 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +20 | ASIA | plac0_gbt3 | 0.521 [0.48,0.57] | 0.561 [0.50,0.62] | - | 0.558 | 0.564 | N | - | - | - | - |  | short by 0.099 AUC, 5 of 5 econ |
| X32-perbook | +20 | NY | bkavg_pair | 0.519 [0.48,0.56] | 0.558 [0.49,0.62] | - | 0.561 | 0.554 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | pre | NY | bkavg_logit2 | 0.520 [0.48,0.56] | 0.558 [0.50,0.61] | - | 0.567 | 0.556 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +45 | ASIA | plac1_gbt3 | 0.539 [0.50,0.58] | 0.556 [0.50,0.61] | - | 0.547 | 0.553 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +60 | ASIA | plac2_gbt3 | 0.505 [0.46,0.56] | 0.556 [0.48,0.64] | - | 0.564 | 0.557 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +20 | ASIA | plac2_gbt3 | 0.547 [0.51,0.59] | 0.555 [0.50,0.61] | - | 0.545 | 0.554 | N | - | - | - | - |  | short by 0.105 AUC, 5 of 5 econ |
| X31-placebo-control | +45 | ASIA | plac0_pair | 0.509 [0.47,0.56] | 0.554 [0.49,0.61] | - | 0.550 | 0.546 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +45 | ASIA | plac1_pair | 0.557 [0.51,0.60] | 0.551 [0.49,0.61] | - | 0.548 | 0.553 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +10 | POOLED | plac1_gbt3 | 0.511 [0.49,0.54] | 0.550 [0.51,0.59] | - | 0.554 | 0.552 | N | - | - | - | - |  | promising: short by 0.130 AUC, 5 of 5 econ |
| X31-placebo-control | +45 | POOLED | plac0_pair | 0.513 [0.49,0.54] | 0.547 [0.51,0.58] | - | 0.547 | 0.538 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +15 | ASIA | plac0_gbt3 | 0.513 [0.47,0.56] | 0.547 [0.49,0.60] | - | 0.543 | 0.545 | N | - | - | - | - |  | short by 0.113 AUC, 5 of 5 econ |
| X32-perbook | +15 | POOLED | bkavg_pair | 0.514 [0.49,0.54] | 0.547 [0.51,0.59] | - | 0.547 | 0.545 | N | - | - | - | - |  | promising: short by 0.133 AUC, 5 of 5 econ |
| X31-placebo-control | +45 | POOLED | plac2_gbt3 | 0.525 [0.50,0.55] | 0.544 [0.51,0.58] | - | 0.543 | 0.532 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +20 | POOLED | plac0_pair | 0.523 [0.50,0.55] | 0.543 [0.51,0.58] | - | 0.540 | 0.540 | N | - | - | - | - |  | short by 0.137 AUC, 5 of 5 econ |
| X32-perbook | +20 | LONDON | bkavg_pair | 0.525 [0.48,0.56] | 0.541 [0.48,0.60] | - | 0.550 | 0.538 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | pre | ASIA | plac2_gbt3 | 0.503 [0.46,0.55] | 0.541 [0.48,0.60] | - | 0.541 | 0.541 | N | - | - | - | - |  | short by 0.119 AUC, 5 of 5 econ |
| X32-perbook | +20 | ASIA | bkavg_logit2 | 0.535 [0.50,0.58] | 0.541 [0.48,0.60] | - | 0.538 | 0.548 | N | - | - | - | - |  | short by 0.119 AUC, 5 of 5 econ |
| X31-placebo-control | +45 | POOLED | plac2_pair | 0.536 [0.51,0.56] | 0.540 [0.50,0.57] | - | 0.539 | 0.534 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | +45 | ASIA | bkavg_logit2 | 0.518 [0.48,0.56] | 0.538 [0.47,0.60] | - | 0.534 | 0.556 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | +10 | LONDON | bkavg_gbt3 | 0.513 [0.47,0.56] | 0.537 [0.47,0.60] | - | 0.531 | 0.540 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +20 | ASIA | plac2_pair | 0.533 [0.49,0.58] | 0.536 [0.48,0.59] | - | 0.527 | 0.539 | N | - | - | - | - |  | short by 0.124 AUC, 5 of 5 econ |
| X32-perbook | +20 | POOLED | bkavg_pair | 0.513 [0.49,0.54] | 0.535 [0.50,0.57] | - | 0.538 | 0.534 | N | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| X31-placebo-control | +10 | ASIA | plac1_gbt3 | 0.486 [0.44,0.53] | 0.534 [0.47,0.60] | - | 0.537 | 0.536 | N | - | - | - | - |  | short by 0.126 AUC, 5 of 5 econ |
| X31-placebo-control | pre | ASIA | plac2_pair | 0.531 [0.49,0.57] | 0.534 [0.48,0.58] | - | 0.523 | 0.533 | N | - | - | - | - |  | short by 0.126 AUC, 5 of 5 econ |
| X31-placebo-control | +45 | POOLED | plac1_gbt3 | 0.517 [0.50,0.54] | 0.533 [0.50,0.57] | - | 0.531 | 0.535 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +10 | POOLED | plac1_pair | 0.516 [0.49,0.54] | 0.533 [0.50,0.57] | - | 0.535 | 0.538 | N | - | - | - | - |  | short by 0.147 AUC, 5 of 5 econ |
| X31-placebo-control | +30 | ASIA | plac0_gbt3 | 0.524 [0.48,0.57] | 0.531 [0.47,0.59] | - | 0.520 | 0.531 | N | - | - | - | - |  | short by 0.129 AUC, 5 of 5 econ |
| X31-placebo-control | +60 | ASIA | plac2_pair | 0.504 [0.45,0.55] | 0.528 [0.47,0.59] | - | 0.533 | 0.530 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +60 | POOLED | plac2_gbt3 | 0.521 [0.50,0.55] | 0.528 [0.49,0.57] | - | 0.530 | 0.523 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +10 | POOLED | plac0_gbt3 | 0.511 [0.49,0.54] | 0.527 [0.49,0.56] | - | 0.526 | 0.516 | N | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| X31-placebo-control | +15 | POOLED | plac0_gbt3 | 0.517 [0.49,0.54] | 0.526 [0.48,0.56] | - | 0.526 | 0.523 | N | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| X31-placebo-control | +10 | ASIA | plac2_gbt3 | 0.505 [0.46,0.55] | 0.525 [0.46,0.58] | - | 0.536 | 0.523 | N | - | - | - | - |  | short by 0.135 AUC, 5 of 5 econ |
| X31-placebo-control | +20 | POOLED | plac0_gbt3 | 0.510 [0.48,0.53] | 0.523 [0.49,0.56] | - | 0.523 | 0.523 | N | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| X31-placebo-control | +20 | POOLED | plac2_pair | 0.513 [0.49,0.54] | 0.521 [0.49,0.55] | - | 0.523 | 0.526 | N | - | - | - | - |  | short by 0.159 AUC, 5 of 5 econ |
| X31-placebo-control | +45 | ASIA | plac0_gbt3 | 0.506 [0.46,0.55] | 0.521 [0.46,0.58] | - | 0.511 | 0.520 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +45 | ASIA | plac2_gbt3 | 0.504 [0.46,0.55] | 0.520 [0.46,0.58] | - | 0.522 | 0.504 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +20 | POOLED | plac2_gbt3 | 0.516 [0.49,0.54] | 0.520 [0.48,0.55] | - | 0.520 | 0.519 | N | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| X31-placebo-control | +20 | ASIA | plac1_pair | 0.511 [0.47,0.55] | 0.519 [0.46,0.57] | - | 0.520 | 0.515 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +30 | POOLED | plac0_gbt3 | 0.511 [0.49,0.53] | 0.519 [0.49,0.55] | - | 0.515 | 0.514 | N | - | - | - | - |  | promising: short by 0.161 AUC, 5 of 5 econ |
| X31-placebo-control | pre | POOLED | plac2_gbt3 | 0.508 [0.49,0.53] | 0.519 [0.48,0.55] | - | 0.520 | 0.522 | N | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| X31-placebo-control | +60 | ASIA | plac1_gbt3 | 0.503 [0.46,0.55] | 0.519 [0.45,0.58] | - | 0.515 | 0.517 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +30 | POOLED | plac0_pair | 0.498 [0.48,0.52] | 0.519 [0.49,0.55] | - | 0.518 | 0.516 | N | - | - | - | - |  | promising: short by 0.161 AUC, 5 of 5 econ |
| X31-placebo-control | +45 | POOLED | plac1_pair | 0.508 [0.48,0.53] | 0.517 [0.48,0.55] | - | 0.516 | 0.510 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +60 | POOLED | plac0_gbt3 | 0.516 [0.49,0.54] | 0.517 [0.47,0.56] | - | 0.514 | 0.507 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +30 | POOLED | plac1_pair | 0.511 [0.49,0.53] | 0.516 [0.49,0.55] | - | 0.515 | 0.519 | N | - | - | - | - |  | promising: short by 0.164 AUC, 5 of 5 econ |
| X32-perbook | +15 | NY | bkavg_logit2 | 0.500 [0.46,0.54] | 0.516 [0.45,0.59] | - | 0.511 | 0.511 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +10 | ASIA | plac0_gbt3 | 0.512 [0.47,0.55] | 0.515 [0.46,0.57] | - | 0.513 | 0.511 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | pre | POOLED | plac1_pair | 0.512 [0.49,0.54] | 0.514 [0.48,0.55] | - | 0.512 | 0.507 | N | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| X31-placebo-control | +30 | POOLED | plac1_gbt3 | 0.515 [0.49,0.54] | 0.514 [0.48,0.55] | - | 0.512 | 0.513 | N | - | - | - | - |  | promising: short by 0.166 AUC, 5 of 5 econ |
| X32-perbook | +10 | NY | bkavg_logit2 | 0.509 [0.47,0.55] | 0.514 [0.45,0.58] | - | 0.509 | 0.509 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | pre | ASIA | bkavg_gbt3 | 0.542 [0.51,0.58] | 0.512 [0.46,0.56] | - | 0.499 | 0.515 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +15 | ASIA | plac1_pair | 0.489 [0.44,0.53] | 0.512 [0.45,0.57] | - | 0.504 | 0.516 | N | - | - | - | - |  | short by 0.148 AUC, 5 of 5 econ |
| X31-placebo-control | +20 | ASIA | plac0_pair | 0.489 [0.45,0.53] | 0.512 [0.46,0.56] | - | 0.509 | 0.513 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +30 | ASIA | plac0_pair | 0.491 [0.45,0.53] | 0.512 [0.44,0.58] | - | 0.504 | 0.516 | N | - | - | - | - |  | short by 0.148 AUC, 5 of 5 econ |
| X32-perbook | +45 | POOLED | bkavg_pair | 0.496 [0.47,0.52] | 0.511 [0.47,0.55] | - | 0.510 | 0.524 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +10 | POOLED | plac2_pair | 0.514 [0.49,0.54] | 0.511 [0.47,0.55] | - | 0.511 | 0.512 | N | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| X31-placebo-control | +30 | POOLED | plac2_pair | 0.507 [0.48,0.53] | 0.511 [0.48,0.54] | - | 0.509 | 0.510 | N | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| X31-placebo-control | +15 | POOLED | plac1_pair | 0.483 [0.46,0.51] | 0.510 [0.47,0.55] | - | 0.508 | 0.510 | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| X31-placebo-control | +30 | ASIA | plac1_gbt3 | 0.521 [0.47,0.57] | 0.510 [0.44,0.57] | - | 0.506 | 0.515 | N | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| X31-placebo-control | +5 | POOLED | plac1_pair | 0.501 [0.48,0.53] | 0.509 [0.47,0.55] | - | 0.509 | 0.506 | N | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| X31-placebo-control | +10 | POOLED | plac0_pair | 0.496 [0.47,0.52] | 0.509 [0.48,0.54] | - | 0.509 | 0.501 | N | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| X31-placebo-control | +60 | POOLED | plac0_pair | 0.508 [0.48,0.53] | 0.509 [0.47,0.55] | - | 0.507 | 0.504 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | pre | POOLED | plac1_gbt3 | 0.513 [0.49,0.54] | 0.508 [0.47,0.55] | - | 0.507 | 0.501 | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| X31-placebo-control | +20 | POOLED | plac1_pair | 0.492 [0.47,0.52] | 0.507 [0.47,0.54] | - | 0.503 | 0.503 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | pre | POOLED | plac0_pair | 0.497 [0.47,0.52] | 0.506 [0.47,0.54] | - | 0.504 | 0.504 | N | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| X31-placebo-control | +30 | POOLED | plac2_gbt3 | 0.509 [0.48,0.53] | 0.505 [0.47,0.54] | - | 0.504 | 0.501 | N | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| X32-perbook | +10 | POOLED | bkavg_logit2 | 0.497 [0.47,0.52] | 0.505 [0.47,0.54] | - | 0.504 | 0.504 | N | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| X31-placebo-control | +5 | ASIA | plac0_gbt3 | 0.537 [0.50,0.58] | 0.504 [0.46,0.55] | - | 0.495 | 0.502 | N | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| X31-placebo-control | +5 | ASIA | plac1_pair | 0.498 [0.46,0.54] | 0.504 [0.45,0.55] | - | 0.503 | 0.504 | N | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| X31-placebo-control | +10 | ASIA | plac1_pair | 0.493 [0.45,0.53] | 0.504 [0.44,0.56] | - | 0.501 | 0.508 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +10 | ASIA | plac0_pair | 0.494 [0.45,0.54] | 0.504 [0.45,0.56] | - | 0.494 | 0.502 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +15 | POOLED | plac1_gbt3 | 0.478 [0.45,0.51] | 0.503 [0.47,0.54] | - | 0.504 | 0.502 | N | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| X31-placebo-control | +5 | POOLED | plac0_pair | 0.518 [0.49,0.54] | 0.503 [0.47,0.54] | - | 0.502 | 0.502 | N | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| X31-placebo-control | +60 | POOLED | plac1_gbt3 | 0.482 [0.46,0.51] | 0.503 [0.46,0.54] | - | 0.503 | 0.498 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +15 | POOLED | plac0_pair | 0.510 [0.48,0.54] | 0.503 [0.46,0.54] | - | 0.504 | 0.501 | N | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| X31-placebo-control | +5 | POOLED | plac1_gbt3 | 0.496 [0.47,0.52] | 0.502 [0.47,0.54] | - | 0.502 | 0.499 | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| X32-perbook | +60 | ASIA | bkavg_logit2 | 0.511 [0.46,0.56] | 0.501 [0.44,0.56] | - | 0.498 | 0.505 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +45 | ASIA | plac2_pair | 0.493 [0.45,0.53] | 0.501 [0.44,0.56] | - | 0.509 | 0.497 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | pre | POOLED | plac0_gbt3 | 0.491 [0.46,0.52] | 0.501 [0.46,0.54] | - | 0.499 | 0.497 | N | - | - | - | - |  | short by 0.179 AUC, 5 of 5 econ |
| X31-placebo-control | +10 | ASIA | plac2_pair | 0.527 [0.49,0.56] | 0.501 [0.45,0.56] | - | 0.504 | 0.502 | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-perbook | pre | LONDON | bkavg_pair | 0.506 [0.46,0.55] | 0.501 [0.43,0.57] | - | 0.503 | 0.502 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +15 | POOLED | plac2_pair | 0.506 [0.48,0.53] | 0.501 [0.46,0.54] | - | 0.498 | 0.494 | N | - | - | - | - |  | short by 0.179 AUC, 5 of 5 econ |
| X32-perbook | pre | POOLED | bkavg_pair | 0.508 [0.48,0.54] | 0.500 [0.46,0.54] | - | 0.500 | 0.501 | N | - | - | - | - |  | short by 0.180 AUC, 5 of 5 econ |
| X31-placebo-control | pre | ASIA | plac1_pair | 0.470 [0.43,0.51] | 0.499 [0.45,0.54] | - | 0.493 | 0.498 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +5 | POOLED | plac0_gbt3 | 0.514 [0.49,0.54] | 0.499 [0.47,0.53] | - | 0.494 | 0.493 | N | - | - | - | - |  | short by 0.181 AUC, 5 of 5 econ |
| X31-placebo-control | +45 | POOLED | plac0_gbt3 | 0.494 [0.47,0.52] | 0.499 [0.46,0.53] | - | 0.496 | 0.495 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +60 | ASIA | plac0_pair | 0.533 [0.48,0.58] | 0.498 [0.43,0.56] | - | 0.499 | 0.499 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | +45 | NY | bkavg_pair | 0.483 [0.43,0.53] | 0.498 [0.43,0.56] | - | 0.503 | 0.509 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | pre | ASIA | plac0_pair | 0.514 [0.48,0.55] | 0.497 [0.45,0.55] | - | 0.490 | 0.499 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +60 | POOLED | plac2_pair | 0.513 [0.49,0.54] | 0.496 [0.46,0.53] | - | 0.496 | 0.493 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | +30 | ASIA | bkavg_logit2 | 0.505 [0.46,0.55] | 0.493 [0.43,0.56] | - | 0.489 | 0.503 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +5 | ASIA | plac2_pair | 0.497 [0.46,0.54] | 0.492 [0.44,0.54] | - | 0.484 | 0.491 | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-perbook | +30 | NY | bkavg_logit2 | 0.499 [0.46,0.54] | 0.491 [0.42,0.56] | - | 0.505 | 0.488 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | +5 | POOLED | bkavg_pair | 0.492 [0.47,0.52] | 0.491 [0.46,0.53] | - | 0.491 | 0.493 | N | - | - | - | - |  | short by 0.189 AUC, 5 of 5 econ |
| X31-placebo-control | +10 | POOLED | plac2_gbt3 | 0.485 [0.46,0.51] | 0.491 [0.45,0.53] | - | 0.491 | 0.488 | N | - | - | - | - |  | short by 0.189 AUC, 5 of 5 econ |
| X32-perbook | +30 | POOLED | bkavg_gbt3 | 0.490 [0.47,0.51] | 0.490 [0.45,0.53] | - | 0.489 | 0.494 | N | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| X31-placebo-control | +20 | POOLED | plac1_gbt3 | 0.485 [0.46,0.51] | 0.488 [0.46,0.52] | - | 0.483 | 0.482 | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-perbook | +5 | LONDON | bkavg_pair | 0.495 [0.45,0.54] | 0.487 [0.42,0.56] | - | 0.488 | 0.496 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | +5 | ASIA | bkavg_pair | 0.493 [0.45,0.54] | 0.487 [0.43,0.55] | - | 0.478 | 0.488 | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-perbook | +45 | LONDON | bkavg_pair | 0.495 [0.46,0.54] | 0.486 [0.43,0.54] | - | 0.489 | 0.499 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +5 | POOLED | plac2_gbt3 | 0.497 [0.47,0.52] | 0.486 [0.45,0.52] | - | 0.484 | 0.479 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +60 | ASIA | plac1_pair | 0.504 [0.46,0.55] | 0.485 [0.43,0.55] | - | 0.485 | 0.492 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +5 | ASIA | plac0_pair | 0.544 [0.50,0.58] | 0.484 [0.43,0.54] | - | 0.478 | 0.481 | N | - | - | - | - |  | WF-only (dead) |
| X31-placebo-control | +15 | POOLED | plac2_gbt3 | 0.491 [0.46,0.52] | 0.483 [0.44,0.52] | - | 0.479 | 0.477 | N | - | - | - | - |  | short by 0.197 AUC, 5 of 5 econ |
| X31-placebo-control | +15 | ASIA | plac0_pair | 0.505 [0.46,0.55] | 0.483 [0.42,0.55] | - | 0.476 | 0.486 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +15 | ASIA | plac1_gbt3 | 0.481 [0.44,0.53] | 0.482 [0.42,0.54] | - | 0.482 | 0.485 | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-perbook | +5 | NY | bkavg_gbt3 | 0.499 [0.46,0.54] | 0.480 [0.42,0.55] | - | 0.483 | 0.479 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | pre | ASIA | plac1_gbt3 | 0.482 [0.44,0.52] | 0.479 [0.42,0.54] | - | 0.479 | 0.482 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +60 | ASIA | plac0_gbt3 | 0.517 [0.46,0.57] | 0.479 [0.41,0.54] | - | 0.473 | 0.476 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | pre | POOLED | plac2_pair | 0.492 [0.47,0.52] | 0.479 [0.44,0.51] | - | 0.477 | 0.479 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +30 | ASIA | plac1_pair | 0.505 [0.46,0.55] | 0.478 [0.43,0.53] | - | 0.477 | 0.491 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +5 | POOLED | plac2_pair | 0.504 [0.48,0.53] | 0.478 [0.44,0.52] | - | 0.474 | 0.471 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +5 | ASIA | plac1_gbt3 | 0.491 [0.45,0.53] | 0.477 [0.43,0.53] | - | 0.469 | 0.478 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +60 | POOLED | plac1_pair | 0.476 [0.45,0.50] | 0.476 [0.44,0.51] | - | 0.474 | 0.476 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | +30 | LONDON | bkavg_pair | 0.478 [0.43,0.53] | 0.475 [0.41,0.55] | - | 0.478 | 0.486 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +30 | ASIA | plac2_pair | 0.488 [0.45,0.53] | 0.474 [0.41,0.54] | - | 0.459 | 0.475 | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-perbook | +60 | POOLED | bkavg_gbt3 | 0.492 [0.47,0.52] | 0.473 [0.44,0.50] | - | 0.471 | 0.471 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | +10 | ASIA | bkavg_logit2 | 0.504 [0.46,0.55] | 0.472 [0.42,0.52] | - | 0.467 | 0.478 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | pre | ASIA | plac0_gbt3 | 0.502 [0.46,0.54] | 0.470 [0.41,0.53] | - | 0.453 | 0.471 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +15 | ASIA | plac2_gbt3 | 0.488 [0.44,0.53] | 0.469 [0.41,0.53] | - | 0.462 | 0.472 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +30 | ASIA | plac2_gbt3 | 0.507 [0.46,0.55] | 0.469 [0.41,0.54] | - | 0.463 | 0.465 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +15 | ASIA | plac2_pair | 0.502 [0.46,0.54] | 0.467 [0.41,0.52] | - | 0.466 | 0.468 | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-perbook | +60 | LONDON | bkavg_pair | 0.498 [0.46,0.54] | 0.464 [0.41,0.53] | - | 0.455 | 0.449 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32-perbook | +15 | ASIA | bkavg_gbt3 | 0.488 [0.45,0.53] | 0.458 [0.41,0.51] | - | 0.457 | 0.462 | N | - | - | - | - |  | dead (no gain over baseline) |
| X32-perbook | +60 | NY | bkavg_pair | 0.470 [0.43,0.51] | 0.452 [0.40,0.51] | - | 0.444 | 0.451 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31-placebo-control | +20 | ASIA | plac1_gbt3 | 0.456 [0.41,0.50] | 0.445 [0.38,0.50] | - | 0.433 | 0.441 | N | - | - | - | - |  | dead (no gain over baseline) |
| X31-placebo-control | +5 | ASIA | plac2_gbt3 | 0.481 [0.44,0.52] | 0.435 [0.38,0.49] | - | 0.429 | 0.437 | N | - | - | - | - |  | dead (no gain over baseline) |

One-sentence notes:
- X31-placebo-control 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X31-placebo-control 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X32-perbook 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
