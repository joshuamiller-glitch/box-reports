# CF4_ZW_TOP - where the top passers pass (book x session) and how many are near-duplicates

Passing test = the full each-alone rule of DS3_CONFLUENCE_ITEMS_CF4_ZW.md. Clusters = greedy grouping of the passing conditions of a cell by |r| > 0.9 of their yes-vectors (60k-row sample); "distinct" is the number of such clusters. Lift in R per signal.

## alt_range8

1055 passing tests, 737 distinct conditions, 559 near-duplicate clusters overall (|r|>0.9). Passing tests by cell type: {'book_sess': 524, 'book': 192, 'ALL': 173, 'sess': 166}. Median |lift| of passing tests 0.070 R, median n_yes 2912.

| cell | book | sess | passing tests | distinct conditions | clusters | median lift R | with sign + / - | top condition (|zw|) |
|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 173 | 173 | 95 | 0.022 | 159/14 | c4_brkS_near_range8_against (4.1) |
| book | P7 |  | 89 | 89 | 68 | 0.026 | 74/15 | c4_sdflipF_near_range8_side (3.6) |
| book_sess | P7 | 4 | 88 | 88 | 72 | 0.081 | 84/4 | c4_smiS_range8_fresh5 (3.5) |
| book_sess | K7 | 5 | 76 | 76 | 50 | 0.116 | 72/4 | c4_w1_ema8_px_range8_fresh5 (4.1) |
| sess |  | 3 | 72 | 72 | 63 | 0.046 | 60/12 | c4_w1_kama_stack_fast_range8_against (4.4) |
| book_sess | P7 | 1 | 46 | 46 | 39 | -0.062 | 13/33 | c4_structF_range8_fresh5 (3.8) |
| sess |  | 4 | 45 | 45 | 38 | 0.046 | 40/5 | c4_w1_linreg_chan20_range8_fresh5 (3.4) |
| book_sess | K7 | 1 | 32 | 32 | 19 | 0.130 | 23/9 | c4_w1_ema50_px_range8_side (3.9) |
| book | A7 |  | 31 | 31 | 22 | 0.047 | 25/6 | c4_almaF_slope_range8_rise (3.7) |
| book_sess | A7 | 0 | 31 | 31 | 28 | 0.165 | 27/4 | c4_w1_kama21_px_range8_nodiv (4.0) |
| book_sess | K7 | 0 | 31 | 31 | 27 | 0.070 | 24/7 | c4_w1_vwma200_px_range8_side (4.3) |
| sess |  | 5 | 30 | 30 | 26 | -0.044 | 13/17 | c4_stP_range8_hold3 (3.3) |
| book | M7 |  | 29 | 29 | 24 | 0.038 | 20/9 | c4_ote_wideS_range8_side (3.4) |
| book_sess | A7 | 3 | 29 | 29 | 23 | 0.110 | 25/4 | c4_don10_pos_range8_side (3.9) |

## alt_ha60

1028 passing tests, 646 distinct conditions, 554 near-duplicate clusters overall (|r|>0.9). Passing tests by cell type: {'book_sess': 403, 'book': 270, 'sess': 252, 'ALL': 103}. Median |lift| of passing tests 0.098 R, median n_yes 1869.

| cell | book | sess | passing tests | distinct conditions | clusters | median lift R | with sign + / - | top condition (|zw|) |
|---|---|---|---|---|---|---|---|---|
| ALL |  |  | 103 | 103 | 97 | -0.050 | 22/81 | c4_smie_ha60_eleave (5.9) |
| book | M7 |  | 103 | 103 | 91 | -0.069 | 9/94 | c4_w1_cmo14_ha60_eleave (4.9) |
| sess |  | 3 | 92 | 92 | 79 | -0.078 | 5/87 | c4_tsi_ha60_divwith (5.1) |
| book | A7 |  | 78 | 78 | 71 | -0.088 | 16/62 | c4_w1_rsi21_ha60_eleave (5.4) |
| book_sess | A7 | 4 | 64 | 64 | 59 | -0.217 | 1/63 | c4_ker_dir_ha60_divwith (4.9) |
| sess |  | 4 | 56 | 56 | 55 | -0.108 | 3/53 | c4_crsi_ha60_divwith (4.7) |
| book_sess | K7 | 0 | 49 | 49 | 37 | 0.075 | 33/16 | c4_kvo_ha60_nodiv (3.6) |
| book | P7 |  | 46 | 46 | 41 | -0.059 | 13/33 | c4_w1_aroon50_ha60_divwith (4.0) |
| sess |  | 5 | 43 | 43 | 35 | -0.100 | 1/42 | c4_kvoF_ha60_divwith (4.1) |
| sess |  | 1 | 35 | 35 | 30 | 0.051 | 18/17 | c4_w1_cmo14_ha60_eleave (4.3) |
| book_sess | K7 | 2 | 26 | 26 | 23 | -0.170 | 11/15 | c4_w1_vortex21_ha60_fresh5 (3.4) |
| book | H7 |  | 22 | 22 | 13 | -0.077 | 10/12 | c4_sdS_dsup_ha60_hi (3.7) |
| book_sess | A7 | 0 | 21 | 21 | 20 | -0.199 | 4/17 | c4_elderS_bull_ha60_nodiv (3.9) |
| book_sess | P7 | 1 | 21 | 21 | 20 | 0.057 | 11/10 | c4_obS_cnt_ha60_rise (3.3) |

## alt_ha5

923 passing tests, 662 distinct conditions, 554 near-duplicate clusters overall (|r|>0.9). Passing tests by cell type: {'book_sess': 540, 'sess': 212, 'book': 153, 'ALL': 18}. Median |lift| of passing tests 0.107 R, median n_yes 1182.

| cell | book | sess | passing tests | distinct conditions | clusters | median lift R | with sign + / - | top condition (|zw|) |
|---|---|---|---|---|---|---|---|---|
| sess |  | 3 | 99 | 99 | 82 | 0.056 | 69/30 | c4_w1_donchian50_pos_ha5_nodiv (3.8) |
| book_sess | K7 | 1 | 75 | 75 | 64 | -0.128 | 21/54 | c4_w1_stoch14_ha5_rise (4.1) |
| book_sess | M7 | 3 | 74 | 74 | 51 | 0.071 | 72/2 | c4_rfilt_ha5_side (4.0) |
| book_sess | M7 | 2 | 55 | 55 | 42 | -0.299 | 6/49 | c4_w1_cci20_ha5_divwith (3.6) |
| book | H7 |  | 48 | 48 | 32 | -0.054 | 23/25 | c4_sqzm_mom_ha5_divwith (4.2) |
| book_sess | K7 | 0 | 47 | 47 | 38 | 0.077 | 37/10 | c4_w1_donchian20_width_ha5_hi (3.9) |
| book_sess | K7 | 2 | 47 | 47 | 39 | -0.127 | 18/29 | c4_w1_adx7_ha5_hi_z1 (4.3) |
| sess |  | 1 | 44 | 44 | 38 | -0.115 | 8/36 | c4_w1_psar_0.02_ha5_divwith (4.0) |
| book_sess | A7 | 5 | 37 | 37 | 34 | 0.282 | 33/4 | c4_elderF_bear_ha5_divwith (4.1) |
| book | A7 |  | 36 | 36 | 34 | -0.113 | 6/30 | c4_w1_donchian10_pos_ha5_divwith (4.1) |
| book | P7 |  | 25 | 25 | 21 | -0.062 | 9/16 | c4_seb_ha5_eenter (4.3) |
| book_sess | A7 | 2 | 22 | 22 | 22 | -0.285 | 3/19 | c4_w1_stoch21_ha5_sig (3.6) |
| sess |  | 2 | 21 | 21 | 20 | -0.257 | 3/18 | c4_w1_ema200_px_ha5_divwith (3.5) |
| ALL |  |  | 18 | 18 | 17 | -0.044 | 4/14 | c4_fvg_dsup_ha5_rise (3.2) |

## alt_tick2000

898 passing tests, 682 distinct conditions, 540 near-duplicate clusters overall (|r|>0.9). Passing tests by cell type: {'book_sess': 472, 'sess': 201, 'book': 176, 'ALL': 49}. Median |lift| of passing tests 0.097 R, median n_yes 1838.

| cell | book | sess | passing tests | distinct conditions | clusters | median lift R | with sign + / - | top condition (|zw|) |
|---|---|---|---|---|---|---|---|---|
| book_sess | K7 | 0 | 167 | 167 | 129 | 0.079 | 95/72 | c4_w1_eom14_tick2000_side (3.8) |
| sess |  | 0 | 75 | 75 | 66 | 0.070 | 63/12 | c4_sdF_near_tick2000_side (4.5) |
| book_sess | K7 | 2 | 65 | 65 | 39 | -0.164 | 16/49 | c4_sslS_tick2000_side (3.7) |
| ALL |  |  | 49 | 49 | 35 | 0.035 | 41/8 | c4_rsima7_tick2000_nodiv (3.8) |
| book | A7 |  | 49 | 49 | 38 | 0.046 | 34/15 | c4_w1_stoch21_tick2000_eagainst (5.5) |
| book | U7 |  | 47 | 47 | 36 | 0.125 | 33/14 | c4_w1_di21_tick2000_nodiv (4.3) |
| book | M7 |  | 38 | 38 | 30 | 0.051 | 28/10 | c4_rsima14_tick2000_nodiv (3.2) |
| sess |  | 1 | 34 | 34 | 29 | -0.070 | 4/30 | c4_sebF_tick2000_eagainst (3.5) |
| sess |  | 4 | 31 | 31 | 26 | 0.063 | 23/8 | c4_w1_roc20_tick2000_nodiv (4.3) |
| sess |  | 3 | 26 | 26 | 24 | -0.052 | 4/22 | c4_w1_ichi_fast_cloud_tick2000_nodiv (3.0) |
| book | P7 |  | 25 | 25 | 23 | 0.036 | 13/12 | c4_w1_linreg_chan50_tick2000_eleave (3.5) |
| book_sess | K7 | 4 | 24 | 24 | 21 | 0.096 | 19/5 | c4_lrcF_tick2000_fresh5 (4.0) |
| book_sess | A7 | 0 | 21 | 21 | 19 | 0.109 | 14/7 | c4_srsiS_tick2000_divwith (3.5) |
| sess |  | 2 | 20 | 20 | 15 | 0.196 | 16/4 | c4_w1_hma200_px_tick2000_nodiv (3.5) |

