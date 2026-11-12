# DS3_WORKS_I - T-WORKS / P7 FIX, worker W-I (families I room to target, J cross-market, K context, L P7 signal internals), page 2026-11-11 23:58Z
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
| WI_J_BR3S | L1M | 26.7 | 29.9 | -3564.8 | 19835.4 | 27055.7 | -414.4 | -414.4 |
| WI_J_BR3S | L3M | 28.1 | 31.2 | -811.4 | 29993.2 | 41699.4 | 29596.9 | -17763.8 |
| WI_J_BR3S | L6M | 14.4 | 18.1 | 782.7 | 35674.8 | 41699.4 | 33013.6 | -57351.5 |
| WI_J_RS15H | L1M | 4.4 | 1.5 | 398.3 | 25860.9 | 27055.7 | -8967.6 | -8967.6 |
| WI_J_RS15H | L3M | -13.5 | -17.0 | -142.2 | 47325.8 | 41699.4 | 995.9 | -6839.6 |
| WI_J_RS15H | L6M | -13.5 | -17.0 | -518.8 | 47325.8 | 41699.4 | 9437.5 | -14404.1 |
| WI_J_NQ60S | L1M | 15.2 | 13.8 | -762.5 | 22937.5 | 27055.7 | 4668.6 | 4668.6 |
| WI_J_NQ60S | L3M | 8.0 | 6.4 | 969.0 | 38376.9 | 41699.4 | 11382.0 | -1301.6 |
| WI_J_NQ60S | L6M | 8.0 | 6.4 | -288.0 | 38376.9 | 41699.4 | 21433.4 | -57892.7 |

vs LPB
| cell | window | cut | eq_cut | dmean | dd | dd_ref | d_worst5 | d_best5 |
|--|--|--|--|--|--|--|--|--|
| WI_J_BR3S | L1M | 61.3 | 63.7 | -6004.0 | 19835.4 | 51252.7 | 13516.8 | 13516.8 |
| WI_J_BR3S | L3M | 61.2 | 63.6 | 4396.7 | 29993.2 | 77224.2 | 83169.8 | -66665.4 |
| WI_J_BR3S | L6M | 53.8 | 56.6 | 1043.4 | 35674.8 | 77224.2 | 87471.4 | -81571.0 |
| WI_J_RS15H | L1M | 49.5 | 42.7 | -10029.2 | 25860.9 | 51252.7 | 4963.7 | 4963.7 |
| WI_J_RS15H | L3M | 38.7 | 30.4 | -3229.6 | 47325.8 | 77224.2 | 71571.3 | -55741.2 |
| WI_J_RS15H | L6M | 38.7 | 30.4 | -2576.8 | 47325.8 | 77224.2 | 80897.7 | -46417.0 |
| WI_J_NQ60S | L1M | 55.2 | 47.6 | -4383.7 | 22937.5 | 51252.7 | 18599.8 | 18599.8 |
| WI_J_NQ60S | L3M | 50.3 | 41.8 | -1589.0 | 38376.9 | 77224.2 | 75561.9 | -50203.2 |
| WI_J_NQ60S | L6M | 50.3 | 41.8 | -3149.4 | 38376.9 | 77224.2 | 86498.1 | -66613.5 |

## Behaviour-targeted use (standing principle 19:45Z): flag acts only on a same-side P7 re-entry after a P7 loser (within 120 min, same session list)
There are 651 such re-entries in 4,958 P7 trades (mean -$54 per trade against +$216 for all other P7 trades). Skipping all of them cuts the L6M stack drawdown by only -2.0 percent (HOLD -14.2, PRE 13.7, X-prime -1.8) and removes $48k of best-20-week winners against $65k of worst-20-week losers; half-size: L6M -0.8, HOLD -4.6. Best flag-conditioned re-entry cells (minimum equal-mean cut over four windows) are all below 9 percent and flag fewer than 300 trades: no robust cell.

## Behavioural scorecard (W-Q tool, exact trades, L6M, whole stack, per week)
- JN04RM L6M (stack, per week): full stops 25.4/wk $-38130; give-backs 9.9/wk (9.8 round-trips) realised $-11306, forgone vs target $28091; same-side losing runs max 13, p95 7, $-42885 lost on 3rd-and-later; no-new-evidence re-entries 43.3/wk $1885; recoveries cut 15.2/wk $39718, clipped fills 0.0/wk $0; pnl $19530/wk.
- WI_J_BR3S L6M (stack, per week): full stops 25.4/wk $-38252; give-backs 9.8/wk (9.7 round-trips) realised $-11326, forgone vs target $27992; same-side losing runs max 13, p95 7, $-40619 lost on 3rd-and-later; no-new-evidence re-entries 41.2/wk $1521; recoveries cut 14.9/wk $37941, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $17749/wk, losers avoided $17043/wk, net -65 $/wk; pnl $19465/wk.
- WI_J_NQ60S L6M (stack, per week): full stops 25.3/wk $-37976; give-backs 9.5/wk (9.4 round-trips) realised $-10704, forgone vs target $26709; same-side losing runs max 13, p95 6, $-39788 lost on 3rd-and-later; no-new-evidence re-entries 40.2/wk $2380; recoveries cut 14.6/wk $37653, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $13575/wk, losers avoided $12103/wk, net -1658 $/wk; pnl $17872/wk.
- WI_J_RS15H L6M (stack, per week): full stops 25.4/wk $-38034; give-backs 9.9/wk (9.8 round-trips) realised $-10915, forgone vs target $27124; same-side losing runs max 13, p95 7, $-42321 lost on 3rd-and-later; no-new-evidence re-entries 44.0/wk $1533; recoveries cut 15.5/wk $38697, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $342/wk, losers avoided $539/wk, net -941 $/wk; pnl $18589/wk.

Plain reading: an entry gate leaves the three defects (full stops, give-backs, same-side losing runs) where they were, because it only removes entries and the entries it removes are not the ones that form the runs; by the standing principle families I-L are therefore NOT acceptable as exits or re-entry fixes on their own. Their use is as evidence tests inside the re-entry rule (W-M probe / confirm).
