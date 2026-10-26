# Live vs replay P9 (2026-10-20 ->), 80 trades, files: <repo>/data/live/StratTrades_DualStrat2_<acct>.csv

## Trades
|                  |   n |   qty |    pts |   span_s |     pnl |
|:-----------------|----:|------:|-------:|---------:|--------:|
| ('HM', 'OTHER')  |   5 |  9.6  |  -3.48 |        0 |   -1305 |
| ('HM', 'STOP')   |  10 | 13.2  | -62.43 |        0 | -163205 |
| ('HM', 'TARGET') |   3 | 14    |  59.99 |        0 |   50390 |
| ('ST', 'OTHER')  |  32 |  8.78 | -13.35 |        0 |  -77150 |
| ('ST', 'STOP')   |  16 | 11.56 | -57.37 |        0 | -217965 |
| ('ST', 'TARGET') |  14 | 10.36 |  50.63 |        0 |  155670 |

## Entry slippage: no reference (give --ref time,mid at signal instants).  Replay table:
|                |   mean |   median |   count |
|:---------------|-------:|---------:|--------:|
| ('EM8', 'HM')  |   3.16 |     2.75 |    6188 |
| ('EM8', 'ST')  |   3.34 |     2.88 |    8143 |
| ('S8x1', 'HM') |   1.75 |     1.5  |    6188 |
| ('S8x1', 'ST') |   1.9  |     1.56 |    8143 |

## Stop exits (live)
n=26  mean exit vs stop level (pts, +ve better) +0.68  worst -10.1

REPLAY XJ8 on STOP exits: mean pts_x - pts_base +0.85  passive fully filled within 3 s: 0.78  any passive fill: 0.83

## NT8 log
StopFB (join timed out) lines 0; rejects 201; EntryFB 0; join fill rate (stop exits - StopFB - rejects)/stop exits ~ see ledger; replay full-fill rate above

