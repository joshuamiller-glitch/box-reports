# PRED ROUND 37 - block K round 4 - K4-latefusion-cond

Best HOLDOUT F-R AUC: +15 POOLED 0.574 [0.53,0.62] | ASIA 0.501 [0.44,0.56] | LONDON 0.594 [0.52,0.67] | NY 0.617 [0.51,0.72]
Best HOLDOUT F-R AUC: +30 POOLED 0.566 [0.52,0.61] | ASIA 0.518 [0.46,0.58] | LONDON 0.567 [0.48,0.65] | NY 0.538 [0.44,0.63]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 0ba3a4c2951a58554e47b83d2ff75b659ad4865a96509a13cd0079049c859079 ; trials added 700 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K4-latefusion-cond | +15 | NY | META(base,A,E,F,G,I,B cond-trained) | - | 0.617 [0.51,0.72] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +5 | NY | META(base,A,E,F,G,I,B cond-trained) | - | 0.599 [0.51,0.69] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +15 | LONDON | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.594 [0.52,0.67] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +15 | POOLED | META(base,A,E,F,G,I,B cond-trained) | - | 0.574 [0.53,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +30 | LONDON | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.567 [0.48,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +30 | POOLED | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.566 [0.52,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +60 | LONDON | META(base,A,E,F,G,I,B cond-trained) | - | 0.565 [0.47,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +20 | POOLED | META(base,A,E,F,G,I,B cond-trained) | - | 0.551 [0.51,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +45 | LONDON | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.550 [0.47,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +10 | ASIA | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.544 [0.48,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +30 | NY | META(base,A,E,F,G,I,B cond-trained) | - | 0.538 [0.44,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +20 | LONDON | META(base,A,E,F,G,I,B cond-trained) | - | 0.536 [0.47,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +45 | ASIA | META(base,A,E,F,G,I,B cond-trained) | - | 0.536 [0.47,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +10 | POOLED | META(base,A,E,F,G,I,B cond-trained) | - | 0.532 [0.49,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +5 | POOLED | META(base,A,E,F,G,I,B cond-trained) | - | 0.529 [0.49,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +5 | LONDON | META(base,A,E,F,G,I,B cond-trained) | - | 0.527 [0.46,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +5 | ASIA | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.521 [0.46,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | pre | LONDON | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.518 [0.45,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +30 | ASIA | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.518 [0.46,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +45 | POOLED | META(base,A,E,F,G,I,B cond-trained) | - | 0.517 [0.47,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | pre | POOLED | META(base,A,E,F,G,I,B cond-trained) | - | 0.516 [0.47,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +20 | ASIA | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.516 [0.45,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +20 | NY | META(base,A,E,F,G,I,B cond-trained) | - | 0.515 [0.42,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | pre | ASIA | META(base,A,E,F,G,I,B cond-trained) | - | 0.513 [0.45,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +60 | POOLED | META(base,A,E,F,G,I,B cond-trained) | - | 0.512 [0.46,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +15 | ASIA | META(base,A,E,F,G,I,B cond-trained) | - | 0.501 [0.44,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +60 | ASIA | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.495 [0.43,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +10 | NY | META(base,A,E,F,G,I,B cond-trained) | - | 0.484 [0.39,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +10 | LONDON | META(base,A,E,F,G,I,B cond-trained) | - | 0.470 [0.38,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +45 | NY | META(base,A,E,F,G,I,B cond-trained) | - | 0.463 [0.36,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | +60 | NY | META(base,A,E,F,G,I,B cond-trained) | - | 0.451 [0.34,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K4-latefusion-cond | pre | NY | AVG(base,A,E,F,G,I,B cond-trained) | - | 0.435 [0.35,0.52] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- K4-latefusion-cond 0 POOLED: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 5 POOLED: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 10 POOLED: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 15 POOLED: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 20 POOLED: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 30 POOLED: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 45 POOLED: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 60 POOLED: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 0 ASIA: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 5 ASIA: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 10 ASIA: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 15 ASIA: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 20 ASIA: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 30 ASIA: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 45 ASIA: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 60 ASIA: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 0 LONDON: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 5 LONDON: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 10 LONDON: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 15 LONDON: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 20 LONDON: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 30 LONDON: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 45 LONDON: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 60 LONDON: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 0 NY: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 5 NY: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 10 NY: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 15 NY: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 20 NY: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 30 NY: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 45 NY: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
- K4-latefusion-cond 60 NY: conditional late fusion: WF-PRE <=0.54, holdout <=0.62 vs bar 0.68
