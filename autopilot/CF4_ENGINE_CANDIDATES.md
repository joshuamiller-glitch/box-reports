# CF4_ENGINE_CANDIDATES - best distinct condition per near-duplicate cluster for P7 Asia and K7 (alt_range8, alt_ha60, alt_ha5, alt_tick2000)

**Verdict line (data end 2026-11-11): 688 distinct condition clusters pass alone in P7 Asia / K7 cells, but at 1-2x the nonsense rate and with lifts of 0.04-0.12 R per signal, below the planted-edge floor of book x session cells; they are engine candidates, not leads.**
688 clusters in total across the 8 target cells (CSV); the table lists the top 6 per cell by |zw| whose sign survives removing W44.


Source: pass-alone tests of DS3_CONFLUENCE_ITEMS_CF4_ZW.md (weekly cluster-robust zw above the nonsense 99th percentile in the cell, same sign every year and in L6M). One row per cluster of passing conditions in the cell (|r|>0.9 between yes-vectors), the strongest by |zw|. Columns are keyed by sid=sig_id in /mnt/l2/l2vast/_confl/cols_cf4/cf4_<set>.parquet. ORDER FOR THE ENGINE: (1) SIZE form first: the column "size_dir" (does not free the book); (2) skip form second, always against an engine random skip with the same keep share (autopilot/PATH_EFFECT_RULE.md). size_gain_R columns are a screen (sum of (mult-1)*R per signal on the in_pos=0 universe), not an engine result. zw_W44_removed = the same weekly t with 2026-W44 (10-26..11-01) removed. Full table: /mnt/l2/l2vast/_confl/cf4_candidates/engine_candidates.csv. Data end 2026-11-11.

| cell | set | condition | cluster size | n yes | share | lift R | zw | bar99 | zw no W44 | years +/n | lift L6M | siblings pass | size form | size gain R/signal full | L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book K7 | alt_ha60 | c4_w1_hv_pct50_ha60_hi | 1 | 7877 | 0.52 | -0.040 | -3.8 | 2.6 | -3.8 | 0/4 | -0.027 | 1 | yes x0.5 / no x1.5 | 0.0085 | 0.0073 |
| book K7 | alt_ha60 | c4_w1_trix8_ha60_divwith | 2 | 2341 | 0.16 | -0.062 | -3.6 | 2.6 | -3.6 | 0/4 | -0.032 | 1 | yes x0.5 / no x1.5 | 0.0117 | -0.0007 |
| book K7 | alt_ha60 | c4_don55_pos_ha60_eagainst | 2 | 320 | 0.02 | -0.126 | -3.5 | 2.6 | -3.5 | 0/4 | -0.095 | 1 | yes x0.5 / no x1.5 | 0.0073 | -0.0057 |
| book K7 | alt_range8 | c4_w1_willr21_range8_eenter | 1 | 3119 | 0.21 | 0.053 | 3.4 | 2.6 | 3.3 | 4/4 | 0.059 | 1 | yes x1.5 / no x0.5 | 0.0057 | 0.0130 |
| book K7 | alt_range8 | c4_ichiS_kj_range8_rise | 1 | 7572 | 0.50 | 0.042 | 3.4 | 2.6 | 3.4 | 4/4 | 0.045 | 1 | yes x1.5 / no x0.5 | 0.0105 | 0.0111 |
| book K7 | alt_ha60 | c4_almaS_px_ha60_divwith | 1 | 2003 | 0.13 | -0.072 | -3.3 | 2.6 | -3.3 | 0/4 | -0.013 | 1 | yes x0.5 / no x1.5 | 0.0118 | -0.0050 |
| book_sess K7 sess0 | alt_range8 | c4_w1_vwma200_px_range8_side | 1 | 3106 | 0.95 | 0.110 | 4.3 | 2.3 | 4.3 | 3/3 | 0.100 | 1 | yes x1.5 / no x0.5 | 0.0247 | 0.0258 |
| book_sess K7 sess0 | alt_range8 | c4_vsa_upthrust_range8_against | 1 | 102 | 0.03 | 0.317 | 4.2 | 2.3 | 3.9 | 2/2 | 0.280 | 1 | yes x1.5 / no x0.5 | -0.0108 | -0.0168 |
| book_sess K7 sess0 | alt_ha5 | c4_w1_donchian20_width_ha5_hi | 1 | 822 | 0.25 | 0.112 | 3.9 | 2.3 | 3.9 | 4/4 | 0.050 | 1 | yes x1.5 / no x0.5 | 0.0103 | 0.0028 |
| book_sess K7 sess0 | alt_tick2000 | c4_w1_eom14_tick2000_side | 1 | 1870 | 0.57 | 0.104 | 3.8 | 2.3 | 3.9 | 4/4 | 0.035 | 1 | yes x1.5 / no x0.5 | 0.0286 | 0.0121 |
| book_sess K7 sess0 | alt_tick2000 | c4_ssl_tick2000_hold3 | 1 | 1535 | 0.47 | 0.127 | 3.8 | 2.3 | 3.8 | 4/4 | 0.045 | 3 | yes x1.5 / no x0.5 | 0.0305 | 0.0093 |
| book_sess K7 sess0 | alt_tick2000 | c4_stc_tick2000_ewith | 1 | 1591 | 0.49 | 0.110 | 3.7 | 2.3 | 3.7 | 4/4 | 0.080 | 1 | yes x1.5 / no x0.5 | 0.0269 | 0.0195 |
| book_sess K7 sess1 | alt_ha60 | c4_ichi_futcloud_ha60_fresh5 | 1 | 158 | 0.06 | 0.201 | 4.3 | 2.4 | 4.0 | 2/2 | 0.260 | 1 | yes x1.5 / no x0.5 | 0.0049 | 0.0282 |
| book_sess K7 sess1 | alt_ha5 | c4_w1_stoch14_ha5_rise | 1 | 1825 | 0.66 | -0.120 | -4.1 | 2.4 | -4.2 | 0/4 | -0.003 | 1 | yes x0.5 / no x1.5 | 0.0246 | 0.0065 |
| book_sess K7 sess1 | alt_range8 | c4_w1_ema50_px_range8_side | 1 | 2615 | 0.95 | 0.137 | 3.9 | 2.4 | 3.6 | 2/2 | 0.290 | 1 | yes x1.5 / no x0.5 | 0.0129 | 0.0035 |
| book_sess K7 sess1 | alt_ha5 | c4_w1_cci20_ha5_divwith | 2 | 329 | 0.12 | -0.235 | -3.6 | 2.4 | -3.5 | 0/3 | -0.158 | 1 | yes x0.5 / no x1.5 | 0.0299 | 0.0036 |
| book_sess K7 sess1 | alt_range8 | c4_w1_mfi21_range8_ewith | 1 | 140 | 0.05 | 0.176 | 3.6 | 2.4 | 3.6 | 2/2 | 0.254 | 1 | yes x1.5 / no x0.5 | 0.0024 | 0.0231 |
| book_sess K7 sess1 | alt_range8 | c4_elderS_impulse_range8_against | 1 | 203 | 0.07 | -0.164 | -3.5 | 2.4 | -3.4 | 0/2 | -0.226 | 1 | yes x0.5 / no x1.5 | 0.0169 | 0.0085 |
| book_sess K7 sess2 | alt_ha5 | c4_w1_adx7_ha5_hi_z1 | 1 | 846 | 0.90 | -0.419 | -4.3 | 2.3 | -3.9 | 0/2 | -0.436 | 1 | yes x0.5 / no x1.5 | 0.0366 | 0.0388 |
| book_sess K7 sess2 | alt_ha5 | c4_w1_demarker7_ha5_eleave | 1 | 196 | 0.21 | 0.272 | 3.9 | 2.3 | 3.9 | 3/3 | 0.288 | 1 | yes x1.5 / no x0.5 | 0.0453 | 0.0291 |
| book_sess K7 sess2 | alt_tick2000 | c4_sslS_tick2000_against | 4 | 260 | 0.28 | 0.225 | 3.7 | 2.3 | 3.6 | 3/3 | 0.348 | 1 | yes x1.5 / no x0.5 | 0.0452 | 0.0680 |
| book_sess K7 sess2 | alt_ha5 | c4_elderS_bull_ha5_side | 1 | 694 | 0.74 | -0.199 | -3.7 | 2.3 | -3.7 | 0/3 | -0.217 | 1 | yes x0.5 / no x1.5 | 0.0384 | 0.0243 |
| book_sess K7 sess2 | alt_ha5 | c4_w1_demarker7_ha5_ewith | 1 | 496 | 0.53 | -0.246 | -3.6 | 2.3 | -3.6 | 0/4 | -0.248 | 1 | yes x0.5 / no x1.5 | 0.0614 | 0.0583 |
| book_sess K7 sess2 | alt_ha5 | c4_w1_cmo9_ha5_eenter | 1 | 141 | 0.15 | -0.283 | -3.6 | 2.3 | -3.6 | 0/2 | -0.556 | 1 | yes x0.5 / no x1.5 | 0.0360 | 0.0777 |
| book_sess K7 sess3 | alt_ha5 | c4_w1_vortex14_ha5_divwith | 1 | 513 | 0.15 | -0.194 | -3.8 | 2.3 | -3.7 | 0/4 | -0.222 | 1 | yes x0.5 / no x1.5 | 0.0270 | 0.0203 |
| book_sess K7 sess3 | alt_ha60 | c4_w1_stoch14_ha60_eenter | 1 | 122 | 0.04 | 0.198 | 3.6 | 2.3 | 3.4 | 2/2 | 0.471 | 1 | yes x1.5 / no x0.5 | 0.0041 | 0.0371 |
| book_sess K7 sess3 | alt_ha5 | c4_obS_dres_ha5_rise | 2 | 1154 | 0.34 | -0.100 | -3.4 | 2.3 | -3.5 | 0/4 | -0.097 | 1 | yes x0.5 / no x1.5 | 0.0178 | 0.0164 |
| book_sess K7 sess3 | alt_tick2000 | c4_w1_trix8_tick2000_divwith | 1 | 290 | 0.08 | 0.106 | 3.3 | 2.3 | 3.3 | 4/4 | 0.059 | 1 | yes x1.5 / no x0.5 | 0.0056 | 0.0186 |
| book_sess K7 sess3 | alt_ha5 | c4_obF_dres_ha5_rise | 1 | 1159 | 0.34 | -0.101 | -3.2 | 2.3 | -3.3 | 0/4 | -0.102 | 1 | yes x0.5 / no x1.5 | 0.0189 | 0.0174 |
| book_sess K7 sess3 | alt_ha5 | c4_w1_linreg_slope50_ha5_divwith | 1 | 646 | 0.19 | 0.145 | 3.2 | 2.3 | 3.3 | 4/4 | 0.149 | 1 | yes x1.5 / no x0.5 | 0.0203 | 0.0354 |
| book_sess K7 sess4 | alt_tick2000 | c4_lrcF_tick2000_fresh5 | 2 | 1133 | 0.43 | 0.131 | 4.0 | 2.3 | 3.9 | 4/4 | 0.253 | 1 | yes x1.5 / no x0.5 | 0.0324 | 0.0633 |
| book_sess K7 sess4 | alt_ha5 | c4_w1_linreg_chan20_ha5_eenter | 1 | 112 | 0.04 | -0.106 | -3.8 | 2.3 | -3.8 | 0/2 | -0.237 | 1 | yes x0.5 / no x1.5 | 0.0021 | -0.0031 |
| book_sess K7 sess4 | alt_tick2000 | c4_hull_tick2000_fresh1 | 1 | 174 | 0.07 | 0.190 | 3.6 | 2.3 | 3.4 | 3/3 | 0.233 | 1 | yes x1.5 / no x0.5 | 0.0137 | 0.0233 |
| book_sess K7 sess4 | alt_ha5 | c4_kstS_ha5_nodiv | 1 | 2170 | 0.81 | 0.143 | 3.5 | 2.3 | 3.4 | 4/4 | 0.244 | 1 | yes x1.5 / no x0.5 | 0.0200 | 0.0283 |
| book_sess K7 sess4 | alt_tick2000 | c4_w1_cmo9_tick2000_nodiv | 1 | 2215 | 0.83 | 0.179 | 3.4 | 2.3 | 3.6 | 4/4 | 0.010 | 1 | yes x1.5 / no x0.5 | 0.0235 | -0.0065 |
| book_sess K7 sess4 | alt_tick2000 | c4_tsiS_tick2000_fresh5 | 1 | 774 | 0.29 | 0.127 | 3.3 | 2.3 | 3.3 | 4/4 | 0.173 | 1 | yes x1.5 / no x0.5 | 0.0271 | 0.0403 |
| book_sess K7 sess5 | alt_range8 | c4_w1_ema8_px_range8_fresh5 | 3 | 896 | 0.45 | 0.119 | 4.1 | 2.6 | 4.0 | 4/4 | 0.200 | 1 | yes x1.5 / no x0.5 | 0.0302 | 0.0532 |
| book_sess K7 sess5 | alt_range8 | c4_don20_pos_range8_fresh5 | 3 | 477 | 0.24 | 0.134 | 3.7 | 2.6 | 3.6 | 4/4 | 0.203 | 1 | yes x1.5 / no x0.5 | 0.0287 | 0.0625 |
| book_sess K7 sess5 | alt_range8 | c4_t3_px_range8_fresh5 | 1 | 1116 | 0.56 | 0.096 | 3.6 | 2.6 | 3.5 | 4/4 | 0.160 | 1 | yes x1.5 / no x0.5 | 0.0227 | 0.0328 |
| book_sess K7 sess5 | alt_range8 | c4_w1_kama8_px_range8_fresh5 | 1 | 634 | 0.32 | 0.100 | 3.6 | 2.6 | 3.5 | 4/4 | 0.117 | 1 | yes x1.5 / no x0.5 | 0.0246 | 0.0428 |
| book_sess K7 sess5 | alt_range8 | c4_w1_willr21_range8_rise | 6 | 951 | 0.47 | 0.134 | 3.5 | 2.6 | 3.4 | 4/4 | 0.279 | 1 | yes x1.5 / no x0.5 | 0.0338 | 0.0729 |
| book_sess K7 sess5 | alt_range8 | c4_zlema_slope_range8_rise | 1 | 976 | 0.49 | 0.122 | 3.5 | 2.6 | 3.4 | 4/4 | 0.250 | 1 | yes x1.5 / no x0.5 | 0.0306 | 0.0650 |
| book_sess P7 sess0 | alt_range8 | c4_w1_kama50_px_range8_fresh5 | 1 | 1320 | 0.28 | 0.092 | 3.8 | 3.1 | 3.9 | 4/4 | 0.077 | 1 | yes x1.5 / no x0.5 | 0.0031 | -0.0149 |
| book_sess P7 sess0 | alt_ha60 | c4_fvg_cnt_ha60_side | 1 | 1472 | 0.31 | 0.120 | 3.8 | 3.1 | 3.7 | 4/4 | 0.062 | 1 | yes x1.5 / no x0.5 | 0.0125 | -0.0089 |
| book_sess P7 sess0 | alt_tick2000 | c4_w1_linreg_slope20_tick2000_rise | 1 | 3131 | 0.67 | 0.138 | 3.7 | 3.1 | 3.6 | 4/4 | 0.202 | 1 | yes x1.5 / no x0.5 | 0.0424 | 0.0640 |
| book_sess P7 sess0 | alt_ha60 | c4_kstS_ha60_side | 1 | 2119 | 0.45 | 0.153 | 3.6 | 3.1 | 3.5 | 4/4 | 0.130 | 1 | yes x1.5 / no x0.5 | 0.0344 | 0.0282 |
| book_sess P7 sess0 | alt_tick2000 | c4_w1_linreg_chan20_tick2000_side | 1 | 3061 | 0.65 | 0.116 | 3.5 | 3.1 | 3.5 | 4/4 | 0.083 | 1 | yes x1.5 / no x0.5 | 0.0370 | 0.0391 |
| book_sess P7 sess0 | alt_ha60 | c4_ichiS_score_ha60_eagainst | 1 | 1200 | 0.25 | -0.123 | -3.5 | 3.1 | -3.6 | 0/4 | -0.048 | 1 | yes x0.5 / no x1.5 | 0.0403 | 0.0286 |
