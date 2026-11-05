# DS3_INSTR2_6E (ZL-1, T-INSTR-2 6E stage B, own-parameter grid keltner / supertrend / momentum_vote / pullback_band / hma_vwap; 2026-11-05). Research only. No PASS claim. Shadow only.
**Plain sentence: no 6E book from these five families clears the diversifier bar: of 65,835 cells 11.9% are NOW-ONLY, the winners are all pre-market (08:30-09:30 ET) 3-5 minute Supertrend / Keltner cells (L6M +$100-540 a week) that lost money in 2024-25 (PRE -$150 to -$510) and in every earlier year but one or two (13-year percent-frame check: mean per trade -$16 to -$150), the 30 finalists have placebo p_book 0.13-0.92 (none <= .10), family p 0.36-1.00 (none <= .10), no walk-forward positive at both lookbacks (0 of 30), correlation to the NQ stack at most 0.23: REGIME-ONLY / best-of-F, no lead.**
Scope T2_6EJ_ZL1_scope.md (sha256 d75d3cc897c244b55a30af74e6b5ca2a09732c4901e3bba816132779f8e5196c; DECISIONS.md, before any ZL-1 cell); Z3 stage A (all 16 library families x 6 sessions x 2 brackets) is separate (l2vast/ds3/out/instr2/6E/, T2_Z3_addendum1.md sha256 2693abea...). Code l2vast/ds3/code/t2cl/ (t2_grid.py, t2_stage2.py, t2_stage3.py, t2_finish.py), library instr2/families.py (look-ahead audit PASS), evaluator instr2_eval.py. Output /mnt/l2/l2vast/instr2_6e/. Ledger T2_6E 65835 rows; rows FADE_ROWS_T2_6E.md; finalist trade frames /mnt/l2/l2vast/instr2_trades/6E/ (30); all-instrument n_tested registry 1,643,823. 
## Stage 1 - 65835 cells
NOW-ONLY (L3M and L6M > 0) 7837 (11.9%); tolerant-lite 2982 (4.5%); positive in all eight windows 36; tolerant with persistence > 60% and n >= 100: 1826; median cell L6M $-197/wk.
| family | cells | NOW-ONLY share | tolerant-lite share | median L6M $/wk | median HOLD $/wk |
|--|--|--|--|--|--|
| hma_vwap_cross | 1512 | 8.5% | 2.1% | -221 | -292 |
| keltner_flip | 40131 | 9.6% | 3.2% | -223 | -266 |
| momentum_vote | 2016 | 10.1% | 5.7% | -234 | -290 |
| pullback_band | 2016 | 4.0% | 1.8% | -345 | -402 |
| supertrend_flip | 20160 | 17.7% | 7.6% | -133 | -158 |

| session | cells | NOW-ONLY share | tolerant-lite share | median L6M |
|--|--|--|--|--|
| london | 16380 | 2.6% | 0.7% | -566 |
| nyam | 16506 | 2.8% | 1.7% | -314 |
| nypm | 16317 | 10.4% | 2.3% | -88 |
| pre | 16632 | 31.5% | 13.3% | -33 |

## Stage 2 - 30 finalists through instr2_eval.evaluate
placebos x100 (shift5 forward-only, random side, shuffled day), p_family = max-statistic over the 30 finalists (LOWER BOUND for the whole grid), walk-forward over up to 40 neighbouring parameter sets (trailing 6/12 months), corr vs the Q1-A ts2 stack (V0, V2). gate_v2a pass 5 of 30, p_book <= .10: 0, p_family <= .10: 0, walk-forward positive at both lookbacks: 0, all-criteria clear: 0, max corr to stack 0.23.
| family | session | params | bracket | n | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | gate_v2a | p_book | p_family | max corr |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| supertrend_flip | nyam | {'k': 15, 'n': 14, 'm': 4.0} | ('atr', 2) 1R T120 | 218 | 320 | 320 | 156 | 35 | 246 | -231 | -191 | 1628 | n | 0.13 | 0.80 | 0.03 |
| supertrend_flip | pre | {'k': 5, 'n': 7, 'm': 3.0} | ('atr', 2) 1R T60 | 411 | 508 | 565 | 182 | 60 | 423 | -438 | 85 | 2023 | n | 0.14 | 0.36 | 0.14 |
| supertrend_flip | pre | {'k': 5, 'n': 14, 'm': 3.0} | ('usd', 2400) 2R T60 | 409 | 58 | 64 | 23 | 13 | 46 | -63 | 51 | 292 | n | 0.17 | 0.85 | 0.23 |
| supertrend_flip | pre | {'k': 5, 'n': 14, 'm': 3.0} | ('usd', 1200) 1.5R T60 | 409 | 58 | 64 | 23 | 13 | 46 | -63 | 51 | 292 | n | 0.17 | 0.85 | 0.23 |
| supertrend_flip | pre | {'k': 5, 'n': 7, 'm': 3.0} | ('atr', 6) 1.5R T60 | 375 | 123 | 144 | 96 | 54 | 128 | -166 | 108 | 721 | n | 0.19 | 0.52 | 0.14 |
| supertrend_flip | pre | {'k': 5, 'n': 7, 'm': 3.0} | ('atr', 6) 2R T60 | 375 | 123 | 144 | 96 | 54 | 128 | -178 | 108 | 721 | n | 0.19 | 0.51 | 0.15 |
| supertrend_flip | pre | {'k': 5, 'n': 10, 'm': 3.0} | ('atr', 2) 1R T60 | 444 | 508 | 565 | 114 | 8 | 255 | -465 | -39 | 2937 | n | 0.22 | 0.72 | 0.16 |
| supertrend_flip | pre | {'k': 5, 'n': 14, 'm': 3.0} | ('atr', 4) 1R T60 | 423 | 251 | 282 | 160 | 120 | 147 | -307 | 220 | 1723 | n | 0.22 | 0.47 | 0.22 |
(8 finalists with the smallest p_book; all 30 with fail reasons in FADE_ROWS_T2_6E.md.)

## Stage 3 - 13-year percent-frame check of the finalists (1-minute 2013-06..2023-03, per-roll-segment rescale; weekly $ by year)
| family | session | params | bracket | n pre-2023 | mean $/trade | $/wk | years positive | negative every year |
|--|--|--|--|--|--|--|--|--|
| supertrend_flip | pre | {'k': 3, 'n': 5, 'm': 4.0} | ('atr', 3) 2R T120 | 974 | -112.7 | -214 | 2/11 | False |
| supertrend_flip | pre | {'k': 3, 'n': 7, 'm': 4.0} | ('atr', 3) 1.5R T120 | 990 | -79.1 | -153 | 3/11 | False |
| supertrend_flip | pre | {'k': 3, 'n': 7, 'm': 4.0} | ('atr', 4) 1.5R T120 | 968 | -83.9 | -159 | 4/11 | False |
| supertrend_flip | pre | {'k': 3, 'n': 7, 'm': 4.0} | ('atr', 4) 1R T120 | 968 | -56.3 | -106 | 2/11 | False |
| supertrend_flip | pre | {'k': 5, 'n': 7, 'm': 3.0} | ('atr', 2) 1R T60 | 967 | -136.4 | -257 | 2/11 | False |
| supertrend_flip | pre | {'k': 3, 'n': 5, 'm': 4.0} | ('atr', 3) 1.5R T120 | 974 | -92.3 | -175 | 1/11 | False |
| supertrend_flip | pre | {'k': 3, 'n': 5, 'm': 4.0} | ('atr', 3) 1R T120 | 974 | -70.7 | -134 | 2/11 | False |
| supertrend_flip | pre | {'k': 5, 'n': 14, 'm': 3.0} | ('atr', 4) 1R T60 | 973 | -87.3 | -166 | 1/11 | False |
| supertrend_flip | nyam | {'k': 15, 'n': 14, 'm': 4.0} | ('atr', 2) 1R T120 | 502 | -127.2 | -125 | 2/10 | False |
| supertrend_flip | pre | {'k': 5, 'n': 7, 'm': 3.0} | ('atr', 6) 1.5R T60 | 904 | -49.1 | -87 | 2/11 | False |
| supertrend_flip | pre | {'k': 5, 'n': 7, 'm': 3.0} | ('atr', 6) 2R T60 | 904 | -51.8 | -91 | 2/11 | False |
| supertrend_flip | pre | {'k': 15, 'n': 14, 'm': 1.5} | ('atr', 4) 1R T120 | 926 | -64.3 | -116 | 2/11 | False |
Summary: 0 of 30 finalists have a positive pre-2023 mean $/trade; 3 are negative in every year with >= 15 trades.

## Limits
1-minute bar simulation throughout (finalists were not re-run on a 1-s tape); fee per Z2 json (label: 6E); stage 1 uses the library bar simulator and stage 2 the evaluator's; several finalists are bracket variants of one signal set; Z2 wf_selector.py not yet applied (stage 2 uses the evaluator's purged walk-forward). Ledger rows carry L6M / HOLD / PRE.
