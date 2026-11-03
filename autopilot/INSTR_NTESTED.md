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
