# D8_CAN_RESULTS: canonical-print re-runs (CAN / CANQ) beside the stored BASE results (W-D8SPEC)

Window definitions as in all ALN pages: L6M 2026-05..10, L3M 2026-08..10, years 2023/2024/2025 (2025 without Nov). Sets are book-alone on the all-new base (account layers on), 1 lot. $/wk = mean weekly P&L after fees; ulcer = root-mean-square drawdown of cumulative daily P&L; max DD = deepest drawdown; trades = MF1 trades. 'delta' = CAN minus BASE as % of BASE (ulcer and max DD: positive = worse).

## Verdicts

| book | set | verdict | detail |
|---|---|---|---|
| Ldcdb0b6e | CAN | HOLDS | all windows within 15% |
| Ldcdb0b6e | CANQ | BREAKS | Y2023 >30% worse (mean -18%, ulcer +41%) |
| Lfb608c7b | CAN | BREAKS | L6M >30% worse (mean -54%, ulcer +102%) |
| Lfb608c7b | CANQ | BREAKS | L6M >30% worse (mean -37%, ulcer +79%); Y2025 >30% worse (mean -78%, ulcer +73%) |
| L7cc56d99 | CAN | HOLDS | all windows within 15% |
| L7cc56d99 | CANQ | HOLDS | all windows within 15% |
| L488784d8 | CAN | HOLDS | all windows within 15% |
| L488784d8 | CANQ | HOLDS | all windows within 15% |

HOLDS = every window within 15% of BASE on mean and ulcer; CHANGES = some window 15-30% worse; BREAKS = any window mean <= 0 or > 30% worse (the book works only on the old record split).


## Ldcdb0b6e (AS) CAN vs BASE: HOLDS

| window | trades_BASE | trades_new | mean_wk_BASE | mean_wk_new | mean_delta_pct | ulcer_BASE | ulcer_new | ulcer_delta_pct | maxdd_BASE | maxdd_new | maxdd_delta_pct |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 548 | 541 | 2256 | 2292 | 1.6 | 3706 | 3476 | -6.2 | -11884 | -11465 | -3.5 |
| L3M | 229 | 227 | 1470 | 2094 | 42.5 | 4466 | 3648 | -18.3 | -11441 | -10191 | -10.9 |
| Y2023 | 219 | 221 | 380 | 407 | 6.9 | 2764 | 2784 | 0.7 | -6300 | -6300 | 0.0 |
| Y2024 | 391 | 391 | 628 | 653 | 4.0 | 4487 | 4631 | 3.2 | -12697 | -13546 | 6.7 |
| Y2025 | 509 | 509 | 391 | 381 | -2.6 | 10407 | 10335 | -0.7 | -21690 | -21096 | -2.7 |

## Ldcdb0b6e (AS) CANQ vs BASE: BREAKS

| window | trades_BASE | trades_new | mean_wk_BASE | mean_wk_new | mean_delta_pct | ulcer_BASE | ulcer_new | ulcer_delta_pct | maxdd_BASE | maxdd_new | maxdd_delta_pct |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 548 | 549 | 2256 | 1808 | -19.8 | 3706 | 4705 | 26.9 | -11884 | -15049 | 26.6 |
| L3M | 229 | 227 | 1470 | 1459 | -0.7 | 4466 | 5213 | 16.7 | -11441 | -13561 | 18.5 |
| Y2023 | 219 | 221 | 380 | 314 | -17.5 | 2764 | 3883 | 40.5 | -6300 | -8619 | 36.8 |
| Y2024 | 391 | 385 | 628 | 774 | 23.2 | 4487 | 2343 | -47.8 | -12697 | -6773 | -46.7 |
| Y2025 | 509 | 494 | 391 | 280 | -28.4 | 10407 | 10575 | 1.6 | -21690 | -20970 | -3.3 |

## Lfb608c7b (AS) CAN vs BASE: BREAKS

| window | trades_BASE | trades_new | mean_wk_BASE | mean_wk_new | mean_delta_pct | ulcer_BASE | ulcer_new | ulcer_delta_pct | maxdd_BASE | maxdd_new | maxdd_delta_pct |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 763 | 766 | 1979 | 903 | -54.3 | 5119 | 10321 | 101.6 | -14179 | -19261 | 35.8 |
| L3M | 301 | 295 | 2139 | 2740 | 28.1 | 6305 | 4753 | -24.6 | -14179 | -12149 | -14.3 |
| Y2023 | 244 | 244 | 121 | 128 | 5.7 | 5100 | 4821 | -5.5 | -11222 | -10742 | -4.3 |
| Y2024 | 494 | 489 | 212 | 255 | 20.3 | 6875 | 6455 | -6.1 | -19297 | -18633 | -3.4 |
| Y2025 | 695 | 701 | 711 | 740 | 4.0 | 4987 | 4153 | -16.7 | -15359 | -11449 | -25.5 |

## Lfb608c7b (AS) CANQ vs BASE: BREAKS

| window | trades_BASE | trades_new | mean_wk_BASE | mean_wk_new | mean_delta_pct | ulcer_BASE | ulcer_new | ulcer_delta_pct | maxdd_BASE | maxdd_new | maxdd_delta_pct |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 763 | 776 | 1979 | 1239 | -37.4 | 5119 | 9163 | 79.0 | -14179 | -20053 | 41.4 |
| L3M | 301 | 293 | 2139 | 2341 | 9.4 | 6305 | 5453 | -13.5 | -14179 | -13391 | -5.6 |
| Y2023 | 244 | 242 | 121 | 248 | 104.2 | 5100 | 3292 | -35.5 | -11222 | -8149 | -27.4 |
| Y2024 | 494 | 497 | 212 | 407 | 92.1 | 6875 | 7942 | 15.5 | -19297 | -20095 | 4.1 |
| Y2025 | 695 | 712 | 711 | 157 | -78.0 | 4987 | 8623 | 72.9 | -15359 | -21095 | 37.3 |

## L7cc56d99 (NY) CAN vs BASE: HOLDS

| window | trades_BASE | trades_new | mean_wk_BASE | mean_wk_new | mean_delta_pct | ulcer_BASE | ulcer_new | ulcer_delta_pct | maxdd_BASE | maxdd_new | maxdd_delta_pct |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 271 | 271 | 2405 | 2405 | 0.0 | 4790 | 4790 | 0.0 | -13326 | -13326 | 0.0 |
| L3M | 110 | 110 | 2166 | 2166 | 0.0 | 4719 | 4719 | 0.0 | -11089 | -11089 | 0.0 |
| Y2023 | 208 | 208 | 1066 | 1066 | 0.0 | 3889 | 3889 | 0.0 | -11074 | -11074 | 0.0 |
| Y2024 | 341 | 341 | 320 | 320 | 0.0 | 9284 | 9284 | 0.0 | -17987 | -17987 | 0.0 |
| Y2025 | 379 | 379 | 872 | 872 | 0.0 | 10265 | 10265 | 0.0 | -31363 | -31363 | 0.0 |

## L7cc56d99 (NY) CANQ vs BASE: HOLDS

| window | trades_BASE | trades_new | mean_wk_BASE | mean_wk_new | mean_delta_pct | ulcer_BASE | ulcer_new | ulcer_delta_pct | maxdd_BASE | maxdd_new | maxdd_delta_pct |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 271 | 271 | 2405 | 2405 | 0.0 | 4790 | 4790 | 0.0 | -13326 | -13326 | 0.0 |
| L3M | 110 | 110 | 2166 | 2166 | 0.0 | 4719 | 4719 | 0.0 | -11089 | -11089 | 0.0 |
| Y2023 | 208 | 208 | 1066 | 1066 | 0.0 | 3889 | 3889 | 0.0 | -11074 | -11074 | 0.0 |
| Y2024 | 341 | 341 | 320 | 320 | 0.0 | 9284 | 9284 | 0.0 | -17987 | -17987 | 0.0 |
| Y2025 | 379 | 379 | 872 | 872 | 0.0 | 10265 | 10265 | 0.0 | -31363 | -31363 | 0.0 |

## L488784d8 (NY) CAN vs BASE: HOLDS

| window | trades_BASE | trades_new | mean_wk_BASE | mean_wk_new | mean_delta_pct | ulcer_BASE | ulcer_new | ulcer_delta_pct | maxdd_BASE | maxdd_new | maxdd_delta_pct |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 176 | 178 | 961 | 976 | 1.5 | 2839 | 2812 | -0.9 | -7243 | -7243 | 0.0 |
| L3M | 74 | 75 | 538 | 660 | 22.6 | 3024 | 2901 | -4.1 | -6311 | -6311 | 0.0 |
| Y2023 | 202 | 204 | 396 | 486 | 22.5 | 4911 | 4521 | -7.9 | -13517 | -13517 | 0.0 |
| Y2024 | 339 | 338 | 352 | 386 | 9.6 | 6084 | 5245 | -13.8 | -13494 | -11839 | -12.3 |
| Y2025 | 348 | 347 | 708 | 713 | 0.7 | 11039 | 10643 | -3.6 | -22356 | -20901 | -6.5 |

## L488784d8 (NY) CANQ vs BASE: HOLDS

| window | trades_BASE | trades_new | mean_wk_BASE | mean_wk_new | mean_delta_pct | ulcer_BASE | ulcer_new | ulcer_delta_pct | maxdd_BASE | maxdd_new | maxdd_delta_pct |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | 176 | 176 | 961 | 961 | 0.0 | 2839 | 2839 | 0.0 | -7243 | -7243 | 0.0 |
| L3M | 74 | 74 | 538 | 538 | 0.0 | 3024 | 3024 | 0.0 | -6311 | -6311 | 0.0 |
| Y2023 | 202 | 202 | 396 | 396 | 0.0 | 4911 | 4911 | 0.0 | -13517 | -13517 | 0.0 |
| Y2024 | 339 | 339 | 352 | 352 | 0.0 | 6084 | 6084 | 0.0 | -13494 | -13494 | 0.0 |
| Y2025 | 348 | 348 | 708 | 708 | 0.0 | 11039 | 11039 | 0.0 | -22356 | -22356 | 0.0 |
