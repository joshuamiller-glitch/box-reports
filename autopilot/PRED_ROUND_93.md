# PRED ROUND 93 - block X2 round 4 - X-G-unlocked

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.549 [0.52,0.58]
Gap to FOUND: 0.131 AUC, 5 of 5 economic conditions short.
not found - short by 0.131 AUC and 5 of 5 economic conditions

prereg 8a861763b775585174ab65f372022ac5aa4ed269b521142afb43a01cf51cbde0 ; trials added 2600 ; truncation audit {'decisions': 7200, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X2_X6_sigu.parquet', 'l2vast/pred/store/X2_X10_sigu.parquet', 'l2vast/pred/store/X2_X7_sigu.parquet', 'l2vast/pred/store/X2_X8_sigu.parquet', 'l2vast/pred/store/X2_X9_sigu.parquet', 'l2vast/pred/store/X2_X26_sigu.parquet', 'l2vast/pred/store/X2_X27_sigu.parquet', 'l2vast/pred/store/X2_X28_sigu.parquet', 'l2vast/pred/store/X2_X29_sigu.parquet', 'l2vast/pred/store/X2_X30_sigu.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Xall10-G-unlocked | sig | NY/HM | gbt3 | 0.554 [0.53,0.58] | 0.549 [0.52,0.58] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | NY | logit2 | 0.546 [0.53,0.56] | 0.548 [0.53,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | NY/HM | logit2 | 0.545 [0.52,0.57] | 0.548 [0.52,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | NY/ST | logit2 | 0.546 [0.53,0.57] | 0.547 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | NY | logit2 | 0.548 [0.53,0.57] | 0.547 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | NY | logit2 | 0.546 [0.53,0.56] | 0.547 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | NY/HM | logit2 | 0.546 [0.52,0.57] | 0.547 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | NY | logit2 | 0.546 [0.53,0.56] | 0.547 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | NY/HM | logit2 | 0.548 [0.53,0.57] | 0.547 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | NY/ST | logit2 | 0.549 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | NY/ST | logit2 | 0.547 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | NY | logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | NY | logit2 | 0.548 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | NY/HM | logit2 | 0.546 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | NY | logit2 | 0.545 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | NY/HM | logit2 | 0.545 [0.52,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | NY/HM | logit2 | 0.548 [0.53,0.57] | 0.546 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | NY/ST | logit2 | 0.546 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | NY/ST | logit2 | 0.546 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | NY/ST | logit2 | 0.545 [0.53,0.56] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | NY/ST | logit2 | 0.548 [0.53,0.57] | 0.546 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | NY | logit2 | 0.544 [0.53,0.56] | 0.545 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | NY/HM | logit2 | 0.545 [0.52,0.57] | 0.545 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | NY/HM | stack | 0.542 [0.52,0.56] | 0.545 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | NY | logit2 | 0.545 [0.53,0.56] | 0.544 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | NY/HM | rf | 0.546 [0.52,0.57] | 0.542 [0.51,0.58] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | NY | logit2 | 0.544 [0.53,0.56] | 0.542 [0.52,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | NY/ST | logit2 | 0.544 [0.52,0.56] | 0.541 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | NY/ST | logit2 | 0.543 [0.52,0.56] | 0.541 [0.52,0.57] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | NY/ST | logit2 | 0.544 [0.52,0.56] | 0.541 [0.52,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | NY/HM | logit2 | 0.543 [0.52,0.56] | 0.541 [0.51,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | NY/ST | logit2 | 0.543 [0.52,0.56] | 0.538 [0.51,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | NY | logit2 | 0.543 [0.53,0.56] | 0.538 [0.52,0.56] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | NY/ST | stack | 0.539 [0.52,0.56] | 0.535 [0.51,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | NY/ST | logit2 | 0.542 [0.52,0.56] | 0.534 [0.51,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | NY | logit2 | 0.544 [0.53,0.56] | 0.534 [0.51,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | ASIA/ST | stack | 0.522 [0.49,0.55] | 0.533 [0.50,0.57] | - | - | - | N | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X9-G-unlocked | sig | NY | logit2 | 0.543 [0.53,0.56] | 0.532 [0.51,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | LONDON/HM | logit2 | 0.516 [0.49,0.55] | 0.530 [0.49,0.58] | - | - | - | N | - | - | - | - | stack | short by 0.150 AUC, 5 of 5 econ |
| X6-G-unlocked | sig | ASIA/ST | gbt3 | 0.511 [0.48,0.54] | 0.528 [0.49,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | ASIA/ST | gbt3 | 0.516 [0.48,0.55] | 0.528 [0.49,0.57] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | NY/HM | logit2 | 0.543 [0.52,0.56] | 0.528 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | NY/ST | logit2 | 0.519 [0.50,0.54] | 0.526 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | promising: short by 0.154 AUC, 5 of 5 econ |
| X789-G-unlocked | sig | NY/HM | logit2 | 0.544 [0.52,0.56] | 0.526 [0.50,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | ASIA/ST | gbt3 | 0.516 [0.49,0.54] | 0.524 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | ASIA/ST | gbt3 | 0.510 [0.48,0.54] | 0.524 [0.48,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | LONDON | logit2 | 0.510 [0.49,0.53] | 0.524 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| X6-G-unlocked | sig | LONDON/HM | logit2 | 0.516 [0.49,0.55] | 0.524 [0.48,0.57] | - | - | - | N | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| Xall10-G-unlocked | sig | LONDON/ST | logit2 | 0.508 [0.48,0.53] | 0.523 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | LONDON/HM | rf | 0.517 [0.49,0.55] | 0.523 [0.48,0.56] | - | - | - | N | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| X610-G-unlocked | sig | LONDON/ST | logit2 | 0.509 [0.48,0.53] | 0.523 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| X10-G-unlocked | sig | NY/HM | logit2 | 0.526 [0.50,0.55] | 0.522 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X9-G-unlocked | sig | ASIA/HM | gbt3 | 0.529 [0.50,0.56] | 0.522 [0.48,0.56] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | ASIA/HM | gbt3 | 0.524 [0.49,0.55] | 0.522 [0.48,0.56] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X10-G-unlocked | sig | NY | logit2 | 0.519 [0.50,0.54] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X10-G-unlocked | sig | NY/ST | logit2 | 0.514 [0.49,0.54] | 0.522 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X28-G-unlocked | sig | NY | logit2 | 0.521 [0.50,0.54] | 0.521 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| X610-G-unlocked | sig | NY/HM | logit2 | 0.522 [0.49,0.55] | 0.521 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| X610-G-unlocked | sig | LONDON | logit2 | 0.509 [0.49,0.53] | 0.521 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| X7-G-unlocked | sig | ASIA/ST | gbt3 | 0.509 [0.48,0.54] | 0.521 [0.48,0.56] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | NY/ST | rf | 0.520 [0.50,0.54] | 0.521 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| X6-G-unlocked | sig | LONDON | logit2 | 0.510 [0.49,0.53] | 0.520 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X30-G-unlocked | sig | NY/HM | logit2 | 0.528 [0.50,0.55] | 0.520 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X28-G-unlocked | sig | LONDON/HM | rf | 0.516 [0.49,0.54] | 0.519 [0.48,0.56] | - | - | - | N | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| X30-G-unlocked | sig | POOLED | logit2 | 0.520 [0.51,0.53] | 0.519 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | POOLED/ST | gbt3 | 0.520 [0.51,0.53] | 0.519 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | POOLED/ST | gbt3 | 0.518 [0.51,0.53] | 0.518 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | POOLED/ST | gbt3 | 0.520 [0.51,0.53] | 0.518 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | NY/ST | logit2 | 0.515 [0.50,0.54] | 0.518 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| X26-G-unlocked | sig | LONDON/HM | logit2 | 0.516 [0.48,0.55] | 0.518 [0.48,0.57] | - | - | - | N | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| X27-G-unlocked | sig | LONDON/HM | logit2 | 0.517 [0.49,0.55] | 0.518 [0.48,0.56] | - | - | - | N | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| X6-G-unlocked | sig | LONDON/ST | logit2 | 0.506 [0.48,0.53] | 0.518 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| X9-G-unlocked | sig | LONDON/HM | logit2 | 0.515 [0.48,0.55] | 0.518 [0.47,0.56] | - | - | - | N | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| X30-G-unlocked | sig | NY | logit2 | 0.518 [0.50,0.54] | 0.517 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X27-G-unlocked | sig | NY/ST | logit2 | 0.517 [0.50,0.54] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X26-G-unlocked | sig | NY/ST | logit2 | 0.516 [0.50,0.54] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | NY/ST | logit2 | 0.518 [0.50,0.54] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X9-G-unlocked | sig | ASIA | gbt3 | 0.514 [0.49,0.54] | 0.517 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X26-G-unlocked | sig | ASIA | gbt3 | 0.515 [0.49,0.54] | 0.517 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | ASIA | gbt3 | 0.509 [0.49,0.53] | 0.517 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X10-G-unlocked | sig | POOLED/ST | gbt3 | 0.520 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | POOLED/ST | gbt3 | 0.516 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | POOLED/ST | gbt3 | 0.517 [0.50,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | NY | logit2 | 0.520 [0.50,0.54] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X10-G-unlocked | sig | POOLED | logit2 | 0.520 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | POOLED | logit2 | 0.519 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | NY | logit2 | 0.518 [0.50,0.54] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X8-G-unlocked | sig | NY/ST | logit2 | 0.515 [0.50,0.54] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X6-G-unlocked | sig | NY/HM | logit2 | 0.526 [0.50,0.55] | 0.516 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X26-G-unlocked | sig | POOLED | logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | POOLED | logit2 | 0.518 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | POOLED | logit2 | 0.519 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | POOLED/ST | gbt3 | 0.516 [0.50,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | LONDON | logit2 | 0.507 [0.48,0.53] | 0.516 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X610-G-unlocked | sig | POOLED/HM | gbt3 | 0.513 [0.50,0.53] | 0.516 [0.50,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X6-G-unlocked | sig | NY/ST | rf | 0.521 [0.50,0.54] | 0.516 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X27-G-unlocked | sig | NY | logit2 | 0.521 [0.50,0.54] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X28-G-unlocked | sig | POOLED | rf | 0.519 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | NY | logit2 | 0.520 [0.50,0.54] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | NY | logit2 | 0.521 [0.50,0.54] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X10-G-unlocked | sig | POOLED/ST | logit2 | 0.507 [0.49,0.52] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X28-G-unlocked | sig | POOLED/ST | logit2 | 0.509 [0.49,0.53] | 0.516 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X30-G-unlocked | sig | POOLED/HM | logit2 | 0.520 [0.51,0.54] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | ASIA/ST | stack | 0.508 [0.48,0.54] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | POOLED/HM | logit2 | 0.511 [0.50,0.53] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X610-G-unlocked | sig | POOLED | logit2 | 0.511 [0.50,0.52] | 0.515 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X8-G-unlocked | sig | NY | logit2 | 0.519 [0.50,0.54] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | POOLED/ST | logit2 | 0.518 [0.51,0.53] | 0.515 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | POOLED/ST | gbt3 | 0.519 [0.51,0.53] | 0.515 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | NY | logit2 | 0.520 [0.50,0.54] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X7-G-unlocked | sig | ASIA/ST | stack | 0.510 [0.49,0.54] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | NY | logit2 | 0.514 [0.50,0.53] | 0.515 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X9-G-unlocked | sig | NY/HM | logit2 | 0.527 [0.50,0.55] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| X610-G-unlocked | sig | POOLED/ST | logit2 | 0.511 [0.50,0.52] | 0.514 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | LONDON | logit2 | 0.511 [0.49,0.53] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| X27-G-unlocked | sig | LONDON | logit2 | 0.511 [0.49,0.53] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| X30-G-unlocked | sig | ASIA/ST | stack | 0.510 [0.48,0.54] | 0.514 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | NY/ST | logit2 | 0.509 [0.49,0.53] | 0.514 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| X27-G-unlocked | sig | ASIA/ST | stack | 0.510 [0.48,0.54] | 0.513 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | POOLED/ST | logit2 | 0.518 [0.50,0.53] | 0.513 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | POOLED | logit2 | 0.510 [0.50,0.52] | 0.513 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X10-G-unlocked | sig | POOLED | logit2 | 0.509 [0.50,0.52] | 0.513 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | POOLED | logit2 | 0.518 [0.51,0.53] | 0.513 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | POOLED/HM | logit2 | 0.515 [0.50,0.53] | 0.513 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X28-G-unlocked | sig | NY/HM | logit2 | 0.525 [0.50,0.55] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X8-G-unlocked | sig | POOLED | logit2 | 0.518 [0.51,0.53] | 0.513 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | POOLED | logit2 | 0.510 [0.50,0.52] | 0.513 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X27-G-unlocked | sig | NY/HM | logit2 | 0.527 [0.50,0.55] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X8-G-unlocked | sig | NY/HM | logit2 | 0.526 [0.50,0.55] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X26-G-unlocked | sig | NY/HM | logit2 | 0.526 [0.50,0.55] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | NY/HM | logit2 | 0.527 [0.50,0.55] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X28-G-unlocked | sig | POOLED/HM | rf | 0.523 [0.51,0.54] | 0.513 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | POOLED | logit2 | 0.512 [0.50,0.52] | 0.513 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X8-G-unlocked | sig | POOLED/ST | logit2 | 0.509 [0.49,0.53] | 0.513 [0.50,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X10-G-unlocked | sig | LONDON/ST | logit2 | 0.509 [0.48,0.53] | 0.512 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| Xall10-G-unlocked | sig | NY/ST | logit2 | 0.513 [0.49,0.53] | 0.512 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X9-G-unlocked | sig | POOLED/ST | logit2 | 0.509 [0.49,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X26-G-unlocked | sig | POOLED/ST | logit2 | 0.509 [0.49,0.52] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | POOLED/ST | logit2 | 0.510 [0.49,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X27-G-unlocked | sig | POOLED/ST | logit2 | 0.510 [0.49,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X789-G-unlocked | sig | NY/ST | logit2 | 0.507 [0.49,0.53] | 0.512 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X28-G-unlocked | sig | POOLED/HM | rf | 0.515 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X28-G-unlocked | sig | POOLED | logit2 | 0.511 [0.50,0.52] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| Xall10-G-unlocked | sig | POOLED/ST | logit2 | 0.508 [0.49,0.52] | 0.512 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X7-G-unlocked | sig | POOLED/HM | rf | 0.518 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | ASIA/HM | rf | 0.511 [0.48,0.54] | 0.511 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X10-G-unlocked | sig | LONDON | logit2 | 0.508 [0.48,0.53] | 0.511 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X8-G-unlocked | sig | POOLED/HM | rf | 0.518 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | LONDON/ST | logit2 | 0.506 [0.48,0.53] | 0.511 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X610-G-unlocked | sig | POOLED | gbt3 | 0.517 [0.51,0.53] | 0.511 [0.50,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | ASIA/HM | rf | 0.512 [0.48,0.54] | 0.511 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| Xall10-G-unlocked | sig | NY/HM | rf | 0.512 [0.49,0.54] | 0.511 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X9-G-unlocked | sig | POOLED | logit2 | 0.512 [0.50,0.52] | 0.511 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X7-G-unlocked | sig | LONDON | logit2 | 0.506 [0.48,0.53] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| X8-G-unlocked | sig | POOLED | logit2 | 0.511 [0.50,0.52] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X10-G-unlocked | sig | POOLED/HM | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X30-G-unlocked | sig | POOLED/ST | logit2 | 0.506 [0.49,0.52] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X26-G-unlocked | sig | POOLED | logit2 | 0.511 [0.50,0.52] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X27-G-unlocked | sig | POOLED | logit2 | 0.512 [0.50,0.52] | 0.510 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| Xall10-G-unlocked | sig | ASIA | rf | 0.509 [0.49,0.53] | 0.510 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| Xall10-G-unlocked | sig | POOLED/ST | logit2 | 0.517 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | ASIA | rf | 0.509 [0.48,0.53] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| X8-G-unlocked | sig | ASIA/HM | rf | 0.521 [0.49,0.55] | 0.510 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X7-G-unlocked | sig | NY | logit2 | 0.513 [0.49,0.53] | 0.510 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X7-G-unlocked | sig | POOLED/ST | logit2 | 0.504 [0.49,0.52] | 0.509 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | NY | logit2 | 0.513 [0.49,0.53] | 0.509 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X26-G-unlocked | sig | ASIA/ST | stack | 0.509 [0.48,0.54] | 0.509 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | POOLED/HM | rf | 0.516 [0.50,0.53] | 0.509 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | POOLED/ST | logit2 | 0.504 [0.49,0.52] | 0.508 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | POOLED/HM | rf | 0.517 [0.50,0.53] | 0.508 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | ASIA/HM | gbt3 | 0.510 [0.48,0.54] | 0.508 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| X9-G-unlocked | sig | POOLED/HM | logit2 | 0.515 [0.50,0.53] | 0.508 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| X6-G-unlocked | sig | POOLED/ST | rf | 0.507 [0.49,0.52] | 0.508 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | POOLED | logit2 | 0.517 [0.51,0.53] | 0.508 [0.49,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | ASIA/ST | gbt3 | 0.507 [0.48,0.53] | 0.507 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | POOLED/HM | logit2 | 0.515 [0.50,0.53] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| X26-G-unlocked | sig | POOLED/HM | logit2 | 0.515 [0.50,0.53] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| X29-G-unlocked | sig | POOLED/HM | logit2 | 0.515 [0.50,0.53] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| X8-G-unlocked | sig | POOLED/HM | logit2 | 0.513 [0.50,0.53] | 0.507 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| X789-G-unlocked | sig | POOLED/ST | logit2 | 0.516 [0.50,0.53] | 0.507 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | POOLED/HM | gbt3 | 0.511 [0.50,0.53] | 0.507 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| X9-G-unlocked | sig | POOLED/ST | logit2 | 0.517 [0.50,0.53] | 0.507 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | ASIA | stack | 0.508 [0.48,0.53] | 0.507 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | POOLED/HM | rf | 0.517 [0.50,0.53] | 0.506 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | ASIA | rf | 0.501 [0.48,0.52] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | POOLED | logit2 | 0.507 [0.49,0.52] | 0.506 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | ASIA/HM | rf | 0.509 [0.48,0.54] | 0.506 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | short by 0.174 AUC, 5 of 5 econ |
| X789-G-unlocked | sig | POOLED | logit2 | 0.507 [0.49,0.52] | 0.506 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | ASIA/ST | logit2 | 0.502 [0.47,0.53] | 0.506 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | ASIA | stack | 0.499 [0.47,0.52] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | POOLED | logit2 | 0.516 [0.50,0.53] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | POOLED/HM | gbt3 | 0.514 [0.50,0.53] | 0.505 [0.49,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | ASIA/ST | rf | 0.498 [0.47,0.53] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | POOLED | logit2 | 0.518 [0.51,0.53] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | POOLED/HM | rf | 0.517 [0.50,0.53] | 0.505 [0.49,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | NY/HM | logit2 | 0.522 [0.49,0.55] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| X30-G-unlocked | sig | LONDON/ST | logit2 | 0.500 [0.48,0.52] | 0.505 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| X9-G-unlocked | sig | ASIA/ST | logit2 | 0.502 [0.47,0.53] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | LONDON/HM | rf | 0.502 [0.47,0.53] | 0.504 [0.46,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | ASIA | gbt3 | 0.501 [0.48,0.52] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | ASIA | gbt3 | 0.504 [0.48,0.53] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | ASIA | gbt3 | 0.506 [0.48,0.53] | 0.503 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | NY/HM | logit2 | 0.519 [0.49,0.54] | 0.503 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | POOLED/HM | logit2 | 0.519 [0.50,0.53] | 0.502 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | POOLED/HM | logit2 | 0.512 [0.49,0.53] | 0.502 [0.48,0.53] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| X10-G-unlocked | sig | ASIA/ST | rf | 0.493 [0.46,0.52] | 0.502 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | LONDON/HM | stack | 0.503 [0.48,0.53] | 0.502 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | LONDON/ST | rf | 0.501 [0.47,0.53] | 0.502 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| X28-G-unlocked | sig | ASIA | gbt3 | 0.503 [0.48,0.53] | 0.502 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | LONDON/ST | gbt3 | 0.497 [0.47,0.52] | 0.502 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | ASIA | gbt3 | 0.504 [0.48,0.53] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | ASIA/ST | stack | 0.510 [0.48,0.54] | 0.501 [0.46,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | LONDON | gbt3 | 0.500 [0.48,0.52] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | NY/ST | gbt3 | 0.505 [0.48,0.52] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | short by 0.179 AUC, 5 of 5 econ |
| X8-G-unlocked | sig | LONDON/HM | gbt3 | 0.504 [0.47,0.53] | 0.501 [0.45,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | LONDON/ST | rf | 0.496 [0.47,0.52] | 0.501 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | POOLED/HM | rf | 0.508 [0.49,0.52] | 0.501 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | LONDON/ST | gbt3 | 0.502 [0.48,0.52] | 0.501 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| X789-G-unlocked | sig | POOLED/HM | rf | 0.517 [0.50,0.53] | 0.501 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | LONDON/HM | rf | 0.503 [0.47,0.53] | 0.500 [0.46,0.55] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | ASIA/HM | rf | 0.518 [0.49,0.55] | 0.500 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| X8-G-unlocked | sig | ASIA/ST | gbt3 | 0.501 [0.47,0.53] | 0.500 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | LONDON/ST | gbt3 | 0.496 [0.47,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | POOLED/HM | gbt3 | 0.514 [0.50,0.53] | 0.500 [0.48,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | LONDON | gbt3 | 0.503 [0.48,0.52] | 0.500 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | ASIA | gbt3 | 0.500 [0.48,0.52] | 0.499 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | ASIA/HM | rf | 0.507 [0.48,0.54] | 0.499 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.181 AUC, 5 of 5 econ |
| X789-G-unlocked | sig | ASIA/HM | rf | 0.509 [0.48,0.54] | 0.499 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.181 AUC, 5 of 5 econ |
| X610-G-unlocked | sig | ASIA/ST | gbt3 | 0.503 [0.47,0.53] | 0.499 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | ASIA/ST | gbt3 | 0.503 [0.48,0.53] | 0.499 [0.46,0.53] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | POOLED/HM | rf | 0.518 [0.50,0.53] | 0.498 [0.48,0.52] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | ASIA/ST | gbt3 | 0.500 [0.47,0.53] | 0.498 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | ASIA | rf | 0.500 [0.48,0.52] | 0.498 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | ASIA/HM | rf | 0.513 [0.48,0.54] | 0.497 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.183 AUC, 5 of 5 econ |
| X30-G-unlocked | sig | ASIA | gbt3 | 0.499 [0.47,0.52] | 0.496 [0.47,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | LONDON | gbt3 | 0.501 [0.48,0.52] | 0.495 [0.47,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | LONDON/ST | gbt3 | 0.497 [0.47,0.52] | 0.495 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| X28-G-unlocked | sig | ASIA/HM | rf | 0.510 [0.48,0.54] | 0.494 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.186 AUC, 5 of 5 econ |
| X6-G-unlocked | sig | ASIA | stack | 0.502 [0.47,0.53] | 0.494 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | ASIA | gbt3 | 0.498 [0.48,0.52] | 0.494 [0.47,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | ASIA/HM | rf | 0.507 [0.48,0.54] | 0.494 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | short by 0.186 AUC, 5 of 5 econ |
| X27-G-unlocked | sig | ASIA | rf | 0.499 [0.47,0.52] | 0.494 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | LONDON/HM | gbt3 | 0.497 [0.47,0.52] | 0.494 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | ASIA/ST | gbt3 | 0.495 [0.47,0.52] | 0.494 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | LONDON/ST | gbt3 | 0.499 [0.47,0.52] | 0.494 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | ASIA/ST | gbt3 | 0.493 [0.47,0.52] | 0.494 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | ASIA | gbt3 | 0.498 [0.47,0.52] | 0.493 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | ASIA | rf | 0.497 [0.47,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | ASIA | logit2 | 0.497 [0.47,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | LONDON | gbt3 | 0.496 [0.47,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | ASIA | logit2 | 0.497 [0.48,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | LONDON/HM | rf | 0.499 [0.47,0.53] | 0.491 [0.45,0.54] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | ASIA/HM | logit2 | 0.498 [0.47,0.53] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | ASIA/HM | logit2 | 0.504 [0.47,0.54] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | LONDON/ST | gbt3 | 0.494 [0.47,0.52] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | ASIA | logit2 | 0.499 [0.47,0.52] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | ASIA/HM | logit2 | 0.507 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | ASIA/HM | logit2 | 0.506 [0.48,0.54] | 0.490 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | ASIA/HM | logit2 | 0.503 [0.48,0.53] | 0.490 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | LONDON | gbt3 | 0.498 [0.47,0.52] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | ASIA/HM | logit2 | 0.503 [0.47,0.53] | 0.489 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | LONDON/ST | logit2 | 0.492 [0.47,0.52] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | ASIA | gbt3 | 0.493 [0.47,0.52] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | LONDON/ST | gbt3 | 0.501 [0.47,0.52] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| X28-G-unlocked | sig | LONDON/ST | gbt3 | 0.500 [0.47,0.52] | 0.487 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | WF-only (dead) |
| X9-G-unlocked | sig | LONDON | gbt3 | 0.496 [0.47,0.52] | 0.487 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | LONDON | gbt3 | 0.498 [0.47,0.52] | 0.487 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | ASIA/HM | logit2 | 0.510 [0.48,0.54] | 0.485 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | LONDON | rf | 0.492 [0.47,0.51] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | LONDON | gbt3 | 0.495 [0.47,0.52] | 0.484 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | LONDON | rf | 0.497 [0.47,0.52] | 0.483 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | LONDON/ST | logit2 | 0.495 [0.47,0.52] | 0.483 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | LONDON/ST | logit2 | 0.491 [0.47,0.51] | 0.483 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | LONDON | logit2 | 0.498 [0.48,0.52] | 0.483 [0.46,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | LONDON | rf | 0.493 [0.47,0.51] | 0.483 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | ASIA/HM | logit2 | 0.499 [0.47,0.53] | 0.483 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | LONDON | rf | 0.492 [0.47,0.51] | 0.483 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | LONDON | rf | 0.497 [0.47,0.52] | 0.482 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | ASIA/ST | gbt3 | 0.488 [0.46,0.51] | 0.482 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | ASIA/HM | logit2 | 0.500 [0.47,0.53] | 0.481 [0.44,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | LONDON/HM | gbt3 | 0.493 [0.46,0.52] | 0.480 [0.44,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | ASIA/ST | stack | 0.489 [0.46,0.52] | 0.480 [0.44,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | LONDON | logit2 | 0.494 [0.47,0.51] | 0.480 [0.45,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | LONDON | logit2 | 0.491 [0.47,0.51] | 0.480 [0.45,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | ASIA/HM | logit2 | 0.496 [0.47,0.53] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | LONDON/ST | gbt3 | 0.492 [0.47,0.52] | 0.480 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X29-G-unlocked | sig | ASIA/HM | logit2 | 0.497 [0.47,0.53] | 0.479 [0.44,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X789-G-unlocked | sig | LONDON/HM | rf | 0.495 [0.47,0.52] | 0.479 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | LONDON/ST | gbt3 | 0.488 [0.46,0.51] | 0.479 [0.45,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | LONDON/ST | logit2 | 0.498 [0.48,0.52] | 0.478 [0.45,0.51] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | LONDON | rf | 0.491 [0.47,0.51] | 0.478 [0.44,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | LONDON | logit2 | 0.494 [0.47,0.51] | 0.476 [0.45,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | ASIA/ST | stack | 0.491 [0.46,0.52] | 0.476 [0.43,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | LONDON/ST | logit2 | 0.494 [0.47,0.52] | 0.476 [0.45,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | LONDON/HM | logit2 | 0.492 [0.46,0.52] | 0.475 [0.44,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | LONDON/ST | gbt3 | 0.491 [0.46,0.52] | 0.474 [0.44,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | LONDON/ST | gbt3 | 0.494 [0.47,0.52] | 0.474 [0.44,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | LONDON/ST | gbt3 | 0.487 [0.46,0.51] | 0.474 [0.44,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | ASIA | stack | 0.495 [0.47,0.52] | 0.473 [0.45,0.50] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X610-G-unlocked | sig | ASIA/HM | gbt3 | 0.490 [0.46,0.52] | 0.471 [0.43,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X30-G-unlocked | sig | LONDON/HM | rf | 0.489 [0.46,0.52] | 0.467 [0.43,0.51] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X7-G-unlocked | sig | LONDON/HM | rf | 0.489 [0.46,0.52] | 0.464 [0.43,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X9-G-unlocked | sig | LONDON/HM | rf | 0.494 [0.46,0.52] | 0.464 [0.43,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | LONDON/HM | rf | 0.485 [0.46,0.51] | 0.462 [0.43,0.50] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X27-G-unlocked | sig | LONDON/HM | rf | 0.489 [0.46,0.52] | 0.461 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-G-unlocked | sig | LONDON/HM | rf | 0.494 [0.47,0.52] | 0.461 [0.43,0.50] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X26-G-unlocked | sig | LONDON/HM | rf | 0.492 [0.46,0.52] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| Xall10-G-unlocked | sig | ASIA/HM | rf | 0.495 [0.47,0.52] | 0.458 [0.42,0.49] | - | - | - | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X10-G-unlocked | sig | LONDON/HM | rf | 0.492 [0.46,0.52] | 0.458 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X8-G-unlocked | sig | LONDON/HM | rf | 0.490 [0.46,0.52] | 0.457 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |
| X6-G-unlocked | sig | LONDON/HM | rf | 0.480 [0.45,0.51] | 0.451 [0.42,0.49] | - | - | - | N | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- X6-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 NY: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 NY: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 NY: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 NY: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 NY: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-G-unlocked -1 NY: FAILPRED feats (unlocked) + X6 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 NY: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 NY: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 NY: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 NY: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 NY: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-G-unlocked -1 NY: FAILPRED feats (unlocked) + X10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 NY: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 NY: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 NY: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 NY: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 NY: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X610-G-unlocked -1 NY: FAILPRED feats (unlocked) + X610 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 NY: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 NY: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 NY: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 NY: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 NY: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X7-G-unlocked -1 NY: FAILPRED feats (unlocked) + X7 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 NY: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 NY: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 NY: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 NY: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 NY: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X8-G-unlocked -1 NY: FAILPRED feats (unlocked) + X8 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 NY: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 NY: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 NY: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 NY: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 NY: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X9-G-unlocked -1 NY: FAILPRED feats (unlocked) + X9 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 NY: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 NY: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 NY: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 NY: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 NY: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X789-G-unlocked -1 NY: FAILPRED feats (unlocked) + X789 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 NY: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 NY: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 NY: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 NY: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 NY: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-G-unlocked -1 NY: FAILPRED feats (unlocked) + X26 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 NY: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 NY: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 NY: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 NY: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 NY: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-G-unlocked -1 NY: FAILPRED feats (unlocked) + X27 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 NY: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 NY: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 NY: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 NY: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 NY: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-G-unlocked -1 NY: FAILPRED feats (unlocked) + X28 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 NY: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 NY: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 NY: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 NY: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 NY: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-G-unlocked -1 NY: FAILPRED feats (unlocked) + X29 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 NY: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 NY: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 NY: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 NY: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 NY: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X30-G-unlocked -1 NY: FAILPRED feats (unlocked) + X30 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 NY: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 NY: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 NY: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 LONDON: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 ASIA: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 POOLED: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 NY: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 NY: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- Xall10-G-unlocked -1 NY: FAILPRED feats (unlocked) + Xall10 signal features for all 14,080 unlocked signals; model by WF-PRE; no gate/R11 (pre AUC<0.68)
