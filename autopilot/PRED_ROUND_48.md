# PRED ROUND 48 - block X5 round 4 - X31-aggressor-flow+X32-book-depth+X33-approach-dynamics+X34-level-proximity+X35-whipsaw-neighbours

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.617 [0.57,0.66]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 1fc036460ebd3d85d19e8e0e4186ee48a0d58715abf4f72894217d4961909264 ; trials added 130 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X31_sig.parquet', 'l2vast/pred/store/X32_sig.parquet', 'l2vast/pred/store/X33_sig.parquet', 'l2vast/pred/store/X34_sig.parquet', 'l2vast/pred/store/X35_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X34-level-proximity | sig | ASIA/HM | M34R:stack | 0.589 [0.56,0.62] | 0.617 [0.57,0.66] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | ASIA | M34R:stack | 0.583 [0.56,0.61] | 0.602 [0.57,0.64] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | NY/ST | M31R:stack | 0.520 [0.47,0.57] | 0.593 [0.53,0.65] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | ASIA/ST | M34R:stack | 0.577 [0.55,0.61] | 0.591 [0.55,0.63] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | POOLED/HM | M34R:stack | 0.560 [0.54,0.58] | 0.580 [0.55,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | NY/ST | M32R:stack | 0.532 [0.49,0.59] | 0.580 [0.52,0.65] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | POOLED | M34R:stack | 0.560 [0.54,0.58] | 0.577 [0.56,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | POOLED/ST | M34R:stack | 0.559 [0.54,0.58] | 0.574 [0.55,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | NY | M31R:stack | 0.526 [0.49,0.56] | 0.569 [0.52,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | NY/ST | M33R:stack | 0.522 [0.48,0.57] | 0.565 [0.49,0.63] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | LONDON/ST | M35T:stack | 0.487 [0.44,0.53] | 0.560 [0.50,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | NY | M32R:stack | 0.518 [0.48,0.55] | 0.559 [0.51,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | NY | M33R:stack | 0.523 [0.49,0.56] | 0.554 [0.50,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | NY/ST | M35R:stack | 0.507 [0.46,0.56] | 0.552 [0.49,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | NY/HM | M34R:stack | 0.571 [0.52,0.62] | 0.549 [0.48,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | LONDON | M34R:stack | 0.519 [0.48,0.56] | 0.546 [0.49,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | LONDON/ST | M34R:stack | 0.519 [0.47,0.56] | 0.545 [0.49,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | NY | M34R:stack | 0.557 [0.52,0.59] | 0.545 [0.50,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | NY/ST | M34R:stack | 0.548 [0.51,0.59] | 0.545 [0.48,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | LONDON/HM | M34R:stack | 0.517 [0.47,0.56] | 0.544 [0.48,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | NY/HM | M31R:stack | 0.534 [0.49,0.58] | 0.540 [0.48,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | LONDON/ST | M32R:stack | 0.505 [0.46,0.55] | 0.540 [0.48,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | ASIA/HM | M34T:stack | 0.542 [0.50,0.58] | 0.540 [0.49,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | NY | M35R:stack | 0.495 [0.46,0.53] | 0.539 [0.48,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | LONDON | M35T:stack | 0.484 [0.44,0.53] | 0.539 [0.48,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | ASIA/HM | M31R:stack | 0.532 [0.50,0.57] | 0.539 [0.49,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | LONDON/HM | M31R:stack | 0.459 [0.41,0.51] | 0.537 [0.48,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | NY/HM | M33R:stack | 0.523 [0.48,0.56] | 0.536 [0.47,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | POOLED/HM | M31R:stack | 0.508 [0.48,0.53] | 0.536 [0.51,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | ASIA | M34T:stack | 0.534 [0.50,0.56] | 0.535 [0.50,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | LONDON/ST | M34T:stack | 0.506 [0.46,0.55] | 0.535 [0.47,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | POOLED | M31R:stack | 0.508 [0.49,0.53] | 0.533 [0.51,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | LONDON/ST | M31T:stack | 0.478 [0.43,0.52] | 0.533 [0.46,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | POOLED/ST | M31R:stack | 0.508 [0.48,0.53] | 0.533 [0.50,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | ASIA/ST | M34T:stack | 0.527 [0.49,0.56] | 0.532 [0.48,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | NY/HM | M32R:stack | 0.502 [0.45,0.55] | 0.531 [0.45,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | POOLED/ST | M32R:stack | 0.517 [0.49,0.54] | 0.530 [0.50,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | POOLED/HM | M34T:stack | 0.528 [0.50,0.55] | 0.529 [0.50,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | LONDON | M34T:stack | 0.498 [0.46,0.54] | 0.528 [0.48,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | POOLED | M34T:stack | 0.522 [0.50,0.54] | 0.526 [0.50,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | ASIA | M31R:stack | 0.517 [0.49,0.54] | 0.525 [0.49,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | NY/HM | M35R:stack | 0.485 [0.44,0.53] | 0.525 [0.45,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | LONDON | M31R:stack | 0.477 [0.44,0.51] | 0.523 [0.48,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | POOLED/ST | M34T:stack | 0.516 [0.49,0.54] | 0.523 [0.49,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | LONDON/HM | M34T:stack | 0.490 [0.44,0.54] | 0.522 [0.44,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | LONDON/HM | M35T:stack | 0.479 [0.43,0.53] | 0.519 [0.44,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | NY/HM | M35T:stack | 0.465 [0.42,0.52] | 0.518 [0.44,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | ASIA/ST | M31R:stack | 0.505 [0.47,0.54] | 0.517 [0.47,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | LONDON/ST | M32T:stack | 0.492 [0.44,0.54] | 0.516 [0.45,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | ASIA/HM | M33T:stack | 0.506 [0.47,0.54] | 0.514 [0.47,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | LONDON/ST | M35R:stack | 0.493 [0.45,0.54] | 0.514 [0.45,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | POOLED | M32R:stack | 0.504 [0.48,0.52] | 0.514 [0.49,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | LONDON | M35R:stack | 0.484 [0.44,0.52] | 0.512 [0.46,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | NY/ST | M31T:stack | 0.476 [0.43,0.53] | 0.511 [0.45,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | POOLED/ST | M35R:stack | 0.499 [0.47,0.52] | 0.511 [0.48,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | LONDON/ST | M31R:stack | 0.494 [0.45,0.54] | 0.511 [0.44,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | LONDON/HM | M35R:stack | 0.476 [0.43,0.52] | 0.510 [0.44,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | NY/HM | M34T:stack | 0.552 [0.50,0.61] | 0.510 [0.43,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | POOLED/ST | M31T:stack | 0.479 [0.45,0.50] | 0.508 [0.48,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | ASIA | M33T:stack | 0.509 [0.48,0.54] | 0.506 [0.47,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | POOLED | M35R:stack | 0.493 [0.47,0.51] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | LONDON/HM | M33T:stack | 0.489 [0.45,0.53] | 0.506 [0.45,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | NY | M31T:stack | 0.486 [0.45,0.52] | 0.506 [0.45,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | NY/HM | M31T:stack | 0.496 [0.44,0.55] | 0.505 [0.42,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | ASIA | M32R:stack | 0.503 [0.47,0.53] | 0.504 [0.46,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | ASIA/ST | M32R:stack | 0.512 [0.47,0.55] | 0.503 [0.45,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | ASIA/HM | M32R:stack | 0.492 [0.45,0.53] | 0.503 [0.45,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | LONDON | M33T:stack | 0.481 [0.44,0.52] | 0.503 [0.45,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | POOLED/HM | M35T:stack | 0.491 [0.47,0.52] | 0.502 [0.46,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | POOLED/HM | M35R:stack | 0.486 [0.46,0.51] | 0.502 [0.47,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | LONDON/ST | M33T:stack | 0.472 [0.43,0.52] | 0.501 [0.44,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | ASIA/HM | M31T:stack | 0.519 [0.48,0.55] | 0.500 [0.46,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | ASIA/ST | M33T:stack | 0.513 [0.48,0.55] | 0.500 [0.45,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | LONDON/ST | M33R:stack | 0.451 [0.40,0.50] | 0.500 [0.43,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | POOLED/ST | M33T:stack | 0.496 [0.47,0.52] | 0.499 [0.47,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | ASIA | M31T:stack | 0.499 [0.47,0.53] | 0.499 [0.46,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | POOLED | M31T:stack | 0.485 [0.47,0.50] | 0.499 [0.47,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | LONDON | M32R:stack | 0.490 [0.46,0.52] | 0.498 [0.46,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | LONDON | M31T:stack | 0.460 [0.43,0.49] | 0.497 [0.45,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | POOLED/HM | M32R:stack | 0.489 [0.46,0.51] | 0.497 [0.46,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | ASIA/ST | M31T:stack | 0.481 [0.44,0.52] | 0.496 [0.45,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | POOLED | M35T:stack | 0.487 [0.47,0.51] | 0.495 [0.47,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | NY | M34T:stack | 0.525 [0.49,0.56] | 0.494 [0.44,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | NY/ST | M33T:stack | 0.486 [0.44,0.54] | 0.493 [0.44,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | LONDON | M32T:stack | 0.472 [0.43,0.51] | 0.493 [0.44,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | ASIA/HM | M35R:stack | 0.495 [0.46,0.53] | 0.492 [0.44,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | POOLED | M33T:stack | 0.489 [0.47,0.51] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | ASIA/HM | M33R:stack | 0.493 [0.46,0.53] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | POOLED/ST | M35T:stack | 0.482 [0.46,0.51] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | POOLED/ST | M33R:stack | 0.483 [0.46,0.51] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | ASIA | M35R:stack | 0.493 [0.46,0.52] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | ASIA/HM | M35T:stack | 0.511 [0.47,0.55] | 0.489 [0.43,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | POOLED | M33R:stack | 0.483 [0.46,0.50] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | POOLED/HM | M31T:stack | 0.491 [0.47,0.51] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | POOLED/HM | M33R:stack | 0.484 [0.46,0.51] | 0.488 [0.45,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | ASIA/ST | M35R:stack | 0.491 [0.46,0.52] | 0.488 [0.44,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | POOLED/HM | M33T:stack | 0.482 [0.46,0.51] | 0.485 [0.45,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | ASIA | M35T:stack | 0.497 [0.46,0.53] | 0.485 [0.44,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | ASIA/ST | M35T:stack | 0.485 [0.45,0.52] | 0.481 [0.44,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X34-level-proximity | sig | NY/ST | M34T:stack | 0.500 [0.45,0.55] | 0.480 [0.42,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | POOLED/ST | M32T:stack | 0.478 [0.45,0.50] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | NY/HM | M32T:stack | 0.487 [0.43,0.54] | 0.477 [0.39,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | LONDON | M33R:stack | 0.445 [0.41,0.48] | 0.475 [0.43,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | ASIA/ST | M32T:stack | 0.475 [0.44,0.51] | 0.475 [0.44,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | LONDON/HM | M32T:stack | 0.451 [0.40,0.50] | 0.472 [0.40,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | ASIA | M33R:stack | 0.485 [0.46,0.51] | 0.471 [0.43,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | NY | M35T:stack | 0.468 [0.43,0.51] | 0.469 [0.41,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | NY | M32T:stack | 0.477 [0.44,0.52] | 0.465 [0.41,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | POOLED | M32T:stack | 0.468 [0.45,0.49] | 0.464 [0.44,0.49] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X31-aggressor-flow | sig | LONDON/HM | M31T:stack | 0.440 [0.39,0.48] | 0.460 [0.40,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | LONDON/HM | M32R:stack | 0.475 [0.44,0.51] | 0.456 [0.40,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | ASIA/ST | M33R:stack | 0.478 [0.44,0.51] | 0.455 [0.41,0.50] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | NY/ST | M32T:stack | 0.468 [0.41,0.53] | 0.453 [0.38,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | ASIA | M32T:stack | 0.462 [0.44,0.49] | 0.452 [0.42,0.49] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | LONDON/HM | M33R:stack | 0.439 [0.39,0.48] | 0.451 [0.39,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | POOLED/HM | M32T:stack | 0.457 [0.43,0.48] | 0.448 [0.41,0.49] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | NY | M33T:stack | 0.456 [0.42,0.49] | 0.442 [0.40,0.49] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X35-whipsaw-neighbours | sig | NY/ST | M35T:stack | 0.472 [0.42,0.52] | 0.430 [0.37,0.49] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X32-book-depth | sig | ASIA/HM | M32T:stack | 0.448 [0.41,0.49] | 0.427 [0.38,0.48] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X33-approach-dynamics | sig | NY/HM | M33T:stack | 0.421 [0.37,0.47] | 0.376 [0.31,0.45] | - | - | - | N | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- X31-aggressor-flow -1 POOLED: family+minimal+noise; econ not run (holdout stop_vs_target AUC < 0.58)
- X31-aggressor-flow -1 ASIA: family+minimal+noise
- X31-aggressor-flow -1 LONDON: family+minimal+noise
- X31-aggressor-flow -1 NY: family+minimal+noise
- X31-aggressor-flow -1 POOLED: family+minimal+noise
- X31-aggressor-flow -1 ASIA: family+minimal+noise
- X31-aggressor-flow -1 LONDON: family+minimal+noise
- X31-aggressor-flow -1 NY: family+minimal+noise
- X31-aggressor-flow -1 POOLED: family+minimal+noise
- X31-aggressor-flow -1 ASIA: family+minimal+noise
- X31-aggressor-flow -1 LONDON: family+minimal+noise
- X31-aggressor-flow -1 NY: family+minimal+noise
- X31-aggressor-flow -1 POOLED: family+minimal+noise; econ not run (holdout stop_vs_target AUC < 0.58)
- X31-aggressor-flow -1 ASIA: family+minimal+noise
- X31-aggressor-flow -1 LONDON: family+minimal+noise
- X31-aggressor-flow -1 NY: family+minimal+noise
- X31-aggressor-flow -1 POOLED: family+minimal+noise
- X31-aggressor-flow -1 ASIA: family+minimal+noise
- X31-aggressor-flow -1 LONDON: family+minimal+noise
- X31-aggressor-flow -1 NY: family+minimal+noise
- X31-aggressor-flow -1 POOLED: family+minimal+noise
- X31-aggressor-flow -1 ASIA: family+minimal+noise
- X31-aggressor-flow -1 LONDON: family+minimal+noise
- X31-aggressor-flow -1 NY: family+minimal+noise
- X32-book-depth -1 POOLED: family+minimal+noise; econ not run (holdout stop_vs_target AUC < 0.58)
- X32-book-depth -1 ASIA: family+minimal+noise
- X32-book-depth -1 LONDON: family+minimal+noise
- X32-book-depth -1 NY: family+minimal+noise
- X32-book-depth -1 POOLED: family+minimal+noise
- X32-book-depth -1 ASIA: family+minimal+noise
- X32-book-depth -1 LONDON: family+minimal+noise
- X32-book-depth -1 NY: family+minimal+noise
- X32-book-depth -1 POOLED: family+minimal+noise
- X32-book-depth -1 ASIA: family+minimal+noise
- X32-book-depth -1 LONDON: family+minimal+noise
- X32-book-depth -1 NY: family+minimal+noise
- X32-book-depth -1 POOLED: family+minimal+noise; econ not run (holdout stop_vs_target AUC < 0.58)
- X32-book-depth -1 ASIA: family+minimal+noise
- X32-book-depth -1 LONDON: family+minimal+noise
- X32-book-depth -1 NY: family+minimal+noise
- X32-book-depth -1 POOLED: family+minimal+noise
- X32-book-depth -1 ASIA: family+minimal+noise
- X32-book-depth -1 LONDON: family+minimal+noise
- X32-book-depth -1 NY: family+minimal+noise
- X32-book-depth -1 POOLED: family+minimal+noise
- X32-book-depth -1 ASIA: family+minimal+noise
- X32-book-depth -1 LONDON: family+minimal+noise
- X32-book-depth -1 NY: family+minimal+noise
- X33-approach-dynamics -1 POOLED: family+minimal+noise; econ not run (holdout stop_vs_target AUC < 0.58)
- X33-approach-dynamics -1 ASIA: family+minimal+noise
- X33-approach-dynamics -1 LONDON: family+minimal+noise
- X33-approach-dynamics -1 NY: family+minimal+noise
- X33-approach-dynamics -1 POOLED: family+minimal+noise
- X33-approach-dynamics -1 ASIA: family+minimal+noise
- X33-approach-dynamics -1 LONDON: family+minimal+noise
- X33-approach-dynamics -1 NY: family+minimal+noise
- X33-approach-dynamics -1 POOLED: family+minimal+noise
- X33-approach-dynamics -1 ASIA: family+minimal+noise
- X33-approach-dynamics -1 LONDON: family+minimal+noise
- X33-approach-dynamics -1 NY: family+minimal+noise
- X33-approach-dynamics -1 POOLED: family+minimal+noise; econ not run (holdout stop_vs_target AUC < 0.58)
- X33-approach-dynamics -1 ASIA: family+minimal+noise
- X33-approach-dynamics -1 LONDON: family+minimal+noise
- X33-approach-dynamics -1 NY: family+minimal+noise
- X33-approach-dynamics -1 POOLED: family+minimal+noise
- X33-approach-dynamics -1 ASIA: family+minimal+noise
- X33-approach-dynamics -1 LONDON: family+minimal+noise
- X33-approach-dynamics -1 NY: family+minimal+noise
- X33-approach-dynamics -1 POOLED: family+minimal+noise
- X33-approach-dynamics -1 ASIA: family+minimal+noise
- X33-approach-dynamics -1 LONDON: family+minimal+noise
- X33-approach-dynamics -1 NY: family+minimal+noise
- X34-level-proximity -1 POOLED: family+minimal+noise; econ not run (holdout stop_vs_target AUC < 0.58)
- X34-level-proximity -1 ASIA: family+minimal+noise
- X34-level-proximity -1 LONDON: family+minimal+noise
- X34-level-proximity -1 NY: family+minimal+noise
- X34-level-proximity -1 POOLED: family+minimal+noise
- X34-level-proximity -1 ASIA: family+minimal+noise
- X34-level-proximity -1 LONDON: family+minimal+noise
- X34-level-proximity -1 NY: family+minimal+noise
- X34-level-proximity -1 POOLED: family+minimal+noise
- X34-level-proximity -1 ASIA: family+minimal+noise
- X34-level-proximity -1 LONDON: family+minimal+noise
- X34-level-proximity -1 NY: family+minimal+noise
- X34-level-proximity -1 POOLED: family+minimal+noise; econ not run (holdout stop_vs_target AUC < 0.58)
- X34-level-proximity -1 ASIA: family+minimal+noise
- X34-level-proximity -1 LONDON: family+minimal+noise
- X34-level-proximity -1 NY: family+minimal+noise
- X34-level-proximity -1 POOLED: family+minimal+noise
- X34-level-proximity -1 ASIA: family+minimal+noise
- X34-level-proximity -1 LONDON: family+minimal+noise
- X34-level-proximity -1 NY: family+minimal+noise
- X34-level-proximity -1 POOLED: family+minimal+noise
- X34-level-proximity -1 ASIA: family+minimal+noise
- X34-level-proximity -1 LONDON: family+minimal+noise
- X34-level-proximity -1 NY: family+minimal+noise
- X35-whipsaw-neighbours -1 POOLED: family+minimal+noise; econ not run (holdout stop_vs_target AUC < 0.58)
- X35-whipsaw-neighbours -1 ASIA: family+minimal+noise
- X35-whipsaw-neighbours -1 LONDON: family+minimal+noise
- X35-whipsaw-neighbours -1 NY: family+minimal+noise
- X35-whipsaw-neighbours -1 POOLED: family+minimal+noise
- X35-whipsaw-neighbours -1 ASIA: family+minimal+noise
- X35-whipsaw-neighbours -1 LONDON: family+minimal+noise
- X35-whipsaw-neighbours -1 NY: family+minimal+noise
- X35-whipsaw-neighbours -1 POOLED: family+minimal+noise
- X35-whipsaw-neighbours -1 ASIA: family+minimal+noise
- X35-whipsaw-neighbours -1 LONDON: family+minimal+noise
- X35-whipsaw-neighbours -1 NY: family+minimal+noise
- X35-whipsaw-neighbours -1 POOLED: family+minimal+noise; econ not run (holdout stop_vs_target AUC < 0.58)
- X35-whipsaw-neighbours -1 ASIA: family+minimal+noise
- X35-whipsaw-neighbours -1 LONDON: family+minimal+noise
- X35-whipsaw-neighbours -1 NY: family+minimal+noise
- X35-whipsaw-neighbours -1 POOLED: family+minimal+noise
- X35-whipsaw-neighbours -1 ASIA: family+minimal+noise
- X35-whipsaw-neighbours -1 LONDON: family+minimal+noise
- X35-whipsaw-neighbours -1 NY: family+minimal+noise
- X35-whipsaw-neighbours -1 POOLED: family+minimal+noise
- X35-whipsaw-neighbours -1 ASIA: family+minimal+noise
- X35-whipsaw-neighbours -1 LONDON: family+minimal+noise
- X35-whipsaw-neighbours -1 NY: family+minimal+noise
