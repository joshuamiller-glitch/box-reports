# DS3_FILTERS_RAW - Part 2 of DIRECTIVE_BASIC_TESTS (W-CF3) - FIRST PASS

VERDICT (data ends 2026-10-30; FIRST PASS): (1) PATH EFFECT, not yet fully explained: of the engine gate's extra drawdown ($103k vs $52k base) about $11k is the selection (removing the counter-trend half removes a hedge) and about $40k comes from MORE aligned trades because freed books take every aligned signal (1,090 replacement trades, positively correlated with the core trades); same-side re-entry within 30 minutes of a rejection is only about 18 % of the replacements, so H002 as stated is not supported; the wait / stand-down / random-gate diagnostic engine runs are queued and every skip-rule engine result keeps the flag PATH EFFECT UNEXPLAINED until they land. (2) On the raw books (one book alone, ISO2, 23 of 43 months) filters work only weakly and unevenly: at the nonsense 99th-percentile bar (1 % pass by construction) the real pass rates are 0.2 % to 5.9 % per cell, highest in P7 NY PM, M7 NY AM and NY PM, K7 NY AM, A7 Asia / K7 Asia; the P7 NY PM leads do NOT survive a split-sample check (below), so no raw-book filter is established. (3) What the live layers already capture: strong raw conditions are not systematically weaker on the stack, because the pass rates are not systematically higher raw than on the stack (table 2b). FIRST PASS: 23 ISO2 months of 43, 7,074 conditions; nothing here is a verdict.

## 1. Path effect: what is known (all L6M, JN05W2 vs TL3_CF_PL_G = keep only signals where c_A_trend_15m, c_D_sess_side and c_E_ret15_with are all true, every universe signal gated)
- Engine gate: 2,863 trades, net $499,963, max DD $103,361; base: 4,169 trades, $660,702, DD $52,233. Table-level subset of the base trades that are all-three-true (no replacements, no path change): 1,991 trades, $393,443, DD $63,119.
- Replacements (engine trades whose signal was not a base trade): 1,090 of 2,863 (38 %), net $170,035, DD $59,125 alone; non-replacement engine trades: 1,773, $329,929, DD $56,282; weekly correlation between the two 0.24 (daily 0.20): the engine DD is close to the SUM of two positively correlated parts.
- Hedge removal: weekly correlation between the aligned subset and the rest -0.13; worst subset week -$36,337 while the dropped trades made +$31,829 in that week.
- Not extra exposure at a time: time-weighted mean |net directional lots| 1.13 (base 1.63), 95th pct 6 (8), peak 17 (17); mean gross lots open 1.13 (1.79); daily P&L sd $13.6k (base $15.3k); mean pairwise daily correlation between books 0.186 (0.123).
- Same-side re-entry (H002): replacements within 15 / 30 / 60 minutes of a dropped base trade of the same book: 11 % / 21 % / 34 % of replacements, of which 97 % / 86 % / 71 % same side; mean $ of the same-side ones within 30 min +$83 (opposite -$559). Re-entering into the failed move explains a minority.
- Queued (tag CF, L6M): random gate with the same keep share (PX_RND), gate with 30-minute stand-down (PX_G30), random with stand-down (PX_RND30), mirror gate (PX_MIR). Switching off post-stop blackout, DAY-DONE, stack cap and lot gates needs engine flags not exposed in the set files; to be added after the stand-down result.

## 1b. Path effect: engine diagnostics landed (L6M, JN05W2, every universe signal gated; FIRST PASS; data ends 2026-10-30)
| set | trades | net $ | max DD $ | max DD R | worst week $ | PF | $/trade | R/trade | share of trades that are replacements |
|--|--|--|--|--|--|--|--|--|--|
| JN05W2 base | 4,169 | 660,702 | 52,233 | 20.8 | -36,371 | 1.20 | 158 | 0.061 | 0 % |
| PL_G aligned gate (all three true, 50 % keep) | 2,863 | 499,963 | 103,361 | 60.5 | -47,069 | 1.24 | 175 | 0.070 | 38 % |
| PX_RND random gate, same keep share per book/session/month | 3,397 | 428,037 | 85,922 | 35.5 | -36,621 | 1.16 | 126 | 0.054 | 43 % |
| PX_G30 aligned gate + 30-min stand-down after each skip | 2,600 | 448,342 | 98,303 | 51.2 | -56,388 | 1.23 | 172 | 0.067 | 38 % |
| PX_RND30 random gate + 30-min stand-down | 2,765 | 345,348 | 72,422 | 31.1 | -30,544 | 1.17 | 125 | 0.060 | 40 % |
| PX_MIR all three FALSE (66 trades) | 66 | 8,566 | 32,933 | 10.1 | -14,698 | 1.09 | 130 | 0.068 | 65 % |

Findings: (1) A RANDOM 50 % skip rule already raises the stack drawdown from $52k to $86k (R 20.8 to 35.5) and cuts net from $661k to $428k: the path effect is generic to skip rules, not specific to the aligned gate. Mechanism: the freed book takes later re-signals that the base run could not take (the book was in a position when they arrived): 43 % of trades under the random gate are such replacements and the trade average falls from $158 to $126, i.e. replacements are weaker, later entries, and they add trades in the same stretch. (2) The aligned gate adds about $17k on top (hedge removal, trend-aligned clustering: $103k vs $86k) and earns a higher expectancy than the random gate ($175 vs $126 per trade, 0.070 vs 0.054 R, PF 1.24 vs 1.16). (3) A 30-minute stand-down after a skip helps the random gate (DD 86k to 72k, R 35.5 to 31.1) but hardly helps the aligned gate (103k to 98k); it does not return to base. (4) So of the extra $51k drawdown of the aligned gate, about $34k is the generic replacement effect (random gate) and about $17k is specific to the aligned selection.
Consequence for verdicts: any skip-rule engine result must be read against the engine random gate of the same keep share (PX_RND-type placebo) and against the stack, not against the table or the base alone; sizing the kept trades or waiting (which do not free the book) avoid (1). The flag PATH EFFECT UNEXPLAINED is replaced by PATH EFFECT = FREED-BOOK REPLACEMENT (generic, quantified above) for skip rules; the one-cause-at-a-time switch runs (stack cut, DAY-DONE C22, c_gov, LOT, SIGQ, REG, day caps; sets TL3_CF_DX_G_* / DX_B_*) are queued to say WHICH engine rule lets the replacements through.

Note from W-PM (relayed 2026-11-15): TL3_PM_N_A7NOSC (an A7 Stop no longer triggers the same-side stack cut on other books) is +$1,641/wk in L3M (A7 itself +0, others +1,641, DD -0.4 %, -1.7 % ex-W44) vs A7 flat -40 +2,126/wk: most of the A7 flat -40 gain is the stack cut losing money, not an A7 exit effect. The stack rule (Asia entries only, cuts 50 % of same-side positions in other books) is therefore a SECOND path-effect cause besides freed-book replacement; the DX_G_NOSC / DX_B_NOSC sets (queued) will be read against it.

## 2. Raw books (isolation mode TL3_CF_ISO2, 23 months), each-alone, cluster-robust by week (zw), nonsense calibrated
Outcome R (clipped +-3); a condition passes alone if |zw| is above the 99th percentile of |zw| of the 200 nonsense conditions in the same cell and its sign is the same in every year with >= 30 per side. At that bar 1 % of conditions (about 70) would pass by construction.

| cell | raw trades | weeks | bar zw | real share beyond 2 | nonsense share beyond 2 | real conditions above the nonsense 99th pct | sign-stable | top sign-stable (zw, n yes, R lift) |
|--|--|--|--|--|--|--|--|--|
| A7|0 | 621 | 103 | 2.28 | 3.1 % | 3.0 % | 119 (1.7 %) | 107 | m_cmf10_60m_divwith (-4.3, 119, -0.17); m_vwma200_px_5m_nodiv (-4.0, 586, -0.36); m_kama50_px_5m_nodiv (-3.7, 526, -0.20) |
| A7|1 | 693 | 106 | 2.45 | 4.8 % | 3.5 % | 137 (2.0 %) | 111 | m_kama200_px_1d_fresh5 (7.1, 44, +0.39); m_kama100_px_1d_fresh5 (4.8, 78, +0.29); m_hma200_px_5m_nodiv (-4.6, 612, -0.30) |
| A7|3 | 647 | 106 | 2.60 | 3.1 % | 7.5 % | 60 (0.9 %) | 46 | m_ichi_std_cloud_1d_rise (5.0, 33, +0.55); m_pat_inside_1d_hi (4.9, 63, +0.17); m_atr_pct100_60m_hi (-4.5, 388, -0.35) |
| A7|4 | 440 | 103 | 3.14 | 3.5 % | 12.5 % | 19 (0.3 %) | 17 | m_vwma200_px_60m_fresh5 (3.9, 68, +0.02); m_stochrsi8_1m_eleave (3.9, 72, +0.22); m_ema_ribbon_1d_fresh5 (-3.8, 31, -0.36) |
| H7|0 | 384 | 103 | 2.82 | 2.9 % | 5.5 % | 37 (0.5 %) | 25 | m_willr7_60m_nodiv (-4.2, 293, -0.01); m_donchian10_pos_60m_nodiv (-4.0, 295, -0.03); m_donchian50_pos_60m_nodiv (-3.9, 310, +0.15) |
| H7|1 | 351 | 101 | 2.39 | 2.7 % | 10.5 % | 93 (1.4 %) | 75 | m_demarker21_15m_rise (-10.3, 287, -0.19); c_K_hour_04 (5.2, 76, +0.17); c_L_sess_net_ge0.5 (4.7, 75, +0.39) |
| K7|0 | 1135 | 106 | 2.68 | 6.8 % | 4.0 % | 127 (1.8 %) | 102 | c_B_cl_ahead_kinds2_15 (5.9, 350, +0.34); c_B_cl_ahead_cnt2_15 (5.9, 346, +0.35); m_hma21_px_1m_side (5.6, 1072, +0.37) |
| K7|1 | 910 | 103 | 2.71 | 3.9 % | 2.5 % | 52 (0.8 %) | 39 | m_boll10_pctb_3m_nodiv (4.0, 690, +0.15); m_ichi_std_tkkj_1m_divwith (-3.8, 101, -0.33); m_boll10_walk_1m_divwith (-3.8, 57, -0.12) |
| K7|3 | 972 | 106 | 2.33 | 3.9 % | 2.5 % | 133 (1.9 %) | 98 | m_cmo21_15m_ewith (4.6, 75, +0.20); m_linreg_chan50_60m_eagainst (3.8, 48, +0.12); m_fisher10_3m_divwith (3.7, 83, +0.17) |
| K7|4 | 831 | 106 | 2.44 | 2.2 % | 3.5 % | 60 (0.9 %) | 49 | m_mfi14_15m_ewith (5.2, 57, +0.34); m_rsi21_15m_ewith (3.8, 70, +0.32); c_L_sess_net_ge0 (3.6, 697, +0.30) |
| M7|0 | 1058 | 106 | 2.36 | 5.5 % | 4.0 % | 176 (2.6 %) | 144 | m_cci50_1d_divwith (-4.1, 69, -0.31); m_di7_15m_nodiv (-3.9, 931, -0.15); m_aroon25_3m_divwith (-3.8, 68, -0.27) |
| M7|1 | 850 | 102 | 2.39 | 4.6 % | 4.0 % | 124 (1.8 %) | 91 | m_keltner10_pos_agree3of4 (-3.9, 804, -0.24); c_D4_rsi14_n4 (-3.9, 795, -0.13); m_roc5_1m_divwith (3.9, 94, +0.33) |
| M7|3 | 847 | 106 | 2.14 | 3.4 % | 2.0 % | 177 (2.6 %) | 129 | c_B5_YM_5m_sqz_fired_dir_with (5.7, 43, +0.31); m_linreg_chan50_1m_divwith (-4.5, 68, -0.18); c_C_px_dpoc_side (-4.4, 792, -0.24) |
| M7|4 | 774 | 106 | 2.25 | 4.4 % | 3.0 % | 185 (2.7 %) | 146 | m_hma200_px_5m_side (-4.2, 717, -0.18); m_turbo_vzo_60m_eagainst (4.1, 64, +0.10); c_A_hhhl_60m (3.9, 219, +0.15) |
| P7|0 | 1099 | 106 | 2.45 | 4.7 % | 4.0 % | 117 (1.7 %) | 74 | c_B_cl_ahead_kinds2_10 (4.1, 322, +0.23); c_B_cl_ahead_cnt2_10 (3.9, 318, +0.22); m_linreg_chan10_5m_nodiv (-3.8, 794, -0.17) |
| P7|1 | 878 | 104 | 3.09 | 3.3 % | 5.5 % | 17 (0.2 %) | 16 | m_macd19_39_9_hist_5m_divwith (10.2, 50, +0.35); m_stochrsi14_1m_fresh5 (-4.3, 187, -0.16); m_vwmacd_5m_divwith (3.8, 49, +0.41) |
| P7|3 | 751 | 106 | 2.59 | 3.2 % | 4.5 % | 49 (0.7 %) | 44 | m_rsi7_3m_divwith (5.1, 73, +0.14); m_keltner20_pos_3m_divwith (4.9, 77, +0.30); m_ema8_px_3m_divwith (4.3, 91, +0.19) |
| P7|4 | 708 | 105 | 2.14 | 7.5 % | 2.5 % | 407 (5.9 %) | 232 | m_ema21_hold_1m_side (5.7, 38, +0.36); c_G_wall_behind10_ge15 (-4.8, 91, -0.12); c_G_wall_behind40_ge15 (-4.8, 91, -0.12) |
| U7|0 | 358 | 99 | 2.90 | 2.0 % | 6.0 % | 19 (0.3 %) | 17 | m_force13_1m_nodiv (4.0, 277, +0.11); m_rsi14_60m_fresh5 (-3.8, 47, +0.07); m_ema21_px_60m_fresh5 (-3.8, 48, +0.07) |
| U7|1 | 367 | 103 | 2.36 | 3.0 % | 4.0 % | 82 (1.2 %) | 67 | c_B_round100_behind_le10 (5.9, 45, +0.32); m_ichi_slow_cloud_15m_fresh5 (4.6, 40, +0.21); m_stochrsi21_60m_divwith (4.2, 59, +0.29) |
| SESSION 0 pooled | 4655 | 106 | 2.25 | 5.5 % | 4.0 % | 226 (3.3 %) | 132 | c_B_cl_ahead_kinds2_15 (5.6, 1514, +0.27); c_B_cl_ahead_cnt2_15 (5.5, 1496, +0.26); c_B_cl_ahead_kinds2_10 (4.4, 1555, +0.24) |
| SESSION 1 pooled | 4049 | 106 | 2.41 | 5.5 % | 5.5 % | 171 (2.5 %) | 125 | m_donchian10_pos_1d_eagainst (-4.5, 338, -0.28); c_B15_pc_tot_pct_le20 (-4.1, 944, -0.18); m_willr7_15m_eagainst (3.9, 58, +0.19) |
| SESSION 2 pooled | 630 | 98 | 2.44 | 3.8 % | 4.0 % | 124 (1.8 %) | 101 | m_vwma100_px_5m_divwith (-5.4, 57, -0.33); m_keltner40_pos_5m_divwith (-5.2, 72, -0.29); m_ema34_px_5m_divwith (-5.2, 72, -0.30) |
| SESSION 3 pooled | 3871 | 106 | 2.51 | 5.1 % | 4.0 % | 102 (1.5 %) | 64 | c_A_firstpb_15m (-5.5, 305, -0.31); m_macd19_39_9_hist_1m_fresh5 (-4.1, 673, -0.20); m_vol_avg_rel_60m_hi (-3.7, 3662, -0.31) |
| SESSION 4 pooled | 3103 | 106 | 2.14 | 7.3 % | 3.0 % | 376 (5.5 %) | 180 | c_F_big50_noagainst5 (4.7, 2904, +0.28); c_D_beyond_3sig (-4.7, 40, -0.57); m_demarker7_15m_ewith (-4.0, 1602, -0.06) |

### 2b. Same screen on the STACK (JN05W2 taken trades, all live layers ON) for the same 23 months
Cells: raw (stable passers, % of conditions) vs stack. If the live layers had already captured a raw condition, the stack pass rate would be lower than the raw one in the cells where the layers act.

| cell | raw trades / stable passers (%) | stack trades / stable passers (%) |
|--|--|--|
| A7|0 | 621 / 107 (1.6 %) | 616 / 65 (0.9 %) |
| H7|0 | 384 / 25 (0.4 %) | 396 / 49 (0.7 %) |
| K7|0 | 1135 / 102 (1.5 %) | 1333 / 80 (1.2 %) |
| K7|1 | 910 / 39 (0.6 %) | 949 / 134 (1.9 %) |
| K7|3 | 972 / 98 (1.4 %) | 834 / 25 (0.4 %) |
| K7|4 | 831 / 49 (0.7 %) | 578 / 119 (1.7 %) |
| M7|1 | 850 / 91 (1.3 %) | 1334 / 67 (1.0 %) |
| M7|3 | 847 / 129 (1.9 %) | 776 / 50 (0.7 %) |
| P7|0 | 1099 / 74 (1.1 %) | 1152 / 70 (1.0 %) |
| P7|1 | 878 / 16 (0.2 %) | 827 / 67 (1.0 %) |
| P7|3 | 751 / 44 (0.6 %) | 554 / 111 (1.6 %) |
| U7|0 | 358 / 17 (0.2 %) | 358 / 16 (0.2 %) |
| U7|1 | 367 / 67 (1.0 %) | 347 / 46 (0.7 %) |

Reading 2b: the stack pass rate is lower than the raw one in K7 NY AM, M7 NY AM, M7 Asia and A7 Asia / London (the layers act there), and higher in K7 London, K7 NY PM, P7 London and P7 NY AM (the layers add outcome structure of their own, e.g. context cut and state cut create conditional exits; or the zero-lot P7/K7 cells have far fewer stack trades). A per-condition overlap with each named live layer needs per-trade flags of the layers from the engine logs; not built, so layer-by-layer "already in the stack under another name" cannot yet be stated.

### 2c. P7 NY PM (benched in the stack; raw -$145 per trade over 708 raw trades): split-sample check (p7pm_rescue.py)
Conditions chosen on raw trades before 2025-01 (269 trades, |zw| above the nonsense 99th percentile 2.78, 28 conditions beyond the bar, 25 sign-stable), tested on 2025-01..2026-10 (439 trades, raw -$196 per trade): of the top 40 sign-stable singles, 20 % have positive out-of-sample $/trade in their favourable state and 44 % beat the unfiltered raw cell; the 40 best nonsense conditions chosen the same way: 10 % positive and 47 % better. So the P7 NY PM raw-filter "leads" do not hold out of sample: first pass verdict for the rescue of this benched cell: no checklist helps (same method that found them in-sample).

## 3. Not done yet (no verdicts)
Layer-by-layer overlap (2c proper), replacement settings of a layer (2d; W-LA has the loss-layer table in DS3_DEEPEN_LOSS_LAYERS.md and takes library conditions as TL3_LA_R_* cells), size / wait-for-it tests of any raw-working condition on the full stack (2e), November extension (2g), the remaining 20 ISO2 months, blocks 4-5 and 7-17 in the raw-book library, diagnostic engine runs of the path effect (queued).
