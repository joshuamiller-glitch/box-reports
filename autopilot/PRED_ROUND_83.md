# PRED ROUND 83 - block Y1 round 3 - Y11-es-engine-agree+Y12-closed-trade-path+Y13-crossbook-agree+Y14-barrier-timing+Y15-levels-stoprun+YU3-union

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.566 [0.53,0.61]
Gap to FOUND: 0.114 AUC, 5 of 5 economic conditions short.
not found - short by 0.114 AUC and 5 of 5 economic conditions

prereg 5e060211f5992a266ea6790d0f946a42dd05b7d00842eecefa776f01fbcb74dd ; trials added 600 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/Y11_esagree.parquet', 'l2vast/pred/store/Y11_esagree_sig.parquet', 'l2vast/pred/store/Y11_esagree_sigu.parquet', 'l2vast/pred/store/Y12_tradepath.parquet', 'l2vast/pred/store/Y12_tradepath_sig.parquet', 'l2vast/pred/store/Y12_tradepath_sigu.parquet', 'l2vast/pred/store/Y13_crossbook.parquet', 'l2vast/pred/store/Y13_crossbook_sig.parquet', 'l2vast/pred/store/Y13_crossbook_sigu.parquet', 'l2vast/pred/store/Y14_barrier_sig.parquet', 'l2vast/pred/store/Y14_barrier_sigu.parquet', 'l2vast/pred/store/Y15_levels.parquet', 'l2vast/pred/store/Y15_levels_sig.parquet', 'l2vast/pred/store/Y15_levels_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y14-barrier-timing | sig | NY/HM | Yu3_g_Y14_only_vr:stack | 0.555 [0.53,0.58] | 0.566 [0.53,0.61] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y12-closed-trade-path | sig | ASIA/HM | Yu3_g_Y12_only_vr:logit2 | 0.526 [0.50,0.56] | 0.553 [0.51,0.60] | - | - | - | N | - | - | - | - |  | short by 0.127 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | ASIA/HM | Yu3_g_Y12_only_vt:logit2 | 0.526 [0.50,0.56] | 0.553 [0.51,0.60] | - | - | - | N | - | - | - | - |  | short by 0.127 AUC, 5 of 5 econ |
| YU3-union+base | sig | NY/HM | Yu3_g_U_base_vr:rf | 0.553 [0.53,0.58] | 0.552 [0.52,0.59] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing | sig | NY | Yu3_g_Y14_only_vr:gbt3 | 0.542 [0.52,0.56] | 0.552 [0.52,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| YU3-union+base | sig | NY/ST | Yu3_g_U_base_vr:logit2 | 0.550 [0.53,0.57] | 0.550 [0.52,0.58] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | NY/HM | Yu3_g_Y14_base_vr:rf | 0.553 [0.53,0.58] | 0.550 [0.52,0.58] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | NY | Yu3_g_U_base_vr:logit2 | 0.549 [0.53,0.57] | 0.549 [0.52,0.57] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | NY/ST | Yu3_g_Y14_base_vr:logit2 | 0.550 [0.53,0.57] | 0.549 [0.52,0.58] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | NY | Yu3_g_Y14_base_vr:logit2 | 0.550 [0.53,0.57] | 0.548 [0.52,0.57] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | NY | Yu3_g_Y11_base_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing | sig | NY/ST | Yu3_g_Y14_only_vr:gbt3 | 0.541 [0.52,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | NY | Yu3_g_Y13_base_vr:logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | NY | Yu3_g_Y15_base_vr:logit2 | 0.544 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | NY/ST | Yu3_g_Y15_base_vr:logit2 | 0.545 [0.52,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | NY/HM | Yu3_g_Y11_base_vr:logit2 | 0.545 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | NY/ST | Yu3_g_Y11_base_vr:logit2 | 0.547 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | NY/ST | Yu3_g_Y13_base_vr:logit2 | 0.546 [0.52,0.56] | 0.545 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | NY/HM | Yu3_g_Y13_base_vr:logit2 | 0.545 [0.52,0.57] | 0.545 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | NY/HM | Yu3_g_Y15_base_vr:logit2 | 0.544 [0.52,0.57] | 0.545 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | NY | Yu3_g_Y12_base_vr:logit2 | 0.545 [0.53,0.56] | 0.544 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | NY/ST | Yu3_g_Y12_base_vr:logit2 | 0.545 [0.53,0.56] | 0.544 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | ASIA/HM | Yu3_g_Y13_only_vr:stack | 0.512 [0.48,0.54] | 0.544 [0.50,0.58] | - | - | - | N | - | - | - | - |  | short by 0.136 AUC, 5 of 5 econ |
| Y13-crossbook-agree | sig | ASIA/HM | Yu3_g_Y13_only_vt:stack | 0.509 [0.48,0.54] | 0.544 [0.50,0.58] | - | - | - | N | - | - | - | - |  | short by 0.136 AUC, 5 of 5 econ |
| Y12-closed-trade-path+base | sig | NY/HM | Yu3_g_Y12_base_vr:logit2 | 0.544 [0.52,0.57] | 0.543 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | NY | Yu3_g_Y12_only_vr:stack | 0.532 [0.52,0.55] | 0.538 [0.51,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | NY/HM | Yu3_g_Y12_only_vr:stack | 0.531 [0.51,0.56] | 0.537 [0.51,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | ASIA | Yu3_g_Y12_only_vt:logit2 | 0.515 [0.49,0.54] | 0.534 [0.51,0.56] | - | - | - | N | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | ASIA | Yu3_g_Y12_only_vr:logit2 | 0.515 [0.49,0.54] | 0.534 [0.51,0.56] | - | - | - | N | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| Y13-crossbook-agree | sig | NY/HM | Yu3_g_Y13_only_vr:stack | 0.518 [0.49,0.54] | 0.533 [0.50,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | NY/ST | Yu3_g_Y12_only_vr:rf | 0.537 [0.52,0.56] | 0.533 [0.51,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | POOLED/HM | Yu3_g_Y14_only_vr:logit2 | 0.526 [0.51,0.54] | 0.532 [0.51,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | POOLED | Yu3_g_Y14_only_vr:logit2 | 0.524 [0.51,0.54] | 0.530 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | NY/HM | Yu3_g_Y13_only_vt:stack | 0.507 [0.48,0.53] | 0.528 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| Y14-barrier-timing | sig | POOLED/ST | Yu3_g_Y14_only_vr:logit2 | 0.522 [0.51,0.54] | 0.527 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | ASIA | Yu3_g_Y11_only_vr:stack | 0.511 [0.49,0.54] | 0.527 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| Y11-es-engine-agree | sig | ASIA | Yu3_g_Y11_only_vt:stack | 0.508 [0.48,0.53] | 0.526 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| Y13-crossbook-agree | sig | POOLED/HM | Yu3_g_Y13_only_vr:logit2 | 0.516 [0.50,0.53] | 0.524 [0.50,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | POOLED/ST | Yu3_g_Y12_only_vr:rf | 0.527 [0.51,0.54] | 0.524 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | ASIA/ST | Yu3_g_Y15_base_vr:gbt3 | 0.513 [0.48,0.54] | 0.524 [0.48,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | ASIA/ST | Yu3_g_Y15_base_vt:gbt3 | 0.512 [0.48,0.54] | 0.524 [0.48,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | NY | Yu3_g_Y13_only_vr:stack | 0.516 [0.50,0.54] | 0.523 [0.50,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | POOLED/HM | Yu3_g_Y12_only_vt:logit2 | 0.509 [0.49,0.53] | 0.523 [0.50,0.55] | - | - | - | N | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| Y11-es-engine-agree+base | sig | NY/ST | Yu3_g_Y11_base_vt:logit2 | 0.520 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y15-levels-stoprun+base | sig | NY/ST | Yu3_g_Y15_base_vt:logit2 | 0.517 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y13-crossbook-agree+base | sig | NY/ST | Yu3_g_Y13_base_vt:logit2 | 0.518 [0.50,0.54] | 0.522 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | POOLED | Yu3_g_Y12_only_vr:rf | 0.521 [0.51,0.53] | 0.521 [0.51,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | NY/ST | Yu3_g_Y12_base_vt:logit2 | 0.518 [0.50,0.54] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| Y15-levels-stoprun | sig | POOLED/HM | Yu3_g_Y15_only_vr:rf | 0.531 [0.51,0.55] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | NY | Yu3_g_Y11_base_vt:logit2 | 0.516 [0.50,0.53] | 0.520 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| Y11-es-engine-agree | sig | ASIA/ST | Yu3_g_Y11_only_vr:logit2 | 0.509 [0.48,0.54] | 0.519 [0.48,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | NY | Yu3_g_Y13_base_vt:logit2 | 0.515 [0.50,0.53] | 0.519 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| Y15-levels-stoprun+base | sig | NY | Yu3_g_Y15_base_vt:logit2 | 0.514 [0.50,0.53] | 0.519 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| YU3-union+base | sig | NY/ST | Yu3_g_U_base_vt:logit2 | 0.513 [0.49,0.53] | 0.519 [0.49,0.54] | - | - | - | ok | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| Y11-es-engine-agree | sig | ASIA/ST | Yu3_g_Y11_only_vt:logit2 | 0.508 [0.48,0.54] | 0.519 [0.48,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | NY/HM | Yu3_g_Y14_only_vt:logit2 | 0.506 [0.48,0.53] | 0.519 [0.48,0.56] | - | - | - | N | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| Y11-es-engine-agree | sig | ASIA/HM | Yu3_g_Y11_only_vr:stack | 0.506 [0.48,0.54] | 0.519 [0.48,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | ASIA/ST | Yu3_g_Y15_only_vr:logit2 | 0.507 [0.48,0.54] | 0.518 [0.48,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | POOLED/ST | Yu3_g_Y12_base_vr:logit2 | 0.519 [0.51,0.53] | 0.518 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | NY/ST | Yu3_g_Y14_base_vt:logit2 | 0.515 [0.50,0.53] | 0.518 [0.49,0.54] | - | - | - | ok | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| Y15-levels-stoprun | sig | NY/HM | Yu3_g_Y15_only_vr:stack | 0.534 [0.51,0.56] | 0.518 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | NY/ST | Yu3_g_Y13_only_vr:stack | 0.514 [0.49,0.54] | 0.518 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | POOLED/HM | Yu3_g_Y13_only_vt:logit2 | 0.507 [0.49,0.52] | 0.518 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| Y12-closed-trade-path+base | sig | NY | Yu3_g_Y12_base_vt:logit2 | 0.514 [0.50,0.53] | 0.518 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| Y14-barrier-timing+base | sig | POOLED/ST | Yu3_g_Y14_base_vr:logit2 | 0.523 [0.51,0.54] | 0.518 [0.50,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | ASIA/ST | Yu3_g_Y15_only_vt:logit2 | 0.506 [0.48,0.54] | 0.517 [0.48,0.56] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | POOLED/ST | Yu3_g_Y13_base_vr:logit2 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | ASIA/HM | Yu3_g_Y11_only_vt:stack | 0.503 [0.47,0.53] | 0.517 [0.48,0.56] | - | - | - | N | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| Y11-es-engine-agree+base | sig | POOLED/ST | Yu3_g_Y11_base_vr:gbt3 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | POOLED/ST | Yu3_g_Y15_base_vr:gbt3 | 0.520 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | POOLED/HM | Yu3_g_U_base_vr:rf | 0.526 [0.51,0.54] | 0.517 [0.50,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | ASIA | Yu3_g_Y15_only_vr:logit2 | 0.516 [0.49,0.54] | 0.517 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | POOLED/HM | Yu3_g_Y14_base_vr:rf | 0.524 [0.51,0.54] | 0.517 [0.50,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | ASIA | Yu3_g_Y15_only_vt:logit2 | 0.515 [0.49,0.54] | 0.516 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | LONDON/ST | Yu3_g_Y12_only_vr:rf | 0.520 [0.49,0.55] | 0.516 [0.49,0.55] | - | - | - | N | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| Y11-es-engine-agree+base | sig | POOLED | Yu3_g_Y11_base_vr:logit2 | 0.519 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | NY | Yu3_g_Y13_only_vt:stack | 0.505 [0.49,0.53] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| Y14-barrier-timing | sig | NY | Yu3_g_Y14_only_vt:gbt3 | 0.502 [0.48,0.52] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| Y13-crossbook-agree+base | sig | POOLED | Yu3_g_Y13_base_vr:logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | POOLED | Yu3_g_Y12_base_vr:logit2 | 0.519 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | LONDON/ST | Yu3_g_Y12_only_vt:rf | 0.519 [0.49,0.55] | 0.516 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | POOLED/HM | Yu3_g_Y12_only_vr:rf | 0.513 [0.50,0.53] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | NY/HM | Yu3_g_Y11_base_vt:logit2 | 0.510 [0.49,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | POOLED/ST | Yu3_g_Y12_only_vt:rf | 0.517 [0.50,0.53] | 0.515 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | NY/ST | Yu3_g_Y12_only_vt:rf | 0.520 [0.50,0.54] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | NY/HM | Yu3_g_Y12_only_vt:stack | 0.509 [0.48,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| Y14-barrier-timing | sig | NY/ST | Yu3_g_Y14_only_vt:gbt3 | 0.504 [0.48,0.52] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | ASIA/ST | Yu3_g_Y12_only_vr:rf | 0.509 [0.48,0.53] | 0.514 [0.49,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | ASIA/HM | Yu3_g_Y15_only_vt:logit2 | 0.527 [0.50,0.56] | 0.514 [0.47,0.56] | - | - | - | N | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| Y15-levels-stoprun | sig | POOLED | Yu3_g_Y15_only_vr:rf | 0.524 [0.51,0.54] | 0.514 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | POOLED | Yu3_g_Y14_base_vr:logit2 | 0.520 [0.51,0.53] | 0.514 [0.50,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | NY/HM | Yu3_g_Y13_base_vt:logit2 | 0.509 [0.49,0.53] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | ASIA/ST | Yu3_g_Y12_only_vt:rf | 0.508 [0.48,0.53] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | ASIA/HM | Yu3_g_Y15_only_vr:logit2 | 0.527 [0.50,0.56] | 0.514 [0.47,0.56] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y15-levels-stoprun | sig | POOLED/HM | Yu3_g_Y15_only_vt:rf | 0.521 [0.50,0.54] | 0.514 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| Y15-levels-stoprun+base | sig | NY/HM | Yu3_g_Y15_base_vt:logit2 | 0.508 [0.48,0.53] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| YU3-union+base | sig | POOLED/ST | Yu3_g_U_base_vr:stack | 0.517 [0.50,0.53] | 0.513 [0.50,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | POOLED/HM | Yu3_g_Y11_base_vr:logit2 | 0.519 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | NY | Yu3_g_Y12_only_vt:rf | 0.516 [0.50,0.53] | 0.513 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| YU3-union+base | sig | POOLED | Yu3_g_U_base_vr:rf | 0.520 [0.51,0.53] | 0.513 [0.50,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | NY | Yu3_g_U_base_vt:logit2 | 0.507 [0.49,0.52] | 0.513 [0.49,0.54] | - | - | - | ok | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| Y15-levels-stoprun+base | sig | POOLED/HM | Yu3_g_Y15_base_vr:logit2 | 0.518 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | NY/HM | Yu3_g_U_base_vt:rf | 0.508 [0.48,0.53] | 0.513 [0.48,0.55] | - | - | - | ok | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| Y14-barrier-timing+base | sig | NY | Yu3_g_Y14_base_vt:logit2 | 0.508 [0.49,0.53] | 0.512 [0.49,0.54] | - | - | - | ok | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| Y12-closed-trade-path+base | sig | NY/HM | Yu3_g_Y12_base_vt:logit2 | 0.508 [0.48,0.53] | 0.512 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| Y13-crossbook-agree | sig | POOLED | Yu3_g_Y13_only_vr:logit2 | 0.509 [0.50,0.52] | 0.512 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | POOLED/ST | Yu3_g_Y11_only_vr:stack | 0.509 [0.50,0.52] | 0.512 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | POOLED | Yu3_g_Y11_only_vr:stack | 0.507 [0.49,0.52] | 0.512 [0.50,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | POOLED/HM | Yu3_g_Y14_only_vt:logit2 | 0.502 [0.48,0.52] | 0.512 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| Y14-barrier-timing+base | sig | NY/HM | Yu3_g_Y14_base_vt:gbt3 | 0.505 [0.48,0.53] | 0.512 [0.47,0.55] | - | - | - | ok | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| Y12-closed-trade-path+base | sig | POOLED/HM | Yu3_g_Y12_base_vr:logit2 | 0.518 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | POOLED/HM | Yu3_g_Y11_only_vr:stack | 0.504 [0.49,0.52] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | NY | Yu3_g_Y15_only_vr:stack | 0.532 [0.51,0.55] | 0.511 [0.49,0.54] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | POOLED | Yu3_g_Y14_only_vt:logit2 | 0.502 [0.49,0.51] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| Y12-closed-trade-path | sig | POOLED | Yu3_g_Y12_only_vt:rf | 0.510 [0.50,0.52] | 0.511 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| Y15-levels-stoprun | sig | NY/HM | Yu3_g_Y15_only_vt:stack | 0.519 [0.49,0.55] | 0.510 [0.48,0.55] | - | - | - | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| Y11-es-engine-agree | sig | POOLED | Yu3_g_Y11_only_vt:stack | 0.500 [0.49,0.51] | 0.510 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| Y11-es-engine-agree+base | sig | ASIA/ST | Yu3_g_Y11_base_vr:stack | 0.510 [0.48,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | POOLED/ST | Yu3_g_Y11_only_vt:stack | 0.503 [0.49,0.52] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| Y13-crossbook-agree+base | sig | ASIA/ST | Yu3_g_Y13_base_vr:stack | 0.507 [0.48,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | ASIA/ST | Yu3_g_Y11_base_vt:stack | 0.508 [0.48,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | ASIA/ST | Yu3_g_Y13_base_vt:stack | 0.505 [0.48,0.53] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | POOLED/ST | Yu3_g_Y15_only_vr:rf | 0.519 [0.51,0.53] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | POOLED | Yu3_g_Y15_base_vr:gbt3 | 0.516 [0.51,0.53] | 0.509 [0.50,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | NY/ST | Yu3_g_Y13_only_vt:stack | 0.504 [0.48,0.52] | 0.509 [0.48,0.54] | - | - | - | N | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| Y15-levels-stoprun | sig | POOLED | Yu3_g_Y15_only_vt:rf | 0.515 [0.50,0.53] | 0.509 [0.49,0.52] | - | - | - | N | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| Y11-es-engine-agree | sig | POOLED/HM | Yu3_g_Y11_only_vt:logit2 | 0.501 [0.48,0.52] | 0.508 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| Y15-levels-stoprun | sig | LONDON/HM | Yu3_g_Y15_only_vr:rf | 0.523 [0.49,0.55] | 0.508 [0.47,0.54] | - | - | - | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| Y14-barrier-timing | sig | ASIA/HM | Yu3_g_Y14_only_vt:logit2 | 0.500 [0.47,0.53] | 0.508 [0.47,0.55] | - | - | - | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| Y14-barrier-timing | sig | ASIA/HM | Yu3_g_Y14_only_vr:logit2 | 0.500 [0.47,0.53] | 0.508 [0.47,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | ASIA | Yu3_g_Y13_only_vr:stack | 0.498 [0.48,0.52] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | POOLED/ST | Yu3_g_Y13_only_vr:rf | 0.506 [0.49,0.52] | 0.507 [0.49,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | ASIA | Yu3_g_Y13_only_vt:stack | 0.495 [0.47,0.52] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | POOLED/HM | Yu3_g_Y13_base_vr:rf | 0.516 [0.50,0.53] | 0.507 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | NY/ST | Yu3_g_Y15_only_vr:stack | 0.530 [0.51,0.55] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | POOLED/ST | Yu3_g_Y15_base_vt:gbt3 | 0.506 [0.49,0.52] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | ASIA | Yu3_g_Y11_base_vr:stack | 0.509 [0.48,0.53] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | NY | Yu3_g_Y15_only_vt:stack | 0.518 [0.50,0.54] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| Y12-closed-trade-path+base | sig | POOLED/ST | Yu3_g_Y12_base_vt:logit2 | 0.503 [0.49,0.52] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | POOLED/ST | Yu3_g_Y15_only_vt:rf | 0.510 [0.50,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y11-es-engine-agree+base | sig | POOLED/ST | Yu3_g_Y11_base_vt:logit2 | 0.503 [0.49,0.52] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | POOLED | Yu3_g_Y13_only_vt:logit2 | 0.501 [0.49,0.51] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | ASIA | Yu3_g_Y11_base_vt:stack | 0.506 [0.48,0.53] | 0.505 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | POOLED/ST | Yu3_g_Y13_base_vt:logit2 | 0.502 [0.49,0.51] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | LONDON | Yu3_g_Y12_only_vr:rf | 0.505 [0.48,0.53] | 0.504 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.176 AUC, 5 of 5 econ |
| YU3-union+base | sig | POOLED/ST | Yu3_g_U_base_vt:logit2 | 0.502 [0.49,0.52] | 0.503 [0.49,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing | sig | LONDON/ST | Yu3_g_Y14_only_vr:logit2 | 0.513 [0.49,0.54] | 0.503 [0.47,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| YU3-union+base | sig | ASIA/HM | Yu3_g_U_base_vr:rf | 0.512 [0.48,0.54] | 0.503 [0.46,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | LONDON | Yu3_g_Y12_only_vt:rf | 0.504 [0.48,0.53] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| YU3-union+base | sig | ASIA/HM | Yu3_g_U_base_vt:rf | 0.509 [0.48,0.54] | 0.503 [0.46,0.54] | - | - | - | ok | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| Y11-es-engine-agree+base | sig | POOLED | Yu3_g_Y11_base_vt:logit2 | 0.502 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | NY/ST | Yu3_g_Y15_only_vt:stack | 0.518 [0.50,0.54] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| Y14-barrier-timing+base | sig | ASIA/HM | Yu3_g_Y14_base_vr:rf | 0.503 [0.47,0.53] | 0.502 [0.46,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | LONDON/HM | Yu3_g_Y11_only_vr:logit2 | 0.507 [0.48,0.54] | 0.502 [0.47,0.53] | - | - | - | N | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| Y12-closed-trade-path+base | sig | POOLED | Yu3_g_Y12_base_vt:logit2 | 0.501 [0.49,0.51] | 0.502 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | POOLED | Yu3_g_Y13_base_vt:logit2 | 0.500 [0.49,0.51] | 0.502 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | LONDON/HM | Yu3_g_Y15_only_vt:gbt3 | 0.519 [0.49,0.55] | 0.502 [0.47,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y14-barrier-timing+base | sig | POOLED/ST | Yu3_g_Y14_base_vt:logit2 | 0.503 [0.49,0.52] | 0.502 [0.48,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing | sig | ASIA | Yu3_g_Y14_only_vr:logit2 | 0.500 [0.48,0.52] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | ASIA | Yu3_g_Y14_only_vt:logit2 | 0.499 [0.48,0.52] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | LONDON/ST | Yu3_g_Y11_base_vr:gbt3 | 0.498 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | LONDON/ST | Yu3_g_Y15_base_vr:gbt3 | 0.501 [0.48,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y13-crossbook-agree+base | sig | LONDON/ST | Yu3_g_Y13_base_vr:rf | 0.490 [0.46,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | LONDON/HM | Yu3_g_Y11_only_vt:logit2 | 0.506 [0.47,0.53] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | NY/ST | Yu3_g_Y11_only_vr:stack | 0.513 [0.50,0.53] | 0.499 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | POOLED/ST | Yu3_g_Y14_only_vt:gbt3 | 0.498 [0.48,0.51] | 0.499 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | LONDON/ST | Yu3_g_Y14_only_vt:logit2 | 0.510 [0.49,0.53] | 0.499 [0.47,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y14-barrier-timing | sig | LONDON | Yu3_g_Y14_only_vr:logit2 | 0.505 [0.48,0.53] | 0.499 [0.47,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| YU3-union+base | sig | POOLED/HM | Yu3_g_U_base_vt:rf | 0.503 [0.49,0.52] | 0.499 [0.47,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | POOLED | Yu3_g_Y15_base_vt:gbt3 | 0.500 [0.49,0.51] | 0.498 [0.48,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | ASIA/ST | Yu3_g_Y12_base_vr:gbt3 | 0.496 [0.46,0.52] | 0.498 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | POOLED/HM | Yu3_g_Y14_base_vt:rf | 0.501 [0.48,0.52] | 0.498 [0.47,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | ASIA/ST | Yu3_g_Y12_base_vt:gbt3 | 0.493 [0.46,0.52] | 0.498 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | POOLED/HM | Yu3_g_Y11_base_vt:logit2 | 0.500 [0.49,0.52] | 0.498 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | POOLED/HM | Yu3_g_Y15_base_vt:logit2 | 0.500 [0.48,0.51] | 0.497 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | POOLED/HM | Yu3_g_Y13_base_vt:logit2 | 0.499 [0.48,0.51] | 0.497 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | LONDON/ST | Yu3_g_Y11_base_vt:gbt3 | 0.495 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | LONDON/ST | Yu3_g_Y15_base_vt:gbt3 | 0.499 [0.47,0.52] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y11-es-engine-agree | sig | NY | Yu3_g_Y11_only_vr:stack | 0.512 [0.49,0.53] | 0.497 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | POOLED | Yu3_g_Y14_base_vt:logit2 | 0.499 [0.49,0.51] | 0.497 [0.48,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | LONDON/ST | Yu3_g_Y13_base_vt:rf | 0.487 [0.46,0.51] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | NY/ST | Yu3_g_Y11_only_vt:stack | 0.504 [0.49,0.52] | 0.497 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | POOLED/HM | Yu3_g_Y12_base_vt:logit2 | 0.498 [0.48,0.51] | 0.496 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | POOLED | Yu3_g_U_base_vt:rf | 0.498 [0.49,0.51] | 0.496 [0.48,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing | sig | ASIA/ST | Yu3_g_Y14_only_vr:logit2 | 0.499 [0.47,0.53] | 0.496 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | LONDON | Yu3_g_Y14_only_vt:logit2 | 0.502 [0.48,0.53] | 0.496 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | ASIA/ST | Yu3_g_Y14_only_vt:logit2 | 0.498 [0.47,0.53] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing | sig | LONDON/HM | Yu3_g_Y14_only_vr:logit2 | 0.495 [0.46,0.53] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - |  | short by 0.185 AUC, 5 of 5 econ |
| Y13-crossbook-agree | sig | POOLED/ST | Yu3_g_Y13_only_vt:gbt3 | 0.496 [0.48,0.51] | 0.495 [0.48,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | NY | Yu3_g_Y11_only_vt:stack | 0.501 [0.48,0.52] | 0.494 [0.47,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | LONDON/ST | Yu3_g_Y13_only_vr:gbt3 | 0.508 [0.48,0.53] | 0.494 [0.46,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| YU3-union+base | sig | LONDON/ST | Yu3_g_U_base_vr:logit2 | 0.505 [0.48,0.53] | 0.493 [0.47,0.52] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| Y13-crossbook-agree | sig | LONDON | Yu3_g_Y13_only_vr:gbt3 | 0.503 [0.48,0.53] | 0.493 [0.46,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y11-es-engine-agree | sig | NY/HM | Yu3_g_Y11_only_vr:stack | 0.510 [0.48,0.53] | 0.493 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | ASIA | Yu3_g_Y15_base_vr:logit2 | 0.501 [0.48,0.53] | 0.493 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | ASIA | Yu3_g_Y13_base_vr:logit2 | 0.498 [0.48,0.52] | 0.493 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | LONDON/ST | Yu3_g_Y11_only_vr:rf | 0.489 [0.46,0.52] | 0.493 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| YU3-union+base | sig | LONDON/ST | Yu3_g_U_base_vt:logit2 | 0.502 [0.48,0.53] | 0.492 [0.46,0.52] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| Y15-levels-stoprun+base | sig | ASIA | Yu3_g_Y15_base_vt:logit2 | 0.500 [0.48,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | LONDON | Yu3_g_Y15_only_vt:gbt3 | 0.507 [0.49,0.53] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y13-crossbook-agree | sig | LONDON/ST | Yu3_g_Y13_only_vt:gbt3 | 0.506 [0.48,0.53] | 0.492 [0.46,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y13-crossbook-agree | sig | LONDON | Yu3_g_Y13_only_vt:gbt3 | 0.502 [0.48,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | ASIA | Yu3_g_Y13_base_vt:logit2 | 0.496 [0.47,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | ASIA | Yu3_g_Y12_base_vt:logit2 | 0.494 [0.47,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | LONDON/HM | Yu3_g_Y13_only_vt:gbt3 | 0.496 [0.47,0.53] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | LONDON/ST | Yu3_g_Y11_only_vt:rf | 0.488 [0.46,0.51] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | LONDON/HM | Yu3_g_Y13_only_vr:gbt3 | 0.496 [0.47,0.53] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | ASIA/HM | Yu3_g_Y13_base_vr:logit2 | 0.508 [0.48,0.54] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | ASIA/HM | Yu3_g_Y15_base_vr:logit2 | 0.513 [0.48,0.54] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | NY/HM | Yu3_g_Y11_only_vt:stack | 0.497 [0.47,0.52] | 0.491 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | LONDON | Yu3_g_Y15_only_vr:gbt3 | 0.507 [0.49,0.53] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y12-closed-trade-path+base | sig | ASIA/HM | Yu3_g_Y12_base_vr:logit2 | 0.505 [0.48,0.53] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path | sig | LONDON/HM | Yu3_g_Y12_only_vr:logit2 | 0.491 [0.46,0.52] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | ASIA/HM | Yu3_g_Y11_base_vr:logit2 | 0.508 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | LONDON | Yu3_g_Y15_base_vr:gbt3 | 0.498 [0.48,0.52] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | LONDON | Yu3_g_Y11_only_vr:logit2 | 0.493 [0.47,0.51] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | ASIA/HM | Yu3_g_Y13_base_vt:logit2 | 0.506 [0.48,0.54] | 0.489 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y15-levels-stoprun+base | sig | ASIA/HM | Yu3_g_Y15_base_vt:logit2 | 0.511 [0.48,0.54] | 0.489 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y12-closed-trade-path | sig | LONDON/HM | Yu3_g_Y12_only_vt:logit2 | 0.491 [0.46,0.52] | 0.489 [0.45,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | ASIA | Yu3_g_Y14_base_vr:rf | 0.496 [0.47,0.52] | 0.489 [0.46,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | ASIA | Yu3_g_Y12_base_vr:gbt3 | 0.491 [0.47,0.51] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree | sig | LONDON | Yu3_g_Y11_only_vt:logit2 | 0.493 [0.47,0.51] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | ASIA/HM | Yu3_g_Y12_base_vt:logit2 | 0.502 [0.48,0.53] | 0.489 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y11-es-engine-agree+base | sig | ASIA/HM | Yu3_g_Y11_base_vt:logit2 | 0.506 [0.48,0.54] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Y14-barrier-timing+base | sig | ASIA | Yu3_g_Y14_base_vt:rf | 0.495 [0.47,0.52] | 0.488 [0.46,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | LONDON | Yu3_g_Y15_base_vt:gbt3 | 0.496 [0.47,0.51] | 0.487 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | LONDON/ST | Yu3_g_Y14_base_vr:logit2 | 0.507 [0.48,0.53] | 0.487 [0.46,0.51] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| YU3-union+base | sig | ASIA | Yu3_g_U_base_vr:rf | 0.500 [0.48,0.52] | 0.487 [0.46,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | ASIA | Yu3_g_U_base_vt:rf | 0.498 [0.47,0.52] | 0.486 [0.46,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | LONDON/ST | Yu3_g_Y12_base_vr:logit2 | 0.489 [0.47,0.51] | 0.486 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | LONDON/ST | Yu3_g_Y14_base_vt:logit2 | 0.505 [0.48,0.53] | 0.486 [0.46,0.51] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| Y14-barrier-timing+base | sig | LONDON | Yu3_g_Y14_base_vr:logit2 | 0.498 [0.48,0.52] | 0.485 [0.46,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | LONDON/ST | Yu3_g_Y12_base_vt:logit2 | 0.487 [0.46,0.51] | 0.484 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | LONDON/ST | Yu3_g_Y15_only_vt:gbt3 | 0.498 [0.47,0.52] | 0.484 [0.45,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y11-es-engine-agree+base | sig | LONDON | Yu3_g_Y11_base_vr:rf | 0.490 [0.47,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | LONDON | Yu3_g_U_base_vr:rf | 0.495 [0.47,0.51] | 0.483 [0.45,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | LONDON | Yu3_g_Y14_base_vt:logit2 | 0.496 [0.47,0.52] | 0.483 [0.46,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun | sig | LONDON/ST | Yu3_g_Y15_only_vr:gbt3 | 0.498 [0.47,0.52] | 0.483 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | ASIA/ST | Yu3_g_Y13_only_vr:rf | 0.479 [0.45,0.51] | 0.482 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | LONDON | Yu3_g_Y12_base_vr:rf | 0.490 [0.47,0.51] | 0.482 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | LONDON | Yu3_g_U_base_vt:rf | 0.493 [0.47,0.51] | 0.481 [0.45,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree | sig | ASIA/ST | Yu3_g_Y13_only_vt:rf | 0.478 [0.45,0.51] | 0.481 [0.45,0.51] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | LONDON | Yu3_g_Y11_base_vt:rf | 0.488 [0.47,0.51] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | LONDON | Yu3_g_Y13_base_vr:rf | 0.488 [0.46,0.51] | 0.479 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | LONDON | Yu3_g_Y12_base_vt:rf | 0.488 [0.47,0.51] | 0.479 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing | sig | LONDON/HM | Yu3_g_Y14_only_vt:gbt3 | 0.484 [0.46,0.51] | 0.478 [0.44,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | ASIA/ST | Yu3_g_Y14_base_vt:rf | 0.489 [0.46,0.52] | 0.477 [0.44,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | LONDON/HM | Yu3_g_Y14_base_vr:rf | 0.493 [0.46,0.52] | 0.477 [0.44,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | LONDON | Yu3_g_Y13_base_vt:rf | 0.485 [0.46,0.51] | 0.476 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | LONDON/HM | Yu3_g_Y14_base_vt:rf | 0.492 [0.46,0.52] | 0.474 [0.44,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | LONDON/HM | Yu3_g_U_base_vr:rf | 0.492 [0.46,0.52] | 0.474 [0.44,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | ASIA/ST | Yu3_g_U_base_vt:gbt3 | 0.489 [0.46,0.52] | 0.473 [0.44,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | ASIA/ST | Yu3_g_U_base_vr:gbt3 | 0.491 [0.46,0.52] | 0.473 [0.44,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| YU3-union+base | sig | LONDON/HM | Yu3_g_U_base_vt:rf | 0.491 [0.46,0.52] | 0.472 [0.44,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | ASIA/HM | Yu3_g_Y14_base_vt:logit2 | 0.483 [0.45,0.51] | 0.467 [0.43,0.50] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y14-barrier-timing+base | sig | ASIA/ST | Yu3_g_Y14_base_vr:stack | 0.488 [0.46,0.52] | 0.466 [0.43,0.50] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | LONDON/HM | Yu3_g_Y12_base_vr:rf | 0.490 [0.46,0.52] | 0.462 [0.43,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | LONDON/HM | Yu3_g_Y11_base_vr:rf | 0.489 [0.46,0.52] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | LONDON/HM | Yu3_g_Y15_base_vr:rf | 0.482 [0.46,0.51] | 0.459 [0.42,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y12-closed-trade-path+base | sig | LONDON/HM | Yu3_g_Y12_base_vt:rf | 0.488 [0.46,0.52] | 0.459 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y11-es-engine-agree+base | sig | LONDON/HM | Yu3_g_Y11_base_vt:rf | 0.487 [0.46,0.51] | 0.457 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y15-levels-stoprun+base | sig | LONDON/HM | Yu3_g_Y15_base_vt:rf | 0.480 [0.45,0.51] | 0.455 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | LONDON/HM | Yu3_g_Y13_base_vr:rf | 0.484 [0.46,0.51] | 0.454 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Y13-crossbook-agree+base | sig | LONDON/HM | Yu3_g_Y13_base_vt:rf | 0.483 [0.46,0.51] | 0.450 [0.42,0.48] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- Y11-es-engine-agree -1 POOLED: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 ASIA: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 LONDON: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 NY: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 POOLED: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 ASIA: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 LONDON: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 NY: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 POOLED: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 ASIA: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 LONDON: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree -1 NY: Yu3_g_Y11_only_vt model by WF-PRE
- Y11-es-engine-agree+base -1 POOLED: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 ASIA: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 LONDON: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 NY: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 POOLED: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 ASIA: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 LONDON: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 NY: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 POOLED: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 ASIA: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 LONDON: Yu3_g_Y11_base_vt model by WF-PRE
- Y11-es-engine-agree+base -1 NY: Yu3_g_Y11_base_vt model by WF-PRE
- Y12-closed-trade-path -1 POOLED: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 ASIA: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 LONDON: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 NY: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 POOLED: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 ASIA: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 LONDON: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 NY: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 POOLED: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 ASIA: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 LONDON: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path -1 NY: Yu3_g_Y12_only_vt model by WF-PRE
- Y12-closed-trade-path+base -1 POOLED: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 ASIA: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 LONDON: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 NY: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 POOLED: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 ASIA: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 LONDON: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 NY: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 POOLED: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 ASIA: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 LONDON: Yu3_g_Y12_base_vt model by WF-PRE
- Y12-closed-trade-path+base -1 NY: Yu3_g_Y12_base_vt model by WF-PRE
- Y13-crossbook-agree -1 POOLED: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 ASIA: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 LONDON: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 NY: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 POOLED: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 ASIA: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 LONDON: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 NY: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 POOLED: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 ASIA: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 LONDON: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree -1 NY: Yu3_g_Y13_only_vt model by WF-PRE
- Y13-crossbook-agree+base -1 POOLED: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 ASIA: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 LONDON: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 NY: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 POOLED: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 ASIA: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 LONDON: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 NY: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 POOLED: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 ASIA: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 LONDON: Yu3_g_Y13_base_vt model by WF-PRE
- Y13-crossbook-agree+base -1 NY: Yu3_g_Y13_base_vt model by WF-PRE
- Y14-barrier-timing -1 POOLED: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 ASIA: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 LONDON: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 NY: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 POOLED: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 ASIA: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 LONDON: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 NY: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 POOLED: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 ASIA: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 LONDON: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing -1 NY: Yu3_g_Y14_only_vt model by WF-PRE
- Y14-barrier-timing+base -1 POOLED: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 ASIA: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 LONDON: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 NY: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 POOLED: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 ASIA: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 LONDON: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 NY: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 POOLED: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 ASIA: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 LONDON: Yu3_g_Y14_base_vt model by WF-PRE
- Y14-barrier-timing+base -1 NY: Yu3_g_Y14_base_vt model by WF-PRE
- Y15-levels-stoprun -1 POOLED: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 ASIA: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 LONDON: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 NY: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 POOLED: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 ASIA: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 LONDON: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 NY: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 POOLED: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 ASIA: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 LONDON: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun -1 NY: Yu3_g_Y15_only_vt model by WF-PRE
- Y15-levels-stoprun+base -1 POOLED: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 ASIA: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 LONDON: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 NY: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 POOLED: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 ASIA: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 LONDON: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 NY: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 POOLED: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 ASIA: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 LONDON: Yu3_g_Y15_base_vt model by WF-PRE
- Y15-levels-stoprun+base -1 NY: Yu3_g_Y15_base_vt model by WF-PRE
- YU3-union+base -1 POOLED: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 ASIA: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 LONDON: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 NY: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 POOLED: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 ASIA: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 LONDON: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 NY: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 POOLED: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 ASIA: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 LONDON: Yu3_g_U_base_vt model by WF-PRE
- YU3-union+base -1 NY: Yu3_g_U_base_vt model by WF-PRE
- Y11-es-engine-agree -1 POOLED: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 ASIA: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 LONDON: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 NY: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 POOLED: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 ASIA: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 LONDON: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 NY: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 POOLED: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 ASIA: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 LONDON: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree -1 NY: Yu3_g_Y11_only_vr model by WF-PRE
- Y11-es-engine-agree+base -1 POOLED: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 ASIA: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 LONDON: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 NY: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 POOLED: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 ASIA: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 LONDON: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 NY: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 POOLED: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 ASIA: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 LONDON: Yu3_g_Y11_base_vr model by WF-PRE
- Y11-es-engine-agree+base -1 NY: Yu3_g_Y11_base_vr model by WF-PRE
- Y12-closed-trade-path -1 POOLED: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 ASIA: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 LONDON: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 NY: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 POOLED: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 ASIA: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 LONDON: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 NY: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 POOLED: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 ASIA: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 LONDON: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path -1 NY: Yu3_g_Y12_only_vr model by WF-PRE
- Y12-closed-trade-path+base -1 POOLED: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 ASIA: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 LONDON: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 NY: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 POOLED: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 ASIA: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 LONDON: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 NY: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 POOLED: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 ASIA: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 LONDON: Yu3_g_Y12_base_vr model by WF-PRE
- Y12-closed-trade-path+base -1 NY: Yu3_g_Y12_base_vr model by WF-PRE
- Y13-crossbook-agree -1 POOLED: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 ASIA: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 LONDON: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 NY: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 POOLED: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 ASIA: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 LONDON: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 NY: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 POOLED: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 ASIA: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 LONDON: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree -1 NY: Yu3_g_Y13_only_vr model by WF-PRE
- Y13-crossbook-agree+base -1 POOLED: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 ASIA: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 LONDON: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 NY: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 POOLED: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 ASIA: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 LONDON: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 NY: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 POOLED: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 ASIA: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 LONDON: Yu3_g_Y13_base_vr model by WF-PRE
- Y13-crossbook-agree+base -1 NY: Yu3_g_Y13_base_vr model by WF-PRE
- Y14-barrier-timing -1 POOLED: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 ASIA: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 LONDON: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 NY: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 POOLED: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 ASIA: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 LONDON: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 NY: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 POOLED: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 ASIA: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 LONDON: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing -1 NY: Yu3_g_Y14_only_vr model by WF-PRE
- Y14-barrier-timing+base -1 POOLED: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 ASIA: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 LONDON: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 NY: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 POOLED: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 ASIA: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 LONDON: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 NY: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 POOLED: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 ASIA: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 LONDON: Yu3_g_Y14_base_vr model by WF-PRE
- Y14-barrier-timing+base -1 NY: Yu3_g_Y14_base_vr model by WF-PRE
- Y15-levels-stoprun -1 POOLED: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 ASIA: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 LONDON: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 NY: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 POOLED: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 ASIA: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 LONDON: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 NY: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 POOLED: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 ASIA: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 LONDON: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun -1 NY: Yu3_g_Y15_only_vr model by WF-PRE
- Y15-levels-stoprun+base -1 POOLED: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 ASIA: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 LONDON: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 NY: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 POOLED: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 ASIA: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 LONDON: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 NY: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 POOLED: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 ASIA: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 LONDON: Yu3_g_Y15_base_vr model by WF-PRE
- Y15-levels-stoprun+base -1 NY: Yu3_g_Y15_base_vr model by WF-PRE
- YU3-union+base -1 POOLED: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 ASIA: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 LONDON: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 NY: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 POOLED: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 ASIA: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 LONDON: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 NY: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 POOLED: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 ASIA: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 LONDON: Yu3_g_U_base_vr model by WF-PRE
- YU3-union+base -1 NY: Yu3_g_U_base_vr model by WF-PRE
