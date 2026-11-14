# DS3_CHOP_ACTIONS - what D7 does on a chop call (exact engine, JN05W2 / JN05W2J, all layers ON). W-CH2, built 2026-11-14 19:15Z

**VERDICT (running): 4 cells scored so far; no PASS claimed. See section 2 (oracle ceiling, NON-CAUSAL), section 3 (causal calls), section 5 (placebos).**

## 0. Method
Hook code/th_chop2/chop_hooks.py (outermost, additive; identity: TL3_CH_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL). Actions: A1 stand-down (rest of call) | A2 half size | A3b target x0.67 | A3f chop mode (tgt x.67 + session-mean + 60 min time stop + no same-side re-entry after a loss) | A4 favour K7, others x0.5 | A5 book loss cap x0.5 + stack day-done (n>=8 or <= -6000) | T5/T67/T8 target only (x0.5/.67/.8) | A6x no flip-back ablation. Call versions: O = ORACLE (W-CH1 label_sessions, hindsight, ceiling only), P = previous session was chop, Y = same session yesterday chop, M/R/C/Rg/Y/A + h = W-CH1 causal calls at h minutes, DP/DS = W-CH1 D7-dollar calls, R<var><q> = lowest range-forecast bucket (one-sided), RH = HIGH-forecast tail (separate arm). Months before a call file starts are inert (=reference).
Columns: dd/ww in $ per week series (engine base lots, live = x1.75); dd_cut % vs reference; dd44 = same with 2026-W44 removed; best5 = share of reference best-5 weeks kept; w2l = reference winning weeks turned losing; cuts_wk = StateCut exits per week.

## 2. ORACLE (non-causal ceiling, NOT a result)
### L1M
| cell         |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   d_mean44 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-----------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_CH_O_A1  |       4 | -3239.3 |  -3845.6 | 36370.5 |  36370.5 |        0 |        nan |    -5127.5 | -36370.5 | -36370.5 |    -5.3 |     0 |      48.2 |            56 |  129.5 |      149.5 |
| TL3_CH_O_A2  |       4 | -1601.6 |  -2207.9 | 36370.5 |  36370.5 |        0 |        nan |    -2943.8 | -36370.5 | -36370.5 |    -2.6 |     0 |      55.8 |            56 |  147.5 |      149.5 |
| TL3_CH_O_A3m |       4 |   146   |   -460.3 | 36370.5 |  36370.5 |        0 |        nan |     -613.7 | -36370.5 | -36370.5 |     0.2 |     0 |      56   |            56 |  150   |      149.5 |
| TL3_CH_O_A5  |       4 | -3239.3 |  -3845.6 | 36370.5 |  36370.5 |        0 |        nan |    -5127.5 | -36370.5 | -36370.5 |    -5.3 |     0 |      48.8 |            56 |  133.2 |      149.5 |

### L3M
| cell        |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   d_mean44 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-----------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_CH_O_A1 |      13 | 18589.7 |   2574.5 | 36370.5 |  36370.5 |        0 |       82.6 |       2789 | -36370.5 | -36370.5 |       1 |     0 |      36.4 |          52.5 |  107.7 |      144.2 |

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

## 5. Exact placebos (same action, same frequency per session type; shift 11/23/37 sessions forward, 3 permutations within month x session)
(placebo cells pending)
