# FADE_NTESTED - books tested per FADE_* slice (n_tested for the family null = sum of the latest row per slice)
| utc | slice | owner | n_tested | note |
|--|--|--|--|--|
| 2026-11-03T21:29Z | FADE_selftest | ZL-2 | 0 | header |
| 2026-11-03T21:32Z | FADE_MZ | Z1 | 96 | mirror question 96 cells (6 books x 8 switches x OFF/HALF); fade-entry cells to be added |
| 2026-11-03T21:33Z | FADE_TP | S4b | 441 | screen: 7 tape triggers x 11 anchor groups x 4 sessions x 2 shapes (non-empty cells >= 40 trades); shape / buffer expansion later counted separately |
| 2026-11-03T21:33Z | FADE_LV | ZL-1 | 1054 | level-anchor fades: stage 1 (170 cells default shape) + stage 2 (12 cells x 72 shapes) + stage 3 (20 planned) |
| 2026-11-03T21:38Z | FADE_RG | CAL | 387 | NY-AM fade family F1 (378 books) + 9 round-number offset placebo lines; prereg FADE_RG_prereg sha 7437edd0... |
| 2026-11-03T21:39Z | FADE_VW | Z2 | 10512 | VWAP bands / stretch / TOD stretch / IB60 / OR5-15-30 x 3 triggers x 4 sessions x 2 buffers x 7 targets x 3 time stops x 2 re-entry |
| 2026-11-03T21:40Z | FADE_LV | ZL-1 | 1054 | level-anchor fades: stage 1 (170 cells default shape) + stage 2 (12 cells x 72 shapes) + stage 3 (20 planned) |
| 2026-11-03T21:42Z | FADE_VW | Z2 | 10512 | VWAP bands / stretch / TOD stretch / IB60 / OR5-15-30 x 3 triggers x 4 sessions x 2 buffers x 7 targets x 3 time stops x 2 re-entry |
| 2026-11-03T21:46Z | FADE_TP | S4b | 441 | screen: 7 tape triggers x 11 anchor groups x 4 sessions x 2 shapes (non-empty cells >= 40 trades); shape / buffer expansion later counted separately |
| 2026-11-03T21:46Z | FADE_LV | ZL-1 | 1054 | level-anchor fades: stage 1 (170 cells default shape) + stage 2 (12 cells x 72 shapes) + stage 3 (20 planned) |
| 2026-11-03T21:46Z | FADE_RG | CAL | 1359 | F1 378 + RN offset placebos 9 + neighbourhood scan G (ON, AS, IB60 failed-break fade x 324 each, one family per anchor); prereg addendum FADE_RG |
| 2026-11-03T21:53Z | FADE_VW_STNB | Z2 | 324 | NY-AM stretch-reject neighbourhood family |
| 2026-11-03T22:01Z | FADE_TP | S4b | 981 | screen 441 + shape expansion 540 (12 cells x 45 shapes) |
| 2026-11-03T22:14Z | FADE_TP | S4b | 1710 | all cells tried: 441 screen + 540 shape expansion + 729 neighbourhood |
| 2026-11-03T22:24Z | FADE_LV | ZL-1 | 1054 | level-anchor fades: stage 1 (170 cells default shape) + stage 2 (12 cells x 72 shapes) + stage 3 (20 planned) |
| 2026-11-03T22:35Z | FADE_LV | ZL-1 | 1054 | level-anchor fades: stage 1 (170 cells default shape) + stage 2 (12 cells x 72 shapes) + stage 3 (20 planned) |
| 2026-11-03T22:46Z | FADE_LV | ZL-1 | 1054 | level-anchor fades: stage 1 (170 cells default shape) + stage 2 (12 cells x 72 shapes) + stage 3 (20 planned) |
| 2026-11-03T22:55Z | FADE_TP | S4b | 486 | screen: 7 tape triggers x 11 anchor groups x 4 sessions x 2 shapes (non-empty cells >= 40 trades); shape / buffer expansion later counted separately |
| 2026-11-03T22:59Z | FADE_TP | S4b | 2484 | v2 after ZL-2 audit fixes: screen 486 + shape expansion 540 + neighbourhood 1,458 (two-sided and one-sided) |
| 2026-11-03T22:59Z | FADE_TP | S4b | 2484 | v2 after ZL-2 audit fixes: screen 486 + shape expansion 540 + neighbourhood 1,458 (two-sided and one-sided) |
| 2026-11-03T23:00Z | FADE_TP | S4b | 2484 | v2 all cells tried: 2484 |
| 2026-11-03T23:02Z | FADE_MZ | Z1 | 2336 | mirror 96 cells + Mancini failed-break 2,240 cells (1,672 with trades) |
| 2026-11-03T23:15Z | FADE_TP | S4b | 487 | screen: 7 tape triggers x 11 anchor groups x 4 sessions x 2 shapes (non-empty cells >= 40 trades); shape / buffer expansion later counted separately |
| 2026-11-03T23:20Z | FADE_TP | S4b | 2485 | v2 all cells tried: 2485 |
| 2026-11-04T00:15Z | FADE_XI | Z2 | 60 | 6 books x (NQ ref + ES RTY YM); ONRTH/VWAPF/ORBF x 4 scalings; ATR-based books one variant |
| 2026-11-04T00:25Z | FADE_MZ | Z1 | 3104 | mirror 96 + Mancini failed-break 2,240 + zone-line failed-break 768 cells |
| 2026-11-04T00:40Z | FADE_GM | CAL | 60 | gamma regime: 7 fade series + 6 live NY-AM books x 3 predictors (G_POS/NEG, ZGD, WALL) + family max-stat; prereg FADE_GM_prereg sha ca77055d |
| 2026-11-04T01:10Z | FADE_LV | ZL-1 | 1054 | level-anchor fades: stage 1 (170 cells default shape) + stage 2 (12 cells x 72 shapes) + stage 3 (20 planned) |
