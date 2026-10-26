# PRED ROUND 39 - block X2 round 2 - X7-X8-X9

Best HOLDOUT F-R AUC: +15 POOLED 0.584 [0.54,0.63] | ASIA 0.553 [0.49,0.61] | LONDON 0.571 [0.49,0.65] | NY 0.553 [0.45,0.65]
Best HOLDOUT F-R AUC: +30 POOLED 0.583 [0.54,0.63] | ASIA 0.553 [0.50,0.61] | LONDON 0.561 [0.48,0.64] | NY 0.550 [0.43,0.67]
Best G HOLDOUT AUC: 0.649 [0.61,0.69]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 3db67f251c99197489bc61ad04b1c033979e1907fa63ad5c24d64dd910a0b8ab ; trials added 2400 ; truncation audit {'decisions': 2160, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X2_X7.parquet', 'l2vast/pred/store/X2_X8.parquet', 'l2vast/pred/store/X2_X9.parquet', 'l2vast/pred/store/X2_X7_sig.parquet', 'l2vast/pred/store/X2_X8_sig.parquet', 'l2vast/pred/store/X2_X9_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| combo-X789-G | sig | ASIA/HM | gbt3 | 0.613 [0.58,0.65] | 0.649 [0.61,0.69] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | ASIA | gbt3 | 0.596 [0.57,0.62] | 0.632 [0.60,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | NY/ST | rf | 0.618 [0.57,0.66] | 0.631 [0.56,0.69] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | ASIA/HM | rf | 0.599 [0.57,0.63] | 0.631 [0.59,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | ASIA/HM | gbt3 | 0.587 [0.56,0.62] | 0.623 [0.58,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | NY | rf | 0.620 [0.58,0.66] | 0.622 [0.57,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | ASIA/ST | gbt3 | 0.583 [0.55,0.61] | 0.620 [0.58,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | ASIA/HM | rf | 0.594 [0.56,0.62] | 0.618 [0.58,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +10 | LONDON | gbt3 | 0.531 [0.46,0.59] | 0.618 [0.53,0.70] | - | 0.613 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | ASIA | rf | 0.584 [0.56,0.61] | 0.617 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | NY | rf | 0.620 [0.58,0.66] | 0.617 [0.57,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | POOLED/HM | rf | 0.606 [0.59,0.62] | 0.616 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +60 | LONDON | gbt3 | 0.555 [0.50,0.61] | 0.616 [0.54,0.69] | - | 0.616 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | POOLED/HM | rf | 0.603 [0.58,0.62] | 0.615 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +60 | LONDON | gbt3 | 0.566 [0.52,0.62] | 0.615 [0.53,0.69] | - | 0.617 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | POOLED/HM | rf | 0.599 [0.58,0.62] | 0.615 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | NY/ST | stack | 0.615 [0.57,0.66] | 0.615 [0.55,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | POOLED/ST | rf | 0.603 [0.58,0.63] | 0.614 [0.58,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | POOLED | rf | 0.603 [0.59,0.62] | 0.614 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | POOLED | rf | 0.600 [0.58,0.62] | 0.613 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | POOLED | rf | 0.604 [0.59,0.62] | 0.613 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | NY | rf | 0.612 [0.58,0.65] | 0.613 [0.57,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | NY/HM | rf | 0.624 [0.58,0.67] | 0.613 [0.54,0.70] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | NY/ST | logit2 | 0.604 [0.56,0.65] | 0.613 [0.55,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | LONDON/ST | logit2 | 0.640 [0.60,0.68] | 0.612 [0.54,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | ASIA | gbt3 | 0.578 [0.55,0.60] | 0.612 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | NY/ST | logit2 | 0.599 [0.56,0.64] | 0.611 [0.55,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | POOLED | rf | 0.600 [0.58,0.62] | 0.610 [0.59,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | NY/HM | rf | 0.618 [0.57,0.67] | 0.609 [0.54,0.69] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | POOLED/HM | rf | 0.600 [0.58,0.62] | 0.609 [0.58,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | LONDON/ST | logit2 | 0.642 [0.60,0.69] | 0.609 [0.54,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | LONDON/ST | logit2 | 0.642 [0.60,0.69] | 0.608 [0.54,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +20 | LONDON | logit2 | 0.556 [0.50,0.61] | 0.607 [0.53,0.69] | - | 0.564 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | ASIA/ST | rf | 0.572 [0.54,0.60] | 0.606 [0.57,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | ASIA | stack | 0.577 [0.55,0.60] | 0.606 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | LONDON/ST | logit2 | 0.641 [0.60,0.68] | 0.606 [0.53,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | NY/HM | rf | 0.618 [0.58,0.66] | 0.605 [0.54,0.69] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | LONDON | logit2 | 0.625 [0.59,0.66] | 0.604 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | ASIA/ST | gbt3 | 0.571 [0.54,0.60] | 0.604 [0.57,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | LONDON | logit2 | 0.628 [0.60,0.66] | 0.603 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | LONDON | logit2 | 0.628 [0.60,0.66] | 0.602 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | LONDON/HM | logit2 | 0.613 [0.57,0.65] | 0.600 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | LONDON/HM | logit2 | 0.614 [0.57,0.65] | 0.600 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | NY | logit2 | 0.603 [0.57,0.64] | 0.600 [0.56,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | LONDON | logit2 | 0.624 [0.59,0.66] | 0.599 [0.55,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | POOLED/ST | logit2 | 0.594 [0.57,0.61] | 0.599 [0.57,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | LONDON/HM | logit2 | 0.610 [0.57,0.65] | 0.598 [0.54,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | POOLED/ST | logit2 | 0.597 [0.58,0.62] | 0.598 [0.57,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | POOLED/ST | logit2 | 0.595 [0.57,0.62] | 0.598 [0.57,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +20 | LONDON | gbt3 | 0.544 [0.49,0.59] | 0.594 [0.52,0.67] | - | 0.593 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | LONDON/HM | logit2 | 0.607 [0.57,0.64] | 0.593 [0.54,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +20 | LONDON | logit2 | 0.556 [0.51,0.61] | 0.592 [0.52,0.67] | - | 0.556 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +45 | LONDON | rf | 0.534 [0.48,0.59] | 0.590 [0.53,0.66] | - | 0.571 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +20 | POOLED | logit2 | 0.548 [0.52,0.58] | 0.589 [0.55,0.63] | - | 0.564 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +60 | LONDON | gbt3 | 0.544 [0.48,0.61] | 0.589 [0.51,0.66] | - | 0.578 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +20 | POOLED | logit2 | 0.552 [0.52,0.58] | 0.588 [0.55,0.63] | - | 0.563 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | ASIA/ST | logit2 | 0.560 [0.53,0.59] | 0.587 [0.56,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +10 | POOLED | rf | 0.556 [0.53,0.59] | 0.586 [0.54,0.63] | - | 0.552 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | NY/HM | logit2 | 0.605 [0.55,0.65] | 0.584 [0.51,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +15 | POOLED | logit2 | 0.549 [0.52,0.58] | 0.584 [0.54,0.63] | - | 0.562 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +30 | POOLED | logit2 | 0.536 [0.50,0.57] | 0.583 [0.54,0.63] | - | 0.566 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +15 | POOLED | logit2 | 0.544 [0.52,0.57] | 0.583 [0.54,0.62] | - | 0.560 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +20 | POOLED | logit2 | 0.554 [0.52,0.59] | 0.582 [0.53,0.63] | - | 0.563 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +10 | POOLED | rf | 0.550 [0.52,0.58] | 0.580 [0.54,0.63] | - | 0.552 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +20 | POOLED | logit2 | 0.548 [0.52,0.58] | 0.580 [0.53,0.63] | - | 0.561 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +10 | POOLED | rf | 0.549 [0.52,0.58] | 0.580 [0.53,0.63] | - | 0.554 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +60 | LONDON | gbt3 | 0.546 [0.49,0.60] | 0.580 [0.50,0.65] | - | 0.581 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +15 | POOLED | stack | 0.573 [0.54,0.60] | 0.580 [0.53,0.62] | - | 0.563 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +10 | POOLED | rf | 0.552 [0.52,0.58] | 0.580 [0.54,0.62] | - | 0.552 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +45 | POOLED | rf | 0.554 [0.53,0.58] | 0.579 [0.54,0.62] | - | 0.559 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +60 | NY | gbt3 | 0.547 [0.48,0.62] | 0.577 [0.47,0.68] | - | 0.564 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +20 | LONDON | logit2 | 0.540 [0.49,0.59] | 0.576 [0.50,0.65] | - | 0.545 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +45 | LONDON | stack | 0.539 [0.48,0.60] | 0.575 [0.49,0.66] | - | 0.568 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +15 | POOLED | gbt3 | 0.567 [0.54,0.60] | 0.575 [0.54,0.61] | - | 0.553 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | pre | POOLED | gbt3 | 0.549 [0.52,0.58] | 0.574 [0.53,0.61] | - | 0.543 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +20 | NY | rf | 0.546 [0.48,0.61] | 0.573 [0.47,0.68] | - | 0.564 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +15 | LONDON | stack | 0.566 [0.52,0.62] | 0.571 [0.49,0.65] | - | 0.541 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +45 | ASIA | rf | 0.568 [0.53,0.61] | 0.570 [0.52,0.62] | - | 0.548 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +45 | LONDON | stack | 0.544 [0.49,0.60] | 0.570 [0.49,0.65] | - | 0.551 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +5 | POOLED | rf | 0.543 [0.51,0.57] | 0.569 [0.53,0.61] | - | 0.546 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +45 | NY | rf | 0.541 [0.48,0.61] | 0.569 [0.47,0.66] | - | 0.574 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | pre | POOLED | rf | 0.542 [0.51,0.57] | 0.568 [0.52,0.62] | - | 0.548 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +5 | LONDON | stack | 0.554 [0.50,0.60] | 0.568 [0.49,0.65] | - | 0.537 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +45 | POOLED | rf | 0.560 [0.53,0.59] | 0.568 [0.53,0.61] | - | 0.543 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +60 | LONDON | gbt3 | 0.545 [0.49,0.60] | 0.567 [0.50,0.63] | - | 0.572 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +60 | POOLED | gbt3 | 0.548 [0.52,0.58] | 0.567 [0.53,0.61] | - | 0.550 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +45 | POOLED | rf | 0.550 [0.52,0.58] | 0.566 [0.53,0.61] | - | 0.542 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +20 | LONDON | logit2 | 0.543 [0.49,0.60] | 0.564 [0.49,0.64] | - | 0.568 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +45 | POOLED | rf | 0.551 [0.52,0.58] | 0.564 [0.52,0.61] | - | 0.542 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +5 | ASIA | rf | 0.534 [0.49,0.58] | 0.564 [0.51,0.62] | - | 0.555 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +45 | POOLED | rf | 0.555 [0.53,0.58] | 0.564 [0.53,0.60] | - | 0.539 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +15 | LONDON | gbt3 | 0.531 [0.48,0.58] | 0.563 [0.49,0.63] | - | 0.579 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +5 | POOLED | rf | 0.540 [0.51,0.57] | 0.562 [0.52,0.61] | - | 0.537 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +30 | LONDON | logit2 | 0.530 [0.47,0.59] | 0.561 [0.48,0.64] | - | 0.549 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +20 | POOLED | logit2 | 0.553 [0.52,0.58] | 0.560 [0.51,0.60] | - | 0.548 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +30 | POOLED | logit2 | 0.543 [0.51,0.58] | 0.560 [0.51,0.61] | - | 0.551 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +30 | POOLED | rf | 0.556 [0.53,0.58] | 0.558 [0.52,0.60] | - | 0.532 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +20 | POOLED | logit2 | 0.562 [0.53,0.59] | 0.558 [0.52,0.60] | - | 0.535 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +20 | ASIA | stack | 0.537 [0.50,0.58] | 0.557 [0.50,0.62] | - | 0.539 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +45 | POOLED | rf | 0.558 [0.53,0.59] | 0.557 [0.51,0.60] | - | 0.535 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +10 | POOLED | logit2 | 0.550 [0.52,0.58] | 0.556 [0.52,0.59] | - | 0.531 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +15 | POOLED | stack | 0.558 [0.53,0.58] | 0.556 [0.52,0.59] | - | 0.529 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | pre | POOLED | rf | 0.544 [0.51,0.58] | 0.555 [0.51,0.60] | - | 0.529 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +10 | POOLED | rf | 0.563 [0.53,0.59] | 0.555 [0.52,0.59] | - | 0.528 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +45 | LONDON | gbt3 | 0.542 [0.49,0.59] | 0.555 [0.48,0.62] | - | 0.512 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | pre | LONDON | gbt3 | 0.537 [0.48,0.59] | 0.555 [0.47,0.63] | - | 0.543 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +60 | POOLED | logit2 | 0.535 [0.51,0.57] | 0.554 [0.51,0.60] | - | 0.543 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +45 | NY | rf | 0.521 [0.46,0.59] | 0.554 [0.46,0.64] | - | 0.544 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +10 | NY | rf | 0.579 [0.51,0.64] | 0.554 [0.45,0.64] | - | 0.564 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +30 | ASIA | rf | 0.571 [0.53,0.61] | 0.553 [0.50,0.61] | - | 0.532 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | +15 | ASIA | logit2 | 0.543 [0.50,0.58] | 0.553 [0.49,0.61] | - | 0.539 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +15 | NY | stack | 0.526 [0.46,0.59] | 0.553 [0.45,0.65] | - | 0.541 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +5 | NY | logit2 | 0.545 [0.48,0.61] | 0.552 [0.46,0.64] | - | 0.506 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | pre | ASIA | rf | 0.539 [0.49,0.58] | 0.552 [0.49,0.62] | - | 0.531 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +60 | POOLED | gbt3 | 0.539 [0.51,0.58] | 0.552 [0.51,0.60] | - | 0.541 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +15 | NY | stack | 0.532 [0.46,0.60] | 0.551 [0.44,0.65] | - | 0.548 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +15 | ASIA | stack | 0.544 [0.50,0.59] | 0.551 [0.49,0.61] | - | 0.546 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +30 | NY | logit2 | 0.521 [0.45,0.59] | 0.550 [0.43,0.67] | - | 0.562 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +20 | NY | rf | 0.532 [0.47,0.59] | 0.549 [0.44,0.65] | - | 0.565 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +30 | ASIA | logit2 | 0.533 [0.49,0.57] | 0.549 [0.49,0.61] | - | 0.539 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +20 | NY | gbt3 | 0.557 [0.49,0.62] | 0.549 [0.45,0.65] | - | 0.550 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | +30 | NY | logit2 | 0.525 [0.46,0.59] | 0.549 [0.43,0.67] | - | 0.559 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +45 | NY | logit2 | 0.526 [0.45,0.60] | 0.549 [0.46,0.63] | - | 0.562 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +15 | NY | gbt3 | 0.561 [0.50,0.63] | 0.548 [0.45,0.65] | - | 0.541 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +20 | NY | logit2 | 0.535 [0.47,0.59] | 0.548 [0.45,0.64] | - | 0.537 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +45 | ASIA | rf | 0.582 [0.54,0.63] | 0.548 [0.48,0.61] | - | 0.530 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +15 | NY | gbt3 | 0.517 [0.45,0.59] | 0.548 [0.45,0.65] | - | 0.515 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | pre | POOLED | logit2 | 0.544 [0.51,0.57] | 0.547 [0.51,0.59] | - | 0.524 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | LONDON/ST | logit2 | 0.535 [0.49,0.58] | 0.547 [0.48,0.62] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +45 | NY | rf | 0.544 [0.48,0.61] | 0.547 [0.47,0.63] | - | 0.540 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +60 | LONDON | logit2 | 0.500 [0.45,0.55] | 0.547 [0.48,0.62] | - | 0.536 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +15 | POOLED | stack | 0.544 [0.51,0.58] | 0.546 [0.50,0.59] | - | 0.517 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +10 | NY | logit2 | 0.547 [0.49,0.61] | 0.546 [0.45,0.63] | - | 0.526 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +5 | POOLED | stack | 0.531 [0.50,0.56] | 0.546 [0.50,0.59] | - | 0.526 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +5 | POOLED | rf | 0.550 [0.52,0.58] | 0.544 [0.51,0.58] | - | 0.527 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +15 | ASIA | logit2 | 0.538 [0.50,0.58] | 0.544 [0.49,0.61] | - | 0.524 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +60 | POOLED | logit2 | 0.530 [0.50,0.56] | 0.544 [0.50,0.59] | - | 0.530 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +45 | LONDON | stack | 0.517 [0.46,0.58] | 0.543 [0.46,0.62] | - | 0.514 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +30 | ASIA | logit2 | 0.543 [0.50,0.59] | 0.543 [0.48,0.61] | - | 0.518 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +15 | LONDON | stack | 0.554 [0.51,0.61] | 0.542 [0.46,0.62] | - | 0.520 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | pre | POOLED | rf | 0.547 [0.52,0.58] | 0.542 [0.50,0.59] | - | 0.513 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +45 | LONDON | stack | 0.564 [0.51,0.61] | 0.542 [0.47,0.61] | - | 0.528 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +15 | ASIA | rf | 0.556 [0.51,0.60] | 0.542 [0.48,0.60] | - | 0.531 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +5 | ASIA | rf | 0.521 [0.48,0.57] | 0.541 [0.48,0.60] | - | 0.538 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +10 | LONDON | stack | 0.532 [0.48,0.59] | 0.541 [0.46,0.62] | - | 0.527 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +30 | LONDON | logit2 | 0.530 [0.47,0.58] | 0.540 [0.47,0.61] | - | 0.529 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +15 | POOLED | stack | 0.531 [0.50,0.56] | 0.540 [0.50,0.58] | - | 0.516 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +5 | ASIA | rf | 0.540 [0.49,0.58] | 0.539 [0.49,0.60] | - | 0.526 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +15 | POOLED | rf | 0.543 [0.51,0.57] | 0.538 [0.50,0.58] | - | 0.516 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +20 | POOLED | rf | 0.549 [0.52,0.58] | 0.537 [0.49,0.58] | - | 0.525 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | +15 | NY | stack | 0.543 [0.47,0.61] | 0.537 [0.42,0.65] | - | 0.502 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +45 | ASIA | stack | 0.531 [0.49,0.57] | 0.537 [0.47,0.59] | - | 0.511 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +10 | NY | rf | 0.544 [0.48,0.61] | 0.536 [0.44,0.62] | - | 0.616 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +5 | ASIA | rf | 0.535 [0.49,0.58] | 0.535 [0.48,0.59] | - | 0.519 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +45 | POOLED | stack | 0.538 [0.51,0.57] | 0.534 [0.50,0.57] | - | 0.503 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | +60 | NY | rf | 0.544 [0.48,0.62] | 0.534 [0.44,0.62] | - | 0.556 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +30 | POOLED | stack | 0.538 [0.51,0.57] | 0.533 [0.49,0.58] | - | 0.497 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | LONDON | logit2 | 0.527 [0.49,0.56] | 0.533 [0.48,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | LONDON/ST | rf | 0.533 [0.48,0.58] | 0.533 [0.47,0.61] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +60 | POOLED | rf | 0.530 [0.50,0.56] | 0.532 [0.49,0.57] | - | 0.520 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +45 | ASIA | logit2 | 0.545 [0.50,0.59] | 0.532 [0.47,0.60] | - | 0.522 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +30 | LONDON | stack | 0.541 [0.49,0.59] | 0.532 [0.45,0.61] | - | 0.525 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +5 | LONDON | gbt3 | 0.531 [0.48,0.58] | 0.532 [0.44,0.62] | - | 0.521 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +60 | NY | rf | 0.544 [0.47,0.61] | 0.531 [0.44,0.61] | - | 0.545 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +30 | POOLED | stack | 0.558 [0.53,0.59] | 0.531 [0.48,0.58] | - | 0.516 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | +15 | LONDON | stack | 0.550 [0.50,0.60] | 0.531 [0.45,0.61] | - | 0.519 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +20 | LONDON | stack | 0.522 [0.47,0.57] | 0.531 [0.45,0.61] | - | 0.516 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +5 | LONDON | stack | 0.541 [0.49,0.59] | 0.531 [0.45,0.61] | - | 0.531 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +5 | POOLED | rf | 0.536 [0.51,0.56] | 0.530 [0.49,0.57] | - | 0.520 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +10 | NY | gbt3 | 0.501 [0.44,0.57] | 0.530 [0.44,0.62] | - | 0.581 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | LONDON | logit2 | 0.529 [0.49,0.56] | 0.529 [0.48,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +10 | POOLED | stack | 0.543 [0.51,0.57] | 0.529 [0.49,0.57] | - | 0.511 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +60 | POOLED | rf | 0.537 [0.51,0.57] | 0.529 [0.49,0.57] | - | 0.512 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +5 | POOLED | gbt3 | 0.541 [0.51,0.57] | 0.529 [0.49,0.57] | - | 0.503 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | pre | POOLED | rf | 0.538 [0.51,0.57] | 0.528 [0.48,0.57] | - | 0.503 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +15 | NY | logit2 | 0.500 [0.44,0.56] | 0.528 [0.44,0.62] | - | 0.499 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | pre | LONDON | gbt3 | 0.518 [0.46,0.58] | 0.528 [0.45,0.61] | - | 0.526 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +30 | POOLED | stack | 0.532 [0.50,0.56] | 0.528 [0.49,0.57] | - | 0.492 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +5 | POOLED | stack | 0.514 [0.48,0.54] | 0.528 [0.48,0.57] | - | 0.498 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +30 | ASIA | rf | 0.530 [0.49,0.57] | 0.527 [0.47,0.59] | - | 0.507 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +15 | LONDON | stack | 0.533 [0.49,0.58] | 0.527 [0.45,0.61] | - | 0.515 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | POOLED | rf | 0.514 [0.49,0.53] | 0.526 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +30 | ASIA | stack | 0.546 [0.51,0.58] | 0.526 [0.46,0.59] | - | 0.489 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +60 | ASIA | rf | 0.531 [0.49,0.57] | 0.526 [0.47,0.59] | - | 0.505 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +10 | ASIA | stack | 0.557 [0.52,0.60] | 0.525 [0.46,0.59] | - | 0.514 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | +10 | NY | stack | 0.530 [0.47,0.60] | 0.525 [0.43,0.63] | - | 0.599 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +20 | ASIA | stack | 0.524 [0.48,0.57] | 0.525 [0.47,0.59] | - | 0.499 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +10 | NY | stack | 0.523 [0.46,0.59] | 0.524 [0.42,0.63] | - | 0.559 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +30 | NY | logit2 | 0.517 [0.45,0.58] | 0.524 [0.42,0.62] | - | 0.535 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +60 | NY | rf | 0.537 [0.46,0.61] | 0.523 [0.41,0.63] | - | 0.548 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | pre | LONDON | gbt3 | 0.505 [0.44,0.56] | 0.523 [0.44,0.61] | - | 0.527 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +20 | ASIA | stack | 0.528 [0.49,0.57] | 0.523 [0.46,0.58] | - | 0.498 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | POOLED/HM | rf | 0.522 [0.50,0.54] | 0.522 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +30 | NY | logit2 | 0.517 [0.45,0.58] | 0.522 [0.42,0.62] | - | 0.530 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | POOLED | rf | 0.511 [0.49,0.53] | 0.521 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +15 | LONDON | stack | 0.529 [0.48,0.58] | 0.521 [0.44,0.60] | - | 0.500 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +10 | LONDON | stack | 0.535 [0.48,0.58] | 0.521 [0.45,0.59] | - | 0.496 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise-G | sig | POOLED/ST | logit2 | 0.504 [0.48,0.53] | 0.521 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +30 | ASIA | stack | 0.531 [0.49,0.57] | 0.520 [0.46,0.58] | - | 0.486 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | LONDON/HM | logit2 | 0.519 [0.48,0.56] | 0.520 [0.46,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +45 | ASIA | rf | 0.544 [0.50,0.59] | 0.519 [0.46,0.58] | - | 0.496 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +30 | ASIA | rf | 0.529 [0.48,0.57] | 0.519 [0.46,0.57] | - | 0.496 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | pre | NY | gbt3 | 0.532 [0.46,0.60] | 0.519 [0.42,0.62] | - | 0.524 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +20 | ASIA | rf | 0.551 [0.51,0.59] | 0.519 [0.46,0.57] | - | 0.510 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise-G | sig | LONDON/ST | rf | 0.527 [0.48,0.58] | 0.519 [0.44,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +10 | ASIA | rf | 0.563 [0.52,0.60] | 0.518 [0.46,0.57] | - | 0.486 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789-G | sig | POOLED/ST | logit2 | 0.504 [0.48,0.53] | 0.518 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +15 | LONDON | stack | 0.526 [0.47,0.58] | 0.518 [0.45,0.59] | - | 0.481 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise-G | sig | POOLED/HM | rf | 0.515 [0.49,0.54] | 0.518 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +20 | ASIA | rf | 0.553 [0.51,0.59] | 0.517 [0.46,0.58] | - | 0.498 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +10 | ASIA | rf | 0.533 [0.49,0.58] | 0.517 [0.46,0.58] | - | 0.492 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +45 | NY | rf | 0.515 [0.45,0.58] | 0.516 [0.41,0.62] | - | 0.513 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | POOLED/HM | rf | 0.517 [0.49,0.54] | 0.516 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +5 | NY | stack | 0.497 [0.42,0.56] | 0.516 [0.40,0.62] | - | 0.530 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +45 | ASIA | gbt3 | 0.554 [0.51,0.60] | 0.516 [0.45,0.58] | - | 0.504 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +60 | ASIA | logit2 | 0.533 [0.49,0.58] | 0.515 [0.45,0.58] | - | 0.497 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +20 | NY | logit2 | 0.536 [0.48,0.59] | 0.514 [0.40,0.61] | - | 0.516 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | pre | ASIA | logit2 | 0.538 [0.50,0.58] | 0.513 [0.46,0.57] | - | 0.505 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise-G | sig | LONDON/HM | logit2 | 0.517 [0.48,0.56] | 0.513 [0.46,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +5 | LONDON | stack | 0.536 [0.49,0.59] | 0.513 [0.44,0.59] | - | 0.508 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | NY | rf | 0.519 [0.48,0.55] | 0.513 [0.45,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +10 | LONDON | stack | 0.517 [0.46,0.58] | 0.513 [0.42,0.60] | - | 0.472 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +5 | LONDON | stack | 0.515 [0.46,0.58] | 0.512 [0.44,0.59] | - | 0.514 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +10 | LONDON | stack | 0.537 [0.48,0.59] | 0.511 [0.44,0.59] | - | 0.512 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +5 | ASIA | rf | 0.551 [0.51,0.59] | 0.511 [0.46,0.57] | - | 0.504 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | +10 | ASIA | rf | 0.540 [0.49,0.58] | 0.511 [0.45,0.57] | - | 0.487 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | POOLED/HM | gbt3 | 0.511 [0.49,0.53] | 0.511 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +45 | LONDON | logit2 | 0.491 [0.43,0.55] | 0.511 [0.44,0.59] | - | 0.522 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +15 | ASIA | stack | 0.528 [0.49,0.57] | 0.511 [0.45,0.57] | - | 0.487 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | LONDON | rf | 0.519 [0.48,0.56] | 0.510 [0.46,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +60 | LONDON | stack | 0.530 [0.47,0.59] | 0.510 [0.41,0.61] | - | 0.492 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise-G | sig | NY | rf | 0.510 [0.47,0.55] | 0.510 [0.45,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +60 | NY | rf | 0.525 [0.45,0.59] | 0.509 [0.40,0.62] | - | 0.504 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +10 | LONDON | stack | 0.508 [0.46,0.56] | 0.509 [0.44,0.59] | - | 0.479 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +5 | LONDON | gbt3 | 0.501 [0.44,0.56] | 0.509 [0.42,0.60] | - | 0.528 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | pre | ASIA | rf | 0.532 [0.49,0.58] | 0.509 [0.45,0.57] | - | 0.487 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | POOLED | logit2 | 0.501 [0.48,0.52] | 0.508 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +20 | ASIA | stack | 0.519 [0.48,0.56] | 0.507 [0.44,0.57] | - | 0.487 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +30 | POOLED | logit2 | 0.512 [0.48,0.54] | 0.507 [0.47,0.55] | - | 0.497 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +15 | ASIA | rf | 0.546 [0.51,0.58] | 0.507 [0.45,0.56] | - | 0.486 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +45 | ASIA | rf | 0.539 [0.49,0.58] | 0.507 [0.45,0.57] | - | 0.500 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | pre | ASIA | rf | 0.534 [0.49,0.58] | 0.506 [0.45,0.57] | - | 0.478 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +60 | ASIA | logit2 | 0.532 [0.49,0.57] | 0.506 [0.45,0.57] | - | 0.490 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | POOLED | logit2 | 0.502 [0.48,0.52] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +10 | ASIA | rf | 0.524 [0.48,0.57] | 0.505 [0.45,0.57] | - | 0.484 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +60 | ASIA | logit2 | 0.522 [0.48,0.57] | 0.505 [0.45,0.56] | - | 0.495 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +60 | ASIA | logit2 | 0.516 [0.47,0.56] | 0.505 [0.45,0.56] | - | 0.495 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +30 | LONDON | stack | 0.535 [0.48,0.59] | 0.504 [0.42,0.60] | - | 0.454 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +15 | LONDON | stack | 0.508 [0.45,0.56] | 0.504 [0.43,0.58] | - | 0.508 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +30 | NY | logit2 | 0.509 [0.43,0.59] | 0.504 [0.39,0.62] | - | 0.510 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol-G | sig | NY/ST | stack | 0.504 [0.46,0.56] | 0.504 [0.43,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | pre | NY | logit2 | 0.516 [0.45,0.57] | 0.503 [0.40,0.61] | - | 0.510 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +10 | LONDON | stack | 0.519 [0.46,0.58] | 0.502 [0.43,0.58] | - | 0.496 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol-G | sig | LONDON | rf | 0.514 [0.48,0.55] | 0.502 [0.45,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +60 | ASIA | rf | 0.524 [0.48,0.57] | 0.502 [0.44,0.56] | - | 0.480 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +30 | POOLED | stack | 0.518 [0.49,0.55] | 0.502 [0.46,0.55] | - | 0.467 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | NY/ST | stack | 0.496 [0.45,0.54] | 0.501 [0.44,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | POOLED/ST | gbt3 | 0.498 [0.47,0.53] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | pre | POOLED | stack | 0.533 [0.51,0.56] | 0.500 [0.46,0.54] | - | 0.489 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +10 | ASIA | rf | 0.520 [0.47,0.56] | 0.498 [0.44,0.56] | - | 0.485 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | ASIA | stack | 0.498 [0.47,0.53] | 0.498 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | LONDON/HM | rf | 0.509 [0.46,0.55] | 0.498 [0.44,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +30 | ASIA | stack | 0.559 [0.51,0.60] | 0.497 [0.43,0.57] | - | 0.483 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | +30 | LONDON | stack | 0.563 [0.52,0.61] | 0.497 [0.42,0.59] | - | 0.451 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +20 | ASIA | gbt3 | 0.528 [0.48,0.57] | 0.496 [0.44,0.56] | - | 0.492 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +60 | POOLED | stack | 0.514 [0.48,0.55] | 0.495 [0.44,0.55] | - | 0.486 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff-G | sig | NY/ST | gbt3 | 0.505 [0.45,0.56] | 0.495 [0.41,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +15 | NY | stack | 0.518 [0.45,0.58] | 0.494 [0.38,0.59] | - | 0.505 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789-G | sig | ASIA/ST | gbt3 | 0.490 [0.46,0.52] | 0.493 [0.45,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | +5 | NY | rf | 0.501 [0.44,0.57] | 0.493 [0.39,0.60] | - | 0.556 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +20 | NY | gbt3 | 0.534 [0.47,0.60] | 0.493 [0.39,0.59] | - | 0.515 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | +15 | ASIA | rf | 0.528 [0.49,0.57] | 0.493 [0.44,0.55] | - | 0.482 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +10 | ASIA | gbt3 | 0.542 [0.50,0.59] | 0.493 [0.43,0.55] | - | 0.465 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff-G | sig | LONDON/HM | rf | 0.505 [0.46,0.55] | 0.492 [0.43,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | ASIA | logit2 | 0.487 [0.46,0.51] | 0.492 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +5 | ASIA | rf | 0.530 [0.49,0.57] | 0.492 [0.43,0.56] | - | 0.493 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise-G | sig | ASIA/ST | stack | 0.491 [0.46,0.52] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | pre | NY | stack | 0.483 [0.42,0.54] | 0.490 [0.38,0.60] | - | 0.541 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol-G | sig | ASIA/HM | stack | 0.511 [0.48,0.55] | 0.490 [0.44,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | ASIA | stack | 0.499 [0.47,0.53] | 0.489 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +5 | ASIA | rf | 0.544 [0.50,0.59] | 0.489 [0.43,0.55] | - | 0.481 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol-G | sig | LONDON/ST | gbt3 | 0.510 [0.46,0.56] | 0.488 [0.41,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +5 | NY | rf | 0.508 [0.45,0.57] | 0.488 [0.39,0.59] | - | 0.529 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +15 | ASIA | stack | 0.536 [0.49,0.58] | 0.488 [0.42,0.55] | - | 0.469 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | NY | gbt3 | 0.517 [0.48,0.56] | 0.487 [0.42,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | ASIA/HM | stack | 0.507 [0.47,0.54] | 0.487 [0.43,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | ASIA/ST | gbt3 | 0.476 [0.44,0.51] | 0.486 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | ASIA/ST | gbt3 | 0.479 [0.44,0.51] | 0.486 [0.44,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | POOLED/ST | gbt3 | 0.486 [0.46,0.51] | 0.484 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | pre | ASIA | rf | 0.530 [0.49,0.58] | 0.483 [0.42,0.54] | - | 0.463 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff-G | sig | ASIA/HM | stack | 0.512 [0.47,0.55] | 0.482 [0.43,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | pre | ASIA | stack | 0.520 [0.47,0.56] | 0.482 [0.42,0.55] | - | 0.481 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff-G | sig | ASIA | stack | 0.496 [0.47,0.53] | 0.481 [0.44,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +30 | LONDON | stack | 0.517 [0.46,0.57] | 0.481 [0.39,0.56] | - | 0.439 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | NY/ST | gbt3 | 0.491 [0.43,0.55] | 0.479 [0.40,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +30 | LONDON | stack | 0.530 [0.48,0.58] | 0.479 [0.40,0.56] | - | 0.447 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | pre | LONDON | stack | 0.516 [0.46,0.57] | 0.478 [0.39,0.56] | - | 0.454 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +20 | LONDON | stack | 0.529 [0.48,0.58] | 0.477 [0.40,0.55] | - | 0.447 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff-G | sig | NY/HM | gbt3 | 0.530 [0.48,0.59] | 0.476 [0.39,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise-G | sig | NY/HM | rf | 0.516 [0.47,0.57] | 0.476 [0.40,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | pre | LONDON | stack | 0.524 [0.48,0.58] | 0.476 [0.40,0.55] | - | 0.465 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +10 | NY | logit2 | 0.539 [0.48,0.60] | 0.474 [0.37,0.56] | - | 0.505 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +30 | NY | rf | 0.505 [0.45,0.56] | 0.474 [0.38,0.56] | - | 0.477 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | pre | ASIA | rf | 0.525 [0.48,0.57] | 0.471 [0.40,0.54] | - | 0.463 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | pre | NY | stack | 0.501 [0.44,0.56] | 0.470 [0.37,0.57] | - | 0.477 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | ASIA/HM | stack | 0.491 [0.45,0.53] | 0.468 [0.42,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +5 | NY | stack | 0.499 [0.44,0.56] | 0.468 [0.35,0.57] | - | 0.469 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +60 | ASIA | logit2 | 0.505 [0.46,0.55] | 0.467 [0.40,0.53] | - | 0.458 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789-G | sig | NY | gbt3 | 0.507 [0.47,0.54] | 0.466 [0.41,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +60 | NY | stack | 0.537 [0.47,0.61] | 0.465 [0.34,0.59] | - | 0.447 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | pre | NY | rf | 0.515 [0.45,0.58] | 0.463 [0.36,0.56] | - | 0.479 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol-G | sig | NY/HM | rf | 0.523 [0.47,0.58] | 0.462 [0.38,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | pre | LONDON | stack | 0.489 [0.43,0.54] | 0.462 [0.39,0.55] | - | 0.469 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +5 | NY | gbt3 | 0.498 [0.43,0.58] | 0.458 [0.37,0.57] | - | 0.482 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +15 | NY | logit2 | 0.511 [0.44,0.58] | 0.457 [0.35,0.56] | - | 0.450 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | pre | LONDON | stack | 0.517 [0.45,0.57] | 0.456 [0.37,0.54] | - | 0.459 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | pre | NY | gbt3 | 0.478 [0.41,0.55] | 0.456 [0.35,0.55] | - | 0.476 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-X789 | +30 | NY | logit2 | 0.488 [0.42,0.56] | 0.455 [0.37,0.54] | - | 0.462 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X7-cross-session-handoff | +45 | NY | stack | 0.524 [0.46,0.60] | 0.455 [0.36,0.56] | - | 0.452 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +5 | LONDON | stack | 0.513 [0.46,0.57] | 0.454 [0.39,0.52] | - | 0.433 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X8-vol-of-vol | pre | NY | stack | 0.510 [0.44,0.57] | 0.450 [0.37,0.53] | - | 0.437 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X789-G | sig | NY/HM | gbt3 | 0.526 [0.47,0.58] | 0.449 [0.37,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-X789 | +30 | LONDON | logit2 | 0.476 [0.42,0.53] | 0.409 [0.33,0.49] | - | 0.416 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X9-microstructure-noise | +45 | NY | stack | 0.484 [0.41,0.56] | 0.408 [0.31,0.51] | - | 0.380 | - | ok | - | - | - | - |  | locked label (reference only) |
| X9-microstructure-noise | +20 | NY | stack | 0.509 [0.44,0.57] | 0.405 [0.31,0.50] | - | 0.398 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +60 | NY | rf | 0.480 [0.41,0.55] | 0.401 [0.30,0.50] | - | 0.426 | - | ok | - | - | - | - |  | locked label (reference only) |
| X8-vol-of-vol | +5 | NY | stack | 0.459 [0.39,0.52] | 0.384 [0.30,0.48] | - | 0.417 | - | ok | - | - | - | - |  | locked label (reference only) |
| X7-cross-session-handoff | +30 | NY | logit2 | 0.495 [0.43,0.56] | 0.376 [0.28,0.47] | - | 0.380 | - | ok | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- X7-cross-session-handoff 60 LONDON: run X2_r2c_X7; model chosen by cond WF-PRE 0.467; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 60 POOLED: run X2_r2c_X7; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 30 LONDON: run X2_r2c_X7; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 60 ASIA: run X2_r2c_X7; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 0 POOLED: run X2_r2c_X7; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 0 LONDON: run X2_r2c_X7; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 0 NY: run X2_r2c_X7; model chosen by cond WF-PRE 0.525; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 60 NY: run X2_r2c_X7; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 45 NY: run X2_r2c_X7; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 5 LONDON: run X2_r2c_X7; model chosen by cond WF-PRE 0.536; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 45 LONDON: run X2_r2c_X7; model chosen by cond WF-PRE 0.536; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 10 POOLED: run X2_r2c_X7; model chosen by cond WF-PRE 0.536; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 10 LONDON: run X2_r2c_X7; model chosen by cond WF-PRE 0.539; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 15 NY: run X2_r2c_X7; model chosen by cond WF-PRE 0.541; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 5 NY: run X2_r2c_X7; model chosen by cond WF-PRE 0.541; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 45 POOLED: run X2_r2c_X7; model chosen by cond WF-PRE 0.544; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 20 LONDON: run X2_r2c_X7; model chosen by cond WF-PRE 0.545; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 15 POOLED: run X2_r2c_X7; model chosen by cond WF-PRE 0.546; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 20 POOLED: run X2_r2c_X7; model chosen by cond WF-PRE 0.546; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 0 ASIA: run X2_r2c_X7; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 5 POOLED: run X2_r2c_X7; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 10 NY: run X2_r2c_X7; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 15 LONDON: run X2_r2c_X7; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 30 POOLED: run X2_r2c_X7; model chosen by cond WF-PRE 0.551; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 20 NY: run X2_r2c_X7; model chosen by cond WF-PRE 0.555; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 30 NY: run X2_r2c_X7; model chosen by cond WF-PRE 0.558; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 15 ASIA: run X2_r2c_X7; model chosen by cond WF-PRE 0.564; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 20 ASIA: run X2_r2c_X7; model chosen by cond WF-PRE 0.567; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 10 ASIA: run X2_r2c_X7; model chosen by cond WF-PRE 0.568; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 5 ASIA: run X2_r2c_X7; model chosen by cond WF-PRE 0.582; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 30 ASIA: run X2_r2c_X7; model chosen by cond WF-PRE 0.590; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 45 ASIA: run X2_r2c_X7; model chosen by cond WF-PRE 0.606; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 10 LONDON: run X2_r2c_X7b; model chosen by cond WF-PRE 0.469; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 45 LONDON: run X2_r2c_X7b; model chosen by cond WF-PRE 0.480; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 5 NY: run X2_r2c_X7b; model chosen by cond WF-PRE 0.488; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 0 LONDON: run X2_r2c_X7b; model chosen by cond WF-PRE 0.490; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 30 POOLED: run X2_r2c_X7b; model chosen by cond WF-PRE 0.498; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 5 POOLED: run X2_r2c_X7b; model chosen by cond WF-PRE 0.500; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 20 ASIA: run X2_r2c_X7b; model chosen by cond WF-PRE 0.503; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 15 NY: run X2_r2c_X7b; model chosen by cond WF-PRE 0.504; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 5 ASIA: run X2_r2c_X7b; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 45 NY: run X2_r2c_X7b; model chosen by cond WF-PRE 0.507; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 30 ASIA: run X2_r2c_X7b; model chosen by cond WF-PRE 0.511; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 30 LONDON: run X2_r2c_X7b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 10 POOLED: run X2_r2c_X7b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 15 POOLED: run X2_r2c_X7b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 0 POOLED: run X2_r2c_X7b; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 30 NY: run X2_r2c_X7b; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 10 ASIA: run X2_r2c_X7b; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 20 LONDON: run X2_r2c_X7b; model chosen by cond WF-PRE 0.519; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 15 LONDON: run X2_r2c_X7b; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 20 NY: run X2_r2c_X7b; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 60 NY: run X2_r2c_X7b; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 10 NY: run X2_r2c_X7b; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 60 LONDON: run X2_r2c_X7b; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 20 POOLED: run X2_r2c_X7b; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 60 ASIA: run X2_r2c_X7b; model chosen by cond WF-PRE 0.525; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 60 POOLED: run X2_r2c_X7b; model chosen by cond WF-PRE 0.525; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 5 LONDON: run X2_r2c_X7b; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 0 ASIA: run X2_r2c_X7b; model chosen by cond WF-PRE 0.539; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 45 POOLED: run X2_r2c_X7b; model chosen by cond WF-PRE 0.542; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 0 NY: run X2_r2c_X7b; model chosen by cond WF-PRE 0.542; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 15 ASIA: run X2_r2c_X7b; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff 45 ASIA: run X2_r2c_X7b; model chosen by cond WF-PRE 0.582; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 45 LONDON: run X2_r2c_X8; model chosen by cond WF-PRE 0.472; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 15 LONDON: run X2_r2c_X8; model chosen by cond WF-PRE 0.473; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 60 LONDON: run X2_r2c_X8; model chosen by cond WF-PRE 0.486; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 5 LONDON: run X2_r2c_X8; model chosen by cond WF-PRE 0.495; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 10 LONDON: run X2_r2c_X8; model chosen by cond WF-PRE 0.500; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 20 LONDON: run X2_r2c_X8; model chosen by cond WF-PRE 0.502; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 45 NY: run X2_r2c_X8; model chosen by cond WF-PRE 0.504; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 30 LONDON: run X2_r2c_X8; model chosen by cond WF-PRE 0.505; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 0 NY: run X2_r2c_X8; model chosen by cond WF-PRE 0.507; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 30 NY: run X2_r2c_X8; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 45 POOLED: run X2_r2c_X8; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 15 NY: run X2_r2c_X8; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 0 POOLED: run X2_r2c_X8; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 60 POOLED: run X2_r2c_X8; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 15 POOLED: run X2_r2c_X8; model chosen by cond WF-PRE 0.537; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 60 ASIA: run X2_r2c_X8; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 0 LONDON: run X2_r2c_X8; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 30 POOLED: run X2_r2c_X8; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 60 NY: run X2_r2c_X8; model chosen by cond WF-PRE 0.546; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 5 POOLED: run X2_r2c_X8; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 5 NY: run X2_r2c_X8; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 0 ASIA: run X2_r2c_X8; model chosen by cond WF-PRE 0.553; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 20 POOLED: run X2_r2c_X8; model chosen by cond WF-PRE 0.557; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 10 POOLED: run X2_r2c_X8; model chosen by cond WF-PRE 0.558; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 20 NY: run X2_r2c_X8; model chosen by cond WF-PRE 0.561; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 45 ASIA: run X2_r2c_X8; model chosen by cond WF-PRE 0.566; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 20 ASIA: run X2_r2c_X8; model chosen by cond WF-PRE 0.570; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 5 ASIA: run X2_r2c_X8; model chosen by cond WF-PRE 0.570; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 15 ASIA: run X2_r2c_X8; model chosen by cond WF-PRE 0.572; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 10 NY: run X2_r2c_X8; model chosen by cond WF-PRE 0.578; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 30 ASIA: run X2_r2c_X8; model chosen by cond WF-PRE 0.580; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 10 ASIA: run X2_r2c_X8; model chosen by cond WF-PRE 0.585; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 0 LONDON: run X2_r2c_X8b; model chosen by cond WF-PRE 0.474; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 15 NY: run X2_r2c_X8b; model chosen by cond WF-PRE 0.481; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 10 LONDON: run X2_r2c_X8b; model chosen by cond WF-PRE 0.488; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 30 NY: run X2_r2c_X8b; model chosen by cond WF-PRE 0.496; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 60 LONDON: run X2_r2c_X8b; model chosen by cond WF-PRE 0.501; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 45 LONDON: run X2_r2c_X8b; model chosen by cond WF-PRE 0.505; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 5 LONDON: run X2_r2c_X8b; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 30 POOLED: run X2_r2c_X8b; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 5 NY: run X2_r2c_X8b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 5 POOLED: run X2_r2c_X8b; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 60 POOLED: run X2_r2c_X8b; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 15 POOLED: run X2_r2c_X8b; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 20 ASIA: run X2_r2c_X8b; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 20 POOLED: run X2_r2c_X8b; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 20 LONDON: run X2_r2c_X8b; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 15 ASIA: run X2_r2c_X8b; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 10 POOLED: run X2_r2c_X8b; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 30 LONDON: run X2_r2c_X8b; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 10 ASIA: run X2_r2c_X8b; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 20 NY: run X2_r2c_X8b; model chosen by cond WF-PRE 0.530; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 30 ASIA: run X2_r2c_X8b; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 45 POOLED: run X2_r2c_X8b; model chosen by cond WF-PRE 0.535; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 5 ASIA: run X2_r2c_X8b; model chosen by cond WF-PRE 0.537; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 45 NY: run X2_r2c_X8b; model chosen by cond WF-PRE 0.538; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 15 LONDON: run X2_r2c_X8b; model chosen by cond WF-PRE 0.541; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 60 ASIA: run X2_r2c_X8b; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 0 POOLED: run X2_r2c_X8b; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 60 NY: run X2_r2c_X8b; model chosen by cond WF-PRE 0.547; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 0 NY: run X2_r2c_X8b; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 0 ASIA: run X2_r2c_X8b; model chosen by cond WF-PRE 0.550; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 10 NY: run X2_r2c_X8b; model chosen by cond WF-PRE 0.551; econ/CPCV not run (cond pre AUC<0.60)
- X8-vol-of-vol 45 ASIA: run X2_r2c_X8b; model chosen by cond WF-PRE 0.560; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 45 NY: run X2_r2c_X9; model chosen by cond WF-PRE 0.469; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 0 NY: run X2_r2c_X9; model chosen by cond WF-PRE 0.484; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 30 ASIA: run X2_r2c_X9; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 60 POOLED: run X2_r2c_X9; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 30 LONDON: run X2_r2c_X9; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 45 POOLED: run X2_r2c_X9; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 20 LONDON: run X2_r2c_X9; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 45 ASIA: run X2_r2c_X9; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 30 NY: run X2_r2c_X9; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 30 POOLED: run X2_r2c_X9; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 60 ASIA: run X2_r2c_X9; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 15 LONDON: run X2_r2c_X9; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 5 POOLED: run X2_r2c_X9; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 5 LONDON: run X2_r2c_X9; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 60 LONDON: run X2_r2c_X9; model chosen by cond WF-PRE 0.537; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 5 NY: run X2_r2c_X9; model chosen by cond WF-PRE 0.537; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 20 POOLED: run X2_r2c_X9; model chosen by cond WF-PRE 0.539; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 10 POOLED: run X2_r2c_X9; model chosen by cond WF-PRE 0.539; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 0 POOLED: run X2_r2c_X9; model chosen by cond WF-PRE 0.539; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 15 ASIA: run X2_r2c_X9; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 10 LONDON: run X2_r2c_X9; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 0 LONDON: run X2_r2c_X9; model chosen by cond WF-PRE 0.542; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 20 ASIA: run X2_r2c_X9; model chosen by cond WF-PRE 0.546; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 45 LONDON: run X2_r2c_X9; model chosen by cond WF-PRE 0.547; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 15 POOLED: run X2_r2c_X9; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 60 NY: run X2_r2c_X9; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 15 NY: run X2_r2c_X9; model chosen by cond WF-PRE 0.550; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 5 ASIA: run X2_r2c_X9; model chosen by cond WF-PRE 0.551; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 0 ASIA: run X2_r2c_X9; model chosen by cond WF-PRE 0.557; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 20 NY: run X2_r2c_X9; model chosen by cond WF-PRE 0.560; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 10 ASIA: run X2_r2c_X9; model chosen by cond WF-PRE 0.564; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 10 NY: run X2_r2c_X9; model chosen by cond WF-PRE 0.600; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 10 LONDON: run X2_r2c_X9b; model chosen by cond WF-PRE 0.460; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 5 POOLED: run X2_r2c_X9b; model chosen by cond WF-PRE 0.486; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 10 NY: run X2_r2c_X9b; model chosen by cond WF-PRE 0.487; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 15 NY: run X2_r2c_X9b; model chosen by cond WF-PRE 0.490; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 5 ASIA: run X2_r2c_X9b; model chosen by cond WF-PRE 0.497; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 45 NY: run X2_r2c_X9b; model chosen by cond WF-PRE 0.497; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 45 LONDON: run X2_r2c_X9b; model chosen by cond WF-PRE 0.502; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 20 ASIA: run X2_r2c_X9b; model chosen by cond WF-PRE 0.504; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 15 POOLED: run X2_r2c_X9b; model chosen by cond WF-PRE 0.504; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 30 POOLED: run X2_r2c_X9b; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 10 POOLED: run X2_r2c_X9b; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 30 NY: run X2_r2c_X9b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 60 ASIA: run X2_r2c_X9b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 0 LONDON: run X2_r2c_X9b; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 10 ASIA: run X2_r2c_X9b; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 60 POOLED: run X2_r2c_X9b; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 0 POOLED: run X2_r2c_X9b; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 15 ASIA: run X2_r2c_X9b; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 60 LONDON: run X2_r2c_X9b; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 15 LONDON: run X2_r2c_X9b; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 0 ASIA: run X2_r2c_X9b; model chosen by cond WF-PRE 0.526; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 0 NY: run X2_r2c_X9b; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 30 ASIA: run X2_r2c_X9b; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 5 NY: run X2_r2c_X9b; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 45 POOLED: run X2_r2c_X9b; model chosen by cond WF-PRE 0.530; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 60 NY: run X2_r2c_X9b; model chosen by cond WF-PRE 0.531; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 20 POOLED: run X2_r2c_X9b; model chosen by cond WF-PRE 0.535; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 5 LONDON: run X2_r2c_X9b; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 20 LONDON: run X2_r2c_X9b; model chosen by cond WF-PRE 0.544; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 30 LONDON: run X2_r2c_X9b; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 45 ASIA: run X2_r2c_X9b; model chosen by cond WF-PRE 0.560; econ/CPCV not run (cond pre AUC<0.60)
- X9-microstructure-noise 20 NY: run X2_r2c_X9b; model chosen by cond WF-PRE 0.561; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 45 LONDON: run X2_r2c_X789b; model chosen by cond WF-PRE 0.464; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 0 LONDON: run X2_r2c_X789b; model chosen by cond WF-PRE 0.482; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 10 LONDON: run X2_r2c_X789b; model chosen by cond WF-PRE 0.494; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 15 NY: run X2_r2c_X789b; model chosen by cond WF-PRE 0.496; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 30 NY: run X2_r2c_X789b; model chosen by cond WF-PRE 0.507; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 20 LONDON: run X2_r2c_X789b; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 15 POOLED: run X2_r2c_X789b; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 60 LONDON: run X2_r2c_X789b; model chosen by cond WF-PRE 0.510; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 20 POOLED: run X2_r2c_X789b; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 5 POOLED: run X2_r2c_X789b; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 60 POOLED: run X2_r2c_X789b; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 45 NY: run X2_r2c_X789b; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 10 POOLED: run X2_r2c_X789b; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 30 POOLED: run X2_r2c_X789b; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 20 NY: run X2_r2c_X789b; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 15 ASIA: run X2_r2c_X789b; model chosen by cond WF-PRE 0.525; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 5 NY: run X2_r2c_X789b; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 45 POOLED: run X2_r2c_X789b; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 10 NY: run X2_r2c_X789b; model chosen by cond WF-PRE 0.530; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 5 ASIA: run X2_r2c_X789b; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 0 POOLED: run X2_r2c_X789b; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 0 NY: run X2_r2c_X789b; model chosen by cond WF-PRE 0.537; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 20 ASIA: run X2_r2c_X789b; model chosen by cond WF-PRE 0.538; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 5 LONDON: run X2_r2c_X789b; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 60 NY: run X2_r2c_X789b; model chosen by cond WF-PRE 0.546; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 10 ASIA: run X2_r2c_X789b; model chosen by cond WF-PRE 0.546; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 0 ASIA: run X2_r2c_X789b; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 60 ASIA: run X2_r2c_X789b; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 30 ASIA: run X2_r2c_X789b; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 15 LONDON: run X2_r2c_X789b; model chosen by cond WF-PRE 0.551; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 45 ASIA: run X2_r2c_X789b; model chosen by cond WF-PRE 0.563; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 30 LONDON: run X2_r2c_X789b; model chosen by cond WF-PRE 0.587; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 15 LONDON: run X2_r2c_X789pt; model chosen by cond WF-PRE 0.502; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 30 POOLED: run X2_r2c_X789pt; model chosen by cond WF-PRE 0.511; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 30 LONDON: run X2_r2c_X789pt; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 30 NY: run X2_r2c_X789pt; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 30 ASIA: run X2_r2c_X789pt; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 15 ASIA: run X2_r2c_X789pt; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 15 NY: run X2_r2c_X789pt; model chosen by cond WF-PRE 0.550; econ/CPCV not run (cond pre AUC<0.60)
- combo-X789 15 POOLED: run X2_r2c_X789pt; model chosen by cond WF-PRE 0.556; econ/CPCV not run (cond pre AUC<0.60)
- X7-cross-session-handoff-G -1 ASIA: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 POOLED: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 POOLED: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 ASIA: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 NY: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 LONDON: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 POOLED: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 LONDON: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 LONDON: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 NY: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 ASIA: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 NY: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 ASIA: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 ASIA: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 ASIA: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 NY: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 POOLED: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 POOLED: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 POOLED: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 NY: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 LONDON: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 NY: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 LONDON: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-cross-session-handoff-G -1 LONDON: FAILPRED feats + X7 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 ASIA: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 POOLED: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 ASIA: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 POOLED: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 NY: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 POOLED: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 NY: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 LONDON: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 LONDON: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 LONDON: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 ASIA: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 NY: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 ASIA: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 ASIA: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 ASIA: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 POOLED: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 NY: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 POOLED: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 POOLED: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 NY: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 LONDON: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 NY: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 LONDON: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-vol-of-vol-G -1 LONDON: FAILPRED feats + X8 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 ASIA: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 POOLED: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 NY: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 POOLED: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 POOLED: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 ASIA: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 NY: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 LONDON: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 LONDON: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 LONDON: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 ASIA: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 NY: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 ASIA: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 ASIA: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 ASIA: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 POOLED: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 POOLED: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 POOLED: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 NY: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 NY: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 LONDON: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 NY: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 LONDON: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-microstructure-noise-G -1 LONDON: FAILPRED feats + X9 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 ASIA: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 ASIA: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 POOLED: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 POOLED: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 NY: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 POOLED: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 ASIA: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 LONDON: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 LONDON: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 LONDON: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 NY: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 NY: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 ASIA: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 ASIA: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 ASIA: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 POOLED: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 POOLED: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 POOLED: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 NY: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 NY: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 LONDON: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 NY: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 LONDON: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X789-G -1 LONDON: FAILPRED feats + X789 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
