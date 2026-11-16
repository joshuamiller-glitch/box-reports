# DS3_REBUILD_S5 - T-REBUILD stage 5: leave-one-out audit of every live layer on JL2 (W-PM). DESIGN PAGE, no engine result yet.

VERDICT (data ends 2026-10-30; DESIGN ONLY, nothing run): stage 5 is about 28 leave-one-out cells plus about 18 persistent-draw controls on the JL2 base (46 cells; 1,978 cell-months for 43 months, 552 for the recent L6M + HOLD tier first); reference rows only, nothing is removed from live; it waits for W-EV's switch list (some layers have no switch yet: NKD take, BREADTH, NTZ, profit lines) and server 2.

## Layers (live list, ANSWER_LIVE_LAYERS_20261116.md) and the switch to turn each OFF on JL2
1 governor / WL_E1 (c_gov gov []); 2 ATR-SKIP (ev_panel atr_skip removed); 3 DAY-DONE C22 (scr_hooks entry removed); 4 stack cut 50% Asia-only (pm_hooks sc off); 5 JN04 stack cap 10 lots London (cde key removed; JL2 has cap 6 London in the cde key, to be stated); 6 NTZ half size within 20 pts (switch needed from W-EV); 7 BREADTH P7 15 min (switch needed); 8 P7 post-exit blackout 30 min (ev_panel bo removed); 9 NKD take P7,U7 at 0.80 (not in JL2: adding it is a different test, flagged); 10-12 JN04 LOT, SIGQ, REG on P7 (ev_switch lot_off, sigq_off, reg_off); 13 K7 flat -45 (ec_hooks rule removed); 14 P7 flat -42 (live from 11-12; not in JL2); 15-21 book cut lines: the state cut off per book (K7 P7 M7 U7 H7 A7 O7, 7 cells); 22-24 profit lines (K7 delta_mult lock, M7 tot_rel step, U7 delta_mult tighten, 3 cells); 25 lot tables / p7_sess; 26 session caps; 27 P7 day cap 8,400 (wb_hooks panel); 28 F3 context cut (wb_hooks ctxcut).

## Also audited (stage 3/4 existing rules, per the addendum)
brackets by forecast (D10 / W-D10 bracket cells: reference rows from their JL2 runs, not new cells), NKD take, stack cut, stack cap, NTZ, breadth skip, blackout, governor, ATR skip, LOT/SIGQ/REG: all already in the 28-cell list above except the forecast brackets.

## Table (per layer, per window L3M L6M HOLD GAP PRE X' ALL43)
worth of the layer = JL2 (layer on) minus leave-one-out: net per week (and x1.75 live, and at $4.84 RT), DD cut by the layer, worst-week change, trades changed. Overlap with other layers = share of the trades changed by layer A that are also changed by layer B (computed from the trade tables, matrix at ALL43 and at HOLD). Layers that skip or shrink get 3 persistent-draw controls (same rate, one persistent random draw per signal across the run, not a per-second redraw) beside the real row; W44-removed DD for L6M. Scorer: code/th_pm/pm_rb.py (s5, worth_row, overlap) already tested on a stand-in cell.

## Budget and order
46 cells: tier A months 202511..202610 (12) = 552 cell-months, tier B the other 31 months = 1,426; total 1,978. With S0 (315) the program is about 2,300 cell-months, about 770 worker-hours (about 26 hours on 30 workers). Queue file /mnt/l2/l2vast/_rebuild/pending.txt, set prefix TL3_RB_S5_<LAYER>; the lead adds the PRIORITY tag RB when the sets are ready.

## Status
Pending: W-EV switch list, server 2.
