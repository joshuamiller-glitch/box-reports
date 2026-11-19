## COMBO_DRYRUN: exact combined engine (production driver jn05_run2) vs fast scorer A / B

Base lots, p484 net ($4.84 per lot RT). Months 202605-202610 (L6M) only; prior-year months were not run (engine budget). today = TL3_EV_JL3 landed (identical to a fresh run). Stats: ulcer = RMS drawdown of the cumulative daily curve; max DD; worst calendar week; mean $/week.

### L6M: ulcer / max DD / worst week / mean $ per week

| stack | exact engine | scorer A | scorer B | exact vs today (ulcer, mean) |
|---|---|---|---|---|
| TODAY (JL3) | 9416 / -31109 / -15728 / 18755 | | | |
| M1: A7(Asia)<-L5c9e11b3 + K7(NYAM)<-L01811caa | 8807 / -26193 / -11905 / 20805 | 8679 / -26193 / -11905 / 21572 | 9268 / -29495 / -13858 / 20865 | -609 (-6.5%) / +2050 |
| M7: P7(NYAM)<-L01811caa + K7(NYAM)<-L6a25b155 (same session) | 8642 / -30383 / -15322 / 20527 | 8611 / -30383 / -15322 / 20389 | 8379 / -28646 / -15322 / 20312 | -774 (-8.2%) / +1772 |
| M8: A7(Asia)<-Lda55d973 + P7(NYAM)<-L01811caa + K7(NYAM)<-L6a25b155 | 7501 / -23024 / -11753 / 20733 | 7327 / -23024 / -11753 / 21299 | 6937 / -25311 / -12240 / 21350 | -1916 (-20.3%) / +1978 |

### L3M: ulcer / max DD / worst week / mean $ per week

| stack | exact engine | scorer A | scorer B | exact vs today (ulcer, mean) |
|---|---|---|---|---|
| TODAY (JL3) | 11035 / -31109 / -15728 / 16098 | | | |
| M1: A7(Asia)<-L5c9e11b3 + K7(NYAM)<-L01811caa | 9636 / -26193 / -11905 / 21088 | 9523 / -26193 / -11905 / 22168 | 10526 / -29495 / -13858 / 20496 | -1399 (-12.7%) / +4989 |
| M7: P7(NYAM)<-L01811caa + K7(NYAM)<-L6a25b155 (same session) | 9143 / -24519 / -12782 / 18445 | 9134 / -24519 / -12078 / 18232 | 8854 / -23986 / -12782 / 18522 | -1892 (-17.1%) / +2346 |
| M8: A7(Asia)<-Lda55d973 + P7(NYAM)<-L01811caa + K7(NYAM)<-L6a25b155 | 7863 / -23024 / -7622 / 19533 | 7824 / -23024 / -7622 / 20375 | 7198 / -25311 / -5276 / 20458 | -3172 (-28.7%) / +3434 |

### Scorer error (L6M, 3 combined stacks, 6 months each)

| statistic | scorer A abs error mean / max | scorer B abs error mean / max | exact change vs today (mean abs) |
|---|---|---|---|
| ulcer | 111 / 174 | 429 / 564 | 1100 |
| max DD | 0 / 0 | 2442 / 3302 | 4576 |
| worst week | 0 / 0 | 813 / 1953 | 2735 |
| mean $/wk | 491 / 767 | 297 / 617 | 1933 |

Rank correlation (Spearman, only 3 stacks: indicative, not significant): ulcer A 1.00 B 1.00; mean $/wk A 1.00 B 0.50. Order by exact ulcer: ['M8', 'M7', 'M1']; by scorer A: ['M8', 'M7', 'M1'].

| stack | total P&L 6 months: exact / A / B / today |
|---|---|
| M1 | 561734 / 582437 / 563364 / 506392 |
| M7 | 554234 / 550492 / 548437 / 506392 |
| M8 | 559786 / 575076 / 576447 / 506392 |

Daily P&L RMSE vs exact: M1 A 1067 / B 2219, M7 A 501 / B 1125, M8 A 1309 / B 2441 $/day.

Reading: scorer A reproduces max DD and worst week of the exact stacks exactly in these three (the same trades drive them), is off by ~$110 in ulcer (about 10% of the ulcer improvement) and by ~$490/wk in mean (about 25% of the mean improvement; it overstates the mean: its 6-month total is +20.7k / +15.3k above exact for M1 / M8 and -3.7k for M7). Scorer B (slot swap) is clearly worse on drawdown. All three combined stacks beat today's stack on L6M in the exact engine (ulcer 8,807 / 8,642 / 7,501 vs 9,416; mean $/wk 20.8k / 20.5k / 20.7k vs 18.8k) and the exact ranking M8 < M7 < M1 on ulcer equals scorer A's. Caveats: 3 stacks, one 6-month window, the Asia and NY AM streams of the same two or three passers; same-session pair M7 was NOT worse predicted than the cross-session pair M1 (so no evidence yet that same-session interactions break scorer A, but only one same-session stack was tested); prior-year behaviour of the scorer untested.