# PRED ROUND 69 - block X1 round 6 - X1-G-specialised

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.535 [0.51,0.56]
Gap to FOUND: 0.145 AUC, 5 of 5 economic conditions short.
not found - short by 0.145 AUC and 5 of 5 economic conditions

prereg 7b5a5849c8ea2898c73e2aa2ce6563e42483a5dc244c7dcf531528f0ae074070 ; trials added 2800 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X4_sigu.parquet', 'l2vast/pred/store/X5_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X1-G-base | sig | NY/ST | b_g_logit2 | 0.542 [0.52,0.56] | 0.535 [0.51,0.56] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| X1-G-base | sig | NY | b_g_logit2 | 0.540 [0.52,0.56] | 0.534 [0.51,0.56] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| X1-G-base | sig | NY/HM | b_g_mono30 | 0.537 [0.51,0.56] | 0.528 [0.50,0.56] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| X1-G-base | sig | ASIA/ST | b_g_xe | 0.508 [0.48,0.54] | 0.517 [0.48,0.55] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X1-G-base | sig | ASIA | b_g_xe | 0.509 [0.49,0.53] | 0.509 [0.48,0.54] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X1-G-xstore | sig | ASIA/HM | x_g_ll | 0.518 [0.49,0.55] | 0.508 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X1-G-base | sig | POOLED/HM | b_g_rf | 0.508 [0.49,0.52] | 0.508 [0.49,0.53] | - | - | - | N | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| X1-G-base | sig | POOLED | b_g_mono30 | 0.518 [0.51,0.53] | 0.507 [0.49,0.52] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| X1-G-xstore | sig | NY/ST | x_g_logit2 | 0.509 [0.49,0.53] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| X1-G-xstore | sig | NY | x_g_logit2 | 0.512 [0.49,0.53] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.174 AUC, 5 of 5 econ |
| X1-G-base | sig | NY/HM | b_g_logit2 | 0.516 [0.49,0.54] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| X1-G-base | sig | POOLED/HM | b_g_mono30 | 0.519 [0.50,0.53] | 0.504 [0.48,0.53] | - | - | - | ok | - | - | - | - |  | dead (no gain over baseline) |
| X1-G-base | sig | POOLED/ST | b_g_pair | 0.515 [0.50,0.53] | 0.503 [0.49,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X1-G-xstore | sig | POOLED | x_g_logit2 | 0.504 [0.49,0.52] | 0.501 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X1-G-base | sig | ASIA/HM | b_g_xe | 0.510 [0.48,0.54] | 0.499 [0.46,0.54] | - | - | - | N | - | - | - | - |  | short by 0.181 AUC, 5 of 5 econ |
| X1-G-base | sig | POOLED/ST | b_g_mono30 | 0.504 [0.49,0.52] | 0.499 [0.48,0.52] | - | - | - | N | - | - | - | - |  | dead (no gain over baseline) |
| X1-G-xstore | sig | LONDON/HM | x_g_mono30 | 0.506 [0.48,0.53] | 0.498 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X1-G-xstore | sig | ASIA/ST | x_g_xe | 0.497 [0.47,0.53] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X1-G-xstore | sig | LONDON | x_g_mono30 | 0.504 [0.48,0.53] | 0.493 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| X1-G-base | sig | LONDON/ST | b_g_mono30 | 0.505 [0.48,0.53] | 0.492 [0.46,0.53] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X1-G-xstore | sig | ASIA | x_g_xe | 0.500 [0.48,0.52] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X1-G-base | sig | LONDON/ST | b_g_pair | 0.501 [0.47,0.53] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - |  | WF-only (dead) |
| X1-G-xstore | sig | LONDON/HM | x_g_mono30 | 0.504 [0.47,0.53] | 0.487 [0.45,0.53] | - | - | - | ok | - | - | - | - | stack | WF-only (dead) |
| X1-G-xstore | sig | LONDON | x_g_mono30 | 0.500 [0.48,0.52] | 0.480 [0.45,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- X1-G-base -1 ASIA: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-xstore -1 POOLED: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 POOLED: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 ASIA: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 POOLED: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 LONDON: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-xstore -1 LONDON: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-xstore -1 NY: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-xstore -1 LONDON: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-xstore -1 NY: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 ASIA: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 NY: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-xstore -1 ASIA: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-xstore -1 ASIA: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 LONDON: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-xstore -1 LONDON: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-xstore -1 LONDON: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-xstore -1 ASIA: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 POOLED: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 POOLED: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 POOLED: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 NY: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 NY: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
- X1-G-base -1 NY: selected by WF-PRE AUC among 14 (variant,model); baseline R0 unlocked stack same label
