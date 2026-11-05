# DS3_INSTR2_ZN - interim stage A 2026-11-05T20:12Z (Z3, T-INSTR-2 section 1; stage A screen, NOT a verdict)
Base: library families (code/instr2/families.py, 16 families), 1-min bar sim FM.sim_bars (signal at close, entry next open, stop first), Z2 sessions, ZN tick/fee proxy from INSTR2_SESSIONS.md, integer lots at USD 1,200 risk, participation-capped, window = $/week net with carrying weeks dropped. Prereg: prereg/T2_ZN_scope.md + T2_Z3_addendum1.md (sha256 in DECISIONS.md). Stage A = 5426 rows (signal cell x session x 2 reference brackets). Look-ahead cut test: intraday truncation test (t2_trunc.py, cuts every 15 min over DST / roll / normal days, 3 params per family, all 16 families): 0 mismatches; ZL-1's audit of families.py 0 / 5,116.
Plain sentence: of 5426 stage-A rows, 57 have L3M, L6M and HOLD all positive and 8 pass the screen gate (older windows tolerant, L6M n>=20); none has a placebo, walk-forward or stack check yet, so none is a lead; the stage-B bracket sweep on the top 300 cells is running.

| instrument | session | family | params | bracket | n | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD HOLD | Calmar | corr to NQ stack | stack gain | placebo | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ZN | nyam | supertrend_flip | {'k': 15, 'n': 14, 'm': 2} | atr3_1.5R_60 | 461 | 559 | 663 | 340 | 25 | 13 | -408 | -137 | 9214 | 0.1 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZN | nyam | keltner_flip | {'k': 5, 'n': 8, 'n_atr': 7, 'mult': 1.5} | usd1200_1.5R_60 | 365 | 119 | 117 | 21 | 17 | 41 | -49 | 53 | 619 | 1.1 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZN | nyam | keltner_flip | {'k': 5, 'n': 13, 'n_atr': 14, 'mult': 2.0} | atr3_1.5R_60 | 385 | 152 | 119 | 95 | 16 | 365 | -324 | -155 | 7527 | 0.1 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZN | nyam | supertrend_flip | {'k': 5, 'n': 14, 'm': 3} | usd1200_1.5R_60 | 505 | 176 | 200 | 44 | 14 | -8 | 6 | 23 | 740 | 0.8 | n/a | n/a | n/a | SCREEN-GATE ONLY (stage A; no placebo/WF/stack) |
| ZN | nyam | supertrend_flip | {'k': 3, 'n': 10, 'm': 4} | usd1200_1.5R_60 | 486 | 190 | 211 | 44 | 13 | -6 | -20 | 2 | 1053 | 0.5 | n/a | n/a | n/a | SCREEN-GATE ONLY (stage A; no placebo/WF/stack) |
| ZN | nyam | supertrend_flip | {'k': 15, 'n': 14, 'm': 2} | usd1200_1.5R_60 | 438 | 116 | 137 | 39 | 11 | 10 | -53 | 32 | 865 | 0.5 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZN | nyam | keltner_flip | {'k': 5, 'n': 13, 'n_atr': 14, 'mult': 2.0} | usd1200_1.5R_60 | 371 | 47 | 45 | 33 | 11 | 40 | -51 | 2 | 799 | 0.6 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZN | nyam | supertrend_flip | {'k': 10, 'n': 5, 'm': 2} | usd1200_1.5R_60 | 454 | 119 | 137 | 29 | 11 | 15 | -24 | -3 | 726 | 0.6 | n/a | n/a | n/a | SCREEN-GATE ONLY (stage A; no placebo/WF/stack) |
| ZN | nyam | supertrend_flip | {'k': 15, 'n': 14, 'm': 1.5} | usd1200_1.5R_60 | 580 | 129 | 129 | 7 | 11 | 20 | -46 | 78 | 749 | 0.6 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZN | nyam | supertrend_flip | {'k': 15, 'n': 10, 'm': 1.5} | usd1200_1.5R_60 | 534 | 98 | 98 | 12 | 7 | 20 | -43 | 66 | 900 | 0.3 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZN | nyam | supertrend_flip | {'k': 3, 'n': 14, 'm': 4} | usd1200_1.5R_60 | 484 | 150 | 174 | 44 | 4 | -35 | -8 | 27 | 1204 | 0.2 | n/a | n/a | n/a | SCREEN-GATE ONLY (stage A; no placebo/WF/stack) |
| ZN | nyam | supertrend_flip | {'k': 5, 'n': 5, 'm': 4} | usd1200_1.5R_60 | 331 | 130 | 168 | 37 | 4 | 13 | -30 | 17 | 919 | 0.2 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZN | nyam | keltner_flip | {'k': 2, 'n': 13, 'n_atr': 14, 'mult': 2.5} | usd1200_1.5R_60 | 262 | 41 | 19 | 5 | 4 | -6 | -18 | 69 | 580 | 0.3 | n/a | n/a | n/a | SCREEN-GATE ONLY (stage A; no placebo/WF/stack) |
| ZN | nyam | supertrend_flip | {'k': 5, 'n': 5, 'm': 3} | usd1200_1.5R_60 | 489 | 157 | 181 | 44 | 2 | -36 | -16 | 18 | 1346 | 0.1 | n/a | n/a | n/a | SCREEN-GATE ONLY (stage A; no placebo/WF/stack) |
| ZN | nyam | supertrend_flip | {'k': 5, 'n': 10, 'm': 3} | usd1200_1.5R_60 | 491 | 148 | 172 | 25 | 2 | -29 | -23 | 22 | 1245 | 0.1 | n/a | n/a | n/a | SCREEN-GATE ONLY (stage A; no placebo/WF/stack) |

Columns L1M..X' are net $/week (carry dropped) at the cell's own lots, rank = min(L3M, L6M, HOLD). Stage-B (300 x 84 brackets) and the evaluator (placebos, walk-forward, stack correlation, 13-year check) follow; finalist trade frames go to /mnt/l2/l2vast/instr2_trades/ZN/. Rows are screening numbers: best-of-5426, NOT leads.

## Walk-forward selector diagnostic (Z2 wf_selector.py, weekly equal-risk matrix of all 25,200 stage-B cells; trailing 26 and 52 weeks, purge 1 week, top-1/top-3; Z3 2026-11-05T20:47Z)
Out-of-sample mean USD/week of the monthly re-selected cell, by session and lookback (details: l2vast/ds3/out/instr2/ZN/WF.pkl): negative or zero in all 12 session x lookback combinations (no combination is positive; several are exactly 0 because no candidate was eligible). The selector does not rescue any ZN book: the parameter choice does not carry forward.

## Plain sentence (ZN)
No ZN book on its own grid clears the diversifier bar: of 30 finalists none passes the tolerant gate with placebo, walk-forward and stack checks, every recent positive is NOW-ONLY/regime (0 of 60 tested cells positive in most pre-2023 years), and a one-tick cost change flips the sign of the best screen cell; ZN is DEAD for this grid (ranked table above), not a lead. Base for numbers: library families, evaluator basis, 2023-04..2026-10-16, USD 1,200 risk, carrying weeks dropped.
