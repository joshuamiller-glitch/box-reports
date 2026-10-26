# PRED ROUND 21 - block X3 round 3 - X16..X20 conditional-on-entry

Best HOLDOUT F-R AUC: +15 POOLED 0.572 [0.53,0.61] | ASIA 0.524 [0.47,0.58] | LONDON 0.565 [0.47,0.65] | NY 0.554 [0.44,0.64]
Best HOLDOUT F-R AUC: +30 POOLED 0.568 [0.52,0.62] | ASIA 0.569 [0.51,0.63] | LONDON 0.560 [0.48,0.63] | NY 0.606 [0.52,0.69]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 4378ae9cbe58eaece0f0984ce52866356a7f527aced7d57e9786943068107a10 ; trials added 400 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X11.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X19-cond-book | +30 | NY | Q4 | 0.549 [-,-] | 0.606 [0.52,0.69] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | pre | ASIA | Q5 | 0.540 [-,-] | 0.585 [0.51,0.65] | - | - | 0.600 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +5 | NY | Q4 | 0.511 [-,-] | 0.581 [0.48,0.68] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +30 | NY | Q2 | 0.539 [-,-] | 0.578 [0.48,0.69] | - | - | 0.885 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +15 | POOLED | Q2 | 0.546 [-,-] | 0.572 [0.53,0.61] | - | - | 0.729 | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +15 | POOLED | Q1 | 0.537 [-,-] | 0.572 [0.53,0.61] | - | - | 0.727 | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +30 | ASIA | Q5 | 0.538 [-,-] | 0.569 [0.51,0.63] | - | - | 0.595 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +30 | POOLED | Q2 | 0.548 [-,-] | 0.568 [0.52,0.62] | - | - | 0.743 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +15 | LONDON | Q2 | 0.544 [-,-] | 0.565 [0.47,0.65] | - | - | 0.723 | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +15 | LONDON | Q1 | 0.534 [-,-] | 0.565 [0.48,0.64] | - | - | 0.717 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +5 | POOLED | Q2 | 0.533 [-,-] | 0.563 [0.52,0.60] | - | - | 0.720 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +30 | POOLED | Q4 | 0.540 [-,-] | 0.562 [0.52,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +30 | LONDON | Q1 | 0.532 [-,-] | 0.560 [0.48,0.63] | - | - | 0.736 | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +30 | POOLED | Q5 | 0.534 [-,-] | 0.558 [0.51,0.60] | - | - | 0.738 | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +30 | POOLED | Q1 | 0.532 [-,-] | 0.555 [0.51,0.60] | - | - | 0.739 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +15 | NY | Q2 | 0.497 [-,-] | 0.554 [0.44,0.64] | - | - | 0.862 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | pre | NY | Q2 | 0.531 [-,-] | 0.553 [0.45,0.65] | - | - | 0.831 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | pre | POOLED | Q2 | 0.538 [-,-] | 0.552 [0.50,0.60] | - | - | 0.714 | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | pre | POOLED | Q5 | 0.531 [-,-] | 0.552 [0.50,0.60] | - | - | 0.720 | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | pre | ASIA | Q1 | 0.528 [-,-] | 0.551 [0.49,0.62] | - | - | 0.569 | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | pre | POOLED | Q1 | 0.535 [-,-] | 0.549 [0.50,0.59] | - | - | 0.712 | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +5 | POOLED | Q5 | 0.523 [-,-] | 0.548 [0.50,0.59] | - | - | 0.706 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +5 | NY | Q2 | 0.522 [-,-] | 0.545 [0.44,0.65] | - | - | 0.834 | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +5 | POOLED | Q1 | 0.520 [-,-] | 0.543 [0.50,0.58] | - | - | 0.708 | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +5 | NY | Q3 | 0.491 [-,-] | 0.543 [0.44,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +30 | NY | Q5 | 0.495 [-,-] | 0.541 [0.44,0.65] | - | - | 0.872 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +30 | ASIA | Q4 | 0.534 [-,-] | 0.541 [0.47,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +15 | NY | Q4 | 0.504 [-,-] | 0.541 [0.46,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +15 | LONDON | Q5 | 0.537 [-,-] | 0.540 [0.46,0.62] | - | - | 0.711 | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +5 | ASIA | Q1 | 0.516 [-,-] | 0.540 [0.49,0.60] | - | - | 0.555 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +5 | POOLED | Q4 | 0.525 [-,-] | 0.539 [0.49,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +15 | POOLED | Q5 | 0.530 [-,-] | 0.538 [0.49,0.58] | - | - | 0.711 | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | pre | ASIA | Q3 | 0.484 [-,-] | 0.538 [0.46,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +5 | ASIA | Q5 | 0.508 [-,-] | 0.536 [0.48,0.60] | - | - | 0.552 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | pre | POOLED | Q4 | 0.523 [-,-] | 0.535 [0.49,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +5 | NY | Q5 | 0.528 [-,-] | 0.535 [0.44,0.62] | - | - | 0.831 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +5 | ASIA | Q2 | 0.508 [-,-] | 0.534 [0.48,0.60] | - | - | 0.553 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | pre | NY | Q4 | 0.532 [-,-] | 0.534 [0.45,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | pre | ASIA | Q2 | 0.526 [-,-] | 0.529 [0.47,0.59] | - | - | 0.549 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +30 | LONDON | Q2 | 0.515 [-,-] | 0.528 [0.44,0.60] | - | - | 0.727 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +30 | ASIA | Q2 | 0.524 [-,-] | 0.528 [0.47,0.60] | - | - | 0.560 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +15 | POOLED | Q4 | 0.532 [-,-] | 0.528 [0.48,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +15 | NY | Q1 | 0.485 [-,-] | 0.528 [0.43,0.62] | - | - | 0.852 | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +5 | ASIA | Q3 | 0.479 [-,-] | 0.527 [0.47,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +15 | ASIA | Q1 | 0.507 [-,-] | 0.524 [0.47,0.58] | - | - | 0.544 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | pre | ASIA | Q4 | 0.515 [-,-] | 0.522 [0.46,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +5 | LONDON | Q2 | 0.501 [-,-] | 0.521 [0.44,0.60] | - | - | 0.720 | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +15 | NY | Q3 | 0.488 [-,-] | 0.521 [0.43,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | pre | NY | Q1 | 0.521 [-,-] | 0.520 [0.42,0.63] | - | - | 0.829 | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +30 | ASIA | Q1 | 0.506 [-,-] | 0.519 [0.46,0.59] | - | - | 0.549 | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +15 | NY | Q5 | 0.478 [-,-] | 0.512 [0.40,0.62] | - | - | 0.834 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +5 | ASIA | Q4 | 0.512 [-,-] | 0.511 [0.46,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +5 | POOLED | Q3 | 0.469 [-,-] | 0.509 [0.47,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | +15 | ASIA | Q2 | 0.509 [-,-] | 0.508 [0.45,0.57] | - | - | 0.532 | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | pre | NY | Q3 | 0.486 [-,-] | 0.508 [0.43,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +15 | ASIA | Q3 | 0.481 [-,-] | 0.507 [0.45,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +30 | NY | Q1 | 0.493 [-,-] | 0.505 [0.41,0.62] | - | - | 0.876 | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +5 | LONDON | Q3 | 0.476 [-,-] | 0.503 [0.43,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +30 | LONDON | Q5 | 0.500 [-,-] | 0.492 [0.41,0.58] | - | - | 0.699 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +15 | ASIA | Q4 | 0.511 [-,-] | 0.492 [0.44,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +5 | NY | Q1 | 0.472 [-,-] | 0.491 [0.39,0.59] | - | - | 0.826 | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +5 | LONDON | Q5 | 0.482 [-,-] | 0.491 [0.41,0.57] | - | - | 0.689 | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +30 | NY | Q3 | 0.529 [-,-] | 0.490 [0.40,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +30 | LONDON | Q3 | 0.478 [-,-] | 0.489 [0.41,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | +15 | ASIA | Q5 | 0.508 [-,-] | 0.488 [0.43,0.55] | - | - | 0.516 | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +15 | POOLED | Q3 | 0.477 [-,-] | 0.486 [0.44,0.52] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +15 | LONDON | Q3 | 0.499 [-,-] | 0.485 [0.39,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | pre | LONDON | Q5 | 0.495 [-,-] | 0.484 [0.42,0.56] | - | - | 0.709 | - | - | - | - | - | stack | locked label (reference only) |
| X17-cond-x11 | pre | LONDON | Q2 | 0.496 [-,-] | 0.484 [0.40,0.57] | - | - | 0.713 | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +30 | POOLED | Q3 | 0.478 [-,-] | 0.483 [0.45,0.52] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | +30 | ASIA | Q3 | 0.463 [-,-] | 0.482 [0.43,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | pre | POOLED | Q3 | 0.464 [-,-] | 0.477 [0.43,0.52] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | +5 | LONDON | Q1 | 0.473 [-,-] | 0.475 [0.39,0.55] | - | - | 0.696 | - | - | - | - | - | stack | locked label (reference only) |
| X16-cond-lgbm | pre | LONDON | Q1 | 0.491 [-,-] | 0.473 [0.40,0.55] | - | - | 0.702 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +30 | LONDON | Q4 | 0.474 [-,-] | 0.465 [0.37,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X20-cond-top40 | pre | NY | Q5 | 0.489 [-,-] | 0.450 [0.36,0.55] | - | - | 0.817 | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +15 | LONDON | Q4 | 0.506 [-,-] | 0.447 [0.36,0.51] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X18-cond-loss | pre | LONDON | Q3 | 0.467 [-,-] | 0.435 [0.35,0.51] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | +5 | LONDON | Q4 | 0.456 [-,-] | 0.416 [0.33,0.50] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X19-cond-book | pre | LONDON | Q4 | 0.441 [-,-] | 0.415 [0.33,0.50] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- X16-cond-lgbm 0 POOLED: conditional-trained Q1; cond hold 0.549 vs R0 uncond-model-on-S_h 0.490 (bar 0.68); headline=False
- X16-cond-lgbm 0 ASIA: conditional-trained Q1; cond hold 0.551 vs R0 uncond-model-on-S_h 0.532 (bar 0.68); headline=False
- X16-cond-lgbm 0 LONDON: conditional-trained Q1; cond hold 0.473 vs R0 uncond-model-on-S_h 0.522 (bar 0.68); headline=False
- X16-cond-lgbm 0 NY: conditional-trained Q1; cond hold 0.520 vs R0 uncond-model-on-S_h 0.448 (bar 0.68); headline=False
- X16-cond-lgbm 5 POOLED: conditional-trained Q1; cond hold 0.543 vs R0 uncond-model-on-S_h 0.460 (bar 0.68); headline=False
- X16-cond-lgbm 5 ASIA: conditional-trained Q1; cond hold 0.540 vs R0 uncond-model-on-S_h 0.532 (bar 0.68); headline=False
- X16-cond-lgbm 5 LONDON: conditional-trained Q1; cond hold 0.475 vs R0 uncond-model-on-S_h 0.438 (bar 0.68); headline=False
- X16-cond-lgbm 5 NY: conditional-trained Q1; cond hold 0.491 vs R0 uncond-model-on-S_h 0.500 (bar 0.68); headline=False
- X16-cond-lgbm 15 POOLED: conditional-trained Q1; cond hold 0.572 vs R0 uncond-model-on-S_h 0.529 (bar 0.68); headline=False
- X16-cond-lgbm 15 ASIA: conditional-trained Q1; cond hold 0.524 vs R0 uncond-model-on-S_h 0.559 (bar 0.68); headline=False
- X16-cond-lgbm 15 LONDON: conditional-trained Q1; cond hold 0.565 vs R0 uncond-model-on-S_h 0.486 (bar 0.68); headline=False
- X16-cond-lgbm 15 NY: conditional-trained Q1; cond hold 0.528 vs R0 uncond-model-on-S_h 0.520 (bar 0.68); headline=False
- X16-cond-lgbm 30 POOLED: conditional-trained Q1; cond hold 0.555 vs R0 uncond-model-on-S_h 0.541 (bar 0.68); headline=False
- X16-cond-lgbm 30 ASIA: conditional-trained Q1; cond hold 0.519 vs R0 uncond-model-on-S_h 0.528 (bar 0.68); headline=False
- X16-cond-lgbm 30 LONDON: conditional-trained Q1; cond hold 0.560 vs R0 uncond-model-on-S_h 0.546 (bar 0.68); headline=False
- X16-cond-lgbm 30 NY: conditional-trained Q1; cond hold 0.505 vs R0 uncond-model-on-S_h 0.571 (bar 0.68); headline=False
- X17-cond-x11 0 POOLED: conditional-trained Q2; cond hold 0.552 vs R0 uncond-model-on-S_h 0.490 (bar 0.68); headline=True
- X17-cond-x11 0 ASIA: conditional-trained Q2; cond hold 0.529 vs R0 uncond-model-on-S_h 0.532 (bar 0.68); headline=True
- X17-cond-x11 0 LONDON: conditional-trained Q2; cond hold 0.484 vs R0 uncond-model-on-S_h 0.522 (bar 0.68); headline=True
- X17-cond-x11 0 NY: conditional-trained Q2; cond hold 0.553 vs R0 uncond-model-on-S_h 0.448 (bar 0.68); headline=True
- X17-cond-x11 5 POOLED: conditional-trained Q2; cond hold 0.563 vs R0 uncond-model-on-S_h 0.460 (bar 0.68); headline=False
- X17-cond-x11 5 ASIA: conditional-trained Q2; cond hold 0.534 vs R0 uncond-model-on-S_h 0.532 (bar 0.68); headline=False
- X17-cond-x11 5 LONDON: conditional-trained Q2; cond hold 0.521 vs R0 uncond-model-on-S_h 0.438 (bar 0.68); headline=False
- X17-cond-x11 5 NY: conditional-trained Q2; cond hold 0.545 vs R0 uncond-model-on-S_h 0.500 (bar 0.68); headline=False
- X17-cond-x11 15 POOLED: conditional-trained Q2; cond hold 0.572 vs R0 uncond-model-on-S_h 0.529 (bar 0.68); headline=False
- X17-cond-x11 15 ASIA: conditional-trained Q2; cond hold 0.508 vs R0 uncond-model-on-S_h 0.559 (bar 0.68); headline=False
- X17-cond-x11 15 LONDON: conditional-trained Q2; cond hold 0.565 vs R0 uncond-model-on-S_h 0.486 (bar 0.68); headline=False
- X17-cond-x11 15 NY: conditional-trained Q2; cond hold 0.554 vs R0 uncond-model-on-S_h 0.520 (bar 0.68); headline=False
- X17-cond-x11 30 POOLED: conditional-trained Q2; cond hold 0.568 vs R0 uncond-model-on-S_h 0.541 (bar 0.68); headline=True
- X17-cond-x11 30 ASIA: conditional-trained Q2; cond hold 0.528 vs R0 uncond-model-on-S_h 0.528 (bar 0.68); headline=True
- X17-cond-x11 30 LONDON: conditional-trained Q2; cond hold 0.528 vs R0 uncond-model-on-S_h 0.546 (bar 0.68); headline=True
- X17-cond-x11 30 NY: conditional-trained Q2; cond hold 0.578 vs R0 uncond-model-on-S_h 0.571 (bar 0.68); headline=True
- X18-cond-loss 0 POOLED: conditional-trained Q3; cond hold 0.477 vs R0 uncond-model-on-S_h 0.490 (bar 0.68); headline=False
- X18-cond-loss 0 ASIA: conditional-trained Q3; cond hold 0.538 vs R0 uncond-model-on-S_h 0.532 (bar 0.68); headline=False
- X18-cond-loss 0 LONDON: conditional-trained Q3; cond hold 0.435 vs R0 uncond-model-on-S_h 0.522 (bar 0.68); headline=False
- X18-cond-loss 0 NY: conditional-trained Q3; cond hold 0.508 vs R0 uncond-model-on-S_h 0.448 (bar 0.68); headline=False
- X18-cond-loss 5 POOLED: conditional-trained Q3; cond hold 0.509 vs R0 uncond-model-on-S_h 0.460 (bar 0.68); headline=False
- X18-cond-loss 5 ASIA: conditional-trained Q3; cond hold 0.527 vs R0 uncond-model-on-S_h 0.532 (bar 0.68); headline=False
- X18-cond-loss 5 LONDON: conditional-trained Q3; cond hold 0.503 vs R0 uncond-model-on-S_h 0.438 (bar 0.68); headline=False
- X18-cond-loss 5 NY: conditional-trained Q3; cond hold 0.543 vs R0 uncond-model-on-S_h 0.500 (bar 0.68); headline=False
- X18-cond-loss 15 POOLED: conditional-trained Q3; cond hold 0.486 vs R0 uncond-model-on-S_h 0.529 (bar 0.68); headline=False
- X18-cond-loss 15 ASIA: conditional-trained Q3; cond hold 0.507 vs R0 uncond-model-on-S_h 0.559 (bar 0.68); headline=False
- X18-cond-loss 15 LONDON: conditional-trained Q3; cond hold 0.485 vs R0 uncond-model-on-S_h 0.486 (bar 0.68); headline=False
- X18-cond-loss 15 NY: conditional-trained Q3; cond hold 0.521 vs R0 uncond-model-on-S_h 0.520 (bar 0.68); headline=False
- X18-cond-loss 30 POOLED: conditional-trained Q3; cond hold 0.483 vs R0 uncond-model-on-S_h 0.541 (bar 0.68); headline=False
- X18-cond-loss 30 ASIA: conditional-trained Q3; cond hold 0.482 vs R0 uncond-model-on-S_h 0.528 (bar 0.68); headline=False
- X18-cond-loss 30 LONDON: conditional-trained Q3; cond hold 0.489 vs R0 uncond-model-on-S_h 0.546 (bar 0.68); headline=False
- X18-cond-loss 30 NY: conditional-trained Q3; cond hold 0.490 vs R0 uncond-model-on-S_h 0.571 (bar 0.68); headline=False
- X19-cond-book 0 POOLED: conditional-trained Q4; cond hold 0.535 vs R0 uncond-model-on-S_h 0.490 (bar 0.68); headline=False
- X19-cond-book 0 ASIA: conditional-trained Q4; cond hold 0.522 vs R0 uncond-model-on-S_h 0.532 (bar 0.68); headline=False
- X19-cond-book 0 LONDON: conditional-trained Q4; cond hold 0.415 vs R0 uncond-model-on-S_h 0.522 (bar 0.68); headline=False
- X19-cond-book 0 NY: conditional-trained Q4; cond hold 0.534 vs R0 uncond-model-on-S_h 0.448 (bar 0.68); headline=False
- X19-cond-book 5 POOLED: conditional-trained Q4; cond hold 0.539 vs R0 uncond-model-on-S_h 0.460 (bar 0.68); headline=True
- X19-cond-book 5 ASIA: conditional-trained Q4; cond hold 0.511 vs R0 uncond-model-on-S_h 0.532 (bar 0.68); headline=True
- X19-cond-book 5 LONDON: conditional-trained Q4; cond hold 0.416 vs R0 uncond-model-on-S_h 0.438 (bar 0.68); headline=True
- X19-cond-book 5 NY: conditional-trained Q4; cond hold 0.581 vs R0 uncond-model-on-S_h 0.500 (bar 0.68); headline=True
- X19-cond-book 15 POOLED: conditional-trained Q4; cond hold 0.528 vs R0 uncond-model-on-S_h 0.529 (bar 0.68); headline=True
- X19-cond-book 15 ASIA: conditional-trained Q4; cond hold 0.492 vs R0 uncond-model-on-S_h 0.559 (bar 0.68); headline=True
- X19-cond-book 15 LONDON: conditional-trained Q4; cond hold 0.447 vs R0 uncond-model-on-S_h 0.486 (bar 0.68); headline=True
- X19-cond-book 15 NY: conditional-trained Q4; cond hold 0.541 vs R0 uncond-model-on-S_h 0.520 (bar 0.68); headline=True
- X19-cond-book 30 POOLED: conditional-trained Q4; cond hold 0.562 vs R0 uncond-model-on-S_h 0.541 (bar 0.68); headline=False
- X19-cond-book 30 ASIA: conditional-trained Q4; cond hold 0.541 vs R0 uncond-model-on-S_h 0.528 (bar 0.68); headline=False
- X19-cond-book 30 LONDON: conditional-trained Q4; cond hold 0.465 vs R0 uncond-model-on-S_h 0.546 (bar 0.68); headline=False
- X19-cond-book 30 NY: conditional-trained Q4; cond hold 0.606 vs R0 uncond-model-on-S_h 0.571 (bar 0.68); headline=False
- X20-cond-top40 0 POOLED: conditional-trained Q5; cond hold 0.552 vs R0 uncond-model-on-S_h 0.490 (bar 0.68); headline=False
- X20-cond-top40 0 ASIA: conditional-trained Q5; cond hold 0.585 vs R0 uncond-model-on-S_h 0.532 (bar 0.68); headline=False
- X20-cond-top40 0 LONDON: conditional-trained Q5; cond hold 0.484 vs R0 uncond-model-on-S_h 0.522 (bar 0.68); headline=False
- X20-cond-top40 0 NY: conditional-trained Q5; cond hold 0.450 vs R0 uncond-model-on-S_h 0.448 (bar 0.68); headline=False
- X20-cond-top40 5 POOLED: conditional-trained Q5; cond hold 0.548 vs R0 uncond-model-on-S_h 0.460 (bar 0.68); headline=False
- X20-cond-top40 5 ASIA: conditional-trained Q5; cond hold 0.536 vs R0 uncond-model-on-S_h 0.532 (bar 0.68); headline=False
- X20-cond-top40 5 LONDON: conditional-trained Q5; cond hold 0.491 vs R0 uncond-model-on-S_h 0.438 (bar 0.68); headline=False
- X20-cond-top40 5 NY: conditional-trained Q5; cond hold 0.535 vs R0 uncond-model-on-S_h 0.500 (bar 0.68); headline=False
- X20-cond-top40 15 POOLED: conditional-trained Q5; cond hold 0.538 vs R0 uncond-model-on-S_h 0.529 (bar 0.68); headline=False
- X20-cond-top40 15 ASIA: conditional-trained Q5; cond hold 0.488 vs R0 uncond-model-on-S_h 0.559 (bar 0.68); headline=False
- X20-cond-top40 15 LONDON: conditional-trained Q5; cond hold 0.540 vs R0 uncond-model-on-S_h 0.486 (bar 0.68); headline=False
- X20-cond-top40 15 NY: conditional-trained Q5; cond hold 0.512 vs R0 uncond-model-on-S_h 0.520 (bar 0.68); headline=False
- X20-cond-top40 30 POOLED: conditional-trained Q5; cond hold 0.558 vs R0 uncond-model-on-S_h 0.541 (bar 0.68); headline=False
- X20-cond-top40 30 ASIA: conditional-trained Q5; cond hold 0.569 vs R0 uncond-model-on-S_h 0.528 (bar 0.68); headline=False
- X20-cond-top40 30 LONDON: conditional-trained Q5; cond hold 0.492 vs R0 uncond-model-on-S_h 0.546 (bar 0.68); headline=False
- X20-cond-top40 30 NY: conditional-trained Q5; cond hold 0.541 vs R0 uncond-model-on-S_h 0.571 (bar 0.68); headline=False
