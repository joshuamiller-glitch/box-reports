# REPORT I5E - execution-form arms of the retrace book (IDEAS-5000 family E)
**Verdict: 0 LEAD, 0 FOUND-PENDING, 0 FOUND.** 512 cells scored (4 books x 2 targets x 4 rules x 16 forms), every row carries its MKT0 market-entry control and its rule. 21 cells were stage-1 selected, 20 beat the own depth-permutation null p95 and had clean uplift >= +0.10 (gate-3 at stage 1: 20 against a chance bound of <= 1.1 even if every selected cell were independent), but they are one mechanism (V1 volume clock, limit cancelled after 1-2 minutes) and all 20 fail H2 (read once): uplift H2 between -0.70 and +0.07, bootstrap lower bound < 0, plateau <= 0.67.
Engine: exec_engine_pp ECONOMICS (exec_engine v1 + same-row price-priority tie-break, see Amendment E-D2 in PREREG_IDEAS5000.md); rules ffw / ooat / nro / stk2 as an explicit factor of every cell; NQ, clean window 2023-08..2025-07 for stage 1 (H1/H2 untouched until stage 3); R-sized USD (9,600 per trade, cap 24 contracts), 1 tick adverse on market entries and stop exits, $4.36 per contract. Registry: outputs/ideas5000/CELLS.csv (latest row per cell_id), TALLY.csv; per-cell tables i5ej_stage1_pp.csv / i5ej_stage3_pp.csv; v1-engine archive i5ej_stage{1,3}_v1engine.csv. Code: code/census/night_ins/ap_i5_ej.py, exec_engine_pp.py.

## An ENGINE DEFECT changed the answer (read this first)
With exec_engine v1 the stage-1/3 result was six LEAD/FOUND-PENDING cells (V1 volume clock, replace-on-move chase CH1/CH2 under first-fill-wins, additive 20% uplift +0.32..0.42 clean, +0.69..0.79 H1, +0.47..1.18 H2, six of six gates, replication 3 of 3). Diagnostic D1 (replace-the-previous-order chase CHR) collapsed the Sharpe (2.4 -> 0.6) and the order logs showed why: when several working orders can fill on the same 1-minute row v1 fills the OLDEST working order (kernel loop over the working list in placement order), not the order the price reaches first. In a chase ladder the oldest orders are the deepest, so a long gets filled at the best price of the bar. With a price-priority tie-break (exec_engine_pp) ladder and replace-chase give identical entries, net R/trade falls from +0.040 to -0.025, and even the plain L0 book under ffw moves from +0.009 to -0.008 R/trade. All E/J cells were re-run on the corrected engine with unchanged cell list and gates; the v1 outputs are archived. Consequence for the project: every ffw / stk result produced with exec_engine v1 for programs with overlapping working orders is optimistic (including the IMP3 baseline -0.049 R/trade reference); the engine owner has been told. Pre-registration: Amendments E-D1 and E-D2 in PREREG_IDEAS5000.md were written before the diagnostic and before the corrected re-run.

## Stage 1 by execution form (corrected engine; clean weekly Sharpe of the 1-contract R-sized program)
| form   |   cells |   median_clean_sharpe |   best_clean_sharpe |   median_netR |   median_fill |   selected |   g3 |
|:-------|--------:|----------------------:|--------------------:|--------------:|--------------:|-----------:|-----:|
| CH1    |      32 |                -2.202 |               0.17  |        -0.047 |         0.228 |          0 |    0 |
| CH2    |      32 |                -2.162 |               0.222 |        -0.045 |         0.239 |          0 |    0 |
| CX1    |      32 |                 0.101 |               0.73  |        -0.026 |         0.041 |          7 |    7 |
| CX10   |      32 |                -0.913 |              -0.278 |        -0.033 |         0.352 |          0 |    0 |
| CX2    |      32 |                -0.122 |               1.128 |        -0.023 |         0.111 |         13 |   13 |
| CX20   |      32 |                -1.309 |              -0.235 |        -0.036 |         0.451 |          0 |    0 |
| CX5    |      32 |                -0.952 |              -0.605 |        -0.042 |         0.255 |          0 |    0 |
| L0     |      32 |                -1.532 |              -0.106 |        -0.036 |         0.55  |          0 |    0 |
| LD2    |      32 |                -0.463 |              -0.238 |        -0.065 |         0.937 |          0 |    0 |
| LD4    |      32 |                -0.955 |               0.512 |        -0.055 |         0.924 |          0 |    0 |
| LD8    |      32 |                -0.844 |               0.355 |        -0.039 |         0.899 |          1 |    0 |
| MK1    |      32 |                -2.657 |              -0.65  |        -0.076 |         0.936 |          0 |    0 |
| SE1    |      32 |                -2.357 |              -0.282 |        -0.048 |         0.838 |          0 |    0 |
| SE2    |      32 |                -2.412 |              -0.335 |        -0.049 |         0.829 |          0 |    0 |
| SE4    |      32 |                -2.278 |              -0.209 |        -0.046 |         0.805 |          0 |    0 |
| SEB    |      32 |                -2.594 |              -0.111 |        -0.052 |         0.96  |          0 |    0 |

Market-entry control arm (MKT0, same bracket) per book / target / rule: clean Sharpe and net R/trade
|                              |   ctrl_sharpe |   ctrl_netR |
|:-----------------------------|--------------:|------------:|
| ('T3_k1.125', '1.5', 'ffw')  |        -5.374 |      -0.048 |
| ('T3_k1.125', '1.5', 'nro')  |        -5.374 |      -0.048 |
| ('T3_k1.125', '1.5', 'ooat') |        -5.374 |      -0.048 |
| ('T3_k1.125', '1.5', 'stk2') |        -4.934 |      -0.041 |
| ('T3_k1.125', '2.0', 'ffw')  |        -2.891 |      -0.039 |
| ('T3_k1.125', '2.0', 'nro')  |        -2.891 |      -0.039 |
| ('T3_k1.125', '2.0', 'ooat') |        -2.891 |      -0.039 |
| ('T3_k1.125', '2.0', 'stk2') |        -2.261 |      -0.028 |
| ('T3_k1.5', '1.5', 'ffw')    |        -4.672 |      -0.044 |
| ('T3_k1.5', '1.5', 'nro')    |        -4.672 |      -0.044 |
| ('T3_k1.5', '1.5', 'ooat')   |        -4.672 |      -0.044 |
| ('T3_k1.5', '1.5', 'stk2')   |        -4.175 |      -0.038 |
| ('T3_k1.5', '2.0', 'ffw')    |        -2.905 |      -0.037 |
| ('T3_k1.5', '2.0', 'nro')    |        -2.905 |      -0.037 |
| ('T3_k1.5', '2.0', 'ooat')   |        -2.905 |      -0.037 |
| ('T3_k1.5', '2.0', 'stk2')   |        -2.328 |      -0.03  |
| ('V1_k1.125', '1.5', 'ffw')  |        -3.941 |      -0.025 |
| ('V1_k1.125', '1.5', 'nro')  |        -3.941 |      -0.025 |
| ('V1_k1.125', '1.5', 'ooat') |        -3.941 |      -0.025 |
| ('V1_k1.125', '1.5', 'stk2') |        -2.66  |      -0.016 |
| ('V1_k1.125', '2.0', 'ffw')  |        -1.991 |      -0.02  |
| ('V1_k1.125', '2.0', 'nro')  |        -1.991 |      -0.02  |
| ('V1_k1.125', '2.0', 'ooat') |        -1.991 |      -0.02  |
| ('V1_k1.125', '2.0', 'stk2') |         0.123 |       0.001 |
| ('V1_k1.5', '1.5', 'ffw')    |        -2.402 |      -0.018 |
| ('V1_k1.5', '1.5', 'nro')    |        -2.402 |      -0.018 |
| ('V1_k1.5', '1.5', 'ooat')   |        -2.402 |      -0.018 |
| ('V1_k1.5', '1.5', 'stk2')   |        -1.834 |      -0.012 |
| ('V1_k1.5', '2.0', 'ffw')    |        -0.968 |      -0.012 |
| ('V1_k1.5', '2.0', 'nro')    |        -0.968 |      -0.012 |
| ('V1_k1.5', '2.0', 'ooat')   |        -0.968 |      -0.012 |
| ('V1_k1.5', '2.0', 'stk2')   |         0.171 |       0.002 |

## Stage 3 (H1/H2 read once; the 23 gate-3 cells of the corrected run)
All 23 have gates_detail 010001 or 010000 (only the worst-week and worst-decile gates pass): uplift H2 <= +0.07 for every cell, bootstrap lo <= 0, plateau <= 0.67, 2x-slippage H2 negative. Table: i5ej_stage3_pp.csv. Replication battery: not reached (a cell needs gates first).

## What was not scored
Sub-minute cancel lifetimes (CX at 15/60 seconds) and tick-level queue positions are not expressible in the 1-minute engine; the mbp-10 skip filters (resting depth at/beyond the limit, imbalance sign) wait for the NQ L2 pipeline (K-L2 watcher). No stage 2 (clock/instrument expansion) was run: nothing passed stage 3, so the expansion rule (expand null-passers) was applied only to the cells that passed stage 3 (none).

## Update (exec_engine v2 confirmation, 2026-10-17)
exec_engine v2 (price-priority merged) re-run of all 1,120 E/J cells with the shared-seed 200-replicate null: results identical to the exec_engine_pp run (max abs difference 0.0 in trades, clean Sharpe, net R, uplift; same selected set 21 E + 8 J, same 23 gate-3 cells, same stage-3 outcome: none survives H2). Null arrays for the global family null: outputs/ideas5000/nulls_E.npz (21 cells x 200) and nulls_J.npz (8 x 200), arrays ids / nulls / obs (clean weekly Sharpe of each depth-permutation world; replicate i uses seed 777000+i for every cell, so the permutation order is shared across cells of the same book).
