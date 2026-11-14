# DS3_CHOP_ACTIONS - what D7 does on a chop call (exact engine, JN05W2 / JN05W2J, all layers ON). W-CH2, built 2026-11-14 21:49Z

**VERDICT (running): 16 cells scored so far; no PASS claimed. See section 2 (oracle ceiling, NON-CAUSAL), section 3 (causal calls), section 5 (placebos).**

## 0. Method
Hook code/th_chop2/chop_hooks.py (outermost, additive; identity: TL3_CH_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL). Actions: A1 stand-down (rest of call) | A2 half size | A3b target x0.67 | A3f chop mode (tgt x.67 + session-mean + 60 min time stop + no same-side re-entry after a loss) | A4 favour K7, others x0.5 | A5 book loss cap x0.5 + stack day-done (n>=8 or <= -6000) | T5/T67/T8 target only (x0.5/.67/.8) | A6x no flip-back ablation. Call versions: O = ORACLE (W-CH1 label_sessions, hindsight, ceiling only), P = previous session was chop, Y = same session yesterday chop, M/R/C/Rg/Y/A + h = W-CH1 causal calls at h minutes, DP/DS = W-CH1 D7-dollar calls, R<var><q> = lowest range-forecast bucket (one-sided), RH = HIGH-forecast tail (separate arm). Months before a call file starts are inert (=reference).
Columns: dd/ww in $ per week series (engine base lots, live = x1.75); dd_cut % vs reference; dd44 = same with 2026-W44 removed; best5 = share of reference best-5 weeks kept; w2l = reference winning weeks turned losing; cuts_wk = StateCut exits per week.

## 2. ORACLE (non-causal ceiling, NOT a result)
### L1M
(no cell has this window yet)

### L3M
(no cell has this window yet)

### L6M
(no cell has this window yet)

### HOLD
(no cell has this window yet)

### PRE
(no cell has this window yet)

### X'
(no cell has this window yet)

### GAP
(no cell has this window yet)

## 3. Causal / stand-in calls
### L1M
| cell               |   weeks |   mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   d_mean44 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-------------------|--------:|-------:|---------:|--------:|---------:|---------:|-----------:|-----------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_CH_RHaq3_T5    |       4 |  606.3 |      0   | 36370.5 |  36370.5 |        0 |        nan |        0   | -36370.5 | -36370.5 |     1   |     0 |      55   |            56 |  149.8 |      149.5 |
| TL3_CH_RHaq3_T67   |       4 |  606.3 |      0   | 36370.5 |  36370.5 |        0 |        nan |        0   | -36370.5 | -36370.5 |     1   |     0 |      55   |            56 |  149.5 |      149.5 |
| TL3_CH_RHaq3_T8    |       4 |  606.3 |      0   | 36370.5 |  36370.5 |        0 |        nan |        0   | -36370.5 | -36370.5 |     1   |     0 |      56   |            56 |  149.5 |      149.5 |
| TL3_CH_RHaq3_T67t  |       4 |  606.3 |      0   | 36370.5 |  36370.5 |        0 |        nan |        0   | -36370.5 | -36370.5 |     1   |     0 |      54.8 |            56 |  149.8 |      149.5 |
| TL3_CH_RHaq10_T5   |       4 |  606.3 |      0   | 36370.5 |  36370.5 |        0 |        nan |        0   | -36370.5 | -36370.5 |     1   |     0 |      56   |            56 |  149.5 |      149.5 |
| TL3_CH_RHaq10_T8   |       4 |  606.3 |      0   | 36370.5 |  36370.5 |        0 |        nan |        0   | -36370.5 | -36370.5 |     1   |     0 |      56   |            56 |  149.5 |      149.5 |
| TL3_CH_RHcq3_T5    |       4 | -425.6 |  -1031.8 | 36370.5 |  36370.5 |        0 |        nan |    -1375.8 | -36370.5 | -36370.5 |    -0.7 |     0 |      59.2 |            56 |  167.5 |      149.5 |
| TL3_CH_RHcq3_T67   |       4 |  125.6 |   -480.7 | 36370.5 |  36370.5 |        0 |        nan |     -641   | -36370.5 | -36370.5 |     0.2 |     0 |      57.8 |            56 |  158.2 |      149.5 |
| TL3_CH_S90f33_T67  |       4 | 1548.1 |    941.8 | 36370.5 |  36370.5 |        0 |        nan |     1255.8 | -36370.5 | -36370.5 |     2.6 |     0 |      56.2 |            56 |  151.2 |      149.5 |
| TL3_CH_S90f33F_A2  |       4 |  606.3 |      0   | 36370.5 |  36370.5 |        0 |        nan |        0   | -36370.5 | -36370.5 |     1   |     0 |      56   |            56 |  149.5 |      149.5 |
| TL3_CH_S90f33F_T67 |       4 |  199   |   -407.3 | 36370.5 |  36370.5 |        0 |        nan |     -543.1 | -36370.5 | -36370.5 |     0.3 |     0 |      56.2 |            56 |  149.8 |      149.5 |
| TL3_CH_S90f33F_A1  |       4 | -233.8 |   -840.1 | 36370.5 |  36370.5 |        0 |        nan |    -1120.2 | -36370.5 | -36370.5 |    -0.4 |     0 |      56.2 |            56 |  149.2 |      149.5 |
| TL3_CH_S90f40_A1   |       4 | 4114.1 |   3507.8 | 36370.5 |  36370.5 |        0 |        nan |     4677   | -36370.5 | -36370.5 |     6.8 |     0 |      51.2 |            56 |  143.2 |      149.5 |
| TL3_CH_K790f33_A5  |       4 |  606.3 |      0   | 36370.5 |  36370.5 |        0 |        nan |        0   | -36370.5 | -36370.5 |     1   |     0 |      54   |            56 |  146   |      149.5 |

### L3M
| cell               |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   d_mean44 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-------------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-----------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_CH_RHaq3_T5    |      13 | 17075.3 |   1060.1 | 36370.5 |  36370.5 |      0   |       22.2 |     1148.4 | -36370.5 | -36370.5 |     1   |     0 |      50.8 |          52.5 |  147.2 |      144.2 |
| TL3_CH_RHaq3_T67   |      13 | 17356.5 |   1341.3 | 36370.5 |  36370.5 |      0   |       30.1 |     1453.1 | -36370.5 | -36370.5 |     1   |     0 |      52.4 |          52.5 |  148.6 |      144.2 |
| TL3_CH_RHaq3_T8    |      13 | 16746.3 |    731.1 | 36370.5 |  36370.5 |      0   |       16.4 |      792   | -36370.5 | -36370.5 |     1   |     0 |      51.9 |          52.5 |  144.9 |      144.2 |
| TL3_CH_RHaq3_T67t  |      13 | 16391.4 |    376.2 | 36370.5 |  36370.5 |      0   |       -4.9 |      407.6 | -36370.5 | -36370.5 |     1   |     0 |      50.6 |          52.5 |  144.3 |      144.2 |
| TL3_CH_RHaq10_T5   |      13 | 16015.2 |      0   | 36370.5 |  36370.5 |      0   |        0   |        0   | -36370.5 | -36370.5 |     1   |     0 |      52.5 |          52.5 |  146.8 |      144.2 |
| TL3_CH_RHaq10_T8   |      13 | 16015.2 |      0   | 36370.5 |  36370.5 |      0   |        0   |        0   | -36370.5 | -36370.5 |     1   |     0 |      51.9 |          52.5 |  143.8 |      144.2 |
| TL3_CH_RHcq3_T5    |      13 | 14374.4 |  -1640.8 | 36370.5 |  36370.5 |      0   |       11.3 |    -1777.5 | -36370.5 | -36370.5 |     0.9 |     0 |      53.5 |          52.5 |  153.4 |      144.2 |
| TL3_CH_RHcq3_T67   |      13 | 14954.6 |  -1060.6 | 36370.5 |  36370.5 |      0   |       38.1 |    -1148.9 | -36370.5 | -36370.5 |     0.9 |     0 |      53.2 |          52.5 |  148.7 |      144.2 |
| TL3_CH_S90f33_T67  |      13 | 15782.2 |   -233   | 36370.5 |  36370.5 |      0   |       24.7 |     -252.4 | -36370.5 | -36370.5 |     0.9 |     0 |      52.7 |          52.5 |  148.7 |      144.2 |
| TL3_CH_S90f33F_A2  |      13 | 16461.5 |    446.3 | 36370.5 |  36370.5 |      0   |       -3.9 |      483.4 | -36370.5 | -36370.5 |     1   |     0 |      52.5 |          52.5 |  144.3 |      144.2 |
| TL3_CH_S90f33F_T67 |      13 | 16452.5 |    437.4 | 36370.5 |  36370.5 |      0   |       -2.6 |      473.8 | -36370.5 | -36370.5 |     1   |     0 |      52.4 |          52.5 |  144.7 |      144.2 |
| TL3_CH_S90f33F_A1  |      13 | 16696.7 |    681.5 | 36370.5 |  36370.5 |      0   |       -6.1 |      738.3 | -36370.5 | -36370.5 |     1.1 |     0 |      52.1 |          52.5 |  143.3 |      144.2 |
| TL3_CH_K790f33_A5  |      13 | 17715   |   1699.8 | 36370.5 |  36370.5 |      0   |       14.8 |     1841.4 | -36370.5 | -36370.5 |     1   |     0 |      48.9 |          52.5 |  137.8 |      144.2 |
| TL3_CH_S90f40_A1   |      13 | 15999.4 |    -15.8 | 44557.3 |  36370.5 |    -22.5 |      -45.9 |      -17.1 | -36370.5 | -36370.5 |     0.9 |     0 |      45.3 |          52.5 |  127.8 |      144.2 |

### L6M
(no cell has this window yet)

### HOLD
(no cell has this window yet)

### PRE
(no cell has this window yet)

### X'
(no cell has this window yet)

### GAP
| cell              |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   d_mean44 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:------------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-----------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_CH_RHaq3_T67t |      18 | 13019.7 |    643.4 | 68946.5 |  68946.5 |        0 |        nan |        nan | -68946.5 | -68946.5 |       1 |     0 |      24.8 |          25.7 |   95.7 |       93.2 |
| TL3_CH_RHaq10_T5  |      18 | 12376.3 |      0   | 68946.5 |  68946.5 |        0 |        nan |        nan | -68946.5 | -68946.5 |       1 |     0 |      25.7 |          25.7 |   93.2 |       93.2 |
| TL3_CH_RHaq10_T8  |      18 | 12376.3 |      0   | 68946.5 |  68946.5 |        0 |        nan |        nan | -68946.5 | -68946.5 |       1 |     0 |      25.7 |          25.7 |   93.2 |       93.2 |
| TL3_CH_RHcq10_T5  |      18 | 12542.1 |    165.8 | 68946.5 |  68946.5 |        0 |        nan |        nan | -68946.5 | -68946.5 |       1 |     0 |      25.3 |          25.7 |   92.4 |       93.2 |
| TL3_CH_RHcq10_T67 |      18 | 12513.9 |    137.6 | 68946.5 |  68946.5 |        0 |        nan |        nan | -68946.5 | -68946.5 |       1 |     0 |      25.7 |          25.7 |   93.7 |       93.2 |

## 5. Exact placebos (same action, same frequency per session type; shift 11/23/37 sessions forward, 3 permutations within month x session)
(placebo cells pending)
