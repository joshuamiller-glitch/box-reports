# DS3_TOOLS_T2_P3 - refreshed 03:26Z (driver code/th_t2b/t2b_driver.sh; page 2 = DS3_TOOLS_T2_P2.md; no PASS claims)

## Narrative (W-TL2b, written 03:40Z; auto sections below are regenerated every 4 h by code/th_t2b/t2b_driver.sh)
New since page 2 (DS3_TOOLS_T2_P2.md):
1. LEVEL-RELATIVE HOOK BUILT from the existing zone hooks (code/th_zn_act/zone_hooks.py already has `retgt` = target placed at wall + off, `struct` = stop just behind the wall behind, keyed by a (book7, signal second) level table). I only supplied level tables: /mnt/l2/l2vast/_th_zn/ztable_TL2A.npz (native A hourly OI walls: call res, put sup, 0DTE call/put), ztable_TL2V (A hourly volume-source walls), ztable_TL2B (B: NDX OI call wall / put wall / magnet, prior-day), built by code/th_t2b/t2b_ztable.py (keys = S1B-COMB base trades + LPB_BASE + JN05W2 trade lists; ahead coverage 45-55%). Sets (state S1-COMB, zone_exact, TL2_ names = admission tag TOOLS): TL2_RETA/RETV/RETB (target -> wall - 3 pts when a wall is 0-60 pts ahead, min 4), TL2_STOPA/STOPB (structure stop = wall behind + 3 pts when the wall is 6-60 pts behind, lots rescaled to equal $ risk, cap 3x), TL2_RETA2 (wall within 45, off -8), TL2_STOPV, TL2_ZID (identity).
2. IDENTITY GATE PASSED: TL2_ZID (table loaded, flags never fire) vs the exact base RB_COMB, month 202610: 823 / 823 trades identical on (book, entry, exit, gross), gross 47,330.5 = 47,330.5. Only then are the numbers below counted.
3. Exact month 202610 (state base, net after fees): RETA -36.4k, RETB -26.0k (targets cut at walls hurt a lot: walls are rarely the turning point), RETV +12.6k, STOPA -1.8k, STOPB +13.3k, STOPV +0.7k. One month only: nothing is claimed; the queue (t2b_zqueue.py, 5 sets per month, ~15 min per month) runs L6M then HOLD then PRE; results appear in the auto section below as months finish.
4. PER-MINUTE PLACEBO now exists (london sig-minute snapshots shifted 7-60 days, 8 offsets): JN05W2 London skip when price is >= 73 pts above the volume-source flip: recents $2.6k/wk vs placebo max $1.05k and family null q95 $1.8k (L3M +2.6k, L6M +3.7k, HOLD +1.6k, trend weeks +12.9k/+30.7k, PRE -1.1k); LPB_BASE does not replicate it (not LEAD there). Other London per-minute LEADs (net gamma sign, wall distances) exceed their placebo max too but are mostly E-press cells (leverage). Exact set TL2_LONFL73 (+ _RM) queued in the TOOLS runner (grid T2B_M_VFLU built: per-minute price minus vol-flip, London minutes).
5. BLOCKERS: (a) K-hold (loss-cut hold) leads have no exact hook (no 'cut gate'); they stay first-order. (b) The TOOLS exact runner (EMF03/EMF07/LONFL73 on LPB_BASE/JN04RM) is still waiting for tp_admit (cap 24 workers); the zone sets run through zone_exact's own gate and are running.

## AUTO: level-relative exact sets TL2_* vs RB_COMB (t2b_zscore.py)
set | month | n base->set | net base -> set | delta $
TL2_RETA 202610  n 823->830  net 45347 -> 8951  delta -36396
  L6M: months 1 of 6, delta -36396 $ (-8377 $/wk), set better in 0 of 1 months
  trade-sequence maxDD base 124920 -> set 132052 over the 1 months done
TL2_STOPA 202610  n 823->823  net 45347 -> 43510  delta -1837
  L6M: months 1 of 6, delta -1837 $ (-423 $/wk), set better in 0 of 1 months
  trade-sequence maxDD base 124920 -> set 130467 over the 1 months done
TL2_RETV 202610  n 823->833  net 45347 -> 57994  delta +12647
  L6M: months 1 of 6, delta +12647 $ (+2911 $/wk), set better in 1 of 1 months
  trade-sequence maxDD base 124920 -> set 116677 over the 1 months done
TL2_RETB 202610  n 823->840  net 45347 -> 19316  delta -26031
  L6M: months 1 of 6, delta -26031 $ (-5991 $/wk), set better in 0 of 1 months
  trade-sequence maxDD base 124920 -> set 126460 over the 1 months done
TL2_STOPB 202610  n 823->794  net 45347 -> 58638  delta +13291
  L6M: months 1 of 6, delta +13291 $ (+3059 $/wk), set better in 1 of 1 months
  trade-sequence maxDD base 124920 -> set 102702 over the 1 months done

## AUTO: TOOLS exact runner (EMF03/EMF07/LONFL73)
02:44:57 start 104 jobs
02:59:45 start 104 jobs
03:03:48 start 156 jobs
#### Exact sets (one set per job, TP engine, engine = base + screen gate hook th_screens/scr_hooks.py; bases LPB_BASE and JN04RM)
- TL2_EMF03 vs LPB_BASE: 0 of 43 months done.
- TL2_EMF07 vs LPB_BASE: 0 of 43 months done.
- TL2_LONFL73 vs LPB_BASE: 0 of 43 months done.
- TL2_EMF03_RM vs JN04RM: 0 of 43 months done.
- TL2_EMF07_RM vs JN04RM: 0 of 43 months done.
- TL2_LONFL73_RM vs JN04RM: 0 of 43 months done.

## AUTO: first-order screens
## cells scored per group and LEAD count (LEAD = recents > within-month family-null q95, L3M>0, both L6M halves > 0)
              scopes  LEAD  best_margin  med_margin
set      grp                                       
JN05W2   Ad      328     8        271.0      -339.0
         Ah      328     4        102.0      -387.0
         Am      328    14        830.0      -379.0
         Am2     328    14        830.0      -379.0
         Blv     328     6        150.0      -291.0
         Buw     208     4        310.0      -186.0
LPB_BASE Ad      336    34        747.0      -349.0
         Ah      336    37        711.0      -321.0
         Am      336    28        602.0      -291.0
         Am2     336    28        602.0      -291.0
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
     set grp use   act book  scope           feat dir     th  n_L6M     L1M    L3M    L6M   HOLD     MID   PREUW  recents  null_q95  plc_rank  tw_best5  tw_worst5  win_turned_losing
LPB_BASE  Ad   E  skip   P7   asia     Nd_em_room  ge  522.3    102  5022.9 4763.3 4286.9 3010.6   334.4   879.7   3648.8    2981.0       1.0    -408.4    36686.5                0.0
LPB_BASE  Ad   E  skip  ALL   asia     Nd_em_frac  le   -0.3    285  4455.8 4816.2 3426.8 2915.1   294.8 -1597.6   3170.9    2663.5       1.0      19.6    23185.5                1.0
LPB_BASE  Ad   E press  ALL london  Nd_vol_wfront  ge   34.8    887  4890.3 3910.9 3697.6 2517.2  4340.9   636.6   3107.4    2491.8       1.0   19037.1     4592.1                0.0
LPB_BASE Am2   E press  ALL london    Nm_vol_netg  le    0.0    841  3153.6 3039.8 3303.7 2729.3  4011.5  -660.6   3016.5    2414.7       1.0   20876.5   -11105.0                1.0
LPB_BASE  Am   E press  ALL london    Nm_vol_netg  le    0.0    841  3153.6 3039.8 3303.7 2729.3  4011.5  -660.6   3016.5    2414.7       1.0   20876.5   -11105.0                1.0
LPB_BASE  Am   E press  ALL london    Nm_vol_netg  le    0.1    979  2766.3 3356.2 3108.3 2896.1  5119.4  -187.6   3002.2    2414.7       1.0   24763.8   -16052.6                1.0
LPB_BASE Am2   E press  ALL london    Nm_vol_netg  le    0.1    979  2766.3 3356.2 3108.3 2896.1  5119.4  -187.6   3002.2    2414.7       1.0   24763.8   -16052.6                1.0
LPB_BASE  Ah   K  hold  ALL london Nh_vol_wbehind  ge  198.6    252   136.7 3182.2 2541.8 3360.2  2537.0   261.9   2951.0    2630.7       1.0   28566.2    -7573.5                0.0
LPB_BASE Am2   E press  ALL london    Nm_vol_netg  le    0.2   1137  2815.9 3868.2 3217.3 2680.1  4391.7  -195.4   2948.7    2414.7       1.0   35617.2    -9206.8                2.0
LPB_BASE  Am   E press  ALL london    Nm_vol_netg  le    0.2   1137  2815.9 3868.2 3217.3 2680.1  4391.7  -195.4   2948.7    2414.7       1.0   35617.2    -9206.8                2.0
LPB_BASE  Ad   E press  ALL london  Nd_vol_wfront  ge   71.0    783  3291.3 3200.1 3077.6 2610.9  5205.3   899.5   2844.2    2491.8       1.0   23392.5    -2726.6                1.0
LPB_BASE  Ad   E press  ALL london    Nd_vol_netg  le    0.0    855  3800.1 3155.1 3283.7 2392.9  3301.8  -486.0   2838.3    2491.8       1.0   23405.1     -193.1                0.0
LPB_BASE  Ad   E press  ALL london    Nd_vol_netg  le    0.1   1168  1790.0 3865.4 3023.7 2624.1  4702.2   -87.3   2823.9    2491.8       1.0   30107.4    -6178.8                2.0
LPB_BASE  Ah   E press  ALL london    Nh_vol_netg  le    0.1   1142  2623.2 3777.1 2995.8 2572.2  4714.8  -112.2   2784.0    2434.3       1.0   34820.0    -9352.6                2.0
LPB_BASE  Ah   E press  ALL london    Nh_vol_netg  le    0.0    842  2917.8 2872.6 2993.9 2542.0  3640.6  -404.3   2767.9    2434.3       1.0   21463.1   -12000.4                1.0
LPB_BASE Blv   E press  ALL london   NB_NDX_oi_mg  ge -913.0   1381  -612.1 3237.9 2771.0 2738.1  5669.6   429.1   2754.6    2479.8       1.0   54220.2   -23318.4                3.0
LPB_BASE  Ad   E press  ALL london      Nd_iv_atm  le    0.2   1047  2783.6 3348.7 2853.1 2597.9  4651.1  -212.9   2725.5    2491.8       1.0   24627.4    -6617.9                2.0
LPB_BASE  Ah   E press  ALL london  Nh_vol_wfront  ge   57.9    942  5294.2 4049.5 3012.9 2418.9  3618.4    53.1   2715.9    2434.3       1.0   21346.2    -6500.2                1.0
LPB_BASE  Am   E press  ALL london  Nm_vol_wfront  ge   57.9   1071  5518.6 4687.7 2772.7 2652.2  4213.3  -565.2   2712.4    2414.7       1.0   25318.2   -13090.2                1.0
LPB_BASE Am2   E press  ALL london  Nm_vol_wfront  ge   57.9   1071  5518.6 4687.7 2772.7 2652.2  4213.3  -565.2   2712.4    2414.7       1.0   25318.2   -13090.2                1.0
LPB_BASE Am2   E press  ALL london  Nm_vol_wfront  ge   87.7    921  5311.0 4819.6 2901.3 2486.8  3652.4  -434.4   2694.1    2414.7       1.0   20204.0    -5724.3                1.0
LPB_BASE  Am   E press  ALL london  Nm_vol_wfront  ge   87.7    921  5311.0 4819.6 2901.3 2486.8  3652.4  -434.4   2694.1    2414.7       1.0   20204.0    -5724.3                1.0
LPB_BASE  Ah   E press  ALL london  Nh_vol_wfront  ge   27.5   1051  4592.1 3762.5 3008.8 2294.6  3778.3   323.4   2651.7    2434.3       1.0   21134.6      687.4                1.0
LPB_BASE Am2   E press  ALL london Nm_vol_abehind  le  130.2    675  1563.3 2664.6 2822.2 2455.5  3083.8   102.5   2638.8    2414.7       1.0   32032.4   -16251.4                0.0
LPB_BASE  Am   E press  ALL london Nm_vol_abehind  le  130.2    675  1563.3 2664.6 2822.2 2455.5  3083.8   102.5   2638.8    2414.7       1.0   32032.4   -16251.4                0.0
  JN05W2  Am   E  skip  ALL london    Nm_vol_fl_u  ge   72.9    576  -935.3 2578.4 3695.1 1565.1 -5592.8 -1067.0   2630.1    1799.9       1.0   12913.0    30733.0                1.0
  JN05W2 Am2   E  skip  ALL london    Nm_vol_fl_u  ge   72.9    576  -935.3 2578.4 3695.1 1565.1 -5592.8 -1067.0   2630.1    1799.9       1.0   12913.0    30733.0                1.0
LPB_BASE  Ad   E press  ALL london      Nd_iv_atm  le    0.2    934  2783.6 3348.7 2790.0 2433.2  4066.7  -243.3   2611.6    2491.8       1.0   21868.8    -6617.9                2.0
LPB_BASE  Ah   E press  ALL london    Nh_vol_netg  le    0.1    978  2360.6 3001.6 2530.0 2680.8  5142.9  -546.9   2605.4    2434.3       1.0   25123.7   -17300.8                2.0
LPB_BASE Blv   E press  ALL london   NB_SPX_oi_cw  ge -487.3   1026 -2280.5 3974.9 2853.0 2351.1  3585.5  -317.3   2602.1    2479.8       1.0   49646.3    -5382.9                2.0
LPB_BASE  Ad   E press  ALL london  Nd_vol_afront  ge   20.5    972  4435.2 3360.6 2893.0 2307.5  4771.4   253.6   2600.3    2491.8       1.0   17310.9    -2270.7                1.0
LPB_BASE  Am   E press  ALL london    Nm_vol_net0  le    0.1   1020  2498.3 3664.9 2728.1 2460.1  4043.7  -249.6   2594.1    2414.7       1.0   24778.4   -15065.3                2.0
LPB_BASE Am2   E press  ALL london    Nm_vol_net0  le    0.1   1020  2498.3 3664.9 2728.1 2460.1  4043.7  -249.6   2594.1    2414.7       1.0   24778.4   -15065.3                2.0
LPB_BASE  Am   E press  ALL london     Nm_oi_net0  le    0.1   1026  3476.7 3584.8 2758.8 2425.0  4045.5  -314.4   2591.9    2414.7       1.0   23383.0    -3210.8                2.0
