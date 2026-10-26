# PRED ROUND 24 - block I round 7 - I6-wavelet

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.606 [0.56,0.65]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 2f3966342d091596543afef853b134a331eb0d65bb0e4f95a1f1e527641446ef ; trials added 212 ; truncation audit {'decisions': 240, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/I6.parquet', 'l2vast/pred/store/I6_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I6-wavelet | sig | LONDON | logit2/GBOTH | 0.627 [0.59,0.66] | 0.606 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I6-wavelet | sig | NY | logit2/GBOTH | 0.605 [0.57,0.64] | 0.601 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I6-wavelet | sig | POOLED/ST | rf/GBOTH | 0.582 [0.56,0.61] | 0.586 [0.55,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I6-wavelet | sig | POOLED | rf/GBOTH | 0.580 [0.56,0.60] | 0.582 [0.56,0.61] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I6-wavelet | sig | POOLED/HM | rf/GBOTH | 0.579 [0.56,0.60] | 0.579 [0.55,0.61] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I6-wavelet | sig | ASIA | logit2/GI1 | 0.546 [0.52,0.57] | 0.554 [0.52,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| I6-wavelet | sig | ASIA | logit2/GI1 | 0.539 [0.51,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| I6-wavelet | sig | LONDON | logit2/GBOTH | 0.558 [0.52,0.60] | 0.528 [0.47,0.59] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I6-wavelet | sig | POOLED/HM | rf/GBOTH | 0.529 [0.51,0.55] | 0.525 [0.49,0.56] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I6-wavelet | sig | POOLED/ST | rf/GBOTH | 0.528 [0.50,0.56] | 0.525 [0.49,0.57] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I6-wavelet | sig | POOLED | rf/GBOTH | 0.528 [0.51,0.55] | 0.525 [0.50,0.55] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I6-wavelet | sig | NY | logit2/GBOTH | 0.543 [0.51,0.58] | 0.522 [0.47,0.57] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- I6-wavelet -1 POOLED: G ALL: same-cell GBASE hold 0.582; delta -0.000
- I6-wavelet -1 POOLED: stop_vs_target variant
- I6-wavelet -1 ASIA: G ASIA: same-cell GBASE hold 0.562; delta -0.008
- I6-wavelet -1 ASIA: stop_vs_target variant
- I6-wavelet -1 POOLED: G HM: same-cell GBASE hold 0.579; delta -0.000
- I6-wavelet -1 POOLED: stop_vs_target variant
- I6-wavelet -1 LONDON: G LONDON: same-cell GBASE hold 0.607; delta -0.000
- I6-wavelet -1 LONDON: stop_vs_target variant
- I6-wavelet -1 NY: G NY: same-cell GBASE hold 0.603; delta -0.002
- I6-wavelet -1 NY: stop_vs_target variant
- I6-wavelet -1 POOLED: G ST: same-cell GBASE hold 0.587; delta -0.001
- I6-wavelet -1 POOLED: stop_vs_target variant
