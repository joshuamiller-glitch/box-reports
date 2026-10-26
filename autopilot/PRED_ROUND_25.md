# PRED ROUND 25 - block I round 8 - I7-signature

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.607 [0.56,0.65]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg bbbda4e9190743a50147a23a2a0d8796956cf6cc2711989b38922b7a653f2563 ; trials added 296 ; truncation audit {'decisions': 240, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/I7.parquet', 'l2vast/pred/store/I7_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I7-signature | sig | LONDON | logit2/GBOTH | 0.627 [0.59,0.66] | 0.607 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I7-signature | sig | NY | logit2/GBOTH | 0.606 [0.57,0.64] | 0.601 [0.55,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I7-signature | sig | POOLED/ST | logit2/GBOTH | 0.587 [0.56,0.61] | 0.596 [0.56,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I7-signature | sig | POOLED | logit2/GBOTH | 0.583 [0.56,0.60] | 0.587 [0.56,0.61] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I7-signature | sig | POOLED/HM | logit2/GBOTH | 0.579 [0.56,0.60] | 0.579 [0.55,0.61] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I7-signature | sig | POOLED/ST | logit2/GBOTH | 0.538 [0.51,0.56] | 0.543 [0.51,0.58] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I7-signature | sig | ASIA | rf/GI1 | 0.540 [0.52,0.56] | 0.541 [0.52,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| I7-signature | sig | POOLED | logit2/GBOTH | 0.532 [0.51,0.55] | 0.532 [0.50,0.56] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I7-signature | sig | LONDON | logit2/GBOTH | 0.559 [0.52,0.60] | 0.529 [0.47,0.59] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I7-signature | sig | ASIA | rf/GI1 | 0.526 [0.50,0.55] | 0.528 [0.50,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| I7-signature | sig | NY | logit2/GBOTH | 0.547 [0.51,0.58] | 0.526 [0.48,0.58] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I7-signature | sig | POOLED/HM | logit2/GBOTH | 0.525 [0.50,0.54] | 0.522 [0.49,0.55] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- I7-signature -1 POOLED: G ALL: same-cell GBASE hold 0.582; delta +0.005
- I7-signature -1 POOLED: stop_vs_target variant
- I7-signature -1 ASIA: G ASIA: same-cell GBASE hold 0.562; delta -0.021
- I7-signature -1 ASIA: stop_vs_target variant
- I7-signature -1 POOLED: G HM: same-cell GBASE hold 0.579; delta +0.000
- I7-signature -1 POOLED: stop_vs_target variant
- I7-signature -1 LONDON: G LONDON: same-cell GBASE hold 0.607; delta +0.000
- I7-signature -1 LONDON: stop_vs_target variant
- I7-signature -1 NY: G NY: same-cell GBASE hold 0.603; delta -0.002
- I7-signature -1 NY: stop_vs_target variant
- I7-signature -1 POOLED: G ST: same-cell GBASE hold 0.587; delta +0.009
- I7-signature -1 POOLED: stop_vs_target variant
