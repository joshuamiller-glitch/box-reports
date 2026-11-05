# DS3_INSTR2_ZB - interim stage A 2026-11-05T20:12Z (Z3, T-INSTR-2 section 1; stage A screen, NOT a verdict)
Base: library families (code/instr2/families.py, 16 families), 1-min bar sim FM.sim_bars (signal at close, entry next open, stop first), Z2 sessions, ZB tick/fee proxy from INSTR2_SESSIONS.md, integer lots at USD 1,200 risk, participation-capped, window = $/week net with carrying weeks dropped. Prereg: prereg/T2_ZB_scope.md + T2_Z3_addendum1.md (sha256 in DECISIONS.md). Stage A = 5426 rows (signal cell x session x 2 reference brackets). Look-ahead cut test: intraday truncation test (t2_trunc.py, cuts every 15 min over DST / roll / normal days, 3 params per family, all 16 families): 0 mismatches; ZL-1's audit of families.py 0 / 5,116.
Plain sentence: of 5426 stage-A rows, 30 have L3M, L6M and HOLD all positive and 3 pass the screen gate (older windows tolerant, L6M n>=20); none has a placebo, walk-forward or stack check yet, so none is a lead; the stage-B bracket sweep on the top 300 cells is running.

| instrument | session | family | params | bracket | n | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD HOLD | Calmar | corr to NQ stack | stack gain | placebo | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ZB | pre | keltner_flip | {'k': 2, 'n': 13, 'n_atr': 7, 'mult': 2.5} | atr3_1.5R_60 | 276 | 392 | 74 | 105 | 193 | 392 | -431 | -18 | 7129 | 1.1 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | nyam | supertrend_flip | {'k': 3, 'n': 10, 'm': 4} | usd1200_1.5R_60 | 547 | 204 | 259 | 43 | 47 | 92 | -46 | 46 | 1371 | 1.4 | n/a | n/a | n/a | SCREEN-GATE ONLY (stage A; no placebo/WF/stack) |
| ZB | pre | session_extreme_fade | {'anchor_hm': 500, 'span_min': 400, 'min_bars': 15, 'cooldown': 30} | usd1200_1.5R_60 | 299 | 150 | 118 | 52 | 31 | 42 | -73 | -43 | 1017 | 1.3 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | pre | session_extreme_fade | {'anchor_hm': 500, 'span_min': 400, 'min_bars': 15, 'cooldown': 15} | usd1200_1.5R_60 | 299 | 150 | 118 | 52 | 31 | 42 | -73 | -43 | 1017 | 1.3 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | nyam | supertrend_flip | {'k': 10, 'n': 5, 'm': 2} | usd1200_1.5R_60 | 488 | 154 | 154 | 27 | 45 | 78 | -11 | -25 | 1147 | 1.6 | n/a | n/a | n/a | SCREEN-GATE ONLY (stage A; no placebo/WF/stack) |
| ZB | nyam | supertrend_flip | {'k': 10, 'n': 10, 'm': 2} | usd1200_1.5R_60 | 547 | 130 | 130 | 17 | 13 | -22 | -17 | 100 | 1770 | 0.3 | n/a | n/a | n/a | SCREEN-GATE ONLY (stage A; no placebo/WF/stack) |
| ZB | nyam | supertrend_flip | {'k': 15, 'n': 10, 'm': 2} | usd1200_1.5R_60 | 421 | 110 | 110 | -0 | 6 | 19 | -56 | 46 | 1729 | 0.1 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | nyam | supertrend_flip | {'k': 15, 'n': 14, 'm': 2} | usd1200_1.5R_60 | 456 | 104 | 104 | -6 | 24 | 53 | -46 | 15 | 1417 | 0.7 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | nyam | supertrend_flip | {'k': 3, 'n': 5, 'm': 4} | usd1200_1.5R_60 | 587 | 178 | 208 | -8 | 5 | 25 | -53 | -28 | 2150 | 0.1 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | nyam | supertrend_flip | {'k': 10, 'n': 5, 'm': 3} | usd1200_1.5R_60 | 308 | 30 | 30 | -3 | -8 | -68 | -30 | -13 | 1859 | -0.2 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | pre | supertrend_flip | {'k': 3, 'n': 5, 'm': 3} | usd1200_1.5R_60 | 452 | -5 | -8 | -3 | -13 | -43 | -137 | 64 | 1665 | -0.3 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | nyam | supertrend_flip | {'k': 10, 'n': 14, 'm': 4} | atr3_1.5R_60 | 293 | 46 | 46 | -12 | -14 | 175 | -140 | -488 | 6997 | -0.1 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | nyam | supertrend_flip | {'k': 10, 'n': 10, 'm': 3} | usd1200_1.5R_60 | 339 | 111 | 111 | -14 | -15 | -55 | -65 | 1 | 2271 | -0.3 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | nyam | supertrend_flip | {'k': 10, 'n': 14, 'm': 4} | usd1200_1.5R_60 | 286 | 12 | 12 | -2 | -17 | 27 | -29 | -118 | 1698 | -0.4 | n/a | n/a | n/a | SCREEN (fails older-window gate) |
| ZB | nyam | supertrend_flip | {'k': 10, 'n': 14, 'm': 3} | usd1200_1.5R_60 | 367 | 124 | 124 | -17 | 15 | 104 | -46 | 48 | 1325 | 0.5 | n/a | n/a | n/a | SCREEN (fails older-window gate) |

Columns L1M..X' are net $/week (carry dropped) at the cell's own lots, rank = min(L3M, L6M, HOLD). Stage-B (300 x 84 brackets) and the evaluator (placebos, walk-forward, stack correlation, 13-year check) follow; finalist trade frames go to /mnt/l2/l2vast/instr2_trades/ZB/. Rows are screening numbers: best-of-5426, NOT leads.

## Walk-forward selector diagnostic (Z2 wf_selector.py, weekly equal-risk matrix of all 25,200 stage-B cells; trailing 26 and 52 weeks, purge 1 week, top-1/top-3; Z3 2026-11-05T20:47Z)
Out-of-sample mean USD/week of the monthly re-selected cell, by session and lookback (details: l2vast/ds3/out/instr2/ZB/WF.pkl): negative or zero in all 12 session x lookback combinations (no combination is positive; several are exactly 0 because no candidate was eligible). The selector does not rescue any ZB book: the parameter choice does not carry forward.

## Plain sentence (ZB)
No ZB book on its own grid clears the diversifier bar: of 30 finalists none passes the tolerant gate with placebo, walk-forward and stack checks, every recent positive is NOW-ONLY/regime (0 of 60 tested cells positive in most pre-2023 years), and a one-tick cost change flips the sign of the best screen cell; ZB is DEAD for this grid (ranked table above), not a lead. Base for numbers: library families, evaluator basis, 2023-04..2026-10-16, USD 1,200 risk, carrying weeks dropped.
