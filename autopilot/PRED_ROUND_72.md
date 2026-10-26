# PRED ROUND 72 - block Y1 round 6 - Y25-y-union

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.552 [0.52,0.58]
Gap to FOUND: 0.128 AUC, 5 of 5 economic conditions short.
not found - short by 0.128 AUC and 5 of 5 economic conditions

prereg 7bc3ad30b17029862dc1e053da3c0004606b4b3cbb72d722d16e516bbc8c9653 ; trials added 200 ; truncation audit {'decisions': 6120, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/Y10_parity.parquet', 'l2vast/pred/store/Y10_parity_sig.parquet', 'l2vast/pred/store/Y10_parity_sigu.parquet', 'l2vast/pred/store/Y11_esagree.parquet', 'l2vast/pred/store/Y11_esagree_sig.parquet', 'l2vast/pred/store/Y11_esagree_sigu.parquet', 'l2vast/pred/store/Y12_tradepath.parquet', 'l2vast/pred/store/Y12_tradepath_sig.parquet', 'l2vast/pred/store/Y12_tradepath_sigu.parquet', 'l2vast/pred/store/Y13_crossbook.parquet', 'l2vast/pred/store/Y13_crossbook_sig.parquet', 'l2vast/pred/store/Y13_crossbook_sigu.parquet', 'l2vast/pred/store/Y14_barrier_sig.parquet', 'l2vast/pred/store/Y14_barrier_sigu.parquet', 'l2vast/pred/store/Y15_levels.parquet', 'l2vast/pred/store/Y15_levels_sig.parquet', 'l2vast/pred/store/Y15_levels_sigu.parquet', 'l2vast/pred/store/Y16_mtf_sig.parquet', 'l2vast/pred/store/Y16_mtf_sigu.parquet', 'l2vast/pred/store/Y17_handoff.parquet', 'l2vast/pred/store/Y17_handoff_sig.parquet', 'l2vast/pred/store/Y17_handoff_sigu.parquet', 'l2vast/pred/store/Y18_rangebud.parquet', 'l2vast/pred/store/Y18_rangebud_sig.parquet', 'l2vast/pred/store/Y18_rangebud_sigu.parquet', 'l2vast/pred/store/Y19_vr.parquet', 'l2vast/pred/store/Y19_vr_sig.parquet', 'l2vast/pred/store/Y19_vr_sigu.parquet', 'l2vast/pred/store/Y1_shadow.parquet', 'l2vast/pred/store/Y1_shadow_sig.parquet', 'l2vast/pred/store/Y1_shadow_sigu.parquet', 'l2vast/pred/store/Y20_swing.parquet', 'l2vast/pred/store/Y20_swing_sig.parquet', 'l2vast/pred/store/Y20_swing_sigu.parquet', 'l2vast/pred/store/Y21_queue.parquet', 'l2vast/pred/store/Y21_queue_sig.parquet', 'l2vast/pred/store/Y21_queue_sigu.parquet', 'l2vast/pred/store/Y23_intramom.parquet', 'l2vast/pred/store/Y23_intramom_sig.parquet', 'l2vast/pred/store/Y23_intramom_sigu.parquet', 'l2vast/pred/store/Y3_engstate.parquet', 'l2vast/pred/store/Y3_engstate_sig.parquet', 'l2vast/pred/store/Y3_engstate_sigu.parquet', 'l2vast/pred/store/Y4_lock.parquet', 'l2vast/pred/store/Y4_lock_sig.parquet', 'l2vast/pred/store/Y4_lock_sigu.parquet', 'l2vast/pred/store/Y5_cluster.parquet', 'l2vast/pred/store/Y5_cluster_sig.parquet', 'l2vast/pred/store/Y5_cluster_sigu.parquet', 'l2vast/pred/store/Y6_ebseas.parquet', 'l2vast/pred/store/Y6_ebseas_sig.parquet', 'l2vast/pred/store/Y6_ebseas_sigu.parquet', 'l2vast/pred/store/Y7_knn_sig.parquet', 'l2vast/pred/store/Y7_knn_sigu.parquet', 'l2vast/pred/store/Y8_hmm.parquet', 'l2vast/pred/store/Y8_hmm_sig.parquet', 'l2vast/pred/store/Y8_hmm_sigu.parquet', 'l2vast/pred/store/Y9_trigger.parquet', 'l2vast/pred/store/Y9_trigger_sig.parquet', 'l2vast/pred/store/Y9_trigger_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Y25-y-union+base | sig | NY/ST | Yu6_g_ALLY_base_vr:logit2 | 0.548 [0.53,0.57] | 0.552 [0.52,0.58] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union+base | sig | NY | Yu6_g_ALLY_base_vr:logit2 | 0.548 [0.53,0.57] | 0.551 [0.53,0.58] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union+base | sig | NY/HM | Yu6_g_ALLY_base_vr:logit2 | 0.547 [0.52,0.57] | 0.547 [0.51,0.58] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union | sig | NY | Yu6_g_ALLY_only_vr:gbt3 | 0.544 [0.52,0.57] | 0.547 [0.52,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y25-y-union | sig | NY/HM | Yu6_g_ALLY_only_vr:rf | 0.551 [0.53,0.57] | 0.547 [0.51,0.58] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y25-y-union | sig | NY/ST | Yu6_g_ALLY_only_vr:gbt3 | 0.539 [0.52,0.56] | 0.539 [0.51,0.57] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y25-y-union | sig | POOLED/ST | Yu6_g_ALLY_only_vr:logit2 | 0.532 [0.52,0.55] | 0.531 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y25-y-union | sig | POOLED | Yu6_g_ALLY_only_vr:logit2 | 0.534 [0.52,0.55] | 0.531 [0.51,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y25-y-union | sig | POOLED/HM | Yu6_g_ALLY_only_vr:logit2 | 0.537 [0.52,0.55] | 0.531 [0.51,0.55] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y25-y-union | sig | ASIA/HM | Yu6_g_ALLY_only_vt:logit2 | 0.548 [0.52,0.58] | 0.529 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| Y25-y-union | sig | ASIA/HM | Yu6_g_ALLY_only_vr:logit2 | 0.547 [0.52,0.58] | 0.527 [0.49,0.57] | - | - | - | N | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| Y25-y-union+base | sig | POOLED/ST | Yu6_g_ALLY_base_vr:logit2 | 0.524 [0.51,0.54] | 0.527 [0.51,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union+base | sig | POOLED | Yu6_g_ALLY_base_vr:logit2 | 0.523 [0.51,0.54] | 0.524 [0.51,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union | sig | ASIA | Yu6_g_ALLY_only_vt:logit2 | 0.533 [0.51,0.56] | 0.524 [0.49,0.56] | - | - | - | N | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| Y25-y-union | sig | ASIA | Yu6_g_ALLY_only_vr:logit2 | 0.533 [0.51,0.56] | 0.523 [0.49,0.55] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y25-y-union+base | sig | NY/ST | Yu6_g_ALLY_base_vt:logit2 | 0.513 [0.49,0.53] | 0.521 [0.49,0.55] | - | - | - | ok | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| Y25-y-union+base | sig | POOLED/HM | Yu6_g_ALLY_base_vr:rf | 0.520 [0.50,0.54] | 0.519 [0.50,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union | sig | NY/HM | Yu6_g_ALLY_only_vt:stack | 0.504 [0.48,0.53] | 0.518 [0.48,0.56] | - | - | - | N | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| Y25-y-union | sig | POOLED/ST | Yu6_g_ALLY_only_vt:logit2 | 0.514 [0.50,0.53] | 0.515 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| Y25-y-union+base | sig | NY | Yu6_g_ALLY_base_vt:logit2 | 0.507 [0.49,0.52] | 0.515 [0.49,0.54] | - | - | - | ok | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| Y25-y-union | sig | ASIA/ST | Yu6_g_ALLY_only_vt:gbt3 | 0.518 [0.49,0.55] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y25-y-union | sig | ASIA/ST | Yu6_g_ALLY_only_vr:gbt3 | 0.520 [0.49,0.55] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y25-y-union | sig | POOLED | Yu6_g_ALLY_only_vt:logit2 | 0.514 [0.50,0.53] | 0.514 [0.50,0.53] | - | - | - | N | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| Y25-y-union | sig | NY | Yu6_g_ALLY_only_vt:gbt3 | 0.504 [0.49,0.52] | 0.512 [0.49,0.54] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| Y25-y-union | sig | POOLED/HM | Yu6_g_ALLY_only_vt:logit2 | 0.516 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| Y25-y-union+base | sig | POOLED/ST | Yu6_g_ALLY_base_vt:logit2 | 0.505 [0.49,0.52] | 0.511 [0.49,0.53] | - | - | - | ok | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| Y25-y-union | sig | NY/ST | Yu6_g_ALLY_only_vt:gbt3 | 0.504 [0.48,0.52] | 0.509 [0.48,0.53] | - | - | - | N | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| Y25-y-union+base | sig | ASIA | Yu6_g_ALLY_base_vr:rf | 0.504 [0.48,0.53] | 0.508 [0.48,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union | sig | LONDON/ST | Yu6_g_ALLY_only_vr:logit2 | 0.517 [0.49,0.54] | 0.507 [0.47,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y25-y-union+base | sig | ASIA | Yu6_g_ALLY_base_vt:rf | 0.502 [0.48,0.53] | 0.507 [0.48,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union+base | sig | POOLED | Yu6_g_ALLY_base_vt:logit2 | 0.502 [0.49,0.51] | 0.507 [0.49,0.52] | - | - | - | ok | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| Y25-y-union | sig | LONDON/ST | Yu6_g_ALLY_only_vt:logit2 | 0.515 [0.49,0.54] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y25-y-union | sig | LONDON | Yu6_g_ALLY_only_vr:logit2 | 0.513 [0.49,0.54] | 0.503 [0.47,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y25-y-union+base | sig | ASIA/HM | Yu6_g_ALLY_base_vr:logit2 | 0.502 [0.48,0.53] | 0.502 [0.47,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union+base | sig | ASIA/HM | Yu6_g_ALLY_base_vt:logit2 | 0.502 [0.48,0.53] | 0.502 [0.47,0.54] | - | - | - | ok | - | - | - | - | stack | short by 0.178 AUC, 5 of 5 econ |
| Y25-y-union+base | sig | NY/HM | Yu6_g_ALLY_base_vt:rf | 0.499 [0.48,0.52] | 0.502 [0.47,0.54] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union+base | sig | LONDON/ST | Yu6_g_ALLY_base_vr:logit2 | 0.518 [0.49,0.54] | 0.502 [0.47,0.53] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| Y25-y-union | sig | LONDON | Yu6_g_ALLY_only_vt:logit2 | 0.511 [0.49,0.53] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| Y25-y-union+base | sig | LONDON/ST | Yu6_g_ALLY_base_vt:logit2 | 0.516 [0.49,0.54] | 0.500 [0.47,0.53] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| Y25-y-union+base | sig | POOLED/HM | Yu6_g_ALLY_base_vt:rf | 0.498 [0.48,0.51] | 0.500 [0.48,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union+base | sig | LONDON | Yu6_g_ALLY_base_vr:logit2 | 0.508 [0.48,0.53] | 0.497 [0.47,0.53] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| Y25-y-union | sig | LONDON/HM | Yu6_g_ALLY_only_vr:logit2 | 0.508 [0.48,0.54] | 0.496 [0.46,0.53] | - | - | - | N | - | - | - | - |  | short by 0.184 AUC, 5 of 5 econ |
| Y25-y-union+base | sig | LONDON | Yu6_g_ALLY_base_vt:logit2 | 0.506 [0.48,0.53] | 0.496 [0.47,0.53] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| Y25-y-union | sig | LONDON/HM | Yu6_g_ALLY_only_vt:logit2 | 0.507 [0.48,0.53] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| Y25-y-union+base | sig | ASIA/ST | Yu6_g_ALLY_base_vt:rf | 0.495 [0.47,0.52] | 0.494 [0.46,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union+base | sig | ASIA/ST | Yu6_g_ALLY_base_vr:gbt3 | 0.499 [0.47,0.53] | 0.490 [0.45,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union+base | sig | LONDON/HM | Yu6_g_ALLY_base_vr:rf | 0.484 [0.45,0.51] | 0.472 [0.43,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Y25-y-union+base | sig | LONDON/HM | Yu6_g_ALLY_base_vt:rf | 0.483 [0.45,0.51] | 0.469 [0.43,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- Y25-y-union -1 POOLED: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 ASIA: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 LONDON: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 NY: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 POOLED: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 ASIA: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 LONDON: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 NY: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 POOLED: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 ASIA: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 LONDON: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union -1 NY: Yu6_g_ALLY_only_vt model by WF-PRE
- Y25-y-union+base -1 POOLED: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 ASIA: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 LONDON: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 NY: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 POOLED: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 ASIA: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 LONDON: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 NY: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 POOLED: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 ASIA: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 LONDON: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union+base -1 NY: Yu6_g_ALLY_base_vt model by WF-PRE
- Y25-y-union -1 POOLED: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 ASIA: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 LONDON: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 NY: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 POOLED: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 ASIA: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 LONDON: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 NY: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 POOLED: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 ASIA: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 LONDON: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union -1 NY: Yu6_g_ALLY_only_vr model by WF-PRE
- Y25-y-union+base -1 POOLED: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 ASIA: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 LONDON: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 NY: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 POOLED: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 ASIA: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 LONDON: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 NY: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 POOLED: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 ASIA: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 LONDON: Yu6_g_ALLY_base_vr model by WF-PRE
- Y25-y-union+base -1 NY: Yu6_g_ALLY_base_vr model by WF-PRE
