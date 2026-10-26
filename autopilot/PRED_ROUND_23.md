# PRED ROUND 23 - block I round 6 - I5-rocket

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.598 [0.56,0.65]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 3e488b269c3f0b7d559c8c87ed65c4bc32f475c1369be3e164868c6f5baa140b ; trials added 740 ; truncation audit {'decisions': 240, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/I5.parquet', 'l2vast/pred/store/I5_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I5-rocket | sig | LONDON | logit2/GBOTH | 0.622 [0.59,0.66] | 0.598 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I5-rocket | sig | NY | rf/GBOTH | 0.598 [0.56,0.64] | 0.594 [0.54,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I5-rocket | sig | POOLED | logit2/GBOTH | 0.583 [0.57,0.60] | 0.589 [0.56,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I5-rocket | sig | POOLED/HM | logit2/GBOTH | 0.581 [0.56,0.60] | 0.580 [0.55,0.61] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I5-rocket | sig | POOLED/ST | rf/GBOTH | 0.576 [0.55,0.60] | 0.577 [0.55,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I5-rocket | sig | POOLED | logit2/GBOTH | 0.532 [0.51,0.55] | 0.536 [0.51,0.56] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I5-rocket | sig | POOLED/HM | logit2/GBOTH | 0.529 [0.50,0.55] | 0.527 [0.49,0.56] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I5-rocket | sig | ASIA | logit2/GI1 | 0.526 [0.50,0.55] | 0.527 [0.49,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| I5-rocket | sig | LONDON | logit2/GBOTH | 0.556 [0.52,0.59] | 0.523 [0.47,0.58] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I5-rocket | sig | ASIA | logit2/GI1 | 0.515 [0.49,0.54] | 0.520 [0.48,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| I5-rocket | sig | POOLED/ST | rf/GBOTH | 0.521 [0.49,0.55] | 0.517 [0.48,0.56] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I5-rocket | sig | NY | rf/GBOTH | 0.534 [0.50,0.57] | 0.514 [0.46,0.56] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- I5-rocket -1 POOLED: G ALL: same-cell GBASE hold 0.582; delta +0.007
- I5-rocket -1 POOLED: stop_vs_target variant
- I5-rocket -1 ASIA: G ASIA: same-cell GBASE hold 0.562; delta -0.034
- I5-rocket -1 ASIA: stop_vs_target variant
- I5-rocket -1 POOLED: G HM: same-cell GBASE hold 0.579; delta +0.001
- I5-rocket -1 POOLED: stop_vs_target variant
- I5-rocket -1 LONDON: G LONDON: same-cell GBASE hold 0.607; delta -0.009
- I5-rocket -1 LONDON: stop_vs_target variant
- I5-rocket -1 NY: G NY: same-cell GBASE hold 0.603; delta -0.009
- I5-rocket -1 NY: stop_vs_target variant
- I5-rocket -1 POOLED: G ST: same-cell GBASE hold 0.587; delta -0.010
- I5-rocket -1 POOLED: stop_vs_target variant
