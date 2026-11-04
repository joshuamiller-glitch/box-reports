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
| 2026-11-04T19:08Z | Q4_ZL2 | ZL-2 | 85 | change-point dating, common break, online detectors, candidate-vs-break demo |
| 2026-11-04T19:11Z | DISA_D1 | Z3 | 264 | D1 multi-hour holds: 9 sources x session x stop x time stop x target; prereg DIS_A sha 2280ce04 |
| 2026-11-04T19:17Z | DIS_C | S4b | 229 | weekend / Sunday-open: 21 predictor tests + 180 Sunday cells + 28 stack-Asia tests |
| 2026-11-04T19:18Z | FADE_DISB | S4a | 1338 | DIS-B pre-market structure books: cells with n>=100 |
| 2026-11-04T19:20Z | FADE_DISB | S4a | 1338 | DIS-B pre-market structure books: cells with n>=100 |
| 2026-11-04T19:24Z | DIS_E | S4b | 496 | queue-dynamics entry books: A IMB, B CAN, C ADD, D RFAIL, E LIQ-ORB, F ABS-ANCHOR |
| 2026-11-04T19:36Z | DISI | BASE-4 | 1038 | FLOW-CALENDAR: 800 entry books (25 flags x 4 sessions x 4 kinds x 2 shapes) + 238 Q1-A overlay cells (25 flags x 5 scopes x 2 actions minus 12 EINT2-covered); prereg DISI_prereg sha be78eb84... |
| 2026-11-04T19:54Z | Q5 | ZL-2 | 450 | hold shapes on the six live books: 11 shapes x ~41 book/session cells |
| 2026-11-04T20:00Z | Q8 | ZL-2 | 100 | day-type switch: 14 classifiers x 6 rules + 2 oracle + classifier metrics |
| 2026-11-04T20:04Z | DISJ | ZL-1 | 668 | option-OI level books on NQ: stage 1 84 + stage 2 8 x 72 + stage 3 8 planned |
| 2026-11-04T20:07Z | Q9 | ZL-2 | 180 | session-to-session conditional books + overlays, 172 cells |
| 2026-11-04T20:17Z | Q10 | ZL-2 | 100 | earnings-season books: 72 gap cells + 16 opening-move-fade cells + report |
| 2026-11-04T20:18Z | Q6 | Q6-owner | 294 | pyramiding on continuation: 6 live books x (48 PYR cells) + 6 DIP7030 reference cells (NOADD = reference) |
| 2026-11-04T20:23Z | Q11 | BASE-4 | 480 | daily-trend-aligned P7/A7 books: 360 entry cells (6 trend defs x WITH/COUNTER x 5 groups x sides x 2 shapes) + 120 descriptive cells for KB/SM/HM/MV; prereg Q11_prereg sha 8a523441... |
| 2026-11-04T20:23Z | Q12 | ZL-2 | 160 | bar-type diversity: KB/SM/PB x 9 bar types + control x 5 sessions |
| 2026-11-04T20:24Z | DISA_D2 | Z3 | 48 | D2 pyramids: 4 sources x session x trail x adds; prereg DIS_A sha 2280ce04 |
| 2026-11-04T20:34Z | DISG | Z1 | 736 | DIS-G: NQ entry books driven by ES/RTY/YM state (G1-G5, 736 cells) |
| 2026-11-04T20:38Z | Q14 | Q14-owner | 240 | NQ-vs-ES spread books NY-AM: A two-leg spread 96 + B NQ own move ES-flat 96 + B0 control 48 |
| 2026-11-04T20:39Z | Q13 | ZL-1 | 477 | gap-conditioned books on NQ: stage 1 45 + stage 2 6 x 36 shapes (prereg said 72; code uses 36) ; n_tested bound 477 |
| 2026-11-04T20:49Z | DISG | Z1 | 783 | DIS-G: 736 entry cells + 47 (filters 20, YM-conditioning 15, ES/RTY delta splits 12) |
| 2026-11-04T20:50Z | DISF | CAL | 50 | DIS-F post-earnings-day overlay: 2 flags x 5 variants x (sleeve + 4 fade targets); placebos 10 shifts + 100/200 random + 100/200 circular, 150 family worlds |
| 2026-11-04T21:01Z | DISQ | CAL | 440 | DIS-Q late-day books: 200 eligible-type + 240 calendar cross-tab cells (WITCH/RUSS empty); placebos 5 clock shifts + 100 side + 100 shift5 per eligible cell, 100 family worlds x 2 kinds |
| 2026-11-04T21:05Z | DISN | Z1 | 817 | DIS-N: 777 clock overlay cells + 40 entry-delay cells |
| 2026-11-04T21:06Z | DIST | ZL-2 | 60 | watch-bundle portfolio: estimators, leave-one-out, placebo bundle |
| 2026-11-04T21:07Z | DISM | BASE-4 | 112 | DIS-M drift benchmark: 24 random-time + 48 fixed-clock benchmark cells, 20 live groups (replica), 19 candidates (Shadow lines + own cells), 1 hedged stack; prereg DISM_prereg sha f32b5312... + addendum1 e28ad121... |
| 2026-11-04T21:10Z | FADE_DISU | ZL-1 | 52 | DIS-U regime episodes/duration/detector replay (prereg DISU sha be47bffe...) |
| 2026-11-04T21:27Z | DISY | BASE-4 | 22 | DIS-Y drift-excess table: 22 watch cells (12 ranked-list / DIS-Q, 8 NYAM-fade and FADE lines incl. bundle, 2 Q4 amplifier forms); prereg DISY sha 860b18ca... |
| 2026-11-04T21:36Z | AUDITL2 | BASE-4 | 12 | AUDIT-L2 part 2: 4 fade survivors (+2 sensitivity) x 3 fair placebos; prereg AUDITL2 sha 2b587f93... |
| 2026-11-04T21:44Z | FADE_DISG | S4a | 525 | DIS-G pre-market structure books: cells with n>=100 |
| 2026-11-04T21:49Z | DISAA | BASE-4 | 6 | DIS-AA pre-2023 OOS: 5 lines + bundle x 4 benchmarks x 14 years (descriptive, 6 verdicts); scope DISAA sha 5927ec85... |
| 2026-11-04T21:53Z | DISAC | Z3 | 288 | DIS-AC: Asia continuation hold regime book: asia sub-grid x 3 switches; prereg DIS_AC sha 3595f2c6 |
| 2026-11-04T21:57Z | DISS | CAL | 86 | DIS-S equity-curve/streak: 44 serial-dependence tests + 28 engine overlay cells + 14 bundle cells; 100 draws x 3 placebos per cell, 100 family worlds |
| 2026-11-04T21:58Z | DISAD | BASE-4 | 16 | DIS-AD PB asia reconcile: 4 Asia cells x 4 periods decomposition (+ yearly PB, O2/O3 windows); scope DISAD sha 9ce7146c... |
