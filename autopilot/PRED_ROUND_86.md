# PRED ROUND 86 - block F round 8 - F-session-cond-r8

Best HOLDOUT F-R AUC: +15 POOLED 0.548 [0.51,0.59] | ASIA 0.569 [0.51,0.63] | LONDON 0.578 [0.51,0.64] | NY 0.527 [0.46,0.60]
Best HOLDOUT F-R AUC: +30 POOLED 0.519 [0.49,0.55] | ASIA 0.576 [0.51,0.64] | LONDON 0.508 [0.44,0.57] | NY 0.519 [0.46,0.58]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.072 AUC, 5 of 5 economic conditions short.
not found - short by 0.072 AUC and 5 of 5 economic conditions

prereg b226916074c81cb5b813a6a0efe53a6b991761404851e55f35e80a707d4cdcba ; trials added 0 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F9-13 | +20 | ASIA | logit2 | 0.556 [0.51,0.60] | 0.588 [0.53,0.65] | - | 0.589 | - | - | - | - | - | - |  | short by 0.072 AUC, 5 of 5 econ |
| F9-13 | +20 | ASIA | rf | 0.561 [0.52,0.60] | 0.580 [0.52,0.64] | - | 0.574 | - | - | - | - | - | - |  | short by 0.080 AUC, 5 of 5 econ |
| F9-13 | +20 | ASIA | rf | 0.561 [0.52,0.60] | 0.580 [0.52,0.64] | - | 0.574 | - | - | - | - | - | - |  | short by 0.080 AUC, 5 of 5 econ |
| F5-8 | +20 | ASIA | rf | 0.575 [0.53,0.62] | 0.579 [0.51,0.64] | - | 0.576 | - | - | - | - | - | - |  | short by 0.081 AUC, 5 of 5 econ |
| F5-8 | +20 | ASIA | rf | 0.575 [0.53,0.62] | 0.579 [0.51,0.64] | - | 0.576 | - | - | - | - | - | - |  | short by 0.081 AUC, 5 of 5 econ |
| F14-18+base | +15 | LONDON | logit2 | 0.508 [0.46,0.55] | 0.578 [0.51,0.64] | - | 0.572 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | ASIA | gbt3 | 0.550 [0.51,0.59] | 0.576 [0.51,0.64] | - | 0.567 | - | - | - | - | - | - | stack | short by 0.084 AUC, 5 of 5 econ |
| F5-8+base | +30 | ASIA | gbt3 | 0.550 [0.51,0.59] | 0.576 [0.51,0.64] | - | 0.567 | - | - | - | - | - | - | stack | short by 0.084 AUC, 5 of 5 econ |
| F1-4 | +60 | ASIA | stack | 0.554 [0.50,0.60] | 0.570 [0.50,0.64] | - | 0.562 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | ASIA | stack | 0.554 [0.50,0.60] | 0.570 [0.50,0.64] | - | 0.562 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | ASIA | logit2 | 0.545 [0.50,0.59] | 0.569 [0.51,0.63] | - | 0.563 | - | - | - | - | - | - | stack | short by 0.091 AUC, 5 of 5 econ |
| F1-4+base | +15 | ASIA | logit2 | 0.545 [0.50,0.59] | 0.569 [0.51,0.63] | - | 0.563 | - | - | - | - | - | - | stack | short by 0.091 AUC, 5 of 5 econ |
| F1-4+base | +15 | ASIA | logit2 | 0.545 [0.50,0.59] | 0.569 [0.51,0.63] | - | 0.563 | - | - | - | - | - | - | stack | short by 0.091 AUC, 5 of 5 econ |
| F1-4+base | +15 | ASIA | logit2 | 0.545 [0.50,0.59] | 0.569 [0.51,0.63] | - | 0.563 | - | - | - | - | - | - | stack | short by 0.091 AUC, 5 of 5 econ |
| F1-4+base | +15 | ASIA | logit2 | 0.545 [0.50,0.59] | 0.569 [0.51,0.63] | - | 0.563 | - | - | - | - | - | - | stack | short by 0.091 AUC, 5 of 5 econ |
| F1-4+base | +15 | ASIA | logit2 | 0.545 [0.50,0.59] | 0.569 [0.51,0.63] | - | 0.563 | - | - | - | - | - | - | stack | short by 0.091 AUC, 5 of 5 econ |
| F5-8 | +20 | ASIA | logit2 | 0.538 [0.50,0.58] | 0.568 [0.50,0.63] | - | 0.572 | - | - | - | - | - | - |  | short by 0.092 AUC, 5 of 5 econ |
| F1-4+base | +10 | LONDON | logit2 | 0.504 [0.46,0.55] | 0.566 [0.50,0.63] | - | 0.561 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | ASIA | logit2 | 0.523 [0.48,0.57] | 0.565 [0.49,0.63] | - | 0.554 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | ASIA | logit2 | 0.523 [0.48,0.57] | 0.565 [0.49,0.63] | - | 0.554 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | ASIA | logit2 | 0.523 [0.48,0.57] | 0.565 [0.49,0.63] | - | 0.554 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | ASIA | logit2 | 0.523 [0.48,0.57] | 0.565 [0.49,0.63] | - | 0.554 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | ASIA | logit2 | 0.539 [0.49,0.58] | 0.564 [0.51,0.63] | - | 0.564 | - | - | - | - | - | - | stack | short by 0.096 AUC, 5 of 5 econ |
| F14-18+base | +15 | ASIA | logit2 | 0.539 [0.49,0.58] | 0.564 [0.51,0.63] | - | 0.564 | - | - | - | - | - | - | stack | short by 0.096 AUC, 5 of 5 econ |
| F14-18+base | +15 | ASIA | logit2 | 0.539 [0.49,0.58] | 0.564 [0.51,0.63] | - | 0.564 | - | - | - | - | - | - | stack | short by 0.096 AUC, 5 of 5 econ |
| F14-18+base | +15 | ASIA | logit2 | 0.539 [0.49,0.58] | 0.564 [0.51,0.63] | - | 0.564 | - | - | - | - | - | - | stack | short by 0.096 AUC, 5 of 5 econ |
| F14-18+base | +15 | ASIA | logit2 | 0.539 [0.49,0.58] | 0.564 [0.51,0.63] | - | 0.564 | - | - | - | - | - | - | stack | short by 0.096 AUC, 5 of 5 econ |
| F14-18+base | +15 | ASIA | logit2 | 0.539 [0.49,0.58] | 0.564 [0.51,0.63] | - | 0.564 | - | - | - | - | - | - | stack | short by 0.096 AUC, 5 of 5 econ |
| F5-8+base | +45 | ASIA | logit2 | 0.547 [0.50,0.59] | 0.563 [0.50,0.63] | - | 0.560 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | ASIA | logit2 | 0.547 [0.50,0.59] | 0.563 [0.50,0.63] | - | 0.560 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | ASIA | logit2 | 0.547 [0.50,0.59] | 0.563 [0.50,0.63] | - | 0.560 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | ASIA | logit2 | 0.547 [0.50,0.59] | 0.563 [0.50,0.63] | - | 0.560 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | ASIA | rf | 0.547 [0.50,0.59] | 0.563 [0.49,0.63] | - | 0.551 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | ASIA | stack | 0.553 [0.51,0.60] | 0.561 [0.50,0.62] | - | 0.552 | - | - | - | - | - | - |  | short by 0.099 AUC, 5 of 5 econ |
| F9-13 | +20 | ASIA | stack | 0.553 [0.51,0.60] | 0.561 [0.50,0.62] | - | 0.552 | - | - | - | - | - | - |  | short by 0.099 AUC, 5 of 5 econ |
| F9-13 | +20 | ASIA | stack | 0.553 [0.51,0.60] | 0.561 [0.50,0.62] | - | 0.552 | - | - | - | - | - | - |  | short by 0.099 AUC, 5 of 5 econ |
| F9-13 | +20 | ASIA | stack | 0.553 [0.51,0.60] | 0.561 [0.50,0.62] | - | 0.552 | - | - | - | - | - | - |  | short by 0.099 AUC, 5 of 5 econ |
| F1-4 | +60 | ASIA | rf | 0.562 [0.51,0.61] | 0.561 [0.49,0.62] | - | 0.560 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | ASIA | rf | 0.534 [0.49,0.58] | 0.561 [0.50,0.62] | - | 0.551 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | LONDON | logit2 | 0.508 [0.47,0.55] | 0.560 [0.50,0.62] | - | 0.559 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | ASIA | logit2 | 0.546 [0.50,0.59] | 0.558 [0.49,0.63] | - | 0.549 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | ASIA | logit2 | 0.546 [0.50,0.59] | 0.558 [0.49,0.63] | - | 0.549 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | ASIA | logit2 | 0.546 [0.50,0.59] | 0.558 [0.49,0.63] | - | 0.549 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | ASIA | logit2 | 0.546 [0.50,0.59] | 0.558 [0.49,0.63] | - | 0.549 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | LONDON | logit2 | 0.496 [0.45,0.54] | 0.557 [0.49,0.62] | - | 0.553 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | ASIA | logit2 | 0.540 [0.49,0.59] | 0.556 [0.50,0.62] | - | 0.553 | - | - | - | - | - | - | stack | short by 0.104 AUC, 5 of 5 econ |
| F5-8+base | +15 | ASIA | logit2 | 0.540 [0.49,0.59] | 0.556 [0.50,0.62] | - | 0.553 | - | - | - | - | - | - | stack | short by 0.104 AUC, 5 of 5 econ |
| F5-8+base | +15 | ASIA | logit2 | 0.540 [0.49,0.59] | 0.556 [0.50,0.62] | - | 0.553 | - | - | - | - | - | - | stack | short by 0.104 AUC, 5 of 5 econ |
| F5-8+base | +15 | ASIA | logit2 | 0.540 [0.49,0.59] | 0.556 [0.50,0.62] | - | 0.553 | - | - | - | - | - | - | stack | short by 0.104 AUC, 5 of 5 econ |
| F5-8+base | +15 | ASIA | logit2 | 0.540 [0.49,0.59] | 0.556 [0.50,0.62] | - | 0.553 | - | - | - | - | - | - | stack | short by 0.104 AUC, 5 of 5 econ |
| F5-8+base | +15 | ASIA | logit2 | 0.540 [0.49,0.59] | 0.556 [0.50,0.62] | - | 0.553 | - | - | - | - | - | - | stack | short by 0.104 AUC, 5 of 5 econ |
| F5-8+base | +10 | LONDON | logit2 | 0.506 [0.47,0.54] | 0.556 [0.49,0.62] | - | 0.557 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | ASIA | rf | 0.541 [0.50,0.58] | 0.555 [0.49,0.62] | - | 0.545 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | ASIA | rf | 0.539 [0.50,0.58] | 0.554 [0.49,0.63] | - | 0.551 | - | - | - | - | - | - | stack | short by 0.106 AUC, 5 of 5 econ |
| F14-18+base | +45 | ASIA | logit2 | 0.533 [0.49,0.58] | 0.553 [0.48,0.62] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | ASIA | logit2 | 0.533 [0.49,0.58] | 0.553 [0.48,0.62] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | ASIA | logit2 | 0.533 [0.49,0.58] | 0.553 [0.48,0.62] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | ASIA | logit2 | 0.533 [0.49,0.58] | 0.553 [0.48,0.62] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | LONDON | rf | 0.523 [0.49,0.56] | 0.552 [0.50,0.60] | - | 0.555 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | LONDON | rf | 0.523 [0.49,0.56] | 0.552 [0.50,0.60] | - | 0.555 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | LONDON | rf | 0.523 [0.49,0.56] | 0.552 [0.50,0.60] | - | 0.555 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | ASIA | gbt3 | 0.524 [0.49,0.56] | 0.552 [0.49,0.61] | - | 0.554 | - | - | - | - | - | - | stack | short by 0.108 AUC, 5 of 5 econ |
| F5-8 | +10 | ASIA | rf | 0.563 [0.52,0.60] | 0.552 [0.49,0.62] | - | 0.547 | - | - | - | - | - | - |  | short by 0.108 AUC, 5 of 5 econ |
| F5-8 | +60 | ASIA | stack | 0.547 [0.50,0.59] | 0.551 [0.49,0.61] | - | 0.536 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | ASIA | stack | 0.547 [0.50,0.59] | 0.551 [0.49,0.61] | - | 0.536 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | LONDON | rf | 0.531 [0.49,0.58] | 0.551 [0.49,0.61] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | LONDON | rf | 0.531 [0.49,0.58] | 0.551 [0.49,0.61] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | LONDON | rf | 0.531 [0.49,0.58] | 0.551 [0.49,0.61] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | ASIA | logit2 | 0.527 [0.49,0.57] | 0.551 [0.49,0.61] | - | 0.548 | - | - | - | - | - | - | stack | short by 0.109 AUC, 5 of 5 econ |
| F5-8+base | +60 | LONDON | logit2 | 0.536 [0.49,0.58] | 0.550 [0.48,0.61] | - | 0.550 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | LONDON | logit2 | 0.536 [0.49,0.58] | 0.550 [0.48,0.61] | - | 0.550 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | ASIA | rf | 0.552 [0.51,0.59] | 0.550 [0.49,0.62] | - | 0.543 | - | - | - | - | - | - |  | short by 0.110 AUC, 5 of 5 econ |
| F1-4 | +20 | ASIA | rf | 0.552 [0.51,0.59] | 0.550 [0.49,0.62] | - | 0.543 | - | - | - | - | - | - |  | short by 0.110 AUC, 5 of 5 econ |
| F5-8 | +30 | ASIA | logit2 | 0.532 [0.49,0.58] | 0.549 [0.48,0.62] | - | 0.551 | - | - | - | - | - | - |  | short by 0.111 AUC, 5 of 5 econ |
| F5-8 | +30 | ASIA | logit2 | 0.532 [0.49,0.58] | 0.549 [0.48,0.62] | - | 0.551 | - | - | - | - | - | - |  | short by 0.111 AUC, 5 of 5 econ |
| F5-8 | +30 | ASIA | logit2 | 0.532 [0.49,0.58] | 0.549 [0.48,0.62] | - | 0.551 | - | - | - | - | - | - |  | short by 0.111 AUC, 5 of 5 econ |
| F5-8 | +30 | ASIA | logit2 | 0.532 [0.49,0.58] | 0.549 [0.48,0.62] | - | 0.551 | - | - | - | - | - | - |  | short by 0.111 AUC, 5 of 5 econ |
| F5-8 | +30 | ASIA | logit2 | 0.532 [0.49,0.58] | 0.549 [0.48,0.62] | - | 0.551 | - | - | - | - | - | - |  | short by 0.111 AUC, 5 of 5 econ |
| F5-8+base | +15 | LONDON | logit2 | 0.497 [0.45,0.54] | 0.548 [0.48,0.61] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | ASIA | logit2 | 0.523 [0.48,0.57] | 0.548 [0.49,0.61] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | ASIA | logit2 | 0.523 [0.48,0.57] | 0.548 [0.49,0.61] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | ASIA | logit2 | 0.523 [0.48,0.57] | 0.548 [0.49,0.61] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | ASIA | logit2 | 0.523 [0.48,0.57] | 0.548 [0.49,0.61] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | POOLED | logit2 | 0.519 [0.49,0.54] | 0.548 [0.51,0.59] | - | 0.547 | - | - | - | - | - | - | stack | promising: short by 0.132 AUC, 5 of 5 econ |
| F1-4+base | +15 | LONDON | logit2 | 0.500 [0.46,0.55] | 0.548 [0.48,0.61] | - | 0.544 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | LONDON | logit2 | 0.524 [0.47,0.57] | 0.547 [0.48,0.61] | - | 0.548 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | LONDON | logit2 | 0.524 [0.47,0.57] | 0.547 [0.48,0.61] | - | 0.548 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | LONDON | logit2 | 0.510 [0.47,0.55] | 0.547 [0.49,0.61] | - | 0.551 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | ASIA | stack | 0.529 [0.49,0.57] | 0.547 [0.48,0.61] | - | 0.541 | - | - | - | - | - | - |  | short by 0.113 AUC, 5 of 5 econ |
| F5-8 | +20 | ASIA | stack | 0.529 [0.49,0.57] | 0.547 [0.48,0.61] | - | 0.541 | - | - | - | - | - | - |  | short by 0.113 AUC, 5 of 5 econ |
| F5-8 | +20 | ASIA | stack | 0.529 [0.49,0.57] | 0.547 [0.48,0.61] | - | 0.541 | - | - | - | - | - | - |  | short by 0.113 AUC, 5 of 5 econ |
| F5-8 | +20 | ASIA | stack | 0.529 [0.49,0.57] | 0.547 [0.48,0.61] | - | 0.541 | - | - | - | - | - | - |  | short by 0.113 AUC, 5 of 5 econ |
| F5-8 | +60 | NY | logit2 | 0.512 [0.46,0.56] | 0.547 [0.48,0.61] | - | 0.546 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | NY | logit2 | 0.512 [0.46,0.56] | 0.547 [0.48,0.61] | - | 0.546 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | NY | logit2 | 0.512 [0.46,0.56] | 0.547 [0.48,0.61] | - | 0.546 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | LONDON | logit2 | 0.506 [0.46,0.55] | 0.546 [0.49,0.60] | - | 0.550 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | ASIA | gbt3 | 0.540 [0.50,0.59] | 0.546 [0.48,0.61] | - | 0.550 | - | - | - | - | - | - |  | short by 0.114 AUC, 5 of 5 econ |
| F1-4+base | +60 | ASIA | gbt3 | 0.543 [0.50,0.59] | 0.545 [0.48,0.61] | - | 0.544 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | NY | logit2 | 0.526 [0.48,0.57] | 0.545 [0.47,0.62] | - | 0.547 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | NY | logit2 | 0.526 [0.48,0.57] | 0.545 [0.47,0.62] | - | 0.547 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | NY | logit2 | 0.526 [0.48,0.57] | 0.545 [0.47,0.62] | - | 0.547 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | NY | logit2 | 0.526 [0.48,0.57] | 0.545 [0.47,0.62] | - | 0.547 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | NY | logit2 | 0.526 [0.48,0.57] | 0.545 [0.47,0.62] | - | 0.547 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | ASIA | gbt3 | 0.523 [0.48,0.57] | 0.545 [0.48,0.61] | - | 0.544 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | ASIA | gbt3 | 0.523 [0.48,0.57] | 0.545 [0.48,0.61] | - | 0.544 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.545 [0.49,0.61] | - | 0.541 | - | - | - | - | - | - | stack | short by 0.115 AUC, 5 of 5 econ |
| F9-13+base | +15 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.545 [0.49,0.61] | - | 0.541 | - | - | - | - | - | - | stack | short by 0.115 AUC, 5 of 5 econ |
| F9-13+base | +15 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.545 [0.49,0.61] | - | 0.541 | - | - | - | - | - | - | stack | short by 0.115 AUC, 5 of 5 econ |
| F9-13+base | +15 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.545 [0.49,0.61] | - | 0.541 | - | - | - | - | - | - | stack | short by 0.115 AUC, 5 of 5 econ |
| F9-13+base | +15 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.545 [0.49,0.61] | - | 0.541 | - | - | - | - | - | - | stack | short by 0.115 AUC, 5 of 5 econ |
| F9-13+base | +15 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.545 [0.49,0.61] | - | 0.541 | - | - | - | - | - | - | stack | short by 0.115 AUC, 5 of 5 econ |
| F9-13+base | +10 | LONDON | gbt3 | 0.506 [0.46,0.55] | 0.544 [0.49,0.60] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | ASIA | gbt3 | 0.531 [0.49,0.57] | 0.543 [0.48,0.60] | - | 0.539 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | ASIA | gbt3 | 0.531 [0.49,0.57] | 0.543 [0.48,0.60] | - | 0.536 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | NY | logit2 | 0.525 [0.49,0.56] | 0.543 [0.49,0.60] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | NY | logit2 | 0.525 [0.49,0.56] | 0.543 [0.49,0.60] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | POOLED | rf | 0.528 [0.50,0.55] | 0.543 [0.51,0.58] | - | 0.541 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | POOLED | rf | 0.528 [0.50,0.55] | 0.543 [0.51,0.58] | - | 0.541 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | POOLED | rf | 0.528 [0.50,0.55] | 0.543 [0.51,0.58] | - | 0.541 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | POOLED | rf | 0.528 [0.50,0.55] | 0.543 [0.51,0.58] | - | 0.541 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | ASIA | logit2 | 0.518 [0.48,0.56] | 0.543 [0.48,0.60] | - | 0.537 | - | - | - | - | - | - | stack | short by 0.117 AUC, 5 of 5 econ |
| F9-13+base | +45 | ASIA | rf | 0.518 [0.47,0.56] | 0.542 [0.48,0.60] | - | 0.537 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | POOLED | logit2 | 0.518 [0.49,0.54] | 0.542 [0.51,0.58] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | NY | logit2 | 0.534 [0.49,0.58] | 0.541 [0.47,0.61] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | NY | logit2 | 0.534 [0.49,0.58] | 0.541 [0.47,0.61] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | ASIA | rf | 0.525 [0.48,0.57] | 0.541 [0.47,0.61] | - | 0.539 | - | - | - | - | - | - | stack | short by 0.119 AUC, 5 of 5 econ |
| F5-8 | +15 | ASIA | logit2 | 0.521 [0.48,0.57] | 0.541 [0.48,0.60] | - | 0.540 | - | - | - | - | - | - |  | short by 0.119 AUC, 5 of 5 econ |
| F5-8 | +15 | ASIA | logit2 | 0.521 [0.48,0.57] | 0.541 [0.48,0.60] | - | 0.540 | - | - | - | - | - | - |  | short by 0.119 AUC, 5 of 5 econ |
| F5-8 | +15 | ASIA | logit2 | 0.521 [0.48,0.57] | 0.541 [0.48,0.60] | - | 0.540 | - | - | - | - | - | - |  | short by 0.119 AUC, 5 of 5 econ |
| F5-8 | +15 | ASIA | logit2 | 0.521 [0.48,0.57] | 0.541 [0.48,0.60] | - | 0.540 | - | - | - | - | - | - |  | short by 0.119 AUC, 5 of 5 econ |
| F5-8 | +15 | ASIA | logit2 | 0.521 [0.48,0.57] | 0.541 [0.48,0.60] | - | 0.540 | - | - | - | - | - | - |  | short by 0.119 AUC, 5 of 5 econ |
| F5-8 | +15 | ASIA | logit2 | 0.521 [0.48,0.57] | 0.541 [0.48,0.60] | - | 0.540 | - | - | - | - | - | - |  | short by 0.119 AUC, 5 of 5 econ |
| F5-8+base | +20 | ASIA | gbt3 | 0.528 [0.49,0.57] | 0.541 [0.48,0.60] | - | 0.536 | - | - | - | - | - | - | stack | short by 0.119 AUC, 5 of 5 econ |
| F14-18 | +45 | ASIA | gbt3 | 0.539 [0.50,0.58] | 0.540 [0.47,0.61] | - | 0.534 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | ASIA | gbt3 | 0.539 [0.50,0.58] | 0.540 [0.47,0.61] | - | 0.534 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | ASIA | logit2 | 0.548 [0.50,0.60] | 0.540 [0.46,0.61] | - | 0.531 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | ASIA | logit2 | 0.548 [0.50,0.60] | 0.540 [0.46,0.61] | - | 0.531 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | ASIA | logit2 | 0.548 [0.50,0.60] | 0.540 [0.46,0.61] | - | 0.531 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | ASIA | logit2 | 0.548 [0.50,0.60] | 0.540 [0.46,0.61] | - | 0.531 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.539 [0.48,0.60] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.539 [0.48,0.60] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.539 [0.48,0.60] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.539 [0.48,0.60] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | POOLED | logit2 | 0.499 [0.47,0.53] | 0.539 [0.50,0.58] | - | 0.539 | - | - | - | - | - | - | stack | short by 0.141 AUC, 5 of 5 econ |
| F5-8 | +60 | LONDON | logit2 | 0.537 [0.49,0.58] | 0.539 [0.48,0.60] | - | 0.537 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | LONDON | logit2 | 0.537 [0.49,0.58] | 0.539 [0.48,0.60] | - | 0.537 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | ASIA | logit2 | 0.530 [0.49,0.57] | 0.539 [0.48,0.60] | - | 0.533 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | ASIA | logit2 | 0.530 [0.49,0.57] | 0.539 [0.48,0.60] | - | 0.533 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | ASIA | logit2 | 0.530 [0.49,0.57] | 0.539 [0.48,0.60] | - | 0.533 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | ASIA | logit2 | 0.530 [0.49,0.57] | 0.539 [0.48,0.60] | - | 0.533 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | NY | logit2 | 0.521 [0.47,0.57] | 0.538 [0.47,0.61] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | NY | logit2 | 0.521 [0.47,0.57] | 0.538 [0.47,0.61] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | ASIA | rf | 0.533 [0.49,0.58] | 0.537 [0.47,0.60] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | NY | rf | 0.499 [0.46,0.54] | 0.537 [0.47,0.61] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | NY | rf | 0.499 [0.46,0.54] | 0.537 [0.47,0.61] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | NY | rf | 0.499 [0.46,0.54] | 0.537 [0.47,0.61] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | NY | rf | 0.499 [0.46,0.54] | 0.537 [0.47,0.61] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | POOLED | logit2 | 0.527 [0.50,0.55] | 0.537 [0.50,0.58] | - | 0.536 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F5-8 | +20 | POOLED | logit2 | 0.527 [0.50,0.55] | 0.537 [0.50,0.58] | - | 0.536 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F5-8+base | pre | ASIA | rf | 0.546 [0.51,0.59] | 0.537 [0.48,0.60] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| F5-8+base | pre | ASIA | rf | 0.546 [0.51,0.59] | 0.537 [0.48,0.60] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| F14-18 | +20 | ASIA | gbt3 | 0.522 [0.48,0.56] | 0.536 [0.47,0.59] | - | 0.531 | - | - | - | - | - | - |  | short by 0.124 AUC, 5 of 5 econ |
| F5-8+base | +60 | NY | logit2 | 0.495 [0.45,0.54] | 0.536 [0.47,0.60] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | NY | logit2 | 0.495 [0.45,0.54] | 0.536 [0.47,0.60] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | NY | logit2 | 0.495 [0.45,0.54] | 0.536 [0.47,0.60] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | ASIA | logit2 | 0.518 [0.48,0.56] | 0.536 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.124 AUC, 5 of 5 econ |
| F5-8 | +45 | ASIA | rf | 0.537 [0.49,0.58] | 0.535 [0.47,0.59] | - | 0.527 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | LONDON | rf | 0.541 [0.50,0.58] | 0.535 [0.48,0.60] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | LONDON | rf | 0.541 [0.50,0.58] | 0.535 [0.48,0.60] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | LONDON | rf | 0.541 [0.50,0.58] | 0.535 [0.48,0.60] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | ASIA | gbt3 | 0.543 [0.50,0.58] | 0.535 [0.47,0.59] | - | 0.534 | - | - | - | - | - | - |  | short by 0.125 AUC, 5 of 5 econ |
| F5-8 | +5 | ASIA | gbt3 | 0.543 [0.50,0.58] | 0.535 [0.47,0.59] | - | 0.534 | - | - | - | - | - | - |  | short by 0.125 AUC, 5 of 5 econ |
| F5-8 | +5 | ASIA | gbt3 | 0.543 [0.50,0.58] | 0.535 [0.47,0.59] | - | 0.534 | - | - | - | - | - | - |  | short by 0.125 AUC, 5 of 5 econ |
| F5-8 | +5 | ASIA | gbt3 | 0.543 [0.50,0.58] | 0.535 [0.47,0.59] | - | 0.534 | - | - | - | - | - | - |  | short by 0.125 AUC, 5 of 5 econ |
| F5-8+base | +45 | ASIA | gbt3 | 0.514 [0.47,0.56] | 0.535 [0.47,0.60] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | ASIA | gbt3 | 0.514 [0.47,0.56] | 0.535 [0.47,0.60] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | NY | logit2 | 0.521 [0.47,0.57] | 0.535 [0.46,0.60] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | NY | logit2 | 0.521 [0.47,0.57] | 0.535 [0.46,0.60] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | ASIA | stack | 0.561 [0.52,0.60] | 0.535 [0.47,0.60] | - | 0.529 | - | - | - | - | - | - |  | short by 0.125 AUC, 5 of 5 econ |
| F5-8 | +15 | ASIA | stack | 0.561 [0.52,0.60] | 0.535 [0.47,0.60] | - | 0.529 | - | - | - | - | - | - |  | short by 0.125 AUC, 5 of 5 econ |
| F9-13 | +60 | LONDON | rf | 0.541 [0.50,0.59] | 0.535 [0.47,0.60] | - | 0.536 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | LONDON | rf | 0.541 [0.50,0.59] | 0.535 [0.47,0.60] | - | 0.536 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | LONDON | rf | 0.541 [0.50,0.59] | 0.535 [0.47,0.60] | - | 0.536 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | ASIA | gbt3 | 0.521 [0.48,0.56] | 0.534 [0.47,0.60] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.126 AUC, 5 of 5 econ |
| F1-4+base | +30 | ASIA | gbt3 | 0.521 [0.48,0.56] | 0.534 [0.47,0.60] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.126 AUC, 5 of 5 econ |
| F9-13+base | +60 | ASIA | gbt3 | 0.519 [0.48,0.56] | 0.534 [0.47,0.60] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | ASIA | rf | 0.527 [0.48,0.57] | 0.534 [0.47,0.60] | - | 0.521 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | LONDON | rf | 0.528 [0.48,0.57] | 0.534 [0.47,0.60] | - | 0.540 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | ASIA | rf | 0.530 [0.48,0.58] | 0.534 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | ASIA | rf | 0.545 [0.51,0.58] | 0.533 [0.48,0.59] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.127 AUC, 5 of 5 econ |
| F14-18+base | pre | ASIA | rf | 0.545 [0.51,0.58] | 0.533 [0.48,0.59] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.127 AUC, 5 of 5 econ |
| F5-8+base | +45 | ASIA | rf | 0.524 [0.48,0.57] | 0.533 [0.47,0.60] | - | 0.537 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | ASIA | logit2 | 0.532 [0.48,0.58] | 0.533 [0.46,0.61] | - | 0.528 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | ASIA | logit2 | 0.532 [0.48,0.58] | 0.533 [0.46,0.61] | - | 0.528 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | ASIA | logit2 | 0.532 [0.48,0.58] | 0.533 [0.46,0.61] | - | 0.528 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | ASIA | logit2 | 0.532 [0.48,0.58] | 0.533 [0.46,0.61] | - | 0.528 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | ASIA | stack | 0.530 [0.49,0.57] | 0.533 [0.47,0.59] | - | 0.524 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | POOLED | logit2 | 0.516 [0.49,0.54] | 0.533 [0.50,0.57] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| F1-4+base | +10 | ASIA | logit2 | 0.526 [0.48,0.57] | 0.533 [0.47,0.60] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.127 AUC, 5 of 5 econ |
| F9-13+base | +15 | POOLED | logit2 | 0.510 [0.48,0.54] | 0.533 [0.49,0.58] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| F1-4 | +5 | NY | gbt3 | 0.498 [0.46,0.54] | 0.533 [0.48,0.59] | - | 0.531 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | NY | gbt3 | 0.498 [0.46,0.54] | 0.533 [0.48,0.59] | - | 0.531 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | NY | gbt3 | 0.498 [0.46,0.54] | 0.533 [0.48,0.59] | - | 0.531 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | NY | gbt3 | 0.498 [0.46,0.54] | 0.533 [0.48,0.59] | - | 0.531 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | POOLED | rf | 0.506 [0.48,0.53] | 0.533 [0.49,0.57] | - | 0.529 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| F14-18 | +60 | ASIA | stack | 0.523 [0.48,0.57] | 0.533 [0.46,0.60] | - | 0.531 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | ASIA | stack | 0.523 [0.48,0.57] | 0.533 [0.46,0.60] | - | 0.531 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | ASIA | gbt3 | 0.551 [0.50,0.60] | 0.533 [0.46,0.60] | - | 0.525 | - | - | - | - | - | - |  | short by 0.127 AUC, 5 of 5 econ |
| F9-13+base | +60 | POOLED | logit2 | 0.517 [0.49,0.54] | 0.532 [0.50,0.57] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | POOLED | gbt3 | 0.511 [0.48,0.54] | 0.532 [0.50,0.57] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| F14-18+base | +5 | NY | logit2 | 0.495 [0.45,0.54] | 0.532 [0.47,0.59] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | NY | logit2 | 0.495 [0.45,0.54] | 0.532 [0.47,0.59] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | ASIA | gbt3 | 0.527 [0.48,0.57] | 0.532 [0.47,0.60] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.128 AUC, 5 of 5 econ |
| F14-18+base | +10 | ASIA | gbt3 | 0.527 [0.48,0.57] | 0.532 [0.47,0.60] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.128 AUC, 5 of 5 econ |
| F14-18+base | +10 | ASIA | gbt3 | 0.527 [0.48,0.57] | 0.532 [0.47,0.60] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.128 AUC, 5 of 5 econ |
| F1-4+base | +45 | ASIA | gbt3 | 0.510 [0.46,0.55] | 0.531 [0.47,0.59] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | ASIA | gbt3 | 0.510 [0.46,0.55] | 0.531 [0.47,0.59] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | ASIA | gbt3 | 0.533 [0.49,0.58] | 0.531 [0.47,0.60] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | ASIA | gbt3 | 0.533 [0.49,0.58] | 0.531 [0.47,0.60] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | ASIA | gbt3 | 0.530 [0.49,0.57] | 0.531 [0.47,0.59] | - | 0.520 | - | - | - | - | - | - |  | short by 0.129 AUC, 5 of 5 econ |
| F9-13 | +30 | ASIA | gbt3 | 0.530 [0.49,0.57] | 0.531 [0.47,0.59] | - | 0.520 | - | - | - | - | - | - |  | short by 0.129 AUC, 5 of 5 econ |
| F1-4+base | +30 | ASIA | logit2 | 0.546 [0.50,0.59] | 0.531 [0.48,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| F1-4+base | +30 | ASIA | logit2 | 0.546 [0.50,0.59] | 0.531 [0.48,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| F1-4+base | +30 | ASIA | logit2 | 0.546 [0.50,0.59] | 0.531 [0.48,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| F1-4+base | +30 | ASIA | logit2 | 0.546 [0.50,0.59] | 0.531 [0.48,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| F1-4+base | +30 | ASIA | logit2 | 0.546 [0.50,0.59] | 0.531 [0.48,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| F5-8+base | +20 | LONDON | rf | 0.516 [0.47,0.56] | 0.531 [0.47,0.59] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | LONDON | rf | 0.516 [0.47,0.56] | 0.531 [0.47,0.59] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | LONDON | rf | 0.516 [0.47,0.56] | 0.531 [0.47,0.59] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | ASIA | rf | 0.536 [0.49,0.58] | 0.531 [0.47,0.59] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| F9-13+base | pre | ASIA | rf | 0.536 [0.49,0.58] | 0.531 [0.47,0.59] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| F5-8 | +60 | POOLED | logit2 | 0.522 [0.50,0.55] | 0.531 [0.49,0.57] | - | 0.528 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | POOLED | logit2 | 0.516 [0.49,0.54] | 0.531 [0.49,0.57] | - | 0.529 | - | - | - | - | - | - | stack | short by 0.149 AUC, 5 of 5 econ |
| F14-18 | +60 | ASIA | rf | 0.519 [0.47,0.57] | 0.530 [0.47,0.59] | - | 0.533 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | ASIA | logit2 | 0.517 [0.48,0.56] | 0.530 [0.47,0.59] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | ASIA | logit2 | 0.517 [0.48,0.56] | 0.530 [0.47,0.59] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | ASIA | logit2 | 0.517 [0.48,0.56] | 0.530 [0.47,0.59] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | ASIA | logit2 | 0.517 [0.48,0.56] | 0.530 [0.47,0.59] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | ASIA | logit2 | 0.543 [0.50,0.58] | 0.530 [0.48,0.58] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.130 AUC, 5 of 5 econ |
| F9-13+base | +30 | ASIA | logit2 | 0.543 [0.50,0.58] | 0.530 [0.48,0.58] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.130 AUC, 5 of 5 econ |
| F9-13+base | +30 | ASIA | logit2 | 0.543 [0.50,0.58] | 0.530 [0.48,0.58] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.130 AUC, 5 of 5 econ |
| F9-13+base | +30 | ASIA | logit2 | 0.543 [0.50,0.58] | 0.530 [0.48,0.58] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.130 AUC, 5 of 5 econ |
| F9-13+base | +30 | ASIA | logit2 | 0.543 [0.50,0.58] | 0.530 [0.48,0.58] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.130 AUC, 5 of 5 econ |
| F5-8+base | +60 | ASIA | rf | 0.517 [0.47,0.56] | 0.529 [0.46,0.60] | - | 0.519 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | POOLED | gbt3 | 0.514 [0.49,0.54] | 0.529 [0.49,0.57] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| F5-8+base | +5 | ASIA | logit2 | 0.509 [0.47,0.55] | 0.528 [0.48,0.58] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.132 AUC, 5 of 5 econ |
| F5-8+base | +5 | ASIA | logit2 | 0.509 [0.47,0.55] | 0.528 [0.48,0.58] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.132 AUC, 5 of 5 econ |
| F5-8+base | +15 | POOLED | rf | 0.511 [0.48,0.54] | 0.528 [0.49,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| F14-18 | +45 | ASIA | logit2 | 0.518 [0.47,0.56] | 0.528 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | ASIA | logit2 | 0.518 [0.47,0.56] | 0.528 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | ASIA | logit2 | 0.518 [0.47,0.56] | 0.528 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | ASIA | logit2 | 0.518 [0.47,0.56] | 0.528 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | ASIA | rf | 0.530 [0.49,0.58] | 0.528 [0.46,0.60] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.132 AUC, 5 of 5 econ |
| F9-13+base | +60 | ASIA | stack | 0.536 [0.49,0.58] | 0.528 [0.45,0.60] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | ASIA | stack | 0.536 [0.49,0.58] | 0.528 [0.45,0.60] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | POOLED | rf | 0.526 [0.50,0.55] | 0.528 [0.49,0.57] | - | 0.525 | - | - | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| F5-8+base | +15 | POOLED | logit2 | 0.515 [0.49,0.54] | 0.528 [0.49,0.57] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| F1-4+base | +20 | LONDON | logit2 | 0.496 [0.45,0.55] | 0.528 [0.47,0.59] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | NY | logit2 | 0.497 [0.46,0.54] | 0.527 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | NY | logit2 | 0.497 [0.46,0.54] | 0.527 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | ASIA | gbt3 | 0.519 [0.47,0.56] | 0.527 [0.46,0.59] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.133 AUC, 5 of 5 econ |
| F9-13+base | +30 | ASIA | gbt3 | 0.519 [0.47,0.56] | 0.527 [0.46,0.59] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.133 AUC, 5 of 5 econ |
| F1-4+base | +60 | POOLED | gbt3 | 0.519 [0.49,0.54] | 0.527 [0.48,0.56] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | POOLED | gbt3 | 0.519 [0.49,0.54] | 0.527 [0.48,0.56] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | LONDON | logit2 | 0.533 [0.49,0.58] | 0.527 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | LONDON | logit2 | 0.533 [0.49,0.58] | 0.527 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | NY | gbt3 | 0.489 [0.45,0.53] | 0.527 [0.47,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | ASIA | stack | 0.525 [0.48,0.57] | 0.527 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - |  | short by 0.133 AUC, 5 of 5 econ |
| F1-4 | +15 | ASIA | stack | 0.525 [0.48,0.57] | 0.527 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - |  | short by 0.133 AUC, 5 of 5 econ |
| F14-18+base | +15 | NY | rf | 0.505 [0.46,0.55] | 0.527 [0.46,0.60] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | NY | gbt3 | 0.525 [0.48,0.57] | 0.527 [0.47,0.58] | - | 0.540 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | ASIA | logit2 | 0.536 [0.49,0.58] | 0.527 [0.46,0.60] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | ASIA | logit2 | 0.536 [0.49,0.58] | 0.527 [0.46,0.60] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | ASIA | logit2 | 0.536 [0.49,0.58] | 0.527 [0.46,0.60] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | ASIA | logit2 | 0.536 [0.49,0.58] | 0.527 [0.46,0.60] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | POOLED | logit2 | 0.515 [0.49,0.54] | 0.527 [0.49,0.56] | - | 0.524 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | NY | rf | 0.505 [0.46,0.55] | 0.527 [0.46,0.59] | - | 0.522 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | NY | rf | 0.505 [0.46,0.55] | 0.527 [0.46,0.59] | - | 0.522 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | NY | rf | 0.505 [0.46,0.55] | 0.527 [0.46,0.59] | - | 0.522 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | NY | rf | 0.505 [0.46,0.55] | 0.527 [0.46,0.59] | - | 0.522 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | NY | gbt3 | 0.532 [0.49,0.58] | 0.526 [0.46,0.60] | - | 0.535 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | NY | gbt3 | 0.532 [0.49,0.58] | 0.526 [0.46,0.60] | - | 0.535 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | ASIA | logit2 | 0.495 [0.45,0.54] | 0.526 [0.47,0.58] | - | 0.524 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +45 | ASIA | rf | 0.539 [0.49,0.58] | 0.526 [0.46,0.59] | - | 0.524 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | ASIA | logit2 | 0.512 [0.46,0.56] | 0.526 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | ASIA | logit2 | 0.512 [0.46,0.56] | 0.526 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | ASIA | logit2 | 0.512 [0.46,0.56] | 0.526 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | ASIA | logit2 | 0.512 [0.46,0.56] | 0.526 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | LONDON | logit2 | 0.514 [0.47,0.56] | 0.526 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | LONDON | logit2 | 0.514 [0.47,0.56] | 0.526 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | ASIA | stack | 0.554 [0.52,0.59] | 0.525 [0.47,0.58] | - | 0.511 | - | - | - | - | - | - | stack | WF-only (dead) |
| F9-13+base | pre | ASIA | stack | 0.554 [0.52,0.59] | 0.525 [0.47,0.58] | - | 0.511 | - | - | - | - | - | - | stack | WF-only (dead) |
| F9-13+base | pre | ASIA | stack | 0.554 [0.52,0.59] | 0.525 [0.47,0.58] | - | 0.511 | - | - | - | - | - | - | stack | WF-only (dead) |
| F9-13+base | pre | ASIA | stack | 0.554 [0.52,0.59] | 0.525 [0.47,0.58] | - | 0.511 | - | - | - | - | - | - | stack | WF-only (dead) |
| F5-8+base | +60 | ASIA | stack | 0.515 [0.47,0.56] | 0.524 [0.46,0.59] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | ASIA | stack | 0.515 [0.47,0.56] | 0.524 [0.46,0.59] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | LONDON | logit2 | 0.546 [0.50,0.59] | 0.524 [0.46,0.59] | - | 0.532 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | ASIA | gbt3 | 0.528 [0.49,0.57] | 0.524 [0.46,0.59] | - | 0.518 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4+base | +60 | POOLED | logit2 | 0.516 [0.49,0.54] | 0.524 [0.49,0.56] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | POOLED | rf | 0.511 [0.48,0.54] | 0.524 [0.49,0.56] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| F5-8+base | +5 | ASIA | gbt3 | 0.527 [0.48,0.57] | 0.524 [0.47,0.58] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| F5-8+base | +5 | ASIA | gbt3 | 0.527 [0.48,0.57] | 0.524 [0.47,0.58] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| F5-8+base | +5 | ASIA | gbt3 | 0.527 [0.48,0.57] | 0.524 [0.47,0.58] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| F5-8+base | +5 | ASIA | gbt3 | 0.527 [0.48,0.57] | 0.524 [0.47,0.58] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| F14-18+base | +30 | ASIA | gbt3 | 0.515 [0.47,0.56] | 0.524 [0.46,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| F14-18+base | +30 | ASIA | gbt3 | 0.515 [0.47,0.56] | 0.524 [0.46,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| F14-18+base | +20 | LONDON | gbt3 | 0.531 [0.49,0.57] | 0.524 [0.47,0.59] | - | 0.521 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | LONDON | gbt3 | 0.531 [0.49,0.57] | 0.524 [0.47,0.59] | - | 0.521 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | LONDON | gbt3 | 0.531 [0.49,0.57] | 0.524 [0.47,0.59] | - | 0.521 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | LONDON | gbt3 | 0.531 [0.49,0.57] | 0.524 [0.47,0.59] | - | 0.521 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | ASIA | stack | 0.544 [0.50,0.59] | 0.524 [0.47,0.58] | - | 0.516 | - | - | - | - | - | - |  | short by 0.136 AUC, 5 of 5 econ |
| F9-13 | +45 | ASIA | stack | 0.541 [0.50,0.59] | 0.523 [0.45,0.59] | - | 0.510 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | POOLED | rf | 0.519 [0.49,0.54] | 0.523 [0.48,0.56] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| F14-18+base | +5 | ASIA | logit2 | 0.496 [0.45,0.54] | 0.523 [0.48,0.57] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| F14-18+base | +5 | ASIA | logit2 | 0.496 [0.45,0.54] | 0.523 [0.48,0.57] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| F5-8+base | +60 | POOLED | rf | 0.514 [0.49,0.54] | 0.523 [0.49,0.56] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | POOLED | rf | 0.514 [0.49,0.54] | 0.523 [0.49,0.56] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | POOLED | rf | 0.514 [0.49,0.54] | 0.523 [0.49,0.56] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | POOLED | rf | 0.514 [0.49,0.54] | 0.523 [0.49,0.56] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | ASIA | rf | 0.522 [0.48,0.56] | 0.523 [0.47,0.58] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| F9-13+base | +5 | ASIA | rf | 0.522 [0.48,0.56] | 0.523 [0.47,0.58] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| F1-4+base | +45 | ASIA | rf | 0.512 [0.47,0.56] | 0.523 [0.46,0.59] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | POOLED | rf | 0.521 [0.50,0.55] | 0.523 [0.48,0.57] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| F5-8+base | +10 | POOLED | rf | 0.521 [0.50,0.55] | 0.523 [0.48,0.57] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| F5-8+base | +10 | POOLED | rf | 0.521 [0.50,0.55] | 0.523 [0.48,0.57] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| F5-8+base | +10 | POOLED | rf | 0.521 [0.50,0.55] | 0.523 [0.48,0.57] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| F5-8+base | +10 | POOLED | rf | 0.521 [0.50,0.55] | 0.523 [0.48,0.57] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| F5-8+base | +10 | ASIA | gbt3 | 0.526 [0.48,0.57] | 0.523 [0.46,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| F5-8+base | +10 | ASIA | gbt3 | 0.526 [0.48,0.57] | 0.523 [0.46,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| F5-8+base | +10 | ASIA | gbt3 | 0.526 [0.48,0.57] | 0.523 [0.46,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| F9-13+base | +60 | NY | logit2 | 0.486 [0.45,0.53] | 0.523 [0.46,0.59] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | NY | logit2 | 0.486 [0.45,0.53] | 0.523 [0.46,0.59] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | NY | logit2 | 0.486 [0.45,0.53] | 0.523 [0.46,0.59] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | POOLED | gbt3 | 0.517 [0.49,0.54] | 0.523 [0.49,0.56] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | POOLED | gbt3 | 0.517 [0.49,0.54] | 0.523 [0.49,0.56] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | LONDON | gbt3 | 0.519 [0.48,0.56] | 0.523 [0.46,0.59] | - | 0.524 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | LONDON | gbt3 | 0.528 [0.49,0.57] | 0.523 [0.47,0.58] | - | 0.523 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | LONDON | gbt3 | 0.483 [0.44,0.52] | 0.523 [0.46,0.60] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | ASIA | gbt3 | 0.525 [0.47,0.57] | 0.523 [0.45,0.59] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | ASIA | gbt3 | 0.524 [0.48,0.56] | 0.523 [0.46,0.58] | - | 0.515 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | ASIA | logit2 | 0.531 [0.49,0.57] | 0.522 [0.47,0.57] | - | 0.517 | - | - | - | - | - | - |  | short by 0.138 AUC, 5 of 5 econ |
| F1-4 | +15 | ASIA | logit2 | 0.531 [0.49,0.57] | 0.522 [0.47,0.57] | - | 0.517 | - | - | - | - | - | - |  | short by 0.138 AUC, 5 of 5 econ |
| F1-4 | +15 | ASIA | logit2 | 0.531 [0.49,0.57] | 0.522 [0.47,0.57] | - | 0.517 | - | - | - | - | - | - |  | short by 0.138 AUC, 5 of 5 econ |
| F1-4 | +15 | ASIA | logit2 | 0.531 [0.49,0.57] | 0.522 [0.47,0.57] | - | 0.517 | - | - | - | - | - | - |  | short by 0.138 AUC, 5 of 5 econ |
| F1-4 | +15 | ASIA | logit2 | 0.531 [0.49,0.57] | 0.522 [0.47,0.57] | - | 0.517 | - | - | - | - | - | - |  | short by 0.138 AUC, 5 of 5 econ |
| F1-4 | +15 | ASIA | logit2 | 0.531 [0.49,0.57] | 0.522 [0.47,0.57] | - | 0.517 | - | - | - | - | - | - |  | short by 0.138 AUC, 5 of 5 econ |
| F14-18+base | +60 | ASIA | stack | 0.542 [0.50,0.59] | 0.522 [0.45,0.59] | - | 0.496 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | ASIA | stack | 0.542 [0.50,0.59] | 0.522 [0.45,0.59] | - | 0.496 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | POOLED | logit2 | 0.512 [0.49,0.54] | 0.522 [0.49,0.55] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| F5-8+base | pre | NY | rf | 0.524 [0.47,0.57] | 0.522 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | NY | rf | 0.524 [0.47,0.57] | 0.522 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | NY | rf | 0.524 [0.47,0.57] | 0.522 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | NY | rf | 0.524 [0.47,0.57] | 0.522 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | NY | rf | 0.524 [0.47,0.57] | 0.522 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | LONDON | stack | 0.535 [0.49,0.57] | 0.521 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | LONDON | stack | 0.535 [0.49,0.57] | 0.521 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | LONDON | gbt3 | 0.482 [0.44,0.53] | 0.521 [0.46,0.59] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | ASIA | gbt3 | 0.521 [0.48,0.56] | 0.521 [0.47,0.58] | - | 0.513 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +15 | POOLED | gbt3 | 0.508 [0.48,0.53] | 0.521 [0.48,0.56] | - | 0.520 | - | - | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| F5-8 | +20 | NY | rf | 0.507 [0.47,0.55] | 0.521 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | NY | rf | 0.484 [0.45,0.52] | 0.521 [0.46,0.58] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | NY | rf | 0.484 [0.45,0.52] | 0.521 [0.46,0.58] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | ASIA | rf | 0.525 [0.48,0.57] | 0.521 [0.45,0.59] | - | 0.513 | - | - | - | - | - | - |  | short by 0.139 AUC, 5 of 5 econ |
| F5-8 | +5 | ASIA | rf | 0.525 [0.48,0.57] | 0.521 [0.45,0.59] | - | 0.513 | - | - | - | - | - | - |  | short by 0.139 AUC, 5 of 5 econ |
| F1-4+base | +60 | LONDON | gbt3 | 0.532 [0.48,0.58] | 0.520 [0.46,0.58] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | POOLED | gbt3 | 0.530 [0.50,0.56] | 0.520 [0.48,0.56] | - | 0.517 | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| F5-8 | +20 | POOLED | gbt3 | 0.530 [0.50,0.56] | 0.520 [0.48,0.56] | - | 0.517 | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| F5-8 | +20 | POOLED | gbt3 | 0.530 [0.50,0.56] | 0.520 [0.48,0.56] | - | 0.517 | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| F5-8 | +20 | POOLED | gbt3 | 0.530 [0.50,0.56] | 0.520 [0.48,0.56] | - | 0.517 | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| F1-4+base | +45 | NY | rf | 0.496 [0.45,0.54] | 0.520 [0.47,0.58] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | NY | rf | 0.496 [0.45,0.54] | 0.520 [0.47,0.58] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | NY | logit2 | 0.511 [0.47,0.55] | 0.520 [0.45,0.59] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | NY | logit2 | 0.511 [0.47,0.55] | 0.520 [0.45,0.59] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | NY | gbt3 | 0.502 [0.46,0.54] | 0.520 [0.45,0.59] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | ASIA | rf | 0.534 [0.49,0.58] | 0.520 [0.46,0.58] | - | 0.510 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | pre | ASIA | gbt3 | 0.538 [0.49,0.58] | 0.520 [0.46,0.58] | - | 0.515 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | pre | ASIA | gbt3 | 0.538 [0.49,0.58] | 0.520 [0.46,0.58] | - | 0.515 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +20 | ASIA | rf | 0.500 [0.46,0.54] | 0.520 [0.46,0.58] | - | 0.514 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +20 | ASIA | rf | 0.500 [0.46,0.54] | 0.520 [0.46,0.58] | - | 0.514 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8 | +10 | LONDON | gbt3 | 0.520 [0.48,0.56] | 0.520 [0.46,0.59] | - | 0.519 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | LONDON | rf | 0.517 [0.47,0.56] | 0.520 [0.46,0.58] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | POOLED | gbt3 | 0.498 [0.47,0.52] | 0.520 [0.48,0.55] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| F5-8 | +60 | POOLED | gbt3 | 0.512 [0.49,0.53] | 0.519 [0.48,0.55] | - | 0.517 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | POOLED | gbt3 | 0.512 [0.49,0.53] | 0.519 [0.48,0.55] | - | 0.517 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | POOLED | rf | 0.510 [0.48,0.54] | 0.519 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| F14-18+base | +5 | POOLED | rf | 0.510 [0.48,0.54] | 0.519 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| F14-18+base | +5 | POOLED | rf | 0.510 [0.48,0.54] | 0.519 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| F9-13+base | +20 | ASIA | logit2 | 0.499 [0.45,0.54] | 0.519 [0.46,0.58] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | pre | POOLED | logit2 | 0.506 [0.48,0.53] | 0.519 [0.49,0.55] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| F14-18+base | +20 | POOLED | logit2 | 0.508 [0.48,0.54] | 0.519 [0.49,0.55] | - | 0.520 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| F14-18+base | +20 | POOLED | logit2 | 0.508 [0.48,0.54] | 0.519 [0.49,0.55] | - | 0.520 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| F1-4 | +20 | ASIA | stack | 0.541 [0.50,0.58] | 0.519 [0.46,0.58] | - | 0.504 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +20 | ASIA | stack | 0.541 [0.50,0.58] | 0.519 [0.46,0.58] | - | 0.504 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +20 | ASIA | stack | 0.541 [0.50,0.58] | 0.519 [0.46,0.58] | - | 0.504 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +20 | ASIA | stack | 0.541 [0.50,0.58] | 0.519 [0.46,0.58] | - | 0.504 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8+base | +20 | LONDON | logit2 | 0.490 [0.45,0.53] | 0.519 [0.47,0.57] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | POOLED | logit2 | 0.497 [0.47,0.52] | 0.519 [0.48,0.55] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| F9-13 | +30 | POOLED | rf | 0.513 [0.49,0.54] | 0.519 [0.49,0.55] | - | 0.517 | - | - | - | - | - | - |  | promising: short by 0.161 AUC, 5 of 5 econ |
| F9-13+base | +5 | POOLED | logit2 | 0.507 [0.48,0.53] | 0.519 [0.48,0.56] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| F14-18+base | +30 | NY | rf | 0.495 [0.45,0.54] | 0.519 [0.46,0.58] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | NY | rf | 0.495 [0.45,0.54] | 0.519 [0.46,0.58] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | NY | rf | 0.495 [0.45,0.54] | 0.519 [0.46,0.58] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | NY | rf | 0.495 [0.45,0.54] | 0.519 [0.46,0.58] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | ASIA | logit2 | 0.519 [0.47,0.56] | 0.519 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F14-18 | +15 | ASIA | logit2 | 0.519 [0.47,0.56] | 0.519 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F14-18 | +15 | ASIA | logit2 | 0.519 [0.47,0.56] | 0.519 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F14-18 | +15 | ASIA | logit2 | 0.519 [0.47,0.56] | 0.519 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F14-18 | +15 | ASIA | logit2 | 0.519 [0.47,0.56] | 0.519 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F14-18 | +15 | ASIA | logit2 | 0.519 [0.47,0.56] | 0.519 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F14-18+base | +10 | LONDON | gbt3 | 0.507 [0.47,0.55] | 0.519 [0.46,0.58] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | NY | rf | 0.512 [0.47,0.56] | 0.519 [0.45,0.58] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | NY | rf | 0.512 [0.47,0.56] | 0.519 [0.45,0.58] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | NY | rf | 0.512 [0.47,0.56] | 0.519 [0.45,0.58] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | NY | rf | 0.512 [0.47,0.56] | 0.519 [0.45,0.58] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | NY | rf | 0.512 [0.47,0.56] | 0.519 [0.45,0.58] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | ASIA | rf | 0.512 [0.47,0.55] | 0.519 [0.45,0.59] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | ASIA | logit2 | 0.519 [0.48,0.56] | 0.519 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F9-13 | +15 | ASIA | logit2 | 0.519 [0.48,0.56] | 0.519 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F9-13 | +15 | ASIA | logit2 | 0.519 [0.48,0.56] | 0.519 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F9-13 | +15 | ASIA | logit2 | 0.519 [0.48,0.56] | 0.519 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F9-13 | +15 | ASIA | logit2 | 0.519 [0.48,0.56] | 0.519 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F9-13 | +15 | ASIA | logit2 | 0.519 [0.48,0.56] | 0.519 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - |  | short by 0.141 AUC, 5 of 5 econ |
| F1-4 | +10 | ASIA | logit2 | 0.528 [0.49,0.57] | 0.519 [0.46,0.58] | - | 0.512 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +45 | POOLED | rf | 0.521 [0.50,0.54] | 0.518 [0.49,0.55] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | POOLED | rf | 0.521 [0.50,0.54] | 0.518 [0.49,0.55] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | POOLED | rf | 0.521 [0.50,0.54] | 0.518 [0.49,0.55] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | POOLED | rf | 0.521 [0.50,0.54] | 0.518 [0.49,0.55] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | ASIA | gbt3 | 0.528 [0.48,0.58] | 0.518 [0.45,0.59] | - | 0.519 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +10 | ASIA | gbt3 | 0.528 [0.48,0.58] | 0.518 [0.45,0.59] | - | 0.519 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +10 | ASIA | gbt3 | 0.528 [0.48,0.58] | 0.518 [0.45,0.59] | - | 0.519 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | pre | ASIA | gbt3 | 0.531 [0.49,0.57] | 0.518 [0.46,0.58] | - | 0.503 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | pre | ASIA | gbt3 | 0.531 [0.49,0.57] | 0.518 [0.46,0.58] | - | 0.503 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +5 | ASIA | rf | 0.531 [0.49,0.57] | 0.518 [0.46,0.58] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.142 AUC, 5 of 5 econ |
| F5-8+base | +5 | ASIA | rf | 0.531 [0.49,0.57] | 0.518 [0.46,0.58] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.142 AUC, 5 of 5 econ |
| F5-8 | +30 | ASIA | stack | 0.544 [0.51,0.58] | 0.518 [0.45,0.58] | - | 0.498 | - | - | - | - | - | - |  | short by 0.142 AUC, 5 of 5 econ |
| F9-13+base | +10 | LONDON | rf | 0.522 [0.48,0.57] | 0.518 [0.46,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | POOLED | rf | 0.500 [0.48,0.52] | 0.518 [0.48,0.55] | - | 0.514 | - | - | - | - | - | - | stack | promising: short by 0.162 AUC, 5 of 5 econ |
| F14-18 | +10 | ASIA | rf | 0.496 [0.45,0.54] | 0.518 [0.46,0.57] | - | 0.513 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4+base | +10 | POOLED | rf | 0.517 [0.49,0.54] | 0.518 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| F1-4+base | +10 | POOLED | rf | 0.517 [0.49,0.54] | 0.518 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| F1-4+base | +10 | POOLED | rf | 0.517 [0.49,0.54] | 0.518 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| F1-4+base | +10 | POOLED | rf | 0.517 [0.49,0.54] | 0.518 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| F1-4+base | +10 | POOLED | rf | 0.517 [0.49,0.54] | 0.518 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| F14-18 | +15 | NY | gbt3 | 0.499 [0.46,0.54] | 0.517 [0.46,0.58] | - | 0.518 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | ASIA | gbt3 | 0.495 [0.45,0.54] | 0.517 [0.45,0.58] | - | 0.501 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F14-18 | +5 | ASIA | gbt3 | 0.495 [0.45,0.54] | 0.517 [0.45,0.58] | - | 0.501 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F14-18 | +5 | ASIA | gbt3 | 0.495 [0.45,0.54] | 0.517 [0.45,0.58] | - | 0.501 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F14-18 | +5 | ASIA | gbt3 | 0.495 [0.45,0.54] | 0.517 [0.45,0.58] | - | 0.501 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F1-4+base | pre | NY | logit2 | 0.521 [0.48,0.57] | 0.517 [0.46,0.58] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | NY | logit2 | 0.521 [0.48,0.57] | 0.517 [0.46,0.58] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | POOLED | rf | 0.507 [0.48,0.54] | 0.517 [0.47,0.56] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| F5-8+base | +30 | POOLED | gbt3 | 0.501 [0.48,0.53] | 0.517 [0.47,0.56] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| F9-13 | +30 | ASIA | logit2 | 0.516 [0.47,0.56] | 0.517 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F9-13 | +30 | ASIA | logit2 | 0.516 [0.47,0.56] | 0.517 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F9-13 | +30 | ASIA | logit2 | 0.516 [0.47,0.56] | 0.517 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F9-13 | +30 | ASIA | logit2 | 0.516 [0.47,0.56] | 0.517 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F9-13 | +30 | ASIA | logit2 | 0.516 [0.47,0.56] | 0.517 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - |  | short by 0.143 AUC, 5 of 5 econ |
| F5-8+base | +10 | NY | rf | 0.522 [0.48,0.57] | 0.517 [0.45,0.59] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | NY | rf | 0.522 [0.48,0.57] | 0.517 [0.45,0.59] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | NY | rf | 0.522 [0.48,0.57] | 0.517 [0.45,0.59] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | NY | rf | 0.522 [0.48,0.57] | 0.517 [0.45,0.59] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | NY | rf | 0.522 [0.48,0.57] | 0.517 [0.45,0.59] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | POOLED | logit2 | 0.512 [0.49,0.54] | 0.517 [0.48,0.55] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | LONDON | gbt3 | 0.509 [0.46,0.56] | 0.517 [0.46,0.58] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | LONDON | gbt3 | 0.509 [0.46,0.56] | 0.517 [0.46,0.58] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | LONDON | gbt3 | 0.509 [0.46,0.56] | 0.517 [0.46,0.58] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | LONDON | gbt3 | 0.509 [0.46,0.56] | 0.517 [0.46,0.58] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | POOLED | rf | 0.510 [0.48,0.53] | 0.517 [0.48,0.55] | - | 0.516 | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| F14-18 | +10 | POOLED | rf | 0.510 [0.48,0.53] | 0.517 [0.48,0.55] | - | 0.516 | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| F14-18 | +10 | POOLED | rf | 0.510 [0.48,0.53] | 0.517 [0.48,0.55] | - | 0.516 | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| F14-18 | +10 | POOLED | rf | 0.510 [0.48,0.53] | 0.517 [0.48,0.55] | - | 0.516 | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| F14-18 | +10 | POOLED | rf | 0.510 [0.48,0.53] | 0.517 [0.48,0.55] | - | 0.516 | - | - | - | - | - | - |  | short by 0.163 AUC, 5 of 5 econ |
| F1-4 | pre | ASIA | stack | 0.526 [0.49,0.56] | 0.517 [0.46,0.57] | - | 0.512 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | ASIA | stack | 0.526 [0.49,0.56] | 0.517 [0.46,0.57] | - | 0.512 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | ASIA | stack | 0.526 [0.49,0.56] | 0.517 [0.46,0.57] | - | 0.512 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | ASIA | stack | 0.526 [0.49,0.56] | 0.517 [0.46,0.57] | - | 0.512 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +60 | POOLED | rf | 0.520 [0.49,0.55] | 0.517 [0.48,0.55] | - | 0.517 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | POOLED | rf | 0.520 [0.49,0.55] | 0.517 [0.48,0.55] | - | 0.517 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | POOLED | rf | 0.520 [0.49,0.55] | 0.517 [0.48,0.55] | - | 0.517 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | POOLED | rf | 0.520 [0.49,0.55] | 0.517 [0.48,0.55] | - | 0.517 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | ASIA | stack | 0.539 [0.50,0.58] | 0.516 [0.46,0.57] | - | 0.496 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | pre | ASIA | stack | 0.539 [0.50,0.58] | 0.516 [0.46,0.57] | - | 0.496 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | pre | ASIA | stack | 0.539 [0.50,0.58] | 0.516 [0.46,0.57] | - | 0.496 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | pre | ASIA | stack | 0.539 [0.50,0.58] | 0.516 [0.46,0.57] | - | 0.496 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +30 | ASIA | logit2 | 0.530 [0.49,0.57] | 0.516 [0.46,0.58] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.144 AUC, 5 of 5 econ |
| F5-8+base | +30 | ASIA | logit2 | 0.530 [0.49,0.57] | 0.516 [0.46,0.58] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.144 AUC, 5 of 5 econ |
| F5-8+base | +30 | ASIA | logit2 | 0.530 [0.49,0.57] | 0.516 [0.46,0.58] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.144 AUC, 5 of 5 econ |
| F5-8+base | +30 | ASIA | logit2 | 0.530 [0.49,0.57] | 0.516 [0.46,0.58] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.144 AUC, 5 of 5 econ |
| F5-8+base | +30 | ASIA | logit2 | 0.530 [0.49,0.57] | 0.516 [0.46,0.58] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.144 AUC, 5 of 5 econ |
| F1-4 | +45 | ASIA | gbt3 | 0.547 [0.50,0.59] | 0.516 [0.45,0.59] | - | 0.519 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | ASIA | gbt3 | 0.547 [0.50,0.59] | 0.516 [0.45,0.59] | - | 0.519 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | NY | rf | 0.491 [0.45,0.53] | 0.516 [0.46,0.58] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | NY | rf | 0.491 [0.45,0.53] | 0.516 [0.46,0.58] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | ASIA | logit2 | 0.499 [0.45,0.54] | 0.516 [0.46,0.58] | - | 0.515 | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| F14-18 | +5 | ASIA | logit2 | 0.499 [0.45,0.54] | 0.516 [0.46,0.58] | - | 0.515 | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| F1-4+base | pre | POOLED | gbt3 | 0.512 [0.48,0.54] | 0.515 [0.48,0.56] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| F1-4+base | pre | POOLED | gbt3 | 0.512 [0.48,0.54] | 0.515 [0.48,0.56] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| F9-13 | +60 | ASIA | stack | 0.543 [0.50,0.59] | 0.515 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | ASIA | stack | 0.543 [0.50,0.59] | 0.515 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | ASIA | stack | 0.540 [0.50,0.58] | 0.515 [0.46,0.57] | - | 0.501 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | pre | ASIA | stack | 0.540 [0.50,0.58] | 0.515 [0.46,0.57] | - | 0.501 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | pre | ASIA | stack | 0.540 [0.50,0.58] | 0.515 [0.46,0.57] | - | 0.501 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | pre | ASIA | stack | 0.540 [0.50,0.58] | 0.515 [0.46,0.57] | - | 0.501 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +10 | ASIA | rf | 0.516 [0.47,0.56] | 0.515 [0.45,0.58] | - | 0.508 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18 | +20 | ASIA | rf | 0.522 [0.48,0.57] | 0.515 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +20 | ASIA | rf | 0.522 [0.48,0.57] | 0.515 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +45 | POOLED | rf | 0.509 [0.48,0.54] | 0.515 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | POOLED | rf | 0.509 [0.48,0.54] | 0.515 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | POOLED | rf | 0.509 [0.48,0.54] | 0.515 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | POOLED | rf | 0.509 [0.48,0.54] | 0.515 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | POOLED | rf | 0.511 [0.49,0.54] | 0.515 [0.48,0.55] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | POOLED | rf | 0.511 [0.49,0.54] | 0.515 [0.48,0.55] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | POOLED | rf | 0.511 [0.49,0.54] | 0.515 [0.48,0.55] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | POOLED | rf | 0.511 [0.49,0.54] | 0.515 [0.48,0.55] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | POOLED | rf | 0.506 [0.48,0.53] | 0.515 [0.48,0.55] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | POOLED | rf | 0.506 [0.48,0.53] | 0.515 [0.48,0.55] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | POOLED | rf | 0.506 [0.48,0.53] | 0.515 [0.48,0.55] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | POOLED | rf | 0.506 [0.48,0.53] | 0.515 [0.48,0.55] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | POOLED | logit2 | 0.511 [0.48,0.54] | 0.514 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +20 | POOLED | logit2 | 0.511 [0.48,0.54] | 0.514 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +20 | ASIA | logit2 | 0.507 [0.46,0.55] | 0.514 [0.45,0.58] | - | 0.514 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18+base | +20 | ASIA | logit2 | 0.501 [0.46,0.54] | 0.514 [0.47,0.57] | - | 0.508 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | pre | POOLED | logit2 | 0.509 [0.48,0.53] | 0.514 [0.48,0.54] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| F9-13+base | +20 | ASIA | rf | 0.489 [0.45,0.53] | 0.514 [0.45,0.57] | - | 0.513 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +20 | ASIA | rf | 0.489 [0.45,0.53] | 0.514 [0.45,0.57] | - | 0.513 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8 | pre | ASIA | rf | 0.514 [0.47,0.56] | 0.514 [0.45,0.57] | - | 0.514 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | ASIA | rf | 0.514 [0.47,0.56] | 0.514 [0.45,0.57] | - | 0.514 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18+base | +5 | LONDON | gbt3 | 0.497 [0.45,0.54] | 0.514 [0.45,0.58] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | POOLED | gbt3 | 0.511 [0.48,0.54] | 0.514 [0.48,0.55] | - | 0.509 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +20 | POOLED | gbt3 | 0.511 [0.48,0.54] | 0.514 [0.48,0.55] | - | 0.509 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +20 | POOLED | gbt3 | 0.511 [0.48,0.54] | 0.514 [0.48,0.55] | - | 0.509 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +20 | POOLED | gbt3 | 0.511 [0.48,0.54] | 0.514 [0.48,0.55] | - | 0.509 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +10 | POOLED | gbt3 | 0.509 [0.48,0.53] | 0.514 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| F9-13 | +45 | POOLED | rf | 0.518 [0.49,0.54] | 0.514 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | POOLED | rf | 0.518 [0.49,0.54] | 0.514 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | POOLED | rf | 0.518 [0.49,0.54] | 0.514 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | POOLED | rf | 0.518 [0.49,0.54] | 0.514 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | POOLED | gbt3 | 0.516 [0.49,0.54] | 0.513 [0.48,0.55] | - | 0.509 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +20 | POOLED | gbt3 | 0.516 [0.49,0.54] | 0.513 [0.48,0.55] | - | 0.509 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +20 | POOLED | gbt3 | 0.516 [0.49,0.54] | 0.513 [0.48,0.55] | - | 0.509 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +20 | POOLED | gbt3 | 0.516 [0.49,0.54] | 0.513 [0.48,0.55] | - | 0.509 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13 | +20 | POOLED | logit2 | 0.502 [0.48,0.53] | 0.513 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +20 | POOLED | logit2 | 0.502 [0.48,0.53] | 0.513 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18+base | +60 | ASIA | rf | 0.517 [0.47,0.56] | 0.513 [0.45,0.58] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | ASIA | rf | 0.494 [0.45,0.54] | 0.513 [0.46,0.57] | - | 0.513 | - | - | - | - | - | - |  | short by 0.147 AUC, 5 of 5 econ |
| F14-18 | +5 | ASIA | rf | 0.494 [0.45,0.54] | 0.513 [0.46,0.57] | - | 0.513 | - | - | - | - | - | - |  | short by 0.147 AUC, 5 of 5 econ |
| F14-18+base | +20 | POOLED | rf | 0.500 [0.47,0.53] | 0.513 [0.48,0.55] | - | 0.508 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +20 | POOLED | logit2 | 0.501 [0.48,0.53] | 0.513 [0.48,0.55] | - | 0.512 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +20 | POOLED | logit2 | 0.501 [0.48,0.53] | 0.513 [0.48,0.55] | - | 0.512 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +45 | ASIA | stack | 0.533 [0.49,0.57] | 0.513 [0.45,0.58] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | LONDON | logit2 | 0.483 [0.44,0.53] | 0.513 [0.46,0.57] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | NY | rf | 0.521 [0.47,0.57] | 0.513 [0.45,0.58] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | POOLED | rf | 0.524 [0.50,0.55] | 0.513 [0.47,0.56] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| F9-13+base | +10 | POOLED | rf | 0.524 [0.50,0.55] | 0.513 [0.47,0.56] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| F9-13+base | +10 | POOLED | rf | 0.524 [0.50,0.55] | 0.513 [0.47,0.56] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| F9-13+base | +10 | POOLED | rf | 0.524 [0.50,0.55] | 0.513 [0.47,0.56] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| F9-13+base | +10 | POOLED | rf | 0.524 [0.50,0.55] | 0.513 [0.47,0.56] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| F14-18+base | +30 | ASIA | logit2 | 0.535 [0.49,0.58] | 0.512 [0.45,0.58] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| F14-18+base | +30 | ASIA | logit2 | 0.535 [0.49,0.58] | 0.512 [0.45,0.58] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| F14-18+base | +30 | ASIA | logit2 | 0.535 [0.49,0.58] | 0.512 [0.45,0.58] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| F14-18+base | +30 | ASIA | logit2 | 0.535 [0.49,0.58] | 0.512 [0.45,0.58] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| F14-18+base | +30 | ASIA | logit2 | 0.535 [0.49,0.58] | 0.512 [0.45,0.58] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| F1-4+base | pre | ASIA | gbt3 | 0.529 [0.49,0.56] | 0.512 [0.46,0.57] | - | 0.498 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | pre | ASIA | gbt3 | 0.529 [0.49,0.56] | 0.512 [0.46,0.57] | - | 0.498 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +60 | NY | rf | 0.490 [0.45,0.53] | 0.512 [0.45,0.58] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | NY | rf | 0.490 [0.45,0.53] | 0.512 [0.45,0.58] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | NY | rf | 0.490 [0.45,0.53] | 0.512 [0.45,0.58] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | NY | rf | 0.490 [0.45,0.53] | 0.512 [0.45,0.58] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | NY | rf | 0.509 [0.47,0.56] | 0.512 [0.45,0.58] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | LONDON | gbt3 | 0.534 [0.49,0.58] | 0.512 [0.45,0.58] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | LONDON | gbt3 | 0.534 [0.49,0.58] | 0.512 [0.45,0.58] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | LONDON | gbt3 | 0.534 [0.49,0.58] | 0.512 [0.45,0.58] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | LONDON | gbt3 | 0.534 [0.49,0.58] | 0.512 [0.45,0.58] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | LONDON | gbt3 | 0.485 [0.45,0.52] | 0.512 [0.46,0.57] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | NY | gbt3 | 0.478 [0.43,0.52] | 0.512 [0.45,0.58] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | POOLED | gbt3 | 0.508 [0.48,0.53] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | POOLED | gbt3 | 0.508 [0.48,0.53] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | NY | gbt3 | 0.505 [0.46,0.55] | 0.512 [0.45,0.58] | - | 0.509 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | NY | gbt3 | 0.505 [0.46,0.55] | 0.512 [0.45,0.58] | - | 0.509 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | POOLED | rf | 0.507 [0.48,0.53] | 0.512 [0.47,0.55] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | POOLED | rf | 0.507 [0.48,0.53] | 0.512 [0.47,0.55] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | POOLED | rf | 0.507 [0.48,0.53] | 0.512 [0.47,0.55] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | POOLED | rf | 0.507 [0.48,0.53] | 0.512 [0.47,0.55] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | POOLED | rf | 0.492 [0.47,0.52] | 0.512 [0.48,0.54] | - | 0.506 | - | - | - | - | - | - | stack | promising: short by 0.168 AUC, 5 of 5 econ |
| F5-8+base | +45 | LONDON | gbt3 | 0.502 [0.46,0.55] | 0.512 [0.45,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | LONDON | gbt3 | 0.502 [0.46,0.55] | 0.512 [0.45,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | ASIA | gbt3 | 0.513 [0.47,0.56] | 0.511 [0.45,0.57] | - | 0.508 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | POOLED | rf | 0.508 [0.48,0.53] | 0.511 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | POOLED | rf | 0.508 [0.48,0.53] | 0.511 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | POOLED | rf | 0.508 [0.48,0.53] | 0.511 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | POOLED | rf | 0.508 [0.48,0.53] | 0.511 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | ASIA | logit2 | 0.508 [0.46,0.55] | 0.511 [0.45,0.57] | - | 0.510 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +60 | NY | gbt3 | 0.481 [0.44,0.52] | 0.511 [0.45,0.58] | - | 0.508 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | NY | gbt3 | 0.504 [0.46,0.55] | 0.511 [0.45,0.57] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | NY | gbt3 | 0.504 [0.46,0.55] | 0.511 [0.45,0.57] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | NY | logit2 | 0.490 [0.45,0.53] | 0.511 [0.45,0.57] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | NY | logit2 | 0.490 [0.45,0.53] | 0.511 [0.45,0.57] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | NY | logit2 | 0.490 [0.45,0.53] | 0.511 [0.45,0.57] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | NY | rf | 0.491 [0.46,0.53] | 0.511 [0.45,0.56] | - | 0.502 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | NY | rf | 0.491 [0.46,0.53] | 0.511 [0.45,0.56] | - | 0.502 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | POOLED | gbt3 | 0.498 [0.47,0.52] | 0.510 [0.47,0.55] | - | 0.507 | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| F5-8+base | pre | POOLED | rf | 0.514 [0.49,0.54] | 0.510 [0.47,0.55] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| F5-8+base | pre | POOLED | rf | 0.514 [0.49,0.54] | 0.510 [0.47,0.55] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| F5-8+base | pre | POOLED | rf | 0.514 [0.49,0.54] | 0.510 [0.47,0.55] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| F5-8+base | pre | POOLED | rf | 0.514 [0.49,0.54] | 0.510 [0.47,0.55] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| F5-8+base | pre | POOLED | rf | 0.514 [0.49,0.54] | 0.510 [0.47,0.55] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| F14-18 | +30 | ASIA | logit2 | 0.497 [0.45,0.54] | 0.510 [0.45,0.57] | - | 0.501 | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| F14-18 | +30 | ASIA | logit2 | 0.497 [0.45,0.54] | 0.510 [0.45,0.57] | - | 0.501 | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| F14-18 | +30 | ASIA | logit2 | 0.497 [0.45,0.54] | 0.510 [0.45,0.57] | - | 0.501 | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| F14-18 | +30 | ASIA | logit2 | 0.497 [0.45,0.54] | 0.510 [0.45,0.57] | - | 0.501 | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| F14-18 | +30 | ASIA | logit2 | 0.497 [0.45,0.54] | 0.510 [0.45,0.57] | - | 0.501 | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| F14-18+base | +20 | ASIA | gbt3 | 0.502 [0.46,0.54] | 0.510 [0.46,0.57] | - | 0.501 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +30 | POOLED | gbt3 | 0.493 [0.47,0.52] | 0.510 [0.48,0.55] | - | 0.505 | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| F1-4+base | +45 | LONDON | gbt3 | 0.505 [0.46,0.55] | 0.510 [0.45,0.57] | - | 0.505 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | LONDON | gbt3 | 0.505 [0.46,0.55] | 0.510 [0.45,0.57] | - | 0.505 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | NY | logit2 | 0.512 [0.47,0.56] | 0.509 [0.44,0.58] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | NY | logit2 | 0.512 [0.47,0.56] | 0.509 [0.44,0.58] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | NY | logit2 | 0.512 [0.47,0.56] | 0.509 [0.44,0.58] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | NY | logit2 | 0.512 [0.47,0.56] | 0.509 [0.44,0.58] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | NY | logit2 | 0.512 [0.47,0.56] | 0.509 [0.44,0.58] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | POOLED | rf | 0.501 [0.48,0.53] | 0.509 [0.48,0.54] | - | 0.505 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13 | +60 | NY | logit2 | 0.476 [0.43,0.52] | 0.509 [0.45,0.58] | - | 0.504 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | NY | logit2 | 0.476 [0.43,0.52] | 0.509 [0.45,0.58] | - | 0.504 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | NY | logit2 | 0.476 [0.43,0.52] | 0.509 [0.45,0.58] | - | 0.504 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | POOLED | rf | 0.519 [0.49,0.55] | 0.509 [0.48,0.54] | - | 0.508 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +20 | POOLED | rf | 0.521 [0.50,0.55] | 0.509 [0.47,0.54] | - | 0.509 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4+base | +5 | NY | gbt3 | 0.528 [0.49,0.57] | 0.509 [0.45,0.56] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | NY | gbt3 | 0.528 [0.49,0.57] | 0.509 [0.45,0.56] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | NY | gbt3 | 0.528 [0.49,0.57] | 0.509 [0.45,0.56] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | NY | gbt3 | 0.528 [0.49,0.57] | 0.509 [0.45,0.56] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | ASIA | rf | 0.522 [0.48,0.57] | 0.509 [0.45,0.57] | - | 0.499 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | pre | ASIA | rf | 0.522 [0.48,0.57] | 0.509 [0.45,0.57] | - | 0.499 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +5 | ASIA | logit2 | 0.500 [0.46,0.55] | 0.509 [0.45,0.57] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| F9-13+base | +5 | ASIA | logit2 | 0.500 [0.46,0.55] | 0.509 [0.45,0.57] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| F5-8 | +20 | POOLED | stack | 0.505 [0.48,0.53] | 0.508 [0.46,0.55] | - | 0.505 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +45 | NY | rf | 0.498 [0.45,0.54] | 0.508 [0.45,0.58] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | NY | rf | 0.498 [0.45,0.54] | 0.508 [0.45,0.58] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | LONDON | logit2 | 0.494 [0.45,0.54] | 0.508 [0.45,0.56] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | POOLED | gbt3 | 0.517 [0.49,0.54] | 0.508 [0.47,0.54] | - | 0.507 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +20 | POOLED | gbt3 | 0.517 [0.49,0.54] | 0.508 [0.47,0.54] | - | 0.507 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +20 | POOLED | gbt3 | 0.517 [0.49,0.54] | 0.508 [0.47,0.54] | - | 0.507 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +20 | POOLED | gbt3 | 0.517 [0.49,0.54] | 0.508 [0.47,0.54] | - | 0.507 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +15 | POOLED | rf | 0.508 [0.48,0.54] | 0.508 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| F14-18+base | +5 | ASIA | gbt3 | 0.535 [0.49,0.58] | 0.508 [0.45,0.56] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| F14-18+base | +5 | ASIA | gbt3 | 0.535 [0.49,0.58] | 0.508 [0.45,0.56] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| F14-18+base | +5 | ASIA | gbt3 | 0.535 [0.49,0.58] | 0.508 [0.45,0.56] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| F14-18+base | +5 | ASIA | gbt3 | 0.535 [0.49,0.58] | 0.508 [0.45,0.56] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| F1-4+base | +20 | NY | logit2 | 0.521 [0.48,0.56] | 0.508 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | NY | logit2 | 0.521 [0.48,0.56] | 0.508 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | NY | logit2 | 0.521 [0.48,0.56] | 0.508 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | NY | logit2 | 0.521 [0.48,0.56] | 0.508 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | NY | logit2 | 0.521 [0.48,0.56] | 0.508 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | ASIA | rf | 0.523 [0.48,0.57] | 0.508 [0.45,0.57] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| F1-4+base | +5 | ASIA | rf | 0.523 [0.48,0.57] | 0.508 [0.45,0.57] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| F9-13+base | +30 | LONDON | stack | 0.521 [0.48,0.57] | 0.508 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | LONDON | stack | 0.521 [0.48,0.57] | 0.508 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | LONDON | stack | 0.521 [0.48,0.57] | 0.508 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | LONDON | stack | 0.521 [0.48,0.57] | 0.508 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | LONDON | stack | 0.521 [0.48,0.57] | 0.508 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | LONDON | stack | 0.521 [0.48,0.57] | 0.508 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | POOLED | gbt3 | 0.506 [0.48,0.53] | 0.508 [0.47,0.55] | - | 0.506 | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| F5-8 | +15 | POOLED | stack | 0.519 [0.49,0.55] | 0.508 [0.47,0.54] | - | 0.505 | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| F5-8 | +15 | POOLED | stack | 0.519 [0.49,0.55] | 0.508 [0.47,0.54] | - | 0.505 | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| F5-8 | +15 | POOLED | stack | 0.519 [0.49,0.55] | 0.508 [0.47,0.54] | - | 0.505 | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| F5-8 | +15 | POOLED | stack | 0.519 [0.49,0.55] | 0.508 [0.47,0.54] | - | 0.505 | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| F5-8 | +15 | POOLED | stack | 0.519 [0.49,0.55] | 0.508 [0.47,0.54] | - | 0.505 | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| F9-13+base | pre | NY | rf | 0.522 [0.48,0.56] | 0.508 [0.45,0.57] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | NY | rf | 0.522 [0.48,0.56] | 0.508 [0.45,0.57] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | NY | rf | 0.522 [0.48,0.56] | 0.508 [0.45,0.57] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | NY | rf | 0.522 [0.48,0.56] | 0.508 [0.45,0.57] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | NY | rf | 0.522 [0.48,0.56] | 0.508 [0.45,0.57] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | LONDON | rf | 0.504 [0.46,0.55] | 0.507 [0.45,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | LONDON | rf | 0.504 [0.46,0.55] | 0.507 [0.45,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | LONDON | rf | 0.504 [0.46,0.55] | 0.507 [0.45,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | LONDON | gbt3 | 0.492 [0.45,0.53] | 0.507 [0.45,0.56] | - | 0.508 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | POOLED | rf | 0.506 [0.48,0.53] | 0.507 [0.47,0.55] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | POOLED | rf | 0.506 [0.48,0.53] | 0.507 [0.47,0.55] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | POOLED | rf | 0.506 [0.48,0.53] | 0.507 [0.47,0.55] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | POOLED | rf | 0.506 [0.48,0.53] | 0.507 [0.47,0.55] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | POOLED | gbt3 | 0.505 [0.48,0.53] | 0.507 [0.47,0.54] | - | 0.505 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +20 | POOLED | gbt3 | 0.505 [0.48,0.53] | 0.507 [0.47,0.54] | - | 0.505 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +20 | POOLED | gbt3 | 0.505 [0.48,0.53] | 0.507 [0.47,0.54] | - | 0.505 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +20 | POOLED | gbt3 | 0.505 [0.48,0.53] | 0.507 [0.47,0.54] | - | 0.505 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8+base | +45 | POOLED | gbt3 | 0.498 [0.47,0.53] | 0.507 [0.47,0.55] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | POOLED | gbt3 | 0.498 [0.47,0.53] | 0.507 [0.47,0.55] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | ASIA | rf | 0.491 [0.45,0.53] | 0.507 [0.45,0.56] | - | 0.497 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +20 | ASIA | rf | 0.491 [0.45,0.53] | 0.507 [0.45,0.56] | - | 0.497 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +20 | ASIA | rf | 0.482 [0.44,0.53] | 0.507 [0.45,0.56] | - | 0.495 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +20 | ASIA | rf | 0.482 [0.44,0.53] | 0.507 [0.45,0.56] | - | 0.495 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +20 | POOLED | logit2 | 0.502 [0.47,0.53] | 0.507 [0.48,0.54] | - | 0.504 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +20 | POOLED | logit2 | 0.502 [0.47,0.53] | 0.507 [0.48,0.54] | - | 0.504 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | pre | LONDON | gbt3 | 0.482 [0.44,0.53] | 0.506 [0.44,0.57] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | POOLED | gbt3 | 0.526 [0.50,0.55] | 0.506 [0.46,0.55] | - | 0.503 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +20 | POOLED | gbt3 | 0.526 [0.50,0.55] | 0.506 [0.46,0.55] | - | 0.503 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +20 | POOLED | gbt3 | 0.526 [0.50,0.55] | 0.506 [0.46,0.55] | - | 0.503 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +20 | POOLED | gbt3 | 0.526 [0.50,0.55] | 0.506 [0.46,0.55] | - | 0.503 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8+base | +10 | LONDON | rf | 0.505 [0.47,0.55] | 0.506 [0.45,0.57] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | POOLED | rf | 0.511 [0.48,0.54] | 0.506 [0.47,0.54] | - | 0.502 | - | - | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| F14-18+base | +20 | NY | gbt3 | 0.513 [0.47,0.55] | 0.506 [0.45,0.57] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | NY | gbt3 | 0.513 [0.47,0.55] | 0.506 [0.45,0.57] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | ASIA | gbt3 | 0.520 [0.48,0.56] | 0.506 [0.44,0.57] | - | 0.494 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +10 | ASIA | gbt3 | 0.520 [0.48,0.56] | 0.506 [0.44,0.57] | - | 0.494 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +10 | ASIA | gbt3 | 0.520 [0.48,0.56] | 0.506 [0.44,0.57] | - | 0.494 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +45 | NY | rf | 0.490 [0.45,0.53] | 0.506 [0.44,0.58] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | NY | rf | 0.490 [0.45,0.53] | 0.506 [0.44,0.58] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | NY | rf | 0.498 [0.46,0.54] | 0.506 [0.44,0.57] | - | 0.504 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | LONDON | gbt3 | 0.529 [0.49,0.57] | 0.506 [0.45,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | LONDON | gbt3 | 0.529 [0.49,0.57] | 0.506 [0.45,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | LONDON | gbt3 | 0.529 [0.49,0.57] | 0.506 [0.45,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | LONDON | gbt3 | 0.529 [0.49,0.57] | 0.506 [0.45,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | POOLED | gbt3 | 0.509 [0.48,0.54] | 0.506 [0.47,0.54] | - | 0.501 | - | - | - | - | - | - | stack | short by 0.174 AUC, 5 of 5 econ |
| F9-13+base | pre | POOLED | rf | 0.517 [0.49,0.54] | 0.505 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F9-13+base | pre | POOLED | rf | 0.517 [0.49,0.54] | 0.505 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F9-13+base | pre | POOLED | rf | 0.517 [0.49,0.54] | 0.505 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F9-13+base | pre | POOLED | rf | 0.517 [0.49,0.54] | 0.505 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F9-13+base | pre | POOLED | rf | 0.517 [0.49,0.54] | 0.505 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F1-4+base | +45 | POOLED | gbt3 | 0.493 [0.47,0.52] | 0.505 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | POOLED | gbt3 | 0.493 [0.47,0.52] | 0.505 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | ASIA | gbt3 | 0.506 [0.46,0.55] | 0.505 [0.44,0.57] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | ASIA | gbt3 | 0.506 [0.46,0.55] | 0.505 [0.44,0.57] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | ASIA | rf | 0.525 [0.48,0.57] | 0.505 [0.45,0.57] | - | 0.492 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| F14-18+base | +5 | ASIA | rf | 0.525 [0.48,0.57] | 0.505 [0.45,0.57] | - | 0.492 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| F14-18 | +20 | NY | gbt3 | 0.488 [0.45,0.53] | 0.505 [0.44,0.57] | - | 0.508 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | NY | gbt3 | 0.488 [0.45,0.53] | 0.505 [0.44,0.57] | - | 0.508 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | POOLED | gbt3 | 0.503 [0.48,0.53] | 0.505 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F5-8+base | +5 | POOLED | gbt3 | 0.503 [0.48,0.53] | 0.505 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F5-8+base | +10 | NY | logit2 | 0.505 [0.46,0.55] | 0.505 [0.44,0.58] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | POOLED | rf | 0.509 [0.48,0.54] | 0.505 [0.47,0.55] | - | 0.505 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F14-18+base | +10 | POOLED | rf | 0.509 [0.48,0.54] | 0.505 [0.47,0.55] | - | 0.505 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F14-18+base | +10 | POOLED | rf | 0.509 [0.48,0.54] | 0.505 [0.47,0.55] | - | 0.505 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F14-18+base | +10 | POOLED | rf | 0.509 [0.48,0.54] | 0.505 [0.47,0.55] | - | 0.505 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F14-18+base | +10 | POOLED | rf | 0.509 [0.48,0.54] | 0.505 [0.47,0.55] | - | 0.505 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F5-8 | +15 | POOLED | rf | 0.509 [0.49,0.53] | 0.505 [0.47,0.54] | - | 0.503 | - | - | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| F1-4+base | +5 | POOLED | gbt3 | 0.505 [0.48,0.53] | 0.505 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F1-4+base | +5 | POOLED | gbt3 | 0.505 [0.48,0.53] | 0.505 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| F1-4 | +15 | POOLED | logit2 | 0.511 [0.48,0.54] | 0.505 [0.47,0.54] | - | 0.502 | - | - | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| F14-18+base | pre | NY | rf | 0.511 [0.46,0.56] | 0.505 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | NY | rf | 0.511 [0.46,0.56] | 0.505 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | NY | rf | 0.511 [0.46,0.56] | 0.505 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | NY | rf | 0.511 [0.46,0.56] | 0.505 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | NY | rf | 0.511 [0.46,0.56] | 0.505 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | ASIA | stack | 0.536 [0.50,0.57] | 0.505 [0.45,0.57] | - | 0.498 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +20 | ASIA | stack | 0.536 [0.50,0.57] | 0.505 [0.45,0.57] | - | 0.498 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +20 | ASIA | stack | 0.536 [0.50,0.57] | 0.505 [0.45,0.57] | - | 0.498 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +20 | ASIA | stack | 0.536 [0.50,0.57] | 0.505 [0.45,0.57] | - | 0.498 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | pre | ASIA | stack | 0.539 [0.50,0.58] | 0.504 [0.44,0.56] | - | 0.491 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | pre | ASIA | stack | 0.539 [0.50,0.58] | 0.504 [0.44,0.56] | - | 0.491 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | pre | ASIA | stack | 0.539 [0.50,0.58] | 0.504 [0.44,0.56] | - | 0.491 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | pre | ASIA | stack | 0.539 [0.50,0.58] | 0.504 [0.44,0.56] | - | 0.491 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +15 | NY | logit2 | 0.487 [0.44,0.53] | 0.504 [0.44,0.57] | - | 0.498 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | NY | logit2 | 0.487 [0.44,0.53] | 0.504 [0.44,0.57] | - | 0.498 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | NY | logit2 | 0.487 [0.44,0.53] | 0.504 [0.44,0.57] | - | 0.498 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | NY | logit2 | 0.487 [0.44,0.53] | 0.504 [0.44,0.57] | - | 0.498 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | NY | logit2 | 0.487 [0.44,0.53] | 0.504 [0.44,0.57] | - | 0.498 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | POOLED | logit2 | 0.506 [0.48,0.53] | 0.504 [0.47,0.54] | - | 0.501 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +20 | POOLED | logit2 | 0.506 [0.48,0.53] | 0.504 [0.47,0.54] | - | 0.501 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18+base | +60 | POOLED | rf | 0.508 [0.48,0.53] | 0.504 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | POOLED | rf | 0.508 [0.48,0.53] | 0.504 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | POOLED | rf | 0.508 [0.48,0.53] | 0.504 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | POOLED | rf | 0.508 [0.48,0.53] | 0.504 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | ASIA | gbt3 | 0.523 [0.48,0.56] | 0.504 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | ASIA | gbt3 | 0.523 [0.48,0.56] | 0.504 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +15 | NY | rf | 0.508 [0.46,0.56] | 0.504 [0.43,0.57] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | POOLED | rf | 0.494 [0.47,0.52] | 0.504 [0.47,0.54] | - | 0.501 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18 | +45 | NY | rf | 0.485 [0.44,0.53] | 0.504 [0.45,0.56] | - | 0.502 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | NY | rf | 0.485 [0.44,0.53] | 0.504 [0.45,0.56] | - | 0.502 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | NY | gbt3 | 0.485 [0.44,0.53] | 0.504 [0.44,0.57] | - | 0.513 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | NY | gbt3 | 0.485 [0.44,0.53] | 0.504 [0.44,0.57] | - | 0.513 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | NY | gbt3 | 0.485 [0.44,0.53] | 0.504 [0.44,0.57] | - | 0.513 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | ASIA | stack | 0.542 [0.50,0.58] | 0.504 [0.44,0.56] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +10 | ASIA | stack | 0.542 [0.50,0.58] | 0.504 [0.44,0.56] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +10 | ASIA | stack | 0.542 [0.50,0.58] | 0.504 [0.44,0.56] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4+base | +20 | ASIA | logit2 | 0.512 [0.47,0.56] | 0.504 [0.45,0.56] | - | 0.500 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | pre | NY | gbt3 | 0.518 [0.48,0.56] | 0.503 [0.45,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | NY | rf | 0.502 [0.46,0.55] | 0.503 [0.44,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | NY | rf | 0.502 [0.46,0.55] | 0.503 [0.44,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | NY | rf | 0.502 [0.46,0.55] | 0.503 [0.44,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | NY | rf | 0.502 [0.46,0.55] | 0.503 [0.44,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | NY | rf | 0.518 [0.48,0.56] | 0.503 [0.44,0.56] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | NY | rf | 0.518 [0.48,0.56] | 0.503 [0.44,0.56] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | NY | rf | 0.518 [0.48,0.56] | 0.503 [0.44,0.56] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | NY | rf | 0.518 [0.48,0.56] | 0.503 [0.44,0.56] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | NY | rf | 0.518 [0.48,0.56] | 0.503 [0.44,0.56] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | NY | gbt3 | 0.481 [0.44,0.53] | 0.503 [0.44,0.57] | - | 0.508 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | POOLED | rf | 0.502 [0.48,0.53] | 0.503 [0.47,0.54] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | POOLED | rf | 0.502 [0.48,0.53] | 0.503 [0.47,0.54] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | POOLED | rf | 0.502 [0.48,0.53] | 0.503 [0.47,0.54] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | POOLED | rf | 0.502 [0.48,0.53] | 0.503 [0.47,0.54] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | LONDON | rf | 0.511 [0.46,0.56] | 0.503 [0.44,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | LONDON | rf | 0.511 [0.46,0.56] | 0.503 [0.44,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | LONDON | rf | 0.511 [0.46,0.56] | 0.503 [0.44,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | LONDON | gbt3 | 0.530 [0.49,0.58] | 0.503 [0.44,0.57] | - | 0.506 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | POOLED | rf | 0.489 [0.47,0.51] | 0.503 [0.47,0.54] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| F5-8 | +60 | ASIA | logit2 | 0.510 [0.46,0.56] | 0.503 [0.44,0.56] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | ASIA | logit2 | 0.525 [0.48,0.57] | 0.503 [0.43,0.58] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | ASIA | logit2 | 0.510 [0.46,0.56] | 0.503 [0.44,0.56] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | ASIA | logit2 | 0.525 [0.48,0.57] | 0.503 [0.43,0.58] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | ASIA | logit2 | 0.510 [0.46,0.56] | 0.503 [0.44,0.56] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | ASIA | logit2 | 0.525 [0.48,0.57] | 0.503 [0.43,0.58] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | ASIA | logit2 | 0.510 [0.46,0.56] | 0.503 [0.44,0.56] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | ASIA | logit2 | 0.525 [0.48,0.57] | 0.503 [0.43,0.58] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | ASIA | stack | 0.515 [0.48,0.55] | 0.503 [0.45,0.56] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | NY | rf | 0.504 [0.46,0.55] | 0.503 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | NY | rf | 0.504 [0.46,0.55] | 0.503 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | LONDON | gbt3 | 0.523 [0.48,0.57] | 0.503 [0.45,0.57] | - | 0.511 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | NY | logit2 | 0.460 [0.42,0.50] | 0.502 [0.44,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | NY | logit2 | 0.460 [0.42,0.50] | 0.502 [0.44,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | NY | logit2 | 0.460 [0.42,0.50] | 0.502 [0.44,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | NY | logit2 | 0.460 [0.42,0.50] | 0.502 [0.44,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | NY | logit2 | 0.460 [0.42,0.50] | 0.502 [0.44,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | POOLED | stack | 0.511 [0.48,0.54] | 0.502 [0.46,0.54] | - | 0.504 | - | - | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| F1-4 | +15 | POOLED | stack | 0.511 [0.48,0.54] | 0.502 [0.46,0.54] | - | 0.504 | - | - | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| F1-4 | +15 | POOLED | stack | 0.511 [0.48,0.54] | 0.502 [0.46,0.54] | - | 0.504 | - | - | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| F1-4 | +15 | POOLED | stack | 0.511 [0.48,0.54] | 0.502 [0.46,0.54] | - | 0.504 | - | - | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| F1-4 | +15 | POOLED | stack | 0.511 [0.48,0.54] | 0.502 [0.46,0.54] | - | 0.504 | - | - | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| F1-4 | +10 | ASIA | stack | 0.529 [0.49,0.57] | 0.502 [0.44,0.57] | - | 0.496 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | ASIA | stack | 0.529 [0.49,0.57] | 0.502 [0.44,0.57] | - | 0.496 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | ASIA | stack | 0.529 [0.49,0.57] | 0.502 [0.44,0.57] | - | 0.496 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4+base | +60 | ASIA | stack | 0.537 [0.49,0.58] | 0.502 [0.44,0.57] | - | 0.488 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | ASIA | stack | 0.537 [0.49,0.58] | 0.502 [0.44,0.57] | - | 0.488 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | LONDON | rf | 0.516 [0.47,0.56] | 0.502 [0.44,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | NY | gbt3 | 0.509 [0.47,0.56] | 0.502 [0.44,0.56] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | NY | gbt3 | 0.489 [0.45,0.53] | 0.502 [0.44,0.56] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | LONDON | gbt3 | 0.484 [0.44,0.53] | 0.502 [0.44,0.57] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | POOLED | gbt3 | 0.507 [0.48,0.53] | 0.501 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.179 AUC, 5 of 5 econ |
| F14-18+base | +5 | POOLED | gbt3 | 0.507 [0.48,0.53] | 0.501 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.179 AUC, 5 of 5 econ |
| F9-13 | +60 | POOLED | gbt3 | 0.508 [0.48,0.53] | 0.501 [0.46,0.54] | - | 0.502 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | POOLED | gbt3 | 0.508 [0.48,0.53] | 0.501 [0.46,0.54] | - | 0.502 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | NY | rf | 0.474 [0.43,0.52] | 0.501 [0.43,0.57] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | NY | rf | 0.474 [0.43,0.52] | 0.501 [0.43,0.57] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | NY | rf | 0.474 [0.43,0.52] | 0.501 [0.43,0.57] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | NY | rf | 0.474 [0.43,0.52] | 0.501 [0.43,0.57] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | NY | logit2 | 0.504 [0.46,0.55] | 0.501 [0.43,0.57] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | NY | logit2 | 0.504 [0.46,0.55] | 0.501 [0.43,0.57] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | NY | logit2 | 0.504 [0.46,0.55] | 0.501 [0.43,0.57] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | NY | logit2 | 0.504 [0.46,0.55] | 0.501 [0.43,0.57] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | NY | logit2 | 0.504 [0.46,0.55] | 0.501 [0.43,0.57] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | LONDON | logit2 | 0.493 [0.45,0.54] | 0.501 [0.44,0.57] | - | 0.507 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | LONDON | logit2 | 0.484 [0.44,0.53] | 0.501 [0.45,0.55] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | POOLED | logit2 | 0.501 [0.48,0.53] | 0.501 [0.47,0.54] | - | 0.500 | - | - | - | - | - | - |  | short by 0.179 AUC, 5 of 5 econ |
| F1-4 | +60 | POOLED | rf | 0.518 [0.49,0.55] | 0.501 [0.46,0.54] | - | 0.499 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | POOLED | rf | 0.518 [0.49,0.55] | 0.501 [0.46,0.54] | - | 0.499 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | POOLED | rf | 0.518 [0.49,0.55] | 0.501 [0.46,0.54] | - | 0.499 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | POOLED | rf | 0.518 [0.49,0.55] | 0.501 [0.46,0.54] | - | 0.499 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | ASIA | stack | 0.534 [0.50,0.57] | 0.501 [0.43,0.57] | - | 0.488 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +10 | ASIA | stack | 0.534 [0.50,0.57] | 0.501 [0.43,0.57] | - | 0.488 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +10 | ASIA | stack | 0.534 [0.50,0.57] | 0.501 [0.43,0.57] | - | 0.488 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +10 | ASIA | stack | 0.531 [0.49,0.57] | 0.500 [0.43,0.57] | - | 0.492 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +10 | ASIA | stack | 0.531 [0.49,0.57] | 0.500 [0.43,0.57] | - | 0.492 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +10 | ASIA | stack | 0.531 [0.49,0.57] | 0.500 [0.43,0.57] | - | 0.492 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | pre | POOLED | rf | 0.511 [0.48,0.54] | 0.500 [0.46,0.54] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F14-18+base | pre | POOLED | rf | 0.511 [0.48,0.54] | 0.500 [0.46,0.54] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F14-18+base | pre | POOLED | rf | 0.511 [0.48,0.54] | 0.500 [0.46,0.54] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F14-18+base | pre | POOLED | rf | 0.511 [0.48,0.54] | 0.500 [0.46,0.54] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F14-18+base | pre | POOLED | rf | 0.511 [0.48,0.54] | 0.500 [0.46,0.54] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F1-4+base | +20 | NY | rf | 0.498 [0.46,0.54] | 0.500 [0.45,0.55] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | NY | logit2 | 0.515 [0.47,0.56] | 0.500 [0.44,0.56] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | NY | logit2 | 0.515 [0.47,0.56] | 0.500 [0.44,0.56] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | NY | logit2 | 0.515 [0.47,0.56] | 0.500 [0.44,0.56] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | NY | logit2 | 0.515 [0.47,0.56] | 0.500 [0.44,0.56] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | NY | logit2 | 0.515 [0.47,0.56] | 0.500 [0.44,0.56] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | POOLED | rf | 0.504 [0.48,0.53] | 0.500 [0.46,0.54] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F1-4+base | +5 | POOLED | rf | 0.504 [0.48,0.53] | 0.500 [0.46,0.54] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F1-4+base | +5 | POOLED | rf | 0.504 [0.48,0.53] | 0.500 [0.46,0.54] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F9-13 | +20 | NY | gbt3 | 0.488 [0.45,0.53] | 0.500 [0.44,0.56] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | NY | gbt3 | 0.488 [0.45,0.53] | 0.500 [0.44,0.56] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | LONDON | gbt3 | 0.475 [0.43,0.52] | 0.500 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | POOLED | gbt3 | 0.499 [0.48,0.52] | 0.500 [0.47,0.53] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F1-4+base | pre | POOLED | rf | 0.513 [0.49,0.54] | 0.500 [0.47,0.53] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F1-4+base | pre | POOLED | rf | 0.513 [0.49,0.54] | 0.500 [0.47,0.53] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F1-4+base | pre | POOLED | rf | 0.513 [0.49,0.54] | 0.500 [0.47,0.53] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F1-4+base | pre | POOLED | rf | 0.513 [0.49,0.54] | 0.500 [0.47,0.53] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F1-4+base | pre | POOLED | rf | 0.513 [0.49,0.54] | 0.500 [0.47,0.53] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| F1-4 | +15 | POOLED | gbt3 | 0.498 [0.47,0.53] | 0.500 [0.46,0.54] | - | 0.495 | - | - | - | - | - | - |  | short by 0.180 AUC, 5 of 5 econ |
| F9-13 | +60 | LONDON | logit2 | 0.541 [0.50,0.59] | 0.500 [0.44,0.56] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | LONDON | logit2 | 0.541 [0.50,0.59] | 0.500 [0.44,0.56] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | ASIA | gbt3 | 0.515 [0.48,0.56] | 0.500 [0.44,0.56] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | pre | ASIA | gbt3 | 0.515 [0.48,0.56] | 0.500 [0.44,0.56] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +30 | NY | rf | 0.490 [0.45,0.53] | 0.499 [0.44,0.56] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | NY | rf | 0.490 [0.45,0.53] | 0.499 [0.44,0.56] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | NY | rf | 0.490 [0.45,0.53] | 0.499 [0.44,0.56] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | NY | rf | 0.490 [0.45,0.53] | 0.499 [0.44,0.56] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | NY | gbt3 | 0.496 [0.46,0.53] | 0.499 [0.44,0.55] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | NY | gbt3 | 0.496 [0.46,0.53] | 0.499 [0.44,0.55] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | NY | gbt3 | 0.496 [0.46,0.53] | 0.499 [0.44,0.55] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | NY | gbt3 | 0.496 [0.46,0.53] | 0.499 [0.44,0.55] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | NY | rf | 0.521 [0.48,0.57] | 0.499 [0.43,0.58] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | NY | rf | 0.521 [0.48,0.57] | 0.499 [0.43,0.58] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | NY | rf | 0.521 [0.48,0.57] | 0.499 [0.43,0.58] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | NY | rf | 0.521 [0.48,0.57] | 0.499 [0.43,0.58] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | NY | rf | 0.521 [0.48,0.57] | 0.499 [0.43,0.58] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | POOLED | gbt3 | 0.501 [0.47,0.53] | 0.499 [0.46,0.54] | - | 0.497 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | POOLED | gbt3 | 0.501 [0.47,0.53] | 0.499 [0.46,0.54] | - | 0.497 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | LONDON | rf | 0.530 [0.49,0.58] | 0.499 [0.43,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | LONDON | rf | 0.530 [0.49,0.58] | 0.499 [0.43,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | LONDON | rf | 0.530 [0.49,0.58] | 0.499 [0.43,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | LONDON | rf | 0.530 [0.49,0.58] | 0.499 [0.43,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | NY | gbt3 | 0.508 [0.46,0.55] | 0.499 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | POOLED | gbt3 | 0.499 [0.47,0.53] | 0.499 [0.47,0.53] | - | 0.496 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +20 | POOLED | gbt3 | 0.499 [0.47,0.53] | 0.499 [0.47,0.53] | - | 0.496 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +20 | POOLED | gbt3 | 0.499 [0.47,0.53] | 0.499 [0.47,0.53] | - | 0.496 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +20 | POOLED | gbt3 | 0.499 [0.47,0.53] | 0.499 [0.47,0.53] | - | 0.496 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13 | +30 | POOLED | gbt3 | 0.500 [0.48,0.53] | 0.499 [0.46,0.53] | - | 0.496 | - | - | - | - | - | - |  | short by 0.181 AUC, 5 of 5 econ |
| F14-18 | +20 | ASIA | logit2 | 0.523 [0.48,0.57] | 0.499 [0.43,0.56] | - | 0.498 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8+base | +20 | NY | logit2 | 0.517 [0.47,0.56] | 0.499 [0.43,0.56] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | NY | logit2 | 0.517 [0.47,0.56] | 0.499 [0.43,0.56] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | NY | logit2 | 0.517 [0.47,0.56] | 0.499 [0.43,0.56] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | NY | logit2 | 0.517 [0.47,0.56] | 0.499 [0.43,0.56] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | NY | logit2 | 0.517 [0.47,0.56] | 0.499 [0.43,0.56] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | NY | rf | 0.507 [0.46,0.55] | 0.498 [0.43,0.56] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | NY | rf | 0.507 [0.46,0.55] | 0.498 [0.43,0.56] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | NY | rf | 0.507 [0.46,0.55] | 0.498 [0.43,0.56] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | NY | rf | 0.507 [0.46,0.55] | 0.498 [0.43,0.56] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | NY | rf | 0.507 [0.46,0.55] | 0.498 [0.43,0.56] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | LONDON | stack | 0.529 [0.48,0.57] | 0.498 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | LONDON | stack | 0.529 [0.48,0.57] | 0.498 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | LONDON | stack | 0.529 [0.48,0.57] | 0.498 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | LONDON | stack | 0.529 [0.48,0.57] | 0.498 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | LONDON | stack | 0.529 [0.48,0.57] | 0.498 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | LONDON | stack | 0.529 [0.48,0.57] | 0.498 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | NY | gbt3 | 0.479 [0.43,0.52] | 0.498 [0.43,0.56] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | POOLED | gbt3 | 0.504 [0.48,0.53] | 0.498 [0.46,0.54] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.182 AUC, 5 of 5 econ |
| F9-13+base | +5 | POOLED | gbt3 | 0.504 [0.48,0.53] | 0.498 [0.46,0.54] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.182 AUC, 5 of 5 econ |
| F5-8+base | +60 | LONDON | gbt3 | 0.512 [0.46,0.56] | 0.498 [0.44,0.56] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | POOLED | logit2 | 0.505 [0.48,0.53] | 0.497 [0.46,0.53] | - | 0.495 | - | - | - | - | - | - |  | short by 0.183 AUC, 5 of 5 econ |
| F14-18+base | +60 | POOLED | gbt3 | 0.505 [0.48,0.53] | 0.497 [0.46,0.53] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | POOLED | gbt3 | 0.505 [0.48,0.53] | 0.497 [0.46,0.53] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | NY | logit2 | 0.485 [0.45,0.52] | 0.497 [0.43,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | NY | logit2 | 0.485 [0.45,0.52] | 0.497 [0.43,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | NY | logit2 | 0.485 [0.45,0.52] | 0.497 [0.43,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | NY | logit2 | 0.485 [0.45,0.52] | 0.497 [0.43,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | NY | logit2 | 0.485 [0.45,0.52] | 0.497 [0.43,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | POOLED | rf | 0.514 [0.49,0.54] | 0.497 [0.46,0.54] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.183 AUC, 5 of 5 econ |
| F9-13+base | +5 | POOLED | rf | 0.514 [0.49,0.54] | 0.497 [0.46,0.54] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.183 AUC, 5 of 5 econ |
| F9-13+base | +5 | POOLED | rf | 0.514 [0.49,0.54] | 0.497 [0.46,0.54] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.183 AUC, 5 of 5 econ |
| F14-18+base | +10 | NY | logit2 | 0.498 [0.46,0.54] | 0.497 [0.43,0.57] | - | 0.505 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | ASIA | logit2 | 0.513 [0.47,0.56] | 0.496 [0.43,0.56] | - | 0.496 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +5 | ASIA | logit2 | 0.513 [0.47,0.56] | 0.496 [0.43,0.56] | - | 0.496 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +45 | POOLED | stack | 0.511 [0.49,0.54] | 0.496 [0.46,0.53] | - | 0.492 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | POOLED | stack | 0.511 [0.49,0.54] | 0.496 [0.46,0.53] | - | 0.492 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | POOLED | rf | 0.508 [0.48,0.53] | 0.496 [0.46,0.53] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | POOLED | rf | 0.508 [0.48,0.53] | 0.496 [0.46,0.53] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | POOLED | rf | 0.508 [0.48,0.53] | 0.496 [0.46,0.53] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | POOLED | rf | 0.508 [0.48,0.53] | 0.496 [0.46,0.53] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | NY | rf | 0.500 [0.45,0.55] | 0.496 [0.43,0.56] | - | 0.497 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | POOLED | logit2 | 0.508 [0.48,0.53] | 0.496 [0.46,0.53] | - | 0.493 | - | - | - | - | - | - |  | short by 0.184 AUC, 5 of 5 econ |
| F5-8+base | +5 | POOLED | rf | 0.508 [0.48,0.53] | 0.496 [0.46,0.54] | - | 0.492 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| F5-8+base | +5 | POOLED | rf | 0.508 [0.48,0.53] | 0.496 [0.46,0.54] | - | 0.492 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| F5-8+base | +5 | POOLED | rf | 0.508 [0.48,0.53] | 0.496 [0.46,0.54] | - | 0.492 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| F1-4+base | +10 | POOLED | gbt3 | 0.502 [0.48,0.53] | 0.496 [0.46,0.53] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| F9-13 | +10 | ASIA | logit2 | 0.514 [0.47,0.56] | 0.496 [0.44,0.55] | - | 0.492 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8+base | pre | NY | gbt3 | 0.495 [0.45,0.54] | 0.496 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | POOLED | stack | 0.508 [0.48,0.54] | 0.495 [0.46,0.53] | - | 0.492 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | POOLED | stack | 0.513 [0.49,0.54] | 0.495 [0.46,0.53] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | POOLED | stack | 0.513 [0.49,0.54] | 0.495 [0.46,0.53] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | NY | rf | 0.503 [0.46,0.54] | 0.495 [0.44,0.54] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | NY | rf | 0.503 [0.46,0.54] | 0.495 [0.44,0.54] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | NY | rf | 0.503 [0.46,0.54] | 0.495 [0.44,0.54] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | NY | rf | 0.503 [0.46,0.54] | 0.495 [0.44,0.54] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | NY | rf | 0.503 [0.46,0.54] | 0.495 [0.44,0.54] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | NY | gbt3 | 0.500 [0.46,0.54] | 0.495 [0.43,0.56] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | NY | gbt3 | 0.500 [0.46,0.54] | 0.495 [0.43,0.56] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | NY | gbt3 | 0.500 [0.46,0.54] | 0.495 [0.43,0.56] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | NY | gbt3 | 0.494 [0.45,0.54] | 0.495 [0.44,0.55] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | NY | gbt3 | 0.497 [0.45,0.54] | 0.495 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | NY | gbt3 | 0.494 [0.45,0.54] | 0.495 [0.44,0.55] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | NY | gbt3 | 0.497 [0.45,0.54] | 0.495 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | ASIA | stack | 0.516 [0.48,0.56] | 0.495 [0.42,0.57] | - | 0.486 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| F9-13+base | +15 | ASIA | stack | 0.516 [0.48,0.56] | 0.495 [0.42,0.57] | - | 0.486 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| F9-13 | +20 | POOLED | gbt3 | 0.503 [0.48,0.53] | 0.495 [0.46,0.53] | - | 0.493 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +20 | POOLED | gbt3 | 0.503 [0.48,0.53] | 0.495 [0.46,0.53] | - | 0.493 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +20 | POOLED | gbt3 | 0.503 [0.48,0.53] | 0.495 [0.46,0.53] | - | 0.493 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +20 | POOLED | gbt3 | 0.503 [0.48,0.53] | 0.495 [0.46,0.53] | - | 0.493 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18+base | +5 | NY | gbt3 | 0.492 [0.46,0.53] | 0.495 [0.45,0.54] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | NY | gbt3 | 0.492 [0.46,0.53] | 0.495 [0.45,0.54] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | NY | gbt3 | 0.492 [0.46,0.53] | 0.495 [0.45,0.54] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | NY | gbt3 | 0.492 [0.46,0.53] | 0.495 [0.45,0.54] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | POOLED | stack | 0.507 [0.48,0.53] | 0.495 [0.45,0.54] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | NY | stack | 0.499 [0.45,0.54] | 0.494 [0.44,0.55] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | POOLED | rf | 0.500 [0.48,0.52] | 0.494 [0.46,0.52] | - | 0.490 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8+base | pre | ASIA | gbt3 | 0.524 [0.48,0.57] | 0.494 [0.42,0.56] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | pre | ASIA | gbt3 | 0.524 [0.48,0.57] | 0.494 [0.42,0.56] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +20 | NY | logit2 | 0.521 [0.48,0.57] | 0.494 [0.43,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | NY | logit2 | 0.521 [0.48,0.57] | 0.494 [0.43,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | NY | logit2 | 0.521 [0.48,0.57] | 0.494 [0.43,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | NY | logit2 | 0.521 [0.48,0.57] | 0.494 [0.43,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | NY | logit2 | 0.521 [0.48,0.57] | 0.494 [0.43,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | NY | logit2 | 0.487 [0.45,0.53] | 0.494 [0.43,0.55] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | NY | logit2 | 0.487 [0.45,0.53] | 0.494 [0.43,0.55] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | NY | logit2 | 0.487 [0.45,0.53] | 0.494 [0.43,0.55] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | LONDON | logit2 | 0.509 [0.47,0.55] | 0.494 [0.44,0.55] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | LONDON | stack | 0.503 [0.45,0.56] | 0.494 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | LONDON | stack | 0.503 [0.45,0.56] | 0.494 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | LONDON | stack | 0.503 [0.45,0.56] | 0.494 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | LONDON | stack | 0.503 [0.45,0.56] | 0.494 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | LONDON | stack | 0.503 [0.45,0.56] | 0.494 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | LONDON | stack | 0.503 [0.45,0.56] | 0.494 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | LONDON | stack | 0.503 [0.45,0.56] | 0.494 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | LONDON | rf | 0.519 [0.47,0.57] | 0.494 [0.43,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | LONDON | rf | 0.519 [0.47,0.57] | 0.494 [0.43,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | LONDON | rf | 0.519 [0.47,0.57] | 0.494 [0.43,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | ASIA | logit2 | 0.526 [0.48,0.57] | 0.494 [0.43,0.56] | - | 0.494 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +5 | NY | gbt3 | 0.509 [0.47,0.55] | 0.494 [0.45,0.55] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | NY | gbt3 | 0.509 [0.47,0.55] | 0.494 [0.45,0.55] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | NY | gbt3 | 0.509 [0.47,0.55] | 0.494 [0.45,0.55] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | NY | gbt3 | 0.509 [0.47,0.55] | 0.494 [0.45,0.55] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | NY | rf | 0.484 [0.45,0.53] | 0.494 [0.44,0.56] | - | 0.489 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | NY | rf | 0.484 [0.45,0.53] | 0.494 [0.44,0.56] | - | 0.489 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | ASIA | gbt3 | 0.514 [0.47,0.56] | 0.493 [0.43,0.56] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | NY | gbt3 | 0.496 [0.45,0.54] | 0.493 [0.43,0.56] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | POOLED | logit2 | 0.506 [0.48,0.53] | 0.493 [0.46,0.53] | - | 0.492 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| F5-8 | +10 | POOLED | gbt3 | 0.516 [0.49,0.54] | 0.493 [0.45,0.54] | - | 0.492 | - | - | - | - | - | - |  | short by 0.187 AUC, 5 of 5 econ |
| F14-18 | +45 | POOLED | gbt3 | 0.507 [0.48,0.54] | 0.493 [0.46,0.53] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | POOLED | gbt3 | 0.507 [0.48,0.54] | 0.493 [0.46,0.53] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | NY | rf | 0.494 [0.46,0.54] | 0.492 [0.45,0.54] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | LONDON | rf | 0.515 [0.47,0.56] | 0.492 [0.44,0.55] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | ASIA | logit2 | 0.527 [0.48,0.58] | 0.492 [0.43,0.56] | - | 0.483 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | ASIA | logit2 | 0.527 [0.48,0.58] | 0.492 [0.43,0.56] | - | 0.483 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | ASIA | logit2 | 0.527 [0.48,0.58] | 0.492 [0.43,0.56] | - | 0.483 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | ASIA | logit2 | 0.527 [0.48,0.58] | 0.492 [0.43,0.56] | - | 0.483 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | POOLED | gbt3 | 0.508 [0.48,0.54] | 0.492 [0.46,0.53] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.188 AUC, 5 of 5 econ |
| F9-13+base | pre | POOLED | gbt3 | 0.508 [0.48,0.54] | 0.492 [0.46,0.53] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.188 AUC, 5 of 5 econ |
| F1-4+base | +5 | ASIA | gbt3 | 0.504 [0.46,0.55] | 0.492 [0.44,0.55] | - | 0.475 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +5 | ASIA | gbt3 | 0.504 [0.46,0.55] | 0.492 [0.44,0.55] | - | 0.475 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +5 | ASIA | gbt3 | 0.504 [0.46,0.55] | 0.492 [0.44,0.55] | - | 0.475 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +5 | ASIA | gbt3 | 0.504 [0.46,0.55] | 0.492 [0.44,0.55] | - | 0.475 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13 | +15 | ASIA | stack | 0.517 [0.48,0.56] | 0.492 [0.43,0.55] | - | 0.491 | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| F9-13 | +15 | ASIA | stack | 0.517 [0.48,0.56] | 0.492 [0.43,0.55] | - | 0.491 | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| F1-4+base | +45 | LONDON | rf | 0.504 [0.46,0.55] | 0.492 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | LONDON | rf | 0.504 [0.46,0.55] | 0.492 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | LONDON | rf | 0.504 [0.46,0.55] | 0.492 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | LONDON | rf | 0.504 [0.46,0.55] | 0.492 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | NY | logit2 | 0.503 [0.46,0.55] | 0.492 [0.43,0.56] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | NY | logit2 | 0.503 [0.46,0.55] | 0.492 [0.43,0.56] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | NY | logit2 | 0.503 [0.46,0.55] | 0.492 [0.43,0.56] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | NY | logit2 | 0.503 [0.46,0.55] | 0.492 [0.43,0.56] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | NY | logit2 | 0.503 [0.46,0.55] | 0.492 [0.43,0.56] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | LONDON | logit2 | 0.487 [0.44,0.53] | 0.492 [0.44,0.55] | - | 0.496 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | NY | rf | 0.480 [0.44,0.53] | 0.492 [0.42,0.56] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | NY | rf | 0.480 [0.44,0.53] | 0.492 [0.42,0.56] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | NY | rf | 0.480 [0.44,0.53] | 0.492 [0.42,0.56] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | NY | rf | 0.480 [0.44,0.53] | 0.492 [0.42,0.56] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | ASIA | logit2 | 0.532 [0.49,0.57] | 0.492 [0.42,0.56] | - | 0.480 | - | - | - | - | - | - |  | WF-only (dead) |
| F1-4 | +30 | ASIA | logit2 | 0.532 [0.49,0.57] | 0.492 [0.42,0.56] | - | 0.480 | - | - | - | - | - | - |  | WF-only (dead) |
| F1-4 | +30 | ASIA | logit2 | 0.532 [0.49,0.57] | 0.492 [0.42,0.56] | - | 0.480 | - | - | - | - | - | - |  | WF-only (dead) |
| F1-4 | +30 | ASIA | logit2 | 0.532 [0.49,0.57] | 0.492 [0.42,0.56] | - | 0.480 | - | - | - | - | - | - |  | WF-only (dead) |
| F1-4 | +30 | ASIA | logit2 | 0.532 [0.49,0.57] | 0.492 [0.42,0.56] | - | 0.480 | - | - | - | - | - | - |  | WF-only (dead) |
| F14-18 | +20 | LONDON | rf | 0.513 [0.47,0.55] | 0.492 [0.44,0.55] | - | 0.483 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | LONDON | rf | 0.513 [0.47,0.55] | 0.492 [0.44,0.55] | - | 0.483 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | LONDON | rf | 0.513 [0.47,0.55] | 0.492 [0.44,0.55] | - | 0.483 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | POOLED | gbt3 | 0.510 [0.48,0.54] | 0.491 [0.46,0.53] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | POOLED | gbt3 | 0.510 [0.48,0.54] | 0.491 [0.46,0.53] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | NY | rf | 0.490 [0.45,0.53] | 0.491 [0.45,0.54] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | ASIA | stack | 0.518 [0.48,0.56] | 0.491 [0.43,0.55] | - | 0.481 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +20 | ASIA | stack | 0.518 [0.48,0.56] | 0.491 [0.43,0.55] | - | 0.481 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +20 | ASIA | stack | 0.518 [0.48,0.56] | 0.491 [0.43,0.55] | - | 0.481 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +20 | ASIA | stack | 0.518 [0.48,0.56] | 0.491 [0.43,0.55] | - | 0.481 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +5 | POOLED | rf | 0.506 [0.48,0.53] | 0.491 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | short by 0.189 AUC, 5 of 5 econ |
| F5-8 | +5 | POOLED | rf | 0.506 [0.48,0.53] | 0.491 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | short by 0.189 AUC, 5 of 5 econ |
| F5-8 | +5 | POOLED | rf | 0.506 [0.48,0.53] | 0.491 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | short by 0.189 AUC, 5 of 5 econ |
| F5-8+base | +15 | NY | logit2 | 0.512 [0.47,0.56] | 0.491 [0.42,0.56] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | NY | logit2 | 0.512 [0.47,0.56] | 0.491 [0.42,0.56] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | NY | logit2 | 0.512 [0.47,0.56] | 0.491 [0.42,0.56] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | NY | logit2 | 0.512 [0.47,0.56] | 0.491 [0.42,0.56] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | NY | logit2 | 0.512 [0.47,0.56] | 0.491 [0.42,0.56] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | POOLED | logit2 | 0.505 [0.48,0.53] | 0.491 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | ASIA | gbt3 | 0.528 [0.48,0.57] | 0.491 [0.42,0.55] | - | 0.481 | - | - | - | - | - | - |  | WF-only (dead) |
| F5-8 | +30 | ASIA | gbt3 | 0.528 [0.48,0.57] | 0.491 [0.42,0.55] | - | 0.481 | - | - | - | - | - | - |  | WF-only (dead) |
| F1-4+base | +30 | NY | rf | 0.479 [0.44,0.52] | 0.491 [0.42,0.56] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | NY | rf | 0.479 [0.44,0.52] | 0.491 [0.42,0.56] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | NY | rf | 0.479 [0.44,0.52] | 0.491 [0.42,0.56] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | NY | rf | 0.479 [0.44,0.52] | 0.491 [0.42,0.56] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | ASIA | logit2 | 0.505 [0.47,0.55] | 0.491 [0.44,0.55] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +5 | ASIA | logit2 | 0.505 [0.47,0.55] | 0.491 [0.44,0.55] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | pre | NY | logit2 | 0.492 [0.45,0.53] | 0.491 [0.43,0.55] | - | 0.506 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | NY | logit2 | 0.492 [0.45,0.53] | 0.491 [0.43,0.55] | - | 0.506 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | POOLED | gbt3 | 0.514 [0.49,0.54] | 0.491 [0.45,0.53] | - | 0.489 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | POOLED | gbt3 | 0.514 [0.49,0.54] | 0.491 [0.45,0.53] | - | 0.489 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | POOLED | gbt3 | 0.498 [0.47,0.52] | 0.491 [0.46,0.53] | - | 0.483 | - | - | - | - | - | - |  | short by 0.189 AUC, 5 of 5 econ |
| F14-18 | pre | POOLED | gbt3 | 0.498 [0.47,0.52] | 0.491 [0.46,0.53] | - | 0.483 | - | - | - | - | - | - |  | short by 0.189 AUC, 5 of 5 econ |
| F9-13+base | +60 | LONDON | rf | 0.517 [0.47,0.56] | 0.491 [0.42,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | LONDON | rf | 0.517 [0.47,0.56] | 0.491 [0.42,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | LONDON | rf | 0.517 [0.47,0.56] | 0.491 [0.42,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | LONDON | logit2 | 0.494 [0.45,0.54] | 0.491 [0.43,0.55] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | ASIA | stack | 0.519 [0.48,0.56] | 0.490 [0.43,0.55] | - | 0.485 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +45 | POOLED | gbt3 | 0.502 [0.48,0.53] | 0.490 [0.46,0.52] | - | 0.490 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | POOLED | gbt3 | 0.502 [0.48,0.53] | 0.490 [0.46,0.52] | - | 0.490 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | POOLED | logit2 | 0.491 [0.47,0.52] | 0.490 [0.46,0.52] | - | 0.491 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F5-8 | +5 | POOLED | gbt3 | 0.511 [0.49,0.54] | 0.490 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F5-8 | +5 | POOLED | gbt3 | 0.511 [0.49,0.54] | 0.490 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F1-4 | +15 | NY | stack | 0.489 [0.44,0.53] | 0.490 [0.43,0.56] | - | 0.499 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | ASIA | stack | 0.539 [0.50,0.58] | 0.490 [0.43,0.55] | - | 0.468 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +20 | ASIA | stack | 0.539 [0.50,0.58] | 0.490 [0.43,0.55] | - | 0.468 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +20 | ASIA | stack | 0.539 [0.50,0.58] | 0.490 [0.43,0.55] | - | 0.468 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +20 | ASIA | stack | 0.539 [0.50,0.58] | 0.490 [0.43,0.55] | - | 0.468 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8 | +10 | POOLED | rf | 0.514 [0.49,0.54] | 0.490 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F5-8 | +10 | POOLED | rf | 0.514 [0.49,0.54] | 0.490 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F5-8 | +10 | POOLED | rf | 0.514 [0.49,0.54] | 0.490 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F5-8 | +10 | POOLED | rf | 0.514 [0.49,0.54] | 0.490 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F5-8 | +10 | POOLED | rf | 0.514 [0.49,0.54] | 0.490 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F9-13+base | +10 | NY | logit2 | 0.510 [0.47,0.55] | 0.490 [0.42,0.56] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | POOLED | rf | 0.496 [0.47,0.52] | 0.490 [0.46,0.52] | - | 0.486 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F1-4+base | +15 | ASIA | stack | 0.518 [0.48,0.56] | 0.490 [0.43,0.56] | - | 0.476 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +15 | ASIA | stack | 0.518 [0.48,0.56] | 0.490 [0.43,0.56] | - | 0.476 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8 | +10 | ASIA | gbt3 | 0.523 [0.48,0.57] | 0.490 [0.42,0.56] | - | 0.487 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +10 | ASIA | gbt3 | 0.523 [0.48,0.57] | 0.490 [0.42,0.56] | - | 0.487 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +10 | ASIA | gbt3 | 0.523 [0.48,0.57] | 0.490 [0.42,0.56] | - | 0.487 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +30 | LONDON | rf | 0.508 [0.47,0.55] | 0.490 [0.43,0.54] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | ASIA | stack | 0.529 [0.49,0.57] | 0.490 [0.43,0.56] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +10 | ASIA | stack | 0.529 [0.49,0.57] | 0.490 [0.43,0.56] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +10 | ASIA | stack | 0.529 [0.49,0.57] | 0.490 [0.43,0.56] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +15 | LONDON | logit2 | 0.516 [0.47,0.56] | 0.490 [0.43,0.56] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | POOLED | gbt3 | 0.500 [0.48,0.52] | 0.490 [0.46,0.52] | - | 0.487 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F1-4 | +5 | POOLED | gbt3 | 0.500 [0.48,0.52] | 0.490 [0.46,0.52] | - | 0.487 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| F9-13 | +10 | ASIA | gbt3 | 0.519 [0.48,0.56] | 0.490 [0.43,0.55] | - | 0.481 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +10 | ASIA | gbt3 | 0.519 [0.48,0.56] | 0.490 [0.43,0.55] | - | 0.481 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +10 | ASIA | gbt3 | 0.519 [0.48,0.56] | 0.490 [0.43,0.55] | - | 0.481 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +10 | POOLED | gbt3 | 0.501 [0.48,0.52] | 0.489 [0.46,0.52] | - | 0.485 | - | - | - | - | - | - |  | short by 0.191 AUC, 5 of 5 econ |
| F14-18+base | +20 | POOLED | stack | 0.508 [0.48,0.53] | 0.489 [0.45,0.53] | - | 0.482 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +30 | POOLED | rf | 0.487 [0.46,0.51] | 0.489 [0.46,0.52] | - | 0.484 | - | - | - | - | - | - | stack | short by 0.191 AUC, 5 of 5 econ |
| F14-18 | +15 | POOLED | rf | 0.503 [0.48,0.53] | 0.489 [0.45,0.53] | - | 0.487 | - | - | - | - | - | - |  | short by 0.191 AUC, 5 of 5 econ |
| F9-13+base | +45 | LONDON | rf | 0.508 [0.46,0.56] | 0.489 [0.42,0.55] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | LONDON | rf | 0.508 [0.46,0.56] | 0.489 [0.42,0.55] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | LONDON | rf | 0.508 [0.46,0.56] | 0.489 [0.42,0.55] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | LONDON | rf | 0.508 [0.46,0.56] | 0.489 [0.42,0.55] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | LONDON | logit2 | 0.524 [0.48,0.57] | 0.489 [0.43,0.55] | - | 0.489 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | LONDON | stack | 0.494 [0.45,0.54] | 0.488 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | LONDON | stack | 0.494 [0.45,0.54] | 0.488 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | LONDON | stack | 0.494 [0.45,0.54] | 0.488 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | LONDON | stack | 0.494 [0.45,0.54] | 0.488 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | LONDON | stack | 0.494 [0.45,0.54] | 0.488 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | LONDON | stack | 0.494 [0.45,0.54] | 0.488 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | LONDON | stack | 0.494 [0.45,0.54] | 0.488 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | POOLED | gbt3 | 0.494 [0.47,0.52] | 0.488 [0.45,0.53] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | pre | POOLED | gbt3 | 0.494 [0.47,0.52] | 0.488 [0.45,0.53] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8 | +5 | NY | logit2 | 0.502 [0.47,0.54] | 0.488 [0.44,0.55] | - | 0.497 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | NY | logit2 | 0.502 [0.47,0.54] | 0.488 [0.44,0.55] | - | 0.497 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | NY | rf | 0.514 [0.48,0.56] | 0.488 [0.43,0.55] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | NY | rf | 0.514 [0.48,0.56] | 0.488 [0.43,0.55] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | ASIA | stack | 0.512 [0.47,0.56] | 0.488 [0.43,0.55] | - | 0.477 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | NY | rf | 0.517 [0.48,0.56] | 0.488 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | NY | rf | 0.517 [0.48,0.56] | 0.488 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | NY | logit2 | 0.502 [0.46,0.54] | 0.488 [0.43,0.55] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | POOLED | rf | 0.503 [0.48,0.53] | 0.487 [0.45,0.52] | - | 0.487 | - | - | - | - | - | - |  | short by 0.193 AUC, 5 of 5 econ |
| F9-13 | +20 | POOLED | stack | 0.505 [0.48,0.53] | 0.487 [0.45,0.52] | - | 0.483 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | pre | ASIA | rf | 0.491 [0.45,0.54] | 0.487 [0.43,0.54] | - | 0.491 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | pre | ASIA | rf | 0.491 [0.45,0.54] | 0.487 [0.43,0.54] | - | 0.491 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +45 | LONDON | gbt3 | 0.520 [0.48,0.57] | 0.487 [0.42,0.55] | - | 0.487 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | LONDON | gbt3 | 0.520 [0.48,0.57] | 0.487 [0.42,0.55] | - | 0.487 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | LONDON | stack | 0.519 [0.47,0.57] | 0.487 [0.42,0.54] | - | 0.487 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | LONDON | stack | 0.519 [0.47,0.57] | 0.487 [0.42,0.54] | - | 0.487 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | LONDON | stack | 0.519 [0.47,0.57] | 0.487 [0.42,0.54] | - | 0.487 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | LONDON | stack | 0.519 [0.47,0.57] | 0.487 [0.42,0.54] | - | 0.487 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | LONDON | stack | 0.519 [0.47,0.57] | 0.487 [0.42,0.54] | - | 0.487 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | LONDON | stack | 0.519 [0.47,0.57] | 0.487 [0.42,0.54] | - | 0.487 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | LONDON | stack | 0.519 [0.47,0.57] | 0.487 [0.42,0.54] | - | 0.487 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | POOLED | stack | 0.500 [0.47,0.53] | 0.487 [0.45,0.52] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | NY | stack | 0.493 [0.45,0.53] | 0.487 [0.43,0.55] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | POOLED | gbt3 | 0.488 [0.46,0.51] | 0.487 [0.45,0.52] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | POOLED | gbt3 | 0.488 [0.46,0.51] | 0.487 [0.45,0.52] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | LONDON | logit2 | 0.509 [0.47,0.56] | 0.487 [0.43,0.55] | - | 0.485 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | POOLED | logit2 | 0.492 [0.47,0.52] | 0.486 [0.45,0.52] | - | 0.482 | - | - | - | - | - | - |  | short by 0.194 AUC, 5 of 5 econ |
| F9-13+base | +30 | POOLED | gbt3 | 0.485 [0.46,0.51] | 0.486 [0.45,0.52] | - | 0.482 | - | - | - | - | - | - | stack | short by 0.194 AUC, 5 of 5 econ |
| F1-4 | +30 | ASIA | gbt3 | 0.492 [0.45,0.53] | 0.486 [0.43,0.54] | - | 0.476 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +30 | ASIA | gbt3 | 0.492 [0.45,0.53] | 0.486 [0.43,0.54] | - | 0.476 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | ASIA | gbt3 | 0.499 [0.46,0.54] | 0.486 [0.43,0.54] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | ASIA | gbt3 | 0.499 [0.46,0.54] | 0.486 [0.43,0.54] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +5 | ASIA | gbt3 | 0.521 [0.47,0.57] | 0.486 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +5 | ASIA | gbt3 | 0.521 [0.47,0.57] | 0.486 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +5 | ASIA | gbt3 | 0.521 [0.47,0.57] | 0.486 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +5 | ASIA | gbt3 | 0.521 [0.47,0.57] | 0.486 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +10 | ASIA | stack | 0.538 [0.50,0.58] | 0.486 [0.42,0.55] | - | 0.466 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +10 | ASIA | stack | 0.538 [0.50,0.58] | 0.486 [0.42,0.55] | - | 0.466 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +10 | ASIA | stack | 0.538 [0.50,0.58] | 0.486 [0.42,0.55] | - | 0.466 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18 | +30 | POOLED | gbt3 | 0.474 [0.45,0.50] | 0.486 [0.44,0.53] | - | 0.483 | - | - | - | - | - | - |  | short by 0.194 AUC, 5 of 5 econ |
| F1-4 | +20 | LONDON | rf | 0.511 [0.47,0.56] | 0.485 [0.42,0.54] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | LONDON | rf | 0.511 [0.47,0.56] | 0.485 [0.42,0.54] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | LONDON | rf | 0.511 [0.47,0.56] | 0.485 [0.42,0.54] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +20 | NY | rf | 0.495 [0.45,0.54] | 0.485 [0.43,0.54] | - | 0.483 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | ASIA | stack | 0.506 [0.47,0.55] | 0.485 [0.42,0.55] | - | 0.483 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | POOLED | stack | 0.520 [0.49,0.55] | 0.485 [0.44,0.52] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | NY | logit2 | 0.500 [0.46,0.54] | 0.485 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | NY | logit2 | 0.500 [0.46,0.54] | 0.485 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | NY | stack | 0.513 [0.47,0.56] | 0.485 [0.42,0.56] | - | 0.479 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | NY | stack | 0.513 [0.47,0.56] | 0.485 [0.42,0.56] | - | 0.479 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | NY | stack | 0.513 [0.47,0.56] | 0.485 [0.42,0.56] | - | 0.479 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | NY | stack | 0.513 [0.47,0.56] | 0.485 [0.42,0.56] | - | 0.479 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | ASIA | gbt3 | 0.513 [0.47,0.55] | 0.485 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +5 | ASIA | gbt3 | 0.513 [0.47,0.55] | 0.485 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +5 | ASIA | gbt3 | 0.513 [0.47,0.55] | 0.485 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +5 | ASIA | gbt3 | 0.513 [0.47,0.55] | 0.485 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18+base | pre | POOLED | gbt3 | 0.494 [0.47,0.52] | 0.484 [0.45,0.52] | - | 0.480 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | pre | POOLED | gbt3 | 0.494 [0.47,0.52] | 0.484 [0.45,0.52] | - | 0.480 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +10 | ASIA | rf | 0.507 [0.46,0.55] | 0.484 [0.42,0.55] | - | 0.479 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +5 | POOLED | logit2 | 0.500 [0.48,0.53] | 0.484 [0.45,0.52] | - | 0.482 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +20 | NY | logit2 | 0.476 [0.43,0.52] | 0.484 [0.42,0.55] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | NY | logit2 | 0.476 [0.43,0.52] | 0.484 [0.42,0.55] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | NY | logit2 | 0.476 [0.43,0.52] | 0.484 [0.42,0.55] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | NY | logit2 | 0.476 [0.43,0.52] | 0.484 [0.42,0.55] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | NY | logit2 | 0.476 [0.43,0.52] | 0.484 [0.42,0.55] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | POOLED | stack | 0.505 [0.48,0.53] | 0.484 [0.45,0.52] | - | 0.485 | - | - | - | - | - | - |  | short by 0.196 AUC, 5 of 5 econ |
| F1-4 | +10 | POOLED | stack | 0.505 [0.48,0.53] | 0.484 [0.45,0.52] | - | 0.485 | - | - | - | - | - | - |  | short by 0.196 AUC, 5 of 5 econ |
| F14-18+base | +10 | LONDON | rf | 0.500 [0.46,0.54] | 0.484 [0.42,0.54] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | ASIA | gbt3 | 0.513 [0.47,0.56] | 0.484 [0.41,0.55] | - | 0.470 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | ASIA | gbt3 | 0.513 [0.47,0.56] | 0.484 [0.41,0.55] | - | 0.470 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8+base | +20 | ASIA | stack | 0.514 [0.47,0.55] | 0.483 [0.43,0.54] | - | 0.475 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +20 | ASIA | stack | 0.514 [0.47,0.55] | 0.483 [0.43,0.54] | - | 0.475 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +20 | ASIA | stack | 0.514 [0.47,0.55] | 0.483 [0.43,0.54] | - | 0.475 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +20 | ASIA | stack | 0.514 [0.47,0.55] | 0.483 [0.43,0.54] | - | 0.475 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18 | +20 | POOLED | logit2 | 0.503 [0.48,0.53] | 0.483 [0.45,0.51] | - | 0.481 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +20 | POOLED | logit2 | 0.503 [0.48,0.53] | 0.483 [0.45,0.51] | - | 0.481 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +15 | LONDON | stack | 0.522 [0.48,0.57] | 0.483 [0.43,0.53] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | LONDON | stack | 0.522 [0.48,0.57] | 0.483 [0.43,0.53] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | LONDON | stack | 0.522 [0.48,0.57] | 0.483 [0.43,0.53] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | LONDON | stack | 0.522 [0.48,0.57] | 0.483 [0.43,0.53] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | LONDON | stack | 0.522 [0.48,0.57] | 0.483 [0.43,0.53] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | LONDON | stack | 0.522 [0.48,0.57] | 0.483 [0.43,0.53] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | LONDON | stack | 0.522 [0.48,0.57] | 0.483 [0.43,0.53] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | NY | logit2 | 0.488 [0.45,0.53] | 0.483 [0.43,0.53] | - | 0.492 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | NY | logit2 | 0.488 [0.45,0.53] | 0.483 [0.43,0.53] | - | 0.492 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | LONDON | stack | 0.503 [0.46,0.55] | 0.483 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | LONDON | stack | 0.503 [0.46,0.55] | 0.483 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | LONDON | stack | 0.503 [0.46,0.55] | 0.483 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | LONDON | stack | 0.503 [0.46,0.55] | 0.483 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | LONDON | stack | 0.503 [0.46,0.55] | 0.483 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | LONDON | stack | 0.503 [0.46,0.55] | 0.483 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | NY | gbt3 | 0.486 [0.44,0.53] | 0.483 [0.42,0.55] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | NY | gbt3 | 0.494 [0.44,0.54] | 0.483 [0.42,0.55] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | NY | gbt3 | 0.494 [0.44,0.54] | 0.483 [0.42,0.55] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | NY | gbt3 | 0.494 [0.44,0.54] | 0.483 [0.42,0.55] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +15 | NY | rf | 0.480 [0.43,0.52] | 0.483 [0.42,0.54] | - | 0.476 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | LONDON | gbt3 | 0.467 [0.43,0.51] | 0.483 [0.42,0.54] | - | 0.480 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | LONDON | gbt3 | 0.517 [0.47,0.56] | 0.482 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | LONDON | rf | 0.457 [0.41,0.50] | 0.482 [0.42,0.54] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | LONDON | stack | 0.493 [0.45,0.54] | 0.482 [0.42,0.54] | - | 0.471 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | LONDON | stack | 0.493 [0.45,0.54] | 0.482 [0.42,0.54] | - | 0.471 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | LONDON | stack | 0.493 [0.45,0.54] | 0.482 [0.42,0.54] | - | 0.471 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | LONDON | stack | 0.493 [0.45,0.54] | 0.482 [0.42,0.54] | - | 0.471 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | LONDON | stack | 0.493 [0.45,0.54] | 0.482 [0.42,0.54] | - | 0.471 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | LONDON | rf | 0.505 [0.46,0.55] | 0.482 [0.43,0.55] | - | 0.476 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | POOLED | gbt3 | 0.493 [0.47,0.52] | 0.482 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | POOLED | gbt3 | 0.493 [0.47,0.52] | 0.482 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | NY | gbt3 | 0.508 [0.46,0.55] | 0.482 [0.43,0.54] | - | 0.481 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | NY | gbt3 | 0.508 [0.46,0.55] | 0.482 [0.43,0.54] | - | 0.481 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | NY | gbt3 | 0.508 [0.46,0.55] | 0.482 [0.43,0.54] | - | 0.481 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | NY | gbt3 | 0.498 [0.46,0.54] | 0.482 [0.41,0.55] | - | 0.476 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | NY | gbt3 | 0.498 [0.46,0.54] | 0.482 [0.41,0.55] | - | 0.476 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | NY | gbt3 | 0.498 [0.46,0.54] | 0.482 [0.41,0.55] | - | 0.476 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | NY | logit2 | 0.491 [0.45,0.53] | 0.481 [0.43,0.54] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | NY | logit2 | 0.491 [0.45,0.53] | 0.481 [0.43,0.54] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | NY | logit2 | 0.491 [0.45,0.53] | 0.481 [0.43,0.54] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | NY | logit2 | 0.491 [0.45,0.53] | 0.481 [0.43,0.54] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | NY | logit2 | 0.491 [0.45,0.53] | 0.481 [0.43,0.54] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | POOLED | gbt3 | 0.490 [0.47,0.52] | 0.481 [0.45,0.52] | - | 0.479 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +5 | POOLED | gbt3 | 0.490 [0.47,0.52] | 0.481 [0.45,0.52] | - | 0.479 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | LONDON | stack | 0.512 [0.47,0.56] | 0.481 [0.42,0.54] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | LONDON | stack | 0.512 [0.47,0.56] | 0.481 [0.42,0.54] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | LONDON | stack | 0.512 [0.47,0.56] | 0.481 [0.42,0.54] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | LONDON | stack | 0.512 [0.47,0.56] | 0.481 [0.42,0.54] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | LONDON | stack | 0.512 [0.47,0.56] | 0.481 [0.42,0.54] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | LONDON | stack | 0.492 [0.45,0.54] | 0.481 [0.42,0.54] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | LONDON | stack | 0.492 [0.45,0.54] | 0.481 [0.42,0.54] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | LONDON | stack | 0.492 [0.45,0.54] | 0.481 [0.42,0.54] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | LONDON | stack | 0.492 [0.45,0.54] | 0.481 [0.42,0.54] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | LONDON | stack | 0.492 [0.45,0.54] | 0.481 [0.42,0.54] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | LONDON | stack | 0.492 [0.45,0.54] | 0.481 [0.42,0.54] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | LONDON | stack | 0.504 [0.46,0.55] | 0.480 [0.42,0.54] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | LONDON | stack | 0.504 [0.46,0.55] | 0.480 [0.42,0.54] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | POOLED | stack | 0.513 [0.49,0.54] | 0.480 [0.44,0.51] | - | 0.473 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | POOLED | stack | 0.513 [0.49,0.54] | 0.480 [0.44,0.51] | - | 0.473 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | ASIA | stack | 0.531 [0.49,0.57] | 0.480 [0.42,0.54] | - | 0.460 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | ASIA | stack | 0.531 [0.49,0.57] | 0.480 [0.42,0.54] | - | 0.460 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | ASIA | stack | 0.531 [0.49,0.57] | 0.480 [0.42,0.54] | - | 0.460 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | ASIA | stack | 0.531 [0.49,0.57] | 0.480 [0.42,0.54] | - | 0.460 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | ASIA | gbt3 | 0.486 [0.44,0.53] | 0.480 [0.43,0.53] | - | 0.476 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | ASIA | gbt3 | 0.486 [0.44,0.53] | 0.480 [0.43,0.53] | - | 0.476 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | ASIA | gbt3 | 0.486 [0.44,0.53] | 0.480 [0.43,0.53] | - | 0.476 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +45 | LONDON | stack | 0.514 [0.46,0.56] | 0.480 [0.41,0.55] | - | 0.471 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | LONDON | stack | 0.514 [0.46,0.56] | 0.480 [0.41,0.55] | - | 0.471 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | LONDON | gbt3 | 0.500 [0.46,0.54] | 0.480 [0.42,0.54] | - | 0.475 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | LONDON | logit2 | 0.505 [0.46,0.55] | 0.479 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | LONDON | stack | 0.525 [0.47,0.57] | 0.479 [0.41,0.54] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | LONDON | stack | 0.525 [0.47,0.57] | 0.479 [0.41,0.54] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | LONDON | stack | 0.525 [0.47,0.57] | 0.479 [0.41,0.54] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | LONDON | stack | 0.525 [0.47,0.57] | 0.479 [0.41,0.54] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | LONDON | stack | 0.525 [0.47,0.57] | 0.479 [0.41,0.54] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | pre | LONDON | stack | 0.525 [0.47,0.57] | 0.479 [0.41,0.54] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | POOLED | gbt3 | 0.493 [0.47,0.52] | 0.479 [0.44,0.52] | - | 0.480 | - | - | - | - | - | - |  | short by 0.201 AUC, 5 of 5 econ |
| F14-18 | +5 | POOLED | rf | 0.495 [0.47,0.52] | 0.479 [0.45,0.51] | - | 0.479 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +5 | POOLED | rf | 0.495 [0.47,0.52] | 0.479 [0.45,0.51] | - | 0.479 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +5 | POOLED | rf | 0.495 [0.47,0.52] | 0.479 [0.45,0.51] | - | 0.479 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8+base | +20 | NY | gbt3 | 0.492 [0.45,0.53] | 0.479 [0.43,0.53] | - | 0.474 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +20 | NY | gbt3 | 0.492 [0.45,0.53] | 0.479 [0.43,0.53] | - | 0.474 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | LONDON | rf | 0.500 [0.45,0.55] | 0.479 [0.41,0.55] | - | 0.473 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | LONDON | rf | 0.500 [0.45,0.55] | 0.479 [0.41,0.55] | - | 0.473 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | LONDON | rf | 0.500 [0.45,0.55] | 0.479 [0.41,0.55] | - | 0.473 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | LONDON | rf | 0.500 [0.45,0.55] | 0.479 [0.41,0.55] | - | 0.473 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | LONDON | rf | 0.494 [0.45,0.54] | 0.478 [0.42,0.53] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | LONDON | stack | 0.507 [0.47,0.55] | 0.478 [0.42,0.54] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | LONDON | stack | 0.507 [0.47,0.55] | 0.478 [0.42,0.54] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | LONDON | stack | 0.507 [0.47,0.55] | 0.478 [0.42,0.54] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | LONDON | stack | 0.507 [0.47,0.55] | 0.478 [0.42,0.54] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | LONDON | stack | 0.507 [0.47,0.55] | 0.478 [0.42,0.54] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | LONDON | stack | 0.507 [0.47,0.55] | 0.478 [0.42,0.54] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | LONDON | stack | 0.507 [0.47,0.55] | 0.478 [0.42,0.54] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | NY | gbt3 | 0.486 [0.44,0.53] | 0.478 [0.41,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | NY | gbt3 | 0.486 [0.44,0.53] | 0.478 [0.41,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | NY | gbt3 | 0.486 [0.44,0.53] | 0.478 [0.41,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | NY | gbt3 | 0.486 [0.44,0.53] | 0.478 [0.41,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | NY | rf | 0.477 [0.44,0.52] | 0.478 [0.42,0.54] | - | 0.486 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | NY | rf | 0.477 [0.44,0.52] | 0.478 [0.42,0.54] | - | 0.486 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | NY | rf | 0.477 [0.44,0.52] | 0.478 [0.42,0.54] | - | 0.486 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | NY | rf | 0.477 [0.44,0.52] | 0.478 [0.42,0.54] | - | 0.486 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | NY | rf | 0.477 [0.44,0.52] | 0.478 [0.42,0.54] | - | 0.486 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | LONDON | stack | 0.511 [0.47,0.56] | 0.477 [0.42,0.55] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | LONDON | stack | 0.511 [0.47,0.56] | 0.477 [0.42,0.55] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | LONDON | stack | 0.511 [0.47,0.56] | 0.477 [0.42,0.55] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | LONDON | stack | 0.511 [0.47,0.56] | 0.477 [0.42,0.55] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | LONDON | stack | 0.511 [0.47,0.56] | 0.477 [0.42,0.55] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | POOLED | logit2 | 0.493 [0.47,0.52] | 0.477 [0.44,0.52] | - | 0.475 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +60 | POOLED | rf | 0.504 [0.48,0.53] | 0.477 [0.44,0.52] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | POOLED | rf | 0.504 [0.48,0.53] | 0.477 [0.44,0.52] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | POOLED | rf | 0.504 [0.48,0.53] | 0.477 [0.44,0.52] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | POOLED | rf | 0.504 [0.48,0.53] | 0.477 [0.44,0.52] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | POOLED | stack | 0.506 [0.48,0.53] | 0.477 [0.43,0.52] | - | 0.470 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +10 | POOLED | stack | 0.506 [0.48,0.53] | 0.477 [0.43,0.52] | - | 0.470 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +5 | POOLED | logit2 | 0.495 [0.47,0.52] | 0.477 [0.44,0.52] | - | 0.473 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8+base | +5 | NY | rf | 0.484 [0.44,0.53] | 0.477 [0.41,0.54] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +5 | NY | rf | 0.484 [0.44,0.53] | 0.477 [0.41,0.54] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | LONDON | rf | 0.459 [0.42,0.50] | 0.476 [0.42,0.54] | - | 0.470 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | LONDON | rf | 0.485 [0.44,0.53] | 0.476 [0.41,0.54] | - | 0.479 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | NY | gbt3 | 0.478 [0.43,0.53] | 0.476 [0.41,0.54] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | NY | gbt3 | 0.478 [0.43,0.53] | 0.476 [0.41,0.54] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | NY | gbt3 | 0.478 [0.43,0.53] | 0.476 [0.41,0.54] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | LONDON | gbt3 | 0.492 [0.45,0.53] | 0.476 [0.42,0.53] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | LONDON | gbt3 | 0.492 [0.45,0.53] | 0.476 [0.42,0.53] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | LONDON | gbt3 | 0.492 [0.45,0.53] | 0.476 [0.42,0.53] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | LONDON | gbt3 | 0.492 [0.45,0.53] | 0.476 [0.42,0.53] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | NY | gbt3 | 0.471 [0.43,0.51] | 0.476 [0.42,0.54] | - | 0.492 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | NY | rf | 0.472 [0.43,0.52] | 0.476 [0.41,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | NY | rf | 0.472 [0.43,0.52] | 0.476 [0.41,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | POOLED | stack | 0.498 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.474 | - | - | - | - | - | - |  | short by 0.204 AUC, 5 of 5 econ |
| F14-18 | +15 | POOLED | stack | 0.498 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.474 | - | - | - | - | - | - |  | short by 0.204 AUC, 5 of 5 econ |
| F14-18 | +15 | POOLED | stack | 0.498 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.474 | - | - | - | - | - | - |  | short by 0.204 AUC, 5 of 5 econ |
| F14-18 | +15 | POOLED | stack | 0.498 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.474 | - | - | - | - | - | - |  | short by 0.204 AUC, 5 of 5 econ |
| F14-18 | +15 | POOLED | stack | 0.498 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.474 | - | - | - | - | - | - |  | short by 0.204 AUC, 5 of 5 econ |
| F5-8 | +60 | LONDON | stack | 0.505 [0.46,0.55] | 0.476 [0.42,0.53] | - | 0.474 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +60 | LONDON | stack | 0.505 [0.46,0.55] | 0.476 [0.42,0.53] | - | 0.474 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | NY | logit2 | 0.471 [0.43,0.51] | 0.476 [0.42,0.53] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | NY | logit2 | 0.471 [0.43,0.51] | 0.476 [0.42,0.53] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | NY | logit2 | 0.471 [0.43,0.51] | 0.476 [0.42,0.53] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | NY | logit2 | 0.471 [0.43,0.51] | 0.476 [0.42,0.53] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | NY | logit2 | 0.471 [0.43,0.51] | 0.476 [0.42,0.53] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | POOLED | logit2 | 0.506 [0.48,0.53] | 0.476 [0.44,0.51] | - | 0.473 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +45 | ASIA | gbt3 | 0.502 [0.46,0.55] | 0.476 [0.41,0.54] | - | 0.476 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | ASIA | gbt3 | 0.502 [0.46,0.55] | 0.476 [0.41,0.54] | - | 0.476 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | POOLED | rf | 0.495 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.475 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | POOLED | rf | 0.495 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.475 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | POOLED | rf | 0.495 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.475 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | POOLED | rf | 0.495 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.475 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | POOLED | rf | 0.495 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.475 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +45 | NY | stack | 0.487 [0.45,0.53] | 0.475 [0.41,0.54] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | NY | stack | 0.487 [0.45,0.53] | 0.475 [0.41,0.54] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | NY | stack | 0.487 [0.45,0.53] | 0.475 [0.41,0.54] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | POOLED | stack | 0.506 [0.48,0.53] | 0.475 [0.44,0.51] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | ASIA | gbt3 | 0.452 [0.40,0.50] | 0.475 [0.41,0.54] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +30 | ASIA | gbt3 | 0.452 [0.40,0.50] | 0.475 [0.41,0.54] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4+base | +10 | NY | gbt3 | 0.504 [0.47,0.54] | 0.475 [0.42,0.53] | - | 0.480 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | NY | gbt3 | 0.504 [0.47,0.54] | 0.475 [0.42,0.53] | - | 0.480 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | POOLED | gbt3 | 0.499 [0.47,0.53] | 0.475 [0.44,0.51] | - | 0.473 | - | - | - | - | - | - |  | short by 0.205 AUC, 5 of 5 econ |
| F14-18 | +20 | POOLED | stack | 0.491 [0.46,0.52] | 0.474 [0.43,0.51] | - | 0.470 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +10 | LONDON | logit2 | 0.497 [0.45,0.54] | 0.474 [0.41,0.54] | - | 0.469 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | LONDON | stack | 0.523 [0.48,0.57] | 0.474 [0.41,0.54] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | LONDON | stack | 0.523 [0.48,0.57] | 0.474 [0.41,0.54] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | LONDON | stack | 0.523 [0.48,0.57] | 0.474 [0.41,0.54] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | LONDON | stack | 0.523 [0.48,0.57] | 0.474 [0.41,0.54] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | LONDON | stack | 0.523 [0.48,0.57] | 0.474 [0.41,0.54] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | LONDON | stack | 0.523 [0.48,0.57] | 0.474 [0.41,0.54] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | LONDON | stack | 0.523 [0.48,0.57] | 0.474 [0.41,0.54] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | LONDON | rf | 0.497 [0.46,0.54] | 0.474 [0.42,0.53] | - | 0.470 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | LONDON | rf | 0.497 [0.46,0.54] | 0.474 [0.42,0.53] | - | 0.470 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | LONDON | rf | 0.497 [0.46,0.54] | 0.474 [0.42,0.53] | - | 0.470 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | LONDON | rf | 0.497 [0.46,0.54] | 0.474 [0.42,0.53] | - | 0.470 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | POOLED | stack | 0.516 [0.49,0.54] | 0.474 [0.44,0.51] | - | 0.468 | - | - | - | - | - | - | stack | short by 0.206 AUC, 5 of 5 econ |
| F14-18+base | +15 | POOLED | stack | 0.516 [0.49,0.54] | 0.474 [0.44,0.51] | - | 0.468 | - | - | - | - | - | - | stack | short by 0.206 AUC, 5 of 5 econ |
| F14-18+base | +15 | POOLED | stack | 0.516 [0.49,0.54] | 0.474 [0.44,0.51] | - | 0.468 | - | - | - | - | - | - | stack | short by 0.206 AUC, 5 of 5 econ |
| F14-18+base | +15 | POOLED | stack | 0.516 [0.49,0.54] | 0.474 [0.44,0.51] | - | 0.468 | - | - | - | - | - | - | stack | short by 0.206 AUC, 5 of 5 econ |
| F14-18+base | +15 | POOLED | stack | 0.516 [0.49,0.54] | 0.474 [0.44,0.51] | - | 0.468 | - | - | - | - | - | - | stack | short by 0.206 AUC, 5 of 5 econ |
| F14-18 | +5 | POOLED | stack | 0.501 [0.48,0.52] | 0.474 [0.43,0.51] | - | 0.469 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +5 | POOLED | stack | 0.501 [0.48,0.52] | 0.474 [0.43,0.51] | - | 0.469 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | POOLED | rf | 0.495 [0.47,0.52] | 0.474 [0.44,0.51] | - | 0.472 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | POOLED | rf | 0.495 [0.47,0.52] | 0.474 [0.44,0.51] | - | 0.472 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | POOLED | rf | 0.495 [0.47,0.52] | 0.474 [0.44,0.51] | - | 0.472 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +30 | POOLED | stack | 0.506 [0.48,0.53] | 0.474 [0.44,0.51] | - | 0.472 | - | - | - | - | - | - |  | short by 0.206 AUC, 5 of 5 econ |
| F14-18 | +30 | POOLED | stack | 0.506 [0.48,0.53] | 0.474 [0.44,0.51] | - | 0.472 | - | - | - | - | - | - |  | short by 0.206 AUC, 5 of 5 econ |
| F14-18 | +30 | POOLED | stack | 0.506 [0.48,0.53] | 0.474 [0.44,0.51] | - | 0.472 | - | - | - | - | - | - |  | short by 0.206 AUC, 5 of 5 econ |
| F14-18 | +30 | POOLED | stack | 0.506 [0.48,0.53] | 0.474 [0.44,0.51] | - | 0.472 | - | - | - | - | - | - |  | short by 0.206 AUC, 5 of 5 econ |
| F14-18 | +30 | POOLED | stack | 0.506 [0.48,0.53] | 0.474 [0.44,0.51] | - | 0.472 | - | - | - | - | - | - |  | short by 0.206 AUC, 5 of 5 econ |
| F14-18 | +30 | POOLED | stack | 0.506 [0.48,0.53] | 0.474 [0.44,0.51] | - | 0.472 | - | - | - | - | - | - |  | short by 0.206 AUC, 5 of 5 econ |
| F5-8+base | +20 | POOLED | stack | 0.497 [0.47,0.52] | 0.474 [0.44,0.51] | - | 0.469 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +10 | POOLED | stack | 0.505 [0.48,0.53] | 0.474 [0.43,0.52] | - | 0.468 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +10 | POOLED | stack | 0.505 [0.48,0.53] | 0.474 [0.43,0.52] | - | 0.468 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +10 | LONDON | stack | 0.501 [0.46,0.55] | 0.474 [0.42,0.54] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | LONDON | stack | 0.501 [0.46,0.55] | 0.474 [0.42,0.54] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | LONDON | stack | 0.501 [0.46,0.55] | 0.474 [0.42,0.54] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | LONDON | stack | 0.501 [0.46,0.55] | 0.474 [0.42,0.54] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +10 | LONDON | stack | 0.501 [0.46,0.55] | 0.474 [0.42,0.54] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | LONDON | gbt3 | 0.479 [0.44,0.53] | 0.473 [0.41,0.53] | - | 0.469 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | LONDON | gbt3 | 0.479 [0.44,0.53] | 0.473 [0.41,0.53] | - | 0.469 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | NY | gbt3 | 0.482 [0.44,0.53] | 0.473 [0.42,0.53] | - | 0.466 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | NY | gbt3 | 0.482 [0.44,0.53] | 0.473 [0.42,0.53] | - | 0.466 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | POOLED | stack | 0.504 [0.48,0.53] | 0.473 [0.43,0.52] | - | 0.467 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4+base | +45 | NY | gbt3 | 0.460 [0.42,0.50] | 0.473 [0.41,0.53] | - | 0.474 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | NY | gbt3 | 0.460 [0.42,0.50] | 0.473 [0.41,0.53] | - | 0.474 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | NY | gbt3 | 0.460 [0.42,0.50] | 0.473 [0.41,0.53] | - | 0.474 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | NY | rf | 0.488 [0.45,0.53] | 0.473 [0.41,0.54] | - | 0.469 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | ASIA | rf | 0.499 [0.46,0.54] | 0.473 [0.41,0.54] | - | 0.468 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | ASIA | rf | 0.499 [0.46,0.54] | 0.473 [0.41,0.54] | - | 0.468 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18+base | +45 | LONDON | rf | 0.500 [0.45,0.55] | 0.473 [0.41,0.54] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | LONDON | rf | 0.500 [0.45,0.55] | 0.473 [0.41,0.54] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | LONDON | rf | 0.500 [0.45,0.55] | 0.473 [0.41,0.54] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | LONDON | rf | 0.500 [0.45,0.55] | 0.473 [0.41,0.54] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | POOLED | stack | 0.508 [0.48,0.53] | 0.473 [0.44,0.50] | - | 0.470 | - | - | - | - | - | - |  | short by 0.207 AUC, 5 of 5 econ |
| F9-13 | +30 | POOLED | stack | 0.508 [0.48,0.53] | 0.473 [0.44,0.50] | - | 0.470 | - | - | - | - | - | - |  | short by 0.207 AUC, 5 of 5 econ |
| F9-13 | +30 | POOLED | stack | 0.508 [0.48,0.53] | 0.473 [0.44,0.50] | - | 0.470 | - | - | - | - | - | - |  | short by 0.207 AUC, 5 of 5 econ |
| F9-13 | +30 | POOLED | stack | 0.508 [0.48,0.53] | 0.473 [0.44,0.50] | - | 0.470 | - | - | - | - | - | - |  | short by 0.207 AUC, 5 of 5 econ |
| F9-13 | +30 | POOLED | stack | 0.508 [0.48,0.53] | 0.473 [0.44,0.50] | - | 0.470 | - | - | - | - | - | - |  | short by 0.207 AUC, 5 of 5 econ |
| F9-13 | +30 | POOLED | stack | 0.508 [0.48,0.53] | 0.473 [0.44,0.50] | - | 0.470 | - | - | - | - | - | - |  | short by 0.207 AUC, 5 of 5 econ |
| F9-13 | +45 | LONDON | rf | 0.482 [0.44,0.52] | 0.473 [0.42,0.53] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | LONDON | rf | 0.482 [0.44,0.52] | 0.473 [0.42,0.53] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | LONDON | rf | 0.482 [0.44,0.52] | 0.473 [0.42,0.53] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | LONDON | rf | 0.482 [0.44,0.52] | 0.473 [0.42,0.53] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | NY | gbt3 | 0.501 [0.46,0.55] | 0.473 [0.41,0.54] | - | 0.466 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +10 | NY | gbt3 | 0.501 [0.46,0.55] | 0.473 [0.41,0.54] | - | 0.466 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | POOLED | stack | 0.496 [0.47,0.52] | 0.473 [0.43,0.51] | - | 0.463 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | NY | gbt3 | 0.506 [0.46,0.54] | 0.473 [0.41,0.54] | - | 0.475 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | NY | gbt3 | 0.506 [0.46,0.54] | 0.473 [0.41,0.54] | - | 0.475 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | POOLED | stack | 0.513 [0.49,0.54] | 0.472 [0.43,0.51] | - | 0.465 | - | - | - | - | - | - |  | short by 0.208 AUC, 5 of 5 econ |
| F1-4 | +30 | POOLED | stack | 0.513 [0.49,0.54] | 0.472 [0.43,0.51] | - | 0.465 | - | - | - | - | - | - |  | short by 0.208 AUC, 5 of 5 econ |
| F1-4 | +30 | POOLED | stack | 0.513 [0.49,0.54] | 0.472 [0.43,0.51] | - | 0.465 | - | - | - | - | - | - |  | short by 0.208 AUC, 5 of 5 econ |
| F1-4 | +30 | POOLED | stack | 0.513 [0.49,0.54] | 0.472 [0.43,0.51] | - | 0.465 | - | - | - | - | - | - |  | short by 0.208 AUC, 5 of 5 econ |
| F1-4 | +30 | POOLED | stack | 0.513 [0.49,0.54] | 0.472 [0.43,0.51] | - | 0.465 | - | - | - | - | - | - |  | short by 0.208 AUC, 5 of 5 econ |
| F1-4 | +30 | POOLED | stack | 0.513 [0.49,0.54] | 0.472 [0.43,0.51] | - | 0.465 | - | - | - | - | - | - |  | short by 0.208 AUC, 5 of 5 econ |
| F5-8+base | +45 | NY | gbt3 | 0.475 [0.43,0.52] | 0.472 [0.40,0.54] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | NY | gbt3 | 0.475 [0.43,0.52] | 0.472 [0.40,0.54] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | NY | gbt3 | 0.475 [0.43,0.52] | 0.472 [0.40,0.54] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | NY | stack | 0.516 [0.47,0.56] | 0.472 [0.41,0.54] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | LONDON | rf | 0.509 [0.46,0.55] | 0.472 [0.40,0.54] | - | 0.472 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | LONDON | rf | 0.509 [0.46,0.55] | 0.472 [0.40,0.54] | - | 0.472 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | LONDON | rf | 0.509 [0.46,0.55] | 0.472 [0.40,0.54] | - | 0.472 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | ASIA | stack | 0.525 [0.49,0.56] | 0.472 [0.41,0.53] | - | 0.461 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | ASIA | stack | 0.525 [0.49,0.56] | 0.472 [0.41,0.53] | - | 0.461 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | ASIA | stack | 0.525 [0.49,0.56] | 0.472 [0.41,0.53] | - | 0.461 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | ASIA | stack | 0.525 [0.49,0.56] | 0.472 [0.41,0.53] | - | 0.461 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +5 | NY | logit2 | 0.480 [0.44,0.52] | 0.472 [0.40,0.53] | - | 0.475 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | NY | logit2 | 0.480 [0.44,0.52] | 0.472 [0.40,0.53] | - | 0.475 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | ASIA | stack | 0.507 [0.47,0.55] | 0.472 [0.42,0.53] | - | 0.462 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13 | +30 | NY | rf | 0.474 [0.43,0.52] | 0.472 [0.41,0.53] | - | 0.474 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | NY | rf | 0.474 [0.43,0.52] | 0.472 [0.41,0.53] | - | 0.474 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | NY | rf | 0.474 [0.43,0.52] | 0.472 [0.41,0.53] | - | 0.474 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | NY | rf | 0.474 [0.43,0.52] | 0.472 [0.41,0.53] | - | 0.474 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | POOLED | stack | 0.498 [0.47,0.53] | 0.471 [0.44,0.50] | - | 0.465 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +10 | NY | gbt3 | 0.486 [0.44,0.53] | 0.471 [0.41,0.53] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +10 | NY | gbt3 | 0.486 [0.44,0.53] | 0.471 [0.41,0.53] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | POOLED | gbt3 | 0.499 [0.48,0.52] | 0.471 [0.44,0.51] | - | 0.470 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | POOLED | gbt3 | 0.499 [0.48,0.52] | 0.471 [0.44,0.51] | - | 0.470 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +60 | NY | logit2 | 0.468 [0.43,0.51] | 0.471 [0.41,0.54] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | NY | logit2 | 0.468 [0.43,0.51] | 0.471 [0.41,0.54] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | NY | logit2 | 0.468 [0.43,0.51] | 0.471 [0.41,0.54] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | POOLED | gbt3 | 0.499 [0.47,0.52] | 0.470 [0.43,0.51] | - | 0.466 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +5 | ASIA | logit2 | 0.492 [0.45,0.53] | 0.470 [0.41,0.53] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +5 | ASIA | logit2 | 0.492 [0.45,0.53] | 0.470 [0.41,0.53] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +10 | POOLED | stack | 0.503 [0.48,0.53] | 0.470 [0.43,0.51] | - | 0.463 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +10 | POOLED | stack | 0.503 [0.48,0.53] | 0.470 [0.43,0.51] | - | 0.463 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +30 | LONDON | rf | 0.450 [0.41,0.49] | 0.470 [0.41,0.53] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | LONDON | rf | 0.508 [0.46,0.55] | 0.470 [0.41,0.53] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | LONDON | rf | 0.508 [0.46,0.55] | 0.470 [0.41,0.53] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | LONDON | rf | 0.508 [0.46,0.55] | 0.470 [0.41,0.53] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | LONDON | gbt3 | 0.475 [0.44,0.52] | 0.470 [0.42,0.53] | - | 0.471 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | POOLED | stack | 0.505 [0.48,0.53] | 0.470 [0.44,0.51] | - | 0.467 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +15 | POOLED | stack | 0.505 [0.48,0.53] | 0.470 [0.44,0.51] | - | 0.467 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +15 | POOLED | stack | 0.505 [0.48,0.53] | 0.470 [0.44,0.51] | - | 0.467 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +15 | POOLED | stack | 0.505 [0.48,0.53] | 0.470 [0.44,0.51] | - | 0.467 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +15 | POOLED | stack | 0.505 [0.48,0.53] | 0.470 [0.44,0.51] | - | 0.467 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +45 | LONDON | gbt3 | 0.482 [0.44,0.53] | 0.470 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | LONDON | gbt3 | 0.482 [0.44,0.53] | 0.470 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | LONDON | rf | 0.488 [0.45,0.53] | 0.469 [0.41,0.53] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | LONDON | rf | 0.488 [0.45,0.53] | 0.469 [0.41,0.53] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +20 | LONDON | rf | 0.488 [0.45,0.53] | 0.469 [0.41,0.53] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | LONDON | logit2 | 0.511 [0.47,0.55] | 0.469 [0.41,0.53] | - | 0.464 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | ASIA | stack | 0.519 [0.49,0.56] | 0.469 [0.41,0.52] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | pre | ASIA | stack | 0.519 [0.49,0.56] | 0.469 [0.41,0.52] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | pre | ASIA | stack | 0.519 [0.49,0.56] | 0.469 [0.41,0.52] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | pre | ASIA | stack | 0.519 [0.49,0.56] | 0.469 [0.41,0.52] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +30 | POOLED | stack | 0.503 [0.48,0.53] | 0.469 [0.43,0.51] | - | 0.462 | - | - | - | - | - | - |  | short by 0.211 AUC, 5 of 5 econ |
| F5-8 | +30 | POOLED | stack | 0.503 [0.48,0.53] | 0.469 [0.43,0.51] | - | 0.462 | - | - | - | - | - | - |  | short by 0.211 AUC, 5 of 5 econ |
| F5-8 | +30 | POOLED | stack | 0.503 [0.48,0.53] | 0.469 [0.43,0.51] | - | 0.462 | - | - | - | - | - | - |  | short by 0.211 AUC, 5 of 5 econ |
| F5-8 | +30 | POOLED | stack | 0.503 [0.48,0.53] | 0.469 [0.43,0.51] | - | 0.462 | - | - | - | - | - | - |  | short by 0.211 AUC, 5 of 5 econ |
| F5-8 | +30 | POOLED | stack | 0.503 [0.48,0.53] | 0.469 [0.43,0.51] | - | 0.462 | - | - | - | - | - | - |  | short by 0.211 AUC, 5 of 5 econ |
| F5-8 | +30 | POOLED | stack | 0.503 [0.48,0.53] | 0.469 [0.43,0.51] | - | 0.462 | - | - | - | - | - | - |  | short by 0.211 AUC, 5 of 5 econ |
| F14-18 | +60 | POOLED | gbt3 | 0.493 [0.47,0.52] | 0.469 [0.44,0.50] | - | 0.469 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | POOLED | gbt3 | 0.493 [0.47,0.52] | 0.469 [0.44,0.50] | - | 0.469 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +15 | ASIA | stack | 0.524 [0.48,0.56] | 0.468 [0.40,0.54] | - | 0.450 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +15 | ASIA | stack | 0.524 [0.48,0.56] | 0.468 [0.40,0.54] | - | 0.450 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18 | +60 | POOLED | logit2 | 0.494 [0.47,0.52] | 0.468 [0.44,0.50] | - | 0.467 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | NY | gbt3 | 0.456 [0.42,0.50] | 0.468 [0.41,0.53] | - | 0.470 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | LONDON | gbt3 | 0.500 [0.46,0.54] | 0.468 [0.41,0.53] | - | 0.467 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | LONDON | gbt3 | 0.500 [0.46,0.54] | 0.468 [0.41,0.53] | - | 0.467 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | LONDON | gbt3 | 0.500 [0.46,0.54] | 0.468 [0.41,0.53] | - | 0.467 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +20 | LONDON | gbt3 | 0.500 [0.46,0.54] | 0.468 [0.41,0.53] | - | 0.467 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | LONDON | gbt3 | 0.477 [0.43,0.52] | 0.467 [0.40,0.54] | - | 0.463 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | LONDON | stack | 0.496 [0.45,0.55] | 0.467 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | LONDON | stack | 0.496 [0.45,0.55] | 0.467 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | LONDON | stack | 0.496 [0.45,0.55] | 0.467 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | LONDON | stack | 0.496 [0.45,0.55] | 0.467 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | LONDON | stack | 0.496 [0.45,0.55] | 0.467 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | LONDON | stack | 0.496 [0.45,0.55] | 0.467 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | POOLED | rf | 0.497 [0.47,0.52] | 0.467 [0.43,0.50] | - | 0.468 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | pre | POOLED | rf | 0.497 [0.47,0.52] | 0.467 [0.43,0.50] | - | 0.468 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | pre | POOLED | rf | 0.497 [0.47,0.52] | 0.467 [0.43,0.50] | - | 0.468 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | pre | POOLED | rf | 0.497 [0.47,0.52] | 0.467 [0.43,0.50] | - | 0.468 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | pre | POOLED | rf | 0.497 [0.47,0.52] | 0.467 [0.43,0.50] | - | 0.468 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +20 | NY | rf | 0.460 [0.42,0.51] | 0.467 [0.40,0.53] | - | 0.470 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | LONDON | logit2 | 0.465 [0.42,0.51] | 0.467 [0.40,0.53] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | LONDON | stack | 0.487 [0.44,0.54] | 0.467 [0.41,0.53] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | LONDON | stack | 0.487 [0.44,0.54] | 0.467 [0.41,0.53] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | LONDON | stack | 0.487 [0.44,0.54] | 0.467 [0.41,0.53] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | LONDON | stack | 0.487 [0.44,0.54] | 0.467 [0.41,0.53] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | LONDON | stack | 0.487 [0.44,0.54] | 0.467 [0.41,0.53] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | NY | stack | 0.501 [0.45,0.55] | 0.467 [0.39,0.54] | - | 0.488 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | POOLED | stack | 0.506 [0.48,0.53] | 0.467 [0.42,0.51] | - | 0.457 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +15 | POOLED | stack | 0.506 [0.48,0.53] | 0.467 [0.42,0.51] | - | 0.457 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +15 | POOLED | stack | 0.506 [0.48,0.53] | 0.467 [0.42,0.51] | - | 0.457 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +15 | POOLED | stack | 0.506 [0.48,0.53] | 0.467 [0.42,0.51] | - | 0.457 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +15 | POOLED | stack | 0.506 [0.48,0.53] | 0.467 [0.42,0.51] | - | 0.457 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +15 | LONDON | stack | 0.512 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | LONDON | stack | 0.512 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | LONDON | stack | 0.512 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | LONDON | stack | 0.512 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | LONDON | stack | 0.512 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | LONDON | stack | 0.512 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | LONDON | stack | 0.512 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | LONDON | gbt3 | 0.520 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | LONDON | gbt3 | 0.520 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | LONDON | gbt3 | 0.520 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +20 | LONDON | gbt3 | 0.520 [0.47,0.56] | 0.467 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | ASIA | stack | 0.509 [0.47,0.55] | 0.466 [0.40,0.53] | - | 0.472 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8 | +15 | NY | logit2 | 0.482 [0.44,0.52] | 0.466 [0.40,0.53] | - | 0.468 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | NY | logit2 | 0.482 [0.44,0.52] | 0.466 [0.40,0.53] | - | 0.468 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | NY | logit2 | 0.482 [0.44,0.52] | 0.466 [0.40,0.53] | - | 0.468 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | NY | logit2 | 0.482 [0.44,0.52] | 0.466 [0.40,0.53] | - | 0.468 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +15 | NY | logit2 | 0.482 [0.44,0.52] | 0.466 [0.40,0.53] | - | 0.468 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | NY | stack | 0.510 [0.47,0.55] | 0.465 [0.41,0.53] | - | 0.473 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | NY | rf | 0.476 [0.44,0.52] | 0.465 [0.41,0.52] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | NY | rf | 0.476 [0.44,0.52] | 0.465 [0.41,0.52] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | NY | rf | 0.476 [0.44,0.52] | 0.465 [0.41,0.52] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | NY | rf | 0.476 [0.44,0.52] | 0.465 [0.41,0.52] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | NY | rf | 0.476 [0.44,0.52] | 0.465 [0.41,0.52] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | POOLED | rf | 0.494 [0.47,0.52] | 0.465 [0.43,0.50] | - | 0.462 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +5 | POOLED | rf | 0.494 [0.47,0.52] | 0.465 [0.43,0.50] | - | 0.462 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +5 | POOLED | rf | 0.494 [0.47,0.52] | 0.465 [0.43,0.50] | - | 0.462 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +5 | LONDON | gbt3 | 0.504 [0.46,0.54] | 0.465 [0.42,0.51] | - | 0.467 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | POOLED | stack | 0.502 [0.48,0.53] | 0.465 [0.43,0.50] | - | 0.466 | - | - | - | - | - | - | stack | short by 0.215 AUC, 5 of 5 econ |
| F9-13+base | +30 | POOLED | stack | 0.502 [0.48,0.53] | 0.465 [0.43,0.50] | - | 0.466 | - | - | - | - | - | - | stack | short by 0.215 AUC, 5 of 5 econ |
| F9-13+base | +30 | POOLED | stack | 0.502 [0.48,0.53] | 0.465 [0.43,0.50] | - | 0.466 | - | - | - | - | - | - | stack | short by 0.215 AUC, 5 of 5 econ |
| F9-13+base | +30 | POOLED | stack | 0.502 [0.48,0.53] | 0.465 [0.43,0.50] | - | 0.466 | - | - | - | - | - | - | stack | short by 0.215 AUC, 5 of 5 econ |
| F9-13+base | +30 | POOLED | stack | 0.502 [0.48,0.53] | 0.465 [0.43,0.50] | - | 0.466 | - | - | - | - | - | - | stack | short by 0.215 AUC, 5 of 5 econ |
| F9-13+base | +30 | POOLED | stack | 0.502 [0.48,0.53] | 0.465 [0.43,0.50] | - | 0.466 | - | - | - | - | - | - | stack | short by 0.215 AUC, 5 of 5 econ |
| F1-4+base | +60 | LONDON | stack | 0.538 [0.49,0.59] | 0.464 [0.41,0.52] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +60 | LONDON | stack | 0.538 [0.49,0.59] | 0.464 [0.41,0.52] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | LONDON | gbt3 | 0.468 [0.42,0.51] | 0.464 [0.40,0.53] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | POOLED | rf | 0.497 [0.47,0.52] | 0.464 [0.43,0.50] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +10 | POOLED | rf | 0.497 [0.47,0.52] | 0.464 [0.43,0.50] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +10 | POOLED | rf | 0.497 [0.47,0.52] | 0.464 [0.43,0.50] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +10 | POOLED | rf | 0.497 [0.47,0.52] | 0.464 [0.43,0.50] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +10 | POOLED | rf | 0.497 [0.47,0.52] | 0.464 [0.43,0.50] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | pre | LONDON | gbt3 | 0.470 [0.43,0.51] | 0.464 [0.40,0.53] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | LONDON | gbt3 | 0.492 [0.45,0.53] | 0.463 [0.40,0.52] | - | 0.457 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +20 | POOLED | stack | 0.504 [0.48,0.53] | 0.463 [0.43,0.50] | - | 0.454 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +5 | POOLED | stack | 0.485 [0.46,0.51] | 0.463 [0.42,0.50] | - | 0.461 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +5 | POOLED | stack | 0.485 [0.46,0.51] | 0.463 [0.42,0.50] | - | 0.461 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +5 | NY | rf | 0.460 [0.42,0.50] | 0.463 [0.40,0.52] | - | 0.462 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | NY | rf | 0.460 [0.42,0.50] | 0.463 [0.40,0.52] | - | 0.462 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | LONDON | logit2 | 0.486 [0.44,0.53] | 0.462 [0.41,0.52] | - | 0.458 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | ASIA | rf | 0.500 [0.46,0.54] | 0.462 [0.40,0.52] | - | 0.452 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +5 | ASIA | rf | 0.500 [0.46,0.54] | 0.462 [0.40,0.52] | - | 0.452 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +10 | ASIA | stack | 0.533 [0.49,0.57] | 0.462 [0.41,0.52] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +10 | ASIA | stack | 0.533 [0.49,0.57] | 0.462 [0.41,0.52] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +10 | ASIA | stack | 0.533 [0.49,0.57] | 0.462 [0.41,0.52] | - | 0.463 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | ASIA | rf | 0.490 [0.45,0.53] | 0.462 [0.40,0.52] | - | 0.454 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | ASIA | rf | 0.490 [0.45,0.53] | 0.462 [0.40,0.52] | - | 0.454 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | POOLED | gbt3 | 0.488 [0.47,0.51] | 0.462 [0.43,0.50] | - | 0.457 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | POOLED | gbt3 | 0.488 [0.47,0.51] | 0.462 [0.43,0.50] | - | 0.457 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +60 | POOLED | stack | 0.501 [0.47,0.53] | 0.462 [0.42,0.51] | - | 0.457 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | NY | rf | 0.471 [0.43,0.52] | 0.462 [0.40,0.53] | - | 0.455 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | NY | rf | 0.471 [0.43,0.52] | 0.462 [0.40,0.53] | - | 0.455 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | NY | rf | 0.471 [0.43,0.52] | 0.462 [0.40,0.53] | - | 0.455 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | NY | rf | 0.471 [0.43,0.52] | 0.462 [0.40,0.53] | - | 0.455 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | LONDON | stack | 0.488 [0.44,0.53] | 0.462 [0.40,0.53] | - | 0.450 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | LONDON | stack | 0.488 [0.44,0.53] | 0.462 [0.40,0.53] | - | 0.450 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | LONDON | stack | 0.488 [0.44,0.53] | 0.462 [0.40,0.53] | - | 0.450 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | LONDON | stack | 0.488 [0.44,0.53] | 0.462 [0.40,0.53] | - | 0.450 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | LONDON | stack | 0.488 [0.44,0.53] | 0.462 [0.40,0.53] | - | 0.450 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | pre | LONDON | stack | 0.488 [0.44,0.53] | 0.462 [0.40,0.53] | - | 0.450 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | POOLED | rf | 0.496 [0.47,0.52] | 0.461 [0.43,0.50] | - | 0.460 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | POOLED | rf | 0.496 [0.47,0.52] | 0.461 [0.43,0.50] | - | 0.460 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | POOLED | rf | 0.496 [0.47,0.52] | 0.461 [0.43,0.50] | - | 0.460 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | POOLED | rf | 0.496 [0.47,0.52] | 0.461 [0.43,0.50] | - | 0.460 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | POOLED | rf | 0.496 [0.47,0.52] | 0.461 [0.43,0.50] | - | 0.460 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4+base | +5 | POOLED | stack | 0.491 [0.47,0.52] | 0.461 [0.42,0.50] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +5 | POOLED | stack | 0.491 [0.47,0.52] | 0.461 [0.42,0.50] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18 | +5 | NY | gbt3 | 0.472 [0.43,0.52] | 0.461 [0.40,0.53] | - | 0.468 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | NY | gbt3 | 0.472 [0.43,0.52] | 0.461 [0.40,0.53] | - | 0.468 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | NY | gbt3 | 0.472 [0.43,0.52] | 0.461 [0.40,0.53] | - | 0.468 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | NY | gbt3 | 0.472 [0.43,0.52] | 0.461 [0.40,0.53] | - | 0.468 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | POOLED | rf | 0.490 [0.46,0.52] | 0.461 [0.43,0.49] | - | 0.455 | - | - | - | - | - | - |  | short by 0.219 AUC, 5 of 5 econ |
| F9-13 | +10 | LONDON | logit2 | 0.499 [0.46,0.54] | 0.461 [0.40,0.52] | - | 0.461 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | NY | rf | 0.466 [0.42,0.51] | 0.461 [0.40,0.52] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | NY | rf | 0.466 [0.42,0.51] | 0.461 [0.40,0.52] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | NY | rf | 0.466 [0.42,0.51] | 0.461 [0.40,0.52] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | NY | rf | 0.466 [0.42,0.51] | 0.461 [0.40,0.52] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | NY | rf | 0.466 [0.42,0.51] | 0.461 [0.40,0.52] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | LONDON | stack | 0.524 [0.48,0.57] | 0.460 [0.39,0.53] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | LONDON | stack | 0.524 [0.48,0.57] | 0.460 [0.39,0.53] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | LONDON | stack | 0.524 [0.48,0.57] | 0.460 [0.39,0.53] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | LONDON | stack | 0.524 [0.48,0.57] | 0.460 [0.39,0.53] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | LONDON | stack | 0.524 [0.48,0.57] | 0.460 [0.39,0.53] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | LONDON | stack | 0.524 [0.48,0.57] | 0.460 [0.39,0.53] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | LONDON | stack | 0.524 [0.48,0.57] | 0.460 [0.39,0.53] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | POOLED | rf | 0.489 [0.46,0.52] | 0.460 [0.43,0.50] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | POOLED | rf | 0.489 [0.46,0.52] | 0.460 [0.43,0.50] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | POOLED | rf | 0.489 [0.46,0.52] | 0.460 [0.43,0.50] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | POOLED | rf | 0.489 [0.46,0.52] | 0.460 [0.43,0.50] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | POOLED | rf | 0.489 [0.46,0.52] | 0.460 [0.43,0.50] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +30 | NY | rf | 0.464 [0.42,0.51] | 0.460 [0.41,0.52] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | NY | rf | 0.464 [0.42,0.51] | 0.460 [0.41,0.52] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | NY | rf | 0.464 [0.42,0.51] | 0.460 [0.41,0.52] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | NY | rf | 0.464 [0.42,0.51] | 0.460 [0.41,0.52] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | LONDON | stack | 0.507 [0.46,0.55] | 0.460 [0.40,0.52] | - | 0.450 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +60 | LONDON | stack | 0.507 [0.46,0.55] | 0.460 [0.40,0.52] | - | 0.450 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | NY | stack | 0.491 [0.45,0.53] | 0.460 [0.41,0.52] | - | 0.450 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | NY | stack | 0.491 [0.45,0.53] | 0.460 [0.41,0.52] | - | 0.450 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +45 | NY | stack | 0.491 [0.45,0.53] | 0.460 [0.41,0.52] | - | 0.450 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | POOLED | stack | 0.494 [0.47,0.52] | 0.460 [0.42,0.50] | - | 0.456 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | POOLED | stack | 0.494 [0.47,0.52] | 0.460 [0.42,0.50] | - | 0.456 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +5 | POOLED | stack | 0.497 [0.47,0.53] | 0.460 [0.42,0.50] | - | 0.456 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +5 | POOLED | stack | 0.497 [0.47,0.53] | 0.460 [0.42,0.50] | - | 0.456 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18+base | +45 | ASIA | stack | 0.506 [0.46,0.55] | 0.459 [0.38,0.53] | - | 0.447 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | LONDON | logit2 | 0.505 [0.46,0.55] | 0.459 [0.41,0.52] | - | 0.459 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | LONDON | logit2 | 0.505 [0.46,0.55] | 0.459 [0.41,0.52] | - | 0.459 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | ASIA | stack | 0.508 [0.46,0.55] | 0.459 [0.40,0.52] | - | 0.458 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | POOLED | gbt3 | 0.488 [0.46,0.51] | 0.459 [0.42,0.49] | - | 0.455 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +15 | POOLED | stack | 0.494 [0.47,0.52] | 0.458 [0.42,0.51] | - | 0.450 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +15 | POOLED | stack | 0.494 [0.47,0.52] | 0.458 [0.42,0.51] | - | 0.450 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +15 | POOLED | stack | 0.494 [0.47,0.52] | 0.458 [0.42,0.51] | - | 0.450 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +15 | POOLED | stack | 0.494 [0.47,0.52] | 0.458 [0.42,0.51] | - | 0.450 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +15 | POOLED | stack | 0.494 [0.47,0.52] | 0.458 [0.42,0.51] | - | 0.450 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +10 | POOLED | stack | 0.502 [0.48,0.53] | 0.458 [0.42,0.50] | - | 0.458 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +10 | POOLED | stack | 0.502 [0.48,0.53] | 0.458 [0.42,0.50] | - | 0.458 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +60 | LONDON | gbt3 | 0.503 [0.46,0.55] | 0.458 [0.40,0.52] | - | 0.456 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | NY | gbt3 | 0.472 [0.43,0.51] | 0.458 [0.40,0.52] | - | 0.448 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +20 | ASIA | stack | 0.505 [0.46,0.55] | 0.458 [0.40,0.52] | - | 0.442 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +20 | ASIA | stack | 0.505 [0.46,0.55] | 0.458 [0.40,0.52] | - | 0.442 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +20 | ASIA | stack | 0.505 [0.46,0.55] | 0.458 [0.40,0.52] | - | 0.442 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +20 | ASIA | stack | 0.505 [0.46,0.55] | 0.458 [0.40,0.52] | - | 0.442 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +10 | NY | gbt3 | 0.479 [0.43,0.53] | 0.458 [0.40,0.52] | - | 0.469 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | NY | gbt3 | 0.479 [0.43,0.53] | 0.458 [0.40,0.52] | - | 0.469 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +15 | ASIA | stack | 0.479 [0.44,0.52] | 0.458 [0.40,0.52] | - | 0.452 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +15 | ASIA | stack | 0.479 [0.44,0.52] | 0.458 [0.40,0.52] | - | 0.452 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4+base | +5 | LONDON | stack | 0.506 [0.45,0.56] | 0.457 [0.39,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | LONDON | stack | 0.506 [0.45,0.56] | 0.457 [0.39,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | LONDON | stack | 0.506 [0.45,0.56] | 0.457 [0.39,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | LONDON | stack | 0.506 [0.45,0.56] | 0.457 [0.39,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | LONDON | stack | 0.506 [0.45,0.56] | 0.457 [0.39,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | LONDON | stack | 0.506 [0.45,0.56] | 0.457 [0.39,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +5 | LONDON | stack | 0.506 [0.45,0.56] | 0.457 [0.39,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | NY | gbt3 | 0.464 [0.42,0.51] | 0.457 [0.39,0.53] | - | 0.454 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | ASIA | stack | 0.504 [0.46,0.54] | 0.457 [0.39,0.52] | - | 0.442 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +15 | ASIA | stack | 0.504 [0.46,0.54] | 0.457 [0.39,0.52] | - | 0.442 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +10 | POOLED | gbt3 | 0.480 [0.46,0.50] | 0.457 [0.42,0.49] | - | 0.456 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +15 | NY | rf | 0.471 [0.43,0.52] | 0.457 [0.40,0.52] | - | 0.456 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | ASIA | stack | 0.533 [0.49,0.58] | 0.456 [0.39,0.53] | - | 0.444 | - | - | - | - | - | - |  | WF-only (dead) |
| F9-13 | pre | POOLED | logit2 | 0.487 [0.46,0.51] | 0.456 [0.42,0.49] | - | 0.456 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +30 | NY | stack | 0.476 [0.43,0.52] | 0.456 [0.38,0.53] | - | 0.456 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | NY | stack | 0.476 [0.43,0.52] | 0.456 [0.38,0.53] | - | 0.456 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | NY | stack | 0.476 [0.43,0.52] | 0.456 [0.38,0.53] | - | 0.456 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | NY | stack | 0.476 [0.43,0.52] | 0.456 [0.38,0.53] | - | 0.456 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | LONDON | stack | 0.499 [0.46,0.55] | 0.455 [0.39,0.51] | - | 0.452 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | LONDON | stack | 0.499 [0.46,0.55] | 0.455 [0.39,0.51] | - | 0.452 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | LONDON | stack | 0.499 [0.46,0.55] | 0.455 [0.39,0.51] | - | 0.452 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | LONDON | stack | 0.499 [0.46,0.55] | 0.455 [0.39,0.51] | - | 0.452 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | LONDON | stack | 0.499 [0.46,0.55] | 0.455 [0.39,0.51] | - | 0.452 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | LONDON | stack | 0.499 [0.46,0.55] | 0.455 [0.39,0.51] | - | 0.452 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | POOLED | gbt3 | 0.499 [0.48,0.53] | 0.455 [0.42,0.49] | - | 0.453 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | POOLED | gbt3 | 0.499 [0.48,0.53] | 0.455 [0.42,0.49] | - | 0.453 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +60 | LONDON | stack | 0.500 [0.46,0.54] | 0.455 [0.39,0.52] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | LONDON | stack | 0.500 [0.46,0.54] | 0.455 [0.39,0.52] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | LONDON | stack | 0.493 [0.45,0.54] | 0.455 [0.39,0.52] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | LONDON | stack | 0.493 [0.45,0.54] | 0.455 [0.39,0.52] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | LONDON | stack | 0.493 [0.45,0.54] | 0.455 [0.39,0.52] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | LONDON | stack | 0.493 [0.45,0.54] | 0.455 [0.39,0.52] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | LONDON | stack | 0.493 [0.45,0.54] | 0.455 [0.39,0.52] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | LONDON | stack | 0.493 [0.45,0.54] | 0.455 [0.39,0.52] | - | 0.449 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | NY | logit2 | 0.476 [0.44,0.52] | 0.455 [0.40,0.51] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | NY | logit2 | 0.476 [0.44,0.52] | 0.455 [0.40,0.51] | - | 0.466 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | POOLED | rf | 0.483 [0.46,0.51] | 0.454 [0.42,0.49] | - | 0.454 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | POOLED | rf | 0.483 [0.46,0.51] | 0.454 [0.42,0.49] | - | 0.454 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | POOLED | rf | 0.483 [0.46,0.51] | 0.454 [0.42,0.49] | - | 0.454 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | POOLED | rf | 0.483 [0.46,0.51] | 0.454 [0.42,0.49] | - | 0.454 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | pre | POOLED | rf | 0.483 [0.46,0.51] | 0.454 [0.42,0.49] | - | 0.454 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18+base | +30 | ASIA | stack | 0.487 [0.45,0.53] | 0.454 [0.40,0.51] | - | 0.441 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8 | +10 | POOLED | stack | 0.503 [0.48,0.53] | 0.454 [0.42,0.49] | - | 0.450 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +10 | POOLED | stack | 0.503 [0.48,0.53] | 0.454 [0.42,0.49] | - | 0.450 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +60 | POOLED | stack | 0.493 [0.47,0.52] | 0.453 [0.42,0.49] | - | 0.452 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | LONDON | gbt3 | 0.489 [0.44,0.54] | 0.453 [0.40,0.51] | - | 0.452 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | LONDON | gbt3 | 0.489 [0.44,0.54] | 0.453 [0.40,0.51] | - | 0.452 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | NY | rf | 0.475 [0.43,0.52] | 0.453 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | NY | rf | 0.475 [0.43,0.52] | 0.453 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | NY | rf | 0.475 [0.43,0.52] | 0.453 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | NY | rf | 0.475 [0.43,0.52] | 0.453 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | POOLED | stack | 0.493 [0.47,0.52] | 0.453 [0.41,0.49] | - | 0.450 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | POOLED | stack | 0.493 [0.47,0.52] | 0.453 [0.41,0.49] | - | 0.450 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | ASIA | gbt3 | 0.506 [0.47,0.54] | 0.453 [0.40,0.50] | - | 0.453 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | ASIA | gbt3 | 0.506 [0.47,0.54] | 0.453 [0.40,0.50] | - | 0.453 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | ASIA | gbt3 | 0.506 [0.47,0.54] | 0.453 [0.40,0.50] | - | 0.453 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | ASIA | gbt3 | 0.506 [0.47,0.54] | 0.453 [0.40,0.50] | - | 0.453 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | LONDON | logit2 | 0.508 [0.46,0.56] | 0.452 [0.39,0.51] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | LONDON | stack | 0.487 [0.44,0.53] | 0.452 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | LONDON | stack | 0.487 [0.44,0.53] | 0.452 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | LONDON | stack | 0.487 [0.44,0.53] | 0.452 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | LONDON | stack | 0.487 [0.44,0.53] | 0.452 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | LONDON | stack | 0.487 [0.44,0.53] | 0.452 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | LONDON | stack | 0.487 [0.44,0.53] | 0.452 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | LONDON | gbt3 | 0.485 [0.44,0.53] | 0.452 [0.40,0.52] | - | 0.450 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +45 | LONDON | gbt3 | 0.485 [0.44,0.53] | 0.452 [0.40,0.52] | - | 0.450 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | NY | rf | 0.472 [0.43,0.52] | 0.452 [0.40,0.51] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | NY | rf | 0.472 [0.43,0.52] | 0.452 [0.40,0.51] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | LONDON | gbt3 | 0.459 [0.41,0.51] | 0.451 [0.38,0.52] | - | 0.440 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | NY | gbt3 | 0.497 [0.45,0.54] | 0.451 [0.39,0.51] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | NY | gbt3 | 0.497 [0.45,0.54] | 0.451 [0.39,0.51] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | NY | gbt3 | 0.497 [0.45,0.54] | 0.451 [0.39,0.51] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | NY | gbt3 | 0.497 [0.45,0.54] | 0.451 [0.39,0.51] | - | 0.463 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | LONDON | stack | 0.497 [0.45,0.54] | 0.451 [0.38,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | LONDON | stack | 0.497 [0.45,0.54] | 0.451 [0.38,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | LONDON | stack | 0.497 [0.45,0.54] | 0.451 [0.38,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | LONDON | stack | 0.497 [0.45,0.54] | 0.451 [0.38,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | LONDON | stack | 0.497 [0.45,0.54] | 0.451 [0.38,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | LONDON | stack | 0.497 [0.45,0.54] | 0.451 [0.38,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | LONDON | gbt3 | 0.468 [0.42,0.51] | 0.451 [0.38,0.52] | - | 0.445 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | POOLED | stack | 0.492 [0.47,0.52] | 0.451 [0.41,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13+base | +5 | POOLED | stack | 0.492 [0.47,0.52] | 0.451 [0.41,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +30 | POOLED | stack | 0.495 [0.47,0.52] | 0.451 [0.42,0.49] | - | 0.446 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +30 | POOLED | stack | 0.495 [0.47,0.52] | 0.451 [0.42,0.49] | - | 0.446 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +30 | POOLED | stack | 0.495 [0.47,0.52] | 0.451 [0.42,0.49] | - | 0.446 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +30 | POOLED | stack | 0.495 [0.47,0.52] | 0.451 [0.42,0.49] | - | 0.446 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +30 | POOLED | stack | 0.495 [0.47,0.52] | 0.451 [0.42,0.49] | - | 0.446 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +30 | POOLED | stack | 0.495 [0.47,0.52] | 0.451 [0.42,0.49] | - | 0.446 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18 | +60 | LONDON | rf | 0.508 [0.47,0.55] | 0.451 [0.39,0.51] | - | 0.449 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | LONDON | rf | 0.508 [0.47,0.55] | 0.451 [0.39,0.51] | - | 0.449 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | LONDON | rf | 0.508 [0.47,0.55] | 0.451 [0.39,0.51] | - | 0.449 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | NY | logit2 | 0.488 [0.45,0.53] | 0.450 [0.40,0.50] | - | 0.455 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | POOLED | gbt3 | 0.480 [0.45,0.51] | 0.450 [0.41,0.49] | - | 0.441 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | POOLED | gbt3 | 0.480 [0.45,0.51] | 0.450 [0.41,0.49] | - | 0.441 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +60 | LONDON | gbt3 | 0.500 [0.46,0.54] | 0.450 [0.39,0.51] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | ASIA | gbt3 | 0.490 [0.45,0.53] | 0.450 [0.39,0.51] | - | 0.447 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +10 | ASIA | gbt3 | 0.490 [0.45,0.53] | 0.450 [0.39,0.51] | - | 0.447 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +10 | ASIA | gbt3 | 0.490 [0.45,0.53] | 0.450 [0.39,0.51] | - | 0.447 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +30 | LONDON | gbt3 | 0.500 [0.46,0.54] | 0.450 [0.39,0.51] | - | 0.460 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | NY | rf | 0.480 [0.44,0.52] | 0.450 [0.39,0.51] | - | 0.450 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | NY | rf | 0.480 [0.44,0.52] | 0.450 [0.39,0.51] | - | 0.450 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | NY | rf | 0.480 [0.44,0.52] | 0.450 [0.39,0.51] | - | 0.450 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | NY | rf | 0.480 [0.44,0.52] | 0.450 [0.39,0.51] | - | 0.450 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | LONDON | stack | 0.478 [0.44,0.52] | 0.450 [0.39,0.51] | - | 0.442 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | LONDON | stack | 0.478 [0.44,0.52] | 0.450 [0.39,0.51] | - | 0.442 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | LONDON | stack | 0.478 [0.44,0.52] | 0.450 [0.39,0.51] | - | 0.442 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | LONDON | stack | 0.478 [0.44,0.52] | 0.450 [0.39,0.51] | - | 0.442 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | LONDON | stack | 0.478 [0.44,0.52] | 0.450 [0.39,0.51] | - | 0.442 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | pre | LONDON | stack | 0.478 [0.44,0.52] | 0.450 [0.39,0.51] | - | 0.442 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | LONDON | stack | 0.510 [0.46,0.56] | 0.449 [0.38,0.51] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | LONDON | stack | 0.510 [0.46,0.56] | 0.449 [0.38,0.51] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | LONDON | stack | 0.510 [0.46,0.56] | 0.449 [0.38,0.51] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | LONDON | stack | 0.510 [0.46,0.56] | 0.449 [0.38,0.51] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | LONDON | stack | 0.510 [0.46,0.56] | 0.449 [0.38,0.51] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | LONDON | logit2 | 0.469 [0.43,0.51] | 0.449 [0.39,0.51] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | NY | stack | 0.475 [0.43,0.52] | 0.449 [0.38,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | LONDON | stack | 0.500 [0.46,0.54] | 0.449 [0.39,0.51] | - | 0.432 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | LONDON | stack | 0.500 [0.46,0.54] | 0.449 [0.39,0.51] | - | 0.432 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | LONDON | stack | 0.500 [0.46,0.54] | 0.449 [0.39,0.51] | - | 0.432 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | LONDON | stack | 0.500 [0.46,0.54] | 0.449 [0.39,0.51] | - | 0.432 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | LONDON | stack | 0.500 [0.46,0.54] | 0.449 [0.39,0.51] | - | 0.432 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | LONDON | stack | 0.500 [0.46,0.54] | 0.449 [0.39,0.51] | - | 0.432 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +15 | LONDON | stack | 0.500 [0.46,0.54] | 0.449 [0.39,0.51] | - | 0.432 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | ASIA | logit2 | 0.503 [0.46,0.55] | 0.449 [0.39,0.51] | - | 0.446 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +5 | ASIA | logit2 | 0.503 [0.46,0.55] | 0.449 [0.39,0.51] | - | 0.446 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | pre | NY | rf | 0.484 [0.45,0.52] | 0.448 [0.39,0.51] | - | 0.449 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | NY | rf | 0.484 [0.45,0.52] | 0.448 [0.39,0.51] | - | 0.449 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | NY | rf | 0.484 [0.45,0.52] | 0.448 [0.39,0.51] | - | 0.449 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | NY | rf | 0.484 [0.45,0.52] | 0.448 [0.39,0.51] | - | 0.449 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | NY | rf | 0.484 [0.45,0.52] | 0.448 [0.39,0.51] | - | 0.449 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | NY | gbt3 | 0.477 [0.44,0.51] | 0.448 [0.39,0.51] | - | 0.455 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | NY | gbt3 | 0.477 [0.44,0.51] | 0.448 [0.39,0.51] | - | 0.455 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | NY | logit2 | 0.480 [0.44,0.52] | 0.448 [0.39,0.50] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | LONDON | stack | 0.489 [0.44,0.54] | 0.447 [0.39,0.50] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | LONDON | stack | 0.489 [0.44,0.54] | 0.447 [0.39,0.50] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | LONDON | stack | 0.489 [0.44,0.54] | 0.447 [0.39,0.50] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | LONDON | stack | 0.489 [0.44,0.54] | 0.447 [0.39,0.50] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | LONDON | stack | 0.489 [0.44,0.54] | 0.447 [0.39,0.50] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | LONDON | stack | 0.489 [0.44,0.54] | 0.447 [0.39,0.50] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | LONDON | stack | 0.489 [0.44,0.54] | 0.447 [0.39,0.50] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | NY | gbt3 | 0.499 [0.46,0.53] | 0.447 [0.40,0.50] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | NY | logit2 | 0.452 [0.40,0.50] | 0.447 [0.38,0.51] | - | 0.438 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | NY | logit2 | 0.452 [0.40,0.50] | 0.447 [0.38,0.51] | - | 0.438 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | NY | logit2 | 0.452 [0.40,0.50] | 0.447 [0.38,0.51] | - | 0.438 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | LONDON | gbt3 | 0.492 [0.45,0.53] | 0.447 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | LONDON | gbt3 | 0.492 [0.45,0.53] | 0.447 [0.39,0.51] | - | 0.435 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | POOLED | stack | 0.502 [0.47,0.53] | 0.446 [0.40,0.49] | - | 0.437 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +15 | POOLED | stack | 0.502 [0.47,0.53] | 0.446 [0.40,0.49] | - | 0.437 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +15 | POOLED | stack | 0.502 [0.47,0.53] | 0.446 [0.40,0.49] | - | 0.437 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +15 | POOLED | stack | 0.502 [0.47,0.53] | 0.446 [0.40,0.49] | - | 0.437 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +15 | POOLED | stack | 0.502 [0.47,0.53] | 0.446 [0.40,0.49] | - | 0.437 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18 | +10 | POOLED | stack | 0.488 [0.46,0.52] | 0.446 [0.41,0.48] | - | 0.442 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +10 | POOLED | stack | 0.488 [0.46,0.52] | 0.446 [0.41,0.48] | - | 0.442 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +10 | POOLED | stack | 0.499 [0.47,0.52] | 0.446 [0.41,0.49] | - | 0.443 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +10 | POOLED | stack | 0.499 [0.47,0.52] | 0.446 [0.41,0.49] | - | 0.443 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +5 | POOLED | stack | 0.489 [0.47,0.51] | 0.446 [0.41,0.48] | - | 0.442 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F5-8 | +5 | POOLED | stack | 0.489 [0.47,0.51] | 0.446 [0.41,0.48] | - | 0.442 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | +45 | LONDON | rf | 0.490 [0.44,0.54] | 0.445 [0.39,0.50] | - | 0.443 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | LONDON | rf | 0.490 [0.44,0.54] | 0.445 [0.39,0.50] | - | 0.443 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | LONDON | rf | 0.490 [0.44,0.54] | 0.445 [0.39,0.50] | - | 0.443 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | LONDON | rf | 0.490 [0.44,0.54] | 0.445 [0.39,0.50] | - | 0.443 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | LONDON | stack | 0.504 [0.45,0.55] | 0.445 [0.38,0.50] | - | 0.444 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | LONDON | stack | 0.504 [0.45,0.55] | 0.445 [0.38,0.50] | - | 0.444 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | LONDON | stack | 0.504 [0.45,0.55] | 0.445 [0.38,0.50] | - | 0.444 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | LONDON | stack | 0.504 [0.45,0.55] | 0.445 [0.38,0.50] | - | 0.444 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | LONDON | stack | 0.504 [0.45,0.55] | 0.445 [0.38,0.50] | - | 0.444 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | LONDON | stack | 0.504 [0.45,0.55] | 0.445 [0.38,0.50] | - | 0.444 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | NY | gbt3 | 0.462 [0.42,0.51] | 0.444 [0.37,0.52] | - | 0.445 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | LONDON | stack | 0.500 [0.46,0.54] | 0.444 [0.39,0.51] | - | 0.438 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | LONDON | stack | 0.500 [0.46,0.54] | 0.444 [0.39,0.51] | - | 0.438 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | LONDON | stack | 0.500 [0.46,0.54] | 0.444 [0.39,0.51] | - | 0.438 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | LONDON | stack | 0.500 [0.46,0.54] | 0.444 [0.39,0.51] | - | 0.438 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | LONDON | stack | 0.500 [0.46,0.54] | 0.444 [0.39,0.51] | - | 0.438 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | LONDON | stack | 0.500 [0.46,0.54] | 0.444 [0.39,0.51] | - | 0.438 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +5 | LONDON | stack | 0.500 [0.46,0.54] | 0.444 [0.39,0.51] | - | 0.438 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | pre | LONDON | gbt3 | 0.443 [0.40,0.48] | 0.444 [0.39,0.50] | - | 0.441 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +60 | LONDON | gbt3 | 0.476 [0.43,0.52] | 0.444 [0.39,0.50] | - | 0.443 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | NY | gbt3 | 0.482 [0.44,0.53] | 0.443 [0.38,0.52] | - | 0.458 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | NY | logit2 | 0.463 [0.42,0.51] | 0.443 [0.39,0.50] | - | 0.461 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | NY | logit2 | 0.463 [0.42,0.51] | 0.443 [0.39,0.50] | - | 0.461 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | LONDON | gbt3 | 0.495 [0.45,0.54] | 0.443 [0.39,0.50] | - | 0.448 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | NY | gbt3 | 0.475 [0.44,0.52] | 0.443 [0.38,0.51] | - | 0.434 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | LONDON | stack | 0.489 [0.44,0.54] | 0.442 [0.38,0.50] | - | 0.439 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | LONDON | stack | 0.489 [0.44,0.54] | 0.442 [0.38,0.50] | - | 0.439 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | LONDON | stack | 0.489 [0.44,0.54] | 0.442 [0.38,0.50] | - | 0.439 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | LONDON | stack | 0.489 [0.44,0.54] | 0.442 [0.38,0.50] | - | 0.439 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | LONDON | stack | 0.489 [0.44,0.54] | 0.442 [0.38,0.50] | - | 0.439 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | NY | rf | 0.480 [0.44,0.52] | 0.442 [0.39,0.49] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +5 | NY | rf | 0.480 [0.44,0.52] | 0.442 [0.39,0.49] | - | 0.446 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | NY | rf | 0.480 [0.44,0.52] | 0.442 [0.38,0.50] | - | 0.441 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | NY | rf | 0.480 [0.44,0.52] | 0.442 [0.38,0.50] | - | 0.441 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | NY | rf | 0.480 [0.44,0.52] | 0.442 [0.38,0.50] | - | 0.441 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | NY | rf | 0.480 [0.44,0.52] | 0.442 [0.38,0.50] | - | 0.441 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +10 | NY | rf | 0.480 [0.44,0.52] | 0.442 [0.38,0.50] | - | 0.441 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | POOLED | logit2 | 0.485 [0.46,0.51] | 0.441 [0.41,0.48] | - | 0.439 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18+base | +5 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.50] | - | 0.429 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.50] | - | 0.429 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.50] | - | 0.429 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.50] | - | 0.429 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.50] | - | 0.429 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +30 | LONDON | stack | 0.504 [0.46,0.55] | 0.441 [0.39,0.50] | - | 0.429 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | pre | LONDON | logit2 | 0.495 [0.45,0.54] | 0.440 [0.37,0.51] | - | 0.440 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | LONDON | stack | 0.514 [0.47,0.56] | 0.440 [0.38,0.51] | - | 0.440 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | LONDON | stack | 0.514 [0.47,0.56] | 0.440 [0.38,0.51] | - | 0.440 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | LONDON | stack | 0.514 [0.47,0.56] | 0.440 [0.38,0.51] | - | 0.440 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | LONDON | stack | 0.514 [0.47,0.56] | 0.440 [0.38,0.51] | - | 0.440 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | LONDON | stack | 0.514 [0.47,0.56] | 0.440 [0.38,0.51] | - | 0.440 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | LONDON | stack | 0.514 [0.47,0.56] | 0.440 [0.38,0.51] | - | 0.440 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | LONDON | stack | 0.514 [0.47,0.56] | 0.440 [0.38,0.51] | - | 0.440 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | LONDON | stack | 0.507 [0.46,0.55] | 0.439 [0.37,0.51] | - | 0.429 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +60 | LONDON | stack | 0.507 [0.46,0.55] | 0.439 [0.37,0.51] | - | 0.429 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +10 | ASIA | stack | 0.474 [0.43,0.52] | 0.439 [0.38,0.51] | - | 0.428 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +10 | ASIA | stack | 0.474 [0.43,0.52] | 0.439 [0.38,0.51] | - | 0.428 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +10 | ASIA | stack | 0.474 [0.43,0.52] | 0.439 [0.38,0.51] | - | 0.428 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13+base | +60 | LONDON | stack | 0.487 [0.44,0.53] | 0.439 [0.37,0.50] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +60 | LONDON | stack | 0.487 [0.44,0.53] | 0.439 [0.37,0.50] | - | 0.434 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | ASIA | rf | 0.484 [0.44,0.52] | 0.439 [0.38,0.50] | - | 0.436 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F1-4 | pre | ASIA | rf | 0.484 [0.44,0.52] | 0.439 [0.38,0.50] | - | 0.436 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F14-18 | +60 | LONDON | logit2 | 0.481 [0.44,0.52] | 0.439 [0.38,0.50] | - | 0.441 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | LONDON | logit2 | 0.481 [0.44,0.52] | 0.439 [0.38,0.50] | - | 0.441 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | NY | gbt3 | 0.463 [0.42,0.50] | 0.439 [0.38,0.50] | - | 0.443 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | LONDON | gbt3 | 0.478 [0.43,0.52] | 0.438 [0.39,0.49] | - | 0.438 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | POOLED | stack | 0.486 [0.46,0.51] | 0.438 [0.40,0.47] | - | 0.431 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | POOLED | stack | 0.486 [0.46,0.51] | 0.438 [0.40,0.47] | - | 0.431 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | pre | LONDON | gbt3 | 0.480 [0.43,0.53] | 0.438 [0.38,0.50] | - | 0.425 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | POOLED | stack | 0.492 [0.47,0.52] | 0.438 [0.40,0.48] | - | 0.437 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | POOLED | stack | 0.492 [0.47,0.52] | 0.438 [0.40,0.48] | - | 0.437 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | ASIA | stack | 0.493 [0.45,0.54] | 0.438 [0.38,0.50] | - | 0.422 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +30 | LONDON | stack | 0.501 [0.46,0.55] | 0.437 [0.38,0.49] | - | 0.443 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | LONDON | stack | 0.501 [0.46,0.55] | 0.437 [0.38,0.49] | - | 0.443 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | LONDON | stack | 0.501 [0.46,0.55] | 0.437 [0.38,0.49] | - | 0.443 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | LONDON | stack | 0.501 [0.46,0.55] | 0.437 [0.38,0.49] | - | 0.443 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | LONDON | stack | 0.501 [0.46,0.55] | 0.437 [0.38,0.49] | - | 0.443 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | LONDON | stack | 0.501 [0.46,0.55] | 0.437 [0.38,0.49] | - | 0.443 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | LONDON | logit2 | 0.482 [0.44,0.53] | 0.437 [0.38,0.50] | - | 0.425 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +5 | POOLED | stack | 0.491 [0.47,0.52] | 0.437 [0.40,0.48] | - | 0.433 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +5 | POOLED | stack | 0.491 [0.47,0.52] | 0.437 [0.40,0.48] | - | 0.433 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4+base | +30 | LONDON | rf | 0.447 [0.40,0.49] | 0.437 [0.37,0.50] | - | 0.425 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | POOLED | stack | 0.493 [0.47,0.52] | 0.436 [0.40,0.47] | - | 0.435 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +30 | POOLED | stack | 0.493 [0.47,0.52] | 0.436 [0.40,0.47] | - | 0.435 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +30 | POOLED | stack | 0.493 [0.47,0.52] | 0.436 [0.40,0.47] | - | 0.435 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +30 | POOLED | stack | 0.493 [0.47,0.52] | 0.436 [0.40,0.47] | - | 0.435 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +30 | POOLED | stack | 0.493 [0.47,0.52] | 0.436 [0.40,0.47] | - | 0.435 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F14-18+base | +30 | POOLED | stack | 0.493 [0.47,0.52] | 0.436 [0.40,0.47] | - | 0.435 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F9-13 | pre | LONDON | gbt3 | 0.501 [0.45,0.55] | 0.436 [0.37,0.51] | - | 0.445 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | LONDON | stack | 0.492 [0.45,0.54] | 0.436 [0.37,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | LONDON | stack | 0.492 [0.45,0.54] | 0.436 [0.37,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | LONDON | stack | 0.492 [0.45,0.54] | 0.436 [0.37,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | LONDON | stack | 0.492 [0.45,0.54] | 0.436 [0.37,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | LONDON | stack | 0.492 [0.45,0.54] | 0.436 [0.37,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | LONDON | stack | 0.492 [0.45,0.54] | 0.436 [0.37,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +15 | LONDON | stack | 0.492 [0.45,0.54] | 0.436 [0.37,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | LONDON | gbt3 | 0.463 [0.42,0.52] | 0.436 [0.37,0.51] | - | 0.425 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | LONDON | rf | 0.491 [0.45,0.54] | 0.435 [0.39,0.49] | - | 0.437 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | LONDON | rf | 0.491 [0.45,0.54] | 0.435 [0.39,0.49] | - | 0.437 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | LONDON | rf | 0.491 [0.45,0.54] | 0.435 [0.39,0.49] | - | 0.437 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | POOLED | stack | 0.483 [0.46,0.51] | 0.434 [0.39,0.48] | - | 0.429 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | POOLED | stack | 0.483 [0.46,0.51] | 0.434 [0.39,0.48] | - | 0.429 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | POOLED | gbt3 | 0.471 [0.44,0.50] | 0.434 [0.40,0.46] | - | 0.429 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| F9-13 | +20 | LONDON | gbt3 | 0.479 [0.44,0.52] | 0.434 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | LONDON | gbt3 | 0.479 [0.44,0.52] | 0.434 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | LONDON | gbt3 | 0.479 [0.44,0.52] | 0.434 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +20 | LONDON | gbt3 | 0.479 [0.44,0.52] | 0.434 [0.39,0.49] | - | 0.434 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | NY | stack | 0.495 [0.45,0.54] | 0.434 [0.38,0.49] | - | 0.431 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | NY | stack | 0.495 [0.45,0.54] | 0.434 [0.38,0.49] | - | 0.431 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +45 | NY | stack | 0.495 [0.45,0.54] | 0.434 [0.38,0.49] | - | 0.431 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +15 | NY | rf | 0.481 [0.44,0.52] | 0.433 [0.37,0.49] | - | 0.430 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | NY | rf | 0.479 [0.44,0.53] | 0.433 [0.37,0.49] | - | 0.451 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | NY | rf | 0.479 [0.44,0.53] | 0.433 [0.37,0.49] | - | 0.451 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | NY | rf | 0.479 [0.44,0.53] | 0.433 [0.37,0.49] | - | 0.451 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | NY | rf | 0.479 [0.44,0.53] | 0.433 [0.37,0.49] | - | 0.451 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | NY | rf | 0.479 [0.44,0.53] | 0.433 [0.37,0.49] | - | 0.451 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | NY | rf | 0.476 [0.43,0.52] | 0.431 [0.38,0.49] | - | 0.439 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | NY | rf | 0.476 [0.43,0.52] | 0.431 [0.38,0.49] | - | 0.439 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | NY | rf | 0.476 [0.43,0.52] | 0.431 [0.38,0.49] | - | 0.439 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | NY | rf | 0.476 [0.43,0.52] | 0.431 [0.38,0.49] | - | 0.439 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | pre | LONDON | gbt3 | 0.468 [0.42,0.51] | 0.430 [0.37,0.50] | - | 0.424 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | POOLED | stack | 0.484 [0.46,0.51] | 0.430 [0.39,0.47] | - | 0.423 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +30 | POOLED | stack | 0.484 [0.46,0.51] | 0.430 [0.39,0.47] | - | 0.423 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +30 | POOLED | stack | 0.484 [0.46,0.51] | 0.430 [0.39,0.47] | - | 0.423 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +30 | POOLED | stack | 0.484 [0.46,0.51] | 0.430 [0.39,0.47] | - | 0.423 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +30 | POOLED | stack | 0.484 [0.46,0.51] | 0.430 [0.39,0.47] | - | 0.423 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F5-8+base | +30 | POOLED | stack | 0.484 [0.46,0.51] | 0.430 [0.39,0.47] | - | 0.423 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| F1-4 | +45 | LONDON | stack | 0.494 [0.45,0.54] | 0.429 [0.37,0.49] | - | 0.421 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | LONDON | stack | 0.494 [0.45,0.54] | 0.429 [0.37,0.49] | - | 0.421 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +10 | NY | logit2 | 0.448 [0.41,0.49] | 0.429 [0.37,0.48] | - | 0.427 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | NY | stack | 0.455 [0.41,0.50] | 0.428 [0.37,0.49] | - | 0.423 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | NY | stack | 0.455 [0.41,0.50] | 0.428 [0.37,0.49] | - | 0.423 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +45 | NY | stack | 0.455 [0.41,0.50] | 0.428 [0.37,0.49] | - | 0.423 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | POOLED | stack | 0.474 [0.45,0.50] | 0.426 [0.39,0.47] | - | 0.422 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | POOLED | stack | 0.474 [0.45,0.50] | 0.426 [0.39,0.47] | - | 0.422 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | LONDON | stack | 0.494 [0.44,0.54] | 0.426 [0.37,0.49] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | LONDON | stack | 0.494 [0.44,0.54] | 0.426 [0.37,0.49] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | NY | stack | 0.469 [0.43,0.52] | 0.426 [0.36,0.50] | - | 0.426 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | NY | stack | 0.469 [0.43,0.52] | 0.426 [0.36,0.50] | - | 0.426 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | NY | stack | 0.469 [0.43,0.52] | 0.426 [0.36,0.50] | - | 0.426 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +30 | NY | stack | 0.469 [0.43,0.52] | 0.426 [0.36,0.50] | - | 0.426 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | NY | stack | 0.486 [0.44,0.53] | 0.426 [0.36,0.49] | - | 0.427 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | NY | stack | 0.486 [0.44,0.53] | 0.426 [0.36,0.49] | - | 0.427 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | NY | stack | 0.486 [0.44,0.53] | 0.426 [0.36,0.49] | - | 0.427 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +30 | NY | stack | 0.486 [0.44,0.53] | 0.426 [0.36,0.49] | - | 0.427 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | NY | stack | 0.474 [0.43,0.52] | 0.425 [0.37,0.48] | - | 0.418 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | NY | stack | 0.474 [0.43,0.52] | 0.425 [0.37,0.48] | - | 0.418 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +45 | NY | stack | 0.474 [0.43,0.52] | 0.425 [0.37,0.48] | - | 0.418 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | LONDON | stack | 0.467 [0.42,0.51] | 0.424 [0.36,0.49] | - | 0.414 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | LONDON | stack | 0.467 [0.42,0.51] | 0.424 [0.36,0.49] | - | 0.414 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | LONDON | stack | 0.492 [0.45,0.54] | 0.423 [0.36,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | LONDON | stack | 0.492 [0.45,0.54] | 0.423 [0.36,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | LONDON | stack | 0.492 [0.45,0.54] | 0.423 [0.36,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | LONDON | stack | 0.492 [0.45,0.54] | 0.423 [0.36,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +10 | LONDON | stack | 0.492 [0.45,0.54] | 0.423 [0.36,0.50] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | NY | stack | 0.468 [0.43,0.51] | 0.423 [0.36,0.48] | - | 0.430 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | NY | stack | 0.468 [0.43,0.51] | 0.423 [0.36,0.48] | - | 0.430 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | NY | stack | 0.468 [0.43,0.51] | 0.423 [0.36,0.48] | - | 0.430 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +30 | NY | stack | 0.468 [0.43,0.51] | 0.423 [0.36,0.48] | - | 0.430 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | NY | stack | 0.481 [0.43,0.53] | 0.422 [0.36,0.49] | - | 0.422 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | NY | stack | 0.481 [0.43,0.53] | 0.422 [0.36,0.49] | - | 0.422 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | NY | stack | 0.481 [0.43,0.53] | 0.422 [0.36,0.49] | - | 0.422 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +30 | NY | stack | 0.481 [0.43,0.53] | 0.422 [0.36,0.49] | - | 0.422 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | LONDON | stack | 0.479 [0.44,0.53] | 0.418 [0.35,0.48] | - | 0.415 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +60 | LONDON | stack | 0.479 [0.44,0.53] | 0.418 [0.35,0.48] | - | 0.415 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | NY | rf | 0.451 [0.41,0.49] | 0.417 [0.36,0.48] | - | 0.411 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | NY | rf | 0.451 [0.41,0.49] | 0.417 [0.36,0.48] | - | 0.411 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | NY | rf | 0.451 [0.41,0.49] | 0.417 [0.36,0.48] | - | 0.411 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | NY | rf | 0.451 [0.41,0.49] | 0.417 [0.36,0.48] | - | 0.411 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | LONDON | stack | 0.509 [0.46,0.56] | 0.415 [0.36,0.47] | - | 0.407 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | LONDON | stack | 0.509 [0.46,0.56] | 0.415 [0.36,0.47] | - | 0.407 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | LONDON | stack | 0.509 [0.46,0.56] | 0.415 [0.36,0.47] | - | 0.407 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | LONDON | stack | 0.509 [0.46,0.56] | 0.415 [0.36,0.47] | - | 0.407 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | LONDON | stack | 0.509 [0.46,0.56] | 0.415 [0.36,0.47] | - | 0.407 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | pre | LONDON | stack | 0.509 [0.46,0.56] | 0.415 [0.36,0.47] | - | 0.407 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | NY | stack | 0.492 [0.45,0.54] | 0.415 [0.35,0.47] | - | 0.423 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | NY | stack | 0.492 [0.45,0.54] | 0.415 [0.35,0.47] | - | 0.423 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | NY | stack | 0.492 [0.45,0.54] | 0.415 [0.35,0.47] | - | 0.423 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +30 | NY | stack | 0.492 [0.45,0.54] | 0.415 [0.35,0.47] | - | 0.423 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +15 | NY | stack | 0.488 [0.44,0.53] | 0.413 [0.35,0.48] | - | 0.422 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | NY | stack | 0.462 [0.42,0.51] | 0.412 [0.36,0.47] | - | 0.415 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | NY | stack | 0.462 [0.42,0.51] | 0.412 [0.36,0.47] | - | 0.415 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | NY | stack | 0.462 [0.42,0.51] | 0.412 [0.36,0.47] | - | 0.415 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | LONDON | stack | 0.499 [0.46,0.54] | 0.409 [0.35,0.47] | - | 0.402 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18 | +60 | LONDON | stack | 0.499 [0.46,0.54] | 0.409 [0.35,0.47] | - | 0.402 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | LONDON | stack | 0.467 [0.42,0.51] | 0.408 [0.34,0.47] | - | 0.397 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | LONDON | stack | 0.467 [0.42,0.51] | 0.408 [0.34,0.47] | - | 0.397 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | LONDON | rf | 0.480 [0.43,0.53] | 0.408 [0.35,0.46] | - | 0.406 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | NY | stack | 0.465 [0.42,0.51] | 0.402 [0.34,0.47] | - | 0.403 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | NY | stack | 0.465 [0.42,0.51] | 0.402 [0.34,0.47] | - | 0.403 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | NY | stack | 0.465 [0.42,0.51] | 0.402 [0.34,0.47] | - | 0.403 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8+base | +30 | NY | stack | 0.465 [0.42,0.51] | 0.402 [0.34,0.47] | - | 0.403 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | NY | stack | 0.476 [0.43,0.52] | 0.402 [0.34,0.47] | - | 0.399 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | NY | stack | 0.476 [0.43,0.52] | 0.402 [0.34,0.47] | - | 0.399 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13+base | +45 | NY | stack | 0.476 [0.43,0.52] | 0.402 [0.34,0.47] | - | 0.399 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | NY | rf | 0.469 [0.43,0.51] | 0.401 [0.35,0.45] | - | 0.402 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | NY | rf | 0.469 [0.43,0.51] | 0.401 [0.35,0.45] | - | 0.402 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | NY | rf | 0.469 [0.43,0.51] | 0.401 [0.35,0.45] | - | 0.402 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | NY | rf | 0.469 [0.43,0.51] | 0.401 [0.35,0.45] | - | 0.402 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | NY | rf | 0.469 [0.43,0.51] | 0.401 [0.35,0.45] | - | 0.402 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | LONDON | stack | 0.455 [0.41,0.50] | 0.401 [0.35,0.47] | - | 0.395 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F14-18+base | +45 | LONDON | stack | 0.455 [0.41,0.50] | 0.401 [0.35,0.47] | - | 0.395 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +10 | NY | logit2 | 0.463 [0.42,0.51] | 0.400 [0.34,0.46] | - | 0.407 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | NY | logit2 | 0.452 [0.41,0.50] | 0.397 [0.34,0.45] | - | 0.410 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F9-13 | +5 | NY | logit2 | 0.452 [0.41,0.50] | 0.397 [0.34,0.45] | - | 0.410 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4 | +30 | LONDON | gbt3 | 0.475 [0.42,0.53] | 0.391 [0.34,0.45] | - | 0.386 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | NY | stack | 0.472 [0.43,0.51] | 0.386 [0.33,0.44] | - | 0.378 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | NY | stack | 0.472 [0.43,0.51] | 0.386 [0.33,0.44] | - | 0.378 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F1-4+base | +45 | NY | stack | 0.472 [0.43,0.51] | 0.386 [0.33,0.44] | - | 0.378 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | LONDON | stack | 0.453 [0.41,0.50] | 0.379 [0.32,0.44] | - | 0.366 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | LONDON | stack | 0.453 [0.41,0.50] | 0.379 [0.32,0.44] | - | 0.366 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | LONDON | stack | 0.453 [0.41,0.50] | 0.379 [0.32,0.44] | - | 0.366 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | LONDON | stack | 0.453 [0.41,0.50] | 0.379 [0.32,0.44] | - | 0.366 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | LONDON | stack | 0.453 [0.41,0.50] | 0.379 [0.32,0.44] | - | 0.366 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | LONDON | stack | 0.453 [0.41,0.50] | 0.379 [0.32,0.44] | - | 0.366 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| F5-8 | +5 | LONDON | stack | 0.453 [0.41,0.50] | 0.379 [0.32,0.44] | - | 0.366 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |

One-sentence notes:
- F1-4 0 POOLED: conditional, unlocked
- F1-4+base 0 POOLED: conditional, unlocked
- F5-8 0 POOLED: conditional, unlocked
- F5-8+base 0 POOLED: conditional, unlocked
- F9-13 0 POOLED: conditional, unlocked
- F9-13+base 0 POOLED: conditional, unlocked
- F14-18 0 POOLED: conditional, unlocked
- F14-18+base 0 POOLED: conditional, unlocked
- F1-4 0 ASIA: conditional, unlocked
- F1-4+base 0 ASIA: conditional, unlocked
- F5-8 0 ASIA: conditional, unlocked
- F5-8+base 0 ASIA: conditional, unlocked
- F9-13 0 ASIA: conditional, unlocked
- F9-13+base 0 ASIA: conditional, unlocked
- F14-18 0 ASIA: conditional, unlocked
- F14-18+base 0 ASIA: conditional, unlocked
- F1-4 0 LONDON: conditional, unlocked
- F1-4+base 0 LONDON: conditional, unlocked
- F5-8 0 LONDON: conditional, unlocked
- F5-8+base 0 LONDON: conditional, unlocked
- F9-13 0 LONDON: conditional, unlocked
- F9-13+base 0 LONDON: conditional, unlocked
- F14-18 0 LONDON: conditional, unlocked
- F14-18+base 0 LONDON: conditional, unlocked
- F1-4 0 NY: conditional, unlocked
- F1-4+base 0 NY: conditional, unlocked
- F5-8 0 NY: conditional, unlocked
- F5-8+base 0 NY: conditional, unlocked
- F9-13 0 NY: conditional, unlocked
- F9-13+base 0 NY: conditional, unlocked
- F14-18 0 NY: conditional, unlocked
- F14-18+base 0 NY: conditional, unlocked
- F1-4 5 POOLED: conditional, unlocked
- F1-4+base 5 POOLED: conditional, unlocked
- F5-8 5 POOLED: conditional, unlocked
- F5-8+base 5 POOLED: conditional, unlocked
- F9-13 5 POOLED: conditional, unlocked
- F9-13+base 5 POOLED: conditional, unlocked
- F14-18 5 POOLED: conditional, unlocked
- F14-18+base 5 POOLED: conditional, unlocked
- F1-4 5 ASIA: conditional, unlocked
- F1-4+base 5 ASIA: conditional, unlocked
- F5-8 5 ASIA: conditional, unlocked
- F5-8+base 5 ASIA: conditional, unlocked
- F9-13 5 ASIA: conditional, unlocked
- F9-13+base 5 ASIA: conditional, unlocked
- F14-18 5 ASIA: conditional, unlocked
- F14-18+base 5 ASIA: conditional, unlocked
- F1-4 5 LONDON: conditional, unlocked
- F1-4+base 5 LONDON: conditional, unlocked
- F5-8 5 LONDON: conditional, unlocked
- F5-8+base 5 LONDON: conditional, unlocked
- F9-13 5 LONDON: conditional, unlocked
- F9-13+base 5 LONDON: conditional, unlocked
- F14-18 5 LONDON: conditional, unlocked
- F14-18+base 5 LONDON: conditional, unlocked
- F1-4 5 NY: conditional, unlocked
- F1-4+base 5 NY: conditional, unlocked
- F5-8 5 NY: conditional, unlocked
- F5-8+base 5 NY: conditional, unlocked
- F9-13 5 NY: conditional, unlocked
- F9-13+base 5 NY: conditional, unlocked
- F14-18 5 NY: conditional, unlocked
- F14-18+base 5 NY: conditional, unlocked
- F1-4 10 POOLED: conditional, unlocked
- F1-4+base 10 POOLED: conditional, unlocked
- F5-8 10 POOLED: conditional, unlocked
- F5-8+base 10 POOLED: conditional, unlocked
- F9-13 10 POOLED: conditional, unlocked
- F9-13+base 10 POOLED: conditional, unlocked
- F14-18 10 POOLED: conditional, unlocked
- F14-18+base 10 POOLED: conditional, unlocked
- F1-4 10 ASIA: conditional, unlocked
- F1-4+base 10 ASIA: conditional, unlocked
- F5-8 10 ASIA: conditional, unlocked
- F5-8+base 10 ASIA: conditional, unlocked
- F9-13 10 ASIA: conditional, unlocked
- F9-13+base 10 ASIA: conditional, unlocked
- F14-18 10 ASIA: conditional, unlocked
- F14-18+base 10 ASIA: conditional, unlocked
- F1-4 10 LONDON: conditional, unlocked
- F1-4+base 10 LONDON: conditional, unlocked
- F5-8 10 LONDON: conditional, unlocked
- F5-8+base 10 LONDON: conditional, unlocked
- F9-13 10 LONDON: conditional, unlocked
- F9-13+base 10 LONDON: conditional, unlocked
- F14-18 10 LONDON: conditional, unlocked
- F14-18+base 10 LONDON: conditional, unlocked
- F1-4 10 NY: conditional, unlocked
- F1-4+base 10 NY: conditional, unlocked
- F5-8 10 NY: conditional, unlocked
- F5-8+base 10 NY: conditional, unlocked
- F9-13 10 NY: conditional, unlocked
- F9-13+base 10 NY: conditional, unlocked
- F14-18 10 NY: conditional, unlocked
- F14-18+base 10 NY: conditional, unlocked
- F1-4 15 POOLED: conditional, unlocked
- F1-4+base 15 POOLED: conditional, unlocked
- F5-8 15 POOLED: conditional, unlocked
- F5-8+base 15 POOLED: conditional, unlocked
- F9-13 15 POOLED: conditional, unlocked
- F9-13+base 15 POOLED: conditional, unlocked
- F14-18 15 POOLED: conditional, unlocked
- F14-18+base 15 POOLED: conditional, unlocked
- F1-4 15 ASIA: conditional, unlocked
- F1-4+base 15 ASIA: conditional, unlocked
- F5-8 15 ASIA: conditional, unlocked
- F5-8+base 15 ASIA: conditional, unlocked
- F9-13 15 ASIA: conditional, unlocked
- F9-13+base 15 ASIA: conditional, unlocked
- F14-18 15 ASIA: conditional, unlocked
- F14-18+base 15 ASIA: conditional, unlocked
- F1-4 15 LONDON: conditional, unlocked
- F1-4+base 15 LONDON: conditional, unlocked
- F5-8 15 LONDON: conditional, unlocked
- F5-8+base 15 LONDON: conditional, unlocked
- F9-13 15 LONDON: conditional, unlocked
- F9-13+base 15 LONDON: conditional, unlocked
- F14-18 15 LONDON: conditional, unlocked
- F14-18+base 15 LONDON: conditional, unlocked
- F1-4 15 NY: conditional, unlocked
- F1-4+base 15 NY: conditional, unlocked
- F5-8 15 NY: conditional, unlocked
- F5-8+base 15 NY: conditional, unlocked
- F9-13 15 NY: conditional, unlocked
- F9-13+base 15 NY: conditional, unlocked
- F14-18 15 NY: conditional, unlocked
- F14-18+base 15 NY: conditional, unlocked
- F1-4 20 POOLED: conditional, unlocked
- F1-4+base 20 POOLED: conditional, unlocked
- F5-8 20 POOLED: conditional, unlocked
- F5-8+base 20 POOLED: conditional, unlocked
- F9-13 20 POOLED: conditional, unlocked
- F9-13+base 20 POOLED: conditional, unlocked
- F14-18 20 POOLED: conditional, unlocked
- F14-18+base 20 POOLED: conditional, unlocked
- F1-4 20 ASIA: conditional, unlocked
- F1-4+base 20 ASIA: conditional, unlocked
- F5-8 20 ASIA: conditional, unlocked
- F5-8+base 20 ASIA: conditional, unlocked
- F9-13 20 ASIA: conditional, unlocked
- F9-13+base 20 ASIA: conditional, unlocked
- F14-18 20 ASIA: conditional, unlocked
- F14-18+base 20 ASIA: conditional, unlocked
- F1-4 20 LONDON: conditional, unlocked
- F1-4+base 20 LONDON: conditional, unlocked
- F5-8 20 LONDON: conditional, unlocked
- F5-8+base 20 LONDON: conditional, unlocked
- F9-13 20 LONDON: conditional, unlocked
- F9-13+base 20 LONDON: conditional, unlocked
- F14-18 20 LONDON: conditional, unlocked
- F14-18+base 20 LONDON: conditional, unlocked
- F1-4 20 NY: conditional, unlocked
- F1-4+base 20 NY: conditional, unlocked
- F5-8 20 NY: conditional, unlocked
- F5-8+base 20 NY: conditional, unlocked
- F9-13 20 NY: conditional, unlocked
- F9-13+base 20 NY: conditional, unlocked
- F14-18 20 NY: conditional, unlocked
- F14-18+base 20 NY: conditional, unlocked
- F1-4 30 POOLED: conditional, unlocked
- F1-4+base 30 POOLED: conditional, unlocked
- F5-8 30 POOLED: conditional, unlocked
- F5-8+base 30 POOLED: conditional, unlocked
- F9-13 30 POOLED: conditional, unlocked
- F9-13+base 30 POOLED: conditional, unlocked
- F14-18 30 POOLED: conditional, unlocked
- F14-18+base 30 POOLED: conditional, unlocked
- F1-4 30 ASIA: conditional, unlocked
- F1-4+base 30 ASIA: conditional, unlocked
- F5-8 30 ASIA: conditional, unlocked
- F5-8+base 30 ASIA: conditional, unlocked
- F9-13 30 ASIA: conditional, unlocked
- F9-13+base 30 ASIA: conditional, unlocked
- F14-18 30 ASIA: conditional, unlocked
- F14-18+base 30 ASIA: conditional, unlocked
- F1-4 30 LONDON: conditional, unlocked
- F1-4+base 30 LONDON: conditional, unlocked
- F5-8 30 LONDON: conditional, unlocked
- F5-8+base 30 LONDON: conditional, unlocked
- F9-13 30 LONDON: conditional, unlocked
- F9-13+base 30 LONDON: conditional, unlocked
- F14-18 30 LONDON: conditional, unlocked
- F14-18+base 30 LONDON: conditional, unlocked
- F1-4 30 NY: conditional, unlocked
- F1-4+base 30 NY: conditional, unlocked
- F5-8 30 NY: conditional, unlocked
- F5-8+base 30 NY: conditional, unlocked
- F9-13 30 NY: conditional, unlocked
- F9-13+base 30 NY: conditional, unlocked
- F14-18 30 NY: conditional, unlocked
- F14-18+base 30 NY: conditional, unlocked
- F1-4 45 POOLED: conditional, unlocked
- F1-4+base 45 POOLED: conditional, unlocked
- F5-8 45 POOLED: conditional, unlocked
- F5-8+base 45 POOLED: conditional, unlocked
- F9-13 45 POOLED: conditional, unlocked
- F9-13+base 45 POOLED: conditional, unlocked
- F14-18 45 POOLED: conditional, unlocked
- F14-18+base 45 POOLED: conditional, unlocked
- F1-4 45 ASIA: conditional, unlocked
- F1-4+base 45 ASIA: conditional, unlocked
- F5-8 45 ASIA: conditional, unlocked
- F5-8+base 45 ASIA: conditional, unlocked
- F9-13 45 ASIA: conditional, unlocked
- F9-13+base 45 ASIA: conditional, unlocked
- F14-18 45 ASIA: conditional, unlocked
- F14-18+base 45 ASIA: conditional, unlocked
- F1-4 45 LONDON: conditional, unlocked
- F1-4+base 45 LONDON: conditional, unlocked
- F5-8 45 LONDON: conditional, unlocked
- F5-8+base 45 LONDON: conditional, unlocked
- F9-13 45 LONDON: conditional, unlocked
- F9-13+base 45 LONDON: conditional, unlocked
- F14-18 45 LONDON: conditional, unlocked
- F14-18+base 45 LONDON: conditional, unlocked
- F1-4 45 NY: conditional, unlocked
- F1-4+base 45 NY: conditional, unlocked
- F5-8 45 NY: conditional, unlocked
- F5-8+base 45 NY: conditional, unlocked
- F9-13 45 NY: conditional, unlocked
- F9-13+base 45 NY: conditional, unlocked
- F14-18 45 NY: conditional, unlocked
- F14-18+base 45 NY: conditional, unlocked
- F1-4 60 POOLED: conditional, unlocked
- F1-4+base 60 POOLED: conditional, unlocked
- F5-8 60 POOLED: conditional, unlocked
- F5-8+base 60 POOLED: conditional, unlocked
- F9-13 60 POOLED: conditional, unlocked
- F9-13+base 60 POOLED: conditional, unlocked
- F14-18 60 POOLED: conditional, unlocked
- F14-18+base 60 POOLED: conditional, unlocked
- F1-4 60 ASIA: conditional, unlocked
- F1-4+base 60 ASIA: conditional, unlocked
- F5-8 60 ASIA: conditional, unlocked
- F5-8+base 60 ASIA: conditional, unlocked
- F9-13 60 ASIA: conditional, unlocked
- F9-13+base 60 ASIA: conditional, unlocked
- F14-18 60 ASIA: conditional, unlocked
- F14-18+base 60 ASIA: conditional, unlocked
- F1-4 60 LONDON: conditional, unlocked
- F1-4+base 60 LONDON: conditional, unlocked
- F5-8 60 LONDON: conditional, unlocked
- F5-8+base 60 LONDON: conditional, unlocked
- F9-13 60 LONDON: conditional, unlocked
- F9-13+base 60 LONDON: conditional, unlocked
- F14-18 60 LONDON: conditional, unlocked
- F14-18+base 60 LONDON: conditional, unlocked
- F1-4 60 NY: conditional, unlocked
- F1-4+base 60 NY: conditional, unlocked
- F5-8 60 NY: conditional, unlocked
- F5-8+base 60 NY: conditional, unlocked
- F9-13 60 NY: conditional, unlocked
- F9-13+base 60 NY: conditional, unlocked
- F14-18 60 NY: conditional, unlocked
- F14-18+base 60 NY: conditional, unlocked
- F1-4 0 POOLED: conditional, unlocked
- F1-4+base 0 POOLED: conditional, unlocked
- F5-8 0 POOLED: conditional, unlocked
- F5-8+base 0 POOLED: conditional, unlocked
- F9-13 0 POOLED: conditional, unlocked
- F9-13+base 0 POOLED: conditional, unlocked
- F14-18 0 POOLED: conditional, unlocked
- F14-18+base 0 POOLED: conditional, unlocked
- F1-4 0 ASIA: conditional, unlocked
- F1-4+base 0 ASIA: conditional, unlocked
- F5-8 0 ASIA: conditional, unlocked
- F5-8+base 0 ASIA: conditional, unlocked
- F9-13 0 ASIA: conditional, unlocked
- F9-13+base 0 ASIA: conditional, unlocked
- F14-18 0 ASIA: conditional, unlocked
- F14-18+base 0 ASIA: conditional, unlocked
- F1-4 0 LONDON: conditional, unlocked
- F1-4+base 0 LONDON: conditional, unlocked
- F5-8 0 LONDON: conditional, unlocked
- F5-8+base 0 LONDON: conditional, unlocked
- F9-13 0 LONDON: conditional, unlocked
- F9-13+base 0 LONDON: conditional, unlocked
- F14-18 0 LONDON: conditional, unlocked
- F14-18+base 0 LONDON: conditional, unlocked
- F1-4 0 NY: conditional, unlocked
- F1-4+base 0 NY: conditional, unlocked
- F5-8 0 NY: conditional, unlocked
- F5-8+base 0 NY: conditional, unlocked
- F9-13 0 NY: conditional, unlocked
- F9-13+base 0 NY: conditional, unlocked
- F14-18 0 NY: conditional, unlocked
- F14-18+base 0 NY: conditional, unlocked
- F1-4 5 POOLED: conditional, unlocked
- F1-4+base 5 POOLED: conditional, unlocked
- F5-8 5 POOLED: conditional, unlocked
- F5-8+base 5 POOLED: conditional, unlocked
- F9-13 5 POOLED: conditional, unlocked
- F9-13+base 5 POOLED: conditional, unlocked
- F14-18 5 POOLED: conditional, unlocked
- F14-18+base 5 POOLED: conditional, unlocked
- F1-4 5 ASIA: conditional, unlocked
- F1-4+base 5 ASIA: conditional, unlocked
- F5-8 5 ASIA: conditional, unlocked
- F5-8+base 5 ASIA: conditional, unlocked
- F9-13 5 ASIA: conditional, unlocked
- F9-13+base 5 ASIA: conditional, unlocked
- F14-18 5 ASIA: conditional, unlocked
- F14-18+base 5 ASIA: conditional, unlocked
- F1-4 5 LONDON: conditional, unlocked
- F1-4+base 5 LONDON: conditional, unlocked
- F5-8 5 LONDON: conditional, unlocked
- F5-8+base 5 LONDON: conditional, unlocked
- F9-13 5 LONDON: conditional, unlocked
- F9-13+base 5 LONDON: conditional, unlocked
- F14-18 5 LONDON: conditional, unlocked
- F14-18+base 5 LONDON: conditional, unlocked
- F1-4 5 NY: conditional, unlocked
- F1-4+base 5 NY: conditional, unlocked
- F5-8 5 NY: conditional, unlocked
- F5-8+base 5 NY: conditional, unlocked
- F9-13 5 NY: conditional, unlocked
- F9-13+base 5 NY: conditional, unlocked
- F14-18 5 NY: conditional, unlocked
- F14-18+base 5 NY: conditional, unlocked
- F1-4 10 POOLED: conditional, unlocked
- F1-4+base 10 POOLED: conditional, unlocked
- F5-8 10 POOLED: conditional, unlocked
- F5-8+base 10 POOLED: conditional, unlocked
- F9-13 10 POOLED: conditional, unlocked
- F9-13+base 10 POOLED: conditional, unlocked
- F14-18 10 POOLED: conditional, unlocked
- F14-18+base 10 POOLED: conditional, unlocked
- F1-4 10 ASIA: conditional, unlocked
- F1-4+base 10 ASIA: conditional, unlocked
- F5-8 10 ASIA: conditional, unlocked
- F5-8+base 10 ASIA: conditional, unlocked
- F9-13 10 ASIA: conditional, unlocked
- F9-13+base 10 ASIA: conditional, unlocked
- F14-18 10 ASIA: conditional, unlocked
- F14-18+base 10 ASIA: conditional, unlocked
- F1-4 10 LONDON: conditional, unlocked
- F1-4+base 10 LONDON: conditional, unlocked
- F5-8 10 LONDON: conditional, unlocked
- F5-8+base 10 LONDON: conditional, unlocked
- F9-13 10 LONDON: conditional, unlocked
- F9-13+base 10 LONDON: conditional, unlocked
- F14-18 10 LONDON: conditional, unlocked
- F14-18+base 10 LONDON: conditional, unlocked
- F1-4 10 NY: conditional, unlocked
- F1-4+base 10 NY: conditional, unlocked
- F5-8 10 NY: conditional, unlocked
- F5-8+base 10 NY: conditional, unlocked
- F9-13 10 NY: conditional, unlocked
- F9-13+base 10 NY: conditional, unlocked
- F14-18 10 NY: conditional, unlocked
- F14-18+base 10 NY: conditional, unlocked
- F1-4 15 POOLED: conditional, unlocked
- F1-4+base 15 POOLED: conditional, unlocked
- F5-8 15 POOLED: conditional, unlocked
- F5-8+base 15 POOLED: conditional, unlocked
- F9-13 15 POOLED: conditional, unlocked
- F9-13+base 15 POOLED: conditional, unlocked
- F14-18 15 POOLED: conditional, unlocked
- F14-18+base 15 POOLED: conditional, unlocked
- F1-4 15 ASIA: conditional, unlocked
- F1-4+base 15 ASIA: conditional, unlocked
- F5-8 15 ASIA: conditional, unlocked
- F5-8+base 15 ASIA: conditional, unlocked
- F9-13 15 ASIA: conditional, unlocked
- F9-13+base 15 ASIA: conditional, unlocked
- F14-18 15 ASIA: conditional, unlocked
- F14-18+base 15 ASIA: conditional, unlocked
- F1-4 15 LONDON: conditional, unlocked
- F1-4+base 15 LONDON: conditional, unlocked
- F5-8 15 LONDON: conditional, unlocked
- F5-8+base 15 LONDON: conditional, unlocked
- F9-13 15 LONDON: conditional, unlocked
- F9-13+base 15 LONDON: conditional, unlocked
- F14-18 15 LONDON: conditional, unlocked
- F14-18+base 15 LONDON: conditional, unlocked
- F1-4 15 NY: conditional, unlocked
- F1-4+base 15 NY: conditional, unlocked
- F5-8 15 NY: conditional, unlocked
- F5-8+base 15 NY: conditional, unlocked
- F9-13 15 NY: conditional, unlocked
- F9-13+base 15 NY: conditional, unlocked
- F14-18 15 NY: conditional, unlocked
- F14-18+base 15 NY: conditional, unlocked
- F1-4 20 POOLED: conditional, unlocked
- F1-4+base 20 POOLED: conditional, unlocked
- F5-8 20 POOLED: conditional, unlocked
- F5-8+base 20 POOLED: conditional, unlocked
- F9-13 20 POOLED: conditional, unlocked
- F9-13+base 20 POOLED: conditional, unlocked
- F14-18 20 POOLED: conditional, unlocked
- F14-18+base 20 POOLED: conditional, unlocked
- F1-4 20 ASIA: conditional, unlocked
- F1-4+base 20 ASIA: conditional, unlocked
- F5-8 20 ASIA: conditional, unlocked
- F5-8+base 20 ASIA: conditional, unlocked
- F9-13 20 ASIA: conditional, unlocked
- F9-13+base 20 ASIA: conditional, unlocked
- F14-18 20 ASIA: conditional, unlocked
- F14-18+base 20 ASIA: conditional, unlocked
- F1-4 20 LONDON: conditional, unlocked
- F1-4+base 20 LONDON: conditional, unlocked
- F5-8 20 LONDON: conditional, unlocked
- F5-8+base 20 LONDON: conditional, unlocked
- F9-13 20 LONDON: conditional, unlocked
- F9-13+base 20 LONDON: conditional, unlocked
- F14-18 20 LONDON: conditional, unlocked
- F14-18+base 20 LONDON: conditional, unlocked
- F1-4 20 NY: conditional, unlocked
- F1-4+base 20 NY: conditional, unlocked
- F5-8 20 NY: conditional, unlocked
- F5-8+base 20 NY: conditional, unlocked
- F9-13 20 NY: conditional, unlocked
- F9-13+base 20 NY: conditional, unlocked
- F14-18 20 NY: conditional, unlocked
- F14-18+base 20 NY: conditional, unlocked
- F1-4 30 POOLED: conditional, unlocked
- F1-4+base 30 POOLED: conditional, unlocked
- F5-8 30 POOLED: conditional, unlocked
- F5-8+base 30 POOLED: conditional, unlocked
- F9-13 30 POOLED: conditional, unlocked
- F9-13+base 30 POOLED: conditional, unlocked
- F14-18 30 POOLED: conditional, unlocked
- F14-18+base 30 POOLED: conditional, unlocked
- F1-4 30 ASIA: conditional, unlocked
- F1-4+base 30 ASIA: conditional, unlocked
- F5-8 30 ASIA: conditional, unlocked
- F5-8+base 30 ASIA: conditional, unlocked
- F9-13 30 ASIA: conditional, unlocked
- F9-13+base 30 ASIA: conditional, unlocked
- F14-18 30 ASIA: conditional, unlocked
- F14-18+base 30 ASIA: conditional, unlocked
- F1-4 30 LONDON: conditional, unlocked
- F1-4+base 30 LONDON: conditional, unlocked
- F5-8 30 LONDON: conditional, unlocked
- F5-8+base 30 LONDON: conditional, unlocked
- F9-13 30 LONDON: conditional, unlocked
- F9-13+base 30 LONDON: conditional, unlocked
- F14-18 30 LONDON: conditional, unlocked
- F14-18+base 30 LONDON: conditional, unlocked
- F1-4 30 NY: conditional, unlocked
- F1-4+base 30 NY: conditional, unlocked
- F5-8 30 NY: conditional, unlocked
- F5-8+base 30 NY: conditional, unlocked
- F9-13 30 NY: conditional, unlocked
- F9-13+base 30 NY: conditional, unlocked
- F14-18 30 NY: conditional, unlocked
- F14-18+base 30 NY: conditional, unlocked
- F1-4 45 POOLED: conditional, unlocked
- F1-4+base 45 POOLED: conditional, unlocked
- F5-8 45 POOLED: conditional, unlocked
- F5-8+base 45 POOLED: conditional, unlocked
- F9-13 45 POOLED: conditional, unlocked
- F9-13+base 45 POOLED: conditional, unlocked
- F14-18 45 POOLED: conditional, unlocked
- F14-18+base 45 POOLED: conditional, unlocked
- F1-4 45 ASIA: conditional, unlocked
- F1-4+base 45 ASIA: conditional, unlocked
- F5-8 45 ASIA: conditional, unlocked
- F5-8+base 45 ASIA: conditional, unlocked
- F9-13 45 ASIA: conditional, unlocked
- F9-13+base 45 ASIA: conditional, unlocked
- F14-18 45 ASIA: conditional, unlocked
- F14-18+base 45 ASIA: conditional, unlocked
- F1-4 45 LONDON: conditional, unlocked
- F1-4+base 45 LONDON: conditional, unlocked
- F5-8 45 LONDON: conditional, unlocked
- F5-8+base 45 LONDON: conditional, unlocked
- F9-13 45 LONDON: conditional, unlocked
- F9-13+base 45 LONDON: conditional, unlocked
- F14-18 45 LONDON: conditional, unlocked
- F14-18+base 45 LONDON: conditional, unlocked
- F1-4 45 NY: conditional, unlocked
- F1-4+base 45 NY: conditional, unlocked
- F5-8 45 NY: conditional, unlocked
- F5-8+base 45 NY: conditional, unlocked
- F9-13 45 NY: conditional, unlocked
- F9-13+base 45 NY: conditional, unlocked
- F14-18 45 NY: conditional, unlocked
- F14-18+base 45 NY: conditional, unlocked
- F1-4 60 POOLED: conditional, unlocked
- F1-4+base 60 POOLED: conditional, unlocked
- F5-8 60 POOLED: conditional, unlocked
- F5-8+base 60 POOLED: conditional, unlocked
- F9-13 60 POOLED: conditional, unlocked
- F9-13+base 60 POOLED: conditional, unlocked
- F14-18 60 POOLED: conditional, unlocked
- F14-18+base 60 POOLED: conditional, unlocked
- F1-4 60 ASIA: conditional, unlocked
- F1-4+base 60 ASIA: conditional, unlocked
- F5-8 60 ASIA: conditional, unlocked
- F5-8+base 60 ASIA: conditional, unlocked
- F9-13 60 ASIA: conditional, unlocked
- F9-13+base 60 ASIA: conditional, unlocked
- F14-18 60 ASIA: conditional, unlocked
- F14-18+base 60 ASIA: conditional, unlocked
- F1-4 60 LONDON: conditional, unlocked
- F1-4+base 60 LONDON: conditional, unlocked
- F5-8 60 LONDON: conditional, unlocked
- F5-8+base 60 LONDON: conditional, unlocked
- F9-13 60 LONDON: conditional, unlocked
- F9-13+base 60 LONDON: conditional, unlocked
- F14-18 60 LONDON: conditional, unlocked
- F14-18+base 60 LONDON: conditional, unlocked
- F1-4 60 NY: conditional, unlocked
- F1-4+base 60 NY: conditional, unlocked
- F5-8 60 NY: conditional, unlocked
- F5-8+base 60 NY: conditional, unlocked
- F9-13 60 NY: conditional, unlocked
- F9-13+base 60 NY: conditional, unlocked
- F14-18 60 NY: conditional, unlocked
- F14-18+base 60 NY: conditional, unlocked
- F1-4 0 POOLED: conditional, unlocked
- F1-4+base 0 POOLED: conditional, unlocked
- F5-8 0 POOLED: conditional, unlocked
- F5-8+base 0 POOLED: conditional, unlocked
- F9-13 0 POOLED: conditional, unlocked
- F9-13+base 0 POOLED: conditional, unlocked
- F14-18 0 POOLED: conditional, unlocked
- F14-18+base 0 POOLED: conditional, unlocked
- F1-4 0 ASIA: conditional, unlocked
- F1-4+base 0 ASIA: conditional, unlocked
- F5-8 0 ASIA: conditional, unlocked
- F5-8+base 0 ASIA: conditional, unlocked
- F9-13 0 ASIA: conditional, unlocked
- F9-13+base 0 ASIA: conditional, unlocked
- F14-18 0 ASIA: conditional, unlocked
- F14-18+base 0 ASIA: conditional, unlocked
- F1-4 0 LONDON: conditional, unlocked
- F1-4+base 0 LONDON: conditional, unlocked
- F5-8 0 LONDON: conditional, unlocked
- F5-8+base 0 LONDON: conditional, unlocked
- F9-13 0 LONDON: conditional, unlocked
- F9-13+base 0 LONDON: conditional, unlocked
- F14-18 0 LONDON: conditional, unlocked
- F14-18+base 0 LONDON: conditional, unlocked
- F1-4 0 NY: conditional, unlocked
- F1-4+base 0 NY: conditional, unlocked
- F5-8 0 NY: conditional, unlocked
- F5-8+base 0 NY: conditional, unlocked
- F9-13 0 NY: conditional, unlocked
- F9-13+base 0 NY: conditional, unlocked
- F14-18 0 NY: conditional, unlocked
- F14-18+base 0 NY: conditional, unlocked
- F1-4 5 POOLED: conditional, unlocked
- F1-4+base 5 POOLED: conditional, unlocked
- F5-8 5 POOLED: conditional, unlocked
- F5-8+base 5 POOLED: conditional, unlocked
- F9-13 5 POOLED: conditional, unlocked
- F9-13+base 5 POOLED: conditional, unlocked
- F14-18 5 POOLED: conditional, unlocked
- F14-18+base 5 POOLED: conditional, unlocked
- F1-4 5 ASIA: conditional, unlocked
- F1-4+base 5 ASIA: conditional, unlocked
- F5-8 5 ASIA: conditional, unlocked
- F5-8+base 5 ASIA: conditional, unlocked
- F9-13 5 ASIA: conditional, unlocked
- F9-13+base 5 ASIA: conditional, unlocked
- F14-18 5 ASIA: conditional, unlocked
- F14-18+base 5 ASIA: conditional, unlocked
- F1-4 5 LONDON: conditional, unlocked
- F1-4+base 5 LONDON: conditional, unlocked
- F5-8 5 LONDON: conditional, unlocked
- F5-8+base 5 LONDON: conditional, unlocked
- F9-13 5 LONDON: conditional, unlocked
- F9-13+base 5 LONDON: conditional, unlocked
- F14-18 5 LONDON: conditional, unlocked
- F14-18+base 5 LONDON: conditional, unlocked
- F1-4 5 NY: conditional, unlocked
- F1-4+base 5 NY: conditional, unlocked
- F5-8 5 NY: conditional, unlocked
- F5-8+base 5 NY: conditional, unlocked
- F9-13 5 NY: conditional, unlocked
- F9-13+base 5 NY: conditional, unlocked
- F14-18 5 NY: conditional, unlocked
- F14-18+base 5 NY: conditional, unlocked
- F1-4 10 POOLED: conditional, unlocked
- F1-4+base 10 POOLED: conditional, unlocked
- F5-8 10 POOLED: conditional, unlocked
- F5-8+base 10 POOLED: conditional, unlocked
- F9-13 10 POOLED: conditional, unlocked
- F9-13+base 10 POOLED: conditional, unlocked
- F14-18 10 POOLED: conditional, unlocked
- F14-18+base 10 POOLED: conditional, unlocked
- F1-4 10 ASIA: conditional, unlocked
- F1-4+base 10 ASIA: conditional, unlocked
- F5-8 10 ASIA: conditional, unlocked
- F5-8+base 10 ASIA: conditional, unlocked
- F9-13 10 ASIA: conditional, unlocked
- F9-13+base 10 ASIA: conditional, unlocked
- F14-18 10 ASIA: conditional, unlocked
- F14-18+base 10 ASIA: conditional, unlocked
- F1-4 10 LONDON: conditional, unlocked
- F1-4+base 10 LONDON: conditional, unlocked
- F5-8 10 LONDON: conditional, unlocked
- F5-8+base 10 LONDON: conditional, unlocked
- F9-13 10 LONDON: conditional, unlocked
- F9-13+base 10 LONDON: conditional, unlocked
- F14-18 10 LONDON: conditional, unlocked
- F14-18+base 10 LONDON: conditional, unlocked
- F1-4 10 NY: conditional, unlocked
- F1-4+base 10 NY: conditional, unlocked
- F5-8 10 NY: conditional, unlocked
- F5-8+base 10 NY: conditional, unlocked
- F9-13 10 NY: conditional, unlocked
- F9-13+base 10 NY: conditional, unlocked
- F14-18 10 NY: conditional, unlocked
- F14-18+base 10 NY: conditional, unlocked
- F1-4 15 POOLED: conditional, unlocked
- F1-4+base 15 POOLED: conditional, unlocked
- F5-8 15 POOLED: conditional, unlocked
- F5-8+base 15 POOLED: conditional, unlocked
- F9-13 15 POOLED: conditional, unlocked
- F9-13+base 15 POOLED: conditional, unlocked
- F14-18 15 POOLED: conditional, unlocked
- F14-18+base 15 POOLED: conditional, unlocked
- F1-4 15 ASIA: conditional, unlocked
- F1-4+base 15 ASIA: conditional, unlocked
- F5-8 15 ASIA: conditional, unlocked
- F5-8+base 15 ASIA: conditional, unlocked
- F9-13 15 ASIA: conditional, unlocked
- F9-13+base 15 ASIA: conditional, unlocked
- F14-18 15 ASIA: conditional, unlocked
- F14-18+base 15 ASIA: conditional, unlocked
- F1-4 15 LONDON: conditional, unlocked
- F1-4+base 15 LONDON: conditional, unlocked
- F5-8 15 LONDON: conditional, unlocked
- F5-8+base 15 LONDON: conditional, unlocked
- F9-13 15 LONDON: conditional, unlocked
- F9-13+base 15 LONDON: conditional, unlocked
- F14-18 15 LONDON: conditional, unlocked
- F14-18+base 15 LONDON: conditional, unlocked
- F1-4 15 NY: conditional, unlocked
- F1-4+base 15 NY: conditional, unlocked
- F5-8 15 NY: conditional, unlocked
- F5-8+base 15 NY: conditional, unlocked
- F9-13 15 NY: conditional, unlocked
- F9-13+base 15 NY: conditional, unlocked
- F14-18 15 NY: conditional, unlocked
- F14-18+base 15 NY: conditional, unlocked
- F1-4 20 POOLED: conditional, unlocked
- F1-4+base 20 POOLED: conditional, unlocked
- F5-8 20 POOLED: conditional, unlocked
- F5-8+base 20 POOLED: conditional, unlocked
- F9-13 20 POOLED: conditional, unlocked
- F9-13+base 20 POOLED: conditional, unlocked
- F14-18 20 POOLED: conditional, unlocked
- F14-18+base 20 POOLED: conditional, unlocked
- F1-4 20 ASIA: conditional, unlocked
- F1-4+base 20 ASIA: conditional, unlocked
- F5-8 20 ASIA: conditional, unlocked
- F5-8+base 20 ASIA: conditional, unlocked
- F9-13 20 ASIA: conditional, unlocked
- F9-13+base 20 ASIA: conditional, unlocked
- F14-18 20 ASIA: conditional, unlocked
- F14-18+base 20 ASIA: conditional, unlocked
- F1-4 20 LONDON: conditional, unlocked
- F1-4+base 20 LONDON: conditional, unlocked
- F5-8 20 LONDON: conditional, unlocked
- F5-8+base 20 LONDON: conditional, unlocked
- F9-13 20 LONDON: conditional, unlocked
- F9-13+base 20 LONDON: conditional, unlocked
- F14-18 20 LONDON: conditional, unlocked
- F14-18+base 20 LONDON: conditional, unlocked
- F1-4 20 NY: conditional, unlocked
- F1-4+base 20 NY: conditional, unlocked
- F5-8 20 NY: conditional, unlocked
- F5-8+base 20 NY: conditional, unlocked
- F9-13 20 NY: conditional, unlocked
- F9-13+base 20 NY: conditional, unlocked
- F14-18 20 NY: conditional, unlocked
- F14-18+base 20 NY: conditional, unlocked
- F1-4 30 POOLED: conditional, unlocked
- F1-4+base 30 POOLED: conditional, unlocked
- F5-8 30 POOLED: conditional, unlocked
- F5-8+base 30 POOLED: conditional, unlocked
- F9-13 30 POOLED: conditional, unlocked
- F9-13+base 30 POOLED: conditional, unlocked
- F14-18 30 POOLED: conditional, unlocked
- F14-18+base 30 POOLED: conditional, unlocked
- F1-4 30 ASIA: conditional, unlocked
- F1-4+base 30 ASIA: conditional, unlocked
- F5-8 30 ASIA: conditional, unlocked
- F5-8+base 30 ASIA: conditional, unlocked
- F9-13 30 ASIA: conditional, unlocked
- F9-13+base 30 ASIA: conditional, unlocked
- F14-18 30 ASIA: conditional, unlocked
- F14-18+base 30 ASIA: conditional, unlocked
- F1-4 30 LONDON: conditional, unlocked
- F1-4+base 30 LONDON: conditional, unlocked
- F5-8 30 LONDON: conditional, unlocked
- F5-8+base 30 LONDON: conditional, unlocked
- F9-13 30 LONDON: conditional, unlocked
- F9-13+base 30 LONDON: conditional, unlocked
- F14-18 30 LONDON: conditional, unlocked
- F14-18+base 30 LONDON: conditional, unlocked
- F1-4 30 NY: conditional, unlocked
- F1-4+base 30 NY: conditional, unlocked
- F5-8 30 NY: conditional, unlocked
- F5-8+base 30 NY: conditional, unlocked
- F9-13 30 NY: conditional, unlocked
- F9-13+base 30 NY: conditional, unlocked
- F14-18 30 NY: conditional, unlocked
- F14-18+base 30 NY: conditional, unlocked
- F1-4 45 POOLED: conditional, unlocked
- F1-4+base 45 POOLED: conditional, unlocked
- F5-8 45 POOLED: conditional, unlocked
- F5-8+base 45 POOLED: conditional, unlocked
- F9-13 45 POOLED: conditional, unlocked
- F9-13+base 45 POOLED: conditional, unlocked
- F14-18 45 POOLED: conditional, unlocked
- F14-18+base 45 POOLED: conditional, unlocked
- F1-4 45 ASIA: conditional, unlocked
- F1-4+base 45 ASIA: conditional, unlocked
- F5-8 45 ASIA: conditional, unlocked
- F5-8+base 45 ASIA: conditional, unlocked
- F9-13 45 ASIA: conditional, unlocked
- F9-13+base 45 ASIA: conditional, unlocked
- F14-18 45 ASIA: conditional, unlocked
- F14-18+base 45 ASIA: conditional, unlocked
- F1-4 45 LONDON: conditional, unlocked
- F1-4+base 45 LONDON: conditional, unlocked
- F5-8 45 LONDON: conditional, unlocked
- F5-8+base 45 LONDON: conditional, unlocked
- F9-13 45 LONDON: conditional, unlocked
- F9-13+base 45 LONDON: conditional, unlocked
- F14-18 45 LONDON: conditional, unlocked
- F14-18+base 45 LONDON: conditional, unlocked
- F1-4 45 NY: conditional, unlocked
- F1-4+base 45 NY: conditional, unlocked
- F5-8 45 NY: conditional, unlocked
- F5-8+base 45 NY: conditional, unlocked
- F9-13 45 NY: conditional, unlocked
- F9-13+base 45 NY: conditional, unlocked
- F14-18 45 NY: conditional, unlocked
- F14-18+base 45 NY: conditional, unlocked
- F1-4 60 POOLED: conditional, unlocked
- F1-4+base 60 POOLED: conditional, unlocked
- F5-8 60 POOLED: conditional, unlocked
- F5-8+base 60 POOLED: conditional, unlocked
- F9-13 60 POOLED: conditional, unlocked
- F9-13+base 60 POOLED: conditional, unlocked
- F14-18 60 POOLED: conditional, unlocked
- F14-18+base 60 POOLED: conditional, unlocked
- F1-4 60 ASIA: conditional, unlocked
- F1-4+base 60 ASIA: conditional, unlocked
- F5-8 60 ASIA: conditional, unlocked
- F5-8+base 60 ASIA: conditional, unlocked
- F9-13 60 ASIA: conditional, unlocked
- F9-13+base 60 ASIA: conditional, unlocked
- F14-18 60 ASIA: conditional, unlocked
- F14-18+base 60 ASIA: conditional, unlocked
- F1-4 60 LONDON: conditional, unlocked
- F1-4+base 60 LONDON: conditional, unlocked
- F5-8 60 LONDON: conditional, unlocked
- F5-8+base 60 LONDON: conditional, unlocked
- F9-13 60 LONDON: conditional, unlocked
- F9-13+base 60 LONDON: conditional, unlocked
- F14-18 60 LONDON: conditional, unlocked
- F14-18+base 60 LONDON: conditional, unlocked
- F1-4 60 NY: conditional, unlocked
- F1-4+base 60 NY: conditional, unlocked
- F5-8 60 NY: conditional, unlocked
- F5-8+base 60 NY: conditional, unlocked
- F9-13 60 NY: conditional, unlocked
- F9-13+base 60 NY: conditional, unlocked
- F14-18 60 NY: conditional, unlocked
- F14-18+base 60 NY: conditional, unlocked
- F1-4 0 POOLED: conditional, unlocked
- F1-4+base 0 POOLED: conditional, unlocked
- F5-8 0 POOLED: conditional, unlocked
- F5-8+base 0 POOLED: conditional, unlocked
- F9-13 0 POOLED: conditional, unlocked
- F9-13+base 0 POOLED: conditional, unlocked
- F14-18 0 POOLED: conditional, unlocked
- F14-18+base 0 POOLED: conditional, unlocked
- F1-4 0 ASIA: conditional, unlocked
- F1-4+base 0 ASIA: conditional, unlocked
- F5-8 0 ASIA: conditional, unlocked
- F5-8+base 0 ASIA: conditional, unlocked
- F9-13 0 ASIA: conditional, unlocked
- F9-13+base 0 ASIA: conditional, unlocked
- F14-18 0 ASIA: conditional, unlocked
- F14-18+base 0 ASIA: conditional, unlocked
- F1-4 0 LONDON: conditional, unlocked
- F1-4+base 0 LONDON: conditional, unlocked
- F5-8 0 LONDON: conditional, unlocked
- F5-8+base 0 LONDON: conditional, unlocked
- F9-13 0 LONDON: conditional, unlocked
- F9-13+base 0 LONDON: conditional, unlocked
- F14-18 0 LONDON: conditional, unlocked
- F14-18+base 0 LONDON: conditional, unlocked
- F1-4 0 NY: conditional, unlocked
- F1-4+base 0 NY: conditional, unlocked
- F5-8 0 NY: conditional, unlocked
- F5-8+base 0 NY: conditional, unlocked
- F9-13 0 NY: conditional, unlocked
- F9-13+base 0 NY: conditional, unlocked
- F14-18 0 NY: conditional, unlocked
- F14-18+base 0 NY: conditional, unlocked
- F1-4 5 POOLED: conditional, unlocked
- F1-4+base 5 POOLED: conditional, unlocked
- F5-8 5 POOLED: conditional, unlocked
- F5-8+base 5 POOLED: conditional, unlocked
- F9-13 5 POOLED: conditional, unlocked
- F9-13+base 5 POOLED: conditional, unlocked
- F14-18 5 POOLED: conditional, unlocked
- F14-18+base 5 POOLED: conditional, unlocked
- F1-4 5 ASIA: conditional, unlocked
- F1-4+base 5 ASIA: conditional, unlocked
- F5-8 5 ASIA: conditional, unlocked
- F5-8+base 5 ASIA: conditional, unlocked
- F9-13 5 ASIA: conditional, unlocked
- F9-13+base 5 ASIA: conditional, unlocked
- F14-18 5 ASIA: conditional, unlocked
- F14-18+base 5 ASIA: conditional, unlocked
- F1-4 5 LONDON: conditional, unlocked
- F1-4+base 5 LONDON: conditional, unlocked
- F5-8 5 LONDON: conditional, unlocked
- F5-8+base 5 LONDON: conditional, unlocked
- F9-13 5 LONDON: conditional, unlocked
- F9-13+base 5 LONDON: conditional, unlocked
- F14-18 5 LONDON: conditional, unlocked
- F14-18+base 5 LONDON: conditional, unlocked
- F1-4 5 NY: conditional, unlocked
- F1-4+base 5 NY: conditional, unlocked
- F5-8 5 NY: conditional, unlocked
- F5-8+base 5 NY: conditional, unlocked
- F9-13 5 NY: conditional, unlocked
- F9-13+base 5 NY: conditional, unlocked
- F14-18 5 NY: conditional, unlocked
- F14-18+base 5 NY: conditional, unlocked
- F1-4 10 POOLED: conditional, unlocked
- F1-4+base 10 POOLED: conditional, unlocked
- F5-8 10 POOLED: conditional, unlocked
- F5-8+base 10 POOLED: conditional, unlocked
- F9-13 10 POOLED: conditional, unlocked
- F9-13+base 10 POOLED: conditional, unlocked
- F14-18 10 POOLED: conditional, unlocked
- F14-18+base 10 POOLED: conditional, unlocked
- F1-4 10 ASIA: conditional, unlocked
- F1-4+base 10 ASIA: conditional, unlocked
- F5-8 10 ASIA: conditional, unlocked
- F5-8+base 10 ASIA: conditional, unlocked
- F9-13 10 ASIA: conditional, unlocked
- F9-13+base 10 ASIA: conditional, unlocked
- F14-18 10 ASIA: conditional, unlocked
- F14-18+base 10 ASIA: conditional, unlocked
- F1-4 10 LONDON: conditional, unlocked
- F1-4+base 10 LONDON: conditional, unlocked
- F5-8 10 LONDON: conditional, unlocked
- F5-8+base 10 LONDON: conditional, unlocked
- F9-13 10 LONDON: conditional, unlocked
- F9-13+base 10 LONDON: conditional, unlocked
- F14-18 10 LONDON: conditional, unlocked
- F14-18+base 10 LONDON: conditional, unlocked
- F1-4 10 NY: conditional, unlocked
- F1-4+base 10 NY: conditional, unlocked
- F5-8 10 NY: conditional, unlocked
- F5-8+base 10 NY: conditional, unlocked
- F9-13 10 NY: conditional, unlocked
- F9-13+base 10 NY: conditional, unlocked
- F14-18 10 NY: conditional, unlocked
- F14-18+base 10 NY: conditional, unlocked
- F1-4 15 POOLED: conditional, unlocked
- F1-4+base 15 POOLED: conditional, unlocked
- F5-8 15 POOLED: conditional, unlocked
- F5-8+base 15 POOLED: conditional, unlocked
- F9-13 15 POOLED: conditional, unlocked
- F9-13+base 15 POOLED: conditional, unlocked
- F14-18 15 POOLED: conditional, unlocked
- F14-18+base 15 POOLED: conditional, unlocked
- F1-4 15 ASIA: conditional, unlocked
- F1-4+base 15 ASIA: conditional, unlocked
- F5-8 15 ASIA: conditional, unlocked
- F5-8+base 15 ASIA: conditional, unlocked
- F9-13 15 ASIA: conditional, unlocked
- F9-13+base 15 ASIA: conditional, unlocked
- F14-18 15 ASIA: conditional, unlocked
- F14-18+base 15 ASIA: conditional, unlocked
- F1-4 15 LONDON: conditional, unlocked
- F1-4+base 15 LONDON: conditional, unlocked
- F5-8 15 LONDON: conditional, unlocked
- F5-8+base 15 LONDON: conditional, unlocked
- F9-13 15 LONDON: conditional, unlocked
- F9-13+base 15 LONDON: conditional, unlocked
- F14-18 15 LONDON: conditional, unlocked
- F14-18+base 15 LONDON: conditional, unlocked
- F1-4 15 NY: conditional, unlocked
- F1-4+base 15 NY: conditional, unlocked
- F5-8 15 NY: conditional, unlocked
- F5-8+base 15 NY: conditional, unlocked
- F9-13 15 NY: conditional, unlocked
- F9-13+base 15 NY: conditional, unlocked
- F14-18 15 NY: conditional, unlocked
- F14-18+base 15 NY: conditional, unlocked
- F1-4 20 POOLED: conditional, unlocked
- F1-4+base 20 POOLED: conditional, unlocked
- F5-8 20 POOLED: conditional, unlocked
- F5-8+base 20 POOLED: conditional, unlocked
- F9-13 20 POOLED: conditional, unlocked
- F9-13+base 20 POOLED: conditional, unlocked
- F14-18 20 POOLED: conditional, unlocked
- F14-18+base 20 POOLED: conditional, unlocked
- F1-4 20 ASIA: conditional, unlocked
- F1-4+base 20 ASIA: conditional, unlocked
- F5-8 20 ASIA: conditional, unlocked
- F5-8+base 20 ASIA: conditional, unlocked
- F9-13 20 ASIA: conditional, unlocked
- F9-13+base 20 ASIA: conditional, unlocked
- F14-18 20 ASIA: conditional, unlocked
- F14-18+base 20 ASIA: conditional, unlocked
- F1-4 20 LONDON: conditional, unlocked
- F1-4+base 20 LONDON: conditional, unlocked
- F5-8 20 LONDON: conditional, unlocked
- F5-8+base 20 LONDON: conditional, unlocked
- F9-13 20 LONDON: conditional, unlocked
- F9-13+base 20 LONDON: conditional, unlocked
- F14-18 20 LONDON: conditional, unlocked
- F14-18+base 20 LONDON: conditional, unlocked
- F1-4 20 NY: conditional, unlocked
- F1-4+base 20 NY: conditional, unlocked
- F5-8 20 NY: conditional, unlocked
- F5-8+base 20 NY: conditional, unlocked
- F9-13 20 NY: conditional, unlocked
- F9-13+base 20 NY: conditional, unlocked
- F14-18 20 NY: conditional, unlocked
- F14-18+base 20 NY: conditional, unlocked
- F1-4 30 POOLED: conditional, unlocked
- F1-4+base 30 POOLED: conditional, unlocked
- F5-8 30 POOLED: conditional, unlocked
- F5-8+base 30 POOLED: conditional, unlocked
- F9-13 30 POOLED: conditional, unlocked
- F9-13+base 30 POOLED: conditional, unlocked
- F14-18 30 POOLED: conditional, unlocked
- F14-18+base 30 POOLED: conditional, unlocked
- F1-4 30 ASIA: conditional, unlocked
- F1-4+base 30 ASIA: conditional, unlocked
- F5-8 30 ASIA: conditional, unlocked
- F5-8+base 30 ASIA: conditional, unlocked
- F9-13 30 ASIA: conditional, unlocked
- F9-13+base 30 ASIA: conditional, unlocked
- F14-18 30 ASIA: conditional, unlocked
- F14-18+base 30 ASIA: conditional, unlocked
- F1-4 30 LONDON: conditional, unlocked
- F1-4+base 30 LONDON: conditional, unlocked
- F5-8 30 LONDON: conditional, unlocked
- F5-8+base 30 LONDON: conditional, unlocked
- F9-13 30 LONDON: conditional, unlocked
- F9-13+base 30 LONDON: conditional, unlocked
- F14-18 30 LONDON: conditional, unlocked
- F14-18+base 30 LONDON: conditional, unlocked
- F1-4 30 NY: conditional, unlocked
- F1-4+base 30 NY: conditional, unlocked
- F5-8 30 NY: conditional, unlocked
- F5-8+base 30 NY: conditional, unlocked
- F9-13 30 NY: conditional, unlocked
- F9-13+base 30 NY: conditional, unlocked
- F14-18 30 NY: conditional, unlocked
- F14-18+base 30 NY: conditional, unlocked
- F1-4 45 POOLED: conditional, unlocked
- F1-4+base 45 POOLED: conditional, unlocked
- F5-8 45 POOLED: conditional, unlocked
- F5-8+base 45 POOLED: conditional, unlocked
- F9-13 45 POOLED: conditional, unlocked
- F9-13+base 45 POOLED: conditional, unlocked
- F14-18 45 POOLED: conditional, unlocked
- F14-18+base 45 POOLED: conditional, unlocked
- F1-4 45 ASIA: conditional, unlocked
- F1-4+base 45 ASIA: conditional, unlocked
- F5-8 45 ASIA: conditional, unlocked
- F5-8+base 45 ASIA: conditional, unlocked
- F9-13 45 ASIA: conditional, unlocked
- F9-13+base 45 ASIA: conditional, unlocked
- F14-18 45 ASIA: conditional, unlocked
- F14-18+base 45 ASIA: conditional, unlocked
- F1-4 45 LONDON: conditional, unlocked
- F1-4+base 45 LONDON: conditional, unlocked
- F5-8 45 LONDON: conditional, unlocked
- F5-8+base 45 LONDON: conditional, unlocked
- F9-13 45 LONDON: conditional, unlocked
- F9-13+base 45 LONDON: conditional, unlocked
- F14-18 45 LONDON: conditional, unlocked
- F14-18+base 45 LONDON: conditional, unlocked
- F1-4 45 NY: conditional, unlocked
- F1-4+base 45 NY: conditional, unlocked
- F5-8 45 NY: conditional, unlocked
- F5-8+base 45 NY: conditional, unlocked
- F9-13 45 NY: conditional, unlocked
- F9-13+base 45 NY: conditional, unlocked
- F14-18 45 NY: conditional, unlocked
- F14-18+base 45 NY: conditional, unlocked
- F1-4 60 POOLED: conditional, unlocked
- F1-4+base 60 POOLED: conditional, unlocked
- F5-8 60 POOLED: conditional, unlocked
- F5-8+base 60 POOLED: conditional, unlocked
- F9-13 60 POOLED: conditional, unlocked
- F9-13+base 60 POOLED: conditional, unlocked
- F14-18 60 POOLED: conditional, unlocked
- F14-18+base 60 POOLED: conditional, unlocked
- F1-4 60 ASIA: conditional, unlocked
- F1-4+base 60 ASIA: conditional, unlocked
- F5-8 60 ASIA: conditional, unlocked
- F5-8+base 60 ASIA: conditional, unlocked
- F9-13 60 ASIA: conditional, unlocked
- F9-13+base 60 ASIA: conditional, unlocked
- F14-18 60 ASIA: conditional, unlocked
- F14-18+base 60 ASIA: conditional, unlocked
- F1-4 60 LONDON: conditional, unlocked
- F1-4+base 60 LONDON: conditional, unlocked
- F5-8 60 LONDON: conditional, unlocked
- F5-8+base 60 LONDON: conditional, unlocked
- F9-13 60 LONDON: conditional, unlocked
- F9-13+base 60 LONDON: conditional, unlocked
- F14-18 60 LONDON: conditional, unlocked
- F14-18+base 60 LONDON: conditional, unlocked
- F1-4 60 NY: conditional, unlocked
- F1-4+base 60 NY: conditional, unlocked
- F5-8 60 NY: conditional, unlocked
- F5-8+base 60 NY: conditional, unlocked
- F9-13 60 NY: conditional, unlocked
- F9-13+base 60 NY: conditional, unlocked
- F14-18 60 NY: conditional, unlocked
- F14-18+base 60 NY: conditional, unlocked
- F1-4 0 POOLED: conditional, unlocked
- F1-4+base 0 POOLED: conditional, unlocked
- F5-8 0 POOLED: conditional, unlocked
- F5-8+base 0 POOLED: conditional, unlocked
- F9-13 0 POOLED: conditional, unlocked
- F9-13+base 0 POOLED: conditional, unlocked
- F14-18 0 POOLED: conditional, unlocked
- F14-18+base 0 POOLED: conditional, unlocked
- F1-4 0 ASIA: conditional, unlocked
- F1-4+base 0 ASIA: conditional, unlocked
- F5-8 0 ASIA: conditional, unlocked
- F5-8+base 0 ASIA: conditional, unlocked
- F9-13 0 ASIA: conditional, unlocked
- F9-13+base 0 ASIA: conditional, unlocked
- F14-18 0 ASIA: conditional, unlocked
- F14-18+base 0 ASIA: conditional, unlocked
- F1-4 0 LONDON: conditional, unlocked
- F1-4+base 0 LONDON: conditional, unlocked
- F5-8 0 LONDON: conditional, unlocked
- F5-8+base 0 LONDON: conditional, unlocked
- F9-13 0 LONDON: conditional, unlocked
- F9-13+base 0 LONDON: conditional, unlocked
- F14-18 0 LONDON: conditional, unlocked
- F14-18+base 0 LONDON: conditional, unlocked
- F1-4 0 NY: conditional, unlocked
- F1-4+base 0 NY: conditional, unlocked
- F5-8 0 NY: conditional, unlocked
- F5-8+base 0 NY: conditional, unlocked
- F9-13 0 NY: conditional, unlocked
- F9-13+base 0 NY: conditional, unlocked
- F14-18 0 NY: conditional, unlocked
- F14-18+base 0 NY: conditional, unlocked
- F1-4 5 POOLED: conditional, unlocked
- F1-4+base 5 POOLED: conditional, unlocked
- F5-8 5 POOLED: conditional, unlocked
- F5-8+base 5 POOLED: conditional, unlocked
- F9-13 5 POOLED: conditional, unlocked
- F9-13+base 5 POOLED: conditional, unlocked
- F14-18 5 POOLED: conditional, unlocked
- F14-18+base 5 POOLED: conditional, unlocked
- F1-4 5 ASIA: conditional, unlocked
- F1-4+base 5 ASIA: conditional, unlocked
- F5-8 5 ASIA: conditional, unlocked
- F5-8+base 5 ASIA: conditional, unlocked
- F9-13 5 ASIA: conditional, unlocked
- F9-13+base 5 ASIA: conditional, unlocked
- F14-18 5 ASIA: conditional, unlocked
- F14-18+base 5 ASIA: conditional, unlocked
- F1-4 5 LONDON: conditional, unlocked
- F1-4+base 5 LONDON: conditional, unlocked
- F5-8 5 LONDON: conditional, unlocked
- F5-8+base 5 LONDON: conditional, unlocked
- F9-13 5 LONDON: conditional, unlocked
- F9-13+base 5 LONDON: conditional, unlocked
- F14-18 5 LONDON: conditional, unlocked
- F14-18+base 5 LONDON: conditional, unlocked
- F1-4 5 NY: conditional, unlocked
- F1-4+base 5 NY: conditional, unlocked
- F5-8 5 NY: conditional, unlocked
- F5-8+base 5 NY: conditional, unlocked
- F9-13 5 NY: conditional, unlocked
- F9-13+base 5 NY: conditional, unlocked
- F14-18 5 NY: conditional, unlocked
- F14-18+base 5 NY: conditional, unlocked
- F1-4 10 POOLED: conditional, unlocked
- F1-4+base 10 POOLED: conditional, unlocked
- F5-8 10 POOLED: conditional, unlocked
- F5-8+base 10 POOLED: conditional, unlocked
- F9-13 10 POOLED: conditional, unlocked
- F9-13+base 10 POOLED: conditional, unlocked
- F14-18 10 POOLED: conditional, unlocked
- F14-18+base 10 POOLED: conditional, unlocked
- F1-4 10 ASIA: conditional, unlocked
- F1-4+base 10 ASIA: conditional, unlocked
- F5-8 10 ASIA: conditional, unlocked
- F5-8+base 10 ASIA: conditional, unlocked
- F9-13 10 ASIA: conditional, unlocked
- F9-13+base 10 ASIA: conditional, unlocked
- F14-18 10 ASIA: conditional, unlocked
- F14-18+base 10 ASIA: conditional, unlocked
- F1-4 10 LONDON: conditional, unlocked
- F1-4+base 10 LONDON: conditional, unlocked
- F5-8 10 LONDON: conditional, unlocked
- F5-8+base 10 LONDON: conditional, unlocked
- F9-13 10 LONDON: conditional, unlocked
- F9-13+base 10 LONDON: conditional, unlocked
- F14-18 10 LONDON: conditional, unlocked
- F14-18+base 10 LONDON: conditional, unlocked
- F1-4 10 NY: conditional, unlocked
- F1-4+base 10 NY: conditional, unlocked
- F5-8 10 NY: conditional, unlocked
- F5-8+base 10 NY: conditional, unlocked
- F9-13 10 NY: conditional, unlocked
- F9-13+base 10 NY: conditional, unlocked
- F14-18 10 NY: conditional, unlocked
- F14-18+base 10 NY: conditional, unlocked
- F1-4 15 POOLED: conditional, unlocked
- F1-4+base 15 POOLED: conditional, unlocked
- F5-8 15 POOLED: conditional, unlocked
- F5-8+base 15 POOLED: conditional, unlocked
- F9-13 15 POOLED: conditional, unlocked
- F9-13+base 15 POOLED: conditional, unlocked
- F14-18 15 POOLED: conditional, unlocked
- F14-18+base 15 POOLED: conditional, unlocked
- F1-4 15 ASIA: conditional, unlocked
- F1-4+base 15 ASIA: conditional, unlocked
- F5-8 15 ASIA: conditional, unlocked
- F5-8+base 15 ASIA: conditional, unlocked
- F9-13 15 ASIA: conditional, unlocked
- F9-13+base 15 ASIA: conditional, unlocked
- F14-18 15 ASIA: conditional, unlocked
- F14-18+base 15 ASIA: conditional, unlocked
- F1-4 15 LONDON: conditional, unlocked
- F1-4+base 15 LONDON: conditional, unlocked
- F5-8 15 LONDON: conditional, unlocked
- F5-8+base 15 LONDON: conditional, unlocked
- F9-13 15 LONDON: conditional, unlocked
- F9-13+base 15 LONDON: conditional, unlocked
- F14-18 15 LONDON: conditional, unlocked
- F14-18+base 15 LONDON: conditional, unlocked
- F1-4 15 NY: conditional, unlocked
- F1-4+base 15 NY: conditional, unlocked
- F5-8 15 NY: conditional, unlocked
- F5-8+base 15 NY: conditional, unlocked
- F9-13 15 NY: conditional, unlocked
- F9-13+base 15 NY: conditional, unlocked
- F14-18 15 NY: conditional, unlocked
- F14-18+base 15 NY: conditional, unlocked
- F1-4 20 POOLED: conditional, unlocked
- F1-4+base 20 POOLED: conditional, unlocked
- F5-8 20 POOLED: conditional, unlocked
- F5-8+base 20 POOLED: conditional, unlocked
- F9-13 20 POOLED: conditional, unlocked
- F9-13+base 20 POOLED: conditional, unlocked
- F14-18 20 POOLED: conditional, unlocked
- F14-18+base 20 POOLED: conditional, unlocked
- F1-4 20 ASIA: conditional, unlocked
- F1-4+base 20 ASIA: conditional, unlocked
- F5-8 20 ASIA: conditional, unlocked
- F5-8+base 20 ASIA: conditional, unlocked
- F9-13 20 ASIA: conditional, unlocked
- F9-13+base 20 ASIA: conditional, unlocked
- F14-18 20 ASIA: conditional, unlocked
- F14-18+base 20 ASIA: conditional, unlocked
- F1-4 20 LONDON: conditional, unlocked
- F1-4+base 20 LONDON: conditional, unlocked
- F5-8 20 LONDON: conditional, unlocked
- F5-8+base 20 LONDON: conditional, unlocked
- F9-13 20 LONDON: conditional, unlocked
- F9-13+base 20 LONDON: conditional, unlocked
- F14-18 20 LONDON: conditional, unlocked
- F14-18+base 20 LONDON: conditional, unlocked
- F1-4 20 NY: conditional, unlocked
- F1-4+base 20 NY: conditional, unlocked
- F5-8 20 NY: conditional, unlocked
- F5-8+base 20 NY: conditional, unlocked
- F9-13 20 NY: conditional, unlocked
- F9-13+base 20 NY: conditional, unlocked
- F14-18 20 NY: conditional, unlocked
- F14-18+base 20 NY: conditional, unlocked
- F1-4 30 POOLED: conditional, unlocked
- F1-4+base 30 POOLED: conditional, unlocked
- F5-8 30 POOLED: conditional, unlocked
- F5-8+base 30 POOLED: conditional, unlocked
- F9-13 30 POOLED: conditional, unlocked
- F9-13+base 30 POOLED: conditional, unlocked
- F14-18 30 POOLED: conditional, unlocked
- F14-18+base 30 POOLED: conditional, unlocked
- F1-4 30 ASIA: conditional, unlocked
- F1-4+base 30 ASIA: conditional, unlocked
- F5-8 30 ASIA: conditional, unlocked
- F5-8+base 30 ASIA: conditional, unlocked
- F9-13 30 ASIA: conditional, unlocked
- F9-13+base 30 ASIA: conditional, unlocked
- F14-18 30 ASIA: conditional, unlocked
- F14-18+base 30 ASIA: conditional, unlocked
- F1-4 30 LONDON: conditional, unlocked
- F1-4+base 30 LONDON: conditional, unlocked
- F5-8 30 LONDON: conditional, unlocked
- F5-8+base 30 LONDON: conditional, unlocked
- F9-13 30 LONDON: conditional, unlocked
- F9-13+base 30 LONDON: conditional, unlocked
- F14-18 30 LONDON: conditional, unlocked
- F14-18+base 30 LONDON: conditional, unlocked
- F1-4 30 NY: conditional, unlocked
- F1-4+base 30 NY: conditional, unlocked
- F5-8 30 NY: conditional, unlocked
- F5-8+base 30 NY: conditional, unlocked
- F9-13 30 NY: conditional, unlocked
- F9-13+base 30 NY: conditional, unlocked
- F14-18 30 NY: conditional, unlocked
- F14-18+base 30 NY: conditional, unlocked
- F1-4 45 POOLED: conditional, unlocked
- F1-4+base 45 POOLED: conditional, unlocked
- F5-8 45 POOLED: conditional, unlocked
- F5-8+base 45 POOLED: conditional, unlocked
- F9-13 45 POOLED: conditional, unlocked
- F9-13+base 45 POOLED: conditional, unlocked
- F14-18 45 POOLED: conditional, unlocked
- F14-18+base 45 POOLED: conditional, unlocked
- F1-4 45 ASIA: conditional, unlocked
- F1-4+base 45 ASIA: conditional, unlocked
- F5-8 45 ASIA: conditional, unlocked
- F5-8+base 45 ASIA: conditional, unlocked
- F9-13 45 ASIA: conditional, unlocked
- F9-13+base 45 ASIA: conditional, unlocked
- F14-18 45 ASIA: conditional, unlocked
- F14-18+base 45 ASIA: conditional, unlocked
- F1-4 45 LONDON: conditional, unlocked
- F1-4+base 45 LONDON: conditional, unlocked
- F5-8 45 LONDON: conditional, unlocked
- F5-8+base 45 LONDON: conditional, unlocked
- F9-13 45 LONDON: conditional, unlocked
- F9-13+base 45 LONDON: conditional, unlocked
- F14-18 45 LONDON: conditional, unlocked
- F14-18+base 45 LONDON: conditional, unlocked
- F1-4 45 NY: conditional, unlocked
- F1-4+base 45 NY: conditional, unlocked
- F5-8 45 NY: conditional, unlocked
- F5-8+base 45 NY: conditional, unlocked
- F9-13 45 NY: conditional, unlocked
- F9-13+base 45 NY: conditional, unlocked
- F14-18 45 NY: conditional, unlocked
- F14-18+base 45 NY: conditional, unlocked
- F1-4 60 POOLED: conditional, unlocked
- F1-4+base 60 POOLED: conditional, unlocked
- F5-8 60 POOLED: conditional, unlocked
- F5-8+base 60 POOLED: conditional, unlocked
- F9-13 60 POOLED: conditional, unlocked
- F9-13+base 60 POOLED: conditional, unlocked
- F14-18 60 POOLED: conditional, unlocked
- F14-18+base 60 POOLED: conditional, unlocked
- F1-4 60 ASIA: conditional, unlocked
- F1-4+base 60 ASIA: conditional, unlocked
- F5-8 60 ASIA: conditional, unlocked
- F5-8+base 60 ASIA: conditional, unlocked
- F9-13 60 ASIA: conditional, unlocked
- F9-13+base 60 ASIA: conditional, unlocked
- F14-18 60 ASIA: conditional, unlocked
- F14-18+base 60 ASIA: conditional, unlocked
- F1-4 60 LONDON: conditional, unlocked
- F1-4+base 60 LONDON: conditional, unlocked
- F5-8 60 LONDON: conditional, unlocked
- F5-8+base 60 LONDON: conditional, unlocked
- F9-13 60 LONDON: conditional, unlocked
- F9-13+base 60 LONDON: conditional, unlocked
- F14-18 60 LONDON: conditional, unlocked
- F14-18+base 60 LONDON: conditional, unlocked
- F1-4 60 NY: conditional, unlocked
- F1-4+base 60 NY: conditional, unlocked
- F5-8 60 NY: conditional, unlocked
- F5-8+base 60 NY: conditional, unlocked
- F9-13 60 NY: conditional, unlocked
- F9-13+base 60 NY: conditional, unlocked
- F14-18 60 NY: conditional, unlocked
- F14-18+base 60 NY: conditional, unlocked
- F1-4 0 POOLED: conditional, unlocked
- F1-4+base 0 POOLED: conditional, unlocked
- F5-8 0 POOLED: conditional, unlocked
- F5-8+base 0 POOLED: conditional, unlocked
- F9-13 0 POOLED: conditional, unlocked
- F9-13+base 0 POOLED: conditional, unlocked
- F14-18 0 POOLED: conditional, unlocked
- F14-18+base 0 POOLED: conditional, unlocked
- F1-4 0 ASIA: conditional, unlocked
- F1-4+base 0 ASIA: conditional, unlocked
- F5-8 0 ASIA: conditional, unlocked
- F5-8+base 0 ASIA: conditional, unlocked
- F9-13 0 ASIA: conditional, unlocked
- F9-13+base 0 ASIA: conditional, unlocked
- F14-18 0 ASIA: conditional, unlocked
- F14-18+base 0 ASIA: conditional, unlocked
- F1-4 0 LONDON: conditional, unlocked
- F1-4+base 0 LONDON: conditional, unlocked
- F5-8 0 LONDON: conditional, unlocked
- F5-8+base 0 LONDON: conditional, unlocked
- F9-13 0 LONDON: conditional, unlocked
- F9-13+base 0 LONDON: conditional, unlocked
- F14-18 0 LONDON: conditional, unlocked
- F14-18+base 0 LONDON: conditional, unlocked
- F1-4 0 NY: conditional, unlocked
- F1-4+base 0 NY: conditional, unlocked
- F5-8 0 NY: conditional, unlocked
- F5-8+base 0 NY: conditional, unlocked
- F9-13 0 NY: conditional, unlocked
- F9-13+base 0 NY: conditional, unlocked
- F14-18 0 NY: conditional, unlocked
- F14-18+base 0 NY: conditional, unlocked
- F1-4 5 POOLED: conditional, unlocked
- F1-4+base 5 POOLED: conditional, unlocked
- F5-8 5 POOLED: conditional, unlocked
- F5-8+base 5 POOLED: conditional, unlocked
- F9-13 5 POOLED: conditional, unlocked
- F9-13+base 5 POOLED: conditional, unlocked
- F14-18 5 POOLED: conditional, unlocked
- F14-18+base 5 POOLED: conditional, unlocked
- F1-4 5 ASIA: conditional, unlocked
- F1-4+base 5 ASIA: conditional, unlocked
- F5-8 5 ASIA: conditional, unlocked
- F5-8+base 5 ASIA: conditional, unlocked
- F9-13 5 ASIA: conditional, unlocked
- F9-13+base 5 ASIA: conditional, unlocked
- F14-18 5 ASIA: conditional, unlocked
- F14-18+base 5 ASIA: conditional, unlocked
- F1-4 5 LONDON: conditional, unlocked
- F1-4+base 5 LONDON: conditional, unlocked
- F5-8 5 LONDON: conditional, unlocked
- F5-8+base 5 LONDON: conditional, unlocked
- F9-13 5 LONDON: conditional, unlocked
- F9-13+base 5 LONDON: conditional, unlocked
- F14-18 5 LONDON: conditional, unlocked
- F14-18+base 5 LONDON: conditional, unlocked
- F1-4 5 NY: conditional, unlocked
- F1-4+base 5 NY: conditional, unlocked
- F5-8 5 NY: conditional, unlocked
- F5-8+base 5 NY: conditional, unlocked
- F9-13 5 NY: conditional, unlocked
- F9-13+base 5 NY: conditional, unlocked
- F14-18 5 NY: conditional, unlocked
- F14-18+base 5 NY: conditional, unlocked
- F1-4 10 POOLED: conditional, unlocked
- F1-4+base 10 POOLED: conditional, unlocked
- F5-8 10 POOLED: conditional, unlocked
- F5-8+base 10 POOLED: conditional, unlocked
- F9-13 10 POOLED: conditional, unlocked
- F9-13+base 10 POOLED: conditional, unlocked
- F14-18 10 POOLED: conditional, unlocked
- F14-18+base 10 POOLED: conditional, unlocked
- F1-4 10 ASIA: conditional, unlocked
- F1-4+base 10 ASIA: conditional, unlocked
- F5-8 10 ASIA: conditional, unlocked
- F5-8+base 10 ASIA: conditional, unlocked
- F9-13 10 ASIA: conditional, unlocked
- F9-13+base 10 ASIA: conditional, unlocked
- F14-18 10 ASIA: conditional, unlocked
- F14-18+base 10 ASIA: conditional, unlocked
- F1-4 10 LONDON: conditional, unlocked
- F1-4+base 10 LONDON: conditional, unlocked
- F5-8 10 LONDON: conditional, unlocked
- F5-8+base 10 LONDON: conditional, unlocked
- F9-13 10 LONDON: conditional, unlocked
- F9-13+base 10 LONDON: conditional, unlocked
- F14-18 10 LONDON: conditional, unlocked
- F14-18+base 10 LONDON: conditional, unlocked
- F1-4 10 NY: conditional, unlocked
- F1-4+base 10 NY: conditional, unlocked
- F5-8 10 NY: conditional, unlocked
- F5-8+base 10 NY: conditional, unlocked
- F9-13 10 NY: conditional, unlocked
- F9-13+base 10 NY: conditional, unlocked
- F14-18 10 NY: conditional, unlocked
- F14-18+base 10 NY: conditional, unlocked
- F1-4 15 POOLED: conditional, unlocked
- F1-4+base 15 POOLED: conditional, unlocked
- F5-8 15 POOLED: conditional, unlocked
- F5-8+base 15 POOLED: conditional, unlocked
- F9-13 15 POOLED: conditional, unlocked
- F9-13+base 15 POOLED: conditional, unlocked
- F14-18 15 POOLED: conditional, unlocked
- F14-18+base 15 POOLED: conditional, unlocked
- F1-4 15 ASIA: conditional, unlocked
- F1-4+base 15 ASIA: conditional, unlocked
- F5-8 15 ASIA: conditional, unlocked
- F5-8+base 15 ASIA: conditional, unlocked
- F9-13 15 ASIA: conditional, unlocked
- F9-13+base 15 ASIA: conditional, unlocked
- F14-18 15 ASIA: conditional, unlocked
- F14-18+base 15 ASIA: conditional, unlocked
- F1-4 15 LONDON: conditional, unlocked
- F1-4+base 15 LONDON: conditional, unlocked
- F5-8 15 LONDON: conditional, unlocked
- F5-8+base 15 LONDON: conditional, unlocked
- F9-13 15 LONDON: conditional, unlocked
- F9-13+base 15 LONDON: conditional, unlocked
- F14-18 15 LONDON: conditional, unlocked
- F14-18+base 15 LONDON: conditional, unlocked
- F1-4 15 NY: conditional, unlocked
- F1-4+base 15 NY: conditional, unlocked
- F5-8 15 NY: conditional, unlocked
- F5-8+base 15 NY: conditional, unlocked
- F9-13 15 NY: conditional, unlocked
- F9-13+base 15 NY: conditional, unlocked
- F14-18 15 NY: conditional, unlocked
- F14-18+base 15 NY: conditional, unlocked
- F1-4 20 POOLED: conditional, unlocked
- F1-4+base 20 POOLED: conditional, unlocked
- F5-8 20 POOLED: conditional, unlocked
- F5-8+base 20 POOLED: conditional, unlocked
- F9-13 20 POOLED: conditional, unlocked
- F9-13+base 20 POOLED: conditional, unlocked
- F14-18 20 POOLED: conditional, unlocked
- F14-18+base 20 POOLED: conditional, unlocked
- F1-4 20 ASIA: conditional, unlocked
- F1-4+base 20 ASIA: conditional, unlocked
- F5-8 20 ASIA: conditional, unlocked
- F5-8+base 20 ASIA: conditional, unlocked
- F9-13 20 ASIA: conditional, unlocked
- F9-13+base 20 ASIA: conditional, unlocked
- F14-18 20 ASIA: conditional, unlocked
- F14-18+base 20 ASIA: conditional, unlocked
- F1-4 20 LONDON: conditional, unlocked
- F1-4+base 20 LONDON: conditional, unlocked
- F5-8 20 LONDON: conditional, unlocked
- F5-8+base 20 LONDON: conditional, unlocked
- F9-13 20 LONDON: conditional, unlocked
- F9-13+base 20 LONDON: conditional, unlocked
- F14-18 20 LONDON: conditional, unlocked
- F14-18+base 20 LONDON: conditional, unlocked
- F1-4 20 NY: conditional, unlocked
- F1-4+base 20 NY: conditional, unlocked
- F5-8 20 NY: conditional, unlocked
- F5-8+base 20 NY: conditional, unlocked
- F9-13 20 NY: conditional, unlocked
- F9-13+base 20 NY: conditional, unlocked
- F14-18 20 NY: conditional, unlocked
- F14-18+base 20 NY: conditional, unlocked
- F1-4 30 POOLED: conditional, unlocked
- F1-4+base 30 POOLED: conditional, unlocked
- F5-8 30 POOLED: conditional, unlocked
- F5-8+base 30 POOLED: conditional, unlocked
- F9-13 30 POOLED: conditional, unlocked
- F9-13+base 30 POOLED: conditional, unlocked
- F14-18 30 POOLED: conditional, unlocked
- F14-18+base 30 POOLED: conditional, unlocked
- F1-4 30 ASIA: conditional, unlocked
- F1-4+base 30 ASIA: conditional, unlocked
- F5-8 30 ASIA: conditional, unlocked
- F5-8+base 30 ASIA: conditional, unlocked
- F9-13 30 ASIA: conditional, unlocked
- F9-13+base 30 ASIA: conditional, unlocked
- F14-18 30 ASIA: conditional, unlocked
- F14-18+base 30 ASIA: conditional, unlocked
- F1-4 30 LONDON: conditional, unlocked
- F1-4+base 30 LONDON: conditional, unlocked
- F5-8 30 LONDON: conditional, unlocked
- F5-8+base 30 LONDON: conditional, unlocked
- F9-13 30 LONDON: conditional, unlocked
- F9-13+base 30 LONDON: conditional, unlocked
- F14-18 30 LONDON: conditional, unlocked
- F14-18+base 30 LONDON: conditional, unlocked
- F1-4 30 NY: conditional, unlocked
- F1-4+base 30 NY: conditional, unlocked
- F5-8 30 NY: conditional, unlocked
- F5-8+base 30 NY: conditional, unlocked
- F9-13 30 NY: conditional, unlocked
- F9-13+base 30 NY: conditional, unlocked
- F14-18 30 NY: conditional, unlocked
- F14-18+base 30 NY: conditional, unlocked
- F1-4 45 POOLED: conditional, unlocked
- F1-4+base 45 POOLED: conditional, unlocked
- F5-8 45 POOLED: conditional, unlocked
- F5-8+base 45 POOLED: conditional, unlocked
- F9-13 45 POOLED: conditional, unlocked
- F9-13+base 45 POOLED: conditional, unlocked
- F14-18 45 POOLED: conditional, unlocked
- F14-18+base 45 POOLED: conditional, unlocked
- F1-4 45 ASIA: conditional, unlocked
- F1-4+base 45 ASIA: conditional, unlocked
- F5-8 45 ASIA: conditional, unlocked
- F5-8+base 45 ASIA: conditional, unlocked
- F9-13 45 ASIA: conditional, unlocked
- F9-13+base 45 ASIA: conditional, unlocked
- F14-18 45 ASIA: conditional, unlocked
- F14-18+base 45 ASIA: conditional, unlocked
- F1-4 45 LONDON: conditional, unlocked
- F1-4+base 45 LONDON: conditional, unlocked
- F5-8 45 LONDON: conditional, unlocked
- F5-8+base 45 LONDON: conditional, unlocked
- F9-13 45 LONDON: conditional, unlocked
- F9-13+base 45 LONDON: conditional, unlocked
- F14-18 45 LONDON: conditional, unlocked
- F14-18+base 45 LONDON: conditional, unlocked
- F1-4 45 NY: conditional, unlocked
- F1-4+base 45 NY: conditional, unlocked
- F5-8 45 NY: conditional, unlocked
- F5-8+base 45 NY: conditional, unlocked
- F9-13 45 NY: conditional, unlocked
- F9-13+base 45 NY: conditional, unlocked
- F14-18 45 NY: conditional, unlocked
- F14-18+base 45 NY: conditional, unlocked
- F1-4 60 POOLED: conditional, unlocked
- F1-4+base 60 POOLED: conditional, unlocked
- F5-8 60 POOLED: conditional, unlocked
- F5-8+base 60 POOLED: conditional, unlocked
- F9-13 60 POOLED: conditional, unlocked
- F9-13+base 60 POOLED: conditional, unlocked
- F14-18 60 POOLED: conditional, unlocked
- F14-18+base 60 POOLED: conditional, unlocked
- F1-4 60 ASIA: conditional, unlocked
- F1-4+base 60 ASIA: conditional, unlocked
- F5-8 60 ASIA: conditional, unlocked
- F5-8+base 60 ASIA: conditional, unlocked
- F9-13 60 ASIA: conditional, unlocked
- F9-13+base 60 ASIA: conditional, unlocked
- F14-18 60 ASIA: conditional, unlocked
- F14-18+base 60 ASIA: conditional, unlocked
- F1-4 60 LONDON: conditional, unlocked
- F1-4+base 60 LONDON: conditional, unlocked
- F5-8 60 LONDON: conditional, unlocked
- F5-8+base 60 LONDON: conditional, unlocked
- F9-13 60 LONDON: conditional, unlocked
- F9-13+base 60 LONDON: conditional, unlocked
- F14-18 60 LONDON: conditional, unlocked
- F14-18+base 60 LONDON: conditional, unlocked
- F1-4 60 NY: conditional, unlocked
- F1-4+base 60 NY: conditional, unlocked
- F5-8 60 NY: conditional, unlocked
- F5-8+base 60 NY: conditional, unlocked
- F9-13 60 NY: conditional, unlocked
- F9-13+base 60 NY: conditional, unlocked
- F14-18 60 NY: conditional, unlocked
- F14-18+base 60 NY: conditional, unlocked
- F1-4 0 POOLED: conditional, unlocked
- F1-4+base 0 POOLED: conditional, unlocked
- F5-8 0 POOLED: conditional, unlocked
- F5-8+base 0 POOLED: conditional, unlocked
- F9-13 0 POOLED: conditional, unlocked
- F9-13+base 0 POOLED: conditional, unlocked
- F14-18 0 POOLED: conditional, unlocked
- F14-18+base 0 POOLED: conditional, unlocked
- F1-4 0 ASIA: conditional, unlocked
- F1-4+base 0 ASIA: conditional, unlocked
- F5-8 0 ASIA: conditional, unlocked
- F5-8+base 0 ASIA: conditional, unlocked
- F9-13 0 ASIA: conditional, unlocked
- F9-13+base 0 ASIA: conditional, unlocked
- F14-18 0 ASIA: conditional, unlocked
- F14-18+base 0 ASIA: conditional, unlocked
- F1-4 0 LONDON: conditional, unlocked
- F1-4+base 0 LONDON: conditional, unlocked
- F5-8 0 LONDON: conditional, unlocked
- F5-8+base 0 LONDON: conditional, unlocked
- F9-13 0 LONDON: conditional, unlocked
- F9-13+base 0 LONDON: conditional, unlocked
- F14-18 0 LONDON: conditional, unlocked
- F14-18+base 0 LONDON: conditional, unlocked
- F1-4 0 NY: conditional, unlocked
- F1-4+base 0 NY: conditional, unlocked
- F5-8 0 NY: conditional, unlocked
- F5-8+base 0 NY: conditional, unlocked
- F9-13 0 NY: conditional, unlocked
- F9-13+base 0 NY: conditional, unlocked
- F14-18 0 NY: conditional, unlocked
- F14-18+base 0 NY: conditional, unlocked
- F1-4 5 POOLED: conditional, unlocked
- F1-4+base 5 POOLED: conditional, unlocked
- F5-8 5 POOLED: conditional, unlocked
- F5-8+base 5 POOLED: conditional, unlocked
- F9-13 5 POOLED: conditional, unlocked
- F9-13+base 5 POOLED: conditional, unlocked
- F14-18 5 POOLED: conditional, unlocked
- F14-18+base 5 POOLED: conditional, unlocked
- F1-4 5 ASIA: conditional, unlocked
- F1-4+base 5 ASIA: conditional, unlocked
- F5-8 5 ASIA: conditional, unlocked
- F5-8+base 5 ASIA: conditional, unlocked
- F9-13 5 ASIA: conditional, unlocked
- F9-13+base 5 ASIA: conditional, unlocked
- F14-18 5 ASIA: conditional, unlocked
- F14-18+base 5 ASIA: conditional, unlocked
- F1-4 5 LONDON: conditional, unlocked
- F1-4+base 5 LONDON: conditional, unlocked
- F5-8 5 LONDON: conditional, unlocked
- F5-8+base 5 LONDON: conditional, unlocked
- F9-13 5 LONDON: conditional, unlocked
- F9-13+base 5 LONDON: conditional, unlocked
- F14-18 5 LONDON: conditional, unlocked
- F14-18+base 5 LONDON: conditional, unlocked
- F1-4 5 NY: conditional, unlocked
- F1-4+base 5 NY: conditional, unlocked
- F5-8 5 NY: conditional, unlocked
- F5-8+base 5 NY: conditional, unlocked
- F9-13 5 NY: conditional, unlocked
- F9-13+base 5 NY: conditional, unlocked
- F14-18 5 NY: conditional, unlocked
- F14-18+base 5 NY: conditional, unlocked
- F1-4 10 POOLED: conditional, unlocked
- F1-4+base 10 POOLED: conditional, unlocked
- F5-8 10 POOLED: conditional, unlocked
- F5-8+base 10 POOLED: conditional, unlocked
- F9-13 10 POOLED: conditional, unlocked
- F9-13+base 10 POOLED: conditional, unlocked
- F14-18 10 POOLED: conditional, unlocked
- F14-18+base 10 POOLED: conditional, unlocked
- F1-4 10 ASIA: conditional, unlocked
- F1-4+base 10 ASIA: conditional, unlocked
- F5-8 10 ASIA: conditional, unlocked
- F5-8+base 10 ASIA: conditional, unlocked
- F9-13 10 ASIA: conditional, unlocked
- F9-13+base 10 ASIA: conditional, unlocked
- F14-18 10 ASIA: conditional, unlocked
- F14-18+base 10 ASIA: conditional, unlocked
- F1-4 10 LONDON: conditional, unlocked
- F1-4+base 10 LONDON: conditional, unlocked
- F5-8 10 LONDON: conditional, unlocked
- F5-8+base 10 LONDON: conditional, unlocked
- F9-13 10 LONDON: conditional, unlocked
- F9-13+base 10 LONDON: conditional, unlocked
- F14-18 10 LONDON: conditional, unlocked
- F14-18+base 10 LONDON: conditional, unlocked
- F1-4 10 NY: conditional, unlocked
- F1-4+base 10 NY: conditional, unlocked
- F5-8 10 NY: conditional, unlocked
- F5-8+base 10 NY: conditional, unlocked
- F9-13 10 NY: conditional, unlocked
- F9-13+base 10 NY: conditional, unlocked
- F14-18 10 NY: conditional, unlocked
- F14-18+base 10 NY: conditional, unlocked
- F1-4 15 POOLED: conditional, unlocked
- F1-4+base 15 POOLED: conditional, unlocked
- F5-8 15 POOLED: conditional, unlocked
- F5-8+base 15 POOLED: conditional, unlocked
- F9-13 15 POOLED: conditional, unlocked
- F9-13+base 15 POOLED: conditional, unlocked
- F14-18 15 POOLED: conditional, unlocked
- F14-18+base 15 POOLED: conditional, unlocked
- F1-4 15 ASIA: conditional, unlocked
- F1-4+base 15 ASIA: conditional, unlocked
- F5-8 15 ASIA: conditional, unlocked
- F5-8+base 15 ASIA: conditional, unlocked
- F9-13 15 ASIA: conditional, unlocked
- F9-13+base 15 ASIA: conditional, unlocked
- F14-18 15 ASIA: conditional, unlocked
- F14-18+base 15 ASIA: conditional, unlocked
- F1-4 15 LONDON: conditional, unlocked
- F1-4+base 15 LONDON: conditional, unlocked
- F5-8 15 LONDON: conditional, unlocked
- F5-8+base 15 LONDON: conditional, unlocked
- F9-13 15 LONDON: conditional, unlocked
- F9-13+base 15 LONDON: conditional, unlocked
- F14-18 15 LONDON: conditional, unlocked
- F14-18+base 15 LONDON: conditional, unlocked
- F1-4 15 NY: conditional, unlocked
- F1-4+base 15 NY: conditional, unlocked
- F5-8 15 NY: conditional, unlocked
- F5-8+base 15 NY: conditional, unlocked
- F9-13 15 NY: conditional, unlocked
- F9-13+base 15 NY: conditional, unlocked
- F14-18 15 NY: conditional, unlocked
- F14-18+base 15 NY: conditional, unlocked
- F1-4 20 POOLED: conditional, unlocked
- F1-4+base 20 POOLED: conditional, unlocked
- F5-8 20 POOLED: conditional, unlocked
- F5-8+base 20 POOLED: conditional, unlocked
- F9-13 20 POOLED: conditional, unlocked
- F9-13+base 20 POOLED: conditional, unlocked
- F14-18 20 POOLED: conditional, unlocked
- F14-18+base 20 POOLED: conditional, unlocked
- F1-4 20 ASIA: conditional, unlocked
- F1-4+base 20 ASIA: conditional, unlocked
- F5-8 20 ASIA: conditional, unlocked
- F5-8+base 20 ASIA: conditional, unlocked
- F9-13 20 ASIA: conditional, unlocked
- F9-13+base 20 ASIA: conditional, unlocked
- F14-18 20 ASIA: conditional, unlocked
- F14-18+base 20 ASIA: conditional, unlocked
- F1-4 20 LONDON: conditional, unlocked
- F1-4+base 20 LONDON: conditional, unlocked
- F5-8 20 LONDON: conditional, unlocked
- F5-8+base 20 LONDON: conditional, unlocked
- F9-13 20 LONDON: conditional, unlocked
- F9-13+base 20 LONDON: conditional, unlocked
- F14-18 20 LONDON: conditional, unlocked
- F14-18+base 20 LONDON: conditional, unlocked
- F1-4 20 NY: conditional, unlocked
- F1-4+base 20 NY: conditional, unlocked
- F5-8 20 NY: conditional, unlocked
- F5-8+base 20 NY: conditional, unlocked
- F9-13 20 NY: conditional, unlocked
- F9-13+base 20 NY: conditional, unlocked
- F14-18 20 NY: conditional, unlocked
- F14-18+base 20 NY: conditional, unlocked
- F1-4 30 POOLED: conditional, unlocked
- F1-4+base 30 POOLED: conditional, unlocked
- F5-8 30 POOLED: conditional, unlocked
- F5-8+base 30 POOLED: conditional, unlocked
- F9-13 30 POOLED: conditional, unlocked
- F9-13+base 30 POOLED: conditional, unlocked
- F14-18 30 POOLED: conditional, unlocked
- F14-18+base 30 POOLED: conditional, unlocked
- F1-4 30 ASIA: conditional, unlocked
- F1-4+base 30 ASIA: conditional, unlocked
- F5-8 30 ASIA: conditional, unlocked
- F5-8+base 30 ASIA: conditional, unlocked
- F9-13 30 ASIA: conditional, unlocked
- F9-13+base 30 ASIA: conditional, unlocked
- F14-18 30 ASIA: conditional, unlocked
- F14-18+base 30 ASIA: conditional, unlocked
- F1-4 30 LONDON: conditional, unlocked
- F1-4+base 30 LONDON: conditional, unlocked
- F5-8 30 LONDON: conditional, unlocked
- F5-8+base 30 LONDON: conditional, unlocked
- F9-13 30 LONDON: conditional, unlocked
- F9-13+base 30 LONDON: conditional, unlocked
- F14-18 30 LONDON: conditional, unlocked
- F14-18+base 30 LONDON: conditional, unlocked
- F1-4 30 NY: conditional, unlocked
- F1-4+base 30 NY: conditional, unlocked
- F5-8 30 NY: conditional, unlocked
- F5-8+base 30 NY: conditional, unlocked
- F9-13 30 NY: conditional, unlocked
- F9-13+base 30 NY: conditional, unlocked
- F14-18 30 NY: conditional, unlocked
- F14-18+base 30 NY: conditional, unlocked
- F1-4 45 POOLED: conditional, unlocked
- F1-4+base 45 POOLED: conditional, unlocked
- F5-8 45 POOLED: conditional, unlocked
- F5-8+base 45 POOLED: conditional, unlocked
- F9-13 45 POOLED: conditional, unlocked
- F9-13+base 45 POOLED: conditional, unlocked
- F14-18 45 POOLED: conditional, unlocked
- F14-18+base 45 POOLED: conditional, unlocked
- F1-4 45 ASIA: conditional, unlocked
- F1-4+base 45 ASIA: conditional, unlocked
- F5-8 45 ASIA: conditional, unlocked
- F5-8+base 45 ASIA: conditional, unlocked
- F9-13 45 ASIA: conditional, unlocked
- F9-13+base 45 ASIA: conditional, unlocked
- F14-18 45 ASIA: conditional, unlocked
- F14-18+base 45 ASIA: conditional, unlocked
- F1-4 45 LONDON: conditional, unlocked
- F1-4+base 45 LONDON: conditional, unlocked
- F5-8 45 LONDON: conditional, unlocked
- F5-8+base 45 LONDON: conditional, unlocked
- F9-13 45 LONDON: conditional, unlocked
- F9-13+base 45 LONDON: conditional, unlocked
- F14-18 45 LONDON: conditional, unlocked
- F14-18+base 45 LONDON: conditional, unlocked
- F1-4 45 NY: conditional, unlocked
- F1-4+base 45 NY: conditional, unlocked
- F5-8 45 NY: conditional, unlocked
- F5-8+base 45 NY: conditional, unlocked
- F9-13 45 NY: conditional, unlocked
- F9-13+base 45 NY: conditional, unlocked
- F14-18 45 NY: conditional, unlocked
- F14-18+base 45 NY: conditional, unlocked
- F1-4 60 POOLED: conditional, unlocked
- F1-4+base 60 POOLED: conditional, unlocked
- F5-8 60 POOLED: conditional, unlocked
- F5-8+base 60 POOLED: conditional, unlocked
- F9-13 60 POOLED: conditional, unlocked
- F9-13+base 60 POOLED: conditional, unlocked
- F14-18 60 POOLED: conditional, unlocked
- F14-18+base 60 POOLED: conditional, unlocked
- F1-4 60 ASIA: conditional, unlocked
- F1-4+base 60 ASIA: conditional, unlocked
- F5-8 60 ASIA: conditional, unlocked
- F5-8+base 60 ASIA: conditional, unlocked
- F9-13 60 ASIA: conditional, unlocked
- F9-13+base 60 ASIA: conditional, unlocked
- F14-18 60 ASIA: conditional, unlocked
- F14-18+base 60 ASIA: conditional, unlocked
- F1-4 60 LONDON: conditional, unlocked
- F1-4+base 60 LONDON: conditional, unlocked
- F5-8 60 LONDON: conditional, unlocked
- F5-8+base 60 LONDON: conditional, unlocked
- F9-13 60 LONDON: conditional, unlocked
- F9-13+base 60 LONDON: conditional, unlocked
- F14-18 60 LONDON: conditional, unlocked
- F14-18+base 60 LONDON: conditional, unlocked
- F1-4 60 NY: conditional, unlocked
- F1-4+base 60 NY: conditional, unlocked
- F5-8 60 NY: conditional, unlocked
- F5-8+base 60 NY: conditional, unlocked
- F9-13 60 NY: conditional, unlocked
- F9-13+base 60 NY: conditional, unlocked
- F14-18 60 NY: conditional, unlocked
- F14-18+base 60 NY: conditional, unlocked
- F1-4 0 POOLED: conditional, unlocked
- F1-4+base 0 POOLED: conditional, unlocked
- F5-8 0 POOLED: conditional, unlocked
- F5-8+base 0 POOLED: conditional, unlocked
- F9-13 0 POOLED: conditional, unlocked
- F9-13+base 0 POOLED: conditional, unlocked
- F14-18 0 POOLED: conditional, unlocked
- F14-18+base 0 POOLED: conditional, unlocked
- F1-4 0 ASIA: conditional, unlocked
- F1-4+base 0 ASIA: conditional, unlocked
- F5-8 0 ASIA: conditional, unlocked
- F5-8+base 0 ASIA: conditional, unlocked
- F9-13 0 ASIA: conditional, unlocked
- F9-13+base 0 ASIA: conditional, unlocked
- F14-18 0 ASIA: conditional, unlocked
- F14-18+base 0 ASIA: conditional, unlocked
- F1-4 0 LONDON: conditional, unlocked
- F1-4+base 0 LONDON: conditional, unlocked
- F5-8 0 LONDON: conditional, unlocked
- F5-8+base 0 LONDON: conditional, unlocked
- F9-13 0 LONDON: conditional, unlocked
- F9-13+base 0 LONDON: conditional, unlocked
- F14-18 0 LONDON: conditional, unlocked
- F14-18+base 0 LONDON: conditional, unlocked
- F1-4 0 NY: conditional, unlocked
- F1-4+base 0 NY: conditional, unlocked
- F5-8 0 NY: conditional, unlocked
- F5-8+base 0 NY: conditional, unlocked
- F9-13 0 NY: conditional, unlocked
- F9-13+base 0 NY: conditional, unlocked
- F14-18 0 NY: conditional, unlocked
- F14-18+base 0 NY: conditional, unlocked
- F1-4 5 POOLED: conditional, unlocked
- F1-4+base 5 POOLED: conditional, unlocked
- F5-8 5 POOLED: conditional, unlocked
- F5-8+base 5 POOLED: conditional, unlocked
- F9-13 5 POOLED: conditional, unlocked
- F9-13+base 5 POOLED: conditional, unlocked
- F14-18 5 POOLED: conditional, unlocked
- F14-18+base 5 POOLED: conditional, unlocked
- F1-4 5 ASIA: conditional, unlocked
- F1-4+base 5 ASIA: conditional, unlocked
- F5-8 5 ASIA: conditional, unlocked
- F5-8+base 5 ASIA: conditional, unlocked
- F9-13 5 ASIA: conditional, unlocked
- F9-13+base 5 ASIA: conditional, unlocked
- F14-18 5 ASIA: conditional, unlocked
- F14-18+base 5 ASIA: conditional, unlocked
- F1-4 5 LONDON: conditional, unlocked
- F1-4+base 5 LONDON: conditional, unlocked
- F5-8 5 LONDON: conditional, unlocked
- F5-8+base 5 LONDON: conditional, unlocked
- F9-13 5 LONDON: conditional, unlocked
- F9-13+base 5 LONDON: conditional, unlocked
- F14-18 5 LONDON: conditional, unlocked
- F14-18+base 5 LONDON: conditional, unlocked
- F1-4 5 NY: conditional, unlocked
- F1-4+base 5 NY: conditional, unlocked
- F5-8 5 NY: conditional, unlocked
- F5-8+base 5 NY: conditional, unlocked
- F9-13 5 NY: conditional, unlocked
- F9-13+base 5 NY: conditional, unlocked
- F14-18 5 NY: conditional, unlocked
- F14-18+base 5 NY: conditional, unlocked
- F1-4 10 POOLED: conditional, unlocked
- F1-4+base 10 POOLED: conditional, unlocked
- F5-8 10 POOLED: conditional, unlocked
- F5-8+base 10 POOLED: conditional, unlocked
- F9-13 10 POOLED: conditional, unlocked
- F9-13+base 10 POOLED: conditional, unlocked
- F14-18 10 POOLED: conditional, unlocked
- F14-18+base 10 POOLED: conditional, unlocked
- F1-4 10 ASIA: conditional, unlocked
- F1-4+base 10 ASIA: conditional, unlocked
- F5-8 10 ASIA: conditional, unlocked
- F5-8+base 10 ASIA: conditional, unlocked
- F9-13 10 ASIA: conditional, unlocked
- F9-13+base 10 ASIA: conditional, unlocked
- F14-18 10 ASIA: conditional, unlocked
- F14-18+base 10 ASIA: conditional, unlocked
- F1-4 10 LONDON: conditional, unlocked
- F1-4+base 10 LONDON: conditional, unlocked
- F5-8 10 LONDON: conditional, unlocked
- F5-8+base 10 LONDON: conditional, unlocked
- F9-13 10 LONDON: conditional, unlocked
- F9-13+base 10 LONDON: conditional, unlocked
- F14-18 10 LONDON: conditional, unlocked
- F14-18+base 10 LONDON: conditional, unlocked
- F1-4 10 NY: conditional, unlocked
- F1-4+base 10 NY: conditional, unlocked
- F5-8 10 NY: conditional, unlocked
- F5-8+base 10 NY: conditional, unlocked
- F9-13 10 NY: conditional, unlocked
- F9-13+base 10 NY: conditional, unlocked
- F14-18 10 NY: conditional, unlocked
- F14-18+base 10 NY: conditional, unlocked
- F1-4 15 POOLED: conditional, unlocked
- F1-4+base 15 POOLED: conditional, unlocked
- F5-8 15 POOLED: conditional, unlocked
- F5-8+base 15 POOLED: conditional, unlocked
- F9-13 15 POOLED: conditional, unlocked
- F9-13+base 15 POOLED: conditional, unlocked
- F14-18 15 POOLED: conditional, unlocked
- F14-18+base 15 POOLED: conditional, unlocked
- F1-4 15 ASIA: conditional, unlocked
- F1-4+base 15 ASIA: conditional, unlocked
- F5-8 15 ASIA: conditional, unlocked
- F5-8+base 15 ASIA: conditional, unlocked
- F9-13 15 ASIA: conditional, unlocked
- F9-13+base 15 ASIA: conditional, unlocked
- F14-18 15 ASIA: conditional, unlocked
- F14-18+base 15 ASIA: conditional, unlocked
- F1-4 15 LONDON: conditional, unlocked
- F1-4+base 15 LONDON: conditional, unlocked
- F5-8 15 LONDON: conditional, unlocked
- F5-8+base 15 LONDON: conditional, unlocked
- F9-13 15 LONDON: conditional, unlocked
- F9-13+base 15 LONDON: conditional, unlocked
- F14-18 15 LONDON: conditional, unlocked
- F14-18+base 15 LONDON: conditional, unlocked
- F1-4 15 NY: conditional, unlocked
- F1-4+base 15 NY: conditional, unlocked
- F5-8 15 NY: conditional, unlocked
- F5-8+base 15 NY: conditional, unlocked
- F9-13 15 NY: conditional, unlocked
- F9-13+base 15 NY: conditional, unlocked
- F14-18 15 NY: conditional, unlocked
- F14-18+base 15 NY: conditional, unlocked
- F1-4 20 POOLED: conditional, unlocked
- F1-4+base 20 POOLED: conditional, unlocked
- F5-8 20 POOLED: conditional, unlocked
- F5-8+base 20 POOLED: conditional, unlocked
- F9-13 20 POOLED: conditional, unlocked
- F9-13+base 20 POOLED: conditional, unlocked
- F14-18 20 POOLED: conditional, unlocked
- F14-18+base 20 POOLED: conditional, unlocked
- F1-4 20 ASIA: conditional, unlocked
- F1-4+base 20 ASIA: conditional, unlocked
- F5-8 20 ASIA: conditional, unlocked
- F5-8+base 20 ASIA: conditional, unlocked
- F9-13 20 ASIA: conditional, unlocked
- F9-13+base 20 ASIA: conditional, unlocked
- F14-18 20 ASIA: conditional, unlocked
- F14-18+base 20 ASIA: conditional, unlocked
- F1-4 20 LONDON: conditional, unlocked
- F1-4+base 20 LONDON: conditional, unlocked
- F5-8 20 LONDON: conditional, unlocked
- F5-8+base 20 LONDON: conditional, unlocked
- F9-13 20 LONDON: conditional, unlocked
- F9-13+base 20 LONDON: conditional, unlocked
- F14-18 20 LONDON: conditional, unlocked
- F14-18+base 20 LONDON: conditional, unlocked
- F1-4 20 NY: conditional, unlocked
- F1-4+base 20 NY: conditional, unlocked
- F5-8 20 NY: conditional, unlocked
- F5-8+base 20 NY: conditional, unlocked
- F9-13 20 NY: conditional, unlocked
- F9-13+base 20 NY: conditional, unlocked
- F14-18 20 NY: conditional, unlocked
- F14-18+base 20 NY: conditional, unlocked
- F1-4 30 POOLED: conditional, unlocked
- F1-4+base 30 POOLED: conditional, unlocked
- F5-8 30 POOLED: conditional, unlocked
- F5-8+base 30 POOLED: conditional, unlocked
- F9-13 30 POOLED: conditional, unlocked
- F9-13+base 30 POOLED: conditional, unlocked
- F14-18 30 POOLED: conditional, unlocked
- F14-18+base 30 POOLED: conditional, unlocked
- F1-4 30 ASIA: conditional, unlocked
- F1-4+base 30 ASIA: conditional, unlocked
- F5-8 30 ASIA: conditional, unlocked
- F5-8+base 30 ASIA: conditional, unlocked
- F9-13 30 ASIA: conditional, unlocked
- F9-13+base 30 ASIA: conditional, unlocked
- F14-18 30 ASIA: conditional, unlocked
- F14-18+base 30 ASIA: conditional, unlocked
- F1-4 30 LONDON: conditional, unlocked
- F1-4+base 30 LONDON: conditional, unlocked
- F5-8 30 LONDON: conditional, unlocked
- F5-8+base 30 LONDON: conditional, unlocked
- F9-13 30 LONDON: conditional, unlocked
- F9-13+base 30 LONDON: conditional, unlocked
- F14-18 30 LONDON: conditional, unlocked
- F14-18+base 30 LONDON: conditional, unlocked
- F1-4 30 NY: conditional, unlocked
- F1-4+base 30 NY: conditional, unlocked
- F5-8 30 NY: conditional, unlocked
- F5-8+base 30 NY: conditional, unlocked
- F9-13 30 NY: conditional, unlocked
- F9-13+base 30 NY: conditional, unlocked
- F14-18 30 NY: conditional, unlocked
- F14-18+base 30 NY: conditional, unlocked
- F1-4 45 POOLED: conditional, unlocked
- F1-4+base 45 POOLED: conditional, unlocked
- F5-8 45 POOLED: conditional, unlocked
- F5-8+base 45 POOLED: conditional, unlocked
- F9-13 45 POOLED: conditional, unlocked
- F9-13+base 45 POOLED: conditional, unlocked
- F14-18 45 POOLED: conditional, unlocked
- F14-18+base 45 POOLED: conditional, unlocked
- F1-4 45 ASIA: conditional, unlocked
- F1-4+base 45 ASIA: conditional, unlocked
- F5-8 45 ASIA: conditional, unlocked
- F5-8+base 45 ASIA: conditional, unlocked
- F9-13 45 ASIA: conditional, unlocked
- F9-13+base 45 ASIA: conditional, unlocked
- F14-18 45 ASIA: conditional, unlocked
- F14-18+base 45 ASIA: conditional, unlocked
- F1-4 45 LONDON: conditional, unlocked
- F1-4+base 45 LONDON: conditional, unlocked
- F5-8 45 LONDON: conditional, unlocked
- F5-8+base 45 LONDON: conditional, unlocked
- F9-13 45 LONDON: conditional, unlocked
- F9-13+base 45 LONDON: conditional, unlocked
- F14-18 45 LONDON: conditional, unlocked
- F14-18+base 45 LONDON: conditional, unlocked
- F1-4 45 NY: conditional, unlocked
- F1-4+base 45 NY: conditional, unlocked
- F5-8 45 NY: conditional, unlocked
- F5-8+base 45 NY: conditional, unlocked
- F9-13 45 NY: conditional, unlocked
- F9-13+base 45 NY: conditional, unlocked
- F14-18 45 NY: conditional, unlocked
- F14-18+base 45 NY: conditional, unlocked
- F1-4 60 POOLED: conditional, unlocked
- F1-4+base 60 POOLED: conditional, unlocked
- F5-8 60 POOLED: conditional, unlocked
- F5-8+base 60 POOLED: conditional, unlocked
- F9-13 60 POOLED: conditional, unlocked
- F9-13+base 60 POOLED: conditional, unlocked
- F14-18 60 POOLED: conditional, unlocked
- F14-18+base 60 POOLED: conditional, unlocked
- F1-4 60 ASIA: conditional, unlocked
- F1-4+base 60 ASIA: conditional, unlocked
- F5-8 60 ASIA: conditional, unlocked
- F5-8+base 60 ASIA: conditional, unlocked
- F9-13 60 ASIA: conditional, unlocked
- F9-13+base 60 ASIA: conditional, unlocked
- F14-18 60 ASIA: conditional, unlocked
- F14-18+base 60 ASIA: conditional, unlocked
- F1-4 60 LONDON: conditional, unlocked
- F1-4+base 60 LONDON: conditional, unlocked
- F5-8 60 LONDON: conditional, unlocked
- F5-8+base 60 LONDON: conditional, unlocked
- F9-13 60 LONDON: conditional, unlocked
- F9-13+base 60 LONDON: conditional, unlocked
- F14-18 60 LONDON: conditional, unlocked
- F14-18+base 60 LONDON: conditional, unlocked
- F1-4 60 NY: conditional, unlocked
- F1-4+base 60 NY: conditional, unlocked
- F5-8 60 NY: conditional, unlocked
- F5-8+base 60 NY: conditional, unlocked
- F9-13 60 NY: conditional, unlocked
- F9-13+base 60 NY: conditional, unlocked
- F14-18 60 NY: conditional, unlocked
- F14-18+base 60 NY: conditional, unlocked
