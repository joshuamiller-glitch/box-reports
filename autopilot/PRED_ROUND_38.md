# PRED ROUND 38 - block X5 round 3 - X26-time-minimal+X27-signal-flow+X28-ev-regression+X29-recency+X30-per-cell-models

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.632 [0.57,0.69]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg d7fdbf471ea7a215c488a8d9815b74a03612dafed913c9ccec7d5975767c527f ; trials added 300 ; truncation audit {'decisions': 150, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'X27 flow features audited (audit/X5_flow_trunc.json); others use R0 matrix'} ; holdout scored True ; feature store ['l2vast/pred/store/X22_geo_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X27-signal-flow | sig | NY/ST | X27BR:stack | 0.608 [0.56,0.65] | 0.632 [0.57,0.69] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | LONDON/ST | X27BR:stack | 0.633 [0.59,0.67] | 0.625 [0.55,0.69] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | NY | X27BR:stack | 0.611 [0.58,0.65] | 0.620 [0.57,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | POOLED/ST | X27BR:stack | 0.601 [0.58,0.62] | 0.616 [0.59,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | LONDON/ST | X29UR:lgb | 0.595 [0.56,0.64] | 0.614 [0.55,0.68] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | NY/ST | X29UR:lgb | 0.616 [0.57,0.66] | 0.610 [0.55,0.67] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | ASIA/HM | X27BR:stack | 0.585 [0.55,0.62] | 0.610 [0.57,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | NY/HM | X29UR:lgb | 0.606 [0.55,0.66] | 0.610 [0.53,0.69] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | NY | X29UR:lgb | 0.610 [0.57,0.65] | 0.609 [0.56,0.67] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | POOLED | X27BR:stack | 0.595 [0.58,0.61] | 0.608 [0.59,0.63] | - | - | - | ok | -1805 | -31256 | - | 1/5 | stack | locked label (reference only) |
| X27-signal-flow | sig | ASIA | X27BR:stack | 0.577 [0.55,0.60] | 0.606 [0.58,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | LONDON | X27BR:stack | 0.611 [0.58,0.64] | 0.604 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | ASIA/ST | X27BR:stack | 0.571 [0.54,0.60] | 0.603 [0.57,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | POOLED/HM | X27BR:stack | 0.589 [0.57,0.61] | 0.602 [0.57,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | NY/HM | X27BR:stack | 0.608 [0.56,0.66] | 0.601 [0.53,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | LONDON | X29UR:lgb | 0.583 [0.55,0.61] | 0.595 [0.55,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | ASIA/ST | X30R:stack | 0.557 [0.52,0.59] | 0.591 [0.55,0.63] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | LONDON/HM | X27BR:stack | 0.589 [0.55,0.63] | 0.587 [0.53,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | POOLED/HM | X29UR:lgb | 0.567 [0.54,0.59] | 0.582 [0.55,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | POOLED | X29UR:lgb | 0.567 [0.55,0.58] | 0.580 [0.55,0.61] | - | - | - | - | 496 | -31256 | - | 2/5 | stack | locked label (reference only) |
| X29-recency | sig | POOLED/ST | X29UR:lgb | 0.568 [0.55,0.59] | 0.579 [0.55,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | NY/ST | X30R:stack | 0.570 [0.52,0.62] | 0.577 [0.52,0.63] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | LONDON/HM | X29UR:lgb | 0.570 [0.53,0.61] | 0.577 [0.52,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | POOLED/ST | X30R:stack | 0.567 [0.54,0.59] | 0.576 [0.55,0.61] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | ASIA/HM | X29UR:lgb | 0.549 [0.51,0.58] | 0.574 [0.53,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | NY | X30R:stack | 0.579 [0.55,0.61] | 0.571 [0.53,0.62] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | ASIA | X30R:stack | 0.544 [0.52,0.57] | 0.569 [0.54,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-ev-regression | sig | NY | X28:lgb | 0.548 [0.51,0.59] | 0.566 [0.50,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | NY/HM | X28:lgb | 0.564 [0.51,0.62] | 0.566 [0.48,0.66] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | NY/ST | X28:lgb | 0.534 [0.49,0.58] | 0.566 [0.51,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X30-per-cell-models | sig | LONDON/ST | X30R:stack | 0.582 [0.53,0.63] | 0.563 [0.49,0.64] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | NY/HM | X30R:stack | 0.587 [0.54,0.63] | 0.562 [0.49,0.64] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-ev-regression | sig | NY/HM | X28:lgb | 0.565 [0.50,0.63] | 0.560 [0.47,0.66] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X30-per-cell-models | sig | POOLED | X30R:stack | 0.556 [0.54,0.57] | 0.560 [0.54,0.58] | - | - | - | N | 259 | -31256 | - | 2/5 | stack | locked label (reference only) |
| X29-recency | sig | ASIA | X29UR:lgb | 0.534 [0.51,0.56] | 0.557 [0.52,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | LONDON | X30R:stack | 0.560 [0.53,0.59] | 0.549 [0.50,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-ev-regression | sig | NY | X28:lgb | 0.538 [0.50,0.58] | 0.548 [0.48,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X29-recency | sig | ASIA/ST | X29UR:lgb | 0.521 [0.49,0.55] | 0.543 [0.51,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | LONDON/HM | X30R:stack | 0.538 [0.49,0.58] | 0.542 [0.49,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | POOLED/HM | X30R:stack | 0.543 [0.52,0.56] | 0.542 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | LONDON/ST | X30T:stack | 0.503 [0.46,0.55] | 0.540 [0.48,0.61] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-time-minimal | sig | NY/ST | X26R:stack | 0.520 [0.48,0.57] | 0.538 [0.47,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X30-per-cell-models | sig | ASIA/HM | X30R:stack | 0.527 [0.49,0.56] | 0.536 [0.49,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | NY/HM | X29UT:lgb | 0.549 [0.49,0.61] | 0.535 [0.45,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X28-ev-regression | sig | NY/ST | X28:lgb | 0.513 [0.47,0.56] | 0.535 [0.47,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | ASIA/ST | X26R:stack | 0.508 [0.47,0.54] | 0.532 [0.48,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | LONDON/ST | X28:lgb | 0.500 [0.46,0.54] | 0.531 [0.48,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X27-signal-flow | sig | LONDON/ST | X27BT:stack | 0.487 [0.44,0.53] | 0.531 [0.47,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | NY | X29UT:lgb | 0.523 [0.48,0.56] | 0.531 [0.47,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | LONDON/ST | X29UT:lgb | 0.521 [0.48,0.57] | 0.530 [0.47,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | NY/ST | X29UT:lgb | 0.503 [0.45,0.55] | 0.529 [0.47,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | LONDON | X27BT:stack | 0.485 [0.45,0.52] | 0.528 [0.48,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | LONDON/HM | X27BT:stack | 0.482 [0.44,0.52] | 0.526 [0.46,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-time-minimal | sig | POOLED/ST | X26R:stack | 0.504 [0.48,0.53] | 0.526 [0.50,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | NY/ST | X26T:stack | 0.488 [0.44,0.54] | 0.524 [0.46,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X30-per-cell-models | sig | NY/HM | X30T:stack | 0.509 [0.45,0.57] | 0.521 [0.44,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | NY | X30T:stack | 0.498 [0.46,0.53] | 0.517 [0.46,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-ev-regression | sig | LONDON/ST | X28:lgb | 0.492 [0.45,0.54] | 0.515 [0.45,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | NY | X26R:stack | 0.515 [0.48,0.55] | 0.512 [0.45,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X27-signal-flow | sig | POOLED/ST | X27BT:stack | 0.485 [0.46,0.51] | 0.510 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-time-minimal | sig | NY | X26T:stack | 0.469 [0.43,0.51] | 0.508 [0.45,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | LONDON | X28:lgb | 0.490 [0.46,0.52] | 0.508 [0.47,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X27-signal-flow | sig | POOLED | X27BT:stack | 0.493 [0.47,0.51] | 0.508 [0.47,0.54] | - | - | - | N | 906 | -2 | - | 2/5 | stack | locked label (reference only) |
| X26-time-minimal | sig | ASIA | X26R:stack | 0.486 [0.45,0.52] | 0.508 [0.46,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | LONDON/HM | X26R:stack | 0.480 [0.43,0.53] | 0.507 [0.44,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | POOLED | X26R:stack | 0.491 [0.47,0.51] | 0.507 [0.48,0.54] | - | - | - | N | -308 | -331 | - | 1/5 |  | locked label (reference only) |
| X26-time-minimal | sig | LONDON | X26R:stack | 0.478 [0.44,0.52] | 0.507 [0.46,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | LONDON/ST | X26R:stack | 0.476 [0.43,0.52] | 0.506 [0.45,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X27-signal-flow | sig | POOLED/HM | X27BT:stack | 0.501 [0.47,0.53] | 0.505 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | POOLED/ST | X29UT:lgb | 0.496 [0.47,0.52] | 0.504 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | NY/HM | X27BT:stack | 0.518 [0.47,0.57] | 0.502 [0.43,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | NY | X27BT:stack | 0.506 [0.47,0.54] | 0.502 [0.44,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | ASIA/ST | X27BT:stack | 0.478 [0.44,0.51] | 0.500 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | NY/ST | X27BT:stack | 0.496 [0.45,0.55] | 0.500 [0.43,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | LONDON | X29UT:lgb | 0.504 [0.47,0.54] | 0.500 [0.45,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | POOLED | X29UT:lgb | 0.499 [0.48,0.52] | 0.499 [0.47,0.53] | - | - | - | - | -505 | -3590 | - | 1/5 | stack | locked label (reference only) |
| X30-per-cell-models | sig | LONDON | X30T:stack | 0.493 [0.46,0.52] | 0.498 [0.45,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-signal-flow | sig | ASIA | X27BT:stack | 0.491 [0.46,0.52] | 0.498 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-ev-regression | sig | POOLED/ST | X28:lgb | 0.485 [0.46,0.51] | 0.496 [0.47,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | LONDON/ST | X26T:stack | 0.457 [0.41,0.50] | 0.496 [0.43,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | POOLED | X28:lgb | 0.490 [0.47,0.51] | 0.496 [0.47,0.53] | - | - | - | - | 2011 | -20004 | - | 3/5 |  | locked label (reference only) |
| X28-ev-regression | sig | POOLED/HM | X28:lgb | 0.498 [0.47,0.52] | 0.495 [0.46,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | POOLED/ST | X26T:stack | 0.485 [0.46,0.51] | 0.495 [0.47,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | POOLED/HM | X28:lgb | 0.496 [0.47,0.52] | 0.495 [0.45,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X27-signal-flow | sig | ASIA/HM | X27BT:stack | 0.507 [0.47,0.55] | 0.495 [0.44,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | POOLED/ST | X30T:stack | 0.488 [0.46,0.52] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-ev-regression | sig | LONDON | X28:lgb | 0.483 [0.45,0.52] | 0.494 [0.45,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X29-recency | sig | POOLED/HM | X29UT:lgb | 0.502 [0.47,0.53] | 0.493 [0.45,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X28-ev-regression | sig | POOLED | X28:lgb | 0.489 [0.47,0.51] | 0.492 [0.46,0.52] | - | - | - | - | 2011 | -20004 | - | 3/5 |  | locked label (reference only) |
| X29-recency | sig | ASIA/HM | X29UT:lgb | 0.490 [0.46,0.52] | 0.490 [0.44,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | POOLED | X30T:stack | 0.490 [0.47,0.51] | 0.490 [0.47,0.51] | - | - | - | N | 1419 | -31256 | - | 2/5 | stack | locked label (reference only) |
| X28-ev-regression | sig | LONDON/HM | X28:lgb | 0.480 [0.44,0.52] | 0.489 [0.43,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | POOLED/ST | X28:lgb | 0.480 [0.46,0.50] | 0.488 [0.46,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X30-per-cell-models | sig | POOLED/HM | X30T:stack | 0.490 [0.46,0.51] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-time-minimal | sig | LONDON | X26T:stack | 0.464 [0.43,0.50] | 0.488 [0.43,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | POOLED | X26T:stack | 0.487 [0.47,0.51] | 0.487 [0.46,0.52] | - | - | - | N | 438 | 111230 | - | 1/5 |  | locked label (reference only) |
| X26-time-minimal | sig | NY/HM | X26T:stack | 0.447 [0.39,0.51] | 0.486 [0.41,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | POOLED/HM | X26R:stack | 0.477 [0.45,0.50] | 0.486 [0.45,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X29-recency | sig | ASIA | X29UT:lgb | 0.484 [0.46,0.51] | 0.486 [0.45,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X26-time-minimal | sig | ASIA/ST | X26T:stack | 0.501 [0.47,0.54] | 0.484 [0.44,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | NY/HM | X26R:stack | 0.510 [0.46,0.55] | 0.482 [0.41,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X29-recency | sig | ASIA/ST | X29UT:lgb | 0.480 [0.44,0.51] | 0.482 [0.44,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | NY/ST | X30T:stack | 0.464 [0.41,0.52] | 0.481 [0.41,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-time-minimal | sig | ASIA | X26T:stack | 0.510 [0.48,0.54] | 0.480 [0.44,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | ASIA/HM | X26R:stack | 0.462 [0.42,0.50] | 0.478 [0.43,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | LONDON/HM | X26T:stack | 0.471 [0.42,0.52] | 0.477 [0.41,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | POOLED/HM | X26T:stack | 0.488 [0.46,0.51] | 0.477 [0.44,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | LONDON/HM | X28:lgb | 0.473 [0.43,0.52] | 0.476 [0.42,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | ASIA/HM | X28:lgb | 0.479 [0.44,0.52] | 0.476 [0.42,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X26-time-minimal | sig | ASIA/HM | X26T:stack | 0.518 [0.48,0.56] | 0.474 [0.42,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X30-per-cell-models | sig | ASIA/ST | X30T:stack | 0.482 [0.45,0.52] | 0.473 [0.43,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-recency | sig | LONDON/HM | X29UT:lgb | 0.487 [0.44,0.53] | 0.472 [0.41,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | ASIA | X30T:stack | 0.478 [0.45,0.50] | 0.471 [0.44,0.50] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | LONDON/HM | X30T:stack | 0.483 [0.44,0.53] | 0.469 [0.41,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-per-cell-models | sig | ASIA/HM | X30T:stack | 0.473 [0.44,0.51] | 0.466 [0.42,0.51] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-ev-regression | sig | ASIA/HM | X28:lgb | 0.471 [0.43,0.51] | 0.466 [0.41,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | ASIA | X28:lgb | 0.468 [0.44,0.50] | 0.465 [0.42,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | ASIA | X28:lgb | 0.462 [0.43,0.49] | 0.458 [0.42,0.50] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | ASIA/ST | X28:lgb | 0.459 [0.42,0.49] | 0.455 [0.41,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| X28-ev-regression | sig | ASIA/ST | X28:lgb | 0.453 [0.42,0.49] | 0.449 [0.40,0.50] | - | - | - | - | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- X26-time-minimal -1 POOLED: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 ASIA: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 LONDON: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 NY: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 POOLED: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 ASIA: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 LONDON: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 NY: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 POOLED: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 ASIA: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 LONDON: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 NY: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 POOLED: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 ASIA: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 LONDON: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 NY: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 POOLED: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 ASIA: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 LONDON: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 NY: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 POOLED: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 ASIA: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 LONDON: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X26-time-minimal -1 NY: book/side/session/minute only; holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 POOLED: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 ASIA: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 LONDON: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 NY: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 POOLED: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 ASIA: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 LONDON: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 NY: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 POOLED: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 ASIA: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 LONDON: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 NY: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 POOLED: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 ASIA: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 LONDON: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 NY: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 POOLED: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 ASIA: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 LONDON: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 NY: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 POOLED: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 ASIA: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 LONDON: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X28-ev-regression -1 NY: EV regression mapped to P(pts<0); holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 POOLED: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 ASIA: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 LONDON: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 NY: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 POOLED: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 ASIA: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 LONDON: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 NY: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 POOLED: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 ASIA: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 LONDON: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 NY: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 POOLED: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 ASIA: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 LONDON: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 NY: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 POOLED: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 ASIA: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 LONDON: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 NY: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 POOLED: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 ASIA: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 LONDON: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X27-signal-flow -1 NY: flow state + R0 matrix; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 POOLED: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 ASIA: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 LONDON: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 NY: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 POOLED: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 ASIA: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 LONDON: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 NY: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 POOLED: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 ASIA: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 LONDON: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 NY: unweighted lgb (recency-weighted lost WF-PRE); holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 POOLED: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 ASIA: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 LONDON: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 NY: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 POOLED: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 ASIA: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 LONDON: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 NY: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 POOLED: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 ASIA: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 LONDON: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X29-recency -1 NY: unweighted lgb; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 POOLED: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 ASIA: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 LONDON: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 NY: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 POOLED: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 ASIA: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 LONDON: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 NY: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 POOLED: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 ASIA: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 LONDON: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 NY: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 POOLED: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 ASIA: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 LONDON: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 NY: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 POOLED: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 ASIA: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 LONDON: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 NY: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 POOLED: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 ASIA: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 LONDON: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
- X30-per-cell-models -1 NY: per session x book models; holdout AUC far below FOUND, no gain over R0; dead
