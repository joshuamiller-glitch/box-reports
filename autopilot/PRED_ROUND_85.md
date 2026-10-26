# PRED ROUND 85 - block K round 9 - K9-I5-stack

Best HOLDOUT F-R AUC: +15 POOLED 0.512 [0.48,0.55] | ASIA 0.571 [0.51,0.63] | LONDON 0.517 [0.46,0.58] | NY 0.456 [0.39,0.52]
Best HOLDOUT F-R AUC: +30 POOLED 0.518 [0.48,0.56] | ASIA 0.586 [0.52,0.65] | LONDON 0.504 [0.44,0.57] | NY 0.452 [0.39,0.52]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.074 AUC, 5 of 5 economic conditions short.
not found - short by 0.074 AUC and 5 of 5 economic conditions

prereg 949906ed12d7a63644ed6703f8a27140f6d32f5a426253b1489ec798c94f009a ; trials added 1800 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K9-S_I5 | +30 | ASIA | S_I5 | 0.573 [0.54,0.61] | 0.586 [0.52,0.65] | - | 0.587 | - | - | - | - | - | - |  | short by 0.074 AUC, 5 of 5 econ |
| K9-S_I5 | +15 | ASIA | S_I5 | 0.547 [0.51,0.59] | 0.571 [0.51,0.63] | - | 0.566 | - | - | - | - | - | - |  | short by 0.089 AUC, 5 of 5 econ |
| K9-S_I5 | +5 | ASIA | S_I5 | 0.550 [0.51,0.59] | 0.556 [0.49,0.61] | - | 0.550 | - | - | - | - | - | - |  | short by 0.104 AUC, 5 of 5 econ |
| K9-S_I5B | +15 | ASIA | S_I5B | 0.546 [0.51,0.58] | 0.556 [0.50,0.62] | - | 0.543 | - | - | - | - | - | - | stack | short by 0.104 AUC, 5 of 5 econ |
| K9-S_I5B | +45 | ASIA | S_I5B | 0.551 [0.51,0.59] | 0.546 [0.49,0.61] | - | 0.555 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +30 | ASIA | S_AVG2 | 0.545 [0.51,0.58] | 0.546 [0.49,0.61] | - | 0.541 | - | - | - | - | - | - | stack | short by 0.114 AUC, 5 of 5 econ |
| K9-S_I5B | pre | ASIA | S_I5B | 0.550 [0.52,0.58] | 0.544 [0.49,0.59] | - | 0.536 | - | - | - | - | - | - | stack | short by 0.116 AUC, 5 of 5 econ |
| K9-S_AVG2 | +20 | ASIA | S_AVG2 | 0.558 [0.52,0.60] | 0.542 [0.49,0.59] | - | 0.529 | - | - | - | - | - | - | stack | short by 0.118 AUC, 5 of 5 econ |
| K9-S_AVG2 | +45 | ASIA | S_AVG2 | 0.535 [0.49,0.58] | 0.541 [0.48,0.60] | - | 0.544 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +20 | ASIA | S_I5 | 0.559 [0.52,0.60] | 0.540 [0.48,0.60] | - | 0.538 | - | - | - | - | - | - |  | short by 0.120 AUC, 5 of 5 econ |
| K9-S_I5T3 | +30 | ASIA | S_I5T3 | 0.563 [0.52,0.60] | 0.540 [0.48,0.60] | - | 0.527 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| K9-S_I5B | +60 | ASIA | S_I5B | 0.559 [0.52,0.61] | 0.540 [0.47,0.61] | - | 0.535 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +15 | ASIA | S_AVG2 | 0.542 [0.51,0.58] | 0.539 [0.48,0.60] | - | 0.525 | - | - | - | - | - | - | stack | short by 0.121 AUC, 5 of 5 econ |
| K9-S_I5 | +45 | ASIA | S_I5 | 0.541 [0.50,0.58] | 0.538 [0.48,0.60] | - | 0.533 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +15 | ASIA | S_I5T3 | 0.551 [0.52,0.59] | 0.525 [0.46,0.59] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| K9-S_AVG2 | +5 | ASIA | S_AVG2 | 0.536 [0.50,0.57] | 0.525 [0.47,0.58] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| K9-S_I5 | +10 | ASIA | S_I5 | 0.546 [0.51,0.58] | 0.524 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - |  | short by 0.136 AUC, 5 of 5 econ |
| K9-S_I5T3 | +10 | ASIA | S_I5T3 | 0.553 [0.52,0.59] | 0.521 [0.46,0.58] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.139 AUC, 5 of 5 econ |
| K9-S_I5B | +10 | ASIA | S_I5B | 0.553 [0.51,0.60] | 0.520 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_AVG2 | +10 | ASIA | S_AVG2 | 0.550 [0.52,0.59] | 0.519 [0.45,0.58] | - | 0.510 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5T3 | +45 | ASIA | S_I5T3 | 0.536 [0.49,0.57] | 0.518 [0.45,0.58] | - | 0.505 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +30 | POOLED | S_I5 | 0.518 [0.49,0.54] | 0.518 [0.48,0.56] | - | 0.519 | - | - | - | - | - | - |  | promising: short by 0.162 AUC, 5 of 5 econ |
| K9-S_I5B | +5 | LONDON | S_I5B | 0.532 [0.49,0.58] | 0.517 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +30 | ASIA | S_I5B | 0.518 [0.48,0.55] | 0.517 [0.46,0.57] | - | 0.505 | - | - | - | - | - | - | stack | short by 0.143 AUC, 5 of 5 econ |
| K9-S_T10 | +5 | ASIA | S_T10 | 0.534 [0.50,0.57] | 0.517 [0.46,0.57] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.143 AUC, 5 of 5 econ |
| K9-S_I5B | +15 | LONDON | S_I5B | 0.524 [0.48,0.57] | 0.517 [0.46,0.58] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +45 | ASIA | S_T10 | 0.545 [0.51,0.58] | 0.516 [0.45,0.57] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | pre | LONDON | S_I5B | 0.516 [0.47,0.56] | 0.515 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +15 | POOLED | S_I5B | 0.521 [0.50,0.55] | 0.512 [0.48,0.55] | - | 0.507 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| K9-S_I5B | pre | POOLED | S_I5B | 0.507 [0.48,0.53] | 0.512 [0.47,0.55] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| K9-S_T10 | +30 | ASIA | S_T10 | 0.554 [0.52,0.59] | 0.511 [0.45,0.57] | - | 0.489 | - | - | - | - | - | - | stack | short by 0.149 AUC, 5 of 5 econ |
| K9-S_AVG2 | +60 | ASIA | S_AVG2 | 0.521 [0.48,0.57] | 0.511 [0.44,0.58] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +20 | ASIA | S_base | 0.541 [0.50,0.58] | 0.511 [0.45,0.57] | - | 0.491 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5 | +60 | ASIA | S_I5 | 0.535 [0.49,0.58] | 0.511 [0.44,0.58] | - | 0.509 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +10 | ASIA | S_T10 | 0.554 [0.52,0.59] | 0.510 [0.44,0.58] | - | 0.507 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_base | pre | ASIA | S_base | 0.534 [0.50,0.57] | 0.510 [0.45,0.57] | - | 0.490 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_T10 | +15 | ASIA | S_T10 | 0.549 [0.51,0.59] | 0.509 [0.45,0.57] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| K9-S_I5 | +15 | POOLED | S_I5 | 0.519 [0.49,0.54] | 0.509 [0.48,0.54] | - | 0.508 | - | - | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| K9-S_base | +20 | LONDON | S_base | 0.481 [0.43,0.53] | 0.507 [0.44,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +20 | NY | S_I5B | 0.497 [0.45,0.54] | 0.506 [0.43,0.57] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +5 | ASIA | S_I5T3 | 0.536 [0.50,0.57] | 0.505 [0.45,0.57] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| K9-S_T10 | +20 | ASIA | S_T10 | 0.547 [0.51,0.58] | 0.505 [0.44,0.56] | - | 0.497 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5 | +30 | LONDON | S_I5 | 0.494 [0.45,0.54] | 0.504 [0.44,0.57] | - | 0.509 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +20 | POOLED | S_I5B | 0.515 [0.49,0.54] | 0.503 [0.47,0.53] | - | 0.500 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5B | +5 | ASIA | S_I5B | 0.529 [0.49,0.57] | 0.502 [0.44,0.56] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| K9-S_base | +60 | ASIA | S_base | 0.510 [0.46,0.56] | 0.502 [0.44,0.57] | - | 0.478 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +10 | ASIA | S_base | 0.539 [0.50,0.58] | 0.501 [0.44,0.57] | - | 0.490 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5 | +15 | LONDON | S_I5 | 0.517 [0.47,0.56] | 0.501 [0.44,0.56] | - | 0.498 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +20 | ASIA | S_I5B | 0.545 [0.51,0.58] | 0.499 [0.44,0.56] | - | 0.489 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5T3 | pre | ASIA | S_I5T3 | 0.552 [0.51,0.59] | 0.499 [0.44,0.56] | - | 0.483 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5B | +10 | LONDON | S_I5B | 0.509 [0.46,0.56] | 0.499 [0.43,0.57] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +60 | ASIA | S_I5T3 | 0.531 [0.49,0.58] | 0.498 [0.43,0.57] | - | 0.480 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +20 | POOLED | S_base | 0.511 [0.49,0.54] | 0.498 [0.46,0.53] | - | 0.490 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_base | +45 | ASIA | S_base | 0.505 [0.46,0.55] | 0.496 [0.43,0.56] | - | 0.494 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +10 | LONDON | S_I5 | 0.512 [0.46,0.56] | 0.495 [0.43,0.56] | - | 0.479 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +60 | ASIA | S_T10 | 0.559 [0.51,0.60] | 0.493 [0.42,0.56] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +20 | LONDON | S_I5B | 0.497 [0.45,0.54] | 0.492 [0.44,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +5 | LONDON | S_base | 0.502 [0.46,0.55] | 0.492 [0.43,0.55] | - | 0.494 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +45 | POOLED | S_I5B | 0.505 [0.48,0.53] | 0.491 [0.46,0.53] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +20 | ASIA | S_I5T3 | 0.541 [0.50,0.58] | 0.491 [0.43,0.55] | - | 0.482 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5B | +60 | POOLED | S_I5B | 0.514 [0.49,0.55] | 0.490 [0.45,0.53] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +10 | POOLED | S_I5 | 0.513 [0.49,0.54] | 0.489 [0.45,0.53] | - | 0.482 | - | - | - | - | - | - |  | short by 0.191 AUC, 5 of 5 econ |
| K9-S_AVG2 | +20 | POOLED | S_AVG2 | 0.513 [0.49,0.54] | 0.489 [0.46,0.52] | - | 0.483 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5T3 | +5 | LONDON | S_I5T3 | 0.519 [0.48,0.56] | 0.488 [0.43,0.55] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +5 | POOLED | S_I5 | 0.510 [0.49,0.54] | 0.487 [0.45,0.52] | - | 0.483 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| K9-S_I5 | +45 | POOLED | S_I5 | 0.510 [0.48,0.54] | 0.487 [0.45,0.52] | - | 0.482 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | pre | ASIA | S_AVG2 | 0.532 [0.49,0.57] | 0.486 [0.42,0.55] | - | 0.470 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_T10 | pre | ASIA | S_T10 | 0.541 [0.51,0.58] | 0.485 [0.43,0.54] | - | 0.468 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_base | +20 | NY | S_base | 0.512 [0.47,0.55] | 0.482 [0.42,0.54] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +60 | POOLED | S_base | 0.503 [0.48,0.53] | 0.482 [0.44,0.53] | - | 0.478 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +30 | POOLED | S_AVG2 | 0.500 [0.47,0.53] | 0.481 [0.44,0.52] | - | 0.482 | - | - | - | - | - | - | stack | short by 0.199 AUC, 5 of 5 econ |
| K9-S_I5B | +10 | POOLED | S_I5B | 0.507 [0.48,0.53] | 0.481 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_AVG2 | +15 | POOLED | S_AVG2 | 0.516 [0.49,0.54] | 0.481 [0.44,0.51] | - | 0.475 | - | - | - | - | - | - | stack | short by 0.199 AUC, 5 of 5 econ |
| K9-S_I5 | pre | LONDON | S_I5 | 0.503 [0.46,0.55] | 0.480 [0.42,0.54] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +60 | LONDON | S_I5B | 0.513 [0.47,0.56] | 0.480 [0.42,0.54] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +5 | POOLED | S_I5B | 0.505 [0.48,0.53] | 0.480 [0.44,0.52] | - | 0.477 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5T3 | +30 | POOLED | S_I5T3 | 0.514 [0.49,0.54] | 0.480 [0.44,0.52] | - | 0.475 | - | - | - | - | - | - | stack | short by 0.200 AUC, 5 of 5 econ |
| K9-S_base | +5 | ASIA | S_base | 0.515 [0.48,0.56] | 0.480 [0.42,0.54] | - | 0.464 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5 | +20 | POOLED | S_I5 | 0.512 [0.49,0.54] | 0.480 [0.45,0.51] | - | 0.478 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| K9-S_AVG2 | +5 | LONDON | S_AVG2 | 0.501 [0.46,0.54] | 0.478 [0.42,0.53] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +10 | LONDON | S_AVG2 | 0.505 [0.46,0.55] | 0.477 [0.41,0.54] | - | 0.464 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +10 | LONDON | S_I5T3 | 0.523 [0.48,0.57] | 0.477 [0.42,0.54] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +5 | POOLED | S_I5T3 | 0.509 [0.49,0.54] | 0.477 [0.44,0.52] | - | 0.474 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5B | pre | NY | S_I5B | 0.455 [0.41,0.50] | 0.477 [0.42,0.53] | - | 0.483 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +30 | ASIA | S_base | 0.505 [0.46,0.55] | 0.475 [0.42,0.53] | - | 0.463 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5 | +60 | POOLED | S_I5 | 0.500 [0.47,0.53] | 0.475 [0.43,0.52] | - | 0.477 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +5 | POOLED | S_AVG2 | 0.501 [0.48,0.53] | 0.475 [0.44,0.51] | - | 0.470 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_AVG2 | +20 | LONDON | S_AVG2 | 0.490 [0.44,0.54] | 0.474 [0.42,0.53] | - | 0.464 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | pre | ASIA | S_I5 | 0.526 [0.48,0.57] | 0.472 [0.41,0.54] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| K9-S_AVG2 | +10 | POOLED | S_AVG2 | 0.510 [0.48,0.54] | 0.472 [0.43,0.52] | - | 0.464 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_base | +60 | LONDON | S_base | 0.520 [0.47,0.57] | 0.471 [0.41,0.54] | - | 0.464 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +30 | POOLED | S_I5B | 0.499 [0.47,0.52] | 0.471 [0.44,0.50] | - | 0.459 | - | - | - | - | - | - | stack | short by 0.209 AUC, 5 of 5 econ |
| K9-S_I5T3 | pre | POOLED | S_I5T3 | 0.511 [0.48,0.54] | 0.471 [0.43,0.51] | - | 0.467 | - | - | - | - | - | - | stack | WF-only (dead) |
| K9-S_base | +15 | ASIA | S_base | 0.522 [0.48,0.56] | 0.470 [0.41,0.53] | - | 0.458 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_T10 | +30 | POOLED | S_T10 | 0.514 [0.49,0.54] | 0.470 [0.43,0.51] | - | 0.463 | - | - | - | - | - | - | stack | short by 0.210 AUC, 5 of 5 econ |
| K9-S_I5 | pre | POOLED | S_I5 | 0.498 [0.47,0.52] | 0.470 [0.43,0.51] | - | 0.465 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| K9-S_AVG2 | +30 | LONDON | S_AVG2 | 0.483 [0.44,0.53] | 0.469 [0.40,0.54] | - | 0.473 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +15 | POOLED | S_I5T3 | 0.518 [0.49,0.55] | 0.469 [0.43,0.51] | - | 0.464 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_AVG2 | +45 | POOLED | S_AVG2 | 0.499 [0.47,0.52] | 0.469 [0.44,0.50] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +5 | POOLED | S_base | 0.494 [0.47,0.52] | 0.469 [0.43,0.51] | - | 0.469 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_base | pre | POOLED | S_base | 0.490 [0.47,0.52] | 0.468 [0.43,0.51] | - | 0.464 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_AVG2 | +60 | POOLED | S_AVG2 | 0.503 [0.47,0.53] | 0.468 [0.43,0.52] | - | 0.466 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +30 | LONDON | S_I5T3 | 0.503 [0.46,0.55] | 0.468 [0.40,0.53] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +15 | LONDON | S_AVG2 | 0.511 [0.47,0.55] | 0.467 [0.41,0.53] | - | 0.459 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +10 | POOLED | S_I5T3 | 0.517 [0.49,0.54] | 0.467 [0.43,0.51] | - | 0.462 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5T3 | +60 | POOLED | S_I5T3 | 0.522 [0.50,0.55] | 0.466 [0.42,0.51] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +10 | LONDON | S_base | 0.492 [0.45,0.54] | 0.465 [0.40,0.53] | - | 0.457 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +45 | LONDON | S_I5B | 0.481 [0.44,0.53] | 0.465 [0.41,0.52] | - | 0.460 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +5 | LONDON | S_I5 | 0.504 [0.46,0.54] | 0.464 [0.40,0.52] | - | 0.458 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +45 | NY | S_I5 | 0.491 [0.45,0.54] | 0.463 [0.40,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +10 | POOLED | S_base | 0.504 [0.48,0.53] | 0.463 [0.42,0.51] | - | 0.455 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_T10 | +5 | POOLED | S_T10 | 0.507 [0.48,0.53] | 0.463 [0.42,0.50] | - | 0.460 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_base | +60 | NY | S_base | 0.479 [0.43,0.53] | 0.463 [0.39,0.54] | - | 0.460 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +20 | POOLED | S_T10 | 0.515 [0.49,0.54] | 0.462 [0.42,0.50] | - | 0.458 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5B | +30 | LONDON | S_I5B | 0.486 [0.44,0.53] | 0.461 [0.40,0.52] | - | 0.446 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | pre | NY | S_I5 | 0.465 [0.42,0.51] | 0.459 [0.39,0.53] | - | 0.464 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +45 | POOLED | S_I5T3 | 0.511 [0.48,0.54] | 0.459 [0.43,0.49] | - | 0.454 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | pre | LONDON | S_I5T3 | 0.508 [0.47,0.55] | 0.459 [0.40,0.51] | - | 0.458 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | pre | POOLED | S_AVG2 | 0.491 [0.47,0.52] | 0.458 [0.42,0.50] | - | 0.451 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5T3 | +20 | POOLED | S_I5T3 | 0.511 [0.48,0.54] | 0.458 [0.42,0.49] | - | 0.455 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_T10 | +45 | POOLED | S_T10 | 0.517 [0.49,0.55] | 0.458 [0.42,0.49] | - | 0.450 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | pre | LONDON | S_AVG2 | 0.484 [0.44,0.53] | 0.457 [0.40,0.52] | - | 0.451 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +5 | LONDON | S_T10 | 0.517 [0.47,0.56] | 0.456 [0.40,0.51] | - | 0.450 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +15 | NY | S_I5B | 0.491 [0.45,0.54] | 0.456 [0.39,0.52] | - | 0.469 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +20 | LONDON | S_T10 | 0.513 [0.47,0.56] | 0.456 [0.40,0.51] | - | 0.446 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +60 | LONDON | S_I5 | 0.486 [0.44,0.54] | 0.454 [0.40,0.51] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | pre | NY | S_I5T3 | 0.471 [0.43,0.51] | 0.453 [0.40,0.51] | - | 0.464 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +15 | POOLED | S_base | 0.503 [0.48,0.53] | 0.453 [0.41,0.50] | - | 0.443 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_T10 | +10 | POOLED | S_T10 | 0.512 [0.49,0.54] | 0.453 [0.41,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_T10 | +15 | POOLED | S_T10 | 0.513 [0.49,0.54] | 0.452 [0.41,0.49] | - | 0.451 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_base | pre | LONDON | S_base | 0.477 [0.43,0.52] | 0.452 [0.39,0.52] | - | 0.448 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +30 | NY | S_T10 | 0.484 [0.44,0.53] | 0.452 [0.39,0.52] | - | 0.451 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +15 | LONDON | S_I5T3 | 0.509 [0.46,0.56] | 0.452 [0.39,0.51] | - | 0.442 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +60 | POOLED | S_T10 | 0.521 [0.49,0.55] | 0.450 [0.41,0.50] | - | 0.440 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | pre | POOLED | S_T10 | 0.505 [0.48,0.53] | 0.449 [0.41,0.49] | - | 0.443 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_I5 | +30 | NY | S_I5 | 0.481 [0.44,0.53] | 0.449 [0.39,0.50] | - | 0.456 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +60 | NY | S_I5T3 | 0.508 [0.46,0.55] | 0.449 [0.38,0.52] | - | 0.443 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +20 | LONDON | S_I5 | 0.504 [0.46,0.54] | 0.448 [0.40,0.50] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +10 | LONDON | S_T10 | 0.508 [0.46,0.56] | 0.448 [0.39,0.50] | - | 0.430 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +45 | LONDON | S_I5T3 | 0.512 [0.47,0.56] | 0.447 [0.39,0.51] | - | 0.431 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | pre | NY | S_base | 0.458 [0.41,0.50] | 0.447 [0.39,0.51] | - | 0.455 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +15 | NY | S_base | 0.495 [0.45,0.54] | 0.446 [0.38,0.53] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +20 | NY | S_AVG2 | 0.490 [0.44,0.53] | 0.445 [0.38,0.51] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +60 | NY | S_I5 | 0.471 [0.43,0.51] | 0.445 [0.38,0.51] | - | 0.428 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +45 | LONDON | S_I5 | 0.492 [0.45,0.54] | 0.444 [0.39,0.50] | - | 0.434 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +15 | LONDON | S_T10 | 0.507 [0.46,0.55] | 0.444 [0.38,0.50] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +10 | NY | S_I5 | 0.478 [0.43,0.52] | 0.444 [0.38,0.51] | - | 0.453 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +45 | POOLED | S_base | 0.482 [0.46,0.51] | 0.443 [0.40,0.49] | - | 0.441 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +30 | LONDON | S_T10 | 0.501 [0.46,0.55] | 0.442 [0.39,0.50] | - | 0.430 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +15 | LONDON | S_base | 0.494 [0.45,0.54] | 0.442 [0.38,0.50] | - | 0.425 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +45 | NY | S_I5B | 0.474 [0.43,0.52] | 0.442 [0.38,0.50] | - | 0.443 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +20 | LONDON | S_I5T3 | 0.496 [0.45,0.54] | 0.442 [0.39,0.50] | - | 0.438 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +60 | NY | S_I5B | 0.468 [0.42,0.51] | 0.440 [0.38,0.52] | - | 0.427 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +60 | NY | S_AVG2 | 0.473 [0.43,0.52] | 0.440 [0.37,0.51] | - | 0.430 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +60 | LONDON | S_AVG2 | 0.510 [0.46,0.56] | 0.439 [0.38,0.50] | - | 0.431 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +20 | NY | S_I5 | 0.472 [0.43,0.52] | 0.439 [0.38,0.50] | - | 0.443 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +30 | POOLED | S_base | 0.488 [0.46,0.51] | 0.439 [0.40,0.48] | - | 0.437 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| K9-S_base | +30 | LONDON | S_base | 0.495 [0.45,0.54] | 0.438 [0.38,0.50] | - | 0.444 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +60 | LONDON | S_I5T3 | 0.522 [0.47,0.57] | 0.437 [0.38,0.50] | - | 0.421 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +5 | NY | S_I5T3 | 0.474 [0.43,0.52] | 0.436 [0.38,0.49] | - | 0.447 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +15 | NY | S_I5 | 0.493 [0.45,0.54] | 0.435 [0.38,0.49] | - | 0.444 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +5 | NY | S_base | 0.467 [0.42,0.51] | 0.433 [0.38,0.49] | - | 0.447 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | pre | LONDON | S_T10 | 0.505 [0.46,0.55] | 0.433 [0.38,0.49] | - | 0.426 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +20 | NY | S_I5T3 | 0.494 [0.45,0.54] | 0.433 [0.37,0.49] | - | 0.441 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | pre | NY | S_T10 | 0.469 [0.42,0.51] | 0.433 [0.38,0.49] | - | 0.445 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +45 | LONDON | S_base | 0.467 [0.42,0.52] | 0.432 [0.37,0.50] | - | 0.427 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +45 | LONDON | S_AVG2 | 0.478 [0.43,0.52] | 0.432 [0.37,0.49] | - | 0.425 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5 | +5 | NY | S_I5 | 0.472 [0.43,0.52] | 0.431 [0.38,0.49] | - | 0.442 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +30 | NY | S_I5B | 0.493 [0.44,0.54] | 0.430 [0.38,0.49] | - | 0.437 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | pre | NY | S_AVG2 | 0.456 [0.41,0.50] | 0.430 [0.38,0.49] | - | 0.435 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +30 | NY | S_I5T3 | 0.476 [0.43,0.52] | 0.429 [0.37,0.49] | - | 0.430 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +60 | NY | S_T10 | 0.490 [0.45,0.54] | 0.428 [0.36,0.50] | - | 0.416 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +15 | NY | S_AVG2 | 0.493 [0.45,0.54] | 0.427 [0.36,0.49] | - | 0.437 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +45 | LONDON | S_T10 | 0.513 [0.47,0.56] | 0.425 [0.37,0.48] | - | 0.410 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +5 | NY | S_I5B | 0.459 [0.41,0.51] | 0.424 [0.37,0.48] | - | 0.436 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +10 | NY | S_base | 0.481 [0.44,0.53] | 0.424 [0.36,0.49] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +10 | NY | S_AVG2 | 0.475 [0.43,0.52] | 0.423 [0.36,0.49] | - | 0.424 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +15 | NY | S_I5T3 | 0.491 [0.44,0.54] | 0.422 [0.36,0.50] | - | 0.426 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5B | +10 | NY | S_I5B | 0.460 [0.42,0.50] | 0.422 [0.36,0.49] | - | 0.425 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +45 | NY | S_T10 | 0.495 [0.45,0.54] | 0.420 [0.36,0.49] | - | 0.413 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +20 | NY | S_T10 | 0.485 [0.44,0.53] | 0.420 [0.36,0.48] | - | 0.424 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +45 | NY | S_AVG2 | 0.479 [0.44,0.53] | 0.419 [0.36,0.48] | - | 0.417 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +60 | LONDON | S_T10 | 0.511 [0.46,0.56] | 0.415 [0.36,0.48] | - | 0.397 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +30 | NY | S_AVG2 | 0.472 [0.42,0.52] | 0.415 [0.35,0.48] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +5 | NY | S_T10 | 0.469 [0.43,0.51] | 0.413 [0.36,0.48] | - | 0.427 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_AVG2 | +5 | NY | S_AVG2 | 0.464 [0.42,0.51] | 0.413 [0.36,0.47] | - | 0.425 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +10 | NY | S_T10 | 0.474 [0.43,0.52] | 0.405 [0.34,0.47] | - | 0.413 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +10 | NY | S_I5T3 | 0.475 [0.43,0.52] | 0.400 [0.34,0.47] | - | 0.409 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +45 | NY | S_base | 0.474 [0.43,0.52] | 0.400 [0.34,0.46] | - | 0.399 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_I5T3 | +45 | NY | S_I5T3 | 0.484 [0.44,0.53] | 0.399 [0.33,0.46] | - | 0.399 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_base | +30 | NY | S_base | 0.466 [0.42,0.52] | 0.396 [0.33,0.47] | - | 0.404 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| K9-S_T10 | +15 | NY | S_T10 | 0.481 [0.44,0.53] | 0.394 [0.33,0.47] | - | 0.401 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |

One-sentence notes:
- K9-S_AVG2 0 POOLED: unlocked cond late fusion with I5
- K9-S_AVG2 0 ASIA: unlocked cond late fusion with I5
- K9-S_AVG2 0 LONDON: unlocked cond late fusion with I5
- K9-S_AVG2 0 NY: unlocked cond late fusion with I5
- K9-S_I5 0 POOLED: unlocked cond late fusion with I5
- K9-S_I5 0 ASIA: unlocked cond late fusion with I5
- K9-S_I5 0 LONDON: unlocked cond late fusion with I5
- K9-S_I5 0 NY: unlocked cond late fusion with I5
- K9-S_I5B 0 POOLED: unlocked cond late fusion with I5
- K9-S_I5B 0 ASIA: unlocked cond late fusion with I5
- K9-S_I5B 0 LONDON: unlocked cond late fusion with I5
- K9-S_I5B 0 NY: unlocked cond late fusion with I5
- K9-S_I5T3 0 POOLED: unlocked cond late fusion with I5
- K9-S_I5T3 0 ASIA: unlocked cond late fusion with I5
- K9-S_I5T3 0 LONDON: unlocked cond late fusion with I5
- K9-S_I5T3 0 NY: unlocked cond late fusion with I5
- K9-S_T10 0 POOLED: unlocked cond late fusion with I5
- K9-S_T10 0 ASIA: unlocked cond late fusion with I5
- K9-S_T10 0 LONDON: unlocked cond late fusion with I5
- K9-S_T10 0 NY: unlocked cond late fusion with I5
- K9-S_base 0 POOLED: unlocked cond late fusion with I5
- K9-S_base 0 ASIA: unlocked cond late fusion with I5
- K9-S_base 0 LONDON: unlocked cond late fusion with I5
- K9-S_base 0 NY: unlocked cond late fusion with I5
- K9-S_AVG2 10 POOLED: unlocked cond late fusion with I5
- K9-S_AVG2 10 ASIA: unlocked cond late fusion with I5
- K9-S_AVG2 10 LONDON: unlocked cond late fusion with I5
- K9-S_AVG2 10 NY: unlocked cond late fusion with I5
- K9-S_I5 10 POOLED: unlocked cond late fusion with I5
- K9-S_I5 10 ASIA: unlocked cond late fusion with I5
- K9-S_I5 10 LONDON: unlocked cond late fusion with I5
- K9-S_I5 10 NY: unlocked cond late fusion with I5
- K9-S_I5B 10 POOLED: unlocked cond late fusion with I5
- K9-S_I5B 10 ASIA: unlocked cond late fusion with I5
- K9-S_I5B 10 LONDON: unlocked cond late fusion with I5
- K9-S_I5B 10 NY: unlocked cond late fusion with I5
- K9-S_I5T3 10 POOLED: unlocked cond late fusion with I5
- K9-S_I5T3 10 ASIA: unlocked cond late fusion with I5
- K9-S_I5T3 10 LONDON: unlocked cond late fusion with I5
- K9-S_I5T3 10 NY: unlocked cond late fusion with I5
- K9-S_T10 10 POOLED: unlocked cond late fusion with I5
- K9-S_T10 10 ASIA: unlocked cond late fusion with I5
- K9-S_T10 10 LONDON: unlocked cond late fusion with I5
- K9-S_T10 10 NY: unlocked cond late fusion with I5
- K9-S_base 10 POOLED: unlocked cond late fusion with I5
- K9-S_base 10 ASIA: unlocked cond late fusion with I5
- K9-S_base 10 LONDON: unlocked cond late fusion with I5
- K9-S_base 10 NY: unlocked cond late fusion with I5
- K9-S_AVG2 15 POOLED: placebo: I5 rank among 71 single sources 0.93; I5T3 null rank 0.29
- K9-S_AVG2 15 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.35
- K9-S_AVG2 15 LONDON: unlocked cond late fusion with I5
- K9-S_AVG2 15 NY: unlocked cond late fusion with I5
- K9-S_I5 15 POOLED: placebo: I5 rank among 71 single sources 0.93; I5T3 null rank 0.29
- K9-S_I5 15 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.35
- K9-S_I5 15 LONDON: unlocked cond late fusion with I5
- K9-S_I5 15 NY: unlocked cond late fusion with I5
- K9-S_I5B 15 POOLED: placebo: I5 rank among 71 single sources 0.93; I5T3 null rank 0.29
- K9-S_I5B 15 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.35
- K9-S_I5B 15 LONDON: unlocked cond late fusion with I5
- K9-S_I5B 15 NY: unlocked cond late fusion with I5
- K9-S_I5T3 15 POOLED: placebo: I5 rank among 71 single sources 0.93; I5T3 null rank 0.29
- K9-S_I5T3 15 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.35
- K9-S_I5T3 15 LONDON: unlocked cond late fusion with I5
- K9-S_I5T3 15 NY: unlocked cond late fusion with I5
- K9-S_T10 15 POOLED: placebo: I5 rank among 71 single sources 0.93; I5T3 null rank 0.29
- K9-S_T10 15 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.35
- K9-S_T10 15 LONDON: unlocked cond late fusion with I5
- K9-S_T10 15 NY: unlocked cond late fusion with I5
- K9-S_base 15 POOLED: placebo: I5 rank among 71 single sources 0.93; I5T3 null rank 0.29
- K9-S_base 15 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.35
- K9-S_base 15 LONDON: unlocked cond late fusion with I5
- K9-S_base 15 NY: unlocked cond late fusion with I5
- K9-S_AVG2 20 POOLED: unlocked cond late fusion with I5
- K9-S_AVG2 20 ASIA: unlocked cond late fusion with I5
- K9-S_AVG2 20 LONDON: unlocked cond late fusion with I5
- K9-S_AVG2 20 NY: unlocked cond late fusion with I5
- K9-S_I5 20 POOLED: unlocked cond late fusion with I5
- K9-S_I5 20 ASIA: unlocked cond late fusion with I5
- K9-S_I5 20 LONDON: unlocked cond late fusion with I5
- K9-S_I5 20 NY: unlocked cond late fusion with I5
- K9-S_I5B 20 POOLED: unlocked cond late fusion with I5
- K9-S_I5B 20 ASIA: unlocked cond late fusion with I5
- K9-S_I5B 20 LONDON: unlocked cond late fusion with I5
- K9-S_I5B 20 NY: unlocked cond late fusion with I5
- K9-S_I5T3 20 POOLED: unlocked cond late fusion with I5
- K9-S_I5T3 20 ASIA: unlocked cond late fusion with I5
- K9-S_I5T3 20 LONDON: unlocked cond late fusion with I5
- K9-S_I5T3 20 NY: unlocked cond late fusion with I5
- K9-S_T10 20 POOLED: unlocked cond late fusion with I5
- K9-S_T10 20 ASIA: unlocked cond late fusion with I5
- K9-S_T10 20 LONDON: unlocked cond late fusion with I5
- K9-S_T10 20 NY: unlocked cond late fusion with I5
- K9-S_base 20 POOLED: unlocked cond late fusion with I5
- K9-S_base 20 ASIA: unlocked cond late fusion with I5
- K9-S_base 20 LONDON: unlocked cond late fusion with I5
- K9-S_base 20 NY: unlocked cond late fusion with I5
- K9-S_AVG2 30 POOLED: placebo: I5 rank among 71 single sources 0.99; I5T3 null rank 0.74
- K9-S_AVG2 30 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.70
- K9-S_AVG2 30 LONDON: unlocked cond late fusion with I5
- K9-S_AVG2 30 NY: unlocked cond late fusion with I5
- K9-S_I5 30 POOLED: placebo: I5 rank among 71 single sources 0.99; I5T3 null rank 0.74
- K9-S_I5 30 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.70
- K9-S_I5 30 LONDON: unlocked cond late fusion with I5
- K9-S_I5 30 NY: unlocked cond late fusion with I5
- K9-S_I5B 30 POOLED: placebo: I5 rank among 71 single sources 0.99; I5T3 null rank 0.74
- K9-S_I5B 30 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.70
- K9-S_I5B 30 LONDON: unlocked cond late fusion with I5
- K9-S_I5B 30 NY: unlocked cond late fusion with I5
- K9-S_I5T3 30 POOLED: placebo: I5 rank among 71 single sources 0.99; I5T3 null rank 0.74
- K9-S_I5T3 30 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.70
- K9-S_I5T3 30 LONDON: unlocked cond late fusion with I5
- K9-S_I5T3 30 NY: unlocked cond late fusion with I5
- K9-S_T10 30 POOLED: placebo: I5 rank among 71 single sources 0.99; I5T3 null rank 0.74
- K9-S_T10 30 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.70
- K9-S_T10 30 LONDON: unlocked cond late fusion with I5
- K9-S_T10 30 NY: unlocked cond late fusion with I5
- K9-S_base 30 POOLED: placebo: I5 rank among 71 single sources 0.99; I5T3 null rank 0.74
- K9-S_base 30 ASIA: placebo: I5 rank among 71 single sources 1.00; I5T3 null rank 0.70
- K9-S_base 30 LONDON: unlocked cond late fusion with I5
- K9-S_base 30 NY: unlocked cond late fusion with I5
- K9-S_AVG2 45 POOLED: unlocked cond late fusion with I5
- K9-S_AVG2 45 ASIA: unlocked cond late fusion with I5
- K9-S_AVG2 45 LONDON: unlocked cond late fusion with I5
- K9-S_AVG2 45 NY: unlocked cond late fusion with I5
- K9-S_I5 45 POOLED: unlocked cond late fusion with I5
- K9-S_I5 45 ASIA: unlocked cond late fusion with I5
- K9-S_I5 45 LONDON: unlocked cond late fusion with I5
- K9-S_I5 45 NY: unlocked cond late fusion with I5
- K9-S_I5B 45 POOLED: unlocked cond late fusion with I5
- K9-S_I5B 45 ASIA: unlocked cond late fusion with I5
- K9-S_I5B 45 LONDON: unlocked cond late fusion with I5
- K9-S_I5B 45 NY: unlocked cond late fusion with I5
- K9-S_I5T3 45 POOLED: unlocked cond late fusion with I5
- K9-S_I5T3 45 ASIA: unlocked cond late fusion with I5
- K9-S_I5T3 45 LONDON: unlocked cond late fusion with I5
- K9-S_I5T3 45 NY: unlocked cond late fusion with I5
- K9-S_T10 45 POOLED: unlocked cond late fusion with I5
- K9-S_T10 45 ASIA: unlocked cond late fusion with I5
- K9-S_T10 45 LONDON: unlocked cond late fusion with I5
- K9-S_T10 45 NY: unlocked cond late fusion with I5
- K9-S_base 45 POOLED: unlocked cond late fusion with I5
- K9-S_base 45 ASIA: unlocked cond late fusion with I5
- K9-S_base 45 LONDON: unlocked cond late fusion with I5
- K9-S_base 45 NY: unlocked cond late fusion with I5
- K9-S_AVG2 5 POOLED: unlocked cond late fusion with I5
- K9-S_AVG2 5 ASIA: unlocked cond late fusion with I5
- K9-S_AVG2 5 LONDON: unlocked cond late fusion with I5
- K9-S_AVG2 5 NY: unlocked cond late fusion with I5
- K9-S_I5 5 POOLED: unlocked cond late fusion with I5
- K9-S_I5 5 ASIA: unlocked cond late fusion with I5
- K9-S_I5 5 LONDON: unlocked cond late fusion with I5
- K9-S_I5 5 NY: unlocked cond late fusion with I5
- K9-S_I5B 5 POOLED: unlocked cond late fusion with I5
- K9-S_I5B 5 ASIA: unlocked cond late fusion with I5
- K9-S_I5B 5 LONDON: unlocked cond late fusion with I5
- K9-S_I5B 5 NY: unlocked cond late fusion with I5
- K9-S_I5T3 5 POOLED: unlocked cond late fusion with I5
- K9-S_I5T3 5 ASIA: unlocked cond late fusion with I5
- K9-S_I5T3 5 LONDON: unlocked cond late fusion with I5
- K9-S_I5T3 5 NY: unlocked cond late fusion with I5
- K9-S_T10 5 POOLED: unlocked cond late fusion with I5
- K9-S_T10 5 ASIA: unlocked cond late fusion with I5
- K9-S_T10 5 LONDON: unlocked cond late fusion with I5
- K9-S_T10 5 NY: unlocked cond late fusion with I5
- K9-S_base 5 POOLED: unlocked cond late fusion with I5
- K9-S_base 5 ASIA: unlocked cond late fusion with I5
- K9-S_base 5 LONDON: unlocked cond late fusion with I5
- K9-S_base 5 NY: unlocked cond late fusion with I5
- K9-S_AVG2 60 POOLED: unlocked cond late fusion with I5
- K9-S_AVG2 60 ASIA: unlocked cond late fusion with I5
- K9-S_AVG2 60 LONDON: unlocked cond late fusion with I5
- K9-S_AVG2 60 NY: unlocked cond late fusion with I5
- K9-S_I5 60 POOLED: unlocked cond late fusion with I5
- K9-S_I5 60 ASIA: unlocked cond late fusion with I5
- K9-S_I5 60 LONDON: unlocked cond late fusion with I5
- K9-S_I5 60 NY: unlocked cond late fusion with I5
- K9-S_I5B 60 POOLED: unlocked cond late fusion with I5
- K9-S_I5B 60 ASIA: unlocked cond late fusion with I5
- K9-S_I5B 60 LONDON: unlocked cond late fusion with I5
- K9-S_I5B 60 NY: unlocked cond late fusion with I5
- K9-S_I5T3 60 POOLED: unlocked cond late fusion with I5
- K9-S_I5T3 60 ASIA: unlocked cond late fusion with I5
- K9-S_I5T3 60 LONDON: unlocked cond late fusion with I5
- K9-S_I5T3 60 NY: unlocked cond late fusion with I5
- K9-S_T10 60 POOLED: unlocked cond late fusion with I5
- K9-S_T10 60 ASIA: unlocked cond late fusion with I5
- K9-S_T10 60 LONDON: unlocked cond late fusion with I5
- K9-S_T10 60 NY: unlocked cond late fusion with I5
- K9-S_base 60 POOLED: unlocked cond late fusion with I5
- K9-S_base 60 ASIA: unlocked cond late fusion with I5
- K9-S_base 60 LONDON: unlocked cond late fusion with I5
- K9-S_base 60 NY: unlocked cond late fusion with I5
