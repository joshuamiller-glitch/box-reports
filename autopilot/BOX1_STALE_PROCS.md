# BOX 1 STALE / STOPPED PROCESSES holding memory (W-GRIDOPS 20:40Z, inventory only, NOTHING killed)

box 1 MemAvail ~47-49 GB; tp_admit gate needs 40 GB after reservations => box-1 engine admissions blocked (PA/NYL WAIT). These 25 processes (age 20-34 days, idle) hold 57.4 GB of ANONYMOUS memory:

| pid | GB | what |
|---|---|---|
| 1967594 | 5.5 |  |
| 1117679 | 4.9 |  |
| 1112283 | 4.9 |  |
| 1117678 | 4.6 |  |
| 1117680 | 4.0 |  |
| 1117469 | 4.0 |  |
| 31964 | 3.5 |  |
| 31963 | 3.3 |  |
| 1758635 | 3.1 |  |
| 31966 | 1.7 |  |
| 40216 | 1.7 |  |
| 31962 | 1.6 |  |
| 31960 | 1.4 |  |
| 31959 | 1.4 |  |
| 31961 | 1.3 |  |
| 1104351 | 1.2 |  |
| 1104350 | 1.2 |  |
| 1103023 | 1.2 |  |
| 1104338 | 1.2 |  |
| 1104335 | 1.2 |  |
| 3773117 | 1.2 |  |
| 3771574 | 1.2 |  |
| 3745332 | 1.0 |  |
| 1957151 | 0.8 |  |
| 6947 | 0.4 |  |

Groups: SIGSTOPped (state T) since ~23 d: mx_m9.py 1967594 (5.5), pb4_direct workers 1117679/1117678/1117680 (4.9+4.6+4.0), pro1_direct 1112283 (4.9), pb2_direct 1117469 (4.0), mx_m10.py 1957151 (0.8) = 28.7 GB; hung pools: rc_grid.py RA2 workers 31959-31966 + 40216 (age 20 d, futex/pipe wait, ~16 GB), ap_assembly --null 2 smoke (34 d, 6 GB, pids 1103023 1104335 1104338 1104350 1104351), joblib loky worker 1758635 (27 d, 3.1 GB); KEEP: grid.py ES/RTY/NQ loops (31 d, sleeping loops, 3.2 GB: periodic, may be wanted) and the claude process 6947.
