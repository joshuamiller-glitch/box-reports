# NEGBOOK_LOG (W-NEGBOOK, order 14:45Z; started 15:00Z 27 Nov)
Method: (A) every signal event of the cell library (Test 5 qualifier cells 3,300 Asia/NY AM + London/NY PM, supertrend/PSAR/Heikin/HMA/EMA-flip family x 28 rows x full GRID, live books' signal events) dumped per bar row on server C (code/th_negbook/ev_extract.py, same filters as th_planas/cell_sigs.py).
(B) first-passage table on the 1-s NQ path for EVERY entry second, both sides (fp_table.py): time to +5/+8/+10/+15 and to -20/-30/-45/-60/-90 (hi/lo of the 1-s bar, same-second tie = loss, entry = open of the second after the signal +1 tick adverse, fee 0.24 pt, stop slip 0.25 pt, bell = session end).
(C) matched random control (ctl.py): random entries every minute of every session window both sides, keyed session x 15-min offset-to-bell x side x trailing-30-min-range tercile x 13-week block; EXCESS = event outcome minus the control mean of its own key.
(D) weekly sums per (cell,session,mode) -> walk-forward qualification, ranking, loser anatomy.
Nice: C is saturated (load 240 on 128 cores, 12,000% at nice 0), my jobs run at nice 8.
