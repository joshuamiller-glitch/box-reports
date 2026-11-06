# INSTR_NTESTED - number of books tested per INSTR_* ledger (Bonferroni n_tested for gate_v2 is the SUM over the latest row of each slice)
| utc | slice | owner | n_tested | note |
|--|--|--|--|--|
| 2026-11-03T19:52Z | harness self-test | ZL-2 | 0 | header created by ZL-2; slice owners append one row per ledger update (latest row per slice is summed for Bonferroni) |
| 2026-11-03T19:55Z | INSTR_EQ | Z2 | 264 | ES RTY YM (+NQ ref): 6 books x 3 brackets x 4 sessions; NQ U60 duplicate excluded; cost variants not counted |
| 2026-11-03T19:59Z | INSTR_CM | S4b | 75 | GC CL NKD BTC MBT x K7 U7 H7 x (ALL + 4 sessions); cost/scaling variants not counted |
| 2026-11-03T20:01Z | INSTR_EQ | Z2 | 408 | ES RTY YM + NQ ref: 6 books x 4 sessions x brackets (S60 Z1-f, W60 warm-up k, B60 bps, U60 unscaled, ATR1; NQ S60+ATR1); cost-stress variants not counted |
| 2026-11-03T20:02Z | INSTR_RF | ZL-1 | 534 | ZN/ZB/6E/6J x 7 books x (pooled + NQ-tag sessions + own sessions) x 3 stop mappings (atr/warm/bps) = 534 distinct cells (178 per mapping); costs z1 base and z1_stress |
| 2026-11-03T20:09Z | INSTR_CM | S4b | 245 | interim 2: 5 instruments x 7 books (K7 U7 H7 P7 M7 A7 O7) x (ALL + sessions [+ GC/CL cash 09:00-14:30]) + GC/CL stop x2 variants (ALL + cash); cost/scaling sensitivities not counted |
| 2026-11-03T20:10Z | INSTR_CM | S4b | 245 | interim 2: 5 instruments x 7 books (K7 U7 H7 P7 M7 A7 O7) x (ALL + sessions [+ GC/CL cash 09:00-14:30]) + GC/CL stop x2 variants (ALL + cash); cost/scaling sensitivities not counted |
| 2026-11-03T20:33Z | INSTR_CM | S4b | 245 | interim 2: 5 instruments x 7 books (K7 U7 H7 P7 M7 A7 O7) x (ALL + sessions [+ GC/CL cash 09:00-14:30]) + GC/CL stop x2 variants (ALL + cash); cost/scaling sensitivities not counted |
| 2026-11-03T20:57Z | INSTR_CM | S4b | 255 | interim 2 + O7 (pinned drive-pullback) on 5 instruments x 2 scalings |
| 2026-11-03T20:58Z | INSTR_EQ | Z2 | 420 | 408 + O7 (ES RTY YM x 4 scalings = 12) |
| 2026-11-03T20:58Z | INSTR_CM | S4b | 253 | interim 2 + O7 (pinned drive-pullback) on 4 instruments x 2 scalings (BTC dropped: 09:30 ET has no meaning for crypto and Z1 has no BTC ratio) |
P3_NTESTED: 96 simulated cells (12 books x 8 scenarios), no hypothesis tests; Z2 2026-11-04
P3_NTESTED: 144 simulated cells (prereg 96 + addendum 48 fade at 2 lots), no hypothesis tests; Z2 2026-11-04
DISH_NTESTED: 108 cells (6 books x 3 variants x 3 sizes x 2 cost bases); 120 family worlds + 3x100 placebos on size-1 cells; Z2 2026-11-04
DISK_NTESTED: 278 cells (180 BO + 78 EX + 20 overlay); 120 family worlds + placebos; Z2 2026-11-04
DISK_NTESTED: 356 cells (180 BO + 156 EX + 20 overlay) - supersedes the 278 line above; Z2 2026-11-04
Q7_NTESTED: 288 cells (6 books x 4 offsets x 3 timings x 2 windows x 2 fill models); 120 family worlds + 3x100 placebos; Z2 2026-11-04
Q7_NTESTED_PASS2: 32 cells (8 best pass-1 cells x {TICK_WITH, TICK_AGAINST} + x {Q25, Q100}); total Q7 320; Z2 2026-11-04
DISAZ_NTESTED: 108 cells (6 books x 2 offsets x 3 timeouts x 3 strength); 120 shift5 worlds; Z2 2026-11-04
DISBG_NTESTED: 14 cells (5 ORBF + 3 DISK + 6 live-book boundary); Z2 2026-11-04
| 2026-11-04T22:56Z | INSTR_SC | Z1 | 12 | QA-2 note (Z1): INSTR_SC (scaling note cells, ledger program INSTR_SC) had no registry line; n = ledger rows 12; these are scaling/cost cells, not hypotheses |
DISBK_NTESTED: 9 cells (5 post-2023 variants + 4 pre-2023 variants); ORBF selection N = 346 + 4 = 350; Z2 2026-11-04
T2_SESSIONS_NTESTED: 72 descriptive measurement cells (12 instruments x 6 sessions); Z2 2026-11-05
| 2026-11-05T19:46:29Z | T2_NQ13 | ZL-2 | 9855 | cell-sessions (3483 cells, live sessions x 9 brackets); ledger T2_NQ13 |
T2WF_NTESTED: 72 selector cells (3 instruments x 12 x top1/top3); Z2 2026-11-05
T2_STAGE_A_NTESTED: ZN 5426, ZB 5426, 6E 5400, 6J 5336 stage-A cells (library families, 2 reference brackets); Z3 2026-11-05
T2_STAGE_B_NTESTED: ZN 25200, ZB 25200 stage-B cells (frozen top-300 x 84 brackets); family size for placebo/Bonferroni per instrument = 5426 + 25200 = 30626; Z3 2026-11-05
| 2026-11-05T20:32:53Z | T2_NQ13_ESXFER | ZL-2 | 0 | descriptive ES run of the same 3483 NQ cells x V0/V2, no selection, no new search |
| 2026-11-05T20:39:30Z | T2_NQ13_ENG | ZL-2 | 126 | engine-in-the-loop bracket cells (9 x 14 live pairs), ledger T2_NQ13_ENG |
| 2026-11-06T01:25:01Z | T_FIND_1B_DE | ZL-2 | 810 | measurement cells (ES/RTY/NQ x 9 signals x 6 sessions x 5 horizons), passive-entry fill + measured-cost room; no tests |
