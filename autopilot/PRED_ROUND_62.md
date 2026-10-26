# PRED ROUND 62 - block Y1 round 1 - Y-ctrl-base-G-unlocked+Y1-shadow-outcomes+Y2-ctrl-real-trades-only+Y2-shadow-train+Y3-engine-state+Y4-lockstate+Y5-signal-clustering+YU1-union

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.562 [0.53,0.60]
Gap to FOUND: 0.118 AUC, 5 of 5 economic conditions short.
not found - short by 0.118 AUC and 5 of 5 economic conditions

prereg 5e060211f5992a266ea6790d0f946a42dd05b7d00842eecefa776f01fbcb74dd ; trials added 600 ; truncation audit {'decisions': 1440, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/Y1_shadow_sigu.parquet', 'l2vast/pred/store/Y3_engstate_sigu.parquet', 'l2vast/pred/store/Y4_lock_sigu.parquet', 'l2vast/pred/store/Y5_cluster_sigu.parquet', 'l2vast/pred/store/Y2u_rawmat.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y3-engine-state | sig | NY/HM | Yu1_g_Y3_only_vr:logit2 | 0.556 [0.53,0.58] | 0.562 [0.53,0.60] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y5-signal-clustering | sig | NY/HM | Yu1_g_Y5_only_vr:stack | 0.548 [0.52,0.57] | 0.555 [0.52,0.59] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y2-shadow-train | sig | NY/HM | Y2u_vr:logit | 0.540 [0.51,0.56] | 0.551 [0.52,0.59] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | NY/ST | Y2u_vr:ctrl_lgb | 0.540 [0.52,0.56] | 0.551 [0.53,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state | sig | ASIA/ST | Yu1_g_Y3_only_vr:stack | 0.528 [0.50,0.56] | 0.551 [0.52,0.58] | - | - | - | N | - | - | - | - |  | short by 0.129 AUC, 5 of 5 econ |
| Y5-signal-clustering | sig | NY | Yu1_g_Y5_only_vr:stack | 0.542 [0.52,0.56] | 0.551 [0.53,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y2-shadow-train | sig | NY | Y2u_vr:logit | 0.540 [0.52,0.56] | 0.551 [0.53,0.58] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state | sig | ASIA/ST | Yu1_g_Y3_only_vt:stack | 0.526 [0.50,0.56] | 0.550 [0.52,0.58] | - | - | - | N | - | - | - | - |  | short by 0.130 AUC, 5 of 5 econ |
| Y3-engine-state+base | sig | NY/HM | Yu1_g_Y3_base_vr:logit2 | 0.547 [0.52,0.57] | 0.549 [0.51,0.59] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-shadow-train | sig | NY/ST | Y2u_vr:logit | 0.540 [0.52,0.56] | 0.549 [0.52,0.58] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | NY/ST | Yu1_g_Y5_only_vr:stack | 0.538 [0.52,0.56] | 0.549 [0.53,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state+base | sig | NY | Yu1_g_Y3_base_vr:logit2 | 0.547 [0.53,0.56] | 0.549 [0.53,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering | sig | ASIA/HM | Yu1_g_Y5_only_vr:rf | 0.525 [0.50,0.55] | 0.548 [0.51,0.58] | - | - | - | N | - | - | - | - |  | short by 0.132 AUC, 5 of 5 econ |
| Y5-signal-clustering | sig | ASIA/HM | Yu1_g_Y5_only_vt:rf | 0.523 [0.49,0.55] | 0.548 [0.51,0.58] | - | - | - | N | - | - | - | - |  | short by 0.132 AUC, 5 of 5 econ |
| Y3-engine-state+base | sig | NY/ST | Yu1_g_Y3_base_vr:logit2 | 0.547 [0.53,0.57] | 0.547 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | NY | Yu1_g_ctrl_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | NY | Yu1_g_Y4_base_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | NY/HM | Yu1_g_U_base_vr:logit2 | 0.546 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | NY | Yu1_g_Y1_base_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | NY | Yu1_g_U_base_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | NY/HM | Yu1_g_ctrl_vr:logit2 | 0.545 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | NY/HM | Yu1_g_Y4_base_vr:logit2 | 0.545 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | NY/ST | Yu1_g_ctrl_vr:logit2 | 0.546 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | NY/ST | Yu1_g_Y4_base_vr:logit2 | 0.546 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | NY/ST | Yu1_g_Y1_base_vr:logit2 | 0.546 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state | sig | ASIA | Yu1_g_Y3_only_vr:stack | 0.517 [0.49,0.54] | 0.545 [0.51,0.58] | - | - | - | N | - | - | - | - |  | short by 0.135 AUC, 5 of 5 econ |
| Y1-shadow-outcomes+base | sig | NY/HM | Yu1_g_Y1_base_vr:logit2 | 0.544 [0.52,0.57] | 0.545 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state | sig | ASIA | Yu1_g_Y3_only_vt:stack | 0.515 [0.49,0.54] | 0.544 [0.51,0.58] | - | - | - | N | - | - | - | - |  | short by 0.136 AUC, 5 of 5 econ |
| Y3-engine-state | sig | NY | Yu1_g_Y3_only_vr:stack | 0.536 [0.52,0.55] | 0.544 [0.52,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | NY | Yu1_g_Y5_base_vr:logit2 | 0.545 [0.53,0.56] | 0.544 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | NY/ST | Yu1_g_U_base_vr:logit2 | 0.546 [0.53,0.57] | 0.544 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | NY/HM | Yu1_g_Y5_base_vr:logit2 | 0.544 [0.52,0.57] | 0.544 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | NY/ST | Yu1_g_Y5_base_vr:logit2 | 0.546 [0.52,0.57] | 0.543 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | NY | Y2u_vr:ctrl_lgb | 0.537 [0.52,0.55] | 0.542 [0.52,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state | sig | NY/ST | Yu1_g_Y3_only_vr:stack | 0.532 [0.51,0.55] | 0.541 [0.52,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | ASIA | Yu1_g_Y5_only_vr:rf | 0.518 [0.50,0.54] | 0.536 [0.51,0.56] | - | - | - | N | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| Y5-signal-clustering | sig | ASIA | Yu1_g_Y5_only_vt:rf | 0.516 [0.49,0.54] | 0.535 [0.51,0.56] | - | - | - | N | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| Y3-engine-state | sig | POOLED/HM | Yu1_g_Y3_only_vr:logit2 | 0.530 [0.52,0.54] | 0.534 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | POOLED/HM | Yu1_g_Y5_only_vr:rf | 0.531 [0.52,0.55] | 0.533 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state | sig | POOLED | Yu1_g_Y3_only_vr:stack | 0.524 [0.51,0.53] | 0.532 [0.52,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state | sig | POOLED/ST | Yu1_g_Y3_only_vr:stack | 0.526 [0.51,0.54] | 0.531 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | POOLED | Yu1_g_Y5_only_vr:rf | 0.527 [0.52,0.54] | 0.530 [0.52,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | NY/ST | Yu1_g_Y5_only_vt:stack | 0.516 [0.50,0.53] | 0.529 [0.50,0.55] | - | - | - | N | - | - | - | - |  | promising: short by 0.151 AUC, 5 of 5 econ |
| Y2-ctrl-real-trades-only | sig | POOLED/ST | Y2u_vr:ctrl_lgb | 0.527 [0.51,0.54] | 0.528 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | ASIA/ST | Yu1_g_Y5_only_vr:rf | 0.512 [0.48,0.54] | 0.528 [0.49,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | POOLED/ST | Yu1_g_Y5_only_vr:rf | 0.524 [0.51,0.54] | 0.528 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | ASIA/ST | Yu1_g_Y5_only_vt:rf | 0.511 [0.48,0.54] | 0.527 [0.49,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | NY | Yu1_g_Y5_only_vt:stack | 0.517 [0.50,0.53] | 0.527 [0.51,0.55] | - | - | - | N | - | - | - | - |  | promising: short by 0.153 AUC, 5 of 5 econ |
| Y3-engine-state | sig | ASIA/HM | Yu1_g_Y3_only_vt:logit2 | 0.514 [0.48,0.54] | 0.527 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| Y2-shadow-train | sig | ASIA/HM | Y2u_vt:logit | 0.516 [0.49,0.54] | 0.527 [0.49,0.57] | - | - | - | ok | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| Y3-engine-state | sig | ASIA/HM | Yu1_g_Y3_only_vr:logit2 | 0.513 [0.48,0.54] | 0.526 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| Y5-signal-clustering | sig | NY/HM | Yu1_g_Y5_only_vt:stack | 0.520 [0.49,0.55] | 0.525 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.155 AUC, 5 of 5 econ |
| Y2-ctrl-real-trades-only | sig | NY/HM | Y2u_vr:ctrl_lgb | 0.531 [0.51,0.56] | 0.525 [0.49,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | LONDON/ST | Yu1_g_Y5_only_vr:gbt3 | 0.531 [0.51,0.55] | 0.525 [0.49,0.55] | - | - | - | N | - | - | - | - |  | short by 0.155 AUC, 5 of 5 econ |
| Y1-shadow-outcomes | sig | ASIA/HM | Yu1_g_Y1_only_vr:rf | 0.509 [0.48,0.54] | 0.524 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| Y1-shadow-outcomes | sig | ASIA/HM | Yu1_g_Y1_only_vt:rf | 0.508 [0.48,0.54] | 0.524 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| Y2-shadow-train | sig | POOLED/HM | Y2u_vr:logit | 0.520 [0.51,0.53] | 0.523 [0.50,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | LONDON/ST | Yu1_g_Y5_only_vt:gbt3 | 0.529 [0.50,0.55] | 0.523 [0.49,0.55] | - | - | - | N | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| Y3-engine-state | sig | NY/HM | Yu1_g_Y3_only_vt:logit2 | 0.517 [0.49,0.54] | 0.523 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| Y2-ctrl-real-trades-only | sig | POOLED | Y2u_vr:ctrl_lgb | 0.523 [0.51,0.53] | 0.522 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state+base | sig | NY/ST | Yu1_g_Y3_base_vt:logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y1-shadow-outcomes+base | sig | NY/ST | Yu1_g_Y1_base_vt:logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y4-lockstate+base | sig | NY/ST | Yu1_g_Y4_base_vt:logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y-ctrl-base-G-unlocked | sig | NY/ST | Yu1_g_ctrl_vt:logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y2-shadow-train | sig | POOLED | Y2u_vr:logit | 0.522 [0.51,0.53] | 0.522 [0.51,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| YU1-union+base | sig | POOLED/HM | Yu1_g_U_base_vr:logit2 | 0.521 [0.51,0.54] | 0.521 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-shadow-train | sig | POOLED/ST | Y2u_vr:logit | 0.523 [0.51,0.53] | 0.521 [0.50,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state+base | sig | NY | Yu1_g_Y3_base_vt:logit2 | 0.516 [0.50,0.53] | 0.521 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| YU1-union+base | sig | POOLED | Yu1_g_U_base_vr:logit2 | 0.520 [0.51,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | ASIA | Yu1_g_Y5_base_vr:stack | 0.514 [0.49,0.54] | 0.520 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | NY | Yu1_g_Y4_base_vt:logit2 | 0.515 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| Y-ctrl-base-G-unlocked | sig | NY | Yu1_g_ctrl_vt:logit2 | 0.515 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| YU1-union+base | sig | ASIA/ST | Yu1_g_U_base_vr:gbt3 | 0.508 [0.48,0.54] | 0.520 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | ASIA/ST | Yu1_g_U_base_vt:gbt3 | 0.507 [0.48,0.53] | 0.520 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | NY | Yu1_g_Y1_base_vt:logit2 | 0.515 [0.50,0.53] | 0.519 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| Y5-signal-clustering+base | sig | NY/ST | Yu1_g_Y5_base_vt:logit2 | 0.518 [0.50,0.54] | 0.519 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| Y1-shadow-outcomes+base | sig | POOLED/ST | Yu1_g_Y1_base_vr:gbt3 | 0.518 [0.51,0.53] | 0.519 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | ASIA | Yu1_g_Y5_base_vt:stack | 0.511 [0.49,0.54] | 0.519 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| YU1-union+base | sig | NY/ST | Yu1_g_U_base_vt:logit2 | 0.518 [0.50,0.54] | 0.519 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| Y5-signal-clustering+base | sig | POOLED/HM | Yu1_g_Y5_base_vr:logit2 | 0.521 [0.51,0.54] | 0.519 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering | sig | POOLED/HM | Yu1_g_Y5_only_vt:rf | 0.515 [0.50,0.53] | 0.518 [0.50,0.54] | - | - | - | N | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| Y5-signal-clustering+base | sig | POOLED | Yu1_g_Y5_base_vr:logit2 | 0.520 [0.51,0.53] | 0.518 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | POOLED/HM | Yu1_g_Y1_only_vr:rf | 0.512 [0.49,0.53] | 0.518 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state+base | sig | POOLED | Yu1_g_Y3_base_vr:logit2 | 0.518 [0.51,0.53] | 0.518 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | POOLED/ST | Yu1_g_U_base_vr:gbt3 | 0.517 [0.51,0.53] | 0.518 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | NY | Yu1_g_U_base_vt:logit2 | 0.515 [0.50,0.53] | 0.518 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| Y5-signal-clustering+base | sig | POOLED/ST | Yu1_g_Y5_base_vr:gbt3 | 0.516 [0.50,0.53] | 0.517 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | NY | Yu1_g_Y5_base_vt:logit2 | 0.514 [0.50,0.53] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| Y5-signal-clustering | sig | POOLED | Yu1_g_Y5_only_vt:rf | 0.512 [0.50,0.52] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| Y1-shadow-outcomes | sig | NY | Yu1_g_Y1_only_vr:gbt3 | 0.522 [0.50,0.54] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | POOLED/ST | Yu1_g_ctrl_vr:gbt3 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | POOLED/ST | Yu1_g_Y4_base_vr:gbt3 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | ASIA/HM | Yu1_g_U_base_vr:logit2 | 0.519 [0.49,0.55] | 0.517 [0.48,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering | sig | POOLED/ST | Yu1_g_Y5_only_vt:rf | 0.510 [0.50,0.52] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| Y3-engine-state+base | sig | NY/HM | Yu1_g_Y3_base_vt:logit2 | 0.510 [0.49,0.53] | 0.517 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| Y3-engine-state | sig | POOLED | Yu1_g_Y3_only_vt:stack | 0.507 [0.50,0.52] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| Y1-shadow-outcomes+base | sig | POOLED | Yu1_g_Y1_base_vr:logit2 | 0.519 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | POOLED | Yu1_g_ctrl_vr:logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | POOLED | Yu1_g_Y4_base_vr:logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | POOLED/ST | Yu1_g_Y3_base_vr:gbt3 | 0.515 [0.50,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state | sig | POOLED/HM | Yu1_g_Y3_only_vt:logit2 | 0.510 [0.49,0.52] | 0.516 [0.50,0.54] | - | - | - | N | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| Y3-engine-state | sig | POOLED/ST | Yu1_g_Y3_only_vt:stack | 0.510 [0.50,0.52] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| Y1-shadow-outcomes | sig | ASIA | Yu1_g_Y1_only_vr:logit2 | 0.508 [0.48,0.53] | 0.516 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| YU1-union+base | sig | ASIA/HM | Yu1_g_U_base_vt:logit2 | 0.518 [0.49,0.55] | 0.516 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| Y1-shadow-outcomes | sig | NY/HM | Yu1_g_Y1_only_vr:rf | 0.515 [0.49,0.54] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | ASIA | Yu1_g_Y1_only_vt:logit2 | 0.506 [0.48,0.53] | 0.515 [0.49,0.55] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| Y4-lockstate | sig | POOLED | Yu1_g_Y4_only_vr:logit2 | 0.514 [0.50,0.53] | 0.515 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate+base | sig | NY/HM | Yu1_g_Y4_base_vt:logit2 | 0.509 [0.49,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| Y-ctrl-base-G-unlocked | sig | NY/HM | Yu1_g_ctrl_vt:logit2 | 0.509 [0.49,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| Y4-lockstate | sig | POOLED/ST | Yu1_g_Y4_only_vr:gbt3 | 0.517 [0.50,0.53] | 0.515 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | ASIA/ST | Y2u_vr:ctrl_logit | 0.505 [0.48,0.53] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state+base | sig | ASIA/ST | Yu1_g_Y3_base_vr:gbt3 | 0.504 [0.48,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | ASIA/ST | Yu1_g_Y3_base_vt:gbt3 | 0.502 [0.47,0.53] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate | sig | NY/HM | Yu1_g_Y4_only_vr:stack | 0.517 [0.49,0.55] | 0.514 [0.47,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| YU1-union+base | sig | NY/HM | Yu1_g_U_base_vt:logit2 | 0.509 [0.49,0.53] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| Y1-shadow-outcomes+base | sig | NY/HM | Yu1_g_Y1_base_vt:logit2 | 0.509 [0.48,0.53] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| Y5-signal-clustering+base | sig | NY/HM | Yu1_g_Y5_base_vt:logit2 | 0.508 [0.49,0.53] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| Y2-ctrl-real-trades-only | sig | POOLED/HM | Y2u_vr:ctrl_lgb | 0.517 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | ASIA | Y2u_vr:ctrl_logit | 0.514 [0.49,0.54] | 0.513 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | POOLED | Yu1_g_Y1_only_vr:logit2 | 0.515 [0.50,0.53] | 0.513 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | POOLED/HM | Yu1_g_Y1_base_vr:logit2 | 0.518 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | POOLED/ST | Yu1_g_Y1_only_vr:logit2 | 0.520 [0.50,0.54] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y2-shadow-train | sig | POOLED/HM | Y2u_vt:lgb | 0.501 [0.48,0.52] | 0.512 [0.49,0.53] | - | - | - | ok | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| Y4-lockstate | sig | POOLED/HM | Yu1_g_Y4_only_vr:stack | 0.508 [0.49,0.52] | 0.512 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | NY/HM | Yu1_g_Y1_only_vt:gbt3 | 0.507 [0.48,0.53] | 0.512 [0.48,0.54] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| Y2-shadow-train | sig | ASIA | Y2u_vt:stack | 0.509 [0.49,0.53] | 0.511 [0.48,0.54] | - | - | - | ok | - | - | - | - |  | WF-only (dead) |
| Y2-shadow-train | sig | LONDON/ST | Y2u_vt:lgb | 0.497 [0.47,0.53] | 0.511 [0.47,0.55] | - | - | - | ok | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| Y-ctrl-base-G-unlocked | sig | ASIA/ST | Yu1_g_ctrl_vr:stack | 0.509 [0.48,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | NY/ST | Yu1_g_Y1_only_vr:gbt3 | 0.522 [0.50,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state | sig | NY | Yu1_g_Y3_only_vt:stack | 0.505 [0.49,0.52] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| Y3-engine-state | sig | NY/ST | Yu1_g_Y3_only_vt:stack | 0.504 [0.48,0.52] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| Y-ctrl-base-G-unlocked | sig | ASIA/ST | Yu1_g_ctrl_vt:stack | 0.507 [0.48,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | ASIA/ST | Yu1_g_Y4_base_vr:stack | 0.509 [0.48,0.54] | 0.510 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | ASIA/HM | Yu1_g_Y5_base_vr:logit2 | 0.517 [0.49,0.55] | 0.510 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-shadow-train | sig | LONDON | Y2u_vt:lgb | 0.498 [0.48,0.52] | 0.510 [0.48,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | ASIA/ST | Yu1_g_Y1_only_vr:logit2 | 0.508 [0.48,0.54] | 0.510 [0.47,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate | sig | LONDON/ST | Yu1_g_Y4_only_vr:gbt3 | 0.516 [0.49,0.54] | 0.510 [0.47,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y4-lockstate+base | sig | ASIA/ST | Yu1_g_Y4_base_vt:stack | 0.507 [0.48,0.54] | 0.510 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | ASIA/HM | Y2u_vr:ctrl_logit | 0.525 [0.50,0.55] | 0.509 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | ASIA/ST | Yu1_g_Y1_base_vr:stack | 0.508 [0.48,0.54] | 0.509 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | LONDON/ST | Y2u_vr:ctrl_lgb | 0.525 [0.50,0.55] | 0.509 [0.47,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y1-shadow-outcomes | sig | ASIA/ST | Yu1_g_Y1_only_vt:logit2 | 0.507 [0.48,0.54] | 0.509 [0.47,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | ASIA/ST | Yu1_g_Y1_base_vt:stack | 0.506 [0.48,0.53] | 0.509 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | ASIA/ST | Y2u_vt:ctrl_lgb | 0.500 [0.47,0.53] | 0.508 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | ASIA/HM | Yu1_g_Y5_base_vt:logit2 | 0.515 [0.49,0.55] | 0.508 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| Y4-lockstate | sig | LONDON/ST | Yu1_g_Y4_only_vt:gbt3 | 0.516 [0.49,0.54] | 0.508 [0.47,0.54] | - | - | - | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| Y2-shadow-train | sig | ASIA/ST | Y2u_vr:lgb | 0.509 [0.48,0.53] | 0.508 [0.48,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y2-shadow-train | sig | LONDON/HM | Y2u_vt:lgb | 0.498 [0.47,0.53] | 0.508 [0.47,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering | sig | LONDON/HM | Yu1_g_Y5_only_vr:logit2 | 0.523 [0.50,0.55] | 0.507 [0.48,0.54] | - | - | - | N | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| Y4-lockstate | sig | POOLED/ST | Yu1_g_Y4_only_vt:gbt3 | 0.510 [0.50,0.52] | 0.507 [0.49,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y2-shadow-train | sig | NY | Y2u_vt:stack | 0.507 [0.49,0.53] | 0.507 [0.48,0.53] | - | - | - | ok | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| YU1-union+base | sig | ASIA | Yu1_g_U_base_vr:logit2 | 0.504 [0.48,0.53] | 0.507 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate | sig | POOLED | Yu1_g_Y4_only_vt:stack | 0.502 [0.49,0.51] | 0.507 [0.49,0.52] | - | - | - | N | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| YU1-union+base | sig | POOLED/ST | Yu1_g_U_base_vt:gbt3 | 0.501 [0.49,0.51] | 0.507 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | LONDON/ST | Y2u_vt:ctrl_lgb | 0.516 [0.49,0.54] | 0.507 [0.47,0.54] | - | - | - | N | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| Y2-ctrl-real-trades-only | sig | ASIA | Y2u_vt:ctrl_logit | 0.504 [0.48,0.53] | 0.507 [0.47,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate | sig | NY/ST | Yu1_g_Y4_only_vr:rf | 0.516 [0.49,0.54] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate | sig | POOLED/HM | Yu1_g_Y4_only_vt:stack | 0.502 [0.49,0.52] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| Y1-shadow-outcomes | sig | POOLED/ST | Yu1_g_Y1_only_vt:logit2 | 0.512 [0.50,0.53] | 0.506 [0.49,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y-ctrl-base-G-unlocked | sig | POOLED/HM | Yu1_g_ctrl_vr:rf | 0.516 [0.50,0.53] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | POOLED/HM | Yu1_g_Y4_base_vr:rf | 0.516 [0.50,0.53] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | ASIA | Yu1_g_Y3_base_vr:stack | 0.505 [0.48,0.53] | 0.506 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | ASIA | Yu1_g_U_base_vt:logit2 | 0.502 [0.48,0.53] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | POOLED/HM | Yu1_g_Y3_base_vr:rf | 0.515 [0.50,0.53] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering | sig | LONDON | Yu1_g_Y5_only_vr:logit2 | 0.520 [0.50,0.54] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| Y2-shadow-train | sig | ASIA | Y2u_vr:logit | 0.508 [0.49,0.53] | 0.506 [0.48,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate+base | sig | ASIA | Yu1_g_Y4_base_vr:stack | 0.508 [0.48,0.53] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | ASIA | Yu1_g_ctrl_vr:stack | 0.508 [0.48,0.53] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | POOLED/ST | Yu1_g_Y1_base_vt:logit2 | 0.503 [0.49,0.52] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | POOLED/ST | Yu1_g_Y5_base_vt:gbt3 | 0.500 [0.49,0.51] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | ASIA | Yu1_g_Y3_base_vt:stack | 0.502 [0.48,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering | sig | LONDON/HM | Yu1_g_Y5_only_vt:logit2 | 0.524 [0.49,0.55] | 0.505 [0.47,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y2-shadow-train | sig | ASIA/HM | Y2u_vr:logit | 0.508 [0.48,0.54] | 0.505 [0.46,0.55] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| YU1-union+base | sig | POOLED | Yu1_g_U_base_vt:logit2 | 0.502 [0.49,0.51] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | POOLED/HM | Yu1_g_U_base_vt:logit2 | 0.502 [0.49,0.52] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| Y4-lockstate+base | sig | POOLED/ST | Yu1_g_Y4_base_vt:logit2 | 0.503 [0.49,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | POOLED/ST | Yu1_g_ctrl_vt:logit2 | 0.503 [0.49,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | ASIA | Yu1_g_Y4_base_vt:stack | 0.505 [0.48,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | ASIA | Yu1_g_ctrl_vt:stack | 0.505 [0.48,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | POOLED/ST | Yu1_g_Y3_base_vt:gbt3 | 0.499 [0.49,0.51] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate | sig | NY | Yu1_g_Y4_only_vr:rf | 0.510 [0.49,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | ASIA/HM | Y2u_vt:ctrl_logit | 0.519 [0.49,0.55] | 0.504 [0.46,0.54] | - | - | - | - | - | - | - | - |  | short by 0.176 AUC, 5 of 5 econ |
| Y5-signal-clustering+base | sig | POOLED | Yu1_g_Y5_base_vt:logit2 | 0.502 [0.49,0.51] | 0.504 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | POOLED/ST | Y2u_vt:ctrl_lgb | 0.504 [0.49,0.52] | 0.504 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state | sig | LONDON/ST | Yu1_g_Y3_only_vr:rf | 0.517 [0.49,0.54] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y5-signal-clustering | sig | LONDON | Yu1_g_Y5_only_vt:logit2 | 0.519 [0.50,0.54] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y1-shadow-outcomes+base | sig | ASIA | Yu1_g_Y1_base_vr:stack | 0.506 [0.48,0.53] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | POOLED/HM | Yu1_g_Y5_base_vt:logit2 | 0.502 [0.49,0.52] | 0.504 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | short by 0.176 AUC, 5 of 5 econ |
| Y2-shadow-train | sig | POOLED | Y2u_vt:lgb | 0.501 [0.49,0.51] | 0.504 [0.49,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state+base | sig | POOLED | Yu1_g_Y3_base_vt:logit2 | 0.501 [0.49,0.51] | 0.503 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | POOLED/HM | Yu1_g_Y1_only_vt:gbt3 | 0.497 [0.48,0.51] | 0.503 [0.48,0.52] | - | - | - | N | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| Y3-engine-state | sig | LONDON/ST | Yu1_g_Y3_only_vt:rf | 0.515 [0.49,0.54] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y1-shadow-outcomes | sig | NY | Yu1_g_Y1_only_vt:gbt3 | 0.510 [0.49,0.53] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| Y2-ctrl-real-trades-only | sig | LONDON/HM | Y2u_vt:ctrl_logit | 0.498 [0.46,0.53] | 0.503 [0.46,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | POOLED/HM | Y2u_vt:ctrl_logit | 0.503 [0.49,0.52] | 0.503 [0.48,0.53] | - | - | - | - | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| Y5-signal-clustering+base | sig | ASIA/ST | Yu1_g_Y5_base_vr:stack | 0.507 [0.48,0.54] | 0.503 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | POOLED | Yu1_g_Y1_base_vt:logit2 | 0.501 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | POOLED | Yu1_g_Y4_base_vt:logit2 | 0.501 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | POOLED | Yu1_g_ctrl_vt:logit2 | 0.501 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-shadow-train | sig | ASIA/ST | Y2u_vt:lgb | 0.504 [0.48,0.53] | 0.502 [0.47,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate | sig | NY | Yu1_g_Y4_only_vt:gbt3 | 0.506 [0.49,0.52] | 0.502 [0.48,0.52] | - | - | - | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| Y4-lockstate | sig | NY/HM | Yu1_g_Y4_only_vt:stack | 0.508 [0.48,0.54] | 0.502 [0.46,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | ASIA/ST | Yu1_g_Y5_base_vt:stack | 0.504 [0.47,0.54] | 0.502 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | LONDON | Y2u_vt:ctrl_lgb | 0.505 [0.48,0.53] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y2-shadow-train | sig | NY/HM | Y2u_vt:logit | 0.497 [0.47,0.52] | 0.501 [0.46,0.54] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | LONDON/ST | Yu1_g_ctrl_vr:gbt3 | 0.498 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | LONDON/ST | Yu1_g_Y4_base_vr:gbt3 | 0.498 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | LONDON/ST | Yu1_g_U_base_vr:gbt3 | 0.493 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | POOLED | Y2u_vt:ctrl_lgb | 0.501 [0.49,0.51] | 0.500 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | POOLED | Yu1_g_Y1_only_vt:gbt3 | 0.502 [0.49,0.51] | 0.500 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state+base | sig | POOLED/HM | Yu1_g_Y3_base_vt:logit2 | 0.499 [0.48,0.51] | 0.499 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | NY/ST | Y2u_vt:ctrl_lgb | 0.498 [0.48,0.52] | 0.499 [0.47,0.53] | - | - | - | N | - | - | - | - |  | short by 0.181 AUC, 5 of 5 econ |
| Y4-lockstate | sig | NY/ST | Yu1_g_Y4_only_vt:gbt3 | 0.510 [0.49,0.53] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - |  | short by 0.182 AUC, 5 of 5 econ |
| Y1-shadow-outcomes | sig | NY/ST | Yu1_g_Y1_only_vt:gbt3 | 0.512 [0.49,0.53] | 0.498 [0.47,0.53] | - | - | - | N | - | - | - | - |  | short by 0.182 AUC, 5 of 5 econ |
| Y4-lockstate+base | sig | POOLED/HM | Yu1_g_Y4_base_vt:logit2 | 0.499 [0.48,0.51] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | POOLED/HM | Yu1_g_ctrl_vt:logit2 | 0.499 [0.48,0.51] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-shadow-train | sig | POOLED/ST | Y2u_vt:lgb | 0.502 [0.49,0.52] | 0.498 [0.48,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | LONDON/ST | Yu1_g_Y1_base_vr:gbt3 | 0.497 [0.47,0.52] | 0.498 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | LONDON | Y2u_vr:ctrl_lgb | 0.514 [0.49,0.53] | 0.497 [0.47,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y1-shadow-outcomes+base | sig | POOLED/HM | Yu1_g_Y1_base_vt:logit2 | 0.499 [0.48,0.51] | 0.497 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | LONDON/ST | Yu1_g_ctrl_vt:gbt3 | 0.495 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | LONDON/ST | Yu1_g_Y4_base_vt:gbt3 | 0.495 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state | sig | LONDON | Yu1_g_Y3_only_vr:stack | 0.501 [0.48,0.52] | 0.497 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate | sig | ASIA/ST | Yu1_g_Y4_only_vt:stack | 0.505 [0.48,0.53] | 0.496 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate | sig | ASIA | Yu1_g_Y4_only_vt:stack | 0.496 [0.47,0.52] | 0.496 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate | sig | ASIA/HM | Yu1_g_Y4_only_vr:stack | 0.488 [0.46,0.52] | 0.496 [0.45,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate | sig | ASIA/HM | Yu1_g_Y4_only_vt:stack | 0.486 [0.46,0.52] | 0.496 [0.45,0.54] | - | - | - | N | - | - | - | - |  | short by 0.184 AUC, 5 of 5 econ |
| YU1-union+base | sig | LONDON/ST | Yu1_g_U_base_vt:gbt3 | 0.490 [0.46,0.52] | 0.496 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate | sig | ASIA | Yu1_g_Y4_only_vr:stack | 0.498 [0.48,0.52] | 0.496 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y4-lockstate | sig | ASIA/ST | Yu1_g_Y4_only_vr:stack | 0.507 [0.48,0.53] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state | sig | LONDON | Yu1_g_Y3_only_vt:stack | 0.500 [0.48,0.52] | 0.495 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | NY | Y2u_vt:ctrl_lgb | 0.498 [0.48,0.51] | 0.495 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | LONDON/ST | Yu1_g_Y1_base_vt:gbt3 | 0.494 [0.47,0.52] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | ASIA/HM | Yu1_g_Y3_base_vr:logit2 | 0.505 [0.48,0.54] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | LONDON/ST | Yu1_g_Y5_base_vr:gbt3 | 0.491 [0.47,0.51] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | ASIA/HM | Yu1_g_Y3_base_vt:logit2 | 0.504 [0.48,0.54] | 0.493 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| Y2-ctrl-real-trades-only | sig | NY/HM | Y2u_vt:ctrl_lgb | 0.497 [0.47,0.52] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | ASIA | Yu1_g_Y1_base_vt:logit2 | 0.496 [0.47,0.52] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | LONDON/ST | Yu1_g_Y5_base_vt:gbt3 | 0.488 [0.46,0.51] | 0.490 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | ASIA/HM | Yu1_g_ctrl_vr:logit2 | 0.507 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | ASIA/HM | Yu1_g_Y4_base_vr:logit2 | 0.507 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate | sig | LONDON | Yu1_g_Y4_only_vr:logit2 | 0.497 [0.47,0.52] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | ASIA/HM | Yu1_g_Y1_base_vr:logit2 | 0.507 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-shadow-train | sig | LONDON/HM | Y2u_vr:logit | 0.485 [0.46,0.51] | 0.489 [0.45,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | ASIA/HM | Yu1_g_ctrl_vt:logit2 | 0.505 [0.48,0.54] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y4-lockstate+base | sig | ASIA/HM | Yu1_g_Y4_base_vt:logit2 | 0.505 [0.48,0.54] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y1-shadow-outcomes+base | sig | ASIA/HM | Yu1_g_Y1_base_vt:logit2 | 0.505 [0.48,0.54] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y4-lockstate | sig | LONDON | Yu1_g_Y4_only_vt:logit2 | 0.495 [0.47,0.52] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y2-shadow-train | sig | NY/ST | Y2u_vt:lgb | 0.504 [0.48,0.52] | 0.486 [0.46,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state | sig | LONDON/HM | Yu1_g_Y3_only_vr:logit2 | 0.491 [0.46,0.52] | 0.486 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y2-shadow-train | sig | LONDON | Y2u_vr:logit | 0.491 [0.47,0.51] | 0.486 [0.46,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | LONDON/ST | Yu1_g_Y1_only_vr:gbt3 | 0.507 [0.48,0.54] | 0.486 [0.45,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| YU1-union+base | sig | LONDON | Yu1_g_U_base_vr:gbt3 | 0.489 [0.46,0.51] | 0.485 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | LONDON | Yu1_g_Y1_base_vr:rf | 0.491 [0.47,0.51] | 0.485 [0.46,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | LONDON/ST | Yu1_g_Y1_only_vt:gbt3 | 0.507 [0.48,0.54] | 0.484 [0.45,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y-ctrl-base-G-unlocked | sig | LONDON | Yu1_g_ctrl_vr:rf | 0.492 [0.47,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | LONDON | Yu1_g_Y4_base_vr:rf | 0.492 [0.47,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-shadow-train | sig | LONDON/ST | Y2u_vr:logit | 0.496 [0.47,0.52] | 0.484 [0.45,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state | sig | LONDON/HM | Yu1_g_Y3_only_vt:logit2 | 0.490 [0.46,0.52] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state+base | sig | LONDON/ST | Yu1_g_Y3_base_vr:logit2 | 0.483 [0.46,0.51] | 0.483 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y2-ctrl-real-trades-only | sig | LONDON/HM | Y2u_vr:ctrl_lgb | 0.499 [0.47,0.53] | 0.483 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | LONDON | Yu1_g_Y5_base_vr:gbt3 | 0.489 [0.46,0.51] | 0.482 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate | sig | LONDON/HM | Yu1_g_Y4_only_vr:logit2 | 0.494 [0.46,0.52] | 0.482 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | LONDON | Yu1_g_Y1_base_vt:rf | 0.489 [0.47,0.51] | 0.482 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | LONDON | Yu1_g_U_base_vt:gbt3 | 0.487 [0.46,0.51] | 0.482 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | LONDON/ST | Yu1_g_Y3_base_vt:logit2 | 0.481 [0.46,0.50] | 0.481 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | LONDON | Yu1_g_Y1_only_vr:gbt3 | 0.496 [0.47,0.52] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | LONDON | Yu1_g_ctrl_vt:rf | 0.489 [0.47,0.51] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | LONDON | Yu1_g_Y4_base_vt:rf | 0.489 [0.47,0.51] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate | sig | LONDON/HM | Yu1_g_Y4_only_vt:logit2 | 0.492 [0.46,0.52] | 0.480 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | LONDON | Yu1_g_Y1_only_vt:gbt3 | 0.495 [0.47,0.52] | 0.479 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | LONDON | Yu1_g_Y5_base_vt:rf | 0.486 [0.46,0.51] | 0.477 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | LONDON/HM | Yu1_g_Y1_only_vr:gbt3 | 0.481 [0.45,0.51] | 0.472 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state+base | sig | LONDON | Yu1_g_Y3_base_vr:rf | 0.482 [0.46,0.50] | 0.471 [0.44,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes | sig | LONDON/HM | Yu1_g_Y1_only_vt:gbt3 | 0.480 [0.45,0.51] | 0.471 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y3-engine-state+base | sig | LONDON | Yu1_g_Y3_base_vt:rf | 0.480 [0.46,0.50] | 0.468 [0.44,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | LONDON/HM | Yu1_g_Y1_base_vr:rf | 0.491 [0.46,0.52] | 0.465 [0.43,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y1-shadow-outcomes+base | sig | LONDON/HM | Yu1_g_Y1_base_vt:rf | 0.490 [0.46,0.52] | 0.462 [0.43,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | LONDON/HM | Yu1_g_U_base_vr:rf | 0.481 [0.45,0.51] | 0.460 [0.43,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | LONDON/HM | Yu1_g_ctrl_vr:rf | 0.490 [0.46,0.52] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | LONDON/HM | Yu1_g_Y4_base_vr:rf | 0.490 [0.46,0.52] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | LONDON/HM | Yu1_g_Y5_base_vr:rf | 0.488 [0.46,0.52] | 0.460 [0.42,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | LONDON/HM | Yu1_g_Y3_base_vr:rf | 0.485 [0.46,0.51] | 0.459 [0.43,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y-ctrl-base-G-unlocked | sig | LONDON/HM | Yu1_g_ctrl_vt:rf | 0.488 [0.46,0.52] | 0.457 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y4-lockstate+base | sig | LONDON/HM | Yu1_g_Y4_base_vt:rf | 0.488 [0.46,0.52] | 0.457 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU1-union+base | sig | LONDON/HM | Yu1_g_U_base_vt:rf | 0.479 [0.45,0.51] | 0.456 [0.42,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y5-signal-clustering+base | sig | LONDON/HM | Yu1_g_Y5_base_vt:rf | 0.486 [0.46,0.51] | 0.456 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y3-engine-state+base | sig | LONDON/HM | Yu1_g_Y3_base_vt:rf | 0.483 [0.45,0.51] | 0.456 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- Y-ctrl-base-G-unlocked -1 POOLED: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 ASIA: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 LONDON: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 NY: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 POOLED: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 ASIA: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 LONDON: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 NY: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 POOLED: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 ASIA: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 LONDON: Yu1_g_ctrl_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 NY: Yu1_g_ctrl_vt model by WF-PRE
- Y1-shadow-outcomes -1 POOLED: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 ASIA: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 LONDON: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 NY: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 POOLED: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 ASIA: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 LONDON: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 NY: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 POOLED: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 ASIA: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 LONDON: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes -1 NY: Yu1_g_Y1_only_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 POOLED: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 ASIA: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 LONDON: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 NY: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 POOLED: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 ASIA: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 LONDON: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 NY: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 POOLED: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 ASIA: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 LONDON: Yu1_g_Y1_base_vt model by WF-PRE
- Y1-shadow-outcomes+base -1 NY: Yu1_g_Y1_base_vt model by WF-PRE
- Y3-engine-state -1 POOLED: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 ASIA: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 LONDON: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 NY: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 POOLED: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 ASIA: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 LONDON: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 NY: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 POOLED: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 ASIA: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 LONDON: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state -1 NY: Yu1_g_Y3_only_vt model by WF-PRE
- Y3-engine-state+base -1 POOLED: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 ASIA: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 LONDON: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 NY: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 POOLED: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 ASIA: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 LONDON: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 NY: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 POOLED: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 ASIA: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 LONDON: Yu1_g_Y3_base_vt model by WF-PRE
- Y3-engine-state+base -1 NY: Yu1_g_Y3_base_vt model by WF-PRE
- Y4-lockstate -1 POOLED: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 ASIA: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 LONDON: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 NY: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 POOLED: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 ASIA: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 LONDON: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 NY: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 POOLED: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 ASIA: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 LONDON: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate -1 NY: Yu1_g_Y4_only_vt model by WF-PRE
- Y4-lockstate+base -1 POOLED: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 ASIA: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 LONDON: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 NY: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 POOLED: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 ASIA: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 LONDON: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 NY: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 POOLED: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 ASIA: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 LONDON: Yu1_g_Y4_base_vt model by WF-PRE
- Y4-lockstate+base -1 NY: Yu1_g_Y4_base_vt model by WF-PRE
- Y5-signal-clustering -1 POOLED: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 ASIA: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 LONDON: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 NY: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 POOLED: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 ASIA: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 LONDON: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 NY: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 POOLED: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 ASIA: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 LONDON: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering -1 NY: Yu1_g_Y5_only_vt model by WF-PRE
- Y5-signal-clustering+base -1 POOLED: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 ASIA: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 LONDON: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 NY: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 POOLED: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 ASIA: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 LONDON: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 NY: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 POOLED: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 ASIA: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 LONDON: Yu1_g_Y5_base_vt model by WF-PRE
- Y5-signal-clustering+base -1 NY: Yu1_g_Y5_base_vt model by WF-PRE
- YU1-union+base -1 POOLED: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 ASIA: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 LONDON: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 NY: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 POOLED: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 ASIA: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 LONDON: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 NY: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 POOLED: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 ASIA: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 LONDON: Yu1_g_U_base_vt model by WF-PRE
- YU1-union+base -1 NY: Yu1_g_U_base_vt model by WF-PRE
- Y-ctrl-base-G-unlocked -1 POOLED: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 ASIA: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 LONDON: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 NY: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 POOLED: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 ASIA: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 LONDON: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 NY: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 POOLED: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 ASIA: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 LONDON: Yu1_g_ctrl_vr model by WF-PRE
- Y-ctrl-base-G-unlocked -1 NY: Yu1_g_ctrl_vr model by WF-PRE
- Y1-shadow-outcomes -1 POOLED: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 ASIA: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 LONDON: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 NY: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 POOLED: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 ASIA: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 LONDON: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 NY: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 POOLED: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 ASIA: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 LONDON: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes -1 NY: Yu1_g_Y1_only_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 POOLED: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 ASIA: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 LONDON: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 NY: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 POOLED: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 ASIA: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 LONDON: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 NY: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 POOLED: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 ASIA: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 LONDON: Yu1_g_Y1_base_vr model by WF-PRE
- Y1-shadow-outcomes+base -1 NY: Yu1_g_Y1_base_vr model by WF-PRE
- Y3-engine-state -1 POOLED: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 ASIA: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 LONDON: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 NY: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 POOLED: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 ASIA: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 LONDON: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 NY: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 POOLED: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 ASIA: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 LONDON: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state -1 NY: Yu1_g_Y3_only_vr model by WF-PRE
- Y3-engine-state+base -1 POOLED: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 ASIA: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 LONDON: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 NY: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 POOLED: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 ASIA: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 LONDON: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 NY: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 POOLED: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 ASIA: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 LONDON: Yu1_g_Y3_base_vr model by WF-PRE
- Y3-engine-state+base -1 NY: Yu1_g_Y3_base_vr model by WF-PRE
- Y4-lockstate -1 POOLED: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 ASIA: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 LONDON: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 NY: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 POOLED: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 ASIA: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 LONDON: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 NY: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 POOLED: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 ASIA: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 LONDON: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate -1 NY: Yu1_g_Y4_only_vr model by WF-PRE
- Y4-lockstate+base -1 POOLED: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 ASIA: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 LONDON: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 NY: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 POOLED: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 ASIA: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 LONDON: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 NY: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 POOLED: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 ASIA: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 LONDON: Yu1_g_Y4_base_vr model by WF-PRE
- Y4-lockstate+base -1 NY: Yu1_g_Y4_base_vr model by WF-PRE
- Y5-signal-clustering -1 POOLED: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 ASIA: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 LONDON: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 NY: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 POOLED: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 ASIA: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 LONDON: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 NY: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 POOLED: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 ASIA: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 LONDON: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering -1 NY: Yu1_g_Y5_only_vr model by WF-PRE
- Y5-signal-clustering+base -1 POOLED: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 ASIA: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 LONDON: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 NY: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 POOLED: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 ASIA: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 LONDON: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 NY: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 POOLED: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 ASIA: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 LONDON: Yu1_g_Y5_base_vr model by WF-PRE
- Y5-signal-clustering+base -1 NY: Yu1_g_Y5_base_vr model by WF-PRE
- YU1-union+base -1 POOLED: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 ASIA: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 LONDON: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 NY: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 POOLED: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 ASIA: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 LONDON: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 NY: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 POOLED: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 ASIA: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 LONDON: Yu1_g_U_base_vr model by WF-PRE
- YU1-union+base -1 NY: Yu1_g_U_base_vr model by WF-PRE
- Y2-shadow-train -1 POOLED: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 ASIA: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 LONDON: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 NY: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 POOLED: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 ASIA: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 LONDON: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 NY: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 POOLED: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 ASIA: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 LONDON: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 NY: Y2u_vt model by WF-PRE
- Y2-shadow-train -1 POOLED: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 ASIA: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 LONDON: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 NY: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 POOLED: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 ASIA: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 LONDON: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 NY: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 POOLED: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 ASIA: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 LONDON: Y2u_vr model by WF-PRE
- Y2-shadow-train -1 NY: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 POOLED: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 ASIA: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 LONDON: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 NY: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 POOLED: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 ASIA: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 LONDON: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 NY: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 POOLED: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 ASIA: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 LONDON: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 NY: Y2u_vt model by WF-PRE
- Y2-ctrl-real-trades-only -1 POOLED: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 ASIA: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 LONDON: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 NY: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 POOLED: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 ASIA: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 LONDON: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 NY: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 POOLED: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 ASIA: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 LONDON: Y2u_vr model by WF-PRE
- Y2-ctrl-real-trades-only -1 NY: Y2u_vr model by WF-PRE
