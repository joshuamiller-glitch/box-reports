# PRED ROUND 98 - block A round 7 - R7-unlocked-session

Best HOLDOUT F-R AUC: +15 POOLED 0.551 [-,-] | ASIA 0.576 [-,-] | LONDON 0.562 [-,-] | NY 0.560 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.583 [-,-] | ASIA 0.600 [-,-] | LONDON 0.506 [-,-] | NY 0.530 [-,-]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.058 AUC, 5 of 5 economic conditions short.
not found - short by 0.058 AUC and 5 of 5 economic conditions

prereg 3dae94d45189d693cd3f0928e9f9d8c83a77bdb6903fec0e23951378aa6c0833 ; trials added 3000 ; truncation audit {'decisions': 74810, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/A/r7_sess_u.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R7-pool-share | +10 | ASIA | pool_share | 0.570 [-,-] | 0.602 [-,-] | - | 0.601 | - | - | - | - | - | - | stack | short by 0.058 AUC, 5 of 5 econ |
| R7-pool-first | +30 | ASIA | pool_first | 0.561 [-,-] | 0.600 [-,-] | - | 0.597 | - | - | - | - | - | - | stack | short by 0.060 AUC, 5 of 5 econ |
| R7-pool-frc | pre | LONDON | pool_frc | 0.565 [-,-] | 0.596 [-,-] | - | 0.600 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-share | +20 | ASIA | pool_share | 0.586 [-,-] | 0.588 [-,-] | - | 0.588 | - | - | - | - | - | - | stack | short by 0.072 AUC, 5 of 5 econ |
| R7-pool-rate | +20 | ASIA | pool_rate | 0.567 [-,-] | 0.586 [-,-] | - | 0.579 | - | - | - | - | - | - | stack | short by 0.074 AUC, 5 of 5 econ |
| R7-pool-rate | +30 | ASIA | pool_rate | 0.585 [-,-] | 0.584 [-,-] | - | 0.586 | - | - | - | - | - | - | stack | short by 0.076 AUC, 5 of 5 econ |
| R7-asia-share | +30 | ASIA | asia_share | 0.537 [-,-] | 0.583 [-,-] | - | 0.576 | - | - | - | - | - | - |  | short by 0.077 AUC, 5 of 5 econ |
| R7-asia-share | +30 | POOLED | asia_share | 0.537 [-,-] | 0.583 [-,-] | - | 0.576 | - | - | - | - | - | - |  | short by 0.097 AUC, 5 of 5 econ |
| R7-pool-dm | +15 | ASIA | pool_dm | 0.579 [-,-] | 0.576 [-,-] | - | 0.576 | - | - | - | - | - | - | stack | short by 0.084 AUC, 5 of 5 econ |
| R7-pool-dm | +10 | ASIA | pool_dm | 0.554 [-,-] | 0.575 [-,-] | - | 0.571 | - | - | - | - | - | - | stack | short by 0.085 AUC, 5 of 5 econ |
| R7-pool-dm | +20 | ASIA | pool_dm | 0.566 [-,-] | 0.574 [-,-] | - | 0.573 | - | - | - | - | - | - | stack | short by 0.086 AUC, 5 of 5 econ |
| R7-pool-dm | pre | LONDON | pool_dm | 0.558 [-,-] | 0.573 [-,-] | - | 0.577 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-share | +30 | ASIA | pool_share | 0.570 [-,-] | 0.572 [-,-] | - | 0.573 | - | - | - | - | - | - | stack | short by 0.088 AUC, 5 of 5 econ |
| R7-pool-share | +20 | LONDON | pool_share | 0.521 [-,-] | 0.571 [-,-] | - | 0.575 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-rate | +30 | ASIA | asia_rate | 0.583 [-,-] | 0.571 [-,-] | - | 0.567 | - | - | - | - | - | - |  | short by 0.089 AUC, 5 of 5 econ |
| R7-asia-rate | +30 | POOLED | asia_rate | 0.583 [-,-] | 0.571 [-,-] | - | 0.567 | - | - | - | - | - | - |  | short by 0.109 AUC, 5 of 5 econ |
| R7-pool-frc | +20 | ASIA | pool_frc | 0.581 [-,-] | 0.570 [-,-] | - | 0.557 | - | - | - | - | - | - | stack | short by 0.090 AUC, 5 of 5 econ |
| R7-pool-first | +5 | NY | pool_first | 0.495 [-,-] | 0.569 [-,-] | - | 0.562 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-share | +5 | ASIA | pool_share | 0.542 [-,-] | 0.568 [-,-] | - | 0.564 | - | - | - | - | - | - | stack | short by 0.092 AUC, 5 of 5 econ |
| R7-pool-frc | +5 | ASIA | pool_frc | 0.552 [-,-] | 0.565 [-,-] | - | 0.565 | - | - | - | - | - | - | stack | short by 0.095 AUC, 5 of 5 econ |
| R7-pool-share | pre | NY | pool_share | 0.524 [-,-] | 0.565 [-,-] | - | 0.578 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-frc | +5 | LONDON | pool_frc | 0.508 [-,-] | 0.564 [-,-] | - | 0.564 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-share | +10 | LONDON | pool_share | 0.534 [-,-] | 0.564 [-,-] | - | 0.573 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-share | pre | ASIA | pool_share | 0.534 [-,-] | 0.564 [-,-] | - | 0.565 | - | - | - | - | - | - | stack | short by 0.096 AUC, 5 of 5 econ |
| R7-pool-dm | +15 | LONDON | pool_dm | 0.512 [-,-] | 0.562 [-,-] | - | 0.560 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-dm | +5 | LONDON | pool_dm | 0.520 [-,-] | 0.562 [-,-] | - | 0.557 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-rate | pre | ASIA | pool_rate | 0.535 [-,-] | 0.562 [-,-] | - | 0.558 | - | - | - | - | - | - | stack | short by 0.098 AUC, 5 of 5 econ |
| R7-pool-rate | +15 | NY | pool_rate | 0.540 [-,-] | 0.560 [-,-] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-share | +20 | POOLED | pool_share | 0.537 [-,-] | 0.560 [-,-] | - | 0.561 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| R7-pool-share | pre | POOLED | pool_share | 0.533 [-,-] | 0.559 [-,-] | - | 0.559 | - | - | - | - | - | - | stack | short by 0.121 AUC, 5 of 5 econ |
| R7-pool-share | +10 | POOLED | pool_share | 0.534 [-,-] | 0.558 [-,-] | - | 0.557 | - | - | - | - | - | - | stack | short by 0.122 AUC, 5 of 5 econ |
| R7-pool-frc | +10 | ASIA | pool_frc | 0.559 [-,-] | 0.558 [-,-] | - | 0.559 | - | - | - | - | - | - | stack | short by 0.102 AUC, 5 of 5 econ |
| R7-asia-rate | +20 | ASIA | asia_rate | 0.547 [-,-] | 0.557 [-,-] | - | 0.545 | - | - | - | - | - | - |  | short by 0.103 AUC, 5 of 5 econ |
| R7-asia-rate | +20 | POOLED | asia_rate | 0.547 [-,-] | 0.557 [-,-] | - | 0.545 | - | - | - | - | - | - |  | short by 0.123 AUC, 5 of 5 econ |
| R7-pool-rate | +15 | ASIA | pool_rate | 0.575 [-,-] | 0.557 [-,-] | - | 0.551 | - | - | - | - | - | - | stack | short by 0.103 AUC, 5 of 5 econ |
| R7-pool-frc | +30 | ASIA | pool_frc | 0.579 [-,-] | 0.556 [-,-] | - | 0.559 | - | - | - | - | - | - | stack | short by 0.104 AUC, 5 of 5 econ |
| R7-pool-rate | pre | POOLED | pool_rate | 0.529 [-,-] | 0.555 [-,-] | - | 0.555 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| R7-pool-rate | pre | LONDON | pool_rate | 0.519 [-,-] | 0.554 [-,-] | - | 0.553 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-frc | +20 | ASIA | asia_frc | 0.555 [-,-] | 0.554 [-,-] | - | 0.548 | - | - | - | - | - | - |  | short by 0.106 AUC, 5 of 5 econ |
| R7-asia-frc | +20 | POOLED | asia_frc | 0.555 [-,-] | 0.554 [-,-] | - | 0.548 | - | - | - | - | - | - |  | short by 0.126 AUC, 5 of 5 econ |
| R7-pool-rate | +10 | LONDON | pool_rate | 0.507 [-,-] | 0.554 [-,-] | - | 0.553 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-frc | +15 | ASIA | pool_frc | 0.566 [-,-] | 0.553 [-,-] | - | 0.547 | - | - | - | - | - | - | stack | short by 0.107 AUC, 5 of 5 econ |
| R7-asia-frc | +30 | ASIA | asia_frc | 0.573 [-,-] | 0.552 [-,-] | - | 0.540 | - | - | - | - | - | - |  | short by 0.108 AUC, 5 of 5 econ |
| R7-asia-frc | +30 | POOLED | asia_frc | 0.573 [-,-] | 0.552 [-,-] | - | 0.540 | - | - | - | - | - | - |  | short by 0.128 AUC, 5 of 5 econ |
| R7-asia-rate | +10 | ASIA | asia_rate | 0.527 [-,-] | 0.552 [-,-] | - | 0.537 | - | - | - | - | - | - |  | short by 0.108 AUC, 5 of 5 econ |
| R7-asia-rate | +10 | POOLED | asia_rate | 0.527 [-,-] | 0.552 [-,-] | - | 0.537 | - | - | - | - | - | - |  | short by 0.128 AUC, 5 of 5 econ |
| R7-pool-first | +15 | ASIA | pool_first | 0.530 [-,-] | 0.551 [-,-] | - | 0.553 | - | - | - | - | - | - | stack | short by 0.109 AUC, 5 of 5 econ |
| R7-asia-rate | +5 | ASIA | asia_rate | 0.546 [-,-] | 0.551 [-,-] | - | 0.533 | - | - | - | - | - | - |  | short by 0.109 AUC, 5 of 5 econ |
| R7-asia-rate | +5 | POOLED | asia_rate | 0.546 [-,-] | 0.551 [-,-] | - | 0.533 | - | - | - | - | - | - |  | short by 0.129 AUC, 5 of 5 econ |
| R7-pool-rate | pre | NY | pool_rate | 0.537 [-,-] | 0.551 [-,-] | - | 0.557 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-share | +15 | ASIA | asia_share | 0.519 [-,-] | 0.551 [-,-] | - | 0.548 | - | - | - | - | - | - |  | short by 0.109 AUC, 5 of 5 econ |
| R7-asia-share | +15 | POOLED | asia_share | 0.519 [-,-] | 0.551 [-,-] | - | 0.548 | - | - | - | - | - | - |  | short by 0.129 AUC, 5 of 5 econ |
| R7-pool-share | pre | LONDON | pool_share | 0.542 [-,-] | 0.550 [-,-] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-dm | +15 | POOLED | pool_dm | 0.533 [-,-] | 0.550 [-,-] | - | 0.549 | - | - | - | - | - | - | stack | short by 0.130 AUC, 5 of 5 econ |
| R7-pool-dm | pre | POOLED | pool_dm | 0.523 [-,-] | 0.549 [-,-] | - | 0.549 | - | - | - | - | - | - | stack | short by 0.131 AUC, 5 of 5 econ |
| R7-pool-dm | +30 | ASIA | pool_dm | 0.585 [-,-] | 0.548 [-,-] | - | 0.551 | - | - | - | - | - | - | stack | short by 0.112 AUC, 5 of 5 econ |
| R7-pool-share | +5 | LONDON | pool_share | 0.502 [-,-] | 0.548 [-,-] | - | 0.544 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-share | +15 | ASIA | pool_share | 0.537 [-,-] | 0.548 [-,-] | - | 0.546 | - | - | - | - | - | - | stack | short by 0.112 AUC, 5 of 5 econ |
| R7-pool-rate | +15 | POOLED | pool_rate | 0.535 [-,-] | 0.547 [-,-] | - | 0.547 | - | - | - | - | - | - | stack | short by 0.133 AUC, 5 of 5 econ |
| R7-pool-rate | +5 | ASIA | pool_rate | 0.556 [-,-] | 0.547 [-,-] | - | 0.545 | - | - | - | - | - | - | stack | short by 0.113 AUC, 5 of 5 econ |
| R7-pool-dm | +5 | ASIA | pool_dm | 0.530 [-,-] | 0.546 [-,-] | - | 0.548 | - | - | - | - | - | - | stack | short by 0.114 AUC, 5 of 5 econ |
| R7-pool-frc | pre | POOLED | pool_frc | 0.521 [-,-] | 0.545 [-,-] | - | 0.544 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| R7-asia-share | +20 | ASIA | asia_share | 0.525 [-,-] | 0.545 [-,-] | - | 0.539 | - | - | - | - | - | - |  | short by 0.115 AUC, 5 of 5 econ |
| R7-asia-share | +20 | POOLED | asia_share | 0.525 [-,-] | 0.545 [-,-] | - | 0.539 | - | - | - | - | - | - |  | short by 0.135 AUC, 5 of 5 econ |
| R7-asia-frc | +10 | ASIA | asia_frc | 0.548 [-,-] | 0.545 [-,-] | - | 0.533 | - | - | - | - | - | - |  | short by 0.115 AUC, 5 of 5 econ |
| R7-asia-frc | +10 | POOLED | asia_frc | 0.548 [-,-] | 0.545 [-,-] | - | 0.533 | - | - | - | - | - | - |  | short by 0.135 AUC, 5 of 5 econ |
| R7-pool-share | +5 | POOLED | pool_share | 0.519 [-,-] | 0.544 [-,-] | - | 0.542 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| R7-pool-first | +20 | ASIA | pool_first | 0.515 [-,-] | 0.543 [-,-] | - | 0.547 | - | - | - | - | - | - | stack | short by 0.117 AUC, 5 of 5 econ |
| R7-pool-first | +30 | POOLED | pool_first | 0.531 [-,-] | 0.541 [-,-] | - | 0.542 | - | - | - | - | - | - | stack | short by 0.139 AUC, 5 of 5 econ |
| R7-pool-frc | pre | ASIA | pool_frc | 0.526 [-,-] | 0.541 [-,-] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.119 AUC, 5 of 5 econ |
| R7-pool-rate | +10 | POOLED | pool_rate | 0.533 [-,-] | 0.540 [-,-] | - | 0.541 | - | - | - | - | - | - | stack | short by 0.140 AUC, 5 of 5 econ |
| R7-pool-dm | pre | ASIA | pool_dm | 0.520 [-,-] | 0.540 [-,-] | - | 0.538 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| R7-asia-share | +5 | ASIA | asia_share | 0.519 [-,-] | 0.540 [-,-] | - | 0.528 | - | - | - | - | - | - |  | short by 0.120 AUC, 5 of 5 econ |
| R7-asia-share | +5 | POOLED | asia_share | 0.519 [-,-] | 0.540 [-,-] | - | 0.528 | - | - | - | - | - | - |  | short by 0.140 AUC, 5 of 5 econ |
| R7-pool-rate | +10 | NY | pool_rate | 0.553 [-,-] | 0.540 [-,-] | - | 0.537 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-first | +30 | ASIA | asia_first | 0.496 [-,-] | 0.538 [-,-] | - | 0.531 | - | - | - | - | - | - |  | short by 0.122 AUC, 5 of 5 econ |
| R7-asia-first | +30 | POOLED | asia_first | 0.496 [-,-] | 0.538 [-,-] | - | 0.531 | - | - | - | - | - | - |  | short by 0.142 AUC, 5 of 5 econ |
| R7-pool-dm | +20 | LONDON | pool_dm | 0.513 [-,-] | 0.538 [-,-] | - | 0.547 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-rate | +10 | ASIA | pool_rate | 0.544 [-,-] | 0.537 [-,-] | - | 0.540 | - | - | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| R7-pool-frc | +5 | POOLED | pool_frc | 0.512 [-,-] | 0.537 [-,-] | - | 0.536 | - | - | - | - | - | - | stack | short by 0.143 AUC, 5 of 5 econ |
| R7-pool-frc | +20 | LONDON | pool_frc | 0.506 [-,-] | 0.536 [-,-] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-dm | +20 | POOLED | pool_dm | 0.530 [-,-] | 0.536 [-,-] | - | 0.536 | - | - | - | - | - | - | stack | short by 0.144 AUC, 5 of 5 econ |
| R7-pool-frc | +20 | POOLED | pool_frc | 0.531 [-,-] | 0.535 [-,-] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| R7-pool-rate | +5 | POOLED | pool_rate | 0.528 [-,-] | 0.533 [-,-] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| R7-pool-share | +30 | POOLED | pool_share | 0.533 [-,-] | 0.532 [-,-] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| R7-pool-rate | +30 | POOLED | pool_rate | 0.528 [-,-] | 0.532 [-,-] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| R7-pool-dm | pre | NY | pool_dm | 0.493 [-,-] | 0.532 [-,-] | - | 0.535 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | +10 | ASIA | pool_first | 0.520 [-,-] | 0.531 [-,-] | - | 0.547 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| R7-pool-rate | +20 | POOLED | pool_rate | 0.529 [-,-] | 0.531 [-,-] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.149 AUC, 5 of 5 econ |
| R7-asia-first | +15 | ASIA | asia_first | 0.496 [-,-] | 0.531 [-,-] | - | 0.529 | - | - | - | - | - | - |  | short by 0.129 AUC, 5 of 5 econ |
| R7-asia-first | +15 | POOLED | asia_first | 0.496 [-,-] | 0.531 [-,-] | - | 0.529 | - | - | - | - | - | - |  | short by 0.149 AUC, 5 of 5 econ |
| R7-pool-dm | +5 | POOLED | pool_dm | 0.514 [-,-] | 0.531 [-,-] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.149 AUC, 5 of 5 econ |
| R7-pool-first | +5 | POOLED | pool_first | 0.503 [-,-] | 0.530 [-,-] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.150 AUC, 5 of 5 econ |
| R7-pool-rate | +30 | NY | pool_rate | 0.523 [-,-] | 0.530 [-,-] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-rate | +5 | LONDON | pool_rate | 0.514 [-,-] | 0.530 [-,-] | - | 0.531 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-frc | pre | ASIA | asia_frc | 0.535 [-,-] | 0.530 [-,-] | - | 0.529 | - | - | - | - | - | - |  | short by 0.130 AUC, 5 of 5 econ |
| R7-asia-frc | pre | POOLED | asia_frc | 0.535 [-,-] | 0.530 [-,-] | - | 0.529 | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| R7-pool-first | pre | NY | pool_first | 0.524 [-,-] | 0.530 [-,-] | - | 0.540 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-rate | +15 | ASIA | asia_rate | 0.530 [-,-] | 0.530 [-,-] | - | 0.514 | - | - | - | - | - | - |  | short by 0.130 AUC, 5 of 5 econ |
| R7-asia-rate | +15 | POOLED | asia_rate | 0.530 [-,-] | 0.530 [-,-] | - | 0.514 | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| R7-pool-share | +15 | POOLED | pool_share | 0.521 [-,-] | 0.529 [-,-] | - | 0.529 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| R7-pool-first | +30 | NY | pool_first | 0.526 [-,-] | 0.528 [-,-] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | +10 | LONDON | pool_first | 0.485 [-,-] | 0.528 [-,-] | - | 0.530 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-frc | +15 | POOLED | pool_frc | 0.525 [-,-] | 0.527 [-,-] | - | 0.525 | - | - | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| R7-pool-share | +15 | NY | pool_share | 0.524 [-,-] | 0.527 [-,-] | - | 0.519 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-frc | +15 | LONDON | pool_frc | 0.505 [-,-] | 0.526 [-,-] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-dm | +30 | NY | pool_dm | 0.523 [-,-] | 0.526 [-,-] | - | 0.536 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-share | +10 | ASIA | asia_share | 0.518 [-,-] | 0.526 [-,-] | - | 0.516 | - | - | - | - | - | - |  | short by 0.134 AUC, 5 of 5 econ |
| R7-asia-share | +10 | POOLED | asia_share | 0.518 [-,-] | 0.526 [-,-] | - | 0.516 | - | - | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| R7-pool-dm | +10 | LONDON | pool_dm | 0.511 [-,-] | 0.523 [-,-] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | pre | ASIA | pool_first | 0.500 [-,-] | 0.523 [-,-] | - | 0.527 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R7-pool-dm | +10 | POOLED | pool_dm | 0.516 [-,-] | 0.522 [-,-] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| R7-pool-dm | +30 | POOLED | pool_dm | 0.535 [-,-] | 0.522 [-,-] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| R7-pool-share | +20 | NY | pool_share | 0.505 [-,-] | 0.522 [-,-] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | +10 | POOLED | pool_first | 0.498 [-,-] | 0.521 [-,-] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| R7-pool-rate | +5 | NY | pool_rate | 0.509 [-,-] | 0.520 [-,-] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | +15 | POOLED | pool_first | 0.507 [-,-] | 0.520 [-,-] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| R7-pool-frc | +30 | POOLED | pool_frc | 0.527 [-,-] | 0.520 [-,-] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| R7-asia-first | +20 | ASIA | asia_first | 0.501 [-,-] | 0.518 [-,-] | - | 0.521 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| R7-asia-first | +20 | POOLED | asia_first | 0.501 [-,-] | 0.518 [-,-] | - | 0.521 | - | - | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| R7-pool-share | +5 | NY | pool_share | 0.510 [-,-] | 0.517 [-,-] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-frc | +5 | ASIA | asia_frc | 0.537 [-,-] | 0.516 [-,-] | - | 0.513 | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| R7-asia-frc | +5 | POOLED | asia_frc | 0.537 [-,-] | 0.516 [-,-] | - | 0.513 | - | - | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| R7-pool-share | +30 | NY | pool_share | 0.506 [-,-] | 0.515 [-,-] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | +15 | NY | pool_first | 0.483 [-,-] | 0.515 [-,-] | - | 0.505 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | +10 | NY | pool_first | 0.488 [-,-] | 0.515 [-,-] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | +5 | ASIA | pool_first | 0.512 [-,-] | 0.515 [-,-] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| R7-pool-first | pre | POOLED | pool_first | 0.506 [-,-] | 0.514 [-,-] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| R7-pool-first | +5 | LONDON | pool_first | 0.503 [-,-] | 0.514 [-,-] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-rate | +15 | LONDON | pool_rate | 0.489 [-,-] | 0.512 [-,-] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-share | +10 | NY | pool_share | 0.493 [-,-] | 0.512 [-,-] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-rate | pre | ASIA | asia_rate | 0.501 [-,-] | 0.510 [-,-] | - | 0.505 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| R7-asia-rate | pre | POOLED | asia_rate | 0.501 [-,-] | 0.510 [-,-] | - | 0.505 | - | - | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| R7-pool-first | +20 | POOLED | pool_first | 0.498 [-,-] | 0.508 [-,-] | - | 0.508 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R7-pool-frc | +30 | LONDON | pool_frc | 0.499 [-,-] | 0.506 [-,-] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-frc | +15 | ASIA | asia_frc | 0.529 [-,-] | 0.505 [-,-] | - | 0.493 | - | - | - | - | - | - |  | short by 0.155 AUC, 5 of 5 econ |
| R7-asia-frc | +15 | POOLED | asia_frc | 0.529 [-,-] | 0.505 [-,-] | - | 0.493 | - | - | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| R7-pool-dm | +15 | NY | pool_dm | 0.502 [-,-] | 0.504 [-,-] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-frc | pre | NY | pool_frc | 0.477 [-,-] | 0.504 [-,-] | - | 0.505 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-frc | +10 | POOLED | pool_frc | 0.500 [-,-] | 0.504 [-,-] | - | 0.505 | - | - | - | - | - | - | stack | short by 0.176 AUC, 5 of 5 econ |
| R7-pool-first | +15 | LONDON | pool_first | 0.506 [-,-] | 0.503 [-,-] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | +20 | NY | pool_first | 0.498 [-,-] | 0.503 [-,-] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | +30 | LONDON | pool_first | 0.510 [-,-] | 0.502 [-,-] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-rate | +20 | NY | pool_rate | 0.517 [-,-] | 0.502 [-,-] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-share | +15 | LONDON | pool_share | 0.499 [-,-] | 0.502 [-,-] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-first | +10 | ASIA | asia_first | 0.495 [-,-] | 0.502 [-,-] | - | 0.506 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| R7-asia-first | +10 | POOLED | asia_first | 0.495 [-,-] | 0.502 [-,-] | - | 0.506 | - | - | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| R7-pool-frc | +10 | LONDON | pool_frc | 0.491 [-,-] | 0.500 [-,-] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | pre | LONDON | pool_first | 0.496 [-,-] | 0.500 [-,-] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-first | pre | ASIA | asia_first | 0.488 [-,-] | 0.499 [-,-] | - | 0.497 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| R7-asia-first | pre | POOLED | asia_first | 0.488 [-,-] | 0.499 [-,-] | - | 0.497 | - | - | - | - | - | - |  | short by 0.181 AUC, 5 of 5 econ |
| R7-pool-rate | +20 | LONDON | pool_rate | 0.504 [-,-] | 0.497 [-,-] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-frc | +20 | NY | pool_frc | 0.504 [-,-] | 0.494 [-,-] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-frc | +15 | NY | pool_frc | 0.498 [-,-] | 0.494 [-,-] | - | 0.496 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-share | +30 | LONDON | pool_share | 0.516 [-,-] | 0.494 [-,-] | - | 0.488 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-dm | +30 | LONDON | pool_dm | 0.496 [-,-] | 0.493 [-,-] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-dm | +20 | NY | pool_dm | 0.509 [-,-] | 0.493 [-,-] | - | 0.493 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-frc | +30 | NY | pool_frc | 0.501 [-,-] | 0.492 [-,-] | - | 0.497 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-first | +20 | LONDON | pool_first | 0.482 [-,-] | 0.485 [-,-] | - | 0.476 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-dm | +5 | NY | pool_dm | 0.489 [-,-] | 0.484 [-,-] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-first | +5 | ASIA | asia_first | 0.491 [-,-] | 0.483 [-,-] | - | 0.480 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| R7-asia-first | +5 | POOLED | asia_first | 0.491 [-,-] | 0.483 [-,-] | - | 0.480 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| R7-pool-frc | +5 | NY | pool_frc | 0.470 [-,-] | 0.481 [-,-] | - | 0.488 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-asia-share | pre | ASIA | asia_share | 0.493 [-,-] | 0.480 [-,-] | - | 0.470 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| R7-asia-share | pre | POOLED | asia_share | 0.493 [-,-] | 0.480 [-,-] | - | 0.470 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| R7-pool-rate | +30 | LONDON | pool_rate | 0.475 [-,-] | 0.463 [-,-] | - | 0.458 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-dm | +10 | NY | pool_dm | 0.481 [-,-] | 0.462 [-,-] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R7-pool-frc | +10 | NY | pool_frc | 0.446 [-,-] | 0.443 [-,-] | - | 0.451 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |

One-sentence notes:
- R7-asia-first 0 ASIA: strata hold 0.497 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 0 POOLED: strata hold 0.497 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 5 ASIA: strata hold 0.480 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 5 POOLED: strata hold 0.480 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 10 ASIA: strata hold 0.506 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 10 POOLED: strata hold 0.506 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 15 ASIA: strata hold 0.529 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 15 POOLED: strata hold 0.529 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 20 ASIA: strata hold 0.521 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 20 POOLED: strata hold 0.521 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 30 ASIA: strata hold 0.531 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-asia-first 30 POOLED: strata hold 0.531 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 0 ASIA: strata hold 0.529 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 0 POOLED: strata hold 0.529 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 5 ASIA: strata hold 0.513 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 5 POOLED: strata hold 0.513 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 10 ASIA: strata hold 0.533 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 10 POOLED: strata hold 0.533 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 15 ASIA: strata hold 0.493 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 15 POOLED: strata hold 0.493 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 20 ASIA: strata hold 0.548 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 20 POOLED: strata hold 0.548 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 30 ASIA: strata hold 0.540 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-asia-frc 30 POOLED: strata hold 0.540 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 0 ASIA: strata hold 0.505 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 0 POOLED: strata hold 0.505 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 5 ASIA: strata hold 0.533 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 5 POOLED: strata hold 0.533 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 10 ASIA: strata hold 0.537 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 10 POOLED: strata hold 0.537 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 15 ASIA: strata hold 0.514 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 15 POOLED: strata hold 0.514 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 20 ASIA: strata hold 0.545 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 20 POOLED: strata hold 0.545 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 30 ASIA: strata hold 0.567 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-asia-rate 30 POOLED: strata hold 0.567 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 0 ASIA: strata hold 0.470 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 0 POOLED: strata hold 0.470 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 5 ASIA: strata hold 0.528 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 5 POOLED: strata hold 0.528 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 10 ASIA: strata hold 0.516 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 10 POOLED: strata hold 0.516 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 15 ASIA: strata hold 0.548 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 15 POOLED: strata hold 0.548 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 20 ASIA: strata hold 0.539 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 20 POOLED: strata hold 0.539 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 30 ASIA: strata hold 0.576 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-asia-share 30 POOLED: strata hold 0.576 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 0 ASIA: strata hold 0.538 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 0 LONDON: strata hold 0.577 vs R0u 0.448; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 0 NY: strata hold 0.535 vs R0u 0.455; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 0 POOLED: strata hold 0.549 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 5 ASIA: strata hold 0.548 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 5 LONDON: strata hold 0.557 vs R0u 0.494; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 5 NY: strata hold 0.484 vs R0u 0.447; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 5 POOLED: strata hold 0.528 vs R0u 0.469; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 10 ASIA: strata hold 0.571 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 10 LONDON: strata hold 0.520 vs R0u 0.457; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 10 NY: strata hold 0.468 vs R0u 0.419; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 10 POOLED: strata hold 0.523 vs R0u 0.455; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 15 ASIA: strata hold 0.576 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 15 LONDON: strata hold 0.560 vs R0u 0.425; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 15 NY: strata hold 0.503 vs R0u 0.452; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 15 POOLED: strata hold 0.549 vs R0u 0.443; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 20 ASIA: strata hold 0.573 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 20 LONDON: strata hold 0.547 vs R0u 0.502; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 20 NY: strata hold 0.493 vs R0u 0.489; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 20 POOLED: strata hold 0.536 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 30 ASIA: strata hold 0.551 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 30 LONDON: strata hold 0.495 vs R0u 0.444; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 30 NY: strata hold 0.536 vs R0u 0.404; CPCV/noise/perm not run; below FOUND bar
- R7-pool-dm 30 POOLED: strata hold 0.522 vs R0u 0.437; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 0 ASIA: strata hold 0.527 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 0 LONDON: strata hold 0.495 vs R0u 0.448; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 0 NY: strata hold 0.540 vs R0u 0.455; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 0 POOLED: strata hold 0.515 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 5 ASIA: strata hold 0.522 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 5 LONDON: strata hold 0.518 vs R0u 0.494; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 5 NY: strata hold 0.562 vs R0u 0.447; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 5 POOLED: strata hold 0.532 vs R0u 0.469; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 10 ASIA: strata hold 0.547 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 10 LONDON: strata hold 0.530 vs R0u 0.457; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 10 NY: strata hold 0.514 vs R0u 0.419; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 10 POOLED: strata hold 0.523 vs R0u 0.455; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 15 ASIA: strata hold 0.553 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 15 LONDON: strata hold 0.514 vs R0u 0.425; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 15 NY: strata hold 0.505 vs R0u 0.452; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 15 POOLED: strata hold 0.521 vs R0u 0.443; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 20 ASIA: strata hold 0.547 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 20 LONDON: strata hold 0.476 vs R0u 0.502; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 20 NY: strata hold 0.506 vs R0u 0.489; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 20 POOLED: strata hold 0.508 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 30 ASIA: strata hold 0.597 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 30 LONDON: strata hold 0.507 vs R0u 0.444; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 30 NY: strata hold 0.534 vs R0u 0.404; CPCV/noise/perm not run; below FOUND bar
- R7-pool-first 30 POOLED: strata hold 0.542 vs R0u 0.437; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 0 ASIA: strata hold 0.531 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 0 LONDON: strata hold 0.600 vs R0u 0.448; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 0 NY: strata hold 0.505 vs R0u 0.455; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 0 POOLED: strata hold 0.544 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 5 ASIA: strata hold 0.565 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 5 LONDON: strata hold 0.564 vs R0u 0.494; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 5 NY: strata hold 0.488 vs R0u 0.447; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 5 POOLED: strata hold 0.536 vs R0u 0.469; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 10 ASIA: strata hold 0.559 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 10 LONDON: strata hold 0.501 vs R0u 0.457; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 10 NY: strata hold 0.451 vs R0u 0.419; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 10 POOLED: strata hold 0.505 vs R0u 0.455; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 15 ASIA: strata hold 0.547 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 15 LONDON: strata hold 0.518 vs R0u 0.425; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 15 NY: strata hold 0.496 vs R0u 0.452; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 15 POOLED: strata hold 0.525 vs R0u 0.443; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 20 ASIA: strata hold 0.557 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 20 LONDON: strata hold 0.534 vs R0u 0.502; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 20 NY: strata hold 0.495 vs R0u 0.489; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 20 POOLED: strata hold 0.530 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 30 ASIA: strata hold 0.559 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 30 LONDON: strata hold 0.512 vs R0u 0.444; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 30 NY: strata hold 0.497 vs R0u 0.404; CPCV/noise/perm not run; below FOUND bar
- R7-pool-frc 30 POOLED: strata hold 0.517 vs R0u 0.437; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 0 ASIA: strata hold 0.558 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 0 LONDON: strata hold 0.553 vs R0u 0.448; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 0 NY: strata hold 0.557 vs R0u 0.455; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 0 POOLED: strata hold 0.555 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 5 ASIA: strata hold 0.545 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 5 LONDON: strata hold 0.531 vs R0u 0.494; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 5 NY: strata hold 0.509 vs R0u 0.447; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 5 POOLED: strata hold 0.532 vs R0u 0.469; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 10 ASIA: strata hold 0.540 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 10 LONDON: strata hold 0.553 vs R0u 0.457; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 10 NY: strata hold 0.537 vs R0u 0.419; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 10 POOLED: strata hold 0.541 vs R0u 0.455; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 15 ASIA: strata hold 0.551 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 15 LONDON: strata hold 0.511 vs R0u 0.425; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 15 NY: strata hold 0.552 vs R0u 0.452; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 15 POOLED: strata hold 0.547 vs R0u 0.443; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 20 ASIA: strata hold 0.579 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 20 LONDON: strata hold 0.501 vs R0u 0.502; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 20 NY: strata hold 0.501 vs R0u 0.489; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 20 POOLED: strata hold 0.530 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 30 ASIA: strata hold 0.586 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 30 LONDON: strata hold 0.458 vs R0u 0.444; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 30 NY: strata hold 0.529 vs R0u 0.404; CPCV/noise/perm not run; below FOUND bar
- R7-pool-rate 30 POOLED: strata hold 0.531 vs R0u 0.437; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 0 ASIA: strata hold 0.565 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 0 LONDON: strata hold 0.542 vs R0u 0.448; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 0 NY: strata hold 0.578 vs R0u 0.455; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 0 POOLED: strata hold 0.559 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 5 ASIA: strata hold 0.564 vs R0u 0.464; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 5 LONDON: strata hold 0.544 vs R0u 0.494; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 5 NY: strata hold 0.514 vs R0u 0.447; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 5 POOLED: strata hold 0.542 vs R0u 0.469; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 10 ASIA: strata hold 0.601 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 10 LONDON: strata hold 0.573 vs R0u 0.457; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 10 NY: strata hold 0.503 vs R0u 0.419; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 10 POOLED: strata hold 0.557 vs R0u 0.455; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 15 ASIA: strata hold 0.546 vs R0u 0.458; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 15 LONDON: strata hold 0.506 vs R0u 0.425; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 15 NY: strata hold 0.519 vs R0u 0.452; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 15 POOLED: strata hold 0.529 vs R0u 0.443; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 20 ASIA: strata hold 0.588 vs R0u 0.491; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 20 LONDON: strata hold 0.575 vs R0u 0.502; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 20 NY: strata hold 0.534 vs R0u 0.489; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 20 POOLED: strata hold 0.561 vs R0u 0.490; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 30 ASIA: strata hold 0.573 vs R0u 0.463; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 30 LONDON: strata hold 0.488 vs R0u 0.444; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 30 NY: strata hold 0.518 vs R0u 0.404; CPCV/noise/perm not run; below FOUND bar
- R7-pool-share 30 POOLED: strata hold 0.530 vs R0u 0.437; CPCV/noise/perm not run; below FOUND bar
