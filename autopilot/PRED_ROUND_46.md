# PRED ROUND 46 - block B round 4 - B8

Best HOLDOUT F-R AUC: +15 POOLED 0.573 [0.53,0.61] | ASIA 0.491 [0.42,0.55] | LONDON 0.579 [0.50,0.66] | NY 0.475 [0.39,0.57]
Best HOLDOUT F-R AUC: +30 POOLED 0.564 [0.52,0.61] | ASIA 0.546 [0.48,0.61] | LONDON 0.521 [0.45,0.59] | NY 0.479 [0.36,0.59]
Best G HOLDOUT AUC: 0.584 [0.56,0.61]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 5436a15b60dd8c70a7c43c47e34b8e822c05f4740c77e6b2660b34cf441b061c ; trials added 1000 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'rounds 1-3 audits 0 mismatches (41280/35200/50560 checks)'} ; holdout scored True ; feature store ['l2vast/pred/store/B10_round5.parquet', 'l2vast/pred/store/B10_round5_sig.parquet', 'l2vast/pred/store/B11_round5.parquet', 'l2vast/pred/store/B11_round5_sig.parquet', 'l2vast/pred/store/B12_round5.parquet', 'l2vast/pred/store/B12_round5_sig.parquet', 'l2vast/pred/store/B13_round5.parquet', 'l2vast/pred/store/B13_round5_sig.parquet', 'l2vast/pred/store/B14_round5.parquet', 'l2vast/pred/store/B14_round5_sig.parquet', 'l2vast/pred/store/B15_round5.parquet', 'l2vast/pred/store/B15_round5_sig.parquet', 'l2vast/pred/store/B1_round1.parquet', 'l2vast/pred/store/B1_round1_sig.parquet', 'l2vast/pred/store/B2_round1.parquet', 'l2vast/pred/store/B2_round1_sig.parquet', 'l2vast/pred/store/B3_round1.parquet', 'l2vast/pred/store/B3_round1_sig.parquet', 'l2vast/pred/store/B4_round3.parquet', 'l2vast/pred/store/B4_round3_sig.parquet', 'l2vast/pred/store/B5_round2.parquet', 'l2vast/pred/store/B5_round2_sig.parquet', 'l2vast/pred/store/B6_round3.parquet', 'l2vast/pred/store/B6_round3_sig.parquet', 'l2vast/pred/store/B7_round2.parquet', 'l2vast/pred/store/B7_round2_sig.parquet', 'l2vast/pred/store/B9_round3.parquet', 'l2vast/pred/store/B9_round3_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B8-G | sig | POOLED | logit2 | 0.580 [0.56,0.60] | 0.584 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +15 | LONDON | stack | 0.519 [0.46,0.57] | 0.579 [0.50,0.66] | - | 0.573 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +10 | POOLED | stack | 0.569 [0.54,0.60] | 0.574 [0.53,0.62] | - | 0.557 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +15 | POOLED | stack | 0.559 [0.53,0.59] | 0.573 [0.53,0.61] | - | 0.559 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +15 | LONDON | stack | 0.555 [0.50,0.61] | 0.571 [0.50,0.64] | - | 0.556 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +30 | POOLED | logit2 | 0.537 [0.51,0.57] | 0.564 [0.52,0.61] | - | 0.541 | - | - | - | - | - | - |  | locked label (reference only) |
| B8-cond | +30 | POOLED | stack | 0.541 [0.51,0.57] | 0.558 [0.51,0.60] | - | 0.541 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +30 | ASIA | logit2 | 0.541 [0.50,0.58] | 0.546 [0.48,0.61] | - | 0.527 | - | - | - | - | - | - |  | locked label (reference only) |
| B8-cond | +15 | POOLED | stack | 0.539 [0.51,0.57] | 0.534 [0.49,0.57] | - | 0.503 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +30 | LONDON | logit2 | 0.475 [0.42,0.53] | 0.521 [0.45,0.59] | - | 0.515 | - | - | - | - | - | - |  | locked label (reference only) |
| B8-cond | +10 | ASIA | stack | 0.550 [0.51,0.59] | 0.517 [0.45,0.58] | - | 0.511 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-G | sig | POOLED | rf | 0.509 [0.49,0.53] | 0.513 [0.49,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B8-cond | +30 | ASIA | stack | 0.524 [0.48,0.56] | 0.492 [0.42,0.56] | - | 0.466 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +15 | ASIA | stack | 0.533 [0.49,0.58] | 0.491 [0.42,0.55] | - | 0.464 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +15 | ASIA | stack | 0.511 [0.47,0.55] | 0.486 [0.42,0.54] | - | 0.478 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +30 | NY | logit2 | 0.502 [0.42,0.58] | 0.479 [0.36,0.59] | - | 0.464 | - | - | - | - | - | - |  | locked label (reference only) |
| B8-cond | +10 | LONDON | stack | 0.487 [0.43,0.55] | 0.476 [0.40,0.56] | - | 0.488 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +15 | NY | stack | 0.509 [0.44,0.57] | 0.475 [0.39,0.57] | - | 0.462 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +30 | LONDON | stack | 0.469 [0.42,0.52] | 0.472 [0.39,0.55] | - | 0.463 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +10 | NY | stack | 0.444 [0.39,0.50] | 0.456 [0.36,0.56] | - | 0.441 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +30 | NY | stack | 0.470 [0.40,0.54] | 0.446 [0.36,0.55] | - | 0.436 | - | - | - | - | - | - | stack | locked label (reference only) |
| B8-cond | +15 | NY | stack | 0.458 [0.40,0.52] | 0.424 [0.32,0.52] | - | 0.391 | - | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- B8-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B8-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B8-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B8-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B8-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B8-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B8-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B8-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B8-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B8-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B8-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B8-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B8-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B8-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B8-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B8-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B8-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B8-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B8-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B8-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B8-G -1 POOLED: selected on WF-PRE
- B8-G -1 POOLED: selected on WF-PRE
