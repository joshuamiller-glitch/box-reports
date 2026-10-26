# PRED ROUND 22 - block G round 2 - G-regime-sequence

Best HOLDOUT F-R AUC: +15 POOLED 0.524 [-,-] | ASIA 0.534 [-,-] | LONDON 0.512 [-,-] | NY 0.527 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.535 [-,-] | ASIA 0.540 [-,-] | LONDON 0.515 [-,-] | NY 0.580 [-,-]
Best G HOLDOUT AUC: 0.616 [0.57,0.66]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg ce1bc14f9d14b6e84bf581a8b9eacbb8a9ffbaabeddc0bf9436273b5f684ae05 ; trials added 600 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': True, 'note': 'G1/G2/G4/G5/G7: first audit had 266 mismatches (HMM float32 refit nondeterminism: audit used a re-fit parameter file); canonicalised on G_series2.npz, features rebuilt, re-run 0/43,920. G3/G6 prefix audit 0/10,086,582. decisions 360 (A full-refilter 36); feature checks 43920; mismatches 0; by feature {} | G3/G6 prefix audit: cuts 5; feature checks 10086582; mismatches 0; detail {}'} ; holdout scored True ; feature store ['l2vast/pred/store/G3.parquet', 'l2vast/pred/store/G3_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G-sig-BASE | sig | NY | rf | 0.605 [0.57,0.64] | 0.616 [0.57,0.66] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G3 | pre | NY | stack | - | 0.611 [-,-] | - | - | 0.540 | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G3+BASE | sig | LONDON | logit2 | 0.628 [0.59,0.66] | 0.607 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G3+BASE | sig | NY | rf | 0.598 [0.56,0.63] | 0.606 [0.56,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | LONDON | logit2 | 0.626 [0.59,0.66] | 0.604 [0.56,0.65] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +60 | NY | gbt3 | - | 0.598 [-,-] | - | - | 0.878 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | POOLED/HM | rf | 0.587 [0.57,0.60] | 0.583 [0.55,0.61] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +20 | NY | stack | - | 0.583 [-,-] | - | - | 0.837 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | POOLED | rf | 0.583 [0.56,0.60] | 0.582 [0.56,0.61] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | POOLED/ST | rf | 0.580 [0.56,0.61] | 0.582 [0.55,0.62] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G3+BASE | sig | POOLED/HM | rf | 0.582 [0.56,0.60] | 0.582 [0.55,0.61] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G3+BASE | sig | POOLED/ST | rf | 0.576 [0.55,0.60] | 0.581 [0.55,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G3+BASE | sig | POOLED | rf | 0.578 [0.56,0.60] | 0.581 [0.55,0.61] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +30 | NY | logit2 | - | 0.580 [-,-] | - | - | 0.594 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3+BASE | sig | ASIA | rf | 0.546 [0.52,0.58] | 0.563 [0.53,0.60] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +10 | NY | rf | - | 0.558 [-,-] | - | - | 0.764 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +30 | NY | rf | - | 0.549 [-,-] | - | - | 0.798 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | ASIA | stack | 0.542 [0.51,0.57] | 0.548 [0.51,0.59] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +45 | POOLED | rf | - | 0.542 [-,-] | - | - | 0.675 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +30 | ASIA | gbt3 | - | 0.540 [-,-] | - | - | 0.550 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +45 | NY | gbt3 | - | 0.540 [-,-] | - | - | 0.795 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +30 | ASIA | stack | - | 0.537 [-,-] | - | - | 0.521 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | pre | ASIA | rf | - | 0.536 [-,-] | - | - | 0.535 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +30 | POOLED | gbt3 | - | 0.535 [-,-] | - | - | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +15 | ASIA | rf | - | 0.534 [-,-] | - | - | 0.544 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G3 | sig | NY | gbt3 | 0.529 [0.49,0.56] | 0.532 [0.49,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | LONDON | logit2 | 0.533 [0.50,0.57] | 0.530 [0.48,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G3 | +5 | LONDON | stack | - | 0.528 [-,-] | - | - | 0.507 | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +15 | NY | stack | - | 0.527 [-,-] | - | - | 0.801 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +60 | POOLED | rf | - | 0.527 [-,-] | - | - | 0.699 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +10 | LONDON | rf | - | 0.526 [-,-] | - | - | 0.653 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G3+BASE | sig | LONDON | logit2 | 0.532 [0.50,0.56] | 0.525 [0.48,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| G3 | +60 | ASIA | stack | - | 0.525 [-,-] | - | - | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +15 | POOLED | rf | - | 0.524 [-,-] | - | - | 0.695 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +10 | ASIA | gbt3 | - | 0.524 [-,-] | - | - | 0.525 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +10 | ASIA | rf | - | 0.522 [-,-] | - | - | 0.517 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +5 | NY | gbt3 | - | 0.520 [-,-] | - | - | 0.504 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +5 | ASIA | rf | - | 0.520 [-,-] | - | - | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +5 | NY | rf | - | 0.520 [-,-] | - | - | 0.709 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | pre | LONDON | gbt3 | - | 0.519 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +30 | LONDON | gbt3 | - | 0.515 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | POOLED/HM | rf | 0.514 [0.49,0.54] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3 | sig | POOLED/HM | gbt3 | 0.515 [0.49,0.54] | 0.515 [0.47,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G3 | +10 | POOLED | rf | - | 0.515 [-,-] | - | - | 0.666 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +20 | POOLED | rf | - | 0.514 [-,-] | - | - | 0.681 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +45 | ASIA | rf | - | 0.514 [-,-] | - | - | 0.497 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +20 | ASIA | logit2 | - | 0.514 [-,-] | - | - | 0.508 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +60 | LONDON | rf | - | 0.513 [-,-] | - | - | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G3 | sig | NY | gbt3 | 0.533 [0.49,0.57] | 0.512 [0.45,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G3 | +15 | LONDON | rf | - | 0.512 [-,-] | - | - | 0.663 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +15 | ASIA | logit2 | - | 0.511 [-,-] | - | - | 0.505 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | POOLED | logit2 | 0.502 [0.48,0.52] | 0.508 [0.48,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3 | sig | POOLED | gbt3 | 0.507 [0.49,0.52] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | NY | gbt3 | 0.510 [0.47,0.55] | 0.503 [0.44,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3 | sig | LONDON | rf | 0.506 [0.47,0.54] | 0.502 [0.46,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3 | sig | POOLED/HM | logit2 | 0.503 [0.48,0.52] | 0.502 [0.47,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G3 | +45 | LONDON | gbt3 | - | 0.501 [-,-] | - | - | 0.627 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G3+BASE | sig | POOLED/HM | gbt3 | 0.510 [0.49,0.53] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| G3 | +20 | NY | logit2 | - | 0.498 [-,-] | - | - | 0.505 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3+BASE | sig | NY | gbt3 | 0.524 [0.49,0.56] | 0.497 [0.45,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| G-sig-G3+BASE | sig | ASIA | stack | 0.491 [0.46,0.52] | 0.496 [0.46,0.54] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | ASIA | stack | 0.497 [0.47,0.53] | 0.496 [0.46,0.54] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +45 | POOLED | rf | - | 0.495 [-,-] | - | - | 0.588 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3+BASE | sig | POOLED | gbt3 | 0.502 [0.48,0.52] | 0.491 [0.47,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| G3 | pre | LONDON | rf | - | 0.491 [-,-] | - | - | 0.505 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3 | sig | POOLED/ST | gbt3 | 0.499 [0.48,0.52] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G3 | +45 | NY | stack | - | 0.490 [-,-] | - | - | 0.573 | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G3 | sig | ASIA | rf | 0.490 [0.47,0.51] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3 | sig | POOLED | rf | 0.494 [0.48,0.51] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3 | sig | ASIA | stack | 0.481 [0.46,0.51] | 0.485 [0.45,0.53] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +20 | ASIA | stack | - | 0.485 [-,-] | - | - | 0.481 | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G3+BASE | sig | POOLED/ST | gbt3 | 0.495 [0.47,0.52] | 0.485 [0.46,0.51] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| G3 | +20 | LONDON | gbt3 | - | 0.484 [-,-] | - | - | 0.647 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G3 | sig | LONDON | gbt3 | 0.506 [0.48,0.54] | 0.483 [0.44,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G3 | pre | POOLED | rf | - | 0.483 [-,-] | - | - | 0.648 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | POOLED/ST | gbt3 | 0.486 [0.46,0.51] | 0.481 [0.45,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G3 | +5 | ASIA | gbt3 | - | 0.480 [-,-] | - | - | 0.480 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +45 | ASIA | gbt3 | - | 0.480 [-,-] | - | - | 0.493 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +15 | NY | stack | - | 0.480 [-,-] | - | - | 0.460 | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +20 | POOLED | rf | - | 0.477 [-,-] | - | - | 0.584 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +10 | NY | gbt3 | - | 0.476 [-,-] | - | - | 0.543 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +15 | POOLED | logit2 | - | 0.474 [-,-] | - | - | 0.553 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G3 | sig | POOLED/ST | rf | 0.490 [0.47,0.51] | 0.473 [0.44,0.50] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G3 | +30 | LONDON | stack | - | 0.471 [-,-] | - | - | 0.446 | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +30 | POOLED | rf | - | 0.470 [-,-] | - | - | 0.571 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +10 | POOLED | gbt3 | - | 0.465 [-,-] | - | - | 0.555 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +60 | LONDON | stack | - | 0.465 [-,-] | - | - | 0.470 | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +60 | POOLED | stack | - | 0.462 [-,-] | - | - | 0.572 | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +5 | POOLED | rf | - | 0.461 [-,-] | - | - | 0.632 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +60 | ASIA | logit2 | - | 0.459 [-,-] | - | - | 0.471 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +5 | POOLED | stack | - | 0.459 [-,-] | - | - | 0.555 | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +10 | LONDON | stack | - | 0.453 [-,-] | - | - | 0.474 | ok | - | - | - | - |  | locked label (reference only) |
| G3 | pre | ASIA | rf | - | 0.453 [-,-] | - | - | 0.461 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +60 | NY | stack | - | 0.452 [-,-] | - | - | 0.525 | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +45 | LONDON | stack | - | 0.450 [-,-] | - | - | 0.478 | ok | - | - | - | - |  | locked label (reference only) |
| G3 | +15 | LONDON | gbt3 | - | 0.447 [-,-] | - | - | 0.446 | N | - | - | - | - |  | locked label (reference only) |
| G3 | pre | NY | rf | - | 0.444 [-,-] | - | - | 0.690 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | +5 | LONDON | rf | - | 0.443 [-,-] | - | - | 0.590 | ok | - | - | - | - | stack | locked label (reference only) |
| G3 | pre | POOLED | rf | - | 0.440 [-,-] | - | - | 0.555 | N | - | - | - | - |  | locked label (reference only) |
| G3 | +20 | LONDON | stack | - | 0.429 [-,-] | - | - | 0.450 | ok | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- G3 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G3 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 NY: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 NY: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G3 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G3+BASE -1 POOLED: no gate econ (AUC far below 0.68)
