# DS3_INSTR2_6J (ZL-1, T-INSTR-2 6J stage B, own-parameter grid keltner / supertrend / momentum_vote / pullback_band / hma_vwap; 2026-11-05). Research only. No PASS claim. Shadow only.
**Plain sentence: no 6J book from these five families clears the diversifier bar: of 82,152 cells only 2.6% are NOW-ONLY (yen futures lost in almost every cell: median cell L6M -$257 a week, costs at 1-2 ticks dominate small ATRs), the 30 tolerant finalists are small (L6M +$0-120 a week), have placebo p_book 0.12-0.99 (none <= .10), family p 0.39-1.00 (none <= .10), only 2 of 30 have a positive walk-forward at both lookbacks and the 13-year percent-frame check is negative in most years: REGIME-ONLY / best-of-F, no lead; correlation to the NQ stack at most 0.27.**
Scope T2_6EJ_ZL1_scope.md (sha256 d75d3cc897c244b55a30af74e6b5ca2a09732c4901e3bba816132779f8e5196c; DECISIONS.md, before any ZL-1 cell); Z3 stage A (all 16 library families x 6 sessions x 2 brackets) is separate (l2vast/ds3/out/instr2/6J/, T2_Z3_addendum1.md sha256 2693abea...). Code l2vast/ds3/code/t2cl/ (t2_grid.py, t2_stage2.py, t2_stage3.py, t2_finish.py), library instr2/families.py (look-ahead audit PASS), evaluator instr2_eval.py. Output /mnt/l2/l2vast/instr2_6j/. Ledger T2_6J 82152 rows; rows FADE_ROWS_T2_6J.md; finalist trade frames /mnt/l2/l2vast/instr2_trades/6J/ (30); all-instrument n_tested registry 1,867,095. 6J has purchased 1-s data 2023-04..2026-10 (not used: no finalist cleared the 1-minute stage).
## Stage 1 - 82152 cells
NOW-ONLY (L3M and L6M > 0) 2118 (2.6%); tolerant-lite 719 (0.9%); positive in all eight windows 1; tolerant with persistence > 60% and n >= 100: 355; median cell L6M $-257/wk.
| family | cells | NOW-ONLY share | tolerant-lite share | median L6M $/wk | median HOLD $/wk |
|--|--|--|--|--|--|
| hma_vwap_cross | 1512 | 0.0% | 0.0% | -456 | -409 |
| keltner_flip | 50400 | 2.5% | 1.1% | -285 | -312 |
| momentum_vote | 2520 | 0.2% | 0.0% | -448 | -529 |
| pullback_band | 2520 | 0.9% | 0.0% | -515 | -496 |
| supertrend_flip | 25200 | 3.2% | 0.7% | -180 | -197 |

| session | cells | NOW-ONLY share | tolerant-lite share | median L6M |
|--|--|--|--|--|
| asia | 16128 | 6.1% | 2.0% | -314 |
| london | 16380 | 0.1% | 0.1% | -542 |
| nyam | 16632 | 1.2% | 0.2% | -277 |
| nypm | 16380 | 4.8% | 1.9% | -140 |
| pre | 16632 | 0.8% | 0.2% | -145 |

## Stage 2 - 30 finalists through instr2_eval.evaluate
placebos x100 (shift5 forward-only, random side, shuffled day), p_family = max-statistic over the 30 finalists (LOWER BOUND for the whole grid), walk-forward over up to 40 neighbouring parameter sets (trailing 6/12 months), corr vs the Q1-A ts2 stack (V0, V2). gate_v2a pass 1 of 30, p_book <= .10: 0, p_family <= .10: 0, walk-forward positive at both lookbacks: 2, all-criteria clear: 0, max corr to stack 0.27.
| family | session | params | bracket | n | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | gate_v2a | p_book | p_family | max corr |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| keltner_flip | asia | {'k': 5, 'n': 8, 'n_atr': 14, 'mult': 2. | ('atr', 2) 1R T60 | 454 | -80 | -45 | -9 | -99 | -75 | -80 | -267 | 1175 | n | 0.12 | 0.51 | 0.21 |
| keltner_flip | london | {'k': 10, 'n': 14, 'n_atr': 7, 'mult': 2 | ('atr', 2) 1R T120 | 325 | 44 | 150 | -27 | -67 | -39 | -54 | -163 | 1813 | n | 0.20 | 0.90 | 0.08 |
| keltner_flip | asia | {'k': 5, 'n': 8, 'n_atr': 14, 'mult': 2. | ('atr', 2) 1R T120 | 454 | -45 | -40 | -17 | -110 | -98 | -65 | -158 | 1300 | n | 0.26 | 0.85 | 0.20 |
| keltner_flip | asia | {'k': 10, 'n': 14, 'n_atr': 7, 'mult': 2 | ('atr', 3) 1R T120 | 414 | -10 | -20 | 16 | -128 | 2 | -205 | -250 | 1350 | n | 0.30 | 1.00 | 0.05 |
| keltner_flip | london | {'k': 10, 'n': 14, 'n_atr': 7, 'mult': 2 | ('atr', 2) 1R T60 | 325 | 44 | 150 | -29 | -94 | -36 | -69 | -187 | 1844 | n | 0.31 | 0.98 | 0.08 |
| keltner_flip | asia | {'k': 5, 'n': 8, 'n_atr': 7, 'mult': 2.0 | ('usd', 600) 1.5R T120 | 631 | -35 | -3 | 89 | -57 | -252 | 5 | -157 | 438 | n | 0.50 | 0.98 | 0.26 |
| supertrend_flip | nypm | {'k': 15, 'n': 14, 'm': 3.0} | ('atr', 6) 1.5R T120 | 164 | 325 | 75 | -59 | -89 | -158 | -87 | -23 | 2606 | n | 0.50 | 1.00 | 0.05 |
| keltner_flip | london | {'k': 10, 'n': 8, 'n_atr': 14, 'mult': 2 | ('atr', 2) 1R T120 | 142 | -37 | 69 | 29 | 37 | 150 | 45 | 69 | 844 | n | 0.50 | 0.39 | 0.02 |
(8 finalists with the smallest p_book; all 30 with fail reasons in FADE_ROWS_T2_6J.md.)

## Stage 3 - 13-year percent-frame check of the finalists (1-minute 2013-06..2023-03, per-roll-segment rescale; weekly $ by year)
| family | session | params | bracket | n pre-2023 | mean $/trade | $/wk | years positive | negative every year |
|--|--|--|--|--|--|--|--|--|
| keltner_flip | london | {'k': 10, 'n': 8, 'n_atr': 14, 'mu | ('atr', 2) 1R T120 | 407 | 0.7 | 1 | 5/10 | False |
| keltner_flip | london | {'k': 10, 'n': 8, 'n_atr': 14, 'mu | ('atr', 2) 1R T60 | 407 | -12.9 | -10 | 5/10 | False |
| keltner_flip | asia | {'k': 3, 'n': 8, 'n_atr': 7, 'mult | ('usd', 1200) 1R T120 | 1002 | -12.8 | -25 | 2/11 | False |
| keltner_flip | asia | {'k': 3, 'n': 8, 'n_atr': 7, 'mult | ('usd', 600) 2R T120 | 1002 | -27.6 | -54 | 2/11 | False |
| keltner_flip | london | {'k': 10, 'n': 14, 'n_atr': 7, 'mu | ('atr', 2) 1R T120 | 882 | -26.9 | -47 | 4/11 | False |
| keltner_flip | london | {'k': 10, 'n': 8, 'n_atr': 14, 'mu | ('atr', 2) 1R T30 | 407 | -39.7 | -32 | 3/10 | False |
| keltner_flip | asia | {'k': 5, 'n': 8, 'n_atr': 7, 'mult | ('usd', 600) 1.5R T120 | 1873 | -25.5 | -93 | 1/11 | False |
| keltner_flip | asia | {'k': 3, 'n': 8, 'n_atr': 7, 'mult | ('usd', 600) 1.5R T120 | 1003 | -30.0 | -59 | 2/11 | False |
| keltner_flip | asia | {'k': 10, 'n': 8, 'n_atr': 14, 'mu | ('atr', 3) 1R T60 | 497 | -83.4 | -82 | 1/10 | False |
| keltner_flip | asia | {'k': 10, 'n': 8, 'n_atr': 14, 'mu | ('atr', 2) 1R T60 | 505 | -63.6 | -63 | 1/10 | False |
| keltner_flip | asia | {'k': 10, 'n': 8, 'n_atr': 14, 'mu | ('usd', 600) 1.5R T30 | 482 | -29.8 | -28 | 1/10 | False |
| keltner_flip | asia | {'k': 5, 'n': 8, 'n_atr': 7, 'mult | ('usd', 600) 1R T120 | 1874 | -25.4 | -93 | 1/11 | False |
Summary: 1 of 30 finalists have a positive pre-2023 mean $/trade; 0 are negative in every year with >= 15 trades.

## Limits
1-minute bar simulation throughout (finalists were not re-run on a 1-s tape); fee per Z2 json (label: 6J); stage 1 uses the library bar simulator and stage 2 the evaluator's; several finalists are bracket variants of one signal set; Z2 wf_selector.py not yet applied (stage 2 uses the evaluator's purged walk-forward). Ledger rows carry L6M / HOLD / PRE.
