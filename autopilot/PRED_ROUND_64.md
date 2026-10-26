# PRED ROUND 64 - block B round 15 - B16+B17+B24

Best HOLDOUT F-R AUC: +15 POOLED 0.537 [0.50,0.57] | ASIA 0.578 [0.52,0.64] | LONDON 0.552 [0.49,0.61] | NY 0.490 [0.42,0.56]
Best HOLDOUT F-R AUC: +30 POOLED 0.522 [0.49,0.55] | ASIA 0.540 [0.49,0.60] | LONDON 0.515 [0.46,0.57] | NY 0.512 [0.45,0.57]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.082 AUC, 5 of 5 economic conditions short.
not found - short by 0.082 AUC and 5 of 5 economic conditions

prereg 5436a15b60dd8c70a7c43c47e34b8e822c05f4740c77e6b2660b34cf441b061c ; trials added 1000 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'rounds 1-3 audits 0 mismatches (41280/35200/50560 checks)'} ; holdout scored True ; feature store ['l2vast/pred/store/B10_round5.parquet', 'l2vast/pred/store/B10_round5_sig.parquet', 'l2vast/pred/store/B10_round5_sigu.parquet', 'l2vast/pred/store/B11_round5.parquet', 'l2vast/pred/store/B11_round5_sig.parquet', 'l2vast/pred/store/B11_round5_sigu.parquet', 'l2vast/pred/store/B12_round5.parquet', 'l2vast/pred/store/B12_round5_sig.parquet', 'l2vast/pred/store/B12_round5_sigu.parquet', 'l2vast/pred/store/B13_round5.parquet', 'l2vast/pred/store/B13_round5_sig.parquet', 'l2vast/pred/store/B13_round5_sigu.parquet', 'l2vast/pred/store/B14_round5.parquet', 'l2vast/pred/store/B14_round5_sig.parquet', 'l2vast/pred/store/B14_round5_sigu.parquet', 'l2vast/pred/store/B15_round5.parquet', 'l2vast/pred/store/B15_round5_sig.parquet', 'l2vast/pred/store/B15_round5_sigu.parquet', 'l2vast/pred/store/B16_round8.parquet', 'l2vast/pred/store/B16_round8_sig.parquet', 'l2vast/pred/store/B16_round8_sigu.parquet', 'l2vast/pred/store/B17_round8.parquet', 'l2vast/pred/store/B17_round8_sig.parquet', 'l2vast/pred/store/B17_round8_sigu.parquet', 'l2vast/pred/store/B18_round9_sig.parquet', 'l2vast/pred/store/B18_round9_sigu.parquet', 'l2vast/pred/store/B19_round9_sig.parquet', 'l2vast/pred/store/B19_round9_sigu.parquet', 'l2vast/pred/store/B1_round1.parquet', 'l2vast/pred/store/B1_round1_sig.parquet', 'l2vast/pred/store/B1_round1_sigu.parquet', 'l2vast/pred/store/B20_round12_sigu.parquet', 'l2vast/pred/store/B21_round12_sigu.parquet', 'l2vast/pred/store/B22_round13_sigu.parquet', 'l2vast/pred/store/B23_round13_sigu.parquet', 'l2vast/pred/store/B24_round13.parquet', 'l2vast/pred/store/B24_round13_sigu.parquet', 'l2vast/pred/store/B25_round13_sigu.parquet', 'l2vast/pred/store/B26_round16_sigu.parquet', 'l2vast/pred/store/B27_round16_sigu.parquet', 'l2vast/pred/store/B28_round16_sigu.parquet', 'l2vast/pred/store/B2_round1.parquet', 'l2vast/pred/store/B2_round1_sig.parquet', 'l2vast/pred/store/B2_round1_sigu.parquet', 'l2vast/pred/store/B3_round1.parquet', 'l2vast/pred/store/B3_round1_sig.parquet', 'l2vast/pred/store/B3_round1_sigu.parquet', 'l2vast/pred/store/B4_round3.parquet', 'l2vast/pred/store/B4_round3_sig.parquet', 'l2vast/pred/store/B4_round3_sigu.parquet', 'l2vast/pred/store/B5_round2.parquet', 'l2vast/pred/store/B5_round2_sig.parquet', 'l2vast/pred/store/B5_round2_sigu.parquet', 'l2vast/pred/store/B6_round3.parquet', 'l2vast/pred/store/B6_round3_sig.parquet', 'l2vast/pred/store/B6_round3_sigu.parquet', 'l2vast/pred/store/B7_round2.parquet', 'l2vast/pred/store/B7_round2_sig.parquet', 'l2vast/pred/store/B7_round2_sigu.parquet', 'l2vast/pred/store/B9_round3.parquet', 'l2vast/pred/store/B9_round3_sig.parquet', 'l2vast/pred/store/B9_round3_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B16-cond | +15 | ASIA | logit2 | 0.561 [0.52,0.61] | 0.578 [0.52,0.64] | - | 0.581 | - | - | - | - | - | - | stack | short by 0.082 AUC, 5 of 5 econ |
| B16-cond | +15 | LONDON | logit2 | 0.498 [0.45,0.54] | 0.552 [0.49,0.61] | - | 0.545 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B24-cond | +10 | LONDON | stack | 0.563 [0.52,0.60] | 0.543 [0.49,0.59] | - | 0.543 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +30 | ASIA | logit2 | 0.538 [0.50,0.58] | 0.540 [0.49,0.60] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| B16-cond | +15 | POOLED | logit2 | 0.520 [0.50,0.55] | 0.537 [0.50,0.57] | - | 0.538 | - | - | - | - | - | - | stack | promising: short by 0.143 AUC, 5 of 5 econ |
| B17-cond | +20 | ASIA | stack | 0.544 [0.51,0.58] | 0.528 [0.48,0.58] | - | 0.513 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B16-cond | +15 | ASIA | stack | 0.550 [0.51,0.59] | 0.527 [0.47,0.59] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.133 AUC, 5 of 5 econ |
| B17-cond | +10 | LONDON | gbt3 | 0.553 [0.51,0.60] | 0.525 [0.46,0.59] | - | 0.537 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B16-cond | +30 | ASIA | logit2 | 0.530 [0.49,0.57] | 0.525 [0.46,0.59] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| B16-cond | +10 | ASIA | logit2 | 0.547 [0.50,0.59] | 0.523 [0.46,0.58] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| B17-cond | +30 | POOLED | logit2 | 0.511 [0.49,0.53] | 0.522 [0.49,0.55] | - | 0.519 | - | - | - | - | - | - | stack | promising: short by 0.158 AUC, 5 of 5 econ |
| B16-cond | +15 | LONDON | stack | 0.523 [0.48,0.57] | 0.521 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B24-cond | +30 | ASIA | logit2 | 0.532 [0.49,0.57] | 0.518 [0.46,0.58] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.142 AUC, 5 of 5 econ |
| B24-cond | +10 | POOLED | stack | 0.530 [0.51,0.55] | 0.515 [0.48,0.55] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| B17-cond | +30 | LONDON | logit2 | 0.482 [0.44,0.53] | 0.515 [0.46,0.57] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +30 | NY | logit2 | 0.516 [0.48,0.56] | 0.512 [0.45,0.57] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B16-cond | +10 | POOLED | logit2 | 0.514 [0.49,0.54] | 0.512 [0.48,0.54] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| B24-cond | +10 | ASIA | stack | 0.529 [0.49,0.56] | 0.509 [0.45,0.57] | - | 0.495 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B16-cond | +10 | NY | logit2 | 0.507 [0.47,0.55] | 0.506 [0.45,0.57] | - | 0.508 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +15 | ASIA | stack | 0.522 [0.48,0.56] | 0.505 [0.45,0.56] | - | 0.492 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| B16-cond | +10 | LONDON | logit2 | 0.490 [0.44,0.54] | 0.504 [0.44,0.58] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +10 | ASIA | gbt3 | 0.519 [0.48,0.56] | 0.504 [0.45,0.56] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B16-cond | +15 | POOLED | stack | 0.521 [0.49,0.55] | 0.504 [0.47,0.54] | - | 0.500 | - | - | - | - | - | - | stack | short by 0.176 AUC, 5 of 5 econ |
| B24-cond | +20 | ASIA | stack | 0.548 [0.51,0.58] | 0.503 [0.45,0.56] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B24-cond | +30 | POOLED | logit2 | 0.496 [0.47,0.52] | 0.498 [0.47,0.53] | - | 0.495 | - | - | - | - | - | - | stack | short by 0.182 AUC, 5 of 5 econ |
| B16-cond | +30 | POOLED | logit2 | 0.497 [0.47,0.52] | 0.497 [0.46,0.53] | - | 0.492 | - | - | - | - | - | - | stack | short by 0.183 AUC, 5 of 5 econ |
| B24-cond | +20 | POOLED | stack | 0.517 [0.49,0.54] | 0.496 [0.46,0.53] | - | 0.490 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B24-cond | +20 | LONDON | stack | 0.480 [0.43,0.53] | 0.496 [0.44,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B24-cond | +20 | NY | stack | 0.523 [0.48,0.57] | 0.493 [0.43,0.56] | - | 0.496 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +20 | POOLED | stack | 0.508 [0.48,0.53] | 0.493 [0.45,0.53] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B17-cond | +10 | POOLED | gbt3 | 0.516 [0.49,0.54] | 0.493 [0.46,0.52] | - | 0.491 | - | - | - | - | - | - |  | short by 0.187 AUC, 5 of 5 econ |
| B16-cond | +15 | NY | logit2 | 0.502 [0.46,0.55] | 0.490 [0.42,0.56] | - | 0.494 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +20 | LONDON | stack | 0.483 [0.44,0.53] | 0.490 [0.42,0.55] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B24-cond | +30 | NY | logit2 | 0.489 [0.44,0.54] | 0.489 [0.43,0.55] | - | 0.488 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B24-cond | +30 | LONDON | logit2 | 0.469 [0.43,0.51] | 0.485 [0.43,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B16-cond | +30 | LONDON | logit2 | 0.472 [0.43,0.51] | 0.484 [0.43,0.53] | - | 0.477 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B16-cond | +30 | NY | logit2 | 0.487 [0.44,0.53] | 0.481 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B24-cond | +30 | ASIA | stack | 0.502 [0.46,0.54] | 0.470 [0.41,0.53] | - | 0.456 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B17-cond | +15 | LONDON | stack | 0.506 [0.47,0.55] | 0.468 [0.40,0.53] | - | 0.469 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B24-cond | +10 | NY | stack | 0.492 [0.45,0.54] | 0.467 [0.40,0.53] | - | 0.473 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +15 | POOLED | stack | 0.507 [0.49,0.53] | 0.465 [0.43,0.50] | - | 0.462 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B24-cond | +15 | ASIA | stack | 0.518 [0.48,0.55] | 0.464 [0.40,0.52] | - | 0.451 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B16-cond | +30 | LONDON | stack | 0.508 [0.46,0.55] | 0.462 [0.40,0.53] | - | 0.466 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +30 | ASIA | stack | 0.513 [0.47,0.56] | 0.459 [0.40,0.53] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B17-cond | +20 | NY | stack | 0.496 [0.45,0.54] | 0.459 [0.39,0.53] | - | 0.458 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +30 | LONDON | stack | 0.489 [0.44,0.54] | 0.458 [0.40,0.53] | - | 0.455 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +10 | NY | gbt3 | 0.478 [0.44,0.52] | 0.457 [0.40,0.52] | - | 0.470 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B16-cond | +30 | ASIA | stack | 0.503 [0.46,0.54] | 0.453 [0.40,0.52] | - | 0.456 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B24-cond | +15 | POOLED | stack | 0.502 [0.48,0.53] | 0.450 [0.41,0.49] | - | 0.442 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B24-cond | +15 | NY | stack | 0.500 [0.45,0.55] | 0.449 [0.38,0.53] | - | 0.458 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +30 | POOLED | stack | 0.494 [0.47,0.52] | 0.448 [0.41,0.49] | - | 0.445 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B16-cond | +30 | POOLED | stack | 0.500 [0.48,0.52] | 0.445 [0.41,0.48] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B24-cond | +15 | LONDON | stack | 0.489 [0.45,0.54] | 0.442 [0.38,0.50] | - | 0.426 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B24-cond | +30 | LONDON | stack | 0.493 [0.45,0.54] | 0.441 [0.38,0.50] | - | 0.446 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B24-cond | +30 | POOLED | stack | 0.486 [0.46,0.51] | 0.437 [0.40,0.48] | - | 0.435 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B16-cond | +15 | NY | stack | 0.482 [0.44,0.52] | 0.435 [0.38,0.49] | - | 0.440 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B16-cond | +30 | NY | stack | 0.492 [0.44,0.54] | 0.415 [0.36,0.48] | - | 0.424 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +30 | NY | stack | 0.479 [0.43,0.52] | 0.414 [0.36,0.47] | - | 0.419 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B17-cond | +15 | NY | stack | 0.483 [0.44,0.53] | 0.410 [0.35,0.47] | - | 0.418 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| B24-cond | +30 | NY | stack | 0.464 [0.42,0.51] | 0.395 [0.32,0.48] | - | 0.403 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |

One-sentence notes:
- B16-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B16-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B16-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B16-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B16-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B16-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B16-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B16-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B16-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B16-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B16-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B16-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B16-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B16-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B16-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B16-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B16-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B16-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B16-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B16-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B17-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B17-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B17-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B17-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B17-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B17-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B17-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B17-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B17-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B17-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B17-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B17-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B17-cond 20 POOLED: conditional-trained; selected on conditional WF-PRE
- B17-cond 20 ASIA: conditional-trained; selected on conditional WF-PRE
- B17-cond 20 LONDON: conditional-trained; selected on conditional WF-PRE
- B17-cond 20 NY: conditional-trained; selected on conditional WF-PRE
- B17-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B17-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B17-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B17-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B24-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B24-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B24-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B24-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B24-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B24-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B24-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B24-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B24-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B24-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B24-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B24-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B24-cond 20 POOLED: conditional-trained; selected on conditional WF-PRE
- B24-cond 20 ASIA: conditional-trained; selected on conditional WF-PRE
- B24-cond 20 LONDON: conditional-trained; selected on conditional WF-PRE
- B24-cond 20 NY: conditional-trained; selected on conditional WF-PRE
- B24-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B24-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B24-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B24-cond 30 NY: conditional-trained; selected on conditional WF-PRE
