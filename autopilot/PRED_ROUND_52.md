# PRED ROUND 52 - block K round 5 - K5-latefusion-cond

Best HOLDOUT F-R AUC: +15 POOLED 0.568 [0.52,0.61] | ASIA 0.496 [0.44,0.56] | LONDON 0.523 [0.44,0.60] | NY 0.618 [0.52,0.72]
Best HOLDOUT F-R AUC: +30 POOLED 0.569 [0.52,0.61] | ASIA 0.532 [0.47,0.60] | LONDON 0.559 [0.48,0.63] | NY 0.485 [0.39,0.60]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 98e49f7e82f818b3ec43452b754e719d7b4203d0aa0995aed057afc6f590672e ; trials added 900 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K5-latefusion-cond | +15 | NY | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.569 [0.50,0.64] | 0.618 [0.52,0.72] | - | 0.614 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +10 | POOLED | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.555 [0.53,0.58] | 0.581 [0.54,0.62] | - | 0.553 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +30 | POOLED | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.549 [0.52,0.58] | 0.569 [0.52,0.61] | - | 0.537 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +60 | LONDON | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.554 [0.50,0.60] | 0.569 [0.49,0.64] | - | 0.552 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +15 | POOLED | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.561 [0.53,0.59] | 0.568 [0.52,0.61] | - | 0.556 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | pre | POOLED | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.535 [0.51,0.56] | 0.564 [0.52,0.61] | - | 0.533 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +30 | LONDON | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.534 [0.48,0.59] | 0.559 [0.48,0.63] | - | 0.526 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +5 | NY | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.511 [0.45,0.57] | 0.557 [0.46,0.65] | - | 0.573 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +5 | POOLED | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.533 [0.50,0.56] | 0.547 [0.51,0.59] | - | 0.547 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +5 | LONDON | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.541 [0.48,0.59] | 0.547 [0.48,0.62] | - | 0.556 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +10 | ASIA | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.555 [0.51,0.59] | 0.546 [0.48,0.61] | - | 0.523 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +10 | LONDON | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.533 [0.48,0.59] | 0.546 [0.48,0.61] | - | 0.528 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +20 | POOLED | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.552 [0.52,0.58] | 0.544 [0.50,0.59] | - | 0.538 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +20 | NY | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.555 [0.49,0.62] | 0.534 [0.44,0.63] | - | 0.528 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +30 | ASIA | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.542 [0.50,0.58] | 0.532 [0.47,0.60] | - | 0.500 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +45 | ASIA | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.523 [0.48,0.56] | 0.531 [0.47,0.59] | - | 0.509 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | pre | LONDON | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.531 [0.47,0.59] | 0.530 [0.45,0.61] | - | 0.509 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | pre | ASIA | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.536 [0.49,0.58] | 0.526 [0.46,0.58] | - | 0.503 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +15 | LONDON | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.499 [0.44,0.55] | 0.523 [0.44,0.60] | - | 0.526 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +60 | POOLED | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.522 [0.49,0.55] | 0.522 [0.48,0.57] | - | 0.492 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +45 | POOLED | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.515 [0.49,0.54] | 0.512 [0.47,0.55] | - | 0.481 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +20 | ASIA | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.528 [0.48,0.57] | 0.511 [0.45,0.57] | - | 0.502 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +15 | ASIA | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.558 [0.51,0.60] | 0.496 [0.44,0.56] | - | 0.493 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +60 | ASIA | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.479 [0.43,0.53] | 0.496 [0.43,0.57] | - | 0.461 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +5 | ASIA | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.509 [0.47,0.56] | 0.492 [0.42,0.56] | - | 0.490 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +20 | LONDON | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.548 [0.49,0.60] | 0.491 [0.42,0.57] | - | 0.524 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +30 | NY | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.508 [0.43,0.58] | 0.485 [0.39,0.60] | - | 0.482 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +60 | NY | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.515 [0.44,0.59] | 0.478 [0.37,0.59] | - | 0.459 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +45 | NY | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.490 [0.42,0.56] | 0.472 [0.36,0.59] | - | 0.462 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +10 | NY | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.494 [0.43,0.55] | 0.459 [0.36,0.56] | - | 0.493 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | pre | NY | AVG(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.464 [0.40,0.52] | 0.448 [0.36,0.53] | - | 0.454 | - | - | - | - | - | - | stack | locked label (reference only) |
| K5-latefusion-cond | +45 | LONDON | META(base,A,E,F,G,I,B,E2g,C,I2,X cond) | 0.467 [0.41,0.52] | 0.426 [0.35,0.50] | - | 0.394 | - | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- K5-latefusion-cond 0 POOLED: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 5 POOLED: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 10 POOLED: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 15 POOLED: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 20 POOLED: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 30 POOLED: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 45 POOLED: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 60 POOLED: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 0 ASIA: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 5 ASIA: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 10 ASIA: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 15 ASIA: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 20 ASIA: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 30 ASIA: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 45 ASIA: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 60 ASIA: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 0 LONDON: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 5 LONDON: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 10 LONDON: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 15 LONDON: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 20 LONDON: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 30 LONDON: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 45 LONDON: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 60 LONDON: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 0 NY: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 5 NY: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 10 NY: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 15 NY: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 20 NY: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 30 NY: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 45 NY: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
- K5-latefusion-cond 60 NY: conditional late fusion of 10 families; no signal (WF-PRE<=0.55)
