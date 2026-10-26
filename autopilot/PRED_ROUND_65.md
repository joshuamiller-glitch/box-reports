# PRED ROUND 65 - block A round 10 - A10-G-state

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.567 [0.55,0.59]
Gap to FOUND: 0.113 AUC, 5 of 5 economic conditions short.
not found - short by 0.113 AUC and 5 of 5 economic conditions

prereg 39bad3a6e3b4ed60dbac3e3b054c3a8865436b09a17265eda6096c8e6f938102 ; trials added 300 ; truncation audit {'decisions': 300, 'mismatches': 0, 'fixed_and_rerun': True} ; holdout scored True ; feature store ['l2vast/pred/store/A_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A10-G-state | sig | NY | V4_fast | 0.559 [-,-] | 0.567 [0.55,0.59] | - | - | - | - | - | - | - | - |  | short by 0.113 AUC, 5 of 5 econ |
| A10-G-state | sig | NY | V4_dur | 0.561 [-,-] | 0.567 [0.55,0.59] | - | - | - | - | - | - | - | - |  | short by 0.113 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/ST | V4_fast | 0.558 [-,-] | 0.567 [0.54,0.59] | - | - | - | - | - | - | - | - |  | short by 0.113 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/HM | V4_dur | 0.559 [-,-] | 0.567 [0.53,0.60] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | NY/HM | V4_fast | 0.560 [-,-] | 0.564 [0.53,0.59] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | NY/ST | V4_dur | 0.561 [-,-] | 0.564 [0.54,0.59] | - | - | - | - | - | - | - | - |  | short by 0.116 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/ST | M0 | 0.539 [-,-] | 0.544 [0.52,0.57] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY | M0 | 0.545 [-,-] | 0.541 [0.52,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/ST | V3_firstlater | 0.518 [-,-] | 0.535 [0.52,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/HM | M0 | 0.553 [-,-] | 0.534 [0.50,0.57] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/ST | V1_state | 0.519 [-,-] | 0.534 [0.51,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/ST | V4_fast | 0.519 [-,-] | 0.533 [0.51,0.55] | - | - | - | - | - | - | - | - |  | promising: short by 0.147 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/ST | V3_firstlater | 0.515 [-,-] | 0.532 [0.51,0.55] | - | - | - | - | - | - | - | - |  | promising: short by 0.148 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/ST | V4_fast | 0.527 [-,-] | 0.531 [0.51,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/ST | V0_base | 0.506 [-,-] | 0.531 [0.50,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/ST | V1_state | 0.518 [-,-] | 0.531 [0.51,0.55] | - | - | - | - | - | - | - | - |  | promising: short by 0.149 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/ST | V4_dur | 0.523 [-,-] | 0.530 [0.51,0.55] | - | - | - | - | - | - | - | - |  | promising: short by 0.150 AUC, 5 of 5 econ |
| A10-G-state | sig | NY | V4_fast | 0.514 [-,-] | 0.528 [0.51,0.55] | - | - | - | - | - | - | - | - |  | promising: short by 0.152 AUC, 5 of 5 econ |
| A10-G-state | sig | NY | V4_dur | 0.517 [-,-] | 0.528 [0.51,0.55] | - | - | - | - | - | - | - | - |  | promising: short by 0.152 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/ST | V0_base | 0.503 [-,-] | 0.528 [0.50,0.55] | - | - | - | - | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/ST | V4_dur | 0.526 [-,-] | 0.528 [0.51,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | V4_fast | 0.521 [-,-] | 0.527 [0.51,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | V4_dur | 0.521 [-,-] | 0.525 [0.51,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY | V3_firstlater | 0.515 [-,-] | 0.525 [0.51,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V4_fast | 0.525 [-,-] | 0.524 [0.49,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V4_fast | 0.523 [-,-] | 0.523 [0.49,0.56] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | NY/ST | M0 | 0.511 [-,-] | 0.523 [0.50,0.55] | - | - | - | - | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| A10-G-state | sig | ASIA/HM | V0_base | 0.511 [-,-] | 0.523 [0.48,0.56] | - | - | - | - | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/ST | V4_fast | 0.517 [-,-] | 0.522 [0.50,0.54] | - | - | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/ST | V1c_cluster | 0.500 [-,-] | 0.522 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY | V0_base | 0.503 [-,-] | 0.522 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | V0_base | 0.510 [-,-] | 0.522 [0.48,0.56] | - | - | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| A10-G-state | sig | NY | V3_firstlater | 0.512 [-,-] | 0.522 [0.50,0.54] | - | - | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| A10-G-state | sig | NY | V1_state | 0.513 [-,-] | 0.522 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/HM | V4_dur | 0.507 [-,-] | 0.520 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| A10-G-state | sig | NY | V1_state | 0.510 [-,-] | 0.520 [0.50,0.54] | - | - | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/ST | V1c_cluster | 0.498 [-,-] | 0.519 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/HM | V4_dur | 0.512 [-,-] | 0.519 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY | V0_base | 0.499 [-,-] | 0.519 [0.50,0.54] | - | - | - | - | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/ST | V4_dur | 0.516 [-,-] | 0.518 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/HM | V4_fast | 0.507 [-,-] | 0.518 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/HM | V4_fast | 0.511 [-,-] | 0.517 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | V4_fast | 0.510 [-,-] | 0.517 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| A10-G-state | sig | ASIA | V4_fast | 0.508 [-,-] | 0.517 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/ST | M0 | 0.515 [-,-] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | M0 | 0.522 [-,-] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY | M0 | 0.513 [-,-] | 0.517 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| A10-G-state | sig | ASIA | V4_fast | 0.505 [-,-] | 0.516 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| A10-G-state | sig | LONDON/ST | V2_side | 0.512 [-,-] | 0.516 [0.48,0.56] | - | - | - | - | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/HM | M0 | 0.530 [-,-] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | V4_dur | 0.510 [-,-] | 0.516 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| A10-G-state | sig | LONDON/ST | V4_fast | 0.518 [-,-] | 0.515 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| A10-G-state | sig | LONDON/ST | V4_fast | 0.517 [-,-] | 0.515 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| A10-G-state | sig | NY | V1c_cluster | 0.502 [-,-] | 0.515 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/ST | V0_base | 0.510 [-,-] | 0.513 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| A10-G-state | sig | ASIA/ST | V4_dur | 0.521 [-,-] | 0.513 [0.47,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V4_dur | 0.519 [-,-] | 0.513 [0.47,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/ST | V2_side | 0.511 [-,-] | 0.513 [0.48,0.55] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | NY | V1c_cluster | 0.498 [-,-] | 0.513 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/ST | V1_state | 0.511 [-,-] | 0.512 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/ST | V1_state | 0.511 [-,-] | 0.512 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/ST | V0_base | 0.505 [-,-] | 0.512 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/ST | V0_base | 0.504 [-,-] | 0.511 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A10-G-state | sig | LONDON/ST | V0_base | 0.510 [-,-] | 0.511 [0.48,0.55] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | LONDON/ST | V3_firstlater | 0.498 [-,-] | 0.511 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/ST | V3_firstlater | 0.502 [-,-] | 0.510 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/ST | V3_firstlater | 0.500 [-,-] | 0.509 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V4_dur | 0.501 [-,-] | 0.509 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/HM | V3_firstlater | 0.513 [-,-] | 0.509 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/ST | V3_firstlater | 0.498 [-,-] | 0.509 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/ST | V4_dur | 0.512 [-,-] | 0.509 [0.47,0.54] | - | - | - | - | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| A10-G-state | sig | ASIA | V4_dur | 0.508 [-,-] | 0.509 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/ST | V1_state | 0.512 [-,-] | 0.508 [0.48,0.55] | - | - | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| A10-G-state | sig | LONDON/ST | V4_dur | 0.513 [-,-] | 0.508 [0.47,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | POOLED | V0_base | 0.502 [-,-] | 0.508 [0.50,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/HM | V0_base | 0.502 [-,-] | 0.508 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | V0_base | 0.501 [-,-] | 0.508 [0.49,0.52] | - | - | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| A10-G-state | sig | ASIA | V4_dur | 0.505 [-,-] | 0.508 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V2_side | 0.496 [-,-] | 0.507 [0.47,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V4_fast | 0.500 [-,-] | 0.507 [0.48,0.53] | - | - | - | - | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| A10-G-state | sig | ASIA/ST | V2_side | 0.496 [-,-] | 0.507 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/HM | M0 | 0.517 [-,-] | 0.506 [0.47,0.54] | - | - | - | - | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/ST | V2_side | 0.505 [-,-] | 0.505 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/ST | V1_state | 0.511 [-,-] | 0.505 [0.47,0.55] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | POOLED | V1_state | 0.504 [-,-] | 0.505 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/HM | V3_firstlater | 0.506 [-,-] | 0.505 [0.48,0.54] | - | - | - | - | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED | V1_state | 0.505 [-,-] | 0.505 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | V4_fast | 0.487 [-,-] | 0.505 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | V3_firstlater | 0.499 [-,-] | 0.505 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/HM | V1c_cluster | 0.505 [-,-] | 0.504 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/HM | V0_base | 0.494 [-,-] | 0.504 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/ST | V2_side | 0.504 [-,-] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | V3_firstlater | 0.498 [-,-] | 0.504 [0.49,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/ST | M0 | 0.499 [-,-] | 0.504 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V0_base | 0.499 [-,-] | 0.503 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | V4_fast | 0.483 [-,-] | 0.503 [0.46,0.54] | - | - | - | - | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/HM | V0_base | 0.497 [-,-] | 0.503 [0.48,0.52] | - | - | - | - | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/HM | V1c_cluster | 0.498 [-,-] | 0.503 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | M0 | 0.503 [-,-] | 0.502 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/HM | V2_side | 0.509 [-,-] | 0.502 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | V2_side | 0.500 [-,-] | 0.501 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/ST | V2_side | 0.507 [-,-] | 0.501 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | V2_side | 0.500 [-,-] | 0.501 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | V4_fast | 0.505 [-,-] | 0.501 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | ASIA/HM | V3_firstlater | 0.482 [-,-] | 0.501 [0.46,0.54] | - | - | - | - | - | - | - | - |  | short by 0.179 AUC, 5 of 5 econ |
| A10-G-state | sig | NY/HM | V1_state | 0.498 [-,-] | 0.501 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | V4_fast | 0.504 [-,-] | 0.501 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | LONDON/ST | V1c_cluster | 0.501 [-,-] | 0.501 [0.47,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | NY/HM | V1_state | 0.504 [-,-] | 0.501 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | V3_firstlater | 0.479 [-,-] | 0.501 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY | V2_side | 0.509 [-,-] | 0.500 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/ST | V1c_cluster | 0.499 [-,-] | 0.500 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | V1_state | 0.492 [-,-] | 0.500 [0.47,0.53] | - | - | - | - | - | - | - | - |  | short by 0.180 AUC, 5 of 5 econ |
| A10-G-state | sig | ASIA/HM | M0 | 0.500 [-,-] | 0.500 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | M0 | 0.498 [-,-] | 0.500 [0.46,0.54] | - | - | - | - | - | - | - | - |  | short by 0.180 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED/HM | M0 | 0.509 [-,-] | 0.500 [0.47,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | LONDON | V2_side | 0.500 [-,-] | 0.500 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | V4_dur | 0.503 [-,-] | 0.500 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | LONDON | V4_dur | 0.504 [-,-] | 0.500 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | NY/HM | V2_side | 0.513 [-,-] | 0.500 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | V1_state | 0.491 [-,-] | 0.500 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/ST | V1c_cluster | 0.498 [-,-] | 0.500 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | V2_side | 0.504 [-,-] | 0.499 [0.49,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | V0_base | 0.500 [-,-] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | V2_side | 0.503 [-,-] | 0.499 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | V2_side | 0.499 [-,-] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/ST | V1c_cluster | 0.500 [-,-] | 0.499 [0.47,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | ASIA/HM | V4_dur | 0.491 [-,-] | 0.499 [0.45,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | V0_base | 0.502 [-,-] | 0.498 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | V0_base | 0.500 [-,-] | 0.498 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | V0_base | 0.502 [-,-] | 0.498 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY | V2_side | 0.505 [-,-] | 0.498 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V3_firstlater | 0.496 [-,-] | 0.497 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | V4_dur | 0.487 [-,-] | 0.497 [0.45,0.54] | - | - | - | - | - | - | - | - |  | short by 0.183 AUC, 5 of 5 econ |
| A10-G-state | sig | POOLED | V1c_cluster | 0.497 [-,-] | 0.497 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | V3_firstlater | 0.493 [-,-] | 0.497 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V3_firstlater | 0.495 [-,-] | 0.497 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED | V1c_cluster | 0.496 [-,-] | 0.496 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | M0 | 0.511 [-,-] | 0.496 [0.45,0.54] | - | - | - | - | - | - | - | - |  | short by 0.184 AUC, 5 of 5 econ |
| A10-G-state | sig | LONDON | V1_state | 0.503 [-,-] | 0.496 [0.47,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | LONDON | V3_firstlater | 0.494 [-,-] | 0.496 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | NY/ST | V2_side | 0.503 [-,-] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V1_state | 0.496 [-,-] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | V2_side | 0.505 [-,-] | 0.494 [0.44,0.54] | - | - | - | - | - | - | - | - |  | short by 0.186 AUC, 5 of 5 econ |
| A10-G-state | sig | LONDON | V1_state | 0.503 [-,-] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| A10-G-state | sig | ASIA/HM | V2_side | 0.505 [-,-] | 0.494 [0.44,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V1_state | 0.497 [-,-] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | M0 | 0.499 [-,-] | 0.494 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | V1c_cluster | 0.497 [-,-] | 0.494 [0.46,0.52] | - | - | - | - | - | - | - | - |  | short by 0.186 AUC, 5 of 5 econ |
| A10-G-state | sig | ASIA | M0 | 0.491 [-,-] | 0.493 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/HM | V1c_cluster | 0.497 [-,-] | 0.493 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | M0 | 0.509 [-,-] | 0.493 [0.45,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V2_side | 0.501 [-,-] | 0.493 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | M0 | 0.489 [-,-] | 0.493 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V1c_cluster | 0.493 [-,-] | 0.493 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V1c_cluster | 0.496 [-,-] | 0.492 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/ST | M0 | 0.490 [-,-] | 0.492 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | POOLED/HM | V2_side | 0.502 [-,-] | 0.492 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | V1c_cluster | 0.492 [-,-] | 0.491 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | V1_state | 0.494 [-,-] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | V1_state | 0.494 [-,-] | 0.491 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | M0 | 0.497 [-,-] | 0.490 [0.45,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON | V1c_cluster | 0.492 [-,-] | 0.490 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/ST | M0 | 0.488 [-,-] | 0.488 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V4_dur | 0.489 [-,-] | 0.488 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V4_dur | 0.489 [-,-] | 0.488 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | M0 | 0.482 [-,-] | 0.487 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | M0 | 0.481 [-,-] | 0.486 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V1_state | 0.496 [-,-] | 0.484 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V1_state | 0.496 [-,-] | 0.483 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V4_fast | 0.488 [-,-] | 0.483 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V4_fast | 0.487 [-,-] | 0.482 [0.45,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V1_state | 0.494 [-,-] | 0.481 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | V3_firstlater | 0.474 [-,-] | 0.481 [0.45,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | V3_firstlater | 0.475 [-,-] | 0.481 [0.45,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V0_base | 0.487 [-,-] | 0.481 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V1_state | 0.494 [-,-] | 0.481 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V2_side | 0.485 [-,-] | 0.481 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V0_base | 0.486 [-,-] | 0.480 [0.43,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V2_side | 0.484 [-,-] | 0.480 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V0_base | 0.495 [-,-] | 0.480 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V0_base | 0.496 [-,-] | 0.480 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V1c_cluster | 0.482 [-,-] | 0.479 [0.44,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V3_firstlater | 0.487 [-,-] | 0.479 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V3_firstlater | 0.487 [-,-] | 0.478 [0.44,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | LONDON/HM | V1c_cluster | 0.482 [-,-] | 0.478 [0.44,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | V1c_cluster | 0.495 [-,-] | 0.476 [0.45,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA | V1c_cluster | 0.495 [-,-] | 0.476 [0.45,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V3_firstlater | 0.470 [-,-] | 0.466 [0.43,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V3_firstlater | 0.471 [-,-] | 0.466 [0.43,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V1c_cluster | 0.493 [-,-] | 0.463 [0.43,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A10-G-state | sig | ASIA/ST | V1c_cluster | 0.494 [-,-] | 0.463 [0.43,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |

One-sentence notes:
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 ASIA: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 LONDON: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 NY: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
- A10-G-state -1 POOLED: chance-level
