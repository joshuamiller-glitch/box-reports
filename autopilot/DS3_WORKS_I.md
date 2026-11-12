# DS3_WORKS_I - T-WORKS / P7 FIX, worker W-I (families I room to target, J cross-market, K context, L P7 signal internals), page 2026-11-12 10:23Z
Label PRE-PROOF, post-hoc, Shadow only, no PASS claim. Prereg autopilot/WORKS_I_PREREG.md (sha in DECISIONS.md; the first first-order screen ran before the sha line, disclosed there). Code code/th_works_i/, tables /mnt/l2/l2vast/_th_works/i/, feature table /mnt/l2/l2vast/_th_works/p7_feat_I.parquet (key sig_ts, 5,011 P7 taken trades x 128 columns; W-E signal-level table not used, so signals that were not taken are not in these tests).

## What exists
1. One feature function (i_feat.build) serves both the first-order table and the exact engine (identity checked: the table and the function output are identical in all 128 columns). Bars: NQ/ES/RTY 1-min with volume to 2026-11-10, ZN/6E/6J owned core bars, calendar events verified against the 08:30 / 14:00 ET range spike (unverified dates: FOMC 2026-03-18, NFP 2025-04-04, 2025-11-16, 2026-02-06; CPI identity cannot be told apart from PPI/retail days by the spike alone, the listed CPI dates all spike).
2. First-order screen: 1,176 flags x skip/half = 2,352 cells on the LPB_BASE trade list (whole-stack daily P&L, live rows excluded), each with removed-$ in the 20 worst P7 weeks vs the 20 best (trend) weeks and the flagged trades of the frozen live week. Not built: ES print absorption (needs ES trades), tick-level 45-s confirm quality beyond signal-to-entry seconds and the 1-s dip.
3. Exact hook: i_mixin.IGateMixin (skip / half / target retarget at the signal second inside the JN04RM / LPB engine), set builder i_mkset.py, manager i_mgr.py (launch gate 62 GB, hard guard 40 GB), scorer i_score.py.

## Family null (is the best cell of a family better than the best cell of random flags?)
The feature rows were permuted among P7 trades inside the same calendar month, the whole grid re-scored, and the best minimum equal-mean cut over L6M, HOLD, PRE and X-prime (cells flagging 5-45 percent of trades) recorded; 300 draws.

| family | observed best | null median | null p90 | family p |
|--|--|--|--|--|
| I | 16.3 | 7.9 | 16.6 | 0.110 |
| J | 27.3 | 20.6 | 28.8 | 0.136 |
| K | 21.3 | 13.3 | 22.6 | 0.140 |
| L | 14.4 | 18.2 | 25.1 | 0.751 |

Plain reading: no family beats its null at 5 percent. J (cross-market) is closest on cell count; I, K are about 0.1; L is at the null. Everything below is therefore a lead, not a finding.

## Registered cells (top-3 per family by the prereg rule, plus asymmetry picks)
Columns: cut and eq_cut are stack maxDD cut percent (first-order, vs LPB_BASE, equal-mean for eq); rem w20 / rem b20 = P&L $ of the removed part in the 20 worst / 20 best P7 weeks (negative = losers removed); live = flagged trades in the frozen live week and the $ removed there (positive = winners removed).

| fam | kind | cell | scope | act | n_flag | cut_L6M | cut_HOLD | cut_PRE | cut_X' | dmean_L6M | placebo_p | rem_w20 | rem_b20 | live_n | live_rem |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| I | prereg_top3 | room_on_x<2.0 | all | skip | 1766 | 27.6 | 13.0 | 12.2 | 29.9 | 776.6 | 0.0 | -232901.7 | 281945.8 | 11 | 20662.8 |
| I | prereg_top3 | room_on_x<1.5 | all | skip | 1431 | 20.6 | 7.2 | 0.3 | 23.6 | 1074.2 | 0.1 | -188232.2 | 238580.1 | 9 | 18761.6 |
| I | prereg_top3 | room_on_x<1.5 | asia | half | 505 | 0.5 | 2.5 | -0.4 | 10.9 | 623.5 | 0.1 | -62023.8 | 76271.3 | 3 | 6552.3 |
| J | prereg_top3 | breadth_ext15==3 | all | skip | 1602 | 22.5 | 24.1 | 25.1 | 39.7 | 1081.1 | 0.0 | -190031.7 | 283510.9 | 11 | 30227.7 |
| J | prereg_top3 | x_es_pull_opp5>=1.225(q70) | all | skip | 1245 | 3.5 | 5.4 | -1.0 | 0.9 | 4691.2 | 0.1 | -90678.8 | 165414.9 | 0 | 0.0 |
| J | prereg_top3 | es_r60m>=21.82(q70) | all | skip | 1147 | 20.1 | 21.7 | 12.5 | 20.2 | 1657.7 | 0.0 | -143057.5 | 151408.8 | 13 | 12470.2 |
| K | prereg_top3 | dow==2 | asia | skip | 408 | 35.5 | 8.0 | 4.7 | 13.2 | 3584.8 | 0.0 | -76942.0 | 88268.5 | 14 | 10053.3 |
| K | prereg_top3 | dow==2 | all | skip | 895 | 40.4 | 1.1 | 12.4 | 13.9 | 3069.8 | 0.0 | -89549.4 | 141877.1 | 19 | 8571.2 |
| K | prereg_top3 | dow>1 | asia | skip | 1307 | 33.1 | 10.3 | -0.1 | 33.2 | 2900.3 | 0.0 | -276281.1 | 340685.0 | 21 | 27343.7 |
| L | prereg_top3 | push_beyond_ref<=-1(q30) | all | half | 1682 | 14.1 | 15.9 | 14.3 | 11.8 | 527.0 | 0.0 | -73951.5 | 98885.3 | 24 | 20206.2 |
| L | prereg_top3 | pb_depth>=13.75(q70) | all | half | 1875 | 4.0 | 6.0 | 2.2 | 11.1 | 2109.7 | 0.1 | -56351.0 | 60354.7 | 38 | 20686.8 |
| L | prereg_top3 | pb_depth>=18(q80) | all | skip | 1275 | 28.5 | -11.4 | 8.3 | 9.6 | 4657.0 | 0.0 | -91302.4 | 85225.2 | 32 | 29690.0 |
| J | asymmetry_pick | rs_es15>=4.377(q80) | all | half | 1090 | 12.3 | 12.2 | 10.0 | 14.8 | 1804.4 | nan | -60988.7 | -4937.7 | 21 | 15820.3 |
| J | asymmetry_pick | rs_es30>=9.397(q80) | all | half | 998 | 19.9 | 9.4 | 21.0 | 6.5 | 592.0 | nan | -53167.4 | -1761.4 | 18 | 13599.6 |
| J | asymmetry_pick | nq_r60m>=32.91(q70) | all | skip | 1199 | 46.5 | 37.4 | 20.7 | 10.4 | 1242.3 | nan | -154496.0 | 153429.7 | 19 | 4934.1 |

## Bi-weekly walk-forward (first-order)
| kind | fam | cell | wf2w_cut | wf2w_mean | wf2w_beat_pct |
|--|--|--|--|--|--|
| family_repick | I | all 68 cells | -8.3 | -2495.7 | 59.5 |
| family_repick | J | all 954 cells | -3.2 | -2402.3 | 60.8 |
| family_repick | K | all 206 cells | -7.9 | -2768.6 | 51.9 |
| family_repick | L | all 488 cells | 11.4 | -1266.0 | 68.4 |
| cell_vs_live | I | I|room_on_x<2.0|all|skip | 12.2 | -2150.4 | 41.8 |
| cell_vs_live | I | I|room_on_x<1.5|all|skip | 0.3 | -1696.8 | 30.4 |
| cell_vs_live | I | I|room_on_x<1.5|asia|half | -0.4 | -337.9 | 34.2 |
| cell_vs_live | J | J|breadth_ext15==3|all|skip | 25.1 | -127.2 | 64.6 |
| cell_vs_live | J | J|breadth_ext15>2|all|skip | 25.1 | -127.2 | 64.6 |
| cell_vs_live | J | J|x_es_pull_opp5>=1.225(q70)|all|skip | -1.0 | 445.7 | 39.2 |
| cell_vs_live | J | J|es_r60m>=21.82(q70)|all|skip | 2.9 | 18.2 | 51.9 |
| cell_vs_live | J | J|rs_es15>=4.377(q80)|all|half | 10.0 | 565.8 | 48.1 |
| cell_vs_live | J | J|rty_ext15==1|all|skip | 20.7 | -1052.6 | 63.3 |
| cell_vs_live | J | J|rty_ext15>0|all|skip | 20.7 | -1052.6 | 63.3 |
| cell_vs_live | J | J|rs_es15>=4.377(q80)|all|skip | 25.1 | 876.9 | 46.8 |
| cell_vs_live | K | K|dow==2|asia|skip | -0.3 | 312.3 | 39.2 |
| cell_vs_live | K | K|dow==2|all|skip | -3.3 | -615.8 | 48.1 |
| cell_vs_live | K | K|dow>1|asia|skip | -0.1 | -1254.5 | 40.5 |
| cell_vs_live | K | K|dow>1|asia|half | 4.5 | -739.8 | 62.0 |
| cell_vs_live | K | K|dow==2|asia|half | 3.9 | 37.8 | 48.1 |
| cell_vs_live | K | K|dow==3|all|skip | 14.2 | -108.8 | 54.4 |
| cell_vs_live | K | K|dow==2|all|half | 8.9 | -64.9 | 57.0 |
| cell_vs_live | K | K|dow==3|asia|skip | -2.5 | -894.7 | 26.6 |
| cell_vs_live | L | L|push_beyond_ref<=-1(q30)|all|half | 14.3 | 82.2 | 73.4 |
| cell_vs_live | L | L|pb_depth>=13.75(q70)|all|half | -6.5 | 363.2 | 70.9 |
| cell_vs_live | L | L|pb_depth>=18(q80)|all|skip | -14.1 | 203.5 | 55.7 |
| cell_vs_live | L | L|ema_slope15>=1.3(q80)|all|skip | -0.4 | -528.3 | 57.0 |
| cell_vs_live | L | L|dip3>=20.75(q80)|all|half | -4.6 | 380.0 | 54.4 |
| cell_vs_live | L | L|l2conf<=1|asia|half | 14.1 | -63.7 | 51.9 |
| cell_vs_live | L | L|pb_depth>=13.75(q70)|all|skip | -15.5 | -747.4 | 53.2 |
| cell_vs_live | L | L|ema_slope15>=1.3(q80)|all|half | 28.2 | 193.4 | 65.8 |

The family re-pick rows are the honest out-of-sample of the whole screen: only L shows a drawdown cut and it costs mean; the others are negative.

## Asymmetric bracket (flagged entries get target 30/35/45 instead of 60, first-order from the PTR paths; only the target side is representable)
| cell | tgt | n_flag | n_hit | cut_L6M | cut_HOLD | cut_PRE | cut_X' | dmean_L6M | chg_w20 | chg_b20 |
|--|--|--|--|--|--|--|--|--|--|--|
| I|room_on_x<2.0|all | 30.0 | 1766 | 1060 | -6.0 | -4.8 | 14.0 | 10.1 | -948.5 | 99731.7 | -143534.0 |
| I|room_on_x<2.0|all | 35.0 | 1766 | 993 | -3.7 | -1.7 | 12.4 | 3.7 | -1199.2 | 98673.2 | -111047.0 |
| I|room_on_x<2.0|all | 45.0 | 1766 | 877 | 7.9 | -4.3 | 2.6 | -0.3 | -1341.8 | 46673.2 | -60972.5 |
| J|breadth_ext15==3|all | 30.0 | 1602 | 943 | 3.9 | 5.9 | 13.5 | 5.4 | 75.5 | 68954.2 | -79936.5 |
| J|breadth_ext15==3|all | 35.0 | 1602 | 877 | 2.6 | 4.6 | 18.9 | 9.1 | -369.1 | 42752.7 | -50883.0 |
| J|breadth_ext15==3|all | 45.0 | 1602 | 781 | 17.7 | 17.9 | 5.5 | 2.6 | -304.7 | 29479.7 | -17524.5 |
| J|es_r60m>=21.82(q70)|all | 30.0 | 1147 | 653 | 3.8 | 5.7 | 7.1 | -0.1 | 1161.7 | 61170.2 | -56213.0 |
| J|es_r60m>=21.82(q70)|all | 35.0 | 1147 | 623 | 4.0 | 6.0 | 11.9 | 0.5 | 1937.8 | 56669.7 | -47780.0 |
| J|es_r60m>=21.82(q70)|all | 45.0 | 1147 | 543 | 4.5 | 6.5 | 18.4 | -2.1 | 539.7 | 39691.7 | -33925.0 |
| J|rs_es15>=4.377(q80)|all | 30.0 | 1090 | 637 | -0.4 | 1.6 | 0.0 | 24.4 | 495.5 | 42236.0 | 6908.5 |
| J|rs_es15>=4.377(q80)|all | 35.0 | 1090 | 606 | 1.0 | 3.0 | 8.4 | 26.3 | 257.0 | 38303.0 | 24323.5 |
| J|rs_es15>=4.377(q80)|all | 45.0 | 1090 | 516 | 6.0 | 0.3 | -10.6 | -0.6 | 506.7 | 7740.0 | 37582.0 |
| K|dow==2|asia | 30.0 | 408 | 244 | 24.1 | 15.3 | 5.1 | 12.1 | 1027.4 | 22861.0 | -56825.0 |
| K|dow==2|asia | 35.0 | 408 | 224 | 27.5 | 18.5 | 2.9 | 10.4 | 1085.7 | 20156.5 | -39525.0 |
| K|dow==2|asia | 45.0 | 408 | 193 | 30.5 | 24.9 | 9.5 | 16.3 | 257.1 | 36951.5 | -6917.0 |
| L|push_beyond_ref<=-1(q30)|all | 30.0 | 1682 | 1017 | 36.4 | 16.4 | 12.7 | 29.6 | 972.9 | 84315.0 | -109085.0 |
| L|push_beyond_ref<=-1(q30)|all | 35.0 | 1682 | 953 | 40.7 | 22.8 | 15.8 | 19.3 | 963.9 | 89365.0 | -75674.0 |
| L|push_beyond_ref<=-1(q30)|all | 45.0 | 1682 | 836 | 28.8 | 18.1 | 9.3 | 14.8 | 1815.0 | 63708.0 | -33010.5 |
| L|ema_slope15>=1.3(q80)|all | 30.0 | 1257 | 737 | 15.0 | 11.3 | 24.4 | 5.2 | -562.7 | 92699.2 | -20066.5 |
| L|ema_slope15>=1.3(q80)|all | 35.0 | 1257 | 695 | 12.8 | 14.6 | 26.3 | 5.3 | 758.2 | 80441.7 | -4730.0 |
| L|ema_slope15>=1.3(q80)|all | 45.0 | 1257 | 614 | 8.5 | 10.4 | 24.1 | 5.2 | 656.6 | 48607.2 | 13658.5 |

## Exact (one set per job, JN04RM base, vs JN04RM and LPB references)

vs JN04RM
| cell | window | cut | eq_cut | dmean | dd | dd_ref | d_worst5 | d_best5 |
|--|--|--|--|--|--|--|--|--|
| WI_J_RS15H | L1M | 4.4 | 1.5 | 398.3 | 25860.9 | 27055.7 | -8967.6 | -8967.6 |
| WI_J_RS15H | L3M | -13.5 | -17.0 | -142.2 | 47325.8 | 41699.4 | 995.9 | -6839.6 |
| WI_J_RS15H | L6M | -13.5 | -17.0 | -518.8 | 47325.8 | 41699.4 | 9437.5 | -14404.1 |
| WI_J_ES60S | L1M | -6.1 | -6.3 | 119.6 | 28692.8 | 27055.7 | -3185.1 | -3185.1 |
| WI_J_ES60S | L3M | 0.0 | -0.3 | -213.5 | 41694.9 | 41699.4 | -1632.6 | 3410.2 |
| WI_J_ES60S | L6M | 0.0 | -0.3 | -47.5 | 41694.9 | 41699.4 | 7220.0 | -34804.8 |
| WI_K_W2AS | L1M | -1.1 | -3.2 | -95.4 | 27342.1 | 27055.7 | -4255.9 | -4255.9 |
| WI_K_W2AS | L3M | 8.0 | 6.1 | -447.0 | 38344.3 | 41699.4 | 6498.6 | 717.1 |
| WI_K_W2AS | L6M | 8.0 | 6.1 | -430.7 | 38344.3 | 41699.4 | 18250.5 | 1471.6 |
| WI_L_PB13H | L1M | 2.0 | -0.1 | 181.3 | 26511.7 | 27055.7 | -6564.8 | -6564.8 |
| WI_L_PB13H | L3M | 7.4 | 5.4 | -72.0 | 38613.6 | 41699.4 | 3629.8 | -13748.2 |
| WI_L_PB13H | L6M | 7.4 | 5.4 | -370.8 | 38613.6 | 41699.4 | 19538.6 | -37748.5 |
| WI_L_SL13S | L1M | 51.1 | 53.8 | 1337.1 | 13236.2 | 27055.7 | 13480.3 | 13480.3 |
| WI_L_SL13S | L3M | -8.1 | -2.2 | 687.9 | 45087.2 | 41699.4 | 15172.9 | 6062.0 |
| WI_L_SL13S | L6M | -8.1 | -2.2 | 1061.9 | 45087.2 | 41699.4 | 13101.0 | -9716.9 |
| WI_J_BR3T45 | L1M | 17.0 | 12.3 | 401.0 | 22462.1 | 27055.7 | 3700.1 | 3700.1 |
| WI_J_BR3T45 | L3M | 12.7 | 7.8 | 428.3 | 36418.2 | 41699.4 | 13297.8 | -1804.3 |
| WI_J_BR3T45 | L6M | 3.3 | -2.1 | -1010.2 | 40309.0 | 41699.4 | 12080.4 | -14483.7 |
| WI_K_W2AT45 | L1M | -0.7 | -1.9 | 323.1 | 27254.1 | 27055.7 | -230.7 | -230.7 |
| WI_K_W2AT45 | L3M | 10.1 | 9.1 | -37.7 | 37471.9 | 41699.4 | 6724.7 | 11805.6 |
| WI_K_W2AT45 | L6M | 10.1 | 9.1 | -203.1 | 37471.9 | 41699.4 | 13914.0 | -7040.1 |
| WI_L_SL13T35 | L1M | 41.1 | 36.0 | 40.7 | 15944.4 | 27055.7 | 9072.2 | 9072.2 |
| WI_L_SL13T35 | L3M | -36.0 | -47.6 | -1376.9 | 56717.1 | 41699.4 | -1697.7 | 16818.1 |
| WI_L_SL13T35 | L6M | -36.0 | -47.6 | -1406.6 | 56717.1 | 41699.4 | 6956.8 | -8163.5 |
| WI_I_ON15S | L1M | 10.3 | 7.0 | -2871.2 | 24263.6 | 27055.7 | -2122.3 | -2122.3 |
| WI_I_ON15S | L3M | -12.4 | -16.6 | -660.5 | 46873.7 | 41699.4 | -2382.2 | -40967.2 |
| WI_I_ON15S | L6M | -12.4 | -16.6 | -585.7 | 46873.7 | 41699.4 | 16505.6 | -48766.7 |
| WI_J_RS30T35 | L1M | 60.2 | 60.0 | 1094.9 | 10775.2 | 27055.7 | 11703.3 | 11703.3 |
| WI_J_RS30T35 | L3M | 8.5 | 8.1 | 1031.0 | 38158.6 | 41699.4 | 21333.7 | 7413.0 |
| WI_J_RS30T35 | L6M | 8.5 | 8.1 | -83.4 | 38158.6 | 41699.4 | 31162.1 | -4886.5 |
| WI_J_RS30T35 | HOLD | -0.5 | -0.9 | 90.1 | 73098.7 | 72757.5 | 16772.8 | -2761.7 |
| WI_K_DOW1AS | L1M | 31.2 | 23.5 | -2906.0 | 18603.7 | 27055.7 | 2288.8 | 2288.8 |
| WI_K_DOW1AS | L3M | -10.6 | -23.0 | -1684.1 | 46100.8 | 41699.4 | 15996.2 | -28524.3 |
| WI_K_DOW1AS | L6M | -10.6 | -23.0 | -1695.6 | 46100.8 | 41699.4 | 22766.3 | -80446.9 |
| WI_K_W2S | L1M | 32.8 | 35.7 | -1510.9 | 18189.9 | 27055.7 | 2356.9 | 2356.9 |
| WI_K_W2S | L3M | 35.0 | 37.9 | 1579.3 | 27090.1 | 41699.4 | 25296.7 | -3913.0 |
| WI_K_W2S | L6M | 27.3 | 30.5 | 766.5 | 30321.6 | 41699.4 | 34066.6 | -3965.6 |
| WI_K_W2S | HOLD | -5.4 | -0.8 | -41.3 | 76692.8 | 72757.5 | 20557.6 | -14435.0 |
| WI_J_BR3S | L1M | 26.7 | 29.9 | -3564.8 | 19835.4 | 27055.7 | -414.4 | -414.4 |
| WI_J_BR3S | L3M | 28.1 | 31.2 | -811.4 | 29993.2 | 41699.4 | 29596.9 | -17763.8 |
| WI_J_BR3S | L6M | 14.4 | 18.1 | 782.7 | 35674.8 | 41699.4 | 33013.6 | -57351.5 |
| WI_J_BR3S | HOLD | 19.0 | 22.5 | 441.6 | 58943.3 | 72757.5 | 5774.6 | -44697.2 |
| WI_J_BR3S | PRE | 5.2 | 9.3 | -452.3 | 63274.5 | 66713.5 | 12000.0 | -26099.3 |
| WI_J_BR3S | X' | 4.3 | 8.5 | 69.4 | 61307.4 | 64076.6 | 15525.5 | -345.4 |
| WI_J_BR3S | WF2W | 0.0 | 50.6 | -257.7 | nan | nan | nan | nan |
| WI_J_RS30H | L1M | 15.9 | 12.0 | -50.0 | 22762.2 | 27055.7 | 3316.3 | 3316.3 |
| WI_J_RS30H | L3M | 13.6 | 9.6 | 108.5 | 36044.5 | 41699.4 | 13070.7 | -24516.5 |
| WI_J_RS30H | L6M | 13.6 | 9.6 | -755.3 | 36044.5 | 41699.4 | 20365.3 | -36859.2 |
| WI_L_PUSHH | L1M | 4.7 | 3.0 | 423.3 | 25785.9 | 27055.7 | -2344.1 | -2344.1 |
| WI_L_PUSHH | L3M | 15.9 | 14.4 | -215.0 | 35087.7 | 41699.4 | 12501.2 | -22280.8 |
| WI_L_PUSHH | L6M | 15.9 | 14.4 | -296.1 | 35087.7 | 41699.4 | 18416.1 | -21772.9 |
| WI_L_PUSHH | HOLD | 20.2 | 18.8 | -342.1 | 58036.4 | 72757.5 | 22567.1 | -18037.8 |
| WI_G_BR3S | L1M | 37.7 | 33.7 | -3343.3 | 16856.9 | 27055.7 | 238.9 | 238.9 |
| WI_G_BR3S | L3M | 28.1 | 23.4 | -987.7 | 29993.2 | 41699.4 | 32575.3 | -22858.3 |
| WI_G_BR3S | L6M | 13.5 | 8.0 | -1202.3 | 36051.4 | 41699.4 | 35615.5 | -67149.8 |
| WI_I_ON2S | L1M | 12.4 | 5.1 | 1114.7 | 23711.7 | 27055.7 | -4186.2 | -4186.2 |
| WI_I_ON2S | L3M | 9.5 | 2.0 | -1526.0 | 37742.4 | 41699.4 | 7301.0 | -43953.3 |
| WI_I_ON2S | L6M | 9.5 | 2.0 | -1458.7 | 37742.4 | 41699.4 | 25695.5 | -61850.9 |
| WI_J_NQ60S | L1M | 15.2 | 13.8 | -762.5 | 22937.5 | 27055.7 | 4668.6 | 4668.6 |
| WI_J_NQ60S | L3M | 8.0 | 6.4 | 969.0 | 38376.9 | 41699.4 | 11382.0 | -1301.6 |
| WI_J_NQ60S | L6M | 8.0 | 6.4 | -288.0 | 38376.9 | 41699.4 | 21433.4 | -57892.7 |
| WI_L_PB18S | L1M | 26.2 | 31.1 | -2824.7 | 19979.6 | 27055.7 | -361.0 | -361.0 |
| WI_L_PB18S | L3M | 11.4 | 17.3 | 445.6 | 36964.7 | 41699.4 | 16723.1 | -1314.5 |
| WI_L_PB18S | L6M | 11.4 | 17.3 | 1245.3 | 36964.7 | 41699.4 | 24513.1 | -39871.6 |
| WI_L_SL19H | L1M | 32.8 | 33.2 | -191.1 | 18190.7 | 27055.7 | 4825.3 | 4825.3 |
| WI_L_SL19H | L3M | -3.7 | -3.1 | 919.2 | 43224.7 | 41699.4 | 11334.0 | -1416.8 |
| WI_L_SL19H | L6M | -3.7 | -3.1 | 109.3 | 43224.7 | 41699.4 | 13461.4 | -14078.5 |
| WI_N_BR3S | L1M | 36.2 | 35.0 | 3260.4 | 17274.5 | 27055.7 | -1585.9 | -1585.9 |
| WI_N_BR3S | L3M | 58.6 | 57.8 | 12.6 | 17274.5 | 41699.4 | 35565.0 | -73428.4 |
| WI_N_BR3S | L6M | 58.6 | 57.8 | -287.0 | 17274.5 | 41699.4 | 72070.9 | -125597.8 |

vs LPB
| cell | window | cut | eq_cut | dmean | dd | dd_ref | d_worst5 | d_best5 |
|--|--|--|--|--|--|--|--|--|
| WI_J_RS15H | L1M | 49.5 | 42.7 | -10029.2 | 25860.9 | 51252.7 | 4963.7 | 4963.7 |
| WI_J_RS15H | L3M | 38.7 | 30.4 | -3229.6 | 47325.8 | 77224.2 | 71571.3 | -55741.2 |
| WI_J_RS15H | L6M | 38.7 | 30.4 | -2576.8 | 47325.8 | 77224.2 | 80897.7 | -46417.0 |
| WI_J_ES60S | L1M | 44.0 | 36.0 | -6766.1 | 28692.8 | 51252.7 | 10746.2 | 10746.2 |
| WI_J_ES60S | L3M | 46.0 | 38.3 | -1811.6 | 41694.9 | 77224.2 | 69149.4 | -45491.3 |
| WI_J_ES60S | L6M | 46.0 | 38.3 | -2695.8 | 41694.9 | 77224.2 | 78886.9 | -46554.7 |
| WI_K_W2AS | L1M | 46.7 | 42.2 | -8806.1 | 27342.1 | 51252.7 | 9675.3 | 9675.3 |
| WI_K_W2AS | L3M | 50.3 | 46.2 | -2083.6 | 38344.3 | 77224.2 | 79180.0 | -48184.5 |
| WI_K_W2AS | L6M | 50.3 | 46.2 | -1653.8 | 38344.3 | 77224.2 | 91816.8 | -43340.5 |
| WI_L_PB13H | L1M | 48.3 | 41.2 | -7762.6 | 26511.7 | 51252.7 | 7366.4 | 7366.4 |
| WI_L_PB13H | L3M | 50.0 | 43.2 | -2538.4 | 38613.6 | 77224.2 | 70056.5 | -62649.8 |
| WI_L_PB13H | L6M | 50.0 | 43.2 | -2586.2 | 38613.6 | 77224.2 | 86850.1 | -65544.4 |
| WI_L_SL13S | L1M | 74.2 | 72.2 | -3842.5 | 13236.2 | 51252.7 | 27411.6 | 27411.6 |
| WI_L_SL13S | L3M | 41.6 | 37.2 | -1087.4 | 45087.2 | 77224.2 | 74220.8 | -42839.6 |
| WI_L_SL13S | L6M | 41.6 | 37.2 | -1523.3 | 45087.2 | 77224.2 | 73033.7 | -37514.0 |
| WI_J_BR3T45 | L1M | 56.2 | 51.1 | -6484.8 | 22462.1 | 51252.7 | 17631.3 | 17631.3 |
| WI_J_BR3T45 | L3M | 52.8 | 47.4 | -920.2 | 36418.2 | 77224.2 | 77891.7 | -50705.9 |
| WI_J_BR3T45 | L6M | 47.8 | 41.7 | -2233.5 | 40309.0 | 77224.2 | 77559.1 | -54900.7 |
| WI_K_W2AT45 | L1M | 46.8 | 43.3 | -6562.7 | 27254.1 | 51252.7 | 13700.5 | 13700.5 |
| WI_K_W2AT45 | L3M | 51.5 | 48.3 | -1203.1 | 37471.9 | 77224.2 | 74249.8 | -37096.0 |
| WI_K_W2AT45 | L6M | 51.5 | 48.3 | -1338.6 | 37471.9 | 77224.2 | 82324.0 | -47862.1 |
| WI_L_SL13T35 | L1M | 68.9 | 65.1 | -4582.1 | 15944.4 | 51252.7 | 23003.4 | 23003.4 |
| WI_L_SL13T35 | L3M | 26.6 | 17.6 | -2102.2 | 56717.1 | 77224.2 | 61243.7 | -32083.5 |
| WI_L_SL13T35 | L6M | 26.6 | 17.6 | -2330.9 | 56717.1 | 77224.2 | 70783.0 | -39984.9 |
| WI_I_ON15S | L1M | 52.7 | 43.9 | -9757.0 | 24263.6 | 51252.7 | 11808.9 | 11808.9 |
| WI_I_ON15S | L3M | 39.3 | 28.1 | -5207.0 | 46873.7 | 77224.2 | 74588.7 | -89868.8 |
| WI_I_ON15S | L6M | 39.3 | 28.1 | -3344.1 | 46873.7 | 77224.2 | 94361.3 | -83398.6 |
| WI_J_RS30T35 | L1M | 79.0 | 77.3 | -5605.3 | 10775.2 | 51252.7 | 25634.5 | 25634.5 |
| WI_J_RS30T35 | L3M | 50.6 | 46.6 | -908.3 | 38158.6 | 77224.2 | 82343.0 | -41488.6 |
| WI_J_RS30T35 | L6M | 50.6 | 46.6 | -1590.3 | 38158.6 | 77224.2 | 93056.2 | -43899.2 |
| WI_J_RS30T35 | HOLD | 7.3 | -0.1 | -3434.3 | 73098.7 | 78842.0 | 110152.0 | -63127.0 |
| WI_K_DOW1AS | L1M | 63.7 | 52.9 | -9791.7 | 18603.7 | 51252.7 | 16220.1 | 16220.1 |
| WI_K_DOW1AS | L3M | 40.3 | 22.6 | -2983.4 | 46100.8 | 77224.2 | 96778.0 | -77425.9 |
| WI_K_DOW1AS | L6M | 40.3 | 22.6 | -4924.2 | 46100.8 | 77224.2 | 104432.9 | -111633.0 |
| WI_K_W2S | L1M | 64.5 | 61.2 | -8396.7 | 18189.9 | 51252.7 | 16288.1 | 16288.1 |
| WI_K_W2S | L3M | 64.9 | 61.6 | -2210.0 | 27090.1 | 77224.2 | 96672.7 | -52814.6 |
| WI_K_W2S | L6M | 60.7 | 57.0 | -1846.0 | 30321.6 | 77224.2 | 106327.5 | -55401.4 |
| WI_K_W2S | HOLD | 2.7 | -6.4 | -4107.6 | 76692.8 | 78842.0 | 113676.1 | -88542.8 |
| WI_J_BR3S | L1M | 61.3 | 63.7 | -6004.0 | 19835.4 | 51252.7 | 13516.8 | 13516.8 |
| WI_J_BR3S | L3M | 61.2 | 63.6 | 4396.7 | 29993.2 | 77224.2 | 83169.8 | -66665.4 |
| WI_J_BR3S | L6M | 53.8 | 56.6 | 1043.4 | 35674.8 | 77224.2 | 87471.4 | -81571.0 |
| WI_J_BR3S | HOLD | 25.2 | 29.8 | -2144.8 | 58943.3 | 78842.0 | 96023.4 | -102406.2 |
| WI_J_BR3S | PRE | 36.4 | 40.3 | -1961.6 | 63274.5 | 99479.4 | 104974.3 | -166595.6 |
| WI_J_BR3S | X' | 50.0 | 53.1 | -641.8 | 61307.4 | 122552.7 | 82071.3 | -54645.7 |
| WI_J_BR3S | WF2W | 36.4 | 86.1 | -3018.3 | nan | nan | nan | nan |
| WI_J_RS30H | L1M | 55.6 | 48.0 | -6056.0 | 22762.2 | 51252.7 | 17247.6 | 17247.6 |
| WI_J_RS30H | L3M | 53.3 | 45.3 | -3679.1 | 36044.5 | 77224.2 | 79613.0 | -73418.1 |
| WI_J_RS30H | L6M | 53.3 | 45.3 | -3149.5 | 36044.5 | 77224.2 | 87792.4 | -70769.5 |
| WI_L_PUSHH | L1M | 49.7 | 43.4 | -7528.7 | 25785.9 | 51252.7 | 11587.1 | 11587.1 |
| WI_L_PUSHH | L3M | 54.6 | 48.9 | -3386.0 | 35087.7 | 77224.2 | 84244.1 | -71182.4 |
| WI_L_PUSHH | L6M | 54.6 | 48.9 | -2394.2 | 35087.7 | 77224.2 | 91043.9 | -49731.0 |
| WI_L_PUSHH | HOLD | 26.4 | 17.2 | -4156.3 | 58036.4 | 78842.0 | 109098.8 | -61452.5 |
| WI_G_BR3S | L1M | 67.1 | 68.7 | -6782.8 | 16856.9 | 51252.7 | 14170.2 | 14170.2 |
| WI_G_BR3S | L3M | 61.2 | 63.1 | 4420.2 | 29993.2 | 77224.2 | 86159.4 | -71759.8 |
| WI_G_BR3S | L6M | 53.3 | 55.6 | 817.4 | 36051.4 | 77224.2 | 90084.3 | -92400.3 |
| WI_I_ON2S | L1M | 53.7 | 48.5 | -10628.9 | 23711.7 | 51252.7 | 9745.0 | 9745.0 |
| WI_I_ON2S | L3M | 51.1 | 45.6 | -2253.1 | 37742.4 | 77224.2 | 91523.7 | -92854.8 |
| WI_I_ON2S | L6M | 51.1 | 45.6 | -2174.3 | 37742.4 | 77224.2 | 110803.1 | -95845.2 |
| WI_J_NQ60S | L1M | 55.2 | 47.6 | -4383.7 | 22937.5 | 51252.7 | 18599.8 | 18599.8 |
| WI_J_NQ60S | L3M | 50.3 | 41.8 | -1589.0 | 38376.9 | 77224.2 | 75561.9 | -50203.2 |
| WI_J_NQ60S | L6M | 50.3 | 41.8 | -3149.4 | 38376.9 | 77224.2 | 86498.1 | -66613.5 |
| WI_L_PB18S | L1M | 61.0 | 58.4 | -6660.4 | 19979.6 | 51252.7 | 13570.2 | 13570.2 |
| WI_L_PB18S | L3M | 52.1 | 49.0 | -205.4 | 36964.7 | 77224.2 | 75388.6 | -50216.1 |
| WI_L_PB18S | L6M | 52.1 | 49.0 | -1330.0 | 36964.7 | 77224.2 | 84063.5 | -67373.7 |
| WI_L_SL19H | L1M | 64.5 | 60.4 | -7076.9 | 18190.7 | 51252.7 | 18756.6 | 18756.6 |
| WI_L_SL19H | L3M | 44.0 | 37.5 | -2329.6 | 43224.7 | 77224.2 | 78255.4 | -50318.4 |
| WI_L_SL19H | L6M | 44.0 | 37.5 | -2232.5 | 43224.7 | 77224.2 | 81267.6 | -41370.0 |
| WI_N_BR3S | L1M | 66.3 | 66.4 | -8424.7 | 17274.5 | 51252.7 | 12345.3 | 12345.3 |
| WI_N_BR3S | L3M | 77.6 | 77.7 | 2087.5 | 17274.5 | 77224.2 | 109668.7 | -122330.0 |
| WI_N_BR3S | L6M | 77.6 | 77.7 | 68.4 | 17274.5 | 77224.2 | 147059.4 | -167919.2 |

## Behaviour-targeted use (standing principle 19:45Z): flag acts only on a same-side P7 re-entry after a P7 loser (within 120 min, same session list)
There are 651 such re-entries in 4,958 P7 trades (mean -$54 per trade against +$216 for all other P7 trades). Skipping all of them cuts the L6M stack drawdown by only -2.0 percent (HOLD -14.2, PRE 13.7, X-prime -1.8) and removes $48k of best-20-week winners against $65k of worst-20-week losers; half-size: L6M -0.8, HOLD -4.6. Best flag-conditioned re-entry cells (minimum equal-mean cut over four windows) are all below 9 percent and flag fewer than 300 trades: no robust cell.

## Behavioural scorecard (W-Q tool, exact trades, L6M, whole stack, per week)
- JN04RM L6M (stack, per week): full stops 25.4/wk $-38130; give-backs 9.9/wk (9.8 round-trips) realised $-11306, forgone vs target $28091; same-side losing runs max 13, p95 7, $-42885 lost on 3rd-and-later; no-new-evidence re-entries 43.3/wk $1885; recoveries cut 15.2/wk $39718, clipped fills 0.0/wk $0; pnl $19530/wk.
- WI_G_BR3S L6M (stack, per week): full stops 25.4/wk $-38297; give-backs 9.8/wk (9.7 round-trips) realised $-11293, forgone vs target $27911; same-side losing runs max 13, p95 6, $-39955 lost on 3rd-and-later; no-new-evidence re-entries 39.2/wk $1185; recoveries cut 14.7/wk $37599, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $19408/wk, losers avoided $18264/wk, net -393 $/wk; pnl $19137/wk.
- WI_I_ON15S L6M (stack, per week): full stops 25.2/wk $-37911; give-backs 9.6/wk (9.5 round-trips) realised $-10923, forgone vs target $27074; same-side losing runs max 13, p95 6, $-39365 lost on 3rd-and-later; no-new-evidence re-entries 40.4/wk $1166; recoveries cut 14.9/wk $38252, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $13267/wk, losers avoided $9756/wk, net -1477 $/wk; pnl $18053/wk.
- WI_I_ON2S L6M (stack, per week): full stops 25.2/wk $-37942; give-backs 9.5/wk (9.4 round-trips) realised $-10702, forgone vs target $26691; same-side losing runs max 13, p95 6, $-37527 lost on 3rd-and-later; no-new-evidence re-entries 39.8/wk $1571; recoveries cut 14.7/wk $37637, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $16129/wk, losers avoided $13422/wk, net -264 $/wk; pnl $19266/wk.
- WI_J_BR3S L6M (stack, per week): full stops 25.4/wk $-38252; give-backs 9.8/wk (9.7 round-trips) realised $-11326, forgone vs target $27992; same-side losing runs max 13, p95 7, $-40619 lost on 3rd-and-later; no-new-evidence re-entries 41.2/wk $1521; recoveries cut 14.9/wk $37941, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $17749/wk, losers avoided $17043/wk, net -65 $/wk; pnl $19465/wk.
- WI_J_BR3T45 L6M (stack, per week): full stops 25.4/wk $-38231; give-backs 9.4/wk (9.2 round-trips) realised $-10360, forgone vs target $25562; same-side losing runs max 13, p95 7, $-43327 lost on 3rd-and-later; no-new-evidence re-entries 43.5/wk $2281; recoveries cut 15.3/wk $40661, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2538/wk, losers avoided $2277/wk, net -509 $/wk; pnl $19021/wk.
- WI_J_ES60S L6M (stack, per week): full stops 25.3/wk $-38028; give-backs 9.4/wk (9.2 round-trips) realised $-10669, forgone vs target $26478; same-side losing runs max 13, p95 7, $-41534 lost on 3rd-and-later; no-new-evidence re-entries 41.5/wk $1546; recoveries cut 14.8/wk $38563, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $8392/wk, losers avoided $7033/wk, net -1226 $/wk; pnl $18305/wk.
- WI_J_NQ60S L6M (stack, per week): full stops 25.3/wk $-37976; give-backs 9.5/wk (9.4 round-trips) realised $-10704, forgone vs target $26709; same-side losing runs max 13, p95 6, $-39788 lost on 3rd-and-later; no-new-evidence re-entries 40.2/wk $2380; recoveries cut 14.6/wk $37653, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $13575/wk, losers avoided $12103/wk, net -1658 $/wk; pnl $17872/wk.
- WI_J_RS15H L6M (stack, per week): full stops 25.4/wk $-38034; give-backs 9.9/wk (9.8 round-trips) realised $-10915, forgone vs target $27124; same-side losing runs max 13, p95 7, $-42321 lost on 3rd-and-later; no-new-evidence re-entries 44.0/wk $1533; recoveries cut 15.5/wk $38697, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $342/wk, losers avoided $539/wk, net -941 $/wk; pnl $18589/wk.
- WI_J_RS30H L6M (stack, per week): full stops 25.5/wk $-38276; give-backs 9.9/wk (9.8 round-trips) realised $-11002, forgone vs target $27348; same-side losing runs max 13, p95 7, $-42920 lost on 3rd-and-later; no-new-evidence re-entries 44.1/wk $1686; recoveries cut 15.3/wk $37636, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $208/wk, losers avoided $295/wk, net -1509 $/wk; pnl $18021/wk.
- WI_J_RS30T35 L6M (stack, per week): full stops 25.5/wk $-38189; give-backs 9.2/wk (9.1 round-trips) realised $-10401, forgone vs target $25868; same-side losing runs max 13, p95 6, $-40963 lost on 3rd-and-later; no-new-evidence re-entries 43.5/wk $2955; recoveries cut 14.9/wk $39205, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2441/wk, losers avoided $1922/wk, net +363 $/wk; pnl $19893/wk.
- WI_K_DOW1AS L6M (stack, per week): full stops 25.4/wk $-37932; give-backs 9.6/wk (9.5 round-trips) realised $-10431, forgone vs target $25863; same-side losing runs max 13, p95 6, $-35717 lost on 3rd-and-later; no-new-evidence re-entries 40.0/wk $1543; recoveries cut 14.2/wk $34685, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $21275/wk, losers avoided $18005/wk, net -2901 $/wk; pnl $16629/wk.
- WI_K_W2AS L6M (stack, per week): full stops 25.4/wk $-38081; give-backs 9.9/wk (9.8 round-trips) realised $-10968, forgone vs target $27363; same-side losing runs max 13, p95 6, $-41119 lost on 3rd-and-later; no-new-evidence re-entries 42.2/wk $2243; recoveries cut 14.9/wk $37388, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $5402/wk, losers avoided $5430/wk, net +40 $/wk; pnl $19570/wk.
- WI_K_W2AT45 L6M (stack, per week): full stops 25.4/wk $-38181; give-backs 9.8/wk (9.6 round-trips) realised $-10892, forgone vs target $27140; same-side losing runs max 13, p95 7, $-42691 lost on 3rd-and-later; no-new-evidence re-entries 43.8/wk $2743; recoveries cut 15.3/wk $39223, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $1220/wk, losers avoided $737/wk, net +251 $/wk; pnl $19781/wk.
- WI_K_W2S L6M (stack, per week): full stops 25.2/wk $-37882; give-backs 9.6/wk (9.5 round-trips) realised $-10649, forgone vs target $26653; same-side losing runs max 11, p95 6, $-38739 lost on 3rd-and-later; no-new-evidence re-entries 40.2/wk $2632; recoveries cut 14.3/wk $35693, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $9109/wk, losers avoided $8854/wk, net +64 $/wk; pnl $19594/wk.
- WI_L_PB13H L6M (stack, per week): full stops 25.4/wk $-38019; give-backs 9.9/wk (9.8 round-trips) realised $-10640, forgone vs target $26459; same-side losing runs max 13, p95 6, $-42157 lost on 3rd-and-later; no-new-evidence re-entries 44.4/wk $1951; recoveries cut 15.5/wk $36873, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $391/wk, losers avoided $787/wk, net -1130 $/wk; pnl $18400/wk.
- WI_L_PB18S L6M (stack, per week): full stops 25.2/wk $-37803; give-backs 9.1/wk (9.0 round-trips) realised $-10387, forgone vs target $25913; same-side losing runs max 10, p95 6, $-37541 lost on 3rd-and-later; no-new-evidence re-entries 37.4/wk $2805; recoveries cut 13.9/wk $34898, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $18204/wk, losers avoided $19048/wk, net +266 $/wk; pnl $19796/wk.
- WI_L_PUSHH L6M (stack, per week): full stops 25.5/wk $-38238; give-backs 10.0/wk (9.9 round-trips) realised $-10608, forgone vs target $26098; same-side losing runs max 13, p95 7, $-42784 lost on 3rd-and-later; no-new-evidence re-entries 44.4/wk $2049; recoveries cut 15.5/wk $37935, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $439/wk, losers avoided $976/wk, net -791 $/wk; pnl $18739/wk.
- WI_L_SL13S L6M (stack, per week): full stops 25.4/wk $-38216; give-backs 9.1/wk (9.0 round-trips) realised $-10347, forgone vs target $25489; same-side losing runs max 13, p95 6, $-40201 lost on 3rd-and-later; no-new-evidence re-entries 39.8/wk $2445; recoveries cut 14.2/wk $35279, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $19867/wk, losers avoided $18845/wk, net +289 $/wk; pnl $19819/wk.
- WI_L_SL13T35 L6M (stack, per week): full stops 25.4/wk $-38129; give-backs 8.9/wk (8.8 round-trips) realised $-10063, forgone vs target $24777; same-side losing runs max 13, p95 7, $-42080 lost on 3rd-and-later; no-new-evidence re-entries 43.3/wk $1104; recoveries cut 15.0/wk $39004, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $4078/wk, losers avoided $2538/wk, net -622 $/wk; pnl $18908/wk.
- WI_L_SL19H L6M (stack, per week): full stops 25.5/wk $-38226; give-backs 9.8/wk (9.8 round-trips) realised $-10964, forgone vs target $27065; same-side losing runs max 13, p95 7, $-43009 lost on 3rd-and-later; no-new-evidence re-entries 43.7/wk $1831; recoveries cut 15.3/wk $38631, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $13/wk, losers avoided $174/wk, net -390 $/wk; pnl $19140/wk.
- WI_N_BR3S L6M (stack, per week): full stops 21.6/wk $-34323; give-backs 8.3/wk (8.3 round-trips) realised $-9141, forgone vs target $23997; same-side losing runs max 14, p95 6, $-29442 lost on 3rd-and-later; no-new-evidence re-entries 32.2/wk $-997; recoveries cut 14.7/wk $37905, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $44763/wk, losers avoided $44405/wk, net -1811 $/wk; pnl $17719/wk.

Plain reading: an entry gate leaves the three defects (full stops, give-backs, same-side losing runs) where they were, because it only removes entries and the entries it removes are not the ones that form the runs; by the standing principle families I-L are therefore NOT acceptable as exits or re-entry fixes on their own. Their use is as evidence tests inside the re-entry rule (W-M probe / confirm).
