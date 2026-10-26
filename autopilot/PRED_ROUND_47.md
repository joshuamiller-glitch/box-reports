# PRED ROUND 47 - block B round 5 - B1015+B10+B11+B12+B13+B14+B15

Best HOLDOUT F-R AUC: +15 POOLED 0.582 [0.53,0.62] | ASIA 0.529 [0.46,0.59] | LONDON 0.610 [0.54,0.68] | NY 0.568 [0.45,0.69]
Best HOLDOUT F-R AUC: +30 POOLED 0.580 [0.54,0.63] | ASIA 0.539 [0.48,0.61] | LONDON 0.615 [0.54,0.69] | NY 0.559 [0.45,0.67]
Best G HOLDOUT AUC: 0.590 [0.57,0.61]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 5436a15b60dd8c70a7c43c47e34b8e822c05f4740c77e6b2660b34cf441b061c ; trials added 1000 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'rounds 1-3 audits 0 mismatches (41280/35200/50560 checks)'} ; holdout scored True ; feature store ['l2vast/pred/store/B10_round5.parquet', 'l2vast/pred/store/B10_round5_sig.parquet', 'l2vast/pred/store/B10_round5_sigu.parquet', 'l2vast/pred/store/B11_round5.parquet', 'l2vast/pred/store/B11_round5_sig.parquet', 'l2vast/pred/store/B11_round5_sigu.parquet', 'l2vast/pred/store/B12_round5.parquet', 'l2vast/pred/store/B12_round5_sig.parquet', 'l2vast/pred/store/B12_round5_sigu.parquet', 'l2vast/pred/store/B13_round5.parquet', 'l2vast/pred/store/B13_round5_sig.parquet', 'l2vast/pred/store/B13_round5_sigu.parquet', 'l2vast/pred/store/B14_round5.parquet', 'l2vast/pred/store/B14_round5_sig.parquet', 'l2vast/pred/store/B14_round5_sigu.parquet', 'l2vast/pred/store/B15_round5.parquet', 'l2vast/pred/store/B15_round5_sig.parquet', 'l2vast/pred/store/B15_round5_sigu.parquet', 'l2vast/pred/store/B16_round8.parquet', 'l2vast/pred/store/B16_round8_sig.parquet', 'l2vast/pred/store/B16_round8_sigu.parquet', 'l2vast/pred/store/B17_round8.parquet', 'l2vast/pred/store/B17_round8_sig.parquet', 'l2vast/pred/store/B17_round8_sigu.parquet', 'l2vast/pred/store/B1_round1.parquet', 'l2vast/pred/store/B1_round1_sig.parquet', 'l2vast/pred/store/B1_round1_sigu.parquet', 'l2vast/pred/store/B2_round1.parquet', 'l2vast/pred/store/B2_round1_sig.parquet', 'l2vast/pred/store/B2_round1_sigu.parquet', 'l2vast/pred/store/B3_round1.parquet', 'l2vast/pred/store/B3_round1_sig.parquet', 'l2vast/pred/store/B3_round1_sigu.parquet', 'l2vast/pred/store/B4_round3.parquet', 'l2vast/pred/store/B4_round3_sig.parquet', 'l2vast/pred/store/B4_round3_sigu.parquet', 'l2vast/pred/store/B5_round2.parquet', 'l2vast/pred/store/B5_round2_sig.parquet', 'l2vast/pred/store/B5_round2_sigu.parquet', 'l2vast/pred/store/B6_round3.parquet', 'l2vast/pred/store/B6_round3_sig.parquet', 'l2vast/pred/store/B6_round3_sigu.parquet', 'l2vast/pred/store/B7_round2.parquet', 'l2vast/pred/store/B7_round2_sig.parquet', 'l2vast/pred/store/B7_round2_sigu.parquet', 'l2vast/pred/store/B9_round3.parquet', 'l2vast/pred/store/B9_round3_sig.parquet', 'l2vast/pred/store/B9_round3_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B1015-cond | +30 | LONDON | rf | 0.569 [0.52,0.62] | 0.615 [0.54,0.69] | - | 0.608 | - | - | - | - | - | - |  | locked label (reference only) |
| B15-cond | +15 | LONDON | stack | 0.511 [0.46,0.57] | 0.610 [0.54,0.68] | - | 0.625 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +10 | POOLED | stack | 0.577 [0.55,0.61] | 0.591 [0.55,0.64] | - | 0.571 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-G | sig | POOLED | logit2 | 0.585 [0.57,0.60] | 0.590 [0.57,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-G | sig | POOLED | logit2 | 0.583 [0.56,0.60] | 0.587 [0.57,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +10 | POOLED | rf | 0.554 [0.53,0.59] | 0.584 [0.53,0.63] | - | 0.565 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +10 | POOLED | stack | 0.579 [0.55,0.61] | 0.584 [0.54,0.63] | - | 0.563 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-G | sig | POOLED | rf | 0.583 [0.56,0.60] | 0.584 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-G | sig | POOLED | logit2 | 0.582 [0.56,0.60] | 0.583 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +10 | POOLED | stack | 0.574 [0.54,0.60] | 0.582 [0.54,0.63] | - | 0.564 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +15 | POOLED | stack | 0.559 [0.53,0.59] | 0.582 [0.53,0.62] | - | 0.565 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +10 | POOLED | stack | 0.571 [0.54,0.60] | 0.582 [0.53,0.63] | - | 0.563 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +15 | POOLED | stack | 0.559 [0.53,0.59] | 0.581 [0.54,0.62] | - | 0.566 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-G | sig | POOLED | logit2 | 0.581 [0.56,0.60] | 0.581 [0.56,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-G | sig | POOLED | logit2 | 0.581 [0.56,0.60] | 0.581 [0.56,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +30 | POOLED | logit2 | 0.542 [0.51,0.57] | 0.580 [0.54,0.63] | - | 0.566 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +15 | LONDON | stack | 0.503 [0.45,0.56] | 0.580 [0.50,0.67] | - | 0.585 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +30 | POOLED | logit2 | 0.538 [0.51,0.57] | 0.579 [0.54,0.62] | - | 0.562 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +10 | POOLED | stack | 0.580 [0.55,0.61] | 0.578 [0.53,0.62] | - | 0.563 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-G | sig | POOLED | logit2 | 0.578 [0.56,0.60] | 0.578 [0.55,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +20 | POOLED | rf | 0.573 [0.54,0.60] | 0.578 [0.53,0.62] | - | 0.561 | - | - | - | - | - | - |  | locked label (reference only) |
| B14-cond | +15 | POOLED | stack | 0.564 [0.53,0.59] | 0.577 [0.53,0.62] | - | 0.561 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +15 | LONDON | stack | 0.501 [0.44,0.56] | 0.577 [0.49,0.66] | - | 0.572 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +15 | POOLED | stack | 0.559 [0.53,0.59] | 0.577 [0.53,0.62] | - | 0.562 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +10 | POOLED | rf | 0.553 [0.52,0.58] | 0.575 [0.53,0.63] | - | 0.556 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +15 | POOLED | stack | 0.555 [0.52,0.58] | 0.575 [0.53,0.62] | - | 0.559 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +30 | POOLED | rf | 0.565 [0.53,0.60] | 0.574 [0.53,0.62] | - | 0.552 | - | - | - | - | - | - |  | locked label (reference only) |
| B10-cond | +15 | POOLED | stack | 0.569 [0.54,0.60] | 0.572 [0.53,0.61] | - | 0.557 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +20 | POOLED | stack | 0.564 [0.53,0.59] | 0.572 [0.53,0.61] | - | 0.561 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +30 | LONDON | logit2 | 0.486 [0.43,0.54] | 0.570 [0.50,0.65] | - | 0.552 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +15 | POOLED | stack | 0.560 [0.53,0.59] | 0.570 [0.52,0.61] | - | 0.552 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +15 | NY | stack | 0.525 [0.46,0.59] | 0.568 [0.45,0.69] | - | 0.544 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +30 | LONDON | gbt3 | 0.548 [0.49,0.60] | 0.566 [0.48,0.64] | - | 0.549 | - | - | - | - | - | - |  | locked label (reference only) |
| B13-cond | +10 | LONDON | rf | 0.522 [0.47,0.57] | 0.566 [0.49,0.64] | - | 0.565 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +30 | LONDON | logit2 | 0.493 [0.43,0.55] | 0.566 [0.49,0.65] | - | 0.542 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +15 | POOLED | stack | 0.543 [0.52,0.57] | 0.562 [0.52,0.60] | - | 0.537 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +30 | POOLED | stack | 0.543 [0.51,0.57] | 0.561 [0.51,0.60] | - | 0.545 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +15 | LONDON | stack | 0.487 [0.43,0.54] | 0.559 [0.47,0.65] | - | 0.558 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +30 | NY | gbt3 | 0.502 [0.42,0.58] | 0.559 [0.45,0.67] | - | 0.554 | - | - | - | - | - | - |  | locked label (reference only) |
| B10-cond | +15 | LONDON | stack | 0.514 [0.46,0.57] | 0.558 [0.47,0.64] | - | 0.567 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +20 | ASIA | rf | 0.561 [0.52,0.60] | 0.558 [0.50,0.63] | - | 0.544 | - | - | - | - | - | - |  | locked label (reference only) |
| B14-cond | +30 | POOLED | stack | 0.544 [0.51,0.57] | 0.558 [0.51,0.60] | - | 0.544 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +10 | POOLED | rf | 0.551 [0.52,0.58] | 0.557 [0.51,0.61] | - | 0.538 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +15 | POOLED | stack | 0.543 [0.51,0.57] | 0.557 [0.52,0.60] | - | 0.527 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +30 | POOLED | rf | 0.536 [0.51,0.56] | 0.556 [0.51,0.60] | - | 0.529 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +30 | POOLED | gbt3 | 0.547 [0.51,0.58] | 0.555 [0.50,0.60] | - | 0.528 | - | - | - | - | - | - |  | locked label (reference only) |
| B13-cond | +15 | NY | stack | 0.512 [0.44,0.58] | 0.554 [0.46,0.66] | - | 0.519 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +10 | ASIA | stack | 0.554 [0.51,0.60] | 0.553 [0.49,0.61] | - | 0.537 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +30 | LONDON | rf | 0.512 [0.46,0.56] | 0.553 [0.48,0.63] | - | 0.548 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +15 | NY | stack | 0.521 [0.46,0.58] | 0.551 [0.45,0.65] | - | 0.553 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +15 | NY | stack | 0.531 [0.46,0.60] | 0.551 [0.45,0.65] | - | 0.538 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +10 | LONDON | rf | 0.504 [0.45,0.56] | 0.550 [0.47,0.63] | - | 0.560 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +10 | LONDON | rf | 0.520 [0.47,0.57] | 0.550 [0.48,0.62] | - | 0.537 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +20 | LONDON | stack | 0.508 [0.45,0.57] | 0.550 [0.47,0.63] | - | 0.559 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +15 | NY | stack | 0.552 [0.49,0.62] | 0.547 [0.45,0.64] | - | 0.537 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +15 | LONDON | stack | 0.486 [0.43,0.54] | 0.546 [0.46,0.62] | - | 0.560 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +10 | ASIA | rf | 0.563 [0.51,0.61] | 0.544 [0.47,0.62] | - | 0.534 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +15 | LONDON | stack | 0.538 [0.49,0.59] | 0.543 [0.47,0.62] | - | 0.536 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +15 | POOLED | stack | 0.533 [0.50,0.56] | 0.542 [0.50,0.59] | - | 0.520 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +15 | POOLED | stack | 0.533 [0.50,0.56] | 0.542 [0.50,0.59] | - | 0.517 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +15 | POOLED | stack | 0.538 [0.51,0.57] | 0.540 [0.50,0.59] | - | 0.522 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +15 | LONDON | stack | 0.543 [0.49,0.59] | 0.540 [0.46,0.61] | - | 0.528 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +30 | ASIA | logit2 | 0.533 [0.49,0.57] | 0.539 [0.48,0.61] | - | 0.513 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +30 | NY | logit2 | 0.529 [0.46,0.59] | 0.538 [0.44,0.63] | - | 0.553 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +10 | POOLED | logit2 | 0.536 [0.51,0.56] | 0.537 [0.50,0.58] | - | 0.523 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +30 | ASIA | logit2 | 0.529 [0.48,0.57] | 0.536 [0.47,0.60] | - | 0.519 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +15 | POOLED | stack | 0.533 [0.50,0.57] | 0.534 [0.49,0.58] | - | 0.507 | - | - | - | - | - | - |  | locked label (reference only) |
| B12-cond | +10 | NY | stack | 0.478 [0.41,0.54] | 0.533 [0.44,0.63] | - | 0.505 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +20 | NY | stack | 0.495 [0.44,0.56] | 0.533 [0.43,0.63] | - | 0.550 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +15 | LONDON | stack | 0.507 [0.45,0.56] | 0.532 [0.46,0.61] | - | 0.546 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +10 | POOLED | logit2 | 0.537 [0.51,0.56] | 0.532 [0.49,0.57] | - | 0.522 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +30 | POOLED | logit2 | 0.527 [0.50,0.56] | 0.531 [0.49,0.57] | - | 0.519 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +15 | ASIA | stack | 0.549 [0.51,0.59] | 0.529 [0.46,0.59] | - | 0.504 | - | - | - | - | - | - |  | locked label (reference only) |
| B10-cond | +30 | ASIA | logit2 | 0.513 [0.46,0.56] | 0.529 [0.47,0.59] | - | 0.514 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +15 | NY | stack | 0.528 [0.46,0.59] | 0.527 [0.42,0.63] | - | 0.512 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +10 | ASIA | logit2 | 0.554 [0.52,0.59] | 0.527 [0.46,0.59] | - | 0.514 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +30 | POOLED | logit2 | 0.525 [0.50,0.55] | 0.526 [0.48,0.57] | - | 0.510 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +10 | ASIA | stack | 0.557 [0.52,0.60] | 0.526 [0.46,0.59] | - | 0.511 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +30 | ASIA | rf | 0.546 [0.50,0.59] | 0.526 [0.47,0.58] | - | 0.503 | - | - | - | - | - | - |  | locked label (reference only) |
| B11-cond | +10 | LONDON | logit2 | 0.511 [0.45,0.57] | 0.525 [0.44,0.61] | - | 0.524 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +30 | ASIA | logit2 | 0.513 [0.47,0.56] | 0.525 [0.47,0.58] | - | 0.516 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +30 | ASIA | stack | 0.533 [0.49,0.57] | 0.525 [0.46,0.59] | - | 0.494 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +10 | LONDON | stack | 0.507 [0.46,0.56] | 0.525 [0.46,0.60] | - | 0.534 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +15 | ASIA | stack | 0.542 [0.50,0.58] | 0.524 [0.47,0.58] | - | 0.513 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +10 | ASIA | rf | 0.557 [0.51,0.61] | 0.523 [0.45,0.60] | - | 0.516 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +30 | POOLED | logit2 | 0.521 [0.49,0.55] | 0.521 [0.48,0.56] | - | 0.507 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +15 | LONDON | stack | 0.524 [0.47,0.58] | 0.521 [0.45,0.59] | - | 0.516 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +30 | NY | logit2 | 0.519 [0.46,0.58] | 0.520 [0.42,0.61] | - | 0.537 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +20 | NY | rf | 0.489 [0.41,0.57] | 0.520 [0.40,0.63] | - | 0.517 | - | - | - | - | - | - |  | locked label (reference only) |
| B14-cond | +30 | ASIA | stack | 0.526 [0.49,0.57] | 0.520 [0.46,0.59] | - | 0.482 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +10 | LONDON | logit2 | 0.511 [0.45,0.57] | 0.518 [0.43,0.60] | - | 0.519 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +10 | ASIA | stack | 0.556 [0.51,0.60] | 0.517 [0.45,0.58] | - | 0.517 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +10 | ASIA | stack | 0.542 [0.50,0.59] | 0.517 [0.44,0.59] | - | 0.505 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +10 | ASIA | logit2 | 0.539 [0.50,0.58] | 0.517 [0.45,0.59] | - | 0.503 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +15 | LONDON | stack | 0.524 [0.47,0.58] | 0.516 [0.44,0.60] | - | 0.498 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +15 | NY | stack | 0.531 [0.46,0.60] | 0.515 [0.39,0.63] | - | 0.491 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +15 | NY | stack | 0.520 [0.45,0.58] | 0.515 [0.41,0.61] | - | 0.493 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +10 | NY | rf | 0.458 [0.39,0.53] | 0.515 [0.42,0.62] | - | 0.511 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +30 | ASIA | stack | 0.523 [0.48,0.56] | 0.514 [0.45,0.58] | - | 0.480 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +30 | ASIA | rf | 0.523 [0.48,0.56] | 0.513 [0.45,0.57] | - | 0.487 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +30 | ASIA | logit2 | 0.506 [0.45,0.55] | 0.513 [0.45,0.58] | - | 0.500 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +15 | ASIA | stack | 0.535 [0.49,0.58] | 0.512 [0.45,0.57] | - | 0.484 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +30 | NY | stack | 0.476 [0.41,0.55] | 0.511 [0.44,0.59] | - | 0.499 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +15 | ASIA | stack | 0.530 [0.49,0.57] | 0.509 [0.45,0.57] | - | 0.488 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +15 | ASIA | stack | 0.528 [0.48,0.57] | 0.509 [0.45,0.58] | - | 0.485 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +20 | LONDON | rf | 0.540 [0.48,0.60] | 0.507 [0.43,0.59] | - | 0.499 | - | - | - | - | - | - |  | locked label (reference only) |
| B1015-G | sig | POOLED | logit2 | 0.511 [0.49,0.53] | 0.507 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +10 | ASIA | rf | 0.552 [0.50,0.60] | 0.506 [0.44,0.57] | - | 0.499 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +10 | LONDON | stack | 0.490 [0.44,0.54] | 0.506 [0.44,0.58] | - | 0.526 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +30 | POOLED | stack | 0.510 [0.48,0.54] | 0.505 [0.46,0.55] | - | 0.471 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +10 | ASIA | stack | 0.535 [0.49,0.58] | 0.505 [0.44,0.57] | - | 0.496 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +30 | LONDON | stack | 0.525 [0.47,0.58] | 0.504 [0.43,0.58] | - | 0.476 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +15 | LONDON | stack | 0.524 [0.47,0.58] | 0.504 [0.43,0.59] | - | 0.504 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +15 | NY | stack | 0.518 [0.45,0.58] | 0.504 [0.40,0.61] | - | 0.505 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +15 | ASIA | stack | 0.527 [0.49,0.57] | 0.503 [0.44,0.57] | - | 0.478 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +30 | POOLED | stack | 0.509 [0.48,0.54] | 0.503 [0.46,0.55] | - | 0.467 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +30 | LONDON | logit2 | 0.509 [0.45,0.56] | 0.502 [0.41,0.59] | - | 0.499 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +30 | POOLED | stack | 0.506 [0.48,0.54] | 0.502 [0.46,0.55] | - | 0.467 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +15 | ASIA | stack | 0.512 [0.47,0.55] | 0.502 [0.44,0.56] | - | 0.485 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +15 | ASIA | stack | 0.502 [0.46,0.54] | 0.501 [0.43,0.56] | - | 0.482 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +30 | LONDON | logit2 | 0.516 [0.46,0.57] | 0.499 [0.41,0.59] | - | 0.496 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +30 | NY | rf | 0.490 [0.42,0.56] | 0.499 [0.41,0.59] | - | 0.496 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +15 | ASIA | stack | 0.500 [0.46,0.55] | 0.498 [0.43,0.56] | - | 0.478 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +15 | NY | stack | 0.529 [0.46,0.59] | 0.498 [0.39,0.61] | - | 0.472 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +10 | NY | stack | 0.490 [0.43,0.55] | 0.497 [0.40,0.60] | - | 0.472 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +10 | LONDON | stack | 0.493 [0.45,0.54] | 0.497 [0.43,0.57] | - | 0.493 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +30 | ASIA | stack | 0.522 [0.48,0.56] | 0.497 [0.43,0.56] | - | 0.472 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +10 | LONDON | stack | 0.498 [0.45,0.55] | 0.496 [0.43,0.57] | - | 0.496 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +10 | NY | stack | 0.475 [0.41,0.54] | 0.495 [0.41,0.58] | - | 0.478 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +30 | ASIA | gbt3 | 0.531 [0.49,0.57] | 0.494 [0.44,0.56] | - | 0.465 | - | - | - | - | - | - |  | locked label (reference only) |
| B10-cond | +15 | ASIA | stack | 0.518 [0.48,0.56] | 0.494 [0.43,0.55] | - | 0.486 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +10 | LONDON | stack | 0.504 [0.45,0.55] | 0.492 [0.41,0.57] | - | 0.505 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +10 | NY | rf | 0.452 [0.38,0.53] | 0.492 [0.39,0.59] | - | 0.479 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +30 | ASIA | stack | 0.529 [0.49,0.57] | 0.492 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +15 | ASIA | stack | 0.511 [0.47,0.55] | 0.492 [0.43,0.55] | - | 0.471 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +15 | ASIA | stack | 0.498 [0.46,0.54] | 0.490 [0.43,0.54] | - | 0.474 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +30 | NY | rf | 0.493 [0.42,0.57] | 0.490 [0.41,0.58] | - | 0.491 | - | - | - | - | - | - |  | locked label (reference only) |
| B11-cond | +20 | ASIA | stack | 0.512 [0.47,0.55] | 0.488 [0.42,0.55] | - | 0.471 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +30 | LONDON | stack | 0.482 [0.43,0.54] | 0.487 [0.41,0.56] | - | 0.483 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +30 | LONDON | stack | 0.514 [0.46,0.57] | 0.487 [0.41,0.57] | - | 0.458 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +15 | NY | stack | 0.476 [0.41,0.54] | 0.486 [0.37,0.59] | - | 0.491 | - | - | - | - | - | - |  | locked label (reference only) |
| B15-cond | +10 | NY | stack | 0.500 [0.44,0.56] | 0.485 [0.39,0.58] | - | 0.475 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +10 | NY | stack | 0.478 [0.41,0.54] | 0.481 [0.39,0.57] | - | 0.459 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +30 | LONDON | stack | 0.474 [0.42,0.53] | 0.479 [0.40,0.55] | - | 0.472 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +30 | LONDON | logit2 | 0.506 [0.45,0.56] | 0.476 [0.39,0.56] | - | 0.476 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +15 | NY | stack | 0.520 [0.45,0.59] | 0.476 [0.37,0.59] | - | 0.465 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +30 | LONDON | stack | 0.507 [0.45,0.57] | 0.474 [0.39,0.56] | - | 0.438 | - | - | - | - | - | - | stack | locked label (reference only) |
| B11-cond | +10 | NY | logit2 | 0.456 [0.39,0.53] | 0.472 [0.38,0.57] | - | 0.466 | - | - | - | - | - | - | stack | locked label (reference only) |
| B12-cond | +15 | ASIA | stack | 0.490 [0.45,0.53] | 0.459 [0.40,0.51] | - | 0.438 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +30 | NY | logit2 | 0.485 [0.42,0.56] | 0.457 [0.37,0.54] | - | 0.473 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1015-cond | +15 | LONDON | stack | 0.473 [0.41,0.53] | 0.457 [0.38,0.54] | - | 0.469 | - | - | - | - | - | - |  | locked label (reference only) |
| B12-cond | +10 | NY | rf | 0.456 [0.39,0.52] | 0.451 [0.36,0.54] | - | 0.460 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +30 | NY | stack | 0.462 [0.40,0.53] | 0.447 [0.36,0.52] | - | 0.454 | - | - | - | - | - | - | stack | locked label (reference only) |
| B10-cond | +30 | NY | logit2 | 0.485 [0.42,0.55] | 0.445 [0.35,0.54] | - | 0.456 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +30 | NY | logit2 | 0.478 [0.41,0.55] | 0.445 [0.35,0.53] | - | 0.450 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +15 | NY | stack | 0.499 [0.44,0.56] | 0.443 [0.33,0.57] | - | 0.420 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +10 | NY | logit2 | 0.443 [0.37,0.51] | 0.434 [0.34,0.54] | - | 0.427 | - | - | - | - | - | - | stack | locked label (reference only) |
| B13-cond | +30 | NY | stack | 0.440 [0.37,0.51] | 0.408 [0.30,0.52] | - | 0.403 | - | - | - | - | - | - | stack | locked label (reference only) |
| B14-cond | +30 | NY | stack | 0.434 [0.36,0.51] | 0.405 [0.30,0.52] | - | 0.406 | - | - | - | - | - | - | stack | locked label (reference only) |
| B15-cond | +30 | NY | stack | 0.445 [0.37,0.52] | 0.398 [0.29,0.51] | - | 0.376 | - | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- B1015-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B1015-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B1015-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B1015-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B1015-cond 20 POOLED: conditional-trained; selected on conditional WF-PRE
- B1015-cond 20 ASIA: conditional-trained; selected on conditional WF-PRE
- B1015-cond 20 LONDON: conditional-trained; selected on conditional WF-PRE
- B1015-cond 20 NY: conditional-trained; selected on conditional WF-PRE
- B1015-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B1015-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B1015-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B1015-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B1015-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B1015-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B1015-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B1015-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B1015-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B1015-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B1015-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B1015-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B10-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B10-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B10-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B10-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B10-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B10-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B10-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B10-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B10-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B10-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B10-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B10-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B10-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B10-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B10-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B10-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B10-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B10-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B10-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B10-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B11-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B11-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B11-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B11-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B11-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B11-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B11-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B11-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B11-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B11-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B11-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B11-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B11-cond 20 POOLED: conditional-trained; selected on conditional WF-PRE
- B11-cond 20 ASIA: conditional-trained; selected on conditional WF-PRE
- B11-cond 20 LONDON: conditional-trained; selected on conditional WF-PRE
- B11-cond 20 NY: conditional-trained; selected on conditional WF-PRE
- B11-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B11-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B11-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B11-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B12-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B12-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B12-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B12-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B12-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B12-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B12-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B12-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B12-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B12-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B12-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B12-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B12-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B12-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B12-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B12-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B12-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B12-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B12-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B12-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B12-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B12-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B12-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B12-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B13-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B13-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B13-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B13-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B13-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B13-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B13-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B13-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B13-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B13-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B13-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B13-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B13-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B13-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B13-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B13-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B13-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B13-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B13-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B13-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B13-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B13-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B13-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B13-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B14-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B14-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B14-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B14-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B14-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B14-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B14-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B14-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B14-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B14-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B14-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B14-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B14-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B14-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B14-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B14-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B14-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B14-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B14-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B14-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B14-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B14-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B14-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B14-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B15-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B15-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B15-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B15-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B15-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B15-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B15-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B15-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B15-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B15-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B15-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B15-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B15-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B15-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B15-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B15-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B15-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B15-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B15-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B15-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B1015-G -1 POOLED: selected on WF-PRE
- B10-G -1 POOLED: selected on WF-PRE
- B11-G -1 POOLED: selected on WF-PRE
- B12-G -1 POOLED: selected on WF-PRE
- B13-G -1 POOLED: selected on WF-PRE
- B14-G -1 POOLED: selected on WF-PRE
- B15-G -1 POOLED: selected on WF-PRE
- B1015-G -1 POOLED: selected on WF-PRE
