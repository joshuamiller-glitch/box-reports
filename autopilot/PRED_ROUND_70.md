# PRED ROUND 70 - block F round 5 - F-round5 G unlocked

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.547 [0.52,0.57]
Gap to FOUND: 0.133 AUC, 5 of 5 economic conditions short.
not found - short by 0.133 AUC and 5 of 5 economic conditions

prereg 7159c248c173e896a0e837b6b178cca14fd112caf20ab084898edd525aab5b6c ; trials added 1008 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/F_auction_sigu.parquet', 'l2vast/pred/store/F5678_auction2_sigu.parquet', 'l2vast/pred/store/F9_13_tape_sigu.parquet', 'l2vast/pred/store/F14_18_ctx_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G-base(FAILPRED-asof) | sig | NY | logit2 | 0.546 [0.53,0.56] | 0.547 [0.52,0.57] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18+base | sig | NY | logit2 | 0.539 [0.52,0.56] | 0.537 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-F9-13 | sig | NY | rf | 0.543 [0.53,0.56] | 0.533 [0.51,0.56] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18 | sig | NY | stack | 0.542 [0.53,0.56] | 0.532 [0.51,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-4 | sig | NY | rf | 0.536 [0.52,0.55] | 0.521 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F14-18 | sig | POOLED/HM | rf | 0.530 [0.52,0.54] | 0.520 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-base(FAILPRED-asof) | sig | ASIA | gbt3 | 0.509 [0.48,0.53] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| G-F5-8 | sig | POOLED/HM | rf | 0.531 [0.52,0.55] | 0.518 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F14-18 | sig | POOLED/ST | logit2 | 0.523 [0.51,0.54] | 0.518 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-base(FAILPRED-asof) | sig | LONDON | logit2 | 0.512 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - |  | short by 0.162 AUC, 5 of 5 econ |
| G-F1-18+base | sig | POOLED/ST | logit2 | 0.523 [0.51,0.54] | 0.518 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-base(FAILPRED-asof) | sig | POOLED/ST | gbt3 | 0.519 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F5-8 | sig | POOLED/HM | gbt3 | 0.521 [0.50,0.54] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| G-base(FAILPRED-asof) | sig | POOLED | logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-base(FAILPRED-asof) | sig | NY | logit2 | 0.522 [0.50,0.54] | 0.516 [0.49,0.54] | - | - | - | - | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| G-F14-18 | sig | POOLED | logit2 | 0.523 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F14-18 | sig | NY | rf | 0.529 [0.51,0.55] | 0.515 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F5-8 | sig | NY | rf | 0.533 [0.52,0.55] | 0.515 [0.49,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-base(FAILPRED-asof) | sig | POOLED/ST | logit2 | 0.512 [0.50,0.53] | 0.515 [0.50,0.53] | - | - | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| G-F1-18 | sig | ASIA | gbt3 | 0.522 [0.50,0.55] | 0.514 [0.48,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F5-8 | sig | POOLED | rf | 0.525 [0.51,0.54] | 0.514 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-base(FAILPRED-asof) | sig | POOLED/HM | logit2 | 0.517 [0.50,0.53] | 0.513 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18 | sig | POOLED/ST | rf | 0.529 [0.52,0.54] | 0.513 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18+base | sig | POOLED | logit2 | 0.523 [0.51,0.54] | 0.513 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-F14-18 | sig | POOLED/HM | gbt3 | 0.525 [0.51,0.54] | 0.513 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| G-F1-18 | sig | POOLED | rf | 0.529 [0.52,0.54] | 0.513 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F14-18 | sig | POOLED | gbt3 | 0.521 [0.51,0.53] | 0.512 [0.50,0.52] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| G-F14-18 | sig | NY | gbt3 | 0.514 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| G-F14-18 | sig | POOLED/ST | gbt3 | 0.517 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| G-base(FAILPRED-asof) | sig | POOLED | logit2 | 0.513 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| G-F1-18 | sig | POOLED/HM | rf | 0.529 [0.51,0.54] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18 | sig | NY | logit2 | 0.514 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| G-base(FAILPRED-asof) | sig | ASIA | stack | 0.509 [0.49,0.53] | 0.509 [0.48,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F5-8 | sig | ASIA | stack | 0.515 [0.49,0.54] | 0.509 [0.47,0.55] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F9-13 | sig | POOLED/ST | rf | 0.526 [0.51,0.54] | 0.509 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18 | sig | POOLED/ST | rf | 0.511 [0.49,0.53] | 0.509 [0.49,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F5-8 | sig | NY | gbt3 | 0.517 [0.50,0.53] | 0.507 [0.48,0.53] | - | - | - | - | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| G-base(FAILPRED-asof) | sig | POOLED/HM | logit2 | 0.515 [0.50,0.53] | 0.507 [0.48,0.53] | - | - | - | - | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| G-F1-4 | sig | POOLED/ST | rf | 0.523 [0.51,0.53] | 0.507 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18+base | sig | ASIA | rf | 0.518 [0.50,0.54] | 0.507 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| G-F5-8 | sig | POOLED/ST | stack | 0.518 [0.50,0.53] | 0.506 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F5-8 | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.506 [0.49,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-18+base | sig | POOLED/ST | logit2 | 0.513 [0.50,0.53] | 0.506 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| G-F1-18+base | sig | POOLED/HM | gbt3 | 0.521 [0.50,0.54] | 0.506 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-F9-13 | sig | POOLED | rf | 0.528 [0.52,0.54] | 0.506 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18+base | sig | NY | logit2 | 0.518 [0.50,0.53] | 0.506 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.174 AUC, 5 of 5 econ |
| G-F14-18 | sig | ASIA | logit2 | 0.520 [0.50,0.54] | 0.505 [0.48,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F5-8 | sig | LONDON | gbt3 | 0.507 [0.49,0.52] | 0.504 [0.48,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-18+base | sig | POOLED | rf | 0.513 [0.50,0.53] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| G-F14-18 | sig | ASIA | gbt3 | 0.505 [0.48,0.53] | 0.503 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F14-18 | sig | LONDON | gbt3 | 0.524 [0.50,0.55] | 0.503 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-4 | sig | POOLED | rf | 0.523 [0.51,0.53] | 0.503 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18 | sig | LONDON | gbt3 | 0.507 [0.48,0.53] | 0.503 [0.47,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-18+base | sig | POOLED/HM | rf | 0.516 [0.50,0.53] | 0.503 [0.48,0.52] | - | - | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| G-F1-18 | sig | ASIA | gbt3 | 0.526 [0.50,0.55] | 0.503 [0.47,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F5-8 | sig | ASIA | rf | 0.519 [0.49,0.54] | 0.502 [0.47,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F14-18 | sig | LONDON | logit2 | 0.514 [0.49,0.53] | 0.502 [0.48,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F9-13 | sig | ASIA | logit2 | 0.519 [0.49,0.55] | 0.502 [0.47,0.54] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-4 | sig | POOLED/ST | gbt3 | 0.515 [0.50,0.53] | 0.501 [0.48,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F9-13 | sig | POOLED/HM | rf | 0.530 [0.52,0.54] | 0.501 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18 | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.500 [0.48,0.51] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F9-13 | sig | POOLED/ST | logit2 | 0.508 [0.49,0.52] | 0.500 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F9-13 | sig | LONDON | rf | 0.516 [0.49,0.54] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-18+base | sig | LONDON | rf | 0.513 [0.49,0.53] | 0.499 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | WF-only (dead) |
| G-F5-8 | sig | POOLED/ST | gbt3 | 0.503 [0.49,0.51] | 0.499 [0.49,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-4 | sig | POOLED | rf | 0.516 [0.50,0.53] | 0.499 [0.48,0.51] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-4 | sig | POOLED/HM | rf | 0.524 [0.51,0.54] | 0.498 [0.48,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-4 | sig | NY | gbt3 | 0.509 [0.49,0.53] | 0.497 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F5-8 | sig | LONDON | logit2 | 0.498 [0.48,0.52] | 0.496 [0.47,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-4 | sig | ASIA | rf | 0.513 [0.49,0.54] | 0.495 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-18 | sig | POOLED/HM | gbt3 | 0.516 [0.50,0.53] | 0.495 [0.48,0.51] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F9-13 | sig | ASIA | rf | 0.514 [0.49,0.54] | 0.494 [0.46,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F9-13 | sig | POOLED | rf | 0.509 [0.50,0.52] | 0.493 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F9-13 | sig | LONDON | logit2 | 0.518 [0.50,0.54] | 0.490 [0.46,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-base(FAILPRED-asof) | sig | LONDON | gbt3 | 0.497 [0.47,0.52] | 0.490 [0.46,0.52] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F9-13 | sig | NY | rf | 0.509 [0.49,0.53] | 0.490 [0.47,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| G-F1-4 | sig | POOLED/HM | rf | 0.514 [0.50,0.53] | 0.489 [0.47,0.51] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F9-13 | sig | POOLED/HM | rf | 0.513 [0.50,0.53] | 0.485 [0.47,0.50] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-4 | sig | ASIA | gbt3 | 0.518 [0.49,0.54] | 0.484 [0.45,0.51] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-18+base | sig | ASIA | logit2 | 0.504 [0.48,0.53] | 0.483 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-F1-18+base | sig | LONDON | rf | 0.498 [0.48,0.52] | 0.480 [0.45,0.51] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| G-F1-18 | sig | LONDON | rf | 0.509 [0.48,0.53] | 0.478 [0.45,0.50] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-4 | sig | LONDON | rf | 0.509 [0.48,0.53] | 0.475 [0.44,0.51] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| G-F1-4 | sig | LONDON | rf | 0.502 [0.48,0.52] | 0.474 [0.44,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |

One-sentence notes:
- G-F1-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-base(FAILPRED-asof) -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-4 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F5-8 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F9-13 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F14-18 -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 ASIA: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 LONDON: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 NY: G on unlocked label; no gate economics unless pre-bar cleared
- G-F1-18+base -1 POOLED: G on unlocked label; no gate economics unless pre-bar cleared
