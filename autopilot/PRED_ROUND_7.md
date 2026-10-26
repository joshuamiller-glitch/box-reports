# PRED ROUND 7 - block K round 1 - K1-stack

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.627 [-,-]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 4c4c2e732a481697f7dff37671e9bafdac9665527223da6067910355d8031e9f ; trials added 1500 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1-G-earlyfusion-EI | sig | NY/ST | stack | 0.599 [-,-] | 0.627 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | ASIA/HM | stack | 0.597 [-,-] | 0.626 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | LONDON/ST | stack | 0.619 [-,-] | 0.622 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | POOLED/ST | stack | 0.594 [-,-] | 0.618 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | ASIA | stack | 0.583 [-,-] | 0.616 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | POOLED | stack | 0.591 [-,-] | 0.612 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | ASIA/ST | stack | 0.571 [-,-] | 0.609 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | NY | stack | 0.589 [-,-] | 0.608 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | POOLED/HM | stack | 0.587 [-,-] | 0.606 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | LONDON | stack | 0.604 [-,-] | 0.606 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | LONDON/HM | stack | 0.588 [-,-] | 0.593 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | NY/HM | stack | 0.576 [-,-] | 0.583 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | NY/HM | stack | 0.507 [-,-] | 0.569 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | NY | stack | 0.509 [-,-] | 0.543 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | NY/ST | stack | 0.511 [-,-] | 0.523 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | POOLED/HM | stack | 0.488 [-,-] | 0.502 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | LONDON/HM | stack | 0.463 [-,-] | 0.493 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | POOLED | stack | 0.484 [-,-] | 0.488 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | ASIA/ST | stack | 0.490 [-,-] | 0.486 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | ASIA | stack | 0.493 [-,-] | 0.485 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | ASIA/HM | stack | 0.495 [-,-] | 0.484 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | POOLED/ST | stack | 0.481 [-,-] | 0.476 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | LONDON | stack | 0.451 [-,-] | 0.455 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-G-earlyfusion-EI | sig | LONDON/ST | stack | 0.441 [-,-] | 0.415 [-,-] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | pre | POOLED | rf | - | - | - | - | 0.613 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +5 | POOLED | gbt3 | - | - | - | - | 0.621 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +10 | POOLED | logit2 | - | - | - | - | 0.628 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +15 | POOLED | rf | - | - | - | - | 0.649 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +20 | POOLED | logit2 | - | - | - | - | 0.645 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +30 | POOLED | logit2 | - | - | - | - | 0.656 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +45 | POOLED | rf | - | - | - | - | 0.648 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +60 | POOLED | rf | - | - | - | - | 0.649 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | pre | ASIA | rf | - | - | - | - | 0.536 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +5 | ASIA | gbt3 | - | - | - | - | 0.539 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +10 | ASIA | logit2 | - | - | - | - | 0.529 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +15 | ASIA | rf | - | - | - | - | 0.528 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +20 | ASIA | logit2 | - | - | - | - | 0.504 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +30 | ASIA | logit2 | - | - | - | - | 0.552 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +45 | ASIA | rf | - | - | - | - | 0.515 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +60 | ASIA | rf | - | - | - | - | 0.493 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | pre | LONDON | rf | - | - | - | - | 0.590 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +5 | LONDON | gbt3 | - | - | - | - | 0.605 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +10 | LONDON | logit2 | - | - | - | - | 0.645 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +15 | LONDON | rf | - | - | - | - | 0.636 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +20 | LONDON | logit2 | - | - | - | - | 0.650 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +30 | LONDON | logit2 | - | - | - | - | 0.644 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +45 | LONDON | rf | - | - | - | - | 0.614 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +60 | LONDON | rf | - | - | - | - | 0.628 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | pre | NY | rf | - | - | - | - | 0.583 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +5 | NY | gbt3 | - | - | - | - | 0.583 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +10 | NY | logit2 | - | - | - | - | 0.615 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +15 | NY | rf | - | - | - | - | 0.646 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +20 | NY | logit2 | - | - | - | - | 0.646 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +30 | NY | logit2 | - | - | - | - | 0.649 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +45 | NY | rf | - | - | - | - | 0.661 | - | - | - | - | - | stack | locked label (reference only) |
| K1-earlyfusion-AEI | +60 | NY | rf | - | - | - | - | 0.660 | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- K1-earlyfusion-AEI 0 POOLED: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 5 POOLED: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 10 POOLED: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 15 POOLED: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 20 POOLED: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 30 POOLED: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 45 POOLED: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 60 POOLED: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 0 ASIA: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 5 ASIA: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 10 ASIA: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 15 ASIA: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 20 ASIA: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 30 ASIA: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 45 ASIA: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 60 ASIA: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 0 LONDON: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 5 LONDON: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 10 LONDON: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 15 LONDON: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 20 LONDON: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 30 LONDON: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 45 LONDON: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 60 LONDON: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 0 NY: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 5 NY: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 10 NY: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 15 NY: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 20 NY: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 30 NY: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 45 NY: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-earlyfusion-AEI 60 NY: early fusion below R0 baseline on WF-PRE at h<=15; dilution
- K1-G-earlyfusion-EI -1 POOLED: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 ASIA: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 LONDON: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 NY: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 POOLED: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 ASIA: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 LONDON: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 NY: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 POOLED: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 ASIA: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 LONDON: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 NY: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 POOLED: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 ASIA: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 LONDON: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 NY: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 POOLED: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 ASIA: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 LONDON: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 NY: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 POOLED: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 ASIA: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 LONDON: G stack no gain over FAILPRED-base
- K1-G-earlyfusion-EI -1 NY: G stack no gain over FAILPRED-base
