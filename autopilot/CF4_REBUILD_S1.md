# CF4_REBUILD_S1 - T-REBUILD Stage 1, family 1 (indicator / alt-bar / structure / state conditions) scored per book x session x cell (W-CF4)

**Verdict (data ends 2026-11-11) line (PREVIEW on signals_all outcomes = JN05W2 taken trades + 1-minute-hypothetical skipped signals, NOT the raw table; to be re-run on the Stage 0 raw trades): 22071 conditions scored (13 family-1 blocks plus IRL/ERL); effect on mean R: 16470 of 1103550 tests beat their cell's nonsense bar (1.49%, nominal 1%) and 5840 also keep the sign every year and in L6M (0.53%; the 200 nonsense controls pass the same full rule in ~0.44%); MFE: 2.06% beat the bar; MAE: 2.69% beat the bar. MAE and MFE effects are largely mechanical (conditions that mark high or low volatility move the excursions), read them as a map, not as edge.**

Scoring: per condition and cell (pooled, book, session, book x session; prev outcomes) lift of yes vs no for R (higher better), MFE points (higher better), MAE points (lower better); weekly cluster-robust zw; bar = 99th percentile of |zw| of the 200 nonsense controls in the same cell and outcome; R pass additionally needs the same lift sign in every year with >= 30 per side and in L6M. Code code/th_confl_cf4/c4_s1.py; tables /mnt/l2/l2vast/_confl/cols_cf4/s1_prev/; manifest /mnt/l2/l2vast/_confl/cols_cf4/s1_manifest.csv (conditions, family, feed flags: D7 can compute all of them live from its own completed bars; footprint and delta/CVD need tick data with aggressor side = NT8 time&sales, flagged not dropped).

| block | family | conditions | R tests | R beat bar | R pass | MFE beat bar | MFE pass | MAE beat bar | MAE pass |
|---|---|---|---|---|---|---|---|---|---|
| alt_range8 | 1 | 2311 | 115550 | 1874 (1.62%) | 1045 | 1663 (1.44%) | 859 | 3976 (3.44%) | 2436 |
| altagree | 1 | 4622 | 231100 | 2114 (0.91%) | 736 | 3733 (1.62%) | 1557 | 4450 (1.93%) | 1955 |
| candle | 1 | 3370 | 168500 | 1562 (0.93%) | 423 | 1890 (1.12%) | 531 | 1599 (0.95%) | 604 |
| fp | 1 | 197 | 9850 | 155 (1.57%) | 62 | 171 (1.74%) | 83 | 276 (2.80%) | 139 |
| geom | 1 | 1188 | 59400 | 722 (1.22%) | 193 | 898 (1.51%) | 312 | 853 (1.44%) | 330 |
| irl | 2 | 334 | 16700 | 195 (1.17%) | 86 | 362 (2.17%) | 147 | 572 (3.43%) | 306 |
| ml | 1 | 222 | 11100 | 143 (1.29%) | 49 | 219 (1.97%) | 95 | 307 (2.77%) | 149 |
| osc | 1 | 3144 | 157200 | 3456 (2.20%) | 1054 | 4834 (3.08%) | 1798 | 5897 (3.75%) | 2799 |
| smc | 1 | 2030 | 101500 | 1969 (1.94%) | 700 | 2258 (2.22%) | 862 | 2476 (2.44%) | 1151 |
| squeeze | 1 | 408 | 20400 | 367 (1.80%) | 140 | 545 (2.67%) | 236 | 682 (3.34%) | 297 |
| state | 1 | 317 | 15850 | 338 (2.13%) | 127 | 402 (2.54%) | 145 | 648 (4.09%) | 314 |
| trend | 1 | 3330 | 166500 | 3158 (1.90%) | 1048 | 5127 (3.08%) | 2231 | 6991 (4.20%) | 3438 |
| vol | 1 | 598 | 29900 | 417 (1.39%) | 177 | 582 (1.95%) | 292 | 988 (3.30%) | 513 |

## Strongest passing tests on R (all blocks)

| block | cell | book | sess | condition | n yes | lift R | zw | bar99 | years pos/n | lift L6M |
|---|---|---|---|---|---|---|---|---|---|---|
| altagree | book_sess | U7 | 3 | c4_agr_kvo_fresh5_ge6 | 100 | -0.211 | -7.3 | 2.9 | 0/2 | -0.112 |
| altagree | book_sess | A7 | 1 | c4_agr_crsi_ewith_z1_ge6 | 106 | -0.377 | -6.7 | 2.9 | 0/2 | -0.364 |
| alt_ha60 | ALL |  |  | c4_smie_ha60_eleave | 6542 | -0.123 | -5.9 | 2.4 | 0/4 | -0.101 |
| trend | sess |  | 3 | c4_alma_x_1d_fresh1 | 580 | -0.272 | -5.6 | 2.0 | 0/4 | -0.168 |
| altagree | book_sess | H7 | 4 | c4_agr_w1_psar_0.01_fresh5_ge3 | 198 | -0.184 | -5.6 | 2.9 | 0/4 | -0.443 |
| candle | sess |  | 2 | c4_cdl_hammer_5m_against | 118 | 0.335 | 5.4 | 2.7 | 2/2 | 0.315 |
| osc | sess |  | 3 | c4_elderF_bull_15m_nodiv | 14655 | 0.144 | 5.4 | 2.0 | 4/4 | 0.112 |
| geom | sess |  | 0 | c4_flag_5m_against | 870 | -0.177 | -5.4 | 2.9 | 0/4 | -0.097 |
| altagree | sess |  | 0 | c4_agr_kstS_side_ge3 | 10562 | 0.268 | 5.4 | 2.9 | 4/4 | 0.230 |
| alt_ha60 | book | A7 |  | c4_w1_rsi21_ha60_eleave | 969 | -0.187 | -5.4 | 2.3 | 0/4 | -0.249 |
| alt_ha60 | book | A7 |  | c4_rsima21_ha60_eleave | 972 | -0.187 | -5.4 | 2.3 | 0/4 | -0.249 |
| altagree | sess |  | 1 | c4_agr_crsi_ewith_z1_ge6 | 141 | -0.255 | -5.4 | 2.5 | 0/3 | -0.268 |
| alt_ha60 | book | A7 |  | c4_elderF_bear_ha60_divwith | 2476 | -0.108 | -5.3 | 2.3 | 0/4 | -0.035 |
| alt_ha60 | book | A7 |  | c4_ker_dir_ha60_divwith | 2715 | -0.121 | -5.3 | 2.3 | 0/4 | -0.115 |
| osc | sess |  | 3 | c4_elder_bull_15m_nodiv | 14857 | 0.144 | 5.3 | 2.0 | 4/4 | 0.154 |
| osc | book | M7 |  | c4_tsiF_60m_eleave | 1785 | -0.138 | -5.2 | 2.2 | 0/4 | -0.139 |
| alt_ha60 | book | A7 |  | c4_w1_trix8_ha60_divwith | 2506 | -0.114 | -5.2 | 2.3 | 0/4 | -0.056 |
| squeeze | ALL |  |  | c4_sqz_alt_ha60_fired5_against | 7165 | -0.083 | -5.2 | 2.4 | 0/4 | -0.171 |
| alt_ha60 | ALL |  |  | c4_w1_cmo14_ha60_eleave | 8921 | -0.097 | -5.2 | 2.4 | 0/4 | -0.144 |
| trend | book | A7 |  | c4_ichiF_score_60m_eleave | 2339 | -0.163 | -5.1 | 2.3 | 0/4 | -0.105 |
| alt_ha60 | book | A7 |  | c4_w1_aroon50_ha60_eagainst | 2187 | -0.148 | -5.1 | 2.3 | 0/4 | -0.101 |
| state | ALL |  |  | c4_st_60m_sqzk20_fa_1_3 | 3107 | -0.093 | -5.1 | 2.4 | 0/4 | -0.147 |
| altagree | sess |  | 0 | c4_agr_sd_near_hold3_ge3 | 743 | -0.125 | -5.1 | 2.9 | 0/4 | -0.020 |
| alt_ha60 | sess |  | 3 | c4_tsi_ha60_divwith | 1438 | -0.103 | -5.1 | 2.0 | 0/4 | -0.006 |
| osc | book_sess | A7 | 3 | c4_elderF_bull_15m_nodiv | 3189 | 0.296 | 5.0 | 2.6 | 4/4 | 0.402 |
