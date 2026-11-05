# DS3_INSTR2_CL (ZL-1, T-INSTR-2 CL, 2026-11-05) - WTI crude, own-parameter grid for keltner_flip / supertrend_flip / momentum_vote / pullback_band / hma_vwap_cross. Research only. No PASS claim. Shadow only.
**Plain sentence: no CL book from these five families clears the diversifier bar - of 66,024 cells 23.7% are NOW-ONLY (about the chance rate; the median cell loses $85 a week in L6M), the 30 tolerant finalists have placebo p_book 0.13-0.95 (none <= .10) and family p 0.17-1.00 (none <= .10), none has a walk-forward that is positive at both lookbacks and also improves the stack Calmar, so this is a REGIME-ONLY / best-of-F result; the cells are, however, uncorrelated with the NQ stack (|r| <= 0.12 daily and weekly, V0 and V2), so CL stays a usable diversifier candidate only if an edge is found in the families of BASE-4 block B (donchian / OR / VWAP / prior-day / failed-break).**
Scope T2_CL_scope.md sha256 77e4df99888cda31c5b0fe08ca722d38ba66732c42474208e90953f5d41b1561 + addendum 1 (reduced to these five families; BASE-4 block B covers the others, T2_CL_B_scope.md); both in DECISIONS.md before any CL cell was read. Code l2vast/ds3/code/t2cl/ (cl_grid.py stage 1, cl_stage2.py stage 2), families library instr2/families.py (intraday look-ahead audit PASS), evaluator instr2_eval.py (BASE-4). Output /mnt/l2/l2vast/instr2_cl/. Ledger T2_CL 66,024 rows; all-instrument n_tested registry now 1,075,248 (this grid 66,024); rows FADE_ROWS_T2_CL.md.
Instrument and fills: CL.v.0 volume-front 1-minute, additive back-adjustment, 114 roll days dropped; $1,000/pt, tick 0.01, fee $4.84 RT (PROXY-STD, not in FEES.md); costs entry 1 tick, stop exit 2 ticks, market exit 1 tick (Z2 cost_pts); sessions london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nypm 12:00-15:00 (asia illiquid, close thin: not tested); max lots per 5 minutes london 7, pre 18, nyam 23, nypm 14; integer lots = round($1,200 / ((stop + cost) x $1,000)) clipped to the cap; entry next 1-minute bar open, stop first on an ambiguous bar, flat 16:55 ET, one position at a time per cell. 1-minute bar simulation throughout (no 1-s CL tape was used; nothing cleared).
## Stage 1 - 66,024 cells (264 signal sets x 63 brackets x 4 sessions; cells with < 20 trades dropped)
Windows (weekly $, carry weeks dropped) as instr2_eval. NOW-ONLY (L3M and L6M > 0): 15629 cells (23.7%); tolerant-lite (NOW-ONLY and PRE / X' mean >= -0.5 MDE): 8030 (12.2%); positive in all eight windows: 575; tolerant with persistence > 60% and n >= 100: 6923.
| family | cells | NOW-ONLY share | tolerant-lite share | median L6M $/wk | median HOLD $/wk |
|--|--|--|--|--|--|
| hma_vwap_cross | 1764 | 35.9% | 19.4% | 16 | -17 |
| keltner_flip | 40068 | 24.6% | 11.3% | -102 | -91 |
| momentum_vote | 2016 | 30.0% | 13.6% | -99 | -108 |
| pullback_band | 2016 | 28.3% | 8.1% | -5 | -27 |
| supertrend_flip | 20160 | 19.7% | 13.6% | -71 | -63 |

| session | cells | NOW-ONLY share | tolerant-lite share | median L6M |
|--|--|--|--|--|
| london | 16380 | 34.2% | 10.7% | 28 |
| nyam | 16506 | 28.1% | 18.7% | -95 |
| nypm | 16569 | 13.7% | 5.8% | -192 |
| pre | 16569 | 18.8% | 13.5% | -26 |

Reading: about a quarter of the cells have L3M and L6M both positive (what random cells with correlated windows show), the median cell is negative in every window, the london session (where crude trended in 2026) has the highest NOW-ONLY share but the worst PRE; the 575 cells positive in all eight windows are best-of-66k by construction.
## Stage 2 - 30 finalists (top by min(L3M, L6M, HOLD) / MDE among tolerant-lite, persistence > 60%, n >= 100; at most 3 per signal set and session) through instr2_eval.evaluate
placebos x100 (shift5 forward-only, random side, shuffled day; HOLD, L6M mean and stack gain); p_family = max-statistic over the 30 finalists (a LOWER BOUND on the family p of the 66,024-cell grid; the Bonferroni bound is 1.0 for any p_book > 1.5e-5); purged walk-forward over up to 40 neighbouring parameter sets of the same family, session and bracket (trailing 6 and 12 months -> next month); corr = max |daily, weekly| vs the Q1-A ts2 stack. Summary: gate_v2a pass 7 of 30, p_book <= .10: 0, p_family <= .10: 0, walk-forward positive at both lookbacks: 3, stack Calmar up at equal risk (HOLD and L6M, carry dropped): 9, corr to stack max 0.12.
| family | session | params | bracket | n | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | gate_v2a | p_book | p_family | max corr |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| keltner_flip | pre | {'k': 10, 'n': 21, 'n_atr': 7, 'mult': 2 | ('atr', 6) 1R T120 | 151 | 282 | 282 | 179 | 280 | 670 | 79 | -255 | 345 | n | 0.13 | 0.50 | 0.02 |
| supertrend_flip | nypm | {'k': 15, 'n': 5, 'm': 3.0} | ('usd', 600) 1R T30 | 163 | 160 | 160 | 135 | 168 | 148 | -51 | 56 | 789 | n | 0.15 | 0.40 | 0.04 |
| keltner_flip | london | {'k': 10, 'n': 8, 'n_atr': 14, 'mult': 0 | ('atr', 4) 1R T120 | 2877 | 77 | 482 | 1090 | 863 | 385 | -1284 | -802 | 3397 | n | 0.19 | 0.66 | 0.11 |
| hma_vwap_cross | pre | {'n': 20, 'm': 55, 'k': 1, 'anchor_hm':  | ('usd', 600) 1.5R T30 | 1057 | 615 | 515 | 552 | 529 | 1751 | -406 | -157 | 1939 | n | 0.21 | 0.28 | 0.07 |
| hma_vwap_cross | pre | {'n': 10, 'm': 30, 'k': 5, 'anchor_hm':  | ('usd', 600) 1R T120 | 526 | 385 | 611 | 752 | 487 | 455 | -394 | -179 | 2169 | n | 0.21 | 0.33 | 0.04 |
| hma_vwap_cross | pre | {'n': 20, 'm': 55, 'k': 1, 'anchor_hm':  | ('usd', 600) 1R T30 | 1068 | 415 | 371 | 393 | 304 | 1115 | -447 | 16 | 1899 | n | 0.21 | 0.87 | 0.06 |
| supertrend_flip | london | {'k': 5, 'n': 14, 'm': 3.0} | ('atr', 4) 1.5R T120 | 1707 | 899 | 1037 | 1329 | 560 | 287 | -679 | -726 | 2738 | n | 0.22 | 0.35 | 0.07 |
| keltner_flip | london | {'k': 3, 'n': 14, 'n_atr': 14, 'mult': 2 | ('atr', 6) 1R T120 | 1333 | 1709 | 1442 | 491 | 626 | 1139 | -649 | -312 | 4433 | n | 0.28 | 0.33 | 0.05 |
(the 8 finalists with the smallest p_book; all 30 rows with the full fail reasons are in FADE_ROWS_T2_CL.md.) Typical fail reasons: tolerant gate (PRE or X' mean below -0.5 MDE: the 2026 winners lost money in 2024-25), placebo p_book 0.13-0.95, family p >= 0.17, walk-forward negative OOS at one lookback, stack Calmar not up. The london keltner 5-minute n34 cells (L6M +$1.2k/wk, HOLD +$1.2k) have PRE -$780 and X' -$960 per week; the pre-market hma_vwap cell (L6M +$552) has PRE -$406: REGIME.
## Not done / limits
No pre-2023 percent-frame check (nothing cleared the tolerant + placebo bar, so the 13-year step of the directive was not triggered); no 1-s CL tape re-run (no finalist cleared); CL fee is the standard proxy $4.84; stage 1 uses the library bar simulator and stage 2 the evaluator's (sim_check correlations are in the rows); several of the 30 finalists are bracket variants of the same signal set. BASE-4 block B (donchian, OR, pdhl, failed-break, session-extreme, VWAP) is a separate family and page (DS3_INSTR2_CL_B.md); the all-CL n_tested is theirs plus 66,024. Ledger T2_CL rows carry L6M / HOLD / PRE (X' omitted).
