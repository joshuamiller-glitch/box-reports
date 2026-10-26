# PRED ROUND 55 - block A round 8 - A-unlocked

Best HOLDOUT F-R AUC: +15 POOLED 0.534 [0.49,0.57] | ASIA 0.515 [0.46,0.57] | LONDON 0.559 [0.51,0.62] | NY 0.560 [0.49,0.62]
Best HOLDOUT F-R AUC: +30 POOLED 0.533 [0.50,0.57] | ASIA 0.516 [0.46,0.57] | LONDON 0.547 [0.50,0.60] | NY 0.559 [0.49,0.62]
Best G HOLDOUT AUC: 0.573 [0.54,0.60]
Gap to FOUND: 0.107 AUC, 5 of 5 economic conditions short.
not found - short by 0.107 AUC and 5 of 5 economic conditions

prereg 9b91d885ec013e19bf44b2b6ec13a30fc1f17a3a314031b323a84c4cddf537f9 ; trials added 600 ; truncation audit {'decisions': 90000, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/A/dense_scores_u.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A4-unlocked | pre | NY | lamS | 0.551 [-,-] | 0.574 [0.50,0.63] | - | 0.577 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY/ST | M3_y | 0.544 [-,-] | 0.573 [0.54,0.60] | - | - | - | - | - | - | - | - | stack | short by 0.107 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY | RAW_a2_rngq90 | 0.566 [-,-] | 0.571 [0.55,0.59] | - | - | - | - | - | - | - | - |  | short by 0.109 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY/HM | RAW_a2_rngq90 | 0.564 [-,-] | 0.571 [0.54,0.60] | - | - | - | - | - | - | - | - |  | short by 0.109 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY/ST | RAW_a2_rngq90 | 0.567 [-,-] | 0.568 [0.54,0.59] | - | - | - | - | - | - | - | - |  | short by 0.112 AUC, 5 of 5 econ |
| A4-unlocked | pre | NY | lamE | 0.557 [-,-] | 0.567 [0.50,0.63] | - | 0.566 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY/ST | RAW_a3_mae60 | 0.564 [-,-] | 0.566 [0.54,0.58] | - | - | - | - | - | - | - | - |  | short by 0.114 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY/HM | M5_y | 0.539 [-,-] | 0.565 [0.54,0.60] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | NY | RAW_a3_mae60 | 0.563 [-,-] | 0.565 [0.54,0.59] | - | - | - | - | - | - | - | - |  | short by 0.115 AUC, 5 of 5 econ |
| A4-unlocked | +5 | LONDON | pE | 0.541 [-,-] | 0.563 [0.51,0.63] | - | 0.554 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +5 | NY | lamE | 0.543 [-,-] | 0.563 [0.50,0.62] | - | 0.555 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY | M3_y | 0.549 [-,-] | 0.563 [0.54,0.59] | - | - | - | - | - | - | - | - | stack | short by 0.117 AUC, 5 of 5 econ |
| A4-unlocked | +20 | NY | lamS | 0.537 [-,-] | 0.562 [0.49,0.62] | - | 0.560 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY | M5_y | 0.544 [-,-] | 0.562 [0.54,0.58] | - | - | - | - | - | - | - | - |  | short by 0.118 AUC, 5 of 5 econ |
| A4-unlocked | +20 | NY | lamE | 0.542 [-,-] | 0.561 [0.49,0.62] | - | 0.556 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +15 | NY | lamE | 0.541 [-,-] | 0.560 [0.49,0.62] | - | 0.545 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY/HM | RAW_a3_mae60 | 0.562 [-,-] | 0.560 [0.53,0.59] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A4-unlocked | +5 | NY | pE | 0.527 [-,-] | 0.559 [0.49,0.62] | - | 0.552 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +30 | NY | lamE | 0.534 [-,-] | 0.559 [0.49,0.62] | - | 0.548 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY/ST | M5_y | 0.547 [-,-] | 0.559 [0.53,0.58] | - | - | - | - | - | - | - | - |  | short by 0.121 AUC, 5 of 5 econ |
| A4-unlocked | +15 | NY | lamS | 0.538 [-,-] | 0.559 [0.49,0.62] | - | 0.550 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +15 | LONDON | pE | 0.538 [-,-] | 0.559 [0.51,0.62] | - | 0.544 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +15 | LONDON | C4 | 0.525 [-,-] | 0.559 [0.50,0.63] | - | 0.549 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | pre | NY | pE | 0.541 [-,-] | 0.557 [0.50,0.62] | - | 0.558 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +5 | NY | lamS | 0.535 [-,-] | 0.556 [0.50,0.61] | - | 0.546 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +10 | NY | lamE | 0.544 [-,-] | 0.556 [0.49,0.61] | - | 0.552 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +10 | NY | lamS | 0.537 [-,-] | 0.555 [0.49,0.62] | - | 0.550 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +30 | NY | lamS | 0.521 [-,-] | 0.554 [0.49,0.61] | - | 0.544 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +30 | NY | pE | 0.522 [-,-] | 0.554 [0.48,0.62] | - | 0.541 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | pre | LONDON | lamS | 0.531 [-,-] | 0.551 [0.49,0.62] | - | 0.536 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +20 | LONDON | lamE | 0.537 [-,-] | 0.551 [0.50,0.61] | - | 0.529 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +5 | LONDON | lamE | 0.534 [-,-] | 0.551 [0.50,0.61] | - | 0.529 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +20 | LONDON | pE | 0.541 [-,-] | 0.551 [0.50,0.61] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +5 | LONDON | lamS | 0.529 [-,-] | 0.547 [0.49,0.61] | - | 0.527 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +5 | POOLED | pE | 0.520 [-,-] | 0.547 [0.51,0.58] | - | 0.539 | - | - | - | - | - | - |  | promising: short by 0.133 AUC, 5 of 5 econ |
| A4-unlocked | pre | LONDON | lamE | 0.533 [-,-] | 0.547 [0.49,0.61] | - | 0.519 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY/HM | M3_y | 0.557 [-,-] | 0.547 [0.51,0.58] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| A4-unlocked | +30 | LONDON | pE | 0.538 [-,-] | 0.547 [0.50,0.60] | - | 0.523 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +10 | NY | pE | 0.525 [-,-] | 0.546 [0.48,0.61] | - | 0.543 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +10 | LONDON | lamE | 0.528 [-,-] | 0.546 [0.49,0.61] | - | 0.522 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY/ST | M3_y | 0.513 [-,-] | 0.545 [0.52,0.57] | - | - | - | - | - | - | - | - | stack | promising: short by 0.135 AUC, 5 of 5 econ |
| A4-unlocked | +15 | LONDON | lamE | 0.534 [-,-] | 0.545 [0.49,0.61] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +10 | LONDON | lamS | 0.527 [-,-] | 0.544 [0.49,0.61] | - | 0.523 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY/ST | M0_y | 0.539 [-,-] | 0.544 [0.52,0.57] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +5 | ASIA | C4 | 0.536 [-,-] | 0.542 [0.49,0.60] | - | 0.539 | - | - | - | - | - | - |  | short by 0.118 AUC, 5 of 5 econ |
| A4-unlocked | +10 | ASIA | C4 | 0.508 [-,-] | 0.541 [0.48,0.60] | - | 0.550 | - | - | - | - | - | - |  | short by 0.119 AUC, 5 of 5 econ |
| A4-unlocked | +10 | LONDON | pE | 0.528 [-,-] | 0.541 [0.49,0.60] | - | 0.517 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +10 | POOLED | lamS | 0.512 [-,-] | 0.541 [0.50,0.58] | - | 0.530 | - | - | - | - | - | - |  | short by 0.139 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY | M0_y | 0.545 [-,-] | 0.541 [0.52,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +30 | LONDON | lamE | 0.539 [-,-] | 0.540 [0.49,0.60] | - | 0.512 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | pre | LONDON | pE | 0.530 [-,-] | 0.540 [0.48,0.60] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +15 | LONDON | lamS | 0.527 [-,-] | 0.539 [0.48,0.60] | - | 0.514 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +20 | LONDON | lamS | 0.528 [-,-] | 0.539 [0.49,0.60] | - | 0.515 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | pre | POOLED | pE | 0.522 [-,-] | 0.539 [0.51,0.57] | - | 0.526 | - | - | - | - | - | - |  | promising: short by 0.141 AUC, 5 of 5 econ |
| A4-unlocked | pre | POOLED | lamS | 0.514 [-,-] | 0.539 [0.50,0.57] | - | 0.531 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| A4-unlocked | +20 | ASIA | C4 | 0.528 [-,-] | 0.539 [0.48,0.60] | - | 0.531 | - | - | - | - | - | - |  | short by 0.121 AUC, 5 of 5 econ |
| A4-unlocked | +15 | NY | pE | 0.517 [-,-] | 0.538 [0.47,0.60] | - | 0.527 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +20 | POOLED | lamS | 0.516 [-,-] | 0.537 [0.50,0.57] | - | 0.529 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| A4-unlocked | +10 | POOLED | lamE | 0.515 [-,-] | 0.537 [0.50,0.57] | - | 0.532 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| A4-unlocked | pre | POOLED | lamE | 0.518 [-,-] | 0.536 [0.50,0.57] | - | 0.529 | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| A4-unlocked | +20 | POOLED | lamE | 0.520 [-,-] | 0.536 [0.50,0.57] | - | 0.530 | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| A4-unlocked | +5 | LONDON | C4 | 0.530 [-,-] | 0.535 [0.46,0.61] | - | 0.540 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY/ST | RAW_a2_rngq90 | 0.528 [-,-] | 0.534 [0.51,0.56] | - | - | - | - | - | - | - | - |  | promising: short by 0.146 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY/HM | M0_y | 0.553 [-,-] | 0.534 [0.50,0.57] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +15 | POOLED | lamS | 0.514 [-,-] | 0.534 [0.49,0.57] | - | 0.523 | - | - | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY/HM | M5_y | 0.500 [-,-] | 0.534 [0.50,0.57] | - | - | - | - | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA/HM | M5_y | 0.511 [-,-] | 0.533 [0.50,0.57] | - | - | - | - | - | - | - | - |  | short by 0.147 AUC, 5 of 5 econ |
| A4-unlocked | +30 | POOLED | pE | 0.520 [-,-] | 0.533 [0.50,0.57] | - | 0.515 | - | - | - | - | - | - |  | promising: short by 0.147 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY | M5_y | 0.510 [-,-] | 0.533 [0.51,0.56] | - | - | - | - | - | - | - | - |  | promising: short by 0.147 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA/HM | M5_y | 0.513 [-,-] | 0.533 [0.50,0.57] | - | - | - | - | - | - | - | - |  | short by 0.147 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY/ST | M5_y | 0.517 [-,-] | 0.533 [0.50,0.56] | - | - | - | - | - | - | - | - |  | promising: short by 0.147 AUC, 5 of 5 econ |
| A4-unlocked | +30 | POOLED | lamS | 0.517 [-,-] | 0.533 [0.50,0.57] | - | 0.519 | - | - | - | - | - | - |  | promising: short by 0.147 AUC, 5 of 5 econ |
| A4-unlocked | +20 | NY | pE | 0.511 [-,-] | 0.533 [0.46,0.60] | - | 0.529 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +5 | POOLED | lamS | 0.509 [-,-] | 0.533 [0.49,0.57] | - | 0.522 | - | - | - | - | - | - |  | short by 0.147 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY/ST | RAW_a3_mae60 | 0.526 [-,-] | 0.533 [0.51,0.55] | - | - | - | - | - | - | - | - |  | promising: short by 0.147 AUC, 5 of 5 econ |
| A4-unlocked | +30 | POOLED | lamE | 0.522 [-,-] | 0.533 [0.50,0.56] | - | 0.519 | - | - | - | - | - | - |  | promising: short by 0.147 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY | RAW_a2_rngq90 | 0.522 [-,-] | 0.533 [0.51,0.55] | - | - | - | - | - | - | - | - |  | promising: short by 0.147 AUC, 5 of 5 econ |
| A4-unlocked | +5 | POOLED | lamE | 0.512 [-,-] | 0.532 [0.49,0.57] | - | 0.523 | - | - | - | - | - | - |  | short by 0.148 AUC, 5 of 5 econ |
| A4-unlocked | +15 | POOLED | pE | 0.519 [-,-] | 0.532 [0.50,0.56] | - | 0.519 | - | - | - | - | - | - |  | promising: short by 0.148 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED/ST | RAW_a2_rngq90 | 0.530 [-,-] | 0.532 [0.51,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | pre | ASIA | C4 | 0.527 [-,-] | 0.531 [0.46,0.60] | - | 0.528 | - | - | - | - | - | - |  | short by 0.129 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED/HM | M5_y | 0.516 [-,-] | 0.530 [0.51,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | NY | M3_y | 0.515 [-,-] | 0.530 [0.51,0.55] | - | - | - | - | - | - | - | - | stack | promising: short by 0.150 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED/ST | M3_y | 0.523 [-,-] | 0.530 [0.51,0.55] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED/ST | RAW_a3_mae60 | 0.531 [-,-] | 0.530 [0.51,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +15 | POOLED | lamE | 0.517 [-,-] | 0.530 [0.49,0.57] | - | 0.522 | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| A4-unlocked | +10 | POOLED | pE | 0.513 [-,-] | 0.530 [0.49,0.56] | - | 0.519 | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED | RAW_a2_rngq90 | 0.524 [-,-] | 0.529 [0.51,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED | M5_y | 0.522 [-,-] | 0.529 [0.52,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +15 | POOLED | C4 | 0.525 [-,-] | 0.529 [0.49,0.57] | - | 0.523 | - | - | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| A4-unlocked | +5 | ASIA | pE | 0.487 [-,-] | 0.528 [0.47,0.59] | - | 0.535 | - | - | - | - | - | - |  | short by 0.132 AUC, 5 of 5 econ |
| A4-unlocked | +30 | LONDON | lamS | 0.534 [-,-] | 0.528 [0.48,0.58] | - | 0.507 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | +20 | POOLED | pE | 0.515 [-,-] | 0.528 [0.50,0.56] | - | 0.515 | - | - | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED | RAW_a3_mae60 | 0.527 [-,-] | 0.528 [0.51,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +30 | NY | C4 | 0.497 [-,-] | 0.528 [0.47,0.60] | - | 0.537 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | POOLED/ST | M5_y | 0.527 [-,-] | 0.528 [0.51,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +10 | POOLED | C4 | 0.526 [-,-] | 0.527 [0.49,0.57] | - | 0.524 | - | - | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| A4-unlocked | pre | LONDON | C4 | 0.525 [-,-] | 0.527 [0.46,0.59] | - | 0.515 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A4-unlocked | pre | NY | C4 | 0.512 [-,-] | 0.526 [0.48,0.58] | - | 0.534 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY | RAW_a3_mae60 | 0.519 [-,-] | 0.526 [0.50,0.55] | - | - | - | - | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| A4-unlocked | pre | POOLED | C4 | 0.522 [-,-] | 0.526 [0.49,0.56] | - | 0.520 | - | - | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| A4-unlocked | +10 | LONDON | C4 | 0.541 [-,-] | 0.526 [0.47,0.59] | - | 0.514 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY/HM | RAW_a2_rngq90 | 0.512 [-,-] | 0.525 [0.49,0.56] | - | - | - | - | - | - | - | - |  | short by 0.155 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED | M3_y | 0.523 [-,-] | 0.524 [0.51,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED/HM | RAW_a3_mae60 | 0.522 [-,-] | 0.523 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +20 | POOLED | C4 | 0.518 [-,-] | 0.523 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| A-G-unlocked | sig | NY/ST | M0_y | 0.511 [-,-] | 0.523 [0.50,0.55] | - | - | - | - | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA/HM | M3_y | 0.520 [-,-] | 0.523 [0.49,0.56] | - | - | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA/HM | M3_y | 0.520 [-,-] | 0.522 [0.49,0.56] | - | - | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| A4-unlocked | +5 | POOLED | C4 | 0.512 [-,-] | 0.522 [0.49,0.56] | - | 0.516 | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED/HM | RAW_a2_rngq90 | 0.514 [-,-] | 0.522 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED/ST | RAW_a2_rngq90 | 0.519 [-,-] | 0.522 [0.50,0.54] | - | - | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| A4-unlocked | +20 | LONDON | C4 | 0.511 [-,-] | 0.521 [0.45,0.58] | - | 0.518 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | ASIA/ST | RAW_a2_rngq90 | 0.521 [-,-] | 0.521 [0.48,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/ST | RAW_a2_rngq90 | 0.519 [-,-] | 0.520 [0.48,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED/HM | M5_y | 0.502 [-,-] | 0.520 [0.50,0.54] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA | M5_y | 0.510 [-,-] | 0.519 [0.49,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED | RAW_a2_rngq90 | 0.512 [-,-] | 0.519 [0.50,0.54] | - | - | - | - | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA | M5_y | 0.510 [-,-] | 0.519 [0.49,0.55] | - | - | - | - | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED/ST | RAW_a3_mae60 | 0.518 [-,-] | 0.519 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED | M5_y | 0.509 [-,-] | 0.519 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| A4-unlocked | +15 | NY | C4 | 0.526 [-,-] | 0.518 [0.46,0.58] | - | 0.520 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | POOLED/ST | M5_y | 0.514 [-,-] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED/ST | M0_y | 0.515 [-,-] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED | M0_y | 0.522 [-,-] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | NY | M0_y | 0.513 [-,-] | 0.517 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED/HM | M3_y | 0.523 [-,-] | 0.516 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED | RAW_a3_mae60 | 0.514 [-,-] | 0.516 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED/ST | M3_y | 0.506 [-,-] | 0.516 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| A4-unlocked | +30 | ASIA | lamS | 0.483 [-,-] | 0.516 [0.46,0.57] | - | 0.509 | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA | RAW_a2_rngq90 | 0.507 [-,-] | 0.516 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED/HM | M0_y | 0.530 [-,-] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +30 | POOLED | C4 | 0.507 [-,-] | 0.515 [0.48,0.56] | - | 0.505 | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| A4-unlocked | +15 | ASIA | C4 | 0.528 [-,-] | 0.515 [0.46,0.57] | - | 0.513 | - | - | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA | RAW_a2_rngq90 | 0.504 [-,-] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| A4-unlocked | +10 | NY | C4 | 0.530 [-,-] | 0.515 [0.45,0.57] | - | 0.518 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | NY/HM | RAW_a3_mae60 | 0.510 [-,-] | 0.514 [0.47,0.55] | - | - | - | - | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| A4-unlocked | +30 | LONDON | C4 | 0.495 [-,-] | 0.513 [0.44,0.59] | - | 0.501 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | LONDON/ST | RAW_a3_mae60 | 0.514 [-,-] | 0.513 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| A-G-unlocked | sig | LONDON/ST | RAW_a3_mae60 | 0.515 [-,-] | 0.513 [0.48,0.55] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A-G-unlocked | sig | LONDON/ST | RAW_a2_rngq90 | 0.513 [-,-] | 0.513 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| A-G-unlocked | sig | LONDON/ST | RAW_a2_rngq90 | 0.514 [-,-] | 0.512 [0.48,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A4-unlocked | +30 | ASIA | pE | 0.487 [-,-] | 0.512 [0.46,0.57] | - | 0.499 | - | - | - | - | - | - |  | short by 0.148 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED/HM | RAW_a2_rngq90 | 0.502 [-,-] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A-G-unlocked | sig | POOLED/HM | RAW_a3_mae60 | 0.507 [-,-] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A4-unlocked | +20 | NY | C4 | 0.512 [-,-] | 0.510 [0.45,0.57] | - | 0.515 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | POOLED | M3_y | 0.505 [-,-] | 0.508 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| A4-unlocked | +10 | ASIA | lamS | 0.464 [-,-] | 0.507 [0.45,0.56] | - | 0.504 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | NY/HM | M3_y | 0.517 [-,-] | 0.507 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| A4-unlocked | +20 | ASIA | lamS | 0.476 [-,-] | 0.506 [0.45,0.56] | - | 0.507 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | NY/HM | M0_y | 0.517 [-,-] | 0.506 [0.47,0.54] | - | - | - | - | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| A-G-unlocked | sig | LONDON | RAW_a3_mae60 | 0.508 [-,-] | 0.506 [0.47,0.54] | - | - | - | - | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| A4-unlocked | +10 | ASIA | pE | 0.478 [-,-] | 0.506 [0.45,0.56] | - | 0.513 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON | RAW_a3_mae60 | 0.507 [-,-] | 0.506 [0.47,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A-G-unlocked | sig | ASIA/ST | M5_y | 0.508 [-,-] | 0.505 [0.47,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/ST | M5_y | 0.507 [-,-] | 0.505 [0.47,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/ST | M5_y | 0.513 [-,-] | 0.505 [0.48,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A-G-unlocked | sig | ASIA/ST | RAW_a3_mae60 | 0.512 [-,-] | 0.505 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/HM | RAW_a2_rngq90 | 0.489 [-,-] | 0.504 [0.46,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +30 | ASIA | lamE | 0.485 [-,-] | 0.504 [0.45,0.56] | - | 0.494 | - | - | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA/ST | RAW_a3_mae60 | 0.510 [-,-] | 0.504 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED/ST | M0_y | 0.499 [-,-] | 0.504 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/ST | M5_y | 0.512 [-,-] | 0.503 [0.48,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A-G-unlocked | sig | ASIA/HM | RAW_a2_rngq90 | 0.485 [-,-] | 0.503 [0.46,0.55] | - | - | - | - | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| A-G-unlocked | sig | LONDON | RAW_a2_rngq90 | 0.501 [-,-] | 0.502 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED | M0_y | 0.503 [-,-] | 0.502 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON | RAW_a2_rngq90 | 0.502 [-,-] | 0.502 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +10 | ASIA | lamE | 0.464 [-,-] | 0.502 [0.45,0.56] | - | 0.505 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +30 | ASIA | C4 | 0.530 [-,-] | 0.502 [0.43,0.56] | - | 0.487 | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA | RAW_a3_mae60 | 0.505 [-,-] | 0.501 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA | RAW_a3_mae60 | 0.502 [-,-] | 0.500 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/HM | M0_y | 0.500 [-,-] | 0.500 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/HM | M0_y | 0.498 [-,-] | 0.500 [0.46,0.54] | - | - | - | - | - | - | - | - |  | short by 0.180 AUC, 5 of 5 econ |
| A4-unlocked | pre | ASIA | pE | 0.476 [-,-] | 0.500 [0.45,0.55] | - | 0.507 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | POOLED/HM | M0_y | 0.509 [-,-] | 0.500 [0.47,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A-G-unlocked | sig | ASIA | M3_y | 0.508 [-,-] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA | M3_y | 0.507 [-,-] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| A4-unlocked | +15 | ASIA | lamS | 0.474 [-,-] | 0.498 [0.45,0.55] | - | 0.498 | - | - | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| A4-unlocked | +5 | NY | C4 | 0.470 [-,-] | 0.498 [0.44,0.55] | - | 0.505 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-G-unlocked | sig | POOLED/HM | M3_y | 0.503 [-,-] | 0.498 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/ST | M3_y | 0.502 [-,-] | 0.497 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| A-G-unlocked | sig | LONDON/HM | RAW_a3_mae60 | 0.498 [-,-] | 0.496 [0.46,0.53] | - | - | - | - | - | - | - | - |  | short by 0.184 AUC, 5 of 5 econ |
| A-G-unlocked | sig | LONDON/HM | M0_y | 0.511 [-,-] | 0.496 [0.45,0.54] | - | - | - | - | - | - | - | - |  | short by 0.184 AUC, 5 of 5 econ |
| A4-unlocked | +5 | ASIA | lamS | 0.468 [-,-] | 0.496 [0.45,0.55] | - | 0.496 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON | M5_y | 0.503 [-,-] | 0.496 [0.47,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A4-unlocked | +20 | ASIA | pE | 0.481 [-,-] | 0.496 [0.44,0.55] | - | 0.494 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/HM | RAW_a3_mae60 | 0.497 [-,-] | 0.496 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +20 | ASIA | lamE | 0.475 [-,-] | 0.495 [0.44,0.55] | - | 0.496 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON | M5_y | 0.503 [-,-] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A-G-unlocked | sig | LONDON/ST | M3_y | 0.502 [-,-] | 0.494 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| A4-unlocked | pre | ASIA | lamE | 0.469 [-,-] | 0.494 [0.44,0.54] | - | 0.499 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON | M0_y | 0.499 [-,-] | 0.494 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +15 | ASIA | pE | 0.489 [-,-] | 0.493 [0.44,0.55] | - | 0.494 | - | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA | M0_y | 0.491 [-,-] | 0.493 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/HM | RAW_a3_mae60 | 0.495 [-,-] | 0.493 [0.45,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/HM | M0_y | 0.509 [-,-] | 0.493 [0.45,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +15 | ASIA | lamE | 0.476 [-,-] | 0.493 [0.44,0.55] | - | 0.495 | - | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| A-G-unlocked | sig | ASIA | M0_y | 0.489 [-,-] | 0.493 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/ST | M0_y | 0.490 [-,-] | 0.492 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/HM | RAW_a3_mae60 | 0.491 [-,-] | 0.492 [0.45,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A-G-unlocked | sig | LONDON | M0_y | 0.497 [-,-] | 0.490 [0.45,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/HM | RAW_a2_rngq90 | 0.485 [-,-] | 0.489 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/HM | RAW_a2_rngq90 | 0.485 [-,-] | 0.489 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | +5 | ASIA | lamE | 0.465 [-,-] | 0.488 [0.44,0.54] | - | 0.488 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/ST | M0_y | 0.488 [-,-] | 0.488 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/ST | M0_y | 0.482 [-,-] | 0.487 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A4-unlocked | pre | ASIA | lamS | 0.465 [-,-] | 0.486 [0.43,0.53] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/ST | M0_y | 0.481 [-,-] | 0.486 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/HM | M5_y | 0.490 [-,-] | 0.484 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/HM | M5_y | 0.491 [-,-] | 0.484 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/ST | M3_y | 0.498 [-,-] | 0.482 [0.44,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON | M3_y | 0.485 [-,-] | 0.481 [0.46,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| A-G-unlocked | sig | ASIA/ST | M3_y | 0.496 [-,-] | 0.481 [0.44,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON | M3_y | 0.486 [-,-] | 0.479 [0.45,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/HM | M3_y | 0.465 [-,-] | 0.461 [0.42,0.50] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| A-G-unlocked | sig | LONDON/HM | M3_y | 0.464 [-,-] | 0.461 [0.42,0.50] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 ASIA: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 LONDON: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 NY: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A-G-unlocked -1 POOLED: chance-level on unlocked label
- A4-unlocked 0 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 0 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 5 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 10 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 15 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 20 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 NY: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 POOLED: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 ASIA: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 LONDON: conditional (S_h) AUC on unlocked label; sign fixed
- A4-unlocked 30 NY: conditional (S_h) AUC on unlocked label; sign fixed
