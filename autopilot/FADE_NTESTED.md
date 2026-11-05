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
| 2026-11-04T22:06Z | DISAG | BASE-4 | 98 | DIS-AG Shadow lot calibration: 14 lines x 7 sizings (L1,2,3,4,6, equal-risk 600/1200); scope DISAG sha 969561f9... |
| 2026-11-04T22:08Z | DISAC | Z3 | 288 | DIS-AC: Asia continuation hold regime book: asia sub-grid x 3 switches; prereg DIS_AC sha 3595f2c6 |
| 2026-11-04T22:11Z | DISAH | CAL | 61 | DIS-AH per-book lot weights on Q1-A ts2 (locks re-run): PE grid 5, PE x HM 30, KB/MV/SM/PB 20, risk-parity 6; bootstrap 2,000 draws; PA9 best 6 |
| 2026-11-04T22:12Z | DISAJ | BASE-4 | 63 | DIS-AJ true-drift family test: 21 cells x 3 world sets (random-minute drift, day-shuffle, matched clock) x 200 worlds; scope DISAJ sha 799e91a1... |
| 2026-11-04T22:14Z | DISP | Z1 | 336 | DIS-P: post-stop cooldown / loss-streak overlays (336 cells) |
| 2026-11-04T22:32Z | FADE_DISAO | Z1 | 400 | DIS-AO: 24 combos x 6 windows x 2 nulls = 288 excess tests + 72 NQ-vs-instrument bootstraps + 40 warm-up sensitivity; ledger DIS_AO |
| 2026-11-04T22:41Z | DISAX | BASE-4 | 26 | DIS-AX TH-L2 cut cost/latency/slicing sensitivity (settings, not hypotheses); scope DISAX sha 371a8908... |
| 2026-11-04T22:43Z | FADE_DISAV | Z1 | 69 | DIS-AV: 48 link tests (24 x bootstrap+placebo) + 12 level shifts + 6 pooled + 3 rank; ledger DIS_AV |
| 2026-11-04T22:47Z | FADE_DISBC | Z1 | 168 | DIS-BC: 36 level shifts + 24 NQ-vs diffs + 36 lag-1 links x 2 nulls + 36 same-day; ledger DIS_BC |
| 2026-11-04T22:53Z | DISBB | BASE-4 | 57 | DIS-BB TH-L2 -30 as a resting stop: 57 engine configurations (stops 25-40, targets, costs 0.80-5.0, per book, arm-only/full); scope DISBB sha 833bc47c... |
| 2026-11-04T22:56Z | FADE_RG | CAL | 1359 | QA-2 note (Z1, 2026-11-04T22:56Z): registry only, ledger rows not stored (no DEAD_CELLS program for this slice; numbers are in its report); n_tested unchanged |
| 2026-11-04T22:56Z | FADE_VW_STNB | Z2 | 324 | QA-2 note (Z1, 2026-11-04T22:56Z): registry only, ledger rows not stored (no DEAD_CELLS program for this slice; numbers are in its report); n_tested unchanged |
| 2026-11-04T22:56Z | Q4_ZL2 | ZL-2 | 85 | QA-2 note (Z1, 2026-11-04T22:56Z): registry only, ledger rows not stored (no DEAD_CELLS program for this slice; numbers are in its report); n_tested unchanged |
| 2026-11-04T22:56Z | Q5 | ZL-2 | 450 | QA-2 note (Z1, 2026-11-04T22:56Z): registry only, ledger rows not stored (no DEAD_CELLS program for this slice; numbers are in its report); n_tested unchanged |
| 2026-11-04T22:56Z | Q8 | ZL-2 | 100 | QA-2 note (Z1, 2026-11-04T22:56Z): registry only, ledger rows not stored (no DEAD_CELLS program for this slice; numbers are in its report); n_tested unchanged |
| 2026-11-04T22:56Z | Q9 | ZL-2 | 180 | QA-2 note (Z1, 2026-11-04T22:56Z): registry only, ledger rows not stored (no DEAD_CELLS program for this slice; numbers are in its report); n_tested unchanged |
| 2026-11-04T22:56Z | Q10 | ZL-2 | 100 | QA-2 note (Z1, 2026-11-04T22:56Z): registry only, ledger rows not stored (no DEAD_CELLS program for this slice; numbers are in its report); n_tested unchanged |
| 2026-11-04T22:56Z | Q12 | ZL-2 | 160 | QA-2 note (Z1, 2026-11-04T22:56Z): registry only, ledger rows not stored (no DEAD_CELLS program for this slice; numbers are in its report); n_tested unchanged |
| 2026-11-04T22:56Z | DIST | ZL-2 | 60 | QA-2 note (Z1, 2026-11-04T22:56Z): registry only, ledger rows not stored (no DEAD_CELLS program for this slice; numbers are in its report); n_tested unchanged |
| 2026-11-04T22:56Z | AUDITL2 | BASE-4 | 12 | QA-2 note (Z1, 2026-11-04T22:56Z): registry only, ledger rows not stored (no DEAD_CELLS program for this slice; numbers are in its report); n_tested unchanged |
| 2026-11-04T22:56Z | DISN | Z1 | 817 | QA-2 note (Z1, 2026-11-04T22:56Z): DIS_N ledger holds 511 rows = 471 sweep cells that produced trades + 40 entry-delay cells; the other 306 of the 817 registered grid cells had no trades and were not stored (checked against disn_sweep.pkl); n_tested unchanged |
| 2026-11-04T22:56Z | DISP | Z1 | 336 | QA-2 note (Z1, 2026-11-04T22:56Z): DIS_P (Z1, = DIS-AN) ledger holds 246 rows = the 246 of the 336 grid cells that produced trades (disp_sweep.pkl); the 90 empty cells were not stored; n_tested unchanged |
| 2026-11-04T22:56Z | DISG | Z1 | 783 | QA-2 note (Z1, 2026-11-04T22:56Z): DIS_G (Z1) ledger holds 748 of the 783 registered cells; the 35 missing are cells without trades by the same rule (not re-verified cell by cell); n_tested unchanged |
| 2026-11-04T22:56Z | DISAQ | Z3 | 10 | QA-2 note (Z1): DIS-AQ had no registry line; n = ledger rows (program DIS_AQ, 10 rows) pending the owner's own test count; owner to confirm or re-append |
| 2026-11-04T23:02Z | DISBH | BASE-4 | 50 | DIS-BH verdict-rule operating characteristics: 10 lines x 5 truths x 5,000 paths + pooled variants (simulation, not hypotheses); scope DISBH sha f05c6b92... |
| 2026-11-04T23:02Z | FADE_DISW | ZL-1 | 44 | DIS-W OOS 2013-2023 1-min watch lines + regime scan (prereg DISW sha 4fbef5bd...) |
| 2026-11-04T23:03Z | SIZER_S3_ID_REUSE_NOTE | Z3 | 0 | CONFIRMED (Z1 QA-2): ledger program SIZER_S3 has 138 repeated cell_ids with different values = id REUSE across three append batches, not double appends: batch 1 (basis v13t_live_q1a, 138 rows: 3.2/3.3 on ts, 3.4, 3.5), batch 2 (basis v13t_ts2_q1a, 138 rows, same cell names rerun on ts2) and batch 3 (basis v13t_ts2_q1a_live3, 123 rows, live-universe ranks); the disambiguating key is cell_spec (…base=q1a / base=ts2q1a / base=ts2q1a_live3) and the basis column; the live-universe causal re-score (ts2live4) was NOT appended separately (its rows are in SIZER_S3_MASTER_ROWS_LIVE4.csv). DISAQ = 10 confirmed (10 cells appended). |
| 2026-11-04T23:11Z | FADE_DISBM | ZL-1 | 28 | DIS-BM OOS 2013-2023 remaining watch lines, raw + percent frames (prereg DISBM sha 49997bf4...) |
| 2026-11-04T23:19Z | DISBR | BASE-4 | 9 | DIS-BR cross-check of DIS-BJ: 9 engine runs of the ts2 base with live-window masks (settings, not hypotheses); scope DISBR sha 323db9b3... |
| 2026-11-04T23:33Z | FADE_DISBU | Z1 | 276 | DIS-BU: 19 cell-variant computations x 4 windows x 3 nulls = 228 excess tests + 48 seed-sensitivity runs; ledger DIS_BU; lot-table rows descriptive (not counted) |
| 2026-11-04T23:40Z | FADE_DISBS | ZL-1 | 363 | DIS-BS YM U7 NY-PM 181 cells x 2 frames + BTC K7 London pre-2023 (prereg DISBS sha b5da27dc...) |
| 2026-11-05T00:02Z | DISBV | BASE-4 | 6 | DIS-BV TH-L2 trigger fidelity: 6 engine runs (TH off, stored, rebuilt-on-stored-rows, rebuilt-every-second, two arm-only) on 37 sample weeks (settings, not hypotheses); scope DISBV sha 42716f5e... |
| 2026-11-05T00:29Z | DISBY | BASE-4 | 23 | DIS-BY TH-L2 evaluation clock: 23 engine runs (clock x slippage x two bases, arm-only variants; settings, not hypotheses), one event-driven rebuild on 37 weeks; scope DISBY sha b2f5e75d... |
