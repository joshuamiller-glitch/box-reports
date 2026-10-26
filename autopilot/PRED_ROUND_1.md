# PRED ROUND 1 - block E round 1 - E1-E7 cross-asset macro

Best HOLDOUT F-R AUC: +15 POOLED 0.530 [-,-] | ASIA 0.582 [-,-] | LONDON 0.617 [-,-] | NY 0.556 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.554 [-,-] | ASIA 0.582 [-,-] | LONDON 0.618 [-,-] | NY 0.532 [-,-]
Best G HOLDOUT AUC: 0.613 [0.54,0.68]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 175c251a5cb118192bb9ed85808a75b75e6d3e1845fb1fdd7a040e8daeb2d1e7 ; trials added 1500 ; truncation audit {'decisions': 720, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/E1.parquet', 'l2vast/pred/store/E1_sig.parquet', 'l2vast/pred/store/Erates.parquet', 'l2vast/pred/store/Efx.parquet', 'l2vast/pred/store/Ecrypto.parquet', 'l2vast/pred/store/Ecmd.parquet', 'l2vast/pred/store/Eidx.parquet', 'l2vast/pred/store/Exc.parquet', 'l2vast/pred/store/Eterm.parquet', 'l2vast/pred/store/Ecot.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E-sub-Erates | +30 | LONDON | stack | - | 0.618 [-,-] | - | - | 0.604 | - | - | - | - | - |  | locked label (reference only) |
| E-all | +15 | LONDON | gbt3 | - | 0.617 [-,-] | - | - | 0.610 | ok | - | - | - | - |  | locked label (reference only) |
| E-all | +45 | LONDON | stack | - | 0.614 [-,-] | - | - | 0.621 | - | - | - | - | - |  | locked label (reference only) |
| E-G-Ebase | sig | LONDON/ST | logit2 | 0.631 [0.59,0.67] | 0.613 [0.54,0.68] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON/ST | logit2 | 0.624 [0.58,0.67] | 0.613 [0.54,0.67] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc | +15 | LONDON | stack | - | 0.611 [-,-] | - | - | 0.595 | - | - | - | - | - |  | locked label (reference only) |
| E-all | +20 | LONDON | gbt3 | - | 0.610 [-,-] | - | - | 0.608 | ok | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates | +15 | LONDON | stack | - | 0.610 [-,-] | - | - | 0.600 | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +45 | LONDON | rf | - | 0.607 [-,-] | - | - | 0.640 | ok | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON | logit2 | 0.629 [0.59,0.66] | 0.607 [0.56,0.66] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-G-Ebase | sig | NY/ST | rf | 0.591 [0.54,0.64] | 0.605 [0.53,0.68] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-G-Ebase | sig | ASIA/HM | gbt3 | 0.578 [0.54,0.61] | 0.605 [0.56,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-all | +60 | LONDON | logit2 | - | 0.605 [-,-] | - | - | 0.638 | ok | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY | logit2 | 0.611 [0.58,0.64] | 0.603 [0.56,0.65] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY/ST | gbt3 | 0.585 [0.53,0.63] | 0.602 [0.54,0.66] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-G-Ebase | sig | LONDON | logit2 | 0.617 [0.58,0.65] | 0.600 [0.55,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-G-Ebase | sig | ASIA | gbt3 | 0.575 [0.55,0.60] | 0.595 [0.56,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-all | +45 | ASIA | stack | - | 0.593 [-,-] | - | - | 0.581 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY/HM | rf | 0.607 [0.56,0.65] | 0.592 [0.53,0.67] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +15 | LONDON | rf | - | 0.591 [-,-] | - | - | 0.635 | ok | - | - | - | - | stack | locked label (reference only) |
| E-G-Eonly | sig | ASIA/HM | rf | 0.569 [0.53,0.61] | 0.589 [0.54,0.64] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all | +5 | LONDON | gbt3 | - | 0.589 [-,-] | - | - | 0.595 | ok | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED/ST | logit2 | 0.582 [0.56,0.60] | 0.588 [0.56,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-G-Ebase | sig | POOLED | logit2 | 0.583 [0.56,0.60] | 0.588 [0.57,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-G-Ebase | sig | POOLED/ST | logit2 | 0.584 [0.56,0.61] | 0.587 [0.56,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-G-Ebase | sig | POOLED/HM | rf | 0.574 [0.55,0.59] | 0.584 [0.55,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eidx | +30 | ASIA | rf | - | 0.582 [-,-] | - | - | 0.573 | N | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED | logit2 | 0.582 [0.56,0.60] | 0.582 [0.56,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all | +15 | ASIA | rf | - | 0.582 [-,-] | - | - | 0.583 | ok | - | - | - | - |  | locked label (reference only) |
| E-all | +30 | ASIA | rf | - | 0.580 [-,-] | - | - | 0.574 | ok | - | - | - | - |  | locked label (reference only) |
| E-G-Ebase | sig | NY | logit2 | 0.595 [0.56,0.63] | 0.580 [0.53,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-G-Ebase | sig | NY/HM | rf | 0.606 [0.56,0.65] | 0.578 [0.50,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-all | +10 | LONDON | stack | - | 0.575 [-,-] | - | - | 0.569 | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +60 | ASIA | rf | - | 0.575 [-,-] | - | - | 0.568 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-Efx | +30 | ASIA | logit2 | - | 0.575 [-,-] | - | - | 0.566 | N | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED/HM | rf | 0.571 [0.55,0.59] | 0.571 [0.54,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +30 | ASIA | gbt3 | - | 0.571 [-,-] | - | - | 0.561 | ok | - | - | - | - | stack | locked label (reference only) |
| E-all | +60 | POOLED | rf | - | 0.571 [-,-] | - | - | 0.668 | ok | - | - | - | - |  | locked label (reference only) |
| E-G-Eonly | sig | ASIA | rf | 0.562 [0.53,0.59] | 0.568 [0.53,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +60 | LONDON | logit2 | - | 0.568 [-,-] | - | - | 0.608 | ok | - | - | - | - | stack | locked label (reference only) |
| E-G-Eonly | sig | NY | logit2 | 0.558 [0.52,0.59] | 0.568 [0.51,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-G-Eonly | sig | POOLED | logit2 | 0.546 [0.53,0.57] | 0.567 [0.54,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all+base-pertype | +15 | LONDON | logit2 | - | 0.565 [-,-] | - | - | 0.576 | - | - | - | - | - | stack | locked label (reference only) |
| E-G-Ebase | sig | LONDON/HM | rf | 0.563 [0.52,0.60] | 0.564 [0.51,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Exc | +30 | LONDON | stack | - | 0.564 [-,-] | - | - | 0.586 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA/HM | stack | 0.542 [0.51,0.58] | 0.563 [0.51,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all | +20 | ASIA | stack | - | 0.563 [-,-] | - | - | 0.557 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON/HM | rf | 0.588 [0.55,0.63] | 0.562 [0.51,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-G-Ebase | sig | ASIA/ST | logit2 | 0.544 [0.52,0.57] | 0.561 [0.52,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-all+base | +15 | ASIA | gbt3 | - | 0.560 [-,-] | - | - | 0.557 | ok | - | - | - | - | stack | locked label (reference only) |
| E-all+base | +45 | ASIA | stack | - | 0.559 [-,-] | - | - | 0.548 | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA | gbt3 | 0.543 [0.51,0.57] | 0.559 [0.52,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all | +45 | POOLED | rf | - | 0.559 [-,-] | - | - | 0.640 | ok | - | - | - | - |  | locked label (reference only) |
| G-context | sig | ASIA/HM | logit2 | 0.550 [0.51,0.59] | 0.558 [0.51,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc | +15 | ASIA | logit2 | - | 0.557 [-,-] | - | - | 0.541 | N | - | - | - | - |  | locked label (reference only) |
| E-G-Eonly | sig | LONDON/ST | logit2 | 0.528 [0.48,0.57] | 0.556 [0.50,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all | +60 | ASIA | gbt3 | - | 0.556 [-,-] | - | - | 0.557 | ok | - | - | - | - |  | locked label (reference only) |
| E-all+base-pertype | +15 | ASIA | logit2 | - | 0.556 [-,-] | - | - | 0.556 | - | - | - | - | - | stack | locked label (reference only) |
| E-all+base-pertype | +15 | NY | rf | - | 0.556 [-,-] | - | - | 0.677 | - | - | - | - | - | stack | locked label (reference only) |
| E-G-Eonly | sig | POOLED/HM | rf | 0.535 [0.51,0.56] | 0.556 [0.52,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA/ST | logit2 | 0.544 [0.51,0.57] | 0.555 [0.52,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx | +30 | POOLED | rf | - | 0.554 [-,-] | - | - | 0.651 | N | - | - | - | - |  | locked label (reference only) |
| E-all+base | +45 | POOLED | rf | - | 0.553 [-,-] | - | - | 0.657 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eidx | +30 | LONDON | gbt3 | - | 0.552 [-,-] | - | - | 0.586 | N | - | - | - | - |  | locked label (reference only) |
| E-all+base | +30 | LONDON | logit2 | - | 0.551 [-,-] | - | - | 0.593 | ok | - | - | - | - | stack | locked label (reference only) |
| E-G-Eonly | sig | ASIA/ST | logit2 | 0.544 [0.51,0.57] | 0.551 [0.51,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all | +10 | ASIA | rf | - | 0.550 [-,-] | - | - | 0.550 | ok | - | - | - | - |  | locked label (reference only) |
| E-G-Eonly | sig | POOLED/ST | logit2 | 0.540 [0.52,0.56] | 0.549 [0.52,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +10 | LONDON | gbt3 | - | 0.549 [-,-] | - | - | 0.626 | ok | - | - | - | - | stack | locked label (reference only) |
| E-all | +30 | LONDON | gbt3 | - | 0.547 [-,-] | - | - | 0.595 | ok | - | - | - | - |  | locked label (reference only) |
| E-all+base | +10 | ASIA | rf | - | 0.547 [-,-] | - | - | 0.540 | ok | - | - | - | - | stack | locked label (reference only) |
| E-all+base-pertype | +30 | ASIA | stack | - | 0.546 [-,-] | - | - | 0.530 | - | - | - | - | - | stack | locked label (reference only) |
| E-all+base | pre | ASIA | logit2 | - | 0.545 [-,-] | - | - | 0.541 | ok | - | - | - | - | stack | locked label (reference only) |
| E-all+base | +60 | NY | gbt3 | - | 0.544 [-,-] | - | - | 0.734 | ok | - | - | - | - | stack | locked label (reference only) |
| E-all | +30 | POOLED | rf | - | 0.544 [-,-] | - | - | 0.655 | ok | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd | +30 | LONDON | gbt3 | - | 0.543 [-,-] | - | - | 0.592 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates | +30 | ASIA | logit2 | - | 0.542 [-,-] | - | - | 0.526 | N | - | - | - | - |  | locked label (reference only) |
| E-all+base | +60 | POOLED | rf | - | 0.540 [-,-] | - | - | 0.673 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-Efx | +30 | LONDON | rf | - | 0.539 [-,-] | - | - | 0.564 | N | - | - | - | - |  | locked label (reference only) |
| E-all+base | +20 | NY | stack | - | 0.538 [-,-] | - | - | 0.669 | - | - | - | - | - | stack | locked label (reference only) |
| E-G-Eonly | sig | LONDON/HM | logit2 | 0.510 [0.47,0.55] | 0.538 [0.48,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx | +15 | LONDON | stack | - | 0.538 [-,-] | - | - | 0.577 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eterm | +15 | ASIA | gbt3 | - | 0.537 [-,-] | - | - | 0.521 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd | +15 | LONDON | gbt3 | - | 0.537 [-,-] | - | - | 0.573 | N | - | - | - | - |  | locked label (reference only) |
| E-G-Eonly | sig | LONDON | logit2 | 0.523 [0.49,0.56] | 0.535 [0.48,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot | +30 | ASIA | rf | - | 0.533 [-,-] | - | - | 0.534 | N | - | - | - | - |  | locked label (reference only) |
| E-all | +20 | POOLED | rf | - | 0.533 [-,-] | - | - | 0.648 | ok | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc | +30 | NY | gbt3 | - | 0.532 [-,-] | - | - | 0.607 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates | +30 | POOLED | logit2 | - | 0.532 [-,-] | - | - | 0.636 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot | +15 | LONDON | logit2 | - | 0.532 [-,-] | - | - | 0.528 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx | +15 | ASIA | logit2 | - | 0.531 [-,-] | - | - | 0.518 | N | - | - | - | - |  | locked label (reference only) |
| E-all | +15 | POOLED | rf | - | 0.530 [-,-] | - | - | 0.646 | ok | - | - | - | - |  | locked label (reference only) |
| E-all+base | +30 | POOLED | gbt3 | - | 0.530 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | ASIA | rf | 0.526 [0.50,0.56] | 0.528 [0.49,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +20 | ASIA | stack | - | 0.528 [-,-] | - | - | 0.517 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Erates | +15 | POOLED | rf | - | 0.527 [-,-] | - | - | 0.620 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED | rf | 0.514 [0.49,0.54] | 0.527 [0.50,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED/HM | logit2 | 0.520 [0.49,0.55] | 0.527 [0.49,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +15 | NY | rf | - | 0.525 [-,-] | - | - | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| E-G-Eonly | sig | NY/ST | logit2 | 0.527 [0.47,0.58] | 0.524 [0.46,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +15 | POOLED | rf | - | 0.524 [-,-] | - | - | 0.650 | ok | - | - | - | - | stack | locked label (reference only) |
| E-all+base | +5 | NY | rf | - | 0.524 [-,-] | - | - | 0.697 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eterm | +15 | LONDON | rf | - | 0.523 [-,-] | - | - | 0.521 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx | +30 | POOLED | logit2 | - | 0.522 [-,-] | - | - | 0.612 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc | +15 | POOLED | stack | - | 0.522 [-,-] | - | - | 0.622 | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +5 | ASIA | stack | - | 0.521 [-,-] | - | - | 0.522 | - | - | - | - | - | stack | locked label (reference only) |
| E-all+base | +20 | POOLED | stack | - | 0.520 [-,-] | - | - | 0.647 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Exc | +15 | NY | rf | - | 0.519 [-,-] | - | - | 0.588 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc | +30 | ASIA | rf | - | 0.519 [-,-] | - | - | 0.499 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot | +15 | ASIA | rf | - | 0.516 [-,-] | - | - | 0.520 | N | - | - | - | - |  | locked label (reference only) |
| E-all+base | +20 | LONDON | gbt3 | - | 0.516 [-,-] | - | - | 0.581 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eterm | +30 | NY | stack | - | 0.516 [-,-] | - | - | 0.514 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx | +15 | POOLED | logit2 | - | 0.515 [-,-] | - | - | 0.609 | N | - | - | - | - |  | locked label (reference only) |
| E-all | pre | ASIA | gbt3 | - | 0.515 [-,-] | - | - | 0.516 | ok | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc | +30 | POOLED | rf | - | 0.513 [-,-] | - | - | 0.625 | N | - | - | - | - |  | locked label (reference only) |
| E-all+base | +45 | NY | gbt3 | - | 0.513 [-,-] | - | - | 0.627 | ok | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | NY | stack | 0.515 [0.48,0.55] | 0.512 [0.45,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot | +15 | NY | gbt3 | - | 0.511 [-,-] | - | - | 0.574 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Eterm | +15 | NY | stack | - | 0.511 [-,-] | - | - | 0.517 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd | +30 | ASIA | rf | - | 0.511 [-,-] | - | - | 0.498 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY/ST | gbt3 | 0.517 [0.47,0.57] | 0.508 [0.44,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eterm | +15 | POOLED | rf | - | 0.508 [-,-] | - | - | 0.579 | N | - | - | - | - |  | locked label (reference only) |
| E-G-Eonly | sig | NY/HM | logit2 | 0.525 [0.47,0.58] | 0.508 [0.42,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all+base | +10 | POOLED | rf | - | 0.507 [-,-] | - | - | 0.630 | ok | - | - | - | - | stack | locked label (reference only) |
| E-all+base-pertype | +30 | LONDON | logit2 | - | 0.506 [-,-] | - | - | 0.560 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Erates | +15 | NY | stack | - | 0.506 [-,-] | - | - | 0.530 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx | +15 | LONDON | stack | - | 0.504 [-,-] | - | - | 0.506 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates | +30 | NY | rf | - | 0.503 [-,-] | - | - | 0.544 | N | - | - | - | - |  | locked label (reference only) |
| E-all+base-pertype | +15 | POOLED | stack | - | 0.501 [-,-] | - | - | 0.610 | - | - | - | - | - | stack | locked label (reference only) |
| E-all+base | +30 | NY | gbt3 | - | 0.500 [-,-] | - | - | 0.666 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eterm | +30 | LONDON | gbt3 | - | 0.499 [-,-] | - | - | 0.490 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto | +30 | ASIA | logit2 | - | 0.497 [-,-] | - | - | 0.502 | N | - | - | - | - |  | locked label (reference only) |
| E-all+base-pertype | +30 | POOLED | stack | - | 0.497 [-,-] | - | - | 0.617 | - | - | - | - | - | stack | locked label (reference only) |
| E-all | +5 | ASIA | gbt3 | - | 0.497 [-,-] | - | - | 0.498 | ok | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED/ST | gbt3 | 0.516 [0.49,0.54] | 0.496 [0.46,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx | +15 | NY | gbt3 | - | 0.495 [-,-] | - | - | 0.507 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto | +30 | LONDON | gbt3 | - | 0.494 [-,-] | - | - | 0.502 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd | +15 | ASIA | gbt3 | - | 0.494 [-,-] | - | - | 0.498 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd | +30 | POOLED | rf | - | 0.492 [-,-] | - | - | 0.597 | N | - | - | - | - |  | locked label (reference only) |
| E-all | pre | NY | logit2 | - | 0.491 [-,-] | - | - | 0.561 | ok | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot | +30 | NY | logit2 | - | 0.491 [-,-] | - | - | 0.537 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY/HM | stack | 0.529 [0.48,0.58] | 0.491 [0.42,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd | +15 | NY | logit2 | - | 0.491 [-,-] | - | - | 0.509 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx | +30 | NY | logit2 | - | 0.490 [-,-] | - | - | 0.513 | N | - | - | - | - |  | locked label (reference only) |
| E-all | +10 | POOLED | gbt3 | - | 0.490 [-,-] | - | - | 0.594 | ok | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx | +15 | ASIA | gbt3 | - | 0.489 [-,-] | - | - | 0.498 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto | +15 | LONDON | rf | - | 0.489 [-,-] | - | - | 0.492 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | ASIA/ST | gbt3 | 0.521 [0.49,0.55] | 0.488 [0.44,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eterm | +30 | POOLED | rf | - | 0.487 [-,-] | - | - | 0.574 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx | +15 | POOLED | gbt3 | - | 0.484 [-,-] | - | - | 0.580 | N | - | - | - | - |  | locked label (reference only) |
| E-all+base | +10 | NY | gbt3 | - | 0.484 [-,-] | - | - | 0.669 | ok | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | LONDON | gbt3 | 0.479 [0.45,0.51] | 0.484 [0.43,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all | pre | LONDON | gbt3 | - | 0.483 [-,-] | - | - | 0.551 | ok | - | - | - | - |  | locked label (reference only) |
| E-sub-Eterm | +30 | ASIA | gbt3 | - | 0.483 [-,-] | - | - | 0.474 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates | +15 | ASIA | gbt3 | - | 0.483 [-,-] | - | - | 0.479 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto | +15 | NY | logit2 | - | 0.482 [-,-] | - | - | 0.493 | N | - | - | - | - |  | locked label (reference only) |
| E-all+base | +5 | LONDON | rf | - | 0.481 [-,-] | - | - | 0.591 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecrypto | +30 | POOLED | rf | - | 0.481 [-,-] | - | - | 0.589 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot | +15 | POOLED | rf | - | 0.479 [-,-] | - | - | 0.580 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | LONDON/HM | logit2 | 0.477 [0.43,0.52] | 0.478 [0.41,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto | +30 | NY | gbt3 | - | 0.477 [-,-] | - | - | 0.488 | N | - | - | - | - |  | locked label (reference only) |
| E-all | +30 | NY | gbt3 | - | 0.475 [-,-] | - | - | 0.515 | ok | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot | +30 | POOLED | rf | - | 0.475 [-,-] | - | - | 0.593 | N | - | - | - | - |  | locked label (reference only) |
| E-all | +5 | POOLED | gbt3 | - | 0.474 [-,-] | - | - | 0.601 | ok | - | - | - | - |  | locked label (reference only) |
| E-all+base | pre | POOLED | stack | - | 0.471 [-,-] | - | - | 0.607 | - | - | - | - | - | stack | locked label (reference only) |
| E-all+base | +5 | POOLED | rf | - | 0.470 [-,-] | - | - | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| E-all+base | pre | LONDON | gbt3 | - | 0.468 [-,-] | - | - | 0.577 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecot | +30 | LONDON | stack | - | 0.467 [-,-] | - | - | 0.455 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd | +15 | POOLED | gbt3 | - | 0.466 [-,-] | - | - | 0.591 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | LONDON/ST | gbt3 | 0.479 [0.44,0.52] | 0.464 [0.41,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-all | +20 | NY | gbt3 | - | 0.463 [-,-] | - | - | 0.542 | ok | - | - | - | - |  | locked label (reference only) |
| E-all+base | pre | NY | gbt3 | - | 0.461 [-,-] | - | - | 0.619 | ok | - | - | - | - | stack | locked label (reference only) |
| E-all | +45 | NY | gbt3 | - | 0.458 [-,-] | - | - | 0.516 | ok | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto | +15 | POOLED | rf | - | 0.451 [-,-] | - | - | 0.564 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx | +30 | NY | stack | - | 0.450 [-,-] | - | - | 0.597 | - | - | - | - | - |  | locked label (reference only) |
| E-all+base-pertype | +30 | NY | logit2 | - | 0.450 [-,-] | - | - | 0.720 | - | - | - | - | - | stack | locked label (reference only) |
| E-all | +15 | NY | rf | - | 0.442 [-,-] | - | - | 0.567 | ok | - | - | - | - |  | locked label (reference only) |
| E-all | pre | POOLED | gbt3 | - | 0.441 [-,-] | - | - | 0.578 | ok | - | - | - | - |  | locked label (reference only) |
| E-all | +60 | NY | logit2 | - | 0.429 [-,-] | - | - | 0.517 | ok | - | - | - | - |  | locked label (reference only) |
| E-all | +5 | NY | logit2 | - | 0.415 [-,-] | - | - | 0.539 | ok | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto | +15 | ASIA | gbt3 | - | 0.411 [-,-] | - | - | 0.413 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd | +30 | NY | rf | - | 0.394 [-,-] | - | - | 0.419 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx | +15 | NY | gbt3 | - | 0.357 [-,-] | - | - | 0.450 | N | - | - | - | - |  | locked label (reference only) |
| E-all | +10 | NY | gbt3 | - | 0.339 [-,-] | - | - | 0.481 | ok | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- E-all 45 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.600 hold 0.667; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 20 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.584 hold 0.681; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 10 NY: E block; baseline R0 lite best-by-pre same cell pre 0.629 hold 0.765; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 60 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.607 hold 0.705; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 0 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.612 hold 0.646; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 20 NY: E block; baseline R0 lite best-by-pre same cell pre 0.609 hold 0.832; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 5 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.594 hold 0.634; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 0 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.582 hold 0.532; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 45 NY: E block; baseline R0 lite best-by-pre same cell pre 0.643 hold 0.795; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 5 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.544 hold 0.583; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 10 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.628 hold 0.672; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 5 NY: E block; baseline R0 lite best-by-pre same cell pre 0.592 hold 0.716; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 0 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.550 hold 0.651; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 0 NY: E block; baseline R0 lite best-by-pre same cell pre 0.630 hold 0.680; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 45 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.569 hold 0.627; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 20 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.504 hold 0.506; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 20 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.559 hold 0.647; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 60 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.574 hold 0.663; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 5 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.554 hold 0.532; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 10 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.584 hold 0.587; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 60 NY: E block; baseline R0 lite best-by-pre same cell pre 0.705 hold 0.878; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 45 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.507 hold 0.499; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 60 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.472 hold 0.527; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all 10 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.591 hold 0.521; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 60 NY: E block; baseline R0 lite best-by-pre same cell pre 0.705 hold 0.878; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 45 NY: E block; baseline R0 lite best-by-pre same cell pre 0.643 hold 0.795; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 10 NY: E block; baseline R0 lite best-by-pre same cell pre 0.629 hold 0.765; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 5 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.594 hold 0.634; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 45 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.600 hold 0.667; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 10 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.628 hold 0.672; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 20 NY: E block; baseline R0 lite best-by-pre same cell pre 0.609 hold 0.832; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 60 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.607 hold 0.705; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 20 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.584 hold 0.681; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 5 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.544 hold 0.583; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 0 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.612 hold 0.646; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 0 NY: E block; baseline R0 lite best-by-pre same cell pre 0.630 hold 0.680; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 60 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.574 hold 0.663; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 5 NY: E block; baseline R0 lite best-by-pre same cell pre 0.592 hold 0.716; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 10 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.584 hold 0.587; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 5 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.554 hold 0.532; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 20 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.504 hold 0.506; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 45 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.569 hold 0.627; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 0 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.550 hold 0.651; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 0 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.582 hold 0.532; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 10 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.591 hold 0.521; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 45 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.507 hold 0.499; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 20 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.559 hold 0.647; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base 60 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.472 hold 0.527; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecmd 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecmd 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecmd 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecmd 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecmd 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecmd 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecmd 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecmd 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecot 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecot 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecot 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecot 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecot 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecot 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecot 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecot 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecrypto 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecrypto 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecrypto 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecrypto 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecrypto 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecrypto 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecrypto 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Ecrypto 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Efx 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Efx 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Efx 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Efx 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Efx 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Efx 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Efx 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Efx 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eidx 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eidx 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eidx 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eidx 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eidx 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eidx 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eidx 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eidx 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Erates 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Erates 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Erates 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Erates 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Erates 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Erates 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Erates 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Erates 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eterm 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eterm 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eterm 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eterm 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eterm 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eterm 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eterm 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Eterm 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Exc 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Exc 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Exc 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Exc 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Exc 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Exc 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Exc 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-sub-Exc 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base-pertype 30 NY: E block; baseline R0 lite best-by-pre same cell pre 0.619 hold 0.804; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base-pertype 30 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.614 hold 0.686; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base-pertype 30 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.601 hold 0.652; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base-pertype 15 POOLED: E block; baseline R0 lite best-by-pre same cell pre 0.625 hold 0.695; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base-pertype 15 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.576 hold 0.543; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base-pertype 15 NY: E block; baseline R0 lite best-by-pre same cell pre 0.649 hold 0.802; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base-pertype 15 LONDON: E block; baseline R0 lite best-by-pre same cell pre 0.590 hold 0.658; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- E-all+base-pertype 30 ASIA: E block; baseline R0 lite best-by-pre same cell pre 0.515 hold 0.514; econ grid not run (no WF-PRE gain >= 0.02 pooled)
- G-baseline-FAILPRED -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Ebase -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- G-baseline-FAILPRED -1 ASIA: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 NY: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 POOLED: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- E-G-Eonly -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
- G-context -1 LONDON: G per-signal P(stop); E adds nothing over FAILPRED features
