# DS3_TOOLS_T2_P3 - auto refresh 02:59Z (driver code/th_t2b/t2b_driver.sh; narrative in DS3_TOOLS_T2_P2.md; no PASS claims)

## exact engine status (runner.log tail)
02:44:57 start 104 jobs
02:59:45 start 104 jobs

## exact results vs LPB_BASE / JN04RM
#### Exact sets (one set per job, TP engine, engine = base + screen gate hook th_screens/scr_hooks.py; bases LPB_BASE and JN04RM)
- TL2_EMF03 vs LPB_BASE: 0 of 43 months done.
- TL2_EMF07 vs LPB_BASE: 0 of 43 months done.
- TL2_EMF03_RM vs JN04RM: 0 of 43 months done.
- TL2_EMF07_RM vs JN04RM: 0 of 43 months done.

## first-order screens (unchanged)
## cells scored per group and LEAD count (LEAD = recents > within-month family-null q95, L3M>0, both L6M halves > 0)
              scopes  LEAD  best_margin  med_margin
set      grp                                       
JN05W2   Ad      328     8        271.0      -339.0
         Ah      328     4        102.0      -387.0
         Am      328    14        830.0      -379.0
         Blv     328     6        150.0      -291.0
         Buw     208     4        310.0      -186.0
LPB_BASE Ad      336    34        747.0      -349.0
         Ah      336    37        711.0      -321.0
         Am      336    28        602.0      -291.0
         Blv     336     7        325.0      -302.0
         Buw     232     0         -5.0      -266.0

## A vs B per scope (best margin = recents minus null q95, $/wk first-order), count of scopes where group best margin > 0 (cells that beat the family null)
Ah vs Blv: scopes 83, Ah>0 in 9, Blv>0 in 7, Ah better in 38
Am vs Blv: scopes 83, Am>0 in 13, Blv>0 in 7, Am better in 32
Ad vs Blv: scopes 83, Ad>0 in 14, Blv>0 in 7, Ad better in 38
Ah vs Buw: scopes 55, Ah>0 in 9, Buw>0 in 4, Ah better in 28
Ah vs Ad: scopes 83, Ah>0 in 9, Ad>0 in 14, Ah better in 38
Am vs Ah: scopes 83, Am>0 in 13, Ah>0 in 9, Am better in 44

## LEAD cells (all groups), sorted by recents
     set grp use   act book  scope              feat dir     th  n_L6M     L1M    L3M    L6M   HOLD     MID   PREUW  recents  null_q95  plc_rank  tw_best5  tw_worst5  win_turned_losing
LPB_BASE  Ad   E  skip   P7   asia        Nd_em_room  ge  522.3    102  5022.9 4763.3 4286.9 3010.6   334.4   879.7   3648.8    2981.0       1.0    -408.4    36686.5                0.0
LPB_BASE  Ad   E  skip  ALL   asia        Nd_em_frac  le   -0.3    285  4455.8 4816.2 3426.8 2915.1   294.8 -1597.6   3170.9    2663.5       1.0      19.6    23185.5                1.0
LPB_BASE  Ad   E press  ALL london     Nd_vol_wfront  ge   34.8    887  4890.3 3910.9 3697.6 2517.2  4340.9   636.6   3107.4    2491.8       1.0   19037.1     4592.1                0.0
LPB_BASE  Am   E press  ALL london       Nm_vol_netg  le    0.0    841  3153.6 3039.8 3303.7 2729.3  4011.5  -660.6   3016.5    2414.7       1.0   20876.5   -11105.0                1.0
LPB_BASE  Am   E press  ALL london       Nm_vol_netg  le    0.1    979  2766.3 3356.2 3108.3 2896.1  5119.4  -187.6   3002.2    2414.7       1.0   24763.8   -16052.6                1.0
LPB_BASE  Ah   K  hold  ALL london    Nh_vol_wbehind  ge  198.6    252   136.7 3182.2 2541.8 3360.2  2537.0   261.9   2951.0    2630.7       1.0   28566.2    -7573.5                0.0
LPB_BASE  Am   E press  ALL london       Nm_vol_netg  le    0.2   1137  2815.9 3868.2 3217.3 2680.1  4391.7  -195.4   2948.7    2414.7       1.0   35617.2    -9206.8                2.0
LPB_BASE  Ad   E press  ALL london     Nd_vol_wfront  ge   71.0    783  3291.3 3200.1 3077.6 2610.9  5205.3   899.5   2844.2    2491.8       1.0   23392.5    -2726.6                1.0
LPB_BASE  Ad   E press  ALL london       Nd_vol_netg  le    0.0    855  3800.1 3155.1 3283.7 2392.9  3301.8  -486.0   2838.3    2491.8       1.0   23405.1     -193.1                0.0
LPB_BASE  Ad   E press  ALL london       Nd_vol_netg  le    0.1   1168  1790.0 3865.4 3023.7 2624.1  4702.2   -87.3   2823.9    2491.8       1.0   30107.4    -6178.8                2.0
LPB_BASE  Ah   E press  ALL london       Nh_vol_netg  le    0.1   1142  2623.2 3777.1 2995.8 2572.2  4714.8  -112.2   2784.0    2434.3       1.0   34820.0    -9352.6                2.0
LPB_BASE  Ah   E press  ALL london       Nh_vol_netg  le    0.0    842  2917.8 2872.6 2993.9 2542.0  3640.6  -404.3   2767.9    2434.3       1.0   21463.1   -12000.4                1.0
LPB_BASE Blv   E press  ALL london      NB_NDX_oi_mg  ge -913.0   1381  -612.1 3237.9 2771.0 2738.1  5669.6   429.1   2754.6    2479.8       1.0   54220.2   -23318.4                3.0
LPB_BASE  Ad   E press  ALL london         Nd_iv_atm  le    0.2   1047  2783.6 3348.7 2853.1 2597.9  4651.1  -212.9   2725.5    2491.8       1.0   24627.4    -6617.9                2.0
LPB_BASE  Ah   E press  ALL london     Nh_vol_wfront  ge   57.9    942  5294.2 4049.5 3012.9 2418.9  3618.4    53.1   2715.9    2434.3       1.0   21346.2    -6500.2                1.0
LPB_BASE  Am   E press  ALL london     Nm_vol_wfront  ge   57.9   1071  5518.6 4687.7 2772.7 2652.2  4213.3  -565.2   2712.4    2414.7       1.0   25318.2   -13090.2                1.0
