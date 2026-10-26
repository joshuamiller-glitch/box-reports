# DS2-50 progress (trackDS50) - append-only
2026-10-22T12:41:14Z PREREG frozen (409 cells / 50 families). Block order: Risk (37-44,48-50) -> Regime/Calendar (16-36) -> Signal (1-15) -> Books (45-47). ETA targets: Risk block scored ~+3h after freeze, Regime ~+7h, Signal ~+12h, Books ~+14h, nulls+report ~+18h (cores <=4 until DS2 tracks finish).
2026-10-22T12:50:26Z Block1 script finished items 49,50
2026-10-22T12:51:45Z Block1 script finished items 39
2026-10-22T12:52:00Z BLOCK 1 (Risk/Accounting 37-44,48-50) scored: 65 cells + 1 comparator, 0 beat benchmark on net AND maxDD in both WF and L8W; 4 pass gate a (item 50 stop-proximity); stage-1 N1 nulls (100 reps) running. Engine validated bit-identical to ds2lib. Next: Regime/Calendar block (ETA ~+4h incl. feature build).
2026-10-22T12:59:23Z Block2 script finished items 34,35,36
2026-10-22T13:00:50Z BLOCK 2 (Regime/Calendar 16-36) scored: 198/198 cells; 33 pass gate a (WF net + maxDD); 14 beat benchmark on net AND maxDD in WF and L8W (before nulls); stage-1 N1 (100 reps) running. NOTE many cells show maxDD delta exactly -75,162 = switch to the 2nd-largest drawdown episode (mechanical), nulls decide. Next: Signal block (row-level 4-8,11-14 then ENGINE 1,2,3,9,10,15).
2026-10-22T13:02:12Z Block3a script finished items 11,12,13,14,4,5,6,7,8
2026-10-22T13:23:09Z Block4 script finished items 45,46,47
2026-10-22T13:23:50Z Block3b script finished items 1,10,15,2,3,9
2026-10-22T13:24:13Z BLOCK 3a/4 scored: Signal row-level (4,5,6,7,8,11-14) 63 cells; New books 45/46/47: 24 cells (+ standalones, NQ minute-bar control WF $32.3k/wk Sh 2.19 vs tick benchmark $37.1k); ES/YM pair standalone strongly negative at market cost and at NQ-relative cost; 3b ENGINE items 15,3,9 done (none beat), 10 done 4/6, items 1,2 running. Stage-2 nulls (500 reps): R22_first3_8 rank .962/.990 beats both windows (LEAD candidate pending gate d); R16 CHOP cells rank_dd .91-.94 (fail c).
2026-10-22T13:32:17Z ALL BLOCKS DONE. REPORT_DS2_50.md written; 0 gate a-d passers; P9 table swappable (F50_P9PTS); rescore on corrected table when lead verifies.
2026-10-22T13:48:20Z Block3a script finished items 11,12,13,14,4,5,6,7,8
2026-10-22T13:48:22Z Block1 script finished items 37,38,39,40,41,42,43,44,48,49,50
2026-10-22T13:49:32Z Block4 script finished items 45,46,47
2026-10-22T13:50:17Z Block2 script finished items 16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36
2026-10-22T14:05:01Z Block3b script finished items 1,10,15,2,3,9
2026-10-22T14:19:21Z RESCORE on corrected P9 table complete (corr/): 22 beat-both, 0 gates a-d; REPORT_DS2_50.md updated (corrected primary, as-built secondary).
