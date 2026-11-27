# REPLACEMENT SETS: exact scorecard vs the live mix as run (W-PLAN-AS)

| subject | stream (managed vs reference) | worst week | winning weeks | st.dev. weekly income | biggest give-back | trades giving back > 50% of peak (all / peak >= $1k) | max DD | income | smoother quarters: all / NQ-up / NQ-down | smoother years: all / up / down | ACCEPTABLE at floor 10% / 20% / 30% | slot effects: entries only in the managed run (n, net $) / only in the bracket run (n, net $) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AS | TL3_DX_AS_REPL_M1_M vs live mix | -36,185 / -37,409 | 62% / 60% | 17,955 / 17,957 | 12,029 / 13,124 [best_px (engine MFE) / 1-s tape] | 3038 / 1158  vs  3307 / 1599 | -66,418 / -67,941 | 1,020,055 / 893,926 | 5/15, 9/13, 4/13 | 1/4, 2/4, 1/4 | no / no / no | 966 (151,874) / 946 (9,092) |
| AS | TL3_DX_AS_REPL_M2_M vs live mix | -41,122 / -37,409 | 62% / 60% | 18,594 / 17,957 | 12,029 / 13,124 [best_px (engine MFE) / 1-s tape] | 3064 / 1154  vs  3307 / 1599 | -68,113 / -67,941 | 999,246 / 893,926 | 6/15, 7/13, 4/13 | 1/4, 3/4, 0/4 | no / no / no | 1065 (128,746) / 955 (14,383) |
| AS | TL3_DX_AS_REPL_M3_M vs live mix | -38,473 / -37,409 | 62% / 60% | 18,873 / 17,957 | 17,580 / 13,124 [best_px (engine MFE) / 1-s tape] | 3356 / 1240  vs  3307 / 1599 | -72,332 / -67,941 | 1,048,797 / 893,926 | 5/15, 5/13, 3/13 | 0/4, 1/4, 0/4 | no / no / no | 1658 (192,919) / 986 (14,672) |
| NY | TL3_DX_NY_REPL_X3_M vs live mix | -92,627 / -110,130 | 63% / 63% | 45,029 / 49,895 | 28,674 / 30,988 [best_px (engine MFE) / 1-s tape] | 5786 / 3028  vs  6740 / 3703 | -247,678 / -200,647 | 2,939,073 / 3,505,193 | 11/15, 6/13, 7/13 | 4/4, 4/4, 2/4 | no / no / no | 3156 (702,867) / 6447 (1,143,119) |
| NY | TL3_DX_NY_REPL_T3_M__v1 vs live mix | -103,248 / -110,130 | 63% / 63% | 47,190 / 49,895 | 28,674 / 30,988 [best_px (engine MFE) / 1-s tape] | 5972 / 3233  vs  6740 / 3703 | -228,155 / -200,647 | 3,155,293 / 3,505,193 | 8/15, 7/13, 8/13 | 3/4, 2/4, 2/4 | no / no / no | 3521 (906,658) / 6452 (1,142,518) |
| NY | TL3_DX_NY_REPL_T4_M__v1 vs live mix | -99,702 / -110,130 | 64% / 63% | 47,426 / 49,895 | 28,674 / 30,988 [best_px (engine MFE) / 1-s tape] | 6365 / 3295  vs  6740 / 3703 | -226,534 / -200,647 | 3,290,770 / 3,505,193 | 8/15, 6/13, 7/13 | 3/4, 2/4, 2/4 | no / no / no | 4236 (1,040,940) / 6451 (1,142,678) |
| NP | TL3_DX_NP_REPL_M1_M__v1 vs live mix | -29,928 / -44,139 | 66% / 64% | 13,078 / 17,852 | 24,155 / 25,005 [best_px (engine MFE) / 1-s tape] | 1633 / 761  vs  3932 / 2021 | -83,364 / -134,363 | 1,084,015 / 1,099,464 | 13/15, 11/13, 8/13 | 4/4, 4/4, 3/4 | no / no / no | 1650 (203,362) / 5444 (219,547) |
| NP | TL3_DX_NP_REPL_M12_M vs live mix | -30,608 / -44,139 | 66% / 64% | 14,383 / 17,852 | 24,155 / 25,005 [best_px (engine MFE) / 1-s tape] | 2512 / 1027  vs  3932 / 2021 | -83,527 / -134,363 | 1,224,030 / 1,099,464 | 13/15, 10/13, 5/13 | 3/4, 4/4, 3/4 | no / no / no | 3210 (346,141) / 5456 (246,229) |

CANDIDATE ALONE, exact (2 lots, engine) vs bare quick screen (1 lot x 2): per-trade $ and trade count
TL3_DX_AS_REPL_c1_A exact trades 974 net/trade $280 (per lot $140) total $272297 exit mix {'UWTime': 0.56, 'Target': 0.27, 'Stop': 0.17}
TL3_DX_AS_REPL_c2_A exact trades 1127 net/trade $231 (per lot $116) total $260831 exit mix {'UWTime': 0.43, 'Target': 0.33, 'Stop': 0.23, 'RollFlat': 0.0}
TL3_DX_AS_REPL_c3_A exact trades 1756 net/trade $219 (per lot $110) total $385427 exit mix {'UWTime': 0.4, 'Target': 0.34, 'Stop': 0.26, 'RollFlat': 0.0}
TL3_DX_NY_REPL_c1_A exact trades 1024 net/trade $385 (per lot $193) total $394688 exit mix {'UWTime': 0.49, 'Target': 0.29, 'Stop': 0.23}
TL3_DX_NY_REPL_c2_A exact trades 1115 net/trade $361 (per lot $181) total $403047 exit mix {'UWTime': 0.46, 'Target': 0.3, 'Stop': 0.24}
TL3_DX_NY_REPL_c3_A exact trades 1325 net/trade $391 (per lot $196) total $518514 exit mix {'UWTime': 0.5, 'Target': 0.28, 'Stop': 0.22}
TL3_DX_NY_REPL_c4_A exact trades 735 net/trade $250 (per lot $125) total $183415 exit mix {'UWTime': 0.53, 'Target': 0.28, 'Stop': 0.19}
TL3_DX_NP_REPL_c1_A exact trades 1749 net/trade $242 (per lot $121) total $423170 exit mix {'UWTime': 0.41, 'Target': 0.32, 'Stop': 0.27}
TL3_DX_NP_REPL_c2_A exact trades 1792 net/trade $146 (per lot $73) total $262203 exit mix {'UWTime': 0.41, 'Target': 0.31, 'Stop': 0.28}
| LO | TL3_DX_LO_REPL_M1_M vs live mix | -55,917 / -107,350 | 61% / 64% | 17,580 / 22,874 | 19,384 / 20,622 [best_px (engine MFE) / 1-s tape] | 1454 / 694  vs  3027 / 1807 | -131,817 / -224,333 | 765,506 / 879,157 | 10/15, 6/13, 9/13 | 3/4, 3/4, 3/4 | no / no / no | 863 (86,091) / 3096 (204,221) |
TL3_DX_LO_REPL_c1_A exact trades 864 net/trade $100 total $86476 {'Target': 0.83, 'UWTime': 0.1, 'Stop': 0.07}
