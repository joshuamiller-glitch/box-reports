# Live vs replay P9 (2026-10-20 ->), 47 trades, files: <repo>/data/live/StratTrades_DualStrat2_<acct>.csv

## Trades
|                  |   n |   qty |    pts |   span_s |     pnl |
|:-----------------|----:|------:|-------:|---------:|--------:|
| ('HM', 'OTHER')  |   4 |  9.5  |  -6.94 |        0 |   -3455 |
| ('HM', 'STOP')   |   8 | 14    | -61.79 |        0 | -137410 |
| ('HM', 'TARGET') |   3 | 14    |  59.99 |        0 |   50390 |
| ('ST', 'OTHER')  |  16 |  7.94 |  -6.51 |        0 |  -15120 |
| ('ST', 'STOP')   |  10 | 14    | -62.19 |        0 | -172910 |
| ('ST', 'TARGET') |   6 | 12.83 |  55.64 |        0 |   88755 |

## Entry slippage: no reference (give --ref time,mid at signal instants).  Replay table:
|                 |   mean |   median |   count |
|:----------------|-------:|---------:|--------:|
| ('EM', 'HM')    |   4.22 |     3.71 |    6188 |
| ('EM', 'ST')    |   4.43 |     3.79 |    8143 |
| ('S14x1', 'HM') |   1.77 |     1.5  |    6188 |
| ('S14x1', 'ST') |   1.9  |     1.54 |    8143 |

## Stop exits (live)
n=18  mean exit vs stop level (pts, +ve better) -2.01  worst -10.1

REPLAY XJ on STOP exits: mean pts_x - pts_base +3.16  passive fully filled within 3 s: nan  any passive fill: nan

## NT8 log
StopFB (join timed out) lines 0; rejects 7; EntryFB 0; join fill rate (stop exits - StopFB - rejects)/stop exits ~ see ledger; replay full-fill rate above

