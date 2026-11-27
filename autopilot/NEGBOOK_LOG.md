# NEGBOOK_LOG (W-NEGBOOK, order 14:45Z; started 15:00Z 27 Nov)
Method: (A) every signal event of the cell library (Test 5 qualifier cells 3,300 Asia/NY AM + London/NY PM, supertrend/PSAR/Heikin/HMA/EMA-flip family x 28 rows x full GRID, live books' signal events) dumped per bar row on server C (code/th_negbook/ev_extract.py, same filters as th_planas/cell_sigs.py).
(B) first-passage table on the 1-s NQ path for EVERY entry second, both sides (fp_table.py): time to +5/+8/+10/+15 and to -20/-30/-45/-60/-90 (hi/lo of the 1-s bar, same-second tie = loss, entry = open of the second after the signal +1 tick adverse, fee 0.24 pt, stop slip 0.25 pt, bell = session end).
(C) matched random control (ctl.py): random entries every minute of every session window both sides, keyed session x 15-min offset-to-bell x side x trailing-30-min-range tercile x 13-week block; EXCESS = event outcome minus the control mean of its own key.
(D) weekly sums per (cell,session,mode) -> walk-forward qualification, ranking, loser anatomy.
Nice: C is saturated (load 240 on 128 cores, 12,000% at nice 0), my jobs run at nice 8.
15:36Z PAUSED by LEAD (Josh 15:17Z). Stopped the xargs launchers on C; in-flight ev_extract (63) and fp_table (pid 1996625 successor, nice 5) left to finish. 110/392 rows extracted. Not started: ctl.py, agg.py, report.py (written, untested). Resume = run in that order. Nothing deleted.
17:53Z two-sided merge done (merge.py): NEGBOOK_TWOSIDED.md. Next if asked: widen jobs.json to full grid (rest of the library), shuffle charge.
17:54Z WIDEN-TO-ALL launched: fused.py over 457 bfl17 rows x all stored modules x all GRID params, + 1 shuffled-timing null twin, nice 5 P=72 on C
18:11Z widened: hosts A (rows_p0), B (p1), S2 207.188.7.103 (p2), C (rows 0-71 in flight + p3); results in each host _negbook/ts_all + ts_null, to be gathered onto C via tar pipe through box1 (no box1 disk)
20:38Z widen partial merge4 posted; remaining rows still running on A,B,dal,C (fused.py, results into host ts_all; gather = tar pipe through box1 then merge4.py on C)
22:09Z widen final-ish: 390 rows, top200 boot, nbtop events written
