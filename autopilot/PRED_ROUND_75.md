# PRED ROUND 75 - block Y1 round 2 - Y10-engine-parity+Y6-eb-seasonality+Y7-knn-context+Y8-outcome-hmm+Y9-trigger-proximity+YU2-union

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.546 [0.52,0.57]
Gap to FOUND: 0.134 AUC, 5 of 5 economic conditions short.
not found - short by 0.134 AUC and 5 of 5 economic conditions

prereg 5e060211f5992a266ea6790d0f946a42dd05b7d00842eecefa776f01fbcb74dd ; trials added 600 ; truncation audit {'decisions': 1800, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/Y10_parity.parquet', 'l2vast/pred/store/Y10_parity_sig.parquet', 'l2vast/pred/store/Y10_parity_sigu.parquet', 'l2vast/pred/store/Y6_ebseas.parquet', 'l2vast/pred/store/Y6_ebseas_sig.parquet', 'l2vast/pred/store/Y6_ebseas_sigu.parquet', 'l2vast/pred/store/Y7_knn_sig.parquet', 'l2vast/pred/store/Y7_knn_sigu.parquet', 'l2vast/pred/store/Y8_hmm.parquet', 'l2vast/pred/store/Y8_hmm_sig.parquet', 'l2vast/pred/store/Y8_hmm_sigu.parquet', 'l2vast/pred/store/Y9_trigger.parquet', 'l2vast/pred/store/Y9_trigger_sig.parquet', 'l2vast/pred/store/Y9_trigger_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y6-eb-seasonality+base | sig | NY | Yu2_g_Y6_base_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | NY | Yu2_g_Y7_base_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | NY | Yu2_g_Y8_base_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | NY | Yu2_g_Y9_base_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | NY | Yu2_g_Y10_base_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | NY | Yu2_g_U_base_vr:logit2 | 0.545 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | NY/HM | Yu2_g_Y6_base_vr:logit2 | 0.545 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | NY/HM | Yu2_g_Y7_base_vr:logit2 | 0.545 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | NY/HM | Yu2_g_Y8_base_vr:logit2 | 0.544 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | NY/HM | Yu2_g_Y9_base_vr:logit2 | 0.545 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | NY/HM | Yu2_g_Y10_base_vr:logit2 | 0.545 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | NY/HM | Yu2_g_U_base_vr:logit2 | 0.544 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | NY/ST | Yu2_g_Y6_base_vr:logit2 | 0.546 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | NY/ST | Yu2_g_Y7_base_vr:logit2 | 0.546 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | NY/ST | Yu2_g_Y8_base_vr:logit2 | 0.546 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | NY/ST | Yu2_g_Y9_base_vr:logit2 | 0.546 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | NY/ST | Yu2_g_Y10_base_vr:logit2 | 0.546 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | NY/ST | Yu2_g_U_base_vr:logit2 | 0.546 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | ASIA/ST | Yu2_g_Y9_only_vr:stack | 0.528 [0.50,0.56] | 0.544 [0.51,0.58] | - | - | - | N | - | - | - | - |  | short by 0.136 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | ASIA/ST | Yu2_g_Y9_only_vt:stack | 0.526 [0.50,0.56] | 0.543 [0.51,0.58] | - | - | - | N | - | - | - | - |  | short by 0.137 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | ASIA | Yu2_g_Y9_only_vr:stack | 0.517 [0.49,0.54] | 0.538 [0.51,0.57] | - | - | - | N | - | - | - | - |  | short by 0.142 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | ASIA | Yu2_g_Y9_only_vt:stack | 0.515 [0.49,0.54] | 0.538 [0.51,0.57] | - | - | - | N | - | - | - | - |  | short by 0.142 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | NY/HM | Yu2_g_Y9_only_vr:gbt3 | 0.530 [0.51,0.55] | 0.537 [0.50,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y7-knn-context | sig | ASIA/HM | Yu2_g_Y7_only_vt:logit2 | 0.528 [0.50,0.56] | 0.534 [0.50,0.57] | - | - | - | N | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| Y7-knn-context | sig | ASIA/HM | Yu2_g_Y7_only_vr:logit2 | 0.529 [0.50,0.56] | 0.533 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.147 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | NY/ST | Yu2_g_Y9_only_vr:stack | 0.527 [0.51,0.55] | 0.533 [0.51,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | ASIA/HM | Yu2_g_Y9_only_vt:stack | 0.502 [0.47,0.53] | 0.529 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| Y10-engine-parity | sig | ASIA/HM | Yu2_g_Y10_only_vr:stack | 0.500 [0.47,0.53] | 0.529 [0.50,0.56] | - | - | - | N | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | ASIA/HM | Yu2_g_Y9_only_vr:stack | 0.504 [0.48,0.53] | 0.529 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| Y10-engine-parity | sig | ASIA/HM | Yu2_g_Y10_only_vt:stack | 0.497 [0.47,0.52] | 0.528 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | NY | Yu2_g_Y9_only_vr:stack | 0.522 [0.50,0.54] | 0.527 [0.50,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | POOLED/ST | Yu2_g_Y9_only_vr:stack | 0.518 [0.51,0.53] | 0.526 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | POOLED | Yu2_g_Y9_only_vr:stack | 0.514 [0.50,0.53] | 0.523 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | ASIA/ST | Yu2_g_Y6_only_vt:logit2 | 0.525 [0.50,0.55] | 0.522 [0.49,0.56] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y6-eb-seasonality+base | sig | NY/ST | Yu2_g_Y6_base_vt:logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y7-knn-context+base | sig | NY/ST | Yu2_g_Y7_base_vt:logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y8-outcome-hmm+base | sig | NY/ST | Yu2_g_Y8_base_vt:logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y9-trigger-proximity+base | sig | NY/ST | Yu2_g_Y9_base_vt:logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y10-engine-parity+base | sig | NY/ST | Yu2_g_Y10_base_vt:logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| YU2-union+base | sig | NY/ST | Yu2_g_U_base_vt:logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y6-eb-seasonality | sig | ASIA/ST | Yu2_g_Y6_only_vr:logit2 | 0.526 [0.50,0.55] | 0.521 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | NY | Yu2_g_Y6_base_vt:logit2 | 0.515 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| Y7-knn-context+base | sig | NY | Yu2_g_Y7_base_vt:logit2 | 0.515 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| Y8-outcome-hmm+base | sig | NY | Yu2_g_Y8_base_vt:logit2 | 0.515 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| Y9-trigger-proximity+base | sig | NY | Yu2_g_Y9_base_vt:logit2 | 0.515 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| Y10-engine-parity+base | sig | NY | Yu2_g_Y10_base_vt:logit2 | 0.515 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| YU2-union+base | sig | NY | Yu2_g_U_base_vt:logit2 | 0.515 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| Y7-knn-context | sig | ASIA | Yu2_g_Y7_only_vt:logit2 | 0.520 [0.50,0.54] | 0.520 [0.50,0.55] | - | - | - | N | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| Y7-knn-context | sig | ASIA | Yu2_g_Y7_only_vr:logit2 | 0.520 [0.50,0.54] | 0.519 [0.50,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | ASIA/HM | Yu2_g_Y8_only_vt:logit2 | 0.524 [0.50,0.55] | 0.519 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| Y10-engine-parity | sig | ASIA | Yu2_g_Y10_only_vr:stack | 0.504 [0.48,0.53] | 0.519 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | POOLED/HM | Yu2_g_Y9_only_vr:stack | 0.509 [0.49,0.53] | 0.518 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | ASIA | Yu2_g_Y6_only_vt:logit2 | 0.513 [0.49,0.54] | 0.518 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| Y8-outcome-hmm | sig | POOLED/HM | Yu2_g_Y8_only_vr:stack | 0.513 [0.50,0.53] | 0.517 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | ASIA/HM | Yu2_g_Y8_only_vr:logit2 | 0.522 [0.49,0.55] | 0.517 [0.48,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | NY/HM | Yu2_g_Y9_only_vt:gbt3 | 0.515 [0.49,0.54] | 0.517 [0.48,0.56] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | POOLED/ST | Yu2_g_Y9_only_vt:stack | 0.509 [0.50,0.52] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| Y6-eb-seasonality+base | sig | POOLED/ST | Yu2_g_Y6_base_vr:gbt3 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | POOLED/ST | Yu2_g_Y7_base_vr:gbt3 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | POOLED/ST | Yu2_g_Y8_base_vr:gbt3 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | POOLED/ST | Yu2_g_Y9_base_vr:gbt3 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | POOLED/ST | Yu2_g_Y10_base_vr:gbt3 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | POOLED/ST | Yu2_g_U_base_vr:gbt3 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | ASIA | Yu2_g_Y6_only_vr:logit2 | 0.514 [0.49,0.54] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y7-knn-context | sig | NY/HM | Yu2_g_Y7_only_vr:stack | 0.524 [0.50,0.55] | 0.517 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | POOLED | Yu2_g_Y6_base_vr:logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | POOLED | Yu2_g_Y7_base_vr:logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | POOLED | Yu2_g_Y8_base_vr:logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | POOLED | Yu2_g_Y9_base_vr:logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | POOLED | Yu2_g_Y10_base_vr:logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | POOLED | Yu2_g_U_base_vr:logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | NY/ST | Yu2_g_Y9_only_vt:stack | 0.513 [0.50,0.53] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| Y6-eb-seasonality+base | sig | NY/HM | Yu2_g_Y6_base_vt:logit2 | 0.509 [0.49,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| Y7-knn-context+base | sig | NY/HM | Yu2_g_Y7_base_vt:logit2 | 0.509 [0.49,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| Y8-outcome-hmm+base | sig | NY/HM | Yu2_g_Y8_base_vt:logit2 | 0.509 [0.49,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| Y9-trigger-proximity+base | sig | NY/HM | Yu2_g_Y9_base_vt:logit2 | 0.509 [0.49,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| Y10-engine-parity+base | sig | NY/HM | Yu2_g_Y10_base_vt:logit2 | 0.509 [0.49,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| YU2-union+base | sig | NY/HM | Yu2_g_U_base_vt:logit2 | 0.509 [0.48,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| Y8-outcome-hmm | sig | NY/HM | Yu2_g_Y8_only_vr:stack | 0.520 [0.49,0.55] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | ASIA/HM | Yu2_g_Y6_only_vt:logit2 | 0.501 [0.47,0.53] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | POOLED | Yu2_g_Y9_only_vt:stack | 0.505 [0.49,0.52] | 0.514 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| Y6-eb-seasonality | sig | ASIA/HM | Yu2_g_Y6_only_vr:logit2 | 0.502 [0.47,0.54] | 0.513 [0.47,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | POOLED/HM | Yu2_g_Y9_base_vr:logit2 | 0.518 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | POOLED/HM | Yu2_g_Y10_base_vr:logit2 | 0.518 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | POOLED/HM | Yu2_g_Y8_only_vt:stack | 0.505 [0.49,0.52] | 0.513 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| Y7-knn-context | sig | POOLED/HM | Yu2_g_Y7_only_vr:logit2 | 0.520 [0.51,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | NY/HM | Yu2_g_Y8_only_vt:stack | 0.513 [0.49,0.54] | 0.512 [0.47,0.55] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| Y7-knn-context | sig | NY/HM | Yu2_g_Y7_only_vt:stack | 0.511 [0.49,0.54] | 0.511 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| Y10-engine-parity+base | sig | ASIA/ST | Yu2_g_Y10_base_vr:stack | 0.509 [0.48,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | ASIA/ST | Yu2_g_Y6_base_vr:stack | 0.509 [0.48,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context | sig | ASIA/ST | Yu2_g_Y7_only_vt:logit2 | 0.513 [0.49,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | ASIA/ST | Yu2_g_Y10_base_vt:stack | 0.507 [0.48,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | ASIA/ST | Yu2_g_Y9_base_vr:stack | 0.509 [0.48,0.54] | 0.510 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | POOLED/HM | Yu2_g_Y9_only_vt:stack | 0.499 [0.48,0.51] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| Y6-eb-seasonality+base | sig | ASIA/ST | Yu2_g_Y6_base_vt:stack | 0.507 [0.48,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | ASIA/ST | Yu2_g_Y7_base_vr:stack | 0.509 [0.48,0.54] | 0.510 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context | sig | ASIA/ST | Yu2_g_Y7_only_vr:logit2 | 0.514 [0.49,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | NY | Yu2_g_Y9_only_vt:stack | 0.507 [0.49,0.53] | 0.510 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| Y9-trigger-proximity+base | sig | ASIA/ST | Yu2_g_Y9_base_vt:stack | 0.507 [0.48,0.53] | 0.510 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | ASIA/ST | Yu2_g_Y7_base_vt:stack | 0.507 [0.48,0.54] | 0.510 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context | sig | NY | Yu2_g_Y7_only_vr:stack | 0.522 [0.50,0.54] | 0.508 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | NY/HM | Yu2_g_Y10_only_vt:stack | 0.503 [0.48,0.53] | 0.507 [0.47,0.55] | - | - | - | N | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| Y6-eb-seasonality | sig | LONDON/HM | Yu2_g_Y6_only_vr:gbt3 | 0.484 [0.46,0.52] | 0.506 [0.47,0.54] | - | - | - | N | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| Y6-eb-seasonality+base | sig | POOLED/HM | Yu2_g_Y6_base_vr:rf | 0.516 [0.50,0.53] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | POOLED/HM | Yu2_g_Y7_base_vr:rf | 0.516 [0.50,0.53] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | POOLED/HM | Yu2_g_Y8_base_vr:rf | 0.516 [0.50,0.53] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | POOLED/HM | Yu2_g_U_base_vr:rf | 0.516 [0.50,0.53] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | POOLED/ST | Yu2_g_Y8_base_vt:gbt3 | 0.501 [0.49,0.51] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | ASIA | Yu2_g_Y9_base_vr:stack | 0.508 [0.48,0.53] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | ASIA | Yu2_g_Y7_base_vr:stack | 0.508 [0.48,0.53] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | ASIA | Yu2_g_Y6_base_vr:stack | 0.508 [0.48,0.53] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity | sig | POOLED/HM | Yu2_g_Y10_only_vr:stack | 0.499 [0.48,0.51] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | POOLED/HM | Yu2_g_Y10_only_vt:stack | 0.493 [0.48,0.51] | 0.505 [0.48,0.52] | - | - | - | N | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| Y6-eb-seasonality | sig | POOLED/ST | Yu2_g_Y6_only_vr:gbt3 | 0.513 [0.50,0.53] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | NY/ST | Yu2_g_Y6_only_vt:stack | 0.510 [0.49,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| Y6-eb-seasonality+base | sig | POOLED/ST | Yu2_g_Y6_base_vt:logit2 | 0.503 [0.49,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | POOLED/ST | Yu2_g_Y7_base_vt:logit2 | 0.503 [0.49,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | POOLED/ST | Yu2_g_Y9_base_vt:logit2 | 0.503 [0.49,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | POOLED/ST | Yu2_g_Y10_base_vt:logit2 | 0.503 [0.49,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | POOLED/ST | Yu2_g_U_base_vt:logit2 | 0.503 [0.49,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | ASIA | Yu2_g_Y9_base_vt:stack | 0.505 [0.48,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | ASIA | Yu2_g_Y7_base_vt:stack | 0.505 [0.48,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | POOLED/HM | Yu2_g_Y6_only_vt:stack | 0.495 [0.48,0.51] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| Y7-knn-context | sig | POOLED | Yu2_g_Y7_only_vr:logit2 | 0.512 [0.50,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | LONDON/HM | Yu2_g_Y6_only_vt:gbt3 | 0.483 [0.45,0.52] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | POOLED | Yu2_g_Y8_only_vr:stack | 0.510 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | LONDON/HM | Yu2_g_Y8_only_vr:gbt3 | 0.499 [0.46,0.53] | 0.503 [0.46,0.54] | - | - | - | N | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| Y7-knn-context | sig | NY | Yu2_g_Y7_only_vt:stack | 0.512 [0.49,0.53] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| Y8-outcome-hmm | sig | LONDON/HM | Yu2_g_Y8_only_vt:gbt3 | 0.499 [0.46,0.53] | 0.503 [0.46,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | POOLED | Yu2_g_Y6_base_vt:logit2 | 0.501 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | POOLED | Yu2_g_Y7_base_vt:logit2 | 0.501 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | POOLED | Yu2_g_Y8_base_vt:logit2 | 0.501 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | POOLED | Yu2_g_Y9_base_vt:logit2 | 0.501 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | POOLED | Yu2_g_Y10_base_vt:logit2 | 0.501 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | POOLED | Yu2_g_U_base_vt:logit2 | 0.501 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | POOLED/HM | Yu2_g_Y6_only_vr:stack | 0.500 [0.48,0.52] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | NY | Yu2_g_Y10_only_vt:stack | 0.502 [0.48,0.52] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| Y8-outcome-hmm+base | sig | ASIA/ST | Yu2_g_Y8_base_vr:rf | 0.499 [0.47,0.53] | 0.502 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | ASIA/ST | Yu2_g_U_base_vr:rf | 0.499 [0.47,0.53] | 0.502 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context | sig | NY/ST | Yu2_g_Y7_only_vr:stack | 0.520 [0.50,0.54] | 0.501 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | ASIA/ST | Yu2_g_Y8_base_vt:rf | 0.498 [0.47,0.53] | 0.501 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | ASIA/ST | Yu2_g_U_base_vt:rf | 0.498 [0.47,0.53] | 0.501 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context | sig | POOLED/HM | Yu2_g_Y7_only_vt:logit2 | 0.507 [0.49,0.52] | 0.501 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | POOLED | Yu2_g_Y8_only_vt:stack | 0.503 [0.49,0.52] | 0.501 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | NY/HM | Yu2_g_Y10_only_vr:stack | 0.509 [0.48,0.54] | 0.501 [0.46,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | LONDON/HM | Yu2_g_Y9_only_vr:stack | 0.500 [0.47,0.53] | 0.501 [0.46,0.54] | - | - | - | N | - | - | - | - |  | short by 0.179 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | LONDON/HM | Yu2_g_Y9_only_vt:stack | 0.499 [0.47,0.53] | 0.500 [0.46,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | LONDON/ST | Yu2_g_Y6_base_vr:gbt3 | 0.498 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | LONDON/ST | Yu2_g_Y7_base_vr:gbt3 | 0.498 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | LONDON/ST | Yu2_g_Y8_base_vr:gbt3 | 0.498 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | LONDON/ST | Yu2_g_Y9_base_vr:gbt3 | 0.498 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | LONDON/ST | Yu2_g_Y10_base_vr:gbt3 | 0.498 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | LONDON/ST | Yu2_g_U_base_vr:gbt3 | 0.498 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | NY | Yu2_g_Y6_only_vt:stack | 0.508 [0.49,0.53] | 0.500 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y7-knn-context | sig | POOLED/ST | Yu2_g_Y7_only_vr:logit2 | 0.507 [0.49,0.52] | 0.500 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | POOLED/ST | Yu2_g_Y6_only_vt:gbt3 | 0.505 [0.49,0.52] | 0.500 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | NY/ST | Yu2_g_Y6_only_vr:stack | 0.513 [0.49,0.53] | 0.499 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | POOLED | Yu2_g_Y6_only_vt:stack | 0.497 [0.48,0.51] | 0.499 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y7-knn-context | sig | NY/ST | Yu2_g_Y7_only_vt:stack | 0.513 [0.49,0.53] | 0.498 [0.47,0.52] | - | - | - | N | - | - | - | - |  | short by 0.182 AUC, 5 of 5 econ |
| Y9-trigger-proximity | sig | LONDON | Yu2_g_Y9_only_vr:stack | 0.493 [0.47,0.51] | 0.498 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | POOLED/HM | Yu2_g_Y6_base_vt:logit2 | 0.499 [0.48,0.51] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | POOLED/HM | Yu2_g_Y7_base_vt:logit2 | 0.499 [0.48,0.51] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | POOLED/HM | Yu2_g_Y8_base_vt:logit2 | 0.499 [0.48,0.51] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | POOLED/HM | Yu2_g_Y9_base_vt:logit2 | 0.499 [0.48,0.51] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | POOLED/HM | Yu2_g_Y10_base_vt:logit2 | 0.499 [0.48,0.51] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | POOLED/HM | Yu2_g_U_base_vt:logit2 | 0.499 [0.48,0.52] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context | sig | LONDON/ST | Yu2_g_Y7_only_vr:logit2 | 0.498 [0.47,0.52] | 0.498 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | NY | Yu2_g_Y10_only_vr:stack | 0.508 [0.49,0.53] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | POOLED | Yu2_g_Y6_only_vr:stack | 0.502 [0.49,0.51] | 0.497 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | LONDON | Yu2_g_Y8_only_vr:rf | 0.501 [0.48,0.52] | 0.497 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | LONDON/ST | Yu2_g_Y6_base_vt:gbt3 | 0.495 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | LONDON/ST | Yu2_g_Y7_base_vt:gbt3 | 0.495 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | LONDON/ST | Yu2_g_Y8_base_vt:gbt3 | 0.495 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | LONDON/ST | Yu2_g_Y9_base_vt:gbt3 | 0.495 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | LONDON/ST | Yu2_g_Y10_base_vt:gbt3 | 0.495 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | LONDON/ST | Yu2_g_U_base_vt:gbt3 | 0.495 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | LONDON | Yu2_g_Y9_only_vt:stack | 0.492 [0.47,0.51] | 0.497 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | ASIA | Yu2_g_Y8_only_vt:logit2 | 0.511 [0.49,0.53] | 0.497 [0.47,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y8-outcome-hmm | sig | NY | Yu2_g_Y8_only_vr:stack | 0.515 [0.50,0.54] | 0.497 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | ASIA | Yu2_g_Y8_only_vr:logit2 | 0.510 [0.49,0.53] | 0.497 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y7-knn-context | sig | LONDON/ST | Yu2_g_Y7_only_vt:logit2 | 0.498 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y8-outcome-hmm | sig | LONDON | Yu2_g_Y8_only_vt:rf | 0.500 [0.48,0.52] | 0.496 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y7-knn-context | sig | POOLED | Yu2_g_Y7_only_vt:logit2 | 0.502 [0.49,0.51] | 0.496 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | NY | Yu2_g_Y8_only_vt:stack | 0.509 [0.49,0.53] | 0.496 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | NY/ST | Yu2_g_Y10_only_vr:stack | 0.507 [0.49,0.52] | 0.496 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | POOLED | Yu2_g_Y10_only_vr:gbt3 | 0.501 [0.49,0.51] | 0.495 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | LONDON | Yu2_g_Y10_only_vr:logit2 | 0.498 [0.48,0.52] | 0.494 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | POOLED/ST | Yu2_g_Y8_only_vr:stack | 0.507 [0.49,0.52] | 0.494 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | LONDON/ST | Yu2_g_Y8_only_vr:rf | 0.507 [0.48,0.53] | 0.493 [0.46,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y6-eb-seasonality | sig | NY | Yu2_g_Y6_only_vr:stack | 0.512 [0.49,0.53] | 0.493 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | LONDON | Yu2_g_Y10_only_vt:logit2 | 0.497 [0.48,0.52] | 0.493 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y7-knn-context | sig | POOLED/ST | Yu2_g_Y7_only_vt:logit2 | 0.498 [0.48,0.51] | 0.493 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | ASIA | Yu2_g_Y8_base_vr:logit2 | 0.498 [0.48,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | ASIA | Yu2_g_Y10_base_vr:logit2 | 0.497 [0.48,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | ASIA | Yu2_g_U_base_vr:logit2 | 0.499 [0.48,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | LONDON/ST | Yu2_g_Y8_only_vt:rf | 0.506 [0.48,0.53] | 0.492 [0.46,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y6-eb-seasonality | sig | LONDON | Yu2_g_Y6_only_vr:gbt3 | 0.486 [0.47,0.51] | 0.491 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | ASIA | Yu2_g_Y6_base_vt:logit2 | 0.496 [0.47,0.52] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | ASIA | Yu2_g_Y8_base_vt:logit2 | 0.497 [0.47,0.52] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | ASIA | Yu2_g_Y10_base_vt:logit2 | 0.496 [0.47,0.52] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | ASIA | Yu2_g_U_base_vt:logit2 | 0.497 [0.48,0.52] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | NY/HM | Yu2_g_Y6_only_vt:stack | 0.506 [0.48,0.53] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | LONDON/HM | Yu2_g_Y10_only_vr:logit2 | 0.493 [0.46,0.52] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | ASIA/HM | Yu2_g_Y6_base_vr:logit2 | 0.507 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | ASIA/HM | Yu2_g_Y7_base_vr:logit2 | 0.507 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | ASIA/HM | Yu2_g_Y8_base_vr:logit2 | 0.509 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | ASIA/HM | Yu2_g_Y9_base_vr:logit2 | 0.507 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | ASIA/HM | Yu2_g_Y10_base_vr:logit2 | 0.507 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | ASIA/HM | Yu2_g_U_base_vr:logit2 | 0.509 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity | sig | LONDON/HM | Yu2_g_Y10_only_vt:logit2 | 0.492 [0.46,0.52] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y7-knn-context | sig | LONDON | Yu2_g_Y7_only_vr:logit2 | 0.500 [0.48,0.52] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | POOLED/ST | Yu2_g_Y10_only_vr:gbt3 | 0.502 [0.49,0.52] | 0.489 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | LONDON | Yu2_g_Y6_only_vt:gbt3 | 0.485 [0.46,0.51] | 0.489 [0.47,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | ASIA/HM | Yu2_g_Y6_base_vt:logit2 | 0.505 [0.48,0.54] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y7-knn-context+base | sig | ASIA/HM | Yu2_g_Y7_base_vt:logit2 | 0.505 [0.48,0.54] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y8-outcome-hmm+base | sig | ASIA/HM | Yu2_g_Y8_base_vt:logit2 | 0.507 [0.48,0.54] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y9-trigger-proximity+base | sig | ASIA/HM | Yu2_g_Y9_base_vt:logit2 | 0.505 [0.48,0.54] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y10-engine-parity+base | sig | ASIA/HM | Yu2_g_Y10_base_vt:logit2 | 0.505 [0.48,0.54] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| YU2-union+base | sig | ASIA/HM | Yu2_g_U_base_vt:logit2 | 0.507 [0.48,0.54] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y7-knn-context | sig | LONDON | Yu2_g_Y7_only_vt:logit2 | 0.500 [0.48,0.52] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | POOLED | Yu2_g_Y10_only_vt:gbt3 | 0.493 [0.48,0.50] | 0.488 [0.47,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | ASIA | Yu2_g_Y10_only_vt:gbt3 | 0.490 [0.46,0.52] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | NY/ST | Yu2_g_Y10_only_vt:rf | 0.497 [0.48,0.52] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | POOLED/ST | Yu2_g_Y8_only_vt:rf | 0.502 [0.49,0.51] | 0.487 [0.47,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | NY/ST | Yu2_g_Y8_only_vt:stack | 0.506 [0.49,0.53] | 0.485 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | NY/ST | Yu2_g_Y8_only_vr:stack | 0.512 [0.49,0.53] | 0.485 [0.46,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | LONDON | Yu2_g_Y6_base_vr:rf | 0.492 [0.47,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | LONDON | Yu2_g_Y7_base_vr:rf | 0.492 [0.47,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | LONDON | Yu2_g_Y8_base_vr:rf | 0.492 [0.47,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | LONDON | Yu2_g_Y9_base_vr:rf | 0.490 [0.47,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | LONDON | Yu2_g_Y10_base_vr:rf | 0.491 [0.47,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | LONDON | Yu2_g_U_base_vr:rf | 0.492 [0.47,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | NY/HM | Yu2_g_Y6_only_vr:stack | 0.510 [0.48,0.54] | 0.483 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | POOLED/ST | Yu2_g_Y10_only_vt:gbt3 | 0.495 [0.48,0.51] | 0.483 [0.47,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | LONDON/ST | Yu2_g_Y9_only_vr:gbt3 | 0.488 [0.46,0.52] | 0.481 [0.45,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | LONDON | Yu2_g_Y6_base_vt:rf | 0.489 [0.47,0.51] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | LONDON | Yu2_g_Y7_base_vt:rf | 0.489 [0.47,0.51] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | LONDON | Yu2_g_Y8_base_vt:rf | 0.489 [0.47,0.51] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | LONDON | Yu2_g_Y9_base_vt:rf | 0.488 [0.47,0.51] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | LONDON | Yu2_g_Y10_base_vt:rf | 0.489 [0.47,0.51] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | LONDON | Yu2_g_U_base_vt:rf | 0.489 [0.47,0.51] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | LONDON/ST | Yu2_g_Y6_only_vr:gbt3 | 0.486 [0.46,0.51] | 0.479 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | ASIA/ST | Yu2_g_Y8_only_vr:logit2 | 0.500 [0.47,0.52] | 0.479 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y7-knn-context | sig | LONDON/HM | Yu2_g_Y7_only_vr:logit2 | 0.503 [0.47,0.53] | 0.478 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y9-trigger-proximity | sig | LONDON/ST | Yu2_g_Y9_only_vt:gbt3 | 0.485 [0.46,0.52] | 0.478 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y8-outcome-hmm | sig | ASIA/ST | Yu2_g_Y8_only_vt:logit2 | 0.500 [0.47,0.52] | 0.478 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y7-knn-context | sig | LONDON/HM | Yu2_g_Y7_only_vt:logit2 | 0.503 [0.47,0.53] | 0.477 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | LONDON/ST | Yu2_g_Y10_only_vr:gbt3 | 0.492 [0.47,0.52] | 0.476 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality | sig | LONDON/ST | Yu2_g_Y6_only_vt:gbt3 | 0.485 [0.46,0.51] | 0.476 [0.45,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | LONDON/ST | Yu2_g_Y10_only_vt:gbt3 | 0.490 [0.47,0.51] | 0.475 [0.44,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | ASIA/ST | Yu2_g_Y10_only_vr:gbt3 | 0.488 [0.46,0.52] | 0.468 [0.43,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y10-engine-parity | sig | ASIA/ST | Yu2_g_Y10_only_vt:gbt3 | 0.488 [0.46,0.52] | 0.467 [0.43,0.50] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | LONDON/HM | Yu2_g_Y6_base_vr:rf | 0.490 [0.46,0.52] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | LONDON/HM | Yu2_g_Y7_base_vr:rf | 0.490 [0.46,0.52] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | LONDON/HM | Yu2_g_Y8_base_vr:rf | 0.488 [0.46,0.52] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | LONDON/HM | Yu2_g_Y9_base_vr:rf | 0.489 [0.46,0.52] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | LONDON/HM | Yu2_g_Y10_base_vr:rf | 0.490 [0.46,0.52] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | LONDON/HM | Yu2_g_U_base_vr:rf | 0.488 [0.46,0.52] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y6-eb-seasonality+base | sig | LONDON/HM | Yu2_g_Y6_base_vt:rf | 0.488 [0.46,0.52] | 0.457 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y7-knn-context+base | sig | LONDON/HM | Yu2_g_Y7_base_vt:rf | 0.488 [0.46,0.52] | 0.457 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y8-outcome-hmm+base | sig | LONDON/HM | Yu2_g_Y8_base_vt:rf | 0.487 [0.46,0.51] | 0.457 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y9-trigger-proximity+base | sig | LONDON/HM | Yu2_g_Y9_base_vt:rf | 0.487 [0.46,0.51] | 0.457 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y10-engine-parity+base | sig | LONDON/HM | Yu2_g_Y10_base_vt:rf | 0.488 [0.46,0.52] | 0.457 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU2-union+base | sig | LONDON/HM | Yu2_g_U_base_vt:rf | 0.487 [0.46,0.51] | 0.457 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- Y6-eb-seasonality -1 POOLED: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 ASIA: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 LONDON: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 NY: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 POOLED: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 ASIA: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 LONDON: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 NY: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 POOLED: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 ASIA: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 LONDON: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality -1 NY: Yu2_g_Y6_only_vt model by WF-PRE
- Y6-eb-seasonality+base -1 POOLED: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 ASIA: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 LONDON: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 NY: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 POOLED: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 ASIA: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 LONDON: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 NY: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 POOLED: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 ASIA: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 LONDON: Yu2_g_Y6_base_vt model by WF-PRE
- Y6-eb-seasonality+base -1 NY: Yu2_g_Y6_base_vt model by WF-PRE
- Y7-knn-context -1 POOLED: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 ASIA: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 LONDON: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 NY: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 POOLED: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 ASIA: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 LONDON: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 NY: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 POOLED: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 ASIA: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 LONDON: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context -1 NY: Yu2_g_Y7_only_vt model by WF-PRE
- Y7-knn-context+base -1 POOLED: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 ASIA: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 LONDON: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 NY: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 POOLED: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 ASIA: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 LONDON: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 NY: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 POOLED: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 ASIA: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 LONDON: Yu2_g_Y7_base_vt model by WF-PRE
- Y7-knn-context+base -1 NY: Yu2_g_Y7_base_vt model by WF-PRE
- Y8-outcome-hmm -1 POOLED: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 ASIA: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 LONDON: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 NY: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 POOLED: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 ASIA: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 LONDON: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 NY: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 POOLED: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 ASIA: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 LONDON: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm -1 NY: Yu2_g_Y8_only_vt model by WF-PRE
- Y8-outcome-hmm+base -1 POOLED: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 ASIA: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 LONDON: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 NY: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 POOLED: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 ASIA: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 LONDON: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 NY: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 POOLED: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 ASIA: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 LONDON: Yu2_g_Y8_base_vt model by WF-PRE
- Y8-outcome-hmm+base -1 NY: Yu2_g_Y8_base_vt model by WF-PRE
- Y9-trigger-proximity -1 POOLED: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 ASIA: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 LONDON: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 NY: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 POOLED: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 ASIA: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 LONDON: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 NY: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 POOLED: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 ASIA: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 LONDON: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity -1 NY: Yu2_g_Y9_only_vt model by WF-PRE
- Y9-trigger-proximity+base -1 POOLED: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 ASIA: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 LONDON: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 NY: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 POOLED: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 ASIA: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 LONDON: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 NY: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 POOLED: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 ASIA: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 LONDON: Yu2_g_Y9_base_vt model by WF-PRE
- Y9-trigger-proximity+base -1 NY: Yu2_g_Y9_base_vt model by WF-PRE
- Y10-engine-parity -1 POOLED: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 ASIA: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 LONDON: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 NY: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 POOLED: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 ASIA: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 LONDON: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 NY: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 POOLED: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 ASIA: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 LONDON: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity -1 NY: Yu2_g_Y10_only_vt model by WF-PRE
- Y10-engine-parity+base -1 POOLED: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 ASIA: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 LONDON: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 NY: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 POOLED: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 ASIA: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 LONDON: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 NY: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 POOLED: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 ASIA: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 LONDON: Yu2_g_Y10_base_vt model by WF-PRE
- Y10-engine-parity+base -1 NY: Yu2_g_Y10_base_vt model by WF-PRE
- YU2-union+base -1 POOLED: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 ASIA: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 LONDON: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 NY: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 POOLED: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 ASIA: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 LONDON: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 NY: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 POOLED: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 ASIA: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 LONDON: Yu2_g_U_base_vt model by WF-PRE
- YU2-union+base -1 NY: Yu2_g_U_base_vt model by WF-PRE
- Y6-eb-seasonality -1 POOLED: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 ASIA: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 LONDON: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 NY: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 POOLED: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 ASIA: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 LONDON: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 NY: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 POOLED: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 ASIA: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 LONDON: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality -1 NY: Yu2_g_Y6_only_vr model by WF-PRE
- Y6-eb-seasonality+base -1 POOLED: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 ASIA: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 LONDON: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 NY: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 POOLED: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 ASIA: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 LONDON: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 NY: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 POOLED: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 ASIA: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 LONDON: Yu2_g_Y6_base_vr model by WF-PRE
- Y6-eb-seasonality+base -1 NY: Yu2_g_Y6_base_vr model by WF-PRE
- Y7-knn-context -1 POOLED: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 ASIA: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 LONDON: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 NY: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 POOLED: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 ASIA: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 LONDON: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 NY: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 POOLED: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 ASIA: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 LONDON: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context -1 NY: Yu2_g_Y7_only_vr model by WF-PRE
- Y7-knn-context+base -1 POOLED: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 ASIA: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 LONDON: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 NY: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 POOLED: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 ASIA: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 LONDON: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 NY: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 POOLED: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 ASIA: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 LONDON: Yu2_g_Y7_base_vr model by WF-PRE
- Y7-knn-context+base -1 NY: Yu2_g_Y7_base_vr model by WF-PRE
- Y8-outcome-hmm -1 POOLED: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 ASIA: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 LONDON: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 NY: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 POOLED: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 ASIA: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 LONDON: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 NY: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 POOLED: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 ASIA: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 LONDON: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm -1 NY: Yu2_g_Y8_only_vr model by WF-PRE
- Y8-outcome-hmm+base -1 POOLED: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 ASIA: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 LONDON: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 NY: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 POOLED: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 ASIA: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 LONDON: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 NY: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 POOLED: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 ASIA: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 LONDON: Yu2_g_Y8_base_vr model by WF-PRE
- Y8-outcome-hmm+base -1 NY: Yu2_g_Y8_base_vr model by WF-PRE
- Y9-trigger-proximity -1 POOLED: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 ASIA: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 LONDON: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 NY: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 POOLED: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 ASIA: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 LONDON: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 NY: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 POOLED: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 ASIA: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 LONDON: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity -1 NY: Yu2_g_Y9_only_vr model by WF-PRE
- Y9-trigger-proximity+base -1 POOLED: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 ASIA: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 LONDON: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 NY: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 POOLED: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 ASIA: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 LONDON: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 NY: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 POOLED: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 ASIA: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 LONDON: Yu2_g_Y9_base_vr model by WF-PRE
- Y9-trigger-proximity+base -1 NY: Yu2_g_Y9_base_vr model by WF-PRE
- Y10-engine-parity -1 POOLED: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 ASIA: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 LONDON: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 NY: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 POOLED: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 ASIA: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 LONDON: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 NY: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 POOLED: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 ASIA: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 LONDON: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity -1 NY: Yu2_g_Y10_only_vr model by WF-PRE
- Y10-engine-parity+base -1 POOLED: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 ASIA: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 LONDON: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 NY: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 POOLED: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 ASIA: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 LONDON: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 NY: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 POOLED: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 ASIA: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 LONDON: Yu2_g_Y10_base_vr model by WF-PRE
- Y10-engine-parity+base -1 NY: Yu2_g_Y10_base_vr model by WF-PRE
- YU2-union+base -1 POOLED: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 ASIA: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 LONDON: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 NY: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 POOLED: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 ASIA: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 LONDON: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 NY: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 POOLED: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 ASIA: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 LONDON: Yu2_g_U_base_vr model by WF-PRE
- YU2-union+base -1 NY: Yu2_g_U_base_vr model by WF-PRE
